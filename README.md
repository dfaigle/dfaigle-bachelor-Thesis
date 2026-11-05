# Bachelor's Thesis

Development and benchmarking of an abstraction layer for quantum software.

Bachelor's thesis in Software Engineering, Hochschule Heilbronn, written in collaboration with **Fraunhofer IPA**, Stuttgart. The thesis text is in German.

This repository contains the final thesis as a PDF. The full text is in [Bachelor's_Thesis_Daniel_Faigle.pdf](Bachelor's_Thesis_Daniel_Faigle.pdf).

## Abstract

This bachelor's thesis addresses the development and runtime analysis of an abstraction layer that allows quantum circuits and observables to be described in a single form and subsequently executed as objects of the quantum frameworks *PennyLane* and *Qiskit*. The software component was integrated into the *Executor* Python library, which is currently under active development at Fraunhofer IPA and was published under an open-source license as [qc-executor](https://github.com/flaqship/qc-executor). Its previous internal representation relied on *Qiskit* objects and was therefore tied to a single framework. This dependency is replaced by a self-contained data structure, so that the description of the circuit remains unchanged and the execution environments of the respective other framework can be addressed solely by selecting the backend. Since framework calls occur exclusively within the backends, a program written once also remains executable across framework version changes. In addition, the runtime overhead introduced by this layer compared to direct use of the frameworks is evaluated.

The implementation itself is not part of this repository. It lives in [qc-executor, branch `ba_daniel`](https://github.com/flaqship/qc-executor/tree/ba_daniel), not on the default branch.

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

| Repository | Description |
|------------|-------------|
| [qc-executor](https://github.com/flaqship/qc-executor/tree/ba_daniel) | Integrate abstraction layer for running quantum circuits across frameworks in the Fraunhofer open source project "qc_executor" |
| [qc-frameworks-benchmark-suite](https://github.com/dfaigle/qc-frameworks-benchmark-suite) | Benchmark harness used for the measurements |

## Author

Daniel Faigle, supervised at Fraunhofer IPA.
