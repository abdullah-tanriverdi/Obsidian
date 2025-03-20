#Yazılım #ProgramlamaDilleri  #Python 
<br>

==**1-`range()`**==

**Açıklama**: `range()`, bir dizi oluşturmak için kullanılır ve genellikle döngülerde kullanılır. Veri bilimi işlemlerinde, özellikle veri sıralama, örnekleme veya iterasyonlarda sıklıkla kullanılır.Büyük veri setlerinde döngüsel işlemler yapılırken sıklıkla kullanılır.
```python
# range() ile 0'dan 9'a kadar bir sayı listesi oluşturma
for i in range(10):
    print(i)

```
==**2. `enumerate()`**==
**Açıklama**: `enumerate()`, bir diziyi (veya iterable yapıyı) iterasyonla gezdiğimizde, her elemanının index’i ile birlikte alınmasını sağlar. Bu, özellikle veriyi index’e göre işlemeniz gerektiğinde kullanışlıdır.Özellikle veri seti üzerinde etiketleme, indeksleme veya belirli bir pozisyondaki veriyi almak için kullanılabilir.
```python
data = ['a', 'b', 'c']
for index, value in enumerate(data):
    print(f"Index: {index}, Value: {value}")

```

==**3. `random`**==
**Açıklama**: `random` modülü rastgele sayılar oluşturmak için kullanılır. Veri bilimi alanında, örnekleme, simülasyon, ve rastgele veri setleri oluşturma gibi işlemlerde sıkça kullanılır.Veri örnekleme, rastgele test verisi oluşturma, simülasyonlar yapma gibi durumlarda yaygın olarak kullanılır.

```python
import random
# 0 ile 10 arasında rastgele bir tam sayı üretme
print(random.randint(0, 10))
# 0 ile 1 arasında rastgele bir float sayısı üretme
print(random.random())

```
==**4. `zip()`**==
**Açıklama**: `zip()`, iki veya daha fazla listeyi (veya iterable'ı) birleştirerek bunları bir tuple dizisine dönüştürür. Bu, verileri paralel olarak işlemek için kullanışlıdır.Özellikle verileri birleştirme (feature engineering), karşılaştırma veya paralel işlem yapma için kullanılır.
```python
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]
zipped = zip(names, ages)
for name, age in zipped:
    print(f"{name} is {age} years old")

```

==**5. `*args` ve `**kwargs`**==
**Açıklama**: `*args` fonksiyonlara değişken sayıda konumsal argüman geçirmemizi sağlar. `**kwargs` ise anahtar-değer çiftleri (keyword arguments) şeklinde değişken sayıda argüman alır.Bu fonksiyonlar, veri analizi veya modelleme sırasında esnek fonksiyonlar yazmak için kullanılır, örneğin değişken sayıda parametre ile fonksiyonlar çalıştırmak.
```python
def sum_all(*args):
    return sum(args)

def print_name(**kwargs):
    print(f"Name: {kwargs['name']}")

print(sum_all(1, 2, 3, 4))  # Çıktı: 10
print_name(name="Alice")  # Çıktı: Name: Alice

```


==**6. `map()`**==
**Açıklama**: `map()`, bir fonksiyonu bir iterable (örneğin liste) üzerindeki her elemana uygular. Veri işleme ve dönüştürme işlemleri için oldukça kullanışlıdır.Verileri hızlıca dönüştürme ve ön işleme işlemleri için kullanılır. Örneğin, bir özellik üzerinde dönüşüm yapmak için kullanılabilir.
```python
numbers = [1, 2, 3, 4]
squared_numbers = map(lambda x: x ** 2, numbers)
print(list(squared_numbers))  # Çıktı: [1, 4, 9, 16]

```
==**7. `filter()`**==
**Açıklama**: `filter()`, bir fonksiyonu iterable elemanlarına uygulayarak, fonksiyondan `True` dönen elemanları döndüren bir fonksiyondur. Bu, veri filtreleme işlemleri için kullanılır.Veri filtreleme işlemleri için kullanılır. Örneğin, sadece belirli koşullara uyan verileri almak için.
```python
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = filter(lambda x: x % 2 == 0, numbers)
print(list(even_numbers))  # Çıktı: [2, 4, 6]

```

==**8. `lambda`**==

**Açıklama**: `lambda`, anonim (isimsiz) fonksiyonlar oluşturmak için kullanılır. Küçük, tek satırlık fonksiyonlar için kullanışlıdır.Genellikle `map()`, `filter()`, `sorted()` gibi fonksiyonlarla birlikte kullanılır. Verileri dönüştürme veya hızlı hesaplamalar için idealdir.
```python
# lambda fonksiyonu ile iki sayıyı toplama
sum_func = lambda x, y: x + y
print(sum_func(3, 4))  # Çıktı: 7

```

***

***Abdullah TANRIVERDİ***
