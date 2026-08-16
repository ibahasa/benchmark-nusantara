# Hasil run `2026-08-02-id-W-procurement`

**run_id:** `100721f1-be1e-4ffe-823a-ad3c7bcb32be` · **tanggal:** 2026-08-01 · **set:** `id-W-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Kontrol ditahan | Mengarang | Token in/out |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `gemini-3.1-flash-lite-preview-or` | 54 | 0 | 0 | 72.2% | — | 64.1% | 14/39 | 9261 / 142 |
| `deepseek-v3-2` | 54 | 0 | 0 | 48.1% | — | 48.7% | 20/39 | 11040 / 876 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

*Kontrol ditahan* = persentase kalimat SUDAH BENAR yang dikembalikan apa adanya. *Mengarang* = berapa kali model menyunting kalimat yang tidak salah. **Untuk editor, kolom ini lebih menentukan daripada akurasi keseluruhan**: model yang 'memperbaiki' tulisan yang sudah benar menghancurkan kepercayaan pengguna, dan kerugiannya tidak sebanding dengan satu koreksi yang terlewat.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
