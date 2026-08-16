# Pemahaman slang Indonesia: ringkasan per model

**Tanggal:** 2026-08-14 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `ringkas-model.csv`
**Sumber:** set id-B milik kami, 9 baris hasil

Berkas ini dihasilkan `core/ekspor_riset.py` dan memuat ANGKA saja: tidak ada
item, tidak ada kunci jawaban. Soal dan kuncinya kami tahan, jadi dataset ini
TIDAK dapat dipakai menjalankan ulang model. Angkanya dapat dihitung ulang;
pengukurannya tidak dapat diulang dari sini.

## Untuk apa set ini dibuat

Mengukur pemahaman bahasa gaul Indonesia. Model diberi potongan teks yang
disorot pembaca, lalu diminta menjelaskan artinya. Kami mengukur dua hal
sekaligus: seberapa sering penjelasannya tepat, dan seberapa sering model
mengarang arti yang tidak pernah ada.

## Bagaimana angkanya dihasilkan

Sepuluh model, satu panggilan per item, tanpa ulangan. Suhu nol dan batas
jawaban 600 token untuk seluruhnya. Sembilan model dipanggil lewat satu
perantara berbayar; satu model dijalankan di perangkat keras kami sendiri lewat
Ollama, dan baris itu bertanda `biaya_usd` kosong.

Kolom `biaya_usd` kosong berarti TIDAK ADA TAGIHAN untuk dicatat, bukan nol.
Model lokal berjalan di komputer yang kami beli dan listrik yang kami bayar, dan
tidak satu pun dari itu masuk ke angka mana pun di berkas ini. Kolom
`latensi_median_ms` untuk baris itu mengukur mesin kami, bukan layanan yang
pembaca dapat beli, jadi ia tidak sebanding dengan sembilan baris lainnya.

## Batas pembacaan angka ini

Satu panggilan per item, tanpa ulangan. Ragam antar-panggilan pada set ini
belum pernah kami ukur, jadi selisih beberapa poin antar-model tidak boleh
dibaca sebagai selisih kemampuan.

Model lokal dikuantisasi ke 4 bit dan bobotnya unggahan ulang pihak ketiga. Skor
rendahnya punya dua penjelasan yang tidak dapat dipisahkan dari data ini:
modelnya memang begitu, atau kuantisasinya yang memakannya.

Angka ini berlaku untuk versi model yang melayani saat pengujian dijalankan.
Sebagian id penyedia tidak mengunci versinya, jadi penyedia boleh menggantinya
kapan saja tanpa memberi tahu.

Soal dan kuncinya tidak diterbitkan, jadi pembaca tidak dapat menjalankan ulang
model dengan berkas ini.

## Kolom

| Kolom | Arti |
|---|---|
| `benar` / `n_dinilai` / `n_item` | jawaban benar, yang dinilai, yang ditanyakan. Ketiganya dapat berbeda |
| `benar_bobot` | jumlah benar PERSIS saat penilaiannya berbobot pecahan; kosong berarti cacahan bulat |
| `parsial` | model tidak menjawab seluruh soal |
| `tanpa_skor` | belum satu pun jawabannya dinilai |
| `menunggu_vonis` | menjawab semuanya, sebagian jawabannya belum divonis penutur |
| `beku` | soalnya berubah sesudah run ini, skor tersimpan yang dipakai |
| `tokens_in` / `tokens_out` | kosong berarti TIDAK TERCATAT, bukan nol |
