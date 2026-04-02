# 🏠 KasaDefteri — Android Native App

**Ev Kasa Defteri** | Kotlin + Jetpack Compose + MVVM + Room

---

## 📁 Proje Yapısı

```
KasaDefteri/
├── app/src/main/java/com/kasadefteri/
│   ├── MainActivity.kt              ← Giriş noktası + Hilt
│   ├── data/
│   │   ├── local/
│   │   │   ├── dao/Daos.kt          ← Room DAO'ları
│   │   │   ├── entity/Entities.kt   ← Room Entity + Mapper + TypeConverter
│   │   │   └── database/KasaDatabase.kt
│   │   └── repository/KasaRepository.kt
│   ├── domain/
│   │   ├── model/Models.kt          ← Domain modeller + Enum'lar
│   │   └── usecase/UseCases.kt      ← İş mantığı
│   ├── di/
│   │   └── DatabaseModule.kt        ← Hilt DI
│   └── ui/
│       ├── theme/Theme.kt           ← Material3 tema + renkler
│       ├── navigation/Navigation.kt ← NavHost + Bottom Nav
│       ├── components/
│       │   ├── Components.kt        ← Paylaşılan UI bileşenler
│       │   └── AddTransactionSheet.kt ← İşlem ekleme modal
│       └── screens/
│           ├── home/                ← HomeScreen + HomeViewModel
│           ├── kasa/                ← KasaScreen + KasaViewModel
│           ├── transactions/        ← TransactionScreen + TransactionViewModel
│           ├── reports/             ← ReportScreen + ReportViewModel
│           └── settings/            ← SettingsScreen
└── gradle/libs.versions.toml        ← Version catalog
```

---

## 🚀 Android Studio'da Kurulum

### 1. Projeyi Aç
```
File → Open → KasaDefteri klasörünü seç
```

### 2. Gradle Sync
Android Studio otomatik sync başlatır. Tamamlanmasını bekle.

### 3. Çalıştır
- Emülatör veya fiziksel cihaz bağla (minSdk 26 = Android 8.0+)
- Run (▶) butonuna bas

---

## 🏗️ Mimari

```
UI Layer (Compose Screens)
     ↓ collectAsStateWithLifecycle
ViewModel (StateFlow + SharedFlow)
     ↓ inject
Use Cases (domain logic)
     ↓ inject
Repository (single source of truth)
     ↓
Room DAO ←→ SQLite Database
```

### State Yönetimi
- `StateFlow` → ekran durumu (UI render)
- `SharedFlow` → tek seferlik olaylar (snackbar, navigation)
- `collectAsStateWithLifecycle` → lifecycle-aware collect

---

## 📱 Ekranlar

| Ekran | Özellikler |
|-------|-----------|
| **Ana Sayfa** | Bakiye kartı, hızlı kayıt, yaklaşan ödemeler, bütçe çubukları, son işlemler |
| **Kasa** | Günlük açılış/kapanış, gün navigasyonu, hareket listesi |
| **İşlemler** | Arama, filtre chipleri, tarih gruplu liste, silme |
| **Raporlar** | Aylık özet, kategori dağılımı, sabit giderler yönetimi |
| **Ayarlar** | Tema, bildirimler, dışa aktarım, kategori yönetimi |

---

## ⚡ Özellikler

### Hızlı Metin Girişi
Ana sayfada metin alanına yaz:
- `250 market` → Gider, Market kategorisi, 250₺
- `2000 maaş` → Gelir, 2000₺
- `90 elektrik faturası` → Gider, Fatura kategorisi

### Kategori Sistemi
Market · Fatura · Kira · Aidat · Ulaşım · Sağlık · Mutfak · Temizlik · Ev İhtiyacı · Borç · Diğer

### Ödeme Yöntemleri
Nakit · Banka · Kredi Kartı · Havale/EFT · Diğer

---

## 📦 Bağımlılıklar

| Kütüphane | Versiyon | Amaç |
|-----------|----------|------|
| Jetpack Compose BOM | 2024.09.03 | UI framework |
| Material 3 | BOM'dan | Design system |
| Navigation Compose | 2.8.2 | Ekran geçişleri |
| Hilt | 2.51.1 | Dependency injection |
| Room | 2.6.1 | Local database |
| Lifecycle | 2.8.6 | ViewModel + StateFlow |
| Coroutines | 1.8.1 | Async işlemler |

---

## 🔮 Sonraki Sürümler (Modüler Yapıda Hazır)

- [ ] Sesle gider ekleme (SpeechRecognizer)
- [ ] Fiş fotoğrafından OCR (ML Kit)
- [ ] Widget desteği (Glance API)
- [ ] PDF rapor export (iTextPDF)
- [ ] Excel export (Apache POI)
- [ ] Bulut yedekleme (Firebase)
- [ ] Aile paylaşımı (multi-user)

---

## 📛 Uygulama İsim Önerileri

| İsim | Açıklama |
|------|----------|
| **KasaDefteri** | Net, akılda kalıcı, Türkçe |
| **EvMizan** | Mizan = denge/hesap, şiirsel |
| **HaneBütçe** | Hane = ev, bütçe = hedefli |

---

*minSdk 26 (Android 8.0+) · targetSdk 35 · Kotlin 2.0 · Compose BOM 2024.09*
