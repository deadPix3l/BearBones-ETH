<script lang="ts">
import {
    connected,
    provider,
    chainId,
    chainData,
    signer,
    signerAddress,
    contracts
} from "ethers-svelte";



import { defaultEvmStores as evm } from "ethers-svelte";

function connectWallet() {
    evm.setProvider()
}

async function accountInfo() {
    const { name, chainId } = await $provider.getNetwork();
    //const balance = await $signer.getBalance();
    console.log(name);
    //console.log(balance);
    //return [name, balance];
}
</script>

{#if $connected}
    <button class="btn btn-sm variant-filled ">{$chainId}</button>
    <button type="button" class="btn btn-sm variant-filled" on:click={evm.disconnect}>{$signerAddress.slice(0,8)}...{$signerAddress.slice(-4)}</button>

{:else}
    <button type="button" class="btn btn-sm variant-filled" on:click={connectWallet}>Connect Wallet</button>
{/if}