#Yazılım #MobilGeliştirme #Android


![[Pasted image 20250109194423.png]]


Retrofit, Android'deki HTTP isteklerini yönetmek için kullanılan popüler bir kütüphanedir. API ile iletişim kurarken, RESTful servisler için JSON verilerini kolayca alabilir ve işleyebilirsiniz. Retrofit, HTTP isteklerini Kotlin'de kolayca yazmanıza olanak sağlar.

==**Bağımlılıklar**==

```gradle
// Retrofit
implementation 'com.squareup.retrofit2:retrofit:2.9.0' implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
// Gson (JSON dönüştürme için)
implementation 'com.google.code.gson:gson:2.8.8'
// OkHttp (istekleri izlemek için)
implementation 'com.squareup.okhttp3:okhttp:4.9.0'
```

==**Retrofit ile API İletişimi**==
Retrofit ile API ile iletişim kurabilmek için önce bir **data model** oluşturmanız gerekir.

**Data Model**
Örnek olarak, JSON'dan veri almak için bir model oluşturacağız:
```kotlin
data class User(
    val id: Int,
    val name: String,
    val username: String,
    val email: String
)

```

**API Interface**
Bir interface oluşturup, API ile yapılacak işlemleri tanımlayın:
```kotlin
import retrofit2.Response
import retrofit2.http.GET

interface ApiService {
    @GET("users") // API endpoint'ini buraya yazın
    suspend fun getUsers(): Response<List<User>>
}

```

**Retrofit Nesnesi Oluşturma**
Retrofit nesnesini oluşturmak için aşağıdaki gibi bir singleton sınıf oluşturabilirsiniz:
```kotlin
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory

object RetrofitInstance {
    private const val BASE_URL = "https://jsonplaceholder.typicode.com/"  // API URL'nizi buraya yazın

    val api: ApiService by lazy {
        Retrofit.Builder()
            .baseUrl(BASE_URL)
            .addConverterFactory(GsonConverterFactory.create())  // JSON'dan Kotlin objesine dönüşüm
            .build()
            .create(ApiService::class.java)
    }
}

```


**Veriyi Çekmek ve Jetpack Compose ile Görüntülemek**
ViewModel kullanarak veri çekebiliriz ve bu veriyi Jetpack Compose ile UI'ye aktarabiliriz.

**ViewModel**
Retrofit'ten veri almak için bir ViewModel sınıfı oluşturuyoruz:


```kotlin
import androidx.lifecycle.ViewModel
import androidx.lifecycle.viewModelScope
import kotlinx.coroutines.launch
import retrofit2.Response

class UserViewModel : ViewModel() {
    private val _users = mutableStateOf<List<User>>(emptyList())
    val users: State<List<User>> = _users

    init {
        fetchUsers()
    }

    private fun fetchUsers() {
        viewModelScope.launch {
            try {
                val response: Response<List<User>> = RetrofitInstance.api.getUsers()
                if (response.isSuccessful) {
                    _users.value = response.body() ?: emptyList()
                }
            } catch (e: Exception) {
                // Hata yönetimi
            }
        }
    }
}

```


**Jetpack Compose UI**
Jetpack Compose kullanarak veriyi UI'da gösterebiliriz:
```kotlin
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.text.BasicText
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.collectAsState
import androidx.compose.runtime.getValue
import androidx.compose.ui.tooling.preview.Preview

@Composable
fun UserListScreen(viewModel: UserViewModel) {
    val users by viewModel.users.collectAsState()

    Column {
        users.forEach { user ->
            Text(text = "Name: ${user.name}")
            Text(text = "Username: ${user.username}")
            Text(text = "Email: ${user.email}")
            Text("-------------")
        }
    }
}

@Preview
@Composable
fun PreviewUserListScreen() {
    UserListScreen(viewModel = UserViewModel())
}

```

```kotlin
import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.lifecycle.viewmodel.compose.viewModel
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            val userViewModel = viewModel<UserViewModel>()
            MaterialTheme {
                Surface {
                    UserListScreen(viewModel = userViewModel)
                }
            }
        }
    }
}

```

[AndroidRetrofit GitHub Reposu]( https://github.com/abdullah-tanriverdi/AndroidRetrofit)

---

***Abdullah TANRIVERDİ***
