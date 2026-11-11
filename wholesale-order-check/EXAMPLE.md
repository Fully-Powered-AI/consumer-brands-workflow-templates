# Wholesale order check: an invented example

*Illustrative example with invented data.* The brand, the retailer, the products, the prices, the stock and every date below are invented. The brand, called the Brand here, makes granola and snack bars. Retailer A is a fictional retail chain. The Brand's account owner runs the check and, with operations, decides. People are referred to by role.

The inputs come first, in full, so the template can be run on them. The check follows.

## The inputs

### 1. Settings (typed by the account owner)

```
Today: Tuesday 10 November 2026
Currency: US dollars
Account: Retailer A
Runs the check: the account owner
Decides: the account owner, with operations
Purchase order: RA-77410, dated 2026-11-09
Quote: Q-2026-118, dated 2026-10-20, valid until 2026-11-20
```

### 2. The purchase order lines

```
po_line,sku,description,cases,units_per_case,price_per_unit,ship_to,delivery_date
1,GR-350,Maple granola 350 g,40,12,4.10,Retailer A DC North,2026-12-01
2,GR-350,Maple granola 350 g,20,12,4.10,Retailer A DC South,2026-12-01
3,GR-700,Maple granola 700 g,25,6,7.40,Retailer A DC North,2026-12-01
4,BR-250,Seed bar box 250 g,30,8,5.50,Retailer A DC North,2026-11-24
5,GR-350V,Vanilla granola 350 g,15,12,4.25,Retailer A DC South,2026-12-01
6,GR-350,Maple granola 350 g,10,12,4.10,Retailer A Store 14,2026-12-01
```

Terms and notes the buyer added to the order:

```
Payment terms requested: Net 60
Other terms requested: Free delivery to all locations. Unsold stock may be returned within 90 days.
Buyer note: If GR-700 cannot ship by 1 December, send GR-350V instead at the same price.
```

### 3. The approved quote

```
sku,description,units_per_case,price_per_unit
GR-350,Maple granola 350 g,12,4.10
GR-700,Maple granola 700 g,6,7.60
BR-250,Seed bar box 250 g,6,5.50
```

### 4. The stock plan (from operations)

```
sku,available_units,earliest_delivery_date
GR-350,840,2026-11-30
GR-700,150,2026-12-03
BR-250,200,2026-11-20
```

### 5. Account terms

```
delivery_locations: Retailer A DC North; Retailer A DC South
payment_terms: Net 30
minimum_order_value: 2500.00
```

## The check

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
