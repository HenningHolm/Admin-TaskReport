<script lang="ts">
  import { beforeUpdate } from 'svelte';
  import reportLogo from './assets/AiReport.png'
  import TodoList from './TodoList.svelte';
  const employers =["Thomas Teknikker", "Runar Rørlegger", "Even Elektrikker"]
  let showEmployers = false;
  let selectedEmployer = "";
</script>

<main>
    <div>
        <img src={reportLogo} class="logo svelte" alt="Svelte Logo"/>
        <h1>ASTA AI PRO PLUS</h1>
    </div>
    <div>
      {#if showEmployers || !selectedEmployer}
      {#each employers as employer}
      <br>
        <button style="background-color: gray; font-size:large" on:click={()=>selectedEmployer=employer}>{employer}</button>
      <br>
      {/each}

      {/if}
    </div>
    <div>
      <br>
    <button on:click={()=>showEmployers=!showEmployers}>{showEmployers ? "Close" :"Select Employer"}</button>
    </div>
    <div>
      {#if selectedEmployer && !showEmployers}
      <TodoList name={selectedEmployer}/>
      {/if}

    </div>
</main>

<style>
  .logo {
    height: 20em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;

  }
img{
  padding: 0 !important;
}


  .read-the-docs {
    color: #888;
  }
</style>
