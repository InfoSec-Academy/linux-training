---
title: resolv.conf
weight: 4
---

/etc/resolv.conf, Unix benzeri işletim sistemlerinde DNS (Domain Name System) yapılandırmasını ayarlamak için kullanılan bir dosyadır. Bu dosya, DNS sorguları yapmak için kullanılan DNS sunucularının IP adreslerini ve diğer yapılandırma seçeneklerini içerir.

Örneğin, bir bilgisayarın /etc/resolv.conf dosyasında aşağıdaki satırlar bulunabilir:

```tpl
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Bu, bilgisayarın DNS sorgularını Google Public DNS sunucularına yönlendireceğini belirtir. Başka seçenekler de vardır, örneğin, arama alanlarını belirlemek veya sorguları sınırlamak için yerel bir DNS sunucusu kullanmak gibi. Bu dosya, kullanıcıların DNS yapılandırmasını kolayca değiştirmelerini sağlar.
