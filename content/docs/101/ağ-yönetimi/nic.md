---
title: NIC
weight: 1
---

**iproute  ve net-tools  bu iki paket bize Network kartımız hakkında bilgi verecek ip ve ifconfig komutlarını barındırmaktadır.**

## NIC

NIC (Network Interface Card), ağ arayüz kartı olarak da bilinen bir donanım bileşenidir. Bilgisayar veya diğer cihazlar için ağ bağlantısı sağlar ve kablosuz veya kablolu ağa bağlanmak için kullanılabilir.

NIC, bir bilgisayarın ağa bağlanmasına izin veren bir ara yüz sağlar. Bir NIC, Ethernet kablosu, fiber optik kablo veya kablosuz ağa bağlanmak için kullanılan antenler gibi fiziksel bağlantı noktaları sağlar. Bu, bilgisayarın ağa erişim sağlamasını ve veri gönderip almasını sağlar.

NIC'ler, birçok farklı boyutta ve şekilde mevcuttur. Bazı NIC'ler, PCI veya PCIe gibi bilgisayarın anakartına yerleştirilirken, diğerleri USB veya Thunderbolt bağlantı noktaları aracılığıyla bilgisayara bağlanır.

NIC'ler, ağ işlemleri için donanım hızlandırma sağlayabilir ve ağ trafiği yönetimi, güvenliği ve yönlendirmesi gibi görevleri yürütebilir. NIC'ler, ayrıca özel amaçlı görevler için de yapılandırılabilir, örneğin ağ protokolü analizi yapmak için kullanılabilirler.


## ip a
"ip a" komutu, Linux tabanlı işletim sistemlerinde ağ yapılandırmasını yönetmek için kullanılan bir komuttur. Bu komutun çıktısı, cihazın ağ bağlantılarını, IP adreslerini ve diğer ağ konfigürasyon ayarlarını gösterir.

örnek çıktı

```tpl
[root@026ddc54726b opt]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
17: eth0@if18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever
```

Burada, her bir ağ arayüzü için bir blok görüntülenir. 
Blok, arayüz adı (örneğin "lo" veya "eth0@if18"), durumu, MTU (maksimum iletim birimi) ve diğer bilgileri içerir. 
Ayrıca, arayüzün IP adresi (inet) ve MAC adresi (link/ether) de görüntülenir.


**"BROADCAST, MULTICAST, UP, LOWER_UP"** ifadeleri, bir ağ arayüzünün durumunu ve özelliklerini tanımlayan farklı bayraklardır.

- "BROADCAST" bayrağı, ağ arayüzünün yayın adresini kullanarak diğer cihazlara veri gönderebileceğini gösterir. Bu, cihazın aynı ağda diğer cihazlarla iletişim kurabilmesi için gereklidir.

- "MULTICAST" bayrağı, ağ arayüzünün çoklu yayın adreslerini kullanarak diğer cihazlara veri gönderebileceğini gösterir. Bu, özellikle video akışı ve diğer çoklu kullanıcılı uygulamalar için önemlidir.

- "UP" bayrağı, ağ arayüzünün etkin olduğunu ve kullanılabilir olduğunu gösterir. Ağ arayüzü, bu bayrağın devre dışı bırakılmasıyla devre dışı bırakılabilir.

- "LOWER_UP" bayrağı, ağ arayüzünün fiziksel olarak bağlı olduğunu gösterir. Yani kablo bağlandığında ağ arayüzü otomatik olarak etkinleştirilir ve "LOWER_UP" bayrağı ayarlanır.

## ifconfig

"ifconfig" komutu, Unix tabanlı işletim sistemlerinde ağ arayüzlerinin yapılandırması ve yönetimi için kullanılan bir komuttur. Bu komutun çıktısı, cihazın ağ arayüzlerinin durumunu, IP adreslerini, MAC adreslerini ve diğer ağ yapılandırma bilgilerini gösterir.

örnek çıktı

```tpl
[root@026ddc54726b opt]# ifconfig 
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:ac:11:00:02  txqueuelen 0  (Ethernet)
        RX packets 69518  bytes 102955785 (98.1 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 36460  bytes 2495651 (2.3 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Bu çıktıda, "eth0" adlı ağ arayüzü için bilgiler görüntülenir. Ağ arayüzü hakkındaki bilgiler, bayraklar, MTU (maksimum iletim birimi), IP adresi, alt ağ maskesi, yayın adresi ve MAC adresi gibi çeşitli bölümlerde ayrılır.

Ayrıca, RX (alınan) ve TX (gönderilen) paketlerinin sayısı ve boyutu da görüntülenir. Bu bölümlerde, RX hataları, düşürülen paketler ve diğer sorunlar hakkında da bilgi alınabilir. Benzer şekilde, TX hataları, düşürülen paketler, taşıyıcı hataları ve çakışmalar hakkında da bilgi alınabilir.

Bu çıktı, ağ arayüzünün durumu, yapılandırması ve performansı hakkında bilgi sağlar ve sorun giderme işlemleri sırasında kullanışlı bir araçtır.