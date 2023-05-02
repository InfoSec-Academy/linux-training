---
title: Kullanıcı Özelliklerini Değiştirme
weight: 3
---

# usermod 
Linux'ta bir kullanıcının özelliklerini değiştirmek için kullanılır. Bu komut, bir kullanıcının adını, ev dizinini, parolasını, grup üyeliğini vb. değiştirmek için kullanılabilir.

**UID Değiştirme**

```tpl
[root@026ddc54726b /]# id new_user
uid=1000(new_user) gid=1000(new_user) groups=1000(new_user)
[root@026ddc54726b /]# usermod -u 1005 new_user
[root@026ddc54726b /]# id new_user
uid=1005(new_user) gid=1000(new_user) groups=1000(new_user)
```

**GID Değiştirme**

```tpl
[root@026ddc54726b /]# id new_user
uid=1005(new_user) gid=1000(new_user) groups=1000(new_user)
[root@026ddc54726b /]# usermod -g 1003 new_user
[root@026ddc54726b /]# id new_user
uid=1005(new_user) gid=1003(new_user2) groups=1003(new_user2)
```


**User Name Değiştirme**

```tpl
[root@026ddc54726b /]# usermod -l new_name_user new_user
[root@026ddc54726b /]# id new_name_user
uid=1005(new_name_user) gid=1003(new_user2) groups=1003(new_user2)
```

