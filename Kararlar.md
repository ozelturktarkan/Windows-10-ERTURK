# Windows 10 ERTÜRK — r2 Mağazasız aday

Türkçe Windows 10 Pro 1909 x64, 18363.959. Hedef: 8 GB+ RAM ve SSD.
ALP ER TUNGA tercihleri temel alınır; 1607'ye özgü AppX onarımları aktarılmaz.

- Microsoft Store ve Store Purchase App kaldırılır. Hesap Makinesi, Fotoğraflar, Ses Kaydedici ve ortak AppX/framework/lisans altyapısı korunur.
- Fotoğraflar, Hesap Makinesi, Ses Kaydedici, klasik Paint, Not Defteri, WordPad, Media Player, Edge Legacy ve web görüntüleme altyapısı korunur. Paint 3D ayrı bir uygulamadır ve kaldırma listesindedir.
- OneDrive, gereksiz tüketici uygulamaları, Xbox kayıt arayüzleri ve Defender ALP profili gibi kaldırma listesindedir. Güvenlik duvarı/BFE/Güvenlik Merkezi korunur. Üçüncü taraf tarayıcı veya antivirüs eklenmez.
- Cortana kapalı; yerel arama, arama arayüzü ve WSearch korunur. Game DVR ilkesi ve kullanıcı kaydı kapalıdır; bütün yerel kayıt ikililerinin silindiği iddia edilmez.
- Otomatik Windows güncellemesi NoAutoUpdate=1; elle güncelleme ve bileşen yükleme hizmetleri korunur.
- DiagTrack kapalı; ALP gibi diğer günlük kullanım hizmetleri korunur. Güç planı, çekirdek sayısı, HPET, performans sayaçları, SysMain, bellek sıkıştırma ve sayfalama dosyası değiştirilmez.
- Görsel seçeneklerden yalnız yazı yumuşatma, masaüstü simge yazısı gölgesi, menü seçiminin solması ve pencere gölgesi açıktır. Diğer efektler ve saydamlık kapalıdır.
- Aynı bayrak imleci ve Alp Er Tunga arka planı. WallpaperStyle=2: Genişlet. İlk oturumdan sonra kullanıcı tercihleri korunur.
- Türkçe Q varsayılan; sonradan dil/klavye ekleme altyapısı, fontlar ve sürücüler topluca silinmez. Hyper-V isteğe bağlı durumuyla korunur.
- Üretim ISO'su yalnız Pro indeksini içerir. Disk silme, hesap/parola, otomatik oturum açma ve aktivasyon betiği yoktur. Yanıt dosyası yalnız herkese açık Pro kurulum anahtarını kullanır; lisans sağlamaz.

## Doğrulama sınırı
r1 kurulumu kullanıcı tarafından yapıldı; Store hata verdi ve kaldırılması istendi. r2 imaj uygulaması ve statik doğrulama tamamlandı; kullanıcı kurulumu sorunsuz tamamladığını bildirdi ve asistanın salt okunur kurulum kontrolleri geçti. Ayrıntılar ve üç Windows kurulum hata kaydı Kurulum-Kontrol.json içindedir. 1909 destek dışı bir tabandır; kaynakların açıklanması güvenlik veya uzun dönem kararlılık garantisi değildir.
