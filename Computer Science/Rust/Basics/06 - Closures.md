---
id: 06 - Closures
aliases: []
tags: []
---
## Introduction

The concept of **closures** in rust is the same as **lambda functions** (Java, Python) or **anonymous functions** (Javascript) in other programming languages. The concept is to create temporary function like constructs, which are supposed to only be used in one place. Lets take as an example the following python code
```python
items = [ ("banana", 5), ("apple", 1), ("orange", 9), ("grape", 4)]
items.sort(key = lambda x: x[1])
```
> items = [ ("apple", 1), ("grape", 4), ("banana", 5), ("orange", 9) ]

In this example we create a small anonymous function telling how the sort method is supposed to sort an array where the items itself dont support a natural way of understanding some ordering. We pass to the sort method how it is supposed to sort. Since it is only used in this place, we use the concept of a **lambda** function. Rust provides this functionality under the name of **closure**.

## Closure Syntax

Closures have the following syntax
```rust
| ARGUMENTS... | BODY;
```
where the vertical bars `{rust} |` wrap the input arguments to the closure and the operations are defined inside the body. A comprehensive example can be found below
```rust showLineNumbers
fn main() {
    // Argument and return type can be inferred for lightweight syntax:
    let double_it = |n| n * 2;
    dbg!(double_it(50));

    // Or we can specify types and bracket the body to be fully explicit:
    let add_1f32 = |x: f32| -> f32 { x + 1.0 };
    dbg!(add_1f32(50.));
}
```
Note, **typehints are optional** for closures.

- `line 3` a function is created using **closure** notation
    - `{rust} n` is the argument to the function
    - `line 4` the function is called
- `line 9` typehints can also be added to the arguments

## Capturing

Inside of closures the variables of the **environment** can be **captured**. The behavior can be interpreted that outside variables are borrowed or owned by the closure. 

```rust showLineNumbers
fn main() {
    let max_value = 5;
    let clamp = |v| {
        if v > max_value { max_value } else { v }
    };

    dbg!(clamp(1));
    dbg!(clamp(3));
    dbg!(clamp(5));
    dbg!(clamp(7));
    dbg!(clamp(10));
}
```
- captured types are passed chosen at compiletime by the least demanding form: exclusive reference < shared reference < move (highest demand)
- captured variables are **not mutable**, unless the variable is decorated as **mutable**
    - for `line 2` we would write `{rust} let mut max_value = 5;` and for `line 3` we would write `{rust} let mut clamp = |v| {...}` to be able to change `{rust} max_value` (`{rust} max_value += 1`)

## Closure traits

Closures have traits. Assume we want to pass a **closure** to a function itself, how would one typehint at it? This is where **closure traits** come in. Functions, generally speaking, offer the following types
- `{rust} Fn` -> trait for callable items, i.e. `{rust} fn my_function(...){...}`
    - is a subtrait (subset) of `{rust} FnMut` and `{rust} FnOnce`
- `{rust} FnMut` -> a closure, which mutates inside of the closure, i.e. `{rust} let mut my_function =  | ... | {...}`
- `{rust} FnOnce` -> closure function, usually defined as `{rust} let my_function = | ... | {...}`

The following function shows how a **closure** function can be typehinted.

```{rust} showLineNumbers
fn apply_and_log(
    func: impl FnOnce(&'static str) -> String,
    func_name: &'static str,
    input: &'static str,
) {
    println!("Calling {func_name}({input}): {}", func(input))
}

fn main() {
    let suffix = "-itis";
    let add_suffix = |x| format!("{x}{suffix}");
    apply_and_log(&add_suffix, "add_suffix", "senior");
    apply_and_log(&add_suffix, "add_suffix", "appendix");

    let mut v = Vec::new();
    let mut accumulate = |x| {
        v.push(x);
        v.join("/")
    };
    apply_and_log(&mut accumulate, "accumulate", "red");
    apply_and_log(&mut accumulate, "accumulate", "green");
    apply_and_log(&mut accumulate, "accumulate", "blue");

    let take_and_reverse = |prefix| {
        let mut acc = String::from(prefix);
        acc.push_str(&v.into_iter().rev().collect::<Vec<_>>().join("/"));
        acc
    };
    apply_and_log(take_and_reverse, "take_and_reverse", "reversed: ");
    }
```
- `line 2` shows the trait of a **closure function** as a function argument
- `line 6` invokes that **closure function**
- `line 11` creating an **immutable closure function**
    -`line 12,13` passing it to `{rust} apply_and_log`
        - we pass it as reference such that it is **not consumed**
- `line 16` creating a **mutable closure function** (implementing traits `{rust} FnMut` and `{rust} FnOnce`)
    - is used because vector `{rust} v` is mutated inside
    - `line 20-22` passing it to `{rust} apply_and_log` as **mutable reference**
        - we need to pass it as reference such that the function is **not consumed**
- `line 24` creating an **immutable closure function**
    - `line 29` passing it as "move" to `{rust} apply_and_log`
        - `{rust} take_and_reverse` will be consumed as soon as it is passed
