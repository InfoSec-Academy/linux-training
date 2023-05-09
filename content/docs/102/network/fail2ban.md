---
title: fail2ban
weight: 2
---


Fail2ban, sunucularda otomatik olarak güvenlik önlemleri alarak, sisteme yapılan saldırıları engellemek için kullanılan bir açık kaynaklı bir yazılımdır. Fail2ban, güvenliği artırmak için sunucu log dosyalarını izleyerek saldırıları tespit eder ve bu saldırıların ardından saldırganın IP adresini belirler ve bu IP adresini engeller.

Fail2ban, birden fazla protokolü destekleyen bir yazılımdır ve bir dizi filtreleme kuralları içerir. Örnek olarak, SSH sunucusunda başarısız oturum açma denemelerini tespit edebilir ve ardından bu IP adreslerini belirleyip firewall kurallarını kullanarak IP adreslerini engelleyebilir.

Fail2ban'ın kullanımı oldukça basittir. İlk olarak, sunucuda Fail2ban'ı yüklemek ve yapılandırmak gerekir. Daha sonra, izlenecek log dosyalarını ve hangi saldırıları tespit edeceğini belirlemek için filtre kuralları oluşturulur. Fail2ban kurallarının yapılandırılması, jail.conf dosyasında yapılır. Bu dosyada, izlenen log dosyaları, filtreleme kuralları ve ne kadar süreyle IP adreslerinin engelleneceği gibi ayarlar yapılabilmektedir.

Fail2ban'ın kurulumu ve yapılandırması çeşitli Linux dağıtımlarında farklılık gösterir, ancak genellikle aşağıdaki adımlar takip edilir:

- Sistemde gerekli bağımlılıkların yüklenmesi:
```tpl
yum install fail2ban
```

- Fail2ban'ın yapılandırılması: 
```tpl
vi /etc/fail2ban/jail.conf
```
- Filtrelerin yapılandırılması: 

```tpl
vi /etc/fail2ban/filter.d/filtername.conf
```

- Fail2ban'ın yeniden başlatılması: 

```tpl
systemctl restart fail2ban
```
Fail2ban'ın örnek kullanımlarından biri, SSH sunucularındaki başarısız oturum açma girişimlerinin engellenmesidir. Bu saldırıları engellemek için, jail.conf dosyasında aşağıdaki ayarlar yapılabilir:

```tpl
[ssh]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
findtime = 600
bantime = 1800
```


Bu ayarlara göre, 3 defa başarısız oturum açma girişiminde bulunan bir IP adresi 10 dakika boyunca engellenecek ve 30 dakika sonra engeli kaldırılacaktır.

Fail2ban, sunucular için önemli bir güvenlik aracıdır ve saldırılara karşı etkili bir koruma sağlayabilir. 