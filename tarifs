<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="Tarifs">
<title>Calculateur de tarif</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: #f2f2f7;
    color: #1c1c1e;
    padding: 20px;
    min-height: 100vh;
    -webkit-tap-highlight-color: transparent;
  }
  .container { max-width: 420px; margin: 0 auto; }
  h1 {
    font-size: 24px;
    font-weight: 800;
    margin-bottom: 20px;
    text-align: center;
    letter-spacing: -0.5px;
  }
  .tabs {
    display: flex;
    gap: 4px;
    margin-bottom: 16px;
    background: #e5e5ea;
    padding: 4px;
    border-radius: 12px;
  }
  .tab {
    flex: 1;
    padding: 10px;
    font-size: 15px;
    font-weight: 600;
    color: #8e8e93;
    background: transparent;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: all 0.15s;
  }
  .tab.active {
    background: #fff;
    color: #1c1c1e;
    box-shadow: 0 1px 4px rgba(0,0,0,0.08);
  }
  .tab-content { display: none; }
  .tab-content.active { display: block; }
  .card {
    background: #fff;
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 16px;
    box-shadow: 0 2px 12px rgba(0,0,0,0.06);
  }
  label {
    display: block;
    font-size: 12px;
    font-weight: 700;
    color: #8e8e93;
    text-transform: uppercase;
    letter-spacing: 0.6px;
    margin-bottom: 8px;
  }
  select, input[type="number"] {
    width: 100%;
    padding: 14px 16px;
    font-size: 17px;
    border: 1.5px solid #e5e5ea;
    border-radius: 12px;
    background: #f9f9fb;
    color: #1c1c1e;
    outline: none;
    -webkit-appearance: none;
    appearance: none;
    margin-bottom: 18px;
    font-weight: 500;
  }
  select {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath fill='%238e8e93' d='M6 8L0 0h12z'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 16px center;
    padding-right: 40px;
  }
  select:focus, input:focus {
    border-color: #007aff;
    background: #fff;
  }
  button.calc {
    width: 100%;
    padding: 16px;
    font-size: 17px;
    font-weight: 700;
    color: #fff;
    background: #007aff;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    transition: opacity 0.15s;
  }
  button.calc:active { opacity: 0.7; }
  .result { display: none; }
  .result.visible { display: block; }
  .result-main {
    font-size: 36px;
    font-weight: 800;
    text-align: center;
    margin-bottom: 2px;
    color: #007aff;
    letter-spacing: -1px;
  }
  .result-label {
    font-size: 13px;
    color: #8e8e93;
    text-align: center;
    margin-bottom: 18px;
    font-weight: 500;
  }
  .detail { font-size: 15px; color: #3a3a3c; }
  .detail-row {
    display: flex;
    justify-content: space-between;
    padding: 8px 0;
    border-bottom: 1px solid #f2f2f7;
  }
  .detail-row:last-child { border-bottom: none; }
  .detail-row span:last-child { font-weight: 600; }
  .note {
    font-size: 11px;
    color: #8e8e93;
    text-align: center;
    margin-top: 12px;
    line-height: 1.4;
  }
  .error {
    color: #ff3b30;
    font-size: 14px;
    text-align: center;
    margin-top: 10px;
    font-weight: 500;
  }
  .grid-section h2 {
    font-size: 17px;
    font-weight: 700;
    margin-bottom: 14px;
    color: #1c1c1e;
  }
  .grid-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 0;
    border-bottom: 1px solid #f2f2f7;
    gap: 8px;
  }
  .grid-row:last-child { border-bottom: none; }
  .grid-row > label {
    font-size: 14px;
    color: #3a3a3c;
    font-weight: 500;
    text-transform: none;
    letter-spacing: 0;
    margin: 0;
    flex: 1;
  }
  .grid-row > input {
    width: 85px;
    padding: 8px 10px;
    font-size: 15px;
    border: 1.5px solid #e5e5ea;
    border-radius: 8px;
    background: #f9f9fb;
    text-align: right;
    font-weight: 600;
    margin: 0;
    -webkit-appearance: none;
    appearance: none;
  }
  .grid-row > input:focus {
    border-color: #007aff;
    background: #fff;
  }
  .grid-row > .unit {
    font-size: 12px;
    color: #8e8e93;
    width: 40px;
    text-align: right;
  }
  button.reset {
    width: 100%;
    padding: 14px;
    font-size: 15px;
    font-weight: 600;
    color: #ff3b30;
    background: #fff;
    border: 1.5px solid #ff3b30;
    border-radius: 12px;
    cursor: pointer;
    margin-top: 8px;
  }
  button.reset:active { opacity: 0.7; }
</style>
</head>
<body>
<div class="container">
  <h1>Calculateur de tarif</h1>
  
  <div class="tabs">
    <button class="tab active" onclick="showTab('calc', this)">Calculateur</button>
    <button class="tab" onclick="showTab('grid', this)">Grilles</button>
  </div>
  
  <!-- ===== ONGLET CALCULATEUR ===== -->
  <div id="tab-calc" class="tab-content active">
    <div class="card">
      <label for="type">Type de prestation</label>
      <select id="type">
        <option value="toiture">Démoussage toiture</option>
        <option value="facade">Nettoyage façade</option>
        <option value="solaire">Nettoyage panneaux solaires</option>
      </select>
      
      <label for="surface">Surface totale (m²)</label>
      <input type="number" id="surface" placeholder="Ex : 150" min="1" step="1" inputmode="decimal">
      
      <button class="calc" onclick="calculer()">Calculer le tarif</button>
      <div id="error" class="error"></div>
    </div>
    
    <div class="card result" id="result">
      <div class="result-main" id="resultMain">—</div>
      <div class="result-label">Total HT</div>
      <div class="detail" id="detail"></div>
      <div class="note">TVA non applicable, art. 293 B du CGI<br>Déplacement inclus</div>
    </div>
  </div>
  
  <!-- ===== ONGLET GRILLES ===== -->
  <div id="tab-grid" class="tab-content">
    
    <!-- Toiture -->
    <div class="card grid-section">
      <h2>Démoussage toiture</h2>
      <div class="grid-row">
        <label>Minimum de facturation</label>
        <input type="number" id="cfg_toiture_min" step="1" oninput="updateConfig('toiture','min',this.value)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Seuil minimum</label>
        <input type="number" id="cfg_toiture_seuilMin" step="1" oninput="updateConfig('toiture','seuilMin',this.value)">
        <span class="unit">m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 0-150 m²</label>
        <input type="number" id="cfg_toiture_r0" step="0.01" oninput="updateConfig('toiture','rates',this.value,0)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 150-300 m²</label>
        <input type="number" id="cfg_toiture_r1" step="0.01" oninput="updateConfig('toiture','rates',this.value,1)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 300-500 m²</label>
        <input type="number" id="cfg_toiture_r2" step="0.01" oninput="updateConfig('toiture','rates',this.value,2)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 500-800 m²</label>
        <input type="number" id="cfg_toiture_r3" step="0.01" oninput="updateConfig('toiture','rates',this.value,3)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 800-1200 m²</label>
        <input type="number" id="cfg_toiture_r4" step="0.01" oninput="updateConfig('toiture','rates',this.value,4)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif &gt; 1200 m²</label>
        <input type="number" id="cfg_toiture_r5" step="0.01" oninput="updateConfig('toiture','rates',this.value,5)">
        <span class="unit">€/m²</span>
      </div>
    </div>
    
    <!-- Façade -->
    <div class="card grid-section">
      <h2>Nettoyage façade</h2>
      <div class="grid-row">
        <label>Minimum de facturation</label>
        <input type="number" id="cfg_facade_min" step="1" oninput="updateConfig('facade','min',this.value)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Tarif 0-150 m²</label>
        <input type="number" id="cfg_facade_rate0" step="0.01" oninput="updateConfig('facade','rate0',this.value)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 150-300 m²</label>
        <input type="number" id="cfg_facade_r0" step="0.01" oninput="updateConfig('facade','rates',this.value,0)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 300-500 m²</label>
        <input type="number" id="cfg_facade_r1" step="0.01" oninput="updateConfig('facade','rates',this.value,1)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 500-800 m²</label>
        <input type="number" id="cfg_facade_r2" step="0.01" oninput="updateConfig('facade','rates',this.value,2)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 800-1200 m²</label>
        <input type="number" id="cfg_facade_r3" step="0.01" oninput="updateConfig('facade','rates',this.value,3)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif &gt; 1200 m²</label>
        <input type="number" id="cfg_facade_r4" step="0.01" oninput="updateConfig('facade','rates',this.value,4)">
        <span class="unit">€/m²</span>
      </div>
    </div>
    
    <!-- Solaire -->
    <div class="card grid-section">
      <h2>Nettoyage panneaux solaires</h2>
      <div class="grid-row">
        <label>Minimum (0-30 m²)</label>
        <input type="number" id="cfg_solaire_min" step="1" oninput="updateConfig('solaire','min',this.value)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Forfait 30-50 m²</label>
        <input type="number" id="cfg_solaire_f0" step="1" oninput="updateConfig('solaire','forfaits',this.value,0)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Forfait 50-75 m²</label>
        <input type="number" id="cfg_solaire_f1" step="1" oninput="updateConfig('solaire','forfaits',this.value,1)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Forfait 75-100 m²</label>
        <input type="number" id="cfg_solaire_f2" step="1" oninput="updateConfig('solaire','forfaits',this.value,2)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Forfait 100-250 m²</label>
        <input type="number" id="cfg_solaire_f3" step="1" oninput="updateConfig('solaire','forfaits',this.value,3)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Forfait 250-500 m²</label>
        <input type="number" id="cfg_solaire_f4" step="1" oninput="updateConfig('solaire','forfaits',this.value,4)">
        <span class="unit">€</span>
      </div>
      <div class="grid-row">
        <label>Tarif 500-1000 m²</label>
        <input type="number" id="cfg_solaire_r0" step="0.01" oninput="updateConfig('solaire','rates',this.value,0)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 1000-1500 m²</label>
        <input type="number" id="cfg_solaire_r1" step="0.01" oninput="updateConfig('solaire','rates',this.value,1)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif 1500-2000 m²</label>
        <input type="number" id="cfg_solaire_r2" step="0.01" oninput="updateConfig('solaire','rates',this.value,2)">
        <span class="unit">€/m²</span>
      </div>
      <div class="grid-row">
        <label>Tarif &gt; 2000 m²</label>
        <input type="number" id="cfg_solaire_r3" step="0.01" oninput="updateConfig('solaire','rates',this.value,3)">
        <span class="unit">€/m²</span>
      </div>
    </div>
    
    <button class="reset" onclick="resetConfig()">Réinitialiser les valeurs par défaut</button>
  </div>
</div>

<script>
// ===== CONFIGURATION PAR DÉFAUT =====
var DEFAULTS = {
  toiture: {
    min: 210,
    seuilMin: 38,
    rates: [5.50, 4.50, 4.20, 3.90, 3.70, 3.50]
  },
  facade: {
    min: 250,
    rate0: 6.50,
    rates: [5.20, 4.60, 4.20, 3.90, 3.60]
  },
  solaire: {
    min: 180,
    forfaits: [215, 250, 305, 345, 425],
    rates: [0.85, 0.75, 0.65, 0.55]
  }
};

var config = loadConfig();

// ===== CHARGEMENT / SAUVEGARDE =====
function loadConfig() {
  var saved = localStorage.getItem('tarifConfig');
  if (saved) {
    try {
      var parsed = JSON.parse(saved);
      // Fusion pour éviter les clés manquantes
      return {
        toiture: Object.assign({}, DEFAULTS.toiture, parsed.toiture || {}),
        facade: Object.assign({}, DEFAULTS.facade, parsed.facade || {}),
        solaire: Object.assign({}, DEFAULTS.solaire, parsed.solaire || {})
      };
    } catch(e) {}
  }
  return JSON.parse(JSON.stringify(DEFAULTS));
}

function saveConfig() {
  localStorage.setItem('tarifConfig', JSON.stringify(config));
}

function updateConfig(service, key, value, index) {
  var num = parseFloat(value);
  if (isNaN(num)) num = 0;
  if (index !== undefined) {
    config[service][key][index] = num;
  } else {
    config[service][key] = num;
  }
  saveConfig();
}

function resetConfig() {
  if (confirm('Réinitialiser tous les tarifs par défaut ?')) {
    config = JSON.parse(JSON.stringify(DEFAULTS));
    saveConfig();
    populateGrid();
  }
}

// ===== REMPLISSAGE DES CHAMPS =====
function populateGrid() {
  document.getElementById('cfg_toiture_min').value = config.toiture.min;
  document.getElementById('cfg_toiture_seuilMin').value = config.toiture.seuilMin;
  for (var i = 0; i < 6; i++) {
    document.getElementById('cfg_toiture_r' + i).value = config.toiture.rates[i];
  }
  document.getElementById('cfg_facade_min').value = config.facade.min;
  document.getElementById('cfg_facade_rate0').value = config.facade.rate0;
  for (var j = 0; j < 5; j++) {
    document.getElementById('cfg_facade_r' + j).value = config.facade.rates[j];
  }
  document.getElementById('cfg_solaire_min').value = config.solaire.min;
  for (var k = 0; k < 5; k++) {
    document.getElementById('cfg_solaire_f' + k).value = config.solaire.forfaits[k];
  }
  for (var l = 0; l < 4; l++) {
    document.getElementById('cfg_solaire_r' + l).value = config.solaire.rates[l];
  }
}

// ===== GRILLES DE CALCUL =====
function calculerToiture(S) {
  var c = config.toiture;
  if (S <= c.seuilMin) return c.min;
  if (S <= 150) return S * c.rates[0];
  var base = 150 * c.rates[0];
  if (S <= 300) return base + (S - 150) * c.rates[1];
  base += 150 * c.rates[1];
  if (S <= 500) return base + (S - 300) * c.rates[2];
  base += 200 * c.rates[2];
  if (S <= 800) return base + (S - 500) * c.rates[3];
  base += 300 * c.rates[3];
  if (S <= 1200) return base + (S - 800) * c.rates[4];
  base += 400 * c.rates[4];
  return base + (S - 1200) * c.rates[5];
}

function calculerFacade(S) {
  var c = config.facade;
  if (S <= 150) return Math.max(S * c.rate0, c.min);
  var base = 150 * c.rate0;
  if (S <= 300) return base + (S - 150) * c.rates[0];
  base += 150 * c.rates[0];
  if (S <= 500) return base + (S - 300) * c.rates[1];
  base += 200 * c.rates[1];
  if (S <= 800) return base + (S - 500) * c.rates[2];
  base += 300 * c.rates[2];
  if (S <= 1200) return base + (S - 800) * c.rates[3];
  base += 400 * c.rates[3];
  return base + (S - 1200) * c.rates[4];
}

function calculerSolaire(S) {
  var c = config.solaire;
  if (S <= 30) return c.min;
  if (S <= 50) return c.forfaits[0];
  if (S <= 75) return c.forfaits[1];
  if (S <= 100) return c.forfaits[2];
  if (S <= 250) return c.forfaits[3];
  if (S <= 500) return c.forfaits[4];
  if (S <= 1000) return S * c.rates[0];
  if (S <= 1500) return S * c.rates[1];
  if (S <= 2000) return S * c.rates[2];
  return S * c.rates[3];
}

// ===== AFFICHAGE =====
function formatEuro(n) {
  return n.toLocaleString('fr-FR', { minimumFractionDigits: 2, maximumFractionDigits: 2 }) + ' €';
}

function showTab(name, btn) {
  document.querySelectorAll('.tab-content').forEach(function(el) {
    el.classList.remove('active');
  });
  document.querySelectorAll('.tab').forEach(function(el) {
    el.classList.remove('active');
  });
  document.getElementById('tab-' + name).classList.add('active');
  btn.classList.add('active');
}

function calculer() {
  var type = document.getElementById('type').value;
  var surface = parseFloat(document.getElementById('surface').value);
  var errorEl = document.getElementById('error');
  var resultEl = document.getElementById('result');
  
  errorEl.textContent = '';
  
  if (isNaN(surface) || surface <= 0) {
    errorEl.textContent = 'Veuillez saisir une surface valide.';
    resultEl.classList.remove('visible');
    return;
  }
  
  var total, detailHtml;
  
  if (type === 'toiture') {
    total = calculerToiture(surface);
    detailHtml = '<div class="detail-row"><span>Surface</span><span>' + surface + ' m²</span></div>';
    detailHtml += '<div class="detail-row"><span>Prestation</span><span>Démoussage toiture</span></div>';
    if (surface <= config.toiture.seuilMin) {
      detailHtml += '<div class="detail-row"><span>Tarif</span><span>Minimum de facturation</span></div>';
    }
  } else if (type === 'facade') {
    total = calculerFacade(surface);
    detailHtml = '<div class="detail-row"><span>Surface</span><span>' + surface + ' m²</span></div>';
    detailHtml += '<div class="detail-row"><span>Prestation</span><span>Nettoyage façade</span></div>';
    if (surface <= 150 && surface * config.facade.rate0 < config.facade.min) {
      detailHtml += '<div class="detail-row"><span>Tarif</span><span>Minimum de facturation</span></div>';
    }
  } else {
    total = calculerSolaire(surface);
    detailHtml = '<div class="detail-row"><span>Surface</span><span>' + surface + ' m²</span></div>';
    detailHtml += '<div class="detail-row"><span>Prestation</span><span>Nettoyage panneaux solaires</span></div>';
    if (surface <= 30) {
      detailHtml += '<div class="detail-row"><span>Tarif</span><span>Minimum de facturation</span></div>';
    } else if (surface <= 500) {
      detailHtml += '<div class="detail-row"><span>Tarif</span><span>Forfait</span></div>';
    }
  }
  
  var prixM2 = total / surface;
  detailHtml += '<div class="detail-row"><span>Prix moyen</span><span>' + formatEuro(prixM2) + ' / m²</span></div>';
  
  document.getElementById('resultMain').textContent = formatEuro(total);
  document.getElementById('detail').innerHTML = detailHtml;
  resultEl.classList.add('visible');
}

// Initialisation
populateGrid();
</script>
</body>
</html>