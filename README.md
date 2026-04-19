![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=flat&logo=dart&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat&logo=supabase&logoColor=white)
![GetX](https://img.shields.io/badge/GetX-8A2BE2?style=flat&logo=flutter&logoColor=white)

# Ad A Coffee – Flutter Coffee Management App
## Deskripsi Singkat
Perkembangan teknologi mobile mendorong digitalisasi pada berbagai sektor bisnis, termasuk industri coffee shop. Sistem manual dalam pengelolaan menu, transaksi, dan stok seringkali menimbulkan permasalahan seperti ketidakefisienan, human error, dan keterlambatan pelaporan.

Berdasarkan permasalahan tersebut, dikembangkan aplikasi Ad A Coffee, yaitu sistem informasi berbasis mobile yang mampu mengelola operasional coffee shop secara terintegrasi menggunakan teknologi Flutter dan Supabase.

## Tujuan Pengembangan
Pengembangan aplikasi ini bertujuan untuk:

- Mengelola data menu kopi secara terstruktur
- Memproses transaksi penjualan
- Mengontrol stok barang
- Menyajikan laporan penjualan
- Mendukung multi-role user (admin & rider)
- Mengintegrasikan database secara real-time

## Alur Sistem
- User login melalui auth_service
- Sistem memverifikasi ke Supabase
- User masuk ke dashboard
- Data diambil dari service layer
- Data ditampilkan ke UI
- Transaksi dilakukan
- Stok otomatis diperbarui
- Laporan dapat diakses real-time


## Teknologi yang Digunakan
- Flutter (SDK ^3.10.8)
- Supabase → Backend as a Service (Database & Auth)
- fl_chart → Visualisasi data (grafik)
- intl → Formatting (mata uang, tanggal, dll)

## Cara Menjalankan

1. Clone repository
```bash
git clone <url-repo>
```

2. Masuk ke folder project
```bash
cd pa-ada-coffe
```

3. Install dependencies
```bash
flutter pub get
```

4. Jalankan aplikasi

- jalankan langsung
```bash
flutter run
```
- jalankan melalui web
```bash
flutter run -d chrome
```

> Pastikan menggunakan Flutter versi stabil terbaru. Cek versi aktif dengan `flutter --version`.



## Struktur Project

``` bash
lib
├── core
│   ├── app_constans.dart
│   ├── supabase
│   │   ├── selected_gerobak_store.dart
│   │   └── supabase_config.dart
│   └── theme
│       └── app_theme.dart
├── data
│   ├── models
│   │   ├── detail_transaksi_model.dart
│   │   ├── menu_item_model.dart
│   │   └── transaksi_model.dart
│   └── services
│       ├── auth_service.dart
│       ├── gerobak_service.dart
│       ├── menu_service.dart
│       ├── report_service.dart
│       ├── stock_service.dart
│       └── transaksi_service.dart
├── main.dart
├── presentation
│   ├── auth
│   │   ├── auth_wrapper.dart
│   │   ├── login_page.dart
│   │   └── register_page.dart
│   ├── dashboard
│   │   └── home_screen.dart
│   ├── home
│   │   └── main_navigation.dart
│   ├── menu
│   │   └── menu_screen.dart
│   ├── profile
│   │   └── profile_screen.dart
│   ├── reports
│   │   └── reports_screen.dart
│   ├── rider
│   │   ├── rider_navigation.dart
│   │   └── rider_page.dart
│   ├── sales
│   │   └── sales_screen.dart
│   ├── stock
│   │   └── stock_screen.dart
│   └── widgets
│       ├── app_button.dart
│       ├── app_card.dart
│       ├── dashboard_card.dart
│       ├── empty_state.dart
│       └── header.dart
└── utils
    ├── currency_formatter.dart
    └── dialog_helper.dart

```
## Fitur Aplikasi
#### 1. Autentikasi Pengguna (Login & Register)
Aplikasi menyediakan fitur login dan registrasi menggunakan Supabase Authentication. Data pengguna disimpan pada tabel profiles dan dilengkapi dengan role seperti owner dan rider untuk membedakan hak akses.

#### 2. Menampilkan Data Menu (Read)
Aplikasi menampilkan seluruh data menu kopi yang tersimpan di database Supabase dalam bentuk daftar (ListView), lengkap dengan informasi nama, harga, kategori, dan stok.

#### 3. Menambahkan Data Menu (Create)
Pengguna dapat menambahkan menu baru melalui halaman form input. Data yang dimasukkan akan langsung disimpan ke database Supabase.

#### 4. Mengedit Data Menu (Update)
Pengguna dapat memperbarui data menu yang sudah ada, seperti nama produk, harga, kategori, dan stok melalui halaman edit.

#### 5. Menghapus Data Menu (Delete)
Pengguna dapat menghapus data menu dari database melalui tombol delete pada setiap item menu.

#### 6. Transaksi Penjualan
Aplikasi menyediakan fitur untuk melakukan transaksi penjualan, di mana pengguna dapat memilih menu, menentukan jumlah, dan sistem akan menghitung total harga secara otomatis sebelum disimpan ke database.

#### 7. Manajemen Stok
Aplikasi mengelola stok barang pada setiap gerobak. Stok akan otomatis berkurang saat transaksi terjadi dan dapat ditambahkan kembali melalui fitur update stok.

#### 8. Manajemen Gerobak
Aplikasi menampilkan data gerobak (cabang penjualan) dan memungkinkan filtering berdasarkan role pengguna, sehingga rider hanya dapat mengakses gerobak yang menjadi tanggung jawabnya.

#### 9. Laporan dan Analisis
Aplikasi menyediakan fitur laporan seperti total pendapatan, jumlah transaksi, serta data produk terlaris. Selain itu, ditampilkan juga grafik tren penjualan untuk membantu analisis performa bisnis.

#### 10. Navigasi Antar Halaman
Aplikasi menggunakan sistem navigasi untuk berpindah antar halaman, seperti:
- Halaman dashboard
- Halaman menu
- Halaman transaksi
- Halaman stok
- Halaman laporan





## Database
Aplikasi menggunakan Supabase sebagai backend database yang menangani penyimpanan data, autentikasi, serta pengolahan data secara real-time.
### Tabel yang Digunakan
#### 1.`menu`
| Field      | Tipe Data          |
| ---------- | ------------------ |
| id         | uuid (Primary Key) |
| name       | text               |
| price      | numeric            |
| category   | text               |
| stock      | int4               |
| emoji      | text               |
| created_at | timestamptz        |

#### 2.`transaksi`
| Field       | Tipe Data          |
| ----------- | ------------------ |
| id          | uuid (Primary Key) |
| gerobak_id  | uuid (Foreign Key) |
| rider_id    | uuid (Foreign Key) |
| total_harga | numeric            |
| tanggal     | timestamptz        |
| status      | text               |

#### 3.`detail_transaksi`
| Field        | Tipe Data          |
| ------------ | ------------------ |
| id           | uuid (Primary Key) |
| transaksi_id | uuid (Foreign Key) |
| menu_id      | uuid (Foreign Key) |
| qty          | int4               |
| harga        | numeric            |
| subtotal     | numeric            |

#### 4.`profiles`
| Field | Tipe Data          |
| ----- | ------------------ |
| id    | uuid (Primary Key) |
| name  | text               |
| role  | text               |
| email | text               |
| created_at  | timestamptz  |
| photo_url       | text     |

#### 5.`gerobak`
| Field        | Tipe Data          |
| ------------ | ------------------ |
| id           | uuid (Primary Key) |
| nama_gerobak | text               |
| lokasi       | text               |
| rider_id     | uuid (Foreign Key) |
| created_at   | timestamptz        |



#### 6.`stok_gerobak`
| Field         | Tipe Data          |
| ------------- | ------------------ |
| id            | uuid (Primary Key) |
| gerobak_id    | uuid (Foreign Key) |
| menu_id       | uuid (Foreign Key) |
| stok_awal     | int4               |
| stok_saat_ini | int4               |
| created_at    | timestamptz        |


#### 7.`stock_outlet`
| Field      | Tipe Data          |
| ---------- | ------------------ |
| id         | uuid (Primary Key) |
| menu_id    | uuid (Foreign Key) |
| stok       | int4               |
| created_at | timestamptz        |
| gerobak_id | text               |


#### 8.`riders`
| Field      | Tipe Data          |
| ---------- | ------------------ |
| id         | uuid (Primary Key) |
| profile_id | uuid (Foreign Key) |
| nama_rider | text               |
| no_hp      | text               |
| created_at | timestamptz        |


## Widget yang Digunakan

Dalam pengembangan aplikasi Ad A Coffee, berbagai widget Flutter dimanfaatkan untuk membangun antarmuka yang responsif, modular, dan mudah dipelihara. Penggunaan widget dibagi menjadi dua kategori utama, yaitu built-in widget (bawaan Flutter) dan custom widget (komponen buatan sendiri).

### 1. Built-in Widget (Flutter)

Berikut beberapa widget utama yang digunakan:

a. Struktur Layout
- `Scaffold` → Kerangka dasar halaman (AppBar, Body, BottomNav)
- `AppBar` → Header aplikasi
- `Column & Row` → Menyusun layout secara vertikal & horizontal
- `Expanded & Flexible` → Mengatur proporsi ruang

Contoh:
``` dart
Scaffold(
  appBar: AppBar(title: Text("Dashboard")),
  body: Column(
    children: [
      Text("Welcome"),
    ],
  ),
)
```

#### b. Widget Tampilan Data
- `Text` → Menampilkan teks
- `Image` → Menampilkan gambar dari assets
- `Icon` → Menampilkan ikon
- `Card` → Menampilkan informasi dalam bentuk kartu

Contoh:
``` dart
Card(
  child: ListTile(
    title: Text("Espresso"),
    subtitle: Text("Rp 20.000"),
  ),
)
```

#### c. Navigasi
- `Navigator` → Perpindahan antar halaman
- `BottomNavigationBar` → Navigasi utama aplikasi

Contoh:
``` dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (_) => DetailPage()),
);
```

#### d. Input & Interaksi
- `TextField` → Input user
- `ElevatedButton` → Tombol aksi
- `GestureDetector` → Menangani event klik

### 2. Custom Widget (Reusable Component)

Aplikasi ini juga mengimplementasikan custom widget untuk meningkatkan efisiensi dan konsistensi UI.

#### a. DashboardCard

Widget ini digunakan untuk menampilkan ringkasan data seperti total penjualan.

``` dart
class DashboardCard extends StatelessWidget {
  final String title;
  final String value;

  const DashboardCard({
    required this.title,
    required this.value,
  });

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Column(
        children: [
          Text(title),
          Text(value),
        ],
      ),
    );
  }
}
```

#### b. CustomButton

Digunakan untuk standarisasi tombol di seluruh aplikasi:
``` dart
ElevatedButton(
  onPressed: onPressed,
  child: Text(label),
)
```

#### c. Widget Modular Lainnya
- `MenuItemCard` → Menampilkan daftar menu kopi
- `TransactionItem` → Menampilkan detail transaksi
- `StockItemTile` → Menampilkan data stok
- `ReportChartWidget` → Visualisasi data (fl_chart)


## Halaman Aplikasi
### 1 Login Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/d99e58c0-5701-449e-8147-82b3a0f0f97d" />

### 2 Register Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/0f8bda92-d072-4798-9035-f6031bde8b78" />

### 3 TAMPILAN OWNER

#### a. Home Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/06185ef8-fc5a-4140-8261-69acc2cb97a9" />

#### b. Sales Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/c03e4562-c25d-433e-8b40-a481a2e23a59" />

#### c. Stock Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/a5c5c626-238f-4e7f-af03-e526344c303c" />

#### d. Reports Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/4c258eea-5c9f-45fc-81d3-bf85a7008028" />

#### e. Profile Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/16068026-1934-4685-856b-b2bc01dbac03" />

### 4. Tampilan Rider
#### a. Home Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/527544d2-1aeb-432a-953d-e7011b388305" />

#### b. Sales Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/f0050cd5-faa0-4015-85dc-bdb5cdf936e5" />

#### c. Reports Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/3a79eb5f-6b71-4f37-b1e3-c63f465e0af7" />

#### d. Profile Page
<img width="250" height="415" alt="image" src="https://github.com/user-attachments/assets/a43af6f1-109c-4acc-9b85-def317f08a63" />



















## Kesimpulan
Aplikasi Ad A Coffee merupakan implementasi sistem informasi berbasis mobile yang dirancang untuk mendukung pengelolaan operasional coffee shop secara terintegrasi. Sistem ini menggabungkan berbagai fungsi utama seperti manajemen menu, transaksi penjualan, pengelolaan stok, serta penyajian laporan dalam satu platform yang terstruktur. Dengan memanfaatkan Flutter sebagai framework utama dan Supabase sebagai backend service, aplikasi ini mampu menghadirkan pengolahan data secara real-time dengan arsitektur yang modular dan terorganisir. Secara keseluruhan, aplikasi ini menunjukkan penerapan konsep pengembangan perangkat lunak yang sistematis, mulai dari pemisahan layer hingga integrasi layanan backend, sehingga mampu memenuhi kebutuhan dasar sistem informasi pada skala bisnis coffee shop.


