---
id: 05 - Generics
aliases: []
tags: []
---
## Generic Functions

Rust provides a powerful design to implement functions for unknown data types, without having to define such a function for each type. Lets say we had functions like
```rust
fn add_i32(n: i32, m: i32) -> i32{...}
fn add_f64(n: f64, m: f64) -> f64{...}
```
This would result in having many functions doing basically the same just for different types. For this Rust provides **generics**. Below you will see the signature of a **generic**.
```rust
fn add<T>(n: T, m: T) -> T{...}
```
where `{rust} T` is a generic datatype and can be used in the function definition as needed. The function then can be called by just assigning for `{rust} n` and `{rust} m` some type and rust will automatically infer the correct type accordingly. See below
```rust
add(2, 3);
```
Below a comprehensive example can be found
```rust showLineNumbers
fn pick<T>(cond: bool, left: T, right: T) -> T {
    if cond { left } else { right }
}

fn main() {
    println!("picked a number: {:?}", pick(true, 222, 333));
    println!("picked a string: {:?}", pick(false, 'L', 'R'));
}
```
Note, it is **very important** that the operations on the generics are supported by the generics. Lets say our `{rust} pick` function would do the following
```rust 
// THIS CODE WILL THROW AN ERROR
fn pick<T>(cond: bool, left: T, right: T) -> T {
    if cond { left } else { left + right }
}
```
The compiler would throw an error, because `{rust} left + right` is not guaranteed to work with every datatype. For it to properly work `{rust} T` must implement `{rust} std::ops::Add`. Hence, one needs to tell the compiler, that it is guaranteed that the **generic type** does allow adding them together.

## Trait Bounds

To solve the problem described previously, one can specify *generics* with **traits**. 

```rust showLineNumbers
fn duplicate<T: Clone>(a: T) -> (T, T) {
    (a.clone(), a.clone())
}

fn main() {
    let foo = String::from("foo");
    let pair = duplicate(foo);
    println!("{pair:?}");
}
```
- `line 1` defines `{rust} T` to be of *trait* `Clone` implementing the `clone` method
- `line 2` utilizes the guaranteed *trait* of the objects

Note, if the trait would have not been given, we would expect the same error as previously described. If multiple *traits* are needed, one can provide them by separating them with a `{rust} +`, i.e.

```rust
fn some_function<T: Trait_1 + Trait_2>{...}
```

## Generic Traits
So far we have used *generics* on functions to have a placeholder for generic types. We can do the same for `{rust} traits`. See the following example
```rust showLineNumbers
#[derive(Debug)]
struct Foo(String);

impl From<u32> for Foo {
    fn from(from: u32) -> Foo {
        Foo(format!("Converted from integer: {from}"))
    }
}

impl From<bool> for Foo {
    fn from(from: bool) -> Foo {
        Foo(format!("Converted from bool: {from}"))
    }
}

fn main() {
    let from_int = Foo::from(123);
    let from_bool = Foo::from(true);
    dbg!(from_int);
    dbg!(from_bool);
}
```
for better understanding, the `{rust} std` implementation of `{rust} From` is added here
```rust 
pub trait From<T>: Sized {
    fn from(value: T) -> Self;
}
```
Note, the `{rust} std` implementation uses the generic type `{rust} <T>` on its trait definition.
- `line 4` implements a method for `{rust} Foo` where the generic is specified as `{rust} u32`
- `line 10` does the same but for type `{rust} bool`
- `lines 17,18` apply the implementations

## impl Trait

Similarly to [[#trait Bounds]] one can also define traits on the parameters of a function instead of on the function itself. Look at the following exampe using [[#trait Bounds]] 
```rust
fn add<T: Into<i32>(x: T) -> i32{...}
```
Instead of defining the trait on the function, one can instead define it on the argument, see
```rust
fn add(x: impl Into<i32>) -> i32{...}
```
A comprehensive example can be found bewow
```rust showLineNumbers
// Syntactic sugar for:
//   fn add_42_millions<T: Into<i32>>(x: T) -> i32 {
fn add_42_millions(x: impl Into<i32>) -> i32 {
    x.into() + 42_000_000
}

fn pair_of(x: u32) -> impl std::fmt::Debug {
    (x + 1, x - 1)
}

fn main() {
    let many = add_42_millions(42_i8);
    dbg!(many);
    let many_more = add_42_millions(10_000_000);
    dbg!(many_more);
    let debuggable = pair_of(27);
    dbg!(debuggable);
}
```

Note, here we do not give a specific type, but rather we ask for the interface `{rust} impl`.

## dyn Trait
Dynamic trait allows for more flexibility on how objects are known during compile time versus runtime. See the following code

```rust showLineNumbers
struct Dog {
    name: String,
    age: i8,
}
struct Cat {
    lives: i8,
}

trait Pet {
    fn talk(&self) -> String;
}

impl Pet for Dog {
    fn talk(&self) -> String {
        format!("Woof, my name is {}!", self.name)
    }
}

impl Pet for Cat {
    fn talk(&self) -> String {
        String::from("Miau!")
    }
}

// Uses generics and static dispatch.
fn generic(pet: &impl Pet) {
    println!("Hello, who are you? {}", pet.talk());
}

// Uses type-erasure and dynamic dispatch.
fn dynamic(pet: &dyn Pet) {
    println!("Hello, who are you? {}", pet.talk());
}

fn main() {
    let cat = Cat { lives: 9 };
    let dog = Dog { name: String::from("Fido"), age: 5 };

    generic(&cat);
    generic(&dog);

    dynamic(&cat);
    dynamic(&dog);
}
```

The `generic` function uses **static dispatch**.

* **Signature:** `fn generic(pet: &impl Pet)`
* **Mechanism:** When the Rust compiler sees `&impl Pet`, it treats it similarly to a generic type parameter (e.g., `fn generic<T: Pet>(pet: &T)`).
* **Compilation Time Resolution:** The compiler generates a **separate, specialized version** of the `generic` function for **every concrete type** it's called with (`Cat` and `Dog`). This process is called **monomorphization**.
* **Performance:** Extremely fast because the exact code to call (`Dog::talk` or `Cat::talk`) is known and hardcoded at compile time. There is **no runtime overhead**.
* **Data Size:** The compiler knows the exact size of the type `T` (e.g., `Dog` or `Cat`) at compile time.

---

The `dynamic` function uses **dynamic dispatch** via a **trait object**.

* **Signature:** `fn dynamic(pet: &dyn Pet)`
* **Mechanism:** The type `&dyn Pet` is a **trait object**. A trait object is a **two-word pointer** (a fat pointer) on the stack:
    1.  A pointer to the actual data (`Dog` or `Cat` instance).
    2.  A pointer to a **vtable** (virtual method table) for the `Pet` trait. 
* **Runtime Resolution:** When `pet.talk()` is called inside the `dynamic` function, the program **looks up** the correct `talk` function pointer in the vtable *at runtime*. This is the **dynamic dispatch**.
* **Type Erasure:** This is also called **type erasure** because within the `dynamic` function, the original concrete type (`Dog` or `Cat`) is "erased." All the function knows is that it has a pointer to *some* data that implements `Pet` and an associated vtable.
* **Flexibility:** It allows you to put different concrete types (`Dog` and `Cat`) into the **same collection** (e.g., `Vec<Box<dyn Pet>>`), which static dispatch cannot do.
* **Performance:** Slightly slower than static dispatch because of the **runtime indirection** (looking up the function in the vtable).


