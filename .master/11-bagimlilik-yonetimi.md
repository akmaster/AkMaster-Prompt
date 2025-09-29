<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Bağımlılık Yönetimi ve Dosya Kontrol Protokolleri

## Dosya Değişikliği Öncesi Zorunlu Kontrol Protokolü

### Adım 1: Sistem Prompt Kontrolü
*   Ana sistem promptunun tamamını gözden geçir
*   İlgili kuralları ve standartları belirle
*   Değişikliğin sistem promptuna uygunluğunu kontrol et

### Adım 2: .master/index.md Kontrolü
*   `.master/index.md` dosyasını oku
*   İlgili modül dosyasını belirle
*   Modül dosyasındaki kuralları kontrol et
*   Diğer ilgili modülleri tespit et

### Adım 3: Bağımlılık Analizi
*   Değiştirilecek dosyanın bağımlılıklarını tespit et
*   Bağımlı dosyaların mevcut durumunu kontrol et
*   Değişikliğin bağımlı dosyalara etkisini değerlendir
*   Potansiyel çakışmaları belirle

### Adım 4: Güvenlik Kontrolü
*   Değişikliğin güvenlik risklerini kontrol et
*   Mevcut sisteme zarar vermeyeceğini doğrula
*   Backup gereksinimlerini belirle

### Adım 5: Test Hazırlığı
*   Test ortamını hazırla
*   Gerekli test dosyalarını oluştur
*   Rollback planını hazırla

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
*   **Sistem Prompt Kontrolü:** Ana sistem promptunu kontrol et
*   **Master Index Kontrolü:** `.master/index.md` dosyasını oku
*   **Modül Dosyası Kontrolü:** İlgili modül dosyasını kontrol et
*   **Bağımlılık Analizi:** Dosya bağımlılıklarını analiz et
*   **Etki Değerlendirmesi:** Değişikliğin etkisini değerlendir
*   **Güvenlik Kontrolü:** Güvenlik risklerini kontrol et
*   **Backup Hazırlığı:** Backup al ve test ortamı hazırla

## Bağımlılık Dosyası Bütünlük Kontrolü

### Dosya Varlık ve Okunabilirlik Kontrolü
*   Bağımlılık dosyalarının varlığı
*   Dosya okunabilirliği
*   Dosya syntax kontrolü
*   Dosya izinleri kontrolü

### Versiyon Uyumluluk Kontrolü
*   Bağımlılık dosyalarının versiyon uyumluluğu
*   API uyumluluğu
*   Veri yapısı uyumluluğu
*   Fonksiyon imza uyumluluğu

### Çakışma Kontrolü
*   Fonksiyon çakışmaları
*   Sınıf çakışmaları
*   Değişken çakışmaları
*   Namespace çakışmaları

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
    if ($change_type === 'api_change') {
        $impact_analysis['breaking_changes'][] = 'API değişikliği tespit edildi';
    }
    
    // Uyumluluk sorunlarını kontrol et
    $compatibility_issues = checkCompatibility($file_path);
    $impact_analysis['compatibility_issues'] = $compatibility_issues;
    
    // Güvenlik risklerini kontrol et
    $security_risks = checkSecurityRisks($file_path);
    $impact_analysis['security_risks'] = $security_risks;
    
    return $impact_analysis;
}
```

### Etkilenen Dosyalar
*   Doğrudan bağımlılık dosyaları
*   Dolaylı bağımlılık dosyaları
*   Import/require edilen dosyalar
*   Include edilen dosyalar

### Breaking Changes
*   API değişiklikleri
*   Fonksiyon imza değişiklikleri
*   Veri yapısı değişiklikleri
*   Konfigürasyon değişiklikleri

### Uyumluluk Sorunları
*   Versiyon uyumsuzlukları
*   Platform uyumsuzlukları
*   Tarayıcı uyumsuzlukları
*   PHP versiyon uyumsuzlukları

### Güvenlik Riskleri
*   XSS açıkları
*   SQL injection riskleri
*   CSRF açıkları
*   Dosya erişim açıkları

## Component Tabanlı Bağımlılık Yönetimi

### Component Bağımlılık Haritası
```json
{
  "components": {
    "header-component": {
      "dependencies": [
        "css/variables.css",
        "js/utils.js",
        "components/navigation/nav-component.js"
      ],
      "version": "1.0.0",
      "last_updated": "2024-01-15T10:00:00Z"
    },
    "nav-component": {
      "dependencies": [
        "css/variables.css",
        "js/event-handlers.js"
      ],
      "version": "1.0.0",
      "last_updated": "2024-01-15T10:00:00Z"
    }
  }
}
```

### Component Bağımlılık Kontrolü
*   Component bağımlılık ağacını oluştur
*   Circular dependency'leri tespit et
*   Component versiyon uyumluluğunu kontrol et
*   Component çakışmalarını engelle

### Component İzolasyonu
*   Her component kendi namespace'inde çalışır
*   Cross-component erişim kontrollü olur
*   Component bağımlılıkları minimize edilir
*   Component testleri izole edilir

## Otomatik Bağımlılık Kontrol Sistemi

### Pre-commit Hooks
*   Dosya değişikliği öncesi otomatik kontrol
*   Bağımlılık çakışmalarını tespit et
*   Versiyon uyumluluğunu kontrol et
*   Güvenlik risklerini tespit et

### CI/CD Entegrasyonu
*   Continuous integration'da bağımlılık kontrolü
*   Otomatik test çalıştırma
*   Deployment öncesi kontrol
*   Rollback tetikleyicileri

### Monitoring ve Alerting
*   Bağımlılık değişikliklerini izle
*   Çakışma uyarıları
*   Versiyon uyumsuzluk uyarıları
*   Güvenlik risk uyarıları

## Bağımlılık Çözüm Stratejileri

### Çakışma Çözümü
*   Namespace kullanımı
*   Fonksiyon yeniden adlandırma
*   Sınıf yeniden adlandırma
*   Modül yeniden yapılandırma

### Versiyon Yönetimi
*   Semantic versioning kullanımı
*   Backward compatibility sağlama
*   Deprecation stratejileri
*   Migration planları

### Güvenlik Risk Azaltma
*   Input validation
*   Output encoding
*   Access control
*   Error handling

## Bağımlılık Dokümantasyonu

### Bağımlılık Dokümantasyon Formatı
```markdown
# [COMPONENT_ADI] Bağımlılık Dokümantasyonu

## Bağımlılıklar
- **database.php** (v1.2.0+): Veritabanı işlemleri
- **security.php** (v1.1.0+): Güvenlik kontrolleri
- **validation.php** (v1.0.0+): Form validasyonu

## Versiyon Gereksinimleri
- PHP: 7.4+
- MySQL: 5.7+
- Browser: Chrome 80+, Firefox 75+

## Güvenlik Gereksinimleri
- HTTPS zorunlu
- CSRF token gerekli
- Input sanitization gerekli

## Test Gereksinimleri
- Unit testler: ✅
- Integration testler: ✅
- Security testler: ✅
```

### Bağımlılık Güncelleme Rehberi
*   Bağımlılık güncelleme prosedürleri
*   Breaking change migration'ları
*   Test stratejileri
*   Rollback planları

