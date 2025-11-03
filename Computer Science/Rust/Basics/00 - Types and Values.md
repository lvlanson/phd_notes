- this [tutorial](https://google.github.io/comprehensive-rust/) is used

## Function Definitions
```rust showLineNumbers title=helloworld.rs
fn main() {
	println!("Hello World!");
}
```

## Data Types
- data types are static

```rust showLineNumbers
fn main() {
	let x: i32 = 10; // explicit type assignment
    let y = 10;      // implicit type assignment
    println!("x: {x}");
    println!("y: {y}");
}
```

- basic datatypes are

| Datatype               | Code                           | Examples               |
| ---------------------- | ------------------------------ | ---------------------- |
| Signed integers        | i8, i16, i32, i64, i128, isize | -10, 0, 1_000, 123_i64 |
| Unsigned integers      | u8, u16, u32, u64, u128, usize | 0, 123, 10_u16         |
| Floating point numbers | f32, f64                       | 3.14, -10.0e20, 2_f32  |
| Unicode scalar values  | char                           | 'a', 'α', '∞'          |
| Booleans               | bool                           | true, false            |


## Arithmetic
```rust showLineNumbers title=functions.rs
fn interproduct(a: i32, b: i32, c: i32) -> i32 {
    return a * b + b * c + c * a;
}

fn main() {
    println!("result: {}", interproduct(120, 100, 248));
}
```

- functions arguments require type declarations i.e. `{rust} a:i32` 
- functions require return type i.e. `{rust} -> i32`