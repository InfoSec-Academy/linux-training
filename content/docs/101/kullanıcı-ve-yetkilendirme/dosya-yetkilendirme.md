---
title: Dosya Yetkilendirme
weight: 4
---

# Bir Dosyanın Geçerli Sahibini ve Grup Sahipliğini Bulma

Linux'ta bir dosya/dizinde yer alan izinleri gösteren güçlü ve muhtemelen tanıdık bir komut vardır. Bu, ls -l komutudur:

```tpl
[root@026ddc54726b opt]# ls -l
-rwxr--r-- 1 root root 0 Apr 25 06:38 test.sh
```
 
* ilk karakter dosya türünü belirtir. (-)
  > (-) dosya
  > (d) dizin
  > (I) sembolik link
* 2-4 karakter kullanıcı için izinlerini belirtir.(rwx)
* 5-7 karakter  group izinlerini belirtir.(r--)
* 8-10 karakter diğerizinleri belirtir. (r--)




{{< tabs "uniqueid" >}}
{{< tab "read" >}}
## read

Okuma izni, bir dosyanın içeriğini açıp okumanıza izin verir. Ancak dosyada herhangi bir düzenleme veya değişiklik yapamazsınız.

{{< /tab >}}

{{< tab "write" >}}

## write

Yazma izni, bir dosyayı düzenlemenize, kaldırmanıza veya yeniden adlandırmanıza izin verir.

{{< /tab >}}

{{< tab "execute" >}}

## execute

Unix tipi sistemde, yürütme izni verilmeden bir programı çalıştıramaz

{{< /tab >}}
{{< /tabs >}}

# chmod

"chmod", Linux ve diğer Unix tabanlı işletim sistemlerinde dosya ve klasör izinlerini değiştirmek için kullanılan bir komuttur.

"chmod" komutu, üç farklı öğe kullanarak izinleri ayarlar:

- İzin verilen kullanıcı türü (örneğin, sahibi, grup üyeleri, diğer kullanıcılar)
- Hangi izinlerin verileceği (örneğin, okuma, yazma, çalıştırma)
- Hangi işlem yapılacağı (ekleme, kaldırma, ayarlama)

**Octal Table**

| binary | octal | permissions |
|--------|-------|-------------|
| 000    | 0     | ---         |
| 001    | 1     | --x         |
| 010    | 2     | -w-         |
| 011    | 3     | -wx         |
| 100    | 4     | r--         |
| 101    | 5     | r-x         |
| 110    | 6     | rw-         |
| 111    | 7     | rwx         |


```
chmod <groupName>=<permissions> <fileName>  
```

Örnek;

```tpl
[root@026ddc54726b opt]# ls -l
-rw-r--r-- 1 root root 0 Apr 27 06:38 test.sh
[root@026ddc54726b opt]# chmod u=rwx,g=rx,o=x test.sh 
[root@026ddc54726b opt]# ls -l
-rwxr-x--x 1 root root 0 Apr 27 06:38 test.sh
```

```
777 = rwxrwxrwx  
765 = rwxrw-r-x  
654 = rw-r-xr--  
```

Örnek;

```tpl
[root@026ddc54726b opt]# chmod 701 test.sh 
[root@026ddc54726b opt]# ls -l
-rwx-----x 1 root root 0 Apr 27 06:38 test.sh
```


#  chown

"chown" komutu, Linux ve diğer Unix tabanlı işletim sistemlerinde bir dosyanın veya klasörün sahibini değiştirmek için kullanılır.


```
chown <user_name>:<group_name> <file_name>
```

Örnek;

```tpl
[root@026ddc54726b opt]# chown new_user2:db_admins test.sh 
[root@026ddc54726b opt]# ls -l test.sh 
-rwx-----x 1 new_user2 db_admins 0 Apr 27 06:38 test.sh
```
 
 # chgrp

Linux ve diğer Unix tabanlı işletim sistemlerinde bir dosyanın veya klasörün grubunu değiştirmek için kullanılır. Bu komut, dosya grubunu değiştirmenin yanı sıra, dosya sahibini değiştirmez.

```
chown <group_name> <file_name>
```

Örnek;

```tpl
[root@026ddc54726b opt]# chgrp root test.sh 
[root@026ddc54726b opt]# ls -l test.sh 
-rwx-----x 1 new_user2 root 0 Apr 27 06:38 test.sh
```


