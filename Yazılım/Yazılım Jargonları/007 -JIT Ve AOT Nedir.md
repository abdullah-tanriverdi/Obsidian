#Yazılım #YazılımJargonları

![[JIT_AOT.jpg|500]]


 JIT (Just-In-Time) ve AOT (Ahead-Of-Time) derleme, uygulamaların nasıl derlendiği ve çalıştırıldığı ile ilgili iki farklı yaklaşımdır.

==**JIT Derleme:**== JIT, uygulamanın çalıştığı anda derlendiği bir derleme yöntemidir. Uygulama kodu, çalıştırılmadan önce byte koduna çevrilir ve bu işlem uygulama çalışırken gerçekleşir.

**Avantajları:**

- **Hızlı Geliştirme:** Geliştiriciler, kodlarında yaptıkları değişiklikleri hemen test edebilirler. Uygulama anında çalıştırıldığı için derleme süresi kısalır.
- **Dinamik Optimizasyon:** JIT derleyici, kodun hangi parçalarının daha fazla çalıştığını gözlemleyebilir ve en çok kullanılan parçaları optimize edebilir.
  

**Dezavantajları:**

- **Başlangıç Süresi:** Uygulamanın ilk başlama süresi, JIT derlemesi nedeniyle daha uzun olabilir.
- **Bellek Kullanımı:** JIT derleyici, daha fazla bellek kullanabilir çünkü çalışma zamanında ek bilgi ve optimizasyonlar depolar.
  
==**AOT Derleme:**== AOT, uygulama kodunun, çalıştırılmadan önce tam olarak derlendiği bir yöntemdir. Uygulama, derleme sürecinde doğrudan makine koduna veya makineye yakın bir forma çevrilir.

**Avantajları:**

- **Performans:** AOT ile derlenen uygulamalar, başlangıçta daha hızlı başlar çünkü tüm kod daha önce derlenmiştir.
- **Bellek Kullanımı:** Daha az bellek kullanımı ile sonuçlanabilir çünkü çalışma zamanı için daha az ek bilgi tutulur.


**Dezavantajları:**

- **Geliştirme Süresi:** Geliştiricilerin kodda yaptıkları değişikliklerin etkisini görmek için uygulamayı yeniden derlemeleri gerekebilir, bu da geliştirme süresini uzatır.
- **Daha az dinamik optimizasyon:** Uygulama çalıştığı süre boyunca kod optimizasyonları yapılamaz.

<br>

==**JIT Kullanım Senaryosu**==

**Senaryo:** Mobil Uygulama Geliştirme

- **Açıklama:** Bir mobil uygulama geliştiriyorsanız, uygulamanız üzerinde sık sık değişiklikler yapmanız gerekebilir. Örneğin, bir kullanıcı arayüzü (UI) bileşeninin tasarımını değiştirmek veya yeni bir özellik eklemek istiyorsunuz. JIT derlemesi, bu tür değişiklikleri hızlı bir şekilde test etmenizi sağlar.
    
- **Kullanım:** Uygulamanızı Dart SDK ile geliştirdiğinizde, `flutter run` komutunu kullanarak uygulamanızı çalıştırdığınızda JIT derleyici devreye girer. Böylece kod değişikliklerinizi anında görebilir ve uygulamanızı hızlıca güncelleyebilirsiniz.
    

==**AOT Kullanım Senaryosu**==

**Senaryo:** Üretim Ortamında Mobil Uygulama Dağıtımı

- **Açıklama:** Uygulamanız geliştirme aşamasını tamamladıktan sonra, artık son kullanıcılar için hazır hale getirilmesi gerekir. Bu noktada performans ve kullanıcı deneyimi önem kazanır. AOT derlemesi, uygulamanızın daha hızlı başlatılmasını ve daha az bellek kullanmasını sağlar.
    
- **Kullanım:** Uygulamanızı üretim ortamına dağıtmak için `flutter build apk` komutunu kullanarak AOT derlemesi ile bir APK dosyası oluşturursunuz. Bu işlem, uygulamanızın tüm kodunu makine koduna derler. Kullanıcılar uygulamayı yüklediklerinde, daha hızlı bir açılış ve daha akıcı bir deneyim yaşarlar.


  
<iframe width="600" height="300" src="https://www.youtube.com/embed/8hqMK_lhWdE?start=59" frameborder="0" allowfullscreen></iframe>


> [!note] KISACA
> **JIT:** Geliştirme sürecinde, sürekli değişiklik yaparak hızlı geri bildirim almak için kullanılır.
> **AOT:** Üretim ortamında, performansın kritik olduğu durumlarda, kullanıcı deneyimini artırmak için tercih edilir.

***
***Abdullah TANRIVERDİ***
