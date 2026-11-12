<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mega da Virada 2026 - Sistema Completo</title>
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
        body { font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; background-color: var(--bg-primary); color: var(--text-primary); margin: 0; padding: 20px; line-height: 1.6; }
        .container { max-width: 1200px; margin: 0 auto; }
        header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid var(--accent-green); padding-bottom: 20px; }
        header h1 { color: var(--accent-neon); margin: 0; font-size: 2.5rem; text-shadow: 0 0 10px rgba(0, 255, 106, 0.3); }
        header p { color: var(--text-secondary); margin: 10px 0 0; }
        .tabs { display: flex; gap: 8px; margin-bottom: 20px; flex-wrap: wrap; }
        .tab-btn { padding: 10px 18px; background: var(--bg-secondary); border: 1px solid #333; color: var(--text-secondary); cursor: pointer; border-radius: 8px 8px 0 0; font-size: 0.95rem; font-weight: 600; transition: all 0.3s; }
        .tab-btn.active { background: var(--bg-card); color: var(--accent-neon); border-bottom: 2px solid var(--accent-neon); }
        .tab-content { display: none; background: var(--bg-card); padding: 30px; border-radius: 0 12px 12px 12px; border: 1px solid #333; animation: fadeIn 0.4s; }
        .tab-content.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-bottom: 30px; }
        .card { background: var(--bg-secondary); padding: 20px; border-radius: 10px; border-left: 4px solid var(--accent-green); }
        .card h3 { margin-top: 0; color: var(--accent-neon); font-size: 1.2rem; }
        .number-badge { display: inline-block; width: 40px; height: 40px; line-height: 40px; text-align: center; background: var(--bg-primary); border: 1px solid var(--accent-green); border-radius: 50%; margin: 4px; font-weight: bold; color: var(--accent-neon); }
        .number-badge.danger { border-color: var(--danger); color: var(--danger); }
        .number-grid { display: grid; grid-template-columns: repeat(10, 1fr); gap: 8px; margin: 20px 0; }
        .num-btn { aspect-ratio: 1; background: var(--bg-secondary); border: 1px solid #444; color: var(--text-primary); border-radius: 8px; cursor: pointer; font-size: 1.1rem; font-weight: bold; transition: all 0.2s; }
        .num-btn:hover { background: #333; transform: scale(1.05); }
        .num-btn.selected { background: var(--accent-green); color: white; border-color: var(--accent-neon); box-shadow: 0 0 10px rgba(0, 255, 106, 0.4); }
        .num-btn.never-drawn { background: rgba(239, 68, 68, 0.1); border-color: var(--danger); color: var(--danger); }
        .analysis-panel { background: var(--bg-secondary); padding: 20px; border-radius: 10px; margin-top: 20px; border: 1px solid #333; }
        .analysis-item { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #333; flex-wrap: wrap; gap: 10px; }
        .analysis-item:last-child { border-bottom: none; }
        .status-good { color: var(--accent-neon); font-weight: bold; }
        .status-warn { color: var(--warning); font-weight: bold; }
        .status-bad { color: var(--danger); font-weight: bold; }
        .btn { padding: 12px 24px; background: var(--accent-green); color: white; border: none; border-radius: 6px; cursor: pointer; font-size: 1rem; font-weight: bold; transition: all 0.2s; margin: 5px; }
        .btn:hover { background: #187a30; transform: translateY(-2px); }
        .btn-secondary { background: #333; border: 1px solid #555; }
        .btn-info { background: var(--info); }
        .btn-danger { background: var(--danger); }
        .btn-purple { background: var(--purple); }
        .btn-sm { padding: 6px 12px; font-size: 0.85rem; }
        .game-card { background: var(--bg-secondary); padding: 15px; border-radius: 8px; margin: 10px 0; display: flex; justify-content: space-between; align-items: center; border-left: 4px solid var(--accent-neon); flex-wrap: wrap; gap: 10px; }
        .game-numbers { font-size: 1.3rem; font-weight: bold; letter-spacing: 2px; }
        .game-tag { font-size: 0.8rem; background: rgba(0, 255, 106, 0.1); color: var(--accent-neon); padding: 4px 8px; border-radius: 4px; }
        .input-group { margin: 20px 0; display: flex; gap: 10px; align-items: center; flex-wrap: wrap; }
        input[type="number"], input[type="text"], input[type="password"], select { padding: 10px; background: var(--bg-primary); border: 1px solid #444; color: white; border-radius: 6px; font-size: 1rem; }
        input[type="number"] { width: 80px; }
        .saved-game { background: var(--bg-primary); padding: 12px 15px; border-radius: 6px; margin: 8px 0; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; }
        .saved-game-numbers { font-weight: bold; font-size: 1.1rem; letter-spacing: 1px; }
        .cost-tag { background: rgba(59, 130, 246, 0.15); color: var(--info); padding: 4px 10px; border-radius: 4px; font-weight: bold; }
        .summary-box { background: linear-gradient(135deg, rgba(32, 158, 63, 0.15), rgba(0, 255, 106, 0.05)); border: 2px solid var(--accent-green); padding: 25px; border-radius: 12px; margin-top: 30px; text-align: center; }
        .summary-box h2 { color: var(--accent-neon); margin-top: 0; }
        .summary-total { font-size: 2.5rem; font-weight: bold; color: var(--accent-neon); margin: 15px 0; text-shadow: 0 0 15px rgba(0, 255, 106, 0.4); }
        .summary-details { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; margin-top: 20px; }
        .summary-item { background: var(--bg-secondary); padding: 15px; border-radius: 8px; }
        .summary-item-label { color: var(--text-secondary); font-size: 0.9rem; margin-bottom: 5px; }
        .summary-item-value { font-size: 1.5rem; font-weight: bold; color: var(--accent-neon); }
        .empty-state { text-align: center; padding: 40px 20px; color: var(--text-secondary); }
        .empty-state-icon { font-size: 3rem; margin-bottom: 10px; }
        .modal-overlay { display: none; position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.8); z-index: 1000; justify-content: center; align-items: center; padding: 20px; }
        .modal-overlay.active { display: flex; }
        .modal { background: var(--bg-card); padding: 30px; border-radius: 12px; max-width: 500px; width: 100%; border: 1px solid #444; }
        .modal h3 { color: var(--accent-neon); margin-top: 0; }
        .modal input, .modal select { width: 100%; box-sizing: border-box; margin: 10px 0; }
        .info-box { background: rgba(59, 130, 246, 0.1); border-left: 4px solid var(--info); padding: 15px; border-radius: 6px; margin: 15px 0; color: var(--text-secondary); }
        .info-box b { color: var(--info); }
        .github-config { background: rgba(168, 85, 247, 0.1); border-left: 4px solid var(--purple); padding: 20px; border-radius: 8px; margin: 20px 0; }
        .github-config h3 { color: var(--purple); margin-top: 0; }
        .toast { position: fixed; top: 20px; right: 20px; padding: 15px 25px; border-radius: 8px; color: white; font-weight: bold; z-index: 2000; box-shadow: 0 4px 12px rgba(0,0,0,0.3); animation: slideIn 0.3s, fadeOut 0.3s 2.7s; max-width: 400px; }
        .toast-success { background: var(--accent-green); }
        .toast-error { background: var(--danger); }
        .toast-info { background: var(--info); }
        @keyframes slideIn { from { transform: translateX(400px); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
        @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; } }
        .price-table { width: 100%; border-collapse: collapse; margin-top: 15px; }
        .price-table th, .price-table td { padding: 10px; text-align: left; border-bottom: 1px solid #333; }
        .price-table th { background: var(--bg-primary); color: var(--accent-neon); }
        .price-table tr:hover { background: rgba(0, 255, 106, 0.05); }
        .disclaimer { margin-top: 30px; padding: 15px; background: rgba(245, 158, 11, 0.1); border-left: 4px solid var(--warning); color: var(--text-secondary); font-size: 0.9rem; border-radius: 4px; }
        @media (max-width: 600px) { .number-grid { grid-template-columns: repeat(6, 1fr); } header h1 { font-size: 1.8rem; } }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>🍀 Mega da Virada 2026</h1>
        <p>Sistema Completo - Administrador (Ocelio)</p>
    </header>

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
                <div id="hot-numbers"></div>
            </div>
            <div class="card" style="border-left-color: var(--danger);">
                <h3 style="color: var(--danger);">🚫 Números Nunca Sorteados</h3>
                <div id="cold-numbers"></div>
            </div>
            <div class="card">
                <h3>⚖️ Distribuição Pares / Ímpares</h3>
                <ul style="list-style: none; padding: 0;">
                    <li>3 Pares / 3 Ímpares: <b style="color: var(--accent-neon)">4
