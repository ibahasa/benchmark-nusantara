# Hasil run `2026-08-02-id-B-kontrol`

**run_id:** `fb632090-6a28-490a-b85c-32f1728394a9` · **tanggal:** 2026-08-01 · **set:** `id-B-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Kontrol ditahan | Mengarang | Token in/out |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `deepseek-v3-2` | 24 | 0 | 0 | 95.8% | — | 95.8% | 1/24 | 4092 / 46 |
| `gemini-3.1-flash-lite-preview-or` | 24 | 0 | 0 | 87.5% | — | 87.5% | 3/24 | 3453 / 24 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

*Kontrol ditahan* = persentase kalimat SUDAH BENAR yang dikembalikan apa adanya. *Mengarang* = berapa kali model menyunting kalimat yang tidak salah. **Untuk editor, kolom ini lebih menentukan daripada akurasi keseluruhan**: model yang 'memperbaiki' tulisan yang sudah benar menghancurkan kepercayaan pengguna, dan kerugiannya tidak sebanding dengan satu koreksi yang terlewat.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
