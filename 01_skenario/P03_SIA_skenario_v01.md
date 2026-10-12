## Skenario
Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap
pengajuan menjalankan validasi KRS yang memeriksa kelengkapan,
prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil,
sistem menyimpan pengajuan berstatus menunggu persetujuan dosen
wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih
mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS
dan memberikan catatan keputusan.

| ID Kebutuhan | Tugas |
|---|---|
| SIA-R01 | Mahasiswa dapat melihat jadwal kuliah |
| SIA-R02 | Admin akademik dapat mengelola jadwal kuliah |
| SIA-R03 | Mahasiswa dapat mengajukan KRS |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS |

## Batas dan Asumsi

1. Pengguna telah terautentikasi.
2. Data mata kuliah, prasyarat, dan jadwal tersedia.
3. Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
4. Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
5. KRS tersimpan belum berarti disetujui.
6. Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas.

## Tentukan Actor dan Kebutuhan

| Aktor | Kebutuhan |
|---|---|
| Mahasiswa | Dapat melihat jadwal kuliah, mengajukan KRS, mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| Admin Akademik | Mengelola jadwal kuliah |
| Dosen Wali | Memproses persetujuan atau penolakan KRS |

