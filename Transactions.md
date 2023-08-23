## Solana transactions



## Creating and sending transaction
```ts

const recentBlockhash = await connection.getLatestBlockhash().then(res => res.blockhash);

const message = new TransactionMessage({
    payerKey: payer.publicKey,
    recentBlockhash,
    instructions: [createAccountId],
}).compileToV0Message();


const tx = new VersionedTransaction(message);

// in this case, payer and also keypair are signing the transaction
tx.sign([payer, keypair]);

// sending transaction
const sig = await connection.sendTransaction(tx);

```