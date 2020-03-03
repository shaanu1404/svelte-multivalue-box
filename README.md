# svelte-multivalue-box

`svelte-multivalue-box` gives you ability to select multiple values from a list of choices in a svelte project. The choice from the list of choices can bi searched by typing the input.

## Installing svelte-multivalue-box

```bash
npm install svelte-multivalue-box
```

## Using svelte-multivalue-box

```js
<script>
import Box from 'svelte-multivalue-box';

let choices = [// your choices //];
let result;
</script>

<Box subjects={choices} bind:selectedSubjects={result} />
```
