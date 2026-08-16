# Hasil run `2026-08-02-id-B-ab-A-terpotong-ulang`

**run_id:** `b1c0f1ea-0000-4000-8000-00000000000c` · **tanggal:** 2026-08-02 · **set:** `id-B-A-terpotong` · **templat prompt:** `mcq-v1` · **item:** 38 · **ulangan:** 3

Lengan A eksperimen A/B terkontrol: aturan pemotongan opsi >90 karakter DIHIDUPKAN. Dijalankan ulang setelah pelabelan galat harness diperbaiki; 228 dari 228 baris berskor, nol error, satu percobaan ulang. **Inilah lengan A yang sah**, bukan `-A-terpotong` tanpa akhiran.

| Model | Panggilan | Error | Gagal format | Skor | Item kontrol | Token in/out |
|---|---:|---:|---:|---:|---:|---:|
| `deepseek-v3-2` | 114 | 0 | 0 | 96.5% | 95.8% | 19832 / 206 |
| `gemini-3.1-flash-lite-preview-or` | 114 | 0 | 0 | 94.7% | 100.0% | 17004 / 114 |

Seluruh item `id-B` bertingkat *medium*, sehingga tidak ada pemisahan inti/dasar seperti pada set lain.

*Item kontrol* pada set ini berarti item yang jawaban benarnya adalah "kata itu tidak dikenal", dipakai menguji halusinasi. Jangan disamakan dengan kolom *Kontrol ditahan* pada set kalimat seperti `id-D`, yang mengukur berapa persen kalimat SUDAH BENAR dikembalikan apa adanya.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak dapat mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

Berkas ini sengaja hanya memuat **agregat per model**. Hasil per item tidak diterbitkan: pasangan `item_id` dan `score` memulihkan kunci jawaban item yang ditahan tanpa pernah melihat soalnya. Parameter reproduksi ada di `meta.json`.
