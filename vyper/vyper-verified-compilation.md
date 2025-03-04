# Verified Compilation of Vyper

## Project Abstract

We will create a formally verified compiler for [Vyper](https://vyperlang.org) that is usable by real applications. This project addresses the critical need for trustworthy smart contract development on Ethereum by ensuring that compiled bytecode faithfully preserves the intended semantics of source programs. Not having to worry about compiler bugs will strengthen the case for source-level application verification.

Formal verification in our context means that the EVM (Ethereum Virtual Machine) bytecode produced by the compiler exhibits behaviors only as allowed by the semantics of the source Vyper program. This means that developers and users only need to inspect or reason about the source program to trust that the deployed contract behaves as expected, eliminating the compiler as a point of vulnerability.

All semantics and proofs will be developed in higher-order logic using [the HOL4 interactive theorem prover](https://hol-theorem-prover.org), providing a small trusted computing base and mechanical verification of all claims. This approach not only ensures compiler correctness but also establishes a foundation for comprehensive correctness proofs of applications written in Vyper, which can then also be carried out in HOL4.

## Objectives

Our primary objective is to develop a verified subset of the Vyper compiler that produces usable bytecode with semantics preservation guarantees. Success for this project is defined by:

1. Developing and formalising semantics for Vyper (or a substantial subset thereof) in HOL4
2. Creating a formal model of EVM execution that accurately captures all relevant behaviors
3. Implementing an executable compiler within the logic that preserves source program semantics
4. Producing a working compiler that developers can use for real applications
5. Contributing to making Vyper's language specification more explicit and formal

We will measure success through:
- Completeness of the formalisation (proportion of Vyper language features covered)
- Validation of the formalisation (conformance with existing test suites and examples)
- Correctness guarantees (strength and interpretability of theorems proved about the compiler)
- Usability (ability to compile real-world contracts, comparable output with the production unverified compiler)
- Academic output (quality and number of publications)

Objective 1 is partially covered by an already-awarded grant from the ESP (Ecosystem Support Program) (ID: FY25-1892), and work is already underway. Substantial work towards objective 2 has been done already as part of the [Verifereum](https://verifereum.org) project.

## Outcomes

This project will benefit the Ethereum ecosystem in several critical ways:

1. **Enhanced Security**: Smart contracts secure billions of dollars in value. Eliminating compiler bugs removes a significant attack vector in the development pipeline.
2. **Increased Trust**: Developers and users will be able to trust that deployed contracts faithfully implement their source-level intentions.
3. **Lower Verification Burden**: The verification burden is reduced to inspecting or proving properties about source code, rather than reasoning about low-level bytecode.
4. **Formal Foundation**: Providing a formal semantics for Vyper contributes to the overall maturity of the Ethereum development ecosystem.
5. **Bug Discovery**: The process of formalisation often reveals bugs or inconsistencies in language definitions, benefiting the Vyper language itself.
6. **Academic Advancement**: The project will advance formal methods research applied to smart-contract blockchains in general with a strong focus on Ethereum.

To give more concreteness, here are some examples of the topics for papers we expect to write during the project:

- Formal Semantics of Vyper
- Semantics of the EVM in HOL (Verifereum) that is up to date, maintainable, and used
- Verification of parts of the Vyper compiler, e.g. the Venom IR and optimisation passes on it
- A Verified Compiler for Vyper (perhaps unoptimising, but complete and usable)
- End-to-end verification of Vyper programs (i.e., including examples of verified source programs)
- Verification of (some particular) Vyper compiler optimisations
- Practical Verified Compilation for Vyper Applications (i.e. an optimising verified compiler, and an approach to proving bytecode equivalence with the production compiler)
- How we keep the verified Vyper compiler up to date as the EVM, the Vyper language, and the compilation algorithms evolve

## Grant Scope

Our research will focus on:

1. Formalising the semantics of Vyper and the EVM in HOL4
2. Developing an executable verified compiler from Vyper to EVM bytecode
3. Proving that this compiler preserves the semantics of source programs
4. Creating a usable implementation that produces correct bytecode

Expected outputs include:

- Formal specifications of Vyper and EVM
- A verified compiler implementation for a substantial subset of Vyper
- Academic papers describing the semantics, verification approach, and results
- Documentation to help make the Vyper language specification more explicit
- A working compiler that can be used by developers

We will prioritise the most interesting parts of the roadmap toward verified compilation, focusing on derisking the path to a full verified compiler while delivering something immediately usable at the conclusion of the grant period.

## Related Work

Our project builds upon and extends several research areas:

1. **EVM Formalisations**: Previous and current work includes formalisations in K, Lean4, ACL2, Coq, and Isabelle/HOL; additionally there are executable specifications such as EELS and hevm. Each of these approaches has different strengths and weaknesses, although some are incomplete or no longer maintained. Our HOL4 formalization will be both comprehensive and maintained, and leverage the strengths of HOL4: deep expressivity and extensibility of the formalisation, and a small trustworthy kernel.

2. **Verified Compilation**: Projects like CompCert and CakeML have demonstrated the feasibility of verified compilation for conventional languages. Our work extends these techniques to the domain-specific challenges of smart-contract languages.

3. **Smart Contract Verification**: Numerous tools exist for verifying properties of smart contracts (e.g., using Dafny, Z3), but these typically operate either reasoning directly at the bytecode level or use simplified models of execution disconnected from the real bytecode semantics.

4. **Vyper Semantics**: Limited formal work exists on Vyper's semantics. Our project will provide the first comprehensive formalisation of the language.

The specific gap we are addressing is the lack of a verified compiler for a high-level Ethereum language that both preserves semantics and is usable in practice. While verification tools exist, they typically operate after compilation, when issues may already be present, or assume compiler correctness. Our approach eliminates compilation bugs as a source of vulnerabilities.

## Project Team

Our interdisciplinary team combines expertise in formal verification, compiler development, and Ethereum technology.

We have an open project structure, developing all code and proofs in the open, welcoming all contributions, and mentoring new community members. As such, not all contributors will be listed here in advance. However, we highlight the core contributors who will be leading the project and ensuring its completion:

1. Ramana Kumar, PhD in formal verification, user and developer of Ethereum applications, lead developer of Verifereum

2. Magnus Myreen, PhD in formal verification, professor at Chalmers University, lead developer of the CakeML verified compiler

3. Michael Norrish, PhD in formal verification, professor at the Australian National University, lead developer of the HOL4 theorem prover

4. Charles Cooper, lead developer of the Vyper language and compiler

5. Cyberthirst and/or Benny should also be listed?

## Background and Prior Work

Our team brings together the expertise needed to successfully complete this challenging project:

- **Compiler Verification Expertise**: Team members have contributed to the CakeML verified compiler and related projects, demonstrating the ability to verify complex compiler transformations in higher-order logic.

- **Vyper Development Experience**: We include core members of the Vyper compiler development team who bring deep knowledge of the language, its implementation challenges, and evolution plans.

- **Ethereum Expertise**: Our team includes active participants in the Ethereum ecosystem as contract developers, home-stakers, and Rocket Pool node-runners/validators, ensuring our work remains relevant to real-world needs.

Relevant prior work includes:
- [Add specific papers, repositories, or projects]
- [Add links to team members' prior research]
- [Note: Our team has already received a small grant for initial work on Vyper semantics]

## Methodology

Our approach follows a methodical progression through formal specification, implementation, verification, and validation:

### High-level Roadmap/Milestones:

1. **EVM Semantics** [Must] - 3 person months (Done?)
   - Formalize execution model in HOL4
   - Cover all relevant opcodes and state transitions
   - Ensure alignment with latest EVM specifications

2. **Vyper Semantics** [Must] - 3-6 person months (Done?)
   - Formalize core subset of Vyper
   - Collaborate with Vyper team on specification improvements
   - Document memory/storage layout and execution model
   - Reify view of the abstract Vyper machine to EVM state

2b. **Vyper Semantics Add-Ons** [Nice to have] - ??
   - Parser
   - Type checking
   - Semantic analysis
   - Import resolution

3a. **Validation of EVM Semantics** [Nice to have] - 6 person months
   - Test against reference implementations
   - Prove key properties about the semantics

3b. **Validation of Vyper Semantics** [Nice to have] - 6 person months
   - Test against reference implementations
   - Prove key properties about the semantics

4. **IR Semantics** [Nice to have] - 6-9 person months
   - Formalize Venom IR for compiler intermediate representation
   - Specify IR transformations and optimizations

5. **Compiler Implementation in Logic** [Must] - 1-2 person months
   - Implement executable compiler in HOL4
   - Start with unoptimized version for core language subset
   - Extend to more features as verification progresses

6. **Validation of Implementation** [Nice to have] - 9-12 person months
   - Test against reference compiler output
   - Develop equivalence checking for bytecode

7. **Compiler Verification** [Must] - 12 months
   - Prove semantics preservation
   - Establish end-to-end correctness guarantees

### Timeline and Deliverables:

**Milestone 1: EVM and Core Vyper Semantics**
- Budget: $X (based on Y hours at $Z/hour)
- Deliverables:
  - HOL4 formalization of EVM execution model
  - HOL4 formalization of core Vyper subset
  - Documentation of formal semantics
  - Technical report on semantic design choices

**Milestone 2: Compiler Implementation and Initial Verification**
- Budget: $X (based on Y hours at $Z/hour)
- Deliverables:
  - Executable compiler implementation in HOL4
  - Initial correctness proofs for subset of transformations
  - Test suite validating against reference compiler
  - Report on implementation approach

**Milestone 3: Complete Verification and Usable Compiler**
- Budget: $X (based on Y hours at $Z/hour)
- Deliverables:
  - Complete semantics preservation proofs
  - Usable compiler implementation
  - Documentation for developers
  - Academic paper(s) describing the verification
  - Contributions to Vyper language specification

## Requested Grant Amount and Budget

We request a total grant of $XXX,XXX to support this work.

### Budget Breakdown:

**Principal Researcher Costs**: $XXX,XXX
- PI: X months at $Y/month
- Compiler Verification Lead: X months at $Y/month
- Vyper Expert: X months at $Y/month

**Other Staff Costs**: $XX,XXX
- Research Assistants: X months at $Y/month
- EVM Semantics Specialist: X months at $Y/month

**Indirect Costs**: $XX,XXX
- University/Institution overhead (X% of direct costs)

**Hardware/Software Costs**: $X,XXX
- Specialized computing resources for proof development
- Software licenses

**Scaling Options**:
- At $XXX,XXX funding level: Core Vyper subset with basic verification
- At $XXX,XXX funding level: Extended language coverage and optimizations
- At $XXX,XXX funding level: Comprehensive verification with tooling for bytecode equivalence checking

We are prepared to adjust the scope based on available funding while ensuring delivery of a useful verified compiler.
