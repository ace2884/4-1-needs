# unit 5
## Parsing Command-Line Arguments: 
Parsing command-line arguments is a common task in many programs, and Go provides the flag 
package to make this process straightforward. 
1. **Importing the Required Package:** Begin by importing the flag package.
```   
import ( 
"flag" 
"fmt" 
)
```
2. **Define Flags:** Flags can be of various data types including string, int, bool, etc. 
```
var name = flag.String("name", "Guest", "Your name") 
var age = flag.Int("age", 25, "Your age") 
var isMember = flag.Bool("member", false, "Are you a member?")
```
The flag.AAA functions (e.g., flag.String, flag.Int) return a pointer to the variable type. The 
functions take three arguments.
The flag name as it will appear on the command line (name in this case). 
The default value. 
3. **Parse the Flags:** Once the flags have been defined, you can parse the command line into the 
defined flags using the ```flag.Parse()``` method. 

4. **Accessing Flag Values:** Since the flag functions return pointers, you must dereference them to 
access the underlying value.
```
fmt.Printf("Hello, %s!\n", *name) 
fmt.Printf("You are %d years old.\n", *age) 
fmt.Printf("Member status: %v\n", *isMember)
```

5.**Custom Flags:** If you have a custom type you want to use as a flag, you can define your own flag type by 
implementing the flag.Value interface, which requires Set(string) error and String() string 
methods. 

#### Example:  
```
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
go run main.go -name=John -age=30 -member=true
```
##### output:
```
Hello, John! 
You are 30 years old. 
Member status: true
```
---

## Positional Arguments: 
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

## concurrency 
with an invalid value, the program will print an error message and exit.
