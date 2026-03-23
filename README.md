<div align="center">

# DELTA

**An autonomous system that hunts for breakthrough deep-tech opportunities 24/7.**

It scans hundreds of sources daily, filters ideas through physics and market reality,  
and surfaces only what genuinely hasn't been built yet.

[![RD Engine](https://github.com/ecoopti3-prog/DELTA/actions/workflows/rd_engine.yml/badge.svg)](https://github.com/ecoopti3-prog/DELTA/actions)
[![SIM Engine](https://github.com/ecoopti3-prog/DELTA/actions/workflows/sim_engine.yml/badge.svg)](https://github.com/ecoopti3-prog/DELTA/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-orange.svg)](LICENSE)
[![Python 3.12](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)

</div>

---

## How It Works

```
[200+ sources] → [RD Engine: 4 cycles/day] → [♦ Diamond] → [SIM Engine: 8 physics steps] → [Verdict]
```

### RD Engine — Finds the Opportunity

Runs 4 autonomous cycles per day:

| Cycle | Time (UTC) | What Happens |
|-------|-----------|--------------|
| 1 — Harvest | 06:00 | Scans 200+ signals from 14 sources |
| 2 — Physics | 12:00 | Physics gate + novelty detection |
| 3 — Kill Round | 18:00 | Market analysis + devil's advocate |
| 4 — Director | 23:00 | Final scoring. Diamonds promoted. |

### SIM Engine — Validates With Real Physics

Every Diamond runs through 8 simulation steps:

```
1. Workload trace      → P(t), di/dt profile
2. Thermal 1D + 2D    → T_junction, hotspot, JEDEC margin
3. PDN RLC + SSN      → voltage droop, switching noise
4. Coupled solver     → thermal ↔ electrical Newton iterations
5. CMOS + PVT         → power model, timing corners
6. Aging NBTI+HCI+EM  → 10-year MTTF
7. Data movement      → roofline, NoC congestion
8. Monte Carlo        → 1000-sample yield analysis
```

Result: **score 0–10 + verdict: pursue / revise / kill**

---

## Quick Start

### 1. Clone

```bash
git clone https://github.com/ecoopti3-prog/DELTA
cd DELTA
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Set up Supabase

Create a free project at [supabase.com](https://supabase.com).  
Run `rd_engine/db/schema.sql` in the SQL Editor.

### 4. Add GitHub Secrets

Go to Settings → Secrets and add:

```
SUPABASE_URL
SUPABASE_KEY
GROQ_API_KEY
CEREBRAS_API_KEY
GEMINI_API_KEY
MISTRAL_API_KEY
COHERE_API_KEY
SAMBANOVA_API_KEY
GITHUB_TOKEN
HF_TOKEN
LENS_API_KEY
UNPAYWALL_EMAIL
NASA_API_KEY
SEMANTIC_SCHOLAR_API_KEY
MODELS_TOKEN
```

### 5. Run

Runs automatically via GitHub Actions — no server needed.

```bash
# Manual run:
cd rd_engine && python main.py --cycle 1
cd sim_engine && python main.py --auto
```

---

## Repository Structure

```
delta/
├── rd_engine/          ← Autonomous research engine
│   ├── agents/         ← 14 research + analysis agents
│   ├── core/           ← LLM router, base agent, schemas
│   ├── db/             ← Supabase client + feedback loop
│   ├── physics/        ← Physics gate (kills impossible ideas)
│   ├── novelty/        ← Embedding-based duplicate detection
│   ├── utils/          ← 14 data source scrapers
│   ├── config/         ← seed.json, settings
│   └── main.py
├── sim_engine/         ← Physics simulation engine
│   ├── simulations/    ← 8 physics simulation modules
│   ├── core/           ← Dispatcher, schemas
│   ├── db/             ← Supabase reader/writer
│   └── main.py
├── dashboard/          ← Live dashboards (connect to Supabase)
│   ├── rd/             ← RD Engine dashboard
│   └── sim/            ← SIM Engine dashboard
└── .github/workflows/  ← Automated schedules
```

---

## Data Sources (14)

| Category | Sources |
|----------|---------|
| Academic | arXiv, OpenAlex, CORE, CrossRef, HuggingFace Papers |
| Industry | GitHub Issues, RSS (IEEE, EE Times, SemiAnalysis, Tom's Hardware, Semiwiki) |
| Government | NASA NTRS, DARPA BAA, DOE OSTI, SEC EDGAR |
| IP | Lens.org Patents, OCP Specs |

---

## Research Domains

```
AI chips & accelerators    Thermal management       Power delivery (PDN)
Data movement & memory     Advanced packaging       Industrial robotics
Liquid cooling systems     Wiring & connectors      Fluid dynamics
```

---

## What a Diamond Looks Like

```
♦ Thermal-induced PDN impedance rise in 3D-stacked AI accelerators

Problem:  Thermal gradients increase PDN impedance by 15-40%,
          causing voltage droop during LLM inference bursts.

Physics:  T_op=35°C, droop=18mV, factor=0.012 — within safe range.
Market:   Score 10/10 — active pain at hyperscalers.
SIM:      score=6.93 · status=WARNING · verdict=revise PDN

Diamond score: 9.1 / 10
```

---

## LLM Providers — Auto-Fallback

```
Cerebras → Groq → Mistral → Cohere → SambaNova → Gemini
```

If one fails, the next takes over instantly. Zero downtime. All free tiers.

---

## License

MIT — use it, fork it, build on it.

---

<div align="center">

**Built to find what physics allows and the market hasn't built yet.**

</div>
