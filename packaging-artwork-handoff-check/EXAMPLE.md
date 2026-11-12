# Packaging artwork handoff check: an invented example

*Illustrative example with invented data.* The brand, the printer, the product codes, the barcodes, the approval references and the files below are all invented. "Brand A" is a small invented granola brand sending three variants to "Printer A". First come the inputs the packaging owner supplied, in full, then the checklist the workflow template returned.

## The inputs

### 1. Variant matrix

```
sku,product_name,variant,pack_size,pack_format,barcode,approved_copy_id
G-OH-350,Brand A Granola,Oat & Honey,350 g,carton-350,2000000000011,C-OH
G-OH-750,Brand A Granola,Oat & Honey,750 g,pouch-750,2000000000028,C-OH
G-CB-350,Brand A Granola,Cacao & Berry,350 g,carton-350,2000000000035,C-CB
```

### 2. Approved copy

A dash means nothing recorded. The packaging owner marked the regulated lines.

```
copy_id,panel,line,text,approval_ref,regulated,specialist_approval_ref
C-OH,front,1,Oat & Honey Granola,AP-101,no,-
C-OH,front,2,Baked in small batches,AP-101,no,-
C-OH,back,1,"Ingredients: oats, honey, sunflower oil, almonds.",AP-102,yes,SP-31
C-OH,back,2,May contain traces of other nuts.,AP-102,yes,SP-31
C-OH,back,3,Net weight {pack_size},AP-102,yes,SP-31
C-CB,front,1,Cacao & Berry Granola,AP-103,no,-
C-CB,front,2,Crunchy clusters with real berries,-,no,-
C-CB,back,1,"Ingredients: oats, cacao, dried cranberries, sunflower oil, almonds.",AP-104,yes,-
C-CB,back,2,May contain traces of other nuts.,AP-104,yes,-
C-CB,back,3,Net weight {pack_size},AP-104,yes,-
```

### 3. Artwork file list

Lines of text on a panel are separated by " | " in the order they are printed. The packaging owner pasted them from the files.

```
file_name,sku,panel,version,modified,width_mm,height_mm,colour_mode,barcode,text_on_artwork,in_release
OH350_front_v3.pdf,G-OH-350,front,v3,2026-10-20,160,220,CMYK,-,Oat & Honey Granola | Baked in small batches,yes
OH350_back_v2.pdf,G-OH-350,back,v2,2026-10-22,160,220,CMYK,2000000000011,"Ingredients: oats, honey, sunflower oil, almonds. | May contain traces of other nuts. | Net weight 350 g",yes
OH350_side_v1.pdf,G-OH-350,side,v1,2026-10-18,60,220,CMYK,-,-,yes
OH750_front_v2.pdf,G-OH-750,front,v2,2026-10-21,200,300,CMYK,-,Oat & Honey Granola | Baked in small batches,yes
OH750_back_v1.pdf,G-OH-750,back,v1,2026-10-15,200,300,CMYK,2000000000011,"Ingredients: oats, honey, sunflower oil, almonds. | May contain traces of other nuts. | Net weight 350 g",yes
OH750_back_v2.pdf,G-OH-750,back,v2,2026-10-24,200,300,CMYK,2000000000028,"Ingredients: oats, honey, sunflower oil, almonds. | May contain traces of other nuts. | Net weight 750 g",no
CB350_front_v1.pdf,G-CB-350,front,v1,2026-10-23,160,220,CMYK,-,Cacao & Berry Granola | Crunchy clusters with real berries,yes
CB350_back_v1.pdf,G-CB-350,back,v1,2026-10-23,160,215,RGB,2000000000035,"Ingredients: oats, cacao, dried cranberries, sunflower oil, almonds. | May contain traces of other nuts. | Net weight 350 g | Gluten free",yes
```

### 4. Printer specification

```
pack_format,panel,width_mm,height_mm,colour_mode,barcode_required
carton-350,front,160,220,CMYK,no
carton-350,back,160,220,CMYK,yes
carton-350,side,60,220,CMYK,no
pouch-750,front,200,300,CMYK,no
pouch-750,back,200,300,CMYK,yes
```

### 5. Review log

```
record_ref,file_name,version,reviewer_role,decision,date
RV-01,OH350_front_v3.pdf,v3,Brand manager,approved,2026-10-21
RV-02,OH350_back_v2.pdf,v2,Quality reviewer,approved,2026-10-23
RV-03,OH750_front_v2.pdf,v2,Brand manager,approved,2026-10-22
RV-04,OH750_back_v1.pdf,v1,Quality reviewer,approved,2026-10-16
RV-05,OH750_back_v2.pdf,v2,Quality reviewer,pending,2026-10-24
RV-06,CB350_front_v1.pdf,v1,Brand manager,changes requested,2026-10-24
RV-07,OH350_side_v1.pdf,v1,Brand manager,approved,2026-10-19
```

### 6. Settings

```
Printer: Printer A
Release owner: Packaging owner
Designated specialist for regulated wording: Regulatory specialist
Size tolerance: 0 mm
Today: 3 November 2026
```

## The output

**PACKAGING ARTWORK HANDOFF CHECK: Brand A Granola, release to Printer A**

Prepared 3 November 2026 from 3 variants, 8 required slots, 8 artwork files, 10 approved-copy lines, 7 review records.

Status: NOT READY. 10 findings on 4 slots.

**Slots:**

- G-OH-350, 350 g, front: OH350_front_v3.pdf (v3) - CLEAR
- G-OH-350, 350 g, back: OH350_back_v2.pdf (v2) - CLEAR
- G-OH-350, 350 g, side: OH350_side_v1.pdf (v1) - CLEAR
- G-OH-750, 750 g, front: OH750_front_v2.pdf (v2) - CLEAR
- G-OH-750, 750 g, back: OH750_back_v1.pdf (v1) - BLOCKED (F1, F2, F3)
- G-CB-350, 350 g, front: CB350_front_v1.pdf (v1) - BLOCKED (F4, F5)
- G-CB-350, 350 g, back: CB350_back_v1.pdf (v1) - BLOCKED (F6, F7, F8, F9)
- G-CB-350, 350 g, side: NO RELEASE FILE (F10)

**Findings:**

- F1 Files: G-OH-750, back. Expected: no other file for the slot with a higher version than the release file. Found: OH750_back_v1.pdf (v1, 15 October) is in the release; OH750_back_v2.pdf (v2, 24 October) is on the list and is not. Resolves: Packaging owner.
- F2 Specification: OH750_back_v1.pdf. Expected: barcode 2000000000028 (variant matrix, G-OH-750). Found: 2000000000011, which the variant matrix gives to G-OH-350. Resolves: Designer.
- F3 Text: OH750_back_v1.pdf. Expected: "Net weight 750 g" (approved copy C-OH back line 3, with the pack size from the variant matrix). Found: "Net weight 350 g", which differs from the approved line. Resolves: Designer.
- F4 Copy approval: CB350_front_v1.pdf. Expected: an approval reference for C-CB front line 2, "Crunchy clusters with real berries". Found: none recorded. The file's text matches the line. Resolves: Packaging owner.
- F5 Review record: CB350_front_v1.pdf. Expected: a record with decision "approved" for this file and version. Found: RV-06, Brand manager, "changes requested", 24 October. Resolves: Packaging owner.
- F6 Specification: CB350_back_v1.pdf. Expected: 160 x 220 mm, CMYK (printer specification, carton-350 back). Found: 160 x 215 mm, RGB. Resolves: Designer.
- F7 Text: CB350_back_v1.pdf. Expected: the three lines of C-CB back. Found: the three lines match; a fourth line, "Gluten free", is not in approved copy. Resolves: Packaging owner, with the Regulatory specialist.
- F8 Regulated wording: CB350_back_v1.pdf. Expected: a specialist approval reference on each regulated line of C-CB back. Found: lines 1, 2 and 3 are marked regulated and none has one. Resolves: Regulatory specialist.
- F9 Review record: CB350_back_v1.pdf. Expected: a record with decision "approved" for this file and version. Found: no record. Resolves: Packaging owner.
- F10 Files: G-CB-350, side. Expected: one release file for carton-350 side (60 x 220 mm). Found: no file on the list. Resolves: Packaging owner.

**Version conflicts:** G-OH-750, back: OH750_back_v1.pdf (v1, 15 October, in the release) and OH750_back_v2.pdf (v2, 24 October, not in the release; its review, RV-05, is pending).

**Missing approvals:**

- Copy lines with no approval reference: C-CB front line 2 (F4).
- Regulated wording with no specialist approval: C-CB back lines 1 to 3 (F8).
- Release files with no approving review record: CB350_front_v1.pdf, "changes requested" (F5); CB350_back_v1.pdf, no record (F9).

**Decisions for the packaging owner: 4**

1. G-OH-750, back: which file goes to Printer A, v1 or v2? v1 carries the 350 g barcode and weight statement (F2, F3). v2 is not in the release and its review is pending.
2. G-CB-350, front: who approves "Crunchy clusters with real berries", and what changes did the Brand manager request in RV-06?
3. G-CB-350, back: does "Gluten free" stay on the panel? It is not in approved copy (F7). Who asks the Regulatory specialist about it?
4. G-CB-350, side: is there a side panel file for this release, or is the slot not needed? The printer specification lists one for carton-350.

**Not checked:** Print quality, colour accuracy, legibility and whether any wording is correct or permitted. Only the text, sizes, versions and records supplied were compared.

Draft for the packaging owner. Nothing has been approved, released or sent to the printer.
