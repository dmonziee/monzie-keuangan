# Rekapan Monzie

Aplikasi rekapan transaksi **pemasukan & pengeluaran mingguan** — statis (HTML/CSS/JS saja, tanpa backend).

- 🌐 Live: https://monzie.is-a.dev (setelah PR is-a.dev di-merge) — sementara: https://dmonziee.github.io/monzie-keuangan/
- 📱 APK Android: `Rekapan-Monzie-1.0.apk` (WebView, paket `app.monzie.keuangan`)

## Fitur

- Rekap mingguan (Senin–Minggu): total pemasukan, pengeluaran, saldo, grafik per hari, daftar per hari
- Navigasi minggu (sebelum/berikutnya, lompat tanggal, "Minggu Ini")
- Filter tipe/kategori + cari catatan
- **Publik (tanpa login):** hanya memantau — lihat rekap, total, daftar, grafik
- **Admin:** login `admin` / `monzie123` (ganti di Pengaturan setelah login pertama) — tambah/edit/hapus transaksi, export/import JSON, export CSV, hapus data contoh

## Data

Data tersimpan di perangkat (localStorage browser, key `monzie-keuangan-v1`). **Belum ada sinkronisasi server** — entri admin di satu perangkat tidak otomatis terlihat di perangkat lain. Untuk berbagi, admin bisa export JSON/CSV.

Data contoh minggu 23–29 Nov 2026 disertakan saat pertama kali dibuka dan bisa dihapus admin di Pengaturan.
