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
