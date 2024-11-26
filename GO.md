
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

# unit 4

### Core Packages in Go 

### **1. `fmt` Package**
The `fmt` package is used for formatted input and output operations.

#### Commonly Used Functions:
- **`Print()`**: Prints text without a newline.
- **`Println()`**: Prints text followed by a newline.
- **`Printf()`**: Prints formatted strings.
- **`Scan()`**: Reads user input into variables.
- **`Scanf()`**: Reads formatted input.

---

### **2. `math` Package**
The `math` package provides functions for mathematical operations like square root, maximum, minimum, etc.

#### Commonly Used Functions:
- **`math.Sqrt(x)`**: Calculates the square root of `x`.
- **`math.Max(x, y)`**: Returns the larger of `x` and `y`.
- **`math.Min(x, y)`**: Returns the smaller of `x` and `y`.

---

### **3. `net/http` Package**
The `net/http` package is used to build HTTP servers and make HTTP requests.

#### Commonly Used Functions:
- **`http.HandleFunc()`**: Registers a handler function for a route.
- **`http.ListenAndServe()`**: Starts an HTTP server.
  
---
### **4. `strings` Package**

The `strings` package provides functions to manipulate and work with UTF-8 encoded strings. It is part of the Go standard library and contains many useful utilities for string operations.

#### Commonly Used Functions:
- **`strings.Contains(str, substr)`**: Checks if the `str` contains the substring `substr`.
- **`strings.Count(str, substr)`**: Returns the number of times `substr` appears in `str`.
- **`strings.Compare(str1, str2)`**: Compares two strings lexicographically.
- **`strings.ToLower(str)`**: Converts the string to lowercase.
- **`strings.ToUpper(str)`**: Converts the string to uppercase.
- **`strings.Join([]string, sep)`**: Joins a slice of strings into a single string, with a separator `sep`.
- **`strings.Split(str, sep)`**: Splits a string into a slice of substrings based on the separator `sep`.


---

### **5. Input/Output (I/O) Package**

The `io` package provides basic interfaces for I/O operations, including reading from and writing to different types of data streams like files, networks, or memory.

#### Commonly Used Interfaces:
- **`Reader`**: An interface for reading data.
  - `Read(p []byte) (n int, err error)` method to read data into a byte slice.
- **`Writer`**: An interface for writing data.
  - `Write(p []byte) (n int, err error)` method to write data from a byte slice.


---

### **6. File and Folders (`os` Package)**

The `os` package provides functions for interacting with the operating system, particularly for file manipulation and accessing environment variables.

#### Commonly Used Functions:
- **`os.Open(path string)`**: Opens a file for reading.
- **`os.Create(path string)`**: Creates a new file for writing.
- **`os.Remove(path string)`**: Deletes a file or folder.
- **`os.Stat(path string)`**: Retrieves information about a file (e.g., size, permissions).
- **`os.Mkdir(path string, perm os.FileMode)`**: Creates a new directory with the specified permissions.



---

### **7. Containers and List (`container/list` Package)**

The `container/list` package implements a doubly linked list. It is useful for situations where elements need to be inserted or removed from both ends frequently.

#### Commonly Used Methods:
- **`list.New()`**: Creates a new empty list.
- **`list.PushBack(value)`**: Adds a new element to the end of the list.
- **`list.PushFront(value)`**: Adds a new element to the front of the list.
- **`list.Remove(element)`**: Removes an element from the list.



---

### **8. Sort Package (`sort` Package)**

The `sort` package provides functions to sort slices and user-defined collections. It is widely used for ordering data.

#### Commonly Used Functions:
- **`sort.Ints(slice []int)`**: Sorts a slice of integers in increasing order.
- **`sort.Strings(slice []string)`**: Sorts a slice of strings in lexicographical order.
- **`sort.Sort(sort.Interface)`**: Sorts any collection that implements the `sort.Interface`.

---

### **9. Errors Package (`errors` Package)**

The `errors` package provides functions for creating and handling errors in Go. It allows for better error handling and generation.

#### Commonly Used Functions:
- **`errors.New("message")`**: Creates a new error with the given message.
- **`fmt.Errorf("format", args...)`**: Formats and returns an error.



---


## Step-by-Step Guide to Create Packages in Go

1. **Create a New File**
   - Create a `.go` file in your workspace for your custom package.

2. **Declare the Package**
   - Add the `package` keyword followed by the package name at the beginning of the file. This name should describe the functionality.
   ```go
   package calculator
   ```

3. **Write Functions**
   - Define the functions you want to include in your package. Use an uppercase first letter in function names to make them **exported** (accessible outside the package).
   ```go
   package calculator

   func Add(a, b int) int {
       return a + b
   }

   func Subtract(a, b int) int {
       return a - b
   }
   ```

4. **Save the File**
   - Save the file with an appropriate name, such as `calculator.go`.

5. **Use the Package**
   - Create another `.go` file in your workspace (e.g., `main.go`) and import your custom package.

6. **Import the Package**
   - Use the `import` keyword and the package path. Ensure the package is in the correct `GOPATH` or module structure.
   ```go
   package main

   import (
       "fmt"
       "your_module_path/calculator"
   )
   ```

7. **Call Package Functions**
   - Call the functions defined in your custom package.
   ```go
   func main() {
       result := calculator.Add(3, 5)
       fmt.Println("Sum:", result)

       result = calculator.Subtract(10, 4)
       fmt.Println("Difference:", result)
   }
   ```

8. **Build and Run**
   - Use the `go run main.go` or `go build` command to execute the program. Ensure all files are correctly referenced and in the appropriate paths.


---

## **Steps to Create a Server in Go**

In Go, creating a server is straightforward using the `net/http` package. The process involves defining routes, handling requests, and starting the server. Here's how to do it:


### **1. Import Necessary Packages**
- Import the `net/http` package for HTTP server functionalities.
- Optionally, import other packages like `fmt` for logging or additional utilities.


### **2. Create HTTP Handler Functions**
Handler functions define how the server responds to specific routes. Each handler function has the following signature:
```go
func(w http.ResponseWriter, r *http.Request)
```
- **`http.ResponseWriter`**: Used to write the response back to the client.
- **`http.Request`**: Contains the details of the HTTP request.

### **3. Register Routes**
- Use `http.HandleFunc` to map specific URL paths to handler functions.
- For static files, you can use `http.FileServer` or a similar utility.
- Map URL paths to handler functions using `http.HandleFunc`.
- Serve static files (HTML, CSS, JS) using `http.FileServer`.


### **4. Start the Server**
- Use `http.ListenAndServe` to start the server.
- Specify the address (e.g., `":8080"`) where the server will listen for incoming requests.
- Use `http.ListenAndServe` to listen for requests on a specified port.
- It blocks and runs the server until terminated.

- **Middleware**: Add middleware to log requests, handle authentication, or compress responses.

  
- **Complete Example**

```go
package main

import (
    "fmt"
    "net/http"
)

// Handler function for the root path
func homeHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "Welcome to the Go Server!")
}

// Handler function for another route
func aboutHandler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "This is the About Page.")
}

func main() {
    // Register routes
    http.HandleFunc("/", homeHandler) // Maps "/" to homeHandler
    http.HandleFunc("/about", aboutHandler) // Maps "/about" to aboutHandler

    // Start the server on port 8080
    fmt.Println("Server is running on http://localhost:8080")
    err := http.ListenAndServe(":8080", nil) // Start server
    if err != nil {
        fmt.Println("Error starting server:", err)
    }
}
```
---
## **Steps to Create a TCP Server in Go** (Based on the PDF)

A TCP server in Go is implemented using the `net` package, which provides the tools needed to manage connections and exchange data over the Transmission Control Protocol (TCP).


### **1. Import Necessary Packages**
- **`net`**: Provides functions to listen for and handle TCP connections.
- **`fmt`**: For logging and debugging.


### **2. Start a TCP Listener**
- Use `net.Listen("tcp", ":port")` to create a listener that waits for incoming TCP connections on a specific port (e.g., `":9999"`).

 - `net.Listen("tcp", ":9999")`: Opens a TCP port (9999) for listening.
 - `listener.Accept()`: Waits for and accepts incoming client connections.


### **3. Accept Connections**
- Use `listener.Accept()` in a loop to accept incoming client connections.
- Each accepted connection is represented by a `net.Conn` object, which is used to read and write data.


### **4. Handle Connections**
- For each connection, handle client communication (e.g., read/write) in a separate goroutine to allow multiple clients to connect concurrently.
- **Connection Handling**:
   - Each connection is represented by a `net.Conn` object.
   - Handling is done in a separate goroutine (`go handleConnection`) to manage multiple clients simultaneously.


### **5. Read and Write Data**
- Use `conn.Read()` to receive data from the client.
- Use `conn.Write()` to send data back to the client.


### 6. **Graceful Closure**:
   - `conn.Close()`: Ensures the connection is closed after communication is complete.


- **Complete Example: TCP Server**

```go
package main

import (
    "bufio"
    "fmt"
    "net"
)

func handleConnection(conn net.Conn) {
    defer conn.Close() // Ensure the connection is closed when the function exits

    // Read data from the client
    reader := bufio.NewReader(conn)
    msg, _ := reader.ReadString('\n')
    fmt.Println("Message from client:", msg)

    // Write response back to the client
    conn.Write([]byte("Hello, Client!\n"))
}

func main() {
    // Start a TCP listener on port 9999
    listener, err := net.Listen("tcp", ":9999")
    if err != nil {
        fmt.Println("Error starting server:", err)
        return
    }
    defer listener.Close()

    fmt.Println("TCP Server is running on port 9999...")

    // Accept connections in a loop
    for {
        conn, err := listener.Accept()
        if err != nil {
            fmt.Println("Connection error:", err)
            continue
        }
        go handleConnection(conn) // Handle each connection in a separate goroutine
    }
}
```

---
### **Steps to Create an RPC Server in Go** (Referenced from the PDF)

In Go, creating an RPC (Remote Procedure Call) server enables you to expose methods for remote execution over a network. The `net/rpc` package simplifies the implementation process.
- **Benefits of RPC in Go**
- Simplifies remote method invocation.
- Efficient for client-server communication.
- Supports structured data transmission over a network.

### **1. Import Necessary Packages**
- **`net/rpc`**: Core package for RPC functionality.
- **`net`**: For establishing network connections.
- **Optional**: Import `fmt` for logging and debugging.


### **2. Define the Server Struct and Methods**
- Create a struct to represent the RPC server.
- Define methods on the struct that can be remotely invoked. Each method must follow this signature:
  ```go
  func (s *StructName) MethodName(args ArgType, reply *ReplyType) error
  ```
  - **`args`**: Input parameters for the method.
  - **`reply`**: Pointer to store the result.
  - **`error`**: Return an error if the method fails.


### **3. Register the Server**
- Register the server using `rpc.Register(&Server{})`. This makes the server's methods accessible for RPC calls.


### **4. Start Listening for Connections**
- Use `net.Listen` to create a TCP listener on a specific port.
- Use `rpc.ServeConn` to handle incoming connections.


### **5. Write the Client**
- Use `rpc.Dial` to connect to the server.
- Call methods on the server using `client.Call`.


---

## HTTP GET and POST request

### **1. HTTP GET Requests**

HTTP GET requests are used to retrieve data from the server. The server does not modify its state or resources with these requests.

- Use **GET** for fetching data or performing operations that do not modify server state.
- Sent in the URL as query parameters
- Data retrieval
- Less secure (data visible in URL)
- Limited by URL length

#### **Process**
1. **Define a Handler Function**: The handler reads query parameters from the URL using `r.URL.Query()`.
2. **Register the Route**: Map a URL path to the handler using `http.HandleFunc`.
3. **Access Query Parameters**:
   - Query parameters are extracted as key-value pairs.
   - Use `r.URL.Query().Get("key")` to fetch specific parameter values.

#### **Code for Handling GET Requests**
```go
package main

import (
    "fmt"
    "net/http"
)

func getHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method == http.MethodGet {
        queryParam := r.URL.Query().Get("name")
        fmt.Fprintf(w, "Hello, %s!", queryParam)
    }
}

func main() {
    http.HandleFunc("/get", getHandler)
    http.ListenAndServe(":8080", nil)
}
```

---

### **2. HTTP POST Requests**

HTTP POST requests are used to send data to the server for processing (e.g., form submissions). Unlike GET, POST carries data in the request body.
- Use **POST** for submitting data or performing actions that change server state.
- Sent in the request body
- Data submission
- More secure (data not in URL)
- No practical size limit

#### **Process**
1. **Define a Handler Function**: The handler reads form data from the request body.
2. **Register the Route**: Map a URL path to the handler using `http.HandleFunc`.
3. **Parse and Access Data**:
   - Use `r.ParseForm()` to parse form data.
   - Access form values with `r.FormValue("key")`.

#### **Code for Handling POST Requests**
```go
package main

import (
    "fmt"
    "net/http"
)

func postHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method == http.MethodPost {
        r.ParseForm()
        name := r.FormValue("name")
        fmt.Fprintf(w, "Received POST data: %s", name)
    }
}

func main() {
    http.HandleFunc("/post", postHandler)
    http.ListenAndServe(":8080", nil)
}
```

---

### Differences Between `http.ListenAndServe` and `http.Server` in Go

| **Aspect**               | **`http.ListenAndServe`**                          | **`http.Server` Method**                                |
|---------------------------|---------------------------------------------------|--------------------------------------------------------|
| **Definition**            | A convenience function that creates and starts an HTTP server with default settings. | A customizable HTTP server struct for advanced configurations. |
| **Use Case**              | Simple use cases where default settings are sufficient. | Complex scenarios requiring custom timeouts, TLS, or logging. |
| **Customization**         | Limited customization (e.g., can only specify address and handler). | Fully customizable by modifying server fields.         |
| **Configuration**         | Does not allow setting parameters like timeouts, TLSConfig, etc. | Allows configuration of fields like `ReadTimeout`, `WriteTimeout`, and `TLSConfig`. |
| **Return Value**          | Returns an error directly.                        | Requires explicit invocation of methods like `ListenAndServe` or `ListenAndServeTLS`. |
| **TLS Support**           | Use `http.ListenAndServeTLS` for HTTPS support.   | HTTPS is supported directly via `TLSConfig`.           |
| **Implementation**        | Function provided for convenience; internally initializes an `http.Server`. | A struct requiring manual setup and invocation methods. |
| **Handler Specification** | Specify the handler directly as a second parameter. | Use the `Handler` field in the `http.Server` struct.   |
| **Default Port**          | No default; must specify the address (e.g., `":8080"`). | No default; must specify the address in the `Addr` field. |

---

## **Security Best Practices for Building a Go Server**

#### **1. Input Validation and Sanitization**
- Always validate and sanitize user input to prevent injection attacks.
- Use proper libraries to escape inputs, especially in SQL queries and HTML rendering.

#### **2. HTTPS and TLS**
- Use HTTPS to encrypt data in transit.
- Configure TLS securely by disabling weak ciphers and protocols.
- Use certificates from trusted certificate authorities.

#### **3. Authentication and Authorization**
- Implement strong authentication mechanisms (e.g., OAuth2, JWT).
- Use role-based access control (RBAC) to manage permissions.
- Never hard-code sensitive credentials or secrets.

#### **4. Protect Against CSRF and XSS**
- Implement Cross-Site Request Forgery (CSRF) tokens for sensitive actions.
- Escape or encode all user-generated content to prevent Cross-Site Scripting (XSS) attacks.

#### **5. Rate Limiting and Throttling**
- Limit the number of requests from a single client to mitigate abuse or denial-of-service attacks.
- Use rate-limiting middleware or tools.

#### **6. Error Handling**
- Do not expose detailed error messages to clients, as they might reveal server implementation details.
- Log errors securely for debugging purposes.

#### **7. Content Security Policy (CSP)**
- Configure a CSP to restrict sources of scripts, styles, and other content, reducing XSS risks.

#### **8. Secure Cookies**
- Use `Secure`, `HttpOnly`, and `SameSite` flags for cookies to protect session data.

#### **9. File Upload Security**
- Validate uploaded files for type, size, and content.
- Store uploaded files in secure, isolated locations with limited permissions.

#### **10. Keep Dependencies Up-to-Date**
- Regularly update Go packages and libraries to patch known vulnerabilities.

---

## **Handling File Uploads in a Go HTTP Server**

Handling file uploads involves allowing users to upload files to the server, processing them securely, and storing them in appropriate locations.

#### **Steps for Handling File Uploads**
1. **Set Up an HTTP Endpoint**:
   - Define a route to accept file uploads using an HTTP POST request.

2. **Parse Incoming Requests**:
   - Use `r.ParseMultipartForm` to handle `multipart/form-data` forms.
   - Access the uploaded file via `r.FormFile`.

3. **Validate the File**:
   - Check the file type, size, and name for security.

4. **Store the File**:
   - Save the file to a secure location on the server or a cloud storage solution.

### **Security Considerations for File Uploads**
1. **Limit File Size**:
   - Use `r.ParseMultipartForm(sizeLimit)` to prevent large files from overwhelming the server.

2. **Validate File Type**:
   - Inspect the file's content type or magic bytes to ensure it matches the expected format.

3. **Restrict File Paths**:
   - Prevent directory traversal attacks by sanitizing filenames.

4. **Use Temporary Storage**:
   - Store uploaded files in a temporary or sandboxed location for further inspection.

5. **Regularly Clean Up**:
   - Periodically remove unused or temporary uploaded files.


- **Code Example for Handling File Uploads**
```go
package main

import (
    "fmt"
    "net/http"
    "os"
    "io"
)

func uploadHandler(w http.ResponseWriter, r *http.Request) {
    if r.Method != http.MethodPost {
        http.Error(w, "Invalid request method", http.StatusMethodNotAllowed)
        return
    }

    // Parse the form and get the file
    r.ParseMultipartForm(10 << 20) // Max file size: 10 MB
    file, handler, err := r.FormFile("file")
    if err != nil {
        http.Error(w, "Error retrieving file", http.StatusBadRequest)
        return
    }
    defer file.Close()

    // Create destination file
    dst, err := os.Create("./uploads/" + handler.Filename)
    if err != nil {
        http.Error(w, "Unable to save file", http.StatusInternalServerError)
        return
    }
    defer dst.Close()

    // Copy file contents
    io.Copy(dst, file)

    fmt.Fprintf(w, "File uploaded successfully: %s", handler.Filename)
}

func main() {
    http.HandleFunc("/upload", uploadHandler)
    http.ListenAndServe(":8080", nil)
}
```

---
## **Handling WebSocket Connections in a Go Server**

To handle WebSocket connections in Go, the `github.com/gorilla/websocket` package is commonly used. Here are the high-level steps involved in implementing WebSocket connections in a Go server:

1. **Install the Gorilla WebSocket Package**:
   - Use `go get` to install the Gorilla WebSocket package.

2. **Upgrade HTTP Connection to WebSocket**:
   - Use `websocket.Upgrader` to upgrade an HTTP connection to a WebSocket connection.

3. **Accept Incoming WebSocket Connections**:
   - In the handler, use `websocket.Accept` to accept incoming WebSocket connections.

4. **Read and Write Messages**:
   - Use methods like `conn.ReadMessage()` and `conn.WriteMessage()` to read and write data to the WebSocket connection.

5. **Close the Connection**:
   - Properly close the WebSocket connection when done using `conn.Close()`.

---

## **Steps for Implementing Request Logging and Metrics in a Go Server**

1. **Request Logging**:
   - Create middleware to log incoming requests (method, URL, headers, etc.).
   - Log the response status and time taken to process the request.
   - Use the `log` package or a third-party logger like `logrus` or `zap`.

2. **Metrics Collection**:
   - Use libraries like `prometheus/client_golang` to gather metrics such as request count, response time, and error rates.
   - Define counters, histograms, and gauges for tracking metrics.
   - Expose an HTTP endpoint (e.g., `/metrics`) to allow Prometheus or another monitoring system to scrape metrics.

3. **Middleware for Logging and Metrics**:
   - Combine logging and metrics in middleware functions to capture data for every request.
   - Record metrics like the request duration and success/failure status.

4. **Logging and Metric Exporting**:
   - Periodically export the logs to a file or logging system (e.g., ELK stack, Splunk).
   - Expose the metrics for monitoring systems such as Prometheus, Grafana, or Datadog.

---

## Hashes and Cryptography in Go

Hashes and cryptography in Go are foundational for securing data, validating file integrity, and implementing cryptographic protocols. The PDF highlights two primary uses of hashes: **non-cryptographic hashes** and **cryptographic hashes**.


### **1. Non-Cryptographic Hashes**
Non-cryptographic hash functions generate fixed-size representations of data for fast lookups or comparisons. These are not suitable for security-sensitive applications.

#### Example: Using `crc32` for File Comparison
- The `crc32` package is part of Go's standard library for checksum calculations.

#### Key Steps:
1. **Create a CRC32 Hash Object**
   - Use `crc32.NewIEEE()` to initialize a hash generator.
   - Write data to the hash using `Write`.

   ```go
   import (
       "fmt"
       "hash/crc32"
   )

   func main() {
       h := crc32.NewIEEE()
       h.Write([]byte("example data"))
       fmt.Println(h.Sum32()) // Outputs: Checksum as uint32
   }
   ```

2. **Compare Files with CRC32**
   - Read file contents, compute their CRC32 values, and compare the results.

   ```go
   import (
       "fmt"
       "hash/crc32"
       "io/ioutil"
   )

   func getHash(filename string) (uint32, error) {
       data, err := ioutil.ReadFile(filename)
       if err != nil {
           return 0, err
       }
       h := crc32.NewIEEE()
       h.Write(data)
       return h.Sum32(), nil
   }

   func main() {
       hash1, _ := getHash("file1.txt")
       hash2, _ := getHash("file2.txt")
       fmt.Println("Files are identical:", hash1 == hash2)
   }
   ```


### **2. Cryptographic Hashes**
Cryptographic hash functions are designed for security. They produce fixed-size outputs that are nearly impossible to reverse or predict, ensuring data integrity and authentication.

   - **Fixed Size**: SHA-1 always outputs a 160-bit (20-byte) hash.
   - **Collision Resistance**: Hard to find two inputs producing the same hash.
   - **Irreversibility**: Given a hash, it’s computationally infeasible to deduce the original input.

#### Applications:
- Password hashing
- Digital signatures
- File integrity checks

#### Example: Using SHA-1
- The `crypto/sha1` package provides a cryptographic hash function for generating 160-bit hashes.

#### Key Steps:
1. **Create a SHA-1 Hash**
   - Initialize a SHA-1 hash using `sha1.New()`.
   - Write data to the hash and get the digest using `Sum`.

   ```go
   import (
       "crypto/sha1"
       "fmt"
   )

   func main() {
       h := sha1.New()
       h.Write([]byte("secure data"))
       fmt.Printf("%x\n", h.Sum(nil)) // Outputs: SHA-1 hash in hexadecimal
   }
   ```



---


