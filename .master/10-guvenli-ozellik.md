<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Güvenli Özellik Ekleme ve Mevcut Sistem Koruması

## Özellik Ekleme Öncesi Kontrol Listesi

### Mevcut Sistem Analizi
*   ✅ Mevcut kod yapısını detaylı analiz et
*   ✅ Bağımlılıkları tespit et
*   ✅ Kritik fonksiyonları belirle
*   ✅ Test edilmiş kod bloklarını işaretle

### Etki Analizi
*   ✅ Yeni özelliğin hangi dosyaları etkileyeceğini belirle
*   ✅ Mevcut fonksiyonlara etkisini değerlendir
*   ✅ Veritabanı değişikliklerini planla
*   ✅ API endpoint'lerini kontrol et

## Güvenli Kod Değişikliği Protokolü

### Backup Oluşturma (Zorunlu)
*   Değişiklik öncesi tam sistem backup'ı al
*   Kritik dosyaları ayrı yedekle
*   Veritabanı snapshot'ı oluştur
*   Backup'ları `/temp-files/backups/` klasöründe sakla

### Test Ortamı Hazırlama
*   Yeni özelliği test ortamında dene
*   Mevcut fonksiyonları test et
*   Edge case'leri kontrol et
*   Performance impact'i ölç

## Kod Değişikliği Kuralları

### Mevcut Kodu Koruma
*   ✅ Mevcut fonksiyonları değiştirme, yeni fonksiyon oluştur
*   ✅ Kritik kod bloklarına dokunma
*   ✅ Test edilmiş kodları bozma
*   ✅ Sadece gerekli yerleri değiştir

### Geriye Uyumluluk
*   ✅ Eski API'leri desteklemeye devam et
*   ✅ Mevcut veri yapılarını koru
*   ✅ Eski parametreleri kabul et
*   ✅ Deprecated uyarıları ekle

## Veritabanı Değişikliği Güvenliği

### Migration Stratejisi
*   ✅ Mevcut veriyi koruyan migration'lar yaz
*   ✅ Rollback planı hazırla
*   ✅ Veri kaybını önleyici kontroller ekle
*   ✅ Test veritabanında dene

### Tablo Değişiklikleri
*   ✅ Yeni kolonlar NULL olarak ekle
*   ✅ Mevcut veriyi etkilemeyen değişiklikler yap
*   ✅ Index'leri dikkatli ekle
*   ✅ Foreign key'leri güvenli şekilde ekle

## API ve Endpoint Güvenliği

### Mevcut Endpoint'leri Koruma
*   ✅ Eski endpoint'leri değiştirme
*   ✅ Yeni versiyonlar oluştur (v2, v3)
*   ✅ Backward compatibility sağla
*   ✅ Deprecation notice ekle

### Yeni Endpoint Oluşturma
*   ✅ RESTful standartlara uy
*   ✅ Güvenlik kontrollerini ekle
*   ✅ Rate limiting uygula
*   ✅ Input validation yap

## Frontend Değişiklik Güvenliği

### CSS Değişiklikleri
*   ✅ Mevcut stilleri bozma
*   ✅ Yeni CSS sınıfları oluştur
*   ✅ Responsive tasarımı koru
*   ✅ Cross-browser uyumluluğu test et

### JavaScript Değişiklikleri
*   ✅ Global değişkenleri kirletme
*   ✅ Mevcut event listener'ları bozma
*   ✅ Namespace kullan
*   ✅ Error handling ekle

## Hata Yakalama ve Geri Alma

### Try-Catch Blokları
*   ✅ Tüm kritik işlemleri try-catch ile sar
*   ✅ Hata durumunda rollback yap
*   ✅ Kullanıcıya anlamlı hata mesajı ver
*   ✅ Hataları logla

### Geri Alma Mekanizması
*   ✅ Her değişiklik için rollback planı hazırla
*   ✅ Backup'tan geri yükleme scripti yaz
*   ✅ Veritabanı rollback migration'ları hazırla
*   ✅ Hızlı geri alma prosedürü oluştur

## Test Stratejisi

### Unit Testler
*   ✅ Yeni özellik için unit test yaz
*   ✅ Mevcut testleri güncelle
*   ✅ Edge case'leri test et
*   ✅ Mock data kullan

### Integration Testler
*   ✅ Sistem entegrasyonunu test et
*   ✅ API endpoint'lerini test et
*   ✅ Veritabanı işlemlerini test et
*   ✅ Cross-module etkileşimleri kontrol et

## Deployment Güvenliği

### Aşamalı Deployment
*   ✅ Önce test ortamında dene
*   ✅ Staging ortamında test et
*   ✅ Canlı ortamda aşamalı yayınla
*   ✅ Monitoring ile takip et

### Rollback Hazırlığı
*   ✅ Hızlı rollback planı hazırla
*   ✅ Database rollback scripti hazırla
*   ✅ File rollback prosedürü oluştur
*   ✅ Emergency contact listesi hazırla

## Kod Review ve Onay Süreci

### Değişiklik Onayı
*   ✅ Kritik değişiklikler için kullanıcı onayı al
*   ✅ Risk analizi yap
*   ✅ Etki değerlendirmesi sun
*   ✅ Alternatif çözümler öner

### Code Review Checklist
*   ✅ Mevcut kodu bozuyor mu?
*   ✅ Performance'ı etkiliyor mu?
*   ✅ Güvenlik açığı oluşturuyor mu?
*   ✅ Test coverage yeterli mi?

## Monitoring ve Alerting

### Sistem İzleme
*   ✅ Değişiklik sonrası sistem durumunu izle
*   ✅ Error rate'i takip et
*   ✅ Performance metriklerini ölç
*   ✅ User experience'i değerlendir

### Alert Sistemi
*   ✅ Kritik hatalar için alert kur
*   ✅ Performance düşüşü için uyarı ver
*   ✅ Anormal davranışları tespit et
*   ✅ Otomatik rollback tetikleyicileri ekle

## Dokümantasyon ve İletişim

### Değişiklik Dokümantasyonu
*   ✅ Yapılan değişiklikleri detaylı dokümante et
*   ✅ Etkilenen dosyaları listele
*   ✅ Yeni özellik kullanım kılavuzu yaz
*   ✅ Breaking change'leri belirt

### Kullanıcı Bilgilendirme
*   ✅ Değişiklikleri önceden duyur
*   ✅ Migration rehberi hazırla
*   ✅ FAQ bölümü güncelle
*   ✅ Support kanallarını hazırla

## Risk Yönetimi

### Risk Değerlendirmesi
*   ✅ Yüksek riskli değişiklikleri belirle
*   ✅ Mitigation stratejileri geliştir
*   ✅ Contingency planları hazırla
*   ✅ Risk seviyesine göre onay süreci uygula

### Emergency Response
*   ✅ Acil durum prosedürleri oluştur
*   ✅ Hızlı müdahale ekibi belirle
*   ✅ Communication planı hazırla
*   ✅ Recovery time objective (RTO) belirle

## Özellik Ekleme Sonrası Kontroller

### Post-Deployment Testing
*   ✅ Canlı ortamda smoke test yap
*   ✅ Kritik user journey'leri test et
*   ✅ Performance benchmark'ları kontrol et
*   ✅ Error log'larını incele

### Monitoring ve Optimizasyon
*   ✅ İlk 24 saat yoğun monitoring yap
*   ✅ User feedback'lerini topla
*   ✅ Performance bottleneck'leri tespit et
*   ✅ Gerekirse hotfix uygula

## Özellik Ekleme Yasakları

### Kesinlikle Yapılmaması Gerekenler
*   ❌ Mevcut çalışan kodu değiştirme
*   ❌ Kritik fonksiyonları silme
*   ❌ Veritabanı yapısını bozma
*   ❌ API contract'larını kırma
*   ❌ Güvenlik kontrollerini bypass etme
*   ❌ Test edilmemiş kodu canlıya alma
*   ❌ Backup almadan değişiklik yapma

## Component Tabanlı Güvenli Özellik Ekleme

### Component İzolasyonu
*   ✅ Yeni özellikler ayrı component olarak oluştur
*   ✅ Mevcut component'lere dokunma
*   ✅ Component bağımlılıklarını kontrol et
*   ✅ Cross-component etkileşimleri minimize et

### Component Test Stratejisi
*   ✅ Her component için ayrı test yaz
*   ✅ Component integration testleri
*   ✅ Component performance testleri
*   ✅ Component güvenlik testleri

### Component Rollback
*   ✅ Component bazlı rollback sistemi
*   ✅ Component versiyon yönetimi
*   ✅ Component bağımlılık kontrolü
*   ✅ Component geri yükleme prosedürleri

