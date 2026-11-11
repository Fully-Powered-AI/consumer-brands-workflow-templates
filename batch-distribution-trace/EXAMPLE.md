# Batch distribution trace: an invented example

*Illustrative example with invented data.* Brand X, the retailers, the warehouses, the production partner and every code, reference and quantity below are invented. The quality lead has asked for a trace of batch B2611A, a chilli oil, after a production partner's note raised a question about it. The unit throughout is bottles.

## What the person supplies

**Batch record**

```
batch_code,sku,product_name,production_date,quantity_produced,unit
B2611A,CO-250,Chilli oil 250 ml,2026-09-14,2400,bottle
```

**Movement export** (every row for B2611A)

```
movement_id,movement_date,batch_code,sku,from_location,to_location,quantity,unit,movement_type,document_ref
M1,2026-09-15,B2611A,CO-250,Production partner P,Warehouse 1,2376,bottle,receipt,GRN-5521
M2,2026-09-22,B2611A,CO-250,Warehouse 1,Warehouse 2,600,bottle,transfer,TO-318
M3,2026-09-23,B2611A,CO-250,Warehouse 1,Warehouse 3,400,bottle,transfer,TO-321
M4,2026-10-05,B2611A,CO-250,Warehouse 2,Warehouse 3,150,bottle,transfer,TO-344
M5,2026-10-06,B2611A,CO-250,Warehouse 3,Warehouse 4,380,bottle,transfer,TO-349
```

**Repacking records**

```
repack_id,repack_date,source_batch_code,source_quantity,location,new_batch_code,new_sku,new_quantity,unit
R1,2026-10-01,B2611A,360,Warehouse 1,X2611-R1,CO-250-EX,354,bottle
```

**Dispatch lines** (all lines for SKU CO-250 and CO-250-EX from 15 September to 12 October)

```
dispatch_id,dispatch_date,batch_code,sku,quantity,unit,ship_from,destination,retailer_reference,carrier_reference
D1,2026-09-18,B2611A,CO-250,288,bottle,Warehouse 1,Retailer A DC North,RA-PO-7741,CAR-1101
D2,2026-09-19,B2611A,CO-250,336,bottle,Warehouse 1,Retailer B stores,RB-4402,CAR-1105
D3,2026-09-30,B2611A,CO-250,240,bottle,Warehouse 2,Retailer A DC North,RA-PO-7790,CAR-1120
D4,2026-10-03,B2611A,CO-250,192,bottle,Warehouse 3,Retailer C,RC-1187,CAR-1131
D5,2026-10-08,B2611A/B2611B,CO-250,120,bottle,Warehouse 2,Retailer D,RD-0095,CAR-1140
D6,2026-10-09,,CO-250,96,bottle,Warehouse 3,Retailer B stores,RB-4460,CAR-1144
D7,2026-10-10,B2611-A,CO-250,48,bottle,Warehouse 2,Own-site orders (consolidated),,CAR-1150
D8,2026-10-12,X2611-R1,CO-250-EX,240,bottle,Warehouse 1,Export distributor E,ED-3310,CAR-1160
```

**Settings:** batch to trace B2611A; unit bottle; quality lead named "the quality lead"; operations named "the operations lead"; trace prepared 10 November 2026.

## What comes out

**BATCH DISTRIBUTION TRACE: B2611A, Chilli oil 250 ml (CO-250)**

For: the quality lead, to confirm scope with the operations lead. Records used: batch record pasted; movements to 6 October 2026; repacking records pasted; dispatch lines 18 September to 12 October 2026. Prepared 10 November 2026.

**1. The batch**

Produced: 2,400 bottles on 2026-09-14. Recorded as received: 2,376, which is 24 fewer than produced (G1).

**2. Where it moved**

- 2026-09-15 M1: received from Production partner P into Warehouse 1, 2,376 (GRN-5521). Warehouse 1 now 2,376.
- 2026-09-18 D1: dispatched from Warehouse 1, 288. Warehouse 1 now 2,088.
- 2026-09-19 D2: dispatched from Warehouse 1, 336. Warehouse 1 now 1,752.
- 2026-09-22 M2: Warehouse 1 to Warehouse 2, 600 (TO-318). Warehouse 1 now 1,152; Warehouse 2 now 600.
- 2026-09-23 M3: Warehouse 1 to Warehouse 3, 400 (TO-321). Warehouse 1 now 752; Warehouse 3 now 400.
- 2026-09-30 D3: dispatched from Warehouse 2, 240. Warehouse 2 now 360.
- 2026-10-01 R1: repacked out at Warehouse 1, 360. Warehouse 1 now 392.
- 2026-10-03 D4: dispatched from Warehouse 3, 192. Warehouse 3 now 208.
- 2026-10-05 M4: Warehouse 2 to Warehouse 3, 150 (TO-344). Warehouse 2 now 210; Warehouse 3 now 358.
- 2026-10-06 M5: Warehouse 3 to Warehouse 4, 380 (TO-349). Warehouse 3 now -22 (G2); Warehouse 4 now 380.

Recorded balance by location: Warehouse 1 392; Warehouse 2 210; Warehouse 3 -22; Warehouse 4 380. Total 960.

**3. Batch-to-shipment map**

- D1, 2026-09-18: 288 from Warehouse 1 to Retailer A DC North; retailer reference RA-PO-7741; carrier CAR-1101. Route: Production partner P, Warehouse 1. Status: Traced.
- D2, 2026-09-19: 336 from Warehouse 1 to Retailer B stores; retailer reference RB-4402; carrier CAR-1105. Route: Production partner P, Warehouse 1. Status: Traced.
- D3, 2026-09-30: 240 from Warehouse 2 to Retailer A DC North; retailer reference RA-PO-7790; carrier CAR-1120. Route: Production partner P, Warehouse 1, Warehouse 2. Status: Traced.
- D4, 2026-10-03: 192 from Warehouse 3 to Retailer C; retailer reference RC-1187; carrier CAR-1131. Route: Production partner P, Warehouse 1, Warehouse 3. Status: Traced.

Recorded to each destination (traced, direct): Retailer A DC North 528; Retailer B stores 336; Retailer C 192. Total 1,056.

Unplaced lines (not counted):
- D5, 2026-10-08: 120 from Warehouse 2 to Retailer D; the code reads "B2611A/B2611B", so the quantity is not split (G4).
- D6, 2026-10-09: 96 from Warehouse 3 to Retailer B stores; no batch code, SKU matches, and Warehouse 3 recorded the batch on 2026-09-23 (G5).
- D7, 2026-10-10: 48 from Warehouse 2 to Own-site orders (consolidated); the code reads "B2611-A" (G6).

Blank-code lines for this SKU from locations with no record of the batch, not listed: 0.

**4. Repacking links**

R1, 2026-10-01: 360 of B2611A into X2611-R1 (CO-250-EX) at Warehouse 1; 354 recorded as made, 6 fewer (G3). Shipments of X2611-R1: D8, 2026-10-12: 240 from Warehouse 1 to Export distributor E; retailer reference ED-3310; carrier CAR-1160. Route: Production partner P, Warehouse 1, repacked under R1. Status: Traced. Balance of X2611-R1: Warehouse 1 114.

**5. Gaps in the trace**

- G1. Receipt differs from production: batch record, M1. Quantity at stake: 24 bottles. Question for the operations lead: what does the goods-in record for GRN-5521 show, and what quantity does Production partner P's record show as sent?
- G2. Unmatched transfer: M5. Quantity at stake: 22 bottles (Warehouse 3 recorded 358 on 2026-10-06 and TO-349 moved 380). Question for the operations lead: what do the Warehouse 3 receipt and transfer records show for the 22 bottles on TO-349 beyond the 358 recorded there?
- G3. Repack quantity differs: R1. Quantity at stake: 6 bottles. Question for the operations lead: what does the repacking record show for the 6 bottles between the 360 used and the 354 made?
- G4. Mixed lot: D5. Quantity at stake: up to 120 bottles. Question for the operations lead: how many of the 120 bottles came from B2611A and how many from B2611B, according to the pick record?
- G5. No batch code: D6. Quantity at stake: up to 96 bottles. Question for the operations lead: which batch did the pick record assign to these 96 bottles at Warehouse 3?
- G6. Near-match code: D7. Quantity at stake: up to 48 bottles. Question for the operations lead: is "B2611-A" on D7 a mistyped B2611A or a different batch?

**6. For the quality lead and operations**

Tie-out: 2,376 received - 1,056 direct dispatches posted to the ledger - 360 repacked out = 960; location balances add to 960 (392 + 210 - 22 + 380).

What the records show: 1,056 bottles to 3 destinations through traced dispatch lines; 240 bottles to Export distributor E through X2611-R1; still recorded on hand: Warehouse 1 392, Warehouse 2 210, Warehouse 4 380, with Warehouse 3 recorded at -22 (G2), and X2611-R1 114 at Warehouse 1.

Quantity not placed: 264 bottles in 3 lines (G4, G5, G6).

Operations to verify: D1 to D4 and D8 against the carrier and retailer documents; the answers to the six questions in section 5.

Open gaps: 6. This trace is incomplete, so it cannot show that no other stock is affected. The quality lead confirms the affected scope, and operations verifies each match, before any hold or contact. This trace decides no recall or regulatory question, contacts nobody and changes no record.
