---
title: fstab
weight: 7
---

fstab (File System Table) Linux işletim sistemi dosya sistemi yönetiminde kullanılan bir dosyadır. Bu dosya, sistemin açılış sırasında otomatik olarak bağlanması gereken dosya sistemlerini belirler. Bu dosyadaki girdiler, işletim sistemi tarafından otomatik olarak yüklenir.

fstab dosyası, dosya sistemi türleri ve parametreleri belirleyerek sistemdeki dosya sistemlerinin nasıl monte edileceğini belirler. Ayrıca bu dosya, sistem açılırken otomatik olarak monte edilecek dosya sistemleri, hangi kullanıcıların bunu yapabileceği, nasıl yapılandırılacağı ve bağlama seçenekleri hakkında bilgi içerir.

fstab dosyası, aşağıdaki gibi yapılandırılır:

```tpl
<file system> <mount point> <type> <options> <dump> <pass>
```

- <file system>: bağlanacak dosya sisteminin dosya yolunu veya etiketini belirtir.
- <mount point>: dosya sisteminin bağlanacağı dizin yolunu belirtir.
- <type>: dosya sistemi türünü belirtir (örn. ext4, nfs, vfat).
- <options>: dosya sistemi ile ilgili seçenekleri belirtir.
- <dump>: dosya sisteminin yedeklenmesi gerekip gerekmediğini belirtir.
- <pass>: dosya sisteminin dosya sistemlerinin sırayla nasıl kontrol edileceğini belirtir.

Örnek fstab girdileri:

```tpl
/dev/sda2 none swap sw 0 0
---
/dev/sda2: Swap bölümünün bir ismi.

none: Swap dosyası için bir dosya sistemi tanımlayıcısı.

swap: Dosya sistemi türü.

sw: Swap bölümünü kullanmaya izin veren seçenekler.

0: Dosya sistemi önyükleme sırasında yedekleme yapılmayacak.

0: Swap bölümü için dosya sistemi geçerlilik kontrolü yapmayacak.
---

/dev/sda1 / ext4 errors=remount-ro 0 1

---
/dev/sda1: Kök dosya sistemi bölümünün bir ismi.

/: Kök dosya sisteminin yerini belirtir.

ext4: Dosya sistemi türü.

errors=remount-ro: Eğer sistemde bir hata olursa, dosya sistemi otomatik olarak okunur-yazılır bir moda geçirilir.

0: Dosya sistemi önyükleme sırasında yedekleme yapılmayacak.

1: Kök dosya sistemi, diğer dosya sistemlerinden önce önyükleme yapacak.
---


/dev/sda3 /home ext4 defaults 0 2

---
/dev/sda3: Kullanıcıların ev dizinlerinin bulunduğu dosya sisteminin bir ismi.

/home: Ev dizinlerinin bulunduğu yer.

ext4: Dosya sistemi türü.

defaults: Dosya sistemi için varsayılan seçenekler.

0: Dosya sistemi önyükleme sırasında yedekleme yapılmayacak.

2: Ev dizinleri diğer dosya sistemlerinden sonra önyükleme yapacak.
---

```

