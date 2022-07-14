<script>
	// all that's left is to make it possible to regenerate a new 1RM
	let reps;
	let weight;
	let oneRepMax;

	function get1RM() {
		if (!reps && !weight) {
			window.alert("MISSING WEIGHT AND/OR REPS\nTRY AGAIN!")
		} else if (!isNaN(reps) && !isNaN(weight)) {
			if (reps < 1 || weight < 1) {
				window.alert("ONLY POSITIVE NUMBERS MAY BE ENTERED\nTRY AGAIN!")
			} else {
				oneRepMax = parseInt(weight) * (1+ parseInt(reps)/30)
			}
		} else {
			window.alert("PLEASE ENTER VALID INTS\nTRY AGAIN!")
		}
	}
</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.user-input {
		border: solid;
		padding: 10px;
		align-self: center;
		margin-left: auto;
		margin-right: auto;
		max-width: 240px;
	}

    .description {
        border: dotted;
        text-align: center;
        max-width: 400px;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
    <h1>1RM Calculator</h1>

    <div class="description">
        <p><strong>
            Here you can calculate your one rep max. all you need to do is provide the number of reps you did
            (1 or more) and the weight you lifted to get an idea what your one rep max should be.
        </strong></p> 
    </div>
    <br />
	<div class="user-input">
		Reps: <input bind:value={reps} placeholder="enter your reps">
		<br>
        <br>
		Weight: <input bind:value={weight} placeholder="enter weight">
        <br>
        <br>
		<button on:click={get1RM}>Get 1RM!</button>
	</div>
    <br>
	<div class="display-max">
		{#if oneRepMax}
		<p>Your one rep max: <b><u>{oneRepMax}</u></b> lbs</p>
		{/if}
	</div>


</main>