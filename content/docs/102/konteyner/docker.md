---
title: docker
weight: 3
---

Docker, uygulamaların bir yazılım paketi olarak paketlenmesi, taşınması ve çalıştırılması için açık kaynaklı bir konteyner teknolojisidir. Docker, uygulamaların ve bağımlılıklarının sanal ortamlarda (konteynerler) çalıştırılmasını sağlar, bu sayede uygulamaların daha hızlı, güvenilir ve taşınabilir olmasını sağlar. Docker konteyner teknolojisi, farklı işletim sistemleri ve altyapılar üzerinde de çalışabilir.

Docker kullanarak bir uygulama çalıştırmak için öncelikle Docker Engine yazılımının kurulması gerekiyor. Daha sonra, uygulamanın Dockerfile adı verilen bir dosyada tanımlanması ve Docker build komutu kullanılarak bir Docker imajının oluşturulması gerekiyor. Bu imaj, uygulamanın ve bağımlılıklarının tam bir kopyasını içerir. Bu imaj, Docker Hub gibi bir imaj deposuna yüklenerek başkaları tarafından kullanılabilir hale getirilebilir.

Bir Docker imajı çalıştırmak için Docker run komutu kullanılır. Bu komut, bir Docker konteyneri oluşturur ve imajdaki uygulamanın bu konteynerde çalışmasını sağlar. Docker konteynerleri, izole edilmiş bir çevrede çalıştığı için birden çok konteyner aynı anda aynı makinede çalıştırılabilir.

Docker, uygulamaları hızlı bir şekilde dağıtmak ve güncellemek için de kullanılabilir. Docker Hub gibi bir imaj deposuna yüklenen imajlar, birden çok sunucuda hızlı bir şekilde çalıştırılabilir. Bu sayede, uygulamaların hızlı bir şekilde dağıtılması ve güncellenmesi mümkün hale gelir.

Özetle, Docker konteyner teknolojisi, uygulamaların izole edilmiş sanal ortamlarda çalıştırılmasını sağlayan açık kaynaklı bir teknolojidir.



## Kurulum

```tpl
yum install docker-ce docker-ce-cli containerd.io
```

## Başlatma

Docker servisini başlatmak için aşağıdaki komutu çalıştırın:

```tpl
systemctl start docker
```

## Konteyner Kaldırma

İlk konteyneri çalıştırmak için, örneğin Nginx web sunucusunu çalıştırmak için aşağıdaki komutu kullanabilirsiniz:

```tpl
docker run -d -p 8080:80 nginx
```

Bu komut, Nginx konteyner imajını indirir ve 8080 portundan gelen trafiği konteyner içindeki 80 numaralı porta yönlendirir.

Konteynerin çalışıp çalışmadığını görmek için aşağıdaki komutu çalıştırabilirsiniz:

```tpl
docker ps
```

## Durdurma

Konteyneri durdurmak için aşağıdaki komutu kullanabilirsiniz:

```tpl
docker stop <CONTAINER_ID>
```

## Silme

Konteyneri silmek için aşağıdaki komutu kullanabilirsiniz:

```tpl
docker rm <CONTAINER_ID>
```