#Yazılım #ProgramlamaDilleri #Python 

Python'da modüler paketler ve kütüphaneler, kodu daha düzenli, tekrar kullanılabilir ve bakımı kolay hale getirmek için önemli bir kavramdır.

==**Modülerlik Nedir?**==
Modülerlik, yazılımın küçük, bağımsız ve birbirinden ayrılmış parçalara (modüllere) bölünmesi ilkesidir. Bu, büyük yazılım projelerinin daha yönetilebilir ve sürdürülebilir olmasını sağlar.
<br>

**Python Modülleri**

- **Modül:** Bir Python dosyasıdır (`.py` uzantılı) ve içinde fonksiyonlar, sınıflar, değişkenler ve başka modüller olabilir.
    
- **Modül İçe Aktarımı (Importing Modules):** Modülleri başka bir Python dosyasına dahil etmek için `import` anahtar kelimesi kullanılır.
```python
import module_name

```
Bir modül içindeki belirli fonksiyonları da şu şekilde alabilirsiniz:
```python
from module_name import function_name

```

<br>

**Python Paketleri**

- **Paket:** Modülleri gruplayan dizinlerdir. Bir paket, içinde başka modüller veya alt paketler barındırabilir.
    
- **Paket Yapısı:** Bir paket, bir dizin ve o dizinde `__init__.py` adlı özel bir dosya içerir. Bu dosya dizinin bir paket olarak tanınmasını sağlar.
```python
my_package/
    __init__.py
    module1.py
    module2.py

```
Bu dizini `import my_package` şeklinde içe aktarabilirsiniz.

<br>
**Python Kütüphaneleri**

- **Kütüphane:** Python'da bir dizi modül veya paket içeren büyük bir yazılım koleksiyonudur. Kütüphaneler, belirli bir alanda işlevsellik sağlayan geniş araç setleri sunar.
    
- Kütüphaneler genellikle açık kaynaklıdır ve `pip` (Python Package Index) ile yüklenebilir.
```python
pip install numpy

```


==**Öne Çıkan Modüler Paketler**==

- **NumPy:** Matematiksel hesaplamalar için kullanılır.
- **Pandas:** Veri analizi ve manipülasyonu için kullanılır.
- **Matplotlib:** Veri görselleştirme için kullanılır.
- **Requests:** HTTP istekleri yapmak için kullanılır.
- **Flask/Django:** Web geliştirme için popüler frameworklerdir.

**Paketlerin Yönetimi**

- **`pip`:** Python paketlerini yüklemek ve yönetmek için kullanılır. `pip` ile yüklenen paketler, Python projelerinde kolayca erişilebilir ve kullanılabilir.
```python
pip install requests
pip uninstall requests

```
-  **`requirements.txt`:** Projelerde kullanılan tüm dış kütüphaneleri listeler. Bu dosya, projeyi paylaşırken gerekli olan tüm bağımlılıkların kurulmasını sağlar.

Örnek `requirements.txt`:
```python
numpy==1.23.0
pandas==1.5.0

```
Kurulum için:
```python
pip install -r requirements.txt

```

**Kendi Paketlerinizi Oluşturma**

Python'da kendi paketlerinizi oluşturmak için aşağıdaki adımları takip edebilirsiniz:

1. Projeniz için bir dizin oluşturun.
2. İçine modüller ve bir `__init__.py` dosyası ekleyin.
3. `setup.py` dosyasını hazırlayarak, paketinizin nasıl kurulacağını tanımlayın.

Örnek `setup.py`:
```python
from setuptools import setup, find_packages

setup(
    name="my_package",
    version="0.1",
    packages=find_packages(),
)

```
****
***Abdullah TANRIVERDİ***
