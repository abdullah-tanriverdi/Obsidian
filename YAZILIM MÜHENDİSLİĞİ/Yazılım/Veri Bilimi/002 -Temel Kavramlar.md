#Yazılım #VeriBilimi 

==**Veri (Data)**== 

Veri, gözlemler, ölçümler veya hesaplamalar yoluyla toplanan bilgilerdir. Veri, anlamlı sonuçlara ulaşmak için analiz edilmesi gereken ham bilgidir. İki ana türde veri bulunur:
- **Yapılandırılmış Veri (Structured Data):** İyi tanımlanmış formatlarda, örneğin veri tabanlarında bulunan veriler. Satır ve sütunlardan oluşur.
- **Yapılandırılmamış Veri (Unstructured Data):** Metin, resimler, videolar gibi belirli bir formatı olmayan verilerdir.

==**Veri Tipleri (Data Types)**==

Veri, çeşitli türlerde olabilir. En yaygın veri tipleri şunlardır:
- **Sayısal Veri (Numeric Data):** Sayılarla ifade edilen verilerdir. İki ana türü vardır:
    
    - **Kesirli (Continuous):** Sürekli bir değer alabilen veriler, örneğin boy, ağırlık.
    - **Ayrık (Discrete):** Belirli değerleri alabilen veriler, örneğin öğrenci sayısı.
- **Kategorik Veri (Categorical Data):** Değerler sınıflandırılabilir, ancak sırasızdır. Örneğin, renkler veya cinsiyet.
    
    - **Nominal Veri:** Hiçbir sıralama veya derecelendirme yapılmayan kategorilerdir. Örneğin, şehir isimleri.
    - **Ordinal Veri:** Kategoriler arasında bir sıralama vardır. Örneğin, eğitim seviyesi (ilkokul, ortaokul, lise).
- **Zaman Serisi Veri (Time Series Data):** Zaman içinde düzenli aralıklarla toplanan verilerdir. Örneğin, bir şirketin aylık satışları.

==**Veri Kümesi (Dataset)**==

Veri kümesi, belirli bir konuyu incelemek için toplanmış verilerin bir koleksiyonudur. Veri kümesi, genellikle satırlar (gözlemler) ve sütunlar (değişkenler) şeklinde düzenlenir. Veri kümesindeki her bir satır, bir gözlem birimini, her bir sütun ise bir özelliği temsil eder.


==**Öznitelik (Feature) ve Etiket (Label)**==

- **Öznitelik (Feature):** Veri kümesindeki her sütun bir öznitelik (özellik) temsil eder. Bu özellikler, modelin eğitilmesi için kullanılır.
- **Etiket (Label):** Özellikle denetimli öğrenme (supervised learning) senaryolarında, modelin tahmin yapmaya çalıştığı sonuçları ifade eder. Örneğin, ev fiyatlarını tahmin etmek için "fiyat" bir etikettir.



==**Veri Temizleme (Data Cleaning)**==

Veri temizleme, verilerin analiz için uygun hale getirilmesi sürecidir. Veri temizleme işlemleri şunları içerebilir:

- **Eksik Veriler (Missing Data):** Verilerdeki eksiklikleri tespit etmek ve gidermek.
- **Aykırı Değerler (Outliers):** Verideki olağan dışı değerlerin tespit edilmesi ve gerektiğinde düzeltilmesi.
- **Tutarsızlıklar:** Veri setindeki tutarsızlıkları ve hataları düzeltme.



==**Modelleme (Modeling)**==

Modelleme, veriyi analiz etmek ve tahmin yapmak için matematiksel ve istatistiksel algoritmalar kullanma sürecidir. En yaygın model türleri şunlardır:

- **Regresyon (Regression):** Sürekli veriler için kullanılan bir modelleme tekniğidir. Örneğin, ev fiyatını tahmin etme.
- **Sınıflandırma (Classification):** Etiketli verilerle, veriyi kategorilere ayıran bir modeldir. Örneğin, e-postaların spam olup olmadığını tahmin etme.
- **Kümeleme (Clustering):** Denetimsiz öğrenme tekniğidir ve benzer öğeleri gruplamak için kullanılır. Örneğin, müşteri segmentasyonu.

==**Veri Görselleştirme (Data Visualization)**==

Veri görselleştirme, verinin grafiksel bir şekilde sunulmasıdır. Bu süreç, verinin daha kolay anlaşılmasını sağlar ve analiz sonuçlarının paylaşılmasını kolaylaştırır. Yaygın kullanılan görselleştirme araçları şunlardır:

- **Çizgi Grafikler (Line Charts):** Zaman içindeki değişiklikleri göstermek için kullanılır.
- **Çubuk Grafikler (Bar Charts):** Kategorik verilerin karşılaştırılmasında kullanılır.
- **Isı Haritaları (Heatmaps):** Veri setindeki ilişkileri renkler aracılığıyla görselleştiren grafiklerdir.


==**Model Değerlendirme (Model Evaluation)**==

Model değerlendirme, modelin doğruluğunu ve başarısını ölçme sürecidir. En yaygın kullanılan metrikler:

- **Doğruluk (Accuracy):** Doğru tahminlerin toplam tahminlere oranı.
- **Hassasiyet (Precision) ve Duyarlılık (Recall):** Sınıflandırma modellerinde kullanılan ve doğru pozitif tahminlerin ne kadar anlamlı olduğunu gösteren metrikler.
- **F1 Skoru:** Hassasiyet ve duyarlılığın harmonik ortalamasıdır ve modelin denge performansını ölçer.
- **AUC-ROC Eğrisi:** İyi bir sınıflandırıcı için doğruluk ve hata oranlarını inceleyen bir görselleştirme.


==**Overfitting ve Underfitting**==

- **Overfitting (Aşırı Uygunluk):** Modelin eğitim verisine fazla uyum sağlaması, ancak yeni verilerde zayıf performans göstermesidir. Bu, modelin karmaşıklığından kaynaklanır.
- **Underfitting (Yetersiz Uygunluk):** Modelin veriye yeterince uyum sağlayamaması, genellikle modelin basit veya hatalı olmasından kaynaklanır.



==**Veri Normalizasyonu ve Standardizasyonu**==

- **Normalizasyon (Normalization):** Veriyi belirli bir aralığa (genellikle 0-1) ölçekleme işlemidir. Bu, farklı ölçekteki verilerin eşit bir düzeyde karşılaştırılmasını sağlar.
- **Standardizasyon (Standardization):** Veriyi ortalama 0 ve standart sapması 1 olacak şekilde dönüştürme işlemidir. Bu, algoritmaların daha hızlı ve etkili çalışmasını sağlar.


==**Veri Dağılımı (Data Distribution)**==

Veri dağılımı, verinin nasıl dağılacağını ve hangi aralıkta yoğunlaştığını gösterir. Yaygın veri dağılımları:

- **Normal Dağılım (Gaussian Distribution):** Çoğu veri seti bu dağılıma yaklaşır, ortalamaya yakın değerler daha sık görülür.
- **Uniform Dağılım:** Her değer eşit olasılıkla görülür.
- **Bimodal Dağılım:** İki farklı zirveye sahip olan veri setleri.


==**Bayesyen İstatistik (Bayesian Statistics)**==

Bayesyen istatistik, olasılık teorisine dayalı olarak, önceki bilgilere (önceden belirlenmiş dağılımlar) dayanarak yeni verilerle tahminler yapma yöntemidir. Bayes Teoremi, belirsizliklerin hesaplanmasında ve modelin güncellenmesinde kullanılır.

---
***Abdullah TANRIVERDİ***

