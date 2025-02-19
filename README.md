# Go Exercises

:information_source: &nbsp;This repo contains questions and exercises to learn and practice Golang

:bar_chart: &nbsp;There are currently **60** exercises and questions

- [Go Exercises](#go-exercises)
  - [Exercises](#exercises)
    - [Hello World](#hello-world)
    - [Strings](#strings)
    - [Arrays](#arrays)
    - [Loops](#loops)
    - [Functions](#functions)
  - [Questions](#questions)
    - [Go 101](#go-101)
    - [Variables and Data Types](#variables-and-data-types)
      - [Constants](#constants)
    - [Logical Operators](#logical-operators)
    - [Strings](#strings-1)
    - [Conditionals](#conditionals)
      - [Switch](#switch)
    - [User Input](#user-input)
    - [Arrays](#arrays-1)
    - [Loops](#loops-1)
    - [Functions](#functions-1)
      - [Defer](#defer)
    - [Packages](#packages)
  - [Projects](#projects)

## Exercises

### Hello World

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Hello World! | [Exercise](exercises/hello_world/exercise.md) | [Solution](exercises/hello_world/main.go) | |
| Variables & Constants | [Exercise](exercises/variables/exercise.md) | [Solution](exercises/variables/main.go) | |
| Arithmetic Operators | [Exercise](exercises/arithmetic_operators/exercise.md) | [Solution](exercises/arithmetic_operators/main.go) | |
| Data Types | [Exercise](exercises/data_types/exercise.md) | [Solution](exercises/data_types/solution.md) | |
| User Input | [Exercise](exercises/user_input/exercise.md) | [Solution](exercises/user_input/main.go) | |
| Packages | [Exercise](exercises/packages/exercise.md) | [Solution](exercises/packages/main.go) |
| Logical Operators | [Exercise](exercises/logical_operators/exercise.md) | [Solution](exercises/logical_operators/solution.md) |
| Conditionals | [Exercise](exercises/conditionals/exercise.md) | [Solution](exercises/conditionals/solution.md) | 
| Switch | [Exercise](exercises/switch/exercise.md) | [Solution](exercises/switch/solution.md) | 


### Strings

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Split Strings | [Exercise](exercises/split_strings/exercise.md) | [Solution](exercises/split_strings/solution.md) | |

### Arrays

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Arrays 101 | [Exercise](exercises/arrays_101/exercise.md) | [Solution](exercises/arrays_101/solution.md) | |
| Slices 101 | [Exercise](exercises/slices_101/exercise.md) | [Solution](exercises/slices_101/solution.md) | |

### Loops

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Loops 101 | [Exercise](exercises/loops_101/exercise.md) | [Solution](exercises/loops_101/main.go) | |
| Loops 102 | [Exercise](exercises/loops_102/exercise.md) | [Solution](exercises/loops_102/main.go) | |
| Continue | [Exercise](exercises/continue/exercise.md) | [Solution](exercises/continue/main.go) | |

### Functions

|Name|Exercise|Solution|Comments|
|--------|--------|------|----|
| Functions 101 | [Exercise](exercises/functions_101/exercise.md) | [Solution](exercises/functions_101/solution.md) | |
| Named Return Values | [Exercise](exercises/named_return_values/exercise.md) | [Solution](exercises/named_return_values/solution.md) | |


## Questions

### Go 101

<details>
<summary>What are some characteristics of the Go programming language?</summary><br><b>

  * Strong and static typing - the type of the variables can't be changed over time and they have to be defined at compile time
  * Simplicity
  * Fast compile times
  * Built-in concurrency
  * Garbage collected
  * Platform independent
  * Compile to standalone binary - anything you need to run your app will be compiled into one binary. Very useful for version management in run-time.
  * Big community
</b></details>

<details>
<summary>True or False?

  * In Go we can redeclare variables
  * Once a variable declared, we must use it
</summary>

* False
* True
</b></details>

<details>
<summary>What libraries of Go have you used?</summary><br><b>

This should be answered based on your usage but some examples are:

  * fmt - formatted I/O
  * math - random numbers, arithmetic operations like square, etc.
  * time - for any time related operation

</b></details>

<details>
<summary>Why some functions and packages in Go begin with a Capital letter?</summary><br><b>

Any exported variable, function, ... begins with a capital letter. In fact when using a package, you can use only the things the package exports for you and others to use.
</b></details>

### Variables and Data Types

<details>
<summary>Demonstrate short and regular variable declaration</summary><br><b>

```Go
package main

import "fmt"

func main() {
  x := 2
  var y int = 2

  fmt.Printf("x: %v. y: %v", x, y)
}
```
</b></details>

<details>
<summary>What is the result of the following program?

```
package main

import "fmt"

func main() {
    var userName
    userName = "user"
    fmt.Println(userName)
}
```
</summary><br><b>

Error. The type userName is not defined. It has to be declared or the value assignment should happen at declaration.

So both `var userName = user` and `var userName string` are valid.

</b></details>

<details>
<summary>What is the result of the following program?

```Go
package main
 
import "fmt"
 
func main() {
    var x uint
    x = -3
    // comment!
    fmt.Println(x)
}
```
</summary><br><b>

Error. When `x` is declared as `uint` it means you can't put any negative values. But because we did put a negative value (`-3`) it will fail to compile it.
</b></details>

<details>
<summary>What is the problem with the following block of code? How to fix it?

```
func main() {
    var x float32 = 13.5
    var y int
    y = x
}
```
</summary><br><b>
</b></details>

<details>
<summary>What is the difference between <code>var x int = 2</code> and <code>x := 2</code>?</summary><br><b>

The result is the same, a variable with the value 2.

With <code>var x int = 2</code> we are setting the variable type to integer, while with <code>x := 2</code> we are letting Go figure out by itself the type.
</b></details>

<details>
<summary>The following block of code tries to convert the integer 101 to a string but instead we get "e". Why is that? How to fix it?

```
package main

import "fmt"

func main() {
    var x int = 101
    var y string
    y = string(x)
    fmt.Println(y)
}
```
</summary><br><b>

It looks what unicode value is set at 101 and uses it for converting the integer to a string.
If you want to get "101" you should use the package "strconv" and replace <code>y = string(x)</code> with <code>y = strconv.Itoa(x)</code>
</b></details>

<details>
<summary>What would be the result of executing the following code:

```Go
package main

import "fmt"

x := 2

func main() {
    x = 3
    fmt.Println(x)
}
```
</summary><br><b>

It will fail with `expected declaration, found x` as outside of a function, every statement should start with a keyword (and short variable declarations won't work).
</b></details>

<details>
<summary>Demonstrate a block of variable declarations (at least 3 variables)</summary><br><b>

```Go
package main

import "fmt"

var (
  x bool   = false
  y int    = 0
  z string = "false"
)

func main() {
  fmt.Printf("The type of x: %T. The value of x: %v\n", x, x)
  fmt.Printf("The type of y: %T. The value of y: %v\n", y, y)
  fmt.Printf("The type of z: %T. The value of z: %v\n", y, y)
}
```
</b></details>

<details>
<summary>Demonstrate type conversion</summary><br><b>

```Go
package main

import "fmt"

func main() {
    var x int = 2
    fmt.Println(x)
    var y float32 = float32(x)                
    fmt.Println(y)
}
```
</b></details>

<details>
<summary>What are package level variables? What would be the reason to use them?</summary><br><b>

Package level variables are variables that defined at the package level instead of a specific function (like main for example).

If you have multiple functions in your package that use the same variables, it might make these variables available to the functions by defining them at the package level. This can be in the same file or any file under the same package.
For example:

```Go
package main

packageLevelVar := 0 

func main() {
  nonPackageLevelVar := 0
}
```

</b></details>

#### Constants 
<details>
<summary>What is wrong with the following code?:

```Go
package main

func main() {
    var x = 2
    var y = 3
    const someConst = x + y
}
```
</summary><br><b>
Constants in Go can only be declared using constant expressions.
But `x`, `y` and their sum is variable.
<br>
<code>const initializer x + y is not a constant</code>

</b></details>

<details>
<summary>What will be the result of executing the following code?

```Go
package main

import "fmt"

func main() {
  const X := 2
  fmt.Print(X)
}
```
</summary><br><b>

It won't run. Constants cannot be declared using `:=`.
</b></details>

<details>
<summary>What will be the result of executing the following code?

```Go
package main

import "fmt"

const (
    Const1 = 1 
    Const2 = 1 < 2 
    Const3 = 1 << 10                              
)

func main() {
    fmt.Println(Const1)
    fmt.Println(Const2)
    fmt.Println(Const3)
}
```
</summary><br><b>

1
true
1024

The 1024 result is because we shifted a 1 bit left 10 places.
</b></details>

### Logical Operators

<details>
<summary>What is the output of the following code?

```Go
package main

import "fmt"

func main() {
    x := 2017

    fmt.Println(x > 2022 && x < 3000)
    fmt.Println(x > 2000 && x < 3000)
    fmt.Println(x > 2000 && x&2 == 0)              
}
```
</summary><br><b>

```
false
true
false
```
</b></details>

<details>
<summary>What is the output of the following code?

```Go
package main

import "fmt"

func main() {
    x := 2017

    fmt.Println(x > 2022 || x < 3000)
    fmt.Println(x > 2000 || x < 3000)
    fmt.Println(x > 2000 || x&2 == 0)              
}
```
</summary><br><b>

```
true
true
true
```
</b></details>

<details>
<summary>What is the output of the following code?

```Go
package main
        
import "fmt"
        
func main() {
    x := true
        
    fmt.Println(x)
    fmt.Println(!x)
    fmt.Println(!x && x)
    fmt.Println(!x || x)                   
}
```
</summary><br><b>

```
true
false
false
true
```
</b></details>

### Strings

<details>
<summary>How to check if a string variable contains the character "o"?
</summary><br><b>

`containsO := strings.Contains(someVar, "o")`
</b></details>

### Conditionals

<details>
<summary>Define a variable with value of 5. Write a conditional to check if the value of the variable is bigger than 0 and if it is, print "It's bigger than 0!"</summary><br><b>

```Go
x := 5
if x > 0 {
  fmt.Print("It's bigger than  0!")
}
```
</b></details>

<details>
<summary>Define a variable with a random value. If its value bigger than 10 print "yay!". If it's smaller than 10, print "nay!"</summary><br><b>

```Go

rand.Seed(time.Now().UnixNano())
var x int = rand.Intn(100)
if x > 10 {
  fmt.Print("yay!")
} else {
  fmt.Print("nay!")
}
```
</b></details>

<details>
<summary>What the following code does?

```Go
package main
  
import ( 
    "fmt"
    "math/rand"
    "time"
)

func main() {
    rand.Seed(time.Now().UnixNano())
    if randNum := rand.Intn(100); randNum%2 == 0 {
        fmt.Print("Bingo!")               
    } else {
        fmt.Print(randNum)
    }       
}
```
</summary><br><b>

Defines a variable with random value between 0 and 100. If the random value is even, prints "Bingo!" otherwise, prints the random value itself.
</b></details>

#### Switch

<details>
<summary>Write a switch case to check what day of the week it is. If Sunday print "Here we go". If Monday print "We have just started". For any other day print the day.
</summary><br><b>

```Go
package main

import (
	"fmt"
	"time"
)

func main() {

    today := time.Now().Weekday().String()

    switch today {
    case "Sunday":
      fmt.Println("Here we go")
    case "Monday":
      fmt.Println("We have just started")
    default:
      fmt.Println(today)
	}
}
```

</b></details>

### User Input

<details>
<summary>Fix the following program to get an input from the user regarding his name and print it

```Go
var name string

fmt.Scan(name)

fmt.Println(name)
```
</summary><br><b>

```Go
var name string

fmt.Scan(&name)

fmt.Println(name)
```

</b></details>

<details>
<summary>Why when asking for user input, we have to specify &?</summary><br><b>

Because we want to reference the memory address of the variable, this is where the user input will be stored.
</b></details>

<details>
<summary>What do we print here?

```Go
var age int = 3

fmt.Println(age)
fmt.Println(&age)
```
</summary><br><b>

The value of `age` variable and then the memory location of `age` variable

</b></details>

### Arrays

<details>
<summary>Define an array of the following colors: red, green and blue</summary><br><b>

```Go
var rgb = [3]string{"red", "green", "blue"}
```
</b></details>

<details>
<summary>You defined the following array and printed it. What was the output? <code>var numbers = [10]int{}</code></summary><br><b>

```Go
[0 0 0 0 0 0 0 0 0 0]
```
</b></details>

### Loops

<details>
<summary>Define a simple for loop with following components:

* variable `i` initialized to 0
* expression where the variable should be smaller than 50
* at the end of each iteration the variable value should be incremented by 1
* In the loop itself, the value of variable `i` should be added to a variable called `sum` (initialize the variable before the loop with value of 0)
</summary><br><b>

```Go
sum := 0
for i := 0; i < 50; i++ {
    sum += i
}
```
</b></details>

<details>
<summary>Implement infinite loop</summary><br><b>

```Go
for {
    fmt.Print("forever!")
}
```
</b></details>

<details>
<summary>What's the difference between the following two loops?

```Go
for {
    fmt.Print("forever!")
}

for true {
    fmt.Print("forever!")
}
```
</summary><br><b>

From result perspective, there is no difference. Both are infinite loops.
</b></details>

### Functions

<details>
<summary>Define a function that prints "Hello World"</summary><br><b>

```Go
func PrintHelloWorld() {
    fmt.Println("Hello World")
}
```
</b></details>

<details>
<summary>What the following code does?

```Go
func add(x int, y int) int {
    return x + y
}
```
</summary><br><b>

add is a function that takes two parameters (two integers) and returns their sum.
</b></details>


<details>
<summary>Which of the following functions will work just fine?

```Go
func add(x int, y int) int {
    return x + y
}

func add(x, y int) int {
    return x + y
}
```
</summary><br><b>

Both. If two or more parameters share the same type, you can specify it only once.
</b></details>

<details>
<summary>True or False? A function in Go can return either zero or one values, but not more than that</summary><br><b>

False. A fucntion in Go can return multiple values
</b></details>

<details>
<summary>Write code that will execute the following function in a valid way

```Go
func swap(x, y string) (string, string) {
    return y, x
}
```
</summary><br><b>

```Go
x, y = swap("and roll", "rock")
fmt.Println(a, b)
```

</b></details>

<details>
<summary>What is the result of the following code?

```Go
func process(num int) (x int) {
    x = num + 10
    var z = num - x
    x = z + x
    return
}

func main() {
  fmt.Println(process(10))
}
```
</summary><br><b>

10
</b></details>

#### Defer

<details>
<summary>What will be the output of the following code? Why?

```Go
package main

import "fmt"

func main() {
    defer fmt.Println("1")

    fmt,Println("2")
}
```
</summary><br><b>

```
2
1
```

2 is printed before 1 due to the defer statement. The `defer` statement defers the execution of the function (`fmt.Println("1")`) until the surrounding fucntion (which is `main()`) returns.
</b></details>

<details><summary>True or False? The arguments of a deferred functions are evaluated but the function itself isn't called until the surrounding function returns</summary><br><b>

True.
</b></details>

<details>
<summary>What will be the output of the following code? Why?

```Go
package main

import "fmt"

func main() {
    fmt.Println("100")

    for i := 0; i < 10; i++ {
      defer fmt.Println(i)
    }

    fmt.Println("200")
  }
```
</summary><br><b>

```
100
200
9
8
7
6
5
4
3
2
1
0
```

Deferred functions are executed in a last-in-first-out order, this is why it prints it from 9 to 0 instead of from 0 to 9.
</b></details>

### Packages

<details>
<summary>How do you export a variable or a function in Go for other packages to use?
</summary><br><b>

Capitalize the first letter.
</b></details>

## Projects

|Name|Description|Solution|Comments|
|--------|--------|------|----|
| Simple Web Server | [Description](projects/simple_web_server/README.md) | [Solution](projects/simple_web_server/main.go) | |
