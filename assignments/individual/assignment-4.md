---
sidebar_label: Tugas 4
sidebar_position: 4
Path: assignments/individual/assignment-4
---

# Tugas 4: Implementasi Autentikasi, Session, dan Cookies pada Django

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Deskripsi Tugas

Pada tugas ini, kamu akan mengimplementasikan konsep *authentication*, *session*, *cookies*, serta menerapkan beberapa konsep yang telah dipelajari selama sesi tutorial.

*Checklist* untuk tugas ini adalah sebagai berikut:

- [ ] Mengimplementasikan fungsi registrasi, login, dan logout untuk memungkinkan pengguna untuk mengakses aplikasi sebelumnya dengan lancar.
- [ ] Membuat **dua** akun pengguna dengan masing-masing **tiga** *dummy data* menggunakan model yang telah dibuat pada aplikasi sebelumnya untuk setiap akun **di lokal**.
- [ ] Menghubungkan model `Product` dengan `User`.
- [ ] Menampilkan detail informasi pengguna yang sedang *logged in* seperti *username* dan menerapkan `cookies` seperti `last login` pada halaman utama aplikasi.
- [ ] Menjawab beberapa pertanyaan berikut pada `README.md` pada *root folder* (silakan modifikasi `README.md` yang telah kamu buat sebelumnya; tambahkan subjudul untuk setiap tugas).
    - [ ] Apa perbedaan antara `HttpResponseRedirect()` dan `redirect()`
    - [ ] Jelaskan cara kerja penghubungan model `Product` dengan `User`!
    - [ ] Apa perbedaan antara *authentication* dan *authorization*, apakah yang dilakukan saat pengguna login? Jelaskan bagaimana Django mengimplementasikan kedua konsep tersebut.
    - [ ] Bagaimana Django mengingat pengguna yang telah login? Jelaskan kegunaan lain dari *cookies* dan apakah semua cookies aman digunakan?
    - [ ] Jelaskan bagaimana cara kamu mengimplementasikan *checklist* di atas secara *step-by-step* (bukan hanya sekadar mengikuti tutorial).
- [ ] Melakukan `add`-`commit`-`push` ke GitHub.

## Tenggat Waktu Pengerjaan

Tenggat waktu pengerjaan Tugas 4 adalah **Rabu, 25 September 2023, pukul 12.00 siang**.

Asisten dosen akan mengecek *last commit* dari repositori tugas lab, sehingga kamu tidak perlu mengumpulkan tautan repositori ke dalam slot submisi.
