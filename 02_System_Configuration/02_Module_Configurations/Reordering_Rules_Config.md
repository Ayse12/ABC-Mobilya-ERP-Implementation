# ⚙️ İkmal Kuralları ve Otomatik Satınalma Konfigürasyonu (REQ-007)

**Proje Adı:** ABC Mobilya ERP Dijital Dönüşümü  
**Hedef Kurum:** ABC Mobilya San. ve Tic. A.Ş.  
**Modül:** Stok (Depo) & Satınalma  
**Gereksinim Referansı:** REQ-007 (Minimum/Maksimum Emniyet Stoğu ve Otomatik PR Motoru)  
**Yazar:** Kıdemli ERP İş Analisti  
**Tarih:** Ekim 2026  

---

## 1. İş İçeriği ve Amaç
ABC Mobilya A.Ş., takip edilmeyen ham madde stok tükenmeleri nedeniyle sık sık üretim duraksamaları yaşamaktaydı. Mevcut durum (As-Is) süreçlerinde, malzeme eksiklikleri üretim sahasında manuel olarak fark ediliyor; bu da ciddi teslimat gecikmelerine ve atıl iş gücüne yol açıyordu.

Manuel stok kontrollerini ortadan kaldırmak ve üretim iş emirleri için malzeme kullanılabilirliğini garanti altına almak amacıyla **Odoo İkmal Kuralları (Min/Max Kuralları)** kurgulanmıştır. Bu otomatik mekanizma, stok eşiklerini anlık olarak izleyerek ve otomatik satınalma talepleri oluşturarak **REQ-007** gereksinimini tam olarak karşılamaktadır.

---

## 2. Sistem Konfigürasyonu ve Mantığı

### 2.1 İkmal Parametreleri
* **Konum / Lokasyon:** `WH/Stock` (Ana Fabrika Deposu)
* **Tetikleme Mekanizması:** Odoo Zamanlayıcısı (`Run Scheduler`) üzerinden otomatik
* **Satınalma Eylemi:** Otomatik Teklif Talebi Taslağı (RFQ / Satınalma Sipariş Taslağı)

### 2.2 İkmal Kuralları Ana Tablosu

|  Ürün Açıklaması | Kategori | Min Miktar (Emniyet) | Max Miktar (Hedef) | Birim | Varsayılan Tedarikçi |
| :--- | :--- | :--- | :--- | :--- | :--- |
| MDF Plaka 18mm (180x240) | Ham Maddeler | 10 | 50 | Adet | *** |
| Tay Tüyü Gri Kumaş | Ham Maddeler | 25 | 100 | Metre | *** |
| Ahşap Cila / Vernik (Mat) | Ham Maddeler | 5 | 25 | Litre | *** |
| Masa Bağlantı Vida Seti | Hırdavat | 20 | 100 | Set | *** |

*(Not: 10'dan fazla ürünün tüm ikmal kuralları haritası `02_System_Configuration/Fuctional_Requirements/Reordering_Rules_Master.xlsx` dosyasında saklanmaktadır.)*

---

## 3. Otomatik İş Akışının Çalıştırılması

1. **Eşik İhlali Tespiti:** Satış siparişleri (SO) veya üretim emirleri (MO) stok rezerve ettikçe, tahmini stok miktarı belirlenen **Minimum Miktar** seviyesinin altına düşer.
2. **Zamanlayıcının Çalışması:** Sistem ikmal motorunu tetikler (`Stok -> İşlemler -> Yeniden Siparişleri Çalıştır`).
3. **RFQ (Teklif Talebi) Oluşturulması:** Odoo, stok seviyesini **Maksimum Miktar** seviyesine tamamlamak için gereken miktarı otomatik olarak hesaplar ($Sipariş_{Miktarı} = Max - Mevcut$) ve tanımlı birincil tedarikçiye atanmış bir **Teklif Talebi Taslağı (RFQ)** oluşturur.
4. **Satınalma ve Üretim Hizalanması:** Satınalma departmanı, üretim sahasından gelen kağıt formlara veya manuel bildirimlere ihtiyaç duymadan taslak RFQ'yu inceleyip Satınalma Siparişine (PO) dönüştürür.

---

## 4. Doğrulama ve Test Kanıtları

* **Konfigürasyon Dosyası:** `02_System_Configuration/Fuctional_Requirements/Reordering_Rules_Master.xlsx`
* **Sistem Ekran Görüntüsü:** `03_Testing_&_Simulation/screenshots/02_Reordering_Rules_List.png`
