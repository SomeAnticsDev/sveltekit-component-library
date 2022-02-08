<script>
	import Button from '$lib/components/button.svelte';
	import Todos from '$lib/components/todos.svelte';
</script>

<h1>Component Library</h1>
<Button --background-color="#4C1074">
	Click me!
</Button>
<Todos />

<style>
	h1 {
		font-size: var(--font-size-fluid-3);
	}
</style>