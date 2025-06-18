#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 


![[Modifier.png]]

Jetpack Compose'ta **`Modifier`**, UI bileşenlerinin görünümünü ve davranışını düzenlemek için kullanılan bir arayüzdür. Bileşenlerin yerleşim, boyut, tıklanabilirlik, arka plan rengi, şekil ve çok daha fazlasını kontrol etmek için `Modifier`'ı kullanırsınız. `Modifier`, Compose bileşenlerine stil eklemenin ve etkileşimli özellikler kazandırmanın esnek bir yoludur.

Bir `Modifier`, bir composable bileşenine bir dizi özellik uygulayabilir, örneğin:
- **Yerleşim (Layout)**: Konumlandırma, hizalama, dolgu (padding) gibi özellikler.
- **Boyutlandırma (Size)**: Genişlik, yükseklik ayarlamaları.
- **Etkileşim (Interaction)**: Tıklama, sürükleme, kaydırma gibi etkileşimler.
- **Görünüm (Appearance)**: Arka plan rengi, kenarlık, opaklık gibi görsel özellikler.


Bir composable bileşene `Modifier` eklemek için, `modifier` parametresi kullanılır.
```kotlin
import androidx.compose.foundation.layout.padding
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp

@Composable
fun TextWithModifier() {
    Text(
        text = "Merhaba Jetpack Compose!",
        modifier = Modifier.padding(16.dp)
    )
}

```
**Açıklama:**
- **`modifier = Modifier.padding(16.dp)`**: `Modifier` ile metin bileşenine 16dp dolgu eklenmiştir. Bu sayede metin, dış kenarlardan biraz boşluk bırakarak görüntülenir.

==**Modifier'ın Zincirleme Kullanımı (Modifier Chain)**==

`Modifier`'lar zincirlenebilir, yani birden fazla `Modifier` özelliğini aynı bileşene uygulayabilirsiniz. Zincirleme işlemi, kodun okunabilirliğini artırır ve daha kompleks stiller oluşturmanıza olanak tanır. Zincirleme işlemi, her `Modifier`'ın sırayla uygulanacağı anlamına gelir.

```kotlin
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.padding
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.dp

@Composable
fun TextWithChainedModifiers() {
    Text(
        text = "Zincirlenmiş Modifier'lar!",
        modifier = Modifier
            .background(Color.Yellow)  // Arka plan rengi
            .padding(16.dp)             // Dolgu (padding)
    )
}

```

Bu örnekte, önce `Text` bileşenine sarı bir arka plan rengi uygulanıyor, ardından bu bileşen 16dp dolgu ile çevreleniyor.

==**Modifier'ın Yaygın Kullanım Alanlar**== 

**Boyutlandırma (Size)**
- `Modifier.size`: Bileşenin genişliğini ve yüksekliğini ayarlar.
- `Modifier.fillMaxWidth` ve `Modifier.fillMaxHeight`: Bileşeni bulunduğu kapsayıcının genişliğini veya yüksekliğini kaplayacak şekilde yayar.
- `Modifier.fillMaxSize`: Bileşeni hem genişlik hem de yükseklik açısından kapsayıcının tamamına yayar.
- `Modifier.wrapContentSize`: İçeriğin doğal boyutlarına göre bileşenin boyutunu belirler.
```kotlin
@Composable
fun SizedBox() {
    Text(
        text = "Boyutlandırılmış Bileşen",
        modifier = Modifier.size(100.dp) // Bileşeni 100dp x 100dp yapar
    )
}

```

**Yerleşim ve Konumlandırma (Layout and Positioning)**
- `Modifier.padding`: Bileşene iç kenarlık (padding) ekler.
- `Modifier.offset`: Bileşeni, belirli bir eksende öteleme yaparak yerleştirir.
- `Modifier.align`: Bileşeni belirli bir konuma hizalar.
```kotlin
@Composable
fun PaddedText() {
    Text(
        text = "Dolgu Uygulandı",
        modifier = Modifier.padding(24.dp) // Bileşenin etrafına 24dp boşluk bırakır
    )
}

```

**Arka Plan ve Kenarlıklar (Background and Borders)**
- `Modifier.background`: Bileşene arka plan rengi ekler.
- `Modifier.border`: Bileşenin çevresine kenarlık (çizgi) ekler.
```kotlin
@Composable
fun BackgroundText() {
    Text(
        text = "Arka Planlı Metin",
        modifier = Modifier
            .background(Color.LightGray)
            .padding(16.dp)
    )
}

```

**Tıklanabilirlik ve Etkileşim (Clickability and Interaction)**
- `Modifier.clickable`: Bileşeni tıklanabilir hale getirir ve tıklama olaylarını yakalar.
- `Modifier.draggable`: Bileşeni sürüklenebilir hale getirir.
- `Modifier.scrollable`: Bileşenin kaydırılabilir olmasını sağlar.
```kotlin
@Composable
fun ClickableText() {
    Text(
        text = "Tıklanabilir Metin",
        modifier = Modifier.clickable { /* Tıklama olayını işler */ }
    )
}
```

**Şekillendirme (Shaping)**
- `Modifier.clip`: Bileşene belirli bir şekil verir (örn. yuvarlatılmış köşeler).
- `Modifier.clipToBounds`: Bileşenin sadece sınırları içinde çizilmesini sağlar.
```kotlin
@Composable
fun ShapedSurface() {
    Surface(
        modifier = Modifier
            .size(100.dp)
            .clip(RoundedCornerShape(16.dp)) // Köşeleri yuvarlanmış kare
    ) {
        Text("Yuvarlatılmış köşe")
    }
}

```

==**Bir Kart Bileşeni Oluşturma**==
```kotlin
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material.Surface
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.dp

@Composable
fun CustomCard() {
    Surface(
        modifier = Modifier
            .padding(16.dp)
            .background(Color.White)
            .padding(8.dp),
        shape = RoundedCornerShape(8.dp),
        elevation = 4.dp
    ) {
        Text(text = "Bu bir kart bileşeni")
    }
}

```

***
***Abdullah TANRIVERDİ***
