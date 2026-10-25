<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Auto Llaker & Limar Rigoni - System</title>
    <!-- FontAwesome & Google Fonts -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800;900&family=Rajdhani:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-dark: #0a0d14;
            --bg-card: #121824;
            --bg-card-hover: #1a2233;
            --accent-blue: #00d2ff;
            --accent-cyan: #00f2fe;
            --accent-green: #00e676;
            --accent-orange: #ff9100;
            --accent-red: #ff3d00;
            --text-main: #f0f4f8;
            --text-muted: #8a99ad;
            --border-color: #1e293b;
            --glow: 0 0 20px rgba(0, 210, 255, 0.35);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Rajdhani', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            min-height: 100vh;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 15% 15%, rgba(0, 210, 255, 0.05) 0%, transparent 40%),
                radial-gradient(circle at 85% 85%, rgba(0, 242, 254, 0.05) 0%, transparent 40%);
        }

        h1, h2, h3, h4, .brand-font {
            font-family: 'Orbitron', sans-serif;
            letter-spacing: 1px;
        }

        /* --- LOGIN SCREEN --- */
        #login-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: linear-gradient(135deg, rgba(10,13,20,0.95), rgba(18,24,36,0.98)), 
                        url('https://images.unsplash.com/photo-1617814076367-b759c7d7e738?auto=format&fit=crop&w=1920&q=80') center/cover no-repeat;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            backdrop-filter: blur(8px);
        }

        .login-card {
            background: rgba(18, 24, 36, 0.9);
            border: 1px solid var(--accent-blue);
            box-shadow: var(--glow);
            border-radius: 20px;
            padding: 40px;
            width: 100%;
            max-width: 440px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .login-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--accent-cyan), transparent);
            animation: scan 3s infinite;
        }

        @keyframes scan {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        .login-logo {
            font-size: 2.5rem;
            color: var(--accent-cyan);
            margin-bottom: 10px;
            text-shadow: 0 0 10px rgba(0, 242, 254, 0.5);
        }

        .login-card h2 {
            font-size: 1.5rem;
            margin-bottom: 5px;
            color: #fff;
        }

        .login-card p {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 30px;
        }

        .input-group {
            margin-bottom: 20px;
            text-align: left;
            position: relative;
        }

        .input-group label {
            display: block;
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 6px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .input-group input, .form-control {
            width: 100%;
            padding: 12px 16px;
            background: rgba(10, 13, 20, 0.8);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            color: #fff;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .input-group input:focus, .form-control:focus {
            outline: none;
            border-color: var(--accent-blue);
            box-shadow: 0 0 10px rgba(0, 210, 255, 0.2);
        }

        .btn-primary {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, var(--accent-blue), #0072ff);
            border: none;
            border-radius: 8px;
            color: #fff;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 210, 255, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 210, 255, 0.5);
        }

        .error-msg {
            color: var(--accent-red);
            font-size: 0.85rem;
            margin-top: 10px;
            display: none;
        }

        /* --- DASHBOARD LAYOUT --- */
        #app-dashboard {
            display: none;
            min-height: 100vh;
            flex-direction: column;
        }

        header {
            background: rgba(18, 24, 36, 0.95);
            border-bottom: 1px solid var(--border-color);
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            backdrop-filter: blur(10px);
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .brand i {
            font-size: 2rem;
            color: var(--accent-cyan);
        }

        .brand-title {
            font-size: 1.3rem;
            font-weight: 800;
            background: linear-gradient(90deg, #fff, var(--text-muted));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .brand-subtitle {
            font-size: 0.75rem;
            color: var(--accent-blue);
            letter-spacing: 2px;
        }

        .user-nav {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .stats-trigger-btn {
            background: rgba(0, 210, 255, 0.1);
            border: 1px solid var(--accent-blue);
            color: var(--accent-cyan);
            padding: 8px 16px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s ease;
        }

        .stats-trigger-btn:hover {
            background: var(--accent-blue);
            color: #000;
            box-shadow: var(--glow);
        }

        .btn-logout {
            background: transparent;
            border: 1px solid var(--border-color);
            color: var(--text-muted);
            padding: 8px 12px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-logout:hover {
            border-color: var(--accent-red);
            color: var(--accent-red);
        }

        main {
            padding: 30px;
            max-width: 1600px;
            margin: 0 auto;
            width: 100%;
            flex: 1;
        }

        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            gap: 20px;
            flex-wrap: wrap;
        }

        .search-filter {
            display: flex;
            gap: 15px;
            flex: 1;
            max-width: 600px;
        }

        .filter-btn-group {
            display: flex;
            background: var(--bg-card);
            padding: 4px;
            border-radius: 10px;
            border: 1px solid var(--border-color);
        }

        .filter-btn {
            padding: 8px 16px;
            background: transparent;
            border: none;
            color: var(--text-muted);
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .filter-btn.active {
            background: var(--accent-blue);
            color: #000;
        }

        .btn-add-car {
            background: linear-gradient(135deg, var(--accent-cyan), #00a8ff);
            color: #000;
            font-weight: 700;
            padding: 12px 24px;
            border-radius: 10px;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 4px 15px rgba(0, 242, 254, 0.3);
            transition: all 0.3s;
        }

        .btn-add-car:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 242, 254, 0.5);
        }

        /* --- CAR GRID --- */
        .car-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
            gap: 25px;
        }

        .car-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 20px;
            transition: all 0.3s ease;
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .car-card:hover {
            border-color: rgba(0, 210, 255, 0.4);
            transform: translateY(-4px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
        }

        .car-status-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
        }

        .status-working {
            background: rgba(255, 145, 0, 0.15);
            color: var(--accent-orange);
            border: 1px solid var(--accent-orange);
        }

        .status-completed {
            background: rgba(0, 230, 118, 0.15);
            color: var(--accent-green);
            border: 1px solid var(--accent-green);
        }

        .car-header {
            margin-bottom: 15px;
            padding-right: 80px;
        }

        .car-title {
            font-size: 1.3rem;
            color: #fff;
            margin-bottom: 4px;
        }

        .car-owner {
            color: var(--text-muted);
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .car-details-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            background: rgba(10, 13, 20, 0.5);
            padding: 12px;
            border-radius: 10px;
            margin-bottom: 15px;
            font-size: 0.85rem;
        }

        .detail-item span {
            display: block;
            color: var(--text-muted);
            font-size: 0.75rem;
        }

        .detail-item strong {
            color: var(--text-main);
        }

        .car-actions {
            display: flex;
            gap: 8px;
            margin-top: 15px;
        }

        .btn-card-action {
            flex: 1;
            padding: 10px;
            border: 1px solid var(--border-color);
            background: rgba(255,255,255,0.03);
            color: #fff;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            transition: all 0.2s;
        }

        .btn-card-action:hover {
            background: rgba(0, 210, 255, 0.1);
            border-color: var(--accent-blue);
            color: var(--accent-cyan);
        }

        .btn-card-delete {
            width: 38px;
            flex: none;
            background: rgba(255, 61, 0, 0.1);
            border-color: rgba(255, 61, 0, 0.3);
            color: var(--accent-red);
        }

        .btn-card-delete:hover {
            background: var(--accent-red);
            color: #fff;
        }

        /* --- MODAL SYSTEM --- */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(10, 13, 20, 0.85);
            backdrop-filter: blur(8px);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 20px;
            overflow-y: auto;
        }

        .modal-content {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            width: 100%;
            max-width: 900px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8);
        }

        .modal-header {
            padding: 20px 25px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            background: var(--bg-card);
            z-index: 10;
        }

        .modal-close {
            background: transparent;
            border: none;
            color: var(--text-muted);
            font-size: 1.5rem;
            cursor: pointer;
        }

        .modal-close:hover { color: #fff; }

        .modal-body { padding: 25px; }

        /* --- 360 CAR INSPECTOR --- */
        .car-inspector-container {
            display: grid;
            grid-template-columns: 1fr 300px;
            gap: 20px;
        }

        @media (max-width: 900px) {
            .car-inspector-container { grid-template-columns: 1fr; }
        }

        .car-view-box {
            background: #07090e;
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 350px;
            position: relative;
        }

        .view-controls {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }

        .view-btn {
            background: rgba(255,255,255,0.05);
            border: 1px solid var(--border-color);
            color: var(--text-muted);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.8rem;
            cursor: pointer;
            transition: all 0.3s;
        }

        .view-btn.active {
            background: var(--accent-blue);
            color: #000;
            font-weight: 700;
        }

        .car-svg-wrapper {
            width: 100%;
            max-width: 450px;
            height: 260px;
        }

        .car-part {
            fill: #1e293b;
            stroke: var(--accent-blue);
            stroke-width: 1.5;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .car-part:hover {
            fill: rgba(0, 210, 255, 0.3);
        }

        .car-part.selected {
            fill: var(--accent-cyan);
            filter: drop-shadow(0 0 8px var(--accent-cyan));
        }

        .parts-checklist {
            background: rgba(10, 13, 20, 0.5);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 15px;
            max-height: 350px;
            overflow-y: auto;
        }

        .parts-checklist h4 {
            margin-bottom: 10px;
            font-size: 0.9rem;
            color: var(--accent-blue);
        }

        .part-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 8px;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            font-size: 0.9rem;
        }

        .part-item input[type="checkbox"] {
            width: 18px;
            height: 18px;
            accent-color: var(--accent-cyan);
            cursor: pointer;
        }

        /* --- STATS / ANALYTICS MODAL --- */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 25px;
        }

        .stat-card {
            background: rgba(10, 13, 20, 0.6);
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: 12px;
            text-align: center;
        }

        .stat-card h3 {
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 8px;
            text-transform: uppercase;
        }

        .stat-card .value {
            font-size: 1.8rem;
            font-weight: 800;
            color: var(--accent-cyan);
            font-family: 'Orbitron', sans-serif;
        }

        /* --- INVOICE PRINT STYLE --- */
        .invoice-box {
            background: #fff;
            color: #000;
            padding: 40px;
            border-radius: 8px;
            font-family: 'Arial', sans-serif;
        }

        .invoice-header {
            display: flex;
            justify-content: space-between;
            border-bottom: 2px solid #000;
            padding-bottom: 20px;
            margin-bottom: 20px;
        }

        .invoice-title {
            font-size: 1.8rem;
            font-weight: 900;
            text-transform: uppercase;
        }

        .invoice-table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }

        .invoice-table th, .invoice-table td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left;
        }

        .invoice-table th {
            background: #f4f4f4;
        }

        .invoice-total {
            text-align: right;
            font-size: 1.3rem;
            font-weight: bold;
            margin-top: 20px;
        }

        @media print {
            body * { visibility: hidden; }
            #printable-invoice, #printable-invoice * { visibility: visible; }
            #printable-invoice {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                padding: 0;
            }
            .no-print { display: none !important; }
        }
    </style>
</head>
<body>

    <!-- 1. LOGIN SCREEN -->
    <div id="login-screen">
        <div class="login-card">
            <div class="login-logo">
                <i class="fa-solid me-2 fa-spray-can-sparkles"></i>
            </div>
            <h2>AUTO LLAKER & LIMAR</h2>
            <h1 style="color: var(--accent-cyan); font-size: 1.8rem; margin-bottom: 10px;">RIGONI</h1>
            <p>Sistemi i Menaxhimit të Veturave</p>
            
            <form id="login-form" onsubmit="handleLogin(event)">
                <div class="input-group">
                    <label><i class="fa-solid fa-user"></i> Përdoruesi</label>
                    <input type="text" id="username" placeholder="Shkruaj përdoruesin..." required autocomplete="off">
                </div>
                <div class="input-group">
                    <label><i class="fa-solid fa-key"></i> Fjalëkalimi</label>
                    <input type="password" id="password" placeholder="Shkruaj fjalëkalimin..." required>
                </div>
                <button type="submit" class="btn-primary">
                    Kyçou në Sistem <i class="fa-solid fa-right-to-bracket"></i>
                </button>
                <div id="login-error" class="error-msg">
                    <i class="fa-solid fa-triangle-exclamation"></i> Përdoruesi ose fjalëkalimi është gabim!
                </div>
            </form>
        </div>
    </div>

    <!-- 2. MAIN DASHBOARD APP -->
    <div id="app-dashboard">
        <!-- HEADER -->
        <header>
            <div class="brand">
                <i class="fa-solid fa-car-burst"></i>
                <div>
                    <div class="brand-title">AUTO LLAKER & LIMAR RIGONI</div>
                    <div class="brand-subtitle">PROFESSIONAL WORKSHOP SYSTEM</div>
                </div>
            </div>

            <div class="user-nav">
                <button class="stats-trigger-btn" onclick="openStatsModal()">
                    <i class="fa-solid fa-chart-pie"></i>
                    <span>Financat & Bilanci</span>
                </button>
                <button class="btn-logout" onclick="handleLogout()" title="Dilni">
                    <i class="fa-solid fa-power-off"></i>
                </button>
            </div>
        </header>

        <!-- MAIN CONTENT -->
        <main>
            <!-- TOP CONTROLS -->
            <div class="top-bar">
                <div class="search-filter">
                    <div class="input-group" style="margin-bottom: 0; flex: 1;">
                        <input type="text" id="search-input" placeholder="Kërko me pronar, model, targa..." oninput="renderCars()">
                    </div>
                    <div class="filter-btn-group">
                        <button class="filter-btn active" onclick="setFilter('all', this)">Të gjitha</button>
                        <button class="filter-btn" onclick="setFilter('working', this)">Në Punë</button>
                        <button class="filter-btn" onclick="setFilter('completed', this)">Të Kryera</button>
                    </div>
                </div>

                <button class="btn-add-car" onclick="openCarModal()">
                    <i class="fa-solid fa-plus-circle"></i>
                    Regjistro Veture të Re
                </button>
            </div>

            <!-- CAR CARDS GRID -->
            <div id="car-grid" class="car-grid">
                <!-- Cars will be loaded dynamically here -->
            </div>
        </main>
    </div>

    <!-- 3. ADD/EDIT CAR MODAL -->
    <div id="car-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modal-title" style="color: var(--accent-cyan);"><i class="fa-solid fa-car"></i> Regjistro Veture të Re</h3>
                <button class="modal-close" onclick="closeModal('car-modal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="car-form" onsubmit="saveCar(event)">
                    <input type="hidden" id="car-id">
                    
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 15px; margin-bottom: 20px;">
                        <div class="input-group">
                            <label>Emri i Pronarit *</label>
                            <input type="text" id="car-owner-input" required placeholder="Nderim Gashi">
                        </div>
                        <div class="input-group">
                            <label>Marka & Modeli *</label>
                            <input type="text" id="car-model-input" required placeholder="VW Golf 7, Audi A6...">
                        </div>
                        <div class="input-group">
                            <label>Targat *</label>
                            <input type="text" id="car-plates-input" required placeholder="01-123-AB">
                        </div>
                        <div class="input-group">
                            <label>Ngjyra / Kodi i Ngjyrës</label>
                            <input type="text" id="car-color-input" placeholder="E Zezë Metallic (LC9X)">
                        </div>
                        <div class="input-group">
                            <label>Numri i Telefonit</label>
                            <input type="text" id="car-phone-input" placeholder="044 123 456">
                        </div>
                        <div class="input-group">
                            <label>Data e Pranimit</label>
                            <input type="date" id="car-date-input" required>
                        </div>
                        <div class="input-group">
                            <label>Çmimi i Marreveshjes (€)</label>
                            <input type="number" id="car-price-input" step="0.01" placeholder="0.00">
                        </div>
                        <div class="input-group">
                            <label>Hargjimet e Materialit (€) (Opsionale)</label>
                            <input type="number" id="car-expenses-input" step="0.01" placeholder="0.00">
                        </div>
                    </div>

                    <!-- 360 INSPECTOR SECTION -->
                    <h4 style="margin-bottom: 10px; color: var(--accent-blue);"><i class="fa-solid fa-spray-can"></i> Zgjidh Pjesët për Lyerje / Rregullim</h4>
                    
                    <div class="car-inspector-container">
                        <div class="car-view-box">
                            <div class="view-controls">
                                <button type="button" class="view-btn active" onclick="changeCarView('side', this)">Anash</button>
                                <button type="button" class="view-btn" onclick="changeCarView('front', this)">Përpara</button>
                                <button type="button" class="view-btn" onclick="changeCarView('rear', this)">Prapa</button>
                                <button type="button" class="view-btn" onclick="changeCarView('top', this)">Sipër (Top)</button>
                            </div>

                            <div class="car-svg-wrapper" id="svg-container">
                                <!-- SVG Views will be rendered dynamically -->
                            </div>
                        </div>

                        <div class="parts-checklist">
                            <h4>Lista e Pjesëve</h4>
                            <div id="parts-list-checkboxes">
                                <!-- Checkboxes generated via JavaScript -->
                            </div>
                        </div>
                    </div>

                    <div style="margin-top: 20px; text-align: right;">
                        <button type="button" class="btn-logout" onclick="closeModal('car-modal')" style="margin-right: 10px;">Anulo</button>
                        <button type="submit" class="btn-primary" style="width: auto; display: inline-block; padding: 12px 30px;">
                            Ruaj Të Dhënat <i class="fa-solid fa-floppy-disk"></i>
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <!-- 4. STATS & ANALYTICS MODAL -->
    <div id="stats-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 style="color: var(--accent-cyan);"><i class="fa-solid fa-chart-line"></i> Pasqyra Financiare & Statistikat</h3>
                <button class="modal-close" onclick="closeModal('stats-modal')">&times;</button>
            </div>
            <div class="modal-body">
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Gjithsej Vetura</h3>
                        <div class="value" id="stat-total-cars">0</div>
                    </div>
                    <div class="stat-card">
                        <h3>Të Hyrat Komplet</h3>
                        <div class="value" id="stat-total-revenue" style="color: var(--accent-green);">€0.00</div>
                    </div>
                    <div class="stat-card">
                        <h3>Gjithsej Hargjime</h3>
                        <div class="value" id="stat-total-expenses" style="color: var(--accent-red);">€0.00</div>
                    </div>
                    <div class="stat-card">
                        <h3>Fitimi Neto (Profit)</h3>
                        <div class="value" id="stat-net-profit" style="color: var(--accent-cyan);">€0.00</div>
                    </div>
                </div>

                <div style="background: rgba(10,13,20,0.5); padding: 20px; border-radius: 12px; border: 1px solid var(--border-color);">
                    <h4 style="color: var(--accent-blue); margin-bottom: 15px;"><i class="fa-solid fa-circle-info"></i> Analiza e Punës</h4>
                    <p style="margin-bottom: 8px;">• Mesatarja e Fitimit për Kerr: <strong id="stat-avg-profit" style="color: #fff;">€0.00</strong></p>
                    <p style="margin-bottom: 8px;">• Kerri me Fitim më të Lartë: <strong id="stat-highest-car" style="color: var(--accent-green);">-</strong></p>
                    <p style="margin-bottom: 8px;">• Vetura në punë e sipër: <strong id="stat-working-count" style="color: var(--accent-orange);">0</strong></p>
                    <p>• Vetura të përfunduara: <strong id="stat-completed-count" style="color: var(--accent-green);">0</strong></p>
                </div>
            </div>
        </div>
    </div>

    <!-- 5. INVOICE PRINT MODAL -->
    <div id="invoice-modal" class="modal">
        <div class="modal-content" style="background: #fff; color: #000; max-width: 800px;">
            <div class="modal-header no-print" style="background: #121824; border-bottom: none;">
                <h3 style="color: var(--accent-cyan);"><i class="fa-solid fa-file-invoice-dollar"></i> Fatura e Shërbimit</h3>
                <div>
                    <button class="btn-primary" onclick="window.print()" style="padding: 6px 15px; font-size: 0.9rem; margin-right: 10px;">
                        <i class="fa-solid fa-print"></i> Printo / Ruaj PDF
                    </button>
                    <button class="modal-close" onclick="closeModal('invoice-modal')">&times;</button>
                </div>
            </div>
            
            <div class="modal-body" id="printable-invoice">
                <div class="invoice-box">
                    <div class="invoice-header">
                        <div>
                            <h2 style="font-size: 1.6rem; color: #000; font-weight: 800;">AUTO LLAKER & LIMAR "RIGONI"</h2>
                            <p style="color: #555; font-size: 0.9rem;">Servis Profesional për Lyerje dhe Limari</p>
                            <p style="color: #555; font-size: 0.9rem;">Pronari: Genit | Tel: +383 4X XXX XXX</p>
                        </div>
                        <div style="text-align: right;">
                            <div class="invoice-title">FATURË</div>
                            <p><strong>Nr:</strong> <span id="inv-num">INV-000</span></p>
                            <p><strong>Data:</strong> <span id="inv-date">--/--/----</span></p>
                        </div>
                    </div>

                    <div style="display: flex; justify-content: space-between; margin-bottom: 25px; font-size: 0.95rem;">
                        <div>
                            <h4 style="border-bottom: 1px solid #ccc; padding-bottom: 4px; margin-bottom: 8px;">KLIENTI:</h4>
                            <p><strong>Emri:</strong> <span id="inv-owner">--</span></p>
                            <p><strong>Tel:</strong> <span id="inv-phone">--</span></p>
                        </div>
                        <div>
                            <h4 style="border-bottom: 1px solid #ccc; padding-bottom: 4px; margin-bottom: 8px;">VETURA:</h4>
                            <p><strong>Modeli:</strong> <span id="inv-model">--</span></p>
                            <p><strong>Targat:</strong> <span id="inv-plates">--</span></p>
                            <p><strong>Ngjyra:</strong> <span id="inv-color">--</span></p>
                        </div>
                    </div>

                    <h4 style="margin-bottom: 10px;">SHËRBIMET DHE PJESËT E NDREQURA:</h4>
                    <table class="invoice-table">
                        <thead>
                            <tr>
                                <th>#</th>
                                <th>Përshkrimi i Pjesës / Shërbimit</th>
                                <th>Lloji i Punës</th>
                            </tr>
                        </thead>
                        <tbody id="inv-parts-table">
                            <!-- Populated dynamically -->
                        </tbody>
                    </table>

                    <div class="invoice-total">
                        Gjithsej për të paguar: <span id="inv-total-price" style="color: #000;">€0.00</span>
                    </div>

                    <div style="margin-top: 50px; display: flex; justify-content: space-between; text-align: center; font-size: 0.9rem;">
                        <div>
                            <p style="border-top: 1px solid #000; width: 180px; padding-top: 5px;">Nënshkrimi i Klientit</p>
                        </div>
                        <div>
                            <p style="border-top: 1px solid #000; width: 180px; padding-top: 5px;">Auto Llaker Rigoni</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // --- CONSTANTS & DATABASE ---
        const ALL_PARTS = [
            { id: 'hauba', name: 'Hauba' },
            { id: 'branik_perparm', name: 'Braniku Përpara' },
            { id: 'branik_prapam', name: 'Braniku Prapa' },
            { id: 'kulmi', name: 'Kulmi (Krov)' },
            { id: 'krah_majt', name: 'Krahi i Majtë Përpara' },
            { id: 'krah_djatht', name: 'Krahi i Djathtë Përpara' },
            { id: 'deri_m_p', name: 'Dera e Majtë Përpara' },
            { id: 'deri_d_p', name: 'Dera e Djathtë Përpara' },
            { id: 'deri_m_m', name: 'Dera e Majtë Prapa' },
            { id: 'deri_d_m', name: 'Dera e Djathtë Prapa' },
            { id: 'gepek', name: 'Gepeku (Prapa)' },
            { id: 'prag_majt', name: 'Pragu i Majtë' },
            { id: 'prag_djatht', name: 'Pragu i Djathtë' }
        ];

        let cars = JSON.parse(localStorage.getItem('rigoni_cars')) || [];
        let currentFilter = 'all';
        let activeView = 'side';
        let selectedParts = [];

        // INITIALIZATION
        window.onload = function() {
            // Check session
            if (sessionStorage.getItem('rigoni_logged_in') === 'true') {
                showDashboard();
            }
            // Set default date input to today
            document.getElementById('car-date-input').valueAsDate = new Date();
        };

        // --- AUTHENTICATION ---
        function handleLogin(e) {
            e.preventDefault();
            const u = document.getElementById('username').value.trim().toLowerCase();
            const p = document.getElementById('password').value.trim();

            if (u === 'genit' && p === 'genit1') {
                sessionStorage.setItem('rigoni_logged_in', 'true');
                showDashboard();
            } else {
                document.getElementById('login-error').style.display = 'block';
            }
        }

        function handleLogout() {
            sessionStorage.removeItem('rigoni_logged_in');
            document.getElementById('app-dashboard').style.display = 'none';
            document.getElementById('login-screen').style.display = 'flex';
        }

        function showDashboard() {
            document.getElementById('login-screen').style.display = 'none';
            document.getElementById('app-dashboard').style.display = 'flex';
            renderCars();
        }

        // --- CAR DATA MANAGEMENT ---
        function saveCar(e) {
            e.preventDefault();
            const id = document.getElementById('car-id').value || Date.now().toString();
            
            const carData = {
                id: id,
                owner: document.getElementById('car-owner-input').value,
                model: document.getElementById('car-model-input').value,
                plates: document.getElementById('car-plates-input').value,
                color: document.getElementById('car-color-input').value || 'E pacaktuar',
                phone: document.getElementById('car-phone-input').value || '-',
                date: document.getElementById('car-date-input').value,
                price: parseFloat(document.getElementById('car-price-input').value) || 0,
                expenses: parseFloat(document.getElementById('car-expenses-input').value) || 0,
                parts: [...selectedParts],
                status: document.getElementById('car-id').value ? 
                    (cars.find(c => c.id === id)?.status || 'working') : 'working'
            };

            const index = cars.findIndex(c => c.id === id);
            if (index > -1) {
                cars[index] = carData;
            } else {
                cars.unshift(carData);
            }

            saveToStorage();
            closeModal('car-modal');
            renderCars();
        }

        function toggleCarStatus(id) {
            const car = cars.find(c => c.id === id);
            if (car) {
                car.status = car.status === 'working' ? 'completed' : 'working';
                saveToStorage();
                renderCars();
            }
        }

        function deleteCar(id) {
            if (confirm('A jeni të sigurt që dëshironi ta fshini këtë veturë nga sistemi?')) {
                cars = cars.filter(c => c.id !== id);
                saveToStorage();
                renderCars();
            }
        }

        function saveToStorage() {
            localStorage.setItem('rigoni_cars', JSON.stringify(cars));
        }

        // --- RENDER CAR CARDS ---
        function renderCars() {
            const grid = document.getElementById('car-grid');
            const search = document.getElementById('search-input').value.toLowerCase();
            grid.innerHTML = '';

            const filtered = cars.filter(car => {
                const matchesFilter = currentFilter === 'all' || car.status === currentFilter;
                const matchesSearch = car.owner.toLowerCase().includes(search) ||
                                      car.model.toLowerCase().includes(search) ||
                                      car.plates.toLowerCase().includes(search);
                return matchesFilter && matchesSearch;
            });

            if (filtered.length === 0) {
                grid.innerHTML = `<div style="grid-column: 1/-1; text-align: center; color: var(--text-muted); padding: 50px;">
                    <i class="fa-solid fa-car-side" style="font-size: 3rem; margin-bottom: 15px; opacity: 0.3;"></i>
                    <p>Nuk u gjet asnjë veturë në sistem.</p>
                </div>`;
                return;
            }

            filtered.forEach(car => {
                const isWorking = car.status === 'working';
                const card = document.createElement('div');
                card.className = 'car-card';
                card.innerHTML = `
                    <div>
                        <span class="car-status-badge ${isWorking ? 'status-working' : 'status-completed'}">
                            ${isWorking ? '<i class="fa-solid fa-wrench"></i> Në Punë' : '<i class="fa-solid fa-check"></i> E Kryer'}
                        </span>
                        <div class="car-header">
                            <div class="car-title">${car.model}</div>
                            <div class="car-owner"><i class="fa-solid fa-user"></i> ${car.owner} (${car.phone})</div>
                        </div>

                        <div class="car-details-grid">
                            <div class="detail-item"><span>Targat</span><strong>${car.plates}</strong></div>
                            <div class="detail-item"><span>Ngjyra</span><strong>${car.color}</strong></div>
                            <div class="detail-item"><span>Data</span><strong>${car.date}</strong></div>
                            <div class="detail-item"><span>Çmimi</span><strong style="color: var(--accent-cyan);">€${car.price.toFixed(2)}</strong></div>
                        </div>

                        <div style="font-size: 0.85rem; color: var(--text-muted); margin-bottom: 15px;">
                            <strong>Pjesët për lyerje (${car.parts.length}):</strong><br>
                            <span style="color: #fff;">${car.parts.map(p => ALL_PARTS.find(ap => ap.id === p)?.name || p).join(', ') || 'Asnjë e zgjedhur'}</span>
                        </div>
                    </div>

                    <div class="car-actions">
                        <button class="btn-card-action" onclick="toggleCarStatus('${car.id}')" title="Ndrro Statutit">
                            <i class="fa-solid fa-rotate"></i> ${isWorking ? 'Kryej' : 'Kthe në Punë'}
                        </button>
                        <button class="btn-card-action" onclick="openInvoiceModal('${car.id}')" title="Printo Faturën">
                            <i class="fa-solid fa-file-invoice"></i> Fatura
                        </button>
                        <button class="btn-card-action" onclick="openCarModal('${car.id}')" title="Ndrysho">
                            <i class="fa-solid fa-pen-to-square"></i>
                        </button>
                        <button class="btn-card-action btn-card-delete" onclick="deleteCar('${car.id}')" title="Fshij">
                            <i class="fa-solid fa-trash"></i>
                        </button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function setFilter(filter, btn) {
            currentFilter = filter;
            document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            renderCars();
        }

        // --- 360 DEGREE INTERACTIVE INSPECTOR ---
        function changeCarView(view, btn) {
            activeView = view;
            document.querySelectorAll('.view-btn').forEach(b => b.classList.remove('active'));
            if(btn) btn.classList.add('active');
            renderSvgView();
        }

        function renderSvgView() {
            const container = document.getElementById('svg-container');
            let svgContent = '';

            if (activeView === 'side') {
                svgContent = `
                <svg viewBox="0 0 500 200" width="100%" height="100%">
                    <path class="car-part ${isPartSelected('hauba')?'selected':''}" onclick="togglePart('hauba')" d="M50,110 L120,105 L170,65 L200,65 L120,110 Z" data-part="hauba"/>
                    <path class="car-part ${isPartSelected('kulmi')?'selected':''}" onclick="togglePart('kulmi')" d="M170,65 L320,65 L360,105 L200,65 Z" data-part="kulmi"/>
                    <path class="car-part ${isPartSelected('deri_m_p')?'selected':''}" onclick="togglePart('deri_m_p')" d="M170,110 L250,110 L250,150 L170,150 Z" data-part="deri_m_p"/>
                    <path class="car-part ${isPartSelected('deri_m_m')?'selected':''}" onclick="togglePart('deri_m_m')" d="M250,110 L340,110 L340,150 L250,150 Z" data-part="deri_m_m"/>
                    <path class="car-part ${isPartSelected('branik_perparm')?'selected':''}" onclick="togglePart('branik_perparm')" d="M20,130 L60,125 L60,155 L20,150 Z" data-part="branik_perparm"/>
                    <path class="car-part ${isPartSelected('branik_prapam')?'selected':''}" onclick="togglePart('branik_prapam')" d="M420,125 L470,130 L470,150 L420,155 Z" data-part="branik_prapam"/>
                    <path class="car-part ${isPartSelected('gepek')?'selected':''}" onclick="togglePart('gepek')" d="M340,105 L420,110 L410,140 L340,140 Z" data-part="gepek"/>
                    <path class="car-part ${isPartSelected('prag_majt')?'selected':''}" onclick="togglePart('prag_majt')" d="M150,150 L350,150 L350,162 L150,162 Z" data-part="prag_majt"/>
                    <!-- Wheels -->
                    <circle cx="100" cy="155" r="28" fill="#111" stroke="#00d2ff" stroke-width="3"/>
                    <circle cx="390" cy="155" r="28" fill="#111" stroke="#00d2ff" stroke-width="3"/>
                </svg>`;
            } else if (activeView === 'front') {
                svgContent = `
                <svg viewBox="0 0 300 200" width="100%" height="100%">
                    <path class="car-part ${isPartSelected('hauba')?'selected':''}" onclick="togglePart('hauba')" d="M60,70 L240,70 L220,120 L80,120 Z"/>
                    <path class="car-part ${isPartSelected('branik_perparm')?'selected':''}" onclick="togglePart('branik_perparm')" d="M40,130 L260,130 L250,170 L50,170 Z"/>
                    <path class="car-part ${isPartSelected('kulmi')?'selected':''}" onclick="togglePart('kulmi')" d="M80,30 L220,30 L240,65 L60,65 Z"/>
                </svg>`;
            } else if (activeView === 'rear') {
                svgContent = `
                <svg viewBox="0 0 300 200" width="100%" height="100%">
                    <path class="car-part ${isPartSelected('gepek')?'selected':''}" onclick="togglePart('gepek')" d="M70,70 L230,70 L220,130 L80,130 Z"/>
                    <path class="car-part ${isPartSelected('branik_prapam')?'selected':''}" onclick="togglePart('branik_prapam')" d="M40,135 L260,135 L250,175 L50,175 Z"/>
                </svg>`;
            } else if (activeView === 'top') {
                svgContent = `
                <svg viewBox="0 0 200 350" width="100%" height="100%">
                    <path class="car-part ${isPartSelected('hauba')?'selected':''}" onclick="togglePart('hauba')" d="M40,40 L160,40 L150,110 L50,110 Z"/>
                    <path class="car-part ${isPartSelected('kulmi')?'selected':''}" onclick="togglePart('kulmi')" d="M50,115 L150,115 L150,220 L50,220 Z"/>
                    <path class="car-part ${isPartSelected('gepek')?'selected':''}" onclick="togglePart('gepek')" d="M50,225 L150,225 L160,290 L40,290 Z"/>
                </svg>`;
            }

            container.innerHTML = svgContent;
        }

        function isPartSelected(partId) {
            return selectedParts.includes(partId);
        }

        function togglePart(partId) {
            if (selectedParts.includes(partId)) {
                selectedParts = selectedParts.filter(p => p !== partId);
            } else {
                selectedParts.push(partId);
            }
            renderSvgView();
            renderCheckboxes();
        }

        function renderCheckboxes() {
            const container = document.getElementById('parts-list-checkboxes');
            container.innerHTML = '';

            ALL_PARTS.forEach(part => {
                const isChecked = selectedParts.includes(part.id);
                const item = document.createElement('div');
                item.className = 'part-item';
                item.innerHTML = `
                    <label for="chk-${part.id}" style="cursor:pointer;">${part.name}</label>
                    <input type="checkbox" id="chk-${part.id}" ${isChecked ? 'checked' : ''} onchange="togglePart('${part.id}')">
                `;
                container.appendChild(item);
            });
        }

        // --- MODAL CONTROLS ---
        function openCarModal(carId = null) {
            const modal = document.getElementById('car-modal');
            const form = document.getElementById('car-form');
            form.reset();

            if (carId) {
                const car = cars.find(c => c.id === carId);
                if (car) {
                    document.getElementById('modal-title').innerText = 'Ndrysho Të Dhënat e Kerrit';
                    document.getElementById('car-id').value = car.id;
                    document.getElementById('car-owner-input').value = car.owner;
                    document.getElementById('car-model-input').value = car.model;
                    document.getElementById('car-plates-input').value = car.plates;
                    document.getElementById('car-color-input').value = car.color;
                    document.getElementById('car-phone-input').value = car.phone;
                    document.getElementById('car-date-input').value = car.date;
                    document.getElementById('car-price-input').value = car.price;
                    document.getElementById('car-expenses-input').value = car.expenses;
                    selectedParts = [...car.parts];
                }
            } else {
                document.getElementById('modal-title').innerText = 'Regjistro Veture të Re';
                document.getElementById('car-id').value = '';
                document.getElementById('car-date-input').valueAsDate = new Date();
                selectedParts = [];
            }

            renderSvgView();
            renderCheckboxes();
            modal.style.display = 'flex';
        }

        function openStatsModal() {
            const totalCars = cars.length;
            const totalRev = cars.reduce((acc, c) => acc + (c.price || 0), 0);
            const totalExp = cars.reduce((acc, c) => acc + (c.expenses || 0), 0);
            const netProfit = totalRev - totalExp;
            const workingCount = cars.filter(c => c.status === 'working').length;
            const completedCount = cars.filter(c => c.status === 'completed').length;
            
            const avgProfit = totalCars > 0 ? (netProfit / totalCars) : 0;
            
            let highestCar = '-';
            if (cars.length > 0) {
                const top = [...cars].sort((a,b) => (b.price - b.expenses) - (a.price - a.expenses))[0];
                highestCar = `${top.model} (${top.owner}) - €${(top.price - top.expenses).toFixed(2)}`;
            }

            document.getElementById('stat-total-cars').innerText = totalCars;
            document.getElementById('stat-total-revenue').innerText = '€' + totalRev.toFixed(2);
            document.getElementById('stat-total-expenses').innerText = '€' + totalExp.toFixed(2);
            document.getElementById('stat-net-profit').innerText = '€' + netProfit.toFixed(2);
            document.getElementById('stat-avg-profit').innerText = '€' + avgProfit.toFixed(2);
            document.getElementById('stat-highest-car').innerText = highestCar;
            document.getElementById('stat-working-count').innerText = workingCount;
            document.getElementById('stat-completed-count').innerText = completedCount;

            document.getElementById('stats-modal').style.display = 'flex';
        }

        function openInvoiceModal(carId) {
            const car = cars.find(c => c.id === carId);
            if (!car) return;

            document.getElementById('inv-num').innerText = 'INV-' + car.id.slice(-4);
            document.getElementById('inv-date').innerText = car.date;
            document.getElementById('inv-owner').innerText = car.owner;
            document.getElementById('inv-phone').innerText = car.phone;
            document.getElementById('inv-model').innerText = car.model;
            document.getElementById('inv-plates').innerText = car.plates;
            document.getElementById('inv-color').innerText = car.color;
            document.getElementById('inv-total-price').innerText = '€' + car.price.toFixed(2);

            const partsTable = document.getElementById('inv-parts-table');
            partsTable.innerHTML = '';

            if (car.parts.length === 0) {
                partsTable.innerHTML = `<tr><td colspan="3" style="text-align:center;">Rregullim/Lyerje e Përgjithshme</td></tr>`;
            } else {
                car.parts.forEach((partId, idx) => {
                    const partObj = ALL_PARTS.find(p => p.id === partId);
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${idx + 1}</td>
                        <td>${partObj ? partObj.name : partId}</td>
                        <td>Lyerje & Limari</td>
                    `;
                    partsTable.appendChild(row);
                });
            }

            document.getElementById('invoice-modal').style.display = 'flex';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // Close modal when clicking outside content
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }
    </script>
</body>
</html>

