# Drone C2 Sinyalleri:

## 1. Özet
Drone komuta-kontrol (C2) sinyali, insansız hava aracı (İHA) ile operatörü arasındaki iletişimi sağlayan radyo frekansı (RF) sinyalleridir. Bu sinyaller, drone yönlendirme, telemetri verilerinin iletilmesi ve video akışını içerir. Farklı drone sistemleri, farklı frekans bantları ve protokoller kullanabilir. Amaçlar arasında operasyonel farkındalık, güvenlik, adli inceleme ve savunma yer alır.

## 2. Frekanslar ve Protokoller
- **2.4 GHz / 5.8 GHz**: Tüketici ve ticari drone'larda yaygın uplink/downlink bantları.
- **433 MHz / 900 MHz / LoRa**: Uzun menzil telemetri ve uzaktan kontrol için.
- **Proprietary protokoller (DJI OcuSync / Lightbridge)**: Özel şifreleme ve kimlik doğrulama içerir.
- **MAVLink / ArduPilot / PX4**: Açık kaynak uçuş yazılımları tarafından kullanılır; MAVLink2 ile paket imzalama ve güvenli telemetri mümkündür.

## 3. Potansiyel Zaafiyetler
- Şifreleme veya kimlik doğrulama eksikliği (özellikle MAVLink 1.0).
- Yan kanal ve fiziksel erişim zafiyetleri (debug portlar, firmware ekstraları).
- Uygulama/SDK/telemetri sızıntıları.
- GPS spoofing ve jamming saldırıları.
- Tedarik zinciri ve firmware güncelleme açıkları.

## 4. Savunma ve Tespit Yöntemleri
### 4.1 RF Spektrum Analizi
SDR ve spektrum analiz cihazları ile bant taraması yaparak anormal sinyaller tespit edilir.

### 4.2 Akustik ve Radar Algılama
Radar ve akustik sensörler ile drone'ların fiziksel varlığı belirlenebilir.

### 4.3 Telemetri Güvenliği
MAVLink2 paket imzalama ve şifreleme ile telemetri güvenliği sağlanabilir.

### 4.4 Operasyonel Önlemler
Geofencing, no-fly zone ve SHGM kayıt/izin süreçleri takip edilmelidir.

### 4.5 Yasal Yetki
Jammer veya frekans bozucular izinsiz kullanılamaz; yetkili otoritelerle koordinasyon şarttır.

## 5. AR-GE / Laboratuvar Çalışmaları
- SHGM ve BTK’dan gerekli izinleri alın.
- Kapalı ve izole test alanları oluşturun.
- Sadece tespit ve analiz yapılmalı; istismar veya müdahale yasadışıdır.
- Donanım/Yazılım: SDR, spektrum analiz cihazları, tersine mühendislik yazılımları.
- Elde edilen veriler akademik veya endüstri raporlarında paylaşılabilir.

## 6. Yasal Çerçeve (Türkiye)
- **TCK**: Haberleşmenin gizliliğini ihlal suçtur.
- **SHGM**: 500g üzeri drone uçuşlarında kayıt ve izin zorunlu.
- **BTK**: Frekans tahsisi ve geçici kullanım düzenlenir.
- **Jammer/karıştırıcı cihazlar**: İzinsiz kullanımı yasak.

## 7. Kurumsal Savunma Önerileri
- Firmware ve uygulamaları güncel tutun.
- Kritik tesislerde uçuş planı ve fiziksel kontrol mekanizmaları kurun.
- Yetkisiz drone tespitinde güvenlik ve otoritelerle koordinasyon, adli delil toplama.
- Personel eğitimleri: drone tehditleri ve yetkili prosedürler konusunda düzenli eğitimler.

## 8. Kaynaklar
- TCK Haberleşmenin Gizliliği (Avukat Baran Doğan)
- SHGM SHT-İHA ve kayıt talimatları (iha.shgm.gov.tr)
- BTK Telsiz ve frekans düzenlemeleri
- MAVLink2 signing (ArduPilot / Mission Planner)
- DJI güvenlik analizleri (NDSS, arXiv)
- Dedrone, DroneShield (C-UAS tespit sistemleri)
