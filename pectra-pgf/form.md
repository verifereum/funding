# Brief project summary

Verifereum (https://verifereum.org) produces a formal model of the EVM in higher-order logic intended to support a broad range of formal verification uses, primarily as the basis for proving comprehensive correctness theorems for Ethereum applications. This project is to update the EVM semantics in Verifereum to fully conform to Pectra (from its current target conformance to Dencun).

# Why is your project important?

While audits can find bugs, mathematical and computer-checked verification proves the absence of entire classes of vulnerabilities. With billions of dollars secured by smart contracts, formal verification of applications on Ethereum provides the level of trustworthiness appropriate to the stakes. Ethereum's deterministic execution model, culture of immutability, and succinct applications (because code is expensive), make it an ideal application for formal verification, specifically the approach using an ITP (interactive theorem prover) adopted by Verifereum that enables deeply expressive correctness statements while bringing more highly-skilled proof engineering to bear.

# How is it different?

Verifereum is distinguished amongst formal verification projects in the following ways:

- General purpose for all Ethereum applications: supporting both verifying decompilation and verified compilation, the techniques enabled by our infrastructure are applicable in principle to arbitrary smart contract applications and prove theorems about the actual on-chain EVM bytecode of the program. This is in contrast to verification of source-level (e.g. Solidity) programs only, which means trusting the compiler and the verifier's semantics of the source language.
- Using higher-order logic: the deep expressivity possible in this formal system allows us to state (and prove) concisely and precisely the complex invariants and desirable properties appropriate to each application. This is in contrast to systems that restrict expressivity for the sake of greater automation.
- Proving theorems: by contrast with fuzzing or symbolic execution methods, we have stronger guarantees of exhaustiveness. When you have a theorem that covers all possible transactions that might interact with an application, you have a very strong guarantee of security for that contract.
- Using HOL4: the HOL Theorem Prover (HOL4) is built in such a way that its trusted code base (TCB), i.e. the "kernel" that needs to be correct for any theorems proved in the system to be trustworthy, is very small. Furthermore, HOL4 can export proofs via OpenTheory for independent verification, and the algorithms and design of the theorem prover have been formally verified themselves in the Candle theorem prover (a HOL theorem prover verified down to its implementation in machine code). This is in contrast to other interactive theorem provers (ITPs) that have a larger TCB or less conservative design.
