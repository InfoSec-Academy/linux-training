---
title: Kullanıcı Oluşturma
weight: 1
---


# Kullanıcı Oluşturma

Linux da  yeni bir kullanıcı oluşturmak için;

```tpl
useradd new_user
```

Linux'ta 'useradd' komutu ile yeni bir kullanıcı eklediğimizde, kilitli bir durumda oluşturulur ve o kullanıcı hesabının kilidini açmak için, 'passwd' komutuyla o hesaba bir şifre belirlememiz gerekir.

```tpl
[root@026ddc54726b /]# passwd new_user
Changing password for user new_user.
New password: 
Retype new password: 
passwd: all authentication tokens updated successfully.
```
# Parola Atama

Yeni bir kullanıcı oluşturulduğunda, (şayet yönlendirme yoksa) otomatik olarak "/etc/passwd" dosyasına eklenir.

```tpl
[root@026ddc54726b /]# cat /etc/passwd | grep new_user
new_user:x:1000:1000::/home/new_user:/bin/bash
```
Yukarıdaki çıktı, iki nokta üst üste ile ayrılmış yedi alan içerir, her alanın kendi anlamı vardır.

# Alanların Anlamları

**Username**: Sisteme giriş yapmak için kullanılan kullanıcı oturum açma adı. 1 ila 32 karakter uzunluğunda olmalıdır.
**Password**: Kullanıcı parolası (veya x karakteri) /etc/shadow dosyasında şifrelenmiş biçimde depolanır.
**User ID (UID)**: Her kullanıcının bir Kullanıcı Kimliği (UID) Kullanıcı Kimlik Numarası olmalıdır. Varsayılan olarak, UID 0 root kullanıcı için ayrılmıştır ve 1-99 arasındaki UID'ler önceden tanımlanmış diğer hesaplar için ayrılmıştır. 100-999 arasında değişen diğer UID'ler, sistem hesapları ve grupları için ayrılmıştır.
**Group ID (GID)**: /etc/group dosyasında saklanan birincil Grup Kimliği (GID) Grup Kimlik Numarası.
**User Info**: Bu alan isteğe bağlıdır ve kullanıcı hakkında ekstra bilgiler tanımlamanıza olanak tanır.
**Home Directory**: Kullanıcının ana dizininin mutlak konumu.
**Shell**: Bir kullanıcının kabuğunun mutlak konumu, yani /bin/bash.

{{< hint info >}} Farklı bir home dizini atayarak oluşturma

```
useradd -d /data/new_user new_user
```
{{< /hint >}}


{{< hint info >}} Farklı bir uid atayarak oluşturma

```
useradd -u 1003 new_user
```
{{< /hint >}}

{{< hint info >}} Farklı gruplara atayarak oluşturma

```
[root@026ddc54726b /]# groupadd admins
[root@026ddc54726b /]# groupadd db_admins
[root@026ddc54726b /]# useradd -G admins,db_admins new_user2
[root@026ddc54726b /]# id new_user2
uid=1001(new_user2) gid=1003(new_user2) groups=1003(new_user2),1001(admins),1002(db_admins)
```
{{< /hint >}}

{{< hint info >}} Home dizini oluşturmadan oluşturma
Linux'ta yeni bir kullanıcı hesabı oluştururken, kullanıcının otomatik olarak ev dizini (home directory) oluşturulmamasını sağlar. 
Bu, genellikle sistem hesapları (system accounts) oluşturmak için kullanılır.

```
[root@026ddc54726b /]# useradd -M new_user3

```
{{< /hint >}}

