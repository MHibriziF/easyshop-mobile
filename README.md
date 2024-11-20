# EasyShop Mobile

Aplikasi ini dibuat dalam rangka memenuhi keperluan tugas mata kuliah Pemrograman Basis Platform Fasilkom UI
semester gasal 24/25.

Dibuat oleh Muhammad Hibrizi Farghana - 2306165585

<details>
<summary><h2><b>Tugas 7 (click to expand) </b></h2></summary>

### Apa yang dimaksud dengan _stateless widget_ dan _stateful widget_ ?

**Stateless Widget**
_Stateless widget_ adalah widget yang tidak memiliki _state_ atau kondisi internal yang tidak dapat berubah sepanjang tampilannya. Artinya, begitu _stateless widget_ dibuat, bentuknya akan tetap sama tanpa ada modifikasi, meskipun pengguna berinteraksi dengan aplikasi atau ada perubahan data.

**Stateful Widget**
_Stateful widget_ adalah widget yang memiliki _state_ dan dapat berubah sepanjang tampilannya. _Stateful widget_ memiliki kemampuan untuk merespons interaksi pengguna atau perubahan data dengan memperbarui tampilannya sesuai dengan kondisi terkini.

#### Perbedaan _stateless widget_ dan _stateful widget_

Perbedaan utama antara _stateless_ dan _stateful_ widget adalah pada kemampuannya untuk menyimpan dan memperbarui _state_. Stateless widget bersifat statis dan tidak dapat berubah setelah dirender, sehingga cocok untuk tampilan yang tidak memerlukan perubahan dinamis. Sebaliknya, _stateful_ widget mampu menyimpan dan memperbarui _state_, sehingga memungkinkan UI untuk berubah sesuai kondisi terbaru atau aksi pengguna.

### Widget yang digunakan pada proyek ini dan fungsinya.

1. Material: Menyediakan tema dan struktur dasar aplikasi.
2. Scaffold: Menyediakan struktur halaman dasar dengan bagian utama AppBar dan body.
3. AppBar: Menampilkan bagian atas halaman dengan judul aplikasi.
4. Padding: Menambahkan jarak sekitar child widget.
5. Column: Menyusun widget secara vertikal.
6. Row: Menyusun widget secara horizontal.
7. SizedBox: Memberikan tinggi dan lebar yang tetap kepada childnya.
8. Card: Kontainer untuk membuat tampilan seperti kartu.
9. Container: Kontainer dengan opsi untuk margin, padding, dan warna latar.
10. GridView.count: Menampilkan child widget dalam grid dengan jumlah kolom tetap.
11. Text: Menampilkan teks dalam aplikasi.
12. InkWell: Membuat objek dapat diklik dan disertai dengan animasi
13. ScaffoldMessenger: Menampilkan SnackBar untuk notifikasi sementara.
14. SnackBar: Menampilkan pesan sementara di bagian bawah layar.
15. Icon: Menampilkan ikon grafis.

### Apa fungsi dari `setState()`? Variabel apa saja yang dapat terdampak dengan fungsi tersebut?

`setState()` adalah fungsi yang digunakan oleh StatefulWidget untuk memberi tahu framework bahwa ada perubahan pada _state_ komponen yang membutuhkan rebuild tampilan.

Variabel yang dapat terdampak oleh `setState()` adalah variabel yang disimpan dalam state komponen, seperti nilai dari kontrol input, posisi dalam daftar, atau kondisi logika tampilan. Hal ini memungkinkan pembaruan tampilan secara otomatis ketika data diubah tanpa manipulasi langsung pada kode program.

### Perbedaan antara `const` dengan `final`

- Nilai dari sebuah `const` harus dapat diketahui di waktu _compile_ dan langsung diberikan saat variabel dideklarasi, sedangkan `final` memperbolehkan nilai yang dikalkulasi saat _runtime_ dan tidak dapat dimodifikasi selanjutnya.

- `const` digunakan untuk nilai _immutable_ dan telah diketahui dari awal, sedangkan `final` digunakan apabila nilai belum dapat diketahui waktu _compile_, tetapi tidak boleh diubah setelah diberikan nilai.

### Implementasi _checklist_

#### Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.

1. Pada direktori yang saya tentukan, saya menjalankan perintah `flutter create easyshop` untuk membuat flutter app baru dengan nama easyshop

2. Akan terdapat direktori baru bernama `easyshop`. Pindah direktori ke direktori flutter app baru tersebut.

3. Membuat file baru bernama `menu.dart` pada direktori `../easyshop/lib`

4. Pada file `menu.dart`, mengimpor package `package:flutter/material.dart`. Kemudian, menambahkan class `MyHomePage` sebagai homepage, `InfoCard` sebagai kartu yang menampilkan informasi user, `ItemCard` sebagai kartu dengan fungsionalitas button, dan `ItemHomePage`sebagai attribut yang ditampilkan oleh tiap `ItemCard`

#### Membuat tiga tombol sederhana dengan ikon dan teks untuk: melihat daftar produk, menambah produk, dan logout

1. Pada file `menu.dart`, menambahkan attribut berikut pada class `MyHomePage`

```dart
final List<ItemHomepage> items = [
    ItemHomepage("Lihat Daftar Produk", Icons.view_day_outlined, Colors.blueAccent),
    ItemHomepage("Tambah Produk", Icons.add, Colors.greenAccent),
    ItemHomepage("Logout", Icons.logout, Colors.redAccent),
  ];
```

2. Class `ItemHomePage` akan berfungsi sebagai attribut-attribut yang dimiliki oleh tiap button. Adapun isi dari `ItemHomePage` adalah sebagai berikut.

```dart
class ItemHomepage {
  final String name;
  final IconData icon;
  final Color color;

  ItemHomepage(this.name, this.icon, this.color);
}
```

3. `ItemCard` diimplementasi dengan kode seperti `ItemCard` di tutorial dengan mengganti attribut color pada Widget class `ItemCard` menjadi `color: item.color`

#### Memunculkan Snackbar

Snackbar diiemplementasikan dengan menambahkan kode berikut pada attribut `onTap` di Widget class `ItemCard`

```dart
...
 onTap: () {
          // Menampilkan pesan SnackBar saat kartu ditekan.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
...
```

</details>

<details>
<summary><h2><b>Tugas 8 (click to expand) </b></h2></summary>

## Kegunaan const di Flutter

`const` digunakan untuk mendeklarasikan nilai atau widget yang bersifat konstan pada waktu kompilasi. Ketika `const` diterapkan pada widget, Flutter akan mengetahui bahwa widget tersebut tidak dapat berubah dan dibuat sekali saja sehingga meningkatkan efisiensi dan performa aplikasi.

### Keuntungan menggunakan const pada kode Flutter

1. Efisiensi Memori: Widget yang ditandai dengan `const` hanya dibuat sekali dan dapat digunakan kembali sehingga menghindari pembuatan ulang widget yang sama berulang kali.

2. Peningkatan Performa: Karena widget `const` tidak memerlukan proses _rebuild_ (penggambaran ulang) di setiap render, penggunaan `const` dapat mempercepat rendering UI.

3. Meningkatkan Readability: Menggunakan `const` membuat kode lebih mudah dimengerti

4. Eror saat compile: Eror pada `const` dapat dideteksi saat waktu compile sehingga memudahkan pengembang ketika melakukan proses debugging

### Kapan sebaiknya kita menggunakan const

1. Stateless Widget: Gunakan `const` pada widget stateless yang tidak berubah dan tidak menerima parameter yang akan mempengaruhi state mereka.

2. Widget dengan Parameter Konstan: Jika widget menerima parameter yang nilainya tetap (tidak berubah), gunakan `const` untuk mendeklarasikannya.

### Kapan sebaiknya tidak menggunakan const

1. Stateful Widget: Hindari menggunakan `const` pada widget yang memiliki state berubah-ubah karena setiap perubahan pada state memerlukan rebuild.

2. Widget dengan Data Dinamis: Jika widget menerima parameter yang berubah sepanjang waktu (seperti input pengguna atau data yang didapatkan dari API), sebaiknya tidak menggunakan const.

## Penggunaan Column dan Row pada Flutter

### Column

Widget ini menyusun child widget secara vertikal. Widget ini biasanya digunakan untuk layout vertikal, misalnya untuk menampilkan daftar item atau formulir.

Contoh:

```dart
Column(
  children: [
    Text(
      title,
      style: const TextStyle(fontWeight: FontWeight.bold),
    ),
    const SizedBox(height: 8.0),
    Text(content),
  ],
)
```

### Row

Widget ini menyusun child widget secara horizontal. Widget ini digunakan ketika kita ingin menyusun widget secara horizontal, misalnya tombol atau elemen-elemen yang disusun berdampingan.

Contoh:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    InfoCard(title: 'NPM', content: npm),
    InfoCard(title: 'Name', content: name),
    InfoCard(title: 'Class', content: className),
  ],
),
```

### Perbandingan

- Column mengatur child widget secara vertikal, sedangkan Row mengatur secara horizontal.

- Kedua widget ini dapat menerima properti seperti mainAxisAlignment dan crossAxisAlignment untuk mengatur penataan dan penyusunan child widget.

- Column lebih sering digunakan ketika kita ingin layout berbentuk daftar atau formulir vertikal, sementara Row lebih cocok untuk elemen yang memerlukan penataan horizontal.

## Elemen input yang digunakan pada halaman form.

Pada halaman `ProductEntryFormPage`, jenis input yang saya gunakan hanya satu, yaitu `TextFormField`.

### Elemen input Flutter lain yang tidak digunakan

Adapun elemen input yang tidak digunakan pada form adalah sebagai berikut:

1. Checkbox: Dapat digunakan untuk memilih banyak opsi di saat yang bersamaan

2. Radio: Berguna untuk memilih salah satu opsi dari beberapa pilihan

3. Switch: Dapat digunakan untuk memilih antara dua keadaan

4. DropdownButton: Dapat digunakan untuk memilih nilai dari daftar pilihan yang terbatas

5. DatePicker: Dapat digunakan untuk memilih tanggal

6. Slider: Dapat digunakan untuk memilih angka dalam rentang tertentu

7. Time Picker: Dapat digunakan untuk memilih waktu

## Cara mengatur tema (theme) dalam aplikasi Flutter

Untuk menjaga konsistensi tampilan dalam aplikasi Flutter, saya mengatur tema menggunakan `ThemeData`. `ThemeData` dapat dibuat di dalam widget `MaterialApp` pada file `main.dart`. Dengan cara ini, seluruh elemen UI di aplikasi akan mengikuti aturan desain yang konsisten sesuai dengan apa yang diatur dalam `ThemeData`.

Perhatikan kode berikut

```dart
MaterialApp(
  title: 'EasyShop',
  theme: ThemeData(
    colorScheme: ColorScheme.fromSwatch(
      primarySwatch: Colors.deepOrange,
    ).copyWith(secondary: Colors.deepPurple[100]),
    useMaterial3: true,
  ),
  home: MyHomePage(),
);
```

Kode tersebut merupakan kode yang saya buat pada file `main.dart`.

Pada attribut theme di `MaterialApp`, saya memberikan tema warna utama yaitu deepOrange dengan warna secondarynya deepPurple. Apabila widgets lain ingin mengikuti warna pada tema, cukup dengan menggunakan `Theme.of(context).colorScheme.primary` pada attribut Colors. Dengan demikian, aplikasi dengan tema warna deepOrange diiringin dengan deepPurple dapat diimplementasikan.

## Cara menangani navigasi pada Flutter

Untuk menangani navigasi dalam aplikasi Flutter, saya menggunakan `Navigator`. Dengan menggunakan `Navigator`, saya dapat melakukan navigasi dengan menggunakan methode `pushReplacement` dan 'push'.

Contoh:

1. Menggunakan `pushReplacement`

```dart
onTap: () {
  Navigator.pushReplacement(
      context,
      MaterialPageRoute(
        builder: (context) => MyHomePage(),
      ));
},
```

Dengan kode tersebut, apabila widget tersebut disentuh, maka halaman saat ini akan digantikan dengan halaman `MyHomePage`

2. Menggunakan `push`

```dart
 onTap: () {
    Navigator.push(context,
        MaterialPageRoute(builder: (context) => const ProductEntryFormPage()));
},
```

Dengan kode tersebut, apabila widget tersebut disentuh, maka halaman `ProductEntryFormPage` akan ditambahkan ke dalam tumpukan navigasi. Apabila pengguna menggunakan tombol back, maka pengguna akan kembali ke laman sebelum wdiget tersebut disentuh.

</details>

<details>
<summary><h2><b>Tugas 9 (click to expand) </b></h2></summary>

## Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?

Membuat model untuk pengambilan atau pengiriman data JSON penting untuk memastikan bahwa data yang diterima atau dikirim memiliki struktur yang konsisten dan mudah dikelola.
Selain itu, model membantu dalam menguraikan data JSON menjadi objek yang dapat digunakan oleh aplikasi, sehingga memudahkan pengaksesan dan manipulasi data.

Apabila kita tidak membuat model terlebih dahulu, aplikasi tetap dapat berfungsi dengan normal. Akan tetapi, tanpa adanya model, risiko terhadap kesalahan dan ketidakstabilan akan menjadi lebih tinggi. Selain itu, proses penguraian data JSON akan menjadi lebih rumit dan rawan error, misalnya akibat tipe data yang tidak sesuai atau data yang tidak lengkap. Hal ini dapat menyebabkan berbagai masalah seperti data yang salah ditampilkan, aplikasi crash, atau kesulitan dalam debugging dan pemeliharaan kode. Dengan menggunakan model, kita bisa mengurangi risiko-risiko ini dan memastikan bahwa data yang diolah selalu dalam format yang benar dan konsisten.

## Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini

Library `http` di Flutter digunakan untuk melakukan permintaan `HTTP`, seperti `GET`, `POST`, `PUT`, dan `DELETE`, ke server. Dengan library ini, kita dapat berkomunikasi dengan server atau API untuk mengirim dan menerima data. Library ini menyediakan cara yang mudah dan efisien untuk menangani permintaan `HTTP` dan mengelola respons yang diterima dari server.

## Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.

`CookieRequest` digunakan untuk menangani sesi pengguna dalam aplikasi, khususnya untuk mengelola cookie yang digunakan untuk autentikasi dan menjaga status login pengguna.
Dengan `CookieRequest`, kita bisa menyimpan cookie yang diterima dari server dan mengirimkannya kembali pada setiap permintaan selanjutnya, sehingga server dapat mengenali pengguna yang sedang login.

Instance `CookieRequest` perlu dibagikan ke semua komponen di aplikasi Flutter untuk memastikan bahwa seluruh aplikasi menggunakan sesi dan autentikasi yang konsisten. Dengan berbagi instance `CookieRequest`, setiap komponen dalam aplikasi dapat mengakses dan mengirim cookie yang sama sehingga server tetap mengenali pengguna yang sedang login di setiap permintaan. Hal ini sangat penting dalam aplikasi yang membutuhkan autentikasi pengguna, karena memungkinkan fitur seperti login, logout, dan akses data pengguna yang aman dan terintegrasi di seluruh aplikasi.

## Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.

Mekanisme pengiriman data di Flutter dimulai dari pengambilan input dari pengguna melalui widget seperti `TextField` atau `Form`. Setelah itu, data yang diinput dikirim ke server menggunakan permintaan HTTP dengan bantuan library `http`. Server kemudian memproses data tersebut dan mengirimkan respons kembali dalam format JSON.
Di sisi Flutter, respons ini diuraikan dan diubah menjadi objek-objek yang dapat digunakan oleh aplikasi.
Data yang telah diuraikan kemudian dapat ditampilkan kepada pengguna melalui widget seperti ListView, GridView, atau widget lainnya yang sesuai dengan desain aplikasi.

## Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.

Proses autentikasi di Flutter melibatkan interaksi dengan backend, seperti Django untuk aplikasi ini.
Saat pengguna menginput data akun untuk login atau register, data tersebut dikirim ke server Django melalui permintaan HTTP.
Django kemudian memverifikasi atau menyimpan data tersebut dan mengirimkan respons yang berisi informasi autentikasi, seperti token atau cookie.
Informasi ini disimpan di aplikasi Flutter menggunakan `CookieRequest`.
Selama pengguna terautentikasi, aplikasi Flutter akan mengirim token atau cookie ini pada setiap permintaan ke server untuk menjaga sesi pengguna tetap aktif.
Ketika pengguna melakukan logout, aplikasi mengirim permintaan ke server untuk mengakhiri sesi, dan informasi autentikasi dihapus dari aplikasi, sehingga pengguna keluar dari aplikasi.

## Implementasi _checklist_

### Memastikan deployment proyek tugas Django kamu telah berjalan dengan baik.

Karena untuk saat ini integrasi django dan flutter dilakukan secara local, checklist ini cukup dicapai dengan memastikan bahwa server local telah berjalan baik dengan menjalankan perintah `python manage.py runserver`

### Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.

1. Pada proyek django, membuat aplikasi baru bernama `authentication`
2. Pastikan aplikasi yang baru dibuat telah ditambahkan ke `INSTALLED_APPS` di `settings.py` pada root project
3. Pada `views.py` aplikasi `authentication`, membuat fungsi baru bernama `register()` untuk menghandle registrasi via flutter
4. Membuat file `urls.py` pada aplikasi `authentication`
5. Melakukan routing untuk fungsi yang telah dibuat pada step-3 dengan menambahkan path ke fungsi tersebut
6. Pada `urls.py` proyek, menambahkan `urls.py` aplikasi `authentication`
7. Pada proyek flutter, membuat file `register.dart` di direktori `lib/screens`
8. Menambahkan package yang dibutuhkan dengan import pada file tersebut. Untuk package yang tidak tersedia secara default pada flutter, ditambakan dengan menjalankan perintah `flutter pub add nama_package`. Pada aplikasi ini, package yang ditambahkan dengan perintah tersebut adalah `provider`, `pbp_django_auth`, dan `http`.
9. Mengimplementasikan program untuk registrasi pada file `register.dart`

### Membuat halaman login pada proyek tugas Flutter.

1. Pada proyek django, membuat fungsi views baru pada aplikasi `authentication` dengan nama `login()`
2. Melakukan routing untuk fungsi baru tersebut di `urls.py` aplikasi `authentication`
3. Pada proyek flutter, membuat file `login.dart` di direktorir `lib/screens`
4. Menambahkan package yang dibutuhkan dengan melakukan import pada file tersebut
5. Mengimplementasikan program untuk login pada file `login.dart`

### Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.

1. Pastikan bahwa server django telah berjalan (sesuai dengan checklist pertama)
2. Pada file `android/app/src/main/AndroidManifest.xml` di proyek flutter, tambahkan `<uses-permission android:name="android.permission.INTERNET" />` di bawah tag application untuk memperbolehkan akses ke internet
3. Pada file `register.dart`, pastikan URL yang dituju pada response ketika tombol register ditekan telah sesuai dengan URL di mana proyek django dijalankan dan menuju ke path register

```dart
final response = await request.postJson(
                "http://127.0.0.1:8000/auth/register/", // URL proyek django untuk register flutter
                jsonEncode({
                  "username": username,
                  "password1": password1,
                  "password2": password2,
                }));
```

3. Pada file `login.dart`, pastikan URL yang dituju pada response ketika tombol login ditekan telah sesuai dengan URL di mana proyek django dijalankan dan menuju ke path login

```dart
final response = await request
                .login("http://127.0.0.1:8000/auth/login/", { // URL proyek django untuk login flutter
              'username': username,
              'password': password,
            });
```

4. Pada proyek django, membuat fungsi views baru `create_product_flutter` pada aplikasi `main`. Kemudian, pada proyek flutter, pada file `productentry_form.dart`, pastikan URL yang dituju pada response ketika tombol save ditekan telah sesuai dengan URL di mana proyek django dijalankan dan menuju ke path untuk menambahkan produk

```dart
final response = await request.postJson(
              "http://127.0.0.1:8000/create-flutter/", // URL django untuk menambahkan produk dari flutter
              jsonEncode(<String, String>{
                'name': _name,
                'stock': _stock.toString(),
                'price': _price.toString(),
                'description': _description,
              }),
```

5. Pada file `list_productentry.dart` (file ini dibuat pada beberapa checklist selanjutnya) pastikan URL yang dituju pada response ketika laman dimuat telah sesuai dengan URL di mana proyek django dijalankan dan menuju ke path untuk memberikan data produk

```dart
final response = await request.get('http://127.0.0.1:8000/json/');
```

6. Pada proyek django, membuat fungsi views baru `logout` pada aplikasi `authentication`. Kemudian, pada proyek flutter, pada file `product_cart.dart` pastikan URL yang dituju pada response ketika tombol logout ditekan telah sesuai dengan URL di mana proyek django dijalankan dan menuju ke path untuk melakukan logout

```dart
final response = await request.logout("http://127.0.0.1:8000/auth/logout/");
```

### Membuat model kustom sesuai dengan proyek aplikasi Django.

1. Salin model JSON pada alamat `http://127.0.0.1:8000/json/` (pastikan server local django berjalan dan sedang login pada suatu akun dan telah menambahkan setidaknya satu produk)

2. Membuka web https://app.quicktype.io/ kemudian tempel data JSON yang disalin pada step-1 di laman tersebut
3. Mengganti namanya menjadi `productEntry`, pastikan source type adalah JSON dan languange adalah dart. Kemudian tekan copy code
4. Pada proyek flutter, membuat direktori baru bernama `models` di dalam direktori `lib`
5. Dalam direktori `lib/models`, membuat file baru dengan nama `product_entry.dart`
6. Menempel kode yang telah disalin pada step-3

### Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy.

1. Pada direktori `lib/screens`, membuat file baru bernama `list_productentry.dart`.
2. Mengimport package yang dibutuhkan
3. Mengimplementasikan tampilan untuk daftar item

#### Tampilkan name, price, dan description dari masing-masing item pada halaman ini.

1. Pada file `list_productentry.dart`, tambahkan fungsi `fetchProduct` berikut untuk mengkonversi data json

```dart
Future<List<ProductEntry>> fetchProduct(CookieRequest request) async {
    final response = await request.get('http://127.0.0.1:8000/json/');
    // Melakukan decode response menjadi bentuk json
    var data = response;
    // Melakukan konversi data json menjadi object ProductEntry
    List<ProductEntry> listProduct = [];
    for (var d in data) {
      if (d != null) {
        listProduct.add(ProductEntry.fromJson(d));
      }
    }
    return listProduct;
  }
```

2. Pada widget Build, tambahkan kode berikut sebgai children dari `ListView`

```dart
Text(
  "${snapshot.data![index].fields.name}",
  style: const TextStyle(
    fontSize: 18.0,
    fontWeight: FontWeight.bold,
  ),
),
const SizedBox(height: 10),
Text("${snapshot.data![index].fields.description}"),
const SizedBox(height: 10),
Text("Stock: ${snapshot.data![index].fields.stock}"),
const SizedBox(height: 10),
Text("Price: Rp${snapshot.data![index].fields.price}")
```

### Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.

### Halaman ini dapat diakses dengan menekan salah satu item pada halaman daftar Item.

### Tampilkan seluruh atribut pada model item kamu pada halaman ini.

### Tambahkan tombol untuk kembali ke halaman daftar item.

### Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login.

Checklist ini diimplementasi dengan mengaitkan tiap produk ke user sehingga ketika endpoint JSON dipanggil data yang didapat otomatis telah difilter berdasarkan user.

```python
@csrf_exempt
def create_product_flutter(request):
    if request.method == 'POST':
        data = json.loads(request.body)
        print(data)
        new_product = Product.objects.create(
            user=request.user,   # Kaitkan langsyng ke user
            name=data["name"],
            stock=int(data["stock"]),
            price=int(data["price"]),
            description=data["description"],
        )
        new_product.save()
        return JsonResponse({"status": "success"}, status=200)
    else:
        return JsonResponse({"status": "error"}, status=401)
```

</details>
