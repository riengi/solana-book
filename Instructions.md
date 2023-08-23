# Solana Instructions



## Creating Account 


```ts
const createAccountIx = SystemProgram.createAccount({
    fromPubkey: payer.publicKey,            // signer
    newAccountPubkey: keypair.publicKey,    // new account pubkey
    lamports,                               // lamports to store in this account
    space,                                  // space to allocate
    programId: SystemProgram.ProgramId      // owning program for this account
})
```

Instruction are executed in order 
If any instruction fails, all transaction fails 

