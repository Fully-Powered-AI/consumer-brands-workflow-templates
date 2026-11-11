# Trial: Dated stock exposure list, run on its invented example

- **Product:** Claude, run in Claude Code

Model: Claude Sonnet 5.5 (model ID claude-sonnet-5-5). The assistant that ran this trial did not write the template.

Date: 2026-11-10

The inputs are the invented example in `public/example.md` (Fernhollow Goods, a made-up small food and body-care brand). No client data was used.

## Inputs used

The settings (today 2026-11-16, YYYY-MM-DD dates, a 30-day horizon, the two role names), the stock-by-batch export (7 lines), the approved date list (1 batch), the retailer acceptance rules (5 rows) and the demand plan (9 lines), all from the "What the supply planner supplies" section of `public/example.md`. The example's own list was not read until after the output below was produced.

## What came out

The instruction block and output format were followed as written. This is the output in full.

```
DATED STOCK EXPOSURE LIST: Fernhollow Goods, as of 2026-11-16

For: Supply lead and Quality owner. Stock export: 7 lines (0 with zero quantity left out). Date key: 1 batch. Rules: 3 accounts. Demand plan: 9 lines. Horizon: 30 days. Date format: YYYY-MM-DD. Transit days: as supplied; 0 for Retailer C (blank, and its rule is not applied).
Lines: 7. Decision needed: 5 (5,150 cartons). Date not placed: 1 (5,000 each). No supply decision flagged: 1 (3,000 each).

1. Decision needed (earliest last dispatch date first)
FH-SP-03 Chilli oil 250 ml, batch C-0877, Warehouse 1: 150 cartons. Stated date 2026-11-02 (best before), from the export. Stated date passed 14 days ago.
  Retailer A: needs 90 days left plus 3 transit; last dispatch date 2026-08-01; missed by 107 days. Planned units from today: 400, of which 0 on or before that date. FLAG: missed.
FH-GR-01 Oat granola 400 g, batch G-0417, Warehouse 1: 1,200 cartons. Stated date 2027-01-15 (best before), from the export.
  Retailer A: needs 120 days left plus 3 transit; last dispatch date 2026-09-14; missed by 63 days. Planned units from today: 800, of which 0 on or before that date. FLAG: missed.
  Retailer B: needs 60 days left plus 4 transit; last dispatch date 2026-11-12; missed by 4 days. Planned units from today: 600, of which 0 on or before that date. FLAG: missed.
FH-SP-03 Chilli oil 250 ml, batch C-0921, Warehouse 1: 800 cartons. Stated date 2026-12-31 (best before), from the export.
  Retailer A: needs 90 days left plus 3 transit; last dispatch date 2026-09-29; missed by 48 days. Planned units from today: 400, of which 0 on or before that date. FLAG: missed.
FH-GR-01 Oat granola 400 g, batch G-0488, Warehouse 1: 2,400 cartons. Stated date 2027-03-20 (best before), from the export.
  Retailer A: needs 120 days left plus 3 transit; last dispatch date 2026-11-17; 1 day left. Planned units from today: 800, of which 400 on or before that date. FLAG: inside horizon.
  Retailer B: needs 60 days left plus 4 transit; last dispatch date 2027-01-15; 60 days left. Planned units from today: 600, of which 300 on or before that date. Not flagged: outside the 30-day horizon.
FH-GR-01 Oat granola 400 g, batch G-0488, Warehouse 2: 600 cartons. Stated date 2027-03-20 (best before), from the export.
  Retailer A: needs 120 days left plus 3 transit; last dispatch date 2026-11-17; 1 day left. Planned units from today: 800, of which 400 on or before that date. FLAG: inside horizon.
  Retailer B: needs 60 days left plus 4 transit; last dispatch date 2027-01-15; 60 days left. Planned units from today: 600, of which 300 on or before that date. Not flagged: outside the 30-day horizon.
Planned units are for the SKU and are shared by every batch of it; none is assigned to a batch.
The Quality owner confirms suitability and any restriction. The Supply lead approves any stock or production action.

2. Date not placed
FH-LB-02 Lip balm 4 g tin, batch L-310, Warehouse 1: 5,000 each. The export gives "2027-02" (month and year only) and the approved date list does not include this batch. No last dispatch date worked out. Answer from: Quality owner.

3. Open items
1. FH-SP-03 batch C-0877, Warehouse 1: stated date 2026-11-02 passed 14 days ago. Answer from: Quality owner.
2. FH-SP-03 batch C-0921, Warehouse 1: storage condition not stated. Answer from: Quality owner.
3. FH-LB-02 batch L-355, Warehouse 2: status "on hold", as supplied. Answer from: Supply lead.

4. No supply decision flagged
FH-LB-02 Lip balm 4 g tin, batch L-355, Warehouse 2: 3,000 each. Stated date 2027-09-30 (best before end), from the approved date list. Earliest last dispatch date 2027-04-01 (Retailer B, 136 days left); Retailer A 2027-06-29 (225 days left).

5. Rules and plan notes
Retailer C: rule is 30% of life remaining, not a day count; not applied to any SKU. Answer from: Supply lead (the day count to use).
Retailer B: no rule supplied for FH-SP-03.
No account appears in the demand plan without a rule row.

Totals by unit: cartons 5,150 (all in Decision needed); each 8,000 (5,000 Date not placed, 3,000 No supply decision flagged).

Draft for the Supply lead and the Quality owner. No date has been interpreted, no shelf life or suitability is stated, and nothing has been changed, sent or moved.
```

## What was observed

- **Every required part was produced.** All five sections, the header lines, the totals and the closing line are present. Nothing in the inputs triggered a stop: every required header was present, no two export lines shared SKU, batch and location, and the rules, today's date and the export were all supplied. I was not asked to interpret a code or choose an action, so the decline paths were not exercised.
- **Arithmetic.** Each last dispatch date was worked out as the placed date minus required days in calendar days, and checked by counting forward again from the result. The days-left figures were counted from 2026-11-16. Quantities by unit match the export (cartons 1,200 + 2,400 + 600 + 150 + 800 = 5,150; each 5,000 + 3,000 = 8,000).
- **Difference from the published example.** The two lists agree on every date, day count, flag, quantity, section, ordering and open item. The only difference in substance is the header: I wrote "Transit days: as supplied; 0 for Retailer C (blank, and its rule is not applied)", the example writes "as supplied". The other differences are in wording: the example adds a role reason in brackets after some "Answer from" names ("the approved date", "suitability and any restriction", "whether the hold affects any plan line"), and ends with a sentence outside the code block that I did not produce. I wrote Retailer C's rule as "30% of life remaining", the example as "a share of life remaining".
- **Facts not in the inputs.** None in my output. In the example, the bracketed reasons after "Answer from" are the author's wording, not facts from the inputs. The closing sentence of the example says each figure traces to the tables, which holds.
- **Reviewer checklist.** Items 1 to 9 hold for my output on reading. I did not run any code; the checking was done by hand.

## Where the template was unclear

- **Blank transit days on a rule that is not applied.** Step 4 says a blank Transit days counts as 0 and the header names the accounts it applies to. Retailer C's blank sits on a rule that is not applied at all. I named Retailer C in the header anyway; the example says only "as supplied". The template does not say which is right.
- **Where the account's own rule is missing for an account with no planned units.** Step 4 says to record "no rule supplied" for each account and SKU, but step 9 limits the notes to SKUs where the account has planned units, and the output format has a line for any "no rule supplied". I listed Retailer B and FH-SP-03 (no planned units) in section 5, as the example does.
- **Which role owns a rule on file.** The Roles list names a key account lead as an example, but the settings name only the supply lead and the quality owner. For Retailer C's day count I wrote "Supply lead"; the template gives no rule for that case.
- **Ordering uses "earliest last dispatch date".** It does not say whether this is the earliest across all of a line's accounts, flagged or not. I used the earliest across all usable accounts. In this example it makes no difference to the order.
- **A batch in two locations.** The acceptance test says the plan figures are "shown once in the note". The output format has no place for that, so I repeated each account's figures on both lines and gave the note once at the end of the section, as the example does.
- **Section 3 order and a possible duplicate.** The template does not say how to order open items. I ordered them by SKU and batch. A line with a stated date that has passed appears in Decision needed and again in Open items, as the template requires, which repeats the fact.
- **"Date key: [n] batches / not supplied"** gives no singular form. I wrote "1 batch", as the example does.
- **Header placeholders.** The output format has "[your horizon]" in the Inputs text (default 30 unless set) but no such placeholder in the instruction block, which says only "horizon in days". An assistant given only the block has no default.

## Edits made after the run

After an independent review, the template was edited to settle the points above. The recorded output above was not changed, and the template has not been run again since these edits.

- Step 4 now says to name every account whose blank transit days count as 0, even where its rule is not applied; the example's header now reads as this run's did.
- Step 9 now lists each SKU in the stock export for which an account in the rules table has no SKU row and no ALL row, so it covers Retailer B and FH-SP-03 as the example shows.
- The default horizon is written as 30 days in the inputs and in the instruction block.
- The roles list says the supply lead answers rule questions when no one else is named.
- Ordering now reads earliest across all usable rules, flagged or not; open items are ordered by SKU, batch, then location.
- Acceptance test 8 now matches the output format; a placed line with no usable rule for any account has its own wording; the header has singular and plural for the date key.
- The instruction block now says to leave out zero-quantity lines and to write the rules and plan notes.
- In the example, the open item for batch L-355 now states only the on-hold status.
- Added after a second review, none of it run again: open items are now listed in the order the lines appear in the export (the earlier SKU, batch, location rule would have put batch L-355 first); the output format allows an optional bracketed question after "Answer from"; the header placeholder for transit days now shows the combined form this run wrote; the instruction block now also covers a blank or non-numeric quantity and a missing demand plan; a note under the output format says that a line whose stated date has passed is repeated under Open items on purpose; and the example's open item for batch L-355 was trimmed to "Answer from: Supply lead." so it matches the note above.
