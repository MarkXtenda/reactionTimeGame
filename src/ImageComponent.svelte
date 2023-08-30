<script>
    import { createEventDispatcher } from "svelte";
    import { onMount, onDestroy } from "svelte";
    export let start;
    let chance = 0;
    const dispatch = createEventDispatcher();

    function updateChance() {
        chance = Math.floor(Math.random() * 2);
    }

    let interval;
    onMount(() => {
        interval = setInterval(updateChance, 500);
    });

    onDestroy(() => {
        clearInterval(interval);
    });

    function handleClick() {
        if (start) {
            dispatch("result", chance)
        }
    }
</script>

<button class="game-button" on:click={handleClick}>
{#if chance && start }
<img alt="go" src="https://media.giphy.com/media/SyP24XyDVsavNPECoR/giphy.gif"/>
{:else}
<img alt="stop" src="https://media.giphy.com/media/8TweEdaxxfuElKkRxz/giphy.gif"/>
{/if}
</button>
