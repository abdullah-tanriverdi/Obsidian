#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose


Jetpack Compose'daki **`Spacer`** bileşeni, arayüzde boşluk (boş alan) oluşturmak için kullanılan bir düzen (layout) bileşenidir. **Görünmezdir** ve iki bileşen arasına boşluk eklemek için kullanılır.

==**Temel Kullanım**==
```kotlin
Column {
    Text("Üst Metin")
    Spacer(modifier = Modifier.height(16.dp)) // 16dp yüksekliğinde dikey  boşluk ekler
    Text("Alt Metin")
}

```

```kotlin
Row {
    Text("Sol Metin")
    Spacer(modifier = Modifier.width(24.dp)) // 24dp yükseliğinde yatay boşluk
    Text("Sağ Metin")
}

```

```kotlin
Row(modifier = Modifier.fillMaxWidth()) {
    Text("Sol")
    Spacer(modifier = Modifier.weight(1f)) //Dinamik Eşit boşluk bırakır
    Text("Orta")
    Spacer(modifier = Modifier.weight(2f)) // Dinamik Daha büyük boşluk bırakır
    Text("Sağ")
}

```

---

***Abdullah TANRIVERDİ***
