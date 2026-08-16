# Hasil run `2026-08-06-idN-dua-model-murah`

**run_id:** `a1b2c3d4-0000-4000-8000-000000000002` · **tanggal:** 2026-08-06 · **set:** `id-N-v2-rujukan-dibetulkan` · **item:** 69 · **ulangan:** 3 · **penyedia:** openrouter

Set normalisasi teks tidak baku ke bentuk baku. Seluruh 69 item bertipe terbuka dan ber-`auto_score`, dinilai dengan perbandingan suntingan terhadap kalimat asal, bukan pencocokan teks persis.

| Model | Panggilan | Error | Gagal format | Skor | Item kontrol | Perlu dinormalkan | Simpangan 3 ulangan | Median latensi | Token in/out | Biaya |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| `mistral-small-3` | 207 | 0 | 0 | **56,52%** | 82,2% | 49,4% | 1,18 | 850 ms | 28.044 / 2.618 | $0,0016 |
| `llama-3-1-8b-instruct-or` | 207 | 0 | 0 | **26,09%** | 42,2% | 21,6% | 3,55 | 941 ms | 32.732 / 2.846 | $0,0019 |

Selisih **30,43 poin**, setara **21,0 item** dari 69. Lantai derau satu item = 1,45 poin.
Uji dua proporsi atas 69 item: z = 3,63, p dua-arah sekitar 0,0003.
Kuasa 80% menuntut 37 item untuk selisih sebesar ini; set ini punya 69, sehingga **cukup kuasa**.

*Item kontrol* = teks yang SUDAH benar dan seharusnya dikembalikan apa adanya. Model yang mengubahnya melakukan koreksi berlebih. Kolom ini lebih menentukan daripada skor keseluruhan untuk pemakaian sebagai penyunting.

**Empat rujukan cacat dibetulkan sebelum run ini.** `id-n1-005`, `-018`, `-028` memuat `bku` dan `-040` memuat `brusaha` serta `smaksimal` di rujukannya sendiri. Akibatnya terbalik: model yang menormalkan dengan benar dinilai salah. Pada run sebelum perbaikan, kedua model mencetak 0,0% di keempat item itu.

Berkas ini sengaja hanya memuat agregat per model; tidak ada skor per item di sini. Empat nomor item yang disebut di atas adalah catatan koreksi dataset, bukan hasil, dan keempatnya bukan item yang ditahan.
