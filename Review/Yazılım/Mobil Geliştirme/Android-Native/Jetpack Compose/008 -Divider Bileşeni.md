#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose



**`Divider`**, Jetpack Compose'da bileşenleri görsel olarak ayırmak için kullanılan yatay veya dikey bir çizgidir. Genellikle menülerde, listelerde veya içerik blokları arasında kullanılır.

==**Temel Kullanım**==
```kotlin
Column {
    Text("Üst Metin")
    Divider()  // Standart Divider
    Text("Alt Metin")
}

```

==**Divider Bileşeninin Temel Özellikleri**==


- `thickness`
**Açıklama:** Divider'ın kalınlığını belirlemek için kullanılır.
```kotlin
Divider(thickness = 4.dp)

```

- `color`
**Açıklama:** Divider'ın rengini değiştirmek için kullanılır.
```kotlin
Divider(color = Color.Red)

```

- `modifier = Modifier.fillMaxWidth()`
**Açıklama:** Divider'ın genişliğini veya yüksekliğini değiştirmek için `Modifier.fillMaxWidth()` veya `Modifier.width()` kullanılabilir.
```kotlin
Divider(modifier = Modifier.fillMaxWidth(0.5f)) // %50 genişlikte Divider

```

---

***Abdullah TANRIVERDİ***






