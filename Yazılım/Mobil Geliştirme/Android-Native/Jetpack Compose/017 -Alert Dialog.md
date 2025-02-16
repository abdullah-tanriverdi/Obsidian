#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 


![[Pasted image 20250216225944.png|500]]


AlertDialog, kullanıcılara önemli mesajlar göstermek ve onlardan geri bildirim almak için kullanılan bir bileşendir. Kullanıcıdan onay almak veya belirli bir işlemi gerçekleştirmeden önce uyarı göstermek için yaygın olarak kullanılır.

```kotlin
@Composable
fun MyAlertDialog(showDialog: Boolean, onDismiss: () -> Unit, onConfirm: () -> Unit) {
    if (showDialog) {
        AlertDialog(
            onDismissRequest = onDismiss,
            title = { Text(text = "Uyarı") },
            text = { Text(text = "Bu işlemi yapmak istediğinizden emin misiniz?") },
            confirmButton = {
                TextButton(onClick = onConfirm) {
                    Text("Evet")
                }
            },
            dismissButton = {
                TextButton(onClick = onDismiss) {
                    Text("Hayır")
                }
            }
        )
    }
}
```


- `AlertDialog`, kullanıcıdan onay almak veya önemli bilgiler göstermek için kullanılır.
- `onDismissRequest`, `title`, `text`, `confirmButton` ve `dismissButton` gibi temel parametrelerle çalışır.
- `remember` ve `mutableStateOf` kullanarak diyalog gösterme/kapatma işlemi kontrol edilir.
- Standart metinler yerine özel içerikler de kullanılabilir.
---

***Abdullah TANRIVERDİ***


