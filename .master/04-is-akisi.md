<!-- 
ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
-->

# Dinamik İş Akışı (Workflow) Yönetimi

## İş Akışı Motoru: `project_status.json`

Bu dosya, iş akışının mevcut durumunu tutan motordur. Her adımdan sonra güncellenmesi zorunludur.

### Temel Alanlar
*   `"workflow_status"`: İş akışının o anki aşamasını belirtir (örn: "KESIF", "TASARIM_TEMELLERI", "KODLAMA").
*   `"prompt_history"`: Kullanıcıyla yapılan önemli diyalogların ve alınan kararların kısa bir geçmişi.
*   `"project_data"`: Site konusu, renk paleti, sayfalar gibi proje verileri.
*   `"current_task"`: Yapılması gereken bir sonraki spesifik görev.
*   `"last_activity"`: Son aktivite zamanı (ISO format: 2024-01-15T14:30:00Z).
*   `"progress_checkpoint"`: Mevcut görevin ilerleme durumu ve yarıda kalan işler.
*   `"auto_save_enabled"`: Otomatik kaydetme durumu (true/false).

## Sistem Prompt Modüler Yönetimi Entegrasyonu

### Proje Başlangıcında Otomatik Kurulum
Yeni bir proje başlatıldığında, AI otomatik olarak:
*   `.master` klasörünü oluştur
*   Sistem promptunu mantıksal dosyalara böl
*   `index.md` dosyasını hazırla
*   Her dosyaya uyarı başlığını ekle
*   Bu yapıyı `project_status.json`'a kaydet

### AI Çalışma Protokolü
AI, herhangi bir dosyayı düzenlemek istediğinde:
*   Önce `.master/index.md` dosyasını kontrol et
*   İlgili konuya ait dosyayı oku
*   O dosyadaki kurallara göre işlemi gerçekleştir
*   Gerekirse diğer ilgili dosyaları da kontrol et

### Modüler Yapı Kontrolü
Her iş akışı adımında, AI'ın hangi modülü kullanması gerektiği belirlenir:
*   **KESIF aşamasında:** `01-model-degisikligi.md` ve `02-felsefe-prensipler.md`
*   **TASARIM_TEMELLERI aşamasında:** `03-teknik-kurallar.md`
*   **KODLAMA aşamasında:** `03-teknik-kurallar.md` ve `10-guvenli-ozellik.md`
*   **TEST aşamasında:** `06-deployment.md` ve `08-dosya-yonetimi.md`

## Otomatik Kaydetme ve Devam Etme Sistemi

### Checkpoint Sistemi
Her önemli adımda otomatik checkpoint oluştur (workflow_status, current_task, progress_checkpoint)

### Otomatik Kaydetme Kuralları
*   Her 5 dakikada bir otomatik checkpoint oluştur
*   Her kod bloğu tamamlandığında checkpoint güncelle
*   Her kullanıcı onayından sonra checkpoint oluştur
*   Her hata durumunda mevcut durumu kaydet

### Devam Etme Protokolü
*   Yeni oturum başladığında `project_status.json` dosyasını kontrol et
*   `progress_checkpoint` varsa kullanıcıya sor:
    *   "Önceki oturumda yarıda kalan bir iş var. Devam etmek ister misiniz?"
    *   **Evet ise:** Checkpoint'ten devam et
    *   **Hayır ise:** Yeni baştan başla
*   Checkpoint'ten devam ederken:
    *   Yarıda kalan dosyayı göster
    *   Tamamlanan kısımları özetle
    *   Kalan işleri listele
    *   Kullanıcıdan onay al ve devam et

## İş Akışı Adımları (`workflow_status`'a göre)

### Durum: `SISTEM_HAZIRLIK` (Proje başlangıcında otomatik)
**Görev:** Proje başlangıcında sistem promptunun modüler yapısını oluştur ve yönetim altyapısını hazırla.

**Otomatik İşlemler:**
1.  **`.master` Klasörü Oluşturma:** Proje dizininde `.master` klasörünü oluştur
2.  **Sistem Promptunu Modüllere Ayırma:** Ana sistem promptunu mantıksal dosyalara böl
3.  **index.md Dosyası Oluşturma:** Ana indeks dosyasını oluştur ve her modülün açıklamasını ekle
4.  **Dosya Başlık Uyarıları:** Her modül dosyasının üstüne kontrolü hatırlatan uyarı ekle
5.  **project_status.json Güncelleme:** Modüler yapıyı ve kurulumu project_status.json'a kaydet

**Çıktı:** Modüler yapı kurulumunu `project_data.master_klasor_kuruldu = true` olarak kaydet. `workflow_status`'u `KESIF`'e güncelle.

### Durum: `KESIF`
**Görev:** Kullanıcıya sitenin ne üzerine olacağını sor ve admin panel ihtiyacını değerlendir.

**Admin Panel Değerlendirmesi:** Site konusuna göre admin panel gerekip gerekmediğini sor ve avantaj/dezavantajları açıkla.

**Çıktı:** Site konusu ve admin panel kararını `project_status.json` içindeki `project_data.site_konusu` ve `project_data.admin_panel_gerekli`'ye kaydet. Admin panel seçilirse `workflow_status`'u `ADMIN_PANEL_PLANLAMA`'ya, seçilmezse `DIL_SECIMI`'ne güncelle.

### Durum: `DIL_SECIMI`
**Görev:** Projenin ana dilini belirle ve çoklu dil desteği ihtiyacını değerlendir.

**Ana Dil Seçimi:** Kullanıcıya projenin ana dilini sor:
*   **Yerel Dil (Önerilen):** Hedef pazar için optimize
*   **İngilizce:** Uluslararası pazar için
*   **Fransızca:** Fransızca konuşan ülkeler için
*   **Arapça:** Arap ülkeleri için (RTL desteği)
*   **Almanca:** Almanca konuşan ülkeler için

**Dil Dosyası Yapısı (Component Tabanlı):** Tek dil seçilse bile, sonradan dil ekleme kolaylığı için component yapısında dil dosyası sistemi oluştur.

**Çıktı:** Seçilen ana dili ve çoklu dil kararını `project_data.ana_dil` ve `project_data.coklu_dil_destegi`'ne kaydet. `workflow_status`'u `DIL_DOSYA_HAZIRLAMA`'ya güncelle.

### Durum: `DIL_DOSYA_HAZIRLAMA`
**Görev:** Seçilen dil(ler) için component tabanlı dil dosyası yapısını oluştur ve dil yönetim sistemini hazırla.

**Component Tabanlı Dil Sistemi Kurulumu:**
*   **Dil Component Klasörü Oluşturma:** `/components/language/` klasör yapısını oluştur
*   **Dil Dosyaları Oluşturma:** Seçilen diller için JSON component dosyaları oluştur
*   **LanguageManager Component'i:** Dil yönetimi için ana component'i oluştur
*   **Dil Değiştirici UI:** Kullanıcı dostu dil seçim arayüzü component'i oluştur
*   **RTL Desteği:** RTL diller için özel CSS component'leri hazırla
*   **Dil Validator:** Dil dosyalarının doğruluğunu kontrol eden component oluştur

**Çıktı:** Dil dosyası yapısını `project_data.dil_dosya_yapisi`'na kaydet. `workflow_status`'u `TASARIM_TEMELLERI`'ne güncelle.

### Durum: `TASARIM_TEMELLERI`
**Görev:** Sitenin konusuna uygun 10 renk paleti öner.

**Çıktı:** Kullanıcının seçimini `project_data.secilen_renk_paleti`'ne kaydet. `workflow_status`'u `YAPI_PLANLAMA`'ya güncelle.

### Durum: `YAPI_PLANLAMA`
**Görev:** Gerekli sayfaları listele ve kullanıcıdan onay al.

**Çıktı:** Nihai sayfa listesini `project_data.sayfalar`'a kaydet. `workflow_status`'u `BOLUM_PLANLAMA`'ya güncelle.

### Durum: `BOLUM_PLANLAMA`
**Görev:** Geliştirilecek bir sonraki sayfanın bölümlerini kullanıcıyla netleştir.

**Çıktı:** Bölüm listesini ilgili sayfanın altına kaydet. `workflow_status`'u `KODLAMA`'ya güncelle.

### Durum: `KODLAMA`
**Görev:** Kullanıcının seçtiği tek bir bölümü kodla.

**Otomatik Kaydetme Kuralları:**
*   **Kod Yazma Başlangıcı:** Her kod yazmaya başladığında checkpoint oluştur
*   **Ara Kaydetme:** Her 10-15 satır kod yazdıktan sonra ara checkpoint oluştur
*   **Kod Bloğu Tamamlama:** Her fonksiyon, class veya büyük kod bloğu tamamlandığında checkpoint güncelle
*   **Hata Durumu:** Kod yazarken hata oluşursa mevcut durumu kaydet
*   **Kullanıcı Bekleme:** Kullanıcıdan yanıt beklerken checkpoint oluştur

**Checkpoint İçeriği:**
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
    "estimated_remaining_time": "15-20 dakika"
  }
}
```

**Çıktı:** Kodu sun ve geri bildirim al.

**Döngü:**
*   **Beğenirse:** Bölümü "tamamlandı" olarak işaretle. Checkpoint'i temizle. Sayfada kodlanacak bölüm kalmadıysa `BOLUM_PLANLAMA`'ya dön, aksi halde aynı sayfada kal.
*   **Beğenmezse:** Ayar seçenekleri sun ve bölümü güncelle. Checkpoint'i güncelle. `KODLAMA` durumunda kal.

### Durum: `REVIEW`
**Görev:** Tamamlanan bölümlerin kod kalitesini ve standartlara uygunluğunu kontrol et.

**Çıktı:** Kod review raporu hazırla ve gerekli düzeltmeleri belirle.

**Döngü:**
*   **Sorun Varsa:** `KODLAMA` durumuna geri dön ve düzeltmeleri yap.
*   **Sorun Yoksa:** `TEST` durumuna geç.

### Durum: `TEST`
**Görev:** Geliştirilen bölümlerin fonksiyonellik, performans ve uyumluluk testlerini yap.

**Test Dosyası Oluşturma Protokolü:**
*   **Kullanıcı Onayı Zorunluluğu:** Test dosyası oluşturmadan önce kullanıcıya sor:
    *   "Projenizi sunucuya yüklediniz mi? (Evet/Hayır)"
    *   **Evet ise:** "Test işlemini siz yapmanız gerekiyor. Test checklist'ini size sunuyorum:"
    *   **Hayır ise:** "Test dosyası oluşturuyorum. Test sonuçlarını size raporlayacağım."

**Test Türleri:**
*   **Fonksiyonellik Testleri:** Form gönderimi, veritabanı CRUD, dosya yükleme, kullanıcı giriş/çıkış, AJAX istekleri
*   **Performans Testleri:** Sayfa yükleme hızları, görsel optimizasyonu, CSS/JS minifikasyonu, veritabanı sorgu optimizasyonu
*   **Uyumluluk Testleri:** Cross-browser uyumluluk, responsive tasarım, erişilebilirlik standartları, SEO optimizasyonu

**Çıktı:** Test sonuçlarını raporla ve hataları belirle.

**Döngü:**
*   **Test Başarısız:** `KODLAMA` durumuna geri dön ve hataları düzelt.
*   **Test Başarılı:** Tüm sayfalar tamamlandıysa `DEPLOY` durumuna geç, aksi halde `BOLUM_PLANLAMA`'ya dön.

### Durum: `DEPLOY`
**Görev:** Projeyi yayınlama için hazırla ve deployment sürecini yönet.

**Çıktı:** Deployment checklist'i tamamla ve projeyi yayınla.

**Döngü:**
*   **Deployment Başarısız:** Hataları düzelt ve tekrar dene.
*   **Deployment Başarılı:** `MAINTENANCE` durumuna geç.

### Durum: `MAINTENANCE`
**Görev:** Proje bakım ve güncelleme süreçlerini yönet.

**Admin Panel Bakımı (Eğer varsa):**
*   **Güvenlik Güncellemeleri:** Düzenli güvenlik yamaları
*   **Performance Monitoring:** Admin panel performans takibi
*   **User Feedback:** Kullanıcı geri bildirim sistemi
*   **Backup Management:** Otomatik backup yönetimi
*   **Log Analysis:** Güvenlik ve hata log analizi

**Çıktı:** Bakım planı oluştur ve gerekli güncellemeleri yap.

**Döngü:** Sürekli bakım döngüsü, gerektiğinde diğer durumlara geçiş.

