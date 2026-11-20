# 🎮 Tic Tac Toe App — Interactive 3×3 Grid Game

![Expo](https://img.shields.io/badge/Expo-~58.0.22-000020?style=for-the-badge&logo=expo&logoColor=white)
![React Native](https://img.shields.io/badge/React_Native-0.88.1-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![React](https://img.shields.io/badge/React-19.3.0-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-~6.0.3-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Expo Router](https://img.shields.io/badge/Expo_Router-~58.0.29-4630EB?style=for-the-badge&logo=expo&logoColor=white)

---

## 📖 Deskripsi Proyek

**Tic Tac Toe App** adalah aplikasi permainan papan interaktif klasik berformat **Grid 3×3** untuk perangkat *mobile* (Android & iOS) serta Web yang dibangun menggunakan **React Native** dan **Expo** dengan bahasa **TypeScript**.

Proyek ini dikembangkan sebagai bagian dari **Tugas Sesi #5 Mata Kuliah Pemrograman Mobile**. Aplikasi ini mendemonstrasikan penerapan konsep fundamental pengembangan aplikasi *mobile* menggunakan React Native, meliputi:
- **State Management** menggunakan React Hook `useState` dan prinsip **Immutability** (`[...board]`).
- **Game Logic & Algoritma Deteksi Kemenangan** pada matriks/array 1 dimensi berukuran 9 elemen.
- **Event Handling** & *Early Return Guard* pada komponen sentuh (`TouchableOpacity`).
- **Tata Letak Responsif** menggunakan **Flexbox** (`StyleSheet.create`) dan *Reusable Render Function*.

---

## ✨ Fitur Utama

Berdasarkan implementasi kode pada [`src/app/index.tsx`](./src/app/index.tsx), aplikasi ini memiliki fitur-fitur berikut:

1. **Papan Permainan Grid 3×3 Interaktif**
   - Dirender menggunakan fungsi *reusable* `renderSquare(index)` yang tersusun dalam 3 baris Flexbox horizontal (`flexDirection: 'row'`).
   - Setiap kotak menggunakan komponen `TouchableOpacity` (`activeOpacity={0.7}`) untuk memberikan umpan balik visual saat disentuh.

2. **Sistem Giliran Pemain Dinamis (`X` & `O`)**
   - Mengelola giliran pemain secara bergantian menggunakan state boolean `xIsNext` (dimulai dari pemain **X**).
   - Pembedaan visual warna simbol: **Merah (`#e74c3c`)** untuk pemain **X** dan **Biru (`#3498db`)** untuk pemain **O**.

3. **Algoritma Deteksi Pemenang (`calculateWinner`)**
   - Mengevaluasi 8 kombinasi garis kemenangan setiap kali state papan berubah:
     - **3 Baris Horizontal**: `[0, 1, 2]`, `[3, 4, 5]`, `[6, 7, 8]`
     - **3 Kolom Vertikal**: `[0, 3, 6]`, `[1, 4, 7]`, `[2, 5, 8]`
     - **2 Garis Diagonal**: `[0, 4, 8]`, `[2, 4, 6]`

4. **Deteksi Kondisi Seri (*Draw*) Otomatis**
   - Mengecek apakah seluruh 9 kotak telah terisi (`board.every((square) => square !== null)`) tanpa adanya pemenang, lalu menampilkan status `"Permainan Seri (Draw)!"`.

5. **Proteksi Interaksi (*Early Return Guard*)**
   - Fungsi `handlePress(index)` secara otomatis mengabaikan ketukan (*tap*) apabila kotak sudah terisi simbol atau permainan telah dimenangkan oleh salah satu pemain (`if (board[index] || winner) return;`).

6. **Tombol Mulai Ulang (*Reset Game*)**
   - Menyediakan tombol **Mulai Ulang** (`resetGame`) yang mengembalikan seluruh elemen array papan ke `null` dan mengatur ulang giliran awal kembali ke pemain **X**.

7. **Type-Safety dengan TypeScript**
   - Dilengkapi definisi tipe ketat (`type Player = 'X' | 'O'` dan `type SquareValue = Player | null`) yang berjalan di atas konfigurasi TypeScript `strict: true`.

---

## 📂 Struktur Proyek

```text
TicTacToeApp/
├── assets/                     # Aset statis (ikon aplikasi, splash screen, gambar)
│   ├── expo.icon/              # Konfigurasi ikon iOS
│   └── images/                 # Gambar ikon Android, web favicon, dan splash screen
├── scripts/
│   └── reset-project.js        # Skrip utilitas bawaan Expo untuk mereset template proyek
├── src/
│   ├── app/                    # Direktori utama berbasis file-based routing (Expo Router)
│   │   ├── _layout.tsx         # Konfigurasi root layout, tema, dan navigasi aplikasi
│   │   ├── index.tsx           # Layar utama Permainan Interaktif Tic Tac Toe (Grid 3x3)
│   │   └── explore.tsx         # Layar informasi tambahan bawaan template
│   ├── components/             # Komponen UI pendukung (themed view/text, tab, splash icon)
│   ├── constants/
│   │   └── theme.ts            # Konstanta warna dan tema tampilan
│   ├── hooks/                  # Custom hooks untuk deteksi skema warna & tema
│   └── global.css              # Styling global untuk target Web
├── AGENTS.md                   # Panduan konfigurasi dan standar pengembangan Expo
├── app.json                    # Konfigurasi metadata aplikasi Expo (nama, slug, ikon, plugin)
├── package.json                # Daftar dependensi, versi library, dan skrip NPM
├── tsconfig.json               # Konfigurasi compiler TypeScript (strict mode & path alias)
└── README.md                   # Dokumentasi proyek
```

---

## ⚙️ Prasyarat & Cara Menjalankan

### Prasyarat
Pastikan perangkat Anda telah terinstal:
- **Node.js** (disarankan versi LTS terbaru) & **npm**
- Aplikasi **Expo Go** di perangkat fisik (Android / iOS), atau **Android Studio Emulator** / **iOS Simulator** di komputer Anda.

### Langkah Instalasi & Menjalankan Aplikasi

1. **Masuk ke direktori proyek**
   ```bash
   cd TicTacToeApp
   ```

2. **Instal seluruh dependensi**
   ```bash
   npm install
   ```

3. **Jalankan server pengembangan Expo**
   ```bash
   npx expo start
   ```

4. **Buka aplikasi di platform pilihan Anda**
   Setelah Metro Bundler berjalan di terminal:
   - **Perangkat Fisik**: Pindai (*scan*) QR Code yang tampil di terminal menggunakan aplikasi **Expo Go** (Android) atau aplikasi **Kamera** (iOS).
   - **Android Emulator**: Tekan tombol `a` di terminal, atau jalankan:
     ```bash
     npm run android
     ```
   - **iOS Simulator** (khusus macOS): Tekan tombol `i` di terminal, atau jalankan:
     ```bash
     npm run ios
     ```
   - **Web Browser**: Tekan tombol `w` di terminal, atau jalankan:
     ```bash
     npm run web
     ```

---

## 📸 Tangkapan Layar / Preview

> *Catatan: Ganti path gambar di bawah ini dengan file screenshot hasil tangkapan layar aplikasi Anda.*

| Tampilan Awal Permainan | Giliran Bermain (`X` & `O`) | Kondisi Menang / Seri (Draw) |
| :---: | :---: | :---: |
| ![Tampilan Awal](./assets/screenshots/preview-initial.png) | ![Giliran Bermain](./assets/screenshots/preview-gameplay.png) | ![Kondisi Akhir](./assets/screenshots/preview-winner.png) |
| *Papan kosong & giliran pemain X* | *Interaksi pengisian simbol X dan O* | *Deteksi pemenang & tombol Mulai Ulang* |

---

## 👨‍💻 Identitas Pembuat

| Atribut | Keterangan |
| :--- | :--- |
| **Nama** | **Fajar Try Sutrasno** |
| **NPM** | `41155050210053` |
| **Program Studi** | Teknik Informatika |
| **Universitas** | Universitas Langlangbuana (UNLA) |
| **Mata Kuliah** | Pemrograman Mobile — Tugas Sesi #5 |

---

<p align="center">
  Dibuat dengan ❤️ menggunakan <strong>React Native</strong> & <strong>Expo</strong>
</p>
