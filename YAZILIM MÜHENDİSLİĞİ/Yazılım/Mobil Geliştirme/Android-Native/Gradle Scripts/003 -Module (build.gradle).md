#Yazılım #MobilGeliştirme #Android-Native  #GradleScript

**Module-level `build.gradle` dosyası**, belirli bir modülün nasıl derleneceğini, hangi bağımlılıkları kullanacağını ve yapılandırma ayarlarını içerir. Android projelerinde genellikle `app` adlı bir uygulama modülü bulunur ve bu dosya, o modülün yapılandırmasını belirler.

==**Module-Level `build.gradle` Dosyasının Bölümleri**==

**1. Plugins Bölümü**
```gradle
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.android)
}

```
- **`android.application`**: Bu plugin, modülün bir Android uygulaması olduğunu belirtir.
- **`kotlin.android`**: Kotlin dilinin Android ile entegre çalışmasını sağlar.

Bu plugin’ler **root-level build.gradle** dosyasında tanımlanan plugin’lerden çekilir. Böylece modül, bu plugin’leri doğrudan kullanabilir.


**2. Android Bölümü**
Android yapılandırmaları bu blokta tanımlanır:
```gradle
android {
    namespace = "com.tanriverdi.androidretrofit"
    compileSdk = 35
    ...
}

```

- **`namespace`**: Uygulamanın package adıyla aynı olan bir ad alanı belirtir. Bu, uygulamanın kodunu diğer projelerden ayırmak için kullanılır.
- **`compileSdk`**: Uygulamanın hangi Android SDK sürümüyle derleneceğini belirler. Burada `35` kullanılmış.

**2.1 `defaultConfig`**
```gradle
defaultConfig {
    applicationId = "com.tanriverdi.androidretrofit"
    minSdk = 24
    targetSdk = 34
    versionCode = 1
    versionName = "1.0"
    ...
}

```
- **`applicationId`**: Uygulamanın benzersiz kimliğidir. Bu, Play Store’a yüklerken önemlidir.
- **`minSdk`**: Uygulamanın desteklediği minimum Android sürümü (`24` - Android 7.0 Nougat).
- **`targetSdk`**: Uygulamanın hedeflediği Android sürümü (`34` - Android 14).
- **`versionCode`**: Uygulama sürümünün sayısal gösterimi (her güncellemede artırılmalı).
- **`versionName`**: Kullanıcıya gösterilen sürüm bilgisi.


**2.2 `buildTypes`**
```gradle
buildTypes {
    release {
        isMinifyEnabled = false
        proguardFiles(
            getDefaultProguardFile("proguard-android-optimize.txt"),
            "proguard-rules.pro"
        )
    }
}

```

- **`release`**: Üretim sürümünde kullanılacak yapılandırmalar.
- **`isMinifyEnabled`**: Kod küçültme (minification) için kullanılır. Burada devre dışı bırakılmış.
- **`proguardFiles`**: ProGuard, kod sıkıştırma ve güvenlik için kullanılan bir araçtır.


**2.3 Diğer Ayarlar**

- **`compileOptions`**: Hangi Java sürümünün kullanılacağını belirtir.
```gradle
compileOptions {
    sourceCompatibility = JavaVersion.VERSION_1_8
    targetCompatibility = JavaVersion.VERSION_1_8
}

```

Java 8 özelliklerini destekler.

- **`kotlinOptions`**: Kotlin için JVM hedef sürümünü belirler.
```gradle
kotlinOptions {
    jvmTarget = "1.8"
}

```

- **`buildFeatures`**: Belirli özellikleri etkinleştirmek için kullanılır.
```gradle
buildFeatures {
    compose = true
}

```
Burada **Jetpack Compose** etkinleştirilmiş.

- **`composeOptions`**: Compose ile ilgili ek yapılandırmalar yapılır.
```gradle
composeOptions {
    kotlinCompilerExtensionVersion = "1.5.1"
}

```

- **`packaging`**: Gereksiz kaynak dosyalarını hariç tutar.
```gradle
packaging {
    resources {
        excludes += "/META-INF/{AL2.0,LGPL2.1}"
    }
}

```


**3. Dependencies (Bağımlılıklar)**

```gradle
dependencies {
    implementation(libs.androidx.core.ktx)
    implementation(libs.androidx.lifecycle.runtime.ktx)
    implementation(libs.androidx.activity.compose)
    ...
    implementation ("com.squareup.retrofit2:retrofit:2.9.0") // Retrofit
    implementation ("com.squareup.retrofit2:converter-gson:2.9.0") // JSON parser
}

```

Bağımlılık türleri:
- **`implementation`**: Projede kullanılacak temel bağımlılıkları belirtir.
- **`testImplementation`**: Birim testler için kullanılacak bağımlılıkları tanımlar.
- **`androidTestImplementation`**: Android cihazlar üzerinde test için kullanılan bağımlılıklar.
- **`debugImplementation`**: Yalnızca hata ayıklama sırasında etkin olan bağımlılıklar.

---

***Abdullah TANRIVERDİ***

