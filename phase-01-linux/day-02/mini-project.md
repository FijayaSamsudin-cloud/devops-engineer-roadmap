# Eksplorasi dan Dokumentasi Filesystem Linux Berdasarkan Filesystem Hierarchy Standard (FHS)

> **Phase:** Linux Foundation  
> **Week:** 1  
> **Day:** 2  
> **Project Type:** Mini Project  
> **Author:** Fijaya Samsudin

---

# Pendahuluan

Filesystem merupakan salah satu komponen paling penting dalam sistem operasi Linux. Seluruh konfigurasi sistem, aplikasi, data pengguna, log, hingga informasi kernel diorganisasikan menggunakan struktur direktori yang mengikuti **Filesystem Hierarchy Standard (FHS)**.

Sebagai Linux Administrator, Cloud Engineer, DevOps Engineer, maupun Site Reliability Engineer (SRE), memahami struktur filesystem Linux merupakan kemampuan dasar yang wajib dimiliki karena hampir seluruh aktivitas administrasi sistem melibatkan direktori-direktori utama Linux.

Mini Project ini bertujuan untuk mendokumentasikan struktur filesystem Linux berdasarkan standar FHS serta menjelaskan fungsi setiap direktori utama beserta penerapannya dalam lingkungan enterprise.

---

# Tujuan

Mini Project ini dibuat untuk:

- Memahami konsep Filesystem Linux.
- Memahami Filesystem Hierarchy Standard (FHS).
- Menjelaskan fungsi setiap direktori utama Linux.
- Memahami perbedaan Absolute Path dan Relative Path.
- Mengenal Virtual Filesystem (`/proc` dan `/sys`).
- Membuat dokumentasi teknis yang layak dipublikasikan di GitHub Portfolio.

---

# Environment

| Item | Value |
|------|-------|
| Cloud Provider | AWS |
| Service | EC2 |
| Operating System | Ubuntu Server 24.04.4 LTS |
| Kernel | Linux 6.17.0-1017-aws |
| Shell | Bash |
| User | ubuntu |

---

# Apa itu Filesystem?

Filesystem adalah mekanisme yang digunakan sistem operasi untuk mengorganisasi, menyimpan, memberi nama, dan mengakses data pada media penyimpanan seperti HDD, SSD, maupun NVMe.

Filesystem tidak hanya menyimpan file, tetapi juga mengatur:

- Struktur direktori
- Metadata file
- Permission
- Ownership
- Lokasi penyimpanan data

Tanpa filesystem, sistem operasi tidak akan mengetahui lokasi suatu file maupun bagaimana file tersebut harus diakses.

---

# Filesystem Hierarchy Standard (FHS)

Filesystem Hierarchy Standard (FHS) merupakan standar yang menentukan lokasi penyimpanan file dan direktori pada sistem Linux.

Dengan adanya FHS, administrator dapat berpindah antar distribusi Linux seperti Ubuntu, Debian, Rocky Linux, maupun RHEL tanpa harus mempelajari ulang lokasi file sistem.

Keuntungan FHS:

- Konsisten antar distribusi Linux
- Mempermudah administrasi server
- Mempermudah troubleshooting
- Mempermudah otomatisasi (Automation)
- Mempermudah deployment aplikasi

---

# Struktur Filesystem Linux

```text
/
├── boot
├── dev
├── etc
├── home
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sys
├── tmp
├── usr
└── var
```

---

# Analisis Direktori Utama

## Root Directory (/)

Merupakan direktori paling atas pada Linux.

Semua direktori lain berada di bawah Root Directory.

Contoh:

```text
/etc
/home
/usr
/var
```

---

## /etc

Berisi seluruh konfigurasi sistem Linux.

Contoh:

```text
/etc/passwd
/etc/group
/etc/hosts
/etc/fstab
/etc/ssh/
```

Digunakan administrator ketika melakukan konfigurasi server maupun troubleshooting.

---

## /home

Home Directory untuk user biasa.

Contoh:

```text
/home/ubuntu
/home/alice
/home/bob
```

Berisi:

- Project
- Source Code
- Script
- Dokumen
- File pribadi

---

## /root

Home Directory milik user root.

Berbeda dengan Root Directory (`/`).

Digunakan administrator sistem ketika login sebagai root.

---

## /var

Menyimpan data yang berubah selama sistem berjalan.

Subdirektori penting:

```text
/var/log
/var/cache
/var/lib
/var/spool
```

Direktori ini sering dipisahkan menjadi volume tersendiri pada server production karena ukuran log dan data aplikasi dapat bertambah dengan cepat.

---

## /usr

Menyimpan executable, library, dokumentasi, dan aplikasi bawaan sistem.

Contoh:

```text
/usr/bin
/usr/lib
/usr/share
/usr/local
```

---

## /opt

Digunakan untuk software tambahan dari pihak ketiga.

Contoh:

```text
/opt/google
/opt/oracle
```

---

## /tmp

Digunakan untuk file sementara.

Sebagian distribusi Linux akan menghapus isi direktori ini secara otomatis ketika reboot.

Tidak disarankan menyimpan data penting pada direktori ini.

---

## /boot

Menyimpan file yang diperlukan ketika proses booting.

Contoh:

- Kernel Linux
- GRUB Bootloader
- initramfs

Tanpa direktori ini sistem tidak dapat melakukan boot dengan benar.

---

## /dev

Berisi representasi perangkat keras dalam bentuk file.

Contoh:

```text
/dev/sda
/dev/null
/dev/tty
```

---

## /proc

Merupakan Virtual Filesystem.

Direktori ini tidak berada pada media penyimpanan, melainkan dibuat secara dinamis oleh Linux Kernel.

Contoh:

```text
/proc/cpuinfo
/proc/meminfo
```

---

## /sys

Merupakan Virtual Filesystem yang menyediakan informasi mengenai perangkat keras dan driver Linux.

Contoh:

```text
/sys/class
/sys/block
/sys/devices
```

---

# Absolute Path vs Relative Path

## Absolute Path

Selalu dimulai dari Root Directory (`/`).

Contoh:

```text
/home/ubuntu/project/file.txt
```

Keunggulan:

- Tidak bergantung pada lokasi direktori saat ini.
- Sangat cocok digunakan pada script otomatisasi.

---

## Relative Path

Bergantung pada posisi direktori kerja saat ini.

Misalnya:

```text
cd lab/day02
```

atau

```text
cd ../..
```

Relative Path lebih singkat, tetapi kurang cocok digunakan pada automation jika posisi direktori dapat berubah.

---

# Diagram ASCII

```text
                               /
                               │
 ┌──────────────┬──────────────┼──────────────┬──────────────┐
 │              │              │              │              │
etc           home           root           var            usr
 │              │              │              │              │
Config      User Data     Root Home     Logs/Data     Programs
 │                                           │
 │                                     ┌─────┴─────┐
 │                                     │           │
 │                                   log        lib
 │
 ├──────────────────────────────────────────────────────┐
 │                                                      │
boot        dev         proc         sys        opt      tmp
 │           │           │            │          │        │
Boot      Devices    Runtime      Hardware   Optional  Temp Files
Files                  Info         Model    Software
```

---

# Screenshot Hasil Praktikum

## Screenshot 1

Root Directory dan Direktori `/etc`

![Screenshot 1](assets/screenshots/screenshot-01-root-and-etc.png)

---

## Screenshot 2

Home Directory, `/var/log`, `/usr/bin/bash`, dan `/opt`

![Screenshot 2](assets/screenshots/screenshot-02-home-varlog-bash-opt.png)

---

## Screenshot 3

Pembuatan Direktori, Relative Path, dan `/proc/cpuinfo`

![Screenshot 3](assets/screenshots/screenshot-03-directory-and-cpuinfo.png)

---

## Screenshot 4

`/proc/meminfo` dan `/sys/class`

![Screenshot 4](assets/screenshots/screenshot-04-meminfo-and-sys.png)

---

# Enterprise Relevance

Pada lingkungan enterprise, pemahaman terhadap Filesystem Linux sangat penting karena:

- Konfigurasi sistem berada di `/etc`.
- Log aplikasi dan sistem berada di `/var/log`.
- Data aplikasi sering berada di `/var/lib`.
- Program sistem berada di `/usr`.
- Software pihak ketiga ditempatkan pada `/opt`.
- Monitoring tools membaca informasi dari `/proc` dan `/sys`.

Cloud Engineer maupun DevOps Engineer menggunakan pemahaman ini ketika melakukan deployment, monitoring, troubleshooting, backup, hingga disaster recovery.

---

# Lessons Learned

Melalui Mini Project ini saya mempelajari bahwa:

- Linux menggunakan struktur filesystem yang terstandarisasi melalui FHS.
- Setiap direktori memiliki fungsi yang spesifik.
- Absolute Path lebih aman digunakan pada automation.
- Relative Path lebih praktis untuk navigasi sehari-hari.
- Virtual Filesystem seperti `/proc` dan `/sys` menyediakan informasi sistem secara real-time.
- Pemahaman Filesystem menjadi fondasi penting sebelum mempelajari Linux Administration, Docker, Kubernetes, maupun Cloud Computing.

---

# Kesimpulan

Filesystem Linux merupakan fondasi utama dalam administrasi sistem. Dengan memahami Filesystem Hierarchy Standard (FHS), administrator dapat mengetahui lokasi konfigurasi, executable, log, data aplikasi, hingga informasi kernel secara konsisten pada berbagai distribusi Linux.

Mini Project ini memberikan pemahaman mengenai fungsi setiap direktori utama, konsep Virtual Filesystem, penggunaan Absolute Path dan Relative Path, serta relevansinya dalam lingkungan enterprise. Pengetahuan ini menjadi dasar yang sangat penting untuk melanjutkan pembelajaran ke Linux Administration, Cloud Computing, DevOps, dan Site Reliability Engineering (SRE).

---

# Referensi

- Linux Foundation — Filesystem Hierarchy Standard (FHS)
- Ubuntu Server Documentation
- Linux Kernel Documentation
- GNU Core Utilities Manual