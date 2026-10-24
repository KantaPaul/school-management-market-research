# Phase approval gates

Completing a phase does not approve the next one. Each gate has a yes or no. A “revise” result stays in the current phase or returns to an earlier one. Durations assume one founder and no application code until Phase 4. They are planning judgements, not commitments to a calendar.

The decision this research supports is **PROCEED WITH CONDITIONS**. Phase 0 produced a niche. It did not produce permission to build.

## Phase 0. Market research

| | |
| --- | --- |
| Objective | Decide whether a solo developer should build a school ERP, a narrower product, or nothing |
| Deliverables | This directory: competitor matrix, segment scores, pricing illustrations, risks, and the recommendation in [README.md](README.md) |
| Duration | Done as of 24 October 2026 |
| Dependencies | Public listings, vendor prices, and news reports of official statistics. No interviews yet |
| Acceptance | A primary segment, a geography, a buyer, a problem, and a business model are named. Claims that were not observed are labelled |
| Risks | Treating vendor prices as proof of pain. Treating a census as a count of buyers |
| Go | Yes, into Phase 1 only. The niche is Dhaka coaching centres and the fee-and-attendance problem |
| No-go | A general multi-country school ERP does not pass this gate |
| Revise if | A later interview round shows the coaching due-list is not a shared job. Return to segment choice rather than adding modules |

## Phase 1. Customer validation

| | |
| --- | --- |
| Objective | Test the dues problem, the price, and the willingness to pilot with people who are not the founder |
| Deliverables | Notes from 12 interviews using [customer-validation-plan.md](customer-validation-plan.md), a price tally, and a written pass or fail |
| Duration | 3 to 5 weeks |
| Dependencies | Phase 0. Access to Dhaka centres. No product build |
| Acceptance | At least two independent owners describe the same dues failure and agree to a paid pilot on one batch |
| Risks | Leading questions. Counting compliments. Interviewing only friends |
| Go | The strong-signal rule in the validation plan is met |
| No-go | Stop the project under the stop rules. Do not open a code repository for the product |
| Revise if | The pain is real and the price ceiling is BDT 999, or the kindergarten contrast is stronger than coaching. Update the positioning document and repeat a smaller interview set before any build |

## Phase 2. Product definition

| | |
| --- | --- |
| Objective | Freeze an MVP that one developer can build and that the interviewed owners would pay for |
| Deliverables | A short PRD taken from [mvp-roadmap.md](mvp-roadmap.md) and [product-positioning.md](product-positioning.md), the user journey for the fee loop, and the price that was actually accepted |
| Duration | 1 to 2 weeks |
| Dependencies | Passed Phase 1. The accepted price and the rejected features are known |
| Acceptance | The MVP is the fee loop plus attendance, import, export, audit, and backup. Anything else from the interviews is either P1 with a named owner or explicitly refused |
| Risks | Writing the owners’ entire wish list into P0 |
| Go | One coherent workflow, buildable in the roadmap’s 11 to 15 implementation weeks, at a price that is not below the support floor |
| No-go | The only version owners will buy includes payroll, board report cards, or multi-branch administration |
| Revise if | The accepted workflow is attendance-only and fees are not the pain. The product definition changes and Phase 1 is repeated for that narrower job |

## Phase 3. Architecture and prototype

| | |
| --- | --- |
| Objective | Show the due list and the receipt on a clickable prototype, and freeze the tenant and ledger rules |
| Deliverables | Domain sketch, role matrix, tenant approach, and a prototype an owner can click. No production student data |
| Duration | 2 weeks |
| Dependencies | Passed Phase 2. The technical rules in [technical-feasibility.md](technical-feasibility.md) |
| Acceptance | Two target users, ideally the future pilot owners, can complete the main path on the prototype without the founder explaining every control. They can also say what is missing. A missing live bKash button is not a failure if manual reference entry is acceptable to them |
| Risks | Polishing a prototype into a secret rewrite of the whole ERP |
| Go | Users complete the path, and the ledger rules still match Phase 2 |
| No-go | Users cannot recognise their own fee desk in the prototype |
| Revise if | They need a different receipt or a different batch structure. Change the prototype. Do not add hostel or exams to rescue a confusing screen |

## Phase 4. MVP implementation

| | |
| --- | --- |
| Objective | A hosted build that passes the money tests and the backup drill |
| Deliverables | The P0 application, automated tests listed in the technical note, a staging environment, a restore rehearsal, and a field list suitable for a privacy review |
| Duration | 9 to 13 weeks after the prototype, inside the overall 11 to 15 week build judgement |
| Dependencies | Passed Phase 3. Counsel has been asked to review the pilot’s data handling under the Personal Data Protection Act, 2026 before real student data is loaded. This research did not perform that review |
| Acceptance | The partial-payment case, tenant isolation, teacher denial on payment routes, idempotent import, and a successful restore all pass. Receipt totals and the due list use the same balance |
| Risks | Financial errors, cross-tenant access, untested backups, scope added during the build |
| Go | Those checks pass and no P2 module has entered the build |
| No-go | Money tests fail, or the only way to make a centre happy is custom code that other centres cannot use |
| Revise if | A test fails because the fee rule from Phase 1 was misunderstood. Fix the rule. Do not widen the product |

## Phase 5. Pilot

| | |
| --- | --- |
| Objective | Learn whether a real centre will pay and will record payments without daily founder help |
| Deliverables | At most two paying centres, import notes, weekly activity, defect list, support-hour log, and a price confirmation or a price change |
| Duration | 6 to 8 weeks, including the first full collection cycle |
| Dependencies | Passed Phase 4. Paid agreements. Real data only after the privacy review agreed in Phase 4 |
| Acceptance | Each pilot centre records payments in week two without the founder present for every receipt. The owner agrees a five-student spot check. Support stays within three hours in a week after import. The centre is willing to pay for a second month |
| Risks | Founder operating the product on their behalf. Data-import mistakes. Churn after the first visit |
| Go | Both pilots meet the acceptance line, or one meets it and the second failure is a defect that is fixed rather than a refusal to pay |
| No-go | Centres stop using the ledger, or they will continue only if support is effectively a full-time clerk |
| Revise if | They pay and use it, and the next most common request is a single P1 item such as a due reminder. That item can be specified. It does not approve an app or a grading engine |

## Phase 6. Commercial launch

| | |
| --- | --- |
| Objective | Accept a small number of new centres without inventing a new service for each one |
| Deliverables | A public demo using fictional data, a price page that matches what pilots pay, backup monitoring, a support boundary, and a short operator guide |
| Duration | 3 to 4 weeks after a passed pilot |
| Dependencies | Passed Phase 5. Measured support hours |
| Acceptance | A new centre can be imported and left to record payments using the written guide. The founder’s support time for a new centre is under the assumption used in the pricing document, or the price is raised until it is |
| Risks | A public launch that invites every feature request at once. Advertising compliance that has not been reviewed |
| Go | The acceptance line is met for at least one centre that was not a design partner |
| No-go | Every new centre needs the founder in the office |
| Revise if | Acquisition is the constraint and the product itself is used. Change the recruiting method. Do not add modules as a substitute for visits |

## Phase 7. Expansion

| | |
| --- | --- |
| Objective | Add a module, a segment, or a second commercial channel only when current customers have earned it |
| Deliverables | A one-page case for the expansion: who asked, what they pay, what it will do to support, and what it will not include |
| Duration | Depends on the change. A P1 reminder is weeks. A kindergarten grading engine is a new Phase 2 |
| Dependencies | Passed Phase 6. At least 15 paying centres before a self-hosted or CodeCanyon channel is even proposed |
| Acceptance | The expansion uses evidence from paying centres. It does not reopen CodeCanyon, Nepal, English-medium curricula, or multi-branch UI on the original ambition alone |
| Risks | The second product destroys the simplicity that made the first one supportable |
| Go | The written case meets the pricing document’s rule for a second channel, or a P1 feature has more than one paying centre asking for the same behaviour |
| No-go | The proposal is “we should also support schools, madrasas, and another country” |
| Revise if | Kindergartens want the same fee desk and not a new report-card system. That expansion can be a packaging change. If they want board marksheets, it is a new product decision and returns to Phase 1 for that segment |

## What is not approved today

Phase 0 is complete. Phases 1 through 7 are not approved. The next action is interviews, not a repository of application code.
