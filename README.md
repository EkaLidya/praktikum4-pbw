Eka Lidya Rahmadini
4523210039
Praktikum PPBW (B)

# 🌀 LaraPress — Instalasi & Konfigurasi Laravel Breeze

Proyek ini menggunakan *Laravel Breeze* sebagai sistem autentikasi dasar dengan dukungan Blade dan Tailwind CSS.  
Dokumen ini memandu Anda melalui proses instalasi, konfigurasi, serta pemahaman struktur yang dihasilkan oleh Breeze.

---

## ⚙ Bagian 1: Instalasi Laravel Breeze

### 1️⃣ Masuk ke Direktori Proyek
Buka terminal dan masuk ke folder proyek *LaraPress*.

### 2️⃣ Instal Breeze via Composer
Lakukan instalasi paket *Laravel Breeze* untuk menambahkan fitur autentikasi dasar.

<img width="1365" height="719" alt="image" src="https://github.com/user-attachments/assets/60e6179f-270e-4c16-b2bf-810d03764d61" />



### 3️⃣ Jalankan Perintah Instalasi Breeze
Setelah instalasi selesai, jalankan proses publikasi file Breeze agar semua komponen (controller, view, dan route) ditambahkan ke dalam proyek.  
Saat proses ini berjalan, pilih opsi berikut:
- Pilih *Blade with Alpine* (opsi nomor 0)  
- Pilih *No* untuk Dark Mode support  
- Pilih *Pest* (opsi nomor 0) sebagai testing framework

<img width="1365" height="716" alt="image" src="https://github.com/user-attachments/assets/23ec2f0b-0a92-4992-8ac6-e4935040fdcd" />


### 4️⃣ Instalasi Dependensi Frontend
Breeze menggunakan *Tailwind CSS*, sehingga perlu menginstal dependensi JavaScript agar tampilan dapat dikompilasi dengan benar.

<img width="1365" height="721" alt="image" src="https://github.com/user-attachments/assets/864321de-c768-48bf-8ca8-c37e5d3d6711" />


### 5️⃣ Kompilasi Aset Frontend
Lakukan proses kompilasi untuk menyiapkan file CSS dan JavaScript yang akan digunakan di browser.

<img width="470" height="269" alt="image" src="https://github.com/user-attachments/assets/073b10bd-de2f-4d4d-9768-36fedb89d3bb" />


### 6️⃣ Jalankan Migrasi Database
Migrasi ini menambahkan kolom remember_token pada tabel users dan membuat tabel password_reset_tokens yang dibutuhkan untuk autentikasi.

<img width="381" height="311" alt="image" src="https://github.com/user-attachments/assets/8a25dde0-18f7-4719-aa29-80c5ce91c729" />


### 7️⃣ Jalankan Aplikasi
Setelah semua langkah selesai, jalankan server Laravel dan buka proyek di browser.  
Jika berhasil, akan muncul tautan *“Log in”* dan *“Register”* di pojok kanan atas.  
Cobalah membuat akun baru dan login untuk memastikan sistem autentikasi berfungsi.

<img width="1358" height="679" alt="image" src="https://github.com/user-attachments/assets/86f343ef-0dab-45cf-9102-51e1eda5fb9f" />
<img width="1362" height="681" alt="image" src="https://github.com/user-attachments/assets/ce2f1cf2-1e24-4cb8-a106-b812f9b58922" />




---

## 🧩 Bagian 2: Membedah Hasil Instalasi Breeze

Bagian ini bertujuan agar Anda memahami apa saja yang telah ditambahkan oleh Breeze ke dalam proyek.

### 🔹 Rute Baru
Buka file routes/web.php dan perhatikan baris pemanggilan require __DIR__.'/auth.php';.  
File routes/auth.php berisi semua rute yang berhubungan dengan autentikasi seperti login, register, logout, dan reset password.

### 🔹 Controller Baru
Masuk ke folder app/Http/Controllers/Auth/.  
Di sini terdapat beberapa controller baru, seperti:
- AuthenticatedSessionController untuk menangani proses login dan logout.  
- RegisteredUserController untuk registrasi pengguna baru.  
- PasswordResetLinkController untuk fitur lupa kata sandi.

Pelajari isi tiap file untuk memahami logika alur autentikasi di Laravel.

### 🔹 View Baru
Lihat folder resources/views/auth/.  
Folder ini berisi semua tampilan form autentikasi, termasuk halaman login, register, dan reset password.

---

## 🔐 Bagian 3: Mengamankan Rute CRUD

Gunakan sistem autentikasi Breeze untuk melindungi fitur-fitur CRUD postingan yang sudah dibuat.

1. Buka file routes/web.php.  
2. Temukan semua rute yang berkaitan dengan pembuatan, penyimpanan, pengeditan, pembaruan, dan penghapusan postingan.  
3. Bungkus semua rute tersebut di dalam *route group* yang menggunakan middleware('auth').  
   Dengan cara ini, hanya pengguna yang sudah login yang dapat mengakses halaman CRUD.  
4. Setelah itu, logout dari aplikasi lalu coba akses halaman pembuatan postingan secara langsung.  
   Laravel akan otomatis mengarahkan Anda ke halaman login, menandakan proteksi berhasil.

<img width="1359" height="722" alt="image" src="https://github.com/user-attachments/assets/87d038f6-ecf0-4b87-b072-b14c542b4095" />


---

## 🧠 Uji Coba Keamanan
1. Logout dari akun Anda.  
2. Coba buka URL pembuatan postingan secara langsung di browser.  
3. Jika sistem mengarahkan Anda ke halaman login, artinya fitur middleware autentikasi sudah berfungsi dengan benar.

---

## 📚 Kesimpulan
Setelah mengikuti seluruh langkah:
- *Laravel Breeze* telah berhasil diinstal dan dikonfigurasi.  
- Proyek *LaraPress* kini memiliki sistem autentikasi lengkap (login, register, logout).  
- Semua fitur CRUD postingan kini dilindungi oleh autentikasi pengguna.

---
