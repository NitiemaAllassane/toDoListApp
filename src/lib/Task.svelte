<script>
    let { content, remove } = $props();
</script>


<li>
    <p>{content}</p>
    <div class="btns">
        <button class="removeBtn" onclick={remove} >Delete</button>
    </div>
</li>

<style>
    li {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
        margin: 1em 0;
    }

    p {
        font-size: 1em;
        font-weight: 400;
        color: #333;
        overflow-wrap: break-word;
        overflow-x: auto;
    }

    button {
        padding: 10px 20px;
        background-color: red;
        color: #fff;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
</style>