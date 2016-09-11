## Dosya İzinleri
![alt text](http://i.hizliresim.com/WbGy32.png "")

Dosya izinlerinde harflerin ne anlama geldiğini açıklamıştım. İzinlerin hemen yanında dosyanın sahibi, onun yanında dosya sahibinin bulunduğu grup bilgisi daha sonra dosya boyutu ve son değiştirildiği tarih yazıyor. 
Örneğin deneme isimli bir kullanıcım var ve bu kullanıcıyı root grubuna eklemek istiyoruz.
~~~bash
usermod -g root deneme
~~~
root grubuna yazma yetkisi verelim. Dosya ve dizinlerin izinlerini değiştirmek için **chmod** komutunu kullanıyoruz.
~~~bash
chmod g+w denemedosya
~~~
Burada g - group , w - write. Gruba çalıştırma yetkisi vermek isteseydik g+x yazmamız gerekirdi. 
~~~bash
chmod o+r denemedosya
~~~
Sistemdeki tüm kullanıcıların dosyayı okuyabilmesi için o+r(others) kullandık. Dosyanın sahibine tam yetki vermek için u+rwx (user) kullanabiliriz.
Ayrıca bunları harf olarak değilde rakam olarakta yazabilirdik.
- r:4 
- w:2 
- x:1 
**Örnek:** Dosyanın sahibinin tüm yetkileri olsun, grubun sadece yazma, diğer kullanıcıların çalıştırma yetkisi olsun.
~~~bash
chmod 721 denemedosya
~~~
Burada 1 diğer kullanıcıların çalıştırma yetkisi, 2 grubun yazma yetkisi , 7 dosya sahibinin full yetkisini belirtir.

*Bir dosya oluşturduğumuzda default olarak hiçbir kullanıcıya çalıştırma yetkisi vermez.* 
~~~bash
umask
~~~
umask komutu varsayılan izinleri gösterir. 0022 varsayılan izindir. Yani 2 (write) maskelenmiş diğer kullanıcıların ve grupların yazma yetkileri yoktur. Default olarak kullanıcıların x (execute) yetkilerini de olmadığını söylemiştim. Yeni bir dosya oluşturduğumuzda karşılaşmamız gereken izinler
-rw-r--r-- şeklinde olmalıdır. Umask komutu sayesinde varsayılan izinleri değiştirebiliriz.
~~~bash 
umask 0062
~~~
umask 0062 komutunu yazdıktan sonra yeni bir dosya oluşturduğumuzda artık izinlerin rw----r-- şeklinde olduğunu görürüz. Diğer kullanıcıların yazma yetkisi maskelenmiş , grupların hem okuma hem yazma yetkisi maskelenmiştir. 

SUID,SGID, Sticky gibi kavramlardan bahsetmiştim. Peki bu izinler nasıl verilir onu öğrenelim. 
- 4 : SUID(SET USER ID)
- 2 : SGID(SET GROUP ID)
- 1 : Sticky
~~~bash
chmod 4752 denemedosya
~~~
Komutu yazdıktan sonra dosyanın izinlerinin -rwsr-x-w-. olduğunu görebiliriz. 
~~~
chmod 4652 denemedosya
~~~
Komutunu yazdıktan sonra -rwSr-x-w-. oldu. Yani dosyanın sahibine x (execute) yetkisi verirsek s, vermezsek S şeklinde gözükür.
~~~bash
chmod 2771 denemedosya
~~~
~~~bash
chmod 1777 denemedosya
~~~ 
Aynı şekilde SGID ve Sticky verebiliriz.

**inode:** Linux Sistemlerde her dosyaya/dizine özel numara vardır. Bu numara sayesinde dosyanın/dizinin harddisk üzerinde bulunduğu yeri öğrenebiliriz. inode'da bir dosyanın izinleri, sahibi, türü , bağ sayısı bilgileri tutulur. inode numaraları bittiğinde artık dosya/dizin oluşturamayız. 

**block:** Dosyaların/dizinlerin içeriğini tutar.
[FileSystem inode&block](https://www.youtube.com/watch?v=oHrlU3b1ZAw)
*videoyu izlerseniz daha iyi anlaşılır.*

## Hard Link , Soft Link 
Link iki dosya arasında bağ yaratma demektir. 
İki dosyayı birbirine **Soft Link** kullanarak bağlarsak ve bu dosyalardan birinin adını değiştirirsek yada dosyanın birini taşırsak aralarındaki bağ kopar. **Hard Link** kullanarak bağlarsak dosya taşınsa yada adı değişse bile bağ bozulmaz. Çünkü Hard Linklerde iki dosyanın tek bir inode numarası olur. Bu sayede dosyayı taşısak bile yerini bulunabilir ve bağ kopmaz. 

Örneğin home dizinimize deneme1 adında bir dosya ve dizin adında bir dizin oluşturalım. Bu dosya ve dizini linklemek istersek;
~~~bash
ln -s /home/hanife/dizin deneme1 
~~~
komutunu yazmalıyız. Önce hedef daha sonra kaynak şeklinde yazmalıyız. Şimdi cd deneme1 komutunu girelim ve ls -l (ll) yazalım. deneme1'in içerisinde dizinimizde bulunan dosyaları görebiliriz. **NOT:*** Normalde bir cd dosyaadi yazarsak hata alırız. Çünkü cd (change directory) yani sadece dizinler için kullanılır. Burada hata almamamızın sebebi dosya ve dizini birbirine linklememizdir. 
Hard link oluşturmak için bir dosya oluşturup yazı yazalım. 
~~~bash
echo "bu bir denemedir" > dosya
~~~
dosyanın içerisine *bu bir denemedir* yazdık. 
~~~bash
ln dosya2 dosya3 
~~~
NOT: dosya3 'ün daha önce oluşturulmamış olması gerekir. Komutu girdikten sonra **cat dosya3** dersek dosya2nin içerisindeki *bu bir denemedir* yazısını görürüz.

## PAKET YÖNETİCİSİ

CentOS Red Hat tabanlı olduğu için RPM Paket Yöneticisini kullanır. 
~~~bash
rpm -i dosya.rpm
~~~
.rpm uzantılı bir paketi yüklemeye yarar.
~~~bash
rpm -e dosya.rpm 
~~~
Yüklü olan bir paketi siler.
~~~bash
rpm -qa
~~~
Sistemde yüklü olan paketleri listeler.
~~~bash
rpm -qc
~~~
Paket ile ilgili ayar dosyalarını gösterir.
~~~bash
rpm -qf komut
~~~
Bir komutun hangi paketin içerisinde geldiğini gösterir.

*Bazı durumlarda bir paketi yüklemek için başka bir paketin yüklenmesi gerekir buna bağımlılık denir*
RPM paket yöneticisi kullanırken bu bağımlılıkları ezbere bilmemiz gerekir ki bu mümkün değil.
**YUM** bir paketi kurarken bağımlılıkları otomatik olarak kurar. Paketleri günceller. 
Örneğin yum ile Apache Server yükleyelim.
~~~bash
yum install httpd
~~~
~~~bash
yum remove httpd
~~~
Yüklü olan bir paketi silmeye yarar.
~~~bash
yum search httpd
~~~
İsminde yada açıklamasında httpd geçen paketleri listeler.
~~~bash
yum update httpd
~~~
Paketleri güncellemeye yarar.
~~~bash
yum provides /etc/ssh
~~~
Bir dosyanın hangi pakete ait olduğunu öğrenebilmemizi sağlar.
