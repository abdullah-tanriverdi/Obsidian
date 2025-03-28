#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 


![[FirebaseLoginArchitecture.png]]

Kullanıcıların e-posta ve parola ile kayıt olabilmesi için Firebase Authentication hizmetini kullanıyorum.


> [!tip] İPUCU
> Firebase Auth hakkında daha fazla bilgi almak için bağlantıya tıkla [[004 -Authentication]]



<br>

- ==**Firebase Projesi Oluşturma**==

**Firebase Console’a Giriş Yapma**: Firebase Console adresine gidiyoruz.

**Yeni Proje Oluşturma**: Firebase Console ana sayfasında, sağ üst köşede bulunan **"Add Project"** (Proje Ekle) butonuna tıklıyoruz. Ardından, karşımıza çıkan adımları takip ederek yeni bir proje oluşturuyoruz. Proje adı ve diğer gerekli bilgileri girerek işlemi tamamlıyoruz.
    
**Firebase Projesinin Hazırlanması**: Projemiz oluşturulduktan sonra, Firebase Console'da yeni projemiz aktif hale gelecektir.
    
**Firebase Authentication Özelliğini Aktif Hale Getirme**: Projemiz hazır olduktan sonra, sol menüde yer alan **Authentication** sekmesine tıklıyoruz. Ardından, **"Get Started"** (Başlayın) butonuna tıklayarak Authentication özelliğini aktifleştiriyoruz.
<br>




- ==**Android Studio Projesini Firebase Projesine Bağlama**==
**Firebase Sekmesine Tıklama**: Android Studio içinde, üst menüde bulunan **Firebase** sekmesine tıklıyoruz.
    
 **Authentication Sekmesine Erişim**: Sol menüde yer alan **Authentication** sekmesine tıklıyoruz. Bu, Firebase Authentication hizmetini proje ile entegre etmek için gerekli ayarları yapmamıza olanak sağlar.
    
 **Custom Authentication Sistemi Seçimi**: Authentication sekmesinin altında bulunan alt seçeneklerden **Authenticate using a custom authentication system** kısmına tıklıyoruz.
    
 **Firebase’e Bağlanma**: Karşımıza çıkan pencerede, **Connect to Firebase** butonuna tıklıyoruz. Bu adım, Android Studio projemizi Firebase projemize bağlamamıza olanak tanır.
    
 **SDK’yı Projeye Ekleme**: Firebase ile bağlantı kurduktan sonra, **Add the Firebase Authentication SDK to your project** seçeneğini tıklıyoruz. Bu, gerekli Firebase Authentication bağımlılıklarını projemize ekleyecektir.
    
 **Değişiklikleri Kabul Etme**: Bağımlılıkları ekledikten sonra, **Accept Changes** seçeneğine tıklayarak, gerekli yapılandırma ve dosya değişikliklerini onaylıyoruz.
    
 **Firebase Console’a Giriş**: Firebase Console’a gidiyoruz ve proje üzerinde çalışmaya devam ediyoruz.
    
 **Authentication Ayarlarını Yapma**: Firebase Console’da, sol menüden **Authentication** sekmesine tıklıyoruz ve ardından **Sign-in method** kısmına geliyoruz.
    
 **E-posta ve Şifre ile Giriş Yapmayı Etkinleştirme**: **Sign-in method** altında **Email/Password** seçeneğini aktif hale getiriyoruz. Bu sayede kullanıcılar, e-posta ve şifre kullanarak uygulamaya giriş yapabilecekler.
<br>
- ==**Firebase Dependencies**==
```Gradle
// Module (app) build.gradle dosyasına ekleyin
dependencies {
    implementation 'com.google.firebase:firebase-auth-ktx:22.0.0'
}
```

==**Firebase'i Başlatma**==
```kotlin
import com.google.firebase.auth.FirebaseAuth

val auth: FirebaseAuth = FirebaseAuth.getInstance()
```



- ==**Firebase Authentication Yapılandırması**==

Firebase Authentication’a bağlanmak için `AuthViewModel` sınıfını oluşturuyorum. Bu sınıf, kullanıcıların kayıt olma, giriş yapma ve şifre sıfırlama işlemlerini yönetiyor.
```kotlin
//authviewmodel sınıfımdan örnek bir fonksiyon
fun registerUser(email: String, password: String) {
    auth.createUserWithEmailAndPassword(email, password)
        .addOnCompleteListener { task ->
            if (task.isSuccessful) {
                val user = auth.currentUser
                user?.sendEmailVerification()
                _authState.value = AuthState.Success
            } else {
                _authState.value = AuthState.Error(task.exception?.message ?: "Registration failed")
            }
        }
}

```

==**Google İle Giriş**==
```kotlin
fun signInWithGoogle(credential: AuthCredential, onSuccess: () -> Unit, onError: (String) -> Unit) {
    auth.signInWithCredential(credential)
        .addOnCompleteListener { task ->
            if (task.isSuccessful) {
                onSuccess()
            } else {
                onError(task.exception?.message ?: "Google ile giriş başarısız")
            }
        }
}
```

<br>


- ==**Firebase AuthState Sınıfı Oluşturulması**==
Kullanıcı işlemleri sırasında farklı durumları kontrol etmek için bir `AuthState` sınıfı tanımlayın. Bu sınıf, işlem sırasında başarılı, hata veya yükleniyor durumlarını yönetir.
```kotlin
sealed class AuthState {
    object Idle : AuthState()
    object Loading : AuthState()
    data class Success(val message: String) : AuthState()
    data class Error(val message: String?) : AuthState()
}

```
<br>

- ==**Gerekli Ekran Tasarımları Ve Fonksiyonların Kullanımı**==
Kullanıcı kaydını ve giriş işlemlerini yapmak için örnek bir ekran yapısı kullanabilirsiniz. Kullanıcıdan e-posta ve şifre alarak Firebase Authentication API'sini çağırın.

```kotlin
@Composable
fun RegisterPage(authViewModel: AuthViewModel, navController: NavController) {
    var email by remember { mutableStateOf("") }
    var password by remember { mutableStateOf("") }
    val authState by authViewModel.authState.observeAsState()

    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(32.dp)
    ) {
        Text("Kayıt Ol", fontSize = 36.sp)
        OutlinedTextField(
            value = email,
            onValueChange = { email = it },
            label = { Text("E-Posta") },
            modifier = Modifier.fillMaxWidth()
        )
        OutlinedTextField(
            value = password,
            onValueChange = { password = it },
            label = { Text("Şifre") },
            modifier = Modifier.fillMaxWidth(),
            visualTransformation = PasswordVisualTransformation()
        )
        Button(
            onClick = { authViewModel.registerUser(email, password) },
            enabled = email.isNotEmpty() && password.isNotEmpty()
        ) {
            Text("Kayıt Ol")
        }
        when (authState) {
            is AuthState.Loading -> CircularProgressIndicator()
            is AuthState.Success -> {
                LaunchedEffect(Unit) {
                    navController.navigate("home")
                }
            }
            is AuthState.Error -> {
                Text("Hata: ${(authState as AuthState.Error).message}")
            }
            else -> {}
        }
    }
}

```

<br>

==**Firebase Authentication'a Bağlantı Testi**==

Firebase Authentication işlevselliğinin doğru çalıştığını test etmek için kayıt ve giriş işlemlerini gerçekleştirdiğinizde, Firebase Console üzerinden kullanıcılarınızın durumu ve işlem sonuçlarını görebilirsiniz.

İşlemler özelliştirilebilir fakat genel taslak bu şekildedir

***

***Abdullah TANRIVERDİ***