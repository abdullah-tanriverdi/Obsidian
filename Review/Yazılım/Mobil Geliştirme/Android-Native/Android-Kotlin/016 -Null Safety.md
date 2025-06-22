#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 


Kotlin’de **Null Safety (Null Güvenliği)**, **`NullPointerException (NPE)` hatalarını önlemek için** geliştirilen bir sistemdir.
- Kotlin'de bir değişken varsayılan olarak `null` olamaz
- Eğer bir değişken `null` olabilir ise bunu açıkça belirtmemiz lazım

==**1. Nullable ve Non-Nullable Değişkenler**==
Kotlin’de bir değişkenin `null` olup olmayacağını açıkça belirtmemiz gerekir.

```kotlin
var name: String = "Ahmet"
name = null // HATA! String null olamaz.

```
✔ Varsayılan olarak değişkenler `null` olamaz.

```kotlin
var name: String? = "Ahmet"
name = null // HATA YOK! Çünkü `?` ile nullable yaptık.

```
✔ `String?` → Bu değişken `null` olabilir.


==**2. Null Kontrolleri ve Operatörler**==

- **Safe Call (?.) - Null Kontrollü ile Güvenli Erişim**
```kotlin
var name: String? = "Mehmet"

println(name?.length) // Çıktı: 6

name = null
println(name?.length) // Çıktı: null (Hata vermez!)

```

✔ `?.` operatörü değişken null ise işlemi atlar ve `null` döner.


- **Elvis Operatörü (?:) - Null Durumunda Varsayılan Değer Kullanma**
```kotlin
var name: String? = null

val length = name?.length ?: 0 // Eğer name null ise 0 döner.
println(length) // Çıktı: 0

```

✔ Eğer `name` null ise, `?:` operatörü ile varsayılan değer atanır.

- **!! Operatörü - Null Olmadığını Zorla Kabul Etme**
```kotlin
var name: String? = null

println(name!!.length) // HATA! NullPointerException (NPE) verir.

```

✔ `!!` kullanımı tehlikelidir, çünkü değişken `null` olursa hata alırız.


==**3. `let` ile Null Kontrolü**==

```kotlin
var email: String? = "test@example.com"

email?.let {
    println("E-posta: $it") // Eğer null değilse çalışır
}

```
✔ `?.let {}` sayesinde `null` olmayan durumlarda işlemi çalıştırabiliriz.


==**4. Safe Casting (`as?`)**==

Eğer bir nesne belirli bir türde değilse, hata almamak için güvenli dönüştürme kullanabiliriz.
```kotlin
val obj: Any = "Merhaba"
val str: String? = obj as? String

println(str) // Çıktı: Merhaba

```
✔ `as?` → Eğer dönüşüm başarısız olursa `null` döner, hata vermez.


---

***Abdullah TANRIVERDİ***

