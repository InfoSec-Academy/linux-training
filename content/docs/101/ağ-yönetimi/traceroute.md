---
title: traceroute
weight: 8
---

Traceroute, ağdaki bir hedefe erişmek için verilerin nasıl ilerlediğini gösteren bir ağ teşhis aracıdır. Traceroute, paketlerin izlenebilirliğini sağlamak için ICMP (Internet Control Message Protocol) ve TTL (Time to Live) kullanır. Traceroute, bir hedefe yönelik veri paketleri gönderir ve bu paketlerin yolu boyunca hangi ağ cihazlarından geçtiğini ve hangi cihazlarda gecikme yaşandığını takip eder.

Traceroute, bir hedefe yönelik veri paketleri gönderir ve her paketin TTL değerini arttırarak gönderir. TTL, her yönlendirici (router) geçişinde bir azaltma işlemi uygular. Eğer bir paket belirli bir yönlendirici tarafından alınır ve TTL değeri sıfıra düşerse, yönlendirici paketi yok sayar ve ICMP mesajıyla geri gönderir. Traceroute, bu ICMP mesajlarını kullanarak, paketin yolu boyunca geçtiği yönlendiricilerin IP adreslerini ve gecikme sürelerini hesaplar.

Traceroute, genellikle ağ bağlantı sorunlarını tespit etmek ve ağdaki yavaş noktaları belirlemek için kullanılır. Traceroute sonuçları, ağ yöneticileri tarafından kullanılarak ağ sorunlarını gidermek ve ağ performansını optimize etmek için kullanılabilir.

![](/images/traceroute.png)

```tpl
root@localhost network-scripts]# traceroute google.com
traceroute to google.com (142.251.140.14), 30 hops max, 60 byte packets
 1  _gateway (192.168.122.1)  0.256 ms  0.158 ms  0.120 ms
 2  192.168.1.1 (192.168.1.1)  1.570 ms  1.712 ms  1.852 ms
 3  10.76.0.1 (10.76.0.1)  5.475 ms  5.469 ms  5.525 ms
 4  10.36.117.186 (10.36.117.186)  6.638 ms  6.827 ms  6.594 ms
 5  10.54.255.14 (10.54.255.14)  6.642 ms  6.591 ms  6.676 ms
 6  10.54.255.49 (10.54.255.49)  7.799 ms  7.022 ms  6.895 ms
 7  10.40.155.155 (10.40.155.155)  10.944 ms  9.379 ms 10.40.155.156 (10.40.155.156)  9.531 ms
 8  10.40.141.73 (10.40.141.73)  11.124 ms * *
 9  10.40.168.31 (10.40.168.31)  6.627 ms  6.596 ms  6.634 ms
10  72.14.212.96 (72.14.212.96)  28.006 ms  27.812 ms  27.970 ms
11  * * *
12  216.239.49.198 (216.239.49.198)  28.838 ms 108.170.250.177 (108.170.250.177)  27.379 ms 172.253.65.42 (172.253.65.42)  27.878 ms
13  142.251.246.235 (142.251.246.235)  24.532 ms 108.170.250.178 (108.170.250.178)  106.250 ms 108.170.250.163 (108.170.250.163)  27.931 ms
14  sof04s04-in-f14.1e100.net (142.251.140.14)  24.847 ms 142.251.242.231 (142.251.242.231)  28.510 ms sof04s04-in-f14.1e100.net (142.251.140.14)  24.730 ms
```

Tablodaki çıktı, Google.com'a bir traceroute işlemi gerçekleştirilerek elde edilmiştir.

İlk sütunda "hop" numaraları yer alır, yani verilerin geçtiği ara noktaların sayısı. "30 hops max" ifadesi ise, traceroute işleminde en fazla 30 ara noktaya kadar izlenebileceğini gösterir.

İkinci sütunda, traceroute işlemi sırasında her ara noktanın IP adresi yer alır. Örneğin, ilk ara nokta "_gateway" adıyla tanımlanmış ve IP adresi 192.168.122.1'dir.

Üçüncü sütunda, her ara noktaya veri paketi gönderilmesi için geçen süreler (ms) yer alır. Örneğin, ilk ara noktaya veri paketi gönderilmesi 0.256 ms sürmüştür.

Çıktıdaki bilgiler, veri paketlerinin hangi ağ cihazlarından geçtiğini ve hangi cihazlarda gecikme yaşandığını takip etmemizi sağlar. Örneğin, ilk ara nokta "_gateway" adıyla tanımlanmış ve bu noktada veri paketleri hemen hemen hiç gecikme yaşamamıştır. Diğer ara noktalarda ise değişken gecikmeler yaşanmıştır.

Son sütunda, her ara noktanın ismi ve IP adresi yer alır. Örneğin, son ara nokta "sof04s04-in-f14.1e100.net" adıyla tanımlanmış ve IP adresi 142.251.140.14'tür. Bu, Google'ın sunucularından biridir.

Traceroute işlemi, ağ sorunlarını tespit etmek ve ağ performansını optimize etmek için kullanılabilir. Bu çıktıda, Google sunucusuna ulaşmak için 14 ara noktanın geçilmesi gerektiği görülüyor ve bazı noktalarda gecikme yaşandığı gözlemleniyor. Ancak genel olarak, veri paketleri hızlı bir şekilde Google sunucusuna ulaşmış  görünüyor.

{{< hint info >}}
*** traceroute çıktısında "timeout" durumunu ifade eder. Yani, bir paket hedefe ulaşamadığında, bir sonraki hop'a geçilir ve bu noktaya kadar olan tüm hop'lar başarıyla geçilmiş olarak kabul edilir.
{{< /hint >}}

