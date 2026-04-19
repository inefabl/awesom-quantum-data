# Time-Ordered View (EN): Quantum Data Management × Tensor Networks

> This companion page reorganizes the literature by **time periods** and only highlights each period's **overall characteristics** (e.g., typical experimental equipment and dominant research directions), instead of paper-by-paper details.
>
> **Linking rule used here:** if a paper/work has a publication link and/or project link in `README.md`, the corresponding entry below includes those links as well.

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
- **Linked works from README**
  - **A Single Quantum Cannot Be Cloned (Nature 1982):** [Paper](https://doi.org/10.1038/299802a0)
  - **Quantum Computation and Quantum Information (CUP 2010):** [Book/Publisher](https://www.cambridge.org/9781107002173)
  - **Quantum Algorithms for Element Distinctness (2000):** [Paper](https://ieeexplore.ieee.org/abstract/document/933880)

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
- **Linked works from README**
  - **Quantum Databases (CIDR 2013):** [Paper](https://infoscience.epfl.ch/entities/publication/1582ce6c-b5b0-4702-8c81-3372784bb369)
  - **FAQ: Questions Asked Frequently (arXiv 2016):** [Paper](https://arxiv.org/abs/1504.04044)

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
- **Linked works from README**
  - **Query Processing on Tensor Computation Runtimes (PVLDB 2022):** [Paper](https://doi.org/10.14778/3551793.3551833)
  - **Join Order Optimisation on Quantum Hardware (PVLDB 2022):** [Paper](https://dl.acm.org/doi/10.1145/3588946) | [Project](https://github.com/lfd/sigmod23-reproduction)
  - **Optimizing Tensor Programs on Flexible Storage (arXiv 2022):** [Paper](https://arxiv.org/abs/2210.06267)

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
- **Linked works from README**
  - **When Quantum Computing Meets Database: Hybrid Sampling for AQP (TKDE 2024):** [Paper](https://doi.org/10.1109/TKDE.2024.3480278)
  - **Quantum Storage Design for Tables in RDBMS (QDSM 2024):** [Paper](https://www.ifis.uni-luebeck.de/~groppe/qdsm/?page=paper&year=2024&paperid=p2)
  - **Towards Quantum Data Structures for Enhanced Database Performance (QDSM 2024):** [Paper](https://www.vldb.org/workshops/2024/proceedings/QDSM/QDSM.6.pdf)
  - **Is Quantum-Based SQL Query Execution Viable? (QDSM 2024):** [Paper](https://www.ifis.uni-luebeck.de/~groppe/qdsm/?page=paper&year=2024&paperid=p5)
  - **Quantum Data Management: From Theory to Opportunities (arXiv 2024):** [Paper](https://ieeexplore.ieee.org/abstract/document/10597772)
  - **Opportunities for Quantum Acceleration of Databases (PVLDB 2023):** [Paper](https://dl.acm.org/doi/10.14778/3598581.3598603) | [Project](https://github.com/TobiasWinker/QC4DB_VQC_Tutorial)
  - **Quantum Annealing Method for Dynamic VM/Task Allocation (ICDEW 2023):** [Paper](https://doi.org/10.1109/ICDEW58674.2023.00023) | [Project](https://github.com/valterUo/quantum-annealing-method-for-dynamic-workflow-scheduling-in-cloud-from-sustainabilitity-perspective)
  - **The State Preparation of Multivariate Normal Distributions using Tree Tensor Network：** [Paper](https://arxiv.org/abs/2412.12067) 

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
- **Linked works from README**
  - **Operational Framework for a Quantum Database (arXiv 2025):** [Paper](https://arxiv.org/abs/2405.14947)
  - **Private Quantum Database (arXiv 2025):** [Paper](https://arxiv.org/abs/2508.19055)
  - **Quantum Data Management in the NISQ Era (PVLDB 2025):** [Paper](https://doi.org/10.14778/3725688.3725701)
  - **Q2O Demo (PVLDB 2025):** [Paper](https://dl.acm.org/doi/10.14778/3750601.3750691) | [Project](https://github.com/ihanwen99/Q2O)
  - **Qymera (SIGMOD-Companion 2025):** [Paper](https://doi.org/10.1145/3722212.3725126)
  - **TQEx (SIGMOD 2025):** [Paper](https://doi.org/10.1145/3769835)
  - **Qute (arXiv 2026):** [Paper](https://arxiv.org/abs/2602.14699) | [Project](https://github.com/weAIDB/Qute)
  - **Approximating Tensor Network Contraction with Sketches (arXiv 2026):** [Paper](https://arxiv.org/abs/2603.07387)

## Cross-Period Trend Summary

- **Hardware trajectory:** from theory/simulation → heterogeneous classical acceleration → hybrid access to real QPUs/annealers.
- **Method trajectory:** from foundations → operator-level exploration → hybrid optimization/sampling → system-level integration.
- **Engineering trajectory:** from conceptual models to reproducible prototypes with clearer interfaces to existing DB ecosystems.
