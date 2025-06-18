#Yazılım #Yazılım-Jargon 


![[Pasted image 20250530114350.jpg|500]]

**Software Development Life Cycle** bir yazılımın geliştirilmesi sürecinde izlenen sistematik aşamaların tümünü ifade eder. Bu döngü , yazılımın planlamasından başlar geliştirme test etme dağıtım ve bakım süreçleriyle devam eder.

**Amaç:**
- Kaliteli yazılım üretmek
- Proje maliyetini ve zamanını azaltmak
- Müşteri gereksinimlerini en iyi şekilde karşılaşmak 
- Süreçleri standartlaştırmak

**Aşamaları:**
- **Gereksinim Analizi (Requirement Analysis)**  
Proje ile ilgili tüm gereksinimleri toplanır. Paydaşlar ile görüşmeler yapılır. Bu süreçte gereksinim dökümanı(SRS - Software Requirement Specification) çıktı olarak oluşturulur ve fonksiyonel gerekisnimler (sistemin ne yapacağı) ve fonksiyonel olmayan gereksinimler (performans, güvenlik vb.) tespit edilir


- **Sistem Ve Yazılım Tasarımı (System Design)**
Yazılımın nasıl geliştirileceği planlanır. Mimari yapı,veritabanı tasarımı, arayüz ve modül tanımlanır. Donanım ve yazılım gereksinimleri belirlenir. Bu süreçte sistem için diyagramlar oluşturulur


- **Uygulama (Implementation / Coding)**
Programcılar tarafından tasarıma uygun kodlama yapılır. Genellikle modüler yaklaşım benimsenir. Kodlama standartları , versiyon kontrol sistemleri gibi araçlar kullanılır.

- **Test Etme (Testing)**
Amaç yazılımın hatasız çalıştığından emin olmak. Belli başlı test türleri vardır bu test sonuçları dahilinde değerlendirmeler yapılır.

- **Dağıtım (Deployment)** 
Yazılım gerçek kullanıcılar için canlı ortama aktarılır. Bu süreçte DevOps araçları kullanılır.

- **Bakım (Maintenance)** 
Canlı ortamdaki yazılımın izlenmesi ve gerektiğinde güncellenmesi sağlanılınır.

| Model          | Açıklama                                     | Avantaj                     | Dezavantaj                        |
| -------------- | -------------------------------------------- | --------------------------- | --------------------------------- |
| **Waterfall**  | Aşamalar sırasıyla, geriye dönüş yok         | Basit, dokümantasyon yoğun  | Esnek değil, geç geri bildirim    |
| **V-Model**    | Her geliştirme adımına karşılık test adımı   | Kalite odaklı               | Değişikliğe kapalı                |
| **Incerement** | Proje parçalar hâlinde tekrarlı geliştirilir | Hızlı teslim, geri bildirim | Planlama karmaşık                 |
| **Spiral**     | Risk odaklı, döngüsel geliştirme             | Büyük projelerde etkili     | Maliyetli, karmaşık               |
| **Agile**      | Kısa süreli sprintlerle esnek geliştirme     | Müşteri odaklı, adaptif     | Disiplin ve sürekli iletişim şart |

**Bir E-Ticaret Sitesi Projesi Üzerinden SDLC**

1. **Gereksinim:** Ürün listeleme, sepete ekleme, ödeme
    
2. **Tasarım:** Kullanıcı arayüzü, veritabanı (ürün, kullanıcı tablosu)
    
3. **Kodlama:** Backend (Java/Python), frontend (React), veritabanı (MySQL)
    
4. **Test:** Sipariş verme senaryosu otomatik test edilir
    
5. **Dağıtım:** AWS veya Azure sunucusunda yayınlanır
    
6. **Bakım:** Yeni kampanya modülü eklenir


SDLC, yazılım geliştirme sürecinin sistematik bir yapıya oturtulmasını sağlar. Geliştiricilerden analistlere kadar her paydaşın rolü net bir şekilde belirlenmiştir. Doğru model seçimi ve etkin uygulama, yazılım kalitesini ve kullanıcı memnuniyetini doğrudan etkiler.

---
***Abdullah TANRIVERDİ***

