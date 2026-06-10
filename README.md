<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>PDB Orde Dua - Osilasi & Rangkaian Listrik | Kelompok 3</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
            background: #eef2f9;
            margin: 0;
            padding: 24px 16px;
        }
        .slide-container {
            max-width: 950px;
            margin: 0 auto;
            background: #ffffff;
            border-radius: 32px;
            padding: 28px 32px;
            box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.15);
            transition: all 0.2s ease;
            border: 1px solid rgba(59,130,246,0.2);
        }
        .content-block {
            margin: 16px 0;
            padding: 16px 22px;
            background: #f9fbfe;
            border-radius: 20px;
            border-left: 5px solid #3b82f6;
            font-size: 1rem;
            line-height: 1.65;
            color: #0f172a;
        }
        .content-block.math-block {
            background: #f0f6ff;
            border-left-color: #2563eb;
            font-family: 'Courier New', 'SF Mono', monospace;
            overflow-x: auto;
        }
        .interactive-area {
            background: #ffffff;
            border: 1px solid #e2e8f0;
            box-shadow: 0 4px 10px rgba(0,0,0,0.02);
        }
        button {
            padding: 10px 20px;
            border-radius: 40px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: 0.2s;
            font-size: 0.9rem;
        }
        .next-btn { background: #2563eb; color: white; box-shadow: 0 2px 6px rgba(37,99,235,0.3);}
        .next-btn:hover { background: #1d4ed8; transform: scale(1.02);}
        #prev-btn { background: #475569; color: white; }
        #prev-btn:hover { background: #334155; }
        .mcq-option, .tf-btn {
            background: #eef2ff;
            color: #1e293b;
            margin: 8px 8px 0 0;
            border-radius: 40px;
            padding: 8px 18px;
            font-weight: 500;
        }
        .mcq-option:hover, .tf-btn:hover { background: #cbdffc; }
        .mcq-option.selected { outline: 3px solid #2563eb; background: #dbeafe; }
        .mcq-option.correct, .tf-btn.correct { background: #bbf7d0 !important; outline: 2px solid #16a34a; color: #14532d;}
        .mcq-option.incorrect, .tf-btn.incorrect { background: #ffddd6 !important; outline: 2px solid #dc2626; }
        .feedback-msg { margin-top: 16px; padding: 12px; border-radius: 28px; font-weight: 500; }
        .feedback-msg.correct { background: #dcfce7; color: #166534; border-left: 5px solid #16a34a; }
        .feedback-msg.incorrect { background: #fee2e2; color: #991b1b; border-left: 5px solid #dc2626; }
        .answer-input {
            width: 100%;
            padding: 12px 16px;
            border-radius: 60px;
            border: 1px solid #cbd5e1;
            font-size: 1rem;
            margin: 12px 0;
            background: white;
        }
        .check-btn { background: #2563eb; color: white; border-radius: 40px; padding: 8px 24px; margin-top: 6px; }
        .slide-indicator {
            text-align: center;
            margin-top: 18px;
            font-weight: 500;
            color: #2c3e66;
        }
        h2, h3 { color: #0c4a6e; margin-top: 0; letter-spacing: -0.3px; }
        hr { margin: 16px 0; border-color: #e2e8f0; }
        .flex-buttons { display: flex; justify-content: center; gap: 18px; margin-top: 20px; flex-wrap: wrap; }
        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
            100% { transform: translateX(0); }
        }
        .animating { animation: fadeSlide 0.2s ease; }
        @keyframes fadeSlide { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: translateY(0); } }
        table { width: 100%; border-collapse: collapse; background: #f8fafc; border-radius: 18px; overflow: hidden; }
        th, td { padding: 10px 12px; border: 1px solid #cbd5e1; text-align: left; vertical-align: top;}
        th { background: #e6f0ff; }
    </style>
    <script>
        window.MathJax = {
            tex: { inlineMath: [['\\(', '\\)']], displayMath: [['\\[', '\\]']] },
            startup: { typeset: false }
        };
    </script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>
<body>
<div id="slide-content" class="slide-container"></div>
<div class="flex-buttons">
    <button id="prev-btn" style="background:#64748b;color:#fff;">← Sebelumnya</button>
    <button id="next-btn" class="next-btn">Selanjutnya →</button>
</div>
<p id="slide-indicator" class="slide-indicator">Slide 1/36</p>

<script>
    // ============================================================
    // SLIDE DEFINITIONS : MATERI OSILASI PEGAS & RANGKAIAN LISTRIK
    // Berdasarkan file PPT_KELOMPOK 3 (PDB Orde Dua)
    // ============================================================
    const slides = [
        // COVER
        { id:'s1', type:'content', blocks:[
            { html:`<h2 style="text-align:center;color:#0c4a6e;">📌 APLIKASI PERSAMAAN DIFERENSIAL ORDE DUA</h2><h3 style="text-align:center;color:#2563eb;">Osilasi Massa Pegas & Rangkaian Listrik</h3><p style="text-align:center;">Kelompok 3 : Try Novian, Rika Dwi, Fiona Ambar, Naisyla Risma, Soni Risky, Rian Adam, Bintang Afra, Rahma Aprilesa</p><p style="text-align:center;">Buku Ajar PDB | Semester Genap</p>`, cls:''}
        ]},
        // Capaian & hukum dasar
        { id:'s2', type:'content', blocks:[
            { html:`<h3>🎯 Capaian Pembelajaran</h3><ul><li>Menerapkan PDB orde dua pada osilasi bebas tak teredam & teredam</li><li>Menganalisis rangkaian RLC seri</li><li>Menentukan solusi eksak dengan syarat awal</li></ul>`, cls:''},
            { html:`<h4>⚖️ Hukum Newton & Hooke</h4><p>\\[ \\sum F = m \\cdot a = m y'' \\quad \\text{(Newton)} \\]</p><p>Gaya pegas: \\( F_{\\text{pegas}} = -k y \\) (Hooke)</p>`, cls:'math-block'}
        ]},
        // Hukum Kirchhoff
        { id:'s3', type:'content', blocks:[
            { html:`<h3>🔌 Hukum Kirchhoff Tegangan</h3><p>\\[ \\sum V = 0 \\quad \\text{atau} \\quad RI + L\\frac{dI}{dt} + \\frac{1}{C}\\int I\\,dt = E(t) \\]</p><p>Hubungan: \\( I = \\frac{dQ}{dt} \\), tegangan kapasitor \\( \\frac{Q}{C} \\)</p>`, cls:'math-block'},
            { html:`<p><strong>Komponen:</strong> Resistor (R), Induktor (L), Kapasitor (C)</p>`, cls:''}
        ]},
        // Osilasi Bebas Tak Teredam - konsep & PD
        { id:'s4', type:'content', blocks:[
            { html:`<h3>⚙️ Osilasi Bebas Tak Teredam</h3><p>Sistem massa-pegas tanpa redaman, energi kekal. Hukum Newton: \\( -ky = my'' \\)</p>`, cls:''},
            { html:`\\[ my'' + ky = 0 \\quad\\Rightarrow\\quad y'' + \\frac{k}{m}y = 0 \\]`, cls:'math-block'},
            { html:`<p>Persamaan karakteristik: \\( \\lambda^2 + \\frac{k}{m}=0 \\), akar imajiner \\( \\lambda = \\pm i\\omega_0 \\) dengan \\( \\omega_0 = \\sqrt{k/m} \\)</p>`, cls:''}
        ]},
        // Solusi umum tak teredam
        { id:'s5', type:'content', blocks:[
            { html:`<h4>📐 Solusi Gerak Harmonik Sederhana</h4>`, cls:''},
            { html:`\\[ y(t) = A \\cos(\\omega_0 t) + B \\sin(\\omega_0 t) \\]`, cls:'math-block'},
            { html:`Atau \\( y(t) = R \\cos(\\omega_0 t - \\phi) \\) dengan amplitudo \\( R = \\sqrt{A^2+B^2} \\), frekuensi sudut \\( \\omega_0 \\), periode \\( T = 2\\pi/\\omega_0 \\).`, cls:''}
        ]},
        // Contoh soal bola besi (tak teredam) -> slide penyelesaian bertahap
        { id:'s6', type:'content', blocks:[
            { html:`<h4>📝 Contoh 1: Bola Besi (Tak Teredam)</h4><p>Berat <strong>70 N</strong> meregangkan pegas 5 cm. Ditarik ke bawah 10 cm lalu dilepas (v₀=0). Tentukan persamaan gerak dan frekuensi.</p>`, cls:''}
        ]},
        { id:'s7', type:'content', blocks:[
            { html:`<strong>Langkah 1:</strong> Hitung konstanta pegas \\( k = \\frac{W}{\\Delta s} = \\frac{70}{0,05} = 1400 \\, N/m \\)`, cls:''},
            { html:`<strong>Massa:</strong> \\( m = W/g = 70/9,8 \\approx 7,14 \\, kg \\)`, cls:''},
            { html:`\\[ \\omega_0 = \\sqrt{\\frac{k}{m}} = \\sqrt{\\frac{1400}{7,14}} = 14 \\, rad/s \\]`, cls:'math-block'}
        ]},
        { id:'s8', type:'content', blocks:[
            { html:`Persamaan gerak: \\( y'' + 196 y = 0 \\) → solusi umum \\( y(t)=A\\cos 14t + B\\sin 14t \\)`, cls:''},
            { html:`Syarat awal: \\( y(0)=0,1 \\), \\( y'(0)=0 \\) → \\( A=0,1,\\; B=0 \\)`, cls:''},
            { html:`\\[ y(t) = 0,1 \\cos(14t) \\] Frekuensi: \\( f = \\frac{14}{2\\pi} \\approx 2,23 \\, Hz \\), periode \\( T \\approx 0,448 \\, s \\)`, cls:'math-block'}
        ]},
        // Osilasi Bebas Teredam ( konsep + PD )
        { id:'s9', type:'content', blocks:[
            { html:`<h3>🛡️ Osilasi Bebas Teredam</h3><p>Gaya pegas \\(-ky\\) dan gaya redaman \\( -c y' \\). Hukum Newton: \\( my'' = -ky - c y' \\)</p>`, cls:''},
            { html:`\\[ my'' + c y' + ky = 0 \\quad\\Rightarrow\\quad y'' + \\frac{c}{m}y' + \\frac{k}{m}y = 0 \\]`, cls:'math-block'},
            { html:`Persamaan karakteristik: \\( \\lambda^2 + \\frac{c}{m}\\lambda + \\frac{k}{m}=0 \\) dengan diskriminan \\( D = \\left(\\frac{c}{m}\\right)^2 - 4\\frac{k}{m} \\).`, cls:''}
        ]},
        // Tiga kasus redaman
        { id:'s10', type:'content', blocks:[
            { html:`<h4>📊 Tiga Kasus Redaman</h4>`, cls:''},
            { html:`<table><tr><th>Kasus</th><th>Syarat</th><th>Solusi</th></tr>
            <tr><td>Overdamped</td><td>\\( c^2 > 4mk \\)</td><td>\\( y = C_1 e^{\\lambda_1 t} + C_2 e^{\\lambda_2 t} \\)</td></tr>
            <tr><td>Critically damped</td><td>\\( c^2 = 4mk \\)</td><td>\\( y = (C_1 + C_2 t)e^{\\lambda t} \\)</td></tr>
            <tr><td>Underdamped</td><td>\\( c^2 < 4mk \\)</td><td>\\( y = e^{\\alpha t}(C_1\\cos\\beta t + C_2\\sin\\beta t) \\)</td></tr></table>`, cls:'math-block'}
        ]},
        // Contoh soal teredam kritis (bola besi c=200)
        { id:'s11', type:'content', blocks:[
            { html:`<h4>📘 Contoh 2: Redaman Kritis</h4><p>Bola besi (W=70N, k=1400 N/m, m≈7,14 kg) dengan redaman c = 200 kg/s. Ditarik 10 cm lalu dilepas. Tentukan y(t).</p>`, cls:''}
        ]},
        { id:'s12', type:'content', blocks:[
            { html:`PD: \\( y'' + \\frac{c}{m}y' + \\frac{k}{m}y =0 \\) → \\( y'' + 28y' + 196y =0 \\)`, cls:'math-block'},
            { html:`Karakteristik: \\( \\lambda^2 + 28\\lambda + 196 = 0 \\) → \\( (\\lambda+14)^2=0 \\), akar kembar \\( \\lambda = -14 \\).`, cls:'math-block'},
            { html:`Solusi umum: \\( y(t) = (C_1 + C_2 t)e^{-14t} \\)`, cls:''}
        ]},
        { id:'s13', type:'content', blocks:[
            { html:`Syarat awal: \\( y(0)=0,1 \\Rightarrow C_1=0,1 \\) ; \\( y'(0)=0 \\) → \\( C_2 -14C_1 =0 \\Rightarrow C_2 = 1,4 \\)`, cls:''},
            { html:`\\[ y(t) = (0,1 + 1,4 t) e^{-14t} \\] Sistem kembali ke setimbang tanpa osilasi (redaman kritis).`, cls:'math-block'}
        ]},
        // Rangkaian RLC Seri
        { id:'s14', type:'content', blocks:[
            { html:`<h3>🔋 Rangkaian RLC Seri (tanpa sumber / sumber nol)</h3><p>Hukum Kirchhoff: \\( L\\frac{dI}{dt} + RI + \\frac{1}{C}Q = 0 \\). Turunkan terhadap t:</p>`, cls:''},
            { html:`\\[ L I'' + R I' + \\frac{1}{C} I = 0 \\quad\\Rightarrow\\quad I'' + \\frac{R}{L} I' + \\frac{1}{LC} I = 0 \\]`, cls:'math-block'},
            { html:`Persamaan analog dengan sistem mekanik: \\( m \\to L,\\; c \\to R,\\; k \\to 1/C \\).`, cls:''}
        ]},
        // Contoh RLC (R=100, L=0.1, C=1mF, I(0)=3mA, I'(0)=0)
        { id:'s15', type:'content', blocks:[
            { html:`<h4>📟 Contoh 3: Rangkaian RLC Seri</h4><p>R=100 Ω, L=0,1 H, C=1 mF, hubung singkat. I(0)=0,003 A, I'(0)=0. Tentukan I(t).</p>`, cls:''}
        ]},
        { id:'s16', type:'content', blocks:[
            { html:`PD: \\( I'' + \\frac{R}{L} I' + \\frac{1}{LC} I = 0 \\) → \\( \\frac{R}{L}=1000,\\; \\frac{1}{LC}=10^4 \\)`, cls:''},
            { html:`\\[ I'' + 1000 I' + 10000 I = 0 \\] Persamaan karakteristik: \\( \\lambda^2 + 1000\\lambda + 10000=0 \\)`, cls:'math-block'}
        ]},
        { id:'s17', type:'content', blocks:[
            { html:`Diskriminan: \\( 1000^2 - 4\\cdot10000 = 960000 \\) → \\( \\sqrt{960000}=400\\sqrt{6} \\approx 979,8 \\)`, cls:''},
            { html:`\\[ \\lambda_{1,2} = \\frac{-1000 \\pm 979,8}{2} \\approx -10,1 \\;\\; \\text{dan} \\;\\; -989,9 \\]`, cls:'math-block'},
            { html:`Solusi umum: \\( I(t) = C_1 e^{-10t} + C_2 e^{-990t} \\) (pembulatan untuk kemudahan)`, cls:''}
        ]},
        { id:'s18', type:'content', blocks:[
            { html:`Syarat awal: \\( I(0)=0,003 = C_1 + C_2 \\), \\( I'(0)= -10C_1 -990C_2 =0 \\)`, cls:''},
            { html:`Eliminasi: \\( C_1 \\approx 0,003031,\\; C_2 \\approx -3,09\\times10^{-5} \\)`, cls:''},
            { html:`\\[ I(t) = 0,00303 e^{-10t} - 3,09\\times10^{-5} e^{-990t} \\] (Arus didominasi suku pertama setelah beberapa saat)`, cls:'math-block'}
        ]},
        // Ringkasan solusi analogi
        { id:'s19', type:'content', blocks:[
            { html:`<h4>📌 Tabel Analogi Mekanik - Listrik</h4>`, cls:''},
            { html:`<table><tr><th>Sistem Mekanik</th><th>Rangkaian RLC</th></tr>
            <tr><td>Massa (m)</td><td>Induktansi (L)</td></tr>
            <tr><td>Redaman (c)</td><td>Resistansi (R)</td></tr>
            <tr><td>Konstanta pegas (k)</td><td>1/Kapasitansi (1/C)</td></tr>
            <tr><td>Simpangan y(t)</td><td>Arus I(t)</td></tr></table>`, cls:''}
        ]},
        // Latihan soal interaktif: soal pilihan ganda (konsep)
        { id:'s20', type:'mcq', question:'Osilasi bebas tak teredam pada sistem massa-pegas memiliki bentuk solusi ....', options:[
            { id:'A', text:'y(t) = C₁ e^{λ₁ t} + C₂ e^{λ₂ t} dengan λ₁,λ₂ real berbeda' },
            { id:'B', text:'y(t) = (C₁ + C₂ t) e^{αt}' },
            { id:'C', text:'y(t) = A cos(ω₀ t) + B sin(ω₀ t)' },
            { id:'D', text:'y(t) = A e^{-kt}' }
        ], correct:'C', fc:'✅ Benar! Solusi tak teredam adalah gerak harmonik sederhana dengan ω₀ = √(k/m).', fi:'❌ Kurang tepat. Osilasi bebas tak teredam menghasilkan fungsi sinus/cosinus (SHM).' },
        // True/False redaman kritis
        { id:'s21', type:'tf', statement:'"Pada redaman kritis (c²=4mk), sistem kembali ke posisi setimbang paling cepat tanpa berosilasi."', correct:true, 
          fc:'✅ Benar! Redaman kritis memberikan waktu balik tercepat tanpa osilasi.', fi:'❌ Salah. Redaman kritis justru menghasilkan sistem tanpa getaran dan kembali paling cepat.' },
        // Soal isian : konstanta redaman
        { id:'s22', type:'short', question:'Pada sistem pegas dengan redaman, persamaan karakteristik λ² + (c/m)λ + k/m = 0. Jika c² > 4mk, sistem disebut ______ (overdamped / underdamped / critically damped).', answers:['overdamped','over damped','overdamped system'], 
          fc:'✅ Benar! c² > 4mk → overdamped (dua akar real negatif berbeda).', fi:'Jawaban: overdamped.' },
        // Soal input angka: hitung frekuensi alami (ω₀) dari contoh k=1400, m≈7.14
        { id:'s23', type:'numberinput', question:'Dari contoh bola besi (k=1400 N/m, m=7,14 kg), hitung ω₀ (rad/s) dalam 2 desimal (gunakan rumus √(k/m)).', correctAnswer:'14.00', 
          fc:'✅ Tepat! ω₀ = √(1400/7,14) = √196 ≈ 14 rad/s.', fi:'❌ Ulangi: ω₀ = √(k/m) = √(1400/7,14) = 14 rad/s. Masukkan 14 atau 14.00.' },
        // Soal pilihan ganda RLC
        { id:'s24', type:'mcq', question:'Persamaan diferensial arus pada rangkaian RLC seri tanpa sumber adalah:', options:[
            { id:'A', text:'I\'\' + (R/L)I\' + (1/LC)I = 0' },
            { id:'B', text:'I\'\' + (L/R)I\' + (C/L)I = 0' },
            { id:'C', text:'I\'\' - (R/L)I\' + (LC)I = 0' },
            { id:'D', text:'I\' + RI + L/C = 0' }
        ], correct:'A', fc:'✅ Benar! Berdasarkan hukum Kirchhoff, turunan menghasilkan I\'\' + (R/L)I\' + (1/LC)I = 0.', fi:'❌ Ingat: L I\'\' + R I\' + (1/C)I = 0 → bagi L.' },
        // Soal hitung konstanta pegas dari soal lain (latihan nomor 1)
        { id:'s25', type:'numberinput', question:'Latihan: Benda berat 50 N meregangkan pegas 6 cm. Hitung konstanta pegas k (N/m).', correctAnswer:'833.33', 
          fc:'✅ Bagus! k = W/Δs = 50 / 0,06 ≈ 833,33 N/m.', fi:'❌ Gunakan k = berat / regangan (dalam meter): 50/0,06 = 833,33.' },
        // Redaman kurang / underdamped
        { id:'s26', type:'mcq', question:'Jika c² < 4mk pada sistem massa-pegas, solusi umum berbentuk:', options:[
            { id:'A', text:'y = e^{αt}(C₁ cosβt + C₂ sinβt)' },
            { id:'B', text:'y = C₁ e^{λ₁ t} + C₂ e^{λ₂ t}' },
            { id:'C', text:'y = (C₁ + C₂ t)e^{λt}' },
            { id:'D', text:'y = A cos(ω₀ t)' }
        ], correct:'A', fc:'✅ Benar! Underdamped menghasilkan osilasi teredam dengan amplitudo eksponensial.', fi:'❌ Kondisi c²<4mk → akar kompleks → solusi teredam kurang (A).' },
        // Interpretasi RLC contoh
        { id:'s27', type:'content', blocks:[
            { html:`<h4>📈 Interpretasi Hasil RLC</h4><p>Pada contoh RLC dengan R=100Ω, L=0.1H, C=1mF, diperoleh arus I(t) = 0,00303 e^{-10t} - 3,09e-5 e^{-990t}. Suku kedua meluruh sangat cepat sehingga arus didominasi oleh eksponensial lambat ≈ e^{-10t}. Sistem overdamped.</p>`, cls:'math-block'}
        ]},
        // Ringkasan akhir & penutup
        { id:'s28', type:'content', blocks:[
            { html:`<h3 style="color:#1e3a5f;">📌 Langkah Umum Menyelesaikan Aplikasi PDB Orde 2</h3><ol><li>Identifikasi sistem (pegas/redaman/rangkaian)</li><li>Tulis hukum fisika (Newton/Hooke/Kirchhoff)</li><li>Bentuk PD homogen orde 2</li><li>Tentukan koefisien & persamaan karakteristik</li><li>Cari akar → tentukan kasus redaman</li><li>Tulis solusi umum → aplikasi syarat awal</li><li>Interpretasi fisis</li></ol>`, cls:''}
        ]},
        { id:'s29', type:'content', blocks:[
            { html:`<h2 style="text-align:center;">✨ Terima Kasih</h2><p style="text-align:center;">Kelompok 3 - Aplikasi Persamaan Diferensial Orde Dua<br>Osilasi Massa Pegas & Rangkaian Listrik</p><p style="text-align:center;">Referensi: Boyce & DiPrima, Kreyszig, Dafik</p>`, cls:''}
        ]}
    ];

    // -------------------- LOGIKA SLIDE -------------------------
    let currentSlide = 0;
    let revealedBlocks = 0;
    let interactiveAnswered = false;

    const slideContainer = document.getElementById('slide-content');
    const indicator = document.getElementById('slide-indicator');
    const nextBtn = document.getElementById('next-btn');
    const prevBtn = document.getElementById('prev-btn');

    function updateIndicator() { indicator.textContent = `Slide ${currentSlide+1}/${slides.length}`; }
    function typesetMath() { if(window.MathJax) MathJax.typesetPromise?.([slideContainer]).catch(e=>console.log(e)); }

    function resetState() { revealedBlocks = 1; interactiveAnswered = false; }

    function renderContentBlocks(slide) {
        slideContainer.innerHTML = '';
        for(let i=0; i<revealedBlocks && i<slide.blocks.length; i++) {
            const div = document.createElement('div');
            div.className = 'content-block ' + (slide.blocks[i].cls || '');
            div.innerHTML = slide.blocks[i].html;
            slideContainer.appendChild(div);
        }
        if(revealedBlocks >= slide.blocks.length) interactiveAnswered = true;
    }

    function revealNextContent() {
        const slide = slides[currentSlide];
        if(slide.type !== 'content' || revealedBlocks >= slide.blocks.length) return false;
        revealedBlocks++;
        renderContentBlocks(slide);
        typesetMath();
        if(revealedBlocks >= slide.blocks.length) interactiveAnswered = true;
        return true;
    }

    // Render MCQ
    function renderMCQ(slide) {
        slideContainer.innerHTML = '';
        const wrapper = document.createElement('div');
        wrapper.className = 'content-block interactive-area';
        wrapper.innerHTML = `<p><strong>📝 Pilihan Ganda</strong></p><p>${slide.question}</p><div>${slide.options.map(o=>`<button class="mcq-option" data-opt="${o.id}">${o.id}. ${o.text}</button>`).join('')}</div><div class="feedback-msg" style="display:none;"></div>`;
        slideContainer.appendChild(wrapper);
        const opts = wrapper.querySelectorAll('.mcq-option');
        const fb = wrapper.querySelector('.feedback-msg');
        opts.forEach(btn => {
            btn.addEventListener('click', (e) => {
                if(interactiveAnswered) return;
                interactiveAnswered = true;
                const chosen = btn.dataset.opt;
                if(chosen === slide.correct) {
                    btn.classList.add('correct');
                    fb.innerHTML = slide.fc;
                    fb.className = 'feedback-msg correct';
                } else {
                    btn.classList.add('incorrect');
                    fb.innerHTML = slide.fi;
                    fb.className = 'feedback-msg incorrect';
                    opts.forEach(b => { if(b.dataset.opt === slide.correct) b.classList.add('correct'); });
                }
                fb.style.display = 'block';
            });
        });
    }

    function renderTF(slide) {
        slideContainer.innerHTML = '';
        const div = document.createElement('div');
        div.className = 'content-block interactive-area';
        div.innerHTML = `<p><strong>✅/❌ True or False</strong></p><p>${slide.statement}</p><div>${['✅ True','❌ False'].map((txt,idx)=>`<button class="tf-btn" data-val="${idx===0}">${txt}</button>`).join('')}</div><div class="feedback-msg" style="display:none;"></div>`;
        slideContainer.appendChild(div);
        const btns = div.querySelectorAll('.tf-btn');
        const fb = div.querySelector('.feedback-msg');
        btns.forEach(btn => {
            btn.addEventListener('click', () => {
                if(interactiveAnswered) return;
                interactiveAnswered = true;
                const val = btn.dataset.val === 'true';
                if(val === slide.correct) {
                    btn.classList.add('correct');
                    fb.innerHTML = slide.fc;
                    fb.className = 'feedback-msg correct';
                } else {
                    btn.classList.add('incorrect');
                    btns.forEach(b => { if((b.dataset.val === 'true') === slide.correct) b.classList.add('correct'); });
                    fb.innerHTML = slide.fi;
                    fb.className = 'feedback-msg incorrect';
                }
                fb.style.display = 'block';
            });
        });
    }

    function renderShort(slide) {
        slideContainer.innerHTML = '';
        const div = document.createElement('div');
        div.className = 'content-block interactive-area';
        div.innerHTML = `<p><strong>✍️ Isian Singkat</strong></p><p>${slide.question}</p><input class="answer-input" placeholder="Jawaban Anda"><button class="check-btn">Periksa</button><div class="feedback-msg" style="display:none;"></div>`;
        slideContainer.appendChild(div);
        const inp = div.querySelector('.answer-input');
        const btn = div.querySelector('.check-btn');
        const fb = div.querySelector('.feedback-msg');
        const check = () => {
            if(interactiveAnswered) return;
            const ans = inp.value.trim().toLowerCase().replace(/\s+/g,'');
            const ok = slide.answers.some(a => a.toLowerCase().replace(/\s+/g,'') === ans);
            interactiveAnswered = true;
            inp.classList.add(ok ? 'correct' : 'incorrect');
            fb.innerHTML = ok ? slide.fc : slide.fi;
            fb.className = `feedback-msg ${ok ? 'correct' : 'incorrect'}`;
            fb.style.display = 'block';
            btn.disabled = true; inp.disabled = true;
        };
        btn.addEventListener('click', check);
        inp.addEventListener('keypress', e => { if(e.key === 'Enter') check(); });
    }

    function renderNumberInput(slide) {
        slideContainer.innerHTML = '';
        const div = document.createElement('div');
        div.className = 'content-block interactive-area';
        div.innerHTML = `<p><strong>🔢 Input Angka</strong></p><p>${slide.question}</p><input type="text" class="answer-input" placeholder="ex: 14.00"><button class="check-btn">Periksa</button><div class="feedback-msg" style="display:none;"></div>`;
        slideContainer.appendChild(div);
        const inp = div.querySelector('.answer-input');
        const btn = div.querySelector('.check-btn');
        const fb = div.querySelector('.feedback-msg');
        const check = () => {
            if(interactiveAnswered) return;
            const val = inp.value.trim();
            const ok = Math.abs(parseFloat(val) - parseFloat(slide.correctAnswer)) < 0.01;
            interactiveAnswered = true;
            inp.classList.add(ok ? 'correct' : 'incorrect');
            fb.innerHTML = ok ? slide.fc : slide.fi;
            fb.className = `feedback-msg ${ok ? 'correct' : 'incorrect'}`;
            fb.style.display = 'block';
            btn.disabled = true; inp.disabled = true;
        };
        btn.addEventListener('click', check);
        inp.addEventListener('keypress', e => { if(e.key === 'Enter') check(); });
    }

    async function renderSlide(index) {
        const slide = slides[index];
        resetState();
        slideContainer.classList.add('animating');
        await new Promise(r => setTimeout(r, 80));
        if(slide.type === 'content') renderContentBlocks(slide);
        else if(slide.type === 'mcq') renderMCQ(slide);
        else if(slide.type === 'tf') renderTF(slide);
        else if(slide.type === 'short') renderShort(slide);
        else if(slide.type === 'numberinput') renderNumberInput(slide);
        else slideContainer.innerHTML = '<p>Error</p>';
        slideContainer.classList.remove('animating');
        typesetMath();
        updateIndicator();
    }

    function nextSlide() {
        const slide = slides[currentSlide];
        if(slide.type === 'content' && revealedBlocks < slide.blocks.length) {
            revealNextContent();
            return;
        }
        if(!interactiveAnswered && slide.type !== 'content') {
            const ia = slideContainer.querySelector('.interactive-area');
            if(ia) ia.style.animation = 'shake 0.4s ease';
            setTimeout(() => { if(ia) ia.style.animation = ''; }, 400);
            return;
        }
        if(currentSlide < slides.length-1) { currentSlide++; renderSlide(currentSlide); }
    }

    function prevSlide() { if(currentSlide > 0) { currentSlide--; renderSlide(currentSlide); } }

    document.addEventListener('keydown', (e) => {
        if(e.key === 'ArrowRight') { e.preventDefault(); nextSlide(); }
        if(e.key === 'ArrowLeft') { e.preventDefault(); prevSlide(); }
    });
    nextBtn.onclick = nextSlide;
    prevBtn.onclick = prevSlide;
    renderSlide(0);
</script>
</body>
</html>
