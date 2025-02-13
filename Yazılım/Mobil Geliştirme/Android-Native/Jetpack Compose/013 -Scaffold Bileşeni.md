#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose

==**Scaffold Nedir**==
`Scaffold`, Jetpack Compose'da temel uygulama iskeleti oluşturan bir bileşendir.

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
            title = { Text("Başlık") },
            backgroundColor = Color.Blue,
            contentColor = Color.White
        )
    },
    content = { padding -> Text("İçerik Alanı", modifier = Modifier.padding(padding)) }
)

```

- **Bottom Bar (Alt Çubuk)**
`bottomBar` parametresi ile **alt gezinti çubuğu (Bottom Navigation Bar)** eklenir.
```kotlin
Scaffold(
    bottomBar = {
        BottomAppBar {
            Text("Alt Çubuk")
        }
    },
    content = { padding -> Text("Ana İçerik", modifier = Modifier.padding(padding)) }
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

