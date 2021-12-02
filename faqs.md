### Q. Which encryption is used in Solana?
ed25519

### Q. Which hashing is used in Solana?
sha256

### Q. What is contract called here?
Program

### Q. What is EOA (in Ethereum) called here?
Account

### Q. Does data & code stored in programs here?
No.

Code and data is separated.

### Q. Where the data is stored?
In the accounts

### Q. Who creates this account required for storing data?
Program creates it an account like this in `initialize` function of a program:

```
...
    #[account(init, payer = user, space = 16 + 16)]
    pub vote_account: Account<'info, VoteAccount>,

...
```

The program owns these accounts. This leads to less boilerplate and less code to reason about.


### Q. Where the code is stored?
In the programs.

Programs need to fetch the data from an account, then it is mentioned like this:

```
#[account]
pub struct VoteAccount {
    pub crunchy: u64,
    pub smooth: u64,
}
```


### Q. Does the data persistence cost?
Yes.

Every account has to give rent or give rent for worth of 2 years. Everyone gives the 2 years of rent. In this way, the account is exempted from rent.

### Q. Is the account owned by anyone?
Yes, by the system program (by default). 

### Q. How many times accounts can be assigned to a new owner?
Only once.

### Q. How does the Solana account address look like?
ed25519 pubkeys and the corresponding privkey is retained by the user for signatures.

### Q. Which model is followed in Solana?
Program/Account model.

Pros:

- Unlike on EVM, EOSIO blockchains, here one doesn't need to deploy code to create a new token. Rather this is taken care by the 'spl token program'. These is followed:
	+ you create an account that can mint tokens, and more accounts that can receive them.
	+ the mint address uniquely determines the token type, and these are all passed as arguments to one static program instance

### Q. What are the functions called here?
Instruction (in Solana) <--> Method (in EVM) <--> Action (in EOSIO)

multiple instructions can be bundled into a __message__ called "__transaction__".

### Q. What is the replacement of `nonce` here?
`blockhash`. Every message contains this.

### Q. When the `solana-test-validator` command is used, then where exacty the validator's info is stored?
It is stored in a file in the folder named `test-ledger/` of current directory the terminal opened at. It looks like this:

```
.
├── accounts
│   ├── 0.0
│   ├── 0.1
│   ├── 0.2
│   ├── 0.3
│   ├── 0.38
│   ├── 0.4
│   ├── 1.5
│   ├── 10.14
│   ├── 10.56
│   ├── 100.171
│   ├── 100.237
│   ├── 11.58
│   ├── 99.168
│   └── 99.239
├── admin.rpc
├── faucet-keypair.json
├── genesis.bin
├── genesis.tar.bz2
├── ledger.lock
├── rocksdb
│   ├── 000077.sst
│   ├── 000078.sst
│   ├── 000079.sst
│   ├── 000080.sst
│   ├── 000081.sst
│   ├── 000082.sst
│   ├── 000083.sst
│   ├── 000085.log
│   ├── CURRENT
│   ├── IDENTITY
│   ├── LOCK
│   ├── LOG
│   ├── LOG.old.1638423285952250
│   ├── MANIFEST-000084
│   ├── OPTIONS-000117
│   └── OPTIONS-000119
├── snapshot
│   └── 100
│       └── 100
├── snapshot-100-F8SWyJ3qoE4soxNHLfbExwhpzBegXN7R5qLvZaGuSkhR.tar
├── tower-AzGBwL6WRyjbZc5AjLqN3WaMFxKDWFE92zZu5mFedLfQ.bin
├── validator-1638423285664.log
├── validator-keypair.json
├── validator.log -> validator-1638423285664.log
└── vote-account-keypair.json

4 directories, 325 files
```

