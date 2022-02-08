<script>
	import {crossfade, fade} from 'svelte/transition';
	import {flip} from 'svelte/animate';
	import Card from './card.svelte';
	import Checkbox from './checkbox.svelte';

	const [send, receive] = crossfade({fallback: fade});

	let todos = [
		{isDone: false, text: 'Do the stream', id: 1},
		{isDone: false, text: 'Greet the chat', id: 2},
		{isDone: false, text: 'Continue to do the stream', id: 3}
	];
</script>

<Card>
	<h2 slot="title">Todo</h2>
	<ul slot="content">
		{#each todos.filter(todo => !todo.isDone) as todo (todo.id)}
			<li
				animate:flip
				in:receive={{key: todo.id}}
				out:send={{key: todo.id}}
			>
				<Checkbox bind:checked={todo.isDone} id={todo.id}>
					{todo.text}
				</Checkbox>
			</li>
		{/each}
	</ul>
</Card>

<Card>
	<h2 slot="title">Done</h2>
	<ul slot="content">
		{#each todos.filter(todo => todo.isDone) as done (done.id)}
			<li
				animate:flip
				in:receive={{key: done.id}}
				out:send={{key: done.id}}
			>
				<Checkbox bind:checked={done.isDone} id={done.id}>
					{done.text}
				</Checkbox>
			</li>
		{/each}
	</ul>
</Card>