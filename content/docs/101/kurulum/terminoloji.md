---
title: Terminoloji
weight: 1
---

- / (Kök dizin): Bu, tüm dosya sisteminin kök dizinidir ve tüm diğer dizinlerin üzerinde bulunur. Bu dizin, tüm sistem dosyalarını içerir ve tüm kullanıcıların erişebileceği her şey burada bulunur.

- /boot: Bu dizin, işletim sisteminin başlangıç ​​dosyalarını içerir. Bu, önyükleme (boot) süreci sırasında kullanılır ve burada bulunan dosyalar, sistem açıldığında yüklenir.

- /boot/efi: Bu dizin, EFI (Extensible Firmware Interface) uyumlu bir sistemde önyükleme dosyalarını içerir. EFI, BIOS'un yerini alan bir donanım arayüzüdür.

- /swap: Bu, bir sistemdeki bellek yönetimi için kullanılan bir alanı temsil eder. Swap, fiziksel RAM'in bir uzantısı olarak kullanılır ve gerektiğinde kullanılır. Bu, sistem belleği (RAM) tükendiğinde kullanılır ve geçici bellek ihtiyacını karşılamak için kullanılır.


## ext4
ext4 (dördüncü genişletilmiş dosya sistemi) Linux'ta en yaygın kullanılan dosya sistemidir. ext3'ün geliştirilmiş bir sürümüdür ve daha iyi performans, güvenilirlik ve ölçeklenebilirlik sağlar. ext4, büyük dosya boyutları, daha büyük disk boyutları ve daha iyi dosya sistemi bütünlüğü için tasarlanmıştır.

## XFS
XFS, SGI tarafından geliştirilen ve daha sonra Linux'ta da kullanılmaya başlanan bir dosya sistemidir. Özellikle büyük dosya boyutları, büyük disk alanları ve yüksek performans gerektiren uygulamalar için önerilir. XFS, özellikle yüksek hızlı veri aktarımı, güvenilirlik ve yüksek bütünlük sağlama konusunda iyi bir performans sergiler.

## LVM
LVM (Logical Volume Manager), Linux'ta kullanılan bir mantıksal disk yönetim sistemidir. LVM, birden fazla disk bölümünü tek bir sanal disk olarak gruplandırmanızı sağlar. Bu, disk bölümleri arasında daha kolay boyut değişikliği yapmanızı, birden fazla disk bölümü arasında veri taşımanızı ve disk hatalarına karşı daha fazla dayanıklılık sağlamanızı mümkün kılar.

## RAID 
(Redundant Array of Independent Disks), birden fazla sabit disk sürücüsünü tek bir mantıksal sürücü olarak birleştirir ve veri yedekliliği ve yüksek performans sağlar. Linux'ta RAID, birkaç farklı düzeyde uygulanabilir. Örneğin RAID 0, veriyi iki veya daha fazla disk sürücüsüne yazarak performansı artırırken, RAID 1, verileri birden fazla disk sürücüsünde yedekleyerek veri bütünlüğünü sağlar.

## GRUB 
(GNU Grand Unified Bootloader), Linux ve diğer işletim sistemlerini önyükleme sürecinde yüklemek için kullanılan bir önyükleme yükleyicisidir. GRUB, önyükleme işlemini kolaylaştırmak için bir dizi özellik sunar ve çeşitli dosya sistemleri ve disk bölümleme düzenleri ile uyumludur.

GRUB, BIOS veya EFI gibi donanım arayüzleri aracılığıyla önyükleme yükleyicisi olarak çalışabilir. Sistem başlatıldığında, GRUB, önyükleme menüsünü görüntüler ve kullanıcının hangi işletim sistemini veya yüklü olan hangi Linux çekirdeğini yüklemek istediğini seçmesine izin verir. Seçim yapıldıktan sonra, GRUB, seçilen işletim sistemini veya çekirdeği belleğe yükler ve işletim sistemini başlatır.

GRUB ayrıca çeşitli yükleme seçeneklerini de destekler, örneğin hata ayıklama modu, tek kullanıcı modu vb. GRUB, Linux sistem yöneticileri için çok önemli bir araçtır ve sistemin önyükleme sürecinde herhangi bir sorun olması durumunda, sorun giderme ve onarım işlemleri için kullanılabilir.

