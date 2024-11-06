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
7. SizedBox: Menambahkan jarak vertikal atau horizontal.
8. Card: Menyediakan kontainer dengan elevasi dan dekorasi untuk membuat tampilan seperti kartu.
9. Container: Menyediakan kontainer dengan opsi untuk margin, padding, dan warna latar.
10. GridView.count: Menampilkan child widget dalam grid dengan jumlah kolom tetap.
11. Text: Menampilkan teks dalam aplikasi.
12. InkWell: Menambahkan interaksi "tap" dengan efek ripple.
13. ScaffoldMessenger: Menampilkan SnackBar untuk notifikasi sement ara.
14. SnackBar: Menampilkan pesan sementara di bagian bawah layar.
15. Icon: Menampilkan ikon grafis.

### Apa fungsi dari `setState()`? Variabel apa saja yang dapat terdampak dengan fungsi tersebut?

### Perbedaan antara `const` dengan `final`

### Implementasi _checklist_

#### Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.

1. Pada direktori yang saya tentukan, saya menjalankan perintah `flutter create easyshop` untuk membuat flutter app baru dengan nama easyshop

2. Akan terdapat direktori baru bernama `easyshop`. Pindah direktori ke direktori flutter app baru tersebut.

3. Membuat file baru bernama `menu.dart` pada direktori `../easyshop/lib`

4. Pada file `menu.dart`, mengimpor package `package:flutter/material.dart`. Kemudian, menambahkan class `MyHomePage` sebagai homepage, `InfoCard` sebagai kartu yang menampilkan informasi user, `ItemCard` sebagai kartu dengan fungsionalitas button, dan `ItemHomePage`sebagai attribut yang ditampilkan oleh tiap `ItemCard`

#### Membuat tiga tombol sederhana dengan ikon dan teks untuk: melihat daftar produk, menambah produk, dan logout

1. Pada file `menu.dart`, menambahkan attribut berikut pada class `MyHomePage`

```
final List<ItemHomepage> items = [
    ItemHomepage("Lihat Daftar Produk", Icons.view_day_outlined, Colors.blueAccent),
    ItemHomepage("Tambah Produk", Icons.add, Colors.greenAccent),
    ItemHomepage("Logout", Icons.logout, Colors.redAccent),
  ];
```

2. Class `ItemHomePage` akan berfungsi sebagai attribut-attribut yang dimiliki oleh tiap button. Adapun isi dari `ItemHomePage` adalah sebagai berikut.

```
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

```
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
