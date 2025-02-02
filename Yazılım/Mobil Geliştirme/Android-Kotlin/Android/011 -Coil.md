#Yazılım #MobilGeliştirme #Android 
![[Pasted image 20250107140556.png]]

Android'deki **Coil** (İngilizce: _Coil_), modern bir görüntü yükleme kütüphanesidir. Android uygulamalarında resimlerin yüklenmesi, önbelleğe alınması ve işlenmesi işlemleri genellikle karmaşık olabilir. Coil, bu işlemleri daha hızlı ve verimli bir şekilde yapabilmek için tasarlanmıştır.

**Coil**, Android için geliştirilmiş bir görsel yükleme kütüphanesidir. Kotlin tabanlıdır ve **okuyucusu** ve **yazıcısı** kolay, modern bir API sunar. Görsellerin internet üzerinden veya yerel depolama alanından hızlı bir şekilde yüklenmesini sağlar. Coil, hem performans hem de kullanıcı deneyimini iyileştirmek için optimizasyonlar yaparak resimlerin hızlı bir şekilde kullanıcıya sunulmasını sağlar.


==**Coil Özellikleri:**==

1. **Kotlin ile Tam Uyumluluk:** Coil, Kotlin dilinde yazılmış bir kütüphanedir, bu yüzden Kotlin ile tamamen uyumludur ve Kotlin'in sunduğu avantajlardan (örneğin null güvenliği, veri sınıfları, lambda ifadeleri) tam anlamıyla faydalanır.
    
2. **Görüntü Yükleme:** Coil, resimleri URL'lerden veya yerel dosyalardan hızlıca yükler. Bu işlem sırasında önbellekleme, dönüştürme ve farklı boyutlarda yükleme gibi işlemleri yönetir.
    
3. **Önbellekleme:** Resimler, ağ bağlantısı zayıf olduğunda bile hızlı bir şekilde yüklenebilmesi için cihazın belleğinde veya diskinde önbelleğe alınabilir.
    
4. **Dönüşüm:** Resimler, gerekirse boyutlandırılabilir, döndürülebilir veya başka görsel efektlerle işlenebilir.
    
5. **Asenkron Yükleme:** Coil, görsel yükleme işlemlerini asenkron olarak gerçekleştirir, yani ana iş parçacığını (UI thread) bloke etmeden görseller yüklenebilir.
    
6. **Kapsayıcı API:** Kotlin Coroutines ve Flow yapıları ile uyumludur. Yani asenkron işlemler daha yönetilebilir ve basit hale gelir.


==**Coil Kullanımı Örnek**==

Coil, Jetpack Compose ile kullanıldığında, `rememberImagePainter` fonksiyonu ile görselleri yükleriz. Aşağıda basit bir örnek verilmiştir:

**Adımlar:**

- Coil kütüphanesini projeye dahil etme
- Jetpack Compose ile görseli yükleme

**Coil Kütüphanesini Dahil Etme**

Proje dosyasına Coil’i dahil etmek için `build.gradle` dosyanıza şu satırı eklemeniz gerekmektedir:
```gradle
dependencies {
    implementation("io.coil-kt:coil-compose:2.0.0")  // Coil Compose uyumlu sürüm
}

```


**Coil ile Görsel Yükleme**

Jetpack Compose kullanarak bir görseli yüklemek için `Image` composable'ı ve `rememberImagePainter` fonksiyonunu kullanabilirsiniz.
```kotlin
import androidx.compose.foundation.Image
import androidx.compose.runtime.Composable
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.res.painterResource
import coil.compose.rememberImagePainter
import androidx.compose.ui.Modifier

@Composable
fun ImageFromUrl() {
    val painter = rememberImagePainter("https://www.example.com/image.jpg")
    Image(painter = painter, contentDescription = null)
}

@Preview
@Composable
fun PreviewImageFromUrl() {
    ImageFromUrl()
}

```
Bu örnekte, `rememberImagePainter` ile URL'den bir görsel yükleniyor ve bu görsel `Image` composable'ı ile ekranda gösteriliyor.


**Görüntü Yüklerken Kullanıcı Deneyimini İyileştirme**

Coil, görsel yükleme işlemi sırasında gösterilecek placeholder ve hata görselleri eklemeyi destekler. Bu, kullanıcı deneyimini önemli ölçüde iyileştirir. İşte bir örnek:

**Placeholder ve Error Görselleri Eklemek**

```kotlin
import coil.compose.rememberImagePainter
import androidx.compose.foundation.Image
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.res.painterResource
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier

@Composable
fun ImageFromUrlWithPlaceholder() {
    val painter = rememberImagePainter(
        "https://www.example.com/image.jpg",
        builder = {
            placeholder(R.drawable.placeholder)  // Placeholder görseli
            error(R.drawable.error)  // Hata görseli
        }
    )
    Image(painter = painter, contentDescription = "Image", modifier = Modifier.fillMaxWidth())
}

```
Burada `placeholder` fonksiyonu, görsel yüklenene kadar gösterilecek bir görsel belirlerken, `error` fonksiyonu yükleme hatası durumunda gösterilecek bir görsel belirler.


 **Görüntü Dönüşümleri**

Coil, görüntüler üzerinde çeşitli dönüşümler yapmanıza olanak tanır. Örneğin, görselleri yuvarlak hale getirebilir, kesme işlemi uygulayabilir veya renk filtreleri ekleyebilirsiniz.

**Yuvarlak Köşe ve Diğer Dönüşümler**

Coil, görselleri yuvarlak hale getirme veya diğer dönüşümleri yapabilmek için `transformations` parametresini destekler.

```kotlin
import coil.compose.rememberImagePainter
import coil.transform.CircleCropTransformation
import coil.transform.Transformation

@Composable
fun RoundedImage() {
    val painter = rememberImagePainter(
        "https://www.example.com/image.jpg",
        builder = {
            transformations(CircleCropTransformation())  // Yuvarlak hale getirme
        }
    )
    Image(painter = painter, contentDescription = "Rounded Image")
}

```

Jetpack Compose ve Coil, modern Android uygulamalarında görsel yükleme işlemlerini hızlı, verimli ve kullanıcı dostu hale getirir. Compose ile Coil'i kullanarak asenkron görsel yüklemeleri, dönüşümleri ve hata yönetimini kolayca entegre edebilirsiniz.

[AndroidCoil GitHub Reposu](https://github.com/abdullah-tanriverdi/AndroidCoil)


---
***Abdullah TANRIVERDİ***