---
title: shadow
weight: 1
---


**/etc/shadow** dosyası, Linux işletim sistemlerinde kullanıcıların şifrelerinin şifrelenmiş halinin tutulduğu dosyadır. Bu dosya, /etc/passwd dosyasındaki kullanıcıların şifrelerinin tutulduğu satırların yerine gelir ve kullanıcı şifrelerini şifreleyerek saklar. Şifreleme, genellikle MD5, SHA256 veya Blowfish algoritmaları kullanılarak yapılır.

/etc/shadow dosyası genellikle sadece root kullanıcısı tarafından okunabilir ve düzenlenebilir. Bu sayede, sadece sistem yöneticisi tarafından erişilebilen şifrelerin güvenliği artırılmış olur.

/etc/shadow dosyasında her satır bir kullanıcıya aittir ve özellikleri iki nokta üst üste (:) karakteri ile ayrılmış beş alan ile tanımlanır:

```tpl
root:$6$TS/VWbU6$eoU6A.YPS2fNUjhroKXayX9.3CswlrUvL8pHyiUisR16UwXd6oOJQmkZlC0I9Xc3li3/lbKvzK1dIFN5xIw1r0:18603:0:99999:7:::
```

Yukarıdaki çıktıda /etc/shadow dosyasında "root" kullanıcısına ait hashlenmiş şifre ve diğer bazı kullanıcı özelliklerini içermektedir. 

- **root**: Bu kullanıcının adıdır.
- **$6$TS/VWbU6$eoU6A.YPS2fNUjhroKXayX9.3CswlrUvL8pHyiUisR16UwXd6oOJQmkZlC0I9Xc3li3/lbKvzK1dIFN5xIw1r0**: kullanıcının hashlenmiş şifresidir. $6$ burada kullanılan hash türünü belirtir (SHA-512), TS/VWbU6 ise salt değerini belirtir ve son kısım ise hashlenmiş şifrenin kendisidir.
- **18603**: Bu kullanıcının son şifre değiştirme tarihini ifade eder. Bu, 1970 yılından bu yana geçen gün sayısını (Unix zaman damgası) gösterir.
- **0**: Bu kullanıcının şifre değiştirme süresini ifade eder. 0, herhangi bir kısıtlama olmadığı anlamına gelir.
- **99999**: Bu kullanıcının hesabının ne zaman süresinin dolduğunu gösterir. 99999, hesabın hiçbir zaman süresinin doldurulmayacağı anlamına gelir.
- **7**: Bu kullanıcının şifre değiştirme hatırlatma süresini ifade eder. 7, kullanıcının şifre değiştirmesi için hatırlatılacağı gün sayısını gösterir.
- **::** : Bu alan kullanılmaz, ancak eski bir parolaya sahip olan kullanıcılar için kullanılır. Şifre değiştirme zamanı dolduğunda, eski şifre burada saklanır.