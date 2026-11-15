<p align="center"><img src="logo.png" width="96" alt="YKT Disk Yöneticisi"></p>

# YKT Disk Yöneticisi

Windows ve Linux için disk bölümü yöneticisi. Bölümleri oluşturur, siler, biçimlendirir, yeniden boyutlandırır,
taşır, böler, birleştirir ve klonlar. Windows'tan Linux (ext4) bölümlerini de yönetebilir.

**Yayımcı:** YKTera Tech · **Güncel sürüm:** 1.0.0 · **Diller:** Türkçe, English

> **Önemli:** Disk işlemleri yanlış kullanıldığında veri kaybına yol açabilir. Bölüm tablosunu değiştiren bir
> işlemden önce önemli verilerinizi mutlaka yedekleyin. Programı ilk kez deniyorsanız önemli veri içermeyen bir
> USB bellekte deneyin.

## İndir

| Sistem | Dosya | Nasıl kurulur |
|---|---|---|
| Windows 10 / 11 | [YKTDiskYoneticisi-Setup.exe](https://github.com/ecankinsundev/YKT-DiskYoneticisi-App/releases/latest/download/YKTDiskYoneticisi-Setup.exe) | Çift tıklayın. Yönetici izni istemeden kurar, masaüstü ve Başlat menüsü kısayolu ekler. |
| Linux | [Linux kurulum paketi](https://github.com/ecankinsundev/YKT-DiskYoneticisi-App/releases/latest) (`…-linux-kurulum.sh`) | `sudo sh YKTDiskYoneticisi-1.0.0-linux-kurulum.sh` — `python3` ve `python3-tk` gerekir. |

Tüm sürümler: [Releases](https://github.com/ecankinsundev/YKT-DiskYoneticisi-App/releases)

**Windows "bilinmeyen yayımcı" uyarısı:** Kurulum dosyası henüz dijital olarak imzalı değildir. Windows SmartScreen
uyarı gösterirse **Ek bilgi → Yine de çalıştır** deyin. İndirdiğiniz dosyanın bozulmadığını her sürümdeki
`SHA256SUMS.txt` ile doğrulayabilirsiniz.

## Nasıl kullanılır

1. **Programı açın.** Windows yönetici onayı ister; onaylamazsanız diskler yalnızca görüntülenir.
2. **Bir disk, bölüm ya da ayrılmamış alan seçin.** Üstteki listeden ya da alttaki disk haritasından tıklayın.
   Soldaki panelde o öğeyle yapılabilecek işlemler listelenir. Soluk görünen bir işleme tıklarsanız neden
   kullanılamadığını söyler.
3. **İşlemi seçin ve ayarlayın.** İşlem hemen uygulanmaz; **Bekleyen işlemler** listesine eklenir ve disk
   haritasında önizlenir. İstediğiniz kadar işlemi sıraya koyabilirsiniz.
4. **Uygula'ya basın.** Yapılacak işlemler listelenir; veri kaybı riski olanlar ayrıca işaretlenir ve onayınız
   istenir. Vazgeçerseniz **Geri al** ya da **Tümünü at** ile sıradakileri silebilirsiniz.
5. **Bitene kadar bilgisayarı kapatmayın.** İlerleme ve ayrıntılı günlük ekranda görünür.

Tema (koyu / açık) ve dil (TR / EN) araç çubuğundaki düğmelerden değiştirilir.

## Özellikler

### Bölüm işlemleri
- Oluştur, sil, biçimlendir (NTFS, FAT32, exFAT, ReFS; Linux'ta ext2/3/4, btrfs, xfs, swap)
- Yeniden boyutlandır ve taşı: sürükleyerek ya da **Tüm kullanılabilir alanı kullan** seçeneğiyle
- Böl ve birleştir: komşu ayrılmamış alanı ekleme ya da iki bölümü birleştirme (dosyalar kopyalanarak)
- Etiket ve sürücü harfi değiştir, gizle / göster, etkin (önyüklenebilir) yap
- Dosya sistemini denetle ve onar

### Disk işlemleri
- MBR ↔ GPT dönüştürme, diski başlatma, tüm bölümleri silme
- Disk ve bölüm klonlama (sektör sektör)
- Verileri kalıcı silme: sıfır, rastgele, DoD 3 geçiş, 7 geçiş
- Çevrimiçi / çevrimdışı ve salt okunur ayarı (Windows)

### Windows'tan Linux bölümleri
- Linux bölümlerini tanır: tür, dosya sistemi (ext2/3/4, btrfs, xfs, swap, LUKS, LVM), etiket, kullanılan alan
- ext2/3/4 bölümlerini **büyütür, küçültür, böler, taşır**; denetler, etiketler, ext4 olarak biçimlendirir
- Bu işlemler, kurulumla gelen küçük ve yalıtılmış bir Linux'ta Linux'un kendi araçlarıyla (`e2fsck`,
  `resize2fs`) yapılır. Bu Linux yalnızca işlem yapılan bölümü görür ve ağ erişimi yoktur.
- İşlemden önce Linux tamamen kapatılmış olmalıdır (hazırda bekletme değil); değilse program işlemi reddeder.

### Araçlar
- Yüzey testi (salt okunur), SMART sağlık bilgisi, 4K hizalama denetimi
- Kayıp bölüm arama ve geri yükleme (deneysel)
- Alan analizi: klasör boyutları ve en büyük 100 dosya

### Güvenlik önlemleri
- İşlemler önce sıraya alınır; **Uygula** denene kadar diske yazılmaz.
- Sistem ve önyükleme bölümleri silinemez, biçimlendirilemez, üzerine klonlanamaz.
- Bölüm taşıma sırasında veri bayt bayt doğrulanır; işlem yarıda kalırsa (ör. elektrik kesintisi) program
  açılışta kaldığı yerden sürdürmeyi önerir.

## Güncelleme

Program açılışta yeni sürüm olup olmadığına bakar; elle denetlemek için araç çubuğundaki **Güncelleme denetle**
düğmesini kullanın. Yeni sürüm varsa kurulu sürümünüzden sonraki her sürümün notları gösterilir.
**Şimdi güncelle** dosyayı indirir, SHA-256 özetini doğrular ve programı yeniler.

Gömülü Linux araçlarının değiştiği sürümlerde (sürüm notlarında belirtilir) güncelleme yerine yeni
`YKTDiskYoneticisi-Setup.exe` dosyasını indirip mevcut kurulumun üzerine kurun.

## Kaldırma

- **Windows:** Ayarlar → Uygulamalar → YKT Disk Yöneticisi → Kaldır. Ayarlarınız korunur.
- **Linux:** `sudo /opt/ykt-disk-yoneticisi/kaldir.sh`

## Bilinen sınırlar

- Klonlama birebir kopyadır: hedef disk ya da bölüm en az kaynak kadar büyük olmalıdır.
- Windows'ta kullanımdaki Windows bölümlerinin (NTFS vb.) başlangıcı taşınamaz; yalnızca sondan küçültülüp
  genişletilebilir. Linux bölümleri taşınabilir.
- Windows'ta btrfs ve xfs bölümleri taşınıp büyütülebilir, ancak dosya sistemleri Linux'ta büyütülmelidir.
- Windows, 32 GB'tan büyük bölümleri FAT32 olarak biçimlendiremez.
- Dinamik disk, BitLocker yönetimi ve önyüklenebilir kurtarma ortamı oluşturma yoktur.

## Sorun bildirme

Bir hata bulursanız ya da öneriniz varsa [Issues](https://github.com/ecankinsundev/YKT-DiskYoneticisi-App/issues) sayfasından yazın. Mümkünse
program sürümünü, işletim sisteminizi ve işlem günlüğündeki son satırları ekleyin.

## Üçüncü taraf yazılımlar

Windows kurulumundaki `linuxvm` klasörü şu özgür yazılımları içerir (GPL-2.0 ve uyumlu lisanslar); kaynak kodları
kendi sitelerinden edinilebilir:

| Yazılım | Kaynak |
|---|---|
| QEMU | <https://www.qemu.org/> (Windows derlemesi: <https://qemu.weilnetz.de/>) |
| Linux çekirdeği, BusyBox, musl (Alpine Linux derlemesi) | <https://alpinelinux.org/> · <https://git.alpinelinux.org/aports> |
| e2fsprogs | <https://e2fsprogs.sourceforge.net/> |

---

# Sürüm notları

Her yeni sürümde bu bölüm kendiliğinden güncellenir. En yeni sürüm en üsttedir.

## Sürüm 1.0.0 — 2026-11-15
İlk sürüm.

### Bölüm ve disk işlemleri
- Disk haritası ve bölüm listesi (GPT / MBR); Windows ve Linux'ta çalışır.
- Bekleyen işlem kuyruğu: işlemler önizlenir, **Uygula** ile gerçekleştirilir; geri al / tümünü at.
- Bölüm: oluştur, sil, biçimlendir, yeniden boyutlandır, taşı, böl, birleştir, etiket ve sürücü harfi değiştir,
  gizle / göster, etkin yap; Linux'ta bağla / ayır.
- Disk: MBR ↔ GPT dönüştürme, başlatma, tüm bölümleri silme, çevrimiçi / çevrimdışı.
- Dosya sistemi dönüştürme: FAT32 → NTFS (Windows), ext2/ext3 → ext4 (Linux).
- Disk ve bölüm klonlama (sektör sektör); verileri kalıcı silme (sıfır, rastgele, DoD 3 geçiş, 7 geçiş).

### Windows'tan Linux bölümleri
- Linux bölümlerini tanır: tür, dosya sistemi (ext2/3/4, btrfs, xfs, swap, LUKS, LVM), etiket, kullanılan alan.
- Linux bölümlerini taşır ve büyütür: veri bayt bayt taşınır ve doğrulanır, işlem yarıda kalırsa program
  açılışta kaldığı yerden sürdürür, bölümün benzersiz kimliği (PARTUUID) korunur.
- ext2/3/4 dosya sistemini büyütür, küçültür, böler, denetler, etiketler ve ext4 olarak biçimlendirir. Bu işlemler
  kurulumla gelen küçük ve yalıtılmış bir Linux'ta, Linux'un kendi `e2fsck` ve `resize2fs` araçlarıyla yapılır.

### Araçlar
- Yüzey testi, dosya sistemi denetimi, SMART sağlık bilgisi, 4K hizalama denetimi.
- Kayıp bölüm arama ve geri yükleme (deneysel).
- Alan analizi: klasör boyutları ve en büyük 100 dosya.

### Arayüz
- Türkçe / İngilizce arayüz ve koyu / açık tema; ikisi de araç çubuğundan değiştirilir.
- Kullanılamayan işlemler tıklanınca nedenini söyler.
- **Birleştir** seçenekli pencereyle açılır; boyutlandırmada **Tüm kullanılabilir alanı kullan** seçeneği vardır.
- Ayrılmamış alanda **Bu alanı bir bölüme ekle**.

### Kurulum ve güncelleme
- Windows kurulum sihirbazı ve Linux kurulum paketi.
- GitHub üzerinden güncelleme: açılışta otomatik ya da **Güncelleme denetle** ile; aradaki her sürümün notları
  gösterilir, indirme SHA-256 ile doğrulanır.

