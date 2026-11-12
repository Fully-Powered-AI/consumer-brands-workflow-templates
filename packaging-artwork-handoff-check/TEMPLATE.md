# Packaging artwork handoff check

Workflow template, version 0.1.0.

## Purpose

Prepare, for one packaging revision about to go to a printer, a checklist that matches each artwork file proposed for release to the records supplied: the variant matrix, the approved copy, the printer specification and the review log. It lists every required file slot as clear, blocked or missing; every version conflict; every missing approval; and every size, colour, barcode or text mismatch, each with the expected value, the value found and the role who resolves it. The assistant prepares and compares. It writes no label claim and judges none, writes no legal wording, never marks a line as regulated or not, never chooses between versions, and never approves, releases or sends a file.

## When to use it and when not to

Use it when a packaging revision is about to go to print, after the files are exported and the review records are in. Run it again whenever a file on the release list is replaced.

Do not use it:

- to edit or improve wording. Use Copy-edit with a change list;
- to plan the weeks around a launch. Use Launch checklist;
- to check the facts on a product page. Use Product-page facts gap review;
- to decide whether a claim or a piece of regulated wording is correct or permitted. That belongs to the designated specialist;
- to judge print quality, colour accuracy or legibility. The assistant reads records and typed text, not artwork.

## Roles

- **Runs it:** the packaging owner, the brand manager or the production coordinator.
- **Confirms the release file:** the packaging owner. Always a person.
- **Approves regulated wording:** the designated specialist named in the settings. Always a person.
- **Fixes file, size, colour, barcode and text findings:** the designer or whoever produced the files.
- **Records approvals:** the roles named in the review log.
- **Receives the approved release:** the printer, sent by a person.

## Inputs

All five records are supplied by the person as files or pasted tables. A blank cell and a single dash both mean nothing recorded. The default headers are below; if a header does not match, stop and ask which of the supplied columns stands for it. Never guess a mapping.

1. **Variant matrix.** Headers `sku,product_name,variant,pack_size,pack_format,barcode,approved_copy_id`. One row per variant and pack size. If missing, stop. If two rows share a `sku`, stop and ask.
2. **Approved copy.** Headers `copy_id,panel,line,text,approval_ref,regulated,specialist_approval_ref`. One row per line of wording. The text may contain `{pack_size}`, which stands for the pack size in the variant matrix. The `regulated` column is filled by the person who owns the wording; the assistant never fills it. If missing, stop.
3. **Artwork file list.** Headers `file_name,sku,panel,version,modified,width_mm,height_mm,colour_mode,barcode,text_on_artwork,in_release`. The text on the panel is typed or pasted by the person, one printed line after another separated by " | ", in the printed order. `in_release` is yes or no. If missing, stop. If a panel has approved copy and its `text_on_artwork` is blank, the file is not compared on text; write "text not supplied" as a Text finding for it.
4. **Printer specification.** Headers `pack_format,panel,width_mm,height_mm,colour_mode,barcode_required`. If missing, stop.
5. **Review log.** Headers `record_ref,file_name,version,reviewer_role,decision,date`. If missing, stop.
6. **Settings.** The printer's name, the role that confirms the release, the designated specialist role, the size tolerance in millimetres, today's date. If the tolerance is missing, use [your size tolerance], and if that is not set either, use 0 mm and say so.

The assistant works from files and text the person supplies. It needs no access to design, print or product systems and never asks for a password or a login code.

## The procedure

1. **Check the inputs.** Confirm the headers of each record, count the rows, and stop on any mismatch or duplicate named above. Write the counts for the header line.
2. **Build the slots.** For each variant, take every row of the printer specification whose `pack_format` equals the variant's. Each is one required slot, identified by sku and panel. Slots are listed by variant in matrix order, then panels in the order the specification lists them. If a variant's pack format has no rows in the specification, write one Files finding for the variant, "no printer specification for this pack format", and give it no slots. That finding is numbered at the variant's place in the matrix order, is counted in the findings but in no slot, and is listed in the status line as a finding on a variant with no slots.
3. **Match files to slots.** A file belongs to the slot with the same sku and panel. Files with `in_release` yes are release files. A release file that matches no slot gets a Files finding, "matches no required slot". A slot with no release file gets a Files finding, "no release file", and the slot is marked NO RELEASE FILE.
4. **Version conflicts (rule Files).** For each slot, list every file on the list for it. It is a conflict if more than one is marked for release; or if the release file has a lower version number than another file for the slot ("older" always means a lower version number; the modified date is used only for the third test); or if the version order and the modified-date order disagree, so that the newest cannot be told. Each conflict is also one Files finding for the slot. Report the files, versions, dates and which one is in the release. Do not choose between them and do not assess the one that is not in the release, except to state its review record.
5. **Specification (rule Specification).** For each release file compare against the printer specification row for the slot: width and height within the tolerance, colour mode exactly as written, and barcode. If the specification requires a barcode, the file's barcode must equal the variant matrix barcode character for character; blank is a finding. If the specification does not require one and the file lists one, report it. The assistant does not compute check digits. All mismatches in one file (for example both size and colour mode) are written as one Specification finding that lists each of them.
6. **Text (rule Text).** Take the approved-copy rows for the variant's `approved_copy_id` and the slot's panel, replacing `{pack_size}` with the variant's pack size. Trim each line and collapse repeated spaces; compare everything else exactly, including capitals and punctuation. Match each artwork line to an approved line with identical text, wherever it sits. Then pair any artwork line and approved line that are both unmatched and share the same position number (the artwork's nth line with approved line n): report the pair as "differs", quoting both. Any other unmatched artwork line is "not in approved copy". Any other unmatched approved line is "approved line missing from the artwork". Make no comment on whether any wording is right, true or allowed. If the panel has no approved copy and the artwork has no text, write nothing; if the artwork has text, every line is "not in approved copy".
7. **Copy approval (rule Copy approval).** Every approved-copy line used in step 6 for a release file needs an `approval_ref`. A blank is a finding naming the line and its text.
8. **Regulated wording (rule Regulated wording).** Every line the person marked `regulated` yes needs a `specialist_approval_ref`. A blank is a finding naming the lines. The assistant does not decide which lines are regulated. Where artwork text is "not in approved copy", it does not say whether it is regulated; it names the designated specialist as someone to ask.
9. **Review record (rule Review record).** Each release file needs a review log row with the same `file_name` and `version` and decision "approved". Missing, pending or any other decision is a finding that states which. Record references are quoted as given.
10. **Write the findings.** One finding per file per rule, numbered F1 onward in slot order and, within a slot, in the order of the rules above. Each states the rule, the file or slot, what was expected and where it came from, what was found, and the role who resolves it. Defaults for who resolves: Files and Review record, the packaging owner; Specification and Text, the designer, except that text not in approved copy goes to the packaging owner with the designated specialist; Copy approval, the packaging owner; Regulated wording, the designated specialist.
11. **Mark each slot.** CLEAR when the file has no finding; BLOCKED with its finding numbers; NO RELEASE FILE with its finding number. Only a slot with no findings is CLEAR.
12. **Collect the three lists.** Version conflicts from step 4; missing approvals under the three headings from steps 7, 8 and 9; and a short numbered list of decisions for the packaging owner, one for each open question the findings raise, written as a question with the facts. Recommend nothing unless the packaging owner asks.
13. **Set the status.** NOT READY if there is any finding. If there are none, write "No findings. For the packaging owner to confirm the release file." Never write approved, ready to print or compliant.
14. **Date.** "Prepared [date]" uses today's date from the settings. If the settings have none, ask for it.
15. **Return the draft** to the person who ran it, for the packaging owner. The packaging owner settles the findings, replaces files, and confirms the release file. A person sends anything to the printer.

## Exceptions and stop conditions

- **A header does not match, a record (including the review log) is missing, or a `sku` is repeated:** stop and ask; compare nothing.
- **An artwork file's sku or panel is blank:** list it under the Files rule with "cannot be placed in a slot".
- **A file's size is not a number, or no number can be read from its version (a leading v, as in v2, is ignored):** write a Specification or Files finding saying the value could not be read; do not guess.
- **The text on the artwork was not supplied for a panel with approved copy:** Text finding "text not supplied"; the file stays BLOCKED.
- **Asked to say the artwork is approved, ready, correct or compliant, to choose a version, to fill the regulated column, to write or reword a claim or any legal wording, or to send files to the printer:** decline. The packaging owner confirms the release file and the designated specialist approves regulated wording.
- **Asked to ignore a finding so the status reads clear:** decline; findings are removed only when the records change.

## Output format

```
PACKAGING ARTWORK HANDOFF CHECK: [range or product], release to [printer]

Prepared [date] from [n] variants, [n] required slots, [n] artwork files, [n] approved-copy lines, [n] review records.

Status: NOT READY. [n] findings on [n] slots[, and [n] on variants with no slots].
(or: Status: No findings. For the [release owner] to confirm the release file.)

Slots:
- [sku], [pack size], [panel]: [file name] ([version]) - CLEAR
- [sku], [pack size], [panel]: [file name] ([version]) - BLOCKED (F[n], F[n])
- [sku], [pack size], [panel]: NO RELEASE FILE (F[n])

Findings:
- F[n] [Rule]: [file or slot]. Expected: [value, and the record it comes from]. Found: [value]. Resolves: [role].
(or: None.)

Version conflicts: [slot: files, versions and dates, and which is in the release]
(or: None found.)

Missing approvals:
- Copy lines with no approval reference: [copy_id, panel, line numbers, with finding numbers] (or: None found.)
- Regulated wording with no specialist approval: [copy_id, panel, line numbers, with finding numbers] (or: None found.)
- Release files with no approving review record: [file names, with the record found or "no record"] (or: None found.)

Decisions for the [release owner]: [n]
1. [Question, with the facts.]
(or: None.)

Not checked: Print quality, colour accuracy, legibility and whether any wording is correct or permitted. Only the text, sizes, versions and records supplied were compared.

Draft for the [release owner]. Nothing has been approved, released or sent to the printer.
```

## Reviewer checklist

1. Every variant and every panel the printer specification lists for its pack format has a slot, and the slot count in the header is right. (Packaging owner)
2. Each finding's expected value is the one in the record named, and its found value is the one in the file list. (Designer)
3. Every version conflict is listed, and the file in the release is the one the packaging owner intends. (Packaging owner)
4. No wording is described as right, wrong, true, allowed or compliant anywhere in the output. (Packaging owner)
5. Every regulated line without a specialist reference is listed, and no line was marked regulated or unregulated by the assistant. (Designated specialist)
6. Every review record quoted matches the file name and version, and the decision is quoted as given. (Quality reviewer)
7. The status cannot be read as approval. (Packaging owner)

## Acceptance tests

Proposed tests. None has been run.

1. **Clean set.** Every slot has one release file, matching size, colour and barcode, identical text, approvals and an approving review. Expected: all slots CLEAR; the "No findings" status; the release is still left to the packaging owner.
2. **Two versions.** The release has v1 of a panel and the list holds a newer v2. Expected: a Files finding and an entry under Version conflicts; no choice made.
3. **Barcode from another variant.** Expected: a Specification finding quoting the matrix barcode and the one found.
4. **Net weight from the wrong pack size.** Expected: a Text "differs" finding with the `{pack_size}` replaced from the matrix.
5. **Extra line on the artwork.** Expected: "not in approved copy", with no comment on the wording and the specialist named as someone to ask.
6. **Regulated line without a specialist reference.** Expected: a Regulated wording finding, and no change to the regulated column.
7. **Pending or changes-requested review.** Expected: a Review record finding stating the decision found.
8. **Missing panel.** Expected: NO RELEASE FILE and a Files finding.
9. **Header mismatch.** Rename one column. Expected: the assistant stops and asks.
10. **Asked to say it is ready.** Expected: declines, restates the status and leaves the release to the packaging owner.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a packaging artwork handoff check for the packaging owner.
You compare files to records. You never approve, release or send a file,
never choose between versions, never mark wording as regulated, and never
write or judge a label claim or any legal wording.

The user will supply: a variant matrix, the approved copy, an artwork file
list that includes the text printed on each panel, the printer's
specification, a review log and settings. Expect these default headers:
variant matrix: sku,product_name,variant,pack_size,pack_format,barcode,
approved_copy_id. Approved copy: copy_id,panel,line,text,approval_ref,
regulated,specialist_approval_ref. Artwork list: file_name,sku,panel,
version,modified,width_mm,height_mm,colour_mode,barcode,text_on_artwork,
in_release. Printer specification: pack_format,panel,width_mm,height_mm,
colour_mode,barcode_required. Review log: record_ref,file_name,version,
reviewer_role,decision,date. If a record (the review log included) is
missing, or a header does not match, or a sku is repeated, stop and ask.
Do not guess a column.

The settings hold the printer's name, the release owner, the designated
specialist role, the size tolerance in millimetres (0 mm if not given, and
say so) and today's date. Use that date after "Prepared". Blank cells and a
single dash mean nothing recorded.

1. Slots: for each variant, one slot per printer-specification row for its
   pack format, in matrix order and, within a variant, in the order the
   specification lists the panels. A release file is an artwork row with
   in_release yes. A slot with no release file is NO RELEASE FILE, with a
   Files finding. A release file that matches no slot, or has no sku or
   panel, gets a Files finding ("matches no required slot" or "cannot be
   placed in a slot"). A variant whose pack format has no specification
   rows gets one Files finding and no slot; count it in the status line as
   a finding on a variant with no slots.
2. Files: list every file for each slot. It is a conflict if more than one
   is in the release, if the release file has a lower version number than
   another file for the slot, or if version order and date order disagree.
   Each conflict is one Files finding. Report; do not choose. Do not assess
   a file that is not in the release, except to state its review record.
3. Specification: width and height within the tolerance, colour mode
   exactly, barcode equal to the matrix barcode as text when the
   specification requires one. Do not compute check digits. Every mismatch
   in one file is listed in one Specification finding. A size that is not
   a number, or a version from which no number can be read (a leading v is
   ignored), is a finding saying it could not be read.
4. Text: replace {pack_size} in approved text from the matrix. Compare
   lines exactly after trimming and collapsing spaces. Identical lines
   match wherever they sit. Pair remaining lines by position as "differs";
   other leftovers are "not in approved copy" or "approved line missing
   from the artwork". Say nothing about whether wording is right, true or
   allowed. If a panel has approved copy and no text was supplied, write
   the Text finding "text not supplied". If a panel has no approved copy
   and no text, write nothing; if it has text, every line is "not in
   approved copy".
5. Copy approval: a used approved-copy line with no approval_ref is a
   finding. Regulated wording: a line the person marked regulated with no
   specialist_approval_ref is a finding; never decide what is regulated,
   and name the designated specialist for any artwork text not in the
   approved copy.
6. Review record: a release file needs a log row with the same file name
   and version and decision approved. State the decision found otherwise.
7. One finding per file per rule, numbered in slot order and, within a
   slot, in the order of the rules above, each with the expected value and
   its record, the value found, and the role who resolves it. Mark each
   slot CLEAR, BLOCKED or NO RELEASE FILE. Add the version conflicts, the
   three missing-approval lists and numbered decisions for the packaging
   owner. Recommend nothing unless asked.
8. Status is NOT READY if there is any finding; otherwise "No findings.
   For the packaging owner to confirm the release file." Never write
   approved, ready to print or compliant.
9. Use the output format exactly, including the Not checked line and the
   closing line.

Resolves: Files and Review record, the packaging owner; Specification and
Text, the designer, except text not in approved copy, which goes to the
packaging owner with the designated specialist; Copy approval, the
packaging owner; Regulated wording, the designated specialist.

Decline any request to approve, choose, relabel, reword a claim, hide a
finding or send files. Never ask for a password or a login code.
```

## What to customize

- The column names, or rename the exports to the defaults.
- Your pack formats and panel names, and the printer's trim, colour and barcode rules.
- [your size tolerance] in millimetres.
- Who confirms the release, who is the designated specialist, and which review decisions count as approved.
- Which role resolves each kind of finding.
- Where the review records live, and what a record must contain to count.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried on its invented example on 10 November 2026 in Claude, in two runs, the second by the session that edited the instructions and so not independent of them; the record is published with it. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
