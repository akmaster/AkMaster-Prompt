<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Proje Durumu ve Checkpoint Yönetimi

## Project Status JSON Yapısı

### Temel Alanlar
```json
{
  "project_info": {
    "name": "Proje Adı",
    "version": "1.0.0",
    "description": "Proje açıklaması",
    "created": "2024-01-15T10:00:00Z",
    "last_updated": "2024-01-15T14:30:00Z"
  },
  "workflow_status": "KODLAMA",
  "current_task": "Header bölümü CSS stillerini yazma",
  "progress_checkpoint": {
    "current_file": "css/components/header-section.css",
    "progress_percentage": 45,
    "completed_parts": ["CSS değişkenleri", "Temel layout"],
    "remaining_parts": ["Navigation stilleri", "Hover efektleri"],
    "last_code_snippet": "/* Header styles */",
    "next_steps": "Navigation menü stillerini ekle",
    "estimated_remaining_time": "15-20 dakika"
  },
  "project_data": {
    "site_konusu": "Kurumsal web sitesi",
    "admin_panel_gerekli": true,
    "ana_dil": "turkish",
    "coklu_dil_destegi": false,
    "secilen_renk_paleti": "kurumsal-mavi",
    "sayfalar": ["ana-sayfa", "hakkimizda", "iletisim"],
    "master_klasor_kuruldu": true
  },
  "prompt_history": [
    {
      "timestamp": "2024-01-15T10:00:00Z",
      "action": "Proje başlatıldı",
      "decision": "Kurumsal web sitesi olarak belirlendi"
    }
  ],
  "temp_files": [
    {
      "path": "temp-files/tests/test-header.php",
      "created": "2024-01-15T14:00:00Z",
      "purpose": "Header component testi",
      "marked_for_deletion": true
    }
  ],
  "auto_save_enabled": true,
  "last_activity": "2024-01-15T14:30:00Z"
}
```

## Checkpoint Oluşturma Kuralları

### Otomatik Checkpoint Tetikleyicileri
*   Her 5 dakikada bir otomatik checkpoint
*   Her kod bloğu tamamlandığında
*   Her kullanıcı onayından sonra
*   Her hata durumunda
*   Her dosya kaydedildiğinde

### Manuel Checkpoint Tetikleyicileri
*   Kullanıcı "kaydet" dediğinde
*   Önemli bir aşama tamamlandığında
*   Kritik bir değişiklik yapıldığında

## Checkpoint İçerik Standartları

### Zorunlu Alanlar
*   `current_file`: Şu anda çalışılan dosya
*   `progress_percentage`: İlerleme yüzdesi
*   `completed_parts`: Tamamlanan kısımlar
*   `remaining_parts`: Kalan kısımlar
*   `last_code_snippet`: Son yazılan kod
*   `next_steps`: Sonraki adımlar

### Opsiyonel Alanlar
*   `estimated_remaining_time`: Tahmini kalan süre
*   `notes`: Geliştirici notları
*   `errors`: Tespit edilen hatalar
*   `warnings`: Uyarılar

## Checkpoint Kurtarma Protokolü

### Otomatik Kurtarma
*   Yeni oturum başladığında checkpoint kontrol edilir
*   Checkpoint varsa kullanıcıya sorulur
*   Kullanıcı onaylarsa checkpoint'ten devam edilir

### Manuel Kurtarma
*   Kullanıcı isterse manuel olarak checkpoint yüklenebilir
*   Checkpoint geçmişi görüntülenebilir
*   Eski checkpoint'ler geri yüklenebilir

## Proje Durumu Güncelleme Kuralları

### Workflow Status Güncellemeleri
*   Her aşama tamamlandığında güncellenir
*   Durum değişikliği loglanır
*   Geçiş tarihi kaydedilir

### Current Task Güncellemeleri
*   Her görev başladığında güncellenir
*   Görev tamamlandığında temizlenir
*   Görev değişikliği loglanır

## Geçici Dosya Takibi

### Dosya Oluşturma
*   Her geçici dosya oluşturulduğunda `temp_files` dizisine eklenir
*   Dosya yolu, oluşturma tarihi ve amacı kaydedilir
*   Dosya durumu takip edilir

### Dosya Silme
*   Geçici dosya silindiğinde listeden çıkarılır
*   Silme tarihi loglanır
*   Silme nedeni kaydedilir

## Hata Yönetimi ve Logging

### Hata Yakalama
*   Tüm hatalar yakalanır ve loglanır
*   Hata türü ve mesajı kaydedilir
*   Hata oluştuğu dosya ve satır bilgisi saklanır

### Hata Raporlama
*   Kritik hatalar anında raporlanır
*   Hata istatistikleri tutulur
*   Hata çözüm önerileri sunulur

## Performans İzleme

### Zaman Takibi
*   Her görev için süre ölçülür
*   Toplam proje süresi hesaplanır
*   Tahmini kalan süre güncellenir

### Kaynak Kullanımı
*   Dosya boyutları takip edilir
*   Bellek kullanımı izlenir
*   CPU kullanımı ölçülür

## Acil Durum Checkpoint Sistemi

### Acil Durum Checkpoint Formatı
```json
{
  "emergency_checkpoint": {
    "timestamp": "2024-01-15T14:30:00Z",
    "current_work": {
      "file": "css/components/header-section.css",
      "line_number": 45,
      "context": "Navigation menü stillerini yazıyordu",
      "last_10_lines": "/* Navigation styles */\n.nav {\n  display: flex;\n  list-style: none;\n  gap: var(--spacing-4);\n}\n\n.nav li {\n  /* Yarıda kalan kod... */"
    },
    "next_actions": [
      "Navigation menü hover efektlerini ekle",
      "Mobile responsive düzenlemeleri yap",
      "Son test ve optimizasyon"
    ],
    "estimated_completion": "10-15 dakika"
  }
}
```

### Kurtarma Protokolü
*   **Otomatik Tespit:** Yeni oturumda `emergency_checkpoint` varlığını kontrol et
*   **Kullanıcı Bilgilendirme:** "Önceki oturumda acil durum checkpoint'i bulundu. Devam etmek ister misiniz?"
*   **Hızlı Devam:** Checkpoint'ten devam ederken:
    *   Son yazılan kodu göster
    *   Kaldığı satırı işaretle
    *   Kalan işleri özetle
    *   Hızlıca devam et

## Checkpoint Optimizasyonu

### Checkpoint Boyutu Yönetimi
*   Checkpoint dosyası boyutu sınırlanır
*   Eski checkpoint'ler arşivlenir
*   Gereksiz veriler temizlenir

### Checkpoint Performansı
*   Checkpoint oluşturma hızı optimize edilir
*   Checkpoint yükleme süresi minimize edilir
*   Checkpoint sıkıştırma kullanılır

## Backup ve Kurtarma

### Checkpoint Backup
*   Kritik checkpoint'ler yedeklenir
*   Backup sıklığı belirlenir
*   Backup dosyaları güvenli şekilde saklanır

### Checkpoint Geri Yükleme
*   Backup'tan checkpoint geri yükleme
*   Checkpoint versiyon yönetimi
*   Geri yükleme doğrulama

## Monitoring ve Alerting

### Checkpoint Monitoring
*   Checkpoint oluşturma sıklığı
*   Checkpoint boyutları
*   Checkpoint hata oranları

### Alert Sistemi
*   Checkpoint oluşturma hatası
*   Checkpoint boyut limiti aşımı
*   Checkpoint kurtarma hatası

