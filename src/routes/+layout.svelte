<script lang="ts">
	import '../app.css';
	import { Toaster } from 'svelte-sonner';
</script>

<div class="m-0 p-0 no-scrollbar min-h-screen">
	<div class="flex items-center justify-between py-2 px-5 bg-primary w-screen bg-yellow-500">
		<a href="/">
			<div class="flex items-center">
				<img src="/logo.svg" class="size-[50px] rounded-full mr-5" alt="logo" />
				<strong class="text-[12px] md:text-xl md:uppercase">Home</strong>
			</div>
		</a>
		<div class="flex gap-x-5 items-center">
			<a class="hidden md:block hover:text-white" href="/docs"> Docs </a>
			<a
				class="hidden md:block hover:text-white"
				href="https://faucet.celo.org/"
				target="_blank"
				rel="noreferrer"
			>
				Faucet
			</a>
			<a
				class="hidden md:block hover:text-white"
				href="https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.26+commit.8a97fa7a.js"
				target="_blank"
				rel="noreferrer"
			>
				Remix
			</a>
			<w3m-core-button balance="hide" icon="hide" />
			<w3m-network-switch />
		</div>
	</div>

	<slot />
</div>
<Toaster position="top-center" />
