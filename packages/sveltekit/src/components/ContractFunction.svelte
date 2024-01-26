<script lang="ts">
    export let item = {
        type: '',
        name: '',
        inputs: [
            {name: ''}
        ],
        stateMutability: ''
    };
</script>

{#if item.type == "function"}
    <div class="card p-4 m-4">
        <div class="flex flex-col space-y-2">
            {item.name}
            <form>
                {#each item.inputs as input}
                    <input class="input my-2" id={input.name} type="text" placeholder="{input.name}" required/>
                {/each}

                
                {#if item.stateMutability == 'view'}
                    <button class="btn btn-md w-full variant-filled-primary ">View</button>
                {:else if item.stateMutability == 'nonpayable'}
                    <button class="btn btn-md w-full variant-filled-warning">Transact</button>

                {:else}
                    Payable Functions not yet supported
                {/if}
            </form>
        </div>
    </div>
{/if}
