## Skenario

Mahasiswa mengajukan peminjaman peralatan dengan memilih alat,
jumlah, dan rentang waktu. Sistem memeriksa ketersediaan. Jika
tersedia dan data lengkap, sistem menyimpan pengajuan berstatus
menunggu keputusan. Pada tampilan konfirmasi, mahasiswa dapat
memilih mencetak bukti pengajuan. Petugas mengelola data peralatan
serta menyetujui atau menolak pengajuan. Kepala laboratorium melihat
laporan peminjaman.


| ID Kebutuhan | Deskripsi Kebutuhan |
|---|---|
| LAB-R01 | Mahasiswa dapat melihat ketersediaan peralatan. |
| LAB-R02 | Petugas dapat mengelola data peralatan. |
| LAB-R03 | Mahasiswa dapat mengajukan peminjaman; sistem memeriksa ketersediaan sebelum menyimpan pengajuan. |
| LAB-R04 | Mahasiswa dapat mencetak bukti pada konfirmasi pengajuan jika memilihnya. |
| LAB-R05 | Petugas dapat menetapkan persetujuan atau penolakan pengajuan. |
| LAB-R06 | Kepala laboratorium dapat melihat laporan peminjaman. |

## Batas Sistem dan Aturan

1. Sistem mencatat dan menyediakan informasi. Perpindahan fisik peralatan tidak terjadi di dalam perangkat lunak.
2. Pengguna telah terautentikasi dan memiliki hak akses sesuai dengan perannya.
3. Pengajuan yang diterima oleh sistem berstatus **Menunggu Keputusan**, bukan otomatis **Disetujui**.
4. Pengajuan dengan peralatan yang tidak tersedia tidak disimpan sebagai pengajuan yang berhasil.
5. Pencetakan bukti tidak menjadi syarat keberhasilan pengajuan peminjaman.
6. Persetujuan oleh petugas belum dimodelkan sebagai reservasi teknis stok.
7. Proses pengambilan, pengembalian, pemeriksaan kondisi peralatan, dan pengenaan denda belum dianalisis dalam model ini.

## Tentukan Actor

| Aktor | Tujuan terhadap Sistem |
|---|---|
| Mahasiswa | Melihat ketersediaan peralatan, mengajukan peminjaman, dan mencetak bukti . |
| Petugas Laboratorium | Mengelola data peralatan dan memproses keputusan . |
| Kepala Laboratorium | Melihat laporan peminjaman. |