# Go

### 5 Reason to choose go-lang

- [x] Build Time
- [x] Fast Startup
- [x] Performance and Efficiency
- [x] Concurrency Model
- [x] State typing and compilation


### Go Pro
- [x] Staically typed
- [x] Fast run time
- [x] Compiled
- [x] Fast Compiled time
- [x] Supports concurrency through goroutines and channel.
- [x] Has automatic garbage collection
- [x] Does not support classes and objects
- [x] Does not supports inheritance
### Commands

`pkg`
`bin`
`src`

`go --help`
`bug` - open default browser to report new bug
`build` compile package and dependencies
`clean` remove object files and cached files
`doc` show documentation for package or symbol
`env` print go environment information
`fix` update packages to use new APIs
`fmt` gofmt (reformat) package resources
`generate` generate Go files by processing source
`get` add dependencies to current module and install them
`install` install packages and dependencies
`list` list packages or modules
`mod` module maintenance
`work` workspace maintenance
`run` compile and run Go program
`test` test package
`tool` run specified go tool
`version` print Go version
`vet` report likely mistakes in packages

### Keywords

```go
package
break
default
func
interface
select
case
defer
go
map
delete
struct
chan
if
else
goto
package
switch
const
var
for
fallthrough
range
type
continue
import
return



```


#### first.go

```go
package main
import "fmt"
func main()  {
  fmt.Println("Hello Golang")
}
```

fmt.Println("Hello World!") is a statement.

In Go, statements are separated by ending a line (hitting the Enter key) or by a semicolon `;`.

Hitting the Enter key adds `;` to the end of the line implicitly (does not show up in the source code).

> The left curly bracket `{` cannot come at the start of a line.

```go
package main
import ("fmt")

func main()//error
{
  fmt.Println("Hello World!")
}
```

way1 - syntax :- var variablename type = value

way2 - with the := sign , variablename := value

> Note: In this case, the type of the variable is inferred from the value (means that the compiler decides the type of the variable, based on the value).

> Note: It is not possible to declare a variable using :=, without assigning a value to it.

### var vs :=

var --> used inside or outside of function

:= --> only inside functions

var --> variable declaration and value assignment can done separately.

:= --> Variable declaration and value assignment **cannot be done separately** (must be done in the same line)

> Note: If you use the type keyword, it is only possible to declare one type of variable per line.
>
> If the type keyword is not specified, you can declare different types of variables in the same line:

```go
 var a3, b3 = 6, "Hello"
	c3, d3 := 7, "World!"
	fmt.Println("-----")

	fmt.Println(a3)//6
	fmt.Println(b3)// "Hello"
	fmt.Println(c3)//7
	fmt.Println(d3)//World
```

#### Multiple variable declarations can also be grouped together into a block for greater readability:

```go
func main() {
   var (
     a int
     b int = 1
     c string = "hello"
   )

  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
}
```

Multiple constants can be grouped together into a block for readability:

```go
const (
  A int = 1
  B = 3.14
  C = "Hi!"
)
```




### Types

````go
package main

// Builtin and custom types
// General types
// - Structs
// - Slices
// - Maps
// - arrays
// - Custom types


// note numbers:=[]int{}  === otherNumbers:=make([]int,0)


bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128```

### Constants

> The const keyword declares the variable as "constant", which means that it is unchangeable and read-only.

There are two types of constants:

- Typed constants
  const A int = 1
  Untyped constants
  const A = 1

- Multiple constants can be grouped together into a block for readability:

```go
const (
  A int = 1
  B = 3.14
  C = "Hi!"
)
````

### Maps

> map[KeyType]ValueType
> ` var m map[string] int`

- Map types are reference types, like pointers or slices,
  and so the value of m above is nil; it doesn’t point to an initialized map.
  A nil map behaves like an empty map when reading,
  but attempts to write to a nil map will cause a runtime panic;
  don’t do that.
  To initialize a map, use the built in make function:

` m := make(map[string]int)`

- The make function allocates and initializes a hash map data structure and returns a map value that points to it. The specifics of that data structure are an implementation detail of the runtime and are not specified by the language itself. In this article we will focus on the use of maps, not their implementation.

### Channel

- <- the data flows in the direction of the arrow.
- Like maps and slices, channels must be created before use.
- ch:=make(chan int)
- ch<-v // send v to channel ch
- v:=<-ch // receive from ch and assign value to v

```go


func sum(s []int, c chan int) {
	sum := 0
	for _, v := range s {
		sum += v
	}
	c <- sum // send sum to c
}

func main() {
	s := []int{7, 2, 8, -9, 4, 0}

	c := make(chan int)
	go sum(s[:len(s)/2], c)
	go sum(s[len(s)/2:], c)
	x, y := <-c, <-c // receive from c

	fmt.Println(x, y, x+y)
}

```
