# Wholesale order check

When a retailer's purchase order arrives, the account owner gets every line set beside the approved quote and the stock plan: products, case packs, prices, delivery locations and dates, with each exception listed. People decide; nothing is confirmed to the buyer.

*Workflow template · Consumer brands · Sales · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/wholesale-order-check/)*

## The outcome

A purchase order from a retail buyer stops being something you skim and hope is right. Every line is compared, in the same order every time, with the quote you approved and the stock you planned: is this a product on the quote, in the case pack you quoted, at the price you quoted, going to a location on the account, on a date operations can meet, from stock that exists?

What does not match is listed once, with the two figures side by side and the person who decides. Lines that match say so. The account owner and operations then settle the order's terms and the delivery promise from one page instead of from a thread of forwarded emails, and the buyer hears nothing until they have.

## Who starts the work, and when

The account owner, or the sales coordinator who handles the account, starts it the day a purchase order arrives against an earlier quote. It runs again if the buyer sends a changed order.

The account owner decides what to accept, change or query, together with operations on stock and delivery dates. A person tells the buyer. The AI assistant tells the buyer nothing and changes no order record.

## What they supply

- **The buyer's purchase order,** with its lines and any notes or terms the buyer added.
- **The approved quote** the order refers to, with its date and how long it stands.
- **The stock plan:** what is available for each product and the earliest date it can arrive.
- **Your account terms,** as written: the delivery locations on the account, payment terms and any minimum order value.

## What comes out

One page in a fixed order:

1. **Order at a glance:** lines, cases, units and value, and what the lines on the quote come to at the order's prices and at the quote's.
2. **Line comparison:** one entry per purchase order line, showing product, case pack, price, location, date and stock against your records, and a result.
3. **Stock by product,** totalled across lines, because two lines can draw on the same stock.
4. **Exceptions:** each mismatch with both figures, the line, the question and the role that decides.
5. **Terms the buyer asked for,** quoted as written, set beside what your quote and account terms say.
6. **What could not be checked,** and a blank decision line for the account owner and for operations.

A good page lets the account owner see in a minute what the buyer would be getting if the order were accepted as sent.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Sales](https://fullypowered.ai/functions/sales/): the step between a buyer's order and your answer to it.
- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/): operations sees the stock and date questions before a delivery is promised.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/): wholesale orders from retailers arrive against a quote and a range that keeps changing.
- [Ecommerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/): brands that sell through stockists and marketplaces receive orders in many shapes.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/): makers who sell cases and pallets to trade buyers check the same things.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/): more accounts and bigger orders than one person can check by eye.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/): long-running accounts where quotes, case packs and locations have drifted.

It sits beside [Discount request review](https://fullypowered.ai/workflows/discount-request-review/), which handles a request for a lower price before an order exists, [Sales proposal preparation](https://fullypowered.ai/workflows/sales-proposal-preparation/), which produces the quote this check compares against, and [Unshipped order review](https://fullypowered.ai/workflows/unshipped-order-review/), which follows orders that are accepted but not yet shipped.

## What has to change for your company

- **Say what counts as your quote,** and keep its product list, case packs and prices in the columns the template expects.
- **Write your account terms down** so the check has something to compare to: delivery locations, payment terms, any minimum order value.
- **Agree the stock plan's shape:** the available units and the earliest delivery date for each product, and who produces it.
- **Name the people:** who runs the check, who decides with operations, who tells the buyer and who records the order.
- **Your platform.** The instructions are written to be pasted into ChatGPT, Claude, Copilot or Gemini. They work from files you supply and need no connection to your order or accounting systems.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example on 10 November 2026 in Claude, in two runs; the record of both is published with it. The instructions, the output format and the example were revised between the runs, and the second run, made by the assistant that revised them, is the one the published example shows. It has not yet been tested in a client environment, and it has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on past purchase orders your account owners remember well, plus hard cases written in advance: a case pack that differs from the quote, a location not on the account, two lines drawing on the same stock, a quote past its date, a term the buyer added. The account owner checks every figure against the order and the quote before anyone relies on the page. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [What we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) shows the record.

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

- [Discount request review](https://fullypowered.ai/workflows/discount-request-review/)
- [Sales proposal preparation](https://fullypowered.ai/workflows/sales-proposal-preparation/)
- [Unshipped order review](https://fullypowered.ai/workflows/unshipped-order-review/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
