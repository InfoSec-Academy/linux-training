---
title: servis ekleme
weight: 2
---

systemd, bir Linux sistem yönetimi sistemidir. Sistemin açılış, kapanış ve hizmet yönetimi işlemlerini yönetir. Aynı zamanda, sistem loglarını yönetir, süreçleri yönetir ve sistem zamanlamasını sağlar.

Systemd, BSD init sistemine alternatif olarak geliştirilmiştir ve modern Linux dağıtımlarında varsayılan olarak kullanılır. Sistem yönetimi için daha yüksek seviyeli bir arayüz sağlar ve hizmetlerin birbirine bağımlılıklarını ve önceliklerini yönetebilir.

Örnek olarak, systemd üzerinden bir hizmetin durumunu kontrol edebilir, başlatıp durdurabilir, hizmet konfigürasyonunu değiştirebilirsiniz. Sistem başlatılırken çalıştırılacak hizmetleri belirlemek de mümkündür.

Bir önek oluşturalım. Yazmış olduğumuz bir scripti  servis haline getirelim:

İlk olarak, systemd servis dosyası oluşturmalısınız. Bunu yapmak için, /etc/systemd/system dizininde <servis-ismi>.service isimli bir dosya oluşturun ve aşağıdaki gibi içeriğini girin:

```tpl
[Unit]
Description=<servis-ismi>

[Service]
Type=simple
ExecStart=/bin/bash /path/to/script.sh

[Install]
WantedBy=multi-user.target
```

Eklemiş olduğumuz sistemin okuması için;

```tpl
systemctl daemon-reload
```


Daha sonra servisi etkinleştirin ve başlatmak için:

```tpl
systemctl enable <servis-ismi>.service
systemctl start <servis-ismi>.service
```


Servisin çalışıp çalışmadığını kontrol etmek için aşağıdaki komutu kullanabilirsiniz:

```tpl
systemctl status <servis-ismi>.service
```
