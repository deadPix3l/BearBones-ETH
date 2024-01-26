<script lang="ts">
	import { tableMapperValues } from '@skeletonlabs/skeleton';
	// Components
	import { Table, TabGroup, Tab, CodeBlock, type TableSource } from '@skeletonlabs/skeleton';


	// Local
	let sourceData = [
	];

	// Table Simple
	const tableSimple: TableSource = {
        head: ["Transaction Hash", "Function Called", "Block Number",	"Time Mined", "From", "To",	"Value (ETH)"],
		body: tableMapperValues(sourceData, ['hash', 'function', 'block', 'time', 'from', 'to', 'value']),
		meta: tableMapperValues(sourceData, ['hash', 'function', 'block', 'time', 'from', 'to', 'value']),
		foot: ['Total Elements', '', `<span class="badge variant-soft-primary">${sourceData.length} Elements</span>`]
	};

	// On Row Selected
	function onSelected(meta: unknown): void {
		console.log('on:selected', meta);
	}
</script>

<div>
<Table source={tableSimple} />
</div>