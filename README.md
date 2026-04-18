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

3. Buat file `.env` di root project
```
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
```

4. Install dependencies
```bash
flutter pub get
```

5. Jalankan aplikasi

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

```` bash
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

````

## Fitur Aplikasi

## Databse

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

## Kesimpulan
Aplikasi Ad A Coffee merupakan implementasi sistem informasi berbasis mobile yang dirancang untuk mendukung pengelolaan operasional coffee shop secara terintegrasi. Sistem ini menggabungkan berbagai fungsi utama seperti manajemen menu, transaksi penjualan, pengelolaan stok, serta penyajian laporan dalam satu platform yang terstruktur. Dengan memanfaatkan Flutter sebagai framework utama dan Supabase sebagai backend service, aplikasi ini mampu menghadirkan pengolahan data secara real-time dengan arsitektur yang modular dan terorganisir. Secara keseluruhan, aplikasi ini menunjukkan penerapan konsep pengembangan perangkat lunak yang sistematis, mulai dari pemisahan layer hingga integrasi layanan backend, sehingga mampu memenuhi kebutuhan dasar sistem informasi pada skala bisnis coffee shop.


