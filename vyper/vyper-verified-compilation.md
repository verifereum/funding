# Verified Compilation of Vyper

## Project Abstract

We will create a formally verified compiler for [Vyper](https://vyperlang.org) that is usable by real applications. This project addresses the critical need for trustworthy smart contract development on Ethereum by ensuring that compiled bytecode faithfully preserves the intended semantics of source programs. Not having to worry about compiler bugs will strengthen the case for source-level application verification.

Formal verification in our context means that the EVM (Ethereum Virtual Machine) bytecode produced by the compiler exhibits behaviors only as allowed by the semantics of the source Vyper program. This means that developers and users need only inspect and/or reason about the source program to trust that the deployed contract behaves as expected, eliminating the compiler as a point of vulnerability.

All semantics and proofs will be developed in higher-order logic using [the HOL4 interactive theorem prover](https://hol-theorem-prover.org), providing a small trusted computing base and mechanical verification of all claims. This approach not only ensures compiler correctness, but also establishes a foundation for comprehensive correctness proofs of applications written in Vyper, which can then also be carried out in HOL4.

## Objectives

Our immediate goal is to show that it is practically possible to build a verified Vyper compiler that produces usable bytecode with semantics preservation guarantees.
Using the funding provided, we will run _a pilot project_ that builds a verified compiler for _a subset of_ the Vyper language.
This pilot project will build the compiler in such a way that it is clear how the work could be extended to more or even all of the Vyper language, and for the verified compiler to eventually support all optimisations performed by the production Vyper compiler.

Success for this project is defined by:

1. Constructing a verified compiler for a subset of the Vyper source language and demonstrating that the verified compiler is practically usable.
2. Publishing an academic paper describing the work and bringing attention to it (with the aim to recruit people to join the effort for the continuation of this work after the pilot project has finished).

Incidental objectives include:

1. Developing and formalising semantics for Vyper (or a substantial subset thereof) in HOL4
2. Creating a formal model of EVM execution that accurately captures all relevant behaviors
3. Implementing an executable compiler within the logic that preserves source program semantics

Incidental objective 1 is partially covered by an already-awarded grant from the ESP (Ecosystem Support Program) (ID: FY25-1892), and work is already underway. Substantial work towards incidental objective 2 has been done already as part of the [Verifereum](https://verifereum.org) project.

The aim of this pilot project is to start a longer project to build a verified compiler that developers can use for real applications, and we also intend to contribute to making Vyper's language specification more explicit and precise through this work.

## Outcomes

This project will benefit the Ethereum ecosystem in several critical ways:

1. **Enhanced Security**: Smart contracts secure billions of dollars in value. Eliminating compiler bugs removes a significant attack vector in the development pipeline.
2. **Increased Trust**: Developers and users will be able to trust that deployed contracts faithfully implement their source-level intentions.
3. **Lower Verification Burden**: The verification burden is reduced to inspecting or proving properties about source code, rather than reasoning about low-level bytecode.
4. **Formal Foundation**: Providing a formal semantics for Vyper contributes to the overall maturity of the Ethereum development ecosystem.
5. **Bug Discovery**: The process of formalisation often reveals bugs or inconsistencies in language definitions, benefiting the Vyper language itself.
6. **Academic Advancement**: The project will advance formal methods research applied to smart-contract blockchains in general with a strong focus on Ethereum. We are planning to publish a paper detailing our achievements within the scope of this grant which will serve as a stepping stone for further publications. This will result in additional attention and interest for Ethereum and blockchains within the academic community.

## Grant Scope

Our research will focus on:

1. Formalising the semantics of a subset Vyper and the EVM in HOL4
2. Developing an executable verified compiler from Vyper to EVM bytecode

Expected outputs include:

- A working compiler that can be used by developers
- An academic paper describing the work achieved within the scope of the grant


## Related Work

Our project builds upon and extends several research areas:

1. **EVM Formalisations**: Previous and current work includes formalisations in [K](https://doi.org/10.1109/CSF.2018.00022), [Lean4](https://github.com/NethermindEth/EVMYulLean), [Dafny](https://github.com/Consensys/evm-dafny), [ACL2](https://www.kestrel.edu/research/ethereum/), [Coq](https://doi.org/10.48550/arXiv.1810.04828), and [Isabelle/HOL](https://doi.org/10.1145/316708); additionally there are executable specifications such as [EELS](https://github.com/ethereum/execution-specs/) and [hevm](https://github.com/ethereum/hevm). Each of these approaches has different strengths and weaknesses, although some are incomplete or no longer maintained. Our HOL4 formalization will be both comprehensive and maintained, and leverage the strengths of HOL4. Unlike K or Dafny which are based on first-order logic, HOL4 is based on higher-order logic whose semantics are [much more expressive](https://philpapers.org/rec/FARTSV). This allows for more complex and comprehensive proofs, beyond simple assertions about a contract's expected behavior. HOL4 has been [formally proven sound](https://www.cl.cam.ac.uk/~jrh13/papers/holhol.html) and has a very small and well reviewed kernel.

2. **Verified Compilation**: Projects like [CompCert](https://doi.org/10.1145/1538788.1538814) and [CakeML](https://doi.org/10.1145/2578855.2535841) have demonstrated the feasibility of verified compilation for conventional languages. Our work extends these techniques to the domain-specific challenges of smart-contract languages.

3. **Smart Contract Verification**: Numerous tools exist for verifying properties of smart contracts (e.g., using [Dafny](https://github.com/Consensys/evm-dafny) or [Z3](https://www.zellic.io/blog/formal-verification-weth/)), but these typically operate by either reasoning directly at the bytecode level or use simplified models of execution disconnected from the real bytecode semantics.

4. **Vyper Semantics**: Limited formal work exists on Vyper's semantics. Our project will provide the first comprehensive formalisation of the language.

The specific gap we are addressing is the lack of a verified compiler for a high-level Ethereum language that both preserves semantics and is usable in practice. While verification tools exist, they typically operate after compilation, when issues may already be present, or assume compiler correctness. Our approach eliminates compilation bugs as a source of vulnerabilities.

## Project Team

Our interdisciplinary team combines expertise in formal verification, compiler development, and Ethereum technology.

We have an open project structure, developing all code and proofs in the open, welcoming all contributions, and mentoring new community members. As such, not all contributors will be listed here in advance. However, we highlight the core contributors who will be leading the project and ensuring its completion:

1. Ramana Kumar, PhD in formal verification, user and developer of Ethereum applications, lead developer of [Verifereum](https://verifereum.org).

2. Magnus Myreen, PhD in formal verification, professor at Chalmers University, lead developer of the [CakeML verified compiler](https://cakeml.org).

3. Michael Norrish, PhD in formal verification, professor at the Australian National University, lead developer of the [HOL4 theorem prover](https://hol-theorem-prover.org).

4. Charles Cooper, lead developer of the [Vyper language and compiler](https://vyperlang.org).

5. Cyberthirst, MSc, lead security engineer of the Vyper compiler

## Background and Prior Work

- **Compiler Verification Expertise**: Our team includes core developers of the CakeML verified compiler and related projects, demonstrating the ability to verify complex compiler transformations in higher-order logic. The CakeML verified compiler is the only production-grade verified compiler in the world, aside from CompCert.

- **Vyper Development Experience**: Our team includes core members of the Vyper compiler development team who bring deep knowledge of the language, its implementation challenges, and evolution plans.

- **Ethereum Expertise**: Our team includes active participants in the Ethereum ecosystem as contract developers, home-stakers, and [Rocket Pool](https://rocketpool.net) node-runners/validators, ensuring our work remains relevant to real-world needs.

## Budget, Timeline, and Deliverables

Our total request is for $120,000 for a 6-month project.

**Milestone 1: Vyper and EVM Semantics in HOL4**

- Deliverables:
  - Formal specification of the EVM execution model
  - Formal specification of core Vyper language
  - Validation of the above executable specifications against existing Vyper and EVM conformance tests
- Timeframe: 2 months (remaining, not considering work already done or funded)
- Budget: $40,000

**Milestone 2: Verified Compiler for a Subset of Vyper**

- Roadmap:
  - Define a relation between the abstract Vyper semantic state and the EVM state
  - Formally specify an intermediate representation (IR) for Vyper
  - Define compilation algorithms (from Vyper to IR to bytecode) in the HOL4 logic
  - Validate the compilation algorithms by execution and inspection of the resulting code
  - Prove semantics preservation for the above algorithms
- Deliverables:
  - Executable (in logic) compiler that takes Vyper source code and produces EVM bytecode
  - Proof of semantics preservation for the above compiler in HOL4
  - Paper describing the work, covering academic insights from both milestones
- Timeframe: 4 months
- Budget: $80,000
