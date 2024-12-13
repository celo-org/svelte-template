# Celo Svelte Template

- Run `yarn` to install packages
- Create an env file with your `VITE_PROJECT_ID` i.e web3modal project id
- Run `yarn dev` to run app


## Web3 based operations

This can be carried out using `@wagmi/core` functions. 
The popular Wagmi hooks were designed for React, and are built on `@wagmi/core`. 
Since, wagmi doesn't have a hooks specific to Svelte we use the core library.

`lib/webs/client` wraps some of the `@wagmi/core` functions to a Svelte observable stream.