---
sidebar_label: Tutorial 4
sidebar_position: 6
Path: docs/tutorial-4
---

# Tutorial 4: Desain Web Menggunakan HTML dan CSS3 & Metode Update dan Delete pada Data

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Tujuan Pembelajaran

Setelah menyelesaikan tutorial ini, mahasiswa diharapkan untuk dapat:

- Memahami susunan tag pada HTML5
- Mengetahui berbagai jenis tag HTML5
- Memahami sintaks penulisan CSS
- Pengenalan framework CSS, yaitu Bootstrap dan Tailwind
- Memahami konsep _static files_ pada Django
- Memahami penggunaan _selector_ pada CSS
- Memahami implementasi _update_ dan _delete_ pada Django
- Melakukan _styling_ Django dengan Tailwind

## *Important Notes*
- Pastikan kalau struktur _file_ Django kalian seperti berikut ini ![Struktur File Django](/img/4-struktur-file-django.png)
```
Catatan: deploy.yml sudah diubah menjadi push.yml
```
- Pastikan  variable DEBUG pada settings.py seperti ini
```python
...
PRODUCTION = os.getenv("PRODUCTION", False)
DEBUG = not PRODUCTION
...
```


## Pengenalan HTML

HyperText Markup Language (HTML) adalah bahasa _markup_ standar untuk dokumen agar dapat ditampilkan dalam _browser_ web. HTML mendefinisikan struktur dari konten suatu _website_.

Silakan melakukan eksplorasi mandiri mengenai HTML pada referensi [berikut](https://www.w3schools.com/html/default.asp).

Perbedaan antara HTML dan HTML5 dapat dibaca pada referensi [berikut](https://www.geeksforgeeks.org/difference-between-html-and-html5/).

## Pengenalan CSS

### Apa itu CSS?

Cascading Style Sheets (CSS) adalah bahasa yang digunakan untuk mendeskripsikan tampilan dan format dari sebuah situs web yang ditulis pada _markup language_ (seperti HTML). CSS berguna untuk membuat tampilan situs web menjadi lebih menarik.

Untuk mempelajari perbedaan antara CSS dan CSS3 dapat dibaca pada referensi [berikut](https://www.geeksforgeeks.org/difference-between-css-and-css3/).

### Cara Penulisan CSS

Secara umum, CSS dapat dituliskan dalam bentuk sebagai berikut.

```css
selector {
  properties: value;
}
```

Silakan melakukan eksplorasi mandiri terkait CSS pada referensi [berikut](https://www.w3schools.com/css/).

Terdapat tiga jenis cara penulisan CSS:

1. **_Inline Styles_**
2. **_Internal Style Sheet_**
3. **_External Style Sheet_**

Silakan melakukan eksplorasi mandiri tentang ketiga jenis CSS tersebut pada referensi [berikut](https://www.geeksforgeeks.org/types-of-css-cascading-style-sheet/).

Perlu diperhatikan, jika kamu membuat jenis _External Style Sheet_, kamu perlu menambahkan _tag_ `{% load static %}` pada halaman HTML kamu. Contohnya seperti potongan kode di bawah ini.

```html
{% load static %}
<html>
  <head>
    <title>Penggunaan External Style Sheet</title>
    <link rel="stylesheet" href="{% static 'style.css' %}" />
  </head>
  <body>
    <div>
      <h1>CSS itu asik! :D</h1>
    </div>
    <div id="main">
      <div>
        <p>Ini Tutorial 4</p>
        <h1><a href="">Mantap</a></h1>
        <p>Tutorial yang ez</p>
      </div>
    </div>
  </body>
</html>
```

Hal ini dapat terjadi karena CSS merupakan _static files_ di Django. _Static files_ akan dijelaskan pada bagian selanjutnya.

### Catatan Tambahan

Jika terdapat lebih dari satu _style_ yang didefinisikan untuk suatu elemen, maka _style_ yang akan diterapkan adalah yang memiliki prioritas yang lebih tinggi. Berikut ini urutan prioritasnya, nomor 1 yang memiliki prioritas paling tinggi.

1. _Inline style_
2. _External_ dan internal _style sheets_
3. _Browser default_

## *Static files* pada Django

Pada _framework_ Django, terdapat _file-file_ yang disebut dengan _static files_. _Static files_ merupakan _file-file_ pendukung HTML pada suatu situs web. Contoh _static files_ adalah CSS, JavaScript, dan gambar. 

Pengaturan untuk _static files_ terletak pada _file_ **`settings.py`**:

```html 
...
# Static files (CSS, JavaScript, Images)
# Dokumentasi: https://docs.djangoproject.com/en/5.1/howto/static-files/
STATIC_URL = '/static/'
STATIC_ROOT = BASE_DIR / 'static'
...
```
Pada `settings.py`, terdapat:

- `STATIC_ROOT` yang menentukan _absolute path_ ke direktori _static files_ ketika menjalankan perintah `collectstatic` pada proyek. `STATIC_ROOT` ini nantinya berguna untuk melakukan menyediakan *path* konten statis pada akses production (`DEBUG=False` pada `settings.py`)
- `STATIC_URL` yang merupakan URL yang dapat diakses publik untuk memperoleh _static files_ tersebut. Contohnya: `http://localhost:8000/static/image/example-image.png`

Perintah `collectstatic` adalah perintah untuk mengumpulkan _static files_ dari semua _app_ sehingga mempermudah akses untuk semua _app_.

Penjelasan lebih lengkap mengenai static files dapat kamu baca pada referensi [berikut](https://docs.djangoproject.com/en/5.1/ref/contrib/staticfiles/).

## _Selector_ pada CSS

Pada tutorial ini, kita akan mengenak tiga jenis _selector_: **_Element Selector_**, **ID _Selector_**, dan **_Class Selector_**.

1. **_Element Selector_**

    _Element Selector_ memungkinkan kita mengubah properti untuk semua elemen yang memiliki tag HTML yang sama.
    
    Contoh penggunaan _Element Selector_:
    ```html 
    <body>
      <div>
        <h1>Aku h1 ges</h1>
        <h2>Aku h2 ges, beda sama h1 :D</h2>
      </div>
      ...
    </body>
    ```
    
    Kita dapat menggunakan _element_ sebagai _selector_ dalam **_file_ CSS**. _Element selector_ menggunakan format *[id_name]* (tanpa diawali oleh sebuah simbol)
    
    ```html 
    h1 {
      color: #5bc933;
      font-family: "Times New Roman";
      font-style: normal;
    }
    ```
2. **ID _Selector_**

    ID _selector_ menggunakan ID pada _tag_ sebagai _selector_-nya. ID bersifat unik dalam satu halaman web. ID dapat ditambahkan pada halaman template HTML.
    
    Contoh penggunaan ID _Selector_ pada **_template_ HTML**:
    
    ```html 
    <body>
      <div id="header">
        <h1>Bermain bersama ID header</h1>
      </div>
      ...
    </body>
    ```
    
    Kemudian, kita dapat menggunakan ID tersebut sebagai _selector_ dalam **_file_ CSS**. ID _selector_ menggunakan format *#[id_name]* (selalu diawali #)
    ```html 
    #header {
      background-color: #a3b90e;
      margin-top: 0;
      padding: 20px 20px 20px 40px;
    }
    ```
    
3. **_Class Selector_**
    
    _Class Selector_ memungkinkan kita untuk mengelompokkan elemen dengan karakteristik yang sama.
    
    Contoh penggunaan _Class Selector_ pada **_template_ HTML**:
    
    ```html
    ...
    <div id="main">
        <div class="parent_content">
            <p class="date">Tanggal 9 September 2024</p>
            <h2><a href="">Subjek: Keseruan PBP</a></h2>
            <p id="content_1">Materi PBP sangat seru!</p>
        </div>
        <div class="parent_content">
            <p class="date">Tanggal 10 September 2024</p>
            <h2><a href="">Subjek: Review PBP</a></h2>
            <p id="content_2">Biar lebih gacor aku review materi PBP</p>
        </div>
        <div class="parent_content">
            <p class="date">Tanggal 11 September 2024</p>
            <h2><a href="">Subjek: Ikut Tutorial PBP</a></h2>
            <p id="content_3">Tutorial PBP sangat seru!</p>
        </div>
    </div>
    ...
    ```
    
    Kemudian, kita dapat menggunakan _Class_ tersebut sebagai _selector_ dalam **_file_ CSS**. _Class selector_ menggunakan format *.[class_name]* (diawali .)
    
    ```html
    .content_section {
      background-color: #112a33;
      margin-bottom: 30px;
      color: #0F0F0F;
      font-family: cursive;
      padding: 20px 20px 20px 40px;
    }
    ```
    
Untuk lebih memahami terkait CSS _Selector Reference_, kamu dapat membaca referensi [berikut](https://www.w3schools.com/cssref/css_selectors.php).

## Tips & trik CSS

### Mengenal _Combinator_ pada CSS
_Combinator_ dalam CSS menghubungkan dua atau lebih _selector_ untuk merincikan lebih lanjut elemen-elemen yang di-*select*.

Terdapat empat *combinators* pada CSS. Berikut ringkasan pemakaiannya: 
    
| *Combinator* | Contoh pemakaian | Penjelasan contoh |
| -------- | -------- | -------- |
| Descendant selector (space) | `div p`     | Menyeleksi semua elemen `p` yang merupakan keturunan dari elemen `div` |
| Child selector (>) | `div > p`     | Menyeleksi semua elemen `p` yang merupakan anak dari elemen `div` |
| Adjacent sibling selector (+) | `div + p` | Menyeleksi elemen `p` pertama yang berada tepat setelah elemen `div` (harus memiliki elemen induk yang sama) |
| General sibling selector (~) | `div ~ p` | Menyeleksi semua elemen `p` yang sejajar dan berada setelah elemen `div` |

Silakan melakukan eksplorasi mandiri mengenai *combinator*  melalui [referensi berikut](https://www.w3schools.com/css/css_combinators.asp).

### Mengenal *Pseudo-class* pada CSS
*Pseudo-class* digunakan untuk mendefinisikan *state* khusus dari suatu elemen. Sintaks pemakaian *pseudo-class* adalah sebagai berikut:

```css
selector:pseudo-class {
  property: value;
}
```


Beberapa contoh *pseudo-class*:
| Pseudo-class | Mengaplikasikan *style* pada .. |
| -------- | -------- |
| `:link` | tautan yang belum pernah dikunjungi |
| `:visited` | tautan yang sudah pernah dikunjungi |
| `:hover` | saat pengguna mengarahkan kursor di atas elemen tersebut |
| `:active` | saat elemen diaktifkan (biasanya saat pengguna mengklik elemen tersebut) |
| `:focus` | saat elemen fokus (seperti saat pengguna mengklik *input field*) |
| `:checked` | elemen yang telah dicentang |
| `:disabled` | elemen yang telah dibuat tidak responsif (misalnya tombol yang tidak bisa diklik) |

Silakan melakukan eksplorasi mandiri terkait *pseudo-class*  melalui [referensi ini](https://www.w3schools.com/css/css_pseudo_classes.asp).

### Mengenal Box Model pada CSS

![CSS Box Model](/img/4-box-model-css.png)

*Box model* pada CSS pada dasarnya merupakan suatu *box* yang membungkus setiap elemen HTML dan terdiri atas:

* *Content*: isi dari *box* (tempat terlihatnya teks dan gambar)
* *Padding*: mengosongkan area di sekitar konten (transparan)
* *Border*: garis tepian yang membungkus konten dan *padding*-nya
* *Margin*: mengosongkan area di sekitar *border* (transparan)

Silakan melakukan eksplorasi mandiri terkait *margin*, *border*, dan *padding* melalui [referensi berikut](https://w3schools.com/css/css_boxmodel.asp).

## Pengenalan Bootstrap & Tailwind

Pada bidang pengembangan web, terdapat banyak *framework* CSS yang sering digunakkan. Fungsi sebuah *framework* adalah untuk mempermudah pekerjaan *programmer* pada saat mengerjakan pekerjaan mereka. *Framework* CSS yang populer saat ini adalah **Bootstrap** dan juga **Tailwind**. Kedua *framework* ini memberikan banyak kelebihan dibandingkan CSS yang biasa kita gunakan. Berikut adalah kelebihan-kelebihan penggunaan *framework* yang diperoleh dibandingkan CSS biasa:

1. Proses Pengembangan Lebih Cepat: *Framework* seperti Bootstrap menyediakan komponen siap pakai sehingga tanpa harus menulis kode CSS dari awal. 
2. Responsif secara Bawaan: *Framework* seperti Bootstrap dan Tailwind telah dirancang dengan responsif.
3. Kustomisasi Mudah: Tailwind memungkinkan kustomisasi yang mendalam. Sementara itu, Bootstrap juga menawarkan opsi kustomisasi tetapi dengan pendekatan yang lebih terbatas.
4. Skalabilitas Besar: *Framework* CSS memberikan struktur yang baik untuk proyek yang berkembang seiring waktu. 

Bootstrap dan Tailwind tentu saja sebagai *framework* memiliki perbedaan yang signifikan antara satu sama lain, yaitu:


| Tailwind | Bootstrap |
| -------- | --------- |
| Tailwind CSS membangun tampilan dengan menggabungkan kelas-kelas utilitas yang telah didefinisikan sebelumnya.     | Bootstrap menggunakan gaya dan komponen yang telah didefinisikan, yang memiliki tampilan yang sudah jadi dan dapat digunakan secara langsung.      |
| Tailwind CSS memiliki _file_ CSS yang lebih kecil sedikit dibandingkan Bootstrap dan hanya akan memuat kelas-kelas utilitas yang ada | Bootstrap memiliki _file_ CSS yang lebih besar dibandingkan dengan Tailwind CSS karena termasuk banyak komponen yang telah didefinisikan. |
| Tailwind CSS memiliki memberikan fleksibilitas dan adaptabilitas tinggi terhadap proyek | Bootstrap sering kali menghasilkan tampilan yang lebih konsisten di seluruh proyek karena menggunakan komponen yang telah didefinisikan. |
| Tailwind CSS memiliki pembelajaran yang lebih curam karena memerlukan pemahaman terhadap kelas-kelas utilitas yang tersedia dan bagaimana menggabungkannya untuk mencapai tampilan yang diinginkan. | Bootstrap memiliki pembelajaran yang lebih cepat untuk pemula karena dapat mulai dengan komponen yang telah didefinisikan. |

## Responsive Web Design

*Responsive web design* merupakan metode sistem desain web yang memiliki tujuan untuk menghasilkan tampilan web yang terlihat baik pada seluruh perangkat seperti *desktop*, *tablet*, *mobile*, dan sebagainya. *Responsive web design* tidak mengubah isi dari situs web, tetapi hanya mengubah tampilan dan penataan pada setiap perangkat agar sesuai dengan lebar layar dan kemampuan perangkat tersebut. Dalam *responsive web design* tampilan-tampilan tertentu membutuhkan bantuan CSS (seperti mengecilkan atau membesarkan) suatu elemen. 

Salah satu cara untuk menguji apakah suatu situs web menggunakan *responsive web design* adalah dengan mengakses situs web tersebut dan mengaktifkan fitur `Toggle Device Mode` pada *browser*. Fitur ini memungkinkan kamu untuk melihat bagaimana situs web tersebut ditampilkan pada berbagai perangkat, seperti komputer, tablet, atau *smartphone*, tanpa harus mengubah ukuran jendela *browser*. 

Berikut adalah cara untuk mengakses fitur tersebut pada *browser* **Google Chrome**.
* Windows/Linux: Tekan `CTRL + SHIFT + I` untuk membuka Dev Tools, lalu tekan `CTRL + SHIFT + M` untuk mengaktifkan `Toggle Device Mode`.
* Mac : `Command + Shift + M`
 
Cara lain yang lebih praktis adalah dengan melakukan klik kanan pada *browser* dan memilih *Inspect Element/Inspect* untuk membuka *Dev Tools* yang berguna.

Untuk mempelajari lebih lengkap mengenai *Reponsive Web Design*, kamu dapat membuka referensi [ini](https://web.dev/responsive-web-design-basics/).

## Tutorial: Menambahkan Tailwind ke Aplikasi
Pada tutorial ini, kita akan berfokus menggunakan Tailwind dalam melakukan styling terhadap aplikasi Django kita.

1. Buka project Django kalian **(mental_health_tracker)**, lalu buka _file_ `base.html` yang telah dibuat sebelumnya pada templates folder yang berada di root project kalian. 

2. Didalam `templates/base.html`, tambahkan tag `<meta name="viewport">` agar halaman web kamu dapat menyesuaikan ukuran dan perilaku perangkat mobile **(apabila belum)**.

    ```html
    <head>
        {% block meta %}
            <meta charset="UTF-8" />
            <meta name="viewport" content="width=device-width, initial-scale=1">
        {% endblock meta %}
    </head>
    ```

3. Untuk menyambungkan template django dengan taiwind, kita dapat memanfaatkan script CDN (*Content Delivery Network*) dari Tailwind untuk diletakkan di dalam html template Django kita. Di `base.html`, kamu perlu menambahkan script cdn tailwind di bagian head. 

    ```html
    <head>
    {% block meta %}
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1">
    {% endblock meta %}
    <script src="https://cdn.tailwindcss.com">
    </script>
    </head>
    ```

## Tutorial: Menambahkan Bootstrap ke Aplikasi (Skip jika Memilih Tailwind)
***Penting***: Jika kamu memilih Bootstrap, kamu harus *skip* tutorial Tailwind karena dapat terjadi konflik kelas CSS jika digabungkan dengan Bootstrap.

1. Buka project Django kalian **(mental_health_tracker)**, lalu buka _file_ `base.html` yang telah dibuat sebelumnya pada templates folder yang berada di root project kalian. 

2. Didalam `templates/base.html`, tambahkan tag `<meta name="viewport">` agar halaman web kamu dapat menyesuaikan ukuran dan perilaku perangkat mobile **(apabila belum)**.

    ```html
    <head>
        {% block meta %}
            <meta charset="UTF-8" />
            <meta name="viewport" content="width=device-width, initial-scale=1">
        {% endblock meta %}
    </head>
    ```

3. Tambahkan Bootstrap CSS dan juga JS. 

    **CSS:**
    ```html
    <head>
        {% block meta %}
            ...
        {% endblock meta %}
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
    </head>
    ```

    **JS:**
    ```html
    <head>
        ...
        <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha384-KyZXEAg3QhqLMpG8r+J4jsl5c9zdLKaUk5Ae5f5b1bw6AUn5f5v8FZJoMxm6f5cH1" crossorigin="anonymous"></script>
    </head>
    ```


4. **(Opsional)** Apabila kalian ingin menggunakan dropdowns, popover, tooltips yang disediakan framework Bootstrap, maka kalian perlu menambahkan 2 baris *script* JS ini dibawah *script* JS yang sudah kalian buat sebelumnya.

    ```html
    <head>
        ...
        <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r" crossorigin="anonymous"></script>
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.min.js" integrity="sha384-BBtl+eGJRgqQAUMxJ7pMwbEyER4l1g+O15P+16Ep7Q9Q+zqX6gSbd85u4mG4QzX+" crossorigin="anonymous"></script>
    </head>
    ```

Referensi: [Get Started with Bootstrap 5.3](https://getbootstrap.com/docs/5.3/getting-started/introduction/)

## Tutorial: Menambahkan Fitur *Edit Mood* pada Aplikasi

Berikut ini hal-hal yang perlu kamu lakukan untuk menambahkan fitur mengubah data *mood*:

1. Buka `views.py` yang ada pada subdirektori `main`, dan buatlah fungsi baru bernama `edit_mood` yang menerima parameter `request` dan `id` seperti berikut.

    ```python
    def edit_mood(request, id):
        # Get mood entry berdasarkan id
        mood = MoodEntry.objects.get(pk = id)

        # Set mood entry sebagai instance dari form
        form = MoodEntryForm(request.POST or None, instance=mood)

        if form.is_valid() and request.method == "POST":
            # Simpan form dan kembali ke halaman awal
            form.save()
            return HttpResponseRedirect(reverse('main:show_main'))

        context = {'form': form}
        return render(request, "edit_mood.html", context)
    ```

2. Tambahkan import pada _file_ `views.py` (**Ingat, hanya tambahkan *import*!**)
   ```python
   from django.shortcuts import .., reverse
   from django.http import .., HttpResponseRedirect
   ```

3. Buatlah berkas HTML baru dengan nama `edit_mood.html` pada subdirektori `main/templates`. Isi berkas tersebut dengan template berikut.

    ```html 
    {% extends 'base.html' %}

    {% load static %}

    {% block content %}

    <h1>Edit Mood</h1>

    <form method="POST">
        {% csrf_token %}
        <table>
            {{ form.as_table }}
            <tr>
                <td></td>
                <td>
                    <input type="submit" value="Edit Mood"/>
                </td>
            </tr>
        </table>
    </form>

    {% endblock %}
    ```

4. Buka `urls.py` yang berada pada direktori `main` dan *import* fungsi `edit_product` yang sudah dibuat.

    ```python
    from main.views import edit_mood
    ```

5. Tambahkan *path* url ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.

    ```python 
    ...
    path('edit-mood/<uuid:id>', edit_mood, name='edit_mood'),
    ...
    ```
:::note
Untuk tipe data dari id menyesuaikan dengan tipe data dari atribut `id` di model MoodEntry. Jika kalian menggunakan tipe data integer, maka ubahlah tipe data menjadi `<int:id>`
:::

6. Buka `main.html` yang berada pada subdirektori `main/templates`. Tambahkan potongan kode berikut sejajar dengan elemen `<td>` terakhir agar terlihat tombol *edit* pada setiap baris tabel.

    ```html 
    ...
    <tr>
        ...
        <td>
            <a href="{% url 'main:edit_mood' mood_entry.pk %}">
                <button>
                    Edit
                </button>
            </a>
        </td>
    </tr>
    ...
    ```
**Penjelasan Kode**
- `{% url 'main:edit_mood' mood_entry.pk %}` digunakan untuk membangun URL dengan menambahkan primary key (pk) dari objek `mood_entry` sebagai **parameter**. Parameter ini akan diteruskan ke fungsi view `edit_mood`, yang membutuhkan nilai id untuk mengetahui entri mana yang akan diedit.

7. Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000](http://localhost:8000) di browser favoritmu. Setelah *login*, cobalah untuk klik tombol `edit` pada suatu *mood* dan ubah datanya sesukamu. Apabila perubahan tersimpan dan terlihat pada halaman utama aplikasi tanpa *error*, maka selamat, kamu berhasil menambahkan fitur *edit*!

## Tutorial: Menambahkan Fitur Hapus *Mood* pada Aplikasi

Berikut ini hal-hal yang perlu kamu lakukan untuk menambahkan fitur menghapus data *mood*:

1. Buat fungsi baru dengan nama `delete_mood` yang menerima parameter `request` dan `id` pada `views.py` di folder `main` untuk menghapus data mood. Kamu dapat menggunakan kode berikut.

    > Jangan lupa untuk memahami isi kodenya ya😅

    ```python
    def delete_mood(request, id):
        # Get mood berdasarkan id
        mood = MoodEntry.objects.get(pk = id)
        # Hapus mood
        mood.delete()
        # Kembali ke halaman awal
        return HttpResponseRedirect(reverse('main:show_main'))
    ```

2. Buka `urls.py` yang ada pada *folder* `main` dan import fungsi yang sudah kamu buat tadi.

    ```python
    from main.views import delete_mood
    ```

3. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor.

    ```python
    ...
    path('delete/<uuid:id>', delete_mood, name='delete_mood'), # sesuaikan dengan nama fungsi yang dibuat
    ...
    ```
:::note
Untuk tipe data dari id menyesuaikan dengan tipe data dari atribut `id` di model MoodEntry. Jika kalian menggunakan tipe data integer, maka ubahlah tipe data menjadi `<int:id>`
:::

4. Bukalah berkas `main.html` yang ada pada folder `main/templates` dan ubahlah kode yang sudah ada menjadi seperti berikut agar terdapat tombol hapus untuk setiap produk.

    ```html 
    ...
    <tr>
        ...
        <td>
            <a href="{% url 'main:edit_mood' mood_entry.pk %}">
                <button>
                    Edit
                </button>
            </a>
        </td>
        <td>
            <a href="{% url 'main:delete_mood' mood_entry.pk %}">
                <button>
                    Delete
                </button>
            </a>
        </td>
    </tr>
    ...
    ```

5. Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000](http://localhost:8000) di *browser* favoritmu. Setelah *login*, cobalah untuk hapus data suatu *mood* dan *refresh* halaman. Apabila *mood* tersebut hilang dari halaman utama aplikasi kamu tanpa *error*, maka selamat, kamu berhasil menambahkan fitur *delete*! 

## Tutorial: Menambahkan *Navigation Bar* pada Aplikasi
*Navigation Bar* (navbar) adalah elemen yang biasanya digunakan untuk menavigasi berbagai halaman atau fitur dalam sebuah aplikasi web. Navbar biasanya ditempatkan di bagian atas halaman dan berisi tautan atau tombol yang mengarah ke halaman-halaman lain dalam aplikasi.

- Buatlah berkas HTML baru dengan nama `navbar.html` pada folder `templates/` di root directory. Isi dari `navbar.html` dapat kamu isi dengan template berikut.
```html
<nav class="bg-indigo-600 shadow-lg fixed top-0 left-0 z-40 w-screen">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <div class="flex items-center">
          <h1 class="text-2xl font-bold text-center text-white">Mental Health Tracker</h1>
        </div>
        <div class="hidden md:flex items-center">
          {% if user.is_authenticated %}
            <span class="text-gray-300 mr-4">Welcome, {{ user.username }}</span>
            <a href="{% url 'main:logout' %}" class="text-center bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded transition duration-300">
              Logout
            </a>
          {% else %}
            <a href="{% url 'main:login' %}" class="text-center bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded transition duration-300 mr-2">
              Login
            </a>
            <a href="{% url 'main:register' %}" class="text-center bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded transition duration-300">
              Register
            </a>
          {% endif %}
        </div>
        <div class="md:hidden flex items-center">
          <button class="mobile-menu-button">
            <svg class="w-6 h-6 text-white" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor">
              <path d="M4 6h16M4 12h16M4 18h16"></path>
            </svg>
          </button>
        </div>
      </div>
    </div>
    <!-- Mobile menu -->
    <div class="mobile-menu hidden md:hidden  px-4 w-full md:max-w-full">
      <div class="pt-2 pb-3 space-y-1 mx-auto">
        {% if user.is_authenticated %}
          <span class="block text-gray-300 px-3 py-2">Welcome, {{ user.username }}</span>
          <a href="{% url 'main:logout' %}" class="block text-center bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded transition duration-300">
            Logout
          </a>
        {% else %}
          <a href="{% url 'main:login' %}" class="block text-center bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded transition duration-300 mb-2">
            Login
          </a>
          <a href="{% url 'main:register' %}" class="block text-center bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded transition duration-300">
            Register
          </a>
        {% endif %}
      </div>
    </div>
    <script>
      const btn = document.querySelector("button.mobile-menu-button");
      const menu = document.querySelector(".mobile-menu");
    
      btn.addEventListener("click", () => {
        menu.classList.toggle("hidden");
      });
    </script>
  </nav>
```
:::note Untuk tutorial kali ini Anda tidak harus dapat memahami cara kerja `<script>`. Penggunaan `<script>` akan Anda pelajari di tutorial 5 minggu depan.
:::

- Kemudian, tautkan navbar tersebut ke dalam `main.html`, `create_mood_entry.html`, dan `edit_mood.html` yang berada di subdirektori `main/templates/` dengan menggunakan tags `include`:
    ```html
    {% extends 'base.html' %}
    {% block content %}
    {% include 'navbar.html' %}
    ...
    {% endblock content%}
    ```

:::note Tanda `...` menandakan kode lainnya dalam berkas yang tidak perlu diubah
:::

Berikut beberapa referensi tambahan terkait cara membuat *navigation bar* yang dapat kamu gunakan: 

- Menggunakan Tailwind: dapat diakses melalui [tautan berikut](https://tailwindui.com/components/application-ui/navigation/navbars)
- Menggunakan Bootstrap: dapat diakses melalui [tautan berikut](https://getbootstrap.com/docs/5.3/components/navbar/)
- Menggunakan CSS manual: dapat diakses melalui [tautan berikut](https://www.w3schools.com/css/css_navbar.asp)

## Tutorial: Konfigurasi _Static Files_ pada Aplikasi

1. Pada `settings.py`, tambahkan _middleware_ WhiteNoise. 
```python
...
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'whitenoise.middleware.WhiteNoiseMiddleware', #Tambahkan tepat di bawah SecurityMiddleware
    ...
]
...
```
Dengan menambahkan _middleware_ WhiteNoise pada `settings.py`, Django dapat mengelola _file_ statis secara otomatis dalam mode produksi (`DEBUG=False`) tanpa perlu konfigurasi yang kompleks. Hal ini berguna agar _file_ statis tersebut bisa diakses di deployment kamu sebab secara default, apabila `DEBUG=False` maka Django tidak akan menyediakan akses ke _file_ statis.

2. Pada `settings.py`, pastikan variabel `STATIC_ROOT`, `STATICFILES_DIRS`, dan `STATIC_URL` dikonfigurasikan seperti ini (jika belum ada, bisa ditambahkan saja):
```python
...
STATIC_URL = '/static/'
if DEBUG:
    STATICFILES_DIRS = [
        BASE_DIR / 'static' # merujuk ke /static root project pada mode development
    ]
else:
    STATIC_ROOT = BASE_DIR / 'static' # merujuk ke /static root project pada mode production
...
```

## Opsional: Menambahkan *Styles* pada Aplikasi dengan Tailwind dan External CSS
:::note
Bagian ini merupakan bagian opsional yang dapat kalian lalui apabila kalian ingin berkreasi sendiri dalam mendekorasi aplikasi. Bila kalian ingin mencoba hasil kreasi asdos, kalian dapat mengikuti langkah-langkah yang diberikan pada bagian ini.
:::
### Tambahkan `global.css`
Buatlah _file_ `global.css` di `/static/css` pada root directory seperti ini:
![Global CSS Path](/img/4-global-css-path.png)
Pada _file_ `global.css` ini, kamu bisa menambahkan kelas _custom_ atau _style_ css yang sudah kamu definisikan sendiri.

### Hubungkan `global.css` dan *script* Tailwind ke base.html
Agar _style_ CSS yang ditambahkan di `global.css` dapat digunakan dalam template Django, kamu perlu menambahkan _file_ tersebut ke `base.html`.
Modifikasi _file_ `base.html` kamu seperti berikut:
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    {% block meta %} {% endblock meta %}
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="{% static 'css/global.css' %}"/>
  </head>
  <body>
    {% block content %} {% endblock content %}
  </body>
</html>
```

### Menambahkan _custom styling_ ke global.css
Modifikasi _file_ `global.css` pada `static/css/global.css` seperti berikut: 
```css 
.form-style form input, form textarea, form select {
    width: 100%;
    padding: 0.5rem;
    border: 2px solid #bcbcbc;
    border-radius: 0.375rem;
}
.form-style form input:focus, form textarea:focus, form select:focus {
    outline: none;
    border-color: #674ea7;
    box-shadow: 0 0 0 3px #674ea7;
}
@keyframes shine {
    0% { background-position: -200% 0; }
    100% { background-position: 200% 0; }
}
.animate-shine {
    background: linear-gradient(120deg, rgba(255, 255, 255, 0.3), rgba(255, 255, 255, 0.1) 50%, rgba(255, 255, 255, 0.3));
    background-size: 200% 100%;
    animation: shine 3s infinite;
}
```

### _Styling_ Halaman Login
Ubah berkas `login.html` pada subdirektori `main/templates/` menjadi seperti berikut:
``` html
{% extends 'base.html' %}

{% block meta %}
<title>Login</title>
{% endblock meta %}

{% block content %}
<div class="min-h-screen flex items-center justify-center w-screen bg-gray-100 py-12 px-4 sm:px-6 lg:px-8">
  <div class="max-w-md w-full space-y-8">
    <div>
      <h2 class="mt-6 text-center text-black text-3xl font-extrabold text-gray-900">
        Login to your account
      </h2>
    </div>
    <form class="mt-8 space-y-6" method="POST" action="">
      {% csrf_token %}
      <input type="hidden" name="remember" value="true">
      <div class="rounded-md shadow-sm -space-y-px">
        <div>
          <label for="username" class="sr-only">Username</label>
          <input id="username" name="username" type="text" required class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm" placeholder="Username">
        </div>
        <div>
          <label for="password" class="sr-only">Password</label>
          <input id="password" name="password" type="password" required class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm" placeholder="Password">
        </div>
      </div>

      <div>
        <button type="submit" class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          Sign in
        </button>
      </div>
    </form>

    {% if messages %}
    <div class="mt-4">
      {% for message in messages %}
      {% if message.tags == "success" %}
            <div class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded relative" role="alert">
                <span class="block sm:inline">{{ message }}</span>
            </div>
        {% elif message.tags == "error" %}
            <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                <span class="block sm:inline">{{ message }}</span>
            </div>
        {% else %}
            <div class="bg-blue-100 border border-blue-400 text-blue-700 px-4 py-3 rounded relative" role="alert">
                <span class="block sm:inline">{{ message }}</span>
            </div>
        {% endif %}
      {% endfor %}
    </div>
    {% endif %}

    <div class="text-center mt-4">
      <p class="text-sm text-black">
        Don't have an account yet?
        <a href="{% url 'main:register' %}" class="font-medium text-indigo-200 hover:text-indigo-300">
          Register Now
        </a>
      </p>
    </div>
  </div>
</div>
{% endblock content %}
```
![Contoh Tampilan Login Page](/img/4-contoh-tampilan-login-page.png)

### _Styling_ Halaman Register
Ubah berkas `register.html` pada subdirektori `main/templates/` menjadi seperti berikut:
``` html
{% extends 'base.html' %}

{% block meta %}
<title>Register</title>
{% endblock meta %}

{% block content %}
<div class="min-h-screen flex items-center justify-center bg-gray-100 py-12 px-4 sm:px-6 lg:px-8">
  <div class="max-w-md w-full space-y-8 form-style">
    <div>
      <h2 class="mt-6 text-center text-3xl font-extrabold text-black">
        Create your account
      </h2>
    </div>
    <form class="mt-8 space-y-6" method="POST">
      {% csrf_token %}
      <input type="hidden" name="remember" value="true">
      <div class="rounded-md shadow-sm -space-y-px">
        {% for field in form %}
          <div class="{% if not forloop.first %}mt-4{% endif %}">
            <label for="{{ field.id_for_label }}" class="mb-2 font-semibold text-black">
              {{ field.label }}
            </label>
            <div class="relative">
              {{ field }}
              <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
                {% if field.errors %}
                  <svg class="h-5 w-5 text-red-500" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7 4a1 1 0 11-2 0 1 1 0 012 0zm-1-9a1 1 0 00-1 1v4a1 1 0 102 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
                  </svg>
                {% endif %}
              </div>
            </div>
            {% if field.errors %}
              {% for error in field.errors %}
                <p class="mt-1 text-sm text-red-600">{{ error }}</p>
              {% endfor %}
            {% endif %}
          </div>
        {% endfor %}
      </div>

      <div>
        <button type="submit" class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          Register
        </button>
      </div>
    </form>

    {% if messages %}
    <div class="mt-4">
      {% for message in messages %}
      <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
        <span class="block sm:inline">{{ message }}</span>
      </div>
      {% endfor %}
    </div>
    {% endif %}

    <div class="text-center mt-4">
      <p class="text-sm text-black">
        Already have an account?
        <a href="{% url 'main:login' %}" class="font-medium text-indigo-200 hover:text-indigo-300">
          Login here
        </a>
      </p>
    </div>
  </div>
</div>
{% endblock content %}
```
![Contoh Tampilan Register Page](/img/4-contoh-tampilan-register-page.png)

### _Styling_ Halaman Home
1. Buat _file_ `card_info.html` di directory `main/templates`, lalu tambahkan kode html seperti ini:
```html
<div class="bg-indigo-700 rounded-xl overflow-hidden border-2 border-indigo-800">
    <div class="p-4 animate-shine">
      <h5 class="text-lg font-semibold text-gray-200">{{ title }}</h5>
      <p class="text-white">{{ value }}</p>
    </div>
</div>
```
![Contoh Tampilan Card Info](/img/4-contoh-tampilan-card-info.png)

> **Note:** Ini adalah contoh tampilan dari elemen `card_info.html`

2. Buat _file_ `card_mood.html` di directory `main/templates`, lalu tambahkan kode html sebagai berikut:
```html
<div class="relative break-inside-avoid">
  <div class="absolute top-2 z-10 left-1/2 -translate-x-1/2 flex items-center -space-x-2">
    <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
    <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
  </div>
  <div class="relative top-5 bg-indigo-100 shadow-md rounded-lg mb-6 break-inside-avoid flex flex-col border-2 border-indigo-300 transform rotate-1 hover:rotate-0 transition-transform duration-300">
    <div class="bg-indigo-200 text-gray-800 p-4 rounded-t-lg border-b-2 border-indigo-300">
      <h3 class="font-bold text-xl mb-2">{{mood_entry.mood}}</h3>
      <p class="text-gray-600">{{mood_entry.time}}</p>
    </div>
    <div class="p-4">
      <p class="font-semibold text-lg mb-2">My Feeling</p> 
      <p class="text-gray-700 mb-2">
        <span class="bg-[linear-gradient(to_bottom,transparent_0%,transparent_calc(100%_-_1px),#CDC1FF_calc(100%_-_1px))] bg-[length:100%_1.5rem] pb-1">{{mood_entry.feelings}}</span>
      </p>
      <div class="mt-4">
        <p class="text-gray-700 font-semibold mb-2">Intensity</p>
        <div class="relative pt-1">
          <div class="flex mb-2 items-center justify-between">
            <div>
              <span class="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full text-indigo-600 bg-indigo-200">
                {% if mood_entry.mood_intensity > 10 %}10+{% else %}{{mood_entry.mood_intensity}}{% endif %}
              </span>
            </div>
          </div>
          <div class="overflow-hidden h-2 mb-4 text-xs flex rounded bg-indigo-200">
            <div style="width:{% if mood_entry.mood_intensity > 10 %}100%{% else %}{{ mood_entry.mood_intensity }}0%{% endif %}" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-indigo-500"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="absolute top-0 -right-4 flex space-x-1">
    <a href="{% url 'main:edit_mood' mood_entry.pk %}" class="bg-yellow-500 hover:bg-yellow-600 text-white rounded-full p-2 transition duration-300 shadow-md">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
        <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z" />
      </svg>
    </a>
    <a href="{% url 'main:delete_mood' mood_entry.pk %}" class="bg-red-500 hover:bg-red-600 text-white rounded-full p-2 transition duration-300 shadow-md">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
        <path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" />
      </svg>
    </a>
  </div>
</div>
```
![Contoh Tampilan Card Mood](/img/4-contoh-tampilan-card-mood.png)
> **Note:** Ini adalah contoh tampilan dari elemen card_mood.html
3. Selanjutnya, kita memerlukan tampilan jika mood_entry masih kosong. Pilihlah satu foto atau *icon* sedih dan namakan`sedih-banget.png`. Kamu dibebaskan memilih foto apa saja. Tambahkan foto `sedih-banget.png` tadi ke direktori `static/image` yang berada di *root project*.
4. Setelah semuanya selesai, kita perlu menggunakan `card_info.html`, `card_mood.html`, dan `sedih-banget.png` tersebut ke template `main.html`. Pada directory `main/templates`, modifikasi `main.html` seperti ini:
```html 
{% extends 'base.html' %}
{% load static %}

{% block meta %}
<title>Mental Health Tracker</title>
{% endblock meta %}
{% block content %}
{% include 'navbar.html' %}
<div class="overflow-x-hidden px-4 md:px-8 pb-8 pt-24 min-h-screen bg-gray-100 flex flex-col">
  <div class="p-2 mb-6 relative">
    <div class="relative grid grid-cols-1 z-30 md:grid-cols-3 gap-8">
      {% include "card_info.html" with title='NPM' value=npm %}
      {% include "card_info.html" with title='Name' value=name %}
      {% include "card_info.html" with title='Class' value=class %}
    </div>
    <div class="w-full px-6  absolute top-[44px] left-0 z-20 hidden md:flex">
      <div class="w-full min-h-4 bg-indigo-700">
      </div>
    </div>
    <div class="h-full w-full py-6  absolute top-0 left-0 z-20 md:hidden flex ">
      <div class="h-full min-w-4 bg-indigo-700 mx-auto">
      </div>
    </div>
</div>
    <div class="px-3 mb-4">
      <div class="flex rounded-md items-center bg-indigo-600 py-2 px-4 w-fit">
        <h1 class="text-white text-center">Last Login: {{last_login}}</h1>
      </div>
    </div>
    <div class="flex justify-end mb-6">
        <a href="{% url 'main:create_mood_entry' %}" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded-lg transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105">
            Add New Mood Entry
        </a>
    </div>
    
    {% if not mood_entries %}
    <div class="flex flex-col items-center justify-center min-h-[24rem] p-6">
        <img src="{% static 'image/sedih-banget.png' %}" alt="Sad face" class="w-32 h-32 mb-4"/>
        <p class="text-center text-gray-600 mt-4">Belum ada data mood pada mental health tracker.</p>
    </div>
    {% else %}
    <div class="columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6 w-full">
        {% for mood_entry in mood_entries %}
            {% include 'card_mood.html' with mood_entry=mood_entry %}
        {% endfor %}
    </div>
    {% endif %}
</div>
{% endblock content %}
```

Tampilan dari [http://localhost:8000](http://localhost:8000) akan berubah seperti ini:
![Contoh Tampilan Main Page saat Tidak Ada Mood](/img/4-contoh-tampilan-main-page-empty.png)

![Contoh Tampilan Main Page saat Ada Mood](/img/4-contoh-tampilan-main-page.png)

### _Styling_ Halaman Create Mood Entry
6. Ubah berkas `create_mood_entry.html` pada subdirektori `main/templates` menjadi seperti berikut:
```html
{% extends 'base.html' %}
{% load static %}
{% block meta %}
<title>Create Mood</title>
{% endblock meta %}

{% block content %}
{% include 'navbar.html' %}

<div class="flex flex-col min-h-screen bg-gray-100">
  <div class="container mx-auto px-4 py-8 mt-16 max-w-xl">
    <h1 class="text-3xl font-bold text-center mb-8 text-black">Create Mood Entry</h1>
  
    <div class="bg-white shadow-md rounded-lg p-6 form-style">
      <form method="POST" class="space-y-6">
        {% csrf_token %}
        {% for field in form %}
          <div class="flex flex-col">
            <label for="{{ field.id_for_label }}" class="mb-2 font-semibold text-gray-700">
              {{ field.label }}
            </label>
            <div class="w-full">
              {{ field }}
            </div>
            {% if field.help_text %}
              <p class="mt-1 text-sm text-gray-500">{{ field.help_text }}</p>
            {% endif %}
            {% for error in field.errors %}
              <p class="mt-1 text-sm text-red-600">{{ error }}</p>
            {% endfor %}
          </div>
        {% endfor %}
        <div class="flex justify-center mt-6">
          <button type="submit" class="bg-indigo-600 text-white font-semibold px-6 py-3 rounded-lg hover:bg-indigo-700 transition duration-300 ease-in-out w-full">
            Create Mood Entry
          </button>
        </div>
      </form>
    </div>
  </div>
</div>

{% endblock %}
```
![Contoh Tampilan Create Mood Entry Page](/img/4-contoh-tampilan-create-mood-entry-page.png)

### _Styling_ Halaman Edit Mood
7. Ubah berkas `edit_mood.html` pada subdirektori `main/templates` menjadi seperti berikut:
```html
{% extends 'base.html' %}
{% load static %}
{% block meta %}
<title>Edit Mood</title>
{% endblock meta %}

{% block content %}
{% include 'navbar.html' %}
<div class="flex flex-col min-h-screen bg-gray-100">
  <div class="container mx-auto px-4 py-8 mt-16 max-w-xl">
    <h1 class="text-3xl font-bold text-center mb-8 text-black">Edit Mood Entry</h1>
  
    <div class="bg-white rounded-lg p-6 form-style">
      <form method="POST" class="space-y-6">
          {% csrf_token %}
          {% for field in form %}
              <div class="flex flex-col">
                  <label for="{{ field.id_for_label }}" class="mb-2 font-semibold text-gray-700">
                      {{ field.label }}
                  </label>
                  <div class="w-full">
                      {{ field }}
                  </div>
                  {% if field.help_text %}
                      <p class="mt-1 text-sm text-gray-500">{{ field.help_text }}</p>
                  {% endif %}
                  {% for error in field.errors %}
                      <p class="mt-1 text-sm text-red-600">{{ error }}</p>
                  {% endfor %}
              </div>
          {% endfor %}
          <div class="flex justify-center mt-6">
              <button type="submit" class="bg-indigo-600 text-white font-semibold px-6 py-3 rounded-lg hover:bg-indigo-700 transition duration-300 ease-in-out w-full">
                  Edit Mood Entry
              </button>
          </div>
      </form>
  </div>
  </div>
</div>
{% endblock %}
```
![Contoh Tampilan Edit Mood Entry Page](/img/4-contoh-tampilan-edit-mood-entry-page.png)

## Penutup
- Setelah menjalankan tutorial di atas, Anda seharusnya memiliki struktur direktori lokal seperti berikut.
 
   ```
   mental-health-tracker
   ├── .github\workflows
   │   └── push.yml
   ├── env    
   ├── main
   │   ├── migrations
   │   │   ├── __init__.py
   │   │   ├── 0001_initial.py
   │   │   ├── 0002_alter_moodentry_id.py
   │   │   └── 0003_moodentry_user.py   
   │   ├── templates
   │   │   ├── create_mood_entry.html
   │   │   ├── card_info.html
   │   │   ├── card_mood.html
   │   │   ├── edit_mood.html
   │   │   ├── login.html
   │   │   ├── main.html
   │   │   └── register.html
   │   ├── __init__.py
   │   ├── admin.py
   │   ├── apps.py
   │   ├── forms.py
   │   ├── models.py
   │   ├── tests.py
   │   ├── urls.py
   │   └── views.py
   ├── mental_health_tracker
   │   ├── __init__.py
   │   ├── asgi.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   ├── templates
   │   └── base.html
   │   └── navbar.html
   ├── static
   │   └── css
   │       └── global.css
   │   └── image
   │       └── sedih-banget.png
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
   ```

## Kontributor

- Isa Citra Buana
- Williams
- Ravie Hasan Abud
- Abbilhaidar Farras Zulfikar
- Alfredo Austin
- Juan Maxwell Tanaya

## Credits

Tutorial ini dikembangkan berdasarkan [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) dan [PBP Genap 2024](https://github.com/pbp-fasilkom-ui/genap-2024) yang ditulis oleh Tim Pengajar Pemrograman Berbasis Platform 2024. Segala tutorial serta instruksi yang dicantumkan pada repositori ini dirancang sedemikian rupa sehingga mahasiswa yang sedang mengambil mata kuliah Pemrograman Berbasis Platform dapat menyelesaikan tutorial saat sesi lab berlangsung.
