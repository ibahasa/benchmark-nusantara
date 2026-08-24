# trial-model-probes: asal-usul dan batasnya

Berkas di sini lahir dari LAJUR UJI apps/benchmark (task-59): jalur karantina
untuk mengukur model di luar panel resmi (model samaran, pratinjau, uji beli)
dengan set, penilai otomatis, dan rubrik yang sama seperti papan resmi.

Batas yang membuatnya BUKAN bagian leaderboard, dan tidak akan pernah:

1. Identitas model bisa berumur pendek. Model samaran (stealth) berganti
   rujukan atau pensiun saat diumumkan; kolom `model_official` mencatat id
   yang benar-benar disajikan pada hari pengukuran.
2. Vonis penutur untuk item terbuka dinilai lewat panel lajur uji dengan
   penilai `penutur-uji`; ia skor-saja dan tidak menggeser kunci deret
   (`versi_kunci` beku pra-vonis). Deret ini TIDAK sebanding satu-ke-satu
   dengan deret resmi yang kuncinya hidup.
3. Model yang lulus uji coba dijalankan ulang di lajur resmi; angka resminya
   lahir di dataset per set repo ini, bukan di folder ini. Berkas di sini
   tetap sebagai catatan bertanggal.
4. Berkas kecocokan memuat bendera per item untuk irisan publik saja: tanpa
   huruf jawaban, tanpa teks, dan item tertahan tidak pernah ikut.

Tiap probe menambah berkas bertanggal baru; tidak ada yang ditimpa.
Angka artikel yang menyitir folder ini wajib dihitung ulang dari berkasnya.
