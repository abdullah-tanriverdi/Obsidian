#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 

![[Pasted image 20250213034506.png|500]]


==**State (Durum) Nedir?**==

**State (durum)**, kullanıcı arayüzünün bir anlık verisini temsil eder. Örneğin:

- Bir butona basıldığında sayacın artması
- Bir metin giriş kutusunun içeriğinin değişmesi
- Bir API çağrısı sonucunda verilerin güncellenmesi

==**State ve Recompositions**==

Jetpack Compose'ta state değiştiğinde, ilgili composable fonksiyonlar tekrar çalıştırılır (recomposition). Ancak sadece değişen kısımlar yeniden oluşturulur, böylece performans kaybı yaşanmaz.


==**State'i Yönetmenin Temel Yolları**==

**`remember` İle State Yönetimi**

Compose'ta bir bileşen içinde değişken tanımlamak istiyorsanız, bu değişkenin yeniden oluşturulduğunda (recomposition) korunması gerekir. Bunun için `remember` kullanılır.

***Örnek: Sayacın `remember` ile yönetilmesi***
 ```kotlin
 @Composable
fun Counter() {
    var count by remember { mutableStateOf(0) }

    Column(horizontalAlignment = Alignment.CenterHorizontally) {
        Text(text = "Sayaç: $count", fontSize = 24.sp)
        Button(onClick = { count++ }) {
            Text("Artır")
        }
    }
}

```
- `remember { mutableStateOf(0) }`: `count` değişkeni recomposition sırasında korunur.
- Recomposition nedir? UI bileşeni güncellendiğinde tekrar oluşturulması işlemidir.
- Eğer `remember` kullanmazsanız, her recomposition sonrası `count` değeri sıfırlanır.



**`rememberSaveable` İle Ekran Dönmelerine Karşı State Koruma**

Eğer ekran döndüğünde (configuration change) state’in kaybolmasını istemiyorsanız `rememberSaveable` kullanmalısınız.

***Örnek: Ekran dönse bile `count` kaybolmaz***

```kotlin
@Composable
fun CounterWithSaveable() {
    var count by rememberSaveable { mutableStateOf(0) }

    Column(horizontalAlignment = Alignment.CenterHorizontally) {
        Text(text = "Sayaç: $count", fontSize = 24.sp)
        Button(onClick = { count++ }) {
            Text("Artır")
        }
    }
}

```

**Farkı ne?**
- `remember` yalnızca bileşen bellekte olduğu sürece veriyi korur.
- `rememberSaveable` ise ekran döndüğünde bile veriyi saklar.


==**State Hoisting (Durumu Yukarı Taşıma)**==

**State Hoisting**, state’in UI bileşenlerinden bağımsız olarak üst seviyede saklanmasıdır.  
Bu, Composable bileşenleri daha yeniden kullanılabilir ve test edilebilir hale getirir.

***Kötü Örnek (State bileşene gömülü)***
```kotlin
@Composable
fun CounterBadExample() {
    var count by remember { mutableStateOf(0) } // Bileşene gömülü

    Button(onClick = { count++ }) {
        Text("Sayaç: $count")
    }
}

```
**Problem:** Bu bileşeni farklı yerlerde kullanmak zorlaşır çünkü state içine gömülüdür.

***İyi Örnek (State Hoisting kullanarak)***
```kotlin
@Composable
fun Counter(count: Int, onIncrement: () -> Unit) {
    Button(onClick = onIncrement) {
        Text("Sayaç: $count")
    }
}

@Composable
fun CounterScreen() {
    var count by remember { mutableStateOf(0) }

    Column {
        Counter(count = count, onIncrement = { count++ })
    }
}

```
- `Counter` bileşeni artık sadece **UI gösteriyor**, state’i kendisi yönetmiyor.
- **Faydalar:**
    - Aynı `Counter` bileşenini farklı yerlerde tekrar kullanabiliriz.
    - State daha iyi yönetilebilir ve test edilebilir hale gelir.


==**ViewModel Kullanarak State Yönetimi**==

Bileşenler arası state paylaşımını yönetmek için **ViewModel** kullanılır. ViewModel, Compose ile kolayca entegre edilebilir.

**ViewModel Kullanımı**

***Örnek: ViewModel içinde State Yönetimi***
```kotlin
class CounterViewModel : ViewModel() {
    var count by mutableStateOf(0)
        private set

    fun increment() {
        count++
    }
}

```


***ViewModel'in Compose İçinde Kullanımı***
```kotlin
@Composable
fun CounterScreen(viewModel: CounterViewModel = viewModel()) {
    Column {
        Text("Sayaç: ${viewModel.count}", fontSize = 24.sp)
        Button(onClick = { viewModel.increment() }) {
            Text("Artır")
        }
    }
}

```

**Avantajları:** 
✅ ViewModel, Compose dışında da kullanılabilir.  
✅ Ekran döndüğünde bile state kaybolmaz.


==**DerivedStateOf ile Performans Optimizasyonu**==

`derivedStateOf`, state’in gereksiz recomposition işlemlerine neden olmasını engellemek için kullanılır.

```kotlin
@Composable
fun ExpensiveComputationExample() {
    var number by remember { mutableStateOf(0) }
    
    val isEven by remember { derivedStateOf { number % 2 == 0 } }

    Column {
        Text("Sayı: $number")
        Text("Çift mi? $isEven")
        Button(onClick = { number++ }) {
            Text("Artır")
        }
    }
}

```
**Faydası:** `isEven`, sadece `number` değiştiğinde hesaplanır, diğer değişimlerde gereksiz hesaplama yapılmaz.


==**`produceState` ve `rememberCoroutineScope` ile Async State Yönetimi**==

Bazı durumlarda, API çağrıları veya uzun süren işlemler state’i güncellemek için kullanılabilir.

**`produceState` ile API Çağrısı**

`produceState`, arka planda çalışan bir işlemi state ile bağlamak için kullanılır.
```kotlin
@Composable
fun FetchData(): String {
    val data by produceState(initialValue = "Yükleniyor...") {
        delay(2000) // Simüle edilmiş API çağrısı
        value = "Veri yüklendi!"
    }

    return data
}

```


**`rememberCoroutineScope` ile Asenkron İşlemler**

Bazı işlemler butona basıldığında başlatılabilir. Bunun için `rememberCoroutineScope` kullanılır.
```kotlin
@Composable
fun LoadDataButton() {
    val scope = rememberCoroutineScope()
    var text by remember { mutableStateOf("Başlamak için tıkla") }

    Button(onClick = {
        scope.launch {
            text = "Yükleniyor..."
            delay(2000)
            text = "Yükleme tamamlandı!"
        }
    }) {
        Text(text)
    }
}

```


==**UIState ve UIEvent Kullanımı (Unidirectional Data Flow - Tek Yönlü Veri Akışı)**==

Büyük ölçekli uygulamalarda, state yönetimi için `UIState` ve `UIEvent` kullanmak daha iyi bir yaklaşımdır.

**UIState Tanımlama**
```kotlin
data class CounterUiState(val count: Int =0)
```

**ViewModel'de UIState Kullanma**
```kotlin
class CounterViewModel : ViewModel() {
    private val _uiState = mutableStateOf(CounterUiState())
    val uiState: State<CounterUiState> = _uiState

    fun increment() {
        _uiState.value = _uiState.value.copy(count = _uiState.value.count + 1)
    }
}

```

**Composable İçinde Kullanımı**
```kotlin
@Composable
fun CounterScreen(viewModel: CounterViewModel = viewModel()) {
    val uiState by viewModel.uiState

    Column(horizontalAlignment = Alignment.CenterHorizontally) {
        Text(text = "Sayaç: ${uiState.count}", fontSize = 24.sp)
        Button(onClick = { viewModel.increment() }) {
            Text("Arttır")
        }
    }
}

```
Bu yaklaşım, **Tek Yönlü Veri Akışı (Unidirectional Data Flow - UDF)** prensibini uygular ve state yönetimini daha düzenli hale getirir.

- **Küçük uygulamalar** için `remember` ve `rememberSaveable` yeterlidir.
- **Daha büyük uygulamalarda** ViewModel ile state yönetimi tercih edilmelidir.
- **Unidirectional Data Flow (Tek yönlü veri akışı)** kullanımı, ölçeklenebilir ve yönetilebilir bir mimari sunar.

***

***Abdullah TANRIVERDİ***
