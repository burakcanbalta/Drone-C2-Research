<img width="637" height="421" alt="image" src="https://github.com/user-attachments/assets/12d7ef4f-05d5-43e5-a62e-80145bba83d7" />


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

# Drone Haberleşmesinin Temelleri

Bir insansız hava aracının güvenli şekilde görev yapabilmesi, yalnızca uçuş kontrol yazılımının başarısına değil; yer kontrol istasyonu ile kurduğu haberleşmenin güvenilirliğine de bağlıdır. Bir drone'un havada kalmasını sağlayan motorlar ve sensörler ne kadar önemliyse, bu bileşenleri yöneten komuta-kontrol (Command & Control – C2) bağlantısı da en az onlar kadar kritik bir rol üstlenir.

Modern drone sistemleri incelendiğinde, tek bir haberleşme kanalının kullanılmadığı görülür. Aksine, farklı amaçlara hizmet eden birçok iletişim akışı eş zamanlı olarak çalışır. Operatör tarafından gönderilen uçuş komutları, drone tarafından iletilen telemetri bilgileri, kamera görüntüleri, GNSS verileri ve görev parametreleri farklı veri akışları üzerinden taşınabilir. Bu mimari hem operasyonel esneklik sağlar hem de sistemin farklı bileşenlerini birbirinden bağımsız hâle getirir.

Temel olarak bir drone haberleşme mimarisi aşağıdaki bileşenlerden oluşur.

```text
               Ground Control Station
                        │
             Command & Control (C2)
                        │
         ───────── RF Communication ─────────
                        │
                        ▼
                  Flight Controller
            ┌──────────┼──────────┐
            │          │          │
          GNSS       IMU       ESC/Motor
            │
            ▼
      Telemetry Module
            │
            ▼
      Camera / Payload
            │
            ▼
        Video Downlink
```

Bu mimaride her bileşen farklı görevler üstlenir ve farklı güvenlik gereksinimlerine sahiptir. Uçuş kontrol bilgisayarı, sensörlerden aldığı verileri işleyerek drone'un dengesini korurken; haberleşme modülü operatör ile hava aracı arasındaki veri alışverişini sağlar. Kamera sistemleri ise görüntü verisini ayrı bir iletişim kanalı üzerinden yer kontrol istasyonuna aktarabilir.

Dolayısıyla drone güvenliği değerlendirilirken yalnızca uçuş kontrol yazılımı değil, haberleşme altyapısının tamamı birlikte ele alınmalıdır.

---

# Komuta-Kontrol (Command & Control – C2) Nedir?

Komuta-kontrol bağlantısı, insansız hava aracı ile yer kontrol istasyonu arasında çift yönlü veri alışverişi sağlayan temel iletişim katmanıdır. Bu bağlantı sayesinde operatör drone'u yönlendirebilir, görev parametrelerini değiştirebilir ve aracın durumunu gerçek zamanlı olarak takip edebilir.

C2 bağlantısı üzerinden taşınan veriler yalnızca uçuş komutlarından ibaret değildir. Tipik bir görev sırasında aşağıdaki bilgiler sürekli olarak iletilir.

- Uçuş komutları
- Telemetri verileri
- Batarya durumu
- Motor bilgileri
- GPS koordinatları
- İrtifa
- Hız
- Uçuş modu
- Sensör sağlık bilgileri
- Görev durumu
- Kamera kontrol komutları
- Faydalı yük (payload) yönetimi

Bu iletişim sayesinde operatör yalnızca drone'u yönlendirmez; aynı zamanda platformun sağlık durumunu da sürekli olarak izleyebilir.

Bazı görevlerde C2 bağlantısının gecikme süresi (latency), görev başarısını doğrudan etkileyebilir. Özellikle hassas manevralar gerektiren operasyonlarda milisaniyeler seviyesindeki gecikmeler dahi kontrol performansını değiştirebilir. Bu nedenle profesyonel platformlarda haberleşme altyapısı düşük gecikme, yüksek güvenilirlik ve hata toleransı sağlayacak şekilde tasarlanır.

---

# Drone Haberleşmesinde Veri Akışları

Bir drone ile yer kontrol istasyonu arasında gerçekleşen iletişim tek tip değildir. Farklı veri türleri, farklı bant genişliği ve gecikme gereksinimlerine sahiptir. Bu nedenle modern sistemlerde veri akışları mantıksal olarak birbirinden ayrılır.

## Uplink

Uplink, yer kontrol istasyonundan drone'a doğru gerçekleştirilen veri iletimidir.

Bu kanal üzerinden genellikle aşağıdaki bilgiler gönderilir.

- Uçuş komutları
- Görev planları
- Rota güncellemeleri
- Kamera kontrol komutları
- Faydalı yük yönetimi
- Acil durum talimatları

Uplink bağlantısında güvenilirlik kritik öneme sahiptir. Kaybolan veya bozulmuş komut paketleri, platformun beklenmeyen davranışlar sergilemesine neden olabileceğinden iletim protokolleri hata kontrol mekanizmalarıyla desteklenir.

## Downlink

Downlink ise drone'dan operatöre doğru gerçekleştirilen veri iletimidir.

Bu kanal üzerinden iletilen başlıca bilgiler şunlardır.

- Telemetri verileri
- GPS konumu
- İrtifa
- Hız
- IMU verileri
- Batarya durumu
- Motor sıcaklıkları
- Kamera görüntüleri
- Sensör çıktıları

Video aktarımı genellikle telemetri verilerine kıyasla çok daha yüksek bant genişliği gerektirir. Bu nedenle birçok ticari platform, video ile telemetriyi aynı fiziksel bağlantı üzerinden taşısa bile mantıksal olarak farklı veri akışları kullanır.

---

# Telemetri Nedir?

Telemetri, bir hava aracının çalışma durumunu uzaktaki operatöre ileten ölçüm verilerinin tamamını ifade eder. Modern drone sistemlerinde telemetri yalnızca konum bilgisinden ibaret değildir; platformun neredeyse tüm çalışma parametreleri gerçek zamanlı olarak izlenebilir.

Tipik bir telemetri paketi aşağıdaki bilgileri içerebilir.

- Enlem ve boylam
- İrtifa
- Yer hızı
- Hava hızı
- Yönelim (Yaw)
- Yatış açısı (Roll)
- Yunuslama açısı (Pitch)
- Batarya gerilimi
- Batarya akımı
- Kalan uçuş süresi
- GPS uydu sayısı
- GNSS doğruluk değeri
- Uçuş modu
- IMU sağlık bilgileri
- Manyetometre durumu
- Barometre verileri

Bu bilgiler yalnızca operatörün durumsal farkındalığını artırmakla kalmaz; aynı zamanda uçuş kontrol yazılımının karar mekanizmalarının izlenebilmesini de sağlar.

Kurumsal platformlarda telemetri kayıtları çoğu zaman görev sonunda merkezi sistemlerde saklanır. Böylece uçuş sonrası analizler yapılabilir, bakım süreçleri planlanabilir ve gerektiğinde olay incelemelerinde geçmiş görev kayıtları incelenebilir.
# Elektromanyetik Dalgalar ve RF Haberleşmesi

Bir drone ile yer kontrol istasyonu arasındaki iletişim, görünmeyen ancak son derece karmaşık bir elektromanyetik haberleşme altyapısı üzerinden gerçekleştirilir. Operatörün kumandadaki küçük bir joystick hareketi, birkaç milisaniye içerisinde radyo dalgalarına dönüştürülerek hava aracına ulaştırılır. Aynı anda drone tarafından üretilen telemetri verileri ve kamera görüntüleri de farklı veri akışları hâlinde operatöre geri gönderilir.

Bu iletişim süreci, elektromanyetik dalgaların temel fizik prensiplerine dayanır. Haberleşmenin güvenilirliği yalnızca yazılım veya kullanılan protokollerle değil; frekans seçimi, anten tasarımı, çevresel koşullar, sinyal-gürültü oranı (Signal-to-Noise Ratio – SNR) ve elektromanyetik girişim (Electromagnetic Interference – EMI) gibi fiziksel faktörlerle de doğrudan ilişkilidir.

Dolayısıyla drone haberleşmesi değerlendirilirken yalnızca ağ protokollerini incelemek yeterli değildir. Haberleşmenin gerçekleştiği fiziksel ortamın özellikleri de güvenlik analizinin önemli bir parçasını oluşturur.

---

# Elektromanyetik Haberleşme Nasıl Gerçekleşir?

Bir yer kontrol istasyonundan gönderilen dijital komutlar doğrudan havada iletilmez. Öncelikle bu veriler, haberleşme modülü tarafından belirli bir taşıyıcı frekans üzerine modüle edilir. Daha sonra anten aracılığıyla elektromanyetik dalga olarak ortama yayılır.

Drone üzerinde bulunan alıcı anten, bu elektromanyetik enerjiyi algılar ve haberleşme modülü sinyali tekrar sayısal verilere dönüştürür. Aynı süreç, drone tarafından operatöre gönderilen telemetri ve görüntü verileri için ters yönde de gerçekleşir.

Basitleştirilmiş haberleşme süreci aşağıdaki gibi özetlenebilir.

```text
Operatör Komutu
        │
        ▼
RF Vericisi
        │
        ▼
Anten
        │
        ▼
Elektromanyetik Dalga
        │
        ▼
Drone Anteni
        │
        ▼
RF Alıcısı
        │
        ▼
Flight Controller
```

Bu süreç, saniyede yüzlerce hatta binlerce veri paketinin karşılıklı olarak iletilmesini sağlayabilir. Kullanılan haberleşme teknolojisine bağlı olarak gecikme süreleri birkaç milisaniye seviyesine kadar düşebilir.

---

# RF Spektrumu ve Drone Haberleşmesi

Radyo frekansı spektrumu, farklı haberleşme teknolojilerinin kullandığı frekans bantlarının tamamını ifade eder. Drone sistemleri de görev gereksinimlerine bağlı olarak farklı frekans aralıklarından yararlanabilir.

Her frekans bandının kendine özgü avantajları ve sınırlamaları bulunur. Düşük frekanslar daha uzun menzil sağlayabilirken, yüksek frekanslar daha fazla bant genişliği sunar. Buna karşılık yüksek frekanslı sinyaller çevresel engellerden daha fazla etkilenebilir.

Bu nedenle profesyonel platformlarda kullanılacak haberleşme teknolojisi; görev profili, çevresel koşullar, veri miktarı ve gecikme gereksinimleri dikkate alınarak belirlenir.

---

# Drone Sistemlerinde Yaygın Frekans Bantları

## 433 MHz

433 MHz bandı, özellikle açık kaynaklı uçuş kontrol sistemlerinde telemetri haberleşmesi amacıyla uzun yıllardır kullanılan frekanslardan biridir.

Bu bant;

- düşük veri hızları,
- görece uzun menzil,
- düşük güç tüketimi

gibi avantajlar sunabilir.

Telemetri verilerinin iletilmesi için yeterli olsa da yüksek çözünürlüklü görüntü aktarımı gibi yüksek bant genişliği gerektiren uygulamalar için uygun değildir.

---

## 868 MHz ve 915 MHz

868 MHz (Avrupa) ve 915 MHz (Amerika Birleşik Devletleri ile bazı diğer bölgeler), günümüzde özellikle LoRa tabanlı uzun menzil haberleşme sistemlerinde yaygın olarak kullanılmaktadır.

Bu bantların temel avantajları şunlardır.

- Uzun iletişim mesafesi
- Düşük enerji tüketimi
- Kararlı sinyal yayılımı
- Telemetri uygulamalarına uygun yapı

Buna karşılık veri aktarım hızları sınırlıdır. Bu nedenle yüksek çözünürlüklü video iletiminden ziyade sensör verileri ve görev bilgileri için tercih edilir.

---

## 2.4 GHz

2.4 GHz ISM bandı, günümüzde ticari drone platformlarının büyük bölümünde kullanılan en yaygın haberleşme frekansıdır.

Bu bant yalnızca drone sistemlerinde değil;

- Wi-Fi
- Bluetooth
- ZigBee
- Kablosuz çevre birimleri

gibi birçok farklı teknolojide de kullanılmaktadır.

Geniş donanım desteği ve yeterli bant genişliği sağlaması önemli avantajlar sunsa da aynı frekans bandını kullanan çok sayıda cihaz bulunması nedeniyle elektromanyetik yoğunluk oldukça yüksektir.

Özellikle şehir merkezlerinde çok sayıda kablosuz ağın bulunduğu ortamlarda haberleşme kalitesi çevresel koşullardan etkilenebilir.

---

## 5.8 GHz

5.8 GHz bandı daha yüksek bant genişliği sağlayabildiği için özellikle yüksek çözünürlüklü video aktarımında tercih edilmektedir.

Bu bant sayesinde;

- daha yüksek veri hızları,
- daha düşük gecikme,
- daha kaliteli görüntü aktarımı

mümkün olabilir.

Bununla birlikte yüksek frekanslı elektromanyetik dalgalar engellerden daha fazla etkilendiğinden kapsama alanı çoğu zaman 2.4 GHz bandına göre daha sınırlıdır.

---

# Aynı Frekans Aynı Güvenlik Anlamına Gelmez

Drone haberleşmesi değerlendirilirken yapılan en yaygın hatalardan biri, kullanılan frekans bandını doğrudan güvenlik seviyesiyle ilişkilendirmektir.

Örneğin iki farklı üretici aynı 2.4 GHz bandını kullanıyor olabilir. Ancak bu durum iki sistemin aynı güvenlik seviyesine sahip olduğu anlamına gelmez.

Gerçek güvenlik;

- haberleşme protokolü,
- kimlik doğrulama mekanizması,
- oturum yönetimi,
- paket bütünlüğü,
- anahtar yönetimi,
- hata kontrol algoritmaları,
- kullanılan kriptografi

gibi çok daha geniş bir mimarinin sonucudur.

Dolayısıyla güvenlik değerlendirmelerinde yalnızca frekans bilgisi yeterli değildir. Haberleşmenin nasıl gerçekleştirildiği, hangi protokollerin kullanıldığı ve iletişim zincirinin nasıl korunduğu birlikte analiz edilmelidir.

---

# Anten Tasarımının Önemi

Kablosuz haberleşme performansını belirleyen en kritik bileşenlerden biri de antendir.

Anten;

- kapsama alanını,
- sinyal kalitesini,
- yönlülüğü,
- bağlantı kararlılığını

doğrudan etkiler.

Profesyonel drone platformlarında çoğu zaman MIMO (Multiple Input Multiple Output), diversity anten yapıları ve akıllı anten teknolojileri kullanılarak haberleşmenin sürekliliği artırılır.

Bu sayede farklı çevresel koşullarda dahi bağlantının mümkün olduğunca kararlı kalması hedeflenir.

## Drone C2 Mimarisi Nasıl Çalışır?

Bir insansız hava aracının güvenliği yalnızca havada uçabilmesine bağlı değildir. Asıl kritik unsur, operatör ile platform arasında **kesintisiz, güvenilir ve doğrulanabilir bir komuta-kontrol (Command and Control - C2) kanalının** kurulabilmesidir. Bu kanal; uçuş komutlarının iletilmesini, telemetri bilgilerinin operatöre geri gönderilmesini ve görev boyunca oluşan operasyonel verilerin paylaşılmasını sağlar.

Basit bir kullanıcı açısından bakıldığında süreç oldukça görünmezdir. Kumandadaki joystick hareket ettirilir, drone yön değiştirir veya irtifa kazanır. Ancak arka planda bunun çok ötesinde çalışan katmanlı bir haberleşme mimarisi bulunmaktadır.

Tipik bir C2 altyapısı aşağıdaki bileşenlerden oluşur.

```text
              Operator
                  │
                  ▼
     Ground Control Station (GCS)
                  │
                  ▼
      RF Communication Link
         (2.4 GHz / 5.8 GHz)
                  │
                  ▼
        Flight Controller (FC)
                  │
          ┌───────┴────────┐
          ▼                ▼
   Navigation          Sensors
  (GPS / IMU)     Camera / LiDAR
          │                │
          └───────┬────────┘
                  ▼
             Telemetry Data
                  │
                  ▼
     Ground Control Station
```

Bu mimaride yer alan her bileşen farklı güvenlik sorumluluklarına sahiptir.

**Ground Control Station (GCS)**, operatörün uçuş görevini yönettiği merkezdir. Uçuş planları hazırlanır, rota güncellenir ve gerçek zamanlı telemetri verileri izlenir.

**RF haberleşme bağlantısı**, komutların hava aracına iletilmesini ve sensör verilerinin operatöre ulaştırılmasını sağlar. Haberleşmenin sürekliliği doğrudan uçuş güvenliğini etkiler.

**Flight Controller (FC)**, drone'un karar mekanizmasıdır. Gelen komutları yorumlar ve motor kontrol algoritmalarını çalıştırarak platformun dengede kalmasını sağlar.

**GPS, IMU, barometre ve pusula** gibi sensörler; konum, hız, yönelim ve çevresel bilgileri sürekli olarak üretir.

**Telemetri kanalı** ise uçuş sırasında oluşan operasyonel verileri yer kontrol istasyonuna geri iletir.

Bu zincirin herhangi bir noktasında meydana gelebilecek hata yalnızca haberleşmeyi değil, görevin tamamını etkileyebilir. Bu nedenle modern C2 sistemleri yalnızca veri iletimine değil; **Gizlilik (Confidentiality), Bütünlük (Integrity), Kimlik Doğrulama (Authentication)** ve **Erişilebilirlik (Availability)** prensiplerine de odaklanmaktadır.

---

## Uplink ve Downlink Kavramları

Drone haberleşmesi incelenirken en sık karşılaşılan kavramlardan ikisi **uplink** ve **downlink** iletişimidir.

Her iki kanal farklı amaçlarla kullanılır ve farklı güvenlik gereksinimlerine sahiptir.

### Uplink

**Uplink**, yer kontrol istasyonundan hava aracına gönderilen komutları ifade eder.

Bu kanal üzerinden;

- Uçuş komutları
- Görev planları
- Rota güncellemeleri
- Hız değişiklikleri
- Kamera kontrolü
- Kalkış ve iniş talimatları
- Acil durum komutları

iletilir.

### Downlink

**Downlink**, hava aracından operatöre geri gönderilen tüm bilgileri ifade eder.

Bu bilgiler arasında;

- GPS koordinatları
- İrtifa
- Hız
- Batarya seviyesi
- Uçuş modu
- Motor durumu
- IMU çıktıları
- Kamera görüntüsü
- Sensör verileri

bulunur.

Profesyonel platformlarda video akışı ile telemetri verileri çoğu zaman farklı mantıksal kanallar üzerinden taşınır. Böylece yüksek bant genişliği gerektiren görüntü aktarımı, kritik uçuş komutlarının iletimini etkilemez.

Bu ayrım, görev güvenilirliği ve haberleşme sürekliliği açısından önemli bir mimari tercih olarak kabul edilir.

---

## C2 Haberleşmesinde Gecikme (Latency) Neden Kritiktir?

Komuta-kontrol sistemlerinde yalnızca bağlantının kurulmuş olması yeterli değildir. Haberleşmenin **ne kadar düşük gecikmeyle** gerçekleştiği de uçuş güvenliğini doğrudan etkiler.

Örneğin operatör kumandayı sağa çevirdiğinde bu komutun birkaç yüz milisaniye gecikmeyle hava aracına ulaşması bile, özellikle yüksek hızda hareket eden platformlarda ciddi kontrol problemlerine yol açabilir.

Bu nedenle profesyonel C2 sistemlerinde gecikme süreleri sürekli olarak ölçülür ve analiz edilir.

En yaygın kullanılan performans metrikleri şunlardır:

- **Round Trip Time (RTT):** Bir komutun gönderilmesi ve yanıtının geri alınması için geçen toplam süre.
- **Packet Loss:** Haberleşme sırasında kaybolan veri paketlerinin oranı.
- **Jitter:** Paketlerin sabit aralıklarla değil, değişken gecikmelerle ulaşmasını ifade eden ölçüt.

Özellikle gerçek zamanlı video aktarımı yapan sistemlerde yüksek jitter değerleri görüntü kalitesini düşürebilir, operatörün durumsal farkındalığını azaltabilir ve kontrol gecikmelerine neden olabilir.

Bu nedenle modern profesyonel drone platformları;

- Adaptive Bitrate (ABR)
- Forward Error Correction (FEC)
- Dinamik kanal seçimi (Dynamic Channel Selection)
- Otomatik frekans atlama (Frequency Hopping)
- Link Quality Monitoring

gibi teknolojileri kullanarak haberleşmenin sürekliliğini ve güvenilirliğini artırmayı hedefler.

# Drone Haberleşmesinde Kullanılan RF Frekansları ve Protokoller

Bir drone'un güvenliği yalnızca kullandığı uçuş kontrol yazılımına bağlı değildir. Komuta-kontrol (Command and Control - C2) kanalının hangi frekans bandında çalıştığı, hangi haberleşme protokolünü kullandığı ve bu protokolün hangi güvenlik mekanizmalarını desteklediği de en az uçuş kontrol algoritmaları kadar önemlidir.

Günümüzde ticari, endüstriyel ve askeri insansız hava araçlarında farklı haberleşme teknolojileri kullanılmaktadır. Seçilecek teknoloji; görev menzili, veri miktarı, gecikme toleransı, enerji tüketimi ve elektromanyetik ortam koşullarına göre değişiklik gösterir.

Her frekans bandı farklı avantajlar ve farklı mühendislik kısıtlamaları sunmaktadır.

---

## 2.4 GHz ISM Bandı

2.4 GHz, dünya genelinde lisans gerektirmeden kullanılabilen **Industrial, Scientific and Medical (ISM)** bandıdır.

Tüketici sınıfı drone'ların önemli bir bölümü bu frekansta çalışmaktadır.

Başlıca avantajları şunlardır:

- Küresel ölçekte yaygın kullanım
- Düşük donanım maliyeti
- Yeterli veri aktarım kapasitesi
- Geniş cihaz desteği

Bununla birlikte aynı frekans bandı;

- Wi-Fi
- Bluetooth
- ZigBee
- Kablosuz klavyeler
- IoT cihazları

tarafından da yoğun şekilde kullanılmaktadır.

Bu durum özellikle şehir merkezlerinde elektromanyetik yoğunluğun artmasına ve haberleşme kalitesinin düşmesine neden olabilir.

Modern sistemler bu sorunu azaltmak amacıyla otomatik kanal seçimi ve adaptif güç yönetimi gibi mekanizmalar kullanmaktadır.

---

## 5.8 GHz Bandı

5.8 GHz bandı da ISM frekans aralığında yer alır.

Özellikle yüksek çözünürlüklü görüntü aktarımı yapan platformlarda tercih edilmektedir.

Bu frekansın en önemli avantajı daha geniş bant genişliği sunmasıdır.

Bu sayede;

- 1080p görüntü aktarımı
- düşük gecikmeli FPV sistemleri
- yüksek veri oranı gerektiren görevler

daha verimli gerçekleştirilebilir.

Bununla birlikte yüksek frekansın doğal sonucu olarak sinyalin yayılım mesafesi azalır.

Ayrıca;

- duvarlar,
- ağaçlar,
- beton yapılar,
- metal yüzeyler

gibi fiziksel engeller sinyal kalitesini daha fazla etkileyebilir.

Bu nedenle birçok profesyonel platform görev sırasında 2.4 GHz ve 5.8 GHz bantları arasında dinamik geçiş yapabilmektedir.

---

## 433 MHz ve 915 MHz Telemetri Sistemleri

Uzun menzilli telemetri uygulamalarında daha düşük frekans bantları tercih edilmektedir.

433 MHz ve 915 MHz bantları özellikle açık kaynak uçuş kontrol sistemlerinde yaygın olarak kullanılmaktadır.

Bu frekansların tercih edilmesinin temel nedenleri şunlardır:

- daha uzun haberleşme mesafesi,
- düşük güç tüketimi,
- engellerden daha az etkilenme,
- düşük veri hızına rağmen yüksek bağlantı kararlılığı.

Bu bantlar çoğunlukla;

- telemetri,
- görev güncellemesi,
- durum bilgisi,
- sensör verileri

için kullanılmaktadır.

Video aktarımı ise çoğu zaman farklı haberleşme kanallarından gerçekleştirilmektedir.

---

## LoRa Tabanlı Haberleşme

Son yıllarda özellikle araştırma projelerinde ve uzun menzilli İHA çalışmalarında LoRa tabanlı çözümler kullanılmaya başlanmıştır.

LoRa (Long Range), düşük veri hızına karşılık oldukça uzun haberleşme mesafeleri sağlayabilen bir haberleşme teknolojisidir.

Temel avantajları şunlardır:

- kilometrelerce menzil,
- düşük enerji tüketimi,
- yüksek bağlantı kararlılığı,
- düşük maliyet.

Ancak LoRa'nın bant genişliği oldukça sınırlıdır.

Bu nedenle;

- video aktarımı,
- yüksek çözünürlüklü görüntüler,
- büyük veri paketleri

için uygun değildir.

LoRa daha çok telemetri, sensör verileri ve düşük bant genişliği gerektiren görevlerde kullanılmaktadır.

---

# Drone Haberleşme Protokolleri

Fiziksel katmanda kullanılan frekans kadar önemli olan diğer konu ise veri paketlerinin nasıl oluşturulduğunu belirleyen haberleşme protokolleridir.

Bu protokoller;

- veri paketlerinin yapısını,
- kimlik doğrulama mekanizmalarını,
- hata kontrolünü,
- paket bütünlüğünü,
- görev yönetimini

tanımlar.

Günümüzde en yaygın kullanılan protokoller MAVLink, DJI OcuSync ve PX4 ekosistemidir.

---

## MAVLink

Micro Air Vehicle Link (MAVLink), açık kaynak insansız hava araçlarında en yaygın kullanılan haberleşme protokolüdür.

ArduPilot ve PX4 ekosistemlerinin temel haberleşme altyapısını oluşturur.

MAVLink;

- telemetri,
- uçuş komutları,
- sensör verileri,
- görev planları,
- durum bilgileri

için standartlaştırılmış mesaj yapıları sunar.

Oldukça hafif olması nedeniyle gömülü sistemlerde düşük işlemci yükü oluşturur.

Bugün binlerce akademik proje ve ticari platform MAVLink kullanmaktadır.

---

## MAVLink 1 ve MAVLink 2 Arasındaki Farklar

İlk sürüm olan MAVLink 1 performans odaklı geliştirilmiştir.

Ancak güvenlik açısından bazı önemli sınırlamaları bulunmaktadır.

Bunlardan en önemlisi mesajların varsayılan olarak kriptografik bütünlük doğrulaması içermemesidir.

Bu nedenle zaman içerisinde MAVLink 2 geliştirilmiştir.

MAVLink 2 ile birlikte;

- Packet Signing
- Mesaj doğrulama
- Genişletilmiş mesaj formatı
- Yeni mesaj tipleri
- Daha güvenli oturum yönetimi

gibi özellikler eklenmiştir.

Modern sistemlerde mümkün olduğunca MAVLink 2 tercih edilmesi önerilmektedir.

---

## PX4 ve ArduPilot Ekosistemi

PX4 ve ArduPilot doğrudan haberleşme protokolü değildir.

Bunlar açık kaynak uçuş kontrol platformlarıdır.

Her iki proje de MAVLink haberleşme standardını kullanmaktadır.

PX4;

- akademik çalışmalar,
- araştırma laboratuvarları,
- endüstriyel geliştirme

alanlarında oldukça yaygındır.

ArduPilot ise;

- sabit kanat,
- multikopter,
- VTOL,
- kara araçları,
- deniz araçları

gibi birçok farklı platformu destekleyen geniş bir ekosisteme sahiptir.

Her iki proje de açık kaynak olmaları nedeniyle dünya genelindeki araştırmacılar tarafından yoğun olarak incelenmektedir.

---

## DJI OcuSync

DJI tarafından geliştirilen OcuSync, ticari drone ekosistemlerinde kullanılan özel (proprietary) bir haberleşme teknolojisidir.

OcuSync yalnızca bir RF protokolü değildir.

Aynı zamanda;

- video aktarımı,
- telemetri,
- komuta-kontrol,
- frekans yönetimi

işlevlerini tek bir mimari altında birleştirir.

OcuSync sistemleri;

- otomatik kanal seçimi,
- adaptif veri oranı,
- düşük gecikmeli video aktarımı,
- gelişmiş bağlantı yönetimi

gibi özellikler sunmaktadır.

Protokolün ayrıntıları üretici tarafından kamuya tamamen açıklanmadığından akademik çalışmalar büyük ölçüde tersine mühendislik analizlerine dayanmaktadır.

---

## Açık ve Kapalı Protokollerin Karşılaştırılması

| Özellik | Açık Protokoller | Kapalı Protokoller |
|----------|-----------------|--------------------|
| İncelenebilirlik | Yüksek | Sınırlı |
| Akademik araştırma | Kolay | Daha zor |
| Topluluk desteği | Çok yüksek | Üreticiye bağlı |
| Özelleştirilebilirlik | Yüksek | Düşük |
| Güvenlik denetimi | Bağımsız yapılabilir | Üreticiye bağımlıdır |

Açık kaynak protokoller araştırmacılar tarafından ayrıntılı biçimde analiz edilebildiğinden güvenlik açıklarının daha hızlı tespit edilmesine olanak tanır.

Kapalı sistemler ise tasarım ayrıntılarının kamuya açık olmaması nedeniyle farklı bir güven modeli benimser. Bununla birlikte, protokol ayrıntılarının gizli tutulması tek başına güvenlik garantisi sağlamaz. Modern güvenlik yaklaşımı; kullanılan algoritmaların gizliliğine değil, kriptografik tasarımın sağlamlığına dayanır.

# Komuta-Kontrol Kanalının Güvenliği

Komuta-kontrol (Command and Control - C2) bağlantısı, insansız hava aracının en kritik bileşenlerinden biridir. Uçuş kontrol komutlarının, telemetri bilgilerinin ve görev verilerinin aynı haberleşme kanalı üzerinden iletilmesi; bu bağlantının gizlilik, bütünlük ve erişilebilirlik açısından korunmasını zorunlu hâle getirir.

Modern drone platformlarında amaç yalnızca haberleşmeyi sağlamak değildir. Aynı zamanda gönderilen verinin gerçekten yetkili bir operatörden geldiğinin doğrulanması, iletim sırasında değiştirilmediğinin garanti edilmesi ve bağlantının görev süresince kesintisiz devam ettirilmesi de hedeflenir.

Bu nedenle günümüzde geliştirilen haberleşme protokolleri klasik kablosuz iletişim sistemlerinden farklı olarak çeşitli güvenlik mekanizmalarıyla desteklenmektedir.

---

## Kimlik Doğrulama (Authentication)

Her haberleşme bağlantısında ilk amaç iletişim kuran tarafların gerçekten beklenen cihazlar olduğunun doğrulanmasıdır.

Drone ekosistemlerinde bu doğrulama;

- Cihaz kimlikleri
- Dijital sertifikalar
- Kriptografik anahtarlar
- Paket imzalama mekanizmaları

gibi yöntemlerle gerçekleştirilebilir.

Kimlik doğrulama mekanizması bulunmayan sistemlerde haberleşme trafiğinin kaynağını doğrulamak mümkün olmayabilir. Bu nedenle modern platformlarda karşılıklı doğrulama (Mutual Authentication) yaklaşımı giderek yaygınlaşmaktadır.

Bu modelde yalnızca drone operatörü doğrulamaz; hava aracı da karşı taraftaki kontrol istasyonunun güvenilir olduğunu doğrular.

---

## Veri Bütünlüğü (Integrity)

Kablosuz haberleşmede iletilen paketlerin değiştirilmeden hedefe ulaşması kritik öneme sahiptir.

Bu amaçla birçok haberleşme protokolünde;

- Message Authentication Code (MAC)
- Hash algoritmaları
- Dijital imzalar
- Paket imzalama (Packet Signing)

kullanılmaktadır.

Veri bütünlüğü mekanizmaları sayesinde alıcı taraf, gelen paketin iletim sırasında değiştirilip değiştirilmediğini doğrulayabilir.

Bu yaklaşım özellikle uçuş komutlarının güvenilir biçimde uygulanabilmesi açısından büyük önem taşır.

---

## Gizlilik (Confidentiality)

Komuta-kontrol bağlantısında taşınan verilerin üçüncü kişiler tarafından okunamaması gerekir.

Bu nedenle modern haberleşme sistemlerinde simetrik şifreleme algoritmaları kullanılmaktadır.

En yaygın kullanılan algoritmalar arasında;

- AES-128
- AES-256

yer almaktadır.

Şifreleme yalnızca uçuş komutlarını değil;

- telemetri verilerini,
- sensör çıktıları,
- görev bilgilerini,
- video akışını

da koruyabilir.

Ancak güçlü bir algoritmanın kullanılması tek başına yeterli değildir.

Anahtar yönetiminin güvenli yapılması, oturum anahtarlarının düzenli olarak yenilenmesi ve güvenli anahtar üretim süreçlerinin uygulanması da aynı derecede önemlidir.

---

## Kullanılabilirlik (Availability)

C2 bağlantısı güvenli olsa bile görev sırasında bağlantının kesilmesi operasyonel açıdan ciddi riskler oluşturabilir.

Bu nedenle haberleşme altyapılarında yüksek erişilebilirlik hedeflenmektedir.

Profesyonel sistemlerde bunun için;

- Otomatik kanal değiştirme
- Yedek haberleşme kanalları
- Adaptif veri oranı
- Hata düzeltme mekanizmaları
- Bağlantı kalite analizi

gibi teknolojiler kullanılmaktadır.

Amaç, zorlu elektromanyetik ortamlarda dahi haberleşmenin mümkün olduğunca kesintisiz devam etmesini sağlamaktır.

---

# Haberleşme Güvenliğinde Kriptografinin Rolü

Kablosuz haberleşmenin doğası gereği iletilen sinyaller fiziksel ortamda yayılır.

Bu nedenle güvenlik yalnızca radyo katmanına bırakılmaz; haberleşme protokolünün üzerinde çalışan kriptografik mekanizmalar da kritik rol oynar.

Modern sistemlerde tipik olarak şu güvenlik bileşenleri birlikte kullanılır:

- Simetrik şifreleme (AES)
- Rastgele sayı üretimi (Nonce)
- Oturum anahtarları (Session Keys)
- Paket imzalama
- Mesaj doğrulama kodları (MAC)
- Replay koruma mekanizmaları

Bu yapı sayesinde haberleşme yalnızca gizlenmekle kalmaz; aynı zamanda iletim sırasında değiştirilmediği ve doğru kaynaktan geldiği de doğrulanabilir.

---

# Haberleşme Performansını Etkileyen Faktörler

Bir komuta-kontrol bağlantısının başarısı yalnızca kullanılan frekans bandına bağlı değildir.

Gerçek saha koşullarında haberleşme performansını etkileyen birçok çevresel faktör bulunmaktadır.

Bunların başlıcaları şunlardır:

- Elektromanyetik parazit (EMI)
- Yoğun Wi-Fi kullanımı
- Çok yollu yayılım (Multipath Propagation)
- Atmosferik koşullar
- Fiziksel engeller
- Anten tasarımı
- Anten yönelimi
- Çıkış gücü
- Alıcı hassasiyeti

Özellikle şehir merkezlerinde aynı frekans bandını kullanan çok sayıda cihazın bulunması, haberleşme kalitesini önemli ölçüde etkileyebilir.

Bu nedenle modern platformlar bağlantı kalitesini sürekli izleyerek en uygun çalışma kanalını dinamik olarak belirleyebilir.

---

# Yazılım Tanımlı Radyo (Software Defined Radio - SDR)

Drone haberleşme sistemlerinin araştırılmasında en yaygın kullanılan teknolojilerden biri Yazılım Tanımlı Radyo (Software Defined Radio - SDR) platformlarıdır.

SDR cihazları klasik donanım tabanlı radyo sistemlerinden farklı olarak birçok sinyal işleme fonksiyonunu yazılım üzerinde gerçekleştirebilir.

Bu sayede araştırmacılar;

- RF spektrumunu gözlemleyebilir,
- farklı frekans bantlarını analiz edebilir,
- sinyal karakteristiklerini inceleyebilir,
- haberleşme protokollerini laboratuvar ortamında değerlendirebilir.

SDR teknolojisi günümüzde;

- akademik araştırmalarda,
- RF mühendisliğinde,
- haberleşme sistemlerinin geliştirilmesinde,
- elektromanyetik uyumluluk testlerinde

yaygın olarak kullanılmaktadır.

Bu araçlar, savunma odaklı analizlerde haberleşme davranışının anlaşılması açısından önemli bir araştırma platformu sunmaktadır.

## Haberleşme Güvenliği ve Kimlik Doğrulama

Drone C2 sistemlerinde güvenlik yalnızca radyo sinyalinin hedefe ulaşmasıyla sınırlı değildir. Asıl önemli olan, bu sinyalin gerçekten yetkili bir operatörden gelip gelmediğinin doğrulanması ve iletim sırasında değiştirilmediğinin garanti altına alınmasıdır.

Bilgi güvenliği açısından değerlendirildiğinde bir C2 bağlantısının sağlaması gereken temel güvenlik özellikleri şunlardır:

- Kimlik doğrulama (Authentication)
- Veri bütünlüğü (Integrity)
- Gizlilik (Confidentiality)
- Erişilebilirlik (Availability)
- Yetkilendirme (Authorization)

Bu özelliklerden herhangi birinin eksik olması, yalnızca haberleşme kalitesini değil, operasyonun güvenilirliğini de doğrudan etkileyebilir.

Örneğin yalnızca güçlü bir şifreleme algoritması kullanılması yeterli değildir. Eğer karşı tarafın kimliği doğrulanmıyorsa, sistem yanlış bir kaynaktan gelen komutları kabul edebilir. Benzer şekilde, kimlik doğrulama uygulanıyor olsa bile iletim sırasında verinin değiştirilmesi engellenemiyorsa, komutların bütünlüğü korunamaz.

Bu nedenle modern C2 mimarileri, güvenliği tek bir katmanda değil; haberleşme zincirinin tamamında ele alır.

---

## Simetrik ve Asimetrik Kriptografi

Komuta-kontrol sistemlerinde kullanılan kriptografik yöntemler genel olarak iki ana grupta incelenebilir.

### Simetrik Şifreleme

Simetrik algoritmalarda aynı anahtar hem şifreleme hem de çözme işlemi için kullanılır.

En yaygın örneklerden biri AES (Advanced Encryption Standard) algoritmasıdır.

Avantajları:

- Düşük işlem maliyeti
- Gerçek zamanlı iletişim için yüksek performans
- Düşük gecikme süresi
- Enerji verimliliği

Bu nedenle birçok C2 platformunda veri aktarımı sırasında simetrik şifreleme tercih edilir.

---

### Asimetrik Şifreleme

Asimetrik kriptografide ise farklı anahtar çiftleri kullanılır.

- Public Key
- Private Key

Bu yöntem özellikle aşağıdaki işlemler için tercih edilir:

- Kimlik doğrulama
- Anahtar değişimi
- Dijital imza
- Sertifika doğrulama

Asimetrik algoritmalar simetrik yöntemlere göre daha yüksek işlem gücü gerektirdiğinden sürekli veri akışının şifrelenmesinde kullanılmaz. Bunun yerine güvenli oturum oluşturulduktan sonra veri iletimi simetrik anahtarlarla devam eder.

Bu hibrit yaklaşım günümüzde TLS, SSH ve benzeri birçok güvenli haberleşme protokolünde olduğu gibi modern C2 sistemlerinde de yaygın olarak kullanılmaktadır.

---

## Oturum Anahtarları (Session Keys)

Uzun süre aynı şifreleme anahtarının kullanılması güvenlik açısından istenmeyen bir durumdur.

Bu nedenle profesyonel sistemlerde her haberleşme oturumu için yeni anahtarlar üretilir.

Genel süreç şu şekilde ilerler:

1. Taraflar birbirlerinin kimliğini doğrular.
2. Güvenli anahtar değişimi gerçekleştirilir.
3. Oturuma özel simetrik anahtar oluşturulur.
4. Haberleşme bu geçici anahtar üzerinden devam eder.
5. Oturum sonlandığında anahtar geçersiz hâle gelir.

Bu yöntem, anahtarların uzun süre kullanılmasından doğabilecek riskleri önemli ölçüde azaltır.

---

## Paket Bütünlüğü (Integrity)

Bir komutun hedefe ulaşması tek başına yeterli değildir.

Gönderilen verinin iletim sırasında değiştirilmediğinin de doğrulanması gerekir.

Bu amaçla çeşitli bütünlük doğrulama mekanizmaları kullanılır.

En yaygın yöntemler arasında:

- HMAC
- SHA-256 tabanlı doğrulama
- AES-GCM
- ChaCha20-Poly1305

gibi algoritmalar yer alır.

Bu mekanizmalar sayesinde alıcı taraf, gelen paketin gerçekten gönderici tarafından üretildiğini ve iletim sırasında değiştirilmediğini doğrulayabilir.

---

## Replay Attack Koruması

Kablosuz haberleşme ortamlarında dikkate alınması gereken önemli risklerden biri de tekrar oynatma (Replay) saldırılarıdır.

Bu senaryoda saldırgan yeni bir komut üretmez.

Bunun yerine daha önce yakalanmış geçerli bir iletişim paketini daha sonra tekrar göndererek sistemin aynı işlemi yeniden gerçekleştirmesini sağlamaya çalışır.

Modern C2 sistemleri bu riski azaltmak amacıyla aşağıdaki mekanizmaları kullanır:

- Nonce değerleri
- Sequence Number
- Timestamp doğrulaması
- Session Identifier

Bu sayede aynı veri paketi ikinci kez gönderildiğinde sistem bunu geçersiz olarak değerlendirebilir.

---

## Fail Safe Mekanizmaları

Hiçbir kablosuz haberleşme sistemi tamamen kesintisiz çalışmayı garanti edemez.

Bu nedenle profesyonel drone platformlarında haberleşme kaybı senaryoları önceden tanımlanır.

Bağlantı belirli bir süre boyunca kurulamazsa uçuş kontrol yazılımı otomatik olarak güvenli moda geçebilir.

Yaygın fail-safe davranışları şunlardır:

- Return to Home (RTH)
- Hover
- Controlled Landing
- Mission Continue
- Emergency Landing

Hangi davranışın uygulanacağı görev senaryosuna göre belirlenir.

Örneğin bir haritalama görevi sırasında görevin devam etmesi tercih edilirken, kritik altyapı yakınında gerçekleştirilen operasyonlarda kontrollü iniş daha güvenli olabilir.

Bu mekanizmalar güvenlik özelliği olarak değerlendirilmese de operasyonel emniyet açısından C2 mimarisinin ayrılmaz bir parçasıdır.

# Haberleşme Protokolleri ve RF Katmanı

Bir C2 sisteminin güvenliği yalnızca kullanılan frekans bandına bağlı değildir. Aynı frekans üzerinde çalışan iki farklı platform, tamamen farklı güvenlik seviyelerine sahip olabilir. Bunun temel nedeni; fiziksel katmanın üzerinde çalışan haberleşme protokolleri, paket yapıları, hata düzeltme mekanizmaları ve kimlik doğrulama süreçleridir.

Modern drone platformlarında haberleşme mimarisi genellikle katmanlı olarak tasarlanır.

```
Application Layer
│
├── Flight Commands
├── Telemetry
├── Video Stream
│
Transport Layer
│
├── MAVLink
├── Proprietary Protocol
│
Data Link Layer
│
├── Packet Framing
├── CRC
├── Error Correction
│
Physical Layer
│
└── RF (433 MHz / 900 MHz / 2.4 GHz / 5.8 GHz)
```

Bu mimaride fiziksel katman yalnızca bitlerin iletiminden sorumludur. Güvenlik ise üst katmanlarda uygulanan doğrulama, bütünlük ve oturum yönetimi mekanizmalarıyla sağlanır.

---

## Yaygın Kullanılan Haberleşme Teknolojileri

Drone ekosisteminde tek bir standart bulunmaz. Platformun amacı, menzili ve üreticisi kullanılan haberleşme mimarisini doğrudan etkiler.

### Wi-Fi Tabanlı Sistemler

Hobi ve giriş seviyesi platformlarda en yaygın yöntemlerden biri IEEE 802.11 tabanlı haberleşmedir.

Avantajları:

- Düşük maliyet
- Yaygın donanım desteği
- Yüksek bant genişliği
- Kolay entegrasyon

Dezavantajları:

- Parazitlere karşı daha hassas olması
- Yoğun şehir ortamlarında kanal çakışmaları
- Sınırlı menzil
- Enerji tüketiminin görece yüksek olması

---

### LoRa Tabanlı Haberleşme

Uzun menzilli telemetri sistemlerinde LoRa teknolojisi sıklıkla tercih edilir.

LoRa; düşük veri hızı karşılığında kilometrelerce haberleşme sağlayabilir.

Bu nedenle;

- tarım dronları,
- çevresel sensör ağları,
- insansız kara araçları,
- uzun menzilli keşif platformları

gibi uygulamalarda yaygın olarak kullanılmaktadır.

Ancak LoRa yüksek bant genişliği gerektiren video aktarımı için uygun değildir.

---

### Özel (Proprietary) RF Protokolleri

DJI, Autel, Skydio ve benzeri üreticiler kendi haberleşme protokollerini geliştirmektedir.

Örneğin DJI platformlarında kullanılan OcuSync teknolojisi;

- dinamik frekans seçimi,
- adaptif veri oranı,
- ileri hata düzeltme,
- çoklu anten (MIMO),
- otomatik kanal optimizasyonu

gibi gelişmiş özellikler sunmaktadır.

Bu tür protokollerin ayrıntıları çoğu zaman kamuya açık değildir.

Dolayısıyla güvenlik değerlendirmeleri daha çok akademik çalışmalar, üretici dokümantasyonu ve tersine mühendislik araştırmaları üzerinden yapılmaktadır.

---

# MAVLink Protokolü

Açık kaynak drone ekosisteminin fiili standartlarından biri MAVLink (Micro Air Vehicle Link) protokolüdür.

ArduPilot ve PX4 tabanlı sistemlerin büyük bölümü bu protokolü kullanmaktadır.

MAVLink oldukça hafif bir mesajlaşma protokolüdür.

Temel amacı;

- uçuş komutlarını taşımak,
- telemetri aktarmak,
- sensör verilerini iletmek,
- görev planlarını paylaşmak

olarak özetlenebilir.

Basitleştirilmiş bir MAVLink paketi aşağıdaki bileşenlerden oluşur.

```
+------------------------------------------------+
| Start Byte                                     |
+------------------------------------------------+
| Payload Length                                 |
+------------------------------------------------+
| Packet Sequence                                |
+------------------------------------------------+
| System ID                                      |
+------------------------------------------------+
| Component ID                                   |
+------------------------------------------------+
| Message ID                                     |
+------------------------------------------------+
| Payload                                        |
+------------------------------------------------+
| CRC                                            |
+------------------------------------------------+
```

Her paket belirli bir mesaj tipini temsil eder.

Örneğin;

- HEARTBEAT
- ATTITUDE
- GPS_RAW_INT
- GLOBAL_POSITION_INT
- BATTERY_STATUS
- COMMAND_LONG
- MISSION_ITEM

gibi mesajlar uçuş boyunca sürekli olarak iletilir.

Bu yapı sayesinde farklı üreticilerin geliştirdiği uçuş kontrol yazılımları ortak bir protokol üzerinden haberleşebilir.

Bu standartlaşma açık kaynak ekosisteminin büyümesini sağlayan en önemli faktörlerden biridir.

---

## MAVLink 1 ve MAVLink 2 Arasındaki Farklar

İlk sürüm olan MAVLink 1 performans odaklı tasarlanmıştır.

Ancak güvenlik açısından önemli eksikliklere sahiptir.

Örneğin;

- mesaj imzalama bulunmaz,
- paketler varsayılan olarak şifrelenmez,
- kimlik doğrulama mekanizması içermez.

Bu nedenle modern sistemlerde mümkün olduğunca MAVLink 2 tercih edilmektedir.

MAVLink 2 ile birlikte;

- Packet Signing
- genişletilmiş mesaj yapısı
- daha fazla mesaj tipi
- uyumluluk geliştirmeleri

protokole eklenmiştir.

Packet Signing özelliği sayesinde alıcı sistem, gelen paketin gerçekten yetkili kaynaktan gelip gelmediğini doğrulayabilir.

Bu özellik mesaj bütünlüğünün korunmasına önemli katkı sağlar.

Ancak unutulmamalıdır ki paket imzalama ile uçtan uca şifreleme aynı kavram değildir.

İmzalama;

- mesajın değiştirilmediğini,
- doğru kaynaktan geldiğini

kanıtlamaya yardımcı olur.

Şifreleme ise mesaj içeriğinin üçüncü taraflar tarafından okunmasını engeller.

Modern profesyonel platformlarda her iki yaklaşımın birlikte kullanılması tavsiye edilmektedir. 

# C2 Güvenlik Mimarisi

Komuta-kontrol sistemleri yalnızca veri ileten haberleşme altyapıları değildir. Aynı zamanda hava aracının güvenlik sınırını oluşturan en kritik bileşendir. Bir C2 bağlantısının kesilmesi, gecikmesi veya bütünlüğünü kaybetmesi doğrudan uçuş emniyetini etkileyebilir.

Bu nedenle modern sistemlerde güvenlik, yalnızca RF katmanında değil; haberleşmenin tamamında ele alınır.

Temel güvenlik hedefleri aşağıdaki dört başlık altında toplanabilir.

- Authentication (Kimlik Doğrulama)
- Integrity (Bütünlük)
- Confidentiality (Gizlilik)
- Availability (Erişilebilirlik)

Bu dört ilke, yalnızca klasik bilgi güvenliği sistemlerinde değil, insansız hava araçlarının komuta-kontrol altyapılarında da temel tasarım prensiplerini oluşturur.

---

## Kimlik Doğrulama (Authentication)

Bir C2 sisteminde ilk soru şudur:

> "Gönderilen komut gerçekten yetkili operatörden mi geliyor?"

Eğer bu doğrulama güvenilir şekilde yapılamıyorsa, haberleşmenin geri kalan kısmının güvenli olmasının da anlamı kalmaz.

Modern platformlarda bu amaçla;

- cihaz kimlikleri,
- dijital sertifikalar,
- oturum anahtarları,
- mesaj imzalama mekanizmaları

kullanılır.

Özellikle profesyonel platformlarda Ground Control Station ile Flight Controller arasında karşılıklı kimlik doğrulama (Mutual Authentication) uygulanır.

Böylece yalnızca drone operatörü doğrulanmaz; drone da haberleştiği yer kontrol istasyonunun gerçekten yetkili sistem olduğunu doğrular.

Bu yaklaşım, sahte yer kontrol istasyonlarının sisteme dahil olmasını engellemeye yardımcı olur.

---

## Veri Bütünlüğü (Integrity)

Bir haberleşme paketinin hedefe ulaşması tek başına yeterli değildir.

Paketin iletim sırasında değiştirilmemiş olması da doğrulanmalıdır.

Bu amaçla çeşitli bütünlük mekanizmaları kullanılır.

Örneğin;

- CRC
- SHA tabanlı özet algoritmaları
- HMAC
- Packet Signing

en yaygın kullanılan yöntemler arasında yer alır.

CRC yalnızca iletim hatalarını tespit etmeye yöneliktir.

Kriptografik güvenlik sağlamaz.

Bu nedenle güvenlik açısından kritik sistemlerde dijital imzalama veya HMAC tabanlı bütünlük doğrulama tercih edilir.

---

## Gizlilik (Confidentiality)

Komuta paketleri, telemetri verileri ve görev planları hassas bilgiler içerebilir.

Örneğin;

- görev koordinatları,
- rota bilgileri,
- hedef noktaları,
- sensör çıktıları,
- kamera yönelim bilgileri,
- görev süresi

operasyonel açıdan kritik kabul edilir.

Bu nedenle birçok profesyonel platform haberleşme sırasında şifreleme kullanmaktadır.

Yaygın olarak kullanılan algoritmalar arasında;

- AES-128
- AES-256
- ChaCha20

bulunmaktadır.

Şifreleme sayesinde haberleşme trafiği üçüncü taraflar tarafından gözlemlense bile içerik okunamaz.

---

## Erişilebilirlik (Availability)

Komuta-kontrol sistemlerinin güvenliği yalnızca gizlilikten ibaret değildir.

Bir C2 bağlantısı sürekli çalışabilir durumda olmalıdır.

Bağlantının tamamen kopması;

- görevin iptal edilmesine,
- otomatik eve dönüş (Return To Home),
- acil iniş,
- güvenli uçuş moduna geçiş

gibi durumları tetikleyebilir.

Bu nedenle profesyonel platformlar;

- yedek haberleşme kanalları,
- frekans atlamalı iletişim,
- otomatik kanal değiştirme,
- adaptif veri oranı

gibi mekanizmalar kullanarak bağlantının sürekliliğini artırmayı hedefler.

---

# Haberleşmede Hata Yönetimi

Kablosuz iletişim doğası gereği kararsızdır.

Atmosferik koşullar, elektromanyetik girişimler, çok yollu yayılım (Multipath Propagation) ve fiziksel engeller paket kayıplarına neden olabilir.

Bu nedenle modern C2 sistemlerinde hata yönetimi kritik öneme sahiptir.

Yaygın kullanılan yöntemler şunlardır.

## CRC (Cyclic Redundancy Check)

Her paket gönderilmeden önce matematiksel bir kontrol değeri oluşturulur.

Alıcı taraf aynı hesabı tekrar yapar.

Sonuçlar uyuşmuyorsa paket geçersiz kabul edilir.

CRC yalnızca iletim hatalarını tespit eder.

Saldırılara karşı güvenlik sağlamaz.

---

## Forward Error Correction (FEC)

FEC yaklaşımında veri gönderilirken fazladan düzeltme bitleri de eklenir.

Böylece bazı paketler kaybolsa bile alıcı taraf eksik verileri yeniden oluşturabilir.

Özellikle;

- uzun menzilli haberleşme,
- video aktarımı,
- gerçek zamanlı telemetri

uygulamalarında yaygın olarak kullanılmaktadır.

---

## Automatic Repeat Request (ARQ)

Bazı sistemlerde eksik paket tespit edildiğinde alıcı taraf yeniden gönderim talebinde bulunur.

Bu yöntem doğruluğu artırmasına rağmen gecikmeyi yükseltebilir.

Gerçek zamanlı uçuş kontrolünde bu nedenle dikkatli kullanılır.

---

# Adaptif Haberleşme Yaklaşımı

Modern drone platformları tek bir veri hızında çalışmaz.

Bağlantı kalitesi sürekli ölçülür.

Örneğin;

- RSSI
- SNR
- Packet Loss
- RTT

gibi metrikler değerlendirilerek sistem dinamik kararlar verir.

Bağlantı kalitesi düştüğünde;

- veri oranı azaltılabilir,
- video çözünürlüğü düşürülebilir,
- farklı frekans kanalına geçilebilir,
- farklı anten kullanılabilir.

Bu yaklaşım sayesinde haberleşmenin tamamen kopması yerine daha düşük performansla da olsa devam etmesi sağlanabilir.

Özellikle profesyonel platformlarda görevin tamamlanması, maksimum bant genişliğinden daha önceliklidir. 

# Modern C2 Sistemlerinde Dayanıklılık Mekanizmaları

Komuta-kontrol bağlantılarının güvenilirliği yalnızca güçlü şifreleme algoritmalarıyla sağlanmaz. Haberleşme altyapısının çevresel koşullara, elektromanyetik parazitlere ve beklenmeyen bağlantı kesintilerine karşı dayanıklı olması da en az güvenlik kadar önemlidir.

Bu nedenle profesyonel insansız hava aracı platformları, bağlantının sürekliliğini artırmak amacıyla çeşitli dayanıklılık (resilience) mekanizmaları kullanır.

---

## Frequency Hopping Spread Spectrum (FHSS)

Kablosuz haberleşmede aynı frekansta uzun süre iletişim kurulması çeşitli riskleri beraberinde getirir.

- Elektromanyetik girişimler
- Kanal yoğunluğu
- Ortak frekans kullanan diğer cihazlar
- Haberleşme kalitesindeki ani değişimler

bağlantının kararlılığını olumsuz etkileyebilir.

Bu nedenle birçok modern platform Frequency Hopping Spread Spectrum (FHSS) tekniğini kullanır.

FHSS yaklaşımında haberleşme tek bir RF kanalı üzerinde sabit kalmaz.

Bunun yerine önceden belirlenmiş bir frekans dizisi boyunca çok kısa zaman aralıklarıyla kanal değiştirilir.

```
2405 MHz
      │
      ▼
2412 MHz
      │
      ▼
2437 MHz
      │
      ▼
2462 MHz
      │
      ▼
2450 MHz
```

Bu yaklaşım sayesinde;

- parazitlerden etkilenme azalır,
- aynı frekanstaki yoğunluk düşürülür,
- bağlantının sürekliliği artırılır.

FHSS, özellikle yüksek elektromanyetik yoğunluğa sahip şehir ortamlarında önemli avantaj sağlar.

---

## Adaptive Frequency Selection (AFS)

Profesyonel sistemlerde yalnızca belirli aralıklarla frekans değiştirmek yeterli görülmez.

Bağlantı kalitesi sürekli analiz edilir.

Örneğin sistem;

- RSSI
- SNR
- Packet Error Rate
- Channel Utilization

gibi ölçümleri değerlendirerek en uygun RF kanalını otomatik olarak seçebilir.

Bu mekanizma Adaptive Frequency Selection olarak adlandırılır.

Amaç, haberleşmeyi en temiz frekansta sürdürebilmektir.

---

## Diversity Antenna Teknolojisi

Tek anten kullanan sistemlerde;

- gölgelenme,
- çok yollu yayılım,
- fiziksel engeller

nedeniyle sinyal kalitesi önemli ölçüde düşebilir.

Bu nedenle birçok profesyonel platform birden fazla anten kullanır.

```
        Drone

   Antenna A
        │
        ▼

   RF Receiver

        ▲
        │
   Antenna B
```

Alıcı taraf sürekli olarak hangi antenin daha güçlü sinyal aldığına karar verir.

Bazı gelişmiş platformlarda aynı anda birden fazla anten üzerinden veri alınarak hata oranı azaltılır.

Bu yaklaşım Antenna Diversity olarak adlandırılır.

---

## MIMO Teknolojisi

Yeni nesil profesyonel platformlarda yalnızca anten çeşitliliği değil, Multiple Input Multiple Output (MIMO) mimarisi de kullanılmaktadır.

MIMO sistemlerinde aynı anda birden fazla veri akışı farklı antenlerden iletilebilir.

Avantajları şunlardır.

- Daha yüksek veri hızı
- Daha düşük paket kaybı
- Daha uzun menzil
- Daha kararlı video aktarımı

Özellikle yüksek çözünürlüklü görüntü aktarımı yapan sistemlerde MIMO önemli avantaj sağlar.

---

# Fail-Safe Mekanizmaları

Her haberleşme bağlantısı belirli koşullar altında kesilebilir.

Profesyonel hava araçları bu durumları "olağan dışı" değil, "beklenen" senaryolar olarak kabul eder.

Bu nedenle Flight Controller içerisinde çeşitli Fail-Safe algoritmaları bulunur.

En yaygın senaryolar aşağıdaki gibidir.

---

## Return To Home (RTH)

Komuta-kontrol bağlantısı belirli bir süre boyunca kesildiğinde drone daha önce kaydedilen güvenli noktaya otomatik olarak geri dönebilir.

```
Mission

      ▼

 Signal Lost

      ▼

 Return To Home

      ▼

 Automatic Landing
```

RTH mekanizması;

- GPS,
- pusula,
- barometre,
- irtifa sensörleri

yardımıyla güvenli dönüş rotasını hesaplar.

---

## Hover Mode

Bazı platformlar bağlantı kesildiğinde bulunduğu konumda beklemeyi tercih eder.

Bu davranış özellikle şehir ortamlarında ani hareketlerin önlenmesi açısından önemlidir.

Bağlantı yeniden kurulduğunda görev devam edebilir.

---

## Automatic Landing

GPS doğruluğunun düşük olduğu veya batarya seviyesinin kritik olduğu durumlarda sistem kontrollü iniş prosedürünü başlatabilir.

Bu mekanizma platformun kontrolsüz şekilde düşmesini engellemeye yardımcı olur.

---

## Geofence Enforcement

Modern sistemlerde uçuş alanları önceden tanımlanabilir.

Drone izin verilen bölgenin dışına çıktığında;

- uyarı verebilir,
- hızı sınırlandırabilir,
- otomatik geri dönüş başlatabilir,
- görevi sonlandırabilir.

Bu yaklaşım özellikle kritik tesislerde operasyonel güvenliği artırmaktadır.

---

# Telemetri Verileri Neleri İçerir?

Komuta-kontrol bağlantısı yalnızca komut taşımaktan sorumlu değildir.

Drone sürekli olarak çok sayıda operasyonel bilgiyi yer kontrol istasyonuna gönderir.

En yaygın telemetri verileri şunlardır.

| Veri | Açıklama |
|------|----------|
| GPS Koordinatı | Anlık konum bilgisi |
| İrtifa | Deniz seviyesine göre yükseklik |
| Hız | Yatay ve dikey hız |
| Heading | Yönelim bilgisi |
| Pitch / Roll / Yaw | Uçağın uzaysal durumu |
| Batarya Seviyesi | Pil kapasitesi ve voltaj |
| Motor Durumu | ESC ve motor sağlık bilgileri |
| Uçuş Modu | Auto, Loiter, RTL, Manual vb. |
| Uydu Sayısı | GPS doğruluğu için kullanılan uydu sayısı |
| Sinyal Kalitesi | RSSI ve bağlantı gücü |
| Sensör Sağlığı | IMU, pusula ve barometre durumları |

Bu bilgiler yalnızca operatörün uçuşu takip etmesini sağlamaz.

Aynı zamanda;

- görev analizi,
- olay incelemesi,
- adli bilişim,
- bakım planlaması,
- performans değerlendirmesi

gibi süreçlerde de kritik öneme sahiptir.

Profesyonel platformlarda telemetri kayıtları çoğu zaman görev sonrasında ayrıntılı olarak analiz edilir ve uçuş geçmişi uzun süre saklanır. 

# Drone C2 Güvenliğinde Tehdit Modellemesi

Bir komuta-kontrol altyapısını güvenli hâle getirebilmek için yalnızca kullanılan teknolojileri bilmek yeterli değildir. Aynı zamanda bu mimarinin hangi tehditlere maruz kalabileceğinin sistematik biçimde değerlendirilmesi gerekir.

Kurumsal güvenlik ekipleri ve Red Team ekipleri bu amaçla tehdit modelleme (Threat Modeling) metodolojilerinden yararlanır.

En yaygın kullanılan yaklaşımlar arasında;

- STRIDE
- MITRE ATT&CK
- NIST Risk Management Framework (RMF)
- ENISA Threat Landscape

bulunmaktadır.

Bu metodolojiler, olası risklerin yalnızca teknik açıdan değil; operasyonel süreçler, insan faktörü ve sistem mimarisi açısından da değerlendirilmesini sağlar.

---

# Drone C2 Sistemlerinde Tehdit Yüzeyi

Bir insansız hava aracının saldırı yüzeyi yalnızca RF haberleşmesinden oluşmaz.

Tipik bir platform aşağıdaki bileşenlerden meydana gelir.

```text
Operator
    │
    ▼
Ground Control Station
    │
    ▼
Communication Network
    │
    ▼
Flight Controller
    │
 ┌──┴────────────┐
 ▼               ▼
Firmware      Navigation
 │               │
 ▼               ▼
Telemetry     Sensors
 │
 ▼
Cloud Services
```

Bu mimaride her bileşen farklı güvenlik riskleri barındırmaktadır.

Örneğin;

- Ground Control Station istemci güvenliği
- RF haberleşme güvenliği
- Firmware bütünlüğü
- Sensör doğruluğu
- GPS güvenilirliği
- Bulut servislerinin güvenliği
- Mobil uygulamaların korunması

ayrı ayrı değerlendirilmelidir.

Bu nedenle modern güvenlik değerlendirmeleri yalnızca tek bir bileşene odaklanmak yerine tüm ekosistemi birlikte ele alır.

---

# STRIDE Perspektifinden Değerlendirme

Microsoft tarafından geliştirilen STRIDE modeli, bilgi sistemlerinin tehdit analizinde yaygın olarak kullanılmaktadır.

Drone komuta-kontrol altyapılarına da kolaylıkla uygulanabilir.

| STRIDE Kategorisi | Drone C2 Örneği |
|-------------------|-----------------|
| Spoofing | Yetkisiz cihazın kendisini meşru GCS gibi göstermesi |
| Tampering | Haberleşme paketlerinin değiştirilmesi |
| Repudiation | Yapılan işlemlerin inkâr edilebilmesi |
| Information Disclosure | Telemetri bilgilerinin yetkisiz kişilerce görüntülenmesi |
| Denial of Service | Haberleşmenin kesintiye uğraması |
| Elevation of Privilege | Yetkisiz kullanıcının yönetici hakları kazanması |

Bu yaklaşım sayesinde yalnızca mevcut açıklıklar değil, gelecekte ortaya çıkabilecek tasarım riskleri de değerlendirilebilir.

---

# MITRE ATT&CK Perspektifi

MITRE ATT&CK çerçevesi, saldırgan davranışlarını standartlaştırılmış teknikler üzerinden sınıflandırmayı amaçlar.

Her ne kadar ağırlıklı olarak kurumsal BT sistemleri için geliştirilmiş olsa da, komuta-kontrol altyapılarının değerlendirilmesinde de faydalı bir referans sunar.

Örneğin bir C2 ekosisteminde aşağıdaki alanlar değerlendirilebilir.

- Initial Access
- Credential Access
- Discovery
- Collection
- Exfiltration
- Command and Control
- Defense Evasion

Burada amaç saldırı senaryoları üretmek değil; hangi güvenlik kontrollerinin eksik olduğunun sistematik biçimde belirlenmesidir.

Kurumsal güvenlik ekipleri bu yaklaşımı kullanarak savunma katmanlarını önceliklendirebilir.

---

# Risk Analizinde Değerlendirilen Başlıca Alanlar

Profesyonel güvenlik değerlendirmelerinde aşağıdaki başlıklar sistematik olarak incelenir.

| Değerlendirilen Alan | İncelenen Unsurlar |
|----------------------|--------------------|
| Kimlik Doğrulama | Operatör kimliği, cihaz kimliği, sertifikalar |
| Haberleşme | Şifreleme, bütünlük, gecikme, süreklilik |
| Flight Controller | Güvenli önyükleme, firmware doğrulama |
| Firmware | Güncelleme mekanizması, dijital imza |
| Telemetri | Veri gizliliği ve doğruluğu |
| Yer Kontrol İstasyonu | İşletim sistemi, kullanıcı yetkilendirmesi |
| Bulut Altyapısı | API güvenliği, erişim kontrolü |
| Günlük Kayıtları | Merkezi loglama ve olay analizi |

Bu yaklaşım, platformun yalnızca bugünkü güvenlik durumunu değil; uzun vadeli operasyonel dayanıklılığını da değerlendirmeye yardımcı olur.

---

# Güvenlik Değerlendirmelerinde Operasyonel Faktörler

Teknik güvenlik kontrolleri kadar operasyonel süreçler de önemlidir.

Örneğin aşağıdaki sorular güvenlik değerlendirmelerinde sıklıkla ele alınır.

- Firmware güncellemeleri nasıl yönetiliyor?
- Kim yeni görev planı oluşturabiliyor?
- Operatör hesapları nasıl korunuyor?
- Görev kayıtları ne kadar süre saklanıyor?
- Telemetri verileri nerede depolanıyor?
- Uçuş loglarına kimler erişebiliyor?
- Anahtar yönetimi merkezi olarak mı gerçekleştiriliyor?
- Cihaz envanteri düzenli olarak güncelleniyor mu?

Bu soruların yanıtları, teknik açıklıklardan bağımsız olarak kurumun güvenlik olgunluğunu ortaya koyar.

Modern güvenlik anlayışında güvenli bir sistem yalnızca güçlü algoritmalar kullanan sistem değil; süreçleri doğru yöneten sistem olarak kabul edilmektedir. 

# Kurumsal Savunma Yaklaşımları

Drone komuta-kontrol sistemlerinin güvenliği yalnızca güçlü haberleşme protokollerine dayanmaz. Güvenilir bir mimari; kimlik yönetimi, anahtar yönetimi, ağ segmentasyonu, sürekli izleme ve güvenli yazılım geliştirme süreçlerinin birlikte uygulanmasını gerektirir.

Savunma yaklaşımının temel amacı, tek bir güvenlik katmanına bağımlı kalmadan çok katmanlı (Defense in Depth) bir mimari oluşturmaktır.

---

# Güvenli Kimlik Yönetimi

Komuta-kontrol sistemlerinde en kritik güvenlik unsurlarından biri operatör kimliğinin doğrulanmasıdır.

Yer kontrol istasyonuna erişim sağlayan her kullanıcı aynı yetkilere sahip olmamalıdır.

Modern platformlarda aşağıdaki prensipler uygulanmaktadır.

- Çok faktörlü kimlik doğrulama (MFA)
- Rol tabanlı yetkilendirme (RBAC)
- En az ayrıcalık prensibi (Least Privilege)
- Ayrıcalıklı hesap yönetimi (PAM)
- Merkezi kimlik yönetimi (IAM)

Örneğin;

Bir bakım personelinin yalnızca sistem durumunu görüntüleyebilmesi yeterliyken, görev planlarını değiştirme veya firmware güncellemesi yapma yetkisi yalnızca yetkili operatörlere verilmelidir.

Bu yaklaşım insan kaynaklı riskleri önemli ölçüde azaltır.

---

# Güvenli Anahtar Yönetimi

Şifreleme algoritmaları kadar kullanılan kriptografik anahtarların nasıl üretildiği, saklandığı ve yenilendiği de kritik öneme sahiptir.

Modern C2 altyapılarında anahtar yönetimi aşağıdaki prensiplere göre yürütülür.

- Rastgele anahtar üretimi
- Donanımsal güvenlik modülleri (HSM)
- Düzenli anahtar rotasyonu
- Güvenli anahtar depolama
- Anahtar erişim kayıtlarının tutulması

Kriptografik anahtarların düz metin olarak saklanması veya tüm cihazlarda ortak anahtar kullanılması, güvenlik seviyesini ciddi ölçüde düşürebilir.

---

# Güvenli Firmware Yönetimi

Bir drone'un güvenliği yalnızca uçuş sırasında değil, üretim ve bakım süreçlerinde de korunmalıdır.

Bu nedenle firmware yaşam döngüsü güvenli biçimde yönetilmelidir.

Profesyonel platformlarda aşağıdaki mekanizmalar uygulanır.

- Secure Boot
- Firmware Signing
- Güvenli OTA (Over-the-Air) güncellemeleri
- Firmware bütünlük doğrulaması
- Geri dönüş (Rollback) koruması

Bu kontroller sayesinde yalnızca üretici tarafından imzalanmış ve doğrulanmış yazılımların çalıştırılması sağlanır.

---

# Ağ Segmentasyonu

Kurumsal ortamlarda yer kontrol istasyonlarının doğrudan kurumsal kullanıcı ağı üzerinde çalıştırılması önerilmez.

Bunun yerine;

```text
Corporate Network
        │
        ▼
Firewall
        │
        ▼
Drone Operations VLAN
        │
        ▼
Ground Control Station
        │
        ▼
Mission Server
```

şeklinde ayrı bir operasyon ağı oluşturulması tavsiye edilir.

Bu mimari sayesinde olası bir güvenlik olayının diğer kurumsal sistemlere yayılma riski azaltılabilir.

---

# Log Yönetimi ve SIEM Entegrasyonu

Profesyonel operasyonlarda uçuş sırasında oluşan olay kayıtları yalnızca saklanmak için değil, güvenlik analizi amacıyla da kullanılır.

Toplanan loglar genellikle aşağıdaki sistemlerden gelir.

- Ground Control Station
- Flight Controller
- Telemetri Sunucuları
- Kimlik Yönetim Sistemi
- Ağ Cihazları
- Bulut Servisleri

Bu kayıtlar merkezi SIEM platformlarına aktarılır.

Böylece farklı kaynaklardan gelen olaylar ilişkilendirilerek güvenlik ekiplerine anlamlı uyarılar üretilebilir.

Örneğin;

- Aynı operatör hesabının farklı lokasyonlardan oturum açması,
- Normal çalışma saatleri dışında görev oluşturulması,
- Beklenmeyen firmware güncellemesi,
- Aynı drone'un kısa süre içinde farklı görev planlarıyla kullanılması

gibi olaylar otomatik korelasyon kurallarıyla tespit edilebilir.

---

# Sürekli İzleme (Continuous Monitoring)

Modern güvenlik anlayışında sistemlerin yalnızca güvenli kurulması yeterli değildir.

Kurulum sonrasında da sürekli olarak izlenmeleri gerekir.

İzleme kapsamında değerlendirilen başlıca metrikler şunlardır.

| İzleme Alanı | Amaç |
|--------------|------|
| RF Bağlantı Kalitesi | Haberleşme kararlılığını izlemek |
| Telemetri Tutarlılığı | Beklenmeyen veri değişimlerini belirlemek |
| Firmware Durumu | Yetkisiz değişiklikleri tespit etmek |
| Operatör Etkinlikleri | Anormal kullanıcı davranışlarını belirlemek |
| Sistem Sağlığı | Donanım arızalarını erken tespit etmek |
| Güvenlik Logları | Olay müdahalesini hızlandırmak |

Bu yaklaşım sayesinde yalnızca gerçekleşmiş güvenlik olayları değil, potansiyel riskler de erken aşamada fark edilebilir.

---

# Zero Trust Yaklaşımının Drone Ekosistemine Uyarlanması

Zero Trust mimarisinin temel prensibi oldukça basittir.

> **"Never Trust, Always Verify."**

Bu yaklaşım drone komuta-kontrol sistemlerine uygulandığında;

- hiçbir cihaz varsayılan olarak güvenilir kabul edilmez,
- her oturum yeniden doğrulanır,
- erişim kararları bağlamsal olarak değerlendirilir,
- kullanıcı davranışları sürekli izlenir.

Örneğin;

- farklı ülkeden yapılan operatör oturumları,
- alışılmadık saatlerde görev planı oluşturulması,
- yeni bir cihazdan sisteme erişim,
- beklenmeyen firmware yükleme girişimleri

ek doğrulama mekanizmalarını tetikleyebilir.

Bu yaklaşım özellikle kritik altyapılar, kamu kurumları, savunma sanayii ve endüstriyel İHA operasyonlarında giderek daha fazla benimsenmektedir. 

# Yapay Zekâ ve Davranış Analitiği ile C2 Güvenliği

Komuta-kontrol sistemlerinden üretilen telemetri verileri yalnızca uçuşun anlık olarak izlenmesini sağlamaz. Aynı zamanda operasyonel güvenlik, olay müdahalesi ve adli bilişim süreçleri açısından oldukça değerli bilgiler içerir.

Büyük ölçekli İHA filolarında her uçuş boyunca milyonlarca veri noktası oluşabilir.

Bu veriler arasında;

- GPS koordinatları,
- hız bilgileri,
- irtifa değişimleri,
- batarya durumu,
- RF sinyal kalitesi,
- paket kayıp oranları,
- sensör çıktıları,
- operatör komutları,
- görev planı değişiklikleri

yer alır.

Bu hacimdeki verilerin manuel olarak incelenmesi pratik değildir.

Bu nedenle modern platformlarda davranış analitiği (Behavior Analytics) ve makine öğrenmesi tabanlı güvenlik sistemleri giderek daha fazla kullanılmaktadır.

---

# Anomali Tespiti (Anomaly Detection)

Geleneksel güvenlik sistemleri belirli kurallara göre çalışır.

Örneğin;

- bağlantı kesildiğinde alarm üret,
- batarya %15'in altına düştüğünde uyarı ver,
- GPS sinyali kaybolduğunda RTH başlat

gibi eşik tabanlı kurallar uygulanır.

Ancak gerçek operasyonlarda tüm riskler önceden tanımlanamaz.

Bu nedenle davranış analitiği sistemleri, platformun normal çalışma düzenini öğrenmeye çalışır.

Örneğin sistem;

- normal uçuş süresi,
- ortalama hız,
- tipik görev bölgeleri,
- RF bağlantı kalitesi,
- operatör davranışları,
- telemetri desenleri

gibi parametrelerden bir profil oluşturur.

Bu profilden önemli sapmalar meydana geldiğinde güvenlik ekipleri uyarılabilir.

---

# Operatör Davranış Analizi (UEBA)

User and Entity Behavior Analytics (UEBA), yalnızca kullanıcı kimliğini doğrulamakla yetinmez.

Kullanıcının sistemi nasıl kullandığını da analiz eder.

Örneğin aşağıdaki davranışlar risk puanını artırabilir.

- Daha önce kullanılmamış bir cihazdan giriş yapılması
- Normal çalışma saatleri dışında görev oluşturulması
- Kısa süre içerisinde çok sayıda görev planının değiştirilmesi
- Aynı hesabın farklı coğrafi konumlardan kullanılması
- Alışılmışın dışında uçuş parametrelerinin seçilmesi

Tek başına bu olaylar güvenlik ihlali anlamına gelmeyebilir.

Ancak birlikte değerlendirildiklerinde operasyonel açıdan dikkat gerektiren durumlar oluşturabilir.

---

# Telemetri Analitiği

Modern güvenlik platformları yalnızca kullanıcı davranışlarını değil, drone'un ürettiği telemetri verilerini de analiz eder.

İncelenen başlıca parametreler şunlardır.

| Parametre | Analiz Amacı |
|-----------|--------------|
| GPS Sapmaları | Konum tutarlılığının değerlendirilmesi |
| İrtifa Profili | Olağan dışı irtifa değişimlerinin belirlenmesi |
| Motor Verileri | Donanım arızalarının erken tespiti |
| Batarya Eğrisi | Beklenmeyen güç tüketiminin izlenmesi |
| RSSI | RF bağlantı kalitesinin değerlendirilmesi |
| Packet Loss | Haberleşme kararlılığının ölçülmesi |
| Sensör Tutarlılığı | IMU ve GPS verilerinin karşılaştırılması |

Bu analizler yalnızca güvenlik amacıyla değil, kestirimci bakım (Predictive Maintenance) süreçlerinde de kullanılmaktadır.

---

# Güvenlik Operasyon Merkezleri (SOC) ve Drone Filoları

Kurumsal yapılarda drone operasyonları artık bağımsız sistemler olarak değerlendirilmemektedir.

Birçok organizasyonda komuta-kontrol altyapıları doğrudan Güvenlik Operasyon Merkezi (Security Operations Center - SOC) ile entegre çalışmaktadır.

Bu sayede;

- uçuş kayıtları,
- kullanıcı oturumları,
- ağ trafiği,
- kimlik doğrulama olayları,
- sistem logları,
- telemetri verileri

tek bir platform üzerinden analiz edilebilir.

Bu yaklaşım farklı güvenlik olaylarının ilişkilendirilmesini kolaylaştırır.

Örneğin;

- Operatör hesabında olağan dışı bir oturum açılması,
- Aynı zaman aralığında yeni bir görev planı oluşturulması,
- Beklenmeyen bir firmware güncellemesi,
- Telemetri verilerinde olağan dışı değişimler

birlikte değerlendirildiğinde güvenlik ekipleri daha anlamlı bir görünürlük elde edebilir.

---

# Dijital İkiz (Digital Twin) Yaklaşımı

Son yıllarda savunma sanayii ve endüstriyel İHA projelerinde öne çıkan kavramlardan biri de Digital Twin mimarisidir.

Dijital ikiz, fiziksel hava aracının gerçek zamanlı dijital modelidir.

Bu model sürekli olarak;

- telemetri,
- sensör çıktıları,
- görev planları,
- çevresel veriler

ile güncellenir.

Bu yaklaşım sayesinde;

- performans analizleri,
- bakım planlaması,
- güvenlik testleri,
- operasyon simülasyonları

gerçek platform riske atılmadan gerçekleştirilebilir.

Özellikle büyük drone filolarında dijital ikiz teknolojileri operasyonel verimliliği önemli ölçüde artırmaktadır.

---

# Bulut Tabanlı Drone Yönetim Platformları

Yeni nesil İHA ekosistemleri yalnızca yer kontrol istasyonu ile sınırlı değildir.

Birçok üretici bulut tabanlı filo yönetim platformları sunmaktadır.

Bu platformlar sayesinde;

- görev planları merkezi olarak yönetilebilir,
- telemetri kayıtları depolanabilir,
- firmware güncellemeleri dağıtılabilir,
- cihaz envanteri takip edilebilir,
- bakım süreçleri planlanabilir.

Bulut altyapılarının sağladığı ölçeklenebilirlik önemli avantajlar sunsa da beraberinde yeni güvenlik gereksinimleri getirir.

Bunlar arasında;

- API güvenliği,
- kimlik federasyonu,
- erişim kontrolü,
- veri şifreleme,
- günlük kayıtlarının korunması,
- bulut yapılandırma güvenliği

ön plana çıkmaktadır.

Bu nedenle modern C2 güvenliği yalnızca RF haberleşmesini değil, bulut servislerini de kapsayan bütüncül bir yaklaşım gerektirir. 

# RF Spektrumunda Drone Haberleşmesi

Bir komuta-kontrol (Command and Control - C2) bağlantısının güvenilirliği yalnızca kullanılan protokole değil, haberleşmenin gerçekleştiği radyo frekansı ortamına da bağlıdır.

Kablosuz haberleşme doğası gereği paylaşımlı bir ortam üzerinde gerçekleşir. Aynı frekans bandını kullanan Wi-Fi erişim noktaları, Bluetooth cihazları, IoT sistemleri ve diğer RF kaynakları haberleşme kalitesini doğrudan etkileyebilir.

Bu nedenle profesyonel insansız hava aracı sistemlerinde yalnızca haberleşme protokolü değil, kullanılan RF katmanı da dikkatle tasarlanır.

Drone üreticileri görev gereksinimlerine göre farklı frekans bantlarını tercih eder.

| Frekans Bandı | Tipik Kullanım | Avantajlar | Dezavantajlar |
|---------------|----------------|------------|---------------|
| 433 MHz | Uzun menzil telemetri | Yüksek kapsama alanı | Düşük veri hızı |
| 868 / 915 MHz | LoRa tabanlı telemetri | Düşük güç tüketimi | Video aktarımı için uygun değildir |
| 2.4 GHz | Komuta-kontrol ve telemetri | Yaygın donanım desteği | Yoğun parazit ortamı |
| 5.8 GHz | HD video aktarımı | Daha yüksek bant genişliği | Daha kısa menzil |
| LTE / 5G | BVLOS operasyonları | Hücresel kapsama avantajı | Operatör altyapısına bağımlılık |

Her frekans bandı farklı avantajlar sunarken aynı zamanda farklı güvenlik gereksinimlerini de beraberinde getirir.

Örneğin 2.4 GHz bandı dünya genelinde en yoğun kullanılan ISM (Industrial, Scientific and Medical) bantlarından biridir.

Wi-Fi ağları, Bluetooth cihazları, kablosuz çevre birimleri ve IoT ürünlerinin önemli bir bölümü aynı frekans aralığında çalışmaktadır.

Bu durum özellikle yoğun şehir merkezlerinde elektromanyetik gürültünün artmasına neden olur.

Profesyonel platformlar bu problemi azaltabilmek amacıyla;

- Dinamik kanal seçimi (Dynamic Channel Selection)
- Frekans atlamalı yayılı spektrum (Frequency Hopping Spread Spectrum - FHSS)
- Adaptif veri oranı (Adaptive Data Rate)
- Otomatik güç kontrolü (Adaptive Power Control)

gibi mekanizmalar kullanır.

Bu teknolojiler haberleşmenin kesintisiz devam etmesini sağlamayı hedeflerken aynı zamanda parazit kaynaklarından kaçınmaya da yardımcı olur.

---

# Telemetri Verileri Neden Bu Kadar Kritiktir?

Bir drone uçuşunda operatörün ekranda gördüğü bilgiler yalnızca konum veya irtifa değildir.

Telemetri, hava aracının operasyonel durumunu gerçek zamanlı olarak yansıtan kapsamlı bir veri kümesidir.

Tipik bir telemetri akışı aşağıdaki bilgileri içerir.

- GPS koordinatları
- İrtifa
- Yer hızı
- Hava hızı
- Heading (Yön)
- Pitch / Roll / Yaw değerleri
- IMU sensör çıktıları
- Batarya voltajı
- Batarya sıcaklığı
- Motor RPM değerleri
- Uçuş modu
- Uydu sayısı
- Link Quality (LQ)
- RSSI
- Paket kayıp oranı
- Görev durumu
- Sensör sağlık bilgileri

Bu veriler yalnızca operatörün uçuşu izlemesini sağlamaz.

Aynı zamanda;

- Uçuş kayıtlarının oluşturulması,
- Arıza analizleri,
- Adli bilişim incelemeleri,
- Kaza araştırmaları,
- Emniyet değerlendirmeleri,
- Siber güvenlik analizleri

için de kritik öneme sahiptir.

Kurumsal İHA operasyonlarında telemetri kayıtları çoğu zaman merkezi log altyapılarında saklanır.

Böylece geçmiş uçuşlar geriye dönük olarak analiz edilebilir.

---

# Ground Control Station (GCS)

Ground Control Station (GCS), drone ekosisteminin en kritik bileşenlerinden biridir.

Operatör açısından bakıldığında yalnızca haritanın görüntülendiği bir yazılım gibi görünse de aslında uçuşun yönetildiği merkezdir.

Modern GCS yazılımları genellikle aşağıdaki yetenekleri sunar.

- Görev planlama
- Waypoint oluşturma
- Harita entegrasyonu
- Canlı telemetri
- Video görüntüleme
- Firmware güncelleme
- Parametre yönetimi
- Sensör kalibrasyonu
- Log analizi
- Fail-safe yapılandırmaları

Açık kaynak ekosisteminde yaygın olarak kullanılan yazılımlar arasında;

- Mission Planner
- QGroundControl
- MAVProxy
- UgCS

bulunmaktadır.

Ticari üreticiler ise kendi kapalı ekosistemlerini geliştirmektedir.

Örneğin DJI Pilot, DJI Fly veya DJI GS Pro gibi çözümler yalnızca ilgili platformlarla birlikte çalışmaktadır.

GCS yazılımları aynı zamanda güvenlik açısından da önemli sorumluluklar üstlenir.

Yetkisiz erişimlerin engellenmesi, kullanıcı doğrulaması, görev planlarının bütünlüğünün korunması ve güvenli haberleşme mekanizmalarının uygulanması doğrudan bu katmanda gerçekleştirilir. 

# Modern Drone Haberleşme Protokolleri

Drone ekosisteminde kullanılan komuta-kontrol protokolleri platformdan platforma farklılık gösterir. Bazı üreticiler tamamen kapalı (proprietary) haberleşme altyapıları geliştirirken, açık kaynak ekosisteminde standartlaşmış protokoller de yaygın olarak kullanılmaktadır.

Kullanılan protokol yalnızca veri iletim biçimini belirlemez; aynı zamanda güvenlik seviyesini, kimlik doğrulama yöntemlerini, hata toleransını ve sistemin genişletilebilirliğini de doğrudan etkiler.

En yaygın kullanılan protokoller aşağıdaki gibidir.

| Protokol | Kullanım Alanı | Yapı |
|----------|----------------|------|
| MAVLink | ArduPilot / PX4 | Açık kaynak |
| DJI OcuSync | DJI Platformları | Kapalı |
| DJI Lightbridge | Eski DJI sistemleri | Kapalı |
| CRSF (Crossfire) | FPV Sistemleri | Düşük gecikme |
| ELRS (ExpressLRS) | FPV Sistemleri | Açık kaynak |
| SBUS | RC Haberleşmesi | Seri protokol |

---

# MAVLink Protokolü

Açık kaynak drone ekosisteminde en yaygın kullanılan haberleşme protokolü MAVLink (Micro Air Vehicle Link)'tir.

MAVLink, ArduPilot ve PX4 tabanlı platformlarda yer kontrol istasyonu ile uçuş kontrolcüsü arasında veri alışverişini sağlayan hafif (lightweight) bir mesajlaşma protokolüdür.

Tasarlanma amacı düşük bant genişliğinde çalışan sistemlerde minimum gecikmeyle yüksek verim sağlamaktır.

MAVLink üzerinden çok sayıda farklı mesaj tipi taşınabilir.

Örneğin;

- GPS verileri
- IMU çıktıları
- Motor durumları
- Batarya bilgileri
- Waypoint görevleri
- Parametre güncellemeleri
- Sensör sağlık bilgileri
- Uçuş modu değişiklikleri
- Kamera kontrol komutları

tek tip mesaj yapısı kullanılarak iletilmektedir.

Mesaj yapısının standart olması sayesinde farklı üreticilerin geliştirdiği yazılımlar aynı platformla haberleşebilir.

Bu birlikte çalışabilirlik (interoperability), MAVLink'in en önemli avantajlarından biridir.

---

# MAVLink Mesaj Yapısı

Her MAVLink paketi belirli alanlardan oluşur.

Tipik bir mesaj aşağıdaki bilgileri içerir.

| Alan | Açıklama |
|------|----------|
| Header | Paket başlangıcı |
| Payload Length | Veri uzunluğu |
| Sequence Number | Paket sırası |
| System ID | Sistem kimliği |
| Component ID | Bileşen kimliği |
| Message ID | Mesaj tipi |
| Payload | Asıl veri |
| CRC | Bütünlük kontrolü |

Bu yapı sayesinde alıcı taraf yalnızca mesajın hangi sisteme ait olduğunu değil, hangi bileşenden geldiğini de anlayabilir.

Örneğin;

- Flight Controller
- GPS Modülü
- Kamera
- Gimbal
- Companion Computer

aynı haberleşme hattını paylaşabilir.

---

# MAVLink 1 ve MAVLink 2 Arasındaki Farklar

İlk sürüm olan MAVLink 1, düşük donanım gereksinimleri nedeniyle uzun yıllar boyunca yaygın olarak kullanılmıştır.

Ancak zaman içerisinde güvenlik açısından bazı eksiklikler ortaya çıkmıştır.

Bunun üzerine MAVLink 2 geliştirilmiştir.

Başlıca yenilikler şunlardır.

- Daha büyük mesaj kapasitesi
- Genişletilebilir mesaj alanları
- Daha güçlü CRC doğrulaması
- Paket imzalama (Message Signing)
- Gelişmiş uyumluluk mekanizmaları

Özellikle Message Signing özelliği, haberleşme güvenliği açısından önemli bir gelişme olarak kabul edilmektedir.

Bu özellik sayesinde mesajların yetkili bir kaynaktan geldiği doğrulanabilir ve iletim sırasında değiştirilmediği kontrol edilebilir.

Bu yaklaşım, haberleşmenin bütünlüğünü (Integrity) korumaya yönelik önemli bir güvenlik mekanizmasıdır.

---

# DJI OcuSync Teknolojisi

DJI platformlarında kullanılan OcuSync teknolojisi, üreticiye özgü kapalı bir haberleşme mimarisidir.

Standart Wi-Fi haberleşmesinden farklı olarak;

- düşük gecikme,
- yüksek çözünürlüklü video aktarımı,
- adaptif frekans seçimi,
- otomatik kanal optimizasyonu,
- gelişmiş hata düzeltme mekanizmaları

gibi özellikler sunmaktadır.

OcuSync haberleşmesi aynı anda hem komuta-kontrol trafiğini hem de yüksek çözünürlüklü video akışını taşıyabilir.

Sistem, bağlantı kalitesini sürekli analiz ederek uygun frekans kanalını dinamik olarak seçebilir.

Bu yaklaşım özellikle elektromanyetik gürültünün yoğun olduğu şehir ortamlarında bağlantı kararlılığını artırmayı amaçlar.

Üretici tarafından kullanılan protokol ayrıntıları kamuya açık olmadığından akademik çalışmalar genellikle RF davranışı ve trafik karakteristikleri üzerine yoğunlaşmaktadır.

---

# Flight Controller Neden Drone'un Beyni Olarak Tanımlanır?

Komuta-kontrol zincirinin merkezinde Flight Controller yer alır.

Flight Controller yalnızca gelen komutları ileten pasif bir bileşen değildir.

Aksine;

- sensör verilerini toplar,
- uçuş algoritmalarını çalıştırır,
- motor hızlarını hesaplar,
- denge kontrolünü gerçekleştirir,
- fail-safe mekanizmalarını yönetir,
- navigasyon hesaplamalarını yapar.

Modern Flight Controller sistemleri saniyede yüzlerce hatta binlerce hesaplama gerçekleştirebilir.

Bu hesaplamalar sırasında GPS, IMU, pusula, barometre ve diğer sensörlerden gelen veriler sürekli olarak birleştirilir.

Bu işleme Sensor Fusion adı verilir.

En yaygın kullanılan algoritmalar arasında;

- Extended Kalman Filter (EKF)
- Unscented Kalman Filter (UKF)
- Complementary Filter

bulunmaktadır.

Bu algoritmalar farklı sensörlerden gelen verileri karşılaştırarak hava aracının gerçek konumunu ve yönelimini mümkün olduğunca doğru biçimde tahmin etmeye çalışır.

Dolayısıyla güvenilir bir C2 sistemi yalnızca sağlam RF haberleşmesine değil, doğru çalışan sensör füzyonu ve uçuş kontrol algoritmalarına da bağlıdır. 

# Komuta-Kontrol Sistemlerinde Güvenlik Yaklaşımları

Komuta-kontrol (C2) altyapıları yalnızca veri ileten haberleşme kanalları değildir. Aynı zamanda operasyon boyunca üretilen her komutun, her telemetri paketinin ve her görev bilgisinin güvenli şekilde işlenmesini sağlayan kritik güven zincirinin temelini oluştururlar.

Modern drone platformlarında güvenlik yalnızca şifreleme ile sağlanmaz. Haberleşme mimarisi; kimlik doğrulama (Authentication), bütünlük (Integrity), gizlilik (Confidentiality) ve erişilebilirlik (Availability) ilkeleri dikkate alınarak tasarlanır.

Bu yaklaşım, klasik bilgi güvenliği prensiplerinin insansız hava aracı sistemlerine uygulanmış hâlidir.

---

# CIA Triadı Perspektifinden Drone C2 Güvenliği

Bilgi güvenliğinde yaygın olarak kullanılan CIA Triadı, drone haberleşme sistemlerinin değerlendirilmesinde de kullanılabilir.

| Güvenlik İlkesi | Drone C2 Karşılığı |
|-----------------|--------------------|
| Confidentiality | Haberleşme trafiğinin yetkisiz kişiler tarafından okunamaması |
| Integrity | Komutların ve telemetrinin değiştirilmediğinin doğrulanması |
| Availability | Haberleşmenin görev boyunca kesintisiz devam etmesi |

Bu üç prensipten herhangi birinin zayıflaması, uçuş güvenliğini doğrudan etkileyebilir.

Örneğin;

- Haberleşme gizliliğinin kaybolması operasyonel bilgilerin açığa çıkmasına,
- Veri bütünlüğünün bozulması yanlış kararların alınmasına,
- Haberleşmenin kesilmesi ise görevin yarıda kalmasına neden olabilir.

Bu nedenle modern C2 sistemleri, yalnızca yüksek veri hızına değil aynı zamanda güvenilir haberleşmeye odaklanmaktadır.

---

# Kimlik Doğrulama (Authentication)

Bir komutun drone tarafından uygulanabilmesi için öncelikle güvenilir bir kaynaktan geldiğinin doğrulanması gerekir.

Modern sistemlerde bu amaçla;

- Kriptografik anahtarlar,
- Dijital imzalar,
- Karşılıklı kimlik doğrulama,
- Güvenli oturum anahtarları

gibi mekanizmalar kullanılmaktadır.

Özellikle kurumsal platformlarda yalnızca doğru komutu göndermek yeterli değildir.

Komutu gönderen cihazın da güvenilir olduğunun doğrulanması gerekir.

Bu yaklaşım, Zero Trust mimarisinin temel prensiplerinden biriyle örtüşmektedir.

---

# Veri Bütünlüğü (Integrity)

Drone haberleşmesinde veri bütünlüğü, iletilen paketin gönderildiği andan alındığı ana kadar değiştirilmediğinin doğrulanmasını ifade eder.

Bu amaçla yaygın olarak;

- CRC (Cyclic Redundancy Check)
- Hash algoritmaları
- Paket imzalama
- Message Authentication Code (MAC)

gibi yöntemler kullanılmaktadır.

Bütünlük kontrolleri yalnızca saldırılara karşı değil, radyo haberleşmesinde oluşabilecek doğal iletim hatalarının tespit edilmesinde de önemli rol oynar.

---

# Haberleşme Gizliliği (Confidentiality)

Operasyon sırasında iletilen veriler çoğu zaman yalnızca uçuş komutlarından ibaret değildir.

Aynı bağlantı üzerinden;

- Canlı video akışı,
- Görev koordinatları,
- Sensör çıktıları,
- Operasyon planları,
- Harita verileri,
- Kamera yönelim bilgileri

de aktarılabilir.

Bu nedenle haberleşmenin gizliliğinin korunması kritik öneme sahiptir.

Modern platformlarda AES tabanlı şifreleme, güvenli oturum anahtarları ve üreticiye özgü kriptografik mekanizmalar bu amaçla kullanılmaktadır.

---

# Haberleşmenin Sürekliliği (Availability)

Bir komuta-kontrol sisteminin güvenli olması kadar erişilebilir olması da gerekir.

Haberleşme kesildiğinde;

- Drone otomatik eve dönüş (Return to Home),
- Havada bekleme (Loiter),
- Güvenli iniş,
- Önceden tanımlanmış görevin devam ettirilmesi

gibi fail-safe mekanizmalarını devreye alabilir.

Bu davranışlar platform üreticisi tarafından belirlenen güvenlik politikalarına göre değişebilir.

Kurumsal sistemlerde fail-safe senaryoları operasyon başlamadan önce ayrıntılı şekilde planlanır ve test edilir.

---

# Fail-Safe Mekanizmaları

Fail-safe, beklenmeyen durumlarda sistemin güvenli davranmasını sağlayan koruma mekanizmalarının genel adıdır.

Modern drone platformlarında yaygın olarak kullanılan fail-safe senaryoları şunlardır.

- Haberleşme bağlantısının kesilmesi
- Kritik batarya seviyesi
- GPS sinyalinin kaybolması
- Sensör arızaları
- Motor hataları
- Compass uyuşmazlıkları
- IMU kalibrasyon problemleri

Bu olaylardan biri gerçekleştiğinde uçuş kontrol yazılımı önceden tanımlanan güvenlik politikasını uygular.

Örneğin;

- Return to Home (RTH)
- Hover
- Controlled Landing
- Mission Abort

gibi davranışlar otomatik olarak gerçekleştirilebilir.

Bu mekanizmalar yalnızca operasyon güvenliği açısından değil, hava sahası emniyeti açısından da kritik öneme sahiptir.

---

# Redundancy (Yedeklilik)

Profesyonel insansız hava aracı platformlarında tek bir bileşene bağımlılık istenmez.

Bu nedenle kritik sistemler çoğu zaman yedekli olarak tasarlanır.

Örneğin;

- Çift IMU
- Çift GPS
- Çift pusula
- Çift batarya
- Çift haberleşme kanalı

gibi mimariler kullanılabilir.

Bir bileşende arıza meydana geldiğinde sistem otomatik olarak yedek bileşene geçebilir.

Bu yaklaşım özellikle endüstriyel, askeri ve kritik altyapı operasyonlarında uçuş güvenilirliğini önemli ölçüde artırmaktadır. 

----------------->>>> DEVAM EDECEK
