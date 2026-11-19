# Range margin by channel review

Get a margin worksheet for every product in every channel, with confirmed and estimated costs and open gaps listed. The finance lead decides.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Range margin by channel review on our website](https://fullypowered.ai/workflows/range-margin-by-channel-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the invented ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Consumer brands · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/range-margin-by-channel-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review)*

## The outcome

The question "which of our products earn money, and where?" gets an answer built from your own exports instead of a hunch. Each product is shown in each channel it sold through: net sales after discounts and returns, then the product cost, the packaging, the freight and the channel's fees, one layer at a time.

Every margin comes in two forms. One counts only the costs that have been confirmed. The other adds the costs that are estimates, such as an allocation someone agreed but nobody has invoiced. Where a cost is missing altogether, or a variant in the sales export has no match in the cost file, the worksheet says so on that line and puts the gap on a list of questions for the finance lead. It never fills a gap with a guess.

The worksheet recommends no price and no channel decision. The finance lead approves the cost basis; the commercial owner decides what to do about it.

## Who starts the work, and when

The finance lead, the bookkeeper or the founder runs it when an offer or a promotion is on the table, such as a wholesale account asking for better terms, a marketplace campaign or a new discount level. The offer or promotion is the occasion, not an input: the worksheet does not model its terms. It runs again whenever a missing cost turns up or an estimate is confirmed.

The finance lead reads the worksheet, answers its questions and approves the cost basis. The commercial owner, who sets prices and chooses channels, decides what follows.

## What they supply

- **A sales export** for one stated period, by product and channel: units, gross sales, discounts and returns.
- **A unit cost file:** each product's product cost and packaging cost per unit, each marked confirmed or estimated.
- **A channel cost file:** freight per unit and fees as a share of net sales for each channel, each marked confirmed or estimated, including any allocation the business has agreed. A channel layer that truly carries no cost is recorded as not applicable, so it is not mistaken for a missing figure.
- **The settings:** the period, the currency and, if you use one, a margin floor.

It works from the files you supply. No connection to your accounting system, shop platform or marketplace is needed, and it never asks for a password. If a column header does not match what it expects, it stops and asks.

## What comes out

One worksheet in a fixed order:

1. **The picture.** How many product and channel lines there are, how many are complete, how many have a gap, and a tie-out of net sales to the sales export.
2. **The grid.** One line for each product, with its margin in each channel.
3. **Margin by product and channel.** For each line, the sales, each cost layer marked confirmed, estimated or missing, and the margin on confirmed costs alone and with estimates added.
4. **The gaps.** Every missing, estimated or unmatched cost, and the lines it touches.
5. **Data notes and questions for the finance lead.**

Good looks like this: every figure traces to a row in an export, no margin is shown without saying which layers it includes, and nowhere does the worksheet say what a price should be.

This is not a price test and not a landed-cost calculation. [Price change review](https://fullypowered.ai/workflows/price-change-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review) works proposed prices through to gross profit, and [Product landed cost worksheet](https://fullypowered.ai/workflows/product-landed-cost-worksheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review) builds a product cost from an import shipment's invoices. This workflow template takes costs as you supply them and shows where each product stands across your channels.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), which owns the cost basis and the margin.
- [Analytics and reporting](https://fullypowered.ai/functions/analytics-and-reporting/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), where the same product can look strong in one channel and thin in another.
- [Sales](https://fullypowered.ai/functions/sales/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), where a wholesale or promotion decision is made.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), where one range sells through your own site, wholesale accounts and marketplaces at once.
- [Ecommerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), where channel fees and freight differ widely.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), for makers that sell their own goods through several routes.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), when a new channel has been added faster than its costs have been tracked.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review), where a range has sold the same way for years and nobody has looked at it channel by channel.

## What has to change for your company

- **Your exports.** The column names your systems produce, so the template reads them as they come.
- **Your channels.** The names you use, and which fees and freight each one carries.
- **Your cost layers.** The default layers are product, packaging, freight and channel fees. Add or remove layers to match how your finance lead builds a cost, and agree what makes a cost confirmed rather than estimated.
- **Your period.** A quarter is a sensible default; use a shorter one if costs or terms changed recently.
- **Your floor.** The margin below which a line is flagged, if you use one.
- **Your platform.** It runs in ChatGPT, Claude, Copilot or Gemini. Decide which files the assistant may read and where the worksheet is kept.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the record is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past quarter your finance lead knows well, with hard cases written in advance: an export whose headers do not match, a product with no packaging cost, a variant that exists in sales and not in the cost file, a fee rate of zero. The finance lead checks every figure against the exports before anyone relies on the worksheet. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review) describes the record we keep.

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

- [Price change review](https://fullypowered.ai/workflows/price-change-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review)
- [Product landed cost worksheet](https://fullypowered.ai/workflows/product-landed-cost-worksheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review)
- [Discount request review](https://fullypowered.ai/workflows/discount-request-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-range-margin-by-channel-review&from=gh-range-margin-by-channel-review).
