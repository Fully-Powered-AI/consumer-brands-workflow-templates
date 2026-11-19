# Batch distribution trace

Map one production batch from its record to every recorded shipment, with each gap written as a question. A person decides scope; it decides no hold.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Batch distribution trace on our website](https://fullypowered.ai/workflows/batch-distribution-trace/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the invented ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Consumer brands · Quality management · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/batch-distribution-trace/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace)*

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

This is not a recall contact plan and not a stock count. [Product recall customer contact plan](https://fullypowered.ai/workflows/product-recall-customer-contact-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace) starts after a recall has been issued and works from affected customers. [Stock count reconciliation](https://fullypowered.ai/workflows/stock-count-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace) compares a physical count with the books. This workflow template only answers where the records say one batch went, and where they do not say.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Quality management](https://fullypowered.ai/functions/quality-management/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), where a batch concern needs a fast, careful reading of where the stock is.
- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), which owns the movement and dispatch records the trace reads.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), where one batch can leave through several warehouses, a production partner and many retail accounts.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), for makers who ship their own batches onward through distributors.
- [Ecommerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), where a batch is split between marketplace, wholesale and own-site orders.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), where the records have grown over years and codes are written several ways.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace), when a second warehouse or a production partner has been added faster than the record keeping.

## What has to change for your company

- **Your exports.** The column names your systems produce, so the template reads them as they come, and the words they use for movement types.
- **Your batch codes.** How a code is written, what a near-match looks like in your records, and how you mark a mixed lot.
- **Your locations.** The warehouses, production partners and third-party sites, and which of them keep their own records.
- **Your units.** The unit each file counts in, and any conversion that repacking involves, agreed in advance.
- **Your people.** Who confirms scope, who verifies matches and who owns each kind of gap.
- **Your platform.** It runs in ChatGPT, Claude, Copilot or Gemini. Decide which files the assistant may read and where the trace is kept.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the record is published with it. Small wording edits made to the instructions and example after that trial have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past batch the quality lead already knows, with hard cases written in advance: a header that does not match, a receipt that differs from production, a transfer larger than the stock recorded, a line with two batch codes, a near-match code and a repack that changes the unit. Operations checks every route against carrier and retailer documents before anyone relies on the map. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace) describes the record we keep.

- Written by FullyPowered AI.
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

- [Product recall customer contact plan](https://fullypowered.ai/workflows/product-recall-customer-contact-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace)
- [Stock count reconciliation](https://fullypowered.ai/workflows/stock-count-reconciliation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace)
- [Supplier quality response check](https://fullypowered.ai/workflows/supplier-quality-response-check/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-batch-distribution-trace&from=gh-batch-distribution-trace).
