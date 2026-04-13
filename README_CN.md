# 量子数据管理 × 张量网络综述

> 本 README 依据 survey 表格重组而成，按 README 风格将条目整理为**主题目录 + 分组条目 + 结构化摘要**。内容覆盖量子存储、量子数据结构、量子 SQL 执行、量子增强优化、张量网络计算与量子启发机器学习等方向。

## 说明

- 共收录 **35** 条文献/系统条目，分为 **11** 个主题。
- 每条记录尽量保留 survey 中的多维评价，但压缩为以下五个视角：**数据模型**、**存储与表示**、**查询与执行**、**系统与工程**、**扩展维度**。
- 符号说明：**√** 表示明确支持或重点讨论，**○** 表示部分支持或有限涉及，**—** 表示未涉及或不是重点。

<a id="toc"></a>

| **五维分类 \ 时间轴** | **1982–2011**<br>理论与表示基础 | **2013–2019**<br>数据库语义萌芽 | **2020–2022**<br>张量执行与优化兴起 | **2023–2024**<br>混合增强阶段 | **2025–2026**<br>系统整合阶段 |
|---|---|---|---|---|---|
| **数据模型** | QCQI<br>No-Cloning<br>TT Decomposition | Quantum Databases<br>Tensor-based Polystore<br>Quantum-inspired Recommendation | Tentris<br>TQP<br>FAQ | Quantum Storage Design for Tables<br>Quantum Data Structures<br>Hybrid Sampling for AQP | Operational Framework for a Quantum Database<br>Private Quantum Database<br>Qute |
| **存储与表示** | QCQI<br>TT Decomposition<br>MPS Compression & Classification | Quantum Databases<br>Tensor-based Polystore | HiCOO<br>ALTO<br>Tentris | Quantum Storage Design for Tables<br>Quantum Data Management in the NISQ Era<br>Quantum Data Structures | Qute<br>Operational Framework for a Quantum Database<br>Private Quantum Database |
| **查询与执行** | QCQI<br>Element Distinctness | Quantum Databases<br>Quantum-inspired Recommendation | FAQ<br>TQP<br>Join Order Optimisation on Quantum Hardware | Is Quantum-Based SQL Query Execution Viable?<br>Hybrid Sampling for AQP<br>Q2O | Qute<br>Operational Framework for a Quantum Database<br>Private Quantum Database |
| **系统与工程** | TT Decomposition | Quantum Databases | TQP<br>Tentris<br>Qymera | Q2O<br>Quantum Annealing for Cloud Scheduling<br>Quantum Data Management in the NISQ Era | Qute<br>Operational Framework for a Quantum Database<br>Quantum Data Management: From Theory to Opportunities |
| **扩展维度** | No-Cloning<br>QCQI | Tensor-based Polystore<br>Quantum-inspired Recommendation | Tentris<br>HiCOO<br>MPS Compression & Classification | Private Quantum Database<br>Quantum Annealing for Cloud Scheduling<br>Quantum Data Management in the NISQ Era | Qute<br>Private Quantum Database<br>Quantum Data Management: From Theory to Opportunities |

## 目录

- [量子存储](#quantum-storage)
- [量子数据结构](#quantum-data-structures)
- [量子隐私数据库](#private-quantum-databases)
- [量子数据管理综述](#quantum-data-management-surveys)
- [量子SQL执行](#quantum-sql-execution)
- [查询理论基础](#query-theory-foundations)
- [量子增强优化查询](#quantum-augmented-query-optimization)
- [混合采样AQP框架](#hybrid-sampling-aqp)
- [云资源分配量子退火](#quantum-annealing-cloud-scheduling)
- [张量网络计算](#tensor-network-computation)
- [量子启发机器学习](#quantum-inspired-ml)

<a id="quantum-storage"></a>
## 量子存储

聚焦量子态、表数据编码、量子索引与量子数据库底层表示。

[**⬆️返回目录**](#toc)

1. **Operational Framework for a Quantum Database (arXiv 2025)**[[project](https://arxiv.org/abs/2405.14947)]
   *Rieger et al., Operational Framework for a Quantum Database, arXiv:2405.14947v2, 2025.*
   - **数据模型**：量子数据库四象限（CC/CQ/QC/QQ）；重点为 QC（量子索引 + 可克隆/经典数据）
   - **压缩存储**：√（量子索引 superposition state 压缩表示；索引寄存器仅需 ⌈log2(k)⌉ qubits）；**索引结构**：√（量子索引；独立 index/data registers）；**数据规模**：按 k 个索引元素建模；算法/框架级，未给大规模数据基准；**量子态表示**：|QDB^(k)⟩ = Σ ψ_j |j⟩_I |d_j⟩_D；区分 classical/quantum data 与 indexing
   - **查询算子**：基础数据库操作：prepare, extend, remove, write, read-out, permute；**执行模式**：量子数据库操作框架；软件式 gate-based 操作（非必须依赖专用 QRAM）；**硬件依赖**：门模型量子处理器；可结合 QRAM，但框架本身是 software-centric；**加载开销**：√（数据库准备/状态制备是核心操作，并显式讨论扩展/删除/写入代价）；**计算原生性**：√（QDB 状态可直接作为后续量子算法输入）
   - **优化目标**：定义可操作的 quantum DB lifecycle；平衡 superposition 压缩与 no-cloning/no-deletion 限制；**调度能力**：○（支持 index permutation 与 extend/remove 等生命周期调度，不是 SQL 调度器）；**真实DB集成**：—（操作框架/算法实现，不是完整 DBMS 集成）；**验证平台**：算法/框架级；讨论 QRAM / QPU 场景；**工程成熟度**：中
   - **关系模型适配**：低-中；**机器学习结合**：○（可为 Grover、pattern recognition 等量子算法提供数据底座）；**张量网络表示**：低；**压缩比**：索引侧由 k entries → ⌈log2(k)⌉ qubits（未给统一压缩比实验）；**计算原生性（综合）**：高

2. **Quantum Storage Design for Tables in RDBMS (QCOS/QROS, QDSM’24)**[[preoject](https://www.ifis.uni-luebeck.de/~groppe/qdsm/?page=paper&year=2024&paperid=p2)]
   *Tuodu Li et al., Quantum Storage Design for Tables in RDBMS (QDSM’24).*
   - **数据模型**：关系表（QCOS：列存；QROS：行存）
   - **压缩存储**：√（以叠加态在量子电路中编码表）；**索引结构**：—（存储格式本身；不引入 B+树等经典索引）；**数据规模**：实验含小表；并在 IBM 真机/模拟器验证（大表真机 Valid Ratio 近 0）；**量子态表示**：量子电路/叠加态寄存器（RowID/Data/Ancilla）；Hadamard/MCT 等门
   - **查询算子**：文中指向可原生支持选择/连接/投影等关系操作（需配套量子算法）；**执行模式**：全量子存储 +（面向量子算法的）量子-经典验证流程设想；**硬件依赖**：IBM 量子模拟器 + IBM 真机（ibm_lagos/nairobi/perth/brisbane 等）；**加载开销**：○（关系表→量子电路编码；测量会破坏叠加态）；**计算原生性**：○
   - **优化目标**：降低量子资源开销：qubit 随数据量对数增长；MCT 线性；并比较 QCOS/QROS；**事务ACID**：—（讨论可加入结果验证流程）；**验证平台**：IBM Q 设备 + 模拟器；**工程成熟度**：低-中
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：中

3. **Quantum Databases (CIDR 2013)**
   *Roy et al., Quantum Databases (CIDR 2013).* [[Project](http://www.youtopia.net/quantumdb/?page_id=16)]
   - **数据模型**：关系模型（资源事务/读事务；SQL-like 扩展）
   - **压缩存储**：○（以 possible worlds/约束 + pending/grounding 表示不确定性）；**索引结构**：√（文中说明为各关系定义索引）；**数据规模**：6000 事务；40 flights×150 seats；pending 事务上界 ~N/2（与到达顺序相关）；**量子态表示**：possible worlds / pending transactions / grounding（类“叠加/塌缩”语义）
   - **查询算子**：资源事务、读事务；约束满足检查（大量 joins）；**执行模式**：经典DB执行 + 延迟绑定/grounding；**硬件依赖**：无量子硬件（MySQL 原型；CPU）；**加载开销**：○（约束检查→join 多；需调 optimizer_search_depth）；**计算原生性**：○
   - **优化目标**：提升资源协调成功率/吞吐；控制 grounding 以平衡复杂度；**调度能力**：○（pending/grounding 策略影响“调度/执行时机”）；**事务ACID**：√（面向事务保证：原子性/持久性等）；**真实DB集成**：√（MySQL 原型验证）；**验证平台**：Intel Xeon 2.13GHz, 48GB RAM; MySQL；**工程成熟度**：中
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：中

4. **Nielsen & Chuang (QCQI) Ch.1–2（教材节选）**
   *Nielsen & Chuang, Quantum Computation and Quantum Information (CUP 2010), Ch.1–2.* [[Project](https://www.cambridge.org/9781107002173)]
   - **数据模型**：—（量子信息/信源模型）
   - **压缩存储**：√（量子信息压缩/编码：以 fidelity 约束讨论可压缩性）；**数据规模**：n→∞（信息论极限/块长）；**量子态表示**：量子态 |ψ⟩ / 密度算符 ρ
   - **查询算子**：—（非SQL；提供电路/测量等基本算子）；**执行模式**：电路模型（unitary + measurement）；**硬件依赖**：理想通用QC（电路）；**加载开销**：—（不涉及数据库装载；关注量子态制备/编码）；**计算原生性**：√
   - **优化目标**：最小化量子存储/通信资源（理论）；**工程成熟度**：高
   - **关系模型适配**：低；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：高

5. **A Single Quantum Cannot Be Cloned (Nature 1982)**
   *Wootters & Zurek, A Single Quantum Cannot Be Cloned, Nature 299:802–803, 1982.* [[DOI](https://doi.org/10.1038/299802a0)]
   - **数据模型**：—（量子信息基础定理）
   - **数据规模**：任意未知量子态（一般性理论结论）；**量子态表示**：任意未知量子态；复制/放大受线性量子力学约束
   - **查询算子**：—（非 SQL；给出不可克隆约束）；**执行模式**：理论证明（基于量子力学线性性）；**硬件依赖**：与具体硬件无关（通用量子系统）；**计算原生性**：○（量子存储态可用但不可任意复制/并行复用）   

<a id="quantum-data-structures"></a>
## 量子数据结构

关注面向检索、oracle 访问与数据库检索加速的量子数据结构。

[**⬆️返回目录**](#toc)

1. **Towards Quantum Data Structures for Enhanced Database Performance (QDSM’24)**[[project](https://www.vldb.org/workshops/2024/proceedings/QDSM/QDSM.6.pdf)]
   *Littau et al., Towards Quantum Data Structures for Enhanced Database Performance (QDSM’24).*
   - **数据模型**：—（面向“数据库检索/操作”的量子数据结构概念）
   - **索引结构**：—（目标是减少传统索引依赖）；**数据规模**：—（电路级演示/概念性，未给大规模数据）；**量子态表示**：电路级量子数据结构（QPD）；基于 superposition/entanglement；借鉴 QRAM/QRAG
   - **查询算子**：检索/搜索（modified Grover 多元素检索）；**执行模式**：电路模型；示例实现（Qiskit 类）；**硬件依赖**：门模型量子计算（NISQ）/模拟器；**加载开销**：√（指出 classical→quantum 数据编码/装载是关键瓶颈）；**计算原生性**：○
   - **优化目标**：加速数据库搜索/操作（多元素检索）；**验证平台**：量子电路实现（SDK/模拟器）；**工程成熟度**：低
   - **关系模型适配**：低；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：中

2. **Quantum Algorithms for Element Distinctness (arXiv:quant-ph/0007016)**[[project](https://ieeexplore.ieee.org/abstract/document/933880)]
   *Buhrman et al., Quantum Algorithms for Element Distinctness, arXiv:quant-ph/0007016v2 (2000).*
   - **数据模型**：—（算法/查询复杂度问题）
   - **数据规模**：输入规模 N（比较复杂度）；**量子态表示**：oracle/unitary + amplitude amplification
   - **查询算子**：比较 oracle；幅度放大/量子搜索；**执行模式**：黑盒（oracle）查询模型；**硬件依赖**：理想量子计算机（理论）；**加载开销**：—（通过 oracle 访问；不讨论 QRAM）；**计算原生性**：√
   - **优化目标**：降低比较复杂度：O(N^{3/4} log N)；有序情形 O(N^{1/2} log N)；**工程成熟度**：中
   - **关系模型适配**：低；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：高

<a id="private-quantum-databases"></a>
## 量子隐私数据库

强调量子编码与数据库检索中的隐私保护机制。

[**⬆️返回目录**](#toc)

1. **Private Quantum Database (arXiv 2025)**
   *Gatti, Geerts & Hai, Private Quantum Database, arXiv:2508.19055v3, 2025.*[[project](https://arxiv.org/abs/2508.19055)]
   - **数据模型**：关系表/键值检索（tuple-level retrieval）
   - **压缩存储**：○（QRAC 将 tuples 编码为量子态；偏隐私用途而非压缩导向）；**索引结构**：○（key→mutually unbiased bases / measurement basis routing；非传统索引）；**数据规模**：按 copy budget k / quantum states 数量计；面向 NISQ 混合架构，未给大规模行数实验；**量子态表示**：QRAC + mutually unbiased bases；测量破坏性 + no-cloning 保证隐私
   - **查询算子**：受限检索：PIR / SPIR（仅返回所请求 tuple）；**执行模式**：混合量子-经典：经典 DBMS 存储状态描述，查询时生成 fresh quantum states 并由客户端测量；**硬件依赖**：NISQ 门模型 + 经典 DBMS；**加载开销**：○（查询时需重新制备 fresh states；避免长期量子存储）；**计算原生性**：○（检索直接依赖量子测量，但量子态按需生成）
   - **优化目标**：双边隐私：用户隐私 + 数据隐私；平衡 correctness–privacy（copy budget k）；**真实DB集成**：○（与标准 DBMS 组成 hybrid architecture）；**验证平台**：概念/架构级；讨论 IBM Heron / System Two、trapped-ion、neutral-atom 等 NISQ 平台背景；**工程成熟度**：低
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：中

<a id="quantum-data-management-surveys"></a>
## 量子数据管理综述

对 NISQ 时代与未来量子数据管理问题做全景式归纳。

[**⬆️返回目录**](#toc)

1. **Quantum Data Management in the NISQ Era (PVLDB 2025)**
   *Hai et al., Quantum Data Management in the NISQ Era, PVLDB 18(6):1720–1729, 2025.* [[DOI](https://doi.org/10.14778/3725688.3725701)]
   - **数据模型**：经典数据与量子数据；提出三类范式（classical simulation / joint quantum-classical / pure quantum）
   - **压缩存储**：○（讨论量子数据紧凑表示、仿真表示与未来量子存储）；**索引结构**：—（综述/路线图层）；**数据规模**：面向 large-scale quantum states、multidimensional quantum data structures、QEC codes；非固定数据规模实验；**量子态表示**：qubits、superposition、entanglement；并讨论用 classical vectors / tensors 表示 quantum states
   - **查询算子**：—（非具体 SQL；聚焦 simulation、encoding、QEC、scheduling 等数据管理任务）；**执行模式**：经典仿真、联合量子-经典、纯量子三范式路线图；**硬件依赖**：经典计算机 + NISQ QPU + 未来 fault-tolerant quantum computers；**加载开销**：√（classical→quantum encoding / preprocessing 被强调为关键瓶颈）；**计算原生性**：○
   - **优化目标**：为量子计算建立数据管理路线图；提升可扩展性、可靠性与可管理性；**调度能力**：○（讨论 qubit allocation、scheduling、simulation resource management）；**真实DB集成**：—（综述/愿景）；**验证平台**：PVLDB 综述；附 preliminary results 与开源资料；**工程成熟度**：中
   - **关系模型适配**：中；**机器学习结合**：○（讨论 simulation optimization、error correction、ML 与数据管理交叉）；**张量网络表示**：○（将 tensor-network simulation 视为关键研究问题之一）；**计算原生性（综合）**：中

2. **Quantum Data Management: From Theory to Opportunities (Tutorial / arXiv 2024)**
   *Hai, Hung & Feld, Quantum Data Management: From Theory to Opportunities, arXiv:2403.02856v1, 2024.*c[[project](https://ieeexplore.ieee.org/abstract/document/10597772)]
   - **数据模型**：量子数据管理理论/教程框架；覆盖经典数据库问题与未来量子互联网数据系统
   - **数据规模**：以量子互联网、云量子计算、量子数据中心愿景为主；非固定实验规模；**量子态表示**：qubits、superposition、entanglement；并引入 quantum internet 中 entanglement-based transmission
   - **查询算子**：—（tutorial；回顾 query optimization、data integration、transaction mgmt 等并展望未来系统）；**执行模式**：理论/教程型：从 quantum computing fundamentals 到 quantum internet data systems；**硬件依赖**：NISQ 设备 + quantum internet（end nodes / repeater）+ 未来云量子系统；**加载开销**：○（讨论 quantum computing environment 中的数据处理与可达性问题）；**计算原生性**：○
   - **优化目标**：建立量子数据管理理论基础并发掘未来机会，尤其是 quantum internet 场景；**调度能力**：○（面向 distributed / quantum internet future systems 的调度与传输愿景）；**真实DB集成**：—（tutorial/vision）；**验证平台**：教程/理论论文；无完整系统原型；**工程成熟度**：中
   - **关系模型适配**：中；**机器学习结合**：○（与未来 QML、distributed quantum workloads 存在结合点）；**张量网络表示**：低；**计算原生性（综合）**：中

<a id="quantum-sql-execution"></a>
## 量子SQL执行

围绕 SQL、关系代数与数据库执行引擎的量子/张量化实现。

[**⬆️返回目录**](#toc)

1. **Qute: Towards Quantum-Native Database (arXiv 2026)**
   *Chen et al., Qute: Towards Quantum-Native Database, arXiv:2602.14699v1, 2026.* [[Code](https://github.com/weAIDB/Qute)]
   - **数据模型**：关系表（扩展 SQL），并面向未来多模态数据
   - **压缩存储**：√（fidelity-aware storage；支持 compressed tensor networks）；**索引结构**：√（selective quantum indexing / hybrid tree structures）；**数据规模**：原型/真实处理器验证；规模受当前 qubit 预算限制，但文称在 real processor 上较经典 baseline 更优；**量子态表示**：qubits + gate-efficient circuits；unified quantum memory；fidelity-aware storage
   - **查询算子**：扩展 SQL；Grover-based filter、similarity join、retrieval/interactive BI 等；**执行模式**：混合量子-经典：extended SQL→量子电路；hybrid optimizer 动态选经典/量子计划；**硬件依赖**：门模型量子计算 + 经典存储/执行；**加载开销**：√（强调 qubit budget 限制、selective probing 与 fidelity-preserving storage）；**计算原生性**：√
   - **优化目标**：gate-efficient compilation、hybrid plan selection、selective quantum indexing、fidelity preservation；**调度能力**：○（quantum-aware optimizer / prefix routing / hybrid plan scheduling）；**事务ACID**：○（路线图中含 rollback / error detection & correction）；**真实DB集成**：○（开源 prototype；非成熟商用 DB 集成）；**验证平台**：OriginQ / origin_wukong real quantum processor；**工程成熟度**：中
   - **关系模型适配**：高；**机器学习结合**：○（路线图含 quantum machine learning / multimodal analytics）；**张量网络表示**：高（存储层显式使用 compressed tensor networks）；**计算原生性（综合）**：高

2. **TQEx: Tensor-based Query Engine Enhanced by Bridging the Gap (SIGMOD 2025)**
   *Zhang et al., TQEx: Tensor-based Query Engine Enhanced by Bridging the Gap, Proc. ACM Manag. Data 3(6), 2025.* [[DOI](https://doi.org/10.1145/3769835)]
   - **数据模型**：关系模型（SQL / TPC-H）
   - **压缩存储**：○（通过紧凑字符串/向量存储与去 padding 策略降低存储和计算开销）；**数据规模**：TPC-H，支持到 SF 300（multi-XPU）；**量子态表示**：张量程序 / tensor ops（非量子态）
   - **查询算子**：SPJ + 聚合 + 字符串算子；重点优化 join / aggregate / variable-length strings；**执行模式**：SQL→tensor program；单/多 XPU 执行；**硬件依赖**：异构 XPU：CPU、NVIDIA/AMD/Apple GPU 等（基于 TCR）；**加载开销**：○（主要瓶颈是 SQL 与 tensor 之间的 irregularity / loop gap，而非 QRAM）；**计算原生性**：√

   
3. **Qymera: Simulating Quantum Circuits using RDBMS (SIGMOD-Companion 2025)**
   *Littau & Hai, Qymera: Simulating Quantum Circuits using RDBMS, SIGMOD-Companion 2025.* [[DOI](https://doi.org/10.1145/3722212.3725126)]
   - **数据模型**：关系表（量子线路/门/状态以表形式存储）
   - **索引结构**：○（复用 RDBMS 表与查询优化；未强调专用索引）；**数据规模**：按量子线路/qubits 计；前期实验中 2GB 内存下稀疏线路可比常规方法多至 3118× qubits；**量子态表示**：状态向量幅值表（s,r,i）+ 门矩阵表；量子门序列翻译为 SQL
   - **查询算子**：非传统 σ/π/⋈；支持量子门应用、状态演化、benchmark/方法比较；**执行模式**：经典 RDBMS 原生执行：线路→SQL→RDBMS；**硬件依赖**：经典 RDBMS / CPU；**加载开销**：○（需 circuit→SQL translation；非 QRAM）；**计算原生性**：√（状态演化直接在 RDBMS 中完成）
   - **优化目标**：以声明式 SQL 执行量子线路仿真；便于 benchmarking / 教学 / 开发；**调度能力**：○（Method Selector 在 SQL/StateVec/LIMDD/MPS 间切换比较）；**真实DB集成**：√（直接以 RDBMS 为执行后端）；**验证平台**：RDBMS backend；并与 StateVec / LIMDD / MPS 等模拟方法比较；**工程成熟度**：中
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：高

4. **Is Quantum-Based SQL Query Execution Viable? (QDSM’24)**
   *Kesarwani & Haritsa, Is Quantum-Based SQL Query Execution Viable?, VLDB QDSM’24.*[[project](https://www.ifis.uni-luebeck.de/~groppe/qdsm/?page=paper&year=2024&paperid=p5)]
   - **数据模型**：关系模型（SQL 查询执行）
   - **索引结构**：○（强调经典后处理用 lightweight index lookups 去假阳性）；**数据规模**：TPCH Q3 级查询示例（未给具体行数）；**量子态表示**：电路模型；Grover oracle；容错阈值 λ；输出含假阳/假阴
   - **查询算子**：σ, ⋈, ∪, ∩, −, Sort；并讨论 Grover/QFT 等可能加速点；**执行模式**：混合量子-经典（quantum engine + classical post-validation；quantum sentinel 决策路径）；**硬件依赖**：门模型量子电路处理器（如 Qiskit 平台）；**加载开销**：√（经典数据→qubits/QRAM/编码为核心挑战）；**计算原生性**：○
   - **优化目标**：降低非索引选择/连接等算子复杂度；在 λ 下权衡质量/代价；**调度能力**：○（quantum sentinel/参数自适应）；**事务ACID**：○（专章讨论量子计算对 ACID 的影响与新 contract）；**真实DB集成**：—（vision/workshop，未给完整系统实现）；**验证平台**：—（概念性；讨论平台如 Qiskit / circuit processors）；**工程成熟度**：低
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：中

5. **Query Processing on Tensor Computation Runtimes (TQP, PVLDB 2022)**
   *He et al., Query Processing on Tensor Computation Runtimes, PVLDB 15(11) 2022, 10.14778/3551793.3551833.*
   - **数据模型**：关系模型（SQL→关系代数）
   - **索引结构**：—（重点在执行引擎/算子映射，而非索引）；**数据规模**：运行完整 TPC-H（22 queries）；**量子态表示**：张量（dense tensors）作为数据表示；tensor ops 组合实现关系算子
   - **查询算子**：覆盖常见关系算子（filter/project/join/agg/sort 等，映射到 tensor ops）；**执行模式**：混合：SQL 编译为 tensor program；在 TCR（PyTorch/TVM/ONNX Runtime）上执行（eager/graph）；**硬件依赖**：多硬件：CPU、离散/集成 GPU、TPU、浏览器等（TCR backends）；**加载开销**：○（需将列数据转为 tensor；但复用 TCR 运行时/编译器）；**计算原生性**：√（张量算子原生可调度到异构硬件）
   - **优化目标**：性能：TPC-H 查询最高 10× 加速；ML+SQL 端到端最高 9× 加速；**调度能力**：○（利用 TCR 的编译/调度与 kernel 优化）；**真实DB集成**：—（原型 query processor，而非完整 RDBMS 集成）；**验证平台**：PyTorch/TVM/ONNX Runtime；CPU/GPU/TPU 等；**工程成熟度**：中
   - **关系模型适配**：高；**机器学习结合**：高（支持 ML+SQL 混合查询）；**张量网络表示**：中（张量计算运行时）；**计算原生性（综合）**：高

<a id="query-theory-foundations"></a>
## 查询理论基础

提供查询表示、超图与 FAQ 框架等理论基础。

[**⬆️返回目录**](#toc)

1. **FAQ: Questions Asked Frequently (arXiv 2016)**
   *Abo Khamis, Ngo & Rudra, FAQ: Questions Asked Frequently, arXiv:1504.04044v5, 2016.*
   - **数据模型**：关系查询 / 函数聚合 / 超图模型（joins, MAP, matrix ops, logic）
   - **数据规模**：以因子/超边规模 N 与输出大小 Z 衡量；通用于 joins、PGM、matrix chain、DFT 等
   - **查询算子**：joins、聚合、MAP、#CQ/#QCQ、矩阵链乘、DFT 等统一为 FAQ；**执行模式**：经典执行：InsideOut / variable elimination / dynamic programming；**硬件依赖**：经典 CPU / 理论算法；**加载开销**：○（讨论 listing representation / oracle access；非 QRAM）；**计算原生性**：√（直接在 FAQ 表达/因子表示上计算）
   - **优化目标**：最小化 variable ordering 的 fractional FAQ-width；统一多类查询推理任务；**调度能力**：√（变量消元顺序 / variable ordering 属核心“调度”）；**真实DB集成**：○（文中指出已在 LogicBlox 实现 InsideOut）；**验证平台**：LogicBlox implementation + 理论分析；**工程成熟度**：高
   - **关系模型适配**：高；**机器学习结合**：○（覆盖 PGM / graphical models 等 ML 相关推理）；**张量网络表示**：低（非张量网络；但覆盖 matrix/tensor-like contraction 形式）；**计算原生性（综合）**：高

<a id="quantum-augmented-query-optimization"></a>
## 量子增强优化查询

关注 join ordering 等优化问题上的量子增强方法。

[**⬆️返回目录**](#toc)

1. **Q2O: Quantum-augmented Query Optimizer (PVLDB 2025 demo)**
   *Liu et al., PVLDB 18(12) 2025, 10.14778/3750601.3750691.* [[Code](https://github.com/ihanwen99/Q2O)]
   - **数据模型**：关系查询优化（Join Ordering）
   - **数据规模**：JOB workload；量子求解器生成 join order hint；relations<15 用 CQM，否则 NL-Encoding；**量子态表示**：D-Wave hybrid solvers：CQM / NL-Encoding（内部 DAG 并发评估 join orders）
   - **查询算子**：—（输出 join order hint；PostgreSQL 负责其余优化与执行）；**执行模式**：混合量子-经典：D-Wave 求 JO → hint → PostgreSQL 生成/执行计划；**硬件依赖**：量子退火（D-Wave hybrid solvers）；**加载开销**：—（主要加载基数/选择率/代价函数，不加载 payload）；**计算原生性**：√
   - **优化目标**：生成更优 join 顺序；报告最高 13× query execution speedup；**真实DB集成**：√（集成 PostgreSQL，planning 阶段注入 plan hint）；**验证平台**：D-Wave hybrid solvers + PostgreSQL；**工程成熟度**：中
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：高

2. **Join Order Optimisation on Quantum Hardware (PVLDB 2022)**
   *Schönberger et al., PVLDB 15(1) 2022.* [[Code](https://github.com/lfd/VLDB23/)]
   - **数据模型**：关系查询优化（Join Ordering）
   - **数据规模**：真实硬件评估：3–5 relations（D-Wave）；更大规模需嵌入大量物理 qubits；**量子态表示**：QUBO/Ising 映射到 qubits；gate-based/QAOA 与退火比较
   - **查询算子**：—（优化器子任务：join 顺序；非直接 SQL 算子执行）；**执行模式**：混合量子-经典（优化子问题上 QPU；其余经典）；**硬件依赖**：NISQ QPU（gate-based + quantum annealing；IBM/Rigetti/D-Wave 等）；**加载开销**：—（不加载 payload；主要加载代价模型/阈值离散等）；**计算原生性**：√
   - **优化目标**：最小化 join plan cost；权衡解质量与可嵌入规模；**真实DB集成**：○（提出 co-design/co-processor 设想）；**验证平台**：D-Wave / gate-based 实验/仿真；Qiskit 等工具链；**工程成熟度**：低-中
   - **关系模型适配**：高；**机器学习结合**：低；**张量网络表示**：低；**计算原生性（综合）**：高

<a id="hybrid-sampling-aqp"></a>
## 混合采样AQP框架

把量子计算引入近似查询处理与混合采样框架。

[**⬆️返回目录**](#toc)

1. **When Quantum Computing Meets Database: A Hybrid Sampling Framework for Approximate Query Processing (TKDE 2024)**
   *Wu et al., When Quantum Computing Meets Database: A Hybrid Sampling Framework for Approximate Query Processing, IEEE TKDE 36(12):9532–9545, 2024.* [[DOI](https://doi.org/10.1109/TKDE.2024.3480278)]
   - **数据模型**：关系查询（SPJ + GROUP BY 的 AQP）
   - **数据规模**：真实数据集：flight records、police road stops；IBM Qiskit + ibm_brisbane；**量子态表示**：QRAM + amplitude amplification / diffusion gate；rare groups 放大
   - **查询算子**：近似聚合/AQP（COUNT/SUM/AVG 等），面向高选择率与长尾 group；**执行模式**：混合量子-经典：经典采样识别 rare groups，量子采样放大，再做结果校正；**硬件依赖**：门模型量子计算（Qiskit 模拟器 + IBM Brisbane 真机）；**加载开销**：√（需 QRAM/量子编码；强调无需预处理但存在放大轮数与校正代价）；**计算原生性**：○

<a id="quantum-annealing-cloud-scheduling"></a>
## 云资源分配量子退火

将量子退火用于任务、虚机与资源调度问题。

[**⬆️返回目录**](#toc)

1. **Opportunities for Quantum Acceleration of Databases (PVLDB 2023)**
   *Çalıkyılmaz et al., PVLDB 16(9) 2023, 10.14778/3598581.3598603; artifacts:.* [[Code](https://github.com/TobiasWinker/QC4DB_VQC_Tutorial)]
   - **数据模型**：关系查询优化 + 事务调度（综述/规模分析）
   - **数据规模**：以参数规模描述：n tables；t transactions、c cores（非固定行数实验）；**量子态表示**：QUBO/Ising、gate-based/VQC、QA 等模型与资源需求综述
   - **查询算子**：—（优化/调度为主，不是具体 SQL 算子实现）；**执行模式**：混合量子-经典（将难子任务卸载到 QPU）；**硬件依赖**：gate-based + quantum annealing；讨论 NISQ、5000+ qubits QA 等；**加载开销**：—（强调 on-site QPU 可降低数据传输；未给数据装载方案细节）；**计算原生性**：○
   - **优化目标**：查询优化（JO/MQO）与事务调度（makespan/throughput）加速机会与挑战；**调度能力**：√（事务调度/资源调度）；**事务ACID**：√（事务调度与 ACID/隔离开销关联）；**真实DB集成**：—（survey，非系统集成）；**验证平台**：Qiskit/Cirq/Pennylane 等库；D-Wave/IBM 等平台（综述）；**工程成熟度**：中
   - **关系模型适配**：中；**机器学习结合**：○（提及 ML/heuristics 与量子方案对比）；**张量网络表示**：低；**计算原生性（综合）**：中

2. **Quantum Annealing Method for Dynamic Virtual Machine and Task Allocation in Cloud Infrastructures from Sustainability Perspective (ICDEW 2023)**
   *Uotila & Lu, Quantum Annealing Method for Dynamic Virtual Machine and Task Allocation in Cloud Infrastructures from Sustainability Perspective, ICDEW 2023.* [[DOI](https://doi.org/10.1109/ICDEW58674.2023.00023)]
   - **数据模型**：云基础设施调度/资源分配（任务—虚机—物理机）
   - **数据规模**：CloudSim + PlanetLab workloads（仿真工作流）；**量子态表示**：QUBO 二次无约束二元优化；xt,v,m 分配变量
   - **查询算子**：—（非 SQL 执行；优化子任务为 VM / task allocation）；**执行模式**：混合量子-经典：经典云调度流程 + D-Wave QA 求解分配；**硬件依赖**：量子退火（D-Wave hybrid/annealer）+ CloudSim；**加载开销**：○（主要加载资源需求/MIPS/可持续性指标，不加载数据 payload）；**计算原生性**：√

<a id="tensor-network-computation"></a>
## 张量网络计算

涵盖 TT/MPS/HiCOO/hypertrie 等张量表示、压缩与计算工作。

[**⬆️返回目录**](#toc)

1. **Approximating Tensor Network Contraction with Sketches (arXiv 2026)**
   *Heddes et al., Approximating Tensor Network Contraction with Sketches, arXiv:2603.07387v1, 2026.*
   - **数据模型**：张量网络 / join-size estimation / graphical models
   - **压缩存储**：○（sketching / dimensionality reduction 用于近似 contraction）；**数据规模**：任意 cyclic/acyclic tensor networks；复杂度按 contractions 数与 sketch size 表示；**量子态表示**：—（经典张量网络，不是量子态存储）
   - **查询算子**：tensor network contraction；多重 join size estimation 为其特例；**执行模式**：经典近似执行：sketch-based ATNC；**硬件依赖**：经典 CPU / sketching；**加载开销**：○（通过 sketches 缩小计算规模；不讨论数据库装载）；**计算原生性**：√（直接在 tensor network contraction 上近似计算）
   - **优化目标**：近似任意 TNC（含 cyclic）；并为 acyclic TNC 给出仅多项式依赖 contractions 数量的方法；**验证平台**：理论算法（classical experiments / analysis）；**工程成熟度**：低-中
   - **关系模型适配**：低；**机器学习结合**：○（应用面覆盖 ML / probability / quantum simulation）；**张量网络表示**：高；**计算原生性（综合）**：高

2. **On the Optimal Linear Contraction Order of Tree Tensor Networks, and Beyond (arXiv 2024)**
   *Stoian, Milbradt & Mendl, On the Optimal Linear Contraction Order of Tree Tensor Networks, and Beyond, arXiv:2209.12332v5, 2024.*
   - **数据模型**：树形/一般张量网络
   - **数据规模**：以 n 个 tensors 的 contraction ordering 为规模；树网络可多项式最优，一般网络用启发式；**量子态表示**：tensor network contraction tree；线性/一般 contraction order
   - **查询算子**：—（非 SQL；核心是 contraction ordering，与数据库 join ordering 对应）；**执行模式**：经典优化：TensorIKKBZ（最优线性顺序）+ LinDP（一般顺序近最优）；**硬件依赖**：经典 CPU / 理论算法；**计算原生性**：√（直接产出可执行的 contraction order / tree）
   - **优化目标**：最小化累计 contraction cost C；树网络线性顺序最优，多拓扑给出近最优启发式；**调度能力**：√（核心即 contraction / join ordering 调度）；**验证平台**：理论算法 + 实验评估；**工程成熟度**：中-高
   - **关系模型适配**：低；**机器学习结合**：○（适用于 quantum circuit simulation、图模型与张量计算背景）；**张量网络表示**：高；**计算原生性（综合）**：高

3. **Optimizing Tensor Programs on Flexible Storage (arXiv 2022)**
   *Schleich, Shaikhha & Suciu, Optimizing Tensor Programs on Flexible Storage, arXiv:2210.06267v1, 2022.*
   - **数据模型**：张量程序（dense/sparse vectors, matrices, higher-order tensors）
   - **压缩存储**：√（支持 COO/CSR/自定义 flexible storage mappings）；**索引结构**：√（用户可声明式定义 storage mapping / memory layout）；**数据规模**：多个 tensor kernels；以系统实验对比 Taco / DuckDB 等为主，非固定行数规模；**量子态表示**：—（经典 tensors）
   - **查询算子**：tensor programs / tensor kernels（如 MTTKRP 等）；通过 declarative tensor calculus 表达；**执行模式**：经典 cost-based optimizer；program 与 storage mappings 联合优化；**硬件依赖**：经典 CPU / Julia 执行 + Egg equality saturation 重写引擎；**加载开销**：○（关注 memory layout / storage mappings 对执行代价的影响，而非 QRAM）；**计算原生性**：√（program + storage mapping 直接编译执行）
   - **优化目标**：依据 storage layout 与统计信息优化 tensor plan；提升 locality、减少 intermediates；**调度能力**：√（cost-based rewrite / factorization / loop fusion / join reordering）；**真实DB集成**：—（系统原型，不是完整关系数据库）；**验证平台**：Julia + Egg；实验对比 Taco 与 DuckDB；**工程成熟度**：高
   - **关系模型适配**：低；**机器学习结合**：○（面向 ML / tensor pipelines 的系统优化）；**张量网络表示**：低（关注 tensor programs / storage，而非张量网络）；**计算原生性（综合）**：高

4. **ALTO: Adaptive Linearized Storage of Sparse Tensors (ICS 2021)**
   *Helal et al., ALTO: Adaptive Linearized Storage of Sparse Tensors, ICS 2021.* [[DOI](https://doi.org/10.1145/3447818.3461703)]
   - **数据模型**：稀疏高阶张量（3D/4D+；mode-agnostic）
   - **压缩存储**：√（adaptive bit encoding + linearized layout 压缩元数据）；**索引结构**：√（线性化索引元数据 + partitions；非传统 B+ 树）；**数据规模**：13 个真实稀疏张量；含 billions 级非零元数据集
   - **查询算子**：MTTKRP / all-modes tensor decomposition（CPD 核心算子）；**执行模式**：经典并行稀疏张量执行；**硬件依赖**：多核 CPU；**加载开销**：○（讨论 format generation time，且显著低于先前压缩格式）；**计算原生性**：√
   - **优化目标**：同时优化 locality、memory footprint、workload balance、同步开销；**调度能力**：√（自适应同步 + perfectly balanced partitions）；**验证平台**：multicore CPU（ICS’21 实验环境）；**工程成熟度**：中-高
   - **关系模型适配**：低；**机器学习结合**：中（面向 data mining / ML / HPC 张量分解）；**张量网络表示**：低（不是 MPS/PEPS 类张量网络）；**压缩比**：4.3×（相对最佳 mode-specific 格式几何平均压缩比）；**计算原生性（综合）**：高

5. **TT-Rec: Tensor Train Compression for DLRM Embeddings (MLSys 2021)**
   *Yin et al., TT-Rec: Tensor Train Compression for Deep Learning Recommendation Model Embeddings (MLSys 2021).* [[Code](https://github.com/facebookresearch/FBTT-Embedding)]
   - **数据模型**：—（DL 推荐模型 embedding tables）
   - **压缩存储**：√（Tensor Train 分解压缩 embedding tables）；**数据规模**：embedding tables 从 tens of GB 到 TB；评测：Criteo Kaggle/Terabyte；**量子态表示**：TT（Tensor Train）张量网络/序列矩阵乘积（经典）
   - **查询算子**：embedding lookup（EmbeddingBag）+ TT-core 乘法；缓存加速；**执行模式**：经典（GPU/CPU）训练；TT-EmbeddingBag kernel + caching；**硬件依赖**：GPU（cuBLAS batched GEMM）/ 加速器；**加载开销**：—（模型权重已在 TT-core/缓存中）；**计算原生性**：√（TT 表示直接用于计算 lookup）
   - **优化目标**：压缩比：Kaggle 4×–221×（精度损失 0.03%–0.3%）；Terabyte 112× 且无精度/训练开销损失；**验证平台**：GPU + cuBLAS；开源实现；**工程成熟度**：中
   - **关系模型适配**：低；**机器学习结合**：高（推荐模型）；**张量网络表示**：高（TT 属张量网络）；**压缩比**：4×–221×（Kaggle）；112×（Terabyte）；**计算原生性（综合）**：高

6. **Tentris – A Tensor-Based Triple Store (ISWC 2020)**
   *Bigerl et al., Tentris – A Tensor-Based Triple Store (ISWC 2020); code+data:.* [[Project](https://tentris.dice-research.org/iswc2020)]
   - **数据模型**：RDF 知识图谱（Triple Store）；SPARQL
   - **压缩存储**：○（hypertrie 统一多索引，减少冗余）；**索引结构**：√（hypertrie：统一多索引的数据结构）；**数据规模**：最多约 10^9 triples（文中三数据集）；**量子态表示**：稀疏三阶张量（order-3；Boolean tensor 表示 RDF）
   - **查询算子**：SPARQL 基本图模式(BGP)+投影（与同类工作一致的片段）；**执行模式**：经典：SPARQL→Einstein Summation；在线决定张量运算顺序；**硬件依赖**：CPU 内存（in-memory）；**加载开销**：—（图数据已在内存张量结构中）；**计算原生性**：√（原生以张量运算执行查询）
   - **优化目标**：提升 QPS：实验中≥1.8×（对比多种 triple store）；**调度能力**：○（在线选择张量运算/连接顺序）；**真实DB集成**：—（独立 triple store 实现）；**验证平台**：in-memory hypertrie（通用 CPU 平台）；**工程成熟度**：中
   - **关系模型适配**：中（非关系模型，RDF/SPARQL）；**机器学习结合**：低；**张量网络表示**：低（张量代数≠张量网络）；**计算原生性（综合）**：高

7. **Efficient Contraction of Large Tensor Networks for Weighted Model Counting through Graph Decompositions**
   *Dudek, Dueñas-Osorio & Vardi, Efficient Contraction of Large Tensor Networks for Weighted Model Counting through Graph Decompositions, arXiv:1908.04381v2, 2020.* [[Paper](https://arxiv.org/abs/1908.04381)]
   - **数据模型**：张量网络 / 因子图 / project-join 对应的约束计数模型
   - **压缩存储**：○（FT 用 Hierarchical Tucker 预分解高阶结构张量）；**索引结构**：○（tree decomposition / carving decomposition 用于 contraction-order 组织）；**数据规模**：面向 large industrial formulas 与标准 WMC benchmarks（非关系行数型规模）；**量子态表示**：—（经典张量，不涉及量子态存储）
   - **查询算子**：非 SQL；weighted model counting / project-join via contraction；**执行模式**：经典 tensor-network contraction + graph decomposition heuristic；**硬件依赖**：经典 CPU；调用 heuristic tree-decomposition solvers 与 tensor libraries；**计算原生性**：√
   - **优化目标**：优化 contraction order / max rank / memory efficiency；提升 WMC 效率；**调度能力**：√（通过 contraction tree / LG / FT 决定收缩顺序）；**验证平台**：TensorOrder 原型 + heuristic tree-decomposition solvers；**工程成熟度**：中
   - **关系模型适配**：低；**机器学习结合**：○（面向 AI / probabilistic reasoning，但非 ML 训练系统）；**张量网络表示**：高（tensor network contraction 是核心）；**计算原生性（综合）**：高

8. **A Tensor Based Data Model for Polystore: An Application to Social Networks Data**
   *Leclercq & Savonnet, A Tensor Based Data Model for Polystore: An Application to Social Networks Data, arXiv:1806.09967v1, 2018.* [[Paper](https://arxiv.org/abs/1806.09967)]
   - **数据模型**：多模型/多范式存储：关系、图、文档、键值、矩阵/时间序列
   - **压缩存储**：○（张量作为 pivot model；重点是逻辑独立与模型桥接而非压缩）；**索引结构**：√（typed associative arrays 作为各维索引）；**数据规模**：Twitter 2017 法国总统选举社交网络案例（规模未以统一行数给出）
   - **查询算子**：project/select、slice/fiber、tensor construction / transformation；支持 CPD / Tucker 分析流程；**执行模式**：经典 polystore + mediator/wrapper 架构；**硬件依赖**：Spark SQL / R；连接 JDBC、JSON、Parquet、Neo4j、Mongo、Cassandra、HBase 等；**加载开销**：○（强调以 tensor pivot 降低 ETL / model transformation 成本）；**计算原生性**：○（tensor 作为分析 pivot，而非完整原生执行引擎）
   - **优化目标**：统一多数据模型、减少模型转换与 ETL、实现逻辑数据独立；**调度能力**：○（mediator/wrapper 协调跨源构造；非系统级优化调度器）；**真实DB集成**：○（通过 wrappers 连接多存储系统，但非单一 DBMS 内核集成）；**验证平台**：R packages + Spark SQL/DataFrame/RDD + 多源 wrappers；**工程成熟度**：中
   - **关系模型适配**：中（桥接 relational / document / graph / key-value）；**机器学习结合**：中（服务于 PageRank、community detection、TF-IDF/SVD、HITS 等分析）；**张量网络表示**：中（使用 tensor / CPD / Tucker，但非量子 TN）；**计算原生性（综合）**：中

9. **HiCOO: Hierarchical Storage of Sparse Tensors (SC18 paper)**
   *Li et al., HiCOO: Hierarchical Storage of Sparse Tensors, SC18 2018 (IEEE).* [[Code](https://github.com/hpcgarage/ParTI)]
   - **数据模型**：稀疏张量（多维数组）
   - **压缩存储**：√（压缩坐标/索引：块化 + element offsets）；**索引结构**：√（block indices + element indices + bptr/lptr；两级 blocking）；**数据规模**：12 个 3D/4D 稀疏张量；最高约 140M nonzeros（如 deli4d）；**量子态表示**：—（经典张量存储格式；非量子态）
   - **查询算子**：支持 MTTKRP/CPD 核心算子（张量分解）；**执行模式**：经典多核并行（superblock scheduler）；**硬件依赖**：CPU multicore（实验至 56 threads）；**加载开销**：○（COO→HiCOO：Z-order sorting + partition + compression）；**计算原生性**：√
   - **优化目标**：减少存储字节 & 提升局部性：MTTKRP 平均 6.8×（最高 23×）快于 COO；并对 CPD 加速；**调度能力**：√（superblock scheduling/并行粒度）；**验证平台**：多核 CPU（单机并行）；ParTI!/SPLATT 相关；**工程成熟度**：中
   - **关系模型适配**：低；**机器学习结合**：中（张量分析/分解常用于数据挖掘/ML）；**张量网络表示**：低；**压缩比**：最多约 2.5× 少于 COO（索引更紧凑）；**计算原生性（综合）**：高

10. **HiCOO (SC18 slides / talk deck)**
   *Li et al., HiCOO SC18 slides (pap511s5.pdf).* [[Code](https://github.com/hpcgarage/ParTI)]
   - **数据模型**：稀疏张量（多维数组）
   - **压缩存储**：√（强调 index compression + data locality）；**索引结构**：√（展示 block/superblock 结构与参数 αb,L,B）；**数据规模**：3D/4D tensors（nell2, choa, darpa, fb-m, fb-s, deli, nips, enron, flickr, deli4d 等）
   - **查询算子**：MTTKRP/CPD（slides 展示 speedup 与 thread scalability）；**执行模式**：经典并行（superblock scheduler；SIMD 优化）；**硬件依赖**：CPU multicore + SIMD；**加载开销**：○（Z-order sorting、index compression、SIMD 分解贡献）；**计算原生性**：√
   - **优化目标**：性能分解：Z-order sorting / compression / SIMD 贡献；强调可扩展性；**调度能力**：√（thread scalability）；**验证平台**：CPU multicore + ParTI! 代码库；**工程成熟度**：中
   - **关系模型适配**：低；**机器学习结合**：中；**张量网络表示**：低；**计算原生性（综合）**：高

12. **Matrix Product State for Higher-Order Tensor Compression and Classification**
   *Bengua et al., Matrix Product State for Higher-Order Tensor Compression and Classification (TensorCompression.pdf).*
   - **数据模型**：张量数据（高阶）
   - **压缩存储**：√（MPS/TT 将高阶张量压缩为核心矩阵特征）；**数据规模**：示例：COIL-100 32×32×3（训练/测试划分）；特征数 Nf=Δ_{n-1}Δ_n 可控；**量子态表示**：MPS / TT（张量网络）
   - **查询算子**：SVD sweep；bond dimension 控制；用于分类（KNN 等）；**执行模式**：经典执行（量子启发的张量网络分解）；**硬件依赖**：无量子硬件（经典线性代数）；**加载开销**：○（reshape/permutation；未单独量化）；**计算原生性**：○
   - **优化目标**：降低计算/提高分类；避免 ALS 局部最优；以阈值 ε 控制保真/PSNR；**工程成熟度**：中
   - **关系模型适配**：低；**机器学习结合**：高（监督学习/分类）；**张量网络表示**：高；**压缩比**：示例：3072→432（ε=0.9，≈7.1×）；3072→18（ε=0.65，≈171×）；**计算原生性（综合）**：中

11. **Hand-waving and Interpretive Dance: An Introductory Course on Tensor Networks**
   *Bridgeman & Chubb, Hand-waving and Interpretive Dance: An Introductory Course on Tensor Networks, arXiv:1603.03039v4, 2017.* [[Paper](https://arxiv.org/abs/1603.03039)]
   - **数据模型**：张量网络教程（量子多体态 / MPS / PEPS / MERA）
   - **压缩存储**：√（以低 bond dimension 的 TN 表示缓解 Hilbert 空间指数爆炸）；**数据规模**：教程/方法综述级；覆盖 1D/2D many-body systems（非统一数据行数基准）；**量子态表示**：纯态/算符的张量网络表示；MPS、PEPS、MERA、PEPO/MPO
   - **查询算子**：非 SQL；tensor product、trace、contraction、SVD truncation、DMRG、TEBD；**执行模式**：经典张量网络数值方法 / 变分算法；**硬件依赖**：经典 CPU / 线性代数环境（讲义未绑定特定硬件）；**加载开销**：○（讨论 contraction complexity 与表示成本，但非数据库装载问题）；**计算原生性**：√
   - **优化目标**：缓解维数灾难；高效表示量子多体态、相分类与低能态计算；**调度能力**：○（讨论 contraction / bubbling / computational complexity，不是系统级调度器）；**验证平台**：—（lecture notes / course material）；**工程成熟度**：低（教程/讲义）
   - **关系模型适配**：低；**机器学习结合**：低；**张量网络表示**：高（系统覆盖 MPS / PEPS / MERA / PEPO）；**计算原生性（综合）**：高

13. **Tensor-Train Decomposition (SIAM J. Sci. Comput. 2011)**
   *Oseledets, Tensor-Train Decomposition, SIAM J. Sci. Comput. 33(5):2295–2317, 2011.* [[DOI](https://doi.org/10.1137/090752286)]
   - **数据模型**：高维张量/矩阵
   - **压缩存储**：√（TT-format 以低参数 cores 压缩高维张量）；**数据规模**：示例达 19 维算子；理论目标维度可达 10/100/1000；**量子态表示**：TT-format / MPS（线性张量网络；三阶 cores）
   - **查询算子**：基本线性代数：TT-SVD、TT-rounding、加法、Hadamard/内积、矩阵-向量乘；**执行模式**：经典数值计算（TT cores 上直接运算）；**硬件依赖**：无量子硬件（经典 SVD/QR 数值线代）；**加载开销**：○（需要 unfolding / reshape 与截断 SVD，但不涉及数据库装载）；**计算原生性**：√


<a id="quantum-inspired-ml"></a>
## 量子启发机器学习

关注量子启发算法与低秩/采样思想对数据系统的影响。

[**⬆️返回目录**](#toc)

1. **A quantum-inspired classical algorithm for recommendation systems**
   *Ewin Tang, A quantum-inspired classical algorithm for recommendation systems, arXiv:1807.04271v3, 2019.* [[Paper](https://arxiv.org/abs/1807.04271)]
   - **数据模型**：用户-物品偏好矩阵（低秩推荐系统）
   - **压缩存储**：○（利用低秩近似/子采样，不是存储压缩系统）；**索引结构**：√（支持 ℓ2-norm sampling 的动态数据结构）；**数据规模**：一般 m×n 偏好矩阵；秩 k；理论复杂度 poly(k)·log(mn)；**量子态表示**：以 ℓ2-norm sampling 分布充当 quantum superposition 的经典对应物
   - **查询算子**：推荐样本生成 / 从低秩近似行分布采样；**执行模式**：纯经典、量子启发式（对标量子推荐算法）；**硬件依赖**：经典 RAM + sampling data structure；**加载开销**：√（输入必须在支持 ℓ2-norm sampling 的数据结构中）；**计算原生性**：○（依赖 sampling-oracle / data structure，而非原生 DB 存储）
   - **优化目标**：证明量子推荐并无指数优势；以近似低秩采样实现快速推荐；**验证平台**：理论工作（无真实 DBMS 集成）；**工程成熟度**：低
   - **关系模型适配**：低；**机器学习结合**：高（推荐系统 / QML 对比分析）；**张量网络表示**：低；**计算原生性（综合）**：中
