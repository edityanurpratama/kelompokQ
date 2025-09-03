# kelompokQ
Kecerdasan buatan

# Diabetes Dataset Analytics - Machine Learning Demo

Aplikasi web interaktif untuk analisis dataset diabetes dengan implementasi algoritma Naive Bayes dan K-Nearest Neighbors (KNN) menggunakan vanilla JavaScript.

##  Fitur Utama

###  Analisis Dataset Interaktif
- **Tabel Dinamis**: Sorting, filtering, pencarian global, dan pagination
- **Upload CSV**: Import dataset kustom dengan validasi schema
- **Download CSV**: Export data yang sudah difilter
- **Visualisasi**: Scatterplot interaktif dengan tooltip

###  Demo Algoritma Machine Learning
- **Naive Bayes**: Implementasi lengkap dengan perhitungan step-by-step
- **K-Nearest Neighbors**: Algoritma KNN dengan visualisasi jarak
- **Penjelasan Interaktif**: Setiap langkah perhitungan ditampilkan secara detail

###  UI/UX Modern
- **Progressive Enhancement**: Berfungsi tanpa JavaScript
- **Dark/Light Mode**: Toggle tema dengan auto-detection `prefers-color-scheme`
- **Responsive Design**: Mobile-first dengan CSS Grid & Flexbox
- **Keyboard Shortcuts**: Navigasi cepat dengan hotkeys
- **PWA Ready**: Service worker untuk offline caching

###  Accessibility & Performance
- **WCAG AA Compliant**: Kontras warna, keyboard navigation, ARIA labels
- **Print-Friendly**: CSS print styles untuk export PDF
- **Performance Optimized**: Lazy loading, efficient DOM manipulation
- **Reduced Motion**: Respect `prefers-reduced-motion`

##  Quick Start

### Deploy ke Hosting Statis
1. **Upload semua file** ke root directory hosting:
   ```
   index.html
   styles.css
   app.js
   sw.js
   diabetes.csv
   manifest.json (opsional)
   README.md
   ```

2. **Akses melalui browser** - aplikasi siap digunakan!

### Local Development
1. Clone atau download semua file
2. Buka `index.html` di browser modern
3. Untuk PWA features, gunakan local server:
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Node.js (http-server)
   npx http-server
   ```

##  Cara Menggunakan

### Keyboard Shortcuts
- `D` - Download dataset aktif
- `I` - Toggle info dataset
- `T` - Toggle dark/light mode  
- `S` - Focus ke search box
- `Esc` - Close modal/dialog

### Upload Dataset Kustom
1. Klik **"Upload CSV"** di bagian dataset
2. Pilih file CSV dengan kolom yang sesuai:
   ```
   Pregnancies,Glucose,BloodPressure,SkinThickness,Insulin,BMI,DiabetesPedigreeFunction,Age,Outcome
   ```
3. File akan divalidasi dan ditampilkan di tabel

### Demo Algoritma ML
1. **Input Data**: Adjust slider untuk Glucose, BloodPressure, Age
2. **Pilih Model**: Naive Bayes atau KNN (dengan parameter k)
3. **Prediksi**: Klik "Hitung Prediksi" untuk melihat hasil
4. **Step-by-step**: Semua perhitungan matematika ditampilkan detail

### Visualisasi Interactive
- **Hover**: Lihat detail data point
- **Click**: Analisis ML untuk sampel spesifik
- **Zoom**: Scroll untuk zoom in/out (desktop)

### Task Management
- **Add Task**: Klik "+ Tambah Tugas"
- **Drag & Drop**: Reorder tugas dengan drag-drop
- **Progress Sync**: Status tersimpan otomatis di localStorage
- **Export**: Download progress sebagai JSON/CSV

##  Contoh Input/Output

### Input Prediksi:
```javascript
{
  glucose: 148,
  bloodPressure: 72,
  age: 50
}
```

### Output Naive Bayes:
```
=== PERHITUNGAN NAIVE BAYES ===
Prior P(diabetes=1): 0.348837
Prior P(diabetes=0): 0.651163

Likelihood untuk diabetes=1:
- P(glucose=148|diabetes=1) = 0.024691
- P(bloodPressure=72|diabetes=1) = 0.042857  
- P(age=50|diabetes=1) = 0.028571

Posterior P(diabetes=1|X) = 0.742536
Prediksi: DIABETES (74.25%)
```

### Output KNN (k=5):
```
=== PERHITUNGAN KNN (k=5) ===
Jarak terdekat:
1. Index 0: distance = 2.236 → Diabetes
2. Index 15: distance = 3.162 → No Diabetes  
3. Index 23: distance = 4.123 → Diabetes
4. Index 47: distance = 4.899 → Diabetes
5. Index 88: distance = 5.477 → No Diabetes

Voting: 3 Diabetes, 2 No Diabetes
Prediksi: DIABETES (60%)
```

##  Struktur File

```
├── index.html          # Main HTML dengan semantic structure
├── styles.css          # CSS dengan custom properties & responsive
├── app.js             # JavaScript utama (modular functions)
├── sw.js              # Service worker untuk PWA caching
├── diabetes.csv       # Dataset statis (fallback)
├── manifest.json      # PWA manifest (opsional)
└── README.md          # Dokumentasi lengkap
```

##  Testing & Validation

### Built-in Test Suite
Buka Developer Console dan jalankan:
```javascript
runTests(); // Menjalankan 10 unit tests otomatis
```

Tests mencakup:
- ✅ CSV parsing accuracy
- ✅ Sorting algorithm correctness  
- ✅ Naive Bayes calculations
- ✅ KNN distance calculations
- ✅ Data validation functions
- ✅ LocalStorage operations
- ✅ Theme switching
- ✅ Progressive enhancement
- ✅ Accessibility features
- ✅ Performance metrics

### Manual Testing Checklist

**Progressive Enhancement:**
- [ ] Konten terbaca tanpa JavaScript
- [ ] Link download CSV statis berfungsi
- [ ] JavaScript enhance tabel menjadi interactive

**Accessibility:**
- [ ] Semua tombol fokusable dengan Tab
- [ ] Kontras warna minimum 4.5:1 
- [ ] Screen reader compatible
- [ ] Keyboard shortcuts berfungsi

**Performance:**
- [ ] Tabel responsive dengan >1000 rows
- [ ] Canvas rendering smooth 60fps
- [ ] PWA caching berfungsi offline
- [ ] Critical CSS inline < 14KB

**Cross-browser:**
- [ ] Chrome/Edge (modern)
- [ ] Firefox  
- [ ] Safari
- [ ] Mobile browsers

## 🔧 Kustomisasi

### Tema & Warna
Edit CSS custom properties di `styles.css`:
```css
:root {
  --primary-color: #3b82f6;
  --background-color: #ffffff;
  --text-color: #1f2937;
  /* ... */
}
```

### Dataset Schema
Untuk dataset kustom, pastikan kolom sesuai:
```csv
Pregnancies,Glucose,BloodPressure,SkinThickness,Insulin,BMI,DiabetesPedigreeFunction,Age,Outcome
```

### Algoritma Parameters
Modifikasi konstanta di `app.js`:
```javascript
const DEFAULT_K = 5;           // KNN default k
const SMOOTHING = 1e-6;        // Naive Bayes smoothing
const MAX_ROWS_PER_PAGE = 25;  // Pagination size
```

##  Arsitektur Teknis

### Progressive Enhancement Strategy
1. **Base Layer**: HTML semantik + CSS dasar
2. **Enhancement Layer**: JavaScript interaktivity
3. **PWA Layer**: Service worker + caching

### Performance Optimizations
- **Virtual Scrolling**: Tabel besar rendering efficiently
- **Debounced Search**: Input filtering dengan delay
- **RequestAnimationFrame**: Smooth canvas animations
- **Lazy Loading**: Non-critical resources loaded on-demand

### Security Measures
- **Input Sanitization**: CSV upload validation
- **XSS Prevention**: No `innerHTML` dengan user data
- **CSP Ready**: Content Security Policy compatible

##  Troubleshooting

### PWA Tidak Install
- Pastikan HTTPS atau localhost
- Check service worker registration di DevTools
- Verify manifest.json format

### Tabel Lambat dengan Dataset Besar
- Enable virtual scrolling (otomatis >500 rows)
- Reduce pagination size di settings
- Close browser tabs lain

### Upload CSV Gagal
- Check file format (UTF-8 encoding)
- Verify column headers match schema
- Maximum file size: 5MB

### Algoritma Hasil Tidak Akurat
- Pastikan input dalam range valid
- Check console untuk error messages
- Verify dataset quality (no missing values)

##  Contributing

Contributions welcome! Areas yang bisa dikembangkan:
- Algoritma ML tambahan (SVM, Decision Tree)
- Visualisasi advanced (3D plots, heatmaps)
- Export format lain (Excel, PDF report)
- Integrasi dengan backend API
- Mobile app wrapper (Cordova/Capacitor)

##  Changelog

### v1.0.0 (Initial Release)
- ✅ Complete refactor dari single HTML ke modular structure
- ✅ Interactive table dengan sort/filter/pagination
- ✅ ML algorithms implementation (Naive Bayes + KNN)
- ✅ PWA dengan offline caching
- ✅ Accessibility WCAG AA compliance
- ✅ Dark mode dengan system preference detection
- ✅ Comprehensive test suite
- ✅ Print-friendly & export-to-PDF
- ✅ Responsive mobile-first design

##  License

MIT License - bebas digunakan untuk proyek personal & komersial.

---

**Dibuat secara bertahap menggunakan Vanilla JS - No frameworks, no dependencies, just pure web standards!**
