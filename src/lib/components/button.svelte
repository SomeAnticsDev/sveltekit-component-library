<script>
	let variant = 'default';
	let disabled = false;

	export {variant, disabled};
</script>

<button on:click class:default={variant} {disabled}>
	<slot />
</button>

<style>
	:root {
		--background-color: var(--teal-9);
	}
	.default {
		background-color: var(--background-color);
		color: white;
	}
</style>