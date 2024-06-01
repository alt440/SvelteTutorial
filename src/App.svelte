<script>

	import Modal from './components/Modal.svelte';
	import InfoBubble from './components/InfoBubble.svelte';

	// internal var
	let showModal = false;
	let messageModal;
	let infoBubbleGroup = [];

	const surprise = () => {
		console.log('Surprise!');

		//if its currently showing, add component to store
		if(showModal && infoBubbleGroup.length < 10){
			let finalMessage = messageModal;
			if(messageModal === undefined || messageModal === ""){
				finalMessage = "It's some Svelte!";
			}
			infoBubbleGroup[infoBubbleGroup.length] = { id:infoBubbleGroup.length, message: finalMessage };
		}
		showModal = !showModal;
	};
</script>

<main>
	<Modal showModal={showModal} message={messageModal} on:click={surprise} />
	<div>
		<div class="inputsToSurprise">
			<input type="text" class="daBestInput" bind:value={messageModal} />
			<button class="surpriseButton" on:click={surprise}>Surprise</button>
		</div>
		<br>
		<ul>
			{#each infoBubbleGroup as item}
					<li><InfoBubble message={item.message} /></li>
			{/each}
		</ul>
	</div>
</main>

<style>
	main {
		background-color: gray;
		width: 100vw;
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		top: 0;
		left: 0;
		margin: 0;
		padding: 0;
		position: absolute;
	}

	button {
		height: fit-content;
		width: auto;
	}

	.inputsToSurprise {
		display: inline-block;
	}

	ul > li {
		margin-top: 5px;
	}

	ul {
		list-style-type: none;
	}

	input.daBestInput {
		appearance: none;
		border: none;
		outline: none;
		border-bottom: .2em solid white;
		background-color: transparent;
		padding: .4em;
		color: white;
		caret-color: white;
		margin-right: 15px;
	}

	button.surpriseButton {
		appearance: none;
		border: .2em solid white;
		background: transparent;
		padding: .85em 1.5em;
		color: white;
		transition: 0.2s;
	}

	button.surpriseButton:hover {
		border: .2em solid gray;
		background: white;
		color: gray;
	}
</style>