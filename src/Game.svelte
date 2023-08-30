<script>
    import ImageComponent from "./ImageComponent.svelte";
    let counter = 20;
    let score = 0;
    let start = false;

    function handleResult(event) {
        if (event.detail) {
            score += 1;
        } else {
            counter -= 1;
        }
    }

    function handleStart() {
        start = !start;
        counter = 20;
        if (start) {
            score = 0;
        }
    }
</script>

<div>
    <div>
        <h3>Counter: {counter}</h3>
        <h3>Score: {score}</h3>
    </div>
    <ImageComponent on:result={handleResult} {start}/>
    <hr>
    {#if !start}
    <button on:click={handleStart}>Start</button>
    {#if score > 0}
        <h3>Your Score is {score}</h3>
    {/if}
    {:else}
    <button on:click={handleStart}>Stop</button>
    {/if}

</div>