## Methods

In *object oriented* programming one can define classes which in its most basic form consist of
- attributes
- methods
While rust enables the use of *object oriented* design, its approach surely differs from most other object oriented programming languages. The definition of classes is split into two parts
- attributes => defined by `{rust} struct`s
- methods => defined by `{rust} trait`s

Therefore, a `{rust} struct` allows us to define a **new type**, which encapsulates possibly different attributes into a single type. This type can then be extended with the definition of methods by using `{rust} trait`s. 

```rust showLineNumbers
#[derive(Debug)]
struct CarRace {
    name: String,
    laps: Vec<i32>,
}

impl CarRace {
    // No receiver, a static method
    fn new(name: &str) -> Self {
        Self { name: String::from(name), laps: Vec::new() }
    }

    // Exclusive borrowed read-write access to self
    fn add_lap(&mut self, lap: i32) {
        self.laps.push(lap);
    }

    // Shared and read-only borrowed access to self
    fn print_laps(&self) {
        println!("Recorded {} laps for {}:", self.laps.len(), self.name);
        for (idx, lap) in self.laps.iter().enumerate() {
            println!("Lap {idx}: {lap} sec");
        }
    }

    // Exclusive ownership of self (covered later)
    fn finish(self) {
        let total: i32 = self.laps.iter().sum();
        println!("Race {} is finished, total lap time: {}", self.name, total);
    }
}

fn main() {
    let mut race = CarRace::new("Monaco Grand Prix");
    race.add_lap(70);
    race.add_lap(68);
    race.print_laps();
    race.add_lap(71);
    race.print_laps();
    race.finish();
    // race.add_lap(42);
}
```
Explanation:
- `lines 2-5` defines new type `{rust} CarRace`
- `lines 9-11` defines the **constructor**
    - no **receiver** `{rust} self` is passed
    - it is naming convention to call it `{rust} new`
    - to that method to be a constructor conceptionally it must return `{rust} Self` constructing its base type it refers to
- `lines 14-16` defines a method, where
    - its first argument is a **mutable reference** to itself
    - this means `{rust} self` is only borrowed to the function, but can be changed
- `lines 19-24` defines a method, where
    - `{rust} self` is borrowed again, but is not allowed to be changed
- `lines 26-30` defines a method, where
    - the ownership of `{rust} self` is transfered to the method
    - the object will be **consumed** by the function 
    - as pointed out before, the object with its attributes will be deallocated as soon as it is passed to the function

## Traits

A trait extends the set of common tools of *object oriented* programming. A `{rust} trait` can be thought of as an `{java} interface` like in *Java*. This means we can define a required set of functions a `{rust} impl` has to implement in order to be of the same type.

The following examples shows the definition of a `{rust} trait` with the implementation of the `{rust} trait` in a specific `{rust} impl`.a

```rust showLineNumbers
trait Pet {
    fn talk(&self) -> String;

    fn greet(&self) {
        println!("Oh you're a cutie! What's your name? {}", self.talk());
    }
}

struct Dog {
    name: String,
    age: i8,
}

impl Pet for Dog {
    fn talk(&self) -> String {
        format!("Woof, my name is {}!", self.name)
    }
}

fn main() {
    let fido = Dog { name: String::from("Fido"), age: 5 };
    dbg!(fido.talk());
    fido.greet();
}
```
In more detail:
- `lines 1-7` defines a `{rust} trait`, where
    - `line 2` defines a required method, which must be implemented
    - `lines 4-6` defines a default method implementation
- `lines 9-12` defines a new type `{rust} Dog`
- `lines 14-18` defines the `{rust} impl`, where
    - `line 14` uses the `trait for type` pattern, where `Pet` will be used **for** the type `Dog`a
    - `line 15` implements the required method


## Supertraits

Traits can also extend/inherit/implement other traits. This is called **trait inheritance** or **supertraits**.

```rust showLineNumbers
trait Animal {
    fn leg_count(&self) -> u32;
}

trait Pet: Animal {
    fn name(&self) -> String;
}

struct Dog(String);

impl Animal for Dog {
    fn leg_count(&self) -> u32 {
        4
    }
}

impl Pet for Dog {
    fn name(&self) -> String {
        self.0.clone()
    }
}

fn main() {
    let puppy = Dog(String::from("Rex"));
    println!("{} has {} legs", puppy.name(), puppy.leg_count());
}
```

## Associated Types

Associated types are placeholder types within `{rust} trait`s. Usually they are used to define the output of an interfaced function.

```rust showLineNumbers
#[derive(Debug)]
struct Meters(i32);
#[derive(Debug)]
struct MetersSquared(i32);

trait Multiply {
    type Output; //associated type
    fn multiply(&self, other: &Self) -> Self::Output;
}

impl Multiply for Meters {
    type Output = MetersSquared; // implemented associated type
    fn multiply(&self, other: &Self) -> Self::Output {
        MetersSquared(self.0 * other.0)
    }
}

fn main() {
    println!("{:?}", Meters(10).multiply(&Meters(20)));
}
```
We can see
- `line 7` interfaces an associated type as output for `line 8`
- `line 12` defines that type, while the associated type is still used in `line 13`

## Deriving

Deriving can avoid having too much boilerplate code, if there exists already `{struct} impl` implementations, such that one only desires to link those with the respective data type

```rust showLineNumbers
#[derive(Debug, Clone, Default)]
struct Player {
    name: String,
    strength: u8,
    hit_points: u8,
}

fn main() {
    let p1 = Player::default(); // Default trait adds `default` constructor.
    let mut p2 = p1.clone(); // Clone trait adds `clone` method.
    p2.name = String::from("EldurScrollz");
    // Debug trait adds support for printing with `{:?}`.
    println!("{p1:?} vs. {p2:?}");
}
```

- `line 1` introduces the traits via macros `{trust} #[deriv(...)]` onto the following new type
- `lines 9, 10, 13` make use of the derived implementations
