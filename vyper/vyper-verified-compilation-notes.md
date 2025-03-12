Submit _on or before_ March 14th!

# Scoping / Notes

An approach to the grant:
  - We will do the research to explore the most interesting parts of the roadmap towards the ultimate target
  - The output of the research is to derisk "cranking the handle" to get the ultimate target
  - Concretely, for example, a verified compiler that has a subset of the optimisations and/or features and/or performance
Be clear to say: at the end of the grant that we have something actually usable, i.e. you can run it.

## Ultimate targets (beyond this grant):

  - Verified compiler for Vyper that produces the same bytecode as the _latest released_ unverified compiler.

    What is it verified to do?

    - Preserve the semantics of the source program (i.e. when a transaction calls a Vyper contract).

    What is included in the semantics?

    1. State changes to the EVM (includes revert/succeed, includes balance changes to pay for execution)
    2. Logs/events
    3. Gas usage?

  - Help Vyper become more explicit about the specification of their language
    - including things like memory/storage layout
    - also help them find all their compiler bugs..

  - Academic output describing this work, i.e. papers

    Which papers?

    - Semantics of Vyper

    - Semantics of EVM in HOL (Verifereum)
      - executable
      - completeness: what does it mean?
      - uptodate + maintanable
      - usable for what?

    - Verification of parts of the Vyper compiler, e.g.
      - Formalising the Venom IR
      - Formalising some of the IR->IR passes

    - A Verified Compiler for Vyper
      - e.g. unoptimised Vyper -> EVM algorithm with semantics preservation proof

    - End-to-end verification of Vyper programs (i.e., including examples of verified source programs)

    - Verification of the optimisations

    - Practical verified compilation for Vyper applications
      - somewhat optimising verified compiler
      - verifying (i.e. produces hints) optimising unverified compiler (the Python one)
      - some bytecode equivalence automatic checking of the outputs

    - How we keep the verification up to date with changing EVM and changing Vyper
       - e.g. CI methodology, AI proof repair, including formal stuff in the dev methodology somehow, ...

## How does Vyper differ from conventional compilers?

  - The target (and source) language are a bit weird compared to conventional
    - EVM state changes are the main point (i.e. that's the "I/O" that needs to be preserved)
    - Logs are novel (but not that interesting)
    - Gas usage is novel
    - Contract (external) calls are novel
      - in particular reentrancy can be complicated
    - Contract ABI datatypes are a bit unusual
    - Vyper is a very simple language:
      - no recursion (but yes to function calls)
      - statically known call targets
      - first-order
      - bounded loops (bound is known from the type)
        - either a concrete number
        - or an iterator whose type contains a bound
      - imperative
      - data structures:
        - simple: bool, bytes, ints, words, etc.
        - structs, arrays, tuples
        - HashMaps, these nest, but are only at the top level
      - access to the underlying environment
        - block and transaction info
      - no inline EVM assembly, but maybe some day? + there are some low-level
        builtins that expose some of it
  - There is an old IR and a new IR (Venom). Probably at some point only Venom
    will be used, but not for a while.
  - Vyper -> Vyper AST (parsing, type checking) -> Old IR (+ optimisations) -> Venom IR (+ optimisations) -> Assembly -> EVM Bytecode
  - Old IR is basically s expressions. Has variables. Doesn't have functions :|
  - Venom has functions and basic blocks
  - Assembly is EVM with labelled jumps



# Verified Compilation of Vyper

# Project Abstract

We will create a formally verified compiler for Vyper that is usable by real
applications.

Formal verification here means the EVM bytecode produced by the compiler
exhibits behaviours only as allowed by the semantics of the source Vyper
program. [TODO: improve] This means that if you want to trust that the deployed
contract has some behaviour, you only need to inspect (or reason about) the
source program, and can trust that the compiled code has those behaviours.

All the semantics and proofs will be done in higher-order logic using the HOL4
interactive theorem prover. This means that the proofs are verified
mechanically by [TODO: more about small TCB and trustworthiness] [TODO: also
something about deep expressivity, can be extended to comprehensive correctness
proofs about the applications written in Vyper]

In 3-5 sentences what problem are you trying to solve? (The project abstract may be used for for the winners announcement.)

## Objectives

What are you hoping to accomplish with this grant? How do you define and measure success for this project?

See the scoping/target stuff above

Motivation notes:
- Smart contracts secure lots of value
- Vyper (and Solidity for that matter) has had compiler bugs in the past
- Contracts are typically small programs that are easy to reason about, the
  Vyper language is an excellent target for full verification

## Outcomes

How does this project benefit the greater Ethereum ecosystem?

Notes:
--> Whether you can trust a Vyper-compiled program is reduced to inspecting (or
proving things about) the source code. You can trust the compiler and don't
need to reason about its output directly.

# Grant Scope

What are you going to research? What is the expected output?

# Related Work

What existing research is relevant to your project?
What is the specific gap your research is addressing within this context?

Notes:
- verified compilation to the EVM? (probably yes)
- formalisation of the EVM has a lot of related work (afaik: K, Lean4, ACL2, Rocq (both unmaintained and in progress?), Isabelle/HOL (unmaintained?))
- formalisation of Vyper?
- formalisation of other EVM source languages (Solidity)
- static analysis / "formal verification" outside of ITPs  for smart contracts, EVM, etc. e.g. Dafny, Z3,
- smart contract verification outside of EVM-based chains?

# Project Team

How many people are working on this project?

Please list their names and roles for the project as well as how many hours per month will each person work on this project?

## Background and Prior Work

Give us a bit of info and include relevant links, if available! Please provide other projects or research papers (ideally public and/or open source), engagements or other types of proof that your team has the necessary experience to undertake the project you are applying for.

Any links for us to review? E.g. research papers, blog posts, etc.

Notes on team background:
- Deep compiler verification expertise: CakeML + various other compilers and
  formal verification projects
- Vyper compiler lead dev team: deep experience with the main target of the
  project, will ensure it actually gets used
- Deep Ethereum expertise and stake in its success: experience using Ethereum
  both as end user, contract writer, and as a home-staking (and Rocket Pool)
  node-runner and validator.

# Methodology

High-level Roadmap/milestones:
1. EVM semantics [must]
2. Vyper semantics [must -- could be subset]
3. Validation of the semantics [nice to have]
4. IR semantics [nice to have, depends on how much compiler is verified]
5. Compiler implementation in logic [must -- but can be small subset]
6. Validation of the compiler implementation [nice to have]
7. Compiler verification [must]

(can be broken down in a lot of detail, but maybe not for the application,
 except maybe as an example to show the next level of detail is possible)

1 and 2 already exist (ready to go in HOL4) in part (point also to the small grant already awarded for 2)

## How do you plan to achieve your research objectives?
Timeline

Please include a brief explanation on the milestones/roadmap, along with expected deliverables. Also outline how the funds will be used for the research project and or members of the team.

Milestone 1: title
Budget: based off hourly rate and number of hours
Number of hours (roughly)
summary of work, subtasks
Budget

# Requested grant amount and how this will be used

Notes:
- stipends for people to work on it
- indirect costs for university overheads
- we should be clear about the different levels of delivery possible at different budgets


Please provide an requested amount and outline of how the grant will be used. A detailed budget proposal would be helpful and some item you could include are:

    Principle Researchers Costs
    Other Staff Costs
    Hardware Costs
    Software Costs
    Data Collection Costs
    Indirect Costs


# Full project costing and milestones

### High-level Roadmap/Milestones:

Our roadmap to success is roughly composed of the following milestones. Time estimates (in person months) are provided to provide an indicative sense of the relative difficulty of implementing the various milestones.

1. **EVM Semantics** [Must] - 6 person months
   - Formalize execution model in HOL4
   - Cover all relevant opcodes and state transitions
   - Ensure alignment with latest EVM specifications
   - Mostly complete already, ~1 person month remaining

2. **Vyper Semantics** [Must] - 4 person months
   - Formalize core subset of Vyper, including in particular: ...**TODO**...
   - Collaborate with Vyper team on specification improvements
   - Document memory/storage layout and execution model
   - Reify view of the abstract Vyper machine to EVM state
   - Partially complete, ~2 person months remaining

2b. **Vyper Semantics Add-Ons** [Nice to have] - 3-6 person months
   - Parser
   - Type checking
   - Type soundness proof
   - Import resolution
   - Semantic analysis

3a. **Validation of EVM Semantics** [Nice to have] - 2-3 person months
   - Test against reference implementations
   - Prove key properties about the semantics

3b. **Validation of Vyper Semantics** [Nice to have] - 2-3 person months
   - Test against reference implementations
   - Prove key properties about the semantics

4. **IR Semantics** [Nice to have] - 6-9 person months
   - Formalize Venom IR for compiler intermediate representation
   - Specify IR transformations and optimizations

5. **Compiler Implementation in Logic** [Must] - 3-4 person months
   - Implement executable compiler in HOL4
   - Start with unoptimized version for core language subset
   - Extend to more features as verification progresses

6. **Validation of Implementation** [Nice to have] - 1 person months
   - Test against reference compiler output

7. **Compiler Verification** [Must] - 9-12 person months
   - Develop equivalence checking for bytecode (**TODO** why?)
   - Prove semantics preservation
   - Establish end-to-end correctness guarantees

### Timeline and Deliverables:

**Milestone 1: EVM and Core Vyper Semantics**
<!-- 10-22 months -->
- Budget: $352,000-$774,400 (based on 10-22 person months at $200/hour with 0 overhead)
- Deliverables:
  - HOL4 formalization of EVM execution model
  - HOL4 formalization of core Vyper subset
  - Documentation of formal semantics
  - Technical report on semantic design choices

  <!-- 3-5 months -->
**Milestone 2: Compiler Implementation and Initial Verification**
- Budget: $105,600-$176,000 (based on 3-5 person months at $200/hour with 0 overhead)
- Deliverables:
  - Executable compiler implementation in HOL4
  - Initial correctness proofs for subset of transformations
  - Test suite validating against reference compiler
  - Report on implementation approach

  <!-- 9-18 months -->
**Milestone 3: Complete Verification and Usable Compiler**
- Budget: $316,800-$633,600 (based on 9-18 person months at $200/hour with 0 overhead)
- Deliverables:
  - Complete semantics preservation proofs
  - Usable compiler implementation
  - Documentation for developers
  - Academic paper(s) describing the verification
  - Contributions to Vyper language specification

## Requested Grant Amount and Budget

TODO: big project and small project versions with total costs

### Budget Breakdown:

TODO: list the kinds of things the budget will be spent on
