<script>
    export let currentEmoji;
    let current = 'emoji1';
</script>

<style>
    #currentEmoji {
        font-size: 3em;
    }
    
    div {
        display: inline;
        margin: 0.15em;
        justify-content: center;
        align-items: center;
    }

    button {
        color: black;
        border-radius: 15px;
    }

    .active {
        background-color: #8bd3dd;
        color: white;
    }
</style>

<div id="currentEmoji">{currentEmoji}</div>

<p>What's your current mood?</p>
<div>
    <button class:active={current === 'emoji1'} on:click={() => current = 'emoji1'}>😀 Happy</button>
    <button class:active={current === 'emoji2'} on:click={() => current = 'emoji2'}>🤣 ROFL</button>
    <button class:active={current === 'emoji3'} on:click={() => current = 'emoji3'}>😐 Neutral</button>
    <button class:active={current === 'emoji4'} on:click={() => current = 'emoji4'}>😔 Sad</button>
    <button class={current === 'emoji5' ? 'active' : ''} on:click={() => current = 'emoji5'}>😵 Dizzy</button>
</div>