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



- **Scrollable Column (Kaydırılabilir Alan)**

Eğer içeriğiniz çok uzunsa **scroll özelliği** eklemek için `Modifier.verticalScroll()` kullanabilirsiniz.

```kotlin
@Composable
fun ScrollableColumnExample() {
    Column(
        modifier = Modifier
            .fillMaxSize()
            .verticalScroll(rememberScrollState()) // Scroll özelliği ekler
    ) {
        for (i in 1..50) {
            Text(text = "Öğe $i", fontSize = 20.sp, modifier = Modifier.padding(8.dp))
        }
    }
}

```



- **Weight Kullanımı ile Esnek Yerleşim**
**`Modifier.weight()`**, iç bileşenlerin alanı **eşit veya belirli oranlarda paylaşmasını** sağlar.
```kotlin
@Composable
fun WeightedColumnExample() {
    Column(modifier = Modifier.fillMaxSize()) {
        Box(modifier = Modifier.weight(1f).fillMaxWidth().background(Color.Red))
        Box(modifier = Modifier.weight(2f).fillMaxWidth().background(Color.Green))
        Box(modifier = Modifier.weight(1f).fillMaxWidth().background(Color.Blue))
    }
}

```
- **1:2:1 oranında** üç farklı renkte kutu oluşturur.
- **`weight(1f)`** → Alanın **1 birimini** kaplar.
- **`weight(2f)`** → Alanın **2 birimini** kaplar.

- **LazyColumn**
Büyük listeleri **performanslı bir şekilde** göstermek için kullanılan bir Jetpack Compose bileşenidir.  
Standart **Column** tüm öğeleri hafızada tutarken, **LazyColumn** yalnızca ekranda görünen öğeleri oluşturur ve gerektiğinde yeniden kullanır.

✔ **Performanslıdır** → Sadece görünen öğeleri işler, gereksiz bellek tüketimini önler.  
✔ **Büyük listeler için idealdir** → Binlerce öğe içeren listelerde sorunsuz çalışır.  
✔ **Otomatik kaydırma (scrolling)** desteği vardır.

```kotlin
@Composable
fun SimpleLazyColumnExample() {
    LazyColumn {
        items(50) { index ->
            Text(
                text = "Öğe $index",
                fontSize = 20.sp,
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(8.dp)
                    .background(Color.LightGray)
            )
        }
    }
}

```
- **50 öğeden oluşan bir liste** oluşturur.
- **Sadece görünen öğeleri render eder**, performans sağlar.

Bazı durumlarda kaydırma (scroll) durumunu izlemek isteyebiliriz. `rememberLazyListState()` ile **scroll durumunu** yönetebiliriz.
```kotlin
@Composable
fun ScrollStateExample() {
    val listState = rememberLazyListState()

    LazyColumn(state = listState) {
        items(50) { index ->
            Text(
                text = "Öğe $index",
                fontSize = 20.sp,
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(16.dp)
            )
        }
    }
}


```

- `rememberLazyListState()` ile **scroll durumunu kontrol ettik**.
- `state = listState` parametresi ile **LazyColumn'a bu durumu bağladık**.


**LazyColumn vs Column Karşılaştırması**

|**Özellik**|**LazyColumn**|**Column**|
|---|---|---|
|**Performans**|Yalnızca ekranda görünen öğeleri oluşturur|Tüm öğeleri aynı anda oluşturur|
|**Büyük Listeler İçin Uygun mu?**|✅ Evet|❌ Hayır|
|**Bellek Kullanımı**|Düşük|Yüksek|
|**Kaydırılabilir mi?**|Evet, kendiliğinden kaydırılabilir|Hayır, `Modifier.verticalScroll()` eklenmesi gerekir|


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


- **Row İçinde Scroll (Yatay Kaydırma)**
Eğer `Row` içeriği fazla uzun olacaksa, **kaydırma (scroll) özelliği** ekleyebiliriz.
```kotlin
@Composable
fun ScrollableRowExample() {
    Row(
        modifier = Modifier
            .fillMaxWidth()
            .horizontalScroll(rememberScrollState()) // Yatay scroll özelliği ekler
    ) {
        for (i in 1..10) {
            Text(
                text = "Öğe $i",
                fontSize = 20.sp,
                modifier = Modifier
                    .padding(8.dp)
                    .background(Color.LightGray)
            )
        }
    }
}

```




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
