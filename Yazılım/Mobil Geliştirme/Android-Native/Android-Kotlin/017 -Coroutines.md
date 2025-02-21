#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 

![[Pasted image 20250216232125.png]]


Coroutines, Kotlin'in asenkron işlemleri yönetmek için sunduğu **hafif** iş parçacıklarıdır. Geleneksel iş parçacıklarına (Threads) göre daha verimli ve yönetimi kolaydır.

✅ **Ana Thread’i (UI) Bloklamadan** Asenkron Çalışma  
✅ **Lightweight (Hafif) Thread’ler** – 1000’lerce coroutine çalıştırabilirsiniz  
✅ **Structured Concurrency (Yapısal Eşzamanlılık)** – Tüm işlemler belirli bir kapsamda yönetilir  
✅ **Suspend Fonksiyonlar** – Bloklamadan duraklatma ve devam ettirme


==**Coroutines Bağımlılığını Eklemek**==
```kotlin
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.6.4")
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.6.4")
}

```


==**Coroutines Temel Yapısı**==  
Coroutines başlatmak için aşağıdaki kapsamları (Scopes) kullanırız:

🔹 `GlobalScope.launch {}`
Tüm uygulama ömrü boyunca çalışan bir coroutine başlatır (genellikle önerilmez).
```kotlin
import kotlinx.coroutines.*

fun main() {
    GlobalScope.launch {
        delay(1000L)
        println("Coroutines ile Asenkron İşlem")
    }
    println("Ana İşlem")  
    Thread.sleep(2000L) // Ana thread kapanmasın diye bekletiyoruz
}
//Ana İşlem
//Coroutines ile Asenkron İşlem


```
✅ `delay(1000L)`: Coroutines’te beklemeyi sağlar (Thread.sleep yerine kullanılır).  
✅ `GlobalScope.launch {}` ile yeni bir coroutine başlatıldı.

🔹`runBlocking {}` **– Ana Thread’i Bekletme**
`runBlocking {}` tüm coroutine işlemleri bitene kadar **ana thread’i bloklar**.
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("Coroutine İçinde Çalışıyorum")
    }
    println("Ana Thread Bloklandı")
}

//Ana Thread Bloklandı
//Coroutine İçinde Çalışıyorum


```

✅ `runBlocking {}` içinde coroutine çalışır ve tamamlanmadan `main` fonksiyon bitmez.

🔹 `CoroutineScope.launch {}` **– Yapısal Eşzamanlılık**
Önerilen yöntem `CoroutineScope` kullanmaktır.
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job = launch {
        delay(1000L)
        println("Coroutine Bitti")
    }
    println("Ana Thread Devam Ediyor")
    job.join() // Coroutine bitene kadar bekletiyoruz
}

//Ana Thread Devam Ediyor
//Coroutine Bitti


```
✅ `launch {}` içinde coroutine çalışır.  
✅ `job.join()` ile coroutine’in tamamlanmasını bekleyebiliriz


`suspend` **Fonksiyonlar (Asenkron Çalışma)**
Suspend fonksiyonlar, coroutine içinde **bloklamadan duraklatma ve devam ettirme** yeteneği sağlar.
```kotlin
import kotlinx.coroutines.*

suspend fun fetchData() {
    delay(2000L)
    println("Veri Alındı")
}

fun main() = runBlocking {
    fetchData()
    println("İşlem Tamamlandı")
}

//Veri Alındı 
//İşlem Tamamlandı

```
✅ `fetchData()` coroutine içinde çağrılmalıdır.  
✅ `suspend` fonksiyonlar sadece coroutine içinde çalışabilir.


==**Coroutine Dispatcher – İş Parçacığı Yönetimi**==
Coroutines farklı **Dispatcher** kullanarak farklı iş parçacıklarında çalışabilir.

| **Dispatcher**           | **Açıklama**                                        |
| ------------------------ | --------------------------------------------------- |
| `Dispatchers.Default`    | CPU yoğun işlemler için (paralel çalışır).          |
| `Dispatchers.IO`         | Ağ veya disk işlemleri için (arka planda çalışır).  |
| `Dispatchers.Main`       | UI işlemleri için (Android’de ana thread).          |

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch(Dispatchers.Default) {
        println("Default Dispatcher: ${Thread.currentThread().name}")
    }
    launch(Dispatchers.IO) {
        println("IO Dispatcher: ${Thread.currentThread().name}")
    }
    launch(Dispatchers.Main) { // Android'de kullanılır
        println("Main Dispatcher: ${Thread.currentThread().name}")
    }
}

```

**Çıktı**
```yaml
Default Dispatcher: DefaultDispatcher-worker-1
IO Dispatcher: DefaultDispatcher-worker-2
Main Dispatcher: main

```


`async {}` ve `await()` **– Paralel Çalışma**
Coroutines, `async` ile **paralel işlemler** yapabilir.
```kotlin
import kotlinx.coroutines.*

suspend fun fetchData1(): String {
    delay(2000L)
    return "Veri 1"
}

suspend fun fetchData2(): String {
    delay(3000L)
    return "Veri 2"
}

fun main() = runBlocking {
    val data1 = async { fetchData1() }
    val data2 = async { fetchData2() }

    println("Sonuç: ${data1.await()} ve ${data2.await()}")
}

//Sonuç: Veri 1 ve Veri 2

```
✅ `async {}` işlemleri **paralel olarak başlatır**.  
✅ `await()` ile sonucu bekleyerek alırız.

`withContext {}` **– Farklı Dispatcher’a Geçiş**
Bir işlem sırasında farklı bir iş parçacığına geçiş yapmak için kullanılır.
```kotlin
import kotlinx.coroutines.*

suspend fun fetchData(): String {
    return withContext(Dispatchers.IO) {
        delay(2000L)
        "Veri Alındı"
    }
}

fun main() = runBlocking {
    val result = fetchData()
    println(result)
}

```

✅ `withContext(Dispatchers.IO) {}` ile **IO iş parçacığında** çalıştırılır.



**Sonuç**

✅ Coroutines **hafif ve verimli** asenkron işlemler sağlar.  
✅ **`launch {}` ve `async {}`** farklı amaçlar için kullanılır.  
✅ **`suspend` fonksiyonlar** coroutine içinde çalışır.  
✅ **`Dispatchers.IO`, `Dispatchers.Default`, `Dispatchers.Main`** ile iş parçacığı yönetilir.  
✅ **`async {}` ve `await()`** ile paralel işlemler yapılabilir.  
✅ **`withContext {}`** ile farklı dispatcher’a geçiş yapılır.




---
***Abdullah TANRIVERDİ***