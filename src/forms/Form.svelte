<script>
  import InputBox from "./InputBox.svelte"
  export let formItems = []
  export let onChange = () => {}

</script>

{#each formItems as item, i}
  {#if item.type === 'input'}
    <InputBox bind:item={item} i={i} onChange={(e) => { onChange(e) }}/>
  {/if}
{/each}

<style>

  input { 
    margin-bottom: 3px
  }
</style>