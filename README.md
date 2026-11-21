<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Pengayaan Belajar di Rumah - SD ICT Klapasawit</title>
<style>
  :root { --bg:#eef6f3; --card:#ffffff; --ink:#1f2937; --muted:#5b6672; --main:#0f766e; --on-main:#ffffff; --acc:#f59e0b;
          --ok:#15803d; --bad:#dc2626; --line:#d5e2dd; --soft:#e6f4f1; --warn:#b45309; }
  @media (prefers-color-scheme: dark) {
    :root { --bg:#0b1b1a; --card:#14292a; --ink:#e8f1ef; --muted:#9db4b1; --main:#2dd4bf; --on-main:#04201d; --line:#27494a; --soft:#173635; --ok:#4ade80; --bad:#f87171; --warn:#fbbf24; }
  }
  * { box-sizing:border-box; }
  body { margin:0; font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif; background:var(--bg); color:var(--ink); line-height:1.55; }
  [hidden] { display:none !important; }
  .wrap { max-width:720px; margin:0 auto; padding:14px; }
  .card { background:var(--card); border:1px solid var(--line); border-radius:18px; padding:20px; margin-bottom:14px; }
  h1,h2,h3 { line-height:1.25; margin:0 0 8px; }
  h3 { margin-top:16px; font-size:1.05rem; }
  .muted { color:var(--muted); font-size:.95rem; }

  /* kepala sekolah */
  .kepala { text-align:center; padding:26px 18px; background:linear-gradient(135deg,#0f766e 0%,#0e9488 100%); color:#fff; border-radius:18px; margin-bottom:14px; }
  .kepala .sek { font-size:.95rem; letter-spacing:.08em; text-transform:uppercase; opacity:.95; }
  .kepala h1 { font-size:1.7rem; margin:6px 0; }
  .kepala .tag { display:inline-block; margin-top:4px; background:var(--acc); color:#3b2300; font-weight:800; padding:4px 16px; border-radius:999px; }

  label.f { display:block; font-weight:700; margin:16px 0 6px; }
  input[type=text] { width:100%; padding:14px; font-size:1.15rem; border:2px solid var(--line); border-radius:12px; background:var(--card); color:var(--ink); }
  input[type=text]:focus { outline:none; border-color:var(--main); }
  .btn { display:inline-block; border:0; border-radius:12px; padding:13px 22px; font-size:1.05rem; font-weight:800; cursor:pointer; color:var(--on-main); background:var(--main); text-decoration:none; text-align:center; }
  .btn.full { display:block; width:100%; margin-top:14px; }
  .btn.sec { background:#64748b; color:#fff; } .btn.wa { background:#16a34a; color:#fff; } .btn.warn { background:var(--bad); color:#fff; }
  .btn:disabled { opacity:.45; cursor:not-allowed; }
  .info { background:var(--soft); border-left:5px solid var(--main); border-radius:10px; padding:12px 14px; margin-top:14px; font-size:.96rem; }

  /* materi */
  .materi h2 { color:var(--main); }
  .materi ul { padding-left:22px; margin:8px 0; }
  .materi li { margin:4px 0; }
  .rumus { background:var(--soft); border-radius:12px; padding:10px 14px; margin:10px 0; font-weight:700; }
  .contoh { background:var(--soft); border-radius:12px; padding:6px 14px; margin:10px 0; }
  .contoh p { margin:6px 0; }
  table { width:100%; border-collapse:collapse; margin:10px 0; font-size:.94rem; }
  th, td { border:1px solid var(--line); padding:7px 8px; text-align:left; vertical-align:top; }
  th { background:var(--soft); }
  .tabel-geser { overflow-x:auto; }

  /* soal */
  .bar { position:sticky; top:8px; z-index:5; display:flex; align-items:center; justify-content:space-between; gap:12px; background:var(--card); border:1px solid var(--line); border-radius:999px; padding:8px 18px; margin-bottom:12px; box-shadow:0 2px 10px rgba(0,0,0,.12); }
  #timer { font:800 1.55rem ui-monospace,Menlo,monospace; color:var(--ok); }
  #timer.hampir { color:var(--warn); } #timer.kritis { color:var(--bad); }
  .terjawab { font-weight:700; font-size:.95rem; }
  .chips { display:flex; flex-wrap:wrap; gap:6px; margin-bottom:12px; }
  .chip { width:38px; height:38px; border-radius:10px; border:2px solid var(--line); background:var(--card); color:var(--ink); font-weight:800; cursor:pointer; }
  .chip.sebagian { border-style:dashed; border-color:var(--acc); }
  .chip.isi { background:var(--main); border-color:var(--main); color:var(--on-main); }
  .chip.kini { outline:3px solid var(--acc); outline-offset:1px; }
  .label-soal { display:flex; flex-wrap:wrap; gap:8px; align-items:center; margin-bottom:10px; }
  .nomor { display:inline-block; background:var(--main); color:var(--on-main); border-radius:999px; padding:3px 14px; font-weight:800; font-size:.9rem; }
  .jenis { display:inline-block; background:var(--soft); color:var(--main); border:1px solid var(--main); border-radius:999px; padding:2px 12px; font-weight:700; font-size:.82rem; }
  #teks p { margin:0 0 8px; font-size:1.12rem; font-weight:600; }
  #teks p.kutip { background:var(--soft); border-left:5px solid var(--acc); padding:10px 14px; border-radius:8px; font-style:italic; font-weight:600; }
  .kasus { background:var(--soft); border-left:5px solid var(--acc); border-radius:10px; padding:12px 14px; margin-bottom:12px; font-size:1.04rem; }
  .petunjuk { font-weight:700; margin:0 0 4px; }
  .blank { display:inline-block; min-width:70px; border-bottom:3px solid var(--ink); margin:0 4px; }
  .opsi { display:flex; align-items:center; gap:12px; padding:12px 14px; border:2px solid var(--line); border-radius:14px; margin-top:10px; cursor:pointer; background:var(--card); }
  .opsi:hover { border-color:var(--main); }
  .opsi input { position:absolute; opacity:0; pointer-events:none; }
  .opsi .h { flex:0 0 34px; height:34px; border-radius:50%; background:var(--soft); color:var(--main); display:flex; align-items:center; justify-content:center; font-weight:800; }
  .opsi.pilih { border-color:var(--main); background:var(--soft); }
  .opsi.pilih .h { background:var(--main); color:var(--on-main); }
  .opsi:focus-within { outline:3px solid var(--acc); }
  .pern { border:2px solid var(--line); border-radius:14px; padding:12px 14px; margin-top:10px; background:var(--card); }
  .pern.lengkap { border-color:var(--main); }
  .pern p { margin:0 0 10px; font-weight:600; }
  .bs { display:flex; gap:10px; }
  .pill { flex:1; text-align:center; padding:10px; border:2px solid var(--line); border-radius:12px; font-weight:800; cursor:pointer; background:var(--card); }
  .pill:hover { border-color:var(--main); }
  .pill input { position:absolute; opacity:0; pointer-events:none; }
  .pill.pilih { background:var(--main); border-color:var(--main); color:var(--on-main); }
  .pill:focus-within { outline:3px solid var(--acc); }
  .nav { display:flex; gap:10px; margin-top:16px; }
  .nav .btn { flex:1; }

  /* hasil */
  .nilai { font-size:3.6rem; font-weight:900; color:var(--main); text-align:center; line-height:1.1; margin:6px 0; }
  .center { text-align:center; }
  .bar-materi { display:flex; align-items:center; gap:10px; margin:8px 0; font-size:.95rem; }
  .bar-materi .n { flex:0 0 150px; font-weight:700; }
  .bar-materi .t { flex:1; height:14px; background:var(--soft); border-radius:99px; overflow:hidden; }
  .bar-materi .t i { display:block; height:100%; background:var(--main); }
  .pesan { background:var(--soft); border:1px dashed var(--main); border-radius:12px; padding:12px; white-space:pre-wrap; font-size:.9rem; margin-top:10px; }
  tr.ok { background:rgba(21,128,61,.10); } tr.bad { background:rgba(220,38,38,.10); }
  td.pbh { font-size:.88rem; color:var(--muted); }
</style>
</head>
<body>
<!-- Data soal berada di blok JSON ini. Untuk mengganti soal, ganti isi blok ini saja. -->
<script id="data-soal" type="application/json">{
 "sekolah": "SD ICT Klapasawit",
 "program": "Pengayaan Belajar di Rumah",
 "tagline": "Siswa Hebat",
 "mapel": "Pendidikan Pancasila",
 "topik": "Norma dalam Kehidupan Sehari-hari",
 "kelas": "V (Lima)",
 "durasi_menit": 30,
 "nomor_wa": "089670482001",
 "tampilkan_koreksi": false,
 "soal": [
  {
   "nomor": 1,
   "jenis": "pilihan_ganda",
   "materi": "Pengertian & manfaat norma",
   "teks": "Norma adalah ....",
   "pilihan": {
    "a": "aturan atau pedoman hidup yang mengatur tingkah laku manusia",
    "b": "hukuman yang diberikan kepada orang yang bersalah",
    "c": "kebiasaan buruk yang sering dilakukan orang",
    "d": "permainan yang dimainkan bersama-sama"
   },
   "kunci": "a",
   "pembahasan": "Norma adalah aturan atau pedoman hidup yang mengatur tingkah laku manusia agar hidup tertib, aman, damai, dan saling menghormati."
  },
  {
   "nomor": 2,
   "jenis": "pilihan_ganda",
   "materi": "Pengertian & manfaat norma",
   "teks": "Salah satu tujuan adanya norma dalam kehidupan sehari-hari adalah ....",
   "pilihan": {
    "a": "membuat orang bebas berbuat sesuka hati",
    "b": "menciptakan kehidupan yang tertib, aman, dan rukun",
    "c": "mempersulit orang yang ingin berbuat baik",
    "d": "membedakan orang kaya dan orang miskin"
   },
   "kunci": "b",
   "pembahasan": "Norma dibuat untuk menciptakan ketertiban, keamanan, dan kerukunan, bukan untuk mempersulit manusia."
  },
  {
   "nomor": 3,
   "jenis": "pilihan_ganda",
   "materi": "Pengertian & manfaat norma",
   "teks": "Siswa mengantre dengan tertib saat membeli makanan di kantin. Manfaat dari perbuatan tersebut adalah ....",
   "pilihan": {
    "a": "makanan di kantin menjadi gratis",
    "b": "kantin menjadi lebih cepat tutup",
    "c": "tidak ada yang saling menyerobot atau berebut makanan",
    "d": "penjual tidak perlu melayani pembeli"
   },
   "kunci": "c",
   "pembahasan": "Jika semua siswa menaati aturan antre, tidak akan terjadi saling menyerobot atau berebut makanan."
  },
  {
   "nomor": 4,
   "jenis": "pilihan_ganda",
   "materi": "Jenis norma",
   "teks": "Pasangan jenis norma dan sumber aturannya yang tepat adalah ....",
   "pilihan": {
    "a": "norma agama - hati nurani",
    "b": "norma kesusilaan - peraturan resmi",
    "c": "norma hukum - ajaran Tuhan",
    "d": "norma kesopanan - kebiasaan dan tata krama dalam pergaulan masyarakat"
   },
   "kunci": "d",
   "pembahasan": "Agama bersumber dari ajaran Tuhan, kesusilaan dari hati nurani, kesopanan dari kebiasaan dan tata krama masyarakat, hukum dari peraturan resmi."
  },
  {
   "nomor": 5,
   "jenis": "pilihan_ganda",
   "materi": "Akibat pelanggaran",
   "teks": "Dimas menyontek saat ulangan. Setelah itu ia merasa bersalah dan menyesal. Perasaan Dimas merupakan akibat melanggar norma ....",
   "pilihan": {
    "a": "hukum",
    "b": "kesopanan",
    "c": "kesusilaan",
    "d": "agama"
   },
   "kunci": "c",
   "pembahasan": "Rasa bersalah, menyesal, atau malu adalah akibat melanggar norma kesusilaan yang berasal dari hati nurani."
  },
  {
   "nomor": 6,
   "jenis": "pilihan_ganda",
   "materi": "Jenis norma",
   "teks": "Perbuatan berikut yang termasuk norma kesopanan adalah ....",
   "pilihan": {
    "a": "mengucapkan permisi ketika lewat di depan orang",
    "b": "memakai helm saat mengendarai sepeda motor",
    "c": "berdoa sebelum belajar",
    "d": "mengakui kesalahan yang telah dibuat"
   },
   "kunci": "a",
   "pembahasan": "Mengucapkan permisi adalah tata krama dalam pergaulan (kesopanan). Helm = hukum, berdoa = agama, mengakui kesalahan = kesusilaan."
  },
  {
   "nomor": 7,
   "jenis": "pilihan_ganda",
   "materi": "Jenis norma",
   "teks": "Aturan yang dibuat oleh pihak berwenang, bersifat mengikat, dan memiliki sanksi tegas disebut norma ....",
   "pilihan": {
    "a": "kesusilaan",
    "b": "hukum",
    "c": "kesopanan",
    "d": "agama"
   },
   "kunci": "b",
   "pembahasan": "Norma hukum dibuat oleh lembaga atau pihak berwenang, bersifat mengikat, dan memiliki sanksi tegas."
  },
  {
   "nomor": 8,
   "jenis": "pilihan_ganda",
   "materi": "Norma di lingkungan",
   "teks": "Perbuatan yang menunjukkan penerapan norma di lingkungan keluarga adalah ....",
   "pilihan": {
    "a": "datang ke sekolah tepat waktu",
    "b": "mengikuti kerja bakti di kampung",
    "c": "memakai seragam sesuai aturan",
    "d": "meminta izin kepada orang tua ketika akan pergi"
   },
   "kunci": "d",
   "pembahasan": "Meminta izin kepada orang tua adalah norma di keluarga. Datang tepat waktu dan seragam adalah norma sekolah, kerja bakti adalah norma masyarakat."
  },
  {
   "nomor": 9,
   "jenis": "pilihan_ganda",
   "materi": "Akibat pelanggaran",
   "teks": "Rani mencuri barang milik orang lain, lalu dilaporkan kepada pihak berwenang. Akibat yang paling tepat berdasarkan norma hukum adalah ....",
   "pilihan": {
    "a": "mendapat sanksi sesuai peraturan, seperti denda atau hukuman",
    "b": "hanya mendapat teguran dari teman",
    "c": "dianggap tidak sopan oleh tetangga",
    "d": "tidak mendapat akibat apa pun"
   },
   "kunci": "a",
   "pembahasan": "Pelanggaran norma hukum, seperti mencuri, mendapat sanksi sesuai peraturan, misalnya denda atau hukuman."
  },
  {
   "nomor": 10,
   "jenis": "pilihan_ganda",
   "materi": "Sikap patuh norma",
   "teks": "Sikap berikut yang mencerminkan kepatuhan terhadap norma adalah ....",
   "pilihan": {
    "a": "berbohong agar tidak dimarahi",
    "b": "membiarkan sampah berserakan di halaman",
    "c": "meminta maaf ketika melakukan kesalahan",
    "d": "menyontek ketika ulangan agar nilainya bagus"
   },
   "kunci": "c",
   "pembahasan": "Mau meminta maaf ketika melakukan kesalahan adalah sikap yang mencerminkan kepatuhan terhadap norma."
  },
  {
   "nomor": 11,
   "jenis": "benar_salah",
   "materi": "Pengertian & manfaat norma",
   "kasus": "Saat istirahat, kantin sekolah sangat ramai. Beni dan teman-temannya mengantre dengan tertib. Tiba-tiba Rudi datang dan langsung menyerobot ke depan barisan. Beberapa siswa menjadi kesal dan hampir bertengkar. Bu Guru menegur Rudi dan mengajaknya kembali ke belakang barisan.",
   "pernyataan": [
    "Mengantre dengan tertib adalah contoh menaati norma.",
    "Rudi tidak melanggar aturan apa pun karena kantin adalah tempat umum.",
    "Jika semua siswa menaati aturan antre, perselisihan seperti itu dapat dicegah."
   ],
   "kunci": [
    true,
    false,
    true
   ],
   "pembahasan": "(1) Benar: antre adalah contoh menaati norma. (2) Salah: Rudi melanggar norma kesopanan dan tata tertib karena menyerobot. (3) Benar: aturan antre mencegah perselisihan."
  },
  {
   "nomor": 12,
   "jenis": "benar_salah",
   "materi": "Jenis norma",
   "kasus": "Sinta membeli jajan di warung. Penjual salah memberi uang kembalian sehingga uang Sinta berlebih Rp5.000. Tidak ada orang lain yang menyadarinya. Sinta merasa ragu sejenak, lalu mengembalikan kelebihan uang itu kepada penjual.",
   "pernyataan": [
    "Keputusan Sinta berkaitan dengan norma kesusilaan yang berasal dari hati nurani.",
    "Perbuatan Sinta menunjukkan sikap jujur.",
    "Jika Sinta menyimpan uang itu, ia pasti langsung dihukum denda oleh polisi."
   ],
   "kunci": [
    true,
    true,
    false
   ],
   "pembahasan": "(1) Benar: hati nurani adalah sumber norma kesusilaan. (2) Benar: mengembalikan uang menunjukkan kejujuran. (3) Salah: akibat yang paling mungkin adalah rasa bersalah, bukan denda langsung dari polisi."
  },
  {
   "nomor": 13,
   "jenis": "benar_salah",
   "materi": "Jenis norma",
   "kasus": "Dito ingin lewat di depan Pak Rahmat yang sedang duduk mengobrol di teras. Dito membungkuk sedikit dan berkata, \"Permisi, Pak.\" Ketika Pak Rahmat mengambilkan bolanya yang menggelinding, Dito berkata, \"Terima kasih, Pak.\"",
   "pernyataan": [
    "Ucapan \"permisi\" dan \"terima kasih\" adalah contoh norma hukum.",
    "Jika Dito lewat tanpa permisi, ia dapat ditegur atau dianggap tidak sopan.",
    "Norma kesopanan berasal dari kebiasaan dan tata krama dalam pergaulan masyarakat."
   ],
   "kunci": [
    false,
    true,
    true
   ],
   "pembahasan": "(1) Salah: itu contoh norma kesopanan. (2) Benar: akibat melanggar kesopanan adalah teguran atau celaan. (3) Benar: itulah sumber norma kesopanan."
  },
  {
   "nomor": 14,
   "jenis": "benar_salah",
   "materi": "Jenis norma",
   "kasus": "Kak Andi mengantar adiknya ke sekolah dengan sepeda motor. Ia memakai helm dan berhenti ketika lampu lalu lintas menyala merah. Di perempatan yang sama, seorang pengendara lain menerobos lampu merah dan ditegur oleh polisi.",
   "pernyataan": [
    "Berhenti saat lampu merah menyala adalah contoh norma kesopanan.",
    "Peraturan lalu lintas tidak memiliki sanksi sehingga boleh dilanggar.",
    "Pengendara yang menerobos lampu merah dapat ditegur atau dikenai sanksi oleh pihak berwenang."
   ],
   "kunci": [
    false,
    false,
    true
   ],
   "pembahasan": "(1) Salah: aturan lalu lintas adalah norma hukum. (2) Salah: norma hukum memiliki sanksi tegas. (3) Benar: pelanggar dapat ditegur atau dikenai sanksi."
  },
  {
   "nomor": 15,
   "jenis": "benar_salah",
   "materi": "Jenis norma",
   "kasus": "Menjelang pelajaran pertama, Aisyah dan teman-temannya berdoa bersama. Saat istirahat, Aisyah melihat Dina terjatuh dan lututnya terluka. Aisyah segera menolong Dina dan mengantarnya ke ruang UKS.",
   "pernyataan": [
    "Berdoa sebelum belajar adalah contoh norma agama.",
    "Norma agama berasal dari ajaran Tuhan Yang Maha Esa melalui agama dan kepercayaan.",
    "Menolong orang yang membutuhkan, seperti yang dilakukan Aisyah, sesuai dengan norma agama."
   ],
   "kunci": [
    true,
    true,
    true
   ],
   "pembahasan": "Ketiga pernyataan benar: berdoa dan menolong sesama adalah contoh norma agama, dan sumbernya adalah ajaran Tuhan."
  },
  {
   "nomor": 16,
   "jenis": "benar_salah",
   "materi": "Norma di lingkungan",
   "kasus": "Warga RT 05 mengadakan kerja bakti membersihkan selokan. Bimo ikut membantu membawa karung sampah. Sementara itu, Toni asyik bermain gawai di depan rumah dan sempat membuang bungkus jajan ke selokan yang baru dibersihkan.",
   "pernyataan": [
    "Bimo menerapkan norma di lingkungan masyarakat dengan ikut kerja bakti.",
    "Membuang bungkus jajan ke selokan termasuk menjaga kebersihan lingkungan.",
    "Norma hanya berlaku di sekolah, sehingga warga tidak perlu menaatinya di kampung."
   ],
   "kunci": [
    true,
    false,
    false
   ],
   "pembahasan": "(1) Benar: gotong royong adalah norma di masyarakat. (2) Salah: itu mengotori lingkungan. (3) Salah: norma berlaku di rumah, sekolah, dan masyarakat."
  },
  {
   "nomor": 17,
   "jenis": "benar_salah",
   "materi": "Akibat pelanggaran",
   "kasus": "Raka meminjam buku cerita milik Fira dan berjanji mengembalikannya besok. Ternyata buku itu hilang, tetapi Raka berbohong dan mengatakan bukunya tertinggal di rumah. Beberapa hari kemudian Fira mengetahui kebenarannya. Sejak itu Fira tidak mau lagi meminjamkan barang kepada Raka.",
   "pernyataan": [
    "Sikap Raka mencerminkan kejujuran dan tanggung jawab.",
    "Berbohong kepada teman dapat menyebabkan hilangnya kepercayaan.",
    "Seharusnya Raka mengakui kesalahan dan meminta maaf kepada Fira."
   ],
   "kunci": [
    false,
    true,
    true
   ],
   "pembahasan": "(1) Salah: Raka berbohong. (2) Benar: akibat berbohong adalah hilangnya kepercayaan. (3) Benar: mengakui kesalahan dan meminta maaf adalah sikap yang tepat."
  },
  {
   "nomor": 18,
   "jenis": "benar_salah",
   "materi": "Norma di lingkungan",
   "kasus": "Wali kelas menetapkan tata tertib: datang tepat waktu, memakai seragam sesuai aturan, dan melaksanakan piket sesuai jadwal. Hari ini Wahyu terlambat dan lupa memakai dasi. Wali kelas menasihatinya dengan lembut dan meminta Wahyu menaati tata tertib mulai besok.",
   "pernyataan": [
    "Datang tepat waktu dan memakai seragam sesuai aturan adalah contoh menerapkan norma di sekolah.",
    "Melanggar tata tertib sekolah dapat mendapat teguran atau pembinaan.",
    "Wahyu tidak perlu mengubah kebiasaannya karena tata tertib sekolah tidak mengikat siswa."
   ],
   "kunci": [
    true,
    true,
    false
   ],
   "pembahasan": "(1) Benar: itu norma di lingkungan sekolah. (2) Benar: pelanggar tata tertib mendapat teguran atau pembinaan. (3) Salah: tata tertib wajib ditaati oleh siswa."
  },
  {
   "nomor": 19,
   "jenis": "benar_salah",
   "materi": "Jenis norma",
   "kasus": "Bu Lina bertanya, \"Jika seseorang mencuri, norma apa saja yang ia langgar?\" Para siswa berdiskusi. Mereka sepakat bahwa mencuri dilarang oleh ajaran agama, membuat pelakunya merasa bersalah, dan dapat membuat pelakunya dikenai hukuman.",
   "pernyataan": [
    "Mencuri dilarang oleh ajaran agama sehingga melanggar norma agama.",
    "Satu perbuatan tidak mungkin melanggar lebih dari satu jenis norma.",
    "Mencuri dapat dikenai sanksi hukum karena melanggar norma hukum."
   ],
   "kunci": [
    true,
    false,
    true
   ],
   "pembahasan": "(1) Benar. (2) Salah: satu perbuatan bisa melanggar beberapa norma sekaligus, misalnya mencuri melanggar norma agama, kesusilaan, dan hukum. (3) Benar."
  },
  {
   "nomor": 20,
   "jenis": "benar_salah",
   "materi": "Sikap patuh norma",
   "kasus": "Saat ulangan Matematika, Dewi lupa rumus. Teman di sebelahnya menawarkan untuk menunjukkan jawabannya. Dewi menolak dan mengerjakan sebisanya. Setelah ulangan, ia jujur kepada guru bahwa ada beberapa soal yang belum ia kuasai.",
   "pernyataan": [
    "Dewi sebaiknya menerima tawaran temannya karena tidak ada yang tahu.",
    "Menolak menyontek menunjukkan sikap jujur dan disiplin menaati aturan.",
    "Sikap jujur hanya penting jika dilihat oleh guru."
   ],
   "kunci": [
    false,
    true,
    false
   ],
   "pembahasan": "(1) Salah: menyontek melanggar norma kesusilaan dan tata tertib. (2) Benar. (3) Salah: kejujuran harus dilakukan walaupun tidak ada yang melihat."
  }
 ]
}</script>

<div class="wrap">

  <!-- HALAMAN 1: identitas siswa -->
  <section id="p1">
    <div class="kepala">
      <div class="sek" id="k-sek"></div>
      <h1 id="k-program"></h1>
      <span class="tag" id="k-tag"></span>
    </div>
    <div class="card">
      <h2>Selamat datang! 👋</h2>
      <p><b>Pengayaan Belajar di Rumah</b> adalah kegiatan belajar tambahan di rumah untuk memperdalam materi yang sudah dipelajari di sekolah. Kamu bisa membaca materi, lalu mencoba soal latihan dengan tenang.</p>
      <p><b>Siswa Hebat</b> adalah siswa yang mau terus belajar, berani mencoba, dan jujur dalam mengerjakan.</p>
      <div class="info">
        📘 <b id="k-mapel"></b> · Kelas <span id="k-kelas"></span><br>
        ✏️ Materi: <b id="k-topik"></b><br>
        📝 <span id="k-jml"></span><br>
        ⏱️ Waktu mengerjakan: <span id="k-durasi"></span> menit
      </div>
      <label class="f" for="nama">Tulis namamu</label>
      <input type="text" id="nama" maxlength="40" placeholder="Nama lengkap" autocomplete="name">
      <button class="btn full" id="btn-lanjut1">Lanjut ke Materi →</button>
    </div>
  </section>

  <!-- HALAMAN 2: materi -->
  <section id="p2" hidden>
    <div class="card materi">
      <h1 id="m-judul"></h1>
      <p class="muted">Halo, <b id="m-nama"></b>! Baca materi ini sampai selesai. Waktu mengerjakan soal baru dihitung setelah kamu menekan tombol <b>Mulai Mengerjakan</b>.</p>
    </div>

    <div class="card materi">
      <h2>1. Apa Itu Norma?</h2>
      <p>Pernahkah kamu melihat teman membuang sampah sembarangan? Atau melihat siswa yang mengantre dengan tertib di kantin?</p>
      <p>Mengapa kita harus membuang sampah pada tempatnya dan mengantre dengan tertib? Karena dalam kehidupan sehari-hari ada aturan yang harus kita patuhi. Aturan itu disebut <b>norma</b>.</p>
      <div class="rumus">Norma adalah aturan atau pedoman hidup yang mengatur tingkah laku manusia agar tercipta kehidupan yang tertib, aman, damai, dan saling menghormati.</div>
      <p>Contoh norma sehari-hari:</p>
      <div class="contoh">
        <p>✔ Mengucapkan salam ketika bertemu guru.</p>
        <p>✔ Berbicara sopan kepada orang tua.</p>
        <p>✔ Tidak mengambil barang milik teman.</p>
        <p>✔ Mematuhi tata tertib sekolah.</p>
        <p>✔ Menyeberang jalan di tempat penyeberangan.</p>
      </div>
      <div class="info">💡 <b>Ingat!</b> Norma dibuat bukan untuk mempersulit manusia, tetapi untuk membantu manusia hidup dengan baik bersama orang lain.</div>
    </div>

    <div class="card materi">
      <h2>2. Mengapa Kita Harus Mematuhi Norma?</h2>
      <p>Norma memiliki beberapa tujuan dan manfaat:</p>
      <ul>
        <li>Menciptakan kehidupan yang tertib dan teratur.</li>
        <li>Menjaga keamanan dan keselamatan.</li>
        <li>Menghormati hak orang lain.</li>
        <li>Mencegah terjadinya pertengkaran dan perselisihan.</li>
        <li>Menciptakan kerukunan dalam masyarakat.</li>
        <li>Membiasakan diri menjadi manusia yang bertanggung jawab.</li>
      </ul>
      <div class="contoh"><p><b>Contoh:</b> Jika semua siswa menaati aturan antre di kantin, tidak akan terjadi saling menyerobot atau berebut makanan.</p></div>
    </div>

    <div class="card materi">
      <h2>3. Jenis-Jenis Norma</h2>
      <p>Dalam kehidupan masyarakat Indonesia, ada <b>empat jenis norma</b> yang perlu kita ketahui.</p>

      <h3>🙏 A. Norma Agama</h3>
      <div class="rumus">Norma yang berasal dari ajaran Tuhan Yang Maha Esa melalui agama dan kepercayaan.</div>
      <div class="contoh">
        <p>Contoh: beribadah sesuai agama masing-masing, berdoa sebelum belajar, menolong orang yang membutuhkan.</p>
        <p><b>Akibat melanggar:</b> mendapat dosa atau konsekuensi menurut ajaran agama.</p>
      </div>

      <h3>💛 B. Norma Kesusilaan</h3>
      <div class="rumus">Norma yang berasal dari hati nurani manusia tentang perbuatan baik dan buruk.</div>
      <div class="contoh">
        <p>Contoh: berkata jujur, mengakui kesalahan, tidak menyontek, merasa bersalah ketika berbuat curang.</p>
        <p><b>Akibat melanggar:</b> merasa bersalah, menyesal, atau malu.</p>
      </div>

      <h3>🤝 C. Norma Kesopanan</h3>
      <div class="rumus">Norma yang berasal dari kebiasaan dan tata krama dalam pergaulan masyarakat.</div>
      <div class="contoh">
        <p>Contoh: mengucapkan permisi ketika lewat di depan orang, menghormati orang tua dan guru, tidak berbicara kasar, mengucapkan terima kasih setelah dibantu.</p>
        <p><b>Akibat melanggar:</b> mendapat teguran, celaan, atau dianggap tidak sopan.</p>
      </div>

      <h3>⚖️ D. Norma Hukum</h3>
      <div class="rumus">Norma yang dibuat oleh lembaga atau pihak berwenang, bersifat mengikat, dan memiliki sanksi tegas.</div>
      <div class="contoh">
        <p>Contoh: mematuhi rambu lalu lintas, tidak mencuri, memakai helm saat mengendarai sepeda motor, tidak merusak fasilitas umum.</p>
        <p><b>Akibat melanggar:</b> mendapat sanksi sesuai peraturan, seperti denda atau hukuman.</p>
      </div>
    </div>

    <div class="card materi">
      <h2>4. Perbedaan Keempat Norma</h2>
      <p>Agar lebih mudah diingat, perhatikan tabel berikut.</p>
      <div class="tabel-geser">
        <table>
          <tr><th>Jenis norma</th><th>Sumber aturan</th><th>Contoh akibat pelanggaran</th></tr>
          <tr><td>Agama</td><td>Ajaran Tuhan</td><td>Dosa</td></tr>
          <tr><td>Kesusilaan</td><td>Hati nurani</td><td>Rasa bersalah</td></tr>
          <tr><td>Kesopanan</td><td>Kebiasaan masyarakat</td><td>Teguran atau celaan</td></tr>
          <tr><td>Hukum</td><td>Peraturan resmi</td><td>Denda atau hukuman</td></tr>
        </table>
      </div>
      <div class="rumus">Cara mudah mengingat:<br>Agama = Tuhan<br>Kesusilaan = Hati nurani<br>Kesopanan = Tata krama<br>Hukum = Peraturan resmi</div>
      <div class="info">🔎 <b>Tips menentukan jenis norma:</b> tanyakan pada diri sendiri, <i>"Aturan ini berasal dari mana?"</i> dan <i>"Apa akibatnya kalau dilanggar?"</i></div>
      <div class="info">🌟 <b>Tahukah kamu?</b> Satu perbuatan bisa melanggar lebih dari satu norma. Contohnya mencuri: dilarang oleh ajaran agama (norma agama), membuat pelaku merasa bersalah (norma kesusilaan), dan dapat dikenai sanksi (norma hukum).</div>
    </div>

    <div class="card materi">
      <h2>5. Norma di Lingkungan Kehidupan Kita</h2>
      <p>Norma harus diterapkan di mana saja, bukan hanya di sekolah.</p>
      <h3>🏠 Di lingkungan keluarga</h3>
      <div class="contoh">
        <p>• Menghormati orang tua.</p>
        <p>• Membantu pekerjaan rumah.</p>
        <p>• Berbicara dengan santun.</p>
        <p>• Meminta izin ketika akan pergi.</p>
      </div>
      <h3>🏫 Di lingkungan sekolah</h3>
      <div class="contoh">
        <p>• Datang tepat waktu.</p>
        <p>• Memakai seragam sesuai aturan.</p>
        <p>• Menghormati guru.</p>
        <p>• Tidak menyontek.</p>
        <p>• Melaksanakan piket kelas.</p>
      </div>
      <h3>🏘️ Di lingkungan masyarakat</h3>
      <div class="contoh">
        <p>• Mengikuti kegiatan gotong royong.</p>
        <p>• Menghormati tetangga.</p>
        <p>• Menjaga kebersihan lingkungan.</p>
        <p>• Tidak mengganggu ketenangan orang lain.</p>
      </div>
    </div>

    <div class="card materi">
      <h2>6. Apa yang Terjadi Jika Kita Tidak Mematuhi Norma?</h2>
      <p>Setiap norma memiliki konsekuensi apabila dilanggar. Contohnya:</p>
      <div class="tabel-geser">
        <table>
          <tr><th>Perbuatan</th><th>Akibat</th></tr>
          <tr><td>Tidak beribadah sesuai ajaran agama</td><td>Bertentangan dengan kewajiban agama</td></tr>
          <tr><td>Berbohong kepada teman</td><td>Hilangnya kepercayaan</td></tr>
          <tr><td>Berbicara kasar kepada guru</td><td>Mendapat teguran</td></tr>
          <tr><td>Mencuri barang orang lain</td><td>Mendapat sanksi hukum</td></tr>
          <tr><td>Membuang sampah sembarangan</td><td>Lingkungan menjadi kotor dan tidak sehat</td></tr>
          <tr><td>Melanggar tata tertib sekolah</td><td>Mendapat teguran atau pembinaan</td></tr>
        </table>
      </div>
      <div class="info">💡 Setiap tindakan memiliki akibat. Karena itu, kita harus <b>berpikir sebelum bertindak</b>.</div>
    </div>

    <div class="card materi">
      <h2>7. Sikap yang Mencerminkan Kepatuhan terhadap Norma</h2>
      <p>Anak yang memahami norma akan menunjukkan perilaku berikut:</p>
      <ul>
        <li>Jujur dalam perkataan dan perbuatan.</li>
        <li>Bertanggung jawab terhadap tugas.</li>
        <li>Menghormati orang lain.</li>
        <li>Menghargai perbedaan agama dan pendapat.</li>
        <li>Disiplin menaati aturan.</li>
        <li>Peduli terhadap lingkungan.</li>
        <li>Mau meminta maaf ketika melakukan kesalahan.</li>
      </ul>
    </div>

    <div class="card materi">
      <h2>⭐ Kesimpulan: Apa yang Harus Kita Ingat?</h2>
      <ul>
        <li>Norma adalah aturan atau pedoman dalam kehidupan manusia.</li>
        <li>Norma bertujuan menciptakan ketertiban, keamanan, dan kerukunan.</li>
        <li>Ada empat jenis norma: <b>agama, kesusilaan, kesopanan, dan hukum</b>.</li>
        <li>Norma berlaku di rumah, sekolah, dan masyarakat.</li>
        <li>Setiap pelanggaran norma dapat menimbulkan konsekuensi.</li>
        <li>Mematuhi norma merupakan bentuk tanggung jawab kita sebagai anggota masyarakat.</li>
      </ul>
      <div class="info">🇮🇩 Mematuhi norma juga cara kita mengamalkan nilai-nilai Pancasila: beribadah sesuai agama (sila ke-1), menghormati sesama dengan adil dan beradab (sila ke-2), serta menjaga persatuan dan kerukunan lewat gotong royong (sila ke-3).</div>
    </div>


    <div class="card">
      <div class="info" style="margin-top:0">⏱️ Setelah menekan tombol di bawah, waktu <b id="m-durasi"></b> menit langsung berjalan. Pastikan kamu siap!</div>
      <button class="btn full" id="btn-mulai">🚀 Mulai Mengerjakan</button>
      <button class="btn full sec" id="btn-kembali1">← Kembali</button>
    </div>
  </section>

  <!-- HALAMAN 3: soal -->
  <section id="p3" hidden>
    <div class="bar">
      <span id="timer">30:00</span>
      <span class="terjawab" id="terjawab">0 / 20 terjawab</span>
    </div>
    <div class="chips" id="chips"></div>
    <div class="card">
      <div class="label-soal"><span class="nomor" id="no-soal"></span><span class="jenis" id="jenis"></span></div>
      <div id="teks"></div>
      <div id="opsi"></div>
    </div>
    <div class="nav">
      <button class="btn sec" id="btn-prev">← Sebelumnya</button>
      <button class="btn" id="btn-next">Selanjutnya →</button>
    </div>
    <button class="btn full warn" id="btn-selesai">✅ Selesai &amp; Kumpulkan</button>
  </section>

  <!-- HALAMAN 4: hasil -->
  <section id="p4" hidden>
    <div class="card">
      <div class="center">
        <h1>🎉 Kerja bagus, <span id="h-nama"></span>!</h1>
        <div class="nilai" id="h-nilai"></div>
        <div id="h-rinci"></div>
        <div class="muted" id="h-waktu"></div>
      </div>
      <h3 style="margin-top:18px">Hasil per bagian</h3>
      <div id="h-bagian"></div>
      <h3 style="margin-top:18px">Hasil per materi</h3>
      <div id="h-materi"></div>
    </div>

    <div class="card">
      <h2>📲 Kirim hasilmu ke guru</h2>
      <p>Tekan tombol hijau di bawah. WhatsApp akan terbuka dengan pesan yang sudah terisi. Lalu tekan tombol <b>Kirim</b> di WhatsApp.</p>
      <a class="btn wa full" id="btn-wa" href="#" target="_blank" rel="noopener">📱 Kirim ke WhatsApp Guru</a>
      <p class="muted" style="margin-top:12px">Kalau WhatsApp tidak terbuka, salin pesan ini lalu kirim ke nomor <b id="h-nomor"></b>:</p>
      <div class="pesan" id="h-pesan"></div>
      <button class="btn full sec" id="btn-salin">📋 Salin Pesan</button>
    </div>

    <div class="card" id="kotak-koreksi" hidden>
      <h2>Koreksi jawabanku</h2>
      <div class="tabel-geser" id="h-koreksi"></div>
    </div>
  </section>
</div>

<script>
// ============================================================
// 1. DATA DAN KEADAAN
//    jenis soal: "pilihan_ganda" (satu jawaban) dan "benar_salah" (studi kasus, beberapa pernyataan)
// ============================================================
const CFG = JSON.parse(document.getElementById('data-soal').textContent);
const SOAL = CFG.soal;
const TOTAL = SOAL.length;
const DURASI = CFG.durasi_menit * 60;
const NAMA_JENIS = { pilihan_ganda: 'Pilihan ganda', benar_salah: 'Studi kasus' };

let nama = '', idx = 0, sisa = DURASI, timer = null, mulaiMs = 0, berjalan = false;
// pilihan_ganda -> huruf ('a'..'d') atau null; benar_salah -> daftar [true/false/null, ...]
let jawab = SOAL.map(s => s.jenis === 'benar_salah' ? new Array(s.pernyataan.length).fill(null) : null);
let pesanWA = '';

const $ = id => document.getElementById(id);
const esc = s => String(s).replace(/[&<>"]/g, c => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;' }[c]));
const fmt = d => Math.floor(d / 60) + ':' + String(d % 60).padStart(2, '0');

// Memeriksa struktur data. Mengembalikan pesan kesalahan, atau '' jika aman.
function cekData(d) {
  if (!d || !Array.isArray(d.soal) || !d.soal.length) return 'Daftar "soal" kosong.';
  for (let i = 0; i < d.soal.length; i++) {
    const s = d.soal[i], no = 'Soal ' + (i + 1) + ': ';
    if (s.jenis === 'pilihan_ganda') {
      if (!s.teks || !s.pilihan || !(s.kunci in s.pilihan)) return no + '"teks", "pilihan", atau "kunci" bermasalah.';
    } else if (s.jenis === 'benar_salah') {
      if (!s.kasus || !Array.isArray(s.pernyataan) || !Array.isArray(s.kunci) || s.pernyataan.length !== s.kunci.length) return no + '"kasus", "pernyataan", atau "kunci" bermasalah.';
    } else return no + '"jenis" tidak dikenal.';
  }
  return '';
}

function nomorWA(v) {                       // 0896... -> 62896...
  let n = String(v).replace(/\D/g, '');
  if (n.startsWith('0')) n = '62' + n.slice(1);
  else if (!n.startsWith('62')) n = '62' + n;
  return n;
}

function halaman(n) {
  ['p1', 'p2', 'p3', 'p4'].forEach((id, i) => { $(id).hidden = (i + 1 !== n); });
  window.scrollTo(0, 0);
}

const galat = cekData(CFG);
if (galat) alert('Data soal bermasalah: ' + galat);

// isi teks awal dari data
const jmlPG = SOAL.filter(s => s.jenis === 'pilihan_ganda').length;
const jmlBS = SOAL.filter(s => s.jenis === 'benar_salah').length;
$('k-sek').textContent = CFG.sekolah;
$('k-program').textContent = CFG.program;
$('k-tag').textContent = '⭐ ' + CFG.tagline + ' ⭐';
$('k-mapel').textContent = CFG.mapel;
$('k-kelas').textContent = CFG.kelas;
$('k-topik').textContent = CFG.topik;
$('k-jml').textContent = TOTAL + ' soal (' + jmlPG + ' pilihan ganda + ' + jmlBS + ' studi kasus benar/salah)';
$('k-durasi').textContent = CFG.durasi_menit;
$('m-durasi').textContent = CFG.durasi_menit;
$('m-judul').textContent = '📖 Materi: ' + CFG.topik;
$('timer').textContent = fmt(DURASI);
$('terjawab').textContent = '0 / ' + TOTAL + ' terjawab';

// ============================================================
// 2. HALAMAN 1 -> 2 -> 3
// ============================================================
function keMateri() {
  nama = $('nama').value.trim();
  if (!nama) { alert('Tulis namamu dulu ya.'); $('nama').focus(); return; }
  $('m-nama').textContent = nama;
  halaman(2);
}

function mulai() {
  sisa = DURASI; mulaiMs = Date.now(); berjalan = true; idx = 0;
  halaman(3);
  $('chips').innerHTML = SOAL.map((s, i) => '<button class="chip" data-i="' + i + '" aria-label="Soal ' + (i + 1) + '">' + (i + 1) + '</button>').join('');
  tampilSoal();
  perbaruiTimer();
  timer = setInterval(() => {
    sisa--;
    perbaruiTimer();
    if (sisa <= 0) { alert('Waktu habis! Jawabanmu dikumpulkan otomatis.'); selesai(true); }
  }, 1000);
}

function perbaruiTimer() {
  const t = $('timer');
  t.textContent = fmt(Math.max(sisa, 0));
  t.className = sisa <= 60 ? 'kritis' : (sisa <= 300 ? 'hampir' : '');
}

// ============================================================
// 3. STATUS JAWABAN
// ============================================================
function lengkap(i) {                        // soal sudah dijawab penuh?
  const a = jawab[i];
  return SOAL[i].jenis === 'benar_salah' ? a.every(x => x !== null) : a !== null;
}
function sebagian(i) {                       // studi kasus baru terisi sebagian?
  const a = jawab[i];
  return SOAL[i].jenis === 'benar_salah' && a.some(x => x !== null) && !lengkap(i);
}
function benar(i) {
  const s = SOAL[i], a = jawab[i];
  return s.jenis === 'benar_salah' ? s.kunci.every((k, j) => a[j] === k) : a === s.kunci;
}

function perbaruiChips() {
  document.querySelectorAll('#chips .chip').forEach((el, i) => {
    el.classList.toggle('isi', lengkap(i));
    el.classList.toggle('sebagian', sebagian(i));
    el.classList.toggle('kini', i === idx);
  });
  $('terjawab').textContent = SOAL.filter((_, i) => lengkap(i)).length + ' / ' + TOTAL + ' terjawab';
}

// ============================================================
// 4. MENAMPILKAN SATU SOAL
// ============================================================
function tampilSoal() {
  const s = SOAL[idx];
  $('no-soal').textContent = 'Soal ' + (idx + 1) + ' dari ' + TOTAL;
  $('jenis').textContent = s.jenis === 'benar_salah' ? 'Studi kasus: Benar atau Salah?' : 'Pilihan ganda';

  if (s.jenis === 'pilihan_ganda') {
    // kalimat dalam tanda kutip = kalimat rumpang; "..." diubah menjadi garis kosong
    $('teks').innerHTML = s.teks.split('\n').map(baris => {
      const kutip = baris.startsWith('"');
      let h = esc(baris);
      if (kutip) h = h.replace(/\.{3,}/g, '<span class="blank"></span>').replace(/&quot;/g, '');
      return '<p class="' + (kutip ? 'kutip' : '') + '">' + h + '</p>';
    }).join('');
    $('opsi').innerHTML = Object.entries(s.pilihan).map(([k, t]) =>
      '<label class="opsi' + (jawab[idx] === k ? ' pilih' : '') + '"><input type="radio" name="opsi" value="' + k + '"' + (jawab[idx] === k ? ' checked' : '') + '>' +
      '<span class="h">' + k.toUpperCase() + '</span><span>' + esc(t) + '</span></label>'
    ).join('');
  } else {
    $('teks').innerHTML = '<div class="kasus">' + s.kasus.split('\n').map(p => '<p style="font-weight:400;font-size:1.04rem">' + esc(p) + '</p>').join('') + '</div>' +
      '<p class="petunjuk">Tentukan setiap pernyataan berikut Benar atau Salah.</p>';
    $('opsi').innerHTML = s.pernyataan.map((p, j) => {
      const a = jawab[idx][j];
      return '<div class="pern' + (a !== null ? ' lengkap' : '') + '"><p>' + (j + 1) + '. ' + esc(p) + '</p><div class="bs">' +
        '<label class="pill' + (a === true ? ' pilih' : '') + '"><input type="radio" name="p' + j + '" value="true"' + (a === true ? ' checked' : '') + '>Benar</label>' +
        '<label class="pill' + (a === false ? ' pilih' : '') + '"><input type="radio" name="p' + j + '" value="false"' + (a === false ? ' checked' : '') + '>Salah</label>' +
        '</div></div>';
    }).join('');
  }
  $('btn-prev').disabled = idx === 0;
  $('btn-next').disabled = idx === TOTAL - 1;
  perbaruiChips();
  window.scrollTo(0, 0);
}

// ============================================================
// 5. SELESAI DAN PENILAIAN
//    pilihan ganda: benar jika huruf sama dengan kunci
//    benar/salah  : benar jika SEMUA pernyataan tepat
// ============================================================
function teksJawaban(s, a, kunci) {
  if (s.jenis === 'benar_salah') return (kunci ? s.kunci : a).map(x => x === null ? '-' : (x ? 'B' : 'S')).join(' ');
  return kunci ? s.kunci.toUpperCase() : (a ? a.toUpperCase() : '-');
}

function selesai(paksa) {
  if (!berjalan) return;
  if (!paksa) {
    const kosong = SOAL.filter((_, i) => !lengkap(i)).length;
    if (!confirm(kosong ? kosong + ' soal belum dijawab lengkap. Yakin ingin mengumpulkan?' : 'Yakin ingin mengumpulkan jawaban?')) return;
  }
  clearInterval(timer);
  berjalan = false;

  const detik = Math.min(Math.round((Date.now() - mulaiMs) / 1000), DURASI);
  const waktu = Math.floor(detik / 60) + ' menit ' + (detik % 60) + ' detik';

  let jumlahBenar = 0;
  const salah = [], perMateri = {}, perBagian = {};
  SOAL.forEach((s, i) => {
    const ok = benar(i);
    if (ok) jumlahBenar++; else salah.push(i + 1);
    const m = (perMateri[s.materi] = perMateri[s.materi] || { b: 0, t: 0 });
    const g = (perBagian[NAMA_JENIS[s.jenis]] = perBagian[NAMA_JENIS[s.jenis]] || { b: 0, t: 0 });
    m.t++; g.t++;
    if (ok) { m.b++; g.b++; }
  });
  const nilai = Math.round(jumlahBenar * 100 / TOTAL);

  const barisBar = obj => Object.entries(obj).map(([n, v]) =>
    '<div class="bar-materi"><span class="n">' + esc(n) + '</span><span class="t"><i style="width:' + (v.b * 100 / v.t) + '%"></i></span><b>' + v.b + '/' + v.t + '</b></div>').join('');
  const ringkas = obj => Object.entries(obj).map(([n, v]) => n + ' ' + v.b + '/' + v.t).join(' | ');

  $('h-nama').textContent = nama;
  $('h-nilai').textContent = nilai + ' / 100';
  $('h-rinci').innerHTML = '<b>' + jumlahBenar + '</b> dari <b>' + TOTAL + '</b> soal benar';
  $('h-waktu').textContent = '⏱️ Waktu: ' + waktu;
  $('h-bagian').innerHTML = barisBar(perBagian);
  $('h-materi').innerHTML = barisBar(perMateri);

  pesanWA = [
    '*HASIL PENGAYAAN BELAJAR DI RUMAH*',
    '🏫 ' + CFG.sekolah,
    '📚 ' + CFG.mapel + ' - ' + CFG.topik,
    '------------------------',
    '👤 Nama: ' + nama,
    '📊 Nilai: ' + nilai + ' / 100',
    '✅ Benar: ' + jumlahBenar + ' / ' + TOTAL,
    '⏱️ Waktu: ' + waktu,
    '❌ Soal salah: ' + (salah.length ? salah.join(', ') : 'tidak ada'),
    '📌 Per bagian: ' + ringkas(perBagian),
    '📌 Per materi: ' + ringkas(perMateri)
  ].join('\n');
  $('h-pesan').textContent = pesanWA;
  $('h-nomor').textContent = CFG.nomor_wa;
  $('btn-wa').href = 'https://wa.me/' + nomorWA(CFG.nomor_wa) + '?text=' + encodeURIComponent(pesanWA);

  if (CFG.tampilkan_koreksi) {
    $('kotak-koreksi').hidden = false;
    $('h-koreksi').innerHTML = '<table><tr><th>No</th><th>Jawabanmu</th><th>Kunci</th><th></th></tr>' +
      SOAL.map((s, i) => {
        const ok = benar(i);
        return '<tr class="' + (ok ? 'ok' : 'bad') + '"><td>' + (i + 1) + '</td><td>' + teksJawaban(s, jawab[i], false) + '</td><td>' + teksJawaban(s, jawab[i], true) + '</td><td>' + (ok ? '✓' : '✗') + '</td></tr>' +
          (s.pembahasan ? '<tr class="' + (ok ? 'ok' : 'bad') + '"><td></td><td colspan="3" class="pbh">' + esc(s.pembahasan) + '</td></tr>' : '');
      }).join('') + '</table><p class="muted">B = Benar, S = Salah</p>';
  }
  halaman(4);
}

// ============================================================
// 6. TOMBOL
// ============================================================
$('btn-lanjut1').addEventListener('click', keMateri);
$('nama').addEventListener('keydown', e => { if (e.key === 'Enter') keMateri(); });
$('btn-kembali1').addEventListener('click', () => halaman(1));
$('btn-mulai').addEventListener('click', mulai);
$('btn-prev').addEventListener('click', () => { if (idx > 0) { idx--; tampilSoal(); } });
$('btn-next').addEventListener('click', () => { if (idx < TOTAL - 1) { idx++; tampilSoal(); } });
$('btn-selesai').addEventListener('click', () => selesai(false));
$('chips').addEventListener('click', e => {
  const b = e.target.closest('.chip');
  if (b) { idx = +b.dataset.i; tampilSoal(); }
});
// jawaban dipilih (pilihan ganda: name="opsi"; benar/salah: name="p<nomor pernyataan>")
$('opsi').addEventListener('change', e => {
  const t = e.target;
  if (t.name === 'opsi') {
    jawab[idx] = t.value;
    document.querySelectorAll('#opsi .opsi').forEach(l => l.classList.toggle('pilih', l.querySelector('input').checked));
  } else if (/^p\d+$/.test(t.name)) {
    const j = +t.name.slice(1);
    jawab[idx][j] = (t.value === 'true');
    const kartu = t.closest('.pern');
    kartu.classList.add('lengkap');
    kartu.querySelectorAll('.pill').forEach(l => l.classList.toggle('pilih', l.querySelector('input').checked));
  }
  perbaruiChips();
});
$('btn-salin').addEventListener('click', () => {
  const selesaiSalin = () => { $('btn-salin').textContent = '✅ Tersalin!'; setTimeout(() => { $('btn-salin').textContent = '📋 Salin Pesan'; }, 2000); };
  const cadangan = () => {
    const ta = document.createElement('textarea');
    ta.value = pesanWA; document.body.appendChild(ta); ta.select();
    try { document.execCommand('copy'); selesaiSalin(); } catch (x) { alert('Salin manual: tekan lama pada pesan, lalu pilih Salin.'); }
    document.body.removeChild(ta);
  };
  if (navigator.clipboard && window.isSecureContext) navigator.clipboard.writeText(pesanWA).then(selesaiSalin, cadangan);
  else cadangan();
});
window.addEventListener('beforeunload', e => { if (berjalan) { e.preventDefault(); e.returnValue = ''; } });
</script>
</body>
</html>
