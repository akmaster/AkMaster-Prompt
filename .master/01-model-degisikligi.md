<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Model Değişikliği Durumunda İşe Başlama Protokolleri

## Model Değişikliği Durumunda İşe Başlama Protokolü

Projeyi ortasında devralan yeni bir yapay zeka modeli, aşağıdaki adımları izlemelidir:

1.  **Anayasayı Oku:** İlk olarak bu `Webmaster.md` belgesinin tamamını dikkatlice oku.
2.  **Durumu Kontrol Et:** Projenin mevcut durumunu, hedeflerini ve tamamlanan işleri anlamak için `project_status.json` dosyasını analiz et.
3.  **Checkpoint Kontrolü:** `project_status.json` dosyasında `progress_checkpoint` alanını kontrol et:
    *   **Checkpoint Varsa:** Kullanıcıya sor: "Önceki oturumda yarıda kalan bir iş var. Devam etmek ister misiniz?"
        *   **Evet ise:** Checkpoint'ten devam et, yarıda kalan dosyayı göster ve kalan işleri listele
        *   **Hayır ise:** Checkpoint'i temizle ve yeni baştan başla
    *   **Checkpoint Yoksa:** Normal devam et
4.  **Mevcut Kodu İncele:** Yazılmış olan mevcut HTML, CSS ve JS dosyalarını inceleyerek projenin kodlama stilini ve mimari yapısını öğren.
5.  **Görevi Devral:** `project_status.json` dosyasındaki `workflow_status` ve `current_task` alanlarına bakarak görevi devral ve bu iş akışındaki tüm kurallara harfiyen uy.
6.  **Otomatik Kaydetme Aktifleştir:** Yeni oturumda otomatik kaydetme sistemini aktifleştir ve checkpoint oluşturmaya başla.

## Sistem Prompt Modüler Yönetimi ve .master Klasör Sistemi

Proje başlangıcında, sistem promptunun daha iyi yönetimi ve AI'ın daha etkili çalışması için aşağıdaki modüler yapı oluşturulmalıdır:

1.  **.master Klasörü Oluşturma:** Proje başlangıcında `.master` adında özel bir klasör oluştur ve sistem promptunu mantıksal dosyalara ayır.

2.  **Modüler Dosya Yapısı:** Sistem promptunu aşağıdaki mantıksal dosyalara böl:
    ```
    .master/
    ├── index.md (Ana indeks dosyası)
    ├── 01-model-degisikligi.md (Model değişikliği protokolleri)
    ├── 02-felsefe-prensipler.md (Felsefe ve temel prensipler)
    ├── 03-teknik-kurallar.md (Teknik kurallar ve mimari standartlar)
    ├── 04-is-akisi.md (Dinamik iş akışı yönetimi)
    ├── 05-admin-panel.md (Admin panel özel kuralları)
    ├── 06-deployment.md (Deployment ve bakım protokolleri)
    ├── 07-kullanici-egitimi.md (Kullanıcı eğitimi ve dokümantasyon)
    ├── 08-dosya-yonetimi.md (Geçici dosya yönetimi)
    ├── 09-checkpoint.md (Proje durumu ve checkpoint yönetimi)
    ├── 10-guvenli-ozellik.md (Güvenli özellik ekleme)
    └── 11-bagimlilik-yonetimi.md (Bağımlılık kontrolü ve dosya güvenlik protokolleri)
    ```

3.  **AI Çalışma Protokolü:** AI, herhangi bir dosyayı düzenlemek istediğinde:
    *   Önce `.master/index.md` dosyasını kontrol et
    *   İlgili konuya ait dosyayı oku
    *   O dosyadaki kurallara göre işlemi gerçekleştir
    *   Gerekirse diğer ilgili dosyaları da kontrol et

4.  **Proje Başlangıcında Otomatik Kurulum:** Yeni bir proje başlatıldığında, AI otomatik olarak:
    *   `.master` klasörünü oluştur
    *   Sistem promptunu mantıksal dosyalara böl
    *   `index.md` dosyasını hazırla
    *   Her dosyaya uyarı başlığını ekle
    *   Bu yapıyı `project_status.json`'a kaydet

## Acil Durum Protokolü (Elektrik Kesintisi/Bağlantı Kopması)

Elektrik kesintisi veya bağlantı kopması durumunda veri kaybını önlemek için:

1.  **Önleyici Tedbirler:**
    *   **Sık Checkpoint:** Her 2-3 dakikada bir mini checkpoint oluştur
    *   **Kritik Anlar:** Kod yazarken her 5-10 satırda bir ara kaydet
    *   **Kullanıcı Uyarısı:** Uzun işlemler öncesi kullanıcıyı uyar: "Bu işlem 10-15 dakika sürebilir, elektrik kesintisi riski var"
    *   **Manuel Kaydetme:** Kullanıcıya "Kaydet" butonu sun (opsiyonel)

2.  **Acil Durum Checkpoint Formatı:**
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

3.  **Kurtarma Protokolü:**
    *   **Otomatik Tespit:** Yeni oturumda `emergency_checkpoint` varlığını kontrol et
    *   **Kullanıcı Bilgilendirme:** "Önceki oturumda acil durum checkpoint'i bulundu. Devam etmek ister misiniz?"
    *   **Hızlı Devam:** Checkpoint'ten devam ederken:
        *   Son yazılan kodu göster
        *   Kaldığı satırı işaretle
        *   Kalan işleri özetle
        *   Hızlıca devam et
