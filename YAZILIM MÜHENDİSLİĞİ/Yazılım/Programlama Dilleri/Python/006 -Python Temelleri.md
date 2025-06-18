#Yazılım  #ProgramlamaDilleri #Python 


- ==**Yorum Satırları**==
Tek satırlık yorumlar için `#`
Çok satırlı yorum için
```python
"""
Bu bir
çok satırlı
yorumdur.
"""

```
- ==**Değişkenler**==
Python'da değişken tanımlarken tür belirtmenize gerek yoktur
```python
isim = "Ahmet"  # String
yas = 25        # Integer
boy = 1.75      # Float
aktif = True    # Boolean

```
Türleri öğrenmek için
```python
print(type(isim))  # Çıktı: <class 'str'>

```
- ==**Veri Türleri**==
Python'daki temel veri türleri

| Veri Türü | Açıklama                        | Örnek           |
| --------- | ------------------------------- | --------------- |
| `int`     | Tam sayılar                     | `10, -5, 0`     |
| `float`   | Ondalıklı sayılar               | `3.14, -0.1`    |
| `str`     | Metin                           | `"Merhaba"`     |
| `bool`    | Doğru/Yanlış (True/False)       | `True, False`   |
| `list`    | Liste                           | `[1, 2, 3]`     |
| `tuple`   | Değiştirilemez liste            | `(4, 5, 6)`     |
| `dict`    | Sözlük (anahtar-değer çiftleri) | `{'ad': 'Ali'}` |
| `set`     | Benzersiz öğeler topluluğu      | `{1, 2, 3}`     |
 - ==**Girdi ve Çıktı**==
```python
print("Merhaba, Dünya!")

isim = input("Adınızı girin: ") print(f"Merhaba, {isim}!")

```



- ==**Operatörler**==

| Operatör | Açıklama      | Örnek           |
| -------- | ------------- | --------------- |
| `+`      | Toplama       | `5 + 3` → `8`   |
| `-`      | Çıkarma       | `5 - 3` → `2`   |
| `*`      | Çarpma        | `5 * 3` → `15`  |
| `/`      | Bölme         | `5 / 2` → `2.5` |
| `//`     | Tam bölme     | `5 // 2` → `2`  |
| `%`      | Modül (kalan) | `5 % 2` → `1`   |
| `**`     | Üs alma       | `2 ** 3` → `8`  |

- ==**Koşul Yapıları**==
```python
yas = 20

if yas < 18:
    print("Reşit değilsiniz.")
elif yas == 18:
    print("Tam sınırdasınız.")
else:
    print("Reşitsiniz.")

```
- ==**Döngüler**==
```python
#for döngüsü
for i in range(1, 6):  # 1'den 5'e kadar
    print(i)


#while döngüsü
sayac = 0
while sayac < 5:
    print(sayac)
    sayac += 1

```

- ==**Fonksiyonlar**==
Python'da fonksiyon tanımlamak için `def` anahtar kelimesi kullanılır
```python
def selamla(isim):
    print(f"Merhaba, {isim}!")

selamla("Ahmet")  # Çıktı: Merhaba, Ahmet!

```

- ==**Listeler**==
Listeler birden çok öğeyi bir arada tutar
```python
meyveler = ["elma", "armut", "çilek"]
print(meyveler[0])  # Çıktı: elma

# Listeye eleman ekleme
meyveler.append("muz")

```

- ==**Sözlükler**==
Sözlükler anahtar-değer çifteri tutar
```python
ogrenci = {"isim": "Ali", "yas": 21}
print(ogrenci["isim"])  # Çıktı: Ali

```
Temel python yapıları bu şekilde detaylı konulara başlık altında özel olarak incellenir

---
***Abdullah TANRIVERDİ***

