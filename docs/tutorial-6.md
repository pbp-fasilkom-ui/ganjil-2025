---
sidebar_label: Tutorial 6
sidebar_position: 8
Path: docs/tutorial-6
---

# Tutorial 6: Pengantar Flutter

Pemrograman Berbasis Platform (CSGE602022) — diselenggarakan oleh Fakultas Ilmu Komputer Universitas Indonesia, Semester Ganjil 2024/2025

---

## Tujuan Pembelajaran

Setelah menyelesaikan tutorial ini, mahasiswa diharapkan untuk dapat:

- Mengerti proses instalasi Flutter.
- Mengerti dan mampu menggunakan perintah-perintah dasar Flutter yang perlu diketahui untuk mengembangkan proyek aplikasi.
- Memahami alur dasar pembuatan dan eksekusi aplikasi Flutter.
- Memahami elemen-elemen dasar pada Flutter.

## Flutter

### Pengenalan Flutter

Flutter adalah sebuah *framework* aplikasi mobile *open source* yang dikembangkan oleh Google pada tahun 2017. *Framework* ini digunakan untuk membangun aplikasi pada sistem operasi Android dan iOS, serta mendukung pengembangan aplikasi berbasis web, Windows, Linux, dan MacOS secara native.

Salah satu **keuntungan utama** Flutter adalah kemampuannya untuk menghasilkan aplikasi di berbagai platform hanya dengan satu *codebase* (*cross-platform development*). Selain itu, fitur JIT (*just in time*) memungkinkan pengembang untuk melihat perubahan yang dilakukan pada *codebase* secara langsung tanpa perlu mengulang proses kompilasi dari awal.

Berikut adalah **keuntungan lainnya** yang dimiliki Flutter sebagai *framework* yang dapat *cross-platform*:

- **Performa yang cepat dan efektif**: Flutter menggunakan bahasa pemrograman Dart dan dikompilasi menjadi kode mesin. Perangkat host memahami kode ini sehingga memastikan performa yang cepat dan efektif.
- **Rendering yang cepat, konsisten, dan dapat disesuaikan**: Alih-alih mengandalkan alat rendering khusus platform, Flutter menggunakan Skia, _library_ grafis _open source_ milik Google untuk me-render UI. Keuntungan ini memberi pengguna visual yang konsisten, apa pun platform yang digunakan untuk mengakses aplikasi.
- **Alat yang ramah developer**: Google membuat Flutter dengan mengutamakan pada kemudahan penggunaan. Dengan alat seperti hot reload, developer dapat melihat seperti apa perubahan kode tanpa kehilangan status. Alat lain seperti pemeriksa widget memudahkan dalam memvisualisasikan dan memecahkan masalah tata letak UI.

Flutter memiliki dua komponen utama, yaitu Flutter SDK dan framework UI.

- **Flutter SDK (Software Development Kit)** – merupakan sekumpulan alat dan perangkat lunak yang digunakan untuk mengembangkan aplikasi menggunakan Flutter. SDK ini mencakup berbagai komponen seperti compiler, debugger, emulator, serta beragam library yang diperlukan untuk membangun aplikasi Flutter.
- **Framework UI** – adalah komponen yang digunakan untuk merancang antarmuka pengguna aplikasi. Framework ini menyediakan berbagai elemen seperti widget, tombol, navigasi, dan fitur lainnya yang memungkinkan pengembang untuk membuat tampilan aplikasi yang menarik dan konsisten di berbagai platform.

## _System Requirements_
Sebelum memulai instalasi dan pengembangan menggunakan Flutter, pastikan perangkat yang akan digunakan memenuhi spesifikasi minimum yang diperlukan. Berikut adalah kebutuhan perangkat keras dan perangkat lunak yang direkomendasikan untuk memastikan proses pengembangan berjalan dengan lancar.

#### _Hardware Requirements_ (macOS)

| Requirement         | Minimum      | Recommended   |
|---------------------|---------------|----------------|
| CPU Cores           | 4             | 8              |
| Memory in GB        | 8             | 16             |
| Display Resolution  | WXGA (1366 x 768) | FHD (1920 x 1080) |
| Free Disk Space     | 44.0 GB       | 70.0 GB        |

#### _Hardware Requirements_ (Windows)

| Requirement        | Minimum      | Recommended    |
|---------------------|---------------|----------------|
| CPU Cores           | 4             | 8              |
| Memory in GB        | 8             | 16             |
| Display Resolution  | WXGA (1366 x 768) | FHD (1920 x 1080) |
| Free Disk Space     | 11.0 GB       | 60.0 GB        |

#### _Software Requirements_ (Baik macOS dan Windows)

- **Operating System**:
  - macOS 11 (Big Sur) _or later_.
  - Windows 10 64-bit _or later_.



## Tutorial: Instalasi Flutter

Sebelum mengembangkan aplikasi dengan Flutter, berikut adalah langkah-langkah untuk melakukan instalasi.

#### Windows
> Untuk tutorial lengkapnya, kalian dapat mengakses tautan [berikut](https://docs.flutter.dev/get-started/install/windows/mobile).
1. _Download_ flutter SDK [di sini](https://docs.flutter.dev/get-started/install/windows/mobile#download-then-install-flutter) untuk Windows.
![image](https://hackmd.io/_uploads/ByeUnVWeye.png)
2. Setelah folder tersebut telah di-*download*, pindahkan zip folder tersebut ke folder permanen atau tujuan dan lakukan ekstrak zip folder yang telah diunduh. Disarankan untuk membuat folder di lokasi berikut:  
    - `%USERPROFILE%\dev\` Contoh: `C:\Users\{username}\dev\flutter`.
    - `%LOCALAPPDATA%` Contoh: `C:\Users\{username}\AppData\Local\flutter`.  
    :::warning
    Jangan instal Flutter di direktori atau _path_ yang memenuhi salah satu atau kedua kondisi berikut:
	    - Mengandung karakter khusus atau spasi (pastikan `{username}` tidak menggandung spasi atau karakter khusus kalau ada bisa ditempatkan pada `path` lain).
	    - Membutuhkan hak akses khusus (contoh: `C:\Program Files`).  

    :::

    ![image](https://hackmd.io/_uploads/S1texrWgke.png)
    :::info
    Pada tutorial ini kita menggunakan PATH `C:\Users\{username}\dev\flutter`
    :::
3. Tambahkan Flutter ke variabel PATH
    - Buka menu Start dan ketik "env" pada kolom pencarian. Kemudian pilih `Edit the system environment variables` dari hasil pencarian.
        ![image](https://hackmd.io/_uploads/HkI5lHZlyg.png)
    - Pada jendela `System Properties`, klik tombol `Environment Variables`.
        ![image](https://hackmd.io/_uploads/B1KaeHWekx.png)
    - Di bagian `User variables for {username}`, cari variabel `Path` dan klik dua kali untuk mengeditnya.
        ![image](https://hackmd.io/_uploads/r1HKZrZeye.png)
    - Di folder yang sudah diekstrak sebelumnya, cari folder dengan nama `bin`.
Salin _path_ lengkap dari folder tersebut.
        ![image](https://hackmd.io/_uploads/rkqfGSWx1g.png)
        ![image](https://hackmd.io/_uploads/HJlVMBZxyx.png)
    - Pada jendela `Edit Environment Variable` sebelumnya, klik **New** atau klik dua kali di baris kosong, lalu tambahkan _path_ yang telah disalin. 
        ![image](https://hackmd.io/_uploads/ByeHMSWeJe.png)
4. Setelah _path_ ditambahkan, klik `OK` untuk menyimpan perubahan, klik `OK`  juga pada jendela `System Properties`, kemudian tutup semua jendela dan buka kembali terminal atau PowerShell agar perubahan tersebut diterapkan. 
5. Untuk memastikan Flutter telah ditambahkan ke path dengan benar, buka terminal atau PowerShell dan jalankan _command_ `flutter --version`. Jika Flutter telah terinstal dengan benar, kamu akan melihat informasi versi Flutter yang ter-*install*. 
    ![image](https://hackmd.io/_uploads/rkd_YBblye.png)
6. Selamat! 🐼 Instalasi Flutter sudah berhasil dan lanjutkan dengan instalasi Android Studio.

#### MacOS
> Untuk tutorial lengkapnya, kalian dapat mengakses tautan [berikut](https://docs.flutter.dev/get-started/install/macos/mobile-android).

Khusus untuk pengguna macOS, kalian dapat melakukan instalasi flutter menggunakan _command_ berikut di terminal.
```bash
brew install --cask flutter 
```

Bagi yang belum meng-_install_ Homebrew di macOS, dapat menginstalnya dengan _command_ berikut.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Secara default, file `--cask` yang didownload melalui Homebrew akan tersimpan di
- `/opt/homebrew/Caskroom` untuk **Apple Silicon**
- `/usr/local/Caskroom` untuk **Mac Intel**

Untuk memastikan apakah flutter telah terinstall, kalian dapat menjalankan _command_ berikut di terminal.
```
brew info --cask flutter
```
Apabila Flutter sudah terinstall dengan benar, informasi seperti _screenshot_ di bawah ini akan muncul
![Screen Shot 2024-10-19 at 9.28.17 PM](https://hackmd.io/_uploads/HJZfMrZgJe.png)

Selamat! Instalasi Flutter sudah berhasil. Untuk mengecek versi dari Flutter, jalankan _command_ berikut dan lanjutkan dengan instalasi Android Studio.
```
flutter --version
```

#### Linux
Instalasi untuk perangkat linux dapat dilihat [di sini](https://docs.flutter.dev/get-started/install/linux/android).

## Tutorial: Instalasi Android Studio
1. Untuk memulai, unduh Android Studio dari situs resmi [berikut](https://developer.android.com/studio).
2. Setelah unduhan selesai, buka *installer* Android Studio dan jalankan untuk meng-*install* Android Studio.
3. Setelah itu, buka Android Studio dengan mengikuti langkah-langkah di bawah ini untuk menyelesaikan instalasi:
    - Klik `Next` pada halaman selamat datang untuk memulai proses instalasi. Kemudian pilih opsi `Standard` pada bagian _Install Type_ agar semua komponen yang diperlukan diinstal secara otomatis. 
        ![image](https://hackmd.io/_uploads/r1no18-xJx.png)
    - Klik tombol `Finish` untuk melanjutkan proses instalasi.
        ![image](https://hackmd.io/_uploads/rJfRyUWxkl.png)
    - Pada bagian ini, kalian akan melihat _License Agreement_ seperti gambar di bawah. Pilih `Accept` untuk menyetujui semua lisensi, lalu klik `Finish` untuk melanjutkan instalasi.
![image](https://hackmd.io/_uploads/ByTHeLZeJg.png)
    - Setelah instalasi Android Studio selesai, pastikan komponen SDK yang diperlukan sudah terinstal dengan benar. Pada halaman awal pilih `More Actions` lalu klik `SDK Manager`.
    ![image](https://hackmd.io/_uploads/SknSzIWeyg.png)
    - Atau, kalian bisa masuk ke menu **Settings > Languages & Frameworks > Android SDK** untuk mengecek dan memastikan bahwa komponen yang dibutuhkan seperti di bawah ini telah terinstal.  
      ![image](https://hackmd.io/_uploads/B1PDXUWg1x.png)
    - Pastikan komponen berikut sudah dipilih (dicentang):
      - **Android SDK Command-line Tools**
      - **Android SDK Build-Tools**
      - **Android SDK Platform-Tools**
      - **Android Emulator**
      - **NDK (Side by Side)**
      - **CMake**
      - **Android Emulator hypervisor driver (installer)**
    - Jika kolom **Status** menunjukkan _Update available_ atau _Not installed_ untuk komponen tertentu, pilih komponen tersebut lalu klik `Apply`.
    - Setelah proses penginstalan selesai, klik `OK` untuk menyimpan perubahan dan menutup jendela.
4. Setelah instalasi Flutter selesai, kita perlu memastikan bahwa semua komponen yang diperlukan telah diinstal dan dikonfigurasi dengan benar. Untuk itu, Flutter menyediakan perintah `flutter doctor` yang membantu memeriksa status instalasi.
    - Buka terminal atau PowerShell, lalu jalankan perintah `flutter doctor`. Hasilnya akan menunjukkan apakah semua komponen yang diperlukan sudah terpasang dengan benar. Contoh output:
        ```
        C:\Users\Ridho>flutter doctor
        Doctor summary (to see all details, run flutter doctor -v):
        [√] Flutter (Channel stable, 3.24.3, on Microsoft Windows [Version 10.0.22631.4317], locale en-ID)
        [√] Windows Version (Installed version of Windows is version 10 or higher)
        [!] Android toolchain - develop for Android devices (Android SDK version 32.1.0-rc1)
            ! Some Android licenses not accepted. To resolve this, run: flutter doctor --android-licenses
        [√] Chrome - develop for the web
        [X] Visual Studio - develop Windows apps
            X Visual Studio not installed; this is necessary to develop Windows apps.
              Download at https://visualstudio.microsoft.com/downloads/.
              Please install the "Desktop development with C++" workload, including all of its default components
        [√] Android Studio (version 2024.2)
        [√] VS Code, 64-bit edition (version 1.93.1)
        [√] Connected device (3 available)
        [√] Network resources

        ! Doctor found issues in 2 categories.
        ```
    - Jika `flutter doctor` menemukan masalah, seperti pada Android toolchain dengan pesan "Some Android licenses not accepted", kalian dapat memperbaikinya dengan menjalankan perintah `flutter doctor --android-licenses`.

        ```
        C:\Users\Ridho>flutter doctor --android-licenses
        5 of 7 SDK package licenses not accepted. 100% Computing updates...
        Review licenses that have not been accepted (y/N)? y
        ```
    - Ikuti instruksi yang muncul di layar dan ketik `y` untuk menerima lisensi yang belum diterima. Setelah itu, masalah terkait lisensi Android akan terselesaikan. Jalankan kembali perintah `flutter doctor`.
    
        ```
        C:\Users\Ridho>flutter doctor
        Doctor summary (to see all details, run flutter doctor -v):
        [√] Flutter (Channel stable, 3.24.3, on Microsoft Windows [Version 10.0.22631.4317], locale en-ID)
        [√] Windows Version (Installed version of Windows is version 10 or higher)
        [√] Android toolchain - develop for Android devices (Android SDK version 34.0.0)
        [√] Chrome - develop for the web
        [X] Visual Studio - develop Windows apps
            X Visual Studio not installed; this is necessary to develop Windows apps.
              Download at https://visualstudio.microsoft.com/downloads/.
              Please install the "Desktop development with C++" workload, including all of its default components
        [√] Android Studio (version 2024.2)
        [√] VS Code, 64-bit edition (version 1.93.1)
        [√] Connected device (3 available)
        [√] Network resources

        ! Doctor found issues in 1 category.
        ```
    - Kalian tidak perlu menginstal **Visual Studio** karena fokus pengembangan berada pada aplikasi mobile, sehingga **Visual Studio** tidak diperlukan. Namun, jika di masa depan ingin mengembangkan aplikasi Desktop Windows, kalian dapat menginstal **Visual Studio** dengan komponen "Desktop development with C++" melalui tautan [berikut](https://visualstudio.microsoft.com/downloads/).
5. Selamat! 🐼 Instalasi Flutter dan Android Studio telah berhasil! 🎉 Kalian siap untuk mulai mengembangkan aplikasi Flutter.

## Penggunaan IDE
Instal IDE pilihan kamu yang akan digunakan untuk mengembangkan aplikasi Flutter.  Kalian direkomendasikan untuk menggunakan Android Studio.
1. Android Studio
2. Visual Studio Code

Apabila kalian menggunakan VS Code dalam pengembangan menggunakan flutter, maka kalian perlu untuk meng-*install* dua *extension* berikut, yaitu **Dart** dan **Flutter**:
![Screen Shot 2024-10-19 at 9.40.25 PM](https://hackmd.io/_uploads/BJ88HHWlyx.png)
![Screen Shot 2024-10-19 at 9.41.28 PM](https://hackmd.io/_uploads/B1ldHSbx1l.png)


## Tutorial: *Getting Started with Flutter*

1. Buka Terminal atau Command Prompt. 
2. Buat dan masuk ke direktori di mana kamu akan menyimpan proyek Flutter-mu.
3. *Generate* proyek Flutter baru pada terminal dengan nama **mental_health_tracker**, kemudian masuk ke dalam direktori proyek tersebut.
    ```
    flutter create <APP_NAME>
    cd <APP_NAME>
    ```
4. Jalankan proyek kamu melalui Terminal atau Command Prompt.
    ```
    flutter run
    ```
    Terdapat beberapa opsi untuk menjalankan aplikasi Flutter, namun yang termudah adalah:
    - Menggunakan [emulator pada Android Studio](https://docs.flutter.dev/get-started/install/macos#set-up-the-android-emulator)
    - Menggunakan Google Chrome
        - Jalankan perintah di bawah untuk *enable web support* (hanya perlu dilakukan sekali):
            ```
            flutter config --enable-web
            ```
        - Kemudian, di direktori proyek, jalankan proyek tersebut di aplikasi Google Chrome dengan perintah:
            ```
            flutter run -d chrome
            ```
    - Menggunakan run debug (F5) pada VS Code.
5. Berikut tampilan yang akan muncul.
    - Menggunakan Emulator pada *Device* Android
    ![image](https://hackmd.io/_uploads/BJsB6IZgyg.png)
    
    - Menggunakan Google Chrome
    ![image](https://hackmd.io/_uploads/HyRtTIWgJg.png)

6. Lakukan `git init` pada root folder dan lakukan `add-commit-push` proyek ke sebuah repositori baru di GitHub. Kamu dapat menamai repositori barumu dengan nama `mental-health-tracker-mobile`.


## Tutorial: Merapikan Struktur Proyek

Sebelum melakukan pengembangan aplikasi Flutter lebih lanjut, kita akan merapikan struktur proyek file pada proyek kamu terlebih dahulu agar kode proyek dapat lebih mudah dipahami. Hal ini merupakan bentuk penerapan _best practice_ dalam pengembangan aplikasi, yakni [_clean architecture_](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html).

1. Buatlah file baru bernama `menu.dart` pada direktori `mental_health_tracker/lib`. Pada baris pertama file tersebut, tambahkan kode di bawah ini:

    ```dart
    import 'package:flutter/material.dart';
    ```

2. Dari file `main.dart`, pindahkan (_cut_) kode baris ke-39 hingga akhir yang berisi kedua class di bawah ini:  

    ```dart
    class MyHomePage ... {
        ...
    }
    
    class _MyHomePageState ... {
        ...
    }
    ```

    ke file `menu.dart` yang baru saja kamu buat.

3. Kamu akan melihat bahwa pada file `main.dart`, akan terdapat error pada baris ke-34, yang berisi kode berikut:

    ```dart
    home: const MyHomePage(title: 'Flutter Demo Home Page'),
    ```

    Hal ini terjadi karena file `main.dart` tidak lagi mengenali class MyHomePage karena sudah kamu pindahkan ke file lain, yaitu `menu.dart`. Untuk menyelesaikan masalah ini, tambahkan kode berikut ini pada awal file.

    ```dart
    import 'package:mental_health_tracker/menu.dart';
    ```

4. Jalankan proyek melalui Terminal atau Command Prompt untuk memastikan bahwa aplikasi tetap dapat berjalan dengan baik.

## Tutorial: Membuat Widget Sederhana pada Flutter
Dalam tutorial ini, kamu akan belajar membuat widget sederhana di Flutter. Kamu akan membuat halaman utama dengan _mental_health_tracker_  sebagai _header_, diikuti dengan informasi pengguna di bagian atas, serta membuat _card_ sebagai _button_ untuk fitur-fitur seperti "Lihat Mood", "Tambah Mood", dan "Logout". Saat _button_ yang ada ditekan, maka akan muncul pemberitahuan di bagian bawah layar.

### Langkah 1: Mengubah Tema Warna Aplikasi 

1. Buka file `main.dart`.

2. Ubah kode pada `main.dart` di bagian tema aplikasi kamu yang mempunyai tipe `MaterialApp` menjadi seperti di bawah ini.

   ```dart
    colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.deepPurple,
    ).copyWith(secondary: Colors.deepPurple[400]),
   ```

	:::note  
	Kamu juga bisa mengubah warna tema aplikasi sesuai yang kamu inginkan dengan mengacu kepada [dokumentasi Colors](https://api.flutter.dev/flutter/material/Colors-class.html).
	:::


### Langkah 2: Mengubah Sifat _Widget_ Halaman Menu Menjadi *Stateless*

1. Pada berkas `main.dart`, hapus `const MyHomePage(title: 'Flutter Demo Home Page')` sehingga cukup menjadi:

   ```dart
   MyHomePage(),
   ```

   Jangan lupa untuk menghapus kata kunci `const`-nya juga.

2. Pada berkas `menu.dart`, kamu akan mengubah sifat _widget_ halaman dari _stateful_ menjadi _stateless_ dengan:
    
    - Menghapus semua isi dari `class MyHomePage ...` seperti `const MyHomePage({super.key, required this.title});`, variabel `final String title;`, komentar-komentar pada berkas, dan `State<MyHomePage> createState() => _MyHomePageState();`
    - Mengubah `... extends StatefulWidget` menjadi `... extends StatelessWidget` pada `class MyHomePage`.
    - Menambahkan `MyHomePage({super.key});` sebagai constructor class `MyHomePage`.
    - Menghapus seluruh class `class _MyHomePageState extends State<MyHomePage>`
    - Menambahkan Widget build sehingga kode terlihat seperti di bawah.  

    <br/>Setelah melakukan langkah-langkah tersebut, seharusnya berkas `menu.dart` kamu akan terlihat seperti ini.
	```dart
	class MyHomePage extends StatelessWidget {
	    MyHomePage({super.key});

	    @override
	    Widget build(BuildContext context) {
		return Scaffold(
		    ... // jangan copy titik-titik ini!
		);
	    }
	}
	```

### Langkah 3: Membuat _Card_ Sederhana yang Berisi NPM, Nama, dan Kelas
Perlu diketahui sebelumnya bahwa setiap UI yang dibuat oleh Flutter disebut sebagai widget dan dibentuk pada bagian `Widget build()`.

1. Sebelum membuat _card_, kamu dapat mendeklarasikan tiga variabel bertipe _string_ yang berisi NPM, nama, dan kelas pada `class MyHomePage` di `menu.dart` seperti contoh di bawah.

    ```dart
    class MyHomePage extends StatelessWidget {
        final String npm = '5000000000'; // NPM
        final String name = 'Gedagedi Gedagedago'; // Nama
        final String className = 'PBP S'; // Kelas
        
        ...
    }

    ```
    :::note
    Jangan lupa untuk mengganti NPM, Nama, dan Kelas sesuai dengan data diri kalian yaa!!
    :::

2. Setelah mendeklarasikan ketiga variabel tersebut, kamu dapat membuat _class_ baru bernama `InfoCard` pada berkas `menu.dart` untuk membuat card sederhana yang akan menampilkan informasi NPM, nama, dan kelas kamu.
    ```dart
    ...
    class InfoCard extends StatelessWidget {
      // Kartu informasi yang menampilkan title dan content.

      final String title;  // Judul kartu.
      final String content;  // Isi kartu.

      const InfoCard({super.key, required this.title, required this.content});

      @override
      Widget build(BuildContext context) {
        return Card(
          // Membuat kotak kartu dengan bayangan dibawahnya.
          elevation: 2.0,
          child: Container(
            // Mengatur ukuran dan jarak di dalam kartu.
            width: MediaQuery.of(context).size.width / 3.5, // menyesuaikan dengan lebar device yang digunakan.
            padding: const EdgeInsets.all(16.0),
            // Menyusun title dan content secara vertikal.
            child: Column(
              children: [
                Text(
                  title,
                  style: const TextStyle(fontWeight: FontWeight.bold),
                ),
                const SizedBox(height: 8.0),
                Text(content),
              ],
            ),
          ),
        );
      }
    }

    ```


### Langkah 4: Membuat _Button Card_ Sederhana dengan Icon

1. Sebelum membuat _button_ untuk _card_, kamu dapat membuat _class_ baru bernama `ItemHomepage` yang berisi atribut-atribut dari card yang akan kamu buat (pada kasus ini berisi _name_ dan _icon_). Pada berkas `menu.dart`, letakkan kode di bawah ini di luar class `MyHomePage` dan `InfoCard` yang sudah ada.

   ```dart
    ...
    class ItemHomepage {
        final String name;
        final IconData icon;

        ItemHomepage(this.name, this.icon);
    }
    ...
   ```
2. Setelah itu, kamu dapat membuat _list of_ `ItemHomepage` yang berisi tombol-tombol yang ingin kamu tambahkan pada _class_ `MyHomePage`.

   ```dart
    class MyHomePage extends StatelessWidget {  
        ...
        final List<ItemHomepage> items = [
            ItemHomepage("Lihat Mood", Icons.mood),
            ItemHomepage("Tambah Mood", Icons.add),
            ItemHomepage("Logout", Icons.logout),
        ];
        ...
    }
   ```

3. Apabila kamu sudah menambahkan tombol-tombol yang kamu inginkan, kamu dapat membuat _class_ `ItemCard` untuk menampilkan tombol-tombolmu. Untuk saat ini, tombol yang ditekan hanya akan menampilkan _snackbar_ yang berisi pesan "Kamu telah menekan tombol [**nama _button_**]".
    ```dart
    ...
    class ItemCard extends StatelessWidget {
      // Menampilkan kartu dengan ikon dan nama.

      final ItemHomepage item; 
      
      const ItemCard(this.item, {super.key}); 

      @override
      Widget build(BuildContext context) {
        return Material(
          // Menentukan warna latar belakang dari tema aplikasi.
          color: Theme.of(context).colorScheme.secondary,
          // Membuat sudut kartu melengkung.
          borderRadius: BorderRadius.circular(12),
          
          child: InkWell(
            // Aksi ketika kartu ditekan.
            onTap: () {
              // Menampilkan pesan SnackBar saat kartu ditekan.
              ScaffoldMessenger.of(context)
                ..hideCurrentSnackBar()
                ..showSnackBar(
                  SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
                );
            },
            // Container untuk menyimpan Icon dan Text
            child: Container(
              padding: const EdgeInsets.all(8),
              child: Center(
                child: Column(
                  // Menyusun ikon dan teks di tengah kartu.
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Icon(
                      item.icon,
                      color: Colors.white,
                      size: 30.0,
                    ),
                    const Padding(padding: EdgeInsets.all(3)),
                    Text(
                      item.name,
                      textAlign: TextAlign.center,
                      style: const TextStyle(color: Colors.white),
                    ),
                  ],
                ),
              ),
            ),
          ),
        );
      }
      
    }
    ...
    ```

### Langkah 5: Mengintegrasikan InfoCard dan ItemCard untuk Ditampilkan di MyHomePage
Ingat kembali bahwa seluruh elemen UI (Widget) yang ada di Flutter akan didefinisikan dan disusun pada bagian `Widget build()`. Untuk mengintegrasikan dan menampilkan seluruh _card_ yang kamu miliki di `HomePage`-mu, kamu dapat mengubah bagian `Widget build()` pada _class_ `MyHomePage`.

```dart
...
class MyHomePage extends StatelessWidget {
  ...  

  @override
  Widget build(BuildContext context) {
    // Scaffold menyediakan struktur dasar halaman dengan AppBar dan body.
    return Scaffold(
      // AppBar adalah bagian atas halaman yang menampilkan judul.
      appBar: AppBar(
        // Judul aplikasi "Mental Health Tracker" dengan teks putih dan tebal.
        title: const Text(
          'Mental Health Tracker',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        // Warna latar belakang AppBar diambil dari skema warna tema aplikasi.
        backgroundColor: Theme.of(context).colorScheme.primary,
      ),
      // Body halaman dengan padding di sekelilingnya.
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        // Menyusun widget secara vertikal dalam sebuah kolom.
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            // Row untuk menampilkan 3 InfoCard secara horizontal.
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                InfoCard(title: 'NPM', content: npm),
                InfoCard(title: 'Name', content: name),
                InfoCard(title: 'Class', content: className),
              ],
            ),

            // Memberikan jarak vertikal 16 unit.
            const SizedBox(height: 16.0),

            // Menempatkan widget berikutnya di tengah halaman.
            Center(
              child: Column(
                // Menyusun teks dan grid item secara vertikal.

                children: [
                  // Menampilkan teks sambutan dengan gaya tebal dan ukuran 18.
                  const Padding(
                    padding: EdgeInsets.only(top: 16.0),
                    child: Text(
                      'Welcome to Mental Health Tracker',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                        fontSize: 18.0,
                      ),
                    ),
                  ),

                  // Grid untuk menampilkan ItemCard dalam bentuk grid 3 kolom.
                  GridView.count(
                    primary: true,
                    padding: const EdgeInsets.all(20),
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    crossAxisCount: 3,
                    // Agar grid menyesuaikan tinggi kontennya.
                    shrinkWrap: true,

                    // Menampilkan ItemCard untuk setiap item dalam list items.
                    children: items.map((ItemHomepage item) {
                      return ItemCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
...
```

:::tip

Sebagai bentuk _best practice_, jalankan perintah `flutter analyze` pada _root folder_ proyek setelah kode kamu selesai ditulis. 

Hal ini sebaiknya dilakukan untuk memastikan tidak ada isu-isu pada kode kamu yang dapat mengganggu performa atau fungsionalitas aplikasi. Jika kamu mengikuti tutorial dengan baik, seharusnya hasil perintah menunjukkan bahwa tidak ada isu terdeteksi pada proyek kamu.

```bash
mental_health_tracker % flutter analyze
Analyzing mental_health_tracker...                                      
No issues found! (ran in 1.6s)
```

Apabila ternyata terdapat isu pada kode kamu (contohnya pada bagian di bawah ini), cobalah untuk menyelesaikan isu tersebut dengan mengikuti tutorial secara lebih teliti atau memperhatikan baris kode di mana isu tersebut terjadi.

```bash
mental_health_tracker % flutter analyze
Analyzing mental_health_tracker...                                      

  error • The constructor being called isn't a const constructor • lib/main.dart:37:13 • const_with_non_const

1 issue found. (ran in 1.5s)
```

Langkah ini juga dapat membantu proses building yang akan dilakukan pada beberapa tutorial yang akan datang.

:::

## Penutup

Selamat! Kamu berhasil menyelesaikan Tutorial 6! 🐼🎉

Kamu dapat mencoba menjalankan aplikasi Flutter kamu menggunakan perintah `flutter run`, seperti yang sudah diajarkan pada tutorial ini.

Sekarang, kamu sudah lebih menguasai dasar-dasar Flutter, mulai dari instalasi hingga memahami struktur dasar aplikasi. 

1. Pelajari dan pahami kembali kode yang sudah kamu tuliskan di atas dengan baik.
2. Setelah semua langkah pada tutorial ini, aplikasi Flutter dasar kamu seharusnya sudah dapat menampilkan tampilan awal seperti berikut.
    ![image](https://hackmd.io/_uploads/Hy9dEd5gyx.png)
3. Pada akhir tutorial ini, struktur direktori lokalmu akan terlihat seperti ini.
    ```
    mental_health_tracker
    ├── .dart_tool
    ├── .idea 
    ├── android
    ├── ios
    ├── lib
    │   ├── main.dart
    │   └── menu.dart
    ├── linux
    ├── macos
    ├── test
    ├── web
    ├── windows
    ├── .gitignore
    ├── .metadata
    ├── analysis_options.yaml
    ├── mental_health_tracker.iml
    ├── pubspec.lock
    ├── pubspec.yaml
    └── README.md
    ```
5. Pastikan struktur direktori lokal sudah benar. Selanjutnya, lakukan `add`, `commit` dan `push` untuk memperbarui repositori GitHub.
6. Jalankan perintah berikut untuk melakukan `add`, `commit` dan `push`

   ```shell
   git add .
   git commit -m "<pesan_commit>"
   git push -u origin <branch_utama>
   ```

   - Ubah `<pesan_commit>` sesuai dengan keinginan. Contoh: `git commit -m "tutorial 6 selesai"`.
   - Ubah `<branch_utama>` sesuai dengan nama branch utamamu. Contoh: `git push -u origin main` atau `git push -u origin master`.

## Referensi Tambahan

- [Flutter Documentation](https://docs.flutter.dev/)
- [Write your first Flutter app, part 1](https://docs.flutter.dev/get-started/codelab)
- [An Introduction to Flutter: The Basics by FreeCodeCamp](https://www.freecodecamp.org/news/an-introduction-to-flutter-the-basics-9fe541fd39e2/)
- [Flutter Course for Beginners – 37-hour Cross Platform App Development Tutorial by FreeCodeCamp](https://www.youtube.com/watch?v=VPvVD8t02U8)
- [An Introduction to Flutter Clean Architecture](https://medium.com/ruangguru/an-introduction-to-flutter-clean-architecture-ae00154001b0)


## Kontributor

- Restu Ahmad Ar Ridho
- Naufal Ichsan
- Vinka Alrezky As
- Fiona Ratu Maheswari

## Credits

Tutorial ini dikembangkan berdasarkan [PBP Ganjil 2024](https://github.com/pbp-fasilkom-ui/ganjil-2024) dan [PBP Genap 2024](https://github.com/pbp-fasilkom-ui/genap-2024) yang ditulis oleh Tim Pengajar Pemrograman Berbasis Platform 2024. Segala tutorial serta instruksi yang dicantumkan pada repositori ini dirancang sedemikian rupa sehingga mahasiswa yang sedang mengambil mata kuliah Pemrograman Berbasis Platform dapat menyelesaikan tutorial saat sesi lab berlangsung.
