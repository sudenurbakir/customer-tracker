# Jira Setup

Bu dokümanda Customer Tracker projesi için Jira Kanban board kurulum adımları yer alır.

## 1. Proje Oluşturma

1. Jira’ya giriş yap
2. **Projects** → **Create project**
3. Şablon olarak **Kanban** seç
4. Proje bilgilerini gir:
   - Project name: `Customer Tracker`
   - Project key: `CT` (veya istediğin kısa kod)
5. **Create** butonuna tıkla

## 2. Board Yapısı

Varsayılan sütunlar kullanılacaktır:

| Sütun         | Açıklama                        |
|---------------|---------------------------------|
| To Do         | Yapılacak işler                 |
| In Progress   | Üzerinde çalışılan işler        |
| Done          | Tamamlanan işler                |

## 3. Temel Ayarlar

- Issue type olarak şimdilik sadece **Task** kullanılacak
- WIP (Work In Progress) limiti: In Progress sütunu için **3**
- Öncelik alanını aktif tut (Highest, High, Medium, Low, Lowest)

## 4. İlk İşlerin Eklenmesi

Board’a ilk etapta şu tarz işler eklenebilir:

- Proje yapısını netleştir
- Müşteri modeli oluştur
- Proje modeli oluştur
- Fatura ve ödeme yapısını kur
- Basit arayüz iskeleti hazırla

## 5. Metrikler

Geliştirme başladığında şu raporlar takip edilecek:

- Control Chart (Cycle Time)
- Cumulative Flow Diagram
- Average Age Report

## 6. Kurallar

- Aynı anda In Progress’te en fazla 3 iş olacak
- Bir iş bitmeden yeni işe başlanmayacak (mümkün olduğunca)
- İşler küçük ve net tanımlanacak
