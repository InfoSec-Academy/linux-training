---
title: grub
weight: 2
---

GRUB (Grand Unified Bootloader), bilgisayarınızı açarken hangi işletim sistemini başlatacağınızı seçmenize izin veren bir önyükleme yükleyicisidir. GRUB, Linux ve diğer işletim sistemlerinin önyükleme işlemini kolaylaştırır.

GRUB ayarları genellikle "/etc/default/grub" dosyasında bulunur. Bu dosyada, GRUB önyükleme menüsünün görünümünü ve davranışını değiştirebileceğiniz bir dizi değişken bulunur.

Örneğin, "GRUB_TIMEOUT" değişkeni, önyükleme menüsünün görüntülenme süresini belirler. "GRUB_DEFAULT" değişkeni, önyükleme menüsünde varsayılan olarak seçilen işletim sistemini belirler. "GRUB_CMDLINE_LINUX" değişkeni, Linux çekirdeğinin önyükleme argümanlarını belirtir.

GRUB ayarlarınızı değiştirmek için, "/etc/default/grub" dosyasını bir metin editörü ile açın, değişikliklerinizi yapın ve dosyayı kaydedin. Daha sonra, "sudo update-grub" komutunu kullanarak değişiklikleri uygulayabilirsiniz. Bu komut, GRUB konfigürasyon dosyasını yeniden oluşturacak ve değişikliklerinizi etkinleştirecektir.


```tlp
[root@localhost ~]# cat /etc/default/grub 
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="rhgb quiet"
GRUB_DISABLE_RECOVERY="true"
GRUB_ENABLE_BLSCFG=true
```


- **GRUB_TIMEOUT=5**: Bu, GRUB menüsünün görüntülenme süresini 5 saniyeye ayarlar. Bu süre sonunda, varsayılan işletim sistemi otomatik olarak başlatılır.

- **GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"**: Bu satır, GRUB menüsünde gösterilecek dağıtım adını ayarlar. Bu satır örnek olarak CentOS/RHEL işletim sistemlerinde kullanılabilir.

- **GRUB_DEFAULT=saved**: Bu, son seçilen işletim sistemini varsayılan olarak ayarlar. Bu özelliği kullanarak, her seferinde manuel olarak seçmeniz gerekmez.

- **GRUB_DISABLE_SUBMENU=true**: Bu, alt menülerin kullanılmasını devre dışı bırakır. Bu özellik sayesinde, GRUB menüsü daha basit ve kullanıcı dostu hale getirilir.

- **GRUB_TERMINAL_OUTPUT="console"**: Bu, GRUB'un terminale çıktı göndermesini ayarlar.

- **GRUB_CMDLINE_LINUX="rhgb quiet"**: Bu, Linux çekirdeği için komut satırı parametrelerini belirler. rhgb ve quiet parametreleri, önyükleme işlemi sırasında çıktıyı minimumda tutar ve daha iyi bir kullanıcı deneyimi sağlar.

- **GRUB_DISABLE_RECOVERY="true"**: Bu, kurtarma modunu devre dışı bırakır.

- **GRUB_ENABLE_BLSCFG=true**: Bu, BootLoaderSpecification (BLS) yapılandırmasını etkinleştirir. Bu özellik, işletim sistemi güncelleştirmeleri sırasında GRUB yapılandırmasını daha kolay hale getirir.


## Bir modülü disable etmek

Bir kernel modülünü GRUB'da devre dışı bırakmak için, GRUB_CMDLINE_LINUX satırına modprobe.blacklist=modul_adı parametresini eklemeniz gerekiyor. Burada, modul_adı kısmını devre dışı bırakmak istediğiniz kernel modülünün adı ile değiştirmelisiniz.

Örneğin, eğer pcspkr kernel modülünü devre dışı bırakmak isterseniz, /etc/default/grub dosyasındaki GRUB_CMDLINE_LINUX satırını aşağıdaki gibi değiştirebilirsiniz:

```tlp
GRUB_CMDLINE_LINUX="rhgb quiet modprobe.blacklist=pcspkr"
```

Yapılan değişiklikleri kaydettikten sonra, sudo update-grub komutuyla GRUB yapılandırmasını güncellemeniz gerekiyor.

{{< hint info >}}
pcspkr modülü, Linux çekirdeği tarafından yüklenen bir kernel modülüdür. Bu modül, sistemin hoparlöründen çıkan tiz ve kısa bip seslerini üretmek için kullanılır.
{{< /hint >}}


GRUB ayarları ile yapabileceğiniz bazı şeyler şunlardır:

- Başlangıç ​​bekleme süresini ayarlama veya değiştirme
- Önyükleme sırasında kullanılacak varsayılan işletim sistemi veya çekirdek sürümünü belirleme
- Kernel parametrelerini belirleme veya düzenleme
- Kernel modüllerini yükleme veya kaldırma
- Sistem hatalarının veya diğer mesajların konsolda görüntülenip görüntülenmeyeceğini ayarlama
- Başlatma işleminin başarısız olması durumunda, sistem kurtarma modunda açılabilir
- Başlangıçta farklı bir dil ve klavye düzeni seçebilme
