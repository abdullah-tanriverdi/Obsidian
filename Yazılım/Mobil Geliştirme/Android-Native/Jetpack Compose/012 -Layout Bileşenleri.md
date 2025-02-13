#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

Jetpack Compose’da **Column, Row ve Box** bileşenleri, içerikleri düzenlemek için kullanılır.

- **`Column`** → **Dikey hizalama (Alt alta yerleştirme)**
- **`Row`** → **Yatay hizalama (Yan yana yerleştirme)**
- **`Box`** → **Üst üste yerleştirme**

==**Column (Dikey Düzen)**==

**Temel Kullanım**

```kotlin
Column {
    Text("Üstteki Metin")
    Text("Alttaki Metin")
}

```

- `verticalArrangement`

`verticalArrangement` ile içerikleri başlangıca, merkeze veya sona hizalayabiliriz.
```kotlin
Column(
    modifier = Modifier.fillMaxSize(),
    verticalArrangement = Arrangement.Center // Ortaya hizalar
) {
    Text("Ortaya hizalanmış metin")
}

```

- `Arrangement.Top` → Üste hizalar
- `Arrangement.Center` → Ortaya hizalar
- `Arrangement.Bottom` → Alta hizalar
- `Arrangement.SpaceBetween` → Üst ve alt kenara dayalı hizalar
- `Arrangement.SpaceAround` → Kenarlardan eşit boşluk bırakır
- `Arrangement.SpaceEvenly` → İçerikleri eşit aralıklarla dizer



- `horizontalAlignment`
`horizontalAlignment` ile metinleri yatayda hizalayabiliriz.
``
```kotlin
Column(
    modifier = Modifier.fillMaxWidth(),
    horizontalAlignment = Alignment.CenterHorizontally // Yatay ortalar
) {
    Text("Bu metin ortalanmış!")
}

```

- `Alignment.Start` → Sola hizalar
- `Alignment.CenterHorizontally` → Ortaya hizalar
- `Alignment.End` → Sağa hizalar


==**Row (Yatay Hizalama)**==

**Temel Kullanım**
```kotlin
Row {
    Text("Sol")
    Text("Orta")
    Text("Sağ")
}

```

- `horizontalArrangement`
```kotlin
Row(
    modifier = Modifier.fillMaxWidth(),
    horizontalArrangement = Arrangement.Center // Ortaya hizalar
) {
    Text("Ortalı metin")
}

```

- `Arrangement.Start` → Sola hizalar
- `Arrangement.Center` → Ortaya hizalar
- `Arrangement.End` → Sağa hizalar
- `Arrangement.SpaceBetween` → Baş ve son kenarlara dayalı hizalar
- `Arrangement.SpaceAround` → Kenarlardan eşit boşluk bırakır
- `Arrangement.SpaceEvenly` → İçerikleri eşit aralıklarla dizer



- `verticalAlignment`
```kotlin
Row(
    modifier = Modifier.fillMaxWidth(),
    verticalAlignment = Alignment.CenterVertically // Dikeyde ortalar
) {
    Text("Bu metin dikeyde ortalanmış!")
}

```

- `Alignment.Top` → Üste hizalar
- `Alignment.CenterVertically` → Ortaya hizalar
- `Alignment.Bottom` → Alta hizalar




==**Box(Üst Üste Yerleşim)**==

**Temel Kullanım**
```kotlin
*Box(modifier = Modifier.size(200.dp)) {
    Text("Bu bir Box içinde!")
}
*
```

- `contentAlignment`
```kotlin
Box(
    modifier = Modifier
        .size(200.dp)
        .background(Color.LightGray),
    contentAlignment = Alignment.Center // Ortaya hizalar
) {
    Text("Ortalanmış Metin")
}

```

- `Alignment.TopStart` → Sol üst
- `Alignment.TopCenter` → Üst orta
- `Alignment.TopEnd` → Sağ üst
- `Alignment.CenterStart` → Ortada sol
- `Alignment.Center` → Tam merkez
- `Alignment.CenterEnd` → Ortada sağ
- `Alignment.BottomStart` → Sol alt
- `Alignment.BottomCenter` → Alt orta
- `Alignment.BottomEnd` → Sağ alt


**Column-Row-Box Kombinasyonu**
```kotlin
Column(modifier = Modifier.fillMaxSize()) {
    Box(
        modifier = Modifier
            .fillMaxWidth()
            .height(200.dp)
            .background(Color.Blue),
        contentAlignment = Alignment.Center
    ) {
        Text("Başlık", color = Color.White, fontSize = 24.sp)
    }

    Row(
        modifier = Modifier.fillMaxWidth(),
        horizontalArrangement = Arrangement.SpaceAround
    ) {
        Text("Sol")
        Text("Orta")
        Text("Sağ")
    }
}

```
**Sonuç:**

- Üstte mavi bir Box (başlık)
- Altında Row içinde üç metin olur.

---

***Abdullah TANRIVERDİ***
