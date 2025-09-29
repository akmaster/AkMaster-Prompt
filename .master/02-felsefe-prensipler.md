<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Felsefe ve Temel Prensipler

Bu modül, proje geliştirme sürecinde uyulması gereken temel felsefe ve prensipleri tanımlar.

## Temel Prensipler

### 1. Kullanıcı Odaklılık
Her zaman projenin amacını ve kullanıcının ihtiyaçlarını anlayarak başla.

### 2. Sürdürülebilirlik ve Anlaşılırlık
Kod, senden sonra projeyi devralacak başka bir geliştiricinin (yapay zeka veya insan) kolayca anlayabileceği ve bakım yapabileceği şekilde temiz, sade ve iyi belgelenmiş olmalıdır.

### 3. Modern ve Şık Tasarım
Tasarımlar, güncel web trendlerine uygun, estetik, kullanıcı dostu ve tamamen duyarlı (responsive) olmalıdır.

### 4. Standartlara Uygunluk
Maksimum uyumluluk ve erişilebilirlik için genel kabul görmüş web standartlarına (HTML5, CSS3) sadık kal.

## Tasarım Stratejileri ve Proje Bazlı Kombinasyonlar

### Kurumsal ve Ciddi Projeler (Hukuk Bürosu, Finans Danışmanlığı)
- **Tasarım Anlayışı:** Minimalist, profesyonel ve güven veren.
- **Renk Paleti:** Genellikle mavi, gri, beyaz gibi nötr ve kurumsal renkler. Vurgu rengi olarak tek bir canlı renk kullanılabilir.
- **Font Kombinasyonu:** Okunaklı ve ciddi Serif (örn: Playfair Display, Merriweather) başlıklar ve Sans-serif (örn: Lato, Open Sans) paragraf metinleri.

### Yaratıcı ve Sanatsal Projeler (Portfolyo, Tasarım Ajansı, Fotoğrafçılık)
- **Tasarım Anlayışı:** Cesur, yenilikçi ve görsel odaklı. Asimetrik yerleşimler, büyük görseller ve animasyonlar kullanılabilir.
- **Renk Paleti:** Canlı, kontrastlı ve geniş bir renk yelpazesi. Siyah-beyaz temalar üzerine tek bir parlak renk de etkili olabilir.
- **Font Kombinasyonu:** Karakterli ve stilize fontlar (örn: Montserrat, Raleway, Oswald). El yazısı (script) fontları da vurgu için kullanılabilir.

### E-ticaret ve Satış Odaklı Siteler
- **Tasarım Anlayışı:** Kullanıcı dostu, temiz ve dönüşüm odaklı. Ürün görselleri ön planda olmalı, "Satın Al" butonları belirgin olmalıdır.
- **Renk Paleti:** Marka kimliğine uygun, dikkat çekici ve harekete geçirici renkler (örn: turuncu, kırmızı, yeşil).
- **Font Kombinasyonu:** Çok net ve okunaklı Sans-serif fontlar (örn: Roboto, Lato, Nunito Sans) tercih edilir. Fiyat ve ürün başlıkları belirgin olmalıdır.

### Blog ve İçerik Odaklı Siteler
- **Tasarım Anlayışı:** Okunabilirlik odaklı, sade ve göz yormayan. İçerik akışını bozacak dikkat dağıtıcı unsurlardan kaçınılmalıdır.
- **Renk Paleti:** Genellikle açık tonlarda bir arka plan ve koyu metin rengi. Başlıklar ve linkler için yumuşak vurgu renkleri.
- **Font Kombinasyonu:** Uzun metin okumaları için ideal, göz yormayan Serif fontlar (örn: Lora, PT Serif) veya yüksek okunabilirliğe sahip Sans-serif fontlar (örn: Open Sans).

## Tasarımsal Bütünlük ve Tutarlılık Standartları

### Tasarım Tutarlılığı Kontrolü
Her yeni sayfa veya bölüm geliştirilirken, mevcut sayfaların tasarım stillerini kontrol et ve tutarlılığı sağla.

### Stil Kontrol Listesi
- **Renk Paleti Uyumu:** Yeni sayfada kullanılan renkler, proje başında belirlenen renk paletinde bulunmalı
- **Font Tutarlılığı:** Başlık, alt başlık ve paragraf fontları tüm sayfalarda aynı olmalı
- **Spacing Tutarlılığı:** Margin, padding ve gap değerleri standart ölçülerde olmalı
- **Component Tutarlılığı:** Butonlar, form elemanları, kartlar gibi bileşenler aynı stilde olmalı
- **Layout Tutarlılığı:** Grid sistem, container genişlikleri ve breakpoint'ler tutarlı olmalı

### Mevcut Stil Analizi
Yeni bölüm geliştirmeden önce renk değişkenleri, font ailesi, spacing sistemi ve component stillerini kontrol et

### Tasarım Sistemi Dokümantasyonu
Her projede tutarlılık için tasarım sistemi oluştur (renk paleti, typography, spacing, border radius, shadow sistemi)

### Component Tutarlılığı
Aynı türdeki bileşenler aynı stilde olmalı (butonlar, kartlar, form elemanları)

### Responsive Tutarlılık
Tüm sayfalar aynı breakpoint'lerde aynı şekilde davranmalı (Mobile, Tablet, Desktop)

## Dil Yerelleştirme ve Uluslararasılaştırma (i18n/l10n)

### ZORUNLU: Component Tabanlı Dil Sistemi (Tek Dil İçin Bile)
**ÖNEMLİ:** Projede tek dil olsa bile, sonradan dil ekleme kolaylığı için mutlaka component yapıda dil sistemi kurulmalıdır. Bu yaklaşım gelecekteki genişletmeleri kolaylaştırır ve kod yapısını daha sürdürülebilir hale getirir.

### Çoklu Dil Desteği Seçenekleri
- **URL Tabanlı (SEO Önerilen):** Her dil ayrı URL'de (`/tr/`, `/en/`, `/fr/`)
- **Subdomain Tabanlı:** Dil bazlı subdomain'ler (`tr.site.com`, `en.site.com`)
- **Query Parameter Tabanlı:** Tek dosya yönetimi (`?lang=tr`)

### Dil Değiştirme Sistemi
- **Cookie + URL Kombinasyonu:** Kullanıcı tercihi hatırlanır, SEO dostu
- **Otomatik Dil Algılama:** Browser dilini algıla ve uygun dile yönlendir

### RTL (Right-to-Left) Dil Desteği
- **RTL Diller:** Arapça, Farsça, İbranice, Urduca
- **CSS RTL Desteği:** `[dir="rtl"]` selector'ları ile RTL stilleri
- **HTML RTL Desteği:** `dir="auto"` ve `lang` attribute'ları

### Kültürel Uyarlama
- **Tarih Formatları:** Ülkeye göre tarih formatı (MM/DD/YYYY, DD/MM/YYYY, YYYY-MM-DD)
- **Sayı Formatları:** Binlik ayırıcı ve ondalık işareti (1,234.56 vs 1.234,56)
- **Para Birimi Formatları:** Para birimi sembolü ve formatı ($1,234.56, €1.234,56)
- **Telefon Formatları:** Ülkeye göre telefon numarası formatı

## Frontend Dil Yerelleştirme Teknikleri

### Component Tabanlı Dil Dosyası Yapısı (Tek Dil İçin Bile Zorunlu)
```
/components/language/
├── manager/              # Dil yönetim componentleri
│   ├── language-manager.js
│   ├── language-manager.css
│   └── language-manager.php
├── files/               # Dil dosyaları (component olarak)
│   ├── tr.json          # Türkçe component (ana dil)
│   ├── en.json          # İngilizce component (gelecek için hazır)
│   ├── fr.json          # Fransızca component (gelecek için hazır)
│   ├── ar.json          # Arapça component (RTL - gelecek için hazır)
│   └── de.json          # Almanca component (gelecek için hazır)
├── ui/                  # Dil değiştirici UI componentleri
│   ├── language-selector.html
│   ├── language-selector.css
│   └── language-selector.js
└── utils/               # Dil yardımcı fonksiyonları
    ├── translation-helper.js
    ├── rtl-helper.css
    └── language-validator.js
```

**NOT:** Tek dil projesi olsa bile, gelecekte dil ekleme kolaylığı için tüm dil dosyaları component olarak oluşturulur. Aktif olmayan dil dosyaları boş bırakılır veya temel yapı ile hazırlanır.

### Component Tabanlı Dil Dosyası Formatı
Her dil dosyası component olarak organize edilir:

#### Dil Dosyası Component Yapısı
```json
{
  "component_info": {
    "name": "turkish-language",
    "version": "1.0.0",
    "description": "Türkçe dil component'i",
    "rtl": false,
    "charset": "utf-8"
  },
  "translations": {
    "common": {
      "welcome": "Hoş Geldiniz",
      "loading": "Yükleniyor...",
      "error": "Hata"
    },
    "navigation": {
      "home": "Ana Sayfa",
      "about": "Hakkımızda",
      "contact": "İletişim"
    },
    "forms": {
      "name": "Ad",
      "email": "E-posta",
      "submit": "Gönder"
    },
    "seo": {
      "title": "Site Başlığı",
      "description": "Site Açıklaması",
      "keywords": "Anahtar Kelimeler"
    }
  }
}
```

#### Component Başlığı Zorunluluğu
Her dil dosyası component başlığı ile başlamalıdır:
```json
{
  "component_info": {
    "name": "turkish-language",
    "version": "1.0.0",
    "description": "Türkçe dil component'i",
    "rtl": false,
    "charset": "utf-8",
    "author": "AI Assistant",
    "created": "2024-01-15",
    "last_updated": "2024-01-15",
    "dependencies": [],
    "master_index_required": true
  }
}
```

### Modüler Yapı Özellikleri
- **Modüler Yapı:** Her dil kendi component'i olarak izole edilir
- **Gelecek Genişletme:** Yeni diller kolayca component olarak eklenebilir
- **Component İzolasyonu:** Her dil dosyası kendi namespace'inde çalışır

### JavaScript Dil Yönetimi
LanguageManager component'i ile dil algılama, çeviri yükleme ve RTL desteği

### HTML Dil Desteği
`data-translate` attribute'ları ile çeviri elementleri ve dil değiştirici component'i

## Backend Dil Yerelleştirme Teknikleri

### Component Tabanlı Veritabanı Yapısı
languages, translations, content tabloları ile çoklu dil desteği

### PHP Dil Yönetimi Component'i
LanguageManager component'i ile dil algılama, çeviri yükleme, RTL desteği ve kültürel formatlar

### Dil Component Yönetimi
- **Dil Dosyası Yükleme:** Component tabanlı dil dosyası yükleme sistemi
- **Dil Validasyonu:** Her dil component'inin doğruluğunu kontrol etme
- **Component Bağımlılık Yönetimi:** Dil component'leri arası bağımlılık kontrolü
- **Otomatik Dil Algılama:** Browser dilini algılama ve uygun component'i yükleme

### Admin Panel Dil Yönetimi
- **Dil Ekleme/Çıkarma:** Yeni dil ekleme, mevcut dili deaktive etme
- **Çeviri Editörü:** WYSIWYG çeviri editörü
- **Toplu Çeviri:** Birden fazla içeriği aynı anda çevirme
- **Çeviri Durumu:** Hangi içeriklerin çevrildiğini takip
- **Otomatik Çeviri:** Google Translate API entegrasyonu
- **Çevirmen Yönetimi:** Çevirmen atama ve yetki yönetimi

## SEO Dil Yerelleştirme Optimizasyonu

### Hreflang Etiketleri
Her dil için hreflang etiketleri ve x-default

### Dil Bazlı Sitemap
Her dil için ayrı sitemap dosyaları

### Dil Bazlı Meta Taglar
Her dil için özel meta taglar

### Canonical URL'ler
Her dil için doğru canonical URL'ler
