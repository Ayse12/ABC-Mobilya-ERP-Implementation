# REQ-010: Lojistik ve Sevkiyat Yönetimi Konfigürasyonu

## Genel Bakış
Bu doküman, ABC Mobilya projesi kapsamında Odoo ERP üzerinde kurgulanan Lojistik ve Sevkiyat sürecinin sistem konfigürasyonunu ve operasyonel işleyiş mantığını tanımlar.

## Süreç İş Akışı
1. **Sipariş Serbest Bırakma:** REQ-008 Kalite Kontrol aşamasından geçen ürünler sevkiyat alanına (`WH/Output`) aktarılır.
2. **Sevkiyat Emri (WH/OUT):** Satış veya dahili transfer işlemlerinin tamamlanmasıyla birlikte otomatik olarak toplama ve paketleme listeleri oluşturulur.
3. **Stok Düşüşü:** Giden sevkiyatın doğrulanması ve onaylanmasıyla birlikte envanter stok miktarları gerçek zamanlı olarak düşürülür.

## Doğrulama ve Kanıt
* **Ekran Görüntüsü Referansı:** `03_Testing_&_Simulation/screenshots/07_Logistics_&_Dispatch.png`
* **Durum:** Yapılandırıldı ve Doğrulandı
