**Senaryo 4**: Bu uygulama, kullanıcı tarafından girilen sayıların toplamını hesaplayan bir konsol uygulamasıdır. Uygulamada, yukarıda bahsedilen bazı en iyi uygulama prensipleri de kullanılmaktadır.

Vim editöründe "boolean.go" adlı sayfayı oluşturalım.

`vim boolean.go`

```
package main

import (
"fmt"
"strconv"
)

func main() {
var numbers []int

    for {
    	var input string
    	fmt.Print("Enter a number or 'done' to finish: ")
    	fmt.Scanln(&input)

    	if input == "done" {
    		break
    	}

    	number, err := strconv.Atoi(input)
    	if err != nil {
    		fmt.Println("Invalid input")
    		continue
    	}

    	numbers = append(numbers, number)
    }

    sum := calculateSum(numbers)
    fmt.Println("The sum of the numbers is:", sum)

}

func calculateSum(numbers []int) int {
sum := 0

    for _, number := range numbers {
    	sum += number
    }

    return sum

}
```

Bu kodu çalıştırmak için, bir Go derleyicisine sahip olmanız gerekir. Go derleyicisine sahipseniz, kodu bir dosyaya kaydedin (örneğin boolean.go), ardından terminali açın, kodun bulunduğu dizine gidin ve aşağıdaki komutu çalıştırın:

`go run boolean.go`

Daha sonra, uygulama kullanıcının girdiği sayıların toplamını hesaplayacak ve sonucu konsolda gösterecektir.
