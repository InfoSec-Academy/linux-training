---
title: iptables
weight: 2
---

iptables, Linux işletim sistemi için geliştirilmiş bir güvenlik yazılımıdır. Paket filtreleme, ağ adresi çevirme (NAT) ve port yönlendirme gibi işlevleri yerine getirir. İptables, Linux'un dahili bir parçasıdır ve çoğu Linux dağıtımında mevcuttur. Ayrıca, birçok güvenlik duvarı uygulaması da iptables tabanlıdır.

İptables, bir dizi kurala dayalı olarak çalışır. Her bir kural, bir paketin belirli bir eylem için uygun olup olmadığını belirler. Paketler, gelen ve giden trafiği kontrol etmek için farklı zincirlerde işlenir. Bu zincirler, paketin kaynağına ve hedefine göre belirlenir.

Örnek olarak, bir web sunucusu üzerindeki bir iptables kuralları, sadece belirli IP adreslerinden gelen HTTP trafiğini kabul etmek ve diğer tüm trafiği reddetmek için ayarlanabilir. Bu şekilde, saldırganların sunucuya erişmelerini engelleyebilirsiniz.


İptables kurallarının listelenmesi:


```tpl
iptables -L
```

Bu komut, mevcut tüm iptables kurallarını listeler.

İptables kuralı ekleme:

```tpl
iptables -A INPUT -s 192.168.0.0/24 -j DROP
```

Bu komut, gelen bağlantılarda kaynak IP'si 192.168.0.0/24 olanları engeller.

İptables kuralı silme:

```tpl
iptables -D INPUT -s 192.168.0.0/24 -j DROP
```

Belirli bir IP adresinden gelen trafiği kabul etme:

```tpl
iptables -A INPUT -s 192.168.1.100 -j ACCEPT
```


- Belirli bir portu engelleme:

8080 numaralı HTTP portunu engellemek istiyoruz. Bu durumda aşağıdaki iptables komutunu kullanabiliriz:

```tpl
iptables -A INPUT -p tcp --dport 8080 -j DROP
```
Bu komut, gelen tüm TCP trafiğini 8080 portundan düşürecek (DROP).


Yukarıdaki örneler gelen trafikler içindir. 

Iptables ile giden trafiği engellemek için OUTPUT chain'inin kullanılması gerekmektedir. OUTPUT chain'i, paketin sunucudan ayrılıp gitmek üzere dışarı çıkacağı zamanda kontrol edilir. Giden trafiği engellemek için OUTPUT chain'indeki DROP hedefi kullanılabilir.

Aşağıdaki örnekte, tüm çıkış trafiği engellenir:

```tpl
iptables -A OUTPUT -j DROP
```

Bu komut, tüm çıkış trafiğini engelleyerek sunucunun internete erişimini de engelleyecektir. Bu nedenle, sadece belirli portlara izin vermek için filtreleme kuralları eklenmelidir. Örneğin, yalnızca HTTP (port 80) trafiğine izin vermek için aşağıdaki komut kullanılabilir:

```tpl
iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -j DROP
```
Bu komutlar, HTTP trafiğine izin vermek için bir kural ekler ve diğer tüm çıkış trafiğini engeller.


