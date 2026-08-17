# Pemahaman slang Indonesia: ringkasan per model

**Tanggal:** 2026-08-17 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `ringkas-model.csv`, `per-item.csv`
**Sumber:** set id-B milik kami

Berkas ini dihasilkan `core/ekspor_riset.py` dan memuat ANGKA saja: tidak ada
item, tidak ada kunci jawaban. Soal dan kuncinya kami tahan, jadi dataset ini
TIDAK dapat dipakai menjalankan ulang model. Angkanya dapat dihitung ulang.
Pengukurannya tidak dapat diulang dari sini.

## In English

**What this is.** Indonesian slang comprehension. Models were shown a passage
flagged by a reader and asked to explain what it means. Two things are
measured at once: how often the explanation is right, and how often the model
invents a meaning that never existed. The model panel grows, so read the
current list from `ringkas-model.csv`. The set grew from 38 items to 60 on
2026-08-17 and the whole panel was re-run, so figures dated before that measure a
different set of questions and are not comparable line by line.

**Who scored it.** Machine-scored multiple choice, one call per item at
temperature 0. The answer cap is 600 tokens, raised to 2400 for the handful of
items where a model spent the whole budget reasoning before answering.

**Main limits.** Run-to-run variance was measured once, on 2026-08-17: one
model was run twice on the same day and gave an identical verdict on all 60 items.
That is one model on one day and does not license reading small gaps between
models as ability differences. The gap between the public and the withheld slice
needs to reach 36.8 points before this set can call it real, which is still above
the 30-point bar our own pages use. One model answered every item correctly, so
the ceiling here is the measuring instrument, not the model. Every item comes from
entries already published on ibahasa.com, which any crawler may have read. One row is a 4-bit quantised local model whose low score has two
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

Mengukur pemahaman bahasa gaul Indonesia. Model diberi potongan teks yang
disorot pembaca, lalu diminta menjelaskan artinya. Kami mengukur dua hal
sekaligus: seberapa sering penjelasannya tepat, dan seberapa sering model
mengarang arti yang tidak pernah ada.

Jumlah model di panel ini bertambah dari waktu ke waktu, jadi bacalah daftar
beserta cacahannya dari `ringkas-model.csv`, bukan dari kalimat di berkas ini.

## Set ini bertambah besar pada 2026-08-17

Dari 38 item jadi 60. Seluruh panel dijalankan ulang, bukan cuma item barunya,
sebab skor lama menjawab himpunan soal yang berbeda dan menempelkannya ke skor
baru menghasilkan angka yang tidak pernah diukur siapa pun.

Angka bertanggal sebelum 17 Agustus karena itu mengukur set yang lain. Keduanya
tetap kami simpan, dan `versi_soal` di `ringkas-model.csv` membedakannya. Jangan
membandingkan baris antar-versi soal.

Ke-22 item baru bersumber dari korpus kamus kami sendiri dan dari daftar
normalisasi slang milik mesin editor kami. Tingkat kesulitannya sebanding dengan
yang lama: dua model mencetak lebih rendah di item baru, satu lebih tinggi.

## Bagaimana angkanya dihasilkan

Satu panggilan per item. Suhu nol untuk seluruhnya, dan batas jawaban 600 token
yang dinaikkan ke 2400 pada sebagian kecil item, yaitu waktu sebuah model
menghabiskan seluruh jatahnya untuk menalar sebelum menjawab. Item yang terpotong
seperti itu selalu dipanggil ulang dengan batas lebih besar sebelum dipanen.

Satu model dijalankan dua kali pada hari yang sama untuk mengukur ragam
antar-panggilan. Barisnya bertanda `ulangan`. Sebagian besar model dipanggil lewat
satu perantara berbayar.
Model yang dijalankan di perangkat keras kami sendiri lewat Ollama bertanda
`biaya_usd` kosong, dan kosong di sana berarti tidak bertagihan, bukan gratis.

Kolom `biaya_usd` kosong berarti TIDAK ADA TAGIHAN untuk dicatat, bukan nol.
Model lokal berjalan di komputer yang kami beli dan listrik yang kami bayar, dan
tidak satu pun dari itu masuk ke angka mana pun di berkas ini. Kolom
`latensi_median_ms` untuk baris itu mengukur mesin kami, bukan layanan yang
pembaca dapat beli, jadi ia tidak sebanding dengan sembilan baris lainnya.

## Batas pembacaan angka ini

**Ragam antar-panggilan baru diukur sekali.** Pada 17 Agustus satu model
dijalankan dua kali di hari yang sama dan memberi vonis identik pada keenam puluh
itemnya, nol item berbeda. Satu model pada satu hari bukan bukti bahwa seluruh
panel sestabil itu, jadi selisih beberapa poin antar-model tetap tidak boleh
dibaca sebagai selisih kemampuan.

**Selisih irisan publik dan irisan tertahan baru terbaca mulai 36,8 poin.**
Angka itu dihitung dari ukuran kedua irisannya, 42 lawan 18. Penambahan item
menurunkannya dari 44,8 poin, dan ia masih di atas batas 30 poin yang dipakai
laman kami sendiri untuk memutuskan apakah persentase kedua irisan layak
ditampilkan berdampingan. Untuk menembus batas itu set ini perlu sekitar seratus
item.

**Satu model menjawab benar seluruh 60 item.** Untuk model sekelas itu, set ini
hanya dapat menyatakan bahwa tidak ada kesalahan yang terdeteksi, bukan seberapa
bagus. Langit-langitnya alat ukur kami, bukan modelnya.

**Seluruh item bersumber dari entri yang sudah tayang di ibahasa.com**, dan
robots.txt situs itu tidak memuat aturan apa pun. Perayap model mana pun boleh
sudah membacanya. Risiko kontaminasi set ini kami nyatakan TINGGI, dan irisan
tertahan tidak menghapusnya, sebab irisan itu bersumber dari kolam yang sama.

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

**Sengaja TIDAK ada di sini.** Kalimat soal, kunci jawaban, teks jawaban model,
dan opsi yang dipilih model.

Kolom terakhir itu yang paling menentukan pada tugas pilihan ganda. Opsi pilihan
model yang terbit bersama vonis membocorkan kuncinya seketika: satu baris berskor
1 sudah cukup untuk tahu opsi mana yang benar. Pemeriksa ekspor kami menolak
berkas apa pun yang memuat kolom semacam itu pada set pilihan ganda.

**Baris irisan tertahan juga tidak ada.** Agregat irisan publik sudah dapat
dihitung ulang tanpanya, sementara menerbitkannya berarti menyebutkan butir mana
yang jadi cadangan beserta vonis tiap model di atasnya.

Karena soal dan kuncinya ditahan, berkas ini cukup untuk memeriksa **aritmetika**
kami, bukan **penilaian** kami. Vonis tiap baris tetap harus dipercaya.
