#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

==**Temel Anotasyonlar**==

==**@Composable**==

**Açıklama**
- `@Composable` anotasyonu, bir fonksiyonun Compose tarafından UI oluşturmak için kullanılacağını belirtir.
- Compose bileşenleri bu anotasyonn ile işaretlenmelidir.
- UI oluşturacak tüm fonksiyonlarda zorunludur.
```kotlin
@Composable
fun Greeting(name: String){
Text(text="Merhaba: $name")
}
```

==**@Preview**==

**Açıklama**
- Compose bileşenlerinin Android Studio içinde önizlenmesini sağlar.
- Tek başına veya birden fazla versiyon ile kullanılabilir.
- `@Preview` ile farklı ekran boyutlarını ve temalar için bileşenleri test edebiliriz.
```kotlin
@Preview(showBackground = true , name = "Önizleme")
@Composable
fun Greeting(name: String){
Text(text="Merhaba: $name")
}
```

|Parametre|Açıklama|
|---|---|
|`showBackground`|Arka plan ekler (Varsayılan: false)|
|`backgroundColor`|Hex renk koduyla arka plan rengi belirler|
|`name`|Önizleme için özel bir ad tanımlar|
|`widthDp` / `heightDp`|Önizleme penceresi boyutlarını belirler|

==**@Stable**==

**Açıklama**

- Compose'un optimizasyon yapmasın sağlar.
- Eğer bir sınıf içeriği değişmezse `@Stable` eklenerek yeniden oluşturulması engellenir.
- Performansı artırır.
```kotlin
@Stable
data class User(val name : String)
```

- Eğer bir nesne `@Stable` olarak işaretlenmişse, içindeki veriler değişmedikçe recomposition gerçekleşmez.


==**Durum Yönetimiyle İlgili Anotasyonlar**==


==**@Immutable**==

**Açıklama**

- `@Stable` gibi, ancak tamamen değiştirilmez (Immutable) olduğu garantilidir.
-  İçindeki tüm veriler `val ` olmalıdır.
```kotlin
@Immutable
data class UserProfile (val id : Int , val name : String)
```
- Compose, `@Immutable` olarak işaretlenmiş nesneleri asla değiştirmeyeceğini bilir ve performans optimizasyonları yapar.



==**@ReadOnlyComposable**==

**Açıklama**
- Sadece okunabilir Composable fonksiyonları belirtmek için kullanılır.
- Performans optimizasyonu sağlar.
```kotlin
@ReadOnlyComposable
@Composable
fun getStaticText():{
return "Bu metin her zaman aynı kalır"
}
```
- Eğer bir fonksiyon Composable ama değişmeyen bir şey döndürüyorsa, bu anotasyon ile işaretlenebilir.


==**@OptIn**==

**Açıklama**

- Compose'un deneysel (experimental) API'lerini kullanmak için gereklidir.
- Geliştirme aşamasında ki API'leri kullanırken uyumluluk sorunlarnı kabul ettiğimizi belirtir.
```kotlin
@OptIn(ExperimentalComposeUiApi::class)
@Composable
fun ExperimnetalFeature(){
//Deneysel bir API kullanımı
}
```


==**Hilt ve Dependency Injection (DI) İle İlgili Anotasyonlar**==

==**@HiltViewModel**==

**Açıklama**
- Jetpack Compose ile Hilt Dependency Injection kullanırken, ViewModel’lerin Hilt tarafından yönetilmesini sağlar.
```kotlin
@HiltViewModel
class MyViewModel @Inject constructor(
    private val repository: MyRepository
) : ViewModel() {
    // ViewModel iş mantığı
}

```


- Hilt kullanıyorsanız, ViewModel’i Compose içerisinde şu şekilde çağırabiliriz:
```kotlin
@Composable
fun MyScreen(viewModel: MyViewModel = hiltViewModel()) {
    // UI kodları
}

```


==**Test Anotasyonları**==

==**@Test**==

**Açıklama**
- Compose ile UI testleri yazarken `@Test` anotasyonu kullanılır.
```kotlin
@Test
fun myComposableTest() {
    composeTestRule.setContent {
        MyComposable()
    }

    composeTestRule.onNodeWithText("Merhaba Jetpack Compose!").assertExists()
}

```


==**@RunWith(AndroidJUnit4::class)**==

**Açıklama**
- JUnit kullanrak Android testleri çalıştırmak için kullanılır.
```kotlin
@RunWith(AndroidJUnit4::class)
class MyComposeTest {
    // Test metotları
}

```


Jetpack Compose'ta anotasyonlar, Compose'un nasıl çalışacağını belirleyen önemli bileşenlerdir. İşte en önemli anotasyonların kısa özeti:

|Anotasyon|Açıklama|
|---|---|
|`@Composable`|Compose bileşeni olduğunu belirtir.|
|`@Preview`|Android Studio'da önizleme yapmayı sağlar.|
|`@Stable`|Bir nesnenin Compose tarafından optimize edilmesini sağlar.|
|`@Immutable`|Bir nesnenin tamamen değişmez olduğunu belirtir.|
|`@ReadOnlyComposable`|Yan etki oluşturmayan fonksiyonları optimize etmek için kullanılır.|
|`@HiltViewModel`|ViewModel’lerin Hilt DI ile kullanılmasını sağlar.|
|`@Test`|UI testleri yazmak için kullanılır.|
|`@RunWith(AndroidJUnit4::class)`|Testlerin JUnit ile çalışmasını sağlar.|

Bu anotasyonlar, Jetpack Compose'un performansını artırarak daha temiz ve yönetilebilir bir UI kodu yazmamızı sağlar. 

***

***Abdullah TANRIVERDİ***















---

# **Özet ve Kullanım Senaryoları**

|Anotasyon|Kullanım Amacı|
|---|---|
|`@Composable`|UI bileşeni oluşturan fonksiyonları tanımlar|
|`@Preview`|Android Studio'da bileşenleri önizlemek için kullanılır|
|`@Stable`|Değişmeyecek veri yapıları için optimizasyon sağlar|
|`@Immutable`|Kesinlikle değiştirilemez veri yapılarını işaretler|
|`@ReadOnlyComposable`|Salt okunur Compose fonksiyonları için kullanılır|
|`@OptIn`|Deneysel API'leri kullanmak için gereklidir|
|`@ComposableContract`|Compose fonksiyonlarının kurallarını belirler|
|`@InternalComposeApi`|Compose’un dahili API’lerini açmak için kullanılır|
|`@UiToolingData`|UI araçlarını destekleyen dahili bir anotasyondur|

---

Bu anotasyonları bilerek ve doğru şekilde kullanarak Compose uygulamalarında performans artışı ve kod organizasyonu sağlayabilirsiniz. 🚀