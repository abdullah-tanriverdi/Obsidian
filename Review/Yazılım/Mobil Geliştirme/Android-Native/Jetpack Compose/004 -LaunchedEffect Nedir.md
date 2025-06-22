#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

`LaunchedEffect`, Jetpack Compose içinde side-effect (yan etki) oluşturmak için kullanılan bir Compose API'sidir. Compose bileşeni ilk kez oluşturulduğunda (`Composition` aşamasında) çalıştırılır ve belirli bir anahtar (`key`) değiştiğinde yeniden çalışır.

```kotlin
@Composable
fun MyComposable(value: Int) {
    LaunchedEffect(key1 = value) {
        // value değiştiğinde çalışacak kod bloğu
        println("LaunchedEffect çalıştı: $value")
    }
}

```
Burada `value` değiştikçe `LaunchedEffect` tetiklenir ve içindeki kod çalıştırılır.

==**Ne Zaman Kullanılır?**==

- Asenkron işlemleri başlatmak (ör. API çağrısı, veri tabanı sorgusu)
- Tek seferlik işlemler yapmak (ör. bir ekran yüklendiğinde bir işlem çalıştırmak)
- Composable yaşam döngüsüne bağlı işlemleri yönetmek


==**Key Parametresi ve Yeniden Çalıştırma**==

`LaunchedEffect`’in bir veya daha fazla anahtar parametresi (`key1`, `key2` vb.) olabilir. Eğer anahtar değişirse, `LaunchedEffect` yeniden çalışır.

```kotlin
LaunchedEffect(key1 = Unit) { 
    println("Bu yalnızca bir kez çalışacak") 
}

```
Burada `Unit` kullanıldığı için `LaunchedEffect` sadece **ilk kez** çalışır ve asla yeniden tetiklenmez.



==**Asenkron Çalışma ve `CoroutineScope`**==
`LaunchedEffect` bir **Coroutine Scope** içinde çalışır. Böylece `suspend` fonksiyonları doğrudan çağırabiliriz
```kotlin
LaunchedEffect(key1 = userId) {
    val user = fetchUserData(userId) // Suspend fonksiyon
    println("Kullanıcı verisi çekildi: $user")
}

```
Burada `userId` değiştikçe yeni bir veri çekme işlemi başlatılır.


==**Dikkat Edilmesi Gerekenler**==

- `LaunchedEffect`, anahtar değiştiğinde önceki coroutine’i iptal eder ve yenisini başlatır.
- `rememberCoroutineScope` yerine kullanılabilir, ancak `LaunchedEffect` yalnızca composable yaşam döngüsüne bağlıdır.

==**Alternatif: rememberCoroutineScope**==

Eğer bir işlemi yalnızca kullanıcının etkileşimiyle başlatmak istiyorsanız `rememberCoroutineScope` kullanmalısınız:
```kotlin
val coroutineScope = rememberCoroutineScope()
Button(onClick = {
    coroutineScope.launch {
        fetchUserData(userId)
    }
}) {
    Text("Veriyi Getir")
}

```
Burada `LaunchedEffect` yerine `rememberCoroutineScope` tercih edilir çünkü işlem kullanıcı etkileşimiyle başlatılmalıdır.

***

***Abdullah TANRIVERDİ***

