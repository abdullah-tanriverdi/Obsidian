#Yazılım #VeriBilimi 

![[Pasted image 20250407160923.jpg|500]]


[Google Play Store Market Gap Analysis - GitHub](https://github.com/abdullah-tanriverdi/GooglePlayStoreMarketGapAnalysis/blob/master/google_play_store_market_gap_analysis.ipynb)



`pip install numpy`
`pip install pandas`
`pip install seaborn`
`pip install matplotlib`

```python
  
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import MinMaxScaler
from IPython.display import display

```

---

`.read_csv()` **=**  Bu fonksiyon, bir CSV dosyasını okur ve onu pandas DataFrame'e dönüştürür. CSV (Comma Separated Values) dosyası, genellikle verilerin virgülle ayrıldığı ve satırlara yerleştirildiği bir dosya formatıdır.

---


`.info()`  **=**  Bu metodu çağırdığınızda, DataFrame hakkında genel bir özet bilgi alırsınız. 
- **Sütun Adları**: DataFrame'deki her sütunun ismi.
    
- **Sütun Sayısı**: DataFrame'deki toplam sütun sayısı.
    
- **Veri Türü (dtype)**: Her sütunun veri tipi, örneğin `int64`, `float64`, `object`gibi.
    
- **Null Değerler**: Her sütundaki null verilerin sayısı.
    
- **Bellek Kullanımı**: DataFrame'in tahmin edilen bellek kullanımını (RAM) gösterir.

---

`.describe()` **=** Pandasta ki bu metod, genellikle veri kümesindeki sayısal verilerin dağılımı hakkında hızlıca bilgi edinmek için kullanılır.

DataFrame'in sayısal sütunlarıyla ilgili şu bilgileri sağlar:

1. **count**: Sütundaki geçerli (null olmayan) değer sayısı.
    
2. **mean**: Ortalama (mean) değeri.
    
3. **std**: Standart sapma (std), verinin ne kadar yayıldığını gösterir.
    
4. **min**: Minimum değer.
    
5. **25%**: İlk çeyrek (Q1) değeri. Verinin %25'inin bu değerden küçük olduğu değeri gösterir.
    
6. **50%**: Medyan (Q2) değeri. Verinin ortanca değeri.
    
7. **75%**: Üçüncü çeyrek (Q3) değeri. Verinin %75'inin bu değerden küçük olduğu değeri gösterir.
    
8. **max**: Maksimum değer.

---

`.shape()` **=** DataFrame veya Series'in boyutlarını (satır ve sütun sayısını) döndüren bir özelliktir. Bu metod, verinin yapısını anlamanıza yardımcı olur.

`.shape`, bir tuple döndürür:

- **İlk Değer**: Satır sayısı.
    
- **İkinci Değer**: Sütun sayısı.

---

`.head()` **=** DataFrame veya Series’in ilk birkaç satırını görüntülemek için kullanılır. Parantez içine bir sayı yazarak, görüntülemek istediğiniz satır sayısını belirtebilirsiniz

---

`.copy()` **=** Seçilen bu  sütunların bağımsız bir kopyasını oluşturur.
```python
ds = data[["App Name" , "Category" , "Rating" , "Installs"]].copy()

```
---

`.isnull()` **=** Pandas'ta bir DataFrame veya Series içinde eksik (null / NaN) değerleri tespit etmek için kullanılır. Her hücre için True  ya da False  döndürür.

---

`.sum()` **=** Pandas'ta toplama işlemi yapar. Hem Series hem de DataFrame üzerinde çalışır.

---

`.str` **=** Bir sütun metin verisi içeriyorsa (`dtype=object` veya `string`), `.str` ile o sütundaki her bir hücreye Python string fonksiyonlarını vektörel olarak uygulayabilirsiniz.Tek tek döngü yazmak yerine, bütün bir sütuna bir kerede string işlemi uygulayabilirsiniz.

| Metot                   | Açıklama                                    |
| ----------------------- | ------------------------------------------- |
| `.str.replace(a, b)`    | Karakter veya kelime değiştirir             |

```python
  
ds["Installs"] = ds["Installs"].str.replace("+" , "" , regex = False)
```

- `regex=True` dersen, gelişmiş desen arama yapabilirsin.
    
- `regex=False` dersen, ifaden dümdüz metin olarak işlenir.

---

`.to_numeric(...)` **=**  Pandas’ın sayısal veri tipine dönüştürme fonksiyonudur.Yani, `"1000"` gibi bir string değeri → `1000` (int) yapar. Aynı şekilde `"10.5"` → `10.5` (float).

```python
ds["Installs"] = pd.to_numeric(ds["Installs"] , errors = "coerce")
```


 - **errors**, dönüşüm sırasında hatalı (uyumsuz) veriyle karşılaşıldığında ne yapılacağını belirler. 
  `errors="coerce"` =  Dönüştürme sırasında hatalı (yani sayıya çevrilemeyen) veriler olursa, bunları NaN  olarak işaretler.
  `errors="raise"` → Hata varsa işlem durur (varsayılan).
  `errors="ignore"` → Hata varsa o hücre olduğu gibi bırakılır.

---

`.dropna()` **=** Pandas'ta eksik (NaN) verileri silmek için kullanılan bir fonksiyondur. Bu metot, veri setindeki NaN (Not a Number) veya eksik değerleri kaldırarak temiz veri ile çalışmanıza yardımcı olur.

---

`isna()` **=** Pandas'ta bir DataFrame veya Series içindeki eksik (NaN) verileri belirlemek için kullanılan bir fonksiyondur.

---

`.unique()` **=** Pandas'ta bir Series veya DataFrame'deki benzersiz  değerleri döndürmek için kullanılır.


---

 `.len()` **=** DataFrame veya Series'in satır sayısını döndürür.


---

`.corr()` **=** DataFrame'deki numerik  sütunlar arasındaki korelasyonu hesaplamak için kullanılır. Korelasyon, iki değişkenin ne kadar birbirine bağlı olduğunu gösteren bir istatistiksel ölçüttür.
```python
correlation_matrix = ds.corr(numeric_only = True)
```
**`numeric_only=True`**: Yalnızca sayısal veri tipine sahip sütunları dikkate alır.


> [!tip] İPUCU
> Korelasyon hakkında daha fazla bilgi almak için bağlantıya tıkla [[010 -Korelasyon]]



---

`.figure()` **=**  Bir grafik oluşturulmadan önce bu fonksiyonla çizim alanı ayarlamış oluruz.
 - **`figsize`** (Varsayılan: `(6.0, 4.0)`): Bu parametre, figürün boyutlarını belirler. Boyutlar, bir tuple olarak `(genişlik, yükseklik)` şeklinde verilir.
---

`.heatmap` **=** Seaborn kütüphanesi kullanılarak bir ısı haritası (heatmap) çiziliyor. Isı haritası, korelasyon gibi sayısal verileri renklerle görselleştirmek için çok kullanışlıdır.


```python
sns.heatmap(corr , annot = True , cmap = "coolwarm" , fmt = ".4f" , linewidths = 0.5)
```
`corr`

- Genellikle bir korelasyon matrisi kullanılır.
    
- Bu matris, sayısal sütunlar arasındaki ilişkiyi (korelasyonu) gösterir.
    
 `annot=True`

- `annot` = "annotation" (açıklama, not).
    
- Hücrelerin içine sayısal korelasyon değerlerini yazdırır.

 `cmap="coolwarm"`

- Renk paleti belirler.
    
- Negatif korelasyonla → mavi tonlarında
    
- Pozitif korelasyonlar → kırmızı tonlarında
    
- 0 civarı korelasyonlar → beyaza yakın tonlarda görünür.

`fmt=".4f"`

- Sayısal değerlerin formatı belirlenir.
    
- `.4f` → Virgülden sonra 4 basamaklı ondalık sayı gösterir.  

 `linewidths=0.5`

- Hücreler arasındaki çizgilerin kalınlığını ayarlar.
    
- `0.5` değeri, ince ama belirgin çizgiler oluşturur.

---

`.regplot()` **=** Regression Plot (regresyon çizimi) oluşturmak için kullanılır. Bu fonksiyon, iki değişken arasındaki ilişkiyi görselleştirirken aynı zamanda doğrusal regresyon doğrusu (lineer regresyon doğrusu) çizer. 

> [!tip] İPUCU
> Regresyon hakkında daha fazla bilgi edinmek için bağlantıya tıkla [[011 -Regresyon]]
> 

```python
g = sns.regplot( x = "Installs" , y = "Rating"  , data = ds[ds["Installs"]>0] , scatter_kws={"alpha":0.3} , line_kws={"color":"red"} )
```

**`regplot()` Parametreleri:**

1. **`x`** (gereklidir):
    
    - X ekseninde gösterilecek değişkenin adı.
        
2. **`y`** (gereklidir):
    
    - Y ekseninde gösterilecek değişkenin adı.
        
3. **`data`** (gereklidir):
    
    - Verilerin bulunduğu **DataFrame** veya benzeri bir yapı.
     
4. **`scatter_kws`** (isteğe bağlı):

	- **scatter plot**'u özelleştirmek için kullanılan parametreler. Örneğin, noktaların rengini veya şekillerini değiştirmek için kullanılabilir.
5. **`line_kws`** (isteğe bağlı):

- Doğrusal regresyon çizgisi için özellikleri belirtir. Örneğin, çizgi rengini veya stilini değiştirmek için kullanılır.
---

`.show()` **=** Matplotlib kütüphanesinde kullanılan ve grafiği ekrana çizmek için kullanılan bir fonksiyondur. Bu metot, oluşturduğunuz tüm grafiklerin, çizimlerin ve görselleştirmelerin ekranda görünmesini sağlar.

---

`.xscale()` **=** Bu fonksiyon sayesinde, grafikteki x eksenini belirli bir ölçek türüne ayarlayabilirsiniz. Örneğin, lineer, logaritmik veya symlog (simetrik logaritmik) gibi farklı ölçekler kullanabilirsiniz.

1. **`'linear'`** (Varsayılan):
    
    - Bu, standart lineer ölçek anlamına gelir. Veriler doğrudan eşit mesafelerle gösterilir.
        
    - **Örnek**: `plt.xscale('linear')`
        
2. **`'log'`**:
    
    - Logaritmik ölçek kullanılır. Bu, verilerin büyük bir aralığını daha anlamlı hale getirebilir. Logaritmik ölçek, özellikle büyüklük farkları çok büyük olan veriler için kullanışlıdır
        
    - **Örnek**: `plt.xscale('log')`
        
3. **`'symlog'`** (Simetrik Logaritmik):
    
    - Simetrik logaritmik ölçek, negatif ve pozitif değerleri simetrik şekilde işler. Yani, negatif değerler logaritmik şekilde işlenirken pozitif değerler de aynı şekilde logaritmik olarak gösterilir.
        
    - **Örnek**: `plt.xscale('symlog')`
        
4. **`'logit'`**:
    
    - Logit ölçeği, özellikle oranlar veya olasılıkların olduğu veriler için uygundur. Bu ölçek, verilerin 0 ve 1 arasındaki değerler için logaritmik dönüşüm uygular.
        
    - **Örnek**: `plt.xscale('logit')`


---

`yscale()` **=** Y ekseninin ölçeğini değiştirmek için kullanılan bir fonksiyondur. Bu fonksiyon, grafikteki y ekseninin ölçeğini belirli bir türde ayarlamanıza olanak sağlar.

---

`.title()` **=** Matplotlib kütüphanesinde bir grafik veya çizim için başlık eklemek amacıyla kullanılan bir fonksiyondur.

**`label` (Başlık Metni):**

- Başlık metnini belirler. Bu parametre, grafikte görünen başlık olacak olan metni alır

**`loc` (Başlık Konumu):**

- Başlığın konumunu belirler. 'left', 'center'` (varsayılan değer), `'right' seçeneklerini alabilir.

**`fontsize`**

- Başlığın yazı tipinin boyutunu belirler.

**`fontweight`**

- Başlık yazısının ağırlığını ayarlamanızı sağlar. `'bold'`, `'normal'` gibi seçenekler alabilir.


**`color`**

- Başlık yazısının rengini ayarlamanızı sağlar.

**`pad`**
- Başlık ile grafiğin arasındaki mesafeyi belirler.

---

`.value_counts()` **=** Pandas'ta `value_counts()` metodu, bir Series (tek sütunlu veri) içerisindeki benzersiz değerlerin sayısını döndürür.

---

`.round()`**=** **Series** veya **DataFrame** içerisindeki sayıları, belirtilen bir ondalık basamağa yuvarlamak için kullanılır. Bu, verilerin daha okunabilir hale gelmesini sağlamak veya belirli bir hassasiyete yuvarlama yapmak için çok kullanışlıdır.

---

`.set_style()` **=** Seaborn tarafından sağlanan belirli stiller arasında seçim yapmanıza olanak tanır. Bu stiller, grafiğin arka planını, grid çizgilerini, ekseni ve diğer estetik öğeleri etkiler.

- **`white`**: Beyaz bir arka plan, grid çizgileri yoktur.
    
- **`dark`**: Koyu arka plan ve grid çizgileri ile daha dramatik bir görünüm sağlar.
    
- **`whitegrid`**: Beyaz bir arka plan ve grid çizgileri ile, veri noktalarını daha net gösterir.
    
- **`darkgrid`**: Koyu arka plan ve grid çizgileri, grafikleri daha modern bir görünüme kavuşturur.
    
- **`ticks`**: Yalnızca eksenlerdeki işaretçileri gösteren minimal bir stil.
```python
sns.set_style("whitegrid")
```

---
<br>

`.plt.barh()` **=** Bar chart (çubuk grafik) oluşturmak için kullanılır, ancak yatay bir çubuk grafik üretir. Bu metod, özellikle kategorik verilerin yatay eksende görselleştirilmesinde kullanılır.
```python
bars = plt.barh(category_counts.index , category_counts.values, color= "Skyblue")
```

**Parametreler:**

1. **`x`**:
    
    - Kategorilerin yer alacağı sütunu belirtir.
        
        
2. **`y`**:
    
    - Çubukların uzunluğunu belirleyen sayısal verilerin bulunduğu sütunu belirtir.
        
3. **`color`**:
    
    - Çubukların rengini değiştirmek için kullanılır.

---

`zip()` **=** İki veya daha fazla iterable (tekrarlanabilir) objeyi birleştirerek, her bir iterable'ın karşılık gelen öğelerini bir arada birleştirir.
<br>


---


`enumerate()` **=**  Bir iterable alır ve her öğeyi, o öğenin indeks (sıra numarası) değeriyle birlikte döndürür. Bu indeksler 0'dan başlar ve her döngüde birer birer artar.

**`enumerate()`** fonksiyonu, her öğe için iki değer döndürür:

1. **İndeks (index)**: Öğenin sırası.
    
2. **Değer (value)**: Öğenin kendisi.

 **Parametreler:**
1. **`iterable`**:
    
    - Döngü yapılacak veri yapısı (liste, tuple, string, vb.).
        
2. **`start` (opsiyonel)**:
    
    - İndeksin kaçtan başlamasını istediğinizi belirten bir parametre. Varsayılan olarak 0'dan başlar, ancak farklı bir başlangıç değeri verilebilir.

---

`plt.gca()` **=** get current axis" ifadesinin kısaltmasıdır. Üzerinde işlem yapılan mevcut grafik eksenini döndürür. 

---
`.invert_yaxis()` **=** Y eksenindeki değerler genellikle artış yönünde yukarı doğru giderken, `.invert_yaxis()` metodu kullanıldığında bu değerler azalış yönünde  sıralanır.

---

`plt.tight_layout` **=** Bu fonksiyon, bir grafiğin tüm öğelerinin (düzgün bir şekilde yerleşmesini sağlar ve grafiğin kenarlarına yakın yerleşen öğeleri uygun şekilde taşmaz.

---

`rcParams[]` **=** Aslında global ayarlar içerir. Yani, matplotlib kullanarak çizilen her grafik bu ayarlara uyar. Bu, belirli bir ayarı değiştirdiğinizde, grafikleri etkileyen tüm görsel öğeleri değiştirdiğiniz anlamına gelir.

Eğer tüm özelleştirmeleri geri almak ve matplotlib'i varsayılan ayarlarına döndürmek isterseniz, `matplotlib.rcdefaults()` fonksiyonunu kullanabilirsiniz.

```python
plt.rcParams["figure.figsize"] = 12,6
```


---

`.kdeplot()` **=** Verilerin üzerindeki dağılımı sürekli bir fonksiyonla modellemeye çalışır. KDE, verilerin arkasındaki olasılık dağılımını tahmin etmek için kullanılan bir tekniktir. En yaygın kullanımı, tek değişkenli bir verinin yoğunluğunu (distribution) görselleştirmektir.


> [!tip] İPUCU
> KDE Grafiği hakkında daha fazla bilgi almak için bağlantıya tıkla [[012 -Kernel Density Estimation (KDE) Grafiği]]

```python
g = sns.kdeplot(ds.Rating , color = "Green" , fill = True)
```

**Parametreler:**

1. **`data`**:
    
    - KDE'yi hesaplamak için kullanılacak veri.
    
2. **`color`**:

- KDE eğrisinin rengini belirler.

3. **`fill`** (bool):

- Eğri altında renkli alan doldurulup doldurulmayacağını belirler. `True` ise eğri altı doldurulur.
---

`xlabel` **=** Grafikteki x ekseni için bir etiket  belirler
`ylabel` **=** Grafikteki y ekseni için bir etiket belirler.

---

`.boxplot()` **=** Verilerin dağılımını ve özet istatistiklerini görselleştirmek için kullanılır. Özellikle, verilerin çeyrek dilimleri, medyanı ve outlier'ları hakkında bilgi verir.

**Boxplot’un Temel Öğeleri:**

1. **Kutu (Box):**
    
    - Kutu, verilerin 1. çeyrek (Q1) ve 3. çeyrek (Q3) arasındaki aralığı gösterir. Yani IQR'yi (Interquartile Range) temsil eder.
        
2. **Çizgiler (Whiskers):**
    
    - Kutu dışındaki çizgiler, verilerin minimum ve maksimum değerlerini gösterir. Bu değerler genellikle Q1 - 1.5*IQ** ve Q3 + 1.5*IQR ile sınırlandırılır.
        
    - Bu çizgiler, outlier'lar hariç tüm veriyi kapsar.
        
3. **Medyan:**
    
    - Kutu içindeki yatay çizgi, verinin medyanını (Q2) yani ortanca değerini gösterir.
        
4. **Outlier'lar (Aykırı Değerler):**
    
    - Outlier'lar, whisker çizgilerinin dışında kalan veri noktalarıdır. Bu değerler genellikle 1.5IQR'den daha uzak olan veri noktalarıdır.

**Parametreler:**

1. **`x` ve `y`**:
    
    - Boxplot'ta eksenleri belirler. **`x`** genellikle kategorik bir veri olurken, **`y`** sayısal bir veri olur.
        
2. **`data`**:
    
    - Veriyi belirler, genellikle pandas DataFrame kullanılır.
        
3. **`hue`**:
    
    - Verinin kategorik bir özelliğine göre renk gruplarını ayırır. Örneğin, cinsiyet veya bölge gibi bir kategoriyi renk ile görselleştirebilirsiniz.
        
4. **`palette`**:
    
    - Renk paletini belirler. Örneğin, `palette='Set2'` gibi bir parametre ile renk şeması ayarlanabilir.
        
5. **`notch`**:
    
    - Eğer **`True`** olarak ayarlanırsa, kutu kesik (notch) olur. Bu, **medyan**ın güven aralığını gösterir.
        
6. **`width`**:
    
    - Kutu genişliğini belirler.
        
7. **`fliersize`**:
    
    - Outlier'ların boyutunu belirler.


> [!tip] İPUCU
> Boxplot hakkında daha fazla bilgi almak için bağlantıya tıkla [[013 -Boxplot]]

---

`groupby()` **=** Bu fonksiyon, veriyi belirli bir veya birden fazla kategoriye göre gruplayarak her grup için işlem yapmanıza olanak tanır. `groupby()`, genellikle toplama, ortalamalar, çeşitli istatistiksel hesaplamalar ve transformasyon gibi işlemler için kullanılır.

---

`.mean()` **=** Sayısal verilere uygulandığında, veri kümesindeki tüm değerlerin toplamını alır ve bu toplamı veri sayısına bölerek ortalamayı elde eder.

---

`.sort_values()` **=**  Bu metot, genellikle verilerin belirli bir düzende, örneğin küçükten büyüğe veya büyükten küçüğe sıralanması gerektiğinde kullanılır.

**`ascending`**:

- `ascending=True` (varsayılan): Artan sıralama 
    
- `ascending=False`: Azalan sıralama 

---

`.barplot()` **=** Seaborn kütüphanesinde yer alan ve bar plot  çizmek için kullanılan bir fonksiyondur. 
- **`x`**:
    
    - Kategorik değişkeni veya eksen üzerinde yer alacak veri. 
        
- **`y`**:
    
    - Sayısal değişken. Çubukların boyutunu belirleyecek olan sayısal veridir.


> [!tip] İPUCU
> Barplot hakkında daha fazla bilgi almak için bağlantıya tıkla [[014 -Barplot]]


---
`.sample()` **=** DataFrame'den rastgele satırlar seçer.
```python
ds.sample(5000 , random_state=42)
# `ds` isimli veri setinden rastgele 5000 satır al demektir.
#random_state parametresi bu kodu her çalıştırdığında aynı 5000 satırı seçmeni sağlar
```

---

`.scatterplot()` **=** Dağılım grafiği çizmeye yarayan fonksiyondur.

> [!tip] İPUCU
> Scatterplot hakkında daha fazla bilgi almak için bağlantıya tıkla [[015 -Scatterplot]]


```python
sns.scatterplot(data=sample_df, x='Installs', y='Rating', alpha=0.3)
```

**Parametreler:**

1. **`x` ve `y`**:
    
    - X ve Y eksenlerinde hangi sütunların gösterileceğini belirler.
        
2. **`data`**:
    
    - Veriyi belirler, genellikle pandas DataFrame kullanılır.

3. **alpha**: 
   - Noktaların şeffaflığını ayarlar.  Kümeleşme veya yoğunluk olduğunda netlik kazandırır.
---

`.agg({})` **=**  Gruplar üzerinde toplu işlemler yapmak.Parantez içine verdiğimiz sözlük ile her sütun için farklı bir işlem yapılabilir.

```python
{
    "Rating": "mean",      # Her kategorideki uygulamaların ortalama puanı
    "Installs": "mean",    # Her kategorideki ortalama yüklenme sayısı
    "Category": "count"    # O kategoride kaç uygulama var
}

```

---

`.rename(columns{})` **=** Oluşan yeni sütunlara daha anlamlı isimler vermek

```python
.rename(columns={
    "Rating": "Avg_Rating",
    "Installs": "Avg_Installs",
    "Category": "App_Count"
})
```

---

`.sort_values(by="")` **=**  DataFrame'i, belirtilen sütuna göre sıralar.

```python
category_summary = category_summary.sort_values(by="App_Count")
```

---

`MinMaxScaller()` **=** `MinMaxScaler`, her bir sütundaki değerleri 0 ile 1 arasında yeniden ölçekler. 


> [!tip] İPUCU
> MinMaxScaller hakkında daha fazla bilgi almak için bağlantıya tıkla [[016 -MinMaxScaller]]


---

`scaler.fit_transform()` **=** 
- `fit()` → Verinin minimum ve maksimum değerlerini öğrenir.
    
- `transform()` → Bu değerlere göre her sütundaki veriyi 0–1 aralığına dönüştürür.
Bu çıktı bir NumPy dizisi (`numpy.ndarray`) olur.

---

`plt.grid()` **=** komutu, grafikteki ızgarayı (grid) açıp kapatma işlemi sağlar.

---

***Abdullah TANRIVERDİ***
