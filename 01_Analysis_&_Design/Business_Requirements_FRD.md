
# 📄 Functional Requirement Document (FRD)
**Project Name:** AhşapDünyası Mobilya ERP Digital Transformation  
**Target Organization:** AhşapDünyası Mobilya San. ve Tic. A.Ş.  
**Author:** Ayşe İlhanlı (Lead ERP Business Analyst)  
**Version:** v1.0 | **Date:** October 2026  

---

## 1. Document Control & History

| Version | Date | Description | Author | Approved By |
| :--- | :--- | :--- | :--- | :--- |
| v1.0 | 03.10.2026 | Baseline FRD Creation for To-Be ERP Model | Ayşe ilhanlı | Operations Steering Committee |

---

## 2. Company Profile & Scope (Şirket Profili)

* **Company Name:** AhşapDünyası Mobilya San. ve Tic. A.Ş.
* **Industry:** Ahşap / MDF Ev Mobilyası İmalatı ve Perakende Satışı (Yemek odası, Yatak odası, TV üniteleri).
* **Scale & Capacity:** 85 Çalışan (50 Mavi Yaka, 35 Beyaz Yaka/Saha/Mağaza Personeli).
* **Operational Footprint:**
  * 1 Production Facility & Main Warehouse (Organize Sanayi Bölgesi)
  * 2 Showroom / Retail Stores (Şehir Merkezi)
  * 1 E-Commerce & Dealer Sales Team (Fabrika Merkez Binası)

---

## 3. As-Is Problem Statement (Mevcut Durum Kök Neden Analizi)

Şirket genelinde entegre bir ERP yazılımının olmaması; süreçlerin eski bir yerel muhasebe programı, kağıt defterler, Excel siloları ve WhatsApp grupları üzerinden yürütülmesine yol açmaktadır. Bu durum aşağıdaki operasyonel darboğazları yaratmaktadır:

1. **Mağaza & Satış Operasyon Kopukluğu:** Mağazadaki özel müşteri taleplerinin (örn. tay tüyü gri kumaş, +10 cm masa ölçüsü) WhatsApp veya e-posta üzerinden iletilmesi sebebiyle taleplerin kaybolması, Ar-Ge/Fabrika onayı alınmadan gerçekçi olmayan teslimat süreleri (15 gün) verilmesi.
2. **Kör İmalat ve Reçetesiz Üretim:** Ustabaşının imalatı kara kaplı defterden takip etmesi, canlı Excel'i göremediği için ham madde eksikliğini üretimin 4. gününde fark etmesi ve yanlış kumaş/renk ile hatalı üretim yapılması.
3. **Manuel Depo & Geciken Mal Kabul:** Depocunun fiziki kontrol yapmadan stok bilgisi verememesi; satın alınan ham maddelerin depoya giriş irsaliyelerinin muhasebe ve üretime 2 gün geç bildirilmesi nedeniyle üretimin durması.
4. **Kalite Kontrol ve Rework Eksikliği:** Üretimi biten ürünlerde QC aşaması olmadığı için eksik parça veya yanlış kumaş hatalarının ancak sevkiyat günü veya müşterinin evinde fark edilmesi.
5. **Rotasız Sevkiyat & Lojistik Verimsizliği:** Araç kapasitesi ve bölge optimizasyonu yapılmadığı için şoförlerin aynı mahalleye üst üste gitmesi ve tamamlanmamış ürünlerin araca yüklenmeye çalışılması.
6. **Maliyet ve Kârlılık Belirsizliği:** Sipariş bazlı harcanan fiili ham madde, işçilik ve kapora takibinin yapılamaması; fatura kesimlerinin fiziki evrak kayıpları yüzünden haftalarca gecikmesi.

---

## 4. Functional Requirements (Fonksiyonel Gereksinimler)

### 4.1 Sales & Custom Order Management (Satış & Özel Sipariş Yönetimi)
* **REQ-001 (Real-Time Inventory Visibility):** Sales çalışanı anlık stok durumunu ve kullanabileceği ham madde miktarını sipariş ekranında görebilmelidir.
* **REQ-003 (Customization & Technical Approval Workflow):** Standart konfigürasyon parametreleri dışındaki özel talepler (ör. "+10 cm masa boyu", tay tüyü özel kumaş) girildiğinde, sistem siparişi otomatik olarak "Fabrika / Ar-Ge Onayı Bekliyor" statüsüne almalı ve teknik onay gelmeden siparişin kesinleşmesine/üretime kaymasına izin vermemelidir.
* **REQ-006 (Automatic Stock Reservation):** Müşteri siparişi (SO) onaylandığı anda, depodaki hazır mamuller veya tahsis edilecek ham maddeler otomatik olarak ilgili siparişe rezerve edilmelidir.

### 4.2 Manufacturing & MRP (Üretim & Malzeme Planlama)
* **REQ-002 (Automated BOM Explosion):** Üretim modülü, mamul için tanımlanmış Ürün Reçetesini (BOM) kullanarak gerekli hammadde miktarını otomatik hesaplamalıdır.
* **REQ-007 (Automated Purchase Requisition via Min/Max & MRP):** Stok seviyesi belirlenen emniyet stok sınırının altına düştüğünde veya üretim için malzeme eksik olduğunda sistem otomatik Satın Alma Talebi (PR) oluşturmalıdır.
* **REQ-011 (Digital Shop-Floor Terminals):** Üretim sahasındaki ustabaşı ve operatörler, onaylanmış iş emirlerini, güncel ürün reçetelerini (BOM) ve özel sipariş notlarını (kumaş, renk, ölçü) terminal/tablet ekranları üzerinden anlık olarak görüntüleyebilmelidir.

### 4.3 Procurement & WMS / Inventory (Satınalma & Depo Yönetimi)
* **REQ-004 (Real-Time Goods Receipt & PO Update):** Tedarikçiden hammadde girişi (Mal Kabul) yapıldığı anda envanter miktarları, depo lokasyonu ve ilgili Satın Alma Siparişi (PO) otomatik güncellenerek üretim ve finans modüllerine anlık bildirim düşmelidir.

### 4.4 Quality Control & Rework (Kalite Kontrol & Yeniden İşlem)
* **REQ-008 (Mandatory Quality Control Gate):** Üretimi tamamlanan ürünler, sistemde Kalite Kontrol (QC) Onayı almadan sevkiyat deposuna aktarılamamalı ve sevkiyat irsaliyesine/listesine eklenememelidir.
* **REQ-009 (Automated Rework Order Generation):** Kalite kontrol aşamasında tespit edilen hatalar için sistemde otomatik Rötuş/Yeniden İşlem (Rework) İş Emri oluşmalı ve hata kategorisi (kumaş defosu, ölçü hatası, çizik vb.) kaydedilebilmelidir.

### 4.5 Logistics & Delivery Management (Lojistik & Sevkiyat)
* **REQ-010 (Route & Capacity Optimization):** Sevkiyat planlaması; sistemdeki teslimat adresi, bölge/rota optimizasyon kuralları ve araç kapasiteleri (desi/hacim) dikkate alınarak otomatik sevkiyat rotası ve zaman çizelgesi üzerinden yapılmalıdır.

### 4.6 Finance, Invoicing & Costing (Finans, Faturalandırma & Maliyetleme)
* **REQ-005 (Automated Billing via Delivery):** Sevkiyat gerçekleştiğinde sistem otomatik olarak Satış Faturası taslağı oluşturmalı ve Finance modülüne cari alacak kaydı düşmelidir.
* **REQ-012 (Advance Payment Matching & Actual Costing):** Müşteriden alınan ön ödemeler (kapora) ilgili Satış Siparişi (SO) ile doğrudan eşleştirilmeli; sistem, kullanılan hammadde ve işçilik giderlerine göre ürünün Fiili Maliyetini (Actual Cost) hesaplayıp sipariş bazlı kârlılık raporlayabilmelidir.

---

## 5. System Sign-off & Acceptance Criteria

İşbu FRD dokümanındaki 12 fonksiyonel gereksinim, Kullanıcı Kabul Testlerinde (UAT) başarıyla doğrulandığı takdirde sistem konfigürasyonu tamamlanmış kabul edilecektir.

| Role | Name | Title | Status | Date |
| :--- | :--- | :--- | :--- | :--- |
| **Client Sign-off** | Ahmet Yılmaz | Operations Director (COO) | Approved | 03.10.2026 |
| **Lead Analyst** | [Adın Soyadın] | Senior ERP Implementation Consultant | Approved | 03.10.2026 |
