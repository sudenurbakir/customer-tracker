# Customer Tracker - Kabul Kriterleri (Test Edilebilir)

**Proje:** customer-tracker  
**Versiyon:** 1.0 (MVP)  
**Amaç:** Her kriterin net, ölçülebilir ve test edilebilir olması

---

## 1. Müşteri Yönetimi

### AC-01: Yeni Müşteri Oluşturma
**Verilen:** Kullanıcı Müşteri Listesi sayfasındadır  
**Ne zaman:** “Yeni Müşteri” butonuna tıklar ve zorunlu alanları doldurup kaydeder  
**O zaman:**
- Müşteri başarıyla oluşturulur
- Müşteri Listesi’nde görünür
- Müşteri Detay sayfasına yönlendirilir

**Test Adımları:**
1. Müşteri Listesi’ne git
2. “Yeni Müşteri” butonuna tıkla
3. Sadece “name” alanını doldur, diğerlerini boş bırak
4. Kaydet
5. Müşterinin listede göründüğünü ve detay sayfasının açıldığını doğrula

---

### AC-02: Müşteri Silme Engeli
**Verilen:** Bir müşteriye bağlı en az bir proje vardır  
**Ne zaman:** Kullanıcı o müşteriyi silmeye çalışır  
**O zaman:**
- Silme işlemi engellenir
- Kullanıcıya anlamlı bir uyarı mesajı gösterilir

**Test Adımları:**
1. Projesi olan bir müşteri seç
2. Sil butonuna tıkla
3. İşlemin gerçekleşmediğini ve uyarı mesajı çıktığını doğrula

---

### AC-03: Müşteri Arama
**Verilen:** Sistemde birden fazla müşteri vardır  
**Ne zaman:** Kullanıcı isme göre arama yapar  
**O zaman:**
- Sadece eşleşen müşteriler listelenir

**Test Adımları:**
1. En az 3 farklı isimde müşteri oluştur
2. Arama kutusuna bir müşteri adının bir kısmını yaz
3. Sadece ilgili müşterinin geldiğini doğrula

---

## 2. Proje Yönetimi

### AC-04: Projeyi Müşteriye Bağlama
**Verilen:** En az bir müşteri mevcuttur  
**Ne zaman:** Kullanıcı yeni proje oluştururken müşteri seçer  
**O zaman:**
- Proje seçilen müşteriye bağlanır
- Müşteri Detay sayfasında proje görünür

**Test Adımları:**
1. Bir müşteri oluştur
2. O müşteriye yeni proje ekle
3. Müşteri Detay’da projenin listelendiğini doğrula

---

### AC-05: Proje Durumu Güncelleme
**Verilen:** Bir proje mevcuttur  
**Ne zaman:** Kullanıcı proje durumunu değiştirir  
**O zaman:**
- Yeni durum kaydedilir
- Proje Listesi ve Proje Detay’da güncel durum görünür

**Test Adımları:**
1. Bir proje oluştur (varsayılan: Planlama)
2. Durumu “Devam Ediyor” olarak değiştir
3. Hem liste hem detay sayfasında durumun güncellendiğini doğrula

---

### AC-06: Proje Tarih Kontrolü
**Verilen:** Kullanıcı proje oluşturuyor veya güncelliyor  
**Ne zaman:** Bitiş tarihi, başlangıç tarihinden önce girilir  
**O zaman:**
- Kayıt engellenir
- Kullanıcıya hata mesajı gösterilir

**Test Adımları:**
1. Yeni proje formunu aç
2. Başlangıç tarihi: 2025-05-10
3. Bitiş tarihi: 2025-05-01 gir
4. Kaydetmeye çalış
5. Hata mesajı aldığını ve kaydın oluşmadığını doğrula

---

## 3. Sözleşme Yönetimi

### AC-07: Sözleşme Ekleme
**Verilen:** Bir proje mevcuttur  
**Ne zaman:** Kullanıcı projeye sözleşme ekler  
**O zaman:**
- Sözleşme başarıyla kaydedilir
- Proje Detay sayfasında listelenir

**Test Adımları:**
1. Bir proje detayına gir
2. “Sözleşme Ekle” butonuna tıkla
3. Zorunlu alanları doldurup kaydet
4. Sözleşmenin listede göründüğünü doğrula

---

## 4. Fatura & Ödeme Yönetimi

### AC-08: Fatura Oluşturma
**Verilen:** Bir proje mevcuttur  
**Ne zaman:** Kullanıcı fatura ekler  
**O zaman:**
- Fatura “Ödenmedi” durumuyla oluşur
- Proje Detay’da görünür
- Proje kalan alacağı güncellenir

**Test Adımları:**
1. Bir proje detayına gir
2. 10.000 TL tutarında fatura ekle
3. Faturanın “Ödenmedi” olarak göründüğünü doğrula
4. Kalan Alacak’ın 10.000 TL olduğunu doğrula

---

### AC-09: Ödeme Ekleme ve Kalan Alacak Hesabı
**Verilen:** Ödenmemiş bir fatura vardır  
**Ne zaman:** Kullanıcı faturaya ödeme ekler  
**O zaman:**
- Ödeme kaydedilir
- Fatura durumu gerekirse güncellenir
- Proje ve Müşteri kalan alacağı doğru hesaplanır

**Test Adımları:**
1. 10.000 TL’lik bir fatura oluştur
2. 4.000 TL ödeme ekle
3. Kalan Alacak’ın 6.000 TL olduğunu doğrula
4. Fatura durumunun “Kısmi Ödendi” olduğunu doğrula
5. Kalan 6.000 TL’yi de öde
6. Fatura durumunun “Ödendi” ve Kalan Alacak’ın 0 TL olduğunu doğrula

---

### AC-10: Ödeme Tutarı Kontrolü
**Verilen:** Bir faturanın kalan tutarı 5.000 TL’dir  
**Ne zaman:** Kullanıcı 6.000 TL ödeme girmeye çalışır  
**O zaman:**
- Kayıt engellenir
- Kullanıcıya “Ödeme tutarı kalan tutardan fazla olamaz” uyarısı gösterilir

**Test Adımları:**
1. 5.000 TL kalanı olan bir fatura bul
2. 6.000 TL ödeme girmeye çalış
3. İşlemin engellendiğini ve uyarı mesajı çıktığını doğrula

---

### AC-11: Fatura Silindiğinde Ödemelerin Silinmesi
**Verilen:** Bir faturaya bağlı en az bir ödeme vardır  
**Ne zaman:** Kullanıcı faturayı siler  
**O zaman:**
- Fatura ve ona bağlı tüm ödemeler silinir
- Proje kalan alacağı güncellenir

**Test Adımları:**
1. Faturası ve ödemesi olan bir proje seç
2. Faturayı sil
3. Ödemelerin de silindiğini doğrula
4. Kalan Alacak’ın doğru güncellendiğini doğrula

---

## 5. Not / Aktivite

### AC-12: Not Ekleme
**Verilen:** Bir proje mevcuttur  
**Ne zaman:** Kullanıcı not ekler  
**O zaman:**
- Not kaydedilir
- Proje Detay’da tarih sırasına göre görünür

**Test Adımları:**
1. Bir proje detayına gir
2. Yeni not ekle
3. Notun listede göründüğünü doğrula

---

## 6. Finansal Özet

### AC-13: Proje Bazlı Kalan Alacak
**Verilen:** Bir projede birden fazla fatura ve ödeme vardır  
**Ne zaman:** Kullanıcı Proje Detay sayfasını açar  
**O zaman:**
- Toplam Faturalandırılan, Toplam Ödenen ve Kalan Alacak doğru hesaplanır ve gösterilir

**Test Senaryosu:**
- Fatura 1: 10.000 TL
- Fatura 2: 5.000 TL
- Ödeme 1: 3.000 TL (Fatura 1’e)
- Ödeme 2: 2.000 TL (Fatura 2’ye)
- **Beklenen:** Toplam Fatura = 15.000 | Toplam Ödeme = 5.000 | Kalan = 10.000

---

### AC-14: Müşteri Bazlı Kalan Alacak
**Verilen:** Bir müşterinin birden fazla projesi vardır  
**Ne zaman:** Kullanıcı Müşteri Detay sayfasını açar  
**O zaman:**
- Tüm projelerin kalan alacakları toplanarak gösterilir

**Test Senaryosu:**
- Proje A Kalan: 8.000 TL
- Proje B Kalan: 4.500 TL
- **Beklenen Müşteri Kalan Alacak:** 12.500 TL

---

## 7. Genel Kurallar

### AC-15: Zorunlu Alan Kontrolü
**Verilen:** Kullanıcı herhangi bir form dolduruyor  
**Ne zaman:** Zorunlu alanlardan biri boş bırakılır  
**O zaman:**
- Form kaydedilmez
- Eksik alanlar belirtilir

---

### AC-16: Pozitif Tutar Kontrolü
**Verilen:** Kullanıcı tutar giriyor (Fatura, Ödeme, Sözleşme)  
**Ne zaman:** 0 veya negatif değer girer  
**O zaman:**
- Kayıt engellenir
- Uygun hata mesajı gösterilir

---

## 8. MVP Tamamlanma Kriteri

Aşağıdaki tüm maddeler başarıyla geçildiğinde Faz 1 tamamlanmış kabul edilir:

- [ ] AC-01 ile AC-16 arasındaki tüm kriterler test edilmiş ve geçilmiştir
- [ ] Hiçbir kritik iş kuralı ihlal edilmemektedir
- [ ] Proje Detay ekranında finansal özet doğru çalışmaktadır
- [ ] Müşteri Detay ekranında toplam kalan alacak doğru çalışmaktadır
- [ ] Temel kullanıcı akışı (Müşteri → Proje → Fatura → Ödeme) 3 dakikadan kısa sürede tamamlanabilmektedir
