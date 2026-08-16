# Hasil run `2026-08-02-id-W-3x-ulangan`

**run_id:** `96d9f019-e36d-4cde-b2fe-b901c2b8e0ea` · **tanggal:** 2026-08-01 · **set:** `id-W-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Kontrol ditahan | Mengarang | Token in/out |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `gemini-3.1-flash-lite-preview-or` | 162 | 0 | 0 | 73.5% | — | 65.8% | 40/117 | 27783 / 433 |
| `deepseek-v3-2` | 162 | 0 | 0 | 54.9% | — | 60.7% | 46/117 | 33235 / 639 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

*Kontrol ditahan* = persentase kalimat SUDAH BENAR yang dikembalikan apa adanya. *Mengarang* = berapa kali model menyunting kalimat yang tidak salah. **Untuk editor, kolom ini lebih menentukan daripada akurasi keseluruhan**: model yang 'memperbaiki' tulisan yang sudah benar menghancurkan kepercayaan pengguna, dan kerugiannya tidak sebanding dengan satu koreksi yang terlewat.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
