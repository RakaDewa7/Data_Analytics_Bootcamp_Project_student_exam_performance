# Dashboard Analisis Kelulusan Siswa & Performa Akademik

## Ringkasan
Membangun dasbor analitik interaktif untuk mengevaluasi faktor-faktor penentu kelulusan siswa dari dataset berskala besar (100.000 data siswa). Proyek ini berfokus untuk membedah akar permasalahan tingginya angka ketidaklulusan (22,61%) dengan meninjau korelasi antara aspek psikologis (stres dan kecemasan), durasi istirahat/tidur, kebiasaan belajar harian, hingga pola persiapan ujian[cite: 185, 193].

## Problem Statement
Berdasarkan studi kasus performa akademik, sekitar **22,61% dari total 100.000 siswa tercatat tidak lulus**[cite: 185]. Analisis mendalam diperlukan untuk mengidentifikasi penyebab utama kegagalan tersebut—apakah dipengaruhi oleh demografi (gender), atau justru bersumber dari faktor internal seperti tingkat stres yang ekstrem, manajemen waktu belajar yang kurang optimal, serta kebiasaan belajar mendadak menjelang ujian[cite: 186, 193].

## Data Exploration & Understanding
* **Sumber Data:** Dataset *Student Exam Performance* dari Kaggle[cite: 173].
* **Ukuran Dataset:** 100.000 baris × 44 kolom[cite: 170].
* **Tipe Data:** Terdiri dari tipe data *object* (kategorikal), *int* (bilangan bulat), dan *float* (desimal)[cite: 170].
* **Variabel Utama:** Mencakup demografi siswa, riwayat akademik (`previous_gpa`, `attendance_percentage`), aspek kebiasaan belajar (`study_hours_per_day`, `self_study_hours`), kondisi kesehatan (`sleep_hours`, `stress_level`), hingga hasil ujian akhir (`exam_score`, `pass_status`)[cite: 171, 172, 173].

## Data Preparation & Cleaning
* **Missing Value:** Ditemukan beberapa kolom dengan nilai kosong (seperti *attendance_percentage* 9,86%, *time_management_score* 9,61%, *notes_quality* 8,41%, *previous_gpa* 7,79%, dan *sleep_quality* 6,99%)[cite: 175]. Penanganan dilakukan dengan mengisi nilai kosong menggunakan penanda `'None'` atau evaluasi lanjutan guna mempertahankan jumlah observasi total[cite: 180].
* **Duplikasi:** Pengecekan duplikasi menunjukkan **tidak ada baris data yang terduplikasi (0,00%)**[cite: 177].
* **Outlier (IQR):** Identifikasi menggunakan metode IQR mendeteksi beberapa nilai ekstrem[cite: 178]. Namun, nilai tersebut dipertahankan karena merepresentasikan variasi perilaku belajar dan karakteristik individu siswa yang beragam[cite: 178].
* **Uji Normalitas:** Sebagian besar variabel numerik terbukti berdistribusi tidak normal (*P-Value < 0.05*), kecuali variabel `sleep_hours` yang menunjukkan distribusi relatif normal[cite: 181].

## Feature Engineering
Untuk mempermudah pengelompokan dan analisis mendalam, dilakukan penambahan kolom kategori baru menggunakan fungsi *binning* (`pd.cut`):
* **`stress_category`**: Pengelompokan tingkat stres (*Very Low, Low, Moderate, High, Very High*)[cite: 183, 184].
* **`study_category`**: Kategorisasi durasi total waktu belajar harian[cite: 183, 184].
* **`self_study_category`**: Kategorisasi intensitas waktu belajar mandiri per hari[cite: 183, 184].
* **`sleep_category`**: Pengelompokan durasi tidur per malam (*Very Low, Low, Recommended, High*)[cite: 183, 184].
* **`preparation_category`**: Pengelompokan lama hari persiapan ujian (*Very Short, Short, Moderate, Long*)[cite: 183].

## Visualization & Dashboard Insights
* **Distribusi Demografi & Kegagalan:** Dari 100.000 siswa (49.130 laki-laki, 48.841 perempuan)[cite: 185], angka kegagalan terbagi merata antara siswa laki-laki (11.084 siswa) dan perempuan (11.048 siswa), membuktikan bahwa **faktor gender bukan penentu utama kegagalan**[cite: 186].
* **Kombinasi Tidur Ideal & Stres Ekstrem:** Konsentrasi kegagalan tertinggi justru terjadi pada kelompok siswa dengan durasi tidur ideal (*Recommended*), namun mengalami tingkat stres yang sangat tinggi (*Very High*) sebanyak **11.421 siswa**[cite: 187].
* **Faktor Kecemasan Ujian:** Dari kelompok tidur *Recommended*, sebanyak **11.085 siswa** yang tidak lulus mengalami kategori kecemasan *Very High*[cite: 188].
* **Durasi Belajar & Persiapan:** Sebagian besar siswa yang gagal dengan durasi tidur ideal ternyata memiliki alokasi waktu belajar harian yang rendah (*Low* sebanyak 6.395 siswa)[cite: 189], belajar mandiri menengah (*Moderate* 5.667 siswa)[cite: 190], serta persiapan ujian yang sangat singkat (*Very Short* / mendadak sebanyak 4.961 siswa)[cite: 191].

## Conclusion
* Kegagalan siswa (22,61%) tidak dipengaruhi oleh faktor demografi seperti gender[cite: 185, 193].
* Kegagalan didorong oleh akumulasi faktor psikologis yang buruk (stres dan kecemasan ekstrem) serta kebiasaan belajar yang tidak efektif—seperti jam belajar harian yang rendah, minimnya belajar mandiri, dan kebiasaan menunda persiapan ujian hingga mendadak (*short notice*)[cite: 193].

## Recommendation
* **Intervensi Psikologis & Konseling:** Sekolah perlu menyediakan layanan konseling kilat dan program manajemen stres/kecemasan intensif (seperti teknik pernapasan *grounding* 4-7-8 sebelum ujian) untuk menangani siswa di zona risiko tinggi[cite: 188, 193].
* **Penerapan Jadwal Belajar Terstruktur:** Menerapkan *mandatory study blocks* (jadwal harian terstruktur) untuk menyeimbangkan waktu sekolah, istirahat, dan belajar mandiri guna menghindari penumpukan beban belajar[cite: 189, 193].
* **Sistem *Milestone* Persiapan Ujian:** Membagikan kalender akademik dan kisi-kisi resmi minimal 1 bulan sebelum pelaksanaan ujian untuk mencegah kebiasaan belajar sistem kebut semalam (*Very Short preparation*)[cite: 191, 193].

## Tools yang Digunakan
Tableau / Dashboard Interaktif · Python (Pandas, Scipy, IQR, Matplotlib, Seaborn) · Feature Engineering (*Binning*) · Exploratory Data Analysis (EDA)

---
*Bagian dari Portofolio Graphic Design & Data Analytics Career Accelerator — Tempat Belajar (2026)*[cite: 159]  
*Disusun oleh: Raka Dewa Dipa Mahesa Arsandy*[cite: 158]
