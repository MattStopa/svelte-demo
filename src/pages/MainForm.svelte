<script>
  import Form from '../forms/Form.svelte'
  import Card from '../Card.svelte'
  import { fade, fly } from 'svelte/transition';

  let view = ''
  let color = '#e66465'
  let formItems = [
    { 'type': 'input', title: 'First Name', code: 'fn', value: 'tony' },
    { 'type': 'input', title: 'Last Name', code: 'ln', value: 'balloney' },
    { 'type': 'input', title: 'Address', code: 'addy', value: '323 Bad Stree aRISING' },
    { 'type': 'select', title: 'Fav Fruit', code: 'addy', value: 'Banaana', options: [{title: "Banaana"}, {title: "Apples"}] },
    { 'type': 'tag', title: 'Tags', code: 'addy', value: ['dog', 't-rex', 'brontosaurus'] }
  ]
</script>


<div in:fade >
  <Card title={"Form"}>
    
    <div class="flex">
      <input type="color" id="head" name="head"  bind:value={color} class="h-12 mr-2"/>
      <input type='text' bind:value={color} class="mr-2 appearance-none border-2 border-gray-100 rounded-lg px-4 py-3 placeholder-gray-300 focus:outline-none focus:ring-2 focus:ring-green-600 focus:shadow-lg"/>
    </div>
    
		<div class=" w-1/2">
      <Form bind:formItems={formItems} onChange={ (e,i) => { 
        e.errors= e.value.length < 3 ? "It's too short bro" : '' 
        formItems[i] = e
      }}></Form>
    </div>
  </Card>
</div>
