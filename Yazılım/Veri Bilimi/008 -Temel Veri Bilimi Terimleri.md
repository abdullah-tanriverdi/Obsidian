#Yazılım #VeriBilimi 


==**Aykırı Değer (Outlier) Nedir**==
**Tanım:** Veri setinde, diğer değerlerden çok farklı olan verilere "aykırı değer" denir.  
**Örnek:** Bir sınıfta öğrencilerin yaş ortalaması 20, ama bir öğrenci 50 yaşında → Aykırı değer! 
📌 Z-score veya IQR yöntemi ile bulunur.


==**Eksik Veri (Missing Data)**==
**Tanım:** Veri setinde bazı hücrelerin boş olması durumu.  
**Nasıl çözülür?**  
✔ Silme (`dropna()`)  
✔ Ortalama, medyan veya en yakın değerle doldurma (`fillna()`)



==**Standart Sapma (Standard Deviation)**==
**Tanım:** Verilerin ortalama etrafında nasıl dağıldığını gösteren bir ölçü.  
✔ **Düşük Standart Sapma:** Veriler birbirine yakın (örneğin: 49, 50, 51)  
✔ **Yüksek Standart Sapma:** Veriler çok farklı (örneğin: 10, 50, 90)


==**Korelasyon(Correlation)**==
**Tanım:** İki değişken arasındaki ilişkinin gücünü gösterir.  
📌 Korelasyon katsayısı -1 ile 1 arasında değişir:

- +1 → Güçlü pozitif ilişki (Boy arttıkça kilo da artar)
- -1 → Güçlü negatif ilişki (Hız arttıkça yakıt tüketimi azalır)
- 0 → Hiç ilişki yok
🔹 Heatmap (Isı Haritası) ile görselleştirilebilir.



==**Normalizasyon & Standartlaştırma**==

📌 Veriyi ölçeklendirme yöntemleridir.  
✔ Normalizasyon (Min-Max Scaling): Veriyi 0 ile 1 arasına sıkıştırır.  
✔ Standartlaştırma (StandardScaler): Verinin ortalamasını 0, standart sapmasını 1 yapar.

**Örnek:**

- Orijinal veriler: `[10, 200, 5000]`
- Normalizasyon sonrası: `[0.002, 0.04, 1]`


******

***Abdullah TANRIVERDİ***

