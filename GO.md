

### **2. Composite Data Types**
These types are built from other types.

#### **a. Array**
- **Fixed size**: All elements must be of the same type.
- **Example**:
  ```go
  var nums [5]int = [5]int{1, 2, 3, 4, 5}
  ```

#### **b. Slice**
- **Dynamic size**: Built on top of arrays, allows resizing.
- **Example**:
  ```go
  var nums []int = []int{1, 2, 3}
  nums = append(nums, 4) // Adds 4 to the slice
  ```

#### **c. Map**
- **Key-value pairs**: Keys and values must be of a single type.
- **Example**:
  ```go
  var person map[string]int = map[string]int{"age": 30, "height": 180}
  ```

#### **d. Struct**
- **Custom data types**: Groups fields together.
- **Example**:
  ```go
  type Person struct {
      Name string
      Age  int
  }

  var p = Person{Name: "Alice", Age: 25}
  ```

---

### **3. Reference Types**
These types involve references or pointers.

#### **a. Pointer**
- **Type**: `*T` (pointer to type `T`).
- **Example**:
  ```go
  var x int = 10
  var p *int = &x // Pointer to x
  ```

#### **b. Function**
- Functions are first-class citizens in Go.
- **Example**:
  ```go
  func add(a int, b int) int {
      return a + b
  }
  ```

---

### **4. Interface**
- **Type**: `interface{}`
- **Description**: Defines a set of methods that a type must implement.
- **Example**:
  ```go
  type Shape interface {
      Area() float64
  }
  ```

---

### **5. Special Types**
#### **a. nil**
- Represents an uninitialized value for reference types (e.g., pointers, maps, slices, etc.).
- **Example**:
  ```go
  var p *int = nil
  ```

# UNIT 3


### 1. **Functions in Go**
   - **Definition**: A function is a block of code that performs a specific task. It is reusable and can be called multiple times in a program.
   - **Syntax**:
     ```go
     func functionName() {
         // code
     }
     ```
   - **Example**: Creating a simple function called `wish`:
     ```go
     package main
     import "fmt"
     
     func wish() {
         fmt.Println("Good Morning")
     }
     
     func main() {
         wish()  // Function call
     }
     ```
   - **Output**:
     ```
     Good Morning
     ```

   - **Functions with Parameters**:
     ```go
     func addNumbers(num1 int, num2 int) {
         tot := num1 + num2
         fmt.Println("Total:", tot)
     }
     
     func main() {
         addNumbers(32, 18)  // Function call with arguments
     }
     ```
   - **Output**:
     ```
     Total: 50
     ```

   - **Functions with Return Values**:
     ```go
     func addNumbers(num1 int, num2 int) int {
         tot := num1 + num2
         return tot
     }
     
     func main() {
         result := addNumbers(32, 18)
         fmt.Println("Total:", result)
     }
     ```
   - **Output**:
     ```
     Total: 50
     ```

   - **Returning Multiple Values**:
     ```go
     func calculate(num1 int, num2 int) (int, int) {
         tot := num1 + num2
         difference := num1 - num2
         return tot, difference
     }
     
     func main() {
         tot, difference := calculate(32, 18)
         fmt.Println("Total:", tot, "Difference:", difference)
     }
     ```
   - **Output**:
     ```
     Total: 50 Difference: 14
     ```

---

### 2. **Variadic Functions**
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

### 3. **Closures in Go**
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

### 4. **Recursion in Go**
   - **Definition**: A function that calls itself.
   - **Example**: Simple recursive countdown.
     ```go
     func countDown(number int) {
         if number > 0 {
             fmt.Println(number)
             countDown(number - 1)
         } else {
             fmt.Println("Countdown Stops")
         }
     }
     
     func main() {
         countDown(3)
     }
     ```
   - **Output**:
     ```
     3
     2
     1
     Countdown Stops
     ```

   - **Calculating Sum Using Recursion**:
     ```go
     func sum(number int) int {
         if number == 0 {
             return 0
         } else {
             return number + sum(number-1)
         }
     }
     
     func main() {
         var num = 50
         var result = sum(num)
         fmt.Println("Sum:", result)
     }
     ```
   - **Output**:
     ```
     Sum: 1275
     ```

   - **Calculating Factorial Using Recursion**:
     ```go
     func factorial(num int) int {
         if num == 0 {
             return 1
         } else {
             return num * factorial(num-1)
         }
     }
     
     func main() {
         var number = 3
         var result = factorial(number)
         fmt.Println("The factorial of 3 is", result)
     }
     ```
   - **Output**:
     ```
     The factorial of 3 is 6
     ```

---

#### 5. **Defer, Panic, and Recover**
   - **Defer** is used to delay the execution of a function until the surrounding function returns.
   - **Panic** is used to terminate the program when something goes unexpectedly wrong.
   - **Recover** is used to regain control of a panicking goroutine.
   
     ```go
     func main() {
         defer fmt.Println("Three")
         fmt.Println("One")
         fmt.Println("Two")
     }
     ```
   - **Output**:
     ```
     One
     Two
     Three
     ```

   - **Panic**: Used to terminate the program immediately.
     ```go
     func main() {
         fmt.Println("Help! Something bad is happening.")
         panic("Ending the program")
     }
     ```
   - **Output**:
     ```
     Help! Something bad is happening.
     panic: Ending the program
     ```

   - **Recover**: Used to regain control of a panicking program.
     ```go
     func handlePanic() {
         if a := recover(); a != nil {
             fmt.Println("RECOVER", a)
         }
     }
     
     func division(num1, num2 int) {
         defer handlePanic()
         if num2 == 0 {
             panic("Cannot divide a number by zero")
         } else {
             result := num1 / num2
             fmt.Println("Result: ", result)
         }
     }
     
     func main() {
         division(4, 2)
         division(8, 0)
         division(2, 8)
     }
     ```
   - **Output**:
     ```
     Result: 2
     RECOVER Cannot divide a number by zero
     Result: 0
     ```

---

### 6. **Pointers**
   - **Definition**: Pointers are variables that store the memory address of another variable.
   - **Using `*` and `&`**:
     ```go
     var x int = 42
     var ptr *int = &x
     fmt.Println(*ptr)  // Output: 42
     ```
   - **Using `new`**:
     ```go
     type Person struct {
         Name string
         Age  int
     }
     
     func main() {
         p := new(Person)
         fmt.Printf("Name: %s, Age: %d\n", p.Name, p.Age)
     }
     ```
   - **Output**:
     ```
     Name: , Age: 0
     ```
---


### **Structs**

A **struct** (short for "structure") in Go is a composite data type that groups together fields under a single type. It’s similar to a class in other languages, but it does not support inheritance or methods directly within the struct itself. Structs allow you to create more complex data structures by grouping different pieces of data.

#### Declaring a Struct

Here’s the syntax for defining a struct:
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

#### Output
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
   ```go
   person := new(Person)  // Creates a pointer to a new Person struct
   person.Name = "Dave"
   person.Age = 35
   ```

---

#### Methods on Structs

You can define methods on structs, which allows for behavior associated with a struct.

```go
type Rectangle struct {
    Width, Height int
}

// Method to calculate area
func (r Rectangle) Area() int {
    return r.Width * r.Height
}

func main() {
    rect := Rectangle{Width: 10, Height: 5}
    fmt.Println("Area:", rect.Area())
}
```

#### Output
```
Area: 50
```

In this example, `Area()` is a method associated with the `Rectangle` struct. The receiver `(r Rectangle)` allows `Area()` to access the fields of `Rectangle`.

---

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

# unit 3

## Structs: 
- A struct is a composite data type that groups together zero or more values with different data types into a single entity. It is similar to a class in object-oriented programming languages.
- To define a struct, you use the type keyword followed by the struct's name and a set of fields 
enclosed in curly braces.
- **Syntax:** 
```go
type Person struct { 
Name string 
Age  int 
}
```
- **Initialization:** You can create an instance of a struct using a composite literal and then access its fields. 
```go
person := Person{Name: "Mrudhu”, Age: 30}
fmt.Println(person.Name, person.Age) // Output: Mrudhu 30 
 ```

### **Methods:**
-  A struct can have associated methods that operate on its instance. Methods are defined using 
the function keyword with a receiver argument.
```
func (p Person) SayHello() { 
fmt.Printf("Hello, my name is %s and I'm %d years old.\n", p.Name, p.Age) 
}
```

## Interfaces
- An interface is a collection of method signatures that define a contract. A type implements 
an interface if it provides definitions for all the methods declared in the interface. 
- **Syntax:**
-  To define an interface, you use the type keyword followed by the interface's name and a set of 
method signatures.
```
type Animal interface { 
    Speak() string 
    Move() string 
}
```
### **Implementation:** A type implicitly implements an interface if it implements all the methods declared 
in the interface. There is no explicit "implements" keyword like in some other languages. 
```go
type Dog struct{} 
func (d Dog) Speak() string { 
    return "Woof!" 
} 
func (d Dog) Move() string { 
    return "Running" 
} 
```
- **Polymorphism:**
-  Interfaces enable polymorphism, allowing you to create functions that can accept 
different types as long as they implement the interface. 
```go
func Describe(a Animal) { 
    fmt.Printf("The animal says %s and moves by %s.\n", a.Speak(), a.Move()) 
} 
func main() { 
    dog := Dog{} 
    cat := Cat{} 
    Describe(dog) // Output: The animal says Woof! and moves by Running. 
    Describe(cat) // Output: The animal says Meow! and moves by Jumping. 
}
```
- Structs and interfaces are essential concepts in Go programming, and they provide a foundation for 
writing clean, modular, and flexible code. Understanding how to define and use structs and interfaces 
is crucial for building efficient and maintainable Go programs.


 ## **function**
 function is a block of code that performs a specific task. Functions are one of the fundamental building blocks in Go, allowing you to group related operations and reuse code. Here's how you define a function in Go:

###  Syntax
```go
func functionName(parameters) returnType {
    // function body
}
```

### Example
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

 7. **Variadic Functions** 
- A variadic function is a function that accepts a variable number of arguments.  
- In Golang, it is possible to pass a varying number of arguments of the same type as referenced 
in the function signature. 
- To declare a variadic function, the type of the final parameter is preceded by an ellipsis, "...", 
which shows that the function may be called with any number of arguments of this type.
- This type of function is useful when you don't know the number of arguments you are passing 
to the function, the best example is built-in Println function of the fmt package which is a 
variadic function. 
- Select single argument from all arguments of variadic function 
 
- A variadic function accepts a variable number of arguments, which are treated as a slice.

   ```go
   func sum(numbers ...int) int {
       total := 0
       for _, num := range numbers {
           total += num
       }
       return total
   }
   ```


#### Passing multiple string arguments to a variadic function 

- which allows a function to 
accept a variable number of arguments of the same type. 
- the function variadicExample() is defined to accept a variadic parameter of 
type string. This means that it can accept any number of string arguments.  
- The main() function calls variadicExample() multiple times with different numbers of string 
arguments. 
- The first call to variadicExample() is made without any arguments, which is allowed since the 
function is defined to accept zero or more string arguments. 
- The second, third, and fourth calls pass different numbers of string arguments to 
variadicExample(). In each case, the function prints the contents of the s parameter using 
fmt.Println(). 

```go
package main 
import "fmt" 
func main() {  
variadicExample() 
variadicExample("red", "blue") 
variadicExample("red", "blue", "green") 
variadicExample("red", "blue", "green", "yellow") 
} 
func variadicExample(s ...string) { 
 fmt.Println(s) 
}
```
Output 
```
[] 
[red blue] 
[red blue green] 
[red blue green yellow]
```

8. **Go Closure** 
- Go closure is a nested function that allows us to access variables of the outer function even 
after the outer function is closed. 
- Nested Functions, Returning a function 
- **Nested function:** In Go, we can create a function inside another function. This is known as a nested 
function.  

``` go
package main 
import "fmt" 
// outer function 
func wish(name string) { 
// inner function 
var displayName = func() { 
fmt.Println("Hi", name) 
} 
// call inner function 
displayName() 
} 
func main() { 
// call outer function 
wish("Mrudhu")  // Hi Mrudhu 
}
```
In Go, **`defer`**, **`panic`**, and **`recover`** are mechanisms used for controlling the flow of execution, particularly for handling errors and resource cleanup.

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

**Output:**
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

**Output:**
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

**Output:**
```
Recovered from panic: Something went wrong!
Program continues after recovery.
```


