# 📰 News Reader Pro

![Flutter](https://img.shields.io/badge/Flutter-3.32.8-blue)
![Dart](https://img.shields.io/badge/Dart-3.8.1-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20iOS-lightgrey)

A premium Flutter news application that aggregates news from multiple trusted sources with a beautiful, responsive UI and offline support. Built with Clean Architecture and professional state management.

---

## 📋 Deskripsi Proyek

News Reader Pro adalah aplikasi berita modern yang mengumpulkan berita dari 5 sumber API terpercaya. Aplikasi ini dibangun dengan Flutter untuk demonstrasi kemampuan dalam membangun aplikasi produksi dengan arsitektur yang baik, dokumentasi yang lengkap, dan user experience yang optimal.

**Tujuan Pembangunan:**
- Membuktikan kemampuan implementasi Clean Architecture di Flutter
- Menunjukkan pengelolaan state yang efektif dengan Provider
- Membuat UI/UX yang responsif dan menarik
- Menerapkan error handling dan offline support yang robust

**Sumber API:**
1. **GNews API** - Global news dengan update cepat
2. **NewsAPI.org** - 70,000+ sumber berita terpercaya
3. **Currents API** - Berita real-time
4. **NewsData.io** - Multi-language support
5. **Mediastack API** - REST API sederhana

---

## ✨ Fitur-fitur

### 🎯 Fitur Inti
- 📱 **Multi-Source Aggregation** - Otomatis fallback ke API lain jika satu gagal
- 🔍 **Smart Search** - Pencarian real-time di semua sumber berita
- 📂 **Category Filtering** - 7 kategori berita (Business, Technology, Sports, dll)
- 🔖 **Bookmark System** - Penyimpanan lokal dengan SQLite
- 📶 **Offline Reading** - Cache artikel untuk akses tanpa internet
- 🌙 **Dark/Light Mode** - Tema cosmic blue-purple-pink dengan smooth transition
- 📤 **Share Articles** - Berbagi via WhatsApp, Email, Social Media
- 🔄 **Pull to Refresh** - Update data dengan gesture natural
- ⚡ **Error Handling** - Graceful degradation dengan user-friendly messages

### 🎨 UI/UX Excellence
- 📊 **Responsive Grid Layout** - Grid adaptif (1-3 kolom) berdasarkan screen size dengan rasio 4:3
- 🔥 **Hot News Section** - Widget berita trending yang menarik
- 🎨 **Glassmorphism Design** - Modern gradient dan efek transparan
- ✨ **Smooth Animations** - Fade, scale, dan slide transitions
- 📍 **Sticky Navigation** - AppBar tetap terlihat saat scrolling
- 🦶 **Professional Footer** - Lengkap dengan API attribution

### 🔧 Technical Features
- **Clean Architecture** - Separation of concerns yang jelas
- **MVVM Pattern** - Dengan Provider untuk state management
- **Image Caching** - Optimized loading dengan placeholder
- **Dependency Injection** - Untuk testability yang lebih baik

---

## 🚀 Instalasi dan Setup

### Prasyarat

- **Flutter SDK** versi 3.0.0 atau lebih tinggi
- **Dart SDK** versi 2.19.0 atau lebih tinggi
- **IDE**: VS Code atau Android Studio dengan plugin Flutter
- **Device**: Android emulator/iOS simulator atau physical device

### Langkah-langkah Instalasi

1. **Clone repository**
   ```bash
   git clone https://github.com/Nzieraaa/news_reader_pro.git
   cd news_reader_pro
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Run the app**
   ```bash
   flutter run
   ```

### Untuk Platform Spesifik

**Android:**
```bash
flutter run -d android
```

**iOS:**
```bash
flutter run -d ios
```

**Web:**
```bash
flutter run -d chrome
```

---

## 🔑 Konfigurasi API Keys

Aplikasi ini menggunakan 5 API berita. API keys sudah disertakan untuk keperluan demo:

### API yang Dikonfigurasi:
1. **GNews API** - `c162ee64d3d842a9dd66aefe426504ec`
2. **NewsAPI.org** - `dcd530d9f04c4d39adf527c04d3a2d59`
3. **Currents API** - `1f4kxFWKUMBcuAHALrJca9iRdPAjTHETMwdA5i45xID1-6dw`
4. **NewsData.io** - `pub_8a4f8a1c8007448a921d3ede61e0f00b`
5. **Mediastack API** - `119c11c2febc783f983f1dd7faefb235`

### Menggunakan API Keys Sendiri:

1. **Dapatkan API keys gratis dari:**
   - [GNews](https://gnews.io/)
   - [NewsAPI.org](https://newsapi.org/)
   - [Currents API](https://currentsapi.services/)
   - [NewsData.io](https://newsdata.io/)
   - [Mediastack](https://mediastack.com/)

2. **Update file `lib/core/constants/api_constants.dart`:**
   ```dart
   static const String gnewsApiKey = 'YOUR_GNEWS_KEY';
   static const String newsApiKey = 'YOUR_NEWSAPI_KEY';
   static const String currentsApiKey = 'YOUR_CURRENTS_KEY';
   static const String newsdataApiKey = 'YOUR_NEWSDATA_KEY';
   static const String mediastackApiKey = 'YOUR_MEDIASTACK_KEY';
   ```

---

## 🏗️ Arsitektur

Aplikasi ini mengikuti prinsip **Clean Architecture** dengan **MVVM Pattern**:

```
lib/
├── core/                          # Layer inti aplikasi
│   ├── constants/                 # Konstanta aplikasi
│   │   └── api_constants.dart     # API keys dan endpoint
│   ├── exceptions/                # Custom exception classes
│   │   └── app_exceptions.dart    # Exception hierarchy
│   └── theme/                     # Theme dan styling
│       └── app_theme.dart         # Cosmic theme configuration
│
├── data/                          # Layer data (implementasi)
│   ├── datasources/               # Sumber data eksternal
│   │   └── news_api_service.dart  # Service untuk 5 API
│   ├── models/                    # Data models/entities
│   │   ├── news_article.dart      # Model artikel berita
│   │   └── news_response.dart     # Model response API
│   └── repositories/              # Repository implementations
│       └── news_repository_impl.dart
│
├── domain/                        # Layer domain (bisnis logic)
│   ├── entities/                  # Business entities
│   └── repositories/              # Repository interfaces
│       └── news_repository.dart   # Abstract repository
│
└── presentation/                  # Layer presentasi (UI)
    ├── providers/                 # State management
    │   ├── news_provider.dart     # Provider untuk berita
    │   └── theme_provider.dart    # Provider untuk tema
    │
    ├── screens/                   # Halaman aplikasi
    │   ├── home_screen.dart       # Homepage dengan grid
    │   ├── news_detail_screen.dart # Detail artikel
    │   ├── search_screen.dart     # Halaman pencarian
    │   └── bookmarks_screen.dart  # Artikel yang disimpan
    │
    └── widgets/                   # Reusable widgets
        ├── glass_card.dart        # Card dengan efek glassmorphism
        ├── gradient_background.dart # Background dengan gradient
        ├── hot_news_widget.dart   # Widget berita trending
        ├── grid_news_card.dart    # Card untuk grid layout
        └── loading_widget.dart    # Indikator loading custom
```

---

## 📦 Dependencies

### Core Dependencies
```yaml
provider: ^6.1.1              # State management dengan ChangeNotifier
http: ^1.1.0                  # HTTP client untuk API calls
dio: ^5.4.0                   # HTTP client advanced
```

### UI & UX
```yaml
cached_network_image: ^3.3.0  # Image loading dengan caching
shimmer: ^3.0.0               # Shimmer effect untuk loading
pull_to_refresh: ^2.0.0       # Pull to refresh functionality
```

### Storage & Persistence
```yaml
shared_preferences: ^2.2.2    # Simple key-value storage
sqflite: ^2.3.0               # SQLite database untuk bookmarks
path_provider: ^2.1.1         # Filesystem path helpers
```

### Utilities
```yaml
intl: ^0.18.1                 # Internationalization & formatting
url_launcher: ^6.2.1          # Membuka URL di browser
share_plus: ^7.2.1            # Native share functionality
connectivity_plus: ^5.0.2     # Network status monitoring
```

---

## 📸 Screenshots

### Light Mode

| Home Screen | Search Results | Article Detail |
|-------------|----------------|----------------|
| ![Home Screen](Screenshots/home.png) | ![Search Results](Screenshots/Search.png) | ![Article Detail](Screenshots/Article.png) |

### Dark Mode

| Bookmarks | Dark Theme | Smooth Transitions |
|-----------|------------|-------------------|
| ![Bookmarks](Screenshots/Bookmarks.png) | ![Dark Theme](Screenshots/dark.jpeg) | ![Smooth Transitions](Screenshots/Smooth.png) |

### Additional Features

| Gradient Effects |
|------------------|
| ![Gradient Effects](Screenshots/Gradient.png) |

---

## 🎨 Theme

**Cosmic Theme** - Blue, Purple, Pink gradient

- **Primary**: `#4A5BF4` (Deep Blue)
- **Secondary**: `#8B5CF6` (Violet)
- **Accent**: `#EC4899` (Pink)
- **Dark/Light Mode** dengan smooth transitions
- **Glassmorphism effects** untuk modern UI

---

## 🧪 Testing

### Menjalankan Tests
```bash
# Run semua tests
flutter test

# Run tests dengan coverage report
flutter test --coverage

# Run test tertentu
flutter test test/news_provider_test.dart
```

### Test Coverage
- **Unit Tests**: Model, repository, provider
- **Widget Tests**: Screens dan widgets utama
- **Integration Tests**: User flow end-to-end

---

## 📊 Performa & Optimasi

### Load Time Optimization
- **Parallel API Calls**: Mengambil data dari multiple sources secara bersamaan
- **Image Caching**: Menggunakan cached_network_image untuk mengurangi bandwidth
- **Lazy Loading**: Load data saat diperlukan (infinite scroll)

### Memory Management
- **Dispose Resources**: Provider dan controllers di-dispose dengan benar
- **List Pagination**: Membatasi data yang di-load sekaligus
- **Image Compression**: Optimize image loading dengan placeholder

### Offline Capabilities
- **SQLite Storage**: Bookmarks disimpan secara persistent
- **Cache System**: Artikel terakhir di-cache untuk offline reading
- **Network Detection**: Auto-switch ke cache saat offline

---

## 🐛 Known Issues & Limitations

### Platform Specific
- **Web**: Share functionality memiliki keterbatasan di beberapa browser
- **iOS**: Memerlukan konfigurasi `LSApplicationQueriesSchemes` untuk URL launching

### API Limitations
- **Rate Limits**: Free tier APIs memiliki batasan request per hari
- **Data Consistency**: Format response berbeda antar API sources
- **Availability**: Beberapa API mungkin tidak tersedia di region tertentu

### UI/UX Considerations
- **Image Loading**: Beberapa artikel mungkin tidak memiliki gambar
- **Content Length**: Konten artikel mungkin terpotong (preview only)

---

## 🔮 Roadmap & Future Enhancements

### Short-term (v1.1)
- [ ] Notifikasi untuk breaking news
- [ ] Text-to-speech untuk artikel
- [ ] Advanced search filters (date range, language)

### Medium-term (v2.0)
- [ ] User authentication dan personalized feed
- [ ] Social features (komentar, likes)
- [ ] Localization (multi-language support)
- [ ] Unit & Integration Tests yang komprehensif

### Long-term (v3.0)
- [ ] Machine learning untuk rekomendasi artikel
- [ ] Podcast integration
- [ ] Cross-platform desktop support
- [ ] Push notifications untuk breaking news

---

## 🤝 Panduan Kontribusi

Kami menyambut kontribusi dari developer lain! Berikut cara untuk berkontribusi:

### Melaporkan Bug
1. Cek apakah bug sudah dilaporkan di [Issues](https://github.com/Nzieraaa/news_reader_pro/issues)
2. Jika belum, buat issue baru dengan template yang jelas
3. Sertakan langkah reproduksi, expected behavior, dan actual behavior

### Mengajukan Fitur Baru
1. Buka diskusi di [Issues](https://github.com/Nzieraaa/news_reader_pro/issues)
2. Jelaskan fitur yang diusulkan dan manfaatnya
3. Tunggu persetujuan sebelum implementasi

### Pull Request Process
1. Fork repository ini
2. Buat branch untuk fitur/perbaikan Anda
   ```bash
   git checkout -b feature/namafitur
   ```
3. Commit perubahan Anda
   ```bash
   git commit -m 'Add: Deskripsi fitur yang ditambahkan'
   ```
4. Push ke branch Anda
   ```bash
   git push origin feature/namafitur
   ```
5. Buka Pull Request dengan template yang lengkap

### Standar Kode
- Ikuti [Effective Dart](https://dart.dev/guides/language/effective-dart) guidelines
- Gunakan format yang konsisten dengan `dart format`
- Tambahkan dokumentasi untuk public APIs
- Tulis test untuk new features

---

## 📄 Lisensi

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 Nzieraaa

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 👨‍💻 Author

**Nancy Akisya N (Nzieraaa)**

- 📧 Email: nancy.akisya.n@gmail.com
- 🐙 GitHub: [@Nzieraaa](https://github.com/Nzieraaa)
- 💼 LinkedIn: [Nancy Akisya](https://linkedin.com/in/nancy-akisya)

---

## 🙏 Acknowledgments

- Flutter Team untuk framework yang luar biasa
- API Providers yang menyediakan akses gratis ke data berita:
  - GNews, NewsAPI.org, Currents API, NewsData.io, Mediastack
- Open Source Community untuk packages yang mendukung
- Icon resources: Lucide Icons
- Design Inspiration dari aplikasi berita modern seperti Google News dan Apple News

---

## 📞 Support & Contact

Untuk pertanyaan, bug reports, atau kolaborasi:

- 📧 **Email**: nancy.akisya.n@gmail.com
- 🐛 **Issues**: [GitHub Issues](https://github.com/Nzieraaa/news_reader_pro/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/Nzieraaa/news_reader_pro/discussions)

---

<div align="center">

Made with ❤️ using Flutter

**Last Updated**: 20 November 2025  
**Flutter Version**: 3.32.8  
**Dart Version**: 3.8.1

</div>
