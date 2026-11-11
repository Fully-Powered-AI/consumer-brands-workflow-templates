# Dated stock exposure list: an invented example

*Illustrative example with invented data.* Fernhollow Goods is an invented small brand selling granola, chilli oil and lip balm. Retailer A, Retailer B and Retailer C are invented accounts. No real company, product or person is described.

## What the supply planner supplies

Settings: today is 2026-11-16. Dates are written YYYY-MM-DD. The horizon is 30 days. Roles are named only as Supply lead and Quality owner.

**Stock-by-batch export**

```
SKU       | Product              | Batch  | Location    | Quantity | Unit    | Stated date | Date label  | Storage | Status
FH-GR-01  | Oat granola 400 g    | G-0417 | Warehouse 1 | 1200     | cartons | 2027-01-15  | best before | ambient | available
FH-GR-01  | Oat granola 400 g    | G-0488 | Warehouse 1 | 2400     | cartons | 2027-03-20  | best before | ambient | available
FH-GR-01  | Oat granola 400 g    | G-0488 | Warehouse 2 | 600      | cartons | 2027-03-20  | best before | ambient | available
FH-SP-03  | Chilli oil 250 ml    | C-0877 | Warehouse 1 | 150      | cartons | 2026-11-02  | best before | ambient | available
FH-SP-03  | Chilli oil 250 ml    | C-0921 | Warehouse 1 | 800      | cartons | 2026-12-31  | best before |         | available
FH-LB-02  | Lip balm 4 g tin     | L-310  | Warehouse 1 | 5000     | each    | 2027-02     |             | ambient | available
FH-LB-02  | Lip balm 4 g tin     | L-355  | Warehouse 2 | 3000     | each    |             |             | ambient | on hold
```

**Approved date list (quality owner)**

```
Batch | Approved date | Date label       | Approved by
L-355 | 2027-09-30    | best before end  | Quality owner
```

**Retailer acceptance rules**

```
Account    | SKU      | Minimum days remaining | Transit days
Retailer A | ALL      | 90                     | 3
Retailer A | FH-GR-01 | 120                    | 3
Retailer B | FH-GR-01 | 60                     | 4
Retailer B | FH-LB-02 | 180                    | 2
Retailer C | ALL      | 30% of life remaining  |
```

**Demand plan**

```
SKU      | Account    | Week start | Units
FH-GR-01 | Retailer A | 2026-11-16 | 400
FH-GR-01 | Retailer A | 2026-12-14 | 400
FH-GR-01 | Retailer B | 2026-11-23 | 300
FH-GR-01 | Retailer B | 2027-02-01 | 300
FH-SP-03 | Retailer A | 2026-11-23 | 200
FH-SP-03 | Retailer A | 2027-01-04 | 200
FH-LB-02 | Retailer A | 2026-12-07 | 1000
FH-LB-02 | Retailer B | 2026-11-30 | 1500
FH-LB-02 | Retailer B | 2027-03-01 | 1500
```

## The list

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
FH-LB-02 Lip balm 4 g tin, batch L-310, Warehouse 1: 5,000 each. The export gives "2027-02", which has no day, and the approved date list does not include this batch. No last dispatch date worked out. Answer from: Quality owner (the approved date).

3. Open items
1. FH-SP-03 batch C-0877, Warehouse 1: stated date 2026-11-02 passed 14 days ago. Answer from: Quality owner (suitability and any restriction).
2. FH-SP-03 batch C-0921, Warehouse 1: storage condition not stated in the export. Answer from: Quality owner.
3. FH-LB-02 batch L-355, Warehouse 2: status shown as supplied: on hold. Answer from: Supply lead.

4. No supply decision flagged
FH-LB-02 Lip balm 4 g tin, batch L-355, Warehouse 2: 3,000 each. Stated date 2027-09-30 (best before end), from the approved date list. Earliest last dispatch date 2027-04-01 (Retailer B, 136 days left); Retailer A 2027-06-29 (225 days left).

5. Rules and plan notes
Retailer C: rule is a share of life remaining, not days; not applied to any SKU. Answer from: Supply lead (the day count to use).
Retailer B: no rule supplied for FH-SP-03.
No account appears in the demand plan without a rule row.

Totals by unit: cartons 5,150 (all in "Decision needed"). Each 8,000 (5,000 date not placed, 3,000 no supply decision flagged).

Draft for the Supply lead and the Quality owner. No date has been interpreted, no shelf life or suitability is stated, and nothing has been changed, sent or moved.
```

Every date, quantity and rule above comes from the tables the planner supplied; each day count is the stated date minus the required days, set against 2026-11-16. The list changes no records and sends nothing.
