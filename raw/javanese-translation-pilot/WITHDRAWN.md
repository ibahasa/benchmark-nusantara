# Withdrawn 2026-08-16

This dataset is no longer published. The files that used to be here have been
removed from the current tree.

**Why.** The pilot published Javanese lemmas together with their Indonesian
glosses. Two of those lemmas, `Mrika` and `Gabah`, are held-back items in our
`javanese-word-meanings` benchmark, whose answer keys are never published on
purpose. The gloss "ke sana" printed here for `Mrika` is exactly its held-back
key. Four further lemmas from the same reserve pool appeared here as well:
`Amergi`, `Nggawa`, `Pinarak`, `Tampah`.

Withdrawal does not undo what was already published, and it is not meant to. The
files remain readable at earlier commits of this repository and of
`ibahasa/research-data`, so every article that cites them still resolves. What
stops is the republishing: this was a retired pilot that nobody was reading, and
keeping it live kept burning the reserve that our contamination checks depend on.

**What replaced its role.** Nothing. It was a two-model pilot on 20 sentences,
superseded by the sets still published here.

**The check that caught it.** `id_terbit_di_set_lain()` in our export gate now
flags any held-back lemma of one set that appears in another set's published
files. It did not exist when this pilot was published.

---

# Ditarik 2026-08-16

Dataset ini tidak lagi diterbitkan, dan berkasnya dihapus dari pohon sekarang.

**Kenapa.** Pilot ini menerbitkan lema Jawa beserta glos Indonesianya. Dua di
antaranya, `Mrika` dan `Gabah`, adalah item TERTAHAN di benchmark
`javanese-word-meanings` yang kuncinya memang tidak pernah diterbitkan. Glos
"ke sana" untuk `Mrika` di sini persis kunci tertahannya. Empat lema kolam
cadangan lain ikut terbit: `Amergi`, `Nggawa`, `Pinarak`, `Tampah`.

Penarikan tidak menarik kembali yang sudah terbit, dan memang tidak bermaksud
begitu. Berkasnya tetap terbaca pada commit lebih awal di repo ini maupun di
`ibahasa/research-data`, jadi setiap artikel yang mengutipnya tetap hidup. Yang
dihentikan penerbitan ulangnya: ini pilot pensiunan yang tidak dibaca siapa pun,
dan membiarkannya hidup terus membakar cadangan yang justru jadi sandaran
pemeriksaan kontaminasi kami.

**Penggantinya.** Tidak ada. Ia pilot dua model atas 20 kalimat, dan sudah
tergantikan set lain yang masih terbit di sini.

**Pemeriksa yang menangkapnya.** `id_terbit_di_set_lain()` di pagar ekspor kami
sekarang menandai lema tertahan satu set yang muncul di berkas terbit set lain.
Ia belum ada waktu pilot ini diterbitkan.
