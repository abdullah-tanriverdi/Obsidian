#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin


![[Pasted image 20250126201752.jpg]]

==**Dalvik (Android'in Eski Runtime'ı)**==
Dalvik, Android işletim sisteminin ilk zamanlarında uygulamaların çalıştırılması için kullanılan bir sanal makineydi. 2008 yılında, Android'in ilk sürümlerinde, Dalvik ile uygulamalar çalıştırılmaktaydı.



==**Dalvik Özellikleri:**==

- **Java Bytecode'u**: Dalvik, Java dilinde yazılmış uygulamaları çalıştırmak için tasarlanmıştı. Ancak, Java'nın bytecode'u, Dalvik'in kendi formatına dönüştürülüyordu. Android uygulamaları, `.apk` uzantılı dosyalar içinde yer alırken, bu dosyalar Dalvik Virtual Machine (DVM) tarafından çalıştırılmak üzere dönüştürülür.
- **Düşük Bellek Kullanımı**: Dalvik, Java Sanal Makinesi'ne (JVM) göre daha düşük bellek tüketimiyle çalışmak üzere optimize edilmiştir. Bu, mobil cihazlarda sınırlı bellek ve işlem gücü göz önüne alındığında önemliydi.
- **Her Uygulama için Ayrı Süreç**: Dalvik, her uygulamayı ayrı bir süreçte çalıştırıyordu. Bu, Android'in çoklu görev yeteneklerini sağlamasına yardımcı oluyordu.

==**Dalvik'in Çalışma Prensibi:**==

1. **Kodun Derlenmesi**: Java'da yazılmış uygulama kodu, önce bytecode'a derlenir (class dosyaları).
2. **DEX Formatına Dönüştürme**: Bu bytecode daha sonra Dalvik Executable (DEX) formatına dönüştürülür. DEX formatı, Dalvik'in çalıştırabileceği şekilde optimize edilmiştir.
3. **Çalıştırma**: DEX dosyası Dalvik VM tarafından çalıştırılır.

Dalvik zamanla yerini ART'e bırakmıştır, çünkü ART, daha hızlı ve verimli çalışabilen bir çözüm sunmaktadır.


==**ART (Android Runtime)**==

ART, Android 5.0 (Lollipop) ile Dalvik'in yerine geçmiştir. ART, daha hızlı uygulama çalıştırma ve daha az bellek kullanımı sağlamak amacıyla geliştirilmiş bir runtime ortamıdır.

==**ART Özellikleri:**==

- **Ahead-of-Time (AOT) Derleme**: Dalvik, uygulamaları her çalıştırıldığında bytecode'u yorumlayarak çalıştırıyordu. ART, bu bytecode'u uygulama yüklenirken derler. Bu sayede uygulama çalıştırılmadan önce derleme işlemi tamamlanır ve uygulama çalıştırılmaya hazır hale gelir.
- **Daha Yüksek Performans**: ART, AOT derleme sayesinde daha hızlı uygulama çalıştırma imkanı sunar. Bu, Dalvik'e göre daha iyi bir kullanıcı deneyimi sağlar.
- **Geliştirilmiş Bellek Yönetimi**: ART, daha etkili bellek yönetimi ile Dalvik'ten daha verimli çalışır.
- **Garbage Collection İyileştirmeleri**: ART, çöp toplama (Garbage Collection) işlemlerini optimize ederek daha az bellek kullanımı ve daha az gecikme sağlar.

==**ART'in Çalışma Prensibi:**==

1. **Kodun Derlenmesi**: Uygulama yüklendiğinde, bytecode ART tarafından AOT yöntemiyle derlenir.
2. **Çalıştırma**: Derlenen kod, sistemdeki bir C++ kodu gibi çalıştırılır. Bu, Dalvik'in her seferinde bytecode'u yorumlayarak çalıştırmasından çok daha hızlıdır.



==**Dalvik ve ART Arasındaki Farklar:**==

|Özellik|Dalvik|ART|
|---|---|---|
|**Derleme Yöntemi**|JIT (Just-in-Time)|AOT (Ahead-of-Time)|
|**Performans**|Daha düşük, her seferinde yorumlama|Daha yüksek, derleme işlemi uygulama yüklemesinde yapılır|
|**Bellek Yönetimi**|Daha az verimli|Daha verimli, optimize edilmiş|
|**Çöp Toplama**|Yavaş ve sık yapılan çöp toplama|Daha hızlı ve optimize edilmiş|
|**Uygulama Başlatma Süresi**|Uzun (her seferinde yorumlama)|Kısa (önceden derlenmiş kod kullanılır)|
|**Desteklenen Android Sürümü**|Android 4.4 ve öncesi|Android 5.0 (Lollipop) ve sonrası|

![](https://www.youtube.com/watch?v=0J1bm585UCc)


***


***Abdullah TANRIVERDİ***
