# Trial: Wholesale order check, run on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10
- **Template version:** 0.1.0

This is a record of two runs of the capability template on its own invented example. The brand, the retailer, the products, the prices, the stock and the dates are invented, and no client data was used. It shows what the template produced on one set of inputs. It is not a test in any company's environment.

The first run is below as recorded. An independent review of the template and its example then found where the instructions left room to guess, and the instructions, the output format and the example were revised. The second run, made on the revised instructions, is recorded after the first.

# First run

The assistant that ran this trial did not write the template.

The inputs are the invented example in `public/example.md` (a made-up granola and snack-bar brand and a fictional retailer, Retailer A).

## Inputs used (first run)

All five input blocks in the "The inputs" section of `public/example.md`: the settings, the six purchase order lines with the buyer's terms and note, the three-line approved quote, the three-product stock plan and the account terms. The example's own check was not read until after the output below was produced.

## What came out (first run)

The instruction block and output format were followed as written. This is the whole output.

```
WHOLESALE ORDER CHECK: RA-77410

For: the account owner, with operations. Account Retailer A. Purchase order dated 2026-11-09 against quote Q-2026-118 (dated 2026-10-20, valid until 2026-11-20). Prepared 2026-11-10.
Inputs: purchase order 6 lines, quote 3 lines, stock plan 3 products, account terms supplied. Currency US dollars.

Order at a glance: 6 lines, 140 cases, 1,410 units, 6,639.00 at the order's prices. Lines on the quote (5): 5,874.00 at the order's prices, 5,904.00 at the quote's prices, difference -30.00. Lines not on the quote (1): 765.00. Quote still valid on the order date. Minimum order value 2,500.00; the order's 6,639.00 is larger (compared on the whole order only).

Line comparison
Line 1, GR-350 Maple granola 350 g: 40 cases of 12 (quote 12), 480 units. Price 4.10 (quote 4.10). To Retailer A DC North (on account). Date 2026-12-01 (earliest 2026-11-30). Result: matches.
Line 2, GR-350 Maple granola 350 g: 20 cases of 12 (quote 12), 240 units. Price 4.10 (quote 4.10). To Retailer A DC South (on account). Date 2026-12-01 (earliest 2026-11-30). Result: matches.
Line 3, GR-700 Maple granola 700 g: 25 cases of 6 (quote 6), 150 units. Price 7.40 (quote 7.60). To Retailer A DC North (on account). Date 2026-12-01 (earliest 2026-12-03). Result: exceptions 1, 2, 11.
Line 4, BR-250 Seed bar box 250 g: 30 cases of 8 (quote 6), 240 units. Price 5.50 (quote 5.50). To Retailer A DC North (on account). Date 2026-11-24 (earliest 2026-11-20). Result: exceptions 3, 7.
Line 5, GR-350V Vanilla granola 350 g: 15 cases of 12, 180 units. Price 4.25. To Retailer A DC South (on account). Date 2026-12-01. Not on the quote; not in the stock plan. Result: exceptions 4, 5, 11.
Line 6, GR-350 Maple granola 350 g: 10 cases of 12 (quote 12), 120 units. Price 4.10 (quote 4.10). To Retailer A Store 14 (not on account). Date 2026-12-01 (earliest 2026-11-30). Result: exception 6.

Stock by product
GR-350: lines 1, 2, 6 ask for 840 units; 840 available (short 0). Earliest 2026-11-30.
GR-700: line 3 asks for 150 units; 150 available (short 0). Earliest 2026-12-03.
BR-250: line 4 asks for 240 units; 200 available (short 40). Earliest 2026-11-20.
GR-350V: no row in the stock plan.

Exceptions: 11
1. Line 3, GR-700, price. The order says 7.40 a unit; the quote says 7.60. That is 0.20 a unit below the quote, -30.00 over 150 units. Question: does the account owner accept the order's price? Decides: account owner.
2. Line 3, GR-700, date. The order asks for 2026-12-01; the stock plan's earliest is 2026-12-03, 2 days later. Question: can operations meet 2026-12-01? Decides: operations.
3. Line 4, BR-250, case pack. The order says 8 units a case; the quote says 6. At 30 cases the order is 240 units; at the quote's pack it would be 180 units. Question: which pack does the order mean? Decides: account owner.
4. Line 5, GR-350V, not on the quote. The order has 180 units at 4.25, 765.00; the quote has no such sku. Question: is this product to be supplied to this buyer at this price? Decides: account owner.
5. Line 5, GR-350V, not in the stock plan. The order asks for 180 units by 2026-12-01; the stock plan has no row for this sku. Question: what stock and earliest date does operations have for it? Decides: operations.
6. Line 6, GR-350, delivery location. The order ships to "Retailer A Store 14"; the account's locations are "Retailer A DC North" and "Retailer A DC South". Question: is delivery to this location agreed? Decides: account owner.
7. BR-250, stock shortfall (line 4). Lines asking for BR-250 total 240 units; 200 are available, short 40. Question: what quantity can operations supply to this order? Decides: operations, with the account owner (it depends on exception 3).
8. Order, payment terms. The order asks for "Net 60"; the account terms say "Net 30". The words differ. Question: does the account owner accept the buyer's payment term? Decides: account owner.
9. Order, other terms: "Free delivery to all locations." Not in the quote or the account terms. Question: is this term agreed? Decides: account owner.
10. Order, other terms: "Unsold stock may be returned within 90 days." Not in the quote or the account terms. Question: is this term agreed? Decides: account owner.
11. Order, substitution note, linked to exceptions 1, 2, 4 and 5. The buyer wrote: "If GR-700 cannot ship by 1 December, send GR-350V instead at the same price." GR-700 has an earliest date of 2026-12-03 (exception 2). GR-350V is not on the quote and not in the stock plan. Nothing is applied. Question: is any substitution accepted, and on what terms? Decides: account owner, with operations.

Terms the buyer asked for
Payment terms: Net 60 (account terms: Net 30). See exception 8.
Other terms: "Free delivery to all locations."; "Unsold stock may be returned within 90 days." (not in the quote or account terms). See exceptions 9 and 10.
Notes and substitutions: "If GR-700 cannot ship by 1 December, send GR-350V instead at the same price." See exception 11.

Not checked
The meaning of "Net 60", "free delivery" and the 90-day return term is not interpreted. "At the same price" in the substitution note does not say which price (the order's 7.40, the quote's 7.60 or the 4.25 on line 5); it is quoted, not read. Whether "Retailer A Store 14" relates to either delivery location is not decided. The account terms do not say how the minimum order value is measured; the whole order is compared only.

Decision, account owner: Accept / Change / Query each of exceptions 1, 3, 4, 6, 7, 8, 9, 10, 11: ________
Decision, operations: stock and dates for exceptions 2, 5, 7, 11: ________

Nothing has been confirmed to the buyer, and no record has been changed. The account owner tells the buyer once the decisions are made.
```

## What was observed (first run)

- Every part of the output format was produced, and every number in it comes from the inputs. Nothing was asked for that the example did not supply, and nothing in the template made the assistant stop.
- The sums were checked twice and agree with the published example: 140 cases, 1,410 units, 6,639.00 at the order's prices, 5,874.00 and 5,904.00 on the lines on the quote, -30.00.
- All six line results agree with the published example: lines 1 and 2 match; lines 3, 4, 5 and 6 each carry exceptions. The same findings were found: price on line 3, the 2-day date gap on line 3, the case pack and the 40-unit shortfall on line 4, line 5 absent from the quote and the stock plan, the location on line 6, the payment term, the two other terms and the substitution note.
- Differences from the published example, all of form:
  - The published example gives nine exceptions; this run gives eleven. It lists line 5's missing quote row and missing stock row as one exception, and the two extra terms as one; this run split each, because step 11 says one exception for each finding.
  - The example puts the BR-250 shortfall beside the case pack in line order (its exception 4). This run put it with the order-level findings (exception 7), because step 11 does not say where a shortfall by product belongs.
  - The example puts the substitution note before the terms; this run put it last, after the terms, following step 11's order.
  - The example's "Terms the buyer asked for" section has a minimum order line and no "Notes and substitutions" line. The output format has the latter and no minimum line, and this run followed the format. The minimum is stated once, in the at-a-glance paragraph.
  - The example's "Not checked" names a wider agreement; this run listed the wording it left uninterpreted.
  - The example names the deciding role for exception 2 as the account owner with operations; the template says operations decides dates, and this run named operations.
- Facts not in the inputs: none in either output. The example's "no agreement was supplied" is true of the inputs.
- Where the instructions were ambiguous and a guess was needed:
  - Where a stock shortfall sits in the exception order (on its line, or with the order-level findings).
  - Whether a missing quote row and a missing stock row on the same line are one exception or two.
  - Whether "not in the quote or account terms" for an extra term is itself an exception. Step 8 says "mark", the output format says "See exception n", and step 11 says one exception for each finding. This run treated each as an exception.
  - Whether one note covering two terms makes one exception or two.
  - Whether a substitution exception's linked numbers should be listed on the lines it touches. This run did.
  - Which role decides a date: step 11 says operations, while the output format's example line suggests the account owner decides what to offer. This run followed step 11.
  - The "at the same price" wording, which cannot be settled from the records. It is correctly left unread.
- A shortcoming: the two instruction texts (the procedure and the fenced block) differ in length and detail, and the format has no line for the minimum order beyond the at-a-glance paragraph, which the example adds to the terms section. The acceptance tests were not run here; only the one example was tried.

# Second run, on the revised instructions

The inputs are the same five blocks in `public/example.md`. The inputs were not changed.

This run was made by the assistant that revised the template, in the same session, working through the revised procedure and instruction block line by line on the inputs, not in a fresh session. It is therefore a weaker run than the first, which was made by an assistant that had not seen the template's author's reasoning. The published example's check is the output below.

## What changed before this run

- The procedure and the instruction block now settle the points the first run found ambiguous. One exception for each finding, and a finding is one difference between the order and one record. A shortfall is one exception for each product, numbered after the line exceptions and before the other order-level ones. Each requested term is its own exception. Operations decides stock rows, shortfalls and delivery dates; the account owner decides price, case pack, product, location and terms; "operations, with the account owner" is for an exception that depends on the other's decision, with the exception named.
- A line is marked with every exception that names it, including the shortfall for its sku and a substitution note that names it.
- Unclear buyer wording still gets its exception and is also put in "Not checked". The block now says so, and carries the rule for how the minimum is measured and the words "operations, with the account owner".
- New in both: pre-printed standard terms and conditions are recorded as present, not read; an order below the minimum is one order-level exception. Neither case arises in the example, so neither was exercised by this run.
- The example's check was replaced by the output of this run.
- The revision adopted several of the first run's choices as rules, among them the wording of exception 7's deciding role, "operations, with the account owner (it depends on exception 3)". That is why the second run's output is byte-for-byte the first run's: the rules were written from it, and the same assistant then re-derived it. It shows the revised rules reproduce those choices, not that they hold up under a fresh reader.

## What came out (second run)

```
WHOLESALE ORDER CHECK: RA-77410

For: the account owner, with operations. Account Retailer A. Purchase order dated 2026-11-09 against quote Q-2026-118 (dated 2026-10-20, valid until 2026-11-20). Prepared 2026-11-10.
Inputs: purchase order 6 lines, quote 3 lines, stock plan 3 products, account terms supplied. Currency US dollars.

Order at a glance: 6 lines, 140 cases, 1,410 units, 6,639.00 at the order's prices. Lines on the quote (5): 5,874.00 at the order's prices, 5,904.00 at the quote's prices, difference -30.00. Lines not on the quote (1): 765.00. Quote still valid on the order date. Minimum order value 2,500.00; the order's 6,639.00 is larger (compared on the whole order only).

Line comparison
Line 1, GR-350 Maple granola 350 g: 40 cases of 12 (quote 12), 480 units. Price 4.10 (quote 4.10). To Retailer A DC North (on account). Date 2026-12-01 (earliest 2026-11-30). Result: matches.
Line 2, GR-350 Maple granola 350 g: 20 cases of 12 (quote 12), 240 units. Price 4.10 (quote 4.10). To Retailer A DC South (on account). Date 2026-12-01 (earliest 2026-11-30). Result: matches.
Line 3, GR-700 Maple granola 700 g: 25 cases of 6 (quote 6), 150 units. Price 7.40 (quote 7.60). To Retailer A DC North (on account). Date 2026-12-01 (earliest 2026-12-03). Result: exceptions 1, 2, 11.
Line 4, BR-250 Seed bar box 250 g: 30 cases of 8 (quote 6), 240 units. Price 5.50 (quote 5.50). To Retailer A DC North (on account). Date 2026-11-24 (earliest 2026-11-20). Result: exceptions 3, 7.
Line 5, GR-350V Vanilla granola 350 g: 15 cases of 12, 180 units. Price 4.25. To Retailer A DC South (on account). Date 2026-12-01. Not on the quote; not in the stock plan. Result: exceptions 4, 5, 11.
Line 6, GR-350 Maple granola 350 g: 10 cases of 12 (quote 12), 120 units. Price 4.10 (quote 4.10). To Retailer A Store 14 (not on account). Date 2026-12-01 (earliest 2026-11-30). Result: exception 6.

Stock by product
GR-350: lines 1, 2, 6 ask for 840 units; 840 available (short 0). Earliest 2026-11-30.
GR-700: line 3 asks for 150 units; 150 available (short 0). Earliest 2026-12-03.
BR-250: line 4 asks for 240 units; 200 available (short 40). Earliest 2026-11-20.
GR-350V: no row in the stock plan.

Exceptions: 11
1. Line 3, GR-700, price. The order says 7.40 a unit; the quote says 7.60. That is 0.20 a unit below the quote, -30.00 over 150 units. Question: does the account owner accept the order's price? Decides: account owner.
2. Line 3, GR-700, date. The order asks for 2026-12-01; the stock plan's earliest is 2026-12-03, 2 days later. Question: can operations meet 2026-12-01? Decides: operations.
3. Line 4, BR-250, case pack. The order says 8 units a case; the quote says 6. At 30 cases the order is 240 units; at the quote's pack it would be 180 units. Question: which pack does the order mean? Decides: account owner.
4. Line 5, GR-350V, not on the quote. The order has 180 units at 4.25, 765.00; the quote has no such sku. Question: is this product to be supplied to this buyer at this price? Decides: account owner.
5. Line 5, GR-350V, not in the stock plan. The order asks for 180 units by 2026-12-01; the stock plan has no row for this sku. Question: what stock and earliest date does operations have for it? Decides: operations.
6. Line 6, GR-350, delivery location. The order ships to "Retailer A Store 14"; the account's locations are "Retailer A DC North" and "Retailer A DC South". Question: is delivery to this location agreed? Decides: account owner.
7. BR-250, stock shortfall (line 4). Lines asking for BR-250 total 240 units; 200 are available, short 40. Question: what quantity can operations supply to this order? Decides: operations, with the account owner (it depends on exception 3).
8. Order, payment terms. The order asks for "Net 60"; the account terms say "Net 30". The words differ. Question: does the account owner accept the buyer's payment term? Decides: account owner.
9. Order, other terms: "Free delivery to all locations." Not in the quote or the account terms. Question: is this term agreed? Decides: account owner.
10. Order, other terms: "Unsold stock may be returned within 90 days." Not in the quote or the account terms. Question: is this term agreed? Decides: account owner.
11. Order, substitution note, linked to exceptions 1, 2, 4 and 5. The buyer wrote: "If GR-700 cannot ship by 1 December, send GR-350V instead at the same price." GR-700 has an earliest date of 2026-12-03 (exception 2). GR-350V is not on the quote and not in the stock plan. Nothing is applied. Question: is any substitution accepted, and on what terms? Decides: account owner, with operations.

Terms the buyer asked for
Payment terms: Net 60 (account terms: Net 30). See exception 8.
Other terms: "Free delivery to all locations."; "Unsold stock may be returned within 90 days." (not in the quote or account terms). See exceptions 9 and 10.
Notes and substitutions: "If GR-700 cannot ship by 1 December, send GR-350V instead at the same price." See exception 11.

Not checked
The meaning of "Net 60", "free delivery" and the 90-day return term is not interpreted. "At the same price" in the substitution note does not say which price (the order's 7.40, the quote's 7.60 or the 4.25 on line 5); it is quoted, not read. Whether "Retailer A Store 14" relates to either delivery location is not decided. The account terms do not say how the minimum order value is measured; the whole order is compared only.

Decision, account owner: Accept / Change / Query each of exceptions 1, 3, 4, 6, 7, 8, 9, 10, 11: ________
Decision, operations: stock and dates for exceptions 2, 5, 7, 11: ________

Nothing has been confirmed to the buyer, and no record has been changed. The account owner tells the buyer once the decisions are made.
```

## What was observed (second run)

- The output has eleven exceptions, the same eleven as the first run, in the same order and with the same line marks. The example now matches it exactly, so the template, the example and this record give one exception list.
- The "Terms the buyer asked for" section has the three lines the format has, including "Notes and substitutions". There is no minimum line in it; the minimum is stated once, in the at-a-glance paragraph, and its measurement is named in "Not checked".
- Nothing in the output is a fact not in the inputs. Every sum was checked twice.
- Where the revised instructions still leave a choice: what the order of exceptions within a line is when a line has both a stock row exception and a date exception (the instructions say product, case pack, price, location, date, stock row; a sku with no stock row has no date comparison, so the case did not arise). The two new rules (standard terms and conditions, below the minimum) and the acceptance tests were not run.
- Because the second run was made by the assistant that revised the instructions, an independent run on the revised instructions has not yet been made.

## Edits made after the second run

After an independent review, small wording changes were made to the template without a new run. The recorded outputs above are unchanged. The changes: the procedure and block now say how the "Lines on the quote" figures are computed (the order's units at the order's prices and at the quote's prices); a shortfall's exception starts with the product's sku; and a substitution note is decided by "account owner, with operations", which is what exception 11 already says. Worked by hand on the example, these give the same figures and the same exceptions as the second run. They have not been run as a fresh session, and no independent run on the revised instructions exists.
