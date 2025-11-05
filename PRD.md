# 🏆 Product Requirements Document (PRD)
## Aplikasi GSPORTS v2.0

### 👥 Tim Pengembang
* **1. Ahmad Rois** (221240001239)  
* **2. M. Gilang M.W. Sabdokafi** (221240001248)

---

## 📘 1. Ringkasan Produk

**GSPORTS** adalah aplikasi berbasis Flutter yang menyediakan layanan **pemesanan lapangan olahraga secara real-time** untuk berbagai cabang olahraga seperti futsal, badminton, dan basket.  
Aplikasi ini kini dikembangkan menjadi sistem **SaaS multi-tenant**, di mana setiap _Sport Center (SC)_ memiliki akun admin masing-masing, sementara pengguna umum dapat mencari, memesan, dan berbagi biaya sewa lapangan.

Versi 2.0 menghadirkan peningkatan besar:
- **Mode Tamu (Guest Mode)**  
- **Patungan (Split Booking)**  
- **Tarif Admin sebagai Revenue Stream**  
- **Fitur Papan Skor (Scoreboard Integration)**  
- **Sistem Freemium dan Subscription Premium**

---

## 🎯 2. Tujuan Produk

Meningkatkan efisiensi dan keterjangkauan akses terhadap lapangan olahraga dengan:
1. Menyediakan pengalaman pengguna yang mudah dan cepat, bahkan tanpa login.  
2. Menawarkan sistem _booking_ kolaboratif untuk mengurangi beban biaya pemain.  
3. Memberikan nilai tambah bagi pengembang melalui pendapatan admin fee dan fitur premium.  
4. Menumbuhkan komunitas pemain melalui integrasi papan skor dan riwayat pertandingan.  

---

## 🧩 3. Fitur Utama

### 🏠 3.1 Guest Mode (Tanpa Login)
- Pengguna baru dapat langsung menjelajahi daftar lapangan dan melihat ketersediaan jadwal tanpa login.
- Login hanya diperlukan saat akan melakukan pemesanan, menyimpan skor pertandingan, atau mengakses fitur premium.

### 🤝 3.2 Patungan (Split Booking)
- Satu booking dapat diisi oleh beberapa pengguna.
- Biaya sewa dibagi rata berdasarkan jumlah peserta (misal 4 pemain badminton → ¼ biaya per orang).
- Terdapat **kode undangan (join code)** untuk mengajak pemain lain bergabung.

### 💰 3.3 Admin Fee (Platform Revenue Stream)
- Setiap pemesanan akan dikenai potongan **5%** sebagai pendapatan platform.
- Sistem mendukung pencatatan **admin fee** dan **pembayaran bersih (net amount)** untuk Sport Center.

### 🧮 3.4 Scoreboard Integration
- Pengguna dapat mencatat hasil pertandingan di papan skor digital.
- Skor dapat disimpan ke akun pengguna untuk riwayat pertandingan.
- Mendukung mode offline (penyimpanan lokal) dan online (Appwrite Database).

### 💎 3.5 Freemium & Subscription System
- Pengguna baru mendapatkan **5 kuota booking gratis** dan akses ke **5 cabang olahraga**.
- Untuk akses tak terbatas, pengguna harus **upgrade ke Premium Subscription**.
- Sistem subscription otomatis memperbarui status dan masa aktif pengguna.

---

## ⚙️ 4. Arsitektur Sistem

### 🏗️ 4.1 High-Level System Architecture

```mermaid
graph TD
    A[Flutter App] -->|SDK / REST| B[Appwrite Backend]
    B --> C[Database]
    B --> D[Auth & Teams]
    B --> E[Functions]
    B --> F[Realtime]
    E --> G[Midtrans/Xendit Payment Gateway]
    E --> H[Admin Fee Calculator]
    E --> I[Quota & Subscription Checker]
    E --> J[Patungan Manager]
    E --> K[Scoreboard Recorder]
    A --> L[Hive Local Storage]
