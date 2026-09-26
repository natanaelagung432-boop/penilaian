PENILAIAN REALTIME
===================

ISI:
- server.html   : panel operator
- display.html  : layar hasil/ranking realtime
- database-rules.txt : contoh rules Firebase
- README.txt

1. FIREBASE
-----------
Buat Firebase project dan aktifkan Realtime Database.

2. CONFIG
---------
Buka server.html dan display.html.
Cari:

const firebaseConfig={...}

Isi dengan Firebase Web App Config milik Anda.
Kedua file harus memakai project Firebase yang sama.

3. DATABASE
-----------
Struktur otomatis dibuat oleh server:

competition
  rounds
  participants
  scores

Contoh:

competition/
  rounds/
    rondeId/
      name: "Ronde 1"
      order: 1

  participants/
    pesertaId/
      name: "Andi"
      order: 1

  scores/
    rondeId/
      pesertaId: 250

4. SERVER
---------
- Tambah ronde
- Pilih ronde
- Tambah peserta
- Edit nama
- Hapus peserta
- Nilai +1, +10, +50, +100
- Nilai -1, -10, -50, -100
- Edit nilai langsung
- Urutan peserta server tetap

5. DISPLAY
----------
Display otomatis menjumlahkan seluruh ronde untuk setiap peserta.
Ranking diurutkan dari total terbesar ke terkecil.
Perubahan nilai, nama, peserta, atau ronde akan diterima realtime tanpa refresh.

6. CATATAN KEAMANAN
-------------------
database-rules.txt menggunakan rules terbuka untuk pengujian.
Jangan gunakan rules terbuka untuk sistem produksi publik.
Untuk penggunaan resmi, sebaiknya tambahkan Firebase Authentication dan rules berdasarkan akun/operator.

7. MENJALANKAN
--------------
Bisa memakai hosting statis seperti Firebase Hosting, GitHub Pages, Netlify,
atau server lokal yang menyajikan file HTML.

Jangan membuka file dengan file:// jika browser memblokir module.
Gunakan web server sederhana, misalnya:
python -m http.server 8000

Lalu buka:
http://localhost:8000/server.html
http://localhost:8000/display.html
