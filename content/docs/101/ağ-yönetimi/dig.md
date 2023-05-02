---
title: dig
weight: 6
---

dig, Domain Information Groper (Alan Bilgisi Kazıyıcısı) olarak adlandırılan, DNS (Domain Name System) sorguları yapmak için kullanılan bir komut satırı aracıdır. Unix ve Unix benzeri işletim sistemlerinde kullanılabilir.

dig, DNS sorguları yaparak belirtilen bir alan adının IP adresi veya tersi bir DNS sorgusu yaparak bir IP adresinin alan adı gibi bilgileri almanıza olanak tanır. Ayrıca, DNS sunucularını doğrulamak ve bağlantı sorunlarını gidermek için de kullanılabilir.

Örneğin, aşağıdaki komut bir alan adının IP adresini almak için kullanılabilir:

```tpl
[ergunbilsel@localhost linux-101]$ dig e-devlet.gov.tr

; <<>> DiG 9.18.13 <<>> e-devlet.gov.tr
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19898
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;e-devlet.gov.tr.		IN	A

;; ANSWER SECTION:
e-devlet.gov.tr.	5029	IN	A	94.55.118.20

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Fri Apr 28 09:24:23 +03 2023
;; MSG SIZE  rcvd: 60
```

veya aşağıdaki komut bir IP adresinin alan adını almak için kullanılabilir:

```tpl
[ergunbilsel@localhost linux-101]$ dig -x 94.55.118.20

; <<>> DiG 9.18.13 <<>> -x 94.55.118.20
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30753
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;20.118.55.94.in-addr.arpa.	IN	PTR

;; ANSWER SECTION:
20.118.55.94.in-addr.arpa. 7087	IN	PTR	ptr-20.turkiye.gov.tr.

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Fri Apr 28 09:25:41 +03 2023
;; MSG SIZE  rcvd: 89
```
