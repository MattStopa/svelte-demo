<script>

  import ErrorBox from './forms/ErrorBox.svelte'

  let errorMsg = null;
  let value = ''
  let todos = ['Some stuff', 'hard work', 'sleeping in late', 'the greatest story of all time']
  $: console.log(todos)

  function addItem (e) {
    if(e.key !== 'Enter' || value === '') return

    if(value.length < 3 || todos.findIndex( (i) => i === e.target.value) > -1) {
      return errorMsg = "Too Short Or Duplicated Bro"
    }

    errorMsg = null
    todos.push(value); 
    todos = todos
    value = ''
  }

  function removeItem(val) {
    todos = todos.filter( (i) => i !== val)
  }

  </script>

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

<input placeholder="What needs to be done?" class="input" type="text" bind:value on:keypress={(e) => { addItem(e) }}>
<ErrorBox msg={errorMsg}></ErrorBox>

{#each todos as val, i}
  <div class="item flex">
    <div class="mt-5 ml-5">⚪️</div>
    <h3  on:click={(e) => { removeItem(val) }} >{val}</h3>
  </div>
{/each}

