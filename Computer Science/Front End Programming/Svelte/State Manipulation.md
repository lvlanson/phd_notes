Consider a [[Introduction#^f48ab9|stateful]] variable `{ts} let el = $state("string")`. If we want to manipulate it with an `{html} <input>` field, we need to use the **bind** directive.

```ts title="SomeFile.svelte" showLineNumbers {5}
<script lang="ts">
	let el = $state("Some String")
</script>

<input type="text" bind:value={name} />
```