<script>
    import items from '../assets/warmups.json';
    const warmups = items.warmups;
    let generated;

    function genWarmup() {
        generated = warmups[Math.floor(Math.random()*warmups.length)]
    }

    const testConfirm = async (_) => {
    let confirmed = await confirm("GENERATE ANOTHER WARMUP?");
    if (confirmed) genWarmup();
  };
</script>

<style>
    .description {
        text-align: center;
        border: dotted;
        max-width: 450px;
        margin-left: auto;
        margin-right: auto;
    }

    .button {
        text-align: center;
        padding: 10px;
    }

    .warmup {
        text-align: center;
        margin-right: auto;
        margin-left: auto;
    }

    table {
        text-align: center;
        margin-right: auto;
        margin-left: auto;
        border: solid;
        padding: 5px;
    }
</style>

<div class="description">
    <p>
        Use this page to get a warmup generated for you so that you can get to lifting weights sooner.
    </p>
</div>

<div class="button">
    <button on:click={genWarmup}>Generate a Warmup</button>
    <br />
</div>

<div class="warmup">
    {#if generated}
    <table>
        <th>Your warmup for today is:</th>

            {#each generated as gen}
                <tr>{gen}</tr>
            {/each}
            <p>
                <button on:click={testConfirm}>
                  Get another warmup
                </button>
            </p>
    </table>
    {/if}
</div>