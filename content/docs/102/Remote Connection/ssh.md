---
title: ssh
weight: 1
---

SSH, Secure Shell'in kısaltmasıdır ve güvenli bir uzak erişim protokolüdür. SSH, şifreli bir bağlantı sağlayarak bilgisayarınıza uzaktan erişim sağlar ve verilerinizi şifreler. Ayrıca SSH, dosya transferleri, X11 bağlantıları ve TCP bağlantıları için de kullanılabilir.

SSH, Linux ve Unix işletim sistemlerinde bulunur ve aynı zamanda birçok Windows sistemlerinde de kullanılabilir. Ayrıca, birçok bulut sunucu sağlayıcısı da SSH erişimi sağlar.

Birçok Linux/Unix dağıtımında, SSH varsayılan olarak kurulu olarak gelir. Ancak, bir nedenle SSH kurulu değilse, şu adımları izleyerek kurabilirsiniz:

**SSH paketini yükleyin:**
- Debian/Ubuntu: sudo apt-get install openssh-server
- CentOS/Fedora: sudo yum install openssh-server


**SSH servisini başlatın:**
- Debian/Ubuntu: sudo service ssh start
- CentOS/Fedora: sudo systemctl start sshd.service


**SSH servisini otomatik olarak başlatmak için:**
- Debian/Ubuntu: sudo update-rc.d ssh defaults 
- CentOS/Fedora: sudo systemctl enable sshd.service


## SSH Port Değiştirme:

SSH bağlantısı için varsayılan olarak 22 numaralı port kullanılır. Ancak bu, güvenlik açısından risk teşkil edebilir çünkü kötü amaçlı kullanıcılar tarafından bilinen bir porttur. Bu nedenle, SSH bağlantı noktasını değiştirmek, bilgisayarınızın daha güvende olmasına yardımcı olabilir.

Öncelikle, herhangi bir metin düzenleyicisi (nano, vi, gibi) kullanarak /etc/ssh/sshd_config dosyasını açın:

```tpl
 nano /etc/ssh/sshd_config
```

Dosya açıldığında, "Port" satırını bulun ve 22 numarasını, güvendiğiniz bir başka port numarası ile değiştirin. Örneğin, 2222 olarak değiştirebilirsiniz.

```tpl
Port 2222
```

Değişikliği kaydedin ve dosyayı kapatın.

Son olarak, SSH servisini yeniden başlatın.

```tpl
systemctl restart sshd
```

## SSH Anahtar Eşleştirme:

SSH anahtar eşleştirme, kullanıcıların şifreleri yerine anahtarlarını kullanarak güvenli bir şekilde oturum açmasını sağlar. Bu, güvenliği arttırır ve oturum açma işlemini hızlandırır.

Öncelikle, anahtar çiftini oluşturmak için ssh-keygen komutunu kullanın.

```tpl
ssh-keygen
```

Karşınıza "Enter file in which to save the key" şeklinde bir soru çıkacaktır. Sadece "Enter" tuşuna basın.

Karşınıza "Enter file in which to save the key" şeklinde bir soru çıkacaktır. Sadece "Enter" tuşuna basın.

Şimdi, bir parola belirleyin (opsiyonel) ve iki kez onaylayın.

Anahtar çifti oluşturulduktan sonra, public key'i sunucuya göndermeniz gerekiyor. Bunun için ssh-copy-id komutunu kullanın.

```tpl
ssh-copy-id username@remote_host
```

Kullanıcı adını ve uzak sunucunun adresini belirtin ve parolayı girin.

Artık SSH anahtar eşleştirme kurulmuştur. SSH anahtar eşleştirme, şifreleri kullanmadan oturum açmanıza izin verecektir.

## SSH Güvenlik Ayarları:

SSH güvenliğini arttırmak için aşağıdaki adımları uygulayabilirsiniz.

Root kullanıcısının SSH erişimini engelleyin. Bu, bir saldırganın direkt olarak root hesabına saldırmasını önleyecektir.

```tpl
nano /etc/ssh/sshd_config
```
```tpl
PermitRootLogin no
```

**Şifre tabanlı kimlik doğrulamayı devre dışı bırakma:**

Şifre tabanlı kimlik doğrulama, kullanıcı adı ve şifre kullanarak kimlik doğrulamayı içerir. Ancak, bu yöntem güvenli değildir ve şifrelerin kolayca çalınabileceği riski vardır. Bunun yerine, anahtar tabanlı kimlik doğrulamayı kullanmak daha güvenlidir. Anahtar tabanlı kimlik doğrulama, bir kullanıcının bir anahtar çifti oluşturmasını ve anahtarın bir kopyasını sunucuya yüklemesini içerir. Kullanıcı daha sonra anahtarını kullanarak kimlik doğrulama yapabilir.

Şifre tabanlı kimlik doğrulamayı devre dışı bırakmak için ilgili satırları yorum satırına çevirin veya silebilirsiniz. Örneğin:

```tpl
#PasswordAuthentication yes
```

SSH sunucusunu yeniden başlatın:

```tpl
systemctl restart sshd
```

**IP tabanlı erişim kontrolü:**

SSH sunucusuna kimlerin erişebileceğini sınırlamak için IP tabanlı erişim kontrolü yapılabilir. Bu, belirli bir IP adresi aralığına veya tek bir IP adresine erişim sağlamak için kullanılabilir.


AllowUsers" veya "AllowGroups" ayarlarını kullanarak belirli IP adreslerine erişim izni verebilirsiniz. Örneğin, aşağıdaki satırı ekleyerek belirli bir IP adresine erişim izni verebilirsiniz:

```tpl
AllowUsers user1@192.168.0.100
```
Bu ayar, yalnızca "user1" kullanıcısının "192.168.0.100" IP adresinden SSH sunucusuna erişmesine izin verir.

Sadece  bir kullanıcıyı engellemek isterseniz;


```tpl
DenyUsers user1@192.168.0.100
```
