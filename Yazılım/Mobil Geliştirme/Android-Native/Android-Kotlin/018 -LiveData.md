#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 

LiveData, **Android Jetpack** kütüphanesinin bir parçası olan lifecycle-aware (yaşam döngüsüne duyarlı) bir veri konteyneridir. UI bileşenleri ile güvenli ve verimli bir şekilde veri paylaşmak için kullanılır.

✅ **Lifecycle-aware:** Yalnızca aktif (görünür) bileşenlere güncellenmiş veri sağlar.  
✅ **Reactive:** Veriler değiştikçe bağlı bileşenleri otomatik olarak günceller.  
✅ **Memory Leak Önleme:** UI bileşenleri yok olduğunda LiveData, referansları temizler.



 **Gerekli Bağımlılıkları Ekleyelim**
LiveData ve ViewModel’i kullanabilmek için aşağıdaki Jetpack kütüphanelerinin `build.gradle (Module: app)` dosyana eklenecek
```kotlin
dependencies {
    implementation("androidx.lifecycle:lifecycle-livedata-ktx:2.6.2")
    implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.6.2")
}

```


**ViewModel İçinde LiveData Tanımlama**
İlk olarak, bir ViewModel sınıfı oluşturacağız ve içinde LiveData ile bir metin saklayacağız.

```kotlin
class MyViewModel : ViewModel() {
    // Private olarak MutableLiveData tanımlıyoruz
    private val _message = MutableLiveData("Merhaba Jetpack Compose!")
    
    // UI bileşenleri sadece LiveData üzerinden erişebilecek
    val message: LiveData<String> get() = _message

    // Butona tıklanınca mesaj değişsin
    fun updateMessage() {
        _message.value = "Butona tıklandı!"
    }
}

```
✅ `_message` adında MutableLiveData tanımladık.  
✅ UI bileşenleri `_message` değişkenini değiştiremesin diye sadece `message` adında LiveData olarak dışarı açtık.  
✅ `updateMessage()` fonksiyonunu çağırarak mesajı değiştireceğiz.



**Jetpack Compose’da ViewModel ve LiveData Kullanımı**

Şimdi ViewModel’den gelen LiveData’yı UI’de göstereceğiz.

```kotlin
@Composable
fun MyScreen(viewModel: MyViewModel = viewModel()) {
    // LiveData'yı observeAsState ile takip ediyoruz
    val message by viewModel.message.observeAsState("Yükleniyor...")

    Column(
        modifier = Modifier.fillMaxSize(),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        // LiveData’dan gelen mesajı gösteriyoruz
        Text(text = message, fontSize = 24.sp, fontWeight = FontWeight.Bold)

        Spacer(modifier = Modifier.height(16.dp))

        // Butona tıklayınca mesaj değişsin
        Button(onClick = { viewModel.updateMessage() }) {
            Text("Mesajı Güncelle")
        }
    }
}

```
✅ `viewModel()` kullanarak ViewModel’i aldık.  
✅ `observeAsState()` fonksiyonu ile LiveData değişimlerini dinledik.  
✅ Butona tıklanınca updateMessage() fonksiyonunu çağırarak LiveData’yı güncelledik.



**LiveData vs StateFlow Karşılaştırması**

|Özellik|LiveData|StateFlow|
|---|---|---|
|**Lifecycle-aware mi?**|✅ Evet|❌ Hayır|
|**UI otomatik güncellenir mi?**|✅ Evet|✅ Evet|
|**Veri saklanır mı?**|🔸 UI bileşeni yok olursa veri kaybolmaz|✅ Evet|
|**Kullanım alanı**|ViewModel & UI veri akışı|UI state yönetimi|

> [!tip] İPUCU
> StateFlow hakkında bilgi almak için bağlantıya tıkla[[002 -StateFlow]]


|Özellik|Flow|StateFlow|SharedFlow|LiveData|
|---|---|---|---|---|
|Hot/Cold|❄️ Soğuk|🔥 Sıcak|🔥 Sıcak|🔥 Sıcak|
|Son Değeri Tutar mı?|❌ Hayır|✅ Evet|❌ Hayır (replay gerek)|✅ Evet|
|Tek Seferlik mi?|✅ Evet|❌ Hayır|✅ Genelde evet|❌ Hayır|
|UI’ye Bağlı mı?|❌ Hayır|❌ Hayır|❌ Hayır|✅ Lifecycle bağlı|
|Ne İçin Kullanılır?|API, veri üret|UI durumu|Toast, navigasyon|Genel veri gösterimi|


---

***Abdullah TANRIVERDİ***

