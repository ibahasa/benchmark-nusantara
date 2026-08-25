# Tingkat tutur bahasa Jawa: ringkasan per model

**Tanggal:** 2026-08-15 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `ringkas-model.csv`, `per-item.csv`
**Sumber:** set jv-A milik kami. Jumlah baris dan modelnya dibaca dari
`ringkas-model.csv`, bukan dari kalimat ini, sebab panelnya bertambah

## In English

**What this is.** Javanese speech levels (*tingkat tutur*): whether a model
picks the register a listener requires, and whether it notices when the
register is wrong. The set mixes 46 items, 38 machine-scored multiple-choice
items for recognition and 8 open items for production, and the two abilities
are never summed into one score: recognising the right register and producing
it from scratch are different abilities, measured on the same material. The
item count is fixed; the model panel grows, so read the current list and count
from `ringkas-model.csv` rather than from this sentence.

**Who scored it.** Multiple-choice items are scored by machine. The 8 open
items are graded one answer at a time by native speakers under a weighted
rubric, and each verdict is attached to the answer text itself, so two models
that answer with the same sentence receive the same verdict without being
graded twice.

**Main limits.** Eight open items are too few to stand alone: one item is
worth 12.5 points, so a one-answer gap between two models is not an ability
gap. Verdicts were made by one person, and inter-annotator agreement has never
been measured; that is the largest credibility hole in this set. The variety
measured is Yogya-Solo, and the figures measure native-speaker acceptability,
not prescriptive correctness. One call per item, no repetition, so variance is
unmeasured. One model row is `parsial`, standing on 35 of 38 items.

**The rest of this file is in Indonesian**, and that is the canonical version.
It documents the two graders, the per-column meanings, and how to dispute a
verdict. If a figure here matters to you and you cannot read Indonesian, write
to us and we will answer in English: **halo@ibahasa.com**

**If you disagree with a score**, name the item and the criterion. Every
verdict is attached to a specific row, so a dispute can be settled on that row
rather than thrown at us generally.

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
Rubrik berbobot dan rincian kriterianya DITAHAN bersama soal dan kunci, sebab
tiap kriteria menyebut bentuk yang dituntut, dan menerbitkannya sama saja
membocorkan kunci. Yang terbit adalah vonis per item, angka saja. Kesepakatan
antar-penilai juga belum pernah kami ukur, dan itu lubang kredibilitas terbesar
pada kolom isian.

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
| `benar` / `n_dinilai` / `n_item` / `skor` | jawaban benar, yang dinilai, yang ditanyakan, dan rasionya, pada **IRISAN PUBLIK saja**. Ketiganya dapat berbeda |
| `benar_tertahan` / `n_dinilai_tertahan` / `skor_tertahan` | angka yang sama untuk irisan TERTAHAN, yang soal dan kuncinya tidak diterbitkan |
| `benar_bobot` | jumlah benar PERSIS saat penilaiannya berbobot pecahan. Kosong berarti cacahan bulat |
| `parsial` | model tidak menjawab seluruh soal |
| `tanpa_skor` | belum satu pun jawabannya dinilai |
| `menunggu_vonis` | menjawab semuanya, sebagian jawabannya belum divonis penutur |
| `beku` | soalnya berubah sesudah run ini, skor tersimpan yang dipakai |
| `biaya_usd` | kosong untuk baris berjalur lokal, dan itu BUKAN nol |
| `latensi_median_ms` | untuk baris lokal ia mengukur mesin kami, tidak sebanding |
| `tokens_in` / `tokens_out` | kosong berarti TIDAK TERCATAT, bukan nol |

**`benar` sendirian TIDAK pernah berarti "benar dari seluruh soal".** Skor
seluruh set adalah `benar` ditambah `benar_tertahan`, dan penyebutnya
`n_dinilai` ditambah `n_dinilai_tertahan`. Membaca `benar` sebagai total
menghasilkan angka yang terlalu rendah untuk model yang kuat, dan kekeliruan
itu pernah terbit di artikel kami sendiri pada 2026-08-24 lalu dikoreksi dua
hari kemudian.
| `versi_soal` / `versi_kunci` | sidik bentuk dataset saat run. Skor lintas versi kunci berbeda tidak sebanding |

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
