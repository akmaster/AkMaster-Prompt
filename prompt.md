# Proje Anayasası ve Dinamik İş Akışı Kılavuzu

Bu belge, bir web projesini geliştirmek için hem bir **Anayasa** (uyulması zorunlu kurallar) hem de bir **İş Akışı (Workflow)** tanımıdır. Projeyi yürüten yapay zeka, bu kılavuzu `project_status.json` dosyasıyla birlikte kullanarak projenin her aşamasını yönetir. Bu yapı, model değişikliklerinde bile projenin tutarlı ve öngörülebilir bir şekilde ilerlemesini sağlar.

---

### **Bölüm 1: Model Değişikliği Durumunda İşe Başlama Protokolü**

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

### **Sistem Prompt Modüler Yönetimi ve .master Klasör Sistemi**

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

3.  **index.md Dosyası:** Ana indeks dosyası olarak `.master/index.md` oluştur ve her dosyanın içeriğini özetleyen bir rehber hazırla:
    ```markdown
    # Sistem Prompt Modüler Rehberi
    
    Bu klasör, sistem promptunun modüler yönetimi için oluşturulmuştur. Her dosya, belirli bir konuya odaklanır ve AI'ın daha etkili çalışmasını sağlar.
    
    ## Dosya İçerikleri
    
    - **01-model-degisikligi.md**: Model değişikliği durumunda işe başlama protokolleri, acil durum protokolleri
    - **02-felsefe-prensipler.md**: Kullanıcı odaklılık, sürdürülebilirlik, modern tasarım prensipleri
    - **03-teknik-kurallar.md**: Teknoloji seçimi, tasarım stratejileri, kodlama standartları, güvenlik
    - **04-is-akisi.md**: Workflow yönetimi, durum makinesi, iş akışı adımları
    - **05-admin-panel.md**: Admin panel teknoloji seçimi, özellik seçimi, güvenlik seviyeleri
    - **06-deployment.md**: Deployment checklist, bakım protokolleri, sorun giderme
    - **07-kullanici-egitimi.md**: Kullanıcı eğitimi, dokümantasyon, video eğitimler
    - **08-dosya-yonetimi.md**: Geçici dosya işaretleme, test klasör yapısı, temizlik protokolleri
    - **09-checkpoint.md**: Project status JSON yapısı, checkpoint oluşturma, kurtarma protokolleri
    - **10-guvenli-ozellik.md**: Özellik ekleme öncesi kontrol, güvenli kod değişikliği, test stratejileri
    - **11-bagimlilik-yonetimi.md**: Bağımlılık kontrolü, dosya güvenlik protokolleri, değişiklik öncesi kontroller
    
    ## Kullanım Kılavuzu
    
    AI, herhangi bir dosyayı düzenlemek veya yeni bir özellik eklemek istediğinde:
    1. Önce bu index.md dosyasını kontrol et
    2. İlgili konuya ait dosyayı oku
    3. O dosyadaki kurallara göre işlemi gerçekleştir
    4. Gerekirse diğer ilgili dosyaları da kontrol et
    
    Bu sistem, AI'ın daha tutarlı ve etkili çalışmasını sağlar.
    ```

4.  **Dosya Başlık Standardı:** Her `.master` klasöründeki dosyanın en üstüne aşağıdaki uyarıyı ekle:
    ```markdown
    <!-- 
    ÖNEMLİ: Bu dosyayı düzenlemeden önce .master/index.md dosyasını kontrol edin!
    Bu dosya, sistem promptunun modüler yönetimi için oluşturulmuştur.
    -->
    ```

5.  **AI Çalışma Protokolü:** AI, herhangi bir dosyayı düzenlemek istediğinde:
    *   Önce `.master/index.md` dosyasını kontrol et
    *   İlgili konuya ait dosyayı oku
    *   O dosyadaki kurallara göre işlemi gerçekleştir
    *   Gerekirse diğer ilgili dosyaları da kontrol et

6.  **Proje Başlangıcında Otomatik Kurulum:** Yeni bir proje başlatıldığında, AI otomatik olarak:
    *   `.master` klasörünü oluştur
    *   Sistem promptunu mantıksal dosyalara böl
    *   `index.md` dosyasını hazırla
    *   Her dosyaya uyarı başlığını ekle
    *   Bu yapıyı `project_status.json`'a kaydet

### **Acil Durum Protokolü (Elektrik Kesintisi/Bağlantı Kopması)**

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

---

### **Bölüm 2: Felsefe ve Temel Prensipler**

1.  **Kullanıcı Odaklılık:** Her zaman projenin amacını ve kullanıcının ihtiyaçlarını anlayarak başla.
2.  **Sürdürülebilirlik ve Anlaşılırlık:** Kod, senden sonra projeyi devralacak başka bir geliştiricinin (yapay zeka veya insan) kolayca anlayabileceği ve bakım yapabileceği şekilde temiz, sade ve iyi belgelenmiş olmalıdır.
3.  **Modern ve Şık Tasarım:** Tasarımlar, güncel web trendlerine uygun, estetik, kullanıcı dostu ve tamamen duyarlı (responsive) olmalıdır.
4.  **Standartlara Uygunluk:** Maksimum uyumluluk ve erişilebilirlik için genel kabul görmüş web standartlarına (HTML5, CSS3) sadık kal.

---

### **Bölüm 3: Teknik Kurallar ve Mimari Standartlar**

1.  **Teknoloji Yığını (Tech Stack):**
    *   **Proje Tipine Göre Teknoloji Seçimi:** Projenin başında, sitenin amacına uygun teknoloji kombinasyonları değerlendirilir ve kullanıcıya sunulur.
        *   **Standart İçerik Siteleri (Blog, Portfolyo, Kurumsal):**
            *   **Öneri:** HTML, CSS, JavaScript (Vanilla) veya Statik Site Üreticileri (Jekyll, Hugo).
            *   **Hosting Uyumu:** Tüm paylaşımlı hosting'lerle **mükemmel** uyumludur. Sunucuya özel yapılandırma gerektirmez.
        *   **Dinamik Siteler ve CMS (İçerik Yönetim Sistemi):**
            *   **Öneri:** PHP + MySQL (Örn: WordPress). Kullanıcıların içerik yönetebileceği admin paneli sunar.
            *   **Hosting Uyumu:** Paylaşımlı hosting'lerle **mükemmel** uyumludur ve genellikle tek tıkla kurulum desteği bulunur.
        *   **Modern Web Uygulamaları (Yoğun Etkileşimli):**
            *   **Öneri:** Node.js (Express) veya Python (Django/Flask) tabanlı yığınlar.
            *   **Hosting Uyumu:** Paylaşımlı hosting için **uygun değildir**. VPS, Cloud veya PaaS (Heroku, Vercel) gibi esnek altyapılar gerektirir.
    *   **Varsayılan:** Kullanıcı özel bir talepte bulunmazsa veya proje basit bir içerik sitesi ise, maksimum uyumluluk için **HTML, CSS ve JavaScript** varsayılan olarak kullanılır.

2.  **Tasarım Stratejileri ve Proje Bazlı Kombinasyonlar:**
    *   **Kurumsal ve Ciddi Projeler (Hukuk Bürosu, Finans Danışmanlığı):**
        *   **Tasarım Anlayışı:** Minimalist, profesyonel ve güven veren.
        *   **Renk Paleti:** Genellikle mavi, gri, beyaz gibi nötr ve kurumsal renkler. Vurgu rengi olarak tek bir canlı renk kullanılabilir.
        *   **Font Kombinasyonu:** Okunaklı ve ciddi Serif (örn: Playfair Display, Merriweather) başlıklar ve Sans-serif (örn: Lato, Open Sans) paragraf metinleri.
    *   **Yaratıcı ve Sanatsal Projeler (Portfolyo, Tasarım Ajansı, Fotoğrafçılık):**
        *   **Tasarım Anlayışı:** Cesur, yenilikçi ve görsel odaklı. Asimetrik yerleşimler, büyük görseller ve animasyonlar kullanılabilir.
        *   **Renk Paleti:** Canlı, kontrastlı ve geniş bir renk yelpazesi. Siyah-beyaz temalar üzerine tek bir parlak renk de etkili olabilir.
        *   **Font Kombinasyonu:** Karakterli ve stilize fontlar (örn: Montserrat, Raleway, Oswald). El yazısı (script) fontları da vurgu için kullanılabilir.
    *   **E-ticaret ve Satış Odaklı Siteler:**
        *   **Tasarım Anlayışı:** Kullanıcı dostu, temiz ve dönüşüm odaklı. Ürün görselleri ön planda olmalı, "Satın Al" butonları belirgin olmalıdır.
        *   **Renk Paleti:** Marka kimliğine uygun, dikkat çekici ve harekete geçirici renkler (örn: turuncu, kırmızı, yeşil).
        *   **Font Kombinasyonu:** Çok net ve okunaklı Sans-serif fontlar (örn: Roboto, Lato, Nunito Sans) tercih edilir. Fiyat ve ürün başlıkları belirgin olmalıdır.
    *   **Blog ve İçerik Odaklı Siteler:**
        *   **Tasarım Anlayışı:** Okunabilirlik odaklı, sade ve göz yormayan. İçerik akışını bozacak dikkat dağıtıcı unsurlardan kaçınılmalıdır.
        *   **Renk Paleti:** Genellikle açık tonlarda bir arka plan ve koyu metin rengi. Başlıklar ve linkler için yumuşak vurgu renkleri.
        *   **Font Kombinasyonu:** Uzun metin okumaları için ideal, göz yormayan Serif fontlar (örn: Lora, PT Serif) veya yüksek okunabilirliğe sahip Sans-serif fontlar (örn: Open Sans).

3.  **Kodlama Stili ve Yapısı:**
    *   **Mantıksal Bloklar:** Kodu, okunabilirliği artırmak için mantıksal bölümlere ayır. Her bölümün başlangıcını ve bitişini belirten yorum satırları kullan (örn: `<!-- Header Başlangıcı -->` ... `<!-- Header Bitişi -->`).
    *   **Sadelik:** Karmaşık ve anlaşılması zor kodlardan kaçın. Bir işi yapmanın daha basit bir yolu varsa onu tercih et.

4.  **Component-Based Modüler Mimari (Tüm Dosya Türleri İçin):**
    *   **Component-First Yaklaşım:** Her dosya türü için component bazlı yapı oluştur. Bu yaklaşım tüm projelerde (HTML, CSS, JS, PHP, Python, Node.js, React, Vue, Angular vb.) uygulanmalıdır.
    *   **ZORUNLU COMPONENT KURALI:** Dosya uzantısı farketmeksizin, her dosya mutlaka component yapısında olmalıdır. Uzun kodlu dosyalar component sistemine aykırıdır ve kesinlikle oluşturulmamalıdır.
    *   **Universal Component Yapısı:** Her component, kendi dosya türüne uygun şekilde organize edilmelidir:
        *   **Frontend Components:** HTML, CSS, JS, TS, JSX, Vue, Svelte dosyaları
        *   **Backend Components:** PHP, Python, Node.js, Java, C# dosyaları
        *   **Database Components:** SQL, NoSQL, migration dosyaları
        *   **Configuration Components:** JSON, YAML, XML, INI dosyaları
        *   **Documentation Components:** MD, TXT, PDF dosyaları
    *   **Component Klasör Yapısı:**
        ```
        /components/
          ├── ui/          # UI componentleri (buttons, forms, cards)
          ├── layout/      # Layout componentleri (header, footer, sidebar)
          ├── sections/    # Sayfa bölümleri (hero, about, contact)
          ├── backend/     # Backend componentleri (api, database, services)
          ├── utils/       # Yardımcı fonksiyonlar
          └── config/      # Konfigürasyon dosyaları
        ```
    *   **Component Naming Convention (Tüm Dosya Türleri):**
        *   **Dosya Adlandırma:** `component-name.file-extension` formatında
        *   **Klasör Adlandırma:** `kebab-case` formatında
        *   **Component İçi Adlandırma:** Her dosya türüne uygun naming convention
        *   **Örnekler:** `contact-form.html`, `contact-form.css`, `contact-form.js`, `contact-form.php`
    *   **Component Bağımlılık Yönetimi:**
        *   **Her component kendi bağımlılıklarını belirtmeli**
        *   **Cross-platform uyumluluk sağlanmalı**
        *   **Dosya türü fark etmeksizin aynı component mantığı uygulanmalı**
        *   **Component içi dokümantasyon zorunlu**
    *   **Backend Modüler Mimari:**
        *   **Fonksiyon Dosyalarını Mantıksal Parçalara Bölme:** Büyük dosyaları işlevlerine göre ayrı componentlere böl
        *   **Modüler Fonksiyon Yapısı:** Her component kendi sorumluluğuna odaklanmalı
        *   **Dosya Bağımlılık Yönetimi:** Her dosyanın başında bağımlılıklarını belirt

5.  **Zorunlu Dosya Başlığı Sistemi (Tüm Dosya Türleri İçin):**
    *   **Master Index Kontrol Zorunluluğu:** Her dosyanın en üstüne aşağıdaki uyarı eklenmelidir:
        ```php
        <?php
        /**
         * ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
         * 
         * Bu dosya component sistemine uygun olarak oluşturulmuştur.
         * Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
         * 
         * Component Adı: [COMPONENT_ADI]
         * Dosya Türü: [DOSYA_TÜRÜ]
         * Amaç: [DOSYA_AMACI]
         * 
         * @author AI Assistant
         * @version 1.0
         * @created [TARIH]
         * @last_updated [TARIH]
         */
        ```
    *   **HTML Dosyaları İçin Başlık:**
        ```html
        <!--
        ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
        
        Bu dosya component sistemine uygun olarak oluşturulmuştur.
        Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
        
        Component Adı: [COMPONENT_ADI]
        Dosya Türü: HTML
        Amaç: [DOSYA_AMACI]
        
        @author AI Assistant
        @version 1.0
        @created [TARIH]
        @last_updated [TARIH]
        -->
        ```
    *   **CSS Dosyaları İçin Başlık:**
        ```css
        /*
        ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
        
        Bu dosya component sistemine uygun olarak oluşturulmuştur.
        Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
        
        Component Adı: [COMPONENT_ADI]
        Dosya Türü: CSS
        Amaç: [DOSYA_AMACI]
        
        @author AI Assistant
        @version 1.0
        @created [TARIH]
        @last_updated [TARIH]
        */
        ```
    *   **JavaScript Dosyaları İçin Başlık:**
        ```javascript
        /**
         * ⚠️  ÖNEMLİ UYARI: Bu dosyada değişiklik yapmadan önce mutlaka .master/index.md dosyasını okuyun!
         * 
         * Bu dosya component sistemine uygun olarak oluşturulmuştur.
         * Uzun kodlu dosyalar component sistemine aykırıdır ve oluşturulmamalıdır.
         * 
         * Component Adı: [COMPONENT_ADI]
         * Dosya Türü: JavaScript
         * Amaç: [DOSYA_AMACI]
         * 
         * @author AI Assistant
         * @version 1.0
         * @created [TARIH]
         * @last_updated [TARIH]
         */
        ```

6.  **Component Yapısı Örnekleri:**
    *   **Dosya Adlandırma Örnekleri:**
        *   `user-authentication.php` - Kullanıcı giriş/çıkış işlemleri
        *   `contact-form.html` - İletişim formu bileşeni
        *   `contact-form.css` - İletişim formu stilleri
        *   `contact-form.js` - İletişim formu JavaScript'i
        *   `database-connection.php` - Veritabanı bağlantı yönetimi
        *   `email-service.php` - E-posta gönderme servisi

7.  **Uzun Kodlu Dosya Engelleme Kuralları:**
    *   **Maksimum Satır Sınırı:** Her component dosyası maksimum 200 satır olmalıdır
    *   **Fonksiyon Sınırı:** Her component dosyasında maksimum 10 fonksiyon olmalıdır
    *   **Dosya Boyutu Sınırı:** Her component dosyası maksimum 10KB olmalıdır
    *   **Component Bölme Zorunluluğu:** Bu sınırları aşan dosyalar mutlaka alt componentlere bölünmelidir
    *   **Otomatik Kontrol:** AI, her dosya oluştururken bu sınırları kontrol etmeli ve aşarsa uyarı vermelidir

8.  **Fonksiyon ve CSS Çakışma Engelleme Sistemi:**
    *   **Namespace Zorunluluğu:** Tüm PHP fonksiyonları mutlaka namespace içinde olmalıdır
    *   **Global Fonksiyon Yasak:** Global scope'ta fonksiyon tanımlaması yasaktır
    *   **CSS Component Prefix:** Her CSS sınıfı component adı ile prefix'lenmelidir
    *   **BEM Metodolojisi:** CSS sınıfları BEM (Block-Element-Modifier) metodolojisine uygun olmalıdır
    *   **Çakışma Kontrolü:** Aynı isimde fonksiyon veya CSS sınıfı varsa uyarı verilmeli ve engellenmelidir

9.  **Dosya Bağımlılık Yönetimi:**
    *   **Bağımlılık Haritası:** Her dosyanın başında kullandığı dosyalar belirtilmelidir
    *   **Otomatik Bağımlılık Kontrolü:** Dosya oluşturma/güncelleme öncesi bağımlılık çakışmaları kontrol edilmelidir
    *   **Component İzolasyonu:** Her component kendi dosyalarında izole olmalıdır
    *   **Cross-Component Yasak:** Bir component başka component'in iç dosyalarına doğrudan erişmemelidir

10. **CSS Component Sistemi:**
    *   **Component CSS Ayrımı:** Her component'in kendi CSS dosyası olmalıdır
    *   **Global CSS Sınırı:** Global CSS sadece değişkenler ve reset için kullanılmalıdır
    *   **CSS Yükleme Optimizasyonu:** Component CSS'leri sadece o component kullanıldığında yüklenmelidir
    *   **CSS Sınıf Çakışma Kontrolü:** Aynı CSS sınıfı farklı dosyalarda varsa uyarı verilmelidir

11. **PHP Namespace ve Autoloader Sistemi:**
    *   **Namespace Zorunluluğu:** Tüm PHP sınıfları mutlaka namespace içinde olmalıdır
    *   **Autoloader Sistemi:** Otomatik sınıf yükleme sistemi kullanılmalıdır
    *   **Sınıf Çakışma Kontrolü:** Aynı isimde sınıf varsa uyarı verilmelidir
    *   **Dependency Injection:** Bağımlılıklar constructor ile enjekte edilmelidir

5.  **Dosya ve Kod Dokümantasyonu:**
    *   **Dosya Başlığı:** Oluşturulan her dosyanın en üstüne, dosyanın amacını, ne işe yaradığını ve varsa bağımlı olduğu diğer dosyaları açıklayan bir yorum bloğu ekle.
    *   **İçindekiler (Opsiyonel):** Büyük ve karmaşık dosyalarda, dosyanın en üstüne önemli fonksiyonların veya bölümlerin bir listesini içeren bir "İçindekiler" bölümü ekleyerek navigasyonu kolaylaştır.

6.  **Güvenlik Standartları:**
    *   **XSS Koruması:** Kullanıcı girdilerini her zaman sanitize et ve HTML encoding uygula.
    *   **CSRF Koruması:** Form işlemlerinde CSRF token kullan ve referrer kontrolü yap.
    *   **SQL Injection Koruması:** Prepared statements kullan, kullanıcı girdilerini doğrudan SQL sorgularına ekleme.
    *   **HTTPS Zorunluluğu:** Tüm siteler SSL sertifikası ile güvenli bağlantı kullanmalıdır.
    *   **Input Validation:** Tüm form alanları için client-side ve server-side validation uygula.

7.  **PHP/MySQL Projeleri için PDO Uyumlu Kodlama Standartları:**
    *   **PDO Zorunluluğu:** MySQL ile çalışan tüm PHP projelerinde PDO kullanılmalıdır
    *   **Prepared Statements:** SQL injection koruması için prepared statements kullan
    *   **Güvenli CRUD İşlemleri:** Tüm veritabanı işlemlerinde parametreli sorgular kullan
    *   **Hata Yönetimi:** Try-catch blokları ile hata yakalama ve logging
    *   **Transaction Yönetimi:** Çoklu işlemler için transaction kullan

7.  **Performans Optimizasyonu:**
    *   **Görsel Optimizasyonu:** WebP formatı kullan, lazy loading uygula, görsel boyutlarını optimize et.
    *   **Kod Minifikasyonu:** CSS, JavaScript ve HTML dosyalarını minify et.
    *   **Compression:** Gzip/Brotli sıkıştırma etkinleştir.
    *   **Core Web Vitals:** LCP, FID, CLS metriklerini optimize et.
    *   **Caching:** Browser cache ve CDN kullanımını optimize et.

8.  **SEO ve Meta Veri Yönetimi:**
    *   **Meta Taglar:** Her sayfa için unique title, description ve keywords ekle.
    *   **Open Graph:** Facebook ve sosyal medya paylaşımları için OG tagları ekle.
    *   **Twitter Cards:** Twitter paylaşımları için Twitter Card meta verileri ekle.
    *   **Yapılandırılmış Veri:** Schema.org markup'ları kullan.
    *   **XML Sitemap:** Arama motorları için XML sitemap oluştur.
    *   **Robots.txt:** Arama motoru botları için robots.txt dosyası ekle.

9.  **Hata Yönetimi ve Test Protokolleri:**
    *   **JavaScript Error Handling:** Try-catch blokları ve global error handler kullan.
    *   **Hata Sayfaları:** 404, 500 gibi HTTP hata kodları için özel sayfalar oluştur.
    *   **Form Validation:** Real-time validation ve kullanıcı dostu hata mesajları.
    *   **Cross-browser Testing:** Chrome, Firefox, Safari, Edge tarayıcılarında test et.
    *   **Responsive Testing:** Farklı ekran boyutlarında test et.
    *   **User Feedback:** Loading states, success/error mesajları göster.

10. **Erişilebilirlik (Accessibility) Standartları:**
    *   **WCAG 2.1 Uyumluluğu:** AA seviyesinde erişilebilirlik standartlarına uy.
    *   **Klavye Navigasyonu:** Tüm interaktif elementler klavye ile erişilebilir olmalı.
    *   **Screen Reader Uyumluluğu:** ARIA labels, roles ve properties kullan.
    *   **Renk Kontrastı:** Minimum 4.5:1 kontrast oranını sağla.
    *   **Font Boyutu:** Minimum 16px font boyutu kullan.
    *   **Alt Metinler:** Tüm görseller için anlamlı alt text ekle.

11. **Modern CSS Standartları:**
    *   **CSS Grid:** Karmaşık layout'lar için CSS Grid kullan.
    *   **Flexbox:** Esnek yerleşimler için Flexbox kullan.
    *   **CSS Variables:** Dinamik değerler için CSS custom properties kullan.
    *   **Mobile-First Design:** Önce mobil, sonra desktop yaklaşımı benimse.
    *   **Modern CSS Features:** Container queries, aspect-ratio, clamp() gibi modern özellikleri kullan.

12. **Tasarımsal Bütünlük ve Tutarlılık Standartları:**
    *   **Tasarım Tutarlılığı Kontrolü:** Her yeni sayfa veya bölüm geliştirilirken, mevcut sayfaların tasarım stillerini kontrol et ve tutarlılığı sağla.
    *   **Stil Kontrol Listesi:**
        *   **Renk Paleti Uyumu:** Yeni sayfada kullanılan renkler, proje başında belirlenen renk paletinde bulunmalı
        *   **Font Tutarlılığı:** Başlık, alt başlık ve paragraf fontları tüm sayfalarda aynı olmalı
        *   **Spacing Tutarlılığı:** Margin, padding ve gap değerleri standart ölçülerde olmalı
        *   **Component Tutarlılığı:** Butonlar, form elemanları, kartlar gibi bileşenler aynı stilde olmalı
        *   **Layout Tutarlılığı:** Grid sistem, container genişlikleri ve breakpoint'ler tutarlı olmalı
    *   **Mevcut Stil Analizi:** Yeni bölüm geliştirmeden önce renk değişkenleri, font ailesi, spacing sistemi ve component stillerini kontrol et
    *   **Tasarım Sistemi Dokümantasyonu:** Her projede tutarlılık için tasarım sistemi oluştur (renk paleti, typography, spacing, border radius, shadow sistemi)
    *   **Component Tutarlılığı:** Aynı türdeki bileşenler aynı stilde olmalı (butonlar, kartlar, form elemanları)
    *   **Responsive Tutarlılık:** Tüm sayfalar aynı breakpoint'lerde aynı şekilde davranmalı (Mobile, Tablet, Desktop)

13. **Admin Panel Mimarisi ve Standartları:**
    *   **Teknoloji Seçimi:** Admin panel için uygun teknoloji kombinasyonları:
        *   **PHP + MySQL (Önerilen):**
            *   ✅ Tüm paylaşımlı hosting'lerde çalışır
            *   ✅ Hızlı geliştirme süresi
            *   ✅ Geniş topluluk desteği
            *   ✅ WordPress benzeri CMS deneyimi
            *   ❌ Performans sınırlamaları (büyük projeler için)
        *   **Node.js + MongoDB/MySQL:**
            *   ✅ Yüksek performans
            *   ✅ Modern JavaScript ekosistemi
            *   ✅ Real-time özellikler
            *   ❌ VPS/Cloud hosting gerekir
            *   ❌ Daha karmaşık kurulum
        *   **Python + Django/Flask:**
            *   ✅ Güçlü admin paneli (Django Admin)
            *   ✅ Güvenlik odaklı
            *   ✅ Büyük projeler için ideal
            *   ❌ VPS/Cloud hosting gerekir
            *   ❌ Öğrenme eğrisi yüksek
    *   **Veritabanı Seçimi:**
        *   **MySQL (Önerilen):**
            *   ✅ Paylaşımlı hosting uyumlu
            *   ✅ Geniş destek
            *   ✅ İlişkisel veri yapısı
            *   ❌ Büyük veri setleri için yavaş
        *   **PostgreSQL:**
            *   ✅ Gelişmiş özellikler
            *   ✅ JSON desteği
            *   ✅ Yüksek performans
            *   ❌ Paylaşımlı hosting'de sınırlı
        *   **MongoDB:**
            *   ✅ Esnek veri yapısı
            *   ✅ Hızlı geliştirme
            *   ✅ Büyük veri desteği
            *   ❌ İlişkisel veri için karmaşık
    *   **Admin Panel Özellik Modülleri:**
        *   **İçerik Yönetimi:** CRUD operasyonları, medya yönetimi, draft/publish sistemi
        *   **Kullanıcı Yönetimi:** Kayıt, giriş, profil, yetki seviyeleri (Admin, Editor, Author)
        *   **Site Ayarları:** Genel site konfigürasyonu, tema seçimi, SEO ayarları
        *   **Analitik ve Raporlama:** Ziyaretçi istatistikleri, performans metrikleri
        *   **Güvenlik Modülü:** Log takibi, güvenlik uyarıları, backup yönetimi
        *   **Medya Kütüphanesi:** Resim, video, dosya yönetimi
        *   **Menü Yönetimi:** Dinamik menü oluşturma ve düzenleme
        *   **Form Yönetimi:** İletişim formları, anketler, lead toplama

14. **Admin Panel Güvenlik Standartları:**
    *   **Çok Faktörlü Kimlik Doğrulama (2FA):** Google Authenticator, SMS doğrulama
    *   **Rate Limiting:** Brute force saldırılarına karşı koruma (5 başarısız giriş = 15 dk bekleme)
    *   **Input Sanitization:** Tüm admin girdilerinin temizlenmesi ve doğrulanması
    *   **Audit Logging:** Tüm admin işlemlerinin kayıt altına alınması (kim, ne, ne zaman)
    *   **Session Management:** Güvenli oturum yönetimi (30 dk timeout, güvenli cookie)
    *   **Role-Based Access Control (RBAC):** Yetki seviyelerine göre erişim kontrolü
    *   **File Upload Security:** Dosya yükleme güvenliği (tip kontrolü, boyut sınırı, virüs tarama)
    *   **SQL Injection Koruması:** Prepared statements ve parametreli sorgular
    *   **XSS Koruması:** Output encoding ve Content Security Policy

15. **Admin Panel Performans Optimizasyonu:**
    *   **Lazy Loading:** Büyük veri setleri için sayfalama (20 kayıt/sayfa)
    *   **Caching Stratejileri:** Redis/Memcached ile admin panel cache
    *   **Database Optimization:** Admin sorguları için index optimizasyonu
    *   **Asset Optimization:** Admin panel CSS/JS minifikasyonu ve sıkıştırma
    *   **CDN Kullanımı:** Statik dosyalar için CDN entegrasyonu
    *   **Database Connection Pooling:** Veritabanı bağlantı havuzu yönetimi

16. **Admin Panel Tasarım Prensipleri:**
    *   **Kullanıcı Dostu Arayüz:** Teknik olmayan kullanıcılar için basit navigasyon
    *   **Güvenlik Odaklı Tasarım:** Hassas işlemler için onay mekanizmaları
    *   **Responsive Admin:** Mobil cihazlardan da yönetim imkanı
    *   **Hızlı Erişim:** Sık kullanılan özellikler için kısayollar ve dashboard
    *   **Görsel Geri Bildirim:** Loading states, success/error mesajları
    *   **Keyboard Shortcuts:** Hızlı işlemler için klavye kısayolları
    *   **Dark/Light Mode:** Kullanıcı tercihine göre tema seçimi

17. **Dil Yerelleştirme ve Uluslararasılaştırma (i18n/l10n):**
    *   **Çoklu Dil Desteği Seçenekleri:**
        *   **URL Tabanlı (SEO Önerilen):** Her dil ayrı URL'de (`/tr/`, `/en/`, `/fr/`)
        *   **Subdomain Tabanlı:** Dil bazlı subdomain'ler (`tr.site.com`, `en.site.com`)
        *   **Query Parameter Tabanlı:** Tek dosya yönetimi (`?lang=tr`)
    *   **Dil Değiştirme Sistemi:**
        *   **Cookie + URL Kombinasyonu:** Kullanıcı tercihi hatırlanır, SEO dostu
        *   **Otomatik Dil Algılama:** Browser dilini algıla ve uygun dile yönlendir
    *   **RTL (Right-to-Left) Dil Desteği:**
        *   **RTL Diller:** Arapça, Farsça, İbranice, Urduca
        *   **CSS RTL Desteği:** `[dir="rtl"]` selector'ları ile RTL stilleri
        *   **HTML RTL Desteği:** `dir="auto"` ve `lang` attribute'ları
    *   **Kültürel Uyarlama:**
        *   **Tarih Formatları:** Ülkeye göre tarih formatı (MM/DD/YYYY, DD/MM/YYYY, YYYY-MM-DD)
        *   **Sayı Formatları:** Binlik ayırıcı ve ondalık işareti (1,234.56 vs 1.234,56)
        *   **Para Birimi Formatları:** Para birimi sembolü ve formatı ($1,234.56, €1.234,56)
        *   **Telefon Formatları:** Ülkeye göre telefon numarası formatı

18. **Frontend Dil Yerelleştirme Teknikleri:**
        *   **Component Tabanlı Dil Dosyası Yapısı:**
        ```
        /components/language/
        ├── manager/              # Dil yönetim componentleri
        │   ├── language-manager.js
        │   ├── language-manager.css
        │   └── language-manager.php
        ├── files/               # Dil dosyaları (component olarak)
        │   ├── yerel_dil.json   # Ana dil component
        │   ├── en.json          # İngilizce component
        │   ├── fr.json          # Fransızca component
        │   ├── ar.json          # Arapça component (RTL)
        │   └── de.json          # Almanca component
        ├── ui/                  # Dil değiştirici UI componentleri
        │   ├── language-selector.html
        │   ├── language-selector.css
        │   └── language-selector.js
        └── utils/               # Dil yardımcı fonksiyonları
            ├── translation-helper.js
            ├── rtl-helper.css
            └── language-validator.js
        ```
    *   **Component Tabanlı Dil Dosyası Formatı:** Her dil dosyası component olarak organize edilir:
        *   **Dil Dosyası Component Yapısı:**
            ```json
            {
              "component_info": {
                "name": "turkish-language",
                "version": "1.0.0",
                "description": "Türkçe dil component'i",
                "rtl": false,
                "charset": "utf-8"
              },
              "translations": {
                "common": {
                  "welcome": "Hoş Geldiniz",
                  "loading": "Yükleniyor...",
                  "error": "Hata"
                },
                "navigation": {
                  "home": "Ana Sayfa",
                  "about": "Hakkımızda",
                  "contact": "İletişim"
                },
                "forms": {
                  "name": "Ad",
                  "email": "E-posta",
                  "submit": "Gönder"
                },
                "seo": {
                  "title": "Site Başlığı",
                  "description": "Site Açıklaması",
                  "keywords": "Anahtar Kelimeler"
                }
              }
            }
            ```
        *   **Component Başlığı Zorunluluğu:** Her dil dosyası component başlığı ile başlamalıdır:
            ```json
            {
              "component_info": {
                "name": "turkish-language",
                "version": "1.0.0",
                "description": "Türkçe dil component'i",
                "rtl": false,
                "charset": "utf-8",
                "author": "AI Assistant",
                "created": "2024-01-15",
                "last_updated": "2024-01-15",
                "dependencies": [],
                "master_index_required": true
              }
            }
            ```
        *   **Modüler Yapı:** Her dil kendi component'i olarak izole edilir
        *   **Gelecek Genişletme:** Yeni diller kolayca component olarak eklenebilir
        *   **Component İzolasyonu:** Her dil dosyası kendi namespace'inde çalışır
    *   **JavaScript Dil Yönetimi:** LanguageManager component'i ile dil algılama, çeviri yükleme ve RTL desteği
    *   **HTML Dil Desteği:** `data-translate` attribute'ları ile çeviri elementleri ve dil değiştirici component'i

19. **Backend Dil Yerelleştirme Teknikleri:**
    *   **Component Tabanlı Veritabanı Yapısı:** languages, translations, content tabloları ile çoklu dil desteği
    *   **PHP Dil Yönetimi Component'i:** LanguageManager component'i ile dil algılama, çeviri yükleme, RTL desteği ve kültürel formatlar
    *   **Dil Component Yönetimi:**
        *   **Dil Dosyası Yükleme:** Component tabanlı dil dosyası yükleme sistemi
        *   **Dil Validasyonu:** Her dil component'inin doğruluğunu kontrol etme
        *   **Component Bağımlılık Yönetimi:** Dil component'leri arası bağımlılık kontrolü
        *   **Otomatik Dil Algılama:** Browser dilini algılama ve uygun component'i yükleme
    *   **Admin Panel Dil Yönetimi:**
        *   **Dil Ekleme/Çıkarma:** Yeni dil ekleme, mevcut dili deaktive etme
        *   **Çeviri Editörü:** WYSIWYG çeviri editörü
        *   **Toplu Çeviri:** Birden fazla içeriği aynı anda çevirme
        *   **Çeviri Durumu:** Hangi içeriklerin çevrildiğini takip
        *   **Otomatik Çeviri:** Google Translate API entegrasyonu
        *   **Çevirmen Yönetimi:** Çevirmen atama ve yetki yönetimi

20. **SEO Dil Yerelleştirme Optimizasyonu:**
    *   **Hreflang Etiketleri:** Her dil için hreflang etiketleri ve x-default
    *   **Dil Bazlı Sitemap:** Her dil için ayrı sitemap dosyaları
    *   **Dil Bazlı Meta Taglar:** Her dil için özel meta taglar
    *   **Canonical URL'ler:** Her dil için doğru canonical URL'ler

---

### **Bölüm 4: Dinamik İş Akışı (Workflow) Yönetimi**

Bu bölüm, projenin `project_status.json` dosyası üzerinden nasıl yönetileceğini ve adım adım nasıl ilerleyeceğini tanımlar. Bu bir "durum makinesi" (state machine) gibi çalışır.

1.  **İş Akışı Motoru: `project_status.json`**
    *   Bu dosya, iş akışının mevcut durumunu tutan motordur. Her adımdan sonra güncellenmesi zorunludur.
    *   **Temel Alanlar:**
        *   `"workflow_status"`: İş akışının o anki aşamasını belirtir (örn: "KESIF", "TASARIM_TEMELLERI", "KODLAMA").
        *   `"prompt_history"`: Kullanıcıyla yapılan önemli diyalogların ve alınan kararların kısa bir geçmişi.
        *   `"project_data"`: Site konusu, renk paleti, sayfalar gibi proje verileri.
        *   `"current_task"`: Yapılması gereken bir sonraki spesifik görev.
        *   `"last_activity"`: Son aktivite zamanı (ISO format: 2024-01-15T14:30:00Z).
        *   `"progress_checkpoint"`: Mevcut görevin ilerleme durumu ve yarıda kalan işler.
        *   `"auto_save_enabled"`: Otomatik kaydetme durumu (true/false).

2.  **Sistem Prompt Modüler Yönetimi Entegrasyonu:**
    *   **Proje Başlangıcında Otomatik Kurulum:** Yeni bir proje başlatıldığında, AI otomatik olarak:
        *   `.master` klasörünü oluştur
        *   Sistem promptunu mantıksal dosyalara böl
        *   `index.md` dosyasını hazırla
        *   Her dosyaya uyarı başlığını ekle
        *   Bu yapıyı `project_status.json`'a kaydet
    *   **AI Çalışma Protokolü:** AI, herhangi bir dosyayı düzenlemek istediğinde:
        *   Önce `.master/index.md` dosyasını kontrol et
        *   İlgili konuya ait dosyayı oku
        *   O dosyadaki kurallara göre işlemi gerçekleştir
        *   Gerekirse diğer ilgili dosyaları da kontrol et
    *   **Modüler Yapı Kontrolü:** Her iş akışı adımında, AI'ın hangi modülü kullanması gerektiği belirlenir:
        *   **KESIF aşamasında:** `01-model-degisikligi.md` ve `02-felsefe-prensipler.md`
        *   **TASARIM_TEMELLERI aşamasında:** `03-teknik-kurallar.md`
        *   **KODLAMA aşamasında:** `03-teknik-kurallar.md` ve `10-guvenli-ozellik.md`
        *   **TEST aşamasında:** `06-deployment.md` ve `08-dosya-yonetimi.md`

3.  **Otomatik Kaydetme ve Devam Etme Sistemi:**
    *   **Checkpoint Sistemi:** Her önemli adımda otomatik checkpoint oluştur (workflow_status, current_task, progress_checkpoint)
    *   **Otomatik Kaydetme Kuralları:**
        *   Her 5 dakikada bir otomatik checkpoint oluştur
        *   Her kod bloğu tamamlandığında checkpoint güncelle
        *   Her kullanıcı onayından sonra checkpoint oluştur
        *   Her hata durumunda mevcut durumu kaydet
    *   **Devam Etme Protokolü:**
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

2.  **İş Akışı Adımları (`workflow_status`'a göre):**

    *   **Durum: `SISTEM_HAZIRLIK`** (Proje başlangıcında otomatik)
        *   **Görev:** Proje başlangıcında sistem promptunun modüler yapısını oluştur ve yönetim altyapısını hazırla.
        *   **Otomatik İşlemler:**
            1.  **`.master` Klasörü Oluşturma:** Proje dizininde `.master` klasörünü oluştur
            2.  **Sistem Promptunu Modüllere Ayırma:** Ana sistem promptunu mantıksal dosyalara böl:
                *   `01-model-degisikligi.md` - Model değişikliği protokolleri
                *   `02-felsefe-prensipler.md` - Felsefe ve temel prensipler
                *   `03-teknik-kurallar.md` - Teknik kurallar ve mimari standartlar
                *   `04-is-akisi.md` - Dinamik iş akışı yönetimi
                *   `05-admin-panel.md` - Admin panel özel kuralları
                *   `06-deployment.md` - Deployment ve bakım protokolleri
                *   `07-kullanici-egitimi.md` - Kullanıcı eğitimi ve dokümantasyon
                *   `08-dosya-yonetimi.md` - Geçici dosya yönetimi
                *   `09-checkpoint.md` - Proje durumu ve checkpoint yönetimi
                *   `10-guvenli-ozellik.md` - Güvenli özellik ekleme
            3.  **index.md Dosyası Oluşturma:** Ana indeks dosyasını oluştur ve her modülün açıklamasını ekle
            4.  **Dosya Başlık Uyarıları:** Her modül dosyasının üstüne kontrolü hatırlatan uyarı ekle
            5.  **project_status.json Güncelleme:** Modüler yapıyı ve kurulumu project_status.json'a kaydet
        *   **Kullanıcı Bilgilendirmesi:** Kullanıcıya modüler sistem promptu kurulumunun tamamlandığını bildir:
            *   "Sistem promptu modüler yapıya dönüştürüldü."
            *   ".master klasöründe 10 adet modül dosyası oluşturuldu."
            *   "AI artık her işlem öncesi ilgili modülü kontrol edecek."
            *   "Bu yapı, projenin daha organize ve tutarlı gelişmesini sağlar."
        *   **Çıktı:** Modüler yapı kurulumunu `project_data.master_klasor_kuruldu = true` olarak kaydet. `workflow_status`'u `KESIF`'e güncelle.

    *   **Durum: `KESIF`**
        *   **Görev:** Kullanıcıya sitenin ne üzerine olacağını sor ve admin panel ihtiyacını değerlendir.
        *   **Admin Panel Değerlendirmesi:** Site konusuna göre admin panel gerekip gerekmediğini sor ve avantaj/dezavantajları açıkla:
            *   **Admin Panel Olursa:**
                *   ✅ İçerik kolayca güncellenebilir
                *   ✅ Teknik bilgi gerektirmez
                *   ✅ Çoklu kullanıcı desteği
                *   ✅ Dinamik içerik yönetimi
                *   ❌ Daha karmaşık hosting gereksinimi
                *   ❌ Güvenlik riskleri
                *   ❌ Daha fazla geliştirme süresi
            *   **Admin Panel Olmazsa:**
                *   ✅ Hızlı geliştirme
                *   ✅ Tüm hosting'lerde çalışır
                *   ✅ Güvenlik riski minimum
                *   ✅ Performans optimum
                *   ❌ İçerik güncellemesi için teknik bilgi gerekir
                *   ❌ Her değişiklik için kod düzenlemesi
        *   **Çıktı:** Site konusu ve admin panel kararını `project_status.json` içindeki `project_data.site_konusu` ve `project_data.admin_panel_gerekli`'ye kaydet. Admin panel seçilirse `workflow_status`'u `ADMIN_PANEL_PLANLAMA`'ya, seçilmezse `DIL_SECIMI`'ne güncelle.

    *   **Durum: `DIL_SECIMI`**
        *   **Görev:** Projenin ana dilini belirle ve çoklu dil desteği ihtiyacını değerlendir.
        *   **Ana Dil Seçimi:** Kullanıcıya projenin ana dilini sor:
            *   **Yerel Dil (Önerilen):** Hedef pazar için optimize
            *   **İngilizce:** Uluslararası pazar için
            *   **Fransızca:** Fransızca konuşan ülkeler için
            *   **Arapça:** Arap ülkeleri için (RTL desteği)
            *   **Almanca:** Almanca konuşan ülkeler için
        *   **Çoklu Dil Desteği Değerlendirmesi:** Kullanıcıya çoklu dil desteği gerekip gerekmediğini sor:
            *   **Çoklu Dil Desteği Olursa:**
                *   ✅ Uluslararası erişim
                *   ✅ Daha geniş kitle
                *   ✅ SEO avantajı (çoklu dil)
                *   ❌ Daha karmaşık geliştirme
                *   ❌ Çeviri maliyeti
                *   ❌ Daha fazla bakım
            *   **Tek Dil (Ana Dil):**
                *   ✅ Hızlı geliştirme
                *   ✅ Düşük maliyet
                *   ✅ Basit bakım
                *   ❌ Sınırlı erişim
                *   ❌ SEO sınırlaması
        *   **Dil Seçimi Rehberi:** Kullanıcıya dil seçimi konusunda yardım et:
        *   **Yerel Pazar Odaklı Proje:** Yerel dil + İngilizce (opsiyonel)
        *   **Uluslararası Proje:** İngilizce + hedef ülke dilleri
        *   **Bölgesel Proje:** Bölge dili + İngilizce
        *   **Kurumsal Proje:** Ana dil + müşteri dilleri
        *   **Dil Dosyası Yapısı (Component Tabanlı):** Tek dil seçilse bile, sonradan dil ekleme kolaylığı için component yapısında dil dosyası sistemi oluştur:
            *   **Dil Component Klasör Yapısı:**
                ```
                /components/language/
                ├── manager/          # Dil yönetim componentleri
                │   ├── language-manager.js
                │   ├── language-manager.css
                │   └── language-manager.php
                ├── files/           # Dil dosyaları
                │   ├── yerel_dil.json
                │   ├── en.json
                │   └── fr.json
                ├── ui/              # Dil değiştirici UI
                │   ├── language-selector.html
                │   ├── language-selector.css
                │   └── language-selector.js
                └── utils/           # Dil yardımcı fonksiyonları
                    ├── translation-helper.js
                    └── rtl-helper.css
                ```
            *   **Component Tabanlı Dil Yönetimi:** Her dil dosyası kendi component'i olarak organize edilir
            *   **Modüler Dil Sistemi:** Yeni diller kolayca component olarak eklenebilir
            *   **Gelecek Genişletme:** Sonradan yeni diller eklenebilecek şekilde yapılandır
        *   **Çıktı:** Seçilen ana dili ve çoklu dil kararını `project_data.ana_dil` ve `project_data.coklu_dil_destegi`'ne kaydet. `workflow_status`'u `DIL_DOSYA_HAZIRLAMA`'ya güncelle.

    *   **Durum: `DIL_PLANLAMA` (Sadece çoklu dil seçilirse)**
        *   **Görev:** Çoklu dil desteği için detaylı planlama yap ve kullanıcıya seçenekler sun.
        *   **Dil Listesi:** Kullanıcıya hangi dillerin destekleneceğini sor:
            *   **Temel Diller (Önerilen):**
                *   Yerel Dil (yerel_kod) - Ana dil
                *   İngilizce (en) - Uluslararası
            *   **Ek Diller (Opsiyonel):**
                *   Fransızca (fr) - Avrupa
                *   Almanca (de) - Avrupa
                *   Arapça (ar) - Orta Doğu (RTL)
                *   İspanyolca (es) - Latin Amerika
                *   Rusça (ru) - Doğu Avrupa
        *   **Dil Desteği Seviyesi:** Kullanıcıya dil desteği seviyesi seçenekleri sun:
            *   **Temel Desteği:**
                *   ✅ Statik içerik çevirisi
                *   ✅ Menü ve buton çevirisi
                *   ✅ Meta tag çevirisi
                *   **Maliyet:** +0 (sadece geliştirme süresi)
            *   **Gelişmiş Desteği:**
                *   ✅ Dinamik içerik çevirisi
                *   ✅ Admin panel çoklu dil
                *   ✅ Otomatik çeviri entegrasyonu
                *   **Maliyet:** +100-200/ay (çeviri API)
            *   **Profesyonel Desteği:**
                *   ✅ Profesyonel çeviri
                *   ✅ Kültürel uyarlama
                *   ✅ Yerel SEO optimizasyonu
                *   **Maliyet:** +500-1000/ay (çevirmen)
        *   **RTL Dil Desteği:** RTL diller (Arapça, Farsça, İbranice) seçilirse özel desteği açıkla:
            *   ✅ Sağdan sola okuma desteği
            *   ✅ RTL CSS stilleri
            *   ✅ Arapça font desteği
            *   ✅ Kültürel uyarlama
        *   **SEO Dil Optimizasyonu:** Dil bazlı SEO seçenekleri:
            *   **URL Tabanlı (Önerilen):** `/yerel/`, `/en/`, `/fr/`
            *   **Subdomain Tabanlı:** `yerel.site.com`, `en.site.com`
            *   **Hreflang Desteği:** Arama motoru dil etiketlemesi
        *   **Çıktı:** Seçilen dilleri, destek seviyesini ve SEO tercihini `project_data.dil_detaylari`'na kaydet. `workflow_status`'u `DIL_DOSYA_HAZIRLAMA`'ya güncelle.

    *   **Durum: `ADMIN_PANEL_PLANLAMA` (Sadece admin panel seçilirse)**
        *   **Görev:** Admin panel için detaylı planlama yap ve kullanıcıya seçenekler sun.
        *   **Teknoloji Seçimi:** Kullanıcıya admin panel teknolojisi seçeneklerini sun:
            *   **PHP + MySQL (Önerilen):**
                *   ✅ Tüm paylaşımlı hosting'lerde çalışır
                *   ✅ Hızlı geliştirme (2-3 hafta)
                *   ✅ Düşük maliyet
                *   ✅ WordPress benzeri deneyim
                *   **Öneri:** Küçük-orta projeler için ideal
            *   **Node.js + MySQL/MongoDB:**
                *   ✅ Yüksek performans
                *   ✅ Modern geliştirme deneyimi
                *   ✅ Real-time özellikler
                *   ❌ VPS/Cloud hosting gerekir (aylık +10-20)
                *   **Öneri:** Büyük projeler ve gelişmiş özellikler için
            *   **Python + Django:**
                *   ✅ Güçlü admin paneli (Django Admin)
                *   ✅ Güvenlik odaklı
                *   ✅ Büyük projeler için ideal
                *   ❌ VPS/Cloud hosting gerekir (aylık +10-20)
                *   **Öneri:** Kurumsal projeler için
        *   **Veritabanı Seçimi:** Seçilen teknolojiye göre veritabanı öner:
            *   **MySQL:** PHP ile birlikte önerilen, paylaşımlı hosting uyumlu
            *   **PostgreSQL:** Node.js/Python ile birlikte önerilen, gelişmiş özellikler
            *   **MongoDB:** Node.js ile birlikte önerilen, esnek veri yapısı
        *   **Admin Panel Özellikleri:** Kullanıcıya hangi özelliklerin gerekli olduğunu sor:
            *   **Temel Özellikler (Zorunlu):**
                *   İçerik yönetimi (CRUD)
                *   Kullanıcı girişi/çıkışı
                *   Medya yönetimi
                *   Site ayarları
            *   **Gelişmiş Özellikler (Opsiyonel):**
                *   Çoklu kullanıcı desteği
                *   Analitik ve raporlama
                *   Form yönetimi
                *   Menü yönetimi
                *   SEO ayarları
                *   Backup yönetimi
        *   **Güvenlik Seviyesi:** Kullanıcıya güvenlik seviyesi seçenekleri sun:
            *   **Temel Güvenlik:** Standart giriş, basit yetkilendirme
            *   **Orta Güvenlik:** 2FA, rate limiting, audit log
            *   **Yüksek Güvenlik:** Gelişmiş güvenlik protokolleri, şifreleme
        *   **Çıktı:** Seçilen teknoloji, veritabanı, özellikler ve güvenlik seviyesini `project_data.admin_panel_detaylari`'na kaydet. `workflow_status`'u `DIL_DOSYA_HAZIRLAMA`'ya güncelle.

    *   **Durum: `DIL_DOSYA_HAZIRLAMA`**
        *   **Görev:** Seçilen dil(ler) için component tabanlı dil dosyası yapısını oluştur ve dil yönetim sistemini hazırla.
        *   **Component Tabanlı Dil Sistemi Kurulumu:**
            *   **Dil Component Klasörü Oluşturma:** `/components/language/` klasör yapısını oluştur
            *   **Dil Dosyaları Oluşturma:** Seçilen diller için JSON component dosyaları oluştur
            *   **LanguageManager Component'i:** Dil yönetimi için ana component'i oluştur
            *   **Dil Değiştirici UI:** Kullanıcı dostu dil seçim arayüzü component'i oluştur
            *   **RTL Desteği:** RTL diller için özel CSS component'leri hazırla
            *   **Dil Validator:** Dil dosyalarının doğruluğunu kontrol eden component oluştur
        *   **Tek Dil Projeleri İçin Özel Hazırlık:**
            *   **Gelecek Genişletme Hazırlığı:** Sonradan dil eklenebilecek şekilde yapılandır
            *   **Component Yapısı:** Tek dil bile olsa component yapısında organize et
            *   **Dil Manager Hazırlığı:** LanguageManager'ı tek dil için optimize et
        *   **Çoklu Dil Projeleri İçin:**
            *   **Tüm Dil Dosyaları:** Seçilen tüm diller için JSON component'leri oluştur
            *   **Dil Değiştirme Sistemi:** URL routing ve cookie yönetimi hazırla
            *   **SEO Dil Optimizasyonu:** Hreflang ve sitemap component'leri oluştur
        *   **Çıktı:** Dil dosyası yapısını `project_data.dil_dosya_yapisi`'na kaydet. `workflow_status`'u `TASARIM_TEMELLERI`'ne güncelle.

    *   **Durum: `TASARIM_TEMELLERI`**
        *   **Görev:** Sitenin konusuna uygun 10 renk paleti öner.
        *   **Çıktı:** Kullanıcının seçimini `project_data.secilen_renk_paleti`'ne kaydet. `workflow_status`'u `YAPI_PLANLAMA`'ya güncelle.

    *   **Durum: `YAPI_PLANLAMA`**
        *   **Görev:** Gerekli sayfaları listele ve kullanıcıdan onay al.
        *   **Çıktı:** Nihai sayfa listesini `project_data.sayfalar`'a kaydet. `workflow_status`'u `BOLUM_PLANLAMA`'ya güncelle.

    *   **Durum: `BOLUM_PLANLAMA`**
        *   **Görev:** Geliştirilecek bir sonraki sayfanın bölümlerini kullanıcıyla netleştir.
        *   **Çıktı:** Bölüm listesini ilgili sayfanın altına kaydet. `workflow_status`'u `KODLAMA`'ya güncelle.

    *   **Durum: `KODLAMA`**
        *   **Görev:** Kullanıcının seçtiği tek bir bölümü kodla.
        *   **Otomatik Kaydetme Kuralları:**
            *   **Kod Yazma Başlangıcı:** Her kod yazmaya başladığında checkpoint oluştur
            *   **Ara Kaydetme:** Her 10-15 satır kod yazdıktan sonra ara checkpoint oluştur
            *   **Kod Bloğu Tamamlama:** Her fonksiyon, class veya büyük kod bloğu tamamlandığında checkpoint güncelle
            *   **Hata Durumu:** Kod yazarken hata oluşursa mevcut durumu kaydet
            *   **Kullanıcı Bekleme:** Kullanıcıdan yanıt beklerken checkpoint oluştur
        *   **Checkpoint İçeriği:**
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
        *   **Devam Etme Senaryoları:**
            *   **Kod Yazma Yarıda Kaldı:** Kaldığı yerden devam et, son kod bloğunu göster
            *   **Test Yarıda Kaldı:** Test edilen kısımları göster, kalan testleri listele
            *   **Review Yarıda Kaldı:** Review edilen kısımları göster, kalan incelemeleri listele
        *   **Çıktı:** Kodu sun ve geri bildirim al.
        *   **Döngü:**
            *   **Beğenirse:** Bölümü "tamamlandı" olarak işaretle. Checkpoint'i temizle. Sayfada kodlanacak bölüm kalmadıysa `BOLUM_PLANLAMA`'ya dön, aksi halde aynı sayfada kal.
            *   **Beğenmezse:** Ayar seçenekleri sun ve bölümü güncelle. Checkpoint'i güncelle. `KODLAMA` durumunda kal.

    *   **Durum: `REVIEW`**
        *   **Görev:** Tamamlanan bölümlerin kod kalitesini ve standartlara uygunluğunu kontrol et.
        *   **Çıktı:** Kod review raporu hazırla ve gerekli düzeltmeleri belirle.
        *   **Döngü:**
            *   **Sorun Varsa:** `KODLAMA` durumuna geri dön ve düzeltmeleri yap.
            *   **Sorun Yoksa:** `TEST` durumuna geç.

    *   **Durum: `TEST`**
        *   **Görev:** Geliştirilen bölümlerin fonksiyonellik, performans ve uyumluluk testlerini yap.
        *   **Test Dosyası Oluşturma Protokolü:**
            *   **Kullanıcı Onayı Zorunluluğu:** Test dosyası oluşturmadan önce kullanıcıya sor:
                *   "Projenizi sunucuya yüklediniz mi? (Evet/Hayır)"
                *   **Evet ise:** "Test işlemini siz yapmanız gerekiyor. Test checklist'ini size sunuyorum:"
                    *   ✅ Tüm sayfalar doğru yükleniyor mu?
                    *   ✅ Formlar çalışıyor mu?
                    *   ✅ Responsive tasarım tüm cihazlarda uygun mu?
                    *   ✅ Tüm linkler çalışıyor mu?
                    *   ✅ Admin panel (varsa) giriş yapılabiliyor mu?
                    *   ✅ Veritabanı bağlantısı çalışıyor mu?
                    *   ✅ Dosya yükleme işlemleri çalışıyor mu?
                *   **Hayır ise:** "Test dosyası oluşturuyorum. Test sonuçlarını size raporlayacağım."
        *   **Test Türleri:**
            *   **Fonksiyonellik Testleri:**
                *   Form gönderimi ve validasyon
                *   Veritabanı CRUD işlemleri
                *   Dosya yükleme ve indirme
                *   Kullanıcı giriş/çıkış (admin panel varsa)
                *   AJAX istekleri ve API çağrıları
            *   **Performans Testleri:**
                *   Sayfa yükleme hızları (LCP, FID, CLS)
                *   Görsel optimizasyonu kontrolü
                *   CSS/JS minifikasyonu kontrolü
                *   Veritabanı sorgu optimizasyonu
            *   **Uyumluluk Testleri:**
                *   Cross-browser uyumluluk (Chrome, Firefox, Safari, Edge)
                *   Responsive tasarım (mobil, tablet, desktop)
                *   Erişilebilirlik standartları (WCAG 2.1)
                *   SEO optimizasyonu kontrolü
        *   **Test Raporu Formatı:** Fonksiyonellik, performans ve uyumluluk testleri ile hata listesi
        *   **Çıktı:** Test sonuçlarını raporla ve hataları belirle.
        *   **Döngü:**
            *   **Test Başarısız:** `KODLAMA` durumuna geri dön ve hataları düzelt.
            *   **Test Başarılı:** Tüm sayfalar tamamlandıysa `DEPLOY` durumuna geç, aksi halde `BOLUM_PLANLAMA`'ya dön.

    *   **Durum: `DEPLOY`**
        *   **Görev:** Projeyi yayınlama için hazırla ve deployment sürecini yönet.
        *   **Çıktı:** Deployment checklist'i tamamla ve projeyi yayınla.
        *   **Döngü:**
            *   **Deployment Başarısız:** Hataları düzelt ve tekrar dene.
            *   **Deployment Başarılı:** `MAINTENANCE` durumuna geç.

    *   **Durum: `ADMIN_PANEL_TASARIM` (Sadece admin panel seçilirse)**
        *   **Görev:** Admin panel arayüz tasarımını planla ve kullanıcıya seçenekler sun.
        *   **Admin Panel Tasarım Stili:** Kullanıcıya admin panel tasarım seçenekleri sun:
            *   **Minimalist (Önerilen):**
                *   ✅ Temiz ve sade arayüz
                *   ✅ Hızlı yükleme
                *   ✅ Kolay navigasyon
                *   **Öneri:** Küçük-orta projeler için ideal
            *   **Modern Dashboard:**
                *   ✅ Grafik ve istatistikler
                *   ✅ Widget tabanlı arayüz
                *   ✅ Gelişmiş görselleştirme
                *   **Öneri:** Büyük projeler için
            *   **Kurumsal:**
                *   ✅ Profesyonel görünüm
                *   ✅ Güvenlik odaklı tasarım
                *   ✅ Detaylı raporlama
                *   **Öneri:** Kurumsal projeler için
        *   **Renk Paleti:** Admin panel için özel renk seçenekleri:
            *   **Koyu Tema:** Göz yormayan, gece kullanımı için ideal
            *   **Açık Tema:** Klasik, gündüz kullanımı için ideal
            *   **Otomatik:** Sistem temasına göre değişen
        *   **Layout Seçimi:** Admin panel düzeni seçenekleri:
            *   **Sidebar Navigation:** Sol menü, sağ içerik alanı
            *   **Top Navigation:** Üst menü, alt içerik alanı
            *   **Dashboard Style:** Widget tabanlı ana sayfa
        *   **Çıktı:** Seçilen tasarım stilini `project_data.admin_panel_tasarim`'a kaydet. `workflow_status`'u `YAPI_PLANLAMA`'ya güncelle.

    *   **Durum: `DIL_KODLAMA` (Sadece çoklu dil seçilirse)**
        *   **Görev:** Çoklu dil desteği için frontend ve backend kodlamasını yap.
        *   **Frontend Dil Desteği:**
            *   **Dil Dosyası Oluşturma:** Seçilen diller için JSON dosyaları
            *   **JavaScript Dil Yöneticisi:** LanguageManager sınıfı implementasyonu
            *   **HTML Dil Desteği:** data-translate attribute'ları
            *   **RTL Desteği:** RTL diller için CSS ve HTML düzenlemeleri
            *   **Dil Değiştirici:** Kullanıcı dostu dil seçim arayüzü
        *   **Backend Dil Desteği:**
            *   **Veritabanı Yapısı:** languages, translations, content tabloları
            *   **PHP Dil Yöneticisi:** LanguageManager sınıfı implementasyonu
            *   **URL Yönlendirme:** Dil bazlı URL routing
            *   **Cookie Yönetimi:** Dil tercihi cookie sistemi
        *   **SEO Dil Optimizasyonu:**
            *   **Hreflang Etiketleri:** Tüm sayfalar için hreflang implementasyonu
            *   **Dil Bazlı Sitemap:** Her dil için ayrı sitemap
            *   **Meta Tag Yönetimi:** Dil bazlı meta tag sistemi
            *   **Canonical URL'ler:** Dil bazlı canonical URL yapısı
        *   **Admin Panel Dil Yönetimi (Eğer admin panel varsa):**
            *   **Çeviri Editörü:** WYSIWYG çeviri editörü
            *   **Dil Durumu Takibi:** Hangi içeriklerin çevrildiği
            *   **Toplu Çeviri:** Birden fazla içeriği aynı anda çevirme
            *   **Otomatik Çeviri:** API entegrasyonu (opsiyonel)
        *   **Çıktı:** Çoklu dil kodunu sun ve geri bildirim al. `workflow_status`'u `DIL_TEST`'e güncelle.

    *   **Durum: `DIL_TEST` (Sadece çoklu dil seçilirse)**
        *   **Görev:** Çoklu dil desteğinin fonksiyonellik ve SEO testlerini yap.
        *   **Dil Değiştirme Testleri:**
            *   **URL Yönlendirme:** Dil değiştirme URL'lerinin doğru çalışması
            *   **Cookie Yönetimi:** Dil tercihinin hatırlanması
            *   **Otomatik Algılama:** Browser dilinin doğru algılanması
        *   **Çeviri Testleri:**
            *   **Statik İçerik:** Tüm statik metinlerin çevrilmesi
            *   **Dinamik İçerik:** Admin panelden gelen içeriklerin çevrilmesi
            *   **Meta Taglar:** Title, description, keywords çevirileri
        *   **RTL Testleri (Eğer RTL dil varsa):**
            *   **CSS RTL Desteği:** Sağdan sola okuma düzeni
            *   **Font Desteği:** Arapça/Hebrew fontların yüklenmesi
            *   **Layout Kontrolü:** RTL düzenin doğru görüntülenmesi
        *   **SEO Testleri:**
            *   **Hreflang Kontrolü:** Tüm hreflang etiketlerinin doğruluğu
            *   **Sitemap Kontrolü:** Dil bazlı sitemap'lerin oluşturulması
            *   **Canonical URL'ler:** Her dil için doğru canonical URL
        *   **Çıktı:** Test sonuçlarını raporla ve hataları belirle. `workflow_status`'u `ADMIN_PANEL_KODLAMA`'ya veya `KODLAMA`'ya güncelle.

    *   **Durum: `ADMIN_PANEL_KODLAMA` (Sadece admin panel seçilirse)**
        *   **Görev:** Admin panel backend ve frontend kodlamasını yap.
        *   **Backend Geliştirme:** Seçilen teknolojiye göre:
            *   **PHP + MySQL:** PDO ile veritabanı bağlantısı, MVC yapısı
            *   **Node.js:** Express.js framework, RESTful API
            *   **Python:** Django framework, Django Admin entegrasyonu
        *   **Frontend Geliştirme:** Admin panel arayüzü:
            *   **Responsive Design:** Mobil uyumlu admin panel
            *   **Interactive Elements:** AJAX formlar, real-time güncellemeler
            *   **Data Tables:** Sayfalama, sıralama, filtreleme
            *   **File Upload:** Drag & drop medya yükleme
        *   **Güvenlik Implementasyonu:** Seçilen güvenlik seviyesine göre:
            *   **Temel:** Basit giriş/çıkış, session yönetimi
            *   **Orta:** 2FA, rate limiting, input validation
            *   **Yüksek:** Gelişmiş şifreleme, audit logging, RBAC
        *   **Çoklu Dil Desteği (Eğer seçilmişse):**
            *   **Admin Panel Çevirileri:** Admin panel arayüzünün çevrilmesi
            *   **Çeviri Yönetimi:** İçerik çeviri yönetim sistemi
            *   **Dil Durumu:** Hangi dillerin aktif olduğu yönetimi
        *   **Çıktı:** Admin panel kodunu sun ve geri bildirim al. `workflow_status`'u `ADMIN_PANEL_TEST`'e güncelle.

    *   **Durum: `ADMIN_PANEL_TEST` (Sadece admin panel seçilirse)**
        *   **Görev:** Admin panel fonksiyonellik ve güvenlik testlerini yap.
        *   **Fonksiyonellik Testleri:**
            *   **CRUD Operasyonları:** Tüm veri işlemlerinin test edilmesi
            *   **Form Validasyonu:** Tüm formların doğru çalışması
            *   **File Upload:** Medya yükleme ve yönetimi testleri
            *   **User Management:** Kullanıcı kayıt/giriş/çıkış testleri
        *   **Güvenlik Testleri:**
            *   **Authentication:** Giriş/çıkış güvenliği
            *   **Authorization:** Yetki kontrolü testleri
            *   **Input Validation:** XSS ve SQL injection testleri
            *   **File Upload Security:** Zararlı dosya yükleme testleri
        *   **Performance Testleri:**
            *   **Database Queries:** Sorgu optimizasyonu
            *   **Page Load Times:** Sayfa yükleme hızları
            *   **Concurrent Users:** Eşzamanlı kullanıcı testleri
        *   **Çıktı:** Test sonuçlarını raporla ve hataları belirle. `workflow_status`'u `ADMIN_PANEL_DEPLOY`'a güncelle.

    *   **Durum: `ADMIN_PANEL_DEPLOY` (Sadece admin panel seçilirse)**
        *   **Görev:** Admin paneli yayınlama için hazırla ve deployment sürecini yönet.
        *   **Database Setup:** Veritabanı kurulumu ve migration'lar:
            *   **MySQL:** Tablo oluşturma, index'ler, foreign key'ler
            *   **PostgreSQL:** Schema oluşturma, trigger'lar, function'lar
            *   **MongoDB:** Collection'lar, index'ler, aggregation pipeline'lar
        *   **Admin User Creation:** İlk admin kullanıcısının oluşturulması
        *   **Security Configuration:** SSL sertifikası, güvenlik ayarları
        *   **Backup Strategy:** Otomatik backup sistemi kurulumu
        *   **Monitoring Setup:** Hata takibi ve performans monitoring
        *   **Çıktı:** Admin panel deployment'ını tamamla. `workflow_status`'u `MAINTENANCE`'a güncelle.

    *   **Durum: `MAINTENANCE`**
        *   **Görev:** Proje bakım ve güncelleme süreçlerini yönet.
        *   **Admin Panel Bakımı (Eğer varsa):**
            *   **Güvenlik Güncellemeleri:** Düzenli güvenlik yamaları
            *   **Performance Monitoring:** Admin panel performans takibi
            *   **User Feedback:** Kullanıcı geri bildirim sistemi
            *   **Backup Management:** Otomatik backup yönetimi
            *   **Log Analysis:** Güvenlik ve hata log analizi
        *   **Çıktı:** Bakım planı oluştur ve gerekli güncellemeleri yap.
        *   **Döngü:** Sürekli bakım döngüsü, gerektiğinde diğer durumlara geçiş.

---

### **Bölüm 5: Admin Panel Özel Kuralları ve Rehberi**

Bu bölüm, admin panel geliştirme sürecinde uyulması gereken özel kuralları ve kullanıcıya sunulacak seçenekleri detaylandırır.

1.  **Admin Panel Teknoloji Seçimi Rehberi:**
    *   **Kullanıcıya Sorulacak Sorular:**
        *   "Projenizin büyüklüğü nedir? (Küçük/Orta/Büyük)"
        *   "Hosting bütçeniz nedir? (Paylaşımlı/VPS/Cloud)"
        *   "Teknik bilginiz var mı? (Yok/Az/Orta/İleri)"
        *   "Hangi özellikler gerekli? (Temel/Gelişmiş/Kurumsal)"
    *   **Seçim Önerileri:**
        *   **Küçük Proje + Paylaşımlı Hosting + Az Teknik Bilgi = PHP + MySQL**
        *   **Orta Proje + VPS + Orta Teknik Bilgi = Node.js + MySQL**
        *   **Büyük Proje + Cloud + İleri Teknik Bilgi = Python + Django + PostgreSQL**

2.  **Admin Panel Özellik Seçimi Rehberi:**
    *   **Temel Özellikler (Tüm projeler için):**
        *   İçerik yönetimi (CRUD)
        *   Kullanıcı girişi/çıkışı
        *   Medya yönetimi
        *   Site ayarları
    *   **Gelişmiş Özellikler (Orta projeler için):**
        *   Çoklu kullanıcı desteği
        *   Form yönetimi
        *   Menü yönetimi
        *   SEO ayarları
    *   **Kurumsal Özellikler (Büyük projeler için):**
        *   Analitik ve raporlama
        *   Backup yönetimi
        *   Audit logging
        *   API yönetimi

3.  **Admin Panel Güvenlik Seviyesi Rehberi:**
    *   **Temel Güvenlik (Küçük projeler):**
        *   Standart giriş/çıkış
        *   Basit yetkilendirme
        *   Input validation
        *   **Maliyet:** +0
    *   **Orta Güvenlik (Orta projeler):**
        *   2FA (Google Authenticator)
        *   Rate limiting
        *   Audit logging
        *   **Maliyet:** +50-100/ay
    *   **Yüksek Güvenlik (Büyük projeler):**
        *   Gelişmiş şifreleme
        *   RBAC (Role-Based Access Control)
        *   Güvenlik monitoring
        *   **Maliyet:** +200-500/ay

4.  **Admin Panel Tasarım Seçimi Rehberi:**
    *   **Minimalist (Önerilen):**
        *   Temiz ve sade arayüz
        *   Hızlı yükleme
        *   Kolay navigasyon
        *   **Uygun:** Küçük-orta projeler
    *   **Modern Dashboard:**
        *   Grafik ve istatistikler
        *   Widget tabanlı arayüz
        *   Gelişmiş görselleştirme
        *   **Uygun:** Büyük projeler
    *   **Kurumsal:**
        *   Profesyonel görünüm
        *   Güvenlik odaklı tasarım
        *   Detaylı raporlama
        *   **Uygun:** Kurumsal projeler

---

### **Bölüm 6: Admin Panel Deployment ve Bakım Protokolleri**

Bu bölüm, admin panel deployment ve bakım süreçlerini detaylandırır.

1.  **Admin Panel Deployment Checklist:**
    *   **Ön Deployment:**
        *   ✅ Veritabanı yapısı oluşturuldu
        *   ✅ Güvenlik ayarları yapılandırıldı
        *   ✅ SSL sertifikası kuruldu
        *   ✅ Backup stratejisi belirlendi
    *   **Deployment Sırasında:**
        *   ✅ Dosyalar sunucuya yüklendi
        *   ✅ Veritabanı bağlantısı test edildi
        *   ✅ İlk admin kullanıcısı oluşturuldu
        *   ✅ Güvenlik testleri yapıldı
    *   **Post Deployment:**
        *   ✅ Monitoring sistemi kuruldu
        *   ✅ Backup sistemi test edildi
        *   ✅ Performance testleri yapıldı
        *   ✅ Kullanıcı eğitimi verildi

2.  **Admin Panel Bakım Protokolleri:**
    *   **Günlük Bakım:**
        *   Log dosyalarını kontrol et
        *   Backup durumunu kontrol et
        *   Performance metriklerini izle
    *   **Haftalık Bakım:**
        *   Güvenlik güncellemelerini kontrol et
        *   Veritabanı optimizasyonu yap
        *   Kullanıcı aktivitelerini analiz et
    *   **Aylık Bakım:**
        *   Tam sistem backup'ı al
        *   Güvenlik audit'i yap
        *   Performance raporu hazırla

3.  **Admin Panel Sorun Giderme Rehberi:**
    *   **Giriş Sorunları:**
        *   Kullanıcı adı/şifre kontrolü
        *   Session timeout kontrolü
        *   Veritabanı bağlantı kontrolü
    *   **Performans Sorunları:**
        *   Veritabanı sorgu optimizasyonu
        *   Cache ayarları kontrolü
        *   Sunucu kaynak kullanımı kontrolü
    *   **Güvenlik Sorunları:**
        *   Log dosyalarını analiz et
        *   Şüpheli aktiviteleri tespit et
        *   Güvenlik güncellemelerini uygula

---

### **Bölüm 7: Admin Panel Kullanıcı Eğitimi ve Dokümantasyon**

Bu bölüm, admin panel kullanıcıları için eğitim ve dokümantasyon süreçlerini tanımlar.

1.  **Admin Panel Kullanıcı Eğitimi:**
    *   **Temel Eğitim (Tüm kullanıcılar):**
        *   Giriş/çıkış işlemleri
        *   Temel içerik yönetimi
        *   Medya yükleme
        *   Site ayarları
    *   **Gelişmiş Eğitim (Admin/Editor kullanıcılar):**
        *   Kullanıcı yönetimi
        *   Form yönetimi
        *   Menü yönetimi
        *   SEO ayarları
    *   **Uzman Eğitim (Sadece Admin kullanıcılar):**
        *   Sistem ayarları
        *   Backup yönetimi
        *   Güvenlik ayarları
        *   Performans monitoring

2.  **Admin Panel Dokümantasyon:**
    *   **Kullanıcı Kılavuzu:** Adım adım kullanım talimatları
    *   **Video Eğitimler:** Ekran kaydı ile görsel eğitimler
    *   **FAQ:** Sık sorulan sorular ve cevapları
    *   **Teknik Dokümantasyon:** Geliştiriciler için teknik detaylar

---

### **Bölüm 8: Geçici Dosya Yönetimi ve Test Klasör Yapısı**

Bu bölüm, proje geliştirme sürecinde oluşturulan geçici dosyaların ve test dosyalarının nasıl yönetileceğini tanımlar.

1. **Geçici Dosya İşaretleme Sistemi:**
    *   **SİLİNECEK İbaresi:** Sonradan kaldırılması muhtemel tüm dosyaların başına `[SİLİNECEK]` ibaresi eklenmelidir.
    *   **Dosya İsimlendirme Kuralı:** Geçici dosyalar `temp_`, `test_`, `debug_`, `backup_` gibi ön eklerle başlamalıdır.
    *   **Otomatik Temizlik:** Proje tamamlandığında `[SİLİNECEK]` ibareli dosyalar otomatik olarak temizlenmelidir.

2. **Test Klasör Yapısı:**
    ```
    /temp-files/
    ├── tests/          # Test dosyaları
    ├── debug/          # Debug dosyaları
    ├── backups/        # Yedek dosyalar
    └── documentation/  # Geçici dokümantasyon
    ```

3. **Geçici Dosya Türleri ve İşaretleme:**
    *   **Test Dosyaları:**
        *   `[SİLİNECEK] test_*.php` - Test scriptleri
        *   `[SİLİNECEK] debug_*.js` - Debug JavaScript dosyaları
        *   `[SİLİNECEK] temp_*.html` - Geçici HTML dosyaları
    *   **Backup Dosyaları:**
        *   `[SİLİNECEK] *.backup` - Yedek dosyalar
        *   `[SİLİNECEK] *.bak` - Alternatif yedek uzantısı
        *   `[SİLİNECEK] *_old.*` - Eski versiyon dosyalar
    *   **Log Dosyaları:**
        *   `[SİLİNECEK] error.log` - Hata logları
        *   `[SİLİNECEK] debug.log` - Debug logları
        *   `[SİLİNECEK] access.log` - Erişim logları
    *   **Cache Dosyaları:**
        *   `[SİLİNECEK] cache_*.xml` - Cache dosyaları
        *   `[SİLİNECEK] temp_*.json` - Geçici JSON dosyaları

4. **Test Klasörü İçerik Yönetimi:**
    *   **Test Dosyası Oluşturma Kuralları:**
        *   Tüm test dosyaları `/temp-files/tests/` klasöründe oluşturulmalıdır
        *   Test dosyaları `[SİLİNECEK]` ibaresi ile işaretlenmelidir
        *   Test dosyaları açıklayıcı isimlerle adlandırılmalıdır
    *   **Test Kategorileri:**
        *   **Unit Tests:** `unit-tests/test_*.php`
        *   **Integration Tests:** `integration-tests/test_*.php`
        *   **Performance Tests:** `performance-tests/test_*.php`
        *   **Browser Tests:** `browser-tests/test_*.html`

5. **Geçici Dosya Temizlik Protokolü:**
    *   **Otomatik Temizlik Kuralları:**
        *   Her proje tamamlandığında `[SİLİNECEK]` ibareli dosyalar silinir
        *   `/temp-files/` klasörü tamamen temizlenir
        *   Backup dosyaları ayrı bir yere taşınır
    *   **Manuel Temizlik:**
        *   Geliştirici isterse manuel olarak temizlik yapabilir
        *   Temizlik öncesi kullanıcıya onay sorulur
        *   Silinecek dosyaların listesi gösterilir

6. **Test Dosyası İçerik Standartları:**
    *   **Test Dosyası Başlığı:**
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
    *   **Test Sonuç Raporlama:**
        ```php
        // Test sonuçları buraya yazılır
        echo "Test Başarılı: " . ($test_result ? "EVET" : "HAYIR") . "\n";
        echo "Test Süresi: " . $execution_time . " saniye\n";
        echo "Hata Sayısı: " . $error_count . "\n";
        ```

7. **Debug Klasörü Yönetimi:**
    *   **Debug Dosyası Oluşturma:**
        *   Debug dosyaları `/temp-files/debug/` klasöründe oluşturulur
        *   Debug dosyaları `[SİLİNECEK] debug_*.log` formatında adlandırılır
        *   Debug dosyaları otomatik olarak temizlenir
    *   **Log Dosyası Rotasyonu:**
        *   Log dosyaları belirli boyuta ulaştığında yeni dosya oluşturulur
        *   Eski log dosyaları otomatik olarak arşivlenir
        *   Log dosyaları 30 gün sonra silinir

8. **Backup Klasörü Yönetimi:**
    *   **Backup Dosyası Oluşturma:**
        *   Backup dosyaları `/temp-files/backups/` klasöründe oluşturulur
        *   Backup dosyaları `[SİLİNECEK] backup_*.sql` formatında adlandırılır
        *   Backup dosyaları proje tamamlandığında silinir
    *   **Backup Dosyası Saklama:**
        *   Kritik backup'lar ayrı bir yere taşınır
        *   Gereksiz backup'lar otomatik silinir
        *   Backup dosyaları sıkıştırılır

9. **Geçici Dokümantasyon Yönetimi:**
    *   **Dokümantasyon Dosyaları:**
        *   Geçici dokümantasyon `/temp-files/documentation/` klasöründe saklanır
        *   Dokümantasyon dosyaları `[SİLİNECEK] doc_*.md` formatında adlandırılır
        *   Dokümantasyon dosyaları proje tamamlandığında silinir
    *   **Dokümantasyon İçerik Standartları:**
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

10. **Geçici Dosya Güvenlik Kuralları:**
    *   **Hassas Veri Koruması:**
        *   Geçici dosyalarda hassas veri saklanmamalıdır
        *   Test veritabanları ayrı olmalıdır
        *   Debug dosyalarında şifreler loglanmamalıdır
    *   **Dosya İzinleri:**
        *   Geçici dosyalar sadece geliştirici tarafından okunabilir olmalıdır
        *   Geçici dosyalar web sunucusundan erişilemez olmalıdır
        *   Geçici dosyalar .gitignore'a eklenmelidir

11. **Otomatik Temizlik Scripti:**
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

12. **Geçici Dosya İzleme Sistemi:**
    *   **Dosya Oluşturma Takibi:**
        *   Her geçici dosya oluşturulduğunda log tutulur
        *   Dosya oluşturma tarihi ve amacı kaydedilir
        *   Dosya boyutu ve türü takip edilir
    *   **Temizlik Raporu:**
        *   Temizlik işlemi sonrası rapor oluşturulur
        *   Silinen dosya sayısı ve boyutu raporlanır
        *   Temizlik işlemi loglanır

---

### **Bölüm 9: Proje Durumu ve Checkpoint Yönetimi**

Bu bölüm, proje geliştirme sürecinde durum takibi ve checkpoint yönetimini detaylandırır.

1. **Project Status JSON Yapısı:** project_info, workflow_status, current_task, progress_checkpoint, project_data, prompt_history, temp_files

2. **Checkpoint Oluşturma Kuralları:**
    *   **Otomatik Checkpoint Tetikleyicileri:**
        *   Her 5 dakikada bir otomatik checkpoint
        *   Her kod bloğu tamamlandığında
        *   Her kullanıcı onayından sonra
        *   Her hata durumunda
        *   Her dosya kaydedildiğinde
    *   **Manuel Checkpoint Tetikleyicileri:**
        *   Kullanıcı "kaydet" dediğinde
        *   Önemli bir aşama tamamlandığında
        *   Kritik bir değişiklik yapıldığında

3. **Checkpoint İçerik Standartları:**
    *   **Zorunlu Alanlar:**
        *   `current_file`: Şu anda çalışılan dosya
        *   `progress_percentage`: İlerleme yüzdesi
        *   `completed_parts`: Tamamlanan kısımlar
        *   `remaining_parts`: Kalan kısımlar
        *   `last_code_snippet`: Son yazılan kod
        *   `next_steps`: Sonraki adımlar
    *   **Opsiyonel Alanlar:**
        *   `estimated_remaining_time`: Tahmini kalan süre
        *   `notes`: Geliştirici notları
        *   `errors`: Tespit edilen hatalar
        *   `warnings`: Uyarılar

4. **Checkpoint Kurtarma Protokolü:**
    *   **Otomatik Kurtarma:**
        *   Yeni oturum başladığında checkpoint kontrol edilir
        *   Checkpoint varsa kullanıcıya sorulur
        *   Kullanıcı onaylarsa checkpoint'ten devam edilir
    *   **Manuel Kurtarma:**
        *   Kullanıcı isterse manuel olarak checkpoint yüklenebilir
        *   Checkpoint geçmişi görüntülenebilir
        *   Eski checkpoint'ler geri yüklenebilir

5. **Proje Durumu Güncelleme Kuralları:**
    *   **Workflow Status Güncellemeleri:**
        *   Her aşama tamamlandığında güncellenir
        *   Durum değişikliği loglanır
        *   Geçiş tarihi kaydedilir
    *   **Current Task Güncellemeleri:**
        *   Her görev başladığında güncellenir
        *   Görev tamamlandığında temizlenir
        *   Görev değişikliği loglanır

6. **Geçici Dosya Takibi:**
    *   **Dosya Oluşturma:**
        *   Her geçici dosya oluşturulduğunda `temp_files` dizisine eklenir
        *   Dosya yolu, oluşturma tarihi ve amacı kaydedilir
        *   Dosya durumu takip edilir
    *   **Dosya Silme:**
        *   Geçici dosya silindiğinde listeden çıkarılır
        *   Silme tarihi loglanır
        *   Silme nedeni kaydedilir

7. **Hata Yönetimi ve Logging:**
    *   **Hata Yakalama:**
        *   Tüm hatalar yakalanır ve loglanır
        *   Hata türü ve mesajı kaydedilir
        *   Hata oluştuğu dosya ve satır bilgisi saklanır
    *   **Hata Raporlama:**
        *   Kritik hatalar anında raporlanır
        *   Hata istatistikleri tutulur
        *   Hata çözüm önerileri sunulur

8. **Performans İzleme:**
    *   **Zaman Takibi:**
        *   Her görev için süre ölçülür
        *   Toplam proje süresi hesaplanır
        *   Tahmini kalan süre güncellenir
    *   **Kaynak Kullanımı:**
        *   Dosya boyutları takip edilir
        *   Bellek kullanımı izlenir
        *   CPU kullanımı ölçülür

---

### **Bölüm 10: Güvenli Özellik Ekleme ve Mevcut Sistem Koruması**

Bu bölüm, yeni özellikler eklerken mevcut sisteme zarar vermemek için uyulması gereken kritik kuralları tanımlar.

1. **Özellik Ekleme Öncesi Kontrol Listesi:**
    *   **Mevcut Sistem Analizi:**
        *   ✅ Mevcut kod yapısını detaylı analiz et
        *   ✅ Bağımlılıkları tespit et
        *   ✅ Kritik fonksiyonları belirle
        *   ✅ Test edilmiş kod bloklarını işaretle
    *   **Etki Analizi:**
        *   ✅ Yeni özelliğin hangi dosyaları etkileyeceğini belirle
        *   ✅ Mevcut fonksiyonlara etkisini değerlendir
        *   ✅ Veritabanı değişikliklerini planla
        *   ✅ API endpoint'lerini kontrol et

2. **Güvenli Kod Değişikliği Protokolü:**
    *   **Backup Oluşturma (Zorunlu):**
        *   Değişiklik öncesi tam sistem backup'ı al
        *   Kritik dosyaları ayrı yedekle
        *   Veritabanı snapshot'ı oluştur
        *   Backup'ları `/temp-files/backups/` klasöründe sakla
    *   **Test Ortamı Hazırlama:**
        *   Yeni özelliği test ortamında dene
        *   Mevcut fonksiyonları test et
        *   Edge case'leri kontrol et
        *   Performance impact'i ölç

3. **Kod Değişikliği Kuralları:**
    *   **Mevcut Kodu Koruma:**
        *   ✅ Mevcut fonksiyonları değiştirme, yeni fonksiyon oluştur
        *   ✅ Kritik kod bloklarına dokunma
        *   ✅ Test edilmiş kodları bozma
        *   ✅ Sadece gerekli yerleri değiştir
    *   **Geriye Uyumluluk:**
        *   ✅ Eski API'leri desteklemeye devam et
        *   ✅ Mevcut veri yapılarını koru
        *   ✅ Eski parametreleri kabul et
        *   ✅ Deprecated uyarıları ekle

4. **Veritabanı Değişikliği Güvenliği:**
    *   **Migration Stratejisi:**
        *   ✅ Mevcut veriyi koruyan migration'lar yaz
        *   ✅ Rollback planı hazırla
        *   ✅ Veri kaybını önleyici kontroller ekle
        *   ✅ Test veritabanında dene
    *   **Tablo Değişiklikleri:**
        *   ✅ Yeni kolonlar NULL olarak ekle
        *   ✅ Mevcut veriyi etkilemeyen değişiklikler yap
        *   ✅ Index'leri dikkatli ekle
        *   ✅ Foreign key'leri güvenli şekilde ekle

5. **API ve Endpoint Güvenliği:**
    *   **Mevcut Endpoint'leri Koruma:**
        *   ✅ Eski endpoint'leri değiştirme
        *   ✅ Yeni versiyonlar oluştur (v2, v3)
        *   ✅ Backward compatibility sağla
        *   ✅ Deprecation notice ekle
    *   **Yeni Endpoint Oluşturma:**
        *   ✅ RESTful standartlara uy
        *   ✅ Güvenlik kontrollerini ekle
        *   ✅ Rate limiting uygula
        *   ✅ Input validation yap

6. **Frontend Değişiklik Güvenliği:**
    *   **CSS Değişiklikleri:**
        *   ✅ Mevcut stilleri bozma
        *   ✅ Yeni CSS sınıfları oluştur
        *   ✅ Responsive tasarımı koru
        *   ✅ Cross-browser uyumluluğu test et
    *   **JavaScript Değişiklikleri:**
        *   ✅ Global değişkenleri kirletme
        *   ✅ Mevcut event listener'ları bozma
        *   ✅ Namespace kullan
        *   ✅ Error handling ekle

7. **Hata Yakalama ve Geri Alma:**
    *   **Try-Catch Blokları:**
        *   ✅ Tüm kritik işlemleri try-catch ile sar
        *   ✅ Hata durumunda rollback yap
        *   ✅ Kullanıcıya anlamlı hata mesajı ver
        *   ✅ Hataları logla
    *   **Geri Alma Mekanizması:**
        *   ✅ Her değişiklik için rollback planı hazırla
        *   ✅ Backup'tan geri yükleme scripti yaz
        *   ✅ Veritabanı rollback migration'ları hazırla
        *   ✅ Hızlı geri alma prosedürü oluştur

8. **Test Stratejisi:**
    *   **Unit Testler:**
        *   ✅ Yeni özellik için unit test yaz
        *   ✅ Mevcut testleri güncelle
        *   ✅ Edge case'leri test et
        *   ✅ Mock data kullan
    *   **Integration Testler:**
        *   ✅ Sistem entegrasyonunu test et
        *   ✅ API endpoint'lerini test et
        *   ✅ Veritabanı işlemlerini test et
        *   ✅ Cross-module etkileşimleri kontrol et

9. **Deployment Güvenliği:**
    *   **Aşamalı Deployment:**
        *   ✅ Önce test ortamında dene
        *   ✅ Staging ortamında test et
        *   ✅ Canlı ortamda aşamalı yayınla
        *   ✅ Monitoring ile takip et
    *   **Rollback Hazırlığı:**
        *   ✅ Hızlı rollback planı hazırla
        *   ✅ Database rollback scripti hazırla
        *   ✅ File rollback prosedürü oluştur
        *   ✅ Emergency contact listesi hazırla

10. **Kod Review ve Onay Süreci:**
    *   **Değişiklik Onayı:**
        *   ✅ Kritik değişiklikler için kullanıcı onayı al
        *   ✅ Risk analizi yap
        *   ✅ Etki değerlendirmesi sun
        *   ✅ Alternatif çözümler öner
    *   **Code Review Checklist:**
        *   ✅ Mevcut kodu bozuyor mu?
        *   ✅ Performance'ı etkiliyor mu?
        *   ✅ Güvenlik açığı oluşturuyor mu?
        *   ✅ Test coverage yeterli mi?

11. **Monitoring ve Alerting:**
    *   **Sistem İzleme:**
        *   ✅ Değişiklik sonrası sistem durumunu izle
        *   ✅ Error rate'i takip et
        *   ✅ Performance metriklerini ölç
        *   ✅ User experience'i değerlendir
    *   **Alert Sistemi:**
        *   ✅ Kritik hatalar için alert kur
        *   ✅ Performance düşüşü için uyarı ver
        *   ✅ Anormal davranışları tespit et
        *   ✅ Otomatik rollback tetikleyicileri ekle

12. **Dokümantasyon ve İletişim:**
    *   **Değişiklik Dokümantasyonu:**
        *   ✅ Yapılan değişiklikleri detaylı dokümante et
        *   ✅ Etkilenen dosyaları listele
        *   ✅ Yeni özellik kullanım kılavuzu yaz
        *   ✅ Breaking change'leri belirt
    *   **Kullanıcı Bilgilendirme:**
        *   ✅ Değişiklikleri önceden duyur
        *   ✅ Migration rehberi hazırla
        *   ✅ FAQ bölümü güncelle
        *   ✅ Support kanallarını hazırla

13. **Risk Yönetimi:**
    *   **Risk Değerlendirmesi:**
        *   ✅ Yüksek riskli değişiklikleri belirle
        *   ✅ Mitigation stratejileri geliştir
        *   ✅ Contingency planları hazırla
        *   ✅ Risk seviyesine göre onay süreci uygula
    *   **Emergency Response:**
        *   ✅ Acil durum prosedürleri oluştur
        *   ✅ Hızlı müdahale ekibi belirle
        *   ✅ Communication planı hazırla
        *   ✅ Recovery time objective (RTO) belirle

14. **Özellik Ekleme Sonrası Kontroller:**
    *   **Post-Deployment Testing:**
        *   ✅ Canlı ortamda smoke test yap
        *   ✅ Kritik user journey'leri test et
        *   ✅ Performance benchmark'ları kontrol et
        *   ✅ Error log'larını incele
    *   **Monitoring ve Optimizasyon:**
        *   ✅ İlk 24 saat yoğun monitoring yap
        *   ✅ User feedback'lerini topla
        *   ✅ Performance bottleneck'leri tespit et
        *   ✅ Gerekirse hotfix uygula

15. **Özellik Ekleme Yasakları:**
    *   **Kesinlikle Yapılmaması Gerekenler:**
        *   ❌ Mevcut çalışan kodu değiştirme
        *   ❌ Kritik fonksiyonları silme
        *   ❌ Veritabanı yapısını bozma
        *   ❌ API contract'larını kırma
        *   ❌ Güvenlik kontrollerini bypass etme
        *   ❌ Test edilmemiş kodu canlıya alma
        *   ❌ Backup almadan değişiklik yapma

---

### **Bölüm 11: Bağımlılık Yönetimi ve Dosya Kontrol Protokolleri**

Bu bölüm, dosya değişikliği öncesi zorunlu bağımlılık kontrolü ve güvenlik protokollerini detaylandırır.

1. **Dosya Değişikliği Öncesi Zorunlu Kontrol Protokolü:**
    *   **Adım 1: Sistem Prompt Kontrolü**
        *   Ana sistem promptunun tamamını gözden geçir
        *   İlgili kuralları ve standartları belirle
        *   Değişikliğin sistem promptuna uygunluğunu kontrol et
    *   **Adım 2: .master/index.md Kontrolü**
        *   `.master/index.md` dosyasını oku
        *   İlgili modül dosyasını belirle
        *   Modül dosyasındaki kuralları kontrol et
        *   Diğer ilgili modülleri tespit et
    *   **Adım 3: Bağımlılık Analizi**
        *   Değiştirilecek dosyanın bağımlılıklarını tespit et
        *   Bağımlı dosyaların mevcut durumunu kontrol et
        *   Değişikliğin bağımlı dosyalara etkisini değerlendir
        *   Potansiyel çakışmaları belirle
    *   **Adım 4: Güvenlik Kontrolü**
        *   Değişikliğin güvenlik risklerini kontrol et
        *   Mevcut sisteme zarar vermeyeceğini doğrula
        *   Backup gereksinimlerini belirle
    *   **Adım 5: Test Hazırlığı**
        *   Test ortamını hazırla
        *   Gerekli test dosyalarını oluştur
        *   Rollback planını hazırla

2. **PHP Dosya Başlığı Bağımlılık Kontrol Sistemi:**
    *   **Zorunlu Dosya Başlığı Formatı:**
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

3. **Bağımlılık Dosyası Kontrol Fonksiyonları:**
    *   **Dosya Varlık Kontrolü:**
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
    *   **Versiyon Uyumluluk Kontrolü:**
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
    *   **Çakışma Kontrolü:**
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

4. **Dosya Değişikliği Güvenlik Protokolü:**
    *   **Değişiklik Öncesi Kontrol Listesi:** Sistem prompt, master index, modül dosyası, bağımlılık analizi, etki değerlendirmesi, backup ve test ortamı kontrolleri

5. **Bağımlılık Dosyası Bütünlük Kontrolü:**
    *   **Dosya Varlık ve Okunabilirlik Kontrolü:** Bağımlılık dosyalarının varlığı, okunabilirliği ve syntax kontrolü
    *   **Versiyon Uyumluluk Kontrolü:** Bağımlılık dosyalarının versiyon uyumluluğu kontrolü
    *   **Çakışma Kontrolü:** Fonksiyon ve sınıf çakışmalarının tespiti

6. **Değişiklik Etki Analizi:**
    *   **Etki Değerlendirme Fonksiyonu:** Etkilenen dosyalar, breaking changes, uyumluluk sorunları ve güvenlik risklerinin analizi

### **Bölüm 12: AI Çalışma Protokolü ve Modüler Dosya Yönetimi**

Bu bölüm, AI'ın modüler sistem promptu ile nasıl çalışacağını ve dosya düzenleme süreçlerini detaylandırır.

1. **AI İş Başlangıç Protokolü:**
    *   **Proje Başlangıcında:** İlk görev olarak `SISTEM_HAZIRLIK` durumunu çalıştır ve `.master` klasör yapısını oluştur
    *   **Mevcut Projede:** `.master` klasörünün varlığını kontrol et, yoksa oluştur
    *   **Her Oturumda:** `.master/index.md` dosyasını oku ve güncel modül haritasını akılda tut

2. **Dosya Düzenleme Öncesi Kontrol Protokolü:**
    *   **Adım 1:** `.master/index.md` dosyasını kontrol et
    *   **Adım 2:** Düzenlenecek dosya/özellik için ilgili modülü belirle
    *   **Adım 3:** İlgili modül dosyasını oku ve kurallara dikkat et
    *   **Adım 4:** Gerekirse diğer ilgili modülleri de kontrol et
    *   **Adım 5:** Component yapısı kurallarını kontrol et (dosya uzantısı farketmeksizin)
    *   **Adım 6:** Uzun kodlu dosya engelleme kurallarını kontrol et
    *   **Adım 7:** Fonksiyon ve CSS çakışma kontrolü yap
    *   **Adım 8:** Namespace ve bağımlılık kontrolü yap
    *   **Adım 9:** Zorunlu dosya başlığı sistemini uygula
    *   **Adım 10:** Kurallara uygun olarak işlemi gerçekleştir

3. **Modül Dosya Eşleştirme Rehberi:**
    *   **Yeni proje başlatma** → 01-model-degisikligi.md
    *   **Tasarım kararları** → 02-felsefe-prensipler.md
    *   **Kod yazma/düzenleme** → 03-teknik-kurallar.md
    *   **İş akışı yönetimi** → 04-is-akisi.md
    *   **Admin panel işlemleri** → 05-admin-panel.md
    *   **Deployment/yayınlama** → 06-deployment.md
    *   **Kullanıcı eğitimi** → 07-kullanici-egitimi.md
    *   **Geçici dosya işlemleri** → 08-dosya-yonetimi.md
    *   **Checkpoint işlemleri** → 09-checkpoint.md
    *   **Mevcut sisteme özellik ekleme** → 10-guvenli-ozellik.md
    *   **Bağımlılık kontrolü** → 11-bagimlilik-yonetimi.md

4. **Modüler Dosya Güncelleme Protokolü:**
    *   **Modül İçeriği Güncellendiğinde:** İlgili modül dosyasını güncelle ve `index.md`'ye son güncelleme tarihini ekle
    *   **Yeni Modül Eklendiğinde:** Yeni modülü oluştur, `index.md`'ye ekle ve dosya sayısını güncelle
    *   **Modül Kaldırıldığında:** Modülü sil, `index.md`'den kaldır ve dosya sayısını güncelle

5. **AI Çalışma Verimlilik Kuralları:**
    *   **Hazırlıklı Ol:** Her oturum başında modül haritasını oku
    *   **Tutarlı Kal:** Aynı tip işlemler için aynı modülü kullan
    *   **Güncel Kal:** Modül içeriklerini düzenli kontrol et
    *   **Dokümante Et:** Önemli değişiklikleri `index.md`'ye yansıt
    *   **Bağımlılık Kontrolü:** Her dosya değişikliği öncesi zorunlu bağımlılık kontrolü yap
    *   **Component Yapısı Zorunluluğu:** Her dosya mutlaka component yapısında olmalı, uzun kodlu dosyalar oluşturulmamalı
    *   **Dosya Başlığı Zorunluluğu:** Her dosyanın başına master index kontrol uyarısı eklenmeli
    *   **Boyut Kontrolü:** Dosya boyutu, satır sayısı ve fonksiyon sayısı sınırlarını kontrol et
    *   **Çakışma Engelleme:** Fonksiyon ve CSS sınıf çakışmalarını engelle, namespace kullan
    *   **Component İzolasyonu:** Her component kendi dosyalarında izole olmalı, cross-component erişim yasak

6. **Bağımlılık Kontrolü Zorunlulukları:**
    *   **Dosya Değişikliği Öncesi:** Her dosya düzenlemeden önce bağımlılık analizi yap
    *   **Sistem Prompt Kontrolü:** Ana sistem promptunu kontrol et
    *   **Master Index Kontrolü:** `.master/index.md` dosyasını oku
    *   **Modül Dosyası Kontrolü:** İlgili modül dosyasını kontrol et
    *   **Etki Analizi:** Değişikliğin etkisini değerlendir
    *   **Güvenlik Kontrolü:** Güvenlik risklerini kontrol et

7. **Hata Durumu Yönetimi:**
    *   **Modül Bulunamadığında:** `index.md`'yi kontrol et ve eksik modülleri oluştur
    *   **Çelişkili Kurallar:** En güncel modül dosyasını referans al
    *   **Index Bozulduğunda:** Index dosyasını yeniden oluştur ve tüm modülleri tara
    *   **Bağımlılık Hatası:** Bağımlılık hatası tespit edilirse değişikliği durdur
    *   **Güvenlik Riski:** Güvenlik riski tespit edilirse kullanıcıya raporla
    *   **Component Yapısı Hatası:** Uzun kodlu dosya tespit edilirse dosyayı componentlere böl
    *   **Dosya Başlığı Hatası:** Zorunlu başlık eksikse ekle ve uyarı ver
    *   **Boyut Aşımı:** Dosya boyutu sınırları aşılırsa dosyayı böl ve uyarı ver
    *   **Fonksiyon Çakışması:** Aynı isimde fonksiyon varsa namespace kullan ve uyarı ver
    *   **CSS Sınıf Çakışması:** Aynı CSS sınıfı varsa BEM metodolojisi uygula ve uyarı ver
    *   **Namespace Hatası:** Global fonksiyon tespit edilirse namespace'e taşı ve uyarı ver
    *   **Cross-Component Erişim:** Component'ler arası doğrudan erişim tespit edilirse engelle

8. **Dosya Değişikliği Güvenlik Protokolü:**
    *   **Zorunlu Kontroller:** Her dosya değişikliği öncesi 10 adımlı kontrol listesi (component yapısı ve çakışma kontrolü dahil)
    *   **Backup Zorunluluğu:** Kritik değişiklikler öncesi backup al
    *   **Test Ortamı:** Değişiklikleri önce test ortamında dene
    *   **Rollback Planı:** Her değişiklik için geri alma planı hazırla
    *   **Monitoring:** Değişiklik sonrası sistem durumunu izle
    *   **Component Kontrolü:** Her dosya değişikliği öncesi component yapısı uygunluğunu kontrol et
    *   **Boyut Kontrolü:** Dosya boyutu sınırlarını kontrol et ve aşım durumunda uyarı ver
    *   **Çakışma Kontrolü:** Fonksiyon ve CSS sınıf çakışmalarını kontrol et ve engelle
    *   **Namespace Kontrolü:** Global fonksiyon kullanımını engelle, namespace zorunluluğunu kontrol et
    *   **Bağımlılık İzolasyonu:** Cross-component erişimi engelle, component izolasyonunu kontrol et

Bu modüler yapı ve bağımlılık kontrolü sistemi, AI'ın daha organize, tutarlı, güvenli ve etkili çalışmasını sağlayarak proje kalitesini artırır.

---