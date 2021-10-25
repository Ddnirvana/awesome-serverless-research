# Awesome Serverless Research
A curated list of awesome serverless research works, including papers and open-sourced projects.

If you find some interesting work/projects missing in this list, please contact me through issues or email (dd_nirvana@sjtu.edu.cn) :)


## Contents
- [Review](#review)
- [Serverless System and Framework](#serverless-system-and-framework)
- [Optimizations](#optimizations)
- [Stateful serverless computing](#stateful-serverless-computing)
- [Benchmarking](#benchmarking)
- [Reliability and Fault Tolerance](#reliability-and-fault-tolerance)
- [Security](#security)
- [Applications](#applications)
- [Programming Models](#programming-models)
- [Other Related Works](#other-related-works)
- [Other Recommended Lists](#other-recommended-lists)

## Review
- [Serverless Computing: One Step Forward, Two Steps Back (CIDR‘19)](http://cidrdb.org/cidr2019/papers/p119-hellerstein-cidr19.pdf)
- [Cloud Programming Simplified: A Berkeley View onServerless Computing (Technique Report 2019)](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2019/EECS-2019-3.pdf)

## Serverless System and Framework
- (Storage system) [Understanding Ephemeral Storage for Serverless Analytics （ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277431)
- (Storage system) [Pocket: Elastic Ephemeral Storage for Serverless Analytics (OSDI'18)](https://dl.acm.org/doi/10.5555/3291168.3291200)
- (Scheduling/Complier) [From Laptop to Lambda: Outsourcing Everyday Jobs to Thousands of Transient Functional Containers (ATC'19)](https://dl.acm.org/doi/10.5555/3358807.3358848)
- (Runtime) [Firecracker: Lightweight Virtualization for Serverless Applications (NSDI'20)](https://www.usenix.org/system/files/nsdi20-paper-agache.pdf)
- (Runtime) [Faasm: Lightweight Isolation for Efficient Stateful Serverless Computing (ATC'20)](https://www.usenix.org/conference/atc20/presentation/shillaker) - Compared with other runtimes, Faasm utilizes WebAssembly for isolation, which achieves high performance. Code available at [github](https://github.com/faasm/faasm)
- (Framework) [Nightcore: Efficient and Scalable Serverless Computing for Latency-Sensitive, Interactive Microservices (ASPLOS'21)](https://www.cs.utexas.edu/~zjia/asplos21main-p89-final.pdf)
- (Scheduling)[Sequoia: enabling quality-of-service in serverless computing(SOCC'20)](https://dl.acm.org/doi/10.1145/3419111.3421306) - Sequoia is a serverless scheduling and allocation framework, which aims to improve the management in serverless computing.

## Optimizations
- [SOCK: Rapid Task Provisioning with Serverless-Optimized Containers (ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277362)
- [SAND: Towards High-Performance Serverless Computing (ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277444)
- [Catalyzer: Sub-millisecond Startup for ServerlessComputing with Initialization-less Booting (ASPLOS'20)](https://dl.acm.org/doi/10.1145/3373376.3378512) - Catalyzer proposes init-less, which leverages fork/snapshots to skip the initialization costs during startup, and can achieve <1ms startup latency in the best case. The system is based on virtualization based sandboxes, gVisor.
- [Replayable Execution Optimized for Page Sharing for a Managed Runtime Environment (Eurosys'19)](https://dl.acm.org/doi/abs/10.1145/3302424.3303978) - Replayable optimizes CRIU for docker containers to boost container startup latency and reduce memory costs.
- [SEUSS: skip redundant paths to make serverless fast (Eurosys'20)](https://dl.acm.org/doi/abs/10.1145/3342195.3392698) - SEUSS utilizes similir ideas as Catalyzer and Replayable to boost serverless latency (especially for startup latency) using fork/snapshots. The system is based on unikernels.
- [FaasCache: Keeping Serverless Computing Alive with Greedy-Dual Caching (ASPLOS'21)](http://homes.sice.indiana.edu/prateeks/papers/faascache-asplos21.pdf)
- [Faastlane: Accelerating Function-as-a-Service Workflows (ATC'21)](https://www.usenix.org/conference/atc21/presentation/kotni) - Faastlane aims to optimize the communication latency between functions, which is significant for function chain (or workflows in the title). The major idea is to use thread-level isolation, that means different functions are located in the same process, and Faastlane utilizes Intel MPK to provide isolation between different threads.

## Stateful serverless computing

There are many emerging works trying to introduce states to serverless computings --- therefore, we can have more applications like machine learning and data analysis on serverless.

- [Boki: Stateful Serverless Computing with Shared Logs(SOSP'21)](https://www.cs.utexas.edu/~zjia/boki-sosp21.pdf) - Boki solves many problems on stateful serverless computing, including state consistency, fault tolerance, and high-level abstractions for stateful serverless applications. The major novelity is its shared log design. The system is open-sourced at [github](https://github.com/ut-osa/boki). And you can quickly learn the high-level ideas through its [SOSP video](https://www.youtube.com/watch?v=SgfLK1p3dx4).



## Benchmarking
- [Architectural Implications of Function-as-a-Service Computing (Micro'19)](https://dl.acm.org/doi/10.1145/3352460.3358296)
- [Serverless in the Wild: Characterizing and Optimizing the Serverless Workload at a Large Cloud Provider (ATC'20)](https://www.usenix.org/conference/atc20/presentation/shahrad) - SIW is an industry paper by Microsoft Azure. You can learn about real-world issues/techniques of serverless computing from it.
- [Characterizing Serverless Platforms with ServerlessBench (SOCC'20)](https://dl.acm.org/doi/10.1145/3419111.3421280) - This paper presents ServerlessBench, which is the first and state-of-the-art serverless benchmarks. The benchmark suite is open-sourced at [github](https://github.com/SJTU-IPADS/ServerlessBench). The paper utilizes the benchmark suit to analyze several serverless platforms, including AWS lambda, OpenWhisk, Fn, and others, and proposes several new insights/implications that can lead future research works.
- [Benchmarking, Analysis, and Optimization of Serverless Function Snapshots (ASPLOS'21)](https://dl.acm.org/doi/10.1145/3445814.3446714) - This work introduces  one system and one optimization. The system is vHive, an open-source and full-stack serverless framework. The framework is built based on several state-of-the-art infastructure, e.g., Firecracker. Besides, the paper proposes an optimization, called REAP, which is a software mechanism for serverless hosts that records functions' stable working set of guest memory pages and proactively prefetches it from disk into memory.




## Reliability and Fault Tolerance
- [Fault-tolerant and transactional stateful serverless workflows (OSDI'20)](https://www.usenix.org/conference/osdi20/presentation/zhang-haoran) - The paper presents Beldi, a library and runtime system for writing fault-tolerant stateful serverless functions. Code available at [github](https://github.com/eniac/Beldi)
- [A fault-tolerance shim for serverless computing (Eurosys'20)](https://dl.acm.org/doi/10.1145/3342195.3387535) - The paper presents AFT, an atomic fault tolerance shim for serverless functions. AFT ensures atomic visibility of updates by enforcing read atomic isolation guarantee.
- [Formal Foundations of Serverless Computing (OOPSLA'19)](https://dl.acm.org/doi/10.1145/3360575) - It is the best paper of OOPSLA'19, which presents formal model to analyze (and prove) the reliability of serverless computing.

## Security
- [Peeking Behind the Curtains of Serverless Platforms (ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277369)
- [PIE: Confidential Serverless Made Efficient with Plug-In Enclaves (ISCA'21)](https://ipads.se.sjtu.edu.cn/zh/publications/LiISCA21.pdf) - The paper presents PIE, a hardware extension on SGX to boost startup latency of enclaves to support serverless computing.


## Applications
- [Shuffling, Fast and Slow: Scalable Analytics on Serverless Infrastructure (NSDI'19)](https://www.usenix.org/conference/nsdi19/presentation/pu) - This paper  presents Locus, a serverless analytics system combines cheap but slow storage with fast but expensive storage to balance performance and costs.
- [Sprocket: A Serverless Video Processing Framework (SOCC'18)](https://dl.acm.org/doi/10.1145/3267809.3267815) - This paper presents Sprocket, a configurable, stage-based, scalable, serverless video processing framework that exploits intra-video parallelism to achieve low latency.


## Programming Models
- [Kappa: a programming framework for serverless computing](https://dl.acm.org/doi/abs/10.1145/3419111.3421277) - Kappa proposes a new programming model for serverless computing, which utilizes *checkpointing* to support long running services, and reuse python features to manage concurrency. It is open-sourced at [kappa](https://kappa.cs.berkeley.edu) and [github-repo](https://github.com/NetSys/kappa).


## Other Related Works
- [E3: Energy-Efficient Microservices on SmartNIC-Accelerated Servers (ATC'19)](https://dl.acm.org/doi/10.5555/3358807.3358839)

## Other Recommended Lists
- [Awesome Serverless](https://github.com/anaibol/awesome-serverless) - A curated list of awesome services, solutions and resources for serverless / nobackend applications.
- [awesome-serverless-security](https://github.com/puresec/awesome-serverless-security) - A curated list of awesome serverless security resources such as (e)books, articles, whitepapers, blogs and research papers.

