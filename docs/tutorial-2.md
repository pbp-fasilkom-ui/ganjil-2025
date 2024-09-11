---
sidebar_label: Tutorial 2
sidebar_position: 3
Path: docs/tutorial-2
---

# Tutorial 2: Form dan Data Delivery

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

## Tujuan Pembelajaran​

Setelah menyelesaikan tutorial ini, mahasiswa diharapkan untuk dapat:

- Memahami tujuan dan cara implementasi skeleton sebagai kerangka views
- Mengetahui `XML` dan `JSON` sebagai salah satu metode _data delivery_
- Memahami cara kerja submisi data yang diberikan oleh pengguna menggunakan elemen `form` pada `HTML`
- Memahami cara mengirimkan data menggunakan format `XML` dan `JSON`
- Memahami cara mengambil data spesifik berdasarkan `ID`
- Memahami penggunaan postman sebagai data viewer

## Pengenalan Data Delivery

Dalam mengembangkan suatu _platform_, ada kalanya kita perlu mengirimkan data dari satu _stack_ ke _stack_ lainnya. Data yang dikirimkan bisa bermacam-macam bentuknya. Beberapa contoh format data yang umum digunakan antara lain HTML, XML, dan JSON. Implementasi _data delivery_ dalam bentuk HTML sudah kamu pelajari pada tutorial sebelumnya. Pada tutorial ini akan diajarkan terkait XML dan JSON.

## XML (Extensible Markup Language)

XML, atau _eXtensible Markup Language_, adalah sebuah format yang dirancang agar mudah dimengerti hanya dengan membacanya, karena setiap elemen dalam XML mendeskripsikan dirinya sendiri. XML banyak digunakan dalam berbagai aplikasi _web_ dan _mobile_ untuk tujuan penyimpanan dan pertukaran data. File XML hanya berisi data yang dikemas dalam _tag_ tertentu, dan untuk dapat mengirim, menerima, menyimpan, atau menampilkan informasi dari _file_ tersebut, kita perlu membuat program yang dapat memprosesnya.

Contoh Format XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<person>
    <name>Doddy Ferdiansyah</name>
    <age>25</age>
    <address>
        <street>Jl. Ganesa No.10</street>
        <city>Bandung</city>
        <province>Jawa Barat</province>
        <zip>40132</zip>
    </address>
</person>
```

XML di atas sangatlah _self-descriptive_:

- Ada informasi nama (`name`)
- Ada informasi umur (`age`)
- Ada informasi alamat (`address`)
  - Ada informasi jalan (`street`)
  - Ada informasi kota (`city`)
  - Ada informasi provinsi (`province`)
  - Ada informasi kode pos (`zip`)

Dokumen XML membentuk struktur seperti _tree_ yang dimulai dari _root_, lalu _branch_, hingga berakhir pada _leaves_. Dokumen XML **harus mengandung sebuah _root element_** yang merupakan _parent_ dari elemen lainnya. Pada contoh di atas, `<person>` adalah _root element_.

Baris `<?xml version="1.0" encoding="UTF-8"?>` biasanya disebut sebagai **XML Prolog**. XML Prolog bersifat opsional, akan tetapi jika ada maka posisinya harus berada di awal dokumen XML. Pada dokumen XML, **semua elemen wajib memiliki** **closing tag**. **Tag** pada XML sifatnya **case sensitive**, sehingga tag `<person>` dianggap **berbeda** dengan tag `<Person>`.

## JSON (JavaScript Object Notation)

JSON, atau _JavaScript Object Notation_, adalah sebuah format yang dirancang agar mudah dimengerti karena setiap elemennya mendeskripsikan dirinya sendiri atau _self describing_. JSON banyak digunakan dalam berbagai aplikasi _web_ dan _mobile_ untuk menyimpan dan mentransfer data. Meskipun sintaks JSON berasal dari objek JavaScript, JSON sebenarnya adalah format _text_. Oleh karena itu, banyak bahasa pemrograman yang memiliki dukungan untuk membaca dan membuat JSON.

Contoh format JSON:

```json
{
  "name": "Doddy Ferdiansyah",
  "age": 25,
  "address": {
    "street": "Jl. Ganesa No.10",
    "city": "Bandung",
    "province": "Jawa Barat",
    "zip": "40132"
  }
}
```

Data pada JSON disimpan dalam bentuk _key_ dan _value_. Pada contoh di atas yang menjadi _key_ adalah `name`, `age`, dan `address`. _Value_ dapat berupa tipe data primitif (_string, number, boolean_) ataupun berupa objek.

## Pre-Tutorial Notes

Sebelum kamu memulai, serta untuk membantumu mengikuti tutorial 2 dengan baik, kami mengharapkan beberapa hasil berikut dari tutorial 1:

- Struktur direktori `mental-health-tracker` secara lokal adalah sebagai berikut.

![Struktur Direktori Lokal](/img/2-struktur-direktori-lokal.png)


- Struktur repository `mental-health-tracker` pada GitHub adalah sebagai berikut.

![Struktur Repositori Github](/img/2-struktur-direktori-github.png)


## Tutorial: Implementasi _Skeleton_ sebagai Kerangka _Views_

Sebelum kita membuat form registrasi, kita perlu membuat suatu _skeleton_ yang berfungsi sebagai kerangka _views_ dari situs web kita. Dengan kerangka _views_ ini, kita dapat memastikan adanya konsistensi dalam desain situs web kita serta memperkecil kemungkinan terjadinya redundansi kode. Pada tutorial ini, kita akan membuat _skeleton_ untuk situs web yang akan kita buat pada tutorial selanjutnya.

1. Buat direktori `templates` pada direktori utama (**_root folder_**) dan buatlah sebuah berkas HTML baru bernama `base.html`. Berkas `base.html` berfungsi sebagai _template_ dasar yang dapat digunakan sebagai kerangka umum untuk halaman web lainnya di dalam proyek. Isilah berkas `base.html` tersebut dengan kode berikut:

   ```html
   {% load static %}
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       {% block meta %} {% endblock meta %}
     </head>

     <body>
       {% block content %} {% endblock content %}
     </body>
   </html>
   ```

   Baris-baris yang dikurung dalam `{% ... %}` disebut dengan _template tags_ Django. Baris-baris inilah yang akan berfungsi untuk memuat data secara dinamis dari Django ke HTML.

   Pada contoh diatas, tag `{% block %}` di Django digunakan untuk mendefinisikan area dalam template yang dapat diganti oleh template turunan. Template turunan akan me-_extend_ template dasar (pada contoh ini `base.html`) dan mengganti konten di dalam block ini sesuai kebutuhan.

3. Buka `settings.py` yang ada pada direktori proyek (`mental_health_tracker`) dan carilah baris yang mengandung variabel `TEMPLATES`. Sesuaikan kode yang ada dengan potongan kode berikut agar berkas `base.html` terdeteksi sebagai berkas _template_.

   ```python
   ...
   TEMPLATES = [
       {
           'BACKEND': 'django.template.backends.django.DjangoTemplates',
           'DIRS': [BASE_DIR / 'templates'], # Tambahkan konten baris ini
           'APP_DIRS': True,
           ...
       }
   ]
   ...
   ```
   :::note
   Dalam beberapa kasus, `APP_DIRS` pada konfigurasi `TEMPLATES` kamu dapat bernilai `False`. Apabila nilainya `False`, ubah menjadi `True`. `APP_DIRS` **harus** bernilai `True`.
   :::

4. Pada subdirektori `templates` yang ada pada direktori `main` (`main/templates/`), ubahlah kode berkas `main.html` yang telah dibuat di tutorial sebelumnya menjadi sebagai berikut.

   ```html
    {% extends 'base.html' %}
    {% block content %}
    <h1>Mental Health Tracker</h1>

    <h5>NPM: </h5>
    <p>{{ npm }}<p>

    <h5>Name:</h5>
    <p>{{ name }}</p>

    <h5>Class:</h5>
    <p>{{ class }}</p>
    {% endblock content %}
   ```

    Perhatikan bahwa kode diatas merupakan kode yang sama dengan kode pada `main.html` pada tutorial sebelumnya. Perbedaannya adalah pada kode diatas, kita menggunakan `base.html` sebagai _template_ utama.

## Tutorial: Mengubah Primary Key Dari Integer Menjadi UUID

Untuk mengedepankan _best practice_ dari sisi keamanan aplikasi, terdapat sedikit perubahan yang perlu kamu lakukan pada berkas `models.py` di subdirektori `main/`. Secara _default_, ID dari setiap objek model yang akan kamu buat menggunakan tipe data _integer_ yang _incremental_, dimulai dari 1. Ini dapat menjadi salah satu "pintu masuk" terhadap celah keamanan aplikasi Django kalian, karena dapat dilakukan enumerasi terhadap ID dari objek-objek yang terdapat pada aplikasi.

Apabila kamu penasaran celah keamanan ini termasuk ke jenis kerentanan apa dan apa dampak yang dapat terjadi, kamu dapat membaca lebih lanjut pada [artikel ini mengenai IDOR](https://portswigger.net/web-security/access-control/idor). Untuk sekarang, kita akan berfokus pada menerapkan _best practice_ untuk mencegah celah keamanan ini.

:::warning
Apabila kamu sebelumnya sudah menambahkan objek ke modelmu, kamu harus menghapus berkas basis datamu (`db.sqlite3`) terlebih dahulu agar langkah-langkah berikut tidak menimbulkan _error_.
:::

1. Tambahkan baris ini pada berkas `models.py` di subdirektori `main/`.

```python
import uuid  # tambahkan baris ini di paling atas
...
class MoodEntry(models.Model):
    id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)  # tambahkan baris ini
    mood = models.CharField(max_length=255)
    time = models.DateField(auto_now_add=True)
    feelings = models.TextField()
    mood_intensity = models.IntegerField()
...
```

2. Lakukan migrasi model dengan menjalankan perintah berikut.

   Windows:
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```

   Unix (Linux/macOS):
   ```
   python3 manage.py makemigrations
   python3 manage.py migrate
   ```

## Tutorial: Membuat Form Input Data dan Menampilkan Data Mood Entry Pada HTML

Sampai saat ini, belum ada data yang ditambahkan dan dimunculkan ke dalam aplikasi. Sekarang, kita akan membuat sebuah _form_ sederhana untuk menginput data _Mood Entry_ pada aplikasi sehingga nantinya kamu dapat menambahkan data baru untuk ditampilkan pada halaman utama.

1. Buat berkas baru pada direktori `main` dengan nama `forms.py` untuk membuat struktur _form_ yang dapat menerima data _Mood Entry_ baru. Tambahkan kode berikut ke dalam berkas `forms.py`.

   ```python
   from django.forms import ModelForm
   from main.models import MoodEntry

   class MoodEntryForm(ModelForm):
       class Meta:
           model = MoodEntry
           fields = ["mood", "feelings", "mood_intensity"]
   ```

   **Penjelasan Kode:**

   - `model = MoodEntry` untuk menunjukkan model yang akan digunakan untuk _form_. Ketika data dari _form_ disimpan, isi dari _form_ akan disimpan menjadi sebuah objek `MoodEntry`.
   - `fields = ["mood", "feelings", "mood_intensity"]` untuk menunjukkan _field_ dari model `MoodEntry` yang digunakan untuk _form_. _Field_ `time` tidak dimasukkan ke _list_ `fields` karena `time` ditambahkan secara otomatis.

2. Buka berkas `views.py` yang ada pada direktori `main` dan tambahkan beberapa _import_ berikut pada bagian paling atas.

   ```python
   from django.shortcuts import render, redirect   # Tambahkan import redirect di baris ini
   from main.forms import MoodEntryForm
   from main.models import MoodEntry
   ```

3. Masih di berkas yang sama, buat fungsi baru dengan nama `create_mood_entry` yang menerima parameter `request`. Tambahkan potongan kode di bawah ini untuk menghasilkan _form_ yang dapat menambahkan data _Mood Entry_ secara otomatis ketika data di-_submit_ dari _form_.

   ```python
   def create_mood_entry(request):
       form = MoodEntryForm(request.POST or None)

       if form.is_valid() and request.method == "POST":
           form.save()
           return redirect('main:show_main')

       context = {'form': form}
       return render(request, "create_mood_entry.html", context)
   ```

   **Penjelasan Kode:**

   - `form = MoodEntryForm(request.POST or None)` digunakan untuk membuat `MoodEntryForm` baru dengan memasukkan _QueryDict_ berdasarkan input dari _user_ pada `request.POST`.
   - `form.is_valid()` digunakan untuk memvalidasi isi input dari _form_ tersebut.
   - `form.save()` digunakan untuk membuat dan menyimpan data dari _form_ tersebut.
   - `return redirect('main:show_main')` digunakan untuk melakukan _redirect_ ke fungsi `show_main` pada _views_ aplikasi `main` setelah data _form_ berhasil disimpan.

4. Ubahlah fungsi `show_main` yang sudah ada pada berkas `views.py` menjadi seperti berikut.

   ```python
   def show_main(request):
       mood_entries = MoodEntry.objects.all()

       context = {
           'name': 'Pak Bepe',
           'class': 'PBP D',
           'npm': '2306123456',
           'mood_entries': mood_entries
       }

       return render(request, "main.html", context)
   ```

   **Penjelasan Kode:**

   Fungsi `MoodEntry.objects.all()` digunakan untuk mengambil seluruh objek `MoodEntry` yang tersimpan pada _database_.

5. Buka `urls.py` yang ada pada direktori `main` dan _import_ fungsi `create_mood_entry` yang sudah kamu buat tadi.

   ```python
   from main.views import show_main, create_mood_entry
   ```

6. Tambahkan _path_ URL ke dalam variabel `urlpatterns` pada `urls.py` di `main` untuk mengakses fungsi yang sudah di-_import_ pada poin sebelumnya.

   ```python
   urlpatterns = [
      ...
      path('create-mood-entry', create_mood_entry, name='create_mood_entry'),
   ]
   ```

7. Buat berkas HTML baru dengan nama `create_mood_entry.html` pada direktori `main/templates`. Isi `create_mood_entry.html` dengan kode berikut.

   ```html
   {% extends 'base.html' %} 
   {% block content %}
   <h1>Add New Mood Entry</h1>

   <form method="POST">
     {% csrf_token %}
     <table>
       {{ form.as_table }}
       <tr>
         <td></td>
         <td>
           <input type="submit" value="Add Mood Entry" />
         </td>
       </tr>
     </table>
   </form>

   {% endblock %}
   ```

   **Penjelasan Kode:**

   - `<form method="POST">` digunakan untuk menandakan _block_ untuk _form_ dengan metode POST.
   - `{% csrf_token %}` adalah token yang berfungsi sebagai _security_. Token ini di-_generate_ secara otomatis oleh Django untuk mencegah serangan berbahaya.
   - `{{ form.as_table }}` adalah _template tag_ yang digunakan untuk menampilkan _fields_ form yang sudah dibuat pada `forms.py` sebagai _table_.
   - `<input type="submit" value="Add Mood Entry"/>` digunakan sebagai tombol _submit_ untuk mengirimkan _request_ ke _view_ `create_mood_entry(request)`.

8. Buka `main.html` dan tambahkan kode berikut di dalam `{% block content %}` untuk menampilkan data _mood_ dalam bentuk tabel serta tombol "Add New Mood Entry" yang akan _redirect_ ke halaman _form_.

   ```html
   ...
   {% if not mood_entries %}
   <p>Belum ada data mood pada mental health tracker.</p>
   {% else %}
   <table>
     <tr>
       <th>Mood Name</th>
       <th>Time</th>
       <th>Feeling</th>
       <th>Mood Intensity</th>
     </tr>

     {% comment %} Berikut cara memperlihatkan data mood di bawah baris ini 
     {% endcomment %} 
     {% for mood_entry in mood_entries %}
     <tr>
       <td>{{mood_entry.mood}}</td>
       <td>{{mood_entry.time}}</td>
       <td>{{mood_entry.feelings}}</td>
       <td>{{mood_entry.mood_intensity}}</td>
     </tr>
     {% endfor %}
   </table>
   {% endif %}

   <br />

   <a href="{% url 'main:create_mood_entry' %}">
     <button>Add New Mood Entry</button>
   </a>
   {% endblock content %}
   ```

9. Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000/](http://localhost:8000/) di browser favoritmu. Coba tambahkan beberapa data mood baru dan seharusnya kamu dapat melihat data yang ditambahkan pada halaman utama aplikasi.

## Tutorial Mengembalikan Data dalam Bentuk XML

1. Buka `views.py` yang ada pada direktori `main` dan tambahkan _import_ `HttpResponse` dan `Serializer` pada bagian paling atas.

   ```python
   from django.http import HttpResponse
   from django.core import serializers
   ```

2. Buatlah sebuah fungsi baru yang menerima parameter _request_ dengan nama `show_xml` dan buatlah sebuah variabel di dalam fungsi tersebut yang menyimpan hasil _query_ dari seluruh data yang ada pada `MoodEntry`.

   ```python
   def show_xml(request):
       data = MoodEntry.objects.all()
   ```

3. Tambahkan _return function_ berupa `HttpResponse` yang berisi parameter data hasil _query_ yang sudah diserialisasi menjadi XML dan parameter `content_type="application/xml"`.

   ```python
   def show_xml(request):
       data = MoodEntry.objects.all()
       return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
   ```

   **Penjelasan Kode:**

   `serializers` digunakan untuk _translate_ objek model menjadi format lain seperti dalam fungsi ini adalah XML.

4. Buka `urls.py` yang ada pada direktori `main` dan _import_ fungsi yang sudah kamu buat tadi.

   ```python
   from main.views import show_main, create_mood_entry, show_xml
   ```

5. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.

   ```python
   ...
   path('xml/', show_xml, name='show_xml'),
   ...
   ```

6. Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000/xml/](http://localhost:8000/xml/) di browser favoritmu untuk melihat hasilnya.

## Tutorial: Mengembalikan Data dalam Bentuk JSON

1. Buka `views.py` yang ada pada direktori `main` dan buatlah sebuah fungsi baru yang menerima parameter _request_ dengan nama `show_json` dengan sebuah variabel di dalamnya yang menyimpan hasil _query_ dari seluruh data yang ada pada `MoodEntry`.

   ```python
   def show_json(request):
       data = MoodEntry.objects.all()
   ```

2. Tambahkan _return function_ berupa `HttpResponse` yang berisi parameter data hasil _query_ yang sudah diserialisasi menjadi JSON dan parameter `content_type="application/json"`.

   ```python
   def show_json(request):
       data = MoodEntry.objects.all()
       return HttpResponse(serializers.serialize("json", data), content_type="application/json")
   ```

3. Buka `urls.py` yang ada pada direktori `main` dan _import_ fungsi yang sudah kamu buat tadi.

   ```python
   from main.views import show_main, create_mood_entry, show_xml, show_json
   ```

4. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.

   ```python
   ...
   path('json/', show_json, name='show_json'),
   ...
   ```

5. Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000/json/](http://localhost:8000/json/) (sesuaikan dengan _path url_ yang dibuat) di browser favoritmu untuk melihat hasilnya.

## Tutorial: Mengembalikan Data Berdasarkan ID dalam Bentuk XML dan JSON

1. Buka `views.py` yang ada pada direktori `main` dan buatlah dua fungsi baru yang menerima parameter `request` dan `id` dengan nama `show_xml_by_id` dan `show_json_by_id`.

2. Buatlah sebuah variabel di dalam fungsi tersebut yang menyimpan hasil _query_ dari data dengan id tertentu yang ada pada `MoodEntry`.

   ```python
   data = MoodEntry.objects.filter(pk=id)
   ```

3. Tambahkan _return function_ berupa `HttpResponse` yang berisi parameter data hasil _query_ yang sudah diserialisasi menjadi JSON atau XML dan parameter `content_type` dengan _value_ `"application/xml"` (untuk format XML) atau `"application/json"` (untuk format JSON).

   - XML

     ```python
     def show_xml_by_id(request, id):
         data = MoodEntry.objects.filter(pk=id)
         return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
     ```

   - JSON

     ```python
     def show_json_by_id(request, id):
         data = MoodEntry.objects.filter(pk=id)
         return HttpResponse(serializers.serialize("json", data), content_type="application/json")
     ```

4. Buka `urls.py` yang ada pada direktori `main` dan _import_ fungsi yang sudah kamu buat tadi.

   ```python
   from main.views import show_main, create_mood_entry, show_xml, show_json, show_xml_by_id, show_json_by_id
   ```

5. Tambahkan _path_ URL ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.

   ```python
   ...
   path('xml/<str:id>/', show_xml_by_id, name='show_xml_by_id'),
   path('json/<str:id>/', show_json_by_id, name='show_json_by_id'),
   ...
   ```

6. Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000/xml/[id]/](http://localhost:8000/xml/[id]/) atau [http://localhost:8000/json/[id]/](http://localhost:8000/json/[id]/) di browser favoritmu untuk melihat hasilnya.

   :::tip
   Sesuaikan `[id]` pada URL di atas dengan id objek yang ingin dilihat. Kamu dapat mengambil salah satu ID objek yang ditampilkan ketika mengakses _endpoint_ `/json/`.
   :::

## Tutorial: Penggunaan Postman Sebagai _Data Viewer_

1. Pastikan server kamu sudah berjalan dengan perintah `python manage.py runserver`.

2. Buka Postman dan buatlah sebuah _request_ baru dengan _method_ `GET` dan _url_ [http://localhost:8000/xml/](http://localhost:8000/xml/) atau [http://localhost:8000/json/](http://localhost:8000/json/) untuk mengetes apakah data terkirimkan dengan baik.

   > Panduan Instalasi Postman dapat dilihat pada [Laman Resmi Postman](#referensi-tambahan).

   Contoh:
    ![Tampilan Halaman Postman](/img/2-tampilan-halaman-postman.png)



3. Klik tombol `Send` untuk mengirimkan _request_ tersebut.

4. Kamu akan melihat hasil _response_ dari _request_ tersebut pada bagian bawah Postman.

    ![Response Postman](/img/2-response-postman.png)


5. Kamu juga dapat mengubah _url_ menjadi [http://localhost:8000/xml/[id]](http://localhost:8000/xml/[id]) atau [http://localhost:8000/json/[id]](http://localhost:8000/json/[id]) untuk mengetes fungsi pengambilan data Mood Entry berdasarkan ID.

   ![Response Detail Postman](/img/2-response-detail-postman.png)

## Tutorial: Melakukan Push Ke PWS Secara Otomatis Menggunakan GitHub Actions

:::warning
Saat ini, PWS belum bisa kembali digunakan. Kamu bisa tetap mengikuti langkah-langkah yang akan dijelaskan selanjutnya, tetapi harap perhatikan bahwa **deployment pada PWS tidak akan berhasil**.
:::

Pada tutorial-tutorial sebelumnya, apabila kamu ingin melakukan _deployment_ ke PWS dan _push_ ke GitHub, kamu perlu melakukan push sebanyak dua kali, yaitu ke GitHub (`git push origin main`) dan ke PWS (`git push pws master`). Pada langkah tutorial ini, kamu akan membuat sebuah _script_ yang dapat membantumu melakukan _deployment_ ke PWS sekaligus dengan melakukan _push_ ke GitHub hanya dalam satu kali _push_. Kamu hanya perlu mengikuti langkah-langkah berikut dengan cermat.

1. Pada direktori utama proyek Djangomu, buatlah sebuah subdirektori bernama `.github`. Di dalam subdirektori tersebut, buat lagi sebuah subdirektori bernama `workflows`. Masuklah ke direktori tersebut (`.github/workflows/`).

2. Buatlah sebuah berkas bernama `deploy.yml`. Isi berkas tersebut dengan kode berikut.

   ```yml
   name: Push to PWS

   on:
     push:
       branches: [ main ]
       paths-ignore:
           - '**.md'
     pull_request:
       branches: [ main ]
       paths-ignore:
           - '**.md'

   jobs:
     build-and-push:
       runs-on: ubuntu-latest

       steps:
       - name: Checkout code
         uses: actions/checkout@v2
         with:
           fetch-depth: 0

       - name: Set up Git
         run: |
           git config --global user.name 'github-actions[bot]'
           git config --global user.email 'github-actions[bot]@users.noreply.github.com'

       - name: Check PWS remote, pull, merge, and push
         env:
           PWS_URL: ${{ secrets.PWS_URL }}
         run: |
             # Check if master branch exists locally
             if ! git show-ref --verify --quiet refs/heads/master; then
               echo "Creating master branch"
               git branch master
             fi
             
             # Switch to master branch
             git checkout master

             # Push to master branch and capture the output
             push_output=$(git push $PWS_URL main:master 2>&1)
             if [[ $? -ne 0 ]]; then
               echo "Push failed with output: $push_output"
               echo "Error: Unable to push changes. Please check the error message above and resolve any conflicts manually."
               exit 1
             fi
             echo "Push successful with output: $push_output"
   ```
   :::warning
   Jangan _push_ tambahan kode ini terlebih dahulu.
   :::

3. Pada repositori kamu di GitHub, buka halaman Settings > Secrets and variables > Actions. Kamu akan diarahkan ke halaman dengan tampilan seperti ini.

   ![Gambar halaman Action secrets and variables](/img/2-secrets-and-variables.png)

   Klik `New repository secret` untuk menambahkan variabel "rahasia" baru di repositorimu.

4. Isi `Name` dengan `PWS_URL`. Kemudian, isi `Secret` dengan data menggunakan format berikut:

   **https://`<username.sso>`:`<password proyek PWS>`@pbp.cs.ui.ac.id/`<username.sso>`/`<nama proyekmu>`**

   Sebagai contoh, apabila username SSO kamu adalah `hanni.pham`, password proyekmu adalah `abcd1234`, dan nama proyekmu adalah `supernatural`, maka kamu perlu mengisi `Secret` seperti ini:
   ```
   https://hanni.pham:abcd1234@pbp.cs.ui.ac.id/hanni.pham/supernatural
   ```

   ![Contoh pengisian secret](/img/2-new-secret.png)

   Apabila kamu sudah yakin URL yang kamu tuliskan benar, klik `Add Secret` untuk menambahkan _repository secret_ tersebut.

5. Pada berkas `settings.py` di proyekmu, tambahkan baris kode ini di bagian paling bawah berkas.

   ```python
   CSRF_TRUSTED_ORIGINS = ["http://localhost","http://127.0.0.1","http://<URL PWS KAMU>", "https://<URL_PWS_KAMU>"]
   ```

   Pastikan untuk mengganti `<URL_PWS_KAMU>` dengan URL _deployment_ proyek PWS-mu.

6. Lakukan git _add_, _commit_, dan _push_ ke GitHub. Setelah itu, buka halaman repositorimu. Tunggu beberapa saat, dan seharusnya kamu dapat melihat sebuah indikator kuning di samping pesan _commit_-mu.

   ![Contoh indikator kuning](/img/2-yellow.png)

7. Setelah indikator kuning berubah menjadi centang hijau, kamu dapat memeriksa halaman proyekmu pada PWS. Seharusnya, akan ada _deployment_ baru yang sedang dalam status _building_.

   :::tip
   Apabila indikatormu malah berubah menjadi silang merah, artinya terdapat kesalahan pada langkah-langkah yang kamu lakukan. Apabila kamu sudah memastikan isi berkas `deploy.yml` kamu benar, kamu dapat mencoba mengisi ulang _repository secret_ pada langkah 4.
   :::

Setelah menambahkan _script_ ini, kamu tidak perlu lagi menjalankan perintah seperti `git push pws master` setiap ingin _deploy_ ke PWS. Sekarang, setiap kali kamu melakukan _push_ ke GitHub pada _branch_ `main`, GitHub Actions akan secara otomatis melakukan _push_ ke proyek PWS-mu berdasarkan _commit_ terakhir yang kamu _push_, sehingga memicu proses _build_ pada proyek PWS-mu.

## Penutup

1. Setelah menyelesaikan tutorial ini, tampilan halaman web kamu seharusnya terlihat seperti ini.

   ![Web Result](/img/2-web-result.png)


2. Pada akhir tutorial ini, struktur direktori lokalmu akan terlihat seperti ini.

   ![Final Struktur Direktori](/img/2-final-struktur-direktori.png)

3. Sebelum melakukan langkah ini, **pastikan struktur direktori lokal sudah benar**. Selanjutnya, lakukan `add`, `commit` dan `push` untuk memperbarui repositori GitHub.

4. Jalankan perintah berikut untuk melakukan `add`, `commit` dan `push`.

   ```shell
   git add .
   git commit -m "<pesan_commit>"
   git push -u origin <branch_utama>
   ```

   - Ubah `<pesan_commit>` sesuai dengan keinginan. Contoh: `git commit -m "tutorial 2 selesai"`.
   - Ubah `<branch_utama>` sesuai dengan nama branch utamamu. Contoh: `git push -u origin main` atau `git push -u origin master`.

## Referensi Tambahan

- [Install and update Postman](https://learning.postman.com/docs/getting-started/installation/installation-and-updates)
- [Using a UUID as a primary key in Django models](https://stackoverflow.com/questions/3936182/using-a-uuid-as-a-primary-key-in-django-models-generic-relations-impact)

## Kontributor

- Martin Marcelino Tarigan
- Sabrina Atha Shania
- Muhammad Daffa'I Rafi Prasetyo
- Resanda Dezca Asyam
- Muhammad Nabil Mu'afa
- Isa Citra Buana & Juan Maxwell Tanaya (GitHub Actions script)

## Credits

Tutorial ini dikembangkan berdasarkan [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) dan [PBP Genap 2024](https://github.com/pbp-fasilkom-ui/genap-2024) yang ditulis oleh Tim Pengajar Pemrograman Berbasis Platform 2024. Segala tutorial serta instruksi yang dicantumkan pada repositori ini dirancang sedemikian rupa sehingga mahasiswa yang sedang mengambil mata kuliah Pemrograman Berbasis Platform dapat menyelesaikan tutorial saat sesi lab berlangsung.
