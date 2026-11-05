# Bachelor's Thesis

Development and benchmarking of an abstraction layer for quantum software.

Bachelor's thesis in Software Engineering, Hochschule Heilbronn, written in collaboration with **Fraunhofer IPA**, Stuttgart. The thesis text is in German.

This repository contains the final thesis as a PDF. The full text is in [Bachelor's_Thesis_Daniel_Faigle.pdf](Bachelor's_Thesis_Daniel_Faigle.pdf).

## Abstract

Quantum software frameworks differ in their APIs, simulator behaviour and supported feature sets, which makes circuits hard to port and hard to compare. This thesis designs and implements a framework agnostic abstraction layer that expresses a quantum circuit once and executes it on several backends, currently *PennyLane*, *Qiskit*, *Qulacs* and *Pauli Propagation*. A benchmarking methodology is developed alongside it to quantify the runtime overhead the abstraction introduces and to compare the backends under identical workloads.

## Results

[results/](results/) holds the benchmark data from [qc-frameworks-benchmark-suite](https://github.com/dfaigle/qc-frameworks-benchmark-suite). The same random circuits run once directly on PennyLane or Qiskit and once through the Executor, so the difference is the cost of the abstraction.

- [final_plotted_results/](results/final_plotted_results/) contains the comparison plots used in the thesis
- [raw_results/](results/raw_results/) contains the CSVs and per-run plots, one folder per run

Overhead of the Executor compared to the native framework (factor above 1 means the Executor is slower):

| Mode | vs. PennyLane | vs. Qiskit |
|------|---------------|------------|
| Circuit creation | 0.14 | 1.97 |
| Execution | no measurable overhead | 1.40 |
| Gradient | not fully reliable, library versions differed between runs | 2.40 |

The execution overhead over Qiskit shrinks as the qubit count grows, because the extra work is Python bookkeeping that does not depend on register size. Only the Qiskit gradient factor grows with the gate count.

## Related repositories

- [qc-executor, branch `ba_daniel`](https://github.com/flaqship/qc-executor/tree/ba_daniel) holds the abstraction layer implemented for this thesis. The work described here lives on that branch, not on the default branch
- [qc-frameworks-benchmark-suite](https://github.com/dfaigle/qc-frameworks-benchmark-suite) is the benchmark harness used for the measurements

## Author

Daniel Faigle, supervised at Fraunhofer IPA.
