---
title: listeler
weight: 1
---


Bash script'inde listeler, ayrılmış öğelerden oluşan bir dizi gibi davranır. Listeleri oluşturmak için aşağıdaki gibi bir syntax kullanabilirsiniz:

```tpl
my_array=(item1 item2 item3)
```


Listelerdeki öğeler, sıfırdan başlayan bir indeksle erişilir. Örneğin, my_array'in ikinci öğesine erişmek için aşağıdaki syntax kullanılabilir:

```tpl
echo ${my_array[1]}
```

Yeni öğeleri listeye eklemek için, += işlemini kullanabilirsiniz:

```tpl
my_array+=(item4)
```

Öğeleri silmek için, unset komutunu kullanabilirsiniz:
```tpl
unset my_array[1]  # ikinci öğeyi sil
```


```tpl
# Bir liste oluşturmak
fruits=(elma armut kiraz)
echo ${fruits[1]}  # armut

# Listeye yeni bir öğe eklemek
fruits+=(portakal)
echo ${fruits[@]}  # elma armut kiraz portakal

# Bir öğe silmek
unset fruits[2] 
echo ${fruits[@]}  # elma armut portakal
```
