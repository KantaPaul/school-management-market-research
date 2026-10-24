# Risk register

Scores are judgements made on 24 October 2026. Probability and impact are High, Medium, or Low. The owner of every row is the solo founder, because there is nobody else. Approval gates are defined in [phase-approval-gates.md](phase-approval-gates.md).

## 1. Register

| Risk | Probability | Impact | Early warning | Mitigation | Gate affected |
| --- | --- | --- | --- | --- | --- |
| Market saturation in general school ERP | High | High | Interviews name Pathshala, CampusQ, a local developer, or “my nephew installed a script” in the first five conversations | Do not build the general ERP. Sell only the coaching due-list if the interviews agree | Phase 1 |
| Weak differentiation | High | High | Owners like the idea and cannot say what they would stop using | The pilot must replace a named current method. A second general menu is not differentiation | Phase 1 and 2 |
| Price competition | High | High | Respondents anchor at BDT 500 or “free if you install it” | Test 999 / 1,999 / 3,999 before arguing. Stop if the acceptable price is below the support floor in the pricing document | Phase 1 |
| Low customer acquisition | High | High | Fewer than eight owners will sit for an interview after two weeks of visits | Dhaka visits and referrals only. Do not buy ads to hide a refusal to talk | Phase 1 and 5 |
| High customization demand | High | High | The first two interviews ask for payroll, hostel, board cards, or a custom app before discussing dues | Write those requests down as out-of-scope. If they are required to get a signature, this segment is wrong | Phase 1 and 2 |
| Excessive support burden | Medium | High | A pilot needs daily WhatsApp help to record a payment | Time-box support. If one centre exceeds 3 hours in a week for ordinary use, halt more pilots | Phase 5 |
| Data migration errors | Medium | High | The sample import creates duplicate students or wrong opening balances | Idempotent import, a counted error report, and no production import without a rollback | Phase 4 and 5 |
| Financial calculation errors | Medium | High | A receipt total disagrees with the due list on a constructed case | Integer poisha, append-only payments, the partial-payment test, no second formula in reports | Phase 4 |
| Unauthorized data access | Low | High | A cross-tenant test fails, or a teacher can open a fee route | Row-level security and server-side role tests before any real student row | Phase 4 |
| Data loss | Low | High | A backup job fails and nobody notices | Restore drill before go-live. Alert on backup failure | Phase 4 and 6 |
| Local payment integration delays | High | Medium | bKash or an aggregator has not issued production credentials | Do not put live checkout on the critical path. Record references manually | Phase 4 |
| Privacy and regulatory obligations | Medium | High | A pilot wants photos, ID numbers, and SMS to minors with no guardian record | Minimise fields. Read the Personal Data Protection Act, 2026 with counsel before real data. Do not claim compliance in the sales pitch | Phase 4 and 5 |
| CodeCanyon licensing and economics | High, if that channel is opened | High | A plan appears to “upload the script and see” | Do not open the channel first. Author fee is 50% of the item-price component. Licence type must be read before any marketplace sale | Phase 7 |
| SaaS churn | Medium | High | Centres go quiet after the first month, or refuse annual prepay and also refuse month two | Measure activity weekly in the pilot. A centre that does not record payments in week two is not a reference | Phase 5 |
| Solo-developer dependency | High | High | Holidays, illness, or a second client project stop replies | Cap the number of pilots at two until support time is measured. Write the restore steps so a break is not a data loss | Phase 5 and 6 |
| Scope expansion | High | High | “Small” additions land in the P0 list: timetable, exams, SMS, app | P0 is the workflow in the roadmap. New work needs a pilot example and a gate review | Phase 2 and 4 |

## 2. The five risks most likely to kill the business

These are the failures that make the next year a loss even if the code is elegant.

1. **Building a general school ERP into a saturated brochure.** Smart School alone has about 6,100 CodeCanyon sales and a decade of modules. Dhaka vendors already sell hosted systems from a few hundred to a few thousand taka a month. A new all-in-one product does not have a buyer who is waiting for Next.js.

2. **A price ceiling below the cost of support.** CampusQ lists BDT 499–2,499. ClassTablet leads with BDT 499 and a per-student claim. If owners will not pay around the BDT 1,999 test price, the contribution table in the pricing document does not work at a small number of centres.

3. **Customization and hand-holding become the product.** Local sales are personal. The founder who agrees to on-site training, custom marksheets, and a private feature for each centre has taken a services job with SaaS expenses.

4. **A wrong balance in a real centre.** Fee software dies on trust. One receipt that does not match the due list is enough for an owner to go back to the register and tell other owners. This risk is less probable than saturation if the ledger tests are actually written, and the impact is still fatal to the reference customer.

5. **The founder is the only operator.** Acquisition, import, defects, backups, and the next feature are the same person. Two noisy pilots can stop all sales. This is structural. The mitigation is a hard cap on pilots and a refusal to add modules during the pilot, not a plan to “hire later” with revenue that does not yet exist.

CodeCanyon economics would join this list on the day that channel is treated as the launch. It is not in the top five only because the recommended plan does not launch there.

## 3. Risks that are serious and still not a reason to add scope

Live bKash approval can be slow. Manual references are an acceptable first version, and several centres already operate that way. Nagad’s official API terms were not verified. That uncertainty is a reason to wait, not a reason to promise both wallets in the first demo.

Privacy law is a reason to collect less and to get advice before a pilot. It is not a reason to market “compliant school ERP”.

International competitors with five-figure contracts are not a launch risk. They become a risk only if the roadmap drifts toward those buyers without a support plan.
