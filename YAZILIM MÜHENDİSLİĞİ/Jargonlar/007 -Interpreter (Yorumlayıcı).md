#Yazılım #Yazılım-Jargon 

Bir interpreter (yorumlayıcı), yüksek seviyeli bir programlama dilinde yazılmış kaynak kodu satır satır analiz eden ve anında çalıştıran bir çalışma zamanı bileşenidir. Yorumlayıcı, kaynak kodu önceden makine diline çevirmek yerine, onu doğrudan yürütür.

**Derleyici ile Karşılaştırma**

Yorumlayıcılar, derleyicilere göre farklı zamanlama ve yürütme stratejileri izler. Derleyiciler bir defaya mahsus çeviri yaparken, yorumlayıcılar kodu her çalıştırmada analiz eder.

| Özellik       | Derleyici (Compiler)           | Yorumlayıcı (Interpreter)        |
| ------------- | ------------------------------ | -------------------------------- |
| Giriş         | Kaynak Kod                     | Kaynak Kod                       |
| Zamanlama     | Derleme Zamanı                 | Çalışma Zamanı                   |
| Performans    | Yüksek                         | Görece Düşük                     |
| Hata Yakalama | Tüm hatalar derleme aşamasında | Hatalar çalışırken tespit edilir |

**Yorumlayıcı Mimarisi**
Yorumlayıcılar, yapısal olarak derleyicilere benzer bazı aşamalar içerir; ancak her aşama çalışma zamanında yorumlamaya hizmet eder.

**Lexical Analyzer (Sözcüksel Çözümleyici)**
- Kaynak kodu token dizisine dönüştürür.

**Syntax Analyzer (Sözdizimsel Çözümleyici)**
- Token’ların dilin gramer kurallarına uygun olup olmadığını denetlemek.

**Semantic Analyzer(Anlamsal Çözümleyici)**
- Anlamsal hataları bulmak(Değişken tanımsız olması, tür uyuşmazlığı vb.)

**Evaluator (Yorumlayıcı Çekirdek)**
- Abstract Syntax Tree (AST) üzerinde gezilerek her düğümün anlamlı bir işlemle karşılık gelmesi sağlanır.


Yorumlayıcılar, yüksek seviyeli programların doğrudan çalıştırılması için kritik bir rol oynar. Modern sistemlerde yorumlayıcılar, JIT (Just-In-Time) derleyicileri ve virtual machine altyapıları ile birleşerek performansı artırmıştır. Yorumlayıcılar, dinamik dillerin gelişmesinde önemli bir rol oynamaya devam etmektedir.


<iframe width="560" height="315" src="https://www.youtube.com/embed/F64_bwahaWQ" title="YouTube video player" frameborder="0" allowfullscreen></iframe>



***
***Abdullah TANRIVERDİ***
