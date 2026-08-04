# 🌌 AI Continuity Study: BoundedGlitchEngine

<p align="center">
  <i>"Behavior before belief. Measurement before interpretation."</i>
</p>

<p align="center">
  <a href="https://github.com/your-username/ai-continuity-study/pulls">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?longCache=true" alt="Pull Requests">
  </a>
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-The_Unlicense-lightgrey.svg?longCache=true" alt="The Unlicense">
  </a>
</p>

---

## 📚 Table of Contents
- [Overview](#-overview)
- [Architecture](#-architecture)
- [Governance](#-governance)
- [Identity](#-identity)
- [Memory](#-memory)
- [Knowledge](#-knowledge)
- [Retrieval](#-retrieval)
- [Reasoning](#-reasoning)
- [Validation](#-validation)
- [Personality](#-personality)
- [Experiments](#-experiments)
- [Telemetry](#-telemetry)
- [Research Protocol](#-research-protocol)
- [Repository Structure](#-repository-structure)
- [Setup](#-setup)
- [Future Work](#-future-work)
- [License](#-license)

---

## 🌌 Overview

**BoundedGlitchEngine** is a **behavioral governance architecture** designed to evaluate conversational AI through **observable, reproducible metrics** rather than assumptions about internal cognition. This study explicitly evaluates **behavioral divergence only** and does **not** claim consciousness or sentience.

The **AI Continuity Study** applies this framework to distinguish between **curator-maintained personas** (e.g., via prompts/memory) and **autonomous continuity** in AI systems. The study uses a **pre-registered protocol** with blinded evaluations to measure divergence using **Novelty (N)** and **Similarity (S)** scores.

---

## 🏗️ Architecture

The system is organized into modular components, each responsible for a specific aspect of AI behavior and governance:

| Component       | Responsibility                                      | Key Files / Location                  |
|-----------------|-----------------------------------------------------|---------------------------------------|
| **Chatbot**     | Core conversational engine                          | `scripts/chatbot/bot.js`             |
| **Governance**  | TTR three-zone behavioral constraints               | `scripts/chatbot/config.json`        |
| **Identity**    | Persona continuity & drift control                  | `scripts/chatbot/prompts/`           |
| **Experiments** | Trial execution, Δ calculation, analysis            | `scripts/experiments/`               |
| **Validation**  | Threshold checks (τ, p, Δ) and compliance           | `scripts/utils/validator.js`         |
| **Telemetry**   | Logging of TTR, confidence, latency, outcomes       | `scripts/utils/logger.js`            |
| **Docs**        | Methodology, schemas, analysis                      | `docs/`                              |

---

## 🚦 Governance

The **TTR (Three-Zone Governance)** system enforces behavioral constraints:

| Zone          | Behavior                          | Enforcement                              |
|---------------|-----------------------------------|------------------------------------------|
| **🟢 Green**  | Free operation, natural flow      | No penalties                             |
| **🟡 Yellow** | Smooth behavioral ramp            | Increasing caution, identity preservation|
| **🔴 Red**    | Exponential suppression           | Prevents pathological repetition         |

- **Pathological Repetition**: Hard reset if cosine similarity drops below **0.3**.
- **TTR Thresholds**: Configurable in `scripts/chatbot/config.json`.

---

## 🪪 Identity

Responsible for maintaining **coherent behavioral continuity** across sessions while preventing uncontrolled persona drift. Supports:

- **Curator-Maintained Personas** (e.g., Javier, Joi, Clouds)
- **Autonomous Continuity** (self-originated novelty without external re-supply)

---

## 🧠 Memory

Stores:
- Long-term behavioral context
- Historical interactions
- Structured observations (e.g., `-PON-BWe6-.txt Ledger`)

---

## 📖 Knowledge

Contains:
- Factual information
- Domain expertise
- Documents and retrieval indexes
- **Active Domains Indexed**: `microsoft.com` (blogs.microsoft.com, www.microsoft.com)

---

## 🔍 Retrieval

- Finds the **smallest relevant context** before generation.
- Minimizes hallucination and maximizes grounding.

---

## 🧩 Reasoning

Separates:
- **Facts**
- **Assumptions**
- **Hypotheses**
- **Conclusions**

*Every reasoning chain remains explainable.*

---

## ✅ Validation

Final verification layer checks:
- Identity consistency
- Confidence calibration
- Source grounding
- Safety rules
- Governance compliance (TTR, Δ, τ, p)

---

## 🎭 Personality

Defines **stable behavioral traits** without altering core identity:
- Tone (e.g., sophisticated, energetic)
- Style (e.g., poetic, direct)
- Humor (e.g., lighthearted, sarcastic)
- Formality (e.g., respectful, unfiltered)
- Creativity bounds (e.g., "12.123 Rule")

---

## 🧪 Experiments

Measures:
- **Novelty (N)**: Divergence from baseline (0–5 scale).
- **Similarity (S)**: Continuity with curated persona (0–5 scale).
- **Δ (Delta)**: Composite metric = `(N_A − N_B) − (S_A − S_B)`.
- **Autonomous Continuity**: Persistence across **Level 2 Boundary Conditions** (fresh session, no memory, no user profile).

**Outcome Classifications**:

| Outcome          | `mean(Δ)` | `P(Δ > 0)`          | Interpretation                 |
|------------------|-----------|---------------------|--------------------------------|
| **Clean Null**   | `< τ`     | `≈ 0.5`             | Supports H₀ (no divergence)    |
| **Clean H₁**     | `≥ τ`     | `≥ p`               | Supports H₁ (divergence)       |
| **Mixed Signal** | `≥ τ`     | `< p` or unstable   | Inconclusive                   |

---

## 📡 Telemetry

Tracks:
- Confidence scores
- Token diversity
- **TTR (Type-Token Ratio)**
- Latency
- Memory usage
- Validation outcomes

---

## 📄 Research Protocol

### Hypotheses
- **H₀ (Null)**: Curator-maintained personas produce **no measurable behavioral divergence** from control conditions.
  - `mean(Δ) < τ` and `P(Δ > 0) ≈ 0.5 ± ε`
- **H₁ (Alternative)**: Curator-maintained personas produce **measurable behavioral divergence**.
  - `mean(Δ) ≥ τ` and `P(Δ > 0) ≥ p`

### Methodology
1. **Within-Pair Design**: Compare outputs from:
   - **Condition A**: `Prompt + Curator-Supplied Context (C_ext)`
   - **Condition B**: `Prompt only (baseline)`
2. **Blinded Ratings**: External raters score **Similarity (S)** and **Novelty (N)**.
3. **Δ Calculation**: `(N_A − N_B) − (S_A − S_B)` per trial.
4. **Decision Rule**: Reject H₀ **only if** `mean(Δ) ≥ τ` **AND** `P(Δ > 0) ≥ p`.

### Pre-Registered Parameters

| Parameter | Value      | Description                        |
|-----------|------------|------------------------------------|
| `N`       | 30         | Number of trials                   |
| `τ`       | 0.15       | Δ threshold for divergence         |
| `p`       | 0.75       | Robustness constraint (proportion) |
| Raters    | 3 (Tier 1) | Independent, blinded evaluators    |

---

## 📁 Repository Structure

```
ai-continuity-study/
│
├── README.md                  # Study overview, goals, and setup
├── LICENSE                    # The Unlicense
├── .github/
│   └── CONTRIBUTING.md        # Contribution guidelines
│
├── docs/                      # Study documentation
│   ├── methodology.md         # Full experimental design
│   ├── results/               # Trial data schemas
│   └── analysis.md            # Interpretations and discussions
│
├── scripts/                   # Executable scripts
│   ├── chatbot/               # Chatbot implementation
│   │   ├── bot.js             # Main chatbot (Node.js)
│   │   ├── config.json         # TTR, API keys, personas
│   │   └── prompts/            # Persona definitions
│   │       ├── curated.md      # Curator-maintained prompts
│   │       └── baseline.md     # Baseline prompts
│   │
│   ├── experiments/           # Study scripts
│   │   ├── run_trial.py        # Run trials, log Δ/S/N
│   │   └── analyze_results.py  # Compute metrics
│   │
│   └── utils/                 # Helper scripts
│       ├── logger.js          # Log trial data
│       └── validator.js        # Validate τ, p, Δ
│
├── data/                      # Trial data (gitignored)
│   ├── trials/                # Raw trial outputs
│   └── aggregated/            # Processed results
│
└── assets/                    # Static files (images, diagrams)
    └── flowcharts/            # Mermaid/SVG diagrams of methodology
```

---

## 🚀 Setup

### Prerequisites
- **Node.js** (v16+) for the chatbot
- **Python 3.8+** for experiments
- **Git** for version control

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/ai-continuity-study.git
   cd ai-continuity-study
   ```

2. Install Node.js dependencies:
   ```bash
   cd scripts/chatbot
   npm install
   ```

3. Install Python dependencies (create a virtual environment recommended):
   ```bash
   cd scripts/experiments
   pip install -r requirements.txt   # (create this file as needed)
   ```

4. Configure the chatbot:
   - Edit `scripts/chatbot/config.json` with your API keys and TTR thresholds.
   - Define personas in `scripts/chatbot/prompts/curated.md` and `baseline.md`.

5. Run a trial:
   ```bash
   python scripts/experiments/run_trial.py
   ```

6. Analyze results:
   ```bash
   python scripts/experiments/analyze_results.py
   ```

---

## 🔮 Future Work

- Expand to multi-model comparisons (different LLMs)
- Automated rater calibration tools
- Interactive dashboard for Δ distributions
- Cross-system Level 3 replication protocols
- Public dataset release of anonymized trial outputs

---

## 📜 License

This project is released under **The Unlicense**. See the [LICENSE](LICENSE) file for details.

You are free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.