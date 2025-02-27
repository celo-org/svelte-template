<!-- Example -->
<script lang="ts">
	import { signMessage } from '@wagmi/core';
	import { toast } from 'svelte-sonner';
	import { wagmiConfig } from '$lib/web3';

	let signature: string | undefined;
	let label: string = 'Sign Message';

	async function handleSign() {
		label = 'Signing...';
		signature = '_';

		try {
			const _signature = await signMessage(wagmiConfig, {
				message: 'WalletConnect message'
			});

			//@ts-expect-error Wagmi Type bug
			if (_signature !== 'null') {
				signature = _signature;
				toast.success('Message signed successfully');
			} else {
				toast.error('The signature was rejected');
				signature = '_ personal_sign';
			}
		} catch (error) {
			toast.error((error as Error).message);
		} finally {
			label = 'Sign Message';
		}
	}
</script>

<div class="bg-accent py-2 w-full">
	<div class="space-y-4">
		<h3 class="font-bold text-lg">Sign Message</h3>
		<p class="text-left text-sm">
			Result: <span class="text-sm"> {signature ?? ''} </span>
		</p>
		<button class="btn variant-ghost-primary w-full" on:click={handleSign}>{label}</button>
	</div>
</div>
