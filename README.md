# A Survey of Quantum Data Management × Tensor Networks

[English](README.md) | [中文](README_CN.md)

- Time-ordered companion: [timeOrder-EN](timeOrder-EN.md)

> This README is reorganized from the survey spreadsheet into a README-style literature map with **topic sections + grouped entries + concise structured notes**. It covers quantum storage, quantum data structures, quantum SQL execution, quantum-enhanced optimization, tensor-network computation, and quantum-inspired machine learning.

## Notes

- This survey contains **35** paper/system entries organized into **11** themes.
- The Chinese version keeps the more detailed multi-dimensional summary. The English version below is a compact counterpart for easier international sharing.
- Symbols: **√** = explicit support / strong emphasis; **○** = partial support / limited discussion; **—** = not discussed or not the focus.

<a id="toc"></a>
## Contents

- [Time-Ordered View (EN)](timeOrder-EN.md)
- [Quantum Storage](#quantum-storage)
- [Quantum Data Structures](#quantum-data-structures)
- [Private Quantum Databases](#private-quantum-databases)
- [Quantum Data Management Surveys](#quantum-data-management-surveys)
- [Quantum SQL Execution](#quantum-sql-execution)
- [Query-Theoretic Foundations](#query-theory-foundations)
- [Quantum-Augmented Query Optimization](#quantum-augmented-query-optimization)
- [Hybrid-Sampling AQP Frameworks](#hybrid-sampling-aqp)
- [Quantum Annealing for Cloud Scheduling](#quantum-annealing-cloud-scheduling)
- [Tensor-Network Computation](#tensor-network-computation)
- [Quantum-Inspired Machine Learning](#quantum-inspired-ml)

<a id="quantum-storage"></a>
## Quantum Storage

Focuses on quantum-state encoding, table representation, quantum indexing, and storage abstractions for quantum databases.

[**⬆️Back to Contents**](#toc)

1. **Operational Framework for a Quantum Database (arXiv 2025)**  
   *Rieger et al., Operational Framework for a Quantum Database, arXiv:2405.14947v2, 2025.* [[Paper](https://arxiv.org/abs/2405.14947)]  
   - Defines a software-centric operational framework for quantum databases, including prepare, extend, remove, write, read-out, and permute.
   - Strong on lifecycle abstraction and quantum indexing, even without assuming a full QRAM-based implementation.

2. **Quantum Storage Design for Tables in RDBMS (QCOS/QROS, QDSM’24)**  
   *Tuodu Li et al., Quantum Storage Design for Tables in RDBMS (QDSM’24).* [[Paper](https://www.ifis.uni-luebeck.de/~groppe/qdsm/?page=paper&year=2024&paperid=p2)]  
   - Encodes relational tables into quantum circuits, with QCOS and QROS as column-oriented and row-oriented storage layouts.
   - Highlights qubit-efficiency and storage-format design, but also exposes the practical limits of current IBM devices.

3. **Quantum Databases (CIDR 2013)**  
   *Roy et al., Quantum Databases (CIDR 2013).* [[Paper](https://infoscience.epfl.ch/entities/publication/1582ce6c-b5b0-4702-8c81-3372784bb369)]  
   - Presents a relational-style framework for uncertain resource transactions using concepts such as possible worlds, pending transactions, and grounding.
   - Implemented as a classical MySQL prototype; conceptually quantum-inspired rather than quantum-hardware-native.

4. **Nielsen & Chuang (QCQI) Ch.1–2 (textbook excerpt)**  
   *Nielsen & Chuang, Quantum Computation and Quantum Information (CUP 2010), Ch.1–2.* [[Paper](https://www.cambridge.org/9781107002173)]  
   - Introduces the information-theoretic foundations of quantum-state representation, fidelity, and compressibility.
   - Useful as a conceptual baseline for any “quantum storage” discussion, even though it is not a DBMS paper.

5. **A Single Quantum Cannot Be Cloned (Nature 1982)**  
   *Wootters & Zurek, A Single Quantum Cannot Be Cloned, Nature 299:802–803, 1982.* [[Paper](https://doi.org/10.1038/299802a0)]  
   - Establishes the no-cloning theorem, a fundamental constraint for quantum data reuse, backup, and replication.
   - Important whenever a database design assumes copying or broadcasting quantum states.

<a id="quantum-data-structures"></a>
## Quantum Data Structures

Covers quantum data structures for search, oracle access, and accelerated database-style retrieval.

[**⬆️Back to Contents**](#toc)

1. **Towards Quantum Data Structures for Enhanced Database Performance (QDSM’24)**  
   *Littau et al., Towards Quantum Data Structures for Enhanced Database Performance (QDSM’24).* [[Paper](https://www.vldb.org/workshops/2024/proceedings/QDSM/QDSM.6.pdf)]  
   - Explores circuit-level quantum data structures aimed at faster database search and multi-element retrieval.
   - Emphasizes the data-encoding bottleneck and positions the work as an early design study.

2. **Quantum Algorithms for Element Distinctness (arXiv:quant-ph/0007016)**  
   *Buhrman et al., Quantum Algorithms for Element Distinctness, arXiv:quant-ph/0007016v2 (2000).* [[Paper](https://ieeexplore.ieee.org/abstract/document/933880)]  
   - A foundational quantum query-complexity result for distinctness and search-like problems.
   - Useful as theoretical background for database retrieval and comparison primitives.

<a id="private-quantum-databases"></a>
## Private Quantum Databases

Focuses on privacy-preserving retrieval using quantum encoding and destructive measurement.

[**⬆️Back to Contents**](#toc)

1. **Private Quantum Database (arXiv 2025)**  
   *Gatti, Geerts & Hai, Private Quantum Database, arXiv:2508.19055v3, 2025.* [[Paper](https://arxiv.org/abs/2508.19055)]  
   - Proposes a hybrid architecture in which classical systems store the database state description and fresh quantum states are prepared at query time.
   - Uses QRAC-style ideas and mutually unbiased bases to balance user privacy, data privacy, and retrieval correctness.

<a id="quantum-data-management-surveys"></a>
## Quantum Data Management Surveys

Panoramic views of quantum data management in the NISQ era and future distributed quantum systems.

[**⬆️Back to Contents**](#toc)

1. **Quantum Data Management in the NISQ Era (PVLDB 2025)**  
   *Hai et al., Quantum Data Management in the NISQ Era, PVLDB 18(6):1720–1729, 2025.* [[Paper](https://doi.org/10.14778/3725688.3725701)]  
   - Surveys data management problems around quantum-state simulation, hybrid execution, encoding, scheduling, and system reliability.
   - Especially useful as a roadmap paper linking database research with NISQ constraints.

2. **Quantum Data Management: From Theory to Opportunities (Tutorial / arXiv 2024)**  
   *Hai, Hung & Feld, Quantum Data Management: From Theory to Opportunities, arXiv:2403.02856v1, 2024.* [[Paper](https://ieeexplore.ieee.org/abstract/document/10597772)]  
   - A tutorial-style overview spanning quantum computing fundamentals, hybrid systems, and future quantum internet scenarios.
   - Strong on research opportunities and system-level problem framing.

<a id="quantum-sql-execution"></a>
## Quantum SQL Execution

Covers quantum and tensorized realizations of SQL, relational algebra, and database execution engines.

[**⬆️Back to Contents**](#toc)

1. **Qute: Towards Quantum-Native Database (arXiv 2026)**  
   *Chen et al., Qute: Towards Quantum-Native Database, arXiv:2602.14699v1, 2026.* [[Paper](https://arxiv.org/abs/2602.14699)] [[Github](https://github.com/weAIDB/Qute)]  
   - Proposes a hybrid quantum-classical database with extended SQL, selective quantum indexing, fidelity-aware storage, and compressed tensor-network support.
   - Particularly relevant for bridging quantum operators, storage abstractions, and DBMS-style optimization.

2. **TQEx: Tensor-based Query Engine Enhanced by Bridging the Gap (SIGMOD 2025)**  
   *Zhang et al., TQEx: Tensor-based Query Engine Enhanced by Bridging the Gap, Proc. ACM Manag. Data 3(6), 2025.* [[Paper](https://doi.org/10.1145/3769835)]  
   - Extends tensor-based query execution to handle practical issues such as irregular loops, string processing, and multi-XPU execution.
   - Demonstrates that bridging the SQL–tensor gap is essential for strong end-to-end performance.

3. **Qymera: Simulating Quantum Circuits using RDBMS (SIGMOD-Companion 2025)**  
   *Littau & Hai, Qymera: Simulating Quantum Circuits using RDBMS, SIGMOD-Companion 2025.* [[Paper](https://doi.org/10.1145/3722212.3725126)]  
   - Represents quantum states and gates as relational tables and translates circuit evolution into SQL.
   - A notable example of using an RDBMS as the native execution backend for quantum-circuit simulation.

4. **Is Quantum-Based SQL Query Execution Viable? (QDSM’24)**  
   *Kesarwani & Haritsa, Is Quantum-Based SQL Query Execution Viable?, VLDB QDSM’24.* [[Paper](https://www.ifis.uni-luebeck.de/~groppe/qdsm/?page=paper&year=2024&paperid=p5)]  
   - Examines how relational operators such as selection, join, union, intersection, difference, and sort might map onto quantum subroutines.
   - Explicitly discusses hybrid post-validation, uncertainty, and the impact of quantum execution on DBMS contracts.

5. **Query Processing on Tensor Computation Runtimes (TQP, PVLDB 2022)**  
   *He et al., Query Processing on Tensor Computation Runtimes, PVLDB 15(11) 2022.* [[Paper](https://doi.org/10.14778/3551793.3551833)]  
   - Compiles relational queries into tensor programs and executes them on tensor runtimes such as PyTorch, TVM, and ONNX Runtime.
   - A strong reference for “tensor-native” SQL execution on heterogeneous hardware.

<a id="query-theory-foundations"></a>
## Query-Theoretic Foundations

Foundational theory for query representation, hypergraphs, factorization, and join ordering.

[**⬆️Back to Contents**](#toc)

1. **FAQ: Questions Asked Frequently (arXiv 2016)**  
   *Abo Khamis, Ngo & Rudra, FAQ: Questions Asked Frequently, arXiv:1504.04044v5, 2016.* [[Paper](https://arxiv.org/abs/1504.04044)] 
   - Unifies joins, aggregates, probabilistic inference, matrix-chain multiplication, and related tasks in the FAQ framework.
   - Essential for connecting database query processing with tensor contractions and variable-elimination views.

<a id="quantum-augmented-query-optimization"></a>
## Quantum-Augmented Query Optimization

Focuses on quantum-enhanced approaches to optimization subproblems such as join ordering.

[**⬆️Back to Contents**](#toc)

1. **Q2O: Quantum-augmented Query Optimizer (PVLDB 2025 demo)**  
   *Liu et al., A Demonstration of Q2O: Quantum-Augmented Query Optimizer, PVLDB 18(12) 2025, 10.14778/3750601.3750691.* [[Paper](https://dl.acm.org/doi/10.14778/3750601.3750691)] [[Github](https://github.com/ihanwen99/Q2O)]
   - Uses D-Wave hybrid solvers to generate join-order hints that are then injected into PostgreSQL.
   - A practical example of quantum optimization integrated into a mainstream DBMS planning pipeline.

2. **Join Order Optimisation on Quantum Hardware (PVLDB 2022)**  
   *Schönberger et al., eady to Leap (by Co-Design)? Join Order Optimisation on Quantum Hardware, PVLDB 15(1) 2022, 10.1145/3588946.* [[Paper](https://dl.acm.org/doi/10.1145/3588946)] [[Github](https://github.com/lfd/sigmod23-reproduction)]
   - Maps join-order optimization to quantum optimization models such as QUBO/Ising formulations.
   - Compares gate-based and annealing-style hardware, highlighting both promise and scale limits.

<a id="hybrid-sampling-aqp"></a>
## Hybrid-Sampling AQP Frameworks

Introduces quantum ideas into approximate query processing and sampling-heavy analytics.

[**⬆️Back to Contents**](#toc)

1. **When Quantum Computing Meets Database: A Hybrid Sampling Framework for Approximate Query Processing (TKDE 2024)**  
   *Wu et al., When Quantum Computing Meets Database: A Hybrid Sampling Framework for Approximate Query Processing, IEEE TKDE 36(12):9532–9545, 2024.* [[Paper](https://doi.org/10.1109/TKDE.2024.3480278)]  
   - Combines classical sampling with quantum amplitude amplification for rare-group estimation in approximate query processing.
   - One of the clearest examples of hybrid quantum-classical AQP design on current hardware assumptions.

<a id="quantum-annealing-cloud-scheduling"></a>
## Quantum Annealing for Cloud Scheduling

Applies quantum optimization to task scheduling, VM placement, and infrastructure management.

[**⬆️Back to Contents**](#toc)

1. **Opportunities for Quantum Acceleration of Databases (PVLDB 2023)**  
   *Çalıkyılmaz et al., Opportunities for Quantum Acceleration of Databases: Optimization of Queries and Transaction Schedules, PVLDB 16(9) 2023, 10.14778/3598581.3598603; artifacts:.* [[Paper](https://dl.acm.org/doi/10.14778/3598581.3598603)] [[Github](https://github.com/TobiasWinker/QC4DB_VQC_Tutorial)]
   - Surveys where quantum hardware may accelerate database optimization and transaction scheduling.
   - Useful as a broad opportunity map connecting QA, VQCs, and database workloads.

2. **Quantum Annealing Method for Dynamic Virtual Machine and Task Allocation in Cloud Infrastructures from Sustainability Perspective (ICDEW 2023)**  
   *Uotila & Lu, Quantum Annealing Method for Dynamic Virtual Machine and Task Allocation in Cloud Infrastructures from Sustainability Perspective, ICDEW 2023.* [[Paper](https://doi.org/10.1109/ICDEW58674.2023.00023)] [[Github](https://github.com/valterUo/quantum-annealing-method-for-dynamic-workflow-scheduling-in-cloud-from-sustainabilitity-perspective)]
   - Models VM and task allocation as a QUBO problem and targets sustainable cloud scheduling.
   - Relevant as a data-management-adjacent optimization case rather than a query-execution paper.

<a id="tensor-network-computation"></a>
## Tensor-Network Computation

Covers tensor representations, compression, contraction, storage formats, and tensor-based data systems.

[**⬆️Back to Contents**](#toc)

1. **Approximating Tensor Network Contraction with Sketches (arXiv 2026)**
   *Heddes et al., Approximating Tensor Network Contraction with Sketches, arXiv:2603.07387v1, 2026.* [[Paper](https://arxiv.org/abs/2603.07387)]
   - Uses sketching to approximate tensor-network contraction efficiently, including cyclic settings.
   - Interesting for approximate analytics, contraction planning, and join-size estimation connections.

2. **On the Optimal Linear Contraction Order of Tree Tensor Networks, and Beyond (arXiv 2024)**
   *Stoian, Milbradt & Mendl, On the Optimal Linear Contraction Order of Tree Tensor Networks, and Beyond, arXiv:2209.12332v5, 2024.* [[Paper](https://arxiv.org/abs/2209.12332)] 
   - Studies contraction ordering for tree tensor networks and beyond, with clear optimization implications.
   - Particularly relevant if contraction planning is compared to join-order optimization.

3. **Optimizing Tensor Programs on Flexible Storage (arXiv 2022)**
   *Schleich, Shaikhha & Suciu, Optimizing Tensor Programs on Flexible Storage, arXiv:2210.06267v1, 2022.* [[Paper](https://arxiv.org/abs/2210.06267)]
   - Treats tensor programs and storage layouts as jointly optimizable.
   - Highly relevant for DB-style cost models over tensor representations and execution plans.

4. **ALTO: Adaptive Linearized Storage of Sparse Tensors (ICS 2021)**  
   *Helal et al., ALTO: Adaptive Linearized Storage of Sparse Tensors, ICS 2021.* [[Paper](https://doi.org/10.1145/3447818.3461703)]  
   - A sparse-tensor storage format emphasizing locality, compression, balanced work partitioning, and synchronization reduction.
   - Useful for comparing alternative sparse tensor layouts with HiCOO-like designs.

5. **TT-Rec: Tensor Train Compression for DLRM Embeddings (MLSys 2021)**
   *Yin et al., TT-Rec: Tensor Train Compression for Deep Learning Recommendation Model Embeddings (MLSys 2021).* [[Paper](https://proceedings.mlsys.org/paper/2021/file/1c4534ff58dab447545594c4863239b3-Paper.pdf)] [[Github](https://github.com/facebookresearch/FBTT-Embedding)]
   - Compresses large embedding tables with TT decompositions while preserving recommendation quality.
   - Relevant for large vector/table compression and memory-efficient data representation.

6. **Tentris – A Tensor-Based Triple Store (ISWC 2020)**
   *Bigerl et al., Tentris – A Tensor-Based Triple Store (ISWC 2020); code+data:.* [[Paper](https://tentris.dice-research.org/iswc2020)] [[Github](https://github.com/dice-group/tentris-research-project)]
   - Represents RDF data as sparse tensors and executes SPARQL-style patterns through tensor operations.
   - A concrete example of a tensor-native data system, though not a tensor-network system in the quantum sense.

7. **Efficient Contraction of Large Tensor Networks for Weighted Model Counting through Graph Decompositions**  
   *Dudek, Dueñas-Osorio & Vardi, Efficient Contraction of Large Tensor Networks for Weighted Model Counting through Graph Decompositions, arXiv:1908.04381v2, 2020.* [[Paper](https://arxiv.org/abs/1908.04381)]  
   - Connects tensor-network contraction with graph decomposition and weighted model counting.
   - Helpful for understanding contraction planning through a database-style structural lens.

8. **A Tensor Based Data Model for Polystore: An Application to Social Networks Data**  
   *Leclercq & Savonnet, A Tensor Based Data Model for Polystore: An Application to Social Networks Data, arXiv:1806.09967v1, 2018.* [[Paper](https://arxiv.org/abs/1806.09967)]  
   - Uses tensors as a pivot model to bridge multi-model data sources in a polystore setting.
   - Relevant for tensor-based integration rather than tensor-network compression.

9. **HiCOO: Hierarchical Storage of Sparse Tensors (SC18 paper)**
   *Li et al., HiCOO: Hierarchical Storage of Sparse Tensors, SC18 2018 (IEEE).* [[Paper](https://www.computer.org/csdl/proceedings-article/sc/2018/838400a238/17D45VsBU7p)] [[Github](https://github.com/hpcgarage/ParTI)]
   - Proposes a hierarchical sparse-tensor storage format with strong locality and compressed indexing.
   - Important for thinking about block-aware TN pages or sparse tensor storage layers.

10. **HiCOO (SC18 slides / talk deck)**
   *Li et al., HiCOO SC18 slides (pap511s5.pdf).* [[Source](https://www.sc18.supercomputing.org/proceedings/tech_paper/tech_paper_files/pap511s5.pdf)] [[Github](https://github.com/hpcgarage/ParTI)] 
   - Companion slides that emphasize layout decisions, compression intuition, and scheduler behavior.

11. **Matrix Product State for Higher-Order Tensor Compression and Classification**
   *Bengua et al., Matrix Product State for Higher-Order Tensor Compression and Classification (TensorCompression.pdf).* [[Paper](https://compimg.ece.illinois.edu/publications/TensorCompression.pdf)]
   - Applies MPS/TT ideas to compress high-order tensors for downstream classification.
   - A good bridge between TN compression and ML-oriented feature extraction.

12. **Hand-waving and Interpretive Dance: An Introductory Course on Tensor Networks**  
   *Bridgeman & Chubb, Hand-waving and Interpretive Dance: An Introductory Course on Tensor Networks, arXiv:1603.03039v4, 2017.* [[Paper](https://arxiv.org/abs/1603.03039)]  
   - A broad tutorial on MPS, PEPS, MERA, contraction intuition, and computational trade-offs.
   - Excellent background reading for TN terminology and design intuition.
   - Useful for implementation-oriented understanding of HiCOO.

13. **Tensor-Train Decomposition (SIAM J. Sci. Comput. 2011)**  
   *Oseledets, Tensor-Train Decomposition, SIAM J. Sci. Comput. 33(5):2295–2317, 2011.* [[Paper](https://doi.org/10.1137/090752286)]  
   - The canonical reference for TT decomposition, low-rank tensor compression, and core-wise computation.
   - Fundamental for any TN-based storage or computation design.

<a id="quantum-inspired-ml"></a>
## Quantum-Inspired Machine Learning

Covers quantum-inspired algorithms and low-rank/sampling ideas with implications for data systems.

[**⬆️Back to Contents**](#toc)

1. **A quantum-inspired classical algorithm for recommendation systems**  
   *Ewin Tang, A quantum-inspired classical algorithm for recommendation systems, arXiv:1807.04271v3, 2019.* [[Paper](https://arxiv.org/abs/1807.04271)]  
   - A landmark result showing that classical sampling-based data structures can match the spirit of certain quantum recommendation speedups.
   - Important when evaluating whether claimed quantum advantages in data systems truly come from quantum mechanics or from stronger access assumptions.
