#VeriBilimi #Yazılım 

Yapay sinir ağındaki bir nöronun aktivasyon fonksiyonu, nöronun girdilerinden gelen değerlerin toplamını kullanarak nöronun çıktısını hesaplamaya yardımcı olan matematiksel fonksiyondur. Sinir ağının her nöronu, gelen sinyali sadece toplamaz; yorumlar. İşte bu yorumu belirleyen şey aktivasyon fonksiyonudur. O olmadan, ağ sadece toplama-çarpma yapan sıradan bir hesap makinesidir. Aktivasyon fonksiyonu doğrusal olmadığı sürece, sadece birkaç nöron kullanılarak bile karmaşık problemler çözülebilir. Bir köpeği kediden, bir kalp atışını arızalı olandan ayırabilen şey işte bu doğrusal olmayan dönüşümdür.

Matematiksel olarak, her nöronun çıktısı :
`y=f(z)=f(Wx+b)`

- x: girdi vektörü
- W: ağırlıklar
- b: bias
- z=Wx+bz = Wx + bz=Wx+b: toplam giriş
- f: aktivasyon fonksiyonu

Eğer bu fonksiyon doğrusal (linear) olsaydı, ağ ne kadar katmanlı olursa olsun yine tek katmanlı bir modele indirgenirdi. Bu yüzden _doğrusal olmayanlık_, derin öğrenmenin “beyin gücü”dür.

**Görevleri**
- Doğrusal olmayanlık kazandırır.
- Öğrenmeyi yönlendirir.
- Çıktı aralığını kontrol eder.
- Ağ stabilitesini etkiler.


**Step (Basamak) Fonksiyonu**
![[Activation Function2.png]]

Pereptron modeli bu fonksiyonla çalışıyordu. Bir sinyalin belli bir eşiği geçerse "1" (aktif), geçmezse "0" (pasif) dönerdi.

![[Activation Function1.svg]]
Değer kümesi -> {0,1}

Buradaki kapsam bir nöron yeterince uyarı almazsa ateşlenmez. Tüm karar çizgisi dümdüzdür. Yani evet veya hayır ama bu kadar bir katı sistem öğrenemez çünkü küçük bir değişiklik bile sonucu aniden sıfırdan bir atlatır, türevi (değişim oranı) yoktur. Step fonksiyonu duyarsız bir öğretmen gibidir. 50'nin üstü geçer, altı kalır ama kimseye nasıl ilerleyeceğini söylemez.

**Sigmoid (Lojistik) Fonksiyonu**

![[Activation Function3.png]]

Sigmoid, bir dönüm noktasıdır çünkü artık fonksiyon sürekli ve türevi alınabilinir. Yani hata azaldıkça ağırlıklar ince ayarlanabilir.


![[Activation Function4.svg]]
Değer kümesi -> (0,1)

- Küçük girdiler → 0’a yaklaşır.
- Büyük girdiler → 1’e yaklaşır.
- Orta değerler → 0.5 civarı, yani belirsizlik bölgesi.
  
Bu fonksiyon beynin emin değilim ama sanırım böyle dediği yerdir. Olasılık gibi düşünür. Bu görüntü bir kedir olma olasılığı %73. Burada ki sorun aşırı büyük veya küçük değerlerde fonksiyon doygunlaşır. Bu da öğrenmeyi dondurur. Sigmoid, çok nazik bir öğrencidir. Büyük hatalı bile önemli değil diye yumuşatır. Bu da bazen fazla iyi niyetli olur.


> [!note] Vanishing Gradient
> Bir aktivasyon fonksiyonu doygunlaştığında yani girdi değeri çok büyük veya küçük olduğunda çıktısı artık değişmez hale gelir örneğin sigmoid'in 1 ve ya 0'a yaklaşması gibi. Bu durumda fonksiyonun türevi çok küçülür ve neredeyse sıfır olur. Eğitim sırasında geriye doğru hatayı yayarken (backpropagation), bu küçük türevler katmanlardan geçerken daha da küçülür. Sonuçta ağ öğrenmez hale gelir ve buna da vanishing gradient kaybolan gradyan denir.

> [!success] Vanish Gradient
> Bir sinir ağı öğrenirken, yaptığı hatayı biraz düzeltir. Bu düzeltme, gradient gradyan denen küçük yönlendirme sinyalleriyle olur. Yani şurayı biraz artır, burayı biraz azalt gibi. Ama bazı durumlarda bu sinyaller kaybolur. Neden mi? Çünkü aktivasyon fonksiyonu yani nöronun karar mekanizması bazı sayılarda artık tepki vermemeye başlar. Diyelim ki bu fonksiyonu bir ışık düğmesi gibi. Ortada olduğunda ayarılya oynarsın, ışık artar ya da azalır ama düğmeyi en sona kadar çevirirsen, artık ne kadar zorlarsan zorla ışık daha fazla artmaz işte bu noktada doygunlaşma olur. Böyle olunca ağın öğrenmesi için gereken sinyal neredeyse sıfıra iner. Bu sinyal katmanlardan geçtikçe daha da zayıflar, sonunda tamamen kaybolur. Ağ hiçbir şey öğrenemez hale gelir.

> [!note] Backpropagation
> Sinir ağının yaptığı hatayı geriye doğru yayarak her katmandaki ağırlıkları güncelleme yöntemidir. Yani ağ önce tahmin yapar sonra hatayı hesaplar ardından bu hatayı katman katman geriye gönderip her bağlantının bu hatadaki payını bulur. Bu paylar kullanılarak ağırlıklar biraz değiştirilir ağ yavaş yavaş doğruyu öğrenir.


**Tanh (Hiperbolik Tanjant) Fonksiyonu**

![[Activation Function5.png]]

Sigmoid'in kardeşidir ama daha dengelidir. 

![[Activation Function6.svg]]
Değer kümesi -> (-1,1)

Ortalama sıfırdır bu ağın daha dengeli öğrenmesini sağlar çünkü bazı nöronlar pozitif yönde bazılar negatif yönde hata taşır.

- Negatif girişler → -1’e yakın
- Pozitif girişler → +1’e yakın
- Ortalar → 0 civarı (kararsızlık bölgesi)

Tanh, sıfır etrafında dönüp duran denge aracı bir fonksiyondur ama hala büyük değerlerde türevi sıfıra yaklaşır yani vanishing gradient yine burada da olur. 

Sigmoid sadece evet/hayır der fakat Tanh ise şiddetli evet / kararsız / güçlü hayır der. Yani sadece sınırlamakla kalmaz, yoğunlukta taşır bu yüzden tanh, bilgi taşımayı daha verimli yapar çünkü sıfırdan itibaren hem pozitif hem de negatif sinyalleri iletebilir. Sigmoid gibi giriş çok büyüdüğünde türev neredeyse sıfır olur bu da vanishing gradient problemi oluşturur yani ağın derin katmanları öğrenmeyi unutur. Bu yüzden tanh, genellikle orta derinlikteki ağlarda veya LSTM gibi kapılı yapılarda tercih edilir.

**Relu (Rectified Linear Unit) Fonksiyonu**

![[Activation Function7.png]]

Yapay zekanın 2010 sonrası yükselişinde payı vardır. Hem basit hem hızlı hem de büyük ağlarda kaybolmayan bir gradient sağlar. 


![{\displaystyle {\begin{aligned}(x)^{+}\doteq {}&{\begin{cases}0&{\text{if }}x\leq 0\\x&{\text{if }}x>0\end{cases}}\\={}&\max(0,x)=x{\textbf {1}}_{x>0}\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5672f7148bf28e2ce3ec29ceb5cdc4b30509ac21)

Değer kümesi ->  [0,∞)

Sinir ağlarında özellikle derin olanlarda, öğrenme süreci gradyan denen hata sinyaliyle gerçekleşir.ReLU bu sorunu çözdü çünkü pozitif bölgede gradyanı 1'dir. Yani hata sinyali neredeyse hiç zayıflamadan aşağı katmanlara iletir. Bir nöronun görevi aldığı bilgiyi değerlendirmek ve evet  bu sinyalii aktarmaya değer diyebilmektir. ReLU bu kararı sert şekilde verir, negatif girdiler tamamen susturulur pozitif girdiler olduğu gibi geçirir. Yani ağ hangi nöronların aktif olacağını öğrenir. Bu da modele seyreklik sparsity kazandırır. Ağ sadece önemli sinyalleri işler.

Eğer bir nöron çok fazla negatif giriş alırsa sürekli 0 üretmeye başlar ve bir kez bu duruma düşerse artık hirçbir gradyan alamaz. 

ReLU'yu bir öğretmen gibi düşün derse katılmayan öğrencileri susturur, katılım gösterenleri büyütür. Bu tavrı sayesinde sınıf daha hızlı öğrenir ama bazen bazı öğrenciler sonsuza kadar konuşamaz.

**Leaky ReLU Fonksiyonu**

![[Activation Function8.png]]

ReLU'dan farklı olarak negatif taraf tamamen kesilmesin diye küçük bir eğim bırakır. Yani negatif değerler de az da olsa katkı sağlar.

![{\displaystyle {\begin{cases}0.01x&{\text{if }}x\leq 0\\x&{\text{if }}x>0\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c0833be0cfca2ab27db020003b7cf47ee9cc737a)

Değer kümesi -> ( ∞,-∞)

Negatif bölgede küçük bir eğim (0.01) bırakmak, nöronun tamamen ölmesini engeller. Bu küçük eğim gradyanın sıfıra düşmesini engeller ve  böylelikle ağ öğrenmeye devam eder. Buradaki avantaj Dead ReLU problemini büyük ölçüde çözer.

**Parametric ReLU (PReLU)**

![[Activation Function9.png]]

Burada Leaky ReLU'dan farklı olarak negatiflik eğimini kendi belirliyor. Kimi veri setinde negatiflere daha çok izin veriyor, kimi veride daha az.

![[Activation Function10.svg]]

Değer kümesi -> ( ∞,-∞)

Burada a sabit değil öğrenebilir bir parametre. Dezavantaj ise fazladan parametreden dolayı hesaplama biraz daha artar.

**ELU (Exponential Linear Unit)**

![[Activation Function11.png]]

ReLU ailesinin daha biyolojik versiyonudur. Negatif bölgede yumuşak bir şekilde aşağı iner, sıfırda keskin bir kırılma yoktur. Bu ağın çıktısını ortalama olarak sıfır civarına çeker. 

![{\displaystyle {\begin{cases}\alpha \left(e^{x}-1\right)&{\text{if }}x\leq 0\\x&{\text{if }}x>0\end{cases}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0f409bbcde02f828392ce0db27105ac46cc41477)

Değer kümesi ->  ( a,-∞)

Yani pozitif ve negatif aktivasyonlar birbirini dengeler ve öğrenme daha kararlı olur fakat bu durum daha yavaştır çünkü üstel hesaplama yapar.


**Softmax**
Klasik anlamın dışına çıkarak bir aktivasyon fonksiyonunu gibi değilde çıktı katmanında kullanılır ama ağın karar verme mekanizması için çok önemlidir.

![[Activation Function12.svg]]

Değer kümesi -> (0,1)

Her nöronun çıkışını olasılığa çevirir. Toplamları daima 1 eder. Örneğin bir ağ kedi mi köpek mi kuş mu? diye karar veriyorsa:
- Kedi = 0.7
- Köpek = 0.2
- Kuş = 0.1
Bu olasılık temsili sınıflandırma problemlerinde eğitim için de kritiktir çünkü orada kullanılan fonksiyonlar softmax'la beraber çalışır. Burada ki avantaj kararlı olasılığa dönüştürür yorumlanabilir sonuçlar elde edilir fakat çok büyük logit değerlerinde sayısla kararsızlık oluşabilir bu durumlarda da genelde log-softmax kullanılır.


| **Aktivasyon Fonksiyonu** | **Özelliği / Karakteri** |
| ------------------------- | ------------------------ |
| **Step**                  | Ya var ya yok            |
| **Sigmoid**               | Olasılıkçı               |
| **Tanh**                  | Dengeli                  |
| **ReLU**                  | Sert ama güçlü           |
| **Leaky ReLU**            | Merhametli               |
| **PReLU**                 | Uyumlu                   |
| **ELU**                   | Dengeli biyolojik        |
| **Softmax**               | Karar verici             |
***
***Abdullah TANRIVERDİ***