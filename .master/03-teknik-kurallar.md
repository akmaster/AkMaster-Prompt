<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Teknik Kurallar ve Mimari Standartlar

Bu modül, proje geliştirme sürecinde uyulması gereken teknik kurallar ve mimari standartları tanımlar.

## Teknoloji Yığını (Tech Stack)

### Proje Tipine Göre Teknoloji Seçimi
Projenin başında, sitenin amacına uygun teknoloji kombinasyonları değerlendirilir ve kullanıcıya sunulur.

#### Standart İçerik Siteleri (Blog, Portfolyo, Kurumsal)
- **Öneri:** HTML, CSS, JavaScript (Vanilla) veya Statik Site Üreticileri (Jekyll, Hugo).
- **Hosting Uyumu:** Tüm paylaşımlı hosting'lerle **mükemmel** uyumludur. Sunucuya özel yapılandırma gerektirmez.

#### Dinamik Siteler ve CMS (İçerik Yönetim Sistemi)
- **Öneri:** PHP + MySQL (Örn: WordPress). Kullanıcıların içerik yönetebileceği admin paneli sunar.
- **Hosting Uyumu:** Paylaşımlı hosting'lerle **mükemmel** uyumludur ve genellikle tek tıkla kurulum desteği bulunur.

#### Modern Web Uygulamaları (Yoğun Etkileşimli)
- **Öneri:** Node.js (Express) veya Python (Django/Flask) tabanlı yığınlar.
- **Hosting Uyumu:** Paylaşımlı hosting için **uygun değildir**. VPS, Cloud veya PaaS (Heroku, Vercel) gibi esnek altyapılar gerektirir.

#### Varsayılan Teknoloji
Kullanıcı özel bir talepte bulunmazsa veya proje basit bir içerik sitesi ise, maksimum uyumluluk için **HTML, CSS ve JavaScript** varsayılan olarak kullanılır.

## Component-Based Modüler Mimari (Tüm Dosya Türleri İçin)

### Component-First Yaklaşım
Her dosya türü için component bazlı yapı oluştur. Bu yaklaşım tüm projelerde (HTML, CSS, JS, PHP, Python, Node.js, React, Vue, Angular vb.) uygulanmalıdır.

### ZORUNLU COMPONENT KURALI
Dosya uzantısı farketmeksizin, her dosya mutlaka component yapısında olmalıdır. Uzun kodlu dosyalar component sistemine aykırıdır ve kesinlikle oluşturulmamalıdır.

### Universal Component Yapısı
Her component, kendi dosya türüne uygun şekilde organize edilmelidir:
- **Frontend Components:** HTML, CSS, JS, TS, JSX, Vue, Svelte dosyaları
- **Backend Components:** PHP, Python, Node.js, Java, C# dosyaları
- **Database Components:** SQL, NoSQL, migration dosyaları
- **Configuration Components:** JSON, YAML, XML, INI dosyaları
- **Documentation Components:** MD, TXT, PDF dosyaları

### Component Klasör Yapısı
```
/components/
  ├── ui/          # UI componentleri (buttons, forms, cards)
  ├── layout/      # Layout componentleri (header, footer, sidebar)
  ├── sections/    # Sayfa bölümleri (hero, about, contact)
  ├── backend/     # Backend componentleri (api, database, services)
  ├── utils/       # Yardımcı fonksiyonlar
  └── config/      # Konfigürasyon dosyaları
```

### Component Naming Convention (Tüm Dosya Türleri)
- **Dosya Adlandırma:** `component-name.file-extension` formatında
- **Klasör Adlandırma:** `kebab-case` formatında
- **Component İçi Adlandırma:** Her dosya türüne uygun naming convention
- **Örnekler:** `contact-form.html`, `contact-form.css`, `contact-form.js`, `contact-form.php`

### Component Bağımlılık Yönetimi
- **Her component kendi bağımlılıklarını belirtmeli**
- **Cross-platform uyumluluk sağlanmalı**
- **Dosya türü fark etmeksizin aynı component mantığı uygulanmalı**
- **Component içi dokümantasyon zorunlu**

### Backend Modüler Mimari
- **Fonksiyon Dosyalarını Mantıksal Parçalara Bölme:** Büyük dosyaları işlevlerine göre ayrı componentlere böl
- **Modüler Fonksiyon Yapısı:** Her component kendi sorumluluğuna odaklanmalı
- **Dosya Bağımlılık Yönetimi:** Her dosyanın başında bağımlılıklarını belirt

## Zorunlu Dosya Başlığı Sistemi (Tüm Dosya Türleri İçin)

### Master Index Kontrol Zorunluluğu
Her dosyanın en üstüne aşağıdaki uyarı eklenmelidir:

#### PHP Dosyaları İçin Başlık
```php
<?php
/**
 * ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
 * 
 * Bu dosya component sistemine uygun olarak oluşturulmuştur.
 * Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
 * 
 * Component Adı: [COMPONENT_ADI]
 * Dosya Türü: [DOSYA_TÜRÜ]
 * Amaç: [DOSYA_AMACI]
 * 
 * @author AI Assistant
 * @version 1.0
 * @created [TARIH]
 * @last_updated [TARIH]
 */
```

#### HTML Dosyaları İçin Başlık
```html
<!--
⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!

Bu dosya component sistemine uygun olarak oluşturulmuştur.
Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.

Component Adı: [COMPONENT_ADI]
Dosya Türü: HTML
Amaç: [DOSYA_AMACI]

@author AI Assistant
@version 1.0
@created [TARIH]
@last_updated [TARIH]
-->
```

#### CSS Dosyaları İçin Başlık
```css
/*
⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!

Bu dosya component sistemine uygun olarak oluşturulmuştur.
Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.

Component Adı: [COMPONENT_ADI]
Dosya Türü: CSS
Amaç: [DOSYA_AMACI]

@author AI Assistant
@version 1.0
@created [TARIH]
@last_updated [TARIH]
*/
```

#### JavaScript Dosyaları İçin Başlık
```javascript
/**
 * ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
 * 
 * Bu dosya component sistemine uygun olarak oluşturulmuştur.
 * Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
 * 
 * Component Adı: [COMPONENT_ADI]
 * Dosya Türü: JavaScript
 * Amaç: [DOSYA_AMACI]
 * 
 * @author AI Assistant
 * @version 1.0
 * @created [TARIH]
 * @last_updated [TARIH]
 */
```

## Uzun Kodlu Dosya Engelleme Kuralları

### Maksimum Sınırlar
- **Maksimum Satır Sınırı:** Her component dosyası maksimum 200 satır olmalıdır
- **Fonksiyon Sınırı:** Her component dosyasında maksimum 10 fonksiyon olmalıdır
- **Dosya Boyutu Sınırı:** Her component dosyası maksimum 10KB olmalıdır

### Component Bölme Zorunluluğu
Bu sınırları aşan dosyalar mutlaka alt componentlere bölünmelidir

### Otomatik Kontrol
AI, her dosya oluştururken bu sınırları kontrol etmeli ve aşarsa uyarı vermelidir

## Fonksiyon ve CSS Çakışma Engelleme Sistemi

### Namespace Zorunluluğu
Tüm PHP fonksiyonları mutlaka namespace içinde olmalıdır

### Global Fonksiyon Yasak
Global scope'ta fonksiyon tanımlaması yasaktır

### CSS Component Prefix
Her CSS sınıfı component adı ile prefix'lenmelidir

### BEM Metodolojisi
CSS sınıfları BEM (Block-Element-Modifier) metodolojisine uygun olmalıdır

### Çakışma Kontrolü
Aynı isimde fonksiyon veya CSS sınıfı varsa uyarı verilmeli ve engellenmelidir

## Dosya Bağımlılık Yönetimi

### Bağımlılık Haritası
Her dosyanın başında kullandığı dosyalar belirtilmelidir

### Otomatik Bağımlılık Kontrolü
Dosya oluşturma/güncelleme öncesi bağımlılık çakışmaları kontrol edilmelidir

### Component İzolasyonu
Her component kendi dosyalarında izole olmalıdır

### Cross-Component Yasak
Bir component başka component'in iç dosyalarına doğrudan erişmemelidir

## CSS Component Sistemi

### Component CSS Ayrımı
Her component'in kendi CSS dosyası olmalıdır

### Global CSS Sınırı
Global CSS sadece değişkenler ve reset için kullanılmalıdır

### CSS Yükleme Optimizasyonu
Component CSS'leri sadece o component kullanıldığında yüklenmelidir

### CSS Sınıf Çakışma Kontrolü
Aynı CSS sınıfı farklı dosyalarda varsa uyarı verilmelidir

## PHP Namespace ve Autoloader Sistemi

### Namespace Zorunluluğu
Tüm PHP sınıfları mutlaka namespace içinde olmalıdır

### Autoloader Sistemi
Otomatik sınıf yükleme sistemi kullanılmalıdır

### Sınıf Çakışma Kontrolü
Aynı isimde sınıf varsa uyarı verilmelidir

### Dependency Injection
Bağımlılıklar constructor ile enjekte edilmelidir

## Kodlama Stili ve Yapısı

### Mantıksal Bloklar
Kodu, okunabilirliği artırmak için mantıksal bölümlere ayır. Her bölümün başlangıcını ve bitişini belirten yorum satırları kullan (örn: `<!-- Header Başlangıcı -->` ... `<!-- Header Bitişi -->`).

### Sadelik
Karmaşık ve anlaşılması zor kodlardan kaçın. Bir işi yapmanın daha basit bir yolu varsa onu tercih et.

### Dosya ve Kod Dokümantasyonu
- **Dosya Başlığı:** Oluşturulan her dosyanın en üstüne, dosyanın amacını, ne işe yaradığını ve varsa bağımlı olduğu diğer dosyaları açıklayan bir yorum bloğu ekle.
- **İçindekiler (Opsiyonel):** Büyük ve karmaşık dosyalarda, dosyanın en üstüne önemli fonksiyonların veya bölümlerin bir listesini içeren bir "İçindekiler" bölümü ekleyerek navigasyonu kolaylaştır.

## Güvenlik Standartları

### XSS Koruması
Kullanıcı girdilerini her zaman sanitize et ve HTML encoding uygula.

### CSRF Koruması
Form işlemlerinde CSRF token kullan ve referrer kontrolü yap.

### SQL Injection Koruması
Prepared statements kullan, kullanıcı girdilerini doğrudan SQL sorgularına ekleme.

### HTTPS Zorunluluğu
Tüm siteler SSL sertifikası ile güvenli bağlantı kullanmalıdır.

### Input Validation
Tüm form alanları için client-side ve server-side validation uygula.

## PHP/MySQL Projeleri için PDO Uyumlu Kodlama Standartları

### PDO Zorunluluğu
MySQL ile çalışan tüm PHP projelerinde PDO kullanılmalıdır

### Prepared Statements
SQL injection koruması için prepared statements kullan

### Güvenli CRUD İşlemleri
Tüm veritabanı işlemlerinde parametreli sorgular kullan

### Hata Yönetimi
Try-catch blokları ile hata yakalama ve logging

### Transaction Yönetimi
Çoklu işlemler için transaction kullan

## Performans Optimizasyonu

### Görsel Optimizasyonu
WebP formatı kullan, lazy loading uygula, görsel boyutlarını optimize et.

### Kod Minifikasyonu
CSS, JavaScript ve HTML dosyalarını minify et.

### Compression
Gzip/Brotli sıkıştırma etkinleştir.

### Core Web Vitals
LCP, FID, CLS metriklerini optimize et.

### Caching
Browser cache ve CDN kullanımını optimize et.

## SEO ve Meta Veri Yönetimi

### Meta Taglar
Her sayfa için unique title, description ve keywords ekle.

### Open Graph
Facebook ve sosyal medya paylaşımları için OG tagları ekle.

### Twitter Cards
Twitter paylaşımları için Twitter Card meta verileri ekle.

### Yapılandırılmış Veri
Schema.org markup'ları kullan.

### XML Sitemap
Arama motorları için XML sitemap oluştur.

### Robots.txt
Arama motoru botları için robots.txt dosyası ekle.

## Hata Yönetimi ve Test Protokolleri

### JavaScript Error Handling
Try-catch blokları ve global error handler kullan.

### Hata Sayfaları
404, 500 gibi HTTP hata kodları için özel sayfalar oluştur.

### Form Validation
Real-time validation ve kullanıcı dostu hata mesajları.

### Cross-browser Testing
Chrome, Firefox, Safari, Edge tarayıcılarında test et.

### Responsive Testing
Farklı ekran boyutlarında test et.

### User Feedback
Loading states, success/error mesajları göster.

## Erişilebilirlik (Accessibility) Standartları

### WCAG 2.1 Uyumluluğu
AA seviyesinde erişilebilirlik standartlarına uy.

### Klavye Navigasyonu
Tüm interaktif elementler klavye ile erişilebilir olmalı.

### Screen Reader Uyumluluğu
ARIA labels, roles ve properties kullan.

### Renk Kontrastı
Minimum 4.5:1 kontrast oranını sağla.

### Font Boyutu
Minimum 16px font boyutu kullan.

### Alt Metinler
Tüm görseller için anlamlı alt text ekle.

## Modern CSS Standartları

### CSS Grid
Karmaşık layout'lar için CSS Grid kullan.

### Flexbox
Esnek yerleşimler için Flexbox kullan.

### CSS Variables
Dinamik değerler için CSS custom properties kullan.

### Mobile-First Design
Önce mobil, sonra desktop yaklaşımı benimse.

### Modern CSS Features
Container queries, aspect-ratio, clamp() gibi modern özellikleri kullan.
