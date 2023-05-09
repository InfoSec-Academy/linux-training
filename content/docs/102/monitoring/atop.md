---
title: atop
weight: 1
---

**atop** 
Linux sistemlerinde sistem kaynaklarının takibini yapmak için kullanılan bir araçtır. atop, CPU, bellek, disk ve ağ kullanımı gibi sistem kaynaklarını izleyerek ayrıntılı raporlar sağlar.
atop, birçok Linux dağıtımında varsayılan olarak yüklü olmayabilir, bu nedenle öncelikle sisteminize yüklemeniz gerekebilir. 

```tlp
apt-get install atop
yum install atop
```

örnek bir atop çıktısı;

```tlp
PRC | sys    4.27s | user   3.46s | #proc    165 | #zombie    0 | #exit      0 |
CPU | sys	5% | user      6% | irq       0% | idle    186% | wait      2% |
cpu | sys	3% | user      4% | irq       0% | idle     91% | cpu001 w  2% |
cpu | sys	2% | user      2% | irq       0% | idle     95% | cpu000 w  0% |
CPL | numcpu     2 | avg1    0.04 | avg5    0.05 | csw    97534 | intr   78868 |
MEM | tot     1.9G | free    1.1G | cache 451.2M | buff    2.0M | slab   99.5M |
MEM | numnode    1 | shmem   5.0M | shrss   0.0M | tcpsk   0.0M | udpsk   0.0M |
SWP | tot     1.9G | free    1.9G | swcac   0.0M | vmcom 699.0M | vmlim   2.9G |
PAG | migrate    0 | pgin  122095 | pgout  11190 | swout      0 | oomkill    0 |
PSI | cpusome   1% | memsome   0% | memfull   0% | iosome    1% | iofull    1% |
DSK |          vda | busy      6% | read   11492 | write    708 | avio 0.85 ms |
NET | transport    | tcpi     977 | tcpo     972 | udpi      27 | udpo      29 |
NET | network	   | ipi     1012 | ipo     1017 | ipfrw      0 | deliv   1004 |
NET | enp1s0  ---- | pcki    1134 | pcko    1020 | si   14 Kbps | so    7 Kbps |
NET | lo      ---- | pcki	4 | pcko       4 | si    0 Kbps | so    0 Kbps |

```

Yukarıdaki çıktının anlamları;
- **PRC**: sistem kaynaklarının (CPU, bellek, disk, ağ) kullanımına ilişkin bilgileri içerir.
- **CPU**: CPU kullanımını, bekleme sürelerini ve kesme (interrupt) oranlarını gösterir.
- **CPL**: işlemci yükünü gösterir. Bu bölümde, ortalama yük değerleri ve işlemci sayısı gibi bilgiler yer alır.
- **MEM**: bellek kullanımına ilişkin bilgileri gösterir.
- **SWP**: swap belleği kullanımına ilişkin bilgileri gösterir.
- **PAG**: bellek yönetimi ile ilgili sayfa hareketlerini (page) gösterir. Bu bölümde, sayfa girişleri (pgin), sayfa çıkışları (pgout) ve öldürülen işlemler (oomkill) gibi bilgiler yer alır.
- **PSI**: kaynak basıncını (pressure) ölçen bir araçtır. Bu bölümde, CPU, bellek ve I/O kaynakları üzerindeki basınç seviyeleri yer alır.
- **DSK**: disk kullanımına ilişkin bilgileri gösterir. Bu bölümde, disk yoğunluğu (busy), okuma (read) ve yazma (write) işlemleri ve ortalama G/Ç süresi (avio) gibi bilgiler yer alır.
- **NET**: ağ kullanımına ilişkin bilgileri gösterir. Bu bölümde, taşıma (transport) ve ağ (network) seviyesindeki veri trafiği ve arayüz (interface) bazında gönderme (send) ve alma (receive) işlemleri yer alır.
- **PID**: Sürecin benzersiz kimliği.
- **SYSCPU**: Süreç tarafından kullanılan toplam sistem CPU zamanı (saniye).
- **USRCPU**: Süreç tarafından kullanılan toplam kullanıcı CPU zamanı (saniye).
- **RDELAY**: Sürecin giriş/çıkış (I/O) için beklediği toplam süre (milisaniye).
- **BDELAY**: Sürecin bloke edilmesi için beklediği toplam süre (milisaniye).
- **VGROW**: Sürecin sanal bellek boyutunda (virtual memory size) büyüdüğü toplam byte sayısı.
- **RGROW**: Sürecin RSS (resident set size) boyutunda büyüdüğü toplam byte sayısı.
- **RDDSK**: Sürecin diske okuduğu byte sayısı.
- **WRDSK**: Sürecin diske yazdığı byte sayısı.
- **RUID**: Sürecin gerçek kullanıcı kimliği (real user ID).
- **EUID**: Sürecin etkin kullanıcı kimliği (effective user ID).
- **ST**: Sürecin durumu (running, sleeping, stopped, zombie vb.).
- **EXC**: Sürecin son çıkış kodu (exit code).
- **THR**: Sürecin thread (iş parçacığı) sayısı.
- **S**: Sürecin çalıştığı sunucu (server).
- **CPUNR**: Sürecin çalıştığı CPU numarası.
- **CPU**: Sürecin son zaman diliminde kullandığı CPU yüzdesi.
- **CMD**: Sürecin komut satırı.



**atop** farklı şekillerde kullanılabilir.

- -a: Disklerin, CPU'nun, belleğin, ağ trafiğinin, süreçlerin ve diğer birçok özelliğin anlık durumunu gösteren tüm sistem özetini sağlar.
- -m: Bellek kullanımını gösterir.
- -n: Ağ durumunu gösterir.


## Çıktı Kayıt Etme

```tlp
atop -w log.atop 2
```

atop çıktısı her iki saniyede bir log.atop dosyasına yazılır


## Kayıt okuma

```tlp
atop -r log.atop 
```

