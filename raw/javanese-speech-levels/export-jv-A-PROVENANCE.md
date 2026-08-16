# Tingkat tutur bahasa Jawa: ringkasan per model

**Tanggal:** 2026-08-15 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `ringkas-model.csv`
**Sumber:** set jv-A milik kami, 20 baris hasil dari 13 model

## Untuk apa set ini dibuat

Mengukur pemahaman tingkat tutur bahasa Jawa: apakah model memilih ragam yang
tepat bagi lawan bicara, dan apakah ia mengenali ketika ragamnya keliru.

Setnya campuran 46 item, sebagian pilihan ganda dan sebagian isian. **Keduanya
sengaja tidak pernah dijumlahkan jadi satu skor**, dan itu bukan kerapian
melainkan inti rancangannya. Mengenali ragam yang benar dan menghasilkannya dari
nol adalah dua kemampuan yang berbeda, dan set ini memisahkannya di atas materi
yang sama. Baris `tugas` di CSV yang membedakan keduanya: `pilihan-ganda` untuk
38 soal pengenalan, `terbuka` untuk 8 soal produksi.

## Bagaimana angkanya dihasilkan

Tiga belas model, satu panggilan per item, tanpa ulangan. Suhu nol, batas 600
token jawaban. Model berbayar dipanggil lewat satu perantara. Tiga model
bertanda `-local` di kolom `model` dijalankan di perangkat keras kami sendiri,
satu desktop dengan prosesor Ryzen 5 3600, memori 32 GB, dan kartu grafis
RTX 3060 Ti dengan 8 GB VRAM.

Kolom `biaya_usd` dan `latensi_median_ms` untuk baris berjalur lokal **tidak
sebanding** dengan baris lain, dan kolom biayanya sengaja dibiarkan kosong alih
alih diisi nol. Nol pada tagihan bukan nol pada kenyataan: perangkat kerasnya
dibeli dan listriknya dibayar. Waktu tunggunya mengukur mesin kami, bukan
layanan yang siapa pun dapat beli.

**Dua penilai yang berbeda, dan bedanya besar.** Kolom `penilai` menyatakan
mana yang berlaku untuk tiap baris:

- **38 soal pilihan ganda** dinilai mesin. Satu huruf opsi dibaca dari jawaban
  lalu dibandingkan dengan kunci. Jawaban tanpa huruf opsi dicatat sebagai gagal
  format, terpisah dari jawaban salah, supaya alat yang rusak tidak terbaca
  sebagai model yang lemah.
- **8 soal isian dinilai penutur asli, satu jawaban per satu jawaban**, memakai
  rubrik berbobot yang tiap kriterianya dicatat sendiri. Vonis melekat pada
  TEKS jawabannya, bukan pada modelnya, jadi dua model yang menjawab dengan
  kalimat identik menerima vonis yang sama tanpa dinilai dua kali.

Soal dan kunci jawabannya sendiri diperiksa dua penutur asli, seluruh item, satu
per satu: M. Khoirul Huda dan Hasan Basri, guru SMA di Semarang.

## Apa yang tidak boleh disimpulkan dari angka ini

**Delapan soal isian terlalu sedikit untuk berdiri sendiri.** Satu item di sana
bernilai 12,5 poin. Selisih satu jawaban antara dua model bukan selisih
kemampuan, dan angka isian mana pun di CSV ini tidak boleh dikutip tanpa
penyebutnya.

Pada 38 soal pilihan ganda, satu item bernilai 2,63 poin. Selisih di bawah
kira-kira dua item sebaiknya dianggap belum terpisah.

**Vonis atas jawaban model dibuat satu orang saja**, tanpa tinjauan independen.
Rubrik berbobot dan rincian tiap kriteria terbit bersama angkanya, jadi tiap
vonis dapat dibantah pada kriteria tertentu, bukan sekadar ditolak
mentah-mentah. Tetapi kesepakatan antar-penilai belum pernah kami ukur, dan itu
lubang kredibilitas terbesar pada kolom isian.

**Ragam bahasa Jawanya tunggal, Yogya-Solo.** Penutur Jawa Timuran atau
Banyumasan dapat menilai sebagian item secara berbeda.

Angka ini mengukur **keberterimaan penutur asli**, bukan kepatuhan pada aturan
tata bahasa preskriptif. Ia karena itu bukan pernyataan tentang bentuk mana yang
paling benar.

Satu panggilan per item tanpa ulangan, jadi ragam antar-panggilan tidak terukur
sama sekali di set ini.

**Baris `ling-3.0-flash` berdiri di atas 35 item yang sah, bukan 38**, dan
bertanda `parsial`. Persennya karena itu tidak berbagi penyebut dengan baris
lain.

## Apa yang TIDAK ada di berkas ini

Tidak ada kalimat soal, tidak ada kunci jawaban, dan tidak ada teks jawaban
model. Berkas ini memuat angka saja.

Tiga belas dari 46 item bertanda tertahan dan tidak pernah kami terbitkan dalam
bentuk apa pun. Set ini masih jadi set kerja tingkat tutur kami, dan
menerbitkan soalnya berarti model berikutnya melatihnya.

## Kolom

| Kolom | Arti |
|---|---|
| `model` | slug model. Akhiran `-local` berarti dijalankan di perangkat keras kami |
| `tugas` | `pilihan-ganda` untuk pengenalan, `terbuka` untuk produksi. JANGAN dijumlahkan |
| `penilai` | mesin untuk pilihan ganda, rubrik penutur untuk isian |
| `rumusan` | templat prompt yang dipakai |
| `benar` / `n_dinilai` / `n_item` | jawaban benar, yang dinilai, yang ditanyakan. Ketiganya dapat berbeda |
| `benar_bobot` | jumlah benar PERSIS saat penilaiannya berbobot pecahan. Kosong berarti cacahan bulat |
| `parsial` | model tidak menjawab seluruh soal |
| `tanpa_skor` | belum satu pun jawabannya dinilai |
| `menunggu_vonis` | menjawab semuanya, sebagian jawabannya belum divonis penutur |
| `beku` | soalnya berubah sesudah run ini, skor tersimpan yang dipakai |
| `biaya_usd` | kosong untuk baris berjalur lokal, dan itu BUKAN nol |
| `latensi_median_ms` | untuk baris lokal ia mengukur mesin kami, tidak sebanding |
| `tokens_in` / `tokens_out` | kosong berarti TIDAK TERCATAT, bukan nol |
| `versi_soal` / `versi_kunci` | sidik bentuk dataset saat run. Skor lintas versi kunci berbeda tidak sebanding |
