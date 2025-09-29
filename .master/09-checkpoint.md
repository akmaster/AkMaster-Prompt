<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Proje Durumu ve Checkpoint Yönetimi

Bu modül, proje geliştirme sürecinde durum takibi ve checkpoint yönetimini detaylandırır.

## Project Status JSON Yapısı

### Temel Alanlar
```json
{
  "project_info": {
    "name": "Proje Adı",
    "version": "1.0.0",
    "description": "Proje açıklaması",
    "start_date": "2024-01-15T00:00:00Z",
    "last_updated": "2024-01-15T14:30:00Z"
  },
  "workflow_status": "KESIF",
  "current_task": "Site konusunu belirleme",
  "progress_checkpoint": {
    "current_file": "css/components/header-section.css",
    "progress_percentage": 45,
    "completed_parts": ["CSS değişkenleri tanımlandı"],
    "remaining_parts": ["Navigation menü stilleri"],
    "last_code_snippet": "/* CSS kod parçası */",
    "next_steps": "Navigation menü stillerini ekle",
    "estimated_remaining_time": "15-20 dakika"
  },
  "project_data": {
    "site_konusu": "Kurumsal web sitesi",
    "admin_panel_gerekli": true,
    "ana_dil": "tr",
    "coklu_dil_destegi": false,
    "secilen_renk_paleti": "Kurumsal Mavi",
    "sayfalar": ["Ana Sayfa", "Hakkımızda", "İletişim"]
  },
  "prompt_history": [
    {
      "timestamp": "2024-01-15T14:30:00Z",
      "user_input": "Kurumsal web sitesi istiyorum",
      "ai_response": "Admin panel gerekli mi?",
      "decision": "Admin panel gerekli"
    }
  ],
  "temp_files": [
    {
      "path": "/temp-files/tests/test_contact_form.php",
      "created": "2024-01-15T14:30:00Z",
      "purpose": "İletişim formu testi",
      "status": "active"
    }
  ],
  "auto_save_enabled": true,
  "last_activity": "2024-01-15T14:30:00Z"
}
```

## Checkpoint Oluşturma Kuralları

### Otomatik Checkpoint Tetikleyicileri
- **Zaman Bazlı:** Her 5 dakikada bir otomatik checkpoint
- **Kod Tamamlama:** Her kod bloğu tamamlandığında
- **Kullanıcı Onayı:** Her kullanıcı onayından sonra
- **Hata Durumu:** Her hata durumunda
- **Dosya Kaydetme:** Her dosya kaydedildiğinde

### Manuel Checkpoint Tetikleyicileri
- **Kullanıcı İsteği:** Kullanıcı "kaydet" dediğinde
- **Önemli Aşama:** Önemli bir aşama tamamlandığında
- **Kritik Değişiklik:** Kritik bir değişiklik yapıldığında

## Checkpoint İçerik Standartları

### Zorunlu Alanlar
- **current_file:** Şu anda çalışılan dosya
- **progress_percentage:** İlerleme yüzdesi
- **completed_parts:** Tamamlanan kısımlar
- **remaining_parts:** Kalan kısımlar
- **last_code_snippet:** Son yazılan kod
- **next_steps:** Sonraki adımlar

### Opsiyonel Alanlar
- **estimated_remaining_time:** Tahmini kalan süre
- **notes:** Geliştirici notları
- **errors:** Tespit edilen hatalar
- **warnings:** Uyarılar

### Checkpoint Örnek Formatı
```json
{
  "progress_checkpoint": {
    "current_file": "css/components/header-section.css",
    "progress_percentage": 45,
    "completed_parts": [
      "CSS değişkenleri tanımlandı",
      "Temel header layout oluşturuldu",
      "Logo alanı stillendirildi"
    ],
    "remaining_parts": [
      "Navigation menü stilleri",
      "Hover efektleri",
      "Mobile responsive düzenlemeler",
      "Son optimizasyonlar"
    ],
    "last_code_snippet": ".header {\n  background: var(--color-primary);\n  padding: var(--spacing-4);\n  display: flex;\n  justify-content: space-between;\n  align-items: center;\n  /* Navigation menü stilleri burada devam edecek... */",
    "next_steps": "Navigation menü stillerini ekle ve hover efektlerini uygula",
    "estimated_remaining_time": "15-20 dakika",
    "notes": "Renk değişkenleri güncellendi, responsive breakpoint'ler eklendi",
    "errors": [],
    "warnings": ["Mobile görünümde logo çok küçük olabilir"]
  }
}
```

## Checkpoint Kurtarma Protokolü

### Otomatik Kurtarma
- **Yeni Oturum:** Yeni oturum başladığında checkpoint kontrol edilir
- **Kullanıcı Onayı:** Checkpoint varsa kullanıcıya sorulur
- **Devam Etme:** Kullanıcı onaylarsa checkpoint'ten devam edilir

### Manuel Kurtarma
- **Kullanıcı İsteği:** Kullanıcı isterse manuel olarak checkpoint yüklenebilir
- **Checkpoint Geçmişi:** Checkpoint geçmişi görüntülenebilir
- **Eski Checkpoint'ler:** Eski checkpoint'ler geri yüklenebilir

### Kurtarma Senaryoları
- **Kod Yazma Yarıda Kaldı:** Kaldığı yerden devam et, son kod bloğunu göster
- **Test Yarıda Kaldı:** Test edilen kısımları göster, kalan testleri listele
- **Review Yarıda Kaldı:** Review edilen kısımları göster, kalan incelemeleri listele

## Proje Durumu Güncelleme Kuralları

### Workflow Status Güncellemeleri
- **Aşama Tamamlama:** Her aşama tamamlandığında güncellenir
- **Durum Değişikliği:** Durum değişikliği loglanır
- **Geçiş Tarihi:** Geçiş tarihi kaydedilir

### Current Task Güncellemeleri
- **Görev Başlangıcı:** Her görev başladığında güncellenir
- **Görev Tamamlama:** Görev tamamlandığında temizlenir
- **Görev Değişikliği:** Görev değişikliği loglanır

### Progress Checkpoint Güncellemeleri
- **İlerleme Kaydetme:** Her önemli ilerlemede güncellenir
- **Durum Değişikliği:** Çalışılan dosya değiştiğinde güncellenir
- **Hata Durumu:** Hata oluştuğunda güncellenir

## Geçici Dosya Takibi

### Dosya Oluşturma
- **Otomatik Kayıt:** Her geçici dosya oluşturulduğunda `temp_files` dizisine eklenir
- **Dosya Bilgileri:** Dosya yolu, oluşturma tarihi ve amacı kaydedilir
- **Dosya Durumu:** Dosya durumu takip edilir

### Dosya Silme
- **Otomatik Temizlik:** Geçici dosya silindiğinde listeden çıkarılır
- **Silme Tarihi:** Silme tarihi loglanır
- **Silme Nedeni:** Silme nedeni kaydedilir

### Dosya Durumları
- **active:** Aktif kullanımda
- **archived:** Arşivlenmiş
- **deleted:** Silinmiş
- **pending_cleanup:** Temizlik bekliyor

## Hata Yönetimi ve Logging

### Hata Yakalama
- **Try-Catch Blokları:** Tüm hatalar yakalanır ve loglanır
- **Hata Türü:** Hata türü ve mesajı kaydedilir
- **Konum Bilgisi:** Hata oluştuğu dosya ve satır bilgisi saklanır

### Hata Raporlama
- **Kritik Hatalar:** Kritik hatalar anında raporlanır
- **Hata İstatistikleri:** Hata istatistikleri tutulur
- **Çözüm Önerileri:** Hata çözüm önerileri sunulur

### Hata Kategorileri
- **Syntax Errors:** Sözdizimi hataları
- **Runtime Errors:** Çalışma zamanı hataları
- **Logic Errors:** Mantık hataları
- **Performance Issues:** Performans sorunları
- **Security Issues:** Güvenlik sorunları

## Performans İzleme

### Zaman Takibi
- **Görev Süreleri:** Her görev için süre ölçülür
- **Toplam Süre:** Toplam proje süresi hesaplanır
- **Tahmini Süre:** Tahmini kalan süre güncellenir

### Kaynak Kullanımı
- **Dosya Boyutları:** Dosya boyutları takip edilir
- **Bellek Kullanımı:** Bellek kullanımı izlenir
- **CPU Kullanımı:** CPU kullanımı ölçülür

### Performans Metrikleri
- **Response Time:** Yanıt süresi
- **Throughput:** İşlem hacmi
- **Error Rate:** Hata oranı
- **Availability:** Erişilebilirlik
- **Scalability:** Ölçeklenebilirlik

## Acil Durum Checkpoint Sistemi

### Acil Durum Tetikleyicileri
- **Elektrik Kesintisi:** Elektrik kesintisi durumunda
- **Bağlantı Kopması:** İnternet bağlantısı kopması durumunda
- **Sistem Çökmesi:** Sistem çökmesi durumunda
- **Veri Kaybı:** Veri kaybı riski durumunda

### Acil Durum Checkpoint Formatı
```json
{
  "emergency_checkpoint": {
    "timestamp": "2024-01-15T14:30:00Z",
    "trigger_reason": "elektrik_kesintisi",
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
    "estimated_completion": "10-15 dakika",
    "critical_data": {
      "user_inputs": ["Kurumsal web sitesi istiyorum"],
      "decisions": ["Admin panel gerekli"],
      "code_changes": ["CSS değişkenleri eklendi"]
    }
  }
}
```

### Acil Durum Kurtarma
- **Otomatik Tespit:** Yeni oturumda `emergency_checkpoint` varlığını kontrol et
- **Kullanıcı Bilgilendirme:** "Önceki oturumda acil durum checkpoint'i bulundu. Devam etmek ister misiniz?"
- **Hızlı Devam:** Checkpoint'ten devam ederken:
  - Son yazılan kodu göster
  - Kaldığı satırı işaretle
  - Kalan işleri özetle
  - Hızlıca devam et

## Checkpoint Optimizasyonu

### Checkpoint Sıklığı Optimizasyonu
- **Adaptive Frequency:** İş yoğunluğuna göre sıklık ayarlama
- **Smart Triggering:** Akıllı tetikleme mekanizması
- **Resource Awareness:** Kaynak kullanımına göre ayarlama
- **User Preference:** Kullanıcı tercihine göre ayarlama

### Checkpoint Boyutu Optimizasyonu
- **Compression:** Checkpoint verilerini sıkıştırma
- **Selective Saving:** Sadece gerekli verileri kaydetme
- **Incremental Updates:** Artımlı güncellemeler
- **Cleanup Strategy:** Temizlik stratejisi

### Checkpoint Performansı
- **Async Operations:** Asenkron işlemler
- **Background Saving:** Arka plan kaydetme
- **Queue Management:** Kuyruk yönetimi
- **Priority Handling:** Öncelik yönetimi

## Checkpoint Güvenliği

### Veri Güvenliği
- **Encryption:** Checkpoint verilerini şifreleme
- **Access Control:** Erişim kontrolü
- **Audit Trail:** Denetim izi
- **Backup Strategy:** Yedekleme stratejisi

### Güvenlik Protokolleri
- **Authentication:** Kimlik doğrulama
- **Authorization:** Yetkilendirme
- **Integrity Check:** Bütünlük kontrolü
- **Vulnerability Scanning:** Güvenlik açığı taraması

## Checkpoint Raporlama

### Günlük Raporlar
- **Checkpoint Count:** Checkpoint sayısı
- **Recovery Events:** Kurtarma olayları
- **Error Rate:** Hata oranı
- **Performance Metrics:** Performans metrikleri

### Haftalık Raporlar
- **Trend Analysis:** Trend analizi
- **Usage Patterns:** Kullanım kalıpları
- **Optimization Opportunities:** Optimizasyon fırsatları
- **System Health:** Sistem sağlığı

### Aylık Raporlar
- **Comprehensive Analysis:** Kapsamlı analiz
- **Policy Compliance:** Politika uyumu
- **Cost Analysis:** Maliyet analizi
- **Strategic Recommendations:** Stratejik öneriler
