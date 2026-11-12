# Batch distribution trace

When the quality lead needs to know where one production batch went, they get a map from the batch record to every recorded shipment: quantities, transfers and repacking links, with each gap in the trace written as a question. It decides no hold and contacts nobody.

*Workflow template · Consumer brands · Quality management · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/batch-distribution-trace/)*

## The outcome

Following one batch through a warehouse network usually means four exports open side by side and a lot of patience. This workflow template does that reading for you. It starts from the batch record and follows the batch location by location, then out through each dispatch line to the account that received it, and it keeps a running balance so you can see how much of the batch each location is recorded as holding.

Where the records stop agreeing, the map says so rather than smoothing it over. A batch that was received short, a transfer that moved more than the location held, a repacking record whose quantities differ, a dispatch line with no batch code, a line carrying two batch codes and a code that is nearly, but not exactly, the one you are tracing: each becomes a numbered gap with the quantity at stake and a question for a named role. Nothing is assigned by guesswork and no gap is filled.

An incomplete trace cannot show that no other stock is affected, and the map says that in plain words whenever a gap is open. It decides no scope, no hold, no recall and no regulatory question, and it contacts nobody. The quality lead confirms the scope. Operations verifies the matches before anyone acts.

## Who starts the work, and when

The quality lead starts it, naming the batch code to trace, when a quality concern, a supplier or production-partner report, or a customer complaint points at one batch. It runs again when operations corrects a record or answers one of the questions.

Operations, usually the warehouse or logistics lead, checks the matches against carrier and retailer documents. The quality lead decides what the affected scope is and what happens next.

## What they supply

- **A batch record:** the batch code, product, production date and quantity produced.
- **A movement export** for the batch: receipts, transfers between locations, returns and adjustments.
- **Repacking records:** any batch relabelled or re-boxed into a new batch code.
- **Dispatch lines:** what shipped, from which location, to which destination, with the retailer reference and the carrier reference.
- **The settings:** the batch code to trace, the unit, and the people to name in the questions.

It works from files you supply. It needs no connection to your warehouse or order systems and never asks for a password. If a column header does not match what it expects, it stops and asks.

## What comes out

One trace in a fixed order:

1. **The batch.** What was produced and what was recorded as received.
2. **Where it moved.** Every movement in date order, with the recorded balance at each location after it.
3. **The batch-to-shipment map.** One line for each dispatch, with its route and whether it traces cleanly.
4. **Repacking links.** Each new batch code, its quantity compared with the quantity that went in, and its own shipments.
5. **Gaps in the trace.** Each one numbered, with its type, the rows involved, the quantity at stake and a question.
6. **For the quality lead and operations.** A tie-out line, what the records show by destination, what operations is asked to verify, and a closing statement that the trace is a reading of records and decides nothing.

Good looks like this: every number traces to a row in an export, no unresolved line is quietly counted in or out, and nowhere does the trace say a product is safe, unsafe or affected.

This is not a recall contact plan and not a stock count. [Product recall customer contact plan](https://fullypowered.ai/workflows/product-recall-customer-contact-plan/) starts after a recall has been issued and works from affected customers. [Stock count reconciliation](https://fullypowered.ai/workflows/stock-count-reconciliation/) compares a physical count with the books. This workflow template only answers where the records say one batch went, and where they do not say.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Quality management](https://fullypowered.ai/functions/quality-management/), where a batch concern needs a fast, careful reading of where the stock is.
- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/), which owns the movement and dispatch records the trace reads.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), where one batch can leave through several warehouses, a production partner and many retail accounts.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), for makers who ship their own batches onward through distributors.
- [Ecommerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/), where a batch is split between marketplace, wholesale and own-site orders.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where the records have grown over years and codes are written several ways.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when a second warehouse or a production partner has been added faster than the record keeping.

## What has to change for your company

- **Your exports.** The column names your systems produce, so the template reads them as they come, and the words they use for movement types.
- **Your batch codes.** How a code is written, what a near-match looks like in your records, and how you mark a mixed lot.
- **Your locations.** The warehouses, production partners and third-party sites, and which of them keep their own records.
- **Your units.** The unit each file counts in, and any conversion that repacking involves, agreed in advance.
- **Your people.** Who confirms scope, who verifies matches and who owns each kind of gap.
- **Your platform.** It runs in ChatGPT, Claude, Copilot or Gemini. Decide which files the assistant may read and where the trace is kept.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the record is published with it. Small wording edits made to the instructions and example after that trial have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past batch the quality lead already knows, with hard cases written in advance: a header that does not match, a receipt that differs from production, a transfer larger than the stock recorded, a line with two batch codes, a near-match code and a repack that changes the unit. Operations checks every route against carrier and retailer documents before anyone relies on the map. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

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

- [Product recall customer contact plan](https://fullypowered.ai/workflows/product-recall-customer-contact-plan/)
- [Stock count reconciliation](https://fullypowered.ai/workflows/stock-count-reconciliation/)
- [Supplier quality response check](https://fullypowered.ai/workflows/supplier-quality-response-check/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
