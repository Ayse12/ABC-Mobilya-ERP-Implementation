# ⚙️ Real-Time Goods Receipt & Automated Billing Configuration (REQ-004 & REQ-005)

**Project Name:** ABC Mobilya ERP Digital Transformation  
**Target Organization:** ABC Mobilya San. ve Tic. A.Ş.  
**Author:** Ayşe İlhanlı (Lead ERP Business Analyst)  
**Module:** Procurement, Inventory & Finance  
**Requirement Reference:** REQ-004 (Real-Time Goods Receipt & PO Update) & REQ-005 (Automated Billing via Delivery)  
**Version:** v1.0 | **Date:** October 2026  

---

## 1. Business Context & Objective
Mevcut durumda (As-Is), satın alınan ham maddelerin depoya giriş irsaliyelerinin muhasebe ve üretime 2 gün geç bildirilmesi nedeniyle üretim hatları durmakta ve maliyet takibi yapılamamaktaydı.

Bu sorunu ortadan kaldırmak amacıyla Odoo üzerinde **Gerçek Zamanlı Mal Kabul (Goods Receipt)** ve **Teslimata Bağlı Fatura/Cari Kayıt (Automated Billing)** entegrasyonu kurgulanmıştır.

---

## 2. System Configuration & Functional Workflow

### 2.1 REQ-004: Real-Time Goods Receipt & PO Update
* **Eksik Malzeme İkmalı:** Üretim Emri (`WH/MO/00002`) sırasında eksik tespit edilen `HM-ASP-001` (Ahşap Desenli Raf Tablası) malzemesi için otomatik RFQ/PO süreci tetiklenmiştir.
* **Depo Mal Kabul (GRN):** Tedarikçiden hammadde girişi yapıldığı anda (Receipt / Validate), sistem envanter miktarını ve ilgili depodaki stok seviyesini anlık olarak günceller.
* **Üretim & Finans Bildirimi:** Mal kabul tamamlandığı an, askıda bekleyen Üretim Emri (MO) durumunu otomatik olarak "Üretime Hazır" (Ready) seviyesine getirir ve Satınalma Siparişini (PO) günceller.

### 2.2 REQ-005: Automated Billing & Finance Integration
* **Fatura Taslağı Oluşturma:** Depoya kabul edilen malzemelerin irsaliye/teslimat doğrulamasına dayanarak sistem otomatik Satınalma Faturası (Vendor Bill) taslağı oluşturur.
* **Cari Borç Kaydı:** Doğrulanan faturalar doğrudan Finans/Muhasebe modülüne aktarılarak tedarikçi cari borç kaydı (Accounts Payable) anlık olarak işlenir.

---

## 3. Workflow Execution & Verification Steps

1. **PO Confirmation:** Otomatik oluşan Satınalma Siparişi kontrol edilerek `PO/RFQ` onaylanmıştır.
2. **Goods Receipt (GRN):** Depo görevlisi ürün kabulünü yapıp `Doğrulanmış (Done)` statüsüne getirmiştir.
3. **Inventory Update:** Malzeme `WH/Stock` lokasyonuna işlenmiş ve eksik malzeme uyarısı ortadan kalkmıştır.

---

## 4. Verification & Testing Evidence

* **PO & Goods Receipt Screenshots:** 
  * `03_Testing_&_Simulation/screenshots/04_Purchase_Order_Auto.png`
  * `03_Testing_&_Simulation/screenshots/05_Goods_Receipt_GRN.png`
