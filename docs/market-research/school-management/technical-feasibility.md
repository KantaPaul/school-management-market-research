# Technical feasibility

No school-management repository was available. Nothing in this document is a claim about an existing codebase. The stack below is a proposal for a product the founder would host. It is not a CodeCanyon deliverable, and it should not be built until the interview gate in [phase-approval-gates.md](phase-approval-gates.md) is passed.

## 1. Stack

| Choice | Judgement |
| --- | --- |
| Next.js with TypeScript in strict mode | Sound for a hosted UI and server. Useless as a sales claim. Confirmed by the absence of demand for the Node school script on CodeCanyon |
| PostgreSQL | Appropriate for money, constraints, and row-level security. A poor fit for buyers who expect phpMyAdmin. Those buyers are not the launch customer |
| Drizzle | Acceptable if the schema stays in the repository and migrations are reviewed. The ORM is not the financial control. Constraints and tests are |
| Zod | Use it at the boundary, then keep domain calculations in functions that do not trust parsed input a second time |
| Modular monolith | Correct. One deployable application, modules as folders with explicit interfaces. Not microservices |
| Solo founder | The architecture has to be boring enough that a production incident can be understood at night |

Rejected for the first release: a separate auth service, a separate billing service, an event bus, a mobile codebase, a plugin marketplace, and a white-label build pipeline.

## 2. Minimum foundations before a real centre is onboarded

These are gates, not a backlog of nice hardening.

1. One production environment and one staging environment. Staging uses fictional students only.
2. `tenant_id` on every tenant-owned row, plus Postgres row-level security, plus a test that a session for centre A cannot read centre B.
3. Money stored as integer poisha. No floating point in fee arithmetic.
4. Posted payments and waivers are not updated in place. A correction is a new row. The balance is derived.
5. Role checks on the server for every mutation. Hiding a button is not authorization.
6. A spreadsheet import that can be re-run without duplicating students, and an export of students, obligations, and payments.
7. A backup that has been restored onto a throwaway database. A backup that has never been restored does not count.
8. An audit row for ledger changes: who, when, before, after.
9. TLS, hashed passwords, and no student data in application logs.
10. A written list of personal fields collected, and a way to export or delete one student’s record. This is an engineering control. It is not a claim of compliance with the Personal Data Protection Act, 2026.

## 3. Tenancy

Use one database and a shared schema. Each centre is a tenant. Every query that reads or writes tenant data sets the tenant id from the server session, not from a value the browser sends in the body.

Row-level security is the backstop. Application filters are still required so a missing policy fails a test rather than becoming the only control. Do not start with a database per tenant. eSchool advertises that model for buyers who will operate many schools they do not own. It multiplies migrations and backups. It can be introduced later for a large tenant if a contract requires it. Nothing in the Dhaka coaching interviews has happened yet, so that requirement does not exist.

Do not build a branch hierarchy in the first schema beyond a nullable `campus_id` that stays unused. Adding a column later is cheaper than maintaining an empty multi-campus UI. If a second campus is a likely contract, stop and redesign tenancy before signing. Do not sneak it into the pilot.

## 4. Ledger

Suggested shape, to be turned into a real schema only in Phase 3:

- `fee_obligation`: student, batch, period, gross amount in poisha, status.
- `waiver`: obligation, amount, reason, actor. A waiver reduces what is owed.
- `payment`: obligation, amount, method (`cash`, `bkash`, `nagad`, `bank`), external reference, received date, actor.
- `ledger_entry`: append-only view or table of the above, used by the due list and the receipt.

Balance = gross − waivers − payments. All three are sums of rows. A negative balance is a data error and should fail a test, not display as a credit unless a later product decision adds credit balances. Partial payment is the normal case, not an edge case. Discounts that are a percentage must be converted to poisha once, at posting, and stored as an amount so a later change in rounding rules does not rewrite history.

Idempotency matters on imports and, later, on payment callbacks. A client-generated key on each posted payment stops a double submit from recording two receipts.

Live bKash is out of scope until a merchant agreement exists. The column for a processor payment id can exist and stay null. Do not invent a custody flow in which guardians pay the founder’s personal wallet.

## 5. Authorization

Three roles are enough:

| Role | Can do | Cannot do |
| --- | --- | --- |
| Owner | Everything inside the tenant, including exports and inviting users | See another tenant |
| Clerk | Create students, record payments, print receipts | Delete or rewrite a posted payment. Change roles |
| Teacher | Mark attendance for assigned batches. Read the student names on those batches | See fee balances, unless the owner later insists and the reason is written down |

Server-side checks live next to the use case, not only in middleware that can be forgotten on a new route. A permission matrix belongs in tests.

## 6. Privacy and student data

The Personal Data Protection Act, 2026 applies to processing children’s data and requires guardian consent, with the controller able to prove it. See [market-analysis.md](market-analysis.md). Engineering response for a pilot, pending legal advice:

- Collect name, guardian phone, batch, attendance, and payment facts. Do not collect national ID, date of birth, photos, or device location unless a pilot cannot function without one of them.
- Store a consent note: who agreed, on what date, and to what short description.
- Keep backups encrypted and access-limited.
- Do not send student lists to an analytics product that is not named in the pilot agreement.
- Do not add advertising or behavioural profiles.

Sections of the Act are phased. That phase-in is not a reason to collect more data.

## 7. Import, reporting, backup, deployment

Import maps a spreadsheet into students and opening balances. It runs in a transaction per batch. Rows with errors are reported and not half-written. The owner receives a count of created and skipped rows.

Reports for the first release are SQL queries behind two screens: collection for a date range, and outstanding balances by batch. They must use the same balance function as the receipt. A report that reimplements the arithmetic is a defect even if it looks right on sample data.

Backup is a daily database dump to a location that is not the application server, plus a monthly restore drill recorded in a log. Point-in-time recovery is ideal and not required for the first five pilots if the dump-and-restore drill is real. The founder writes the restore steps while building, not after the first loss.

Deployment is one Next.js application and one Postgres instance. Migrations run forward only. A migration that rewrites payment history is forbidden. Monitoring is an error tracker, disk and database health, and an alert when backups fail. That is enough. A custom observability platform is not.

Background jobs: a single queue for imports and, later, SMS. Attendance and payment posting stay in the request path so the user sees the result. Do not introduce a second language or a separate worker platform until a job actually needs it. A cron process next to the app is enough.

Localization: Bangla and English strings in one catalogue. Receipts choose a language per print. Dates and taka formatting are tested, including Bengali digits if a pilot asks for them. Do not invent a translation workflow for other countries.

## 8. Testing

The tests that matter more than a coverage target:

- Tenant isolation, including a forged tenant id in the request.
- The partial-payment example from the roadmap: 1,000 taka gross, 200 taka waiver, two 300 taka payments, 200 taka still due.
- Two clerks submitting the same payment key once.
- A teacher token denied on a payment route.
- Importing the same file twice does not duplicate students.
- A correction does not change the original payment row.

Financial tests use integers. They do not compare floats.

## 9. Licensing, updates, and support operations

The launch product is hosted by the founder. There is no source-code licence to draft until a second channel is justified in [pricing-and-unit-economics.md](pricing-and-unit-economics.md). Updates are deploys, not zip files emailed to customers. That removes the CodeCanyon problem of old forks and “please install it for me”, and it concentrates operational risk on the founder. Backups and a status habit are the mitigation.

Support operations for a pilot:

- One shared inbox.
- Business-day replies.
- A defect is a wrong balance, a failed login, or a broken import. A new report is a request, not a defect.
- No remote-desktop sessions as the default. They become the product.
- No promise of same-day on-site visits.

## 10. What this stack does not solve

It does not make schools pay. It does not replace merchant approval at bKash. It does not make a solo founder into an overnight support team for 40 modules. It does make a small ledger easier to test than a pile of untyped PHP copied from a marketplace script. That is the only technical advantage worth claiming, and it is an advantage for the person who must maintain the system.
