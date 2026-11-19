# TN Holdings LLC

**Quantum compilation by formula, and a self-checking layer that runs users' circuits on IBM devices without the
calibration map.**

We build in the open and test everything the same way: predictions are locked in git before a run, losses are
published next to wins, and every result is given twice, as the benchmark custom would quote it and as someone
running it on a device would see it.

## Projects

- **[PSF-Zero](https://github.com/TN-Holdings-LLC/psf-zero)**, a Qiskit-compatible compiler that builds circuits by
  formula, with no search: chains, rings and lattices that embed in the device, and the device's native fractional
  gates. Every other circuit is refused with a reason. `compile_template()` builds once and rebinds angles in about
  a millisecond, for training loops.
- **[psf-os](https://github.com/TN-Holdings-LLC/psf-os)**, a self-checking layer between a user's circuit and an IBM
  heavy-hex device: it places the circuit by formula, adds checks made of the user's own circuit to the same job
  (floor, mirror, ring sentinel), keeps a list of what it found dead, and returns an answer card. It reads the
  coupling graph and the failed elements, never a calibration quality number. Since 0.2, real-time control: circuits
  that measure in the middle and act on the result while they run, each with its uncontrolled twin in the same job, and
  a loop that diagnoses the device and picks the next round's circuit unattended. *Release 0.2.0 (2026-11-19); DOI
  [10.5281/zenodo.24367846](https://doi.org/10.5281/zenodo.24367846) (all releases:
  [10.5281/zenodo.24211404](https://doi.org/10.5281/zenodo.24211404)).*
- **[psf-os-lab-notebook](https://github.com/TN-Holdings-LLC/psf-os-lab-notebook)**, the declared device tests behind
  the papers: each declared before its calibration was fetched, answers sealed until the verdicts, raw counts
  committed, every result re-scorable without IBM. It also keeps the original task-oriented compiler benchmark.
- **[readable-depth](https://github.com/TN-Holdings-LLC/readable-depth)**, how deep a circuit stays readable on a
  raw device, per problem family: the definition, a small scorer, and the boundary table built from the notebook's
  records.

## Quantum AI: same money, which model? (pre-registered, scored)

6 qubits, 8 layers, a classifier trained with SPSA; Qiskit level 2 against PSF-Zero's template. **Simulation with a
device noise model (FakeFez); nothing here ran on a device.**

| run | what the benchmark headline says | what a user should also know |
| :--- | :--- | :--- |
| Budget: 2 minutes of QPU ($192), 1,000 seeds | PSF-Zero's model is more accurate at the budget: 0.533 against 0.494, better in 624 of 1,000 seeds | at this budget both models are weak: classical models reach 0.73-0.77 |
| Reach: 1,000 iterations, 200 seeds | PSF-Zero reaches 0.70 accuracy in 300 iterations against 400, for $1,133 against $1,549 | the gain is in cost and speed; the end points are close (0.724 against 0.704) |
| Standard 2: 200 seeds, SPSA tuned so both models learn | PSF-Zero's signal (margin) is 1.32 x larger | accuracy did not differ: 0.702 against 0.701; the primary prediction was refuted |

Full records: [psf-os-lab-notebook `results/`](https://github.com/TN-Holdings-LLC/psf-os-lab-notebook/tree/main/results).

## Compilation: where PSF-Zero wins, and where it does not (real IBM devices)

| | result |
| :--- | :--- |
| Ising chains built by formula | PSF-Zero's side won 19 of 23 pairs on three devices, fidelity ratio 1.21 (geometric mean; worst 0.94) |
| Time-aware gate order | fidelity 1.17-1.51 x higher, 8 of 8, in two pre-registered tests on two devices |
| QAOA and Barabasi-Albert graphs (placement decides) | **lost**: 9 of 25 pairs, ratio 0.78; this family is left to others, with our losing data published |
| General circuits (880 Benchpress tests) | about level with Qiskit level 2 in two-qubit gates (1.046 x), and slower |
| Two-qubit synthesis, `compile()` (release 2026-10-14.1) | 2.5-5 x faster than Qiskit level 3 on two-qubit-block circuits; on 10 jobs on two IBM devices, the same fidelity with 14-16 x shorter compile time |

Details, conditions and every losing case: [psf-zero README](https://github.com/TN-Holdings-LLC/psf-zero) and its
`docs/findings/`.

## Papers

All preprints on Zenodo; records, declarations and raw counts in [psf-os-lab-notebook](https://github.com/TN-Holdings-LLC/psf-os-lab-notebook).

1. **Ordering Sensitivity in Subgraph-Isomorphism Layout Search** (VF2 cliff): [10.5281/zenodo.22977930](https://doi.org/10.5281/zenodo.22977930)
2. **PSF-Zero: An Analytic Two-Qubit Gate Synthesizer Combined with a Verified, Ordering-Aware Layout Search**: [10.5281/zenodo.22978090](https://doi.org/10.5281/zenodo.22978090)
3. **When a Quantum Compiler Looks Like a Better Learner: Confounds in Quantum Machine Learning Comparisons** (v1.3, 2026-10-31): [10.5281/zenodo.23826596](https://doi.org/10.5281/zenodo.23826596)
4. **Folding a Ring onto Heavy-Hex: Formula-Built Schedules with Provable Gate Counts** (v1.3, 2026-10-31): [10.5281/zenodo.23826764](https://doi.org/10.5281/zenodo.23826764)
5. **Readable Depth Without the Calibration Map: Formula Placement on Heavy-Hex Devices, and a Defect the Calibration Does Not Show** (v1.1, 2026-10-31): [10.5281/zenodo.23827536](https://doi.org/10.5281/zenodo.23827536)
6. **What Sets the Readable Depth of a Placed Ring, and How Far a Self-Checking Layer Pushes It: Scan, Register, Avoid and Repair on Three Heavy-Hex Devices Without the Calibration Map** (v1.0, 2026-11-02): [10.5281/zenodo.23883938](https://doi.org/10.5281/zenodo.23883938)
7. **Exact Answers, No Map, No Mitigation: User-Written Circuits through a Placement-Only OS on IBM Heron r2 Devices** (v1, 2026-11-08): [10.5281/zenodo.24046673](https://doi.org/10.5281/zenodo.24046673)
8. **Readable Quantum Dynamics Without Error Mitigation: Dual-Unitary Chains up to 91 Qubits and 3D Lattice Tests on IBM Heron Devices** (v1.0, 2026-11-11): [10.5281/zenodo.24136512](https://doi.org/10.5281/zenodo.24136512)
9. **What Makes Raw Quantum Dynamics Readable? The Share of Signal Kept, Across 179 Results on IBM Heron** (v1, 2026-11-16): [10.5281/zenodo.24278888](https://doi.org/10.5281/zenodo.24278888)
10. **Decisions No Correction of the Uncontrolled Circuit Can Reach: Real-Time Control on IBM Heron, Declared Before the Data** (v1, 2026-11-19): [10.5281/zenodo.24367001](https://doi.org/10.5281/zenodo.24367001)

## Contact

contact　　love.os.architect@proton.me
