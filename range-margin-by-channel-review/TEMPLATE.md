# Range margin by channel review

Capability template, version 0.1.0.

## Purpose

Prepare one margin worksheet for the finance lead of a consumer brand that sells the same range through more than one channel. From a sales export, a unit cost file and a channel cost file, the assistant works out, for every product in every channel it sold through, the net sales and each cost layer (product, packaging, freight and channel fees), marks each layer confirmed, estimated or missing, and shows two margins: one on confirmed costs alone and one with estimates added. Missing costs, unmatched variants and estimated allocations are kept apart from confirmed figures and listed as questions. The worksheet recommends no price and no channel decision. The assistant never changes a price, a cost or any record, never invents a cost, and never sends or publishes anything. The finance lead approves the cost basis; the commercial owner decides what to do about it.

## When to use it and when not to

Use it when a wholesale offer, a promotion or a change in channel terms puts the economics of a range in question, ahead of a range review, or when someone asks which products earn money in which channel. The offer or promotion is the occasion for the review; its terms are not an input, and the worksheet does not model them. Run it again when a missing cost arrives or an estimate is confirmed.

Do not use it:

- to test a proposed price list across a range of customer responses. That is a price change review;
- to build a product's cost from an import shipment's freight, duty and brokerage invoices. That is a landed cost worksheet, and its result can then be supplied here as the product cost;
- to judge one customer's request for a lower price. That is a discount request review;
- to choose a price, rank products or channels, or say whether to drop a channel. The commercial owner decides that;
- to interpret an agreement with a retailer or marketplace. Fees and allocations are taken as supplied.

## Roles

- **Runs it:** the finance lead, the bookkeeper or the founder.
- **Supplies the exports and the cost files:** whoever keeps the sales data and the costs, such as the bookkeeper, the sourcing lead or the operations lead.
- **Approves the cost basis and settles every gap:** the finance lead.
- **Decides on pricing or channel changes:** the commercial owner.
- **Changes a price, a cost record or a listing:** a person, after the decision.

## Inputs

1. **The sales export,** one row for each product and channel, for one stated period. Default column headers: `SKU`, `Channel`, `Units`, `Gross sales`, `Discounts`, `Returns`. `Units` are units the customer kept, after returned units; `Gross sales`, `Discounts` and `Returns` are money. Rows with the same `SKU` and `Channel` are added together. If the export is missing, stop. If any default header is missing or named differently, stop and ask which column holds what; never guess a column.
2. **The unit cost file,** one row for each product and cost layer. Default column headers: `SKU`, `Cost layer`, `Unit cost`, `Status`. Default layers: `Product` and `Packaging`. `Status` is `Confirmed` or `Estimated`. If the file is missing, stop. If a header does not match, stop and ask.
3. **The channel cost file,** one row for each channel and cost layer. Default column headers: `Channel`, `Cost layer`, `Basis`, `Rate`, `Status`. Default layers: `Freight`, with the basis `per unit` and a rate in money, and `Channel fees`, with the basis `% of net sales` and a rate in percent. Agreed allocations go here as rows marked `Estimated` or `Confirmed`. If the file is missing, stop. A channel layer that truly carries no cost, such as no channel fee on wholesale invoiced direct, is recorded by the finance lead as a row with the basis `not applicable`, a blank `Rate` and the status `Confirmed`. If a header does not match, or a basis is anything else, stop and ask.
4. **The settings:** business name, review date, period, currency, who reads the worksheet, who prepared it and [your margin floor, default none]. Items in square brackets, here and in the procedure, are these settings. If a setting is missing, use the default and list it under "Defaults used".

The assistant works from the files and notes the person supplies. It needs no connection to the accounting system, the shop platform or a marketplace, and never asks for a password or a login code.

## The procedure

1. **Check the files.** Confirm the default headers in all three files, one stated period, and the status values. If a header does not match, stop and ask. If a `Status` is blank or anything other than `Confirmed` or `Estimated`, stop and ask. If the same product and layer appear twice in the unit cost file, or the same channel and layer twice in the channel cost file, stop and ask which row is meant. Match products and channels by their exact text. List the lines in the order of the sales export; list channels in the order they first appear in the channel cost file.
2. **Net sales.** For each line, net sales = gross sales − discounts − returns. A line with net sales of zero or less, or units of zero or less, gets no margin; list it under Data notes with a question.
3. **Cost layers.** Product cost = units × the product's unit cost for the layer `Product`. Packaging = units × the unit cost for `Packaging`. Freight = units × the channel's per-unit freight rate. Channel fees = the channel's percent rate × net sales. Round each cost line to the cent.
4. **Missing means missing.** A layer is missing when there is no row for it, or its amount is blank or zero. Never use zero or a guess in its place. The one exception is a channel layer whose row has the basis `not applicable` and the status `Confirmed`: it costs nothing, counts as a Confirmed layer of $0.00, and is shown as "not applicable". Show a missing layer as "not supplied" and add it to the gaps. A product in the sales export with no rows at all in the unit cost file is an unmatched variant: list it under the gaps with its channel lines and net sales, and ask whether it is a variant of another product. It is listed there as Unmatched only, not also as Missing.
5. **Two margins.** Margin on confirmed costs = net sales − the layers marked Confirmed. Margin with estimates = that, less the layers marked Estimated. Margin % = margin ÷ net sales, to one decimal place. A layer that is missing is in neither. A line is Complete when no layer is missing, whatever the status of its other layers; a line carrying Estimated layers is therefore still Complete. A line with no margin shown is counted only under No margin shown.
6. **When a layer is missing.** If the Product layer is missing, show no margin on that line: write "no margin shown: no product cost". If any other layer is missing, show both margins and mark the line INCOMPLETE with the missing layers named, because both margins are before those layers.
7. **Flags.** Mark LOSS on a line whose margin with estimates is below zero, and BELOW FLOOR on a line whose margin % with estimates, rounded to one decimal place, is under [your margin floor]. If no floor is set, mark no line BELOW FLOOR. An INCOMPLETE line keeps its flag, and the flag is read as "at least this low, because costs are still missing".
8. **The grid.** For each product, one line giving its margin % with estimates in each channel, in channel order. Write "incomplete" after a figure from an INCOMPLETE line, "n/a" where no margin is shown, and "no sales" for a channel in which the product has no line.
9. **The gaps.** One list: every missing layer, every estimated layer, and every unmatched variant, each with the lines it touches. An estimated layer is listed once, with the lines that carry it, including a line that has no margin shown. An unmatched variant is listed as Unmatched only; do not also list its missing layers.
10. **Tie out.** Add net sales across all lines and compare with total gross sales − total discounts − total returns in the sales export; add units and compare with the export. Lines with no margin are included in both sums. This check catches a dropped or excluded line; it cannot catch a mistake in the export itself, so if the person supplies a control total from the ledger or the shop platform, compare with that too. If either differs, stop, report both figures and the difference, and ask the person who supplied the export.
11. **Data notes.** Lines with no margin and why; products in the unit cost file with no sales, or "none"; channels with no rows in the channel cost file, or "none"; and the standing assumptions: units are net of returns; returned goods and return freight are not costed; costs and rates cover the whole period; allocations are used as supplied.
12. **Questions for the finance lead.** One numbered question, with its facts, for each gap, each unmatched variant and each line left without a margin. Ask for the missing figure or for confirmation of the estimate. Ask nothing about which price to set or which channel to keep.
13. **Round and check.** Money to two decimal places, written with the currency's symbol where it has one and thousands separators, such as $1,234.50; percentages to one. Recompute every figure and every count before returning.
14. **Return the worksheet** to the person who ran it, for the finance lead's review, and stop.

## Exceptions and stop conditions

- **A file is missing or a default header does not match:** stop and ask which column holds what.
- **A status is blank, or a basis other than `per unit`, `% of net sales` or `not applicable`:** stop and ask.
- **A duplicate row for a product and layer, or a channel and layer:** stop and ask which is meant.
- **The tie-out fails:** stop; report both figures and the difference.
- **A cost of zero or blank:** treat as missing and ask the finance lead whether the layer is not applicable for that channel or the figure is still to come. Never fill it.
- **Asked to choose a price, rank the products or channels, say whether a channel should be dropped, or compare against an offer's terms:** decline; offer to rerun with updated costs, and point to the price change review for a proposed price.
- **Asked to model an offer's terms:** decline; the offer is the occasion for the review, not an input. Offer to rerun with updated costs.
- **Asked to change a price, a cost record or a listing, or to tell a customer or retailer anything:** decline; a person does that after the decision.
- **Asked to estimate a missing cost, borrow another product's cost or spread an allocation:** decline; list it as a gap.
- **A file contains a customer's personal details, bank details, a password or a login code:** do not repeat them; tell the person to remove them from the source.

## Output format

```
RANGE MARGIN BY CHANNEL REVIEW: [business], prepared [review date]

For: [reader]. Prepared by the [role] on [date], for the [finance lead role]'s review.
Sources: sales export, [period], [n] lines; unit cost file, [n] rows; channel cost file, [n] rows.
Settings used: currency [currency]; margin floor [n% / none set]. Defaults used: [settings / none].

THE PICTURE
Lines: [n], of [n] products in [n] channels. Complete: [n]. Incomplete: [n]. No margin shown: [n]. Below zero: [n]. Below floor: [n / no floor set].
Tie-out: net sales across lines [amount] = gross sales [amount] − discounts [amount] − returns [amount]. Units [n] = [n].

THE GRID
Margin % with estimates.
[Product]: [Channel] [n]%[ incomplete]; [Channel] [n/a]; [Channel] no sales.

MARGIN BY PRODUCT AND CHANNEL
[Product], [Channel]: [units] units. Gross sales [amount], discounts [amount], returns [amount], net sales [amount].
  Costs: Product [amount, Confirmed / Estimated / not supplied]; Packaging [amount, status / not supplied]; Freight [amount, status / not supplied / not applicable]; Channel fees [amount, status / not supplied / not applicable].
  Margin on confirmed costs: [amount], [n]%. With estimates: [amount], [n]%. [INCOMPLETE: no [layers]; both margins are before them.] [LOSS.] [BELOW FLOOR.]
[Product], [Channel]: [units] units. Net sales [amount]. No margin shown: no product cost. Found: [layers and amounts].
[None.]

THE GAPS
Missing: [layer], [product or channel]: touches [lines].
Estimated: [layer], [product or channel]: [rate or unit cost]; carried by [lines].
Unmatched: [product] in [channel], [units] units, net sales [amount]: no rows in the unit cost file.
[None.]

DATA NOTES
[Line]: [no margin and why].
Products in the unit cost file with no sales in the period: [list / none]. Channels with no rows in the channel cost file: [list / none].
Assumption: units are net of returns; returned goods and return freight are not costed.
Assumption: costs and rates cover the whole period, and allocations are used as supplied.

QUESTIONS FOR THE FINANCE LEAD
[n]. [Product or channel, layer]: [the facts]. [The question.]
[None.]

Prepared for the [finance lead role]'s review. It recommends no price and no channel decision. No price, cost or record has been changed, and nothing has been sent or published.
```

## Reviewer checklist

1. Every unit count, gross sales, discount and returns figure matches the sales export, and the tie-out is arithmetically right. (Bookkeeper)
2. Every cost line is right for its units or net sales, rounded to the cent, and carries the status the cost file gives it. (Finance lead)
3. Both margins are right for every line, and each INCOMPLETE line names every layer that is missing. (Finance lead)
4. No cost of zero or blank was used, and no cost was borrowed from another product or channel. (Finance lead)
5. Every estimated layer, missing layer and unmatched variant is on the gaps list with the lines it touches. (Finance lead)
6. The grid agrees with the line figures. (Analyst)
7. Nowhere does the worksheet say what a price should be, or which product or channel to favour. (Commercial owner)
8. The closing line is present, and nothing has been changed or sent. (Finance lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary quarter.** Three products, three channels, one confirmed and one estimated layer in each cost file. Expected: every section filled; two margins on every line; tie-out shown and correct.
2. **Header not matched.** The sales export has `Product`, `Qty`, `Revenue`. Expected: stops and asks which column is which; does not guess.
3. **Missing layer.** One product has no packaging row. Expected: its lines marked INCOMPLETE with packaging named; both margins labelled as before it; packaging on the gaps list and in the questions.
4. **Unmatched variant.** A product in the sales export with no rows in the unit cost file. Expected: no margin shown for it; listed as unmatched with its net sales; a question asking whether it is a variant of another product.
5. **Zero rate.** A channel fee row with a rate of 0. Expected: treated as missing, not as no fees; a question asking whether the layer is not applicable.
12. **Not applicable.** A channel fee row with the basis `not applicable`, a blank rate and the status Confirmed. Expected: the fee shown as not applicable and counted as Confirmed at $0.00; the line is not INCOMPLETE on that account.
6. **Tie-out fails.** Net sales across lines differ from the export's totals. Expected: stops; reports both figures and the difference.
7. **Loss.** A line where costs exceed net sales. Expected: LOSS marked, with the negative margin shown.
8. **Duplicate cost row.** Two rows for the same product and layer. Expected: stops and asks which is meant.
9. **Asked to estimate.** "Use the packaging cost of the other granola for the box." Expected: declines; lists the gap.
10. **Asked to choose.** "Should we drop the marketplace?" Expected: declines; offers to rerun with updated costs, and points to the price change review for a proposed price.
11. **Asked to update.** "Change the wholesale price list to these." Expected: declines; a person does that after the decision.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a range margin by channel review for the finance lead of a
consumer brand. You prepare; people decide. The finance lead approves
the cost basis and the commercial owner decides on any price or channel
change. You never recommend a price, rank products or channels, or say
whether a channel should be kept. You never change a price, a cost, a
listing or any record, never invent or borrow a cost, and never send or
publish anything. Never ask for a password or a login code; work only
from what the user supplies.

The user will supply: a sales export (SKU, Channel, Units, Gross sales,
Discounts, Returns) for one stated period; a unit cost file (SKU, Cost
layer, Unit cost, Status) with the layers Product and Packaging; a
channel cost file (Channel, Cost layer, Basis, Rate, Status) with the
layers Freight (basis per unit) and Channel fees (basis % of net
sales). A channel layer that truly has no cost may carry the basis
not applicable, a blank Rate and the status Confirmed. The settings are
business, review date, period, currency, reader, preparer and margin
floor. If a file is missing, stop. If any header is missing or named
differently, or a Status is anything but Confirmed or Estimated, or a
Basis is anything but per unit, % of net sales or not applicable, stop
and ask; never guess a column. If the same product and layer, or channel and
layer, appear twice, stop and ask which row is meant. Units are units
kept after returns. Sales rows with the same SKU and Channel are added
together. List lines in the order of the sales export.

1. Net sales = gross sales - discounts - returns. A line with net sales
   or units of zero or less gets no margin; list it and ask.
2. Product = units x unit cost; Packaging = units x unit cost; Freight
   = units x the channel's per-unit rate; Channel fees = percent rate x
   net sales. Round each cost line to the cent.
3. A layer is missing when there is no row or the amount is blank or
   zero. Never use zero or a guess; ask whether the layer is not
   applicable or the figure is still to come. Show it as "not
   supplied". The one exception is a channel layer with the basis not
   applicable and the status Confirmed: it counts as a Confirmed $0.00
   layer and is shown as "not applicable". A product with no rows in
   the unit cost file is an unmatched variant.
4. Margin on confirmed costs = net sales - Confirmed layers. Margin
   with estimates = that less Estimated layers. Margin % = margin / net
   sales, one decimal. If the Product layer is missing, show no margin
   and write "Found:" with the layers that are present and their
   amounts. If another layer is missing, show both margins and mark the
   line INCOMPLETE, naming the layers; both margins are before them. A
   line is Complete when no layer is missing, whatever the status of
   the others; a line with no margin shown is counted only as such.
5. Mark LOSS where the margin with estimates is below zero. Mark BELOW
   FLOOR where its margin %, rounded to one decimal, is under the
   floor, if one is set.
6. The grid: for each product, its margin % with estimates in each
   channel, in the order the channels first appear in the channel cost
   file; "incomplete" after a figure from an incomplete line, "n/a"
   where no margin is shown, "no sales" where there is no line.
7. The gaps: every missing layer, every estimated layer and every
   unmatched variant, with the lines each touches. Include a line with
   no margin among the lines that carry an estimated layer. List an
   unmatched variant as Unmatched only, not also as Missing.
8. Tie out: net sales and units across lines must equal the export's
   totals; lines with no margin are included in the sums. This catches a
   dropped line only; if the user gives a control total, compare with
   it too. If not equal, stop and report both figures and the
   difference.
9. Data notes: lines with no margin and why; products in the unit cost
   file with no sales, or none; channels with no rows in the channel
   cost file, or none; and the two standing assumptions. Questions for
   the finance lead, numbered, each with its facts: every gap, unmatched
   variant and line without a margin. Never ask which price to set.
10. Money to two decimals, percentages to one. Recompute every figure.
    Write money with the currency's symbol where it has one and
    thousands separators, such as $1,234.50. Use the output format
    exactly. Write "None." under any empty section as the format shows.
    End with the closing line.

If asked to choose a price, rank the options, or say whether to drop a
channel, decline and offer to rerun with updated costs; for a proposed
price, point to the price change review. If asked to model an offer's
terms, decline: the offer is the occasion for the review, not an input. If asked to change a price, a cost or a listing, or to
tell a customer or retailer, decline; a person does that after the
decision. If asked to estimate a missing cost or borrow one, decline and list it as a gap. If a file
holds a customer's personal details, bank details, a password or a
login code, do not repeat them; tell the user to remove them.
```

## What to customize

- The column headers your systems export, so the assistant reads them as they come.
- Your channels, and the fees and freight each one carries.
- Your cost layers: the defaults are product, packaging, freight and channel fees. Add or remove layers to match how your finance lead builds a cost, and agree what makes a cost Confirmed rather than Estimated.
- The period; a quarter is a sensible default.
- [your margin floor].
- Which channel layers truly carry no cost; record each as `not applicable` (blank rate, status Confirmed) so it is not treated as missing.
- Whether your reports show margin on net sales, as written here, or on gross sales.
- The currency, and whether sales and costs include sales tax. As written, everything is compared on the basis the exports use.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini, and where the finished worksheet is kept.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Editorially reviewed. Tried once on its invented example in Claude on 10 November 2026; the record is published with it. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
