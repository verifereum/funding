# Verification of EVM Bytecode Programs via Decompilation into Logic

## Project Abstract
<!-- In 3-5 sentences what problem are you trying to solve? (The project abstract may be used for for the winners announcement.) -->
We will implement proof-producing [machine-code decompilation](https://www.cl.cam.ac.uk/~mom22/decompilation.html) for the [Verifereum](https://verifereum.org) formalisation of the Ethereum Virtual Machine (EVM) in the [HOL4 theorem prover](https://hol-theorem-prover.org). This technology will enable reasoning about EVM bytecode programs at a higher level of abstraction using separation logic, bridging the gap between low-level bytecode and high-level program properties. By translating EVM bytecode into logical representations, we will create powerful verification tools that allow developers and auditors to formally verify smart contract properties with greater ease and confidence.

### Objectives
<!-- What are you hoping to accomplish with this grant? How do you define and measure success for this project? -->
1. Adapt the existing machine-code decompilation framework to handle the EVM and EVM bytecode
2. Develop proof-producing translation from EVM bytecode to higher-level logical programs
3. Create a separation logic framework tailored to reasoning about these EVM programs
4. Demonstrate the practical application by decompiling and verifying select real-world smart contracts
5. Success will be measured by our ability to automatically decompile EVM bytecode into logical specifications that are amenable to higher-level reasoning and proof

### Outcomes
<!-- How does this project benefit the greater Ethereum ecosystem? -->
This project will enable formal verification of EVM smart contracts at a higher level of abstraction, making sophisticated verification techniques more accessible to developers. It will reduce the gap between implementation and specification, allowing for stronger guarantees about smart contract behavior. Ultimately, this technology will help improve the security and reliability of the Ethereum ecosystem by providing more powerful and intuitive verification tools that can catch subtle bugs and vulnerabilities before deployment.

## Grant Scope
<!-- What are you going to research? What is the expected output? -->
Our research will focus on adapting Magnus Myreen's decompilation technology to work with EVM bytecode. We will develop the necessary infrastructure to translate EVM operations into higher-level logical constructs, with particular emphasis on handling EVM-specific features such as gas, storage, and the memory model. The expected output includes:

1. A formal implementation of the decompilation technology for EVM in HOL4
2. A separation logic framework tailored to reasoning about EVM programs
3. Case studies demonstrating the application of our technology to verify representative smart contracts
4. An academic paper explaining the insights gleaned from our work and explaining how to use the technology
5. Open-source code and guides integrating with the existing Verifereum project's EVM formalisation

## Related Work
<!-- What existing research is relevant to your project?
What is the specific gap your research is addressing within this context? -->
The Verifereum project has already made significant progress in formalising the EVM in HOL4, providing a solid foundation for our work. Magnus Myreen's research on decompilation into logic has been successfully applied to various architectures, including x86, ARM, and MIPS, demonstrating its versatility and effectiveness.

Other relevant work includes:
- The K Framework's formalisation of EVM (KEVM)
- DeepSEA and Scilla, which provide high-level languages with formal semantics that compile to EVM
- The Certora Prover and similar tools that use SMT solvers for EVM verification

The specific gap our research addresses is the ability to directly reason about existing EVM bytecode at a higher level of abstraction without requiring developers to use specific languages or frameworks during development. Our approach will allow post-hoc verification of any EVM bytecode, providing a universal verification approach regardless of the source language or compiler used.

## Project Team
<!-- How many people are working on this project?
Please list their names and roles for the project as well as how many hours per month will each person work on this project?
-->

- Principal Investigator: Dr. Ramana Kumar - Project lead and formal verification expert (60 hours/month)
- Co-Investigator: Dr. Magnus Myreen - Decompilation technology expert (40 hours/month)
- Research Assistant: [To be hired] - HOL4 implementation and case studies (120 hours/month)

### Background
<!-- Give us a bit of info and include relevant links, if available! Please provide other projects or research papers (ideally public and/or open source), engagements or other types of proof that your team has the necessary experience to undertake the project you are applying for.

Any links for us to review? E.g. research papers, blog posts, etc.
-->

Dr. Ramana Kumar has extensive experience in formal verification and theorem proving, particularly in the context of verified systems. He has been a key contributor to the CakeML project, developing verified compilation techniques and formal semantics for a substantial subset of ML. More recently, Dr. Kumar has been working on the Verifereum project, focusing on formalising the EVM in HOL4. His background bridges the critical domains of formal verification, functional programming, and blockchain technology.

Dr. Magnus Myreen is a pioneer in decompilation technology for formal verification. His work includes:
- CakeML (https://cakeml.org): A verified ML compiler with decompilation technology
- "Decompilation into Logic" methodology (https://www.cl.cam.ac.uk/~mom22/jagger/)
- Publications such as "Machine-Code Verification for Multiple Architectures" (FMCAD 2008)
- "Automatic generation of verified decompilers for theorem provers" (ITP 2013)

[The Verifereum project](https://verifereum.org) has already established a comprehensive formalisation of EVM in HOL4, which will serve as the foundation for our extensions.

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
- Budget: $30,000 (220 hours total)
  - Dr. Kumar: 60 hours/month × 2 months
  - Dr. Myreen: 40 hours/month × 2 months
  - Research Assistant: 120 hours/month × 2 months
- Tasks:
  - Analyze existing EVM formalisation in HOL4
  - Identify and implement necessary extensions
  - Develop initial mapping between EVM operations and logical constructs
  - Deliverable: Technical report on EVM formalisation analysis and extensions

**Milestone 2: Core Decompilation Technology for EVM (Months 3-4)**
- Budget: $40,000 (220 hours total)
  - Dr. Kumar: 60 hours/month × 2 months
  - Dr. Myreen: 40 hours/month × 2 months
  - Research Assistant: 120 hours/month × 2 months
- Tasks:
  - Implement decompilation specifications for EVM operations
  - Develop translation functions from bytecode to logical representations
  - Build proof infrastructure for validating decompilations
  - Initial testing on simple smart contracts
  - Deliverable: Working prototype of EVM decompilation technology with documentation

**Milestone 3: Separation Logic Framework and Case Studies (Months 5-6)**
- Budget: $30,000 (220 hours total)
  - Dr. Kumar: 60 hours/month × 2 months
  - Dr. Myreen: 40 hours/month × 2 months
  - Research Assistant: 120 hours/month × 2 months
- Tasks:
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

**Total Requested Amount: $100,000**

### Budget Breakdown:

**Principal Researchers Costs: $72,000**
- Dr. Ramana Kumar: $36,000 (60 hours/month × 6 months × $100/hour)
- Dr. Magnus Myreen: $36,000 (40 hours/month × 6 months × $150/hour)

**Other Staff Costs: $21,600**
- Research Assistant: $21,600 (120 hours/month × 6 months × $30/hour)

**Hardware and Computing Costs: $3,000**
- High-performance computing resources for theorem proving
- Development workstations for research

**Software and Tools: $1,000**
- Specialized tools and software licenses
- Cloud services for collaboration and testing

**Conference and Publication Costs: $1,400**
- Publication fees for open-access journals
- Presentation materials

**Indirect Costs: $1,000**
- Administrative support
- Project management
