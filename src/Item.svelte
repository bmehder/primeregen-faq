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

<!-- <svelte:head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
  />
</svelte:head> -->

<div class:open={isOpen}>
  <h3 on:click={handleClick}>
    <span>{question}</span>
    <i class="fas fa-chevron-down" />
  </h3>
  {#if selectedItem === index}
    <div transition:slide>{@html answer}</div>
  {/if}
</div>

<style>
  :global(#svelte-faq h3) {
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
  :global(#svelte-faq h3:hover, #svelte-faq .open h3) {
    background: #282568;
    color: #efefef;
  }
  :global(#svelte-faq div div) {
    padding: 1px 2rem;
    font-size: 18px;
    line-height: 1.5rem;
  }
  :global(#svelte-faq p:first-child) {
    padding-top: 1.5rem;
    font-size: 18px;
  }
  :global(#svelte-faq i) {
    transition: transform 200ms ease;
  }
  :global(#svelte-faq .open i) {
    transform: rotate(180deg);
  }
  :global(#svelte-faq .sublist) {
    margin-top: 0.5rem !important;
    padding-left: 1.5rem;
  }
  @media screen and (max-width: 600px) {
    :global(#svelte-faq div div) {
      padding: 1px 0.5rem;
    }
  }
</style>
