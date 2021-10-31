<script>
    import { onMount, onDestroy, beforeUpdate, afterUpdate } from 'svelte';
    let description = ''
    $: characters = description.length;
    $: words = description.split(' ').length;

    $: if(description.length > 10) {
        console.log('-----')
        console.log(`Description: ${description}`);
        }

    function handleSubmit(event) {
        console.log('form submitted. thanks!');
        description = '';
    }

    onMount(() => {
        console.log('onMount');
    });

    onDestroy(() => {
        console.log('onDestroy');
    });

    beforeUpdate(() => {
        console.log('beforeUpdate');
    });

    afterUpdate(() => {
        console.log('afterUpdate');
    });

</script>

<style>
    div {
        margin-top: 0.3em;
        margin-bottom: 0.3em;
    }
    
    form {
        display: flex;
		flex-direction: column;
    }

    button {
        background-color: #8bd3dd;
        color: black;
        border-radius: 15px;
    }
</style>

<div>
    <p>{description}</p>
    <form on:submit|preventDefault="{handleSubmit}">
        <textarea bind:value={description} rows="5" cols="56"/>
        <button type="submit">Save</button>
    </form>
        <p>Characters count: {characters}</p>
        <p>Words count: {words}</p>
</div>