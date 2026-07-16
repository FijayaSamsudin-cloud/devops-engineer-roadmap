# Mini Project - Hari 1
# Mengenal Identitas Sistem Linux

## Informasi Project

| Informasi | Nilai |
|-----------|--------|
| Nama Project | Mengenal Identitas Sistem Linux |
| Fase | Foundation & Core Skills |
| Hari | 1 |
| Platform | Amazon Web Services (AWS) EC2 |
| Sistem Operasi | Ubuntu Server 24.04.4 LTS |
| Kernel | Linux 6.17.0-1017-aws |

---

# Pendahuluan

Linux merupakan sistem operasi yang mendominasi dunia server modern, cloud computing, container, DevOps, hingga supercomputer. Sebagian besar layanan cloud seperti Amazon Web Services (AWS), Google Cloud Platform (GCP), dan Microsoft Azure menjalankan workload di atas Linux karena stabil, aman, fleksibel, dan mudah diotomasi.

Sebelum mempelajari administrasi server, Docker, Kubernetes, Terraform, maupun layanan cloud, seorang Cloud Engineer harus mampu mengenali identitas sistem Linux yang sedang digunakan. Informasi seperti distribution, kernel, shell, dan struktur dasar sistem menjadi fondasi dalam melakukan instalasi software, konfigurasi layanan, troubleshooting, maupun otomatisasi.

Mini Project ini bertujuan untuk memahami identitas dasar sistem Linux melalui proses investigasi langsung pada sebuah server Ubuntu yang berjalan di lingkungan Amazon Web Services (AWS).

---

# Tujuan

Mini Project ini bertujuan untuk:

- Mengidentifikasi distribution Linux yang digunakan.
- Mengidentifikasi versi Linux Kernel.
- Mengetahui shell yang digunakan oleh sistem.
- Mengetahui lokasi executable Bash.
- Memahami perbedaan Terminal dan Shell.
- Memahami hubungan antara User, Application, Shell, Kernel, dan Hardware.
- Melatih penggunaan command dasar Linux.
- Membentuk pola pikir dasar seorang Linux System Administrator dan Cloud Engineer.

---

# Informasi Sistem

| Informasi | Nilai |
|-----------|--------|
| Distribution | Ubuntu Server 24.04.4 LTS |
| Codename | Noble Numbat |
| Family | Debian |
| Kernel | Linux 6.17.0-1017-aws |
| Shell | Bash |
| Bash Location | /usr/bin/bash |
| Working Directory | /home/ubuntu |

---

# Hasil Praktikum

## 1. Menampilkan Shell

```bash
echo $SHELL
```

Output

```text
/bin/bash
```

Shell yang digunakan adalah **Bash (Bourne Again SHell)**.

Bash merupakan shell default pada Ubuntu Server dan menjadi standar di sebagian besar server Linux karena stabil, memiliki kompatibilitas tinggi, mendukung scripting, serta hampir seluruh dokumentasi Linux dan DevOps menggunakan Bash sebagai contoh.

---

## 2. Menampilkan Kernel

```bash
uname -r
```

Output

```text
6.17.0-1017-aws
```

Kernel yang digunakan adalah Linux versi **6.17.0-1017-aws**.

Suffix **-aws** menunjukkan bahwa sistem menggunakan kernel Ubuntu yang dikonfigurasi oleh Canonical agar optimal dijalankan pada lingkungan Amazon Web Services (AWS).

---

## 3. Menampilkan Distribution

```bash
cat /etc/os-release
```

Output

```text
Ubuntu 24.04.4 LTS
```

Sistem operasi yang digunakan adalah **Ubuntu Server 24.04.4 LTS (Long Term Support)**.

Versi LTS dipilih karena mendapatkan pembaruan keamanan dalam jangka panjang sehingga lebih sesuai untuk server produksi.

---

## 4. Menampilkan Lokasi Bash

```bash
which bash
```

Output

```text
/usr/bin/bash
```

Lokasi executable Bash berada pada:

```text
/usr/bin/bash
```

Perintah `which` mencari executable berdasarkan variabel environment `PATH`, sehingga hasilnya dapat berbeda pada distribusi Linux atau konfigurasi sistem yang berbeda.

---

## 5. Menampilkan Working Directory

```bash
pwd
```

Output

```text
/home/ubuntu
```

Working Directory saat ini adalah direktori home milik pengguna `ubuntu`.

---

# Diagram Arsitektur Linux

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
      Application (ls, pwd, cat)
                   │
              System Call
                   │
                   ▼
             Linux Kernel
       ┌─────────┼─────────┐
       │         │         │
   Process    Memory    Network
   Manager    Manager     Stack
       │         │         │
       └─────────┼─────────┘
                 ▼
              Hardware
```

---

# Analisis

Berdasarkan hasil investigasi, server menggunakan **Ubuntu Server 24.04.4 LTS** dengan **Linux Kernel 6.17.0-1017-aws**. Shell yang digunakan adalah **Bash**, sedangkan executable Bash berada pada direktori `/usr/bin/bash`.

Informasi-informasi tersebut merupakan langkah awal yang hampir selalu dilakukan oleh seorang Linux Administrator ketika pertama kali memperoleh akses ke sebuah server. Dengan mengetahui distribution, kernel, shell, dan lingkungan sistem, administrator dapat menentukan dokumentasi yang tepat, memastikan kompatibilitas aplikasi, serta mempermudah proses troubleshooting.

Selain itu, saya memahami bahwa Shell tidak berkomunikasi langsung dengan hardware. Shell menjalankan suatu program (misalnya `ls`, `pwd`, atau `cat`), kemudian program tersebut menggunakan **system call** untuk meminta layanan kepada Linux Kernel. Kernel kemudian mengakses perangkat keras dan mengembalikan hasil kepada aplikasi.

---

# Enterprise Relevance

Dalam lingkungan enterprise, identitas sistem merupakan informasi yang sangat penting.

Sebelum melakukan deployment aplikasi, instalasi software, update sistem, maupun troubleshooting, seorang Cloud Engineer biasanya akan memeriksa:

- Distribution Linux
- Versi Kernel
- Arsitektur CPU
- Shell yang digunakan
- Hostname
- Versi sistem operasi

Informasi tersebut membantu engineer menentukan kompatibilitas software, memilih dokumentasi yang sesuai, mengidentifikasi potensi masalah, serta memastikan bahwa prosedur yang dilakukan sesuai dengan lingkungan server.

Karena alasan tersebut, proses identifikasi sistem hampir selalu menjadi langkah pertama dalam Standard Operating Procedure (SOP) administrasi server.

---

# Kesimpulan

Melalui Mini Project ini saya memahami bahwa Linux bukan hanya sebuah terminal, melainkan sebuah sistem operasi yang terdiri dari berbagai komponen yang bekerja sama, seperti Kernel, Shell, Distribution, aplikasi, dan hardware.

Saya juga memahami bahwa Kernel bertugas mengelola seluruh sumber daya perangkat keras, sedangkan Shell menjadi antarmuka utama bagi pengguna untuk menjalankan berbagai program. Program-program tersebut kemudian menggunakan system call agar dapat meminta layanan kepada Kernel secara aman.

Selain memahami konsep tersebut, saya berhasil mengidentifikasi bahwa server yang digunakan menjalankan Ubuntu Server 24.04.4 LTS dengan Linux Kernel 6.17.0-1017-aws yang dioptimalkan untuk lingkungan Amazon Web Services (AWS).

Pengetahuan dasar ini menjadi fondasi penting sebelum mempelajari administrasi Linux, Cloud Computing, Docker, Kubernetes, Terraform, CI/CD, maupun DevOps.

---

# Lessons Learned

Dari Mini Project ini saya memperoleh beberapa pemahaman penting:

- Linux terdiri dari berbagai komponen yang saling bekerja sama.
- Kernel merupakan inti sistem operasi yang mengelola seluruh sumber daya hardware.
- Shell berbeda dengan Terminal.
- Bash menjadi shell standar karena stabil, kompatibel, dan mendukung otomatisasi.
- Ubuntu merupakan distribution berbasis Debian yang banyak digunakan pada lingkungan cloud.
- Informasi identitas sistem merupakan langkah awal sebelum melakukan administrasi server.
- Perintah sederhana seperti `uname`, `cat`, `which`, `echo`, dan `pwd` memiliki peran penting dalam proses troubleshooting.

---

# Referensi

- Linux Kernel Documentation
- GNU Project Documentation
- Ubuntu Server Documentation
- Debian Documentation