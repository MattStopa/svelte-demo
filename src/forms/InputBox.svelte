<script>
  import ErrorBox from "./ErrorBox.svelte"
  export let item = {}
  export let i = -1

  export let onChange = () => {}
</script>

<div>
  <label class="text-gray-500 mb-2">{item.title}</label>
  <input class="appearance-none border-2 border-gray-100 rounded-lg px-4 py-3 placeholder-gray-300 focus:outline-none focus:ring-2 focus:ring-green-600 focus:shadow-lg w-full" type="text"  bind:value={item.value} on:change={(e) => { onChange(item, i); }}/>
  <ErrorBox msg={item.errors || ''}/>
</div>