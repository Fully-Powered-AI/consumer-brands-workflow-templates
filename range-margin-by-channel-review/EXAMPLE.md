# Range margin by channel review: an invented example

*Illustrative example with invented data.* The business, the products and every figure below are invented. Marrowby Pantry is an invented six-person maker of granola and oat bars that sells through its own website, to wholesale accounts and on a marketplace. A wholesale account has asked for better terms, and the finance lead wants to see what each product earns in each channel first. The bookkeeper runs the review; people are referred to by role.

The inputs come first, in full, so the template can be run on them. The worksheet follows.

## The inputs

### 1. Settings

```
Business: Marrowby Pantry
Review date: Tuesday 10 November 2026
Period: 1 July 2026 to 30 September 2026
For: the finance lead
Prepared by: the bookkeeper
Currency: US dollars
Margin floor: 20%
```

### 2. Sales export, 1 July to 30 September 2026

```
SKU,Channel,Units,Gross sales,Discounts,Returns
G-400,Website,1200,9600.00,480.00,96.00
G-400,Wholesale,3000,16500.00,1650.00,0.00
G-400,Marketplace,800,6400.00,320.00,128.00
G-TIN,Website,300,6900.00,300.00,110.00
G-TIN,Wholesale,500,8000.00,1200.00,0.00
B-12,Website,400,4800.00,200.00,60.00
B-12,Marketplace,600,6600.00,0.00,150.00
B-12W,Wholesale,250,2125.00,125.00,0.00
```

### 3. Unit cost file

```
SKU,Cost layer,Unit cost,Status
G-400,Product,3.10,Confirmed
G-400,Packaging,0.55,Confirmed
G-TIN,Product,6.80,Confirmed
G-TIN,Packaging,2.40,Estimated
B-12,Product,4.20,Confirmed
```

### 4. Channel cost file

```
Channel,Cost layer,Basis,Rate,Status
Website,Freight,per unit,1.20,Estimated
Website,Channel fees,% of net sales,3.5,Confirmed
Wholesale,Freight,per unit,0.40,Confirmed
Wholesale,Channel fees,% of net sales,2.0,Estimated
Marketplace,Freight,per unit,1.10,Confirmed
Marketplace,Channel fees,% of net sales,15,Confirmed
```

## The worksheet

```
RANGE MARGIN BY CHANNEL REVIEW: Marrowby Pantry, prepared 10 November 2026

For: the finance lead. Prepared by the bookkeeper on 10 November 2026, for the finance lead's review.
Sources: sales export, 1 July 2026 to 30 September 2026, 8 lines; unit cost file, 5 rows; channel cost file, 6 rows.
Settings used: currency US dollars; margin floor 20%. Defaults used: none.

THE PICTURE
Lines: 8, of 4 products in 3 channels. Complete: 5. Incomplete: 2. No margin shown: 1. Below zero: 0. Below floor: 1.
Tie-out: net sales across lines $56,106.00 = gross sales $60,925.00 − discounts $4,275.00 − returns $544.00. Units 7,050 = 7,050.

THE GRID
Margin % with estimates.
G-400: Website 32.0%; Wholesale 16.2%; Marketplace 21.2%.
G-TIN: Website 48.4%; Wholesale 27.4%; Marketplace no sales.
B-12: Website 48.9% incomplete; Wholesale no sales; Marketplace 35.7% incomplete.
B-12W: Website no sales; Wholesale n/a; Marketplace no sales.

MARGIN BY PRODUCT AND CHANNEL
G-400, Website: 1,200 units. Gross sales $9,600.00, discounts $480.00, returns $96.00, net sales $9,024.00.
  Costs: Product $3,720.00, Confirmed; Packaging $660.00, Confirmed; Freight $1,440.00, Estimated; Channel fees $315.84, Confirmed.
  Margin on confirmed costs: $4,328.16, 48.0%. With estimates: $2,888.16, 32.0%.
G-400, Wholesale: 3,000 units. Gross sales $16,500.00, discounts $1,650.00, returns $0.00, net sales $14,850.00.
  Costs: Product $9,300.00, Confirmed; Packaging $1,650.00, Confirmed; Freight $1,200.00, Confirmed; Channel fees $297.00, Estimated.
  Margin on confirmed costs: $2,700.00, 18.2%. With estimates: $2,403.00, 16.2%. BELOW FLOOR.
G-400, Marketplace: 800 units. Gross sales $6,400.00, discounts $320.00, returns $128.00, net sales $5,952.00.
  Costs: Product $2,480.00, Confirmed; Packaging $440.00, Confirmed; Freight $880.00, Confirmed; Channel fees $892.80, Confirmed.
  Margin on confirmed costs: $1,259.20, 21.2%. With estimates: $1,259.20, 21.2%.
G-TIN, Website: 300 units. Gross sales $6,900.00, discounts $300.00, returns $110.00, net sales $6,490.00.
  Costs: Product $2,040.00, Confirmed; Packaging $720.00, Estimated; Freight $360.00, Estimated; Channel fees $227.15, Confirmed.
  Margin on confirmed costs: $4,222.85, 65.1%. With estimates: $3,142.85, 48.4%.
G-TIN, Wholesale: 500 units. Gross sales $8,000.00, discounts $1,200.00, returns $0.00, net sales $6,800.00.
  Costs: Product $3,400.00, Confirmed; Packaging $1,200.00, Estimated; Freight $200.00, Confirmed; Channel fees $136.00, Estimated.
  Margin on confirmed costs: $3,200.00, 47.1%. With estimates: $1,864.00, 27.4%.
B-12, Website: 400 units. Gross sales $4,800.00, discounts $200.00, returns $60.00, net sales $4,540.00.
  Costs: Product $1,680.00, Confirmed; Packaging not supplied; Freight $480.00, Estimated; Channel fees $158.90, Confirmed.
  Margin on confirmed costs: $2,701.10, 59.5%. With estimates: $2,221.10, 48.9%. INCOMPLETE: no packaging; both margins are before it.
B-12, Marketplace: 600 units. Gross sales $6,600.00, discounts $0.00, returns $150.00, net sales $6,450.00.
  Costs: Product $2,520.00, Confirmed; Packaging not supplied; Freight $660.00, Confirmed; Channel fees $967.50, Confirmed.
  Margin on confirmed costs: $2,302.50, 35.7%. With estimates: $2,302.50, 35.7%. INCOMPLETE: no packaging; both margins are before it.
B-12W, Wholesale: 250 units. Net sales $2,000.00. No margin shown: no product cost. Found: Freight $100.00, Confirmed; Channel fees $40.00, Estimated.

THE GAPS
Missing: Packaging, B-12: touches B-12 Website, B-12 Marketplace.
Estimated: Packaging, G-TIN: $2.40 a unit; carried by G-TIN Website, G-TIN Wholesale.
Estimated: Freight, Website: $1.20 a unit; carried by G-400 Website, G-TIN Website, B-12 Website.
Estimated: Channel fees, Wholesale: 2.0% of net sales; carried by G-400 Wholesale, G-TIN Wholesale, B-12W Wholesale.
Unmatched: B-12W in Wholesale, 250 units, net sales $2,000.00: no rows in the unit cost file.

DATA NOTES
B-12W, Wholesale: no margin shown because the unit cost file has no rows for B-12W.
Products in the unit cost file with no sales in the period: none. Channels with no rows in the channel cost file: none.
Assumption: units are net of returns; returned goods and return freight are not costed.
Assumption: costs and rates cover the whole period, and allocations are used as supplied.

QUESTIONS FOR THE FINANCE LEAD
1. Packaging, B-12: there is no packaging row, so both margins on B-12 Website and B-12 Marketplace are before it. What is the packaging cost of one unit, and is it confirmed?
2. B-12W, Wholesale: 250 units, net sales $2,000.00, and no rows in the unit cost file. Is B-12W a variant of another product, and what are its product and packaging costs?
3. Packaging, G-TIN: $2.40 a unit is marked Estimated and sits on two lines. Is there a confirmed figure?
4. Freight, Website: $1.20 a unit is marked Estimated and sits on three lines. Is there a confirmed rate?
5. Channel fees, Wholesale: 2.0% of net sales is marked Estimated and sits on three lines. Is that rate confirmed?

Prepared for the finance lead's review. It recommends no price and no channel decision. No price, cost or record has been changed, and nothing has been sent or published.
```
