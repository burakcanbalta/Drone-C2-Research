# Drone C2 Sinyalleri:

![Ekran görüntüsü 2025-08-16 150957](https://github.com/user-attachments/assets/f59d46aa-fdd7-432c-85f2-34757ebe6eb9)

## 1. Özet
Drone komuta-kontrol (C2) sinyali, insansız hava aracı (İHA) ile operatörü arasındaki iletişimi sağlayan radyo frekansı (RF) sinyalleridir. Bu sinyaller, drone yönlendirme, telemetri verilerinin iletilmesi ve video akışını içerir. Amaçlar arasında operasyonel farkındalık, güvenlik, adli inceleme ve savunma yer alır.

## 2. Ne İşe Yarar?
- Drone uçuşlarını yönetir ve kontrol eder.
- Telemetri ve sensör verilerini operatöre iletir.
- Video ve multimedya akışını sağlar.
- Kritik görevlerde operasyonel kontrol sağlar.
- Operatör ile drone arasındaki iletişimi güvenli ve sürekli tutar.

## 3. Frekanslar ve Protokoller
- **2.4 GHz / 5.8 GHz**: Yaygın uplink/downlink bantları.
- **433 MHz / 900 MHz / LoRa**: Uzun menzil telemetri ve kontrol için.
- **Proprietary protokoller (DJI OcuSync / Lightbridge)**: Özel şifreleme ve kimlik doğrulama içerir.
- **MAVLink / ArduPilot / PX4**: Açık kaynak yazılımlar; MAVLink2 ile paket imzalama ve güvenli telemetri.

## 4. Potansiyel Zaafiyetler ve Nasıl Sömürülür (Araştırma Perspektifi)
- **Şifreleme/Kimlik Doğrulama Eksikliği**: MAVLink 1.0 paketleri şifrelenmemiştir, sniffing ile paketler analiz edilebilir.
- **Yan Kanal ve Fiziksel Erişim**: Debug portları veya firmware ekstraları tersine mühendislik ile veri açığa çıkarabilir.
- **Uygulama/SDK/Telemetri Sızıntıları**: Mobil uygulamalar veya cloud servisleri üzerinden operasyonel bilgi toplanabilir.
- **GPS Spoofing / Jamming**: Konum doğrulama eksikliği drone'un yönlendirmesini bozabilir.
- **Firmware Güncelleme ve Tedarik Zinciri Açıkları**: Manipüle edilmiş firmware veya update paketleri laboratuvar ortamında analiz edilebilir.

## 5. Savunma ve Tespit Yöntemleri
- **RF Spektrum Analizi**: SDR ve spektrum analiz cihazları ile bant taraması.
- **Akustik ve Radar Algılama**: Drone fiziksel varlığı tespiti.
- **Telemetri Güvenliği**: MAVLink2 paket imzalama ve şifreleme.
- **Operasyonel Önlemler**: Geofencing, no-fly zone, SHGM izin süreçleri.
- **Yasal Yetki**: Jammer veya frekans bozucular izinsiz kullanılamaz.

## 6. AR-GE / Laboratuvar Çalışmaları
- SHGM ve BTK izinleri alın.
- Kapalı ve izole test alanları oluşturun.
- Sadece tespit ve analiz; istismar yasadışıdır.
- Araçlar: SDR, spektrum analiz cihazları, tersine mühendislik yazılımları.
- Bulgular akademik veya endüstri raporlarında paylaşılabilir.

## 7. Yasal Çerçeve (Türkiye)
- **TCK**: Haberleşmenin gizliliğini ihlal suçtur.
- **SHGM**: 500g üzeri drone uçuşları kayıt ve izin zorunlu.
- **BTK**: Frekans tahsisi ve geçici kullanım düzenlenir.
- **Jammer/karıştırıcılar**: İzinsiz kullanılamaz.

## 8. Kurumsal Savunma Önerileri
- Firmware ve uygulamaları güncel tutun.
- Kritik tesislerde uçuş planı ve fiziksel kontrol mekanizmaları oluşturun.
- Yetkisiz drone tespitinde güvenlik ve otoritelerle koordinasyon, adli delil toplama.
- Personel eğitimleri: drone tehditleri ve yetkili prosedürler.

## 9. Kaynaklar
- TCK Haberleşmenin Gizliliği (Avukat Baran Doğan)
- SHGM SHT-İHA ve kayıt talimatları (iha.shgm.gov.tr)
- BTK Telsiz ve frekans düzenlemeleri
- MAVLink2 signing (ArduPilot / Mission Planner)
- DJI güvenlik analizleri (NDSS, arXiv)
- Dedrone, DroneShield (C-UAS tespit sistemleri)
