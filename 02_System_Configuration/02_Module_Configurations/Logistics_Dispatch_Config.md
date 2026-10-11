# ⚙️ Logistics & Dispatch Management Configuration (REQ-010)

**Project Name:** ABC Mobilya ERP Digital Transformation
**Target Organization:** ABC Mobilya San. ve Tic. A.Ş.
**Author:** Ayşe İlhanlı (Lead ERP Business Analyst)
**Module:** Inventory & Logistics Management
**Requirement Reference:** REQ-010 (Logistics & Dispatch Management)
**Version:** v1.0 | **Date:** October 2026

---

## 1. Business Context & Objective
Mevcut durumda (As-Is), imalatı ve kalite kontrolü tamamlanan ürünlerin sevkiyat süreçleri manuel irsaliyeler üzerinden yürütülmekte, depodan çıkan ürünlerin stok düşüşleri anlık olarak sisteme yansıtılamamaktaydı. Bu durum sevkiyat gecikmelerine ve stok tutarsızlıklarına yol açmaktaydı.

Bu sorunu ortadan kaldırmak amacıyla Odoo ERP üzerinde Entegre Lojistik ve Sevkiyat Yönetimi (Logistics & Dispatch) kurgulanmıştır.

## 2. System Configuration & Functional Workflow

2.1 REQ-010: Logistics & Dispatch Management (Lojistik ve Sevkiyat Yönetimi)
- Onaylı Ürün Transferi: Kalite kontrol adımlarından (REQ-008) başarıyla geçen veya teslimata hazır hale gelen ürünler sevkiyat deposuna (`WH/Output`) yönlendirilir.
- Sevkiyat Emri (Delivery Order - WH/OUT): Müşteri siparişleri ve teslimat planına uygun olarak otomatik giden transfer (WH/OUT) belgeleri oluşturulur.
- Otomatik Stok Düşüşü: Depo görevlisi tarafından sevkiyatın doğrulanması (Validate) ile birlikte envanter stok miktarları gerçek zamanlı olarak düşürülür.


## 3. Workflow Execution & Verification Steps
1. Delivery Order Generation: Müşteri siparişlerine istinaden `WH/OUT/00001` - `WH/OUT/00007` arası giden transfer emirleri oluşturulmuştur.
2. Outbound Validation: Ürünlerin toplama ve paketleme doğrulamaları tamamlanarak teslimat durumları "Yapıldı" (Done) statüsüne getirilmiştir.
3. Real-Time Stock Deduction: Sevkiyatın tamamlanmasıyla envanter güncellenmiş ve cari teslimat akışı tamamlanmıştır.
---
## 4. Verification & Testing Evidence
- Dispatch Screenshot:
  - 03_Testing_&_Simulation/screenshots/07_Logistics_&_Dispatch.png
