---
title: IP
weight: 2
---


İki farklı IP adresi türü mevcuttur: IPv4 (sürüm 4) ve IPv6 (sürüm 6). IPv4 daha eskidir ve çok daha yaygın olarak kullanılırken, IPv6 daha yenidir ve eski standardın doğasında bulunan sınırlamaları aşmak ve daha birçok olası adres sağlamak için tasarlanmıştır.

IPv4, adresler için 32 bit kullanır; yalnızca 4,3 milyar benzersiz adres mevcuttur. Ayrıca, birçok adres tahsis edilir ve rezerve edilir, ancak gerçekte kullanılmaz. IPv4'ün gelecekteki ihtiyaçları karşılamak için yetersiz olduğu düşünülüyor çünkü küresel ağda bulunan cihazların sayısı son yıllarda çok arttı.

IPv6, adresler için 128 bit kullanır; bu, 3,4 X 1038 benzersiz adrese izin verir. Daha geniş bir bilgisayar ağınız varsa ve daha fazlasını eklemek istiyorsanız, daha benzersiz adresler sağladığı için IPv6'ya geçmek isteyebilirsiniz. Ancak, IPv6'ya geçmek karmaşık olabilir; iki protokol her zaman birlikte iyi çalışmaz. Bu nedenle, ekipmanı ve adresleri IPv6'ya taşımak önemli bir çaba gerektirir ve başlangıçta amaçlandığı kadar hızlı olmamıştır.


```tpl
[ergunbilsel@localhost linux-101]$ nslookup lwn.net
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	lwn.net
Address: 173.255.236.65
Name:	lwn.net
Address: 2600:3c03::f03c:93ff:febd:80f5
```
{{< hint info >}}
nslookup, alan adı sistemi (DNS) üzerinden bir alan adının veya IP adresinin çözülmesi için kullanılan bir komut satırı aracıdır. Windows, macOS ve Linux gibi birçok işletim sisteminde bulunur.
{{< /hint >}}


IPv4'ün ortadan kalkmamasının bir nedeni, NAT (Ağ Adresi Çevirisi) gibi yöntemlerle çok daha fazla adresi etkili bir şekilde kullanılabilir hale getirmenin yaygın olarak kullanılan yollarının olmasıdır. NAT, her biri yalnızca yerel ağda görülen benzersiz bir adrese sahip, yerel olarak bağlı birçok bilgisayar arasında bir IP adresinin paylaşılmasını sağlar. Bu, kurumsal ortamlarda kullanılırken, basit ev ağlarında da kullanılır. Örneğin, İnternet Sağlayıcınıza bağlı bir yönlendiriciniz varsa (kablolu sistem gibi), size harici olarak görünür bir adres verir, ancak evinizdeki her cihaza, dış dünya tarafından görülemeyen, ayrı bir yerel adres verir.

![](/images/nat-1.png)