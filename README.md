# Studi Kurva Rotasi Galaksi Bima Sakti dan M31 dengan Model ΛCDM dan Teori MOND

Repository ini berisi kode Python lengkap dan hasil analisis untuk skripsi sarjana Fisika FMIPA UGM dengan judul **"Studi Kurva Rotasi Galaksi Bima Sakti dan M31 dengan Model ΛCDM dan Teori MOND"**.

## 📋 Informasi Umum

- **Penulis**: Muhammad Alvin Nuha
- **Email**: malvinnuha@gmail.com  
- **Institusi**: Fakultas Matematika dan Ilmu Pengetahuan Alam, Universitas Gadjah Mada
- **Program Studi**: Fisika
- **Jenis**: Skripsi Sarjana S1
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
   - **Gas**: Kontribusi gas interstellar (diabaikan dalam analisis ini)
   - **Halo**: Materi gelap (NFW/Core untuk ΛCDM)

4. **Metode Analisis**
   - Fitting parameter dengan `scipy.optimize.curve_fit` dengan metode Trust Region Reflective (`trf`)
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

**Kesimpulan Bima Sakti**: Model ΛCDM NFW menunjukkan performa terbaik dengan AIC terendah (1076.76) dan R² tertinggi (0.5879). Nilai χ²/dof untuk semua model jauh di atas 1, mengindikasikan ketidakcocokan model dengan data atau underestimation dari error pengukuran.

### M31 (Andromeda)
| Model | χ² | χ²/dof | AIC | BIC | R² | Rank |
|-------|-----|---------|------|------|-----|-------|
| MOND Arctan | 33.81 | 0.66 | 41.81 | 49.84 | 0.1050 | 🥇 |
| MOND Std | 40.33 | 0.79 | 48.33 | 56.36 | 0.0904 | 🥈 |
| ΛCDM NFW | 47.55 | 0.97 | 59.55 | 71.60 | -1.4043 | 🥉 |
| ΛCDM Core | 63.24 | 1.29 | 75.24 | 87.28 | -2.6907 | 4 |

**Kesimpulan M31**: Model MOND Arctan menunjukkan performa terbaik dengan AIC terendah (41.81) dan χ²/dof terdekat dengan 1 (0.66). Semua model memiliki χ²/dof yang relatif dekat dengan 1, menunjukkan kecocokan yang lebih baik dibandingkan dengan Bima Sakti.

## 🔍 Temuan Kunci

### Perbandingan Model MOND
- **MOND Arctan** secara konsisten lebih baik daripada **MOND Standar** untuk kedua galaksi.
- Pada Bima Sakti, ΔAIC (Arctan - Std) = -49.80, bukti sangat kuat mendukung MOND Arctan.
- Pada M31, ΔAIC (Arctan - Std) = -6.52, bukti positif mendukung MOND Arctan.
- Iterasi Newton-Raphson untuk menghitung a_M pada MOND Arctan konvergen dengan cepat (2-4 iterasi).

### Perbandingan Halo ΛCDM
- **NFW** lebih disukai daripada **Core** untuk kedua galaksi.
- Pada Bima Sakti, ΔAIC (Core - NFW) = 36.70, bukti sangat kuat mendukung NFW.
- Pada M31, ΔAIC (Core - NFW) = 15.68, bukti sangat kuat mendukung NFW.

### Perbandingan Antar Paradigma (ΛCDM vs MOND)
- **Bima Sakti**: ΛCDM (khususnya NFW) secara signifikan lebih baik daripada MOND (baik Std maupun Arctan). ΔAIC antara ΛCDM NFW dan MOND Arctan adalah -214.00 (bukti sangat kuat mendukung ΛCDM NFW).
- **M31**: MOND (khususnya Arctan) secara signifikan lebih baik daripada ΛCDM. ΔAIC antara MOND Arctan dan ΛCDM NFW adalah -17.74 (bukti sangat kuat mendukung MOND Arctan).

### Kontroversi Galaksi
- **Bima Sakti**: ΛCDM lebih unggul.
- **M31**: MOND lebih unggul.
- Perbedaan ini menunjukkan kemungkinan ketergantungan lingkungan atau karakteristik intrinsik galaksi yang berbeda, atau mungkin juga karena kualitas data yang berbeda.

## 📈 Visualisasi

Analisis menyediakan berbagai plot komprehensif:
1. **Kurva rotasi per model** dengan komponen terpisah (bulge, disk, halo, dan total)
2. **Perbandingan model side-by-side**: 
   - ΛCDM NFW vs Core
   - MOND Std vs Arctan
3. **Plot semua model** dalam satu gambar untuk perbandingan langsung.
4. **Analisis residual** untuk setiap model.

## 🎓 Implikasi Ilmiah

1. **Tidak ada model universal** yang cocok untuk semua galaksi. Hasil berbeda antara Bima Sakti dan M31 menuntut kehati-hatian dalam generalisasi.
2. **ΛCDM** menunjukkan performa baik untuk Bima Sakti, mendukung keberadaan materi gelap.
3. **MOND** tetap kompetitif, terutama untuk M31, mendukung modifikasi gravitasi sebagai alternatif materi gelap.
4. Perlunya **analisis lebih banyak galaksi** dengan data berkualitas tinggi untuk menarik kesimpulan definitif mengenai paradigma mana yang lebih disukai.
5. **Fungsi interpolasi arctan** pada MOND menunjukkan peningkatan dibandingkan fungsi standar, menunjukkan ruang untuk perbaikan dalam formulasi MOND.

## 📄 Lisensi

Proyek ini ditujukan untuk tujuan akademik. Silakan menghubungi penulis untuk penggunaan lebih lanjut.

---

*Terakhir diperbarui: Desember 2025*
