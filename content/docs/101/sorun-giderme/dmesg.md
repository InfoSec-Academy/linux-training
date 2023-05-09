---
title: dmesg
weight: 1
---


dmesg, Linux çekirdeği tarafından üretilen sistem günlüğü mesajlarını görüntülemek için kullanılan bir komut satırı aracıdır. "dmesg" kısaltması, "Donanım Mesajı" anlamına gelir ve işletim sistemi çekirdeğinin başlangıcından bu yana üretilen tüm günlük mesajlarını görüntüler. Bu mesajlar, donanım hataları, sürücü yüklemeleri, sistem zamanlaması ve diğer sistem olayları hakkında bilgi sağlayabilir. dmesg ayrıca sistemdeki donanım bileşenlerini tanımlamak için de kullanılabilir.

**dmesg** komutu aşağıdaki gibi farklı şekillerde kullanılabilir:

- En son sistem logları: dmesg komutu, en son sistem loglarını gösterir.

```tpl
dmesg
```

- Sistemin loglarını sayfa sayfa göstermek: dmesg komutu, less komutu ile birlikte kullanılarak sayfa sayfa gösterilebilir.


```tpl
dmesg | less
```

- Sistemin boot mesajlarını görüntülemek: dmesg komutu, dmesg -T seçeneği ile sistemin boot mesajlarını zaman damgalı bir şekilde görüntüleyebilir.

```tpl
dmesg -T
```


- Dmesg loglarını bir dosyaya kaydetmek: dmesg komutu, çıktısını bir dosyaya yönlendirerek logları kaydedebilir.

```tpl
dmesg > /home/user/dmesg_logs.txt
```


- Dmesg loglarından sadece error mesajlarını gösterilebilir

```tpl
dmesg --level=err
```