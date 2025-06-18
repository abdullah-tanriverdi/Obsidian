
#Yazılım #MobilGeliştirme #Android-Native  #GradleScript

**`gradle-wrapper.properties`** dosyası, Gradle Wrapper’ın yapılandırmasını tanımlayan bir dosyadır. Bu dosya, projede kullanılan Gradle sürümünü belirler ve Gradle Wrapper’ın indirme işlemlerini yönetir.


 **`gradle-wrapper.properties` Dosyasının Görevi**
1. **Gradle Sürümünü Tanımlama**:
    - Projede kullanılacak Gradle sürümünü belirler.
2. **Wrapper Ayarları**:
    - Wrapper’ın indirme işlemlerinin hangi dizinde ve nasıl yapılacağını düzenler.
3. **Projelerde Tutarlılık**:
    - Tüm ekip üyelerinin aynı Gradle sürümünü kullanmasını sağlar.
4. **Otomatik İndirme**:
    - Gerekli Gradle sürümü otomatik olarak indirilir ve kurulur.


==**Kodun İncelenmesi ve Açıklamaları**==

**1. Oluşturulma Zamanı**
```properties
#Sun Jan 26 18:06:08 TRT 2025

```
- **Zaman Bilgisi**:
    - Dosyanın oluşturulma veya son düzenlenme tarihini belirtir.

**2. Wrapper Dağıtım Ayarları**
```properties
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists

```
- **Açıklama**:
    - Wrapper ile indirilen Gradle dosyalarının nereye kaydedileceğini tanımlar.
- **Parametreler**:
    - **`distributionBase`**:
        - Gradle Wrapper’ın indirme işlemlerini hangi temel dizinde yöneteceğini belirtir.
        - Varsayılan değer: **`GRADLE_USER_HOME`**.
    - **`distributionPath`**:
        - İndirilen Gradle dosyalarının saklanacağı alt dizini belirtir.
        - Varsayılan değer: **`wrapper/dists`**.
    - **`zipStoreBase`**:
        - Wrapper tarafından indirilen `.zip` dosyalarının temel dizinini belirtir.
        - Varsayılan değer: **`GRADLE_USER_HOME`**.
    - **`zipStorePath`**:
        - `.zip` dosyalarının saklanacağı alt dizini belirtir.
        - Varsayılan değer: **`wrapper/dists`**.


**3. Gradle Sürüm Bilgisi**
```properties
distributionUrl=https\://services.gradle.org/distributions/gradle-8.7-bin.zip

```
- **Açıklama**:
    - Projede kullanılacak Gradle sürümünün indirilmesi için gerekli URL’yi belirtir.
- **Parametreler**:
    - **`distributionUrl`**:
        - Gradle Wrapper’ın hangi sürümü indireceğini ve kuracağını belirler.
        - Örnekte: **Gradle 8.7** sürümü kullanılacaktır.
        - **`.bin.zip`**:
            - Sadece çalıştırmak için gerekli minimum dosyaları içerir. (Dokümantasyon veya kaynak kodlar yoktur).
        - **`.all.zip`**:
            - Dokümantasyon ve kaynak kodları da içerir.




==**Gradle Wrapper'ın Avantajları**==

1. **Tutarlılık Sağlar**:
    - Tüm ekip üyeleri projede aynı Gradle sürümünü kullanır.
2. **Kolaylık**:
    - Projeyi ilk kez çalıştırırken Gradle sürümünün otomatik olarak indirilmesini sağlar.
3. **Versiyon Yönetimi**:
    - Her proje, ihtiyaçlarına uygun farklı bir Gradle sürümünü bağımsız olarak kullanabilir.
4. **Platform Bağımsızlığı**:
    - Farklı işletim sistemlerinde (Windows, macOS, Linux) aynı Gradle Wrapper ayarları kullanılabilir.


---

***Abdullah TANRIVERDİ***
