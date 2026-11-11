# Fully Powered Capability Templates: Consumer Brands

A brand that knows every product's story, from sample to shelf. These capability templates are written for consumer brands. They prepare the checking and tracing around products, stock and wholesale orders from your own records, and the brand's people decide what changes.

This repository holds 5 capability templates for the people who run product, operations and wholesale at a consumer brand. Each one is a single piece of work with its own folder: what it is for and who starts it, the complete template an AI assistant follows, a worked example with invented data, what to change for your company, what has been checked, and its sources.

## The capabilities

- **[Batch distribution trace](batch-distribution-trace/)**: When the quality lead needs to know where one production batch went, they get a map from the batch record to every recorded shipment: quantities, transfers and repacking links, with each gap in the trace written as a question. It decides no hold and contacts nobody.
- **[Dated stock exposure list](dated-stock-exposure-list/)**: Before the next production or replenishment order, the supply planner gets a batch-by-batch list of stated dates, quantities and locations set against each retailer's acceptance rules, showing which batches need a decision. The quality owner and supply lead decide.
- **[Packaging artwork handoff check](packaging-artwork-handoff-check/)**: Before packaging artwork goes to print, the packaging owner gets a checklist that matches each file to the approved product facts, pack sizes, variants and printer specifications, with version conflicts, missing files and missing approvals listed. It writes and judges no label claim.
- **[Range margin by channel review](range-margin-by-channel-review/)**: When a wholesale offer or a promotion changes the economics of a range, the finance lead gets a margin worksheet for every product in every channel, showing which cost layers are in each figure and which gaps are still open. It invents no cost and changes no price.
- **[Wholesale order check](wholesale-order-check/)**: When a retailer's purchase order arrives, the account owner gets every line set beside the approved quote and the stock plan: products, case packs, prices, delivery locations and dates, with each exception listed. People decide; nothing is confirmed to the buyer.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More capabilities

The [Fully Powered Capabilities Directory](https://fullypowered.ai/capabilities/) lists every capability across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the capability drew on. Published by [Fully Powered AI](https://fullypowered.ai/).
