---
sidebar_label: Tutorial 1
sidebar_position: 3
Path: docs/tutorial-1
---

# Tutorial 1: Pengenalan Aplikasi Django dan *Model-View-Template* (MVT) pada Django

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Tujuan Pembelajaran

Setelah menyelesaikan tutorial ini, mahasiswa diharapkan untuk dapat:

- Mengerti konsep MVT pada aplikasi Django
- Mengerti bagaimana alur Django menampilkan sebuah halaman HTML
- Mengerti konfigurasi *routing* yang ada pada `urls.py`
- Memahami kaitan *models*, *views* dan *template* pada Django
- Memahami pembuatan *unit test* pada *framework* Django

## Ringkasan Hasil Tutorial 0

Untuk membantumu mengerjakan tutorial 1 dengan baik, kami mengharapkan hasil pengerjaan tutorial 0 sebagai berikut.

1. Pada komputer lokal, terdapat direktori utama `mental-health-tracker` yang telah diinisiasi sebagai repositori lokal.
2. Pada direktori utama `mental-health-tracker` tersebut, terdapat beberapa berkas dan subdirektori berikut.

    - Subdirektori `env`.
    - Subdirektori proyek `mental_health_tracker`. Berbeda dengan direktori utama, subdirektori ini terbentuk setelah menjalankan perintah

        ```bash
        django-admin startproject mental_health_tracker .
        ```

    - Berkas `.gitignore`.
    - Berkas `manage.py`.
    - Berkas `requirements.txt`.
    - (Opsional) Berkas `db.sqlite3`.

    Struktur direktori utama `mental-health-tracker` pada lokal adalah sebagai berikut.

    ```
    mental-health-tracker
    ├── mental_health_tracker
    │   ├── __init__.py
    │   ├── asgi.py
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── manage.py
    ├── .gitignore
    └── requirements.txt
    ```

3. Pada repositori GitHub, pastikan repositori `mental-health-tracker` memiliki berkas dan direktori berikut.

    - Direktori proyek `mental_health_tracker`. Direktori ini hasil menjalankan perintah

        ```bash
        django-admin startproject mental_health_tracker .
        ```

    - Berkas `.gitignore`.
    - Berkas `manage.py`.
    - Berkas `requirements.txt`.

    Struktur repository `mental-health-tracker` pada repositori GitHub adalah sebagai berikut.

    ![Struktur Repositori Github](/img/1-filebefore-github.png)

## Pengenalan Mengenai Konsep MVT

Dalam dunia pengembangan web, terdapat berbagai konsep dan arsitektur yang membantu dalam merancang dan mengembangkan aplikasi. Salah satu konsep yang umum digunakan adalah MVT (*Model-View-Template*).

### Apa Itu Konsep MVT?

![MVT Diagram](https://cdn.discordapp.com/attachments/1142468662461214771/1146996248268775484/3._Python_Django_-_Modul_2_Page2_Image5.jpg)

**MVT** adalah singkatan dari ***Model-View-Template***. MVT adalah sebuah konsep arsitektur yang digunakan dalam pengembangan web untuk memisahkan komponen-komponen utama dari sebuah aplikasi. Konsep ini memungkinkan pengembang web untuk mengorganisasi dan mengelola kode dengan lebih terstruktur.

### Apa Itu Model?

***Model*** merupakan komponen dalam konsep MVT yang bertanggung jawab untuk mengatur dan mengelola data dari aplikasi. Model mewakili struktur data dan logika aplikasi yang berada di belakang tampilan. Model menghubungkan aplikasi dengan basis data dan mengatur interaksi dengan data tersebut.

### Apa Itu *View*?

***View*** merupakan komponen yang menangani logika presentasi dalam konsep MVT. *View* mengontrol bagaimana data yang dikelola oleh model akan ditampilkan kepada pengguna. Dalam konteks MVT, *view* berperan sebagai pengatur tampilan dan mengambil data dari model untuk disajikan kepada pengguna.

### Apa Itu *Template*?

***Template*** adalah komponen yang berfungsi untuk mengatur tampilan atau antarmuka pengguna. *Template* memisahkan kode HTML dari logika aplikasi. Dalam MVT, *template* digunakan untuk merancang tampilan yang akhirnya akan diisi dengan data dari model melalui *view*.

### Hubungan Antara Komponen-komponen MVT

Secara ringkas, konsep MVT berjalan dalam kerangka berikut:

- ***Model***: Menyimpan data dan logika aplikasi.
- ***View***: Menampilkan data dari model dan menghubungkannya dengan *template*.
- ***Template***: Menentukan tampilan antarmuka pengguna.

### Manfaat MVT

- **Pemisahan Tugas**

    MVT memisahkan tugas antara logika aplikasi, tampilan, dan data, sehingga memungkinkan pengembang untuk bekerja pada setiap komponen secara terpisah.

- **Kode yang Mudah Dikelola**

    Dengan pemisahan tugas yang jelas, kode menjadi lebih terorganisir dan mudah dikelola.

- **Penggunaan Kembali**

    Kode dapat digunakan kembali dalam berbagai bagian aplikasi yang berbeda.

- **Skalabilitas**

    Struktur MVT mendukung skalabilitas dengan memungkinkan pengembangan paralel pada setiap komponen.

**Catatan:**

- Konsep MVT sangat terkait dengan *framework* Django dalam pengembangan web dengan bahasa pemrograman Python.
- Dalam praktiknya, pemahaman yang baik mengenai konsep MVT akan membantu kamu dalam merancang aplikasi web yang lebih terstruktur dan mudah dikelola.

## Tutorial: Membuat Aplikasi Django beserta Konfigurasi Model

Dalam tutorial ini, akan dijelaskan mengenai konsep aplikasi dan proyek dalam Django.

**Apa Itu Proyek dan Aplikasi dalam Django?**

- **Proyek (*Project*)** adalah keseluruhan proyek web yang kamu bangun dengan menggunakan Django. **Proyek berisi berbagai aplikasi** yang berfungsi secara bersama untuk menciptakan situs web atau aplikasi web yang lengkap.

- **Aplikasi (*Apps*)** adalah unit modular yang melakukan tugas-tugas spesifik dalam suatu proyek Django. Setiap aplikasi dapat memiliki model, tampilan, *template*, dan URL yang terkait dengannya. Aplikasi memungkinkanmu untuk membagi fungsionalitas proyek menjadi bagian-bagian terpisah yang dapat dikelola secara independen.

Sebelum dimulai, kamu perlu mengingat kembali bahwa direktori utama adalah direktori **terluar** (`mental-health-tracker`), sedangkan direktori proyek adalah direktori **di dalam** direktori utama (`mental_health_tracker`).

### Langkah 1: Persiapan Awal

1. Buka Direktori Utama **`mental-health-tracker`**.

    - Sebelum memulai, pastikan kamu berada di direktori **utama** **`mental-health-tracker`** yang telah dibuat pada Tutorial 0.
    - Pengembangan proyek Django kamu akan dilanjutkan pada direktori ini 😎.

2. Buka terminal atau *command prompt* dan pastikan kamu sudah berada pada direktori utama, **`mental-health-tracker`**.

:::tip

- Gunakan perintah `cd [direktori]` untuk berpindah direktori ke direktori lain yang ingin dituju. Perintah ini sangat penting untuk diingat, karena keahlian menggunakan terminal akan bermanfaat tidak hanya untuk mata kuliah PBP, tetapi juga mata kuliah lain nantinya.

:::

3. Aktifkan *virtual environment* yang telah dibuat sebelumnya dengan menjalankan perintah berikut. **(Mohon perhatikan sistem operasi yang kamu gunakan)**.

   - **Windows:**

     ```bash
     env\Scripts\activate
     ```

   - **Unix (Linux & Mac OS):**

     ```bash
     source env/bin/activate
     ```
:::tip
- Untuk pengguna Windows, apabila kamu mendapatkan error berbunyi "*the execution of scripts is disabled on this system...*", berikut adalah solusi yang dapat kamu coba:
    - Buka _PowerShell_ sebagai *administrator* dan jalankan perintah berikut:
        ```bash
        Set-ExecutionPolicy Unrestricted -Force
        ```
    - Pilih opsi `A` dan tekan `Enter`.
- Untuk pengguna sistem operasi berbasis Unix (Linux & macOS), jika kamu mendapatkan error berbunyi "*... Permission Denied*", berikut adalah solusi yang dapat kamu coba:
    - Jalankan perintah berikut:
        ```bash
        chmod +x env/bin/activate
        ```
:::

### Langkah 2: Membuat Aplikasi `main` dalam Proyek *mental-health-tracker*

Kamu akan membuat aplikasi baru bernama `main` dalam proyek *mental-health-tracker*.

1. Jalankan perintah berikut untuk membuat aplikasi baru dengan nama **main**.

     ```shell
     python manage.py startapp main
     ```

    Setelah perintah di atas dijalankan, direktori baru dengan nama `main` akan terbentuk. Direktori main akan berisi struktur awal untuk aplikasi Django kamu.

:::note
Jika kamu masih bingung mengenai istilah-istilah baru seperti **direktori utama**, **direktori proyek**, **direktori aplikasi**, *it's' okay!* Kamu akan terbiasa sesiring berjalannya waktu. Semangat!
:::

2. Mendaftarkan aplikasi `main` ke dalam proyek.

   - Buka berkas `settings.py` di dalam direktori proyek `mental_health_tracker`.
   - Tambahkan `'main'` ke dalam daftar aplikasi yang ada sebagai elemen paling terakhir. Daftar aplikasi dapat kamu akses pada variabel `INSTALLED_APPS`.

     ```python
     INSTALLED_APPS = [
         ...,
         'main'
     ]
     ```

Dengan melakukan langkah-langkah tersebut, kamu telah mendaftarkan aplikasi `main` ke dalam proyek *mental health tracker* kamu.

## Tutorial: Implementasi *Template* Dasar

Pada tahap ini, kamu akan membuat *template* yang berada pada direktori `templates` yang berada di `main`. *Template* ini digunakan untuk menampilkan data program *mental health* kamu.

:::note
Saat ini, aplikasi *mental health tracker* belum menampilkan data apapun. Data akan ditampilkan pada tutorial 2. Semangat!
:::

### Langkah 1: Membuat dan Mengisi Berkas `main.html`

Mari berkenalan dengan HTML terlebih dahulu. HTML (*Hypertext Markup Language*) adalah bahasa penanda yang digunakan pada halaman web untuk menafsirkan dan menulis teks, gambar dan bahan lainnya secara visual maupun suara.

:::note
Hint: Kamu akan mempelajari HTML lebih lanjut di tutorial 4.
:::

1. **Buat direktori baru** bernama `templates` di dalam direktori aplikasi `main`.

2. Di dalam direktori `templates`, **buat berkas baru** bernama `main.html`. Isi berkas `main.html` dengan kode berikut. **Ubah nama dan kelas sesuai dengan data diri kamu!**

     ```html
     <h1>Mental Health Tracker</h1>

     <h5>NPM: </h5>
     <p>2306123456</p> <!-- Ubah sesuai dengan npm kamu -->
     <h5>Name: </h5>
     <p>Pak Bepe</p> <!-- Ubah sesuai dengan nama kamu -->
     <h5>Class: </h5>
     <p>PBP E</p> <!-- Ubah sesuai dengan kelas kamu -->
     ```

3. Buka berkas HTML di peramban web.

   - Sebelum dihubungkan dengan aplikasi, cobalah membuka berkas `main.html` di peramban web-mu.
   - Perlu dicatat bahwa pada tahap ini **hanya untuk memeriksa** tampilan dasar HTML dan **belum terhubung dengan Django.**
   - Berikut merupakan contoh tampilan HTML yang diharapkan.
     ![main.html](/img/1-html-template.jpeg)

## Tutorial: Implementasi Model Dasar

### Langkah 1: Mengubah Berkas `models.py` dalam Aplikasi `main`

Pada langkah ini, kamu akan mengubah berkas `models.py` yang terdapat di dalam direktori aplikasi `main` untuk mendefinisikan model baru.

1. Buka berkas `models.py` pada direktori aplikasi `main`.

2. Isi berkas `models.py` dengan kode berikut.

    ```python
    from django.db import models

    class MoodEntry(models.Model):
        mood = models.CharField(max_length=255)
        time = models.DateField(auto_now_add=True)
        feelings = models.TextField()
        mood_intensity = models.IntegerField()

        @property
        def is_mood_strong(self):
            return self.mood_intensity > 5
    ```

    **Penjelasan Kode:**

    - `models.Model` adalah kelas dasar yang digunakan untuk mendefinisikan model dalam Django.
    - `MoodEntry` adalah nama model yang kamu definisikan.
    - *`mood`*, *`time`*, *`feelings`*, dan *`mood_intensity`* adalah atribut atau *field* pada model. Setiap *field* memiliki tipe data yang sesuai seperti `CharField`, `DateField`, `IntegerField`, dan `TextField`.
    - _Decorator_ `@property` digunakan untuk menambahkan atribut _read-only_ yang tidak disimpan ke dalam basis data, namun merupakan hasil derivasi/perhitungan dari atribut lain. Dalam hal ini, fungsi `is_mood_strong()` yang diberikan _decorator_ `@property` mengukur apakah _mood_ pengguna pada saat itu tergolong "kuat" berdasarkan *`mood_intensity`*.

    :::tip
    Kamu akan mempelajari lebih banyak tentang "atribut hasil derivasi" pada mata kuliah Basis Data nanti. Untuk sementara, apabila kamu ingin mengetahui lebih banyak tentang kegunaan _decorator_ `@property`, kamu dapat membaca [dokumentasi Python mengenai _class property_](https://docs.python.org/3/library/functions.html#property).
    :::

### Langkah 2: Membuat dan Mengaplikasikan Migrasi Model

**Apa itu migrasi model?**

- Migrasi model adalah cara Django melacak perubahan pada model basis data kamu.
- Migrasi ini adalah instruksi untuk mengubah struktur tabel basis data sesuai dengan perubahan model yang didefinisikan dalam kode terbaru kamu.

**Bagaimana cara melakukan migrasi model?**

1. Jalankan perintah berikut untuk membuat migrasi model.

    ```shell
    python manage.py makemigrations
    ```

    :::tip
    `makemigrations` menciptakan berkas migrasi yang berisi perubahan model yang **belum** diaplikasikan ke dalam basis data.
    :::

2. Jalankan perintah berikut untuk menerapkan migrasi ke dalam basis data lokal.

    ```shell
    python manage.py migrate
    ```

   :::tip
   `migrate` mengaplikasikan perubahan model yang tercantum dalam berkas migrasi ke basis data dengan menjalankan perintah sebelumnya.
   :::

**Setiap kali kamu melakukan perubahan pada *model***, seperti menambahkan atau mengubah atribut, **kamu WAJIB melakukan migrasi** untuk merefleksikan perubahan tersebut.

## Tutorial: Menghubungkan *View* dengan  *Template*

Pada tahap ini, kamu akan menghubungkan komponen *view* dengan komponen *template* menggunakan Django.

### Langkah 1: Mengintegrasikan Komponen MVT

Kamu akan mengimpor modul yang diperlukan dan membuat fungsi *view* `show_main`.

1. Buka berkas `views.py` yang terletak di dalam berkas aplikasi `main`.

2. Apabila belum ada, tambahkan baris-baris *import* berikut di bagian paling atas berkas.

    ```python
    from django.shortcuts import render
    ```

    **Penjelasan Kode:**

    - `from django.shortcuts import render` berguna untuk mengimpor fungsi *render* dari modul `django.shortcuts`.
    - Fungsi *render* akan digunakan untuk *render* tampilan HTML dengan menggunakan data yang diberikan.

3. Tambahkan fungsi `show_main` di bawah impor:

    ```python
    def show_main(request):
        context = {
            'npm' : '2306123456',
            'name': 'Pak Bepe',
            'class': 'PBP E'
        }

        return render(request, "main.html", context)
    ```

    **Penjelasan Kode:**

    - Potongan kode di atas mendeklarasikan fungsi `show_main`, yang menerima parameter `request`. Fungsi ini akan mengatur permintaan HTTP dan mengembalikan tampilan yang sesuai.
    - `context` adalah *dictionary* yang berisi data untuk dikirimkan ke tampilan. Pada saat ini, terdapat tiga data yang disertakan, yaitu:

       - `npm`: Data npm-mu.
       - `name`: Data namamu.
       - `class`: Data kelasmu.

    - `return render(request, "main.html", context)` berguna untuk me-*render* tampilan `main.html` dengan menggunakan fungsi `render`. Fungsi `render` mengambil tiga argumen:

       - `request`: Ini adalah objek permintaan HTTP yang dikirim oleh pengguna.
       - `main.html`: Ini adalah nama berkas *template* yang akan digunakan untuk me-*render* tampilan.
       - `context`: Ini adalah *dictionary* yang berisi data yang akan diteruskan ke tampilan untuk digunakan dalam penampilan dinamis.

## Langkah 2: Modifikasi *Template*

Pada tahap ini, kamu akan mengubah *template* `main.html` agar dapat menampilkan data yang telah diambil dari *model*.

1. Buka berkas `main.html` yang telah dibuat sebelumnya dalam direktori `templates` pada direktori `main`.

2. Ubah nama dan kelas menjadi struktur kode Django yang sesuai untuk menampilkan data.

    ```html
    ...
    <h5>NPM: </h5>
    <p>{{ npm }}<p>
    <h5>Name: </h5>
    <p>{{ name }}<p>
    <h5>Class: </h5>
    <p>{{ class }}<p>
    ...
    ```

    **Penjelasan Kode:**

    Sintaks Django `{{ npm }}`, `{{ name }}` dan `{{ class }}`, disebut _template variables_, digunakan untuk menampilkan nilai dari variabel yang telah didefinisikan dalam `context`.

## Tutorial: Mengonfigurasi *Routing* URL

Kamu akan mengatur *routing* URL agar aplikasi `main` dapat diakses melalui peramban web.

### Langkah 1: Mengonfigurasi *Routing* URL Aplikasi `main`

1. Buatlah berkas `urls.py` **di dalam** direktori `main`.
2. Isi `urls.py` dengan kode berikut.

    ```python
    from django.urls import path
    from main.views import show_main

    app_name = 'main'

    urlpatterns = [
        path('', show_main, name='show_main'),
    ]
    ```

   **Penjelasan Kode dalam `urls.py` pada Aplikasi `main`:**

   - `urls.py` bertanggung jawab untuk mengatur rute URL yang terkait dengan aplikasi `main`.
   - Impor `path` dari `django.urls` untuk mendefinisikan pola URL.
   - Gunakan fungsi `show_main` dari modul `main.views` sebagai tampilan yang akan ditampilkan ketika URL terkait diakses.
   - Nama `app_name` diberikan untuk memberikan nama unik pada pola URL dalam aplikasi.

### Langkah 2: Mengonfigurasi *Routing* URL Proyek

Kamu akan menambahkan rute URL dalam `urls.py` proyek untuk menghubungkannya ke tampilan `main`.

1. Buka berkas `urls.py` **di dalam direktori proyek `mental_health_tracker`, bukan yang ada di dalam direktori aplikasi `main`**.
2. Impor fungsi `include` dari `django.urls`.

    ```python
    ...
    from django.urls import path, include
    ...
    ```

3. Tambahkan rute URL seperti berikut untuk mengarahkan ke tampilan `main` di dalam variabel `urlpatterns`.

    ```python
    urlpatterns = [
        ...
        path('', include('main.urls')),
        ...
    ]
    ```

   **Penjelasan:**

   - Berkas `urls.py` pada proyek bertanggung jawab untuk mengatur rute URL tingkat proyek.
   - Fungsi `include` digunakan untuk mengimpor rute URL dari aplikasi lain (dalam hal ini, dari aplikasi `main`) ke dalam berkas `urls.py` proyek.
   - *Path* URL `''` akan diarahkan ke rute yang didefinisikan dalam berkas `urls.py` aplikasi `main`. Path URL dibiarkan berupa string kosong agar halaman aplikasi main dapat diakses secara langsung.


   :::tip
   Sebagai bayangan, apabila kamu menggunakan path `'main/'` pada contoh di atas, maka kamu perlu mengakses halaman `http://localhost:8000/main/` untuk mengakses halaman aplikasi `main`. Karena path yang ditentukan adalah `''`, maka kamu dapat mengakses aplikasi main melalui URL `http://localhost:8000/` saja.
   :::

4. Jalankan proyek Django dengan perintah `python manage.py runserver`

5. Bukalah [http://localhost:8000/](http://localhost:8000/) di peramban web favoritmu untuk melihat halaman yang sudah kamu buat.

Dengan langkah-langkah di atas, kamu telah berhasil mengimplementasikan tampilan dasar dalam aplikasi `main` dan menghubungkannya dengan rute URL proyek. Pastikan kamu memahami setiap langkah dan informasi yang diberikan untuk mengaktifkan tampilan dalam proyek Django-mu.

### Apa bedanya `urls.py` pada aplikasi dan `urls.py` pada proyek?

- Berkas `urls.py` pada aplikasi mengatur rute URL spesifik untuk fitur-fitur dalam aplikasi tersebut.
- `urls.py` pada proyek mengarahkan rute URL tingkat proyek dan dapat mengimpor rute URL dari berkas `urls.py` aplikasi-aplikasi, memungkinkan aplikasi dalam proyek Django untuk bersifat modular dan terpisah.

## Tutorial: Pengenalan Django *Unit Testing*

*Unit testing* dapat digunakan untuk mengecek apakah kode yang dibuat bekerja sesuai dengan keinginan. Hal ini juga berguna ketika kamu melakukan perubahan kode. Dengan menggunakan tes, kamu bisa mengecek apakah perubahan yang dilakukan dapat menyebabkan perilaku yang tidak diinginkan pada aplikasi.

### Langkah 1: Membuat Unit *Test*

1. Bukalah berkas `tests.py` pada direktori aplikasi `main`.
2. Isi `tests.py` dengan kode berikut.

    ```python
    from django.test import TestCase, Client
    from django.utils import timezone
    from .models import MoodEntry

    class mainTest(TestCase):
        def test_main_url_is_exist(self):
            response = Client().get('')
            self.assertEqual(response.status_code, 200)

        def test_main_using_main_template(self):
            response = Client().get('')
            self.assertTemplateUsed(response, 'main.html')

        def test_nonexistent_page(self):
            response = Client().get('/skibidi/')
            self.assertEqual(response.status_code, 404)

        def test_strong_mood_user(self):
            now = timezone.now()
            mood = MoodEntry.objects.create(
              mood="LUMAYAN SENANG",
              time = now,
              feelings = "senang sih, cuman tadi baju aku basah kena hujan :(",
              mood_intensity = 8,
              sadness_level = 2
            )
            self.assertTrue(mood.is_mood_strong)
    ```

    **Penjelasan:**
    - `test_main_url_is_exist` adalah tes untuk mengecek apakah *path* URL utama (`''`) dapat diakses.
    - `test_main_using_main_template` adalah tes untuk mengecek apakah halaman utama di-*render* menggunakan *template* `main.html`.
    - `test_nonexistent_page` adalah tes untuk mengecek apakah halaman yang tidak ada pada proyek Django memang benar-benar tidak ada dan akan memberikan kode respons 404 (_Not Found_).
    - `test_strong_mood_user` adalah tes untuk memeriksa logika kode, terutama pada saat menentukan apakah _mood_ pengguna bisa dikatakan kuat dengan suatu nilai `mood_intensity_ yang tersimpan.

Ketika melakukan unit testing, pastikan kamu selalu mengecek seluruh kemungkinan kasus yang ada. Sebagai contoh, misalkan pada saat melakukan _test_ untuk properti *`is_mood_strong`*, terdapat dua kasus yang dapat menyebabkan _output_ dari fungsi tersebut bernilai antara `True` atau `False`.

### Langkah 2: Menjalankan *Test*

1. Jalankan tes dengan menggunakan perintah berikut.

    ```shell
    python manage.py test
    ```

2. Jika tes berhasil, akan mengeluarkan informasi berikut.

    ```text
    Found 4 test(s).
    Creating test database for alias 'default'...
    System check identified no issues (0 silenced).
    ..
    ----------------------------------------------------------------------
    Ran 4 tests in 0.016s

    OK
    Destroying test database for alias 'default'...
    ```

**Selamat!** Kamu telah berhasil menulis Django *Test* dan menjalankannya.

## Penutup

1. Pada akhir tutorial ini, struktur direktori lokalmu akan terlihat seperti ini.
   ```
   mental-health-tracker
   ├── main
   │   ├── __init__.py
   │   ├── admin.py
   │   ├── apps.py
   │   ├── migrations
   │   │   ├── 0001_initial.py
   │   │   └── __init__.py
   │   ├── models.py
   │   ├── templates
   │   │   └── main.html
   │   ├── tests.py
   │   ├── urls.py
   │   └── views.py
   ├── mental_health_tracker
   │   ├── __init__.py
   │   ├── asgi.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   ├── manage.py
   ├── .gitignore
   └── requirements.txt
   ```

2. Sebelum melakukan langkah ini, **pastikan struktur direktori lokal sudah benar**. Selanjutnya, lakukan `add`, `commit` dan `push` untuk memperbarui repositori GitHub.
3. Jalankan perintah berikut untuk melakukan `add`, `commit` dan `push`.

    ```shell
    git add .
    git commit -m "<pesan_commit>"
    git push -u origin <branch_utama>
    ```

    - Ubah `<pesan_commit>` sesuai dengan keinginan. Contoh: `git commit -m "tutorial 1 selesai"`.
    - Ubah `<branch_utama>` sesuai dengan nama branch utamamu. Contoh: `git push -u origin main` atau `git push -u origin master`.

4. Berikut struktur direktori GitHub setelah kamu menyelesaikan tutorial ini.

    ![Struktur Repositori Github](/img/1-fileafter-github.png)

## Referensi Tambahan

- [Django Unit Testing](https://docs.djangoproject.com/en/4.2/topics/testing/)
- [Django Model Unit Testing](https://stackoverflow.com/questions/64574713/django-models-unit-tests-help-for-a-newbie)

## Kontributor

- Alden Luthfi
- Juan Dharmananda Khusuma
- Puti Raissa
- Tsabit Coda R

## Credits
Tutorial ini dikembangkan berdasarkan [PBP Genap 2024](https://github.com/pbp-fasilkom-ui/genap-2024) dan [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) yang ditulis oleh Tim Pengajar Pemrograman Berbasis Platform 2024. Segala tutorial serta instruksi yang dicantumkan pada repositori ini dirancang sedemikian rupa sehingga mahasiswa yang sedang mengambil mata kuliah Pemrograman Berbasis Platform dapat menyelesaikan tutorial saat sesi lab berlangsung.

