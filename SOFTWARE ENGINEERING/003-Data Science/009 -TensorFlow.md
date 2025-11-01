#Yazılım  #VeriBilimi 

![[TensorFlow1.jpg|500]]

Google Brain ekibi tarafından geliştirilen açık kaynaklı bir sayısal hesaplama ve makine öğrenimi kütüphanesidir. Temelinde tensör işlemleri yani çok boyutlu diziler üzerinde yapılan matematiksel hesaplamalar ve bu işlemlerin hesap grafiği computational graph üzerinden optimize edillmesi yatar. Amaç yapay zeka modellerini kolayca tanımlamak eğitmek ve dağıtmak. CPU, GPU ve TPU üzerinde çalışabilir.

> [!note] Tensor (Tensör)
> Matematikte, tensör, çok boyutlu verinin simgelenebildiği geometrik bir nesnedir. Skaler denilen yönsüz nicel büyüklükler, vektör denilen yönlü büyüklükler ve matris denilen iki boyutlu nesneler birer tensördür. Tensör, tüm bu nesnelerin genelleştirilmiş halidir ve çok boyutlu veri kümeleri için kullanılır.

| Tür    | Boyut | Örnek                       | Açıklama                |
| :----- | :---- | :-------------------------- | :---------------------- |
| Skaler | 0     | `5`                         | Tek bir sayı            |
| Vektör | 1     | `[1, 2, 3]`                 | Tek boyutlu liste       |
| Matris | 2     | `[[1, 2], [3, 4]]`          | 2 boyutlu tablo         |
| Tensör | 3+    | Görsel, ses, video verileri | Çok boyutlu veri yapısı |

![[TensorFlow2.png]]
```python
import tensorflow as tf
a = tf.constant([[1, 2], [3, 4]])
print(a.shape)  # (2, 2)

```

> [!note] Computational Graph
> Her işlem (toplama, çarpma, vs.) bir node, veriler ise edge olarak modellenir. TensorFlow bu grafiği optimize ederek işlemleri GPU/TPU üzerinde pararel çalıştırır.

**Session (TF 1.x) vs. Eager Execution (TF 2.x)**

* **TensorFlow 1.x — Statik Grafik (Static Graph) Yaklaşımı**
TensorFlow’un eski sürümlerinde (1.x), hesaplamalar önce bir “grafik” olarak tanımlanır, sonra bu grafik bir oturum (Session) içinde çalıştırılırdı. Bu sistem biraz “önce planı çiz, sonra uygula” gibiydi.

```python
import tensorflow as tf

# 1. Adım: Grafiği oluştur
a = tf.constant(2)
b = tf.constant(3)
c = a + b  # henüz hesaplanmadı, sadece grafiğe eklendi

# 2. Adım: Grafiği çalıştır
with tf.Session() as sess:
    result = sess.run(c)
    print(result)  # 5

```
Burada `tf.Session()`, grafiği belleğe yükleyip, belirli nodeları (“düğümleri”) çalıştırır.  
Yani, `a + b` satırı gerçekte toplama yapmaz; sadece bir hesaplama düğümü oluşturur.  
Gerçek işlem `sess.run()` çağrıldığında olur. Değişkenlerin anlık değerlerini görmek kolay değildi.

- **TensorFlow 2.x — Eager Execution (Anında Çalıştırma)**
TF 2.x ile birlikte TensorFlow, Eager Execution modunu varsayılan hale getirdi.  
Bu modda, her satır anında çalıştırılır, tıpkı normal Python kodu gibi.
```python
import tensorflow as tf

a = tf.constant(2)
b = tf.constant(3)
c = a + b
print(c)

```

```go
tf.Tensor(5, shape=(), dtype=int32)

```
- Kod hemen çalışıyor, grafik oluşturmaya gerek yok.
- Her işlem sonucunu direkt görebiliyorsun.
- Python değişkenleriyle birlikte TensorFlow objeleri aynı ortamda davranıyor.

```python
import tensorflow as tf
print(tf.executing_eagerly())  # True

```
`tf.executing_eagerly()` Bu fonksiyon, TensorFlow’un şu anda Eager Execution modunda olup olmadığını söyler.

| **Bileşen**                         | **Açıklama**                                                                                                           |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **TensorFlow Core**                 | Düşük seviyeli API. Tensörlerle (çok boyutlu diziler), grafik yapılarıyla ve matematiksel işlemlerle çalışmayı sağlar. |
| **Keras API**                       | TensorFlow’un yüksek seviyeli, kullanıcı dostu arayüzüdür.                                                             |
| **TensorBoard**                     | Eğitim sürecini, kayıpları, metrikleri ve ağ yapısını görselleştiren araçtır.                                          |
| **TensorFlow Lite (TF Lite)**       | Mobil, IoT ve gömülü cihazlarda çalışabilen optimize edilmiş TensorFlow sürümüdür.                                     |
| **TensorFlow Serving (TF Serving)** | Eğitilmiş modelleri üretim ortamında servis olarak sunmak için altyapı sağlar.                                         |
| **TensorFlow Hub (TF Hub)**         | Önceden eğitilmiş modellerin (pre-trained models) paylaşıldığı kütüphane ve platformdur.                               |

|Kavram|Açıklama|
|:--|:--|
|**Tensor**|Çok boyutlu veri yapısı|
|**Graph**|İşlemlerin düğümlerle gösterimi|
|**Session**|TF 1.x’te grafiği çalıştıran ortam|
|**Eager Execution**|TF 2.x’te anında çalıştırma modu|
|**GradientTape**|Otomatik türev hesaplama sistemi|
|**Keras**|Model kurma arayüzü|
|**TensorBoard**|Eğitim sürecini görselleştirme|
|**TF Lite / TF Serving**|Model dağıtımı araçları|


>TensorFlow, matematiksel işlemleri graf temsiliyle optimize eden,  
 derin öğrenme modellerini kolayca kurmamızı sağlayan güçlü bir platformdur.

***
***Abdullah TANRIVERDİ***
