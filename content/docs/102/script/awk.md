---
title: awk
weight: 10
---

Awk, Linux ve Unix tabanlı sistemlerde bulunan bir komut satırı aracıdır. Adını oluşturan AWK, komutun yaratıcısı Alfred Aho, Peter Weinberger ve Brian Kernighan'ın isimlerinin baş harflerinden gelir. Awk, metin dosyalarında belirli bir düzen içinde arama yapmak, dosyalardan belirli verileri çekmek, düzenlemek ve filtrelemek için kullanılır.

Awk, genellikle metin dosyalarındaki belirli satırları veya sütunları seçmek için kullanılır. Awk komutları, bir veya daha fazla eylem ve bir veya daha fazla desenden oluşur. Desenler, seçilen verilerin hangi kriterlere göre seçileceğini belirlerken, eylemler seçilen verilerin ne yapılacağını belirler.


- Metin dosyasında belirli bir kelimeyi arama ve satır numaralarını yazdırma:

```tpl
[root@localhost ~]# awk '/Hakkıdır/ {print NR}' istiklal-marsı.txt 
8
39
40
```

Yukarıda "Hakkıdır" kelimesinin istiklal-marsı.txt içerisinde hangi satırlarda bulunduğunun çıktısını görmekteyiz.

- Dosyadaki belirli bir satırdan itibaren yazdırma:


```tpl
[root@localhost ~]# awk 'NR>=5 && NR<=10' istiklal-marsı.txt 
Çatma, kurban olayım çehreni ey nazlı hilâl!
Kahraman ırkıma bir gül… ne bu şiddet bu celâl?
Sana olmaz dökülen kanlarımız sonra helâl,
Hakkıdır, Hakk’a tapan, milletimin istiklâl.
Ben ezelden beridir hür yaşadım, hür yaşarım.
Hangi çılgın bana zincir vuracakmış? Şaşarım!
```

Yukarıda 5 ve 10 satır arasındaki yerlerin yazdırıldığını görüyoruz.


- Dosyadaki belirli satır ve sütünlarını yazdırma:

```tpl
[root@localhost ~]# awk 'NR>=5 && NR<=10 {print $1,$3}' istiklal-marsı.txt 
Çatma, olayım
Kahraman bir
Sana dökülen
Hakkıdır, tapan,
Ben beridir
Hangi bana
```



