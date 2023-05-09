---
title: crontab
weight: 6
---


Crontab, belirli aralıklarla çalıştırılmak üzere önceden planlanmış görevleri yönetmek için kullanılan bir programdır. Crontab, sistem yöneticilerinin belirli görevleri otomatikleştirmelerine ve zamanlarını daha verimli bir şekilde kullanmalarına olanak tanır. Bu nedenle, Crontab, Linux sistemi yönetimi için önemli bir araçtır.

Crontab, ayrı bir dosya olarak tutulur ve crontab komutu kullanılarak düzenlenir. Crontab dosyası, kullanıcı adı ve çalıştırılacak görevlerin bir listesi içerir. Görevler, dakika, saat, gün, ay ve haftanın hangi günü gibi zamanlama parametreleriyle belirlenir.

Crontab komutu, çeşitli parametrelerle kullanılabilir. En sık kullanılan parametreler aşağıda listelenmiştir:

- -l: Mevcut crontab dosyasını görüntüler
- -e: Crontab dosyasını düzenler
- -r: Mevcut crontab dosyasını kaldırır
Crontab dosyası aşağıdaki formatı takip eder:

```tpl
* * * * * /path/to/command arg1 arg2
- - - - -
| | | | |
| | | | ----- Haftanın hangi günü (0 - 7) 
| | | ------- Ayın hangi günü (1 - 31)
| | --------- Ay (1 - 12)
| ----------- Saat (0 - 23)
------------- Dakika (0 - 59)
```

Örneğin, "30 dakikada bir /home/user/backup.sh dosyasını çalıştır" şeklinde bir crontab görevi aşağıdaki gibi görünebilir:

```tpl
*/30 * * * * /home/user/backup.sh
```

Bu görev, her saat başı 0 ve 30 dakikalarında çalıştırılacaktır.