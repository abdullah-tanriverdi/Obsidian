
#Yazılım #ProgramlamaDilleri #Python 

**CPython** Python programlama dilinin en yaygın kullanılan implementationdur. Python dilinin resmi referans uygulaması olarak kabul edilir ve Python yazılımını derlemek ve çalıştırmak için temel araçtır.

 **Implementation’dan Kasıt Nedir?**

Python’un kendisi interpreted (yorumlanmış) bir dildir. Yani bir interpreter’a (yorumlayıcıya) sahiptir. Implementation ise bu interpreter’ın nasıl yazıldığını, hangi yazılım dillerinin kullanıldığını ve hangi amaç için kullanılacağını bize söyler.

![[cpython.png]]Kullanıcıların resmi Python.org sitesi üzerinden kurduğu -ki muhtemelen sizin de kullandığınız- orijinal ve varsayılan Python sürümü budur. En popüler Python implementation’udur. **C** ile yazılmıştır. C ile yazılması sayesinde, C kütüphane fonksiyonlarını kullanabilir, ve kendi C ve C++ da yazdığınız kütüphanelerin Python’da da kullanılmasını sağlayabilirsiniz.

- **Temel İşlev:** Python kodunu doğrudan makine koduna çevirmek yerine, önce **bytecode** adlı bir ara forma çevirir ve ardından bu bytecode'u çalıştırır.

 **CPython'un Çalışma Mekanizması**

CPython, Python kodunu şu adımlarla işler:

1. **Kaynak Kod:**
    - Kullanıcı tarafından yazılan `.py` uzantılı Python dosyası.
2. **Lexing ve Parsing:**
    - Python kodu, leksik analiz ve sözdizimsel analizden geçerek bir **Abstract Syntax Tree (AST)** oluşturulur.
3. **Bytecode:**
    - AST, Python'un sanal makinesi (PVM) tarafından çalıştırılabilecek bir bytecode'a dönüştürülür.
    - Bytecode, `.pyc` dosyaları olarak depolanır.
4. **Python Virtual Machine (PVM):**
    - Bytecode, CPython'ın içindeki sanal makine tarafından çalıştırılır.
    - Sanal makine, bytecode'u gerçek makine koduna çevirip çalıştırır.
---

***Abdullah TANRIVERDİ***