# trex_research
## 1. Modern Yazılım Geliştirme Pratikleri
### Git ve GitHub nedir?
Git: yapılan değişiklikleri takip eden ve projenin farklı sürümlerini saklamayı sağlayan yerel (local) bir versiyon kontrol sistemidir. Örneğin, Version A Git'e kaydedildikten sonra Version B'de bir sorun oluşursa, önceki Version A'ya geri dönülebilir.
GitHub: Git ile yönetilen projeleri internet üzerinde saklamaya, paylaşmaya ve ekip halinde geliştirmeye yarayan uzak repository platformudur. GitHub'da yapılan değişiklikler proje sahibine gönderilir. Proje sahibi değişiklikleri kabul ederse main repo ile merge yapılır ve yapılan değişiklikler ana projeye eklenmiş olur. Kabul etmezse değişiklikler reddedilir.
### Git komutlarının kısa açıklamaları:
git init: Bir klasorde Git'i baslatilir ve klasoru Git repository'si haline getiriyor.
git clone: proje dosyalarini bilgisayara kopyalar/indirir ve o proje dosyalarina degistirme gelistirme yapmamiza olanak sagliyor.
git add: bir sonraki komut icin dosyalari hazirliyor.
git commit: Degisiklikleri Git'in yerel (local) gecmisine kaydeder.
git push: Local commit'leri GitHub gibi uzak repository'ye gonderir.
git pull: Repository deki guncel degisiklikleri bilgisayar ceker.
git branch: ana proje den bagimsiz bir calisma yada gelistirme Alani olusturur.
git merge: bir branch takti degisiklikleri farkli bir branch ile birlestirir.

### Merge Conflict nedir?
İki branch'te aynı yerde farklı değişiklikler yapılması durumunda branch'leri birleştirirken çakışma oluşur. Bu duruma merge conflict denir. otomatik olarak Git'in branch'leri  birleştirmeyi reddetmesi durumudur.

Çözümü: Çakışan bölge manuel olarak düzeltilir ve hangi değişikliklerle devam edileceğine karar verilir. Daha sonra 'git add .' ve 'git commit' komutları girilerek değişiklikler kaydedilir ve sorun çözülmüş olur.


### CI/CD nedir?
CI, sürekli entegrasyon anlamına geliyor. Yapılan kod değişikliklerinde otomatik olarak build ve test işlemlerini gerçekleştiriyor. Bunun avantajı, hataları daha hızlı fark etmemizi ve bu sayede fazla zaman kaybetmememizi sağlamasıdır. Örneğin A kişisi yeni bir API üzerinde çalışırken, diğer kişi farklı bir UI üzerinde çalışıyor olabilir. CI olmasaydı, bu iki farklı çalışmanın birleştirilmesi sırasında oluşan hatalar çok daha geç fark edilebilirdi. Bu hataları sonradan düzeltmek ise hem maliyetli olabilir hem de çok fazla zaman kaybettirebilir.

CD, CI aşamasındaki build ve test işlemlerinden sonra başarılı olan kodun yayınlanmasını veya yayınlanmaya hazır hale getirilmesini sağlar. Yani kodun otomatik olarak sunucuya gönderilmesi ve kullanıma açılması gibi işlemleri gerçekleştirebilir.

SDLC adımlarının tanımı ve yazılımcının süreçteki yeri nedir?
bir yazılımın fikir aşamasından başlayıp geliştirilmesi, test edilmesi, kullanıma sunulması ve bakımının yapılmasına kadar geçen tüm süreci ifade eder.

## 2. .NET Ekosistemi
.NET nedir? Tarihçesi, amacı, neden kullanılır?
.NET, Microsoft tarafından geliştirilen, uygulama geliştirmek için kullanılan açık kaynaklı ve platformlar arası bir yazılım geliştirme platformudur. C# gibi dillerle web, masaüstü, mobil ve API uygulamaları geliştirmek için kullanılır. Yüksek performans, güvenilirlik ve farklı işletim sistemlerinde çalışabilme gibi avantajları nedeniyle tercih edilir.

.NET Framework, .NET Core ve .NET 7/8+ farkları nelerdir ve Platformlar arası çalışabilir mi? (Windows, Linux, macOS)
.NET Framework, eski nesil ve yalnızca Windows üzerinde çalışan .NET platformudur; .NET Core, açık kaynaklı ve Windows, Linux, macOS gibi farklı platformlarda çalışabilen modern versiyondur; .NET 7/8+ ise .NET Core'un devamı olan güncel .NET sürümleridir ve daha yüksek performans ile yeni özellikler sunar.

### Bilgisayarimdan dotnet --info çıktısı örneği:
SDK Version: Proje geliştirmek için kullanılan .NET sürümü.
OS Name: İşletim sistemi.
Architecture: Sistemin mimarisi (x64, x86, ARM64).
ASP.NET Core Runtime: ASP.NET Core uygulamalarını çalıştırmak için gerekli ortam.
.NETCore Runtime: .NET uygulamalarını çalıştırmak için gerekli ortam.

### Senkron / Asenkron Örnek Senaryo
Senkron: Bir işlem bitmeden sonraki işlem başlamaz. Örneğin bir web sitesinde veritabanından kullanıcı bilgisi istenir; sistem cevabı bekler ve cevap geldikten sonra diğer işlemlere devam eder.
Asenkron: Bir işlem devam ederken program başka işlemleri yapabilir. Örneğin kullanıcı bilgisi veritabanından alınırken uygulama başka işlemleri gerçekleştirebilir; veri geldiğinde ilgili işlem devam eder.
1.	async : Bu işlem zaman alabilir, asenkron çalışabilir. der.
2.	await : Bu işlemin sonucunu bekle, sonuç gelince devam et. der.
3.	Task : Şu anda devam eden bir işlem var. bilgisini temsil eder.
4.	ConfigureAwait(false) : “İşlem bitince eski çalışma ortamına dönmene gerek yok.” demektir.
5.	=> : Kısa bir fonksiyon yazmanın yoludur. Örneğin x => x * 2 → “x'i al, 2 ile çarp.”

## 3.Backend Geliştirme Temelleri
### Backend ve Frontend:
Frontend, kullanıcının gördüğü ve etkileşimde bulunduğu arayüz kısmıdır. Örneğin HTML, CSS ve JavaScript kullanılır.
Backend, uygulamanın arka planda çalışan kısmıdır. Veritabanı işlemleri, kullanıcı girişi, API'ler ve iş kuralları burada yönetilir. Örneğin C#, .NET, Java, Python gibi teknolojiler kullanılabilir.
Web Sunucusu, API ve API Türleri
Web sunucusu, web sitelerinden veya uygulamalardan gelen istekleri karşılayan ve gerekli verileri geri gönderen sistemdir.
API, farklı yazılımların birbirleriyle iletişim kurmasını sağlayan arayüzdür. Örneğin frontend, backend'e API üzerinden "ürünleri getir" isteği gönderir ve backend verileri JSON olarak döndürür.

### HTTP ve HTTP Metodları:
HTTP, istemci (Frontend) ile sunucu (Backend) arasında veri alışverişini sağlayan iletişim protokolüdür.
GET: Veri almak için kullanılır. Örn: GET /products → Ürünleri getirir.
POST: Yeni veri oluşturmak için kullanılır. Örn: POST /products → Yeni ürün ekler.
PUT: Mevcut veriyi güncellemek için kullanılır. Örn: PUT /products/5 → 5 numaralı ürünü günceller.
DELETE: Veri silmek için kullanılır. Örn: DELETE /products/5 → 5 numaralı ürünü siler.

### RESTful servislerin çalışma mantığı nedir?
RESTful servis, istemci (Frontend) ile (Backend) HTTP üzerinden iletişim kurmasını sağlayan API yapısıdır. İstemci GET, POST, PUT, DELETE gibi HTTP metodlarıyla istek gönderir, Backend bu isteği işler ve genellikle JSON formatında cevap döndürür. Örneğin GET /products → ürünleri getirir, POST /products → yeni ürün oluşturur.

### JSON veri formatı ve kullanım amacı nedir?
JSON uygulamalar arasında veri alışverişi yapmak için kullanılan hafif ve hızlı okunabilir bir veri formatıdır. Özellikle API'lerde verileri frontend ve backend arasında göndermek için kullanılır.

#### JSON veri örneği açıklaması:
{
  "id": 1,
  "name": "Laptop",
  "price": 25000
}
Burada id, name ve price veri alanlarını; 1, "Laptop" ve 25000 ise bu alanların değerlerini ifade eder.

### SOAP ve GraphQL nedir, REST’ten farkları nelerdir ve temel karşılaştırması?
REST: HTTP metodlarını kullanarak istemci ve sunucu arasında veri alışverişi yapan, basit ve yaygın bir API yaklaşımıdır.
SOAP: XML tabanlı, belirli kurallara sahip ve daha katı bir web servis protokolüdür.
GraphQL: İstemcinin ihtiyaç duyduğu verileri kendisinin seçerek almasını sağlayan bir API teknolojisidir.

## 4.ASP.NET
### ASP.NET ve ASP.NET Core nedir? Avantajları, farkları.
ASP.NET, .NET Framework üzerinde web uygulamaları geliştirmek için kullanılan, Windows odaklı eski bir web framework'üdür; ASP.NET Core ise modern .NET üzerinde çalışan, açık kaynaklı, yüksek performanslı ve Windows, Linux, macOS gibi farklı platformlarda çalışabilen web framework'üdür. Her ikisi de web uygulaması ve API geliştirmek için kullanılır; temel fark ASP.NET'in eski ve Windows odaklı, ASP.NET Core'un ise modern ve platformlar arası olmasıdır.

### MVC nedir, ne için kullanılır?
MVC (Model-View-Controller), uygulamanın kodlarını Model, View ve Controller olmak üzere üç bölüme ayıran bir tasarım yaklaşımıdır. Model verileri ve iş mantığını, View kullanıcının gördüğü arayüzü, Controller ise gelen istekleri ve Model-View arasındaki iletişimi yönetir.

Örnek olarak MVC ile iligli: 
Kullanıcı: "Ürünleri göster." Buttonun’a basar.
Controller bu isteği alır → Model'den ürünleri ister → sonucu View'a gönderir.

### Middleware, gelen HTTP istekleri ile uygulamanın asıl işlemleri arasında çalışan ara katmandır; istekleri kontrol eder ve gerektiğinde işlem yapar. Örneğin kullanıcının giriş yapıp yapmadığını, ve yetkisini kontrol eder Middleware.

### Startup.cs ya da Program.cs içindeki middleware sıralamasının açıklaması
Middleware, ASP.NET Core'da gelen isteklerin hangi sırayla işleneceğini belirler. Örneğin UseHttpsRedirection() → HTTPS'e yönlendirir, UseAuthentication() → kullanıcının kimliğini kontrol eder, UseAuthorization() → yetkisini kontrol eder ve MapControllers() → isteği ilgili Controller'a gönderir. Sıralama önemlidir, çünkü middleware'ler yazıldıkları sırayla çalışır.

### Dependency Injection (DI), bir sınıfın ihtiyaç duyduğu başka sınıfları kendi oluşturmak yerine dışarıdan almasını sağlayan yapıdır.

#### Middleware ile ilgli akış diyagramı:
Controller
↓
"ProductService'e ihtiyacım var."
↓
DI Container
↓
"Tamam, sana ProductService veriyorum."
↓
Controller

## 5. Veritabanı ve ORM
### SQL Nedir?
SQL, veritabanındaki verileri eklemek, okumak, güncellemek ve silmek için kullanılan bir sorgulama dilidir. Örneğin SELECT ile veri getirir, INSERT ile veri ekler, UPDATE ile günceller, DELETE ile siler.



İlişkisel ve ilişkisel olmayan veri tabanları arasındaki farklari

İlişkisel veritabanları (SQL) verileri tablo, satır ve sütunlar şeklinde düzenler ve tablolar arasında ilişkiler kurar. İlişkisel olmayan veritabanları (NoSQL) ise verileri tablo yerine doküman, key-value, grafik veya kolon gibi farklı yapılarda saklar ve daha esnek bir veri yapısı sunar.

### ORM nedir? Entity Framework Core nedir? 
Örneğin veritabanında:
#### Products tablosu
----------------
Id
Name
Price

EF Core sayesinde bunu C# tarafında:
Product
{
    Id
    Name
    Price
}

Kısaca:
ORM = Veritabanı ile kod arasında köprü
EF Core = Bu köprüyü .NET'te sağlayan araç


#### LINQ (Language Integrated Query), C# içinde koleksiyonlar veya veritabanındaki veriler üzerinde sorgulama ve işlem yapmayı sağlayan yapıdır
1.	Where() : Belirli şartlara uyan verileri getirir.
2.	Select() : Verilerden istenen alanları seçer.
3.	OrderBy() : Verileri küçükten büyüğe sıralar.
4.	OrderByDescending() : Büyükten küçüğe sıralar.
5.	FirstOrDefault() : İlk uygun veriyi getirir.
6.	SingleOrDefault() : Tek bir veri bekler.
7.	Any() : Şarta uyan veri var mı kontrol eder.
8.	Count() : Veri sayısını verir.
9.	Sum() : Sayısal değerleri toplar.
10.	ToList() : Sonucu listeye dönüştürür.


#### Code-First vs DB-First karşılaştırması 
Code-First	       DB-First
Önce C# kodu	       Önce veritabanı
Kod → Veritabanı	       Veritabanı → Kod
EF Core ile veritabanı oluşturulabilir	.      Mevcut veritabanıyla çalışmak için uygundur

#### 4 temel SQL sorgusuna örnekleri:
SELECT = Getir | INSERT = Ekle | UPDATE = Güncelle | DELETE = Sil.
SELECT * FROM Products;
INSERT INTO Products (Name, Price) VALUES ('Laptop', 25000);
UPDATE Products SET Price = 27000 WHERE Id = 1;
DELETE FROM Products WHERE Id = 1;

## 6. Güvenlik ve Performans
### JWT'nin Temel Bileşenleri
1. Header: Token'ın türünü ve kullanılan şifreleme algoritmasını belirtir.
2. Payload: Kullanıcı ID'si, rolü, token'ın süresi gibi bilgileri içerir.
3. Signature: Token'ın değiştirilmediğini doğrulamak için kullanılır.
Yapısı: Header.Payload.Signature   

### Performans için önerilen en az 3 teknik ve açıklamaları:
•	AsNoTracking() → EF Core'da sadece veri okuyorsan, değişiklik takibini kapatarak sorguyu hızlandırır.
•	IAsyncEnumerable → Büyük verileri tamamen belleğe almak yerine parça parça ve asenkron işlemeyi sağlar.
•	Caching → Sık kullanılan verileri tekrar tekrar veritabanından almak yerine geçici olarak saklayarak erişimi hızlandırır.
•	Profiling → Uygulamanın hangi bölümlerinin yavaş olduğunu ölçüp tespit etmeye yarar.
•	Redis → Çok hızlı çalışan, genellikle cache olarak kullanılan bellek tabanlı veri deposudur.
Kısaca:
AsNoTracking → DB sorgusunu hızlandır
IAsyncEnumerable → Büyük veriyi parça parça işle
Caching → Veriyi hazır tut
Profiling → Yavaş noktayı bul
Redis → Hızlı cache kullan

### OWASP Top 10
Neden loglama yapılır? Log seviyesi nedir?
Loglama, uygulamada gerçekleşen olayları kaydetmek için yapılır; hata bulma, sorunları takip etme, güvenlik olaylarını inceleme ve uygulamanın durumunu izleme amacıyla kullanılır. Log seviyesi, kaydedilen olayın önem derecesini belirtir.
Yaygın log seviyeleri:
Trace: En detaylı bilgiler
Debug: Geliştirme ve hata ayıklama bilgileri
Information: Normal işlemler
Warning: Dikkat edilmesi gereken durumlar
Error: Hata oluştu
Critical: Uygulamanın çalışmasını ciddi şekilde etkileyen hata
ASP.NET Core'da logging altyapısı:
ASP.NET Core Logging: Uygulamada olan olayları ve hataları not almak/kaydetmek demektir.
ILogger: Log yazmamızı sağlayan yapı.
LogInformation: Normal bir olay olduğunu kaydeder.
LogWarning: Dikkat edilmesi gereken durumu kaydeder.
LogError: Hata oluştuğunu kaydeder.
LogCritical: Çok ciddi bir hata olduğunu kaydeder.

Logging = Uygulamada ne olduğunu ve hangi hataların oluştuğunu kayıt altına almak.

## 7.Örnek Hata Yönetimi:
try
{
    // Hata oluşabilecek kod
}
catch (Exception ex)
{
    _logger.LogError(ex, "Bir hata oluştu.");
}

try: Hata oluşabilecek kod yazılır.
catch: Hata oluşursa yakalanır.
Exception ex: Oluşan hata hakkında bilgi tutar.
ILogger: Hata bilgisini loglayarak kayıt altına alır.

## 8. Yazılım Geliştirme Prensipleri
### SOLID prensipleri, Her biri için kısa açıklama ve örnek
SOLID Prensipleri: Yazılımın daha anlaşılır, sürdürülebilir, esnek ve geliştirilebilir olmasını sağlayan 5 temel prensiptir.
1. S - Single Responsibility Principle (Tek Sorumluluk):
Bir sınıfın sadece bir sorumluluğu olmalıdır.
Örnek:
UserService: Kullanıcı işlemlerini yapar.
EmailService: E-posta işlemlerini yapar.

2. O - Open/Closed Principle (Açık/Kapalı):
Sınıflar geliştirmeye açık, mevcut kodu değiştirmeye kapalı olmalıdır.
Örnek:
Yeni bir ödeme yöntemi eklerken mevcut PaymentService kodunu değiştirmek yerine yeni bir ödeme sınıfı oluşturmak.

3. L - Liskov Substitution Principle (Liskov Yerine Geçme):
Alt sınıf, üst sınıfın yerine kullanıldığında programın çalışmasını bozmamalıdır.

Örnek:
Bird sınıfından türeyen Penguin, Bird'ün beklenen davranışlarını bozacak şekilde uçamazlık problemi oluşturmamalıdır.

4. I - Interface Segregation Principle (Arayüzlerin Ayrılması):
Bir sınıf kullanmadığı özellikleri içeren büyük bir interface'e bağlı olmamalıdır.


Örnek:
Yazıcı sadece Print özelliğine ihtiyaç duyuyorsa Scan ve Fax özelliklerini zorunlu olarak uygulamamalıdır.

5. D - Dependency Inversion Principle (Bağımlılıkların Tersine Çevrilmesi):
Sınıflar doğrudan başka sınıflara değil, abstraction/interface'lere bağlı olmalıdır.
Örnek:
OrderService doğrudan MySQLService'e bağlı olmak yerine IDatabaseService interface'ine bağlı olur.

Kısaca:
S: Tek sorumluluk
O: Geliştirmeye açık, değiştirmeye kapalı
L: Alt sınıf, üst sınıfın yerine geçebilmeli
I: Küçük ve amaca yönelik interface
D: Interface/abstraction'a bağımlı ol

### Design Patterns: Yazılımda sık karşılaşılan problemlere tekrar kullanılabilir çözüm sunan tasarım kalıplarıdır.

1. Singleton Pattern:
Bir sınıftan uygulama boyunca sadece bir tane nesne oluşturulmasını sağlar.
Örnek:
Bir uygulamada tek bir ConfigurationManager nesnesinin kullanılması.

2. Repository Pattern:
Veritabanı işlemlerini uygulamanın diğer bölümlerinden ayırır.
Örnek:
ProductRepository: Ürünleri veritabanından getirir, ekler, günceller ve siler.

3. Factory Pattern:
Nesnelerin oluşturulma işlemini merkezi bir noktaya taşır. İhtiyaca göre uygun nesneyi oluşturur.
Örnek:
PaymentFactory: Kredi kartı, PayPal veya havale için uygun ödeme nesnesini oluşturur.

Kısaca:
Singleton: Tek nesne oluştur.
Repository: Veritabanı işlemlerini ayır.
Factory: Uygun nesneyi oluştur.

### Clean Code: Okunması, anlaşılması, test edilmesi ve değiştirilmesi kolay olan temiz ve düzenli kod yazma yaklaşımıdır.
Neden önemlidir?
Kodun okunabilirliğini artırır, hataları azaltır, bakım ve geliştirme işlemlerini kolaylaştırır ve ekip çalışmasını daha verimli hale getirir.
Clean Code Uygulama Örnekleri:
1. Anlamlı isimler kullanmak:
Kötü:
int x = 25;
İyi:
int userAge = 25;
2. Fonksiyona tek bir görev vermek:
Kötü:
GetUserAndSendEmailAndSaveLog();
İyi:
GetUser();
SendEmail();
SaveLog();

3. Gereksiz kod yazmamak:
Kötü:
if (isActive == true)
İyi:
if (isActive)

4. Magic Number kullanmamak:
Kötü:
if (age > 18)
İyi:
const int MinimumAge = 18;
if (age > MinimumAge)

5. Kod tekrarından kaçınmak:
Aynı kodu birçok yerde tekrar etmek yerine ortak bir metot veya sınıf oluşturmak.


Kısaca:
Clean Code: Okunabilir, anlaşılır, sade, tekrar etmeyen ve bakımı kolay kod yazmaktır.

Yazılım Mimarileri:
1. Monolithic Architecture:
Tüm uygulama tek bir proje ve yapı içinde bulunur.
Avantaj: Basit ve geliştirmesi kolaydır.
Dezavantaj: Uygulama büyüdükçe yönetimi zorlaşır.

2. Layered Architecture:
Uygulama katmanlara ayrılır. Örneğin Controller, Service, Repository ve Database.
Avantaj: Kodun düzenli ve yönetilebilir olmasını sağlar.
Dezavantaj: Katmanlar birbirine bağımlı hale gelebilir.

3. Microservices Architecture:
Uygulama, her biri farklı bir görevi yapan küçük bağımsız servislere ayrılır.
Avantaj: Servisler bağımsız geliştirilebilir ve ölçeklenebilir.
Dezavantaj: Yönetimi ve iletişimi daha karmaşıktır.

4. Clean Architecture:
Uygulama iş mantığı merkezde olacak şekilde katmanlara ayrılır ve bağımlılıklar merkeze doğru yönelir.
Avantaj: Test edilebilir, sürdürülebilir ve esnek yapı sağlar.
Dezavantaj: Küçük projelerde gereğinden fazla karmaşık olabilir.


Kısaca:
Monolithic: Her şey tek uygulamada.
Layered: Uygulama katmanlara ayrılır.
Microservices: Uygulama küçük bağımsız servislere ayrılır.
Clean Architecture: İş mantığı merkezdedir, dış bağımlılıklar ayrıştırılır.
