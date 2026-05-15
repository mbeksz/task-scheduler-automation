# Görev Zamanlayıcı ve Sözleşme Hatırlatıcı

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white" />
  <img src="https://img.shields.io/badge/PDF%20Processing-FF0000?style=for-the-badge&logo=adobeacrobatreader&logoColor=white" />
  <img src="https://img.shields.io/badge/SMTP-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Durum-Canlıda-brightgreen?style=flat-square" />
  <img src="https://img.shields.io/badge/Tür-Özel%20Kurumsal%20Yazılım-blue?style=flat-square" />
</p>

---

> Bu proje bir otomotiv bayilik grubu için özel kurumsal yazılım olarak geliştirilmiştir.
> Bu repo yalnızca proje yapısını ve dokümantasyonu **portfolyo amaçlı** paylaşmaktadır. Kaynak kod dahil edilmemiştir.

---

## Genel Bakış

İki ayrı otomasyon modülünü barındıran Python tabanlı sistem:

**1. Görev Zamanlayıcı:** Personel verisi senkronizasyonu, fatura aktarımı, takas oranları güncelleme ve sözleşme hatırlatmaları gibi rutin iş süreçlerini tanımlı saatlerde otomatik tetikler. Hata durumunda her görevi üç kez yeniden dener.

**2. Yapay Zeka Sözleşme Hatırlatıcı:** Yüklenen sözleşme PDF'lerini arşivler; yapay zeka ile taraflar, konu ve son geçerlilik tarihini otomatik çıkarır. Belirlenen tarihte ilgili kişilere otomatik e-posta gönderir.

---

## Teknoloji Yığını

```
Zamanlayıcı  → Python · APScheduler / cron
Yapay Zeka   → OpenAI API (görüntü + metin işleme)
PDF İşleme   → PyMuPDF / pdfplumber
Veritabanı   → MSSQL
Bildirim     → SMTP (e-posta)
```

---

## Mimari

```
scheduler.py             # Ana zamanlayıcı servisi
contract.py              # Sözleşme AI okuma ve hatırlatma modülü

uyumsoft_personel/       # ERP personel senkronizasyon görevleri
logo_fatura/             # Logo fatura senkronizasyon görevleri
takas_oranlari/          # Takas oranı güncelleme görevleri
contract/                # Sözleşme arşivi ve işleme

requirements.txt
```

---

## Temel Özellikler

**Zamanlayıcı:**
- Tanımlı saatlerde otomatik görev tetikleme
- Başarısız görevler için 3 deneme mekanizması
- Hata loglama ve bildirim

**Sözleşme Hatırlatıcı:**
- PDF'den yapay zeka ile taraf, konu ve tarih çıkarma
- Sözleşme arşivi ve veritabanı kaydı
- Belirlenen hatırlatma tarihinde otomatik e-posta gönderimi
- Sözleşme yenileme süreçlerinin gözden kaçmasını engeller
