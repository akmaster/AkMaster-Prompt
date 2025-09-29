<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Admin Panel Özel Kuralları ve Rehberi

Bu modül, admin panel geliştirme sürecinde uyulması gereken özel kuralları ve kullanıcıya sunulacak seçenekleri detaylandırır.

## Admin Panel Mimarisi ve Standartları

### Teknoloji Seçimi
Admin panel için uygun teknoloji kombinasyonları:

#### PHP + MySQL (Önerilen)
- ✅ Tüm paylaşımlı hosting'lerde çalışır
- ✅ Hızlı geliştirme süresi
- ✅ Geniş topluluk desteği
- ✅ WordPress benzeri CMS deneyimi
- ❌ Performans sınırlamaları (büyük projeler için)

#### Node.js + MongoDB/MySQL
- ✅ Yüksek performans
- ✅ Modern JavaScript ekosistemi
- ✅ Real-time özellikler
- ❌ VPS/Cloud hosting gerekir
- ❌ Daha karmaşık kurulum

#### Python + Django/Flask
- ✅ Güçlü admin paneli (Django Admin)
- ✅ Güvenlik odaklı
- ✅ Büyük projeler için ideal
- ❌ VPS/Cloud hosting gerekir
- ❌ Öğrenme eğrisi yüksek

### Veritabanı Seçimi

#### MySQL (Önerilen)
- ✅ Paylaşımlı hosting uyumlu
- ✅ Geniş destek
- ✅ İlişkisel veri yapısı
- ❌ Büyük veri setleri için yavaş

#### PostgreSQL
- ✅ Gelişmiş özellikler
- ✅ JSON desteği
- ✅ Yüksek performans
- ❌ Paylaşımlı hosting'de sınırlı

#### MongoDB
- ✅ Esnek veri yapısı
- ✅ Hızlı geliştirme
- ✅ Büyük veri desteği
- ❌ İlişkisel veri için karmaşık

### Admin Panel Özellik Modülleri

#### Temel Özellikler (Zorunlu)
- **İçerik Yönetimi:** CRUD operasyonları, medya yönetimi, draft/publish sistemi
- **Kullanıcı Yönetimi:** Kayıt, giriş, profil, yetki seviyeleri (Admin, Editor, Author)
- **Site Ayarları:** Genel site konfigürasyonu, tema seçimi, SEO ayarları

#### Gelişmiş Özellikler (Opsiyonel)
- **Analitik ve Raporlama:** Ziyaretçi istatistikleri, performans metrikleri
- **Güvenlik Modülü:** Log takibi, güvenlik uyarıları, backup yönetimi
- **Medya Kütüphanesi:** Resim, video, dosya yönetimi
- **Menü Yönetimi:** Dinamik menü oluşturma ve düzenleme
- **Form Yönetimi:** İletişim formları, anketler, lead toplama

## Admin Panel Güvenlik Standartları

### Çok Faktörlü Kimlik Doğrulama (2FA)
Google Authenticator, SMS doğrulama

### Rate Limiting
Brute force saldırılarına karşı koruma (5 başarısız giriş = 15 dk bekleme)

### Input Sanitization
Tüm admin girdilerinin temizlenmesi ve doğrulanması

### Audit Logging
Tüm admin işlemlerinin kayıt altına alınması (kim, ne, ne zaman)

### Session Management
Güvenli oturum yönetimi (30 dk timeout, güvenli cookie)

### Role-Based Access Control (RBAC)
Yetki seviyelerine göre erişim kontrolü

### File Upload Security
Dosya yükleme güvenliği (tip kontrolü, boyut sınırı, virüs tarama)

### SQL Injection Koruması
Prepared statements ve parametreli sorgular

### XSS Koruması
Output encoding ve Content Security Policy

## Admin Panel Performans Optimizasyonu

### Lazy Loading
Büyük veri setleri için sayfalama (20 kayıt/sayfa)

### Caching Stratejileri
Redis/Memcached ile admin panel cache

### Database Optimization
Admin sorguları için index optimizasyonu

### Asset Optimization
Admin panel CSS/JS minifikasyonu ve sıkıştırma

### CDN Kullanımı
Statik dosyalar için CDN entegrasyonu

### Database Connection Pooling
Veritabanı bağlantı havuzu yönetimi

## Admin Panel Tasarım Prensipleri

### Kullanıcı Dostu Arayüz
Teknik olmayan kullanıcılar için basit navigasyon

### Güvenlik Odaklı Tasarım
Hassas işlemler için onay mekanizmaları

### Responsive Admin
Mobil cihazlardan da yönetim imkanı

### Hızlı Erişim
Sık kullanılan özellikler için kısayollar ve dashboard

### Görsel Geri Bildirim
Loading states, success/error mesajları

### Keyboard Shortcuts
Hızlı işlemler için klavye kısayolları

### Dark/Light Mode
Kullanıcı tercihine göre tema seçimi

## Admin Panel Teknoloji Seçimi Rehberi

### Kullanıcıya Sorulacak Sorular
- "Projenizin büyüklüğü nedir? (Küçük/Orta/Büyük)"
- "Hosting bütçeniz nedir? (Paylaşımlı/VPS/Cloud)"
- "Teknik bilginiz var mı? (Yok/Az/Orta/İleri)"
- "Hangi özellikler gerekli? (Temel/Gelişmiş/Kurumsal)"

### Seçim Önerileri
- **Küçük Proje + Paylaşımlı Hosting + Az Teknik Bilgi = PHP + MySQL**
- **Orta Proje + VPS + Orta Teknik Bilgi = Node.js + MySQL**
- **Büyük Proje + Cloud + İleri Teknik Bilgi = Python + Django + PostgreSQL**

## Admin Panel Özellik Seçimi Rehberi

### Temel Özellikler (Tüm projeler için)
- İçerik yönetimi (CRUD)
- Kullanıcı girişi/çıkışı
- Medya yönetimi
- Site ayarları

### Gelişmiş Özellikler (Orta projeler için)
- Çoklu kullanıcı desteği
- Form yönetimi
- Menü yönetimi
- SEO ayarları

### Kurumsal Özellikler (Büyük projeler için)
- Analitik ve raporlama
- Backup yönetimi
- Audit logging
- API yönetimi

## Admin Panel Güvenlik Seviyesi Rehberi

### Temel Güvenlik (Küçük projeler)
- Standart giriş/çıkış
- Basit yetkilendirme
- Input validation
- **Maliyet:** +0

### Orta Güvenlik (Orta projeler)
- 2FA (Google Authenticator)
- Rate limiting
- Audit logging
- **Maliyet:** +50-100/ay

### Yüksek Güvenlik (Büyük projeler)
- Gelişmiş şifreleme
- RBAC (Role-Based Access Control)
- Güvenlik monitoring
- **Maliyet:** +200-500/ay

## Admin Panel Tasarım Seçimi Rehberi

### Minimalist (Önerilen)
- Temiz ve sade arayüz
- Hızlı yükleme
- Kolay navigasyon
- **Uygun:** Küçük-orta projeler

### Modern Dashboard
- Grafik ve istatistikler
- Widget tabanlı arayüz
- Gelişmiş görselleştirme
- **Uygun:** Büyük projeler

### Kurumsal
- Profesyonel görünüm
- Güvenlik odaklı tasarım
- Detaylı raporlama
- **Uygun:** Kurumsal projeler

## Admin Panel Deployment Checklist

### Ön Deployment
- ✅ Veritabanı yapısı oluşturuldu
- ✅ Güvenlik ayarları yapılandırıldı
- ✅ SSL sertifikası kuruldu
- ✅ Backup stratejisi belirlendi

### Deployment Sırasında
- ✅ Dosyalar sunucuya yüklendi
- ✅ Veritabanı bağlantısı test edildi
- ✅ İlk admin kullanıcısı oluşturuldu
- ✅ Güvenlik testleri yapıldı

### Post Deployment
- ✅ Monitoring sistemi kuruldu
- ✅ Backup sistemi test edildi
- ✅ Performance testleri yapıldı
- ✅ Kullanıcı eğitimi verildi

## Admin Panel Bakım Protokolleri

### Günlük Bakım
- Log dosyalarını kontrol et
- Backup durumunu kontrol et
- Performance metriklerini izle

### Haftalık Bakım
- Güvenlik güncellemelerini kontrol et
- Veritabanı optimizasyonu yap
- Kullanıcı aktivitelerini analiz et

### Aylık Bakım
- Tam sistem backup'ı al
- Güvenlik audit'i yap
- Performance raporu hazırla

## Admin Panel Sorun Giderme Rehberi

### Giriş Sorunları
- Kullanıcı adı/şifre kontrolü
- Session timeout kontrolü
- Veritabanı bağlantı kontrolü

### Performans Sorunları
- Veritabanı sorgu optimizasyonu
- Cache ayarları kontrolü
- Sunucu kaynak kullanımı kontrolü

### Güvenlik Sorunları
- Log dosyalarını analiz et
- Şüpheli aktiviteleri tespit et
- Güvenlik güncellemelerini uygula

## Admin Panel Kullanıcı Eğitimi

### Temel Eğitim (Tüm kullanıcılar)
- Giriş/çıkış işlemleri
- Temel içerik yönetimi
- Medya yükleme
- Site ayarları

### Gelişmiş Eğitim (Admin/Editor kullanıcılar)
- Kullanıcı yönetimi
- Form yönetimi
- Menü yönetimi
- SEO ayarları

### Uzman Eğitim (Sadece Admin kullanıcılar)
- Sistem ayarları
- Backup yönetimi
- Güvenlik ayarları
- Performans monitoring

## Admin Panel Dokümantasyon

### Kullanıcı Kılavuzu
Adım adım kullanım talimatları

### Video Eğitimler
Ekran kaydı ile görsel eğitimler

### FAQ
Sık sorulan sorular ve cevapları

### Teknik Dokümantasyon
Geliştiriciler için teknik detaylar

## Admin Panel Çoklu Dil Desteği

### Admin Panel Dil Yönetimi
- **Dil Ekleme/Çıkarma:** Yeni dil ekleme, mevcut dili deaktive etme
- **Çeviri Editörü:** WYSIWYG çeviri editörü
- **Toplu Çeviri:** Birden fazla içeriği aynı anda çevirme
- **Çeviri Durumu:** Hangi içeriklerin çevrildiğini takip
- **Otomatik Çeviri:** Google Translate API entegrasyonu
- **Çevirmen Yönetimi:** Çevirmen atama ve yetki yönetimi

### Admin Panel Çevirileri
Admin panel arayüzünün çevrilmesi

### Çeviri Yönetimi
İçerik çeviri yönetim sistemi

### Dil Durumu
Hangi dillerin aktif olduğu yönetimi

## Admin Panel API Yönetimi

### RESTful API
Admin panel için RESTful API endpoint'leri

### API Güvenliği
API key yönetimi ve rate limiting

### API Dokümantasyonu
Swagger/OpenAPI dokümantasyonu

### API Test Araçları
Postman collection'ları ve test senaryoları

## Admin Panel Monitoring ve Analytics

### Sistem Monitoring
- Server health monitoring
- Database performance tracking
- Error rate monitoring
- Response time tracking

### User Analytics
- Admin panel kullanım istatistikleri
- Feature usage analytics
- User behavior tracking
- Performance metrics

### Alert Sistemi
- Critical error alerts
- Performance degradation alerts
- Security breach alerts
- System maintenance notifications

## Admin Panel Backup ve Recovery

### Backup Stratejileri
- **Database Backup:** Otomatik veritabanı yedekleme
- **File Backup:** Dosya sistemi yedekleme
- **Configuration Backup:** Ayarlar ve konfigürasyon yedekleme
- **Code Backup:** Kaynak kod yedekleme

### Recovery Procedures
- **Point-in-time Recovery:** Belirli bir zamana geri dönme
- **Disaster Recovery:** Felaket durumunda kurtarma
- **Data Migration:** Veri taşıma prosedürleri
- **Rollback Procedures:** Geri alma prosedürleri

### Backup Testing
- **Regular Testing:** Düzenli backup testleri
- **Recovery Testing:** Kurtarma testleri
- **Integrity Testing:** Backup bütünlük testleri
- **Performance Testing:** Backup performans testleri
