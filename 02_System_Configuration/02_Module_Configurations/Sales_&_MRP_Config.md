# ⚙️ MTO (Sipariş Üzerine Üretim) ve Otomatik İş Emri Konfigürasyonu (REQ-002 & REQ-006)

**Proje Adı:** ABC Mobilya ERP Dijital Dönüşümü  
**Hedef Kurum:** ABC Mobilya San. ve Tic. A.Ş.  
**Modül:** Satış (Sales) & Üretim (MRP)  
**Gereksinim Referansı:** REQ-002 (Ürün Reçetesi/BOM Yönetimi) & REQ-006 (MTO Otomatik Üretim Tetikleme)  
**Yazar:** Kıdemli ERP İş Analisti  
**Tarih:** Ekim 2026  

---

## 1. İş İçeriği ve Amaç
ABC Mobilya A.Ş., bitmiş ürün stok maliyetlerini optimize etmek ve özel/sipariş üzerine mobilya üretim süreçlerini doğrudan müşteri taleplerine bağlamak istemektedir. Mevcut durumda (As-Is), satış departmanı ile imalat sahası arasındaki manuel iletişim eksikliği; yanlış veya eksik ürün üretilmesine ve müşteri teslimat sürelerinin uzamasına yol açmaktaydı.

Bu sorunu çözmek amacıyla **Sipariş Üzerine Tedarik (MTO)** ve **Üret (Manufacture)** entegrasyonu kurgulanmıştır. Müşteri Satış Siparişi (SO) onaylandığı an, sistem stok kontrolü yaparak otomatik olarak ilgili siparişle ilişkili bir **Üretim Emri (MO)** tetiklemektedir.

---

## 2. Sistem Konfigürasyonu & Ürün Reçetesi (BOM)

### 2.1 İmalat ve Rota Ayarları
* **Örnek Mamul:** `[STK-CAL-003] 5 Raflı Kitaplık (Metal/Ahşap)`
* **Ürün Tipi:** Stoklanabilir Ürün (`Storable Product`)
* **Aktif Rotalar:** `Replenish on Order (MTO)` + `Manufacture`

### 2.2 Ürün Reçetesi (BOM) Yapısı

| Bileşen Kodu | Bileşen Açıklaması | Tüketilecek Miktar | Birim | Stok Durumu |
| :--- | :--- | :--- | :--- | :--- |
| `HM-ISL-002` | Profil Metal Yan İskelet/Karkas | 1,00 | Adet | Uygun |
| `HM-ASP-001` | Ahşap Desenli Raf Tablası | 1,00 | Adet | Mevcut Değil (İkmal Bekliyor) |
| `HM-BGL-001` | Çapraz Gergi Teli & Bağlantı Vidaları | 1,00 | Paket | Uygun |

---

## 3. Otomatik İş Akışının Doğrulanması

1. **Satış Siparişi (SO):** Satış modülü üzerinden `S00007` numaralı sipariş oluşturulup onaylanmıştır.
2. **Otomatik Üretim Emri (MO):** MTO mekanizması tetiklenerek **`WH/MO/00002`** referanslı Üretim Emri sistem tarafından otomatik olarak `Doğrulanmış` statüsünde açılmıştır.
3. **Malzeme Rezerve / Stok Kontrolü:** Sistem, reçetede yer alan ham maddeleri depodan rezerve etmiştir. Eksiğe düşen bileşenler (`HM-ASP-001`) için otomatik ikmal/satınalma talebi altyapısı devreye girmiştir.

---

## 4. Doğrulama ve Test Kanıtları

* **Master Data Dosyası:** `02_System_Configuration/01_Master_Data/BOM_Recipes.csv`
* **Sistem Ekran Görüntüsü:** `03_Testing_&_Simulation/screenshots/03_MTO_Manufacturing_Order.png`
