<script>
    import Task from "./Task.svelte";

    let tasks = $state([]);
    let task = $state("");

    const addTasks = () => {

        if (task.trim() === "") return;

        tasks.push({
            id: Date.now(),
            content: task,
        });

        task = "";
    }

    function removeTask(id) {
        tasks = tasks.filter(task => task.id !== id);
    }
</script>


<article class="toDo">
    <header>
        <h1>To Do App</h1>
        <form onsubmit={(e) => e.preventDefault()}>
            <label for="task">Ecrire une tache : </label>
            <input bind:value={task} type="text" name="task" id="task">
            <button onclick={addTasks}>
                Ajouter la tache
            </button>
        </form>
    </header>

    <ul class="tasks">
        {#if tasks.length === 0}
            <p style="margin: 1em 0;">Aucune taches pour le moment...</p>
        {:else}
            {#each tasks as task (task.id)}
                <Task content={task.content} remove={() => removeTask(task.id)} />
            {/each}
        {/if}
    </ul>
</article>



<style>
    .toDo {
        width: 600px;
        background-color: #fff;
        padding: 1em 2em;
        margin: 2em auto;
        border-radius: 5px;
    }

    header {
        padding: 1em 0;
        border-bottom: 2px solid #333;
    }

    h1 {
        margin-bottom: 1em;
        font-size: 2em;
        font-weight: 600;
        text-align: center;
    }

    label {
        font-size: 1em;
        display: block;
        margin-bottom: 1em;
    }

    input {
        padding: 10px;
        width: 70%;
        font-size: 1em;
        font-weight: 400;
    }

    button {
        padding: 10px 20px;
        border: none;
        background-color: cornflowerblue;
        color: #fff;
        font-size: 1em;
        font-weight: 500;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }

    button:hover {
        background-color: rgb(0, 38, 255);
    }

    @media screen and (max-width: 40rem) {
        .toDo {
            max-width: 90%;
            height: 100vh;
        }

        input {
            display: block;
            width: 100%;
            margin-bottom: 1em;
        }
    }

</style>