#Yazılım #VeriBilimi 

NumPy (**Numerical Python**), büyük çok boyutlu dizileri (array) ve matrisleri işlemek için kullanılan bir Python kütüphanesidir. Ayrıca bu diziler üzerinde yüksek performanslı matematiksel işlemler yapmamıza olanak tanır.

==**NumPy'nin Avantajları**==

✅ **Hızlıdır**: C diliyle yazıldığı için Python listelerine göre çok daha performanslıdır.  
✅ **Daha Az Bellek Kullanır**: Aynı veri türünden elemanları sakladığı için Python listelerine göre bellek tüketimi daha azdır.  
✅ **Matematiksel İşlemler Kolaydır**: Vektör ve matris işlemlerini kolaylaştırır.


**Kurulum:** 
```bash
pip install numpy
```

**İçeri Aktarma:**
```python
import numpy as np
```




**NumPy Dizileri (ndarray)**
NumPy'nin temel veri yapısı **ndarray**'dir


`numpy.array()` – Listeyi NumPy Dizisine Çevirme
```python
arr = np.array([1, 2, 3, 4, 5])
print(arr, type(arr))  # <class 'numpy.ndarray'>

```

Çok boyutlu dizi:
```python
arr2d = np.array([[1, 2, 3], [4, 5, 6]])
print(arr2d.shape)  # (2, 3)

```

`numpy.asarray()` – Var Olan Veriyi NumPy Dizisine Çevirme

Eğer zaten NumPy dizisi ise kopyalamaz:
```python
lst = [1, 2, 3]
arr1 = np.array(lst)
arr2 = np.asarray(arr1)  # arr1 zaten NumPy array olduğu için kopyalanmaz
print(arr1 is arr2)  # True

```


**NumPy Dizisi Şekillendirme ve Boyutlandırma**

`numpy.reshape()` – Diziyi Yeniden Şekillendirme
```python
arr = np.arange(6)
reshaped_arr = arr.reshape(2, 3)  # 2 satır, 3 sütun
print(reshaped_arr)

```

`numpy.resize()` – Diziyi Yeniden Boyutlandırma
```python
arr = np.array([1, 2, 3, 4])
arr_resized = np.resize(arr, (2, 3))
print(arr_resized)

```


**NumPy Özel Diziler**

`numpy.zeros()` – Sıfırlardan Oluşan Dizi
```python
zero_arr = np.zeros((3, 4))  # 3x4 sıfır matrisi
print(zero_arr)

```

**NumPy Dizilerini Birleştirme ve Bölme**
`numpy.concatenate()` – Dizileri Birleştirme

```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
combined = np.concatenate((arr1, arr2))
print(combined)  # [1 2 3 4 5 6]

```


Çok boyutlu dizileri eksen belirterek birleştirme:
```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])
combined = np.concatenate((arr1, arr2), axis=1)  # Y ekseni bazında
print(combined)

```


`numpy.split()` – Diziyi Eşit Parçalara Bölme

```python
arr = np.array([1, 2, 3, 4, 5, 6])
split_arr = np.split(arr, 3)
print(split_arr)  # [array([1, 2]), array([3, 4]), array([5, 6])]

```


`numpy.array_split()` – Eşit Bölünemeyen Dizileri Bölme

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7])
split_arr = np.array_split(arr, 3)
print(split_arr)  # [array([1, 2, 3]), array([4, 5]), array([6, 7])]

```


**NumPy Dizilerini Değiştirme**

`numpy.append()` – Diziye Eleman Ekleme

```python
arr = np.array([1, 2, 3])
arr = np.append(arr, [4, 5])
print(arr)  # [1 2 3 4 5]

```

Çok boyutlu dizilere ekleme:
```python
arr2d = np.array([[1, 2], [3, 4]])
new_arr = np.append(arr2d, [[5, 6]], axis=0)  # Satır ekleme
print(new_arr)

```


`numpy.insert()` – Belirli Bir İndekse Eleman Ekleme

```python
arr = np.array([1, 2, 3, 4])
arr = np.insert(arr, 2, 99)  # 2. indekse 99 ekle
print(arr)  # [ 1  2 99  3  4]

```


`numpy.delete()` – Diziden Eleman Silme

```kotlin
arr = np.array([1, 2, 3, 4, 5])
arr = np.delete(arr, 2)  # 2. indeksi sil
print(arr)  # [1 2 4 5]

```

==**NumPy ve Python Listeleri Karşılaştırması**==

|Özellik|NumPy Array (`ndarray`)|Python Listesi|
|---|---|---|
|**Performans**|Daha hızlı (C ile optimize)|Daha yavaş|
|**Boyut**|Sabit boyutlu|Dinamik boyutlu|
|**Bellek Kullanımı**|Daha az bellek tüketir|Daha fazla bellek tüketir|
|**Matematiksel İşlemler**|Vektörleştirme ile desteklenir|Döngü ile yapılmalıdır|
|**Veri Türü**|Aynı veri tipine sahip elemanlar içerir|Farklı veri tipleri içerebilir|


Karşılaştırma Örneği
```python
import numpy as np
import time

# Python Listesi
py_list = list(range(1_000_000))
start = time.time()
py_list = [x * 2 for x in py_list]
end = time.time()
print("Python Listesi Süre:", end - start)

# NumPy Dizisi
np_array = np.arange(1_000_000)
start = time.time()
np_array = np_array * 2
end = time.time()
print("NumPy Array Süre:", end - start)

#Python Listesi Süre: 0.06618857383728027
#NumPy Array Süre: 0.0025196075439453125

```


Sıfır, bir ve boş diziler oluşturma:
```python
np.zeros((3, 4))  # 3x4 sıfır matrisi
np.ones((2, 2))   # 2x2 bir matrisi
np.empty((2, 3))  # Bellekteki rastgele değerler
```

Aralıklarla dizi oluşturma:
```python
np.arange(0, 10, 2)  # 0'dan 10'a kadar 2'şer artan dizi
np.linspace(0, 1, 5)  # 0 ile 1 arasında 5 eşit parçaya bölünmüş dizi
```

Rastgele diziler oluşturma:
```python
np.random.rand(3, 3)  # 3x3 rastgele sayı matrisi
np.random.randn(3, 3) # 3x3 standart normal dağılım
np.random.randint(1, 10, (2, 2))  # 1 ile 10 arasında rastgele tam sayılar
```

NumPy dizileri hakkında bilgi almak için:
```python
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr.shape)  # Dizinin boyutu (2,3)
print(arr.size)   # Eleman sayısı
print(arr.ndim)   # Boyut sayısı
print(arr.dtype)  # Veri tipi (int32, float64 vb.)
print(arr.itemsize)  # Bir elemanın bellek boyutu
print(arr.nbytes)  # Toplam bellek boyutu
```

Temel Matematiksel İşlemler
```python
arr = np.array([1, 2, 3, 4])
print(arr + 2)  # [3 4 5 6]
print(arr * 3)  # [3 6 9 12]
print(arr ** 2) # [1 4 9 16]
print(np.sqrt(arr)) # Kare kök
print(np.exp(arr))  # Üstel (e^x)
print(np.log(arr))  # Doğal logaritma
```

Matris İşlemleri
```python
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

print(A + B)  # Matris toplama
print(A * B)  # Eleman bazlı çarpma
print(A.dot(B))  # Matris çarpımı
print(np.linalg.inv(A))  # Matrisin tersi
print(np.linalg.det(A))  # Matrisin determinantı
print(np.linalg.eig(A))  # Özdeğerler ve özvektörler
```

Tek Boyutlu Diziler
```python
arr = np.array([10, 20, 30, 40, 50])
print(arr[0])  # İlk eleman
print(arr[-1]) # Son eleman
print(arr[1:4]) # 1. ile 4. eleman arası
print(arr[::-1]) # Diziyi ters çevirme
```

Çok Boyutlu Diziler
```python
arr2d = np.array([[10, 20, 30], [40, 50, 60]])
print(arr2d[0, 1])  # İlk satır, ikinci sütun
print(arr2d[:, 1])  # Tüm satırların ikinci sütunu
print(arr2d[1, :])  # İkinci satırın tamamı
print(arr2d.T)  # Matrisin transpozesi
```

```python
arr = np.array([1, 2, 3, 4, 5])
print(np.mean(arr))  # Ortalama
print(np.median(arr)) # Medyan
print(np.std(arr))    # Standart sapma
print(np.var(arr))    # Varyans
print(np.min(arr))    # Minimum değer
print(np.max(arr))    # Maksimum değer
print(np.percentile(arr, 50))  # 50. yüzdelik dilim
```


```python
np.random.seed(42)  # Rastgelelik için sabit değer
print(np.random.rand(3, 3))  # 0 ile 1 arasında rastgele sayılar
print(np.random.randint(1, 10, (2, 2)))  # 1-10 arasında rastgele tamsayı matrisi
print(np.random.normal(0, 1, (3, 3)))  # Normal dağılım
print(np.random.choice([10, 20, 30, 40]))  # Belirtilen diziden rastgele seçim
```


```python
np.savetxt("veri.txt", arr)  # Veriyi kaydetme
arr_yeni = np.loadtxt("veri.txt")  # Kaydedilen veriyi yükleme
np.save("veri.npy", arr)  # NumPy formatında kaydetme
arr_yeni = np.load("veri.npy")  # NumPy formatındaki veriyi yükleme
```

***

***Abdullah TANRIVERDİ***
