---
title: who
weight: 2
---

who komutu, Linux ve Unix sistemlerinde mevcut kullanıcıların listesini gösteren bir komuttur. 
Ayrıca hangi terminal üzerinde oturum açtığınızı ve ne kadar süreyle oturum açık kaldığınızı da gösterir.


**who** komutunun bazı yaygın seçenekleri şunlardır:

-a: Tüm girişleri (normal, sistem ve son oturum) gösterir.

```tpl
[root@localhost ~]# who -a
           system boot  2023-05-09 09:10
           run-level 3  2023-05-09 09:10
root     + tty1         2023-05-09 09:13 04:49         710
root     + pts/0        2023-05-09 09:29   .          1386 (192.168.122.1)
test     + pts/1        2023-05-09 14:10 00:01        2020 (192.168.122.1)
```

-b: Sistemin son yeniden başlatılma zamanını gösterir.

```tpl
[root@localhost ~]# who -b
         system boot  2023-05-09 09:10
```

-H: Başlık satırı olmadan çıktıyı gösterir.

```tpl
[root@localhost ~]# who -H
NAME     LINE         TIME             COMMENT
root     tty1         2023-05-09 09:13
root     pts/0        2023-05-09 09:29 (192.168.122.1)
test     pts/1        2023-05-09 14:10 (192.168.122.1)
```

-q: Giriş yapan kullanıcıların sayısını gösterir.

```tpl
[root@localhost ~]# who -q
root root test
# users=3
```

-s: Yalnızca normal oturumları gösterir.

```tpl
[root@localhost ~]# who -s
root     tty1         2023-05-09 09:13
root     pts/0        2023-05-09 09:29 (192.168.122.1)
test     pts/1        2023-05-09 14:10 (192.168.122.1)
```

