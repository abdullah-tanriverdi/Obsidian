#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

Jetpack Compose'da metin görüntülemek için kullanılan temel bileşen **`Text`** bileşenidir. `Text` bileşeni, kullanıcılara yazılı içerik sunmak için çeşitli özellikler ve modifikasyonlar ile esnek bir yapı sunar.

==**Temel Kullanım**==
```kotlin
Text("Merhaba")
```
Bu, ekranda sadece basit bir metin görüntüler. `Text` bileşeni, sadece bir metin gösterme amacıyla kullanılabilir.

==**Text Bileşeninin Temel Özellikleri**==
- `text`
**Açıklama**: Görüntülenecek metnin içeriği.
```kotlin
Text("Hello, World!")

```

- `fontSize`
**Açıklama:** Metnin boyutunu ayarlamak için kullanılır. `TextUnit` cinsinden ifade edilir.
```kotlin
Text("Büyük Yazı", fontSize = 24.sp)

```

- `color`
**Açıklama**: Metnin rengini belirler. `Color` sınıfı ile renk belirlenebilir.
```kotlin
Text("Kırmızı Metin", color = Color.Red)

```

- `fontWeight`
**Açıklama**: Metnin kalınlık seviyesini ayarlamak için kullanılır. `FontWeight` sınıfı ile değerler belirlenebilir.
```kotlin
Text("Kalın Yazı", fontWeight = FontWeight.Bold)

```

- `fontStyle`
**Açıklama**: Metnin stilini belirlemek için kullanılır
```kotlin
Text("İtalik Yazı", fontStyle = FontStyle.Italic)

```

-  `textAlign` 
**Açıklama**: Metnin hizalanmasını kontrol eder (sol, sağ, ortalanmış).
```kotlin
Text("Ortalanmış Metin", textAlign = TextAlign.Center)

```

- `lineHeight`
**Açıklama**: Metin satır yüksekliğini ayarlamak için kullanılır.
```kotlin
Text("Satır Yüksekliği Ayarlanmış", lineHeight = 30.sp)

```


- `letterSpacing` 
**Açıklama:**  Metindeki harfler arasındaki boşluğu ayarlamak için kullanılır.
```kotlin
Text("Harfler Arası Boşluk", letterSpacing = 2.sp)

```

- `AnnotatedString`
**Açıklama:** Jetpack Compose, metin üzerinde stil uygulamak için **`AnnotatedString`** sınıfını kullanmamıza olanak tanır. Bu sınıf, metin içerisine stil özellikleri ekleyerek zengin metinler oluşturmamıza yardımcı olur.
```kotlin
val text = buildAnnotatedString {
    append("Normal Metin ")
    withStyle(style = SpanStyle(color = Color.Red, fontWeight = FontWeight.Bold)) {
        append("Kırmızı ve Kalın Metin")
    }
    append(" Sonra Normal Metin.")
}

Text(text)

```

---

***Abdullah TANRIVERDİ*** 