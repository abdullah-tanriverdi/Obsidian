#Yazılım #Yazılım-Jargon 



![[garbage collector.jpg|500]]

Garbage Collector, bir yazılımın çalışması sırasında artık kullanılmayan bellek alanlarını otomatik olarak serbest bırakan bir mekanizmadır. Bu, bellek sızıntılarını önler ve programın performansını optimize eder.

==**Garbage Collector'ın Amacı**==

- **Bellek Yönetimi:** Kullanıcı tarafından oluşturulan nesnelerin bellekten ne zaman serbest bırakılacağını otomatik olarak belirler.
- **Manuel Müdahaleye Gerek Yoktur:** Geliştiricinin bellek tahsisi veya serbest bırakma işlemi yapmasına gerek kalmaz.
- **Performans İyileştirme:** Bellek sızıntılarının önüne geçerek uzun süreli çalışan uygulamalarda performans düşüşünü engeller.

==**Garbage Collector Nasıl Çalışır?**==

Garbage Collector genellikle şu adımlarla çalışır:

 **1. Bellek Taraması**

- **Kullanılan ve Kullanılmayan Nesneleri Belirleme:**
    - Bellekte yer alan tüm nesneleri tarar.
    - Artık hiçbir referansı olmayan nesneler "çöp" (garbage) olarak işaretlenir.

**2. Çöpün Toplanması**

- Kullanılmayan nesnelerin bellekten temizlenmesi işlemidir.
- Temizlenen bellek alanı yeniden kullanılabilir hale gelir.

**3. Belleğin Yeniden Kullanımı**

- Serbest bırakılan alan, yeni nesneler için kullanılabilir.

<iframe width="600" height="300" src="https://www.youtube.com/embed/Z7egyIzL89Y?start=307" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


==**Garbage Collector Algoritmaları**==

GC, farklı algoritmalar kullanarak bellek yönetimini optimize eder:

 **1. Referans Sayımı (Reference Counting)**

- **Nasıl Çalışır?**
    - Her nesneye bir referans sayacı eklenir.
    - Bir referans eklendiğinde sayaç artırılır, referans kaldırıldığında azaltılır.
    - Sayaç sıfır olduğunda nesne serbest bırakılır.
- **Avantaj:** Gerçek zamanlıdır, hızlı çalışır.
- **Dezavantaj:** Dairesel referansları temizleyemez.

**2. İşaretle ve Süpür (Mark and Sweep)**

- **Nasıl Çalışır?**
    - Tüm nesneler "canlı" veya "çöp" olarak işaretlenir.
    - Çöp olarak işaretlenen nesneler bellekten temizlenir.
- **Avantaj:** Dairesel referans sorunlarını çözebilir.
- **Dezavantaj:** Tarama işlemi maliyetlidir.

<iframe width="600" height="300" src="https://www.youtube.com/embed/c32zXYAK7CI?start=59" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





**3. Kopyalama (Copying)**

- **Nasıl Çalışır?**
    - Bellek iki bölgeye ayrılır: Aktif ve pasif bölge.
    - Canlı nesneler aktif bölgeden pasif bölgeye kopyalanır, çöp olanlar bırakılır.
- **Avantaj:** Bellek parçalanmasını önler.
- **Dezavantaj:** Bellek kullanımı açısından maliyetlidir.

**4. Nesilsel (Generational) GC**

- **Nasıl Çalışır?**
    - Bellek, yaşlarına göre nesiller olarak bölünür: Genç (young), olgun (old), kalıcı (permanent).
    - Genç nesiller sık sık temizlenir, olgun nesiller daha nadir.
- **Avantaj:** Performansı artırır çünkü genç nesneler genellikle kısa ömürlüdür.
- **Dezavantaj:** Algoritmanın karmaşıklığı.

**5. Sayfa Tabanlı (Page-Based)**

- Belleği sayfalara bölerek her bir sayfanın doluluk durumuna göre temizlik yapar.

==**Garbage Collector’ın Performans Etkileri**==

1. **Dur-Kalk Süresi (Stop-the-World Pause):**
    
    - GC çalışırken programın duraklamasına neden olabilir.
    - Bu durumu minimize etmek için GC optimizasyonları yapılır.
2. **Bellek Parçalanması:**
    
    - Kopyalama GC ve sıkıştırma teknikleri, parçalanmayı önlemek için kullanılır.
3. **Oyun ve Gerçek Zamanlı Sistemlerde GC:**
    
    - GC'nin duraklama süreleri gerçek zamanlı sistemlerde sorun yaratabilir.
    - Bu durumlar için **Incremental GC** veya **Low-Latency GC** kullanılır.

> [!info] BİLGİ
>  **Incremental GC**
Çöp toplama işlemini küçük parçalara bölerek kısa duraklamalarla yapar. Program akışı daha az kesintiye uğrar, bu yüzden kullanıcı deneyimi daha akıcıdır. Özellikle oyunlar ve kullanıcı arayüzleri için uygundur.


> [!info] BİLGİ
>**Low-Latency GC**
Çöp toplama işlemini ana iş parçacığını durdurmadan arka planda yapar. Kesintisiz çalışma ve düşük gecikme sağlar. Gerçek zamanlı sistemler, finans uygulamaları ve oyun motorları için idealdir.


---

***Abdullah TANRIVERDİ***








