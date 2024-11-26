# unit -1

## Key Features of Go:

Go, also known as **Golang**, is a statically typed, compiled programming language designed by Google. It emphasizes simplicity, efficiency, and robust performance, making it well-suited for a variety of use cases like web servers, distributed systems, and command-line tools.


1. **Simplicity**: Go has a straightforward syntax and eliminates many complexities found in other languages.
2. **Concurrency**: Go provides first-class support for concurrent programming through **goroutines** and **channels**.
3. **Performance**: Being a compiled language, Go programs run close to native speed.
4. **Garbage Collection**: Go includes automatic memory management, making it easier to avoid memory leaks.
5. **Standard Library**: It has a rich standard library that covers common tasks like networking, file I/O, and web development.
6. **Cross-Compilation**: It supports easy cross-compilation for multiple platforms.

### Go's Ecosystem:
- **Tooling**: Go provides powerful tools like `go build`, `go test`, `go fmt`, and `go mod`.
- **Package Management**: Modules (introduced in Go 1.11) streamline dependency management.
- **Community**: Go has a growing community with many open-source libraries and frameworks.

### Code Example
Here’s a simple Go program:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

### Running the Program
1. Save the code in a file, e.g., `main.go`.
2. Open a terminal, navigate to the file's directory, and run:
   ```bash
   go run main.go
   ```
---

## How Go lang programming is different from c, c++, python, java 

### **1. Syntax**
- **Go:** 
  - Simpler and more concise syntax compared to C and C++.
  - Removes features like header files, preprocessor directives, and complex pointer arithmetic.
- **Others:**  
  - C and C++ have more verbose and complex syntax.
  - Python is known for its simplicity but uses dynamic typing, which is different from Go's static typing.
  - Java is verbose, with a class-based structure and requires more boilerplate code.


### **2. Concurrency**
- **Go:**
  - Built-in support for concurrency through **goroutines** (lightweight threads) and **channels** for communication and synchronization.
- **Others:**
  - C, C++, Python, and Java often require explicit threading models or third-party libraries for concurrency.
  - Java offers threading with more abstraction than C/C++, but it’s not as lightweight as goroutines.


### **3. Memory Management**
- **Go:**
  - Includes a **garbage collector** for automatic memory management.
  - Developers don’t manually allocate or deallocate memory.
- **Others:**
  - **C/C++:** Requires manual memory management.
  - **Python and Java:** Both include garbage collection, but Go's implementation is more optimized for concurrent workloads.


### **4. Type System**
- **Go:**
  - Statically typed (types checked at compile time) with a simpler type system.
- **Others:**
  - **C/C++ and Java:** Statically typed with more advanced or complex type systems.
  - **Python:** Dynamically typed, allowing flexibility but at the cost of runtime checks.


### **5. Standard Library**
- **Go:**
  - A rich standard library for tasks like networking, file I/O, and JSON processing, optimized for simplicity and performance.
- **Others:**
  - C and C++ have standard libraries, but many tasks require external libraries.
  - Python and Java have extensive libraries but might include some redundancy or legacy APIs.


### **6. Compilation and Execution**
- **Go:**
  - Compiled language with **faster compilation times**.
  - Produces statically linked standalone executables, making them easy to distribute.
- **Others:**
  - **C and C++:** Compiled but can have slower compile times, especially for large codebases.
  - **Python and Java:** Use interpreters or Just-In-Time (JIT) compilation, which may affect runtime performance compared to Go.


### **7. Error Handling**
- **Go:**
  - Uses **explicit error handling** with return values, encouraging developers to handle errors directly.
- **Others:**
  - C++/Python/Java use **exceptions**, which can obscure control flow if not managed properly.


### **8. Object-Oriented Programming**
- **Go:**
  - Lacks traditional OOP concepts like classes and inheritance.
  - Uses **struct types**, **interfaces**, and composition for polymorphism and code reuse.
- **Others:**
  - **C++/Java/Python:** Have full-fledged OOP systems with classes, inheritance, and advanced polymorphism.


---


## Go lang Machine setup - Text Editors, The Terminal, Environment 

### **Text Editors and IDEs**
1. **Visual Studio Code (VS Code):**  
   - Lightweight editor with excellent Go support.  
   - Install the Go extension for features like code completion, debugging, and formatting.  

2. **GoLand:**  
   - A specialized IDE from JetBrains for Go.  
   - Includes advanced code analysis, refactoring tools, and version control support.  

3. **Other Editors:**  
   - Editors like Sublime Text, Atom, or Vim also support Go via plugins.

### **The Terminal**
- Go relies on the command-line interface (CLI).  
- You can use an **integrated terminal** within text editors like VS Code or GoLand, or a **separate terminal emulator**, such as:
  - **macOS:** Terminal or iTerm2
  - **Windows:** Git Bash
  - **Linux:** GNOME Terminal  

### **Environment Variables**
1. **GOPATH:**  
   - Specifies the workspace directory for Go projects.  
   - Example: `export GOPATH=$HOME/go`

2. **GOROOT:**  
   - Specifies the Go installation directory.  
   - Automatically set by the installer, no need for manual configuration.

3. **PATH:**  
   - Add Go’s binary directory to the system PATH for easy access to Go commands.  
   - Example for Unix-like systems:
     ```bash
     export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
     ```

---

## datatypes in go
Go has a robust type system, and its data types can be broadly categorized into basic types, composite types, and reference types. Here's a detailed overview:


### **1. Basic Data Types**
These are the fundamental types provided by Go.

#### **a. Boolean**
- **Type**: `bool`
- **Values**: `true` or `false`
- **Example**:
  ```go
  var isAvailable bool = true
  ```

#### **b. Numeric Types**
##### i. **Integer**
- **Signed integers**: `int`, `int8`, `int16`, `int32`, `int64`
- **Unsigned integers**: `uint`, `uint8` (alias for `byte`), `uint16`, `uint32`, `uint64`
- **Platform-dependent**:
  - `int` and `uint` depend on the architecture (32-bit or 64-bit).

##### ii. **Floating-point**
- **Types**: `float32`, `float64`
- **Example**:
  ```go
  var pi float64 = 3.14159
  ```

##### iii. **Complex Numbers**
- **Types**: `complex64`, `complex128`
- **Example**:
  ```go
  var z complex128 = complex(3, 4) // 3 + 4i
  ```

##### iv. **Other Numeric Types**
- `byte`: Alias for `uint8`.
- `rune`: Alias for `int32` (represents Unicode code points).

#### **c. String**
- **Type**: `string`
- **Description**: A sequence of bytes representing text in UTF-8 encoding.
- **Immutable**: Strings in Go cannot be modified after creation.
- **Example**:
  ```go
  var greeting string = "Hello, Go!"
  ```

---

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

---

# unit 2

## **Variables in Go**

A **variable** in Go is a storage container for data that can be used and modified during a program's execution.

#### **Naming Conventions**
- Must start with a letter; additional characters can be letters or numbers.
- Cannot begin with a number or underscore.
- No spaces in names.
- Use camel case for readability, e.g., `empName`.
- Case-sensitive (e.g., `car`, `Car`, and `CAR` are different).
- Cannot use reserved words as variable names.
- Variables starting with a lowercase letter are package-private (unexported), while those starting with an uppercase letter are accessible outside the package (exported).


### **Variable Declaration**
1. **Using `var` Keyword**
   ```go
   var num int = 10
   var name string = "Alice"
   ```
   
2. **Without Initialization**
   ```go
   var num int // Defaults to 0
   var name string // Defaults to ""
   ```
   
3. **With Type Inference**
   ```go
   var age = 25 // Type inferred as int
   var city = "New York" // Type inferred as string
   ```

4. **Short Variable Declaration**
   - Commonly used inside functions.
   - Syntax:
     ```go
     age := 30
     name := "Bob"
     ```
   - No need for `var` or explicit types.

5. **Multiple Variables**
   - Same type:
     ```go
     var a, b, c int = 1, 2, 3
     ```
   - Different types:
     ```go
     var (
         name string = "Alice"
         age  int    = 25
         isActive bool = true
     )
     ```

---

## **Scope of Variables**

The **scope** of a variable in Go refers to the section of code where the variable is accessible.

#### **1. Local Variables**
- Declared inside a function or block.
- Accessible only within that function or block.
- Lifetime ends when the function or block execution finishes.

   **Example:**
   ```go
   func main() {
       var localVar = "I'm local!"
       fmt.Println(localVar) // Accessible here
   }
   // localVar is not accessible here
   ```

#### **2. Global Variables**
- Declared outside any function, usually at the top of the file.
- Accessible by all functions in the same package.

   **Example:**
   ```go
   var globalVar = "I'm global!"

   func main() {
       fmt.Println(globalVar) // Accessible here
   }

   func anotherFunc() {
       fmt.Println(globalVar) // Accessible here too
   }
   ```

#### **3. Package-Level Variables**
- Declared at the package level.
- Accessible throughout the package, but exported variables (starting with uppercase) are accessible outside the package.

---

## **Constants in Go**

- A **constant** in Go is a value that cannot be changed once it is assigned. Constants are evaluated at compile time and provide reliability in code by ensuring immutability.
- Constants ensure immutability and clarity in Go programs, making code easier to debug and maintain.

#### **Key Features of Constants**
- Declared using the `const` keyword.
- Can store values of primitive data types such as **boolean**, **numeric**, or **string**.
- Immutable (cannot be modified once assigned).
- Improves readability and prevents accidental modification of critical values.


### **Declaration Syntax**

1. **Typed Constants**
   - Type is explicitly declared.
   - Example:
     ```go
     const LENGTH int = 10
     const PI float64 = 3.14159
     ```
-  Specific type ensures type safety.
  - Example:
    ```go
    const LENGTH int = 10
    fmt.Printf("Length: %d\n", LENGTH)
    ```

2. **Untyped Constants**
   - No explicit type; type is inferred when used.
   - Example:
     ```go
     const GREETING = "Hello, Go!"
     const PI = 3.14159
     ```

  - Flexible in usage and can adapt their type based on the context.
  - Example:
    ```go
    const COUNT = 10
    var x float64 = COUNT * 1.5
    fmt.Printf("Result: %.2f\n", x)
    ```
     

**Typed and Untyped Constants**
   - Example
   ```go
   const val1 = 10
   const val2 int = 20

   fmt.Println("Value of val1:", val1)
   fmt.Println("Value of val2:", val2)
   ```


### **Types of Constants in Go**

#### **1. Numeric Constants**
   - Numeric constants can be of different types such as **integer**, **floating-point**, and **complex** numbers.
   
   **Example:**
   ```go
   package main
   import "fmt"
   func main() {
       const val1 = 10              // Untyped integer
       const val2 float64 = 10.23   // Typed floating-point
       const complexNum = 1 + 2i    // Untyped complex number

       fmt.Printf("val1: %d\n", val1)
       fmt.Printf("val2: %.2f\n", val2)
       fmt.Printf("Complex number: %v\n", complexNum)
   }
   ```

#### **2. String Literals**
   - String constants are enclosed in double quotes (`"`).
   - Example:
     ```go
     const message = "Welcome to Go programming"
     fmt.Println(message)
     ```

#### **3. Boolean Constants**
   - Can only be `true` or `false`.
   - Example:
     ```go
     const isLearning bool = true
     fmt.Printf("Learning Go: %v\n", isLearning)
     ```
**String and Boolean Constants Example**
   
  ```go
   const myString = "Hello, World!"
   const myBool bool = true

   fmt.Printf("String constant: %s\n", myString)
   fmt.Printf("Boolean constant: %v\n", myBool)
   ```

---

## **Control Structures in Go**

Control structures are used to control the flow of execution in a Go program. They help in making decisions, repeating certain actions, and choosing between different alternatives. Go provides several control structures, including `if`, `if-else`, `if-else-if`, `nested if`, `for` loop, and `switch-case`. 

- These control structures are fundamental for programming in Go, allowing for flexible and efficient code execution.


### **1. If Statement**

The `if` statement is used to execute a block of code if a specified condition is true.
- **If**: Checks a single condition and executes a block of code if the condition is true.

#### **Syntax:**
```go
if condition {
    // code to be executed if condition is true
}
```

#### **Flowchart**:
```
[Start] --> [Evaluate Condition]
            |
            |----> [True] --> [Execute Code]
            |
            |----> [False] --> [End]
```

#### **Example**:
```go
package main
import "fmt"

func main() {
    x := 10
    if x > 5 {
        fmt.Println("x is greater than 5")
    }
}
```

---

### **2. If-Else Statement**

The `if-else` statement allows the program to choose between two blocks of code: one that runs if the condition is true, and another that runs if it is false.
- **If-Else**: Executes one block if the condition is true, another if it is false.


#### **Syntax:**
```go
if condition {
    // code to be executed if condition is true
} else {
    // code to be executed if condition is false
}
```

#### **Flowchart**:
```
[Start] --> [Evaluate Condition]
            |
            |----> [True] --> [Execute True Block] --> [End]
            |
            |----> [False] --> [Execute False Block] --> [End]
```

#### **Example**:
```go
package main
import "fmt"

func main() {
    x := 3
    if x > 5 {
        fmt.Println("x is greater than 5")
    } else {
        fmt.Println("x is less than or equal to 5")
    }
}
```

---

### **3. If-Else-If Statement**

The `if-else-if` statement is used when there are multiple conditions to check, and different code blocks should execute for different conditions.
- **If-Else-If**: Checks multiple conditions and executes corresponding blocks.


#### **Syntax:**
```go
if condition1 {
    // code to be executed if condition1 is true
} else if condition2 {
    // code to be executed if condition2 is true
} else {
    // code to be executed if no conditions are true
}
```

#### **Flowchart**:
```
[Start] --> [Evaluate Condition1]
            |
            |----> [True] --> [Execute Block 1] --> [End]
            |
            |----> [False] --> [Evaluate Condition2]
                             |
                             |----> [True] --> [Execute Block 2] --> [End]
                             |
                             |----> [False] --> [Execute Else Block] --> [End]
```

#### **Example**:
```go
package main
import "fmt"

func main() {
    x := 6
    if x > 10 {
        fmt.Println("x is greater than 10")
    } else if x > 5 {
        fmt.Println("x is greater than 5 but less than or equal to 10")
    } else {
        fmt.Println("x is less than or equal to 5")
    }
}
```

---

### **4. Nested If Statement**

A **nested if** is an `if` statement inside another `if` or `else` block. It allows for more complex decision-making.
- **Nested If**: Allows for more complex decision-making with nested conditions.

#### **Syntax:**
```go
if condition1 {
    if condition2 {
        // code to be executed if condition1 and condition2 are true
    }
}
```

#### **Flowchart**:
```
[Start] --> [Evaluate Condition1]
            |
            |----> [True] --> [Evaluate Condition2]
                             |
                             |----> [True] --> [Execute Code] --> [End]
                             |
                             |----> [False] --> [End]
            |
            |----> [False] --> [End]
```

#### **Example**:
```go
package main
import "fmt"

func main() {
    x := 10
    if x > 5 {
        if x < 15 {
            fmt.Println("x is between 5 and 15")
        }
    }
}
```

---

### **5. For Loop**

Go only has one loop construct: the `for` loop. It is used to repeat a block of code multiple times.
- **For Loop**: Repeats a block of code multiple times based on a condition.


#### **Syntax:**
```go
for initialization; condition; increment {
    // code to be executed repeatedly
}
```

#### **Flowchart**:
```
[Start] --> [Initialize] --> [Evaluate Condition]
            |
            |----> [True] --> [Execute Loop] --> [Increment] --> [Evaluate Condition]
            |
            |----> [False] --> [End]
```

#### **Example**:
```go
package main
import "fmt"

func main() {
    for i := 1; i <= 5; i++ {
        fmt.Println(i)
    }
}
```

---

### **6. Switch-Case Statement**

The `switch` statement is used for multiple conditions that are evaluated and checked in sequence. It is an alternative to a series of `if-else` statements.
- **Switch-Case**: A multi-way branch statement that compares an expression with multiple cases.


#### **Syntax:**
```go
switch expression {
case value1:
    // code to execute if expression == value1
case value2:
    // code to execute if expression == value2
default:
    // code to execute if expression doesn't match any case
}
```

#### **Flowchart**:
```
[Start] --> [Evaluate Expression]
            |
            |----> [Match Case 1] --> [Execute Case 1 Block] --> [End]
            |
            |----> [Match Case 2] --> [Execute Case 2 Block] --> [End]
            |
            |----> [No Match] --> [Execute Default Block] --> [End]
```

#### **Example**:
```go
package main
import "fmt"

func main() {
    day := 3
    switch day {
    case 1:
        fmt.Println("Sunday")
    case 2:
        fmt.Println("Monday")
    case 3:
        fmt.Println("Tuesday")
    case 4:
        fmt.Println("Wednesday")
    default:
        fmt.Println("Invalid day")
    }
}
```

---

## **Arrays in Go**

An **array** in Go is a collection of elements of the same type, stored in contiguous memory locations. Arrays have a fixed size, meaning their length cannot change after declaration.
- Arrays in Go are fixed in size and store elements of the same type.
- Arrays can be initialized one element at a time or all at once.
  

### **Key Characteristics**
1. All elements must be of the same type.
2. Array size is fixed and specified during declaration.
3. Elements can be accessed using zero-based indexing.
4. Go arrays are value types, meaning assigning an array to another variable creates a copy.


### **Declaring and Initializing Arrays**

#### **1. Declaration**
       ```go
      var arrayName [size]dataType
       ```
 - **At Declaration:**
     ```go
     var arrayName = [size]dataType{value1, value2, ..., valueN}
     ```

#### **2. Initialization**
   - **One by One:**
     ```go
     arrayName[index] = value
     ```

   - **Implicit Size:**
     ```go
     arrayName := [...]dataType{value1, value2, ..., valueN}
     ```

#### **Example:**
```go
package main
import "fmt"

func main() {
    // Declare and initialize an array
    var numbers = [5]int{10, 20, 30, 40, 50}

    // Accessing elements
    fmt.Println("First element:", numbers[0])

    // Changing an element
    numbers[0] = 15
    fmt.Println("Modified first element:", numbers[0])
}
```



### **Accessing Array Elements**
- Array elements can be accessed using their index.
- Accessing elements involves specifying the index or indices.
  
```go
var element = arrayName[index]
```

#### **Example:**
```go
fmt.Println(arrayName[2]) // Prints the third element
```
---

## **2D Arrays in Go**

- A **2D array** is an array of arrays. It can be visualized as a table with rows and columns.
- **2D arrays** are arrays of arrays and allow storage of tabular data.


#### **Declaration and Initialization**

**Syntax:**

```go
var arrayName [rows][columns]dataType
```

**Initializing:**

- Row by Row:
  ```go
  arrayName[rowIndex][colIndex] = value
  ```
- All at Once:
  ```go
  var arrayName = [rows][columns]dataType{
      {value1, value2, ..., valueN},  // Row 1
      {value1, value2, ..., valueN},  // Row 2
      ...
  }
  ```

---

#### **Example:**
```go
package main
import "fmt"

func main() {
    // Declare and initialize a 2D array
    var matrix = [3][3]int{
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9},
    }

    // Accessing elements
    fmt.Println("Element at [1][2]:", matrix[1][2])

    // Modifying an element
    matrix[0][0] = 10
    fmt.Println("Modified matrix:", matrix)
}
```

### **Accessing 2D Array Elements**
Elements are accessed using their row and column indices.
```go
var element = arrayName[rowIndex][colIndex]
```


### **Example Program to Print 2D Array**
```go
package main
import "fmt"

func main() {
    // Declare and initialize a 2D array
    var matrix = [2][3]int{
        {1, 2, 3},
        {4, 5, 6},
    }

    // Iterate and print elements
    for i := 0; i < 2; i++ {
        for j := 0; j < 3; j++ {
            fmt.Printf("matrix[%d][%d] = %d\n", i, j, matrix[i][j])
        }
    }
}
```

---

### **Slices in Go**

A **slice** in Go is a dynamic, flexible, and more powerful data structure than an array. While arrays have a fixed size, slices can grow or shrink dynamically. Slices are built on top of arrays and provide a convenient way to work with subsets of data.

- **Slices**: Dynamic and flexible, derived from arrays.

### **Key Features**
1. Slices are references to an underlying array.
2. They have dynamic sizes, unlike arrays.
3. Built-in functions like `append()` and `copy()` make slices flexible and easy to use.
4. Slice properties:
   - **Length** (`len`): Number of elements in the slice.
   - **Capacity** (`cap`): Maximum number of elements the slice can hold without reallocation.



### **Defining a Slice**
  
#### **1. From an Array**
A slice can be created by referencing a portion of an array.
```go
var array = [5]int{1, 2, 3, 4, 5}
var slice = array[1:4] // Creates a slice [2, 3, 4]
```

#### **2. Using `make()`**
The `make()` function is used to create a slice with a specified length and capacity.
```go
slice := make([]int, 5, 10) // Slice with length 5 and capacity 10
```

#### **3. Using Slice Literal**
Similar to an array literal but without specifying the size.
```go
slice := []int{1, 2, 3, 4, 5}
```


### **Appending Elements to a Slice**

The `append()` function adds one or more elements to the end of a slice. If the slice’s capacity is exceeded, a new underlying array is allocated.

#### **Syntax:**
```go
slice = append(slice, values...)
```

#### **Example:**
```go
package main
import "fmt"

func main() {
    slice := []int{1, 2, 3}
    fmt.Println("Original Slice:", slice)

    // Append a single element
    slice = append(slice, 4)
    fmt.Println("After appending 4:", slice)

    // Append multiple elements
    slice = append(slice, 5, 6, 7)
    fmt.Println("After appending 5, 6, 7:", slice)
}
```

---

### **Copying Slices**

The `copy()` function is used to copy elements from one slice to another. The number of elements copied is the minimum of the lengths of the source and destination slices.

#### **Syntax:**
```go
copy(destSlice, srcSlice)
```

#### **Example:**
```go
package main
import "fmt"

func main() {
    src := []int{1, 2, 3, 4, 5}
    dest := make([]int, 3)

    // Copy elements from src to dest
    n := copy(dest, src)
    fmt.Println("Copied Elements:", n)
    fmt.Println("Destination Slice:", dest)
}
```

---

### **Slice Properties**

#### **Getting Length and Capacity**
- **`len(slice)`**: Returns the current length of the slice.
- **`cap(slice)`**: Returns the total capacity of the slice.

#### **Example:**
```go
package main
import "fmt"

func main() {
    slice := make([]int, 3, 5)
    fmt.Println("Length:", len(slice)) // 3
    fmt.Println("Capacity:", cap(slice)) // 5
}
```

---

### **Example Program Using Slices**
```go
package main
import "fmt"

func main() {
    // Create a slice using make()
    slice := make([]int, 3, 5)
    fmt.Println("Initial Slice:", slice)

    // Append elements
    slice = append(slice, 1, 2)
    fmt.Println("After Append:", slice)

    // Create a new slice and copy data
    newSlice := make([]int, 2)
    copy(newSlice, slice)
    fmt.Println("New Slice After Copy:", newSlice)
}
```

---

## **Maps in Go**

A **map** in Go is a built-in data type that associates **keys** to **values**. Maps are unordered collections, meaning there is no defined order for how key-value pairs are stored.

- Maps are essential for key-value data representation and offer flexibility in managing dynamic data.

### **Key Features**
1. Maps are dynamic and grow as you add key-value pairs.
2. Keys must be unique, and their data type must be comparable (e.g., strings, integers, etc.).
3. Values can be of any type.

### **Defining a Map**

#### **Syntax:**
```go
var mapName map[keyType]valueType
```

#### **Creating Maps:**

1. **Using `make()`**:
 - Use `make()` or a literal to initialize a map.
   ```go
   mapName := make(map[keyType]valueType)
   ```
2. **Using a Map Literal**:
   ```go
   mapName := map[keyType]valueType{
       key1: value1,
       key2: value2,
   }
   ```

### **Basic Map Operations**

#### **1. Insert or Update**
- Assign values to keys using `mapName[key] = value`.
- To insert a key-value pair into a map or update an existing key:
```go
mapName[key] = value
```

#### **2. Accessing Values**
- Retrieve a value by using its key:
- Retrieve values with `mapName[key]` and check existence with the `exists` flag.

```go
value, exists := mapName[key]
```
- **`value`**: The value associated with the key.
- **`exists`**: A boolean indicating whether the key exists in the map.


#### **3. Delete**
- To remove a key-value pair:
- Remove key-value pairs using `delete(mapName, key)`.
 
```go
delete(mapName, key)
```

### **Example Program Demonstrating Map Operations**

```go
package main
import "fmt"

func main() {
    // Create a map using make()
    people := make(map[string]int)

    // Insert key-value pairs
    people["John"] = 28
    people["Jane"] = 34

    // Access and check for existence
    age, exists := people["John"]
    if exists {
        fmt.Println("John's age:", age)
    }

    // Update a value
    people["Jane"] = 35
    fmt.Println("Updated map:", people)

    // Delete a key
    delete(people, "John")
    fmt.Println("Map after deletion:", people)
}
```

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

