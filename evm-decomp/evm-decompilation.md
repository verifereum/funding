# Verification of EVM Bytecode Programs via Decompilation into Logic

Notes:

The things that need to be built here:
- Program logic (Separation logic) for EVM bytecode programs
- Proof tools for making proofs about EVM bytecode programs in that logic

What properties do we want to prove?
- The most useful properties will apply to arbitrary transactions that call the
  contract being verified, in arbitrary machine states modulo invariants on the
  contract's own storage.
- (We also want to support suites of interacting contracts, i.e. whole
  applications that involve multiple contracts.)
- The exact correctness properties will depend on the application, but some
  properties will be generally useful such as not leaking funds except in the
  specific application-intended ways.
- So to demonstrate that this work is useful is to pick some good examples of
  applications and what we can verify about them.

Possible target examples, in order of complexity:
- Contrived examples of simple contracts that just do arithmetic or something
  like that. (Take inspiration from examples used for other FV tools.)
- Some of the Vyper examples, like an escrow or auction or fund-raising/pledging contract.
(more realistic and/or actually used from here)
- ERC20 token contracts including simple ones like WETH and more complex like USDC
- 0xSplits components
- Safe (or maybe a simpler) smart contract wallet / multisignature wallet.
(multi-contract from here)
- Liquity v1 or v2
- ENS (Ethereum Name Service)
- Uniswap v1 or v2
- Rocket Pool and/or Lido
- Uniswap v3 or v4

We can also look at open bug bounties (e.g., on immunefi) as a source of protocols to try verifying.

How to convince the reader that we can do this?
- Maybe we need to do one of the contrived examples for concreteness?
- Possibly without the separation logic? E.g. show an execution theorem
- The EVM semantics is written
- Point to machine-code verification work
- We have HOL4 expertise including proof automation, including the above
- EVM is a nice setting for verification: clear semantics, small programs, determinism, premium on correctness, etc.

We should include an example of some contract bytecode and what we expect the
decompiled version of it would look like in logic.

Who will be involved?
- Ramana
- Magnus
- Anyone else we can hire with the grant, and/or who wants to join for any amount

We can refer CakeML as evidence that we know how to make a project in which the
funder gets more than they pay for because the project is larger and more open
than any specific grant. Verifereum is intended to also be such a project.

## Project Abstract

In 3-5 sentences what problem are you trying to solve? (The project abstract may be used for for the winners announcement.)
Objectives

What are you hoping to accomplish with this grant? How do you define and measure success for this project?

### Outcomes

How does this project benefit the greater Ethereum ecosystem?

## Grant Scope

What are you going to research? What is the expected output?

## Related Work

What existing research is relevant to your project?
What is the specific gap your research is addressing within this context?

## Project Team

How many people are working on this project?

Please list their names and roles for the project as well as how many hours per month will each person work on this project?

### Background

Give us a bit of info and include relevant links, if available! Please provide other projects or research papers (ideally public and/or open source), engagements or other types of proof that your team has the necessary experience to undertake the project you are applying for.

Any links for us to review? E.g. research papers, blog posts, etc.

## Methodology

How do you plan to achieve your research objectives?

### Timeline

Please include a brief explanation on the milestones/roadmap, along with expected deliverables. Also outline how the funds will be used for the research project and or members of the team.

Milestone 1: title
Budget: based off hourly rate and number of hours
Number of hours (roughly)
summary of work, subtasks

## Budget

Requested grant amount and how this will be used

Please provide an requested amount and outline of how the grant will be used. A detailed budget proposal would be helpful and some items you could include are:

    Principal Researchers Costs
    Other Staff Costs
    Hardware Costs
    Software Costs
    Data Collection Costs
    Indirect Costs

