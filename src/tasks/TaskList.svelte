<script>
  export let selectedSize = 1;
  export let tasks = []
  export let addTask = () => { }
  export let completeTask = () => { }
  export let deleteTask = () => { }
  export let completedMode = false

  function getEmojii(val) {
    switch(val) {
      case 1:
        return '👶';
      case 2:
        return '🧆';
      case 3:
        return '👷';
    }
  }

  function getSideClass(val) {
    switch(val) {
      case 1:
        return 'border-l-4 border-green-400';
      case 2:
        return 'border-l-4 border-yellow-500';
      case 3:
        return 'border-l-4 border-red-400';
    }
  }

</script>

<div class="bg-gray-100 p-3">
  <div class="flex w-full"> 
    {#if !completedMode} 
      <div class="bg-blue-100  w-full px-3 py-3 m-5 shadow-lg rounded">
        <div class="flex mb-2">
          <div class="hover:bg-blue-200 cursor-pointer p-2 bg-white rounded mr-1 font-semibold {selectedSize == 1 ? 'bg-blue-300' : ''}"
            on:click={() => selectedSize = 1}>
            Small 👶
          </div>
          <div class="hover:bg-blue-200 cursor-pointer  p-2 bg-white rounded mr-1  font-semibold {selectedSize == 2 ? 'bg-blue-300 text-white' : ''}"
            on:click={() => selectedSize = 2}>
            Medium 🧆
          </div>
          <div class="hover:bg-blue-200 cursor-pointer p-2 bg-white rounded mr-1  font-semibold {selectedSize == 3 ? 'bg-blue-300 text-white' : ''}"
            on:click={() => selectedSize = 3}>
            Large 👷
          </div>
        </div>
        <input 
          on:keypress={(e) => { 
            if(e.key === "Enter") {
              addTask(e.target.value, selectedSize)
              e.target.value = ''
            }
          }}
          class="shadow appearance-none border w-full border-gray-400 rounded w-full py-2 px-3 text-gray-700  leading-tight focus:outline-none focus:shadow-outline"
        />
      </div>
    {:else}
      <h2 class="text-2xl font-bold mb-10 mt-6 text-center text-white bg-green-600 w-full p-2 rounded">
        🏆  Completed List  🏆
      </h2> 
    {/if}
  </div>
  {#each tasks as val, i}
    <div class="{getSideClass(val.value)} bg-white px-3 py-2 rounded mb-1  hover:bg-green-400 hover:text-white  cursor-pointer flex justify-between">
      <div class="flex">
        <div class="mr-2">{getEmojii(val.value)}</div>
        <div>{val.title}</div>
      </div>
      {#if !completedMode}
        <div class="flex">
          <div 
            class="bg-gray-200 text-white rounded p-2 py-0 mr-2"
            on:click={(e) => completeTask(i) }>✔️</div>
          <div class="bg-gray-200 text-white rounded p-2 py-0 mr-2"
            on:click={(e) => deleteTask(i) }
          >❌</div>
        </div>
      {/if}
    </div>
  {/each}
</div>

