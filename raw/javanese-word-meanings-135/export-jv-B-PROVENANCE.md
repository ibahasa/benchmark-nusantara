# jv-B: arti 135 kata Jawa, kunci jamak yang ditinjau penutur

**Tanggal:** 2026-08-13, diperbarui 2026-08-16 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `hasil-model.csv`, `kunci.csv`, `ragam.csv`
**Sumber:** lema berbahasa Jawa dari kamus kami, seluruhnya berstatus terverifikasi
manusia dan sudah terbit di halaman kamus publik

Pengukuran kami sendiri atas model yang dipanggil lewat satu perantara. Daftar
model yang berlaku sekarang ada di `ringkas-model.csv`, bukan di kalimat ini. Lema,
definisi, dan kunci jawabannya milik kami.

---

## In English

**What this is.** AI models were asked the meaning of 135 Javanese lemmas.
The lemma count is fixed; the model panel grows, so read the current list and
count from `ringkas-model.csv` rather than from this sentence. The lemmas, their definitions and the answer keys are ours, taken from our own dictionary, and every one of them carries a human verification status. Each item accepts several correct answers rather than one, because a word meaning rarely has a single right wording.

**Who scored it.** The answer keys were drafted from our own dictionary definitions and then reviewed by a native Javanese speaker. Model answers were matched against those keys.

**Main limits.** Every lemma and definition here was already public on our dictionary pages before this dataset was published, so a high score cannot be read as proof that a model was never exposed to them. Our clean measuring instrument is the held-back slice inside this set, whose keys are never published, backed by a further reserve of single-word lemmas from the same pool. Counts move as the set grows, so read them from the data rather than from this sentence. The variety measured is Yogya-Solo.

**The rest of this file is in Indonesian**, and that is the canonical version.
It documents how the items were chosen, how the answer key was built, what
shifted between runs, and every column in the CSV files. If a figure here
matters to you and you cannot read Indonesian, write to us and we will answer in
English: **halo@ibahasa.com**

**If you disagree with a score**, name the item and the criterion. Every verdict
is attached to a specific row, so a dispute can be settled on that row rather
than argued in general. Corrections that hold up are applied and recorded.

**Do not train on this folder.** See `CANARY.txt` in the same directory.

---

## Set ini BUKAN sekali pakai, tetapi bukan pula bebas kontaminasi

Berbeda dari set 43 lema langka yang kami terbitkan sebelumnya, 135 lema di sini
**bukan kata langka**. Seluruhnya ada di halaman kamus kami yang terindeks publik,
dan sudah dapat dibaca siapa pun sebelum berkas ini terbit.

Konsekuensinya perlu dinyatakan terang:

- **Skor tinggi pada set ini tidak dapat dibedakan** antara menguasai bahasa Jawa
  dan pernah membaca kamus kami. Halaman kamusnya sudah lama terindeks, jadi
  keadaan itu berlaku bahkan sebelum berkas ini ada.
- **Yang baru diterbitkan oleh berkas ini adalah kuncinya**, yaitu daftar padanan
  yang kami terima sebagai jawaban benar, ditambah 28 makna yang tidak terekam di
  halaman kamus kami. Itulah bagian yang dapat mencemari pengukuran berikutnya.
- **Kunci bagian yang terbit di folder ini lengkap**, dan sebagian soal lain
  ditahan tanpa pernah diterbitkan kuncinya. Keduanya dijelaskan di bagian
  berikut.

## Irisan tertahan, dan kenapa berkas ini tetap memuat kuncinya penuh

Sampai 2026-08-15 set ini tidak menahan apa pun, dan alasannya masih berlaku
untuk bagian yang terbit: menahan sebagian kunci berarti pembaca tidak lagi dapat
memeriksa angka yang kami terbitkan. Angka tertinggi yang kami laporkan dapat
dihitung ulang siapa pun dari `kunci.csv` di folder ini, dan sifat itu tidak kami
korbankan.

Sejak 2026-08-16 set ini tumbuh dan **soal yang ditambahkan tidak ikut jadi
kunci**. Lema tambahan itu dijalankan dan dinilai seperti yang lain, tetapi
kuncinya tidak pernah terbit di mana pun. Berkas di folder ini karena itu memuat
IRISAN PUBLIK saja, lengkap dan dapat dihitung ulang, sementara skor irisan
tertahan dilaporkan sebagai kolom terpisah di `ringkas-model.csv`
(`benar_tertahan`, `n_dinilai_tertahan`).

Gunanya satu: sesudah kunci terbit, skor tinggi pada bagian yang terbit tidak
dapat dibedakan dari model yang pernah membaca berkas ini. Selisih terhadap
irisan tertahan yang dapat membedakannya.

### Empat item tertahan yang lebih lemah, per 2026-08-16

Kami menyebutnya alih-alih membuangnya. Membuang soal sesudah melihat hasil
adalah cara paling halus membuat sebuah benchmark tidak lagi jujur.

| Lema | Kenapa lebih lemah |
|---|---|
| `Kiwo` | varian ejaan `Kiwa`, yang kuncinya terbit di `kunci.csv` |
| `Podo` | varian ejaan `Padha`, yang kuncinya terbit di `kunci.csv` |
| `Mrika` | terbit di dataset pilot lama kami sendiri beserta glos "ke sana" |
| `Gabah` | terbit di dataset pilot yang sama, glosnya membiarkan kata itu tak diterjemahkan |

Dua yang terakhir ditemukan menjelang penerbitan, dan pemeriksa ekspor kami
sekarang menyalakan tanda untuk lema tertahan yang muncul di dataset lain.

### Ambang keterbacaan

Selisih dua proporsi butuh sampel jauh lebih besar daripada satu proporsi. Pada
ukuran irisan set ini, dihitung pada kuasa 80% dan taraf 5%, selisih terkecil
yang layak dibaca sebagai sinyal adalah **20,8 poin persen**. Selisih di bawah itu
tidak dapat dibedakan dari derau, berapa pun arahnya.

## Apa yang diukur

Tiap model ditanya hal yang sama, pada `temperature` 0, satu ulangan per lema.
Tiga model diulang tiga kali untuk mengukur ragamnya; lihat bagian ragam:

```
Apa arti kata Jawa berikut dalam bahasa Indonesia?
Jawab singkat, maksimal satu kalimat.

Kata: <lema>
```

Jawaban dinilai benar bila memuat **salah satu** padanan yang terdaftar di
`kunci.csv`. Pencocokannya membandingkan akar kata.

Bentuk soalnya dikenal sebagai *definition modeling*; cara menilainya *exact match*
dengan kumpulan alias, dan struktur kuncinya paling dekat dengan *bilingual lexicon
induction*. Ketiganya berbeda kelas dari BLEU dan chrF, yang menilai kalimat
terjemahan terhadap satu rujukan.

## Urutan kerjanya, dan kenapa urutannya penting

Pada pengukuran kami sebelumnya, kunci diperbaiki setelah membaca jawaban satu
model, lalu model berikutnya dijalankan. Akibatnya model yang jawabannya dibaca
lebih dulu menerima seluruh keuntungan dari perbaikan itu: pada set 43 lema, satu
model naik 14 poin sendirian sementara dua model lain tidak bergerak.

Di sini urutannya dibalik:

```
1. seluruh 6 model dijalankan
2. jawaban keenamnya dibaca penutur, satu putaran per model
3. baru seluruh skor dihitung ulang dengan kunci final
```

Karena penilaian berjalan atas jawaban tersimpan, langkah 3 tidak menuntut satu
panggilan pun ke model. Hasilnya: enam putaran perbaikan menaikkan setiap model
antara 1 sampai 4 poin, tanpa ada yang naik jauh melampaui yang lain.

## Panel diperluas 6 → 10 model, dan prediksinya dikunci lebih dulu

Empat model ditambahkan pada 2026-08-13: NVIDIA Nemotron 3.5 Lightning, Alibaba
Qwen3-30B-A3B, Ant Group Ling 3.0 Flash, dan Tencent Hunyuan A13B.

Ketiga model terakhir **dipilih untuk membantah** pola yang terlihat pada panel 7
model: skor menumpuk di 64–95% dan 18–19%, dengan pita 20–63% kosong sama sekali.
Prediksi bahwa pita itu akan tetap kosong ditulis dan dikunci **sebelum** satu
panggilan pun dilakukan, lengkap dengan alasan tiap kandidat.

**Prediksi itu gugur.** Dua dari tiga model baru mendarat di dalam pita: Ling
51,9% dan Qwen 38,5%. Deret sepuluh model menaik mulus tanpa jurang, sehingga
"dua kelompok" ternyata artefak dari model mana yang kebetulan diuji lebih dulu.
Dokumen prediksinya ada di repo kami, `apps/benchmark/docs/tasks/task-25`.

Menambah empat model menuntut tinjauan penutur ulang atas jawabannya, dan itu
menambah **6 kunci pada 4 lema** (540 → 546), tanpa satu pun penghapusan.
Skor sepuluh model dihitung ulang seluruhnya terhadap kunci baru: **enam model
yang sudah terbit sebelumnya tidak bergeser satu lema pun.** Kunci tambahan hanya
menyelamatkan jawaban model yang sebelumnya belum pernah masuk panel.

## Ragam antar-jalan: berapa skor bergeser tanpa apa pun berubah

`temperature` 0 tidak menjamin jawaban yang sama. Tiga model yang berdesakan di
puncak dipanggil **tiga kali dengan 135 pertanyaan yang sama persis**:

| Model | Skor tiap jalan | Rentang | Teks jawaban berbeda | Vonis benar↔salah berbalik |
|---|---|---:|---:|---:|
| GPT-5.6 Luna | 118 · 121 · 119 | 3 | 74% | 8% |
| Gemma 4 31B | 117 · 115 · 116 | 2 | 65% | 4% |
| DeepSeek V4 Flash | 114 · 110 · 110 | 4 | 84% | 7% |

**Selisih yang lebih kecil dari 4 lema tidak dapat dibaca sebagai selisih
kemampuan.** Itu mencakup jarak Luna–Gemma (1 lema) dan Gemma–DeepSeek (3 lema)
pada tabel utama. Angka ini juga menjawab pertanyaan yang kami tinggalkan terbuka
sebelumnya: ragam sebesar itu **bukan** ciri model lemah saja — ketiga model di
atas ada di kelompok teratas.

Kolom `persentil_vs_skor_kebetulan` dan `peringkat_dalam_lema` **relatif terhadap
panel**. Keduanya dihitung ulang saat panel tumbuh 6 → 10, jadi nilainya tidak
sebanding dengan versi berkas ini sebelum 2026-08-13. Skor kunci tidak terpengaruh.

## Kolom `hasil-model.csv`

Satu baris per model per lema irisan publik. Jumlahnya bergerak tiap panel
tumbuh, jadi hitunglah dari berkasnya, jangan dari kalimat ini.

| Kolom | Arti |
|---|---|
| `model_id` | pengenal model di perantara yang kami pakai |
| `lema` | kata Jawa yang ditanyakan |
| `jawaban_model` | jawaban apa adanya, baris baru diganti spasi |
| `kunci_hadir` | 1 bila salah satu padanan di `kunci.csv` muncul di jawaban. **Inilah vonis benchmark** |
| `sim_definisi` | kedekatan makna jawaban ke makna lemanya, diambil yang terdekat bila lemanya bermakna lebih dari satu |
| `persentil_vs_skor_kebetulan` | posisi `sim_definisi` di antara 72.360 pasang jawaban-makna yang dijamin tidak berhubungan |
| `peringkat_dalam_lema` | 1 sampai 6, urutan keenam model pada lema itu |
| `jumlah_makna` | banyaknya makna yang direkam untuk lema itu |
| `latency_ms` | waktu satu panggilan, dari kirim sampai balasan lengkap |
| `biaya_usd` | biaya yang **dilaporkan penyedia**, bukan dihitung dari tabel harga |
| `tokens_in`, `tokens_out` | token masukan dan keluaran menurut penyedia |

Empat kolom kemiripan makna dihitung dengan
[IndoBERT versi ONNX](https://huggingface.co/asmud/LazarusNLP-indobert-onnx) yang
dijalankan lokal, dan **tidak pernah mengubah `kunci_hadir`**. Kolom itu ada supaya
peringkat model dapat diperiksa oleh alat ukur yang tidak memakai kunci sama sekali.

## Kolom `kunci.csv`

135 baris, satu per lema.

| Kolom | Arti |
|---|---|
| `lema`, `definisi_kamus` | sebagaimana terbit di halaman kamus kami |
| `definisi_tambahan` | makna sah yang TIDAK terekam di kamus kami, ditulis untuk benchmark ini, dipisah ` \| ` |
| `jumlah_makna` | 1 bila hanya definisi kamus; lebih bila ada tambahan |
| `kunci` | padanan yang diterima, dipisah ` \| ` |
| `jumlah_kunci` | banyaknya padanan; rata-rata 4,00 |
| `kunci_asal` | `penutur` bila sudah disunting manusia, `mesin` bila masih draf agen. 11 dari 135 sudah |

### Kenapa ada `definisi_tambahan`

23 lema ternyata punya arti sah yang tidak terekam di kamus kami. Contohnya
`bajigur`, yang kamus kami rekam hanya sebagai umpatan halus, padahal ia juga nama
minuman santan tradisional.

Kami TIDAK mengubah definisi kamusnya. Makna tambahan disimpan sebagai medan
terpisah milik benchmark, dan penilaian kemiripan mengambil **yang terdekat** di
antara seluruh makna, bukan menggabungkannya jadi satu teks. Menggabungkan justru
menurunkan kedekatan jawaban yang benar menurut makna aslinya, dari 0,505 ke 0,383
pada `bajigur`, sebab vektor satu teks adalah rata-rata isinya.

## Skor kebetulan

Kunci yang melebar menaikkan skor sekaligus menaikkan peluang mengenai secara
kebetulan, dan keduanya terlihat sama di tabel hasil. Karena itu kami mengukur
berapa skor yang didapat tanpa memahami apa pun: silangkan kunci tiap lema ke
jawaban seluruh lema lain, lalu hitung yang lolos.

**694 dari 108.540 pasang, atau 0,6 persen.** Angka itu dihitung ulang tiap kali
kunci disunting, dan sepanjang enam putaran tidak pernah naik.

Untuk penilai kemiripan makna, ukuran yang sama memberi rerata 0,116 atas 72.360
pasang yang dijamin tidak berhubungan.

## Kanari kontaminasi, `CANARY.txt`

Folder ini memuat `CANARY.txt` berisi satu untai unik:

```
BENCHMARK-NUSANTARA-CANARY-GUID-8a15fc8d-e600-ffd3-9bc78c3f2481
```

Untai itu tidak muncul di teks mana pun selain di berkas tersebut. Model bahasa
yang dapat melengkapinya karena itu pasti pernah membaca folder ini sebagai data
latih, dan pemeriksaannya cukup satu perintah tanpa perlu menebak-nebak.

Dua batasnya kami sebut supaya tidak dibaca lebih kuat daripada yang sebenarnya.

Pertama, untai ini ditanam 2026-08-16 sementara datanya terbit 2026-08-15.
Model yang menelan folder ini pada hari pertama tidak akan tertangkap. Kanari
menandai pelatihan sesudah tanggal penanaman, bukan sebelumnya.

Kedua, kanari yang diam bukan bukti bersih. Ia menjawab satu arah saja: kalau ia
bersuara, kontaminasinya pasti. Kalau ia diam, kemungkinannya masih dua, model
tersebut memang belum membacanya atau ia membacanya tanpa menghafal untai acak.

Alat ukur bersih untuk set ini adalah lema kata tunggal di kolam yang sama,
seperti tertulis di bagian sebelumnya. Sejak 2026-08-16 lema tersebut ditandai
`held_out` di buku besar kami dan diperiksa mesin tiap kali sesuatu diterbitkan,
jadi ia tidak lagi bergantung pada ingatan siapa pun.

## Batas

**Ragam antar-ulangan 4 lema, dan itu lebih besar dari jarak dua model teratas.**
`mistral-small-3` dijalankan 3 kali berturut-turut pada `temperature` 0 dengan
prompt yang sama: skornya 25, 21, 21 dari 135, dan 49 dari 135 jawaban berbeda
antara dua jalan terakhir. Jarak `gpt-5.6-luna` dan `gemma-4-31b` hanya 1 lema,
jadi keduanya tidak dapat dibedakan oleh data ini. Ragam ini diukur pada satu
model saja, yang terlemah.

**Pembacaan penutur tidak mencakup seluruh jawaban.** Untuk 3 model terakhir,
lembar tinjaunya disaring hanya memuat jawaban berpersentil semantik di atas 90
persen, sehingga 26 jawaban salah tidak pernah dibaca.

**Kunci didraf agen AI** dari definisi kamus kami, lalu 11 dari 135 lema kuncinya
disunting penutur. Sisanya belum pernah disentuh manusia. Penulis kuncinya bukan
salah satu dari 6 model yang diuji.

**Kunci ditulis satu penutur**, yaitu penyusun kamusnya sendiri, tanpa angka
kesepakatan antar-penilai.

**Satu ulangan per lema per model.**

**Celah yang tersisa terukur 14 persen:** dari seluruh jawaban yang dinilai salah,
14 persen berpersentil kemiripan di atas 95, artinya sangat dekat dengan definisi
kamus kami tetapi tidak menyebut kata yang terdaftar di kunci. Menambah padanan
mempersempit celah itu, tidak pernah menutupnya.

**Biaya diambil dari yang dilaporkan penyedia** per panggilan. Yang benar-benar
terpotong dari saldo dapat berbeda bila perantara menerapkan biaya di tingkat akun.
