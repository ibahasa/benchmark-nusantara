# id-N: satu tugas normalisasi, tiga rumusan prompt, empat model AI — angka saja

**Tanggal:** 2026-08-13 · **Penulis:** Benchmark Team · **Lisensi:** CC BY 4.0
**Berkas:** `export-id-N-ringkas-model.csv`, `export-id-N-per-item.csv`,
`export-id-N-rumusan.csv`
**Sumber:** set normalisasi teks informal Indonesia milik kami, 69 kalimat,
seluruhnya diverifikasi dua penutur asli

Pengukuran kami sendiri atas 4 model yang dipanggil lewat satu perantara, pada
item dan kunci yang **identik** di ketiga rumusan. Satu-satunya yang berubah
antar-arm adalah kalimat instruksinya.

---

## Kalimat dan kuncinya TIDAK diterbitkan, dan itu disengaja

Dataset ini tidak memuat satu pun kalimat sumber, kata rujukan, atau jawaban
model. Yang ada cuma angka, ditambah `item_id` buram seperti `id-n1-008`.

Dua alasan, dan keduanya berlaku:

1. **20 dari 69 item bertanda `held_out`.** Item held-out ada justru supaya tidak
   pernah bocor ke data latih; menerbitkannya menghancurkannya permanen, berikut
   kemampuan mengukur kontaminasi dengan item itu.
2. **49 sisanya pun ditahan.** id-N adalah set kerja normalisasi kami dan akan
   dipakai lagi. Menerbitkan kuncinya berarti membakar seluruh setnya untuk
   pengukuran berikutnya, bukan cuma bagian held-out-nya.

Berkas ini karena itu **tidak dapat dipakai menjalankan ulang model**, sebab
promptnya memuat kalimat yang kami tahan. Itu bayaran yang kami pilih dengan
sadar, dan kami menyatakannya di muka alih-alih membiarkan pembaca menemukannya
sendiri.

## Berkas ini potret, bukan riwayat

Eksportirnya menulis ulang seluruh berkas dari buku besar. Menjalankan model
kelima menambah baris; menjalankan ulang model yang sama **menimpa** barisnya.
Riwayat perubahannya ada di riwayat git repo ini — kutiplah SHA commit, bukan
nama berkas.

Satu hal yang SHA commit tidak jawab: sebuah berkas dapat memuat baris dari
beberapa tanggal sekaligus. Karena itu tiap baris `export-id-N-per-item.csv` membawa
`waktu_amat` dan `cap_token` sendiri, dan `export-id-N-ringkas-model.csv` membawa rentang
`waktu_amat_awal`–`waktu_amat_akhir`. Kolom `dijalankan_pada` berbeda artinya:
itu waktu berkasnya disusun, bukan waktu modelnya dipanggil.

Pada rilis 2026-08-13 seluruh 12 label diukur dalam satu hari, dan `cap_token`
seragam 600 kecuali Ling — lihat batasan di bawah.

## Yang tetap dapat diverifikasi pembaca

`item_id` mengikat baris antar-berkas, jadi tanpa tahu isi satu item pun pembaca
tetap dapat:

- menghitung ulang **seluruh** tabel A/B dari `export-id-N-per-item.csv`, termasuk setiap
  angka yang kami kutip
- menguji apakah selisih dua rumusan signifikan — pasangannya per item, jadi
  uji McNemar berlaku langsung
- menemukan sendiri item yang tak pernah dijawab benar oleh model mana pun
- memisahkan hasil held-out dari non-held-out lewat kolom `held_out`

Setiap angka di artikel kami turun dari ketiga berkas ini. Tidak ada angka yang
bersandar pada data yang kami tahan.

## Apa yang diukur: satu skor yang ternyata dua kemampuan

Tugas id-N: mengubah teks informal berbahasa Indonesia menjadi bentuk bakunya.
Aturan kuncinya diukur dari 69 pasang sumber–rujukan, bukan ditetapkan lewat
pendapat:

| Bentuk perubahan | Jumlah |
|---|---:|
| singkatan dipulihkan (`hrs` → `harus`) | 128 |
| kata disubstitusi (`gak` → `tidak`) | 40 |

Kata yang **sudah** baku tidak pernah diganti: `aku` bertahan 18 dari 18 kali,
`kamu` 6 dari 6. Kata yang **tidak** baku selalu diganti: `gak` 7 dari 7,
`pengen`/`bgt`/`seneng` 5 dari 5. Aturannya karena itu tunggal dan tanpa
pengecualian: *jadikan setiap kata baku; yang sudah baku dibiarkan.* Metadata
set menyebutnya `norm_basis: prescriptive`, dengan KBBI sebagai dasar.

Dari situ skornya dapat diurai jadi dua kemampuan yang bergerak berlawanan arah:

- **A** — 40 substitusi yang kunci LAKUKAN. Apakah kata rujukan muncul di jawaban?
- **B** — 63 kata yang kunci PERTAHANKAN. Apakah model membiarkannya?

Keduanya dibaca dari kunci, bukan dari daftar kata baku karangan siapa pun.

## Batasan yang perlu dinyatakan

**B dibatasi pada kata yang tergoda.** Dari 243 kata yang bertahan di rujukan,
hanya 63 yang setidaknya satu model benar-benar ganti. Sisanya — `hari`, `buku`
— tidak seorang pun tergoda menyentuh, dan memasukkannya cuma mengencerkan
penyebut sampai semua model tampak patuh. Penyebut 63 itu dihitung dari seluruh
label sekaligus, jadi sama untuk setiap model dan tetap sebanding. Angka B untuk
penyebut 243 dapat dihitung sendiri dari `export-id-N-per-item.csv` bila pembaca tidak
sependapat dengan pilihan ini.

**Ling 3.0 Flash tidak setara ongkosnya.** Pada `open-py3` ia berulang kali habis
anggaran token tanpa mengeluarkan jawaban, dan baru selesai di batas 24.000
token sesudah 600, 2.400, dan 9.600 gagal. Item lain di rumusan yang sama selesai
di 600. Skornya sah dan lengkap; latensi dan biayanya tidak dapat dibandingkan
apa adanya dengan tiga model lain. Pada `open-py2` ia berhenti di 67 dari 69 item.

**Empat model, bukan panel.** Ini bukan papan peringkat. Keempatnya dipilih
karena murah dan cepat, supaya tiga arm penuh terjangkau. Kesimpulannya tentang
rumusan prompt, bukan tentang model mana yang terbaik.

**Penilaiannya kecocokan persis sesudah normalisasi** (`open-py1` sebagai nama
penilai, jangan tertukar dengan nama rumusan). Jawaban yang benar tetapi berbeda
kata dinilai salah. Kolom kemiripan makna berbasis IndoBERT kami hitung terpisah
dan **tidak** pernah mengubah vonis.

**Enam item tak pernah dijawab benar oleh model mana pun** di ketiga rumusan.
Dua pengecualian kunci ikut menyumbang: `dikerjain` dan `ngerti` dibiarkan di
rujukan padahal keduanya tidak baku, jadi keduanya melanggar aturan kunci yang
kami nyatakan di atas. Kami melaporkannya alih-alih membetulkan kuncinya
belakangan supaya angkanya lebih rapi.

**Alias model mengambang.** `model` di berkas ini nama pendek kami. Penyedia
dapat memindahkan alias itu ke bobot yang berbeda tanpa memberi tahu; angka di
sini berlaku untuk yang melayani pada 2026-08-13.

## Kontaminasi

Metadata set menandai `contamination_risk: low-medium`. Kalimatnya tidak pernah
tayang sebagai halaman web, tetapi dasarnya semula data publik yang kemudian
digubah dan diverifikasi ulang; bagian yang masih sama dengan aslinya tetap
berpeluang ada di data latih. Set memuat `canary_guid` untuk mendeteksi
kebocoran di kemudian hari, dan GUID itu **tidak** disertakan dalam berkas ini.

Karena kalimatnya ditahan, penerbitan ini tidak menambah risiko kontaminasi id-N
sama sekali.

## Verifikator

Seluruh 69 item diverifikasi dua penutur asli, verifikator kedua **Hasan Basri**,
guru SMA di Semarang. Tidak ada item yang bersandar pada satu verifikator.

## Cara menghitung ulang

```python
import pandas as pd
d = pd.read_csv("export-id-N-per-item.csv")
g = d.groupby(["model", "rumusan"])[["kunci_hadir", "a_kena", "a_total",
                                     "b_kena", "b_total"]].sum()
g["A"] = g.a_kena / g.a_total
g["B"] = g.b_kena / g.b_total
print(g[["kunci_hadir", "A", "B"]])
```

Hasilnya harus sama persis dengan `export-id-N-ringkas-model.csv`.
