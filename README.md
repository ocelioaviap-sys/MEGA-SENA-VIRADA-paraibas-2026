<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mega da Virada 2026 - Sistema Completo com GitHub</title>
    <style>
        :root {
            --bg-primary: #0f1115;
            --bg-secondary: #1a1d24;
            --bg-card: #222630;
            --accent-green: #209e3f;
            --accent-neon: #00ff6a;
            --text-primary: #e2e8f0;
            --text-secondary: #94a3b8;
            --danger: #ef4444;
            --warning: #f59e0b;
            --info: #3b82f6;
            --purple: #a855f7;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-primary);
            margin: 0;
            padding: 20px;
            line-height: 1.6;
        }

        .container { max-width: 1200px; margin: 0 auto; }

        header {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 2px solid var(--accent-green);
            padding-bottom: 20px;
        }

        header h1 {
            color: var(--accent-neon);
            margin: 0;
            font-size: 2.5rem;
            text-shadow: 0 0 10px rgba(0, 255, 106, 0.3);
        }

        header p { color: var(--text-secondary); margin: 10px 0 0; }

        .tabs {
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .tab-btn {
            padding: 10px 18px;
            background: var(--bg-secondary);
            border: 1px solid #333;
            color: var(--text-secondary);
            cursor: pointer;
            border-radius: 8px 8px 0 0;
            font-size: 0.95rem;
            font-weight: 600;
            transition: all 0.3s;
        }

        .tab-btn.active {
            background: var(--bg-card);
            color: var(--accent-neon);
            border-bottom: 2px solid var(--accent-neon);
        }

        .tab-content {
            display: none;
            background: var(--bg-card);
            padding: 30px;
            border-radius: 0 12px 12px 12px;
            border: 1px solid #333;
            animation: fadeIn 0.4s;
        }

        .tab-content.active { display: block; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background: var(--bg-secondary);
            padding: 20px;
            border-radius: 10px;
            border-left: 4px solid var(--accent-green);
        }

        .card h3 { margin-top: 0; color: var(--accent-neon); font-size: 1.2rem; }

        .number-badge {
            display: inline-block;
            width: 40px;
            height: 40px;
            line-height: 40px;
            text-align: center;
            background: var(--bg-primary);
            border: 1px solid var(--accent-green);
            border-radius: 50%;
            margin: 4px;
            font-weight: bold;
            color: var(--accent-neon);
        }

        .number-badge.danger { border-color: var(--danger); color: var(--danger); }

        .number-grid {
            display: grid;
            grid-template-columns: repeat(10, 1fr);
            gap: 8px;
            margin: 20px 0;
        }

        .num-btn {
            aspect-ratio: 1;
            background: var(--bg-secondary);
            border: 1px solid #444;
            color: var(--text-primary);
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            transition: all 0.2s;
        }

        .num-btn:hover { background: #333; transform: scale(1.05); }

        .num-btn.selected {
            background: var(--accent-green);
            color: white;
            border-color: var(--accent-neon);
            box-shadow: 0 0 10px rgba(0, 255, 106, 0.4);
        }

        .num-btn.never-drawn {
            background: rgba(239, 68, 68, 0.1);
            border-color: var(--danger);
            color: var(--danger);
        }

        .analysis-panel {
            background: var(--bg-secondary);
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            border: 1px solid #333;
        }

        .analysis-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid #333;
            flex-wrap: wrap;
            gap: 10px;
        }

        .analysis-item:last-child { border-bottom: none; }
        
        .status-good { color: var(--accent-neon); font-weight: bold; }
        .status-warn { color: var(--warning); font-weight: bold; }
        .status-bad { color: var(--danger); font-weight: bold; }

        .btn {
            padding: 12px 24px;
            background: var(--accent-green);
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            transition: all 0.2s;
            margin: 5px;
        }

        .btn:hover { background: #187a30; transform: translateY(-2px); }
        .btn:disabled { opacity: 0.5; cursor: not-allowed; }

        .btn-secondary { background: #333; border: 1px solid #555; }
        .btn-secondary:hover { background: #444; }

        .btn-info { background: var(--info); }
        .btn-info:hover { background: #2563eb; }

        .btn-danger { background: var(--danger); }
        .btn-danger:hover { background: #dc2626; }

        .btn-purple { background: var(--purple); }
        .btn-purple:hover { background: #9333ea; }

        .btn-sm { padding: 6px 12px; font-size: 0.85rem; }

        .game-card {
            background: var(--bg-secondary);
            padding: 15px;
            border-radius: 8px;
            margin: 10px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-left: 4px solid var(--accent-neon);
            flex-wrap: wrap;
            gap: 10px;
        }

        .game-numbers {
            font-size: 1.3rem;
            font-weight: bold;
            letter-spacing: 2px;
        }

        .game-tag {
            font-size: 0.8rem;
            background: rgba(0, 255, 106, 0.1);
            color: var(--accent-neon);
            padding: 4px 8px;
            border-radius: 4px;
        }

        .input-group {
            margin: 20px 0;
            display: flex;
            gap: 10px;
            align-items: center;
            flex-wrap: wrap;
        }

        input[type="number"], input[type="text"], input[type="password"], select, textarea {
            padding: 10px;
            background: var(--bg-primary);
            border: 1px solid #444;
            color: white;
            border-radius: 6px;
            font-size: 1rem;
        }

        input[type="number"] { width: 80px; }
        input[type="text"], input[type="password"], textarea { min-width: 200px; }
        textarea { min-height: 100px; resize: vertical; width: 100%; }

        .disclaimer {
            margin-top: 30px;
            padding: 15px;
            background: rgba(245, 158, 11, 0.1);
            border-left: 4px solid var(--warning);
            color: var(--text-secondary);
            font-size: 0.9rem;
            border-radius: 4px;
        }

        .player-card {
            background: var(--bg-secondary);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            border-left: 4px solid var(--info);
        }

        .player-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .player-name {
            font-size: 1.4rem;
            color: var(--accent-neon);
            margin: 0;
        }

        .player-stats {
            display: flex;
            gap: 15px;
            font-size: 0.95rem;
            color: var(--text-secondary);
            flex-wrap: wrap;
        }

        .player-stats b { color: var(--accent-neon); }

        .saved-game {
            background: var(--bg-primary);
            padding: 12px 15px;
            border-radius: 6px;
            margin: 8px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .saved-game-numbers {
            font-weight: bold;
            font-size: 1.1rem;
            letter-spacing: 1px;
        }

        .saved-game-info {
            display: flex;
            gap: 15px;
            align-items: center;
            flex-wrap: wrap;
        }

        .cost-tag {
            background: rgba(59, 130, 246, 0.15);
            color: var(--info);
            padding: 4px 10px;
            border-radius: 4px;
            font-weight: bold;
        }

        .summary-box {
            background: linear-gradient(135deg, rgba(32, 158, 63, 0.15), rgba(0, 255, 106, 0.05));
            border: 2px solid var(--accent-green);
            padding: 25px;
            border-radius: 12px;
            margin-top: 30px;
            text-align: center;
        }

        .summary-box h2 { color: var(--accent-neon); margin-top: 0; }

        .summary-total {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--accent-neon);
            margin: 15px 0;
            text-shadow: 0 0 15px rgba(0, 255, 106, 0.4);
        }

        .summary-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .summary-item {
            background: var(--bg-secondary);
            padding: 15px;
            border-radius: 8px;
        }

        .summary-item-label {
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-bottom: 5px;
        }

        .summary-item-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--accent-neon);
        }

        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: var(--text-secondary);
        }

        .empty-state-icon { font-size: 3rem; margin-bottom: 10px; }

        .modal-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .modal-overlay.active { display: flex; }

        .modal {
            background: var(--bg-card);
            padding: 30px;
            border-radius: 12px;
            max-width: 600px;
            width: 100%;
            border: 1px solid #444;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal h3 { color: var(--accent-neon); margin-top: 0; }

        .modal input, .modal select, .modal textarea {
            width: 100%;
            box-sizing: border-box;
            margin: 10px 0;
        }

        .consolidation-player {
            background: var(--bg-secondary);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            border-left: 4px solid var(--purple);
        }

        .consolidation-player h3 {
            color: var(--purple);
            margin-top: 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .imported-badge {
            background: rgba(168, 85, 247, 0.15);
            color: var(--purple);
            padding: 4px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
        }

        .online-badge {
            background: rgba(32, 158, 63, 0.15);
            color: var(--accent-green);
            padding: 4px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
        }

        .upload-area {
            border: 2px dashed #444;
            border-radius: 10px;
            padding: 40px 20px;
            text-align: center;
            margin: 20px 0;
            transition: all 0.3s;
            cursor: pointer;
        }

        .upload-area:hover {
            border-color: var(--accent-neon);
            background: rgba(0, 255, 106, 0.05);
        }

        .upload-area-icon { font-size: 3rem; margin-bottom: 10px; }

        .info-box {
            background: rgba(59, 130, 246, 0.1);
            border-left: 4px solid var(--info);
            padding: 15px;
            border-radius: 6px;
            margin: 15px 0;
            color: var(--text-secondary);
        }

        .info-box b { color: var(--info); }

        .github-config {
            background: rgba(168, 85, 247, 0.1);
            border-left: 4px solid var(--purple);
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
        }

        .github-config h3 {
            color: var(--purple);
            margin-top: 0;
        }

        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 8px;
            color: white;
            font-weight: bold;
            z-index: 2000;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            animation: slideIn 0.3s, fadeOut 0.3s 2.7s;
            max-width: 400px;
        }

        .toast-success { background: var(--accent-green); }
        .toast-error { background: var(--danger); }
        .toast-info { background: var(--info); }

        @keyframes slideIn {
            from { transform: translateX(400px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        @keyframes fadeOut {
            from { opacity: 1; }
            to { opacity: 0; }
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: var(--bg-primary);
            border-radius: 4px;
            overflow: hidden;
            margin: 15px 0;
            display: none;
        }

        .progress-bar.active { display: block; }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--accent-green), var(--accent-neon));
            width: 0%;
            transition: width 0.3s;
        }

        .storage-indicator {
            background: var(--bg-secondary);
            padding: 10px 15px;
            border-radius: 6px;
            margin: 10px 0;
            font-size: 0.9rem;
            color: var(--text-secondary);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .storage-indicator b { color: var(--accent-neon); }

        .price-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        .price-table th, .price-table td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #333;
        }

        .price-table th {
            background: var(--bg-primary);
            color: var(--accent-neon);
        }

        .price-table tr:hover { background: rgba(0, 255, 106, 0.05); }

        .share-link-box {
            background: var(--bg-primary);
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            border: 1px solid #444;
        }

        .share-link-box textarea {
            width: 100%;
            min-height: 80px;
            font-family: monospace;
            font-size: 0.85rem;
            resize: none;
        }

        @media print {
            body { background: white !important; color: black !important; padding: 10px; }
            .container { max-width: 100%; }
            .tabs, .tab-btn, .btn, .modal-overlay, .disclaimer, header, .upload-area, .info-box, .toast, .storage-indicator, .github-config { display: none !important; }
            .tab-content {
                display: block !important;
                background: white !important;
                color: black !important;
                border: none !important;
                padding: 0 !important;
                page-break-inside: avoid;
            }
            #tab-pools, #tab-consolidation { display: block !important; }
            #tab-stats, #tab-custom, #tab-smart, #tab-generator, #tab-prices, #tab-github { display: none !important; }
            .player-card, .consolidation-player {
                background: white !important;
                border: 2px solid #209e3f !important;
                color: black !important;
                page-break-inside: avoid;
            }
            .player-name { color: #209e3f !important; }
            .consolidation-player h3 { color: #6b21a8 !important; }
            .saved-game {
                background: #f5f5f5 !important;
                color: black !important;
                border: 1px solid #ddd !important;
            }
            .saved-game-numbers { color: black !important; }
            .cost-tag { background: #e3f2fd !important; color: #1976d2 !important; }
            .summary-box {
                background: #f0f9f4 !important;
                border: 3px solid #209e3f !important;
                color: black !important;
            }
            .summary-total { color: #209e3f !important; text-shadow: none !important; }
            .summary-item { background: #f5f5f5 !important; }
            .summary-item-value { color: #209e3f !important; }
            .print-header {
                display: block !important;
                text-align: center;
                border-bottom: 3px solid #209e3f;
                padding-bottom: 15px;
                margin-bottom: 20px;
            }
            .print-header h1 { color: #209e3f !important; margin: 0; }
            .print-header p { color: #555 !important; }
        }

        .print-header { display: none; }

        @media (max-width: 600px) {
            .number-grid { grid-template-columns: repeat(6, 1fr); }
            header h1 { font-size: 1.8rem; }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>🍀 Mega da Virada 2026</h1>
        <p>Sistema Completo com GitHub - Administrador (Ocelio)</p>
    </header>

    <div class="print-header">
        <h1>🍀 Bolão Mega da Virada 2026</h1>
        <p>Relatório gerado em: <span id="print-date"></span></p>
    </div>

    <div class="tabs">
        <button class="tab-btn active" onclick="openTab(event, 'tab-stats')">📊 Estatísticas</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-custom')">🎯 Meus Jogos</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-smart')">🧠 Fechamentos</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-pools')">💰 Meus Bolões</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-consolidation')">📥 Consolidação</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-github')">🐙 GitHub Online</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-generator')">⚙️ Gerar HTML Jogador</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-prices')">💵 Tabela de Preços</button>
    </div>

    <!-- TAB 1: ESTATÍSTICAS -->
    <div id="tab-stats" class="tab-content active">
        <h2>Histórico de 17 Edições (2009 a 2025)</h2>
        <div class="stats-grid">
            <div class="card">
                <h3>🔥 Números Mais Sorteados</h3>
                <p style="color: var(--text-secondary); font-size: 0.9rem;">Números que mais apareceram nos sorteios de virada.</p>
                <div id="hot-numbers"></div>
            </div>
            <div class="card" style="border-left-color: var(--danger);">
                <h3 style="color: var(--danger);">🚫 Números Nunca Sorteados</h3>
                <p style="color: var(--text-secondary); font-size: 0.9rem;">Dezenas que <b>JAMAIS</b> saíram na Mega da Virada.</p>
                <div id="cold-numbers"></div>
            </div>
            <div class="card">
                <h3>⚖️ Distribuição Pares / Ímpares</h3>
                <ul style="list-style: none; padding: 0;">
                    <li>3 Pares / 3 Ímpares: <b style="color: var(--accent-neon)">41,2%</b> (Mais comum)</li>
                    <li>4 Pares / 2 Ímpares: <b style="color: var(--accent-neon)">35,3%</b></li>
                    <li>2 Pares / 4 Ímpares: <b>11,8%</b></li>
                    <li>1 Par / 5 Ímpares: <b>11,8%</b></li>
                    <li style="color: var(--danger);">0 ou 6 Pares/Ímpares: <b>0%</b> (Nunca ocorreu)</li>
                </ul>
            </div>
        </div>
    </div>

    <!-- TAB 2: JOGOS PRÓPRIOS -->
    <div id="tab-custom" class="tab-content">
        <h2>Monte Seu Jogo Próprio</h2>
        <p>Selecione de 6 a 20 números. Os números em <span style="color: var(--danger); font-weight:bold;">vermelho</span> nunca saíram na Virada.</p>
        
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 10px;">
            <span>Selecionados: <b id="selected-count" style="color: var(--accent-neon); font-size: 1.2rem;">0</b> / 60</span>
            <div>
                <button class="btn btn-secondary btn-sm" onclick="clearSelection()">Limpar</button>
                <button class="btn btn-info btn-sm" onclick="openSaveModal()" id="save-game-btn" style="display:none;">💾 Salvar para Jogador</button>
            </div>
        </div>

        <div class="number-grid" id="custom-grid"></div>

        <div class="analysis-panel" id="analysis-panel" style="display: none;">
            <h3>🔍 Análise Inteligente do Seu Jogo</h3>
            <div id="analysis-results"></div>
            <div id="game-cost-preview" style="margin-top: 15px; padding: 10px; background: var(--bg-primary); border-radius: 6px;"></div>
        </div>
    </div>

    <!-- TAB 3: FECHAMENTOS -->
    <div id="tab-smart" class="tab-content">
        <h2>Fechamentos e Gerador Estratégico</h2>
        
        <div class="card" style="margin-bottom: 20px;">
            <h3>🤖 Gerador Estratégico</h3>
            <div class="input-group">
                <label>Quantidade de jogos:</label>
                <input type="number" id="qtd-games" value="5" min="1" max="20">
                <button class="btn" onclick="generateSmartGames()">Gerar Jogos</button>
            </div>
            <div id="smart-games-output"></div>
        </div>

        <div class="card">
            <h3>🔒 Fechamento Matemático</h3>
            <div class="input-group">
                <label>Seus números (separados por vírgula):</label>
                <input type="text" id="closure-input" style="width: 300px;" placeholder="Ex: 05, 10, 17, 20, 33, 34, 41, 58">
                <button class="btn" onclick="generateClosure()">Gerar Fechamento</button>
            </div>
            <div id="closure-output"></div>
        </div>
    </div>

    <!-- TAB 4: BOLÕES -->
    <div id="tab-pools" class="tab-content">
        <h2>💰 Gestão de Bolões - Mega da Virada 2026</h2>
        <p style="color: var(--text-secondary);">Crie jogadores, salve seus jogos e veja o custo total.</p>

        <div style="display: flex; gap: 10px; margin: 20px 0; flex-wrap: wrap;">
            <button class="btn" onclick="openPlayerModal()">➕ Adicionar Jogador</button>
            <button class="btn btn-info" onclick="printPools()">🖨️ Imprimir / Salvar PDF</button>
            <button class="btn btn-danger btn-sm" onclick="clearAllPools()" style="margin-left:auto;">🗑️ Limpar Tudo</button>
        </div>

        <div id="players-container"></div>
        <div id="summary-container"></div>
    </div>

    <!-- TAB 5: CONSOLIDAÇÃO -->
    <div id="tab-consolidation" class="tab-content">
        <h2>📥 Consolidação dos Jogos dos Jogadores</h2>
        <p style="color: var(--text-secondary);">Importe os arquivos JSON enviados pelos jogadores OU receba automaticamente via GitHub.</p>

        <div class="info-box">
            <b>📋 Como funciona:</b>
            <ol style="margin: 10px 0; padding-left: 20px;">
                <li>Configure o GitHub na aba <b>"🐙 GitHub Online"</b></li>
                <li>Gere o HTML do jogador na aba <b>"⚙️ Gerar HTML Jogador"</b></li>
                <li>Envie o arquivo para cada jogador</li>
                <li>Cada jogador monta seus jogos e clica em <b>"💾 Enviar para Ocelio"</b></li>
                <li>Os jogos são enviados automaticamente para o GitHub e aparecem aqui!</li>
            </ol>
        </div>

        <div class="storage-indicator">
            <span>💾 Status do armazenamento:</span>
            <span><b id="storage-count">0</b> jogador(es) salvo(s) | <b id="storage-size">0</b> KB</span>
        </div>

        <div style="display: flex; gap: 10px; margin: 20px 0; flex-wrap: wrap;">
            <button class="btn btn-purple" onclick="syncFromGitHub()">🔄 Sincronizar do GitHub</button>
            <button class="btn btn-info" onclick="printConsolidation()">🖨️ Imprimir Consolidação</button>
            <button class="btn btn-secondary" onclick="exportAllConsolidated()">📤 Exportar Tudo (Backup)</button>
            <button class="btn btn-danger btn-sm" onclick="clearConsolidation()">🗑️ Limpar Importações</button>
        </div>

        <div class="upload-area" id="upload-area" onclick="document.getElementById('file-input').click()">
            <div class="upload-area-icon">📂</div>
            <h3>Ou clique aqui para importar arquivos JSON manualmente</h3>
            <p style="color: var(--text-secondary);">Selecione um ou vários arquivos de jogadores</p>
            <input type="file" id="file-input" accept=".json" multiple style="display:none;">
        </div>

        <div class="progress-bar" id="progress-bar">
            <div class="progress-fill" id="progress-fill"></div>
        </div>

        <div id="consolidation-container"></div>
        <div id="consolidation-summary"></div>
    </div>

    <!-- TAB 6: GITHUB CONFIG -->
    <div id="tab-github" class="tab-content">
        <h2>🐙 Configuração GitHub - Receber Jogos Online</h2>
        <p style="color: var(--text-secondary);">Configure o GitHub para que os jogadores possam enviar seus jogos online diretamente.</p>

        <div class="github-config">
            <h3>🔑 Configuração do GitHub</h3>
            <p style="color: var(--text-secondary);">Para receber os jogos online, você precisa de um <b>Token de Acesso Pessoal</b> do GitHub e um <b>Gist ID</b>.</p>
            
            <div class="info-box">
                <b>📋 Passo a passo:</b>
                <ol style="margin: 10px 0; padding-left: 20px;">
                    <li>Acesse <a href="https://github.com/settings/tokens" target="_blank" style="color: var(--info);">github.com/settings/tokens</a></li>
                    <li>Clique em <b>"Generate new token (classic)"</b></li>
                    <li>Dê um nome (ex: "Mega Virada") e marque a permissão <b>"gist"</b></li>
                    <li>Copie o token gerado (só aparece uma vez!)</li>
                    <li>Crie um Gist em <a href="https://gist.github.com" target="_blank" style="color: var(--info);">gist.github.com</a> com o conteúdo inicial <code>{"players":[]}</code></li>
                    <li>Copie o ID do Gist (está na URL: gist.github.com/seu_usuario/<b style="color: var(--accent-neon);">ID_AQUI</b>)</li>
                    <li>Cole o Token e o Gist ID abaixo</li>
                </ol>
            </div>

            <div class="input-group">
                <label>Token do GitHub:</label>
                <input type="password" id="github-token" placeholder="ghp_xxxxxxxxxxxx" style="flex: 1;">
            </div>
            <div class="input-group">
                <label>Gist ID:</label>
                <input type="text" id="gist-id" placeholder="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" style="flex: 1;">
            </div>
            <div class="input-group">
                <label>Nome do arquivo no Gist:</label>
                <input type="text" id="gist-filename" value="mega_virada_2026.json" style="flex: 1;">
            </div>

            <div style="display: flex; gap: 10px; margin-top: 20px;">
                <button class="btn" onclick="saveGitHubConfig()">💾 Salvar Configuração</button>
                <button class="btn btn-secondary" onclick="testGitHubConnection()">🧪 Testar Conexão</button>
                <button class="btn btn-info" onclick="syncFromGitHub()">🔄 Sincronizar Agora</button>
            </div>

            <div id="github-status" style="margin-top: 20px;"></div>
        </div>

        <div class="card" style="margin-top: 30px;">
            <h3>📤 Link de Compartilhamento para Jogadores</h3>
            <p style="color: var(--text-secondary);">Após configurar, gere o HTML do jogador na próxima aba. O jogador terá o botão "Enviar para Ocelio" que envia direto para este Gist.</p>
        </div>
    </div>

    <!-- TAB 7: GERADOR HTML JOGADOR -->
    <div id="tab-generator" class="tab-content">
        <h2>⚙️ Gerar HTML para Jogadores</h2>
        <p style="color: var(--text-secondary);">Baixe o HTML simplificado para enviar aos jogadores. Eles poderão montar seus jogos e enviar online ou exportar um arquivo.</p>

        <div class="card" style="margin: 20px 0;">
            <h3>📄 HTML do Jogador</h3>
            <p>Este arquivo contém apenas o essencial para o jogador:</p>
            <ul style="color: var(--text-secondary);">
                <li>✅ Estatísticas históricas</li>
                <li>✅ Montagem de jogos próprios</li>
                <li>✅ Fechamentos inteligentes</li>
                <li>✅ <b style="color: var(--accent-neon);">Botão "Enviar para Ocelio"</b> (envia online via GitHub)</li>
                <li>✅ Botão "Exportar Meus Jogos" (backup local)</li>
                <li>✅ Botão "Imprimir"</li>
            </ul>
            <button class="btn btn-purple" onclick="downloadPlayerHTML()" style="margin-top: 15px;">📥 Baixar HTML do Jogador</button>
        </div>

        <div class="info-box">
            <b>💡 Dica:</b> Após baixar, você pode renomear o arquivo para algo personalizado como <code>mega_virada_annely.html</code>, <code>mega_virada_tia.html</code>, etc., antes de enviar.
        </div>
    </div>

    <!-- TAB 8: TABELA DE PREÇOS -->
    <div id="tab-prices" class="tab-content">
        <h2>💵 Tabela Oficial de Preços - Mega-Sena (2026)</h2>
        <p style="color: var(--text-secondary);">Valores atualizados conforme Caixa Econômica Federal.</p>
        
        <table class="price-table">
            <thead>
                <tr>
                    <th>Números</th>
                    <th>Combinações</th>
                    <th>Valor da Aposta</th>
                </tr>
            </thead>
            <tbody id="price-table-body"></tbody>
        </table>
    </div>

    <div class="disclaimer">
        <b>⚠️ Aviso Importante:</b> Loteria é um jogo de azar. Análises estatísticas e fechamentos organizam o jogo, mas <b>não garantem premiação</b>. Valores atualizados conforme tabela oficial da Caixa (vigente em 2026). Jogue com responsabilidade.
    </div>
</div>

<!-- MODAL: ADICIONAR JOGADOR -->
<div class="modal-overlay" id="player-modal">
    <div class="modal">
        <h3>➕ Novo Jogador</h3>
        <input type="text" id="player-name-input" placeholder="Nome do jogador (ex: Ocelio, Annely...)">
        <div style="display: flex; gap: 10px; justify-content: flex-end; margin-top: 15px;">
            <button class="btn btn-secondary" onclick="closePlayerModal()">Cancelar</button>
            <button class="btn" onclick="addPlayer()">Adicionar</button>
        </div>
    </div>
</div>

<!-- MODAL: SALVAR JOGO -->
<div class="modal-overlay" id="save-modal">
    <div class="modal">
        <h3>💾 Salvar Jogo para Jogador</h3>
        <p style="color: var(--text-secondary);">Selecione para qual jogador este jogo será destinado:</p>
        <select id="save-player-select" style="width: 100%; margin: 10px 0;"></select>
        <input type="text" id="game-obs-input" placeholder="Observação (opcional, ex: Jogo 1, Palpite da sorte...)" style="width: 100%; margin: 10px 0;">
        <div style="display: flex; gap: 10px; justify-content: flex-end; margin-top: 15px;">
            <button class="btn btn-secondary" onclick="closeSaveModal()">Cancelar</button>
            <button class="btn" onclick="confirmSaveGame()">Salvar</button>
        </div>
    </div>
</div>

<script>
    // --- DADOS HISTÓRICOS ---
    const NEVER_DRAWN = [7, 8, 26, 28, 39, 44, 54, 60];
    const HOT_NUMBERS = [
        {num: 10, freq: 5}, {num: 33, freq: 5}, {num: 5, freq: 4},
        {num: 3, freq: 3}, {num: 17, freq: 3}, {num: 20, freq: 3}, 
        {num: 32, freq: 3}, {num: 34, freq: 3}, {num: 36, freq: 3}, 
        {num: 41, freq: 3}, {num: 56, freq: 3}, {num: 58, freq: 3}
    ];

    // --- TABELA DE PREÇOS OFICIAL MEGA-SENA 2026 ---
    const PRICE_TABLE = {
        6: 6.00, 7: 42.00, 8: 168.00, 9: 504.00, 10: 1260.00,
        11: 2772.00, 12: 5544.00, 13: 10296.00, 14: 18018.00, 15: 30030.00,
        16: 48048.00, 17: 74256.00, 18: 111384.00, 19: 162792.00, 20: 232560.00
    };

    function calculateGameCost(n) { return PRICE_TABLE[n] || 0; }
    function formatBRL(value) { return value.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }); }

    // --- ESTADO GLOBAL ---
    let players = [];
    let importedPlayers = [];
    let selectedNumbers = new Set();

    // --- GITHUB CONFIG ---
    let githubConfig = JSON.parse(localStorage.getItem('github_config') || '{}');

    // --- TOAST DE NOTIFICAÇÃO ---
    function showToast(message, type = 'success') {
        const toast = document.createElement('div');
        toast.className = `toast toast-${type}`;
        toast.textContent = message;
        document.body.appendChild(toast);
        setTimeout(() => toast.remove(), 3000);
    }

    // --- FUNÇÕES DE PERSISTÊNCIA ---
    function loadFromStorage() {
        try {
            players = JSON.parse(localStorage.getItem('mega_players') || '[]');
            importedPlayers = JSON.parse(localStorage.getItem('mega_imported') || '[]');
            console.log('✅ Dados carregados do localStorage:', { players: players.length, imported: importedPlayers.length });
        } catch (e) {
            console.error('❌ Erro ao carregar do localStorage:', e);
            players = [];
            importedPlayers = [];
            showToast('Erro ao carregar dados salvos', 'error');
        }
    }

    function savePlayers() {
        try {
            localStorage.setItem('mega_players', JSON.stringify(players));
            console.log('✅ Jogadores salvos:', players.length);
            return true;
        } catch (e) {
            console.error('❌ Erro ao salvar jogadores:', e);
            showToast('Erro ao salvar jogadores', 'error');
            return false;
        }
    }

    function saveImported() {
        try {
            const data = JSON.stringify(importedPlayers);
            localStorage.setItem('mega_imported', data);
            console.log('✅ Importados salvos:', importedPlayers.length, 'jogadores |', (data.length / 1024).toFixed(2), 'KB');
            updateStorageIndicator();
            return true;
        } catch (e) {
            console.error('❌ Erro ao salvar importados:', e);
            showToast('Erro ao salvar dados (armazenamento cheio?)', 'error');
            return false;
        }
    }

    function updateStorageIndicator() {
        const countEl = document.getElementById('storage-count');
        const sizeEl = document.getElementById('storage-size');
        if (countEl && sizeEl) {
            countEl.textContent = importedPlayers.length;
            const sizeKB = (JSON.stringify(importedPlayers).length / 1024).toFixed(2);
            sizeEl.textContent = sizeKB;
        }
    }

    // --- GITHUB FUNCTIONS ---
    function saveGitHubConfig() {
        const token = document.getElementById('github-token').value.trim();
        const gistId = document.getElementById('gist-id').value.trim();
        const filename = document.getElementById('gist-filename').value.trim() || 'mega_virada_2026.json';

        if (!token || !gistId) {
            showToast('Preencha o Token e o Gist ID!', 'error');
            return;
        }

        githubConfig = { token, gistId, filename };
        localStorage.setItem('github_config', JSON.stringify(githubConfig));
        showToast('✅ Configuração do GitHub salva!', 'success');
        updateGitHubStatus();
    }

    function updateGitHubStatus() {
        const statusEl = document.getElementById('github-status');
        if (githubConfig.token && githubConfig.gistId) {
            statusEl.innerHTML = `
                <div class="info-box" style="border-left-color: var(--accent-green);">
                    <b style="color: var(--accent-green);">✅ GitHub configurado</b><br>
                    Gist ID: <code>${githubConfig.gistId.substring(0, 8)}...</code><br>
                    Arquivo: <code>${githubConfig.filename}</code>
                </div>
            `;
        } else {
            statusEl.innerHTML = `
                <div class="info-box" style="border-left-color: var(--warning);">
                    <b style="color: var(--warning);">⚠️ GitHub não configurado</b><br>
                    Configure o Token e Gist ID acima para receber jogos online.
                </div>
            `;
        }
    }

    async function testGitHubConnection() {
        if (!githubConfig.token || !githubConfig.gistId) {
            showToast('Configure o GitHub primeiro!', 'error');
            return;
        }

        try {
            const response = await fetch(`https://api.github.com/gists/${githubConfig.gistId}`, {
                headers: {
                    'Authorization': `token ${githubConfig.token}`,
                    'Accept': 'application/vnd.github.v3+json'
                }
            });

            if (response.ok) {
                showToast('✅ Conexão com GitHub funcionando!', 'success');
            } else {
                showToast('❌ Erro na conexão com GitHub', 'error');
            }
        } catch (e) {
            showToast('❌ Erro de rede', 'error');
        }
    }

    async function syncFromGitHub() {
        if (!githubConfig.token || !githubConfig.gistId) {
            showToast('Configure o GitHub na aba "🐙 GitHub Online" primeiro!', 'error');
            return;
        }

        showToast('🔄 Sincronizando do GitHub...', 'info');

        try {
            const response = await fetch(`https://api.github.com/gists/${githubConfig.gistId}`, {
                headers: {
                    'Authorization': `token ${githubConfig.token}`,
                    'Accept': 'application/vnd.github.v3+json'
                }
            });

            if (!response.ok) throw new Error('Erro na API do GitHub');

            const gist = await response.json();
            const file = gist.files[githubConfig.filename];
            
            if (!file) {
                showToast('Arquivo não encontrado no Gist', 'error');
                return;
            }

            const data = JSON.parse(file.content);
            
            if (data.players && Array.isArray(data.players)) {
                importedPlayers = data.players;
                saveImported();
                renderConsolidation();
                showToast(`✅ ${importedPlayers.length} jogador(es) sincronizado(s) do GitHub!`, 'success');
            } else {
                showToast('Formato inválido no arquivo do Gist', 'error');
            }
        } catch (e) {
            console.error('Erro ao sincronizar:', e);
            showToast('❌ Erro ao sincronizar do GitHub', 'error');
        }
    }

    async function pushToGitHub() {
        if (!githubConfig.token || !githubConfig.gistId) {
            return false;
        }

        try {
            const data = {
                files: {
                    [githubConfig.filename]: {
                        content: JSON.stringify({ 
                            players: importedPlayers,
                            lastUpdate: new Date().toISOString()
                        }, null, 2)
                    }
                }
            };

            const response = await fetch(`https://api.github.com/gists/${githubConfig.gistId}`, {
                method: 'PATCH',
                headers: {
                    'Authorization': `token ${githubConfig.token}`,
                    'Accept': 'application/vnd.github.v3+json',
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(data)
            });

            return response.ok;
        } catch (e) {
            console.error('Erro ao push para GitHub:', e);
            return false;
        }
    }

    // --- INICIALIZAÇÃO ---
    document.addEventListener('DOMContentLoaded', () => {
        loadFromStorage();
        renderStats();
        renderCustomGrid();
        renderPlayers();
        renderConsolidation();
        renderPriceTable();
        updateStorageIndicator();
        document.getElementById('print-date').textContent = new Date().toLocaleString('pt-BR');
        
        // Carrega config do GitHub
        if (githubConfig.token) {
            document.getElementById('github-token').value = githubConfig.token;
        }
        if (githubConfig.gistId) {
            document.getElementById('gist-id').value = githubConfig.gistId;
        }
        if (githubConfig.filename) {
            document.getElementById('gist-filename').value = githubConfig.filename;
        }
        updateGitHubStatus();
        
        // Configura drag-and-drop
        setupDragAndDrop();
        
        // Configura input de arquivos
        document.getElementById('file-input').addEventListener('change', handleFiles);
    });

    function setupDragAndDrop() {
        const uploadArea = document.getElementById('upload-area');
        ['dragenter', 'dragover'].forEach(eventName => {
            uploadArea.addEventListener(eventName, (e) => {
                e.preventDefault();
                uploadArea.style.borderColor = 'var(--accent-neon)';
                uploadArea.style.background = 'rgba(0, 255, 106, 0.1)';
            });
        });
        ['dragleave', 'drop'].forEach(eventName => {
            uploadArea.addEventListener(eventName, (e) => {
                e.preventDefault();
                uploadArea.style.borderColor = '#444';
                uploadArea.style.background = 'transparent';
            });
        });
        uploadArea.addEventListener('drop', (e) => {
            const files = e.dataTransfer.files;
            if (files.length) processFiles(Array.from(files));
        });
    }

    function openTab(evt, tabName) {
        document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
        document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
        document.getElementById(tabName).classList.add('active');
        evt.currentTarget.classList.add('active');
        if (tabName === 'tab-pools') renderPlayers();
        if (tabName === 'tab-consolidation') renderConsolidation();
        if (tabName === 'tab-github') updateGitHubStatus();
    }

    // --- TAB 1: ESTATÍSTICAS ---
    function renderStats() {
        const hotContainer = document.getElementById('hot-numbers');
        HOT_NUMBERS.forEach(h => {
            hotContainer.innerHTML += `<span class="number-badge" title="Sorteado ${h.freq}x">${String(h.num).padStart(2, '0')}</span>`;
        });
        const coldContainer = document.getElementById('cold-numbers');
        NEVER_DRAWN.forEach(n => {
            coldContainer.innerHTML += `<span class="number-badge danger" title="Nunca sorteado">${String(n).padStart(2, '0')}</span>`;
        });
    }

    // --- TAB 2: JOGOS PRÓPRIOS ---
    function renderCustomGrid() {
        const grid = document.getElementById('custom-grid');
        for (let i = 1; i <= 60; i++) {
            const btn = document.createElement('button');
            btn.className = 'num-btn';
            btn.textContent = String(i).padStart(2, '0');
            btn.dataset.num = i;
            if (NEVER_DRAWN.includes(i)) btn.classList.add('never-drawn');
            btn.onclick = () => toggleNumber(i, btn);
            grid.appendChild(btn);
        }
    }

    function toggleNumber(num, btn) {
        if (selectedNumbers.has(num)) {
            selectedNumbers.delete(num);
            btn.classList.remove('selected');
        } else {
            selectedNumbers.add(num);
            btn.classList.add('selected');
        }
        updateAnalysis();
    }

    function clearSelection() {
        selectedNumbers.clear();
        document.querySelectorAll('.num-btn').forEach(b => b.classList.remove('selected'));
        document.getElementById('analysis-panel').style.display = 'none';
        document.getElementById('selected-count').textContent = '0';
        document.getElementById('save-game-btn').style.display = 'none';
    }

    function updateAnalysis() {
        const count = selectedNumbers.size;
        document.getElementById('selected-count').textContent = count;
        const panel = document.getElementById('analysis-panel');
        const results = document.getElementById('analysis-results');
        const costPreview = document.getElementById('game-cost-preview');
        
        if (count < 6) {
            panel.style.display = 'none';
            document.getElementById('save-game-btn').style.display = 'none';
            return;
        }
        panel.style.display = 'block';
        document.getElementById('save-game-btn').style.display = 'inline-block';
        
        const nums = Array.from(selectedNumbers);
        const evens = nums.filter(n => n % 2 === 0).length;
        const odds = count - evens;
        const hotHits = nums.filter(n => HOT_NUMBERS.some(h => h.num === n)).length;
        const coldHits = nums.filter(n => NEVER_DRAWN.includes(n)).length;

        let parImparStatus = 'status-bad';
        let parImparText = 'Desequilibrado (Nunca ocorreu na Virada)';
        if ((evens === 3 && odds === 3) || (evens === 4 && odds === 2) || (evens === 2 && odds === 4)) {
            parImparStatus = 'status-good';
            parImparText = 'Excelente (Padrão histórico de 88% dos sorteios)';
        } else if ((evens === 1 && odds === 5) || (evens === 5 && odds === 1)) {
            parImparStatus = 'status-warn';
            parImparText = 'Aceitável (Ocorreu apenas 11,8% das vezes)';
        }

        let coldStatus = coldHits === 0 ? 'status-good' : 'status-bad';
        let coldText = coldHits === 0 ? 'Nenhum número "frio" histórico incluído.' : `Atenção: ${coldHits} número(s) NUNCA sorteado(s) na Virada.`;

        results.innerHTML = `
            <div class="analysis-item">
                <span>Equilíbrio Par/Ímpar (${evens}P / ${odds}I):</span>
                <span class="${parImparStatus}">${parImparText}</span>
            </div>
            <div class="analysis-item">
                <span>Números Mais Frequentes (${hotHits}):</span>
                <span class="${hotHits >= 2 ? 'status-good' : 'status-warn'}">${hotHits} dezenas do Top 12 histórico.</span>
            </div>
            <div class="analysis-item">
                <span>Números "Frios" (Nunca Sorteados):</span>
                <span class="${coldStatus}">${coldText}</span>
            </div>
            <div class="analysis-item">
                <span>Soma das Dezenas:</span>
                <span style="color: var(--text-primary);">${nums.reduce((a, b) => a + b, 0)}</span>
            </div>
        `;

        const cost = calculateGameCost(count);
        costPreview.innerHTML = `
            <div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px;">
                <span>💵 Custo desta aposta (${count} dezenas):</span>
                <span style="color: var(--accent-neon); font-size: 1.3rem; font-weight: bold;">${formatBRL(cost)}</span>
            </div>
        `;
    }

    // --- TAB 3: FECHAMENTOS ---
    function generateSmartGames() {
        const qtd = parseInt(document.getElementById('qtd-games').value);
        const output = document.getElementById('smart-games-output');
        output.innerHTML = '';

        let pool = [];
        for(let i=1; i<=60; i++) {
            if(!NEVER_DRAWN.includes(i)) {
                let weight = HOT_NUMBERS.some(h => h.num === i) ? 3 : 1;
                for(let w=0; w<weight; w++) pool.push(i);
            }
        }

        for(let g=0; g<qtd; g++) {
            let game = new Set();
            let attempts = 0;
            while(game.size < 6 && attempts < 100) {
                game.add(pool[Math.floor(Math.random() * pool.length)]);
                attempts++;
            }
            let gameArr = Array.from(game).sort((a, b) => a - b);
            let evens = gameArr.filter(n => n % 2 === 0).length;
            if(!(evens===3 || evens===4 || evens===2)) { g--; continue; }

            const gameStr = gameArr.map(n => String(n).padStart(2, '0')).join(' - ');
            output.innerHTML += `
                <div class="game-card">
                    <span class="game-numbers">${gameStr}</span>
                    <span class="game-tag">Estratégico ${evens}P/${6-evens}I - ${formatBRL(6.00)}</span>
                </div>
            `;
        }
    }

    function generateClosure() {
        const input = document.getElementById('closure-input').value;
        const output = document.getElementById('closure-output');
        const nums = input.match(/\d+/g);
        if (!nums) {
            output.innerHTML = '<p style="color: var(--danger);">Insira os números separados por vírgula.</p>';
            return;
        }
        const uniqueNums = [...new Set(nums.map(Number))].filter(n => n >= 1 && n <= 60).sort((a,b) => a-b);
        if (uniqueNums.length < 8 || uniqueNums.length > 10) {
            output.innerHTML = `<p style="color: var(--danger);">O fechamento exige entre 8 e 10 números. Você inseriu ${uniqueNums.length}.</p>`;
            return;
        }
        const combinations = getCombinations(uniqueNums, 6);
        const totalCost = combinations.length * 6.00;
        let html = `<p style="color: var(--accent-neon); margin-top: 15px;">Fechamento gerado! <b>${combinations.length} jogos</b> | Custo total: <b>${formatBRL(totalCost)}</b></p>`;
        combinations.forEach((combo, index) => {
            const str = combo.map(n => String(n).padStart(2, '0')).join(' - ');
            html += `<div class="game-card"><span class="game-numbers">${str}</span><span class="game-tag">Jogo ${index + 1} - ${formatBRL(6.00)}</span></div>`;
        });
        output.innerHTML = html;
    }

    function getCombinations(arr, k) {
        const result = [];
        function combine(start, combo) {
            if (combo.length === k) { result.push([...combo]); return; }
            for (let i = start; i < arr.length; i++) {
                combo.push(arr[i]);
                combine(i + 1, combo);
                combo.pop();
            }
        }
        combine(0, []);
        return result;
    }

    // --- TAB 4: BOLÕES ---
    function openPlayerModal() {
        document.getElementById('player-modal').classList.add('active');
        document.getElementById('player-name-input').value = '';
        document.getElementById('player-name-input').focus();
    }

    function closePlayerModal() {
        document.getElementById('player-modal').classList.remove('active');
    }

    function addPlayer() {
        const name = document.getElementById('player-name-input').value.trim();
        if (!name) { alert('Digite o nome do jogador!'); return; }
        players.push({ id: Date.now(), name: name, games: [] });
        if (savePlayers()) {
            showToast(`✅ Jogador "${name}" adicionado!`, 'success');
        }
        closePlayerModal();
        renderPlayers();
    }

    function removePlayer(id) {
        if (!confirm('Remover este jogador e todos os seus jogos?')) return;
        players = players.filter(p => p.id !== id);
        savePlayers();
        renderPlayers();
    }

    function removeGame(playerId, gameIndex) {
        if (!confirm('Remover este jogo?')) return;
        const player = players.find(p => p.id === playerId);
        player.games.splice(gameIndex, 1);
        savePlayers();
        renderPlayers();
    }

    function openSaveModal() {
        if (players.length === 0) {
            alert('Crie pelo menos um jogador na aba "Meus Bolões" primeiro!');
            return;
        }
        const select = document.getElementById('save-player-select');
        select.innerHTML = players.map(p => `<option value="${p.id}">${p.name}</option>`).join('');
        document.getElementById('game-obs-input').value = '';
        document.getElementById('save-modal').classList.add('active');
    }

    function closeSaveModal() {
        document.getElementById('save-modal').classList.remove('active');
    }

    function confirmSaveGame() {
        const playerId = parseInt(document.getElementById('save-player-select').value);
        const obs = document.getElementById('game-obs-input').value.trim();
        const player = players.find(p => p.id === playerId);
        if (!player) return;

        const nums = Array.from(selectedNumbers).sort((a, b) => a - b);
        const cost = calculateGameCost(nums.length);

        player.games.push({
            numbers: nums,
            obs: obs || `Jogo ${player.games.length + 1}`,
            cost: cost,
            createdAt: new Date().toLocaleString('pt-BR')
        });

        if (savePlayers()) {
            showToast(`✅ Jogo salvo para ${player.name}! Custo: ${formatBRL(cost)}`, 'success');
        }
        closeSaveModal();
        clearSelection();
    }

    function renderPlayers() {
        const container = document.getElementById('players-container');
        const summaryContainer = document.getElementById('summary-container');

        if (players.length === 0) {
            container.innerHTML = `
                <div class="empty-state">
                    <div class="empty-state-icon">🎲</div>
                    <h3>Nenhum jogador cadastrado</h3>
                    <p>Clique em "Adicionar Jogador" para começar.</p>
                </div>
            `;
            summaryContainer.innerHTML = '';
            return;
        }

        let totalGames = 0;
        let totalCost = 0;
        let html = '';

        players.forEach(player => {
            const playerCost = player.games.reduce((sum, g) => sum + g.cost, 0);
            totalGames += player.games.length;
            totalCost += playerCost;

            html += `
                <div class="player-card">
                    <div class="player-header">
                        <h3 class="player-name">👤 ${player.name}</h3>
                        <div>
                            <button class="btn btn-sm btn-secondary" onclick="addQuickGame(${player.id})">➕ Jogo Rápido (6 n°)</button>
                            <button class="btn btn-sm btn-danger" onclick="removePlayer(${player.id})">🗑️ Remover</button>
                        </div>
                    </div>
                    <div class="player-stats">
                        <span>🎯 Jogos: <b>${player.games.length}</b></span>
                        <span>💵 Total: <b>${formatBRL(playerCost)}</b></span>
                    </div>
                    <div>
                        ${player.games.length === 0 ? '<p style="color: var(--text-secondary); text-align: center; padding: 15px;">Nenhum jogo salvo.</p>' : ''}
                        ${player.games.map((game, idx) => `
                            <div class="saved-game">
                                <div>
                                    <div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 3px;">${game.obs}</div>
                                    <div class="saved-game-numbers">${game.numbers.map(n => String(n).padStart(2, '0')).join(' - ')}</div>
                                </div>
                                <div class="saved-game-info">
                                    <span style="color: var(--text-secondary); font-size: 0.85rem;">${game.numbers.length} dezenas</span>
                                    <span class="cost-tag">${formatBRL(game.cost)}</span>
                                    <button class="btn btn-sm btn-danger" onclick="removeGame(${player.id}, ${idx})">✕</button>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </div>
            `;
        });

        container.innerHTML = html;

        summaryContainer.innerHTML = `
            <div class="summary-box">
                <h2>📊 Resumo Geral do Bolão</h2>
                <div class="summary-total">${formatBRL(totalCost)}</div>
                <div class="summary-details">
                    <div class="summary-item">
                        <div class="summary-item-label">Total de Jogadores</div>
                        <div class="summary-item-value">${players.length}</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-item-label">Total de Jogos</div>
                        <div class="summary-item-value">${totalGames}</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-item-label">Custo Médio por Jogador</div>
                        <div class="summary-item-value">${formatBRL(totalCost / players.length)}</div>
                    </div>
                </div>
            </div>
        `;
    }

    function addQuickGame(playerId) {
        const player = players.find(p => p.id === playerId);
        if (!player) return;
        const obs = prompt('Observação para este jogo:', `Jogo ${player.games.length + 1}`);
        if (obs === null) return;
        
        let nums = new Set();
        let pool = [];
        for(let i=1; i<=60; i++) {
            if(!NEVER_DRAWN.includes(i)) {
                let weight = HOT_NUMBERS.some(h => h.num === i) ? 3 : 1;
                for(let w=0; w<weight; w++) pool.push(i);
            }
        }
        while(nums.size < 6) nums.add(pool[Math.floor(Math.random() * pool.length)]);
        
        const sortedNums = Array.from(nums).sort((a,b) => a-b);
        player.games.push({
            numbers: sortedNums,
            obs: obs || `Jogo ${player.games.length + 1}`,
            cost: 6.00,
            createdAt: new Date().toLocaleString('pt-BR')
        });
        savePlayers();
        renderPlayers();
    }

    function clearAllPools() {
        if (!confirm('⚠️ Apagar TODOS os jogadores e jogos?')) return;
        players = [];
        savePlayers();
        renderPlayers();
    }

    function printPools() {
        document.getElementById('print-date').textContent = new Date().toLocaleString('pt-BR');
        window.print();
    }

    // --- TAB 5: CONSOLIDAÇÃO ---
    
    function readFileAsJSON(file) {
        return new Promise((resolve, reject) => {
            const reader = new FileReader();
            reader.onload = (e) => {
                try {
                    const data = JSON.parse(e.target.result);
                    resolve({ file, data });
                } catch (err) {
                    reject({ file, error: err });
                }
            };
            reader.onerror = () => reject({ file, error: new Error('Erro na leitura') });
            reader.readAsText(file);
        });
    }

    async function processFiles(files) {
        if (!files.length) return;

        const progressBar = document.getElementById('progress-bar');
        const progressFill = document.getElementById('progress-fill');
        progressBar.classList.add('active');
        progressFill.style.width = '0%';

        let successCount = 0;
        let errorCount = 0;
        const errors = [];

        for (let i = 0; i < files.length; i++) {
            const file = files[i];
            progressFill.style.width = ((i / files.length) * 100) + '%';

            try {
                const { data } = await readFileAsJSON(file);
                
                if (!data.playerName || !Array.isArray(data.games)) {
                    throw new Error('Formato inválido');
                }

                const existingIndex = importedPlayers.findIndex(p => p.playerName === data.playerName);
                if (existingIndex >= 0) {
                    if (confirm(`Jogador "${data.playerName}" já foi importado.\nDeseja SUBSTITUIR pelos novos jogos do arquivo "${file.name}"?`)) {
                        importedPlayers[existingIndex] = data;
                        successCount++;
                    }
                } else {
                    importedPlayers.push(data);
                    successCount++;
                }
            } catch (err) {
                errorCount++;
                errors.push(`${file.name}: ${err.error?.message || 'Erro desconhecido'}`);
            }
        }

        progressFill.style.width = '100%';

        if (successCount > 0) {
            const saved = saveImported();
            if (saved) {
                showToast(`✅ ${successCount} jogador(es) importado(s) e salvo(s) com sucesso!`, 'success');
                // Push para GitHub se configurado
                if (githubConfig.token && githubConfig.gistId) {
                    const pushed = await pushToGitHub();
                    if (pushed) {
                        showToast('✅ Dados sincronizados com GitHub!', 'success');
                    }
                }
            }
        }

        if (errorCount > 0) {
            showToast(`⚠️ ${errorCount} arquivo(s) com erro. Veja o console (F12).`, 'error');
            console.warn('Arquivos com erro:', errors);
        }

        renderConsolidation();
        
        setTimeout(() => {
            progressBar.classList.remove('active');
            progressFill.style.width = '0%';
        }, 1000);

        document.getElementById('file-input').value = '';
    }

    function handleFiles(event) {
        const files = Array.from(event.target.files);
        processFiles(files);
    }

    function removeImported(index) {
        if (!confirm('Remover este jogador da consolidação?')) return;
        importedPlayers.splice(index, 1);
        saveImported();
        renderConsolidation();
        showToast('Jogador removido da consolidação', 'info');
    }

    function clearConsolidation() {
        if (!confirm('⚠️ Apagar TODAS as importações?')) return;
        importedPlayers = [];
        saveImported();
        renderConsolidation();
        showToast('Todas as importações foram apagadas', 'info');
    }

    function exportAllConsolidated() {
        if (importedPlayers.length === 0) {
            showToast('Não há dados para exportar', 'error');
            return;
        }
        const data = {
            exportDate: new Date().toLocaleString('pt-BR'),
            totalPlayers: importedPlayers.length,
            players: importedPlayers
        };
        const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = `backup_consolidacao_${new Date().toISOString().split('T')[0]}.json`;
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
        URL.revokeObjectURL(url);
        showToast('✅ Backup exportado!', 'success');
    }

    function renderConsolidation() {
        const container = document.getElementById('consolidation-container');
        const summaryContainer = document.getElementById('consolidation-summary');

        if (importedPlayers.length === 0) {
            container.innerHTML = `
                <div class="empty-state">
                    <div class="empty-state-icon">📭</div>
                    <h3>Nenhum jogador importado ainda</h3>
                    <p>Importe os arquivos JSON ou sincronize do GitHub acima.</p>
                </div>
            `;
            summaryContainer.innerHTML = '';
            return;
        }

        let totalGames = 0;
        let totalCost = 0;
        let html = '';

        importedPlayers.forEach((player, index) => {
            const playerCost = player.games.reduce((sum, g) => sum + g.cost, 0);
            totalGames += player.games.length;
            totalCost += playerCost;

            html += `
                <div class="consolidation-player">
                    <h3>
                        <span>👤 ${player.playerName}</span>
                        <div>
                            ${player.source === 'github' ? '<span class="online-badge">🌐 Online</span>' : '<span class="imported-badge">📥 Importado</span>'}
                            <button class="btn btn-sm btn-danger" onclick="removeImported(${index})">🗑️</button>
                        </div>
                    </h3>
                    <div class="player-stats" style="margin-bottom: 15px;">
                        <span>🎯 Jogos: <b>${player.games.length}</b></span>
                        <span>💵 Total: <b>${formatBRL(playerCost)}</b></span>
                        ${player.exportDate ? `<span>📅 ${player.exportDate}</span>` : ''}
                    </div>
                    ${player.games.map((game, idx) => `
                        <div class="saved-game">
                            <div>
                                <div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 3px;">${game.obs || `Jogo ${idx + 1}`}</div>
                                <div class="saved-game-numbers">${game.numbers.map(n => String(n).padStart(2, '0')).join(' - ')}</div>
                            </div>
                            <div class="saved-game-info">
                                <span style="color: var(--text-secondary); font-size: 0.85rem;">${game.numbers.length} dezenas</span>
                                <span class="cost-tag">${formatBRL(game.cost)}</span>
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
        });

        container.innerHTML = html;

        summaryContainer.innerHTML = `
            <div class="summary-box">
                <h2>📊 Consolidação Geral - Todos os Jogadores</h2>
                <div class="summary-total">${formatBRL(totalCost)}</div>
                <div class="summary-details">
                    <div class="summary-item">
                        <div class="summary-item-label">Jogadores Importados</div>
                        <div class="summary-item-value">${importedPlayers.length}</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-item-label">Total de Jogos</div>
                        <div class="summary-item-value">${totalGames}</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-item-label">Custo Médio por Jogador</div>
                        <div class="summary-item-value">${formatBRL(totalCost / importedPlayers.length)}</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-item-label">Custo Médio por Jogo</div>
                        <div class="summary-item-value">${totalGames > 0 ? formatBRL(totalCost / totalGames) : formatBRL(0)}</div>
                    </div>
                </div>
            </div>
        `;
    }

    function printConsolidation() {
        document.getElementById('print-date').textContent = new Date().toLocaleString('pt-BR');
        window.print();
    }

    // --- TAB 8: TABELA DE PREÇOS ---
    function renderPriceTable() {
        const tbody = document.getElementById('price-table-body');
        let html = '';
        for (let n = 6; n <= 20; n++) {
            const combinations = calculateCombinations(n, 6);
            html += `
                <tr>
                    <td><b style="color: var(--accent-neon);">${n}</b> números</td>
                    <td>${combinations.toLocaleString('pt-BR')}</td>
                    <td><b style="color: var(--accent-neon);">${formatBRL(PRICE_TABLE[n])}</b></td>
                </tr>
            `;
        }
        tbody.innerHTML = html;
    }

    function calculateCombinations(n, k) {
        let c = 1;
        for (let i = 0; i < k; i++) {
            c = c * (n - i) / (i + 1);
        }
        return Math.round(c);
    }

    // --- TAB 7: GERADOR HTML JOGADOR ---
    function downloadPlayerHTML() {
        const htmlContent = generatePlayerHTML();
        const blob = new Blob([htmlContent], { type: 'text/html;charset=utf-8' });
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = 'mega_virada_jogador.html';
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
        URL.revokeObjectURL(url);
        showToast('✅ HTML do jogador baixado! Envie para seus jogadores.', 'success');
    }

    function generatePlayerHTML() {
        const githubToken = githubConfig.token || '';
        const gistId = githubConfig.gistId || '';
        const gistFilename = githubConfig.filename || 'mega_virada_2026.json';

        return `<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mega da Virada 2026 - Meus Jogos</title>
    <style>
        :root {
            --bg-primary: #0f1115;
            --bg-secondary: #1a1d24;
            --bg-card: #222630;
            --accent-green: #209e3f;
            --accent-neon: #00ff6a;
            --text-primary: #e2e8f0;
            --text-secondary: #94a3b8;
            --danger: #ef4444;
            --warning: #f59e0b;
            --info: #3b82f6;
        }
        body { font-family: 'Segoe UI', Roboto, sans-serif; background: var(--bg-primary); color: var(--text-primary); margin: 0; padding: 20px; line-height: 1.6; }
        .container { max-width: 1000px; margin: 0 auto; }
        header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid var(--accent-green); padding-bottom: 20px; }
        header h1 { color: var(--accent-neon); margin: 0; font-size: 2.2rem; text-shadow: 0 0 10px rgba(0, 255, 106, 0.3); }
        header p { color: var(--text-secondary); margin: 10px 0 0; }
        .tabs { display: flex; gap: 8px; margin-bottom: 20px; flex-wrap: wrap; }
        .tab-btn { padding: 10px 18px; background: var(--bg-secondary); border: 1px solid #333; color: var(--text-secondary); cursor: pointer; border-radius: 8px 8px 0 0; font-size: 0.95rem; font-weight: 600; }
        .tab-btn.active { background: var(--bg-card); color: var(--accent-neon); border-bottom: 2px solid var(--accent-neon); }
        .tab-content { display: none; background: var(--bg-card); padding: 25px; border-radius: 0 12px 12px 12px; border: 1px solid #333; }
        .tab-content.active { display: block; }
        .card { background: var(--bg-secondary); padding: 20px; border-radius: 10px; border-left: 4px solid var(--accent-green); margin-bottom: 15px; }
        .card h3 { margin-top: 0; color: var(--accent-neon); }
        .number-badge { display: inline-block; width: 40px; height: 40px; line-height: 40px; text-align: center; background: var(--bg-primary); border: 1px solid var(--accent-green); border-radius: 50%; margin: 4px; font-weight: bold; color: var(--accent-neon); }
        .number-badge.danger { border-color: var(--danger); color: var(--danger); }
        .number-grid { display: grid; grid-template-columns: repeat(10, 1fr); gap: 8px; margin: 20px 0; }
        .num-btn { aspect-ratio: 1; background: var(--bg-secondary); border: 1px solid #444; color: var(--text-primary); border-radius: 8px; cursor: pointer; font-size: 1.1rem; font-weight: bold; }
        .num-btn:hover { background: #333; }
        .num-btn.selected { background: var(--accent-green); color: white; border-color: var(--accent-neon); box-shadow: 0 0 10px rgba(0, 255, 106, 0.4); }
        .num-btn.never-drawn { background: rgba(239, 68, 68, 0.1); border-color: var(--danger); color: var(--danger); }
        .analysis-panel { background: var(--bg-secondary); padding: 20px; border-radius: 10px; margin-top: 20px; border: 1px solid #333; }
        .analysis-item { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #333; flex-wrap: wrap; gap: 10px; }
        .analysis-item:last-child { border-bottom: none; }
        .status-good { color: var(--accent-neon); font-weight: bold; }
        .status-warn { color: var(--warning); font-weight: bold; }
        .status-bad { color: var(--danger); font-weight: bold; }
        .btn { padding: 12px 24px; background: var(--accent-green); color: white; border: none; border-radius: 6px; cursor: pointer; font-size: 1rem; font-weight: bold; margin: 5px; }
        .btn:hover { background: #187a30; }
        .btn-secondary { background: #333; border: 1px solid #555; }
        .btn-info { background: var(--info); }
        .btn-purple { background: #a855f7; }
        .btn-danger { background: var(--danger); }
        .btn-sm { padding: 6px 12px; font-size: 0.85rem; }
        .game-card { background: var(--bg-secondary); padding: 15px; border-radius: 8px; margin: 10px 0; display: flex; justify-content: space-between; align-items: center; border-left: 4px solid var(--accent-neon); flex-wrap: wrap; gap: 10px; }
        .game-numbers { font-size: 1.3rem; font-weight: bold; letter-spacing: 2px; }
        .game-tag { font-size: 0.8rem; background: rgba(0, 255, 106, 0.1); color: var(--accent-neon); padding: 4px 8px; border-radius: 4px; }
        .input-group { margin: 20px 0; display: flex; gap: 10px; align-items: center; flex-wrap: wrap; }
        input[type="number"], input[type="text"] { padding: 10px; background: var(--bg-primary); border: 1px solid #444; color: white; border-radius: 6px; font-size: 1rem; }
        input[type="number"] { width: 80px; }
        .saved-game { background: var(--bg-primary); padding: 12px 15px; border-radius: 6px; margin: 8px 0; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; }
        .saved-game-numbers { font-weight: bold; font-size: 1.1rem; letter-spacing: 1px; }
        .cost-tag { background: rgba(59, 130, 246, 0.15); color: var(--info); padding: 4px 10px; border-radius: 4px; font-weight: bold; }
        .summary-box { background: linear-gradient(135deg, rgba(32, 158, 63, 0.15), rgba(0, 255, 106, 0.05)); border: 2px solid var(--accent-green); padding: 25px; border-radius: 12px; margin-top: 30px; text-align: center; }
        .summary-box h2 { color: var(--accent-neon); margin-top: 0; }
        .summary-total { font-size: 2.5rem; font-weight: bold; color: var(--accent-neon); margin: 15px 0; }
        .export-info { background: rgba(168, 85, 247, 0.1); border-left: 4px solid #a855f7; padding: 15px; border-radius: 6px; margin: 20px 0; color: var(--text-secondary); }
        .export-info b { color: #a855f7; }
        .player-name-input { padding: 12px; background: var(--bg-primary); border: 2px solid var(--accent-neon); color: var(--accent-neon); border-radius: 6px; font-size: 1.1rem; font-weight: bold; width: 100%; max-width: 400px; box-sizing: border-box; }
        .toast { position: fixed; top: 20px; right: 20px; padding: 15px 25px; border-radius: 8px; color: white; font-weight: bold; z-index: 2000; box-shadow: 0 4px 12px rgba(0,0,0,0.3); }
        .toast-success { background: var(--accent-green); }
        .toast-error { background: var(--danger); }
        .toast-info { background: var(--info); }
        @media print {
            body { background: white !important; color: black !important; }
            .tabs, .tab-btn, .btn, .export-info, header { display: none !important; }
            .tab-content { display: block !important; background: white !important; color: black !important; border: none !important; padding: 0 !important; }
            #tab-mygames { display: block !important; }
            #tab-stats, #tab-smart { display: none !important; }
            .card { background: white !important; border: 2px solid #209e3f !important; color: black !important; }
            .saved-game { background: #f5f5f5 !important; color: black !important; border: 1px solid #ddd !important; }
            .saved-game-numbers { color: black !important; }
            .cost-tag { background: #e3f2fd !important; color: #1976d2 !important; }
            .summary-box { background: #f0f9f4 !important; border: 3px solid #209e3f !important; }
            .summary-total { color: #209e3f !important; }
            .print-header { display: block !important; text-align: center; border-bottom: 3px solid #209e3f; padding-bottom: 15px; margin-bottom: 20px; }
            .print-header h1 { color: #209e3f !important; }
        }
        .print-header { display: none; }
        @media (max-width: 600px) { .number-grid { grid-template-columns: repeat(6, 1fr); } header h1 { font-size: 1.6rem; } }
    </style>
</head>
<body>
<div class="container">
    <header>
        <h1>🍀 Mega da Virada 2026</h1>
        <p>Monte seus jogos e envie para o Ocelio!</p>
    </header>

    <div class="print-header">
        <h1>🍀 Meus Jogos - Mega da Virada 2026</h1>
        <p>Jogador: <b id="print-player-name"></b> | Gerado em: <span id="print-date"></span></p>
    </div>

    <div style="margin-bottom: 20px; padding: 15px; background: var(--bg-secondary); border-radius: 8px;">
        <label style="color: var(--text-secondary);">👤 Seu nome:</label><br>
        <input type="text" id="player-name" class="player-name-input" placeholder="Digite seu nome aqui" onchange="savePlayerName()">
    </div>

    <div class="tabs">
        <button class="tab-btn active" onclick="openTab(event, 'tab-stats')">📊 Estatísticas</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-mygames')">🎯 Meus Jogos</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-smart')">🧠 Fechamentos</button>
    </div>

    <div id="tab-stats" class="tab-content active">
        <h2>Histórico (2009 a 2025)</h2>
        <div class="card">
            <h3>🔥 Números Mais Sorteados</h3>
            <div id="hot-numbers"></div>
        </div>
        <div class="card" style="border-left-color: var(--danger);">
            <h3 style="color: var(--danger);">🚫 Números Nunca Sorteados</h3>
            <div id="cold-numbers"></div>
        </div>
    </div>

    <div id="tab-mygames" class="tab-content">
        <h2>🎯 Monte Seus Jogos</h2>
        <p>Selecione de 6 a 20 números e salve quantos jogos quiser.</p>
        
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 10px;">
            <span>Selecionados: <b id="selected-count" style="color: var(--accent-neon); font-size: 1.2rem;">0</b> / 60</span>
            <div>
                <button class="btn btn-secondary btn-sm" onclick="clearSelection()">Limpar</button>
                <button class="btn btn-info btn-sm" onclick="saveGame()" id="save-game-btn" style="display:none;">💾 Salvar Este Jogo</button>
            </div>
        </div>

        <div class="number-grid" id="custom-grid"></div>

        <div class="analysis-panel" id="analysis-panel" style="display: none;">
            <h3>🔍 Análise do Seu Jogo</h3>
            <div id="analysis-results"></div>
            <div id="game-cost-preview" style="margin-top: 15px; padding: 10px; background: var(--bg-primary); border-radius: 6px;"></div>
        </div>

        <div id="my-games-list" style="margin-top: 30px;"></div>

        <div class="export-info">
            <b>📤 Enviar para Ocelio:</b> Após montar todos os seus jogos, clique no botão abaixo para enviar online. Os jogos serão enviados diretamente para o Ocelio via GitHub.
        </div>

        <div style="display: flex; gap: 10px; flex-wrap: wrap; margin-top: 20px;">
            <button class="btn btn-purple" onclick="sendToOcelio()">🚀 Enviar para Ocelio (Online)</button>
            <button class="btn btn-info" onclick="exportGames()">💾 Exportar Backup (Arquivo)</button>
            <button class="btn btn-secondary" onclick="window.print()">🖨️ Imprimir Meus Jogos</button>
            <button class="btn btn-danger btn-sm" onclick="clearAllGames()">🗑️ Apagar Todos</button>
        </div>

        <div id="my-summary"></div>
    </div>

    <div id="tab-smart" class="tab-content">
        <h2>🧠 Fechamentos</h2>
        <div class="card">
            <h3>🤖 Gerador Estratégico</h3>
            <div class="input-group">
                <label>Quantidade:</label>
                <input type="number" id="qtd-games" value="5" min="1" max="20">
                <button class="btn" onclick="generateSmartGames()">Gerar</button>
            </div>
            <div id="smart-games-output"></div>
        </div>
        <div class="card">
            <h3>🔒 Fechamento Matemático</h3>
            <div class="input-group">
                <label>Números (8 a 10, separados por vírgula):</label>
                <input type="text" id="closure-input" style="width: 300px;" placeholder="Ex: 05, 10, 17, 20, 33, 34, 41, 58">
                <button class="btn" onclick="generateClosure()">Gerar</button>
            </div>
            <div id="closure-output"></div>
        </div>
    </div>
</div>

<script>
    const NEVER_DRAWN = [7, 8, 26, 28, 39, 44, 54, 60];
    const HOT_NUMBERS = [
        {num: 10, freq: 5}, {num: 33, freq: 5}, {num: 5, freq: 4},
        {num: 3, freq: 3}, {num: 17, freq: 3}, {num: 20, freq: 3}, 
        {num: 32, freq: 3}, {num: 34, freq: 3}, {num: 36, freq: 3}, 
        {num: 41, freq: 3}, {num: 56, freq: 3}, {num: 58, freq: 3}
    ];
    const PRICE_TABLE = {
        6: 6.00, 7: 42.00, 8: 168.00, 9: 504.00, 10: 1260.00,
        11: 2772.00, 12: 5544.00, 13: 10296.00, 14: 18018.00, 15: 30030.00,
        16: 48048.00, 17: 74256.00, 18: 111384.00, 19: 162792.00, 20: 232560.00
    };
    
    // Configuração do GitHub (vinda do administrador)
    const GITHUB_CONFIG = {
        token: '${githubToken}',
        gistId: '${gistId}',
        filename: '${gistFilename}'
    };

    function calculateGameCost(n) { return PRICE_TABLE[n] || 0; }
    function formatBRL(v) { return v.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }); }

    function showToast(msg, type='success') {
        const t = document.createElement('div');
        t.className = 'toast toast-' + type;
        t.textContent = msg;
        document.body.appendChild(t);
        setTimeout(() => t.remove(), 3000);
    }

    let myGames = [];
    let selectedNumbers = new Set();

    document.addEventListener('DOMContentLoaded', () => {
        try {
            myGames = JSON.parse(localStorage.getItem('my_mega_games') || '[]');
        } catch(e) { myGames = []; }
        
        renderStats();
        renderCustomGrid();
        renderMyGames();
        const savedName = localStorage.getItem('my_player_name') || '';
        document.getElementById('player-name').value = savedName;
        document.getElementById('print-date').textContent = new Date().toLocaleString('pt-BR');
        document.getElementById('print-player-name').textContent =
