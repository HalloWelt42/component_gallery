<script lang="ts">
    import {States} from "./States";
    import DataBaseIcon from "./DataBaseIcon.svelte";

    let current_state: string = States[States.empty];
    let states_string = Object.keys(States).filter(k => typeof States[k as any] === "number");
    console.log(States);
</script>

<DataBaseIcon bind:current_state/>

<div class="select">
    <select bind:value={current_state}>
        {#each states_string as key}
            <option value="{key}">{key}</option>
        {/each}
    </select>
</div>

