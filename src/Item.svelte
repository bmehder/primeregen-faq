<svelte:head>
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" />
</svelte:head>

<script>
	import { slide } from 'svelte/transition'
	
	export let item
	export let index
	export let selectedItem
	
	const { question, answer } = item
	
	$: isOpen = selectedItem === index
	
	const handleClick = () => {
		if (isOpen) {
			selectedItem = null
			return
		}
		selectedItem = index
	}
</script>

<div class:open={isOpen}>
	<h3 on:click={handleClick}>
		<span>{question}</span>
		<i class="fas fa-chevron-down"></i>
	</h3>
	{#if selectedItem === index}
	<div transition:slide>{@html answer}</div>
	{/if}
</div>

<style>
	div {
		padding: 0 1rem;
	}
	h3 {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
		padding: 2rem;
		background: #efefef;
		color: #282568;
		line-height: 1.5rem;
		cursor: pointer;
	}
	h3:hover, .open h3 {
		background: #282568;
		color: #efefef;
	}
	div div {
		padding: 1px 2rem;
		font-size: 18px;
		line-height: 1.5rem
	}
	i {
		transition: transform 200ms ease;
	}
	.open i {
		transform: rotate(180deg);
	}
</style>