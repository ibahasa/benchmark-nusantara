# Hasil run `2026-07-25-jv-A-gate`

**run_id:** `3f2b1a90-0000-4000-8000-000000000001` · **tanggal:** 2026-07-25 · **set:** `jv-A-draft-v0` · **template prompt:** `mcq-v1`

| Model | Panggilan | Error | Gagal format | Inti | Dasar | Token in/out |
|---|---:|---:|---:|---:|---:|---:|
| `gpt-5.4-pro` | 32 | 0 | 0 | 100.0% | 100.0% | 3890 / 8156 |
| `claude-5-sonnet` | 15 | 0 | 0 | 91.7% | 100.0% | 3358 / 45 |
| `qwen-3.5-flagship` | 32 | 0 | 5 | 75.0% | 100.0% | 3850 / 24180 |
| `qwen3-235b` | 32 | 0 | 0 | 70.0% | 83.3% | 4623 / 19775 |
| `gemini-3.1-pro` | 32 | 32 | 0 | — | — | 0 / 0 |
| `mistral-large-4` | 32 | 32 | 0 | — | — | 0 / 0 |

*Inti* = item medium/hard. *Dasar* = item easy, lantai pengukuran — **jangan pernah dirata-ratakan dengan inti**: item mudah menaikkan skor semua model.

*Gagal format* dihitung terpisah dari jawaban salah: model yang tidak bisa mengikuti format bukan hal yang sama dengan model yang tidak paham bahasanya.

Data mentah per item ada di `results.csv`; parameter reproduksi di `meta.json`.
