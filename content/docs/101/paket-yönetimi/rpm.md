---
title: RPM
weight: 1
---

RPM (Red Hat Package Manager), Linux işletim sistemi için bir paket yönetim sistemidir. RPM, Red Hat ve diğer bazı Linux dağıtımları tarafından kullanılır ve paketlerin kurulumu, kaldırılması, güncellenmesi ve yönetimi için kullanılır.

RPM, paketlerin dosya sistemine nasıl yerleştirileceği ve kurulum sırasında hangi diğer paketlerin gereksinimlerinin karşılanacağı gibi konuları ele alır. Ayrıca paketlerin diğer sistemlerle uyumlu olup olmadığını kontrol eder ve uyumsuzluk durumunda uygun hataları rapor eder.

RPM, özellikle sunucu sistemleri gibi büyük ve karmaşık Linux sistemlerinde kullanımı yaygındır. RPM paketleri, yazılım geliştiricileri tarafından oluşturulabilir ve ayrıca çeşitli depolardan indirilebilir. RPM ayrıca, özellikle Red Hat ve Fedora gibi bazı Linux dağıtımları için yazılım güncelleme araçları tarafından da kullanılır.

## rpm -qa
Komutu, sisteme yüklenmiş tüm RPM paketlerinin listesini görüntülemek için kullanılır. Bu komut, kurulu olan tüm paketlerin isimlerini, sürümlerini ve yayıncılarını gösterir.

```tpl
[ergunbilsel@localhost linux-101]$ rpm -qa
khmeros-fonts-common-5.0-30.fc33.noarch
adwaita-qt4-1.1.3-4.fc33.x86_64
gpg-pubkey-9570ff31-5e3006fb
```

## rpm -q

Belirli bir RPM paketinin sistemde yüklü olup olmadığını kontrol etmek için kullanılır. Bu komut, paket adını belirtilen bir argüman olarak alır ve paketin adını, sürümünü ve yayıncısını görüntüler.

```tpl
[ergunbilsel@localhost linux-101]$ rpm -q adwaita-qt4-1.1.3-4.fc33.x86_64
adwaita-qt4-1.1.3-4.fc33.x86_64
[ergunbilsel@localhost linux-101]$ rpm -q adwaita-qt4-1.1.3-4.fc33.x86_6
adwaita-qt4-1.1.3-4.fc33.x86_6 paketi kurulu değil
```

## rpm -Uvh

Yeni bir RPM paketini yüklemek veya mevcut bir paketi güncellemek için kullanılır. Bu komut, aşağıdaki üç adımı gerçekleştirir:

1. Paketi yüklemek veya güncellemek için gerekli izinleri kontrol eder.
2. Var olan bir paketin yerine yeni bir sürümü yükler.
3. Yeni paketin kurulumunu tamamlar ve kurulum işlemi sırasında ayrıntılı çıktılar gösterir.

"U" seçeneği, güncelleştirme işlemi için kullanılırken, "h" seçeneği, işlem sırasında ilerlemeyi gösteren ayrıntılı bir çıktı sağlar. "v" seçeneği ise, yüklenen veya güncellenen paketlerle ilgili daha fazla ayrıntı sağlar.

```tpl
[ergunbilsel@localhost linux-101]$ sudo rpm -Uvh pam_ssh-2.3-12.fc37.x86_64.rpm [sudo] password for ergunbilsel: 
Verifying...                          ################################# [100%]
Hazırlanıyor...                     ################################# [100%]
Güncelleniyor / kuruluyor...
   1:pam_ssh-2.3-12.fc37              ################################# [100%]
[ergunbilsel@localhost linux-101]$ 
```
## rpm -e

RPM paketini kaldırmak için kullanılır. Bu komut, sisteme yüklenmiş olan bir paketi kaldırır ve sistemden tüm paket dosyalarını ve yapılandırma dosyalarını siler.

Komut, kaldırılacak paketin adını argüman olarak alır. Örneğin, "rpm -e myapp" komutu, "myapp" adlı bir paketi kaldırır.

Eğer kaldırılmak istenen paket, başka bir paket tarafından kullanılıyorsa, "rpm" komutu bir hata mesajı verebilir. Bu durumda, kaldırılacak paketi kullanan diğer paketlerin de önce kaldırılması gerekebilir.



```tpl
[ergunbilsel@localhost linux-101]$ sudo rpm -e pam_ssh
```

## /var/lib/rpm

Red Hat tabanlı Linux sistemlerinde RPM paket yöneticisinin kullandığı veritabanı dosyalarının depolandığı dizindir. Bu dizin, RPM paketlerinin yüklü olduğu ve kaldırıldığı hakkında bilgiyi içeren bir veritabanı dosyası olan "Packages" dosyasını ve paket imza anahtarlarının depolandığı birkaç diğer veritabanı dosyasını içerir.

Bu dizin ayrıca, RPM paket yöneticisinin veritabanına erişmek için kullandığı diğer veritabanı dosyalarını da içerir. Bu dosyaların bazıları, imza anahtarları ve önbellek dosyalarını depolar.

"/var/lib/rpm" dizini, RPM paketlerinin yönetimi için önemli bir rol oynar ve bu nedenle, bu dizinin izinleri ve bütünlüğü dikkatlice korunmalıdır. Ayrıca, RPM paketleri elle düzenlenmeden önce, bu dizin ve alt dizinlerindeki dosyaların yedeklenmesi önerilir.

```tpl
[ergunbilsel@localhost linux-101]$ cd /var/lib/rpm
[ergunbilsel@localhost rpm]$ ls
rpmdb.sqlite  rpmdb.sqlite-shm  rpmdb.sqlite-wal
```

{{< hint info >}} Bir RPM Paketinin İçeriği
![](/images/rpm_include.png)


{{< /hint >}}
## yum

Red Hat tabanlı Linux dağıtımlarında kullanılan bir paket yöneticisidir. Yum, RPM paket yöneticisinin üzerine inşa edilmiştir ve RPM paketlerini indirme, kurma, güncelleştirme ve kaldırma işlemlerini gerçekleştirebilir. Yum **(Yellowdog Updater, Modified)** ayrıca, sistemdeki paketlerin bağımlılıklarını çözer ve yeni bir paket yüklemek istendiğinde, gerekli diğer paketleri otomatik olarak indirir.


```tpl
[ergunbilsel@localhost linux-101]$ cd /var/lib/rpm
[ergunbilsel@localhost rpm]$ ls
rpmdb.sqlite  rpmdb.sqlite-shm  rpmdb.sqlite-wal
```

##  yum list

```tpl
[ergunbilsel@localhost rpm]$ yum list | wc -l
Error: 'virtualbox' deposu için üst veriler indirilemedi: repomd.xml GPG signature verification error: Bad GPG signature
Depolar yok sayılıyor: virtualbox
70733
```

{{< hint info >}} Bir repo silelim


```tpl
[ergunbilsel@localhost static]$ yum repolist 
depo id                                                           depo ismi
Mongodb                                                           MongoDB Repository
anydesk                                                           AnyDesk Fedora - stable
docker-ce-stable                                                  Docker CE Stable - x86_64
fedora                                                            Fedora 37 - x86_64
fedora-cisco-openh264                                             Fedora 37 openh264 (From Cisco) - x86_64
fedora-modular                                                    Fedora Modular 37 - x86_64
google-chrome                                                     google-chrome
opera                                                             Opera packages
rpmfusion-free                                                    RPM Fusion for Fedora 37 - Free
rpmfusion-free-updates                                            RPM Fusion for Fedora 37 - Free - Updates
rpmfusion-nonfree                                                 RPM Fusion for Fedora 37 - Nonfree
rpmfusion-nonfree-updates                                         RPM Fusion for Fedora 37 - Nonfree - Updates
slack                                                             slack
teams                                                             teams
teamviewer                                                        TeamViewer - x86_64
updates                                                           Fedora 37 - x86_64 - Updates
updates-modular                                                   Fedora Modular 37 - x86_64 - Updates
virtualbox                                                        Fedora  -  - VirtualBox
```
Öncelikle mevcut repo listesini görüntüliyelim

## yum-config-manager --disable

```tpl
[ergunbilsel@localhost static]$ sudo yum-config-manager --disable virtualbox 
[ergunbilsel@localhost static]$ yum repolist 
depo id                                                           depo ismi
Mongodb                                                           MongoDB Repository
anydesk                                                           AnyDesk Fedora - stable
docker-ce-stable                                                  Docker CE Stable - x86_64
fedora                                                            Fedora 37 - x86_64
fedora-cisco-openh264                                             Fedora 37 openh264 (From Cisco) - x86_64
fedora-modular                                                    Fedora Modular 37 - x86_64
google-chrome                                                     google-chrome
opera                                                             Opera packages
rpmfusion-free                                                    RPM Fusion for Fedora 37 - Free
rpmfusion-free-updates                                            RPM Fusion for Fedora 37 - Free - Updates
rpmfusion-nonfree                                                 RPM Fusion for Fedora 37 - Nonfree
rpmfusion-nonfree-updates                                         RPM Fusion for Fedora 37 - Nonfree - Updates
slack                                                             slack
teams                                                             teams
teamviewer                                                        TeamViewer - x86_64
updates                                                           Fedora 37 - x86_64 - Updates
updates-modular                                                   Fedora Modular 37 - x86_64 - Updates
```

{{< /hint >}}

## yum search

YUM  paket yöneticisi komutudur ve kullanıcılara, bir veya daha fazla anahtar kelime kullanarak, mevcut paket depolarında arama yapma imkanı sağlar.

```tpl
[ergunbilsel@localhost static]$ yum search python3.8
========================================================== Ad Tam Olarak Eşleşti: python3.8 ==========================================================
python3.8.x86_64 : Version 3.8 of the Python interpreter
python3.8.i686 : Version 3.8 of the Python interpreter
```

Örneğin, "yum search python3.8" komutu, mevcut depolarda "python3.8" anahtar kelimesini içeren tüm paketleri listeleyecektir. Eğer bir paket adı tam olarak bilinmiyorsa, bu komut arama sonuçlarında paket adının bir parçasını da arayabilir.

## yum provides

Paket yöneticisi komutudur ve belirli bir dosyanın hangi pakete ait olduğunu belirlemek için kullanılır.

```tpl
[ergunbilsel@localhost static]$ yum  provides git
git-2.37.3-1.fc37.x86_64 : Fast Version Control System
Depo        : fedora
Şuradan eşleşti:
Sağlayıcı    : git = 2.37.3-1.fc37
```

## yum install

Belirtilen paketi veya paketleri yüklemek için kullanılır.

Örneğin, "yum install firefox" komutu, "firefox" paketini yükler.

## yum update

Yüklü tüm paketleri en son sürümlerine güncellemek için kullanılır.

YUM, paketleri güncelleme işlemi sırasında bağımlılıkları da kontrol eder ve gerektiğinde ilgili paketleri yükleyerek güncelleme işlemini tamamlar. Bu nedenle, "yum update" komutu, sistemdeki tüm paketleri güncellemek için yaygın bir kullanım şeklidir.

## yum grouplist

Yüklü ve kullanıma hazır paket gruplarını ve alt gruplarını listelemek için kullanılır.

```tpl
[ergunbilsel@localhost static]$ yum grouplist
Son üst veri süresi sona erme denetimi: 2:52:44 önce, Çrş 26 Nis 2023 11:26:03 tarihinde.
Kullanılabilir Ortam Grupları:
   Fedora Özel İşletim Sistemi
   Asgari Kurulum
   Fedora Sunucu Sürümü
   Fedora İş İstasyonu
   Fedora Bulut Sunucu
   KDE Plasma Çalışma Alanları
   Xfce Masaüstü
   LXDE Masaüstü
   LXQt Masaüstü
   Cinnamon Masaüstü
   MATE Masaüstü
   Sugar Masaüstü Ortamı
   Deepin Masaüstü
   Budgie Desktop
   Geliştirme ve Yaratıcılık İş İstasyonu
   Web Sunucusu
   Alt Yapı Sunucusu
   i3 desktop
Kurulu Ortam Grupları:
   Temel Masaüstü
Kurulu Gruplar:
   Konteyner Yönetimi
   Geliştirme Araçları
   LibreOffice
   GNOME
   Fontlar
   Donanım Desteği
Kullanılabilir Gruplar:
   3B Yazdırma
   Yönetim Araçları
   Ses Üretimi
   Yazım ve Yayım
   Budgie
   Budgie Desktop Applications
   C Geliştirme Araçları ve Kütüphaneleri
   Bulut Alt Yapısı
   Bulut Yönetim Araçları
   Compiz
   D Geliştirme Araçları ve Kütüphaneleri
   Tasarım Takımı
   Etki Alanı Üyeliği
   Metin Düzenleyiciler
   Eğitim Yazılımı
   Elektronik Laboratuvarı
   Mühendislik ve Bilim
   FreeIPA Sunucusu
   Başsız Yönetim
   MATE Uygulamaları
   Milkymist
   Ağ Sunucuları
   Nöron Modelleme Simülatörleri
   Ofis/Verimlilik
   Python Sınıfı
   Bilimsel Python
   Robotik
   RPM Geliştirme Araçları
   Güvenlik Laboratuvarı
   Metin tabanlı İnternet
   Pencere Yöneticileri
   Deepin Masaüstü Ortamı
   Grafiksel İnternet
   KDE
   Oyunlar ve Eğlencelik
   Ses ve Görüntü
   Sistem Araçları
```

"yum grouplist" komutu, sistemde hangi paket gruplarının mevcut olduğunu anlamak için faydalıdır. Ancak, tüm paket grupları hakkında ayrıntılı bilgi almak isteyen kullanıcılar, "yum groupinfo [grup adı]" komutunu kullanarak daha fazla bilgi alabilirler.

```tpl
[ergunbilsel@localhost linux-101]$ yum groupinfo GNOME
Grup: GNOME
 Tanım: GNOME son derece sezgisel ve kullanıcı dostu bir masaüstü ortamıdır.
 Zorunlu Paketler:
   dconf
   gdm
   gnome-boxes
   gnome-connections
   gnome-control-center
   gnome-initial-setup
   gnome-session-wayland-session
   gnome-session-xsession
   gnome-settings-daemon
   gnome-shell
   gnome-software
   gnome-terminal
   gnome-text-editor
   nautilus
   polkit
   yelp
 Öntanımlı Paketler:
   ModemManager
   NetworkManager-adsl
   NetworkManager-openconnect-gnome
   NetworkManager-openvpn-gnome
   NetworkManager-ppp
   NetworkManager-pptp-gnome
   NetworkManager-ssh-gnome
   NetworkManager-vpnc-gnome
   NetworkManager-wwan
   PackageKit-command-not-found
   PackageKit-gtk3-module
   adobe-source-code-pro-fonts
   at-spi2-atk
   at-spi2-core
   avahi
   baobab
   cheese
   eog
   evince
   evince-djvu
   evince-nautilus
   fprintd-pam
   glib-networking
   gnome-backgrounds
   gnome-bluetooth
   gnome-browser-connector
   gnome-calculator
   gnome-calendar
   gnome-characters
   gnome-classic-session
   gnome-clocks
   gnome-color-manager
   gnome-contacts
   gnome-disk-utility
   gnome-font-viewer
   gnome-logs
   gnome-maps
   gnome-photos
   gnome-remote-desktop
   gnome-system-monitor
   gnome-terminal-nautilus
   gnome-themes-extra
   gnome-user-docs
   gnome-user-share
   gnome-weather
   gvfs-afc
   gvfs-afp
   gvfs-archive
   gvfs-fuse
   gvfs-goa
   gvfs-gphoto2
   gvfs-mtp
   gvfs-smb
   libcanberra-gtk3
   libproxy-duktape
   librsvg2
   libsane-hpaio
   mesa-dri-drivers
   mesa-libEGL
   orca
   rygel
   sane-backends-drivers-scanners
   simple-scan
   sushi
   systemd-oomd-defaults
   totem
   tracker
   tracker-miners
   xdg-desktop-portal
   xdg-desktop-portal-gnome
   xdg-desktop-portal-gtk
   xdg-user-dirs-gtk
 İsteğe Bağlı Paketler:
   vlc
```

## Repolar

Örnek bir repo taslağı

```tpl
[$repo]
name=My Repository
baseurl=http://path/to/MyRepo
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-MyRep
```