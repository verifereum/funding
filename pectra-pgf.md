# Project Abstract

The proposed project is: Update the formal semantics of the EVM defined in Verifereum for the Pectra upgrade.

Verifereum is a formal model of the EVM in higher-order logic intended to support a broad range of formal verification uses, primarily as the basis for proving comprehensive theorems about Ethereum applications (i.e. decentralised applications / smart contracts) ensuring that they are implemented correctly and have desirable/intended properties such as not being exploitable by malicious on-chain interactions.

The Verifereum project aims to maintain an up-to-date EVM semantics that accurately models on-chain execution for all applications live on mainnet (and other EVM chains), and hence to remain relevant as Ethereum hardforks are deployed.

# Project Team

## Team members:

Ramana Kumar is the lead contributor for the Verifereum project, and will take the lead on this upgrade project too.

We will also accept and encourage contributions from the open-source community supporting Verifereum, including (at time of writing) [six additional GitHub contributors](https://github.com/verifereum/verifereum/graphs/contributors).

## Background

Ramana has a PhD in computer science and has done extensive academic research on formal verification (https://scholar.google.com/citations?user=OyX1-qYAAAAJ&hl=en&oi=sra). He is a world leading expert on compiler verification and a key contributor to CakeML, a verified implementation of ML and one of a handful of formally verified compilers. An active contributor to the liquid staking derivative ecosystem on Ethereum, Ramana combines his expertise in formal verification with a deep knowledge of the EVM. His background makes him uniquely qualified to build the Verifereum EVM formal verification framework, and Verifereum-based projects for application verification (including via verified compilation).

The project is entirely free and open source, hosted on [GitHub here](https://github.com/verifereum/verifereum).

# Relevant Pectra EIPs

Since the EVM semantics is primarily concerned with the Execution Layer (EL) of Ethereum, all the Pectra EIPs that touch the EL are relevant. This is _all_ the Pectra EIPs except for EIP-7549 (Move committee index outside Attestation) which only touches the Consensus Layer.

# Objectives

List the project goals:

- Goal 1: Update the formal EVM semantics for each of the 10 relevant Pectra EIPs
- Goal 2: Ensure the updated semantics passes the EL test suites (as updated for Pectra)

# Outcomes

The successful completion of this project will provide several benefits to the Ethereum ecosystem:

1. Enhanced Security: By maintaining an up-to-date formal model of the EVM that incorporates all Pectra upgrade changes, we enable rigorous formal verification of smart contracts against the latest protocol that is live on mainnet. This contributes to the security and reliability of the Ethereum ecosystem.

2. Developer Tools: The updated semantics will serve as a foundation for developing and maintaining tools that help developers write more secure smart contracts as part of the Verifereum project. This includes both automated verification tools and frameworks for manual proof construction.

3. Academic Research: The formal model will support academic research into formal verification for Ethereum applications as well as verified implementations of the EVM. This helps bridge the gap between academic research and practical blockchain development.

# Grant Scope

The focus an primary deliverable for this project is a complete and executable specification of the EVM in higher-order logic that is up-to-date with respect to the Pectra network upgrade.

This project builds on the existing Verifereum EVM which formalises the Dencun specification, so is scoped as making the necessary changes to incorporate the Pectra EIPs.

Expected outputs:

1. A freely available complete formal specification of the EVM defined in the HOL4 theorem prover, building on the existing specification available at https://github.com/verifereum/verifereum.

2. Theorems demonstrating that the above specification passes the same EVM test suites (when the tests have been updated for the Pectra upgrade) that are used to validate Ethereum's execution clients, i.e., https://github.com/ethereum/tests and https://github.com/ethereum/execution-spec-tests.

# Methodology

We will follow the same proof-engineering practices that have produced Verifereum to update the EVM semantics therein:

1. Development Phase:
   - Analysis of each relevant Pectra EIP
   - Iterative decision-making about how to incorporate each change into the existing EVM semantics
   - Translation of the natural-language specifications into definitions in higher-order logic

2. Validation Phase:
   - Update the existing Verifereum testing infrastructure to target the Pectra fork
   - Execution of the tests in the official Ethereum test suites
   - Iteration on the semantics as required to ensure the Pectra tests all pass

3. Tools and Technologies:
   - HOL4 theorem prover for formal specification
   - Ethereum test suites
   - Git (including GitHub) for version control and collaboration
   - Zulip for discussion and onboarding new collaborators

# Timeline and Budget Allocation

We aim to deliver on average 2 EIPs per week at a cost of $1000 each, to be used entirely to pay stipends for the engineering work. Although some EIPs will be more difficult than others, the budget is amortised over them all. There are 10 relevant EIPs.

Total Budget: $10,000, 5 weeks
