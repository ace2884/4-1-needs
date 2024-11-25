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

## defer , panic ,recover

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

---
# unit 5

## comparison of **Concurrency** and **Parallelism**:

| **Aspect**                | **Concurrency**                                            | **Parallelism**                                         |
|---------------------------|------------------------------------------------------------|--------------------------------------------------------|
| **Definition**            | Concurrency refers to the ability to manage multiple tasks simultaneously, but not necessarily at the same time. | Parallelism is the execution of multiple tasks at the exact same time, often on multiple processors or cores. |
| **Execution Model**       | Tasks start, run, and complete in overlapping time periods, but not necessarily simultaneously. | Tasks are executed simultaneously on different processing units. |
| **Analogy**               | Managing multiple tasks like switching between conversations with different people. | Doing multiple tasks at the exact same moment, like having multiple people working in parallel. |
| **Hardware Requirement**  | Can be achieved on a single-core processor by time slicing. | Requires multi-core or multiple processors for true simultaneous execution. |
| **Programming Focus**     | Focuses on the structure of the program and the ability to switch tasks efficiently. | Focuses on the execution speed by distributing tasks across multiple processors. |
| **Use Case Example**      | A web server handling multiple client requests concurrently, but processing them one at a time. | A system processing large amounts of data simultaneously using distributed computing. |
| **Example in Go**         | Using goroutines to handle tasks concurrently.             | Using goroutines in conjunction with multiple CPU cores to execute tasks in parallel. |
| **Goal**                  | Increase responsiveness and utilize resources efficiently. | Increase computational power and reduce the execution time of heavy tasks. |
| **Interdependence**       | Concurrency can occur without parallelism (e.g., on a single-core CPU). | Parallelism requires concurrency but is specifically about simultaneous execution. |



---
## Parsing Command-Line Arguments: 
Parsing command-line arguments is a common task in many programs, and Go provides the flag 
package to make this process straightforward. 
### 1. **Importing the Required Package:** 
Begin by importing the flag package.
```   
import ( 
"flag" 
"fmt" 
)
```
### 2. **Define Flags:** 
Flags can be of various data types including string, int, bool, etc. 
```
var name = flag.String("name", "Guest", "Your name") 
var age = flag.Int("age", 25, "Your age") 
var isMember = flag.Bool("member", false, "Are you a member?")
```
The flag.AAA functions (e.g., flag.String, flag.Int) return a pointer to the variable type. The 
functions take three arguments.
The flag name as it will appear on the command line (name in this case). 
The default value. 
### 3. **Parse the Flags:**
Once the flags have been defined, you can parse the command line into the 
defined flags using the ```flag.Parse()``` method. 

### 4. **Accessing Flag Values:**
Since the flag functions return pointers, you must dereference them to 
access the underlying value.
```
fmt.Printf("Hello, %s!\n", *name) 
fmt.Printf("You are %d years old.\n", *age) 
fmt.Printf("Member status: %v\n", *isMember)
```

### 5.**Custom Flags:** 
If you have a custom type you want to use as a flag, you can define your own flag type by 
implementing the flag.Value interface, which requires Set(string) error and String() string 
methods. 

#### Example:  
```go
package main 
import ( 
"flag" 
"fmt" 
) 
func main() { 
name := flag.String("name", "Guest", "Your name") 
age := flag.Int("age", 25, "Your age") 
isMember := flag.Bool("member", false, "Are you a member?") 
flag.Parse() 
fmt.Printf("Hello, %s!\n", *name) 
fmt.Printf("You are %d years old.\n", *age) 
fmt.Printf("Member status: %v\n", *isMember) 
}
```
##### cmd
```
go run main.go -name=John -age=30 -member=true
```
##### output:
```
Hello, John! 
You are 30 years old. 
Member status: true
```
---


## **Concurrency in Go**
- Go has built-in support for concurrency through goroutines and channels. Concurrency means multiple tasks can run in overlapping time periods, rather than sequentially.

  ### **Goroutines**
  - Goroutines are lightweight, managed threads that allow for concurrent execution in Go. They are much more efficient in terms of memory and processing compared to traditional operating system threads.
   - **How to Start a Goroutine**: Simply prefix the function call with the `go` keyword.
   - **Syntax**:
     ```go
     go functionName(parameters)
     ```
   - **Example**:
     ```go
     package main
     import (
         "fmt"
         "time"
     )

     func printNumbers() {
         for i := 1; i <= 5; i++ {
             fmt.Println(i)
             time.Sleep(500 * time.Millisecond)
         }
     }

     func main() {
         go printNumbers()  // Starts printNumbers as a goroutine
         fmt.Println("Main function continues to run")

         // Give the goroutine some time to finish
         time.Sleep(3 * time.Second)
     }
     ```


  #### **Characteristics of Goroutines**:
  
   - **Efficient**: A single Go program can run thousands of goroutines simultaneously.
   - **Non-blocking**: Starting a goroutine does not block the execution of the main function.
   - **Managed by Go Runtime**: The Go runtime schedules and manages goroutines, making them efficient and easy to use compared to traditional threads.
   - **Lightweight:** Goroutines are more memory efficient than traditional threads. They start with a smaller stack that can grow/shrink as needed, typically starting with just a few 
     kilobytes of memory. 
   - **Concurrent, not necessarily parallel:** While goroutines make concurrent programming simple, it doesn't guarantee parallel execution. However, if your machine has multiple CPU cores 
     and you've set the GOMAXPROCS environment variable (or runtime parameter) to be more than 1, then the Go runtime will utilize those cores and run goroutines in parallel where possible. 



### **Channels**
   -  Channels provide a way for goroutines to communicate and synchronize by passing data. They are a crucial feature in Go for sharing information safely between goroutines.
    - **Syntax**:
   - **Creating a Channel**:
     ```go
     ch := make(chan dataType)
     ```
   - **Sending Data into a Channel**:
     ```go
     ch <- value
     ```
   - **Receiving Data from a Channel**:
     ```go
     value := <-ch
     ```

#### **Example with Channels**:
   ```go
   package main
   import "fmt"

   func sum(a int, b int, ch chan int) {
       result := a + b
       ch <- result  // Send the result into the channel
   }

   func main() {
       ch := make(chan int)
       go sum(3, 4, ch)  // Start sum as a goroutine

       result := <-ch  // Receive the result from the channel
       fmt.Println("Sum:", result)  // Output: Sum: 7
   }
   ```
 
    
---



### **Synchronization Using Channels**
   - **Definition**: Channels in Go provide a way to synchronize goroutines and safely pass data.
   - **Syntax**:
     ```go
     ch := make(chan int)  // Creating a channel
     ch <- value           // Sending value into channel
     value := <-ch         // Receiving value from channel
     ```
   - **Example**:
     ```go
     package main 
     import ( "fmt" )  
       func sendData(ch chan int) { 
         for i := 0; i < 5; i++ {  
         ch <- i } close(ch)  
         } 
          func main() {  
         dataChan := make(chan int)  
         go sendData(dataChan)
         for num := range dataChan {  
        fmt.Println(num) } 
        }   
      ```
- **Explanation**:In this example, a goroutine is sending data on a channel, and the main goroutine is reading from the same channel. The loop in the main function will continue reading from the channel until it's closed in the sendData function.
     
- **Points to remember:** 
- Always synchronize access to shared memory/resources to prevent race conditions. 
- Goroutines are cheap, but they are not free. You shouldn't spawn an unbounded number 
of them. Always be aware of the resources you're utilizing. 
- Using the sync package and its primitives (sync.WaitGroup, sync.Mutex, etc.) can help 
manage and coordinate the execution of goroutines.

---

### **Buffered vs. Unbuffered Channels**
1. **Unbuffered Channels**: The sender is blocked until a receiver is ready to receive the data, and vice versa.
   - **Example**:
     ```go
     ch := make(chan int)  // Unbuffered channel
     ```

2. **Buffered Channels**: The sender is only blocked when the buffer is full, and the receiver is blocked when the buffer is empty.
   - **Syntax**:
     ```go
     ch := make(chan int, 3)  // Buffered channel with a capacity of 3
     ```
     
   - **Example**:
     ```go
     package main
     import "fmt"

     func main() {
         ch := make(chan int, 2)  // Buffered channel

         ch <- 1  // Send data into the channel
         ch <- 2

         fmt.Println(<-ch)  // Receive data from the channel
         fmt.Println(<-ch)
     }
     ```
   - **Explanation**: The buffered channel allows sending two integers without blocking, because its capacity is 2.

Here is a clear comparison between **Buffered** and **Unbuffered Channels** in Go presented in a tabular format:

| **Aspect**                 | **Buffered Channels**                                 | **Unbuffered Channels**                                |
|----------------------------|-------------------------------------------------------|-------------------------------------------------------|
| **Definition**             | Channels with a fixed capacity for storing values.    | Channels with no internal capacity to store values.   |
| **Blocking Behavior**      | Sender only blocks when the buffer is full.           | Sender blocks until a receiver is ready.              |
|                            | Receiver blocks only when the buffer is empty.        | Receiver blocks until data is available.              |
| **Creation Syntax**        | `ch := make(chan int, capacity)`                      | `ch := make(chan int)`                                |
| **Example**                | `ch := make(chan int, 2)` (buffered with capacity 2) | `ch := make(chan int)` (unbuffered)                   |
| **Use Case**               | Useful when you want to temporarily store data.       | Suitable for immediate communication and synchronization. |
| **Efficiency**             | More efficient when frequent data bursts occur.       | Simpler and more efficient when immediate processing is required. |
| **Typical Applications**   | Queuing tasks, managing a pool of resources.          | Synchronizing goroutines or handshaking processes.    |
| **Handling Data**          | Can handle multiple values in the buffer without blocking until full. | Can handle only one value at a time, requiring both sender and receiver to be ready. |



---

## **Channel Directions**
   - **Directional Channels**: You can specify if a channel is only for sending or receiving data, providing better control.
   - **Syntax**:
     ```go
     func sendData(ch chan<- int) {  // Only for sending
         ch <- 42
     }

     func receiveData(ch <-chan int) {  // Only for receiving
         fmt.Println(<-ch)
     }
     ```
   - **Example**:
     ```go
     package main
     import "fmt"

     func sendOnly(ch chan<- int) {
         ch <- 100
     }

     func receiveOnly(ch <-chan int) {
         fmt.Println(<-ch)
     }

     func main() {
         ch := make(chan int)
         go sendOnly(ch)
         go receiveOnly(ch)
     }
     ```



###  **Select Statement**
   - **Definition**: The `select` statement allows a goroutine to wait on multiple communication operations.
   - **Syntax**:
     ```go
     select {
     case val := <-ch1:
         // Process val from ch1
     case val := <-ch2:
         // Process val from ch2
     default:
         // Execute if no channels are ready
     }
     ```
   - **Example**:
     ```go
     package main
     import "fmt"

     func main() {
         ch1 := make(chan string)
         ch2 := make(chan string)

         go func() { ch1 <- "message from channel 1" }()
         go func() { ch2 <- "message from channel 2" }()

         select {
         case msg1 := <-ch1:
             fmt.Println(msg1)
         case msg2 := <-ch2:
             fmt.Println(msg2)
         }
     }
     ```
 **Buffered Channels**: The sender is only blocked when the buffer is full, and the receiver is blocked when the buffer is empty.
   - **Syntax**:
     ```go
     ch := make(chan int, 3)  // Buffered channel with a capacity of 3
     ```
     
   - **Example**:
     ```go
     package main
     import "fmt"

     func main() {
         ch := make(chan int, 2)  // Buffered channel

         ch <- 1  // Send data into the channel
         ch <- 2

         fmt.Println(<-ch)  // Receive data from the channel
         fmt.Println(<-ch)
     }
     ```

     ### **Closing Channels**
   - **Purpose**: Closing a channel indicates that no more values will be sent on it.
   - **Syntax**:
     ```go
     close(ch)
     ```
   - **Example**:
     ```go
     package main
     import "fmt"

     func main() {
         ch := make(chan int, 2)
         ch <- 1
         ch <- 2
         close(ch)

         for value := range ch {
             fmt.Println(value)
         }
     }
     ```
---


###  **Mutexes for Data Safety**
   - **Definition**: A `Mutex` (mutual exclusion) is used to ensure only one goroutine can access a critical section of code at a time.
   - **Import Package**: `"sync"`
   - **Syntax**:
     ```go
     var mu sync.Mutex
     mu.Lock()   // Lock the mutex
     // Critical section
     mu.Unlock() // Unlock the mutex
     ```
   - **Example**:
     ```go
     package main
     import (
         "fmt"
         "sync"
     )

     var counter int
     var mu sync.Mutex

     func increment(wg *sync.WaitGroup) {
         mu.Lock()
         counter++
         mu.Unlock()
         wg.Done()
     }

     func main() {
         var wg sync.WaitGroup
         for i := 0; i < 10; i++ {
             wg.Add(1)
             go increment(&wg)
         }
         wg.Wait()
         fmt.Println("Final Counter:", counter)
     }
     ```
  
---

###  **WaitGroups for Synchronizing Goroutines**
   - **Definition**: `WaitGroup` is used to wait for multiple goroutines to finish executing.
   - **Import Package**: `"sync"`
   - **Syntax**:
     ```go
     var wg sync.WaitGroup
     wg.Add(1)  // Increment the counter
     wg.Done()  // Decrement the counter
     wg.Wait()  // Block until counter is zero
     ```
   - **Example**:
     ```go
     package main
     import (
         "fmt"
         "sync"
     )

     func sayHello(wg *sync.WaitGroup) {
         fmt.Println("Hello, World!")
         wg.Done()  // Mark this goroutine as done
     }

     func main() {
         var wg sync.WaitGroup
         wg.Add(1)  // Add a goroutine to wait for
         go sayHello(&wg)
         wg.Wait()  // Wait for all goroutines to finish
     }
     ```
   - **Explanation**: The `WaitGroup` ensures `main` waits for `sayHello` to complete before exiting.

---
### Positional Arguments: 

The flag package doesn’t handle non-flag arguments by default (i.e., positional arguments). 
These can be accessed using flag.Args() which returns a slice of strings containing all the non
flag arguments. 

**Bool Flags:** 

If you want to parse boolean flags, you can use the Bool function: 

```verbose := flag.Bool("verbose", false, "Enable verbose mode.")  ```

Then, the presence of the flag implies true, otherwise, it defaults to false: 

````$ go run main.go -verbose```` 

**Handling Multiple Values:**

If you want a flag that can take multiple values, you can use the flag.Var function with a custom 
type that implements the flag.Value interface. 

**Error Handling:** 

The flag package provides some default error handling. If a user provides an invalid flag or a flag

---

