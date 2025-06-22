#Yazılım #MobilGeliştirme #Android-Native #Android-Kotlin 


OkHttp, HTTP istemci kütüphanesidir. Java ve Android projelerinde HTTP isteklerini yönetmek için yaygın olarak kullanılır. OkHttp, bir istemci sunucusuyla veri alışverişi yaparken, bağlantıları yönetmek, zaman aşımı (timeout) ayarlamak, yanıtları almak ve bunları işlemek gibi işlemleri kolaylaştırır.


> [!info] İPUCU
> HTTP hakkında daha fazla bilgi almak için bağlantıya tıkla [[009 -HTTP]]

**OkHttp'yi Projeye Dahil Etme**

OkHttp kütüphanesini projeye dahil etmek için Gradle dosyanıza aşağıdaki bağımlılığı ekleyebilirsiniz:
```gradle
implementation("com.squareup.okhttp3:okhttp:4.9.0")

```

==**OkHttp Temel Kullanımı**==

 **GET İsteği Yapmak**
Bir GET isteği, sunucudan veri almak için kullanılır. OkHttp ile GET isteği yapmanın temel adımları şunlardır:
```kotlin

import okhttp3.OkHttpClient
import okhttp3.Request
import okhttp3.Response

fun getExampleData() {
    val client = OkHttpClient()

    val request = Request.Builder()
        .url("https://api.example.com/data")  // URL belirlenir
        .build()

    // Synchronous (senkron) istek
    try {
        val response: Response = client.newCall(request).execute()
        if (response.isSuccessful) {
            println(response.body?.string())  // Başarılı ise yanıtı yazdır
        } else {
            println("Hata: ${response.code}")
        }
    } catch (e: Exception) {
        e.printStackTrace()
    }
}


```
Bu örnekte, `client.newCall(request).execute()` ile GET isteği yapılır ve yanıt alınır. Yanıtın içeriği `response.body?.string()` ile okunur.



**POST İsteği Yapmak**

POST isteği, genellikle sunucuya veri göndermek için kullanılır. POST isteklerinde, veriyi `RequestBody` olarak ekleyebilirsiniz.
```kotlin

import okhttp3.OkHttpClient
import okhttp3.Request
import okhttp3.RequestBody
import okhttp3.MediaType
import okhttp3.Response

fun postExampleData() {
    val client = OkHttpClient()

    val json = """{"name":"John", "age":30}"""
    val mediaType = MediaType.parse("application/json; charset=utf-8")
    val body = RequestBody.create(mediaType, json)

    val request = Request.Builder()
        .url("https://api.example.com/users")
        .post(body)  // POST isteği gönderilir
        .build()

    try {
        val response: Response = client.newCall(request).execute()
        if (response.isSuccessful) {
            println(response.body?.string())  // Başarılı ise yanıtı yazdır
        } else {
            println("Hata: ${response.code}")
        }
    } catch (e: Exception) {
        e.printStackTrace()
    }
}


```

Bu örnekte, `RequestBody.create()` ile JSON verisi gönderilir ve POST isteği yapılır.



**Zaman Aşımı (Timeout) Ayarlama**
OkHttp, istekler için zaman aşımı süreleri belirlemenizi sağlar. Bu, ağ bağlantılarının çok uzun sürmesi durumunda isteğin iptal edilmesini sağlar.

```kotlin
import okhttp3.OkHttpClient
import java.util.concurrent.TimeUnit

fun setupTimeout() {
    val client = OkHttpClient.Builder()
        .connectTimeout(10, TimeUnit.SECONDS)  // Bağlantı zaman aşımı
        .readTimeout(30, TimeUnit.SECONDS)     // Okuma zaman aşımı
        .writeTimeout(15, TimeUnit.SECONDS)    // Yazma zaman aşımı
        .build()

    val request = Request.Builder()
        .url("https://api.example.com/data")
        .build()

    try {
        val response = client.newCall(request).execute()
        if (response.isSuccessful) {
            println(response.body?.string())
        }
    } catch (e: Exception) {
        e.printStackTrace()
    }
}


```

<iframe width="560" height="315" src="https://www.youtube.com/embed/IOTj29_e7A4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Android OkHttp GitHub Repo](https://github.com/abdullah-tanriverdi/AndroidOkHttp)

--- 

***Abdullah TANRIVERDİ***



