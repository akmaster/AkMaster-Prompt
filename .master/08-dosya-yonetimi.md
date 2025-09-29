<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Geçici Dosya Yönetimi ve Test Klasör Yapısı

Bu modül, proje geliştirme sürecinde oluşturulan geçici dosyaların ve test dosyalarının nasıl yönetileceğini tanımlar.

## Geçici Dosya İşaretleme Sistemi

### SİLİNECEK İbaresi
Sonradan kaldırılması muhtemel tüm dosyaların başına `[SİLİNECEK]` ibaresi eklenmelidir.

### Dosya İsimlendirme Kuralı
Geçici dosyalar `temp_`, `test_`, `debug_`, `backup_` gibi ön eklerle başlamalıdır.

### Otomatik Temizlik
Proje tamamlandığında `[SİLİNECEK]` ibareli dosyalar otomatik olarak temizlenmelidir.

## Test Klasör Yapısı

```
/temp-files/
├── tests/          # Test dosyaları
├── debug/          # Debug dosyaları
├── backups/        # Yedek dosyalar
└── documentation/  # Geçici dokümantasyon
```

## Geçici Dosya Türleri ve İşaretleme

### Test Dosyaları
- `[SİLİNECEK] test_*.php` - Test scriptleri
- `[SİLİNECEK] debug_*.js` - Debug JavaScript dosyaları
- `[SİLİNECEK] temp_*.html` - Geçici HTML dosyaları

### Backup Dosyaları
- `[SİLİNECEK] *.backup` - Yedek dosyalar
- `[SİLİNECEK] *.bak` - Alternatif yedek uzantısı
- `[SİLİNECEK] *_old.*` - Eski versiyon dosyalar

### Log Dosyaları
- `[SİLİNECEK] error.log` - Hata logları
- `[SİLİNECEK] debug.log` - Debug logları
- `[SİLİNECEK] access.log` - Erişim logları

### Cache Dosyaları
- `[SİLİNECEK] cache_*.xml` - Cache dosyaları
- `[SİLİNECEK] temp_*.json` - Geçici JSON dosyaları

## Test Klasörü İçerik Yönetimi

### Test Dosyası Oluşturma Kuralları
- Tüm test dosyaları `/temp-files/tests/` klasöründe oluşturulmalıdır
- Test dosyaları `[SİLİNECEK]` ibaresi ile işaretlenmelidir
- Test dosyaları açıklayıcı isimlerle adlandırılmalıdır

### Test Kategorileri
- **Unit Tests:** `unit-tests/test_*.php`
- **Integration Tests:** `integration-tests/test_*.php`
- **Performance Tests:** `performance-tests/test_*.php`
- **Browser Tests:** `browser-tests/test_*.html`

## Geçici Dosya Temizlik Protokolü

### Otomatik Temizlik Kuralları
- Her proje tamamlandığında `[SİLİNECEK]` ibareli dosyalar silinir
- `/temp-files/` klasörü tamamen temizlenir
- Backup dosyaları ayrı bir yere taşınır

### Manuel Temizlik
- Geliştirici isterse manuel olarak temizlik yapabilir
- Temizlik öncesi kullanıcıya onay sorulur
- Silinecek dosyaların listesi gösterilir

## Test Dosyası İçerik Standartları

### Test Dosyası Başlığı
```php
<?php
/**
 * [SİLİNECEK] Test Dosyası - [TEST_ADI]
 * 
 * Bu dosya [TEST_AMACI] için oluşturulmuştur.
 * Proje tamamlandığında silinecektir.
 * 
 * @author AI Assistant
 * @created [TARIH]
 * @purpose [TEST_AMACI]
 */
```

### Test Sonuç Raporlama
```php
// Test sonuçları buraya yazılır
echo "Test Başarılı: " . ($test_result ? "EVET" : "HAYIR") . "\n";
echo "Test Süresi: " . $execution_time . " saniye\n";
echo "Hata Sayısı: " . $error_count . "\n";
```

## Debug Klasörü Yönetimi

### Debug Dosyası Oluşturma
- Debug dosyaları `/temp-files/debug/` klasöründe oluşturulur
- Debug dosyaları `[SİLİNECEK] debug_*.log` formatında adlandırılır
- Debug dosyaları otomatik olarak temizlenir

### Log Dosyası Rotasyonu
- Log dosyaları belirli boyuta ulaştığında yeni dosya oluşturulur
- Eski log dosyaları otomatik olarak arşivlenir
- Log dosyaları 30 gün sonra silinir

## Backup Klasörü Yönetimi

### Backup Dosyası Oluşturma
- Backup dosyaları `/temp-files/backups/` klasöründe oluşturulur
- Backup dosyaları `[SİLİNECEK] backup_*.sql` formatında adlandırılır
- Backup dosyaları proje tamamlandığında silinir

### Backup Dosyası Saklama
- Kritik backup'lar ayrı bir yere taşınır
- Gereksiz backup'lar otomatik silinir
- Backup dosyaları sıkıştırılır

## Geçici Dokümantasyon Yönetimi

### Dokümantasyon Dosyaları
- Geçici dokümantasyon `/temp-files/documentation/` klasöründe saklanır
- Dokümantasyon dosyaları `[SİLİNECEK] doc_*.md` formatında adlandırılır
- Dokümantasyon dosyaları proje tamamlandığında silinir

### Dokümantasyon İçerik Standartları
```markdown
# [SİLİNECEK] [DOKÜMANTASYON_ADI]

> **UYARI:** Bu dosya geçicidir ve proje tamamlandığında silinecektir.

## Amaç
[DOKÜMANTASYON_AMACI]

## İçerik
[DOKÜMANTASYON_İÇERİĞİ]

## Notlar
[GELİŞTİRİCİ_NOTLARI]
```

## Geçici Dosya Güvenlik Kuralları

### Hassas Veri Koruması
- Geçici dosyalarda hassas veri saklanmamalıdır
- Test veritabanları ayrı olmalıdır
- Debug dosyalarında şifreler loglanmamalıdır

### Dosya İzinleri
- Geçici dosyalar sadece geliştirici tarafından okunabilir olmalıdır
- Geçici dosyalar web sunucusundan erişilemez olmalıdır
- Geçici dosyalar .gitignore'a eklenmelidir

## Otomatik Temizlik Scripti

```php
<?php
/**
 * [SİLİNECEK] Geçici Dosya Temizlik Scripti
 * 
 * Bu script proje tamamlandığında çalıştırılır
 * ve tüm geçici dosyaları temizler.
 */

function cleanTempFiles() {
    $tempDir = __DIR__ . '/temp-files/';
    $deletedFiles = [];
    $deletedDirs = [];
    
    // [SİLİNECEK] ibareli dosyaları bul ve sil
    $iterator = new RecursiveIteratorIterator(
        new RecursiveDirectoryIterator($tempDir)
    );
    
    foreach ($iterator as $file) {
        if ($file->isFile()) {
            $content = file_get_contents($file->getPathname());
            if (strpos($content, '[SİLİNECEK]') !== false) {
                $deletedFiles[] = $file->getPathname();
                unlink($file->getPathname());
            }
        }
    }
    
    // Boş klasörleri sil
    $dirs = glob($tempDir . '*', GLOB_ONLYDIR);
    foreach ($dirs as $dir) {
        if (is_dir($dir) && count(scandir($dir)) == 2) {
            $deletedDirs[] = $dir;
            rmdir($dir);
        }
    }
    
    return [
        'deleted_files' => $deletedFiles,
        'deleted_dirs' => $deletedDirs
    ];
}
```

## Geçici Dosya İzleme Sistemi

### Dosya Oluşturma Takibi
- Her geçici dosya oluşturulduğunda log tutulur
- Dosya oluşturma tarihi ve amacı kaydedilir
- Dosya boyutu ve türü takip edilir

### Temizlik Raporu
- Temizlik işlemi sonrası rapor oluşturulur
- Silinen dosya sayısı ve boyutu raporlanır
- Temizlik işlemi loglanır

## Geçici Dosya Kategorileri

### Geliştirme Dosyaları
- **Prototype Files:** `[SİLİNECEK] proto_*.html`
- **Mock Data:** `[SİLİNECEK] mock_*.json`
- **Sample Files:** `[SİLİNECEK] sample_*.txt`
- **Draft Files:** `[SİLİNECEK] draft_*.md`

### Test Verileri
- **Test Data:** `[SİLİNECEK] testdata_*.sql`
- **Mock APIs:** `[SİLİNECEK] mockapi_*.php`
- **Test Images:** `[SİLİNECEK] testimg_*.jpg`
- **Sample Videos:** `[SİLİNECEK] sample_*.mp4`

### Geçici Konfigürasyonlar
- **Config Backups:** `[SİLİNECEK] config_*.backup`
- **Environment Files:** `[SİLİNECEK] env_*.example`
- **Database Dumps:** `[SİLİNECEK] dbdump_*.sql`
- **Log Archives:** `[SİLİNECEK] logs_*.zip`

## Dosya Yaşam Döngüsü Yönetimi

### Oluşturma Aşaması
- **Purpose Definition:** Amaç tanımlama
- **Naming Convention:** İsimlendirme kuralı
- **Location Assignment:** Konum atama
- **Permission Setting:** İzin ayarlama
- **Documentation:** Dokümantasyon

### Kullanım Aşaması
- **Access Control:** Erişim kontrolü
- **Version Management:** Versiyon yönetimi
- **Dependency Tracking:** Bağımlılık takibi
- **Usage Monitoring:** Kullanım izleme
- **Performance Tracking:** Performans takibi

### Arşivleme Aşaması
- **Archive Decision:** Arşivleme kararı
- **Compression:** Sıkıştırma
- **Metadata Preservation:** Meta veri koruma
- **Access Restriction:** Erişim kısıtlama
- **Retention Policy:** Saklama politikası

### Silme Aşaması
- **Deletion Criteria:** Silme kriterleri
- **Safety Checks:** Güvenlik kontrolleri
- **Backup Verification:** Yedekleme doğrulama
- **Cleanup Execution:** Temizlik yürütme
- **Audit Trail:** Denetim izi

## Geçici Dosya Optimizasyonu

### Boyut Optimizasyonu
- **Compression:** Sıkıştırma teknikleri
- **Deduplication:** Tekrarlama kaldırma
- **Cleanup Scheduling:** Temizlik planlaması
- **Size Monitoring:** Boyut izleme
- **Threshold Management:** Eşik yönetimi

### Performans Optimizasyonu
- **I/O Optimization:** Giriş/çıkış optimizasyonu
- **Caching Strategy:** Cache stratejisi
- **Access Pattern Analysis:** Erişim kalıbı analizi
- **Resource Management:** Kaynak yönetimi
- **Load Balancing:** Yük dengeleme

### Güvenlik Optimizasyonu
- **Encryption:** Şifreleme
- **Access Control:** Erişim kontrolü
- **Audit Logging:** Denetim loglama
- **Vulnerability Scanning:** Güvenlik açığı taraması
- **Compliance Checking:** Uyumluluk kontrolü

## Geçici Dosya Raporlama

### Günlük Raporlar
- **File Count:** Dosya sayısı
- **Size Summary:** Boyut özeti
- **Creation Rate:** Oluşturma oranı
- **Deletion Rate:** Silme oranı
- **Usage Statistics:** Kullanım istatistikleri

### Haftalık Raporlar
- **Trend Analysis:** Trend analizi
- **Growth Rate:** Büyüme oranı
- **Cleanup Effectiveness:** Temizlik etkinliği
- **Resource Utilization:** Kaynak kullanımı
- **Performance Metrics:** Performans metrikleri

### Aylık Raporlar
- **Comprehensive Analysis:** Kapsamlı analiz
- **Policy Compliance:** Politika uyumu
- **Cost Analysis:** Maliyet analizi
- **Optimization Recommendations:** Optimizasyon önerileri
- **Strategic Planning:** Stratejik planlama
