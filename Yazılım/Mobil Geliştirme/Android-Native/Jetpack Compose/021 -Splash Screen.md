#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 

Bu proje, Android uygulamanız için bir açılış ekranı oluşturmanın adımlarını içermektedir. Açılış ekranınızı oluşturmak için aşağıdaki adımları takip edin.

 **Gereksinimler**

- Android Studio
- AndroidX Core Kütüphanesi

**Adımlar**

 **1. Kütüphaneyi Ekleme**

Açılış ekranı için gerekli kütüphaneyi `build.gradle` dosyanıza ekleyin:

`groovy implementation("androidx.core:core-splashscreen:1.0.1")`

**2. Görselleri Yeniden Boyutlandırma**

Görsellerinizi açılış ekranı için uygun boyutlara yeniden boyutlandırın. Uygulamanızın farklı ekran boyutlarında iyi görünmesi için çeşitli boyutlarda görseller hazırlamak önemlidir.

![[splashScreen.png]]

**3. Açılış Ekranı Teması Oluşturma**

`res/values` dizininde bir açılış ekranı teması oluşturun. Ayrıca, kullanıcı tercihlerine uygunluk sağlamak için karanlık mod teması da ekleyin.

**4. AndroidManifest.xml Dosyasını Güncelleme**

`AndroidManifest.xml` dosyasına gidin ve uygulamanızın, oluşturduğunuz açılış ekranı temasını kullanmasını sağlayacak şekilde güncelleyin.

**5. Açılış Ekranını Uygulama**

`MainActivity` sınıfında, `setContentView()` yönteminden önce `installSplashScreen()` yöntemini çağırın.


```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <!-- Splash Screen teması tanımlanıyor -->
    <style name="Theme.MySplashScreen" parent="Theme.SplashScreen">
        <!-- Splash Screen arka plan rengi beyaz olarak ayarlandı -->
        <item name="windowSplashScreenBackground">@color/white</item>
        <!-- Splash Screen'da gösterilecek animasyonlu logo tanımlanıyor -->
        <item name="windowSplashScreenAnimatedIcon">@drawable/android12_logo</item>
        <!-- Splash Screen sonrası geçilecek tema ayarı yapılıyor -->
        <item name="postSplashScreenTheme">@style/Theme.AndroidSplashScreen</item>
    </style>
</resources>
```

***
***Abdullah TANRIVERDİ***
