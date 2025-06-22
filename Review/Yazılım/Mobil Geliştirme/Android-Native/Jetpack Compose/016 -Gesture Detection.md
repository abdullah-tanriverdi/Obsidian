#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 
Jetpack Compose, kullanıcı etkileşimlerini algılamak için **Gesture Detection (Dokunma ve Hareket Algılama)** mekanizmaları sunar.

==**1. Click (Tıklama) Algılama**==

En temel hareketlerden biri, kullanıcının bir öğeye dokunmasını algılamaktır.
```kotlin
@Composable
fun ClickGestureExample() {
    var clicked by remember { mutableStateOf(false) }

    Box(
        modifier = Modifier
            .size(100.dp)
            .background(if (clicked) Color.Green else Color.Gray)
            .clickable { clicked = !clicked },
        contentAlignment = Alignment.Center
    ) {
        Text(text = "Tıkla!", color = Color.White)
    }
}

```
✅ `clickable {}` → Tıklama hareketini algılar.

==**2. Long Click (Uzun Basma) Algılama**==
Bir bileşene **uzun süre basıldığında** farklı bir işlem yapabiliriz.
```kotlin
@Composable
fun LongClickGestureExample() {
    var text by remember { mutableStateOf("Beni Basılı Tut!") }

    Box(
        modifier = Modifier
            .size(150.dp)
            .background(Color.Cyan)
            .combinedClickable(
                onClick = { text = "Tıklandı!" },
                onLongClick = { text = "Uzun Basıldı!" }
            ),
        contentAlignment = Alignment.Center
    ) {
        Text(text = text, color = Color.Black)
    }
}

```
✅ `combinedClickable` → Hem normal tıklama hem uzun basma hareketlerini algılar.

==**3. Swipe (Kaydırma) Algılama**==
Kullanıcının bir öğeyi sağa veya sola kaydırmasını algılayabiliriz.
```kotlin
@Composable
fun SwipeGestureExample() {
    var swipeDirection by remember { mutableStateOf("Kaydırın!") }

    val swipeableState = rememberSwipeableState(initialValue = 0)
    val sizePx = with(LocalDensity.current) { 150.dp.toPx() }

    Box(
        modifier = Modifier
            .size(150.dp)
            .background(Color.LightGray)
            .swipeable(
                state = swipeableState,
                anchors = mapOf(0f to 0, sizePx to 1),
                orientation = Orientation.Horizontal
            ),
        contentAlignment = Alignment.Center
    ) {
        swipeDirection = if (swipeableState.currentValue == 1) "Sağa Kaydırıldı!" else "Sola Kaydırıldı!"
        Text(text = swipeDirection, color = Color.Black)
    }
}

```

✅ `swipeable` → Yatay kaydırma hareketlerini algılar.



==**4. Drag (Sürükleme) Algılama**==
Bir öğenin ekran üzerinde sürüklenmesini (Drag & Drop) sağlayabiliriz
```kotlin
@Composable
fun DragGestureExample() {
    var offset by remember { mutableStateOf(Offset(0f, 0f)) }

    Box(
        modifier = Modifier
            .offset { IntOffset(offset.x.roundToInt(), offset.y.roundToInt()) }
            .size(100.dp)
            .background(Color.Blue)
            .pointerInput(Unit) {
                detectDragGestures { _, dragAmount ->
                    offset += dragAmount
                }
            },
        contentAlignment = Alignment.Center
    ) {
        Text(text = "Sürükle!", color = Color.White)
    }
}

```
✅ `detectDragGestures` → Sürükleme hareketlerini algılar.


==**4. Çoklu Dokunma (Multi-Touch) Algılama**==
İki parmak ile yakınlaştırma (Pinch Zoom) veya döndürme (Rotation) hareketlerini algılayabiliriz.
```kotlin
@Composable
fun MultiTouchGestureExample() {
    var scale by remember { mutableStateOf(1f) }
    var rotation by remember { mutableStateOf(0f) }

    Box(
        modifier = Modifier
            .size(150.dp)
            .graphicsLayer(
                scaleX = scale,
                scaleY = scale,
                rotationZ = rotation
            )
            .background(Color.Red)
            .pointerInput(Unit) {
                detectTransformGestures { _, _, zoom, rotate ->
                    scale *= zoom
                    rotation += rotate
                }
            },
        contentAlignment = Alignment.Center
    ) {
        Text(text = "Pinch & Rotate", color = Color.White)
    }
}

```

✅ `detectTransformGestures` → Çoklu dokunma hareketlerini (yakınlaştırma, döndürme) algılar.  
✅ Kutu iki parmakla büyütülebilir ve döndürülebilir.

---

***Abdullah TANRIVERDİ***

