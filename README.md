# haar-cascade-algoritmas-yuztanima-uygulamas-
Haar Cascade Algoritması ile Yüz Tanıma Uygulaması 

ÖZET

GİRİŞ
Yüz tanıma uygulamaları, insan yüzünün özelliklerini tarayan ve bu özellikleri bir veritabanında saklayan bir yöntemdir. Bu uygulamalar, insan yüzünün özelliklerini taramak suretiyle kişinin kimliğini doğrulamaya yarar. Yüz tanıma uygulamaları, güvenlik amacıyla kullanılabilir. Örneğin, bir bina girişinde yüz tanıma sistemi kullanılabilir, bu sayede sadece yetkili kişilerin girişine izin verilebilir, kişinin kimliğinin doğrulanmasında da kullanılabilir, bir sınav sırasında yüz tanıma sistemi kullanılabilir, bu sayede sadece yetkili kişinin sınava girişine izin verilebilir. Manuel işlemlerden daha hızlıdır. Örneğin, bir sınav sırasında manuel olarak kişinin kimliğinin doğrulanması zaman alabilir. Ancak yüz tanıma sistemi kullanıldığında, kişinin kimliği anında doğrulanabilir. Yüz tanıma uygulamaları, manuel işlemlerden daha günceldir. Örneğin, bir kişinin pasaportunun çalınması durumunda, manuel olarak bu kişinin kimliğinin doğrulanması zor olabilir. Ancak yüz tanıma sistemi kullanıldığında, bu kişinin kimliği anında doğrulanabilir.
Zamanın ilerlemesiyle birlikte yüz tanıma sistemleri de artmıştır. Yüz tanıma yapay zekâsı bulunan bir cihazda kişinin kameraya yüzünü göstererek, kameranın, kişinin yüzünü tanıması sağlanır. Bu işlem cihazın donanımsal ve yazılımsal parçalarının birlikte çalışmasıyla sonuç verir. Cihazın içinde bulunan kızıl ötesi ışınların gönderilip geri gelmesiyle yüz derinliği ölçülerek yüz tanıma yapılması, görüntünün alınacağı kameranın kendisi donanıma örnektir. Google’ın geliştirmiş olduğu ML Kit SDK’sı, Opencv ve RetinaFace gibi kütüphaneler yüz tanıma yapabilen yazılım teknolojileridir. Yazılım alanındaki bu kütüphaneler farklı tür cihazlar üzerinde çalışabilir. Örneğin ML Kit mobil uygulamalarda kullanılmak üzereyken Opencv çapraz platformlarda çalışmaktadır. Bu yapay zekanın telefon, bilgisayar ve diğer cihazlarda çalışması için cihaza uygun kütüphanenin kullanılması gerekir.
Opencv (Open Source Computer Vision, anlamı Açık Kaynak Bilgisayar Görüsü Kütüphanesi) gerçek-zamanlı bilgisayar görüsü uygulamalarında kullanılan, intel aracılığıyla geliştirilmiş bir yazılımdır. Yüz tanıma, nesne tanıma, hareket tanıma, hareket takibi, insan-bilgisayar etkileşimi gibi uygulama alanları bulunur. Bu uygulamalardan bazılarını geliştirmek için Opencv yazılımında bir makine öğrenimi kütüphanesi bulunur. Aslen C++ yazılım dili ile yazıldığından yeni geliştirilmiş algoritmalar ve özellikler c++ arayüzüne eklenir. Ama önceki yazılım dili C’nin de daha kısıtlanmış bir arayüzü bulunur. Çapraz platform olduğundan Python, Java, C#, Ruby, Perl, Haskell ve MATLAB ile bağları bulunur (1). Kütüphanenin içinde Michael Jones ve Paul Viola tarafından geliştirilen, resim ve video içinde bulunan nesneyi tespit eden, Haar-Cascade sınıflandırıcı algoritması bu çalışmada gerçek zamanlı yüz tespiti için kullanılacaktır. 
Bir insanın yüzündeki farklılıklar her insana özgüdür. Yüzdeki göz bölgesi, yanak bölgesine göre çukurda kaldığı için daha karanlıktır. Yüz üzerindeki bu gibi özellikler her insanda aynıdır. Bu benzerlikler yüz tespitinde haliyle kullanılabilir. (2)
Haar-Cascade algoritmasında görüntüde aranan nesneyi tespit etmek için siyah beyaz renkte dikdörtgenler bulunur. Pozitif resim nesneyi içinde bulunduran, negatif resim ise içinde aranan nesneyi bulunmayanı temsil etmektedir. Pozitif resmin içinde bu dikdörtgenler her pikseli kaçırmayacak şekilde kaydırılır. Kaydırılırken dikdörtgenin altında bulunan piksellerin yoğunluklarının farkı yüzün tespit edilmesini sağlar (3).

 
Şekil 1:Resim taranırken kullanılan siyah beyaz dikdörtgenler

Tespit edilen yüzün veritabanına saat bilgisi ile birlikte kaydedilmesi kurumlarda güvenlik, giriş-çıkış kontrolüne kolaylık sağlayacaktır. Görüntünün alınacağı cihazın uzaktan bağlantı ile algoritmanın çalıştığı cihaz arasında bağlanması, büyük bölgelerde tek bir kontrol noktasıyla bütün kameralardan gelen verilerin saklanması, iç mekanların yanında dış mekanlarda iş yükünü çok büyük ölçüde azaltacaktır. Şu anda kullanılan kameralar 7/24 görüntü kaydetmektedir. Kaydedilen bu görüntüler kameranın çözünürlüğü arttıkça saklanan verinin boyutunu arttırmaktadır. Bu veriler video şeklinde olduğu için boyutu yüksektir. Bu çalışmada yüz tespit edildiğinde çalışan bir fonksiyon olacağı için sürekli görüntü kayıt edilmez. Yüz tespiti gerçekleştiğinde görüntü veritabanına resim olarak kaydedildiği için boyut video kayıtlarına göre daha düşük olacaktır ve yüksek boyutlu veritabanı gereksinimini çözecektir. Ayrıca bu algoritma öğretilen her nesneyi tanıyabildiğinden trafik vb. birçok uygulamalarda kullanılabilir. Algoritmanın çalışma prensibini anlamak, tespit edilen yüzün istenilen amaçta kullanımına yardımcı olacaktır.
Çalışmada bu teknolojileri Python yazılım dilini kullanarak, tespit edilen yüzleri firebase veritabanına saat bilgileri ile birlikte kaydeden program geliştirilmiştir. Görüntü uzaktan programa bağlanan kamerayla alınacaktır.
Programın yazımında ilk başta gerekli opencv kütüphaneleri eklendi. Firebase veritabanı storage hizmeti kullanıldığından veritabanı bağlantıları hizmete uygun şekilde yazıldı ve gerekli kütüphaneler eklendi. Önceden eğitilmiş yüz tanıma için gerekli olan önyüz tanıma dosyası eklendi. Bu dosya ile gelen görüntüde işlenen resimler karşılaştırılır ve eğer örtüşüyorsa yüz tespit edilmiş demektir. Görüntü gri skalaya çevrilir bu işlem resimdeki karanlık ve açık renkli bölgelerin tespiti için gereklidir. Tespit edilen yüzün çevresi bir dikdörtgen ile çevrilir. Dikdörtgen ile çevrildiğinde kameradaki o anki görüntü bilgisayara kayıt edilir ve zaman bilgisi alınır. Kaydedilen bu görüntü veritabanına (firebase) zaman bilgisi ismiyle kayıt edilir. Veritabanına firebase sitesinden giriş yaptığımızda yakalanan görüntüler storage arayüzünde gözükmektedir.
Makalede, materyal ve yönetim bölümünde ilgili projemizin ayrıntıları ile baştan sonra yapılışı, bulgular bölümünde, algoritmanın kullanılması sonucunda elde ettiğimiz verileri, sonuç bölümünde projenin başarı ölçütüne yer verilmiştir.


MATERYAL VE YÖNTEM

Proje kişilerin sınıfa işyerine vb. odalara girişini yüz tanıma yaparak tespit edip giriş saatlerini yüz bilgisi ile birlikte kaydedip rapor verecektir.
Projede kullanılacak teknolojiler: Python, Java, OpenCV kütüphanesi, Haar-cascade sınıflandırıcı algoritması, Firebase, VS Code
OpenCV gerçek-zamanlı bilgisayar görüsü uygulamalarında kullanılan açık kaynaklı kütüphanedir. Haar-cascade sınıflandırıcı algoritması; dijital bir resim ya da video karesi içerisinde bulunan belirli bir nesnenin tespit edilmesi amacıyla kullanılmaktadır. Haar-cascade OpenCV kütüphanesi içerisinde bulunuyor. Bu algoritma ile yüz tanıma gerçekleştirilecektir. Yüz bilgisi ile o anki saat firebase veritabanına kaydedilecek ve gün sonunda rapor halinde bu saatler yüz bilgisiyle beraber kullanıcıya teslim edilecektir.
Projenin gelişiminde Python kullanarak bilgisayar kamerasını açıp görüntü almayı sağlamaktayız. Bunun için opencv kütüphanesini kuruyoruz. Opencv kütüphanesinde bulunan cv2.VideoCapture(0) komutu ile bilgisayar kamerasına ulaşabiliyoruz. Bunu bir değişkene attıktan sonra read() fonksiyonu ile görüntüyü okuyoruz sonra cv2.imshow(“Kamera”,img) kodu ile okuduğumuz görüntüyü ekrana yansıtabiliriz.
 
Şekil 2:Kameradan görüntü okunması ve görüntünün ekrana yansıtılması
 
Şekil 3:Alınan görüntü
Alınan bu canlı görüntüyü haar-cascade sınıflandırıcı algoritmasını kullanarak tarayıp yüz tanımasını gerçekleştirebiliriz.
Projede haar cascade algoritmasının nesne tespiti için pozitif ve negatif resimlerin sınıflandırıcıya tanıtılmış hazır xml dosyalarını kullanacağız. Yüz tanıma dosyası olan haarcascade_frontalface_alt.xml dosyasını github’tan proje dizinine ekliyoruz. Bu xml dosyasını bir kullanmak üzere bir değişkene aktarıyoruz. Sınıflandırıcı siyah ve beyaz renklerin üzerinde algoritmasını çalıştırdığın için kameradan alınan görüntüyü siyah beyaza çevirmeliyiz. detectMultiScale fonksiyonu tespit edilen yüzlerin (x,y,w,h) konum bilgisini tutmaktadır. Bu fonksiyonu kullanarak tespit edilen yüzün bilgilerini değişkene aktarıyoruz. Bu değişkenin içindeki konum bilgilerine erişerek yüzü bir dikdörtgen arasına alıp bu görüntüyü ekrana yansıtıyoruz. Artık gerçek zamanlı yüz tanıma yapabilmekteyiz.

 
Şekil 4:Yüz çevresinde oluşturulan dikdörtgenin kaynak kodu
 
Şekil 5:Yüz çevresinde oluşan dikdörtgenin görüntüsü
Gerçek zamanlı tespit edebildiğimiz yüzü veritabanına atmaya çalışacağız. Firebase storage hizmetini aktif hale getirip projenin firebase bağlantılarını yapmalıyız.
Proje için gerekli olan firebase storage hizmetini aktif hale getirdik. Daha sonra projenin veritabanı bağlantılarını yaptık. Yüz tanındığında bu yüzü jpg/png formatında veritabanına kaydedeceğiz.
	Proje çalıştırıldığında yüz tanınması esnasında diktörgen oluşuyordu bunu opencv kütüphanesinin cv2.rectangle komutu ile gerçekleştiriyoduk. Eğer dikdörtgen mevcut ise yüz tanınması yapılıyordur. Bu diktörgen oluştuktan sonra veritabanına ekran görüntüsünü atma işlemlerini gerçekleştirecek kodu yazdık. While döngüsünün içinde çalıştığımız için veritabanına kayıt sürekli oluyordu bu durum yüz tanındığında aynı kişinin onlarca fotoğrafının veritabanına atılmasına sebep olur. Time kütüphanesindeki sleep() fonksiyona belirli bir zaman vermek yüz tanımasından sonra belirtilen zaman içerisinde yüz tanımayı engelleyeceği için bu soruna çözüm olacak ve veritabanı yükünü azaltacaktır.
Proje kodları:
 
Şekil 6:Veritabanı kayıt metodu

 
Şekil 7:Firebase Storage (Veritabanı) görüntüsü
Veritabanına gelen fotoğrafın saat bilgileri mevcut bunu giriş saati bilgisi olarak kullanabiliriz. Veritabanına gelen fotoğrafların dosya isimlerinin birbirinden farklı bir şekilde kayıt edilmesini sağlayabiliriz.
Gerçek zamanlı yüz tespiti için kullanılacak kamerayı değiştiriyoruz. Bilgisayar kamerasından aldığımız görüntü ip webcam üzerinden alınacak. Google Play Store’da bulunan IP Webcam uygulaması telefon kamerasını ip webcam’e dönüştürüyor. İki cihazın internete bağlı olması yeterlidir. Uygulama üzerinden server başlatıyoruz ve bize ip bilgileri veriyor. Proje kodlarında yapılan değişiklik şu şekilde:
 
Şekil 8:Kamera girişinin değiştirilmesi
	Görüntünün alındığı kaynağı uygulamanın verdiği adres ile değiştirip görüntüyü video olarak alacağımızı belirtiyoruz ve program başlatıldığında telefondaki görüntü geliyor. Veritabanı ile olan bağlantı işlemlerimiz bitmişti. Görüntü kaynağının değiştirilmesi bu işlemlerimizi etkilemiyor. 
Görüntünün telefon kamerasından alınması:
 
Şekil 9:Görüntünün telefondan görünüşü
 
Şekil 10:Görüntünün bilgisayardan görünüşü
Bulgular
	Haar cascade algoritması görüntülerdeki, belirli bir nesnenin varlığını tespit edilmesinde kullanılabilir. Bu algoritma, önceden eğitilmiş bir veri kümesi kullanarak görüntülerdeki nesneleri tanımlar ve daha sonra bu veri kümesinden öğrendiği bilgileri kullanarak yeni görüntülerde aynı nesnenin varlığını tespit etmeye çalışır. Haar cascade yöntemi, görüntülerdeki nesneleri tanımlamak için matematiksel araçları kullanır ve bu araçlar, görüntülerdeki nesnelere ait özellikleri belirlemek için kullanılır. Haar cascade yöntemi, bu özellikleri kullanarak görüntülerdeki nesneleri tanır ve böylece görüntülerdeki nesnelerin varlığını tespit eder.
Projede veri kümemizde önceden tanımlanmış yüz verileri vardı. Bu yüz verilerini algoritma sayesinde tespit edebildik. Yüzün tespit edilmesinden sonra veritabanı kayıt işlemlerini gerçekleştirdik. Bu projede görüntüyü opencv kütüphanesiyle aldık diğer işlemler için farklı kütüphaneler kullandık. Opencv kütüphanesi, telefon, tablet, bilgisayar, ip kamera gibi cihazlardan alınan görüntüyü haar cascade algoritması ile işleyebilir, bu işlem sonrasında tek bir kütüphaneye bağlı kalmaksızın isteğe göre başka işlevler gerçekleştirebilir.
Haar cascade algoritması, birçok farklı alanda kullanılabilir. Örneğin, görüntülerdeki yüzlerin tespiti, hava trafik kontrol sistemlerinde uçakların tespiti, video güvenlik sistemlerinde insanların tespiti gibi birçok farklı alanda kullanılabilir. Bu yöntem, çok hızlı ve etkili bir şekilde çalıştığı için, görüntü işleme alanında tercih edilebilir.

Sonuç
	Haar cascade, yüz tespiti gibi nesne tespiti görevlerinde kullanılan makine öğrenimi algoritmalarıdır. Algoritma, pozitif ve negatif görüntüler seti üzerinde bir sınıflandırıcı eğitir ve ardından bu sınıflandırıcıyı yeni görüntülerde nesneleri tespit etmek için kullanır.

Proje bağlamında, Haar cascade sınıflandırıcısı ile pozitif görüntüler (yüzlerin görüntüleri) ve negatif görüntüler (yüzler olmayan görüntüler) setinde eğitilmiş yüz verilerini tespit edebildik. Sınıflandırıcı, görüntülerde yüzleri tespit etmek için görüntünün piksel değerlerinde yüzleri belirleyen desenler aramaya çalıştı. Tanımlanan yüz verisi ile aranan yüz verisi eşleştiğinde, tespit edilen yüzü, kare içerisine aldı ve tespit tamamlanmış oldu.

Haar cascade algoritmasının yüz tespiti için başarısı genellikle doğru pozitif ve doğru negatif tahminlerin oranı ile ölçülür. Haar cascade algoritmasının performansını etkileyebilecek diğer faktörler, eğitim verisinin boyutu ve kalitesi, sınıflandırıcının karmaşıklığı ve sınıflandırıcının görüntüleri işleyebildiği hızdır. Proje kapsamında algoritmanın performansını etkileyen bazı faktörler oldu bunlar:
	
Öğrenme verisi:
Algoritmanın öğrenme verisi olarak kullanılan yüz görüntülerinin niteliği, çeşitliliği ve sayısı, algoritmanın performansını etkilemiştir. Daha çok ve daha çeşitli öğrenme verisi kullanılırsa, algoritmanın nesne tespiti yapma yeteneği daha iyi olacaktır.

Öznitelikler:
Algoritma öznitelikler adı verilen özellikleri kullanarak nesneleri tanımlar. Bu özniteliklerin doğru seçilmesi ve öğrenilmesi algoritmanın performansını etkilemektedir.

Tespit parametreleri:
Algoritmanın yüz tespitinde kullanılan parametreler de algoritmanın performansını etkilemiştir. scaleFactor parametresi, tarama işleminin ne kadar hassas olacağını belirler. Bu parametrenin değeri, nesnenin ölçeklenmesine ne kadar duyarlı olacağını belirler. Düşük bir değer daha hassas bir tarama işlemi anlamına gelecektir, ancak bu da işlem hızını düşürebilir. Proje dahilinde bu parametre uygun değerde kullanılmıştır. MinNeighbors parametresi, tespit edilen nesnenin gerçek bir nesne olup olmadığını doğrulamak için kullanılır. Bu parametrenin değeri, tespit edilen nesnenin etrafında kaç tane benzer nesne olması gerektiğini belirler. Bu sayının yüksek olması, tespit edilen nesnenin gerçek bir nesne olma olasılığını arttıracaktır.

Görüntü özellikleri: 
Algoritmanın tespit etmeyi hedeflediği nesnelerin görüntülerinin özellikleri de algoritmanın performansını etkilemiştir. Örneğin, nesnenin yüzünün önünde bir engel olması, nesnenin parçalı görünmesi gibi durumlar algoritmanın performansını düşürmüştür.


