
# Quantum Compiler v2.6.0 — The Quantum Brain 🧠⚛️

> **The first end-to-end interface bridging natural language directly to quantum computation and back.**

Describe your problem in plain English. The Quantum Brain translates it into a real quantum algorithm, runs it on a simulator or physical IBM Quantum hardware, mathematically verifies the result, and translates the noisy quantum measurements back into a human answer.

**Live Demo:** [https://quantum-brain-studio.onrender.com](https://quantum-brain-studio.onrender.com)

![Quantum Compiler UI](UI_Screenshot.png) 
*(Note: Upload your downloaded image to the GitHub repo and name it `UI_Screenshot.png` for this to show up perfectly)*

---

### 🌍 What makes this a World-First?
Standard AI tools (like ChatGPT) simply *recall* an answer from training data, or write Python code that the user has to run. 

Quantum Compiler v2.6.0 is fundamentally different. It is an **Agentic Neuro-Symbolic Pipeline**:
1. **Natural Language Intake:** You ask a question (e.g., "How do we cure cancer?" or "Optimize this spacecraft routing network").
2. **Deterministic Math Engine:** The AI extracts variables and feeds them to a strict Python math engine (no LLM math hallucination). 
3. **Quantum Execution:** The system builds a real Qiskit circuit and executes it on IBM Quantum hardware (or a statevector simulator).
4. **Honesty & Verification Layers:** The raw, noisy quantum data is validated mathematically. If the quantum hardware decoheres and returns garbage, the AI tells you—rather than hallucinating a perfect answer.

We are entering the NISQ (Noisy Intermediate-Scale Quantum) era. This project proves that quantum hardware can be made accessible, trustworthy, and conversational for everyone around the world , making talking to quantum easy accessible and available for everyone.     

---

### ⚛️ System Architecture & Pipeline

The core 9-step execution pipeline is wrapped in rigorous pre-processing, routing, and post-execution validation layers designed to eliminate AI hallucination and detect hardware noise.

flow-diagram-v2.6.svg

### 🏗️ Engine Layout & Module Architecture

The Quantum Brain is powered by a massive 48-module proprietary engine. While the source code remains private, the architectural layout below illustrates the depth and rigor of the system's deterministic kernels, honesty layers, and verification pipelines.

```text
quantum-brain/
├── run.py                  ← launcher (start here)
├── run_local.py            ← quick local launcher (no share link)
├── run_tests.py            ← runs all 26 test suites
├── app.py                  ← Gradio entry point for Spaces
├── setup.py                ← package metadata
├── pyproject.toml          ← build config
├── requirements.txt
├── requirements-dev.txt    ← dev/test dependencies
├── .env.example            ← copy to .env for API keys
├── .vscode/                ← launch configs, tasks, settings
├── deploy/                 ← Hugging Face Spaces hosting
├── examples/               ← notebooks & demos
│
├── qcompiler/              ← the package (48 modules)
│   │
│   ├── app.py              Studio engine + Gradio UI
│   ├── ui.py               UI component library (HTML/CSS renderers)
│   ├── chat.py             standalone chat-mode interface
│   │
│   ├── router.py           chooses which kernel your problem needs
│   ├── intake_agent.py     the interview — extracts parameters from your words
│   ├── interview.py        slot questions, choice explanations, guides
│   ├── planner.py          compound-query decomposition
│   ├── triage.py           routing heuristics
│   │
│   ├── hamiltonian.py      K1 — VQE ground states + Trotter dynamics
│   ├── general.py          K2 — Grover search  (+ kernel dispatch)
│   ├── unitary.py          K3 — state/unitary synthesis
│   ├── modeler.py          K4 — QUBO models (scheduling, Max-Cut, portfolio)
│   │
│   ├── orchestrator.py     grand-challenge decomposition + challenge solver
│   ├── advantage_router.py honest quantum-vs-classical verdict
│   ├── backends.py         simulator vs QPU backend selection
│   ├── resources.py        qubit/gate budget estimation
│   │
│   ├── hardware.py         real IBM execution + error mitigation
│   ├── noise.py            NISQ preview — device noise, free
│   ├── calibration.py      live IBM device calibration data
│   ├── flagship.py         large-circuit experiments (dry-run by default)
│   │
│   ├── verify.py           mirror circuits, MPS/TEBD referee
│   ├── verification.py     per-run confidence certificates
│   ├── self_correct.py     certificate feeds back into re-synthesis
│   ├── validator.py        output sanity checks
│   │
│   ├── threat_model.py     which classical method would dequantize this
│   ├── knowledge.py        quantum-knowledge RAG corpus
│   ├── librarian.py        published-fact lookup
│   │
│   ├── llm.py              LLM client (Gemini, OpenRouter)
│   ├── humanize.py         answer templates + LLM phrasing
│   ├── viz.py              circuit visualization (draw, QASM, PNG)
│   │
│   ├── kernels.py          KernelType enum
│   ├── ir.py               intermediate representation
│   ├── units.py            physical-unit conversions
│   ├── history.py          run history tracking
│   ├── theme.py            UI theme tokens
│   ├── benchmark.py        performance benchmarks
│   ├── classifier.py       problem classifier
│   ├── evaluate.py         evaluation helpers
│   ├── evolution.py        evolution helpers
│   ├── generator.py        circuit generators
│   ├── ising.py            Ising model utilities
│   ├── opt_pipeline.py     optimization pipeline
│   ├── pipeline.py         shared pipeline utilities
│   ├── qubo.py             QUBO model helpers
│   └── __init__.py         package exports
│
├── tests/                  ← 26 suites, 27 test files
└── deploy/                 ← Hugging Face Spaces hosting
```

---

### 🔒 Proprietary Codebase Notice

The source code, math engine, and deterministic kernels for Quantum Compiler v2.6.0 are strictly private and closed-source. 

This repository serves as the official public documentation, architecture showcase, and live demo portal for the project. 

---

### 📜 License

Copyright © 2026 Drona K P. All rights reserved.

No permission is granted to use, copy, modify, distribute, sublicense, sell, publish, or reproduce this software or any portion of it, whether for commercial, non-commercial, private, or public use, without prior written permission from the copyright holder.

Unauthorized use of this software may result in severe civil and criminal penalties, and will be prosecuted to the maximum extent possible under law.

For licensing inquiries or collaboration requests, please contact the author.
```
