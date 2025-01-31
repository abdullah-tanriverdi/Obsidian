#Yazılım  #MobilGeliştirme #Android 

Herkese merhaba, bu yazımda AdMob’u daha yakından tanıyacağız ve mobil uygulama geliştiricilerin nasıl AdMob üzerinden reklam geliri elde edebileceğine dair detayları anlatacağım. Hemen aşağıda yazımın içindekiler kısmında nelerden bahsettiğimi görebilirsiniz. Keyifli okumalar. :)

- AdMob’un Tanımı
- AdMob’un İşleyiş Şekli
- Platformlarla Uyumluluğu
- Google Ads İle Entegrasyonu
- AdMob Hesabı Oluşturma
- Uygulamaları AdMob’a Bağlama
- SDK Entegrasyonu Ve Teknik Ayarlar
- Uygulamanın Test Edilmesi
- Firebase İle AdMob Entegrasyonu
- AdMob Reklam Biçimleri
- AdMob İle Gelir Optimizasyonu
- AdMob Politikaları
- AdMob Rakipleri
- Türkiye’de AdMob Gelirini Alabilme

![](https://miro.medium.com/v2/resize:fit:385/1*BsAaXT4HlFDN05ryaZ0jag.png)

==**AdMob’un Tanımı**==

AdMob, Google tarafından mobil uygulama geliştiricilerine sunulan bir reklam platformudur. 2009 yılında Google tarafından satın alınan AdMob, mobil uygulamalar üzerinden gelir elde etmek isteyen geliştiricilere reklam alanları sunar.

Peki neden reklam gösterilmeli? Uygulama kullanıcılarına reklam göstermek, uygulama geliştiricilerinin işletmesinin büyümesine yardımcı olurken aynı zamanda sürdürülebilir bir ek gelir kaynağı oluşturmamızı sağlar.Reklamverenler için de yeni müşterilere ulaşabilme imkanı sağlar. Bu yapı geliştiriciler, kullanıcılar ve reklamverenler için avantajlıdır

==**AdMob’un İşleyiş Şekli**==

Reklamlar, ürün veya hizmetlerini uygulama kullanıcılarına tanıtmak isteyen reklamverenler tarafından oluşturulur ve ücretleri de onlar tarafından ödenir. Uygulamanızda reklamlar için alan oluşturduktan sonra, AdMob, kullanıcılarınızla alakalı reklamlar göstermek için ödeme yapan reklamverenlerle birlikte çalışır.

==**Platformlarla Uyumluluğu**==

AdMob, mobil uygulama geliştiricilerine farklı platformlarda reklam geliri elde etme fırsatı sunar. Android ve iOS gibi en yaygın mobil işletim sistemleriyle tam uyumludur.Ayrıca Unity gibi oyun motorlarıyla da uyumludur. Bu uyumluluk sadece bunlarla yeterli kalmayıp diğer mobil platformlarda da AdMob reklam çözümleri sunar.

==**Google Ads İle Entegrasyonu**==

![](https://miro.medium.com/v2/resize:fit:386/1*JpHS64h-rJWdaU-CY4BR6A.png)

AdMob, Google ekosisteminin bir parçası olduğu için Google Ads ile sorunsuz bir entegrasyon sunar. Bu entegrasyon, geliştiricilerin uygulama içi reklam gelirlerini artırmak ve reklam performanslarını optimize etmek için güçlü bir araç haline gelir.

Google Ads, reklam verenlerin hedef kitlelere ulaşmasını sağlayan bir platformdur. AdMob, bu platformdan aldığı reklamları mobil uygulamalara entegre eder ve geliştiricilere gösterir. Böylece, uygulama geliştiricileri sadece AdMob üzerinden değil, Google Ads üzerinden de gelen reklamlar ile gelir elde ederler.

==**AdMob Hesabı Oluşturma**==

![](https://miro.medium.com/v2/resize:fit:370/1*5MlRvTWRV4fkiWsWRBd8IA.png)

AdMob hesabı oluşturmak oldukça basittir ve sadece birkaç adımda tamamlanır. İlkin Google hesabınız üzerinden sisteme girin. Genellikle geliştirci hesabınız ile AdMob’u kullanacağınız hesabına aynı olması tavsiye edilir. İki farklı hesapa giriş yapmaya çalışanların çoğu genellikle hata ile karşılaşmaktadırlar. Google hesabınızla giriş yaptıktan sonra Başlayın (Get Started) butonuna tıklayın. Bu tıklama sizi AdMob hesabınızı oluşturma sayfasına yönlendirecektir.

![](https://miro.medium.com/v2/resize:fit:875/1*GhWp5sxu_40e1RZJbSfeZw.png)

Bu aşamadan sonra yardım ve performanstan yararlanılsın mı seçeneği ve ülke seçimi yapılır veAdMob Program Politikaları ve AdMob Hizmet Şartlarını onayladıktan sonra hesabınızın 24 saat içinde AdMob’u kullanmaya uygun olup olmama sürecine girer tabi bu süre zarfında AdMob dashboardı kullanabilirsiniz

![](https://miro.medium.com/v2/resize:fit:875/1*Xc5NktNc647s8qJlN2BlKA.png)

Bu aşamayı da halletikten sonra karşınıza dashboard ekranı çıkacaktır.

![](https://miro.medium.com/v2/resize:fit:875/1*YGBXU66DB3YNlw4aPJw3cw.png)

Dashboardın üstünde göründüğü gibi ödeme bilgilerini girmenizi isteyecektir. Ödeme bilgileri ve kimlik doğrulama adımlarını eksiksiz ve hatasız şekilde doldurmanız lazımdır. Aksi takdirde bi uyuşmazlık olması durumunda hesabınız askıya alınabilir. Bu kısımlarda halledilikten asıl kısımlara geçebiliriz

==**Uygulamaları AdMob’a Bağlama**==

Uygulamanızı AdMob hesabınıza eklemek için ya Başlat butonu üzerinden ya da sol menüdeki Uygulamalar sekmesine tıklayın ve burada Uygulama Ekle butonuna tıklayın. Bu aşamada, uygulamanızın platformunu seçmeniz gerekecektir.

![](https://miro.medium.com/v2/resize:fit:875/1*uSojD-fuKH33y2mTGX_uRg.png)

Bu seçeneklerde uygulamanız yayımlanmış olup olmaması çok önemlidir. Bu aşamalar için farklı adımlar sunulmaktadır. Bu yüzden uygulamanızı eklerken, doğru bilgileri sağlamak önemlidir. Doğru bilgiler girdiğinizden emin olun.

Uygulamanızı AdMob’a başarılı bir şekilde ekledikten sonra, uygulamanızda gösterilecek reklam birimlerini oluşturmanız gerekir. AdMob, banner, geçiş, ödüllü geçiş, yerel gelişmiş vs. tarzda reklam türü sunmaktadır. Bunların detayını AdMob Reklam Biçimleri Ve Stratejileri başlığında detaylı anlatacağım. Reklam türünü seçtikten sonra karşınıza şöyle bir ekran çıkacaktır.

![](https://miro.medium.com/v2/resize:fit:875/1*IPA64EIgF3xSbzSDClT1QA.png)

Bu alanlarıda kendize uygun doldurduktan sonra reklam birimi başarıyla oluşturulmuş oluyor ve size reklam birimini uygulamanıza yerleştirmek için bilgilendirici ekran sunacaktır. Uygulamanıza uygun id ve reklam biriminize uygun id verecektir bunları bi yerde kopyaladıktan sonra Google Mobil Reklamlar SDK’sı Kılavuzundaki talimatları uygulamak lazım ardından seçtiğiniz reklam türüne uygun uygulama kılavuzunda talimatlara uygun biçimde ilerleyin. Bunların detayını sonraki başlıklarda anlatacağım.Şimdilik AdMob’a uygulama bağlama olayı kaba taslak bu şekildedir.

==**SDK Entegrasyonu Ve Teknik Ayarlar**==

![](https://miro.medium.com/v2/resize:fit:293/1*lYb9MKqrKz8gkoh3fZmADQ.jpeg)

Uygulamanın SDK Entegrasyon sürecini Android İşletim Sistemi üzerinden anlatacağım diğer platformların entegrasyon sürecinin dökümanını Kaynaklar bölümünden link olarak sizinle paylaşacağım.

Öncellikle uygulamanın derleme dosyasında minimum sdk sürümü 21 veya daha yüksek olmalı genellikle 34 veya sonrası sdk için daha iyi optimizasyon alırsınız. Oturum açtığınızı, kaydolduğunuzu , uygulamanızın AdMob’a kaydettiğinizi ve AdMob uygulama kimliğinizi almış olduğunuzu farz ederek ilerleyeceğim.

- Gradle ayarlar dosyanızda gerekli şekilde ayarlamanız lazım. (google() ve mavenCentral())

Kotlin -> settings.gradle.kts için

```bash
pluginManagement {  
  repositories {  
    google() **  
    mavenCentral() **  
    gradlePluginPortal()  
  }  
}  
  
dependencyResolutionManagement {  
  repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)  
  repositories {  
    google() **  
    mavenCentral() **  
  }  
}  
  
rootProject.name = "My Application"  
include(":app")
```

Groovy -> settings.gradle için

```bash
pluginManagement {  
  repositories {  
    google() **  
    mavenCentral() **  
    gradlePluginPortal()  
  }  
}  
  
dependencyResolutionManagement {  
  repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)  
  repositories {  
    google() **  
    mavenCentral() **  
  }  
}  
  
rootProject.name = "My Application"  
include ':app'
```

- Google Mobil Reklamlar SDK’sına ilişkin bağımlılıkları uygulama düzeyindeki build.gradle dosyasına ekleyin

Kotlin -> build.gradle.kts

```bash
dependencies {  
  implementation("com.google.android.gms:play-services-ads:23.6.0")  
}

```


Groovy > build.gradle

```bash
dependencies {  
  implementation 'com.google.android.gms:play-services-ads:23.6.0'  
}

```

- AdMob uygulama kimliğinizi AndroidManifest.xml dosyasına ekleyin

<manifest>  
  <application>  
    <!-- Sample AdMob app ID: ca-app-pub-3940256099942544~3347511713 -->  
    <meta-data  
        android:name="com.google.android.gms.ads.APPLICATION_ID"  
        android:value="ca-app-pub-xxxxxxxxxxxxxxxx~yyyyyyyyyy"/>  
  </application>  
</manifest>

- Reklamları yüklemeden önce MobileAds.initialize() çağrısını yaparak Google Mobile Ads SDK’sını ilk kullanıma hazırlayın

Kotlin ->
```kotlin
import com.google.android.gms.ads.MobileAds  
import kotlinx.coroutines.CoroutineScope  
import kotlinx.coroutines.Dispatchers  
import kotlinx.coroutines.launch  
  
class MainActivity : AppCompatActivity() {  
  override fun onCreate(savedInstanceState: Bundle?) {  
    super.onCreate(savedInstanceState)  
    setContentView(R.layout.activity_main)  
  
    val backgroundScope = CoroutineScope(Dispatchers.IO)  
    backgroundScope.launch {  
      // Initialize the Google Mobile Ads SDK on a background thread.  
      MobileAds.initialize(this@MainActivity) {}  
    }  
  }  
}
```

Java ->

```java
import com.google.android.gms.ads.MobileAds;  
import com.google.android.gms.ads.initialization.InitializationStatus;  
import com.google.android.gms.ads.initialization.OnInitializationCompleteListener;  
  
public class MainActivity extends AppCompatActivity {  
  protected void onCreate(Bundle savedInstanceState) {  
    super.onCreate(savedInstanceState);  
    setContentView(R.layout.activity_main);  
  
    new Thread(  
            () -> {  
              // Initialize the Google Mobile Ads SDK on a background thread.  
              MobileAds.initialize(this, initializationStatus -> {});  
            })  
        .start();  
  }  
}
```

Bu adımları da eksiksiz tamamlayabildiyseniz bi sonraki aşamaya yani reklam uygulama aşamasına geçebiliriz.

==**Uygulamanın Test Edilmesi**==

Reklam gösterme aşamasında Banner Reklam aşamasını sizlerle paylaşacağım ama diğer reklam çeşitlerinin projeye uygulanması konusunda yardımcı dökümanların linkleri Kaynaklar kısmına ekleyeceğim.

Banner reklamlar, uygulama düzeninin bir kısmını kaplayan dikdörtgen reklamlardır. Kullanıcılar uygulama ile etkileşimde bulunurken ekranın üst veya alt kısmına sabitlenmiş olarak ya da kullanıcı sayfayı kaydırırken içerikle satır içi şekilde kalırlar. Banner reklamlar, belirli bir süre sonra otomatik olarak yenilenebilir.

Uygulamalarınızı oluşturup test ederken yayındaki üretim reklamları yerine test reklamları kullandığınızdan emin olun. Aksi takdirde hesabınız askıya alınabilir. Test reklamlarını yüklemenin en kolay yolu, Android banner’lar için özel test reklam birimi kimliğini kullanmaktır.

ca-app-pub-3940256099942544/9214589741

Her istek için test reklamları döndürecek şekilde özel olarak yapılandırılmıştır. Kodlama, test etme ve hata ayıklama sırasında kendi uygulamalarınızda kullanabilirsiniz. Uygulamanızı yayınlamadan önce bu kimliği kendi reklam birimi kimliğinizle değiştirdiğinizden emin olun. Test reklamların reklam birim kimlikleri için Kaynaklar kısmında linki bulabilirsiniz.

- AdView Düzeni Ekleme

Tam genişlikte sabitlenmiş uyarlanabilir reklam boyutu oluşturma

Kotlin ->

```kotlin
// Get the ad size with screen width.  
private val adSize: AdSize  
  get() {  
    val displayMetrics = resources.displayMetrics  
    val adWidthPixels =  
      if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.R) {  
        val windowMetrics: WindowMetrics = this.windowManager.currentWindowMetrics  
        windowMetrics.bounds.width()  
      } else {  
        displayMetrics.widthPixels  
      }  
    val density = displayMetrics.density  
    val adWidth = (adWidthPixels / density).toInt()  
    return AdSize.getCurrentOrientationAnchoredAdaptiveBannerAdSize(this, adWidth)  
  }

```

Java ->

```java
// Get the ad size with screen width.  
public AdSize getAdSize() {  
  DisplayMetrics displayMetrics = getResources().getDisplayMetrics();  
  int adWidthPixels = displayMetrics.widthPixels;  
  
  if (VERSION.SDK_INT >= VERSION_CODES.R) {  
    WindowMetrics windowMetrics = this.getWindowManager().getCurrentWindowMetrics();  
    adWidthPixels = windowMetrics.getBounds().width();  
  }  
  
  float density = displayMetrics.density;  
  int adWidth = (int) (adWidthPixels / density);  
  return AdSize.getCurrentOrientationAnchoredAdaptiveBannerAdSize(this, adWidth);  
}

```
Reklam boyutunu kullanarak bir AdView oluşturun ve uygulamaya ekleme

Kotlin ->

```kotlin
// Create a new ad view.  
val adView = AdView(this)  
adView.adUnitId = AD_UNIT_ID  
adView.setAdSize(adSize)  
this.adView = adView  
  
// Replace ad container with new ad view.  
binding.adViewContainer.removeAllViews()  
binding.adViewContainer.addView(adView)
```

Java ->

```java
// Create a new ad view.  
adView = new AdView(this);  
adView.setAdUnitId(AD_UNIT_ID);  
adView.setAdSize(getAdSize());  
  
// Replace ad container with new ad view.  
adContainerView.removeAllViews();  
adContainerView.addView(adView);
```

- Reklam Yükleme

AdView yerleştirildikten sonra bir reklam yüklemeniz gerekir. Bu işlem, AdView sınıfındaki loadAd() yöntemiyle yapılır. Tek bir reklam isteğiyle ilgili hedefleme bilgileri gibi çalışma zamanı bilgilerini içeren bir AdRequest parametresi alır.  
Kotlin ->

```kotlin
// Start loading the ad in the background.  
val adRequest = AdRequest.Builder().build()  
adView.loadAd(adRequest)
```

Java ->

```java
// Start loading the ad in the background.  
AdRequest adRequest = new AdRequest.Builder().build();  
adView.loadAd(adRequest);
```

İşlem başarılı olursa uygulamanız banner reklam göstermeye hazırdır.

- Reklam Etkinlikleri

Reklamın yaşam döngüsünde yükleme, reklam gösterimi ve tıklama ile reklam açma ve kapama etkinlikleri gibi çeşitli etkinlikleri dinleyebilirsiniz. Geri aramayı banner’ı yüklemeden önce ayarlamanız önerilir.

Kotlin ->

```kotlin
adView.adListener = object: AdListener() {  
    override fun onAdClicked() {  
      // Code to be executed when the user clicks on an ad.  
    }  
  
    override fun onAdClosed() {  
      // Code to be executed when the user is about to return  
      // to the app after tapping on an ad.  
    }  
  
    override fun onAdFailedToLoad(adError : LoadAdError) {  
      // Code to be executed when an ad request fails.  
    }  
  
    override fun onAdImpression() {  
      // Code to be executed when an impression is recorded  
      // for an ad.  
    }  
  
    override fun onAdLoaded() {  
      // Code to be executed when an ad finishes loading.  
    }  
  
    override fun onAdOpened() {  
      // Code to be executed when an ad opens an overlay that  
      // covers the screen.  
    }  
}
```

Java ->

```java
adView.setAdListener(new AdListener() {  
    @Override  
    public void onAdClicked() {  
      // Code to be executed when the user clicks on an ad.  
    }  
  
    @Override  
    public void onAdClosed() {  
      // Code to be executed when the user is about to return  
      // to the app after tapping on an ad.  
    }  
  
    @Override  
    public void onAdFailedToLoad(LoadAdError adError) {  
      // Code to be executed when an ad request fails.  
    }  
  
    @Override  
    public void onAdImpression() {  
      // Code to be executed when an impression is recorded  
      // for an ad.  
    }  
  
    @Override  
    public void onAdLoaded() {  
      // Code to be executed when an ad finishes loading.  
    }  
  
    @Override  
    public void onAdOpened() {  
      // Code to be executed when an ad opens an overlay that  
      // covers the screen.  
    }  
});
```

AdListener içindeki geçersiz kılınabilir yöntemlerin her biri, bir reklamın yaşam döngüsündeki bir etkinliğe karşılık gelir. Extradan video reklamlar için donanım hızlandırma aşamaları bulunmaktadır. Yazıma eklemek yerine yardımcı dökümanı Kaynaklar kısmında sizinle paylaşacağım.  
Bu adımları tamamladıktan sonra işin çoğu bitmiş bulunuyor. Şimdi ince ayrıntılara girme zamanı. Bu aşamaya kadar okuduysanız bi takibinizi alırım :))

==**Firebase İle AdMob Entegrasyonu**==

![](https://miro.medium.com/v2/resize:fit:375/1*4UrlZUquD11zPW9kc71H5A.png)

Eğer uygulamanızda Firebase kullanıyorsanız, AdMob reklamlarını da Firebase üzerinden entegre etmeniz gerekecek. Firebase’i kullanarak reklamları göstermek, doğrudan AdMob SDK entegrasyonu ile aynı işlemleri içerir, ancak Firebase Console üzerinden yapılan ayarlamalarla yönetim daha kolay ve merkezi hale gelir.

Firebase SDK’sını Android veya iOS uygulamanıza entegre ettikten sonra, AdMob’un tüm reklam birimlerini ve reklam stratejilerini Firebase üzerinden yönetebilirsiniz. Bu sayede, reklamlarınızı Firebase üzerinden kontrol edebilir ve gerektiğinde ayarlarını değiştirebilirsiniz. Reklam gösterimleri ve ayarlamalar, Firebase Console’daki değişikliklerle uyumlu olarak mobil uygulamanızda doğru şekilde görünecektir.

Eğer uygulamanızda Firebase kullanıyorsanız, AdMob entegrasyonu için Firebase üzerinden işlem yapmanız gereklidir. Bu, daha verimli bir yönetim süreci ve gelişmiş analiz özellikleri sunar.

==**AdMob Reklam Biçimleri**==

![](https://miro.medium.com/v2/resize:fit:555/1*7-q8YyfdMVT56F54bp1cEg.jpeg)

- _Banner Reklamları_

Banner reklamları, uygulamanın üst veya alt kısmında sabit bir şekilde gösterilen küçük reklamlar olup genellikle düşük gelir sağlayan, ancak sürekli görünen reklam türleridir.

- _Interstitial Reklamlar_

Interstitial reklamlar, kullanıcılar bir ekran arasında geçiş yaparken, genellikle tam ekran olarak gösterilen reklamlardır. Bu tür reklamlar, kullanıcıların dikkatini çekme açısından etkilidir ve genellikle uygulamanın geçiş noktalarında kullanılır.

- _Video Reklamlar (Ödüllü ve Otomatik)_

Video reklamlar, kullanıcılara bir video izleyerek ödüller kazanma fırsatı sunar. Bu tür reklamlar genellikle oyun uygulamalarında popülerdir .

- _Native Reklamlar_

Native reklamlar, uygulamanın görünümüne ve içeriğine uyum sağlayarak gösterilen reklam türleridir. Bu reklamlar, uygulamanın doğal akışına entegre edilir ve genellikle daha az dikkat çekicidir, bu da kullanıcıların reklamı daha az fark etmelerini sağlar.

- _App Open Reklamları_

App Open reklamları, uygulama açıldığında gösterilen tam ekran reklamlardır. Bu reklamlar, genellikle kullanıcı uygulamayı ilk açtığında veya uzun süre sonra tekrar açtığında gösterilir.

==**AdMob İle Gelir Optimizasyonu**==

Sadece reklamları uygulamanıza entegre etmek yeterli değildir. Geliriniz artırmak için doğru stratejiler uygulamak ve reklamların performansını sürekli olarak optimize etmek gereklidir.

AdMob, reklamların performansını sürekli olarak izlemek ve analiz etmek için güçlü araçlar sunar. Reklam gelirlerini, tıklama oranlarını (CTR) ve gösterim sayılarını takip ederek hangi reklam türlerinin en verimlii olduğunu anlayabilirsiniz.

- _A/B Testi_

AdMob, A/B testleri ile hangi reklam kombinasyonunun daha iyi performans gösterdiğini bulabilir, böylelikle gelir artışı için efektif adımlar atabilirsiniz.

![](https://miro.medium.com/v2/resize:fit:435/1*suEtxjThJqMyzsSvYbHOiw.png)

==**AdMob Politikaları**==

Hesabınızın askıya alınmaması için bu odaklanarak okumanızı istiyorum. Belirli politikalarla hem reklma verenleri hem de kullanıcıları koruma altına alınması lazım. AdMob, platformunda yayımlanacak reklamlarının belirli standartlara ve etik kurallara uygun olmasını zorunlu kılar. Yasadışı içerikler, yanıltıcı reklamlar ve yanlış reklam yerleştirilmesi yasaktır tespiti durumunda hesabınız askıya alınır.

Bunlarla beraber kullanıcı verisi, trafik manipilasyonu ve yerleşim stratejileri gibi alanlara da dikkat edilmesi gereken çok sayıda kural bulunur. Bunların ek detaylarını Kaynaklar kısmında sizlerle paylaşacağım.

==**AdMob Rakipleri**==

- _Facebook Audience Network (FAN)_

![](https://miro.medium.com/v2/resize:fit:411/1*cC-gRsiQdnFqr5BkM_i2Qg.png)

AdMob’a en güçlü rakiplerinden biridir. Facebook devasa kullanıcı verisi sayesinde FAN’ı oldukça etkili hale getirir.

- _Unity Ads_

![](https://miro.medium.com/v2/resize:fit:401/1*cOYJBQHjRfb5C7VLLAMJbg.jpeg)

Özellikle oyun geliştiricilerin tercih ettiği bir platformdur ve mobil oyunlar için optimize edilmiş reklam servisidir. AdMob’un oyun odaklı rakiplerinden biridir.

- _InMobi_

![](https://miro.medium.com/v2/resize:fit:528/1*XOY9-DB1sxAbxwaeTPhkSw.png)

InMobi, özellikle Asya ve gelişen pazarlarda güçlü bir mobil reklam platformudur. Büyük bir kullanıcı tabanına sahiptir.

- _Tapjoy_

![](https://miro.medium.com/v2/resize:fit:415/1*mv-kAsfM3O8eZo_4oT5M5Q.png)

Tapjoy, özellikle oyun ve uygulama içi ödüllü video reklamlarıyla bilinen bir platformdur. AdMob’a rakip olarak, kullanıcıları reklam izlemeye teşvik etmek için ödüller sunar.

- _Vungle_

![](https://miro.medium.com/v2/resize:fit:398/1*Q0bjjkUENc5UwZsoNnxtRw.jpeg)

Vungle, sadece video reklamları ve özellikle mobil oyunlar için optimize edilmiş bir platformdur. Video reklamlarıyla yüksek gelir elde etme amacı güden geliştiriciler için seçenek olabilir.

AdMob, mobil uygulama geliştiricileri için popüler bir reklam platformu olsa da, rakipleri de güçlü seçenekler sunmaktadır. Her platform, belirli kullanıcı gruplarına, reklam formatlarına veya gelir paylaşım stratejilerine göre farklı avantajlar sağlayabilir. Farklı platformlarda testler yaparak size uygun en iyi performansı veren reklam sağlayıcılarla çalışabilirsiniz.

==**Türkiye’de AdMob Gelirini Alabilme**==

![](https://miro.medium.com/v2/resize:fit:281/1*6Bduv0zPv-Pe1LUMOAFjqg.png)

AdMob, reklam gelirlerinizi toplar ve belirli bir ödeme eşiğini aştığınızda ödemenizi gerçekleştirir. Ödeme eşiğini geçtiğinizde ayın 21'i ile 26'sı arasında ödeme için işlenir. Tr’ de ki kullanıcılar, genellikle banka havalesi yöntemiyle ödemelerini alırlar. Bunun için AdSense veya AdMob hesabınıza bit Türkiye bankasına ait IBAN bilgilerinizi eklemeniz gerekir.

AdMob gelirleri, Türkiye’de vergiye tabidir. Bu nedenle, elde edilen gelirlerin doğru şekilde beyan edilmesi gerekir. Eğer AdMob gelirlerinizi bireysel olarak alıyorsanız, serbet meslek kazancı olarak değerlendirilir ve buna uygun bir gelir vergisi beyanı yapılmaıs gerekir. Şirket sahibiyseniz, gelirlerinizi şirket hesabınıza yönlendirerek kurumlar vergi kapsamında beyan edebilirsiniz. Vergi dairesine kayıtlı değilseniz, bir mali müşavirler çalışarak süreci ilerletebilirsiniz. AdMob gelirleri yurt dışı kazancı olarak değerlendirildiği için yıllık gelir beyanında belirtilmelidir.

AdMob gelirleri, Türkiye’de döviz olarak gelir ve banka hesabınıza yatırılırken ₺’ye çevirilir. Bu kur farkından kaynaklanabilecek kayıpları önlemek adına gelirlerinizin döviz hesabına yatırılmasını sağlamak için bir USD veya EUR hesabı açabilirsiniz. Bankanızı seçerken iyi tercih yapmanızı öneririm bazı bankalar gelen transferlerden işlem ücreti veya havale masrafı altında kesinti yapabiliyor. Tekrardan hatırlatıyorum vergi beyanında eksiklikler veya yanlışlıklar, ileride yasal sorunlara yol açabilir.

AdMob hakkında size anlatacaklarım buraya kadardı. Umarım bu yazım faydalı olmuştur. Başka yazılarımda görüşmek üzere ;)

---
***Abdullah TANRIVERDİ***


