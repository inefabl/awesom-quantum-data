# Time-Ordered View (EN): Quantum Data Management × Tensor Networks

> This companion page reorganizes the literature by **time periods** and only highlights each period's **overall characteristics** (e.g., typical experimental equipment and dominant research directions), instead of paper-by-paper details.

[Back to README](README.md)

## 1982–2011: Theoretical Foundations and Representation Basics

- **Research focus**
  - Quantum information fundamentals (state representation, measurement constraints, no-cloning).
  - Early mathematical/compression representations for high-dimensional data (e.g., tensor decomposition foundations).
- **Typical experimental setup / equipment**
  - Mostly **theoretical analysis** and mathematical derivations.
  - Validation primarily via **classical numerical experiments** on CPUs/workstations.
- **System maturity**
  - No practical quantum DBMS systems yet.
  - Main contribution: constraints and abstractions that later system work must obey.

## 2013–2019: Database Semantics Emergence

- **Research focus**
  - First attempts to connect database semantics with quantum concepts (uncertainty, possible-world style abstractions).
  - Exploration of tensorized representations in data systems and analytics.
- **Typical experimental setup / equipment**
  - Predominantly **classical database engines** and simulation environments.
  - Quantum content is largely conceptual or emulated rather than hardware-native execution.
- **System maturity**
  - Prototype-level ideas, often integrated into existing relational/database workflows.
  - Established a bridge from theory to data-management problem framing.

## 2020–2022: Tensor Execution and Optimization Rise

- **Research focus**
  - Strong growth of **SQL-to-tensor** and tensor-runtime-based execution.
  - Foundational advances in query theory, variable ordering, and join/contraction optimization.
  - Early quantum-hardware studies for optimization subproblems (e.g., join order).
- **Typical experimental setup / equipment**
  - Heterogeneous **CPU/GPU/TPU** tensor runtimes become primary evaluation platforms.
  - Early NISQ evaluations include small-scale runs on gate-based devices and annealers.
- **System maturity**
  - Clear movement from conceptual proposals to measurable engine-level performance.
  - Workloads become more benchmark-driven (e.g., relational analytics suites).

## 2023–2024: Hybrid Quantum-Classical Enhancement Phase

- **Research focus**
  - Hybrid architectures become mainstream: quantum used for selected bottlenecks (optimization, sampling, search), classical systems keep orchestration.
  - More explicit discussion of quantum data loading/encoding overhead, reliability, and deployability.
  - Database-adjacent optimization (query planning, scheduling) becomes a practical entry point.
- **Typical experimental setup / equipment**
  - **D-Wave hybrid solvers/annealers** and **IBM Qiskit + cloud-accessed QPUs** are commonly used.
  - Continued reliance on classical baselines and simulators for end-to-end comparisons.
- **System maturity**
  - More demos and reproducible pipelines appear.
  - Integration with mainstream DB components (e.g., planners/optimizers) increases.

## 2025–2026: System Integration and Quantum-Native Direction

- **Research focus**
  - Shift toward **quantum-native database architecture**: storage abstractions, indexing, lifecycle operations, and extended SQL interfaces.
  - Stronger convergence between quantum data management and compressed tensor-network representations.
  - Increased attention to fidelity-aware storage, hybrid optimizer design, and end-to-end system contracts.
- **Typical experimental setup / equipment**
  - Mixed stack of **real quantum processors**, cloud quantum services, and high-performance classical backends.
  - Evaluation typically combines prototype systems + real-device or realistic hybrid validation.
- **System maturity**
  - Transition from isolated operators to system-level composition.
  - Still constrained by qubit budgets/noise, but architecture-level patterns are becoming clearer.

## Cross-Period Trend Summary

- **Hardware trajectory:** from theory/simulation → heterogeneous classical acceleration → hybrid access to real QPUs/annealers.
- **Method trajectory:** from foundations → operator-level exploration → hybrid optimization/sampling → system-level integration.
- **Engineering trajectory:** from conceptual models to reproducible prototypes with clearer interfaces to existing DB ecosystems.
