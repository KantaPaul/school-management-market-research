# Customer validation plan

No interviews were conducted for the market documents. This plan is the next piece of work. It is also a gate. Building the application before the stop-or-continue rules below are applied is a decision to ignore the research.

The target buyer is a coaching-centre or tuition-academy owner in Dhaka. Kindergarten owners are interviewed only as a contrast, to see whether the same fee problem is real outside coaching. They are not a second pilot group yet.

## 1. Sample

| Group | Target interviews | Why |
| --- | ---: | --- |
| Coaching or tuition owners who collect monthly fees | 8 | Primary segment |
| Owners of small private kindergartens or primary sections | 4 | Tests whether the second segment has the same job |
| Total | 12 | Enough to notice a repeated story. Not a statistical sample |

Stop recruiting after 12 completed interviews, or earlier if the stop rules are already met and further conversations are only friendlier versions of the same refusal.

A completed interview lasts at least 25 minutes and answers the current-tool and price questions. A chat that stays on opinions does not count.

## 2. How to recruit

- Visit centres in two or three Dhaka neighbourhoods. Ask for the person who checks which students have paid.
- Ask each respondent for one other owner who would disagree with them.
- Do not interview only friends, relatives, or people who have already said the idea is good.
- Do not pay for the interview. A paid pilot later is a different event.
- Tell them the conversation is research and that no product is being sold that week.

If two weeks of attempts produce fewer than eight owner conversations, that fact is a result. Record it. Do not replace owners with teachers to fill the quota.

## 3. How to ask

Ask about the last month, not about a hypothetical perfect system. Do not ask “would you use a modern all-in-one school ERP?” Do not describe Next.js, PostgreSQL, or AI. Do not say “other owners struggle with fees” before they have described their own month.

When a price is tested, give the three numbers and ask which, if any, they would pay. Do not follow a “no” with a lower number in the same breath. The lower number can be a separate question after they have answered.

## 4. Questions for owners

1. What did you use last month to know which students still owed fees?
2. How many students are active, and how many batches?
3. Who is allowed to receive cash or a bKash transfer?
4. Tell me about the last time a guardian said they had paid and you could not find it quickly. What did you do that day?
5. How do partial payments work today? What do you write down?
6. What did you pay in the last year for any software, SMS, or a person who maintains a spreadsheet? What was the amount?
7. Who can decide to pay for a tool like this?
8. What would you need to see in the first week before you would put this month’s fees into it?
9. Here are three monthly prices for one centre, without an Android app and without a live bKash connection: 999, 1,999, and 3,999 taka. Which, if any, would you pay, and what would you refuse to pay for?
10. If you did not buy, what would you keep using?

## 5. Questions for accountants and clerks

Ask these only when the owner is not the person who writes the receipt.

1. How many receipts did you write on the last collection day?
2. Where do bKash references get stored?
3. What happens when someone pays half now and half next week?
4. Which mistake is the most annoying to correct?
5. What would make this slower than the register?

## 6. Questions for teachers

1. How do you mark attendance today, and how long did the last batch take?
2. Do you see who has not paid? Should you?
3. What do guardians ask you that you have to forward to the office?

Teachers are not the economic buyers. A teacher who loves the product and an owner who will not pay is a weak signal.

## 7. Questions that map to the brief

| Topic | Question that does not lead |
| --- | --- |
| Current software | What did you open last week, if anything, when a guardian asked for a receipt? |
| Workarounds | What is on paper because the current tool does not do it? |
| Budget and authority | What was the last tool or service this centre paid for, what did it cost, and who agreed? |
| Switching cost | What would you have to copy across before you trusted a new list? |
| Migration | How many students would have to be entered before the tool was useful? Who would type them? |
| Recurring problems | What fee or attendance problem happened more than once in the last term? |
| Price | The 999 / 1,999 / 3,999 question above, asked after the cost of the current method, not before |

## 8. What counts as a strong buying signal

All of the following, from the same owner:

- They name the current tool or the current paper process.
- They describe a specific dues or receipt failure from the last three months.
- They state a current or recent cost, even if that cost is a clerk’s time.
- They identify themselves as the person who can pay.
- They agree to a paid pilot on one real batch, at a stated monthly price, with a start month.

A strong study has this pattern from **at least two owners who do not work at the same centre** and who were not introduced by each other as a single buying group.

## 9. What counts as weak interest

- “This is a good idea.”
- A feature list that includes payroll, hostel, transport, a website, and an app.
- Willingness to try it if it is free, or if the founder sits in the office and operates it.
- A teacher who is enthusiastic and an owner who will not attend.
- Praise for the technology stack.
- One owner who wants a pilot and seven who are being polite.

Weak interest is not a prompt to add features. It is a prompt to stop or to change the segment.

## 10. Pilot acceptance criteria

A pilot is accepted only when:

- The centre pays. A free pilot does not count, because the pricing question is the thing being tested. The amount can be the Batch tier if that is what they signed, and the notes must say so.
- One real batch is imported by the centre or by the founder from the centre’s own list.
- In the second week, the centre records payments without the founder present for every receipt.
- The owner can point to the due list and agree that it matches their own check of five students.
- Support time is logged. More than three hours in a week, excluding the initial import, fails the sustainability check for adding another centre.

Run at most **two** pilots at once.

## 11. When to revise the product

Revise the offer, and do not start a wider build, if:

- Owners confirm the dues problem and reject every price above BDT 999.
- They will pay only if SMS is included, and a gateway quote shows that the included volume costs more than the subscription.
- Kindergarten owners have the pain and coaching owners do not. The primary segment flips, and the scoring note is updated. The MVP still does not gain a grading engine unless those owners refuse to pay without a specific report.

A revision is a written change to the positioning document. It is not a quiet addition of modules.

## 12. When to stop

Stop the project if any of these is true after the interview round:

- Fewer than two independent owners will pay for a pilot.
- The owners who will pay require payroll, library, transport, hostel, or custom board report cards before they pay.
- The price they will actually pay is below the floor at which the pricing document’s support assumption leaves a negative contribution. With the stated assumptions, a centre that will only accept a free tool, or a one-time fee under BDT 10,000 with unlimited support, is a stop.
- Eight coaching interviews produce eight different jobs and no shared dues workflow.
- Counsel reviews the Personal Data Protection Act, 2026 and advises that a pilot cannot be run on the terms the founder can actually meet. That advice was not obtained during this research. It is a condition, not a conclusion that the law forbids the product.

Stopping means no application repository is opened for this product. The research documents remain the record of why.
