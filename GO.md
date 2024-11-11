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



# UNIT 5

### ** Concurrency in Go**
   - **Definition**: Go has built-in support for concurrency through goroutines and channels. Concurrency means multiple tasks can run in overlapping time periods, rather than sequentially.
   - **Key Concepts**: 
     - **Goroutines**: Lightweight threads managed by the Go runtime.
     - **Channels**: Used for communication between goroutines.

   - **Syntax for Goroutines**:
     ```go
     go functionName()  // Starts a new goroutine
     ```
   - **Example**:
     ```go
     package main
     import (
         "fmt"
         "time"
     )

     func printMessage(message string) {
         for i := 0; i < 5; i++ {
             fmt.Println(message)
             time.Sleep(time.Millisecond * 500)
         }
     }

     func main() {
         go printMessage("Goroutine 1")
         go printMessage("Goroutine 2")

         time.Sleep(time.Second * 3)  // Main function waits for goroutines
     }
     ```
   - **Explanation**: `printMessage` runs concurrently in two goroutines, and `time.Sleep` keeps the main function alive to see their output.

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
     import "fmt"

     func calculateSquare(num int, ch chan int) {
         ch <- num * num  // Send the result into the channel
     }

     func main() {
         ch := make(chan int)
         go calculateSquare(4, ch)  // Start a goroutine
         result := <-ch             // Receive the result from channel
         fmt.Println("Square:", result)  // Output: Square: 16
     }
     ```
   - **Explanation**: The result is passed from `calculateSquare` back to `main` using a channel.


---

### **Goroutines**
   - **Definition**: Goroutines are lightweight, managed threads that allow for concurrent execution in Go. They are much more efficient in terms of memory and processing compared to traditional operating system threads.
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
   - **Explanation**: 
     - `printNumbers` is executed concurrently with the `main` function.
     - The `time.Sleep` call in `main` keeps the program running long enough for `printNumbers` to complete.

#### **Characteristics of Goroutines**:
   - **Efficient**: A single Go program can run thousands of goroutines simultaneously.
   - **Non-blocking**: Starting a goroutine does not block the execution of the main function.
   - **Managed by Go Runtime**: The Go runtime schedules and manages goroutines, making them efficient and easy to use compared to traditional threads.

---

### **Channels**
   - **Definition**: Channels provide a way for goroutines to communicate and synchronize by passing data. They are a crucial feature in Go for sharing information safely between goroutines.
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
   - **Explanation**: 
     - `sum` is executed as a goroutine, and the result of the addition is sent into the channel `ch`.
     - The `main` function waits to receive the result from the channel before printing it.

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
   - **Explanation**: Using `range` to iterate over the channel allows reading all values until the channel is closed.

---

### **Channel Directions**
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

---

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
   - **Explanation**: `select` waits for either `ch1` or `ch2` to send a message, and processes whichever is ready first.

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
   - **Explanation**: `mu.Lock()` and `mu.Unlock()` ensure that only one goroutine modifies `counter` at a time.

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

