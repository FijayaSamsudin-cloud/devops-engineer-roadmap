# Hands-on Lab - Hari 2
# Linux Filesystem (Filesystem Hierarchy Standard - FHS)

> **Phase:** Linux Foundation  
> **Week:** 1  
> **Day:** 2  
> **Module:** Linux Filesystem  
> **Author:** Fijaya Samsudin  
> **Environment:** AWS EC2 Ubuntu Server 24.04.4 LTS

---

# Tujuan

Pada praktikum ini saya melakukan eksplorasi terhadap struktur filesystem Linux berdasarkan **Filesystem Hierarchy Standard (FHS)**.

Praktikum bertujuan untuk:

- Memahami struktur direktori utama Linux.
- Mengenali fungsi setiap direktori.
- Mempraktikkan penggunaan Absolute Path dan Relative Path.
- Mengenali Virtual Filesystem (`/proc` dan `/sys`).
- Membiasakan penggunaan command line sebagai Linux Administrator.

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

# Daftar Praktikum

- Root Directory (`/`)
- `/etc`
- Home Directory
- `/var/log`
- `/usr/bin/bash`
- `/opt`
- Membuat Direktori
- Relative Path
- `/proc/cpuinfo`
- `/proc/meminfo`
- `/sys/class`

---

# Praktikum 1 — Menampilkan Root Directory

## Tujuan

Melihat struktur direktori paling atas pada Linux.

## Command

```bash
ls /
```

## Penjelasan

Perintah `ls /` digunakan untuk menampilkan seluruh direktori yang berada pada Root Directory (`/`).

Seluruh filesystem Linux dimulai dari direktori ini sesuai standar **Filesystem Hierarchy Standard (FHS).**

## Hasil

Output menampilkan direktori seperti:

- /etc
- /home
- /root
- /usr
- /var
- /boot
- /proc
- /sys
- /dev

## Analisis

Seluruh direktori utama Linux berhasil ditampilkan.

Ini menunjukkan bahwa Ubuntu mengikuti standar FHS sehingga lokasi file sistem menjadi konsisten di berbagai distribusi Linux.

---

# Praktikum 2 — Eksplorasi Direktori /etc

## Command

```bash
cd /etc
ls
```

## Tujuan

Melihat file konfigurasi sistem Linux.

## Analisis

Direktori `/etc` berisi file konfigurasi penting seperti:

| File | Fungsi |
|------|---------|
| passwd | Informasi user |
| group | Informasi group |
| hostname | Nama host |
| hosts | Local DNS |
| fstab | Mount filesystem |
| ssh | Konfigurasi OpenSSH |

Direktori ini merupakan salah satu lokasi yang paling sering digunakan administrator Linux ketika melakukan konfigurasi server.

---

# Praktikum 3 — Home Directory

## Command

```bash
cd ~
pwd
ls -la
```

## Hasil

Direktori aktif:

```text
/home/ubuntu
```

## Analisis

Simbol `~` mengarah ke Home Directory user yang sedang login.

Home Directory digunakan untuk menyimpan:

- Project
- Source Code
- Script
- Konfigurasi User
- Dokumen

---

# Praktikum 4 — Melihat Log Sistem

## Command

```bash
ls /var/log
```

## Analisis

Direktori `/var/log` berisi log sistem seperti:

- auth.log
- syslog
- kern.log
- journal
- apt

Log digunakan administrator ketika melakukan troubleshooting server.

Pada lingkungan production, direktori ini merupakan lokasi yang hampir selalu diperiksa ketika terjadi gangguan layanan.

---

# Praktikum 5 — Melihat Lokasi Bash

## Command

```bash
ls -l /usr/bin/bash
```

## Analisis

Executable Bash berada di:

```text
/usr/bin/bash
```

Permission:

```text
-rwxr-xr-x
```

Artinya:

- Owner → Read, Write, Execute
- Group → Read, Execute
- Others → Read, Execute

---

# Praktikum 6 — Eksplorasi Direktori /opt

## Command

```bash
ls /opt
```

## Analisis

Direktori `/opt` masih kosong.

Hal ini normal karena server Ubuntu yang digunakan masih merupakan instalasi baru dan belum memiliki aplikasi pihak ketiga.

---

# Praktikum 7 — Membuat Direktori

## Command

```bash
mkdir -p ~/lab/day02
```

## Verifikasi

```bash
ls -la
```

## Analisis

Perintah berhasil membuat struktur direktori:

```text
lab/
└── day02/
```

Option `-p` memungkinkan parent directory dibuat secara otomatis apabila belum tersedia.

---

# Praktikum 8 — Relative Path

## Command

```bash
cd lab/day02
pwd
```

Kemudian:

```bash
cd ../..
pwd
```

## Analisis

Praktikum ini menunjukkan penggunaan Relative Path.

Simbol:

- `.` → Direktori saat ini
- `..` → Direktori induk

Relative Path bergantung pada posisi direktori aktif.

---

# Praktikum 9 — Informasi CPU

## Command

```bash
head -20 /proc/cpuinfo
```

## Analisis

File `/proc/cpuinfo` menampilkan informasi CPU secara langsung dari Linux Kernel.

Informasi meliputi:

- Vendor CPU
- Model CPU
- Cache
- Core
- Flags CPU

---

# Praktikum 10 — Informasi Memory

## Command

```bash
head -20 /proc/meminfo
```

## Analisis

File ini menampilkan penggunaan memori secara real-time.

Informasi meliputi:

- Total Memory
- Free Memory
- Cached Memory
- Available Memory
- Swap

Monitoring tools seperti Prometheus dan Node Exporter memanfaatkan informasi ini.

---

# Praktikum 11 — Eksplorasi /sys

## Command

```bash
ls /sys/class
```

## Analisis

Direktori `/sys` merupakan Virtual Filesystem yang menyediakan informasi perangkat keras.

Direktori ini berisi informasi mengenai:

- Block Device
- Network Interface
- USB
- Power Supply
- Storage
- Thermal

---

# Screenshot

## Screenshot 1

**Root Directory dan Direktori `/etc`**


![Hands-on Lab Hari 2](./assets/screenshots/screenshot-01-root-and-etc.png)

---

## Screenshot 2

**Home Directory, `/var/log`, `/usr/bin/bash`, dan `/opt`**

![Hands-on Lab Hari 2](assets/screenshots/screenshot-02-home-varlog-bash-opt.png)

---

## Screenshot 3

**Pembuatan Direktori, Relative Path, dan `/proc/cpuinfo`**

![Hands-on Lab Hari 2](assets/screenshots/screenshot-03-directory-and-cpuinfo.png)

---

## Screenshot 4

**`/proc/meminfo` dan `/sys/class`**

![Hands-on Lab Hari 2](assets/screenshots/screenshot-04-meminfo-and-sys.png)

---

# Lessons Learned

Melalui praktikum ini saya memahami bahwa:

- Linux menggunakan Filesystem Hierarchy Standard (FHS).
- Seluruh direktori berada di bawah Root Directory (`/`).
- `/etc` menyimpan konfigurasi sistem.
- `/var/log` menyimpan log sistem.
- `/usr` menyimpan executable aplikasi.
- `/opt` digunakan untuk aplikasi tambahan.
- `/proc` dan `/sys` merupakan Virtual Filesystem.
- Absolute Path dan Relative Path memiliki fungsi yang berbeda.

---

# Enterprise Relevance

Pemahaman Filesystem Linux merupakan keterampilan dasar yang wajib dimiliki oleh:

- Linux System Administrator
- Cloud Engineer
- DevOps Engineer
- Platform Engineer
- Site Reliability Engineer (SRE)

Dalam lingkungan production, engineer harus mengetahui lokasi file konfigurasi, executable, log, data aplikasi, dan virtual filesystem untuk mempercepat proses troubleshooting, deployment, monitoring, serta maintenance server.

---

# Kesimpulan

Praktikum ini berhasil memperkenalkan struktur filesystem Linux sesuai standar Filesystem Hierarchy Standard (FHS). Melalui eksplorasi direktori utama seperti `/etc`, `/home`, `/var`, `/usr`, `/opt`, `/proc`, dan `/sys`, saya memperoleh pemahaman mengenai fungsi masing-masing direktori serta penerapannya dalam administrasi sistem.

Selain itu, praktikum ini juga memperkuat pemahaman mengenai penggunaan Absolute Path dan Relative Path serta konsep Virtual Filesystem yang menjadi dasar sebelum mempelajari Linux Administration, Cloud Computing, Docker, Kubernetes, dan DevOps.

---

# Referensi

- Linux Foundation — Filesystem Hierarchy Standard (FHS)
- Ubuntu Server Documentation
- Linux Kernel Documentation
- GNU Core Utilities Manual