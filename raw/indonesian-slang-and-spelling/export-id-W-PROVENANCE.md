# Koreksi ejaan Indonesia: ringkasan per model

**Tanggal:** 2026-08-14 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `ringkas-model.csv`, `per-item.csv`
**Sumber:** set id-W milik kami, 9 baris hasil

Berkas ini dihasilkan `core/ekspor_riset.py` dan memuat ANGKA saja: tidak ada
item, tidak ada kunci jawaban. Soal dan kuncinya kami tahan, jadi dataset ini
TIDAK dapat dipakai menjalankan ulang model. Angkanya dapat dihitung ulang;
pengukurannya tidak dapat diulang dari sini.

## In English

**What this is.** Spelling-correction restraint: whether a model holds its
hand on text that real people wrote. Each item offers one spell-checker
suggestion already judged by a native speaker, and the model decides whether
to accept or reject it. The mix is deliberately lopsided, 39 wrong suggestions
against 15 right ones, so a model that rejects everything cannot score full
marks without understanding a single sentence. The model panel grows, so read
the current list from `ringkas-model.csv`; the item count is fixed.

**Who scored it.** The suggestions were judged by a native speaker; the model
decisions are machine-scored multiple choice, one call per item, no
repetition, at temperature 0 with a 600-token answer cap.

**Main limits.** The run-to-run variance of this set has never been measured,
so a few points of difference between models should not be read as an ability
difference. One row is a 4-bit quantised local model whose low score has two
explanations this data cannot separate: the model is genuinely like that, or
the quantisation cost it. Provider aliases are floating, and the figures apply
to the versions served on the run date. The items and the key are withheld, so
the figures can be re-checked but the measurement cannot be re-run from here.

**The rest of this file is in Indonesian**, and that is the canonical version.
If a figure here matters to you and you cannot read Indonesian, write to us
and we will answer in English: **halo@ibahasa.com**

**If you disagree with a figure**, name the row. A dispute can be settled on
that row rather than thrown at us generally.

## Untuk apa set ini dibuat

Mengukur pengendalian diri model pada teks yang benar-benar ditulis orang.
Tiap soal menyodorkan satu saran pemeriksa ejaan yang sudah dinilai penutur,
lalu model memutuskan menerima atau menolaknya. Campurannya sengaja timpang, 39
saran keliru berbanding 15 saran benar, supaya model yang menolak apa pun tidak
mendapat nilai penuh tanpa memahami satu kalimat pun.

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

## Kolom `per-item.csv`

Satu baris per butir per model, pada **irisan publik saja**. Berkas ini ada supaya
angka di `ringkas-model.csv` dapat dihitung ulang, bukan dipercaya begitu saja:
jumlahkan `benar` per model lalu bulatkan, dan hasilnya wajib sama dengan kolom
`benar` di sana.

| Kolom | Arti |
|---|---|
| `item_id` | penanda butir, buram. Kalimat soalnya tidak terbit |
| `model` | slug kanon, sama dengan `semua-hasil.csv` |
| `tugas` | `pilihan-ganda` atau `terbuka`. Keduanya TIDAK boleh dijumlahkan |
| `penilai` | cara vonis diperoleh, mis. `mcq-py1` atau `open-py1` |
| `benar` | vonis butir itu. Bulat untuk pilihan ganda, dapat pecahan untuk rubrik |
| `latensi_ms`, `tokens_out`, `cap_token` | jejak jalan |
| `biaya_usd` | kosong berarti model dijalankan di perangkat kami, bukan nol |
| `dijalankan_pada` | waktu panggilan itu terjadi |

**Yang sengaja TIDAK ada.** Kalimat soal, kunci jawaban, teks jawaban model, dan
opsi yang dipilih model.

Kolom terakhir itu yang paling menentukan pada tugas pilihan ganda. Opsi pilihan
model yang terbit bersama vonis membocorkan kuncinya seketika: satu baris berskor
1 sudah cukup untuk tahu opsi mana yang benar. Pemeriksa ekspor kami menolak
berkas apa pun yang memuat kolom semacam itu pada set pilihan ganda.

**Baris irisan tertahan juga tidak ada.** Agregat irisan publik sudah dapat
dihitung ulang tanpanya, sementara menerbitkannya berarti menyebutkan butir mana
yang jadi cadangan beserta vonis tiap model di atasnya.

Karena soal dan kuncinya ditahan, berkas ini cukup untuk memeriksa **aritmetika**
kami, bukan **penilaian** kami. Vonis tiap baris tetap harus dipercaya.
