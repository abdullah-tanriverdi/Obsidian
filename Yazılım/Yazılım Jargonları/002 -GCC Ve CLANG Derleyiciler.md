#Yazılım #Yazılım-Jargon 

![[Pasted image 20250126212646.png|400]]

==**GCC (GNU Compiler Collection)**==
GCC, GNU Projesi tarafından geliştirilen açık kaynak kodlu bir derleyici ailesidir. C, C++, Objective-C, Fortran, Ada, Go gibi birçok programlama dilini destekler. Unix tabanlı işletim sistemleri için yaygın olarak kullanılan bir araçtır.

**Özellikleri:**
- **Çoklu Dil Desteği:** C, C++, Fortran, Ada, Go ve daha birçok dili derleyebilir.
- **Taşınabilirlik:** Çeşitli işletim sistemlerinde ve işlemci mimarilerinde çalışır.
- **Optimize Etme:** Kod performansını artıran çeşitli optimizasyon teknikleri içerir.
- **Açık Kaynaklı:** GNU Genel Kamu Lisansı (GPL) ile dağıtılır, bu nedenle ücretsizdir ve kaynak kodu erişilebilirdir.
- **Geniş Topluluk Desteği:** Sürekli olarak geliştirilen ve geniş bir kullanıcı topluluğu tarafından desteklenen bir derleyicidir.

**Kullanımı:**

Bir C programını derlemek için:
```bash
gcc -o cikti dosya.c

```

- **`-o`**: Çıkış dosyasının adını belirtir.
- **`-Wall`**: Tüm uyarıları etkinleştirir.
- **`-O2`**: İkinci seviyede optimizasyon yapar.

**Avantajları:**

- Yaygın ve köklü bir derleyici.
- Çeşitli platformları destekler.
- Geliştiricilere çok sayıda araç sunar.

**Dezavantajları:**

- Büyük projelerde daha yavaş derleme süresine neden olabilir.
- Varsayılan hata mesajları bazen kullanıcı dostu olmayabilir.



==**Clang**==
Clang, LLVM (Low Level Virtual Machine) projesi kapsamında geliştirilmiş bir derleyicidir. C, C++ ve Objective-C gibi diller için optimize edilmiştir. GCC'ye benzer bir şekilde çalışsa da daha modern bir tasarıma sahiptir.

**Özellikleri:**

- **Hızlı Derleme:** GCC’ye göre daha hızlı derleme sürelerine sahip olabilir.
- **Modüler Tasarım:** LLVM altyapısını kullanarak daha esnek bir tasarım sunar.
- **Gelişmiş Hata Mesajları:** Daha ayrıntılı ve kullanıcı dostu hata ve uyarı mesajları sağlar.
- **Açık Kaynaklı:** BSD lisansı ile dağıtılır, bu nedenle ticari kullanım için daha uygundur.
- **Araç Zinciri:** Static analysis (statik analiz) ve kod biçimlendirme gibi ek araçlar içerir.

**Kullanımı:**

Bir C programını derlemek için:
```bash
clang -o cikti dosya.c

```
- **`-Weverything`**: Tüm uyarıları etkinleştirir.
- **`-fsanitize=address`**: Hafıza hatalarını tespit etmek için "AddressSanitizer" özelliğini etkinleştirir.

**Avantajları:**

- Daha anlaşılır hata mesajları.
- Modern ve modüler tasarım.
- Hızlı geliştirme ve yeni özelliklerin entegrasyonu.
- GCC ile büyük ölçüde uyumlu komutlar.

**Dezavantajları:**

- GCC kadar eski ve yaygın değil.
- Daha az sayıda platformu destekleyebilir.

==**GCC ve Clang Karşılaştırması**==

|Özellik|GCC|Clang|
|---|---|---|
|**Lisans**|GPL|BSD|
|**Performans**|Daha uzun derleme süresi|Daha hızlı derleme|
|**Hata Mesajları**|Daha az kullanıcı dostu|Daha detaylı ve kullanıcı dostu|
|**Taşınabilirlik**|Daha geniş platform desteği|Daha sınırlı platform desteği|
|**Topluluk Desteği**|Daha büyük ve köklü bir topluluk|Daha küçük ancak aktif bir topluluk|
***

***Abdullah TANRIVERDİ***
