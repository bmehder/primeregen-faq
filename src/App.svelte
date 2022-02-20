<script>
	import { data } from './data'
	import Item from './Item.svelte'
	
	let selectedItem = null
</script>

<section>
	{#each data as item, index}
		<Item {item} bind:selectedItem {index} />
	{/each}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
	}
</style>