#Yazılım #MobilGeliştirme #Android 


![[Pasted image 20241221165501.png|500]]
Android uygulama mimarisi, genellikle üç ana katmandan oluşur: **UI Layer**, **Domain Layer**, ve **Data Layer**. Bu katmanlar, uygulamanın daha düzenli, test edilebilir ve sürdürülebilir olmasını sağlamak için tasarlanmıştır.

==**UI Layer**==

- **Tanım:** Kullanıcı ile etkileşime giren katmandır. Görsel öğeleri ve kullanıcı girdilerini işler.
- **Jetpack Compose ve View desteği:**
    - Jetpack Compose, modern ve deklaratif bir UI araç setidir.
    - XML tabanlı View sistemini tamamıyla destekler.
- **UI Layer’ın Sorumlulukları:**
    - **State Management:** Uygulamanın durumu bu katmanda gösterilir.
    - Kullanıcıdan gelen girdileri alır ve uygun aksiyonları tetikler.
    - Görsel düzenleme ve animasyon işlemleri.

**UI Layer'daki Bileşenler:**

1. **ViewModel:**
    - İş mantığını içermez; sadece UI için gerekli veriyi sağlar.
    - Jetpack **StateFlow** ve **LiveData** gibi yapılarla UI’ya veri sağlar.
    - UI ile veri arasında bir köprü görevi görür.
2. **State:**
    - Uygulamanın mevcut durumu burada yönetilir.
    - Compose için **remember**, **MutableState** gibi kavramlar kullanılır.

**Örnek Kod:**
```kotlin
@Composable
fun MyScreen(viewModel: MyViewModel) {
    val uiState by viewModel.uiState.collectAsState()
    Text(text = uiState.title)
}

```

**Açıklama:**
- **@Composable:** Jetpack Compose’daki bir fonksiyonu tanımlar. Bu, UI öğeleri oluşturmak için kullanılan bir fonksiyondur.
- **MyScreen(viewModel: MyViewModel):**
    - `MyScreen`, UI ekranını temsil eden bir Compose fonksiyonudur.
    - Bir `ViewModel` alır. Bu, UI’ya veri sağlayan bir yapıdır.
- **viewModel.uiState.collectAsState():**
    - `uiState`, ViewModel içinde tanımlı bir durumdur (örneğin `StateFlow` veya `LiveData`).
    - `collectAsState()`, durum değişikliklerini dinler ve UI’nın güncellenmesini sağlar.
- **Text(text = uiState.title):**
    - Kullanıcıya gösterilecek bir `Text` bileşeni.
    - `uiState.title` kısmı, ViewModel’den gelen ve ekranda gösterilecek olan metindir.


==**Domain Layer**==

- **Tanım:** İş kurallarını ve uygulamanın merkezi mantığını barındırır.
- **Opsiyonel bir katman:** Domain layer, büyük projelerde daha fazla anlam kazanır.
- **Sorumlulukları:**
    - **Use Case** (veya Interactors): Belirli bir iş mantığını temsil eden soyut operasyonlardır.
    - **Bağımsızlık:** Domain katmanı platforma özgü kütüphanelerden bağımsızdır.

**Domain Layer'daki Bileşenler:**

1. **Use Cases:**
    - İş kurallarını kapsüller.
    - Data Layer’dan veri alır, iş kurallarını uygular ve UI Layer’a döner.
2. **Entities:**
    - Uygulamanın temel iş nesnelerini tanımlar.
    - Saf Kotlin sınıflarıdır ve bağımsızdır.

```kotlin
class GetUserUseCase(private val userRepository: UserRepository) {
    suspend operator fun invoke(userId: String): User {
        return userRepository.getUser(userId)
    }
}

```

**Açıklama:**

- **GetUserUseCase:**
    - Bir iş kuralını temsil eder. Burada "Belirli bir kullanıcıyı getir" işlemini kapsülleyen bir sınıftır.
- **private val userRepository: UserRepository:**
    - `UserRepository`, veriyle ilgili işlemleri yöneten bir arayüzdür. Bu arayüz, Data Layer ile iletişim kurar.
- **suspend:**
    - Bu fonksiyonun bir **coroutine** içinde çalışabileceğini belirtir. Genellikle asenkron işlemler için kullanılır (örneğin API çağrısı veya veritabanı işlemleri).
- **operator fun invoke(userId: String):**
    - **`invoke`** özel bir Kotlin fonksiyonudur. Sınıfın örneği, bir fonksiyon gibi çağrıldığında çalışmasını sağlar
```kotlin
val user = getUserUseCase("123")

```

**userRepository.getUser(userId):**

- Repository’den belirli bir kullanıcıyı almak için çağrılır.


==**Data Layer**==

- **Tanım:** Uygulamanın veriyi aldığı, sakladığı ve yönettiği katmandır.
- **Sorumlulukları:**
    - Veri kaynaklarını yönetir (API, veritabanı, cache).
    - Veriyi işler ve Domain Layer’a sunar.

**Data Layer'daki Bileşenler:**

1. **Repositories:**
    - Veri kaynaklarından veri toplar ve domain’e sunar.
    - Verinin nereden geldiği ile ilgilenmez; bu detayları saklar.
2. **Data Sources:**
    - Veri kaynaklarını (ör. Remote API, local database) temsil eder.
3. **DTOs (Data Transfer Objects):**
    - Veri taşımak için kullanılan yapılar.
    - Network veya veritabanı katmanından gelen ham veriyi taşır.

```kotlin
interface UserRepository {
    suspend fun getUser(userId: String): User
}

class UserRepositoryImpl(
    private val api: UserApi,
    private val database: UserDatabase
) : UserRepository {
    override suspend fun getUser(userId: String): User {
        val user = api.getUser(userId)
        database.saveUser(user)
        return user
    }
}

```

**Açıklama:**

**1. Arayüz (Interface):**
```kotlin
interface UserRepository {
    suspend fun getUser(userId: String): User
}

```
- **UserRepository:**
    - Data Layer'daki temel veri işlemlerini tanımlar.
    - Soyut bir yapıdır, yani burada işlem detayları belirtilmez. Bu, üst katmanların veri kaynağının detaylarını bilmeden çalışabilmesini sağlar.
- **suspend fun getUser(userId: String): User:**
    - Belirli bir `userId`’ye sahip kullanıcının alınmasını sağlayan bir metot. Coroutine desteği ile asenkron çalışır.


**2. Uygulama (Implementation):**
```kotlin
class UserRepositoryImpl(
    private val api: UserApi,
    private val database: UserDatabase
) : UserRepository {
    ...
}

```

- **UserRepositoryImpl:**
    - `UserRepository` arayüzünün uygulanmış hali. Verinin nasıl alınacağı burada detaylandırılır.
- **private val api: UserApi:**
    - Uzak bir veri kaynağını (örneğin REST API) temsil eder.
- **private val database: UserDatabase:**
    - Yerel bir veri kaynağını (örneğin SQLite veya Room) temsil eder.

**3. Metot Uygulaması:**
```kotlin
override suspend fun getUser(userId: String): User {
    val user = api.getUser(userId)
    database.saveUser(user)
    return user
}

```

- **api.getUser(userId):**
    - API’den belirtilen kullanıcıyı getirir.
- **database.saveUser(user):**
    - Getirilen kullanıcıyı yerel veritabanına kaydeder (örneğin cache işlemi için).
- **return user:**
    - Kullanıcı bilgisi üst katmana döndürülür (Domain Layer).



==**Katmanlar Arası İletişim**==

1. **UI Layer ile Domain Layer:**
    
    - ViewModel, Use Case’leri çağırarak iş kurallarını uygular.
    - StateFlow veya LiveData ile sonuçlar UI’ya iletilir.
2. **Domain Layer ile Data Layer:**
    
    - Domain katmanı, Repository’lerden veri talep eder.
    - Repository, veri kaynaklarını (API, DB) sorgular ve domain’e döner.


==**Örnek Katmanlı Mimaride Akış**==

1. Kullanıcı bir butona tıklar (UI Layer).
2. ViewModel bir Use Case çağırır (Domain Layer).
3. Use Case, Repository’den veri ister (Data Layer).
4. Repository veriyi kaynaktan alır (API veya DB) ve işler.
5. Veri UI’ya döner ve gösterilir.

---

***Abdullah TANRIVERDİ***