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

<div class="faq-item" class:open={isOpen}>
  <h3 on:click={handleClick}>
    <span>{question}</span>
    <i class="fas fa-chevron-down" />
  </h3>
  {#if selectedItem === index}
    <div transition:slide>{@html answer}</div>
  {/if}
</div>

<style>
  .faq-item h3 {
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
  .faq-item h3:hover,
  .faq-item .open h3 {
    background: #282568;
    color: #efefef;
  }
  .faq-item div {
    padding: 1px 2rem;
    font-size: 18px;
    line-height: 1.5rem;
  }
  :global(.faq-item p:first-child) {
    padding-top: 1.5rem;
    font-size: 18px;
  }
  .faq-item i {
    transition: transform 200ms ease;
  }
  .faq-item .open i {
    transform: rotate(180deg);
  }
  :global(.faq-item .sublist) {
    margin-top: 0.5rem !important;
    padding-left: 1.5rem;
  }
  @media screen and (max-width: 600px) {
    .faq-item div div {
      padding: 1px 0.5rem;
    }
  }
</style>
