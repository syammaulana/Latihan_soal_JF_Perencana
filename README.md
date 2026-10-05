# Latihan Soal Jabatan Fungsional Perencana

Aplikasi latihan soal (70 soal acak, timer 120 menit, KKM 70) untuk persiapan ujian
Jabatan Fungsional Perencana. Materi: Ekonomi, Sosial, Spasial, Teknis Perencanaan
Pembangunan.

## Struktur folder

```
index.html          <- tampilan & logika aplikasi (tidak perlu diubah untuk tambah soal)
data/ekonomi.json    <- 216 soal
data/sosial.json     <- 204 soal
data/spasial.json    <- 239 soal
data/teknis.json     <- 292 soal
```

Setiap kali latihan dimulai, aplikasi mengambil **14 soal acak** dari Ekonomi, Sosial,
dan Spasial, serta **28 soal acak** dari Teknis (total 70). Komposisi ini diatur di
`index.html` lewat variabel `QUOTA`.

## Menjalankan di komputer sendiri

Karena index.html memuat soal lewat `fetch()`, file harus dibuka lewat server lokal
(bukan dobel klik file-nya langsung), contoh:

```
npx serve .
# atau
python3 -m http.server 8080
```

Lalu buka `http://localhost:8080` (atau port yang muncul).

## Menjalankan di GitHub Pages

1. Push folder ini ke sebuah repo GitHub.
2. Masuk ke **Settings → Pages**, pilih branch utama dan folder root (`/`).
3. Tunggu beberapa menit, aplikasi bisa diakses di
   `https://<username>.github.io/<nama-repo>/`.

## Menambah soal

Buka file JSON kategori yang sesuai (`data/ekonomi.json`, dst). Setiap soal adalah
satu array dengan format:

```json
["Teks pertanyaan di sini?", ["Opsi A", "Opsi B", "Opsi C", "Opsi D", "Opsi E"], 2]
```

- Elemen 1: teks soal.
- Elemen 2: array 5 opsi jawaban (urutan A–E).
- Elemen 3: indeks opsi yang benar, **mulai dari 0** (0=A, 1=B, 2=C, 3=D, 4=E).

Tambahkan soal baru sebagai elemen baru di dalam array utama, dipisah koma. Pastikan
file tetap berupa JSON valid (gunakan https://jsonlint.com untuk mengecek jika ragu).

Tidak perlu mengubah `index.html` kecuali ingin mengubah jumlah soal per kategori
(ubah angka di `QUOTA`) atau menambah kategori baru.
