<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Güvenli Özellik Ekleme ve Mevcut Sistem Koruması

Bu modül, yeni özellikler eklerken mevcut sisteme zarar vermemek için uyulması gereken kritik kuralları tanımlar.

## Özellik Ekleme Öncesi Kontrol Listesi

### Mevcut Sistem Analizi
- ✅ Mevcut kod yapısını detaylı analiz et
- ✅ Bağımlılıkları tespit et
- ✅ Kritik fonksiyonları belirle
- ✅ Test edilmiş kod bloklarını işaretle

### Etki Analizi
- ✅ Yeni özelliğin hangi dosyaları etkileyeceğini belirle
- ✅ Mevcut fonksiyonlara etkisini değerlendir
- ✅ Veritabanı değişikliklerini planla
- ✅ API endpoint'lerini kontrol et

## Güvenli Kod Değişikliği Protokolü

### Backup Oluşturma (Zorunlu)
- **Tam Sistem Backup:** Değişiklik öncesi tam sistem backup'ı al
- **Kritik Dosya Yedekleme:** Kritik dosyaları ayrı yedekle
- **Veritabanı Snapshot:** Veritabanı snapshot'ı oluştur
- **Backup Saklama:** Backup'ları `/temp-files/backups/` klasöründe sakla

### Test Ortamı Hazırlama
- **Test Environment:** Yeni özelliği test ortamında dene
- **Mevcut Fonksiyon Testi:** Mevcut fonksiyonları test et
- **Edge Case Kontrolü:** Edge case'leri kontrol et
- **Performance Impact:** Performance impact'i ölç

## Kod Değişikliği Kuralları

### Mevcut Kodu Koruma
- ✅ Mevcut fonksiyonları değiştirme, yeni fonksiyon oluştur
- ✅ Kritik kod bloklarına dokunma
- ✅ Test edilmiş kodları bozma
- ✅ Sadece gerekli yerleri değiştir

### Geriye Uyumluluk
- ✅ Eski API'leri desteklemeye devam et
- ✅ Mevcut veri yapılarını koru
- ✅ Eski parametreleri kabul et
- ✅ Deprecated uyarıları ekle

## Veritabanı Değişikliği Güvenliği

### Migration Stratejisi
- ✅ Mevcut veriyi koruyan migration'lar yaz
- ✅ Rollback planı hazırla
- ✅ Veri kaybını önleyici kontroller ekle
- ✅ Test veritabanında dene

### Tablo Değişiklikleri
- ✅ Yeni kolonlar NULL olarak ekle
- ✅ Mevcut veriyi etkilemeyen değişiklikler yap
- ✅ Index'leri dikkatli ekle
- ✅ Foreign key'leri güvenli şekilde ekle

## API ve Endpoint Güvenliği

### Mevcut Endpoint'leri Koruma
- ✅ Eski endpoint'leri değiştirme
- ✅ Yeni versiyonlar oluştur (v2, v3)
- ✅ Backward compatibility sağla
- ✅ Deprecation notice ekle

### Yeni Endpoint Oluşturma
- ✅ RESTful standartlara uy
- ✅ Güvenlik kontrollerini ekle
- ✅ Rate limiting uygula
- ✅ Input validation yap

## Frontend Değişiklik Güvenliği

### CSS Değişiklikleri
- ✅ Mevcut stilleri bozma
- ✅ Yeni CSS sınıfları oluştur
- ✅ Responsive tasarımı koru
- ✅ Cross-browser uyumluluğu test et

### JavaScript Değişiklikleri
- ✅ Global değişkenleri kirletme
- ✅ Mevcut event listener'ları bozma
- ✅ Namespace kullan
- ✅ Error handling ekle

## Hata Yakalama ve Geri Alma

### Try-Catch Blokları
- ✅ Tüm kritik işlemleri try-catch ile sar
- ✅ Hata durumunda rollback yap
- ✅ Kullanıcıya anlamlı hata mesajı ver
- ✅ Hataları logla

### Geri Alma Mekanizması
- ✅ Her değişiklik için rollback planı hazırla
- ✅ Backup'tan geri yükleme scripti yaz
- ✅ Veritabanı rollback migration'ları hazırla
- ✅ Hızlı geri alma prosedürü oluştur

## Test Stratejisi

### Unit Testler
- ✅ Yeni özellik için unit test yaz
- ✅ Mevcut testleri güncelle
- ✅ Edge case'leri test et
- ✅ Mock data kullan

### Integration Testler
- ✅ Sistem entegrasyonunu test et
- ✅ API endpoint'lerini test et
- ✅ Veritabanı işlemlerini test et
- ✅ Cross-module etkileşimleri kontrol et

## Deployment Güvenliği

### Aşamalı Deployment
- ✅ Önce test ortamında dene
- ✅ Staging ortamında test et
- ✅ Canlı ortamda aşamalı yayınla
- ✅ Monitoring ile takip et

### Rollback Hazırlığı
- ✅ Hızlı rollback planı hazırla
- ✅ Database rollback scripti hazırla
- ✅ File rollback prosedürü oluştur
- ✅ Emergency contact listesi hazırla

## Kod Review ve Onay Süreci

### Değişiklik Onayı
- ✅ Kritik değişiklikler için kullanıcı onayı al
- ✅ Risk analizi yap
- ✅ Etki değerlendirmesi sun
- ✅ Alternatif çözümler öner

### Code Review Checklist
- ✅ Mevcut kodu bozuyor mu?
- ✅ Performance'ı etkiliyor mu?
- ✅ Güvenlik açığı oluşturuyor mu?
- ✅ Test coverage yeterli mi?

## Monitoring ve Alerting

### Sistem İzleme
- ✅ Değişiklik sonrası sistem durumunu izle
- ✅ Error rate'i takip et
- ✅ Performance metriklerini ölç
- ✅ User experience'i değerlendir

### Alert Sistemi
- ✅ Kritik hatalar için alert kur
- ✅ Performance düşüşü için uyarı ver
- ✅ Anormal davranışları tespit et
- ✅ Otomatik rollback tetikleyicileri ekle

## Dokümantasyon ve İletişim

### Değişiklik Dokümantasyonu
- ✅ Yapılan değişiklikleri detaylı dokümante et
- ✅ Etkilenen dosyaları listele
- ✅ Yeni özellik kullanım kılavuzu yaz
- ✅ Breaking change'leri belirt

### Kullanıcı Bilgilendirme
- ✅ Değişiklikleri önceden duyur
- ✅ Migration rehberi hazırla
- ✅ FAQ bölümü güncelle
- ✅ Support kanallarını hazırla

## Risk Yönetimi

### Risk Değerlendirmesi
- ✅ Yüksek riskli değişiklikleri belirle
- ✅ Mitigation stratejileri geliştir
- ✅ Contingency planları hazırla
- ✅ Risk seviyesine göre onay süreci uygula

### Emergency Response
- ✅ Acil durum prosedürleri oluştur
- ✅ Hızlı müdahale ekibi belirle
- ✅ Communication planı hazırla
- ✅ Recovery time objective (RTO) belirle

## Özellik Ekleme Sonrası Kontroller

### Post-Deployment Testing
- ✅ Canlı ortamda smoke test yap
- ✅ Kritik user journey'leri test et
- ✅ Performance benchmark'ları kontrol et
- ✅ Error log'larını incele

### Monitoring ve Optimizasyon
- ✅ İlk 24 saat yoğun monitoring yap
- ✅ User feedback'lerini topla
- ✅ Performance bottleneck'leri tespit et
- ✅ Gerekirse hotfix uygula

## Özellik Ekleme Yasakları

### Kesinlikle Yapılmaması Gerekenler
- ❌ Mevcut çalışan kodu değiştirme
- ❌ Kritik fonksiyonları silme
- ❌ Veritabanı yapısını bozma
- ❌ API contract'larını kırma
- ❌ Güvenlik kontrollerini bypass etme
- ❌ Test edilmemiş kodu canlıya alma
- ❌ Backup almadan değişiklik yapma

## Güvenli Özellik Ekleme Süreci

### 1. Planlama Aşaması
- **İhtiyaç Analizi:** Özellik ihtiyacını analiz et
- **Etki Değerlendirmesi:** Mevcut sisteme etkisini değerlendir
- **Risk Analizi:** Potansiyel riskleri belirle
- **Kaynak Planlaması:** Gerekli kaynakları planla
- **Zaman Çizelgesi:** Gerçekçi zaman çizelgesi oluştur

### 2. Tasarım Aşaması
- **Mimari Tasarım:** Sistem mimarisini tasarla
- **API Tasarımı:** API endpoint'lerini tasarla
- **Veritabanı Tasarımı:** Veritabanı değişikliklerini tasarla
- **UI/UX Tasarımı:** Kullanıcı arayüzünü tasarla
- **Güvenlik Tasarımı:** Güvenlik gereksinimlerini tasarla

### 3. Geliştirme Aşaması
- **Test Ortamı:** Test ortamını hazırla
- **Kod Geliştirme:** Özelliği geliştir
- **Unit Testing:** Unit testleri yaz
- **Integration Testing:** Entegrasyon testleri yap
- **Code Review:** Kod incelemesi yap

### 4. Test Aşaması
- **Functional Testing:** Fonksiyonellik testleri
- **Performance Testing:** Performans testleri
- **Security Testing:** Güvenlik testleri
- **User Acceptance Testing:** Kullanıcı kabul testleri
- **Regression Testing:** Regresyon testleri

### 5. Deployment Aşaması
- **Staging Deployment:** Staging ortamında test
- **Production Deployment:** Canlı ortamda yayınlama
- **Monitoring:** İzleme ve takip
- **Rollback Plan:** Geri alma planı
- **Documentation:** Dokümantasyon güncelleme

## Güvenli Kod Değişikliği Örnekleri

### PHP Özellik Ekleme Örneği
```php
<?php
/**
 * ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
 * 
 * Bu dosya component sistemine uygun olarak oluşturulmuştur.
 * Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
 * 
 * Component Adı: user-notification
 * Dosya Türü: PHP
 * Amaç: Kullanıcı bildirim sistemi
 * 
 * @author AI Assistant
 * @version 1.0
 * @created 2024-01-15
 * @last_updated 2024-01-15
 */

// Mevcut kodu koruma - yeni fonksiyon ekleme
if (!function_exists('sendUserNotification')) {
    function sendUserNotification($userId, $message, $type = 'info') {
        // Yeni özellik implementasyonu
        // Mevcut sistemi etkilemeyen güvenli kod
    }
}

// Deprecated uyarısı ekleme
if (function_exists('oldNotificationFunction')) {
    trigger_error('oldNotificationFunction is deprecated. Use sendUserNotification instead.', E_USER_DEPRECATED);
}
```

### CSS Özellik Ekleme Örneği
```css
/*
⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!

Bu dosya component sistemine uygun olarak oluşturulmuştur.
Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.

Component Adı: notification-component
Dosya Türü: CSS
Amaç: Bildirim bileşeni stilleri

@author AI Assistant
@version 1.0
@created 2024-01-15
@last_updated 2024-01-15
*/

/* Yeni özellik - mevcut stilleri etkilemez */
.notification-component {
    /* Yeni stil kuralları */
}

/* Mevcut stilleri koruma */
.existing-component {
    /* Mevcut stiller değiştirilmez */
}
```

### JavaScript Özellik Ekleme Örneği
```javascript
/**
 * ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
 * 
 * Bu dosya component sistemine uygun olarak oluşturulmuştur.
 * Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
 * 
 * Component Adı: notification-manager
 * Dosya Türü: JavaScript
 * Amaç: Bildirim yönetim sistemi
 * 
 * @author AI Assistant
 * @version 1.0
 * @created 2024-01-15
 * @last_updated 2024-01-15
 */

// Namespace kullanarak global kirliliği önleme
window.NotificationManager = window.NotificationManager || {};

// Yeni özellik - mevcut kodu etkilemez
window.NotificationManager.show = function(message, type) {
    // Yeni özellik implementasyonu
    // Mevcut sistemi etkilemeyen güvenli kod
};

// Mevcut fonksiyonları koruma
if (window.NotificationManager.oldShow) {
    console.warn('oldShow is deprecated. Use show instead.');
}
```

## Sürekli İyileştirme

### Feedback Sistemi
- **Kullanıcı Geri Bildirimi:** Kullanıcı geri bildirimlerini topla
- **Performance Monitoring:** Performans izleme
- **Error Tracking:** Hata takibi
- **Usage Analytics:** Kullanım analitiği

### İyileştirme Süreci
- **Veri Toplama:** Performans ve kullanım verilerini topla
- **Analiz:** Verileri analiz et ve iyileştirme fırsatlarını belirle
- **Planlama:** İyileştirme planı oluştur
- **Uygulama:** İyileştirmeleri uygula
- **Değerlendirme:** Sonuçları değerlendir
