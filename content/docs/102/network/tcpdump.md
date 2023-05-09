---
title: tcpdump
weight: 2
---


**tcpdump**, Linux ve Unix benzeri işletim sistemlerinde ağ trafiğini yakalamak ve analiz etmek için kullanılan bir komut satırı aracıdır. tcpdump, ağ trafiğini yakalamak için promiscuous modda çalışır ve birçok protokolü destekler.

Tcpdump, ağ trafiğini kaydetmek için kullanılabilir ve kaydedilen veriler Wireshark gibi grafik arayüzüne sahip bir araçta analiz edilebilir.

Tcpdump ayrıca, ağda meydana gelen sorunları tespit etmek için kullanılan bir araçtır. Örneğin, ağ trafiğinde neden gecikmeler veya düşük performans yaşandığını belirlemek için kullanılabilir. Ayrıca, ağda herhangi bir kötü niyetli faaliyet tespit etmek için de kullanılabilir.

Tcpdump kullanımı oldukça esnektir ve birçok farklı parametre ile çalışabilir. Bazı temel parametreler şunlardır:

-i: Hangi arayüzün dinlenileceğini belirtir.
-n: IP adreslerinin ve port numaralarının sayısal olarak görüntülenmesini sağlar.
-v: Daha ayrıntılı çıktı verir.
-c: Belirli bir sayıda paket yakalamak için kullanılır.
Örneğin, """tcpdump -i enp1s0  -n -c 10""" komutu, "enp1s0 " arayüzünden gelen ilk 10 paketi sayısal IP adresleri ve port numaralarıyla birlikte gösterecektir.


```tpl
[root@localhost /]# tcpdump -i enp1s0 -n -c 10
dropped privs to tcpdump
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
20:26:54.652683 IP 192.168.122.151.ssh > 192.168.122.1.46026: Flags [P.], seq 2372240427:2372240655, ack 1256259480, win 501, options [nop,nop,TS val 3001248506 ecr 2100104801], length 228
20:26:54.652908 IP 192.168.122.1.46026 > 192.168.122.151.ssh: Flags [.], ack 228, win 6862, options [nop,nop,TS val 2100104937 ecr 3001248506], length 0
20:26:54.744891 IP 192.168.122.151.ssh > 192.168.122.1.46026: Flags [P.], seq 228:616, ack 1, win 501, options [nop,nop,TS val 3001248598 ecr 2100104937], length 388
20:26:54.745050 IP 192.168.122.1.46026 > 192.168.122.151.ssh: Flags [.], ack 616, win 6861, options [nop,nop,TS val 2100105029 ecr 3001248598], length 0
20:26:54.845699 IP 192.168.122.151.ssh > 192.168.122.1.46026: Flags [P.], seq 616:972, ack 1, win 501, options [nop,nop,TS val 3001248699 ecr 2100105029], length 356
20:26:54.846005 IP 192.168.122.1.46026 > 192.168.122.151.ssh: Flags [.], ack 972, win 6862, options [nop,nop,TS val 2100105130 ecr 3001248699], length 0
20:26:54.949595 IP 192.168.122.151.ssh > 192.168.122.1.46026: Flags [P.], seq 972:1328, ack 1, win 501, options [nop,nop,TS val 3001248803 ecr 2100105130], length 356
20:26:54.949890 IP 192.168.122.1.46026 > 192.168.122.151.ssh: Flags [.], ack 1328, win 6862, options [nop,nop,TS val 2100105234 ecr 3001248803], length 0
20:26:55.053679 IP 192.168.122.151.ssh > 192.168.122.1.46026: Flags [P.], seq 1328:1700, ack 1, win 501, options [nop,nop,TS val 3001248907 ecr 2100105234], length 372
20:26:55.053931 IP 192.168.122.1.46026 > 192.168.122.151.ssh: Flags [.], ack 1700, win 6861, options [nop,nop,TS val 2100105338 ecr 3001248907], length 0
```



Tcpdump ayrıca, belirli bir protokolü dinlemek veya belirli bir IP adresi veya port numarasına sahip trafiği dinlemek için de kullanılabilir. Örneğin, sudo tcpdump tcp port 22 komutu, TCP protokolünün 22 numaralı bağlantı noktasında oluşan trafiği gösterecektir.


```tpl
[root@localhost /]# tcpdump tcp port 22
dropped privs to tcpdump
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on enp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
20:35:03.119036 IP _gateway.46026 > localhost.localdomain.ssh: Flags [.], ack 2372301851, win 6862, options [nop,nop,TS val 2100593401 ecr 3001736972], length 0
20:35:03.119154 IP localhost.localdomain.ssh > _gateway.46026: Flags [P.], seq 1:197, ack 0, win 501, options [nop,nop,TS val 3001736972 ecr 2100593401], length 196
20:35:03.119343 IP _gateway.46026 > localhost.localdomain.ssh: Flags [.], ack 197, win 6862, options [nop,nop,TS val 2100593401 ecr 3001736972], length 0
20:35:03.198448 IP localhost.localdomain.ssh > _gateway.46026: Flags [P.], seq 197:569, ack 0, win 501, options [nop,nop,TS val 3001737052 ecr 2100593401], length 372
20:35:03.198671 IP localhost.localdomain.ssh > _gateway.46026: Flags [P.], seq 569:765, ack 0, win 501, options [nop,nop,TS val 3001737052 ecr 2100593401], length 196
20:35:03.198688 IP _gateway.46026 > localhost.localdomain.ssh: Flags [.], ack 569, win 6861, options [nop,nop,TS val 2100593481 ecr 3001737052], length 0
20:35:03.198745 IP _gateway.46026 > localhost.localdomain.ssh: Flags [.], ack 765, win 6862, options [nop,nop,TS val 2100593481 ecr 3001737052], length 0
```

