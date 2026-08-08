---
title: Quantum Compiler
emoji: ⚛️
colorFrom: indigo
colorTo: blue
sdk: gradio
app_file: app.py
python_version: "3.12"
---

# Quantum Compiler — the quantum brain

A language-driven quantum computing system. Describe your problem in plain English and it
translates it into a real quantum algorithm, runs it on a simulator or IBM hardware, and
returns a verified answer — with an honest assessment of whether quantum was necessary.

**How it works:** the LLM handles intake and phrasing only. All computation is deterministic —
four specialized kernels (K1–K4) build and execute the circuits. Every run produces a
verification certificate and a classical threat-model check.

![Quantum Compiler v2.6 Pipeline](docs/flow-diagram-v2.6.svg)

---

## Quick start (5 minutes)

### 1. Open the folder in VS Code
```
File ▸ Open Folder…  ▸  select the  quantum-brain  folder
```
When VS Code offers the recommended extensions (Python, Pylance, Jupyter, Ruff), accept.

### 2. Create a virtual environment

Press **Ctrl+Shift+P** (**Cmd+Shift+P** on Mac) → `Python: Create Environment` → `Venv` →
pick Python 3.9+. VS Code creates `.venv` and selects it automatically.

Or in the terminal:

| | command |
|---|---|
| **Windows** | `python -m venv .venv` then `.venv\Scripts\activate` |
| **macOS / Linux** | `python3 -m venv .venv` then `source .venv/bin/activate` |

### 3. Install dependencies
```bash
pip install -r requirements.txt
```
Takes 2–3 minutes. *(Everything runs on CPU — no GPU, no quantum hardware needed.)*

### 4. Check it works
```bash
python run.py --check
```
You should see `OK` for Python, qiskit, qiskit_aer, gradio, and a smoke test confirming the
quantum pipeline runs.

### 5. Launch the Studio
```bash
python run.py
```
Your browser opens at **http://127.0.0.1:7860**. Type a problem, or click one of the examples.

**In VS Code you can skip the terminal entirely:** open the *Run and Debug* panel (Ctrl+Shift+D)
and pick **▶ Launch Studio (simulator)**.

---

## Try these first

| Type this | What happens |
|---|---|
| `Find the ground state energy of the H2 molecule` | VQE runs, returns −1.137 Ha, verified against exact diagonalization |
| `Grover search for the marked state 101` | Builds a 3-qubit oracle, returns `101` at ~95% of shots |
| `simulate a 4-spin Heisenberg chain` | Trotter evolution, matches exact physics to ~1e-16 |
| `optimize my portfolio of 6 assets picking 3` | QUBO → QAOA, matched against the exact optimum |
| `find one marked item among a billion possibilities` | Infers 58 qubits, then honestly refuses to overclaim |
| `what is entanglement` | Explains, clearly marked as an explanation not a computation |

Then open the **📡 NISQ preview** tab: *Preview on noisy hardware* shows what a real IBM device
would return for your circuit, and *Validate by noise stability* tests whether your answer
survives a deliberate noise sweep — the method IBM & Algorithmiq used (30 Jul 2026) to
establish trust when no classical check exists. Both are free and use no quota.

---

## Command reference

```bash
python run.py                  # launch the Studio (simulator)
python run.py --hardware       # launch with REAL IBM hardware pre-selected
python run.py --port 8080      # different port
python run.py --share          # temporary public link (for demos)
python run.py --check          # environment health check
python run.py --ask "..."      # answer one question in the terminal, no UI

python run_local.py            # quick local launcher (share=False)

python run_tests.py            # run all 26 test suites
python run_tests.py ui noise   # run specific suites
```

---

## Optional: real IBM quantum hardware

The simulator is free, instant, unlimited, and needs no account — **you never have to do
this**. But to run on a real QPU:

1. Make a free account at <https://quantum.cloud.ibm.com> and copy your API token.
2. Copy `.env.example` to `.env` and paste it in:
   ```
   IBM_QUANTUM_TOKEN=your_token_here
   ```
3. Launch with `python run.py --hardware`, or tick the ⚛️ checkbox in the UI.

The `.env` file is loaded automatically on startup — no manual export needed.

The free Open Plan gives ~10 minutes of QPU time per 28 days. The system is built to respect
that: the optimizer loop always runs on the simulator, and only a single mitigated evaluation
is sent to hardware.

`.env` is git-ignored. **Never commit your token.**

### Optional: nicer phrasing
Add a `GEMINI_API_KEY` to `.env` for warmer wording. Nothing quantum depends on it — the LLM
never computes answers, so results are identical with or without it.

---

## Project layout

```
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

## Troubleshooting

**`ModuleNotFoundError`** — the virtual environment isn't active or deps aren't installed.
Run `python run.py --check`; it names exactly what's missing.

**Wrong Python selected in VS Code** — Ctrl+Shift+P → `Python: Select Interpreter` → choose
the one inside `.venv`.

**Port 7860 already in use** — `python run.py --port 8080`.

**Circuit images don't render** — `pip install matplotlib pylatexenc`. The system falls back
to text diagrams automatically.

**Gradio version errors** — components are constructed through a signature-filtering shim, so
any Gradio ≥4.44 (including v5 and v6) should work. If something still breaks, report the
traceback.

**"Not enough quota" from IBM** — the free tier is ~10 min per 28 days. Use the simulator, or
the NISQ preview tab to see what hardware *would* return for free.

---

## What makes this different from asking Google or ChatGPT

Google **retrieves** an answer someone already published. ChatGPT **recalls** one from
training. Quantum Compiler **computes** a fresh one by running a quantum circuit and decoding
the measurement — so it can answer an instance nobody has ever solved, and it tells you
honestly when a classical computer would have been enough.
