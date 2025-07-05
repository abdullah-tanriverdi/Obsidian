#Yazılım #Yazılım-Jargon 

Derleyici (Compiler), yüksek seviyeli bir programlama dilinde yazılmış kaynak kodu alıp, bunu hedef makine diline (genellikle makine kodu ya da ara kod) çeviren bir yazılımdır. Derleyicinin temel amacı, kaynak kodu çalıştırılabilir hale getirmektir.

Java ⟶ Derleyici ⟶ Makine Dili

**Compiler Mimarisi Aşamaları**
Compiler genellikle iki ana bölüme ayrılır :
- Front-End
- Back-End

**Front-End:**  Kaynak kodun analiz edildiği kısımdır.
**Back-End:**  Kodun optimize edilip hedef dile çevrildiği kısımdır.

**Front-End Aşamaları:**
 **Lexical Analysis(Sözcüksel Analiz)**
- Görev: Kaynak koddan token üretmek.

**Syntax Analysis (Sözdizimsel Analiz)**
- Görev: Token’ların dilin gramer kurallarına uygun olup olmadığını denetlemek.

**Semantic Analysis (Anlamsal Analiz)**
- Görev: Anlamsal hataları bulmak(Değişken tanımsız olması, tür uyuşmazlığı vb.)

**Intermediate Code Generation (Ara Kod Üretimi)**
- Görev: Kaynak kodun makine bağımsız ara dile çevrilmesi.



**Back-End Aşamları:** 

**Code Optimization (Kod Optimizasyonu)**
- Amaç: Daha hızlı, daha küçük ve verimli kod üretimi

**Target Code Generation (Makine Kodu Üretimi)**
- Amaç: Ara kod gerçek işlemciye uygun assembly veya makine diline dönüştürülür.

**Code Linking & Assembly**
- Amaç: Derlenen dosyalar (obj dosyaları), kütüphanelerde birleştirilir. Assembly -> Makine Kodu


**Derleyici Türleri**

|Derleyici Türü|Açıklama|
|---|---|
|**Klasik Derleyici**|C/C++ gibi dilleri doğrudan makine koduna çevirir|
|**Cross Compiler**|Bir mimari için başka bir mimaride derleme yapar (örneğin, ARM kodunu x86 bilgisayarda üretmek)|
|**JIT (Just-In-Time) Compiler**|Kod, çalışma zamanında derlenir (örn. Java, .NET)|
|**Interpreter + Compiler**|Yorumlayıcı ve derleyici kombinasyonu (Python'daki bytecode ve VM yaklaşımı gibi)|
|**Self-Hosting Compiler**|Kendisini derleyebilen derleyiciler (örn. C derleyicisinin C ile yazılması)|
Aşamalar: Lexical → Syntax → Semantic → Intermediate → Optimization → Codegen
Derleyici, sadece dönüşüm değil; analiz, optimizasyon ve hata tespiti de yapar.


<iframe width="560" height="315" src="https://www.youtube.com/embed/s6_MpWRRX8U" title="YouTube video player" frameborder="0" allowfullscreen></iframe>

<br>

<iframe width="560" height="315" src="https://www.youtube.com/embed/d1W-vpuuU5k" title="YouTube video player" frameborder="0" allowfullscreen></iframe>

<br>

<iframe width="560" height="315" src="https://www.youtube.com/embed/9rp0WLE_NHY" title="YouTube video player" frameborder="0" allowfullscreen></iframe>



---

***Abdullah TANRIVERDİ***

