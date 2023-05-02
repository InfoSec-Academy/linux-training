---
title: kernel nedir
weight: 1
---


Linux Kernel, Linux işletim sistemi için temel çekirdek bileşenidir. Linux'un temelini oluşturan, donanım kaynaklarını yöneten, işlemleri planlayan, bellek yönetimini sağlayan ve sistem çağrılarını işleyen bir yazılımdır. Linux Kernel, GPL (Genel Kamu Lisansı) altında özgür ve açık kaynaklı bir yazılımdır.

Linux Kernel, başlangıçta Linus Torvalds tarafından geliştirilmiştir ve şimdi dünya çapında bir geliştirici topluluğu tarafından sürdürülmektedir. Çeşitli platformlar için uygun olan Linux Kernel, dünya genelinde birçok cihazda kullanılmaktadır, özellikle sunucu ve gömülü sistemlerde sıkça kullanılır.


## master boot record

Ana önyükleme kaydı veya mbr, bir sabit diskin ilk sektörüdür. Bir diskin birincil bölümlerde bölümlenmesi ve aktif bölüm mbr'de tanımlanır.

MBR (Master Boot Record), bir sabit disk bölümlemesi standardıdır. Sabit disk üzerindeki ilk sektörde (512 byte) yer alır ve disk bölümleme bilgileri ile önyükleme (boot) sektörü bilgilerini içerir. MBR, BIOS (Basic Input/Output System) tarafından önyükleme işleminin başlatılması için kullanılır.

MBR, bir disk üzerindeki bölümleme yapısını tanımlar ve disk bölümlerini oluşturmak için kullanılan partition tablosunu içerir. MBR, disk bölümlerinin başlangıç sektörlerinin konumlarını ve boyutlarını belirtir. Böylece, işletim sistemi, her bir bölümü ayrı bir disk gibi ele alabilir ve her bir bölümde farklı bir dosya sistemi kullanabilir.

MBR ayrıca, disk üzerindeki birincil aktif bölümü tanımlar ve bu bölümdeki önyükleme sektörünün (boot sector) konumunu belirtir. Bu önyükleme sektörü, işletim sisteminin önyüklenmesi için gereken bilgileri içerir ve MBR, BIOS tarafından bu önyükleme sektörünün bulunduğu bölümden işletim sistemini yüklemek için kullanılır.

MBR, bilgisayarın önyükleme sürecinde kritik bir rol oynar ve disk bölümleme ve önyükleme işlemleri için kullanılan bir standarttır. Ancak, MBR'nin 2 TB'dan büyük disklerde ve çoklu işletim sistemlerinin kullanıldığı karmaşık yapılandırmalarda sınırlamaları bulunmaktadır.

## UEFI

UEFI/EFI, BIOS'un yerine daha gelişmiş bir önyükleme arabirimi sağlar. UEFI/EFI, daha yüksek performans, daha fazla güvenlik ve daha fazla özellik sağlar. Örneğin, UEFI/EFI, önyükleme işlemi sırasında donanım testleri yaparak, donanım hatalarını tespit etme ve düzeltme işlevleri gibi gelişmiş özellikler sunar.

UEFI/EFI ayrıca, bilgisayarın önyükleme sürecinde kullanılan önyükleme dosyalarının ve sürücülerinin yönetiminde de daha esnek bir yapı sunar. Bu nedenle, modern bilgisayarlar genellikle UEFI/EFI önyükleme arabirimini kullanır.

