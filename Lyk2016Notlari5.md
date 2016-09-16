~~~bash
wget http://images.gofreedownload.net/linux-tux-100404.jpg
~~~
İnternetten dosya indirmeye yarar. 
~~~bash
wget -c url
~~~
Yarıda kalmış bir indirme işlemine daha sonra devam etmek için  -c parametresini kullanabiliriz.

## Crontab Kullanımı ve Örnekleri 
**Crontab** belirlediğimiz zamanda istediğimiz komutların yada uygulamaların çalışmasını sağlar. Bu işlemleri /etc/crontab dosyasında yapabiliriz.
~~~bash
nano /etc/crontab
~~~
Crontab dosyamızda örnekler yapalım. Dosyada sırasıyla
- Dakika (0-59)
- Saat (0-23)
- Ayın bir günü(1-31)
- Ay(1-12) yada jan,feb,mar şeklinde yazılabilir
- Haftanın bir günü (0-6) Pazar=0 yada Pazar=7 veya sun,mon,tue şeklinde yazılabilir.
**Örnek:** 2 dakikada bir /tmp dizinine deneme adında bir dosya oluştursun. 
~~~bash
2  *  *  *  * root  touch /tmp/deneme
~~~
2 dakikada bir dediğimiz için dakika bölümüne 2 yazdık, haftanın her günü, her ay, her saat çalışacağı için diğer kısımlara * koyduk. 
**Örnek:** Haftasonları sabah 7 akşam 9 arası çalışacak crontab 
~~~bash
0  7-21  *  *  6-7 kullaniciadi  komut
~~~
**Örnek:** Her 10 dakikada bir çalışan crontab
~~~bash
*/10  *  *  *  * kullaniciadi  komut
~~~
**Örnek:** Çarşamba günleri ve her ayın 6. gününde saat 15:45 de çalışan crontab
~~~bash
45  15  6  *  3 kullaniciadi  komut
~~~
Benzer bir çok örnek deneyebilirsiniz. 

/etc/cron.deny dosyasına reddetme listesine eklemek için kullanıcı girebiliriz. 
~~~bash
systemctl restart crond.service
~~~
Cron ayarlarını sıfırlamak için komutunu girebilirsiniz.

## Dosya Arşivleme ve Sıkıştırma
~~~bash
tar
~~~
*Arşivleme dosyaları birleştirme , sıkıştırma dosyanın boyutunu küçültmek için kullanılır.*
~~~bash
tar -cf deneme.tar arsivlenecekdosya1.txt arsivlenecekdosya2.txt
~~~
tar komutu dosyaları arşivlemeye yarar. -c (create) -f (file) parametreleri yeni bir tar dosyası oluşturur.
~~~bash
tar -czf deneme.tar.gz dosya1 dosya2
~~~
-z parametresi oluşan dosyayı sıkıştırmak için kullanılır. gzip komutu ile sıkıştırır. 
~~~bash
tar -cvf deneme.tar dosya1 dosya2
~~~
-v parametresi hangi dosyaların arşivlendiğini ekranda gösterir.
~~~bash
tar -xvf deneme.tar
~~~
-x parametresi arşivden çıkarmak için kullanılır. 
~~~bash
tar -xzvf deneme.tar.gz
~~~
ziplenmiş ve arşivlenmiş dosyayı bu şekilde çıkarırız.
~~~bash
tar -tf deneme.tar
~~~
-t parametresi arşivden çıkarmadan dosyanın içerisinde bulanan dosyaları gösterir.
~~~bash
tar -rf deneme.tar dosya3.txt
~~~
-r parametresi arşivlenmiş bir dosyanın içerisine farklı bir dosya eklemeye yarar.

## SIKIŞTIRMA ALGORİTMALARI 
Kayıplı ve kayıpsız sıkıştırma olarak ikiye ayrılırlar. Kayıplı sıkıştırma verilerde bozulmaya yol açabilir. Örneğin bir JPEG dosyasını sıkıştırdığımızda sıkıştırma katsayısına göre resmin kalitesi bozulur. 
**Huffman Encoding:** Kayıpsız veri sıkıştırma tekniğidir. Daha çok metin tabanlı verilerde kullanılır.
**LZW:** Sıkıştırma oranı en yüksek algoritmalardan biridir. Kayıpsız sıkıştırma işlemi yapar.
~~~bash
gzip dosya.txt
~~~
Dosyayı sıkıştırmak için kullanılır.
~~~bash
gzip -r dizinadi
~~~
Belirtilen dizinin içindeki dosyaları tek tek sıkıştırır.
~~~bash
gunzip dosya.txt.gz
~~~
Sıkıştırılmış bir dosyayı açmak için kullanılır.
~~~bash
bzip2 dosya
~~~
gzip komutundan daha iyi sıkıştırır. 
~~~bash
bunzip2 dosya.bz2
~~~
Sıkıştırılmış dosyayı çıkarmak için kullanılır.
~~~bash
tar -cjf deneme.tar.bz2 /etc
~~~
etc dizinindeki dosyaları hem arşivler hemde bzip2 ile sıkıştırır.
~~~bash
zcat dosya.gz
~~~
Sıkıştırdığımız bir dosyayı çıkarmadan içerisini okumaya yarar.

## Dosya Arama
~~~bash
find
~~~
Dosya aramak için kullanılır.
~~~bash
find -name deneme
~~~
Adı deneme olan dosyayı arar. 
~~~bash
find -name 'deneme*'
~~~
Adı deneme ile başlayan dosyaları bulur.
~~~bash
find -name '*deneme*'
~~~
Adında deneme kelimesi geçen dosyaları bulur. 
~~~bash
find -iname deneme
~~~
Büyük küçük harfe önem vermeden arar. 
~~~bash
find /etc -type f -name 'a*'
~~~
etc dizininde türü dosya olan ve a ile başlayan dosyaları görüntüler.
~~~bash
find /etc -type d -iname '*a'
~~~
etc dizininde türü dizin olan ve a ile biten dosyaları görüntüler.
~~~bash
find -size +1M
~~~
Boyutu 1MB'den büyük tüm dosyaları gösterir.
~~~bash
find /etc -type f -iname '*.conf' | xargs tar -czf conf.tar.gz
~~~
etc dizinindeki .conf uzantılı dosyaları hem arşivlemer, hemde sıkıştırır. 
~~~bash
find /etc -type f -iname '*.conf' >> /tmp/conf
~~~
etc dizinindeki .conf uzantılı dosyaları tmp dizininde conf adında dosyaya yazar.
~~~bash
find -delete
~~~
Bulunduğumuz dizinin içerisindeki her şeyi siler.
~~~bash
find -user kullanici
~~~
Belirttiğimiz kullanıcının dosyalarını gösterir.
~~~bash
find -empty
~~~
Boş dosyaları gösterir.
