---
title: while
weight: 1
---

while döngüsü, belirli bir şart doğru olduğu sürece bir işlemi tekrar tekrar yapmak için kullanılır. Örneğin, bir dizi sayıyı toplamak isteyebilirsiniz. Aşağıdaki örnekte, 1'den 5'e kadar olan sayıları toplar:

```tpl
sum=0
i=1

while [ $i -le 5 ]
do
    sum=$((sum+i))
    i=$((i+1))
done

echo "Toplam: $sum"
```


## Örnek

```tpl
#!/bin/bash
# Bu script ile sayıları 1'den 10'a kadar yazdırıyoruz.

sayi=1
while [ $sayi -le 10 ]
do
    echo $sayi
    sayi=$((sayi+1))
done
```


Burada, **sayi** değişkenini 1'den başlatıyoruz. Döngü her çalıştığında, ekrana sayi değişkeninin değerini yazdırıyoruz ve sayi değişkenini 1 artırıyoruz. Bu şekilde döngü 10'a kadar devam ediyor.

