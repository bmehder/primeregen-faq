<script>
  import { wound, knee } from './data'
  import Item from './Item.svelte'

  let selectedItem = null
</script>

<div class="faq">
  <h2>Wound Care</h2>
  <section>
    {#each wound as item, index}
      <Item {item} bind:selectedItem {index} />
    {/each}
  </section>

  <h2>Knee Pain</h2>
  <section>
    {#each knee as item, index}
      <Item {item} bind:selectedItem {index} />
    {/each}
  </section>
</div>

<style>
  .faq section {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    margin-bottom: 2rem;
  }
  .faq h2 {
    font-size: 2rem;
    line-height: 2em;
  }
</style>
