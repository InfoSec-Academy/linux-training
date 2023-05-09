---
title: lxc
weight: 2
---

LXC (Linux Containers) bir konteynerleştirme teknolojisidir. LXC, Linux çekirdeği için bir sanallaştırma aracıdır ve birden fazla izole edilmiş Linux çevresi (container) çalıştırmaya olanak sağlar. Konteyner teknolojisi, her bir container'ın bağımsız çalışabilen bir işletim sistemi ve uygulama yığınına sahip olduğu bir yöntemdir.

LXC, her bir container'ın host işletim sistemi üzerinde bir izolasyon katmanı sağlar. Bu izolasyon katmanı, container'ın bağımsız bir dosya sistemi, ağ arabirimi, kullanıcıları ve bağlı uygulamaları içerdiği anlamına gelir. LXC, container'ların kaynaklarını (CPU, bellek, disk alanı vb.) doğrudan host işletim sisteminden alır ve böylece sanal makinelere göre daha hafif bir yapıdadır.

LXC, container'ların yönetimini kolaylaştırmak için bir dizi araç sunar. Bu araçlar, container'ları başlatma, durdurma, oluşturma, silme ve yönetme işlemlerini yapmak için kullanılabilir. LXC ayrıca, farklı container'ların birbirleriyle nasıl iletişim kuracağına dair ayarları da yapmak için bir dizi ağ aracı sunar.

LXC'nin avantajları arasında yüksek performans, düşük kaynak tüketimi ve esneklik yer alır. LXC, sanal makinelerle karşılaştırıldığında daha hızlı bir başlatma süresine sahiptir ve daha hafiftir. Bununla birlikte, LXC container'ları tamamen izole edemez ve sınırlı bir güvenlik seviyesi sağlar.


## Yükleme

İlk olarak, sistemde LXC kurulu değilse, paket yöneticisi aracılığıyla LXC paketlerini yüklemeniz gerekiyor. 

```tpl
yum install lxc lxc-templates
```

## Konteyner Oluşturma

LXC yüklendikten sonra, bir LXC konteyneri oluşturabilirsiniz. Aşağıdaki komutu kullanarak yeni bir konteyner oluşturabilirsiniz:

```tpl
lxc-create -t download -n infosec -- -d fedora -r 38 -a amd64
```

## Başlatma

Konteyneri başlatmak için aşağıdaki komutu kullanabilirsiniz:

```tpl
lxc-start -n infosec
```

## Bağlanma

Konteynerinize bağlanmak için aşağıdaki komutu kullanabilirsiniz:

```tpl
lxc exec infosec -- /bin/bash
```

## Durdurma

```tpl
lxc-stop -n infosec
```

## Silme

```tpl
lxc-destroy -n infosec
```

