<script>

  import ErrorBox from './forms/ErrorBox.svelte'

  let errorMsg = null;
  let value = ''
  let todos = [
    {title: 'Some stuff', color: "#ff9393"},
    {title: 'Hard Work', color: "#33333a"},
    {title: 'Sleeping In Late', color: "#aaf3f3"},
    {title: 'Dont Count on it pal', color: "#3f3a33"}
  ]
  let color = "000"
  $: console.log(todos)

  function addItem (e) {
    if(e.key !== 'Enter' || value === '') return

    if(value.length < 3 || todos.findIndex( (i) => i === e.target.value) > -1) {
      return errorMsg = "Too Short Or Duplicated Bro"
    }

    errorMsg = null
    todos.push({title: value, color: color}); 
    todos = todos
    value = ''
    color = "#" + Math.floor(Math.random()*16777215).toString(16)
  }

  function removeItem(val) {
    todos = todos.filter( (i) => i.title !== val.title)
  }

  </script>

  <div class="flex">
    
    <input type="color" id="head" name="head"  bind:value={color} class="h-12 mr-2"/>
    <input placeholder="What needs to be done?" class="input" type="text" bind:value on:keypress={(e) => { addItem(e) }}>
  </div>
  <ErrorBox msg={errorMsg}></ErrorBox>

{#each todos as val, i}
  <div class="item flex" style={`border-left: 5px solid ${val.color}`}  on:click={(e) => { removeItem(val) }}>
    <div class="mt-5 ml-5">⚪️</div>
    <h3 >{val.title}</h3>
  </div>
{/each}


<style>
  h3 {
    background: #fff;
    padding: 20px;
    cursor: pointer;
  }

  h3:hover {
    background-color: #b8ca98;
  }

  .input {

    position: relative;
    margin: 0;
    width: 100%;
    font-size: 24px;
    font-family: inherit;
    font-weight: inherit;
    line-height: 1.4em;
    border: 0;
    color: inherit;
    padding: 6px;
    border: 1px solid #999;
    box-shadow: inset 0 -1px 5px 0 rgb(0 0 0 / 20%);
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    padding: 16px 16px 16px 60px;
    border: none;
    background: rgba(0, 0, 0, 0.003);
    box-shadow: inset 0 -2px 1px rgb(0 0 0 / 3%);
    background: #fff;
    box-shadow: inset 0 -2px 1px rgb(0 0 0 / 3%);
  }

  .item {
    border-bottom: 1px solid #ededed;
    font-size: 24px;
    background-color: #fff;
  }

</style>