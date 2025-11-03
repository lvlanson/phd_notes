## Blocks and Scopes
```rust showLineNumbers
fn main() {
    let z = 13;
    let x = {
        let y = 10;
        dbg!(y);
        z - y
    };
    dbg!(x);
    // dbg!(y);
}
```

Note, `{rust} dbg!` is a **macro** outputting the which `file` at which `line` causes the printout. The concept of scopes should be clear at this point, variables only live in their scope and will be unknown outside of them. Variables **will be deallocated outside their scope**.

## if Expressions
Only things to note
- expression is without parentheses
- code block is encapsulated inside braces `{}`
```rust showLineNumbers
fn main() {
    let x = 10;
    if x == 0 {
        println!("zero!");
    } else if x < 100 {
        println!("biggish");
    } else {
        println!("huge");
    }
}
```

One can assign variables similar like to ternary statements in C/C++ with an if else expression. In `rust` those are called `if/else` expressions.
- `{rust} let var = if STATEMENT { OPTION_1 } else { OPTION_2 }`

```rust showLineNumbers
fn main() {
    let x = 10;
    let size = if x < 20 { "small" } else { "large" };
    println!("number size: {}", size);
}
```



## match Expression

`{rust} match` expressions work analogously to other languages with adapted syntax. `{rust} _` is the final case to be considered (`line 7`), which reflects the case if all the previous cases are non-matching.

```rust showLineNumbers
fn main() {
    let val = 1;
    match val {
        1 => println!("one"),
        10 => println!("ten"),
        100 => println!("one hundred"),
        _ => {
            println!("something else");
        }
    }
}
```

`{rust} match` expressions can be used as `{rust} if` expressions for variable assignments

```rust showLineNumbers
fn main() {
    let flag = true;
    let val = match flag {
        true => 1,
        false => 0,
    };
    println!("The value of {flag} is {val}");
}
```

##  Loops

### while loop

The `{rust} while` loop works as expected

```rust showLineNumbers
fn main() {
    let mut x = 200;
    while x >= 10 {
        x = x / 2;
    }
    dbg!(x);
}
```

### for loop
The `{rust} for` loop works similar to the `python` for loop, it iterates over `Iterables` such as arrays. There are is an idiomatic way to create indices with `{rust} for x in 1..5` or to iterate over Iterables like in the second example.

```rust showLineNumbers
fn main() {
    for x in 1..5 {
        dbg!(x);
    }

    for elem in [2, 4, 8, 16, 32] {
        dbg!(elem);
    }
}
```

### loop 

The `{rust} loop` is a infinite loop which only stops by using the `{rust} break` statement 
```rust showLineNumbers
fn main() {
    let mut i = 0;
    loop {
        i += 1;
        dbg!(i);
        if i > 100 {
            break;
        }
    }
}
```

## break and continue

They work the same as in any conventional programming language 
```rust showLineNumbers
fn main() {
    let mut i = 0;
    loop {
        i += 1;
        if i > 5 {
            break;
        }
        if i % 2 == 0 {
            continue;
        }
        dbg!(i);
    }
}
```

The only novelty is that you can **label** which loop you are referring to with your `{rust} break/continue` statement.
- the following example marks an outer loop with the label `{rust} 'outer` and breaks it with `{rust} break 'outer`

```rust showLineNumbers
fn main() {
    let s = [[5, 6, 7], [8, 9, 10], [21, 15, 32]];
    let mut elements_searched = 0;
    let target_value = 10;
    'outer: for i in 0..=2 {
        for j in 0..=2 {
            elements_searched += 1;
            if s[i][j] == target_value {
                break 'outer;
            }
        }
    }
    dbg!(elements_searched);
}
```

## Functions

Functions work as to be expected in a *statically typed* language. **Input and output data types MUST be specified** in the **function signature**.

```rust showLineNumbers title=functions.rs
fn gcd(a: u32, b: u32) -> u32 {
    if b > 0 { gcd(b, a % b) } else { a }
}

fn main() {
    dbg!(gcd(143, 52));
}
```
**IMPORTANT NOTE**
- as can be seen in `line 2` in the example `functions.rs` the final evaluated expression will be the return of the function implicitly. This final expression also **must** follow the return type of the functions' signature.
## Macros

Macros are syntactic shorthands within the code. They are denoted with the exclamation mark `{rust} some_macro!`. Opposite to function calls, where function calls are compiled into the machine code and placed into the stack in memory, macros are shorthands which are expanded during compile time. The macro is then replaced with the assigned code while compiling. 

We have already seen macros such as
- `{rust} println!`
- `{rust} dbg!`
- `{rust} todo!` 

More notable macros are

- `{rust} assert!`
- `{rust} unreachable!`
- `{rust} eprintln!`

```rust showLineNumbers
fn factorial(n: u32) -> u32 {
    let mut product = 1;
    for i in 1..=n {
        product *= dbg!(i);
    }
    product
}

fn fizzbuzz(n: u32) -> u32 {
    todo!()
}

fn main() {
    let n = 4;
    println!("{n}! = {}", factorial(n));
}
```