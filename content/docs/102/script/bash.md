---
title: bash script
weight: 1
---

## Bash script nedir?
Bash scriptler, bir dizi komutu veya bir betiği çalıştıran, Linux veya diğer Unix benzeri işletim sistemlerinde çalışan betiklerdir.

## Bash scriptler neden kullanılır?
Bash scriptler, işlem tekrarlamaları, rutin görevlerin otomatikleştirilmesi, sistem yapılandırmaları, programlama gibi birçok farklı amaçla kullanılabilirler.

## Bash script dosyası oluşturma
Bir bash script dosyası oluşturmak için bir metin editörü kullanabilirsiniz.  Örnek bir bash script dosyası adı: "my_script.sh"

## Bash script dosyası izinlerinin ayarlanması
Bash script dosyasını çalıştırmak için dosyanın çalıştırılabilir olması gerekiyor. Bu nedenle, dosyaya aşağıdaki komutu kullanarak çalıştırma izinleri vermeniz gerekiyor:

```tpl
chmod +x my_script.sh
```

## Bash script dosyasının ilk satırı
Bir bash script dosyasının ilk satırı, scriptin hangi kabukta çalışacağını belirtir. Çoğu durumda, ilk satırı "#!/bin/bash" şeklinde yazmak yeterlidir.

## Comment eklemek
Bash script dosyalarına açıklama eklemek, diğer kullanıcıların dosyanın amacını ve kullanımını anlamalarına yardımcı olabilir. Açıklamalar # işareti ile başlar.

## Değişkenler
Bir bash script içinde değişkenler kullanarak birçok görevi yerine getirebilirsiniz. Bir değişken tanımlamak için aşağıdaki gibi bir formül kullanabilirsiniz:

```tpl
variable_name=value
```

Örneğin:

```tpl
message="Hello World"
echo $message
```

"Hello World" mesajını ekranda gösterir.

