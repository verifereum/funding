# Verification of EVM Bytecode Programs via Decompilation into Logic

## The things that need to be built:
- Program logic (Separation logic) for EVM bytecode programs
- Proof tools for making proofs about EVM bytecode programs in that logic

## What properties do we want to prove?
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

## Possible target examples, in order of complexity:
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

## Concrete example

Here is contract bytecode that reads the contract's balance of a token and transfers it to the hardcoded owner address.

First we see the raw bytes (in hex):
``` hex
5f6370a082315f5230602052602060406024601c5f739876543210987654321098765432109876
5432105af11563a9059cbb5f527312345678901234567890123456789012345678906020526020
5f6044601c5f7398765432109876543210987654321098765432105af15f511661007357fd5bf3
```

Disassembling these bytes, we can see the opcode at each code location:
``` evm
00000000: PUSH0
00000001: PUSH4 0x70a08231
00000006: PUSH0
00000007: MSTORE
00000008: ADDRESS
00000009: PUSH1 0x20
0000000b: MSTORE
0000000c: PUSH1 0x20
0000000e: PUSH1 0x40
00000010: PUSH1 0x24
00000012: PUSH1 0x1c
00000014: PUSH0
00000015: PUSH20 0x9876543210987654321098765432109876543210
0000002a: GAS
0000002b: CALL
0000002c: ISZERO
0000002d: PUSH4 0xa9059cbb
00000032: PUSH0
00000033: MSTORE
00000034: PUSH20 0x1234567890123456789012345678901234567890
00000049: PUSH1 0x20
0000004b: MSTORE
0000004c: PUSH1 0x20
0000004e: PUSH0
0000004f: PUSH1 0x44
00000051: PUSH1 0x1c
00000053: PUSH0
00000054: PUSH20 0x9876543210987654321098765432109876543210
00000069: GAS
0000006a: CALL
0000006b: PUSH0
0000006c: MLOAD
0000006d: AND
0000006e: PUSH2 0x73
00000071: JUMPI
00000072: REVERT
00000073: JUMPDEST
00000074: RETURN
```

In Huff code (an assembly-like language for EVM bytecode), this contract looks like this, with comments:
``` huff
    #define constant OWNER = 0x1234567890123456789012345678901234567890
    #define constant TOKEN = 0x9876543210987654321098765432109876543210

    push0 // put a 0 on the stack for the eventual revert/return
    __FUNC_SIG("balanceOf(address)") push0 mstore address 0x20 mstore
    0x20 0x40 // store self's token balance at 0x40
    0x24 0x1c // function signature + one argument
    push0 [TOKEN] gas call
    iszero // assume balanceOf succeeded, convert to 0 for revert/return
    __FUNC_SIG("transfer(address,uint256)") push0 mstore [OWNER] 0x20 mstore
    0x20 push0 // store result of transfer at 0x00
    0x44 0x1c // function signature + two arguments
    push0 [TOKEN] gas call
    push0 mload and // require no revert & return of true
    if jumpi revert if: return
```

TODO: show a separation logic triple for a small part of this code (e.g., the first four lines)
TODO: show a separation logic triple for the first call
TODO: show function representing the code in each of the above triples
TODO: show a separation logic triple for the whole contract
TODO: show function representing the whole contract

## How to convince the reader that we can do this?
- Maybe we need to do one of the contrived examples for concreteness?
- Possibly without the separation logic? E.g. show an execution theorem
- The EVM semantics is written
- Point to machine-code verification work
- We have HOL4 expertise including proof automation, including the above
- EVM is a nice setting for verification: clear semantics, small programs, determinism, premium on correctness, etc.

We should include an example of some contract bytecode and what we expect the
decompiled version of it would look like in logic.

## Who will be involved?
- Ramana
- Magnus
- Anyone else we can hire with the grant, and/or who wants to join for any amount

We can refer CakeML as evidence that we know how to make a project in which the
funder gets more than they pay for because the project is larger and more open
than any specific grant. Verifereum is intended to also be such a project.
