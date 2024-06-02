<script>
    export let message;
    let likes = 0;
    let dislikes = 0;

    const increaseLike = () => {
        likes++;
    };

    const increaseDislike = () => {
        dislikes++;
    }
</script>

<div class="containerBubble">
    <div class="title">{message}</div>
    <div class="innerDiv">
        <button class="btnLike" on:click={increaseLike}><img src="images/thumbsUpIcon6.png" alt="Like button" width="20px"> &nbsp; <label contenteditable="true" bind:innerText={likes}></label></button>
        <button class="btnDislike" on:click={increaseDislike}><img src="images/thumbsUpIcon6.png" class="dislike" alt="Dislike button" width="20px"> &nbsp; <label contenteditable="true" bind:innerText={dislikes}></label></button>
    </div>
</div>

<style>
    div.containerBubble{
        background-color: var(--fourth-color);
        border-radius: 5px;
        border: 2px solid var(--second-color);
        text-align: center;

        min-width: 300px;
        max-width: 20vw;
        min-height: 80px;
        align-items: center;
        display: flex;
        flex-direction: column;
        color: var(--second-color);
        word-wrap: break-word;
    }

    div.innerDiv {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    div.title {
        font-size: var(--title-font-size);
        margin-bottom: 8px;
    }

    button{
        display:flex;
        gap: 1px;
        flex-direction: row;
    }

    button.btnLike{
        margin-left: 10px;
        margin-right: 10px;
        background-color: var(--third-color);
        border-radius: 5px;
        color: var(--second-color);
    }

    button.btnLike:hover{
        cursor: pointer;
        opacity: 0.9;
    }

    button.btnDislike{
        background-color: var(--fifth-color);
        border-radius: 5px;
        color: var(--second-color);
    }

    button.btnDislike:hover{
        cursor: pointer;
        opacity: 0.9;
    }

    img.dislike {
        transform: scaleY(-1);
    }

    label {
        display: inline !important;
        pointer-events: none;
    }
</style>