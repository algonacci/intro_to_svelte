<script>
	import { fade } from 'svelte/transition';

	import EmojiDisplay from "./EmojiDisplay.svelte";
	import EmojiDescription from "./EmojiDescription.svelte";

	let isLoaded = false;

	let currentEmoji = '😁';
	const emojis = ['🤣','🤑','👺','👅','👽','👹','😸','💀','😻','☠️','😽','💩','🤡','😾',];

	function randomizeEmoji() {
		return emojis[Math.floor(Math.random() * emojis.length)];
	}

	function handleRandomButton() {
		currentEmoji = randomizeEmoji();
	}

	setTimeout(() => {
		isLoaded = true;
	}, 2500);
</script>


<style>
	button {
		background-color: #8bd3dd;
		padding: 0.5em;
		border-radius: 0.25em;
		border: 2px solid #000;
		box-shadow: 0.4rem 0.4rem 0 #222;
	}

	button:hover {
		box-shadow: 0.25rem 0.25rem 0 #222;
		transition: all 0.4s ease 0s;
		background-color: #8bd;
	}

	#content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	
	h1 {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	div {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	body {
		height: max-content;
	}
</style>


<header>
	<div>
		<h1>Emoji Randomizer</h1>
	</div>
	<div>
		{#if isLoaded === true}
		{#each emojis as emoji}
		<p id="listEmoji">{emoji}</p>
		{/each}
		{:else}
		<hr>
		{/if}
	</div>
</header>

<body>
	<div id="content">
		{#if isLoaded === true}
		<EmojiDisplay {currentEmoji} />
		<EmojiDescription />
		<button on:click={handleRandomButton}>🔁 Randomize</button>
		{:else}
		<img src="images/Loader.gif" alt="Loading">
		<h2>Loading....</h2>
		{/if}
	</div>
</body>