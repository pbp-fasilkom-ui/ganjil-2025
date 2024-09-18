---
sidebar_label: Tutorial 3
sidebar_position: 5
Path: docs/tutorial-3
---

# Tutorial 3: Autentikasi, Session, dan Cookies

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Tujuan Pembelajaran

Setelah menyelesaikan tutorial ini, mahasiswa diharapkan untuk dapat:

- Memahami konsep dasar autentikasi dalam pengembangan web.
- Memahami peran dan fungsi _cookie_ dan _session_ dalam pengembangan web.
- Memahami cara kerja _cookie_ dan _session_ dalam pengembangan web.
- Mengimplementasikan _cookie_ dan _session_ dalam proyek web.

## Pengenalan HTTP

HTTP (_HyperText Transfer Protocol_) adalah protokol yang digunakan untuk berkomunikasi antara _client_ dan _server_. HTTP bersifat _stateless_ yang berarti setiap transaksi/aktivitas yang dilakukan dianggap sebagai transaksi/aktivitas yang benar-benar **baru**, sehingga tidak ada data sebelumnya yang **disimpan** untuk transaksi/aktivitas saat ini.

Beberapa konsep dasar mengenai HTTP:

1. **_Client/Server_**: Interaksi dilakukan antar _client/server_. Klien adalah pihak yang melakukan _request_ dan server adalah pihak yang memberikan _response_.

2. **_Stateless_**: Setiap aktivitas (_request/response_) bersifat independen, tidak tersimpan pada aktivitas terdahulu.

3. **_OSI Layer/Model_**: Model _Open Systems Interconnection (OSI)_ menjelaskan 7 lapisan yang digunakan sistem komputer untuk berkomunikasi melalui jaringan. Model 7-layer OSI terdiri dari _Application Layer_, _Presentation Layer_, _Session Layer_, _Transport Layer_, _Network Layer_, _Data Link Layer_, dan _Physical Layer_.

4. **_Application Layer_**: Pada OSI Model yang disinggung di atas, website berjalan pada _application layer_. Sedangkan, proses _request/response_ terjadi pada _transport Layer_ yang umumnya menggunakan protokol TCP yang menentukan bagaimana data akan dikirim. _Application Layer_ tidak peduli apa yang dilakukan oleh _transport Layer_ (bagaimana data dikirim, diolah, dsb) karena _application layer_ hanya berfokus kepada _request_ dan _response_.

:::note
Lapisan OSI lainnya akan diajarkan pada mata kuliah Jaringan Komputer/Jaringan Komunikasi Data. Kamu dapat mencarinya sendiri jika kamu penasaran. 😉
:::

5. **_Client Actions Method_**: Terdapat metode-metode yang digunakan oleh _client_ saat melakukan _request_. Contoh: GET, POST, PUT, DELETE, dll. Penjelasan lebih detail dapat dibaca [di sini](https://www.restapitutorial.com/lessons/httpmethods.html).

6. **_Server Status Code_**: Merupakan status kode yang diberikan oleh server terhadap suatu _request_ pada sebuah halaman web. Contoh: 200 (OK), 404 (_Page Not Found_), 500 (_Internal Server Error_), dsb. Penjelasan lebih detail dapat dibaca [di sini](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

7. **_Headers_**: Merupakan informasi kecil yang dikirim bersamaan dengan _request_ dan _response_. Informasi-informasi tersebut berguna sebagai data tambahan yang digunakan untuk memproses _request/response_. Contoh: Pada _headers_, terdapat `content-type:json`. Artinya, tipe konten yang diminta/dikirim adalah `json`. _Headers_ juga menyimpan data _cookies_.

## Pengenalan Cookies & Session

Semua komunikasi antara klien dan server dilakukan melalui protokol HTTP, di mana HTTP merupakan _stateless protocol_. Artinya _state_ yang satu dengan yang lain tidak berhubungan (independen). Hal ini mengharuskan komputer klien yang menjalankan _browser_ untuk membuat koneksi TCP ke server **setiap kali melakukan _request_**.

Tanpa adanya koneksi persisten antara klien dan server, _software_ pada setiap sisi (_endpoint_) tidak dapat bergantung hanya pada koneksi TCP untuk melakukan _holding state_ atau _holding session state_.

### Apa yang dimaksud dengan _holding state_?

Sebagai contoh, kamu ingin mengakses suatu halaman A pada suatu web yang mensyaratkan pengaksesnya sudah _login_ ke dalam web. Kemudian kamu _login_ ke web tersebut dan berhasil membuka halaman A. Saat ingin pindah ke halaman B pada web yang sama, tanpa adanya suatu proses _holding state_ **maka kamu akan diminta untuk _login_ kembali**. Begitu yang akan terjadi setiap kali kamu mengakses halaman yang berbeda padahal masih pada web yang sama.

Proses memberitahu "siapa" yang sedang _login_ dan menyimpan data ini dikenal sebagai bentuk dialog antara klien-server dan merupakan dasar _session_ - _a semi-permanent exchange of information_. Merupakan hal yang sulit untuk membuat HTTP melakukan _holding state_ (karena HTTP merupakan _stateless protocol_). Oleh karena itu, dibutuhkan teknik untuk mengatasi masalah tersebut, yaitu _Cookie_ dan _Session_.

### Cara melakukan _holding state_?

Salah satu cara yang paling banyak digunakan untuk melakukan _holding state_ adalah dengan menggunakan _session ID_ yang disimpan sebagai _cookie_ pada komputer klien. _Session ID_ dapat dianggap sebagai suatu _token_ (barisan karakter) untuk mengenali _session_ yang unik pada aplikasi web tertentu. Daripada menyimpan semua jenis informasi sebagai _cookies_ pada klien seperti _username_, nama, dan password, hanya _Session ID_ yang disimpan.

_Session ID_ ini kemudian dapat dipetakan ke suatu struktur data pada sisi web server. Pada struktur data tersebut, kamu dapat menyimpan semua informasi yang kamu butuhkan. Pendekatan ini jauh lebih aman untuk menyimpan informasi mengenai pengguna, daripada menyimpannya pada _cookie_. Dengan cara ini, informasi tidak dapat disalahgunakan oleh klien atau koneksi yang mencurigakan.

Selain itu, pendekatan ini lebih "tepat" jika data yang akan disimpan ada banyak. Hal itu karena cookie hanya dapat menyimpan maksimal 4 KB data. Bayangkan kamu sudah _login_ ke suatu web/aplikasi dan mendapat _session ID_ (_session identifier_). Untuk dapat melakukan _holding state_ pada HTTP yang _stateless_, browser biasanya mengirimkan suatu _session ID_ ke server pada setiap _request_. Dengan begitu, setiap kali datang suatu _request_, maka server akan bereaksi (kurang lebih) "Oh, ini orang yang tepat!". Kemudian server akan mencari informasi _state_ di memori server atau di _database_ berdasarkan _session ID_ yang didapat, lalu mengembalikan data yang diminta.

Perbedaan penting yang perlu diingat adalah data _cookie_ disimpan pada sisi klien, sedangkan data _session_ biasanya disimpan pada sisi server. Untuk pembahasan lebih detail mengenai _stateless, stateful, cookie_, dan _session_ dapat dibaca [di sini](https://sethuramanmurali.wordpress.com/2013/07/07/stateful-stateless-cookie-and-session/).

Berikut tabel singkat yang menjelaskan perbedaan antara _cookies_, _session_, dan _local storage_ secara singkat.

|                       | **_Cookies_**  | **_Local Storage_** | **_Sessions_**     |
| --------------------- | -------------- | ------------------- | ------------------ |
| **Kapasitas**         | 4 KB           | 5 MB                | 5 MB               |
| **Teknologi Browser** | HTML4/HTML5    | HTML5               | HTML5              |
| **Aksesibilitas**     | Semua _window_ | Semua _window_      | _Tab_ yang sama    |
| **Kedaluwarsa**       | Diatur manual  | Selamanya           | Saat _tab_ ditutup |

Beberapa tautan video yang dapat memperkaya pengetahuan terkait materi ini:

- [Session & Cookies](https://www.youtube.com/watch?v=64veb6tKTm0&t=10s)
- [Cookies History](https://www.youtube.com/watch?v=I01XMRo2ESg)
- [Cookies vs. Local Storage vs. Session](https://www.youtube.com/watch?v=AwicscsvGLg)

## Pre-Tutorial Notes

Sebelum kamu memulai, serta untuk membantumu mengikuti tutorial 3 dengan baik, kami mengharapkan beberapa hasil berikut dari tutorial 2:

- Struktur direktori `mental-health-tracker` secara lokal adalah sebagai berikut.
```
   mental-health-tracker
   ├── .github\workflows
   │   └── deploy.yml
   ├── env
   ├── main
   │   ├── migrations
   │   │   ├── __init__.py
   │   │   ├── 0001_initial.py
   │   │   └── 0002_alter_moodentry_id.py
   │   ├── templates
   │   │   ├── create_mood_entry.html
   │   │   └── main.html
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
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
```

- Struktur repository `mental-health-tracker` pada GitHub adalah sebagai berikut.

![Struktur Repositori Github](/img/3-file-before-github.png)

## Tutorial: Membuat Fungsi dan Form Registrasi

Pada tutorial sebelumnya, kita sudah mencoba membuat sebuah form untuk menambahkan _mood entry_. Bagaimana? Mudah kan? Pada tutorial ini kita akan membuat halaman utama (`main`) menjadi _restricted_ dengan cara membuat akun untuk pengguna. Sehingga, pengguna yang ingin mengakses halaman utama `main` harus melakukan _login_ terlebih dahulu agar mendapatkan akses.

1. Aktifkan _virtual environment_ terlebih dahulu pada terminal. (Hint: Ingat tutorial 0!)

2. Buka `views.py` yang ada pada subdirektori `main` pada proyek kamu. Tambahkan _import_ `UserCreationForm` dan `messages` pada bagian paling atas.

   ```python
   from django.contrib.auth.forms import UserCreationForm
   from django.contrib import messages
   ```

   **Penjelasan Kode:**

   `UserCreationForm` adalah impor formulir bawaan yang memudahkan pembuatan formulir pendaftaran pengguna dalam aplikasi web. Dengan formulir ini, pengguna baru dapat mendaftar dengan mudah di situs web Anda tanpa harus menulis kode dari awal.

3. Tambahkan fungsi `register` di bawah ini ke dalam `views.py`. Fungsi ini berfungsi untuk menghasilkan formulir registrasi secara otomatis dan menghasilkan akun pengguna ketika data di-_submit_ dari form.

   ```python
   def register(request):
       form = UserCreationForm()

       if request.method == "POST":
           form = UserCreationForm(request.POST)
           if form.is_valid():
               form.save()
               messages.success(request, 'Your account has been successfully created!')
               return redirect('main:login')
       context = {'form':form}
       return render(request, 'register.html', context)
   ```

   **Penjelasan Kode:**

   - `form = UserCreationForm(request.POST)` digunakan untuk membuat `UserCreationForm` baru dari yang sudah di-impor sebelumnya dengan memasukkan QueryDict berdasarkan input dari _user_ pada `request.POST`.
   - `form.is_valid()` digunakan untuk memvalidasi isi input dari _form_ tersebut.
   - `form.save()` digunakan untuk membuat dan menyimpan data dari _form_ tersebut.
   - `messages.success(request, 'Your account has been successfully created!')` digunakan untuk menampilkan pesan kepada pengguna setelah melakukan suatu aksi.
   - `return redirect('main:show_main')` digunakan untuk melakukan _redirect_ setelah data _form_ berhasil disimpan.

4. Buatlah berkas HTML baru dengan nama `register.html` pada direktori `main/templates`. Isi dari `register.html` dapat kamu isi dengan _template_ berikut.

   ```html
   {% extends 'base.html' %}

   {% block meta %}
   <title>Register</title>
   {% endblock meta %}

   {% block content %}

   <div class="login">
     <h1>Register</h1>

     <form method="POST">
       {% csrf_token %}
       <table>
         {{ form.as_table }}
         <tr>
           <td></td>
           <td><input type="submit" name="submit" value="Daftar" /></td>
         </tr>
       </table>
     </form>

     {% if messages %}
     <ul>
       {% for message in messages %}
       <li>{{ message }}</li>
       {% endfor %}
     </ul>
     {% endif %}
   </div>

   {% endblock content %}
   ```

   :::tip
   Kita menggunakan tag `{{ form.as_table }}` untuk memudahkan membuat form yang berbentuk tabel. Untuk informasi lebih lanjut, kamu bisa membacanya [di sini](https://docs.djangoproject.com/en/5.1/topics/forms/#reusable-form-templates)
   :::

5. Buka `urls.py` yang ada pada subdirektori `main` dan impor fungsi yang sudah kamu buat tadi.

   ```python
   from main.views import register
   ```

6. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.

   ```python
    urlpatterns = [
        ...
        path('register/', register, name='register'),
    ]
   ```

Kita sudah menambahkan formulir registrasi akun dan membuat mekanisme `register`. Selanjutnya, kita akan membuat form _login_ agar pengguna dapat melakukan autentikasi akun.

## Tutorial: Membuat Fungsi Login

1. Buka kembali `views.py` yang ada pada subdirektori `main`. Tambahkan _import_ `authenticate`,  `login`, dan `AuthenticationForm` pada bagian paling atas.

   ```python
   from django.contrib.auth.forms import UserCreationForm, AuthenticationForm
   from django.contrib.auth import authenticate, login
   ```

   **Penjelasan Kode:**

   Singkatnya, fungsi `authenticate` dan `login` yang di-_import_ di atas adalah fungsi bawaan Django yang dapat digunakan untuk melakukan autentikasi dan login (jika autentikasi berhasil). Selengkapnya dapat dibaca [di sini](https://docs.djangoproject.com/en/4.2/topics/auth/default/).

2. Tambahkan fungsi `login_user` di bawah ini ke dalam `views.py`. Fungsi ini berfungsi untuk mengautentikasi pengguna yang ingin _login_.

   ```python
   def login_user(request):
      if request.method == 'POST':
         form = AuthenticationForm(data=request.POST)

         if form.is_valid():
               user = form.get_user()
               login(request, user)
               response = HttpResponseRedirect(reverse("main:show_main"))
               response.set_cookie('last_login', str(datetime.datetime.now()))
               return response

      else:
         form = AuthenticationForm(request)
      context = {'form': form}
      return render(request, 'login.html', context)
   ```

   **Penjelasan Kode:**

   - `authenticate(request, username=username, password=password)` digunakan untuk melakukan autentikasi pengguna berdasarkan username dan password yang diterima dari permintaan (_request_) yang dikirim oleh pengguna saat _login_. Jika kombinasi valid, maka objek `user` akan di-_return_. Jika tidak, maka akan mengembalikan `None`.
   - `login(request, user)` berfungsi untuk melakukan login terlebih dahulu. Jika pengguna valid, fungsi ini akan membuat _session_ untuk pengguna yang berhasil login.

3. Buatlah berkas HTML baru dengan nama `login.html` pada direktori `main/templates`. Isi dari `login.html` dapat kamu isi dengan _template_ berikut.

   ```html
   {% extends 'base.html' %}

   {% block meta %}
   <title>Login</title>
   {% endblock meta %}

   {% block content %}
   <div class="login">
     <h1>Login</h1>

     <form method="POST" action="">
       {% csrf_token %}
       <table>
         {{ form.as_table }}
         <tr>
           <td></td>
           <td><input class="btn login_btn" type="submit" value="Login" /></td>
         </tr>
       </table>
     </form>

     {% if messages %}
     <ul>
       {% for message in messages %}
       <li>{{ message }}</li>
       {% endfor %}
     </ul>
     {% endif %} Don't have an account yet?
     <a href="{% url 'main:register' %}">Register Now</a>
   </div>

   {% endblock content %}
   ```

4. Buka `urls.py` yang ada pada subdirektori `main` dan _import_ fungsi yang sudah kamu buat tadi.

   ```python
   from main.views import login_user
   ```

5. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.

   ```python
   urlpatterns = [
      ...
      path('login/', login_user, name='login'),
   ]
   ```

Kita sudah menambahkan form _login_ akun dan membuat mekanisme `login`. Selanjutnya, kita akan membuat mekanisme _logout_ dan menambahkan tombol _logout_ pada halaman _main_.

## Tutorial: Membuat Fungsi Logout

1. Buka kembali `views.py` yang ada pada subdirektori `main`. Tambahkan _import_ `logout` ini pada bagian paling atas.

   ```python
   from django.contrib.auth import logout
   ```

2. Tambahkan fungsi di bawah ini ke dalam fungsi `views.py`. Fungsi ini berfungsi untuk melakukan mekanisme _logout_.

   ```python
   def logout_user(request):
       logout(request)
       return redirect('main:login')
   ```

   **Penjelasan Kode:**

   - `logout(request)` digunakan untuk menghapus sesi pengguna yang saat ini masuk.
   - `return redirect('main:login')` mengarahkan pengguna ke halaman login dalam aplikasi Django.

3. Bukalah berkas `main.html` yang ada pada direktori `main/templates` dan tambahkan potongan kode di bawah ini setelah _hyperlink tag_ untuk _Add New Mood Entry_.
   ```html
   ...
   <a href="{% url 'main:logout' %}">
     <button>Logout</button>
   </a>
   ...
   ```

   **Penjelasan Kode:**

   - `{% url 'main:logout' %}` digunakan untuk mengarah ke URL secara dinamis berdasarkan `app_name` dan `name` yang sudah didefinisikan di `urls.py`.
      Secara umum, penulisannya adalah dengan `{% url 'app_name:view_name' %}`:
      - `app_name` merupakan nama *app* yang didefinisikan di dalam berkas `urls.py`. Jika *app* menggunakan atribut `app_name` di `urls.py`, maka ini akan dipakai untuk merujuk pada *app* tersebut. Jika `app_name` tidak didefinisikan maka nama *app* yang digunakan adalah nama dari folder *app* yang dibuat.
      - `view_name` merupakan nama dari URL yang diinginkan, didefinisikan melalui parameter `name` dalam `path()` di `urls.py`.
      [Tampilan urls.py](/img/3-tampilan-urls-py.png)

4. Buka `urls.py` yang ada pada subdirektori `main` dan _import_ fungsi yang sudah kamu buat sebelumnya.

   ```python
   from main.views import logout_user
   ```

5. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah di-_import_ sebelumnya.

   ```python
   urlpatterns = [
      ...
      path('logout/', logout_user, name='logout'),
   ]
   ```

Kita sudah membuat mekanisme `logout` dan menyelesaikan sistem autentikasi dalam proyek ini.

## Tutorial: Merestriksi Akses Halaman Main

1. Buka kembali `views.py` yang ada pada subdirektori `main` dan tambahkan _import_ `login_required` pada bagian paling atas.

   ```python
   from django.contrib.auth.decorators import login_required
   ```

   **Penjelasan Kode:**

   Kode `from django.contrib.auth.decorators import login_required` digunakan untuk mengimpor sebuah _decorator_ yang bisa mengharuskan pengguna masuk (_login_) terlebih dahulu sebelum dapat mengakses suatu halaman web.

2. Tambahkan potongan kode `@login_required(login_url='/login')` di atas fungsi `show_main` agar halaman _main_ hanya dapat diakses oleh pengguna yang sudah _login_ (terautentikasi).

   ```python
   ...
   @login_required(login_url='/login')
   def show_main(request):
   ...
   ```

Setelah melakukan restriksi akses halaman main, jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000/](http://localhost:8000/) di browser favoritmu untuk melihat hasilnya. Seharusnya halaman yang muncul bukanlah daftar _mood entry_ di halaman _main_, tetapi akan di-_redirect_ ke halaman login.

## Tutorial: Menggunakan Data Dari _Cookies_

Sekarang, kita akan melihat penggunaan _cookies_ dengan menambahkan data _last login_ dan menampilkannya ke halaman _main_.

1. Lakukan _logout_ terlebih dahulu apabila kamu sedang menjalankan aplikasi Django-mu.

2. Buka kembali `views.py` yang ada pada subdirektori `main`. Tambahkan _import_ `HttpResponseRedirect`, `reverse`, dan `datetime` pada bagian paling atas.

   ```python
   import datetime
   from django.http import HttpResponseRedirect
   from django.urls import reverse
   ```

:::note
Perhatikan indentasi kode kamu, pastikan tidak terdapat _dead code_ pada fungsi tersebut.
:::

4. Pada fungsi `show_main`, tambahkan potongan kode `'last_login': request.COOKIES['last_login']` ke dalam variabel `context`. Berikut adalah contoh kode yang sudah diubah.

   ```python
   context = {
       'name': 'Pak Bepe',
       'class': 'PBP D',
       'npm': '2306123456',
       'mood_entries': mood_entries,
       'last_login': request.COOKIES['last_login'],
   }
   ```

   **Penjelasan Kode:**

   `'last_login': request.COOKIES['last_login']` berfungsi menambahkan informasi _cookie last_login_ pada response yang akan ditampilkan di halaman web.

5. Ubah fungsi `logout_user` menjadi seperti potongan kode berikut.

   ```python
   def logout_user(request):
       logout(request)
       response = HttpResponseRedirect(reverse('main:login'))
       response.delete_cookie('last_login')
       return response
   ```

   **Penjelasan Kode:**

   `response.delete_cookie('last_login')` berfungsi untuk menghapus _cookie_ `last_login` saat pengguna melakukan `logout`.

6. Buka berkas `main.html` dan tambahkan potongan kode berikut di setelah tombol _logout_ untuk menampilkan data _last login_.

   ```html
   ...
   <h5>Sesi terakhir login: {{ last_login }}</h5>
   ...
   ```

7. Silakan _refresh_ halaman _login_ (atau jalankan proyek Django-mu dengan perintah `python manage.py runserver` jika kamu belum menjalankan proyekmu) dan cobalah untuk _login_. Data _last login_ kamu akan muncul di halaman _main_.

8. Jika kamu menggunakan browser Google Chrome, untuk melihat data _cookie_ `last_login`, kamu dapat mengakses fitur _inspect element_ dan membuka bagian _Application/Storage_. Klik bagian _Cookies_ dan kamu dapat melihat data _cookies_ yang tersedia. Selain `last_login`, kamu juga dapat melihat data `sessionid` dan `csrftoken`. Berikut adalah contoh tampilannya.

   ![Gambar Halaman Main beserta Data Cookies](/img/3-tampilan-main-cookies.png)

:::info
Untuk yang menggunakan browser Safari, Kamu dapat melihat *cookies* pada browser dengan `inspect element > Storage > Cookies`. Jika tidak menemukan *inspect element*, kamu dapat mengaktifkannya terlebih dahulu melalui `Safari > Preferences > Advanced` dan centang pilihan `Show Develop menu in menu bar`. Setelah itu, Kamu bisa membuka fitur *Inspect Element* dengan klik kanan pada halaman dan memilih *Inspect Element*, lalu navigasi ke `Storage > Cookies` untuk melihat data *cookies* seperti `last_login`, `sessionid`, dan `csrftoken`.
:::

9. Jika kamu melakukan _logout_ dan membuka bagian riwayat _cookie_, _cookie_ yang dibuat sebelumnya akan hilang dan dibuat ulang ketika kamu _login_ kembali.

:::note
Sebelum melanjutkan ke tutorial berikutnya, cobalah untuk **membuat satu akun** pada halaman web kamu.
:::

## Tutorial: Menghubungkan Model `MoodEntry` dengan `User`

:::danger
Kamu perlu mengikuti tutorial secara berurut dari awal sebelum menjalankan bagian berikut. Jika kamu tidak mengikuti tutorial secara berurut, maka kami tidak bertanggung jawab atas _error_ di luar pembahasan tutorial yang dapat muncul dari bagian tutorial berikut.
:::

Terakhir, kita akan menghubungkan setiap objek `MoodEntry` yang akan dibuat dengan pengguna yang membuatnya, sehingga pengguna yang sedang terotorisasi hanya melihat _mood entries_ yang telah dibuat sendiri. Untuk itu, ikuti langkah-langkah berikut:

1. Buka `models.py` yang ada pada subdirektori `main` dan tambahkan kode berikut pada dibawah baris kode untuk mengimpor model:

   ```python
   ...
   from django.contrib.auth.models import User
   ...
   ```

2. Pada model `MoodEntry` yang sudah dibuat, tambahkan potongan kode berikut:

   ```python
   class MoodEntry(models.Model):
       user = models.ForeignKey(User, on_delete=models.CASCADE)
       ...
   ```

   **Penjelasan Kode:**

   Potongan kode diatas berfungsi untuk menghubungkan satu _mood entry_ dengan satu _user_ melalui sebuah _relationship_, dimana sebuah _mood entry_ pasti terasosiasikan dengan seorang _user_.

:::tip
Kamu akan mempelajari lebih lanjut terkait `ForeignKey` pada mata kuliah Basis Data. Penjelasan lebih lanjut terkait `ForeignKey` pada Django dapat dibaca [di sini](https://docs.djangoproject.com/en/4.2/topics/db/examples/many_to_one/).
:::

3. Buka kembali `views.py` yang ada pada subdirektori `main`, dan ubah potongan kode pada fungsi `create_mood_entry` menjadi sebagai berikut:

   ```python
   def create_mood_entry(request):
       form = MoodEntryForm(request.POST or None)

       if form.is_valid() and request.method == "POST":
           mood_entry = form.save(commit=False)
           mood_entry.user = request.user
           mood_entry.save()
           return redirect('main:show_main')

       context = {'form': form}
       return render(request, "create_mood_entry.html", context)
    ...
   ```

   **Penjelasan Kode:**

   Parameter `commit=False` yang digunakan pada potongan kode diatas berguna untuk mencegah Django agar tidak langsung menyimpan objek yang telah dibuat dari form langsung ke database. Hal tersebut memungkinkan kita untuk memodifikasi terlebih dahulu objek tersebut sebelum disimpan ke _database_. Pada kasus ini, kita akan mengisi field `user` dengan objek `User` dari return value `request.user` yang sedang terotorisasi untuk menandakan bahwa objek tersebut dimiliki oleh pengguna yang sedang _login_.

4. Ubah value dari `mood_entries` dan `context` pada fungsi `show_main` menjadi seperti berikut.

   ```python
   def show_main(request):
       mood_entries = MoodEntry.objects.filter(user=request.user)

       context = {
            'name': request.user.username,
            ...
       }
   ...
   ```

   **Penjelasan Kode:**

   - Potongan kode diatas berfungsi untuk menampilkan objek `Mood Entry` yang terasosiasikan dengan pengguna yang sedang _login_. Hal tersebut dilakukan dengan menyaring seluruh objek dengan hanya mengambil `Mood Entry` yang dimana field `user` terisi dengan objek `User` yang sama dengan pengguna yang sedang login.
   - Kode `request.user.username` berfungsi untuk menampilkan _username_ pengguna yang _login_ pada halaman _main_.

:::danger
Sebelum menjalankan kode pada langkah selanjutnya, pastikan bahwa di _database_ sudah ada minimal satu _user_. Hal ini diperlukan karena pada langkah selanjutnya akan diminta untuk menetapkan nilai _default_ pada _field user_ di semua _row_ yang sudah ada. Proses migrasi model akan _error_ jika tidak ada _user_ yang tercatat sebelumnya.
:::

5. Simpan semua perubahan, dan lakukan migrasi model dengan `python manage.py makemigrations`.

6. Seharusnya, akan muncul _error_ saat melakukan migrasi model. Pilih `1` untuk menetapkan _default value_ untuk _field user_ pada semua _row_ yang telah dibuat pada _database_.

   ![Migrations-1](/img/3-migration-pertama.png)

7. Ketik angka 1 lagi untuk menetapkan _user_ dengan ID 1 (yang sudah kita buat sebelumnya) pada model yang sudah ada.

   ![Migrations-2](/img/3-migration-kedua.png)

8. Lakukan `python manage.py migrate` untuk mengaplikasikan migrasi yang dilakukan pada poin sebelumnya.

9. Langkah terakhir, kita harus mempersiapkan aplikasi web kita untuk _environtment production_. Untuk itu,  tambahkan sebuah import baru pada `settings.py` yang ada pada subdirektori `mental_health_tracker`

      ```python
      import os
      ```

      Kemudian, ganti variabel `DEBUG` dari berkas `settings.py` menjadi seperti ini.

      ```python
      PRODUCTION = os.getenv("PRODUCTION", False)
      DEBUG = not PRODUCTION
      ```

Jalankan proyek Django-mu dengan perintah `python manage.py runserver` dan bukalah [http://localhost:8000/](http://localhost:8000/) di browser favoritmu untuk melihat hasilnya. Cobalah untuk membuat akun baru dan login dengan akun yang baru dibuat. Amatilah halaman utama, _mood entry_ yang tadi telah dibuat dengan akun sebelumnya tidak akan ditampilkan di halaman pengguna akun yang baru saja kamu buat. Hal tersebut berarti kamu sudah berhasil menghubungkan objek `Mood Entry` dengan `User` yang membuatnya.

## Akhir Kata

Selamat! Kamu telah menyelesaikan Tutorial 3 dengan baik. 😄

Setelah kamu menyelesaikan seluruh tutorial di atas, harapannya Kamu sekarang lebih paham tentang penggunaan _form_, autentikasi, _session_, dan _cookie_ pada _framework_ Django.

1. Setelah menyelesaikan tutorial ini, tampilan halaman web kamu seharusnya terlihat seperti ini.
   - Tampilan halaman [http://localhost:8000/login](http://localhost:8000/login)
      ![Tampilan Halaman Login](/img/3-tampilan-halaman-login.png)
   - Tampilan halaman [http://localhost:8000/](http://localhost:8000/) setelah berhasil login
      ![Tampilan Halaman Utama](/img/3-tampilan-halaman-utama.png)

2. Pada akhir tutorial ini, struktur subdirektori `main` pada lokalmu terlihat seperti ini.
   ```
   mental-health-tracker
   ├── .github\workflows
   │   └── deploy.yml
   ├── env
   ├── main
   │   ├── migrations
   │   │   ├── __init__.py
   │   │   ├── 0001_initial.py
   │   │   ├── 0002_alter_moodentry_id.py
   │   │   └── 0003_moodentry_user.py
   │   ├── templates
   │   │   ├── create_mood_entry.html
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
   ├── .gitignore
   ├── manage.py
   └── requirements.txt
   ```

3. Sebelum melakukan langkah ini, **pastikan struktur direktori lokal sudah benar**. Selanjunya, lakukan `add`, `commit` dan `push` untuk memperbarui repositori GitHub.

4. Jalankan perintah berikut untuk melakukan `add`, `commit` dan `push`.

   ```shell
   git add .
   git commit -m "<pesan_commit>"
   git push -u origin <branch_utama>
   ```

   - Ubah `<pesan_commit>` sesuai dengan keinginan. Contoh: `git commit -m "tutorial 3 selesai"`.
   - Ubah `<branch_utama>` sesuai dengan nama branch utamamu. Contoh: `git push -u origin main` atau `git push -u origin master`.

## Kontributor

- Abbilhaidar Farras Zulfikar
- Clarence Grady
- Reyhan Zada Virgiwibowo
- Fernando Valentino Sitinjak
- Alden Luthfi

## Credits

Tutorial ini dikembangkan berdasarkan [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) yang ditulis oleh Tim Pengajar Pemrograman Berbasis Platform 2024/2025. Segala tutorial serta instruksi yang dicantumkan pada repositori ini dirancang sedemikian rupa sehingga mahasiswa yang sedang mengambil mata kuliah Pemrograman Berbasis Platform dapat menyelesaikan tutorial saat sesi lab berlangsung.