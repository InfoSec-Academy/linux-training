---
title: kernel
weight: 1
---


Linux Kernel, Linux işletim sistemi için temel çekirdek bileşenidir. Linux'un temelini oluşturan, donanım kaynaklarını yöneten, işlemleri planlayan, bellek yönetimini sağlayan ve sistem çağrılarını işleyen bir yazılımdır. Linux Kernel, GPL (Genel Kamu Lisansı) altında özgür ve açık kaynaklı bir yazılımdır.

Linux Kernel, başlangıçta Linus Torvalds tarafından geliştirilmiştir ve şimdi dünya çapında bir geliştirici topluluğu tarafından sürdürülmektedir. Çeşitli platformlar için uygun olan Linux Kernel, dünya genelinde birçok cihazda kullanılmaktadır, özellikle sunucu ve gömülü sistemlerde sıkça kullanılır.


![](/images/kernel.png)

Çalıştığım bir server da  kernel bilgilerine nasıl ulaşabilirim?

```tlp
[root@localhost boot]# uname -r
6.2.9-300.fc38.x86_64
```
veya

```tlp
[root@localhost boot]# rpm -q kernel
kernel-6.2.9-300.fc38.x86_64
```


```tlp
[root@localhost boot]# uname -a
Linux localhost.localdomain 6.2.9-300.fc38.x86_64 #1 SMP PREEMPT_DYNAMIC Thu Mar 30 22:32:58 UTC 2023 x86_64 GNU/Linux
```

Bu çıktı, bir Linux işletim sisteminin bazı temel bilgilerini içerir:

- "localhost.localdomain" hostname'dur, yani bu Linux sistemi üzerindeki makinenin adıdır.
- "6.2.9-300.fc38.x86_64" kernel sürümüdür. Bu sürüm numarası, sistemin kullandığı Linux kernel'in sürümünü gösterir. Bu örnek çıktıda, kernel sürümü "6.2.9-300.fc38.x86_64" olarak belirtilmiştir. Bu, Fedora 38 için özelleştirilmiş bir kernel sürümüdür.
- "#1 SMP PREEMPT_DYNAMIC Thu Mar 30 22:32:58 UTC 2023" bölümü, kernel yapılandırması hakkında bazı bilgileri içerir. Bu örnekte, "PREEMPT_DYNAMIC" kernel seçeneği etkinleştirilmiştir, bu da öncelikli işlem kuyruğu desteği sunar. Ayrıca, kernelin hangi tarihte ve saatte yapılandırıldığı belirtilir.
- "x86_64 GNU/Linux" ise, bu Linux sisteminin mimarisini gösterir. "x86_64" mimarisi, 64 bit işlemcileri destekleyen bir mimaridir ve bu sistemde kullanılan işlemcinin bu mimariye sahip olduğunu gösterir.

## Güncelleme

Linux çekirdeği kullanan dağıtımlar; test ve kontrollerinden sonra çekirdek versiyonalarını repolarında yayınlamaktadır. Güncelleme komutları ile bu işlemleri gerçekleştirebilirisniz.


```tlp
[root@localhost boot]# yum check-update kernel
Last metadata expiration check: 0:09:21 ago on Thu 04 May 2023 04:25:04 PM +03.

kernel.x86_64                                 6.2.14-300.fc38                                  updates
```


```tlp
[root@localhost boot]# sudo yum  install kernel --best
Last metadata expiration check: 0:11:10 ago on Thu 04 May 2023 04:25:04 PM +03.
Package kernel-6.2.9-300.fc38.x86_64 is already installed.
Dependencies resolved.
======================================================================================================
 Package                        Architecture      Version                    Repository          Size
======================================================================================================
Installing:
 kernel                         x86_64            6.2.14-300.fc38            updates            129 k
Installing dependencies:
 kernel-core                    x86_64            6.2.14-300.fc38            updates             15 M
 kernel-modules                 x86_64            6.2.14-300.fc38            updates             55 M
 kernel-modules-core            x86_64            6.2.14-300.fc38            updates             30 M

Transaction Summary
======================================================================================================
Install  4 Packages

Total download size: 100 M
Installed size: 146 M
Is this ok [y/N]: 
```


Bu işlemden sonra reboot edip yeni kernel ile oturumu açabilirsiniz.



