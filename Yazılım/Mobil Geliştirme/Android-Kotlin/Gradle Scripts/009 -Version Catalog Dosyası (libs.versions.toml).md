#Yazılım #MobilGeliştirme #Android #GradleScript


**Version Catalog** (Versiyon Kataloğu), Gradle projesinde kullanılan bağımlılıkların ve eklentilerin versiyonlarının merkezi bir şekilde yönetilmesini sağlayan bir yapılandırmadır. Bu, özellikle projelerde kullanılan çok sayıda bağımlılığın sürüm yönetimini kolaylaştırır ve sürüm uyuşmazlıklarını önler. Versiyon kataloğu, Gradle'ın sürüm 7.0 ve sonrasında sağladığı bir özelliktir.

`gradle/libs.versions.toml` dosyası, projede kullanılan bağımlılıkların ve eklentilerin sürümlerini tanımlar. Bu dosya, daha temiz ve yönetilebilir bir yapı oluşturur. Burada, bağımlılıkların ve eklentilerin sürümleri tanımlanarak, build script dosyalarında (build.gradle) sadece bağımlılık adı ve versiyon referansı kullanılabilir. Bu, sürüm güncellemelerini tek bir yerden yönetmeyi sağlar.


==**`libs.versions.toml` Dosyasının İncelenmesi**==

1.   **[versions] Bölümü**
Bu bölümde, projede kullanılan bağımlılıkların sürümleri tanımlanır. Her bağımlılığa bir referans adı verilir ve bu referanslar daha sonra `libraries` bölümünde kullanılır.

```toml
[versions]
agp = "8.6.0"
kotlin = "1.9.0"
coreKtx = "1.15.0"
junit = "4.13.2"
junitVersion = "1.2.1"
espressoCore = "3.6.1"
lifecycleRuntimeKtx = "2.8.7"
activityCompose = "1.9.3"
composeBom = "2024.04.01"

```
- **`agp`**: Android Gradle Plugin (AGP) sürümü.
- **`kotlin`**: Kotlin sürümü.
- **`coreKtx`, `junit`, `espressoCore`, vs.**: Uygulamada kullanılan diğer bağımlılıkların sürümleri.
- Bu sürümler daha sonra **`libraries`** bölümünde referans olarak kullanılacaktır.


2. **[libraries] Bölümü**

Bu bölümde, bağımlılıklar belirtilir. Her bağımlılık, belirli bir grup adı (group), bağımlılık adı (name) ve versiyon referansı ile tanımlanır. Bu, sürüm referanslarının merkezi bir şekilde yönetilmesini sağlar.

```toml
[libraries]
androidx-core-ktx = { group = "androidx.core", name = "core-ktx", version.ref = "coreKtx" }
junit = { group = "junit", name = "junit", version.ref = "junit" }
androidx-junit = { group = "androidx.test.ext", name = "junit", version.ref = "junitVersion" }
androidx-espresso-core = { group = "androidx.test.espresso", name = "espresso-core", version.ref = "espressoCore" }
androidx-lifecycle-runtime-ktx = { group = "androidx.lifecycle", name = "lifecycle-runtime-ktx", version.ref = "lifecycleRuntimeKtx" }
androidx-activity-compose = { group = "androidx.activity", name = "activity-compose", version.ref = "activityCompose" }
androidx-compose-bom = { group = "androidx.compose", name = "compose-bom", version.ref = "composeBom" }
androidx-ui = { group = "androidx.compose.ui", name = "ui" }
androidx-ui-graphics = { group = "androidx.compose.ui", name = "ui-graphics" }
androidx-ui-tooling = { group = "androidx.compose.ui", name = "ui-tooling" }
androidx-ui-tooling-preview = { group = "androidx.compose.ui", name = "ui-tooling-preview" }
androidx-ui-test-manifest = { group = "androidx.compose.ui", name = "ui-test-manifest" }
androidx-ui-test-junit4 = { group = "androidx.compose.ui", name = "ui-test-junit4" }
androidx-material3 = { group = "androidx.compose.material3", name = "material3" }

```
- Her bağımlılık, bir `group` ve `name` ile tanımlanır.
- **`version.ref`**:
    - Burada tanımlanan sürüm referansı (örneğin, `coreKtx`, `junit`) **[versions]** bölümünden alınır.
    - Bu sayede sürümleri merkezi bir şekilde yönetebilirsiniz.

Örneğin, **`androidx-core-ktx`** bağımlılığı `androidx.core:core-ktx` bağımlılığıdır ve sürümü **`coreKtx`** referansı ile belirtilmiştir.


3. **[plugins] Bölümü**
Bu bölümde, kullanılan Gradle eklentilerinin sürümleri tanımlanır. Eklenti isimleri ve sürümleri de yine `version.ref` ile belirtilir.
```toml
[plugins]
android-application = { id = "com.android.application", version.ref = "agp" }
kotlin-android = { id = "org.jetbrains.kotlin.android", version.ref = "kotlin" }

```
- **`android-application`** eklentisi, **`agp`** sürüm referansı ile belirtilen Android Gradle Plugin sürümünü kullanır.
- **`kotlin-android`** eklentisi, **`kotlin`** sürüm referansı ile belirtilen Kotlin sürümünü kullanır.



==**Avantajları ve Kullanımı**==

- **Merkezi Sürüm Yönetimi**:
    
    - Versiyonlar **`libs.versions.toml`** dosyasındaki tek bir yerden yönetilir. Projede kullanılan tüm bağımlılıkların ve eklentilerin sürümleri burada tanımlanır, böylece tutarlılık sağlanır.
- **Kolay Bakım**:
    
    - Bağımlılıkların sürümleri tek bir dosyada tanımlandığı için projede sürüm güncellemesi yapmak çok daha kolaydır. Güncellenmesi gereken bir sürüm varsa, sadece **`libs.versions.toml`** dosyasındaki versiyonları güncellemek yeterlidir.
- **Ekip Çalışması**:
    
    - Projede birden fazla geliştirici çalışıyorsa, tüm ekip aynı sürüm bilgilerini kullandığı için sürüm uyuşmazlıkları önlenir.
- **Daha Temiz Build Script’leri**:
    
    - `build.gradle` dosyalarında sadece bağımlılıklar ve eklenti isimleri yer alır, sürüm numaraları için herhangi bir işlem yapılmaz. Bu, dosyaların daha okunabilir ve temiz olmasını sağlar.

==**Örnek Kullanım: build.gradle**==

**`libs.versions.toml`** dosyasındaki sürümleri kullanmak için, `build.gradle` dosyasına şu şekilde eklemeler yapılabilir:
```groovy
dependencies {
    implementation libs.androidx.core-ktx
    testImplementation libs.junit
    androidTestImplementation libs.androidx.espresso-core
    implementation libs.androidx.lifecycle-runtime-ktx
    implementation libs.androidx.activity-compose
    implementation libs.androidx.compose-bom
}

```
`libs.androidx.core-ktx` burada **`core-ktx`** bağımlılığına karşılık gelir ve sürüm numarası, **`libs.versions.toml`** dosyasından alınır.

---

***Abdullah TANRIVERDİ***
