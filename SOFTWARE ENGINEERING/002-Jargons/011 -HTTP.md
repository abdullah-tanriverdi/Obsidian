#Yazılım #Yazılım-Jargon 

![[HTTP1.jpg]]

HTTP (HyperText Transfer Protocol), web üzerinde veri iletimi için kullanılan bir protokoldür. İnternet üzerinde tarayıcılar ile sunucular arasında veri alışverişini sağlayan temel iletişim protokolüdür. HTTP, istemci (tarayıcı) ve sunucu arasındaki istek ve yanıtları belirleyen kurallar bütünüdür.


- **İstemci**: HTTP isteklerini gönderen yazılım (genellikle bir web tarayıcısı).
    
- **Sunucu**: HTTP isteklerine yanıt veren ve istemciye veriyi gönderen yazılım veya donanım.



**HTTP İstekleri (Requests)**
Bir HTTP isteği, istemcinin sunucuya gönderdiği mesajdır. HTTP isteği şu bileşenlerden oluşur:

- **Metod**: İsteğin amacını belirtir (GET, POST, PUT, DELETE, vb.).
    
- **URL (Uniform Resource Locator)**: İsteğin yapılacağı adresi belirtir.
    
- **Başlıklar (Headers)**: Ekstra bilgiler içerir (örneğin, tarayıcı bilgileri, dil tercihi, vb.).
    
- **Body**: (Opsiyonel) İsteğin içeriğini taşıyan kısmı, genellikle POST ve PUT isteğinde bulunur.
```pgsql
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0

```

**HTTP Yanıtları (Responses)**
Sunucudan istemciye dönen yanıttır ve şu bileşenlerden oluşur:

- **Durum Kodu**: İsteğin sonucunu belirtir (örneğin, 200 OK, 404 Not Found).
    
- **Başlıklar**: Yanıt hakkında bilgiler içerir (örneğin, içerik tipi, içerik uzunluğu, vb.).
    
- **Body**: Yanıtın içeriği, genellikle HTML, JSON veya diğer veri formatlarında olur.

```php-template
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1024

<html>
  <body>
    <h1>Welcome to Example</h1>
  </body>
</html>

```


**HTTP Yöntemleri (Methods)**
HTTP protokolü farklı işlemler için çeşitli yöntemler sunar. En yaygın yöntemler:

- **GET**: Sunucudan veri talep eder (veri alır).
    
- **POST**: Sunucuya veri gönderir (yeni veri oluşturur).
    
- **PUT**: Mevcut veriyi günceller.
    
- **DELETE**: Sunucudan veri siler.
    
- **HEAD**: GET ile aynı ancak yanıt body’sizdir (başlık bilgisi alır).
    
- **OPTIONS**: Sunucunun desteklediği HTTP yöntemlerini sorgular.


**HTTP Durum Kodları**
Durum kodları, HTTP yanıtlarında istemciye sunucu tarafından gönderilen cevapları temsil eder. Yaygın durum kodları:

- **200 OK**: İstek başarıyla tamamlandı.
    
- **201 Created**: Yeni bir kaynak başarıyla oluşturuldu.
    
- **204 No Content**: Yanıt yok (başarılı işlem).
    
- **400 Bad Request**: Hatalı istek.
    
- **401 Unauthorized**: Kimlik doğrulama gerekli.
    
- **404 Not Found**: İstenilen kaynak bulunamadı.
    
- **500 Internal Server Error**: Sunucu hatası.



**HTTP Başlıkları (Headers)**

HTTP başlıkları, istek veya yanıtla ilgili ek bilgileri içerir. İki ana türü vardır:

- **İstek Başlıkları (Request Headers)**: İstemci hakkında bilgi verir (örneğin, `User-Agent`, `Accept`, `Authorization`).
    
- **Yanıt Başlıkları (Response Headers)**: Sunucu hakkında bilgi verir (örneğin, `Content-Type`, `Cache-Control`, `Set-Cookie`).

```makefile
User-Agent: Mozilla/5.0
Accept-Language: en-US
Authorization: Bearer <token>

```

**HTTP ve HTTPS**

- **HTTP** (HyperText Transfer Protocol), güvenliksiz bir protokoldür, veriler şifrelenmeden iletilir.
    
- **HTTPS** (HTTP Secure), şifreli bir iletişim protokolüdür. HTTPS, SSL/TLS şifreleme kullanarak verilerin güvenli bir şekilde iletilmesini sağlar.


**Cookies ve Session**

- **Cookies**: Kullanıcı tarayıcısında saklanan küçük veri parçalarıdır. HTTP istekleri ile sunucuya gönderilebilir.
    
- **Session**: Kullanıcıyla ilgili sunucuda saklanan bilgi. Genellikle kullanıcı oturumlarını yönetmek için kullanılır.



<iframe width="560" height="315" src="https://www.youtube.com/embed/g761Pml_kEU?start=180" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---
***Abdullah TANRIVERDİ***

