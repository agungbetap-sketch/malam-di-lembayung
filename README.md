# Malam di Lembayung

Game werewolf untuk satu kelas. Moderator menampilkan desa 3D bergaya 32-bit lewat proyektor dan memandu permainan. Pemain bisa bergabung lewat HP dengan PIN, atau bermain tanpa HP di satu layar.

**Main sekarang:** https://agungbetap-sketch.github.io/malam-di-lembayung/
**Halaman gabung untuk pemain:** https://agungbetap-sketch.github.io/malam-di-lembayung/join/

## Cara main

1. Buka halaman utama di laptop yang tersambung ke proyektor.
2. Pilih **Main online dengan PIN**. Layar menampilkan PIN dan kode QR.
3. Pemain memindai QR atau membuka halaman gabung, lalu mengisi PIN dan nama panggilan. Tidak perlu akun.
4. Pemain tanpa HP bisa ditambahkan lewat kolom nama di layar persiapan.
5. Bagikan peran, lalu ikuti narator. Pilihan malam dan voting masuk dari HP, dan moderator menekan tombol konfirmasi.

Spasi atau Enter melanjutkan narasi.

## Peran

| Peran | Pihak | Kemampuan |
|---|---|---|
| Serigala | Serigala | Memilih satu korban tiap malam |
| Serigala Alfa | Serigala | Ikut berburu, terlihat seperti warga di mata Peramal |
| Peramal | Warga | Memeriksa satu orang tiap malam |
| Tabib | Warga | Melindungi satu orang tiap malam |
| Penyihir | Warga | Satu ramuan penyembuh dan satu racun, masing-masing sekali pakai |
| Pemburu | Warga | Menembak satu orang saat mati |
| Tetua | Warga | Selamat dari serangan serigala pertama |
| Mak Comblang | Warga | Mengikat sepasang kekasih di malam pertama |
| Badut | Sendiri | Menang jika dihukum lewat voting |
| Warga | Warga | Tanpa kekuatan khusus |

## Teknis

- Satu file `index.html`, dengan Three.js r128 untuk desa 3D.
- Mode online memakai broker MQTT publik lewat WebSocket (HiveMQ, EMQX, atau Mosquitto). Digit pertama PIN menentukan broker.
- Peran rahasia dan pilihan malam dienkripsi end-to-end antara HP pemain dan laptop moderator (ECDH P-256 + AES-GCM), jadi tidak bisa dibaca dari broker.
- Jangan muat ulang laptop moderator selama permainan berjalan, karena keadaan permainan disimpan di laptop itu.
