# Linux Yaz Kampı 2016 Notları

*Linux, Unix’e fikirsel ve teknik anlamda atıfta bulunarak geliştirilmiş; açık kaynak kodlu, özgür ve ücretsiz bir işletim sistemi çekirdeğidir. İster Sanal Makine üzerine isterseniz Ana Makinenize kurabilirsiniz.* 

[Virtual Box'a nasıl kurulur?](http://ferhatyildiz.com.tr/index.php/egitimler/mail-sunucular/mail-sunucu-makaleleri/197-oracle-vm-virtualbox-ile-centos-7-kurulumu)
[Windowsun yanına Ubuntu Kurulumu](http://www.fulloyun.com/f95/tek-pc-ye-linux-ve-windows-kurmak-resimli-anlatim-17131/)

**NOT:** LYK'da makinemize Centos kurduk. Windowsta disk bölümlendirmeyi anlattığı için bu linki paylaştım. Flash Belleğinizin içerisine Centos 7 isosunu atarsanız 1. linkteki gibi kurabilirsiniz.
Iso dosyasını Rufus kullanarak atmak gerekir.

## Terminal Nedir?

Terminal, bir kullanıcının komutlar yazarak bilgisayarla iletişime geçtiği ortamdır. Dağıtımlara göre bazı komutlar farklılık gösterebilir.

##Temel Linux Komutları 
~~~bash
ls 
~~~
ls komutu bulunduğumuz dizin içerisindeki dosya ve klasörleri listeler. 
~~~bash
ls -l
~~~ 
Dosyaların boyut tarih bilgilerini göstererek listeler. Bir komuttan sonra - ile başlayan bir komut kullanımı parametre olarak adlandırılır. Burada ls komutunun l parametresini gördük. 
~~~bash
ls -a
~~~ 
Gizli dosyalar ve dizinler ile birlikte listeler.
~~~bash
clear
~~~ 
Terminal ekranımızı temizler. Kısayolu Ctrl+l 'dir.
~~~bash
echo
~~~
Ekrana yazı yazdırmaya yarar. Örneğin "echo hanife" yazdığımızda ekrana "hanife" yazar.
~~~bash
echo $SHELL 
~~~
Hangi terminalde olduğumuzu gösterir.
~~~bash
touch DOSYA_ADI
~~~
Dosya oluşturmaya yarar.
**NOT**: Varolan bir dosyayı tekrar touch DOSYA_ADI şeklinde yazarsak dosyanın oluşturulma saatinin değiştiğini görebiliriz. (ls -l ile)
~~~bash
touch dosya1 dosya2 
~~~ 
Birden fazla dosya oluşturmak için dosya isimlerini yan yana yazmamız yeterlidir.
~~~bash
mkdir DİZİN_ADI
~~~
Dizin oluşturmaya yarar.
~~~bash
mkdir DİZİN1 DİZİN2
~~~
Aynı anda birden fazla dizin oluşturmak için yan yana yazabiliriz.
**Dosya nedir , dizin nedir ** diye soracak olursanız dosya txt,jpg,mp3 olarak, dizin ise klasör olarak düşünebilirsiniz.
~~~bash
pwd
~~~
Bulunduğumuz dizin bilgisini verir.
~~~bash
rm dosya_adi
~~~
Oluşturduğumuz dosyaları silmeye yarar. Sildikten sonra "silindi" şeklinde bir cevap gelmediği için yaptığımız işlemler sonrasında ls komutunu kullanarak kontrol edebiliriz.
~~~bash
rmdir dizin_adi
~~~
Dizinleri silmek için kullanılır ancak dizinin içerisi doluysa hata verir.
~~~bash
rm -r dizin_adi
~~~
İçerisi dolu olan bir dizini silmek için -r parametresini kullanırız. 
~~~bash
cd dizin_adi
~~~
Dizinler arası geçiş yapmaya yarar. Örneğin dizin1 ve dizin2 adında 2 tane dizinimiz olsun. cd dizin1 komutu ile dizin1 'e geçiyoruz. Fakat daha sonra dizin2 'ye geçmek için cd dizin2 komutunu kullandığımızda hata alacağız. Bunun nedeni dizin1'in içerisindeyken cd dizin2 dememizdir. 

**cd yazıp dizin_adi belirtmezsek bizi home dizinimize yönlendirir.Daha sonra home dizininin ne anlama geldiğini anlatacağım. Şuanlık kodlarımızı yazarken burda olduğumuzu bilelim. ~ işaretinden anlayabilirsiniz.** 
~~~bash
cd ../dizin2
~~~
Buradaki .. bir üst dizini belirtir. Bu şekilde dizin2'ye ulaşmış oluruz.
~~~bash
mv dosya1 yenidosyaadi
~~~
mv komutu dosya ismini değiştirmemizi ve ayrıca dosyayı taşımamızı sağlar.Bu şekilde kullandığımızda varolan dosya1 isimli dosyayının adını yenidosyaadi yapar. 

-Home dizinimizde **(~)** iki tane dizinimiz olsun. dizin1 ve dizin2. 
dizin1'in içerisinde **tasinacakdosya** adında bir dosya olsun ve bunu dizin2'ye taşıyalım. 
-Bunun için cd dizin1 diyerek dizin1'e geçebiliriz.Daha sonra aşağıdaki komutu kullanabiliriz.
~~~bash
mv ./tasinacakdosya ../dizin2
~~~
Bu komutun anlamı : dizin1'in içerisindeki **(. şuan bulunduğum dizin)** tasinacakdosya adlı dosyayı al bir üst dizindeki **(..)** dizin2 isimli dizine taşı.

-Aynı işlemleri ilk başta dizin1'e geçmeden de yapabiliriz.
~~~bash
mv dizin1/tasinacakdosya dizin2
~~~
Hangisi daha kolayınıza gelirse :) 
~~~bash
cp dosya1 kopya
~~~
Bir dosyayı kopyalamaya yarar. 
-Farklı bir dizine kopyalama:
~~~bash
cp dosya1 dizin2/kopya
~~~
Ben dizin2'nin içerisine kopyaladım siz başka bir yere de kopyalayabilirsiniz.
~~~bash
uptime
~~~
Sisteme ne kadar süredir bağlı olduğumuzu gösterir.
~~~bash
reboot
~~~
Reset atar. Ctrl+R kısayoludur.
-Linux'un en önemli komutu man'dir. 
~~~bash
man komut
~~~
Bilgi edinmek istediğimiz komutun nasıl kullanıldığı ve komutun ne işe yaradığı gibi bilgilerin olduğunu gösterir. Komutun sahip olduğu tüm parametreleri ve anlamlarını açıklar. Bu komut sayesinde Linux hakkında hiçbir bilgisi olmayan kişiler rahatlıkla Linux kullanabilir.









 




