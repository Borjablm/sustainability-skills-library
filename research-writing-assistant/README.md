# Research Writing Assistant

End-to-end research and writing assistant for sustainability publications, ESG reports, and consulting articles. From a keyword or topic to a publish-ready article with sourced research, an adversarial writer/editor draft loop, and SEO meta.

**Created by:** Borja Blanco Méndez (borja@azvai.com)

---

## Use case

For sustainability communicators, ESG consultants, and research-led publishers who write analytical long-form content (explainers, comparisons, how-tos, list posts, reviews) where the data, sources, and tone all need to hold up.

The skill is designed for cases where a single prompt is not enough:

- A real dataset or source needs to be researched and cited
- Competitor content needs to be analysed for information gaps
- Brand voice has to stay consistent across many pieces
- An outline needs human approval before drafting
- The final draft needs an adversarial editor pass before it ships

Pairs naturally with the companion `article-images` skill (also in this library) for branded charts, stat cards, and stock imagery.

---

## How it works

5-stage pipeline with two human-approval checkpoints:

```
Stage 1: Brief & Competitor Analysis  →  brief.json + competitors/ + gap-analysis.json
Stage 2: Deep Research (Sonnet sub-agent)  →  research.json
Stage 3: Outline Planning (Opus sub-agent) →  outline.json     ⛔ USER APPROVAL
Stage 4: Adversarial Draft (Opus writer → Opus editor) →  draft.md
Stage 5: Polish & Deliver  →  article.md + meta.json    ⛔ USER APPROVAL
```

Each stage writes structured JSON outputs that feed the next, so the pipeline is auditable and re-runnable when sources update.

### First run: setup phase

On first use, the skill runs a 4-round setup interview to configure brand voice, writing guidelines, calibration examples, and runtime config. The result is saved and reused for every future article. Say "reconfigure" anytime to update.

### Article formats supported

| Format | Use for |
|--------|---------|
| `list` | "10 best [X]", "top tools for [Y]" |
| `how-to` | Step-by-step tutorials |
| `comparison` | A vs B evaluations |
| `review` | In-depth product or framework reviews |
| `explainer` | "What is [X]", "How does [X] work" |

---

## Example

**Input:**
> Write an explainer on "scope 3 category 1 spend-based emissions accounting" for a sustainability consulting audience. Target 2,500 words. Competitor URLs: [...]

**What happens:**
1. Stage 1 captures the brief, scrapes the competitor URLs, runs gap analysis
2. Stage 2 deep-researches across web sources (and optionally YouTube + X if Apify MCP is configured), saves a sourced `research.json`
3. Stage 3 produces an outline with section budgets, asks you to approve
4. Stage 4 writes a draft, then an editor sub-agent revises it (cuts hedging, enforces voice rules, removes em-dashes, verifies sources)
5. Stage 5 produces the final `article.md`, `article.html`, and `meta.json` (5 title options, 3-5 meta descriptions, slug), asks you to approve

**Output folder:**
```
scope-3-category-1-spend-based-2026-05-21/
├── brief.json
├── competitors/
├── gap-analysis.json
├── research.json
├── outline.json
├── draft.md
├── article.md         ← publish-ready
├── article.html       ← WordPress-ready HTML
└── meta.json          ← SEO meta
```

---

## Dependencies

**Pure Claude Code skill.** No Python, no Node.js, no system packages. Runs on Claude's built-in tools (`WebSearch`, `WebFetch`) plus sub-agents.

**Optional:** If you have the Apify MCP server configured in Claude Code, the skill will use it for YouTube transcript research and X/Twitter scraping. Without it, the skill falls back to `WebSearch` automatically.

**No API keys required.**

---

## Installation

This is a Claude Code skill (folder-based with sub-references). To install:

```bash
# Project-scoped
cp -r research-writing-assistant <your-project>/.claude/skills/

# User-scoped (available across all your projects)
cp -r research-writing-assistant ~/.claude/skills/
```

On first run, the skill walks you through the 4-round setup interview to configure brand voice and writing guidelines.

---

## Methodology source

The 5-stage pipeline structure (brief → research → outline → adversarial draft → polish) is adapted from the SEO content commands taught in [Authority Hacker's AI Accelerator](https://www.authorityhacker.com/ai-accelerator/). The non-commodity content rules align with Google's 2026 core update guidance on Information Gain.

---

## License

MIT (per library default).
