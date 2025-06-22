#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

Jetpack Compose'ta **Button** bileşeni, kullanıcı etkileşimleri için yaygın olarak kullanılan ve tıklanabilir bir bileşendir. `Button`, genellikle bir işlemi tetiklemek veya bir eylem gerçekleştirmek amacıyla kullanılır. Compose'da, butonlar sadece UI bileşenleri değil, aynı zamanda işlevsel birimlerdir.

**Temel Kullanımı** 
```kotlin
Button(onClick = { /* Burada işlem yapılır */ }) {
    Text("Tıkla")
}

```
- `onClick`: Butona tıklandığında çalıştırılacak işlev.
- `Text`: Butonun içinde görüntülenecek metin.


==**Button Bileşeninin Temel Özellikleri**==
- `enabled`
**Açıklama:** Butonun aktif olup olmadığını kontrol eder. `enabled = false` ile buton devre dışı bırakılabilir.
```kotlin
Button(onClick = { /* İşlem */ }, enabled = false) {
    Text("Devre Dışı Buton")
}

```


- `colors` 
**Açıklama:** Butonun renklerini özelleştirmek için kullanılır. `ButtonDefaults.buttonColors()` ile butonun farklı durumları için renkler ayarlanabilir: `backgroundColor`, `contentColor`, `disabledBackgroundColor`, `disabledContentColor`.
```kotlin
Button(
    onClick = { /* İşlem */ },
    colors = ButtonDefaults.buttonColors(backgroundColor = Color.Red)
) {
    Text("Kırmızı Buton")
}

```


- `shape`
**Açıklama**: Butonun kenarlarının şeklini belirler. Yuvarlak, dikdörtgen veya özel bir şekil verilebilir.
```kotlin
Button(
    onClick = { /* İşlem */ },
    shape = MaterialTheme.shapes.medium
) {
    Text("Yuvarlak Kenarlı Buton")
}

```


- `contentPadding`
**Açıklama:** Buton içindeki metnin etrafında bir boşluk ayarlamak için kullanılır.
```kotlin
Button(
    onClick = { /* İşlem */ },
    contentPadding = PaddingValues(24.dp)
) {
    Text("Büyük Paddingli Buton")
}

```


==**Button Tipleri**==
Jetpack Compose, butonların farklı stil ve özelliklerde görünmesini sağlayan çeşitli buton türlerini de destekler.

- `OutlinedButton` 
**Açıklama**: Butonun kenarları çizgili olup, genellikle daha hafif bir görünüm sağlar.
```kotlin
OutlinedButton(onClick = { /* İşlem */ }) {
    Text("Outline Buton")
}

```

- `TextButton`
**Açıklama**: Yalnızca metin içerir ve arka planı yoktur, daha minimal bir tasarıma sahiptir
```kotlin
TextButton(onClick = { /* İşlem */ }) {
    Text("Metin Butonu")
}

```

- `IconButton`
**Açıklama**: Buton, bir ikon içerir ve metin yerine ikon kullanılır.
```kotlin
IconButton(onClick = { /* İşlem */ }) {
    Icon(Icons.Default.Favorite, contentDescription = "Favori")
}

```

- `FloatingActionButton`
**Açıklama**: Ekranda genellikle yuvarlak, yükseltilmiş bir buton olarak görünür.
```kotlin
FloatingActionButton(onClick = { /* İşlem */ }) {
    Icon(Icons.Default.Add, contentDescription = "Ekle")
}

```


==**Button'un Görünümünü Özelleştirmek**==
Butonun görsel özelliklerini özelleştirmek için, `ButtonDefaults` ve `Modifier` gibi araçlar kullanılarak butonun boyutları, renkleri ve şekilleri değiştirebilir.
```kotlin
Button(
    onClick = { /* İşlem */ },
    modifier = Modifier
        .padding(16.dp)
        .height(50.dp)
        .fillMaxWidth(),
    colors = ButtonDefaults.buttonColors(backgroundColor = Color.Blue)
) {
    Text("Mavi Buton", color = Color.White)
}

```

---

***Abdullah TANRIVERDİ***
