# Customer Tracker - User Flows (MVP)

**Proje:** customer-tracker  
**Versiyon:** 1.0 (MVP)

---

## 1. Ana Kullanıcı Akışları

### 1.1. Yeni Müşteri + Proje + Fatura Oluşturma Akışı (En Sık Kullanılacak Akış)

1. Kullanıcı Müşteri Listesi sayfasına gider.
2. “Yeni Müşteri” butonuna tıklar.
3. Müşteri bilgilerini doldurur ve kaydeder.
4. Müşteri Detay sayfasına yönlendirilir.
5. “Yeni Proje” butonuna tıklar.
6. Proje bilgilerini doldurur (durum varsayılan: Planlama) ve kaydeder.
7. Proje Detay sayfasına yönlendirilir.
8. “Sözleşme Ekle” ile sözleşme bilgilerini girer (opsiyonel).
9. “Fatura Ekle” ile fatura oluşturur.
10. İhtiyaç halinde faturaya “Ödeme Ekle” yapar.
11. Proje Detay sayfasında kalan alacak otomatik hesaplanır.

---

### 1.2. Mevcut Projeyi Güncelleme Akışı

1. Kullanıcı Proje Listesi veya Müşteri Detay üzerinden ilgili projeye girer.
2. Proje Detay sayfasında:
   - Durumu günceller
   - Yeni not ekler
   - Yeni fatura veya ödeme ekler
   - Sözleşme bilgilerini günceller
3. Değişiklikler anında yansır ve kalan alacak yeniden hesaplanır.

---

### 1.3. Müşteri Bazlı Finansal Kontrol Akışı

1. Kullanıcı Müşteri Listesi’nden ilgili müşteriyi seçer.
2. Müşteri Detay sayfasında şu özetleri görür:
   - Toplam Kalan Alacak
   - Devam Eden Proje Sayısı
   - Açık Fatura Sayısı
3. İlgili projelere tıklayarak detaya inebilir.

---

### 1.4. Proje Durumu Takip Akışı (“Nerede Kaldık?”)

1. Kullanıcı Proje Listesi’nde durum filtresi uygular (örbeğin “Devam Ediyor”).
2. İlgili projenin detayına girer.
3. Notlar bölümünden son gelişmeleri okur.
4. Gerekirse yeni not ekler veya durumu günceller.

---

## 2. Ekran Geçişleri (Basit Site Map)

Müşteri Listesi
│
├── Yeni Müşteri
│
└── Müşteri Detay
│
├── Yeni Proje
│
└── Proje Detay
│
├── Sözleşme Ekle / Düzenle
├── Fatura Ekle / Düzenle
│         └── Ödeme Ekle
└── Not Ekle


---

## 3. Proje Detay

Proje Detay ekranında şu bölümler bulunmalıdır:

- Proje Özet Bilgileri (ad, durum, tarihler)
- Finansal Özet Kutusu (Toplam Fatura, Toplam Ödeme, Kalan Alacak)
- Sözleşmeler Listesi
- Faturalar Listesi (her faturanın altında ödemeleri)
- Notlar / Aktivite Chronology

---

## 4. Hata ve Engelleme Akışları

| Durum | Sistem Davranışı |
|-------|------------------|
| Müşteri silinmek istenirse ve bağlı proje varsa | Silme engellenir, uyarı gösterilir |
| Ödeme tutarı fatura kalan tutarını aşarsa | Kayıt engellenir, uyarı gösterilir |
| Zorunlu alanlar boş bırakılırsa | Form kaydedilmez, eksik alanlar belirtilir |
| Bitiş tarihi başlangıç tarihinden önce girilirse | Kayıt engellenir |

---

## 5. Başarı Kriteri (Akış Bazlı)

Kullanıcı aşağıdaki akışı **3 dakikadan kısa** sürede tamamlayabilmelidir:

> Yeni Müşteri oluştur → Proje ekle → Fatura ekle → Ödeme ekle → Kalan alacağı gör
