#Yazılım #Yazılım-Jargon 



![[Exception Handling1.png|500]]
Hata yönetimi, bir programda beklenmeyen hataların (exceptions) doğru bir şekilde ele alınmasını sağlayarak programın çökmemesini veya yanlış çalışmamasını sağlar.

**Exception (İstisna) Nedir?**

- Bir program çalışırken meydana gelen ve normal akışı bozan beklenmedik olaydır.
- Örnek: Bölme işleminde sıfıra bölme, dosyanın bulunamaması, null referansı kullanma gibi durumlar.

**Exception Türleri**

1. **Checked Exceptions (Kontrol Edilen İstisnalar):**
    
    - Derleme sırasında kontrol edilir.
    - Örneğin: Java'da `IOException`, `SQLException`.
2. **Unchecked Exceptions (Kontrol Edilmeyen İstisnalar):**
    
    - Çalışma zamanı hatalarıdır.
    - Örneğin: `NullPointerException`, `ArrayIndexOutOfBoundsException`.
3. **Errors (Hatalar):**
    
    - Sistem kaynaklı sorunları ifade eder.
    - Örneğin: `OutOfMemoryError`.


**Exception Handling Mekanizması**

Hata yönetimi mekanizması, bir hata meydana geldiğinde:

1. Hata mesajını oluşturur.
2. Programın kalan kısmına zarar vermeden hata ile ilgilenir.
3. Gerekirse programı sonlandırır.

**Hata Yönetiminde Kullanılan Yapılar**

**a. Try-Catch Bloğu**

- Hataları yakalamak ve işlem yapmak için kullanılır.
    
- **Yapısı:**
```java
try {
    // Hata oluşabilecek kod
} catch (ExceptionType e) {
    // Hatanın ele alınması
}

```

**b. Finally Bloğu**

- Hata olsun ya da olmasın mutlaka çalışan bloktur.
- Kaynakları serbest bırakmak için kullanılır (örneğin: dosya kapatma, bellek temizleme).
```java
try {
    // Kod
} finally {
    System.out.println("Bu blok her zaman çalışır.");
}

```


**c. Throw ve Throws**

- **`throw`**: Hata fırlatmak için kullanılır.
    
    ```java
    throw new Exception("Bir hata oluştu!");`
```

- **`throws`**: Bir metodun hata fırlatabileceğini belirtir.
```java
`public void myMethod() throws IOException { //kod
}
```


**Çalışma Zamanı Hatalarını Önleme**  

1. **Input Validation:** Kullanıcıdan gelen girdileri kontrol edin.
2. **Null Kontrolleri:** Referansların `null` olmadığından emin olun.
3. **Kaynak Yönetimi:** Dosya, soket veya bellek sızıntılarını önleyin.

Hata yönetimi, bir programın dayanıklılığını artırır ve kullanıcı deneyimini iyileştirir. Doğru uygulandığında, uygulamalarınız daha güvenilir ve hatalara karşı dirençli hale gelir.

---
***Abdullah TANRIVERDİ***
