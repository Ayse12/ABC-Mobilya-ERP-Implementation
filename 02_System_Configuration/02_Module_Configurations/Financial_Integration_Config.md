# REQ-011: Finans Entegrasyonu ve Otomatik Faturalama (Financial Integration & Automated Invoicing)

## 🎯 Amaç ve Kapsam
Bu konfigürasyonun amacı, ABC Mobilya operasyonlarında tamamlanan müşteri teslimatlarının (`WH/OUT`) ve onaylanan satın alma işlemlerinin (Vendor Bills) manuel müdahaleye gerek kalmadan otomatik olarak Muhasebe ve Finans modülüne aktarılmasını ve fatura taslaklarına dönüştürülmesini sağlamaktır.

---

## ⚙️ Odoo Modül ve Parametre Ayarları

### 1. Faturalama Politikası (Invoicing Policy)
* **Satış (Sales) -> Ürünler (Products):** İlgili mobilya ürün kartlarında faturalandırma politikası **"Delivered quantities" (Teslim edilen miktarlar)** veya siparişe göre faturalandırma senaryosuna göre yapılandırılmıştır.
* **Depo (Inventory) -> Sevkiyat:** Teslimat (`Delivery Order - WH/OUT`) tamamlandığında (Validate edildiğinde), faturalandırılacak miktar (Invoiced Quantity) muhasebe modülü tarafından tetiklenir.

### 2. Otomatik Fatura Oluşturma (Automated Invoicing / Invoice Status)
* Onaylanan teslimat fişleri üzerinden **"Create Invoice"** butonuna basılarak veya toplu faturalandırma sihirbazı (`Batch Invoicing`) kullanılarak faturalar anında taslak (`Draft`) statüsünde oluşturulur.
* Satın alma süreçlerinde ise mal kabulü (`Receipt - WH/IN`) sonrasında gelen tedarikçi faturası `Vendor Bill` ile eşleştirilir.

### 3. Yevmiye Kaydı (Journal Entry) ve Cari Eşleşme
* Fatura onaylandığında (`Post`), Odoo arka planda otomatik olarak çift yönlü muhasebe yevmiye kaydını oluşturur:
  * **Borç (Debit):** Alacak Hesapları (Accounts Receivable - 120 Müşteriler)
  * **Alacak (Credit):** Satış Gelirleri (Sales / Revenue Accounts - 600 Yurtiçi Satışlar) ve Hesaplanan KDV.

---

## 🎬 Adım Adım İşleyiş (Odoo Workflow)

1. **Sevkiyatın Tamamlanması:** Depo operasyonlarında ABC Mobilya müşteri siparişi için `WH/OUT` belgesi `Done` statüsüne getirilir.
2. **Fatura Taslağı:** **Accounting / Invoicing** modülüne gidilir. Müşteriler -> Faturalar (Invoices) sekmesinden ilgili teslimata istinaden oluşan taslak fatura açılır.
3. **Doğrulama ve Yevmiye Kaydı:** Fatura üzerindeki kalemlerin ve tutarların sevkiyatla birebir örtüştüğü doğrulanır. **"Confirm"** butonuna basılarak yevmiye kaydının ve cari borç/alacak eşleşmesinin tam otomatik oluştuğu kontrol edilir.

---

## 📂 GitHub Dosya Yolu
* **Config Dosyası:** `02_System_Configuration/02_Module_Configurations/Financial_Integration_Config.md`
* **Ekran Görüntüsü (SS):** `03_Testing_&_Simulation/screenshots/08_Financial_Integration.png`
