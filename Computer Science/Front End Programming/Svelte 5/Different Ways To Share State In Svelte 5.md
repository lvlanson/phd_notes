---
title: "Different Ways To Share State In Svelte 5"
source: "https://joyofcode.xyz/how-to-share-state-in-svelte-5#using-classes-for-reactive-state"
author:
  - "[[Joy of Code]]"
published:
created: 2025-03-14
description: "Learn different ways you can export and share reactive state in Svelte 5."
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=qI31XOrBuY0)

- [Universal Reactivity](https://joyofcode.xyz/#universal-reactivity)
- [Global State](https://joyofcode.xyz/#global-state)
- [Using Functions To Read And Write To Reactive Values](https://joyofcode.xyz/#using-functions-to-read-and-write-to-reactive-values)
- [Using Property Accessors To Read And Write To Reactive Values](https://joyofcode.xyz/#using-property-accessors-to-read-and-write-to-reactive-values)
- [Destructuring Reactive Values](https://joyofcode.xyz/#destructuring-reactive-values)
- [Using Classes For Reactive State](https://joyofcode.xyz/#using-classes-for-reactive-state)
- [Doing Side Effects](https://joyofcode.xyz/#doing-side-effects)
- [Shared State On The Server](https://joyofcode.xyz/#shared-state-on-the-server)

## Universal Reactivity

[Svelte 5](https://svelte.dev/blog/svelte-5-is-alive) introduced a new universal system of reactivity named runes which means that you can use the same reactivity system inside and outside Svelte components as long as the file name includes the `.svelte` extension.

In this post I’m going to go over the different ways you can export and share reactive state in Svelte 5 using functions, classes and property accessors.

## Global State

This is a simple counter example that declares a reactive value `count` using the `$state` rune and increments it using a button:


```html title="+page.svelte" showLineNumbers
<script lang="ts">
  let count = $state(0)
</script>

<button onclick={() => count++}>
  {count}
</button>
```

Try exporting and importing the `count` value from the component:

```ts title="counter.svelte.ts" showLineNumbers
export let count = $state(0)
```

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { count } from './counter.svelte'
</script>

<button onclick={() => count++}>
  {count}
</button>
```

You might have expected this to work, but instead you get an error that says: **“Cannot assign to import.”**

This is because **Svelte doesn’t change how JavaScript works** and [imported values can only be modified by the exporter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#imported_values_can_only_be_modified_by_the_exporter).

In older versions of Svelte you would use a `writable` store to export the value which works because stores are objects:

```ts title="counter.ts" showLineNumbers
// writable store
export const count = writable(0)
```

In Svelte 5, you can pass an object to `$state` and Svelte is going to use a Proxy object to make the properties reactive:



```ts title="counter.svelte.ts" showLineNumbers
// reactive object using a Proxy
export const count = $state({ value: 0 })
```

You can’t reassign imports, but you can update objects so updating `count.value` works:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { count } from './counter.svelte'
</script>

<button onclick={() => count.value++}>
  {count.value}
</button>
```

This is very useful if you have a config that you want to expose to your entire app:



```ts title="config.svelte.ts" showLineNumbers
export const config = $state({
  theme: 'dark',
  textSize: '16px',
  textLength: '80ch',
  // ...
})
```

## Using Functions To Read And Write To Reactive Values

You can use regular functions to read and write to a reactive value:



```ts title="counter.svelte.ts" showLineNumbers
let count = $state(0)

export function getCount() {
  return count
}

export function setCount(value: number) {
  count = value
}
```

This comes at the cost of developer experience since you have to write more verbose code:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { getCount, setCount } from './counter.svelte'
</script>

<button onclick={() => setCount(getCount() + 1)}>
  {getCount()}
</button>
```

## Using Property Accessors To Read And Write To Reactive Values

You can define a getter and setter and use [property accessors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Property_accessors) for a nicer developer experience:

```ts title="counter.svelte.ts" showLineNumbers
let count = $state(0)

export const counter = {
  get count() { return count },
  set count(value) { count = value },
  increment() { count++ }
}
```

You can use functions instead of property accessors if you want:

```ts title="counter.svelte.ts" showLineNumbers
let count = $state(0)

export const counter = {
  count() { return count },
  setCount(value) { count = value },
  increment() { count++ }
}
```

Using property accessors, you can read and write to count using `counter.count` or `increment`:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { counter } from './counter.svelte'
</script>

<button onclick={() => counter.count++}>
  {counter.count}
</button>
```

Of course, you would not export an object like this directly from the module but from a function instead:

```ts title="counter.svelte.ts" showLineNumbers
export function createCounter() {
  let count = $state(0)
  // you can also derive values
  let double = $derived(count * 2)

  return {
    get count() { return count },
    set count(value) { count = value },
    increment() { count++ }
  }
}
```

Then you would initialize the counter inside the component:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { createCounter } from './counter.svelte'

  const counter = createCounter()
</script>

<button onclick={counter.increment}>
  {counter.count}
</button>
```

## Destructuring Reactive Values

You might want to destructure `count` and `increment` from `counter` but as you’re going to see it won’t work as expected when using property accessors:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { counter } from './counter.svelte'

  const { count, increment } = createCounter()
</script>

<button onclick={() => count++}>
  {count}
</button>
```

This is because when you destructure `count` you’re going to get the value at the time it was created instead of the reactive value.

You can get around this by using proxied state to “wrap” the value or by returning a function:

```ts title="counter.svelte.ts" showLineNumbers
export function createCounterProxy() {
  let count = $state({ value: 0 })
  return { count }
}

export function createCounterFunction() {
  let count = $state(0)

  return {
    count() { return count },
    setCount(value) { count = value },
  }
}
```

Which method you prefer is up to you:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { createCounterProxy, createCounterFunction } from './counter.svelte'

  const { count, increment } = createCounterProxy()
  const { count, setCount, increment } = createCounterFunction()
</script>

<button onclick={() => count.value++}>
  {count.value}
</button>

<button onclick={() => setCount(count() + 1)}>
  {count()}
</button>
```

## Using Classes For Reactive State

Creating a piece of reactive state inside a class works the same:

```ts title="counter.svelte.ts" showLineNumbers
export class Counter {
  count = $state(0)
  // you can also derive values
  double = $derived(this.count * 2)

  increment = () => this.count++
}
```

You can tuck the class inside a function if you want to hide the `new` keyword, but I’m just going to instantiate the class directly:

```html title="+page.svelte" showLineNumbers
<script lang="ts">
  import { Counter } from './counter.svelte'

  const counter = new Counter()
</script>

<button onclick={counter.increment}>
  {counter.count}
</button>
```

Notice how you don’t have to specify a getter and setter for `count` since Svelte does that for you unless you want to:

```ts title="counter.svelte.ts" showLineNumbers
export class Counter {
  // make count private
  #count = $state(0)

  // create property accessors
  get count() {return this.#count }
  set count(value) { this.#count = value }
}
```

If you’re using TypeScript you can use type assertion to type a reactive value inside a class:

```ts title="example.svelte.ts" showLineNumbers
export class Example {
  example = $state() as Type
}
```

## Doing Side Effects

If you need to do a side effect like writing to local storage or updating the DOM you can use `$effect` to track when a value updates:

```ts title="example.svelte.ts" showLineNumbers
export function createCounter() {
  count = $state({ value: 0 })

  $effect(() => {
    console.log(count.value)
  })

  return { count }
}

export class Counter {
  count = $state({ value: 0 })

  constructor() {
    $effect(() => {
      console.log(count.value)
    })
  }
}
```

You should be careful when using functions and classes with effects inside a module outside a Svelte component because effects must have a parent effect for cleanup:

```ts title="example.svelte.ts" showLineNumbers
function createCounter() {
  count = $state({ value: 0 })

  $effect(() => {
    console.log(count.value)
  })

  return { count }
}

// ⛔️ \`$effect\` can only be used inside an effect
// (e.g. during component initialisation)
const counter = createCounter()
```

If you run into that problem you have to wrap the effect with a [root effect](https://svelte.dev/docs/svelte/$effect#$effect.root):

```ts title="example.svelte.ts" showLineNumbers
function createCounter() {
  count = $state({ value: 0 })

  $effect.root(() => {
    $effect(() => {
      console.log(count.value)
    })
  })

  return { count }
}

// 👍️ no problem
const counter = createCounter()
```

You can avoid this problem and do side effects when you read and write to the reactive value:

```ts title="example.svelte.ts" showLineNumbers
export class Counter {
  #count = $state(0)

  get count() {
    console.log(this.#count)
    return this.#count
  }

  set count(value) {
    console.log(value)
    this.#count = value
  }
}
```

## Shared State On The Server

If you’re using SvelteKit and SSR (server-side rendering) [avoid side-effects in load](https://svelte.dev/docs/kit/state-management#No-side-effects-in-load) like using shared state to update a value in your components because it could be shared by your users:

```ts title="+layout.ts" showLineNumbers
import { state } from '$lib/state'

export async function load({ fetch }) {
  const response = await fetch('/api/data')
  const data = await response.json()

  // ⛔️ don't do this
	state.set(data)
}
```

The SvelteKit docs advise you return the data and pass it around to the components that need it using the context API or use [$page.data](https://svelte.dev/docs/kit/load#$page.data):


```ts title="+layout.ts" showLineNumbers
export async function load({ fetch }) {
  const response = await fetch('/api/data')

  return {
    user: await response.json()
  }
}
```

You can spread `data.user` to create a reactive `user` object that can be passed to `setContext`:



```html title="src/routes/+layout.svelte" showLineNumbers
<script lang="ts">
	import { setContext } from 'svelte'

	let { data } = $props()
	let user = $state(...data.user)

	$effect(() => {
    user.name = data.user.name
	})

	setContext('user', user)
</script>
```

```html title="src/routes/user/+page.svelte" showLineNumbers
<script lang="ts">
	import { getContext } from 'svelte'

	const user = getContext('user')
</script>

<p>Welcome {user.name}</p>
```
