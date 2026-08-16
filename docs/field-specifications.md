# Customer Tracker - Alan Bazlı Detaylar (MVP)

**Proje:** customer-tracker  
**Versiyon:** 1.0 (MVP)

---

## 1. Müşteri

| Alan Adı          | Zorunlu | Tip          | Açıklama / Kural                          |
|-------------------|-------|--------------|-------------------------------------------|
| id                | Evet  | UUID / Int   | Sistem tarafından oluşturulur             |
| name              | Evet  | Text         | Müşteri adı veya ünvan                    |
| contact_person    | Hayır | Text         | Yetkili kişi                              |
| phone             | Hayır | Text         | Telefon                                   |
| email             | Hayır | Email        | E-posta                                   |
| address           | Hayır | Text         | Adres                                     |
| notes             | Hayır | Long Text    | Serbest not                               |
| created_at        | Evet  | DateTime     | Sistem tarafından oluşturulur             |
| updated_at        | Evet  | DateTime     | Sistem tarafından güncellenir             |

**Kurallar:**
- `name` boş olamaz.
- Silme işlemi ancak bağlı proje yoksa yapılabilir.

---

## 2. Proje

| Alan Adı          | Zorunlu | Tip          | Açıklama / Kural                          |
|-------------------|-------|--------------|-------------------------------------------|
| id                | Evet  | UUID / Int   | Sistem tarafından oluşturulur             |
| customer_id       | Evet  | FK           | Bağlı müşteri                             |
| name              | Evet  | Text         | Proje adı                                 |
| status            | Evet  | Enum         | Planlama / Devam Ediyor / Beklemede / Tamamlandı / İptal |
| start_date        | Hayır | Date         | Başlangıç tarihi                          |
| end_date          | Hayır | Date         | Bitiş tarihi                              |
| description       | Hayır | Long Text    | Açıklama                                  |
| created_at        | Evet  | DateTime     | Sistem tarafından oluşturulur             |
| updated_at        | Evet  | DateTime     | Sistem tarafından güncellenir             |

**Kurallar:**
- `customer_id` zorunludur.
- `status` varsayılan değeri: `Planlama`
- `end_date`, `start_date` değerinden önce olamaz.

---

## 3. Sözleşme

| Alan Adı          | Zorunlu | Tip          | Açıklama / Kural                          |
|-------------------|-------|--------------|-------------------------------------------|
| id                | Evet  | UUID / Int   | Sistem tarafından oluşturulur             |
| project_id        | Evet  | FK           | Bağlı proje                               |
| title             | Evet  | Text         | Sözleşme adı veya numarası                |
| start_date        | Hayır | Date         | Başlangıç tarihi                          |
| end_date          | Hayır | Date         | Bitiş tarihi                              |
| amount            | Hayır | Decimal      | Sözleşme tutarı                           |
| currency          | Hayır | Enum         | TRY / USD / EUR (varsayılan: TRY)         |
| file_link         | Hayır | URL          | Dosya linki (Google Drive, Dropbox vb.)   |
| notes             | Hayır | Long Text    | Not                                       |
| created_at        | Evet  | DateTime     | Sistem tarafından oluşturulur             |

**Kurallar:**
- `end_date`, `start_date` değerinden önce olamaz.
- `amount` girilmişse 0’dan büyük olmalıdır.

---

## 4. Fatura

| Alan Adı          | Zorunlu | Tip          | Açıklama / Kural                          |
|-------------------|-------|--------------|-------------------------------------------|
| id                | Evet  | UUID / Int   | Sistem tarafından oluşturulur             |
| project_id        | Evet  | FK           | Bağlı proje                               |
| invoice_number    | Evet  | Text         | Fatura numarası                           |
| invoice_date      | Evet  | Date         | Fatura tarihi                             |
| amount            | Evet  | Decimal      | Fatura tutarı                             |
| currency          | Evet  | Enum         | TRY / USD / EUR (varsayılan: TRY)         |
| status            | Evet  | Enum         | Ödenmedi / Kısmi Ödendi / Ödendi          |
| description       | Hayır | Long Text    | Açıklama                                  |
| created_at        | Evet  | DateTime     | Sistem tarafından oluşturulur             |

**Kurallar:**
- `amount` 0’dan büyük olmalıdır.
- Varsayılan `status`: `Ödenmedi`
- Fatura silindiğinde bağlı ödemeler de silinir.

---

## 5. Ödeme

| Alan Adı          | Zorunlu | Tip          | Açıklama / Kural                          |
|-------------------|-------|--------------|-------------------------------------------|
| id                | Evet  | UUID / Int   | Sistem tarafından oluşturulur             |
| invoice_id        | Evet  | FK           | Bağlı fatura                              |
| payment_date      | Evet  | Date         | Ödeme tarihi                              |
| amount            | Evet  | Decimal      | Ödenen tutar                              |
| payment_method    | Hayır | Enum         | Havale / Nakit / Kredi Kartı / Diğer      |
| notes             | Hayır | Long Text    | Açıklama                                  |
| created_at        | Evet  | DateTime     | Sistem tarafından oluşturulur             |

**Kurallar:**
- `amount` 0’dan büyük olmalıdır.
- `amount`, bağlı faturanın kalan tutarından büyük olamaz.
- Kalan tutar = Fatura Tutarı – Daha önceki ödemeler toplamı

---

## 6. Not / Aktivite

| Alan Adı          | Zorunlu | Tip          | Açıklama / Kural                          |
|-------------------|-------|--------------|-------------------------------------------|
| id                | Evet  | UUID / Int   | Sistem tarafından oluşturulur             |
| project_id        | Evet  | FK           | Bağlı proje                               |
| content           | Evet  | Long Text    | Not içeriği                               |
| created_at        | Evet  | DateTime     | Sistem tarafından oluşturulur             |

**Kurallar:**
- `content` boş olamaz.

---

## 7. Hesaplanan Alanlar (Veritabanında Tutulmaz)

| Alan                      | Hesaplama Şekli                                      |
|---------------------------|------------------------------------------------------|
| Proje Toplam Fatura       | SUM(fatura.amount) where project_id = X             |
| Proje Toplam Ödeme        | SUM(ödeme.amount) where ilgili faturalar             |
| Proje Kalan Alacak        | Toplam Fatura – Toplam Ödeme                         |
| Müşteri Kalan Alacak      | SUM(proje kalan alacak) where customer_id = X        |
| Müşteri Açık Fatura Sayısı| COUNT(fatura) where status != Ödendi                 |

---

## 8. Enum Değerleri

**Proje Durumu**
- Planlama
- Devam Ediyor
- Beklemede
- Tamamlandı
- İptal

**Fatura Durumu**
- Ödenmedi
- Kısmi Ödendi
- Ödendi

**Para Birimi**
- TRY
- USD
- EUR

**Ödeme Yöntemi**
- Havale
- Nakit
- Kredi Kartı
- Diğer
