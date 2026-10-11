
# 🪑 ABC Mobilya San. ve Tic. A.Ş. — ERP Dijital Dönüşüm Projesi

> **Odoo ERP Tabanlı Uçtan Uca Üretim, Tedarik, Kalite, Lojistik ve Finans Otomasyonu Simülasyonu**  
> **Proje Sahibi / Baş İş Analisti:** Ayşe İlhanlı  
> **Tarih:** Eylül- Ekim 2026 | **Versiyon:** v1.0 (Production-Ready)

---

## 🎯 Proje Hakkında
Bu repository, **ABC Mobilya San. ve Tic. A.Ş.**'nin manuel ve Excel tabanlı eski sisteminden (**As-Is**), modern entegre ERP yapısına (**To-Be**) geçiş süreçlerini belgelemek amacıyla hazırlanmıştır. Projede, mobilya imalatı ve perakende sektörüne özel 12 temel fonksiyonel gereksinim (REQ-001 - REQ-012) **Odoo ERP** üzerinde uçtan uca kurgulanmış ve test edilmiştir.

---

## 📂 Repository Mimarisi & Dosya Yapısı

```text
├── 01_Analysis_&_Design/
│   ├── As-Is_To-Be_Process_Maps.png
│   └── Business_Requirements_FRD.md        # Fonksiyonel Gereksinimler Dokümanı (FRD v1.0)
├── 02_System_Configuration/
│   ├── 01_Master_Data/
│   │   ├── BOM_Recipes.csv                 # Ürün Reçeteleri (BOM)
│   │   ├── Product_Master_Data.csv         # Ürün ve Malzeme Ana Verileri
│   │   └── Vendor_Customer_Master.csv      # Müşteri ve Tedarikçi Kartları
│   └── 02_Module_Configurations/
│       ├── Financial_Integration_Config.md # REQ-005 & REQ-012: Faturalandırma & Maliyetleme
│       ├── Logistics_Dispatch_Config.md    # REQ-010: Lojistik & Sevkiyat Planlama
│       ├── Master_Data_Config.md           # REQ-001 & REQ-003: Stok Görünürlüğü & Özel Sipariş
│       ├── Procurement_&_GRN_Config.md     # REQ-004: Satınalma & Mal Kabul (GRN)
│       ├── Quality_Control_Config.md       # REQ-008 & REQ-009: Kalite Kontrol & Rework
│       ├── Reordering_Rules_Config.md      # REQ-007: Min/Max İkmal Kuralları
│       └── Sales_&_MRP_Config.md           # REQ-002 & REQ-006: BOM & MTO Üretim Akışı
├── 03_Testing_&_Simulation/
│   └── screenshots/
│       ├── 01_Master_Data_Setup.png
│       ├── 02_Reordering_Rules_List.png
│       ├── 03_MTO_Manufacturing_Order.png
│       ├── 04_Purchase_Order_Auto.png
│       ├── 05_Goods_Receipt_GRN.png
│       ├── 06_Quality_Control_Gate.png
│       ├── 07_Logistics_&_Dispatch.png
│       ├── 08_Financial_Integration.png
│       └── 09_Executive_Dashboard.png
└── README.md                               # Proje Vitrini ve Özet Dokümanı
