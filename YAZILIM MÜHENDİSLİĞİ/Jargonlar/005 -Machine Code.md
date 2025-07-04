#Yazılım #Yazılım-Jargon 


Makine Kodu (Machine Code), bir bilgisayarın merkezi işlem birimi (CPU) tarafından doğrudan yürütülebilen, ikili sayı sistemi (binary) ile yazılmış komutlardır. Bu kod, yazılımın en düşük seviyesini oluşturur ve bilgisayar donanımı ile yazılım arasındaki en temel iletişim dilidir.

Not: Makine kodu genellikle hexadecimal (onaltılık) formatta gösterilir, ancak bu yalnızca insanların okumasını kolaylaştırmak içindir.


> [!tip] İPUCU
> Sayı sistemleri hakkında daha fazla bilgi almak için bağlantıya tıkla [[Sayı Sistemleri]]

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


> [!tip] İPUCU
> Compiler hakkında daha fazla bilgi almak için bağlantıya tıkla [[Compiler]]
> Interpreter hakkında daha fazla bilgi almak için bağlantıya tıkla  [[Interpreter]]
> Assembly hakkında daha fazla bilgi almak için bağlantıya tıkla [[Assembly]]

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


***
***Abdullah TANRIVERDİ***
