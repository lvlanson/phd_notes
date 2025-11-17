---
id: 1762158851-BZQV
aliases:
  - 03 - Pattern Matching
tags: []
---

## Irrefutable Patterns

Recall [[02 - Tuples and Arrays#patterns and destructuring |patterns and destructuring]], where we have seen how destructuring has worked similar to unpacking in Python and how patterns such as `{rust} let a = (1,2,3)` correctly assigns the respective datatypes to `{rust} a`. Rust offers great flexibility in destructuring and pattern matching. Next we will look at different methods on how to **destructure** tuples or also arrays.
```rust showLineNumbers
fn takes_tuple(tuple: (char, i32, bool)) {
    let a = tuple.0;
    let b = tuple.1;
    let c = tuple.2;

    // This does the same thing as above.
    let (a, b, c) = tuple;

    // Ignore the first element, only bind the second and third.
    let (_, b, c) = tuple;

    // Ignore everything but the last element.
    let (.., c) = tuple;
}

fn main() {
    takes_tuple(('a', 777, true));
}
```
- in `lines 2-4` variables are unpacked using the **positional indexing**
- in `line 7` variables are unpacked using **destructuring**
- in `line 10` the `{rust} _` symbol highlights that the first element of the tuple should be disregarded
- in `line 13` all preceding values before the last one should be ignored by using the range pattern `{rust} ..`

Note, it is also possible to ignore values in the middle of the tuple by having
```{rust}
let (a, .., c) = tuple;
```

## Matching Values
`{rust} match` is a very powerful tool, which is widely used in Rust. Though, `{rust} match` in its most standard form is present in most programming languages, but is not closely as tightly knit into usage patterns as it is in Rust. First we will look into a usecase more leaning into something we already encountered in [[01 - Control Flow Basics#match Expression|match Expression]] earlier. In the following example we can see more expressive cases.
```{rust} showLineNumbers
#[rustfmt::skip] // tells the formatter to ignore the following scope
fn main() {
    let input = 'x';
    match input {
        'q'                       => println!("Quitting"),
        'a' | 's' | 'w' | 'd'     => println!("Moving around"),
        '0'..='9'                 => println!("Number input"),
        key if key.is_lowercase() => println!("Lowercase: {key}"),
        _                         => println!("Something else"),
    }
}
```
Note, `{rust} #[rustfmt::skip]` is an attribute to tell the automatic formatting tool `rustfmt` to not change the format of the following codeblock
- `line 5` does simple character matching with datatype `{rust} char`
- `line 6` different chars connected with *or* `{rust} |`
- `line 7` using the range operator `{rust} ..` with inclusion of the last element by using `{rust} ..=`
- `line 8` advanced expression, checking if `{rust} key` holds a condition
    - this is called a **match guard**
    - here one can use a dummy variable representing the input
    - a different name from known variables need to be chosen such that it is considered a **variable binding** 
        - otherwise the value of the outer scope variable is inaccessible anymore
- `line 9` standard *default* case

An interesting feature is also that one can deconstruct rather complex datatypes inside a match arm. In Rust there is a special `{rust} enum` type called `{rust}Option::Some<T>`. Note, this notation tells us that `{rust} Some<T>` is constructed such that it can take any arbitrary type `{rust} <T>`, but as soon as one is inferred it will remain fixed with that type. The purpose of such options is to allow optional returns, i.e.
```rust 
enum Option<T> {
    Some(T),
    None,
}
```
either there is the return with `{rust} Some(T)` or `{rust} None`. Now, going to the destructuring of such an `{rust} enum` in a `{rust} match`
```rust showLineNumbers 
let opt = Some(123);
match opt {
    outer @ Some(inner) => {
        println!("outer: {outer:?}, inner: {inner}");
    }
    None => {}
}
```
- `line 3` destructures `{rust} Some(123)` such that you can actually use the passed value `{rust} inner` in the match arm, while still being able to use the whole enum
## Destructuring Structs

As shown in [[#Matching Values]] in the last example, one can destructure `{rust} enum`s. In a similar fashion this can be done with `{rust} struct`s
```rust showLineNumbers
struct Foo {
    x: (u32, u32),
    y: u32,
}

#[rustfmt::skip]
fn main() {
    let foo = Foo { x: (1, 2), y: 3 };
    match foo {
        Foo { y: 2, x: i }   => println!("y = 2, x = {i:?}"),
        Foo { x: (1, b), y } => println!("x.0 = 1, b = {b}, y = {y}"),
        Foo { y, .. }        => println!("y = {y}, other fields were ignored"),
    }
}
```
- `line 10` if we have a struct `{rust} Foo` with a matching `{rust} y == 2` then we can call the corresponding `{rust} x` as `{rust} i`
    - if in the example we have `{rust} Foo { x: (1, 2), y: 2 };`, then we have `{rust} i = (1, 2)`
- `line 11` if in the struct `{rust} Foo`  there is an `x.0` with `1` then we get a binding to `{rust} b`
- `line 12` we are only interested in having a `{rust} y`

### Very Important Note
#### Passing by Reference VS Passing by Copy
What does actually happen when we `{rust} match foo`? The variable `{rust} foo` is being copied in memory to perform the matching. For low level languages such as Rust this is not the standard approach. Instead of *copying the values* to the matcher, one should instead pass a *reference*  to the matcher. Here, a pointer to the memory cell, where the larger datastructure is to be found, will be passed. This is way more efficient since Rust only needs to copy an address instead of a larger data-structure. The handling inside the match remains the same, since Rust handles the dereferencing of the address automatically.
```rust
//...
    match &foo {
    // ...
    }
// ...
```

#### Ownership and Consumption
In Rust **ownership** of variables is an integral concept in how data can be manipulated and lives within Rust code. When passing `{rust} foo` directly to match, then the `{rust} match` block owns the variable `{rust} foo`. In Rust terminology the variable is **moved** to the `{rust} match` block. More complex objects can have a *trait* implemented called `Copy`. If this trait is implemented, then the original variable will still be allocated and known to the program. If that trait is not implemented, such as for `{rust} String`s, then only a *shallow copy* will be moved to the `{rust} match` block. For `{rust} struct`s all fields need to implement `Copy` and only then `{rust} struct`s will actually be copied and the original variable will be preserved, otherwise it will be **consumed**. This means, as soon as the variable is passed, the original one will be invalidated. In Rust terminology this is called that **the variable is consumed**.

In the case of a `{rust} String`, when initialized the metadata such as the *pointer* to the characters, the *length* of the string and the *memory capacity*  are stored on the **stack**, while the actual sequence of characters are stored on the **heap**. When doing a *shallow copy*, then the *metadata* is being copied. While a deep copy actually copies also the sequence of characters. As soon as the shallow copy goes out of scope, Rust frees the memory used for the *heap data* rendering the original variable pointing to that data useless, i.e. invalidating it.
```{rust} showLineNumbers
fn main() {
    let foo = Foo { name: String::from("Word"), y: 3 };      // foo still exists here
    match foo {                             // foo is being moved and the original foo is being invalidated
        Foo { y: 2, name: i }   => println!("y = 2, name = {i:?}"),
        Foo { y, .. }        => println!("y = {y}, other fields were ignored"),
    }                                       // the match block terminates and the heap data is being freed
    println!("{:?}", foo)                   // will throw an error since foo does not exist anymore
}
```

When finally using the *reference* over the *copy*/*move*, `{rust} match` only **borrows** `{rust} foo` instead of **owning** and **consuming** it.

## Enums
Enums can be destructured similar to [[#Matching Values|Tuples]]. In fact this is a common design pattern for Rust **error handling**. 

```rust showLineNumbers
enum Result {
    Ok(i32),
    Err(String),
}

fn divide_in_two(n: i32) -> Result {
    if n % 2 == 0 {
        Result::Ok(n / 2)
    } else {
        Result::Err(format!("cannot divide {n} into two equal parts"))
    }
}

fn main() {
    let n = 100;
    match divide_in_two(n) {
        Result::Ok(half) => println!("{n} divided in two is {half}"),
        Result::Err(msg) => println!("sorry, an error happened: {msg}"),
    }
}
```
- `lines 1-4` creates a `{rust} enum` for storing a result, if on fail stores an error string
- `lines 17-18` utilizes the signature of the enum to encode the correct handling of the result of the function call

## Let Control Flow

### if let Expressions

`{rust} if let` expressions can make error handling a breeze and creates very readable code. See the following example.

```rust showLineNumbers
use std::time::Duration;

fn sleep_for(secs: f32) {
    let result = Duration::try_from_secs_f32(secs);

    if let Ok(duration) = result {
        std::thread::sleep(duration);
        println!("slept for {duration:?}");
    }
}

fn main() {
    sleep_for(-10.0);
    sleep_for(0.8);
} 
```

- in the `{rust} if` statement, we destructure the content of the variable `{rust} result`
    - `{rust} result` is the return of `{rust} Duration::try_from_secs_f32` and returns `{rust} Result<Duration, TryFromFloatSecsError>`
    - in this statement the variable `{rust} duration` is initialized from the `{rust} Ok` enum field
    - if it does not exist, here instead `{rust} Err` would exist, one not enter the if block
- often this is used for **error-handling** where the error is being caught and handled

### while let Statements

`{rust} while let` works very similar to `{rust} if let` except that it keeps the loop active, until the `{rust} let` assignment breaks.

```rust showLineNumbers
fn main() {
    let mut name = String::from("Comprehensive Rust 🦀");
    while let Some(c) = name.pop() {
        dbg!(c);
    }
    // (There are more efficient ways to reverse a string!)
}
```

## let else Statements
This section addresses the error handling as the next step of the `{rust} if let` statement

```rust showLineNumbers
fn hex_or_die_trying(maybe_string: Option<String>) -> Result<u32, String> {
    let Some(s) = maybe_string else {
        return Err(String::from("got None"));
    };

    let Some(first_byte_char) = s.chars().next() else {
        return Err(String::from("got empty string"));
    };

    let Some(digit) = first_byte_char.to_digit(16) else {
        return Err(String::from("not a hex digit"));
    };

    Ok(digit)
}
```
Recall, the signature of an option is
```rust
pub enum Option<T> {
    None,
    Some(T),
}
```
Therefore the `{rust} let` binding is trying to assign to the variable from the `{rust} Option<T>::Some(T)`, if this fails then and only then the code jumps into the `{rust} else` scope.
- `line 2` assigns the string variable `{rust} s` 
    - if `{rust} maybe_string` is not a `{rust} String` and thus `{rust} None` due to the Opttions signature, the code will go into the `{rust} else` block in `line 3`
- `line 6` assigns the first byte to variable `{rust} first_byte_char`
    - if `{rust} s` is an empty string of length 0, then code will go into the `{rust} else` block in `line 7`
- `line 10` assigns the hex to `{rust} digit` 
    - if `{rust} first_byte_char` can't be converted to a hex digit, code will go int `{rust} else` block in `line 11`
