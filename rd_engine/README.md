# R&D Engine — Autonomous Deep-Tech Research System

An autonomous research engine that runs 4 cycles per day, harvests scientific papers, patents, SEC filings, and government funding signals, validates ideas against deterministic physics laws, and surfaces high-value R&D opportunities in deep-tech domains.

---

## What It Does

Every day the engine runs automatically 4 times:

| Cycle | Time (UTC) | What Happens |
|-------|------------|--------------|
| 1 — Harvest | 06:00 | Collects papers, patents, RSS, jobs, GitHub, EDGAR, DARPA, NASA |
| 2 — Physics + Market | 12:00 | Validates ideas against physics laws, scores market pain |
| 3 — Kill Round | 18:00 | Devil's advocate removes weak or duplicate ideas |
| 4 — Director | 23:00 | Synthesizes findings, updates search strategy for next day |

---

## Research Domains

### Semiconductors & AI Hardware
| Domain | Physics Constraints |
|--------|-------------------|
| Thermal Management | Carnot limit, heat flux (W/cm²), spreading resistance, junction temperature |
| Power Delivery (PDN) | Landauer limit, IR drop, electromigration, PDN impedance |
| Data Movement | Roofline model, memory wall, bandwidth utilization, memory latency |
| Advanced Packaging | Signal integrity, mechanical stress, interconnect density, thermal resistance |
| Compute Scheduling | GPU utilization, load balancing, distributed training overhead |

### Robotics & Industrial
| Domain | Physics Constraints |
|--------|-------------------|
| Mechanical Fatigue | Young's modulus, S-N fatigue curves (Rainflow ASTM E1049), yield strength |
| Motors & Actuators | Back-EMF, torque ripple, thermal derating, bearing life (Weibull ISO 281) |
| Wiring Harness | Joule heating (I²R), arc flash threshold, insulation degradation, contact resistance |

### Liquid Cooling & Fluid Dynamics
| Domain | Physics Constraints |
|--------|-------------------|
| Fluid Dynamics | Bernoulli equation, Reynolds number, viscosity, pressure drop (Darcy-Weisbach) |
| Liquid Cooling | Cavitation (NPSH), galvanic corrosion, pump curve, cold plate temperature |

---

## Physics Gate

Every idea passes a **deterministic physics gate** before entering the pipeline. No LLM — pure math.

**Semiconductor physics:**
- Carnot efficiency limit
- Landauer energy per operation
- JEDEC junction temperature (JESD51)
- PDN impedance and IR drop
- Electromigration (Black's equation)
- Roofline model bandwidth wall

**Advanced physics (NumPy/SciPy):**
- Thermal resistance network — solves N-chip coupled matrix (NumPy)
- Rainflow fatigue counting (ASTM E1049, SciPy)
- Weibull bearing reliability (ISO 281, SciPy)
- Cold plate temperature distribution (1D energy ODE, NumPy)
- S-N fatigue curve, stress vs yield, vibration resonance

**Fluid & electrical:**
- Cavitation (Bernoulli + NPSH)
- Galvanic corrosion (EMF potential difference)
- Joule heating and voltage drop
- Motor back-EMF and thermal derating

---

## Data Sources (14 per cycle)

| Source | Type | Notes |
|--------|------|-------|
| arXiv | Papers | Full PDF text extraction |
| OpenAlex | Papers | Citation-sorted |
| HuggingFace | Papers | Daily papers |
| Semantic Scholar | Papers | Citation + influence scores |
| CrossRef | Papers | IEEE/ACM/Nature coverage |
| OSTI/DOE | Papers | Government research |
| NASA NTRS + Tech Transfer | Papers + Patents | 15 records |
| Lens.org | Patents | 10 patents |
| SEC EDGAR | Filings | 10-K/10-Q risk factors — NVIDIA/Intel/AMD/TSMC |
| DARPA + grants.gov | Funding | Government-confirmed unsolved problems |
| GitHub Issues | Signals | ML framework production pain |
| RSS (13 feeds) | News | IEEE, EE Times, SemiAnalysis, Robot Report, DataCenter Knowledge |
| Job Postings | Signals | Hiring = confirmed active pain |
| OCP (Open Compute) | Specs | Hyperscaler infrastructure signals |

---

## Architecture

```
Cycle 1 — HARVEST (7 agents)
├── PhysicsLimitMapper     — maps current physical bottlenecks
├── PaperResearcher        — arXiv + OpenAlex + CrossRef + S2
├── PatentResearcher       — Lens.org patents
├── InfraResearcher        — RSS + GitHub + EDGAR + DARPA
├── IntelligenceResearcher — job postings + company signals
├── RoboticsResearcher     — robotics + cooling domain signals
└── CrossDomainSynthesizer — finds inter-domain couplings

Cycle 2 — PHYSICS + MARKET (7 agents)
├── PhysicsGate            — deterministic validators (no LLM)
├── ThermalExtractor       — extracts quantified thermal parameters
├── PowerExtractor         — extracts power/PDN parameters
├── PDNExtractor           — extracts PDN impedance parameters
├── DataMovementExtractor  — extracts bandwidth/latency parameters
├── MarketAnalyst          — ROI model + buyer identification
└── CostAnalyst            — scalability score

Cycle 3 — KILL ROUND (5 agents)
├── ThermalEngineer        — deep thermal physics review
├── ElectricalEngineer     — electrical + PDN physics review
├── SystemsArchitect       — system-level feasibility review
├── DevilsAdvocate         — challenges all assumptions
└── CompetitionAnalyst     — prior art + market competition

Cycle 4 — DIRECTOR (3 agents)
├── HypothesisGenerator    — generates testable hypotheses
├── ChiefScientist         — synthesizes cross-cycle patterns
└── DirectorAgent          — executive summary + next cycle plan

Weekly Maintenance (1 agent)
└── WeeklyAnalyst          — trend analysis across 7 days
```
**Total: 23 agents**

---

## Diamond Score

Ideas are scored on 4 dimensions (0–10 each):

| Dimension | What It Measures |
|-----------|-----------------|
| Physics Feasibility | Does it violate known physical laws? |
| Market Pain | Is there a confirmed buyer with budget? |
| Novelty | Is it genuinely new vs prior art? |
| Scalability | Does the solution scale economically? |

A **Diamond** = score ≥ 8 across all dimensions.

---

## Memory System

The engine accumulates memory across days:
- **Killed idea titles** — never regenerates the same dead end
- **Diamond directions** — doubles down on what works
- **Evolved keywords** — search terms derived from successful findings
- **Domain success rates** — shifts focus to high-yield domains

Memory window: 14 days rolling.

---

## Research Profiles

```bash
python main.py --cycle 1 --profile chips       # AI hardware only
python main.py --cycle 1 --profile robotics    # Robotics only
python main.py --cycle 1 --profile datacenter  # Liquid cooling only
python main.py --cycle 1                       # All domains (default)
```

---

## Setup

### Environment Variables (GitHub Secrets)
```
GROQ_API_KEY, CEREBRAS_API_KEY, GEMINI_API_KEY
MISTRAL_API_KEY, COHERE_API_KEY
SUPABASE_URL, SUPABASE_KEY
GITHUB_TOKEN, HF_TOKEN
LENS_API_KEY, NASA_API_KEY, UNPAYWALL_EMAIL
```

### Run Manually
```bash
python main.py --test-physics   # run 55 physics gate tests
python main.py --cycle 1        # harvest
python main.py --cycle 2        # physics + market
python main.py --cycle 3        # kill round
python main.py --cycle 4        # director
```

---

## Tech Stack

- **LLM routing**: Cerebras → Groq → Mistral → Gemini (automatic fallback)
- **Embeddings**: sentence-transformers/all-MiniLM-L6-v2 (local)
- **Physics**: NumPy + SciPy (deterministic, no LLM)
- **Database**: Supabase (PostgreSQL)
- **CI/CD**: GitHub Actions (4 cycles/day automated)
