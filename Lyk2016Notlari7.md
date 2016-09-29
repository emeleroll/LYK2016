## SED (STREAM EDITOR)
Bir dosyanın içerisindeki arattığımız metni bulup başka bir metinle değiştirmeye yarar.
Bir dosya oluşturalım ve içerisine 

Fatih elmasuyu

Suzan portakalsuyu

Melih kavunsuyu

Melih kavunsuyu

Rasim kirazsuyu

Tarık portakalsuyu

Lale şeftalisuyu

Suzan portakalsuyu

Melih kayısısuyu

Ayşe mangosuyu

Galip havuçsuyu

Osman karpuzsuyu

Betül narsuyu 

alt alta olacak şekilde yazalım. 
~~~bash
sed 's/portakalsuyu/limonata/g' dosyaadi
~~~
Yazdığımız komut portakalsuyu yerine limonata yazar. Metinleri değiştirme 's' işleci ile gerçekleşir. 'g' ise tüm satırda aynı işlemi uygulamaya yarar. Bunu bir örnekle gösterelim.
~~~bash
sed 's/u/Z/' dosyaadi
~~~
Metinde bulunan 'u' harflerini 'Z' harfi yapar yalnız aynı satırda birden fazla 'u' varsa sadece ilk bulduğunu değiştirir.
~~~bash
sed 's/u/Z/g' dosyaadi
~~~
Aynı satırdaki tüm 'u' harflerini değiştirmek istiyorsak 'g' yi kullanmamız gerekir.
~~~bash
sed 's/^F/f/' dosyaadi
~~~
Burada F harfini f olarak değiştirdik ancak ^ karakteri satır başı anlamına gelir. Yani satır başında F harfi bulunanları f ile değiştir. Burada dikkat etmemiz gereken nokta bir satırda tek bir satır başı olacağından 'g' kullanmamıza gerek yoktur.
~~~bash
sed 's/$/SATIRSONU/' dosyaadi
~~~
$ karakteri satır sonu anlamına gelir ve bu komut satır sonlarına SATIRSONU yazar.
~~~bash
sed 's/^$/BOSSATIR/' dosyaadi
~~~
Boş satırlara BOSSATIR yazar.
~~~bash
sed '/^$/d' dosyaadi
~~~
d ile silme işlemi yapabiliriz, bu komutta boş satırları siler.
~~~bash
sed -e 's/Z/u/g' -e 's/e/B/g' dosyaadi
~~~
Burada -e parametresi birden fazla değiştirme yapmak için kullanılır. 
## AWK 
Basitleştirilmiş bir programlama dili olarak görülebilir. Bir dosya içerisinde istediğimiz sütunlara kolayca ulaşabiliriz.Veya sütunlar arası matematiksel işlemleri kolayca yapabiliriz. 
~~~bash
awk '{print $1}' dosyaadi
~~~
Az önceki dosyamız için bu komutu yazarsak 1. sütunu yani isim listesini ekrana getirir. 
Varolan dosyamızı şu şekilde düzenleyelim.

Fatih elmasuyu       5      7

Suzan portakalsuyu   3      9

Melih kavunsuyu      2      5

Melih kavunsuyu      7      2

Rasim kirazsuyu      8      4

Tarık portakalsuyu   4      5

Lale şeftalisuyu     5      2

Suzan portakalsuyu   1      8

Melih kayısısuyu     2      5

Ayşe mangosuyu       6      3

Galip havuçsuyu      7      8

Osman karpuzsuyu     3      5

Betül narsuyu        5      1

olarak değiştirelim. 
~~~bash
awk '{sonuc=$3*$4; print $0 ,sonuc}' dosyaadi
~~~
Komutumuz 3 ve 4. satırları çarparak bir sonuc değişkenine atıyor ekrana hem tüm dosya içeriğini hemde sonucu yazıyor.
## BASH SCRIPT (KABUK PROGRAMLAMA)
Kabuk programları, bir veya birden fazla Linux komutunu tutan dosyalardır. sh uzantılı bir dosya oluşturarak dosyanın ilk satırına #!/bin/bash yazmamız gerekir.
~~~bash
#!/bin/bash
echo -n "ben kimim :"
whoami
~~~
deneme.sh adında bir dosya oluşturup içerisine bu komutu yazalım. Yazdığımız komut ekrana ben kimim : kullanıcı adımızı yazar. 
~~~bash
chmod +x deneme.sh 
~~~
Scriptimizi çalıştırmak için öncelikle oluşturduğumuz dosyanın çalıştırılabilir olması lazım. 
~~~bash
sh deneme.sh
~~~
Bu komut ile yazdığımız dosyayı çalıştırabiliriz.
~~~bash
#!/bin/bash
mesaj="bash script ögreniyorum"
echo $mesaj
~~~
Metnimizi bir değişkene attık ve bu değişkeni yazdırdık.
~~~bash
#!/bin/bash
echo "Adınızı giriniz"
read ad
echo "Adınız : " $ad
~~~
Klavyeden veri girişi için read komutunu kullanırız.
~~~bash
#!/bin/bash
let "topla=4+5"
echo $topla
~~~
Aritmetiksel işlemler için let komutunu kullanırız.
~~~bash
#!/bin/bash
echo "bir sayı giriniz"
read sayi
if [ $sayi -lt 10 ]
then
 echo " girdiğiniz sayi 10 dan küçüktür "
else
 echo " girdiğiniz sayi 10 dan büyüktür "
fi
~~~
-lt '<' görevi görür.
~~~bash
#!/bin/bash
echo "bir sayı giriniz"
read sayi
if [ $sayi -gt 10 ]
then
 echo " girdiğiniz sayi 10 dan büyüktür "
else
 echo " girdiğiniz sayi 10 dan küçüktür "
fi
~~~
-gt '>' görevi görür.
~~~bash
#!/bin/bash
echo    "1. dosya ve dizinleri görüntüle"
echo    "2. hangi kullanıcıyla bağlıyım"
echo    "3. ekranı temizle"
echo -n "Secenegi giriniz : "
read secenek
case $secenek in
 1)
  ls
  ;;
 2)
 whoami
  ;;
 3)
  clear
  ;;
 *)
  echo Hatali secenek
esac
~~~
Case yapısı bu şekildedir.
~~~bash
#!/bin/bash
sayac=0
while [ $sayac -lt 10 ]
 do
  sayac=$((sayac+1))
  echo $sayac
 done
~~~
While döngüsü kullanımı bu şekildedir. 1'den 10'a kadar olan sayıları yazar.
~~~bash
#!/bin/bash
for meyve in erik kiraz elma
 do
  echo $meyve
 done
~~~
For döngüsü kullanımı bu şekildedir.
