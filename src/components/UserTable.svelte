<script>
	import { validate_each_argument } from "svelte/internal";

    let columns = ["Namn", "Kniv", "Poäng"]
    let data = [
        ["William", 0, 0]
    ]
    let data2 = new Map();
    let newUser;
    
    function addRow(newUser){
        data2 = data2.set(
            newUser,
            {
                knife: 0,
                score: 0,
            }
        )
        console.dir(data2)
    }

    function deleteRow(removeUser){

        if(data2.delete(removeUser) === true){
            data2 = data2;
        }
        console.dir(data2)
    }

</script>

<div>
    <table>
        <tr>
            {#each columns as column}
                <th>{column}</th>
            {/each}
        </tr>
    
        {#each [...data2] as [key, value]}
        <tr>
            <td contenteditable="false" bind:innerHTML={key} />
            <td contenteditable="false" bind:innerHTML={value.knife} />
            <td contenteditable="false" bind:innerHTML={value.score} />
        </tr>
        {/each}
        
    </table>

    <div>
        <label> Namn:
            <input bind:value={newUser}/>
        </label>
        <button on:click={addRow(newUser)}>Lägg till</button>
        <button on:click={deleteRow(newUser)}>Ta bort</button>
    </div>
    
</div>



