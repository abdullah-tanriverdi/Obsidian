#Yazılım #Yazılım-Jargon 


![[JSON1.png|400]]

**JSON (JavaScript Object Notation)**, veri alışverişi için kullanılan hafif bir veri formatıdır. İnsanlar tarafından okunabilir, makineler tarafından kolayca işlenebilir. Özellikle web servisleri ve API'ler arasında veri iletimi için yaygın bir biçimdir. JSON, JavaScript dilinden türemiş olmasına rağmen, pek çok programlama dili tarafından desteklenir ve kullanılır.


- **Hafif ve İnsan Okunabilir**: JSON, sade bir yapıya sahip olduğundan hem insanlar hem de makineler tarafından kolayca anlaşılabilir.
    
- **Yapılandırılmış Veri Formatı**: JSON, anahtar-değer çiftleri (key-value pairs) şeklinde veriyi organize eder.
    
- **Dil Bağımsızlığı**: JSON, JavaScript'ten türemiş olsa da, hemen hemen tüm programlama dillerinde kullanılabilir (Java, Python, Kotlin, PHP, Ruby, vb.).
    
- **Metin Tabanlı**: JSON tamamen metin tabanlı bir formattır, bu da onu taşıması ve iletmesi kolay kılar.



JSON verisi, **nesneler (objects)** ve **diziler (arrays)** gibi iki ana yapı kullanılarak organize edilir. JSON’daki temel veri türleri şunlardır:

- String (Metin): `"Hello, World"`
    
- Number (Sayı): `123`, `45.67`
    
- Boolean (Mantıksal Değer): `true`, `false`
    
- Null (Boş Değer): `null`
    
- Object (Nesne): `{ "key": "value" }`
    
- Array (Dizi): `[ "item1", "item2", "item3" ]`



**JSON Object (Nesne)**
Bir **JSON nesnesi** (`object`), anahtar-değer çiftlerinden oluşur. Her bir anahtar ve değer arasına iki nokta `:` koyulur. Nesneler, süslü parantez `{}` ile çevrelenir.

```json
{
  "name": "John Doe",
  "age": 30,
  "email": "johndoe@example.com"
}

```
`name`, `age`, ve `email` anahtarları; `"John Doe"`, `30`, ve `"johndoe@example.com"` değerlerine sahiptir.

**JSON Array (Dizi)**
Bir **JSON dizisi** (`array`), sıralı bir değerler koleksiyonudur ve köşeli parantez `[]` ile çevrelenir. Dizi elemanları virgülle ayrılır.

```json
{
  "fruits": ["apple", "banana", "cherry"]
}

```
Burada, `fruits` anahtarının değeri bir dizi olup, dizinin elemanları `"apple"`, `"banana"`, ve `"cherry"`'dir.


---

***Abdullah TANRIVERDİ***

