FYI, next deadline: April 1st 2025 12:00 CEST (noon)

<!-- In 3-5 sentences what problem are you trying to solve? (The project abstract may be used for for the winners announcement.)
This form can be used to request support for your project. Note that releasing software, hardware and content under libre/open licenses, and the application of open standards where possible are transversal requirements for all. From our end we will provide a transparent and efficient selection process. Please check the (call-specific) guide for applicants for the call you are interested in.

Please also don't forget to look into our privacy statement about how we deal with your information (should be a pleasant surprise, actually — we really care about your privacy. Throughout the years we've funded the development of quite some widespread privacy enhancing technologies ourselves).

A practical point: we recommend to prepare longer answers offline, in case something goes wrong with your browser session. It is a light weight procedure, please don't wait until the last hour before the deadline before submitting — deadlines are hard. -->

# Please select a call
<!-- In 3-5 sentences what problem are you trying to solve? (The project abstract may be used for for the winners announcement.)
In the list of current calls below, please indicate the call topic you are responding to. Note that some larger funds (like the NGI0 Commons Fund) and smaller funds with targeted calls (like NGI Fediversity, TALER and Mobifree — all part of the Next Generation Internet initiative) will have some special scope or conditions. You'd better have a look at the respective guides for applicants before you submit a proposal. If in doubt, submit to our open call and mention in the application that you are okay with us allocating your proposal to the most suitable fund. -->

## Thematic call:
- NGI Zero Commons Fund
- NGI TALER
- NGI Mobifree
- NGI Fediversity Research & Higher Education Technology Fund
- **Open Call**
- Other

NOTE: propose to select "open call" so that grant reviewer can align best option (for highest chances of success / best funding option)

# Contact information

- Your name: *TO-DO*
- Email address: james@verifereum.org
- Phone number: n/a
- Organisation: Verifereum
- Country: United Kingdom

# General project information

- Project name: Verifereum
- Website / wiki: https://verifereum.org/

<!-- Please be short and to the point in your answers; focus primarily on the what and how, not so much on the why. Add longer descriptions as attachments (see below). If English isn't your first language, don't worry — our reviewers don't care about spelling errors, only about great ideas. We apologise for the inconvenience of having to submit in English. On the up side, you can be as technical as you need to be (but you don't have to). Do stay concrete. Use plain text in your reply only, if you need any HTML to make your point please include this as attachment. -->

# Abstract: Can you explain the whole project and its expected outcome(s):
    
Verifereum is a formal model of the EVM in higher-order logic  intended to support a broad range of formal verification uses, primarily as the basis for proving comprehensive theorems about Ethereum applications (i.e., decentralised applications / smart contracts) ensuring that they are implemented correctly and have desirable / intended properties such as not being exploitable by malicious on-chain interactions. Verifereum will help safeguard the future of the internet.

The Verifereum project aims to maintain an up-to-date EVM semantics that accurately models on-chain execution for all applications live on mainnet (and other EVM chains), and hence to remain relevant as Ethereum hardforks are deployed.

The blockchain audit industry, currently worth $3bn* is expected to grow tenfold over the next 5 years (https://www.marketsandmarkets.com/PressReleases/blockchain-security.asp), signaling the tremendous demand for rigorous scrutiny of on-chain apps. By mathematically proving that a contract behaves exactly as expected relative to a clearly defined specification, formal verification offers the highest assurance of vulnerability-free code.

Verifereum's expected outcomes include but are not limited to:

- Smart contract security: Verifereum will enable developers to mathematically prove that their smart contracts are exempt from all exploits of a certain type. This will, in turn, enhance the overall trust in Ethereum as a platform.
- Compiler reliability: The Ethereum ecosystem, with its reliance on a couple of languages with no verified compilers, is particularly vulnerable to compiler bugs. By focusing on compiler verification, starting with Vyper, Verifereum will increase confidence in the correctness of compiled smart contract code.
- Advancement of formal methods: Verifereum will push forward the state-of- the-art in formal verification on Ethereum and provide a more expressive and trustworthy framework for developers to work with.
- Community building and education: Drawing upon the experience and network acquired while building the CakeML community, Verifereum will help grow the pool of developers skilled in formal verification methods. We plan to do so by onboarding technical and non-technical contributors, providing documentation and tutorials, and organising outreach events.

*$8bn+ has been lost in various smart contact hacks since the launch of Ethereum.
    
## Have you been involved with projects or organisations relevant to this project before? And if so, can you tell us a bit about your contributions?

[check other grant apps (Vyper, too)]

# Requested support

- Requested Amount (in Euro): €50,000.00

### Explain what the requested budget will be used for? Does the project have other funding sources, both past and present?
<!-- (If you want, you can in addition attach a budget at the bottom of the form) -->

1. Developer salaries x3 months (€100 per hour per person, ~€72,000 for 2x developers @ 120hrs per month) but capped at maximum funding allocation
3. other ad hoc costs associated with brand awareness

# Compare your own project with existing or historical efforts.

[overview of formal verification of Ethereum applications, different ways based on XYZ, dafny, fuzzing] better than prev ... 

Verifereum has already made significant progress in formalising the EVM in HOL4, providing a solid foundation for our work. Magnus Myreen's [research on decompilation](https://www.cl.cam.ac.uk/~mom22/decompilation.html) into logic has been successfully applied to various architectures, including x86, ARM, and MIPS, demonstrating its versatility and effectiveness.

The gaps we are filling:

- More expressive logic than many other approaches to verification of EVM programs, which means we can verify deeper correctness properties
- Scalable expressivity: we can automate our proofs but, in cases where automation fails, there is always the option to do fully interactive proof for the hard parts
- Trustworthiness of the underlying theorem prover HOL4, with its conservative design and small well-reviewed kernel

Related work includes:

- KEVM: [A formal verification tool for Ethereum VM bytecode](https://dl.acm.org/doi/10.1145/3236024.3264591)
- F\*: [EVM-Vale: Formal Verification of EVM Bytecode Using Vale](https://link.springer.com/chapter/10.1007/978-981-97-0006-6_3)
- Dafny: [Formal and Executable Semantics of the Ethereum Virtual Machine in Dafny](https://dl.acm.org/doi/10.1007/978-3-031-27481-7_32)
- Runtime Verification's KEVM formalisation of the EVM in the K Framework (and other EVM formalisations...)
- Deductive verification of smart contracts in Dafny -- must start with a contract written in Dafny
- seL4 and other BA or decompilation work in Isabelle
- HOLBA
- DeepSEA and Scilla, which provide high-level languages with formal semantics that compile to EVM
- The Certora Prover and similar tools that use SMT solvers for EVM verification

**EVM Formalisations**: Previous and current work includes formalisations in [K](https://doi.org/10.1109/CSF.2018.00022), [Lean4](https://github.com/NethermindEth/EVMYulLean), [Dafny](https://github.com/Consensys/evm-dafny), [ACL2](https://www.kestrel.edu/research/ethereum/), [Coq](https://doi.org/10.48550/arXiv.1810.04828), and [Isabelle/HOL](https://doi.org/10.1145/316708); additionally there are executable specifications such as [EELS](https://github.com/ethereum/execution-specs/) and [hevm](https://github.com/ethereum/hevm). Each of these approaches has different strengths and weaknesses, although some are incomplete or no longer maintained. Our HOL4 formalisation will be both comprehensive and maintained, and leverage the strengths of HOL4. Unlike K or Dafny which are based on first-order logic, HOL4 is based on higher-order logic whose semantics are [much more expressive](https://philpapers.org/rec/FARTSV). This allows for more complex and comprehensive proofs, beyond simple assertions about a contract's expected behaviour. HOL4 has been [formally proven sound](https://www.cl.cam.ac.uk/~jrh13/papers/holhol.html) and has a very small and well reviewed kernel.

# What are significant technical challenges you expect to solve during the project, if any?

- Complete executable specification of the EVM in logic
- Enable trustworthy high level reasoning about the bytecode programs
- First production grade verified complier for Ethereum


# Describe the ecosystem of the project, and how you will engage with relevant actors and promote the outcomes?

> Smart contract security is paramount to the Ethereum ecosystem, where over 70 million contracts secure hundreds of billions of dollars of value. The blockchain audit industry, currently worth $3 billion is expected to grow tenfold over the next 5 years (https://www.marketsandmarkets.com/PressReleases/blockchain-security.asp), signaling the tremendous demand for rigorous scrutiny of on-chain apps. By mathematically proving that a contract behaves exactly as expected relative to a clearly defined specification, formal verification offers the highest assurance of vulnerability-free code. 
> 
> Despite the strong need and demand for higher safety and formal verification of smart contract applications and compilers, there is still a supply constraint due to a dearth of tooling, educational resources, and qualified practitioners. Verifereum aims to provide a complete and well-documented framework for the formal verification of any Ethereum application while growing an active community of technical and non-technical contributors to foster the adoption of formal methods.
>
> There are many tools to improve smart contract security (static analysis, fuzzing...). They provide assurance against bugs, but not at the level of formal verification. Formal verification tools like Solidity's SMTChecker work on a high-level language and do not protect against bugs introduced by the compiler. For a contract's binary to be formally verified, its language's compiler itself must be formalized or the compiled binaries must be verified against an EVM specification.
> 
> Formal verification efforts so far, like KEVM or EVM-Dafny, have targeted the latter option. Likewise, the more recent EVM-Vale model in F*/Vale which only handled a subset of the EVM's semantics. Earlier projects gave formal specifications in Isabelle/HOL and CoQ but are not actively used. Work on a Lean model is underway (https://tinyurl.com/drtap9az) but does not fully pass the Ethereum Test Set.
>
> Verifereum solves these approaches' limitations and adds new contributions
> 
> - Compiler verification: Current models target compiled bytecode rather than compilers. By contrast, Verifereum can verify both compilers and compiled code. One of our goals is to fully verify the Vyper compiler.
>
> - Decompilation into logic: Verifereum will offer tooling to decompile EVM bytecode programs into logic, regardless of their original language, to automate verification (https://tinyurl.com/3zbyzpk2). There is nothing similar available for Ethereum applications yet.
>
> - Reliability: Verifereum uses HOL4 which is more trustworthy than the frameworks used by other projects such as K, Dafny, or Vale. HOL4 has been formally proven sound (https://tinyurl.com/mxjb63v3). Its trusted code base is small and extensively reviewed.
> 
> - Expressivity: Unlike K or Dafny which are based on first-order logic, HOL4 is based on higher-order logic which has more expressive semantics (https://philpapers.org/rec/FARTSV), allowing for more complex proofs.
>
> - Depth: HOL4 can be used to prove arbitrarily complex functional correctness properties.
> 
> Verifereum is fully free and open source. It aims to become the reference framework for formal verification work for all Ethereum applications and to build a large community of contributors. It will contribute to securing the EVM (by providing another formal model of its mechanics), its programming languages such as Solidity and Vyper, and potentially any set of smart contracts. 
> 
> While Verifereum may serve as the basis for for-profit ventures in the future (for instance, auditing or consulting), the formal specifications, research, proofs, and documentation will always remain free and open source.
>
> Ultimately, Verifereum will engage with relevant actors via wider community engagement including but not limited to:
> - attendance at conferences and / or workshops
> - online contributions via Discord, Zulip (including the Verifereum community itself), e.g., Rocket Pool (etc.)
> - representation within formal verification community at the Ethereum Foundation 
> - academic, research based collaborations
>
> Verifereum will be active and promote work and progress on other channels such as X, @Verifereum

## Attachments ???
<!-- Attachments: add any additional information about the project that may help us to gain more insight into the proposed effort, for instance a more detailed task description, a justification of costs or relevant endorsements. Attachments should only contain background information, please make sure that the proposal without attachments is self-contained and concise. Don't waste too much time on this. Really.Accepted formats for attachments are: 
HTML, PDF, OpenDocument Format and plain text files.
(The total size of attachments must not exceed 50 MB) --> 
