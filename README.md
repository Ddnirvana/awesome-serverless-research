# Awesome Serverless Research
A curated list of awesome serverless research works, including papers and open-sourced projects.


## Contents
- [Review](#review)
- [Serverless System and Framework](#serverless-system-and-framework)
- [Optimizations](#optimizations)
- [Benchmarking](#benchmarking)
- [Reliability and Fault Tolerance](#reliability-and-fault-tolerance)
- [Security](#security)
- [Architecture Supports](#architecture-supports)
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

## Optimizations
- [SOCK: Rapid Task Provisioning with Serverless-Optimized Containers (ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277362)
- [SAND: Towards High-Performance Serverless Computing (ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277444)
- [Catalyzer: Sub-millisecond Startup for ServerlessComputing with Initialization-less Booting (ASPLOS'20)](https://dl.acm.org/doi/10.1145/3373376.3378512) - Catalyzer proposes init-less, which leverages fork/snapshots to skip the initialization costs during startup, and can achieve <1ms startup latency in the best case. The system is based on virtualization based sandboxes, gVisor.
- [Replayable Execution Optimized for Page Sharing for a Managed Runtime Environment (Eurosys'19)](https://dl.acm.org/doi/abs/10.1145/3302424.3303978) - Replayable optimizes CRIU for docker containers to boost container startup latency and reduce memory costs.
- [SEUSS: skip redundant paths to make serverless fast (Eurosys'20)](https://dl.acm.org/doi/abs/10.1145/3342195.3392698) - SEUSS utilizes similir ideas as Catalyzer and Replayable to boost serverless latency (especially for startup latency) using fork/snapshots. The system is based on unikernels.


## Benchmarking
- [Architectural Implications of Function-as-a-Service Computing (Micro'19)](https://dl.acm.org/doi/10.1145/3352460.3358296)
- [Serverless in the Wild: Characterizing and Optimizing the Serverless Workload at a Large Cloud Provider (ATC'20)](https://www.usenix.org/conference/atc20/presentation/shahrad)
- [Characterizing Serverless Platforms with ServerlessBench (SOCC'20)](https://dl.acm.org/doi/10.1145/3419111.3421280)
- Benchmarking, Analysis, and Optimization of Serverless Function Snapshots (ASPLOS'21)


## Reliability and Fault Tolerance
- [Fault-tolerant and transactional stateful serverless workflows (OSDI'20)](https://www.usenix.org/conference/osdi20/presentation/zhang-haoran) - The paper presents Beldi, a library and runtime system for writing fault-tolerant stateful serverless functions. Code available at [github](https://github.com/eniac/Beldi)
- [A fault-tolerance shim for serverless computing (Eurosys'20)](https://dl.acm.org/doi/10.1145/3342195.3387535) - The paper presents AFT, an atomic fault tolerance shim for serverless functions. AFT ensures atomic visibility of updates by enforcing read atomic isolation guarantee.
- [Formal Foundations of Serverless Computing (OOPSLA'19)](https://dl.acm.org/doi/10.1145/3360575) - It is the best paper of OOPSLA'19, which presents formal model to analyze (and prove) the reliability of serverless computing.

## Security
- [Peeking Behind the Curtains of Serverless Platforms (ATC'18)](https://dl.acm.org/doi/10.5555/3277355.3277369)

## Architecture Supports
- PIE: Confidential Serverless Made Efficient with Plug-In Enclaves (ISCA'21) - The paper presents PIE, a hardware extension on SGX to boost startup latency of enclaves to support serverless computing.

## Programming Models
- [Kappa: a programming framework for serverless computing](https://dl.acm.org/doi/abs/10.1145/3419111.3421277) - Kappa proposes a new programming model for serverless computing, which utilizes *checkpointing* to support long running services, and reuse python features to manage concurrency. It is open-sourced at [kappa](https://kappa.cs.berkeley.edu) and [github-repo](https://github.com/NetSys/kappa).


## Other Related Works
- [E3: Energy-Efficient Microservices on SmartNIC-Accelerated Servers (ATC'19)](https://dl.acm.org/doi/10.5555/3358807.3358839)

## Other Recommended Lists
- [Awesome Serverless](https://github.com/anaibol/awesome-serverless) - A curated list of awesome services, solutions and resources for serverless / nobackend applications.
- [awesome-serverless-security](https://github.com/puresec/awesome-serverless-security) - A curated list of awesome serverless security resources such as (e)books, articles, whitepapers, blogs and research papers.

