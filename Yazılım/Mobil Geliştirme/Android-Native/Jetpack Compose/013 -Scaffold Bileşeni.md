#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

==**Scaffold Nedir**==
`Scaffold`, Jetpack Compose'da temel uygulama iskeleti oluşturan bir bileşendir.

|Bileşen|Açıklama|
|---|---|
|**`topBar`**|Sayfanın üst kısmında yer alan **App Bar** (Başlık Çubuğu)|
|**`bottomBar`**|Sayfanın alt kısmında bulunan **Bottom Navigation Bar**|
|**`floatingActionButton`**|Sayfanın köşesinde duran **FAB butonu**|
|**`drawerContent`**|**Yan menü (Drawer Navigation)** içeriği|
|**`content`**|Sayfanın ana içeriği|

**Temel Kullanım**
Scaffold içinde genellikle topBar, bottomBar, floatingActionButton gibi bileşenler kullanılır.
```kotlin
Scaffold(
    topBar = {
        TopAppBar(title = { Text("Scaffold Örneği") })
    },
    content = { padding ->
        Text(
            text = "Ana İçerik",
            modifier = Modifier.padding(padding)
        )
    }
)

```

- **Top Bar (Üst Çubuk)**
`topBar` parametresi ile **uygulama başlığı (App Bar)** eklenir.
```kotlin
Scaffold(
    topBar = {
        TopAppBar(
        title = {
            Text(
                text = "Jotter",
                fontSize = 20.sp,
                textAlign = TextAlign.Center
            )
        },
        navigationIcon = {
            IconButton(onClick = { /* Geri gitme işlemi */ }) {
                Icon(Icons.Default.ArrowBack, contentDescription = "Geri Dön")
            }
        },
        actions = {
            IconButton(onClick = { /* Arama işlemi */ }) {
                Icon(Icons.Default.Search, contentDescription = "Ara")
            }
        },
        colors = TopAppBarDefaults.topAppBarColors(
            containerColor = Color(0xFF6200EA), // Arka plan rengi
            titleContentColor = Color.White // Başlık rengi
        )
    )}
)

```


- **Bottom Bar (Alt Çubuk)**
`bottomBar` parametresi ile **alt gezinti çubuğu (Bottom Navigation Bar)** eklenir.
```kotlin
Scaffold(
    bottomBar = {
        BottomAppBar(
        containerColor = Color(0xFF6200EA), // Arka plan rengi
        contentColor = Color.White // İkon rengi
    ) {
        IconButton(onClick = { /* Ana Sayfa */ }) {
            Icon(Icons.Default.Home, contentDescription = "Ana Sayfa")
        }
        IconButton(onClick = { /* Arama */ }) {
            Icon(Icons.Default.Search, contentDescription = "Arama")
        }
        IconButton(onClick = { /* Favoriler */ }) {
            Icon(Icons.Default.Favorite, contentDescription = "Favoriler")
        }
        IconButton(onClick = { /* Profil */ }) {
            Icon(Icons.Default.Person, contentDescription = "Profil")
        }
    } }
)

```


- **Floating Action Button (FAB)**
`floatingActionButton` parametresi ile ekranda yüzen buton eklenir.
```kotlin
Scaffold(
    floatingActionButton = {
        FloatingActionButton(onClick = { println("FAB Tıklandı!") }) {
            Icon(Icons.Filled.Add, contentDescription = "Ekle")
        }
    },
    content = { padding -> Text("Ana İçerik", modifier = Modifier.padding(padding)) }
)

```


```kotlin
SmallFloatingActionButton(
    onClick = { /* İşlem */ }
) {
    Icon(Icons.Default.Add, contentDescription = "Küçük FAB")
}

```

```kotlin
ExtendedFloatingActionButton(
    onClick = { /* İşlem */ },
    elevation = FloatingActionButtonDefaults.elevation(8.dp) //Gölgelendirme
    icon = { Icon(Icons.Default.Add, contentDescription = "Ekle") },
    text = { Text("Yeni Not") }
)

```


- **Drawer (Yan Menü)**
Yan menü eklemek için `drawerContent` parametresi kullanılır.
```kotlin
Scaffold(
    drawerContent = {
        Column {
            Text("Menü 1", modifier = Modifier.padding(16.dp))
            Text("Menü 2", modifier = Modifier.padding(16.dp))
        }
    },
    content = { padding -> Text("Ana İçerik", modifier = Modifier.padding(padding)) }
)

```

- **Snackbar (Bildirim Mesajı)**

Snackbar, kullanıcıya geçici bildirim mesajları göstermek için kullanılır.
```kotlin
@Composable
fun SnackbarExample() {
    val snackbarHostState = remember { SnackbarHostState() }
    val coroutineScope = rememberCoroutineScope()

    Scaffold(
        snackbarHost = { SnackbarHost(hostState = snackbarHostState) },
        floatingActionButton = {
            FloatingActionButton(onClick = {
                coroutineScope.launch {
                    snackbarHostState.showSnackbar("Bu bir Snackbar!")
                }
            }) {
                Icon(Icons.Filled.Info, contentDescription = "Bilgi")
            }
        }
    ) { padding ->
        Text("Snackbar Örneği", modifier = Modifier.padding(padding))
    }
}

```



|**Parametre**|**Açıklama**|
|---|---|
|`topBar`|Üst çubuk (AppBar) ekler.|
|`bottomBar`|Alt çubuk (Bottom Navigation) ekler.|
|`floatingActionButton`|Sağ altta yüzen bir buton ekler.|
|`drawerContent`|Yan menü (Drawer) ekler.|
|`snackbarHost`|Kullanıcıya bildirim göstermek için Snackbar ekler.|

---

***Abdullah TANRIVERDİ***

