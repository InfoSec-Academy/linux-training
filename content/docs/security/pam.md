---
title: pam
weight: 3
---


**PAM (Pluggable Authentication Modules)**, Linux sistemlerinde kullanıcı kimlik doğrulama mekanizmalarını yönetmek için kullanılan bir çerçevedir. Bu mekanizmalar, örneğin şifre denetimleri, hesap kilitleme, oturum açma sırasında iki faktörlü kimlik doğrulama gibi işlemleri gerçekleştirebilir.

PAM, bir dizi modül kullanarak kimlik doğrulama işlemlerini yapılandırır. Her modül belirli bir görevi yerine getirir. Örneğin, bir modül kullanıcının şifresini kontrol ederken, diğer modüller hesap kilitleme ve oturum açma sırasında ek güvenlik önlemleri gibi işlemleri yapar.

PAM, sistem yöneticilerine esnek bir yapı sağlar. Kimlik doğrulama mekanizmalarının yapılandırılması, sistem yöneticilerinin ihtiyaçlarına göre değiştirilebilir. PAM, geniş bir yelpazede kimlik doğrulama yöntemlerini destekler ve birçok uygulama tarafından kullanılır.

PAM, çeşitli Linux dağıtımlarında standart bir bileşen haline gelmiştir ve birçok sistem yöneticisi tarafından kullanılmaktadır.

## Aşamalar

PAM modülleri, üç ayrı aşamada çalışır:

> Kimlik Doğrulama PAM, kullanıcının kimliğini doğrulamak için modülleri sırayla çalıştırır. PAM modülleri, kullanıcı adı ve parolasının yanı sıra, diğer kimlik doğrulama yöntemleri için gerekli tüm bilgileri alır ve doğrulama işlemi tamamlanana kadar devam eder.

> Hesap Yönetimi PAM, doğrulama aşamasından sonra hesap yönetimi adımlarını yönetir. Bu adımlar, kullanıcının hesabının geçerliliğini kontrol etmek, kısıtlamaları ayarlamak ve diğer işlemleri gerçekleştirmek için kullanılır.

> Oturum Yönetimi Son olarak, PAM oturum yönetimini sağlar. Bu aşama, kullanıcı oturumunu başlatmak veya sonlandırmak için gereken işlemleri yönetir.


Örnek bir pam çıktısı

```tpl
[test@localhost ~]$ cat  /etc/pam.d/crond 
#
# The PAM configuration file for the cron daemon
#
#
# Although no PAM authentication is called, auth modules
# are used for credential setting
auth       include    system-auth
account    required   pam_access.so
account    include    system-auth
session    required   pam_loginuid.so
session    include    system-auth
```

- **Auth modülleri**: Kullanıcının kimliğini doğrulamak için kullanılır. Kullanıcının kimlik doğrulama bilgileri (kullanıcı adı ve parola) girildiğinde, auth modülleri bu bilgileri doğrulamak ve kullanıcının sisteme erişmesine izin vermek veya reddetmek için kullanılır. Auth modülleri, kullanıcının kimliğini doğrularken, aynı zamanda parola doğrulama politikalarını uygulayabilir ve parola değişikliği işlemlerini de gerçekleştirebilir. Örnek auth modülleri: pam_unix, pam_ldap.

- **Account modülleri**: Kullanıcının hesap durumunu kontrol etmek için kullanılır. Account modülleri, kullanıcının hesap durumunu kontrol eder ve hesapları etkinleştirir veya devre dışı bırakır. Örnek account modülleri: pam_unix, pam_ldap.

- **Session modülleri**: Kullanıcının oturum açma ve oturumu kapatma işlemlerini kontrol etmek için kullanılır. Session modülleri, kullanıcının oturum açma işlemi tamamlandığında, kullanıcının oturum açtığı tarih ve saat gibi oturum bilgilerini tutar. Örnek session modülleri: pam_unix, pam_limits.


## Control-Flag

İkinci sütun Control-Flag  anlamına gelir.

- **required**: Modül başarısız olursa, oturum açma işlemi tamamlanamaz ve hata mesajı görüntülenir.
- **requisite**: required gibi davranır, ancak daha önceki bir modül başarısız olursa modülün kendisi çalıştırılmaz.
- **sufficient**: Bu modül, başarısız olursa bile oturum açma işlemi devam eder.
- **optional**: Bu modül her zaman başarılı olur ve herhangi bir hata mesajı vermez.

**include** direktifi, PAM yapılandırma dosyasında başka bir dosyayı dahil etmek için kullanılır. Bu, PAM modülleri için ayrı dosyalar kullanarak yapılandırmayı daha kolay hale getirir.

Örneğin, aşağıdaki yapılandırma dosyası, pam.d dizinindeki diğer dosyaları da dahil ederek SSH kimlik doğrulama işlemi için PAM modüllerini yapılandırır:

```tpl
# /etc/pam.d/sshd

auth       required     pam_sepermit.so
auth       include      password-auth
```



## Modüller

PAM modülleri, genellikle /lib/security/ veya /lib64/security/ dizinleri altında saklanır.

- **pam_unix**: Bu modül, kullanıcı kimlik doğrulama bilgilerini /etc/passwd ve /etc/shadow dosyalarından alır.

- **pam_limits**: Bu modül, bir kullanıcının sistem kaynaklarına erişimini sınırlandırmak için kullanılır.

- **pam_env**: Bu modül, bir kullanıcının çevresel değişkenlerini belirlemek için kullanılır.

- **pam_deny**: Bu modül, bir kullanıcının kimlik doğrulama işlemini reddeder.

- **pam_access** : Bu modül, belirli bir kullanıcının erişimini sınırlandırmak için IP tabanlı kısıtlamalar sağlar.

- **pam_faillock** : Bu modül, kullanıcının başarısız giriş denemelerini izler ve hesaplarını kilitler.


# Örnek Kullanımlar

## faillock

Aşağıdaki örnek, kullanıcının hesabını 3 başarısız giriş denemesinden sonra kilitler:


```tpl
# /etc/pam.d/password-auth

auth        required      pam_faillock.so preauth silent deny=3 unlock_time=600
auth        required      pam_faillock.so authfail deny=3 unlock_time=600
account     required      pam_faillock.so
...
```

> İlk satır, preauth sırasında (pam_authenticate() çağrıldığında) pam_faillock modülünün kullanılmasını gerektirir. Bu, kullanıcının kimlik doğrulaması yapmadan önce sınırlandırma yapılacağı anlamına gelir. silent seçeneği, kullanıcıya kilitlendiğini bildirmemesini sağlar. deny=3 seçeneği, başarısız denemelerin sayısını 3 olarak ayarlar. Bu seçenek, üç başarısız deneme sonrasında kullanıcının hesabını kilitler. unlock_time=600 seçeneği, hesabın 10 dakika boyunca kilitli kalacağını belirtir.

> İkinci satır, authfail sırasında (pam_authenticate() çağrıldığında) pam_faillock modülünün kullanılmasını gerektirir. Bu satır, kullanıcının kimlik doğrulamasını yaptıktan sonra başarısız olması durumunda sınırlandırma yapılacağını belirtir.

> Son satır, account sırasında (pam_acct_mgmt() çağrıldığında) pam_faillock modülünün kullanılmasını gerektirir. Bu, hesabın kilidini açmak için kullanılır ve bir kullanıcının hesabının kilitli olup olmadığını kontrol eder.


### Kilitli Kullanıcılar

Kilitli kullanıcıları  görmek için;

```tpl
[root@localhost ~]# faillock 
test:
When                Type  Source                                           Valid
2023-05-09 15:06:19 RHOST 192.168.122.1                                        V
2023-05-09 15:06:24 RHOST 192.168.122.1                                        V
2023-05-09 15:06:28 RHOST 192.168.122.1                                        V
```

Örnekte görüldüğü üzere test kullanıcısı kilitli durumuna düşmüştür.

Kilidi kaldırmak için;

```tpl
faillock  --reset --user test
```


## access

> Öncelikle, /etc/security/access.conf dosyasını açarak pam_access modülünü kullanarak hangi kullanıcıların erişimine izin vermek istediğinizi belirleyin. Bu dosyada, her bir kullanıcının izinleri farklı satırlarda belirtilir.

> Ardından, /etc/pam.d/ dizinindeki gerekli servis dosyasını açarak pam_access modülünü etkinleştirin. Örneğin, SSH servisine erişim kontrolü eklemek istiyorsanız, sshd dosyasını açabilirsiniz.

> pam_access modülünü kullanarak erişim kontrolü için gereken şartları belirtin. Bu örnekte, tüm kullanıcıların erişimine izin vermek için pam_access.so modülünü kullanıyoruz, ancak sadece belirli kullanıcılara erişim izni vermek isterseniz pam_access.so modülünü belirli kullanıcılara yönelik yapılandırabilirsiniz.

```tpl
# Herhangi bir host üzerinden root kullanıcısına bağlanabilir
+ : root : ALL

# user1 sadece 192.168.1.100 hostundan  gelen bağlantılar kabul edilir 
+ : user1 : 192.168.1.100

# user2 hiç bir hostan gelen istekleri kabul edemez
- : user2 : ALL

```


Bu ayarlamaları **/etc/security/access.conf** gerçekleştirdikten sshd servisine uygulamak istersek; 

```tpl
# /etc/pam.d/sshd
#%PAM-1.0
auth       substack     password-auth
auth       include      postlogin
account    required     pam_access.so
...
```

## limit

Bu örnekte, bir kullanıcının açık olan dosya sayısını sınırlayacağız. Bunu yapmak için, /etc/security/limits.conf dosyasını düzenleyeceğiz. Bu dosya, pam_limits modülü tarafından kullanılır ve sistem kaynakları için farklı kısıtlamalar tanımlamamızı sağlar.

Önce, /etc/security/limits.conf dosyasını düzenleyin ve aşağıdaki satırları ekleyin:

```tpl
test soft nofile 20
test hard nofile 21
```
test kullanıcısının açık olan dosya sayısını 20 ila 21 arasında sınırlayacaktır. soft limit, kullanıcıyı uyarırken hard limit, kullanıcının maksimum sayıya ulaşmasını engeller.

Daha sonra, /etc/pam.d/sshd dosyasını düzenleyin ve aşağıdaki satırları ekleyin:

```tpl
session required pam_limits.so
```

Son olarak, test kullanıcısını oturum açtığınızda, dosya limit sayısına ulaşmak için **ulimi** kullanabilir.

```tpl
[test@localhost ~]$ ulimit -n
20
```



