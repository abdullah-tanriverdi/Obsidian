#Yazılım #ProgramlamaDilleri #Python 

![[pythonmimarisi.jpg|500]]


**Python Mimarisi**

Python, hem esnekliği hem de kullanım kolaylığı ile popüler bir programlama dilidir. Bu dilin mimarisi, dilin çalışma prensipleri ve temel bileşenlerinin nasıl etkileşime girdiğini anlamamıza yardımcı olur. Python’un mimarisi, dilin performansını, işleyişini ve yazılımlar için sunduğu çeşitli özellikleri şekillendirir. 


==**Python Mimarisi Bileşenleri**==

Python’un mimarisi, dilin çeşitli bileşenleriyle etkileşen bir sistem olarak şekillenir. Bu bileşenler:

1. **Python Derleyicisi (Python Compiler)**
2. **Python Sanal Makinesi (Python Virtual Machine - PVM)**
3. **Python Çalışma Zamanı Ortamı (Python Runtime Environment)**
4. **Python Kütüphaneleri ve Modülleri**
5. **Python Genişletilebilirlik (C Extensions)**
6. **Python Zamanlayıcı (Interpreter)**

<br>

**Python Derleyicisi (Python Compiler)**

Python programları, **Python derleyicisi** tarafından işlenmeden önce **kaynak kodu** şeklinde yazılır. Bu kaynak kod, Python'un **.py** uzantılı dosya formatında saklanır. Python derleyicisi, kaynak kodunu okur ve **bytecode** adı verilen bir ara dilin üretilmesini sağlar. Bytecode, doğrudan makinelerin anlayabileceği bir dil değildir, ancak daha hızlı çalıştırılabilir ve sistem bağımsızdır.

- Python derleyicisi, **CPython** (Python’un en yaygın kullanılan implementasyonu) ile ilişkilidir ve kodu derleyip **bytecode**'a çevirir.
- Python bytecode’u, makine bağımsız olduğu için, farklı platformlarda çalıştırılabilen programlar yazılmasına olanak tanır.


> [!tldr] İPUCU
> Source Code ( Kaynak Kodu ) hakkında bilgi almak için bağlantıya tıklayın [[013 -Source Code]]
> CPython hakkında bilgi almak için bağlantıya tıklayın [[004 -CPython Nedir]]

<br>


 **Python Sanal Makinesi (PVM)**

Python, derlenen bytecode’un çalıştırılmasından sorumlu olan **Python Virtual Machine** (PVM) kullanır. PVM, Python tarafından üretilen bytecode'u makine koduna çeviren bir sanal makinedir. PVM, aslında Python çalışma zamanında (runtime) kodun çalışmasını sağlar.

- PVM'nin önemli bir özelliği, Python bytecode'unu doğrudan çalıştırarak platform bağımsızlığı sunmasıdır.
- PVM, platforma göre farklılık gösterebilir, ancak bytecode’u her zaman aynı şekilde çalıştırır.

<br>


**Python Çalışma Zamanı Ortamı (Runtime Environment)**

Python programlarının çalışması için, bir çalışma zamanı ortamı gereklidir. Çalışma zamanı, Python’un **dış kütüphanelerini** ve **modüllerini** yüklemesi, **bellek yönetimini** ve **çalışma zamanında oluşan istisna (exception) yönetimini** sağlar.

- Python çalışma zamanı ortamı, Python'un ihtiyaç duyduğu temel kütüphaneleri ve kaynakları yükler.
- Python’un **garbage collector**'ı (çöp toplayıcı) burada devreye girer ve bellek yönetimini sağlar.


> [!tldr] İPUCU
> Garbage Collector hakkına bilgi almak için bağlantıya tıkla [[003 -Garbage Collection]]


<br>


**Python Kütüphaneleri ve Modülleri**

Python'un zengin bir kütüphane ekosistemi vardır. Python modülleri ve kütüphaneleri, dilin uygulama alanını genişleten önemli bileşenlerdir. Python’un sahip olduğu bu kütüphaneler, veri analizi, web geliştirme, makine öğrenimi gibi çeşitli alanlarda kullanılır.

- **Modüller**, Python’daki işlevsellikleri gruplayan dosyalardır. Python'da **import** komutu ile modüller kullanılabilir.
- **Kütüphaneler** ise, bir veya birden fazla modülden oluşan büyük koleksiyonlardır. Popüler kütüphaneler arasında **NumPy**, **Pandas**, **TensorFlow** gibi kütüphaneler yer alır.
<br>
**Python Genişletilebilirlik (C Extensions)**

Python, **C dilinde yazılmış** genişletilebilirlik modüllerine sahiptir. Python, performansını artırmak ve daha düşük seviyeli işlevleri yerine getirebilmek için, C dilinde yazılmış modülleri kullanabilir. Bu modüller, Python'un **CPython** implementasyonu ile birlikte çalışır.

- Python’un **C API** kullanarak, C dilinde yazılmış bir modül Python uygulamanıza dahil edilebilir.
- Bu sayede, Python'un hızından ödün vermeden daha yoğun hesaplama yapan kodlar çalıştırılabilir.

<br>
**Python Zamanlayıcı (Interpreter)**

Python’un en temel bileşeni olan **interpreter**, Python kodunun satır satır çalıştırılmasını sağlar. Python, **işlemci bağımsız** bir dil olduğundan, Python kodunun çalıştırılması farklı platformlarda (Windows, Linux, MacOS vb.) aynı şekilde yapılır.

- Python'un zamanlayıcısı, yorumlayıcı bir dil olduğu için **derleme** gerektirmez. Python kodu, çalıştırılmaya başlandığında anında yorumlanır ve işleme sokulur.
- Interpreter, kullanıcı tarafından yazılan Python kodunu okur ve anlamlı komutlara dönüştürür.
 <br>
 
**Python’un Çalışma Prensibi**

**1. Kaynak Kodunun Yazılması**

- **Aşama:** Geliştirici, Python kodunu `.py` dosyası olarak yazar.
- **Rol Oynayan Unsurlar:**
    - Henüz zamanlayıcı ya da çalışma zamanı ortamı devrede değildir.
    - Bu aşamada sadece editör ya da IDE gibi araçlar kullanılır.


**2. Derleme (Bytecode Üretimi)**

- **Aşama:** Python yorumlayıcısı (interpreter), kaynak kodu okur ve optimize edilmiş bir ara kod olan bytecode (`.pyc` dosyası) üretir.
- **Rol Oynayan Unsurlar:**
    - Bu işlem **derleyici** (compiler) tarafından yapılır. Ancak Python'da bu süreç kullanıcıdan gizlidir ve otomatik olarak gerçekleştirilir.
    - Çalışma zamanı ortamı devreye girmez çünkü bu aşama henüz kodun yürütülmesini içermez.
    - Zamanlayıcı bu aşamada kullanılmaz.


**3. Bytecode’un Çalıştırılması (PVM)**

- **Aşama:** Bytecode, Python Virtual Machine (PVM) tarafından okunur ve yürütülür.
- **Rol Oynayan Unsurlar:**
    - **Python Çalışma Zamanı Ortamı (Python Runtime Environment):** Bu aşamada devreye girer. Çalışma zamanı ortamı, aşağıdakiler dahil olmak üzere yürütme sürecini destekler:
        - Değişkenlerin hafızada tutulması.
        - Bellek yönetimi (Garbage Collector).
        - Dinamik tip kontrolü.
        - Standart kütüphanelerin ve modüllerin yüklenmesi.
    - **Zamanlayıcı (Scheduler):**
        - Eğer program birden fazla iş parçacığı (thread) içeriyorsa veya asyncio gibi bir yapı kullanıyorsa, zamanlayıcı devreye girer.
        - Zamanlayıcı, iş parçacıklarının veya eşzamanlı görevlerin (coroutines) sırasını ve zamanlamasını kontrol eder.



**4. Sonuçların Üretilmesi**

- **Aşama:** PVM, bytecode’u çalıştırır ve sonuçları üretir.
- **Rol Oynayan Unsurlar:**
    - Çalışma zamanı ortamı, bu aşamada sonuçların doğru bir şekilde ekrana yazdırılması, dosyalara kaydedilmesi veya başka bir dış ortama gönderilmesini sağlar.
    - Zamanlayıcı, gerektiğinde iş parçacıklarının veya süreçlerin sırasını ayarlamaya devam eder.



**Python Zamanlayıcı ve Çalışma Zamanı Ortamının Kullanıldığı Aşamalar**

|**Aşama**|**Zamanlayıcı**|**Çalışma Zamanı Ortamı**|
|---|---|---|
|Kaynak kodun yazılması|Devrede değil|Devrede değil|
|Bytecode üretimi|Devrede değil|Devrede değil|
|Bytecode’un çalıştırılması|Çoklu iş parçacığı/asenkron durumlarda devrede|Kodun yürütülmesi, bellek yönetimi, modül yükleme vb. işlevlerde devrede|

<br>
**Python’un İşlem Hızı ve Performansı**

Python’un işlem hızı, derlenen dillere (örneğin, C veya C++) kıyasla genellikle daha düşüktür. Ancak Python’un performansı, dış kütüphaneler ve C uzantıları kullanılarak artırılabilir. Örneğin:

- **NumPy** ve **Pandas** gibi kütüphaneler, verimli hesaplamalar yapabilmek için **C** dilinde yazılmıştır ve Python ile entegre bir şekilde çalışır.
- Python'un **JIT (Just-In-Time) derleyicileri** gibi özellikler, çalışma zamanında Python kodunu optimize etmeye yardımcı olabilir.

> [!tldr] İPUCU
> JIT hakkında bilgi almak için bağlantıya tıkla [[002 -JIT vs AOT]]



***
***Abdullah TANRIVERDİ***



