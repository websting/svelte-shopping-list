<script>
    import {fade} from 'svelte/transition';

    let groceries = []; // start with an empty array
    let newItem = ''; 

    // call to local storage if it exits
    if(localStorage.getItem('groceries')){
        groceries = JSON.parse(localStorage.getItem('groceries'))
    }
    $: localStorage.setItem('groceries', JSON.stringify(groceries)) //reactive svelte changes

    // newItems entered randomly get added and list starts
    const addItem = () => {
        groceries = [...groceries, {id: Math.random(), newItem, done: false}];

        newItem = ''; // after user hits enter input resets itself
    }

    // when done items can be checked marked
    const toggle = item => {
        item.done= !item.done;
        groceries = groceries;
    };

    // deletes items checked
    const clearCompleted = () => {
            groceries = groceries.filter(item => !item.done); // filter updates list to items !COMPLETED
        }
</script>

<main>
    <form on:submit|preventDefault={addItem}><!--prevents browser from resetting itself-->
        <!--two way binding looks for newItem entered-->
        <input type="text" id="name" placeholder="Add items" bind:value={newItem} />
        <button type="submit" class="button" on:keyup={addItem}>Add</button>
    </form>

    <ul><!--loop through list-->
        {#each groceries as item}
            <li transition:fade class:done={item.done}>
                <input type="checkbox" class="checkbox" bind:checked={item.done}/>
                <span>{item.newItem}</span> <!--list gets displayed here-->
            </li>
        {/each}
    </ul>
    <button class="clear-button" on:click={clearCompleted}>Clear completed</button>
</main>

<style>
    main {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}
    li {
        list-style: none;
        padding: 2;
    }

    ul {
        padding-left: 0;
        margin-top: 15px;
    }

    .checkbox {
        margin-right: 5px;
    }

    .done span {
        color:rgb(241, 7, 7);
        opacity: 0.4;
        text-decoration: line-through;

    }

    #name {
        color: gray;
        margin-top: 25px;
        font-family: inherit;
        outline: 0;
        border: 0;
        width: 70%;
        font-size: 1.5rem;
    }

    #name:hover {
        color: blueviolet;
        box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
    }
    .clear-button{
        background-color: lightblue;
        border-radius: 4px;
        transition-duration: 0.4s;
        padding: 6px 12px;
    }
    .clear-button:hover {
        background-color: #4CAF50; /* Green */
        color: white;
        box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
}

.button{
        margin-left: 5px;
        padding: 10px;
        background-color: lightblue;
        border-radius: 4px;
        transition-duration: 0.4s;
        padding: 6px 12px;

    }

.button:hover {
    background-color: #4CAF50; /* Green */
        color: white;
        box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
}

@media(max-width:480px) {
    #name {
        margin-left: 40px;
        width: 40%;
        font-size:medium;
    }

    .clear-button {
        padding: 3px 6px;
    }
}
</style>