<script lang="ts">
    let tasks = new Array<string>();
    let newTask = '';
    export let name :string;

    function addTask() {
        if (newTask.trim() !== '') {
            tasks = [...tasks, newTask];
            newTask = '';
        }
    }

    function deleteTask(task: string) {
        tasks = tasks.filter(t => t !== task);
    }
</script>

<style>
    .task-list {
        list-style: none;
        padding: 0;
    }

    .task-item {
        margin: 10px 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    button {
        margin-left: 10px;
    }
</style>

<div>
    <h1>{name}s Controll List</h1>
    <input style="font-size: large;" type="text" bind:value={newTask} placeholder="Legg til ny oppgave" />
    <button on:click={addTask}>Legg til</button>

    <ul class="task-list">
        {#each tasks as task}
            <li class="task-item">
                {task}
                <button on:click={() => deleteTask(task)}>Slett</button>
            </li>
        {/each}
    </ul>
</div>