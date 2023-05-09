---
title: sed
weight: 9
---



Sed (Stream Editor) bir metin düzenleyicisidir. Temel olarak, bir metin akışının (dosya veya bir veri akışı gibi) içeriğini değiştirmek için kullanılır. Genellikle komut satırı aracılığıyla kullanılır ve birçok işletim sisteminde öntanımlı olarak yüklüdür.

Sed, düzenli ifadeler (regular expressions) kullanarak metin akışını işleyebilir. İşlem yaparken, orijinal veri akışını bozmadan yeni bir metin akışı oluşturur. Sed ayrıca, çeşitli sed komutları ve argümanları aracılığıyla, metin akışını filtrelemek, düzenlemek, eşleştirmek, değiştirmek, sıralamak ve biçimlendirmek gibi çeşitli işlemler gerçekleştirebilir.


- Metin dosyasında tüm "Lorem" kelimesini "lrm" ile değiştirme:

```tpl
[root@localhost ~]# cat lorem-ipsum.txt 
Lorem Ipsum, dizgi ve baskı endüstrisinde kullanılan mıgır metinlerdir. Lorem Ipsum, adı bilinmeyen bir matbaacının bir hurufat numune kitabı oluşturmak üzere bir yazı galerisini alarak karıştırdığı 1500'lerden beri endüstri standardı sahte metinler olarak kullanılmıştır. Beşyüz yıl boyunca varlığını sürdürmekle kalmamış, aynı zamanda pek değişmeden elektronik dizgiye de sıçramıştır. 1960'larda Lorem Ipsum pasajları da içeren Letraset yapraklarının yayınlanması ile ve yakın zamanda Aldus PageMaker gibi Lorem Ipsum sürümleri içeren masaüstü yayıncılık yazılımları ile popüler olmuştur.
[root@localhost ~]# sed 's/Lorem/lrm/g' lorem-ipsum.txt 
lrm Ipsum, dizgi ve baskı endüstrisinde kullanılan mıgır metinlerdir. lrm Ipsum, adı bilinmeyen bir matbaacının bir hurufat numune kitabı oluşturmak üzere bir yazı galerisini alarak karıştırdığı 1500'lerden beri endüstri standardı sahte metinler olarak kullanılmıştır. Beşyüz yıl boyunca varlığını sürdürmekle kalmamış, aynı zamanda pek değişmeden elektronik dizgiye de sıçramıştır. 1960'larda lrm Ipsum pasajları da içeren Letraset yapraklarının yayınlanması ile ve yakın zamanda Aldus PageMaker gibi lrm Ipsum sürümleri içeren masaüstü yayıncılık yazılımları ile popüler olmuştur.
```

Yukarıdaki çıktıda metin'in içerisinde "Lorem" kelimesini "lrm" olarak değiştirip metni basmıştır fakat metnin orjinal yapısını değiştirmemiştir.

- Dosyadan belirli bir satırdan başlayarak tüm satırları silme:

```tpl
[root@localhost ~]# sed '3,$d' lorem-ipsum.txt 
Lorem Ipsum, dizgi ve baskı endüstrisinde kullanılan mıgır metinlerdir. 
Lorem Ipsum, adı bilinmeyen bir matbaacının bir hurufat numune kitabı oluşturmak üzere bir yazı galerisini alarak karıştırdığı 1500'lerden beri endüstri standardı sahte metinler olarak kullanılmıştır. 
```

Yukarıdaki çıktıda 3'üncü satırdan dan başlayarak tüm satırları sildiğini görüyoruz.

- Belirli bir kelimeyi içeren satırların yerine başka bir kelime eklemek:

```tpl
[root@localhost ~]# sed '/Lorem/c\Yeni Satır' lorem-ipsum.txt 
Yeni Satır
Yeni Satır
Beşyüz yıl boyunca varlığını sürdürmekle kalmamış, aynı zamanda pek değişmeden elektronik dizgiye de sıçramıştır. 
Yeni Satır
```

Yukarıdaki örnekte "Lorem" kelimesi başka bir satır eklendiğini görüyoruz.



**sed** komutu, yaptığı değişiklikleri dosyada otomatik olarak kaydetmez, ancak çıktıyı başka bir dosyaya yönlendirmenizi veya dosyayı değiştirip değiştirmediğinizi kontrol etmenizi sağlar.


Örneğin, bir dosyadaki elma kelimesini armut ile değiştirmek ve çıktıyı output.txt dosyasına kaydetmek için aşağıdaki komutu kullanabilirsiniz:

```tpl
sed 's/elma/armut/g' input.txt > output.txt
```


Ayrıca, sed komutunu kullanarak dosyanın kendisini değiştirebilirsiniz. Bu durumda, -i seçeneğini kullanmalısınız. Örneğin:

```tpl
sed -i 's/elma/armut/g' input.txt
```
