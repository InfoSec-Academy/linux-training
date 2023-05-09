---
title: if
weight: 1
---

if koşulu, bir şartın doğru olup olmadığını kontrol etmek için kullanılır. Örneğin, belirli bir dosya varsa bir komutu çalıştırmak isteyebilirsiniz. Aşağıdaki örnekte, eğer "myfile.txt" adlı dosya varsa, o zaman "dosya var" yazdıracak, aksi takdirde "dosya yok" yazdıracak:

```tpl
if [ -f "myfile.txt" ]
then
    echo "dosya var"
else
    echo "dosya yok"
fi
```



## Örnek

```tpl
#!/bin/bash
# Bu script ile bir sayının tek mi çift mi olduğunu kontrol ediyoruz.

echo "Lütfen bir sayı giriniz: "
read sayi

if (( $sayi % 2 == 0 ))
then
    echo "$sayi sayısı çifttir."
else
    echo "$sayi sayısı tektir."
fi
```

Burada, kullanıcının girdiği sayının çift mi tek mi olduğunu kontrol ediyoruz. Girdiğimiz sayıyı 2'ye bölümünden kalan 0 ise sayı çift, kalan 1 ise sayı tek olarak değerlendiriliyor. Burada (( )) parantezleri, matematiksel işlemler yapmak için kullanılır.

