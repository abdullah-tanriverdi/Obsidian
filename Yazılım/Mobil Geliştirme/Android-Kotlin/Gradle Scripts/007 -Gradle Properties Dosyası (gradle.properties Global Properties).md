
#Yazılım #MobilGeliştirme #Android #GradleScript


**`gradle.properties` (Global Properties)** dosyası, Gradle yapılandırmasının genel ayarlarını içeren ve tüm projelerde kullanılabilen bir yapılandırma dosyasıdır. Bu dosya, özellikle performans ayarlarını optimize etmek ve proxy ayarlarını yönetmek için kullanılır.

==**Global `gradle.properties` Dosyasının Görevleri**==

1. **Global JVM Ayarları**: JVM için bellek ve diğer yapılandırma parametrelerini belirtir.
2. **Performans Optimizasyonu**: Paralel derleme ve bellek yönetimi gibi yapılandırmalar içerir.
3. **Proxy Ayarları**: HTTP ve HTTPS proxy sunucularını yapılandırmayı sağlar.
4. **Tüm Projeler İçin Geçerlilik**: Bu ayarlar tüm Gradle projelerinde geçerli olur.



==**Kodun İncelenmesi ve Açıklamaları**==

**1. Genel Bilgilendirme**
```properties
## For more details on how to configure your build environment visit
# http://www.gradle.org/docs/current/userguide/build_environment.html

```
**Dokümantasyon Referansı**:
- Gradle yapılandırmasıyla ilgili detaylı bilgiye yukarıdaki bağlantıdan ulaşabilirsiniz.

**2. JVM Ayarları**
```properties
# Specifies the JVM arguments used for the daemon process.
# The setting is particularly useful for tweaking memory settings.
# Default value: -Xmx1024m -XX:MaxPermSize=256m
# org.gradle.jvmargs=-Xmx2048m -XX:MaxPermSize=512m -XX:+HeapDumpOnOutOfMemoryError -Dfile.encoding=UTF-8

```
**`org.gradle.jvmargs`**:
- JVM için argümanları tanımlar.
- **Varsayılan Değerler**:
    - **`-Xmx1024m`**: Maksimum bellek 1024 MB (1 GB).
    - **`-XX:MaxPermSize=256m`**: Maksimum "PermGen" bellek 256 MB.
- **Özelleştirilmiş Değerler**:
    - **`-Xmx2048m`**: Maksimum bellek 2048 MB (2 GB).
    - **`-XX:MaxPermSize=512m`**: Maksimum "PermGen" bellek 512 MB.
    - **`-XX:+HeapDumpOnOutOfMemoryError`**: Bellek yetersizliği durumunda bir "Heap Dump" oluşturur.
    - **`-Dfile.encoding=UTF-8`**: Dosya kodlaması olarak UTF-8 kullanılmasını sağlar.

**3. Paralel Derleme Desteği**
```properties
# When configured, Gradle will run in incubating parallel mode.
# This option should only be used with decoupled projects.
# org.gradle.parallel=true

```

**`org.gradle.parallel`**:
- Gradle’ın projeleri paralel olarak derlemesini sağlar.
- **Faydaları**:
    - Büyük projelerde build sürelerini önemli ölçüde kısaltabilir.
- **UYARI**:
    - Paralel mod, yalnızca bağımsız projelerle (decoupled projects) kullanılmalıdır.


**4. Proxy Ayarları**
```properties
systemProp.http.proxyHost=
systemProp.http.proxyPort=80
systemProp.https.proxyHost=
systemProp.https.proxyPort=80

```

**Proxy Sunucu Ayarları**:
- İnternet erişiminde proxy sunucu kullanan ağlarda yapılandırma yapılmasını sağlar.
- **`http.proxyHost`**: HTTP proxy sunucu adresi.
- **`http.proxyPort`**: HTTP proxy sunucu portu.
- **`https.proxyHost`**: HTTPS proxy sunucu adresi.
- **`https.proxyPort`**: HTTPS proxy sunucu portu.
```properties
#Örnek
systemProp.http.proxyHost=proxy.example.com
systemProp.http.proxyPort=8080
systemProp.https.proxyHost=proxy.example.com
systemProp.https.proxyPort=8080

```

**5. Dosya Oluşturulma Zamanı**
```properties
#Sun Jan 26 18:56:49 TRT 2025

```
**Zaman Bilgisi**:
- Dosyanın oluşturulma veya düzenlenme tarihini belirtir.




**Örnek Kullanım**
```properties
# Bellek Ayarları
org.gradle.jvmargs=-Xmx4096m -XX:+HeapDumpOnOutOfMemoryError -Dfile.encoding=UTF-8

# Paralel Derleme
org.gradle.parallel=true

# Proxy Ayarları
systemProp.http.proxyHost=proxy.example.com
systemProp.http.proxyPort=8080
systemProp.https.proxyHost=proxy.example.com
systemProp.https.proxyPort=8080

```

***

***Abdullah TANRIVERDİ***
