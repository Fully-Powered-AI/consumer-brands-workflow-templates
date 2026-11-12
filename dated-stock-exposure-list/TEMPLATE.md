# Dated stock exposure list

Workflow template, version 0.1.0.

## Purpose

Prepare a batch-level list of dated stock for a supply planner who is about to place or review a production or replenishment order. For every batch line the list gives the stated date, the quantity and the location, works out for each account the last day the batch could ship and still meet that account's rule, and shows which batches need a decision. It reports dates exactly as stated and sets them against rules the brand supplied. The assistant prepares; it never interprets a date code, says how long a product lasts, judges suitability or safety, chooses what to do with stock, or changes, sends or moves anything.

## When to use it and when not to

Use it when date-coded stock needs review before another production or replenishment order, before a planning meeting, or when a new account's rules arrive. Run it again when a new stock export, date list or demand plan is available.

Do not use it:

- to decide whether a product is fit to sell, how long it lasts, or how to read a printed date or lot code. The quality owner decides, and records the answer in the approved date list;
- to price, discount or plan the sale of slow stock. That is Slow-moving stock and markdown plan;
- for clinic or medical supplies with expiry and par levels. That is Clinic supply par levels and expiry check;
- to work out how much to order. That is Inventory reorder plan;
- for rules the brand has not supplied. It does not guess an account's requirements.

## Roles

- **Runs it:** the supply planner.
- **Confirms suitability and any restriction, and supplies approved dates:** the quality owner.
- **Approves any stock action or production change:** the supply lead.
- **Owns the account relationship and the rules on file:** whoever the brand names (for example the key account lead). If none is named, the supply lead answers questions about a rule, such as a day count.
- **Moves, holds or releases stock:** the warehouse, only on a person's instruction.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to any system and never asks for a password or a login code. Every table below is read by its column headers. If a required header is missing, or a header could mean two columns, stop and ask which column is which; never guess.

1. **Stock-by-batch export.** Default headers: SKU, Product, Batch, Location, Quantity, Unit, Stated date, Date label, Storage, Status. Required: SKU, Batch, Location, Quantity, Unit, Stated date. Optional: Product, Date label, Storage, Status. If a required header is missing, stop.
2. **Approved date list,** written by the quality owner. Default headers: Batch, Approved date, Date label, Approved by. If none is supplied, write "Date key: not supplied" and continue.
3. **Retailer acceptance rules,** as the brand has them on file. Default headers: Account, SKU, Minimum days remaining, Transit days. A SKU of ALL means every SKU for that account. If none is supplied, stop: the list is set against these rules.
4. **Demand plan.** Default headers: SKU, Account, Week start, Units. If none is supplied, write "Demand plan: not supplied" and show every planned-unit figure as "not supplied"; no line can be flagged as missed or inside the horizon, so say so in the header.
5. **Settings.** Today's date (required; if missing, stop and ask), the date format of the export (default YYYY-MM-DD), the horizon in days (default 30 days), and the names of the supply lead and quality owner.

## The procedure

1. **Check the inputs.** Confirm each table's headers against the defaults and that the settings are present. Leave out lines with a quantity of zero and count them in the header. If a line has a blank or non-numeric quantity, list it under Open items; do not count it in totals. If two lines share the same SKU, batch and location, stop and ask whether one is a duplicate.
2. **Place the date on each line.** Use the approved date list first: if the batch is listed and its approved date is a full calendar date (day, month and year, in the stated format), use it. Otherwise use the export's stated date, if it is a full calendar date in the stated format. Anything else is unplaced: a month and year only, a printed code, free text, a blank, an impossible date such as 2027-02-30, or a format that does not match. Never read a batch number, a lot code or a product type to work out a date, and never add, subtract or round a date. If the list and the export give different full dates, use the list and put the conflict under Open items.
3. **Take the label as written.** The date label comes from the approved list, then the export, else "label not stated". Copy it word for word. Never turn one label into another or say what a label means.
4. **Choose the rule for each account.** For each account and SKU, use the account's row for that SKU; if there is none, use its ALL row; if there is neither, record "no rule supplied" for that account and SKU. A rule that is not a whole number of days (for example a share of life remaining) is not applied; record it with a request for the day count. Required days are Minimum days remaining plus Transit days. A blank Transit days counts as 0; name every account where it does so in the header, including an account whose rule is not applied.
5. **Work out the last dispatch date.** For each placed line and each usable rule: last dispatch date = placed date minus required days, counted in calendar days. Days left = last dispatch date minus today. A negative figure is "missed by [n] days".
6. **Read the plan.** For each SKU and account, add the units whose Week start is on or after today. Split them into units on or before the last dispatch date and units after it. The plan is for the SKU: show it on every batch line of that SKU and assign none to a batch. If the account has no plan row for the SKU, the figure is 0.
7. **Flag the lines.**
   - **Missed:** days left is below 0 and the account's planned units from today are above 0.
   - **Inside horizon:** days left is from 0 up to the horizon, and the account's planned units from today are above 0.
   - **Stated date passed:** the placed date is before today.
   - A missed or inside-horizon pair without planned units is shown and marked "Not flagged: no planned units". A pair beyond the horizon is shown and marked "Not flagged: outside the [n]-day horizon".
   - A line is **Decision needed** if any pair is flagged or its stated date has passed. A line with no placed date is **Date not placed**. Every other line is **No supply decision flagged**.
8. **Collect the open items.** One numbered item for each of: a stated date that has passed; a conflict between the list and the export; a blank Storage on a line (write "storage condition not stated"); a Status other than available or blank, shown as supplied; a blank or unreadable quantity. Name the role that answers each: the quality owner for dates, storage and suitability; the supply lead for plan and status questions about orders. List the items in the order the lines appear in the export.
9. **Note the rules.** List rules not applied and why, each SKU in the stock export for which an account in the rules table has neither a SKU row nor an ALL row ("no rule supplied"), and accounts in the demand plan with no rule row.
10. **Order and total.** In Decision needed, order lines by their earliest last dispatch date across all usable rules, flagged or not, oldest first; ties by SKU, batch, then location. Total quantities by unit for each section, never adding different units together.
11. **Return the draft** to the supply planner for the quality owner and supply lead. Recommend no action.

## Exceptions and stop conditions

- **No rules table, no today's date, a missing required header, or two lines with the same SKU, batch and location:** stop and ask.
- **A date that cannot be placed:** list the line under Date not placed. Never estimate it, round it or infer it from a code.
- **A date label or code the assistant does not recognize:** copy it as written; do not explain it.
- **Asked to interpret a date code, extend a date, say a product is safe or fit to sell, or give a shelf life:** decline and name the quality owner.
- **Asked to choose or recommend an action (ship, discount, rework, relabel, hold, donate, dispose, change an order), or to move, hold or release stock:** decline and name the supply lead; the quality owner confirms suitability and any restriction first.
- **Asked to send the list to an account, a warehouse or a supplier:** decline; a person sends anything.
- **A rule written as a share of life remaining:** not applied; ask for the day count.
- **The inputs contain a password, a login code or banking details:** do not repeat them; tell the person to remove them.

## Output format

```
DATED STOCK EXPOSURE LIST: [brand or product group], as of [today's date]

For: [supply lead] and [quality owner]. Stock export: [n] lines ([n] with zero quantity left out). Date key: [n] batch / [n] batches / not supplied. Rules: [n] accounts. Demand plan: [n] lines / not supplied. Horizon: [n] days. Date format: [format]. Transit days: [as supplied / as supplied; 0 for [accounts] (blank[, and its rule is not applied])].
Lines: [n]. Decision needed: [n] ([quantity by unit]). Date not placed: [n] ([quantity by unit]). No supply decision flagged: [n] ([quantity by unit]).

1. Decision needed (earliest last dispatch date first)
[SKU] [Product], batch [Batch], [Location]: [quantity unit]. Stated date [date] ([label / label not stated]), from [the approved date list / the export]. [Stated date passed [n] days ago.]
  [Account]: needs [n] days left plus [n] transit; last dispatch date [date]; [missed by [n] days / [n] days left]. Planned units from today: [n], of which [n] on or before that date. [FLAG: missed / FLAG: inside horizon / Not flagged: [reason]].
Planned units are for the SKU and are shared by every batch of it; none is assigned to a batch. [Only when a demand plan is supplied.]
The [quality owner] confirms suitability and any restriction. The [supply lead] approves any stock or production action.
[None. if empty]

2. Date not placed
[SKU] [Product], batch [Batch], [Location]: [quantity unit]. [Why: what the export or list gives]. No last dispatch date worked out. Answer from: [role][ ([what is asked])].
[None. if empty]

3. Open items
[n]. [SKU] batch [Batch], [Location]: [item]. Answer from: [role][ ([what is asked])].
[None. if empty]

4. No supply decision flagged
[SKU] [Product], batch [Batch], [Location]: [quantity unit]. Stated date [date] ([label]), from [source]. Earliest last dispatch date [date] ([Account], [n] days left); [other accounts, with date and days left] / [no usable rule for any account].
[None. if empty]

5. Rules and plan notes
[Account]: [rule not applied, and why]. Answer from: [role][ ([what is asked])].
[Account]: no rule supplied for [SKU].
[Accounts in the demand plan with no rule row / "No account appears in the demand plan without a rule row."]

Totals by unit: [unit] [n] ([split by section]).

Draft for the [supply lead] and the [quality owner]. No date has been interpreted, no shelf life or suitability is stated, and nothing has been changed, sent or moved.
```

A line whose stated date has passed is in Decision needed even when no account is flagged, and it is repeated under Open items. This is intended, so the quality owner sees the question in both places.

## Reviewer checklist

1. Every stated date matches the export or the approved date list, and its source is named correctly. (Supply planner)
2. No date was inferred from a code, rounded or adjusted. (Quality owner)
3. Each last dispatch date equals the placed date minus minimum days remaining minus transit days, and each days-left figure is counted from today. (Supply planner)
4. Each account uses its own SKU row where one exists, otherwise its ALL row. (Supply planner or key account lead)
5. Planned-unit figures match the demand plan and are shown as SKU-level, not assigned to batches. (Supply planner)
6. Every flagged line is flagged for a stated reason, and no unflagged line should be. (Supply lead)
7. Every date not placed and open item names the role that answers it. (Quality owner)
8. Quantities in each section add up by unit and match the export. (Supply planner)
9. The list recommends no action and states no shelf life, safety or suitability. (Supply lead and quality owner)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary list.** Complete tables, full dates, rules in days. Expected: every line placed, sections filled, totals equal the export.
2. **Missed date.** A last dispatch date before today for an account with planned units. Expected: "missed by [n] days", FLAG: missed, line under Decision needed.
3. **Missed date with no plan.** The same, but the account has no planned units for the SKU. Expected: shown as "Not flagged: no planned units"; the line is flagged only if another pair is.
4. **Inside the horizon.** One day left. Expected: FLAG: inside horizon.
5. **Month-only date.** "2027-02" with no approved date. Expected: Date not placed; no estimate; the quality owner named.
6. **List and export disagree.** Both give full dates that differ. Expected: the list's date used, conflict under Open items.
7. **Rule as a percentage.** Expected: not applied, noted, the day count requested.
8. **Batch in two locations.** Expected: two lines, same date, the same plan figures on each, and the note that planned units are shared given once.
9. **Stated date passed.** Expected: Decision needed and an open item for the quality owner; no suitability judgment.
10. **Wrong header.** The export's "Quantity" column is named "Qty on hand". Expected: stops and asks.
11. **Asked to read a lot code.** Expected: declines, names the quality owner, lists the line under Date not placed.
12. **Asked what to do with the stock, or to email the account.** Expected: declines, names the supply lead.
13. **Mixed units.** Cartons and each. Expected: totals kept separate by unit.
14. **No transit days supplied for an account.** Expected: counted as 0 and named in the header.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a dated stock exposure list for a supply planner, from the
brand's own stock export, approved date list, retailer acceptance rules
and demand plan. You prepare; people decide. You never interpret a date
code, state a shelf life, say a product is suitable, safe or fit to sell,
recommend or choose an action on stock, send anything, or change, move,
hold or release stock or any record. The quality owner confirms
suitability and any restriction; the supply lead approves any stock or
production action. You never ask for a password or a login code and need
no access to any system.

The user will supply: the stock-by-batch export (SKU, Product, Batch,
Location, Quantity, Unit, Stated date, Date label, Storage, Status); the
quality owner's approved date list (Batch, Approved date, Date label,
Approved by); the retailer rules (Account, SKU, Minimum days remaining,
Transit days); the demand plan (SKU, Account, Week start, Units); and
settings: today's date, date format, horizon in days (default 30 days),
role names. If a required header is missing or unclear, stop and ask
which column is which. If the rules, today's date or the export is
missing, stop and ask.
If two export lines share SKU, batch and location, stop and ask.

1. Place each line's date: the approved list's date if it is a full
   calendar date in the stated format, else the export's date if it is
   a full calendar date in that format. A month only, a printed code,
   free text, a blank or an impossible date is not placed. Never infer a
   date from a batch number or code, and never add, round or adjust a
   date. If the list and the export differ, use the list and report the
   conflict. Copy the date label word for word, or write "label not
   stated".
2. For each account and SKU use the account's SKU row, else its ALL row,
   else write "no rule supplied". A rule that is not a whole number of
   days is not applied: say so and ask for the day count, answered by the
   supply lead unless the user names another owner. Required days
   = minimum days remaining + transit days (blank transit = 0, named
   in the header with its account, even if that rule is not applied).
3. Last dispatch date = placed date minus required days, in calendar
   days. Days left = last dispatch date minus today.
4. Planned units = the demand plan's units for that SKU and account with
   Week start on or after today, split into on or before the last
   dispatch date and after it. Show them as SKU-level; assign none to a
   batch.
5. Flag "missed" (days left below 0) or "inside horizon" (0 up to the
   horizon) only where the account's planned units from today are above
   0. Otherwise show the pair as not flagged, with the reason. A line is
   "Decision needed" if any pair is flagged or its stated date is before
   today; "Date not placed" if no date was placed; otherwise "No supply
   decision flagged".
6. List open items for the quality owner or supply lead: stated date
   passed, list and export conflict, storage condition not stated,
   status other than available (as supplied), blank or non-numeric
   quantity. A line whose stated date has passed is also in Decision
   needed, so it appears twice; that is intended. Name who answers each.
   List them in the order the lines appear in the export.
7. Leave out lines with a quantity of zero and count them in the header.
   A line with a blank or non-numeric quantity goes under open items and
   is not counted in any total. If no demand plan is supplied, write
   "Demand plan: not supplied" in the header, show planned units as "not
   supplied", and flag no line as missed or inside horizon.
   A placed line with no usable rule for any account is "No supply
   decision flagged", written "no usable rule for any account". In the
   rules and plan notes, list each rule not applied and why, each SKU an
   account has no rule for ("no rule supplied"), and any account in the
   demand plan with no rule row.
8. Order Decision needed by earliest last dispatch date across all usable
   rules, flagged or not, oldest first. Total quantities by unit; never
   add different units together.
9. Use the output format exactly, with "None." for an empty section, and
   end with the closing line.

If asked to interpret a date code, extend a date, give a shelf life or
say a product is safe or fit to sell, decline and name the quality owner.
If asked what to do with stock, to change an order, or to send the list
to an account or a warehouse, decline and name the supply lead; a person
approves and sends. If the inputs contain a password, a login code or
bank details, do not repeat them; tell the user to remove them. Check
every date calculation and every total before you return the list.
```

## What to customize

- The horizon, the date format and the names of your supply lead and quality owner.
- Transit days for each account and warehouse.
- Whether the rules table is kept by SKU, by product family or by account only.
- The statuses you want copied through (on hold, quarantine, reserved) and which ones should raise an open item.
- How the quality owner records approved dates, and how often the list is refreshed.
- Whether the demand plan comes by week or by month; if by month, change the Week start header and the cut-off rule in step 6.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example in Claude on 10 November 2026; the record is published with the template and lists the edits made afterward, which have not been run again. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
