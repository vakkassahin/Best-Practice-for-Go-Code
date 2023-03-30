## Senaryo 2: Değerleri Değiştirmek İçin İşaretçileri Kullanma

### Amaç: İşaretçileri kullanarak değerleri değiştirin ve büyük veri yapılarının kopyalanmasından kaçının.

**Senaryo**: Bir sayıların listesinin ortalamasını hesaplayan bir Go uygulaması geliştirdiğinizi hayal edin. Uygulamanız aşağıdaki kodu içerir:

Vim editöründe "pointers.go" adlı sayfayı oluşturalım.

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

Bu kod, bir sayıların listesinin ortalamasını hesaplar. Ancak, listenin tamamını calculateAverage fonksiyonuna geçirirken kopyalar. Liste büyükse bu işlem verimsiz olabilir. Listeyi kopyalamamak için, liste için bir işaretçi kullanabilirsiniz:

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

Bu kodu "pointers.go" adıyla kaydedebilir ve daha sonra terminal ekranında "go run" komutunu kullanarak çalıştırabilirsiniz:

`go run pointers.go`

Bu kod, calculateAverage fonksiyonunda sayılar listesine bir işaretçi kullanır. Bu, listeyi kopyalamayı önler ve kodun verimliliğini artırır. Ayrıca, \* işlemcisi, işaretçiyi çözmek ve fonksiyonda temel liste erişmek için kullanılır.
