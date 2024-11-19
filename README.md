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
