#Yazılım #MobilGeliştirme #Android #GradleScript

**ProGuard**, Android uygulamalarında kodu sıkıştırmak (minify), optimize etmek ve karıştırmak (obfuscate) için kullanılan bir araçtır. **`proguard-rules.pro`** dosyası, ProGuard'ın nasıl çalışacağını belirleyen özelleştirilmiş kurallar içerir.


> [!tip] İPUCU
> Obfuscate hakkında detaylı bilgi için bağlantıya tıkla [[000 -Obfuscate]]
> Minify hakkında detaylı bilgi için bağlantıya tıkla [[000 -Minify]]


==**ProGuard’ın Görevleri**==

1. **Kod Karıştırma (Obfuscation)**:
    - Kodun anlaşılmasını zorlaştırmak için değişken, sınıf ve yöntem adlarını karıştırır.
2. **Kod Küçültme (Minification)**:
    - Kullanılmayan sınıfları ve yöntemleri kaldırarak APK boyutunu azaltır.
3. **Kod Optimizasyonu**:
    - Kodun daha verimli çalışmasını sağlamak için iyileştirmeler yapar.


==**`proguard-rules.pro` Dosyasının Görevleri**==

- ProGuard’ın davranışını özelleştirmek için kullanılır.
- Hangi sınıfların, yöntemlerin veya değişkenlerin ProGuard tarafından korunacağını ya da optimize edileceğini belirtir.
- Varsayılan olarak **`build.gradle`** dosyasındaki `proguardFiles` özelliğiyle ilişkilendirilir
```gradle
proguardFiles(getDefaultProguardFile("proguard-android-optimize.txt"), "proguard-rules.pro")

```



==**`proguard-rules.pro` Dosyasının İçeriği**==

**1. Proje-Specifik Kurallar**
```pro
# Add project specific ProGuard rules here.

```
- Bu satır, projeye özgü kuralların bu dosyada tanımlanabileceğini belirtir.


**2. ProGuard Yapılandırma Dosyalarının Kontrolü**
```pro
# You can control the set of applied configuration files using the
# proguardFiles setting in build.gradle.

```
- **`proguardFiles`** ile ProGuard için birden fazla yapılandırma dosyası kullanılabilir.


**3. WebView ile JavaScript Kullanımı**
```pro
# If your project uses WebView with JS, uncomment the following
# and specify the fully qualified class name to the JavaScript interface
# class:
#-keepclassmembers class fqcn.of.javascript.interface.for.webview {
#   public *;
#}

```

- **`-keepclassmembers`**:
	- WebView ile JavaScript arayüzü kullanan sınıfların korunmasını sağlar.
	- `fqcn.of.javascript.interface.for.webview` kısmına JavaScript arayüz sınıfının tam adı yazılmalıdır.


**4. Satır Numaralarını Koruma**
```pro
# Uncomment this to preserve the line number information for
# debugging stack traces.
#-keepattributes SourceFile,LineNumberTable

```

- **`-keepattributes SourceFile,LineNumberTable`**:

	- Hata ayıklama sırasında hata yığın izlerinin (stack traces) anlamlı kalması için satır numaralarını korur.


**5. Kaynak Dosya Adını Gizleme**
```pro
# If you keep the line number information, uncomment this to
# hide the original source file name.
#-renamesourcefileattribute SourceFile

```

- **`-renamesourcefileattribute`**:

	- Kaynak dosya adlarını gizler.




==**ProGuard’ın Avantajları**==

1. **APK Boyutunu Küçültür**: Kullanılmayan kodları kaldırarak APK’yı optimize eder.
2. **Kod Güvenliği Sağlar**: Kodun okunmasını zorlaştırarak tersine mühendislik risklerini azaltır.
3. **Performans İyileştirmesi**: Kod optimizasyonuyla daha verimli bir çalışma sağlar.


***

***Abdullah TANRIVERDİ***

