# Challenge Lab - Hari 1
# Pengenalan Linux

## Tujuan

Melakukan investigasi terhadap sistem Linux yang digunakan untuk memahami identitas sistem, Distribution, Kernel, Shell, serta hubungan antara Terminal, Application, Shell, Kernel, dan Hardware sebagai fondasi sebelum mempelajari administrasi server, cloud computing, dan DevOps.

---

# 1. Identifikasi Distribution Linux

## Hasil Investigasi

| Informasi | Nilai |
|-----------|--------|
| Distribution | Ubuntu |
| Versi | Ubuntu 24.04.4 LTS |
| Codename | Noble Numbat |
| Family | Debian |

### Analisis

Berdasarkan hasil pemeriksaan file `/etc/os-release`, sistem operasi yang digunakan adalah **Ubuntu Server 24.04.4 LTS (Long Term Support)** dengan codename **Noble Numbat**.

Ubuntu merupakan distribusi Linux yang berasal dari Debian dan banyak digunakan pada server, cloud computing, DevOps, serta lingkungan enterprise karena stabil, mudah digunakan, memiliki siklus rilis LTS, dan didukung oleh komunitas yang sangat besar.

### Enterprise Relevance

Mengetahui Distribution Linux merupakan langkah awal yang dilakukan administrator sebelum melakukan instalasi software, troubleshooting, maupun deployment aplikasi karena setiap distribution memiliki package manager, struktur paket, dan kebijakan update yang berbeda.

---

# 2. Identifikasi Linux Kernel

## Hasil Investigasi

```text
6.17.0-1017-aws
```

### Analisis

Kernel yang digunakan adalah **Linux Kernel versi 6.17.0-1017-aws**.

Suffix **-aws** menunjukkan bahwa sistem menggunakan varian kernel Ubuntu yang disediakan oleh Canonical dan dikonfigurasi untuk berjalan secara optimal pada lingkungan Amazon Web Services (AWS), khususnya Amazon EC2.

Kernel ini tetap merupakan Linux Kernel, namun memiliki konfigurasi dan optimasi yang sesuai dengan kebutuhan virtualisasi serta perangkat keras virtual pada platform AWS.

### Enterprise Relevance

Mengetahui versi kernel sangat penting untuk:

- Memastikan kompatibilitas aplikasi.
- Menentukan security patch yang sesuai.
- Troubleshooting masalah sistem.
- Audit infrastruktur.
- Validasi sebelum melakukan upgrade kernel.

---

# 3. Identifikasi Shell

## Hasil Investigasi

```text
/bin/bash
```

### Analisis

Shell yang digunakan adalah **Bash (Bourne Again SHell)**.

Bash merupakan shell bawaan (default shell) pada Ubuntu Server dan menjadi salah satu shell yang paling banyak digunakan oleh Linux System Administrator, Cloud Engineer, DevOps Engineer, maupun Site Reliability Engineer (SRE).

Bash mendukung scripting sehingga sangat cocok untuk melakukan otomatisasi administrasi server.

### Mengapa Bash Banyak Digunakan?

- Stabil dan telah digunakan selama bertahun-tahun.
- Tersedia secara default pada sebagian besar distribusi Linux.
- Memiliki dokumentasi yang sangat lengkap.
- Didukung oleh hampir semua tools DevOps seperti Git, Docker, Kubernetes, Terraform, dan AWS CLI.
- Sangat cocok untuk membangun automation script.

---

# 4. Lokasi Executable Bash

## Hasil Investigasi

```text
/usr/bin/bash
```

### Analisis

Lokasi executable Bash berada pada direktori:

```text
/usr/bin/bash
```

Informasi ini diperoleh menggunakan perintah:

```bash
which bash
```

Perintah `which` digunakan untuk mencari lokasi executable berdasarkan variabel environment `PATH`.

Perlu diperhatikan bahwa hasil dari perintah `which` dapat berbeda pada setiap distribusi Linux maupun konfigurasi sistem karena bergantung pada isi variabel `PATH`.

---

# 5. Informasi Sistem Lengkap

## Hasil Investigasi

```text
Linux ip-172-31-32-152
6.17.0-1017-aws
x86_64 GNU/Linux
```

### Analisis

Berdasarkan hasil perintah `uname -a`, diperoleh informasi bahwa:

- Hostname server adalah `ip-172-31-32-152`.
- Sistem menggunakan Linux Kernel versi `6.17.0-1017-aws`.
- Arsitektur prosesor adalah **x86_64 (64-bit)**.
- Sistem berjalan menggunakan GNU/Linux.

### Enterprise Relevance

Dalam lingkungan enterprise, informasi dari `uname -a` sering digunakan untuk:

- Troubleshooting server.
- Membuka tiket support.
- Memastikan arsitektur CPU sebelum instalasi software.
- Memverifikasi kompatibilitas binary.
- Dokumentasi inventaris server.

---

# 6. Working Directory

## Hasil Investigasi

```text
/home/ubuntu
```

### Analisis

Direktori kerja saat ini berada pada:

```text
/home/ubuntu
```

Direktori tersebut merupakan **Home Directory** milik user `ubuntu`.

Sebagian besar file konfigurasi, script, dan data pribadi pengguna akan disimpan di dalam direktori ini.

### Enterprise Relevance

Mengetahui lokasi direktori kerja sangat penting agar administrator tidak menjalankan perintah pada direktori yang salah, terutama ketika melakukan deployment, backup, maupun otomatisasi menggunakan Bash Script.

---

# 7. Perbedaan Terminal dan Shell

Terminal adalah aplikasi yang menyediakan antarmuka berbasis teks bagi pengguna untuk berinteraksi dengan sistem operasi.

Shell adalah program yang berjalan di dalam Terminal dan bertugas menerima perintah dari pengguna, menjalankan program, kemudian berkomunikasi dengan Linux Kernel melalui **System Call**.

Dengan kata lain:

- **Terminal** adalah aplikasi tempat pengguna bekerja.
- **Shell** adalah program yang menerima dan memproses perintah.
- **Kernel** adalah inti sistem operasi yang mengelola seluruh sumber daya perangkat keras.

Ketiga komponen tersebut memiliki fungsi yang berbeda namun saling melengkapi.

---

# 8. Diagram Hubungan Komponen Linux

```text
                User
                  │
                  ▼
        Terminal Emulator
                  │
                  ▼
            Bash Shell
                  │
                  ▼
 Application (ls, pwd, cat, bash)
                  │
             System Call
                  │
                  ▼
            Linux Kernel
      ┌──────────┼──────────┐
      │          │          │
 Process     Memory     Network
 Manager     Manager      Stack
      │          │          │
      └──────────┼──────────┘
                  ▼
               Hardware
```

---

# 9. Operational Relevance

Mengidentifikasi informasi dasar sistem merupakan salah satu langkah pertama yang dilakukan oleh Linux Administrator maupun Cloud Engineer sebelum melakukan konfigurasi atau troubleshooting server.

Informasi seperti Distribution Linux, versi Kernel, Shell, dan arsitektur sistem digunakan untuk:

- Memastikan kompatibilitas aplikasi.
- Menentukan prosedur instalasi software.
- Melakukan audit sistem.
- Menentukan security patch.
- Membantu proses troubleshooting.
- Menyusun dokumentasi infrastruktur.

Di lingkungan cloud seperti AWS, Azure, maupun Google Cloud, proses identifikasi sistem merupakan aktivitas rutin sebelum melakukan deployment maupun maintenance server.

---

# 10. Lessons Learned

Melalui Challenge Lab ini saya memahami bahwa Linux terdiri dari beberapa komponen penting yang bekerja secara bersama, yaitu Terminal, Shell, Application, Kernel, dan Hardware.

Saya juga memahami bahwa setiap perintah Linux yang dijalankan tidak langsung berinteraksi dengan perangkat keras, melainkan diproses melalui Shell, diteruskan ke Kernel menggunakan System Call, kemudian Kernel mengelola akses terhadap hardware.

Selain memahami cara menjalankan perintah Linux, saya mulai memahami mengapa informasi tersebut sangat penting dalam operasional server, troubleshooting, dan administrasi infrastruktur cloud.

---

# Kesimpulan

Berdasarkan hasil investigasi, server yang digunakan menjalankan **Ubuntu Server 24.04.4 LTS (Noble Numbat)** dengan **Linux Kernel 6.17.0-1017-aws** yang dikonfigurasi untuk berjalan secara optimal pada lingkungan Amazon EC2.

Shell yang digunakan adalah **Bash**, sedangkan executable Bash berada pada direktori `/usr/bin/bash`. Direktori kerja pengguna saat ini berada di `/home/ubuntu`, yang merupakan home directory milik user `ubuntu`.

Melalui Challenge Lab ini saya memahami bahwa Terminal, Shell, Application, dan Kernel memiliki peran yang berbeda namun saling berhubungan dalam menjalankan setiap perintah Linux. Saya juga memahami bahwa proses identifikasi sistem merupakan langkah awal yang penting sebelum melakukan konfigurasi, deployment, troubleshooting, maupun administrasi server.

Sebagai calon Cloud Engineer dan DevOps Engineer, saya menyadari bahwa pemahaman terhadap Distribution, Kernel, Shell, dan struktur dasar Linux merupakan fondasi penting sebelum mempelajari teknologi lanjutan seperti AWS, Docker, Terraform, Ansible, Kubernetes, maupun DevSecOps.

---

# Status Challenge

- [x] Distribution berhasil diidentifikasi.
- [x] Kernel berhasil diidentifikasi.
- [x] Shell berhasil diidentifikasi.
- [x] Lokasi Bash berhasil ditemukan.
- [x] Informasi sistem berhasil dianalisis.
- [x] Perbedaan Terminal dan Shell dipahami.
- [x] Diagram hubungan komponen Linux dibuat.
- [x] Enterprise Relevance dijelaskan.
- [x] Lessons Learned ditulis.
- [x] Challenge Lab selesai.