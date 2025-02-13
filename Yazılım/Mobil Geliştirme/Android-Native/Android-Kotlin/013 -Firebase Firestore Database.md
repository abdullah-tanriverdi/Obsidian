#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin


![[Pasted image 20250210153015.jpg]]


> [!tip] İPUCU
> Firestore Nedir hakkında bilgi almak için [[002 -Firestore Database]]


==**Firestore’u Android Projesine Ekleme**==

**Adım 1: Firebase SDK’yı Projeye Dahil Etme**

**`build.gradle (Project Level)`** dosyanıza aşağıdaki satırı ekleyin:
```gradle
classpath 'com.google.gms:google-services:4.3.10' // Güncel sürümü kontrol edin

```
**`build.gradle (App Level)`** dosyanıza şunları ekleyin:
```gradle
implementation("com.google.firebase:firebase-firestore-ktx:24.4.1") // Güncel sürümü kontrol edin

```
Ve en altta şu satırı ekleyin:
```gradle
apply plugin: 'com.google.gms.google-services'

```


**Adım 2: Firebase Projesine Bağlanma**

- Firebase Console adresine gidin.
- Yeni bir proje oluşturun veya mevcut projeye Android uygulamanızı ekleyin.
- **GoogleService-Info.json** dosyasını indirip **app** klasörüne ekleyin.

==**Firestore Veri İşlemleri**==

**Firestore Referansı Alma**
Firestore’a erişmek için `FirebaseFirestore` referansı alınır:
```kotlin
val db = FirebaseFirestore.getInstance()
```

**Veri Ekleme (Add Document)**
Bir koleksiyona yeni doküman eklemek için:
```kotlin
val user = hashMapOf(
"name" to "Ali",
"age" to 25
)

db.collection("users")
	.add(user)
	.addOnSuccesListener{ documentReference -> 
	Log.d()
	}
	.addOnFailureListener { e ->
	Log.w() 
	}

```

Belirli bir ID ile eklemek için:
```kotlin
db.collection("users").document("user1").set(user)
```


==**Veri Okuma (Get Document)**==
```kotlin
db.collection("users").document("user1").get()
    .addOnSuccessListener { documentSnapshot ->
        if (documentSnapshot.exists()) {
            val name = documentSnapshot.getString("name")
            val age = documentSnapshot.getLong("age")
            Log.d("Firestore", "Kullanıcı: $name, Yaş: $age")
        } else {
            Log.d("Firestore", "Doküman bulunamadı")
        }
    }
```

==**Tüm Koleksiyonu Okuma**==
```kotlin
db.collection("users").get()
    .addOnSuccessListener { documents ->
        for (document in documents) {
            Log.d("Firestore", "Veri: ${document.data}")
        }
    }
```


==**Veri Güncelleme (Update Document)**==
```kotlin
db.collection("users").document("user1")
    .update("age", 26)
    .addOnSuccessListener {
        Log.d("Firestore", "Güncellendi")
    }
    .addOnFailureListener { e ->
        Log.w("Firestore", "Hata", e)
    }
```


==**Veri Silme (Delete Document)**==
```kotlin
db.collection("users").document("user1")
    .delete()
    .addOnSuccessListener {
        Log.d("Firestore", "Silindi")
    }
    .addOnFailureListener { e ->
        Log.w("Firestore", "Hata", e)
    }
```


==**Gerçek Zamanlı Veri Dinleme**==
```kotlin
db.collection("users").document("user1")
    .addSnapshotListener { documentSnapshot, e ->
        if (e != null) {
            Log.w("Firestore", "Hata", e)
            return@addSnapshotListener
        }
        if (documentSnapshot != null && documentSnapshot.exists()) {
            Log.d("Firestore", "Güncellenmiş Veri: ${documentSnapshot.data}")
        }
    }
```

==**Firestore ve Offline Kullanım**==
```kotlin
val settings = FirebaseFirestoreSettings.Builder()
    .setPersistenceEnabled(true)
    .build()
db.firestoreSettings = settings
```

Bu ayar sayesinde, internet bağlantısı olmadan da Firestore verileri önbellekten okunabilir.

---


***Abdullah TANRIVERDİ***

