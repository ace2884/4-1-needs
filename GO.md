



# UNIT 3


## **Functions in Go**
  -  A function is a block of code that performs a specific task. It is reusable and can be called multiple times in a program.
- function is a block of code that performs a specific task. Functions are one of the fundamental building blocks in Go, allowing you to group related operations and reuse code. 
 - **Syntax**
```go
func functionName(parameters) returnType {
    // function body
}
```

- **Example**
```go
package main

import "fmt"

// Simple function that takes no parameters and returns no value
func sayHello() {
    fmt.Println("Hello, World!")
}

func main() {
    sayHello()  // Calling the function
}
```

### Types of Functions in Go

1. **Functions with No Parameters and No Return Values**  
   These functions do not take any input and do not return any result.

   ```go
   func printMessage() {
       fmt.Println("This is a message.")
   }
   ```

2. **Functions with Parameters and No Return Values**  
   These functions accept one or more parameters but do not return anything.

   ```go
   func greet(name string) {
       fmt.Println("Hello, " + name)
   }
   ```

3. **Functions with Return Values**  
   These functions return a result after performing operations. You specify the return type after the parameter list.

   ```go
   func add(a int, b int) int {
       return a + b
   }
   ```

4. **Functions with Multiple Return Values**  
   Go allows a function to return more than one value, which is useful for error handling or returning complex results.

   ```go
   func divide(a, b int) (int, int) {
       if b == 0 {
           return 0, 0 // error case
       }
       return a / b, a % b // returns quotient and remainder
   }
   ```

5. **Anonymous Functions**  
   These are functions without a name, often used as arguments to other functions or for quick tasks.

   ```go
   func() {
       fmt.Println("This is an anonymous function.")
   }()
   ```

  

6. **Methods (associated with types)**  
   A method is a function that is associated with a specific type (usually a struct). It can operate on that type's fields.

   ```go
   type Circle struct {
       Radius float64
   }

   func (c Circle) area() float64 {
       return 3.14 * c.Radius * c.Radius
   }
   ```

##  **Variadic Functions**
   - **Definition**: A function that accepts a variable number of arguments.
   - **Syntax**: Use `...` before the data type of the parameter.
   - **Example**: Using a variadic function to handle multiple arguments.
     ```go
     package main
     import "fmt"
     
     func variadicExample(s ...string) {
         fmt.Println(s[0])  // Accessing first element
         fmt.Println(s[3])  // Accessing fourth element
     }
     
     func main() {
         variadicExample("red", "blue", "green", "yellow")
     }
     ```
   - **Output**:
     ```
     red
     yellow
     ```

   - **Passing Different Numbers of Arguments**:
     ```go
     func variadicExample(s ...string) {
         fmt.Println(s)
     }
     
     func main() {
         variadicExample()
         variadicExample("red", "blue")
         variadicExample("red", "blue", "green", "yellow")
     }
     ```
   - **Output**:
     ```
     []
     [red blue]
     [red blue green yellow]
     ```

---

## **Closures in Go**
   - **Definition**: A closure is a nested function that captures and uses variables from the scope in which it was defined.
   - **Example**: Nested function accessing an outer variable.
     ```go
     package main
     import "fmt"
     
     func wish(name string) {
         var displayName = func() {
             fmt.Println("Hi", name)
         }
         displayName()  // Calling the inner function
     }
     
     func main() {
         wish("Mrudhu")
     }
     ```
   - **Output**:
     ```
     Hi Mrudhu
     ```

   - **Returning a Function**:
     ```go
     func wish() func() {
         return func() {
             fmt.Println("Hi Mrudhu")
         }
     }
     
     func main() {
         g1 := wish()
         g1()  // Executing the returned function
     }
     ```
   - **Output**:
     ```
     Hi Mrudhu
     ```

   - **Example of a Closure that Maintains State**:
     ```go
     func calculate() func() int {
         num := 1
         return func() int {
             num = num + 2
             return num
         }
     }
     
     func main() {
         odd := calculate()
         fmt.Println(odd())
         fmt.Println(odd())
         fmt.Println(odd())
         odd2 := calculate()
         fmt.Println(odd2())
     }
     ```
   - **Output**:
     ```
     3
     5
     7
     3
     ```

---

## **Recursion in Go**
Recursion in Go is a programming concept where a function calls itself directly or indirectly, enabling solutions for problems that can be broken into smaller, similar subproblems. 

### Features of Recursion in Go
1. **Recursive Function**: A function is recursive when it calls itself within its definition.
2. **Base Case**: Essential to stop recursion and prevent infinite loops.
3. **Recursive Case**: Defines the conditions where the function calls itself.
4. **Memory Usage**: Each recursive call adds a new layer to the call stack.

- **Example:** Simple Recursion in Go

```go
package main

import "fmt"

// Recursive function to calculate factorial
func factorial(num int) int {
    if num == 0 {
        return 1 // Base case
    }
    return num * factorial(num-1) // Recursive case
}

func main() {
    number := 5
    result := factorial(number)
    fmt.Printf("The factorial of %d is %d\n", number, result)
}
```

- **Output**
```
The factorial of 5 is 120
```
- **Recursive Function with a Conditional Statement**
To avoid infinite recursion, use a conditional statement to manage the recursive process. For example, calculating the sum of numbers up to a given number:

```go
package main

import "fmt"

// Recursive function to calculate sum
func sum(number int) int {
    if number == 0 {
        return 0 // Base case
    }
    return number + sum(number-1) // Recursive case
}

func main() {
    var num = 10
    result := sum(num)
    fmt.Println("Sum:", result)
}
```

- **Output**
```
Sum: 55
```

## Defer , Panic ,Recover

### 1. `defer`

The **`defer`** statement schedules a function to be executed **after** the surrounding function has completed, regardless of whether it returns normally or through a panic. It is often used for cleanup tasks like closing files, releasing resources, or unlocking mutexes.

- **Key Point**: The deferred function is executed **last-in, first-out (LIFO)** order. That means the last `defer` function will execute first when the surrounding function exits.

#### Example of `defer`:

```go
package main

import "fmt"

func example() {
    defer fmt.Println("This is deferred!") // This will execute after example() returns.
    fmt.Println("Hello, World!")
}

func main() {
    example()
}
```

- **Output:**
```
Hello, World!
This is deferred!
```


### 2. `panic`

**`panic`** is used to stop the normal execution of a function and begin unwinding the stack. When a `panic` occurs, the program stops executing the current function and begins executing any deferred functions in the reverse order they were deferred. If there is no recovery from the panic, the program will terminate.

- **Key Point**: Use `panic` for situations that are irrecoverable, like unexpected errors or conditions that should never happen.

#### Example of `panic`:

```go
package main

import "fmt"

func causePanic() {
    panic("Something went wrong!")
}

func main() {
    causePanic() // This will panic and terminate the program.
}
```

- **Output:**
```
panic: Something went wrong!

goroutine 1 [running]:
main.causePanic()
        /path/to/your/file.go:6 +0x59
main.main()
        /path/to/your/file.go:9 +0x20
```

### 3. `recover`

**`recover`** is used to regain control of a panicking function and prevent the program from terminating. `recover` only works if called inside a deferred function. If the function is panicking, `recover` will capture the panic and return the value passed to `panic()`. If there is no panic, `recover` returns `nil`.

- **Key Point**: `recover` can only be used inside a deferred function.

#### Example of `recover`:

```go
package main

import "fmt"

func safeCall() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from panic:", r)
        }
    }()
    panic("Something went wrong!")
}

func main() {
    safeCall() // This will panic, but the panic is recovered.
    fmt.Println("Program continues after recovery.")
}
```

- **Output:**
```
Recovered from panic: Something went wrong!
Program continues after recovery.
```




### **Structs**

A **struct** (short for "structure") in Go is a composite data type that groups together fields under a single type. It’s similar to a class in other languages, but it does not support inheritance or methods directly within the struct itself. Structs allow you to create more complex data structures by grouping different pieces of data.

#### Declaring a Struct
```go
type StructName struct {
    field1 fieldType1
    field2 fieldType2
    // more fields
}
```

#### Example

```go
type Person struct {
    Name string
    Age  int
    Email string
}

func main() {
    // Creating an instance of the struct
    person1 := Person{Name: "Alice", Age: 30, Email: "alice@example.com"}
    
    // Accessing struct fields
    fmt.Println("Name:", person1.Name)
    fmt.Println("Age:", person1.Age)
    fmt.Println("Email:", person1.Email)
}
```

- **Output**
```
Name: Alice
Age: 30
Email: alice@example.com
```

#### Creating and Initializing Structs

1. **With Field Names**:
   ```go
   person := Person{Name: "Bob", Age: 25}
   ```
   Fields not specified are automatically set to their zero values (e.g., `""` for strings, `0` for integers).

2. **Without Field Names**:
   ```go
   person := Person{"Charlie", 40, "charlie@example.com"}
   ```
   This is called **positional initialization** but can be less clear, especially if there are many fields.

3. **Using the `new` Keyword**:
  - The `new` function allocates memory for a struct and returns a pointer initialized with zero values.
   ```go
   person := new(Person)  // Creates a pointer to a new Person struct
   person.Name = "Dave"
   person.Age = 35
   ```

5. **Zero Value Initialization**
When a struct is created without explicit initialization, all its fields are set to their **zero values**:
- Numeric types: `0`
- Strings: `""` (empty string)
- Booleans: `false`
- Pointers, interfaces, slices, maps, channels: `nil`

```go
p := Person{}
fmt.Println(p) // Output: {"" 0}
```

6. **Using Pointers**
The `&` operator is used to create a pointer to the struct.

```go
p := &Person{Name: "Alice", Age: 25}
fmt.Println(p) // Output: &{Alice 25}
```


### **Interfaces**

An **interface** in Go defines a set of method signatures (i.e., behavior) that any type can implement. It enables polymorphism in Go, meaning that different types can be used interchangeably as long as they implement the interface.

#### Declaring an Interface

```go
type InterfaceName interface {
    MethodName1(param1 paramType1) returnType1
    MethodName2(param2 paramType2) returnType2
}
```

#### Example

```go
type Describer interface {
    Describe() string
}
```

Here, any type that has a `Describe` method with the specified signature will implicitly implement the `Describer` interface.

#### Implementing an Interface

Let's say we have a `Person` and a `Car` struct, and we want both to implement the `Describer` interface.

```go
type Person struct {
    Name string
    Age  int
}

func (p Person) Describe() string {
    return fmt.Sprintf("Person: %s, Age: %d", p.Name, p.Age)
}

type Car struct {
    Make  string
    Model string
}

func (c Car) Describe() string {
    return fmt.Sprintf("Car: %s %s", c.Make, c.Model)
}

func main() {
    var d Describer

    p := Person{Name: "Alice", Age: 30}
    c := Car{Make: "Toyota", Model: "Corolla"}

    d = p
    fmt.Println(d.Describe())  // Output: Person: Alice, Age: 30

    d = c
    fmt.Println(d.Describe())  // Output: Car: Toyota Corolla
}
```

In this example:
1. Both `Person` and `Car` structs have a `Describe()` method.
2. Since `Describe()` matches the method signature of the `Describer` interface, both `Person` and `Car` automatically implement `Describer`.
3. We can assign instances of `Person` and `Car` to the variable `d` of type `Describer`, demonstrating polymorphism.

---

### **Interfaces as Parameters**

Interfaces allow for flexibility in function parameters. By accepting an interface as a parameter, a function can accept any type that implements that interface.

```go
func PrintDescription(d Describer) {
    fmt.Println(d.Describe())
}

func main() {
    p := Person{Name: "Bob", Age: 25}
    c := Car{Make: "Ford", Model: "Mustang"}

    PrintDescription(p)  // Person: Bob, Age: 25
    PrintDescription(c)  // Car: Ford Mustang
}
```

---

### **Empty Interface**

The **empty interface** `interface{}` can hold values of any type because every type in Go implements at least zero methods. It’s commonly used when the function needs to handle unknown or dynamic types.

#### Example:
```go
func PrintAnything(i interface{}) {
    fmt.Println(i)
}

func main() {
    PrintAnything("Hello")
    PrintAnything(123)
    PrintAnything(true)
}
```

---

### **Type Assertion**

Type assertion allows you to retrieve the dynamic type of a value stored in an interface variable.

```go
var i interface{} = "hello"

// Type assertion
s, ok := i.(string)
if ok {
    fmt.Println("String:", s)
} else {
    fmt.Println("Not a string")
}
```

#### Output
```
String: hello
```

The `ok` value in `s, ok := i.(string)` is a boolean that indicates whether the assertion succeeded.

---

### **Interface Composition**

Go allows you to compose interfaces, meaning you can build new interfaces by combining existing ones.

```go
type Reader interface {
    Read(p []byte) (n int, err error)
}

type Writer interface {
    Write(p []byte) (n int, err error)
}

type ReadWriter interface {
    Reader
    Writer
}
```

In this example, `ReadWriter` includes both the `Reader` and `Writer` interfaces. Any type that implements both `Read` and `Write` methods will also implement `ReadWriter`.

---






