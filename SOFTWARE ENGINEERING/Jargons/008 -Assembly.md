#Yazılım #Yazılım-Jargon 

![[Assembly1.jpg|400]]

Assembly dili, bilgisayar donanımına çok yakın, düşük seviyeli bir programlama dilidir.

- Her işlemci mimarisi için özel olarak tasarlanır.
    
- İnsan tarafından okunabilir semboller ve kısaltmalar (mnemonics) kullanılır.
    
- Makine dilinin daha anlaşılır hâline getirilmiş versiyonudur.

**Neden Assembly**
- Doğrudan donanım kontrolü sağlar.
    
- Performans kritik sistemlerde, işletim sistemi çekirdeği, sürücüler, gömülü sistemlerde kullanılır.
    
- Yüksek seviyeli dillerin derleyicisinin yapamadığı optimizasyonlar yapılabilir.


**Makine Dili Ve Assembly**
- Makine dili, işlemcinin doğrudan anladığı ikili koddur (binary).
    
- Assembly dili, makine kodunun mnemonik karşılıkları ve sembollerle yazılmasıdır.
    
- Örneğin, `MOV AX, 1` gibi.


> [!info] Mnemonics
> - Her işlemci komutunun kısa ve anlamlı bir adı vardır.
>- Örnekler: `MOV` (taşı), `ADD` (topla), `SUB` (çıkar), `JMP` (atla).


**Komutlar**
```nginx
OPCODE DESTINATION, SOURCE

MOV AX, 5   ; AX ;register 'ına 5 değerini yükle
ADD AX, BX  ; AX = AX + BX
MOV AX, [BX + SI]



```

Yorum satırları `;` ile başlar ve satır sonuna kadar devam eder.


|Komut|İşlevi|Örnek|
|---|---|---|
|MOV|Veri taşıma|`MOV AX, BX`|
|ADD|Toplama|`ADD AX, 1`|
|SUB|Çıkarma|`SUB BX, AX`|
|INC|Bir artırma|`INC CX`|
|DEC|Bir azaltma|`DEC DX`|
|JMP|Koşulsuz atlama|`JMP LABEL`|
|JZ/JNZ|Koşullu atlama (sıfır veya değil)|`JZ END`|
|CMP|Karşılaştırma|`CMP AX, BX`|
|CALL|Fonksiyon çağrısı|`CALL FUNC`|
|RET|Fonksiyondan dönüş|`RET`|
**Bellek Adresleme Modları**
- **Doğrudan Adresleme:** Bellekteki belirli bir adrese erişim
    
- **Dolaylı Adresleme:** Register üzerinden bellek adresine erişim
    
- **İndeksli Adresleme:** Base adres + offset kullanımı

```assembly
MOV AX, [1000h]    ; Bellekten 0x1000 adresindeki veriyi AX'e yükle
MOV BX, [SI+5]     ; SI register’ı + 5 offsetindeki bellek adresinden yükle

```


**Örnek Basit Program**
```assembly
; 2 sayıyı toplayıp sonucu AX register'ına koyar
MOV AX, 5
MOV BX, 3
ADD AX, BX

```

<iframe width="560" height="315" src="https://www.youtube.com/embed/4gwYkEK0gOk" title="YouTube video player" frameborder="0" allowfullscreen></iframe>


***

***Abdullah TANRIVERDİ***