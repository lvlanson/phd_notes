## Binding

Consider a [[1 - Introduction#^f48ab9|stateful]] variable `{ts} let el = $state("string")`. If we want to manipulate it with an `{html} <input>` field, we need to use the **bind** directive.

```ts title="Component.svelte" showLineNumbers {5}
<script lang="ts">
	let el = $state("Some String")
</script>

<input type="text" bind:value={el} />
```

## Shorthands

Assume there is a component, where some type of event will trigger always the same function. Then the shorthand can be used

```ts title="CompactComponent.svelte" showLineNumbers {4,9}
<script lang="ts">
	let status: "ON" | "OFF" = "ON"

	function onclick(){
		status = status === "OPEN" ? "CLOSED" : "OPEN"; 
	}
</script>

<p>The status is {status}</p>
<button {onclick}>Toggle Status</button>
```

## Inline Function Calls

The same can be achieved using **inline anonymous functions**

```ts title="SomeComponent.svelte" showLineNumbers {6-8}
	<script lang="ts">
	let status: "ON" | "OFF" = "ON"
</script>

<p>The status is {status}</p>
<button {() => {
	status = status === "OPEN" ? "CLOSED" : "OPEN"; 
}}>Toggle Status</button> 
```

