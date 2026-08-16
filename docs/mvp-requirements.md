# Customer Tracker - MVP Requirements (Faz 1)

**Proje Adı:** customer-tracker  
**Versiyon:** 1.0 (MVP)  
**Hazırlayan:** İş Analisti bakış açısıyla  
**Tarih:** 2025

---

## 1. Proje Özeti

### Amaç
Küçük ölçekli freelance çalışanlar, ajanslar veya bireysel iş yapanların; müşteri, proje, sözleşme, fatura ve ödeme bilgilerini tek bir yerden takip edebilmesini sağlamak.

### Problem
Bilgilerin Excel, WhatsApp, e-posta ve klasörler arasında dağınık olması nedeniyle şu sorulara hızlı cevap verilememesi:
- Bu müşteriden ne kadar alacağım var?
- Bu projede sözleşmeler ve faturalar ne durumda?
- Proje neredeyse nerede?

### Çözüm
Basit, odaklı ve anlaşılır bir müşteri + proje + sözleşme + fatura + ödeme takip sistemi.

---

## 2. Kapsam

### 2.1. Dahil Olanlar (In Scope)

| Modül               | Açıklama                                      |
|---------------------|-----------------------------------------------|
| Müşteri Yönetimi    | Müşteri ekleme, görüntüleme, düzenleme, listeleme |
| Proje Yönetimi      | Projeyi müşteriye bağlama, durum takibi       |
| Sözleşme Yönetimi   | Projeye sözleşme kaydı                        |
| Fatura Yönetimi     | Projeye fatura ekleme ve durum takibi         |
| Ödeme Yönetimi      | Faturaya ödeme kaydetme                       |
| Not / Aktivite      | Proje bazlı serbest not tutma                 |
| Finansal Özet       | Proje ve müşteri bazında kalan alacak hesaplama |

### 2.2. Dahil Olmayanlar (Out of Scope)

- Kullanıcı girişi ve yetkilendirme
- Dosya yükleme (sadece link tutulacak)
- Teklif / teklif aşaması yönetimi
- Görev ve iş kalemi takibi
- Zaman kaydı (timesheet)
- Otomatik bildirim ve e-posta
- Detaylı raporlama ve grafikler
- Mobil uygulama
- Çoklu şirket / çoklu kullanıcı desteği
- Para birimi kur dönüşümü

---

## 3. Kullanıcı Personası

**Tek Kullanıcı**  
Sistemi kullanan kişi (freelance, küçük ajans sahibi veya bireysel işletme sahibi).  
MVP kapsamında giriş sistemi bulunmamaktadır.

---

## 4. Temel Varlıklar ve İlişkiler

Müşteri (1) ──────── (N) Proje
│
├── (N) Sözleşme
├── (N) Fatura
│         └── (N) Ödeme
└── (N) Not / Aktivite


---

## 5. Kullanıcı Hikâyeleri (User Stories)

### 5.1. Müşteri Yönetimi

**US-01**  
Bir kullanıcı olarak yeni müşteri ekleyebilmek istiyorum, böylece projelerimi bir müşteriye bağlayabilirim.

**US-02**  
Bir kullanıcı olarak mevcut müşterileri listeleyebilmek ve arayabilmek istiyorum.

**US-03**  
Bir kullanıcı olarak müşteri bilgilerini görüntüleyebilmek ve güncelleyebilmek istiyorum.

**US-04**  
Bir kullanıcı olarak bir müşteriyi silebilmek istiyorum (sadece bağlı projesi yoksa).

### 5.2. Proje Yönetimi

**US-05**  
Bir kullanıcı olarak bir müşteriye yeni proje ekleyebilmek istiyorum.

**US-06**  
Bir kullanıcı olarak proje durumunu güncelleyebilmek istiyorum  
(Planlama / Devam Ediyor / Beklemede / Tamamlandı / İptal).

**US-07**  
Bir kullanıcı olarak proje detayını görüntülediğimde; sözleşmeleri, faturaları, ödemeleri ve kalan alacağı tek bakışta görebilmek istiyorum.

**US-08**  
Bir kullanıcı olarak projelere filtre uygulayabilmek istiyorum (duruma göre).

### 5.3. Sözleşme Yönetimi

**US-09**  
Bir kullanıcı olarak bir projeye sözleşme bilgisi ekleyebilmek istiyorum (tarih, tutar, dosya linki).

**US-10**  
Bir kullanıcı olarak mevcut sözleşmeleri görüntüleyebilmek ve düzenleyebilmek istiyorum.

### 5.4. Fatura & Ödeme Yönetimi

**US-11**  
Bir kullanıcı olarak bir projeye fatura ekleyebilmek istiyorum.

**US-12**  
Bir kullanıcı olarak faturanın durumunu güncelleyebilmek istiyorum (Ödenmedi / Kısmi Ödendi / Ödendi).

**US-13**  
Bir kullanıcı olarak bir faturaya ödeme kaydedebilmek istiyorum.

**US-14**  
Bir kullanıcı olarak proje bazında “Toplam Faturalandırılan – Toplam Ödenen = Kalan Alacak” bilgisini görebilmek istiyorum.

**US-15**  
Bir kullanıcı olarak müşteri bazında toplam kalan alacağı görebilmek istiyorum.

### 5.5. Not / Aktivite

**US-16**  
Bir kullanıcı olarak bir projeye not ekleyebilmek istiyorum, böylece “nerede kaldık?” sorusuna cevap verebilirim.

---

## 6. Fonksiyonel Gereksinimler

### 6.1. Müşteri
- CRUD işlemleri desteklenmelidir.
- Silme kuralı: Bağlı proje varsa müşteri silinemez.
- Listeleme ve isme göre basit arama yapılabilmelidir.

### 6.2. Proje
- Her proje mutlaka bir müşteriye bağlı olmalıdır.
- Durum alanı zorunludur ve önceden tanımlı değerlerden seçilmelidir.
- Proje detay sayfasında finansal özet gösterilmelidir.

### 6.3. Sözleşme
- Bir projeye birden fazla sözleşme eklenebilmelidir.
- Dosya linki opsiyoneldir.

### 6.4. Fatura
- Fatura bir projeye bağlıdır.
- Varsayılan durum “Ödenmedi” olmalıdır.
- Fatura tutarı zorunludur.

### 6.5. Ödeme
- Ödeme mutlaka bir faturaya bağlı olmalıdır.
- Ödeme tutarı, ilgili faturanın kalan tutarından fazla olamaz.

### 6.6. Hesaplamalar
- **Proje Kalan Alacak** = Toplam Fatura Tutarı – Toplam Ödeme Tutarı
- **Müşteri Kalan Alacak** = O müşteriye ait tüm projelerin kalan alacakları toplamı

---

## 7. İş Kuralları (Business Rules)

| Kod   | Kural                                                                 |
|-------|-----------------------------------------------------------------------|
| BR-01 | Her proje mutlaka bir müşteriye bağlı olmalıdır.                      |
| BR-02 | Fatura silindiğinde, o faturaya bağlı tüm ödemeler de silinir.        |
| BR-03 | Ödeme tutarı, faturanın kalan tutarından büyük olamaz.                |
| BR-04 | Proje durumu sadece tanımlı değerlerden seçilebilir.                  |
| BR-05 | Müşteri silinmek istendiğinde bağlı proje varsa işlem engellenir.     |
| BR-06 | Tüm tutarlar pozitif sayı olmalıdır.                                  |
| BR-07 | Bitiş tarihi, başlangıç tarihinden önce olamaz.                       |

---

## 8. Ekran Listesi

1. Müşteri Listesi
2. Müşteri Oluşturma / Düzenleme
3. Müşteri Detay (projeler + toplam kalan alacak)
4. Proje Listesi (duruma göre filtreli)
5. Proje Oluşturma / Düzenleme
6. Proje Detay (en kritik ekran)
   - Sözleşmeler
   - Faturalar + Ödemeler
   - Kalan Alacak özeti
   - Notlar
7. Sözleşme Ekleme / Düzenleme
8. Fatura Ekleme / Düzenleme
9. Ödeme Ekleme

---

## 9. Kabul Kriterleri (Definition of Done)

Aşağıdaki maddelerin tamamı sağlandığında MVP tamamlanmış kabul edilir:

- [ ] Müşteri CRUD işlemleri çalışıyor
- [ ] Projeyi müşteriye bağlayıp durum güncelleyebiliyorum
- [ ] Projeye sözleşme, fatura ve ödeme ekleyebiliyorum
- [ ] Proje detayında kalan alacak doğru hesaplanıyor
- [ ] Müşteri detayında toplam kalan alacak doğru görünüyor
- [ ] Not ekleyebiliyorum
- [ ] Temel iş kuralları uygulanıyor
- [ ] Uygulama stabil ve anlaşılır şekilde çalışıyor

---

## 10. Başarı Metrikleri

- Kullanıcı “Bu projede durum ne?” sorusuna 30 saniye içinde cevap alabilmeli
- Kullanıcı “Bu müşteriden ne kadar alacağım var?” sorusuna tek bakışta cevap alabilmeli
- Yeni müşteri + proje + fatura akışı 3 dakikadan kısa sürede tamamlanabilmeli

---

## 11. Sonraki Fazlar için Notlar (Out of Scope - Gelecek)

- Kullanıcı girişi ve yetkilendirme
- Dosya yükleme
- Teklif yönetimi
- Görev / iş kalemi takibi
- Bildirimler
- Gelişmiş raporlama
