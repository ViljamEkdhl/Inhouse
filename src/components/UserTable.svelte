<script>
    import { players } from "../stores/stores";

    let columns = ["Namn", "Kniv", "Poäng"]
    let newUser;
    function addRow(newUser){
        
        players.set(
            newUser,
            {
                knife: 0,
                score: 0,
            }
        )
        players = players;
        console.dir(players)
    }

    function deleteRow(removeUser){

        if(players.delete(removeUser) === true){
            players = players;
        }
        console.dir(players)
    }

</script>

<div>
    <table>
        <tr>
            {#each columns as column}
                <th>{column}</th>
            {/each}
        </tr>
    
        {#each [...players] as [key, value]}
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



