---
title: top
weight: 1
---

## top

top bir Linux ve Unix tabanlı işletim sistemlerinde kullanılan bir sistem izleme aracıdır. 
Bu araç, sistemdeki işlemci, bellek, disk, ağ ve diğer sistem kaynaklarının kullanımını gerçek zamanlı olarak takip eder.

top komutu, sistemdeki işlemci kullanımını, CPU zaman dilimlerini, işlemci kullanımını sıralar ve sistemdeki en çok CPU kaynağına sahip işlemleri ve diğer kaynakları tespit eder. Ayrıca, bu araç, sistemdeki tüm işlemleri, PID numaralarını, kullanılan bellek miktarını ve diğer ayrıntıları da gösterir.

top komutu, arayüzünde sürekli olarak güncellenen bir liste sağlar. Kullanıcılar, bu listede görüntülenen işlemleri PID numarasına veya bellek kullanımına göre sıralayabilirler. Ayrıca, kullanıcılar, işlemleri durdurabilir veya sonlandırabilir, CPU önceliklerini değiştirebilir ve sistem kaynaklarının kullanımı hakkında ayrıntılı istatistikler alabilirler.

örnek bir **top** çıktısı;

```tlp
top - 12:32:46 up 17:52,  2 users,  load average: 0.00, 0.00, 0.00
Tasks: 143 total,   1 running, 141 sleeping,   1 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   1953.7 total,   1169.4 free,    237.9 used,    546.4 buff/cache
MiB Swap:   1953.0 total,   1953.0 free,      0.0 used.   1554.2 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                              
    578 systemd+  20   0   15176   7168   6400 S   0.3   0.4   0:36.27 systemd-oomd                                                                                         
      1 root      20   0  153104  26208  10300 S   0.0   1.3   0:02.20 systemd                                                                                              
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kthreadd                                                                                             
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                               
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                                           
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 slub_flushwq                                                                                         
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns                                                                                                
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                                                          
     10 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                                                                                         
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread                                                                                    
     13 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                                               
     14 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                                              
     15 root      20   0       0      0      0 S   0.0   0.0   0:00.03 ksoftirqd/0                                                                                          
     16 root      20   0       0      0      0 I   0.0   0.0   0:02.65 rcu_preempt                                                                                          
     17 root      rt   0       0      0      0 S   0.0   0.0   0:00.18 migration/0                                                                                          
     19 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                              
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                              
     21 root      rt   0       0      0      0 S   0.0   0.0   0:00.20 migration/1                                                                                          
     22 root      20   0       0      0      0 S   0.0   0.0   0:00.03 ksoftirqd/1                                                                                          
     24 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                                                                          
     25 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kdevtmpfs                                                                                            
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 inet_frag_wq                                                                                         
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd                                                                                              
     29 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper  
```

Şimdi bu çıktının üst bölümündeki alanı inceleyelim;

```tlp
top - 12:32:46 up 17:52,  2 users,  load average: 0.00, 0.00, 0.00
Tasks: 143 total,   1 running, 141 sleeping,   1 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   1953.7 total,   1169.4 free,    237.9 used,    546.4 buff/cache
MiB Swap:   1953.0 total,   1953.0 free,      0.0 used.   1554.2 avail Mem 
```

Yukarıdaki çıktıdaki alanlar ve anlamları;

- top: Komutun adı
- 12:32:46: Sistem saati
- up 17:52: Sistem çalışma süresi
- 2 users: Şu anda oturum açmış 2 kullanıcı var
- load average: 0.00, 0.00, 0.00: Son 1, 5 ve 15 dakikalık yük ortalaması
- Tasks: Toplam işlem sayısı
- 143 total: Toplam işlem sayısı
- 1 running: Şu anda çalışan işlem sayısı
- 141 sleeping: Uyuyan işlem sayısı
- 1 stopped: Durdurulmuş işlem sayısı
- 0 zombie: Zombie işlem sayısı
- %Cpu(s): CPU kullanım istatistikleri
- 0.2 us: Kullanıcı modunda kullanılan CPU yüzdesi
- 0.2 sy: Sistem modunda kullanılan CPU yüzdesi
- 0.0 ni: Öncelikli çalıştırılan işlemde kullanılan CPU yüzdesi
- 99.7 id: CPU'nun boşta kalma yüzdesi
- 0.0 wa: Bekleyen I/O işlemi yüzdesi
- 0.0 hi: Kesinti işlemi yüzdesi
- 0.0 si: Yazma işlemi yüzdesi
- 0.0 st: Sanal CPU yüzdesi
- MiB Mem: Bellek kullanım istatistikleri
- 1953.7 total: Toplam bellek miktarı
- 1169.4 free: Boş bellek miktarı
- 237.9 used: Kullanılan bellek miktarı
- 546.4 buff/cache: Tamponlanmış bellek miktarı
- MiB Swap: Takas kullanım istatistikleri
- 1953.0 total: Toplam takas miktarı
- 1953.0 free: Boş takas miktarı
- 0.0 used: Kullanılan takas miktarı
- 1554.2 avail Mem: Kullanılabilir bellek miktarı


```tlp
 PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND    
```

- PID: İşlem kimliği (Process ID)
- USER: İşlemi başlatan kullanıcı
- PR: İşlem önceliği (Priority)
- NI: İşlem öncelik seviyesi (Nice value)
- VIRT: Sanal bellek kullanımı (Virtual memory usage)
- RES: Gerçek bellek kullanımı (Resident set size)
- SHR: Paylaşılan bellek kullanımı (Shared memory usage)
- S: İşlem durumu (Process status)
- %CPU: CPU kullanım yüzdesi (CPU usage percentage)
- %MEM: Bellek kullanım yüzdesi (Memory usage percentage)
- TIME+: İşlem çalışma süresi (Process CPU time)
- COMMAND: İşlem adı (Command name)


{{< hint info >}}
İşlem önceliği, bir işlemin işletim sistemi tarafından ne kadar öncelikli olduğunu gösteren bir sayısal değerdir. 
Düşük bir işlem önceliği, yüksek bir öncelikli işlem tarafından kesilebilirken, yüksek bir önceliği olan bir işlem diğer düşük öncelikli işlemler tarafından kesilemez.
(-20 , 19)
{{< /hint >}}

## Kısa Yollar

- k: Belirli bir PID'ye sahip işlemi sonlandırmak için kullanılır.
- u: Belirli bir kullanıcının işlemlerini görmek için kullanılır.
- M: İşlem listesini bellek kullanımına göre sıralamak için kullanılır.
- P: İşlem listesini CPU kullanımına göre sıralamak için kullanılır.
- T: İşlem listesini çalışma süresine göre sıralamak için kullanılır.
- q: top komutunu sonlandırır.


