<script>
  import Chip from "./Chip.svelte";
  import SuggestionList from "./SuggestionList.svelte";

  export let subjects;
  export let placeholder = "Search";
  export let threshold = 3;
  export let selectedSubjects = [];
  let inputSubject = "";

  $: subjectList = subjects.filter(sub => sub.includes(inputSubject));

  function addSubject(subject) {
    if (!selectedSubjects.includes(subject))
      selectedSubjects = [...selectedSubjects, subject];
    inputSubject = "";
  }

  function onEnter(e) {
    if (
      subjectList.length > 0 &&
      e.keyCode === 13 &&
      !selectedSubjects.includes(subjectList[0])
    ) {
      selectedSubjects = [...selectedSubjects, subjectList[0]];
      inputSubject = "";
    }
  }

  function removeSubject(subject) {
    selectedSubjects = selectedSubjects.filter(sub => sub !== subject);
  }
  function focus() {
    document.querySelector("#search-input").focus();
  }
</script>

<style>
  .container {
    position: relative;
  }
  .box {
    box-sizing: border-box;
    width: 90%;
    padding: 10px;
    margin: 10px auto;
    border: 1px solid orange;
  }
  .box input {
    margin: 0;
    border: none;
    outline: none;
  }
  .box input::placeholder {
    color: rgba(0, 0, 0, 0.6);
  }
</style>

<div class="container">
  <div class="box" on:click={focus}>
    {#each selectedSubjects as subject, index}
      <Chip {subject} on:click={() => removeSubject(subject)} />
    {/each}
    <input
      type="text"
      id="search-input"
      bind:value={inputSubject}
      on:keyup={onEnter}
      {placeholder} />
  </div>

  <SuggestionList
    {inputSubject}
    {subjectList}
    {threshold}
    on:add={event => addSubject(event.detail)} />
</div>
