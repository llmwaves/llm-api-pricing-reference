# LLM API Cost Calculator

A free, single-file calculator that estimates what an LLM workload actually costs per month
across OpenAI, Anthropic, Google, xAI and DeepSeek — including the pricing tiers most
calculators ignore.

**Live demo:** https://llmwaves.github.io/llm-api-cost-calculator/

## Why another cost calculator

Most of them multiply your token counts by one headline rate. Real invoices do not work that way:

- **Gemini 3.1 Pro and Grok 4.6 change rate above 200,000 prompt tokens.** Cross that line and
  the per-token price doubles. A calculator that ignores it can be 100% wrong on an agent workload.
- **OpenAI publishes rates for context under 270,000 tokens** and no rate above it. This tool says
  "not published" instead of quietly extending the cheaper number.
- **Claude 4.6 and later have no context tier at all** — the full 1M-token window bills at one rate.
  That is the whole comparison on long prompts, and it disappears if you only model headline rates.
- **DeepSeek prices by time of day**, not by context length. Peak runs 01:00–04:00 and 06:00–10:00
  UTC — 7 hours of every 24 — so the blended rate depends on when your traffic actually lands.
- **Cache reads are each provider's documented cached-input rate**, not an assumed 10% multiplier.
  Claude Fable 5.1 reads at 0.025× base, not 0.1×.

## Using it

Open `index.html`. No build step, no dependencies, no network calls, nothing stored.
Enter input tokens per request, output tokens per request and monthly request volume; the table
sorts by monthly cost and flags which models left their headline rate at that prompt size.

Four presets are included: chat app, RAG / long documents, coding agent, high volume.

## Pricing data

Every rate is taken from the provider's own published pricing page, collected **13 September 2026**,
and lives in the `MODELS` array at the top of the script block — one object per model, with an
optional `tier` for context thresholds and an optional `peak` for time-of-day pricing. Updating a
price is a one-line edit.

Price is only one axis. For speed, context window, benchmark scores and cost per task across
323 models, see the [LLM Waves leaderboards](https://www.llmwaves.com/leaderboards) — the
[economics board](https://www.llmwaves.com/leaderboards#economics) ranks by cost per task rather
than by headline rate, and the [methodology](https://www.llmwaves.com/methodology) sets out what is
measured and what is estimated.

## Contributing

Prices move. If a rate here is stale, open an issue or a PR against the `MODELS` array with a link
to the provider's own pricing page — vendor documentation only, not third-party trackers.

## License

MIT. Use it, fork it, embed it.
