#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin

![[navigatiıon component.png|500]]

Navigation component, Android Jetpack'in bir parçasıdır ve uygulama içinde kullanıcının içerik arasında gezinmesini sağlar. Bu basit buton tıklamalarından karmaşık desenlere kadar birçok farklı navigasyon seneryosunu kapsar. Kullanıcı deneyimini tutarlı ve öngörüllebilir olmasını sağlayarak uygulama içindeki  farklı içeriklere kolay erişim sağlar.

==**Ana Kavramlar**==
- **Host:** Geçerli navigasyon hedefini barındıran UI öğesi (NavHost veya NavHostFragment).
- **Graph:** Uygulamadaki tüm navigasyon hedeflerini ve bunlar arasındaki bağlantıları tanımlayan veri yapısı (NavGraph).
- **Controller:** Hedefler arasında geçiş yapmayı yöneten merkezi koordinatör (NavController).
- **Destination:** Kullanıcının gezindiği ve içeriklerin görüntülendiği hedef noktalar (NavDestination).
- **Route:** Her hedefi benzersiz şekilde tanımlayan ve gerekli veriyi taşıyan yo (Serializable veri türleri).

==**Faydalar ve Özellikler**==
- **Animasyonlar ve geçişler**: Animasyonlar ve geçişler için standartlaştırılmış kaynaklar sunar.
- **Derin bağlantılar (Deep Linking)**: Kullanıcıyı doğrudan belirli bir hedefe yönlendiren bağlantıları yönetir.
- **UI desenleri**: Navigasyon çekmecesi ve alt gezinme gibi desenlere minimal ek iş ile destekler.
- **Tip güvenliği**: Hedefler arasında veri geçişi yaparken tip güvenliği sağlar.
- **ViewModel desteği**: UI ile ilgili verilerin paylaşılabilmesi için ViewModel’leri navigasyon grafiğine göre sınırlar.
- **Fragment işlemleri**: Fragment işlemlerini düzgün bir şekilde yönetir.
- **Back ve Up işlemleri**: Geri ve yukarı işlemlerini varsayılan olarak düzgün yönetir.

==**Kurulum**==
Navigasyon desteği eklemek için, `build.gradle` dosyasına belirli bağımlılıklar eklemeniz gerekir. Bu bağımlılıklar, Compose, Fragment, dinamik özellikler, testler ve JSON serileştirme için gereklidir.
```kotlin
plugins {
  // Kotlin serialization plugin for type safe routes and navigation arguments
  kotlin("plugin.serialization") version "2.0.21"
}

dependencies {
  val nav_version = "2.8.5"

  // Jetpack Compose integration
  implementation("androidx.navigation:navigation-compose:$nav_version")

  // Views/Fragments integration
  implementation("androidx.navigation:navigation-fragment:$nav_version")
  implementation("androidx.navigation:navigation-ui:$nav_version")

  // Feature module support for Fragments
  implementation("androidx.navigation:navigation-dynamic-features-fragment:$nav_version")

  // Testing Navigation
  androidTestImplementation("androidx.navigation:navigation-testing:$nav_version")

  // JSON serialization library, works with the Kotlin serialization plugin
  implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.7.3")
}
```


==**Navigation Controller (NavController)**== 
Navigation bileşeninin ana unsurlarından biridir ve navigasyon grafiğini tutar. Uygulamanın içindeki hedefler arasında geçiş yapmak için kullanılan merkezi API'dir.

**NavController Oluşturma:**

- **Compose** kullanıyorsanız, `rememberNavController()` fonksiyonunu çağırarak bir `NavController` oluşturabilirsiniz. Bu, composable hiyerarşinizin üst seviyelerinde yapılmalıdır, böylece tüm composable'lar gerektiğinde buna erişebilir. Bu, state hoisting prensibini takip eder.
  ```kotlin
  val navController = rememberNavController()

```

-  **Views (Fragment/Activity)** kullanıyorsanız, `NavController`'ı şu yöntemlerle elde edebilirsiniz:

- **Fragment**: `Fragment.findNavController()`
- **View**: `View.findNavController()`
- **Activity**: `Activity.findNavController(viewId: Int)`

Örnek olarak, `NavHostFragment`'ı kullanarak `NavController` alabilirsiniz:
```kotlin
val navHostFragment =
    supportFragmentManager.findFragmentById(R.id.nav_host_fragment) as NavHostFragment
val navController = navHostFragment.navController

```


**Dikkat Edilmesi Gerekenler**:
- Her `NavHost` için bir `NavController` oluşturulmalıdır.
- `NavHostFragment`'ı manuel olarak eklerken veya `FragmentContainerView` kullanırken dikkatli olun; çünkü `NavController`'ı almak `onCreate()` sırasında başarısız olabilir. Bu durumda, doğrudan `NavHostFragment`'tan `NavController` almanız gerekir.

==**Navigation Graph Tasarımı**==
Navigation component, uygulamanızın navigasyonunu yönetmek için bir navigasyon grafiği kullanır. Bu grafik, uygulamanızdaki her bir hedefi ve bu hedefler arasındaki bağlantıları içerir.

**Hedef Türleri**:  
Üç ana hedef türü vardır:
- **Hosted**: Tüm navigasyon hostunu doldurur. Önceki hedefler görünmez. Genellikle ana ve detay ekranları.
- **Dialog**: Önceki hedefler altında overlay olarak görünür. Genellikle uyarılar, seçimler, formlar gibi durumlar için kullanılır.
- **Activity**: Uygulama içindeki ekran veya özellikleri temsil eder. Android aktiviteleriyle etkileşimde bulunmak için kullanılır.

**Navigasyon Grafiğini Oluşturma**: Navigasyon grafiğini oluşturmak için, seçtiğiniz UI framework’üne bağlı olarak farklı yöntemler kullanabilirsiniz.

**Compose**:
- `NavHost` composable’ını kullanarak bir navigasyon grafiği oluşturabilirsiniz. Başlangıç hedefi için bir `route` belirleyebilirsiniz.
- Her hedefi, `composable` lambda içinde tanımlarsınız.
- Eğer hedeflere veri gönderecekseniz, parametreleri içeren sınıflar kullanabilirsiniz.
```kotlin
@Serializable
data class Profile(val name: String)

val navController = rememberNavController()

NavHost(navController = navController, startDestination = Profile(name = "John Smith")) {
    composable<Profile> { backStackEntry ->
        val profile: Profile = backStackEntry.toRoute()
        ProfileScreen(name = profile.name)
    }
}

```



**Fragments**:
- **Programmatically**: Kotlin DSL kullanarak fragment'lar için navigasyon grafiği oluşturabilirsiniz. Bu, modern ve temiz bir yöntemdir.
```kotlin
navController.graph = navController.createGraph(startDestination = Profile(name = "John Smith")) {
    fragment<ProfileFragment, Profile>()
    fragment<FriendsListFragment, FriendsList>()
}

```

- **XML**: XML ile de navigasyon grafiği oluşturabilirsiniz. Bu yaklaşımda, `NavHostFragment` içinde `app:navGraph` kullanılarak grafik bağlanır.
```xml
<navigation xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/nav_graph"
    app:startDestination="@id/profile">
    
    <fragment android:id="@+id/profile" android:name="com.example.ProfileFragment" />
    <fragment android:id="@+id/friendslist" android:name="com.example.FriendsListFragment" />
</navigation>

```


==**Veri Gönderme**==
Verileri hedeflere iletmek için, route'ları veri sınıflarıyla tanımlayabilirsiniz. Bu, hedefe veri geçişini daha güvenli hale getirir.
```kotlin
@Serializable
data class Profile(val nickname: String? = null)

```


==**Örnek**==

```kotlin
@Serializable
data class Profile(val name: String)

@Serializable
object FriendsList

// Define the ProfileScreen composable.
@Composable
fun ProfileScreen(
    profile: Profile
    onNavigateToFriendsList: () -> Unit,
  ) {
  Text("Profile for ${profile.name}")
  Button(onClick = { onNavigateToFriendsList() }) {
    Text("Go to Friends List")
  }
}

// Define the FriendsListScreen composable.
@Composable
fun FriendsListScreen(onNavigateToProfile: () -> Unit) {
  Text("Friends List")
  Button(onClick = { onNavigateToProfile() }) {
    Text("Go to Profile")
  }
}

// Define the MyApp composable, including the `NavController` and `NavHost`.
@Composable
fun MyApp() {
  val navController = rememberNavController()
  NavHost(navController, startDestination = Profile(name = "John Smith")) {
    composable<Profile> { backStackEntry ->
        val profile: Profile = backStackEntry.toRoute()
        ProfileScreen(
            profile = profile,
            onNavigateToFriendsList = {
                navController.navigate(route = FriendsList)
            }
        )
    }
    composable<FriendsList> {
      FriendsListScreen(
        onNavigateToProfile = {
          navController.navigate(
            route = Profile(name = "Aisha Devi")
          )
        }
      )
    }
  }
}
```

Burada iki farklı ekran profile ve friend list arasında geçiş yapılıyor. Her ekran için bir composable fonksiyonu oluşturuluyor ve bu ekranlar arasında veri ve olay iletimi sağlanıyor.

**Veri Sınıfı**
 - **Profile** Kullanıcı adı içeren bir veri sınıfıdır. Bu sınıf, kullanıcı bilgilerini tutmak için kullanılır. Bu sınıfın name adlı bir parametresi var ve @Serializable annotation'ı ile seialize edilebilir.
 - **FriendsList**  Bu bir nesne değil, sadece bir objecct olarak tanımlanmış, yani bu türde route ile ilişkilendirilecekk bir hedefi temsil eder. FriendsList ekranına navigasyon için bir referans olarak kullanılır.
**Composable**
- **ProfileScreen**  fonksiyonu , profil ekranını render eder ve ekrana kullanıcının adını yazdırır. Bu composable, profil bilgilierini profile parametresi ve kullanıcıyı FriendsList ekranına yönlendirecek olan bir onNavigateToFriendsList fonksiyonunu alır. Kullanıcı Go to Friends List butonuna tıkladığında onNavigateToFriendsList çağrılır ve kullanıcı FriendsList ekranına yönlendirilir.
- **FriendsListScreen** arkadaşlar listesi ekranını gösterir. Bu ekran, onNavigateToProfile adlı bir parametre  alır, bu da kullanıcıyı Profile ekranına yönlendiren bir fonksiyondur. Kullancı Go to Profile butonuna tıkladığında onNavigateToProfile çağrılır ve kullanıcı Profile ekranına yönlendirilir.
- **MyApp** Bu composable, navigasyonun yapısının merkezi olan NavController ve NavHost composable içerir. 

==**Dialog Destinations**==
Android Navigation'da, _dialog destination_ terimi, uygulamanın navigasyon grafiği içinde, kullanıcı arayüzüne _dialog_ (yüzen pencere) olarak açılan hedefleri ifade eder. Bu tür bir hedef, mevcut uygulama içeriği ve UI öğelerinin üzerine gelir. 
Dialog destinations, `FloatingWindow` arayüzünü uygular. Bu arayüzü implement eden her hedef, bir dialog destination olarak kabul edilir.
Jetpack Compose'da, dialog destination eklemek için `dialog()` fonksiyonunu kullanırız. Bu fonksiyon, `composable()` fonksiyonu gibi çalışır, ancak bir dialog destination oluşturur.

**Örnek**
- **Home ve Settings**
```kotlin
@Serializable
object Home

@Serializable
object Settings

```

- **Composable Fonksiyonlar**
```kotlin
@Composable
fun HomeScreen(onNavigateToSettings: () -> Unit) {
    Column {
        Text("Home")
        Button(onClick = onNavigateToSettings) {
            Text("Open settings")
        }
    }
}

// Bu ekran dialog olarak gösterilecektir
@Composable
fun SettingsScreen() {
    Text("Settings")
    // ...
}

```

- **NavHost ile Navigasyon Yapısı**
`NavHost`, `Home` ekranını başlangıç hedefi olarak alır. `composable()` fonksiyonu, bu ekranı gezilebilir bir hedef olarak ekler. Ayarlar ekranı ise, `dialog()` fonksiyonu ile dialog destination olarak eklenir. Kullanıcı HomeScreen'den SettingsScreen'e geçerken, SettingsScreen önceki ekranın üzerinde bir dialog olarak gösterilecektir.
```kotlin
@Composable
fun MyApp() {
    val navController = rememberNavController()
    NavHost(navController, startDestination = Home) {
        composable<Home> { HomeScreen(onNavigateToSettings = { navController.navigate(route = Settings) }) }
        dialog<Settings> { SettingsScreen() }
    }
}

```

==**Dialog Destinations Özellikleri**==

- **Dialog Destinations**: `dialog()` fonksiyonu kullanılarak tanımlanan hedefler, önceki ekranın üzerine gelir ve bağımsız bir yaşam döngüsüne ve kaydedilen duruma sahiptir.
- **Kullanım Durumları**: Dialog destinations, uygulamanızda ekranlar arasında yeni bir yaşam döngüsü ve durumu yönetmek gerektiğinde kullanılır. Örneğin, bir ayarlar ekranı veya bilgi mesajları gibi durumlar için uygundur.

**Not:** Eğer daha basit bir dialog (örneğin, onay penceresi) istiyorsanız, `AlertDialog` veya ilgili composables kullanılabilir.

Dialog destinations, uygulamanın navigasyon yapısında overlay (üst katman) olarak açılan hedeflerdir. Jetpack Compose'da, bu tür hedefler `dialog()` fonksiyonu ile eklenir. Bu, kullanıcıya önceden gösterilen ekranın üzerine gelen, bağımsız bir yaşam döngüsüne sahip dialog'lar yaratır. Bu yapıyı, kullanıcı etkileşimlerinde daha büyük bir ekran yerine küçük ve odaklı bilgiler sunmak amacıyla kullanabilirsiniz.


==**Nested Graphs**==
Uygulamanızda belirli bir alt akış (örneğin login akışı, wizardlar veya başka bir işlem akışı) olduğunda, bu alt akışları _nested navigation graphs_ (iç içe geçmiş navigasyon grafikleri) kullanarak daha düzenli ve yönetilebilir hale getirebilirsiniz. Nested graph'lar, uygulamanızın ana akışını daha anlaşılır ve yönetilebilir tutar. Ayrıca, bu yapı sayesinde alt akışların içeriği uygulamanın ana akışından bağımsız olarak değiştirilebilir.
**Önemli Noktalar**
- Nested graph'lar, hem tekrar kullanılabilir hem de encapsulated (kapsüllenmiş) yapılar sağlar.
- Ana akış, nested graph içindeki hedeflere doğrudan erişemez. Bunun yerine, ana akış yalnızca nested graph'a yönlendirebilir.
- Bu yapı, kullanıcıyı ilk başta sadece belirli ekranlara yönlendirmek (örneğin kayıt ekranı) ve sonraki seferlerde farklı bir akışa (örneğin ana oyun ekranı) yönlendirmek için faydalıdır.
  ![[nestedgraphs.png]]
**Örnek**
-  **Hedeflerin Tanımlanması** Uygulamanın başlangıcında kullanıcıyı önce Title" ve "Register" ekranlarına yönlendireceğiz. Daha sonra kullanıcı kaydını tamamladığında, "Game" akışına geçilecek. "Game" akışı da kendi içinde bir nested graph barındıracak.

```kotlin
// Rotalar
@Serializable object Title
@Serializable object Register

// Nested graph için rota
@Serializable object Game

// Nested graph içindeki rotalar
@Serializable object Match
@Serializable object InGame
@Serializable object ResultsWinner
@Serializable object GameOver

```

-  **NavHost Yapısı ve Navigasyon**  Uygulamanın ana ekranında kullanıcıyı önce `Title` ekranına yönlendirecek, ardından `Register` ekranına ve en son olarak `Game` ekranına geçeceğiz. `Game` ekranı kendi içinde bir nested graph içeriyor.
  ```kotlin
  NavHost(navController, startDestination = Title) {
   composable<Title> {
       TitleScreen(
           onPlayClicked = { navController.navigate(route = Register) },
           onLeaderboardsClicked = { /* Leaderboard ekranına git */ }
       )
   }
   composable<Register> {
       RegisterScreen(
           onSignUpComplete = { navController.navigate(route = Game) }
       )
   }
   navigation<Game>(startDestination = Match) {
       composable<Match> {
           MatchScreen(
               onStartGame = { navController.navigate(route = InGame) }
           )
       }
       composable<InGame> {
           InGameScreen(
               onGameWin = { navController.navigate(route = ResultsWinner) },
               onGameLose = { navController.navigate(route = GameOver) }
           )
       }
       composable<ResultsWinner> {
           ResultsWinnerScreen(
               onNextMatchClicked = {
                   navController.navigate(route = Match) {
                       popUpTo(route = Match) { inclusive = true }
                   }
               },
               onLeaderboardsClicked = { /* Leaderboard ekranına git */ }
           )
       }
       composable<GameOver> {
           GameOverScreen(
               onTryAgainClicked = {
                   navController.navigate(route = Match) {
                       popUpTo(route = Match) { inclusive = true }
                   }
               }
           )
       }
   }
}

```
**Açıklamalar:**
- `NavHost`, uygulamanın navigasyon yapısını temsil eder.
- `composable()` fonksiyonu, ekranda bir hedef ekler.
- `navigation()` fonksiyonu, nested graph oluşturur ve içinde başka `composable()` veya `dialog()` fonksiyonlarını çağırır.
- `popUpTo()` fonksiyonu, önceki ekranlardan çıkarken belirli ekranları yığından çıkararak navigasyonu kontrol eder.

- **Direkt Nested Graph Hedeflerine Geçiş** Nested graph içindeki hedeflere geçiş yapmak için global bir rota kullanabilirz.Örneğin Match ekranına doğrudan gitmek için :
```kotlin
navController.navigate(route = Match)

```


==**Deep Links**==
Derin bağlantılar (deep links), kullanıcıyı uygulamanın belirli bir ekranına yönlendiren bağlantılardır. Android'de iki tür derin bağlantı bulunur: **açık (explicit)** ve **belirsiz (implicit)** derin bağlantılar.

- **Açık Derin Bağlantı (Explicit Deep Link)**
Açık derin bağlantı, belirli bir etkinliği veya hedefi belirleyerek, kullanıcıyı doğrudan o ekrana yönlendirir. Örneğin, bir bildirim veya widget ile bu bağlantıyı tetikleyebilirsiniz. Açık derin bağlantılar kullanıldığında, uygulamanın yığınları temizlenir ve yerini derin bağlantı hedefi alır.

`NavDeepLinkBuilder` sınıfını kullanarak bir **PendingIntent** oluşturabilirsiniz:
```kotlin
val pendingIntent = NavDeepLinkBuilder(context)
    .setGraph(R.navigation.nav_graph)
    .setDestination(R.id.android)
    .setArguments(args)
    .createPendingIntent()

```

**Not:** `NavDeepLinkBuilder`, derin bağlantıyı varsayılan başlatıcı etkinliğine yönlendirir. Ancak, başka bir etkinlik kullanılıyorsa, `setComponentName()` ile etkinlik adı belirtilmelidir:

```kotlin
val pendingIntent = NavDeepLinkBuilder(context)
    .setGraph(R.navigation.nav_graph)
    .setDestination(R.id.android)
    .setArguments(args)
    .setComponentName(DestinationActivity::class.java)
    .createPendingIntent()

```
Eğer mevcut bir `NavController` varsa, **createDeepLink()** metodu ile derin bağlantı da oluşturulabilir.
**Not:** Eğer bir ekran kullanıcıdan işlem bekliyorsa (örneğin giriş yapması gerekliyse), bu durumda **Koşullu Navigasyon** kullanılarak kullanıcı derin bağlantı ile geldiğinde yönlendirme yapılabilir.


- **Belirsiz Derin Bağlantı (Implicit Deep Link)**  
Belirsiz derin bağlantılar, URI (Uniform Resource Identifier), intent eylemleri ve MIME türleri gibi parametrelere dayalı olarak belirli bir ekrana yönlendirme yapar. Android, bu bağlantıyı aldığında doğru ekrana yönlendirecek şekilde işlemi yönetir.

- **Manifest Dosyasında Yapılacak İşlemler**

Belirsiz derin bağlantıları etkinleştirmek için, uygulamanızın **AndroidManifest.xml** dosyasına `<nav-graph>` öğesi eklenmelidir:
```kotlin
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapplication">
    <application ... >
        <activity name=".MainActivity" ...>
            ...
            <nav-graph android:value="@navigation/nav_graph" />
            ...
        </activity>
    </application>
</manifest>

```
Bu adımla birlikte, Navigation bileşeni derin bağlantıları otomatik olarak işleyerek, belirttiğiniz hedeflere yönlendirme yapar.


- **Derin Bağlantı Yönlendirme ve Geri Dönüş Davranışı**
Derin bağlantılar kullanıldığında, `Intent.FLAG_ACTIVITY_NEW_TASK` bayrağının kullanımı önemli bir fark yaratır:

- **Bayrak Ayarlandığında:** Geri yığın temizlenir ve derin bağlantı hedefi açılır.
- **Bayrak Ayarlanmadığında:** Kullanıcı, önceki uygulamaya geri döner. Geri düğmesine basıldığında önceki uygulamaya geçilir, ancak **Up Düğmesi** ile ana hedefinize yönlendirilirsiniz.
  
- **Derin Bağlantı Yönetimi**
Navigation bileşeni, derin bağlantıları işlemek için **handleDeepLink()** metodunu kullanır. Ancak, etkinlik yeniden kullanılıyorsa (örneğin `singleTop` modunda), `onNewIntent()` içinde bu metodu manuel olarak çağırmalısınız:
```kotlin
override fun onNewIntent(intent: Intent?) {
    super.onNewIntent(intent)
    navController.handleDeepLink(intent)
}

```

==**Yeni Hedef Türlerine Destek Eklemek**==
Yeni hedef türleri eklemek için **NavController**'a özel **Navigator** sınıfları eklemeniz gerekir.

- **Yeni Navigator Eklemek:** Yeni bir **Navigator** sınıfı eklemek için **getNavigatorProvider()** metodunu kullanarak **NavController**'a erişin.
  ```kotlin
  val customNavigator = CustomNavigator()
navController.navigatorProvider += customNavigator

```
-  **Destination Sınıfı:** Çoğu **Navigator** sınıfı, ilgili hedefin özelliklerini belirten bir **Destination** sınıfına sahiptir. Bu sınıf, hedefe özgü parametreleri tanımlar.


==**Navigasyonu Seçeneklerle Yapma**==
Android Navigation bileşeni, hedeflere geçiş yaparken farklı **navigasyon seçenekleri** sunar. Bu seçenekler, geçişlerin nasıl yapılacağı, animasyonların nasıl çalışacağı, geri yığın davranışı gibi özellikleri içerir.

**NavOptions** sınıfı, bu özel seçenekleri tanımlar. Özellikle, animasyonlar, pop davranışları ve tekli modda (single top mode) açılma gibi seçenekler bu sınıf ile yapılandırılabilir.
Navigation Compose kullanırken, **navigate()** fonksiyonuna ek parametreler geçirerek navigasyon davranışını özelleştirebilirsiniz. Bu ek parametreler, animasyonlar, geçiş yöneticileri ve geri yığın davranışları gibi özellikleri içerir.

**NavOptions** oluşturmak için basit bir lambda fonksiyonu kullanabilirsiniz. İşte temel bir örnek:
```kotlin
navController.navigate(route = FriendsList, navOptions = navOptions {
    // Animasyon ayarları
    anim {
        enter = android.R.anim.fade_in
        exit = android.R.anim.fade_out
    }
    // Geri yığınını temizleme ayarları
    popUpTo(Profile) {
        inclusive = true // Profile ekranını geri yığınından kaldır
    }
    // Aynı hedefe tekrar gidilmesini engelle
    launchSingleTop = true
})


```
Burada, **enter** ve **exit** animasyonları **NavOptions** ile yapılandırılmıştır. **navigate()** fonksiyonuna geçiş için gerekli diğer parametreler eklenebilir. `navigate()` fonksiyonu `route` ile hedef ekranı belirtirken, `navOptions` parametresiyle geçiş ayarlarını ekliyoruz.

==**Navigation ve Back Stack**==
- **NavController**, kullanıcının ziyaret ettiği ekranları içeren bir "geri yığın" (back stack) tutar. Kullanıcı uygulama içinde gezinirken, **NavController** yeni ekranları yığına ekler ve eski ekranları çıkarır.
- Geri yığın, **LIFO** (Last In, First Out) veri yapısını takip eder. Yani, en son ziyaret edilen ekran en üstte bulunur ve kullanıcı geri gitmek için en üstteki öğeyi çıkarır.

**Geri Yığının Temel Davranışı**

1. **İlk Ekran**: Uygulama açıldığında, ilk ekran geri yığına eklenir.
2. **Yığına Ekleme**: `NavController.navigate()` her çağrıldığında yeni bir ekran geri yığına eklenir.
3. **Üst Ekranı Çıkarma**: Kullanıcılar **Up** veya **Back** eylemleriyle geri gider:
    - `navigateUp()` kullanıcıyı bir adım yukarı taşır.
    - `popBackStack()` üstteki ekranı geri yığından çıkarır.



**Belirli Bir Ekrana Geri Dönme (Pop Back to Specific Destination)**

- `popBackStack()` ile, bir ekrana geri dönmek için parametre olarak bir hedef verebilirsiniz. Bu işlem, hedefe kadar olan tüm ekranları yığından çıkarır.
```kotlin
navController.popBackStack(R.id.destinationId, true)

```
Burada, `destinationId` ile belirtilen ekrana geri dönülür ve `inclusive` parametresi true ise, bu hedef de yığından çıkarılır.

**Başarısız Pop Durumlarını Yönetme** 
- `popBackStack()` false dönerse, bu durum yığının boş olduğunu gösterebilir. Bu durumda, uygulama boş bir ekran gösterir.
- Bu durumda, yeni bir hedefe yönlendirme yapmanız veya `finish()` metodunu çağırarak aktiviteyi sonlandırmanız gerekir.

**Pop Up to Belirli Bir Hedefe**
- `popUpTo()` ile, bir ekrandan diğerine geçerken yığındaki bazı ekranları çıkarabilirsiniz. Bu işlem, geçiş yapmadan önce belirttiğiniz hedefe kadar olan ekranları çıkarır.
- `inclusive` parametresi ile, hedef ekranın kendisini de yığından çıkarabilirsiniz.

**Durumları Saklayarak Pop Up Yapma (Save State on Pop Up)**
- `popUpTo()` ile ekranlar arasında geçiş yaparken, yığındaki çıkarılan ekranların durumlarını saklayabilirsiniz. Bu sayede, ilerleyen zamanlarda aynı hedefe döndüğünüzde, o ekranın durumu geri yüklenebilir.
- Bunu sağlamak için `saveState = true` ve `restoreState = true` parametrelerini kullanabilirsiniz.
```kotlin
navController.navigate(route = "B") {
    popUpTo("A") {
        inclusive = true
        saveState = true
    }
    restoreState = true
}

```

==**Dialog Destinations**==

**Genel Bakış**
- Dialog hedefleri, yalnızca geri yığının en üstünde bulunabilir. Çünkü, kullanıcı bir dialog hedefi olmayan bir hedefe navigasyon yaptığında, **NavController** otomatik olarak tüm dialog hedeflerini geri yığından çıkarır. Bu, mevcut ekranın diğer ekranların üstünde tam olarak görünmesini sağlar.
- Hedefler, ya **hosted destination** (konuk hedef), **activity destination** (aktivite hedefi) ya da **dialog destination** (dialog hedefi) olabilir.


**Dialog Hedeflerinin Özellikleri**
- **Dialog hedefleri**, **FloatingWindow** arayüzünü uygular. Bu, dialog hedeflerinin diğer hedeflerin üstünde bir katman olarak görünmesini sağlar.

**Örnek**

Geri yığın sadece hosted destination'lardan oluşuyor ve kullanıcı bir dialog hedefine navigasyon yapıyor. Yığın şu şekilde görünebilir:

- Dialog hedefi, yığının en üstünde görünür.

![[Pasted image 20241217225351.png]]


Kullanıcı başka bir dialog hedefine navigasyon yaparsa, bu yeni dialog hedefi en üstteki yığına eklenir.


![[Pasted image 20241217225359.png]]

Kullanıcı bir non-floating hedefe navigasyon yaparsa, öncelikle tüm dialog hedefleri geri yığından çıkarılır ve yeni hedefe geçilir.

![[Pasted image 20241217225403.png]]
Bu şekilde, dialog hedefleri her zaman yığının en üstünde yer alır ve başka bir hedefe geçiş yapılırken yığındaki diğer dialog hedefleri otomatik olarak çıkarılır.


==**Circular Navigation**==

**Senaryo**

- Uygulamanızda üç hedef (destination) olduğunu düşünelim: **A**, **B** ve **C**.
- **A → B**, **B → C**, ve **C → A** yönünde bir navigasyon akışı var.
- Bu yapı dairesel bir navigasyon oluşturur.

**Problem:**

- Her navigasyon işlemi, **NavController** tarafından yeni bir hedefi geri yığına (back stack) ekler.
- Eğer bu akış tekrarlanırsa, geri yığının içeriği şu şekilde olur:  
    `A → B → C → A → B → C → A → B → C`
- Bu durum, aynı hedeflerin tekrar tekrar yığına eklenmesine neden olur.

![[Pasted image 20241217230006.png]]

**Çözüm**

- Geri yığında tekrarı önlemek için **popUpTo()** ve **inclusive = true** kullanarak önceki hedefleri temizlemelisiniz.
- **popUpTo()**: Belirtilen hedefe kadar geri yığındaki hedefleri temizler.
- **inclusive = true**: Belirtilen hedefi de geri yığından çıkarır.


**Çözüm Senaryosu:**

- Örneğin, **C** hedefindeyken **A**'ya dönmek istiyorsunuz.
- **popUpTo("a")** ve **inclusive = true** kullanırsanız, **B**, **C** ve önceki **A** geri yığından kaldırılır.
- Böylece yığın temizlenir ve yalnızca yeni **A** hedefi yığına eklenir.

```kotlin
// NavGraph tanımlarken NavHost içinde
composable("c") {
    DestinationC(
        onNavigateToA = {
            navController.navigate("a") {
                popUpTo("a") { 
                    inclusive = true 
                }
            }
        }
    )
}

```


**Jetpack Navigation Component**, modern Android uygulamaları için güçlü, esnek ve modüler bir navigasyon çözümü sunar.

***

***Abdullah TANRIVERDİ***
