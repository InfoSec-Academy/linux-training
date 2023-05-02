---
title: Temel komutlar
weight: 1
---

Linux, bir işletim sistemi olarak, bilgisayar donanımını yönetir ve kullanıcıların bilgisayar kaynaklarını (dosyalar, yazılımlar, cihazlar vb.) yönetmelerine olanak tanır.
Linux, çekirdek olarak adlandırılan temel bir bileşene sahiptir ve bu çekirdek, işletim sistemi işlevlerini yerine getirmek için kullanılır.
Linux'un çalışması için, bir bilgisayarda öncelikle BIOS (Basic Input/Output System) adı verilen bir yazılım yüklü olmalıdır. BIOS, bilgisayarın temel işlevlerini sağlar, örneğin sabit disk, klavye ve fare gibi bileşenlere erişim sağlar.

Daha sonra, bilgisayarın işletim sistemi yüklenebilmesi için bir önyükleme işlemi gerçekleştirilir. Bu işlemde, bilgisayar önce BIOS tarafından yönlendirilir, ardından işletim sistemi önyükleyicisi olarak adlandırılan bir yazılım yüklenir. 
**Önyükleyici**, işletim sisteminin yüklenmesi için gereken dosyaları bulmak ve yüklemek için gerekli adımları atar.
İşletim sistemi yüklendikten sonra, kullanıcı bir kabuk (shell) aracılığıyla işletim sistemini yönetebilir. Kabuk, kullanıcının komutlar yazmasını ve işletim sistemi ile etkileşimde bulunmasını sağlar. 
**Bash (Bourne-Again SHell)** kabuğu, Linux sistemlerinde en yaygın olarak kullanılan kabuktur.

Ayrıca, bir Linux sistemi için önyükleme sürecinde önemli bir bileşen olan **GRUB (Grand Unified Bootloader)** önyükleme yükleyicisini de ekleyebiliriz. 
GRUB, bilgisayarın önyükleme işlemi sırasında işletim sistemi yükleyicisini bulmak ve yüklemek için kullanılır. Ayrıca, birden fazla işletim sistemi varsa, kullanıcının hangi işletim sistemi yüklemesini seçebileceği bir menü sunar.
Sonuç olarak, Linux, bir işletim sistemi olarak, donanım, önyükleme işlemi, GRUB, kabuk ve işletim sistemi yükleyicisi gibi bileşenleri içeren bir bütündür. Bu bileşenler birbirleriyle etkileşime girerek, kullanıcıların bilgisayar kaynaklarını yönetmesine olanak tanır.

# Komutlar

## ls 
Bu komut, bulunduğunuz dizinin içeriğini listeler. Örneğin, ls komutunu çalıştırdığınızda dizindeki dosyalar ve diğer dizinler listelenecektir.
## cd 
Bu komut, bir dizinden diğerine geçmenizi sağlar. Örneğin, cd /home komutu, bulunduğunuz dizinden /home dizinine geçmenizi sağlar.
## pwd
Bu komut, bulunduğunuz dizinin tam yolunu gösterir. Örneğin, pwd komutu, bulunduğunuz dizinin tam yolunu görüntüler.
## mkdir
Bu komut, yeni bir dizin oluşturmanızı sağlar. Örneğin, mkdir myfolder komutu, bulunduğunuz dizinde myfolder adında yeni bir dizin oluşturur.
## rmdir
Bu komut, boş bir dizini silmenizi sağlar. Örneğin, rmdir myfolder komutu, myfolder adındaki boş dizini siler.
## rm
Bu komut, bir dosya veya dizini silmenizi sağlar. Örneğin, rm myfile.txt komutu, myfile.txt adındaki dosyayı siler.
## cp
Bu komut, bir dosya veya dizini kopyalamanızı sağlar. Örneğin, cp myfile.txt mybackup.txt komutu, myfile.txt dosyasını mybackup.txt adında bir dosyaya kopyalar.
## mv
Bu komut, bir dosya veya dizini taşımanızı veya yeniden adlandırmanızı sağlar. Örneğin, mv myfile.txt myfolder komutu, myfile.txt dosyasını myfolder adındaki dizine taşır.
## touch
Bu komut, yeni bir dosya oluşturmanızı veya dosya zaman bilgilerini güncellemenizi sağlar. Örneğin, touch myfile.txt komutu, myfile.txt adında yeni bir dosya oluşturur veya dosyanın son değiştirilme zamanını günceller.
## cat
Bu komut, bir dosyanın içeriğini görüntüler. Örneğin, cat myfile.txt komutu, myfile.txt adındaki dosyanın içeriğini görüntüler.
## less
Bu komut, bir dosyanın içeriğini sayfa sayfa görüntüler. Örneğin, less myfile.txt komutu, myfile.txt adındaki dosyanın içeriğini sayfa sayfa görüntüler.
## head
Bu komut, bir dosyanın baş kısmını görüntüler. Örneğin, head myfile.txt komutu, myfile.txt adındaki dosyanın baş kısmını görüntüler.
## tail
Bu komut, bir dosyanın son kısmını görüntüler. Örneğin, tail myfile.txt komut
## grep
Bu komut, bir metin dosyasındaki belirli metinleri aramanızı sağlar. Örneğin, grep "example" myfile.txt komutu, myfile.txt dosyasında "example" kelimesini arar.
## echo
Bu komut, bir metin veya değişken içeriğini ekrana yazdırır. Örneğin, echo "Hello, World!" komutu, "Hello, World!" metnini ekrana yazdırır.
## sudo
Bu komut, bir komutu yönetici (root) olarak çalıştırmanızı sağlar. Örneğin, sudo apt-get install htop komutu, htop programını yüklerken yönetici izinleri gerektirir.
## chmod
Bu komut, bir dosyanın izinlerini değiştirmenizi sağlar. Örneğin, chmod 755 myfile.sh komutu, myfile.sh adındaki betik dosyasının izinlerini değiştirir.
## chown
Bu komut, bir dosyanın sahibini veya grup bilgisini değiştirmenizi sağlar. Örneğin, chown myuser myfile.txt komutu, myfile.txt adındaki dosyanın sahibini myuser olarak değiştirir.
## df
Bu komut, dosya sisteminizin disk kullanımını gösterir. Örneğin, df -h komutu, disk kullanımını insan tarafından okunabilir bir formatta görüntüler.
## top
Bu komut, sistemdeki işlemci kullanımını ve en yüksek CPU kullanan işlemleri görüntüler. Örneğin, top komutu, işlemci kullanımını ve en yüksek CPU kullanan işlemleri canlı olarak görüntüler.