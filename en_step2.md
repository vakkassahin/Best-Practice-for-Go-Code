## Scenario 2: Use Pointers to Modify Values

### Objective: Use pointers to modify values and avoid copying large data structures.

**Scenario**: Imagine that you're developing a Go application that calculates the average of a list of numbers. Your application contains the following code:

Let's create the page named "pointers.go" in the vim editor.

`vim pointers.go`

```
package main

import "fmt"

func main() {
numbers := []float64{1, 2, 3, 4, 5}
average := calculateAverage(numbers)
fmt.Printf("The average of the numbers %v is %v.\n", numbers, average)
}

func calculateAverage(numbers []float64) float64 {
var sum float64
for \_, number := range numbers {
sum += number
}
return sum / float64(len(numbers))
}
```

This code calculates the average of a list of numbers. However, it copies the entire list of numbers when passing it to the calculateAverage function. This can be inefficient if the list is large. To avoid copying the list, you can use a pointer to the list:

```
package main

import "fmt"

func main() {
	numbers := []float64{1, 2, 3, 4, 5}
	average := calculateAverage(&numbers)
	fmt.Printf("The average of the numbers %v is %v.\n", numbers, average)
}

func calculateAverage(numbers *[]float64) float64 {
	var sum float64
	for _, number := range *numbers {
		sum += number
	}
	return sum / float64(len(*numbers))
}

```

You can save this code in a file named pointers.go, and then execute it in a terminal screen using the go run command:

`go run pointers.go`
This code uses a pointer to the list of numbers in the calculateAverage function. This avoids copying the list and improves the efficiency of the code. Additionally, the \* operator is used to dereference the pointer and access the underlying list in the function.
