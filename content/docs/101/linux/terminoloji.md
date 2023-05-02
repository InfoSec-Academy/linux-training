---
title: Terminoloji
weight: 10
---

## process
İşlem(process), o anda sistemde çalışan derlenmiş kaynak kodudur.

## PID
Tüm işlemlerin bir işlem kimliği veya PID'si vardır.

## PPID

PPID (Parent Process ID - Ebeveyn İşlem Kimliği), bir işlemin oluşturulduğu ana işlemi tanımlayan bir numaradır. Yani, herhangi bir işlem oluşturulduğunda, bu işlem bir ana işlem tarafından başlatılmışsa, bu işlemin PPID'si, ana işlemin kimliği olacaktır. PPID, işletim sistemi tarafından kullanılır ve işlemlerin yönetimi için önemlidir. Örneğin, bir işlem sona erdiğinde, işletim sistemi, bu işlemin PPID'sine sahip olan ana işlemi kontrol ederek, gerektiğinde onu sonlandırabilir. PPID, işlemler arasındaki hiyerarşik yapıyı tanımlamak için de kullanılır. Her işlem, bir ana işlemin altında veya birçok çocuk işlemi ile birlikte olabilir ve PPID, bu ilişkileri belirlemek için kullanılır.

## init

init, Unix benzeri işletim sistemlerinde sistem açılışının ve işlem yönetiminin başlangıcını yöneten ilk işlem (process) olarak adlandırılır. init, önyükleme (boot) sürecinde, işletim sistemi çekirdeği yüklendikten sonra çalıştırılır ve sistemin diğer işlemlerinin başlatılmasından sorumludur.

init, önceden belirlenmiş bir dizi işlemi (runlevel) belirli bir sırayla başlatır. Bu işlemler, sistem için gerekli olan servisleri, bağımlılıkları ve diğer ayarları yükler. Bu nedenle, init, sistemin stabil bir şekilde başlaması için önemli bir role sahiptir.

Geleneksel olarak, init'in kullanıldığı sistemlerde 0'dan 6'ya kadar altı farklı runlevel vardır. Bu runlevel'lar, sistemde çalışan servislerin durumunu ve hangi hizmetlerin çalıştırılacağını belirler. Örneğin, runlevel 1, sistemi bir kurtarma modunda başlatırken, runlevel 5, bir grafiksel kullanıcı arabirimini (GUI) başlatmak için kullanılabilir.

Modern Linux dağıtımlarında, systemd gibi yeni init sistemleri kullanılır. Bu sistemler, geleneksel init sistemlerine göre daha hızlı başlangıç süreleri ve daha iyi ölçeklenebilirlik özellikleri sunarlar.

## kill

Unix benzeri işletim sistemlerinde bir işlemi sonlandırmak veya durdurmak için kullanılan bir sistem çağrısıdır. Bu işlem, önceden belirlenmiş bir işlem kimliği (PID - Process ID) kullanılarak gerçekleştirilir.

kill komutu, genellikle bir işlemin normal şekilde durdurulamadığı veya donduğu durumlarda kullanılır. Bu durumlar, bir programın yanıt vermediği veya sistem kaynaklarına erişememesi nedeniyle kilitlendiği zamanlarda ortaya çıkabilir. 

## daemon

İşletim sistemlerinde arka planda sürekli olarak çalışan bir işlemdir. Bu işlemler, kullanıcının doğrudan etkileşimine ihtiyaç duymayan servisler, arka plan hizmetleri, görevler ve uygulamalar olabilir.

## zombie

Bir işlem, normal olarak sonlandırıldığında, işletim sistemi tarafından sonlandırıldığına dair bir sinyal alır. Ancak, işlem sonlandırma sinyali alınamadığında veya işlem sonlandırılamadığında, işlem "zombie" durumuna geçer.

