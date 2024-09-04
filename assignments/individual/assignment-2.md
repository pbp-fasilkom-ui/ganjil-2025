---
sidebar_label: Tugas 2
sidebar_position: 1
Path: docs/tugas-2
---

# Tugas 2: Implementasi *Model-View-Template* (MVT) pada Django

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Deskripsi Tugas

Pada tugas ini, kamu akan mengimplementasikan konsep *Model-View-Template* serta beberapa hal yang sudah kamu pelajari di kelas dan tutorial. Perlu diperhatikan bahwa proyek yang dibuat pada tugas **berbeda** dengan proyek yang digunakan pada tutorial.

## Tema Aplikasi

Tema besar aplikasi untuk tugas PBP adalah aplikasi *E-Commerce*. Kamu diberikan kebebasan dalam memilih nama dan tema kecil aplikasi. Buatlah tugasmu sekreatif mungkin.

:::danger
Pastikan nama dan konten dari tugasmu **TIDAK** mengandung unsur **NSFW/18+** dan menyinggung SARA. Apabila aturan ini dilanggar, ada kemungkinan terjadi konsekuensi yang berpotensi mempengaruhi mata kuliah lain nantinya, misalnya seperti akun GitHub yang diblokir.
:::

Aplikasi dari tugas kamu harus memiliki atribut-atribut berikut pada modelnya.

- `name` sebagai nama *item* dengan tipe `CharField`.
- `price` sebagai harga *item* dengan tipe `IntegerField`.
- `description` sebagai deskripsi *item* dengan tipe `TextField`.

Kamu dipersilakan untuk menambahkan atribut lainnya jika diinginkan, seperti `stock`, `category`, `image`, dan lain-lain. Namun, model aplikasi kamu wajib memiliki ketiga atribut wajib di atas (`name`, `price`, `description`). Nama dari ketiga atribut di atas dapat disesuaikan lagi dengan kebutuhan aplikasimu.

Beberapa contoh ide aplikasi pengelolaan yang dapat kamu buat adalah sebagai berikut.

- *e-shop*: `nama`, `harga`, `description`, `rating`, `date`.
- *Coquette Shop*: `name`, `price`, `description`, `coquette-ness`.
- Toko Ijo: `name`, `price`, `description`, `quantity`.

## Checklist Tugas

*Checklist* untuk tugas ini adalah sebagai berikut.

- [ ] Membuat sebuah proyek Django baru.
- [ ] Membuat aplikasi dengan nama `main` pada proyek tersebut.
- [ ] Melakukan *routing* pada proyek agar dapat menjalankan aplikasi `main`.
- [ ] Membuat model pada aplikasi `main` dengan nama `Product` dan memiliki atribut wajib sebagai berikut.
    - `name`
    - `price`
    - `description`
- [ ] Membuat sebuah fungsi pada `views.py` untuk dikembalikan ke dalam sebuah *template* HTML yang menampilkan nama aplikasi serta nama dan kelas kamu.
- [ ] Membuat sebuah *routing* pada `urls.py` aplikasi `main` untuk memetakan fungsi yang telah dibuat pada `views.py`.
- [ ] Melakukan *deployment* ke PWS terhadap aplikasi yang sudah dibuat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet.
- [ ] Membuat sebuah `README.md` yang berisi tautan menuju aplikasi PWS yang sudah di-*deploy*, serta jawaban dari beberapa pertanyaan berikut.
    - Jelaskan bagaimana cara kamu mengimplementasikan *checklist* di atas secara *step-by-step* (bukan hanya sekadar mengikuti tutorial).
    - Buatlah bagan yang berisi *request client* ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara `urls.py`, `views.py`, `models.py`, dan berkas `html`.
    - Jelaskan fungsi `git` dalam pengembangan perangkat lunak!
    - Menurut Anda, dari semua framework yang ada, mengapa framework Django dijadikan permulaan pembelajaran pengembangan perangkat lunak?
    - Mengapa model pada Django disebut sebagai *ORM*?

Perhatikan bahwa kamu harus mengerjakan tugas ini menggunakan repositori yang **berbeda** dengan tutorial.

## Tenggat Waktu Pengerjaan

Tenggat waktu pengerjaan Tugas 2 adalah hari **Rabu, 11 September, pukul 12.00 siang.**

Harap mengumpulkan link repositori yang kamu gunakan ke dalam slot submisi yang telah disediakan di SCELE.

