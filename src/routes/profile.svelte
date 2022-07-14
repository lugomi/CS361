<script>
    import lifts from '../assets/lifts.json';
    import { onMount } from 'svelte';

    let records = lifts;
    let lift;
    let weight;

    function undo() {
        if (records.length > 0) {
            records.pop()
            records = records
            return
        }
    }

    function addToArray(lift, weight) {
        // validate lift and weight
        if (!isNaN(weight)) {
            weight = parseInt(weight)
        } else if (isNaN(weight)) {
            window.alert('WEIGHT NEEDS TO BE A NUMBER\nTRY AGAIN')
            return
        }

        // check to see if entry exists already for a lift
        for (let oldLift of records) {
            if (oldLift.name === lift) {
                if (oldLift.max >= weight) {
                    window.alert(`${lift} ALREADY EXISTS WITH A RECORD OF ${oldLift.max}`)
                    return
                } else {
                    oldLift.max = weight
                    records = records
                    return
                }
            }
        }


        // check to make sure lift not already in list
        records.push({"name": lift, "max": weight});
        records = records;
        // window.alert(`${lifts.length}`)
    }



</script>

<style>
    .lifts {
        text-align: center;
        margin-left: auto;
        margin-right: auto;
    }

    .get-input {
        text-align: center;
        border: solid;
        padding: 5px;
        margin-left: auto;
        margin-right: auto;

    }

    label {
        margin-left: auto;
        margin-right: auto;
    }

    table, th, td {
        border: solid;
    }

    .description {
        text-align: center;
        border: dotted;
        max-width: 450px;
        margin-left: auto;
        margin-right: auto;
    }


</style>

<div class="description">
    <p><strong>
        Here you can calculate your one rep max. all you need to do is provide the number of reps you did
        (1 or more) and the weight you lifted to get an idea what your one rep max should be.
    </strong></p> 
</div>
<br />
<div class="get-input">
    <label>Lift:</label>
    <input bind:value={lift}/>
    <br />
    <br />
    <label>Weight:</label>
    <input bind:value={weight}/>
    <br />
    <br />
    <button on:click={() => addToArray(lift, weight)}>
        Add new PR!
    </button>
    <button on:click={undo}>
        Undo
    </button>
</div>

<br />
<div class="lifts">
    <table class="records">
        <tr>
            <th><b>Lift</b></th>
            <th><b>Weight</b></th>
        </tr>
        {#each records as item}
            <tr>
                <td>{item.name}</td>
                <td>{item.max}</td>
            </tr>
        {/each}
    </table>
</div>