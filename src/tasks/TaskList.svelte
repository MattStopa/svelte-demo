<script>
  export let  tasks = []
  export let addTask = () => { }
  export let completeTask = () => { }
  export let deleteTask = () => { }
  export let completedMode = false
</script>

<div class="bg-gray-100 p-3">
  <div class="flex w-full"> 
    {#if !completedMode} 
      <div class="bg-blue-100  w-full px-3 py-3 m-5 shadow-lg rounded">

        <input 
          on:keypress={(e) => { 
            if(e.key === "Enter") {
              addTask(e.target.value)
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
    <div class=" bg-white px-3 py-2 rounded mb-1  hover:bg-green-400 hover:text-white  cursor-pointer flex justify-between">
      {val}
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

