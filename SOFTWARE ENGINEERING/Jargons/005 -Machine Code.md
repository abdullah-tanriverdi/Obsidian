#Yazılım #Yazılım-Jargon 


Makine Kodu (Machine Code), bir bilgisayarın merkezi işlem birimi (CPU) tarafından doğrudan yürütülebilen, ikili sayı sistemi (binary) ile yazılmış komutlardır. Bu kod, yazılımın en düşük seviyesini oluşturur ve bilgisayar donanımı ile yazılım arasındaki en temel iletişim dilidir.

Not: Makine kodu genellikle hexadecimal (onaltılık) formatta gösterilir, ancak bu yalnızca insanların okumasını kolaylaştırmak içindir.


**Bilgisiyarlar Makine Kodunu Nasıl Kullanır?**

**Von Neumann Mimarisi**
Birçok modern bilgisayar, Von Neumann mimarisine dayanır. Bu mimaride:

- Komutlar ve veriler aynı bellekte yer alır.
    
- Komutlar, işlemci tarafından sırasıyla okunur ve yürütülür.
    
- Her komut makine kodu biçimindedir ve Instruction Register (IR) içine yüklenerek işlenir.

**Instruction Cycle (Komut Döngüsü)**
Makine kodları CPU tarafından şu adımlarla yürütülür:

1. Fetch – Komut, bellekten alınır.
    
2. Decode – Komut çözümlenir.
    
3. Execute – Komut yürütülür.
    
4. Store  – Sonuç belleğe yazılır.


Makine kodu komutları, işlemci mimarisine göre değişiklik gösterir, ancak genel yapı şunları içerir:


```
| OPCODE (n bit) | OPERAND 1 | OPERAND 2 | ... |


```

- OPCODE (Operation Code):

Yapılacak işlemi belirtir (örneğin toplama, çıkarma, taşıma vb.)

- OPERAND(S):

İşlem yapılacak veri, bellek adresi veya register’lar olabilir.



|Tür|Açıklama|
|---|---|
|Veri Transferi|`MOV`, `LOAD`, `STORE`|
|Aritmetik|`ADD`, `SUB`, `MUL`, `DIV`|
|Mantıksal|`AND`, `OR`, `XOR`, `NOT`|
|Kontrol|`JMP`, `CALL`, `RET`, `JE`, `JNE`|
|Giriş/Çıkış|`IN`, `OUT`|


Üst düzey dillerde (C, Python, Java vb.) yazılan kodlar doğrudan CPU tarafından çalıştırılamaz. Bunlar önce makine koduna dönüştürülür.

| Araç                          | Görev                                                            |
| ----------------------------- | ---------------------------------------------------------------- |
| **Compiler (Derleyici)**      | Tüm kodu makine koduna çevirir ve çalıştırılabilir hale getirir. |
| **Interpreter (Yorumlayıcı)** | Kodu satır satır okuyup o anda çalıştırır.                       |
| **Assembler (Yazıcı)**        | Assembly kodunu makine koduna çevirir.                           |


**Assembly (x86)**
```asm
MOV AX, 4C00h
INT 21h

```


**Makine Kodu (Binary/Hex)**
```scss
B8 00 4C
CD 21


```
- `MOV AX, 4C00h`: AX register’ına 4C00 değeri yüklenir.
    
- `INT 21h`: DOS interrupt – program sonlandırılır
Makine kodu, yazılımın donanımla buluştuğu noktadır. Modern programlama dilleri bu kodları üretmek için araç görevi görse de, sistem düzeyinde yazılım geliştiren herkesin makine kodunun nasıl çalıştığını anlaması gerekir.

“Yazılımın donanımla gerçekten konuşmaya başladığı yer, makine kodudur. Bir yazılımcı için orası hem korkutucu hem de büyüleyici olabilir.”

|Özellik|**Bytecode**|**Machine Code (Makine Kodu)**|
|---|---|---|
|**Tanım**|Sanal bir makine (örneğin JVM, .NET CLR) tarafından yürütülen orta seviye kod|Gerçek işlemci (CPU) tarafından doğrudan yürütülen düşük seviye kod|
|**Bağımlılık**|Platforma değil, sanal makineye bağımlıdır|İşlemci mimarisine (x86, ARM vs.) bağımlıdır|
|**Taşınabilirlik**|Yüksek – farklı sistemlerde aynı bytecode çalışabilir|Düşük – her işlemciye özel olarak derlenmelidir|
|**Yürütme Ortamı**|Sanal Makine (örneğin Java Virtual Machine)|Donanım – fiziksel CPU|
|**Okunabilirlik**|İnsan tarafından kısmen anlaşılabilir|Genellikle tamamen ikili (binary) ve okunamaz|
|**Performans**|Machine code’dan genellikle daha yavaştır (çünkü yorumlanır ya da JIT ile çalıştırılır)|En yüksek performans – doğrudan donanımda çalışır|
|**Derleme Süreci**|Yüksek seviyeli dilden bytecode’a derlenir, sonra VM tarafından çalıştırılır|Yüksek seviyeli dilden doğrudan makine koduna derlenir|
|**Örnek Kullanım**|Java, Python (CPython bytecode), .NET (IL code)|C, C++ gibi dillerin derlenmiş çıktısı|
|**Çalışma Zamanı**|Yorumlayıcı (Interpreter) veya JIT derleyici ile çalışır|Derlenmiş hali doğrudan CPU tarafından çalıştırılır|

```python
a = 2 + 3

```

```python
import dis
dis.dis("a = 2 + 3")

```


- **Bytecode Çıktısı**
```scss
  1           0 LOAD_CONST               0 (2)
              2 LOAD_CONST               1 (3)
              4 BINARY_ADD
              6 STORE_NAME               0 (a)
              8 LOAD_CONST               2 (None)
             10 RETURN_VALUE

```

- `LOAD_CONST 0 (2)`: 2 sabitini yükle
    
- `LOAD_CONST 1 (3)`: 3 sabitini yükle
    
- `BINARY_ADD`: İki sayıyı topla
    
- `STORE_NAME 0 (a)`: Sonucu `a`'ya ata
    
- Bu, Python Sanal Makinesi (PVM) tarafından çalıştırılır.


```c
int main() {
    int a = 2 + 3;
    return 0;
}

```


- **Derlendikten Sonra (Assembly/Machine Code)**
```assembly
mov eax, 2
add eax, 3
mov [a], eax

```
Bu assembly kodu, derleyici tarafından makine koduna (binary) çevrilir:

```ruby
B8 02 00 00 00    ; mov eax, 2
83 C0 03          ; add eax, 3
A3 ?? ?? ?? ??    ; mov [a], eax (?? adresi temsil eder)

```
- Gerçek CPU tarafından doğrudan çalıştırılır.
    
- İşlemciye özel bir kodlama biçimiyle yazılmıştır.
    
- Donanıma çok yakındır ve platform bağımlıdır.

- **Örnek Özeti**

|Aşama|Bytecode|Machine Code|
|---|---|---|
|Kaynak Dil|Python|C / C++|
|Ara Katman|Python Bytecode (PVM içindir)|Assembly → Binary (CPU içindir)|
|Ortam|Sanal Makine (örneğin CPython)|Doğrudan donanım (x86 CPU vb.)|


> [!tip] İPUCU
> Sayı sistemleri hakkında daha fazla bilgi almak için bağlantıya tıkla [[Number Systems]]
> Compiler hakkında daha fazla bilgi almak için bağlantıya tıkla [[006 -Compiler]]
> Interpreter hakkında daha fazla bilgi almak için bağlantıya tıkla  [[007 -Interpreter]]
> Assembly hakkında daha fazla bilgi almak için bağlantıya tıkla [[008 -Assembly]]

---

***Abdullah TANRIVERDİ***
