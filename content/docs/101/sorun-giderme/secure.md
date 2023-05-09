---
title: secure
weight: 2
---



Linux sistemlerinde, /var/log/secure dosyası, sistem güvenliğiyle ilgili bilgilerin kaydedildiği bir günlük dosyasıdır. Bu dosyaya genellikle şunlar kaydedilir:

- Yetkilendirme işlemleri (login, logout, başarısız login denemeleri)
- Süper kullanıcı (root) işlemleri
- SSH oturum açma girişimleri
- PAM (Pluggable Authentication Modules) etkinlikleri
- Sudo komutu kullanımı
- Güvenlik duvarı etkinlikleri
Bu dosya, sistem yöneticilerinin sistem güvenliğini izlemesine ve sorunları tespit etmelerine yardımcı olur.

Örnek bir çıktı;

```tpl
[root@localhost mnt]# tail -f /var/log/secure
May  7 17:34:14 localhost sudo[142319]: ergunbilsel : TTY=pts/4 ; PWD=/home/ergunbilsel ; USER=root ; COMMAND=/usr/bin/dmesg -n 7
May  7 17:34:14 localhost sudo[142319]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
May  7 17:34:14 localhost sudo[142319]: pam_unix(sudo:session): session closed for user root
May  7 17:35:52 localhost sudo[142553]: ergunbilsel : TTY=pts/4 ; PWD=/opt ; USER=root ; COMMAND=/usr/bin/dd if=/dev/zero of=test.img bs=1M count=1024
May  7 17:35:52 localhost sudo[142553]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
May  7 17:35:55 localhost sudo[142553]: pam_unix(sudo:session): session closed for user root
May  7 17:36:13 localhost sudo[142600]: ergunbilsel : TTY=pts/4 ; PWD=/opt ; USER=root ; COMMAND=/usr/bin/dd if=/dev/zero of=test.img bs=1M count=1024
May  7 17:36:13 localhost sudo[142600]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
May  7 17:36:59 localhost sudo[142600]: pam_unix(sudo:session): session closed for user root
May  7 17:37:13 localhost su[142774]: pam_unix(su:session): session opened for user root(uid=0) by (uid=1000)
```