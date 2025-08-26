#Yazılım #Yazılım-Jargon 

Process (süreç), bilgisayarda çalışan bir programın çalışmakta olan halidir. Yani program diskte pasif halde durur (örneğin `.exe` dosyası). Çalıştırıldığında işletim sistemi tarafından belleğe yüklenir ve bir process oluşur. Process, CPU üzerinde yürütülen aktif çalışma birimidir.

- **Program:** Sabit disk üzerinde saklanan pasif komutlar topluluğu.
- **Process:** Programın belleğe yüklenmiş ve CPU’da yürütülen hali.

|Özellik|Program|Process|
|---|---|---|
|Durum|Pasif|Aktif|
|Konum|Disk|Bellek (RAM)|
|Ömür|Kalıcı|Çalıştırıldığı sürece var|
|Çoklama|Aynı anda tek|Aynı programdan birden fazla process olabilir|

**Process Bileşenleri**
1. **Kod Bölgesi (Text Segment):** Çalıştırılacak komutlar.
2. **Veri Bölgesi (Data Segment):** Global ve statik değişkenler.
3. **Heap:** Dinamik bellek (runtime’da oluşturulan nesneler).
4. **Stack:** Fonksiyon çağrıları, yerel değişkenler, geri dönüş adresleri.


**Process Control Block (PCB)**
Her process’i işletim sistemi yönetebilmek için bir veri yapısı kullanır:
- Process ID (PID)
- Process’in durumu (ready, running, waiting)
- Program counter (bir sonraki komutun adresi)
- CPU register bilgileri
- Bellek yönetim bilgileri
- Girdi/çıktı (I/O) bilgileri

**Process Türleri**
- **User Processes:** Kullanıcı tarafından başlatılan uygulamalar (Word, oyun, tarayıcı).
- **System Processes:** İşletim sistemi tarafından çalışan arka plan süreçleri (daemon/service).

**Process Yönetimi**
İşletim sistemi (OS), CPU’yu birden fazla process arasında paylaştırır. Bu işleme process scheduling (süreç zamanlayıcı) denir. CPU bir process’ten diğerine geçtiğinde, mevcut process’in bilgileri kaydedilir ve diğerininki yüklenir. Bu işlem işletim sisteminin çoklu görev (multitasking) yapabilmesini sağlar.

**Processler Arası İletişim (Inter-Process Communication-IPC)**
Process’ler birbirinden izole çalışır ama bazen veri paylaşmaları gerekir. Bunun için
- Pipe (Boru hattı)
- Message Queue (Mesaj Kuyruğu)
- Shared Memory (Paylaşımlı Bellek)
- Socket


- Process: Daha ağır, kendi bellek alanı vardır.
- Thread: Process içindeki daha hafif alt çalışma birimi, ortak belleği paylaşır.

|Özellik|Process|Thread|
|---|---|---|
|Bellek Alanı|Ayrı|Ortak|
|Yaratma Maliyeti|Yüksek|Düşük|
|İletişim|Yavaş (IPC gerekir)|Hızlı (ortak bellek)|
|Bağımsızlık|Yüksek|Düşük|

- Process = çalışan program
- İçinde kod, veri, heap, stack bulunur.
- OS tarafından PCB ile yönetilir.
- Yaşam döngüsü: Yeni → Hazır → Çalışıyor → Bekleme → Sonlanma.
- Process yönetimi işletim sisteminin temel görevidir.
***

***Abdullah TANRIVERDİ***
