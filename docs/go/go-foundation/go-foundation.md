

---

# Go Language Notes

### 5 Reasons to Choose Go (Golang)

1. **Build Time** – Fast build times due to its efficient compilation process.
2. **Fast Startup** – Instant start-up times, making it great for quick server responses.
3. **Performance and Efficiency** – Combines the efficiency of a statically typed, compiled language with the simplicity of dynamic languages.
4. **Concurrency Model** – Goroutines provide lightweight, easy-to-use concurrency.
5. **Strong Typing and Compilation** – Static typing and a strong type system ensure type safety and prevent many bugs during compile time.

### Why Go is Great (Go Pros)

- **Statically Typed** – Type checks during compile time, improving reliability.
- **Fast Run Time** – Compiled to machine code, providing near C-level performance.
- **Compiled Language** – Ensures faster performance and safety as the code runs directly on the hardware.
- **Fast Compilation** – Go has one of the fastest compilation times among modern languages.
- **Concurrency Support** – Through goroutines and channels, Go handles multiple tasks simultaneously.
- **Automatic Garbage Collection** – Simplifies memory management by cleaning up unused memory.
- **No Classes & Objects** – Object-oriented paradigms are simplified, no inheritance is used, focusing on composition over inheritance.

---

### Common Go Commands

Here are some frequently used Go commands:

- `pkg` – Package management.
- `bin` – Binary directory for compiled Go programs.
- `src` – Source directory for Go code.

Other important commands include:

- `go --help` – Show command options.
- `bug` – Opens a browser to report bugs.
- `build` – Compile the package and dependencies.
- `clean` – Remove object and cached files.
- `doc` – Show documentation for packages.
- `env` – Print Go environment information.
- `fix` – Update packages to use new APIs.
- `fmt` – Format Go code (automatically adjusts indentation, spacing).
- `generate` – Generate Go files based on source code.
- `get` – Add and install dependencies.
- `install` – Install package dependencies.
- `list` – List packages or modules.
- `mod` – Manage Go modules (dependencies).
- `run` – Compile and run Go program.
- `test` – Run unit tests for packages.
- `version` – Print Go version.
- `vet` – Report suspicious constructs that could be bugs.

---

### Go Keywords

Go language reserves the following keywords:

```go
package, break, default, func, interface, select, 
case, defer, go, map, delete, struct, 
chan, if, else, goto, package, switch, 
const, var, for, fallthrough, range, type, 
continue, import, return
```

---

### Writing Your First Go Program

Example: `first.go`

```go
package main
import "fmt"

func main() {
    fmt.Println("Hello Golang")
}
```

**Explanation:**

- **fmt.Println** – This prints the output. In this case, it prints "Hello Golang".
- Statements in Go are separated by either pressing "Enter" or by using a semicolon (`;`). However, Go automatically adds semicolons when you hit "Enter".

> **Note:** The `{` must be on the same line as the function declaration. For example:

```go
func main() // error if `{` is on a new line
{
  fmt.Println("Hello Golang")
}
```

---

### Variable Declaration in Go

Go provides two ways to declare variables:

1. **Using `var`**:
    ```go
    var variablename type = value
    ```
   - Used inside or outside functions.
   - Declaration and assignment can be done separately.

2. **Using `:=`**:
    ```go
    variablename := value
    ```
   - Used only inside functions.
   - Declaration and assignment **must** be done on the same line.

**Example:**

```go
var a3, b3 = 6, "Hello"
c3, d3 := 7, "World!"
fmt.Println(a3, b3, c3, d3)
```

---

### Grouped Variable Declarations

Variables can also be declared together for better readability:

```go
func main() {
   var (
     a int
     b int = 1
     c string = "hello"
   )
   fmt.Println(a, b, c)
}
```

Similarly, constants can also be grouped together:

```go
const (
  A int = 1
  B = 3.14
  C = "Hi!"
)
```

---

### Data Types in Go

Go supports several built-in types:

- **Basic Types**: `int`, `float64`, `string`, `bool`
- **Complex Types**: `array`, `struct`, `map`, `slice`
- **Type Aliases**:
  - `byte` – Alias for `uint8`
  - `rune` – Alias for `int32`, representing Unicode code points.

---

### Go Constants

Constants in Go are immutable (cannot be changed once assigned). There are two types of constants:

1. **Typed Constants**:
    ```go
    const A int = 1
    ```

2. **Untyped Constants**:
    ```go
    const A = 1
    ```

Constants can also be grouped together:

```go
const (
  A int = 1
  B = 3.14
  C = "Hi!"
)
```

---

### Maps in Go

Maps in Go are used to store key-value pairs:

```go
var m map[string]int
```

- A map must be initialized using `make()` before adding values.
  ```go
  m := make(map[string]int)
  ```
- Maps behave like slices or pointers, meaning a nil map cannot be written to but can be read from.

---

### Channels in Go

Go provides **channels** to allow goroutines to communicate with each other.

- **Channel Declaration**: `ch := make(chan int)`
- To send data into a channel: `ch <- v`
- To receive data from a channel: `v := <- ch`

Example of using channels with goroutines:

```go
func sum(s []int, c chan int) {
    sum := 0
    for _, v := range s {
        sum += v
    }
    c <- sum // send sum to channel c
}

func main() {
    s := []int{7, 2, 8, -9, 4, 0}

    c := make(chan int)
    go sum(s[:len(s)/2], c)
    go sum(s[len(s)/2:], c)
    x, y := <-c, <-c // receive from channel

    fmt.Println(x, y, x+y)
}
```

**Explanation:**

- **Goroutines** – Lightweight threads that run in parallel.
- **Channels** – Used to pass data between goroutines safely.
