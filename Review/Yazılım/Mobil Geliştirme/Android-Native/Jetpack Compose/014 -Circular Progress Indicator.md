#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

`CircularProgressIndicator`, kullanıcıya bir işlemin devam ettiğini göstermek için kullanılan bir bileşendir.

**Temel Kullanım**
```kotlin
@Composable
fun CircularProgressExample() {
    CircularProgressIndicator()
}

```


- `color`
`color` parametresi ile gösterge rengini değiştirebiliriz
```kotlin
@Composable
fun ColoredCircularProgress() {
    CircularProgressIndicator(color = Color.Red)
}

```


- `size`
Modifier ile `size` özelliği kullanılarak çemberin boyutu değiştirilebilir
```kotlin
@Composable
fun SizedCircularProgress() {
    CircularProgressIndicator(
        modifier = Modifier.size(80.dp), // Çapı 80dp yapar
        color = Color.Green
    )
}

```

- `progress`
Eğer sonsuz bir animasyon yerine belirli bir ilerleme seviyesi göstermek istiyorsak, `progress` parametresini kullanabiliriz.

```kotlin
@Composable
fun ProgressCircularIndicator() {
    CircularProgressIndicator(progress = 0.5f) // %50 dolu
}

```
`progress` Değeri:
- `0.0f` → **Tamamen boş**
- `1.0f` → **Tamamen dolu**
---

***Abdullah TANRIVERDİ***

