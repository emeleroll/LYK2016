~~~bash
groups
~~~
Üyesi olduğumuz grupları gösterir.
~~~bash
id
~~~
Üyesi olduğumuz grupları, kullanıcı id ve grup idlerini görmemizi sağlar.
~~~bash
who
~~~
Sisteme bağlı olan kullanıcıları ve bağlandıkları saati gösterir.
~~~bash
cat /etc/shells
~~~
Kullanabileceğimiz terminalleri gösterir.
~~~bash
chsh
~~~
Kullandığımız terminali değiştirmeye yarar.
## DOSYANIN İÇERİSİNDE ARAMA YAPMA
~~~bash
grep 
~~~
Bu komutla dosyanın içerisindeki herhangi bir kelimeyi arayabiliriz. 
"bilgisayar" adında bir dosya oluşturup içerisine şu cümleyi yazdım: "Bilgisayar, kendisine verdiğimiz bilgileri istediğimizde saklayabilen, istediğimizde geri verebilen cihaza denir. İlk elektrikli bilgisayar ENIAC'tır."
~~~bash
grep "elektrik" bilgisayar
~~~
Bu komut bilgisayar isimli dosyanın içerisinde elektrik kelimesini bulur. Bulunan kelime kırmızı renk ile gösterilir.
~~~bash
grep "ELEKTRIK" bilgisayar
~~~
Büyük harflerle yazdığımızda hiçbir işe yaramayacaktır çünkü büyük harfle yazılmış ELEKTRIK kelimesi yoktur.
~~~bash
grep -i "ELEKTRIK" bilgisayar
~~~
-i parametresi ile büyük-küçük harf ayrımı yapmadan yazdığımız kelimeyi bulabiliriz.
~~~bash
grep -i "^b" bilgisayar
~~~
"^" satır başında arama yapmamızı sağlar. ^b yazdığımızda b/B ile başlayan satırları görüntüler.
~~~bash
grep " $" bilgisayar
~~~
"$" satır sonunda arama yapar. " $" satır sonunda boşluk olan satırları görüntüler. 
~~~bash
grep "g.r." bilgisayar
~~~
"." tek bir karakteri ifade eder. Yazdığım cümlede geri kelimesini bulur. Fakat dosyanın içerisinde gari diye bir kelime olsaydı onu da bulacaktı. 
~~~bash
grep ".*" bilgisayar
~~~
Dosyanın tüm içeriğini görüntüler.
~~~bash
grep "^$" bilgisayar
~~~
Boş satırları görüntüler.
~~~bash
grep "^$" bilgisayar | wc -l
~~~
Boş satır sayısını öğrenebiliriz.
~~~bash
grep -v "^$" bilgisayar
~~~
-v parametresi inverse işlem yapar. Boş olmayan(dolu) satırları görüntüler.
~~~bash
grep -B 1 "cihaz" bilgisayar
~~~
-B parametresi "cihaz" kelimesinin geçtiği satırı ve 1 önceki satırı görüntüler.
~~~bash
grep -A 1 "cihaz" bilgisayar 
~~~
-A parametresi "cihaz" kelimesinin geçtiği satırı ve 1 sonraki satırı görüntüler.
~~~bash
grep -C 1 "cihaz" bilgisayar
~~~
-C parametresi "cihaz" kelimesinin geçtiği satırı ve hem 1 önceki satırı hemde 1 sonraki satırı görüntüler.
~~~bash
grep -c "bilgi" bilgisayar
~~~
-c parametresi içerisinde bilgi kelimesi geçen kelimeleden kaç tane olduğunu gösterir.
~~~bash
grep -n "bilgi" bilgisayar
~~~
"bilgi" kelimesinin kaçıncı satırlarda geçtiğini görebiliriz.
~~~bash
grep -w "bilgi" bilgisayar
~~~
-w parametresi "bilgi" yazdığımızda sadece bilgi kelimesini arar. Dosyanın içerisinde "bilgi" kelimesi olmadığından hiçbir şey bulamaz.
Dosyamızın sonuna "senle senden seni senin" yazalım.
~~~bash
grep -E -i "sen(le|in|de)" bilgisayar
~~~
-E parametresi "()" gibi karakterleri kullanmamıza yarar. "senle/senin/sende" kelimelerini aratabiliriz.
~~~bash
dmesg
~~~
Çekirdeğin kayıplarını gösterir.
~~~bash
dmesg | grep -E "(s|h)d[a-z]" 
~~~
dmesg çıktısındaki sda/sdb/hda gibi kelimeleri gösterir. 

## NETWORK - 101 
**Network:** Bilgisayar, yazıcı, kamera ve faks gibi çeşitli cihazların mevcut kaynakları ortak kullanımına olanak sağlayan ve veri iletimi gerçekleştiren yapılara ağ (network) denir. Ağ bağlantısı aynı mekandaki cihazlar arasında gerçekleştirilebileceği gibi, şehirler, ülkeler ve kıtalar arası ağ bağlantıları da kurulabilir.
**İnternet:** Birbiriyle tüm dünya üzerinde yayılmış bilgisayar ağlarının birleşiminden oluşan devasa bir bilgisayar ağıdır.
**LAN (Local Area Network):** LAN’larda temel amaç, aynı yapı içinde kullanılan bilgisayarların bazı donanımları paylaşmasını, ortak çalışma ortamını sağlayarak zamandan tasarruf edilmesi sayesinde bilginin hızlı bir şekilde okunması ve işlenmesini sağlamaktır.
**PAN (Personal Area Network):** PAN kişisel cihazların birbiriyle bağlanması sonucu elde edilen kişisel ağdır. (Telefon , USB gibi)
**WAN (Wide Area Network):** LAN'ların birbirlerine bağlanmasını sağlayan çok geniş ağlardır. 
**MAN (Metropol Area Network):** MAN genellikle bir şehir veya geniş bir yerleşkede kullanılan bilgisayar ağıdır. Bir MAN, genellikle fiber optik bağlantılar gibi yüksek kapasiteli backbone teknolojisini kullanarak Lan lar arasında bağlantı kurar, internet ve WAN için bağlantı hizmetleri sağlar.
**OSI Referans Modeli:** Verinin, kullanıcının uygulamasından kablolara giden iletişim paketinin hangi aşamalardan geçeceğini tanımlayan sistemdir.
7 katmandan oluşur.
- Uygulama Katmanı
- Sunum Katmanı
- Oturum Katmanı
- Taşıma Katmanı
- Ağ Katmanı
- Veri İletim Katmanı 
- Fiziksel Katman

[OSI Katmanları ve Açıklamaları](http://www.tercih.itu.edu.tr/seyirdefteri/blog/2013/09/07/osi-katmanlar%C4%B1)

**TCP/IP:** Veri transferi için kullanılan protokoldür. 4 katmandan oluşur.
- Uygulama Katmanı 
- Taşıma Katmanı 
- Ağ Katmanı 
- Fiziksel Katman 

**Uygulama katmanı:** Bu katmanda gönderilecek veri tipi ve veriyi işleyen uygulamalar bulunur. Örneğin bir HTML web sayfası ve bu veri tipini kullanan HTTP protokolü bu katmandadır. OSI modelindeki sunum ve oturum katmanları TCP/IP modelinde uygulama katmanı içerisinde yer alır. E-Posta gönderimi için kullanılan SMTP ve dosya gönderimi için kullanılan FTP protokolleri bu katmanda bulunur.

**Taşıma katmanı:** Bu katmanda verinin nasıl gönderileceği belirlenir. Veri güvenliği, hata kontrolü gibi işlemler yapılır. TCP ve UDP bu katmandadır. TCP klasik veri aktarımında UDP ise medya aktarımında kullanılır. TCP, UDP ye göre daha güvenli fakat daha yavaş çalışır. Çünkü TCP 'de gönderilen her veri paketinin ardından verinin yerine doğru bir şekilde ulaşıp ulaşmadığı kontrol edilir.

**Ağ katmanı:** IP katmanı olarak da adlandırılan bu katman da verilerin gideceği adres veriye eklenir yani veri bu katmandan gönderilir ve yönlendirilir. IPv4 ün gelecekte yetersiz kalma durumuna karşı IPv6 sistemine geçmek için çalışmalar başlatılmıştır.IPv4 32 bit iken IPv6 ile 128 bitlik adresler kullanılacak. Bu sayede daha fazla cihaza IP adresi atanabilecek.

**Fiziksel katman:** Bu katman verinin hangi yolla gönderileceği belirlenir. İletişim ortamının özelliklerini, haberleşme hızını ve kodlama şemasını belirler. Ethernet, Wi-Fi, Token Ring, ATM gibi protokoller bu katmanda çalışır.

**Port:** Aynı ip üzerinde birden fazla servis verebilmek için port kullanılır.
**Protocol:** Bilgisayarlar arası iletişimi yönetirler.
**DHCP:** Ağdaki bilgisayarlara otomatik ip veren protokoldür.
**ICMP:** Ağ geçitlerinde hata raporlama için kullanılan protokoldür.
**DNS:** Alan Adı isimlerini IP’ye çevirmek için kullanılan bir sistemdir. Örnek : 192.168.70.110 yerine www.google.com domain adresini yazmak gibi. 
**Gateway:** Farklı ağı kullanan iki bilgisayar arasında veri çerçevelerinin iletimini sağlar. 
**Broadcast:** Ağdaki bilgisayarların çevresini tanımak için yaydığı sinyaller bütünüdür. Başka bilgisayarlarla iletişimimizi sağlar.
**NAT:** Ağ içerisinde kullanılan bir IP adresinin baska bir network içerisinde bilinen baska bir IP adresine çevirilmesidir.
**Netmask:** Bir adres alanını subnetlere böler. 
**Subnet:** Kullandığımız ipler boşa gitmesin diye küçük küçük ağlara bölme işlemidir.
 
