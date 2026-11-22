<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/images/keedesk-logo-dark.png">
    <img src="docs/images/keedesk-logo-light.png" alt="KeeDesk — EGEROBOT'tan Mac için uzak masaüstü" width="420">
  </picture>
</p>

<h1 align="center">KeeDesk — Mac için güvenli uzak masaüstü</h1>

<p align="center">
  Mac'inize başka bir bilgisayardan ulaşın ya da birine kendi ekranında yardım edin. Uçtan uca şifreli; ekranın başındaki kişi evet demeden hiçbir şey başlamaz.
</p>

<p align="center">
  <img alt="Durum" src="https://img.shields.io/badge/durum-geli%C5%9Ftiriliyor-844D3E">
  <img alt="Platform" src="https://img.shields.io/badge/platform-macOS%2013%2B-33160F">
  <img alt="Şifreleme" src="https://img.shields.io/badge/%C5%9Fifreleme-u%C3%A7tan%20uca-00696F">
  <a href="README.md"><img alt="English" src="https://img.shields.io/badge/language-English-844D3E"></a>
</p>

---

> **KeeDesk geliştiriliyor.** Mac uygulaması bugün kendi Mac'lerimiz arasında çalışıyor; ilk genel sürüm bu sayfada yayınlanacak. Haber almak için yukarıdan **Watch → Custom → Releases** seçin.

Bu depo **KeeDesk'in GitHub'daki resmî indirme kanalıdır**. Yalnız sürüm dosyaları bulunur, kaynak kod yoktur. Her sürümde Developer ID ile imzalı, Apple onaylı (notarize) kurulum dosyası ve `SHA256SUMS` dosyası olacak.

<img src="docs/images/welcome-tr.jpg" alt="macOS'ta KeeDesk karşılama ekranı: bir Mac'e ulaşın ya da uzaktan yardım edin, uçtan uca şifreli" width="100%">

## Platformlar

| Platform | Durum |
|---|---|
| **macOS 13 ve sonrası** (Apple çipli ve Intel) | Geliştiriliyor — ilk sürüm burada yayınlanacak |
| **Windows ve Linux** | Planlandı, Mac uygulamasından sonra |
| **iOS ve Android** | Planlandı, Mac uygulamasından sonra; geliştirmesine henüz başlanmadı |

## KeeDesk neler yapar

### 9 haneli ID ile bağlanın

Her Mac kendi anahtar çiftinden türeyen bir **KeeDesk ID** alır; hiçbir sunucu bu numarayı uyduramaz ya da başkasına veremez. Karşı tarafın ID'sini yazın ve Bağlan'a basın. KeeDesk **aynı ağdaki** öteki KeeDesk cihazlarını da bulur, **son oturumlarınızı** tutar ve onları yeniden adlandırmanıza izin verir.

### Onayınız olmadan hiçbir şey başlamaz

<img src="docs/images/access-tr.jpg" alt="KeeDesk erişim ayarları: bağlantılara izin ver ya da kapat, yalnız şifreyle erişim ve gözetimsiz erişim" width="100%">

- **Kabul penceresi** kimin istediğini gösterir; neler yapabileceğini siz seçersiniz ve oturum sırasında değiştirebilirsiniz.
- **Gelen bağlantıları** tek düğmeyle kapatın ya da **yalnız şifreyi bilenleri** içeri alın.
- Kendi Mac'leriniz için **gözetimsiz erişim**; **iki aşamalı doğrulama (TOTP)**, ID **izin listesi** ve **izin profilleri** (yalnız ekran, tam erişim, gözetimsiz ya da size özel) ile.
- Bir kez çalışan ve iki saatte sona eren **tek kullanımlık davet kodu**.
- Biri bağlıyken ekranınızın çevresinde **renkli çerçeve**, isteğe bağlı **oturum sonunda ekran kilidi** ve **bağlantı geçmişi**.

### Denetlenebilir güvenlik

- **Uçtan uca şifreleme**: X25519 anahtar değişimi, Ed25519 imzalı el sıkışma, yön başına ayrı anahtarla ChaCha20-Poly1305.
- İki tarafın karşılaştırabildiği **güvenlik kodu** (parmak izi); bilinen bir cihazın anahtarı değişirse KeeDesk durur ve size söyler.
- Şifre yalnız **tuzlu PBKDF2-SHA256 özeti** (310.000 tur) olarak saklanır, sabit sürede karşılaştırılır; hatalı denemelerden sonra bekleme süresi artar ve **istek seli koruması** devrededir.
- Oturum kaydedildiğinde karşı tarafa **her zaman bildirilir**.

### Açık dille macOS izinleri

<img src="docs/images/permissions-tr.jpg" alt="KeeDesk sistem izinleri: Ekran Kaydı, Erişilebilirlik ve Tam Disk Erişimi, her biri açıklamasıyla" width="100%">

KeeDesk, macOS'un istediği üç izni — Ekran Kaydı, Erişilebilirlik ve Tam Disk Erişimi — gösterir, her birinin ne için gerektiğini söyler ve hepsini tek yerden denetleyip sıfırlamanızı sağlar.

### Hızlı ve net görüntü

<img src="docs/images/picture-tr.jpg" alt="KeeDesk oturum ayarları: çözünürlük, kare hızı ve bit hızı sınırları" width="100%">

- KeeDesk'in kendi pencerelerini dışarıda bırakan **ScreenCaptureKit** yakalama, **VideoToolbox HEVC ya da H.264** donanım kodlama ve çözme.
- Uyarlanır kalite (hız · denge · en iyi) ve oturum başına **çözünürlük, kare hızı ve bit hızı** sınırı.
- Çoklu monitör, ayrı **uzak imleç** kanalı, orijinal ya da pencereye sığdır görünüm.

### Bir oturumun ihtiyacı olan her şey

- Unicode yazma ve kısayol iletimiyle (⌘-Tab ve diğerleri) **fare ve klavye** kontrolü; oturum bitince takılı kalan değiştirici tuşlar temizlenir.
- Metin ve görsel için **pano eşitleme**, iki panelli dosya yöneticisiyle **dosya aktarımı**; göndermek için **dosyayı uzak ekranın üstüne bırakın**, almak için uzak dosyayı Finder'a sürükleyin.
- **Sohbet**, **sistem sesi**, mikrofon seçimi ve testiyle **iki yönlü konuşma**.
- İzleyen tarafta **ekran görüntüsü**, **oturum kaydı**, **beyaz tahta**, **gizlilik kipi** (uzak ekranı karart), **yerel girdiyi kilitle**.
- Otomatik yeniden bağlanmalı **uzaktan yeniden başlatma**, **sistem bilgisi**, **TCP tüneli**, **Wake-on-LAN**.
- **Destek kuyruğu**: kişiler ID'nizle yardım ister, siz sırayla alırsınız.
- **Linkle bağlanma** — `keedesk://` linki oturum değil, soru açar.

<img src="docs/images/link-tr.jpg" alt="KeeDesk linkle bağlanma penceresi: Bağlan'a basmadan hiçbir şey olmaz" width="100%">

## Yol haritası

- Buluşma ve röle sunucumuz üzerinden internet bağlantısı; ardından NAT delme ve hata düzeltmeli doğrudan UDP (QUIC).
- KeeDesk hesabı, planlar ve imzalı otomatik güncelleme.
- Windows ve Linux uygulamaları; ardından iOS ve Android.
- 41 arayüz dili (bugün İngilizce ve Türkçe).
- Kurumsal: kendi buluşma sunucunuz, toplu kurulum, tek oturum açma ve markalama.

## Güvenlik bildirimi

Bkz. [SECURITY.md](SECURITY.md).

---

<sub>KeeDesk, **EGEROBOT**'un (EGEROBOT OTOMASYON MÜHENDİSLİK PROJE DANIŞMANLIK SAN. VE TİC. LTD. ŞTİ.) ürünüdür, İzmir, Türkiye. KeeDesk tescilli yazılımdır; bkz. [LICENSE](LICENSE).<br>
Anahtar kelimeler: uzak masaüstü, Mac uzak masaüstü, uzaktan bağlantı, uzaktan destek, uzaktan erişim, ekran paylaşımı, gözetimsiz erişim, uçtan uca şifreli uzak masaüstü, remote desktop, remote desktop for Mac, remote support, screen sharing, KeeDesk.</sub>
