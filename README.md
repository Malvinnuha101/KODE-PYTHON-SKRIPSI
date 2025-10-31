# Studi Kurva Rotasi Galaksi Bima Sakti dan M31 dengan Model ΛCDM dan Teori MOND

Repository ini berisi kode Python lengkap dan hasil analisis untuk skripsi sarjana Fisika FMIPA UGM dengan judul **"Studi Kurva Rotasi Galaksi Bima Sakti dan M31 dengan Model ΛCDM dan Teori MOND"**.

## 📋 Informasi Umum

- **Penulis**: Muhammad Alvin Nuha
- **Email**: malvinnuha@gmail.com  
- **Institusi**: Fakultas Matematika dan Ilmu Pengetahuan Alam, Universitas Gadjah Mada
- **Program Studi**: Fisika
- **Jenis**: Skripsi Sarjana
- **Tahun**: 2025

## 🎯 Tujuan Penelitian

Analisis empiris kurva rotasi galaksi Bima Sakti dan M31 (Andromeda) dengan membandingkan performa:
- **Model ΛCDM** dengan profil halo NFW dan Core
- **Teori MOND** dengan interpolasi fungsi standar dan arctangent
- Evaluasi komprehensif menggunakan metrik statistik modern (AIC, BIC, χ², R²)

## 🏗️ Struktur Kode

### Kelas Utama: `GalaxyRotationAnalyzer`

Kelas utama yang mengimplementasikan seluruh analisis kurva rotasi galaksi.

#### Komponen Penting:

1. **Data Observasi**
   - Data kurva rotasi Bima Sakti (73 titik data) dan M31 (55 titik data)
   - Radius (kpc), kecepatan rotasi (km/s), dan error pengukuran
   - Sumber data empiris terkini

2. **Model Fisika**
   - **MOND Standar**: `v_total_mond_std()` - Fungsi interpolasi standar
   - **MOND Arctan**: `v_total_mond_arctan()` - Fungsi interpolasi arctangent
   - **ΛCDM NFW**: `v_total_nfw()` - Profil halo Navarro-Frenk-White
   - **ΛCDM Core**: `v_total_core()` - Profil halo dengan core

3. **Komponen Galaksi**
   - **Bulge**: Profil de Vaucouleurs dengan integrasi numerik
   - **Disk**: Model eksponensial dengan fungsi Bessel
   - **Gas**: Kontribusi gas interstellar
   - **Halo**: Materi gelap (NFW/Core untuk ΛCDM)

4. **Metode Analisis**
   - Fitting kurva dengan `scipy.optimize.curve_fit`
   - Perbandingan statistik (χ², AIC, BIC, R²)
   - Visualisasi komprehensif dengan matplotlib
   - Uji signifikansi statistik
   - Analisis residual

## ⚙️ Instalasi dan Menjalankan

### Prasyarat
```bash
pip install numpy matplotlib scipy scikit-learn
```

### Menjalankan Analisis
```python
from galaxy_rotation_analyzer import GalaxyRotationAnalyzer

analyzer = GalaxyRotationAnalyzer()
analyzer.run_analysis()
```

## 📊 Hasil Analisis Utama

### Bima Sakti (Milky Way)
| Model | χ² | χ²/dof | AIC | BIC | R² | Rank |
|-------|-----|---------|------|------|-----|-------|
| ΛCDM NFW | 1064.76 | 15.89 | 1076.76 | 1090.50 | 0.5879 | 🥇 |
| ΛCDM Core | 1101.47 | 16.44 | 1113.47 | 1127.21 | 0.4793 | 🥈 |
| MOND Arctan | 1282.76 | 18.59 | 1290.76 | 1299.93 | 0.1654 | 🥉 |
| MOND Std | 1332.56 | 19.31 | 1340.56 | 1349.72 | -0.0165 | 4 |

**Kesimpulan Bima Sakti**: Model ΛCDM NFW menunjukkan performa terbaik dengan AIC terendah (1076.76) dan R² tertinggi (0.5879).

### M31 (Andromeda)
| Model | χ² | χ²/dof | AIC | BIC | R² | Rank |
|-------|-----|---------|------|------|-----|-------|
| MOND Arctan | 20.03 | 0.39 | 28.03 | 36.06 | 0.1048 | 🥇 |
| MOND Std | 21.55 | 0.42 | 29.55 | 37.58 | 0.0974 | 🥈 |
| ΛCDM NFW | 38.71 | 0.79 | 50.71 | 62.75 | -1.4759 | 🥉 |
| ΛCDM Core | 44.84 | 0.92 | 56.84 | 68.88 | -1.9273 | 4 |

**Kesimpulan M31**: Model MOND (terutama varian Arctan) menunjukkan performa superior dengan AIC terendah (28.03) dan χ²/dof mendekati 1.

## 🔍 Temuan Kunci

### Perbandingan Model MOND
- **MOND Arctan** secara konsisten lebih baik daripada **MOND Standar**
- Perbedaan signifikan terlihat pada galaksi Bima Sakti (ΔAIC = -49.80)
- Iterasi Newton-Raphson untuk MOND Arctan konvergen dengan cepat (2-4 iterasi)

### Perbandingan Halo ΛCDM
- **NFW** lebih disukai daripada **Core** untuk kedua galaksi
- Perbedaan lebih menonjol pada Bima Sakti (ΔAIC = -36.70)

### Kontroversi Galaksi
- **Bima Sakti**: ΛCDM lebih unggul
- **M31**: MOND lebih unggul
- Menunjukkan kemungkinan dependensi lingkungan atau karakteristik intrinsik galaksi

## 📈 Visualisasi

Analisis menyediakan berbagai plot komprehensif:
- Kurva rotasi dengan komponen terpisah (bulge, disk, halo)
- Perbandingan model side-by-side
- Analisis residual
- Plot semua model dalam satu gambar

## 🎓 Implikasi Ilmiah

1. **Tidak ada model universal** yang cocok untuk semua galaksi
2. **MOND** menunjukkan performa baik untuk M31, mendukung modifikasi gravitasi
3. **ΛCDM** tetap kompetitif, terutama untuk Bima Sakti
4. Perlunya **analisis lebih banyak galaksi** untuk kesimpulan definitif

## 🔮 Pengembangan Selanjutnya

- Penambahan data galaksi lain
- Implementasi fungsi interpolasi MOND alternatif
- Analisis sensitivitas parameter
- Integrasi dengan data kinematik bintang dan gas

## 📄 Lisensi

Proyek ini ditujukan untuk tujuan akademik. Silakan menghubungi penulis untuk penggunaan lebih lanjut.

---

**Catatan**: Analisis ini memberikan wawasan berharga dalam debat kosmologi modern antara materi gelap (ΛCDM) dan modifikasi gravitasi (MOND).
