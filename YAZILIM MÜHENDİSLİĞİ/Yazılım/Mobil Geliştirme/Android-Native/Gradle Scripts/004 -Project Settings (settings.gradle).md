#Yazılım #MobilGeliştirme #Android-Native  #GradleScript

**`settings.gradle.kts`** dosyası, Android Studio projelerinde Gradle yapılandırma sisteminin başlangıç noktasıdır. Bu dosya, projenin global yapılandırmasını, modüllerin tanımlanmasını ve bağımlılık yönetimi ile ilgili temel ayarları içerir.


**`settings.gradle.kts` Dosyasının Görevleri**
1. Proje adı ve modüllerinin tanımlanması.
2. Bağımlılık ve repository yapılandırmasının yönetimi.
3. Plugin ve bağımlılık çözümleme için gerekli ayarların yapılandırılması.



==**Kodun Bölümlerine Göre İnceleme**==

**1. Plugin Yönetimi (`pluginManagement`)**
```kotlin
pluginManagement {
    repositories {
        google {
            content {
                includeGroupByRegex("com\\.android.*")
                includeGroupByRegex("com\\.google.*")
                includeGroupByRegex("androidx.*")
            }
        }
        mavenCentral()
        gradlePluginPortal()
    }
}

```

**Açıklama:**

- **`pluginManagement`**: Gradle plugin’lerinin hangi depolardan alınacağını tanımlar.
- **`repositories`**: Plugin'leri çözmek için kullanılacak depoların listesini belirtir.
    - **`google`**: Google’ın resmi Android kütüphane ve araçlarının bulunduğu repository.
    - **`mavenCentral`**: Java ve Kotlin projeleri için en yaygın kullanılan repository.
    - **`gradlePluginPortal`**: Gradle plugin’lerinin bulunduğu varsayılan repository.

 **`google` İçindeki `content` Bloku:**

- **`content`**: Google deposunda hangi grupların dahil edileceğini belirtir.
    - **`includeGroupByRegex`**: Belirli bir desene (regex) uyan grupları dahil eder.
        - `com.android.*`: Android ile ilgili plugin’ler.
        - `com.google.*`: Google tarafından sağlanan plugin’ler.
        - `androidx.*`: Android Jetpack kütüphaneleri.


**2. Bağımlılık Yönetimi (`dependencyResolutionManagement`)**
```kotlin
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
    }
}

```

**Açıklama:**

- **`dependencyResolutionManagement`**: Projede bağımlılıkların nasıl çözümleneceğini tanımlar.
- **`repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)`**:
    - Bu ayar, modül düzeyindeki `repositories` bloklarını kullanmayı engeller. Tüm bağımlılıklar yalnızca burada tanımlanan depolardan çözülür. Bu, bağımlılık çözümlemesinde merkezi kontrol sağlar.
- **`repositories`**:
    - **`google()`**: Android SDK ve Jetpack kütüphaneleri için.
    - **`mavenCentral()`**: Üçüncü taraf bağımlılıklar için.


**3. Proje ve Modül Tanımları**
```kotlin
rootProject.name = "AndroidRetrofit"
include(":app")

```

**Açıklama:**
- **`rootProject.name`**: Projenin adını belirtir. Bu, genellikle Android Studio’da üst düzey proje adı olarak görünür. Bu örnekte proje adı **"AndroidRetrofit"** olarak ayarlanmış.
- **`include(":app")`**:
    - Bu, projenin bir parçası olan modülleri belirtir.
    - Burada yalnızca bir modül tanımlanmış: **`:app`**. Bu modül, uygulamanın ana modülüdür.


***

***Abdullah TANRIVERDİ***

