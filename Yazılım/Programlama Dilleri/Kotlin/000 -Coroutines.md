#Yazılım #PD #Kotlin 

![[Pasted image 20250216232125.png|500]]
Coroutines, Kotlin'in asenkron işlemleri yönetmek için sunduğu **hafif** iş parçacıklarıdır. Geleneksel iş parçacıklarına (Threads) göre daha verimli ve yönetimi kolaydır.


==**Coroutine vs. Thread Farkı**==

|**Özellik**|**Coroutine** 🌀|**Thread** 🧵|
|---|---|---|
|**Bağımsız mı?**|Hayır, belirli bir thread'e bağlı değil|Evet, belirli bir thread’e bağlı|
|**Askıya alınabilir mi?**|Evet, `suspend` fonksiyonlarla askıya alınabilir|Hayır, durursa yeniden başlatılamaz|
|**Thread bloklar mı?**|Hayır, aynı thread’i başka işlemler için kullanabilir|Evet, bir işlemi bitirene kadar thread kullanılamaz|
|**Kaynak tüketimi?**|Hafif (lightweight), düşük bellek tüketimi|Ağır, fazla bellek tüketimi|

```kotlin
fun main() = runBlocking { // CoroutineScope sağlıyor
    launch { // Yeni bir coroutine başlatılıyor
        delay(1000L) // 1 saniye bekle (bloklamaz)
        println("World!") // Bekledikten sonra yazdır
    }
    println("Hello") // Ana coroutine devam ederken önce bu yazdırılır
}

```

```nginx
//Çıktı
Hello
World!

```


```kotlin
runBlocking {
    launch { delay(1000L); println("World!") }
    println("Hello")
}

```
Bu kodda `runBlocking` şu işleri yapar:
- Ana thread'i bekletir, tüm coroutine'lerin tamamlanması sağlar.
- Kod `runBlocking` bloğu tamamlanana kadar devam etmez.


Koddan `runBlocking` çıkarılırsa hata alırız
```kotlin
fun main() {
    launch { // HATA: CoroutineScope yok!
        delay(1000L)
        println("World!")
    }
    println("Hello")
}

```
**Hata:** `Unresolved reference: launch`

- `launch`, CoroutineScope içinde tanımlanmalıdır
- `runBlocking` veya başka bir CoroutineScope kullanılmazsa, coroutine başlatılmaz

`runBlocking` Neden Kullanılı
- `runBlocking` ana threadi bekleterek coroutinelerin tamamlanmasını sağlar
- Gerçek projelerde genellikle kullanılmaz, çünkü thread'i gereksiz yere bloklar
- Alternatif olarak `coroutineScope{}` kullanılabilinir
```kotlin
suspend fun doWorld() = coroutineScope {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello")
}

```
- `coroutineScope{}` threadi bloklamaz, sadece coroutinei askıya alır.


==**Structured Concurrency (Yapısal Eşzamanlılık)**== 

 Yapısal Eşzamanlılık Nedir?
- Tüm coroutine'ler bir `CoroutineScope` içinde başlatılır.
- Bir scope tamamlanmadan içindeki coroutine'ler tamamlanamaz.
- Çocuk coroutine'ler, ebeveyn coroutine tamamlanana kadar çalışmaya devam eder.
- Hata yönetimi daha güvenlidir, çünkü hata olursa tüm scope etkilenir ve kontrol kaybolmaz.


Neden Structured Concurrency Kullanmalıyız?
Gerçek bir uygulamada, birçok coroutine başlatılır. Eğer bu coroutine’ler bir scope içinde tutulmazsa:

- Kaybolabilirler (Leak oluşabilir).
- Yaşam döngüsü kontrolü zorlaşır.
- Hata yönetimi karmaşık hale gelir.

Kotlin’in Structured Concurrency prensibi, bu sorunları otomatik olarak engeller.

```kotlin
fun main() = runBlocking {
    launch { 
        delay(1000L) 
        println("World!") 
    }
    println("Hello")
}

```

Burada launch içinde `delay(1000L)` ve `println("World!")` kodları doğrudan yazılmış.  
Bunu refaktör (iyileştirme) edip bir fonksiyona taşıyalım.

```kotlin
fun main() = runBlocking { 
    launch { doWorld() } // Yeni fonksiyon çağırılıyor
    println("Hello")
}
​
// Yeni suspend fonksiyon
suspend fun doWorld() {
    delay(1000L)
    println("World!")
}

```

**Ne Değişti?** ✅ `launch` içinde doğrudan kod yazmak yerine `doWorld()` adında bir suspend fonksiyon çağırıyoruz.  
✅ `doWorld()` içinde `delay(1000L)` ve `"World!"` yazdırma işlemi yapılıyor.  
✅ Kod daha okunabilir ve düzenli hale geliyor.

**Suspend Fonksiyonun Özellikleri**

- Yalnızca coroutine içinde çağrılabilir. (`launch`, `runBlocking` vb.)
- Diğer suspend fonksiyonları çağırabilir. (Örn: `delay()`)
- Coroutine'i askıya alabilir (suspend).
- Thread’i bloklamadan çalışır.


==**`coroutineScope` Nedir?**==
- Bir coroutine'in içinde yeni bir scope oluşturur.
- Tüm başlatılan coroutine'lerin tamamlanmasını bekler.
- Thread’i bloklamaz, sadece suspend eder.


**`runBlocking` vs `coroutineScope`**

|Özellik|`runBlocking`|`coroutineScope`|
|---|---|---|
|**Thread'i bloklar mı?**|✅ Evet, thread bloklanır|❌ Hayır, sadece coroutine askıya alınır|
|**Bir coroutine scope oluşturur mu?**|✅ Evet|✅ Evet|
|**Fonksiyon türü**|Normal fonksiyon|Suspend fonksiyon|
|**Kullanım amacı**|Coroutine dışındaki kodla köprü kurmak|Coroutine içinde yeni bir scope açmak|

```kotlin
fun main() = runBlocking { 
    doWorld()
}
​
// coroutineScope kullanarak yeni bir scope oluşturuyoruz
suspend fun doWorld() = coroutineScope {  
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello")
}

```

```kotlin
Hello
World!

```
1️⃣ `runBlocking` başlar.  
2️⃣ `doWorld()` çağrılır.  
3️⃣ `coroutineScope` başlar ve bir coroutine başlatılır (`launch {}` içinde).  
4️⃣ Ana kod `"Hello"` yazdırır.  
5️⃣ `launch {}` içindeki coroutine **1 saniye bekler** (`delay(1000L)`).  
6️⃣ `"World!"` yazdırılır.

📌 Burada `coroutineScope`, içinde başlatılan coroutine tamamlanmadan sona ermiyor.


==**`Job`Nedir?**== 
`Job`, başlatılan coroutine’in durumunu takip etmek ve gerektiğinde beklemek (join), iptal etmek (cancel) gibi işlemleri yapmak için kullanılır.

**`Job.join()` Kullanımı**
```kotlin
fun main() = runBlocking { 
    val job = launch { // Yeni bir coroutine başlat ve referansını sakla
        delay(1000L)
        println("World!")
    }
    println("Hello")
    job.join() // job tamamlanana kadar bekle
    println("Done") 
}

```
```nginx
Hello
World!
Done

```
1️⃣ `runBlocking` başlar.  
2️⃣ **Bir coroutine başlatılır (`launch {}`), bu coroutine `job` değişkenine atanır.**  
3️⃣ `"Hello"` yazdırılır (çünkü `launch` içindeki coroutine gecikmeli çalışır).  
4️⃣ `job.join()` çağrıldığı için, ana coroutine **alt coroutine tamamlanana kadar bekler.**  
5️⃣ **1 saniye sonra** `"World!"` yazdırılır.  
6️⃣ `"Done"` yazdırılır.


`Job` nesnesi aşağıdaki işlemler için kullanılabilir

|**İşlem**|**Açıklama**|
|---|---|
|`job.join()`|Coroutine’in tamamlanmasını bekler.|
|`job.cancel()`|Coroutine’i iptal eder.|
|`job.isActive`|Coroutine’in çalışıp çalışmadığını kontrol eder.|
|`job.isCompleted`|Coroutine’in tamamlanıp tamamlanmadığını kontrol eder.|
|`job.isCancelled`|Coroutine’in iptal edilip edilmediğini kontrol eder.|

==**Coroutine'ler Neden Hafiftir?**==
Coroutine'ler, JVM'deki `Thread` yapısına kıyasla çok daha az bellek tüketir ve hafiftir.  
Eğer aynı işlemi `Thread` kullanarak yapmaya çalışırsak, sistem kaynaklarını hızla tüketebiliriz.
**50.000 Coroutine Başlatma Örneği**
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    repeat(50_000) { // 50.000 coroutine başlat
        launch {
            delay(5000L)
            print(".")
        }
    }
}

```
Bu kod, 50.000 farklı coroutine başlatır.  
Her biri 5 saniye bekler (`delay(5000L)`) ve ardından `.` karakterini yazdırır.
```nginx
..................................................................

```

Örneğin, aynı işlemi thread ile yaparsak:
**50.000 Thread Başlatma Örneği**
```kotlin
import kotlin.concurrent.thread

fun main() {
    repeat(50_000) {
        thread {
            Thread.sleep(5000L)
            print(".")
        }
    }
}

```
- Her thread, çok fazla bellek tüketir.
- Sistem hızla "OutOfMemoryError" hatası verebilir.
- Thread başlatma süresi uzayabilir.
- Thread'ler arası geçiş (context switch) pahalıdır.


==**`async` Yapısı**==

`async`, bir coroutine başlatır ve bir değer döndürür. Bu, başka bir coroutine'den sonuç almak için kullanılabilir. `await` fonksiyonu ile sonucu alabilirsiniz.
```kotlin
val result = async {
    // Uzun süren bir hesaplama
    return@async 42
}
println("Result: ${result.await()}")

```



==**CoroutineContext ve Dispatcher'lar**==

Coroutines, **CoroutineContext** içinde çalışır. Bu context, coroutine'nin hangi iş parçacığında çalışacağını belirler. `Dispatchers` sınıfı, farklı iş parçacıklarında çalışmak için kullanılır.

- `Dispatchers.Main`: Ana iş parçacığında çalışmak için.
- `Dispatchers.IO`: I/O işlemleri için iş parçacığı.
- `Dispatchers.Default`: Arka planda çalışan default iş parçacığı.


==**Channels ve Verilerin Paylaşılması**==

Channels, coroutines arasında veri paylaşmak için kullanılan yapılar olup, verilerin güvenli bir şekilde aktarılmasına yardımcı olur. Bu, coroutines'in birbirine veri göndermesini sağlar.
Channels, tıpkı bir **Queue** (kuyruk) gibi çalışır, ancak coroutines arasında asenkron veri iletimi sağlamak için optimize edilmiştir. Bu yapı, verilerin yalnızca bir coroutine'den diğerine gönderilmesini sağlar, yani bir coroutine bir veriyi gönderirken, alıcı coroutine bunu almak için hazır olana kadar bekler.

 **Channel Nasıl Çalışır?**

Kanal (Channel) oluşturduğunuzda, iki işlem gerçekleştirebilirsiniz:

1. **send()**: Veriyi kanala gönderir.
2. **receive()**: Kanaldan veri alır.

Bir coroutine bir veriyi **send()** ile kanala gönderdiğinde, **receive()** metoduyla başka bir coroutine bu veriyi alır. Bu iletişim, **asenkron** şekilde yapılır, yani veri gönderme ve alma işlemi, her iki coroutine'in de sırasıyla beklemesi veya devam etmesiyle gerçekleşir.
```kotlin
val channel = Channel<Int>()

launch {
    for (x in 1..5) {
        channel.send(x) // Veri gönder
    }
}

launch {
    repeat(5) {
        println(channel.receive()) // Veriyi al
    }
}

```
**Örnek Açıklama:**

1. İlk **launch** bloğunda, `1`'den `5`'e kadar olan sayılar **channel.send(x)** ile kanala gönderilmektedir.
    
2. İkinci **launch** bloğunda ise, **channel.receive()** metodu ile kanaldan alınan veriler yazdırılmaktadır.
    

Bu işlemde, veriler asenkron bir şekilde iletilir ve ilk coroutine'in gönderdiği veriler, ikinci coroutine tarafından sırasıyla alınır.




==**Coroutine Hata Yönetimi**==

Coroutines, hataları düzgün bir şekilde raporlar ve yönetir. Eğer bir coroutine içinde hata oluşursa, o coroutine `Job` nesnesiyle ilişkili olarak hata verir ve üst scope'a raporlanır.
```kotlin
val job = launch {
    throw Exception("Something went wrong")
}
job.invokeOnCompletion { exception ->
    if (exception != null) {
        println("Error: $exception")
    }
}

```

**SupervisorJob Kullanımı**

**SupervisorJob**, alt coroutine'lerde oluşan hataların, üst coroutine'i etkilemesini engeller. Bu, hataların izole edilmesine ve bir coroutine'in başarısız olmasının diğer coroutine'leri etkilememesine olanak tanır.
```kotlin
val supervisor = SupervisorJob()

val job = CoroutineScope(Dispatchers.Default + supervisor).launch {
    launch {
        throw Exception("Something went wrong in the child coroutine")
    }
    println("This will still run even if the previous coroutine failed")
}

job.invokeOnCompletion { exception ->
    if (exception != null) {
        println("Error: $exception")
    }
}

```

- **`SupervisorJob`** ile coroutine scope'u oluşturulmuştur. Eğer bir alt coroutine (child coroutine) hata alırsa, bu hata sadece o coroutine’i etkiler. Ancak **`SupervisorJob`** sayesinde, **"Bu hala çalışacak"** mesajı yazdırılmaya devam eder.
    
- **`invokeOnCompletion`** callback'inde, **`exception`** parametresi null değilse hata mesajı yazdırılır. Bu, hataların düzgün bir şekilde yakalanmasını sağlar.

<iframe width="560" height="315" src="https://www.youtube.com/embed/e7tKQDJsTGs" frameborder="0" allowfullscreen></iframe>


---
***Abdullah TANRIVERDİ***
