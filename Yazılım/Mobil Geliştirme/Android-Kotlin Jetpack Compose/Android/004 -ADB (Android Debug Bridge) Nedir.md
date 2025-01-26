#Yazılım #MobilGeliştirme #Android

![[Pasted image 20250126221057.jpg|500]]

ADB, Android cihazlarıyla iletişim kurmak için kullanılan bir komut satırı aracıdır. Android cihazlarını bilgisayarınıza bağlayarak çeşitli işlemleri yapabilmenizi sağlar. ADB, Android uygulamaları geliştirirken ve cihazları test ederken oldukça kullanışlıdır. ADB, hem cihazın işletim sistemine erişim sağlar hem de uygulama geliştirme sürecinde yardımcı olur.

==**ADB'nin Temel Bileşenleri:**==

1. **ADB Server**: Bilgisayarınızda çalışan ve ADB istemcileri ile Android cihazları arasındaki bağlantıyı yöneten sunucudur.
2. **ADB Daemon (AdbD)**: Android cihazında çalışan ve ADB komutlarını kabul eden arka planda çalışan bir programdır.
3. **ADB Client**: Kullanıcının komutlarını girdiği ve cihazla etkileşime geçtiği komut satırı aracıdır.


==**ADB Komutları**==

ADB, çok sayıda komutla Android cihazlarıyla etkileşim kurmanızı sağlar. İşte bazı yaygın komutlar:

1. **adb devices**: Bağlı olan Android cihazların listesini gösterir.
    
    - Cihazın doğru şekilde bağlı olup olmadığını kontrol etmek için kullanılır.
2. **adb push [dosya] [hedef dizin]**: Bilgisayardan Android cihaza dosya gönderir.
    
    - Örnek: `adb push myfile.txt /sdcard/`
3. **adb pull [hedef dosya] [dizin]**: Android cihazdan bilgisayara dosya çeker.
    
    - Örnek: `adb pull /sdcard/myfile.txt ./`
4. **adb install [apk dosyası]**: APK dosyasını cihazınıza kurar.
    
    - Örnek: `adb install myapp.apk`
5. **adb uninstall [paket adı]**: Cihazdan bir uygulamayı kaldırır.
    
    - Örnek: `adb uninstall com.example.myapp`
6. **adb logcat**: Android cihazındaki günlükleri (logları) gösterir.
    
    - Cihazdaki hataları, uyarıları veya genel mesajları görmek için kullanılır.
7. **adb shell**: Cihazda komut satırı ortamı açar, cihazın komut satırına erişim sağlar.
    
    - Örnek: `adb shell ls` cihazdaki dosyaların listesini gösterir.
8. **adb reboot**: Cihazı yeniden başlatır.
    
9. **adb sideload [dosya]**: Cihazın yeniden başlatılması sırasında bir ZIP dosyasını yükler.


==**ADB Nasıl Kurulur?**==

1. **Android Studio İle Kurulum**: Android Studio’yu kurarak, ADB aracını ve diğer Android geliştirme araçlarını edinebilirsiniz.
2. **Komut Satırı Kurulumu**: ADB'yi bağımsız olarak da indirip kullanabilirsiniz. Bunun için `platform-tools` paketini indirip, kurulum yapmanız gerekir.

***


***Abdullah TANRIVERDİ***
