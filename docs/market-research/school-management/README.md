# School management product: decision

**Verdict: PROCEED WITH CONDITIONS.**

Do not spend the next 3–6 months building a general School Management System. The evidence supports a much narrower product, and only after paid-pilot interviews. If those interviews fail the rules in [customer-validation-plan.md](customer-validation-plan.md), stop.

Research date: 24 October 2026. No application code was written. No school or coaching-centre interviews were conducted. Figures are snapshots from the cited pages, not a forecast. The source log is [sources.md](sources.md).

## Documents

| Document | What it decides |
| --- | --- |
| [market-analysis.md](market-analysis.md) | Bangladesh and international evidence, payments, and privacy limits |
| [competitor-matrix.md](competitor-matrix.md) | CodeCanyon, local vendors, and why a new stack is not a sales argument |
| [customer-segments.md](customer-segments.md) | Scores for six segments and the weight sensitivity |
| [product-positioning.md](product-positioning.md) | The selected sentence and the two positions that were rejected |
| [mvp-roadmap.md](mvp-roadmap.md) | P0 fee-and-attendance loop. Everything else is deferred |
| [mockup-plan.md](../../design/mockup-plan.md) | Screen map and next-cms-style file tree for a later due-list prototype. Does not approve application code |
| [pricing-and-unit-economics.md](pricing-and-unit-economics.md) | Illustrative prices and contribution. Not a sales forecast |
| [technical-feasibility.md](technical-feasibility.md) | Hosted modular monolith. No existing codebase was inspected |
| [risk-register.md](risk-register.md) | Risks and the five most likely ways the business fails |
| [customer-validation-plan.md](customer-validation-plan.md) | Interview script and stop rules |
| [phase-approval-gates.md](phase-approval-gates.md) | Phase 0 is done. Phases 1–7 are not approved |
| [sources.md](sources.md) | URLs, dates, and conflicts |

## 1. Verdict

**PROCEED WITH CONDITIONS.**

A commercial school product is not rejected outright. Institutions in Bangladesh already pay for software, at published prices. A downloadable full ERP and a multi-country hosted ERP are rejected as the first build. The conditional path is a hosted fee, attendance, and receipt product for Dhaka coaching centres, started only if two independent owners agree to pay for a pilot.

## 2. Evidence behind the verdict

- CodeCanyon is already served by maintained PHP products at $50–$89. Smart School (QDOCS) was listed at $89 with about 6,113 sales and an update on 11 August 2026. Ekattor’s CodeIgniter line was about 3,790 sales at $50. Inilabs School Express was about 2,378 sales at $59. InfixEdu was 1,503 sales at $67. Sources are the item pages linked in [competitor-matrix.md](competitor-matrix.md).
- Newer listings are not catching that history on the strength of a stack. Ekattor 8 (Laravel) had about 547 sales at $55. Mighty School had 66 sales at $29 after about a year. A Node.js, TypeScript, and React school ERP at $99 had 3 sales, and its listing says it will not run on shared hosting.
- From 1 July 2026 Envato’s author fee is 50% of the item-price component, and exclusivity has ended. A $79–$99 script does not fund install support under the assumptions in the pricing document.
- Bangladesh vendors already publish low prices: Pathshala at BDT 500–1,800 per month, CampusQ at BDT 499–2,499, EduZone at BDT 12,000–49,999 per year or BDT 5 per student per month, ClassTablet from BDT 499, and one-time offers around BDT 35,000–85,000. The brief’s BDT 999–3,999 ladder is inside this range, not above it.
- BANBEIS figures reported by Prothom Alo for 2025 show a large system and a small English-medium set: 19,211 secondary schools, 9,296 dakhil-and-above madrasas, and 143 English-medium schools. English-medium enrolment is reported as 29,672 by Prothom Alo and 79,589 by bdnews24. Both are cited. Neither turns 143 schools into a solo-founder market.
- bKash documents a merchant API and an education onboarding form. Production access needs an agreement. SSLCOMMERZ’s integration document includes bKash. Nagad was not in that fetched document, and an official current Nagad API was not verified. Live wallets are not a first-release dependency.
- The Personal Data Protection Ordinance, 2025 was repealed by the Personal Data Protection Act, 2026. A product that stores children’s data needs a legal reading before a pilot. This research is not that reading.
- iSAMS, Veracross, QuickSchools, and Sycamore show that international school systems are priced and supported as a different business. A flat $29–$149 plan is not how those vendors sell, and a solo founder has no local team in those countries.

## 3. Strongest customer segment

Coaching centres and tuition academies. Weighted score 67.2 out of 100 under the base weights. Small private kindergartens scored 59.2 and are the later adjacent segment, not the first build. The score is a judgement. Several inputs are uncertain and marked in [customer-segments.md](customer-segments.md).

## 4. Initial geography

Dhaka. Not nationwide Bangladesh, and not an international launch. The founder can visit owners. National language, training, and connectivity problems wait until one city has paid.

## 5. Primary buying persona

The centre owner who reconciles cash and a personal bKash or Nagad inbox. Teachers and clerks use the product. They do not approve the spend unless they are also the owner.

## 6. Most valuable problem

Showing, for each batch, who has paid, who has paid in part, and who still owes, with a receipt that matches the due list. Attendance belongs in the same product because it is how the batch is run day to day. A full exam engine, payroll, and a parent super-app are not the first problem.

This problem is an **inference** from what local vendors bother to sell, plus the structure of a monthly tuition business. Interviews have not confirmed it. That is why the verdict is conditional.

## 7. Competitors and realistic differentiation

The competitor set for the recommended product is CampusQ, ClassTablet, paper registers, personal wallets, and local fixed-price developers. The competitor set for a general ERP also includes Pathshala, EduZone, MicroCampus, Aara, SchoolSoftBD, EduSoft, and the CodeCanyon PHP products above.

A realistic difference is a short due list, partial payments done correctly, Bangla and English receipts, and hosting so the owner never installs PHP. “Next.js, TypeScript, and PostgreSQL” is an implementation choice. It is not a reason for the owner to switch. “All-in-one”, “AI-powered”, and “more modules than Smart School” are not available as claims.

## 8. Business model for launch

Hosted SaaS, billed in taka, one centre at a time. The price to test is **BDT 1,999 per month** for up to 150 active students, with BDT 999 and BDT 3,999 used in the same conversation as a floor and a ceiling.

CodeCanyon is not the launch channel. A direct self-hosted licence is a possible later channel after at least 15 paying centres and measured support time. The marketplace’s 50% author fee and six-month support expectations make it a poor first business for this stack.

## 9. Proposed MVP

P0: centre and period, batches, students and guardians, staff, three roles, batch attendance, fee obligations, waivers, partial payments, receipts, a due list, collection report, spreadsheet import and export, append-only money audit, backup and a rehearsed restore.

P1, only after a pilot asks with an example: read-only guardian view, SMS reminders at gateway cost, simple test scores.

Not in the first release: accounting, payroll, library, transport, hostel, timetable solver, LMS, analytics, AI, multi-branch UI, native apps, live wallet APIs, board or Cambridge report cards, and other countries.

## 10. Pricing hypotheses

Illustrations, not forecasts. Full tables and the support-hour assumption are in [pricing-and-unit-economics.md](pricing-and-unit-economics.md).

- Bangladesh test prices: BDT 999, 1,999, and 3,999 per month. SMS and live bKash are not included. At the Centre tier, with an assumed 1.5% collection cost, BDT 4,500 hosting and tooling, and one support hour per centre valued at BDT 500, 10 centres leave about BDT 10,000 a month before living costs and VAT. About 58 centres at BDT 1,999 cover an **assumed** BDT 80,000 monthly living cost plus small-scale hosting. VAT was not verified.
- International $29, $79, and $149 flat prices should not be launched. They do not match QuickSchools or Sycamore, and they are high relative to published Bangladesh coaching prices at an illustrative and unverified 120 BDT per USD.
- CodeCanyon at $79–$99 nets about $39.50–$49.50 after a 50% author fee if the list price is the item price. Three hours of support at $20 already exceeds that net.

## 11. Solo-developer effort

| Work | Judgement | Assumption |
| --- | --- | --- |
| Interviews | 3 to 5 weeks | Owners will meet. If they will not, the project ends sooner |
| Product freeze and clickable prototype | About 3 to 4 weeks | Only after the interview gate |
| P0 implementation | 11 to 15 weeks | No payroll, exams, apps, or live payments. One developer who already knows the stack |
| Two-centre pilot | 6 to 8 weeks | Includes one collection cycle |

A disciplined narrow product can fit inside six months **only if** interviews pass quickly and scope stays on the fee loop. A general school ERP does not fit in six months for one person, and the market evidence says it should not be attempted even if it did. The weeks are not approved until Phase 1 passes.

## 12. Five largest business risks

1. Building another general ERP into a market that already has entrenched PHP scripts and cheap local subscriptions.
2. A price ceiling around a few hundred to a few thousand taka, below the cost of hands-on support.
3. Each centre demanding custom features and office visits until the founder is a service shop.
4. A receipt that does not match the due list, which ends trust with the first reference customer.
5. One person carrying sales, imports, defects, and backups, so two noisy pilots can stop the business.

Detail and the wider register: [risk-register.md](risk-register.md).

## 13. Required customer validation

Twelve interviews: eight coaching owners and four kindergarten owners. A strong signal is a named current method, a recent dues failure, a stated cost, and a paid pilot on one batch. At least two independent owners must meet that bar. Compliments, feature wishlists, and free trials are weak. The script and the stop rules are in [customer-validation-plan.md](customer-validation-plan.md).

## 14. Phase gates

Phase 0, this research, is complete and allows Phase 1 only. Phase 1 allows a product definition only if the paid-pilot rule is met. Implementation is Phase 4, after a prototype the target users can operate. Commercial launch is Phase 6, after support hours have been measured. Expansion, including CodeCanyon or another country, is Phase 7 and is not justified by this document. Gates: [phase-approval-gates.md](phase-approval-gates.md).

## 15. When this recommendation should change

| Change the verdict if | New verdict |
| --- | --- |
| Two independent coaching owners will not pay for a one-batch pilot, or they will pay only if payroll, hostel, transport, or board report cards are included | **REJECT** this product |
| Owners have the dues problem and will not pay more than BDT 999, and the support log from a single paid Batch-tier pilot stays under one hour a month | Stay conditional. Keep the narrow product and do not hire or add modules. Re-read the contribution table before a second centre |
| Kindergarten owners, not coaching owners, are the ones who will pay for the same fee desk | Keep the product. Change the first segment. Do not add a grading engine unless they refuse to pay without a specific report |
| A written legal review says a pilot cannot store the minimum student and guardian fields on terms the founder can meet | **REJECT** until the design can meet that advice |
| Fifteen centres are paying, support is measured, and an implementer asks for a self-hosted licence | Consider a second channel. Still not a reason to rebuild a 40-module ERP |
| The goal remains a multi-country school ERP for English-medium and international schools | **PIVOT** is the wrong word. **REJECT** that plan on the current evidence. It needs a team, a support country, and a price point this research did not find a way to serve |

## Answer

Given the available evidence, a solo developer should **not** invest the next 3–6 months in building a general school-management product.

The developer should spend the next 3–5 weeks interviewing Dhaka coaching-centre owners. Only if at least two independent owners agree to pay for a pilot should the following months go into a narrow fee, attendance, and receipt product. If that condition fails, abandon the opportunity. Do not rescue it by widening the product to madrasas, Bangla-medium board schools, English-medium curricula, or a CodeCanyon script.

The main uncertainty is willingness to pay. Published competitors already sell the neighbourhood of this product for BDT 499–2,499 a month. It is possible that the dues problem is real and still not painful enough to switch. That is exactly what the interviews are for. It is not a reason to start coding while the question is open.
