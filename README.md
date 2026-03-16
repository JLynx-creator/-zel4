# Devamsızlık Takip Sistemi - Kapsamlı Dokümantasyon

## 🎯 Sistem Genel Bakış ve Felsefesi

**Öğrenci devamsızlık takibini** dijital ortama taşımışlar. **Web tabanlı ölçeklenebilir ve güvenli** bir sistem yapmışlar. Geleneksel manuel süreçleri otomatikleştirmişler ve eğitim kurumları ile resmi kurumlar arasında **etkin bir iletişim köprüsü** kurmuşlar. Güzel düşünmüşler.

### 🏗️ Sistem Mimarisi ve Tasarım Prensipleri

Sistemi **Çok Katmanlı Mimari (Multi-Layer Architecture)** ile tasarlamışlar. Şu prensiplere dayandırmışlar.

1. **Rol Bazlı Erişim Kontrolü (Role-Based Access Control - RBAC)**. Herkes yalnızca kendi yetki alanına erişiyor. Doğru yapmışlar.
2. **Veri Bütünlüğü ve Güvenliği**. Tüm veriler koruma altında. Hiçbir veri kaybolmuyor. İyi düşünmüşler.
3. **Modüler ve Genişletilebilir Yapı**. İhtiyaç halinde kolayca yeni özellik eklenebiliyor. Akıllıca kurmuşlar.
4. **Kullanıcı Deneyimi Odaklı Arayüz**. Sezgisel ve kullanıcı dostu bir tasarım yapmışlar.
5. **Otomatik Bildirim ve İş Akışı**. Her şeyi otomatik hale getirmişler. İnsan hatası neredeyse yok.

### 🔄 İş Akışı Mantığı

**Üç farklı kullanıcı rolü** ile işbirliğine dayalı bir ekosistem kurmuşlar.

- **Admin (Sistem Yöneticisi)**. Sistemin genel yönetimi ve denetimi. Her şeye erişimi var.
- **Okul (Eğitim Kurumu)**. Öğrenci devamsızlık verilerinin girişi ve takibi. Sahada çalışan kullanıcılar bunlar.
- **Kurum (Resmi Kurumlar)**. Adres teyit ve bilgi taleplerinin yönetimi. Resmi işleri hallediyor.

Her kullanıcı **yetkisi doğrultusunda** sisteme erişiyor ve kendi alanındaki işlemleri yapıyor. **Veri güvenliği** ve **iş bölümü** prensibine dayandırmışlar. Güzel kurmuşlar.

---

## 📁 Detaylı Dosya Yapısı ve Mimarik Analiz

### 🚀 Ana Çekirdek Dosyaları (Core Files)

Bu dosyalar sistemin **omurgasını** oluşturuyor. Tüm işlemler buradan başlıyor.

#### `index.php` - Sistem Kalbi ve Yönlendirme Merkezi

```php
/**
 * Ana Sayfa - Akıllı Yönlendirme Sistemi
 * 
 * İşlevi:
 * 1. Oturum kontrolü yapar
 * 2. Kullanıcı rolünü tespit eder
 * 3. Yetkisine göre panele yönlendirir
 * 4. Güvenlik önlemleri uygular
 */
```

**Teknik Detaylar:**
- **Session Management**. PHP session kontrolü yapıyor.
- **Role-Based Routing**. Rol bazlı yönlendirme algoritması kurmuşlar.
- **Security Layer**. Yetkisiz erişim engelleniyor. Doğru yapmışlar.
- **Performance Optimization**. Minimum kodla maksimum verimlilik sağlamışlar.

**Mantıksal Akış:**
1. Kullanıcı sisteme erişir → `index.php` çalışır
2. `is_logged_in()` fonksiyonu oturum kontrolü yapar
3. Giriş yapmamışsa → `login.php`'ye yönlendirir
4. Giriş yapmışsa → `switch($_SESSION['rol'])` ile rol kontrolü
5. Role göre ilgili panele yönlendirme.
   - `admin` → `admin/index.php`
   - `okul` → `okul/index.php`
   - `kurum` → `kurum/index.php`

#### `login.php` - Güvenlik Kapısı ve Kimlik Doğrulama Merkezi

```php
/**
 * Giriş Sistemi - Çok Katmanlı Güvenlik
 * 
 * Özellikler:
 * 1. Güvenli kimlik doğrulama
 * 2. Şifremi unuttum özelliği
 * 3. Brute force koruması
 * 4. Otomatik yönlendirme
 */
```

**Güvenlik Katmanları:**
- **Password Hashing**. `password_hash()` ile güvenli şifre saklama
- **Input Validation**. Kullanıcı girdilerinin temizlenmesi
- **Session Security**. Güvenli oturum yönetimi
- **CSRF Protection**. Cross-site request forgery koruması

**İş Akışı:**
1. Form verisi POST ile gönderilir
2. `trim()` ile boşluklar temizlenir
3. Veritabanında kullanıcı kontrolü
4. `password_verify()` ile şifre doğrulaması
5. Başarılı girişte session oluşturma
6. Role göre panele yönlendirme

#### `logout.php` - Güvenli Çıkış Sistemi

```php
/**
 * Oturum Sonlandırma - Tam Güvenlikli Çıkış
 * 
 * İşlevler:
 * 1. Session verilerini temizler
 * 2. Oturum dosyasını siler
 * 3. Çerezleri temizler
 * 4. Ana sayfaya yönlendirir
 */
```

**Güvenlik Prosedürleri:**
- `session_destroy()` ile tam oturum sonu
- `unset($_SESSION)` ile session veri temizliği
- `setcookie()` ile çerez temizliği
- Güvenli yönlendirme

#### `hash-olustur.php` - Kriptografik Şifre Üretici

```php
/**
 * Şifre Hash Oluşturucu - Güvenlik Aracı
 * 
 * Kullanım:
 * php hash-olustur.php [sifre]
 * 
 * Özellikler:
 * 1. PASSWORD_DEFAULT algoritması
 * 2. Otomatik tuz (salt) oluşturma
 * 3. Komut satırı desteği
 */
```

**Teknik Özellikler:**
- **Algorithm**. `PASSWORD_DEFAULT` (bcrypt)
- **Salt**. Otomatik rastgele tuz oluşturma
- **Cost Factor**. Optimizasyon için ayarlanabilir maliyet
- **Command Line**. CLI üzerinden kullanım desteği

---

## ⚙️ Konfigürasyon ve Sistem Ayarları

### `config/config.php` - Sistem Beyni ve Ayar Merkezi

Bu dosya sistemin **merkezi sinir sistemi** gibi çalışıyor. Tüm ayarları ve sabitleri buraya toplamışlar. İyi bir yaklaşım.

#### 🌐 Temel Sistem Ayarları

```php
// Sistem Tanımlaması
define('SITE_NAME', 'Devamsızlık Takip Sistemi');
define('SITE_URL', 'http://localhost/devamsizlik_dagitim/');
define('BASE_PATH', dirname(dirname(__FILE__)) . '/');

// Zaman Dilimi ve Lokalizasyon
date_default_timezone_set('Europe/Istanbul');
```

#### 🎭 Rol ve Yetki Tanımlamaları

```php
// Kullanıcı Rolleri - Hiyerarşik Yapı
define('ROL_ADMIN', 'admin');      // En yetkili
define('ROL_OKUL', 'okul');        // Orta yetkili  
define('ROL_KURUM', 'kurum');      // Sınırlı yetkili

// Kurum Türleri - Sınıflandırma
define('KURUM_ILKOKUL', 'ilkokul');
define('KURUM_ORTAOKUL', 'ortaokul');
define('KURUM_LISE', 'lise');
define('KURUM_DIGER', 'diger');
```

#### 📊 İş Akışı ve Durum Yönetimi

```php
// Talep Durumları - İş Akışı
define('TALEP_BEKLIYOR', 'bekliyor');
define('TALEP_TEYIT', 'teyit_edildi');
define('TALEP_IPTAL', 'iptal');

// Devamsızlık Eşiği - Otomatik Tetikleme
define('DEVAMSIZLIK_ESIK', 10); // 10 gün ve üzeri
```

#### 🏛️ Kurum İletişim Ağı

```php
// Bilgi Talep Kurumları - Otomatik Bildirim
define('BILGI_TALEP_KURUMLAR', [
    61,   // Sosyal Hizmetler Müdürlüğü
    86,   // Muhtarlık
    65,   // Nüfus Müdürlüğü
    170,  // Sosyal İşler Müdürlüğü
    172   // Kaymakamlik Sosyal Yardım
]);
```

#### 📧 E-posta İletişim Sistemi

```php
// SMTP Mail Ayarları - Güvenli İletişim
define('SMTP_HOST', 'smtp.gmail.com');
define('SMTP_PORT', 587);
define('SMTP_ENCRYPTION', 'tls');
define('SMTP_USERNAME', 'email@gmail.com');
define('SMTP_PASSWORD', 'app_password');
```

### `config/database.php` - Veri Yönetimi ve Bağlantı Katmanı

```php
/**
 * Veritabanı Bağlantı Yönetimi
 * 
 * Özellikler:
 * 1. PDO ile güvenli bağlantı
 * 2. Hata yakalama mekanizması
 * 3. Karakter seti optimizasyonu
 * 4. Yardımcı sorgu fonksiyonları
 */
```

**Bağlantı Parametreleri:**
- **Host**. `localhost`
- **Charset**. `utf8mb4` yani Unicode desteği var.
- **Collation**. `utf8mb4_turkish_ci` Türkçe karakter desteği düşünmüşler. Güzel.
- **Error Mode**. `PDO::ERRMODE_EXCEPTION` detaylı hata raporu alıyorlar.

**Yardımcı Fonksiyonlar:**
- `db_query()`. Parametreli sorgu çalıştırıyor.
- `db_fetch()`. Tek sonuç getiriyor.
- `db_fetch_all()`. Tüm sonuçları getiriyor.
- `db_insert()`. Veri ekleyip ID döndürüyor. Kullanışlı yapmışlar.

---

## 🔧 Sistem Kütüphaneleri ve Fonksiyonel Modüller

### `includes/functions.php` - Sistem Fonksiyonları Kütüphanesi

Bu dosyada **sık kullanılan işlemleri** merkezi bir yerde toplamışlar. Kod tekrarını önlemişler. Bakımı da kolaylaştırmışlar. Doğru düşünmüşler.

#### 📅 Tarih ve Zaman Yönetimi

```php
/**
 * Tarih Formatlama Fonksiyonları
 * 
 * Özellikler:
 * 1. Türkçe tarih formatı
 * 2. Farklı tarih formatları
 * 3. Zaman hesaplama
 * 4. Lokalizasyon desteği
 */
```

#### 📁 Dosya Yönetimi Sistemi

```php
/**
 * Dosya İşlemleri
 * 
 * Fonksiyonlar:
 * - Dosya yükleme kontrolü
 * - Tip ve boyut doğrulama
 * - Güvenli dosya adı oluşturma
 * - Dizin yönetimi
 */
```

#### 📊 Excel Veri İşleme

```php
/**
 * PhpSpreadsheet Entegrasyonu
 * 
 * Özellikler:
 * 1. Veri dışa aktarma
 * 2. Raporlama
 * 3. Formatlama
 * 4. Otomatik hesaplama
 */
```

### `includes/auth.php` - Güvenlik ve Yetkilendirme Sistemi

Bu dosya sistemin **güvenlik duvarı** gibi çalışıyor. Buraya iyi bakmışlar.

#### 🔐 Kimlik Doğrulama Fonksiyonları

```php
/**
 * Giriş ve Yetki Kontrolü
 * 
 * Fonksiyonlar:
 * - is_logged_in() - Oturum kontrolü
 * - has_role() - Rol kontrolü
 * - redirect() - Güvenli yönlendirme
 * - logout_user() - Çıkış işlemi
 */
```

#### 🛡️ Güvenlik Katmanları

- **Session Validation**. Oturum geçerliliğini kontrol ediyor.
- **Role Authorization**. Rol bazlı yetkilendirme yapmışlar.
- **Secure Routing**. Güvenli sayfa yönlendirmesi var.
- **Token Management**. CSRF token yönetimini de unutmamışlar. Kapsamlı düşünmüşler.

### `includes/header.php` ve `includes/footer.php` - Arayüz Yönetimi

Bu dosyalar **tutarlı kullanıcı deneyimi** sağlıyor. Her sayfada aynı görünüm var.

#### 🎨 Header Bileşenleri
- **Navigation Menu**. Rol bazlı menü gösterimi
- **User Information**. Kullanıcı bilgileri
- **Notification System**. Bildirimler
- **Search Functionality**. Arama özellikleri

#### 🏗️ Footer Bileşenleri
- **Copyright Information**. Telif bilgileri
- **System Information**. Sistem versiyonu
- **Quick Links**. Hızlı erişim linkleri
- **JavaScript Libraries**. Script yükleme

---

## 🎨 Frontend ve Arayüz Mimarisi

### `assets/` Klasörü - Kullanıcı Deneyimi Katmanı

Bu klasör sistemin **görsel ve etkileşimli** tarafını yönetiyor. Arayüz işleri burada.

#### `css/` - Stil ve Tasarım Yönetimi

**Bootstrap Framework** tabanlı modern ve responsive bir tasarım yapmışlar.

```css
/* Ana stil özellikleri */
- Responsive grid system
- Component-based design
- Custom theme colors
- Animation effects
- Mobile-first approach
```

**Özellikler:**
- **Responsive Design**. Tüm cihazlarda uyumlu çalışıyor.
- **Component Library**. Yeniden kullanılabilir bileşenler yapmışlar. Kod tekrarı yok.
- **Theme System**. Renk şeması özelleştirilebilir.
- **Animation**. Yumuşak geçişler ve animasyonlar eklemişler.

#### `js/` - JavaScript ve Etkileşim Yönetimi

**jQuery** tabanlı dinamik etkileşimler kurmuşlar.

```javascript
/* Ana JavaScript özellikleri */
- Form validation
- AJAX operations
- Dynamic content loading
- Real-time updates
- User interactions
```

**Fonksiyonellikler:**
- **Form Validation**. Anlık form kontrolü var.
- **AJAX Operations**. Sayfa yenileme olmadan veri alışverişi yapıyor. Kullanıcı deneyimi düşünmüşler.
- **DataTables**. Gelişmiş tablo özellikleri eklemişler.
- **Chart Libraries**. Grafik ve görselleştirme için kütüphane kullanmışlar.
- **Notification System**. Bildirim yönetimi de var.

#### `images/` - Görsel Varlıklar

Sistem görsellerinin merkezi deposu burası.

- **Logo ve Branding**. Marka görselleri
- **Icons**. İkon setleri
- **Backgrounds**. Arka plan görselleri
- **User Avatars**. Kullanıcı resimleri

#### `plugins/` - Üçüncü Parti Kütüphaneler

Gelişmiş özellikler için üçüncü parti eklentiler kullanmışlar.
- **DataTables**. Gelişmiş tablo işlemleri
- **Chart.js**. Grafik ve görselleştirme
- **DatePicker**. Tarih seçici
- **FileUpload**. Dosya yükleme
- **Validation**. Form doğrulama

---

## 👥 Kullanıcı Panelleri ve Rol Bazlı Arayüzler

### 🅰️ Admin Paneli - Sistem Yönetim Merkezi

**Dosya Sayısı.** 26+ dosya var. Admin paneli oldukça kapsamlı yapmışlar.
**Yetki Seviyesi.** En yüksek yetki seviyesi.
**İşlevsellik.** Tam sistem kontrolü sağlıyor.

#### 🎯 Ana Modüller

**Kullanıcı Yönetimi.**
- `kurum-kullanici-ekle.php`. Yeni kullanıcı ekleme.
- `kurum-kullanici-sifre-yenile-ajax.php`. Şifre yenileme. AJAX ile yapmışlar.
- `kurum-kullanici-sil-ajax.php`. Kullanıcı silme.

**Kurum Yönetimi.**
- `kurum-ekle.php`. Kurum ekleme ve düzenleme.
- `get-kurumlar-yeni-soru-ajax.php`. Kurum listesini AJAX ile çekiyor.

**Raporlama ve İstatistik.**
- `raporlar.php`. Detaylı raporlama sistemi yapmışlar.
- `okul-istatistik.php`. Okul bazlı istatistikler.
- `mail-loglari.php`. E-posta gönderim loglarını da tutuyorlar. İyi.

**İletişim ve Bilgi Akışı.**
- `gelen-sorular.php`. Gelen bilgi taleplerini görüntülüyor.
- `giden-sorular.php`. Gönderilen talepleri takip ediyor.
- `soru-cevaplari.php`. Soru-cevap yönetimi.

**Sistem Bakımı.**
- `profil.php`. Yönetici profili.
- `adres-tespit-yabancilar.php`. Özel adres tespiti için ayrı dosya açmışlar.

#### 🛠️ AJAX İşlemleri

**Asenkron Veri İşlemleri.**
- `admin-soru-ekle-ajax.php`. Soru ekleme.
- `admin-soru-duzenle-ajax.php`. Soru düzenleme.
- `admin-soru-guncelle-ajax.php`. Soru güncelleme.
- `admin-soru-okundu-ajax.php`. Okundu işaretleme. Hepsini AJAX ile yapmışlar. Sayfayı yenilemeden hallediyor.

### 🅱️ Okul Paneli - Eğitim Yönetimi

**Dosya Sayısı.** 15+ dosya.
**Yetki Seviyesi.** Orta seviye yetki.
**İşlevsellik.** Öğrenci ve devamsızlık yönetimi yapıyor.

#### 🎓 Ana Modüller

**Öğrenci Yönetimi.**
- Öğrenci ekleme ve düzenleme yapılıyor.
- Sınıf yönetimi var.
- Öğrenci listeleri görüntülenebiliyor.

**Devamsızlık Takibi.**
- Devamsızlık kayıt sistemi çalışıyor.
- Otomatik bildirim gönderiliyor. Eşik geçilince devreye giriyor.
- İstatistiksel takip de var.

**İletişim Yönetimi.**
- Kurumlara talep gönderilebiliyor.
- Bilgi paylaşımı yapılıyor.
- Raporlama da eklemişler.

### 🅲️ Kurum Paneli - Kurumsal İşlemler

**Dosya Sayısı.** 10+ dosya.
**Yetki Seviyesi.** Sınırlı yetki vermiş ler. Doğru yapmışlar.
**İşlevsellik.** Bilgi talepleri ve teyit işlemlerini yönetiyor.

#### 🏛️ Ana Modüller

**Bilgi Talepleri.**
- Gelen talepler listeleniyor.
- Talep detayına bakılabiliyor.
- Cevap gönderilebiliyor. Sade tutmuşlar.

**Adres Teyit.**
- Adres doğrulaması yapılıyor.
- Bilgi güncellenebiliyor.
- İletişim yönetimi de var.

---

## 📊 Veritabanı Mimarisi ve Veri Modeli

### 🗄️ Veri Yapısı ve İlişkiler

#### `kullanicilar` Tablosu - Kullanıcı Yönetimi

```sql
CREATE TABLE kullanicilar (
    id INT(11) PRIMARY KEY AUTO_INCREMENT,
    kurum_id INT(11) NOT NULL,
    kullanici_adi VARCHAR(50) UNIQUE NOT NULL,
    sifre VARCHAR(255) NOT NULL,
    ad_soyad VARCHAR(100) NOT NULL,
    email VARCHAR(100) NULL,
    telefon VARCHAR(20) NULL,
    rol ENUM('admin', 'okul', 'kurum') NOT NULL,
    aktif TINYINT(1) DEFAULT 1,
    son_giris DATETIME NULL,
    olusturma_tarihi TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    personel_rutbe VARCHAR(50) NULL,
    guncelleme_tarihi TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

**Alan Açıklamaları:**
- **id**. Benzersiz kullanıcı kimliği.
- **kurum_id**. Kullanıcının bağlı olduğu kurum.
- **kullanici_adi**. Giriş için kullanıcı adı.
- **sifre**. `password_hash()` ile şifrelenmiş parola. Güvenli saklıyorlar.
- **rol**. Sistemdeki kullanıcı rolü.
- **aktif**. Hesabın aktif veya pasif durumu.
- **son_giris**. Son başarılı giriş zamanı. Takip etmişler.

#### `ogrenciler` Tablosu - Öğrenci Bilgi Yönetimi

```sql
CREATE TABLE ogrenciler (
    id INT(11) PRIMARY KEY AUTO_INCREMENT,
    okul_id INT(11) NOT NULL,
    sinif_id INT(11) NOT NULL,
    ad_soyad VARCHAR(100) NOT NULL,
    tc_kimlik_no VARCHAR(11) UNIQUE NOT NULL,
    dogum_tarihi DATE NOT NULL,
    cinsiyet ENUM('E', 'K') NOT NULL,
    adres TEXT NOT NULL,
    veli_ad_soyad VARCHAR(100) NULL,
    veli_telefon VARCHAR(20) NULL,
    kayit_tarihi TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**Özellikler:**
- **TC Kimlik No**. Benzersiz kimlik doğrulama için kullanıyorlar.
- **Cinsiyet**. Enum ile kısıtlı seçenek yapmışlar. Veri tutarlılığı düşünmüşler.
- **Adres**. Detaylı adres bilgisi tutuluyor.
- **Veli Bilgileri**. Veli iletişim bilgilerini de eklemişler.

#### `devamsizliklar` Tablosu - Devamsızlık Takip Sistemi

```sql
CREATE TABLE devamsizliklar (
    id INT(11) PRIMARY KEY AUTO_INCREMENT,
    ogrenci_id INT(11) NOT NULL,
    okul_id INT(11) NOT NULL,
    tarih DATE NOT NULL,
    gun_sayisi INT(2) NOT NULL DEFAULT 1,
    sebep VARCHAR(100) NULL,
    aciklama TEXT NULL,
    kayit_yapan INT(11) NOT NULL,
    kayit_tarihi TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (ogrenci_id) REFERENCES ogrenciler(id),
    FOREIGN KEY (okul_id) REFERENCES okullar(id)
);
```

**İşlevsellik:**
- **Tarih**. Devamsızlık tarihi.
- **Gün Sayısı**. Kaç gün devamsızlık yapıldığı.
- **Sebep**. Devamsızlık nedeni de kaydediliyor. İyi düşünmüşler.
- **Kayıt Yapan**. İşlemi yapan kullanıcı kaydediliyor. İzlenebilirlik var.

#### `kurumlar` Tablosu - Kurum Yönetimi

```sql
CREATE TABLE kurumlar (
    id INT(11) PRIMARY KEY AUTO_INCREMENT,
    kurum_adi VARCHAR(100) NOT NULL,
    kurum_tipi ENUM('ilkokul', 'ortaokul', 'lise', 'diger') NOT NULL,
    adres TEXT NOT NULL,
    telefon VARCHAR(20) NULL,
    email VARCHAR(100) NULL,
    yetkili_kisi VARCHAR(100) NULL,
    aktif TINYINT(1) DEFAULT 1,
    olusturma_tarihi TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### `bilgi_talepleri` Tablosu - İletişim Akışı

```sql
CREATE TABLE bilgi_talepleri (
    id INT(11) PRIMARY KEY AUTO_INCREMENT,
    devamsizlik_id INT(11) NOT NULL,
    ogrenci_id INT(11) NOT NULL,
    kurum_id INT(11) NOT NULL,
    talep_tarihi TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    durum ENUM('bekliyor', 'teyit_edildi', 'iptal') DEFAULT 'bekliyor',
    cevap_tarihi DATETIME NULL,
    cevap_metni TEXT NULL,
    gonderen_kullanici_id INT(11) NOT NULL,
    FOREIGN KEY (ogrenci_id) REFERENCES ogrenciler(id),
    FOREIGN KEY (kurum_id) REFERENCES kurumlar(id)
);
```

---

## 🔄 Otomasyon ve İş Akışı Sistemi

### 🤖 Otomatik Bildirim Mekanizması

**10 gün devamsızlık eşiğini** geçen öğrenciler için otomatik bildirim sistemi kurmuşlar. Güzel bir çözüm.

#### 📧 Bildirim Akışı

**1. Tetikleme (Trigger):**
```php
if ($devamsizlik_gun_sayisi >= DEVAMSIZLIK_ESIK) {
    // Otomatik bildirim başlat
    otomatik_bildirim_gonder($ogrenci_id);
}
```

**2. Kurum Seçimi:**
```php
$hedef_kurumlar = BILGI_TALEP_KURUMLAR;
foreach ($hedef_kurumlar as $kurum_id) {
    bilgi_talebi_olustur($ogrenci_id, $kurum_id);
}
```

**3. E-posta Gönderimi:**
```php
$mail = new PHPMailer();
$mail->addAddress($kurum_email);
$mail->Subject = 'Devamsızlık Bildirimi';
$mail->Body = $bildirim_mesaji;
$mail->send();
```

**4. Veritabanı Kaydı:**
```sql
INSERT INTO bilgi_talepleri 
(ogrenci_id, kurum_id, durum, talep_tarihi) 
VALUES (?, ?, 'bekliyor', NOW());
```

### 📊 İş Akışı Diyagramı

```
Öğrenci Devamsızlık (≥10 gün)
           ↓
    Sistem Otomatik Tespit
           ↓
   Kurum Listesi Belirle
           ↓
     Bilgi Talebi Oluştur
           ↓
      E-posta Gönder
           ↓
    Takip Numarası Üret
           ↓
      Kurum Bildirimi
```

---

## 🛡️ Güvenlik Mimarisi ve Koruma Katmanları

### 🔐 Çok Katmanlı Güvenlik Sistemi

**Dört katmanlı güvenlik** mimarisi kurmuşlar. Kapsamlı düşünmüşler. Her katmanı ayrı ayrı ele almışlar.

#### 1. Katman: Kimlik Doğrulama (Authentication)
```php
// Güvenli şifre hashleme
$sifre_hash = password_hash($sifre, PASSWORD_DEFAULT);

// Session güvenliği
session_regenerate_id(true);
$_SESSION['user_agent'] = $_SERVER['HTTP_USER_AGENT'];
```

#### 2. Katman: Yetkilendirme (Authorization)
```php
// Rol bazlı erişim kontrolü
function has_role($required_role) {
    return isset($_SESSION['rol']) && $_SESSION['rol'] === $required_role;
}

// Sayfa bazlı yetkilendirme
if (!has_role('admin')) {
    redirect(SITE_URL . 'login.php');
}
```

#### 3. Katman: Veri Koruma (Data Protection)
```php
// SQL Injection koruması
$stmt = $pdo->prepare("SELECT * FROM kullanicilar WHERE kullanici_adi = ?");
$stmt->execute([$kullanici_adi]);

// XSS koruması
$temiz_veri = htmlspecialchars($kullanici_girdisi, ENT_QUOTES, 'UTF-8');
```

#### 4. Katman: İletişim Güvenliği (Communication Security)
```php
// CSRF token
$_SESSION['csrf_token'] = bin2hex(random_bytes(32));

// HTTPS zorunluluğu
if ($_SERVER['HTTPS'] !== 'on') {
    redirect('https://' . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI']);
}
```

---

## 📈 Performans Optimizasyonu ve Sistem Verimliliği

### ⚡ Optimizasyon Stratejileri

#### Veritabanı Optimizasyonu
```sql
-- İndeksleme
CREATE INDEX idx_ogrenci_devamsizlik ON devamsizliklar(ogrenci_id, tarih);
CREATE INDEX idx_kullanici_rol ON kullanicilar(rol, aktif);

-- Query optimizasyonu
EXPLAIN SELECT * FROM devamsizliklar WHERE ogrenci_id = ? ORDER BY tarih DESC;
```

#### Önbellekleme (Caching)
```php
// Session cache
$_SESSION['cached_data'] = $sik_kullanilan_veriler;

// Veritabanı cache
$cache_key = 'kurum_listesi_' . date('Y-m-d');
if (!apcu_exists($cache_key)) {
    $kurumlar = get_kurum_listesi();
    apcu_store($cache_key, $kurumlar, 3600); // 1 saat
}
```

#### Frontend Optimizasyonu
```javascript
// Lazy loading
$(document).ready(function() {
    $('.lazy-load').on('scroll', function() {
        // Scroll ile veri yükleme
    });
});

// Resource optimization
// CSS minification
// JS compression
// Image optimization
```

---

## 🚀 Dağıtım ve Kurulum Süreci

### 📋 Detaylı Kurulum Rehberi

#### Phase 1: Sunucu Hazırlığı
```bash
# 1. XAMPP kurulumu
indir_xampp.exe
kurulum_yap()

# 2. Servis başlatma
start apache
start mysql

# 3. Güvenlik ayarları
mysql_secure_installation
```

#### Phase 2: Veritabanı Kurulumu
```sql
-- 1. Veritabanı oluştur
CREATE DATABASE devamsizlik_db CHARACTER SET utf8mb4 COLLATE utf8mb4_turkish_ci;

-- 2. Kullanıcı oluştur
CREATE USER 'devamsizlik_user'@'localhost' IDENTIFIED BY 'guvenli_sifre';
GRANT ALL PRIVILEGES ON devamsizlik_db.* TO 'devamsizlik_user'@'localhost';

-- 3. SQL dosyasını içe aktar
SOURCE devamsizlik_db.sql;
```

#### Phase 3: Dosya Dağıtımı
```bash
# 1. Dosyaları kopyala
cp -r devamsizlik_dagitim/ /var/www/html/

# 2. İzinleri ayarla
chmod 755 /var/www/html/devamsizlik_dagitim/
chmod -R 777 /var/www/html/devamsizlik_dagitim/uploads/
chmod -R 777 /var/www/html/devamsizlik_dagitim/resimler/

# 3. Owner ayarla
chown -R www-data:www-data /var/www/html/devamsizlik_dagitim/
```

#### Phase 4: Konfigürasyon
```php
// config/config.php düzenle
define('SITE_URL', 'https://alanadiniz.com/devamsizlik_dagitim/');
define('DB_HOST', 'localhost');
define('DB_USER', 'devamsizlik_user');
define('DB_PASS', 'guvenli_sifre');
define('DB_NAME', 'devamsizlik_db');

// Mail ayarları
define('SMTP_USERNAME', 'sistem@alanadiniz.com');
define('SMTP_PASSWORD', 'mail_app_password');
```

#### Phase 5: Bağımlılıklar
```bash
# Composer paketleri
composer install --no-dev --optimize-autoloader

# Vendor optimizasyonu
composer dump-autoload --optimize
```

---

## 🔧 Bakım, Güncelleme ve Destek

### 🛠️ Rutin Bakım İşlemleri

#### Haftalık Bakım
```bash
# 1. Veritabanı yedekleme
mysqldump -u root -p devamsizlik_db > backup_$(date +%Y%m%d).sql

# 2. Log temizleme
find /var/log/apache2/ -name "*.log" -mtime +30 -delete

# 3. Önbellek temizleme
apcu_clear_cache();
```

#### Aylık Bakım
```bash
# 1. Sistem güncellemeleri
sudo apt update && sudo apt upgrade

# 2. Güvenlik taraması
clamscan -r /var/www/html/

# 3. Performans analizi
mysql -u root -p -e "SHOW ENGINE INNODB STATUS;"
```

### 📊 İzleme ve Monitorizasyon

#### Sistem Metrikleri
- **Kullanıcı Aktivitesi**. Günlük giriş sayılarını takip ediyor.
- **Performans**. Sayfa yükleme sürelerini ölçüyorlar.
- **Hata Oranları**. 500 ve 404 hatalarını izliyorlar. İyi bir pratik.
- **Veritabanı**. Query performansını da takip ediyorlar. Her şeyi görünür kılmışlar.

#### Log Yönetimi
```php
// Sistem logları
error_log("Kullanıcı giriş: " . $kullanici_adi, 0);

// Hata takibi
try {
    // Veritabanı işlemi
} catch (Exception $e) {
    error_log("DB Hatası: " . $e->getMessage());
}
```

---

## 📞 Teknik Destek ve Sorun Giderme

### 🔍 Yaygın Sorunlar ve Çözümleri

#### Veritabanı Bağlantı Hataları
```php
// Sorun: Connection failed
// Çözüm: Bağlantı bilgilerini kontrol et
define('DB_HOST', 'localhost');
define('DB_USER', 'root');
define('DB_PASS', '');
define('DB_NAME', 'devamsizlik_db');
```

#### Mail Gönderim Problemleri
```php
// Sorun: SMTP authentication failed
// Çözüm: App password kullan
define('SMTP_PASSWORD', 'gmail_app_password'); // Normal şifre değil
```

#### Session Hataları
```php
// Sorun: Session not working
// Çözüm: Session path kontrolü
session_save_path('/tmp');
session_start();
```

### 📋 Destek Kanalları

- **Sistem Logları**. `/var/log/apache2/error.log` adresinde.
- **PHP Logları**. `/var/log/php_errors.log` adresinde.
- **Veritabanı Logları**. MySQL slow query log kullanıyorlar.
- **Uygulama Logları**. Kendi yazdıkları özel log sistemi var.

---

## 🎯 Gelecek Geliştirmeler ve Yol Haritası

### 🚀 Planlanan Özellikler

#### V2.0 Özellikleri
- **Mobil Uygulama**. React Native ile mobil uygulama yapılabilir.
- **API Entegrasyonu**. RESTful API desteği eklenebilir.
- **Real-time Bildirimler**. WebSocket teknolojisi kullanılacak. Güzel olacak.
- **Gelişmiş Raporlama**. Power BI entegrasyonu düşünülebilir.

#### V3.0 Özellikleri
- **Otomatik Bildirim Sistemi**. Dokuz gün devamsızlığa geldiğinde uyarı bildirimi gelecek, on güne geldiğinde otomatik olarak log düşecek.
- **Blockchain**. Veri güvenliği için düşünmüşler.
- **Cloud Deployment**. AWS veya Azure desteği planlamışlar.
- **Multi-tenant**. Çoklu kurum desteği gelecek. Ölçeklenebilirliği düşünmüşler.

---

## 📄 Lisans ve Kullanım Koşulları

### 📜 Yasal Bilgiler

Bu sistemi **eğitim kurumlarının** devamsızlık takibi için geliştirmişler. Kullanım şartlarını da belirtmişler.

- ✅ Eğitim kurumlarında ücretsiz kullanım
- ✅ Kamu kurumlarında kullanım
- ⚠️ Ticari kullanım için lisans gerekli
- 🔒 Kaynak kodu korunmaktadır

### 👨‍💻 Teknik Bilgiler

- **Geliştirme Tarihi**. 2025.
- **Son Güncelleme**. 2026 Şubat.
- **PHP Versiyonu**. 8.2+ kullanıyorlar. Güncel tutmuşlar.
- **Veritabanı**. MariaDB 10.4+.
- **Framework**. Kendi PHP framework'lerini yazmışlar.
- **Frontend**. Bootstrap 5 ve jQuery ile yapmışlar.

---

*Bu dokümantasyon Devamsızlık Takip Sistemi'nin tüm yönlerini detaylandırıyor. Kurulum kullanım bakım ve geliştirme için referans niteliğinde yazmışlar.*
