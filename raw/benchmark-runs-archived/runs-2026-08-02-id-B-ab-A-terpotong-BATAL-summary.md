# BATAL — run `2026-08-02-id-B-ab-A-terpotong`

**run_id:** `b1c0f1ea-0000-4000-8000-00000000000a` · **tanggal:** 2026-08-02 · **set:** `id-B-A-terpotong` · **templat prompt:** `mcq-v1` · **item:** 38 · **ulangan:** 3

Lengan A eksperimen A/B terkontrol: aturan pemotongan opsi >90 karakter DIHIDUPKAN.

**BERKAS INI TIDAK BOLEH DIPAKAI SEBAGAI SUMBER ANGKA.** Jalannya kehilangan 2 baris karena kegagalan penyedia salah dilabeli permanen di harness. Penggantinya `2026-08-02-id-B-ab-A-terpotong-ulang`, yang 228 dari 228 baris berskor.

| Model | Panggilan | Error | Gagal format | Skor | Item kontrol | Token in/out |
|---|---:|---:|---:|---:|---:|---:|
| `deepseek-v3-2` | 114 | 0 | 0 | 95.6% | 95.8% | 19826 / 566 |
| `gemini-3.1-flash-lite-preview-or` | 114 | 2 | 0 | 95.5% | 100.0% | 16714 / 112 |

Seluruh item `id-B` bertingkat *medium*, sehingga tidak ada pemisahan inti/dasar seperti pada set lain.

*Item kontrol* pada set ini berarti item yang jawaban benarnya adalah "kata itu tidak dikenal", dipakai menguji halusinasi. Jangan disamakan dengan kolom *Kontrol ditahan* pada set kalimat seperti `id-D`, yang mengukur berapa persen kalimat SUDAH BENAR dikembalikan apa adanya.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak dapat mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

Berkas ini sengaja hanya memuat **agregat per model**. Hasil per item tidak diterbitkan: pasangan `item_id` dan `score` memulihkan kunci jawaban item yang ditahan tanpa pernah melihat soalnya. Parameter reproduksi ada di `meta.json`.
