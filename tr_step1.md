## Senaryo 1: Kodu Tekrar Kullanmak İçin Struct Gömülmesi Kullanma

#### Struct gömülmesini kullanarak kodu tekrar kullanmak ve tekrarlamadan kaçınmak.

**Senaryo**: Farklı izinlere sahip farklı kullanıcı türleri oluşturmayı içeren bir Go uygulaması geliştiriyorsunuz. Kodun yeniden kullanılabilir ve tekrarlanmasını önleyen bir şekilde yazmak istiyorsunuz.

Bunu başarmak için, struct gömülmesini kullanabilirsiniz. Tüm kullanıcı türleri için ortak olan alanları içeren bir User struct tanımlayabilirsiniz:
Öncelikle Go'yu kurmamız gerekiyor.

`apk add go`

Sayfaları oluştururken "Vim Editörü" kullanacağız. Kısayollara hızlıca göz atalım.

:q = Değişiklikler kaydedilirse Vim editörünü kapatır. Aksi takdirde sizi uyarır.

:q! = Değişiklikleri kaydetmeden doğrudan editörü kapatır.

:w = Yapılan değişiklikleri kaydeder.

:wq = Yapılan değişiklikleri kaydeder ve çıkar.

Ardından, vim editöründe "struct.go" adlı ilk sayfayı oluşturalım.

`vim struct.go`

Açılan sayfada çalışabilmek için "Insert Mode"u etkinleştirmek için "i" tuşuna basarak sayfaya çalışmak istediğimiz kodu yazalım.

```
package main

type User struct {
ID int
Name string
Email string
}
```

Daha sonra, User struct'ı gömülen ve her kullanıcı türü için özgü alanlar eklenen diğer struct'ları tanımlayabilirsiniz. Örneğin, User struct'ı gömülen ve IsAdmin alanı eklenen bir Admin struct'ı tanımlayan kod burada yer almaktadır:

```
package main

import "fmt"

type User struct {
ID int
Name string
Email string
}

type Admin struct {
User
IsAdmin bool
}

func main() {
user := User{ID: 1, Name: "Vakkas Sahin", Email: "vakkas.sahin@example.com"}
admin := Admin{User: user, IsAdmin: true}
fmt.Printf("User: %+v\n", user)
fmt.Printf("Admin: %+v\n", admin)
}
```

Bu kod, User struct'ını gömülen ve IsAdmin alanı eklenen bir Admin struct'ı tanımlar. Ayrıca, bir User struct ve bir Admin struct oluşturan ve tüm alanların ve değerlerinin gösterildiği %+v format verb'ini kullanarak bu struct'ların değerlerini yazdıran bir main() fonksiyonu da içerir.

Bu kodu struct.go adlı bir dosyada kaydedebilir ve ardından go run komutunu kullanarak bir terminal ekranında çalıştırabilirsiniz:

`go run struct.go`

```
User: {ID:1 Name:Vakkas Sahin Email:vakkas.sahin@example.com}
Admin: {User:{ID:1 Name:Vakkas Sahin Email:vakkas.sahin@example.com} IsAdmin:true}
```

Bu şekilde yapılandırılmış olan yapısal gömülme (struct embedding), kodunuzu daha yeniden kullanılabilir ve tekrarlamayı önleyici hale getirir. Temel bir yapıda ortak alanları ve davranışları tanımlayabilir ve bu yapıyı diğer yapıların içinde gömerek kodu yeniden kullanılabilir hale getirebilirsiniz. Bu, kodunuzu okuması, yazması ve bakımı daha kolay hale getirebilir.

Bir sonraki örnekle devam edebiliriz.
