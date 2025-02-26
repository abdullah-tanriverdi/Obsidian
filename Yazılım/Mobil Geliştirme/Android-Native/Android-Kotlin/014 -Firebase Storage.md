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
val storageRef = Firebase.storage.reference

```

**Resim Yükleme Fonksiyonu**
```kotlin
fun uploadImageToFirebase(uri: Uri, onSuccess: (String) -> Unit, onFailure: (Exception) -> Unit) {
    val imageRef = storageRef.child("images/${UUID.randomUUID()}.jpg")
    val uploadTask = imageRef.putFile(uri)

    uploadTask.addOnSuccessListener {
        imageRef.downloadUrl.addOnSuccessListener { uri ->
            onSuccess(uri.toString()) // Resmin URL'sini döndürüyoruz
        }
    }.addOnFailureListener {
        onFailure(it)
    }
}

```


**Jetpack Compose ile Kullanımı**

```kotlin
@Composable
fun UploadImageScreen() {
    var selectedImageUri by remember { mutableStateOf<Uri?>(null) }
    val context = LocalContext.current

    Column(
        modifier = Modifier.fillMaxSize(),
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center
    ) {
        Button(onClick = {
            // Burada galeri veya kamera açılabilir (ActivityResult kullanarak)
        }) {
            Text("Resim Seç")
        }

        Spacer(modifier = Modifier.height(16.dp))

        selectedImageUri?.let { uri ->
            Image(
                painter = rememberAsyncImagePainter(uri),
                contentDescription = "Seçilen Resim",
                modifier = Modifier.size(150.dp)
            )

            Spacer(modifier = Modifier.height(16.dp))

            Button(onClick = {
                uploadImageToFirebase(uri,
                    onSuccess = { downloadUrl ->
                        Toast.makeText(context, "Yükleme Başarılı: $downloadUrl", Toast.LENGTH_SHORT).show()
                    },
                    onFailure = { e ->
                        Toast.makeText(context, "Yükleme Hatası: ${e.message}", Toast.LENGTH_SHORT).show()
                    }
                )
            }) {
                Text("Yükle")
            }
        }
    }
}

```


==**Firebase Storage’dan Dosya İndirme**==

Firebase Storage’a yüklenen bir dosyanın URL’si ile indirme işlemi yapabilirsiniz.
```kotlin
fun downloadImage(url: String, onSuccess: (Bitmap) -> Unit, onFailure: (Exception) -> Unit) {
    val storageRef = Firebase.storage.getReferenceFromUrl(url)

    val ONE_MEGABYTE: Long = 1024 * 1024
    storageRef.getBytes(ONE_MEGABYTE)
        .addOnSuccessListener { bytes ->
            val bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.size)
            onSuccess(bitmap)
        }
        .addOnFailureListener {
            onFailure(it)
        }
}

```

Jetpack Compose'da gösterimi için:
```kotlin
@Composable
fun LoadImageScreen(imageUrl: String) {
    var bitmap by remember { mutableStateOf<Bitmap?>(null) }

    LaunchedEffect(imageUrl) {
        downloadImage(imageUrl,
            onSuccess = { bitmap = it },
            onFailure = { Log.e("Image Load", "Error: ${it.message}") }
        )
    }

    bitmap?.let {
        Image(bitmap = it.asImageBitmap(), contentDescription = "Yüklenen Resim")
    } ?: Text("Resim yükleniyor...")
}

```

Bu tür başka fonksiyonlar edinilinebilinir.

---

***Abdullah TANRIVERDİ***

