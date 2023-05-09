---
title: konteyner teknolojisi
weight: 1
---


Linux konteyner teknolojisi, uygulamaları birbirinden izole edilmiş ortamlarda çalıştırmaya olanak tanıyan bir sanallaştırma teknolojisidir. Konteyner teknolojisi, ana işletim sistemi çekirdeğini paylaşan birden fazla uygulama arasında kaynak kullanımını optimize eder ve uygulamaların hızlı bir şekilde başlatılmasına, dağıtılmasına ve ölçeklendirilmesine olanak tanır.

Konteyner teknolojisi, konteynerler adı verilen izole edilmiş uygulama ortamları oluşturur. Konteynerler, uygulamaların çalışması için gerekli olan tüm kütüphaneleri, dosyaları ve diğer bağımlılıkları içerir. Her konteyner, bir veya daha fazla işletim sistemi kaynağını kullanır, ancak her konteyner kendi dosya sistemi, ağ arabirimi, bellek ve CPU'ya sahiptir. Konteynerler, birbirinden tamamen izole edilmiştir ve bir konteynerin çökmesi, diğer konteynerleri etkilemez.

Konteyner teknolojisi, Docker ve Kubernetes gibi araçlarla yönetilir. Docker, uygulamaların konteynerlere paketlenmesini, dağıtılmasını ve çalıştırılmasını kolaylaştıran bir platformdur. Kubernetes ise, Docker konteynerlerinin yönetimini otomatikleştirerek, ölçeklendirme, yüksek erişilebilirlik ve yük dengeleme gibi özellikleri sağlar.

![](/linux-training/images/konteyner.png)

Bu diyagramda, tek bir fiziksel sunucuda birden fazla konteynerin nasıl çalıştığı gösterilir. Her konteyner, kendi işletim sistemi kaynağını kullanır ve birden fazla uygulama barındırabilir. Konteynerler, Docker aracılığıyla yönetilir ve Docker Hub gibi kaynaklardan hazır konteyner imajları indirilebilir. Kubernetes ise, birden fazla sunucuda çalışan konteynerlerin yönetimini sağlar.

Konteyner teknolojisi, uygulama geliştiricilerine, uygulamaları farklı ortamlarda test etme ve dağıtma imkanı sunar. Ayrıca, sistem yöneticileri, konteynerleri farklı sunucular arasında taşıyarak kaynak kullanımını optimize edebilir ve uygulamaların ölçeklendirilmesini kolaylaştırabilir.