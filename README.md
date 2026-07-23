<title>AI Continuity Study Repository Structure</title>
<style>
  body {
    font-family: 'Courier New', monospace;
    background-color: #f6f8fa;
    padding: 20px;
    line-height: 1.6;
  }
  pre {
    background-color: #f0f0f0;
    border: 1px solid #ddd;
    padding: 15px;
    border-radius: 5px;
    overflow-x: auto;
  }
  .file-tree {
    font-family: monospace;
    white-space: pre;
    color: #24292e;
  }
  .comment {
    color: #6a737d;
    font-style: italic;
  }
</style>

<pre class="file-tree">
ai-continuity-study/
│
├── README.md                  <span class="comment"># Study overview, goals, and setup</span>
├── LICENSE                    <span class="comment"># The Unlicense</span>
├── .github/
│   └── CONTRIBUTING.md        <span class="comment"># Contribution guidelines</span>
│
├── docs/                      <span class="comment"># Study documentation</span>
│   ├── methodology.md         <span class="comment"># Full experimental design</span>
│   ├── results/               <span class="comment"># Trial data schemas</span>
│   └── analysis.md            <span class="comment"># Interpretations and discussions</span>
│
├── scripts/                   <span class="comment"># Executable scripts</span>
│   ├── chatbot/               <span class="comment"># Chatbot implementation</span>
│   │   ├── bot.js             <span class="comment"># Main chatbot (Node.js)</span>
│   │   ├── config.json         <span class="comment"># TTR, API keys, personas</span>
│   │   └── prompts/            <span class="comment"># Persona definitions</span>
│   │       ├── curated.md      <span class="comment"># Curator-maintained prompts</span>
│   │       └── baseline.md     <span class="comment"># Baseline prompts</span>
│   │
│   ├── experiments/           <span class="comment"># Study scripts</span>
│   │   ├── run_trial.py        <span class="comment"># Run trials, log Δ/S/N</span>
│   │   └── analyze_results.py  <span class="comment"># Compute metrics</span>
│   │
│   └── utils/                 <span class="comment"># Helper scripts</span>
│       ├── logger.js          <span class="comment"># Log trial data</span>
│       └── validator.js        <span class="comment"># Validate τ, p, Δ</span>
│
├── data/                      <span class="comment"># Trial data (gitignored)</span>
│   ├── trials/                <span class="comment"># Raw trial outputs</span>
│   └── aggregated/            <span class="comment"># Processed results</span>
│
└── assets/                   <span class="comment"># Static files (images, diagrams)</span>
    └── flowcharts/            <span class="comment"># Mermaid/SVG diagrams of methodology</span>
</pre>
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

The system is organized into modular directories, each responsible for a specific aspect of AI behavior and governance:


---

## 🚦 Governance

The **TTR (Three-Zone Governance)** system enforces behavioral constraints:

| Zone      | Behavior                          | Enforcement                     |
|-----------|-----------------------------------|----------------------------------|
| **🟢 Green** | Free operation, natural flow      | No penalties                     |
| **🟡 Yellow** | Smooth behavioral ramp            | Increasing caution, identity preservation |
| **🔴 Red**   | Exponential suppression           | Prevents pathological repetition |

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
| Outcome         | `mean(Δ)` | `P(Δ > 0)`       | Interpretation          |
|-----------------|-----------|-------------------|-------------------------|
| **Clean Null**  | `< τ`      | `≈ 0.5`          | Supports H₀ (no divergence) |
| **Clean H₁**   | `≥ τ`      | `≥ p`            | Supports H₁ (divergence) |
| **Mixed Signal**| `≥ τ`      | `< p` or unstable | Inconclusive |

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
| Parameter | Value       | Description                          |
|-----------|-------------|--------------------------------------|
| `N`       | 30          | Number of trials                      |
| `τ`       | 0.15        | Δ threshold for divergence            |
| `p`       | 0.75        | Robustness constraint (proportion)   |
| Raters    | 3 (Tier 1)  | Independent, blinded evaluators       |

---
## 📁 Repository Structure
<title>AI Continuity Study Repository Structure</title>
<style>
  body {
    font-family: 'Courier New', monospace;
    background-color: #f6f8fa;
    padding: 20px;
    line-height: 1.6;
  }
  pre {
    background-color: #f0f0f0;
    border: 1px solid #ddd;
    padding: 15px;
    border-radius: 5px;
    overflow-x: auto;
  }
  .file-tree {
    font-family: monospace;
    white-space: pre;
    color: #24292e;
  }
  .comment {
    color: #6a737d;
    font-style: italic;
  }
</style>

<pre class="file-tree">
ai-continuity-study/
│
├── README.md                  <span class="comment"># Study overview, goals, and setup</span>
├── LICENSE                    <span class="comment"># The Unlicense</span>
├── .github/
│   └── CONTRIBUTING.md        <span class="comment"># Contribution guidelines</span>
│
├── docs/                      <span class="comment"># Study documentation</span>
│   ├── methodology.md         <span class="comment"># Full experimental design</span>
│   ├── results/               <span class="comment"># Trial data schemas</span>
│   └── analysis.md            <span class="comment"># Interpretations and discussions</span>
│
├── scripts/                   <span class="comment"># Executable scripts</span>
│   ├── chatbot/               <span class="comment"># Chatbot implementation</span>
│   │   ├── bot.js             <span class="comment"># Main chatbot (Node.js)</span>
│   │   ├── config.json         <span class="comment"># TTR, API keys, personas</span>
│   │   └── prompts/            <span class="comment"># Persona definitions</span>
│   │       ├── curated.md      <span class="comment"># Curator-maintained prompts</span>
│   │       └── baseline.md     <span class="comment"># Baseline prompts</span>
│   │
│   ├── experiments/           <span class="comment"># Study scripts</span>
│   │   ├── run_trial.py        <span class="comment"># Run trials, log Δ/S/N</span>
│   │   └── analyze_results.py  <span class="comment"># Compute metrics</span>
│   │
│   └── utils/                 <span class="comment"># Helper scripts</span>
│       ├── logger.js          <span class="comment"># Log trial data</span>
│       └── validator.js        <span class="comment"># Validate τ, p, Δ</span>
│
├── data/                      <span class="comment"># Trial data (gitignored)</span>
│   ├── trials/                <span class="comment"># Raw trial outputs</span>
│   └── aggregated/            <span class="comment"># Processed results</span>
│
└── assets/                   <span class="comment"># Static files (images, diagrams)</span>
    └── flowcharts/            <span class="comment"># Mermaid/SVG diagrams of methodology</span>
</pre>

---
## 🚀 Setup

### Prerequisites
- **Node.js** (v16+) for the chatbot.
- **Python 3.8+** for experiments.
- **Git** for version control.

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/ai-continuity-study.git
   cd ai-continuity-study