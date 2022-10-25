<script>
    import {getUser} from '../secret/FetchUser.js';

    let newUser;
    let steamId;

    async function addUser(){

        getUser(steamId);

    }

</script>

<div>
    <label> SteamId
        <input bind:value={steamId}>
    </label>
    <button on:click={() => addUser(steamId)}>Add user</button>
</div>