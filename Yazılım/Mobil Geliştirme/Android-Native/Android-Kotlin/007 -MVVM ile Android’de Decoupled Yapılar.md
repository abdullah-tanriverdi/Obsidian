#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin


![[mvvm 1.jpg]]


Android uygulama geliştirmek, sürekli değişen teknolojiler ve kullanıcı ihtiyaçlarıyla birlikte daha dinamik bir hale geliyor. Hızla değişen kullanıcı ihtiyaçları ve büyüyen projeler, geliştiricileri daha sağlam ve esnek yazılım mimarilerine yönlendiriyor. Peki, bu tür zorluklarla başa çıkmak için ne yapabiliriz? Uygulama yapılarımızı daha modüler ve yönetilebilir hale getirmek, hem kodumuzu daha kolay bakım yapılabilir kılar hem de projelerimizin ölçeklenebilirliğini artırır. İşte tam burada **MVVM (Model-View-ViewModel)** devreye giriyor. MVVM, Android uygulamalarındaki bağımsız yapılar sayesinde, kodun daha temiz ve sürdürülebilir olmasını sağlıyor. Bu yazımda, MVVM’nin nasıl çalıştığını ve Android projelerinde decoupled yapılar kurmanın neden önemli olduğunu örneklerle anlatacağım.Keyifli okumalar.

==**Kodlarda Modülerlik Neden Önemli?**==

Proje geliştirme süreci zaman alıcı olabilir ve büyüyen projelerle birlikte işler daha karmaşık hale gelir. Ama işin güzel tarafında biri şu ki kodumuzu modüler hale getirdiğimizde, hem işleri kolaylaştırır hem de projeyi daha sürdürülebilir hale getirebiliriz.

Modüler yapı, uygulamamızın farklı işlevlerini bağımsız parçalara ayırmak demektir. Yani, her bir parçanın (modülün) kendi sorumluluğu vardır ve diğer modüllerden mümkün olduğunca bağımsız çalışır. Bu yaklaşım, kodu daha düzenli ve yönetilebilir kılar.

Diyelim ki bir “Hava Durumu” uygulaması geliştiriyoruz. Bu uygulamanın üç ana bölümü olsun: hava durumu verilerini çekmek, bu veriyi ekranda göstermek ve kullanıcıların favori şehirlerini kaydetmek.

- **Veri Çekme Modülü:** Bu modül sadece hava durumu verilerini alır ve işler.
- **Görünüm Modülü:** Bu modül sadece kullanıcıya verileri gösterir, yani ekranı düzenler.
- **Favori Şehirler Modülü:** Bu modül, kullanıcıların favori şehirlerini kaydeder ve yönetir.

Her bir modül, kendi işini yapar. Hava durumu verisi çekme kısmında bir hata oluştuğunda, sadece veri çekme modülüne odaklanabilirsiniz. Görünüm veya favori şehirler modülleri bundan etkilenmez.

==**MVVM (Model-View-ViewModel) Mimarisi Nedir?**==

MVVM, yazılım uygulamalarındaki işlevselliği düzenlemek için kullanılan bir mimari desen olup, uygulamanın farklı katmanları arasında net bir ayrım yapar. MVVM üç ana bileşene sahiptir: 

![[mvmm life cycle.jpg]]

- **Model:** Uygulamanın veri yapısını ve iş mantığını kapsar. Veriyi saklar, işler ve gerektiğinde dış kaynaklardan alır.
- **View:** Kullanıcı arayüzünü temsil eder. Modelden gelen veriyi görsel olarak sunar ve kullanıcı etkileşimlerini alır, ancak doğrudan iş mantığına müdahale etmez.
- **ViewModel:** View ile Model arasındaki bağlantıyı kurar. Kullanıcı etkileşimlerini işler, iş mantığını yönetir ve View’a veri sağlamak için LiveData, StateFlow gibi yapıları kullanır. Bu katman, uygulamanın iş mantığını dışarıya açmadan, veriyi View ile etkili bir şekilde paylaşmayı sağlar.

==**MVVM Kullanmanın Faydaları**==

- **Görevlerin Ayrılması:** UI ve iş mantığı arasında net bir ayrım sağlar.
- **Test Edilebilirlik:** ViewModel için birim testleri yazmak daha kolaydır.
- **Bakım Kolaylığı:** Kod daha modülerdir ve bakım yapması daha basittir.
- **Yeniden Kullanılabilirlik:** Bileşenler, uygulamanın farklı bölümlerinde yeniden kullanılabilir.

==**MVVM ile Örnek Seneryo**==

Uygulamamızda kullanıcı bilgilerini gösterecek bir ekran tasarlayalım. Bu ekran, kullanıcı adını ve yaşını gösterecek.

- **Model**

Model, uygulamanın veri katmanıdır. Bu örnekte, kullanıcı bilgisini tutacak bir `User` sınıfı oluşturacağız.
 ```kotlin
 dataclass User(val name: String, val age: Int)
```


Model, veriyi temsil eder ve iş mantığını yönetir. Burada, sadece basit bir veri yapısı kullanıyoruz, ancak gerçek hayatta veriyi bir API’den veya veritabanından çekilebilir.

- **ViewModel**

ViewModel, UI ile Model arasındaki bağlantıyı kurar. Kullanıcı bilgisini almak ve UI’ya iletmek için `LiveData` kullanacağız.
```kotlin
class UserViewModel : ViewModel() {  
    private val _user = MutableLiveData<User>()  
    val user: LiveData<User> get() = _user  
  
    fun fetchUserData() {  
        // Simüle edilmiş kullanıcı verisi  
        _user.value = User("Ahmet", 25)  
    }  
}
```


ViewModel, `LiveData` kullanarak kullanıcı bilgisini izler ve günceller. `fetchUserData` fonksiyonu, veriyi alıp `_user` değişkenine atar.

- **View**

View, kullanıcıya veriyi gösteren katmandır. Bu katman, ViewModel’den gelen veriyi gözlemler ve UI’yi günceller.
```kotlin
@Composable  
fun UserScreen(userViewModel: UserViewModel = viewModel()) {  
    // Veriyi gözlemliyoruz  
    val user by userViewModel.user.observeAsState()  
  
    // UI elemanları  
    Column(  
        modifier = Modifier  
            .fillMaxSize()  
            .padding(16.dp),  
        horizontalAlignment = Alignment.CenterHorizontally  
    ) {  
        // Eğer kullanıcı verisi gelmişse, veriyi göster  
        user?.let {  
            Text(text = "Name: ${it.name}", style = MaterialTheme.typography.h6)  
            Text(text = "Age: ${it.age}", style = MaterialTheme.typography.body1)  
        }  
  
        // Veriyi almayı başlatan buton  
        Button(onClick = { userViewModel.fetchUserData() }) {  
            Text("Fetch User Data")  
        }  
    }  
}
```

Bu `Composable` fonksiyon, UI katmanını temsil eder. `observeAsState()` ile ViewModel'deki kullanıcı verisini gözlemliyoruz. Verinin değişmesi durumunda UI anında güncellenir.

Bu örnekle MVVM desenini Jetpack Compose kullanarak uygulamış olduk. Compose, kullanıcı arayüzünü daha basit ve anlaşılır bir şekilde yazmamızı sağlar. Ayrıca, ViewModel’deki veriler değiştiğinde, UI otomatik olarak yenilenir. Böylece uygulamanın kodu daha temiz ve sürdürülebilir olur.

==**ViewModel Yaşam Döngüsü**==

ViewModel’in yaşam döngüsü, bağlı olduğu scope (kapsam) ile doğrudan ilişkilidir. ViewModel, bağlı olduğu **ViewModelStoreOwner** yok olana kadar bellekte kalır.

Bir örnekle açıklayacak olursam, bir aktivite ekran döndüğünde (ekranın dönüşü), sistem her seferinde aktivitenin `onCreate()` metodunu çağırabilir. Bu durumda ViewModel, aktivite yok olana kadar (veya activity sonlandığında) bellekte kalmaya devam eder. Bu yaşam döngüsü, fragment'lar için de aynıdır.
![[mvvm2.jpg]]



Bu görselde, bir aktivitenin durum değişiklikleri gösterilirken, aktivite ile ilişkili ViewModel’in yaşam süresi de yan yana gösterilmektedir. Bu, aktivitelerin temel yaşam döngüsünün yanı sıra, fragment’ların yaşam döngüsüne de benzer şekilde uygulanır.


==**LiveData ve StateFlow**==

**LiveData**, Android uygulamalarında verilerin değiştiğini UI’ya bildiren bir yapıdır. Yani, veriler değiştiğinde UI otomatik olarak yenilenir. Bu, kullanıcı etkileşimi veya veri değişiklikleri sonucu UI’yı sürekli güncellemek için çok kullanışlıdır

```kotlin
// ViewModel  
class UserViewModel : ViewModel() {  
    private val _userName = MutableLiveData<String>()  
    val userName: LiveData<String> get() = _userName  
  
    fun setUserName(name: String) {  
        _userName.value = name  
    }  
}  
  
// UI  
val userName by userViewModel.userName.observeAsState("")  
  
Text(text = "User Name: $userName")
```

Bu örnekte kullanıcı adı değiştikçe `LiveData`, UI'ya bu değişikliği bildirir ve UI otomatik olarak yenilenir.

**StateFlow**, Jetpack Compose gibi yeni yapılarla veri akışını yönetmek için kullanılan bir araçtır. `StateFlow`, UI'nin veri değişikliklerine anında tepki vermesini sağlar. Bu, özellikle sürekli değişen verilere ihtiyaç duyduğumuz durumlar için çok kullanışlıdır.

```kotlin
// ViewModel  
class UserViewModel : ViewModel() {  
    private val _userAge = MutableStateFlow(25)  
    val userAge: StateFlow<Int> get() = _userAge  
  
    fun setUserAge(age: Int) {  
        _userAge.value = age  
    }  
}  
  
// UI  
val userAge by userViewModel.userAge.collectAsState()  
  
Text(text = "User Age: $userAge")
```

Bu örnekte, yaş bilgisi değiştiğinde `StateFlow` otomatik olarak UI'ya bildirir ve UI anında güncellenir. `StateFlow`, verilerin sürekli değiştiği durumlarda çok faydalıdır.

 ==**Özet**==

MVVM mimarisini en yeni araçlarla kullanarak, Android uygulamalarımız için daha temiz ve sürdürülebilir kodlar yazabiliriz. LiveData ve StateFlow gibi araçlarla kodumuzu daha düzenli hale getirebilir ve uygulamamızı test edilmesi kolay, ölçeklenebilir yapabiliriz.
****

***Abdullah TANRIVERDİ***