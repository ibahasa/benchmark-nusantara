# Hasil run `2026-08-03-id-B-frasa-dibaurkan`

**run_id:** `b1c0f1ea-0000-4000-8000-00000000000d` · **tanggal:** 2026-08-03 · **set:** `id-B-v3-opsi-tidak-dikenal` · **templat prompt:** `mcq-v1` · **item:** 38 · **ulangan:** 3

Setelah opsi "kata ini tidak dikenal" disisipkan ke seluruh 38 item sehingga kehadirannya tak lagi menandai kunci. Strategi buta "pilih opsi tidak-dikenal" turun dari 8 dari 8 menjadi 8 dari 38, yaitu 21,1%, di bawah tebakan acak. **Skor dari versi item sebelumnya tidak sebanding**: `item_version` ketiga puluh item `id-b1` dinaikkan.

| Model | Panggilan | Error | Gagal format | Skor | Item kontrol | Token in/out |
|---|---:|---:|---:|---:|---:|---:|
| `deepseek-v3-2` | 114 | 0 | 0 | 95.6% | 100.0% | 22012 / 195 |
| `gemini-3.1-flash-lite-preview-or` | 114 | 0 | 0 | 97.4% | 100.0% | 18759 / 114 |

Seluruh item `id-B` bertingkat *medium*, sehingga tidak ada pemisahan inti/dasar seperti pada set lain.

*Item kontrol* pada set ini berarti item yang jawaban benarnya adalah "kata itu tidak dikenal", dipakai menguji halusinasi. Jangan disamakan dengan kolom *Kontrol ditahan* pada set kalimat seperti `id-D`, yang mengukur berapa persen kalimat SUDAH BENAR dikembalikan apa adanya.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak dapat mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

Berkas ini sengaja hanya memuat **agregat per model**. Hasil per item tidak diterbitkan: pasangan `item_id` dan `score` memulihkan kunci jawaban item yang ditahan tanpa pernah melihat soalnya. Parameter reproduksi ada di `meta.json`.
