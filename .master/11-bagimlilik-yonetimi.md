<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Bağımlılık Yönetimi ve Dosya Kontrol Protokolleri

Bu modül, dosya değişikliği öncesi zorunlu bağımlılık kontrolü ve güvenlik protokollerini detaylandırır.

## Dosya Değişikliği Öncesi Zorunlu Kontrol Protokolü

### Adım 1: Sistem Prompt Kontrolü
- Ana sistem promptunun tamamını gözden geçir
- İlgili kuralları ve standartları belirle
- Değişikliğin sistem promptuna uygunluğunu kontrol et

### Adım 2: .master/index.md Kontrolü
- `.master/index.md` dosyasını oku
- İlgili modül dosyasını belirle
- Modül dosyasındaki kuralları kontrol et
- Diğer ilgili modülleri tespit et

### Adım 3: Bağımlılık Analizi
- Değiştirilecek dosyanın bağımlılıklarını tespit et
- Bağımlı dosyaların mevcut durumunu kontrol et
- Değişikliğin bağımlı dosyalara etkisini değerlendir
- Potansiyel çakışmaları belirle

### Adım 4: Güvenlik Kontrolü
- Değişikliğin güvenlik risklerini kontrol et
- Mevcut sisteme zarar vermeyeceğini doğrula
- Backup gereksinimlerini belirle

### Adım 5: Test Hazırlığı
- Test ortamını hazırla
- Gerekli test dosyalarını oluştur
- Rollback planını hazırla

## PHP Dosya Başlığı Bağımlılık Kontrol Sistemi

### Zorunlu Dosya Başlığı Formatı
```php
<?php
/**
 * [DOSYA_ADI] - [DOSYA_AMACI]
 * 
 * Bu dosya [DOSYA_AMACI] için oluşturulmuştur.
 * [DOSYA_İÇERİĞİ] ile ilgili tüm fonksiyonları içerir.
 * 
 * ⚠️  DEĞİŞİKLİK ÖNCESİ KONTROL LİSTESİ:
 * 1. Sistem promptunu kontrol ettiniz mi? ✅/❌
 * 2. .master/index.md dosyasını okudunuz mu? ✅/❌
 * 3. İlgili modül dosyasını kontrol ettiniz mi? ✅/❌
 * 4. Bağımlılık dosyalarını analiz ettiniz mi? ✅/❌
 * 5. Değişikliğin etki analizini yaptınız mı? ✅/❌
 * 
 * Bağımlılıklar:
 * - functions/database.php (veritabanı işlemleri için)
 * - functions/security.php (güvenlik kontrolleri için)
 * - functions/validation.php (form validasyonu için)
 * 
 * Bağımlılık Kontrol Tarihi: [TARIH]
 * Son Bağımlılık Güncelleme: [TARIH]
 * 
 * @author AI Assistant
 * @version 1.0
 * @created [TARIH]
 * @last_updated [TARIH]
 */
```

## Bağımlılık Dosyası Kontrol Fonksiyonları

### Dosya Varlık Kontrolü
```php
// Bağımlılık dosyalarının varlığını kontrol et
$required_files = [
    __DIR__ . '/functions/database.php',
    __DIR__ . '/functions/security.php',
    __DIR__ . '/functions/validation.php'
];

foreach ($required_files as $file) {
    if (!file_exists($file)) {
        throw new Exception("Gerekli bağımlılık dosyası bulunamadı: " . basename($file));
    }
}
```

### Versiyon Uyumluluk Kontrolü
```php
function checkDependencyVersions() {
    $dependencies = [
        'database.php' => '1.2.0',
        'security.php' => '1.1.0',
        'validation.php' => '1.0.0'
    ];
    
    foreach ($dependencies as $file => $required_version) {
        $file_path = __DIR__ . '/functions/' . $file;
        
        if (file_exists($file_path)) {
            $content = file_get_contents($file_path);
            
            if (preg_match('/@version\s+([0-9]+\.[0-9]+\.[0-9]+)/', $content, $matches)) {
                $current_version = $matches[1];
                
                if (version_compare($current_version, $required_version, '<')) {
                    throw new Exception("$file dosyası güncel değil. Gerekli: $required_version, Mevcut: $current_version");
                }
            }
        }
    }
}
```

### Çakışma Kontrolü
```php
function checkDependencyConflicts() {
    $loaded_functions = get_defined_functions()['user'];
    $loaded_classes = get_declared_classes();
    
    $conflicts = [];
    
    // Fonksiyon çakışmalarını kontrol et
    $critical_functions = ['sanitizeInput', 'validateData', 'logError'];
    
    foreach ($critical_functions as $func) {
        if (in_array($func, $loaded_functions)) {
            $conflicts[] = "Fonksiyon çakışması: $func";
        }
    }
    
    if (!empty($conflicts)) {
        throw new Exception("Bağımlılık çakışmaları tespit edildi: " . implode(', ', $conflicts));
    }
}
```

## Dosya Değişikliği Güvenlik Protokolü

### Değişiklik Öncesi Kontrol Listesi
- **Sistem Prompt Kontrolü:** Ana sistem promptunu kontrol et
- **Master Index Kontrolü:** `.master/index.md` dosyasını oku
- **Modül Dosyası Kontrolü:** İlgili modül dosyasını kontrol et
- **Bağımlılık Analizi:** Bağımlılık dosyalarını analiz et
- **Etki Değerlendirmesi:** Değişikliğin etkisini değerlendir
- **Güvenlik Kontrolü:** Güvenlik risklerini kontrol et
- **Backup Hazırlığı:** Backup al ve test ortamını hazırla

## Bağımlılık Dosyası Bütünlük Kontrolü

### Dosya Varlık ve Okunabilirlik Kontrolü
- **Dosya Varlığı:** Bağımlılık dosyalarının varlığını kontrol et
- **Okunabilirlik:** Dosyaların okunabilir olduğunu kontrol et
- **Syntax Kontrolü:** Dosya syntax'ının doğru olduğunu kontrol et

### Versiyon Uyumluluk Kontrolü
- **Versiyon Karşılaştırması:** Bağımlılık dosyalarının versiyonlarını karşılaştır
- **Minimum Versiyon:** Gerekli minimum versiyonu kontrol et
- **Uyumluluk Raporu:** Uyumluluk durumunu raporla

### Çakışma Kontrolü
- **Fonksiyon Çakışması:** Aynı isimde fonksiyonları tespit et
- **Sınıf Çakışması:** Aynı isimde sınıfları tespit et
- **Değişken Çakışması:** Global değişken çakışmalarını tespit et

## Değişiklik Etki Analizi

### Etki Değerlendirme Fonksiyonu
```php
function analyzeChangeImpact($file_path, $change_type) {
    $impact_analysis = [
        'affected_files' => [],
        'breaking_changes' => [],
        'compatibility_issues' => [],
        'security_risks' => []
    ];
    
    // Etkilenen dosyaları tespit et
    $dependencies = getFileDependencies($file_path);
    foreach ($dependencies as $dep) {
        $impact_analysis['affected_files'][] = $dep;
    }
    
    // Breaking change'leri kontrol et
    if ($change_type === 'function_signature_change') {
        $impact_analysis['breaking_changes'][] = 'Function signature changed';
    }
    
    // Uyumluluk sorunlarını kontrol et
    if ($change_type === 'api_change') {
        $impact_analysis['compatibility_issues'][] = 'API contract changed';
    }
    
    // Güvenlik risklerini kontrol et
    if ($change_type === 'security_change') {
        $impact_analysis['security_risks'][] = 'Security implementation changed';
    }
    
    return $impact_analysis;
}
```

## Bağımlılık Yönetimi Stratejileri

### Bağımlılık Haritası Oluşturma
- **Dosya Bağımlılıkları:** Dosyalar arası bağımlılıkları haritalandır
- **Fonksiyon Bağımlılıkları:** Fonksiyonlar arası bağımlılıkları haritalandır
- **Sınıf Bağımlılıkları:** Sınıflar arası bağımlılıkları haritalandır
- **Modül Bağımlılıkları:** Modüller arası bağımlılıkları haritalandır

### Bağımlılık Çözümleme
- **Döngüsel Bağımlılık:** Döngüsel bağımlılıkları tespit et
- **Gereksiz Bağımlılık:** Gereksiz bağımlılıkları tespit et
- **Eksik Bağımlılık:** Eksik bağımlılıkları tespit et
- **Çakışan Bağımlılık:** Çakışan bağımlılıkları tespit et

### Bağımlılık Optimizasyonu
- **Lazy Loading:** Gerektiğinde yükleme
- **Dependency Injection:** Bağımlılık enjeksiyonu
- **Interface Segregation:** Arayüz ayrımı
- **Dependency Inversion:** Bağımlılık tersine çevirme

## Güvenli Bağımlılık Güncelleme

### Güncelleme Stratejisi
- **Aşamalı Güncelleme:** Bağımlılıkları aşamalı olarak güncelle
- **Backward Compatibility:** Geriye uyumluluğu koru
- **Testing:** Her güncelleme sonrası test yap
- **Rollback Plan:** Geri alma planı hazırla

### Güncelleme Kontrol Listesi
- ✅ Mevcut sistem çalışıyor mu?
- ✅ Yeni bağımlılık uyumlu mu?
- ✅ Test edildi mi?
- ✅ Dokümantasyon güncellendi mi?
- ✅ Rollback planı hazır mı?

## Bağımlılık İzleme ve Raporlama

### İzleme Metrikleri
- **Bağımlılık Sayısı:** Toplam bağımlılık sayısı
- **Güncelleme Sıklığı:** Bağımlılık güncelleme sıklığı
- **Çakışma Oranı:** Bağımlılık çakışma oranı
- **Çözüm Süresi:** Çakışma çözüm süresi

### Raporlama
- **Günlük Raporlar:** Günlük bağımlılık durumu
- **Haftalık Raporlar:** Haftalık bağımlılık analizi
- **Aylık Raporlar:** Aylık bağımlılık optimizasyonu
- **Yıllık Raporlar:** Yıllık bağımlılık stratejisi

## Bağımlılık Güvenliği

### Güvenlik Kontrolleri
- **Vulnerability Scanning:** Güvenlik açığı taraması
- **License Compliance:** Lisans uyumluluğu
- **Code Quality:** Kod kalitesi kontrolü
- **Security Updates:** Güvenlik güncellemeleri

### Güvenlik Protokolleri
- **Approval Process:** Onay süreci
- **Security Review:** Güvenlik incelemesi
- **Penetration Testing:** Penetrasyon testi
- **Compliance Audit:** Uyumluluk denetimi

## Bağımlılık Dokümantasyonu

### Dokümantasyon Standartları
- **Bağımlılık Listesi:** Tüm bağımlılıkları listele
- **Versiyon Bilgisi:** Her bağımlılığın versiyonunu belirt
- **Kullanım Amacı:** Her bağımlılığın kullanım amacını açıkla
- **Güncelleme Notları:** Güncelleme notlarını tut

### Dokümantasyon Örnekleri
```markdown
# Bağımlılık Dokümantasyonu

## Ana Bağımlılıklar

### functions/database.php
- **Versiyon:** 1.2.0
- **Amaç:** Veritabanı işlemleri
- **Kullanım:** PDO bağlantı yönetimi
- **Son Güncelleme:** 2024-01-15

### functions/security.php
- **Versiyon:** 1.1.0
- **Amaç:** Güvenlik kontrolleri
- **Kullanım:** Input sanitization, XSS koruması
- **Son Güncelleme:** 2024-01-10

### functions/validation.php
- **Versiyon:** 1.0.0
- **Amaç:** Form validasyonu
- **Kullanım:** Client-side ve server-side validation
- **Son Güncelleme:** 2024-01-05
```

## Bağımlılık Yönetimi Araçları

### Otomatik Araçlar
- **Dependency Scanner:** Bağımlılık tarayıcı
- **Version Checker:** Versiyon kontrolcü
- **Conflict Detector:** Çakışma tespit edici
- **Update Manager:** Güncelleme yöneticisi

### Manuel Araçlar
- **Dependency Graph:** Bağımlılık grafiği
- **Impact Analyzer:** Etki analizcisi
- **Compatibility Checker:** Uyumluluk kontrolcü
- **Security Scanner:** Güvenlik tarayıcı

## Sürekli İyileştirme

### İyileştirme Süreci
- **Veri Toplama:** Bağımlılık verilerini topla
- **Analiz:** Verileri analiz et
- **Optimizasyon:** Bağımlılıkları optimize et
- **Uygulama:** İyileştirmeleri uygula
- **Değerlendirme:** Sonuçları değerlendir

### İyileştirme Metrikleri
- **Bağımlılık Azaltma:** Gereksiz bağımlılıkları azalt
- **Performans Artışı:** Performansı artır
- **Güvenlik İyileştirmesi:** Güvenliği iyileştir
- **Bakım Kolaylığı:** Bakımı kolaylaştır
