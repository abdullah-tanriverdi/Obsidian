#Yazılım #Firebase 


![[Pasted image 20250203214453.jpg|500]]


Cloud Firestore, Firebase tarafından sağlanan **NoSQL tabanlı, bulut tabanlı bir veritabanıdır**. Gerçek zamanlı veri senkronizasyonu ve offline destek sunarak mobil ve web uygulamaları için ölçeklenebilir bir çözüm sağlar.


==**Firestore’un Temel Özellikleri**==

✅ **Gerçek Zamanlı Senkronizasyon**

- Bir cihazda yapılan değişiklikler **diğer bağlı cihazlara anında yansır**.
- Özellikle sohbet uygulamaları, anlık bildirimler gibi projelerde idealdir.

✅ **Offline Desteği**

- Kullanıcılar internet bağlantısı olmasa bile **verilerini kaydedebilir ve okuyabilir**.
- Bağlantı tekrar sağlandığında veriler otomatik olarak güncellenir.

✅ **Hızlı ve Ölçeklenebilir**

- **NoSQL yapısı** sayesinde büyük miktarda veriyi yönetebilir.
- **Google Cloud altyapısını** kullanarak yüksek trafikli uygulamalarda bile performans sağlar

✅ **Esnek Veri Yapısı**

- Firestore, **koleksiyonlar (collections)** ve **dokümanlar (documents)** yapısını kullanır.
- SQL tabanlı ilişkisel veritabanlarına göre **daha esnek ve ölçeklenebilir** bir yapı sunar.

✅ **Güçlü Sorgulama ve Filtreleme**

- Kullanıcılar verileri belirli **şartlara göre filtreleyebilir** ve sıralayabilir.

✅ **Güvenlik Kuralları**

- Firebase **Security Rules** sayesinde veriye erişim yetkilendirmesi yapılabilir.


==**Firestore Veri Yapısı**==

Firestore, **koleksiyonlar (collections)** ve **dokümanlar (documents)** şeklinde organize edilen bir **NoSQL veritabanıdır**.


**📌 Koleksiyonlar (Collections) ve Dokümanlar (Documents)**
- **Koleksiyonlar (Collections):** İçinde dokümanlar barındıran ana veri kümeleridir.
- **Dokümanlar (Documents):** Koleksiyonlar içinde saklanan ve JSON formatına benzeyen veri nesneleridir.
```scss
Kullanıcılar (Collection)
 ├── Kullanıcı_1 (Document)
 │    ├── Ad: "Ali"
 │    ├── Soyad: "Yılmaz"
 │    ├── Yaş: 25
 │    ├── Siparişler (Subcollection)
 │         ├── Sipariş_1 (Document)
 │         │    ├── Ürün: "Laptop"
 │         │    ├── Fiyat: 15.000 TL
 │         ├── Sipariş_2 (Document)
 │              ├── Ürün: "Telefon"
 │              ├── Fiyat: 10.000 TL
 ├── Kullanıcı_2 (Document)
      ├── Ad: "Zeynep"
      ├── Soyad: "Kaya"

```
- Firestore’da **koleksiyonlar içinde doğrudan başka koleksiyonlar olamaz**.
- Yalnızca **dokümanlar içinde alt koleksiyonlar** oluşturulabilir.

==**Firestore Security Rules (Güvenlik Kuralları)**==
Firestore, verilerin güvenliğini sağlamak için **Firebase Security Rules** sistemini kullanır.
```json
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    
    // Kullanıcılar koleksiyonuna erişim kuralları
    match /Kullanıcılar/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
    
    // Siparişler koleksiyonuna erişim
    match /Kullanıcılar/{userId}/Siparişler/{siparisId} {
      allow read: if request.auth != null;
      allow write: if request.auth.uid == userId;
    }
  }
}

```
- Kullanıcı yalnızca **kendi verilerini okuyabilir ve düzenleyebilir**.
- Kimliği doğrulanmamış kullanıcılar **verilere erişemez**.