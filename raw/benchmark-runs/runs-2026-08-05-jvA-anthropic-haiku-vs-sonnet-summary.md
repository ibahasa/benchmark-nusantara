# Hasil run `2026-08-05-jvA-anthropic-haiku-vs-sonnet`

**run_id:** `c1a0de00-0000-4000-8000-000000000001` · **tanggal:** 2026-08-05 · **set:** `jv-A-draft-v0` · **templat prompt:** `mcq-v1` · **item:** 44 · **ulangan:** 3

Dua model Anthropic pada dimensi tingkat tutur bahasa Jawa, dipanggil langsung ke penyedianya, bukan lewat perantara seperti seluruh run kami yang lain.

| Model | Panggilan | Error | Item berskor | Skor MCQ | Simpangan 3 ulangan | Token in/out | Latensi | Biaya |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| `claude-haiku-4-5` | 132 | 0 | 36 | **72,22%** | 0,00 | 21.954 / 888 | 2,44 dtk | $0,0264 |
| `claude-sonnet-4-6` | 132 | 0 | 36 | **91,67%** | 0,00 | 22.086 / 859 | 1,61 dtk | $0,0791 |

Selisih **19,45 poin**, setara **7,0 item** dari 36. Lantai derau satu item = 2,78 poin.
Uji dua proporsi atas 36 item: z = 2,15, p dua-arah sekitar 0,03.

**24 baris per model tidak berskor** dan tidak masuk angka di atas: delapan item terbuka dikali tiga ulangan. Dimensi Jawa melarang penilaian mesin, sehingga item terbuka menunggu penilaian penutur.

Simpangan 0,00 berarti jawaban kedua model **identik di ketiga ulangan**. Itu tanda jawaban yang stabil, bukan jawaban yang benar, dan bukan pula jaminan angka yang sama akan muncul besok pada run terpisah.

Berkas ini sengaja hanya memuat agregat per model. Hasil per item tidak diterbitkan: pasangan `item_id` dan `score` memulihkan kunci jawaban item yang ditahan tanpa pernah melihat soalnya.
