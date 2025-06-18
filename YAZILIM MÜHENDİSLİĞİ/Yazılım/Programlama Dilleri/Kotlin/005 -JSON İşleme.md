#Yazılım #ProgramlamaDilleri #Kotlin 

Kotlin, JSON verilerini işlemek için çok sayıda popüler kütüphane sunmaktadır. Bunlar arasında en yaygın olanlar **Gson**, **Moshi**, ve **Kotlinx Serialization**'dır. Kotlin, JSON verileriyle çalışırken, tip güvenliğini sağlayan araçlar sunarak modern yazılım geliştirme süreçlerini daha kolay hale getirir.


> [!tip] İPUCU
> Json hakkında daha fazla bilgiye erişmek için bağlantıya tıkla [[008 -JSON]]




==**JSON İşleme Kütüphaneleri**==

1. **Gson**
    
2. **Moshi**
    
3. **Kotlinx Serialization**

==**Gson ile JSON İşleme**==

**Gson** Google tarafından geliştirilmiş bir JSON işleme kütüphanesidir. Gson, JSON verisini Kotlin veri sınıflarına ve tam tersine çevirmek için kullanılır.
Kotlin projelerinde Gson kullanabilmek için önce kütüphaneyi projeye dahil etmelisiniz.
```gradle
dependencies {
    implementation 'com.google.code.gson:gson:2.8.8'
}

```

JSON'dan Kotlin Nesnesine Dönüştürme (Deserialization):
```kotlin
import com.google.gson.Gson

data class User(val name: String, val age: Int)

fun parseJson() {
    val json = """{"name": "Alice", "age": 25}"""
    val user = Gson().fromJson(json, User::class.java)
    println(user)
}

```


Kotlin Nesnesinden JSON'a Dönüştürme (Serialization):
```kotlin
fun toJson() {
    val user = User("Alice", 25)
    val json = Gson().toJson(user)
    println(json)
}

```


Gson ile Liste İşleme
```kotlin
data class User(val name: String, val age: Int)

fun parseJsonArray() {
    val json = """[{"name": "Alice", "age": 25}, {"name": "Bob", "age": 30}]"""
    val userList = Gson().fromJson(json, Array<User>::class.java).toList()
    println(userList)
}

```


==**Kotlinx Serialization ile JSON İşleme**==
**Kotlinx Serialization**, JetBrains tarafından geliştirilen ve Kotlin'in resmi JSON işleme kütüphanesidir. Bu kütüphane, Kotlin diline özgü olarak en yüksek uyumlu ve performanslı çözümü sunar.

Kotlinx Serialization Kurulumu
```gradle
plugins {
    id 'kotlinx-serialization' version '1.5.0'
}

dependencies {
    implementation 'org.jetbrains.kotlinx:kotlinx-serialization-json:1.5.0'
}

```


JSON'dan Kotlin Nesnesine Dönüştürme (Deserialization):
```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
data class User(val name: String, val age: Int)

fun parseJson() {
    val json = """{"name": "Alice", "age": 25}"""
    val user = Json.decodeFromString<User>(json)
    println(user)
}

```


Kotlin Nesnesinden JSON'a Dönüştürme (Serialization):
```kotlin
fun toJson() {
    val user = User("Alice", 25)
    val json = Json.encodeToString(user)
    println(json)
}

```

Kotlinx Serialization ile Liste İşleme
```kotlin
fun parseJsonArray() {
    val json = """[{"name": "Alice", "age": 25}, {"name": "Bob", "age": 30}]"""
    val userList = Json.decodeFromString<List<User>>(json)
    println(userList)
}

```


Kotlinx Serialization ile Akışla JSON Okuma:
```kotlin
import kotlinx.serialization.json.*
import kotlinx.coroutines.*
import java.io.File

fun parseLargeJsonFile() = runBlocking {
    val file = File("large_data.json")
    val json = Json { ignoreUnknownKeys = true }
    val stream = file.inputStream()
    
    val data = json.decodeFromStream<Data>(stream)
    println(data)
}

```

Bu yaklaşım, bellekte daha az veri tutarak daha büyük dosyaları verimli bir şekilde okumanızı sağlar.


---

***Abdullah TANRIVERDİ***

