<script lang="ts">
    export let name;
    export let address;
    export let network;

    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

</script>

<div class="card hover:scale-105 active:scale-95 transition-transform duration-300 " on:click={() => dispatch('click')}>
    <div class="flex flex-col p-4 pr-40 m-2 bg-tertiary-800 rounded-md relative">
        <span>{name} ({address.slice(0,6)}...{address.slice(-4)})</span>
        <span>{address.slice(0,6)}...{address.slice(-4)}</span>
        <span class="absolute top-0 right-1 text-secondary-200">{network}</span>
    </div>
</div>
