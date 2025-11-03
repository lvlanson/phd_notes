---
id: 02 - Tuples and Arrays
aliases: []
tags: []
---

## Arrays

The signature to define arrays is `{rust} let a:[TYPE; LENGTH]`. 
- it is important to note, similarly like C/C++, `{rust} LENGTH` must be a known constant during compile time 
- the combination of `{rust}[TYPE; LENGTH]` is considered distinct types for different combinations 
- potentially accessing an array out of bounds will throw an error during compile time 
- accesses during runtime will lead to panics 
- arrays are located on the stack
- arrays can't be changed in size
- printing arrays on the command line requires debug output which is adding the question mark `{rust} ?`, i.e.
- arrays can only contain items of the same datatype given in `{rust} TYPE`
```rust
println!("arr: {arr:?}");
```

The keyword `{rust} mut` just takes care that the content of the array can be changed. The initialization follows by the content of the array put into brackets.

```rust showLineNumbers
fn main() {
    let mut a: [i8; 5] = [5, 4, 3, 2, 1];
    a[2] = 0;
    println!("a: {a:?}");
}
```

Arrays can be also initialized to some constant value using a shorthand. The following example initializes an array 100 times 0

```rust showLineNumbers
fn main(){
    let a: [i32; 100] = [0; 100]; // initialize array with 100 times 0
    dbg!(a);
}
```

## Tuples

Similarly to Python, Rust provides tuples.
- tuples also have fixed length
- tuples can mix datatypes, but are positionally fixed `{rust} (i8, bool)`
- tuples can be accessed by dot notation over its positional index, i.e. `{rust} some_tuple.0` yields the `0`-th entry of `{rust} some_tuple`
- empty tuples `{rust} ()` are the equivalent of `{c} void` in other languages, used for absence of return values
    - this is referred as the **Unit Type**
- tuples can't be used in `{rust} for` loops
- the length of a tuple is fixed

```{rust} showLineNumbers
fn main() {
    let t: (i8, bool) = (7, true);
    dbg!(t.0);
    dbg!(t.1);
}
```

## Array Iteration

Similarly to Python, one can easily iterate over arrays as already highlighted in [[01 - Control Flow Basics#for loop|for loop]]

```rust showLineNumbers
fn main() {
    let primes = [2, 3, 5, 7, 11, 13, 17, 19];
    for prime in primes {
        for i in 2..prime {
            assert_ne!(prime % i, 0);
        }
    }
}
```
- note, the [[01 - Control Flow Basics#Macros|macros]] `{rust} assert_ne!` checks if the two passed arguments are not equal, otherwise it will stop the programm
    - similarly `{rust} assert_eq!, assert!`
- note, there are also debug equivalents [[01 - Control Flow Basics#Macros|macros]] which will only be compiled into non-release builds, i.e. debug builds
    - `{rust} debug_assert!, debug_assert_eq!, debug_assert_neq!`

## Patterns and Destructuring
In python there is the concept of *unpacking* where one can unpack a variable with $n$ elements into $n$ variables. This concept also exists in rust, but with more features
```rust showLineNumbers
fn check_order(tuple: (i32, i32, i32)) -> bool {
    let (left, middle, right) = tuple; // destructuring tuple into left, middle and right
    left < middle && middle < right // returning the final statement, which is bool
}

fn main() {
    let tuple = (1, 5, 3); // rust understands the pattern that tuple will consist of 3 elements
                           // and finally at the function call will understand that its i32
    println!(
        "{tuple:?}: {}",
        if check_order(tuple) { "ordered" } else { "unordered" }
    );
}
```

## User-Defined Types
### Named Structs

Like C/C++ one can create custom datatypes by using `{rust} struct`s. One can think of a struct as a class, where every attribute and method is public. This means those are everywhere accessible. Private attributes/methods however can't be accessed from outside the object. Here a `{rust} struct` is used to bundle information to create a custom datatype, which is rather a primitive construct.

- a variable in a `{rust} struc` is called struct field
- those struct fields do not support default values
- there are different ways to initialize structs
    - see `line 11-14` explicitly assigning the fields with literals
    - see `line 22` implicitly assigning the fields with equally named variables
    - by using **struct update syntax**, which is assigning new values and use already assigned struct values
    ```{rust}
    let jackie = Person {name: String::from("Jackie"), ..avery }; // any missing values are taken from avery
                                                                  // this argument needs to be passed last
    ```
```rust showLineNumbers
struct Person {
    name: String,
    age: u8,
}

fn describe(person: &Person) {
    println!("{} is {} years old", person.name, person.age);
}

fn main() {
    let mut peter = Person {
        name: String::from("Peter"),
        age: 27,
    };
    describe(&peter);

    peter.age = 28;
    describe(&peter);

    let name = String::from("Avery");
    let age = 39;
    let avery = Person { name, age };
    describe(&avery);
}
```

Notable things:
- when passing structs as argument to a function, one needs to pass the reference, i.e. addresse, to the object instead of the object
    - this is achieved by adding `{rust} &` in front of the variable
    - this concept refers to passing by reference instead of passing by value
    - it does not make sense to copy huge data structures in memory, it suffices to pass the address to the structure and go from there
    - rust automatically dereferences the object inside a function, when the datatype is a reference, see `line 7`
- `{rust} String`s are initialized using the `{rust} String` class, unlike python strings must be constructed as objects

### Tuple Structs

Tuple structs are used to give tuples custom type names such as 
```{rust} 
struct Point(i32, i32); // conventional tuple abstracted as Point datatype
struct PoundsOfForce(f64); // single-field wrapper/newtype creating a single field type

fn main() {
    let point = Point(10, 11);
    let force = Newtons(39.4);

    println!("My Point: ({}, {})", point.0, point.1); // tuple positional access
    println!("The Force: {}", force.0);
}
```

- note, if force had `Display` implemented, one could omit the positional access here

### Enums

`{rust} Enum`s are special algebraic data types (ADTs), which encode *magic numbers* into a set of semantically enclosed wrappers. It is common practice to not encode decisive algorithmic information into strings but into numbers. Strings are computationally wasteful in encoding semantic decisions. Imagine the following pseudo-code
```
// some decision
if this_value == "right":
    turn_car_right()
else if this_value == "left":
    turn_car_left()     
```
In high performance environments this is considered bad practice, since it is wasteful to compare strings in time and space complexity. Rather it makes more sense to create an `{rust} Enum` which encodes the semantic meaning numerically
```
Enum Direction:
    Left = 0,
    Right = 1,

if this_value == Directioin.Right:
    turn_car_right()
else if this_value == Direction.Left:
    turn_car_left()

```
Here we expect `this_value` to be a number, but it will be compared with semantic expressions instead of magic numbers, or inefficent strings.

Now the **rust** implementation

```rust showLineNumbers
#[derive(Debug)]
enum Direction {
    Left,
    Right,
}

#[derive(Debug)]
enum PlayerMove {
    Pass,                        // Simple variant
    Run(Direction),              // Tuple variant
    Teleport { x: u32, y: u32 }, // Struct variant
}

fn main() {
    let dir = Direction::Left;
    let player_move: PlayerMove = PlayerMove::Run(dir);
    println!("On this turn: {player_move:?}");
}
```
- **simple variant** is that in order of the attributes the values are incremented by `1` starting from `0`, i.e.
    - `{rust} Direction::Left` = 0
    - `{rust} Direction::Right` = 1
- the `{rust} enum PlayerMove` is more complex
    - `{rust} Pass` still is the standard 0 encoding
    - `{rust} Run(Direction)` is the **Tuple Variant**, where the `{rust} Direction` is accosiated with data     - `{rust} Teleport { x: u32, y: u32}` is the **struct Variant**, where coordinates are encoded as struct
    - the last 2 variants are leaning more into objects
- note, also here the `{rust} enum`s dont implement `Display`, thus, cant naturally be printed
    - the `{rust} #derive(Debug)` directive enables printing in debug mode, i.e. `{:?}`

```rust showLineNumbers
enum Bar {
    A, // 0
    B = 10000,
    C, // 10001
}

fn main() {
    println!("A: {}", Bar::A as u32);
    println!("B: {}", Bar::B as u32);
    println!("C: {}", Bar::C as u32);
}
```
- note, here it is shown how to customize the numbers for `{rust} enum`s
- increments will continue by adding 1

### Type Aliases

A type alias creates a name for another type. The two types can be used interchangeably.

```rust showLineNumbers
enum CarryableConcreteItem {
    Left,
    Right,
}

type Item = CarryableConcreteItem;

// Aliases are more useful with long, complex types:
use std::cell::RefCell;
use std::sync::{Arc, RwLock};
type PlayerInventory = RwLock<Vec<Arc<RefCell<Item>>>>;
```

### Const

- constants are evaluated at compile time, meaning their value must be understood during the code creation process
- similarly to macros constants are **inlined** during compile time
- functions marked `const` must be able to compute values during compile time
- constants are usually written in capital letters

```rust showLineNumbers
const DIGEST_SIZE: usize = 3;
const FILL_VALUE: u8 = calculate_fill_value();

const fn calculate_fill_value() -> u8 {
    if DIGEST_SIZE < 10 { 42 } else { 13 }
}

fn compute_digest(text: &str) -> [u8; DIGEST_SIZE] {
    let mut digest = [FILL_VALUE; DIGEST_SIZE];
    for (idx, &b) in text.as_bytes().iter().enumerate() {
        digest[idx % DIGEST_SIZE] = digest[idx % DIGEST_SIZE].wrapping_add(b);
    }
    digest
}

fn main() {
    let digest = compute_digest("Hello");
    println!("digest: {digest:?}");
}
```

### static
Variables marked `{rust} static` will be visible all over the programm code, making them global variables
- `{rust} static` variables need special handling for threading to keep them in sync
- `{rust} static` variables are by design mutable

```rust showLineNumbers
static BANNER: &str = "Welcome to RustOS 3.14";

fn main() {
    println!("{BANNER}");
}
```

