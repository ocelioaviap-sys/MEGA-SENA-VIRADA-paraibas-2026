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
        <h2>💰 Gestão de Bolões</h2>
        <div style="display: flex; gap: 10px; margin: 20px 0; flex-wrap: wrap;">
            <button class="btn" onclick="openPlayerModal()">➕ Adicionar Jogador</button>
            <button class="btn btn-danger btn-sm" onclick="clearAllPools()" style="margin-left:auto;">🗑️ Limpar Tudo</button>
        </div>
        <div id="players-container"></div>
        <div id="summary-container"></div>
    </div>

    <!-- TAB 5: CONSOLIDAÇÃO -->
    <div id="tab-consolidation" class="tab-content">
        <h2>📥 Consolidação dos Jogos</h2>
        <div class="info-box">
            <b>📋 Como funciona:</b>
            <ol style="margin: 10px 0; padding-left: 20px;">
                <li>Configure o GitHub na aba "🐙 GitHub Online"</li>
                <li>Gere o HTML do jogador e envie para eles</li>
                <li>Eles montam os jogos e clicam em "Enviar para Ocelio"</li>
                <li>Clique em "🔄 Sincronizar do GitHub" para ver os jogos aqui</li>
            </ol>
        </div>
        <div style="display: flex; gap: 10px; margin: 20px 0; flex-wrap: wrap;">
            <button class="btn btn-purple" onclick="syncFromGitHub()">🔄 Sincronizar do GitHub</button>
            <button class="btn btn-danger btn-sm" onclick="clearConsolidation()">🗑️ Limpar Importações</button>
        </div>
        <div id="consolidation-container"></div>
        <div id="consolidation-summary"></div>
    </div>

    <!-- TAB 6: GITHUB CONFIG -->
    <div id="tab-github" class="tab-content">
        <h2>🐙 Configuração GitHub</h2>
        <div class="github-config">
            <h3>🔑 Configuração do GitHub</h3>
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
            </div>
            <div id="github-status" style="margin-top: 20px;"></div>
        </div>
    </div>

    <!-- TAB 7: GERADOR HTML JOGADOR -->
    <div id="tab-generator" class="tab-content">
        <h2>⚙️ Gerar HTML para Jogadores</h2>
        <div class="card" style="margin: 20px 0;">
            <h3>📄 HTML do Jogador</h3>
            <p>Este arquivo contém o essencial para o jogador montar jogos e enviar online.</p>
            <button class="btn btn-purple" onclick="downloadPlayerHTML()">📥 Baixar HTML do Jogador</button>
        </div>
    </div>

    <!-- TAB 8: TABELA DE PREÇOS -->
    <div id="tab-prices" class="tab-content">
        <h2>💵 Tabela Oficial de Preços - Mega-Sena (2026)</h2>
        <table class="price-table">
            <thead><tr><th>Números</th><th>Combinações</th><th>Valor da Aposta</th></tr></thead>
            <tbody id="price-table-body"></tbody>
        </table>
    </div>

    <div class="disclaimer">
        <b>⚠️ Aviso Importante:</b> Loteria é um jogo de azar. Análises estatísticas e fechamentos organizam o jogo, mas <b>não garantem premiação</b>.
    </div>
</div>

<!-- MODAL: ADICIONAR JOGADOR -->
<div class="modal-overlay" id="player-modal">
    <div class="modal">
        <h3>➕ Novo Jogador</h3>
        <input type="text" id="player-name-input" placeholder="Nome do jogador">
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
        <select id="save-player-select" style="width: 100%; margin: 10px 0;"></select>
        <input type="text" id="game-obs-input" placeholder="Observação (opcional)" style="width: 100%; margin: 10px 0;">
        <div style="display: flex; gap: 10px; justify-content: flex-end; margin-top: 15px;">
            <button class="btn btn-secondary" onclick="closeSaveModal()">Cancelar</button>
            <button class="btn" onclick="confirmSaveGame()">Salvar</button>
        </div>
    </div>
</div>

<script>
    // --- DADOS ---
    const NEVER_DRAWN = [7, 8, 26, 28, 39, 44, 54, 60];
    const HOT_NUMBERS = [{num: 10, freq: 5}, {num: 33, freq: 5}, {num: 5, freq: 4}, {num: 3, freq: 3}, {num: 17, freq: 3}, {num: 20, freq: 3}, {num: 32, freq: 3}, {num: 34, freq: 3}, {num: 36, freq: 3}, {num: 41, freq: 3}, {num: 56, freq: 3}, {num: 58, freq: 3}];
    const PRICE_TABLE = {6: 6.00, 7: 42.00, 8: 168.00, 9: 504.00, 10: 1260.00, 11: 2772.00, 12: 5544.00, 13: 10296.00, 14: 18018.00, 15: 30030.00, 16: 48048.00, 17: 74256.00, 18: 111384.00, 19: 162792.00, 20: 232560.00};

    function calculateGameCost(n) { return PRICE_TABLE[n] || 0; }
    function formatBRL(value) { return value.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }); }

    let players = JSON.parse(localStorage.getItem('mega_players') || '[]');
    let importedPlayers = JSON.parse(localStorage.getItem('mega_imported') || '[]');
    let selectedNumbers = new Set();
    let githubConfig = JSON.parse(localStorage.getItem('github_config') || '{}');

    function showToast(message, type = 'success') {
        const toast = document.createElement('div');
        toast.className = 'toast toast-' + type;
        toast.textContent = message;
        document.body.appendChild(toast);
        setTimeout(() => toast.remove(), 3000);
    }

    function savePlayers() { localStorage.setItem('mega_players', JSON.stringify(players)); }
    function saveImported() { localStorage.setItem('mega_imported', JSON.stringify(importedPlayers)); }

    // --- GITHUB ---
    function saveGitHubConfig() {
        githubConfig = {
            token: document.getElementById('github-token').value.trim(),
            gistId: document.getElementById('gist-id').value.trim(),
            filename: document.getElementById('gist-filename').value.trim() || 'mega_virada_2026.json'
        };
        localStorage.setItem('github_config', JSON.stringify(githubConfig));
        showToast('✅ Configuração salva!', 'success');
        updateGitHubStatus();
    }

    function updateGitHubStatus() {
        const statusEl = document.getElementById('github-status');
        if (githubConfig.token && githubConfig.gistId) {
            statusEl.innerHTML = '<div class="info-box" style="border-left-color: var(--accent-green);"><b style="color: var(--accent-green);">✅ GitHub configurado</b><br>Gist ID: <code>' + githubConfig.gistId.substring(0, 8) + '...</code></div>';
        } else {
            statusEl.innerHTML = '<div class="info-box" style="border-left-color: var(--warning);"><b style="color: var(--warning);">⚠️ GitHub não configurado</b></div>';
        }
    }

    async function testGitHubConnection() {
        if (!githubConfig.token || !githubConfig.gistId) return showToast('Configure o GitHub primeiro!', 'error');
        try {
            const res = await fetch('https://api.github.com/gists/' + githubConfig.gistId, { headers: { 'Authorization': 'token ' + githubConfig.token, 'Accept': 'application/vnd.github.v3+json' } });
            showToast(res.ok ? '✅ Conexão funcionando!' : '❌ Erro na conexão', res.ok ? 'success' : 'error');
        } catch (e) { showToast('❌ Erro de rede', 'error'); }
    }

    async function syncFromGitHub() {
        if (!githubConfig.token || !githubConfig.gistId) return showToast('Configure o GitHub primeiro!', 'error');
        showToast('🔄 Sincronizando...', 'info');
        try {
            const res = await fetch('https://api.github.com/gists/' + githubConfig.gistId, { headers: { 'Authorization': 'token ' + githubConfig.token, 'Accept': 'application/vnd.github.v3+json' } });
            if (!res.ok) throw new Error('Erro na API');
            const gist = await res.json();
            const file = gist.files[githubConfig.filename];
            if (!file) throw new Error('Arquivo não encontrado');
            const data = JSON.parse(file.content);
            if (data.players && Array.isArray(data.players)) {
                importedPlayers = data.players;
                saveImported();
                renderConsolidation();
                showToast('✅ Sincronizado com sucesso!', 'success');
            }
        } catch (e) { showToast('❌ Erro ao sincronizar: ' + e.message, 'error'); }
    }

    // --- INICIALIZAÇÃO ---
    document.addEventListener('DOMContentLoaded', function() {
        renderStats();
        renderCustomGrid();
        renderPlayers();
        renderConsolidation();
        renderPriceTable();
        if (githubConfig.token) document.getElementById('github-token').value = githubConfig.token;
        if (githubConfig.gistId) document.getElementById('gist-id').value = githubConfig.gistId;
        if (githubConfig.filename) document.getElementById('gist-filename').value = githubConfig.filename;
        updateGitHubStatus();
    });

    function openTab(evt, tabName) {
        document.querySelectorAll('.tab-content').forEach(function(tab) { tab.classList.remove('active'); });
        document.querySelectorAll('.tab-btn').forEach(function(btn) { btn.classList.remove('active'); });
        document.getElementById(tabName).classList.add('active');
        evt.currentTarget.classList.add('active');
        if (tabName === 'tab-pools') renderPlayers();
        if (tabName === 'tab-consolidation') renderConsolidation();
        if (tabName === 'tab-github') updateGitHubStatus();
    }

    function renderStats() {
        const hotContainer = document.getElementById('hot-numbers');
        HOT_NUMBERS.forEach(function(h) { hotContainer.innerHTML += '<span class="number-badge" title="Sorteado ' + h.freq + 'x">' + String(h.num).padStart(2, '0') + '</span>'; });
        const coldContainer = document.getElementById('cold-numbers');
        NEVER_DRAWN.forEach(function(n) { coldContainer.innerHTML += '<span class="number-badge danger" title="Nunca sorteado">' + String(n).padStart(2, '0') + '</span>'; });
    }

    function renderCustomGrid() {
        const grid = document.getElementById('custom-grid');
        for (let i = 1; i <= 60; i++) {
            const btn = document.createElement('button');
            btn.className = 'num-btn';
            btn.textContent = String(i).padStart(2, '0');
            if (NEVER_DRAWN.includes(i)) btn.classList.add('never-drawn');
            btn.onclick = (function(num, button) {
                return function() {
                    if (selectedNumbers.has(num)) { selectedNumbers.delete(num); button.classList.remove('selected'); }
                    else { selectedNumbers.add(num); button.classList.add('selected'); }
                    updateAnalysis();
                };
            })(i, btn);
            grid.appendChild(btn);
        }
    }

    function clearSelection() {
        selectedNumbers.clear();
        document.querySelectorAll('.num-btn').forEach(function(b) { b.classList.remove('selected'); });
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
        const evens = nums.filter(function(n) { return n % 2 === 0; }).length;
        const odds = count - evens;
        const hotHits = nums.filter(function(n) { return HOT_NUMBERS.some(function(h) { return h.num === n; }); }).length;
        const coldHits = nums.filter(function(n) { return NEVER_DRAWN.includes(n); }).length;

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
        let coldText = coldHits === 0 ? 'Nenhum número "frio" histórico incluído.' : 'Atenção: ' + coldHits + ' número(s) NUNCA sorteado(s) na Virada.';

        results.innerHTML = 
            '<div class="analysis-item"><span>Equilíbrio Par/Ímpar (' + evens + 'P / ' + odds + 'I):</span><span class="' + parImparStatus + '">' + parImparText + '</span></div>' +
            '<div class="analysis-item"><span>Números Mais Frequentes (' + hotHits + '):</span><span class="' + (hotHits >= 2 ? 'status-good' : 'status-warn') + '">' + hotHits + ' dezenas do Top 12 histórico.</span></div>' +
            '<div class="analysis-item"><span>Números "Frios":</span><span class="' + coldStatus + '">' + coldText + '</span></div>' +
            '<div class="analysis-item"><span>Soma das Dezenas:</span><span>' + nums.reduce(function(a, b) { return a + b; }, 0) + '</span></div>';

        costPreview.innerHTML = '<div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px;"><span>💵 Custo desta aposta (' + count + ' dezenas):</span><span style="color: var(--accent-neon); font-size: 1.3rem; font-weight: bold;">' + formatBRL(calculateGameCost(count)) + '</span></div>';
    }

    function generateSmartGames() {
        const qtd = parseInt(document.getElementById('qtd-games').value);
        const output = document.getElementById('smart-games-output');
        output.innerHTML = '';
        let pool = [];
        for(let i=1; i<=60; i++) {
            if(!NEVER_DRAWN.includes(i)) {
                let weight = HOT_NUMBERS.some(function(h) { return h.num === i; }) ? 3 : 1;
                for(let w=0; w<weight; w++) pool.push(i);
            }
        }
        for(let g=0; g<qtd; g++) {
            let game = new Set();
            let attempts = 0;
            while(game.size < 6 && attempts < 100) { game.add(pool[Math.floor(Math.random() * pool.length)]); attempts++; }
            let gameArr = Array.from(game).sort(function(a, b) { return a - b; });
            let evens = gameArr.filter(function(n) { return n % 2 === 0; }).length;
            if(!(evens===3 || evens===4 || evens===2)) { g--; continue; }
            const gameStr = gameArr.map(function(n) { return String(n).padStart(2, '0'); }).join(' - ');
            output.innerHTML += '<div class="game-card"><span class="game-numbers">' + gameStr + '</span><span class="game-tag">Estratégico ' + evens + 'P/' + (6-evens) + 'I - ' + formatBRL(6.00) + '</span></div>';
        }
    }

    function generateClosure() {
        const input = document.getElementById('closure-input').value;
        const output = document.getElementById('closure-output');
        const nums = input.match(/\d+/g);
        if (!nums) { output.innerHTML = '<p style="color: var(--danger);">Insira os números separados por vírgula.</p>'; return; }
        const uniqueNums = Array.from(new Set(nums.map(Number))).filter(function(n) { return n >= 1 && n <= 60; }).sort(function(a,b) { return a-b; });
        if (uniqueNums.length < 8 || uniqueNums.length > 10) { output.innerHTML = '<p style="color: var(--danger);">O fechamento exige entre 8 e 10 números. Você inseriu ' + uniqueNums.length + '.</p>'; return; }
        
        const combinations = [];
        function combine(start, combo) {
            if (combo.length === 6) { combinations.push(combo.slice()); return; }
            for (let i = start; i < uniqueNums.length; i++) {
                combo.push(uniqueNums[i]);
                combine(i + 1, combo);
                combo.pop();
            }
        }
        combine(0, []);
        
        const totalCost = combinations.length * 6.00;
        let html = '<p style="color: var(--accent-neon); margin-top: 15px;">Fechamento gerado! <b>' + combinations.length + ' jogos</b> | Custo total: <b>' + formatBRL(totalCost) + '</b></p>';
        combinations.forEach(function(combo, index) {
            const str = combo.map(function(n) { return String(n).padStart(2, '0'); }).join(' - ');
            html += '<div class="game-card"><span class="game-numbers">' + str + '</span><span class="game-tag">Jogo ' + (index + 1) + ' - ' + formatBRL(6.00) + '</span></div>';
        });
        output.innerHTML = html;
    }

    function openPlayerModal() { document.getElementById('player-modal').classList.add('active'); document.getElementById('player-name-input').value = ''; document.getElementById('player-name-input').focus(); }
    function closePlayerModal() { document.getElementById('player-modal').classList.remove('active'); }
    function addPlayer() {
        const name = document.getElementById('player-name-input').value.trim();
        if (!name) { alert('Digite o nome do jogador!'); return; }
        players.push({ id: Date.now(), name: name, games: [] });
        savePlayers();
        closePlayerModal();
        renderPlayers();
        showToast('✅ Jogador adicionado!', 'success');
    }
    function removePlayer(id) {
        if (!confirm('Remover este jogador e todos os seus jogos?')) return;
        players = players.filter(function(p) { return p.id !== id; });
        savePlayers();
        renderPlayers();
    }
    function removeGame(playerId, gameIndex) {
        if (!confirm('Remover este jogo?')) return;
        const player = players.find(function(p) { return p.id === playerId; });
        player.games.splice(gameIndex, 1);
        savePlayers();
        renderPlayers();
    }
    function openSaveModal() {
        if (players.length === 0) { alert('Crie pelo menos um jogador na aba "Meus Bolões" primeiro!'); return; }
        const select = document.getElementById('save-player-select');
        select.innerHTML = players.map(function(p) { return '<option value="' + p.id + '">' + p.name + '</option>'; }).join('');
        document.getElementById('game-obs-input').value = '';
        document.getElementById('save-modal').classList.add('active');
    }
    function closeSaveModal() { document.getElementById('save-modal').classList.remove('active'); }
    function confirmSaveGame() {
        const playerId = parseInt(document.getElementById('save-player-select').value);
        const obs = document.getElementById('game-obs-input').value.trim();
        const player = players.find(function(p) { return p.id === playerId; });
        if (!player) return;
        const nums = Array.from(selectedNumbers).sort(function(a, b) { return a - b; });
        player.games.push({ numbers: nums, obs: obs || 'Jogo ' + (player.games.length + 1), cost: calculateGameCost(nums.length), createdAt: new Date().toLocaleString('pt-BR') });
        savePlayers();
        closeSaveModal();
        showToast('✅ Jogo salvo para ' + player.name + '!', 'success');
        clearSelection();
    }
    function renderPlayers() {
        const container = document.getElementById('players-container');
        const summaryContainer = document.getElementById('summary-container');
        if (players.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="empty-state-icon">🎲</div><h3>Nenhum jogador cadastrado</h3></div>';
            summaryContainer.innerHTML = '';
            return;
        }
        let totalGames = 0, totalCost = 0, html = '';
        players.forEach(function(player) {
            const playerCost = player.games.reduce(function(sum, g) { return sum + g.cost; }, 0);
            totalGames += player.games.length;
            totalCost += playerCost;
            html += '<div class="card" style="margin-bottom: 15px;"><div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 10px;"><h3 style="margin:0; color: var(--accent-neon);">👤 ' + player.name + '</h3><div><button class="btn btn-sm btn-secondary" onclick="addQuickGame(' + player.id + ')">➕ Jogo Rápido</button> <button class="btn btn-sm btn-danger" onclick="removePlayer(' + player.id + ')">🗑️</button></div></div><div style="color: var(--text-secondary); margin-bottom: 10px;">🎯 Jogos: <b style="color: var(--accent-neon);">' + player.games.length + '</b> | 💵 Total: <b style="color: var(--accent-neon);">' + formatBRL(playerCost) + '</b></div>';
            player.games.forEach(function(game, idx) {
                html += '<div class="saved-game"><div><div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 3px;">' + game.obs + '</div><div class="saved-game-numbers">' + game.numbers.map(function(n) { return String(n).padStart(2, '0'); }).join(' - ') + '</div></div><div style="display: flex; gap: 10px; align-items: center;"><span style="color: var(--text-secondary); font-size: 0.85rem;">' + game.numbers.length + ' dezenas</span><span class="cost-tag">' + formatBRL(game.cost) + '</span><button class="btn btn-sm btn-danger" onclick="removeGame(' + player.id + ', ' + idx + ')">✕</button></div></div>';
            });
            html += '</div>';
        });
        container.innerHTML = html;
        summaryContainer.innerHTML = '<div class="summary-box"><h2>📊 Resumo Geral do Bolão</h2><div class="summary-total">' + formatBRL(totalCost) + '</div><div class="summary-details"><div class="summary-item"><div class="summary-item-label">Total de Jogadores</div><div class="summary-item-value">' + players.length + '</div></div><div class="summary-item"><div class="summary-item-label">Total de Jogos</div><div class="summary-item-value">' + totalGames + '</div></div></div></div>';
    }
    function addQuickGame(playerId) {
        const player = players.find(function(p) { return p.id === playerId; });
        if (!player) return;
        let nums = new Set();
        let pool = [];
        for(let i=1; i<=60; i++) {
            if(!NEVER_DRAWN.includes(i)) {
                let weight = HOT_NUMBERS.some(function(h) { return h.num === i; }) ? 3 : 1;
                for(let w=0; w<weight; w++) pool.push(i);
            }
        }
        while(nums.size < 6) nums.add(pool[Math.floor(Math.random() * pool.length)]);
        const sortedNums = Array.from(nums).sort(function(a,b) { return a-b; });
        player.games.push({ numbers: sortedNums, obs: 'Jogo ' + (player.games.length + 1), cost: 6.00, createdAt: new Date().toLocaleString('pt-BR') });
        savePlayers();
        renderPlayers();
    }
    function clearAllPools() {
        if (!confirm('⚠️ Apagar TODOS os jogadores e jogos?')) return;
        players = [];
        savePlayers();
        renderPlayers();
    }
    function clearConsolidation() {
        if (!confirm('⚠️ Apagar TODAS as importações?')) return;
        importedPlayers = [];
        saveImported();
        renderConsolidation();
    }
    function renderConsolidation() {
        const container = document.getElementById('consolidation-container');
        const summaryContainer = document.getElementById('consolidation-summary');
        if (importedPlayers.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="empty-state-icon">📭</div><h3>Nenhum jogador importado ainda</h3><p>Sincronize do GitHub ou importe arquivos JSON.</p></div>';
            summaryContainer.innerHTML = '';
            return;
        }
        let totalGames = 0, totalCost = 0, html = '';
        importedPlayers.forEach(function(player, index) {
            const playerCost = player.games.reduce(function(sum, g) { return sum + g.cost; }, 0);
            totalGames += player.games.length;
            totalCost += playerCost;
            html += '<div class="card" style="margin-bottom: 15px; border-left-color: var(--purple);"><div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 10px;"><h3 style="margin:0; color: var(--purple);">👤 ' + player.playerName + '</h3><button class="btn btn-sm btn-danger" onclick="removeImported(' + index + ')">🗑️</button></div><div style="color: var(--text-secondary); margin-bottom: 10px;">🎯 Jogos: <b style="color: var(--accent-neon);">' + player.games.length + '</b> | 💵 Total: <b style="color: var(--accent-neon);">' + formatBRL(playerCost) + '</b>' + (player.exportDate ? ' | 📅 ' + player.exportDate : '') + '</div>';
            player.games.forEach(function(game, idx) {
                html += '<div class="saved-game"><div><div style="font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 3px;">' + (game.obs || 'Jogo ' + (idx + 1)) + '</div><div class="saved-game-numbers">' + game.numbers.map(function(n) { return String(n).padStart(2, '0'); }).join(' - ') + '</div></div><div style="display: flex; gap: 10px; align-items: center;"><span style="color: var(--text-secondary); font-size: 0.85rem;">' + game.numbers.length + ' dezenas</span><span class="cost-tag">' + formatBRL(game.cost) + '</span></div></div>';
            });
            html += '</div>';
        });
        container.innerHTML = html;
        summaryContainer.innerHTML = '<div class="summary-box"><h2>📊 Consolidação Geral</h2><div class="summary-total">' + formatBRL(totalCost) + '</div><div class="summary-details"><div class="summary-item"><div class="summary-item-label">Jogadores</div><div class="summary-item-value">' + importedPlayers.length + '</div></div><div class="summary-item"><div class="summary-item-label">Total de Jogos</div><div class="summary-item-value">' + totalGames + '</div></div></div></div>';
    }
    function removeImported(index) {
        if (!confirm('Remover este jogador da consolidação?')) return;
        importedPlayers.splice(index, 1);
        saveImported();
        renderConsolidation();
    }

    function renderPriceTable() {
        const tbody = document.getElementById('price-table-body');
        let html = '';
        for (let n = 6; n <= 20; n++) {
            let c = 1;
            for (let i = 0; i < 6; i++) { c = c * (n - i) / (i + 1); }
            const combinations = Math.round(c);
            html += '<tr><td><b style="color: var(--accent-neon);">' + n + '</b> números</td><td>' + combinations.toLocaleString('pt-BR') + '</td><td><b style="color: var(--accent-neon);">' + formatBRL(PRICE_TABLE[n]) + '</b></td></tr>';
        }
        tbody.innerHTML = html;
    }

    // --- GERADOR DE HTML DO JOGADOR (100% SEGURO, SEM TEMPLATES ANINHADOS) ---
    function downloadPlayerHTML() {
        const token = githubConfig.token || '';
        const gistId = githubConfig.gistId || '';
        const filename = githubConfig.filename || 'mega_virada_2026.json';

        // Usamos um template simples com placeholders para evitar QUALQUER erro de sintaxe
        let html = `<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mega da Virada 2026 - Meus Jogos</title>
    <style>
        body { font-family: 'Segoe UI', sans-serif; background: #0f1115; color: #e2e8f0; margin: 0; padding: 20px; }
        .container { max-width: 800px; margin: 0 auto; }
        header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #209e3f; padding-bottom: 20px; }
        header h1 { color: #00ff6a; margin: 0; }
        .tabs { display: flex; gap: 8px; margin-bottom: 20px; flex-wrap: wrap; }
        .tab-btn { padding: 10px 18px; background: #1a1d24; border: 1px solid #333; color: #94a3b8; cursor: pointer; border-radius: 8px 8px 0 0; font-weight: 600; }
        .tab-btn.active { background: #222630; color: #00ff6a; border-bottom: 2px solid #00ff6a; }
        .tab-content { display: none; background: #222630; padding: 25px; border-radius: 0 12px 12px 12px; border: 1px solid #333; }
        .tab-content.active { display: block; }
        .number-grid { display: grid; grid-template-columns: repeat(10, 1fr); gap: 8px; margin: 20px 0; }
        .num-btn { aspect-ratio: 1; background: #1a1d24; border: 1px solid #444; color: #e2e8f0; border-radius: 8px; cursor: pointer; font-size: 1.1rem; font-weight: bold; }
        .num-btn.selected { background: #209e3f; color: white; border-color: #00ff6a; }
        .num-btn.never-drawn { background: rgba(239, 68, 68, 0.1); border-color: #ef4444; color: #ef4444; }
        .btn { padding: 12px 24px; background: #209e3f; color: white; border: none; border-radius: 6px; cursor: pointer; font-size: 1rem; font-weight: bold; margin: 5px; }
        .btn:hover { background: #187a30; }
        .btn-secondary { background: #333; border: 1px solid #555; }
        .btn-info { background: #3b82f6; }
        .btn-danger { background: #ef4444; }
        .btn-purple { background: #a855f7; }
        .saved-game { background: #0f1115; padding: 12px 15px; border-radius: 6px; margin: 8px 0; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; }
        .saved-game-numbers { font-weight: bold; font-size: 1.1rem; letter-spacing: 1px; }
        .cost-tag { background: rgba(59, 130, 246, 0.15); color: #3b82f6; padding: 4px 10px; border-radius: 4px; font-weight: bold; }
        .summary-box { background: linear-gradient(135deg, rgba(32, 158, 63, 0.15), rgba(0, 255, 106, 0.05)); border: 2px solid #209e3f; padding: 25px; border-radius: 12px; margin-top: 30px; text-align: center; }
        .summary-total { font-size: 2.5rem; font-weight: bold; color: #00ff6a; margin: 15px 0; }
        .player-name-input { padding: 12px; background: #0f1115; border: 2px solid #00ff6a; color: #00ff6a; border-radius: 6px; font-size: 1.1rem; font-weight: bold; width: 100%; max-width: 400px; box-sizing: border-box; margin-bottom: 20px; }
        .toast { position: fixed; top: 20px; right: 20px; padding: 15px 25px; border-radius: 8px; color: white; font-weight: bold; z-index: 2000; }
        .toast-success { background: #209e3f; }
        .toast-error { background: #ef4444; }
        @media (max-width: 600px) { .number-grid { grid-template-columns: repeat(6, 1fr); } }
    </style>
</head>
<body>
<div class="container">
    <header><h1>🍀 Mega da Virada 2026</h1><p>Monte seus jogos e envie para o Ocelio!</p></header>
    <input type="text" id="player-name" class="player-name-input" placeholder="👤 Digite seu nome aqui" onchange="savePlayerName()">
    <div class="tabs">
        <button class="tab-btn active" onclick="openTab(event, 'tab-mygames')">🎯 Meus Jogos</button>
        <button class="tab-btn" onclick="openTab(event, 'tab-smart')">🧠 Fechamentos</button>
    </div>
    <div id="tab-mygames" class="tab-content active">
        <h2>🎯 Monte Seus Jogos</h2>
        <p>Selecione de 6 a 20 números. Números em vermelho nunca saíram na Virada.</p>
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
            <span>Selecionados: <b id="selected-count" style="color: #00ff6a; font-size: 1.2rem;">0</b> / 60</span>
            <div>
                <button class="btn btn-secondary" onclick="clearSelection()" style="padding: 6px 12px; font-size: 0.85rem;">Limpar</button>
                <button class="btn btn-info" onclick="saveGame()" id="save-game-btn" style="display:none; padding: 6px 12px; font-size: 0.85rem;">💾 Salvar Este Jogo</button>
            </div>
        </div>
        <div class="number-grid" id="custom-grid"></div>
        <div id="analysis-panel" style="display: none; background: #1a1d24; padding: 20px; border-radius: 10px; margin-top: 20px; border: 1px solid #333;">
            <h3>🔍 Análise do Seu Jogo</h3>
            <div id="analysis-results"></div>
            <div id="game-cost-preview" style="margin-top: 15px; padding: 10px; background: #0f1115; border-radius: 6px;"></div>
        </div>
        <div id="my-games-list" style="margin-top: 30px;"></div>
        <div style="background: rgba(168, 85, 247, 0.1); border-left: 4px solid #a855f7; padding: 15px; border-radius: 6px; margin: 20px 0; color: #94a3b8;">
            <b style="color: #a855f7;">📤 Enviar para Ocelio:</b> Após montar todos os seus jogos, clique no botão abaixo para enviar online.
        </div>
        <div style="display: flex; gap: 10px; flex-wrap: wrap; margin-top: 20px;">
            <button class="btn btn-purple" onclick="sendToOcelio()">🚀 Enviar para Ocelio (Online)</button>
            <button class="btn btn-info" onclick="exportGames()">💾 Exportar Backup (Arquivo)</button>
            <button class="btn btn-danger" onclick="clearAllGames()" style="padding: 6px 12px; font-size: 0.85rem;">🗑️ Apagar Todos</button>
        </div>
        <div id="my-summary"></div>
    </div>
    <div id="tab-smart" class="tab-content">
        <h2>🧠 Fechamentos</h2>
        <div style="background: #1a1d24; padding: 20px; border-radius: 10px; border-left: 4px solid #209e3f; margin-bottom: 15px;">
            <h3 style="margin-top:0; color: #00ff6a;">🤖 Gerador Estratégico</h3>
            <div style="display: flex; gap: 10px; align-items: center; flex-wrap: wrap; margin: 20px 0;">
                <label>Quantidade:</label>
                <input type="number" id="qtd-games" value="5" min="1" max="20" style="padding: 10px; background: #0f1115; border: 1px solid #444; color: white; border-radius: 6px; width: 80px;">
                <button class="btn" onclick="generateSmartGames()">Gerar</button>
            </div>
            <div id="smart-games-output"></div>
        </div>
    </div>
</div>

<script>
    const NEVER_DRAWN = [7, 8, 26, 28, 39, 44, 54, 60];
    const HOT_NUMBERS = [{num: 10, freq: 5}, {num: 33, freq: 5}, {num: 5, freq: 4}, {num: 3, freq: 3}, {num: 17, freq: 3}, {num: 20, freq: 3}, {num: 32, freq: 3}, {num: 34, freq: 3}, {num: 36, freq: 3}, {num: 41, freq: 3}, {num: 56, freq: 3}, {num: 58, freq: 3}];
    const PRICE_TABLE = {6: 6.00, 7: 42.00, 8: 168.00, 9: 504.00, 10: 1260.00, 11: 2772.00, 12: 5544.00, 13: 10296.00, 14: 18018.00, 15: 30030.00, 16: 48048.00, 17: 74256.00, 18: 111384.00, 19: 162792.00, 20: 232560.00};
    
    const GITHUB_CONFIG = {
        token: '__GITHUB_TOKEN__',
        gistId: '__GIST_ID__',
        filename: '__GIST_FILENAME__'
    };

    function calculateGameCost(n) { return PRICE_TABLE[n] || 0; }
    function formatBRL(v) { return v.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }); }

    function showToast(msg, type) {
        const t = document.createElement('div');
        t.className = 'toast toast-' + (type || 'success');
        t.textContent = msg;
        document.body.appendChild(t);
        setTimeout(function() { t.remove(); }, 3000);
    }

    let myGames = [];
    let selectedNumbers = new Set();

    document.addEventListener('DOMContentLoaded', function() {
        try { myGames = JSON.parse(localStorage.getItem('my_mega_games') || '[]'); } catch(e) { myGames = []; }
        renderCustomGrid();
        renderMyGames();
        const savedName = localStorage.getItem('my_player_name') || '';
        document.getElementById('player-name').value = savedName;
    });

    function savePlayerName() {
        const name = document.getElementById('player-name').value.trim();
        localStorage.setItem('my_player_name', name);
    }

    function openTab(evt, tabName) {
        document.querySelectorAll('.tab-content').forEach(function(tab) { tab.classList.remove('active'); });
        document.querySelectorAll('.tab-btn').forEach(function(btn) { btn.classList.remove('active'); });
        document.getElementById(tabName).classList.add('active');
        evt.currentTarget.classList.add('active');
    }

    function renderCustomGrid() {
        const grid = document.getElementById('custom-grid');
        for (let i = 1; i <= 60; i++) {
            const btn = document.createElement('button');
            btn.className = 'num-btn';
            btn.textContent = String(i).padStart(2, '0');
            if (NEVER_DRAWN.includes(i)) btn.classList.add('never-drawn');
            btn.onclick = (function(num, button) {
                return function() {
                    if (selectedNumbers.has(num)) { selectedNumbers.delete(num); button.classList.remove('selected'); }
                    else { selectedNumbers.add(num); button.classList.add('selected'); }
                    updateAnalysis();
                };
            })(i, btn);
            grid.appendChild(btn);
        }
    }

    function clearSelection() {
        selectedNumbers.clear();
        document.querySelectorAll('.num-btn').forEach(function(b) { b.classList.remove('selected'); });
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
        const evens = nums.filter(function(n) { return n % 2 === 0; }).length;
        const odds = count - evens;
        const hotHits = nums.filter(function(n) { return HOT_NUMBERS.some(function(h) { return h.num === n; }); }).length;
        const coldHits = nums.filter(function(n) { return NEVER_DRAWN.includes(n); }).length;

        let parImparStatus = 'status-bad';
        let parImparText = 'Desequilibrado';
        if ((evens === 3 && odds === 3) || (evens === 4 && odds === 2) || (evens === 2 && odds === 4)) {
            parImparStatus = 'status-good';
            parImparText = 'Excelente (88% dos sorteios)';
        } else if ((evens === 1 && odds === 5) || (evens === 5 && odds === 1)) {
            parImparStatus = 'status-warn';
            parImparText = 'Aceitável (11,8%)';
        }

        results.innerHTML = 
            '<div style="display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #333;"><span>Par/Ímpar (' + evens + 'P / ' + odds + 'I):</span><span style="color: ' + (parImparStatus === 'status-good' ? '#00ff6a' : (parImparStatus === 'status-warn' ? '#f59e0b' : '#ef4444')) + '; font-weight: bold;">' + parImparText + '</span></div>' +
            '<div style="display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #333;"><span>Mais Frequentes:</span><span style="color: ' + (hotHits >= 2 ? '#00ff6a' : '#f59e0b') + '; font-weight: bold;">' + hotHits + ' no Top 12</span></div>' +
            '<div style="display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #333;"><span>Números "Frios":</span><span style="color: ' + (coldHits === 0 ? '#00ff6a' : '#ef4444') + '; font-weight: bold;">' + (coldHits === 0 ? 'Nenhum' : coldHits + ' nunca sorteado(s)') + '</span></div>' +
            '<div style="display: flex; justify-content: space-between; padding: 10px 0;"><span>Soma:</span><span>' + nums.reduce(function(a, b) { return a + b; }, 0) + '</span></div>';

        costPreview.innerHTML = '<div style="display: flex; justify-content: space-between; align-items: center;"><span>💵 Custo (' + count + ' dezenas):</span><span style="color: #00ff6a; font-size: 1.3rem; font-weight: bold;">' + formatBRL(calculateGameCost(count)) + '</span></div>';
    }

    function saveGame() {
        const name = document.getElementById('player-name').value.trim();
        if (!name) { alert('Por favor, digite seu nome no topo da página antes de salvar!'); return; }
        const obs = prompt('Observação para este jogo (opcional):', 'Jogo ' + (myGames.length + 1));
        if (obs === null) return;
        const nums = Array.from(selectedNumbers).sort(function(a, b) { return a - b; });
        myGames.push({ numbers: nums, obs: obs || 'Jogo ' + (myGames.length + 1), cost: calculateGameCost(nums.length) });
        try {
            localStorage.setItem('my_mega_games', JSON.stringify(myGames));
            showToast('✅ Jogo salvo!', 'success');
        } catch(e) { showToast('❌ Erro ao salvar', 'error'); }
        clearSelection();
        renderMyGames();
    }

    function removeGame(idx) {
        if (!confirm('Remover este jogo?')) return;
        myGames.splice(idx, 1);
        localStorage.setItem('my_mega_games', JSON.stringify(myGames));
        renderMyGames();
    }

    function clearAllGames() {
        if (!confirm('⚠️ Apagar TODOS os seus jogos?')) return;
        myGames = [];
        localStorage.setItem('my_mega_games', JSON.stringify(myGames));
        renderMyGames();
    }

    function renderMyGames() {
        const container = document.getElementById('my-games-list');
        const summaryContainer = document.getElementById('my-summary');
        if (myGames.length === 0) {
            container.innerHTML = '<p style="color: #94a3b8; text-align: center; padding: 20px;">Nenhum jogo salvo ainda.</p>';
            summaryContainer.innerHTML = '';
            return;
        }
        let totalCost = 0;
        let html = '<h3 style="color: #00ff6a;">📋 Meus Jogos Salvos (' + myGames.length + ')</h3>';
        myGames.forEach(function(game, idx) {
            totalCost += game.cost;
            html += '<div class="saved-game"><div><div style="font-size: 0.85rem; color: #94a3b8; margin-bottom: 3px;">' + game.obs + '</div><div class="saved-game-numbers">' + game.numbers.map(function(n) { return String(n).padStart(2, '0'); }).join(' - ') + '</div></div><div style="display: flex; gap: 10px; align-items: center;"><span style="color: #94a3b8; font-size: 0.85rem;">' + game.numbers.length + ' dezenas</span><span class="cost-tag">' + formatBRL(game.cost) + '</span><button class="btn btn-danger" onclick="removeGame(' + idx + ')" style="padding: 6px 12px; font-size: 0.85rem;">✕</button></div></div>';
        });
        container.innerHTML = html;
        summaryContainer.innerHTML = '<div class="summary-box"><h2 style="color: #00ff6a; margin-top: 0;">💰 Meu Total</h2><div class="summary-total">' + formatBRL(totalCost) + '</div><p style="color: #94a3b8;">' + myGames.length + ' jogo(s) | Média: ' + formatBRL(totalCost / myGames.length) + ' por jogo</p></div>';
    }

    async function sendToOcelio() {
        const playerName = document.getElementById('player-name').value.trim();
        if (!playerName) { alert('Por favor, digite seu nome antes de enviar!'); return; }
        if (myGames.length === 0) { alert('Você não tem jogos salvos!'); return; }
        if (!GITHUB_CONFIG.token || !GITHUB_CONFIG.gistId) {
            alert('Configuração do GitHub não disponível. Use a opção "Exportar Backup" e envie o arquivo manualmente.');
            return;
        }
        showToast('🚀 Enviando para Ocelio...', 'info');
        try {
            const getResponse = await fetch('https://api.github.com/gists/' + GITHUB_CONFIG.gistId, {
                headers: { 'Authorization': 'token ' + GITHUB_CONFIG.token, 'Accept': 'application/vnd.github.v3+json' }
            });
            let currentData = { players: [] };
            if (getResponse.ok) {
                const gist = await getResponse.json();
                const file = gist.files[GITHUB_CONFIG.filename];
                if (file) currentData = JSON.parse(file.content);
            }
            const playerData = { playerName: playerName, games: myGames, totalCost: myGames.reduce(function(s, g) { return s + g.cost; }, 0), exportDate: new Date().toLocaleString('pt-BR'), source: 'github' };
            const existingIndex = currentData.players.findIndex(function(p) { return p.playerName === playerName; });
            if (existingIndex >= 0) currentData.players[existingIndex] = playerData;
            else currentData.players.push(playerData);

            const updateResponse = await fetch('https://api.github.com/gists/' + GITHUB_CONFIG.gistId, {
                method: 'PATCH',
                headers: { 'Authorization': 'token ' + GITHUB_CONFIG.token, 'Accept': 'application/vnd.github.v3+json', 'Content-Type': 'application/json' },
                body: JSON.stringify({ files: { [GITHUB_CONFIG.filename]: { content: JSON.stringify(currentData, null, 2) } } })
            });
            if (updateResponse.ok) showToast('✅ Jogos enviados para Ocelio com sucesso!', 'success');
            else throw new Error('Erro na API do GitHub');
        } catch (e) {
            console.error('Erro ao enviar:', e);
            showToast('❌ Erro ao enviar. Tente exportar o arquivo.', 'error');
        }
    }

    function exportGames() {
        const playerName = document.getElementById('player-name').value.trim();
        if (!playerName) { alert('Por favor, digite seu nome antes de exportar!'); return; }
        if (myGames.length === 0) { alert('Você não tem jogos salvos!'); return; }
        const data = { playerName: playerName, games: myGames, totalCost: myGames.reduce(function(s, g) { return s + g.cost; }, 0), exportDate: new Date().toLocaleString('pt-BR') };
        const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = 'jogos_' + playerName.toLowerCase().replace(/\\s+/g, '_') + '.json';
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
        URL.revokeObjectURL(url);
        showToast('✅ Arquivo gerado! Envie para o Ocelio.', 'success');
    }

    function generateSmartGames() {
        const qtd = parseInt(document.getElementById('qtd-games').value);
        const output = document.getElementById('smart-games-output');
        output.innerHTML = '';
        let pool = [];
        for(let i=1; i<=60; i++) {
            if(!NEVER_DRAWN.includes(i)) {
                let weight = HOT_NUMBERS.some(function(h) { return h.num === i; }) ? 3 : 1;
                for(let w=0; w<weight; w++) pool.push(i);
            }
        }
        for(let g=0; g<qtd; g++) {
            let game = new Set();
            let attempts = 0;
            while(game.size < 6 && attempts < 100) { game.add(pool[Math.floor(Math.random() * pool.length)]); attempts++; }
            let gameArr = Array.from(game).sort(function(a, b) { return a - b; });
            let evens = gameArr.filter(function(n) { return n % 2 === 0; }).length;
            if(!(evens===3 || evens===4 || evens===2)) { g--; continue; }
            const gameStr = gameArr.map(function(n) { return String(n).padStart(2, '0'); }).join(' - ');
            output.innerHTML += '<div style="background: #1a1d24; padding: 15px; border-radius: 8px; margin: 10px 0; display: flex; justify-content: space-between; align-items: center; border-left: 4px solid #00ff6a; flex-wrap: wrap; gap: 10px;"><span style="font-size: 1.3rem; font-weight: bold; letter-spacing: 2px;">' + gameStr + '</span><span style="font-size: 0.8rem; background: rgba(0, 255, 106, 0.1); color: #00ff6a; padding: 4px 8px; border-radius: 4px;">Estratégico ' + evens + 'P/' + (6-evens) + 'I - ' + formatBRL(6.00) + '</span></div>';
        }
    }
<\/script>
</body>
</html>`;

        // Substituição segura dos placeholders (elimina 100% dos erros de sintaxe)
        html = html.replace('__GITHUB_TOKEN__', token);
        html = html.replace('__GIST_ID__', gistId);
        html = html.replace('__GIST_FILENAME__', filename);

        const blob = new Blob([html], { type: 'text/html;charset=utf-8' });
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = 'mega_virada_jogador.html';
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
        URL.revokeObjectURL(url);
        showToast('✅ HTML do jogador baixado!', 'success');
    }
</script>

</body>
</html>
