# Pricing and unit economics

Every total in this document is an **illustration under stated assumptions**. It is not a forecast of sales, churn, or profit. Access date for competitor prices: 24 October 2026. Sources are linked in [competitor-matrix.md](competitor-matrix.md) and [sources.md](sources.md).

Currency note: an illustrative rate of **120 BDT per 1 USD** is used only so a reader can compare ladders. The spot rate on 24 October 2026 was **not verified**. Do not use the converted figures as quotes.

## 1. What the market already publishes

### Bangladesh, hosted or local

| Offer | Published price | Implied monthly, roughly |
| --- | --- | --- |
| Pathshala software | BDT 500 / 700 / 1,200 per month | As listed. App bundles go higher |
| CampusQ | BDT 499 / 1,399 / 2,499 per month | As listed, with student caps |
| ClassTablet | BDT 20 per student, starter BDT 499 | A 100-student centre would be BDT 2,000 if the per-student claim is applied literally. That arithmetic is ours, not a quote |
| EduZone | BDT 12,000–49,999 per year, or BDT 5 per active student per month | About BDT 1,000–4,167 per month on the annual bands |
| EduSoft | BDT 2,999 per month after a free tier | As listed. SMS is a custom plan |
| SchoolSoftBD | BDT 7 or 12 per student per month | A 200-student school is BDT 1,400 or 2,400. Our arithmetic |
| MicroCampus and Aara | BDT 35,000–85,000 one-time | Not a monthly comparison without an assumed life. Not assumed here |
| Apps Maker BD | From BDT 45,000 once | A project, not a subscription |

### International, hosted

| Offer | Published price | What a flat $29 / $79 / $149 plan would mean |
| --- | --- | --- |
| QuickSchools | $0.99–$2.99 per student per month, 30-student minimum | $29 covers about 10–29 students at those rates, which is near or below their minimum. $149 covers about 50–150 students |
| Sycamore | $4 per student per month | $149 covers about 37 students. A 150-student school is $600 |
| iSAMS | Directory listing from £6,000 per year | Not comparable to a self-serve $79 plan |
| Veracross | Quote only | No public number to beat |
| EduSaaS Pakistan | Rs 1,499 per month on the vendor site for the paid tier shown | Same shape as a low flat fee, in another country |

### CodeCanyon scripts

Established school scripts are listed at $50–$89. The Node/TypeScript listing found at $99 had 3 sales. From 1 July 2026, Envato’s author fee is 50% of the **item-price component**, and exclusivity no longer applies. Sources: [author hub](https://author.envato.com/hub/changes-to-envato-market-revenue-share-and-exclusivity-what-you-need-to-know/), [earnings](https://help.author.envato.com/hc/en-us/articles/360000472943-Introduction-to-Earnings).

**Assumption, labelled:** the tables below treat the displayed script price as the item-price component. If Envato adds a buyer fee on top, the author still receives 50% of the item-price component, not 50% of everything the buyer pays. The exact buyer-fee formula was not recalculated from a rates schedule in this research.

## 2. Bangladesh SaaS hypothesis

These tiers are for the coaching product, not for a full school ERP. They are hypotheses to show in interviews. They are not a price list.

| | Batch | Centre | Academy |
| --- | --- | --- | --- |
| Monthly price | BDT 999 | BDT 1,999 | BDT 3,999 |
| Annual price, if two months are waived | BDT 9,990 | BDT 19,990 | BDT 39,990 |
| Active students included | 40 | 150 | 400 |
| Campuses | 1 | 1 | 1 |
| Included | Students, batches, attendance, fees, partial payments, receipts, due list, export | Same, plus more than one batch and a clerk user | Same, plus a rehearsed import session |
| SMS | Not included | Not included | Not included |
| Live bKash API | Not included | Not included | Not included |
| Setup | BDT 0 if the owner imports a sample file | BDT 5,000 if the founder imports one batch. Waived when the first year is prepaid | BDT 10,000 import, waived on annual prepay |
| Support | Email or WhatsApp on business days, product defects only | Same. No on-site visits | Same. No custom reports |
| Overage | Stop adding students, or move up a tier. Do not silently charge per student until a per-student price has been tested | Same | Same |

Why these caps: CampusQ’s published caps are 75, 250, and 750 students at BDT 499, 1,399, and 2,499. Matching their caps at a higher price would lose the comparison. Smaller caps make BDT 1,999 a centre plan rather than a discount against CampusQ’s top tier. Whether owners accept that is **Unknown**.

Why SMS is excluded: EduZone includes only six SMS per student per year and still charges for the software. SMS gateways have a per-message cost this research did not price. Bundling an unlimited SMS promise is a way to lose money. A later add-on can pass the gateway cost through.

Why BDT 3,999 is doubtful: it is above CampusQ’s highest published monthly plan and above Pathshala’s highest software-only monthly price. It should be offered in interviews as a ceiling, not as the expected tier. If nobody chooses it, delete it.

### Buyer and unit

The buyer is the centre owner. The pricing unit is the centre per month, with a student cap, not a national per-student meter. Per-student pricing exists locally (EduZone, ClassTablet, SchoolSoftBD). It punishes a centre for growing and it is harder to explain. It can be revisited if owners reject flat tiers.

### Cost assumptions for one hosted product

| Item | Assumption | Status |
| --- | --- | --- |
| App and database hosting | BDT 3,000 per month until 50 paying centres, then BDT 8,000 | Illustration. No vendor quote attached |
| Error tracking and backups | BDT 1,500 per month | Illustration |
| Payment collection for the subscription itself | bKash merchant or a manual transfer. Merchant discount rate **not verified**. Model it as 1.5% of collected subscription revenue | Assumption. Replace when a schedule exists |
| SMS | BDT 0 in the base product | Decision |
| Founder support time | 1 hour per paying centre per month | Assumption to stress-test. A well-scoped product should be lower |
| Founder time valued at | BDT 500 per hour | Assumption for contribution math only. It is not a salary the business pays |
| VAT | EduZone’s page says prices exclude VAT. The rate and whether this SaaS must charge it were **not verified**. Tables below are before VAT | Unknown |
| Annual prepay share | Not assumed in the monthly snapshots | Unknown |

### Contribution at the Centre tier

Formula, all assumptions: `centres × 1,999 × (1 − 0.015) − hosting − tooling − centres × 500`.

| Paying centres | Subscription cash | After 1.5% collection assumption | Hosting + tooling | Support time at BDT 500 | Left, before VAT and before unpaid build time |
| ---: | ---: | ---: | ---: | ---: | ---: |
| 10 | 19,990 | 19,690 | 4,500 | 5,000 | 10,190 |
| 25 | 49,975 | 49,225 | 4,500 | 12,500 | 32,225 |
| 50 | 99,950 | 98,451 | 9,500 | 25,000 | 63,951 |
| 100 | 199,900 | 196,902 | 9,500 | 50,000 | 137,402 |

At 10 centres the leftover is about BDT 10,000 a month under these assumptions. That does not pay back the build. At 50 centres the leftover is meaningful only if support really stays near one hour and the founder is not also building the next module. If support is 3 hours per centre, the 25-centre case falls by another BDT 25,000 and the leftover is about BDT 7,000. **That is the sensitivity that matters.**

### If every centre is on Batch at BDT 999

The 50-centre leftover becomes `50 × 999 × 0.985 − 9,500 − 25,000`, which is about BDT 14,700. Fifty small centres on the cheap tier do not support a solo business under the one-hour assumption.

### Break-even illustration

Fixed monthly cost in the model is hosting plus tooling, BDT 4,500 at the small scale. Variable cost is 1.5% plus BDT 500 support. Contribution per Centre-tier customer is about `1,999 × 0.985 − 500 = 1,469`. Fixed cost divided by that is about **4 centres** to cover hosting only. To cover hosting plus a notional BDT 80,000 per month for the founder’s living cost, the same tier needs about `(4,500 + 80,000) / 1,469 ≈ 58` centres. The BDT 80,000 living cost is an **assumption**, not a measured personal budget. If the reader’s required income is different, the centre count moves in proportion.

### Churn illustration, not a prediction

No local churn study was found. If 5% of centres leave each month and none are replaced, 50 centres become about 28 in 12 months (`50 × 0.95^12`). If new sales exactly replace leavers, the stock stays at 50 and the founder’s time goes to replacement rather than to product. Both statements are arithmetic, not a forecast. Interviews must ask how long owners kept their last tool.

### Scenarios

| Scenario | What is assumed | 12-month picture |
| --- | --- | --- |
| Conservative | 8 centres, all on BDT 999, 1.5 hours of support each, no annual prepay | Subscription cash about BDT 8,000 a month. Support time alone is BDT 6,000 at the BDT 500 valuation. The product does not pay for itself |
| Base | 25 centres on BDT 1,999, 1 hour support, hosting as above | About BDT 32,000 a month left before living costs and VAT, from the table. A living, not a funded company |
| Optimistic | 80 centres, mix of 1,999 and 3,999 averaging BDT 2,500, support falls to 0.4 hour because the product is stable | Cash about BDT 200,000 a month before collection fees. Support valuation about BDT 16,000. This requires a sales channel this research did not find |

The optimistic row is the one to distrust. Nothing in the competitor sales data for a new product supports 80 centres in year one.

## 3. International SaaS hypothesis

Do not launch these prices. They are here because the brief asked for them.

| Test price | Problem |
| --- | --- |
| USD 29 per school per month | About BDT 3,480 at the unverified 120 rate, already near the top of the Bangladesh ladder, and far below QuickSchools or Sycamore for any real enrolment. Too high for the recommended Dhaka buyer if converted, too low for a US school that needs support |
| USD 79 | About BDT 9,480. No Bangladesh coaching price in this research sits there. For a US school it buys a tiny fraction of Sycamore’s per-student bill and none of the support those schools expect |
| USD 149 | About BDT 17,880. Same mismatch |

A later international price, if Nepal or a similar market is ever validated, should be rebuilt from local competitors. It should not be a translation of the US SIS market. Card fees, refunds, and chargebacks are **not modelled** because this plan does not sell there.

## 4. CodeCanyon hypothesis

| Listed price treated as item price | Author fee 50% | Net before tax and before support |
| ---: | ---: | ---: |
| $79 | $39.50 | $39.50 |
| $89 | $44.50 | $44.50 |
| $99 | $49.50 | $49.50 |

Support assumption: 3 hours in the first six months per buyer, because the captured support pages show that buyers ask for installation even when the policy excludes it. Value that hour at $20. Cost is $60, which is already above the net on a $99 sale.

| Sales per month | Gross at $89 | Net at 50% | Support at 3 hours and $20 | Left |
| ---: | ---: | ---: | ---: | ---: |
| 2 | $178 | $89 | $120 | −$31 |
| 5 | $445 | $223 | $300 | −$78 |
| 10 | $890 | $445 | $600 | −$155 |
| 20 | $1,780 | $890 | $1,200 | −$310 |

Under this support assumption the line never turns positive, because each sale costs more in time than it returns. It turns positive only if support falls below about 2.2 hours at $20, or the founder values the hour below about $15 and keeps support at 3 hours. New listings in this category do not have a verified path to 20 sales a month. Mighty School, updated and priced at $29, showed 66 sales after about a year. Samyotech showed 3 sales at $99. Those are history, not a projection for this founder.

Extended-licence multiples and support renewals can add revenue. The amounts were **not verified** on the school items captured, beyond ScriptMint’s direct-store support renewal shown at $49 per year. They are not included in the table.

A premium CodeCanyon price is not justified. The buyers who pay $50–$89 already receive a mature PHP system. A $99 TypeScript product has not demonstrated demand.

## 5. Acquisition, tax, and maintenance

Customer acquisition cost was **not measured**. The validation plan assumes in-person visits in Dhaka, which cost time rather than ads. If paid ads are required later, the contribution table is incomplete until that cost is known.

Income tax and VAT are **Unknown** in amount. EduZone states that VAT is extra. A model that ignores VAT overstates what the founder keeps. Replace the placeholder when an accountant gives the rate.

Ongoing development is not in the monthly contribution table. The MVP estimate in [mvp-roadmap.md](mvp-roadmap.md) is 11 to 15 build weeks after interviews and a prototype. Those weeks are unpaid labour. A one-time CodeCanyon spike does not fund them either.

## 6. Which model to launch, and when a second model appears

**Launch hosted SaaS in Dhaka, or launch nothing.** The Centre tier at BDT 1,999 is the price to test. BDT 999 is the floor that still has local precedent and, in the illustration, does not support the founder. BDT 3,999 is a probe.

**Do not launch on CodeCanyon first.** The fee, the support pattern, the shared-hosting expectation, and the feature bar all work against a new Next.js product. A second channel is allowed only after all of the following:

- At least 15 centres are paying for the hosted product.
- Support time per centre has been measured and is under one hour a month.
- A buyer who is not a school, such as a local implementer, asks for a self-hosted licence in writing.
- Counsel has read the current Envato licence if the channel is CodeCanyon, or a direct licence is used instead.

The better second channel, if one is ever needed, is a **direct self-hosted licence** with a named annual update fee, sold to one implementer at a time. That avoids the 50% marketplace fee. It is still a worse business than hosted SaaS until the product is stable, because each install is a support relationship. It should not be opened in the first year on hope.

Hybrid “script plus SaaS plus apps plus add-ons”, which is what QDOCS, Creativeitem, and CodeThemes already do, is the incumbent model. Copying it at the start means copying their support burden without their sales base.
