#Yazılım #ProgramlamaDilleri #Java 


![[History Of Java1.png]]

Java, 23 Mayıs 1995 yılında Sun Microsystems tarafından geliştirilen, nesne yönelimli, platform bağımsız, yüksek seviyeli ve güvenli bir programlama dilidir. Dilin tasarımı ve geliştirilmesi, bilgisayar mühendisi James Gosling liderliğindeki deneyimli bir ekip tarafından gerçekleştirilmiştir. 



![[History Of Java2.png]]

> [!note] Sun Microsystems
> 1982 yılında kurulan Amerikan merkezli bir teknoloji şirketidir. Sun, özellikle Java programlama dili ve Unix tabanlı Solaris işletim sistemi ile tanınır. 2010 yılında Oracle Corporation tarafından satın alınmıştır.


James Gosling ve Ekibi, 1990'ların başında Sun Microsystems bünyesinde Java programlama dilini geliştirmek üzere bir araya gelen yazılım mühendisleri ve araştırmacılardan oluşan bir takımdır. Bu ekip, “Green Project” (Yeşil Proje) adı verilen bir girişim kapsamında çalışmaya başlamış, amacı taşınabilir, güvenli ve platform bağımsız bir programlama dili oluşturmaktı.


- **James Gosling**: Projenin lideri ve Java dilinin asıl mimarı. Dili tasarladı ve temel özelliklerini belirledi.
    
- **Mike Sheridan**: Projede önemli bir rol oynayan yazılım mühendisi, ilk JVM (Java Virtual Machine) geliştirilmesinde görev aldı.
    
- **Patrick Naughton**: Projenin erken aşamalarında yer alan ve Java’nın ilk prototiplerini geliştiren ekip üyelerinden biri.


![[History Of Java3.jpg|400]]

Platformdan bağımsız bir geliştirme süreci yaratmak isteyen Gosling, işe C++ derleyicisini genişleterek başladı. Ancak bir süre sonra, ne kadar eklenti yapılırsa yapılsın C++’ın yetersiz kalacağını anladı. Böylece Oak dili 1991 ortasında doğdu. 

**C++ İle Yaşanan Sorunlar**
- **Platform Bağımlılığı:** C++ kodu doğrudan işletim sistemine ve donanıma bağımlı şekilde derleniyordu.
- **Bellek Yönetimi:** C++’ta bellek yönetimi tamamen programcının elindeydi (`malloc/free`, `new/delete`). Bu esneklik güzel ama özellikle gömülü cihazlarda hafıza hataları, bellek sızıntıları gibi kritik problemler yaratıyordu.
- **Güvenlik:** C++ pointer’larla çok güçlü ama aynı zamanda riskli bir dil. Pointer hataları, buffer overflow saldırılarına açık kapı bırakıyordu.

> [!info] İPUCU
> - **Buffer Overflow Saldırısı:** Bir programın ayırdığı bellek sınırlarını aşarak fazladan veri yazılması sonucu, saldırganın zararlı kod çalıştırabilmesine yol açan güvenlik açığıdır.
>- **Pointer Hatası:** Yanlış veya geçersiz bir bellek adresine işaret eden pointer kullanımı nedeniyle programın çökmesine ya da beklenmedik davranış göstermesine denir.

- **Basitlik:** C++ çok karmaşık bir dil hâline gelmişti.

> [!note] OAK
> Java’nın öncüsü olan Oak adlı dil, James Gosling ve Green Team (Yeşil Takım) tarafından tasarlandı. Oak dili, tüketici elektroniği (set-top box’lar, TV cihazları) için geliştirilen gömülü sistemlerde kullanılmak üzere tasarlanmıştı. Oak hiçbir zaman yaygınlaşmadı çünkü cihaz üreticileri çok sınırlı donanımlara sahipti. Bu yüzden proje beklemeye alındı.

> [!tip] Neden Oak İsmi
>James Gosling’in ofisinin önünde duran meşe ağacından (oak) ilham alındı.

> [!quote] ALINTI
> “Dil başlı başına bir amaç değildi, sadece bir araçtı,” diyor Gosling.  
“Amacımız C++ ile rekabet etmek değil, birbirleriyle iletişim kurabilen çok sayıda dağıtık, heterojen tüketici elektroniği cihazlarından oluşan bir sistem kurmaktı.”


> [!tip] WORA
> Java’nın temel amacı, geliştiricilerin bir kez yazdıkları kodu farklı donanım ve işletim sistemlerinde değişiklik yapmadan çalıştırabilmesini sağlamaktır. Bu nedenle Java, “**Write Once, Run Anywhere**” (WORA) sloganıyla tanınır.



> [!tip] Neden Java İsmi
> İsmini Java kahvesinden aldı. Geliştiriciler kod yazarken çok kahve tüketiyordu

2010 yılında Oracle Corporation, Sun Microsystems’i yaklaşık **7,4 Milyar Dolar** değerinde bir anlaşma ile satın almış ve böylece Java’nın gelişimi ve desteğini üstlenmiştir. 21 Ocak 2010’da şartsız onay verilmiştir. 27 Ocak 2010’da resmî olarak tamamlanan bu satın alma ile Oracle yalnızca yazılım şirketi olmaktan çıkarak, donanım ve yazılımı entegre eden güçlü bir teknoloji şirketine dönüşmüştür.

![[History Of Java4.png]]


> [!note] Oracle Corporation
> 1977 yılında kurulan dünyanın önde gelen teknoloji şirketlerinden biridir. Şirket, 2010 yılında Sun Microsystems’i satın alarak Java programlama dili, Solaris işletim sistemi ve MySQL veri tabanı gibi önemli teknolojileri portföyüne katmıştır. Oracle, dünya çapında finans, sağlık, telekomünikasyon, kamu ve perakende gibi birçok sektörde kritik altyapıları desteklemekte ve dijital dönüşüm süreçlerine öncülük etmektedir. Sürekli Ar-Ge yatırımlarıyla inovasyona büyük önem verir.


**Java Maskotu**

![[History Of Java5.png]]

- **Adı:** Duke

Açık kaynak lisansla (BSD License) paylaşıldı – isteyen geliştiriciler kendi Duke sürümlerini oluşturabilir.




| Özellik                         | Açıklama                                                                  |
| ------------------------------- | ------------------------------------------------------------------------- |
| **Nesne Yönelimli (OOP)**       | Tüm yapı nesneler ve sınıflar etrafında şekillenir.                       |
| **Platform Bağımsız**           | "Write Once, Run Anywhere" (WORA) felsefesiyle çalışır.                   |
| **Güvenli**                     | Bellek yönetimi ve sınırlı erişim sayesinde daha güvenli bir ortam sunar. |
| **Çoklu İş Parçacığı (Thread)** | Aynı anda birden fazla işlem yapılabilir.                                 |
| **Dağıtık Uygulama Desteği**    | Ağ üzerinden çalışan uygulamalar kolayca geliştirilebilir.                |
| **Yüksek Performanslı**         | JIT (Just-In-Time) Compiler sayesinde hızlı çalışır.                      |
| **Garbage Collection**          | Bellek yönetimi otomatik olarak yapılır.                                  |
| **Dinamik ve Genişletilebilir** | Yeni kodlar çalışma anında yüklenebilir.                                  |




**Java'nın WORA Felsefesi**

- Java derlendikten sonra makine koduna değil, bytecode’a çevrilir.
    
- Bu bytecode, her işletim sistemi için ayrı geliştirilen JVM ile çalıştırılır.
    
- Böylece bir kez yazılan kod, farklı işletim sistemlerinde yeniden derlenmeden çalışabilir.




**Java'nın Kullanım Alanları**

|Alan|Açıklama|
|---|---|
|**Web Uygulamaları**|Spring, JSP, Servlets gibi araçlarla güçlü backend sistemleri|
|**Mobil Uygulamalar**|Android uygulamalarının temel dili Java’dır|
|**Masaüstü Uygulamaları**|JavaFX, Swing, AWT kullanılır|
|**Kurumsal Yazılımlar**|JEE (Java Enterprise Edition) ile büyük ölçekli çözümler|
|**Gömülü Sistemler**|Küçük cihazlar (akıllı kartlar vb.)|
|**Bilimsel Uygulamalar**|Yüksek performanslı, taşınabilir bilimsel hesaplamalar|
|**Oyun Geliştirme**|Minecraft örneği|

| Yıl   | Gelişme                                            |
| ----- | -------------------------------------------------- |
| 1991  | James Gosling “Oak” dilini tasarladı               |
| 1995  | Java 1.0 piyasaya sürüldü                          |
| 2006  | Java açık kaynak oldu (OpenJDK)                    |
| 2010  | Oracle, Sun Microsystems’ı satın aldı              |
| 2017  | Yeni sürüm politikası (6 ayda bir) başladı         |
| 2023+ | Java 21 gibi LTS(Long-Term Support) sürümler çıktı |



> [!success] STAR7
Java’nın ilk dönemlerinde ortaya çıkan, Java platformunun ilk grafiksel kullanıcı arayüzü (GUI) testleri ve etkileşimli teknolojileri için geliştirilen deneysel bir cihazdır. Sun Microsystems, 1990’larda internetin ve akıllı cihazların önem kazanacağını öngörerek bu tür cihazlar üzerinde çalışıyordu. Star7 bu vizyonun ilk adımıydı. Green işletim sistemi, arayüz ve donanım dahil olmak üzere tonla kod yazdıktan sonra ekip "*" 7 (telefon tuşlarındaki yıldızdan esinlenerek bu cihaza bu ismi vermişlerdir.



![[History Of Java6.jpg]]


| STAR7 Özellik                 | Açıklama                                                      |
| ----------------------------- | ------------------------------------------------------------- |
| 📺 **Küçük Ekran**            | LCD ekran; grafik arayüz destekliydi                          |
| 🎙️ **Ses Giriş/Çıkış**       | Mikrofon ve hoparlör içeriyordu; sesli etkileşim için         |
| 🖱️ **Basit Giriş Cihazları** | Butonlar veya dokunmatik ekran                                |
| 🧠 **Gömülü Yazılım**         | Oak dili (Java’nın öncüsü) ile yazılmış basit işletim sistemi |
| 🤖 **Duke Maskotu**           | Sanal rehber olarak cihaz arayüzünde Duke yer alıyordu        |

<iframe width="560" height="315" 
  src="https://www.youtube.com/embed/1CsTH9S79qI" 
  title="YouTube video player" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>


> [!info] JavaOne
> İlk olarak 1996 yılında Sun Microsystems tarafından düzenlenen, Java geliştiricilerine yönelik en büyük ve en etkili yıllık teknoloji konferanslarından biridir. 2018’den sonra Oracle, JavaOne yerine Oracle Code One isminde daha geniş kapsamlı bir etkinlik yapmaya başladı. Ancak 2022 itibarıyla JavaOne tekrar bağımsız bir etkinlik olarak geri döndü.


> [!success] WebRunner
> Java WebRunner, 1990’ların ortalarında Sun Microsystems tarafından geliştirilen, tamamen Java diliyle yazılmış ilk web tarayıcılardan biridir. Başlangıçta “WebRunner” olarak adlandırılan bu tarayıcı, daha sonra “HotJava” ismini almıştır. Java WebRunner, Java applet’lerini çalıştırabilen ve web içeriğini dinamik olarak yorumlayabilen yenilikçi bir araç olarak, Java teknolojisinin potansiyelini göstermek amacıyla geliştirilmiştir. Bu tarayıcı, Java’nın “bir kere yaz, her yerde çalıştır” felsefesinin ilk uygulamalarından biri olarak kabul edilir ve modern web tarayıcılarının Java desteğinin temelini oluşturmuştur. Günümüzde ise “WebRunner” ismi, bazı Java tabanlı projelerde web uygulamalarını hızlıca çalıştırmak için kullanılan araçlar ya da embedded server başlatıcıları için de kullanılabilmektedir.


> [!note] Java Applet
Java Applet, web sayfalarına gömülebilen küçük Java programlarıdır.



![[History Of Java7.jpg]]


<iframe width="560" height="315" 
  src="https://www.youtube.com/embed/r19P3y1VBiw" 
  title="YouTube video player" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>



<iframe width="560" height="315" 
  src="https://www.youtube.com/embed/l9AzO1FMgM8" 
  title="YouTube video player" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>


<iframe width="560" height="315" 
  src="https://www.youtube.com/embed/3xjr3DmLfmM" 
  title="YouTube video player" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
  allowfullscreen>
</iframe>


<iframe width="560" height="315" 
    src="https://www.youtube.com/embed/6iP376VwcjY" 
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    allowfullscreen>
</iframe>



> [!tip] İPUCU
> [[001 -James Gosling]]
> [[002 -JVM]]
> [[003 -Garbage Collection]]
> [[001 -OOP]]
> [[019 -Thread]]
> [[002 -JIT vs AOT]]
> [[005 -Machine Code]]
> [[004 -Byte Code]]
> [[006 -Compiler]]

***

***Abdullah TANRIVERDİ***

