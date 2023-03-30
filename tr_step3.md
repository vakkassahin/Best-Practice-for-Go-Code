**Senaryo 3**: Go'da HTTP Sunucu uygulamasının nasıl oluşturulabileceği konusunda bir örnektir. Bu örnekte, bir HTTP Sunucu oluşturulacak ve kullanıcıların "/hello" endpoint'ine istek göndermeleri durumunda "Hello, BulutBilisimci!" yanıtı dönecektir.

Vim editöründe "http.go" adlı sayfayı oluşturalım.

`vim http.go`

```
package main

import (
	"fmt"
	"net/http"
)

func main() {
	http.HandleFunc("/hello", helloHandler)
	http.ListenAndServe(":8080", nil)
}

func helloHandler(w http.ResponseWriter, r *http.Request) {
	fmt.Fprint(w, "Hello, Bulutbilisimci!")
}

```

Bu kodu çalıştırmak için, bir Go derleyicisine ihtiyacınız vardır. Kodu bir dosyaya kaydedin (örneğin http.go), ardından terminali açın, kodun bulunduğu dizine gidin ve aşağıdaki komutu çalıştırın:

Bu kodu "http.go" adıyla kaydedebilir ve daha sonra terminal ekranında "go run" komutunu kullanarak çalıştırabilirsiniz:

`go run http.go`

Daha sonra, bir web tarayıcısı açın ve adres çubuğuna http://localhost:8080/hello yazın. Bu, tarayıcınıza "Hello, BulutBilisimci!" yazısıyla yanıt veren bir web sayfası gösterecektir.
