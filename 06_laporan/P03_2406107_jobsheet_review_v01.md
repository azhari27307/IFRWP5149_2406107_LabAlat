## Menentukan Relasi `include`

**Relasi yang digunakan:**

`SIA-UC01 — Ajukan KRS` `<<include>>` `SIA-UC02 — Validasi KRS`

- **Sumber kebutuhan:** SIA-R03 dan SIA-R04.
- **Alasan:** Setiap pengajuan KRS harus melalui proses validasi sebelum dapat disimpan.
- **Arah panah:** Dari SIA-UC01 (Ajukan KRS) menuju SIA-UC02 (Validasi KRS).

## 4. Menentukan Relasi `extend`

**Relasi yang digunakan:**

`SIA-UC03 — Unduh Bukti Pengajuan KRS` `<<extend>>` `SIA-UC01 — Ajukan KRS`

- **Use case dasar:** SIA-UC01 — Ajukan KRS.
- **Use case tambahan:** SIA-UC03 — Unduh Bukti Pengajuan KRS.
- **Sumber kebutuhan:** SIA-R05.
- **Extension point:** Bukti pengajuan tersedia, setelah sistem berhasil menyimpan KRS dan menampilkan konfirmasi.
- **Kondisi:** `[mahasiswa memilih unduh bukti]`.
- **Alasan:** Pengajuan KRS tetap berhasil meskipun mahasiswa tidak mengunduh bukti.
- **Arah panah:** Dari SIA-UC03 (Unduh Bukti Pengajuan KRS) menuju SIA-UC01 (Ajukan KRS).

### A. SIA-UC01 — Ajukan KRS

**Sumber kebutuhan:** SIA-R03 dan SIA-R05, dengan validasi SIA-R04.

| Elemen | Deskripsi |
|---|---|
| ID dan nama | SIA-UC01 — Ajukan KRS |
| Tujuan | Menghasilkan pengajuan KRS yang tersimpan dengan status menunggu persetujuan dosen wali. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Tidak ada aktor pendukung langsung yang ditetapkan untuk pengajuan. |
| Pemicu | Mahasiswa memilih fungsi pengajuan KRS. |
| Prasyarat | Mahasiswa telah terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia. |
| Include | SIA-UC02 — Validasi KRS. |
| Extension point | Bukti pengajuan tersedia, setelah penyimpanan berhasil dan konfirmasi ditampilkan. |
| Extend | SIA-UC03 — Unduh bukti pengajuan KRS, jika `[mahasiswa memilih unduh bukti]`. |
| Pascakondisi berhasil | Pengajuan tersimpan dan berstatus Menunggu Persetujuan Dosen Wali. |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan. |

### B. SIA-UC02 — Validasi KRS

**Sumber kebutuhan:** SIA-R04.

| Elemen | Deskripsi |
|---|---|
| ID dan nama | SIA-UC02 — Validasi KRS |
| Tujuan | Memastikan pengajuan KRS memenuhi pemeriksaan yang ditentukan. |
| Aktor utama | Tidak ada aktor manusia yang memulai secara langsung; use case ini disertakan oleh SIA-UC01. |
| Aktor pendukung | Tidak ada yang ditetapkan. |
| Pemicu | SIA-UC01 mencapai tahap validasi pengajuan. |
| Prasyarat | Pengajuan KRS sedang diproses; data mata kuliah, prasyarat, dan jadwal tersedia. |
| Pascakondisi berhasil | Hasil validasi menyatakan pengajuan memenuhi pemeriksaan sehingga dapat disimpan oleh SIA-UC01. |
| Pascakondisi gagal | Hasil validasi menyatakan pengajuan tidak memenuhi pemeriksaan dan tidak berhasil disimpan. |


### C. SIA-UC03 — Unduh Bukti Pengajuan KRS

**Sumber kebutuhan:** SIA-R05.

| Elemen | Deskripsi |
|---|---|
| ID dan nama | SIA-UC03 — Unduh Bukti Pengajuan KRS |
| Tujuan | Memberikan bukti pengajuan KRS kepada mahasiswa. |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Tidak ada yang ditetapkan. |
| Pemicu | Mahasiswa memilih unduh bukti pada konfirmasi pengajuan yang berhasil disimpan. |
| Prasyarat | Pengajuan KRS berhasil tersimpan dan konfirmasi pengajuan ditampilkan. |
| Relasi | `<<extend>>` SIA-UC01 — Ajukan KRS. |
| Kondisi | `[mahasiswa memilih unduh bukti]` |
| Extension point | Bukti pengajuan tersedia, setelah sistem berhasil menyimpan KRS dan menampilkan konfirmasi. |
| Pascakondisi berhasil | Bukti pengajuan tersedia untuk diunduh oleh mahasiswa. |
| Pascakondisi gagal | Bukti tidak berhasil diunduh; status pengajuan KRS yang telah tersimpan tidak berubah akibat kegagalan unduh. |

### D. SIA-UC04 — Proses Keputusan KRS

**Sumber kebutuhan:** SIA-R06.

| Elemen | Deskripsi |
|---|---|
| ID dan nama | SIA-UC04 — Proses Keputusan KRS |
| Tujuan | Mencatat keputusan persetujuan atau penolakan terhadap pengajuan KRS. |
| Aktor utama | Dosen wali |
| Aktor pendukung | Tidak ada yang ditetapkan. |
| Pemicu | Dosen wali memilih fungsi pemrosesan keputusan KRS. |
| Prasyarat | Pengajuan KRS telah tersimpan dan menunggu persetujuan dosen wali; dosen wali telah terautentikasi. |
| Pascakondisi berhasil | Keputusan persetujuan atau penolakan dan catatan keputusan tersimpan. |
| Pascakondisi gagal | Keputusan belum berhasil diproses atau disimpan. |

## 7. Uji Konsistensi Diagram dan Deskripsi

Modul meminta tiga situasi untuk memastikan hasil diagram sesuai dengan deskripsi *use case*.

| Situasi Pengujian | Hasil yang Seharusnya | Konsisten? |
|---|---|---|
| A. Validasi berhasil dan mahasiswa tidak mengunduh bukti | KRS tersimpan dengan status Menunggu Persetujuan Dosen Wali. SIA-UC03 tidak dijalankan. | Ya |
| B. Validasi gagal | KRS belum berhasil tersimpan. Sistem menyampaikan kegagalan validasi. | Ya |
| C. Validasi berhasil dan mahasiswa memilih mengunduh bukti | KRS tersimpan dengan status menunggu persetujuan, kemudian SIA-UC03 dijalankan untuk mengunduh bukti. | Ya |

### Penjelasan Hasil Pengujian

1. **Situasi A:** Relasi `include` tetap dijalankan karena validasi wajib dilakukan. Relasi `extend` tidak dijalankan karena mahasiswa tidak memilih opsi unduh bukti.

2. **Situasi B:** Validasi tetap menjadi bagian dari proses pengajuan KRS. Namun, hasil validasi yang gagal menyebabkan pengajuan tidak berhasil disimpan.

3. **Situasi C:** Validasi berhasil sehingga pengajuan KRS tersimpan. Karena kondisi `extend` terpenuhi, proses unduh bukti dapat dijalankan tanpa mengubah status dasar pengajuan.