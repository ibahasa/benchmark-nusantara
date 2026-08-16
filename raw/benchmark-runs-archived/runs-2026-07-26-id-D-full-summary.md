# Hasil run `2026-07-26-id-D-full`

**run_id:** `3f2b1a90-0000-4000-8000-000000000009` · **tanggal:** 2026-07-26 · **set:** `id-D-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Kontrol ditahan | Mengarang | Token in/out |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `gemini-3.1-flash-lite-preview-or` | 124 | 0 | 0 | 92.9% | 100.0% | 90.6% | 3/32 | 9462 / 1014 |
| `gemma-4-31b` | 124 | 0 | 0 | 90.8% | 100.0% | 93.8% | 2/32 | 11717 / 1309 |
| `gemini-2.5-flash` | 124 | 0 | 0 | 89.8% | 100.0% | 96.9% | 1/32 | 9240 / 1016 |
| `deepseek-v3-2` | 124 | 0 | 0 | 87.8% | 92.3% | 87.5% | 4/32 | 11515 / 1277 |
| `qwen3-235b` | 124 | 0 | 0 | 80.6% | 88.5% | 81.2% | 6/32 | 13827 / 83142 |
| `qwen-3.5-flagship` | 108 | 1 | 5 | 70.9% | 85.7% | 67.9% | 9/28 | 9441 / 105254 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

*Kontrol ditahan* = persentase kalimat SUDAH BENAR yang dikembalikan apa adanya. *Mengarang* = berapa kali model menyunting kalimat yang tidak salah. **Untuk editor, kolom ini lebih menentukan daripada akurasi keseluruhan**: model yang 'memperbaiki' tulisan yang sudah benar menghancurkan kepercayaan pengguna, dan kerugiannya tidak sebanding dengan satu koreksi yang terlewat.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
