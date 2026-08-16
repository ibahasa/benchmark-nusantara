# Hasil run `2026-07-26-id-D-procurement`

**run_id:** `3f2b1a90-0000-4000-8000-000000000007` · **tanggal:** 2026-07-26 · **set:** `id-D-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Kontrol ditahan | Mengarang | Token in/out |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `gemini-3.1-flash-lite-preview-or` | 24 | 0 | 0 | 92.9% | 100.0% | — | — | 1713 / 138 |
| `deepseek-v3-2` | 24 | 0 | 0 | 78.6% | 100.0% | — | — | 2089 / 189 |
| `gemini-2.5-flash` | 24 | 0 | 0 | 78.6% | 100.0% | — | — | 1673 / 139 |
| `gemma-4-31b` | 24 | 0 | 0 | 78.6% | 100.0% | — | — | 2099 / 162 |
| `qwen3-235b` | 24 | 0 | 0 | 71.4% | 100.0% | — | — | 2490 / 21158 |
| `qwen-3.5-flagship` | 24 | 0 | 1 | 57.1% | 100.0% | — | — | 1973 / 21740 |
| `mistral-small-3.2-24b-or` | 24 | 0 | 0 | 42.9% | 80.0% | — | — | 2126 / 216 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

*Kontrol ditahan* = persentase kalimat SUDAH BENAR yang dikembalikan apa adanya. *Mengarang* = berapa kali model menyunting kalimat yang tidak salah. **Untuk editor, kolom ini lebih menentukan daripada akurasi keseluruhan**: model yang 'memperbaiki' tulisan yang sudah benar menghancurkan kepercayaan pengguna, dan kerugiannya tidak sebanding dengan satu koreksi yang terlewat.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
