# Windows 10 ERTÜRK

**Türkçe Windows 10 Pro 1909 · 64 bit · r2 Mağazasız**

ERTÜRK, [HAKANLAR dizisinin](https://github.com/ozelturktarkan/Windows-10-11-HAKANLAR-Dizesi) 1909 tabanlı sürümüdür. Hedef donanım **8 GB ve üzeri RAM + SSD**; kurulum testi **4 GB RAM'li sanal makinede** yapıldı. Bu depo NTLite XML'lerini, kurulum betiklerini, kişiselleştirme dosyalarını, test kayıtlarını ve ISO hashlerini paylaşır.

## ISO indirme durumu

**[Windows 10 ERTÜRK.iso indir](https://archive.org/download/windows-10-erturk/Windows%2010%20ERT%C3%9CRK.iso)** · [Archive sayfası](https://archive.org/details/windows-10-erturk). Archive boyut, SHA-1 ve MD5 değerleri son r2 ISO ile eşleşti; indirme adresi HTTP üzerinden doğrulandı. Archive kopyasının tamamı yeniden indirilip SHA-256 hesaplanmadı. [Doğrulama kaydı](Archive-Dogrulama.json). GitHub'daki kaynak ZIP/TAR dosyaları Windows kurulum ISO'su değildir. [Küçük dosyalar ve kaynak paketi](https://github.com/ozelturktarkan/Windows-10-ERTURK/releases/tag/v1.0-r2).

| Özellik | Değer |
| --- | --- |
| Taban | Windows 10 Pro 1909, 18363.959 |
| Dil / mimari | Türkçe / x64 (64 bit) |
| Kurulum seçeneği | Yalnız Pro, indeks 1 |
| Revizyon | r2 — Mağazasız, 30 Eylül 2026 |
| ISO adı | Windows 10 ERTÜRK.iso |
| Boyut | 4.576.935.936 bayt; yaklaşık 4.26 GiB |
| Önyükleme | BIOS ve x64 EFI kayıtları |

## İmleç ve arka planı ayrı indirin

| Dosya | İndir | Kullanım |
| --- | --- | --- |
| Dalgalanan Türk bayrağı imleci | [turk.ani](https://github.com/ozelturktarkan/Windows-10-ERTURK/releases/download/v1.0-r2/turk.ani) | Fare > İşaretçiler > Normal Seçim > Gözat |
| ALP ER TUNGA ile ortak arka plan | [ERTURK.jpg](https://github.com/ozelturktarkan/Windows-10-ERTURK/releases/download/v1.0-r2/ERTURK.jpg) | Kişiselleştirme > Arka Plan; yerleşim: Genişlet |

Bunları kullanmak için Windows'u yeniden kurmanız veya NTLite edinmeniz gerekmez. [Dosya özetleri ve kullanım](assets/README.md).

<img src="assets/ERTURK.jpg" alt="Windows 10 ERTÜRK arka planı" width="720">

## İnceleyin, kendiniz hazırlayın

Uygun NTLite lisansıyla kendi Türkçe Windows 10 Pro 1909 x64 kaynağınız üzerinde yayımlanan XML'leri **betikler ve Medya-Eki ile birlikte** kullanabilirsiniz. [Yeniden üretim tarifi](YENIDEN-URETIM.md), kullanılan iki aşamayı açıklar: önce r1 tabanı, ardından Store ve Store Purchase App'i kaldıran r2 farkı.

[Birleşik XML](NTLite-ERTURK.xml) inceleme ve tek geçişli hazırlama için sunulur; temiz kaynakta tek geçiş yolu ayrıca denenmedi. XML tek başına tema ve ilk oturum ayarlarını içermez. Ayrı bir temiz ortamda uçtan uca yeniden üretim karşılaştırması yapılmadı; **bayt bayt aynı ISO/hash garantisi verilmez**.

Kaynak WIM 18363.959 yapısıdır; temiz kaynakta Pro indeksi 4, yayımlanan sonuçta 1'dir. Temiz ve işlenmiş WIM özetleri [Kaynak-Bilgisi.json](Kaynak-Bilgisi.json) içindedir. [Başlangıç 1909 ISO'sunun indirme adresi ve hesaplanan hashleri](KAYNAK-ISOLAR.md) eklendi. Boyut/SHA-1/MD5 Archive metaverisiyle, ISO içindeki WIM de üretim kaynağıyla eşleşti. **Resmî Microsoft referansı bulunamadığından Microsoft özgünlüğü bağımsız doğrulanmış değildir.**

## Neler değişti?

- **Microsoft Store ve Store Purchase App kaldırıldı.** r1'de Store açılış testi başarısız oldu; kullanıcı tercihiyle r2'den çıkarıldı. Bu tek test, bütün 1909 kurulumları hakkında sonuç sayılmaz.
- Hesap Makinesi, Fotoğraflar, Ses Kaydedici, klasik Paint, Not Defteri, WordPad, Windows Media Player, Edge Legacy ve temel yazdırma/ağ altyapısı korundu. Paint 3D ayrı uygulamadır ve kaldırıldı.
- OneDrive, Xbox kayıt arayüzleri ve seçilmiş yerleşik uygulamalar kaldırıldı. Tam bileşen listeleri [r1 uygulanan XML](NTLite-ERTURK-r1-Uygulanan.xml) ve [r2 uygulanan fark](NTLite-ERTURK-r2-Uygulanan-Fark.xml) içindedir.
- **Defender kaldırıldı; güvenlik duvarı korundu.** Üçüncü taraf antivirüs, Firefox veya yeni Edge gömülmedi. Test ekranında sonradan kurulmuş yeni Edge görülmesi ISO'da bulunduğu anlamına gelmez.
- Cortana kapalı; **yerel arama, arama arayüzü ve WSearch korunuyor**. Game DVR kapalı; bütün kayıt ikililerinin silindiği iddia edilmiyor.
- Otomatik Windows güncellemesi `NoAutoUpdate=1` ilkesiyle kapalı. Elle bakım/güncelleme ve bileşen yükleme altyapısı korundu; güncel güncellemelerin kullanılabilirliği test edilmiş sayılmaz.
- DiagTrack kapalı. SysMain, bellek sıkıştırması, sayfalama dosyası, güç planı ve işlemci/zamanlayıcı ayarları değiştirilmedi; HPET zorlaması veya performans sayaçlarını kapatma uygulanmadı.
- Görsel efektlerden yalnız **yazı yumuşatma, masaüstü simge yazısı gölgesi, menü seçiminin solması ve pencere gölgesi** açık. Diğer efektler ve saydamlık kapalı. [Görsel profil](Gorsel-Profil.json), ERTÜRK/ULUTÜRK için seçilen ortak tercihi kaydeder.
- Arka plan **Genişlet**, normal imleç Türk bayrağı. İlk oturumdan sonraki kullanıcı tercihleri korunur.
- Türkçe Q varsayılan; dil/klavye ekleme, sürücüler ve Hyper-V'nin isteğe bağlı altyapısı korunur. Hyper-V zorunlu olarak açılmaz.

[Ayrıntılı kararlar](Kararlar.md) · [Kurulum betikleri](Medya-Eki/sources/%24OEM%24/%24%24/Setup/ERTURK)

## Test sonuçları ve bilinen sınırlar

| Kontrol | Sonuç / kanıt |
| --- | --- |
| r2 kurulumu ve masaüstü | Kullanıcı kurulumu tamamladığını ve sorun görmediğini bildirdi; masaüstü gözlendi |
| Profil, ilk oturum, Store'un yokluğu, korunan uygulama kayıtları, dosya hashleri | [Kurulum-Kontrol.json](Kurulum-Kontrol.json): salt okunur kontroller geçti |
| Dört efektli profil | İlk oturum doğrulamasındaki 22 karşılaştırma geçti; `true`, beklenen değere uyulduğunu gösterir, bütün efektlerin açık olduğunu değil |
| İmaj ve ISO içeriği, BIOS/x64 EFI | [WIM-Dogrulama.json](WIM-Dogrulama.json) ve [Icerik-dogrulama.json](Icerik-dogrulama.json) |
| Ses | VM ses ayarı ve kullanıcının Windows sorun gidericisi müdahalesinden sonra kullanıcı ses geldiğini doğruladı; [Ses-Testi.json](Ses-Testi.json) |
| Fiziksel donanım, uzun dönem yük/kararlılık, bütün uygulamaların canlı açılışı | Kapsamlı test yapılmadı |

Ses araştırmasında VM'nin AC97 aygıtı ve kapalı ses çıkışı görüldü. VM, Intel HD Audio/STAC9221 ve açık çıkışa geçirildi. Bu bir ISO sürücü değişikliği değildir; sorun giderici de kullanıldığından tek bir kök neden kesinleştirilmedi.

**Windows kurulum günlüklerinde üç hata satırı var:** IBS `0x00000490`, CBS `0x80070002`, OOBE LocalUser Plugin `0x80070490`. Masaüstüne ulaşılması ve ERTÜRK betiklerinin tamamlanması doğrulandı; bu satırların kök nedenleri belirlenmedi. Günlüklerin tamamen hatasız olduğu iddia edilmez. Çalışan VM diskinin salt okunur kontrolü anlık hizmet çalışma durumunu veya duyulan sesi kanıtlamaz.

Üretim anındaki raporlarda görülen “kurulum bekleniyor” durumu tarihîdir; sonraki sonuç [Kurulum-Kontrol.json](Kurulum-Kontrol.json) içindedir. Edge Legacy eski bir tarayıcıdır; güncel sitelerle uyumluluk garantisi yoktur. Doğrulanmamış RAM/FPS veya güvenlik iddiası sunulmaz.

## ISO bütünlüğünü doğrulayın

```text
SHA-256  5eb35124b8847124ee308326910c1868b4f28cc7e35466a6947279bcee6821d4
SHA-1    6f8de4c81fb3c740d52ec4163a9cfbbeacfe8b7a
MD5      015044a550bde39c1f906ae7d7ed6773
```

```powershell
Get-FileHash -LiteralPath '.\Windows 10 ERTÜRK.iso' -Algorithm SHA256
```

Sonucu [HASHES.txt](HASHES.txt) ile karşılaştırın. SHA-256 tercih edin; hash eşleşmesi dosyanın güvenli olduğunun kanıtı değildir. Küçük dosyaların özetleri [DOSYALAR-SHA256.json](DOSYALAR-SHA256.json) içindedir; kaynak ZIP'in kendi SHA-256 dosyası sürüm sayfasındadır.

## Lisans ve geri bildirim

Windows 10 Pro 1909 destek dışı bir tabandır. Bu çalışma Microsoft'un resmî sürümü değildir; güncel güvenlik veya her donanımda sorunsuzluk garantisi verilmez. Windows lisansı gerekir. Etkinleştirme atlatma aracı, kişisel ürün anahtarı, hesap/parola veya disk silme betiği yoktur. Yanıt dosyasındaki genel Pro kurulum anahtarı lisans sağlamaz. [Lisans ve varlık notları](LISANS-NOTU.md).

Sorunları sürüm, donanım ve tekrar etme adımlarıyla [Issues](https://github.com/ozelturktarkan/Windows-10-ERTURK/issues) bölümüne yazabilirsiniz. Parola, kişisel ürün anahtarı veya kişisel dosya paylaşmayın.
