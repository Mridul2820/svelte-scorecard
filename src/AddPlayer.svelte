<script>
    import { createEventDispatcher } from "svelte";

    const disptch = createEventDispatcher();

    let player = {
        name: "",
        points: 0
    }

    const onSubmit = (e) => {
        e.preventDefault();
        disptch("addplayer", player)
        player = {
            name: "",
            points: 0
        }
    }
</script>

<form on:submit={onSubmit} class="grid-3">
    <input type="text" placeholder="Player Name" bind:value={player.name}>
    <input type="number" placeholder="Player Number" bind:value={player.points}>
    <input class="btn btn-primary" type="submit" value="Add Player">
</form>