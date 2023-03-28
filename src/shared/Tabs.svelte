<script>
    import { createEventDispatcher } from "svelte";
    
    export let tabs = [];
    export let activeItem = '';
    
    const dispatch = createEventDispatcher();

</script>

<div class="tabs">
    <ul>
        {#each tabs as tab}
            <li on:click={() => {dispatch('changeTab', tab)}} class:active={tab === activeItem}>
                <div>{tab}</div>
            </li>
        {/each}
    </ul>
</div>

<style>
    .tabs {
        margin-bottom: 14px;
    }
    ul {
        display: flex;
        justify-content: center;
        padding: 0;
        list-style-type: none;
    }
    li {
        margin: 0 16px;
        font-size: 18px;
        color: #555;
        cursor: pointer;
    }
    .active {
        color: #d91b42;
        border-bottom: 2px solid #d91b42;
        padding-bottom: 8px;
        }
</style>