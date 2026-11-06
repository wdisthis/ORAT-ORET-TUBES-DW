# Rangkuman Capstone Data Wrangling: Kelompok 12
hadeh
**Kasus 12: Upah dan pekerjaan informal** (klaster C, Gender dan ketenagakerjaan, SDG 8)
Periode: Ganjil 2026/2027 · Pembimbing: **Mika Alvionita** · Disusun: 5 Nov 2026 (WIB)

Sumber yang dibaca:
1. `tugas_besar.pdf`: screenshot Workbench (Aturan & Ketentuan, Kontrak Tim, Denyut tim, Kasus tim, Galeri)
2. `00-langkah-kerja-capstone-dw.pdf`: langkah kerja harian, 8 tahap, ringkasan sprint
3. `kelompok-12.pdf`: panduan khusus Kelompok 12
4. `Data_Science_Workbench.pdf`: screenshot panduan di Workbench
5. `pedoman-capstone-dw_1.pdf`: pedoman lengkap, 70 halaman (dibaca penuh)
6. `pedoman-capstone-dw.pdf`: sama dengan no. 5 pada halaman 1–20 (sisanya belum dibaca, lihat bagian 11)

---

## 1. Ringkasan: apa yang harus dilakukan

1. **Sekarang (Sprint 0, 2–8 Nov).** Lengkapi Kontrak Tim (baru 2/5 bagian terisi). Ikat akun GitHub ke Workbench. Pastikan repo tim sudah dibuat, semua anggota diundang, dan repo sudah diikat di Papan Tim. Jalankan `unduh_data.py --kasus 12` di laptop sampai pemeriksaan sha256 lolos. Lakukan push pertama. Tulis baris pertama `log-keputusan.csv`. Tulis Log Sprint 0.
2. **Batas waktu paling dekat:** Sprint 0 berakhir Minggu 8 Nov. Log dan tugas Sprint 0 masih diterima sampai **Senin 9 Nov 23.59 WIB**. Setelah itu, log yang kosong dianggap tidak hadir.
3. **Hal mendesak:** di screenshot Denyut tim (hari ke-4 Sprint 0), akunmu tercatat "belum ada detak" dan "senyap sejak awal", dan pembimbing bisa melihatnya. Pastikan aktivitasmu tercatat (akun terikat, push dari aplikasi DSWorkbench).
4. **Sampai akhir periode:** kerjakan satu komponen kode (bobot terbesar individu), tulis laporan perorangan (maks. 1200 kata), ikut 3 demo sprint wajib, tulis Log Sprint tiap sprint, review PR rekan, catat AI_LOG tim, dan ikut wawancara 7–13 Des.

---

## 2. Tim Kelompok 12

| No | Nama | NIM | Catatan |
|---|---|---|---|
| 1 | Cerine Sihotang | 124450049 | Di Denyut tim: senyap sejak awal |
| 2 | Zoland Ryo Febriano | 124450065 | Di Denyut tim: aktif (5 jam lalu) |
| 3 | Bunga Clarisa Sefa | 124450097 | Di Denyut tim: senyap sejak awal |
| 4 | **Fitra** (kamu) | 124450102 | Di Denyut tim: senyap sejak awal |
| 5 | Yulia Kristine Malau | 124450119 | Di Denyut tim: senyap sejak awal |

- Nama tim di Galeri: **"Semoga bisa"** (tampil sebagai "Kelompok 12 · Semoga bisa").
- Pembimbing kelompok ini adalah **Mika Alvionita** (Pedoman, Lampiran D).
- Kelompok 5 orang: setiap komponen wajib diisi, jadi **setiap anggota memegang tepat satu komponen dan satu tugas sampingan**.

---

## 3. Jadwal (WIB)

| Sprint | Tanggal | Fokus | Demo | Definition of Done (ringkas) |
|---|---|---|---|---|
| **0** | 2–8 Nov (Minggu) | Kontrak, repo, unduh paket | Tidak wajib | Kontrak Tim terisi; repo dari template, semua anggota terikat GitHub dan sudah push; `unduh_data.py --kasus 12` lolos sha256 di laptop tiap anggota; baris pertama `log-keputusan.csv` |
| **1** | 9–22 Nov | Tahap 1–3: ekstraksi, profil, pembersihan; Silver pertama | **Wajib** | Membaca semua format mentah (tahap 1); profil & anomali per seri (tahap 2); missing, outlier, patahan, duplikat ditangani dan dicatat di log (tahap 3); `silver.parquet` lolos `python -m src.common.skema`; `results/<nim>/metrics.json` tiap anggota sudah di-commit |
| **2** | 23–29 Nov | Tahap 4–6: transformasi, penyimpanan, integrasi | **Wajib** | Reshape ke panel Gold (provinsi × periode × indikator); Silver dan Gold di SQL dengan alasan pilihan; tabel rekonsiliasi seri utama vs pembanding nasional dengan selisih dijelaskan |
| **3** | 30 Nov–6 Des | Tahap 7–8: skala (arsip WDI), validasi, dokumentasi, laporan | **Wajib** | Analisis revisi arsip WDI; perbandingan pandas vs DuckDB/Dask; skema validasi otomatis dan data dictionary lengkap; `python pipeline.py` dari data mentah menghasilkan ulang Silver dan Gold yang di-commit; `reports/tim.md`, `reports/individu/<nim>.md`, `AI_LOG.md` lengkap |
| Galeri | Pilihan favorit: 30 Nov–6 Des | Pilih satu karya tim lain | – | Bukan nilai |
| **Akhir** | **Minggu 6 Des, 23.59 WIB** | Isi `main` dinilai | – | Keterlambatan: potongan ~10% per hari, maks. 3 hari; setelah itu dinilai dari isi `main` pada saat itu |
| Wawancara | 7–13 Des | 10 menit per anggota + 10 menit tim (± 60 menit per tim) | – | Usulan waktu diajukan lewat kartu Wawancara tim; boleh daring; layar + audio direkam |
| Rilis nilai | ≤ 1 minggu setelah jendela wawancara | – | – | Nilai final dari dosen pengampu di Workbench |

Catatan jendela sprint: setiap sprint terbuka pukul 00.00 WIB dan menerima Log serta Demo sampai 24 jam setelah tanggal selesai. Sprint yang berakhir hari Minggu masih menerima log sampai Senin 23.59 WIB. Pedoman tidak menyebut dengan tegas apakah tenggang ini berlaku juga untuk Sprint 3 (lihat bagian 11).

---

## 4. Sistem penilaian

### 4.1 Komponen dan bobot (bawaan platform)

| Kode | Komponen | Bobot | Sumber nilai |
|---|---|---|---|
| s1 | Individu: komponen milik sendiri | **30** | Rubrik pembimbing (kode, eksperimen, jejak hasil) |
| s2 | Individu: laporan perorangan | 15 | Rubrik pembimbing; maks. 1200 kata |
| s3 | Individu: proses (commit, Log Sprint, review PR) | 15 | Dihitung otomatis dari lampu sprint |
| s4 | Tim: analisis integrasi/komparasi | 25 | Rubrik pembimbing; satu dokumen bersama (`reports/tim.md`) |
| s5 | Tim: reproduksibilitas dan demo akhir | 15 | Rubrik pembimbing; satu perintah menjalankan semua |

Total individu 55–70 dan total tim 30–45, jumlah 100. Pembimbing boleh menyesuaikan bobot dalam rentang itu.

### 4.2 Rumus nilai akhir

```
akhir = [(b1·s1 + b2·s2 + b3·s3) / 100] × pengali wawancara
      + [(b4·s4 + b5·s5) / 100] × faktor kontribusi
```

- **Pengali wawancara** (hanya untuk bagian individu): 1,0 paham penuh · 0,7 paham sebagian · 0,3 tidak bisa menjelaskan karyanya sendiri.
- **Faktor kontribusi** (hanya untuk bagian tim): 0,8 + 0,2 × rata-rata lampu sprint, dengan hijau = 1, kuning = 0,5, merah = 0. Rentang 0,8–1,0. Pembimbing bisa menyesuaikan dengan catatan tertulis.
- Contoh di pedoman: s1 = 90, s2 = 80, lampu hijau-kuning-hijau (faktor 0,97), s3 = 83, s4 = 80, s5 = 90, pengali 1,0 → akhir ≈ 84,0.

### 4.3 Lampu sprint (menentukan s3 dan faktor kontribusi)

- **Hijau:** Log Sprint terisi, minimal 1 commit, dan minimal 1 artefak hasil atau review PR.
- **Kuning:** Log terisi, tetapi ada salah satu yang kurang atau bermasalah (commit, artefak, atau review).
- **Merah:** Log kosong, atau tidak ada jejak sama sekali.
- Ikon garis = sementara, sprint belum ditutup.
- Dua sprint merah berturut-turut memberi tanda bendera. Koordinator wajib melapor.

### 4.4 Wawancara

- Per tim, setelah semua sprint selesai. Durasi 10 menit per anggota, ditambah 10 menit untuk tim.
- Tiap anggota diminta: (a) menjelaskan komponennya (satu keputusan desain dan satu kegagalan); (b) mengubah sesuatu di tempat, yang diminta pembimbing; (c) menjawab satu pertanyaan tentang komponen rekan.
- Pertanyaan diambil dari bank pertanyaan (Lampiran A) dan pertanyaan khas Data Wrangling (bagian 7).
- **Tim tidak dihukum** karena anggota yang hilang, tetapi anggota yang hilang mendapat nol di komponen individunya.

### 4.5 Yang tidak dihitung

- Log dan demo adalah jejak proses. Terlambat mengisinya berarti tidak ada.
- Commit dari akun yang tidak terikat ke Workbench tidak dihitung sebagai kontribusi.
- Push dari terminal (di luar aplikasi DSWorkbench) tidak tercatat otomatis. Catat tautannya di formulir bukti kontribusi jika ingin diklaim, dan pembimbing akan memeriksanya saat wawancara.
- Angka hasil tanpa jejak `run` dari Local Runner dianggap tidak ada.

---

## 5. Checklist per fase

### 5.A Sprint 0 (sekarang sampai 8 Nov; tenggang sampai 9 Nov 23.59)

- [ ] **Kontrak Tim lengkap (5 bagian).** Status saat ini: 2/5. Isi: nama tim dan avatar; komponen tiap anggota; tugas sampingan tiap anggota; jam standup mingguan dan kanal komunikasi; kesepakatan "apa yang kami lakukan jika ada anggota yang menghilang". Lengkapi sebelum Sprint 1 dimulai (9 Nov).
- [ ] **Pilih komponen dan tugas sampingan** di kartu *Tim saya* (satu per orang, tidak boleh sama dengan rekan).
- [ ] **Ikat akun GitHub ke Workbench** (menu profil › Tautkan GitHub). Commit dari akun yang belum terikat tidak dihitung.
- [ ] **Repo tim:** satu anggota membuat repo dari template `sains-data/capstone-dw-2026-starter` (tombol *Use this template*), mengundang semua anggota sebagai kolaborator, lalu mengikatnya di kartu *Repo tim* pada Papan Tim. Kartu tampak masih kosong di screenshot.
- [ ] **Setup lokal:** `python -m venv .venv`, aktifkan, `pip install -r requirements.txt`.
- [ ] **Unduh paket:** `python unduh_data.py --kasus 12`. Pemeriksaan sha256 harus lolos di laptop masing-masing.
- [ ] **Cek pipeline awal:** `python pipeline.py` harus berhenti dengan pesan "Tahap 1: tulis pembaca…" (tahap 1 belum ditulis, itu wajar).
- [ ] **Baris pertama `log-keputusan.csv`:** aturan pemetaan wilayah ke susunan 38 provinsi tahun 2025 (Yogyakarta, Kalimantan Utara, Papua baru, dll.). Pilih salah satu strategi (lihat bagian 8.4 pedoman) dan catat.
- [ ] **Push pertama** dari cabang kerja `<nim>/kerja` (dibuat otomatis oleh DSWorkbench saat folder tim dibuka). Push dilakukan dari aplikasi.
- [ ] **Baca `data/KASUS.md`** dan `kelompok-12.pdf`.
- [ ] **Pecah Sprint 1** jadi tugas kecil di Papan Tim. Beri label komponen, penanggung jawab, dan judul yang menyebut seri dan keputusan.
- [ ] **Log Sprint 0:** tiga baris (selesai, berikutnya, hambatan). Ditulis sekali per sprint dan tidak bisa diubah setelah disimpan. Kalau tidak hadir, biarkan kosong.
- [ ] **Lampu hijau Sprint 0:** perlu log, ≥1 commit, dan ≥1 artefak hasil atau review PR. Artefak Sprint 0 belum jelas bentuknya di pedoman. Tanyakan pembimbing atau gunakan review PR.

### 5.B Sprint 1 (9–22 Nov): tahap 1–3, demo wajib

- [ ] Komponen kamu: tulis fungsi pembaca per format di `src/ekstraksi/` (jika komponen Ekstraksi) atau kode profil/pembersihan (jika Profil & pembersihan). Catat jumlah berkas dan baris mentah.
- [ ] Profil dan anomali: statistik deskriptif per seri dan per provinsi, boxplot, deret waktu, z-score atau IQR untuk menandai calon anomali. Simpan grafik di `reports/gambar/`. Tujuannya menemukan, bukan memperbaiki.
- [ ] Pembersihan: buat grid lengkap wilayah × periode × rincian sebelum membahas missing. Bedakan tiga hal: outlier asli (ditandai, tidak diubah), patahan seri (kolom tambahan `patahan_definisi`, tidak diubah), galat input (boleh diperbaiki dan dicatat).
- [ ] Setiap keputusan wrangling dicatat satu baris di `log-keputusan.csv` (id, tanggal, nim, tahap, seri_kode, keputusan, alternatif_ditolak, alasan, dampak_baris).
- [ ] `python -m src.common.skema data/silver/silver.parquet` harus lolos.
- [ ] Hasil ditulis ke `results/<nim>/metrics.json` lewat `python -m src.common.hasil ...`, lalu di-commit. Jalankan *Periksa artefak* dari aplikasi setelah commit.
- [ ] **Demo Sprint 1** (wajib): rekaman layar maksimal 10 menit (MP4/WebM, maks. 50 MB) atau tautan. Tunjukkan keadaan komponen tiap anggota, bukan presentasi.
- [ ] Profil Galeri: judul karya dan ringkasan Markdown (maks. 6000 karakter) sudah bisa diisi sejak Sprint 1 (tidak dinilai).

### 5.C Sprint 2 (23–29 Nov): tahap 4–6, demo wajib

- [ ] Transformasi (tahap 4): simpan upah nominal di Silver. Upah riil dan transformasi logaritma dibuat di Gold sebagai kolom tambahan. Reshape ke panel lebar provinsi × periode × indikator.
- [ ] Penyimpanan (tahap 5): Silver dan Gold di SQLite/DuckDB/PostgreSQL dengan kunci primer. Jelaskan di laporan mengapa satu pendekatan dipilih untuk lapis tertentu.
- [ ] Integrasi (tahap 6): tabel rekonsiliasi untuk setiap pasangan seri utama vs pembanding nasional. Kolom: periode, nilai BPS, nilai ILO, selisih, dan kategori penjelasan (definisi berbeda, metode berbeda, vintage berbeda, cakupan berbeda, belum terjelaskan). Selisih tidak dihapus dan tidak dipaksa sama.
- [ ] **Demo Sprint 2** (wajib).

### 5.D Sprint 3 (30 Nov–6 Des): tahap 7–8, laporan, demo wajib

- [ ] Skala (tahap 7): unduh arsip WDI (`python unduh_data.py --arsip-wdi`, sekitar 19 MB). Saring seri pembanding, lalu ukur seberapa sering dan seberapa besar seri itu direvisi antar 142 rilis. Ulangi dengan pandas dan DuckDB atau Dask. Catat waktu dan memori. Skrip di `src/skala/`.
- [ ] Validasi dan dokumentasi (tahap 8): skema validasi otomatis (pandera atau Great Expectations) untuk Silver dan Gold. `docs/data-dictionary.md` lengkap untuk setiap kolom. Lineage satu baris Gold sampai berkas mentahnya.
- [ ] Reproduksi dari nol: klon bersih di mesin lain, `python unduh_data.py --kasus 12`, lalu `python pipeline.py`. Batas 15 menit di laptop (CPU, RAM 8 GB), tanpa layanan berbayar. Hasilnya harus sama dengan yang di-commit.
- [ ] `README.md`: satu perintah yang menjalankan semua, dan sudah diuji di mesin lain.
- [ ] **Laporan perorangan** `reports/individu/124450102.md` (maks. 1200 kata, lihat bagian 6.2).
- [ ] **Laporan tim** `reports/tim.md` (satu dokumen bersama, lihat bagian 6.3).
- [ ] **AI_LOG.md** tim: tabel tanggal | alat | untuk apa | apa yang diubah dari keluarannya.
- [ ] **Demo Sprint 3** (wajib). Tunjukkan satu perintah reproduksi yang menjalankan semua.
- [ ] **Pilihan favorit Galeri** (30 Nov–6 Des): pilih satu karya tim lain. Bukan nilai, tapi menentukan Juara Galeri.
- [ ] **Semua pull request sudah di-merge ke `main`** sebelum 6 Des 23.59 WIB.

### 5.E Wawancara (7–13 Des) dan nilai

- [ ] Ajukan usulan waktu lewat kartu *Wawancara tim* setelah Sprint 3 selesai (Definition of Done terpenuhi).
- [ ] Siapkan jawaban untuk pertanyaan di bagian 7. Kamu harus bisa menunjukkan buktinya di repo.
- [ ] Setelah wawancara, lihat nilai di kartu *Wawancara tim*: nilai individu (× pengali) dan nilai tim (× faktor).

---

## 6. Format pengumpulan

### 6.1 Apa dikumpulkan dan di mana

| Butir | Letak | Bentuk |
|---|---|---|
| Kasus tim | Workbench, Papan Tim › Kasus tim | Dicatat pembimbing |
| Protokol tim | repo, `src/protokol/` + `data/MANIFEST.json` | Pemuat data, split, metrik utama; dibekukan setelah Sprint 0 |
| Kontrak Tim | Workbench (dokumen bersama) | Lima bagian, lengkap sebelum Sprint 1 |
| Log Sprint | Workbench, Papan Tim | Tiga baris per anggota per sprint |
| Demo Sprint | Workbench, Papan Tim | MP4/WebM ≤ 50 MB atau tautan; ≤ 10 menit |
| Kode komponen | repo, `models/{nim}/` (atau folder yang ditetapkan dosen) | Hanya diubah pemiliknya |
| Berkas hasil | repo, `results/{nim}/metrics.json` | JSON berskema baku, diperiksa Local Runner |
| Laporan perorangan | repo, `reports/individu/{nim}.md` | Markdown, ≤ 1200 kata |
| Laporan tim | repo, `reports/tim.md` | Markdown, enam bagian |
| AI_LOG | repo, `AI_LOG.md` | Tabel kronologis |
| README | repo, `README.md` | Satu perintah untuk reproduksi |
| Profil Galeri | Workbench, Papan Tim | Judul dan ringkasan Markdown |

### 6.2 Laporan perorangan (`reports/individu/124450102.md`, ≤ 1200 kata di luar tabel dan kode)

1. **Komponen saya** (2–3 kalimat): komponen yang dipilih dan perannya dalam proyek tim.
2. **Keputusan desain:** satu keputusan utama, alternatif yang ditolak, dan alasan menolaknya.
3. **Kegagalan dan pelajaran:** satu kegagalan nyata dan perubahan yang diambil karenanya.
4. **Hasil:** angka dari `metrics.json` (sebut `seed` dan `run`), dibaca dengan batas yang jujur.
5. **Yang akan saya ubah jika ada satu sprint lagi** (3–5 kalimat).

Setiap angka di laporan harus ada di `results/` yang sudah di-commit.

### 6.3 Laporan tim (`reports/tim.md`)

Struktur menurut Bab 6.3 pedoman dan parameter Workbench:

1. **Ringkasan**
2. **Protokol:** apa yang membuat perbandingan antarkomponen adil
3. **Hasil:** tabel komparasi, angkanya ditarik dari berkas hasil tiap anggota
4. **Analisis**
5. **Rekomendasi**
6. **Pembagian kerja:** siapa menulis bagian mana dan komponen yang tidak tersedia

Laporan tim tidak dibatasi kata. Yang dinilai adalah ketajaman analisis, bukan panjangnya.

### 6.4 AI_LOG.md

Tabel kronologis dengan empat kolom: tanggal, alat, untuk apa, dan apa yang diubah dari keluarannya. Satu baris per pemakaian yang bermakna. Contoh di pedoman: `2026-11-05 | Copilot | kerangka fungsi pemuat data | ganti nama variabel, tambah penanganan berkas kosong`.

Riwayat percakapan dengan Bravais di Workbench tersimpan dan boleh dipakai mahasiswa sebagai bukti proses belajar saat wawancara.

### 6.5 Hak ubah folder

| Folder atau berkas | Pemilik | Aturan |
|---|---|---|
| `src/common/`, `unduh_data.py` | Dosen | Tidak boleh diubah; pemeriksaan otomatis menolak perubahan |
| `src/ekstraksi/`, `src/silver/`, `src/gold/`, `src/skala/`, `src/validasi/` | Komponen | Diubah lewat pull request yang di-review minimal satu rekan |
| `pipeline.py` | Tim | Urutan tahap tidak diubah; isi tiap tahap di `src/<tahap>/` |
| `models/{nim}/`, `reports/individu/{nim}.md`, `sprint/*/{nim}.md`, `results/{nim}/` | Perorangan | Hanya diubah pemiliknya |
| `log-keputusan.csv`, `docs/data-dictionary.md` | Tim | Setiap anggota menulis barisnya untuk keputusannya sendiri |
| `data/silver/`, `data/gold/` | Tim | Di-commit bila < 20 MB; `data/raw/` tidak boleh di-commit (ada di `.gitignore`) |
| `reports/tim.md`, `AI_LOG.md` | Tim | Enam bagian laporan tim dan catatan AI |

Cabang kerja: `<nim>/kerja` (atau `nim/<topik>`). Cabang `main` dilindungi, dan penggabungan hanya lewat pull request.

---

## 7. Kasus 12: detail teknis

### 7.1 Seri

| Peran | Sumber | Kode | Kode SDG | Satuan di katalog | Periode |
|---|---|---|---|---|---|
| **Seri utama** | BPS | `var1172` | 8.5.1 (upah per jam) | `rupiah_per_jam` | 2015–2025 |
| **Seri utama** | BPS | `var2153` | 8.3.1 (informalitas) | `tidak_ada` (harus ditetapkan dari metadata) | 2018–2025 |
| **Pembanding nasional** | ILOSTAT | `SDG_0851_SEX_OCU_NB` | 8.5.1 | mata uang lokal, per jam (cek unitnya) | 2007–2023 |
| **Pembanding nasional** | ILOSTAT | `SDG_0831_SEX_ECO_RT` | 8.3.1 | – | 2016–2023 |
| **Skala (pengganti WDI)** | Arsip WDI | `SL.ISV.IFRM.ZS` | 8.3.1 | – | (lapangan kerja informal non-pertanian) |
| **Skala (pengganti WDI)** | Arsip WDI | `SL.EMP.WORK.ZS` | 8.3.1 | – | (pekerja bergaji) |

Paket kasus ini tidak memuat seri WDI, jadi tahap skala memakai seri pengganti dari arsip WDI. Pilihan ini harus dijelaskan di log dan diperiksa dengan pembimbing pada Sprint 2.

**Paket:** `k12-upah-informalitas.zip` · 10 berkas mentah · snapshot 17 Okt (BPS) dan 20 Okt 2026 (ILOSTAT).

Pemeriksaan rekonsiliasi (tahap 6):
- `var1172` vs `SDG_0851_SEX_OCU_NB`: samakan unit dulu (mata uang, per jam, nominal atau riil).
- `var2153` vs `SDG_0831_SEX_ECO_RT`: periksa cakupan sektor (termasuk atau tanpa pertanian) di kedua sumber.

**Peringatan dari panduan kelompok:** kode SDG, satuan, dan nama seri di katalog awal "belum tentu benar". Periksa terhadap judul tabel dan metadata di berkas mentah. Setiap koreksi dicatat di log.

### 7.2 Hal yang harus diperhatikan

- **Upah dalam rupiah nominal.** Jelaskan apakah dan bagaimana kamu menyesuaikannya dengan inflasi. Indeks bisa dari skrip data pendukung atau seri inflasi di arsip WDI (catat sumbernya).
- **Upah ILO** dalam mata uang lokal dan rincian jabatan berbeda. Samakan unit sebelum membandingkan.
- **Distribusi upah antarprovinsi tidak simetris.** Pilih transformasi yang tepat (misalnya logaritma) dan catat alasannya.
- **Empat seri BPS memakai satuan berbeda** (laju, rupiah, proporsi) di panduan lama. Standarisasi diperlukan sebelum digabung dalam satu judul.
- **Kesalahan yang harus dihindari** (dari panduan kelompok):
  - membandingkan upah nominal antartahun seolah riil;
  - membandingkan informalitas dengan cakupan sektor yang berbeda tanpa catatan;
  - membiarkan tahap skala kosong karena paket tidak memuat WDI.

### 7.3 Jebakan umum (berlaku untuk semua kasus)

- **Wilayah:** jumlah baris provinsi berubah antartahun (33, 34, 35, 38, atau 39 baris). Gabungkan berdasarkan kode, bukan nama. Nama provinsi tidak seragam (contoh: "DI Yogyakarta", "D.I. Yogyakarta", "Daerah Istimewa Yogyakarta").
- **Missing yang tidak terlihat:** seri "lengkap" di tabel panjang bisa bolong setelah dibentuk menjadi grid. Laporkan kelengkapan panel per seri.
- **Dua snapshot BPS:** angka yang sama dari 17 dan 20 Okt bukan duplikat yang salah. Angka yang berbeda adalah revisi. Keduanya disimpan di Silver (`_berkas_raw` termasuk kunci unik), dan pilihannya dicatat di Gold dan log.
- **Periode campur:** seri semesteran dan bulanan tidak dirata-rata ke tahunan di Silver. Agregasi dilakukan di Gold dengan aturan yang tercatat.
- **Patahan definisi** (lonjakan serentak di hampir semua provinsi pada tahun yang sama) biasanya perubahan metode, bukan outlier.

---

## 8. Komponen dan tugas (Kelompok 12)

### 8.1 Lima komponen (satu per anggota)

| # | Komponen | Tahap | Sprint utama | Rubrik bawaan |
|---|---|---|---|---|
| 1 | Ekstraksi dan lineage | 1 | 1 | Ketepatan teknik 40, kualitas eksperimen 35, jejak hasil 25 |
| 2 | Profil dan pembersihan | 2–3 | 1 | sama |
| 3 | Transformasi dan panel | 4 | 1–2 | sama |
| 4 | Integrasi, penyimpanan, dan skala | 5–7 | 2–3 | sama |
| 5 | Validasi dan dokumentasi | 8 | 3 (dimulai sejak Sprint 1) | sama |

### 8.2 Lima tugas sampingan (satu per anggota)

| Tugas | Tanggung jawab |
|---|---|
| Koordinator | Ritme sprint, mengajukan jadwal wawancara, lapor ke pembimbing bila ada anggota berbendera (dua sprint merah berturut-turut) |
| Penjaga Data & Evaluasi | Memastikan data hanya yang disetujui dosen, menjaga protokol evaluasi yang sama untuk semua komponen, dan mengevaluasi data uji tersembunyi sekali di akhir (jika ada) |
| Integrator | Mengelola `main`, menggabungkan pull request, dan memastikan satu perintah mereproduksi seluruh hasil |
| Analis Utama | Memimpin penulisan analisis integrasi/komparasi di laporan tim |
| Reproduksi & Demo | Menyiapkan demo sprint dan menguji reproduksi dari nol di mesin lain |

Komponen dan tugas sampingan yang kamu pilih belum terkonfirmasi di dokumen. Lihat bagian 11.2.

---

## 9. Aturan Workbench dan platform

- **Papan Tim:** kolom sprint (Backlog → Akan dikerjakan → Dikerjakan → Review → Selesai). Hanya pembimbing yang boleh memindahkan ke Selesai. Pecah tugas kecil dengan label komponen, penanggung jawab, dan sprint.
- **Kartu Log Sprint:** tekan chip "log" di kartu namamu. Ketiga kotak (selesai, berikutnya, hambatan) disimpan sekali dan tidak bisa diubah. Log boleh direvisi selama jendela sprint masih terbuka.
- **Bukti kontribusi:** commit dan artefak dari aplikasi tercatat otomatis. Review PR untuk rekan dicatat lewat *Tambah bukti* di panel Log Sprint.
- **Demo Sprint:** tempel tautan rekaman atau unggah berkas MP4/WebM (maks. 50 MB). Kirim baru untuk menggantikan yang lama.
- **Kontrak Tim:** dokumen bersama. Setiap anggota menyunting bagiannya. Perubahan tercatat per orang.
- **Badge:** Sprint Streak (semua sprint hijau), Reviewer Andal (lima review PR bermakna atau lebih), Reproducible (artefak tervalidasi di setiap sprint sejak Sprint 1), Pembela Karya (wawancara dengan pengali ×1,0), Juara Galeri. Badge tampil di Liga dan Rapor Belajar.
- **Liga Capstone:** peringkat lintas kelas dari poin sprint (hijau 10, kuning 4 per anggota; semua anggota hijau +15; demo wajib terunggah +8; tiap pilihan favorit +2). Tidak memengaruhi nilai.
- **Aturan yang sudah kamu setujui:** versi 1, disetujui 5 Nov 2026 pukul 10.05 (tercatat di Workbench).

---

## 10. Pertanyaan wawancara yang perlu disiapkan

Dari panduan kelompok:
1. Bagaimana kamu menyesuaikan upah dengan inflasi, dan dari mana indeksnya?
2. Apa perbedaan cakupan informalitas BPS, ILO, dan WDI?
3. Ambil satu baris Gold dan telusuri sampai ke berkas mentahnya lewat `_berkas_raw` dan `_sha256_raw`.
4. Keputusan mana di `log-keputusan.csv` yang paling banyak mengubah jumlah baris? Apa alternatif yang kamu tolak?

Dari bagian khas pedoman (9.7):
5. Jelaskan selisih terbesar antara seri provinsi dan pembanding nasional. Apakah itu galat atau perbedaan definisi?
6. Bagaimana membedakan outlier dari patahan seri karena perubahan metodologi?
7. Jika data mentah diunduh ulang besok dan satu berkas berubah, bagian pipeline mana yang menangkapnya?

Bank umum (Lampiran A), yang paling sering muncul:
- Tunjukkan satu commit milikmu di folder komponenmu dan jelaskan apa yang berubah.
- Apa satu keputusan desain yang bisa saja salah? Bagaimana kamu mengujinya?
- Ceritakan satu kegagalan (eksperimen, bug, atau pendekatan yang dibuang) dan apa pelajarannya.
- Jika seorang anggota menghilang di Sprint 2, apa yang tim lakukan menurut Kontrak Tim kalian?

---

## 11. Konflik, kekurangan informasi, dan hal yang perlu dikonfirmasi

### 11.1 Ketidaksesuaian antar-dokumen

1. **Ukuran tim:** Pedoman Bab 2.1 menulis "empat sampai lima orang". Pedoman Bab 9.1, panduan tugas besar, dan parameter Workbench menulis **5–7 orang**. Kelompok 12 beranggota 5 orang, jadi tidak berdampak, tetapi perlu diketahui.
2. **Struktur laporan tim:** Pedoman Bab 6.3 dan parameter Workbench (gambar 12.3) menulis enam bagian: Ringkasan, Protokol, Hasil, Analisis, Rekomendasi, Pembagian kerja. Pedoman Bab 9.6 menulis: Ringkasan, Data dan lineage, Masalah data dan penanganannya, Integrasi dan rekonsiliasi, Validasi dan reproduksibilitas, Pembagian kerja. Laporan ini memakai versi Bab 6.3 karena cocok dengan parameter Workbench. **Konfirmasi ke pembimbing.**
3. **Tenggang Sprint 3:** Pedoman menulis "pengumpulan akhir isi main pada 6 Des 23.59" dan juga "Log dan demo masih diterima sampai 23.59 sehari setelah sprint berakhir" (Sprint 3 berakhir Minggu 6 Des). Belum jelas apakah log dan demo Sprint 3 masih diterima sampai Senin 7 Des. **Anggap batas akhir adalah 6 Des 23.59**.
4. **Sprint 2 dalam pedoman:** Tabel 3 menulis "1–2 minggu", sedangkan jadwal tetap 23–29 Nov (satu minggu). Tidak berdampak, hanya catatan.
5. **Lampu hijau Sprint 0:** pedoman mensyaratkan artefak hasil atau review PR, tetapi Sprint 0 tidak memintanya. Konfirmasi ke pembimbing.

### 11.2 Informasi yang belum ada di dokumen

- Komponen dan tugas sampingan kamu. Screenshot Workbench menunjukkan dropdown "Transformasi dan panel" dan "Integrator", tetapi tidak jelas apakah itu pilihanmu.
- Isi Kontrak Tim yang sudah terisi dan yang belum.
- Apakah repo tim sudah dibuat. URL repo tidak ada di dokumen.
- Username GitHub kalian dan apakah akunmu sudah terikat ke Workbench.
- Apakah paket kasus sudah diunduh dan sha256 sudah lolos di laptopmu.
- Spesifikasi laptop dan versi Python (untuk memastikan pipeline selesai dalam 15 menit).
- Jam standup dan kanal komunikasi tim.
- Kesepakatan tim jika ada anggota yang menghilang.

### 11.3 Berkas yang belum sepenuhnya dibaca

- `pedoman-capstone-dw.pdf` (tanpa `_1`): hanya halaman 1–20 dibaca dan terlihat identik dengan `pedoman-capstone-dw_1.pdf`. Halaman 21–70 belum dibaca. Jika ini versi revisi, beri tahu saya.

---

## 12. Contoh cara menghitung nilai

Anggap nilai individu kamu: s1 = 90, s2 = 80, s3 = 83; lampu sprint hijau-kuning-hijau (rata-rata 0,83, faktor 0,97). Tim: s4 = 80, s5 = 90. Pengali wawancara 1,0.

- Individu = (30·90 + 15·80 + 15·83) / 100 = 51,5
- Tim = (25·80 + 15·90) / 100 = 33,5
- Akhir = 51,5 × 1,0 + 33,5 × 0,97 ≈ **84,0**

Jika pengali wawancara turun ke 0,7 (paham sebagian), bagian individu menjadi 51,5 × 0,7 ≈ 36,1, dan nilai akhir turun menjadi sekitar 68,6.
