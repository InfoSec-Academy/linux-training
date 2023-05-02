---
title: Terminoloji
weight: 10
---

## OSI

OSI (Open Systems Interconnection) modeli, ağ iletişiminde kullanılan standart bir referans modelidir. OSI modeli, farklı ağ cihazları arasındaki iletişimi standartlaştırmak ve uyumluluğu sağlamak için tasarlanmıştır.

OSI modeli, 7 farklı katmandan oluşur ve her katman, belirli bir işlevi yerine getirir. Bu katmanlar şunlardır:

- Fiziksel Katman (Physical Layer): Bu katman, ağ cihazları arasındaki verilerin fiziksel ortamda taşınmasından sorumludur. Veriler, elektrik sinyalleri, radyo dalgaları veya fiber optik kablolama gibi farklı fiziksel ortamlarda taşınabilir.

- Veri Bağlantı Katmanı (Data Link Layer): Bu katman, fiziksel katmanda taşınan verilerin parçalanmasını, hata düzeltmesini ve denetimini yapar. Bu katman, ağ cihazları arasında veri paketleri göndermek için kullanılan çerçeveleri yönetir.

- Ağ Katmanı (Network Layer): Bu katman, veri paketlerinin ağ üzerindeki yönlendirmesinden sorumludur. Bu katmanda, veri paketleri yönlendiriciler aracılığıyla diğer ağlara iletilir.

- Taşıma Katmanı (Transport Layer): Bu katman, veri akışının yönetiminden sorumludur ve veri akışını segmentlere ayırır. Bu katmanda, hata kontrolü yapılır ve veri akışının düzenlenmesi sağlanır.

- Oturum Katmanı (Session Layer): Bu katman, veri iletişimindeki oturum yönetimini sağlar. Bu katmanda, veri akışı, belirli bir zaman aralığında yapılır.

- Sunum Katmanı (Presentation Layer): Bu katman, verilerin sunulması için yapılandırma ve kodlama yöntemlerini tanımlar. Bu katmanda, verilerin dönüştürülmesi ve kodlanması yapılır.

- Uygulama Katmanı (Application Layer): Bu katman, uygulamalar arasındaki veri alışverişinden sorumludur. Bu katmanda, e-posta, dosya paylaşımı, web sayfaları gibi farklı uygulamalar arasındaki iletişim gerçekleştirilir.

Her katman, üstündeki ve altındaki katmanlarla belirli bir protokol kullanarak iletişim kurar. OSI modeli, farklı ağ cihazları arasındaki iletişimi standartlaştırdığı için, farklı protokollerin ve cihazların birbirleriyle uyumlu çalışmasını sağlar.

## DOD

"DOD modeli" terimi, ağ güvenliği için kullanılan bir modeli ifade eder. Bu model, "Department of Defense" (Savunma Bakanlığı) tarafından geliştirilmiş ve kullanılan bir modeldir.

DOD modeli, ağ güvenliği için çeşitli katmanlardan oluşur. Bu katmanlar, fiziksel güvenlik, kişisel güvenlik, işletim sistemleri güvenliği, ağ güvenliği ve uygulama güvenliği gibi konuları kapsar.

DOD modelinin 7 katmanı şunlardır:

- Fiziksel güvenlik: Fiziksel güvenlik, ağ kaynaklarına fiziksel erişimi kısıtlamak ve korumakla ilgilidir. Bu katmanda, fiziksel erişimi kısıtlayan duvarlar, kapılar, kilitler ve benzeri cihazlar kullanılır.

- Kişisel güvenlik: Kişisel güvenlik, ağ kaynaklarına erişim izni olan kişilerin belirlenmesi ve bu kişilerin yetkilerinin yönetilmesiyle ilgilidir. Bu katmanda, kullanıcı adları, şifreler ve benzeri kimlik doğrulama yöntemleri kullanılır.

- İşletim sistemi güvenliği: İşletim sistemi güvenliği, ağa bağlı cihazlardaki işletim sistemlerinin güvenliğini sağlamayı amaçlar. Bu katmanda, işletim sistemi yamalarının uygulanması, antivirüs yazılımı ve diğer güvenlik araçları kullanılır.

- Ağ güvenliği: Ağ güvenliği, ağ kaynaklarına yapılan saldırıları engellemek ve ağa erişim izni olan cihazların güvenliğini sağlamakla ilgilidir. Bu katmanda, güvenlik duvarları, sanal özel ağlar (VPN'ler), ağ tabanlı saldırı tespit sistemleri (IDS'ler) ve benzeri cihazlar kullanılır.

- İletişim güvenliği: İletişim güvenliği, ağ üzerinden iletilen verilerin gizliliğini, bütünlüğünü ve doğruluğunu sağlamayı amaçlar. Bu katmanda, şifreleme, SSL/TLS gibi protokoller ve benzeri teknolojiler kullanılır.

- Uygulama güvenliği: Uygulama güvenliği, ağ üzerinde çalışan uygulamaların güvenliğini sağlamayı amaçlar. Bu katmanda, uygulama güvenlik duvarları, uygulama katmanı şifreleme protokolleri ve benzeri teknolojiler kullanılır.

- Yönetim güvenliği: Yönetim güvenliği, ağın yönetimini sağlayan cihazların güvenliğini sağlamayı amaçlar. 


![](/images/networklayers.png)


# LAN, WAN ve MAN

LAN, WAN ve MAN, bilgisayar ağlarındaki farklı ağ tiplerini ifade eden terimlerdir.

- LAN (Local Area Network): LAN, kısa mesafelerde birbirine bağlı olan cihazlar arasında veri iletişimi sağlayan ağlardır. Örneğin, bir ofis binasında birkaç bilgisayarın birbirine bağlı olduğu ağlar LAN örnekleri olabilir.

- WAN (Wide Area Network): WAN, geniş alanlarda uzak cihazlar arasında veri iletişimi sağlayan ağlardır. İnternet, bir WAN örneğidir. Bir şirketin merkez ofisi ve şube ofisleri arasında uzak mesafelerde bağlantı kurmak için kullanılan özel hatlar da WAN örnekleridir.

- MAN (Metropolitan Area Network): MAN, bir şehir veya bir bölge gibi kısmen daha büyük bir alanı kapsayan ağlardır. MAN'lar, birkaç farklı LAN'ın birbirine bağlanması ile oluşabilir.

Bu üç ağ türü, özellikle boyutları ve kapsama alanları açısından birbirlerinden farklıdırlar. LAN'lar küçük bir alanda kullanılırken, WAN'lar geniş alanları kapsar ve MAN'lar ise LAN ve WAN arasında bir orta nokta sağlar.

# tcp/ip

TCP/IP, İletişim Protokolü (TCP) ve İnternet Protokolü (IP) gibi bir dizi protokolden oluşan bir ağ iletişim protokolüdür. Bu protokol, İnternet'in temel altyapısıdır ve birçok farklı cihazın birbirleriyle iletişim kurmasını sağlar.

TCP, verilerin kesintisiz bir şekilde aktarılmasını sağlar ve iletişim sırasında hata kontrolü ve yeniden aktarım gibi özellikler sunar. IP ise, ağdaki cihazların adreslerini belirleyerek verilerin doğru hedeflere yönlendirilmesini sağlar.

TCP/IP, birçok farklı uygulama tarafından kullanılan bir protokoldür ve internet bağlantısı sağlayan cihazlar arasındaki iletişimde de kullanılır. Bu protokolün kullanılması, verilerin güvenli ve doğru bir şekilde iletilmesini sağlar.
