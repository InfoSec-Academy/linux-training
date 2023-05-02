---
title: static IP
weight: 6
---

{{< hint info >}}
"nmcli" (Network Manager Command Line Interface), Linux işletim sistemlerinde Network Manager'ı yönetmek için kullanılan bir komut satırı arayüzüdür. Bu araç, kablosuz ve kablolu ağ bağlantılarını yapılandırmak, yönetmek ve izlemek için kullanılabilir.

"nmcli" aracı, ağ bağlantılarını yapılandırmak, düzenlemek ve silmek için kullanılabilir. Ayrıca, ağ bağlantılarını listelemek, bağlantı durumunu kontrol etmek ve ağ profillerini yönetmek için de kullanılabilir. Bu araç, komut satırından çalıştırıldığı için otomasyon ve betikleme için de uygundur.
{{< /hint >}}

{{< hint info >}}
Önceden, NetworkManager ağ profillerini ifcfg biçiminde saklıyordu.
bu dizinde (/etc/sysconfig/network-scripts/). Ancak, ifcfg
format kullanımdan kaldırıldı.
{{< /hint >}}


Öncelikle mevcut network kartlarını görüntüleyelim;

```tpl
[root@localhost ~]# nmcli connection show
NAME    UUID                                  TYPE      DEVICE 
enp1s0  081eac1c-b9ab-3f1f-ba81-4acfbca5e469  ethernet  enp1s0 
lo      4f3307e7-8e4f-4817-bade-89180fd581a1  loopback  lo  
```

Yeni bir nic profili tanımlayalım;

```tpl
root@localhost ~]# nmcli con add type ethernet con-name "static-ip" ifname enp1s0 ipv4.addresses 192.168.122.150/24 gw4 192.168.122.1
Connection 'static-ip' (be6f4767-448e-4daa-89b6-55e335c09071) successfully added.
```

Mevcut profilleri görüntüliyelim;

```tpl
[root@localhost ~]# nmcli connection show
NAME       UUID                                  TYPE      DEVICE 
enp1s0     081eac1c-b9ab-3f1f-ba81-4acfbca5e469  ethernet  enp1s0 
lo         4f3307e7-8e4f-4817-bade-89180fd581a1  loopback  lo     
static-ip  be6f4767-448e-4daa-89b6-55e335c09071  ethernet  --    
```

static-ip isminde bir profil oluştuğunu görmekteyiz. Bu profile DNS ayaralarını ekliyoruz.

```tpl
[root@localhost ~]#  nmcli con mod static-ip ipv4.dns "8.8.8.8 8.8.4.4"
```

oluşturdğumuz kartı aktif hale getiriyoruz.

```tpl
[root@localhost ~]# nmcli con up static-ip ifname enp1s0
Connection successfully activated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/6)
```

Enp1s0 ağ arayüzümüze başka bir IP adresi ekledik. IP adresinin başarıyla eklendiğini doğrulamak için ip komutunu çalıştıracağız:


```tpl
[root@localhost ~]# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 52:54:00:1e:33:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.150/24 brd 192.168.122.255 scope global noprefixroute enp1s0
       valid_lft forever preferred_lft forever
    inet 192.168.122.10/24 brd 192.168.122.255 scope global secondary dynamic noprefixroute enp1s0
       valid_lft 3512sec preferred_lft 3512sec
    inet6 fe80::2eb2:fd3c:7c3f:a8a3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
[root@localhost ~]# 
```

## Up & Down
Bağlantıyı etkinleştirerek veya devre dışı bırakarak nasıl yönetebileceğinizi keşfedeceğiz. Bir bağlantıyı devre dışı bırakmak veya devre dışı bırakmak için şu komutu çalıştırın:

```tpl
nmcli con down id "static-ip" ifname enp1s0

```

![](/images/down-nic.png)

```tpl
nmcli con up id "static-ip" ifname enp1s0
```

![](/images/nic-up.png)


## edit

Oluşturmuş olduğumuz profili editlemek için;


```tpl
[root@localhost network-scripts]# nmcli connection edit static-ip
nmcli> set ipv4.method manual
nmcli> set ipv4.address 192.168.122.151/24
nmcli> save
```


## Config File

Yapılan tüm değişiklikler  **/etc/NetworkManager/system-connections/** dizininde tutulmaktadır.

```tpl
[root@localhost network-scripts]# cat /etc/NetworkManager/system-connections/static-ip.nmconnection 
[connection]
id=static-ip
uuid=be6f4767-448e-4daa-89b6-55e335c09071
type=ethernet
interface-name=enp1s0
timestamp=1682674842

[ethernet]

[ipv4]
address1=192.168.122.150/24,192.168.122.1
address2=192.168.122.151/24
dns=8.8.8.8;8.8.4.4;
method=manual

[ipv6]
addr-gen-mode=default
method=auto

[proxy]
```


