<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kuis Ujian Interaktif Kelas 11</title>
    <style>
        :root {
            --primary-color: #2563eb;
            --primary-hover: #1d4ed8;
            --bg-color: #f8fafc;
            --card-bg: #ffffff;
            --text-color: #1e293b;
            --border-color: #e2e8f0;
            --correct-color: #16a34a;
            --wrong-color: #dc2626;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 800px;
            background: var(--card-bg);
            border-radius: 12px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
            padding: 30px;
        }

        h1, h2, h3 {
            text-align: center;
            margin-bottom: 20px;
            color: var(--primary-color);
        }

        .hidden {
            display: none !important;
        }

        /* Form Styling */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }

        input, select {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        input:focus, select:focus {
            border-color: var(--primary-color);
        }

        /* Grid Mapel */
        .mapel-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .btn-mapel {
            background-color: #f1f5f9;
            border: 2px solid var(--border-color);
            padding: 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            color: var(--text-color);
            transition: all 0.2s;
            text-align: center;
        }

        .btn-mapel:hover {
            background-color: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }

        /* Soal Styling */
        .question-card {
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            background-color: #fafafa;
        }

        .question-text {
            font-weight: 600;
            margin-bottom: 15px;
            font-size: 1.05rem;
        }

        .options-list {
            list-style: none;
        }

        .option-item {
            margin-bottom: 10px;
        }

        .option-label {
            display: flex;
            align-items: center;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            background-color: white;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .option-label:hover {
            background-color: #f1f5f9;
        }

        .option-label input {
            width: auto;
            margin-right: 12px;
        }

        /* Button Main */
        .btn-submit {
            width: 100%;
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 14px;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            transition: background-color 0.2s;
            margin-top: 10px;
        }

        .btn-submit:disabled {
            background-color: #94a3b8;
            cursor: not-allowed;
        }

        .btn-submit:hover:not(:disabled) {
            background-color: var(--primary-hover);
        }

        /* Skor & Hasil */
        .score-box {
            text-align: center;
            background-color: #eff6ff;
            padding: 25px;
            border-radius: 8px;
            margin-bottom: 25px;
        }

        .score-num {
            font-size: 3rem;
            font-weight: bold;
            color: var(--primary-color);
        }

        .review-card {
            border-left: 4px solid var(--border-color);
            padding: 15px;
            margin-bottom: 15px;
            background-color: white;
            border-radius: 0 8px 8px 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        .review-card.correct {
            border-left-color: var(--correct-color);
        }

        .review-card.wrong {
            border-left-color: var(--wrong-color);
        }

        .status-badge {
            display: inline-block;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.85rem;
            font-weight: bold;
            color: white;
            margin-bottom: 8px;
        }

        .bg-correct { background-color: var(--correct-color); }
        .bg-wrong { background-color: var(--wrong-color); }

        .explanation {
            margin-top: 8px;
            font-size: 0.95rem;
            color: #475569;
            background-color: #f8fafc;
            padding: 8px;
            border-radius: 4px;
        }

        /* Penutup */
        .footer-section {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 2px dashed var(--border-color);
            text-align: center;
        }

        .motivation-quote {
            font-style: italic;
            color: #475569;
            margin-top: 8px;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- BAGIAN 1: FORM IDENTITAS SISWA -->
    <div id="section-identity">
        <h1>Ujian Online Kelas 11</h1>
        <p style="text-align: center; margin-bottom: 25px; color: #64748b;">Silakan isi identitas Anda terlebih dahulu untuk memulai ujian.</p>
        
        <form id="identity-form">
            <div class="form-group">
                <label for="nama">Nama Lengkap</label>
                <input type="text" id="nama" placeholder="Masukkan nama lengkap Anda" required>
            </div>

            <div class="form-group">
                <label for="absen">Nomor Absen</label>
                <input type="number" id="absen" min="1" max="50" placeholder="Contoh: 12" required>
            </div>

            <div class="form-group">
                <label for="kelas">Kelas</label>
                <select id="kelas" required>
                    <option value="">-- Pilih Kelas --</option>
                    <option value="11 TJKT 1">11 TJKT 1</option>
                    <option value="11 TJKT 2">11 TJKT 2</option>
                    <option value="11 TJKT 3">11 TJKT 3</option>
                </select>
            </div>

            <button type="button" id="btn-start" class="btn-submit" disabled>Mulai Kuis</button>
        </form>
    </div>

    <!-- BAGIAN 2: PEMILIHAN MATA PELAJARAN -->
    <div id="section-mapel" class="hidden">
        <h2>Pilih Mata Pelajaran</h2>
        <p style="text-align: center; color: #64748b;">Halo <span id="user-display-name" style="font-weight: bold;"></span>, silakan pilih mata pelajaran yang ingin diujikan:</p>
        
        <div class="mapel-grid">
            <button class="btn-mapel" onclick="selectMapel('indo')">Bahasa Indonesia</button>
            <button class="btn-mapel" onclick="selectMapel('sejarah')">Sejarah</button>
            <button class="btn-mapel" onclick="selectMapel('mtk')">Matematika</button>
            <button class="btn-mapel" onclick="selectMapel('tjkt')">TJKT</button>
        </div>
    </div>

    <!-- BAGIAN 3: LEMBAR SOAL KUIS -->
    <div id="section-quiz" class="hidden">
        <h2 id="quiz-title">Soal Ujian</h2>
        <p style="text-align: center; margin-bottom: 20px; color: #64748b;">Jawablah 20 soal pilihan ganda di bawah ini dengan teliti.</p>
        
        <form id="quiz-form">
            <div id="questions-container"></div>
            <button type="submit" class="btn-submit">Kirim Jawaban (Submit)</button>
        </form>
    </div>

    <!-- BAGIAN 4: HASIL / SKOR & KUNCI JAWABAN -->
    <div id="section-result" class="hidden">
        <h2>Hasil Ujian</h2>
        
        <div class="score-box">
            <p>Nilai Akhir Anda:</p>
            <div class="score-num" id="final-score">0</div>
            <p id="score-summary" style="margin-top: 10px; font-weight: 500;"></p>
        </div>

        <h3>Kunci Jawaban & Pembahasan</h3>
        <div id="review-container"></div>

        <!-- BAGIAN 5: PENUTUP -->
        <div class="footer-section">
            <h3>Terima Kasih!</h3>
            <p>Terima kasih telah mengikuti ujian ini dengan jujur dan tertib.</p>
            <p class="motivation-quote">"Jangan pernah berhenti belajar, karena hidup tidak pernah berhenti mengajarkan. Tetap semangat dan tingkatkan lagi giat belajarmu untuk meraih cita-cita!"</p>
        </div>
    </div>

</div>

<script>
    // DATA SOAL (20 Soal Per Mapel - Medium Level Kelas 11)
    const questionsData = {
        indo: [
            { q: "Berikut yang merupakan struktur teks prosedur yang tepat adalah...", o: ["Tesis, Argumentasi, Penutup", "Tujuan, Langkah-langkah, Penegasan Ulang", "Orientasi, Komplikasi, Resolusi", "Pernyataan Umum, Deretan Penjelas, Interpretasi", "Abstraksi, Orientasi, Krisis"], a: 1, e: "Struktur teks prosedur terdiri atas Tujuan, Langkah-langkah, dan Penegasan Ulang." },
            { q: "Kalimat imperatif dalam teks prosedur ditandai dengan...", o: ["Penggunaan kata kerja aktif transitif", "Penggunaan kalimat perintah/larangan", "Penggunaan kata hubung temporal", "Penggunaan kata sifat berlebihan", "Penggunaan data statistik"], a: 1, e: "Kalimat imperatif adalah kalimat yang berisi perintah atau larangan." },
            { q: "Salah satu ciri bahasa dalam teks eksplanasi adalah menggunakan kata kerja material dan rasional, artinya...", o: ["Menunjukkan tindakan fisik dan hubungan sebab akibat", "Mengandung unsur fiksi dan imajinasi", "Menggunakan bahasa kiasan", "Menggunakan sudut pandang orang pertama", "Menggunakan kalimat tanya"], a: 0, e: "Kata kerja material menunjukkan tindakan fisik, sedangkan rasional menyatakan hubungan sebab-akibat." },
            { q: "Bagian teks ceramah yang berisi argumen-argumen pembicara disebut...", o: ["Pendahuluan", "Isi/Rangkaian Argumen", "Penutup", "Tesis", "Orientasi"], a: 1, e: "Bagian isi berisi rangkaian argumen pendukung topik ceramah." },
            { q: "Unsur ekstrinsik cerpen yang berkaitan dengan nilai-nilai kemasyarakatan adalah...", o: ["Nilai Moral", "Nilai Sosial", "Nilai Estetika", "Nilai Budaya", "Nilai Agama"], a: 1, e: "Nilai sosial berhubungan erat dengan interaksi antarmanusia di masyarakat." },
            { q: "Struktur resensi buku yang berisi gambaran umum mengenai isi buku adalah...", o: ["Identitas Buku", "Orientasi", "Sinopsis", "Analisis", "Evaluasi"], a: 2, e: "Sinopsis menyajikan ringkasan/gambaran umum isi buku." },
            { q: "Penggunaan konjungsi kausalitas terdapat dalam kalimat...", o: ["Budi pergi ke sekolah lalu belajar", "Ia tidak masuk sekolah karena sakit", "Meskipun hujan, dia tetap berangkat", "Ibu memasak dan ayah membaca", "Jika hari hujan, saya membawa payung"], a: 1, e: "'Karena' merupakan konjungsi kausalitas (sebab-akibat)." },
            { q: "Dalam proposal kegiatan, bagian 'Latar Belakang' berisi tentang...", o: ["Rincian biaya kegiatan", "Alasan atau pemikiran terselenggaranya kegiatan", "Jadwal pelaksanaan", "Susunan panitia", "Tujuan kegiatan"], a: 1, e: "Latar belakang mendasari mengapa suatu kegiatan perlu dilaksanakan." },
            { q: "Kalimat bernada lugas dan objektif merupakan ciri bahasa dalam...", o: ["Puisi", "Karya Tulis Ilmiah", "Novel", "Cerpen", "Drama"], a: 1, e: "Karya ilmiah menuntut penggunaan bahasa baku, denotatif (lugas), dan objektif." },
            { q: "Bagian karya ilmiah yang berisi daftar buku/sumber rujukan disebut...", o: ["Lampiran", "Glosarium", "Daftar Pustaka", "Catatan Kaki", "Abstrak"], a: 2, e: "Daftar Pustaka mencantumkan semua sumber rujukan yang digunakan." },
            { q: "Berikut yang BUKAN merupakan jenis drama berdasarkan sarana pementasannya adalah...", o: ["Drama Panggung", "Drama Radio", "Drama Televisi", "Drama Tragedi", "Drama Film"], a: 3, e: "Tragedi adalah jenis drama berdasarkan isi ceritanya, bukan sarana media pementasan." },
            { q: "Tokoh yang berfungsi sebagai penengah dalam konflik drama disebut...", o: ["Protagonis", "Antagonis", "Tritagonis", "Figuran", "Utama"], a: 2, e: "Tritagonis adalah tokoh penengah/pembantu." },
            { q: "Tahapan alur cerpen tempat terjadinya konflik puncak disebut...", o: ["Pengenalan", "Klimaks", "Antiklimaks", "Resolusi", "Krisis"], a: 1, e: "Klimaks adalah titik puncak ketegangan atau konflik." },
            { q: "Kalimat yang menggunakan kata berkonotasi positif adalah...", o: ["Ia menjadi buah bibir karena prestasinya", "Ia ditangkap polisi karena mencuri", "Wajahnya cemberut seharian", "Rumahnya sangat kotor", "Anak itu sangat nakal"], a: 0, e: "'Buah bibir' karena prestasi bermakna positif (menjadi bahan pujian)." },
            { q: "Perbedaan utama antara cerita pendek dan novel terletak pada...", o: ["Adanya alur cerita", "Kompleksitas masalah dan panjang cerita", "Penggunaan tokoh", "Adanya tema", "Penggunaan bahasa"], a: 1, e: "Cerpen fokus pada satu konflik utama, sedangkan novel lebih kompleks dan panjang." },
            { q: "Ciri khas kalimat penutup surat resmi yang benar adalah...", o: ["Atas perhatiannya, diucapkan terima kasih banyak.", "Atas perhatian Bapak/Ibu, kami ucapkan terima kasih.", "Sekian dan terima kasih.", "Semoga Bapak menyetujuinya.", "Demikian agar dimaklumi adanya."], a: 1, e: "Penggunaan kata sapaan 'Bapak/Ibu' dan 'terima kasih' tanpa '-nya' sesuai tata bahasa baku." },
            { q: "Sistematika proposal penulisan yang memuat langkah kerja adalah...", o: ["Metode Penelitian", "Tujuan Penelitian", "Manfaat Penelitian", "Tinjauan Pustaka", "Rumusan Masalah"], a: 0, e: "Metode penelitian menjabarkan tahapan dan langkah kerja." },
            { q: "Kata ilmiah 'hipotesis' memiliki arti...", o: ["Kesimpulan akhir", "Dugaan/jawaban sementara", "Pengumpulan data", "Hasil pengamatan", "Analisis data"], a: 1, e: "Hipotesis adalah dugaan sementara yang harus dibuktikan kebenarannya." },
            { q: "Dalam drama, percakapan seorang pemain dengan dirinya sendiri disebut...", o: ["Monolog", "Dialog", "Prolog", "Epilog", "MIMIK"], a: 0, e: "Monolog adalah percakapan tunggal/dengan diri sendiri." },
            { q: "Esai yang membahas tentang masalah kebudayaan atau karya seni disebut esai...", o: ["Sastra/Kritik", "Deskriptif", "Tajuk", "Pribadi", "Reflektif"], a: 0, e: "Esai kritik/sastra membahas karya seni dan kebudayaan secara mendalam." }
        ],
        sejarah: [
            { q: "Tujuan utama kedatangan bangsa Barat ke Nusantara pada abad ke-16 adalah...", o: ["Menyebarkan agama Islam", "Mencari rempah-rempah", "Membangun pangkalan militer", "Membantu kerajaan lokal", "Melakukan studi kebudayaan"], a: 1, e: "Tujuan awal bangsa Eropa datang adalah berburu rempah-rempah akibat jatuhnya Konstantinopel." },
            { q: "Sistem Tanam Paksa (Cultuurstelsel) di Indonesia diperkenalkan oleh...", o: ["Raffles", "Daendels", "Van den Bosch", "Jan Pieterszoon Coen", "Van Deventer"], a: 2, e: "Gubernur Jenderal Johannes van den Bosch mencanangkan Tanam Paksa pada tahun 1830." },
            { q: "Kebijakan VOC untuk memusnahkan tanaman rempah-rempah yang berlebih dinamakan...", o: ["Hongi Tochten", "Pelayaran Hongi", "Ekstirpasi", "Contingenten", "Verplichte Leverantie"], a: 2, e: "Ekstirpasi adalah hak VOC memusnahkan pohon rempah-rempah agar harga tidak anjlok." },
            { q: "Tokoh yang memimpin Perang Paderi di Sumatera Barat adalah...", o: ["Pangeran Diponegoro", "Tuanku Imam Bonjol", "Sisingamangaraja XII", "Cut Nyak Dien", "Sultan Hasanuddin"], a: 1, e: "Perang Paderi dipimpin oleh Tuanku Imam Bonjol." },
            { q: "Dampak positif dari pelaksanaan Politik Etis bagi bangsa Indonesia adalah...", o: ["Lahirnya golongan terpelajar/intelektual", "Ekonomi rakyat makin makmur", "Pemerintahan kolonial berakhir", "Hilangnya monopoli perdagangan", "Sistem perbudakan dihapus"], a: 0, e: "Program edukasi dalam Politik Etis melahirkan elite terpelajar yang merintis Pergerakan Nasional." },
            { q: "Organisasi pergerakan nasional pertama yang berdiri di Indonesia pada tahun 1908 adalah...", o: ["Sarekat Islam", "Indische Partij", "Budi Utomo", "PNI", "Muhammadiyah"], a: 2, e: "Budi Utomo didirikan pada 20 Mei 1908 oleh Dr. Soetomo dan para mahasiswa STOVIA." },
            { q: "Kongres Pemuda II tanggal 28 Oktober 1928 menghasilkan sebuah ikrar bersejarah yaitu...", o: ["Pancasila", "Proklamasi", "Sumpah Pemuda", "UUD 1945", "Dwikora"], a: 2, e: "Kongres Pemuda II menghasilkan Sumpah Pemuda." },
            { q: "Organisasi bentukan Jepang yang bertujuan melatih pemuda dalam bidang militer adalah...", o: ["Seinedan", "PUTERA", "PETA", "Heiho", "Keibodan"], a: 2, e: "PETA (Pembela Tanah Air) dibentuk untuk latihan militer bentukan Jepang." },
            { q: "Tokoh yang menjahit Bendera Pusaka Merah Putih saat Proklamasi adalah...", o: ["Sayuti Melik", "Fatmawati", "Sukarni", "Laksamana Maeda", "S. Suhud"], a: 1, e: "Ibu Fatmawati menjahit Bendera Pusaka Merah Putih." },
            { q: "Teks Proklamasi Kemerdekaan Indonesia diketik oleh...", o: ["Ir. Soekarno", "Drs. Mohammad Hatta", "Sayuti Melik", "Ahmad Soebardjo", "Sukarni"], a: 2, e: "Sayuti Melik bertugas mengetik draf naskah Proklamasi." },
            { q: "Peristiwa Rengasdengklok terjadi karena adanya perbedaan pendapat antara kelompok muda dan tua mengenai...", o: ["Waktu pelaksanaan proklamasi", "Tempat pembacaan teks proklamasi", "Tokoh yang menandatangani teks", "Isi dari naskah proklamasi", "Bentuk negara Indonesia"], a: 0, e: "Pemuda menginginkan proklamasi dilakukan secepatnya tanpa campur tangan PPKI/Jepang." },
            { q: "Pemerintah kolonial Belanda menyerah tanpa syarat kepada Jepang di...", o: ["Kalijati, Subang", "Linggarjati, Cirebon", "Renville, Jakarta", "Roem-Royen", "KMB, Den Haag"], a: 0, e: "Perjanjian Kalijati (8 Maret 1942) menandai menyerahnya Belanda ke Jepang." },
            { q: "Surat kabar pertama yang menyebarkan berita proklamasi adalah...", o: ["Medan Prijaji", "Soeara Asia", "Jawa Hokokai", "Kompas", "Republika"], a: 1, e: "Harian Soeara Asia di Surabaya memuat berita kemerdekaan Indonesia." },
            { q: "Tugas utama AFNEI di Indonesia pasca kekalahan Jepang adalah...", o: ["Menjajah kembali Indonesia", "Menerima penyerahan kekuasaan dari Jepang dan melucuti senjata mereka", "Membantu perjuangan Indonesia", "Mendirikan negara boneka", "Mengambil alih kekayaan alam"], a: 1, e: "AFNEI bertugas melucuti tentara Jepang dan mengembalikan tawanan perang." },
            { q: "Sultan Hasanuddin mendapatkan julukan 'Ayam Jantan dari Timur' karena...", o: ["Keberaniannya melawan VOC di Makassar", "Penguasai wilayah Timur terluas", "Memiliki pasukan tak terkalahkan", "Bekerja sama dengan VOC", "Raja pertama di Indonesia"], a: 0, e: "Belanda menjuluki Sultan Hasanuddin karena kegigihan dan keberaniannya." },
            { q: "Strategi Devide et Impera yang diterapkan Belanda memiliki arti...", o: ["Sistem tanam paksa", "Sistem politik pecah belah", "Kerja rodi tanpa upah", "Monopoli perdagangan", "Perang gerilya"], a: 1, e: "Devide et Impera adalah strategi adu domba/pecah belah kerajaan lokal." },
            { q: "Pemimpin perlawanan rakyat Maluku terhadap Belanda pada tahun 1817 adalah...", o: ["Pangeran Antasari", "Pattimura (Thomas Matulessy)", "Sultan Baabullah", "Silas Papare", "I Gusti Ketut Jelantik"], a: 1, e: "Kapitan Pattimura memimpin perlawanan di Saparua, Maluku." },
            { q: "Berikut ini yang BUKAN merupakan empat serangkai pemimpin PUTERA adalah...", o: ["Ir. Soekarno", "Drs. Mohammad Hatta", "Ki Hajar Dewantara", "K.H. Mas Mansyur", "Sutan Sjahrir"], a: 4, e: "Empat Serangkai adalah Soekarno, Hatta, Ki Hajar Dewantara, dan KH Mas Mansyur." },
            { q: "Latar belakang lahirnya Perang Diponegoro (1825-1830) adalah...", o: ["Pemasangan patok jalan oleh Belanda yang melintasi makam leluhur Diponegoro", "Monopoli rempah-rempah di Yogyakarta", "Penangkapan Sultan Hamengkubuwono I", "Penutupan pesantren di Jawa", "Pengangkatan raja baru oleh Belanda"], a: 0, e: "Insiden tancap patok di tanah milik Diponegoro memicu terjadinya Perang Jawa." },
            { q: "Sidang pertama PPKI tanggal 18 Agustus 1945 menghasilkan keputusan...", o: ["Membentuk Tentara Keamanan Rakyat", "Mengesahkan UUD 1945 dan memilih Presiden/Wapres", "Membentuk Kabinet Pertama", "Membagi wilayah RI menjadi 8 provinsi", "Merumuskan Pancasila"], a: 1, e: "Sidang PPKI 18 Agustus menetapkan UUD 1945 dan mengesahkan Soekarno-Hatta sebagai Presiden & Wapres." }
        ],
        mtk: [
            { q: "Jika $f(x) = 2x + 3$ dan $g(x) = x^2 - 1$, maka nilai $(f \\circ g)(2)$ adalah...", o: ["5", "7", "9", "11", "13"], a: 2, e: "$g(2) = 2^2 - 1 = 3$. Maka $f(g(2)) = f(3) = 2(3) + 3 = 9$." },
            { q: "Invers dari fungsi $f(x) = \\frac{2x + 1}{x - 3}, x \\neq 3$ adalah...", o: ["\\frac{3x + 1}{x - 2}", "\\frac{3x - 1}{x + 2}", "\\frac{2x - 3}{x + 1}", "\\frac{x + 3}{2x - 1}", "\\frac{3x + 2}{x - 1}"], a: 0, e: "Gunakan rumus invers matriks/persamaan rasional: $f^{-1}(x) = \\frac{dx + b}{-cx + a} = \\frac{3x + 1}{x - 2}$." },
            { q: "Persamaan lingkaran yang berpusat di (0,0) dan melalui titik (3, 4) adalah...", o: ["$x^2 + y^2 = 7$", "$x^2 + y^2 = 12$", "$x^2 + y^2 = 25$", "$x^2 + y^2 = 49$", "$x^2 + y^2 = 16$"], a: 2, e: "Jari-jari $r = \\sqrt{3^2 + 4^2} = 5$. Persamaan lingkaran: $x^2 + y^2 = r^2 = 25$." },
            { q: "Pusat dan jari-jari dari lingkaran $x^2 + y^2 - 4x + 6y - 12 = 0$ berturut-turut adalah...", o: ["(2, -3) dan 5", "(-2, 3) dan 5", "(2, 3) dan 25", "(-4, 6) dan 12", "(4, -6) dan 5"], a: 0, e: "Pusat $(-A/2, -B/2) = (2, -3)$. $r = \\sqrt{2^2 + (-3)^2 - (-12)} = \\sqrt{4+9+12} = 5$." },
            { q: "Diketahui matriks $A = \\begin{pmatrix} 2 & 3 \\\\ 1 & 4 \\end{pmatrix}$. Determinan dari matriks A adalah...", o: ["5", "8", "10", "11", "14"], a: 0, e: "Det(A) = $(ad - bc) = (2 \\cdot 4) - (3 \\cdot 1) = 8 - 3 = 5$." },
            { q: "Suku ke-10 dari barisan aritmatika 3, 7, 11, 15, ... adalah...", o: ["35", "39", "41", "43", "45"], a: 1, e: "$a = 3, b = 4$. $U_{10} = a + 9b = 3 + 9(4) = 39$." },
            { q: "Jumlah 8 suku pertama dari deret geometri 2 + 4 + 8 + 16 + ... adalah...", o: ["254", "256", "510", "512", "1022"], a: 2, e: "$a=2, r=2$. $S_8 = \\frac{2(2^8 - 1)}{2 - 1} = 2(255) = 510$." },
            { q: "Nilai dari $\\lim_{x \\to 3} \\frac{x^2 - 9}{x - 3}$ adalah...", o: ["0", "3", "6", "9", "Tak terhingga"], a: 2, e: "Faktorkan: $\\frac{(x-3)(x+3)}{x-3} = x+3$. Substitusi $x=3 \\Rightarrow 3+3 = 6$." },
            { q: "Turunan pertama dari fungsi $f(x) = 3x^3 - 2x^2 + 5x - 7$ adalah...", o: ["$9x^2 - 4x + 5$", "$9x^2 - 2x + 5$", "$6x^2 - 4x + 5$", "$3x^2 - 4x$", "$9x^3 - 4x^2 + 5$"], a: 0, e: "$f'(x) = 3(3)x^2 - 2(2)x + 5 = 9x^2 - 4x + 5$." },
            { q: "Turunan pertama dari $f(x) = (2x + 3)^4$ adalah...", o: ["$4(2x + 3)^3$", "$8(2x + 3)^3$", "$2(2x + 3)^3$", "$12(2x + 3)^3$", "$16(2x + 3)^3$"], a: 1, e: "Aturan rantai: $f'(x) = 4(2x+3)^3 \\cdot 2 = 8(2x+3)^3$." },
            { q: "Integral tak tentu dari $\\int (6x^2 - 4x + 3) dx$ adalah...", o: ["$2x^3 - 2x^2 + 3x + C$", "$3x^3 - 2x^2 + 3x + C$", "$6x^3 - 4x^2 + 3x + C$", "$2x^3 - 4x^2 + 3x + C$", "$x^3 - 2x^2 + 3x + C$"], a: 0, e: "$\\int (6x^2 - 4x + 3) dx = \\frac{6}{3}x^3 - \\frac{4}{2}x^2 + 3x + C = 2x^3 - 2x^2 + 3x + C$." },
            { q: "Nilai dari $\\int_{0}^{2} (3x^2 + 2x) dx$ adalah...", o: ["10", "12", "14", "16", "18"], a: 1, e: "$[x^3 + x^2]_0^2 = (2^3 + 2^2) - (0) = 8 + 4 = 12$." },
            { q: "Sebuah dadu dilempar sekali. Peluang muncul angka prima adalah...", o: ["1/6", "2/6", "3/6", "4/6", "5/6"], a: 2, e: "Angka prima pada dadu = {2, 3, 5} (3 angka). Peluang = 3/6 = 1/2." },
            { q: "Banyaknya cara menyusun 4 orang duduk berdampingan dalam satu baris adalah...", o: ["6", "12", "24", "48", "120"], a: 2, e: "Permutasi $4! = 4 \\times 3 \\times 2 \\times 1 = 24$ cara." },
            { q: "Modus dari data: 5, 6, 7, 7, 8, 8, 8, 9, 10 adalah...", o: ["6", "7", "8", "9", "10"], a: 2, e: "Modus adalah nilai yang paling sering muncul, yaitu 8 (3 kali)." },
            { q: "Bayangan titik A(2, 3) jika ditranslasikan oleh $T = (3, -1)$ adalah...", o: ["(5, 2)", "(5, 4)", "(-1, 4)", "(1, 2)", "(6, -3)"], a: 0, e: "$A' = (2+3, 3+(-1)) = (5, 2)$." },
            { q: "Bayangan titik B(-1, 4) jika dicerminkan terhadap garis $y = x$ adalah...", o: ["(1, -4)", "(4, -1)", "(-4, 1)", "(-1, -4)", "(4, 1)"], a: 1, e: "Refleksi garis $y=x$: $(x,y) \\rightarrow (y,x) \\Rightarrow (-1,4) \\rightarrow (4, -1)$." },
            { q: "Diketahui $\\sin A = \\frac{3}{5}$ di kuadran I. Nilai $\\cos A$ adalah...", o: ["4/5", "3/4", "5/4", "3/5", "1/5"], a: 0, e: "Sisi samping = $\\sqrt{5^2 - 3^2} = 4$. Maka $\\cos A = 4/5$." },
            { q: "Nilai dari $\\cos 120^\\circ$ adalah...", o: ["1/2", "$\\frac{1}{2}\\sqrt{3}$", "-1/2", "$-\\frac{1}{2}\\sqrt{3}$", "0"], a: 2, e: "$\\cos(180^\\circ - 60^\\circ) = -\\cos 60^\\circ = -1/2$ (Kuadran II)." },
            { q: "Simpangan rata-rata dari data: 4, 6, 8, 10, 12 adalah...", o: ["2", "2.4", "3", "3.2", "4"], a: 1, e: "Rata-rata $(\\bar{x}) = 40/5 = 8$. Deviasi: $|4-8|+|6-8|+|8-8|+|10-8|+|12-8| = 4+2+0+2+4 = 12$. SR = $12/5 = 2.4$." }
        ],
        tjkt: [
            { q: "Urutan warna standar Internasional T568B untuk kabel UTP straight adalah...", o: ["Putih-Oranye, Oranye, Putih-Hijau, Biru, Putih-Biru, Hijau, Putih-Cokelat, Cokelat", "Putih-Hijau, Hijau, Putih-Oranye, Biru, Putih-Biru, Oranye, Putih-Cokelat, Cokelat", "Putih-Oranye, Oranye, Putih-Hijau, Hijau, Putih-Biru, Biru, Putih-Cokelat, Cokelat", "Putih-Cokelat, Cokelat, Putih-Hijau, Biru, Putih-Biru, Hijau, Putih-Oranye, Oranye", "Putih-Biru, Biru, Putih-Oranye, Oranye, Putih-Hijau, Hijau, Putih-Cokelat, Cokelat"], a: 0, e: "Standar T568B dimulai dari Putih-Oranye, Oranye, Putih-Hijau, Biru, Putih-Biru, Hijau, Putih-Cokelat, Cokelat." },
            { q: "Subnet mask default untuk IP Address Kelas C (/24) adalah...", o: ["255.0.0.0", "255.255.0.0", "255.255.255.0", "255.255.255.128", "255.255.255.252"], a: 2, e: "Prefix /24 setara dengan 255.255.255.0." },
            { q: "Perangkat jaringan Mikrotik yang berfungsi menghubungkan dua jaringan berbeda subnet adalah...", o: ["Switch", "Router", "Hub", "Access Point", "Repeater"], a: 1, e: "Router bekerja pada Layer 3 untuk menghubungkan antar jaringan/subnet yang beda." },
            { q: "Layanan jaringan yang memberikan alamat IP secara otomatis ke klien dinamakan...", o: ["DNS", "DHCP", "FTP", "Web Server", "SSH"], a: 1, e: "DHCP (Dynamic Host Configuration Protocol) bertugas membagikan IP otomatis." },
            { q: "Port default yang digunakan untuk layanan HTTP dan HTTPS berturut-turut adalah...", o: ["21 dan 22", "80 dan 443", "53 dan 80", "8080 dan 21", "25 dan 110"], a: 1, e: "HTTP menggunakan port 80 dan HTTPS menggunakan port 443." },
            { q: "Perangkat media transmisi yang memanfaatkan gelombang cahaya sebagai penghantar data adalah...", o: ["Kabel UTP", "Kabel Coaxial", "Fiber Optic", "Wireless", "Bluetooth"], a: 2, e: "Fiber Optic mentransmisikan data dalam bentuk pulsa cahaya melalui serat kaca." },
            { q: "Perintah CLI Mikrotik untuk melihat daftar IP Address yang terpasang adalah...", o: ["ip address print", "ip address add", "show ip interface", "ip config", "ifconfig"], a: 0, e: "Di RouterOS Mikrotik, perintah `ip address print` digunakan untuk menampilkan IP." },
            { q: "Model OSI terdiri dari berapa layer/lapisan?", o: ["4 Layer", "5 Layer", "6 Layer", "7 Layer", "8 Layer"], a: 3, e: "OSI Layer terdiri dari 7 lapisan (Physical, Data Link, Network, Transport, Session, Presentation, Application)." },
            { q: "Perangkat jangkauan jaringan yang menghubungkan komputer dalam satu LAN tanpa pemisahan collision domain dinamakan...", o: ["Switch Managed", "Hub", "Router", "Gateway", "Firewall"], a: 1, e: "Hub meneruskan sinyal ke semua port (broadcast) sehingga masih dalam 1 collision domain." },
            { q: "Berapa jumlah host yang dapat digunakan pada subnet mask /28?", o: ["2 Host", "6 Host", "14 Host", "30 Host", "62 Host"], a: 2, e: "Prefix /28 memiliki $2^4 = 16$ IP. Dikurangi Network & Broadcast = 14 host." },
            { q: "Topologi jaringan yang menggunakan satu kabel pusat (backbone) sebagai media transmisi dinamakan...", o: ["Topologi Star", "Topologi Bus", "Topologi Ring", "Topologi Mesh", "Topologi Tree"], a: 1, e: "Topologi Bus menggunakan kabel tunggal sebagai jalur utama." },
            { q: "Domain Name System (DNS) memiliki fungsi utama untuk...", o: ["Mengamankan lalu lintas jaringan", "Menerjemahkan nama domain menjadi IP Address", "Membagi bandwidth", "Mengirim e-mail", "Mengatur rute data"], a: 1, e: "DNS berfungsi mengarahkan nama domain (misal google.com) ke alamat IP." },
            { q: "Pada Mikrotik, fitur yang digunakan untuk membatasi atau mengontrol penggunaan bandwidth adalah...", o: ["Firewall NAT", "Queue", "Bridge", "DHCP Leases", "IP Route"], a: 1, e: "Fitur Queue (Simple Queue/Queue Tree) digunakan untuk melimitasi bandwidth." },
            { q: "Teknologi nirkabel Wi-Fi standar 802.11n bekerja pada frekuensi...", o: ["2.4 GHz dan 5 GHz", "900 MHz", "60 GHz", "10 GHz", "5 GHz saja"], a: 0, e: "Wi-Fi 4 (802.11n) mendukung frekuensi ganda 2.4 GHz dan 5 GHz." },
            { q: "Berikut ini yang merupakan IP Address versi 6 (IPv6) yang benar adalah...", o: ["192.168.1.1", "10.0.0.1", "2001:0db8:85a3:0000:0000:8a2e:0370:7334", "FE80::192.168.1.1", "255.255.255.255"], a: 2, e: "IPv6 terdiri dari 128 bit yang ditulis dalam format heksadesimal dipisahkan tanda titik dua (:)." },
            { q: "Perintah `ping` pada prompt utilitas jaringan digunakan untuk...", o: ["Mengecek konektivitas jaringan", "Melihat rute jaringan", "Menampilkan IP Address", "Membuka port", "Mengunduh file"], a: 0, e: "Ping (Packet Internet Groper) digunakan untuk menguji status konektivitas antar host." },
            { q: "Protokol keamanan nirkabel yang paling kuat saat ini adalah...", o: ["WEP", "WPA", "WPA2", "WPA3", "MAC Filtering"], a: 3, e: "WPA3 adalah standar enkripsi keamanan Wi-Fi paling modern dan aman." },
            { q: "Tools penyambung serat optik (Fiber Optic) secara permanen menggunakan peleburan kaca dinamakan...", o: ["Stripper", "Cleaver", "Fusion Splicer", "OTDR", "Optical Power Meter"], a: 2, e: "Fusion Splicer digunakan untuk menyambung inti serat optik menggunakan sinar las/panas." },
            { q: "Alat pengukur daya gelombang cahaya pada jaringan fiber optik adalah...", o: ["OTDR", "OPM (Optical Power Meter)", "Visual Fault Locator", "LAN Tester", "Multitester"], a: 1, e: "OPM digunakan untuk mengukur daya/redaman sinyal cahaya pada kabel FO." },
            { q: "VLAN (Virtual Local Area Network) bekerja pada OSI Layer berapa?", o: ["Layer 1 (Physical)", "Layer 2 (Data Link)", "Layer 3 (Network)", "Layer 4 (Transport)", "Layer 7 (Application)"], a: 1, e: "VLAN bekerja pada Switch Layer 2 (Data Link)." }
        ]
    };

    // State Aplikasi
    let studentData = { nama: '', absen: '', kelas: '' };
    let selectedMapelKey = '';
    let currentQuestions = [];

    // Elemen DOM
    const inputNama = document.getElementById('nama');
    const inputAbsen = document.getElementById('absen');
    const selectKelas = document.getElementById('kelas');
    const btnStart = document.getElementById('btn-start');

    const sectionIdentity = document.getElementById('section-identity');
    const sectionMapel = document.getElementById('section-mapel');
    const sectionQuiz = document.getElementById('section-quiz');
    const sectionResult = document.getElementById('section-result');

    // Validasi Form Identitas
    function checkFormValidity() {
        if (inputNama.value.trim() !== '' && inputAbsen.value.trim() !== '' && selectKelas.value !== '') {
            btnStart.disabled = false;
        } else {
            btnStart.disabled = true;
        }
    }

    inputNama.addEventListener('input', checkFormValidity);
    inputAbsen.addEventListener('input', checkFormValidity);
    selectKelas.addEventListener('change', checkFormValidity);

    // Tombol Mulai Kuis -> Pindah ke Pilih Mapel
    btnStart.addEventListener('click', () => {
        studentData.nama = inputNama.value.trim();
        studentData.absen = inputAbsen.value.trim();
        studentData.kelas = selectKelas.value;

        document.getElementById('user-display-name').innerText = studentData.nama;

        sectionIdentity.classList.add('hidden');
        sectionMapel.classList.remove('hidden');
    });

    // Memilih Mapel & Load Soal
    function selectMapel(key) {
        selectedMapelKey = key;
        currentQuestions = questionsData[key];

        let mapelName = "";
        if(key === 'indo') mapelName = "Bahasa Indonesia";
        if(key === 'sejarah') mapelName = "Sejarah";
        if(key === 'mtk') mapelName = "Matematika";
        if(key === 'tjkt') mapelName = "TJKT";

        document.getElementById('quiz-title').innerText = "Kuis " + mapelName + " - Kelas 11";

        renderQuestions();

        sectionMapel.classList.add('hidden');
        sectionQuiz.classList.remove('hidden');
        window.scrollTo(0, 0);
    }

    // Render Soal ke HTML
    function renderQuestions() {
        const container = document.getElementById('questions-container');
        container.innerHTML = '';

        currentQuestions.forEach((q, index) => {
            const card = document.createElement('div');
            card.className = 'question-card';

            let optionsHTML = '';
            const labels = ['A', 'B', 'C', 'D', 'E'];
            
            q.o.forEach((opt, optIndex) => {
                optionsHTML += `
                    <li class="option-item">
                        <label class="option-label">
                            <input type="radio" name="question_${index}" value="${optIndex}" required>
                            <span><strong>${labels[optIndex]}.</strong> ${opt}</span>
                        </label>
                    </li>
                `;
            });

            card.innerHTML = `
                <div class="question-text">${index + 1}. ${q.q}</div>
                <ul class="options-list">${optionsHTML}</ul>
            `;

            container.appendChild(card);
        });
    }

    // Submit Kuis & Hitung Nilai
    document.getElementById('quiz-form').addEventListener('submit', function(e) {
        e.preventDefault();

        let correctCount = 0;
        const reviewContainer = document.getElementById('review-container');
        reviewContainer.innerHTML = '';

        const labels = ['A', 'B', 'C', 'D', 'E'];

        currentQuestions.forEach((q, index) => {
            const selectedOption = document.querySelector(`input[name="question_${index}"]:checked`);
            const userAnswer = selectedOption ? parseInt(selectedOption.value) : -1;
            const isCorrect = (userAnswer === q.a);

            if (isCorrect) correctCount++;

            // Render Review
            const reviewCard = document.createElement('div');
            reviewCard.className = `review-card ${isCorrect ? 'correct' : 'wrong'}`;

            reviewCard.innerHTML = `
                <span class="status-badge ${isCorrect ? 'bg-correct' : 'bg-wrong'}">
                    ${isCorrect ? 'BENAR' : 'SALAH'}
                </span>
                <p><strong>Soal ${index + 1}:</strong> ${q.q}</p>
                <p style="margin-top:5px;">Jawaban Anda: <strong style="color: ${isCorrect ? 'var(--correct-color)' : 'var(--wrong-color)'}">
                    ${userAnswer !== -1 ? labels[userAnswer] + '. ' + q.o[userAnswer] : 'Tidak dijawab'}
                </strong></p>
                ${!isCorrect ? `<p>Kunci Jawaban: <strong style="color: var(--correct-color)">${labels[q.a]}.${q.o[q.a]}</strong></p>` : ''}
                <div class="explanation"><strong>Pembahasan:</strong> ${q.e}</div>
            `;

            reviewContainer.appendChild(reviewCard);
        });

        // Hitung Skor (Skala 0 - 100)
        const finalScore = (correctCount / currentQuestions.length) * 100;
        
        document.getElementById('final-score').innerText = finalScore;
        document.getElementById('score-summary').innerText = 
            `Siswa: ${studentData.nama} (${studentData.kelas} / Absen ${studentData.absen}) - Menjawab benar ${correctCount} dari ${currentQuestions.length} soal.`;

        sectionQuiz.classList.add('hidden');
        sectionResult.classList.remove('hidden');
        window.scrollTo(0, 0);
    });
</script>

</body>
</html>
