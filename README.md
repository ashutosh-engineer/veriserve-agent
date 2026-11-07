# veriserve-agent

VeriCore: Verifiable Self-Serving Agents via Unsat-Core Constraint Pruning


> **Research Implementation (Work in Progress)**  
> *Neuro-Symbolic Control & Formal SMT Verification for Resource-Constrained Autonomous LLM Agents*

## Overview
Standard Large Language Model (LLM) agents rely on probabilistic prompting to obey safety, latency, and budget constraints—frequently failing on long-horizon tasks. **VeriServe** decouples semantic planning (LLM) from formal verification (Z3 SMT Solver).

### Key Contributions
1. **Formal SMT Constraint Gate:** Verifies candidate agent plans against hard resource (`cost`, `latency`) and safety (`PII`, `DB snapshot`) predicates prior to execution.
2. **Minimal Unsat-Core Diagnostics:** Extracts the exact conflicting constraint subset ($\mathcal{C}_{\text{unsat}}$) when a plan fails verification.
3. **Self-Serving Action-Space Pruning:** Automatically down-shifts reasoning models and injects mandatory safety preconditions without burning extra LLM retry tokens.

## Project Structure
```text
├── README.md
├── requirements.txt
├── src/
│   ├── constraint_gate.py    # Z3 SMT Verifier & Unsat-Core Extractor
│   ├── router.py             # Self-Serving Model & Resource Arbitrator
│   └── agent_loop.py         # Closed-Loop Neuro-Symbolic Planner
└── benchmarks/               # Evaluation task suites