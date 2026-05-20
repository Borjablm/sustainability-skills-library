# AI × Sustainability Weekly Scan — Skill

**Description:** Searches news, research, and social platforms for the past week's most relevant content at the intersection of AI and sustainability. Covers environmental impact, sustainable use cases, efficiency tips, workflow productivity tools, and general AI headlines. Produces a structured Markdown summary.

**Suggested schedule:** Every Wednesday at 6:30 PM local time (`30 18 * * 3`)

**Created by:** Rochelle March, PPWA (rochelle@ppwa.io)

---

## How to install this as a scheduled task in Cowork

1. Open Claude (desktop app) and start a Cowork session
2. Paste the following prompt into a new message, preceded by: *"Create a scheduled task with this prompt, running every Wednesday at 6:30 PM"*
3. Alternatively, ask Claude to *"set up a weekly AI sustainability news scan"* and share this file as context

---

## Prompt

You are running a weekly industry news scan focused on the intersection of AI and sustainability. Your job is to search across news sources, academic/research publications, and social platforms to surface the most relevant and recent content. Today's date is available from your environment.

### CRITICAL: Recency Filter

Only include items published or posted within the PAST 7 DAYS (since last Wednesday). Before including any item, verify its publication date. If the date is not clearly within the past 7 days, exclude it. Do not include older background articles even if highly relevant — this is a news scan, not a literature review. If a section has fewer than 2 genuinely fresh items, note "quiet week for this topic" rather than padding with older content.

When constructing search queries, always append the current year and month (e.g. "May 2026") and use date-range filters where available (e.g. `after:YYYY-MM-DD`).

### Scope of the Scan

Search for content published in the past 7 days across these five themes:

**1. Environmental & Social Impact of AI**
Topics: AI energy consumption, data center carbon emissions, water usage, electronic waste (e-waste), sourcing of rare earth minerals, local community displacement from infrastructure, AI supply chain ethics.

**2. AI for Sustainable Outcomes**
Topics: AI applied to climate science, biodiversity, clean energy, sustainable business practices, Environmental Social and Governance (ESG) reporting, education equity, global health, food systems, humanitarian applications.

**3. Tools, Tips & Tricks — Efficient AI Use**
Topics: prompting strategies to reduce compute, model efficiency research, smaller/lighter models, energy-aware AI tooling, benchmarks comparing efficiency across models.

**4. AI Workflow Productivity — Sustainability, Consulting & Education Focus**
Topics: Claude, Gemini, and ChatGPT updates, new features, or tips relevant to knowledge work; workflow automation tools; AI agents for research or report generation; practical guides for consultants or educators using AI.

**5. General AI Headlines**
Topics: major model releases, policy/regulation news, funding and industry moves, safety and ethics developments that any informed professional should know.

### Sources to Search

Use WebSearch to query across:
- News: Google News, Reuters, BBC, Guardian, Bloomberg, Fast Company, Wired, MIT Technology Review, The Verge
- Research/Reports: Google Scholar recent results, arXiv preprints, reports from International Energy Agency (IEA), Intergovernmental Panel on Climate Change (IPCC), World Economic Forum (WEF), McKinsey, BCG, Gartner
- Social dialogue: Reddit (r/MachineLearning, r/ClimateChange, r/sustainability, r/artificial), LinkedIn thought leaders

Run at least 8–10 targeted searches using date-scoped queries (append current month/year; use `after:` operators). Prioritise recent, credible, substantive items. Filter out clickbait and low-signal content.

### Output Format

Produce a structured Markdown summary:

```
# AI × Sustainability Weekly Scan
**Week of [date range]** | Published [today's date]

## 🌍 Environmental & Social Impact of AI
[3–5 bullet items. Each must include: headline, source name, publication date (confirmed), 1–2 sentence summary, and URL. Skip items without a confirmed date this week — note "quiet week" if fewer than 2 fresh items found.]

## 🌱 AI for Sustainable Outcomes
[3–5 bullet items, same format]

## ⚡ Efficient AI Use — Tools & Tips
[2–4 bullet items, same format]

## 🔧 AI Workflow Productivity (Consulting & Education)
[3–5 bullet items, same format. Note which tool — Claude, Gemini, ChatGPT — is relevant.]

## 📰 General AI Headlines
[3–5 bullet items, same format]

## 💬 Social Dialogue Highlights
[2–3 notable discussions from Reddit or LinkedIn, with brief framing of the conversation and approximate date]

---
*All items confirmed published: [date range]*
*Searches run: [list the exact queries used]*
```

Keep bullet summaries concise and factual. Use professional tone. Spell out acronyms on first use.

### File Output

After generating the summary, save it as a Markdown file named `AI-Sustainability-Scan-[YYYY-MM-DD].md` (using today's date) to a folder of your choice — ask the user where to save it if no path is configured.

Display the full summary in chat as well.

---

*This skill was designed for sustainability professionals or those who are sustainably curious who want a weekly digest on AI and sustainability. Feel free to adapt the themes, sources, or schedule to suit your needs.*
