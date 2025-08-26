#Yazılım #Yazılım-Jargon 


Thread (iş parçacığı), bir programın (process / süreç) içinde bağımsız şekilde yürütülebilen en küçük çalışma birimidir.Tek bir process birden fazla thread barındırabilir.

Aynı process içindeki tüm thread’ler:
- Aynı adres alanını (memory space) paylaşır.
- Aynı kod, veri ve heap segmentlerini paylaşır.
- Ancak her thread’in kendine ait stack alanı vardır.

- **Process (Süreç):**
    - İşletim sistemi tarafından çalışan bağımsız bir program.
        
    - Her sürecin kendi bellek alanı vardır.
        
- **Thread (İş Parçacığı):**
    - Süreç içerisinde çalışan alt yürütme birimi.
        
    - Aynı bellek alanını paylaşır, bu yüzden thread’ler arası iletişim hızlıdır.

|Özellik|Process|Thread|
|---|---|---|
|Bellek Alanı|Ayrı|Ortak|
|Oluşturma Maliyeti|Yüksek|Düşük|
|İletişim|IPC (Pipe, Socket, Message Queue)|Ortak bellek|
|Bağımlılık|Bağımsız|Aynı process’e bağlı|

**Thread Çeşitleri**
- **User-Level Thread (Kullanıcı Düzeyi):**
    - İşletim sisteminden bağımsız, kütüphane tarafından yönetilir.
    - Hafiftir ama çekirdek tarafından direkt görülmez.
- **Kernel-Level Thread (Çekirdek Düzeyi):**
    - İşletim sistemi çekirdeği tarafından yönetilir.
    - Daha güçlü ama maliyetlidir.

**Thread İle İlgili Kavramlar**
- **Race Condition:** Aynı kaynağa aynı anda erişen thread’lerin veriyi bozması.
- **Mutex (Mutual Exclusion):** Tek seferde yalnızca bir thread’in erişmesine izin veren kilit.
- **Semaphore:** Kaynağa aynı anda belirli sayıda thread’in erişimini kısıtlayan mekanizma.
- **Deadlock:** Thread’lerin birbirini bekleyerek sonsuz kilitlenme yaşaması.
- **Context Switch:** CPU’nun bir thread’den diğerine geçiş yapma işlemi.

**Örnek Kod İle Thread Oluşturma**
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread çalışıyor: " + Thread.currentThread().getName());
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        MyThread t2 = new MyThread();
        
        t1.start();
        t2.start();
    }
}

```

**Kısacası**
- Thread, bir programın aynı anda birden fazla işi yapabilmesini sağlar.
- Performansı artırır ama dikkatli kullanılmazsa senkronizasyon sorunları çıkar.
- Modern yazılım geliştirmede (özellikle yüksek performanslı uygulamalarda) multithreading vazgeçilmezdir.

***
***Abdullah TANRIVERDİ***
