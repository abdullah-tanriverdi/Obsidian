#Yazılım #MobilGeliştirme #Android-Native  #JetpackCompose 

 DropDown Menu, kullanıcının seçim yapabileceği açılır bir liste sunar.

 ![[Pasted image 20250320104657.png]]

 ```kotlin
 import androidx.compose.foundation.clickable
import androidx.compose.foundation.layout.*
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp

@Composable
fun SimpleDropDownMenu() {
    var expanded by remember { mutableStateOf(false) }
    val options = listOf("Seçenek 1", "Seçenek 2", "Seçenek 3")
    var selectedOption by remember { mutableStateOf(options[0]) }

    Column {
        Button(onClick = { expanded = true }) {
            Text(selectedOption)
        }

        DropdownMenu(
            expanded = expanded,
            onDismissRequest = { expanded = false }
        ) {
            options.forEach { option ->
                DropdownMenuItem(
                    text = { Text(option) },
                    onClick = {
                        selectedOption = option
                        expanded = false
                    }
                )
            }
        }
    }
}

```


```kotlin
@Composable
fun OverflowMenu() {
    var expanded by remember { mutableStateOf(false) }

    Box {
        IconButton(onClick = { expanded = true }) {
            Icon(Icons.Default.MoreVert, contentDescription = "Menü")
        }

        DropdownMenu(expanded = expanded, onDismissRequest = { expanded = false }) {
            DropdownMenuItem(
                text = { Text("Ayarlar") },
                onClick = { expanded = false }
            )
            DropdownMenuItem(
                text = { Text("Hakkında") },
                onClick = { expanded = false }
            )
            DropdownMenuItem(
                text = { Text("Çıkış Yap") },
                onClick = { expanded = false }
            )
        }
    }
}

```

---
***Abdullah TANRIVERDİ***