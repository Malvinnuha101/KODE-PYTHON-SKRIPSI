# Studi Kurva Rotasi Galaksi Bima Sakti dan M31 dengan Model ΛCDM dan Teori MOND

Repository ini berisi kode Python lengkap dan hasil analisis untuk skripsi sarjana Fisika FMIPA UGM dengan judul **"Studi Kurva Rotasi Galaksi Bima Sakti dan M31 dengan Model ΛCDM dan Teori MOND"**.

## 📋 Informasi Umum

- **Penulis**: Muhammad Alvin Nuha
- **Email**: malvinnuha@gmail.com  
- **Institusi**: Fakultas Matematika dan Ilmu Pengetahuan Alam, Universitas Gadjah Mada
- **Program Studi**: Fisika
- **Jenis**: Skripsi Sarjana

## 🎯 Tujuan Penelitian

Analisis empiris kurva rotasi galaksi Bima Sakti dan M31 (Andromeda) dengan membandingkan performa:
- **Model ΛCDM** dengan profil halo NFW dan Core
- **Teori MOND** dengan interpolasi fungsi standar dan arctangent

## 🏗️ Struktur Kode

### Kelas Utama: `GalaxyRotationAnalyzer`

Kelas utama yang mengimplementasikan seluruh analisis kurva rotasi galaksi.

#### Komponen Penting:

1. **Data Observasi**
   - Data kurva rotasi Bima Sakti dan M31 dari sumber empiris terkini
   - Radius (kpc), kecepatan rotasi (km/s), dan error pengukuran

2. **Model Fisika**
   - **MOND Standar**: `v_total_mond_std()`
   - **MOND Arctan**: `v_total_mond_arctan()`
   - **ΛCDM NFW**: `v_total_nfw()`
   - **ΛCDM Core**: `v_total_core()`

3. **Komponen Galaksi**
   - Bulge dengan profil de Vaucouleurs
   - Disk eksponensial
   - Halo materi gelap (NFW dan Core)

4. **Metode Analisis**
   - Fitting kurva dengan `curve_fit`
   - Perbandingan statistik (χ², AIC, BIC, R²)
   - Visualisasi komprehensif
   - Uji hipotesis baryonik

## 📊 Hasil Analisis Utama

### Bima Sakti
- **Model Terbaik**: ΛCDM NFW (AIC terendah: 1076.76)
- **Performa MOND**: MOND Arctan lebih baik daripada MOND Standar
- **χ² terendah**: ΛCDM NFW (1064.76)

### M31 (Andromeda)
- **Model Terbaik**: MOND (baik Standar maupun Arctan)
- **AIC terendah**: MOND Arctan (28.03)
- **ΛCDM** menunjukkan performa lebih buruk untuk M31

## 🚀 Cara Menjalankan

### Prasyarat
```bash
pip install numpy matplotlib scipy scikit-learn
