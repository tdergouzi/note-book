# Debug Record



## Verify contract failed

I deployed a contract on arbitrum-goerli using the Hardhat framework, and I use the Waffle flatten plugin to flatten my contract. However, I encountered an issue when trying to verify the contract due to differences in the contract bytecode. Here is my `hardhat.config.ts` file:

```typescript
 const DEFAULT_COMPILER_SETTINGS = {
   version: "0.8.9",
   settings: {
     optimizer: {
       enabled: true,
       runs: 1_000_000,
     },
     metadata: {
       bytecodeHash: 'none',
     },
   },
 }
 
  const config: HardhatUserConfig = {
   defaultNetwork: "hardhat",
   solidity: {
     compilers: [DEFAULT_COMPILER_SETTINGS]
   }
  }
```

The reason for the bug is the `metadata` configuration. If you set it up, the bytecode of the contract will be altered. Here is Solidity's explanation of the configuration:

```json
    // Metadata settings (optional)
    "metadata": {
      // Use only literal content and not URLs (false by default)
      "useLiteralContent": true,
      // Use the given hash method for the metadata hash that is appended to the bytecode.
      // The metadata hash can be removed from the bytecode via option "none".
      // The other options are "ipfs" and "bzzr1".
      // If the option is omitted, "ipfs" is used by default.
      "bytecodeHash": "ipfs"
    },
```

Remove the `metadata` configuration and redploy the contract again, verify will be successful.