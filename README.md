# Bachelor's Thesis

Development and benchmarking of an abstraction layer for quantum software.

Bachelor's thesis in Software Engineering, Hochschule Heilbronn, written in collaboration with **Fraunhofer IPA**, Stuttgart. The thesis text is in German.

This repository contains the final thesis as a PDF. The full text is in [Bachelor's_Thesis_Daniel_Faigle.pdf](Bachelor's_Thesis_Daniel_Faigle.pdf).

## Abstract

Quantum software frameworks differ in their APIs, simulator behaviour and supported feature sets, which makes circuits hard to port and hard to compare. This thesis designs and implements a framework agnostic abstraction layer that expresses a quantum circuit once and executes it on several backends, currently *PennyLane*, *Qiskit*, *Qulacs* and *Pauli Propagation*. A benchmarking methodology is developed alongside it to quantify the runtime overhead the abstraction introduces and to compare the backends under identical workloads.

## Related repositories

- [qc-executor, branch `ba_daniel`](https://github.com/flaqship/qc-executor/tree/ba_daniel) holds the abstraction layer implemented for this thesis. The work described here lives on that branch, not on the default branch
- [benchmarking-system](https://github.com/dfaigle/benchmarking-system) is the benchmark harness used for the measurements

## Author

Daniel Faigle, supervised at Fraunhofer IPA.
