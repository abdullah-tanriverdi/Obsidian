#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

Jetpack Compose'daki **`Card`** bileşeni, içerikleri kart formatında göstermek için kullanılır.

==**Temel Kullanım**==

```kotlin
Card(
    modifier = Modifier.padding(16.dp),
    elevation = CardDefaults.cardElevation(defaultElevation = 4.dp)
) {
    Text(
        text = "Bu bir kart örneğidir.",
        modifier = Modifier.padding(16.dp)
    )
}

```

- `shape`
Kartın köşelerini yuvarlatmak için `RoundedCornerShape()` kullanılır.
```kotlin
Card(
    shape = RoundedCornerShape(16.dp), // Köşe yuvarlatma
    elevation = CardDefaults.cardElevation(defaultElevation = 6.dp),
    modifier = Modifier.padding(8.dp)
) {
    Text("Yuvarlatılmış Köşeli Kart", modifier = Modifier.padding(16.dp))
}

```


- `colors`
Kartın arka plan rengini değiştirmek için `colors` parametresi kullanılır.
```kotlin
Card(
    colors = CardDefaults.cardColors(containerColor = Color.LightGray),
    modifier = Modifier.padding(8.dp)
) {
    Text("Arka Plan Renkli Kart", modifier = Modifier.padding(16.dp))
}

```


- `clickable`
Kartı tıklanabilir yapmak için `Modifier.clickable` kullanılabilir.
```kotlin
Card(
    modifier = Modifier
        .padding(8.dp)
        .clickable { println("Kart tıklandı!") },
    elevation = CardDefaults.cardElevation(defaultElevation = 6.dp)
) {
    Text("Tıklanabilir Kart", modifier = Modifier.padding(16.dp))
}

```

---

***Abdullah TANRIVERDİ***
