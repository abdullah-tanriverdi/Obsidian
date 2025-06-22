#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin

Image Picker, kullanıcının galerisinden bir resim seçmesini sağlayan mekanizmadır. Jetpack Compose'da doğrudan bir `ImagePicker` bileşeni yoktur. Bunun yerine, Android'in Activity Result API'si ile galeri veya kamera erişimi sağlanır.

==**Temel Image Picker Kullanımı**==
Jetpack Compose'da galeriye erişmek için `ActivityResultLauncher` kullanılır.
```kotlin
@Composable
fun ImagePickerExample() {
    val context = LocalContext.current
    var imageUri by remember { mutableStateOf<Uri?>(null) }

    val pickImageLauncher = rememberLauncherForActivityResult(
        contract = ActivityResultContracts.GetContent()
    ) { uri: Uri? ->
        imageUri = uri
    }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        imageUri?.let {
            Image(
                painter = rememberAsyncImagePainter(it),
                contentDescription = "Seçilen Resim",
                modifier = Modifier.size(200.dp)
            )
        }

        Spacer(modifier = Modifier.height(16.dp))

        Button(onClick = { pickImageLauncher.launch("image/*") }) {
            Text("Resim Seç")
        }
    }
}

```
✅`rememberLauncherForActivityResult` → Galeriden resim seçmek için bir başlatıcı oluşturur.  
✅ `ActivityResultContracts.GetContent()` → Kullanıcının galeriye erişmesini sağlar.  
✅ `imageUri` → Seçilen resmin URI'sini saklar.  
✅ `rememberAsyncImagePainter` → URI kullanarak resmi gösterir.


==**Kamera ile Fotoğraf Çekme**==

Kamera kullanarak anlık fotoğraf çekmek için **ActivityResultContracts.TakePicture()** kullanılır
```kotlin
@Composable
fun CameraCaptureExample() {
    val context = LocalContext.current
    var imageUri by remember { mutableStateOf<Uri?>(null) }

    val file = remember { File(context.cacheDir, "temp_image.jpg") }
    val uri = remember { FileProvider.getUriForFile(context, "${context.packageName}.provider", file) }

    val takePictureLauncher = rememberLauncherForActivityResult(
        contract = ActivityResultContracts.TakePicture()
    ) { success: Boolean ->
        if (success) {
            imageUri = uri
        }
    }

    Column(
        modifier = Modifier.fillMaxSize(),
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        imageUri?.let {
            Image(
                painter = rememberAsyncImagePainter(it),
                contentDescription = "Çekilen Resim",
                modifier = Modifier.size(200.dp)
            )
        }

        Spacer(modifier = Modifier.height(16.dp))

        Button(onClick = { takePictureLauncher.launch(uri) }) {
            Text("Fotoğraf Çek")
        }
    }
}

```

✅ `FileProvider` → Kamera ile çekilen resmin güvenli bir URI'ye kaydedilmesini sağlar.  
✅ `ActivityResultContracts.TakePicture()` → Kamera açarak fotoğraf çekmeyi başlatır.
Manifest dosyanıza aşağıdaki satırı eklemelisiniz
```xml
<provider
    android:name="androidx.core.content.FileProvider"
    android:authorities="${applicationId}.provider"
    android:grantUriPermissions="true"
    android:exported="false">
    <meta-data
        android:name="android.support.FILE_PROVIDER_PATHS"
        android:resource="@xml/file_paths" />
</provider>

```

Ve `res/xml/file_paths.xml` dosyanızı oluşturmalısınız:

```xml
<paths>
    <cache-path name="cache" path="." />
</paths>

```


---

***Abdullah TANRIVERDİ***
