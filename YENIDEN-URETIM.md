# ERTÜRK r2 yeniden üretim tarifi

Bu tarif kurulum medyası hazırlamak içindir; betikleri günlük kullandığınız Windows'ta doğrudan çalıştırmayın. XML tek başına ERTÜRK'ün tamamını üretmez. ISO, test sanal makinesinin diskinden yakalanmadı; hazırlanmış Windows kaynağı ile Medya-Eki birleştirildi.

## Kaynak ve araçlar

- Türkçe Windows 10 Pro 1909 x64, **18363.959** kaynağı. Başlangıç çoklu sürüm WIM'inde Pro indeksi 4'tür; kendi kaynağınızda adı/mimariyi doğrulayın, indeks numarasına körlemesine güvenmeyin.
- Kayıtlı temiz `install.wim`: 4.390.834.000 bayt, SHA-256 `d100034418028a3d6ddd01aacfd90fe5a1ae1253381b53062b8557ea7f13a1e9`. Başlangıç ISO'sunun adresi ve hash'i ayrıca doğrulanmadı.
- Üretimde **NTLite 2026.09.12209.0** kullanıldı; ücretli seçenekler uygun lisans gerektirir. NTLite programı/lisansı depoda yoktur.
- ISO oluşturmak için Python 3.11+ ve `requirements.txt` içindeki **pycdlib 1.14.0**.
- Temiz kaynak kopyası ve çıktı ISO'su için yeterli boş alan; ayrı çıktı dizini kullanın.

## Uygulanan iki aşama

1. Temiz medyayı ayrı çalışma klasörüne açın; Pro x64 1909 imajını NTLite'a yükleyin.
2. `NTLite-ERTURK-r1-Uygulanan.xml` ön ayarını içe aktarın. Bileşen seçimlerini gözden geçirip uygulayın ve yalnız Pro içeren WIM olarak kaydedin. r1'de Store bulunuyordu.
3. Kaydedilmiş Pro imajına `NTLite-ERTURK-r2-Uygulanan-Fark.xml` dosyasını uygulayın. Bu fark Microsoft.WindowsStore ve Microsoft.StorePurchaseApp'i kaldırır. Kaydedip imajı boşaltın.
4. Çıktıda `sources/install.wim` tek Pro indeksini (1) içermeli. Kurulum medyasının `boot`, `efi`, `sources/boot.wim` ve `sources/sxs` gibi kalan dosyalarını koruyun.

`NTLite-ERTURK-r2-Fark.xml` istenen r2 farkını, `NTLite-ERTURK.xml` birleşik hedefi gösterir. Birleşik dosyayla temiz kaynakta tek geçiş ayrıca denenmedi; yayımlanan üretim kanıtı yukarıdaki iki aşamaya aittir. Diğer sürümlere ait XML veya 1607 AppX onarımlarını bu tarife eklemeyin.

## Medya eki ve ISO

Depo dizininde PowerShell açın. Aşağıdaki D: yolları örnektir; kendi çalışma ve çıktı dizinlerinizi yazın. Çıktı klasörünü önceden oluşturun.

```powershell
py -3 -m pip install -r requirements.txt
py -3 tools/Build-ISO.py --source "D:\ERTURK-HAZIR-MEDYA" --overlay "Medya-Eki" --output "D:\ERTURK-CIKTI\Windows 10 ERTÜRK.iso" --report "D:\ERTURK-CIKTI\ISO-Uretim.json"
```

`Build-ISO.py` mevcut çıktı ISO'sunu üzerine yazmaktan korur; kaynak medyayı değiştirmez. Medya-Eki içindeki `autounattend.xml`, OEM dosyaları, ilk oturum betikleri, tema, imleç ve arka planı ekler. Kaynaktaki eski OEM/yanıt dosyası bu medya ekiyle değiştirilir; başka özelleştirmeler içeren kaynak kullanmayın. BIOS ve x64 EFI kayıtlarını üretir, medya eki baytlarını kontrol eder ve ISO SHA-256/SHA-1/MD5 özetlerini yazar.

Yanıt dosyası Türkçe klavye/dil ve kurulum betiklerini ayarlar. Herkese açık Pro kurulum anahtarı kullanılır; kişisel lisans değildir ve etkinleştirme sağlamaz. Disk seçimi ve hesap oluşturma kullanıcıya aittir.

## Doğrulama sınırı

Yayımlanan işlenmiş WIM'in SHA-256 değeri `efcb6bbc64c27e5f029c6ad3ef0b4e990f627e51c8b0ebf768879053e786c285`'tir. `WIM-Dogrulama.json`, **bu WIM üzerinde üretim sırasında yapılan çevrimdışı incelemenin kaydıdır**; kendi WIM'inizi otomatik inceleyen bir araç değildir.

Hazırladığınız WIM bu kayıtla aynı hash'e sahipse ek denetim:

```powershell
py -3 tools/Verify-ISO.py --report "D:\ERTURK-CIKTI\ISO-Uretim.json" --wim-report "WIM-Dogrulama.json"
```

Bu araç ISO içindeki WIM hash'ini, önyükleme ve kurulum yanıtı koşullarını raporla karşılaştırır. Kendi WIM hash'iniz farklıysa yayımlanan WIM raporu size ait kanıt sayılmaz; bu komut eşleşme kontrolünde durur. Başarılı görünmesi için rapordaki hash'i veya kontrolleri değiştirmeyin. İmajın bileşen/uygulama/sürücü durumunu ayrıca inceleyin ve yeni ISO ile temiz kurulum sınaması yapın.

Üretim aracı kurulum yapmaz; rapordaki bekleyen kurulum durumu ancak gerçek sınamadan sonra ayrı bir test kaydıyla tamamlanır. Ses, arama, temel uygulamalar, yeniden başlatma ve görsel profil yeni kurulumda kontrol edilmelidir. Sanal testler 4 GB RAM ile yapıldı; fiziksel donanım sürücü uyumu ayrıca değerlendirilmelidir.

NTLite sürümü, kaynak, sıkıştırma ve zaman damgaları farklı olabilir. Başka bir temiz ortamda aynı ISO hash'ini ürettiğimiz doğrulanmadı; birebir yeniden üretim garantisi verilmez. Hash eşleşmesi de güvenlik sertifikası değildir.
