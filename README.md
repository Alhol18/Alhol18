# Oleksandr Holovko

I run an e-commerce brand and build the AI agents and automations it runs on.

For seven years I have been building HOLBAND, a fitness equipment brand, from scratch. For the past year my main work has been rebuilding how it runs, with Claude Code, the Anthropic API and Cloudflare Workers. I had done almost every job in the business by hand, so I knew what was worth automating and where it would break.

Case studies with screenshots and technical details: **[holovko-ai.pages.dev](https://holovko-ai.pages.dev)**

## What I have built

These are examples, not the full list. The first five run in production in my own business, the last one was built for another team. The site has thirteen breakdowns.

| Process | What changed | Stack |
|---|---|---|
| **Business operating system** | An LLM with the full context of the company: money, stock, sales, customers, product. Data from every channel refreshes hourly, a brief is ready each morning, and decisions that need a human go into a queue. | Claude API, Python, Flask, PostgreSQL, Render, Shopify Admin GraphQL, GA4 Data API, Meta Marketing API |
| **[Fiscal receipts](https://github.com/Alhol18/shopify-checkbox-fiscal)** (open source) | Receipts were issued by hand every evening. Now a Worker issues the receipt when the payment arrives, opens the shift, and sends the receipt to the customer. Not a single manual receipt since 13 August 2026. | Cloudflare Workers, Shopify webhooks, HMAC-SHA256, KV for idempotency, CheckBox PRRO API |
| **Customer bot** | The same questions used to arrive in DMs. Now a Telegram bot sends the tracking number when the parcel ships and handles loyalty points, promo codes, referrals and reviews. Only the serious questions reach a person. | Telegram Bot API, Cloudflare Workers, Hyperdrive, PostgreSQL, Nova Poshta API |
| **Shipping notifications** | The manager had to keep checking the order system. Now each new waybill arrives as one Telegram message with the tracking number, the customer, the branch and a photo of every item. | Shopify webhooks, PostgreSQL jsonb, Telegram sendMediaGroup |
| **Finances** | 4,879 bank transactions over three years sorted automatically and reconciled to the penny: business apart from personal, results by year, margin by product. | Python, pdfplumber, Shopify Admin GraphQL |
| **Silent listener for work chats** (built for another team) | Instructions were born mid-conversation in Telegram groups and got lost there. One bot listens to the groups and never writes in them. A second one sends the team lead proposed tasks with the quote they came from, reminds people about deadlines and brings an evening summary of the day. The model proposes, a person confirms. Tested on two test groups. | Cloudflare Workers, Telegram Bot API, Mini App, PostgreSQL, Hyperdrive, Gemini |

I am opening these one by one as separate repositories.

## The system behind it

All of this runs on one setup: Claude Code as the daily operator, an instruction file, model routing, hooks, skills and plain Python tools. A brand-neutral extract is public: **[claude-code-operating-system](https://github.com/Alhol18/claude-code-operating-system)**.

As of 10 October 2026 the private setup holds 88 Python tools and data collectors, 18 project skills, 214 memory notes and a knowledge base of 188 pages.

## Results as of September 2026, last 12 months against the year before

| Metric | Change |
|---|---|
| Revenue | ×3.3 |
| Orders | ×2 |
| Average order value | +64% |
| Visits from search, June to August | ×2.2, with ₴0 spent on ads |

## How I work

- **By hand first.** I automate a process only after I have done it myself and know where it goes wrong.
- **The model reasons, code executes.** An LLM decides what needs to happen. Deterministic scripts do it, so the same input gives the same result.
- **The cheapest path to the same result.** Every tool has to earn its place. As of October 2026 the whole stack costs about ₴8,700 a month, less than one entry-level salary.
- **Check through a second route.** A result is verified by a different path than the one that produced it. The fiscal worker was checked this way: 100% match, 0 failures.
- **People decide, agents prepare.** Anything that needs a human judgment goes into a queue with the context attached.

## Background

Fifteen years in football: professional from 2010 to 2022 in the Ukrainian First League and Premier League, then semi-professional in France. Master's degree in Sport Psychology. Based in France, working remotely. Ukrainian, English, French, Russian.
