# Dated stock exposure list

Before the next production or replenishment order, the supply planner gets a batch-by-batch list of stated dates, quantities and locations set against each retailer's acceptance rules, showing which batches need a decision. The quality owner and supply lead decide.

*Workflow template · Consumer brands · Supply chain and inventory · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflow templates/dated-stock-exposure-list/)*

## The outcome

The supply planner sees, on one list, every batch of dated goods and where it stands against each account's rules: the date each batch was last able to ship to that account, how many days are left or how many were missed, and what the demand plan still sends there. The batches that need a decision are at the top, earliest first. Batches whose date cannot be placed are listed separately with the question that unlocks them.

The list reads dates exactly as stated. It does not interpret a date code, judge whether a product is suitable or say how long anything lasts. The quality owner confirms suitability and any restriction. The supply lead approves any action on the stock or the next order.

## Who starts the work, and when

The supply planner starts it when date-coded stock needs review before another production or replenishment order, or ahead of a planning meeting. The quality owner reads the open items; the supply lead reads the batches that need a decision.

## What they supply

- The stock-by-batch export: SKU, batch, location, quantity, unit and stated date, with the date label, storage note and status where the system holds them.
- The quality owner's approved date list for any batch whose date the export does not give plainly.
- The retailer acceptance rules the brand has on file, stated in days.
- The demand plan by SKU, account and week.
- Today's date, the date format, and how many days ahead count as close.

## What comes out

One list in a fixed order: batches that need a decision, dates that could not be placed, open items with the role that answers each, batches with nothing flagged, and notes on rules and plan lines that could not be used. Each batch line shows its stated date and where the date came from, and each account's last dispatch date worked out in days. It closes with totals by unit.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), where food, beauty and other dated goods sit in several warehouses and ship to accounts with their own rules.
- [E-commerce & retail](https://fullypowered.ai/industries/ecommerce-and-retail/), for brands and sellers who hold dated stock for retail accounts and marketplaces.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where production runs create batches that must be placed against open orders.
- [Supply chain & inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/), which owns the stock export, the demand plan and the order decisions.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), with several accounts and rule sets to hold in mind at once.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when a new retailer arrives with rules the existing spreadsheet was never built for.

## What has to change for your company

Set how many days ahead count as close, and the date format your system exports. Put your own transit days against each account. Agree who the quality owner is and how they record an approved date, so the date list keeps one shape. Decide which stock statuses (on hold, quarantine, reserved) you want copied through. Keep the rules table to what the account has actually stated in days; a rule written as a share of life remaining needs your quality owner or supply lead to supply the day count first.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026, and the record of that run is published with the template; it lists the edits made afterward, which clarify wording the run had to interpret and have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past stock position your team already understands, with cases written in advance: a month-only date, a date that conflicts with the approved list, a rule stated as a percentage, a batch split across two locations. The supply planner checks every date and day count against the export before anyone relies on the list. [Slow-moving stock and markdown plan](https://fullypowered.ai/workflows/slow-moving-stock-and-markdown-plan/) is the neighbouring workflow template for stock that sells too slowly; this one is about stated dates against account rules.

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

- [Slow-moving stock and markdown plan](https://fullypowered.ai/workflow templates/slow-moving-stock-and-markdown-plan/)
- [Clinic supply par levels and expiry check](https://fullypowered.ai/workflow templates/clinic-supply-par-levels-and-expiry-check/)
- [Inventory reorder plan](https://fullypowered.ai/workflow templates/inventory-reorder-plan/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
