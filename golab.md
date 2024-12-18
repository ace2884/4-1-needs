# go lab

### To run the program open folder and 
and enter following commands which opens Terminal
```
cmd
```
in Terminal 
```
go run filename.go
```


## week1 : LCM AND GCD

```go
package main

import "fmt"

func lcm(temp1 int, temp2 int) {
	var lcmnum int = 1
	if temp1 > temp2 {
		lcmnum = temp1
	} else {
		lcmnum = temp2
	}
	for {
		if lcmnum%temp1 == 0 && lcmnum%temp2 == 0 {
			fmt.Printf("LCM of %d amd %d is %d", temp1, temp2, lcmnum)
			break
		}
		lcmnum++
	}
	return
}
func gcd(temp1 int, temp2 int) {
	var gcdnum int
	for i := 1; i <= temp1 && i <= temp2; i++ {
		if temp1%i == 0 && temp2%i == 0 {
			gcdnum = i
		}
	}
	fmt.Printf("GCD of %d amd %d is %d", temp1, temp2, gcdnum)
	return
}
func main() {
	var n1, n2, action int
	fmt.Println("Enter two positive integers:")
	fmt.Scanln(&n1)
	fmt.Scanln(&n2)
	fmt.Println("Enter 1 for lcm and 2 for gcd")
	fmt.Scanln(&action)
	switch action {
	case 1:
		lcm(n1, n2)
	case 2:
		gcd(n1, n2)
	}
}
```

## week2 :PRINT PYRAMID OF NUMBER

```go

package main

import "fmt"

func main() {
	var n int
	fmt.Println("Enter number of levels:")
	fmt.Scanln(&n)
	for i := 1; i <= n; i++ {
		for j := 1; j <= n-i; j++ {
			fmt.Printf(" ")
		}
		for j := 1; j <= i; j++ {
			fmt.Printf(" %d", j)

		}
		for j := i - 1; j >= 1; j-- {
			fmt.Printf(" %d", j)
		}
		fmt.Println()
	}
}
```

## week3 : use struct that is imported from another package

```go
package main
import ("fmt" "newpack")
func main(){
result:= newpack.square(6)
fmt.Println("Square of 6 is:", result)
}
```
#### square.go
```go
package newpack
func square(x int) int{
return x * x
}
```

## week4 : CALCULATE SD IN MATH PACKAGE

```go

package main

import (
	"fmt"
	"math"
)

func main() {
	var num [10]float64
	var sum, mean, sd float64
	fmt.Println("******* Enter 10 elements *******")
	for i := 1; i <= 10; i++ {
		fmt.Printf("Enter %d element : ", i)
		fmt.Scan(&num[i-1])
		sum += num[i-1]
	}
	mean = sum / 10

	for j := 0; j < 10; j++ {
		sd += math.Pow(num[j]-mean, 2)

	}
//the use of sqrt math function func sqrt(x float64)
	sd = math.Sqrt(sd / 10)
	fmt.Println("The Standard Deviation is : ", sd)
}
```
## week5 : PRINT FLOYD'S TRIANGLE

```go

package main

import "fmt"

func main() {
	var rows int
	var temp int = 1
	fmt.Println("Enter number of rows:")
	fmt.Scanln(&rows)
	for i := 1; i <= rows; i++ {
		for k := 1; k <= i; k++ {
			fmt.Printf("%d ", temp)
			temp++
		}
		fmt.Println(" ")

	}

}

```
## week6 : ADDITION OF TWO STRINGS

```go

package main

import "fmt"

func main() {
	fmt.Print("enter first string")
	var first string
	fmt.Scanln(&first)
	fmt.Print("enter second string ")
	var second string
	fmt.Scanln(&second)
	fmt.Print(first + second)
}

```

## week7 : CHECK WHETHER A STRING IS A PALINDROME OR NOT 

```go
package main
import "fmt"
func main(){
var number, remainder, temp int
var reverse int=10
fmt.Print("Enter any positive integer:")
fmt.Scan(&number)
temp=number
for{
remainder=number%10
reverse=reverse*10 + remainder
number%10
if(number==0){
break
}
}
if(temp==reverse){
fmt.Printf("%d is a palindrome",temp)
}
else
{
fmt.Printf("%d is not a palindrome",)
}
}
```
## week8 : build a contact form 

```html
#form.html
<!DOCTYPE html>
<html>
<head>
<title> Simple Form Example </title>
</head>
<body>
<h2> Submit Form </h2>
<form action="/" method="post">
<label for="name"> Name:</label><br>
<input type="text" id="name" name="name" required> <br><br>

<label for="email"> Email:</label><br>
<input type="email" id="email" name="email" required> <br><br>

<label for="email"> Message:</label><br>
<input type="Message" id="Message" name="Message" required> <br><br>

<input type="reset" value="reset">
<input type="submit" value="Submit">
</form>
</body>
</html>
```
```go
package main
import (
	"fmt"
	"net/http"
)
func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		if r.Method != http.MethodPost {
			http.ServeFile(w, r, "form.html")
			return
		}
		r.ParseForm() // Parse form data
		name := r.Form.Get("name")
		email := r.Form.Get("email")
		fmt.Println("Name:", name)
		fmt.Println("Email:", email)

		fmt.Fprintf(w, "Received form submission\nName: %s\nEmail: %s\n", name, email)
	})
	fmt.Println("Server is running on localhost:8080")
	http.ListenAndServe(":8080", nil) // Corrected port specification
}
```

## week9 : CHECK WHETHER A STRING IS PALINDROME OR NOT

```go

package main 
import "fmt" 
func main(){
var num[100] int 
var temp,sum,avg int
fmt.Print("Enter number of elements: ") 
fmt.Scanln(&temp)
for i := 0; i < temp; i++ { 
fmt.Print("Enter the number : ") 
fmt.Scanln(&num[i])
sum += num[i]
}
avg = sum/temp
fmt.Printf("The Avg %d number(s) is %d",temp,avg)
}

```

## week 10: delete duplicate element in array
```go
package main
import "fmt"

func removeDuplicate(arr[8]int) []int {
map_var := map[int]bool{}
	result := []int{}
	for e := range arr {
		if map_var[arr[e]] != true {
		   map_var[arr[e]] = true
		   result = append(result,arr[e])
		}
	}
	return result
}
func main() {
   arr := [8]int{1,2,2,4,4,5,7,5}
   fmt.Println("The unsorted array entered is:", arr)
   result := removeDuplicate(arr)
   fmt.Println("Thr array obtained after removing the duplicate values is:", result)
}
```

## week 11: reverse array sort for integers and strings

```go
package main
import ("fmt"
"sort"
)
func main(){
fmt.Println("Integer Reverse sort")
num:=[]int { 50,20,10,35,62}
sort.Sort(sort.Reverse(sort.IntSlice(num)))
fmt.Println(num)
fmt.Println("String Reverse Sort")
text:=[] string{"India", "Australia", "Japan", "Germany"}
sort.Sort(sort.Reverse(sort.StringSlice(text)))
fmt.Println(text)
}
```
## week12: contains, contains any, count, equal fold string functions

```go
package main
import (
"fmt"
"strings"
)
func main(){
fmt.Println(strings.ContainsAny("Germany","G"))
fmt.Println(strings.ContainsAny("Germany","g"))
fmt.Println(strings.Contains("Germany","Ger"))
fmt.Println(strings.Contains("Germany","ger"))
fmt.Println(strings.Contains("Germany","er"))
fmt.Println(strings.Count("cheese","e"))
fmt.Println(strings.EqualFold("Cat","cAt"))
fmt.Println(strings.EqualFold("India","Indiana"))
}
```

## week 14: create multiple go routines 

```
package main
import (
	"fmt"
	"runtime"
	"sync"
)
func main() {
	runtime.GOMAXPROCS(3)
	var processTest sync.WaitGroup
	processTest.Add(3)
	
	go func() {
		defer processTest.Done()
		for i := 0; i < 3; i++ {
			for j := 15; j <= 25; j++ {
				fmt.Printf(" %d", j)
				if j == 18{
					fmt.Println()
				}
			}
		}
	}()

	go func() {
		defer processTest.Done()
		for j := 0; j < 3; j++ {
			for char := 'A'; char < 'A'+10; char++ {
				fmt.Printf("%c ", char)
				if char == 'F' {
					fmt.Println()
				}
			}
		}
	}()

	go func() {
		defer processTest.Done()
		for i := 0; i < 3; i++ {
			for j := 0; j <= 15; j++ {
				fmt.Printf(" %d", j)
				if j == 10 {
					fmt.Println()
				}
			}
		}
	}()
	processTest.Wait()
}
```
