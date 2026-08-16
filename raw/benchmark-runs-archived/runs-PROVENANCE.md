# benchmark-runs-archived: 28 jalan benchmark, 2026-07-25 sampai 2026-08-06

**ARSIP.** Kumpulan ini tidak bertambah lagi.

**Lisensi:** CC BY 4.0 · **Berkas:** satu `meta.json` dan satu `summary.md` per jalan

---

## In English

**What this is.** Twenty-eight benchmark runs recorded between 2026-07-25 and
2026-08-06, two files each: the parameters the run was launched with, and a
human-readable results table. It is a working log, not a leaderboard.

**Read the date range first.** This dataset covers one particular way of
recording runs, and that method was retired on 2026-08-06. **Nothing after that
date appears here, and nothing after that date is missing from our published
figures either.** Later runs are recorded differently and are published inside
the dataset of the set they belong to, alongside that set's answer key and
provenance. If you want current results, start at `INDEX.md` and pick the set,
not this folder.

**What it does not contain.** No question text, no answer keys, no model answers.
Aggregate counts, run parameters, and prose notes only.

**Rest of this file is in Indonesian, which is the canonical version.** Write to
**halo@ibahasa.com** if a figure here matters to you and you cannot read it.

---

## Isinya

Dua berkas per jalan.

`meta.json` memuat pengenal jalan, tanggal, versi set yang dipakai, templat
prompt, daftar model, dan catatan penulisnya. Cukup untuk menyusun ulang jalan
yang sama.

`summary.md` memuat tabel hasil yang dapat dibaca manusia: jumlah panggilan,
galat, kegagalan format, skor, median latensi, token, dan biaya per model.
Sebagian juga memuat uji dua proporsi beserta perhitungan kuasanya, sebab
selisih dua model tidak berarti apa-apa tanpa keduanya.

## Batas tanggal, dan kenapa ia ada

Kumpulan ini merekam **satu cara mencatat jalan yang kami tinggalkan pada
2026-08-06**. Sesudah tanggal itu, pencatatannya pindah ke buku besar per set,
dan buku besar itulah yang menyuplai dataset lain di repo ini.

Jadi berhentinya bukan karena benchmark berhenti berjalan, dan bukan pula ada
hasil yang kami tahan. Angka sesudah 2026-08-06 terbit lengkap, hanya saja
tempatnya di dataset set masing-masing, bersama kunci jawaban dan provenance-nya
sendiri.

Kami menyebutnya di sini karena kumpulan yang berhenti tanpa keterangan terbaca
seperti data yang hilang, dan itu tuduhan yang pantas kalau tidak dijawab.

## Yang TIDAK ada di berkas ini

Tidak ada kalimat soal, tidak ada kunci jawaban, dan tidak ada teks jawaban
model. Yang ada cuma cacahan, parameter, dan catatan.

Sebagian besar jalan di sini memakai versi set bertanda `draft`, yaitu set yang
soalnya masih bergerak saat itu. Angkanya karena itu **tidak sebanding** dengan
angka yang terbit di dataset set, dan jangan diadu langsung.

## Satu jalan bertanda BATAL

`runs-2026-08-02-id-B-ab-A-terpotong-BATAL` sengaja tetap ada. Jalan itu gugur
karena keluarannya terpotong, dan penggantinya ada di jalan `-ulang` pada tanggal
yang sama.

Jalan yang gugur dibuang diam-diam akan membuat riwayat ini terbaca lebih rapi
daripada kenyataannya. Kami lebih memilih riwayat yang jujur daripada riwayat
yang rapi, dan pembaca yang menghitung jumlah jalan berhak tahu satu di antaranya
tidak dipakai.

## Perantara

Sebagian besar model dipanggil lewat satu perantara komersial, dan `meta.json`
menyebut namanya di medan `provider`. Satu jalan memakai API penyedia secara
langsung, dan itu pun tercatat di medan yang sama.

Perbedaan itu berpengaruh pada latensi dan biaya, bukan pada skor.

## Cara mengutip

Pakai permalink yang dipatok ke commit, bukan ke `main`:

```
https://github.com/ibahasa/benchmark-nusantara/blob/<commit-sha>/raw/benchmark-runs/<berkas>
```

`sha256` tiap berkas ada di `MANIFEST.json`.

## Kalau menurut Anda ada yang keliru

Sebut berkas dan barisnya. Lihat `CONTRIBUTING.md` di akar repo, atau tulis ke
**halo@ibahasa.com**.
