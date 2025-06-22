#Yazılım #VeriBilimi 
![[pandas.png]]

Pandas, Python programlama dilinde veri analizi ve manipülasyonu için kullanılan güçlü bir kütüphanedir. Veri biliminde yaygın olarak kullanılır ve özellikle tablo şeklindeki veriler üzerinde işlem yapmak için uygundur.


**Pandas Kurulumu:**
```bash
pip install pandas
```

**İçeri Aktarma:**
```python
import pandas as pd
```


**Temel Veri Yapıları:**
Pandas iki temel veri yapısı sunar:
- Series: Tek boyutlu veri yapısıdır
- DataFrame : İki boyutlu (satır-sütün) veri yapısıdır

**Series**
```python
import pandas as pd

data = [10, 20, 30, 40]
ser = pd.Series(data)
print(ser)


```

```bash
0    10
1    20
2    30
3    40
dtype: int64
```

```python
s = pd.Series([10, 20, 30], index=['a', 'b', 'c'])
print(s)

```

```bash
a    10
b    20
c    30
dtype: int64

```



**DataFrame** 

```python
data = [[1, 'Ali', 23], [2, 'Veli', 25], [3, 'Ayşe', 22]]
df = pd.DataFrame(data, columns=['ID', 'İsim', 'Yaş'])
print(df)
```

```bash
   ID  İsim  Yaş
0   1  Ali   23
1   2  Veli  25
2   3  Ayşe  22

```


```python
data = {
    'İsim': ['Ali', 'Veli', 'Ayşe'],
    'Yaş': [23, 25, 22],
    'Şehir': ['Ankara', 'İstanbul', 'İzmir']
}
df = pd.DataFrame(data)
print(df)

```

```markdown
    İsim  Yaş    Şehir
0   Ali   23   Ankara
1  Veli   25  İstanbul
2  Ayşe   22    İzmir

```


**DataFrame Temel İşlemleri**


Pandas farklı formatlardaki verileri okuyabilir ve yazabilir:
```python
df = pd.read_csv('veri.csv')  # CSV dosyasını oku
df.to_csv('cikti.csv', index=False)  # CSV dosyasına yaz
```


Veri setini inceleme
```python
df.head()    # İlk 5 satırı getirir
df.tail(3)   # Son 3 satırı getirir
df.shape     # Satır ve sütun sayısını döndürür
df.info()    # Veri setinin genel bilgilerini gösterir
df.describe()  # Sayısal sütunlarla ilgili özet istatistikleri verir

```

Sütun ve satır seçme
```python
df['İsim']
df[['İsim', 'Yaş']]

```

```python
df.loc[0]  # İlk satırı getirir
df.loc[0:1]  # İlk iki satırı getirir
df.iloc[2]  # İndekse göre üçüncü satırı getirir
df.iloc[1:3]  # İkinci ve üçüncü satırları getirir

```

Yeni sütun ekleme
```python
df['Maaş'] = [5000, 6000, 5500]

```

Sütun silme
```python
df.drop('Şehir', axis=1, inplace=True)  # inplace=True değişiklikleri kaydeder

```

Satır silme
```python
df.drop(1, axis=0, inplace=True)  # 1. indexteki satırı siler

```

Veri filtreleme
```python
df[df['Yaş'] > 23]  # Yaşı 23'ten büyük olanları seçer
df[(df['Yaş'] > 22) & (df['Maaş'] > 5000)]  # Birden fazla koşul

```

Eksik verileri bulma
```python
df.isnull().sum()  # Hangi sütunda kaç eksik değer var?

```

Eksik verileri doldurma
```python
df.fillna(df.mean(), inplace=True)  # Eksik değerleri sütunun ortalama değeriyle doldurur

```

Gruplama işlemi
```python
df.groupby('Şehir')['Maaş'].mean()

```

Toplam,ortalama,max,min
```python
df['Maaş'].sum()  # Toplam maaş
df['Maaş'].mean()  # Ortalama maaş
df['Maaş'].max()  # En yüksek maaş
df['Maaş'].min()  # En düşük maaş

```

Concat kullanımı
```python
df1 = pd.DataFrame({'ID': [1, 2], 'İsim': ['Ali', 'Veli']})
df2 = pd.DataFrame({'ID': [3, 4], 'İsim': ['Ayşe', 'Fatma']})

df_concat = pd.concat([df1, df2])

```

Merge kullanımı
```python
df1 = pd.DataFrame({'ID': [1, 2, 3], 'İsim': ['Ali', 'Veli', 'Ayşe']})
df2 = pd.DataFrame({'ID': [1, 2, 3], 'Maaş': [5000, 6000, 5500]})

df_merge = pd.merge(df1, df2, on='ID')

```

Kullanışlı fonksiyonları

| Fonksiyon       | Açıklama                  |
| --------------- | ------------------------- |
| `head()`        | İlk n satırı getirir      |
| `tail()`        | Son n satırı getirir      |
| `describe()`    | İstatistik özetini verir  |
| `sort_values()` | Veriyi sıralar            |
| `drop()`        | Satır veya sütun siler    |
| `merge()`       | İki DataFrame birleştirir |
| `pivot_table()` | Pivot tablo oluşturur     |


---
***Abdullah TANRIVERDİ***
