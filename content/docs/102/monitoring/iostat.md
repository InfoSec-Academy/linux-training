---
title: iostat
weight: 1
---

**iostat** komutu, disk aktivitelerini ve transfer oranlarını, I/O taleplerinin bekleyen sürelerini, CPU kullanım oranlarını ve daha birçok performans istatistiğini görüntüleyebilir. iostat komutu, sistemdeki farklı disklerin performansını ve kullanımını ayrı ayrı gösterir. Bu nedenle, sistem yöneticileri ve sistem performansını izlemek isteyen diğer kullanıcılar tarafından sıkça kullanılır.

iostat, çoğu Linux dağıtımında varsayılan olarak kurulu gelen sysstat paketinin bir parçasıdır. Eğer sisteminizde sysstat paketi yüklü değilse, öncelikle sisteminizdeki paket yöneticisi ile sysstat paketini yüklemeniz gerekmektedir.

```tpl
yum install sysstat
apt install sysstat
```

örnek iostat çıktısı;

```tpl
[root@localhost /]# iostat 
Linux 6.2.14-300.fc38.x86_64 (localhost.localdomain) 	05/06/2023 	_x86_64_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.25    0.05    0.25    0.03    0.01   99.42

Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
vda               2.11        68.77        22.17         0.00     499056     160893          0
zram0             0.04         0.16         0.00         0.00       1176          4          0
```

Bu çıktıyı yorumlamak gerekirse

- avg-cpu: Sistemin ortalama CPU kullanımını ve bekleme süresini gösterir. 
- %user kullanıcı işlemleri için kullanılan CPU yüzdesini, 
- %system işletim sistemi işlemleri için kullanılan CPU yüzdesini, 
- %idle boşta geçen CPU yüzdesini, %iowait disk girdi/çıktısı için beklenen CPU yüzdesini, 
- %nice öncelikli (nice) kullanıcı işlemleri için kullanılan CPU yüzdesini, %steal sanal işlemcilerin (CPU'ların) ana bilgisayarda fiziksel işlemcinin paylaşılması durumunda çaldıkları zaman yüzdesini gösterir.

**Device**: Bu bölüm, disklerin adını ve istatistiklerini içerir. tps saniyedeki transferlerin (okuma veya yazma) sayısını, **kB_read/s** ve **kB_wrtn/s** saniyede okunan ve yazılan kilobayt miktarını, kB_read, kB_wrtn ve kB_dscd toplam okunan, yazılan ve verilerin atıldığı kilobayt miktarını gösterir.

Bu çıktıya göre, sistemin bir disk bölümü **(vda)** ve bir **zram (zram0)** disk birimi var. vda saniyede 2.11 transfer gerçekleştiriyor ve saniyede 68.77 kB okuyor ve 22.17 kB yazıyor. zram0 ise çok düşük kullanım oranlarına sahip olduğundan, disk girdi/çıktısı hemen hemen hiç olmuyor.