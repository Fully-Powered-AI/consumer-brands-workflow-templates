# Packaging artwork handoff check

Before packaging artwork goes to print, the packaging owner gets a checklist that matches each file to the approved product facts, pack sizes, variants and printer specifications, with version conflicts, missing files and missing approvals listed. It writes and judges no label claim.

*Workflow template · Consumer brands · Marketing and content · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflow templates/packaging-artwork-handoff-check/)*

## The outcome

The packaging owner sends artwork to the printer knowing what was compared and what was not. Every variant and every panel the printer needs has a line on one checklist: the file proposed for release, whether its size, colour mode and barcode match the printer's specification, whether its text matches the approved copy character for character, and whether a recorded approval exists for that exact version.

The things that usually surface after the plates are made surface first: an older version going out while a newer one sits in the folder, a barcode copied from the neighbouring pack size, a weight statement that belongs to another variant, a panel nobody sent. Each is written as a finding with the expected value, the value found and the role who resolves it.

Nothing on the checklist says the artwork is right. It says what matches the records you supplied and what does not. The packaging owner confirms the release file. A designated specialist approves any regulated wording. The assistant does neither.

## Who starts the work, and when

The packaging owner, the brand manager or the production coordinator starts it when a packaging revision is about to go to print, once the files have been exported and the review records are in. It runs again each time a file is replaced, because a new version is a new file to check.

## What they supply

- **Variant matrix.** One row per product variant and pack size: the code, name, pack size, pack format and barcode.
- **Approved copy.** The approved wording, line by line and panel by panel, with its approval reference. Whoever owns the wording marks which lines are regulated and gives the specialist's approval reference for those.
- **Artwork file list.** Each file with its product code, panel, version, date, dimensions, colour mode, barcode, the text printed on the panel, and whether it is proposed for release. The person types or pastes the text from the file; the assistant does not open artwork.
- **Printer specification.** For each pack format and panel, the trim size, colour mode and whether a barcode is required.
- **Review log.** Who reviewed which file and version, and what they decided.

## What comes out

One checklist with a line for every required file slot, marked clear, blocked or missing, followed by numbered findings. Each finding names the rule, the file, the expected value and where it came from, the value found, and who resolves it. Then three short lists: version conflicts, missing approvals, and the questions only the packaging owner can answer. A fixed line states what was not checked: print quality, colour accuracy, legibility and whether any wording is correct.

When nothing is found, the checklist says so and still leaves the release to the packaging owner.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Marketing and content](https://fullypowered.ai/functions/marketing-and-content/), where the packaging revision is owned and the copy is kept.
- [Quality management](https://fullypowered.ai/functions/quality-management/), where review records and approvals need to match the version that ships.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), where one product comes in several pack sizes and variants, each with its own artwork.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where packaging is printed to a supplier's specification and a wrong plate is paid for.
- [E-commerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/), where a private-label range is sent to print by a small team.
- [New business lines](https://fullypowered.ai/situations/new-business-lines/), when a first range or a new pack size is going to print.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when the number of variants outgrows the memory of the person who sends the files.

This workflow template checks files against records. To edit wording, use [Copy-edit with a change list](https://fullypowered.ai/workflows/copy-edit-with-a-change-list/). To plan the weeks around a launch, use [Launch checklist](https://fullypowered.ai/workflows/launch-checklist/). To check the facts on a product page, use [Product-page facts gap review](https://fullypowered.ai/workflows/product-page-facts-gap-review/).

## What has to change for your company

Use your own column names or rename them to the defaults; the assistant stops and asks when a header does not match. Decide what counts as a pack format and a panel in your range. Set the size tolerance the printer allows. Name the specialist who approves regulated wording and the role that marks which lines are regulated; the assistant never decides that. Agree where review records are kept and what a valid one contains. Decide who may change the release file once the packaging owner has confirmed it. It runs in ChatGPT, Claude, Copilot or Gemini from the files you supply and needs no connection to your design or print systems.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example on 10 November 2026 in Claude, in two runs, the second not independent of the edits made after the first; the record is published with it. It has not been tested in a client environment, and it has not been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past print run your team remembers well, plus hard cases written in advance with their expected behavior: two versions of one panel, a barcode that belongs to another size, a regulated line with no specialist reference, a header that does not match. The packaging owner checks every finding against the files before anyone relies on the checklist. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) shows the record.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Launch checklist](https://fullypowered.ai/workflow templates/launch-checklist/)
- [Copy edit with a change list](https://fullypowered.ai/workflow templates/copy-edit-with-a-change-list/)
- [Product-page facts gap review](https://fullypowered.ai/workflow templates/product-page-facts-gap-review/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
