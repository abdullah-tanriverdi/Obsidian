#Yazılım #MobilGeliştirme #Android
![[Lifecycle_Android.png]]


Jetpack Android Yaşam Döngüsü (Lifecycle), Android uygulamalarındaki **Activity** ve **Fragment** gibi bileşenlerin yaşam döngülerini yönetmek için kullanılan bir mimaridir. Bu mimari, bileşenlerin belirli yaşam döngüsü durumlarına göre nasıl davranması gerektiğini tanımlar ve uygulamayı daha sağlam, yönetilebilir hale getirir. Jetpack Lifecycle kütüphanesi, bu yönetimi kolaylaştırarak uygulamanın UI bileşenlerini yaşam döngüsüne duyarlı hale getirir.
<br>


==**Android Yaşam Döngüsü Nedir?**==
Android'de her **Activity** ve **Fragment**, belirli yaşam döngüsü olaylarına (lifecycle events) sahiptir. Bu olaylar, kullanıcı etkileşimlerine veya sistem olaylarına göre tetiklenir. Örneğin, bir Activity ilk kez başlatıldığında, duraklatıldığında, yeniden başlatıldığında veya yok edildiğinde farklı yaşam döngüsü olayları devreye girer. Uygulama geliştiricileri bu olayları kullanarak, uygulama bileşenlerinin duruma göre nasıl tepki vermesi gerektiğini kontrol edebilir.

**Temel Yaşam Döngüsü Olayları**
1. **onCreate()**: Activity veya Fragment oluşturulduğunda çağrılır. Bu olayda, UI bileşenleri ve veriler hazırlanır.
2. **onStart()**: Activity veya Fragment ekrana geldiğinde çağrılır ve kullanıcıya görünür hale gelir.
3. **onResume()**: Activity veya Fragment etkileşim için hazır hale geldiğinde çağrılır. Kullanıcı bu durumda uygulama ile doğrudan etkileşim kurabilir.
4. **onPause()**: Activity veya Fragment odak kaybettiğinde (örneğin, başka bir Activity açıldığında) çağrılır. Genellikle uygulamayı geçici olarak durdurmak için kullanılır.
5. **onStop()**: Activity veya Fragment artık kullanıcıya görünmez hale geldiğinde çağrılır.
6. **onDestroy()**: Activity veya Fragment yok edildiğinde, yani yaşam döngüsünün sonuna ulaşıldığında çağrılır. Bellek temizliği bu aşamada yapılır.
<br>

==**Jetpack Lifecycle Kütüphanesi**==
Jetpack **Lifecycle** kütüphanesi, Android yaşam döngüsünün karmaşıklığını yönetmek için geliştirilmiş bir çözümdür. Bu kütüphane, Activity ve Fragment gibi bileşenlerin yaşam döngülerini daha etkin bir şekilde yönetmenize yardımcı olur.

- **LifecycleOwner**: Android'deki `Activity` veya `Fragment` gibi yaşam döngüsüne sahip herhangi bir bileşen, `LifecycleOwner` arayüzünü uygular. Bu, bileşenin yaşam döngüsüne erişmenizi ve onu yönetmenizi sağlar. Jetpack Compose bileşenleri de bu arayüzü destekler.
    
- **LifecycleObserver**: Bu arayüz, bir bileşenin yaşam döngüsüne yanıt vermek için kullanılan bir gözlemci sınıfıdır. Örneğin, bir servis veya veritabanı işlemi, yaşam döngüsündeki belirli olaylara göre (örn. `onStart`, `onStop`) tepki verebilir. `LifecycleObserver`, bu olaylara abone olup yaşam döngüsü değişikliklerine göre tepki verir.

```kotlin
import androidx.lifecycle.Lifecycle
import androidx.lifecycle.LifecycleObserver
import androidx.lifecycle.OnLifecycleEvent

class MyObserver : LifecycleObserver {

    @OnLifecycleEvent(Lifecycle.Event.ON_START)
    fun onStartEvent() {
        // onStart çağrıldığında yapılacak işlemler
        println("Activity/Fragment başladı")
    }

    @OnLifecycleEvent(Lifecycle.Event.ON_STOP)
    fun onStopEvent() {
        // onStop çağrıldığında yapılacak işlemler
        println("Activity/Fragment durduruldu")
    }
}

```
Bu sınıf, bir `LifecycleOwner` tarafından gözlemlendiğinde (örn. bir `Activity` veya `Fragment`), yaşam döngüsü olaylarını dinler ve ona göre işlem yapar.

```kotlin
class MyActivity : AppCompatActivity() {

    private lateinit var myObserver: MyObserver

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // LifecycleObserver'ı oluştur ve yaşam döngüsünü gözlemle
        myObserver = MyObserver()
        lifecycle.addObserver(myObserver)
    }
}

```

Bu örnekte, `MyObserver` yaşam döngüsünü gözlemliyor ve `onStart()` ile `onStop()` gibi olayları yakalıyor.
<br>

==**LifecycleScope ve ViewModel ile Entegrasyon**==
Jetpack Lifecycle kütüphanesi, `ViewModel` ve `LiveData` gibi diğer Jetpack bileşenleri ile sıkı bir entegrasyon içindedir. `LifecycleScope`, yaşam döngüsüne duyarlı işlemleri yönetmemize yardımcı olur.

**LifecycleScope**: Coroutine'leri yaşam döngüsüne duyarlı hale getirir. Örneğin, bir coroutine yalnızca Activity etkin olduğu sürece çalışır ve durdurulduğunda otomatik olarak iptal edilir. Bu, bellek sızıntılarını önlemeye yardımcı olur.
```kotlin
import androidx.lifecycle.lifecycleScope
import kotlinx.coroutines.launch

class MyActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // LifecycleScope içinde bir coroutine başlat
        lifecycleScope.launch {
            // Uzun süreli işlemler burada çalışır
        }
    }
}

```

**ViewModel**: ViewModel, yaşam döngüsüne dayanıklı olacak şekilde veri saklamak ve işlemek için kullanılır. Activity veya Fragment yeniden oluşturulsa bile ViewModel verileri korunur. Lifecycle kütüphanesi, ViewModel'in yaşam döngüsüyle uyumlu olmasını sağlar.


==**Jetpack Lifecycle'ın Avantajları**==
1. **Basit Yaşam Döngüsü Yönetimi**: Jetpack Lifecycle kütüphanesi, yaşam döngüsü olaylarını ve bileşenleri daha yönetilebilir hale getirir.
2. **LifecycleObserver ile Temiz Kod**: Uygulamanın yaşam döngüsüne duyarlı işlemler, temiz ve modüler bir şekilde kodlanabilir.
3. **Memory Leak (Bellek Sızıntısı) Önleme**: Lifecycle kütüphanesi, yaşam döngüsüne uygun olarak işlemleri otomatik olarak durdurarak bellek sızıntılarını önler.
4. **Jetpack Bileşenleri ile Uyum**: `LiveData`, `ViewModel` ve `CoroutineScope` gibi diğer Jetpack bileşenleri ile sıkı bir entegrasyon sağlar, böylece reaktif programlamayı destekler.
***

***Abdullah TANRIVERDİ***