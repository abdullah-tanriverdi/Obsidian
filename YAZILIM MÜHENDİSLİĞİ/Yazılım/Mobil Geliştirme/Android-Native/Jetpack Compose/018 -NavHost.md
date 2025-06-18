#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 

Jetpack Compose, Android'de modern bir UI oluşturma yaklaşımıdır ve gezinme işlemleri için `Navigation Component` kütüphanesini kullanır. Geleneksel `Fragment` veya `Activity` tabanlı navigasyondan farklı olarak, Compose’da **NavHost** ve **NavController** bileşenleri kullanılır.

Jetpack Compose’da Navigation kullanmak için aşağıdaki bağımlılıkları `build.gradle.kts` dosyanıza ekleyin:
```kotlin
dependencies {
    implementation("androidx.navigation:navigation-compose:2.7.6")
}

```
Bu kütüphane sayesinde **NavController**, **NavHost** ve **NavGraph** gibi bileşenleri kullanabiliriz.



Jetpack Compose’da gezinme için aşağıdaki bileşenler kullanılır:

- **`NavController`**: Uygulamanın gezinme durumunu yöneten kontrol birimi.
- **`NavHost`**: Uygulama içinde farklı ekranlar arasında geçişi yöneten kapsayıcı.
- **`NavGraph`**: Gezinme yollarını belirleyen yapı.



==📌 **Temel Akış**:==

1. `NavController` oluşturulur.
2. `NavHost` içinde ekranlar (`composable`) tanımlanır.
3. `NavController` ile ekranlar arasında geçiş yapılır.


NavHost, uygulamanın navigasyonunu yöneten bir kapsayıcıdır. **NavController** kullanarak belirlenen rotalar arasında geçiş yapılır.

**Adım 1: NavController Oluşturma**

NavController, Compose’un `rememberNavController()` fonksiyonu ile oluşturulur:
```kotlin
val navController = rememberNavController()

```

**Adım 2: NavHost Tanımlama**

NavHost içinde farklı ekranları tanımlarız. Örnek bir yapı:

```kotlin
@Composable
fun AppNavigation() {
    val navController = rememberNavController()
    NavHost(
        navController = navController,
        startDestination = "home"
    ) {
        composable("home") { HomeScreen(navController) }
        composable("detail/{id}") { backStackEntry ->
            DetailScreen(navController, backStackEntry.arguments?.getString("id"))
        }
    }
}

```


**Adım 3: Ekranlar (Composable Fonksiyonlar)**

Örnek olarak **Ana Sayfa** ve **Detay Sayfası** oluşturuyoruz:
```kotlin
@Composable
fun HomeScreen(navController: NavController) {
    Column(
        modifier = Modifier.fillMaxSize(),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        Button(onClick = { navController.navigate("detail/123") }) {
            Text("Detay Sayfasına Git")
        }
    }
}

@Composable
fun DetailScreen(navController: NavController, id: String?) {
    Column(
        modifier = Modifier.fillMaxSize(),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        Text("Detay Sayfası, ID: $id")
        Button(onClick = { navController.popBackStack() }) {
            Text("Geri Dön")
        }
    }
}

```

- Home ekranında bir butona tıklandığında `detail/123` rotasına yönlendirme yapıyoruz.
- `DetailScreen` sayfasında `id` parametresini alıyoruz.
- **popBackStack()** ile geri dönüş yapıyoruz.


==**Geri Dönüş Yöntemleri**==
**1. popBackStack() Kullanımı**

Ekranı kapatıp bir önceki ekrana geri dönmek için:
```kotlin
navController.popBackStack()

```

**2. popBackStack ile belirli bir rotaya kadar temizleme**

Belirli bir sayfaya kadar olan tüm sayfaları geri yığından kaldırmak için:
```kotlin
navController.popBackStack("home", inclusive = false)

```
```Bu kod, `home` ekranına kadar olan tüm ekranları kapatır, ancak `home` ekranını kapatmaz.
```kotlin
navController.popBackStack("home", inclusive = true)

```
Bu kod ise `home` ekranı dahil tüm ekranları kapatır.


**3.navigateUp() Kullanımı**

Önceki ekrana geri dönmek için `navigateUp()` kullanabilirsiniz:
```kotlin
navController.navigateUp()

```


**4.Yeni ekran açarken önceki ekranı kaldırmak (Single Top)**

Aynı ekrandan birden fazla açılmasını engellemek için:
```kotlin
navController.navigate("detail/123") {
    launchSingleTop = true
}

```

Bu kod, `detail/123` ekranı zaten açıksa tekrar açılmasını engeller.

**5.Geri Yığını Temizlemek (Clear BackStack)**

Belirli bir ekran dışında tüm ekranları kaldırmak için:
```kotlin
navController.navigate("home") {
    popUpTo("home") { inclusive = true }
}

```
Bu kod, tüm ekranları kaldırır ve `home` ekranını yeniden başlatır.

**6.backStackEntry Kullanımı*

**backStackEntry**, gezinme yığınının (BackStack) mevcut girişine erişmek için kullanılır. Örneğin, bir ekrana parametre geçerken kullanabiliriz:
```kotlin
composable("detail/{id}") { backStackEntry ->
    DetailScreen(navController, backStackEntry.arguments?.getString("id"))
}

```
Burada `{id}` parametresini alıyoruz ve `backStackEntry.arguments?.getString("id")` ile değeri çekiyoruz.


==**BackStackEntry vs NavOptions Karşılaştırması**==

|**Özellik**|**backStackEntry**|**NavOptions**|
|---|---|---|
|Parametre alma|✅|❌|
|Geçmişi temizleme|❌|✅|
|Yeni ekran açma|✅|✅|
|Yığından silme|❌|✅|

- **`backStackEntry`**, bir sayfaya parametre geçerken kullanılır.
- **`NavOptions`**, gezinme davranışını (yığın temizleme, tek ekran açma vb.) belirlemek için kullanılır.