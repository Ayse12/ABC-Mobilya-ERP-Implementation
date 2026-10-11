# ⚙️ Mandatory Quality Control Gate & Rework Process (REQ-008 & REQ-009)

**Project Name:** ABC Mobilya ERP Digital Transformation  
**Target Organization:** ABC Mobilya San. ve Tic. A.Ş.  
**Author:** Ayşe İlhanlı (Lead ERP Business Analyst)  
**Module:** Quality Control (QC) & Manufacturing (MRP)  
**Requirement Reference:** REQ-008 (Mandatory Quality Control Gate) & REQ-009 (Automated Rework Order Generation)  
**Version:** v1.0 | **Date:** October 2026  

---

## 1. Business Context & Objective
Mevcut durumda (As-Is), üretimi biten ürünlerde zorunlu bir kalite kontrol (QC) aşaması olmaması nedeniyle eksik parça veya yanlış kumaş hataları ancak sevkiyat günü veya doğrudan müşterinin evinde fark edilmekteydi. Bu durum müşteri memnuniyetsizliğine ve yüksek maliyetli iadelere yol açıyordu.

Bu sorunu çözmek amacıyla Odoo üzerinde **Zorunlu Kalite Kontrol Kapısı (Quality Control Gate)** ve **Hata Yönetimi/Yeniden İşlem (Rework)** akışı kurgulanmıştır.

---

## 2. System Configuration & Functional Workflow

### 2.1 REQ-008: Mandatory Quality Control Gate
* **Kalite Kontrol Noktası:** Üretim Emri (MO) tamamlandığında (`Done` statüsüne geçiş öncesi), sistem otomatik olarak bir Kalite Kontrol kontrol noktası tetikler.
* **Sevkiyat Engeli:** Ürün, kalite kontrol testinden (Görsel kontrol, ölçü kontrolü, menteşe ve bağlantı kontrolü) **"Pass" (Başarılı)** onayı almadan sevkiyat deposuna (`WH/Output`) aktarılamaz ve sevkiyat irsaliyesine eklenemez.

### 2.2 REQ-009: Automated Rework Order Generation (Yeniden İşlem)
* **Hata Kategorizasyonu:** Kalite kontrol sırasında bir kusur tespit edildiğinde (örn. *Ahşap yüzeyde çizik* veya *Kumaş defosu*), kontrol personeli sonucu **"Fail" (Başarılı Değil)** olarak işaretler.
* **Rötuş İş Emri:** Sistem otomatik olarak ilgili ürün için bir **Rework / Yeniden İşlem Emri** oluşturur ve ürün ilgili düzeltme istasyonuna yönlendirilir.

---

## 3. Workflow Execution & Verification Steps

1. **Üretim Tamamlama:** İmalatı biten ürün için sistem kalite kontrol kontrol listesini (Checklist) ekrana getirir.
2. **QC Onayı / Reddi:** Kontrolör onay verir veya hata kaydı girerek yeniden işlem akışını tetikler.
3. **Sevkiyat Uygunluğu:** Başarılı onay alan ürünler sevkiyat deposuna serbest bırakılır.

---

## 4. Verification & Testing Evidence

* **Quality Control Gate Ekran Görüntüsü:** `03_Testing_&_Simulation/screenshots/06_Quality_Control_Gate.png`
