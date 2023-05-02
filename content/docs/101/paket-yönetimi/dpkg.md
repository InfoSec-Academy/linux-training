---
title: DPKG
weight: 1
---

dpkg, tek bir paketi veya bir dizi paketi kurmak, kaldırmak, yeniden yapılandırmak, yükseltmek veya sorgulamak için kullanılabilir. Ayrıca, dpkg, sistemde yüklü olan tüm paketlerin listesini de görüntüleyebilir.

dpkg, önceden hazırlanmış Debian paketlerinin yönetimini sağlar. Bu paketler, .deb uzantılı dosyalar olarak adlandırılır ve Debian veya Ubuntu depolarından indirilebilirler.

dpkg komutu, aşağıdaki temel işlevleri sağlar:

Paket kurulumu: "dpkg -i paket.deb" komutu kullanılarak bir Debian paketi kurulabilir.
Paket kaldırma: "dpkg -r paket_adı" komutu kullanılarak bir Debian paketi kaldırılabilir.
Paket güncelleme: "dpkg -i paket.deb" komutu kullanılarak güncellenmiş bir Debian paketi kurulabilir.
Paket bilgisi sorgulama: "dpkg -p paket_adı" komutu kullanılarak bir paket hakkında bilgi alınabilir.
Sistemdeki tüm paketlerin listesi: "dpkg --list" komutu kullanılarak tüm yüklü Debian paketleri listelenebilir.
dpkg, yalnızca Debian paketlerini yönetmek için kullanılır. dpkg, diğer Linux dağıtımlarında kullanılan paket yöneticilerinden farklı olarak, paket bağımlılıklarını ve bağımlılık yönetimini otomatik olarak yönetmez. 

## dpkg -l
"dpkg -l" komutu, sisteme yüklenmiş tüm paketleri listelemek için kullanılır.

## dpkg -l $package

Belirli bir paketin sistemde yüklü olup olmadığını kontrol etmek için kullanılır. 

## dpkg -S

Belirli bir dosyanın hangi pakete ait olduğunu belirlemek için kullanılır. Komutu kullanarak, dosyanın tam yolu veya dosya adını belirtmeniz gerekir.

## dpkg -L

Bu komutu çalıştırdığınızda, paketin tüm dosyalarının listesi görüntülenecektir. Bu dosyalar arasında, paketin program dosyaları, yapılandırma dosyaları, dokümantasyon dosyaları vb. olabilir.