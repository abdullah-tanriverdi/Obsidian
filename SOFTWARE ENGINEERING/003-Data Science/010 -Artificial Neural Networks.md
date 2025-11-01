#Yazılım #VeriBilimi 

![[Artificial Neural Networks1.jpg|500]]

Yapay Sinir Ağı (YSA), insan beyninden ilham alınarak geliştirilen, veriden öğrenebilen bir matematiksel modeldir. YSA ile basit biyolojiksinir sisteminin çalışma şekli taklit edilir. Yani biyolojik sinir hücrelerinin ve bu hücrelerin birbirleri ile arasında kurduğu sinaptik bağın dijital olarak modellenmesidir. Bir YSA, girdi verisini alır, bunu ağ içindeki nöronlar aracılığıyla işler ve çıktı üretir. Bu çıktı, genellikle bir tahmin, sınıflandırma veya regresyon sonucudur.

Gerçek nöronlar, dendritlerden sinyal alır, bu sinyalleri gövdesinde işler ve aksonla diğer nöronlara gönderir.
Matematiksel nöron ise şöyle çalışır:
```makelife
Girdiler: x₁, x₂, x₃ ...
Ağırlıklar: w₁, w₂, w₃ ...
Bias: b
Toplam: z = w₁x₁ + w₂x₂ + w₃x₃ + b
Aktivasyon: y = f(z)

```

Buradaki f, aktivasyon fonksiyonudur; nöronun çıktısını doğrusal olmayan (non-linear) hale getirir.


**Kısa Tarihçe**
Yapay sinir ağlarının kökeni 1940’lara dayanır.
- **1943:** _McCulloch ve Pitts_, ilk yapay nöron modelini tanıttı.
- **1958:** _Frank Rosenblatt_, veriden öğrenebilen ilk model olan Perceptron’u geliştirdi.
- **1970’ler:** YSA’lar bir süre ilgi kaybetti (donanım yetersizliği ve teorik sınırlar nedeniyle).
- **1986:** _Backpropagation_ algoritmasının yeniden keşfi, alanı canlandırdı.
- **2000’ler sonrası:** Artan işlem gücü ve büyük veri sayesinde “derin öğrenme (Deep Learning)” kavramı doğdu. Bugün yüz tanımadan doğal dil işlemeye kadar birçok alanda YSA tabanlı modeller kullanılmaktadır.


> [!note] Perceptron
> Perceptron, yapay sinir ağlarının atası sayılan ilk öğrenebilen yapay nöron modelidir. 1958’de Frank Rosenblatt tarafından geliştirilmiştir.  
   Basitçe, bir girdi kümesini alır, her girdiye bir ağırlık uygular, bunları toplar ve sonucu bir eşik (threshold) fonksiyonundan geçirerek çıktı üretir.
   Perceptron, girdilerle çıktılar arasında doğrusal bir karar sınırı çizmeye çalışır. Bu nedenle sadece lineer olarak ayrılabilen problemleri çözebilir (örneğin AND, OR kapıları). Ancak XOR gibi doğrusal olmayan ilişkileri öğrenemez — bu sınırlama yüzünden 1970’lerde YSA araştırmaları bir süre duraklamıştır.
   

![[Artificial Neural Networks3.png]]

**Katmanların Yapısı**

Bir yapay sinir ağı, tipik olarak üç tür katmandan oluşur:

- **Girdi Katmanı (Input Layer)**
	Ham veriyi alır. Örneğin bir resimdeki pikseller veya bir tablodaki özellikler
- **Gizli Katmanlar (Hidden Layers)**
	Asıl öğrenme burada olur. Nöronlar arasındaki ağırlıklar, verinin iç ilişkilerini öğrenir.
- **Çıktı Katmanı (Output Layer)**
	Modelin nihai tahmini üretir. Sınıflandırmada olasılık, regresyonda sayısal değer döner.
![[Artificial Neural Networks2.png]]

**Nasıl Öğrenir?**
- **İleri Yayılım (Forward Propagation)**
	Veri, giriş katmanından çıkış katmanına doğru akar. Her nöron girişleri toplar, aktivasyon fonksiyonuyla işler ve bir sonraki katmana aktarır. Bu aşamada tahmin üretilir.
- **Kayıp (Loss / Cost) Hesabı**
	Tahmin edilen değer ile gerçek değer arasındaki fark hesaplanır. Regresyon ve sınıflandırma metotları kullanılarak.
- **Geri Yayılım (Backpropagation)**
	Hata, zincir kuralı chain rule ile katmanlara geri yayılır. Ağ ağırlıkları günceller.

|Ağ Türü|Açıklama|Kullanım Alanı|Özellik|
|:--|:--|:--|:--|
|**Feedforward Neural Network (FFNN)**|Veriler sadece ileri yönde akar; girişten çıkışa doğru.|Basit sınıflandırma, regresyon|En temel YSA yapısı|
|**Convolutional Neural Network (CNN)**|Katmanlar filtrelerle (kernel) yerel özellikleri çıkarır.|Görüntü, video, nesne tanıma|Uzaysal ilişkileri yakalar|
|**Recurrent Neural Network (RNN)**|Önceki çıktıları sonraki girişlerde kullanır; belleği vardır.|Metin, ses, zaman serileri|Zaman bağımlı verilerde başarılı|
|**Generative Adversarial Network (GAN)**|Biri veri üretir (Generator), diğeri gerçek–sahte ayrımı yapar (Discriminator).|Görsel üretim, sahte veri üretimi|Rekabetle öğrenme prensibi|
|**Autoencoder**|Girdiyi sıkıştırıp yeniden üretir.|Boyut indirgeme, gürültü giderme|Özellik öğrenmede güçlü|
|**Transformer**|Dikkat (attention) mekanizmasıyla bağlamı öğrenir.|Doğal dil işleme, çeviri|Paralel işlemeye uygundur|
***
***Abdullah TANRIVERDİ***
