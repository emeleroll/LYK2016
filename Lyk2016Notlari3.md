~~~bash
du
~~~
Bir dosya veya dizinin boyutunu öğrenmemizi sağlar. Dizinin içerisindeyken bu komutu kullanırsak dizindeki tüm dosyaların tek tek boyutlarını bize verir. Sadece bir dosyanın boyutunu öğrenmek istiyorsak **du dosyaadi** şeklinde kullanabiliriz.
~~~bash
du -s
~~~
-s parametresi dizindeki dosyaların toplam boyutunu öğrenmemizi sağlar.
~~~bash
du -sh
~~~
-h parametresi boyutu MB cinsinden gösterir.
~~~bash
whatis komutadi
~~~
Bir komutun açılımını gösterir. Örneğin **whatis pwd** yazdığımızda print working directorynin baş harflerinden oluştuğunu öğrenebiliriz.
~~~bash
whoami
~~~
Sisteme hangi kullanıcı adıyla giriş yaptığımızı gösterir.
~~~bash 
cat dosyaadi
~~~
Bir dosyanın içerisini görmemizi sağlar.
~~~bash
whereis komutadi
~~~
Bir komutun hangi klasörde olduğunu gösterir.
~~~bash
nano dosyaadi
~~~
Bu komutla oluşturduğumuz bir dosyanın içerisine yazı yazabiliriz. Dosyada yaptığımız bir değişikliği nasıl kaydedeceğimizi en altta kısayollarla gösterir.
~~~bash
file dosyaveyadizinadi
~~~
Dosyanın türü bilgisini verir. (dizin,dosya vb)
~~~bash
dd if=/dev/sda of=/dev/sdb
~~~
Harddiskimizi kopyalamaya yarar. 
~~~bash
dd if=/dev/zero of=/dev/sda
~~~
Harddiskinizi okunmayacak hale sokar bu yüzden sadece sanal makinede deneyin :) /zero yerine /random değerlerde atabiliriz.
~~~bash
history
~~~
Terminalde yazdığımız komut geçmişini gösterir.
~~~bash
history -c 
~~~
Komut geçmişini temizleyebiliriz.
Örneğin hergün yazdığımız komutları kaydetmek istediğimizi düşünelim. Bunun için şöyle bir komut yazabiliriz.
~~~bash
history > dizin/08.09.2016
~~~
Bir dizin oluşturup içerisinde oluşturduğumuz dosyaya historynin çıktılarını atabiliriz. (> , >> , | kullanımını daha sonra ayrıntılı şekilde anlatacağım)

*Geçmişte yazdığımız bir komutu arıyorsak history yazdıktan sonra CTRL+R ye basarak aramak istediğimiz komutun belirli bir kısmını yazarsak bulabiliriz.*

history komutunu yazdıktan sonra komutların başında belirli numaralar olduğunu farketmişsinizdir. Bu numaralar ile de bir komutu çalıştırabiliriz.
Örneğin 65 numaralı komutumuz ls olsun ve bunu çalıştıralım. **!65** 

~~~bash
poweroff
~~~
Sistemi kapatır.
~~~bash
script
~~~
Terminaldeki tüm çıktıları kaydetmeye yarar.Kaydı durdurmak için **exit** komutunu kullanabilirsiniz.
~~~bash
cat typescript
~~~
Kaydettiğiniz çıktıları gösterir.
~~~bash
date
~~~
Sistem tarihini gösterir.
~~~bash
less dosyaadi
~~~
cat ile bir dosyanın içerisine bakmak istediğimiz zaman page up ve page down kullanmak zorundayız. Bu bazılarımıza zor gelebilir bu yüzden less komutu
kullanarak yön tuşları ile dosyayı okuyabiliriz.
~~~bash
more dosyaadi
~~~
more komutu ile entera basarak dosyanın içerisini okuyabiliriz.

## > , >> , | KULLANIMI
~~~bash
cat > dosyaadi
~~~
'>' işareti bir dosyanın içerisine yazı yazmamızı sağlar. Sistemde varolan bir dosyayı kullanırsak içeriği silinerek yeni yazdıklarımız kaydolur.
komutu yazdıktan sonra bi alt satırda dosya içerisine yazmak istediklerimizi girebiliriz, CTRL+D ile yazı yazma işlemini bitirebiliriz. **cat dosyaadi** ile yaptıklarımızı gözden geçirebilirsiniz. 
~~~bash
cat >> dosyaadi
~~~
'>' kullanırken içerisi dolu olan bir dosyaya yazı yazdığımızda içerisinin silindiğini söylemiştik. Bunu engellemek için '>>' kullanabiliriz.
Yazdıklarımızı dosyanın en alt kısmına ekler. 

**NOT:** cat yerine başka komutlarda deneyebilirsiniz. Örneğin **ls > dosyaadi** komutunu yazarsanız ls çıktısını bir dosyaya aktardığını görebilirsiniz.

- | (pipe) yazdığımız bir komutun çıktısını başka bir komutun girdisi olarak atar.
~~~bash
ls | wc
~~~
ls komutunun çıktısındaki satır,kelime ve byte değerlerini(wc) verir.
~~~bash
head dosyaadi
~~~
Bir dosyadaki ilk 10 satırı görüntüler.
~~~bash
head -n 5 dosyaadi
~~~
-n parametresiyle görüntülemek istediğimiz satır sayısında değişiklik yapabiliriz.
~~~bash
head -n -5 dosyaadi
~~~
Bu şekilde negatif bir sayı ile kullanırsak son 5 satır haricini görüntüleyebiliriz.
~~~bash
tail dosyaadi
~~~
Bir dosyadaki son 10 satırı görüntüler.
~~~bash
tail -n 5 dosyaadi
~~~
-n parametresiyle görüntülemek istediğimiz satır sayısında değişiklik yapabiliriz. Bu şekilde son 5 satırı görüntüleyebiliriz.
~~~bash
su
~~~
Farklı bir kullanıcıdayken ROOT olmaya yarar.
~~~bash
su - kullaniciadi
~~~
Root kullanıcısındayken farklı bir kullanıcıya geçebiliriz. Bu şekilde tekrar çıkış yapmamıza gerek kalmıyor. 
~~~bash
alias listele='ls -l' 
~~~
Bir komutun adını değiştirmeye yarar. ls -l yerine artık listele yazabiliriz. (farklı komutlarda yazılabilir)
~~~bash 
unalias listele
~~~
Oluşturduğumuz komutu kaldırmaya yarar. 
