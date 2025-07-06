#Yazılım #Yazılım-Jargon 

![[Pasted image 20250622194456.jpg]]



Bir sanal makine (VM) tarafından yürütülmek üzere tasarlanmış, kompakt ve düşük seviyeli ama donanıma özgü olmayan komut kümesidir. Gerçek bir donanım işlemcisine yönelik olan makine kodu gibi çalışmaz.

Özellikleri:

- Stack-Based Architecture kullanır (özellikle JVM).
    
- Her komut (opcode), sabit uzunlukta değildir.
    
- Veri tipleri, runtime’da kontrol edilir.
    
- Platform bağımsızdır.

> [!note] Stack-Based Architecture
> Stack-Based Architecture, işlemleri gerçekleştirmek için verileri bir yığıt (stack) üzerinde tutan bir mimaridir. Tüm aritmetik ve mantıksal işlemler, verilerin stack’e push edilip daha sonra pop edilerek işlenmesiyle yapılır. Java Virtual Machine (JVM) ve Python yorumlayıcısı bu mimariyi kullanır.



```java
Yüksek Seviye Kod (Java, Python)
        ↓
   Derleyici / Derleyici + Bytecode Çevirici
        ↓
      BYTECODE
        ↓
  Sanal Makine (JVM, PVM)
        ↓
Makineye Özgü Kod (Assembly seviyesinde çalışır)

```


**Java Bytecode**
Java'da `.java` dosyası `.class` uzantılı bytecode dosyasına dönüşme süreci

```java
int a = 10;
int b = 20;
int c = a + b;


```

```bash
javac Merhaba.java     // → Merhaba.class oluşturur
java Merhaba           // JVM Merhaba.class dosyasını çalıştırır

```

```bash
javap -c Merhaba

```

```bytecode
0: bipush        10     // 10’u stack’e bas
2: istore_1             // stack’ten al, local variable 1’e ata (a)
3: bipush        20
5: istore_2             // b
6: iload_1              // a’yı yükle
7: iload_2              // b’yi yükle
8: iadd                 // stack’teki iki değeri topla
9: istore_3             // sonucu c’ye ata


```

**Bytecode Yapısı**

```text
[Opcode] [Operand1] [Operand2] ...

```
- **Opcode:** Byte türünde işlem komutu (örneğin `0x60` = `iadd`).
    
- **Operands:** Eğer opcode bir sabit, referans, offset vs. istiyorsa onları takip eder.


**Bytecode Optimizasyonu**
 1. **Dead Code Elimination:**
Kullanılmayan bytecode satırları silinir.

 2. **Peephole Optimization:**
Küçük opcode desenleri daha verimli olanlarla değiştirilir.

 3. **Inlining:**
Sık kullanılan fonksiyonlar direkt olarak çağıran kodun içine kopyalanabilir.


Bytecode, sanal makineler ile fiziksel donanım arasındaki köprüdür. Yüksek seviyeli soyutlamaları çalıştırılabilir hale getirirken:

- Tip güvenliği sağlar
    
- Platform bağımsızlığı sunar
    
- Optimizasyonlara izin verir
    
- Derleyici ve yorumlayıcı teknolojisinin temel yapı taşıdır



<iframe width="560" height="315" src="https://www.youtube.com/embed/cAoymPToQdg" frameborder="0" allowfullscreen></iframe>


---

***Abdullah TANRIVERDİ***

