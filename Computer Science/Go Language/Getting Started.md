|                            | Command           |
| -------------------------- | ----------------- |
| Run Go Program             | `go run $.go`     |
| Compile Go Program         | `go build $.go`   |
| Install Go Library Locally | `go install $lib` |

## Basic Knowledge
- not initialized variables are defaulted with a **default zero** value
- **literals** are numbers, strings or characters with respect to the data type

### Data Types

#### Integers
- **integers** literals can be represented in **different bases** with different prefixes
	- `0b` -> binary
	- `0o` -> octal
	- `0x` -> hexadecimal
- **integers** can be written with underscores, such that they are more readable
	- `1_000_000_000`

![[Figures/integer_types.png|center|500]]

- a `uint8` is also referred to as `byte`
- `int` = `int32` on 32-bit machines (equivalent for `uint`)
- `int` = `int64` on 64-bit machines (equivalent for `uint`)
- default zero is $0$

#### Floating point
- **floats** can be represented with either a *dot* or the letter `e`
	- `10.2`
	- `6.03e23`
- **floats** can also be represented as hexadecimal. Here either the decimal point is used, or for the `0x` notation instead of the `e` for the exponential notation the letter `p` is used

![[Figures/float_types.png|center|500]]

- default zero is $0$
- floats use [IEEE 754 specification](https://en.wikipedia.org/wiki/IEEE_754) (large range, low precision)

#### Rune Literals
- `Runes` are characters surrounded by quotation marks. They can be written
	- unicode characters -> `'a'`
	- 8-bit octal numbers -> `'\141'`
	- 8-bit hexadecimal numbers -> `'\x61'`
	- 16-bit hexadecimal numbers -> `'\u0061'`
	- 32-bit unicode numbers -> `'\U00000061'`

#### Strings
- `Strings` are rune literals encapsulated in double quotation marks as **interpreted string literal**
	- `"I am a string"` where unescaped backslashes cannot appear
- or as **raw string literal**
	- using (\`) backquotes
- zero value is the empty string `""`


#### Booleans 
- booleans can either be `false` or `true`
- default value is `false`
```go
var flag bool // no value assigned, set to false
var isAwesome = true
```

### Complex Numbers
- initialized with  `complex(a,b)` for $a + bi \in \mathbb{C}$
- real values can be extracted with `real()`
- imaginary values can be extracted with `complex()`
- `complex64` which uses `float32`
- `complex128` which uses `float64`

---
### Operators

#### Integers
- arithmetic -> `+ - * / %`
	- dividing two integers gives an integer
	- shorthands `+= -= *= /= %=`
	- division by `0` causes a **panic**
- comparisons -> `== <= >= != < >`
- bit-manipulation -> 
	- bit-shift left `<<` (right `>>`)
	- logical AND `&`
	- logical OR `|`
	- logical XOR `^`
	- logical AND NOT `&^`
	- shorthands `<<= >>= &= ...` all available

### Floats
- arithmetic -> `+ - * /` (no mod)
	- dividing a non-zero float by `0` returns either `+Inf` or `-Inf`
	- dividing a zero float by `0` returns `NaN` (not a number)
- comparisons on float exist (same as integers) but **should not be used** directly 
	- if necessary use some epsilon range and compare over that

### Strings
- arithmetic -> `+` concatenates strings
- strings can be compared using the already mentioned comparative operators
- strings are **immutable**
	- one can only reassign, but not change

---
## Explicit Type Conversion

- Go does not allow *automatic type promotion*
- Example
```go
var x int = 10
var y float64 = 30.2
var z float64 = float64(10) + y
var d int = x + int(y)
```
- go does not treat other types as booleans, hence one must

## Variable Declaration and Initialization

```go
var x int = 10
var x = 10
var x int // Zero Initialized

/* Multiple Variables */
var x,y int = 10,20
var x,y int 
var x,y = 10, "hello"

var (
	x    int
	y        = 20
	z    int = 30
	d, e     = 40, "hello"
	f, g string 
)

/* Shorthand */
var x = 10
x := 10

var x, y = 10, "hello"
x, y := 10, "hello"

/* Assign to Existing Variables with Shorthand */
x := 10
x, y := 30, "hello"
```

- note: shorthand can't be used at package level (outside functions)

### Constants

```go
const x int64 = 10

const (
    idKey   = "id"
    nameKey = "name"
)
```
- immutables can only be used on values which are known at compile time

### Arrays

#### 1-dimensional Arrays
```go
var x[3] int
var x = [3]int{10, 20, 30}
var x = [12]int{1, 5: 4, 6, 10: 100, 15} // for sparse arrays
```
- the last line produces the array
``` [1, 0, 0, 0, 0, 4, 6, 0, 0, 0, 100, 15]```

#### 2-dimensional Arrays
```go
var x[2][3]int
```

##### Access Values
```go
var x = [3]int{10, 20, 30}
fmt.Println(x[2])
```

- arrays are rarely used in go, because their size need to be known at run-time

### Slices
- by not specifying the argument inside the square brackets, you create some kind of dynamic array

```go
var x = []int{10, 20, 30}
```

- all rules from arrays apply here too
- **but** the following line initializes an array of length 0
```go
var x []int
```
which compares true to `nil`
- **important:** slices are not comparable!


#### len
The `len` function returns the length of an array-like structure

#### append
The append function appends values to some slice

```go
var x []int
x = append(x, 10)
x = append(x, 5, 6, 7)
```
An array/slice can be appended to a slice using the `...` operator
```go
y := []int{20, 30, 40}
x = append(x, y...)
```

#### cap
`cap` returns the currently allocated length for the slice
```go
cap(x)
```
the capacity grows automatically

#### make
`make` can declare a slice of some length and capacity beforehand
```go
x := make([]int, 5) //length = 5, capacity = 5
```
`make`can set these parameters distinctively
```go
x := make([]int, 5, 10) //length = 5, capacity = 10 with x[0] to [x4] is 0
```

#### slicing
Slices can be sliced similar to python
 ```go
 x := []int{1, 2, 3, 4}
 d := x[1:3]
 ```
 with the [start:stop] code. **Important to note**, slices share the memory, hence changing one slice changes the related slices.
```go
 x[1] = 10 // d[0] is 10 now
```
This also affects `append`, appending to a slice `x[:2]` will append to 

**<span style="color:#f7b8ff">Slicing can be also used on arrays</span>**

#### copy

To create independent slices, one can `copy` slices, such that they not share memory

```go
x := []int{1, 2, 3, 4}
y := make([]int, 4)
num := copy(y, x)
```

If one wants to copy only a part of an array/slice, one can restrict the value in the make function

```go
x := []int{1, 2, 3, 4}
y := make([]int, 2)
num  := copy(y, x)
num2 := copy(y, x[2:])
num2 := copy(x[1:], x[:2])
```

### Maps

... are Hash-Maps
```go
totalWins := map[string]int{}
teams := map[string][]string {
	"Orcas": []string{"Fred", "Ralph", "Bijou"},
	"Lions": []string{"Sarah", "Peter", "Billie"},
	"Kittens": []string{"Waldo", "Raul", "Ze"},
}
ages := make(map[int][]string, 10) // make initialized maps will have length 0 but capacity 10
```

Working with Maps is similar to other languages
```go
totalWins := map[string]int{}
totalWins["Orcas"] = 1
totalWins["Lions"] = 2
fmt.Println(totalWins["Orcas"])
fmt.Println(totalWins["Kittens"])
```

Asking for a key which is not defined returns the **zero-value**

#### Comma Ok Idiom

One can also determine if a key is available by using the **comma ok idiom**
```go
m := map[string]int{
"hello": 5,
"world": 0,
}
v, ok := m["hello"]
fmt.Println(v, ok) // > 5, true

v, ok = m["world"]
fmt.Println(v, ok) // > 0, true

v, ok = m["goodbye"]
fmt.Println(v, ok) // > 0, false
```

#### Deleting from Maps

```go
m := map[string]int{
	"hello": 5,
	"world": 10,
}
delete(m, "hello")
```

### Structs
A struct is 

```go
type person struct {
	name string
	age int
	pet string
}
```