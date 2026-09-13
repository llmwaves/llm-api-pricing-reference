# LLM API Pricing Reference — September 2026

Current published API rates for the major LLM providers, with the **pricing tiers and thresholds
that most comparison tables leave out**. Every figure below was read off the provider's own pricing
page on **13 September 2026**. No third-party trackers.

USD per 1,000,000 tokens unless stated otherwise.

---

## The short version

Four things break a simple price comparison, and almost nobody shows them:

1. **Gemini Pro and Grok 4.6 change rate above 200,000 prompt tokens.** The published price doubles.
2. **OpenAI's published rates cover context under 270,000 tokens.** There is no published rate above it.
3. **Claude 4.6 and later have no context tier at all** — one rate across the full 1M window.
4. **DeepSeek prices by time of day**, not by context length.

---

## OpenAI

| Model | Input | Cached input | Output |
|---|---|---|---|
| GPT-5.6 Sol | $5.00 | $0.50 | $30.00 |
| GPT-5.6 Terra | $2.00 | $0.20 | $12.00 |
| GPT-5.6 Luna | $0.20 | $0.02 | $1.20 |

**Threshold:** the pricing page states these rates apply to context lengths **under 270,000 tokens**.
No rate is published above that.

---

## Anthropic (Claude)

| Model | Input | Output | Cache write (5m) | Cache read |
|---|---|---|---|---|
| Claude Fable 5.1 | $10.00 | $50.00 | $12.50 | $0.25 |
| Claude Mythos 5.1 | $10.00 | $50.00 | $12.50 | $0.25 |
| Claude Opus 5 | $5.00 | $25.00 | $6.25 | $0.50 |
| Claude Sonnet 5 | $2.00 | $10.00 | $2.50 | $0.20 |
| Claude Sonnet 4.6 | $3.00 | $15.00 | $3.75 | $0.30 |
| Claude Haiku 4.5 | $1.00 | $5.00 | $1.25 | $0.10 |

**No long-context tier.** Claude 4.6 and later include the full 1M-token context window at standard
pricing: a 900,000-token request bills at the same per-token rate as a 9,000-token one.

**Cache reads are not a flat 10% everywhere.** Fable 5.1 and Mythos 5.1 read at 0.025× base input
($0.25); every other model uses the 0.1× multiplier.

**Fast mode** (Opus 5 and 4.8 only): $10 input / $50 output, across the full window.

---

## Google (Gemini)

| Model | Input | Output | Cache read | Notes |
|---|---|---|---|---|
| Gemini 3.1 Pro (Preview) ≤200K | $2.00 | $12.00 | $0.20 | doubles above 200K |
| Gemini 2.5 Pro ≤200K | $1.25 | $10.00 | $0.125 | doubles above 200K |
| Gemini 3.8 / 3.7 / 3.6 Flash | $0.75 | $3.75 | $0.075 | introductory rate |
| Gemini 3.5 Flash | $1.50 | $9.00 | $0.15 | |
| Gemini 3.5 Flash-Lite | $0.30 | $2.50 | not available | no context caching |

**Threshold:** above 200,000 prompt tokens, both Pro models bill at double the rates above.

**Expiry:** the 3.x Flash rates are introductory and run through **31 December 2026**. They increase
on 1 January 2027.

**Status:** Gemini 3.1 Pro is still **Preview**. Gemini 2.5 Pro is the only generally available
Pro-tier model.

**Service tiers:** Batch and Flex are 50% of Standard; Priority is roughly 80% above it. Flex is
synchronous, so it does not carry Batch's asynchronous wait.

---

## xAI (Grok)

| Model | Input | Cached input | Output |
|---|---|---|---|
| Grok 4.6 ≤200K prompt tokens | $2.00 | $0.50 | $6.00 |
| Grok 4.6 above 200K | $4.00 | $1.00 | $12.00 |

**Server-side tools are billed separately** and are missing from every comparison table: Web/X search
$5 per 1,000 calls, X user profiles $10/1K, file attachments $10/1K, code execution $5/1K,
collections search $2.50/1K, plus per-GiB storage and egress.

---

## DeepSeek

| Model | Off-peak input | Off-peak output | Peak input | Peak output |
|---|---|---|---|---|
| DeepSeek V4-Pro | $0.66 | $1.98 | $1.32 | $3.96 |
| DeepSeek V4-Flash | $0.22 | $0.66 | $0.44 | $1.32 |

**No context tier — a time-of-day tier instead.** Peak runs **01:00–04:00 and 06:00–10:00 UTC**,
seven hours of every twenty-four. Traffic that straddles both windows pays a blend, so a single
headline rate is not a real number for DeepSeek.

Cache hits discount input by roughly 30×.

---

## Where the comparison actually gets decided

Price per token decides less than it looks. A model at half the rate that needs three times the
output tokens to finish the same job is not cheaper.

The [LLM Waves leaderboards](https://www.llmwaves.com/leaderboards) track intelligence, coding and
agentic indices, output speed, context window and Arena Elo across 323 models, and the
[economics board](https://www.llmwaves.com/leaderboards#economics) ranks by **cost per task** rather
than by headline rate. What is measured and what is estimated is set out in the
[methodology](https://www.llmwaves.com/methodology).

---

## Corrections

Rates move, and this file will go stale. If a figure here no longer matches the provider's own
pricing page, open an issue or a PR with the link — vendor documentation only, not third-party
trackers.

## License

MIT.
