---
title: systemd operasyonları
weight: 1
---

Systemd, modern Linux sistemlerinde başlatma ve durdurma işlemlerinin yönetimini sağlayan bir sistem yönetimi aracıdır. Systemd, birim dosyaları olarak adlandırılan yapılandırma dosyaları kullanarak sistem hizmetlerini yönetir. Bu birim dosyaları, hizmetin başlatma, durdurma, yeniden başlatma, devreye alma ve devre dışı bırakma gibi işlemlerini yönetmek için komutlar sağlar.

Systemd ile kullanılan en temel işlemler şunlardır:

- start: Bir hizmeti başlatmak için kullanılır.
Örnek kullanım:


```tpl
systemctl start nginx.service
```

Bu komut, nginx hizmetini başlatır.

- stop: Bir hizmeti durdurmak için kullanılır.
Örnek kullanım:

```tpl
systemctl stop nginx.service
```

Bu komut, nginx hizmetini durdurur.

- restart: Bir hizmeti yeniden başlatmak için kullanılır.
Örnek kullanım:

```tpl
systemctl restart nginx.service
```

Bu komut, nginx hizmetini yeniden başlatır.

- enable: Bir hizmeti başlangıçta otomatik olarak başlatmak için kullanılır.
Örnek kullanım:

```tpl
systemctl enable nginx.service
```

Bu komut, nginx hizmetinin sistem başlangıcında otomatik olarak başlatılmasını sağlar.

- disable: Bir hizmeti başlangıçta otomatik olarak başlatmayı devre dışı bırakmak için kullanılır.

```tpl
systemctl disable nginx.service
```

Bu komut, nginx hizmetinin sistem başlangıcında otomatik olarak başlatılmasını engeller.