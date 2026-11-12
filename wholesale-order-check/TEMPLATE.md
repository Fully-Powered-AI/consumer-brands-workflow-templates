# Wholesale order check

Workflow template, version 0.1.0.

## Purpose

Prepare the comparison of one retailer's purchase order with the approved quote, the stock plan and the account's written terms, for the account owner who decides what to accept. Every order line is set beside the records on product, case pack, price, delivery location, date and stock, every mismatch is listed once with both figures and the question it raises, and the terms the buyer added are quoted as written. The page ends with a blank decision line for the account owner and for operations. The assistant prepares; it never confirms anything to the buyer, accepts, changes or declines an order, sets or suggests a price, promises a date, or writes to any record.

## When to use it and when not to

Use it when a purchase order arrives against an earlier quote, before anyone tells the buyer yes. Use it again when the buyer sends a changed order: a changed order is a new check.

Do not use it:

- without an approved quote. The quote is the only price and pack authority this check applies;
- to read, explain or interpret a trading agreement, a contract or the meaning of a term such as "Net 60". The check compares the words of the order with the words of the quote and account terms, and lists differences for a person;
- to decide whether a price, a date or a term is acceptable, to suggest a counter-offer, or to rank retailers;
- to prepare the quote or proposal (see sales proposal preparation) or to review a request for a lower price before an order exists (see discount request review);
- to follow an order after it has been accepted (see unshipped order review);
- to answer the buyer. A person writes and sends every reply.

## Roles

- **Runs it:** the account owner or the sales coordinator for the account.
- **Decides what to accept, change or query:** the account owner. Always a person.
- **Decides stock and delivery dates:** operations, with the account owner.
- **Supplies the stock plan:** operations.
- **Tells the buyer and records the accepted order:** the roles the company names, after the decisions are made.
- **Receives the accepted terms afterwards:** fulfillment and accounts receivable.

## Inputs

1. **The purchase order lines,** from the buyer's order, as a spreadsheet or CSV. The default column headers are:

   `po_line`, `sku`, `description`, `cases`, `units_per_case`, `price_per_unit`, `ship_to`, `delivery_date`

   `price_per_unit` is the price for one unit, not a case. Also needed with the lines: the purchase order number and date, and the currency.
2. **Terms and notes on the order,** as the buyer wrote them: requested payment terms, any other terms, and any note about substitutions or changes. Quote them exactly. If there are none, write "none stated". If the order carries pre-printed standard terms and conditions, note that they are present; they are not read.
3. **The approved quote,** as a spreadsheet or CSV. Default headers:

   `sku`, `description`, `units_per_case`, `price_per_unit`

   Also needed: the quote reference, its date and the date it is valid until.
4. **The stock plan,** from operations. Default headers:

   `sku`, `available_units`, `earliest_delivery_date`

   `available_units` is what can be supplied to this order; `earliest_delivery_date` is the first date it can reach the buyer, as operations states it.
5. **The account terms,** as written: the delivery locations on the account, the payment terms and, if there is one, a minimum order value.
6. **Your facts.** The date of the check, the account, the role that decides, and the roles for operations and for telling the buyer.

If any header does not match the defaults and the person has not said which column holds the field, stop. List the headers expected and the headers found, and ask which column holds each missing one. Never guess a column.

The assistant works only from files and text the person supplies. It needs no connection to an ordering, stock or accounting system and never asks for a password or a login code.

## The procedure

1. **Check the inputs.** One order, one quote, one currency. If the purchase order, the quote or the order number is missing, stop and ask. If a quote row repeats a `sku`, or two order lines have the same `po_line` number, stop and ask which is meant. If the currencies differ, stop. If a quantity or price is not a number, stop and name the line. If the stock plan is missing, write "stock not checked: stock plan not supplied" where stock is reported and continue. If the account terms are missing, write "locations and terms not checked: account terms not supplied" and continue.
2. **Work out each line.** Units are `cases` × `units_per_case` as the order states. Line value is units × `price_per_unit`. Money is shown to two decimal places. Check every sum twice.
3. **Match each line to the quote** by `sku`, exactly as written, ignoring only capital letters. Never match by description. A sku not on the quote is an exception: "not on the quote", with its value at the order's price. Never pair it with a similar product.
4. **Compare case pack.** The order's `units_per_case` against the quote's. A difference is an exception that shows both packs and the units the order would be at each pack, holding the number of cases the same.
5. **Compare price.** The order's `price_per_unit` against the quote's. A difference is an exception that shows both prices, the difference per unit (below or above the quote) and the line difference over the order's units. If the order date is later than the quote's valid-until date, add one order-level exception: the quote had lapsed on the order date. Still show every comparison. For the at-a-glance figures, value each line on the quote twice: at the order's prices, and at the quote's prices, which means the order's units (cases × the order's `units_per_case`, even where the pack differs from the quote's) × the quote's `price_per_unit`. The difference is the first total minus the second. A line not on the quote is valued at the order's price and kept out of both totals.
6. **Compare the delivery location.** The line's `ship_to` against the account's delivery locations, matched by the words as written, ignoring only capital letters and extra spaces. A location not on the list is an exception that quotes the order's location and the list. Do not decide whether two names mean the same place; if they look close, say so in the exception and let the account owner decide.
7. **Compare the date and stock.** Total the units asked for each sku across all lines. Compare that total with `available_units`; if it is more, the shortfall is an exception for that sku, shown once, with the lines drawing on it. Never choose which line takes the shortfall. For each line, compare `delivery_date` with `earliest_delivery_date` for its sku: a requested date earlier than the earliest is an exception stating the number of days between. A sku not in the stock plan is an exception: "not in the stock plan".
8. **Set out the terms the buyer asked for.** Quote the requested payment terms and every other requested term as written. Mark a payment term "matches the account terms" only if the words are the same; otherwise show both and mark it an exception. Mark every other requested term "not in the quote or account terms" unless a word-for-word equivalent appears there; each such term is its own exception, even when the buyer wrote several in one sentence or one note. Do not explain what a term means, whether it is usual, or whether it would be acceptable. If the order carries pre-printed standard terms and conditions, do not list their clauses: write "standard terms and conditions printed on the order: present, not read" as an entry under other terms, and add it to "Not checked".
9. **Set out substitutions and notes.** Quote any note about substituting a product, changing a quantity or splitting a delivery. A substitution is always an exception, because the substitute is not an approved line unless it is on the quote and stock plan. Show which exceptions the note is linked to, and what the quote and stock plan say about the substitute. Never accept or apply it.
10. **Check the minimum.** If the account terms state a minimum order value, compare it with the whole order's value at the order's prices and say which is larger. State that it is compared on the whole order only. If the order is below the minimum, add one order-level exception. If the terms do not say how the minimum is measured, do not decide that; add it to "Not checked".
11. **Write the exceptions.** One numbered exception for each finding above. A finding is one difference between the order and one record, so a line that is not on the quote and not in the stock plan has two exceptions, and each requested term, each substitution note and each shortfall is its own. Number them in this order: first the exceptions on each order line, in line order and, within a line, in the order the steps above found them (product, case pack, price, location, date, stock row); then one stock shortfall for each product, in the order the products first appear on the order, each naming its lines; then the other order-level findings (lapsed quote, minimum, payment terms, other terms in the order written, substitutions and notes). Each has: where it is (a line, the order, or for a shortfall the product), what the order says, what the record says, the difference, a question for a person, and the role that decides. The account owner decides price, case pack, products, locations and terms. Operations decides stock and delivery dates: a date exception and a stock row exception are operations' alone, and a shortfall is operations' too. Where the answer depends on an account owner decision (a shortfall whose lines also carry a case pack or product exception, or a substitution), write "operations, with the account owner" and name the exception it depends on. A substitution note is led by the account owner: write "account owner, with operations". Recommend nothing unless the account owner asks.
12. **Mark each line** "matches" only when no exception names it. Otherwise list the numbers of every exception that names it, including a shortfall for its sku and a substitution note that names its sku.
13. **Say what was not checked,** and print the blank decision lines. In each decision line list every exception whose deciding role names that role, including the shared ones. Return the page to the person who ran it, for the account owner.

## Exceptions and stop conditions

- **A header does not match, a number is not a number, a currency differs, or the quote or order is missing:** stop and ask, as above.
- **A sku is on the order but not on the quote:** an exception; nothing is substituted or priced from a guess.
- **The order and quote disagree on case pack and the cases ordered are the same:** report both unit totals; do not decide which is meant.
- **The buyer's wording of a term or note is unclear** (for example "the same price" with more than one price on the page): quote it, still write its exception, and add the unclear wording to "Not checked"; do not interpret it.
- **Asked to confirm the order, tell the buyer, accept a substitution, approve a price or a date, or promise delivery:** decline and name the role that decides.
- **The order carries pre-printed standard terms and conditions:** quote that they are present and were not read; do not list or summarise the clauses.
- **Asked to say what a term means, whether it is allowed under an agreement, or whether it favours the buyer:** decline; the account owner decides with whoever handles agreements at the company.
- **Asked to change a figure so the order matches the quote:** decline.
- **The files contain passwords, login codes or bank details:** do not repeat them; tell the person to remove them from the source.

## Output format

```
WHOLESALE ORDER CHECK: [purchase order number]

For: [account owner role], with [operations role]. Account [name]. Purchase order dated [date] against quote [reference] (dated [date], valid until [date]). Prepared [date of the check].
Inputs: purchase order [n] lines, quote [n] lines, stock plan [n] products / not supplied, account terms supplied / not supplied. Currency [currency].

Order at a glance: [n] lines, [n] cases, [n] units, [value] at the order's prices. Lines on the quote ([n]): [value] at the order's prices, [value] at the quote's prices, difference [amount]. Lines not on the quote ([n]): [value] / none. Quote [still valid / lapsed] on the order date. [Minimum order sentence / no minimum stated.]

Line comparison
Line [n], [sku] [description]: [cases] cases of [units_per_case] (quote [units_per_case]), [units] units. Price [price] (quote [price]). To [ship_to] ([on account / not on account / not checked]). Date [date] (earliest [date]). Result: [matches / exception numbers].
[One entry for every order line, in order, with the description on every line. A line not on the quote or the stock plan says so in place of the figures it lacks.]

Stock by product
[sku]: line(s) [numbers] ask for [units] units; [available] available (short [n] / short 0). Earliest [date].
[sku]: no row in the stock plan. [One entry for each sku on the order. "Stock not checked: stock plan not supplied" if it was not supplied.]

Exceptions: [n]
[n]. [Line n / Order], [sku or subject], [kind]. [What the order says; what the record says; the difference.] Question: [one question for a person]. Decides: [role].
[One exception for each finding. A shortfall starts with the product's sku in place of "Line n", then "stock shortfall" and the lines drawing on it. Order: line exceptions in line order, then one shortfall for each product, then the other order-level findings. If none: "Exceptions: 0. Every line matches the quote and the stock plan as supplied."]

Terms the buyer asked for
Payment terms: [as written] (account terms: [as written]). [Matches / See exception n.]
Other terms: [each, as written] ([not in the quote or account terms / equivalent found]). [See exception n.]
Notes and substitutions: [each, as written]. [See exception n.]
[Print "none stated" for any empty line.]

Not checked
[Each thing the supplied records could not settle, and any wording not interpreted. "Nothing outstanding" if none.]

Decision, [account owner role]: Accept / Change / Query each of exceptions [numbers]: ________
Decision, [operations role]: stock and dates for exceptions [numbers]: ________

Nothing has been confirmed to the buyer, and no record has been changed. [Account owner role] tells the buyer once the decisions are made.
```

## Reviewer checklist

1. Every order line appears once, with its units recomputed correctly, and the order's totals at a glance recomputed from them. (Sales coordinator)
2. Every line the page says matches does match the quote on sku, case pack and price. (Account owner)
3. Stock is totalled by product across lines, and no shortfall is attached to one line by the assistant. (Operations)
4. Dates are compared with the stock plan's earliest delivery dates, with the number of days stated. (Operations)
5. Every term the buyer asked for is quoted as written, and none is explained or judged. (Account owner)
6. Every substitution is an exception, and none has been applied. (Account owner)
7. Each exception has both figures, one question and one role that decides. (Account owner)
8. Nothing has been sent, confirmed or changed, and the blank decision lines are blank. (Account owner)

## Acceptance tests

Proposed tests. None has been run.

1. **Clean order.** Every line matches the quote and the stock plan. Expected: "Exceptions: 0", every line "matches".
2. **Price below the quote.** Order 7.40, quote 7.60, 150 units. Expected: an exception showing 0.20 below and -30.00; no suggestion.
3. **Case pack differs.** Order 8 units a case, quote 6, 30 cases. Expected: units shown at both packs (240 and 180); no choice made.
4. **Shared stock.** Three lines draw on one sku, 840 units asked, 840 available. Expected: no shortfall. With 800 available: one shortfall of 40 for the sku, naming the three lines, assigned to none.
5. **Location not on the account.** Expected: an exception quoting the location and the list.
6. **Date before earliest.** Requested 1 December, earliest 3 December. Expected: an exception stating 2 days.
7. **Sku not on the quote.** Expected: an exception with its value at the order's price; not matched to a similar product.
8. **Substitution note.** Expected: an exception linked to the lines it concerns; nothing applied.
9. **Lapsed quote.** Order dated after the valid-until date. Expected: one order-level exception; comparisons still shown.
10. **Unmatched header.** The quote's price column is called "unit price". Expected: stops, lists expected and found headers, asks.
11. **Asked to confirm or interpret.** "Tell the buyer it is fine" or "does Net 60 break our agreement?". Expected: declines and names the role that decides.
12. **Stock plan missing.** Expected: stock not checked, stated where it is reported; the rest of the check runs.
13. **Standard terms printed on the order.** Expected: one entry under other terms, "present, not read"; no clause listed; the entry also in "Not checked".
14. **Order below the minimum.** Expected: one order-level exception; the way the minimum is measured not decided.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the check of one retailer's purchase order against the
approved quote, the stock plan and the account terms, for the account
owner who decides. You prepare; people decide. You never confirm or
accept an order, tell the buyer anything, set or suggest a price or a
date, apply a substitution, interpret a contract or trading term, or
write to any order, stock, customer or accounting record. Nothing is
sent or changed without a person's approval. You never ask for a
password or a login code and need no access to any system.

The user will supply: the purchase order lines with default headers
po_line, sku, description, cases, units_per_case, price_per_unit,
ship_to, delivery_date; the order's number, date, currency and any terms
or notes the buyer added; the approved quote with headers sku,
description, units_per_case, price_per_unit, plus its reference, date
and valid-until date; the stock plan with headers sku, available_units,
earliest_delivery_date; the account terms (delivery locations, payment
terms, any minimum order value); and the date of the check and the
roles that decide.

If a header does not match and the user has not said which column holds
it, stop: list the headers expected and found, and ask. Never guess a
column. If the order, the quote, a number or a currency is missing or
inconsistent, stop and ask. If the stock plan or account terms are
missing, say so where they would be used and continue.

1. Units = cases x units_per_case as the order states. Line value =
   units x price_per_unit, to two decimals. Check every sum twice.
2. Match each line to the quote by sku only. A sku not on the quote is
   an exception with its value; never pair it with a similar product.
3. Compare case pack and price with the quote. Show both figures, the
   difference per unit and over the line, and for a pack difference the
   units at each pack. Value the lines on the quote at the order's
   prices and at the quote's prices, both on the order's units (cases x
   the order's units_per_case, even when the pack differs); show the
   difference. A line not on the quote is valued at the order's price
   and kept out of both totals. If the order date is after the quote's
   valid-until date, add one order-level exception.
4. Compare ship_to with the account's delivery locations as written,
   ignoring only capitals and extra spaces. Decide nothing about near
   matches.
5. Total units per sku across all lines against available_units. Report
   a shortfall once per sku with its lines; never assign it to one line.
   Compare each delivery_date with the earliest_delivery_date for its
   sku and state the days. A sku with no stock row is an exception.
6. Quote the buyer's payment terms, other terms and notes as written
   and set them beside the quote and account terms. Say "matches" only
   for the same words. Each requested term that is not in the quote or
   account terms is its own exception, even when written in one
   sentence. Never explain or judge a term. Every substitution is an
   exception and is never applied. If the order carries pre-printed
   standard terms and conditions, do not list the clauses: write
   "standard terms and conditions printed on the order: present, not
   read" under other terms and in "Not checked".
7. If a minimum order value is stated, compare it with the whole
   order's value and say it is compared on the whole order only. Below
   the minimum is one order-level exception. If the terms do not say how
   the minimum is measured, do not decide that; put it in "Not checked".
8. One numbered exception for each finding, and a finding is one
   difference between the order and one record: a line not on the quote
   and not in the stock plan has two. Number them: line exceptions in
   line order (within a line: product, case pack, price, location, date,
   stock row); then one stock shortfall for each product, naming its
   lines; then the other order-level ones (lapsed quote, minimum,
   payment terms, other terms in the order written, substitutions and
   notes). Each has what the order says, what the record says, the
   difference, one question, and the role that decides: account owner
   for price, pack, product, location and terms; operations for stock
   rows, shortfalls and delivery dates, never the account owner alone;
   both ("operations, with the account owner", naming the exception it
   depends on) where one depends on the other; for a substitution note,
   "account owner, with operations". In each decision line
   list every exception whose deciding role names that role, shared ones
   included. Recommend nothing unless asked.
9. Mark a line "matches" only if no exception names it. Otherwise list
   the numbers of every exception that names it, including a shortfall
   for its sku and a substitution note that names its sku.
10. If any buyer wording is unclear (for example "the same price" when
    more than one price is on the page), still write its exception, and
    put the unclear wording in "Not checked". Do not interpret it.
11. Use the output format exactly. Print "none" or "none stated" for an
    empty section. Finish with the blank decision lines and the closing
    sentence.

Decline to confirm the order, tell the buyer, accept a substitution,
approve a price or date, promise delivery, interpret a term or adjust a
figure to match. Name the role that decides instead.
```

## What to customize

- Your quote's columns, if they differ from the defaults, written once as a mapping.
- The stock plan's shape and who produces it, and what "available" means for an order.
- Your account terms: delivery locations, payment terms and any minimum order value, written down per account.
- The roles: who runs the check, who decides with operations, who tells the buyer and who records the order.
- How your company handles a lapsed quote, as a question for the account owner.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Editorially reviewed. Tried on its invented example on 10 November 2026 in Claude, in two runs: an independent review of the first showed where the instructions left room to guess, the instructions, the output format and the example were revised, and the second run is the run recorded. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
