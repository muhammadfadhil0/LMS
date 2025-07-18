# Learning Education System (LMS)

Sistem Manajemen Belajar (LMS) yang dirancang khusus untuk mendukung kegiatan belajar mengajar . Platform ini menyediakan berbagai fitur untuk memfasilitasi interaksi antara guru, siswa, dan administrator dalam lingkungan pembelajaran digital.

## Fitur Utama

| Role              | Fitur                                                                                                                                                                                                                                                          |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Siswa**         | • Akses materi pembelajaran<br>• Pengumpulan tugas online<br>• Forum diskusi kelas<br>• Lihat nilai dan progress belajar<br>• Jadwal pelajaran dan ujian<br>• Evaluasi Ujian dengan AI<br>• Fitur AI Dasar                                                     |
| **Guru**          | • Upload dan kelola materi pembelajaran<br>• Buat dan kelola tugas/kuis<br>• Manajemen kelas<br>• Laporan kemajuan siswa<br>• Evaluasi Ujian dengan AI<br>• Pengelolaan ujian siswa dengan AI<br>• Pengelolaan Kelas dengan AI<br>• Fitur AI yang ditingkatkan |
| **Administrator** | • Manajemen user (siswa, guru, admin)<br>• Pengaturan sistem sekolah<br>• Dashboard dan statistik<br>• Konfigurasi sistem                                                                                                                                      |

## Artificial Intelegence

Artificial Intelegence yang telah di atur sehingga dapat membantu guru dalam membuat soal, evaluasi hasil ujian secara umum maupun siswa, evaluasi hasil ujian siswa, dan dapat dipersonalisasikan sesuai dengan kebutuhan sekolah melalui admin. Saat ini untuk AI sendiri ditenagai oleh Groq AI dengan berbagai macam model yang digunakan sesuai dengan kebutuhan.

## Otorisasi

Sistem menggunakan role-based access control dengan 3 level akses:

- **Student**: Akses terbatas ke materi, tugas kelas, dan juga ujian
- **Teacher**: Akses penuh ke kelas yang diampu, dan ujian
- **Admin**: Akses penuh ke seluruh sistem, termasuk pada modifikasi akses database, dan AI.

## Instalasi

### 1. Clone Repository

```bash
git clone https://github.com/username/smagaedu.com.git
cd smagaedu.com
```

### 2. Setup Project

1. **Pindahkan folder main ke root project**
   - Copy semua isi folder `main/` ke dalam root project atau folder `htdocs` (untuk XAMPP/WAMP)

### 3. Konfigurasi API Key

API Key yang dimaksud digunakan untuk fitur AI yang akan mengakses user dalam mengakses LMS, saat ini API yang digunakan menggunakan Groq API, namun Anda dapat mengkostumisasi sesuai dengan prefensi Anda

1. **Generate API Key dari Groq**

   - Daftar di [Groq Console](https://console.groq.com)
   - Buat API key baru

   2. **Update file konfigurasi**

      **File: `generate_multiple_soal.php`**

      ```php
      // Setup API Groq
      $apiKey = 'YOUR_API_KEY';  // Ganti dengan API key Anda
      $url = 'https://api.groq.com/openai/v1/chat/completions';
      $soal_generated = [];
      ```

      **File: `buat_soal.php`**

      ```php
      const GROQ_API_KEY = 'YOUR_API_KEY'; // Ganti dengan API key Anda
      ```

      **File: `groq_config_ujian.php`**

      ```php
      // Konfigurasi Groq API
      define('GROQ_API_KEY', 'YOUR_API_KEY'); // Ganti dengan API key Groq Anda
      define('GROQ_MODEL', 'llama-3.3-70b-versatile'); // Model yang akan digunakan
      define('GROQ_API_URL', 'https://api.groq.com/openai/v1/chat/completions');
      ```

      **File: `detail_jawaban.php`**

      ```php
      // API Key Groq - ganti dengan API key Anda
      const GROQ_API_KEY = 'YOUR_API_KEY'; // Ganti dengan API key Groq Anda
      ```

      **File: `profil.php`**

      ```php
      $groq_api_key = 'YOUR_API_KEY';
      $should_analyze = isset($_POST['start_analysis']) && $_POST['start_analysis'] === 'true';

      ```

      **File: `ai_process.php`**

      ```php
      // Grog AI API configuration
      $api_key = 'YOUR_API_KEY'; // Ganti dengan API key Groq Anda
      $api_url = 'https://api.groq.com/openai/v1/chat/completions';

      ```

      **File: `semantic_search.php`**

      ```php
      function generateEmbedding($text) {
      // Panggil API embedding (contoh menggunakan OpenAI)
      $apiKey = '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';
      $url = 'https://api.groq.com/openai/v1/chat/completions';
      ...
      }


      ```

      - Ganti variabel API key Groq sesuai dengan API Groq milik Anda
      - Pastikan semua endpoint menggunakan Groq API

### 4. Setup Database

1. **Import database**

   - Buka phpMyAdmin atau MySQL client
   - Import file database yang tersedia di folder `database/`

2. **Konfigurasi koneksi database**
   - Update credentials database di file konfigurasi
   - Test koneksi database

### 5. Menjalankan Aplikasi

- Akses melalui browser: `http://localhost/smagaedu` (sesuaikan dengan nama folder)
- Login menggunakan akun yang tersedia di database

## Pengembang

Saat ini SMAGAEdu di dikembangkan dan dikelola oleh Muhammad Fadhil Manfa selaku pengembang utama LMS.
