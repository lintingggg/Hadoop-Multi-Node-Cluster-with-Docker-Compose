# 🐘 Hadoop Multi-Node Cluster with Docker Compose

Repositori ini berisi konfigurasi untuk menjalankan **Apache Hadoop 3.2.1** di dalam lingkungan Docker. Proyek ini dirancang untuk memudahkan mahasiswa atau developer dalam mempelajari ekosistem Big Data tanpa perlu instalasi manual yang rumit di sistem operasi lokal.

---

## 🏗️ Arsitektur Cluster

Cluster ini menggunakan **Hadoop 3.2.1** yang berjalan di atas **Java 8**.

- **NameNode**: Master node yang mengelola metadata HDFS (Port: 9870).
- **DataNode**: Worker node yang menyimpan blok data aktual.

---

## 🚀 Persiapan & Instalasi

### 1. Prasyarat

Pastikan sistem kamu sudah terinstall:

- **Docker Engine** (v20.10+)
- **Docker Compose** (v2.0+)

### 2. Struktur Folder

Pastikan folder kamu memiliki struktur seperti berikut:

```text
hadoop-docker-lab/
├── docker-compose.yml
├── hadoop.env
└── README.md
```

### 3. Menjalankan Cluster

Jalankan perintah berikut di terminal:

```bash
# Menyalakan cluster di latar belakang (detached mode)
docker compose up -d
```

### 4. Verifikasi Layanan

Cek apakah kontainer sudah berjalan dengan benar:

```bash
docker compose ps
```

---

## 🛠️ Penggunaan HDFS (Hands-on)

Untuk berinteraksi dengan sistem file Hadoop, kamu harus masuk ke dalam kontainer NameNode.

### Masuk ke Container

```bash
docker exec -it namenode bash
```

### Perintah Dasar HDFS

| Perintah | Deskripsi |
|----------|----------|
| `hdfs dfs -ls /` | Melihat daftar file di root |
| `hdfs dfs -mkdir /latihan` | Membuat direktori baru |
| `hdfs dfs -put <file_lokal> /latihan` | Upload file ke HDFS |
| `hdfs dfs -cat /latihan/file.txt` | Membaca isi file |
| `hdfs dfs -rm -r /latihan` | Menghapus direktori |

---

## 🌐 Monitoring Web UI

Kamu dapat memantau status cluster melalui browser di alamat berikut:

| Nama Layanan | URL | Fungsi |
|--------------|-----|--------|
| HDFS NameNode | http://localhost:9870 | Cek kesehatan node & file system |
| DataNode Info | http://localhost:9864 | Spesifikasi teknis data node |

---

## 🧹 Maintenance (Pemeliharaan)

- **Menghentikan Cluster:**
  ```bash
  docker compose stop
  ```
  *(Data di HDFS tetap tersimpan)*

- **Menghapus Cluster & Data:**
  ```bash
  docker compose down -v
  ```
  *(Menghapus kontainer dan volume data secara permanen)*

- **Menambah DataNode (Scaling):**
  ```bash
  docker compose up -d --scale datanode=3
  ```

> **Note:** File ini dibuat untuk keperluan pembelajaran mata kuliah Sistem Informasi. Gunakan dengan bijak!

---

## 💡 Cara Menggunakannya di Linux

1. Buka terminal di folder `~/hadoop-docker-lab`
2. Ketik:
   ```bash
   nano README.md
   ```
3. Paste (tempel) kode di atas
4. Simpan (**Ctrl + O**, **Enter**) dan keluar (**Ctrl + X**)

---

Sekarang folder lab kamu sudah standar profesional!  
Ada file konfigurasi (`.yml`), file lingkungan (`.env`), dan dokumentasi (`.md`).
