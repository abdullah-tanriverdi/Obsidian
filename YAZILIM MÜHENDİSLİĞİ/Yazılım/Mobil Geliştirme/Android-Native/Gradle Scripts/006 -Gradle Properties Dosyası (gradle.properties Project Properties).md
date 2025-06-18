
#Yazılım #MobilGeliştirme #Android-Native  #GradleScript

**`gradle.properties`** dosyası, Android projelerinde proje genelinde Gradle yapılandırmasını özelleştirmek için kullanılır. Bu dosya, JVM (Java Virtual Machine) ayarlarını, Android özelliklerini ve diğer yapılandırma parametrelerini içerir.


==**`gradle.properties` Dosyasının Görevleri**==

1. **Global Ayarlar**: Tüm proje modülleri için geçerli olacak genel yapılandırmalar tanımlanır.
2. **Performans Optimizasyonu**: Build sürecini hızlandırmak ve bellek kullanımını optimize etmek için JVM ve Gradle parametreleri ayarlanır.
3. **Android Özellikleri**: Android'e özgü ayarlar ve iyileştirmeler yapılabilir.
4. **Kotlin ve Diğer Diller**: Kod stili ve diğer dil özellikleri tanımlanabilir.


==**Kodun Bölümlerine Göre İnceleme**==

 **1. Proje Genel Ayarları**
 ```properties
 # Project-wide Gradle settings.
# IDE (e.g. Android Studio) users:
# Gradle settings configured through the IDE *will override*
# any settings specified in this file.

```
**Proje Genişindeki Ayarlar**:
- Bu dosya, proje genelinde Gradle yapılandırmalarını içerir.
- IDE (örneğin, Android Studio) üzerinden yapılan ayarlar, bu dosyada belirtilen ayarları geçersiz kılabilir.


**2. JVM Argümanları**
```properties
# Specifies the JVM arguments used for the daemon process.
# The setting is particularly useful for tweaking memory settings.
org.gradle.jvmargs=-Xmx2048m -Dfile.encoding=UTF-8

```
**`org.gradle.jvmargs`**:
- JVM için kullanılacak argümanları belirtir.
- **`-Xmx2048m`**: JVM’in maksimum bellek kullanımını 2048 MB (2 GB) olarak sınırlar.
- **`-Dfile.encoding=UTF-8`**: Dosya kodlaması olarak UTF-8 kullanılmasını sağlar.



**3. Paralel Build Desteği (Opsiyonel)**
```properties 
# When configured, Gradle will run in incubating parallel mode.
# This option should only be used with decoupled projects. For more details, visit
# https://developer.android.com/r/tools/gradle-multi-project-decoupled-projects
# org.gradle.parallel=true

```
**`org.gradle.parallel`**:
- Gradle’ın projeleri paralel olarak derlemesine olanak tanır.
- Varsayılan olarak devre dışıdır. Etkinleştirilmesi büyük projelerde derleme süresini kısaltabilir.
- **UYARI**: Paralel mod, yalnızca bağımsız (decoupled) projelerde güvenle kullanılabilir.


**4. AndroidX Desteği**
```properties
# AndroidX package structure to make it clearer which packages are bundled with the
# Android operating system, and which are packaged with your app's APK
# https://developer.android.com/topic/libraries/support-library/androidx-rn
android.useAndroidX=true

```
**`android.useAndroidX=true`**:
- Projede AndroidX paket yapısını etkinleştirir.
- AndroidX, Android Support Library'nin modernleştirilmiş ve daha iyi organize edilmiş bir versiyonudur.

**5. Kotlin Kod Stili**
```properties
# Kotlin code style for this project: "official" or "obsolete":
kotlin.code.style=official

```
**`kotlin.code.style`**:
- Kotlin kod yazım stili belirler.
- **`official`**: Kotlin için resmi kod stili kullanılır.
- **`obsolete`**: Eski kod stilini kullanmak isteyenler için bir opsiyondur (modern projelerde önerilmez).


**6. Transitive R Class (Kaynak Sınıfı) Yönetimi**
```properties
# Enables namespacing of each library's R class so that its R class includes only the
# resources declared in the library itself and none from the library's dependencies,
# thereby reducing the size of the R class for that library
android.nonTransitiveRClass=true

```
- **`android.nonTransitiveRClass=true`**:
    - Her kütüphanenin **R** sınıfı yalnızca kendi tanımladığı kaynakları içerir.
    - Bağımlılıklardan gelen kaynaklar eklenmez.
    - **Avantajları**:
        - **Performans**: Build sürelerini kısaltır.
        - **Bellek Kullanımı**: Daha küçük R sınıfları, belleği daha verimli kullanır.


==**Performans İyileştirme Ayarları**==

- **Bellek Kullanımı**: `org.gradle.jvmargs` ile JVM bellek limitleri ayarlanır.
- **Paralel Build**: `org.gradle.parallel` ayarı büyük projelerde build süresini hızlandırır.
- **R Class Namespacing**: `android.nonTransitiveRClass=true` ayarıyla R sınıfı optimizasyonu yapılır.
***
***


***Abdullah TANRIVERDİ***






