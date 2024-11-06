---
sidebar_label: Tugas 8
sidebar_position: 8
Path: assignment/individual/assignment-8
---

# Tugas 8: Flutter Navigation, Layouts, Forms, and Input Elements

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Genap 2024/2025

---

## Deskripsi Tugas

Pada tugas ini, kamu akan mengimplementasikan *navigation*, *layout*, *form*, dan *form input elements* pada aplikasi Flutter yang kamu buat pada tugas sebelumnya.

*Checklist* untuk tugas ini adalah sebagai berikut:

- [ ] Membuat minimal satu halaman baru pada aplikasi, yaitu halaman formulir tambah item baru dengan ketentuan sebagai berikut:
	- [ ] Memakai minimal tiga elemen input, yaitu `name`, `amount`, `description`. Tambahkan elemen input sesuai dengan model pada aplikasi tugas Django yang telah kamu buat.
    - [ ] Memiliki sebuah tombol `Save`.
    - [ ] Setiap elemen input di formulir juga harus divalidasi dengan ketentuan sebagai berikut:
        - [ ] Setiap elemen input tidak boleh kosong.
        - [ ] Setiap elemen input harus berisi data dengan tipe data atribut modelnya.
        ::::warning
        Perhatikan *case-case* seperti angka negatif, panjang *string* minimum (jika ada), panjang *string* maksimum (jika ada), dan lain sebagainya. Tidak hanya tipe datanya saja!
        ::::
- [ ] Mengarahkan pengguna ke halaman form tambah item baru ketika menekan tombol `Tambah Item` pada halaman utama.
- [ ] Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah `pop-up` setelah menekan tombol `Save` pada halaman formulir tambah item baru.
- [ ] Membuat sebuah drawer pada aplikasi dengan ketentuan sebagai berikut:
    - [ ] Drawer minimal memiliki dua buah opsi, yaitu `Halaman Utama` dan `Tambah Item`.
    - [ ] Ketika memiih opsi `Halaman Utama`, maka aplikasi akan mengarahkan pengguna ke halaman utama.
    - [ ] Ketika memiih opsi `Tambah Item`, maka aplikasi akan mengarahkan pengguna ke halaman form tambah item baru.
- [ ] Menjawab beberapa pertanyaan berikut pada `README.md` pada *root folder* (silakan modifikasi `README.md` yang telah kamu buat sebelumnya; tambahkan subjudul untuk setiap tugas).
    - [ ] Apa kegunaan `const` di Flutter? Jelaskan apa keuntungan ketika menggunakan `const` pada kode Flutter. Kapan sebaiknya kita menggunakan `const`, dan kapan sebaiknya tidak digunakan?
    - [ ] Jelaskan dan bandingkan penggunaan *Column* dan *Row* pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
    - [ ] Sebutkan apa saja elemen input yang kamu gunakan pada halaman *form* yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!
    - [ ] Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
    - [ ] Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?
- [ ] Melakukan `add`-`commit`-`push` ke GitHub.

## Tenggat Waktu Pengerjaan

Tenggat waktu pengerjaan Tugas 8 adalah **Rabu, 13 November 2024, pukul 12.00 siang**.

Asisten dosen akan mengecek *last commit* dari repositori tugas lab, sehingga kamu tidak perlu mengumpulkan tautan repositori ke dalam slot submisi.