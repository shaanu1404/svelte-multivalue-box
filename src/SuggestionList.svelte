<script>
  import { createEventDispatcher } from "svelte";
  export let inputSubject = [];
  export let subjectList = [];
  export let threshold;

  const dispatch = createEventDispatcher();
</script>

<style>
  .suggestion {
    width: 90%;
    margin: 10px auto;
    list-style: none;
    padding: 0;
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    z-index: 1999;
    background: white;
  }
  .suggestion li {
    padding: 10px 8px;
    margin: 2px 0;
    border-right: 0.5px solid #ffa500;
    border-left: 0.5px solid #ffa500;
    text-transform: capitalize;
    color: rgba(20, 20, 20, 0.8);
    background: #f6fafd;
  }
  .suggestion li:hover {
    background: #ffa50087;
    cursor: pointer;
  }
</style>

{#if inputSubject.length >= threshold}
  <ul class="suggestion">
    {#each subjectList as subject, index}
      <li on:click={() => dispatch('add', subject)}>{subject}</li>
    {/each}
  </ul>
{/if}
