<script lang="ts">
    import Contract from "../../components/ContractCard.svelte";
    import { ethers } from 'ethers';

    import contractsAllChains from "../../../generated/deployedContracts"
    import ContractFunction from "../../components/ContractFunction.svelte";
    
    let showView = true;
    let showWrite = true;
    let searchTerm = "";

    async function doThing() {
        //const x = await ethers.getNetwork();
        console.log(ethers.BrowserProvider);
    }

    let selected = {abi: []};
    function selectContract(contract) {
        selected = contract;
        console.log(contract)
    }

</script>
<div class="flex flex-row space-x-10">
    <div class="flex flex-col">
    {#each Object.entries(contractsAllChains) as [chain, contractsSingleChain]}

        <!-- <legend>{chain}</legend> -->
        {#each contractsSingleChain as contracts}
        {#each Object.entries(contracts["contracts"]) as [contractName, contract]}
                <Contract name={contractName} address={contract.address} network={contracts.name} on:click={() => selectContract(contract)}/>
        {/each}
        {/each}

    {:else}
        <p>No contracts Deployed...</p>
    {/each}
    </div>
    <div id="active_contract" class="grid grid-cols-2">
        <div class="flex flex-row col-span-2 space-x-4">
            <input type="checkbox" class="checkbox" id="showView" bind:checked={showView}>
            <label for="showView">Show View Functions</label>
            <input type="checkbox" class="checkbox" id="showWrite" bind:checked={showWrite}>
            <label for="showWrite">Show Write Functions</label>
            <input type="text" class="input w-full" placeholder="Search..." bind:value={searchTerm}/>
        </div>
        {#each selected.abi as item}

            {#if item.type == "function" && item.name.includes(searchTerm)}
                {#if item.stateMutability == "view" && showView}
                    <ContractFunction {item} />
                {:else if item.stateMutability != "view" && showWrite}
                    <ContractFunction {item} />
                {/if}
            {/if}


        {/each}
    </div>

</div>

