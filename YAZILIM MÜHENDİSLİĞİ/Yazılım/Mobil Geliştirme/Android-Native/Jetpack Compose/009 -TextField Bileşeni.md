#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

`TextField`, Jetpack Compose'da kullanıcının giriş yapmasını sağlayan bir bileşendir. Kullanıcıdan metin girişi almak için kullanılır ve genellikle formlar, arama çubukları ve yorum alanlarında yer alır.

Jetpack Compose, iki farklı `TextField` bileşeni sunar:

1. **`TextField`** → Standart metin giriş alanı.
2. **`OutlinedTextField`** → Kenarlıklı metin giriş alanı

==**Temel Kullanım**==

```kotlin
var text by remember { mutableStateOf("") }

TextField(
    value = text,
    onValueChange = { text = it },
    label = { Text("Adınızı Girin") }
)

```

- `Placeholder`
Yer tutucu (`placeholder`), kullanıcı henüz bir şey yazmadığında görünen metindir.
```kotlin
TextField(
    value = text,
    onValueChange = { text = it },
    placeholder = { Text("Buraya yazın...") }
)

```


- ``leadingIcon`, `trailingIcon``
`leadingIcon`: Sol tarafa ikon ekler.
 `trailingIcon`: Sağ tarafa ikon ekler.
 ```kotlin
 TextField(
    value = text,
    onValueChange = { text = it },
    label = { Text("E-posta") },
    leadingIcon = { Icon(Icons.Default.Email, contentDescription = "E-posta İkonu") }
)

```

- `PasswordField`
Şifre girişinde metni gizlemek için **`visualTransformation`** kullanılır.
```kotlin
TextField(
    value = password,
    onValueChange = { password = it },
    label = { Text("Şifre") },
    visualTransformation = PasswordVisualTransformation()
)

```
Girilen şifre yerine **●●●●** şeklinde karakterler gösterilir.


- `Hata Mesajı Gösterme`
Girişin geçerli olup olmadığını kontrol etmek için kullanılabilir.
```kotlin
val isError = text.length < 3  // En az 3 karakter olmalı

TextField(
    value = text,
    onValueChange = { text = it },
    label = { Text("Ad") },
    isError = isError,
    supportingText = {
        if (isError) Text("En az 3 karakter giriniz!", color = Color.Red)
    }
)

```


- `keyboardOptions`
`keyboardOptions` ile giriş türü belirlenebilir.
```kotlin
TextField(
    value = text,
    onValueChange = { text = it },
    label = { Text("Yaşınızı Girin") },
    keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Number)
)

```


- `OutlinedTextField`
Daha modern bir görünüm için **`OutlinedTextField`** kullanılabilir.
```kotlin
OutlinedTextField(
    value = text,
    onValueChange = { text = it },
    label = { Text("Kullanıcı Adı") }
)

```

---

***Abdullah TANRIVERDİ***
