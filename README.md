# Sveltekit | Celo Composer

This is a starter kit for Sveltekit. It's a perfect starter kit to get your project started on Celo blockchain. It uses TailwindCSS for styling and wagmi for onchain communication.

## Setup & Installation


### Set environment variables

Create a copy of `.env.example` and rename it to `.env`.

#### Add Wallet Connect ID

Create a WalletConnect Cloud Project ID from [WalletConnect Cloud](https://cloud.walletconnect.com/)

Provide the WalletConnect Cloud Project ID in your `.env` file to use WalletConnect in your project. As shown in the `.env.example` file.

```typescript
TS_PUBLIC_PROJECT_ID=YOUR_EXAMPLE_PROJECT_ID;
```


### Install dependencies

Install all the required dependencies to run the dApp.

Using **yarn**

```bash
yarn
```

or using **npm**

```bash
npm i
```

> Sveltekit + Tailwind CSS Template does not have any dependency on hardhat.
> This starterkit does not include connection of Hardhat/Truffle with Sveltekit. It's up to the user to integrate smart contract with Sveltekit. This gives user more flexibility over the dApp.

- To start the dApp, run the following command.

```bash
yarn dev
```

## UI Components

To add a component from the shadcn library run:

```bash
npx shadcn-svelte@latest add <component-name>
```

The component will be added to the `src/libs/components/ui` dir


## Dependencies

- [Sveltekit](https://svelte.dev/) app framework
- [TailwindCSS](https://tailwindcss.com/) for styling
- [UI Components](https://www.shadcn-svelte.com/) - Svelte Shadcn  
- [Wagmi](https://wagmi.sh/) for onchain transactions

### Project Structure

```
├── src
│   ├── components (custom components)
│   │   ├── **/*.svelte
│   ├── lib
│   │   ├── components (shadcn components)
│   │   ├── utils
│   │   ├── web3 (Wagmi and web3 config files)
│   └── routes
│       ├── +page.svelte
│       └── docs
├── static (public files)
├── node_modules
├── README.md
├── package.json
├── other _config_files
└── .gitignore

```
## Web3 based operations

This can be carried out using `@wagmi/core` functions. 
The popular Wagmi hooks were designed for React, and are built on `@wagmi/core`. 
Since, wagmi doesn't have a hooks specific to Svelte we use the core library.

`lib/webs/client` wraps some of the `@wagmi/core` functions to a Svelte observable stream.


