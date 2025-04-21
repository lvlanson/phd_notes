### Introduction

Some important facts about Javascript are important to know. **Passing the following arguments to a function is handled as follows**
- **<span style="color:#38ffa9">Objects and Arrays</span>** are passed as reference (where objects refer to maps `{ts} obj = {key : value}`
- **<span style="color:#38ffa9">Values</span>** are passed by value, where anything except for *objects and arrays* are considered values

The Javascript [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions?utm_source=chatgpt.com) states
>
>Arguments are always [*passed by value*](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_reference) and never *passed by reference*. This means that if a function reassigns a parameter, the value won't change outside the function. More precisely, object arguments are [*passed by sharing*](https://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_sharing), which means if the object's properties are mutated, the change will impact the outside of the function. For example:
>
>```js
>function updateBrand(obj) {
  // Mutating the object is visible outside the function
  obj.brand = "Toyota";
  // Try to reassign the parameter, but this won't affect
  // the variable's value outside the function
  obj = null;
}
>
>const car = {
  brand: "Honda",
  model: "Accord",
  year: 1998,
};
>
>console.log(car.brand); // Honda
>
>// Pass object reference to the function
>updateBrand(car);
>
>// updateBrand mutates car
>console.log(car.brand); // Toyota
>```

### Using Classes with Svelte 5

To use states inside classes and to manipulate them, one has to pass `objects` into the `class instance`. See the following example

```html title="App.svelte" showLineNumbers {5, 6, 9,10}
<script>
	import Slider from "./Slider.svelte"
	import { Point } from "./script.svelte.js"

	let value = $state({ value: null });
	let pt = new Point(value);
</script>

<h1>Point x value: {pt.x?pt.x:"Empty"}</h1>
<h1>Point y value: {pt.y?pt.y:"Empty"}</h1>
<h1>Vale from slider: {value.value}</h1>
<Slider bind:value={value.value}></Slider>
```

```html title="Slider.svelte" showLineNumbers {2,7}
<script>
	export let value;
</script>

<div>
  <p>Integer Scale</p>
  <input type="range" bind:value>
</div>
```

```ts title="script.svelte.js" showLineNumbers {4,5,7,8}
export class Point{
	#value;
	
	x = $derived(this.value.value);
	y = $derived(this.value.value);
	
	constructor(value) {
		this.value = value;
	}
}
```