#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

==**Temel Kullanım**==

`Image` bileşeni, painter (resim kaynağı) ve contentDescription (erişilebilirlik) parametreleri ile çalışır.
```kotlin
Image(
    painter = painterResource(id = R.drawable.ic_launcher_foreground),
    contentDescription = "Uygulama İkonu"
)

```

- `contentScale`
 **Crop:** Resmi kırpar, tüm alanı kaplar.
 **Fit:** Resmi bozmadan sığdırır.
**FillBounds:** Tüm alanı kaplar ama bozulabilir.
 **Inside:** Resmi sığdırır ama kesmez.
```kotlin
Image(
    painter = painterResource(id = R.drawable.sample),
    contentDescription = "Örnek Resim",
    modifier = Modifier.size(200.dp),
    contentScale = ContentScale.Crop  // Kırpma
)

```


- `clip()`
Resmi **daire veya yuvarlak köşeli** yapabiliriz.
```kotlin
Image(
    painter = painterResource(id = R.drawable.sample),
    contentDescription = "Yuvarlak Resim",
    modifier = Modifier
        .size(100.dp)
        .clip(CircleShape) // Resmi daire yapar
)

```


**İnternetten Resim Yükleme**
Jetpack Compose, **doğrudan** internetten resim yükleyemez. Bunun için **Coil veya Glide** kütüphaneleri kullanılır.
```kotlin
import coil.compose.rememberImagePainter

Image(
    painter = rememberImagePainter("https://www.example.com/image.jpg"),
    contentDescription = "İnternet Resmi"
)

```

---

***Abdullah TANRIVERDİ***