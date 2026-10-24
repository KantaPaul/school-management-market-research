# MVP and roadmap

The product under consideration is not a 40-module school ERP. It is the fee, attendance, and student-record loop for one Dhaka coaching centre. Modules from the original brief are all listed below so the exclusions are explicit. Inclusion follows the positioning in [product-positioning.md](product-positioning.md), not the length of competitor feature grids.

No application code is in this repository. There was no existing school-management codebase to preserve.

## 1. The workflow that must work

A centre can do all of the following without a spreadsheet and without the founder clicking through the task for them:

1. Create the centre, one campus, and the current collection period.
2. Create a batch with a subject, a teacher, a weekly pattern, a fee amount, and a list of students.
3. Record a guardian phone number against the student.
4. Import that list from a spreadsheet, or enter it directly.
5. Mark the batch present or absent for a date in one pass.
6. Generate the period’s fee obligations. Apply a discount or a waiver to one student with a reason.
7. Record a full payment, a partial payment, or several payments against one obligation. Each payment has a method: cash, bKash, Nagad, or bank. Wallet payments store a reference the owner can see. They do not call a live API.
8. Issue a receipt that shows the amount, the remaining balance, and the student.
9. Open a due list filtered by batch and by aging.
10. Export students, obligations, payments, and attendance.
11. See an audit row when a recorded payment or a waiver changes.

That is the commercial product. Exams, payroll, and a guardian login are not required for this loop to be true.

## 2. Priority definitions

| Priority | Meaning |
| --- | --- |
| P0 | Required for a paying pilot centre to run the loop above |
| P1 | Build only after a pilot uses P0 and asks for this with a specific example |
| P2 | Not in the first product. Reopens the “general ERP” scope |

## 3. Module decisions

| Module | Priority | Problem | Business value | Depends on | Complexity | Risk | Acceptance, if it is ever built | Why it is here |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Centre and period setup | P0 | The owner needs a place for this month’s students and fees | Without it there is no tenant | None | Low | Over-building academic years, shifts, and campuses | One centre, one open period, later periods do not edit closed receipts | Required to operate |
| Batches, subjects, teachers | P0 | Coaching is organised in batches, not classes 1–12 | This is the unit owners already use | Centre | Low | Modelling a full school timetable “just in case” | A student can sit in more than one batch. A batch has one default fee | ClassTablet and CampusQ both sell batches. [ClassTablet](https://classtablet.com/en-US/coaching-center-software), [CampusQ](https://campusqbd.com/pricing) |
| Classes, sections, and a K-12 calendar | P2 | Schools need this. Coaching centres do not | Expands the buyer set later | A decision to serve schools | Medium | Pulls the product into segment B before segment A pays | Not in the pilot | Deferred. Kindergartens are the second segment, not the first |
| Admissions pipeline | P1 | Some centres want an enquiry list | Useful, not required to collect fees from people already attending | Students | Medium | Becomes a CRM | Can be a status on the student. A full application portal is P2 | Attractive. Not required for the fee loop |
| Student and guardian records | P0 | Receipts and attendance need a person and a phone number | Core record | Centre | Low | Collecting more personal data than the fee desk needs | Name, phone, batch, status. Extra fields are optional and justified | Required |
| Staff records | P0 | The teacher who marks attendance must be a user | Accountability | Centre | Low | Quietly becoming payroll | Name, phone, role. No salary | Required for permissions |
| Role-based permissions | P0 | A teacher should not edit a receipt | Trust | Staff | Medium | A homemade permission bug | Owner sees money. Teacher marks attendance for assigned batches. Clerk records payments and cannot delete a posted receipt | Required before real money is entered |
| Student attendance | P0 | Teachers need a fast batch roll | Owners use absence as a reason to chase fees. **Hypothesis** that this is daily | Batches, students | Low | Making it a biometric integration | A batch of 40 can be marked on a phone in one sitting | In the core loop. Biometric machines are P2 |
| Examinations and full mark entry | P2 | Schools and some centres want results | High for schools, not for the fee problem | Grading | High | Recreates InfixEdu | Not in the first release | Overrepresented on CodeCanyon. Not the buying trigger |
| Simple test scores | P1 | Some tuition centres publish a weekly test | Retention of a centre that already pays | Students, batches | Medium | Turns into a grading engine | One score per student per test. No GPA, no board tabulation | Only after a paying pilot asks |
| Configurable grading and report cards | P2 | Bangla-medium and English-medium schools need different marksheets | Large project | Exams | High | NCTB, Dakhil, and Cambridge are three products | Not in the first release | Aara and MicroCampus already advertise this for schools |
| Fee structures and billing | P0 | Monthly obligations must exist without retyping | The product’s reason to exist | Students, batches | Medium | Wrong fee rules | A batch fee generates obligations. A student can have an override | Required |
| Discounts, waivers, partial payments | P0 | Real centres do not collect the full invoice on the first day | This is the failure mode of a naive “paid or unpaid” flag | Fees | High | Rounding and balance errors | A 1,000 taka fee with a 200 taka waiver and two 300 taka payments leaves 200 taka due. The receipt shows that | MicroCampus and general ERPs advertise partial pay and waivers. Correctness is the product |
| Receipts, dues, reconciliation | P0 | The owner’s actual question at night | Directly tied to cash | Payments | Medium | A due list that does not match the sum of receipts | Due list, receipt, and export agree to the poisha | Required |
| Guardian portal | P1 | Guardians ask “how much do we owe?” | Reduces phone calls if they actually log in | Receipts, auth | Medium | Building an app nobody opens. SMS may matter more | Read-only balance and attendance. No messaging thread | Vendors advertise portals. Usage is **Unknown**. Do not block launch |
| Notices and notifications | P1 | Owners send batch changes and fee reminders | Expected by local vendors | Guardian phone | Medium | SMS cost and a gateway contract | A manual reminder to the unpaid list. Delivery status stored | P1 because SMS providers and templates were not selected |
| Operational reports | P0 | Daily collection and the due list | The owner will not trust a system with no total | Payments, attendance | Medium | Slow reports, or a report that uses different rules from the ledger | Collection today, collection this period, outstanding by batch | Required. A chart library is not |
| Audit trail | P0 | Disputes about who changed a receipt | Trust, and a practical control | Payments, waivers | Medium | Logging everything and being unable to read it | Money rows are append-only. Corrections are new rows | Required before a pilot |
| Spreadsheet import and export | P0 | Centres will not retype 200 students, and they will not accept a hostage database | Switching cost and trust | Students, payments | Medium | Bad imports that create duplicate students | A sample file imports a batch. Export opens in a spreadsheet | Required. Migration errors are a top risk |
| Backup and recovery | P0 | The founder holds the data | A hosted product that cannot restore is not sellable | Database | Medium | Untested backups | A documented restore of one tenant has been rehearsed | Required before real data |
| Accounting and expenses | P2 | A full cash book | Out of scope for the promise | Fees | High | The product becomes an accounting suite | Not in the first release | Owners may ask. It is a reject-or-defer signal if they will not pay without it |
| Payroll | P2 | Staff salaries | Separate domain | Staff | High | Wrong salary calculations | Not in the first release | Common on ERP brochures. Not the coaching trigger |
| Library, transport, hostel | P2 | Campus operations | Irrelevant to a tutoring centre | Students | High | Scope expansion | Not in the first release | On every CodeCanyon grid. Excluded on purpose |
| Timetable scheduling | P2 | Clash-free weekly schedules | Batch time can be a text field in P0 | Batches | High | A scheduler is a product | Not in the first release | Text “Sat/Mon/Wed 5 pm” is enough for P0 |
| Online classes and LMS | P2 | Pandemic-era feature lists | Centres already use Meet or Zoom | None | High | Empty features | Not in the first release | InfixEdu and others sell this as add-ons with low sales relative to the base script |
| Advanced analytics and AI | P2 | Demos | No evidence of willingness to pay | Clean data | Medium | Distracts from the ledger | Not in the first release | Rejected as a differentiator |
| Multi-branch administration | P2 | Groups with several centres | Higher contract value, much more design | Tenancy | High | Breaks a simple tenant model if bolted on late, which is why tenant_id exists from day one without a branch UI | Not in the first release | Second-segment or later. Do not build the UI |
| Native mobile apps | P2 | Owners imagine a Play Store app | Phone browser can mark attendance | API stability | High | Store accounts, devices, reviews | Not in the first release | eSchool’s apps are for people buying source code. Pathshala charges extra for an APK |
| More countries and languages | P2 | The long-term ambition | Bangla and English are the launch languages | Copy and payments | High | Pretending the data model is universal | English and Bangla UI strings only | Nepal and Sri Lanka were not researched enough to design for |

## 4. What is required versus what is attractive

Required to take money from a pilot:

- The workflow in section 1.
- Bangla and English for navigation, the due list, and the receipt.
- Permissions that keep a teacher out of the ledger.
- Export and a rehearsed backup.
- A way to correct a mistake without silently editing history.

Attractive and refused for the first release:

- Live bKash or Nagad checkout. The APIs are not a substitute for merchant approval. See [market-analysis.md](market-analysis.md).
- SMS blasts.
- Report cards.
- An Android app.
- Anything whose only evidence of demand is that Smart School, InfixEdu, or a local ERP lists it.

## 5. Suggested build sequence, after the interview gate

This sequence starts only if [phase-approval-gates.md](phase-approval-gates.md) allows Phase 4. Durations are solo-developer judgements, not a staffed plan.

| Step | Duration, one developer | Output |
| --- | --- | --- |
| Domain model and clickable due-list prototype | 2 weeks | Owners can point at a screen. No production data |
| Tenancy, auth, students, batches | 2 weeks | A centre can log in and import a batch |
| Ledger: obligations, waivers, partial payments, receipts, audit | 3 to 4 weeks | The arithmetic cases in the acceptance column pass |
| Attendance and the daily collection report | 1 to 2 weeks | The phone path works on a small batch |
| Backup, export, and a pilot checklist | 1 week | Restore rehearsed |
| Pilot repairs | 2 to 4 weeks | Only defects and gaps the pilot actually hits |

The implementation stretch is about 11 to 15 weeks after a prototype, if scope stays here. It is not a 3–6 month plan to clone a school ERP. The weeks before this, for interviews, are required and are not development.

## 6. Explicit non-goals for the first paying version

- One codebase “ready” for madrasas, British curricula, and US schools.
- Pixel parity with Smart School’s module list.
- A self-hosted installer for buyers who are not the founder.
- Automated payroll, inventory, or library fines.
- AI-written report comments.
