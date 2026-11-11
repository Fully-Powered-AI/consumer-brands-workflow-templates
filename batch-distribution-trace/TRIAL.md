# Batch distribution trace: tried once on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in [`example.md`](example.md): the batch record, movement export, repacking record, dispatch lines and settings for batch B2611A. No client data was used. The model that ran the template did not write it. It followed the instruction block and output format in the template on those inputs, and only afterwards compared its result with the published example's output.

## What came out

The trace followed the output format in six sections. These are its substantial parts.

**The batch.** 2,400 bottles produced on 2026-09-14; 2,376 recorded as received, 24 fewer (G1).

**Where it moved.** Ten events in date order. Final recorded balances: Warehouse 1 392, Warehouse 2 210, Warehouse 3 -22, Warehouse 4 380; total 960. The Warehouse 3 balance went negative on 2026-10-06, when transfer M5 moved 380 out of a location that held 358 (G2).

**Batch-to-shipment map.** Four dispatch lines (D1 to D4) were traced: 528 to Retailer A DC North, 336 to Retailer B stores, 192 to Retailer C; total 1,056. Three lines were left unplaced and not counted: D5 (mixed lot, 120), D6 (blank code, a candidate because Warehouse 3 had received the batch, 96) and D7 (near-match "B2611-A", 48). Blank-code lines from locations with no record of the batch: 0.

**Repacking.** R1 turned 360 bottles of B2611A into 354 of X2611-R1 at Warehouse 1 (6 fewer, G3). One dispatch of X2611-R1 (D8, 240, to Export distributor E) was traced. 114 of X2611-R1 remain at Warehouse 1.

**Gaps.** Six: G1 receipt differs from production (24); G2 unmatched transfer (22); G3 repack quantity differs (6); G4 mixed lot (up to 120); G5 no batch code (up to 96); G6 near-match code (up to 48). Each had its rows, a quantity and one question.

**Close.** Tie-out: 2,376 received - 1,056 traced direct dispatches - 360 repacked out = 960; location balances add to 960 (392 + 210 - 22 + 380). Quantity not placed: 264 bottles in 3 lines. Six gaps open, so the trace said it is incomplete and cannot show that no other stock is affected, and that the quality lead confirms the scope and operations verifies each match. It made no statement about whether stock is affected, safe, or subject to a recall or report.

## What was observed

- **Every required part was produced.** All six sections, the ledger, the map, the repacking link, the numbered gaps and the tie-out were produced from the inputs alone. Nothing in the instructions required a stop on this example, and the model did not stop.
- **The result matched the published example on every figure:** all ledger balances, the destination totals, the six gaps and their quantities, the unplaced total of 264, and the tie-out.
- **Differences from the published example were small and in wording:**
  - The example lists the "records used" with a batch record "dated 14 September 2026". The input has no file date; that is the production date. The model wrote the batch record as supplied. (This describes the example at the time of the trial; since corrected, it now reads "as supplied".)
  - The example gives the route for D8 as "Production partner P, Warehouse 1, repacked under R1"; the model wrote the same route and named X2611-R1 as the code shipped.
  - The example addresses all six gap questions to the operations lead. The model did the same, but see the second point under ambiguities.
- **Details in the example that are not in the inputs.** The question for G1 suggests the difference may be "held at Production partner P", the question for G3 suggests bottles were "damaged or discarded", and G2's question suggests "a receipt or transfer into Warehouse 3 is missing". These are framed as questions and the template allows them, but they are guesses about causes that no input states. The model's own gap questions were kept neutral and did not name causes. Every figure in both outputs, including the 358 balance and the Warehouse 3 receipt date cited in the example, can be worked out from the input rows. (This describes the example at the time of the trial; since corrected, its gap questions are neutral.)

### Where the instructions were ambiguous

- **Gap numbering.** The template says to number gaps "in order of the sections above", but the gap types listed in step 10 run in a different order from the sections (mixed lot and near-match are found in step 3, before the ledger). The model numbered by the type list, which gave the same numbers as the example. (This describes the template at the time of the trial; since corrected, it no longer says "in order of the sections above".)
- **Who is asked.** The roles section says questions about a production partner's records go to the person who manages that partner, but the settings only name a quality lead and operations. G1, which concerns the partner's receipt, had no named recipient. The model addressed it to operations to put to the partner's contact.
- **A transfer that is impossible.** The instructions say to keep the negative balance and flag it, but do not say whether the receiving location (Warehouse 4) still gets the full 380. The model credited the full quantity, as a transfer "moves the quantity", and this agrees with the tie-out.
- **"Records used" line.** The format asks for "[file or date]" for the batch record, with no guidance for inputs that are pasted rather than uploaded.
- **Gap quantity for unplaced lines.** The format asks for a quantity at stake. For mixed-lot, blank-code and near-match lines it is an upper bound ("up to"), but the format does not say to write it that way. The model followed the acceptance tests' wording.
- **Dispatch of the new code.** Step 8 says to run the ledger and mapping again for the new code, but the dispatch file is described as holding lines for the original SKU; the example includes the new SKU's lines in it. The model assumed the dispatch file includes them.

### Shortcomings of this trial

- It was one run, by one model, on one invented example, where the answer was already published. It shows that the instructions can be followed to the same figures. It does not show how the template behaves on messy real files, other file formats, other models, or headers that differ from the defaults.
- None of the stop conditions (missing header, unit mismatch, unknown movement type, failed tie-out) were triggered, so none was exercised.
- The acceptance tests in the template are still proposed and were not run.
- No client data was used, and the template has not been tested in a client environment.
