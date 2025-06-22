#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 

![[Pasted image 20250210161015.png|500]]


> [!tip] İPUCU
> Storage Nedir hakkında bilgi almak için [[003 -Storage]]

Firebase Storage, Google’ın sağladığı bulut tabanlı bir depolama hizmetidir. Android uygulamalarında medya dosyalarını (resim, video, ses) ve diğer dokümanları saklamak için kullanılır

==**Gerekli Bağımlılıklar**==

Firebase Storage'ı Jetpack Compose ile kullanabilmek için `build.gradle` dosyanıza aşağıdaki bağımlılıkları ekleyin:
```gradle
dependencies {
    implementation("com.google.firebase:firebase-storage-ktx:20.2.1")
}

```

==**Firebase Projesi Oluşturma ve Konfigürasyon**==

1. Firebase Console üzerinden yeni bir proje oluşturun.
2. Android Uygulamanızı Firebase’e Ekleyin:
    - Uygulama paketi adınızı girin.
    - `google-services.json` dosyasını indirerek `app/` dizinine ekleyin.
3. Firebase Storage'ı Etkinleştirin:
    - Firebase Console > Build > Storage sekmesine gidin.
    - `Başlat` butonuna tıklayarak Storage’ı etkinleştirin.

==**Storage Kuralları**==

Varsayılan olarak, Firebase Storage kimlik doğrulama gerektirir. Geliştirme aşamasında herkesin dosya yükleyip indirebilmesi için aşağıdaki kuralları geçici olarak kullanabilirsiniz:
```json
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read, write: if true;
    }
  }
}

```


==**Dosya Yükleme**==

Jetpack Compose arayüzü üzerinden bir resmi Firebase Storage’a yüklemek için aşağıdaki adımları takip edebilirsiniz.

**Storage Referansını Oluşturun**
```kotlin
import com.google.firebase.storage.FirebaseStorage

val storage = FirebaseStorage.getInstance()
val storageRef = storage.reference

```


**Resim Yükleme Fonksiyonu**
```kotlin
fun uploadImage(imageUri: Uri, onSuccess: (String) -> Unit, onError: (String) -> Unit) {
    val storageRef = FirebaseStorage.getInstance().reference.child("images/${imageUri.lastPathSegment}")

    storageRef.putFile(imageUri)
        .addOnSuccessListener { taskSnapshot ->
            storageRef.downloadUrl.addOnSuccessListener { uri ->
                onSuccess(uri.toString()) // Resmin URL’sini al
            }
        }
        .addOnFailureListener { e ->
            onError(e.message ?: "Yükleme hatası")
        }
}


```

**Dosya İndirme**
Firebase Storage’daki bir resmi Jetpack Compose ile göstermek için:
```kotlin
fun getDownloadUrl(imageName: String, onSuccess: (String) -> Unit, onError: (String) -> Unit) {
    val storageRef = FirebaseStorage.getInstance().reference.child("images/$imageName")

    storageRef.downloadUrl
        .addOnSuccessListener { uri -> onSuccess(uri.toString()) }
        .addOnFailureListener { e -> onError(e.message ?: "Dosya alınamadı") }
}

```

**Dosya Silme**


```kotlin 
fun deleteFile(imageName: String, onSuccess: () -> Unit, onError: (String) -> Unit) {
    val storageRef = FirebaseStorage.getInstance().reference.child("images/$imageName")

    storageRef.delete()
        .addOnSuccessListener { onSuccess() }
        .addOnFailureListener { e -> onError(e.message ?: "Silme hatası") }
}

```

**Kullanııcıdan Fotoğraf Seçme**
```kotlin
@Composable
fun PickImage(onImagePicked: (Uri) -> Unit) {
    val launcher = rememberLauncherForActivityResult(contract = ActivityResultContracts.GetContent()) { uri: Uri? ->
        uri?.let { onImagePicked(it) }
    }

    Button(onClick = { launcher.launch("image/*") }) {
        Text("Fotoğraf Seç")
    }
}

```


**Jetpack Compose ile Kullanımı**

```kotlin
@Composable
fun UploadImageScreen() {
    var imageUri by remember { mutableStateOf<Uri?>(null) }
    var imageUrl by remember { mutableStateOf<String?>(null) }
    val context = LocalContext.current

    Column(
        modifier = Modifier.fillMaxSize(),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        PickImage { uri -> imageUri = uri }

        imageUri?.let { uri ->
            Button(onClick = {
                uploadImage(uri,
                    onSuccess = { url -> imageUrl = url },
                    onError = { msg -> Toast.makeText(context, msg, Toast.LENGTH_SHORT).show() }
                )
            }) {
                Text("Fotoğraf Yükle")
            }
        }

        imageUrl?.let { url ->
            AsyncImage(
                model = url,
                contentDescription = "Yüklenen Fotoğraf",
                modifier = Modifier.size(200.dp)
            )
        }
    }
}


```

**Coil İle Görsel Yükleme**

```Gradle
dependencies {
    implementation("io.coil-kt:coil-compose:2.4.0")
}

```


```kotlin
@Composable
fun DisplayImageFromStorage(imageName: String) {
    var imageUrl by remember { mutableStateOf<String?>(null) }
    val context = LocalContext.current

    // Resmin URL'sini almak için Firestore'u çağırıyoruz
    LaunchedEffect(imageName) {
        val storageRef = FirebaseStorage.getInstance().reference.child("images/$imageName")
        storageRef.downloadUrl
            .addOnSuccessListener { uri -> imageUrl = uri.toString() }
            .addOnFailureListener { e ->
                Toast.makeText(context, "Hata: ${e.message}", Toast.LENGTH_SHORT).show()
            }
    }

    Column(
        modifier = Modifier.fillMaxSize(),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        if (imageUrl != null) {
            AsyncImage(
                model = imageUrl,
                contentDescription = "Firebase Storage Resmi",
                modifier = Modifier.size(200.dp)
            )
        } else {
            CircularProgressIndicator() // Resim yüklenene kadar gösterilir
        }
    }
}

```
📌 **`LaunchedEffect(imageName)`**: Ekran açıldığında Firebase Storage’dan resmin URL’sini almak için çalıştırılır.  
📌 `AsyncImage(model = imageUrl, ...)`: Coil kullanarak resmi indirip ekranda gösterir.  
📌 `CircularProgressIndicator()`: Resim yüklenirken yükleme göstergesi çıkar.


```kotlin
@Composable
fun ImageScreen() {
    DisplayImageFromStorage(imageName = "example_image.jpg")
}

```


---

***Abdullah TANRIVERDİ***

