---
title: sudo
weight: 2
---


## sudo

**sudo** Linux sistemlerinde güvenli bir şekilde kullanıcıların kök veya başka bir kullanıcının yetkisine sahip olmalarına izin veren bir programdır. Genellikle sistem yöneticileri tarafından kullanılır.

sudo komutu, sistemde belirtilen kullanıcının yetkilerini geçici olarak yükseltmek için kullanılır. Bu sayede kullanıcı kök yetkilerine sahip olmadan belirli işlemleri yapabilir. Bu işlem, kök kullanıcısı olarak giriş yapmak yerine belirli bir kullanıcının belirli bir işlemi yapmasına izin verir ve güvenliği artırır.


## sudoers

**sudoers** dosyası, sudo komutunun hangi kullanıcıların hangi işlemleri yapabileceğini belirlemesine yardımcı olan yapılandırma dosyasıdır. sudoers dosyası, yalnızca sistem yöneticileri tarafından değiştirilebilir.

sudoers dosyasındaki ayarlamalar sayesinde, belirli bir kullanıcının yalnızca belirli bir komutu çalıştırmasına izin verilebilir. Böylece kullanıcıların yetkileri ihtiyaç duydukları kadarıyla yükseltilir ve gereksiz riskler azaltılmış olur.

```tpl
test  ALL=(ALL) NOPASSWD: ALL
```
Yukarıdaki örnekte, test adlı kullanıcıya, tüm komutları çalıştırabilmesi için sudo yetkisi veriyoruz. NOPASSWD seçeneği ise, kullanıcının sudo için herhangi bir şifre girmesine gerek olmadığını belirtir.

{{< hint info >}}
sudoers dosyasında değişiklik yapmak için **visudo** komutundan yararlanabilirsiniz. Sudoers lokasyonu **/etc/sudoers**
{{< /hint >}}

## !visiblepw

***Defaults !visiblepw** satırı sudoers dosyasındaki bir parametredir ve sudo programının belirli bir davranışını değiştirir. Bu parametre etkinleştirildiğinde, kullanıcılara yönetici şifresi veya parolası sırasında geri bildirim verilmez. Yani, şifre veya parola girildiğinde ekranda karakterlerin görünür olması engellenir. Bu, güvenlik nedenleriyle kullanışlı bir özelliktir çünkü parolaların başkaları tarafından görüntülenmesini engeller.




