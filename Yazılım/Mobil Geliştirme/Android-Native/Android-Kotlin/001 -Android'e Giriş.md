#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin

Android, Google tarafından geliştirilen açık kaynaklı bir mobil işletim sistemidir.Linux çekirdeği üzerine inşa edilmiş olup, mobil cihazlar ve çeşitli platformlar için tasarlanmıştır. Geliştiriciler, Android uygulamarını yazmak için belli başlı programlama dillerini kullanılabilir.


- **Java**: Android'in ilk ve ana dilidir. Java'nın güçlü nesne yönelimli yapısı, geniş kütüphaneleri ve Android'e özgü araçlarla birleşerek uygulama geliştirme süreçlerini kolaylaştırır.
    
- **Kotlin**: 2017 yılında Google tarafından resmi Android dili olarak duyuruldu. Kotlin, Java'ya kıyasla daha modern, esnek ve okunabilir bir dil olup, geliştiricilere daha güvenli ve hataya dayanıklı kod yazma imkanı sunar. Kotlin ayrıca Java ile tamamen uyumludur, bu da mevcut Java projelerinde Kotlin kullanmaya başlanmasını kolaylaştırır.
    
- **C++**: Android NDK (Native Development Kit) aracılığıyla C++ ile uygulamalar yazmak mümkündür. Özellikle yüksek performans gerektiren oyunlar ve grafik yoğun uygulamalar geliştirilirken tercih edilir. C++ kullanımı genellikle performans optimizasyonu için yapılır, ancak uygulama yönetimi, UI ve diğer platformla ilgili kodlar Java veya Kotlin ile yazılır. 
 <br>
 
> [!tip]  İPUCU
>  Android NDK hakkında bilgi almak için bağlantıya tıkla [[002 -Android NDK]]
<br>
    
- **Dart (Flutter)**: Google tarafından geliştirilen Flutter framework'ü, Android ve IOS için çapraz platform uygulama geliştirmede kullanılan bir araçtır. Dart dilini kullanır ve tek bir kod tabanıyla hem Android hem de IOS uygulamaları geliştirmeyi sağlar. Bu, daha az maliyetle daha geniş bir kitleye ulaşmayı kolaylaştırır.
    
- **JavaScript (React Native)**: Facebook tarafından geliştirilen framework, JavaScript kullanarak Android ve IOS için çapraz platform uygulamaları oluşturmanıza olanak tanır. React Native ile JavaScript, HTML ve CSS bilen geliştiriciler mobil uygulama geliştirmeye geçiş yapabilirler.
    
- **Python**: Android uygulama geliştirmek için doğrudan desteklenmese de Kivy gibi kütüphaneler ile Python kullanarak Android uygulamaları geliştirmek mümkündür. Python, genellikle bilimsel hesaplamalar, yapay zeka ve hızlı prototipleme için tercih edilir.
    
- **C#(Xamarin)**: Microsoft’un Xamarin teknolojisi aracılığıyla Android uygulamaları geliştirmek mümkündür. C# ile hem Android hem de IOS için çapraz platform uygulamaları geliştirebilirsiniz. Xamarin, .NET ekosisteminin avantajlarından yararlanır ve C# geliştiricilerine mobil uygulama dünyasına girmeyi kolaylaştırır.
<br>

**Android'de Java'nın Rolü:**  Android uygulama geliştirmede kullanılan en popüler programlama dillerinden biridir. Sun Microsystems tarafından 1995 yılında geliştirilen, daha sonra Oracle tarafından sahiplenilen, nesne yönelimli bir dildir. Java'nın özellikleri, Android'in temel yapı taşlarından biri olmasını sağlamıştır. Java, Android'de Dalvik ve Android Runtime(ART) sanal makineleri üzerinde çalışır. Android uygulamaları, Java kodu olarak yazılır ve bu kod, önce bytecode formatına dönüştürülür. Bytecode, Android' deki Dalvik ya da ART tarafından çalıştırılır, bu da Java'nın platform bağımsız olma özelliğinin Android cihazlarında uygulanmasını sağlar.

> [!INFO]  Dalvik Virtual Machine (Dalvik VM)
>  Android'in ilk versiyonlarında kullanılan sanal makinedir. Java programlama dilinde yazılmış Android uygulamaları, önce bytecode formatına dönüştürülür ve ardından Dalvik sanal makinesi tarafından çalıştırılmak üzere Dalvik Executable (DEX) formatına derlenir.

> [!INFO] Android Runtime (ART)
>Android 5.0 Lollipop sürümünden itibaren varsayılan çalışma zamanı oldu. Dalvik'in yerini almak için geliştirilmiş ve performans iyileştirmelerine odaklanmıştır. ART, uygulamaların daha hızlı ve daha verimli çalışmasını sağlar.

> [!tip] İPUCU
> 
> Dalvik ve ART hakkında daha fazla bilgi için bu bağlantıya tıkla [[003 -Dalvik Ve ART Nedir]]

<br>

**Android'de Kotlin'in Rolü:**  2017 yılında Google tarafından Android için resmi programlama dili olarak duyurulmuştur. JetBrains tarafından geliştirilen bu modern dil, Java ile birlikte kullanılabilen, daha yalın ve esnek bir programlama dilidir. Kotlin, özellikle Android uygulama geliştirme sürecini daha verimli, güvenli hale getirmeyi amaçlar. Kotlin özellikle daha temiz ve güvenli kod yazmak için güzel bir seçenektir. Android ekosisteminde hızla yaygınlaşan Kotlin, Java ile birlikte uzun vadede Android geliştirme dünyasında büyük bir rol oynuyor.


<br>

**Android Studio:** Android uygulamaları geliştirmek için kullanılan resmi entegre geliştirme ortamı(IDE)'dir. Google tarafından geliştirilen Android Studio, Android SDK (Software Development Kit) ile entegre çalışır ve geliştiricilerle kapsamlı bir geliştirme ortamı sunar. 

<br>

**Android SDK(Software Development Kit):** Android işletim sistemi için uygulama geliştirmek amacıyla kullanılan bir araç ve yazılım kütüphanesidir. SDK, Android uygulamaları oluşturmak, test etmek ve hata ayıklamak için gerekli olan tüm araçları içerir. Android geliştiricileri bu kit aracılığıyla uygulamaları yazabilir, çalıştırabilir ve optimize edebilir.

> [!tip] İPUCU
>  SDK hakkında daha fazla bilgi almak için bu bağlantıya tıkla [[001 -SDK Nedir]]



Özetle, Android işletim sistemi, açık kaynaklı yapısı, geniş geliştirici topluluğu ve kapsamlı araçlarıyla mobil dünyada güçlü bir konuma sahiptir. Java ve Kotlin gibi dillerin yanı sıra Android Studio ve Android SDK, geliştiricilere kullanıcı dostu ve yenilikçi uygulamalar oluşturma imkanı sunar. Dalvik VM’den ART’ye geçiş, Android’in performansını ve verimliliğini artırırken, bu platformun esnek yapısı farklı cihaz ve platformlara uyum sağlamayı mümkün kılar.

---


***Abdullah TANRIVERDİ***
