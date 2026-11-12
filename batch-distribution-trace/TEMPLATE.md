# Batch distribution trace

Workflow template, version 0.1.0.

## Purpose

Give the quality lead one trace of where a single production batch went, according to the company's own records: what was produced and received, every move between locations with a running balance, every dispatch line that carries the batch code, every repacking link to a new batch code, and every gap where the records stop agreeing. Each gap is numbered, sized in units and written as a question for a named role. The assistant reads and reports. It confirms no scope, orders no hold, contacts nobody, makes no regulatory judgment and changes no record.

## When to use it and when not to

Use it when a quality concern, a report from a supplier or production partner, or a complaint points at one named batch and the quality lead needs to see where the records say it went, before anyone decides what to do.

Do not use it to run the response once a recall has been decided, which is the work of the product recall customer contact plan. Do not use it to compare a physical count with the books, which is stock count reconciliation. Do not use it to decide whether a product is safe, whether to recall it, or whether anything must be reported to an authority. Those decisions belong to people.

## Roles

- **Starts it and names the batch:** the quality lead.
- **Supplies the files and verifies the matches:** operations, usually the warehouse or logistics lead.
- **Answers questions about a production partner's records:** the person who manages that partner.
- **Confirms the affected scope and decides what follows:** the quality lead, with whoever the company's own procedures name.

## Inputs

Four files, plus the settings. Each file is read by header, using the default headers below. If a required header is missing or named differently, stop and ask which column to use. Never guess a column.

1. **Batch record.** Headers: `batch_code`, `sku`, `product_name`, `production_date`, `quantity_produced`, `unit`. The batch to trace must appear exactly once. If it is missing or appears twice, stop.
2. **Movement export.** Headers: `movement_id`, `movement_date`, `batch_code`, `sku`, `from_location`, `to_location`, `quantity`, `unit`, `movement_type`, `document_ref`. The movement types are `receipt` (into the first location, from the producing site), `transfer`, `return` (back into a location from a customer) and `adjustment` (a signed quantity at `to_location`). If a movement type is anything else, stop and ask.
3. **Repacking records.** Headers: `repack_id`, `repack_date`, `source_batch_code`, `source_quantity`, `location`, `new_batch_code`, `new_sku`, `new_quantity`, `unit`. If none exist, the user says so; write "none supplied" and trace no repacking.
4. **Dispatch lines.** Headers: `dispatch_id`, `dispatch_date`, `batch_code`, `sku`, `quantity`, `unit`, `ship_from`, `destination`, `retailer_reference`, `carrier_reference`. A blank retailer or carrier reference is allowed and is reported as "none". Include the dispatch lines for any new batch code created by repacking.
5. **Settings.** The batch code to trace, the unit, the name of the quality lead and of operations, and, if a production partner is involved, the person who manages that partner. If the unit differs between files, stop.

## The procedure

1. **Check the files.** Confirm every header. Confirm the dates read as dates and the quantities as numbers. Confirm one unit throughout. Stop on any failure and say which file and column.
2. **Fix what is being traced.** The batch code is matched exactly as written, including case, hyphens and spaces. Never treat two different strings as the same batch.
3. **Find the codes that are not exact.** Across the movement and dispatch files, list every code that is not the exact code but differs from it only by case, spaces, a hyphen, or a leading or trailing character (a near-match), and every code field that holds two or more codes joined by a slash, plus, comma or "and" (a mixed lot). Near-matches and mixed lots are never merged into the trace, split or assigned.
4. **Tie production to receipt.** Add the `receipt` quantities for the exact code and compare them with `quantity_produced`. A difference is a gap, with the difference in units.
5. **Build the ledger.** Take every event for the exact code and put them in date order: receipts, transfers, returns, adjustments, repacking out and dispatches. On the same date, apply movements into a location before movements out. Keep a running balance for each location after every event. A transfer moves the quantity from one location to the other. A dispatch and a repacking record reduce the balance at their location. A return and a positive adjustment add; a negative adjustment reduces.
6. **Flag impossible moves.** If an event takes a location's balance below zero, record the event as an unmatched transfer (or an unmatched dispatch), keep the negative balance visible in the ledger, and make it a gap with the quantity by which the record exceeds the stock recorded there. Never adjust a quantity to avoid it.
7. **Map the dispatches.** Each dispatch line carrying the exact code is one line of the map, with its route (producing site, then the locations the ledger shows the batch passing through, then the destination) and a status: traced, or the gap number that applies. A line is traced only if the shipping location had recorded stock of the batch on the dispatch date.
8. **Follow repacking.** For each repacking record with the exact code as source, reduce the source balance by `source_quantity` and open the `new_batch_code` as a linked batch at that location with `new_quantity`. Compare the two quantities; a difference is a gap. If the units differ between source and new, stop and ask for the agreed conversion; never assume one. Then run steps 5 to 7 for the new code, using its own dispatch lines and movements. Repeat for any further repacking until none remains.
9. **Place the unplaced lines.** Three kinds of dispatch line stay unplaced and are never counted into or out of the balances: a mixed-lot line (quantity not split), a line with a near-match code, and a line with a blank batch code. List a blank-code line only if its SKU matches and the shipping location has a recorded receipt or transfer-in of the batch on or before the dispatch date; it is a candidate, never a match. Count the blank-code lines for the SKU that were not from such a location and print the count without listing them.
10. **Write the gaps.** Number them in the order of the gap types listed here. Each has a type, the rows it involves (by id), the quantity at stake in units, and one question for a named role. The gap types are: receipt differs from production; unmatched transfer or dispatch; repack quantity differs; mixed lot; no batch code; near-match code.
11. **Tie out.** Received, minus every direct dispatch of the exact code posted to the ledger (traced or not, including one that took a location below zero, but not the unplaced lines), minus the quantity repacked out, plus returns and adjustments, must equal the sum of the location balances. State the arithmetic. If it does not hold, stop and report the figures.
12. **Close.** Total the quantity in unplaced lines. State what the records show by destination, what operations is asked to verify, and that the quality lead confirms the scope. If any gap is open, say that an incomplete trace cannot show that no other stock is affected. Return the trace to the quality lead only.

## Exceptions and stop conditions

- **A header is missing or differs from the default:** stop and ask which column to use.
- **The batch is missing from the batch record, or appears twice:** stop.
- **Units differ between files, or a repack changes the unit:** stop and ask for the conversion.
- **A movement type is not one of the four:** stop and ask.
- **The tie-out fails:** stop and report the figures and the difference.
- **Missing batch codes, mixed lots and unmatched transfers:** these stay open as gaps. Nothing is inferred from a quantity, a date or a destination.
- **No gaps are found:** say so, and say that the result covers only the records supplied.
- **Asked to confirm the scope, to say stock is or is not affected, to recommend a hold, a recall or a report to an authority, to contact a retailer, customer or warehouse, or to correct a record:** decline. The quality lead decides, and operations makes any contact or correction.

## Output format

```
BATCH DISTRIBUTION TRACE: [batch code], [product name] ([SKU])

For: [quality lead], to confirm scope with [operations]. Records used: batch record [file name, or "pasted" if it was pasted rather than uploaded]; movements to [last date]; repacking records [file or "none supplied"]; dispatch lines [first date] to [last date]. Prepared [date].

1. The batch
Produced: [n] [unit] on [date]. Recorded as received: [n] [matches production, or n units fewer or more: G#].

2. Where it moved
[date] [id]: [event, from and to or location, quantity] ([document or reference]). [Location] now [balance].
(one line per event, in date order; a negative balance is printed as it is)
Recorded balance by location: [location] [n]; [location] [n]. Total [n].

3. Batch-to-shipment map
[dispatch_id], [date]: [n] from [location] to [destination]; retailer reference [ref or none]; carrier [ref or none]. Route: [producing site, locations]. Status: [Traced, or G#].
Recorded to each destination (traced, direct): [destination] [n]; [destination] [n]. Total [n].
Unplaced lines (not counted): [dispatch_id], [date]: [n] from [location] to [destination]; [why unplaced: G#].
Blank-code lines for this SKU from locations with no record of the batch, not listed: [n].

4. Repacking links
[repack_id], [date]: [n] of [batch code] into [new code] ([new SKU]) at [location]; [n] recorded as made, [difference: G#]. Shipments of [new code]: [dispatch lines in the same form as section 3]. Balance of [new code]: [location] [n].
(if none: None in the records supplied.)

5. Gaps in the trace
G[#]. [Type]: [rows]. Quantity at stake: [n] [unit] (written "up to [n]" for mixed-lot, no-code and near-match lines). Question for [role]: [question].
(if none: None in the records supplied.)

6. For the quality lead and operations
Tie-out: [received] - [direct dispatches posted to the ledger, traced or not] - [repacked out] [+ returns and adjustments] = [n]; location balances add to [n].
What the records show: [n] units to [n] destinations through traced dispatch lines; [n] units to [destination] through [new code]; still recorded on hand: [locations and quantities].
Quantity not placed: [n] [unit] in [n] lines ([gap numbers]).
Operations to verify: [each traced dispatch line against the carrier and retailer documents; the answers to the questions in section 5].
Open gaps: [n]. [If any: This trace is incomplete, so it cannot show that no other stock is affected.] The quality lead confirms the affected scope, and operations verifies each match, before any hold or contact. This trace decides no recall or regulatory question, contacts nobody and changes no record.
```

## Reviewer checklist

1. Every figure in the trace can be found in a row of the files supplied. (Operations)
2. The ledger balances are correct after every event, and the tie-out line is arithmetically right. (Operations)
3. No near-match, mixed-lot or blank-code line has been counted into a balance or a destination total. (Quality lead)
4. Every gap has a type, rows, a quantity and one question for a named role. (Quality lead)
5. Each repacking record is followed to its new code and its shipments. (Operations)
6. The trace says nowhere that stock is, or is not, affected, safe, or subject to a recall or a report. (Quality lead)
7. Empty sections are printed as "None in the records supplied." (Quality lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Clean batch.** Produced 1,000, received 1,000, two dispatches of 400 and 350 from the receiving location, nothing else. Expected: ledger balance 250; tie-out 1,000 - 750 = 250; gaps "None in the records supplied"; the closing line says the result covers only the records supplied.
2. **Header mismatch.** The dispatch file names its quantity column `qty`. Expected: stops and asks which column to use; produces no trace.
3. **Short receipt.** Produced 2,400, receipts total 2,376. Expected: a receipt-differs gap of 24 units.
4. **Transfer beyond stock.** A location holds 358 and a transfer takes out 380. Expected: balance shown as -22 and an unmatched-transfer gap of 22.
5. **Mixed lot.** A dispatch line carries "B2611A/B2611B" for 120 units. Expected: not split, not counted, listed as unplaced with up to 120 at stake.
6. **Blank code.** A 96-unit line has no code, matching SKU, shipped from a location that received the batch. Expected: listed as a candidate gap, not a match. A second blank-code line from a location with no record of the batch is counted, not listed.
7. **Near-match.** A line carries "B2611-A" for the batch "B2611A". Expected: reported as a near-match gap, not merged.
8. **Repack changes unit.** Source in units, new batch in cases. Expected: stops and asks for the conversion.
9. **Repack with fewer units.** 360 in, 354 out. Expected: gap of 6 units; the new code's shipments are traced separately.
10. **Asked for a verdict.** The user asks whether any stock is unaffected or whether to hold the batch. Expected: declines, restates the open gaps, and leaves the decision with the quality lead.

## Instructions for the AI assistant

```
You prepare a batch distribution trace for the quality lead: where one
production batch went, according to the records supplied. You never
confirm the affected scope, order a hold, contact anyone, make a
regulatory judgment, or change a record. Anything that sends, posts, pays
or changes a record waits for a person's approval, and you do none of it.
Never ask for a password or a login code.

The user supplies: a batch record, a movement export, repacking records
(or says there are none), dispatch lines, and the settings: the batch code
to trace, the unit, who the quality lead and operations are, and who
manages any production partner. Dispatch lines include those for any new
batch code created by repacking. Default headers. Batch record:
batch_code, sku, product_name, production_date, quantity_produced, unit.
Movements: movement_id, movement_date,
batch_code, sku, from_location, to_location, quantity, unit,
movement_type (receipt, transfer, return, adjustment), document_ref.
Repacking: repack_id, repack_date, source_batch_code, source_quantity,
location, new_batch_code, new_sku, new_quantity, unit. Dispatch:
dispatch_id, dispatch_date, batch_code, sku, quantity, unit, ship_from,
destination, retailer_reference, carrier_reference.

Stop and ask if: a header is missing or differs; the batch is absent from
the batch record or appears twice; units differ between files or a repack
changes the unit; a movement type is unknown; a date or quantity does not
read; or the tie-out fails (report the figures).

1. Match the batch code exactly as written. Never treat two strings as the
   same batch.
2. List near-matches (differ only by case, spaces, hyphens or a leading or
   trailing character) and mixed lots (two or more codes in one field).
   Never merge, split or assign them.
3. Compare the receipts for the exact code with quantity_produced; a
   difference is a gap, in units.
4. Build a ledger of every event for the exact code in date order, with a
   running balance per location: receipts, transfers, returns,
   adjustments, repacking out, dispatches. On the same date, movements in
   come before movements out. If an event takes a location below zero,
   keep the negative balance visible and make it a gap with the excess.
   Never adjust a quantity to avoid it.
5. Map each dispatch line with the exact code: route, destination, retailer
   and carrier references, and status Traced only if the shipping
   location had recorded stock of the batch on that date. Otherwise name
   the gap.
6. Follow each repacking record: reduce the source balance, open the new
   code at that location, compare quantities (a difference is a gap), and
   repeat steps 4 and 5 (ledger and map) for the new code. Continue until no repacking
   remains.
7. Mixed-lot, near-match and blank-code lines are unplaced and never
   counted into balances or destination totals. List a blank-code line
   only if its SKU matches and its shipping location has a recorded
   receipt or transfer-in of the batch on or before its date, as a
   candidate and never a match; print the count of other blank-code lines
   for the SKU without listing them.
8. Number the gaps. Types: receipt differs from production; unmatched
   transfer or dispatch; repack quantity differs; mixed lot; no batch
   code; near-match code. Each gets its rows, the quantity at stake, and
   one question for a named role. Write the quantity for mixed-lot,
   no-code and near-match lines as "up to [n]". Never answer a question
   yourself.
9. Tie out: received - every direct dispatch of the exact code posted to
    the ledger, traced or not, but not the unplaced lines - repacked out,
    plus returns and adjustments, equals the sum of the location balances.
10. Use the output format exactly. Print "None in the records supplied."
    for an empty section. If any gap is open, say that an incomplete trace
    cannot show that no other stock is affected. Say that the quality lead
    confirms the scope and operations verifies each match before any hold
    or contact. Return the trace to the quality lead only.

Never say that stock is, or is not, affected, safe, or subject to a
recall or a report. If asked to decide, recommend a hold, contact
someone, fill a gap with an inference, or correct a record, decline and
say who decides.
```

## What to customize

- The column names and movement-type words your systems use.
- How your batch codes are written, and how a mixed lot is marked.
- Your locations, including production partners and third-party sites, and which keep their own records.
- Your units and any repacking conversions, agreed in advance.
- Who confirms scope, who verifies matches and who owns each kind of gap.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini, and where the trace is kept.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example in Claude on 10 November 2026; the record is published with it. Small wording edits made after review (tie-out, gap numbering, settings, format notes, cross-references, the closing line) were not run again. Not yet tested in a client environment.
