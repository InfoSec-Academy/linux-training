---
title: sözlükler
weight: 1
---

Bash script'inde sözlükler, anahtar-değer çiftlerinden oluşan bir yapıdır. Sözlükler oluşturmak için aşağıdaki gibi bir syntax kullanabilirsiniz:

```tpl
declare -A my_dict  # -A seçeneği, bir sözlük oluşturur
my_dict=([key1]=value1 [key2]=value2 [key3]=value3)
```

Yeni bir öğe eklemek için, aşağıdaki gibi bir syntax kullanabilirsiniz:

```tpl
my_dict[key4]=value4
```

Bir öğe silmek için, unset komutunu kullanabilirsiniz:

```tpl
unset my_dict[key2]
```

Bir sözlükteki tüm anahtarları veya tüm değerleri almak için, ! işaretini kullanabilirsiniz:

```tpl
echo ${!my_dict[@]}  # tüm anahtarları alır
echo ${my_dict[@]}  # tüm değerleri alır
```

```tpl
# Bir sözlük oluşturmak
declare -A colors
colors=([red]=FF0000 [green]=00FF00 [blue]=0000FF)
echo ${colors[green]}  # 00FF00

# Bir öğe eklemek
colors[yellow]=FFFF00
echo ${colors[@]}  # FF0000 00FF00 0000FF FFFF00

# Bir öğe silmek
unset colors[blue]
echo ${colors[@]}  # FF0000 00FF00 FFFF00

# Tüm anahtarları almak
echo ${!colors[@]}  # red green yellow
```
