# Programming on Solana - basics


## Accounts
Accounts are key elements of Solana blockchain. Basically everything is an Account on Solana. 

Accounts are like kind of files in Linux OS. 

### Account attributes
* unique 256-bit addresses
* hold some balance of SOL
* Can store arbitrary data
* Data storage is paid with Rent


## Default permissions
* Anyone can credit SOL or read data on/from account
* Only account's owner can debit SOL or modify data


```js

{
    key: number,                // address of the account
    lamports, number,           // lamports held / solana balance
    data: Uint8Array,           // data stored in the account
    is_executable: boolean      // is this account a program or just data account? 
    owner: PublicKey            // account owner, program with write access
}


```


## Programs
Programs are basically smart contracts. 
* special kkid of accounts
* data is eBPF bytecode (Berkley Packet filtered bytecode)
* written in Rust, C/C++, Python


* Programs are stateless - they read and write data to other accounts, allows paralelism
* Must be owner of an account to modify
* Programs process instructions
* programs can send istructions to other programs via CPI (Cross Program Invocation)


## Summary
* everything is an account
* All accounts hold SOL
* All accounts can store arbitrary data
* Accounts can also store executable programs
* Accounts are passed into programs

## Instruction

```js
{
    program_id: number,     // program this instruction is for
    keys: Array<{           // accounts involved in the instruction
        key: PublicKey,
        is_mutable: boolean,
        is_signer: boolean
    }>,
    data: Uint8Array,       // Action, args
}
```

## Transaction
Bundle of instructions.

Transaction is sent to RPCs/Validators on the Solana Network, it processed 


```js
{
    message: {
            instructions: Array<Instruction>,   // list of transactions
            recent_blockhash: number,           // used for deduplication of transactiosn
            fee_payer: PublicKey                // who pays the fee for the transaction
    },
    signers: Array<Uint8Array>                  // signers for data modification of debit
}
```


## Summary
* programs are invoked by instructions
* instruction are sent via transactions
* transactions are atomic
* transactions must be signed

## Transaction lifecyle

1. Client build the instructions
2. Client put instruction into transactions
3. Client sents the transaction to the RPC Client
4. RPC client forwards all the transactions to the voting validators
5. Validators will use Solana Runtime that will execute every instruction within transaction
6. Each instruction will call to specific program 
7. Program does what it is implemented to do

