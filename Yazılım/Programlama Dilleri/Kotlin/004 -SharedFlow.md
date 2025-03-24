#Yazılım #ProgramlamaDilleri #Kotlin 

`SharedFlow`, Kotlin Coroutines kütüphanesinde bulunan ve birden çok kolektöre aynı anda veri gönderebilen (hot stream) bir veri akışıdır Yani veri üretimi, bu veriyi toplayan (collect) birisi olmasa bile devam eder.Yani SharedFlow, "Ben buradan bağıracağım, kim duymak istiyorsa dinlesin!" der. Bu özellik, `StateFlow` gibi durumları paylaşmak veya `LiveData` alternatifleri oluşturmak için yaygın olarak kullanılır.

Event Broadcasting

==**Temel Kavramlar**==

| Özellik          | Açıklama                                                                                  |
| ---------------- | ----------------------------------------------------------------------------------------- |
| **Hot Stream**   | Veri akışı başlatıldığında collect eden olmasa bile çalışmaya devam eder.                 |
| **Multicast**    | Birden fazla collector aynı `SharedFlow`’dan veri alabilir.                               |
| **Replay Cache** | Yeni bir subscriber geldiğinde, geçmişteki son `n` değeri tekrar iletebilir (`replay=n`). |
| **Buffering**    | `extraBufferCapacity` parametresi ile buffer büyüklüğü belirlenebilir.                    |
| **Backpressure** | Aşırı veri geldiğinde ne yapılacağı kontrol edilir (drop, suspend, vs.).                  |

**1. Oluşturma**
```kotlin
val sharedFlow = MutableSharedFlow<String>()

```
Buraya `String` türünde mesajlar göndereceğiz.

**2. Veri Gönderme (emit)**
```kotlin
sharedFlow.emit("Merhaba!")

```
Bir şey gönderiyoruz. Ama dikkat: kimse dinlemiyorsa boşa gider.



**3. Veri Dinleme (collect)**
```kotlin
sharedFlow.collect { veri ->
    println("Gelen veri: $veri")
}

```
Gelen her veriyi yakalıyoruz ve yazdırıyoruz.


**Senaryo: Toast Mesajı Gösterme**
ViewModel'den Toast mesajı gönderelim:
```kotlin
val toastFlow = MutableSharedFlow<String>()

fun gösterToast() {
    viewModelScope.launch {
        toastFlow.emit("Merhaba kullanıcı!")
    }
}

```

Fragment’te bu mesajı dinleyip ekranda gösterelim:
```kotlin
lifecycleScope.launchWhenStarted {
    viewModel.toastFlow.collect { mesaj ->
        Toast.makeText(context, mesaj, Toast.LENGTH_SHORT).show()
    }
}

```

Mesaj gönderildiğinde, ekranda "Merhaba kullanıcı!" çıkacak


**Peki Replay Nedir?**

`replay` şu işe yarar:  
"Yeni gelen biri, önceki kaç veriyi duysun?"
```kotlin
val sharedFlow = MutableSharedFlow<String>(replay = 1)

```
Kolektör geldikten sonra bir önceki mesajı da alır.



**Peki extraBufferCapacity Nedir ?**


```kotlin
val flow = MutableSharedFlow<String>(
    replay = 1,
    extraBufferCapacity = 2
)

```
 1 kişilik replay koltuğu var, +2 kişi daha sıraya girebilir.

Toplamda 3 kişi eski mesajları alabilir (1 replay, 2 buffer).


**Peki onBufferOverflow Nedir?**
“Yeni mesaj geldi ama yer yok. Ne yapayım?”
İşte `onBufferOverflow` bu durumda nasıl davranacağını söyler.

|Seçenek|Açıklama|
|---|---|
|`SUSPEND`|Varsayılan. `emit()` bekler, yani durur.|
|`DROP_OLDEST`|En eski mesaj çöpe atılır, yenisi gelir.|
|`DROP_LATEST`|Yeni gelen mesaj çöpe atılır, eski kalanlar kalır.|

```kotlin
val flow = MutableSharedFlow<String>(
    replay = 0,
    extraBufferCapacity = 2,
    onBufferOverflow = BufferOverflow.DROP_OLDEST
)

```
2 kişi sıraya girebilir. Yeni gelen olursa en eskisi düşer.



**Peki subscriptionCount Nedir?**

Bazen kaç kişi seni dinliyor bilmek istersin
```kotlin
flow.subscriptionCount.collect {
    println("Dinleyen kişi sayısı: $it")
}

```
0 ise kimse dinlemiyor. 2 ise 2 kişi `collect` ediyor.


**Peki asSharedFlow() Nedir?**

Sen `emit()` yapacaksın ama başkaları sadece dinlesin istiyorsan:
```kotlin
private val _flow = MutableSharedFlow<String>()
val flow = _flow.asSharedFlow()

```
`flow.emit()` dışarıdan çağrılamaz, sadece sen çağırabilirsin.


| Özellik               | Neden Var?                                     |
| --------------------- | ---------------------------------------------- |
| `replay`              | Gelen kişi önceki veriyi de alsın mı?          |
| `extraBufferCapacity` | Fazla olaylar sıraya girsin mi?                |
| `onBufferOverflow`    | Taşarsa ne yapayım: dur, eskiyi at, yeniyi at? |
| `subscriptionCount`   | Dinleyen var mı, boşuna uğraşma                |
| `asSharedFlow()`      | Dışarı sadece okusun, yazamasın                |

## Gerçek Dünya Benzetmesi:

> Sen bir radyo istasyonusun 
> Replay = “Yayına yeni katılanlara son şarkıyı tekrar çal”  
> Buffer = “Telefonlar yağdı, sıraya koy”  
> Overflow = “Yer kalmadı, ya yeni geleni at ya eskisini”  
> SubscriptionCount = “Radyo açık mı dinleyen var mı?”  
> asSharedFlow() = “Sadece sunucu yayın yapabilir, dinleyici karışamaz”

==**SharedFlow ile StateFlow Arasındaki Farklar**==

|Özellik|SharedFlow|StateFlow|
|---|---|---|
|Son değeri tutar mı?|❌ Hayır (isteğe bağlı)|✅ Evet|
|Ne işe yarar?|Olay göndermek (toast, yönlendirme)|Durumu tutmak (buton açık mı?)|
|Tek kişi mi alır?|Hayır, herkes alabilir|Hayır, ama hep son durumu verir|



---
***Abdullah TANRIVERDİ***














































Ardından bu flow'u sadece `collect` ile dinleyebilirsin:
```kotlin
lifecycleScope.launch {
    sharedFlow.collect { value ->
        println("Yeni değer: $value")
    }
}

```

**Temel Özellikleri**

🔸 `replay`

- Kaç tane önceki yayının tekrar edilmesini istediğimizi belirler.
    
- Kolektör geldiğinde geçmişte yayınlanan `replay` kadar değeri alır.
```kotlin
val sharedFlow = MutableSharedFlow<String>(replay = 2)

```


 🔸`extraBufferCapacity`

- Emit sırasında replay dışı kaç ek öğeye buffer oluşturulacağını belirler.
    
- `emit()` çağrısı, buffer dolu değilse `suspend` olmadan çalışabilir.

```kotlin
val sharedFlow = MutableSharedFlow<String>(
    replay = 1,
    extraBufferCapacity = 2
)

```


🔸 `onBufferOverflow`

- Buffer dolduğunda ne yapılacağını belirler:

|Seçenek|Açıklama|
|---|---|
|`SUSPEND`|Varsayılan. `emit()` beklemeye alınır|
|`DROP_LATEST`|En son emit edilen değer düşer|
|`DROP_OLDEST`|En eski değer düşer, yeniye yer açılır|


==**Örnek Kullanım: Toast Event**==
```kotlin
// ViewModel
val toastEvent = MutableSharedFlow<String>()

fun showToast(msg: String) {
    viewModelScope.launch {
        toastEvent.emit(msg)
    }
}

// Fragment
lifecycleScope.launchWhenStarted {
    viewModel.toastEvent.collect { msg ->
        Toast.makeText(context, msg, Toast.LENGTH_SHORT).show()
    }
}

```