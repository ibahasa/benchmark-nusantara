# Pilot terjemahan Jawa ke Indonesia: dua model, 20 kalimat, satu pengadil manusia

**Tanggal:** 2026-08-10 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `hasil-model.csv`, `adu-buta.csv`
**Sumber:** contoh kalimat berbahasa Jawa dari kamus kami, seluruhnya berstatus
terverifikasi manusia dan sudah terbit di halaman kamus publik sejak Februari 2026

Pengukuran kami sendiri atas dua model yang dipanggil lewat satu perantara.
Kalimat sumber dan glosnya milik kami. Tidak ada sumber pihak ketiga di dalamnya,
sehingga tidak ada syarat lisensi yang terseret.

---

## Apa yang diukur, dan apa yang ternyata terukur

Tiap kalimat Jawa disodorkan ke model dengan satu perintah: terjemahkan ke bahasa
Indonesia, jawab hanya dengan kalimatnya. Glos yang sudah menyertai kalimat itu
di kamus dipakai sebagai kunci jawaban.

Rancangan itu **tidak sah sebagai benchmark**, dan berkas ini menerbitkan buktinya
alih-alih menyembunyikannya. Pada adu buta 20 pasang, 11 di antaranya dinilai
seri oleh pengadil manusia. Kunci jawaban yang tidak lebih baik daripada yang
dinilainya mengukur kesepakatan pilihan kata, bukan kemampuan.

Angka pada `hasil-model.csv` tetap berguna dibaca sebagai catatan perilaku model,
tetapi **tidak boleh dibaca sebagai peringkat kemampuan berbahasa Jawa**.

## Kolom `hasil-model.csv`

Satu baris per pasangan model dan kalimat. 40 baris, yaitu 2 model dikali 20
kalimat.

| Kolom | Arti |
|---|---|
| `model_id` | pengenal internal kami untuk model itu |
| `lema` | kata Jawa yang jadi poros contoh kalimatnya di kamus |
| `kalimat_jawa` | kalimat yang disodorkan ke model |
| `glos_indonesia` | glos yang menyertai kalimat itu di kamus, dipakai sebagai kunci |
| `jawaban_model` | jawaban model, sesudah perancah seperti `Terjemahan:` dibuang |
| `cocok_persis` | 1 bila jawaban sama persis dengan glos sesudah huruf besar dan tanda baca disamakan |
| `f1_kata_isi` | F1 kata isi jawaban terhadap kata isi glos, sesudah kata fungsi bahasa Indonesia dibuang |
| `chrf` | chrF, F-score n-gram aksara, n maksimum 6 dan beta 2, tanpa daftar kata fungsi |
| `latency_ms` | waktu satu panggilan, dari kirim sampai balasan lengkap |
| `biaya_usd` | biaya yang **dilaporkan penyedia** untuk panggilan itu, bukan dihitung dari tabel harga |
| `tokens_in`, `tokens_out` | token masukan dan keluaran menurut penyedia |

`cocok_persis` bernilai 1 pada 0 dari 20 jawaban model murah. Itu bukan cacat
model, melainkan cacat penilainya, dan salah satu temuan utama pengukuran ini.

## Kolom `adu-buta.csv`

Satu baris per kalimat. 20 baris.

| Kolom | Arti |
|---|---|
| `no` | nomor urut soal pada lembar penilaian |
| `lema`, `kalimat_jawa` | sama dengan berkas di atas |
| `opsi_a`, `opsi_b` | dua terjemahan yang disandingkan |
| `asal_a`, `asal_b` | `glos_kamus` atau `jawaban_model`. **Tidak terlihat oleh pengadil** saat menilai |
| `pilihan` | `a`, `b`, atau `sama`, sebagaimana ditandai pengadil |
| `menang` | `glos_kamus`, `jawaban_model`, atau `seri` |
| `catatan_pengadil` | alasan yang ditulis pengadil, apa adanya |

Posisi kedua opsi **diacak per soal**. Tanpa itu, kolom yang selalu berisi glos
akan terbaca sebagai pola sebelum soal kesepuluh dan mencemari sisa penilaiannya.
Glos kamus berada di posisi A pada 11 dari 20 soal.

## Yang TIDAK ada di berkas ini, dan kenapa

**Tidak ada soal tertahan.** Seluruh 20 kalimat berasal dari halaman kamus yang
sudah terbit sejak Februari 2026, sehingga menerbitkannya di sini tidak menambah
satu pun paparan yang belum ada. Tidak ada `item_id`, tidak ada versi set, dan
tidak ada kunci jawaban tertahan yang dapat direkonstruksi dari isinya.

**Ini bukan set benchmark, dan tidak boleh dipakai sebagai set benchmark.** Kalau
dimensi ini kelak dibangun sungguhan, soalnya wajib ditulis dari kalimat yang
belum pernah terbit, dan berkas ini tidak boleh jadi sumbernya.

**Tidak ada ulangan.** Tiap kalimat dijalankan sekali per model pada
`temperature` 0, sehingga ragam antar-ulangan tidak terukur sama sekali.

## Batas yang melekat

Satu pengadil, yaitu penyusun kamusnya sendiri, sehingga tidak ada angka
kesepakatan antar-penilai. Dua dari 20 glos ditulis penyusun benchmark, bukan
diambil dari kamus, sebab kalimatnya memang belum berglos; keduanya ditandai
lewat kolom `lema` `mbok menawa` dan `ora ilok`.

Satu arah terjemahan saja. Arah sebaliknya, dari bahasa Indonesia ke bahasa Jawa,
menuntut pemilihan tingkat tutur dan belum diuji sama sekali.

Selisih 5 lawan 4 pada soal yang tidak seri tidak menanggung kesimpulan apa pun.
Dari 9 soal yang menghasilkan keputusan, sebaran itu yang paling mungkin muncul
kalau kedua sisi memang setara.
