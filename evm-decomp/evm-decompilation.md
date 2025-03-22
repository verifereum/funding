# Verification of EVM Bytecode Programs using Decompilation into Logic

## Project Abstract
<!-- In 3-5 sentences what problem are you trying to solve? (The project abstract may be used for for the winners announcement.) -->
We will implement proof-producing [machine-code decompilation](https://www.cl.cam.ac.uk/~mom22/decompilation.html) for the Ethereum Virtual Machine (EVM) formalised by [Verifereum](https://verifereum.org) in the [HOL4 theorem prover](https://hol-theorem-prover.org). This technology will enable reasoning about EVM bytecode programs at a higher level of abstraction using separation logic, bridging the gap between low-level bytecode and high-level program properties. By translating EVM bytecode into logical representations, we will create powerful verification tools that allow developers and auditors to formally verify smart contract properties with greater ease and confidence.

To illustrate what we mean by machine-code decompilation, we expect to take raw bytes of EVM code such as `code = 5f6370a082315f5230602052...` and automatically produce a functional program over the EVM call context and state such as
```
main (stack, mem, storage, ...) =
  let stack = 0w :: stack in
  let stack = 0x70a08231w :: stack in
  let stack = 0w :: stack in
  let mem = mstore ... mem in
    ...
```
together with a theorem stating that execution of `code` in an appropriate context has the same effect on the machine state as the function `main` applied to that machine state in the same context. This enables a developer to draw trustworthy conclusions about `code` by reasoning about `main` instead (including using further proof automation).

### Objectives
<!-- What are you hoping to accomplish with this grant? How do you define and measure success for this project? -->
1. Adapt the [existing machine-code decompilation framework](https://www.cl.cam.ac.uk/~mom22/decompilation.html) to handle EVM state and bytecode
2. Develop proof-producing translation from EVM bytecode to higher-level logical programs
3. Create a separation logic framework tailored to reasoning about these EVM programs
4. Demonstrate practicality by decompiling and verifying examples of smart contracts, including real-world deployments
5. Measure success as our ability to automatically decompile EVM bytecode into logical specifications that are amenable to higher-level reasoning and proof

### Outcomes
<!-- How does this project benefit the greater Ethereum ecosystem? -->
This project enables the following workflow:

1. Start with an EVM program (e.g., a deployed smart contract) produced by any means, e.g., compiled from [Solidity](https://soliditylang.org), written in [Huff](https://huff.sh), etc.
2. Derive a functional program encompassing the behaviour of the EVM program using clean abstractions, together with a proof of equivalence of behaviour with the original program.
3. Use any technique to build assurance in the original program by inspecting or reasoning about the functional program. This might include manual auditing or interactive theorem proving. The theorems produced in step 2 ensure that conclusions drawn about the functional program are also true of the original EVM program.

Therefore, this project will enable formal verification of EVM smart contracts at a higher level of abstraction, and with a higher level of assurance than almost all current approaches to formal verification of EVM programs. Our work will reduce the gap between implementation and specification, allowing for stronger guarantees about smart contract behavior. Ultimately, this technology will help improve the security and reliability of the Ethereum ecosystem by providing more powerful and intuitive verification tools that can catch subtle bugs and vulnerabilities before deployment.

## Grant Scope
<!-- What are you going to research? What is the expected output? -->
Our research will focus on adapting Magnus Myreen's [proof-producing decompilation technology](https://www.cl.cam.ac.uk/~mom22/decompilation.html) to work with EVM bytecode.
This technology has previously only been used for machine code for traditional CPUs.
We will develop the necessary infrastructure to translate EVM operations into higher-level logical constructs, with particular emphasis on handling EVM-specific features such as gas, storage, and the memory model.

The expected output includes:

1. A separation logic framework tailored to reasoning about EVM programs and to work with proof-producing decompilation
2. An implementation in HOL4 of proof-producing decompilation for EVM programs
3. Case studies demonstrating the application of our technology to verify representative smart contracts
4. An academic paper announcing that proof-producing decompilation is applicable to the EVM setting, summarising our findings and insights
5. Open-source code and accessible guides on using this work, integrating with the existing Verifereum project's EVM formalisation

## Related Work
<!-- What existing research is relevant to your project?
What is the specific gap your research is addressing within this context? -->
[The Verifereum project](https://verifereum.org), which we are extending, has already made significant progress in formalising the EVM in HOL4, providing a solid foundation for our work. Magnus Myreen's [research on decompilation](https://www.cl.cam.ac.uk/~mom22/decompilation.html) into logic has been successfully applied to various architectures, including x86, ARM, and PowerPC, demonstrating its versatility and effectiveness.

The gaps we are filling:

- More expressive logic than many other approaches to verification of EVM programs, which means we can verify deeper correctness properties
- Scalable expressivity: we can automate our proofs but, where automation fails, there is always the option to fill out the hard parts with fully interactive proof
- Trustworthiness of the underlying theorem prover [HOL4](https://hol-theorem-prover.org), with its conservative design and small well-reviewed kernel

Some related work on verification of EVM programs and smart contracts is listed in [this linked repository](https://github.com/leonardoalt/ethereum_formal_verification_overview/blob/master/README.md), and others can be found for example at [this website](https://formalverification.xyz). The following items, from these lists and beyond, seem to be the most significant and closest to our goals:

- KEVM: [A formal verification tool for Ethereum VM bytecode](https://dl.acm.org/doi/10.1145/3236024.3264591)
  - This work shares our goal of making an accurate and complete formalisation of the EVM (without, e.g., over-approximations in the model) and even goes further than the Verifereum EVM semantics by modelling all the previous versions of the EVM from past hard forks rather than just the latest live version. When it comes to proofs on top of this semantics, we believe a formalisation in HOL is more appropriate than the K language (although it would be good to prove the two specifications equivalent) because HOL is a more expressive logic for describing correctness properties at the application level.
- Nethermind EVMYulLean: [Executable formal model of the EVM and Yul in Lean 4](https://github.com/NethermindEth/EVMYulLean)
  - This is perhaps the closest related work on the formal specification of the EVM, since it is an accurate and comprehensive model of the latest live EVM in an expressive logic (the [Lean](https://lean-lang.org) language). By comparison, our proposed work benefits from the existing infrastructure for decompilation into logic implement in HOL4 (which is not present in Lean4).
- F\*: [EVM-Vale: Formal Verification of EVM Bytecode Using Vale](https://link.springer.com/chapter/10.1007/978-981-97-0006-6_3)
  - This work shares some aspects with our proposal, since they specify EVM and then use Vale to lift EVM code into higher-level representations that are provably sound representations of the original EVM code. This work has the limitation that all proof goals are ultimately sent to SMT solvers which inherently limits the specifications one can prove to those that fit within what F\* can express in its specifications. F\* does not support general-purpose interactive theorem proving like tools such as HOL4 or Lean4.
- Dafny: [Formal and Executable Semantics of the Ethereum Virtual Machine in Dafny](https://dl.acm.org/doi/10.1007/978-3-031-27481-7_32)

<!--
- Runtime Verification's KEVM formalisation of the EVM in the K Framework (and other EVM formalisations...)
- Deductive verification of smart contracts in Dafny -- must start with a contract written in Dafny
- seL4 and other BA or decompilation work in Isabelle
- HOLBA
- DeepSEA and Scilla, which provide high-level languages with formal semantics that compile to EVM
- The Certora Prover and similar tools that use SMT solvers for EVM verification
-->

## Project Team
<!-- How many people are working on this project?
Please list their names and roles for the project as well as how many hours per month will each person work on this project?
-->

- Principal Investigator: Ramana Kumar - Project lead and formal verification expert
- Co-Investigator: Magnus Myreen - Proof-producing decompilation expert
- Research Assistant: [To be hired] - HOL4 implementation and case studies

### Background
<!-- Give us a bit of info and include relevant links, if available! Please provide other projects or research papers (ideally public and/or open source), engagements or other types of proof that your team has the necessary experience to undertake the project you are applying for.

Any links for us to review? E.g. research papers, blog posts, etc.
-->

Ramana has a PhD in computer science and has done extensive [academic research](https://scholar.google.com/citations?user=OyX1-qYAAAAJ) on formal verification. He is a world leading expert on compiler verification and a key contributor to [CakeML](https://cakeml.org), a verified implementation of ML and one of a handful of formally verified compilers. An active contributor to the Rocket Pool liquid staking ecosystem on Ethereum, user of several decentralised finance (DeFi) protocols, and smart contract author himself, Ramana combines his expertise in formal verification with a deep knowledge of the EVM. His background makes him uniquely qualified to build the Verifereum EVM formal verification framework, and Verifereum-based projects for application verification (including via proof-producing decompilation).

Magnus Myreen is a professor at Chalmers University with a comprehensive [academic career](https://scholar.google.com/citations?user=XfqNgKwAAAAJ). He is like Ramana a key contributor to CakeML and has expertise in compiler verification and in developing proof automation in HOL; Magnus additionally pioneered the bootstrapping techniques used in CakeML in previous work on [Jitawa](https://www.cl.cam.ac.uk/~mom22/jitawa). Magnus is the originator for the proof-producing decompilation methods and technology, highlighted in papers such as _[Translation Validation for a Verified OS Kernel](https://www.cl.cam.ac.uk/~mom22/pldi13.pdf)_, that we intend to apply to the EVM in this work.

[The Verifereum project](https://verifereum.org) has already established a comprehensive formalisation of EVM in HOL4, which will serve as the foundation for our work.

## Methodology
<!-- How do you plan to achieve your research objectives? -->
Our approach consists of four main phases:

1. **Analysis and Extension of EVM Formalisation**: We will analyze the existing HOL4 formalisation of EVM from the Verifereum project and extend it as needed to support decompilation.

2. **Development of EVM Decompilation Framework**: We will adapt Magnus Myreen's decompilation technology to work with EVM bytecode. This involves:
   - Developing decompilation specifications for EVM operations
   - Creating translation rules from EVM operations to logical predicates
   - Handling EVM-specific features (gas, storage, memory model)

3. **Separation Logic Framework**: We will develop a separation logic framework tailored to reasoning about EVM programs, including:
   - Heap models for EVM storage and memory
   - Pre/post-condition specifications for common patterns
   - Proof automation for separation logic reasoning

4. **Case Studies and Documentation**: We will apply our technology to decompile and verify representative smart contracts, document our methodology, and create tutorials for other researchers.

### Timeline
<!-- Please include a brief explanation on the milestones/roadmap, along with expected deliverables. Also outline how the funds will be used for the research project and or members of the team.

Milestone 1: title
Budget: based off hourly rate and number of hours
Number of hours (roughly)
summary of work, subtasks
-->

**Milestone 1: EVM Formalisation Extension and Analysis (Months 1-2)**

- Analyze existing EVM formalisation in HOL4
- Identify and implement necessary extensions
- Develop initial mapping between EVM operations and logical constructs
- Deliverable: Technical report on EVM formalisation analysis and extensions

**Milestone 2: Core Decompilation Technology for EVM (Months 3-4)**

- Implement decompilation specifications for EVM operations
- Develop translation functions from bytecode to logical representations
- Build proof infrastructure for validating decompilations
- Initial testing on simple smart contracts
- Deliverable: Working prototype of EVM decompilation technology with documentation

**Milestone 3: Separation Logic Framework and Case Studies (Months 5-6)**

- Develop separation logic predicates for EVM state
- Create automated proof tactics for common verification patterns
- Apply decompilation to representative smart contracts
- Prepare documentation and final report
- Deliverable: Separation logic framework for EVM with example proofs, documented case studies, and final report

## Budget
<!-- Requested grant amount and how this will be used

Please provide an requested amount and outline of how the grant will be used. A detailed budget proposal would be helpful and some items you could include are:

    Principal Researchers Costs
    Other Staff Costs
    Hardware Costs
    Software Costs
    Data Collection Costs
    Indirect Costs

-->

**Total Requested Amount: $115,200**

### Budget Breakdown:

**Principal Researchers Costs: $72,000**

- Dr. Ramana Kumar: $36,000 (60 hours/month × 6 months × $100/hour)
- Dr. Magnus Myreen: $36,000 (40 hours/month × 6 months × $150/hour)

**Other Staff Costs: $43,200**

- Research Assistant: $43,200 (120 hours/month × 6 months × $60/hour)
