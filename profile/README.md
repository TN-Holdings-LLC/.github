# TN Holdings LLC

**Advancing the "R=0" Frontier in Quantum Control and Systems Engineering.**

TN Holdings LLC is a specialized research and holding entity focused on deterministic system architectures. Our core mission is to eliminate computational friction (Resistance → 0) through geometric and manifold-aware methodologies.

![PSF-Zero vs. Qiskit at scale](https://github.com/TN-Holdings-LLC/psf-zero/blob/main/docs/Figure_1.png)

![PSF-Zero vs Qiskit at the coupling-map cliff: compile time (log scale) and two-qubit gate count, 6x7 and 8x8 grids](docs/Figure_2.png)

### Verified Results — PSF-Zero

| Comparison | Condition | Result |
| :--- | :---: | :---: |
| vs. Qiskit (`optimization_level=3`) | General dense circuits, 15–1000 qubits | **2.5–5x faster** |
| vs. TKET (`FullPeepholeOptimise`) | Same circuit family, 10–160 qubits | **150–270x faster** |
| vs. Qiskit (`optimization_level=3`) | Coupling map nearly/fully saturated, 42–64 qubits | **279–544x faster** |
| vs. Qiskit (`optimization_level=3`), real IBM hardware | 15 qubits, 10 job submissions | Fidelity statistically on par; **14–16x faster compile** |
| Output determinism | 300 trials, identical input | **Zero variance** — always the same circuit |

<sub>Figures are medians/ranges across the conditions in each row, not single best-case
runs, and are backed by raw data and reproducible scripts in the
[psf-zero repository](https://github.com/TN-Holdings-LLC/psf-zero). Output gate-count
parity depends on matching `entangling_basis` to the target hardware; full conditions
and caveats (including the depth trade-off at saturated coupling maps) are documented
there.</sub>

### Core Projects

- **[PSF-Zero](https://github.com/TN-Holdings-LLC/psf-zero)** — Deterministic two-qubit
  gate synthesis for Qiskit via closed-form (Cartan/KAK) decomposition. Benchmarks and
  methodology above are drawn from this project's own published, reproducible record.
- **R0-GPCLayer** — Geometric preconditioning for classical neural networks. *Early
  stage; no published benchmarks yet.*

### Vision

From quantum manifolds to classical AI, we aim to provide a verifiable, frictionless
foundation for next-generation computation — grounded in reproducible measurement, not
projection.

### Contact

contact.love.os.architect@proton.me
