CSS in a component is tightly bound to the component.

```html title="Component.svelte" showLineNumbers {8-10}
<script lang="ts">
	
</script>

<p>Some Text</p>

<style>
	p {
		color: blue;
	}
</style>
```

This CSS will only be applied inside `Component.svelte`. It is possible to apply CSS globally by adding the `{css} :global` directive

```html title="Component.svelte" showLineNumbers {8}
<script lang="ts">
	
</script>

<p>Some Text</p>

<style>
	:global(p) {
		color: blue;
	}
</style>
```