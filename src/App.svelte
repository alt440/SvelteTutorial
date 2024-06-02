<script>

	import Modal from './components/Modal.svelte';
	import InfoBubble from './components/InfoBubble.svelte';

	// internal var
	let showModal = false;
	let messageModal;
	let infoBubbleGroup = [];
	let titleIdeas;

	let infoBubbleIdPrefix = "infoBubbleExit";

	const surprise = () => {

		//if its currently showing, add component to store
		if(showModal && infoBubbleGroup.length < 10){
			let finalMessage = messageModal;
			if(messageModal === undefined || messageModal === ""){
				finalMessage = "It's some Svelte!";
			}
			infoBubbleGroup[infoBubbleGroup.length] = { id:infoBubbleGroup.length, message: finalMessage };
			messageModal = "";
		}
		showModal = !showModal;
	};

	function removeElement(index) {
		infoBubbleGroup = infoBubbleGroup.filter((_, i) => i !== index);
	}

	const removeInfo = (e) => {
		let idElement = e.target.id;
		let indexEl = idElement.replace(infoBubbleIdPrefix, "");
		removeElement(parseInt(indexEl));
		//adjust ids after element removed
		infoBubbleGroup.forEach(function(el) {
			if(el.id >= indexEl){
				el.id = el.id-1;
			}
		})
	}
</script>

<main>
	<Modal showModal={showModal} message={messageModal} on:click={surprise} />
	<div class="mainDiv1">
		<div class="titleDiv">
			<label>Title of this Debate: </label>
			<input type="text" bind:value={titleIdeas}>
		</div>
		<div>
			<div class="inputsToSurprise">
				<input type="text" class="daBestInput" bind:value={messageModal} />
				<button class="surpriseButton" on:click={surprise}>Add Suggestion</button>
			</div>
			<br>
			<div class="infoBubbles">
				{#each infoBubbleGroup as item}
						<InfoBubble id={item.id} idStrPrefix={infoBubbleIdPrefix} message={item.message} on:click={removeInfo}/>
				{/each}
			</div>
		</div>
	</div>
</main>

<style>
	:global(:root){
   		--first-color: #464A4E;
		--second-color: #EEEEEE;
		--third-color: #025179;
		--fourth-color: #2B2D42;
		--fifth-color: #990000;
		--def-font-size: 18px;
		--title-font-size: 24px;
	}

	main {
		background-color: var(--first-color);
		width: 100vw;
		height: 100vh;
		top: 0;
		left: 0;
		margin: 0;
		padding: 0;
		position: absolute;
		font-size: var(--def-font-size);
	}

	div.mainDiv1{
		top: 15vh;
		position: relative;
	}

	button {
		height: fit-content;
		width: auto;
	}

	.inputsToSurprise {
		position: relative;
		top: 10vh;
		width: 100%;
		text-align: center;
		display: inline-block;
	}

	.infoBubbles {
		position: relative;
		top: 10vh;
		max-width: 100vw;
		margin-left: 10vw;
		margin-right: 10vw;
		margin-top: 5vh;

		display:flex;
		flex-direction: row;
		flex-wrap: wrap;
		gap: 5vw;
	}

	input {
		appearance: none;
		border: none;
		outline: none;
		border-bottom: .2em solid var(--second-color);
		background-color: transparent;
		padding: .4em;
		color: var(--second-color);
		caret-color: var(--second-color);
		margin-right: 15px;
	}

	button.surpriseButton {
		appearance: none;
		border: .2em solid var(--second-color);
		background: transparent;
		padding: .85em 1.5em;
		color: var(--second-color);
		transition: 0.2s;
		border-radius: 5px;
	}

	button.surpriseButton:hover {
		border: .2em solid var(--first-color);
		background: var(--second-color);
		color: var(--first-color);
	}

	div.titleDiv {
		display:flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		gap: 10px;
		color: var(--second-color);
		width: 100%;
		font-size: var(--title-font-size);
		top:2vh;
		position:relative;
	}
</style>