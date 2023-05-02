---
title: ethtool
weight: 9
---

ethtool bir Linux aracıdır ve Ethernet kartının ayarlarını değiştirmek için kullanılır. ethtool aracı, bir Ethernet kartının desteklediği özellikleri listelemek, NIC ayarlarını görüntülemek ve yapılandırmak için kullanılabilir.

Birkaç kullanışlı ethtool komutu şunlardır:

- ethtool enp1s0: enp1s0 arayüzündeki NIC ayarlarını gösterir.
- ethtool -i enp1s0: enp1s0 arayüzündeki sürücü bilgilerini gösterir.
- ethtool -S enp1s0: enp1s0 arayüzündeki NIC istatistiklerini gösterir.
- ethtool -A enp1s0 autoneg on: enp1s0 arayüzündeki otomatik anlaşma özelliğini açar.
- ethtool -s enp1s0 speed 1000 duplex full: enp1s0 arayüzündeki hızı 1000Mbps ve tam çift yönlü (full duplex) modunu ayarlar.

```tpl
[root@localhost network-scripts]# ethtool enp1s0
Settings for enp1s0:
	Supported ports: [  ]
	Supported link modes:   Not reported
	Supported pause frame use: No
	Supports auto-negotiation: No
	Supported FEC modes: Not reported
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Advertised FEC modes: Not reported
	Speed: Unknown!
	Duplex: Unknown! (255)
	Auto-negotiation: off
	Port: Other
	PHYAD: 0
	Transceiver: internal
	Link detected: yes
```

```tpl
[root@localhost network-scripts]# ethtool -i enp1s0
driver: virtio_net
version: 1.0.0
firmware-version: 
expansion-rom-version: 
bus-info: 0000:01:00.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: no
supports-priv-flags: no
```