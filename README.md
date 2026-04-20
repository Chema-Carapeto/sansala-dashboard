<!DOCTYPE html>

<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Sansala · Dashboard S16 · 2026</title>
<style>
:root{
  --bg:#f4f6f9;--bg2:#ffffff;--bg3:#f0f3f8;--bg4:#e8ecf2;
  --text:#0f172a;--text2:#475569;--text3:#94a3b8;
  --up:#059669;--down:#dc2626;--warn:#d97706;
  --brand:#0e9e72;--brand-soft:rgba(14,158,114,.10);
  --border:rgba(15,23,42,.07);--border2:rgba(15,23,42,.13);
  --r:12px;--r2:16px;
  --shadow:0 1px 4px rgba(15,23,42,.06),0 0 0 1px rgba(15,23,42,.04);
}
*{box-sizing:border-box;margin:0;padding:0}
body{background:var(--bg);color:var(--text);font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',system-ui,sans-serif;font-size:14px;line-height:1.5;-webkit-font-smoothing:antialiased;max-width:430px;margin:0 auto;min-height:100vh;padding-bottom:80px}

/* HEADER */
.hd{background:var(–bg2);padding:14px 16px 0;border-bottom:1px solid var(–border);position:sticky;top:0;z-index:100;box-shadow:0 1px 8px rgba(15,23,42,.06)}
.hd-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px}
.logo{display:flex;align-items:center;gap:10px}
.logo-icon{width:34px;height:34px;background:var(–brand);border-radius:10px;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:16px;color:#fff;box-shadow:0 2px 8px rgba(14,158,114,.3)}
.logo-name{font-size:15px;font-weight:700;color:var(–text);letter-spacing:-.3px}
.logo-sub{font-size:10px;color:var(–text3);margin-top:1px}
.badge{background:var(–brand-soft);color:var(–brand);font-size:10px;font-weight:600;padding:3px 8px;border-radius:20px;letter-spacing:.4px;text-transform:uppercase;border:1px solid rgba(14,158,114,.2)}
.tabs{display:flex;overflow-x:auto;-webkit-overflow-scrolling:touch;scrollbar-width:none}
.tabs::-webkit-scrollbar{display:none}
.tab{padding:9px 11px;font-size:11px;font-weight:600;color:var(–text3);border-bottom:2px solid transparent;white-space:nowrap;cursor:pointer;-webkit-tap-highlight-color:transparent;flex-shrink:0;transition:color .15s}
.tab.active{color:var(–brand);border-bottom-color:var(–brand)}

/* CONTENT */
.pane{padding:14px;display:none;gap:11px;flex-direction:column}
.pane.active{display:flex}
.slabel{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.8px;color:var(–text3);margin-bottom:2px;padding-left:2px}

/* KPI GRID */
.kgrid{display:grid;grid-template-columns:1fr 1fr;gap:9px}
.kcard{background:var(–bg2);border-radius:var(–r2);padding:13px 13px 11px;box-shadow:var(–shadow);position:relative;overflow:hidden}
.kcard::before{content:’’;position:absolute;top:0;left:0;right:0;height:3px;background:var(–brand);border-radius:3px 3px 0 0}
.kcard.warn::before{background:var(–warn)}
.kcard.down::before{background:var(–down)}
.klbl{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:var(–text3);margin-bottom:5px}
.kval{font-size:21px;font-weight:700;color:var(–text);letter-spacing:-.5px;line-height:1.1}
.ksub{font-size:11px;color:var(–text3);margin-top:3px}
.kdelta{display:inline-flex;align-items:center;gap:3px;font-size:11px;font-weight:600;padding:2px 7px;border-radius:8px;margin-top:5px}
.kdelta.up{background:rgba(5,150,105,.1);color:var(–up)}
.kdelta.dn{background:rgba(220,38,38,.1);color:var(–down)}

/* CARD */
.card{background:var(–bg2);border-radius:var(–r2);padding:13px;box-shadow:var(–shadow)}
.ctitle{font-size:11px;font-weight:700;color:var(–text2);text-transform:uppercase;letter-spacing:.4px;margin-bottom:11px;display:flex;align-items:center;justify-content:space-between}
.ctitle span{font-size:10px;font-weight:500;color:var(–text3);text-transform:none;letter-spacing:0}

/* CHIPS */
.chips{display:flex;gap:10px}
.chip{flex:1;background:var(–bg3);border-radius:10px;padding:9px 10px;text-align:center}
.chip .cv{font-size:15px;font-weight:700;color:var(–text);letter-spacing:-.4px}
.chip .cl{font-size:10px;color:var(–text3);font-weight:600;text-transform:uppercase;letter-spacing:.4px;margin-top:2px}

/* CANAL / ROW ITEMS */
.row{padding:9px 0;border-bottom:1px solid var(–border)}
.row:last-child{border-bottom:none}
.r1{display:flex;align-items:center;justify-content:space-between;margin-bottom:4px}
.rname{font-size:12px;font-weight:600;color:var(–text);flex:1;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;margin-right:8px}
.reur{font-size:13px;font-weight:700;color:var(–text);white-space:nowrap;font-variant-numeric:tabular-nums}
.r2{display:flex;align-items:center;gap:7px}
.bwrap{flex:1;height:5px;background:var(–bg3);border-radius:3px;overflow:hidden}
.bfill{height:100%;border-radius:3px;background:var(–brand);transition:width .4s}
.rshare{font-size:10px;color:var(–text3);font-weight:600;white-space:nowrap;min-width:30px;text-align:right}
.rdelta{font-size:10px;font-weight:700;white-space:nowrap;min-width:46px;text-align:right}
.rdelta.up{color:var(–up)}.rdelta.dn{color:var(–down)}

/* CHART */
.cwrap{width:100%;height:110px;position:relative}
.cwrap svg{width:100%;height:100%}
.clabels{display:flex;justify-content:space-between;margin-top:3px;padding:0 2px}
.clabels span{font-size:9px;color:var(–text3);font-weight:500}

/* PRODUCTOS */
.pitem{padding:8px 0;border-bottom:1px solid var(–border)}
.pitem:last-child{border-bottom:none}
.p1{display:flex;align-items:flex-start;justify-content:space-between;gap:8px;margin-bottom:4px}
.prank{font-size:10px;font-weight:700;color:var(–text3);min-width:16px;padding-top:1px}
.pname{flex:1;font-size:12px;font-weight:600;color:var(–text);line-height:1.3}
.pval{font-size:12px;font-weight:700;color:var(–text);white-space:nowrap;font-variant-numeric:tabular-nums}
.pbwrap{margin-left:22px;height:4px;background:var(–bg3);border-radius:3px;overflow:hidden}
.pbfill{height:100%;border-radius:3px;background:var(–brand)}
.pmeta{margin-left:22px;font-size:10px;color:var(–text3);margin-top:3px}

/* TOGGLE */
.tgroup{display:flex;gap:3px;background:var(–bg3);border-radius:8px;padding:3px}
.tbtn{flex:1;padding:4px 6px;font-size:10px;font-weight:600;color:var(–text3);border:none;background:transparent;border-radius:6px;cursor:pointer;-webkit-tap-highlight-color:transparent}
.tbtn.active{background:var(–bg2);color:var(–brand);box-shadow:0 1px 3px rgba(15,23,42,.1)}

/* ANUAL */
.ybars{display:flex;flex-direction:column;gap:9px}
.yrow{display:flex;align-items:center;gap:9px}
.ylbl{font-size:12px;font-weight:700;color:var(–text2);width:34px;flex-shrink:0}
.ybwrap{flex:1;height:20px;background:var(–bg3);border-radius:6px;overflow:hidden}
.ybar{height:100%;border-radius:6px;display:flex;align-items:center;padding-left:7px;font-size:10px;font-weight:700;color:#fff;transition:width .6s}
.yval{font-size:11px;font-weight:700;color:var(–text);white-space:nowrap;min-width:64px;text-align:right}

/* NOTAS */
.note{background:var(–brand-soft);border:1px solid rgba(14,158,114,.2);border-radius:10px;padding:9px 12px;font-size:11px;color:var(–brand);font-weight:500;line-height:1.45}
.anote{background:rgba(220,38,38,.05);border:1px solid rgba(220,38,38,.2);border-left:3px solid var(–down);border-radius:10px;padding:9px 12px;font-size:11px;color:var(–down);font-weight:500;line-height:1.45}

/* MERCADO POTENCIAL */
.mpgrid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:7px}
.mpkpi{background:var(–bg2);border-radius:var(–r);padding:9px 9px 7px;box-shadow:var(–shadow);text-align:center}
.mpkval{font-size:15px;font-weight:700;letter-spacing:-.4px}
.mpklbl{font-size:9px;color:var(–text3);font-weight:600;text-transform:uppercase;letter-spacing:.4px;margin-top:2px}
.fchips{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:3px}
.fchip{padding:4px 9px;border-radius:20px;font-size:10px;font-weight:600;background:var(–bg3);color:var(–text2);cursor:pointer;border:1px solid var(–border2);-webkit-tap-highlight-color:transparent}
.fchip.active{background:var(–brand);color:#fff;border-color:var(–brand)}
.pitem2{padding:9px 0;border-bottom:1px solid var(–border)}
.pitem2:last-child{border-bottom:none}
.pp1{display:flex;align-items:flex-start;justify-content:space-between;gap:8px;margin-bottom:4px}
.pn{font-size:12px;font-weight:700;color:var(–text);flex:1;line-height:1.3}
.pacc{font-size:12px;font-weight:700;color:var(–brand);white-space:nowrap}
.pp2{display:flex;align-items:center;gap:5px;flex-wrap:wrap}
.badge2{font-size:9px;font-weight:700;padding:2px 7px;border-radius:10px;text-transform:uppercase;letter-spacing:.3px}
.bhot{background:rgba(220,38,38,.1);color:var(–down)}
.bwarm{background:rgba(217,119,6,.1);color:var(–warn)}
.bcold{background:var(–bg3);color:var(–text3)}
.bsect{background:var(–brand-soft);color:var(–brand)}
.pprob{font-size:9px;color:var(–text3);font-weight:600}
.fbar{height:4px;background:var(–bg3);border-radius:3px;overflow:hidden;flex:1}
.fbfill{height:100%;border-radius:3px}

/* NAV */
.bnav{position:fixed;bottom:0;left:0;right:0;max-width:430px;margin:0 auto;background:var(–bg2);border-top:1px solid var(–border);display:flex;padding:0 4px;padding-bottom:env(safe-area-inset-bottom,0px);z-index:200;box-shadow:0 -2px 10px rgba(15,23,42,.06)}
.ni{flex:1;padding:9px 2px 7px;display:flex;flex-direction:column;align-items:center;gap:2px;cursor:pointer;-webkit-tap-highlight-color:transparent}
.ni:active{opacity:.7}
.nico{font-size:17px;line-height:1}
.nlbl{font-size:9px;font-weight:600;color:var(–text3);letter-spacing:.3px;text-transform:uppercase}
.ni.active .nlbl{color:var(–brand)}
</style>

</head>
<body>

<div class="hd">
  <div class="hd-top">
    <div class="logo">
      <div class="logo-icon">S</div>
      <div>
        <div class="logo-name">Sansala</div>
        <div class="logo-sub">Dashboard Comercial</div>
      </div>
    </div>
    <div class="badge">S16 · 2026</div>
  </div>
  <div class="tabs" id="tabs">
    <div class="tab active" data-tab="resumen">Resumen</div>
    <div class="tab" data-tab="tendencia">Tendencia</div>
    <div class="tab" data-tab="canales">Canales</div>
    <div class="tab" data-tab="productos">Productos</div>
    <div class="tab" data-tab="mercado">Pipeline</div>
    <div class="tab" data-tab="anual">Anual</div>
  </div>
</div>

<!-- RESUMEN -->

<div class="pane active" id="tab-resumen">
  <div class="note">📊 Datos hasta S16 · YTD 2026 vs mismo periodo 2025 · Margen est. 27,7%</div>
  <div>
    <div class="slabel">KPIs · YTD S1–S16 · 2026</div>
    <div class="kgrid">
      <div class="kcard">
        <div class="klbl">Facturación</div>
        <div class="kval">2,69M</div>
        <div class="ksub">€ acumulado</div>
        <div class="kdelta up">▲ +23,1%</div>
      </div>
      <div class="kcard">
        <div class="klbl">Unidades</div>
        <div class="kval">1,19M</div>
        <div class="ksub">uds. acumuladas</div>
        <div class="kdelta up">▲ vs 2025</div>
      </div>
      <div class="kcard">
        <div class="klbl">€ / Unidad</div>
        <div class="kval">2,25€</div>
        <div class="ksub">precio medio</div>
        <div class="kdelta up">▲ mix premium</div>
      </div>
      <div class="kcard warn">
        <div class="klbl">Mejor semana</div>
        <div class="kval">251K€</div>
        <div class="ksub">S15 · récord</div>
        <div class="kdelta up">▲ S16: 233K</div>
      </div>
    </div>
  </div>
  <div>
    <div class="slabel">Comparativa YTD vs 2025</div>
    <div class="card">
      <div class="ctitle">S1–S16 <span>mismo periodo</span></div>
      <div class="chips">
        <div class="chip"><div class="cv">2,69M€</div><div class="cl">2026</div></div>
        <div class="chip" style="background:var(--bg3)"><div class="cv" style="color:var(--text2)">2,18M€</div><div class="cl">2025</div></div>
        <div class="chip" style="background:rgba(5,150,105,.08)"><div class="cv" style="color:var(--up)">+504K€</div><div class="cl">Dif.</div></div>
      </div>
    </div>
  </div>
  <div>
    <div class="slabel">Top Canales · >50K€</div>
    <div class="card">
      <div class="row">
        <div class="r1"><div class="rname">🛒 Retail</div><div class="reur">1.072K€</div></div>
        <div class="r2"><div class="bwrap"><div class="bfill" style="width:100%"></div></div><div class="rshare">40,2%</div><div class="rdelta up">+67,6%</div></div>
      </div>
      <div class="row">
        <div class="r1"><div class="rname">✈️ Travel Channel</div><div class="reur">599K€</div></div>
        <div class="r2"><div class="bwrap"><div class="bfill" style="width:55.9%;background:var(--warn)"></div></div><div class="rshare">22,4%</div><div class="rdelta dn">−39,1%</div></div>
      </div>
      <div class="row">
        <div class="r1"><div class="rname">🛫 Travel Retail</div><div class="reur">356K€</div></div>
        <div class="r2"><div class="bwrap"><div class="bfill" style="width:33.2%"></div></div><div class="rshare">13,4%</div><div class="rdelta up">+70,1%</div></div>
      </div>
      <div class="row">
        <div class="r1"><div class="rname">🏫 Colectividades</div><div class="reur">258K€</div></div>
        <div class="r2"><div class="bwrap"><div class="bfill" style="width:24.1%"></div></div><div class="rshare">9,7%</div><div class="rdelta up">+302%</div></div>
      </div>
    </div>
  </div>
  <div class="anote">⚠️ Travel Channel −39,1% YTD (−385K€). Vigilar: ¿pérdida de cuenta o referencia? S14 afectada por Semana Santa (38K€).</div>
</div>

<!-- TENDENCIA -->

<div class="pane" id="tab-tendencia">
  <div class="card">
    <div class="ctitle">Facturación semanal 2026 <span>vs 2025</span></div>
    <div class="cwrap" id="chart-sem"></div>
    <div class="clabels"><span>S1</span><span>S3</span><span>S5</span><span>S7</span><span>S9</span><span>S11</span><span>S13</span><span>S15</span></div>
  </div>
  <div class="note">📈 S14 baja a 38K€ por Semana Santa. S15 récord con 251K€. Media normal: 186K€/sem.</div>
  <div>
    <div class="slabel">Detalle semana a semana</div>
    <div class="card"><div class="ctitle">2026 <span>€ / Uds</span></div><div id="weekly-detail"></div></div>
  </div>
</div>

<!-- CANALES -->

<div class="pane" id="tab-canales">
  <div class="note">Solo canales ≥50K€ YTD.</div>
  <div class="card">
    <div class="ctitle">Canales · YTD S1–S16 · 2026 <span>vs 2025</span></div>
    <div id="canal-list"></div>
  </div>
  <div class="anote">⚠️ Travel Channel −39,1% (−385K€). Investigar si es pérdida de referencia o de cuenta.</div>
  <div>
    <div class="slabel">Distribución 2026</div>
    <div class="card"><div class="cwrap" id="chart-canal" style="height:130px"></div></div>
  </div>
</div>

<!-- PRODUCTOS -->

<div class="pane" id="tab-productos">
  <div>
    <div class="slabel">Vista</div>
    <div class="tgroup" id="prod-toggle">
      <button class="tbtn active" data-view="eur">€ Total</button>
      <button class="tbtn" data-view="ups">€/sem</button>
      <button class="tbtn" data-view="uds_sem">Uds/sem</button>
      <button class="tbtn" data-view="uds_dia">Uds/día</button>
    </div>
  </div>
  <div class="card">
    <div class="ctitle">Top Productos · S1–S16 · 2026 <span id="prod-sub">por facturación</span></div>
    <div id="prod-list"></div>
  </div>
  <div>
    <div class="slabel">Portafolio</div>
    <div class="chips">
      <div class="chip"><div class="cv">232</div><div class="cl">SKUs activos</div></div>
      <div class="chip"><div class="cv">2,25€</div><div class="cl">Precio medio</div></div>
      <div class="chip"><div class="cv">38%</div><div class="cl">Top5 conc.</div></div>
    </div>
  </div>
  <div class="note">🥗 Poke de Salmón lidera (215K€ · 4,01€/ud). Ensalada César top en volumen (997 uds/día).</div>
</div>

<!-- PIPELINE -->

<div class="pane" id="tab-mercado">
  <div>
    <div class="slabel">Pipeline captación · 2026</div>
    <div class="mpgrid">
      <div class="mpkpi"><div class="mpkval" style="color:var(--text)">11,7M€</div><div class="mpklbl">Potencial</div></div>
      <div class="mpkpi"><div class="mpkval" style="color:var(--brand)">2,77M€</div><div class="mpklbl">Accesible</div></div>
      <div class="mpkpi"><div class="mpkval" style="color:var(--warn)">63</div><div class="mpklbl">Prospectos</div></div>
    </div>
  </div>
  <div>
    <div class="slabel">Filtrar</div>
    <div class="fchips" id="sector-chips">
      <div class="fchip active" data-sector="TODOS">Todos</div>
      <div class="fchip" data-sector="TRAVEL RETAIL">Travel</div>
      <div class="fchip" data-sector="RETAIL">Retail</div>
      <div class="fchip" data-sector="HORECA ORGANIZADA">Horeca</div>
      <div class="fchip" data-sector="COLECTIVIDADES">Colect.</div>
      <div class="fchip" data-sector="PETROL">Petrol</div>
    </div>
  </div>
  <div class="card">
    <div class="ctitle">Prospectos <span id="mp-count">63 clientes</span></div>
    <div id="prospect-list"></div>
  </div>
  <div class="note">💡 Competidores: BSF (9 cuentas), Obrador Propio (21), Campofrio (5).</div>
</div>

<!-- ANUAL -->

<div class="pane" id="tab-anual">
  <div class="note">📅 2026: S1–S16. Proyección excl. S1 y S14 (atípicas).</div>
  <div>
    <div class="slabel">Facturación anual</div>
    <div class="card">
      <div class="ctitle">EUR · Total año</div>
      <div class="ybars">
        <div class="yrow"><div class="ylbl">2024</div><div class="ybwrap"><div class="ybar" style="width:82%;background:var(--text3)">7,2M</div></div><div class="yval">7,17M€</div></div>
        <div class="yrow"><div class="ylbl">2025</div><div class="ybwrap"><div class="ybar" style="width:100%;background:var(--brand)">8,8M</div></div><div class="yval">8,78M€</div></div>
        <div class="yrow"><div class="ylbl" style="color:var(--brand)">2026</div><div class="ybwrap"><div class="ybar" style="width:31%;background:rgba(14,158,114,.5)">S16</div></div><div class="yval" style="color:var(--brand)">2,69M€</div></div>
        <div class="yrow"><div class="ylbl" style="color:var(--warn)">Proy.</div><div class="ybwrap"><div class="ybar" style="width:97%;background:rgba(217,119,6,.5)">~9,7M</div></div><div class="yval" style="color:var(--warn)">≈9,7M€</div></div>
      </div>
    </div>
  </div>
  <div>
    <div class="slabel">Crecimiento interanual</div>
    <div class="kgrid">
      <div class="kcard"><div class="klbl">2024→2025</div><div class="kval">+22,4%</div><div class="ksub">EUR total año</div><div class="kdelta up">▲</div></div>
      <div class="kcard"><div class="klbl">2026 YTD</div><div class="kval">+23,1%</div><div class="ksub">vs 2025 S1-S16</div><div class="kdelta up">▲</div></div>
    </div>
  </div>
</div>

<!-- BOTTOM NAV -->

<nav class="bnav" id="bnav">
  <div class="ni active" data-tab="resumen"><div class="nico">📊</div><div class="nlbl">Resumen</div></div>
  <div class="ni" data-tab="tendencia"><div class="nico">📈</div><div class="nlbl">Tendencia</div></div>
  <div class="ni" data-tab="canales"><div class="nico">🏪</div><div class="nlbl">Canales</div></div>
  <div class="ni" data-tab="productos"><div class="nico">🥗</div><div class="nlbl">Productos</div></div>
  <div class="ni" data-tab="mercado"><div class="nico">🎯</div><div class="nlbl">Pipeline</div></div>
  <div class="ni" data-tab="anual"><div class="nico">📅</div><div class="nlbl">Anual</div></div>
</nav>

<script>
const W26=[{w:1,e:40029,u:17463},{w:2,e:150024,u:70940},{w:3,e:169221,u:77823},{w:4,e:152113,u:80380},{w:5,e:166049,u:79849},{w:6,e:175058,u:82700},{w:7,e:148356,u:67707},{w:8,e:173103,u:80230},{w:9,e:182501,u:81818},{w:10,e:194455,u:81067},{w:11,e:200411,u:80260},{w:12,e:186082,u:80240},{w:13,e:225936,u:95683},{w:14,e:38464,u:14135},{w:15,e:251060,u:106040},{w:16,e:232743,u:97747}];
const W25=[120717,108942,146850,127426,143008,138983,128245,131279,181625,146616,136673,137709,129428,129742,154140,120235];
const CANALES=[{n:'Retail',ic:'🛒',e:1072282,e25:639781,sh:40.2,u:416261},{n:'Travel Channel',ic:'✈️',e:599014,e25:983981,sh:22.4,u:372276},{n:'Travel Retail',ic:'🛫',e:356407,e25:209537,sh:13.4,u:145373},{n:'Colectividades',ic:'🏫',e:258327,e25:64284,sh:9.7,u:93094},{n:'Petrol',ic:'⛽',e:150604,e25:6831,sh:5.6,u:57817},{n:'Horeca Org.',ic:'🍽️',e:124127,e25:94039,sh:4.7,u:52353},{n:'Vending',ic:'🎰',e:108111,e25:99057,sh:4.1,u:51438}];
const PRODS=[{n:'Poke de Salmón',e:215492,u:53799,s:15,p:4.01},{n:'Ensalada César',e:190139,u:74836,s:15,p:2.54},{n:'Wrap Salmón Marinado ASC',e:152339,u:57704,s:16,p:2.64},{n:'Ensalada Pasta y Pollo',e:140814,u:51068,s:15,p:2.76},{n:'Pasta Genovesa',e:77227,u:31050,s:16,p:2.49},{n:'Ensalada Cantábrica',e:75749,u:28412,s:15,p:2.67},{n:'Panini Pollo Mostaza',e:67328,u:34508,s:13,p:1.95},{n:'Schiacciata Paleta Ibérica',e:53407,u:22630,s:13,p:2.36},{n:'Wrap Pollo Curry',e:53275,u:26264,s:16,p:2.03},{n:'Serranito con Cinta Lomo',e:48636,u:9792,s:7,p:4.97},{n:'César Pollo Crujiente',e:47367,u:15770,s:13,p:3.00},{n:'Brioche Mixto Fiambre Pavo',e:45277,u:50400,s:11,p:0.90},{n:'Sándwich Club de Pollo',e:40608,u:21600,s:7,p:1.88},{n:'Bloomer Tostado Fiambre Pavo',e:37301,u:27030,s:15,p:1.38},{n:'Especial de Atún',e:30872,u:15470,s:16,p:2.00}];
const PROSPECTOS=[{n:'CAMPOFRIO',sit:'CERRANDO CONTRATO',prob:1.00,pot:900000,acc:900000,sec:'HORECA ORGANIZADA',comp:'EUROPASTRY'},{n:'AREAS',sit:'NUEVOS PROYECTOS',prob:0.10,pot:1080000,acc:108000,sec:'TRAVEL RETAIL',comp:'BSF'},{n:'HUNGRY CLUB',sit:'PDTE RECETAS',prob:0.20,pot:1000000,acc:200000,sec:'TRAVEL RETAIL',comp:'OBRADOR PROPIO'},{n:'EROSKI ULTRAFRESCO',sit:'ENSALADAS CAPRABO',prob:0.75,pot:450000,acc:337500,sec:'RETAIL',comp:'FLORETTE'},{n:'CARREFOUR',sit:'BARECA EN CURSO',prob:0.75,pot:300000,acc:225000,sec:'RETAIL',comp:'NADIE'},{n:'LIDL',sit:'PILOTO EN CURSO',prob:0.40,pot:600000,acc:240000,sec:'RETAIL',comp:'NO'},{n:'EUROMADI',sit:'PROPUESTA PRESENTADA',prob:0.30,pot:400000,acc:120000,sec:'RETAIL',comp:'—'},{n:'GRANIER',sit:'PROPUESTA PRESENTADA',prob:0.30,pot:200000,acc:60000,sec:'HORECA ORGANIZADA',comp:'OBRADOR PROPIO'},{n:'LEGENDS',sit:'REUNIÓN SEPTIEMBRE',prob:0.10,pot:400000,acc:40000,sec:'COLECTIVIDADES',comp:'OBRADOR PROPIO'},{n:'VEGALSA',sit:'PILOTO EN CURSO',prob:0.20,pot:200000,acc:40000,sec:'RETAIL',comp:'OBRADOR PROPIO'},{n:'GAP CONSULTING',sit:'PROPUESTA PRESENTADA',prob:0.50,pot:100000,acc:50000,sec:'TRAVEL CHANNEL',comp:'—'},{n:'EIS MARITIMO',sit:'PROPUESTA PRESENTADA',prob:0.20,pot:200000,acc:40000,sec:'TRAVEL CHANNEL',comp:'—'},{n:'SHELL',sit:'PROPUESTA PRESENTADA',prob:0.20,pot:80000,acc:16000,sec:'PETROL',comp:'—'},{n:'LA VITORIANA',sit:'PROPUESTA PRESENTADA',prob:0.50,pot:60000,acc:30000,sec:'HORECA ORGANIZADA',comp:'OBRADOR PROPIO'},{n:'MC CAFFE',sit:'CONTACTADOS',prob:0.05,pot:1000000,acc:50000,sec:'HORECA ORGANIZADA',comp:'—'},{n:'IBERSOL',sit:'BUSCAR REUNIÓN',prob:0.05,pot:300000,acc:15000,sec:'TRAVEL RETAIL',comp:'OBRADOR PROPIO'},{n:'OKIN',sit:'PROPUESTA PRESENTADA',prob:0.40,pot:40000,acc:16000,sec:'DISTRIBUIDORES',comp:'—'},{n:'PLAZA',sit:'PDTE REUNIÓN',prob:0.50,pot:80000,acc:40000,sec:'RETAIL',comp:'LM'},{n:'FUNDACION JUAN XXIII',sit:'PROPUESTA PRESENTADA',prob:0.30,pot:30000,acc:9000,sec:'HORECA ORGANIZADA',comp:'OBRADOR PROPIO'},{n:'COMESS GROUP',sit:'MUESTRAS ENTREGADAS',prob:0.05,pot:400000,acc:20000,sec:'HORECA ORGANIZADA',comp:'ARTE Y SANO'},{n:'LEVADURA MADRE',sit:'OFERTA ENSALADAS',prob:0.05,pot:400000,acc:20000,sec:'HORECA ORGANIZADA',comp:'—'},{n:'DO EAT',sit:'RETOMAR CONTACTO',prob:0.10,pot:170000,acc:17000,sec:'HORECA ORGANIZADA',comp:'OBRADOR PROPIO'},{n:'VILAPLANA COMPASS',sit:'REUNIÓN SEPTIEMBRE',prob:0.05,pot:200000,acc:10000,sec:'COLECTIVIDADES',comp:'BSF'},{n:'SACYR',sit:'PROPUESTA PRESENTADA',prob:0.05,pot:100000,acc:5000,sec:'TRAVEL RETAIL',comp:'BSF'},{n:'SSP',sit:'CONTACTADOS',prob:0.05,pot:100000,acc:5000,sec:'TRAVEL RETAIL',comp:'BSF'},{n:'OBRADOR 365',sit:'150 TIENDAS BCN',prob:0.10,pot:200000,acc:20000,sec:'HORECA ORGANIZADA',comp:'OBRADOR PROPIO'},{n:'AMETLLER ORIGEN',sit:'PDTE REUNIÓN',prob:0.05,pot:400000,acc:20000,sec:'RETAIL',comp:'CUINA JUSTA'},{n:'GRUPO NAZABAL',sit:'PROPUESTA PRESENTADA',prob:0.20,pot:40000,acc:8000,sec:'HORECA ORGANIZADA',comp:'BSF'},{n:'SCRUP',sit:'RETOMAR CONTACTO',prob:0.05,pot:100000,acc:5000,sec:'RETAIL',comp:'—'},{n:'PLAZA PETROL',sit:'PROPUESTA PRESENTADA',prob:0.05,pot:30000,acc:1500,sec:'PETROL',comp:'—'}];

const fmt=n=>n>=1000000?(n/1e6).toFixed(1)+'M':n>=1000?Math.round(n/1000)+'K':Math.round(n)+'';
const fmtN=n=>new Intl.NumberFormat('es-ES').format(Math.round(n));

// TABS
function goTab(name){
  document.querySelectorAll('.tab').forEach(t=>t.classList.toggle('active',t.dataset.tab===name));
  document.querySelectorAll('.pane').forEach(p=>p.classList.toggle('active',p.id==='tab-'+name));
  document.querySelectorAll('.ni').forEach(n=>n.classList.toggle('active',n.dataset.tab===name));
  if(name==='tendencia')setTimeout(renderSpark,50);
  if(name==='canales')setTimeout(renderDonut,50);
}
document.querySelectorAll('[data-tab]').forEach(el=>el.addEventListener('click',()=>goTab(el.dataset.tab)));

// SPARKLINE
let spDone=false;
function renderSpark(){
  if(spDone)return;
  const wrap=document.getElementById('chart-sem');
  const W=wrap.clientWidth||340,H=110,pl=30,pr=8,pt=10,pb=8;
  const iW=W-pl-pr,iH=H-pt-pb;
  const maxV=Math.max(...W26.map(d=>d.e),...W25)*1.02;
  const xS=i=>pl+(i/(W26.length-1))*iW;
  const yS=v=>pt+iH-(v/maxV)*iH;
  const pts26=W26.map((d,i)=>`${xS(i)},${yS(d.e)}`).join(' ');
  const pts25=W25.map((v,i)=>`${xS(i)},${yS(v)}`).join(' ');
  const area=`M${xS(0)},${yS(W26[0].e)} L${pts26} L${xS(15)},${pt+iH} L${xS(0)},${pt+iH} Z`;
  const grid=[50000,100000,150000,200000,250000].map(v=>v<=maxV?`<line x1="${pl}" y1="${yS(v)}" x2="${W-pr}" y2="${yS(v)}" stroke="#e2e8f0" stroke-width="1"/><text x="${pl-4}" y="${yS(v)+3}" font-size="8" fill="#94a3b8" text-anchor="end">${v/1000}K</text>`:'').join('');
  const maxE=Math.max(...W26.map(d=>d.e));
  const marks=W26.map((d,i)=>{
    if(d.w===14)return`<circle cx="${xS(i)}" cy="${yS(d.e)}" r="3" fill="#dc2626" stroke="#fff" stroke-width="1.5"/><text x="${xS(i)}" y="${yS(d.e)-6}" font-size="7" fill="#dc2626" text-anchor="middle">SS</text>`;
    if(d.e===maxE)return`<circle cx="${xS(i)}" cy="${yS(d.e)}" r="4" fill="#0e9e72" stroke="#fff" stroke-width="2"/><text x="${xS(i)}" y="${yS(d.e)-8}" font-size="8" fill="#0e9e72" text-anchor="middle" font-weight="700">${fmt(d.e)}</text>`;
    return'';
  }).join('');
  wrap.innerHTML=`<svg viewBox="0 0 ${W} ${H}" preserveAspectRatio="none"><defs><linearGradient id="g" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stop-color="#0e9e72" stop-opacity=".16"/><stop offset="100%" stop-color="#0e9e72" stop-opacity=".02"/></linearGradient></defs>${grid}<path d="${area}" fill="url(#g)"/><polyline points="${pts25}" fill="none" stroke="#cbd5e1" stroke-width="1.5" stroke-dasharray="4,2"/><polyline points="${pts26}" fill="none" stroke="#0e9e72" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>${marks}</svg>`;
  spDone=true;
}

// WEEKLY DETAIL
(function(){
  const el=document.getElementById('weekly-detail');
  const mx=Math.max(...W26.map(d=>d.e));
  el.innerHTML=W26.map((d,i)=>{
    const e25=W25[i]||0,dt=e25>0?((d.e/e25)-1)*100:0,isMx=d.e===mx,isSS=d.w===14;
    const lbl=isSS?`S${d.w} 🌴 S.Santa`:`S${d.w}${isMx?' 🏆':''}`;
    const bw=Math.round(d.e/mx*100);
    return`<div class="row"><div class="r1"><div class="rname" style="${isMx?'color:var(--brand);font-weight:700':isSS?'color:var(--warn)':''}">${lbl}</div><div class="reur">${fmtN(d.e)}€</div></div><div class="r2"><div class="bwrap"><div class="bfill" style="width:${bw}%;background:${isMx?'var(--brand)':isSS?'var(--warn)':'rgba(14,158,114,.5)'}"></div></div><div class="rshare">${fmt(d.u)} uds</div><div class="rdelta ${dt>=0?'up':'dn'}">${dt>=0?'+':''}${dt.toFixed(0)}%</div></div></div>`;
  }).join('');
})();

// CANAL LIST
(function(){
  const el=document.getElementById('canal-list');
  const mx=CANALES[0].e;
  el.innerHTML=CANALES.map(c=>{
    const dt=c.e25>0?((c.e/c.e25)-1)*100:9999;
    const bw=Math.round(c.e/mx*100);
    const ds=dt>999?'+2.1K%':`${dt>=0?'+':''}${dt.toFixed(0)}%`;
    return`<div class="row"><div class="r1"><div class="rname">${c.ic} ${c.n}</div><div class="reur">${fmtN(c.e)}€</div></div><div class="r2"><div class="bwrap"><div class="bfill" style="width:${bw}%;background:${dt<0?'var(--warn)':'var(--brand)'}"></div></div><div class="rshare">${c.sh}%</div><div class="rdelta ${dt<0?'dn':'up'}">${ds}</div></div></div>`;
  }).join('');
})();

// DONUT
let donutDone=false;
function renderDonut(){
  if(donutDone)return;
  const el=document.getElementById('chart-canal');
  const W=el.clientWidth||340,H=130;
  const cx=W*0.27,cy=H/2,r=Math.min(W*0.54,H)/2-10;
  const tot=CANALES.reduce((s,c)=>s+c.e,0);
  const cols=['#0e9e72','#f59e0b','#3b82f6','#8b5cf6','#ef4444','#06b6d4','#ec4899'];
  let ang=-Math.PI/2,paths='';
  CANALES.forEach((c,i)=>{
    const a=(c.e/tot)*Math.PI*2;
    const x1=cx+r*Math.cos(ang),y1=cy+r*Math.sin(ang);
    const x2=cx+r*Math.cos(ang+a),y2=cy+r*Math.sin(ang+a);
    const ma=ang+a/2,lx=cx+(r*.65)*Math.cos(ma),ly=cy+(r*.65)*Math.sin(ma);
    const pct=Math.round(c.e/tot*100);
    paths+=`<path d="M${cx},${cy} L${x1},${y1} A${r},${r} 0 ${a>Math.PI?1:0},1 ${x2},${y2} Z" fill="${cols[i]}" stroke="#fff" stroke-width="1.5"/>`;
    if(pct>=6)paths+=`<text x="${lx}" y="${ly+3}" font-size="9" fill="#fff" text-anchor="middle" font-weight="700">${pct}%</text>`;
    ang+=a;
  });
  const leg=CANALES.map((c,i)=>`<div style="display:flex;align-items:center;gap:4px;font-size:10px;color:var(--text2)"><span style="width:8px;height:8px;border-radius:2px;background:${cols[i]};flex-shrink:0;display:inline-block"></span>${c.n.length>12?c.n.slice(0,12)+'…':c.n}</div>`).join('');
  el.innerHTML=`<div style="display:flex;align-items:center;gap:8px"><svg viewBox="0 0 ${W*.54} ${H}" width="${W*.54}" height="${H}">${paths}</svg><div style="flex:1;display:grid;gap:4px">${leg}</div></div>`;
  donutDone=true;
}

// PRODUCTOS TOGGLE
let prodView='eur';
function renderProds(v){
  const el=document.getElementById('prod-list');
  const sub=document.getElementById('prod-sub');
  let getV,getMeta,title;
  if(v==='ups'){getV=p=>p.e/p.s;getMeta=p=>`${fmtN(p.e/p.s)}€/sem · ${p.s} sem`;title='por €/semana activa';}
  else if(v==='uds_sem'){getV=p=>p.u/p.s;getMeta=p=>`${Math.round(p.u/p.s).toLocaleString('es-ES')} uds/sem · ${p.s} sem`;title='por uds/semana activa';}
  else if(v==='uds_dia'){getV=p=>p.u/p.s/5;getMeta=p=>`${(p.u/p.s/5).toFixed(0)} uds/día · ${p.p.toFixed(2)}€/ud`;title='por uds/día';}
  else{getV=p=>p.e;getMeta=p=>`${fmtN(p.u)} uds · ${p.p.toFixed(2)}€/ud`;title='por facturación';}
  sub.textContent=title;
  const sorted=[...PRODS].sort((a,b)=>getV(b)-getV(a));
  const mx=getV(sorted[0]);
  el.innerHTML=sorted.map((p,i)=>{
    const val=getV(p),bw=Math.round(val/mx*100);
    const vs=v==='eur'?`${fmtN(p.e)}€`:v==='ups'?`${fmtN(p.e/p.s)}€/s`:v==='uds_sem'?`${Math.round(p.u/p.s).toLocaleString('es-ES')} u/s`:`${(p.u/p.s/5).toFixed(0)} u/d`;
    return`<div class="pitem"><div class="p1"><div class="prank">#${i+1}</div><div class="pname">${p.n}</div><div class="pval">${vs}</div></div><div class="pbwrap"><div class="pbfill" style="width:${bw}%"></div></div><div class="pmeta">${getMeta(p)}</div></div>`;
  }).join('');
}
document.querySelectorAll('#prod-toggle .tbtn').forEach(b=>{
  b.addEventListener('click',()=>{
    document.querySelectorAll('#prod-toggle .tbtn').forEach(x=>x.classList.remove('active'));
    b.classList.add('active');prodView=b.dataset.view;renderProds(prodView);
  });
});
renderProds('eur');

// PIPELINE
let secAct='TODOS';
function renderPros(sec){
  const el=document.getElementById('prospect-list');
  const ct=document.getElementById('mp-count');
  const lista=sec==='TODOS'?PROSPECTOS:PROSPECTOS.filter(p=>p.sec.includes(sec));
  ct.textContent=`${lista.length} clientes`;
  const mx=Math.max(...lista.map(p=>p.acc),1);
  el.innerHTML=lista.slice().sort((a,b)=>b.acc*b.prob-a.acc*a.prob).map(p=>{
    const heat=p.prob>=.5?{c:'bhot',l:'Hot 🔥'}:p.prob>=.15?{c:'bwarm',l:'Warm'}:{c:'bcold',l:'Cold'};
    const pond=Math.round(p.acc*p.prob);
    const bw=Math.round(p.acc/mx*100);
    const ss=p.sec.split(' ')[0].substring(0,8);
    return`<div class="pitem2"><div class="pp1"><div class="pn">${p.n}</div><div class="pacc">${fmt(p.acc)}€</div></div><div class="pp2"><span class="badge2 ${heat.c}">${heat.l}</span><span class="badge2 bsect">${ss}</span><span class="pprob">${Math.round(p.prob*100)}% · ~${fmt(pond)}€ pond.</span></div><div class="pp2" style="margin-top:3px"><div class="fbar"><div class="fbfill" style="width:${bw}%;background:var(--brand);opacity:.6"></div></div></div><div style="font-size:10px;color:var(--text3);margin-top:3px">${p.sit} · vs <strong>${p.comp}</strong></div></div>`;
  }).join('');
}
document.querySelectorAll('#sector-chips .fchip').forEach(c=>{
  c.addEventListener('click',()=>{
    document.querySelectorAll('#sector-chips .fchip').forEach(x=>x.classList.remove('active'));
    c.classList.add('active');secAct=c.dataset.sector;renderPros(secAct);
  });
});
renderPros('TODOS');
</script>

</body>
</html>