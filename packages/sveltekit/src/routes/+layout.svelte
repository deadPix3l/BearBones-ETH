<script lang="ts">
	import '../app.postcss';
	//import { mainnet, arbitrum } from 'viem/chains'

	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
    import { LightSwitch } from '@skeletonlabs/skeleton';

	// // Floating UI for Popups
	// // import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	// // import { storePopup } from '@skeletonlabs/skeleton';
	// // storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
  	import WalletConnect from '../components/WalletConnect.svelte';
	
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<a href="/"><strong class="text-xl">BearBones-ETH</strong></a>
				<a href="/debug" class="btn btn-sm variant-outline-primary ml-4">Debug</a>
				<a href="/blocks" class="btn btn-sm variant-outline-secondary ml-4">Block Explorer</a>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<LightSwitch />
				<WalletConnect />
				<button class="btn btn-sm variant-outline-tertiary">Faucet</button>
			</svelte:fragment>

		</AppBar>
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
	<div class="text-center w-full mx-auto" slot="pageFooter"> Built with <a href="#bearbonesETH" class="underline">BearBones-ETH</a></div>
</AppShell>

