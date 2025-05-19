# ADVPRO Modul 10

## Nama: Makarim Zufar Prambudyo

## NPM: 2306241751

## Kelas: ADVPRO-B

---

### Experiment 2.1: Original code, and how it run

Server side:
![server side console screenshots](/README-image/server.png)

Client side:
![server side console screenshots](/README-image/client.png)

Dalam pengujian terbaru, saya telah berhasil mengoperasikan sebuah sistem komunikasi berbasis WebSocket yang terdiri dari satu server dan tiga klien. Beberapa poin penting yang dapat diamati:
#### Konfigurasi dan Konektivitas

- Server beroperasi pada port 2000
- Ketiga klien berhasil membentuk koneksi stabil dengan server
- Pertukaran data antar komponen berjalan tanpa kendala

#### Fungsionalitas Komunikasi

- Sistem broadcast berfungsi optimal - pesan dari satu klien terdistribusi ke semua klien lainnya
- Tidak ada penundaan signifikan dalam pengiriman/penerimaan pesan
- Tidak terjadi blocking pada saat komunikasi berlangsung

#### Arsitektur Teknis

- Implementasi memanfaatkan library tokio_websockets untuk pengelolaan koneksi
- Mekanisme broadcast channel dari tokio digunakan untuk distribusi pesan
- Pendekatan asinkron memungkinkan komunikasi real-time yang efisien

Hasil pengujian mengkonfirmasi bahwa kombinasi teknologi ini sangat efektif untuk pengembangan aplikasi chat sederhana dengan kemampuan komunikasi real-time.

### Experiment 2.2: Modifying port

Server side:
![server side console screenshots](/README-image/server2.png)

Client side:
![server side console screenshots](/README-image/client2.png)

Dalam eksperimen lanjutan, saya melakukan modifikasi pada konfigurasi port sistem chat:
#### Perubahan Konfigurasi

- Port komunikasi diubah dari 2000 menjadi 8080
- Perubahan diterapkan pada kedua komponen:

    - Server: modifikasi pada parameter TcpListener::bind
    - Klien: penyesuaian URI dalam fungsi ClientBuilder::from_uri

#### Hasil Modifikasi

- Konektivitas tetap terjaga dengan baik meskipun port telah diubah
- Proses pengiriman dan penerimaan pesan berjalan tanpa gangguan
- Performa real-time tetap konsisten seperti pada konfigurasi sebelumnya

#### Analisis Teknis

- Temuan ini mengkonfirmasi bahwa port hanyalah endpoint untuk koneksi jaringan
- Faktor kunci konektivitas adalah kesamaan alamat dan protokol antara server dan klien
- Protokol WebSocket tetap menjadi basis komunikasi tanpa perubahan
- Logika aplikasi tidak terpengaruh karena modifikasi hanya terjadi pada level transport

Kesimpulannya, aplikasi chat berbasis WebSocket ini menunjukkan fleksibilitas dalam konfigurasi jaringan sambil mempertahankan integritas fungsionalnya.

### Experiment 2.3: Small changes, add IP and Port

Server side:
![server side console screenshots](/README-image/server3.png)

Client side:
![server side console screenshots](/README-image/client3.png)

Dalam pengembangan terbaru, saya telah meningkatkan fungsionalitas sistem chat dengan menerapkan identifikasi asal pesan:
#### Modifikasi yang Dilakukan

- Pengayaan Data Pesan: Informasi alamat IP dan port pengirim kini disertakan dalam setiap pesan
- Implementasi Server: Penambahan dilakukan dengan memodifikasi fungsi bcast_tx.send(...)
- Metadata Komunikasi: Parameter addr yang berisi alamat socket client pengirim diintegrasikan ke dalam struktur pesan

#### Hasil Pengembangan

- Setiap client sekarang dapat melihat identitas teknis (alamat:port) dari pengirim pesan
- Informasi ini berfungsi sebagai pengenal sementara sebelum implementasi sistem username
- Antarmuka client diperbaiki dengan penambahan label "Zufar's Computer - From server:" untuk membedakan pesan masuk dengan input lokal

#### Signifikansi Pengembangan
Eksperimen ini memperlihatkan bagaimana metadata jaringan dapat dimanfaatkan untuk:

- Meningkatkan konteks komunikasi tanpa memerlukan sistem identifikasi kompleks
- Memberikan kejelasan tentang aliran informasi dalam sistem terdistribusi
- Mempermudah debugging dan pemantauan interaksi antar-client

Pengembangan ini merupakan langkah awal yang baik menuju sistem identifikasi pengguna yang lebih komprehensif.
