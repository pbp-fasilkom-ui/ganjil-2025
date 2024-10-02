---
sidebar_label: Tutorial 5
sidebar_position: 7
Path: docs/tutorial-5
---

# Tutorial 5: JavaScript dan AJAX

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Tujuan Pembelajaran

Setelah menyelesaikan tutorial ini, mahasiswa diharapkan untuk dapat:

- Memahami fungsi JavaScript pada *front-end development*
- Menggunakan JavaScript secara dasar
- Menerapkan AJAX dan Fetch API dengan aman

## JavaScript

### Pengenalan JavaScript

JavaScript merupakan bahasa pemrograman multi-paradigma tingkat tinggi lintas platform (*cross-platform high-level multi-paradigm programming language*). Sifat multi-paradigma membuat JavaScript mendukung konsep pemrograman berbasis obyek, pemrograman imperatif, dan pemrograman fungsional. JavaScript sendiri merupakan implementasi dari ECMAScript, yang merupakan inti dari bahasa JavaScript. Beberapa implementasi lain dari ECMAScript yang mirip dengan JavaScript antara lain JScript (Microsoft) dan ActionScript (Adobe).

JavaScript, bersama dengan HTML dan CSS, menjadi tiga teknologi utama yang dipakai pada pengembangan web. Pada dasarnya, keuntungan menggunakan JavaScript dalam pengembangan web adalah manipulasi halaman web dapat dilakukan secara dinamis dan interaksi antara halaman web dengan pengguna dapat meningkat. Oleh karena itu, hampir semua situs web modern saat ini menggunakan JavaScript dalam halaman web mereka untuk memberikan pengalaman terbaik kepada pengguna. Beberapa contoh yang dapat kita lakukan dengan menggunakan JavaScript antara lain menampilkan informasi berdasarkan waktu, mengenali jenis peramban pengguna, melakukan validasi form atau data, membuat *cookies* (bukan kue, namun [HTTP *cookies*](https://en.wikipedia.org/wiki/HTTP_cookie)), mengganti *styling* dan CSS suatu *element* secara dinamis, dan lain sebagainya.

Pada pengembangan web umumnya kode JavaScript digunakan pada *client-side* suatu web (*client-side JavaScript*), namun beberapa jenis kode JavaScript saat ini digunakan pada *server-side* suatu web (*server-side JavaScript*) seperti **node.js**. Istilah *client-side* menunjukkan bahwa kode JavaScript akan dieksekusi atau dijalankan pada peramban pengguna, bukan pada server situs web. Hal ini berarti kompleksitas kode JavaScript tidak akan memengaruhi performa server situs web tersebut namun memengaruhi performa peramban web dan komputer; semakin kompleks kode JavaScript, maka semakin banyak memori komputer yang dikonsumsi oleh peramban web.

Pada mata kuliah PBP, kita hanya akan fokus kepada kode *client-side JavaScript*.

### Tahapan Eksekusi JavaScript oleh Peramban

Perhatikan diagram berikut untuk mengamati tahapan eksekusi JavaScript oleh peramban web.

![javascript-works](https://preview.ibb.co/e258TG/Screenshot_from_2017_10_31_14_29_13.png)

Setelah peramban mengunduh halaman HTML web maka tepat dimana tag `<script></script>` berada, peramban akan melihat *tag script* tersebut, apakah tag tersebut berisi kode *embedded* JavaScript atau merujuk berkas eksternal JavaScript. Jika merujuk pada berkas eksternal JavaScript, maka peramban akan mengunduh berkas tersebut terlebih dahulu.

### Penulisan JavaScript

Penulisan JavaScript dapat dilakukan dengan ***embedded JavaScript*** atau ***external JavaScript***. Kode JavaScript dapat didefinisikan atau dituliskan secara *embedded* pada berkas HTML maupun secara terpisah pada berkas tersendiri. Jika ditulis dalam berkas terpisah dari HTML, ekstensi berkas yang digunakan untuk berkas JavaScript adalah `.js`. Berikut contoh beberapa pendefinisian dari JavaScript.

JavaScript dapat diletakkan pada *head* atau *body* dari halaman HTML. Selain itu, kode JavaScript **harus** dimasukkan di antara tag `<script>` dan `</script>`. Kamu dapat meletakkan lebih dari satu *tag script* yang berisi JavaScript pada suatu berkas HTML.

#### Embedded JavaScript pada HTML

```html title="index.html"
<script type="text/JavaScript">
    alert("Hello World!");
</script>
```

#### External JavaScript pada HTML

```html title="index.html"
<script type="text/JavaScript" src="js/script.js"></script>
```

```javascript title="js/script.js"
alert("Hello World!");
```

Pada berkas eksternal JavaScript, tag `<script>` tidak perlu lagi ditambahkan.

Memisahkan JavaScript pada berkas tersendiri dapat memberikan beberapa keuntungan seperti kode dapat digunakan di berkas HTML lain, kode JavaScript dan HTML tidak bercampur sehingga lebih fokus saat mengembangkan aplikasi, serta mempercepat proses pemuatan halaman. berkas `.js` biasanya akan di-*cache* oleh peramban sehingga jika kita membuka halaman yang sama dan tidak ada perubahan pada berkas `.js`, maka peramban tidak akan meminta berkas `.js` tersebut kepada server lagi, namun akan menggunakan berkas dari *cache* yang sudah disimpan sebelumnya.

### Eksekusi JavaScript

Setelah JavaScript sudah dimuat dengan sempurna, maka peramban akan langsung mulai mengeksekusi kode JavaScript. Jika kode tersebut BUKAN merupakan *event-triggered*, maka kode langsung dieksekusi. Jika kode tersebut merupakan *event-triggered*, maka kode tersebut hanya akan dieksekusi jika *event* yang didefinisikan terpicu (*triggered*).

```javascript
// langsung dieksekusi
alert("Hello World");

// langsung dieksekusi
var obj = document.getElementById("object");
// langsung dieksekusi, menambahkan event handler onclick untuk element object
obj.onclick = function () {
    // hanya dieksekusi jika element 'object' di klik
    alert("You just clicked the object!");
};
```

### Sintaks JavaScript

#### Variabel

Mendefinisikan variabel pada JavaScript cukup mudah. Contohnya seperti berikut.

```javascript
var example = 0; // var example merupakan sebuah bilangan
var example = "example"; // var example merupakan sebuah string
var example = true; // var example merupakan sebuah boolean
```

JavaScript dapat menampung banyak tipe data; mulai dari string, integer, hingga *object* sekalipun. Berbeda dengan Java yang penandaan tipe datanya dibedakan dengan *head variable* (contohnya kamu ingin membuat variabel dengan tipe data `int`, maka sintaknya seperti `int x = 9`), JavaScript mempunyai ciri khas *loosely typed* atau *dynamic language*, yakni kamu tidak perlu menuliskan tipe data pada *head variable* dan JavaScript nantinya akan secara otomatis membaca tipe data kamu berdasarkan standar yang ada (seperti pada contoh di atas).

Ada beberapa aturan dalam pemilihan *indentifiers* atau nama variabel dalam JavaScript. Karakter pertama **harus** merupakan alfabet, *underscore* (`_`), atau karakter dolar (`$`). Selain itu, JavaScript *identifiers* bersifat *case sensitive*.

#### Penggabungan String

Dalam JavaScript, kita juga dapat menyambungkan `string` dengan `string` lainnya seperti pada Java.

```javascript
var str1 = "PBP" + " " + "Fun";
var str2 = "PBP";
var str3 = "Fun";
var str4 = str2 + " " + str3;
var str5 = "Fun";
var str6 = `PBP ${str5}`;  // Memiliki hasil yang sama seperti "PBP" + " " + str5
```

### Ruang Lingkup JavaScript

#### Variabel Lokal

Variabel yang didefinisikan **di dalam** fungsi bersifat lokal, sehingga hanya dapat diakses oleh kode didalam fungsi tersebut.

```javascript
// kode diluar fungsi thisFunction() tidak dapat mengakses variabel courseName
function thisFunction() {
    var courseName = "PBP";
    // kode di dalam fungsi ini dapat mengakses variabel courseName
}
```

#### Variabel Global

Variabel yang didefinisikan **di luar** fungsi bersifat global dan dapat diakses oleh kode lain dalam berkas JavaScript tersebut.

```javascript
var courseName = "PBP";
function thisFunction() {
    // kode di dalam fungsi ini dapat mengakses variabel courseName
}
```

#### Variabel Auto Global

Value yang di-*assign* pada variabel yang belum dideklarasikan otomatis menjadi variabel global, walaupun variabel tersebut berada di dalam suatu fungsi.

```javascript
thisFunction(); // fungsi thisFunction() perlu dipanggil terlebih dahulu
console.log(courseName); // cetak "PBP" pada JavaScript console
function thisFunction() {
    courseName = "PBP";
}
```

#### Mengakses Variabel Global dari HTML

Kamu dapat mengakses variabel yang berada dalam berkas JavaScript pada berkas HTML yang memuat berkas JavaScript tersebut.

```html
...
<input type="text" onclick="this.value=courseName" />
...
```

```javascript
...
var courseName = "PBP";
...
```

### Function dan Event

*Function* adalah sekumpulan grup dari kode-kode yang bisa dipanggil di mana pun pada bagian kode program (mirip dengan `method` pada Java). Hal ini mengurangi redundansi kode yang ada (mengurangi kode-kode yang dapat sama berulang-ulang). Selain itu, *function* pada JavaScript sangat berguna untuk memudahkan elemen pemanggilan secara dinamis. *Function* dapat dipanggil sesama *function* dan dapat juga dipanggil karena *event* (akan dijelaskan di bawah). Sebagai contoh, berikut kode yang terdapat pada `index.html`.

```html title="index.html"
...
<input type="button" value="magicButton" id="magicButton" onclick="hooray();" />
...
```

Kemudian berikut adalah kode pada `javascript.js`.

```javascript title="javascript.js"
...
function hooray() {
    alert("Yahoo!");
}
...
```

Apabila `magicButton` ditekan, maka fungsi `onclick` akan menjalankan *function* `hooray()` pada `javascript.js`, lalu muncul *alert* sesuai yang sudah di-*assign* sebelumnya.

Kode `onclick` sebenarnya adalah salah satu contoh kemampuan JavaScript yang disebut *event*. *Event* adalah kemampuan JavaScript untuk membuat sebuah situs web dinamis. Maksud dari `onclick` adalah penanda apa yang akan dilakukan JavaScript jika elemen tersebut ditekan. Selain itu, *event* biasanya diberikan sebuah fungsi yang berguna sebagai perintah-perintah untuk JavaScript. Selain itu, banyak contoh-contoh *event* lainnya seperti `onchange`, `onmouseover`, `onmouseout`, dan lain sebagainya yang bisa kamu baca pada tautan [ini](https://www.w3schools.com/js/js_events.asp).

### JavaScript DOM

#### HTML DOM

HTML DOM (*Document Object Model*) adalah standar bagaimana mengubah, mengambil, dan menghapus HTML *elements*. HTML DOM dapat diakses melalui JavaScript atau dengan bahasa pemrograman lainnya. Detail lengkapnya dapat dilihat [di sini](https://www.w3schools.com/js/js_htmldom.asp).

Berikut adalah contoh implementasinya.

```html
...     
<div>
    <p onclick="myFunction()" id="demo">Example of HTML DOM</p>
</div>
...
```

```javascript
...
function myFunction() {
    document.getElementById("demo").innerHTML = "YOU CLICKED ME!";
}
...
```

#### CSS DOM

Sama dengan HTML DOM, CSS DOM dapat mengubah CSS secara dinamis melalui JavaScript. Detail lengkapnya dapat dilihat [di sini](https://www.w3schools.com/js/js_htmldom_css.asp).

Berikut adalah contoh implementasinya.

```html title="index.html"
...
<p id="blueText" onclick="changeColor()">Click me v2</p>
...
```

```javascript title="javascript.js"
...
function changeColor(){
    document.getElementById("blueText").style.color="blue";
}
...
```

## AJAX

### Pengenalan AJAX

AJAX merupakan singkatan dari ***A**synchronous **J**avaScript **A**nd **X**ML*.

AJAX bukanlah merupakan sebuah bahasa pemrograman, melainkan sebuah teknologi yang memadukan peramban web (untuk meminta data dari *web server*) dengan JavaScript dan HTML DOM (untuk menampilkan data). AJAX dapat menggunakan XML untuk mengirim data, tetapi AJAX juga dapat menggunakan teks ataupun JSON untuk mengirim data. AJAX memungkinkan halaman web untuk memperbarui data secara asinkronus dengan mengirimkan data ke peladen di balik layar. Hal tersebut berarti bahwa kita dapat memperbarui sebagian elemen data pada halaman tanpa harus me-*reload* halaman secara keseluruhan.

Berikut ini adalah diagram cara kerja AJAX.

![ajax-works](https://www.w3schools.com/js/pic_ajax.gif)

1. Sebuah *event* terjadi pada halaman web (contohnya tombol *submit data* ditekan)
2. Sebuah `XMLHttpRequest` *object* dibuat oleh JavaScript
3. `XMLHttpRequest` *object* mengirimkan *request* ke server
4. Server memproses *request* tersebut
5. Server mengembalikan *response* kembali kepada halaman web
6. *Response* dibaca oleh JavaScript
7. Aksi berikutnya akan dipicu oleh JavaScript sesuai dengan langkah yang dibuat (contohnya memperbarui data di halaman tersebut)

`XMLHttpRequest` sebelumnya merupakan cara standar untuk melakukan permintaan AJAX di JavaScript. Namun, XMLHttpRequest memiliki beberapa kelemahan, seperti penanganan yang kurang rapi ketika bekerja dengan _promises_ dan _callback_ serta keterbatasan dalam mendukung alur kode yang lebih modern.

Oleh karena itu, `fetch()` diperkenalkan sebagai API baru untuk melakukan permintaan HTTP dengan sintaks yang lebih sederhana dan mendukung _promises_ secara langsung. Hal ini memungkinkan pengembang menulis kode yang lebih mudah dibaca, dikelola, dan lebih cocok dengan paradigma asinkron modern seperti _async_/_await_. `fetch()` juga lebih fleksibel dalam menangani format data yang berbeda serta mendukung *API* yang lebih baik untuk menangani kesalahan atau respons HTTP. Penjelasan lebih lanjut terhadap perbedaan `fetch` dan `XMLHttpRequest` dapat dilihat di tautan [ini](https://www.tutorialspoint.com/ajax/fetch_api_vs_xmlhttprequest.htm).

Pada PBP kali ini, kamu akan melakukan AJAX pada peramban web dengan menggunakan fungsi `fetch()` yang diberikan oleh JavaScript. Sebagai gambaran besar, penggunaan `fetch()` untuk melakukan pemanggilan AJAX dapat dilihat di tautan [ini](https://www.w3schools.com/jsref/api_fetch.asp).

### Fetch API

Fetch API merupakan API baru yang diperkenalkan pada ECMAScript 2020 sebagai standar baru untuk membuat *request* dengan `Promise`. Fetch API menyediakan antarmuka untuk mengambil sumber daya (termasuk di seluruh jaringan). API ini merupakan pengganti yang lebih kuat dan fleksibel untuk [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest). Fetch API secara umum digunakan untuk mengimplementasikan AJAX secara lebih mudah daripada AJAX dengan `XMLHttpRequest`. Fetch API juga mendukung lebih banyak metode HTTP dan header HTTP daripada AJAX biasa.

Fungsi `fetch()` memiliki beberapa parameter, yaitu:

- `url`: URL dari sumber daya yang akan diminta
- `method`: Metode HTTP yang akan digunakan
- `headers`: Header HTTP yang akan dikirim
- `body`: Isi dari permintaan HTTP

Fungsi `fetch()` mengembalikan objek `Response`. Objek `Response` memiliki beberapa properti, yaitu:

- `status`: Kode `status` HTTP dari respons
- `headers`: Header HTTP dari respons
- `body`: Isi dari respons

Kamu dapat mempelajari Fetch API lebih lanjut pada tautan [ini](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).

### Fungsi Async dan Await

Sebelum mempelajari penggunaan fungsi `fetch()`, ada baiknya kita mempelajari fungsi `async` dan `await` yang memungkinkan pengimplementasian AJAX tanpa perlu menggunakan *library* eksternal, seperti [jQuery](https://jquery.com/).

Fungsi `async` dan `await` merupakan fungsi baru yang diperkenalkan di ECMAScript 2017. Fungsi `async` digunakan untuk menandai fungsi sebagai fungsi yang dapat mengembalikan nilai secara asinkronus, sedangkan fungsi `await` digunakan untuk menunggu hasil dari fungsi `async`.

Kamu dapat mempelajari fungsi `async` dan `await` lebih lanjut pada tautan [ini](https://www.w3schools.com/js/js_async.asp).

### Penggunaan Fetch API

Fetch API menyediakan antarmuka JavaScript untuk mengakses dan memanipulasi bagian-bagian protokol, seperti *requests* dan *responses*. API ini juga menyediakan metode `fetch()` global yang menyediakan cara yang mudah dan logis untuk mengambil sumber daya secara asinkronus pada seluruh jaringan.

Tidak seperti `XMLHttpRequest` yang merupakan API berbasis *callback*, Fetch API berbasis `Promise` dan menyediakan alternatif yang lebih baik dan dapat dengan mudah digunakan pada *service worker*. Fetch API juga mengintegrasikan konsep HTTP tingkat lanjut seperti CORS dan ekstensi lain ke HTTP.

Berikut adalah contoh penggunaan Fetch API dengan fungsi `async` dan `await` untuk melakukan AJAX.

```javascript
async function fetchData() {
    const response = await fetch("https://jokes-bapack2-api.yuana.id/v1/text/random");
    const data = await response.json();
    return data;
}

const joke = await fetchData();
console.log(joke);
```

Kode di atas akan melakukan AJAX untuk meminta data dari API lelucon bapak-bapak masa kini secara asinkronus. Hasil dari AJAX akan disimpan dalam variabel `joke`.

Kamu dapat mempelajari penggunaan Fetch API lebih lanjut pada tautan [ini](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

## Tutorial: Menambahkan _Error Message_ Pada Login

Untuk memudahkan proses _login_ pada aplikasi anda, berikan _conditional_ pada _view_ `login_user` anda, sehingga kodenya menjadi seperti ini.

```python title="main/views.py"
...
if form.is_valid():
    user = form.get_user()
    login(request, user)
    response = HttpResponseRedirect(reverse("main:show_main"))
    response.set_cookie('last_login', str(datetime.datetime.now()))
    return response
else:
    messages.error(request, "Invalid username or password. Please try again.")
...
```
**Penjelasan Kode:**

- `messages.error(request, msg)` akan "menempelkan" pesan _error_ kepada `request` yang mengirimkan permintaan _login_, yang nantinya akan ditampilkan di templat `login.html`.

## Tutorial: Membuat Fungsi untuk Menambahkan _Mood_ dengan AJAX

Pada bagian ini, kamu akan membuat fungsi pada _views_ untuk menambahkan mood baru ke basis data dengan AJAX.

1. Tambahkan kedua impor berikut pada file `views.py`.
    ```python title="main/views.py"
    from django.views.decorators.csrf import csrf_exempt
    from django.views.decorators.http import require_POST
    ```

2. Buatlah fungsi baru pada `views.py` dengan nama `add_mood_entry_ajax` yang menerima parameter `request` seperti berikut.

    ```python title="main/views.py"
    ...
    @csrf_exempt
    @require_POST
    def add_mood_entry_ajax(request):
        mood = request.POST.get("mood")
        feelings = request.POST.get("feelings")
        mood_intensity = request.POST.get("mood_intensity")
        user = request.user

        new_mood = MoodEntry(
            mood=mood, feelings=feelings,
            mood_intensity=mood_intensity,
            user=user
        )
        new_mood.save()

        return HttpResponse(b"CREATED", status=201)
        ...
    ```
    
    **Penjelasan Kode**:
    - _Decorator_ `csrf_exempt` membuat Django tidak perlu mengecek keberadaan `csrf_token` pada `POST` _request_ yang dikirimkan ke fungsi ini.
    - _Decorator_ `require_POST` membuat fungsi tersebut hanya bisa diakses ketika pengguna mengirimkan `POST` _request_ ke fungsi tersebut. Jika pengguna mengirimkan _request_ dengan _method_ lain, maka dari Django akan dikembalikan eror `405 Method Not Allowed`.
    - `mood = request.POST.get("mood")` dan semacamnya digunakan untuk mengambil data yang dikirimkan pengguna melalui `POST` _request_ secara manual.
    - `new_mood = MoodEntry(...)` merupakan objek `Mood` baru yang dibuat secara manual berdasarkan data-data yang dikirimkan dari `POST` _request_.

## Tutorial: Menambahkan _Routing_ Untuk Fungsi `add_mood_entry_ajax`

1. Buka `urls.py` yang ada pada subdirektori `main` dan impor fungsi yang sudah kamu buat tadi.
    ```python title="main/urls.py"
    from main.views import ..., add_mood_entry_ajax
    ```

2. Tambahkan _path url_ ke dalam `urlpatterns` untuk mengakses fungsi yang sudah diimpor tadi.
    ```python title="main/urls.py"
    urlpatterns = [
        ...
        path('create-mood-entry-ajax', add_mood_entry_ajax, name='add_mood_entry_ajax'),
    ]
    ```

## Tutorial: Menampilkan Data _Mood Entry_ dengan `fetch()` API

1. Bukalah berkas `views.py` dan **hapus dua baris** berikut.
    ```python title="main/views.py"
    mood_entries = MoodEntry.objects.filter(user=request.user)
    ```
    dan
    ```python title="main/views.py"
    'mood_entries': mood_entries,
    ```
    Pada tutorial ini, kita akan mendapatkan objek-objek _mood entry_ dari *endpoint* `/json`, sehingga kode di atas tidak diperlukan lagi.

2. Bukalah berkas `views.py` dan ubahlah baris pertama _views_ untuk `show_json` dan `show_xml` seperti berikut.

    ```python title="main/views.py"
    data = MoodEntry.objects.filter(user=request.user)
    ```

2. Bukalah berkas `main.html`. Hapus bagian _block conditional_ `mood_entries` untuk menampilkan card_mood ketika kosong atau tidak. Untuk memperjelas, inilah _block_ kode yang perlu kamu hapus.

    ```html title="main/templates/main.html"
    ...
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
    ...
    ```

    Setelah menghapus _block conditional_ tersebut, tambahkan potongan kode ini di tempat yang sama.
    ```html title="main/templates/main.html"
    ...
    <div id="mood_entry_cards"></div>
    ...
    ```

3. Buatlah _block_ `<script>` di bagian bawah berkas kamu (sebelum `{% endblock content %}`) dan buatlah fungsi baru pada _block_ `<script>` tersebut dengan nama `getMoodEntries`.

    ```html title="main/templates/main.html"
    <script>
      async function getMoodEntries(){
          return fetch("{% url 'main:show_json' %}").then((res) => res.json())
      }
    </script>
    ```
    **Penjelasan Kode:**
    
	- Fungsi ini menggunakan `fetch()` API ke data JSON secara *asynchronous*.
    - Setelah data di-*fetch*, fungsi `then()` digunakan untuk melakukan *parse* pada data JSON menjadi objek JavaScript.

4. Buatlah **fungsi baru** pada *block* `<script>` dengan nama `refreshMoodEntries` yang digunakan untuk me-*refresh* data *moods* secara asinkronus.

    ```html title="main/templates/main.html"
    <script>
        ...
     async function refreshMoodEntries() {
        document.getElementById("mood_entry_cards").innerHTML = "";
        document.getElementById("mood_entry_cards").className = "";
        const moodEntries = await getMoodEntries();
        let htmlString = "";
        let classNameString = "";

        if (moodEntries.length === 0) {
            classNameString = "flex flex-col items-center justify-center min-h-[24rem] p-6";
            htmlString = `
                <div class="flex flex-col items-center justify-center min-h-[24rem] p-6">
                    <img src="{% static 'image/sedih-banget.png' %}" alt="Sad face" class="w-32 h-32 mb-4"/>
                    <p class="text-center text-gray-600 mt-4">Belum ada data mood pada mental health tracker.</p>
                </div>
            `;
        }
        else {
            classNameString = "columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6 w-full"
            moodEntries.forEach((item) => {
                htmlString += `
                <div class="relative break-inside-avoid">
                    <div class="absolute top-2 z-10 left-1/2 -translate-x-1/2 flex items-center -space-x-2">
                        <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
                        <div class="w-[3rem] h-8 bg-gray-200 rounded-md opacity-80 -rotate-90"></div>
                    </div>
                    <div class="relative top-5 bg-indigo-100 shadow-md rounded-lg mb-6 break-inside-avoid flex flex-col border-2 border-indigo-300 transform rotate-1 hover:rotate-0 transition-transform duration-300">
                        <div class="bg-indigo-200 text-gray-800 p-4 rounded-t-lg border-b-2 border-indigo-300">
                            <h3 class="font-bold text-xl mb-2">${item.fields.mood}</h3>
                            <p class="text-gray-600">${item.fields.time}</p>
                        </div>
                        <div class="p-4">
                            <p class="font-semibold text-lg mb-2">My Feeling</p>
                            <p class="text-gray-700 mb-2">
                                <span class="bg-[linear-gradient(to_bottom,transparent_0%,transparent_calc(100%_-_1px),#CDC1FF_calc(100%_-_1px))] bg-[length:100%_1.5rem] pb-1">${item.fields.feelings}</span>
                            </p>
                            <div class="mt-4">
                                <p class="text-gray-700 font-semibold mb-2">Intensity</p>
                                <div class="relative pt-1">
                                    <div class="flex mb-2 items-center justify-between">
                                        <div>
                                            <span class="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full text-indigo-600 bg-indigo-200">
                                                ${item.fields.mood_intensity > 10 ? '10+' : item.fields.mood_intensity}
                                            </span>
                                        </div>
                                    </div>
                                    <div class="overflow-hidden h-2 mb-4 text-xs flex rounded bg-indigo-200">
                                        <div style="width: ${item.fields.mood_intensity > 10 ? 100 : item.fields.mood_intensity * 10}%;" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-indigo-500"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="absolute top-0 -right-4 flex space-x-1">
                        <a href="/edit-mood/${item.pk}" class="bg-yellow-500 hover:bg-yellow-600 text-white rounded-full p-2 transition duration-300 shadow-md">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
                                <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z" />
                            </svg>
                        </a>
                        <a href="/delete/${item.pk}" class="bg-red-500 hover:bg-red-600 text-white rounded-full p-2 transition duration-300 shadow-md">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-9 w-9" viewBox="0 0 20 20" fill="currentColor">
                                <path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" />
                            </svg>
                        </a>
                    </div>
                </div>
                `;
            });
        }
        document.getElementById("mood_entry_cards").className = classNameString;
        document.getElementById("mood_entry_cards").innerHTML = htmlString;
    }
    refreshMoodEntries();
    </script>
    ```

     **Penjelasan Kode:**

    - `document.getElementById("mood_entry_cards")` digunakan untuk mendapatkan elemen berdasarkan ID nya. Pada baris kode ini, elemen yang dituju adalah tag `<div>` dengan ID `mood_entry_cards` yang sudah kamu buat pada tahapan sebelumnya.
    - `innerHTML` digunakan untuk mengisi *child element* dari elemen yang dituju. Jika `innerHTML = ""`, maka akan mengosongkan isi *child element* dari elemen yang dituju.
    - `className` digunakan untuk mengisi *class name* dari elemen yang dituju.
    - `moodEntries.forEach((item))` digunakan untuk melakukan *for each loop* pada data *moods* yang diambil menggunakan fungsi `getMoodEntries()`. Kemudian, `htmlString` kita konkatenasi dengan data moods untuk mengisi container dengan *cards* seperti pada tutorial sebelumnya.
    - `refreshMoodEntries()` digunakan untuk memanggil fungsi tersebut pada setiap kali membuka halaman web.

## Tutorial: Membuat Modal Sebagai Form untuk Menambahkan _Mood_

1. Tambahkan kode berikut untuk mengimplementasikan modal (_Tailwind_) pada aplikasi kamu. Kamu dapat meletakkan potongan kode berikut dibawah `div` dengan `id` `mood_entry_cards` yang telah kamu tambahkan sebelumnya.
   
    ```html title="main/templates/main.html"
    ...
    <div id="crudModal" tabindex="-1" aria-hidden="true" class="hidden fixed inset-0 z-50 w-full flex items-center justify-center bg-gray-800 bg-opacity-50 overflow-x-hidden overflow-y-auto transition-opacity duration-300 ease-out">
      <div id="crudModalContent" class="relative bg-white rounded-lg shadow-lg w-5/6 sm:w-3/4 md:w-1/2 lg:w-1/3 mx-4 sm:mx-0 transform scale-95 opacity-0 transition-transform transition-opacity duration-300 ease-out">
        <!-- Modal header -->
        <div class="flex items-center justify-between p-4 border-b rounded-t">
          <h3 class="text-xl font-semibold text-gray-900">
            Add New Mood Entry
          </h3>
          <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center" id="closeModalBtn">
            <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path>
            </svg>
            <span class="sr-only">Close modal</span>
          </button>
        </div>
        <!-- Modal body -->
        <div class="px-6 py-4 space-y-6 form-style">
          <form id="moodEntryForm">
            <div class="mb-4">
              <label for="mood" class="block text-sm font-medium text-gray-700">Mood</label>
              <input type="text" id="mood" name="mood" class="mt-1 block w-full border border-gray-300 rounded-md p-2 hover:border-indigo-700" placeholder="Enter your mood" required>
            </div>
            <div class="mb-4">
              <label for="feelings" class="block text-sm font-medium text-gray-700">Feelings</label>
              <textarea id="feelings" name="feelings" rows="3" class="mt-1 block w-full h-52 resize-none border border-gray-300 rounded-md p-2 hover:border-indigo-700" placeholder="Describe your feelings" required></textarea>
            </div>
            <div class="mb-4">
              <label for="moodIntensity" class="block text-sm font-medium text-gray-700">Mood Intensity (1-10)</label>
              <input type="number" id="moodIntensity" name="mood_intensity" min="1" max="10" class="mt-1 block w-full border border-gray-300 rounded-md p-2 hover:border-indigo-700" required>
            </div>
          </form>
        </div>
        <!-- Modal footer -->
        <div class="flex flex-col space-y-2 md:flex-row md:space-y-0 md:space-x-2 p-6 border-t border-gray-200 rounded-b justify-center md:justify-end">
          <button type="button" class="bg-gray-500 hover:bg-gray-600 text-white font-bold py-2 px-4 rounded-lg" id="cancelButton">Cancel</button>
          <button type="submit" id="submitMoodEntry" form="moodEntryForm" class="bg-indigo-700 hover:bg-indigo-600 text-white font-bold py-2 px-4 rounded-lg">Save</button>
        </div>
      </div>
    </div>
    ...
    ```

    
2. Karena kita menggunakan _vanilla Tailwind CSS_, tidak ada _class_ modal yang _built-in_. Oleh karena itu, agar modal dapat berfungsi, kita perlu menambahkan fungsi-fungsi JavaScript berikut.
    ```html title="main/templates/main.html"
    <script>
    ...
      const modal = document.getElementById('crudModal');
      const modalContent = document.getElementById('crudModalContent');

      function showModal() {
          const modal = document.getElementById('crudModal');
          const modalContent = document.getElementById('crudModalContent');

          modal.classList.remove('hidden'); 
          setTimeout(() => {
            modalContent.classList.remove('opacity-0', 'scale-95');
            modalContent.classList.add('opacity-100', 'scale-100');
          }, 50); 
      }

      function hideModal() {
          const modal = document.getElementById('crudModal');
          const modalContent = document.getElementById('crudModalContent');

          modalContent.classList.remove('opacity-100', 'scale-100');
          modalContent.classList.add('opacity-0', 'scale-95');

          setTimeout(() => {
            modal.classList.add('hidden');
          }, 150); 
      }

      document.getElementById("cancelButton").addEventListener("click", hideModal);
      document.getElementById("closeModalBtn").addEventListener("click", hideModal);
    ...
    </script>
    ```
    :::info  
    Form dan fungsi JavaScript pada modal tersebut sudah disesuaikan untuk model pada aplikasi `mental_health_tracker`. Apabila kamu ingin menggunakan model lain yang juga memiliki field lain, perhatikan kembali nilai-nilai dari atribut HTML terkait.
    :::  

3. Ubahlah bagian tombol _Add New Mood Entry_ yang sudah kamu tambahkan di tutorial sebelumnya seperti berikut. Kemudian, tambahkan tombol baru untuk melakukan penambahan data dengan AJAX.

    ```html title="main/templates/main.html"
    ...
        <a href="{% url 'main:create_mood_entry' %}" class="bg-indigo-400 hover:bg-indigo-400 text-white font-bold py-2 px-4 rounded-lg transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105 mx-4 ">
            Add New Mood Entry
        </a>
        <button data-modal-target="crudModal" data-modal-toggle="crudModal" class="btn bg-indigo-700 hover:bg-indigo-600 text-white font-bold py-2 px-4 rounded-lg transition duration-300 ease-in-out transform hover:-translate-y-1 hover:scale-105" onclick="showModal();">
          Add New Mood Entry by AJAX
        </button>
    ...
    ```

## Tutorial: Menambahkan Data _Mood_ dengan AJAX

Modal dengan form yang telah kamu buat sebelumnya belum bisa digunakan untuk menambahkan data _mood_. Oleh karena itu, kamu perlu membuat fungsi JavaScript baru untuk menambahkan data berdasarkan _input_ ke basis data secara AJAX.

1. Buatlah fungsi baru pada block `<script>` dengan nama `addMoodEntry`.
    ```html title="main/templates/main.html"
    <script>
      function addMoodEntry() {
        fetch("{% url 'main:add_mood_entry_ajax' %}", {
          method: "POST",
          body: new FormData(document.querySelector('#moodEntryForm')),
        })
        .then(response => refreshMoodEntries())

        document.getElementById("moodEntryForm").reset(); 
        document.querySelector("[data-modal-toggle='crudModal']").click();

        return false;
      }
    ...
    </script>
    ```
    **Penjelasan Kode:**
    - `new FormData(document.querySelector('#moodEntryForm'))` digunakan untuk membuat sebuah `FormData` baru yang datanya diambil dari _form_ pada modal. Objek `FormData` dapat digunakan untuk mengirimkan data _form_ tersebut ke server.
    - `document.getElementById("moodEntryForm").reset()` digunakan untuk mengosongkan isi *field* form modal setelah di-*submit*.

2. Tambahkan fungsi `onclick` pada *button* "Add Product" pada modal untuk menjalankan fungsi `addMoodEntry()` dengan menambahkan kode berikut.
    ```html title="main/templates/main.html"
    <script>
    ...
    document.getElementById("submitMoodEntry").onclick = addMoodEntry
    </script>
    ```
    **Penjelasan Kode:**
    - `document.getElementById("submitMoodEntry").onclick = addMoodEntry`: Apabila tombol _save_ pada modal (`<button type="submit" id="submitMoodEntry" form="moodEntryForm" class="bg-indigo-700 hover:bg-indigo-600 text-white font-bold py-2 px-4 rounded-lg">Save</button>`) di-_click_, maka aplikasi ada akan memanggil fungsi `addMoodEntry()`. 

Selamat! Kamu telah berhasil membuat aplikasi yang dapat menambahkan data dengan menggunakan AJAX. Bukalah [http://localhost:8000/](http://localhost:8000/) dan cobalah untuk menambahkan data _mood entry_ baru pada aplikasi. Seharusnya, sekarang aplikasi tidak perlu melakukan *reload* setiap kali data _mood entry_ baru ditambahkan.

## Tutorial: Melindungi Aplikasi dari _Cross Site Scripting (XSS)_

### Mencoba XSS

Tahukah kamu bahwa kode yang baru saja kamu tambahkan ternyata membuka celah keamanan pada aplikasimu? Untuk melihat _severity_ dari celah keamanan ini, cobalah ikuti langkah-langkah berikut.

1. Tambahkan data _mood_ baru dengan nilai _field_ `mood` sebagai berikut. _Field_ lain dapat diisi sesuai dengan keinginan kalian.
    ```html
    <img src=x onerror="alert('XSS!');">
    ```

2. Tekan tombol simpan dan jika penyimpanan berhasil dilakukan, kamu akan mendapatkan _alert_ dengan nilai `XSS!` seperti di gambar berikut.
    
    ![Alert Box XSS](/img/5-alert-box-xss.png)

### Menambahkan `strip_tags` untuk "Membersihkan" Data Baru

Dari _input_ di atas, dapat dilihat bahwa orang yang berniat jahat dapat menambahkan data baru yang dapat mengeksekusi JavaScript di _browser_ pengguna aplikasi. Celah keamanan ini biasa disebut sebagai _Cross Site Scripting_ atau XSS. Lebih spesifiknya, dalam aplikasi ini terdapat _Stored XSS_, yang berarti _payload_ untuk XSS nya tersimpan dalam basis data aplikasi. Tentu saja kita tidak mau aplikasi yang kita buat untuk memiliki celah keamanan tersebut. Untuk menutup celah keamanan ini, kamu dapat mengikuti langkah-langkah berikut.

1. Bukalah berkas `views.py` dan `forms.py` dan tambahkan impor berikut.
    ```python title="main/views.py, main/forms.py"
    from django.utils.html import strip_tags
    ```

2. Pada fungsi `add_mood_entry_ajax` di `views.py`, gunakanlah fungsi `strip_tags` pada data `mood` dan `feelings` sebelum data tersebut dimasukkan ke dalam `MoodEntry`.
    ```python title="main/views.py"
    ...
    @csrf_exempt
    @require_POST
    def add_mood_entry_ajax(request):
        # highlight-start
        mood = strip_tags(request.POST.get("mood")) # strip HTML tags!
        feelings = strip_tags(request.POST.get("feelings")) # strip HTML tags!
        # highlight-end
        ...
    ```
    
    **Penjelasan Kode**:
    - Fungsi `strip_tags` akan menghilangkan semua _tag_ HTML yang terdapat pada data yang dikirimkan pengguna melalui `POST` _request_, sehingga data yang disimpan dalam basis data adalah data yang sudah "bersih". Misal `data = "<b>Pemrograman</b> <button>Berbasis</button> Platform <span>Ganjil 2025</span>"`, `strip_tags(data)` akan mengembalikan `Pemrograman Berbasis Platform Ganjil 2025`.
    - Data `mood_intensity` tidak dibersihkan dengan `strip_tags` karena _field_ tersebut berupa `IntegerField` dan jika isinya bukan `int`, Django tidak akan menyimpannya ke basis data.

3. Pada _class_ `MoodEntryForm` di `forms.py` tambahkan kedua _method_ berikut.
    ```python title="main/forms.py"
    ...
    class MoodEntryForm(ModelForm):
        class Meta:
            ...
        
        # highlight-start
        def clean_mood(self):
            mood = self.cleaned_data["mood"]
            return strip_tags(mood)
    
        def clean_feelings(self):
            feelings = self.cleaned_data["feelings"]
            return strip_tags(feelings)
        # highlight-end
    ...
    ```
    
    **Penjelasan Kode**:
    - _Method_ `clean_mood` dan `clean_feelings` akan dipanggil ketika melakukan `form.is_valid()`, sehingga dengan menambahkan kedua _method_ tersebut, kamu sudah melakukan validasi untuk fungsi `create_mood_entry` dan `edit_mood`.

4. Setelah menambahkan `strip_tags`, hapuslah data _mood_ yang tadi kamu tambahkan dan coba tambahkan kembali. Jika kamu dihadapkan dengan _error_ pada form yang mengatakan _field_ `mood` tidak boleh kosong, maka selamat, kamu sudah menambahkan pertahanan terhadap XSS! Jika kamu tidak dihadapkan dengan _error_ tersebut, periksa kembali apakah kamu sudah mengikuti langkah-langkah sebelumnya dengan sesuai.

    ![Form Error](/img/5-form-error.png)

### Membersihkan Data dengan DOMPurify

Fungsi `strip_tags` yang kamu tambahkan akan "membersihkan" semua data **baru**, tetapi data yang lama harus kita bersihkan sendiri atau kita me-_reset_ basis data. Atau, kita juga bisa menggunakan _library_ JavaScript [DOMPurify](https://github.com/cure53/DOMPurify) untuk melakukan pembersihan di _frontend_. Perlu diperhatikan bahwa DOMPurify hanya akan bekerja jika data diambil untuk ditampilkan dengan HTML di aplikasi kita. Jika ada yang menggunakan API `/json` atau `/xml` dari aplikasi kita, maka data yang didapatkan masih data yang "kotor".

1. Bukalah berkas `main.html` dan tambahkan potongan kode berikut pada _block_ `meta`.
    ```html title="main/templates/main.html"
    {% block meta %}
    ...
    <script src="https://cdn.jsdelivr.net/npm/dompurify@3.1.7/dist/purify.min.js"></script>
    ...
    {% endblock meta %}
    ```

2. Setelah itu, pada fungsi `refreshMoodEntries` yang telah kamu tambahkan sebelumnya, tambahkan potongan kode berikut.
    ```html title="main/templates/main.html"
    <script>
        ...
        async function refreshMoodEntries() {
            ...
            moods.forEach((item) => {
                // highlight-start
                const mood = DOMPurify.sanitize(item.fields.mood);
                const feelings = DOMPurify.sanitize(item.fields.feelings);
                // highlight-end
                ...
            });
            ...
        }
        ...
    </script>
    ```
    
    :::note
    Jangan lupa untuk mengubah semua kemunculan `item.fields.mood` menjadi `mood` dan `item.fields.feelings` menjadi `feelings`.
    :::

3. _Refresh_ halaman utama dan jika kamu sebelumnya memiliki data yang "kotor" seperti yang memunculkan _alert box_, _alert box_ tersebut seharusnya tidak muncul lagi pada _browser_ mu.

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
## Referensi Tambahan

- [HackTricks Cross Site Scripting](https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting)
- [OWASP Cross Site Scripting](https://owasp.org/www-community/attacks/xss/)

## Kontributor

- Juan Maxwell Tanaya
- Muhammad Faishal Adly Nelwan
- Muhammad Irfan Firmansyah

## Credits

Tutorial ini dikembangkan berdasarkan [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) dan [PBP Genap 2024](https://github.com/pbp-fasilkom-ui/genap-2024) yang ditulis oleh Tim Pengajar Pemrograman Berbasis Platform 2024. Segala tutorial serta instruksi yang dicantumkan pada repositori ini dirancang sedemikian rupa sehingga mahasiswa yang sedang mengambil mata kuliah Pemrograman Berbasis Platform dapat menyelesaikan tutorial saat sesi lab berlangsung.
