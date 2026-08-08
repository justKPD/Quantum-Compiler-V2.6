
# Quantum Compiler v2.6.0 with Agentic Neuro-Symbolic Pipeline — The Quantum Brain 🧠⚛️

> **The first end-to-end interface bridging natural language directly to quantum computation and back.**

Describe your problem in plain English. The Quantum Brain translates it into a real quantum algorithm, runs it on a simulator or physical IBM Quantum hardware, mathematically verifies the result, and translates the noisy quantum measurements back into a human answer.

**Live preview** [https://quantum-brain-studio.onrender.com](https://quantum-brain-studio.onrender.com)

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
<svg viewBox="0 0 1050 1360" xmlns="http://www.w3.org/2000/svg" width="1050" height="1360">
  <defs>
    <filter id="shadow" x="-4%" y="-4%" width="108%" height="112%">
      <feDropShadow dx="0" dy="2" stdDeviation="4" flood-color="#00000018"/>
    </filter>
    <marker id="arr" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 10 5 L 0 10 z" fill="#94a3b8"/></marker>
    <marker id="arr-t" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 10 5 L 0 10 z" fill="#0E7C7B"/></marker>
    <marker id="arr-a" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 10 5 L 0 10 z" fill="#B5761B"/></marker>
    <marker id="arr-r" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path d="M 0 0 L 10 5 L 0 10 z" fill="#B3413B"/></marker>
  </defs>
  <rect width="1050" height="1360" fill="#f8fafc"/>
  <text x="525" y="32" text-anchor="middle" font-size="20" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Quantum-Brain v2.6 — plain English in, verified quantum answer out</text>
  <text x="525" y="50" text-anchor="middle" font-size="12" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">The language model only interviews and words the reply — it never writes the circuit</text>

  <!-- Step 1 -->
  <rect x="340" y="68" width="320" height="48" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="90" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">1 · you type a problem in plain English</text>
  <text x="500" y="106" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">"ground state of H2" · "search a billion items"</text>
  <line x1="500" y1="116" x2="500" y2="134" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 2 -->
  <rect x="340" y="136" width="320" height="48" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="158" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">2 · interview + planner</text>
  <text x="500" y="174" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">asks only what's missing · splits compound tasks</text>
  <rect x="700" y="138" width="190" height="42" rx="7" fill="#F5F8FA" stroke="#DCE5EC" stroke-dasharray="4,3"/>
  <text x="795" y="156" text-anchor="middle" font-size="10" font-weight="600" fill="#5B4B8A" font-family="Segoe UI, system-ui, sans-serif">compound query planner</text>
  <text x="795" y="170" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">splits "do X then Y" into subtasks</text>
  <line x1="660" y1="160" x2="700" y2="160" stroke="#94a3b8" stroke-width="1" stroke-dasharray="3,3" marker-end="url(#arr)"/>
  <line x1="500" y1="184" x2="500" y2="202" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 3 -->
  <rect x="340" y="204" width="320" height="48" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="226" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">3 · translate → pick a kernel + infer size</text>
  <text x="500" y="242" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">words become structure, then qubits</text>
  <rect x="700" y="200" width="190" height="52" rx="7" fill="#F0F7F5" stroke="#B4D8D2"/>
  <text x="795" y="218" text-anchor="middle" font-size="10" font-weight="600" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">advantage router</text>
  <text x="795" y="232" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">quantum-vs-classical verdict</text>
  <text x="795" y="244" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">+ resource estimation</text>
  <line x1="660" y1="228" x2="700" y2="228" stroke="#0E7C7B" stroke-width="1" stroke-dasharray="3,3" marker-end="url(#arr-t)"/>
  <line x1="500" y1="252" x2="500" y2="272" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 4: Kernels -->
  <rect x="160" y="274" width="680" height="220" rx="10" fill="#EBF3FA" stroke="#1B5E9E" stroke-width="1.5" filter="url(#shadow)"/>
  <text x="500" y="296" text-anchor="middle" font-size="13" font-weight="700" fill="#1B5E9E" font-family="Segoe UI, system-ui, sans-serif">4 · deterministic kernels build the real circuit</text>

  <!-- K1 -->
  <rect x="175" y="308" width="155" height="175" rx="8" fill="#fff" stroke="#1B5E9E" stroke-width="1"/>
  <text x="252" y="326" text-anchor="middle" font-size="11" font-weight="700" fill="#1B5E9E" font-family="Segoe UI, system-ui, sans-serif">K1 Hamiltonian</text>
  <line x1="185" y1="332" x2="320" y2="332" stroke="#DCE5EC"/>
  <text x="185" y="348" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">VQE ground state</text>
  <text x="185" y="362" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">VQD excited states</text>
  <text x="185" y="376" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">QPE phase estimation</text>
  <text x="185" y="390" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Trotter time evolution</text>
  <text x="185" y="404" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">Richardson extrapolation</text>
  <text x="185" y="418" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">Multi-product formula</text>
  <text x="185" y="436" font-size="8.5" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">Families: H2, LiH, Heisenberg,</text>
  <text x="185" y="448" font-size="8.5" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">TFIM, Fermi-Hubbard</text>
  <text x="185" y="468" font-size="8" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">structure: native (beyond classical)</text>

  <!-- K2 -->
  <rect x="345" y="308" width="145" height="175" rx="8" fill="#fff" stroke="#1B5E9E" stroke-width="1"/>
  <text x="417" y="326" text-anchor="middle" font-size="11" font-weight="700" fill="#1B5E9E" font-family="Segoe UI, system-ui, sans-serif">K2 Oracle</text>
  <line x1="355" y1="332" x2="480" y2="332" stroke="#DCE5EC"/>
  <text x="355" y="348" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Grover search</text>
  <text x="355" y="362" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Deutsch-Jozsa</text>
  <text x="355" y="382" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">amplitude amplification</text>
  <text x="355" y="402" font-size="8.5" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">optimal iteration count</text>
  <text x="355" y="416" font-size="8.5" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">oracle: phase flip</text>
  <text x="355" y="436" font-size="8" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">structure: sqrt(N) speedup</text>

  <!-- K3 -->
  <rect x="505" y="308" width="155" height="175" rx="8" fill="#fff" stroke="#1B5E9E" stroke-width="1"/>
  <text x="582" y="326" text-anchor="middle" font-size="11" font-weight="700" fill="#1B5E9E" font-family="Segoe UI, system-ui, sans-serif">K3 Unitary</text>
  <line x1="515" y1="332" x2="650" y2="332" stroke="#DCE5EC"/>
  <text x="515" y="348" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Unitary synthesis (KAK)</text>
  <text x="515" y="362" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">State prep: GHZ, Bell, W</text>
  <text x="515" y="376" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">QFT</text>
  <text x="515" y="396" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">Solovay-Kitaev discrete</text>
  <text x="515" y="410" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">Shannon decomposition</text>
  <text x="515" y="436" font-size="8" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">structure: compile only</text>

  <!-- K4 -->
  <rect x="675" y="308" width="155" height="175" rx="8" fill="#fff" stroke="#1B5E9E" stroke-width="1"/>
  <text x="752" y="326" text-anchor="middle" font-size="11" font-weight="700" fill="#1B5E9E" font-family="Segoe UI, system-ui, sans-serif">K4 Optimization</text>
  <line x1="685" y1="332" x2="820" y2="332" stroke="#DCE5EC"/>
  <text x="685" y="348" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">QAOA</text>
  <text x="685" y="362" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Max-Cut</text>
  <text x="685" y="376" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Task scheduling</text>
  <text x="685" y="390" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">Portfolio (Markowitz)</text>
  <text x="685" y="410" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">QUBO → Ising mapping</text>
  <text x="685" y="424" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">brute-force cross-check</text>
  <text x="685" y="444" font-size="8" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">structure: heuristic</text>

  <line x1="500" y1="494" x2="500" y2="512" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 5 -->
  <rect x="340" y="514" width="320" height="44" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="534" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">5 · show the circuit + QASM</text>
  <text x="500" y="550" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">the actual gates built for your query</text>
  <line x1="500" y1="558" x2="500" y2="576" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 6 -->
  <rect x="340" y="578" width="320" height="48" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="598" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">6 · run it: simulator or real IBM QPU</text>
  <text x="500" y="614" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">free instant sim · one checkbox for hardware</text>
  <rect x="700" y="580" width="190" height="42" rx="7" fill="#FFF8E1" stroke="#B5761B" stroke-dasharray="4,3"/>
  <text x="795" y="598" text-anchor="middle" font-size="10" font-weight="600" fill="#B5761B" font-family="Segoe UI, system-ui, sans-serif">checkbox = sole arbiter</text>
  <text x="795" y="612" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">ON = real QPU · OFF = simulator</text>
  <line x1="660" y1="601" x2="700" y2="601" stroke="#B5761B" stroke-width="1" stroke-dasharray="3,3" marker-end="url(#arr-a)"/>

  <!-- Error mitigation — pushed down to y=640 -->
  <rect x="700" y="640" width="190" height="50" rx="7" fill="#F5F8FA" stroke="#DCE5EC"/>
  <text x="795" y="658" text-anchor="middle" font-size="10" font-weight="600" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">error mitigation (QPU)</text>
  <text x="795" y="672" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">ZNE · TREX · gate twirling · DD</text>
  <text x="795" y="684" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">hybrid: sim opt → 1 QPU eval</text>
  <line x1="700" y1="640" x2="700" y2="630" stroke="#DCE5EC" stroke-width="1" stroke-dasharray="3,3"/>

  <line x1="500" y1="626" x2="500" y2="644" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 7 -->
  <rect x="340" y="646" width="320" height="44" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="666" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">7 · measurement histogram</text>
  <text x="500" y="682" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">many shots → a distribution, not one answer</text>

  <!-- NISQ preview — pushed down to y=706, clear of error mitigation -->
  <rect x="700" y="706" width="190" height="44" rx="7" fill="#F0F7F5" stroke="#B4D8D2"/>
  <text x="795" y="724" text-anchor="middle" font-size="10" font-weight="600" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">NISQ preview</text>
  <text x="795" y="738" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">what real IBM device would return</text>
  <text x="795" y="748" text-anchor="middle" font-size="8" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">free · no quota</text>
  <line x1="660" y1="668" x2="700" y2="728" stroke="#0E7C7B" stroke-width="1" stroke-dasharray="3,3" marker-end="url(#arr-t)"/>

  <line x1="500" y1="690" x2="500" y2="708" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 8 -->
  <rect x="340" y="710" width="320" height="44" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="730" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">8 · decode → plain-words answer</text>
  <text x="500" y="746" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">the reply comes from the measurement</text>
  <line x1="500" y1="754" x2="500" y2="772" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>

  <!-- Step 9 -->
  <rect x="340" y="774" width="320" height="48" rx="9" fill="#fff" stroke="#DCE5EC" filter="url(#shadow)"/>
  <text x="500" y="794" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">9 · verify + honest verdict</text>
  <text x="500" y="810" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">certificate · says when classical is enough</text>

  <!-- Verification stack — pushed down to y=780 -->
  <rect x="700" y="780" width="210" height="82" rx="7" fill="#F0F7F5" stroke="#B4D8D2"/>
  <text x="805" y="798" text-anchor="middle" font-size="10" font-weight="600" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">verification stack</text>
  <text x="805" y="812" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">mirror circuit / Loschmidt echo</text>
  <text x="805" y="826" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">MPS/TEBD classical referee</text>
  <text x="805" y="840" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">conserved quantity check</text>
  <text x="805" y="854" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">noise stability (IBM 2026)</text>
  <line x1="660" y1="810" x2="700" y2="821" stroke="#0E7C7B" stroke-width="1" stroke-dasharray="3,3" marker-end="url(#arr-t)"/>

  <!-- Self-correction — path shifted far left to avoid all boxes -->
  <path d="M 340 800 L 60 800 L 60 308 L 175 308" fill="none" stroke="#B3413B" stroke-width="1.5" stroke-dasharray="5,4" marker-end="url(#arr-r)"/>
  <rect x="10" y="545" width="80" height="42" rx="6" fill="#FFF0EF" stroke="#B3413B" stroke-dasharray="3,3"/>
  <text x="50" y="562" text-anchor="middle" font-size="9" font-weight="600" fill="#B3413B" font-family="Segoe UI, system-ui, sans-serif">self-</text>
  <text x="50" y="574" text-anchor="middle" font-size="9" font-weight="600" fill="#B3413B" font-family="Segoe UI, system-ui, sans-serif">correction</text>
  <text x="50" y="584" text-anchor="middle" font-size="8" fill="#B3413B" font-family="Segoe UI, system-ui, sans-serif">re-runs kernel</text>

  <!-- Honesty + Reach + Flagship -->
  <rect x="160" y="900" width="220" height="50" rx="9" fill="#F5F0E3" stroke="#B5761B" stroke-width="1" filter="url(#shadow)"/>
  <text x="270" y="922" text-anchor="middle" font-size="12" font-weight="700" fill="#B5761B" font-family="Segoe UI, system-ui, sans-serif">honesty layers</text>
  <text x="270" y="938" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">threat model · MPS referee · frontier</text>
  <rect x="415" y="900" width="220" height="50" rx="9" fill="#E8F5ED" stroke="#1D7A46" stroke-width="1" filter="url(#shadow)"/>
  <text x="525" y="922" text-anchor="middle" font-size="12" font-weight="700" fill="#1D7A46" font-family="Segoe UI, system-ui, sans-serif">reach</text>
  <text x="525" y="938" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">H2 · LiH · Hubbard · MaxCut · portfolio</text>
  <rect x="670" y="900" width="220" height="50" rx="9" fill="#F0EBF8" stroke="#5B4B8A" stroke-width="1" filter="url(#shadow)"/>
  <text x="780" y="922" text-anchor="middle" font-size="12" font-weight="700" fill="#5B4B8A" font-family="Segoe UI, system-ui, sans-serif">flagship experiments</text>
  <text x="780" y="938" text-anchor="middle" font-size="10" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">Heisenberg quench · Kicked-Ising Floquet</text>

  <!-- Classical threat model -->
  <rect x="130" y="970" width="760" height="90" rx="10" fill="#FFF0EF" stroke="#B3413B" stroke-width="1" filter="url(#shadow)"/>
  <text x="510" y="992" text-anchor="middle" font-size="12" font-weight="700" fill="#B3413B" font-family="Segoe UI, system-ui, sans-serif">classical threat model — 7 dequantization methods checked after every run</text>
  <text x="160" y="1014" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">1. Belief propagation</text>
  <text x="160" y="1028" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">2. gPEPS simple update</text>
  <text x="160" y="1042" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">3. MPS/TEBD</text>
  <text x="160" y="1052" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">4. isoTNS</text>
  <text x="400" y="1014" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">5. MPO Heisenberg picture</text>
  <text x="400" y="1028" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">6. Sparse Pauli dynamics</text>
  <text x="400" y="1042" font-size="9.5" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">7. Exact statevector</text>
  <text x="660" y="1014" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">Every advantage claim since 2023</text>
  <text x="660" y="1028" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">was overturned by a classical method.</text>
  <text x="660" y="1042" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">The system refuses to overclaim.</text>

  <!-- v2.6 additions -->
  <rect x="130" y="1080" width="760" height="100" rx="10" fill="#F8FAFC" stroke="#DCE5EC" stroke-width="1"/>
  <text x="510" y="1102" text-anchor="middle" font-size="13" font-weight="700" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">v2.6 additions</text>
  <rect x="150" y="1112" width="220" height="55" rx="7" fill="#fff" stroke="#DCE5EC"/>
  <text x="260" y="1132" text-anchor="middle" font-size="10" font-weight="700" fill="#1B5E9E" font-family="Segoe UI, system-ui, sans-serif">i18n — EN · ES · HI · FR</text>
  <text x="260" y="1148" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">all UI text translates</text>
  <text x="260" y="1160" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">via dropdown selector</text>
  <rect x="395" y="1112" width="220" height="55" rx="7" fill="#fff" stroke="#DCE5EC"/>
  <text x="505" y="1132" text-anchor="middle" font-size="10" font-weight="700" fill="#0E7C7B" font-family="Segoe UI, system-ui, sans-serif">.env auto-load</text>
  <text x="505" y="1148" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">tokens loaded on startup</text>
  <text x="505" y="1160" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">all entry points covered</text>
  <rect x="640" y="1112" width="230" height="55" rx="7" fill="#fff" stroke="#DCE5EC"/>
  <text x="755" y="1132" text-anchor="middle" font-size="10" font-weight="700" fill="#B3413B" font-family="Segoe UI, system-ui, sans-serif">checkbox = sole arbiter</text>
  <text x="755" y="1148" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">no auto-override from router</text>
  <text x="755" y="1160" text-anchor="middle" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">compound subtasks respect it</text>

  <!-- Bottom stats -->
  <rect x="200" y="1200" width="180" height="30" rx="7" fill="#F5F8FA" stroke="#DCE5EC"/>
  <text x="290" y="1220" text-anchor="middle" font-size="10" font-weight="600" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">16 algorithms · 26 suites</text>
  <rect x="435" y="1200" width="180" height="30" rx="7" fill="#F5F8FA" stroke="#DCE5EC"/>
  <text x="525" y="1220" text-anchor="middle" font-size="10" font-weight="600" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">4 kernels · 9 verification</text>
  <rect x="670" y="1200" width="180" height="30" rx="7" fill="#F5F8FA" stroke="#DCE5EC"/>
  <text x="760" y="1220" text-anchor="middle" font-size="10" font-weight="600" fill="#0B2239" font-family="Segoe UI, system-ui, sans-serif">real IBM QPU + simulator</text>

  <!-- Legend -->
  <rect x="220" y="1245" width="590" height="35" rx="7" fill="#fff" stroke="#DCE5EC"/>
  <circle cx="250" cy="1262" r="5" fill="#0E7C7B" opacity="0.3"/>
  <text x="262" y="1266" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">new in v2.6</text>
  <line x1="340" y1="1262" x2="365" y2="1262" stroke="#94a3b8" stroke-width="1.5" marker-end="url(#arr)"/>
  <text x="375" y="1266" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">main flow</text>
  <line x1="440" y1="1262" x2="465" y2="1262" stroke="#94a3b8" stroke-width="1" stroke-dasharray="3,3" marker-end="url(#arr)"/>
  <text x="475" y="1266" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">side panel</text>
  <line x1="545" y1="1262" x2="570" y2="1262" stroke="#B3413B" stroke-width="1.5" stroke-dasharray="5,4" marker-end="url(#arr-r)"/>
  <text x="580" y="1266" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">feedback loop</text>
  <rect x="680" y="1255" width="10" height="10" rx="2" fill="#fff" stroke="#B3413B" stroke-width="1"/>
  <text x="696" y="1266" font-size="9" fill="#7C8B9A" font-family="Segoe UI, system-ui, sans-serif">threat model</text>
</svg>

<img width="1050" height="1360" alt="flow-diagram-v2 6" src="https://github.com/user-attachments/assets/c329778b-fbe6-47bb-a3c0-adb6a3ec04ab" />


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
