# Renkli Küp Ayıran Robot Kol (v1)

Üç kişilik öğrenci projesi: kamerayla renkli küpleri algılayıp ayıran 4 eksenli masaüstü robot kol.

## Ekip

| Kişi | Bölüm | Sorumluluklar |
|---|---|---|
| Salih | Makine müh. | Kol geometrisi ve CAD, tork hesabı, servo seçimi, 3D baskı ve montaj, tutucu, kamera standı, ileri kinematik denklemleri |
| Burak | Elektrik-elektronik müh. | Güç kaynağı, PCA9685 ve servo bağlantıları, kablolama, acil stop, devre şeması, ölçümler, aydınlatma, parça siparişi |
| Ali | Bilgisayar müh. | Arduino firmware, seri protokol, PC arayüzü, ters kinematik, OpenCV, ana kontrol döngüsü, repo sahibi |

## Teknik özet (v1)

- 4 eksen + tutucu: taban, omuz, dirsek, bilek, tutucu
- Erişim ~28 cm, yük 50 g'a kadar
- Servolar: omuz DS3218 (20 kg·cm); taban, dirsek, bilek MG996R; tutucu MG90S
- Arduino Uno + PCA9685, ayrı 5-6 V en az 10 A adaptör, GND'ler ortak
- Laptopta Python (OpenCV, numpy, pyserial); Arduino'ya USB seri ile açı komutu
- Örnek protokol: PC `J,90,45,120,90,30\n` gönderir, Arduino hareket bitince `OK` döner; ayrıca `HOME` ve `STOP`
- Gövde: PLA 3D baskı (okul/arkadaş yazıcısı), MDF taban, döner tabla rulmanı, 608ZZ rulmanlar
- Kapsam dışı (v2): step motor, enkoder, ROS, 6 eksen

## Başarı kriterleri

- 30 denemede en az 24 doğru ayırma
- Konum hatası ortalama 1 cm altı
- Bir döngü 20 saniyenin altında

## Takvim

2 Kasım 2026 - 10 Ocak 2027, kişi başı haftada 5-6 saat.

| Hafta | İş | Kontrol noktası |
|---|---|---|
| H1 | Kuruluş, servo seçimi, sipariş | |
| H2 | Tek eklem testi | KT1 |
| H3-4 | Kol CAD + montaj, öğret-oynat modu | KT2 |
| H5-6 | Kinematik ve doğruluk testi | KT3 |
| H7 | Görüntü işleme + kalibrasyon | KT4 |
| H8-9 | Entegrasyon ve güvenilirlik testi | KT5 |
| H10 | Demo videosu, rapor, README | |

Ayrıntılı plan ve görev listesi: https://claude.ai/artifact/ECaoGZDTK6MVf8ML1G625X

## Klasör kuralları

- `firmware/`: Arduino kodu
- `pc/`: Python kodu (kontrol arayüzü, kinematik, görüntü işleme, `main.py`)
- `cad/`: STL ve STEP dışa aktarımları, Onshape/Fusion linkleri, teknik çizim PDF'leri
- `docs/`: hesaplar (tork, güç bütçesi), protokol, devre şeması, ölçüm/test tabloları, toplantı notları, fotoğraflar

## Çalışma şekli

- Biri bitirdiği görevin dosyasını attığında: dosyayı anlamlı bir isimle doğru klasöre koy, gerekirse kısa bir açıklama (`.md`) ekle, Türkçe ve açıklayıcı bir commit mesajı yaz, push'la.
- Commit mesajı formatı: `[alan] kısa açıklama (Hn)`. Örnek: `[cad] omuz eklemi v1 STL (H2)`
- Büyük ikili dosyaları (video, ham CAD) repoya koymadan önce sor.
- Yanıtları Türkçe ver.
