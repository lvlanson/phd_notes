The file tree to consider is
```ts title="Reduced File Tree"
└──myapp
	└── src
        ├── lib
        └── routes
```
There are more files and folders, but we will focus on those

## Components
Components are reusable structures stored in `routes`. The structure of a component is as follows. 

```ts title=Component.svelte showLineNumbers
<script lang="ts">
	// imports and logic goes here
</script>

<h1>HTML goes here</h1>

<style>
	// CSS goes here
</style>
```

This component can be used in some other file like

```ts title=File.svelte {2,5} showLineNumbers
<script lang="ts">
	import Component from './Component.svelte'
</script>

<Component />
```

#### Passing Arguments Through Components Using `props`

If one wants to pass arguments **into a component**, `prop` can be used. First, we pass data into the `Component`
```ts title=File.svelte {5} showLineNumbers
<script lang="ts">
	import Component from './Component.svelte'
</script>

<Component name="passing data"/>
```

```ts title=Component.svelte showLineNumbers {2,5}
<script lang="ts">
	let { data } = $props();
</script>

<h1>Here we get { data }</h1>

<style>
</style>
```

To add typescript types, we do

```ts title=Component.svelte {2} showLineNumbers
<script lang="ts">
	let { data }: {data : string;} = $props();
</script>

<h1>Here we get { data }</h1>

<style>
</style>
```

And go multiline if we receive multiple objects from prop.

#### Optional and Default values for `props` with typescript

When using the last code example, the `{ts} Component` requires the `{ts} data` field to be passed through. One can also declare a component to be optional by adding the `{ts} ?` directive.

```ts title=Component.svelte {4,7} showLineNumbers
<script lang="ts">
	let { 
			data,
			otherData 
		}:{
			data : string;
			otherData? : string;
		} = $props();
</script>

<h1>Here we get { data }</h1>

<style>
</style>
```

Optional data entries can be added by initializing it in the definition statement

```ts title=Component.svelte {4} showLineNumbers
<script lang="ts">
	let { 
			data,
			otherData = "initialized"
		}:{
			data : string;
			otherData? : string;
		} = $props();
</script>

<h1>Here we get { data }</h1>

<style>
</style>
```