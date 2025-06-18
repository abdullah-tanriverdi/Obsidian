#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 


**State Nedir?**

State, bir veri parçasıdır. Bu veri değişirse, ona bağlı olan ekranlar otomatik olarak güncellenir.

Jetpack Compose’da arayüzün (UI), veriye göre otomatik olarak değişmesini istiyoruz.  
Yani veri (state) değiştiğinde, ekran yeniden çizilsin istiyoruz.

Compose’ta her şey “state’e tepki verir” şekilde çalışır.


```kotlin
@Composable
fun SayaçEkranı() {
    var sayac by remember { mutableStateOf(0) }

    Column {
        Text("Sayaç: $sayac")
        Button(onClick = { sayac++ }) {
            Text("Arttır")
        }
    }
}

```
✅ `sayac` adında bir state tanımladık  
✅ Butona basınca `sayac++` oldu  
✅ `Text()` otomatik olarak yeniden çizildi


> `remember`, Compose’un “bu değeri ekran yeniden çizilse bile hatırla” demesidir.


```kotlin
val sayac = mutableStateOf(0)

```

Bu yapı bir **observable state** üretir.  
Yani: “Beni biri kullanıyorsa ve ben değişirsem, onu da uyar.”

```kotlin
var sayac by remember { mutableStateOf(0) }

```
Bu `by` sayesinde, `.value` yazmamıza gerek kalmaz:

- `sayac.value` yerine `sayac`
    
- `sayac.value++` yerine `sayac++`


**State Hoisting**
**❌ Kötü Kullanım (Composable içinde state tutmak)**
```kotlin
@Composable
fun ToggleSwitch() {
    var acik by remember { mutableStateOf(false) }

    Switch(checked = acik, onCheckedChange = { acik = it })
}

```

Bu durumda dışarıdan müdahale edemeyiz

**✅ İyi Kullanım (State yukarıda)**
```kotlin
@Composable
fun AnaEkran() {
    var acik by remember { mutableStateOf(false) }

    ToggleSwitch(acik, onToggle = { acik = it })
}

@Composable
fun ToggleSwitch(acik: Boolean, onToggle: (Boolean) -> Unit) {
    Switch(checked = acik, onCheckedChange = onToggle)
}

```
Bu teknik: **State Hoisting**  
Yani: state’i yukarı taşı, mantığı yukarıda tut, UI’yi sadece göster.



|Fonksiyon|Ne Zaman Kullanılır?|
|---|---|
|`remember`|UI yeniden çizilse bile hatırlar|
|`rememberSaveable`|Uygulama dönse bile (örneğin rotate) hatırlar|
```kotlin
var ad by rememberSaveable { mutableStateOf("") }

```



```kotlin
val kelimeSayisi by remember {
    derivedStateOf { metin.split(" ").size }
}

```
Bir state başka bir state’ten türetiliyorsa `derivedStateOf` kullanabilirsin. Performans için faydalı.


|Araç|Ne işe yarar?|
|---|---|
|`remember`|Composable içinde hafızada tutar|
|`mutableStateOf`|Değişebilir veri oluşturur|
|`rememberSaveable`|Ekran döndüğünde bile hatırlar|
|`State Hoisting`|Durumu yukarı taşır|
|`derivedStateOf`|Başka state'ten türetilmiş değer|

---

***Abdullah TANRIVERDİ***

