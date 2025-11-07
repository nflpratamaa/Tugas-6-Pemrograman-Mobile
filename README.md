# Tugas 6 - Pemrograman Mobile

**Nama:** Naufal Aulia Pratama  
**NIM:** H1D023046  
**Tugas:** Passing Data dari Form ke Tampilan

---

## Deskripsi Project

Aplikasi Flutter sederhana yang mendemonstrasikan cara passing (mengirim) data dari form input ke halaman tampilan. User bisa input nama, NIM, dan tahun lahir, lalu data tersebut akan ditampilkan di halaman berikutnya dengan tampilan yang menarik.

---

## Penjelasan Proses Passing Data

### 1. Persiapan di FormData (form_data.dart)

Pertama, kita bikin controller untuk nangkap data yang user input:

```dart
final _nama = TextEditingController();
final _nim = TextEditingController();
final _tahunLahir = TextEditingController();
```

Controller ini kayak wadah yang nyimpen apa yang user ketik di form.

### 2. Ambil Data dari Form

Setelah user ngisi form dan tekan tombol "Simpan", kita ambil datanya pake `.text`:

```dart
_nama.text          // Ambil data nama
_nim.text           // Ambil data NIM
_tahunLahir.text    // Ambil data tahun lahir
```

### 3. Kirim Data ke Halaman Berikutnya

Nah ini bagian pentingnya! Kita pake `Navigator.push()` untuk pindah halaman sekaligus kirim data:

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (_) => TampilData(
      nama: _nama.text,           // Kirim data nama
      nim: _nim.text,             // Kirim data NIM
      tahunLahir: _tahunLahir.text, // Kirim data tahun lahir
    ),
  ),
);
```

Jadi kita passing data lewat **parameter constructor** class `TampilData`.

### 4. Terima Data di TampilData (tampil_data.dart)

Di halaman tujuan, kita bikin variable untuk terima datanya:

```dart
class TampilData extends StatelessWidget {
  final String nama, nim, tahunLahir; // Variable penampung data

  const TampilData({
    Key? key,
    required this.nama,        // Terima data nama
    required this.nim,         // Terima data NIM
    required this.tahunLahir,  // Terima data tahun lahir
  }) : super(key: key);
```

Keyword `required` artinya data ini **wajib** dikirim, gak boleh kosong.

### 5. Tampilkan Data

Setelah data diterima, tinggal ditampilin aja:

```dart
Text(nama)          // Tampilkan nama
Text(nim)           // Tampilkan NIM
Text('$umur tahun') // Tampilkan umur hasil hitung
```

---

## Alur Passing Data (Ringkasan)

```
FormData                          TampilData
   |                                  |
   | 1. User isi form                 |
   | 2. Tekan tombol Simpan           |
   | 3. Ambil data dari controller    |
   |    (_nama.text, dll)             |
   |                                  |
   | 4. Navigator.push() -----------> | 5. Terima data via
   |    kirim data lewat parameter    |    constructor
   |                                  |
   |                                  | 6. Tampilkan data
   |                                  |    di widget Text
```

---

## Kesimpulan

Cara passing data di Flutter itu simple:
1. **Controller** untuk nangkap input user
2. **Navigator.push()** untuk pindah halaman + kirim data
3. **Constructor parameter** untuk terima data
4. **Variable** untuk nyimpen data yang diterima
5. **Widget** untuk tampilkan data

Gak ribet kok, intinya data dari halaman A dikirim lewat parameter pas pindah ke halaman B. Kayak kirim paket, si pengirim (FormData) kasih paket, si penerima (TampilData) terima dan buka paketnya! 📦

---

## Cara Menjalankan

```bash
flutter run
```

---

## Screenshot

*(Tambahkan screenshot aplikasi disini jika diperlukan)*

---

## Teknologi yang Digunakan

- Flutter SDK
- Dart
- Material Design

---

Dibuat dengan ❤️ untuk Tugas Pemrograman Mobile
