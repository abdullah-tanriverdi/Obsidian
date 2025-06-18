#Yazılım #VeriBilimi 

![[Pasted image 20241225164709.png|500]]

Seaborn, Python'da veri görselleştirme yapmak için kullanılan güçlü ve kullanımı kolay bir kütüphanedir. Matplotlib üzerine inşa edilmiştir ve özellikle istatiksel grafikler için geniş bir yelpazeye sahiptir. Veriyi anlamak ve anlatmak için çok sayıda grafik türü sunar. Seaborn, özellikle istatiksel ilişkileri daha iyi anlamak için geliştirilmiştir ve Matplotlib ile oldukça uyumludur.

==**Seaborn Kurulumu**==
Searbornu kullanmaya başlamak için önce kurulum yapmamamız gerekiyor. Eğer Seaborn yüklü değilse, terminal üzerinden şu komutu kullanarak yükleyin
```bash
pip install seaborn
```

==**Seaborn'un Temel Özellikleri==

En büyük avantajlarından biri, veri görselleştirmeyi cok daha kolay hale getirmesidir.
- **Daha Gelişmiş Grafikler:** Matplotlib'e göre daha yüksek seviyede grafikler sunar.
- **Karmaşık İstatistiksel Hesaplamalar:** Korelasyon, regresyon gibi istatistiksel analizleri doğrudan grafik üzerinde gösterir.
- **Otomatik Renk Paletleri:** Grafikler için önceden tanımlanmış renk paletleri kullanır, böylece grafiklerin görünümü daha profesyonel olur.


==**Seaborn Grafik Türleri**==

 a. **Histogram (Karmaşık Histogramlar)**
`histplot()` fonksiyonu ile verilerin histogramlarını oluşturabiliriz.

```python
sns.histplot(data=df, x='column_name', kde=True)
plt.show()

```

b. **Kutu Grafiği (Box Plot)**

Kutu grafiği, verilerin dağılımını ve olası uç değerleri görmek için kullanılır.
```python
sns.boxplot(x='category_column', y='value_column', data=df)
plt.show()

```


c. **Dağılım Grafiği (Scatter Plot)**

`scatterplot()` fonksiyonu ile veriler arasındaki ilişkiyi gösteren grafikler oluşturabiliriz.

```python
sns.scatterplot(x='column1', y='column2', data=df) plt.show()
```


d. **Çizgi Grafiği (Line Plot)**

`lineplot()` fonksiyonu, özellikle zaman serisi verileri için kullanışlıdır.

```python
sns.lineplot(x='date_column', y='value_column', data=df) plt.show()
```


e. **Isı Haritası (Heatmap)**
Isı haritası, özellikle korelasyon matrislerini görselleştirmek için idealdir.

```python
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.show()

```


==**Seaborn’un İleri Düzey Özellikleri**==

 a. **FacetGrid ile Çoklu Grafikler**
FacetGrid, aynı anda birden fazla küçük grafik (subplot) oluşturmanıza olanak tanır. Bu özellik özellikle veri alt kümelerini karşılaştırmak için faydalıdır

```python
g = sns.FacetGrid(df, col='category_column')
g.map(sns.histplot, 'value_column')
plt.show()

```

b. **Pairplot**
Pairplot, veri setindeki sayısal sütunlar arasındaki tüm ikili ilişkileri görselleştirir.
```python
sns.pairplot(df)
plt.show()

```


c. **Regplot ve lmplot**
Bu fonksiyonlar, regresyon analizini görselleştirmenizi sağlar. `regplot()` ile regresyon çizgisi ekleyebilirsiniz, `lmplot()` ise daha karmaşık modelleri görselleştirir.

```python
sns.regplot(x='column1', y='column2', data=df)
plt.show()

```

Seaborn, Python’da veri görselleştirmeyi çok daha kolay ve estetik hale getiren bir kütüphanedir. Özellikle istatistiksel analizler yapmak isteyenler için harika araçlar sunar. Grafiklerinizi kişiselleştirebilir, renk paletlerini değiştirebilir ve kolayca anlamlı görselleştirmeler oluşturabilirsiniz.

---

***Abdullah TANRIVERDİ***
