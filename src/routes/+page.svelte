<script lang="ts">
	import { account, modal, getBalance, disconnect, formatEtherRounded } from 'lib/web3';
	import { Button, Network } from 'components';
	import { browser } from '$app/environment';

	$: accountAddress = $account.address;

	$: isMiniPay = false;

	if (browser) {
		if (window && window.ethereum) {
			// User has a injected wallet

			if (window.ethereum.isMiniPay) {
				// User is using Minipay
				isMiniPay = true;
				// Requesting account addresses
				let accounts = window.ethereum.request({
					method: 'eth_requestAccounts',
					params: []
				});

				// Injected wallets inject all available addresses,
				// to comply with API Minipay injects one address but in the form of array
				console.log(accounts[0]);
				// @ts-ignore
				// accountAddress = $account.address;
				accountAddress = accounts[0];
			}

			// User is not using MiniPay
		}
	}

	function connectWallet() {
		modal.open({ view: 'Connect' });
	}
</script>

<div class="md:md-0 w-full flex items-center justify-center">
	<div class="w-[85%] my-5 flex items-center justify-center flex-col">
		<div class="h1">There you go... a canvas for your next Celo project!</div>
		{#if $account.isConnected || isMiniPay}
			<div class="pt-10 md:pt-0 mx-0 flex flex-col items-center justify-center w-full">
				<p>Your address:</p>
				<p>{$account.address}</p>
				{#await getBalance($account.address ?? accountAddress!)}
					<p>Balance: ...</p>
				{:then data}
					<p class="text-md">
						Balance: {formatEtherRounded(data.value)}
					</p>
				{/await}
				Extra wallet metadata available when present
				<Network />
				<Button onclick={disconnect} variant="destructive">Disconnect</Button>
			</div>
		{:else}
			<Button variant="secondary" onclick={connectWallet}>Connect</Button>
		{/if}
	</div>
</div>
