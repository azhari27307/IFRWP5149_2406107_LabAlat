## Tugas Praktik: Sistem Informasi Akademik, Layanan Hasil Studi

Tugas ini berbeda dari tugas pertemuan sebelumnya. Tugas Pertemuan 2
adalah jadwal kuliah dan tugas Pertemuan 3 adalah pengajuan KRS. Tugas
Pertemuan 4 adalah layanan hasil studi, dengan teknik generalization dan
collaboration yang sama seperti studi kasus, tetapi diterapkan pada skenario
baru tanpa contoh jawaban.
Skenario tugas berikut fiktif untuk praktikum dan berbeda dari tugas
Pertemuan 2 (jadwal kuliah) dan Pertemuan 3 (pengajuan KRS).
Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang
dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang
diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu
Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin
Akademik mengelola data mahasiswa: menambah data mahasiswa baru,
mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case
utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh
collaboration yang bersesuaian.

## Batas dan asumsi

- Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap mempunyai identitas berbeda.
- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Kalender akademik pada tugas ini adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya); jangan menyamakannya dengan jadwal kuliah pada Pertemuan 2.
- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Ketentuan ini fiktif untuk latihan.
- Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari Pertemuan 3. Pembayaran dan perancangan basis data berada di luar tugas ini.

# 2. Identifikasi Aktor dan Use Case

## Identifikasi Aktor

| No. | Aktor | Jenis Aktor | Deskripsi |
|---:|---|---|---|
| 1 | Civitas Akademika | Aktor umum | Mewakili pengguna dari kelompok civitas akademika yang dapat melihat kalender akademik. |
| 2 | Mahasiswa | Aktor khusus | Dapat melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pengajuan KRS, melihat kalender akademik, dan melihat KHS yang nilainya telah dipublikasikan. |
| 3 | Dosen | Aktor khusus | Dapat melihat kalender akademik dan menginput nilai mata kuliah yang diajarnya. |
| 4 | Admin Akademik | Aktor | Dapat mengelola jadwal kuliah serta menambah, mengubah, dan menghapus data mahasiswa sesuai ketentuan. |
| 5 | Dosen Wali | Aktor | Dapat memproses persetujuan atau penolakan KRS serta memberikan catatan keputusan. |

### Generalisasi Aktor

Mahasiswa dan Dosen merupakan aktor khusus dari Civitas Akademika. Generalisasi ini menunjukkan bahwa kedua aktor tersebut mewarisi hubungan dengan use case umum yang dimiliki Civitas Akademika.

Pada diagram use case, generalisasi digambarkan menggunakan garis solid dengan ujung segitiga kosong yang mengarah ke aktor umum, yaitu Civitas Akademika.

## Katalog Gabungan Use Case

Katalog use case disusun secara kumulatif dengan mempertahankan use case dari Pertemuan 2 dan Pertemuan 3, kemudian menambahkan use case baru dari Pertemuan 4.

| ID | Nama Use Case | Aktor Terkait | Sumber Kebutuhan | Status |
|---|---|---|---|---|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | SIA-R01, Pertemuan 2 | Tetap |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R02, Pertemuan 2 | Tetap |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03, Pertemuan 3 | Tetap |
| SIA-UC04 | Validasi KRS | Proses internal sistem, dipanggil oleh Ajukan KRS | SIA-R04, Pertemuan 3 | Tetap |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | SIA-R05, Pertemuan 3 | Tetap |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R06, Pertemuan 3 | Tetap |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika | SIA-R07, Pertemuan 4 | Baru |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen | SIA-R08, Pertemuan 4 | Baru |
| SIA-UC09 | Lihat KHS | Mahasiswa | SIA-R09, Pertemuan 4 | Baru |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik | SIA-R10, Pertemuan 4 | Baru |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik | SIA-R11, Pertemuan 4 | Baru |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik | SIA-R11, Pertemuan 4 | Baru |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik | SIA-R11, Pertemuan 4 | Baru |

## Tetapkan Generalization Aktor

- Mahasiswa adalah bentuk khusus dari Civitas Akademika, dan Dosen juga merupakan bentuk khusus dari Civitas Akademika. Alasannya, keduanya memiliki fungsi yang sama, yaitu melihat kalender akademik.
- Asosiasi ke SIA-UC07 Lihat Kalender Akademik digambar satu kali dari Civitas Akademika. Jangan menggambar garis yang sama lagi dari Mahasiswa dan Dosen.
- Fungsi khusus Mahasiswa dan Dosen tetap dihubungkan langsung ke aktor masing-masing, seperti Mahasiswa ke SIA-UC09 Lihat KHS dan Dosen ke SIA-UC08 Input Nilai Mata Kuliah.
- Arah panah generalisasi menggunakan segitiga kosong yang mengarah ke Civitas Akademika, bukan ke Mahasiswa atau Dosen.

## Tetapkan Generalization Use Case

- SIA-UC11 Tambah Data Mahasiswa, SIA-UC12 Ubah Data Mahasiswa, dan SIA-UC13 Hapus Data Mahasiswa adalah bentuk khusus dari SIA-UC10 Kelola Data Mahasiswa. Alasannya, ketiganya merupakan bagian dari pengelolaan data mahasiswa.
- Tuliskan perilaku pembeda setiap use case khusus:
  - Tambah Data Mahasiswa: menghasilkan data mahasiswa baru.
  - Ubah Data Mahasiswa: menghasilkan data mahasiswa yang telah diperbarui.
  - Hapus Data Mahasiswa: menghapus data mahasiswa yang tidak memiliki data akademik aktif.

  ## Tetapkan Collaboration

- SIA-CO01 — Input Nilai Mata Kuliah merealisasikan use case SIA-UC08 Input Nilai Mata Kuliah.
- SIA-CO02 — Lihat KHS merealisasikan use case SIA-UC09 Lihat KHS.


## Susun Use Case Description

### SIA-UC08: Input Nilai Mata Kuliah

| Elemen | Deskripsi |
|---|---|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 |
| Tujuan | Menyimpan nilai mahasiswa untuk mata kuliah yang diajar dosen. |
| Aktor utama | Dosen |
| Pemicu | Dosen memilih fungsi input nilai mata kuliah. |
| Prasyarat | Dosen telah terautentikasi dan merupakan pengampu mata kuliah yang dipilih. |
| Pascakondisi berhasil | Nilai berhasil disimpan dan belum ditampilkan pada KHS sebelum dipublikasikan. |
| Pascakondisi gagal | Nilai tidak berhasil disimpan atau data nilai sebelumnya tidak berubah. |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |

Alur utama

| Langkah | Tindakan Dosen | Respons Sistem |
|---|---|---|
| 1 | Memilih mata kuliah yang diajar. | Menampilkan daftar mahasiswa pada mata kuliah tersebut. |
| 2 | Memasukkan nilai mahasiswa. | Menerima nilai yang dimasukkan. |
| 3 | Mengonfirmasi penyimpanan nilai. | Memeriksa hak akses dosen dan rentang nilai. |
| 4 | Menyimpan nilai. | Menyimpan nilai dan menampilkan konfirmasi berhasil. |

Alur alternatif atau pengecualian

- A1: Dosen bukan pengampu mata kuliah. Sistem menolak input nilai dan tidak menyimpan perubahan.
- A2: Nilai di luar rentang yang sah. Sistem menolak nilai tersebut dan menampilkan pesan kesalahan. Nilai tidak disimpan sampai diperbaiki.

### SIA-UC09: Lihat KHS

| Elemen | Deskripsi |
|---|---|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 |
| Tujuan | Menampilkan Kartu Hasil Studi mahasiswa. |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi Lihat KHS. |
| Prasyarat | Mahasiswa telah terautentikasi. |
| Pascakondisi berhasil | KHS ditampilkan dengan nilai yang sudah dipublikasikan. |
| Pascakondisi gagal | KHS tidak dapat ditampilkan dan sistem memberikan informasi yang sesuai. |
| Collaboration | SIA-CO02: Lihat KHS |

Alur utama

| Langkah | Tindakan Mahasiswa | Respons Sistem |
|---|---|---|
| 1 | Memilih semester yang ingin dilihat. | Memeriksa ketersediaan KHS semester tersebut. |
| 2 | Melihat KHS. | Menampilkan nilai yang sudah dipublikasikan. |

**Alur alternatif atau pengecualian**

- **A1: Nilai belum dipublikasikan.** Sistem tidak menampilkan nilai tersebut pada KHS.
- **A2: KHS belum tersedia.** Sistem menampilkan informasi bahwa KHS belum tersedia untuk semester yang dipilih.