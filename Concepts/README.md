# Solana concepts

## About
* Consensus algorithm: Proof of History

## Terminology
* __Cluster__: A cluster is a network of validators that make up an instance of the Solana blockchain. Testnet, Devnet and Mainnet Beta are the clusters primarily recognized by the Solana community. Testnet and Devnet are used for testing and development. Mainnet Beta is the instance where tokens are recognized to have monetary value. But there is no reason other clusters could not exist.
* __Epoch__: Currently ~3 days. This period exists primarily to schedule validators but also times other events such as rent collection and rewards distribution.
* __Accounts__: An account is essentially a file with an address (pubkey) that lives on the Solana blockchain. If you need to store data on chain it gets stored in an account (like EOSIO RAM). Accounts live in the memory of the network of validators. An account must pay rent (see below) in order to persist on chain.
* __Sealevel__: The solana network runtime that enables the parallel execution of instructions and transactions. Though very different in ,implementation and modeling, it is equivalent to Ethereum VM (EVM).
* __Programs__: On Solana smart contracts are called programs. A program is just an account that has been marked executable. Once a program has been deployed on chain it can be read and interacted with via instructions (see below).
* __Program ID__: The public key of the program.
* __Account Ownership__: Accounts are owned by programs which are indicated by a Program id in the metadata “owner” field.
* __Native Programs__: “Special” programs that are required to run the network.
* __System Program__: The system program is responsible for creating new accounts, and assigning account ownership.
* __BPF Loader__: The BPF Loader program is responsible for deployment, upgrades and instruction execution of solana programs.
* There are other native programs but these are the more relevant programs for solana programming.
* __Token Programs__: A kind of program that implements a fungible or non fungible token other than the native $SOL token.
* __Associated Token Accounts__: If an account holds any token other than the native Solana token it will have an associated token account for each type of token it holds.
* __Instructions__: What is called in order to execute a function of a program.
* __Sysvar__: An account which enforces certain variables of the network such as epoch, rent, validator rewards, etc…
* __Rent__ (like EOSIO RAM): The network charges rent (in $SOL) for data held in accounts, since this takes up validator network resources. An account can be exempt from rent collection if it has 2 years of rent in it’s balance. Rent is collected every epoch. If an account is unable to rent it will no longer load.
* __Program Derived Addresses (PDAs)__: PDAs enable the transfer of an account’s ownership from one program to another. This is useful for situations that require an escrow account such as auctions, DEXs, swaps, etc…
* __Cross Program Invocation__: Calling a program from another program. This is helpful for more complex on chain actions. Such as executing an instruction of an associated token account program during a token swap.