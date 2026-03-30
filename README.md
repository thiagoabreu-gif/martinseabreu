Aqui está o código completo para você copiar:
html<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Seleção de Módulo</title>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: #f5f5f3;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 2rem;
    }

    .container {
      background: #ffffff;
      border-radius: 16px;
      padding: 2.5rem 2rem;
      max-width: 560px;
      width: 100%;
      border: 0.5px solid #e0dfd8;
    }

    h2 {
      font-size: 20px;
      font-weight: 500;
      color: #1a1a18;
      margin-bottom: 6px;
    }

    p.sub {
      font-size: 14px;
      color: #6b6b67;
      margin-bottom: 1.5rem;
    }

    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 16px;
      margin-bottom: 1.5rem;
    }

    .option-card {
      background: #ffffff;
      border: 0.5px solid #e0dfd8;
      border-radius: 12px;
      padding: 2rem 1.5rem;
      cursor: pointer;
      transition: border-color 0.2s, transform 0.15s;
      text-align: center;
      user-select: none;
    }

    .option-card:hover {
      border-color: #b0afaa;
      transform: translateY(-2px);
    }

    .option-card.selected {
      border: 2px solid #378ADD;
    }

    .option-card.selected .badge {
      display: inline-block;
    }

    .badge {
      display: none;
      background: #E6F1FB;
      color: #185FA5;
      font-size: 11px;
      padding: 3px 10px;
      border-radius: 8px;
      margin-bottom: 12px;
      font-weight: 500;
    }

    .icon-wrap {
      width: 56px;
      height: 56px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 1rem;
    }

    .icon-solar { background: #FAEEDA; }
    .icon-obras { background: #E1F5EE; }

    .card-title {
      font-size: 16px;
      font-weight: 500;
      color: #1a1a18;
      margin: 0 0 6px;
    }

    .card-desc {
      font-size: 13px;
      color: #6b6b67;
      line-height: 1.5;
    }

    .btn-continue {
      width: 100%;
      padding: 11px;
      border: 0.5px solid #b0afaa;
      border-radius: 8px;
      background: transparent;
      color: #1a1a18;
      font-size: 14px;
      cursor: pointer;
      display: none;
      transition: background 0.15s;
    }

    .btn-continue:hover { background: #f5f5f3; }
    .btn-continue:active { transform: scale(0.98); }
    .btn-continue.visible { display: block; }

    .resultado {
      display: none;
      margin-top: 1.5rem;
      padding: 1rem 1.25rem;
      background: #f5f5f3;
      border-radius: 8px;
      font-size: 14px;
      color: #1a1a18;
      border-left: 3px solid #378ADD;
    }

    .resultado.visible { display: block; }
  </style>
</head>
<body>

  <div class="container">
    <h2>Selecione uma área</h2>
    <p class="sub">Escolha o módulo que deseja acessar</p>

    <div class="card-grid">

      <div class="option-card" id="card-solar" onclick="selecionar('solar')">
        <span class="badge">Selecionado</span>
        <div class="icon-wrap icon-solar">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
            <circle cx="12" cy="12" r="4" fill="#BA7517"/>
            <line x1="12" y1="2" x2="12" y2="5" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="12" y1="19" x2="12" y2="22" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="2" y1="12" x2="5" y2="12" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="19" y1="12" x2="22" y2="12" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="4.22" y1="4.22" x2="6.34" y2="6.34" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="17.66" y1="17.66" x2="19.78" y2="19.78" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="19.78" y1="4.22" x2="17.66" y2="6.34" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
            <line x1="6.34" y1="17.66" x2="4.22" y2="19.78" stroke="#BA7517" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </div>
        <p class="card-title">Energia Solar</p>
        <p class="card-desc">Monitoramento e gestão de sistemas de energia fotovoltaica</p>
      </div>

      <div class="option-card" id="card-obras" onclick="selecionar('obras')">
        <span class="badge">Selecionado</span>
        <div class="icon-wrap icon-obras">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
            <rect x="3" y="14" width="18" height="7" rx="1" fill="#0F6E56"/>
            <rect x="7" y="9" width="10" height="5" rx="1" fill="#1D9E75"/>
            <rect x="10" y="5" width="4" height="4" rx="1" fill="#0F6E56"/>
            <rect x="6" y="16" width="2" height="3" rx="0.5" fill="#E1F5EE"/>
            <rect x="11" y="16" width="2" height="3" rx="0.5" fill="#E1F5EE"/>
            <rect x="16" y="16" width="2" height="3" rx="0.5" fill="#E1F5EE"/>
          </svg>
        </div>
        <p class="card-title">Gestão de Obras</p>
        <p class="card-desc">Acompanhamento de projetos, etapas e equipes de construção</p>
      </div>

    </div>

    <button class="btn-continue" id="btn" onclick="continuar()">Continuar →</button>
    <div class="resultado" id="resultado"></div>
  </div>

  <script>
    let selecionado = null;

    function selecionar(opcao) {
      selecionado = opcao;
      document.getElementById('card-solar').classList.toggle('selected', opcao === 'solar');
      document.getElementById('card-obras').classList.toggle('selected', opcao === 'obras');
      document.getElementById('btn').classList.add('visible');
      document.getElementById('resultado').classList.remove('visible');
    }

    function continuar() {
      const res = document.getElementById('resultado');
      if (selecionado === 'solar') {
        res.textContent = 'Você selecionou: Energia Solar. Redirecionando para o módulo fotovoltaico...';
      } else {
        res.textContent = 'Você selecionou: Gestão de Obras. Redirecionando para o módulo de projetos...';
      }
      res.classList.add('visible');
    }
  </script>

</body>
</html>
