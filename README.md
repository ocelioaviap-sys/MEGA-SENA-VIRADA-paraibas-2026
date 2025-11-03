<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Mega-Sena Virada – Apostas em Grupo</title>
  <style>
    :root {
      --primary: #0056b3;
      --secondary: #007bff;
      --light: #f0f2f5;
      --white: #ffffff;
      --dark: #1c1e21;
      --success: #28a745;
      --danger: #dc3545;
      --gray: #6c757d;
      --warning: #ffc107;
      --info: #17a2b8;
    }
    
    * {
      box-sizing: border-box;
    }
    
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: var(--light);
      color: var(--dark);
      margin: 0;
      padding: 15px;
      line-height: 1.6;
    }
    
    .container {
      max-width: 1000px;
      margin: 0 auto;
      background: var(--white);
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    
    h1 {
      text-align: center;
      color: var(--primary);
      margin-bottom: 30px;
    }
    
    .tabs {
      display: flex;
      margin-bottom: 20px;
      border-bottom: 1px solid #ddd;
      flex-wrap: wrap;
    }
    
    .tab {
      padding: 10px 20px;
      cursor: pointer;
      border: none;
      background: none;
      font-size: 16px;
      border-bottom: 3px solid transparent;
    }
    
    .tab.active {
      border-bottom-color: var(--secondary);
      color: var(--secondary);
      font-weight: bold;
    }
    
    .tab-content {
      display: none;
    }
    
    .tab-content.active {
      display: block;
    }
    
    .player-section {
      margin-bottom: 30px;
      padding: 15px;
      border: 1px solid #ddd;
      border-radius: 8px;
      background-color: #fafafa;
    }
    
    .player-section h2 {
      margin-top: 0;
      color: var(--secondary);
    }
    
    label {
      display: block;
      margin: 10px 0 8px;
      font-weight: bold;
    }
    
    select {
      padding: 8px;
      width: 100%;
      max-width: 400px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    
    .games-container {
      margin-top: 15px;
    }
    
    .game-group {
      margin-bottom: 20px;
      padding: 12px;
      background: #f8f9fa;
      border-radius: 6px;
      border-left: 4px solid var(--secondary);
    }
    
    .game-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;
      flex-wrap: wrap;
    }
    
    .game-title {
      font-weight: bold;
      color: #333;
    }
    
    .game-actions button {
      margin-left: 8px;
      padding: 4px 8px;
      font-size: 13px;
    }
    
    .number-inputs {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 8px;
    }
    
    .number-inputs input {
      width: 42px;
      text-align: center;
      padding: 6px;
      font-weight: bold;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    
    .number-inputs input.error {
      border-color: var(--danger);
      background-color: #ffe6e6;
    }
    
    .email-section {
      margin-top: 30px;
      text-align: center;
    }
    
    .email-section input {
      padding: 10px;
      width: 100%;
      max-width: 400px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    
    button {
      background-color: var(--secondary);
      color: var(--white);
      border: none;
      padding: 12px 24px;
      font-size: 16px;
      border-radius: 6px;
      cursor: pointer;
      transition: opacity 0.2s;
      margin: 5px;
    }
    
    button:hover {
      opacity: 0.9;
    }
    
    button:disabled {
      background-color: var(--gray);
      cursor: not-allowed;
    }
    
    .btn-salvar {
      background-color: var(--success);
    }
    
    .btn-resultado {
      background-color: var(--info);
    }
    
    .btn-copiar {
      background-color: var(--success);
    }
    
    .btn-voltar {
      background-color: var(--gray);
    }
    
    .btn-limpar {
      background-color: var(--danger);
    }
    
    .btn-volante {
      background-color: var(--warning);
      color: var(--dark);
    }
    
    .button-group {
      display: flex;
      justify-content: center;
      gap: 15px;
      flex-wrap: wrap;
      margin-top: 20px;
    }
    
    /* Volante da Mega-Sena */
    .volante-container {
      background-color: var(--white);
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }
    
    .volante-title {
      text-align: center;
      margin-bottom: 15px;
      color: var(--primary);
    }
    
    .volante-grid {
      display: grid;
      grid-template-columns: repeat(10, 1fr);
      gap: 8px;
      margin-bottom: 20px;
    }
    
    .numero {
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: #f8f9fa;
      border: 1px solid #ddd;
      border-radius: 4px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.2s;
      user-select: none;
    }
    
    .numero:hover {
      background-color: #e9ecef;
    }
    
    .numero.selected {
      background-color: var(--secondary);
      color: var(--white);
    }
    
    .volante-controls {
      display: flex;
      justify-content: space-between;
      margin-top: 15px;
      flex-wrap: wrap;
      gap: 10px;
    }
    
    .volante-info {
      margin-top: 15px;
      padding: 10px;
      background-color: #f8f9fa;
      border-radius: 4px;
      text-align: center;
    }
    
    /* Resultado */
    .resultado-container {
      padding: 20px;
      background-color: var(--white);
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    
    .resultado-jogador {
      margin-bottom: 25px;
      padding: 15px;
      border: 1px solid #ddd;
      border-radius: 6px;
      background-color: #fafafa;
    }
    
    .resultado-jogador h3 {
      margin-top: 0;
      color: var(--primary);
      border-bottom: 1px solid #ddd;
      padding-bottom: 8px;
    }
    
    .resultado-jogo {
      margin-bottom: 10px;
      padding: 10px;
      background-color: var(--white);
      border-radius: 4px;
      border-left: 3px solid var(--secondary);
    }
    
    .resultado-numeros {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 5px;
    }
    
    .resultado-numero {
      width: 32px;
      height: 32px;
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: var(--secondary);
      color: var(--white);
      border-radius: 4px;
      font-weight: bold;
    }
    
    .status-info {
      padding: 10px;
      background-color: #e7f3ff;
      border-radius: 4px;
      margin-bottom: 15px;
      text-align: center;
    }
    
    .empty-state {
      text-align: center;
      padding: 40px 20px;
      color: var(--gray);
    }
    
    .empty-state h3 {
      margin-top: 0;
    }
    
    .admin-controls {
      margin-top: 20px;
      padding: 15px;
      background-color: #fff3cd;
      border-radius: 6px;
      border-left: 4px solid var(--warning);
    }
    
    .admin-controls h4 {
      margin-top: 0;
      color: #856404;
    }
    
    .header-buttons {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-bottom: 20px;
      flex-wrap: wrap;
    }
    
    @media (max-width: 600px) {
      .number-inputs input {
        width: 40px;
        font-size: 14px;
      }
      
      .volante-grid {
        grid-template-columns: repeat(5, 1fr);
      }
      
      .volante-controls {
        flex-direction: column;
      }
      
      .game-header {
        flex-direction: column;
        align-items: flex-start;
      }
      
      .game-actions {
        margin-top: 10px;
      }
      
      .button-group, .header-buttons {
        flex-direction: column;
        align-items: center;
      }
      
      .button-group button, .header-buttons button {
        width: 100%;
        max-width: 300px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Mega-Sena Virada – Apostas em Grupo</h1>
    
    <div class="header-buttons">
      <button class="btn-volante" onclick="mudarParaAba('volante')">📋 Usar Volante</button>
      <button class="btn-resultado" onclick="mudarParaAba('resultado')">📊 Ver Resultados Gerais</button>
    </div>
    
    <div class="tabs">
      <button class="tab active" data-tab="aposta">Fazer Apostas</button>
      <button class="tab" data-tab="volante">Volante</button>
      <button class="tab" data-tab="resultado">Resultados Salvos</button>
    </div>
    
    <div id="aposta" class="tab-content active">
      <div class="status-info">
        <p><strong>Status:</strong> <span id="statusApostas">Carregando...</span></p>
      </div>
      
      <form id="apostaForm">
        <div id="playersContainer"></div>
        
        <div class="email-section">
          <label for="senderEmail"><strong>Seu nome (para identificação):</strong></label>
          <input type="text" id="senderEmail" placeholder="Seu nome" />
          <br>
          <div class="button-group">
            <button type="button" class="btn-salvar" id="btnSalvarApostas">💾 Salvar Apostas</button>
            <button type="button" class="btn-resultado" id="btnVerResultados">📊 Ver Meus Resultados</button>
          </div>
        </div>
      </form>
    </div>
    
    <div id="volante" class="tab-content">
      <div class="volante-container">
        <h2 class="volante-title">Volante da Mega-Sena</h2>
        <div class="volante-grid" id="volanteGrid"></div>
        <div class="volante-info">
          <p>Números selecionados: <span id="numerosSelecionados">0</span></p>
          <p>Clique nos números para selecionar/desselecionar</p>
        </div>
        <div class="volante-controls">
          <button type="button" id="btnLimparVolante">🗑️ Limpar Seleção</button>
          <button type="button" id="btnUsarVolante">✅ Usar Números Selecionados</button>
          <button type="button" class="btn-voltar" onclick="mudarParaAba('aposta')">↩️ Voltar para Apostas</button>
        </div>
      </div>
    </div>
    
    <div id="resultado" class="tab-content">
      <div class="resultado-container">
        <h2>Resultado das Apostas</h2>
        <div class="status-info">
          <p><strong>Status:</strong> <span id="statusResultados">Carregando...</span></p>
        </div>
        <div id="resultadoContent">
          <div class="empty-state">
            <h3>Nenhuma aposta salva ainda</h3>
            <p>Vá para a aba "Fazer Apostas" para criar suas apostas.</p>
          </div>
        </div>
        <div class="admin-controls">
          <h4>Controles Administrativos</h4>
          <div class="button-group">
            <button type="button" class="btn-copiar" id="btnCopiarResultado">📋 Copiar Resultado</button>
            <button type="button" class="btn-limpar" id="btnLimparApostas">🗑️ Limpar Todas as Apostas</button>
          </div>
        </div>
        <div class="button-group">
          <button type="button" class="btn-voltar" onclick="mudarParaAba('aposta')">↩️ Voltar para Apostas</button>
        </div>
      </div>
    </div>
  </div>

  <script>
    const jogadores = ["Débora", "Ocelio", "Bernardes", "Edivan", "Erivaldo", "Vei", "Sales", "João"];

    const opcoes = {
      "1": { nome: "Foco em Volume",          jogos: [{tipo:6, qtd:100}] },
      "5": { nome: "Mista (Original)",        jogos: [{tipo:8, qtd:1}, {tipo:6, qtd:72}] },
      "8": { nome: "Mista (Escalonada)",      jogos: [{tipo:8, qtd:1}, {tipo:7, qtd:5}, {tipo:6, qtd:37}] },
      "9": { nome: "Aposta Forte",            jogos: [{tipo:9, qtd:1}, {tipo:6, qtd:16}] }
    };

    // 🔥 Números quentes (top 12) do arquivo MEGA SENA GERAL S BENTO.txt
    const NUMEROS_QUENTES = [4, 23, 20, 17, 10, 25, 18, 33, 56, 11, 53, 36];
    // ❄️ Números frios (top 10 listados visualmente)
    const NUMEROS_FRIOS = [27, 9, 30, 15, 24, 60, 52, 22, 40, 49];
    const TODOS_NUMEROS = Array.from({length: 60}, (_, i) => i + 1);

    // Chave para armazenamento local
    const STORAGE_KEY = 'megaSenaApostas';
    const STORAGE_KEY_TIMESTAMP = 'megaSenaTimestamp';

    // Variáveis globais
    let numerosSelecionadosVolante = [];
    let currentGameGroup = null;
    let apostasSalvas = {};

    // Inicialização
    document.addEventListener('DOMContentLoaded', function() {
      carregarApostasSalvas();
      renderJogadores();
      criarVolante();
      configurarTabs();
      configurarEventos();
      atualizarStatus();
    });

    function mudarParaAba(aba) {
      document.querySelector(`.tab[data-tab="${aba}"]`).click();
    }

    function carregarApostasSalvas() {
      const salvas = localStorage.getItem(STORAGE_KEY);
      if (salvas) {
        apostasSalvas = JSON.parse(salvas);
      }
    }

    function salvarApostas() {
      const dadosApostas = coletarDadosParaSalvar();
      if (!dadosApostas) return false;
      
      // Adicionar timestamp
      dadosApostas.timestamp = new Date().toISOString();
      dadosApostas.autor = document.getElementById('senderEmail').value.trim() || 'Anônimo';
      
      // Salvar no localStorage
      apostasSalvas = dadosApostas;
      localStorage.setItem(STORAGE_KEY, JSON.stringify(apostasSalvas));
      localStorage.setItem(STORAGE_KEY_TIMESTAMP, new Date().toLocaleString('pt-BR'));
      
      return true;
    }

    function coletarDadosParaSalvar() {
      let dados = {
        jogadores: {}
      };
      
      let temAposta = false;
      
      for (const nome of jogadores) {
        const opcao = document.getElementById(`opcao-${nome.replace(/\s+/g, '')}`).value;
        if (!opcao) continue;
        
        temAposta = true;
        const config = opcoes[opcao];
        
        dados.jogadores[nome] = {
          opcao: opcao,
          nomeOpcao: config.nome,
          jogos: []
        };
        
        const container = document.getElementById(`jogos-${nome.replace(/\s+/g, '')}`);
        const grupos = container.querySelectorAll(".game-group");
        
        grupos.forEach((grupo, idx) => {
          const inputs = grupo.querySelectorAll("input");
          const nums = Array.from(inputs).map(inp => inp.value);
          
          dados.jogadores[nome].jogos.push(nums);
        });
      }
      
      return temAposta ? dados : null;
    }

    function carregarApostasNaInterface() {
      if (!apostasSalvas.jogadores) return;
      
      for (const nome of jogadores) {
        if (apostasSalvas.jogadores[nome]) {
          const jogadorData = apostasSalvas.jogadores[nome];
          const select = document.getElementById(`opcao-${nome.replace(/\s+/g, '')}`);
          select.value = jogadorData.opcao;
          atualizarJogos(nome);
          
          // Aguardar um pouco para a interface atualizar antes de preencher os números
          setTimeout(() => {
            const container = document.getElementById(`jogos-${nome.replace(/\s+/g, '')}`);
            const grupos = container.querySelectorAll(".game-group");
            
            grupos.forEach((grupo, idx) => {
              if (jogadorData.jogos[idx]) {
                const inputs = grupo.querySelectorAll("input");
                inputs.forEach((input, i) => {
                  input.value = jogadorData.jogos[idx][i] || "";
                  input.readOnly = true;
                  input.style.backgroundColor = "#f0f8ff";
                });
              }
            });
          }, 100);
        }
      }
      
      if (apostasSalvas.autor) {
        document.getElementById('senderEmail').value = apostasSalvas.autor;
      }
    }

    function configurarTabs() {
      const tabs = document.querySelectorAll('.tab');
      tabs.forEach(tab => {
        tab.addEventListener('click', function() {
          const tabId = this.getAttribute('data-tab');
          
          // Atualizar tabs
          tabs.forEach(t => t.classList.remove('active'));
          this.classList.add('active');
          
          // Atualizar conteúdo
          document.querySelectorAll('.tab-content').forEach(content => {
            content.classList.remove('active');
          });
          document.getElementById(tabId).classList.add('active');
          
          // Se for a aba de resultados, atualizar
          if (tabId === 'resultado') {
            atualizarResultados();
          }
        });
      });
    }

    function configurarEventos() {
      document.getElementById('btnSalvarApostas').addEventListener('click', salvarApostasHandler);
      document.getElementById('btnVerResultados').addEventListener('click', verResultadosHandler);
      document.getElementById('btnLimparVolante').addEventListener('click', limparVolante);
      document.getElementById('btnUsarVolante').addEventListener('click', usarNumerosVolante);
      document.getElementById('btnCopiarResultado').addEventListener('click', copiarResultado);
      document.getElementById('btnLimparApostas').addEventListener('click', limparTodasApostas);
    }

    function criarVolante() {
      const grid = document.getElementById('volanteGrid');
      grid.innerHTML = '';
      
      for (let i = 1; i <= 60; i++) {
        const numero = document.createElement('div');
        numero.className = 'numero';
        numero.textContent = i;
        numero.setAttribute('data-numero', i);
        
        numero.addEventListener('click', function() {
          const num = parseInt(this.getAttribute('data-numero'));
          toggleNumeroVolante(num, this);
        });
        
        grid.appendChild(numero);
      }
      
      atualizarContadorVolante();
    }

    function toggleNumeroVolante(numero, elemento) {
      const index = numerosSelecionadosVolante.indexOf(numero);
      
      if (index === -1) {
        // Adicionar
        if (numerosSelecionadosVolante.length < 15) {
          numerosSelecionadosVolante.push(numero);
          elemento.classList.add('selected');
        } else {
          alert('Você pode selecionar no máximo 15 números.');
        }
      } else {
        // Remover
        numerosSelecionadosVolante.splice(index, 1);
        elemento.classList.remove('selected');
      }
      
      atualizarContadorVolante();
    }

    function limparVolante() {
      numerosSelecionadosVolante = [];
      document.querySelectorAll('.numero.selected').forEach(el => {
        el.classList.remove('selected');
      });
      atualizarContadorVolante();
    }

    function usarNumerosVolante() {
      if (numerosSelecionadosVolante.length === 0) {
        alert('Selecione pelo menos um número no volante.');
        return;
      }
      
      if (!currentGameGroup) {
        alert('Primeiro, selecione um jogo para preencher.');
        return;
      }
      
      const inputs = currentGameGroup.querySelectorAll('input');
      const tipo = inputs.length;
      
      if (numerosSelecionadosVolante.length < tipo) {
        alert(`Este jogo precisa de ${tipo} números, mas você selecionou apenas ${numerosSelecionadosVolante.length}.`);
        return;
      }
      
      // Usar os primeiros N números selecionados
      const numerosParaUsar = [...numerosSelecionadosVolante].slice(0, tipo).sort((a, b) => a - b);
      
      inputs.forEach((input, index) => {
        input.value = numerosParaUsar[index];
        input.readOnly = true;
        input.style.backgroundColor = '#f0f8ff';
        input.classList.remove('error');
      });
      
      // Limpar seleção após uso
      limparVolante();
      
      // Voltar para a aba de apostas
      mudarParaAba('aposta');
    }

    function atualizarContadorVolante() {
      document.getElementById('numerosSelecionados').textContent = numerosSelecionadosVolante.length;
    }

    function gerarJogoInteligente(tipo) {
      const maxTentativas = 500;
      for (let t = 0; t < maxTentativas; t++) {
        let pool = [];
        // 3x chance para quentes, 1x para neutros, 0.3x para frios
        TODOS_NUMEROS.forEach(n => {
          if (NUMEROS_QUENTES.includes(n)) pool.push(...Array(3).fill(n));
          else if (!NUMEROS_FRIOS.includes(n)) pool.push(n);
          else pool.push(...Array(Math.random() > 0.7 ? 1 : 0).fill(n)); // raro
        });
        // Embaralha e escolhe únicos
        let jogoSet = new Set();
        while (jogoSet.size < tipo && pool.length > 0) {
          const idx = Math.floor(Math.random() * pool.length);
          jogoSet.add(pool[idx]);
          pool = pool.filter(x => x !== pool[idx]);
        }
        if (jogoSet.size < tipo) continue;
        let jogo = [...jogoSet].sort((a, b) => a - b);

        // Valida soma
        const soma = jogo.reduce((a, b) => a + b, 0);
        if (soma < 150 || soma > 230) continue;

        // Paridade
        const pares = jogo.filter(n => n % 2 === 0).length;
        if (Math.abs(pares - (tipo - pares)) > 2) continue;

        // Baixos (1-30) e Altos (31-60)
        const baixos = jogo.filter(n => n <= 30).length;
        if (baixos < 2 || baixos > tipo - 2) continue;

        // Sem consecutivos
        let temConsec = false;
        for (let i = 0; i < jogo.length - 1; i++) {
          if (jogo[i + 1] - jogo[i] === 1) { temConsec = true; break; }
        }
        if (temConsec) continue;

        return jogo;
      }

      // Fallback seguro
      return [...TODOS_NUMEROS]
        .sort(() => 0.5 - Math.random())
        .slice(0, tipo)
        .sort((a, b) => a - b);
    }

    function renderJogadores() {
      const container = document.getElementById("playersContainer");
      container.innerHTML = '';
      
      jogadores.forEach(nome => {
        const div = document.createElement("div");
        div.className = "player-section";
        div.innerHTML = `
          <h2>${nome}</h2>
          <label for="opcao-${nome.replace(/\s+/g, '')}">Escolha sua opção:</label>
          <select id="opcao-${nome.replace(/\s+/g, '')}" onchange="atualizarJogos('${nome}')">
            <option value="">Selecione uma opção</option>
            <option value="1">Opção 1: Foco em Volume (100x6)</option>
            <option value="5">Opção 5: Mista (Original)</option>
            <option value="8">Opção 8: Mista (Escalonada)</option>
            <option value="9">Opção 9: Aposta Forte</option>
          </select>
          <div id="jogos-${nome.replace(/\s+/g, '')}" class="games-container"></div>
        `;
        container.appendChild(div);
      });
      
      // Carregar apostas salvas na interface
      carregarApostasNaInterface();
    }

    function atualizarJogos(jogador) {
      const selectId = `opcao-${jogador.replace(/\s+/g, '')}`;
      const containerId = `jogos-${jogador.replace(/\s+/g, '')}`;
      const valor = document.getElementById(selectId).value;
      const container = document.getElementById(containerId);
      container.innerHTML = "";
      if (!valor) return;

      const config = opcoes[valor];
      let jogoIndex = 1;
      config.jogos.forEach(grupo => {
        for (let i = 1; i <= grupo.qtd; i++) {
          const grupoDiv = document.createElement("div");
          grupoDiv.className = "game-group";
          grupoDiv.innerHTML = `
            <div class="game-header">
              <div class="game-title">Jogo ${jogoIndex} (${grupo.tipo} números)</div>
              <div class="game-actions">
                <button type="button" onclick="preencherManual(this)">✏️ Preencher</button>
                <button type="button" onclick="gerarAleatorio(this, ${grupo.tipo})">🎲 Gerar Aleatório</button>
                <button type="button" onclick="usarVolanteParaJogo(this)">📋 Usar Volante</button>
              </div>
            </div>
            <div class="number-inputs"></div>
          `;
          const inputsDiv = grupoDiv.querySelector(".number-inputs");
          for (let n = 0; n < grupo.tipo; n++) {
            const input = document.createElement("input");
            input.type = "number";
            input.min = 1;
            input.max = 60;
            input.readOnly = true;
            input.addEventListener("input", function() {
              this.classList.remove("error");
            });
            inputsDiv.appendChild(input);
          }
          container.appendChild(grupoDiv);
          jogoIndex++;
        }
      });
    }

    function preencherManual(botao) {
      const inputs = botao.closest(".game-group").querySelectorAll("input");
      inputs.forEach(inp => {
        inp.readOnly = false;
        inp.style.backgroundColor = "#fff";
      });
    }

    function gerarAleatorio(botao, tipo) {
      const numeros = gerarJogoInteligente(tipo);
      const inputs = botao.closest(".game-group").querySelectorAll("input");
      inputs.forEach((inp, i) => {
        inp.readOnly = false;
        inp.value = numeros[i] || "";
        inp.readOnly = true;
        inp.style.backgroundColor = "#f0f8ff";
        inp.classList.remove("error");
      });
    }

    function usarVolanteParaJogo(botao) {
      currentGameGroup = botao.closest(".game-group");
      mudarParaAba('volante');
    }

    function validarTudo() {
      const erros = [];
      for (const nome of jogadores) {
        const opcao = document.getElementById(`opcao-${nome.replace(/\s+/g, '')}`).value;
        if (!opcao) continue;

        const container = document.getElementById(`jogos-${nome.replace(/\s+/g, '')}`);
        const grupos = container.querySelectorAll(".game-group");

        grupos.forEach((grupo, idxJogo) => {
          const inputs = grupo.querySelectorAll("input");
          const valores = Array.from(inputs).map(inp => inp.value.trim());
          const jogoNum = idxJogo + 1;

          if (valores.some(v => v === "")) {
            erros.push(`${nome}: Jogo ${jogoNum} está incompleto.`);
          }

          const invalidos = valores.filter(v => v !== "" && (isNaN(v) || v < 1 || v > 60));
          if (invalidos.length > 0) {
            erros.push(`${nome}: Jogo ${jogoNum} tem número(s) inválido(s).`);
          }

          const nums = valores.filter(v => v !== "").map(Number);
          if (new Set(nums).size !== nums.length) {
            erros.push(`${nome}: Jogo ${jogoNum} contém número(s) repetido(s).`);
          }
        });
      }

      if (erros.length > 0) {
        alert("Corrija os seguintes erros antes de salvar:\n\n• " + erros.join("\n• "));
        return false;
      }
      return true;
    }

    function salvarApostasHandler() {
      if (!validarTudo()) return;
      
      if (salvarApostas()) {
        alert('Apostas salvas com sucesso! Agora você pode visualizá-las na aba "Resultados Salvos".');
        atualizarStatus();
      } else {
        alert('Erro ao salvar as apostas. Verifique se pelo menos um jogador fez uma aposta.');
      }
    }

    function verResultadosHandler() {
      if (!apostasSalvas.jogadores || Object.keys(apostasSalvas.jogadores).length === 0) {
        alert('Nenhuma aposta salva ainda. Primeiro salve suas apostas.');
        return;
      }
      
      atualizarResultados();
      mudarParaAba('resultado');
    }

    function atualizarStatus() {
      const timestamp = localStorage.getItem(STORAGE_KEY_TIMESTAMP);
      const temApostas = apostasSalvas && apostasSalvas.jogadores && Object.keys(apostasSalvas.jogadores).length > 0;
      
      if (temApostas) {
        const autor = apostasSalvas.autor || 'Desconhecido';
        document.getElementById('statusApostas').innerHTML = 
          `Apostas salvas em ${timestamp} por <strong>${autor}</strong>`;
        document.getElementById('statusResultados').innerHTML = 
          `Apostas salvas em ${timestamp} por <strong>${autor}</strong>`;
      } else {
        document.getElementById('statusApostas').textContent = 'Nenhuma aposta salva ainda';
        document.getElementById('statusResultados').textContent = 'Nenhuma aposta salva ainda';
      }
    }

    function atualizarResultados() {
      const resultadoContent = document.getElementById('resultadoContent');
      
      if (!apostasSalvas.jogadores || Object.keys(apostasSalvas.jogadores).length === 0) {
        resultadoContent.innerHTML = `
          <div class="empty-state">
            <h3>Nenhuma aposta salva ainda</h3>
            <p>Vá para a aba "Fazer Apostas" para criar suas apostas.</p>
          </div>
        `;
        return;
      }
      
      let htmlResultado = `<h3>Resultado das Apostas - Mega-Sena Virada</h3>`;
      
      if (apostasSalvas.autor) {
        htmlResultado += `<p><strong>Salvo por:</strong> ${apostasSalvas.autor}</p>`;
      }
      
      if (apostasSalvas.timestamp) {
        const data = new Date(apostasSalvas.timestamp);
        htmlResultado += `<p><strong>Data/hora:</strong> ${data.toLocaleString('pt-BR')}</p>`;
      }
      
      htmlResultado += `<hr>`;
      
      for (const nome of jogadores) {
        if (apostasSalvas.jogadores[nome]) {
          const jogadorData = apostasSalvas.jogadores[nome];
          htmlResultado += `<div class="resultado-jogador">`;
          htmlResultado += `<h3>${nome}</h3>`;
          htmlResultado += `<p><strong>Opção:</strong> ${jogadorData.nomeOpcao}</p>`;
          
          jogadorData.jogos.forEach((jogo, idx) => {
            htmlResultado += `<div class="resultado-jogo">`;
            htmlResultado += `<p><strong>Jogo ${idx + 1}:</strong></p>`;
            htmlResultado += `<div class="resultado-numeros">`;
            
            jogo.forEach(num => {
              htmlResultado += `<div class="resultado-numero">${num.toString().padStart(2, '0')}</div>`;
            });
            
            htmlResultado += `</div>`;
            htmlResultado += `</div>`;
          });
          
          htmlResultado += `</div>`;
        }
      }
      
      resultadoContent.innerHTML = htmlResultado;
    }

    function copiarResultado() {
      const resultadoContent = document.getElementById('resultadoContent');
      const texto = resultadoContent.innerText || resultadoContent.textContent;
      
      navigator.clipboard.writeText(texto)
        .then(() => {
          alert('Resultado copiado para a área de transferência!');
        })
        .catch(err => {
          console.error('Erro ao copiar: ', err);
          alert('Erro ao copiar o resultado. Tente novamente.');
        });
    }

    function limparTodasApostas() {
      if (confirm('Tem certeza que deseja limpar TODAS as apostas salvas? Esta ação não pode ser desfeita.')) {
        localStorage.removeItem(STORAGE_KEY);
        localStorage.removeItem(STORAGE_KEY_TIMESTAMP);
        apostasSalvas = {};
        location.reload();
      }
    }
  </script>
</body>
</html>
