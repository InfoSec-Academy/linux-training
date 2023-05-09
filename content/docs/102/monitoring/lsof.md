---
title: lsof
weight: 1
---

lsof (list open files) bir sistem aracıdır ve açık dosyaları listelemek için kullanılır. 
Bu araç, bir sistemde hangi dosyaların açık olduğunu, bu dosyaları hangi kullanıcıların açtığını, hangi proseslerin bu dosyalara eriştiğini ve açık dosyaların hangi bağlantı noktalarına sahip olduğunu görüntülemek için kullanılabilir.

## Tüm port ve bağlantıların listelenmesi

Açık olan tüm network socketleri ve aktif bağlantıları listelemek için -i parametresi kullanılmaktadır.

```tpl
 lsof -i
```

```tpl[root@localhost /]# lsof -i
COMMAND    PID            USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd      1            root   88u  IPv6  21068      0t0  TCP *:websm (LISTEN)
systemd-r  573 systemd-resolve   10u  IPv4  21042      0t0  UDP *:hostmon 
systemd-r  573 systemd-resolve   11u  IPv4  21043      0t0  TCP *:hostmon (LISTEN)
systemd-r  573 systemd-resolve   12u  IPv6  21045      0t0  UDP *:hostmon 
systemd-r  573 systemd-resolve   13u  IPv6  21046      0t0  TCP *:hostmon (LISTEN)
systemd-r  573 systemd-resolve   16u  IPv4  21049      0t0  UDP _localdnsstub:domain 
systemd-r  573 systemd-resolve   17u  IPv4  21050      0t0  TCP _localdnsstub:domain (LISTEN)
systemd-r  573 systemd-resolve   18u  IPv4  21051      0t0  UDP _localdnsproxy:domain 
systemd-r  573 systemd-resolve   19u  IPv4  21052      0t0  TCP _localdnsproxy:domain (LISTEN)
chronyd    653          chrony    5u  IPv4  24322      0t0  UDP localhost:323 
chronyd    653          chrony    6u  IPv6  24323      0t0  UDP localhost:323 
sshd      1338            root    3u  IPv4  28190      0t0  TCP *:ssh (LISTEN)
sshd      1338            root    4u  IPv6  28199      0t0  TCP *:ssh (LISTEN)
sshd      1656            root    4u  IPv4  30988      0t0  TCP localhost.localdomain:ssh->_gateway:46026 (ESTABLISHED)
sshd      1660            root    4u  IPv4  30988      0t0  TCP localhost.localdomain:ssh->_gateway:46026 (ESTABLISHED)
```

Görüldüğü gibi dinlenen (LISTEN) tüm portlar ve aktif bağlantılar listelenmektedir.

Eğer, port ve hostname’lerin isim çözümlemesi yapılmadan numerik olarak listelenmesini isterseniz -Pni parametrelerini kullanmanız gerekir:


```tpl
lsof -Pni
```

```tpl
[root@localhost /]# lsof -Pni
COMMAND    PID            USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd      1            root   88u  IPv6  21068      0t0  TCP *:9090 (LISTEN)
systemd-r  573 systemd-resolve   10u  IPv4  21042      0t0  UDP *:5355 
systemd-r  573 systemd-resolve   11u  IPv4  21043      0t0  TCP *:5355 (LISTEN)
systemd-r  573 systemd-resolve   12u  IPv6  21045      0t0  UDP *:5355 
systemd-r  573 systemd-resolve   13u  IPv6  21046      0t0  TCP *:5355 (LISTEN)
systemd-r  573 systemd-resolve   16u  IPv4  21049      0t0  UDP 127.0.0.53:53 
systemd-r  573 systemd-resolve   17u  IPv4  21050      0t0  TCP 127.0.0.53:53 (LISTEN)
systemd-r  573 systemd-resolve   18u  IPv4  21051      0t0  UDP 127.0.0.54:53 
systemd-r  573 systemd-resolve   19u  IPv4  21052      0t0  TCP 127.0.0.54:53 (LISTEN)
chronyd    653          chrony    5u  IPv4  24322      0t0  UDP 127.0.0.1:323 
chronyd    653          chrony    6u  IPv6  24323      0t0  UDP [::1]:323 
sshd      1338            root    3u  IPv4  28190      0t0  TCP *:22 (LISTEN)
sshd      1338            root    4u  IPv6  28199      0t0  TCP *:22 (LISTEN)
sshd      1656            root    4u  IPv4  30988      0t0  TCP 192.168.122.151:22->192.168.122.1:46026 (ESTABLISHED)
sshd      1660            root    4u  IPv4  30988      0t0  TCP 192.168.122.151:22->192.168.122.1:46026 (ESTABLISHED)
```

