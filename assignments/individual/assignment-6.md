---
sidebar_label: Tugas 6
sidebar_position: 6
Path: assignments/individual/assignment-6
---

# Tugas 6: JavaScript dan AJAX

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Deskripsi Tugas

Pada tugas ini, kamu akan mengimplementasikan AJAX pada aplikasi yang telah kamu buat pada tugas sebelumnya.

*Checklist* untuk tugas ini adalah sebagai berikut:
- [ ] Mengubah tugas 5 yang telah dibuat sebelumnya menjadi menggunakan AJAX.
    - [ ] AJAX `GET`
        - [ ] Ubahlah kode `cards` data _mood_ agar dapat mendukung AJAX `GET`.
        - [ ] Lakukan pengambilan data _mood_ menggunakan AJAX `GET`. Pastikan bahwa data yang diambil hanyalah data milik pengguna yang _logged-in_.
    - [ ] AJAX `POST`
        - [ ] Buatlah sebuah tombol yang membuka sebuah modal dengan form untuk menambahkan _mood_.
            :::note
            Modal di-_trigger_ dengan menekan suatu tombol pada halaman utama. Saat penambahan _mood_ berhasil, modal harus ditutup dan _input_ form harus dibersihkan dari data yang sudah dimasukkan ke dalam form sebelumnya. Jika penambahan gagal, tampilkan pesan _error_.
            :::
        - [ ] Buatlah fungsi _view_ baru untuk menambahkan _mood_ baru ke dalam basis data.
        - [ ] Buatlah _path_ `/create-ajax/` yang mengarah ke fungsi _view_ yang baru kamu buat.
        - [ ] Hubungkan form yang telah kamu buat di dalam modal kamu ke _path_ `/create-ajax/`.
        - [ ] Lakukan _refresh_ pada halaman utama secara asinkronus untuk menampilkan daftar _mood_ terbaru tanpa reload halaman utama secara keseluruhan.
    :::warning
    Pastikan AJAX `GET` dan `POST` dapat dilakukan secara aman.
    :::

- [ ] Menjawab beberapa pertanyaan berikut pada `README.md` pada *root folder* (silakan modifikasi `README.md` yang telah kamu buat sebelumnya; tambahkan subjudul untuk setiap tugas).
    - [ ] Jelaskan manfaat dari penggunaan JavaScript dalam pengembangan aplikasi web!
    - [ ] Jelaskan fungsi dari penggunaan `await` ketika kita menggunakan `fetch()`! Apa yang akan terjadi jika kita tidak menggunakan `await`?
    - [ ] Mengapa kita perlu menggunakan _decorator_ `csrf_exempt` pada _view_ yang akan digunakan untuk AJAX `POST`?
    - [ ] Pada tutorial PBP minggu ini, pembersihan data _input_ pengguna dilakukan di belakang (_backend_) juga. Mengapa hal tersebut tidak dilakukan di _frontend_ saja?
    - [ ] Jelaskan bagaimana cara kamu mengimplementasikan *checklist* di atas secara *step-by-step* (bukan hanya sekadar mengikuti tutorial)!
- [ ] Melakukan `add`-`commit`-`push` ke GitHub.

## Tenggat Waktu Pengerjaan

Tenggat waktu pengerjaan Tugas 6 adalah **Rabu, 9 Oktober 2024, pukul 12.00 siang**.

Asisten dosen akan mengecek *last commit* dari repositori tugas lab, sehingga kamu tidak perlu mengumpulkan tautan repositori ke dalam slot submisi.
