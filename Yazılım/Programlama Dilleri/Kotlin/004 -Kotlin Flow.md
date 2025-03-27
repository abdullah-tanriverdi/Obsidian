#Yazılım #ProgramlamaDilleri #Kotlin 

`Flow`, Kotlin'de **veriyi zamanla, adım adım yollamak** için kullanılan bir yapıdır.

 "Bir listeyi anında değil, **yavaş yavaş** göndereyim" dersin.  
 Bunu dinleyen biri de `collect` ederek sırayla bu verileri alır.


```kotlin
fun sayilar(): Flow<Int> = flow {
    emit(1)
    emit(2)
    emit(3)
}

```
Yukarıdaki `flow {}` bloğu, veri üretir ve her `emit()` ile sırayla gönderir.


```kotlin
lifecycleScope.launch {
    sayilar().collect { sayi ->
        println("Gelen sayı: $sayi")
    }
}

```

```perl
Çıktı
Gelen sayı: 1  
Gelen sayı: 2  
Gelen sayı: 3

```

**Flow Soğuktur (Cold)**

Yani `flow {}` bloğu çalışmaz, ta ki biri `collect` edene kadar
```kotlin
val f = flow {
    println("Başlıyorum!")
    emit(1)
}

println("Flow tanımlandı")   // bu çalışır
// f.collect { ... } olmazsa: "Başlıyorum!" asla yazılmaz

```


Flow içinde `delay()` kullanabilirsin çünkü coroutine içinde çalışır:
```kotlin
flow {
    emit("Bir")
    delay(1000)
    emit("İki")
}

```
Her emit arasında 1 saniye beklenir


**Flow Operatorleri (Ara işlemler)**

Flow’lar sadece veri yaymaz, aynı zamanda işlem yapabilir.

- **map**
```kotlin
sayilar().map { it * 2 }

```
> Her gelen veriyi 2 ile çarpar.

- **filter**
```kotlin
sayilar().filter { it % 2 == 1 }

```
> Sadece tek sayıları geçirir.


- **take**
```kotlin
sayilar().take(2)

```
>İlk 2 değeri alır, sonra durur.



**Hatalar (catch) & Tamamlanma (onCompletion)**
```kotlin
flow {
    emit(1)
    throw Exception("Hata oldu")
}.catch { e ->
    println("Hata: $e")
}.onCompletion {
    println("Akış bitti.")
}

```

**Flow vs Suspend Function**

| Özellik            | Suspend Function | Flow               |
| ------------------ | ---------------- | ------------------ |
| Kaç değer döner?   | 1 değer          | Birden fazla       |
| Ne zaman çalışır?  | Çağrılınca       | `collect` edilince |
| Gecikme desteği    | Var              | Var                |
| Ara işlem (map vs) | Yok              | Var                |

<iframe width="560" height="315" src="https://www.youtube.com/embed/6Jc6-INantQ" frameborder="0" allowfullscreen></iframe>

***

***Abdullah TANRIVERDİ***

