---
title: modprobe
weight: 1
---

modprobe, Linux'ta bir kernel modülü yüklemek veya kaldırmak için kullanılan bir komuttur. 
Kernel modülleri, çekirdek içinde çalışan yazılım parçalarıdır ve donanımı yönetmek, sistem kaynaklarını kontrol etmek veya ek özellikler sağlamak gibi görevleri yerine getirirler. Modüller, Linux çekirdeği için dinamik olarak yüklenir ve kaldırılabilirler, bu da gerektiğinde kullanıcılara kernel işlevselliğini genişletme ve yönetme olanağı sağlar.

## lsmod

Mevcut yüklü kernel modüllerini görüntülemek için **lsmod** komutunu kullanabilirsiniz. 
Bu komut, yüklü modüllerin bir listesini ve her bir modül için kullanılan bellek miktarını gösterir. Ayrıca, her modülün kimliğini, adını, boyutunu, kullanılan sayıyı ve kullanıcıları da listeler.

```tlp
[root@localhost boot]# lsmod | more
Module                  Size  Used by
nft_fib_inet           16384  1
nft_fib_ipv4           16384  1 nft_fib_inet
nft_fib_ipv6           16384  1 nft_fib_inet
nft_fib                16384  3 nft_fib_ipv6,nft_fib_ipv4,nft_fib_inet
nft_reject_inet        16384  6
nf_reject_ipv4         16384  1 nft_reject_inet
nf_reject_ipv6         24576  1 nft_reject_inet
nft_reject             16384  1 nft_reject_inet
nft_ct                 20480  7
nft_chain_nat          16384  3
nf_nat                 65536  1 nft_chain_nat
nf_conntrack          192512  2 nf_nat,nft_ct
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
rfkill                 40960  1
ip_set                 65536  0
nf_tables             348160  189 nft_ct,nft_reject_inet,nft_fib_ipv6,nft_fib_ipv4,nft_chain_nat,nft_r
eject,nft_fib,nft_fib_inet
nfnetlink              20480  3 nf_tables,ip_set
snd_hda_codec_generic   114688  1
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_intel          65536  0
snd_intel_dspcfg       36864  1 snd_hda_intel
snd_intel_sdw_acpi     20480  1 snd_intel_dspcfg
snd_hda_codec         217088  2 snd_hda_codec_generic,snd_hda_intel
intel_rapl_msr         20480  0
intel_rapl_common      36864  1 intel_rapl_msr
--More--
```

## Modül Oluşturma

Modül eklemek ve çıkartmak için örnek bir modül oluşturacağız. Bu modül linux çekirdeğine eklendiği zaman "hello world",
çıkartıldığı zaman "by by world" yazacak. 

```tlp
#include <linux/module.h>
#include <linux/kernel.h>  
#include <linux/init.h>
MODULE_LICENSE("GPL");
MODULE_DESCRIPTION("Hello world!");

static int __init hello_init(void)
{
    printk(KERN_INFO "Hello world\n");
    return 0;
}

static void __exit hello_exit(void)
{
    printk(KERN_INFO "bye bye world\n");
}

module_init(hello_init);
module_exit(hello_exit);
```

Makefile;

```tlp
obj-m = hello-world.o
all:
    make -C /lib/modules/$(shell uname -r)/build/ M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

```tlp
[root@localhost opt]# ls
Makefile  sample-module.c
```


```tlp
[root@localhost opt]# make
make -C /lib/modules/6.2.14-300.fc38.x86_64/build M=/opt modules
make[1]: Entering directory '/usr/src/kernels/6.2.14-300.fc38.x86_64'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: gcc (GCC) 13.1.1 20230426 (Red Hat 13.1.1-1)
  You are using:           gcc (GCC) 13.0.1 20230401 (Red Hat 13.0.1-0)
  CC [M]  /opt/sample-module.o
  MODPOST /opt/Module.symvers
  CC [M]  /opt/sample-module.mod.o
  LD [M]  /opt/sample-module.ko
  BTF [M] /opt/sample-module.ko
Skipping BTF generation for /opt/sample-module.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/kernels/6.2.14-300.fc38.x86_64'
```

```tlp
[root@localhost opt]# ls
Makefile  modules.order  Module.symvers  sample-module.c  sample-module.ko  sample-module.mod  sample-module.mod.c  sample-module.mod.o  sample-module.o
```


## insmod

**insmod** Linux işletim sistemi için kullanılan bir komuttur ve "insert module" kelimelerinin kısaltmasıdır. Bu komut, çalışan bir Linux çekirdeğine yeni bir dinamik yüklenen modülü eklemek için kullanılır.

```tlp
[root@localhost opt]# insmod sample-module.ko 
[root@localhost opt]# dmesg | tail -1
[63572.021553] Hello world
```

{{< hint info >}}
dmesg komutu, sistem mesajlarını görüntülemek için "kernel ring buffer" denilen özel bir bellek bölgesini okur. Bu bellek bölgesi, sistemin başlatılması sırasında ve sonrasında meydana gelen olaylar hakkında ayrıntılı bilgi içerir.

dmesg komutu, bir terminal penceresine sistem mesajlarını yazdırır ve genellikle sorun giderme veya hata ayıklama işlemlerinde kullanılır. 
{{< /hint >}}


## rmmod

**rmmod** komutu, yüklenmiş bir modülü Linux çekirdeğinden kaldırır ve böylece sistem kaynaklarını serbest bırakır.

```tlp
[root@localhost opt]# rmmod sample_module
[root@localhost opt]# dmesg | tail -1
[63805.282855] bye bye world
```



