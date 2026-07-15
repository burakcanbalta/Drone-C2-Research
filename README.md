---
title: "Görünmeyen Bağlantılar: Bir Güvenlik Araştırmacısının Gözünden Drone Komuta-Kontrol (C2) Haberleşmesi ve Modern RF Güvenliği"
author: Burak Balta
description: Drone komuta-kontrol (C2) haberleşmesinin çalışma prensipleri, RF mimarisi, telemetri, modern güvenlik yaklaşımları ve kurumsal savunma perspektifine teknik bir bakış.
tags:
  - Drone
  - UAV
  - RF Security
  - C2
  - Cyber Security
  - SDR
  - Physical Security
readingTime: "25-30 min"
---

# Görünmeyen Bağlantılar

## Bir Güvenlik Araştırmacısının Gözünden Drone Komuta-Kontrol (C2) Haberleşmesi ve Modern RF Güvenliği

> **Not**
>
> Bu makale, insansız hava araçlarının komuta-kontrol (Command & Control - C2) altyapısını savunma perspektifinden ele almaktadır. Amaç; drone haberleşme mimarisini, kullanılan kablosuz teknolojileri, kurumsal güvenlik risklerini ve modern savunma yaklaşımlarını teknik temelleriyle açıklamaktır.
>
> Makalede yer verilen bilgiler yalnızca güvenlik araştırmaları, savunma çalışmaları, akademik incelemeler ve yetkili güvenlik değerlendirmeleri kapsamında değerlendirilmelidir.

---

## Kapak Görseli

**Şekil 1.** Modern bir insansız hava aracının yer kontrol istasyonu ile haberleşmesini gösteren konsept görsel. Arka planda RF spektrumu, telemetri verileri ve dijital ağ mimarisini temsil eden soyut görselleştirme kullanılabilir.

---

# Giriş

> *"Bir drone'u havada tutan yalnızca motorları ve pervaneleri değildir. Onu operatörüne bağlayan görünmez radyo frekansı bağlantısı, modern insansız hava aracı ekosisteminin en kritik bileşenidir."*

İnsansız hava araçları (İHA), son on yıl içerisinde yalnızca askeri operasyonların değil; sivil havacılık, endüstriyel denetim, enerji sektörü, lojistik, tarım, afet yönetimi ve kamu güvenliği gibi birçok alanın da vazgeçilmez teknolojileri arasında yerini aldı. Gelişen batarya teknolojileri, daha güçlü uçuş kontrol sistemleri ve düşük maliyetli elektronik bileşenler sayesinde bugün birkaç yüz gram ağırlığındaki ticari bir drone bile geçmişte yalnızca profesyonel platformlarda bulunan birçok yeteneğe sahip olabiliyor.

Bu dönüşüm, beraberinde yeni güvenlik gereksinimlerini de ortaya çıkardı. Günümüzde bir drone yalnızca havada uçan elektronik bir cihaz değildir; sensörlerden, gömülü sistemlerden, kablosuz haberleşme protokollerinden, uydu navigasyon altyapılarından ve bulut servislerinden oluşan dağıtık bir bilgi işlem platformudur. Dolayısıyla güvenlik değerlendirmesi yalnızca hava aracının fiziksel bütünlüğüyle sınırlı kalmaz. Haberleşme altyapısı, yazılım bileşenleri, yer kontrol istasyonu, mobil uygulamalar ve kimlik doğrulama mekanizmaları da bu ekosistemin ayrılmaz parçalarıdır.

Bir güvenlik araştırmacısı açısından değerlendirildiğinde ise asıl kritik unsur, drone ile operatörü arasında kesintisiz olarak sürdürülen komuta-kontrol (Command & Control – C2) haberleşmesidir. Uçuş komutları, telemetri bilgileri, kamera görüntüleri, sensör verileri ve görev parametreleri bu iletişim kanalı üzerinden aktarılır. C2 bağlantısının güvenilirliği, yalnızca operasyonun başarısını değil; platformun emniyetini, veri bütünlüğünü ve görev sürekliliğini de doğrudan etkiler.

Modern drone sistemleri farklı haberleşme teknolojilerini aynı anda kullanabilir. Uçuş kontrol komutları bir RF bağlantısı üzerinden iletilirken, yüksek çözünürlüklü video akışı farklı bir kanal üzerinden taşınabilir. Aynı anda GNSS uydularından konum bilgisi alınabilir, LTE veya 5G altyapısı üzerinden bulut servislerine veri aktarılabilir ve görev kayıtları uzaktaki yönetim sistemleriyle senkronize edilebilir. Bu çok katmanlı yapı, operasyonel kabiliyetleri artırırken aynı zamanda saldırı yüzeyini de genişletmektedir.

Bu nedenle günümüzde drone güvenliği yalnızca uçuş güvenliğiyle ilgili bir konu değildir. Kritik altyapıları koruyan kurumlar, güvenlik operasyon merkezleri (SOC), savunma sanayii kuruluşları ve kamu kurumları için drone haberleşmesinin güvenliği; fiziksel güvenlik, ağ güvenliği ve elektronik harp disiplinlerinin kesişim noktasında yer almaktadır.

---

# Neden Komuta-Kontrol (C2) Haberleşmesi Bu Kadar Kritik?

Bir drone'un uçabilmesi için motorlarının çalışması yeterli değildir. Operatörden gelen komutların doğru şekilde iletilmesi, sensörlerden elde edilen verilerin geri aktarılması ve uçuş kontrol bilgisayarının bu bilgileri gerçek zamanlı olarak işlemesi gerekir.

Komuta-kontrol bağlantısı kesildiğinde, platformun davranışı tamamen uçuş kontrol yazılımında tanımlanan güvenlik politikalarına bağlıdır. Bazı sistemler otomatik olarak kalkış noktasına geri dönerken (Return-to-Home), bazıları mevcut konumda beklemeyi tercih eder veya güvenli iniş prosedürünü başlatır. Bu karar mekanizmaları, yalnızca operasyonel gereksinimlere değil; güvenlik ve emniyet prensiplerine göre de tasarlanır.

C2 haberleşmesinin güvenilirliği özellikle aşağıdaki senaryolarda kritik öneme sahiptir:

- Kritik altyapıların havadan denetlenmesi
- Elektrik iletim hatlarının kontrolü
- Petrol ve doğal gaz tesislerinin incelenmesi
- Arama ve kurtarma operasyonları
- Afet yönetimi
- Yangın gözlem faaliyetleri
- Kamu güvenliği görevleri
- Endüstriyel haritalama ve ölçüm çalışmaları

Bu operasyonlarda haberleşme altyapısında meydana gelebilecek kesintiler yalnızca görev başarısını değil, çevresel güvenliği ve insan hayatını da etkileyebilir.

Drone haberleşmesi bu nedenle yalnızca bir kablosuz iletişim problemi değil; yüksek erişilebilirlik, veri bütünlüğü, kimlik doğrulama ve operasyonel süreklilik gerektiren bütünleşik bir güvenlik problemidir.

---

# Bu Makalede Neleri İnceleyeceğiz?

Bu yazıda drone güvenliğini yalnızca kablosuz haberleşme açısından değerlendirmeyeceğiz. Bunun yerine komuta-kontrol mimarisini uçtan uca ele alacağız.

Makale boyunca aşağıdaki başlıklara değineceğiz:

- Drone haberleşmesinin temel çalışma prensipleri
- Komuta-kontrol (C2) mimarisi
- RF haberleşmesinin fiziksel katmanı
- Telemetri ve video veri akışları
- Kullanılan frekans bantları ve standartlar
- MAVLink, PX4 ve ArduPilot ekosistemi
- Ticari drone haberleşme teknolojileri
- Kriptografi ve güvenli haberleşme yaklaşımları
- Tehdit modelleme ve kurumsal risk değerlendirmesi
- RF tabanlı drone tespit sistemleri
- Radar, akustik ve optik algılama yöntemleri
- Yapay zekâ destekli drone tespit çözümleri
- Counter-UAS ekosistemi
- Türkiye'deki yasal düzenlemeler
- Geleceğin drone haberleşme teknolojileri

Makalenin amacı herhangi bir sistemi hedef alan saldırı yöntemlerini öğretmek değildir. Bunun yerine modern drone haberleşme mimarisini teknik açıdan inceleyerek savunma odaklı güvenlik yaklaşımını ortaya koymak, güvenlik araştırmacıları ve siber güvenlik profesyonelleri için kapsamlı bir başvuru kaynağı oluşturmaktır.
