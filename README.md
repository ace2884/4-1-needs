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
