# Hasil run `2026-07-27-id-D-deepseek`

**run_id:** `3f2b1a90-0000-4000-8000-000000000021` · **tanggal:** 2026-07-26 · **set:** `id-D-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Kontrol ditahan | Mengarang | Token in/out |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `deepseek-v3-2` | 144 | 0 | 0 | 80.3% | 96.3% | 81.1% | 7/37 | 18003 / 1961 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

*Kontrol ditahan* = persentase kalimat SUDAH BENAR yang dikembalikan apa adanya. *Mengarang* = berapa kali model menyunting kalimat yang tidak salah. **Untuk editor, kolom ini lebih menentukan daripada akurasi keseluruhan**: model yang 'memperbaiki' tulisan yang sudah benar menghancurkan kepercayaan pengguna, dan kerugiannya tidak sebanding dengan satu koreksi yang terlewat.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
