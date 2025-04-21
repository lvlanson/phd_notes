## If-Statements

One can embed `{ts} if` statements inside the HTML statements by using the `{ts} {#if}, {:else if}, {:else}, {/if}` directives.

```ts title="Component.svelte" showLineNumbers {20,23,25,27} wrap
<script lang="ts">
    let counter = $state(1);

    function increment(){
        counter++;
        if (counter > 10){
            counter = 0;
        }
    }
    function decrement(){
        counter--;
        if (counter < 0){
            counter = 10;
        }
    }
</script>
  
<h1>The current state is {counter}</h1>
<button onclick={increment}>Increment</button><button onclick={decrement}>Decrement</button>
{#if counter > 5}
    <p>The counter is greater than 5 with value {counter}</p>

{:else if counter == 3}
    <p>The counter now has exactly value 3</p>
{:else}
    <p>The counter is less than 5 and different from 3 with {counter}</p>
{/if}
```

#### Inline `if`  Statements

One can also write ternary statements inline
```html title="Component.svelte" showLineNumbers {5}
<script lang="ts">
	let state = true;
</script>

<p>{state ? "The statement is true" : "The statement is false!"}</p>

<style>
	p {
		color: blue;
	}
</style>
```
## Loops

