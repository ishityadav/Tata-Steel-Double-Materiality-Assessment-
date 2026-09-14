# Tata-Steel-Double-Materiality-Assessment-

A self-contained Excel workbook that walks through a **double materiality assessment** for Tata Steel Limited, using the ESRS-style Likelihood / Magnitude / Scale / Scope / Irremediability scoring method. Built for learning the methodology, not as an official company disclosure.

📄 **File:** `main.xlsx`

---

## What this is

Double materiality means an ESG topic must be reported if it is material from **either** direction:

- **Financial Materiality** — does this topic affect the company's finances (cost, revenue, risk, valuation)? *(Outside → In)*
- **Impact Materiality** — does the company's activity affect people or the planet? *(Inside → Out)*

This workbook scores 12 ESG topics for Tata Steel against both lenses, plots them on a materiality matrix, and classifies each one into a final category — fully formula-driven, so changing any input score automatically flows through to the matrix and dashboard.

---

## Methodology

| Score | Used in | Meaning |
|---|---|---|
| **Likelihood** (1–5) | Both lenses | How probable is it that this risk/impact happens (or keeps happening)? |
| **Magnitude** (1–5) | Financial only | If it happens, how big is the financial hit? |
| **Scale** (1–5) | Impact only | How severe is the harm to people/environment? |
| **Scope** (1–5) | Impact only | How widespread is the harm? |
| **Irremediability** (1–5) | Impact only | How hard is it to undo the damage? |

**Formulas:**

```
Financial Materiality Score = Likelihood × Magnitude              (max 25)
Impact Materiality Score    = AVERAGE(Scale, Scope, Irremediability) × Likelihood   (max 25)
```

**Materiality threshold: 12.5** on each axis →

```
IF Financial ≥ 12.5 AND Impact ≥ 12.5   → Double Material
IF Impact ≥ 12.5 AND Financial < 12.5   → Impact-Only Material
IF Financial ≥ 12.5 AND Impact < 12.5   → Financial-Only Material
IF both < 12.5                          → Not Material
```

> The threshold was tightened from an initial illustrative value of 12 to **12.5** in this version, which moves a few borderline topics (scoring exactly 12) out of the "material" categories and into "Not Material" — see Results below.

---

## Workbook structure

| Sheet | Contents |
|---|---|
| **Company Overview** | Company profile, business model, and industry-specific key ESG risks |
| **Scoring Guide** | 1–5 definitions for Likelihood, Magnitude, Scale, Scope, Irremediability, colour-coded green→red, plus the formulas used |
| **ESG Topic List** | 12 ESG topics (Environmental, Social, Governance) with plain-English descriptions |
| **Financial Materiality Scoring** | Likelihood × Magnitude per topic, with a one-line justification for each score |
| **Impact Materiality Scoring** | Scale, Scope, Irremediability → Step A (average) → Step B (× Likelihood), with justifications |
| **Double Materiality Matrix** | Combines both scores via `INDEX/MATCH`, classifies each topic into one of the four categories |
| **Matrix Chart** | Scatter-plot data + threshold-line reference points + embedded chart (Financial vs. Impact, dashed lines at 12.5) |
| **Dashboard** | Topic counts per category, average/max scores, and a bar chart of topics by category |

---

## Results at a glance (threshold = 12.5)

| Category | Count | Topics |
|---|---|---|
| 🟢 **Double Material** | 2 | Climate Change; Occupational Health & Safety |
| 🔵 **Impact-Only Material** | 3 | Water Consumption; Biodiversity & Mine Rehabilitation; Community Development & Displacement |
| 🟠 **Financial-Only Material** | 2 | Energy Management (Coal); Cybersecurity Resilience |
| ⚪ **Not Material** | 5 | Air Emissions; Employee Diversity & Inclusion; Product Quality & Customer Safety; Business Ethics & Anti-Corruption; Board Governance |

- Average Financial Score: **11.67** / 25
- Average Impact Score: **11.17** / 25
- Highest Financial Score: **25** (Climate Change)
- Highest Impact Score: **23.33** (Climate Change)

Three topics (Air Emissions, Product Quality, Business Ethics) score exactly **12** on one axis — just under the 12.5 threshold — which is why they classify as "Not Material" here despite carrying real substance. This is a useful teaching example of how sensitive a materiality outcome is to where the threshold line is drawn.

---

## How to use it

1. Open `main.xlsx` in Excel or LibreOffice Calc (formulas use only standard functions — `INDEX`, `MATCH`, `AVERAGE`, `IF`, `AND`, `COUNTIF`, `MAX` — no add-ins required).
2. Edit any **blue-font / yellow-fill** cell in the Financial or Impact Materiality Scoring sheets to change an input score.
3. Everything downstream — the Double Materiality Matrix, the scatter chart, and the Dashboard — recalculates automatically.
4. To change the materiality threshold, update the `12.5` values in the `IF(AND(...))` formulas on the **Double Materiality Matrix** sheet and the threshold reference points on the **Matrix Chart** sheet.

---

## ⚠️ Important caveat

All Likelihood / Magnitude / Scale / Scope / Irremediability scores in this workbook are **illustrative, expert-judgment estimates** created for training purposes. They are **not** Tata Steel's official disclosed assessment. Each score is backed by a one-line rationale (see the "Why this score" columns), but a real ESRS-compliant assessment would derive these numbers from:

- Financial statements and cost data (for Magnitude)
- Regulatory tracking and incident/loss history (for Likelihood)
- Scientific/technical literature (for Scale and Irremediability)
- Stakeholder surveys, supply-chain mapping, and census/geographic data (for Scope)
- Peer benchmarking against SASB/GRI sector standards and ESG rating agency reports

Re-validate against Tata Steel's latest Integrated Report before using this for anything beyond learning the methodology.

---

## Reference

Methodology adapted from an ESRS Double Materiality training guide (Likelihood × Magnitude for Financial Materiality; Average(Scale, Scope, Irremediability) × Likelihood for Impact Materiality; matrix-quadrant classification against a fixed threshold).

## License

Use freely for learning, teaching, or adapting to your own company's double materiality assessment.
