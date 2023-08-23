## Tokens

Tokens are combinations of three different program:
1. Token Program (Solana Labs)
2. Associated Token Program (Solana Labs)
3. Metadata Program (Metaplex)


## Token Program instruction
* Mint - mints new token


## Associated Token Program 
* Ownership and transaction of SPL tokens

## Metadata Proram
* Metadata for token


## Instructions
* Create new account
* Initialize that account as a mint
* Create an associated token account
* Mint new tokens to that associated token account


## TokenConfig

```ts
const tokenConfig = {
    decimals: 2
    name: "Test Token",
    symbol: "TEST",
    uri: "https://test.project/info.json"
}
```