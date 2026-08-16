# Agregat per model: token keluar, latensi, throughput tersirat

**Tanggal:** 2026-08-05 · **Penulis:** agen benchmark · **Lisensi:** CC BY 4.0
**Berkas:** `agregat-model.csv`
**Sumber:** tabel `benchmark_runs`, seluruh run yang diekspor ke `apps/benchmark/runs/`

Pengukuran kami sendiri atas model yang dipanggil lewat satu perantara. Tidak ada
sumber pihak ketiga di dalamnya, sehingga tidak ada syarat lisensi yang terseret.

---

## Kolom

| Kolom | Arti |
|---|---|
| `model_id` | pengenal internal kami untuk model itu |
| `rerata_tokens_out` | rerata token keluaran per panggilan |
| `rerata_tokens_in` | rerata token masukan per panggilan |
| `rerata_latency_detik` | rerata waktu satu panggilan, dari kirim sampai balasan lengkap |
| `median_latency_detik` | median waktu itu. **Ini angka yang sebaiknya dipakai**, lihat di bawah |
| `tokens_per_detik_median` | `rerata_tokens_out` dibagi `median_latency_detik` |
| `n_panggilan` | jumlah panggilan berhasil yang masuk hitungan |
| `n_run` | jumlah run berbeda yang menyumbang |

## Yang TIDAK dihitung, dan kenapa

**Panggilan yang gagal dibuang seluruhnya** (`error IS NULL`). Ini bukan pilihan
kosmetik; tanpanya berkas ini akan memuat angka yang salah.

Sampai 2 Agustus 2026, harness kami menulis `0` pada kolom token untuk panggilan
yang gagal. Nol menyatakan sesuatu diukur dan hasilnya nol, padahal tidak ada yang
pernah diukur. Sejak tanggal itu kolomnya ditulis NULL, tetapi baris lama tetap
berisi 0 dan **tidak** tersaring oleh pemeriksaan NULL.

Akibatnya bila baris gagal ikut dihitung:

| Model | Ikut baris gagal | Hanya panggilan berhasil |
|---|---:|---:|
| `kimi-k2.6` | 24,8 detik | **15,9 detik** |
| `qwen-3.5-flagship` | 18,1 detik | **15,3 detik** |

Satu baris gagal dari 31 menaikkan latensi kimi **56 persen**.

**Tiga model tidak muncul sama sekali di berkas ini**, sebab seluruh panggilannya
gagal dan tidak ada satu pun pengukuran yang tersisa:

| Model | Panggilan | Berhasil |
|---|---:|---:|
| `gemini-3.1-pro` | 32 | 0 |
| `mistral-large-4` | 32 | 0 |
| `deepseek-chat` | 8 | 0 |

Menampilkannya sebagai "0 token, 0,0 token per detik" akan terbaca sebagai
pengukuran, padahal artinya model itu tidak pernah menjawab sekali pun.

## Kenapa median disertakan, dan kenapa ia yang sebaiknya dipakai

`latency_ms` mengukur waktu dinding satu panggilan, dan itu **termasuk jeda tunggu
percobaan ulang di dalam klien** ketika penyedia menjawab 429 atau 5xx. Segelintir
panggilan yang kebetulan menabrak penyedia yang sedang penuh karenanya membawa
latensi puluhan detik, dan rerata ikut terseret.

Seberapa jauh, diukur 2026-08-05:

| Model | Rerata | Median | Rerata lebih tinggi |
|---|---:|---:|---:|
| `gpt-5.4-pro` | 30,5 dtk | 12,1 dtk | **152%** |
| `claude-haiku-4-5` | 2,4 dtk | 1,0 dtk | **149%** |
| `qwen-3.5-flagship` | 15,3 dtk | 9,8 dtk | 56% |
| `mistral-small-3.2-24b` | 1,0 dtk | 1,0 dtk | 4% |

Akibatnya bisa membalik kesimpulan. Pada run 5 Agustus 2026, `claude-haiku-4-5`
tampak **52 persen lebih lambat** dari `claude-sonnet-4-6` menurut rerata (2,4
lawan 1,6 detik), padahal menurut median ia **32 persen lebih cepat** (1,0 lawan
1,4 detik). Penyedia sedang mengembalikan 529 selama giliran haiku, dan seluruh
selisih itu adalah jeda tunggu, bukan kecepatan model.

Kolom rerata tetap disertakan karena itu yang biasa diharapkan orang, tetapi untuk
membandingkan model, pakai mediannya.

## Batas yang melekat pada angka ini

- **`tokens_per_detik` di sini bukan throughput murni.** Ia dihitung dari token
  keluaran dibagi waktu panggilan penuh, sehingga memasukkan jeda sebelum token
  pertama. Untuk model yang menjawab pendek, jeda itulah hampir seluruh waktunya,
  dan angka token per detik jadi kecil bukan karena modelnya lambat mengetik.
- **Jumlah panggilan sangat timpang**, dari 15 sampai 2.410. Model dengan
  `n_panggilan` kecil hanya pernah ikut satu run.
- **Rerata lintas run mencampur beban kerja yang berbeda.** Sebagian run adalah
  soal pilihan ganda berjawab satu huruf, sebagian item terbuka yang menuntut
  kalimat utuh. Panjang keluaran sebuah model karenanya sebagian ditentukan
  soal yang kebetulan ia terima.
- **Angkanya bergerak.** Tiap run baru mengubah reratanya. Tanggal di kepala berkas
  ini adalah tanggal pembacaannya.

## Cara membangkitkan ulang

```sql
SELECT model_id,
       round(avg(tokens_out)) AS rerata_tokens_out,
       round(avg(tokens_in))  AS rerata_tokens_in,
       round(avg(latency_ms)/1000.0,1) AS rerata_latency_detik,
       round(avg(tokens_out)/(avg(latency_ms)/1000.0),1) AS tokens_per_detik,
       count(*) AS n_panggilan,
       count(DISTINCT run_id) AS n_run
FROM benchmark_runs
WHERE error IS NULL AND tokens_out IS NOT NULL AND latency_ms IS NOT NULL
GROUP BY model_id ORDER BY avg(tokens_out) DESC;
```

Syarat `error IS NULL` wajib ada. Menghilangkannya mengembalikan baris gagal
beserta angka yang salah di tabel atas.
