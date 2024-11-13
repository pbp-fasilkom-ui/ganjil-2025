---
sidebar_label: Tugas 9
sidebar_position: 9
Path: assignment/individual/assignment-9
---

# Tugas 9: Integrasi Layanan Web Django dengan Aplikasi Flutter

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Deskripsi Tugas

Pada tugas ini, kamu akan mengintegrasikan layanan Django yang sudah kamu buat pada tugas-tugas sebelumnya dengan aplikasi Flutter yang sudah kamu buat sebelumnya.

*Checklist* untuk tugas ini adalah sebagai berikut:

- [ ] Memastikan *deployment* proyek tugas Django kamu telah berjalan dengan baik.
:::note
Untuk masalah terkait PWS yang belum bisa diintegrasikan dengan Flutter, Tim Asdos akan menginformasikan secara menyusul. Untuk sementara, kalian diperbolehkan untuk melakukan integrasi pada _local host_ saja.
:::
- [ ] Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.
- [ ] Membuat halaman login pada proyek tugas Flutter.
- [ ] Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.
- [ ] Membuat model kustom sesuai dengan proyek aplikasi Django.
- [ ] Membuat halaman yang berisi daftar semua item yang terdapat pada *endpoint* `JSON` di Django yang telah kamu *deploy*.
    - [ ] Tampilkan *name*, *price*, dan *description* dari masing-masing item pada halaman ini.
- [ ] Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.
    - [ ] Halaman ini dapat diakses dengan menekan salah satu item pada halaman daftar Item.
    - [ ] Tampilkan seluruh atribut pada model item kamu pada halaman ini.
    - [ ] Tambahkan tombol untuk kembali ke halaman daftar item.
- [ ] Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login.
- [ ] Menjawab beberapa pertanyaan berikut pada `README.md` pada *root folder* (silakan modifikasi `README.md` yang telah kamu buat sebelumnya; tambahkan subjudul untuk setiap tugas).
    - [ ] Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?
    - [ ] Jelaskan fungsi dari library _http_ yang sudah kamu implementasikan pada tugas ini
    - [ ] Jelaskan fungsi dari CookieRequest dan jelaskan mengapa *instance* CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
    - [ ] Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
    - [ ] Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
    - [ ] Jelaskan bagaimana cara kamu mengimplementasikan *checklist* di atas secara *step-by-step*! (bukan hanya sekadar mengikuti tutorial).
- [ ] Melakukan `add`-`commit`-`push` ke GitHub.

## Tenggat Waktu Pengerjaan

Tenggat waktu pengerjaan Tugas 9 adalah **Rabu, 20 November 2024, pukul 12.00 siang**.

Asisten dosen akan mengecek *last commit* dari repositori tugas lab, sehingga kamu tidak perlu mengumpulkan tautan repositori ke dalam slot submisi.

