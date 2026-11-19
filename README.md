# AI workflow templates for consumer brands

FullyPowered Workflow Templates for consumer brand teams turn the AI your company already pays for into a team that knows how the work is done: a wholesale account owner with every purchase order line checked against the approved quote, a product lead with one sample revision list drafted for the next supplier brief, a finance lead with the margin worksheet for every product in every channel prepared. 6 workflow templates, made to be customized and deployed. All plain Markdown, all free, MIT license.

We are FullyPowered AI. We build AI workflows for companies, and these are the templates we start from. We publish them because a good starting point should be open to everyone. Copy one. Change it. Make it yours.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** These are templates, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See more examples for consumer brand teams](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme) · [Have one built for your team](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme) Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Who this is for**

- Founders and general managers of consumer brands who want AI doing real work in product, operations and wholesale.
- Heads of product, operations and wholesale who want a workflow their team can run this week.
- The account owner, planner or quality lead who does the work, gets a precise preparation, and still decides.

**What these are for**

- **Your best way of doing it, for the whole team.** One piece of work, written down precisely enough that an assistant prepares it the same way every time.
- **Work you can check.** Every template says what it needs, what it produces, what it checked and what it could not.
- **A person decides.** Anything that sends, posts, pays or changes a record waits for someone to approve it.
- **Tied into your business systems.** A workflow can be designed to pull from the systems your company already runs, and even push data back into them, with guardrails and a person approving. [Browse the Connectors Directory](https://fullypowered.ai/connectors/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme).
- **Free, open and portable.** MIT-licensed plain instructions that run in the assistant or agent your team already uses: ChatGPT, Claude, Claude Code, Claude Cowork, Codex, Copilot, Gemini, Grok, Perplexity.

**Quick start**

1. **Check a retailer's order against your quote.** Open ChatGPT, Claude, Copilot or Gemini. Copy the text below into a new chat and put your own details in the square brackets. Paste in an order you already have and the quote it refers to. Nothing needs to be downloaded or signed up for.

   ```text
   You are helping the account owner check one retailer purchase order before anyone replies to the buyer. I will paste the purchase order lines, the buyer's notes and terms, [the approved quote], [the stock plan: units available and earliest delivery date per product] and [our account terms: delivery locations, payment terms, minimum order]. Compare every order line with the quote and stock plan on product, case pack, price, location, date and stock. Quote the buyer's terms and notes as written. Give me one page: order at a glance, line comparison, stock by product, exceptions (both figures, a question, and who decides), buyer terms, and what could not be checked. If a column or number is unclear, ask me. Never confirm, accept, price or promise anything. A person decides and nothing is sent or changed.
   ```

2. Read what comes back. It marks what it checked and what is left for you. What comes out: an invented wholesale order:

   ```text
   WHOLESALE ORDER CHECK: RA-77410

   For: the account owner, with operations. Account Retailer A. Purchase order dated 2026-11-09 against quote Q-2026-118 (dated 2026-10-20, valid until 2026-11-20). Prepared 2026-11-10.
   Inputs: purchase order 6 lines, quote 3 lines, stock plan 3 products, account terms supplied. Currency US dollars.

   Order at a glance: 6 lines, 140 cases, 1,410 units, 6,639.00 at the order's prices. Lines on the quote (5): 5,874.00 at the order's prices, 5,904.00 at the quote's prices, difference -30.00. Lines not on the quote (1): 765.00. Quote still valid on the order date. Minimum order value 2,500.00; the order's 6,639.00 is larger (compared on the whole order only).

   Line comparison
   Line 1, GR-350 Maple granola 350 g: 40 cases of 12 (quote 12), 480 units. Price 4.10 (quote 4.10). To Retailer A DC North (on account). Date 2026-12-01 (earliest 2026-11-30). Result: matches.
   ```

3. Stop there. You will know if this is for you. When you want it fitted to your company, or built into your agents, [that is what we do](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme).

The people at the brand decide: the template prepares and checks, and a person starts each piece of work, supplies the inputs and makes every decision.

These are samples and a starting point, made to be changed to fit how your brand works. Work that is not listed here can be built too, as one step or many.

## The workflow templates here today

- **[Batch distribution trace](batch-distribution-trace/)**: When the quality lead needs to know where one production batch went, they get a map from the batch record to every recorded shipment: quantities, transfers and repacking links, with each gap in the trace written as a question. It decides no hold and contacts nobody.
- **[Dated stock exposure list](dated-stock-exposure-list/)**: Before the next production or replenishment order, the supply planner gets a batch-by-batch list of stated dates, quantities and locations set against each retailer's acceptance rules, showing which batches need a decision. The quality owner and supply lead decide.
- **[Packaging artwork handoff check](packaging-artwork-handoff-check/)**: Before packaging artwork goes to print, the packaging owner gets a checklist that matches each file to the approved product facts, pack sizes, variants and printer specifications, with version conflicts, missing files and missing approvals listed. It writes and judges no label claim.
- **[Product sample feedback revision list](product-sample-feedback-revision-list/)**: After each round of samples, your product lead gets one revision list by sample version and feature: the changes people agree on, the feedback that conflicts, and drafted notes for the next supplier brief. The product owner decides.
- **[Range margin by channel review](range-margin-by-channel-review/)**: When a wholesale offer or a promotion changes the economics of a range, the finance lead gets a margin worksheet for every product in every channel, showing which cost layers are in each figure and which gaps are still open. It invents no cost and changes no price.
- **[Wholesale order check](wholesale-order-check/)**: When a retailer's purchase order arrives, the account owner gets every line set beside the approved quote and the stock plan: products, case packs, prices, delivery locations and dates, with each exception listed. People decide; nothing is confirmed to the buyer.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

To take the whole collection, press **Use this template** at the top of this page: it copies every folder into a repository in your own account, yours to change.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The workflow template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More workflow templates

The [FullyPowered Workflows Directory](https://fullypowered.ai/workflows/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

For the work these templates come from, by area of the business and by task, see [AI workflow examples for consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [FullyPowered AI](https://fullypowered.ai/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=consumer-brands-readme&from=gh-consumer-brands-readme).
