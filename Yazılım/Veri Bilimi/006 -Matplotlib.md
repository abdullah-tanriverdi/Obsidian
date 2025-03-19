#Yazılım #VeriBilimi  

![[matplotlib.png|500]]

Matplotlib, 2D grafikler ve görselleştirmeler oluşturmak için kullanılan popüler bir Python kütüphanesidir. Genellikle veri analizi ve bilimsel hesaplamalarda kullanılır.Matplotlib'in en sık kullanılan modülü pyplot'tur

==**Kurulum ve İçe Aktarma**==
```python
# Matplotlib'i kurmak için:
pip install matplotlib

# Pyplot modülünü içe aktarmak:
import matplotlib.pyplot as plt

```

==**Matplotlib ile İlk Grafik**==

```python
import matplotlib.pyplot as plt

# Veri
x = [1, 2, 3, 4, 5]
y = [10, 20, 25, 30, 35]

# Grafik oluşturma
plt.plot(x, y)

# Başlık ve etiketler
plt.title("Basit Çizgi Grafiği")
plt.xlabel("X Ekseni")
plt.ylabel("Y Ekseni")

# Grafiği gösterme
plt.show()

```

==**Grafik Türleri**==
- **Çizgi Grafiği (Line Plot)**
```python
plt.plot(x, y, color='blue', linestyle='--', marker='o')
plt.title("Çizgi Grafiği")
plt.show()

```

![[cizgi_grafik_ozellestirilmis.png]]

- **Bar Grafiği**
```python
categories = ['A', 'B', 'C', 'D']
values = [3, 7, 8, 5]

plt.bar(categories, values, color='purple')
plt.title("Bar Grafiği")
plt.show()


```
![[bar_grafik.png]]

- **Histogram**
Histogramlar, verilerin dağılımını gösterir.
```python
data = [5, 8, 8, 10, 15, 15, 17, 18, 21, 23, 25, 28]
plt.hist(data, bins=5, color='orange')
plt.title("Histogram")
plt.show()

```

![[histogram.png]]

- **Pasta Grafiği (Pie Chart)**
```python
sizes = [20, 30, 25, 25]
labels = ['A', 'B', 'C', 'D']

plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.title("Pasta Grafiği")
plt.show()

```

![[pasta_grafik 2.png]]
- **Dağılım Grafiği (Scater  Plot)**
```python
x = [5, 7, 8, 10, 12]
y = [10, 20, 25, 35, 50]

plt.scatter(x, y, color='red', marker='x')
plt.title("Dağılım Grafiği")
plt.show()

```


![[dagilim_grafik.png]]


==**Grafikleri Özelleştirme**==

- **Renk, Çizgi ve Marker Ayarları**
Renkler, red, blue,green veya hex kodları ile belirtilebilinir
Çizgi stili -- , - , : , -. şeklinnde ayarlanılabilinir
Marker stili o ^ s x 
```python
plt.plot(x, y, color='green', linestyle='--', marker='^')
plt.title("Özelleştirilmiş Grafik")
plt.show()

```

- **Eksen Ayarlama**
```python
plt.plot(x, y)
plt.xlim(0, 10)  # X ekseni aralığı
plt.ylim(0, 50)  # Y ekseni aralığı
plt.title("Ekseni Ayarlama")
plt.show()

```
- **Birden Fazla Grafik**
```python
# İlk grafik
plt.plot(x, y, label='Doğrusal Büyüme', color='blue')

# İkinci grafik
plt.plot(x, [i**2 for i in x], label='Karesel Büyüme', color='orange')

# Etiketler ve başlık
plt.title("Birden Fazla Grafik")
plt.xlabel("X Ekseni")
plt.ylabel("Y Ekseni")
plt.legend()  # Grafik açıklamaları
plt.show()

```

![[birden_fazla_grafik.png]]

==**Alt Grafikler (Subplots)**==

Aynı figürde birden fazla grafik göstermek için kullanılır
```python
# 1x2 grid: 1. grafik
plt.subplot(1, 2, 1)
plt.plot(x, y)
plt.title("Birinci Grafik")

# 1x2 grid: 2. grafik
plt.subplot(1, 2, 2)
plt.bar(categories, values)
plt.title("İkinci Grafik")

plt.tight_layout()  # Aralıkları düzenle
plt.show()

```

![[alt_grafikler.png]]

==**Kayıt Etme**==
Grafiği bir dosyaya kaydetmek için
```python
plt.plot(x, y)
plt.savefig("grafik.png", dpi=300, bbox_inches='tight')

```


==**Matplotlib Fonksiyonları**==

|Fonksiyon|Açıklama|
|---|---|
|`plot()`|Çizgi grafiği oluşturur|
|`bar()`|Bar grafiği oluşturur|
|`hist()`|Histogram oluşturur|
|`pie()`|Pasta grafiği oluşturur|
|`scatter()`|Dağılım grafiği oluşturur|
|`xlabel()`/`ylabel()`|Eksenlere isim verir|
|`title()`|Grafik başlığı ekler|
|`legend()`|Grafik açıklamaları ekler|
|`grid()`|Grid çizgilerini ekler|
|`savefig()`|Grafiği dosyaya kaydeder|

--- 
***Abdullah TANRIVERDİ***
