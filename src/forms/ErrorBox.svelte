<script>
  import { fade, fly } from 'svelte/transition';
  export let msg = null
</script>

{#if msg}
  <div  in:fade out:fade class="mt-2 bg-red-400 border-red-200 text-white p-2 rounded flex  mb-5">
    <div class="flex">
      <div class="border px-2 rounded mr-3 bg-white text-red-600">Error</div>
      <div>{msg}</div>
    </div>
  </div>
{/if}