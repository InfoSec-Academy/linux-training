---
title: switch/case
weight: 3
---

switch/case koşulu, birden fazla koşulun kontrol edilmesi gerektiğinde kullanılır. Örneğin, bir seçim menüsü oluşturmak isteyebilirsiniz. Aşağıdaki örnekte, kullanıcının girdiği sayıya göre bir işlem yapılır:

```tpl
echo "1. İşlem"
echo "2. İşlem"
echo "3. İşlem"
echo "Lütfen bir sayı girin:"
read num

case $num in
    1)
        echo "İşlem 1"
        ;;
    2)
        echo "İşlem 2"
        ;;
    3)
        echo "İşlem 3"
        ;;
    *)
        echo "Geçersiz sayı"
        ;;
esac
```


## Örnek

```tpl
#!/bin/bash
# Bu script ile belirtilen ayın kaç gün çektiğini yazdırıyoruz.

echo "Hangi ay için gün sayısını öğrenmek istiyorsunuz? (1-12)"
read ay

case $ay in
    1 | 3 | 5 | 7 | 8 | 10 | 12)
        echo "Bu ay 31 gün çeker."
        ;;
    4 | 6 | 9 | 11)
        echo "Bu ay 30 gün çeker."
        ;;
    2)
        echo "Bu ay 28 veya 29 gün çeker."
        ;;
    *)
        echo "Lütfen geçerli bir ay giriniz. (1-12)"
        ;;
esac
```

Burada, kullanıcının girdiği ay değerine göre o ayın kaç gün çektiğini belirliyoruz. case yapısında, girilen ay değerini kontrol ediyoruz. Eğer girilen ay 1, 3, 5, 7, 8, 10 veya 12 ise, o ayın 31 gün çektiğini yazdırıyoruz.

