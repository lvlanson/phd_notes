### State Objects

^f48ab9

State objects are watched by svelte and manipulated into the DOM without rebuilding it. This can be achieved using the `$state()` **<span style="color:#38ffa9">rune</span>**.

##### Example 1
Printing the content of the `count` variable.

```ts showLineNumbers
<script>
	let count = $state(0);

	function increment() {
		count++
	}
</script>

<button onclick={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>
```


##### Example 2
Printing the elements of an array `numbers`.

```html showLineNumbers {2,9}
<script>
	let numbers = $state([1, 2, 3, 4]);

	function addNumber() {
		numbers.push(numbers.length+1)
	}
</script>

<p>{numbers.join(' + ')} = ...</p>

<button onclick={addNumber}>
	Add a number
</button>

```

### Dependent Objects (Derive)
If an object is dependent on a [[#^f48ab9|stateful]] object, then it can be declared with the `$derive()` **<span style="color:#38ffa9">rune</span>**.

##### Example 1
Printing the numbers of a state and **<span style="color:#38ffa9">deriving</span>** the sum from it and printing it.

```html showLineNumbers {3}
<script>
	let numbers = $state([1, 2, 3, 4]);
	let total = $derived(numbers.reduce((t, n) => t + n, 0));
	function addNumber() {
		numbers.push(numbers.length + 1);
	}
	function reset(){
		numbers.pop()
	}
</script>

<p>{numbers.join(' + ')} = {total}</p>

<button onclick={addNumber}>
	Add a number
</button>

<button onclick={reset}>
	Pop
</button>

```

### Logging States
To `console.log` states we have to use `$state.snapshot()`, otherwise we will get a warning.

##### Example 1 

```html showLineNumbers {2,7}
<script>
	let numbers = $state([1, 2, 3, 4]);
	let total = $derived(numbers.reduce((t, n) => t + n, 0));

	function addNumber() {
		numbers.push(numbers.length + 1);
		console.log($state.snapshot(numbers));
	}
</script>

<p>{numbers.join(' + ')} = {total}</p>

<button onclick={addNumber}>
	Add a number
</button>
```

---
There is also the possibility to always log a variable, i.e. watching it with
`$inspect()`

##### Example 2
```html showLineNumbers {3,9}
<script>
	let numbers = $state([1, 2, 3, 4]);
	let total = $derived(numbers.reduce((t, n) => t + n, 0));

	function addNumber() {
		numbers.push(numbers.length + 1);
	}

	$inspect(numbers)
</script>

<p>{numbers.join(' + ')} = {total}</p>

<button onclick={addNumber}>
	Add a number
</button>
```