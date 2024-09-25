---
sidebar_label: Proyek Tengah Semester
sidebar_position: 1
Path: assignments/group/midterm
---

# Proyek Tengah Semester

**Membuat Situs Web menggunakan Framework Django (Berkelompok)**

---

## Tujuan Pembelajaran Khusus

1. Merancang Halaman Web
2. Mengimplementasikan situs web menggunakan *framework* Django dengan memenuhi *Models*, *Views*, dan *Template*
3. Memanfaatkan *framework* CSS untuk mewujudkan *Responsive Web Design*
4. Mengimplementasikan *Unit Test* dan *deployment*

## Aturan Umum Tugas Kelompok

1. Satu kelompok terdiri atas 5-6 orang. Pembagian kelompok sudah dapat dilihat di SCELE.
2. Satu kelompok membuat satu repositori Git (Git _repository_) yang digunakan oleh seluruh anggota kelompok untuk bekerja sama. Kumpulkan tautan repositori Git ke SCELE.  
:::tip  
Setiap kelompok disarankan untuk menggunakan GitHub Organizations untuk mempermudah kolaborasi antar anggota tim. Selain itu, untuk TK Proyek Akhir Semester, setiap kelompok nanti akan diminta untuk membuat repositori baru, dan GitHub Organizations dapat membantu 'pengelompokan' repositori-repositori ini.  
:::  
3. Setiap kelompok dipersilakan untuk mencari ide sendiri mengenai aplikasi yang akan dibuat. Tema aplikasi adalah **informasi seputar produk di sebuah kota**. Tema ini dipilih karena terinspirasi ibu kota baru, IKN (Ibu Kota Nusantara). Jika kita pindah atau berkunjung ke kota yang baru pertama kali kita datangi dan kemudian kita ingin membeli sebuah produk di kota itu, kita mungkin belum tahu toko mana yang menjual produk tersebut di kota itu dan kita membutuhkan sebuah aplikasi yang menyediakan informasi seputar produk tersebut di kota itu.
4. Untuk tugas kelompok PBP ini, setiap kelompok dibebaskan memilih kota yang menjadi basis lokasi aplikasi kelompok, misalnya Kota Depok.
5. Setiap kelompok harus menentukan kategori utama produk yang menjadi _initial dataset_ aplikasi kelompok. Kategori utama produk harus berisi minimal 100 jenis produk. Contoh: 
    - Jika kategori utama produk adalah _laptop_ & _handphone_ maka di _initial dataset_ harus ada minimal 100 merek dan tipe laptop & handphone. 
    - Jika kategori utama produk adalah makanan & minuman maka di _initial dataset_ harus ada minimal 100 macam makanan & minuman. 
    - Jika kategori utama produk adalah buku maka di _initial dataset_ harus ada minimal 100 judul buku. 
    - Jika kategori utama produk adalah tanaman maka di _initial dataset_ harus ada minimal 100 jenis tanaman.
6. Setiap kelompok mengimplementasikan _initial dataset_ dalam bentuk *class Models* dan menyimpan data dari _initial dataset_ tersebut ke dalam *basis data* Django. Sumber data untuk _initial dataset_ boleh berasal dari mana saja, misalnya dari Kaggle dan Wikipedia.
7. Setiap anggota kelompok mengerjakan modul yang berbeda. Modul ditentukan oleh kelompok yang disesuaikan dengan ide aplikasi yang sudah didiskusikan dalam kelompok.
8. Tugas kelompok di-_deploy_ sebagai kesatuan aplikasi web. Setiap kelompok diharapkan menggunakan PWS sebagai PaaS untuk _deployment_ proyek TK, tetapi setiap kelompok juga diberi kebebasan jika ingin melakukan _deployment_ pada PaaS lain.

## Aturan Khusus per Anggota Kelompok

1. Menerapkan *Models* dengan membuat, memanfaatkan yang sudah disediakan oleh Django, atau memanfaatkan yang sudah dibuat oleh anggota kelompok lain (pada modul lain).
2. Menerapkan *Views* untuk memproses *request* dan mengolah data untuk menghasilkan respons menggunakan templat HTML maupun mengembalikan respons JSON.
3. Menerapkan templat HTML dengan kerangka yang sistematis dan efisien, seperti `base.html`, `header.html`, dan `footer.html`.
4. Menerapkan templat HTML menggunakan *responsive framework* (seperti [Bootstrap](https://getbootstrap.com/) atau [Tailwind](https://tailwindcss.com/)).
5. Memiliki halaman form yang dapat menerima masukan dari pengguna kemudian diproses oleh *Views*. Contoh pemrosesan oleh *Views* adalah *insert* data ke dalam Models, *query* data dari Models, dan *update* data di dalam Models.
6. Menerapkan JavaScript dengan pemanggilan AJAX.
7. Menerapkan filter informasi bagi pengguna yang sudah *log in* saja. Contohnya adalah data alamat, umur, dan nomor _handphone_ hanya dapat dilihat oleh pengguna yang sudah *log in* saja.
8. Menerapkan filter pada daftar produk dari _initial dataset_ yang ditampilkan. Contohnya adalah menampilkan daftar produk berdasarkan harga.

## Tahapan Tugas Kelompok

<table>
    <tr>
        <th>Tahapan dan <em>deliverables</em></th>
        <th>Tenggat Waktu dan Keterangan</th>
    </tr>
    <tr>
        <td>
            <b>Tahap I (40%)</b>
            <ul>
                <li>Pembuatan GitHub kelompok</li>
                <li>README.md pada GitHub yang berisi:</li>
                    <ol>
                        <li>Nama-nama anggota kelompok</li>
                        <li>Deskripsi aplikasi (cerita aplikasi yang diajukan serta kebermanfaatannya)</li>
                        <li>Daftar modul yang akan diimplementasikan</li>
                        <li>Sumber <em>initial dataset</em> kategori utama produk</li>
                        <li><em>Role</em> atau peran pengguna beserta deskripsinya (karena bisa saja lebih dari satu jenis pengguna yang mengakses aplikasi)</li>
                        <li>Tautan <em>deployment</em> aplikasi</li>
                    </ol>
            </ul>
        </td>
        <td>
            <b>Tenggat Waktu: Rabu, 9 Oktober 2024, pukul 23:55 WIB</b>
            <p><b>Kumpulkan ke SCELE: Tautan GitHub</b> dengan <em>code base</em> proyek Django yang sudah disiapkan di GitHub.</p>
        </td>
    </tr>
    <tr>
        <td>
            <b>Tahap II (60%)</b>
            <p>(Modul sudah terimplementasi dengan baik)</p>
            <p>Checklist:</p>
            <ul>
                <li>Modul aplikasi dari tiap anggota kelompok</li>
                <li><em>URL Mapping</em> untuk modul</li>
                <li><em>Models</em> untuk modul</li>
                <li><em>Views</em> untuk modul</li>
                <li>Terintegrasi sebagai satu kesatuan aplikasi</li>
                <li>Fungsionalitas sesuai dengan rancangan desain</li>
                <li>Unit Test (<em>passed</em>) untuk semua aspek, diharapkan <em>code coverage</em> bisa mencapai minimal 80%</li>
            </ul>
        </td>
        <td>
            <b>Tenggat Waktu: Minggu, 27 Oktober 2024, pukul 23.55 WIB</b>
            <p><b>Kriteria Submisi:</b> Seluruh modul yang dikerjakan oleh setiap anggota kelompok sudah muncul dan dapat diakses pada proyek Django.</p>
        </td>
    </tr>
</table>
