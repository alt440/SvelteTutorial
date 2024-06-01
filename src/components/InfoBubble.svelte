<script>
    export let message;
    let likes = 0;

    const increaseLike = () => {
        likes++;
    };
</script>

<div class="containerBubble">
    <div class="title">{message}</div>
    <div class="innerDiv">
        <div><div contenteditable="true" bind:innerText={likes}></div></div>
        <button class="btnLike" on:click={increaseLike}>Like <img src="images/thumbsUpIcon5.png" width="20px"></button>
    </div>
</div>

<style>
    div.containerBubble{
        background-color: white;
        border-radius: 5px;
        border: 2px solid black;
        text-align: center;

        min-width: 300px;
        min-height: 80px;
        align-items: center;
        display: flex;
        flex-direction: column;
    }

    div.innerDiv {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    div.title {
        font-size: 20px;
        margin-bottom: 8px;
    }

    button.btnLike{
        margin-left: 10px;
        background-color: rgb(68, 99, 199);
        border-radius: 5px;
        color: white;
    }

    label {
        display: inline !important;
    }
</style>