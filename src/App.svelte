<script>
	import Sidebar from './SideBar.svelte'
	import MainForm from './pages/MainForm.svelte'
	import Todos from './pages/Todos.svelte'
	import Login from './pages/LoginScreen.svelte'
	import { onMount } from 'svelte';

  let view = window.location.hash || '#form'


	window.addEventListener("hashchange", (a) => { 
		view = window.location.hash
		console.log(`---${view}---`)
		if(view === "" || view == "#") { view = '#form' }
	})

	function loaded() { 
		jscolor.install()
	}

	onMount(() => {
		
	});
</script>

<svelte:head>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jscolor/2.4.8/jscolor.min.js" on:load={loaded} ></script>
</svelte:head>


<main class="container m-auto ">
	<div class="flex" >
		{#if view !== '#login'}
			<div class="mr-4" >
				<Sidebar bind:view={view}></Sidebar>
			</div>
		{/if}
		<div class="w-3/4">
			{#if view === '#form'}
				<MainForm></MainForm>
	    {/if}
			{#if view === '#todos'}
				<Todos></Todos>
	    {/if}
			{#if view === '#login'}
				<Login></Login>
			{/if}
	 </div>
</div>


</main>

<style>
 
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
</style>