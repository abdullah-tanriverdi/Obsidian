#Yazılım #Yazılım-Jargon 


![[Gradle1.png]]

 Gradle, açık kaynaklı bir yazılım yapılandırma aracıdır. Java projeleri için geliştirilmiş olsa da, Kotlin, Groovy, Scala, C/C++ gibi dillerle de çalışabilir. Gradle, projelerin derlenmesi, test edilmesi, paketlenmesi ve dağıtılması gibi süreçlerin otomatikleştirilmesini sağlar. Gradle, esnek bir yapılandırma sistemi sunar ve kullanıcıların projelerine özel ihtiyaçlara göre yapı oluşturmasına olanak tanır.

**Gradle'in Temel Özellikleri**
- **Esneklik ve Güçlü Yapılandırma Desteği**: Gradle, DSL (Domain Specific Language) kullanarak özelleştirilebilir yapılandırmalar sunar.
- **İnkremental Derleme**: Gradle, yalnızca değişiklik yapılan bölümleri derler, böylece derleme süresini kısaltır.
- **Bağımlılık Yönetimi**: Gradle, proje bağımlılıklarını (örneğin, dış kütüphaneler) kolayca yönetebilir.
- **Çapraz Platform Desteği**: Gradle, farklı platformlar ve dillerle uyumlu çalışabilir.
- **Yüksek Performans**: Gradle, yüksek verimli derleme süreçleri sunarak, projelerin hızlı bir şekilde oluşturulmasına yardımcı olur.


**Gradle Dosyaları**
Gradle iki ana dosya kullanır:

1. **build.gradle**: Projelerin yapılandırmalarının yer aldığı ana dosya. Java, Kotlin veya Groovy DSL ile yazılabilir.
    - **build.gradle** örneği (Groovy DSL):

```groovy
plugins {
    id 'java'
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework:spring-context:5.3.8'
}

task hello {
    doLast {
        println 'Hello, Gradle!'
    }
}

```

2. **settings.gradle**: Projeler arasında modüler yapı kullanıldığında, projelerin bağlantılarını ve yapılandırmalarını tanımlayan dosya.

 **Gradle Temel Kavramlar**

1. **Task (Görev)**: Gradle, "task" adı verilen iş parçacıklarını kullanarak projeleri oluşturur. Her task, belirli bir işlemi yapar. Örneğin, derleme, test etme, paketleme gibi.
2. **Project (Proje)**: Gradle bir veya birden fazla projeyi yöneten bir yapı sunar. Her proje, bir veya birden fazla task içerebilir.
3. **Build Script (Yapı Scripti)**: build.gradle dosyasındaki komutlar, Gradle'ın yapılandırmasını belirler.

**Gradle Çalıştırma**

Gradle komutları terminal veya komut satırı üzerinden çalıştırılabilir. Yaygın kullanılan bazı komutlar şunlardır:

- `gradle build`: Projeyi derler ve paketler.
- `gradle clean`: Derleme çıktıları ve geçici dosyaları temizler.
- `gradle test`: Testleri çalıştırır.
- `gradle tasks`: Mevcut tüm görevleri listeler.
- `gradle run`: Projeyi çalıştırır.


**Bağımlılık Yönetimi**

Gradle, proje bağımlılıklarını yönetmek için bir `dependencies` bloğu kullanır. Örnek olarak bir dış kütüphaneyi projeye dahil etme:
```groovy
dependencies {
    implementation 'com.google.guava:guava:30.1-jre'
}

```


Gradle, projelerin yapılandırılmasında ve yönetilmesinde çok esnek ve güçlü bir araçtır. Gelişmiş özellikleri ve esneklikleri sayesinde, özellikle büyük ve karmaşık projeler için ideal bir seçimdir.

![](https://www.youtube.com/watch?v=cUGWEQ8NLHk)

***


***Abdullah TANRIVERDİ***
