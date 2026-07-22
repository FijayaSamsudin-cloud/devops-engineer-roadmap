# Day 05 — Linux Process Management

> Phase 01 — Linux Foundation

Pada pembelajaran **Day 05** saya mempelajari konsep **Linux Process Management** dan **Linux Service Management** menggunakan **Ubuntu Server 24.04.4 LTS** yang berjalan pada **AWS EC2**.

Fokus pembelajaran hari ini adalah memahami bagaimana Linux mengelola process dan service, melakukan monitoring resource server, membaca system log menggunakan **journalctl**, serta melakukan investigasi dan troubleshooting dasar yang umum dilakukan oleh seorang **Linux Administrator** pada lingkungan production.

Selain mempelajari penggunaan berbagai utilitas Linux, saya juga mendokumentasikan proses investigasi dan audit server menggunakan pendekatan yang menyerupai workflow di lingkungan enterprise.

---

# Learning Objectives

Setelah menyelesaikan Day 05 saya memahami:

- Linux Process
- Process Lifecycle
- Parent Process & Child Process
- Process Monitoring
- Process Tree
- Process Search
- Linux Job Control
- Linux Signals
- Process Termination
- Linux Service Management
- systemd
- journalctl
- Basic Linux Troubleshooting
- Enterprise Server Investigation
- Basic Server Health Audit

---

# Environment

| Item | Value |
|------|-------|
| Platform | AWS EC2 |
| Operating System | Ubuntu Server 24.04.4 LTS |
| Kernel | Linux 6.17.0-1019-aws |
| Shell | Bash |
| Init System | systemd 255 |

---

# Repository Structure

```text
day-05/
│
├── README.md
├── hands-on-lab.md
├── challenge-lab.md
├── mini-project.md
│
└── assets/
    └── screenshots/
        ├── hands-on-lab/
        ├── challenge/
        └── mini-project/
```

---

# Progress

| Activity | Status |
|----------|--------|
| Hands-on Lab | ✅ Completed |
| Challenge Lab | ✅ Completed |
| Mini Project | ✅ Completed |

---

# Hands-on Lab

Hands-on Lab terdiri dari serangkaian praktikum untuk memahami cara kerja Linux Process Management dan Linux Service Management.

Materi yang dipraktikkan meliputi:

- Environment Verification
- Process Monitoring
- Process Tree
- Process Search
- Job Control
- Background Process
- Linux Signal Handling
- Process Termination
- Service Management
- Journal Investigation

📄 Dokumentasi lengkap tersedia pada:

```text
hands-on-lab.md
```

---

# Challenge Lab

Challenge Lab menggunakan pendekatan **Enterprise Ticket Simulation**, di mana setiap challenge mensimulasikan tiket operasional yang biasa diterima oleh seorang **Junior Linux Administrator**.

Challenge yang diselesaikan meliputi:

- SSH Service Investigation
- Resource Health Investigation
- Background Process Investigation
- Linux Signal Investigation
- Service Health Check
- Journal Investigation
- Production Troubleshooting

Melalui Challenge Lab ini saya berlatih melakukan investigasi secara sistematis sebelum mengambil tindakan terhadap server.

📄 Dokumentasi lengkap tersedia pada:

```text
challenge-lab.md
```

---

# Mini Project

Mini Project menggabungkan seluruh materi Day 05 ke dalam sebuah simulasi pekerjaan nyata sebagai **Junior Linux Administrator**.

Project yang dikerjakan berupa:

> **Enterprise Linux Server Health Audit Report**

Audit dilakukan terhadap server Ubuntu Server 24.04.4 LTS pada AWS EC2 dengan tahapan:

- Environment Assessment
- Process Inventory
- Resource Health Assessment
- Service Health Audit
- Journal Audit
- Final Enterprise Server Health Report

Output akhir berupa laporan teknis yang berisi hasil audit server, temuan utama, analisis kondisi sistem, serta rekomendasi sebelum maintenance dilakukan.

📄 Dokumentasi lengkap tersedia pada:

```text
mini-project.md
```

---

# Skills Acquired

Setelah menyelesaikan seluruh aktivitas pada Day 05 saya memperoleh kemampuan berikut:

- Linux Process Monitoring
- Linux Process Investigation
- Process Tree Analysis
- Process Search
- Linux Job Control
- Linux Signal Handling
- Process Management
- Linux Service Management
- systemd Administration
- journalctl Log Investigation
- Resource Monitoring
- Production Troubleshooting
- Root Cause Analysis (RCA)
- Enterprise Server Health Assessment
- Technical Documentation

---

# Portfolio Highlights

Repository Day 05 ini mendokumentasikan tiga jenis pembelajaran yang saling melengkapi:

### Hands-on Lab

Mempelajari penggunaan command Linux Process Management secara bertahap.

### Challenge Lab

Menyelesaikan investigasi berbasis skenario enterprise layaknya tiket operasional yang diterima oleh Linux Administrator.

### Mini Project

Menyusun **Enterprise Linux Server Health Audit Report** sebagai deliverable profesional yang mengintegrasikan seluruh materi pembelajaran.

---

# Learning Outcomes

Setelah menyelesaikan Day 05 saya mampu:

- Memahami lifecycle process pada Linux.
- Mengidentifikasi parent dan child process.
- Melakukan monitoring CPU, Memory, Swap, dan Load Average.
- Mengelola foreground dan background process.
- Menggunakan Linux Signals secara tepat.
- Melakukan investigasi service menggunakan systemd.
- Menganalisis system log menggunakan journalctl.
- Melakukan audit kondisi server sebelum maintenance.
- Menyusun laporan teknis yang menyerupai workflow Linux Administrator di lingkungan enterprise.

---

# Next Learning

Setelah menyelesaikan Day 05, pembelajaran akan dilanjutkan ke **Day 06 — Linux Package Management**, yang akan membahas pengelolaan paket perangkat lunak menggunakan APT, instalasi aplikasi, repository management, update sistem, serta praktik terbaik dalam melakukan software maintenance pada Ubuntu Server.