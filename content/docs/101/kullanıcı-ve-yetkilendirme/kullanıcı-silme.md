---
title: Kullanıcı Silme
weight: 2
---


# Kullanıcı Silme

Linux'ta bir kullanıcı hesabını silmek için kullanılır. Bu komut, kullanıcının home dizinini ve mail kutusunu da siler.


```tpl
userdel new_user
```

Ayrıca, userdel komutunu kullanarak kullanıcının home dizinini silmeden, sadece kullanıcı hesabını kaldırmak için -r seçeneğini kullanabilirsiniz:

```tpl
userdel -r new_user
```


Kaldırmak istediğiniz kullanıcı hala oturum açmışsa veya bu kullanıcıya ait çalışan işlemler varsa **userdel** komutu kullanıcının kaldırılmasına izin vermez.

Bu durumda, kullanıcının oturumunu kapatması ve kullanıcının çalışan tüm işlemlerini şu komutla sonlandırması önerilir killall :

```tpl
killall -u new_user
```


