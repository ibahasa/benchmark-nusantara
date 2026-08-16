# benchmark-results: satu tabel hasil lintas seluruh set

**Lisensi:** CC BY 4.0 · **Berkas:** `export-semua-hasil.csv`

---

## In English

**What this is.** Every measurement we publish, in one table. One row per model
per set per task per prompt per repetition. It is generated, not written by hand.

**Why it exists.** Our benchmark pages and model pages state when each model was
run and what it scored. Until now that was a claim you had to take on trust. This
file makes it checkable: download one file and compare it against what you see on
the page. It also answers the cross-set question, "when was this model tested, on
everything", which otherwise means opening six separate files.

**What it does not prove.** It proves that the numbers we display match the
numbers we recorded. It does not prove the model calls happened, because nothing
in it comes from a third party. That would need a signature from the provider,
and no provider offers one.

**Read `waktu_pasti` before trusting a date.** A `0` means the timestamp was
inferred from a git commit rather than recorded when the model was called.

**What `penilai` and `rumusan` mean.** The codes in those columns (`mcq-py1`,
`open-py1`, and the rest) are listed with their meanings in the Indonesian
section below.

**Rest of this file is in Indonesian, which is the canonical version.** Write to
**halo@ibahasa.com** if a figure here matters to you and you cannot read it.

---

## Kenapa berkas ini ada

Laman benchmark dan laman model menampilkan kapan tiap model dijalankan dan
berapa skornya. Selama ini itu **klaim**: pembaca disuruh percaya bahwa angka di
layar sama dengan angka yang kami catat.

Berkas ini mengubahnya jadi klaim yang dapat diperiksa. Unduh satu berkas, lalu
cocokkan barisnya dengan apa yang tampil di halaman.

Gunanya yang kedua lintas set. Pertanyaan "kapan saja model ini diuji, di seluruh
benchmark" sebelumnya menuntut membuka enam berkas terpisah.

## Asalnya

Dibangkitkan dari snapshot yang **sama persis** dengan yang diimpor ke basis data
situs. Jadi kesamaan antara berkas ini dan angka yang tampil bukan kebetulan yang
kami jaga dengan hati-hati, melainkan akibat langsung dari sumbernya satu.

Hanya set yang berstatus terbit yang masuk. Set kerja yang sengaja ditahan tidak
punya baris di sini, dan penyaringnya membaca berkas konfigurasi set, bukan
mengandalkan snapshot sudah bersih.

## Hubungannya dengan berkas per set

Tiap dataset set punya `ringkas-model.csv` sendiri. Berkas ini memuat baris yang
sama, disatukan.

Untuk lima dari enam set, kesamaannya dapat Anda periksa langsung: ambil
`ringkas-model.csv` set tersebut, cocokkan barisnya dengan baris di sini yang
kunci enam bagiannya sama, dan seluruh kolomnya harus identik.

Set normalisasi teks Indonesia adalah pengecualian. Ekspornya memakai skema
berbeda karena set itu menilai dua kemampuan yang berlawanan, mengganti kata
tidak baku lawan membiarkan kata yang sudah baku, sehingga kolomnya tidak sama
dengan set lain. Barisnya tetap ada di sini dalam bentuk seragam.

## Baris set kendali

Sebagian baris memakai kode set berakhiran `-kendali`. Set semacam itu bukan
benchmark tersendiri, melainkan kendali kontaminasi bagi set induknya.

Set induknya menerbitkan kunci jawaban penuh supaya angkanya dapat dihitung ulang
siapa pun. Harganya, sesudah kunci itu terbit, skor tinggi tidak dapat dibedakan
dari model yang membaca berkasnya. Set kendali mengukur kemampuan yang sama pada
lema yang kuncinya tidak pernah kami terbitkan, sehingga selisih keduanya
memisahkan paham dari hafal.

Karena lemanya berbeda, **skor kendali tidak sebanding lurus dengan skor
induknya**. Yang dibaca selisihnya, pada model yang sama.

**Lema, kunci, dan jawaban model set kendali tidak akan pernah diterbitkan**,
sebab justru itu yang membuatnya berguna. Yang ada di berkas ini cuma skornya.
Konsekuensinya baris tersebut tidak dapat Anda hitung ulang sendiri, dan kami
menyebutnya di sini alih-alih membiarkan Anda mencari berkas datanya.

## Kolom yang menentukan

**Kunci enam bagian:** `set`, `tugas`, `penilai`, `rumusan`, `versi_soal`,
`versi_kunci`. Dua baris hanya sebanding kalau keenamnya sama. Skor pada
`versi_kunci` yang berbeda datang dari kunci jawaban yang berbeda, dan
membandingkannya menghasilkan selisih yang tidak berarti apa-apa.

**`penilai` dan `rumusan`.** `rumusan` adalah pengenal versi prompt yang dipakai
memanggil model. `penilai` adalah pengenal alat yang mengubah jawaban menjadi
skor. Keduanya bernama sendiri supaya skor dari dua jalur yang berbeda tidak
tercampur secara tidak sengaja. Nilai yang muncul di berkas ini:

| Nilai | Kolom | Arti |
|---|---|---|
| `mcq-py1` | keduanya | tugas pilihan ganda: model memilih satu opsi, dinilai mesin |
| `open-py1` | keduanya | tugas jawaban terbuka, rumusan generik versi 1 |
| `open-py2` | rumusan | varian rumusan yang diuji pada set normalisasi teks |
| `open-py3` | rumusan | varian rumusan kedua, ditulis sesudah aturan kunci diukur |
| `kunci-alias-v1` | penilai | set arti-kata: jawaban dicocokkan ke kunci jamak ber-alias |
| `arti-kata-v1` | rumusan | set arti-kata: model ditanya arti sebuah lema |

**`waktu_pasti`.** Bernilai 0 berarti tanggalnya **ditaksir dari tanggal commit
git**, bukan dicatat saat model dipanggil. Untuk baris semacam itu, tanggalnya
menunjukkan kapan hasilnya masuk ke buku besar kami, bukan kapan modelnya
dipanggil.

Kami menyebutnya karena berkas yang tugasnya membuktikan "kami menjalankan ini
pada tanggal itu" tidak boleh mengarang presisi tanggalnya sendiri.

**`benar`, `n_dinilai`, `n_item`, dan `skor` adalah IRISAN PUBLIK**, bukan
totalnya. Set yang menahan sebagian soalnya tetap menjalankan dan menilai soal
itu, tetapi kunci yang kami terbitkan hanya mencakup irisan publik. Menuliskan
total di sini akan memberi Anda angka yang tidak dapat Anda hitung ulang dengan
kunci yang kami beri.

**`benar_tertahan`, `n_dinilai_tertahan`, dan `skor_tertahan`** memuat irisan
tertahannya. Nol dan kosong berarti set itu tidak menahan apa pun.

Angka tertahan TIDAK sebanding lurus dengan angka publik, sebab soalnya berbeda.
Yang dibaca pola selisihnya antar-model: model yang selisihnya jauh lebih lebar
daripada model lain patut dicurigai pernah membaca kunci yang sudah terbit.

Lema dan kunci irisan tertahan tidak akan pernah diterbitkan, jadi kolom
tertahan memang tidak dapat Anda hitung ulang. Kami menyebutnya di sini alih-alih
membiarkan Anda mencari berkas datanya.

**`tugas`.** Satu set boleh punya beberapa tugas, dan skornya **tidak boleh
dijumlahkan** antar-tugas. Mengenali register yang benar dan memproduksinya
adalah dua kemampuan yang berbeda.

**`biaya_usd` kosong** berarti model dijalankan di perangkat keras kami sendiri.
Kosong bukan nol: tidak ada tagihan bukan berarti tidak ada biaya, dan latensinya
tidak sebanding dengan API terkelola. Model semacam itu berakhiran `-local`.

**Parameter pemanggilan.** Seluruh baris dijalankan pada suhu nol. Pagu jawaban
bawaannya 600 token, dan kolom `cap_token` menyatakan pagu yang benar-benar
dipakai tiap baris. Rincian per set, termasuk jumlah ulangan, ada di
`PROVENANCE.md` dataset masing-masing.

Pagu itu tidak seragam untuk semua model, dan bacalah `cap_token` alih-alih
menganggapnya 600. Pada panel `jv-B` 2026-08-16, `nemotron-3.5-lightning`
menyentuh pagu 600 pada 112 dari 199 soal, sementara sebelas model lain tidak
pernah menyentuhnya sama sekali (keluaran terpanjang di antara mereka 544 token).
Model itu dijalankan ulang pada pagu 3.000, begitu pula satu soal `deepseek`.

Pilihan itu ada harganya dan sengaja tidak disembunyikan: pagu adalah kondisi
ukur, jadi model yang dijalankan pada pagu berbeda tidak sepenuhnya sebanding
dengan yang lain. Alasan memilihnya begitu adalah pagu ada untuk mengerem biaya,
bukan untuk mendefinisikan tugasnya, dan mengukur model bernalar pada 600 token
berarti mengukur apakah jawabannya muat, bukan apakah ia paham.

## Yang TIDAK ada di berkas ini

Tidak ada kalimat soal, tidak ada kunci jawaban, dan tidak ada teks jawaban
model. Angka dan metadata saja.

Kolom `rumusan` hanya memuat pengenal, mis. `mcq-py1`. Teks rumusan lengkap
diterbitkan untuk set normalisasi teks (`rumusan.csv` pada datasetnya) dan
sengaja tidak untuk set lainnya.

## Yang TIDAK dibuktikannya

Berkas ini membuktikan angka yang kami tampilkan sama dengan angka yang kami
catat. Ia **tidak** membuktikan pemanggilan modelnya benar-benar terjadi, sebab
tidak satu pun isinya berasal dari pihak ketiga.

Bukti semacam itu menuntut tanda tangan dari penyedia model, dan tidak ada
penyedia yang menyediakannya. Kami menyebutnya di sini supaya tidak ada yang
membaca berkas ini lebih kuat daripada yang sebenarnya.

## Kalau menurut Anda ada yang keliru

Sebut barisnya beserta kunci enam bagiannya. Lihat `CONTRIBUTING.md` di akar
repo, atau tulis ke **halo@ibahasa.com**.
