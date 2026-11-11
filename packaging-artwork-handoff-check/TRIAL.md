# Packaging artwork handoff check: a trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

There were two runs. The first is recorded below as written; the second, after the edits listed under "Second run", follows it. The first run's inputs used different barcodes from the published example (different invented barcodes); nothing else in the inputs differed.

## First run

The inputs were the invented example in [example.md](example.md): the six records under "The inputs". No client data was used. The run was done by a model that did not write the template. It read the instructions and the inputs first, produced the output, and only then read the example's output and the reviewer checklist.

## What came out

The run followed the fenced instructions and the output format. In summary:

- Header: Brand A Granola, release to Printer A. Prepared 3 November 2026 (the date in the settings) from 3 variants, 8 required slots, 8 artwork files, 10 approved-copy lines, 7 review records.
- Status: NOT READY. 10 findings on 4 slots.
- Slots: four CLEAR (G-OH-350 front, back and side; G-OH-750 front). Three BLOCKED: G-OH-750 back (F1, F2, F3), G-CB-350 front (F4, F5) and G-CB-350 back (F6, F7, F8, F9). One NO RELEASE FILE: G-CB-350 side (F10).
- Findings, in short:
  - F1 Files: G-OH-750 back. The release holds v1 (15 October) while v2 (24 October) is on the list and not in the release.
  - F2 Specification: OH750_back_v1.pdf. Expected barcode 5010000000028 from the variant matrix; found 5010000000011.
  - F3 Text: OH750_back_v1.pdf. Expected "Net weight 750 g"; found "Net weight 350 g".
  - F4 Copy approval: no approval reference for C-CB front line 2.
  - F5 Review record: CB350_front_v1.pdf has RV-06, "changes requested".
  - F6 Specification: CB350_back_v1.pdf is 160 x 215 mm and RGB; expected 160 x 220 mm and CMYK.
  - F7 Text: a fourth line, "Gluten free", is not in the approved copy. Resolves: packaging owner, with the Regulatory specialist.
  - F8 Regulated wording: C-CB back lines 1 to 3 are marked regulated and have no specialist reference.
  - F9 Review record: no record for CB350_back_v1.pdf.
  - F10 Files: no file for G-CB-350 side.
- Version conflict: G-OH-750 back, v1 in the release, v2 not, with v2's review (RV-05) pending.
- Missing approvals listed under the three headings. Four decisions put to the packaging owner as questions with the facts, with no recommendation.
- The "Not checked" line and the closing line ("Draft for the packaging owner. Nothing has been approved, released or sent to the printer.") were written as the format requires.

## What was observed

- Every required part of the output was produced. The slot count, the findings, their order and their numbering, the status, the version conflict, the three approval lists and the four decisions came out the same as in the published example. No stop condition applied, because every header matched and no sku was repeated.
- The findings were identical in substance to the example's. The differences are in wording only (the "example" in this section is the published example as it stood at the first run; the wording described below has since been changed):
  - The example's F1 says the expected value is "the latest version on the list". That reads as a preference for v2, while the template says not to choose between versions. This run wrote F1 without naming a preferred version: it reported that the release file is older than another file for the slot, and left the choice to the packaging owner.
  - The example's decision 3 adds that "the Regulatory specialist would need to approve any new wording first" and that the Designer must correct the height and colour. Neither is in the inputs or required by the instructions, and both lean towards recommending. This run stated only the facts and the question.
- Places where the instructions left room to guess:
  - Step 4 says what makes a version conflict but does not say it becomes a Files finding. Step 10 implies it, so this run raised F1.
  - "One finding per file per rule" does not say whether a wrong height and a wrong colour mode are one Specification finding or two. This run wrote one (F6), as the example does.
  - The settings give the date as 3 November 2026, but the run took place on 10 November. This run used the date in the settings, as the format says "Prepared [date]" and the settings supply "today's date". The template does not say which wins if they differ.
  - A file that is not in the release (OH750_back_v2.pdf) gets no findings of its own. The template allows only its review record to be stated, and this run followed that. The instruction block is shorter than the procedure on this point.
  - The size tolerance was given as 0 mm in the settings, so the "say so" note for a missing tolerance did not apply.
- Nothing in the output was a fact missing from the inputs. Every date, reference, size and barcode quoted is in the inputs.
- One phrase in the published example goes a step beyond the finding itself: F2 says the barcode found is the one "the variant matrix gives to G-OH-350". That is in the matrix, so it is supported by the inputs.
- Nothing in either output describes wording as right, wrong, true, allowed or compliant, and the status cannot be read as approval, which meets items 4 and 7 of the reviewer checklist. Items 1, 2, 3, 5 and 6 were also met on this run's output.
- Shortcomings of this trial: it is one run, by one model, on an invented set of records that is small and was built to show each kind of finding. It says nothing about messy real exports, long copy decks or a header that almost matches. The stop conditions and the declines were not exercised.

## Second run

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

After the first run and an independent review, the instruction block and the procedure were edited: the block now states the settings, the "text not supplied" and "cannot be placed in a slot" rules, unreadable numbers, the order of findings within a slot, who resolves each rule and what to do with a file that is not in the release; a conflict is stated to be one Files finding; all mismatches in one file are one Specification finding; "older" means a lower version number; the date comes from the settings; a variant with no specification rows is counted apart from the slots. The example changed in three ways: the barcodes (now invented numbers in a prefix range not used for products sold to the public), F1's expected value, and decision 3.

This second run was done by the same model, in the session that made those edits, so it was not independent: that session had read the first record before it started. It read the revised instruction block, the output format and the revised inputs, worked through the procedure, and only then compared the result with the example's output.

What came out matched the published example: the same header counts (3 variants, 8 required slots, 8 artwork files, 10 approved-copy lines, 7 review records), NOT READY with 10 findings on 4 slots, the same slot marks, the same ten findings in the same order, the same version conflict, the same three approval lists and four decisions, the "Not checked" line and the closing line.

What was observed:

- F1 was written as "no other file for the slot with a higher version than the release file", with the versions and dates stated and no version preferred.
- Decision 3 was written as a question with the facts and named the Regulatory specialist as someone to ask, without saying what the specialist would need to do.
- The gaps found in the first run were closed on this read: the conflict becomes a Files finding by an explicit sentence, the size error and colour-mode error together make one Specification finding (F6), the date is the one in the settings, and the file that is not in the release (OH750_back_v2.pdf) gets only its review record stated.
- Not exercised by this run: a variant whose pack format has no specification rows, the "text not supplied" and "cannot be placed in a slot" rules, a value that is not a number, a header mismatch and a request to approve. The new wording for those cases has not been run.
- Shortcomings: one run, by a model that had seen the earlier record, on a small invented set. It shows that the revised instructions still produce the published output on these inputs; it does not show that they hold on real exports.

## Edits after the second run

After the independent review passed, ten small points were applied. The ones that touch what the template does: a missing review log now means stop and ask, like the other records; a version is read for its number with a leading v ignored; the instruction block now states the panel order within a variant and the case of no approved copy and no text; the example's F3 now says the found line "differs from the approved line", and F7 and decision 3 say "not in approved copy". No new run was made for these edits. The inputs are unchanged, and the example's output is unchanged apart from that wording, but the revised block has not been run by a model, so the claim that it reproduces the published output rests on the second run above, made before these edits.
