<script>
    import { createEventDispatcher } from "svelte";

	const disptch = createEventDispatcher();

	export let name;
	export let points;
	let showControls = false;

	const addPoint = () => points += 1
	const removePoint = () => points -= 1

	const toggleControl = () => (showControls = !showControls)

	const onDelete = () => {
		disptch("deleteplayer", name)
	}
</script>

<div class="card">
	<h1>
		{name}!
		<button class="btn btn-sm btn-success" on:click={toggleControl}>
			{#if showControls} - {:else} + {/if}
		</button>
		<button class="btn btn-sm btn-danger" on:click={onDelete}>x</button>
	</h1>
	<h3>Points : {points}</h3>
	{#if showControls}
		<button class="btn btn-dark" on:click={removePoint}>-1</button>
		<button class="btn" on:click={addPoint}>+1</button>

		<input type="number" bind:value={points}>
	{/if}
</div>

<style>
	h1 {
		color: #204f6e;
		text-transform: uppercase;
		font-weight: 100;
	}

	h3 {
		margin-bottom: 10px;
	}
</style>