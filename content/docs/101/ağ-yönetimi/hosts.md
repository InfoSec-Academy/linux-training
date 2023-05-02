---
title: hosts.conf
weight: 5
---

/etc/hosts, Unix benzeri işletim sistemlerinde kullanılan bir dosyadır ve IP adresleri ile alan adları arasında elle yapılan eşleştirmeleri sağlar. Bu dosya, bir bilgisayarın DNS sunucularını kullanmadan, yerel olarak alan adlarına IP adresleri atamak için kullanılabilir.

Örneğin, /etc/hosts dosyasında aşağıdaki satırlar bulunabilir:

```tpl
127.0.0.1 localhost
192.168.1.10 myserver.com
```

Bu, bilgisayarın yerel DNS sunucusunu kullanmadan, "localhost" adının her zaman 127.0.0.1 IP adresine eşit olduğunu ve "myserver.com" adının 192.168.1.10 IP adresine eşit olduğunu belirtir.

/etc/hosts dosyası, bir bilgisayarın yerel ağındaki diğer bilgisayarları adlandırmak veya test amaçlı web sitelerini yönlendirmek gibi çeşitli amaçlar için kullanılabilir. Ancak, büyük ağlarda veya Internet'teki geniş kullanıcı tabanına sahip sitelerde kullanımı sınırlıdır, çünkü bu durumlarda, DNS sunucuları IP adresi ve alan adı eşleştirmelerini daha etkili bir şekilde yönetir.


{{< hint info >}}
**TCP Wrapper**
TCP Wrapper, ağ servisleri için ağ erişim kontrolü ve günlük tutma özellikleri sağlayan bir yazılım uygulamasıdır. Gelen ağ trafiğini bağlanan ana bilgisayarın IP adresine göre filtrelemenize olanak tanıyan bir güvenlik aracıdır.
{{< /hint >}}


