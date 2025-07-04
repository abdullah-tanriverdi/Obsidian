#Yazılım #Yazılım-Jargon 

![[JIT_AOT.jpg|500]]


 JIT (Just-In-Time) ve AOT (Ahead-Of-Time) derleme, uygulamaların nasıl derlendiği ve çalıştırıldığı ile ilgili iki farklı yaklaşımdır.

**JIT Derleme:** JIT, uygulamanın çalıştığı anda derlendiği bir derleme yöntemidir. Uygulama kodu, çalıştırılmadan önce byte koduna çevrilir ve bu işlem uygulama çalışırken gerçekleşir.

- **Kaynak kod → Bytecode** (örneğin Java’da `javac` ile `.class` dosyası)
    
- JVM uygulamayı çalıştırmaya başlar.
    
- JVM, sık çalışan (“hot path”) kodları tespit eder.
    
- Bu kod parçaları JIT tarafından optimize edilerek makine koduna çevrilir.
    
- Gelecek çalışmalarda bu optimize kod doğrudan çalıştırılır.

**Avantajları:**

- **Hızlı Geliştirme:** Geliştiriciler, kodlarında yaptıkları değişiklikleri hemen test edebilirler. Uygulama anında çalıştırıldığı için derleme süresi kısalır.
- **Dinamik Optimizasyon:** JIT derleyici, kodun hangi parçalarının daha fazla çalıştığını gözlemleyebilir ve en çok kullanılan parçaları optimize edebilir.
  

**Dezavantajları:**

- **Başlangıç Süresi:** Uygulamanın ilk başlama süresi, JIT derlemesi nedeniyle daha uzun olabilir.
- **Bellek Kullanımı:** JIT derleyici, daha fazla bellek kullanabilir çünkü çalışma zamanında ek bilgi ve optimizasyonlar depolar.
  
**AOT Derleme:** AOT, uygulama kodunun, çalıştırılmadan önce tam olarak derlendiği bir yöntemdir. Uygulama, derleme sürecinde doğrudan makine koduna veya makineye yakın bir forma çevrilir.

- Geliştirici kaynak kodu ya da bytecode’u AOT derleyicisine verir.
    
- Derleyici, hedef makine mimarisine özel yerel kod üretir.
    
- Uygulama çalıştığında, doğrudan bu makine kodu çalışır – JIT gerekmez.

**Avantajları:**

- **Performans:** AOT ile derlenen uygulamalar, başlangıçta daha hızlı başlar çünkü tüm kod daha önce derlenmiştir.
- **Bellek Kullanımı:** Daha az bellek kullanımı ile sonuçlanabilir çünkü çalışma zamanı için daha az ek bilgi tutulur.


**Dezavantajları:**

- **Geliştirme Süresi:** Geliştiricilerin kodda yaptıkları değişikliklerin etkisini görmek için uygulamayı yeniden derlemeleri gerekebilir, bu da geliştirme süresini uzatır.
- **Daha az dinamik optimizasyon:** Uygulama çalıştığı süre boyunca kod optimizasyonları yapılamaz.

<br>

**JIT Kullanım Senaryosu**

**Senaryo:** Mobil Uygulama Geliştirme

- **Açıklama:** Bir mobil uygulama geliştiriyorsanız, uygulamanız üzerinde sık sık değişiklikler yapmanız gerekebilir. Örneğin, bir kullanıcı arayüzü (UI) bileşeninin tasarımını değiştirmek veya yeni bir özellik eklemek istiyorsunuz. JIT derlemesi, bu tür değişiklikleri hızlı bir şekilde test etmenizi sağlar.
    
- **Kullanım:** Uygulamanızı Dart SDK ile geliştirdiğinizde, `flutter run` komutunu kullanarak uygulamanızı çalıştırdığınızda JIT derleyici devreye girer. Böylece kod değişikliklerinizi anında görebilir ve uygulamanızı hızlıca güncelleyebilirsiniz.
    

**AOT Kullanım Senaryosu**

**Senaryo:** Üretim Ortamında Mobil Uygulama Dağıtımı

- **Açıklama:** Uygulamanız geliştirme aşamasını tamamladıktan sonra, artık son kullanıcılar için hazır hale getirilmesi gerekir. Bu noktada performans ve kullanıcı deneyimi önem kazanır. AOT derlemesi, uygulamanızın daha hızlı başlatılmasını ve daha az bellek kullanmasını sağlar.
    
- **Kullanım:** Uygulamanızı üretim ortamına dağıtmak için `flutter build apk` komutunu kullanarak AOT derlemesi ile bir APK dosyası oluşturursunuz. Bu işlem, uygulamanızın tüm kodunu makine koduna derler. Kullanıcılar uygulamayı yüklediklerinde, daha hızlı bir açılış ve daha akıcı bir deneyim yaşarlar.

| Özellik              | JIT                                | AOT                                   |
| -------------------- | ---------------------------------- | ------------------------------------- |
| Derleme Zamanı       | Çalışma zamanı (runtime)           | Derleme zamanı (build time)           |
| Başlama Süresi       | Geç (çünkü derleme sonradan olur)  | Hızlı (çünkü doğrudan makine kodu)    |
| Koşu Performansı     | Genellikle yüksek (optimizasyonlu) | İyi ama JIT kadar dinamik değil       |
| Dinamik Optimizasyon | ✔ (profil tabanlı)                 | ✘ (statik)                            |
| Bellek Kullanımı     | Daha fazla (çünkü JIT cache tutar) | Daha az                               |
| Platform Bağımsızlık | ✔ (bytecode taşınabilir)           | ✘ (hedef platforma bağlı makine kodu) |

**JIT Mimarisi**

```text

JIT
        [ Kaynak Kod ]
              ↓
        [ Derleyici (javac / csc) ]
              ↓
        [ Ara Kod (Bytecode / IL) ]
              ↓
        [ Sanal Makine (JVM / CLR) ]
              ↓
      ┌────────────────────────────┐
      │  JIT Derleyici             │
      │  (HotSpot / RyuJIT / etc.)│
      └────────────────────────────┘
              ↓
       [ Makine Kodu ] → CPU

```

**AOT Mimarisi**

```text
AOT
        [ Kaynak Kod ]
              ↓
      ┌────────────────────────────┐
      │ AOT Derleyici              │
      │ (LLVM, GraalVM Native,    │
      │  .NET Native, Clang, ART) │
      └────────────────────────────┘
              ↓
     [ Makine Kodu / Native Binary ]
              ↓
            CPU (Doğrudan çalıştırılır)

```


<iframe width="600" height="300" 
    src="https://www.youtube.com/embed/5rn_MAspYFM?list=PLrdBiaxMhrdx33G3hFK0vO4NwlAy0FGf8" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
</iframe>



> [!note] KISACA
> **JIT:** Geliştirme sürecinde, sürekli değişiklik yaparak hızlı geri bildirim almak için kullanılır.
> **AOT:** Üretim ortamında, performansın kritik olduğu durumlarda, kullanıcı deneyimini artırmak için tercih edilir.

***
***Abdullah TANRIVERDİ***
