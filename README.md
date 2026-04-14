[index.html](https://github.com/user-attachments/files/26731089/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MetalScope — Precious Metals Arbitrage Intelligence</title>
<style>
:root {
  --gold:#C9A84C; --gold-light:#F0D080; --gold-dark:#8B6914;
  --silver:#A8B8C8; --copper:#B87333;
  --bg:#0D1117; --card:#161B22; --card2:#1C2330;
  --txt:#E6EDF3; --txt2:#8B949E;
  --green:#3FB950; --red:#F85149; --border:#30363D;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Segoe UI',system-ui,sans-serif;background:var(--bg);color:var(--txt);min-height:100vh;}

/* NAV */
nav{background:var(--card);border-bottom:1px solid var(--border);padding:0 1.5rem;display:flex;align-items:center;justify-content:space-between;height:58px;position:sticky;top:0;z-index:200;}
.logo{display:flex;align-items:center;gap:9px;font-size:1.25rem;font-weight:800;color:var(--gold);}
.logo-icon{width:30px;height:30px;background:linear-gradient(135deg,var(--gold),var(--gold-dark));border-radius:7px;display:flex;align-items:center;justify-content:center;font-size:.9rem;}
.nav-links{display:flex;gap:1.25rem;list-style:none;}
.nav-links a{color:var(--txt2);text-decoration:none;font-size:.85rem;transition:color .2s;}
.nav-links a:hover,.nav-links a.active{color:var(--gold);}
.nav-r{display:flex;gap:.6rem;align-items:center;}
.btn-out{border:1px solid var(--gold);color:var(--gold);background:transparent;padding:5px 14px;border-radius:6px;cursor:pointer;font-size:.8rem;transition:all .2s;}
.btn-out:hover{background:var(--gold);color:var(--bg);}
.btn-sol{background:var(--gold);color:var(--bg);border:none;padding:5px 14px;border-radius:6px;cursor:pointer;font-size:.8rem;font-weight:700;}
.btn-sol:hover{background:var(--gold-light);}

/* TICKER */
.ticker{background:var(--card2);border-bottom:1px solid var(--border);padding:7px 1.5rem;display:flex;gap:1.75rem;overflow-x:auto;font-size:.8rem;white-space:nowrap;}
.ti{display:flex;align-items:center;gap:7px;}
.ti-metal{font-weight:600;color:var(--txt2);}
.ti-price{font-weight:700;}
.up{color:var(--green);} .dn{color:var(--red);}
.dot{width:7px;height:7px;border-radius:50%;display:inline-block;}
.live-dot{display:inline-block;width:6px;height:6px;background:var(--green);border-radius:50%;animation:pulse 2s infinite;margin-right:3px;}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:.3;}}

/* CONTAINER */
.wrap{max-width:1420px;margin:0 auto;padding:1.25rem 1.5rem;}

/* HERO */
.hero{background:linear-gradient(135deg,#161B22,#1C2330);border:1px solid var(--border);border-radius:12px;padding:1.75rem;margin-bottom:1.25rem;display:flex;justify-content:space-between;align-items:center;gap:1rem;}
.hero h1{font-size:1.7rem;font-weight:800;background:linear-gradient(90deg,var(--gold-light),var(--gold));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;margin-bottom:.4rem;}
.hero p{color:var(--txt2);font-size:.88rem;max-width:520px;}
.hero-stats{display:flex;gap:1rem;flex-shrink:0;}
.stat{text-align:center;background:var(--bg);border:1px solid var(--border);border-radius:8px;padding:.85rem 1.25rem;min-width:100px;}
.stat-v{font-size:1.3rem;font-weight:800;color:var(--gold);}
.stat-l{font-size:.7rem;color:var(--txt2);margin-top:3px;}

/* CARDS */
.card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:1.15rem;margin-bottom:1.25rem;}
.sec-title{font-size:.95rem;font-weight:700;margin-bottom:.85rem;display:flex;align-items:center;gap:8px;}
.badge{background:var(--gold);color:var(--bg);border-radius:4px;font-size:.68rem;padding:2px 7px;font-weight:700;}

/* MAIN GRID */
.mgrid{display:grid;grid-template-columns:1fr 340px;gap:1.25rem;}

/* TABLE */
table{width:100%;border-collapse:collapse;font-size:.82rem;}
thead th{text-align:left;color:var(--txt2);font-weight:600;font-size:.72rem;text-transform:uppercase;letter-spacing:.05em;padding:7px 9px;border-bottom:1px solid var(--border);}
tbody tr{border-bottom:1px solid rgba(48,54,61,.5);transition:background .15s;}
tbody tr:hover{background:rgba(201,168,76,.05);}
tbody td{padding:9px 9px;}
.pname{font-weight:600;} .psub{font-size:.72rem;color:var(--txt2);margin-top:1px;}

.vtag{display:inline-block;padding:2px 7px;border-radius:4px;font-size:.68rem;font-weight:600;}
.ebay{background:rgba(230,100,30,.15);color:#E66420;}
.apmex{background:rgba(201,168,76,.15);color:var(--gold);}
.jmb{background:rgba(59,130,246,.15);color:#60A5FA;}
.reddit{background:rgba(255,69,0,.15);color:#FF6534;}
.lcs{background:rgba(168,178,200,.15);color:var(--silver);}
.costco{background:rgba(0,115,182,.15);color:#38BDF8;}
.sd{background:rgba(34,197,94,.15);color:#4ADE80;}

.arb-pos{font-weight:800;color:var(--green);}
.arb-neg{font-weight:800;color:var(--red);}
.abadge{display:inline-flex;align-items:center;gap:3px;padding:2px 9px;border-radius:20px;font-size:.72rem;font-weight:700;}
.ab-hot{background:rgba(63,185,80,.15);color:var(--green);border:1px solid rgba(63,185,80,.3);}
.ab-warm{background:rgba(201,168,76,.15);color:var(--gold);border:1px solid rgba(201,168,76,.3);}
.ab-cold{background:rgba(139,148,158,.1);color:var(--txt2);border:1px solid var(--border);}

/* FILTERS */
.filters{display:flex;gap:.6rem;margin-bottom:1.1rem;flex-wrap:wrap;align-items:center;}
.fl{color:var(--txt2);font-size:.8rem;}
.chip{background:var(--card2);border:1px solid var(--border);color:var(--txt2);padding:4px 12px;border-radius:20px;cursor:pointer;font-size:.78rem;transition:all .2s;}
.chip:hover{border-color:var(--gold);color:var(--gold);}
.chip.on{background:var(--gold);color:var(--bg);border-color:var(--gold);font-weight:600;}

/* TABS */
.tabs{display:flex;border-bottom:1px solid var(--border);margin-bottom:1rem;}
.tab{background:none;border:none;color:var(--txt2);padding:7px 16px;cursor:pointer;font-size:.82rem;border-bottom:2px solid transparent;transition:all .2s;font-family:inherit;}
.tab:hover{color:var(--txt);}
.tab.on{color:var(--gold);border-bottom-color:var(--gold);font-weight:600;}

/* SIDEBAR */
.spot-card{background:linear-gradient(135deg,#1C2330,#161B22);border:1px solid var(--gold-dark);border-radius:12px;padding:1.15rem;margin-bottom:1.25rem;}
.spot-row{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid rgba(48,54,61,.6);}
.spot-row:last-child{border-bottom:none;}
.spot-metal{font-weight:600;display:flex;align-items:center;gap:7px;font-size:.88rem;}
.spot-main{font-size:1rem;font-weight:700;}
.spot-ch{font-size:.72rem;}

/* PBAR */
.pbar-row{display:flex;align-items:center;gap:9px;margin-bottom:7px;font-size:.78rem;}
.pbar-lbl{width:95px;color:var(--txt2);flex-shrink:0;}
.pbar-track{flex:1;background:var(--bg);border-radius:4px;height:17px;overflow:hidden;}
.pbar-fill{height:100%;border-radius:4px;display:flex;align-items:center;padding-left:5px;font-size:.68rem;font-weight:700;color:var(--bg);}

/* ALERT */
.alert-item{display:flex;align-items:flex-start;gap:9px;padding:9px 0;border-bottom:1px solid rgba(48,54,61,.5);font-size:.8rem;}
.alert-item:last-child{border-bottom:none;}
.adot{width:7px;height:7px;border-radius:50%;flex-shrink:0;margin-top:3px;}
.ameta{color:var(--txt2);font-size:.72rem;margin-top:2px;}

/* HEATMAP */
.hmap{display:grid;grid-template-columns:repeat(5,1fr);gap:7px;margin-top:.5rem;}
.hcell{border-radius:7px;padding:9px 7px;text-align:center;font-size:.72rem;cursor:pointer;transition:transform .15s;}
.hcell:hover{transform:scale(1.04);}
.hm-hot{background:rgba(63,185,80,.22);border:1px solid rgba(63,185,80,.38);}
.hm-warm{background:rgba(201,168,76,.18);border:1px solid rgba(201,168,76,.32);}
.hm-neu{background:rgba(139,148,158,.1);border:1px solid var(--border);}
.hm-cool{background:rgba(248,81,73,.1);border:1px solid rgba(248,81,73,.2);}

/* OPP CARDS */
.opp-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:.9rem;margin-bottom:1.25rem;}
.occ{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:.9rem;position:relative;overflow:hidden;}
.occ::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;}
.occ.hot::before{background:var(--green);}
.occ.warm::before{background:var(--gold);}
.occ.watch::before{background:var(--copper);}
.ot{font-weight:700;font-size:.88rem;margin-bottom:5px;}
.od{font-size:.75rem;color:var(--txt2);margin-bottom:8px;line-height:1.4;}
.op{font-size:1.15rem;font-weight:800;color:var(--green);}
.om{font-size:.7rem;color:var(--txt2);margin-top:3px;}
.ovs{display:flex;gap:4px;flex-wrap:wrap;margin-top:7px;}

/* ══════════════════════════════════
   CITY EXPLORER
══════════════════════════════════ */
.city-section{border-top:1px solid var(--border);padding:2rem 0;}
.city-header{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:1.5rem;flex-wrap:wrap;gap:1rem;}
.city-header h2{font-size:1.3rem;font-weight:800;color:var(--gold);}
.city-header p{color:var(--txt2);font-size:.85rem;margin-top:.3rem;}

/* tax callout strip */
.tax-strip{display:grid;grid-template-columns:1fr 1fr 1fr;gap:.85rem;margin-bottom:1.5rem;}
.tax-box{border-radius:10px;padding:.9rem 1.1rem;font-size:.78rem;}
.tax-box.good{background:rgba(63,185,80,.07);border:1px solid rgba(63,185,80,.22);}
.tax-box.warn{background:rgba(255,165,0,.07);border:1px solid rgba(255,165,0,.22);}
.tax-box.bad{background:rgba(248,81,73,.07);border:1px solid rgba(248,81,73,.22);}
.tax-box strong.head{display:block;font-size:.82rem;font-weight:700;margin-bottom:.4rem;}

/* search + controls */
.city-controls{display:flex;gap:.75rem;margin-bottom:1.1rem;flex-wrap:wrap;align-items:center;}
.city-search{background:var(--card);border:1px solid var(--border);border-radius:8px;padding:7px 14px;color:var(--txt);font-size:.85rem;width:230px;font-family:inherit;outline:none;}
.city-search:focus{border-color:var(--gold);}
.city-search::placeholder{color:var(--txt2);}
select.city-sel{background:var(--card);border:1px solid var(--border);border-radius:8px;padding:7px 12px;color:var(--txt);font-size:.82rem;font-family:inherit;cursor:pointer;outline:none;}
select.city-sel:focus{border-color:var(--gold);}
select.city-sel option{background:var(--card);}
.sort-btn{background:var(--card2);border:1px solid var(--border);color:var(--txt2);padding:6px 12px;border-radius:6px;cursor:pointer;font-size:.78rem;transition:all .2s;font-family:inherit;}
.sort-btn:hover{border-color:var(--gold);color:var(--gold);}
.sort-btn.on{border-color:var(--gold);color:var(--gold);font-weight:600;}

/* top city cards */
.top-city-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:.85rem;margin-bottom:1.5rem;}
.city-card{background:var(--card);border:1px solid var(--border);border-radius:11px;padding:1rem;cursor:pointer;transition:border-color .2s,transform .15s;position:relative;}
.city-card:hover{border-color:var(--gold);transform:translateY(-2px);}
.cc-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:.65rem;}
.cc-name{font-weight:800;font-size:.95rem;}
.cc-state{font-size:.72rem;color:var(--txt2);margin-top:1px;}
.tax-badge{font-size:.68rem;font-weight:700;padding:2px 8px;border-radius:9px;}
.tb-free{background:rgba(63,185,80,.14);color:var(--green);border:1px solid rgba(63,185,80,.28);}
.tb-part{background:rgba(255,165,0,.14);color:#FFA500;border:1px solid rgba(255,165,0,.28);}
.tb-taxed{background:rgba(248,81,73,.14);color:var(--red);border:1px solid rgba(248,81,73,.28);}
.tb-exp{background:rgba(255,165,0,.2);color:#FFB300;border:1px solid rgba(255,165,0,.4);}
.cc-scores{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-bottom:.6rem;}
.cc-score{background:var(--bg);border-radius:6px;padding:7px;text-align:center;}
.csl{font-size:.65rem;color:var(--txt2);margin-bottom:3px;}
.csv{font-size:1.1rem;font-weight:800;}
.cbar{height:3px;background:var(--border);border-radius:2px;margin-top:3px;overflow:hidden;}
.cbar-f{height:100%;border-radius:2px;}
.cc-meta{display:flex;justify-content:space-between;font-size:.72rem;color:var(--txt2);margin-bottom:.5rem;}
.cc-tags{display:flex;gap:4px;flex-wrap:wrap;}
.ctag{font-size:.65rem;padding:2px 7px;border-radius:9px;background:rgba(139,148,158,.1);border:1px solid var(--border);color:var(--txt2);}
.rank-pill{position:absolute;top:9px;right:9px;width:22px;height:22px;border-radius:50%;font-size:.62rem;font-weight:800;display:flex;align-items:center;justify-content:center;}
.rk1{background:var(--gold);color:var(--bg);}
.rk2{background:#aaa;color:var(--bg);}
.rk3{background:var(--copper);color:var(--bg);}

/* BIG TABLE */
.city-table-wrap{overflow-x:auto;}
#cityTable thead th{cursor:pointer;user-select:none;}
#cityTable thead th:hover{color:var(--gold);}
.results-info{font-size:.75rem;color:var(--txt2);margin-bottom:.6rem;}
.pg-btns{display:flex;gap:.5rem;margin-top:1rem;justify-content:center;flex-wrap:wrap;}
.pg-btn{background:var(--card2);border:1px solid var(--border);color:var(--txt2);padding:4px 11px;border-radius:5px;cursor:pointer;font-size:.78rem;}
.pg-btn.on{background:var(--gold);color:var(--bg);border-color:var(--gold);font-weight:700;}
.pg-btn:hover:not(.on){border-color:var(--gold);color:var(--gold);}

/* INSIGHT TRIO */
.insight-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:.9rem;margin-bottom:1.5rem;}
.ig-card{background:var(--card);border:1px solid var(--border);border-radius:10px;padding:.95rem;}
.ig-title{font-weight:700;font-size:.85rem;margin-bottom:.65rem;}
.ig-row{font-size:.78rem;color:var(--txt2);padding:3px 0;line-height:1.5;}
.ig-row strong{color:var(--txt);}

/* STATE LEGEND */
.state-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:.5rem;margin-bottom:1.5rem;}
.state-item{background:var(--card);border:1px solid var(--border);border-radius:7px;padding:.55rem .75rem;display:flex;justify-content:space-between;align-items:center;font-size:.75rem;}
.si-name{font-weight:600;}
.si-tax{font-size:.68rem;font-weight:700;padding:1px 6px;border-radius:4px;}

footer{border-top:1px solid var(--border);padding:1.25rem 1.5rem;display:flex;justify-content:space-between;align-items:center;font-size:.75rem;color:var(--txt2);}
footer a{color:var(--gold);text-decoration:none;}

@media(max-width:1050px){.mgrid{grid-template-columns:1fr;}.opp-grid{grid-template-columns:1fr 1fr;}.hero-stats{display:none;}.tax-strip{grid-template-columns:1fr;}.insight-grid{grid-template-columns:1fr;}}
@media(max-width:700px){.opp-grid{grid-template-columns:1fr;}.hmap{grid-template-columns:repeat(3,1fr);}.top-city-grid{grid-template-columns:1fr;}}

/* ── MAP SECTION ── */
#mapSection{background:var(--card);border-top:1px solid var(--border);border-bottom:1px solid var(--border);margin-bottom:1.25rem;padding:1.25rem 1.5rem;}
.map-header{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:.75rem;margin-bottom:1rem;}
.map-title{font-size:1rem;font-weight:700;color:var(--txt);}
.map-subtitle{font-size:.78rem;color:var(--txt2);margin-top:2px;}
.map-toggle{display:flex;gap:0;border:1px solid var(--border);border-radius:8px;overflow:hidden;}
.mtbtn{background:var(--card2);border:none;color:var(--txt2);padding:7px 18px;cursor:pointer;font-size:.8rem;font-weight:600;font-family:inherit;transition:all .2s;border-right:1px solid var(--border);}
.mtbtn:last-child{border-right:none;}
.mtbtn.buyer-on{background:#1565C0;color:#fff;}
.mtbtn.seller-on{background:#C62828;color:#fff;}
.mtbtn.split-on{background:linear-gradient(90deg,#1565C0,#C62828);color:#fff;}
.mtbtn:hover:not(.buyer-on):not(.seller-on):not(.split-on){background:var(--border);color:var(--txt);}
#mapWrap{position:relative;width:100%;height:520px;background:var(--bg);border-radius:10px;overflow:hidden;border:1px solid var(--border);}
#usMap{width:100%;height:100%;}
.map-loader{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-size:.85rem;color:var(--txt2);flex-direction:column;gap:.5rem;}
.spin{width:28px;height:28px;border:3px solid var(--border);border-top-color:var(--gold);border-radius:50%;animation:spin .8s linear infinite;}
@keyframes spin{to{transform:rotate(360deg);}}
#mapTooltip{position:absolute;pointer-events:none;background:rgba(22,27,34,.97);border:1px solid var(--border);border-radius:8px;padding:10px 14px;font-size:.78rem;max-width:220px;box-shadow:0 4px 20px rgba(0,0,0,.5);display:none;z-index:50;}
#mapTooltip .tt-city{font-weight:800;font-size:.9rem;margin-bottom:4px;}
#mapTooltip .tt-state{color:var(--txt2);font-size:.72rem;margin-bottom:6px;}
#mapTooltip .tt-row{display:flex;justify-content:space-between;gap:12px;margin-bottom:2px;}
#mapTooltip .tt-lbl{color:var(--txt2);}
#mapTooltip .tt-val{font-weight:700;}
#mapTooltip .tt-tax{margin-top:6px;font-size:.72rem;font-weight:600;padding:2px 8px;border-radius:4px;display:inline-block;}
.map-legend{display:flex;align-items:center;gap:1.5rem;flex-wrap:wrap;margin-top:.8rem;}
.leg-item{display:flex;align-items:center;gap:.5rem;font-size:.75rem;color:var(--txt2);}
.leg-swatch{width:120px;height:12px;border-radius:3px;}
.leg-tax{display:flex;align-items:center;gap:5px;font-size:.75rem;color:var(--txt2);}
.leg-tax-swatch{width:14px;height:14px;border-radius:3px;background:repeating-linear-gradient(-45deg,rgba(255,165,0,.5),rgba(255,165,0,.5) 2px,transparent 2px,transparent 6px);border:1px solid rgba(255,165,0,.4);}
.map-info-bar{display:flex;justify-content:space-between;align-items:center;margin-top:.6rem;font-size:.75rem;color:var(--txt2);}
</style>
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/topojson/3.0.2/topojson.min.js"></script>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo"><div class="logo-icon">⚖</div>MetalScope</div>
  <ul class="nav-links">
    <li><a href="#" class="active">Arbitrage</a></li>
    <li><a href="#cityExplorer">City Markets</a></li>
    <li><a href="#">Dealers</a></li>
    <li><a href="#">Price History</a></li>
    <li><a href="#">Alerts</a></li>
    <li><a href="#">Calculator</a></li>
  </ul>
  <div class="nav-r">
    <button class="btn-out">Sign In</button>
    <button class="btn-sol">Get Pro</button>
  </div>
</nav>

<!-- TICKER — prices updated by prices.json loader -->
<div class="ticker">
  <div class="ti"><span class="dot" style="background:var(--gold)"></span><span class="ti-metal">GOLD</span><span id="tick-gold" class="ti-price">$4,747.20</span><span id="tick-gold-ch" class="dn">▼ −$18.30 (−0.38%)</span></div>
  <div class="ti"><span class="dot" style="background:var(--silver)"></span><span class="ti-metal">SILVER</span><span id="tick-silver" class="ti-price">$75.76</span><span id="tick-silver-ch" class="up">▲ +$0.55 (+0.73%)</span></div>
  <div class="ti"><span class="dot" style="background:#e8e8e8"></span><span class="ti-metal">PLATINUM</span><span id="tick-platinum" class="ti-price">$2,044.00</span><span id="tick-platinum-ch" class="dn">▼ −$56.00 (−2.67%)</span></div>
  <div class="ti"><span class="dot" style="background:#999"></span><span class="ti-metal">PALLADIUM</span><span id="tick-palladium" class="ti-price">$1,507.00</span><span id="tick-palladium-ch" class="dn">▼ −$37.50 (−2.43%)</span></div>
  <div class="ti"><span class="dot" style="background:var(--copper)"></span><span class="ti-metal">COPPER</span><span id="tick-copper" class="ti-price">$5.78/lb</span><span class="up">▲ +$0.06 (+1.05%)</span></div>
  <div class="ti" style="margin-left:auto;font-size:.72rem;color:var(--txt2);"><span class="live-dot"></span><span id="tickerSrc">Swissquote · loading…</span></div>
</div>

<div class="wrap">

<!-- HERO -->
<div class="hero">
  <div>
    <h1>Precious Metals Arbitrage Intelligence</h1>
    <p>Real-time buy/sell spreads across all US markets — every state, 300+ cities, 12+ venues. Gold at $4,747 · Silver at $75.76. Find where to buy cheap and sell at the best price.</p>
  </div>
  <div class="hero-stats">
    <div class="stat"><div class="stat-v">47</div><div class="stat-l">Live Arb Ops</div></div>
    <div class="stat"><div class="stat-v">$5.80</div><div class="stat-l">Best Ag Spread</div></div>
    <div class="stat"><div class="stat-v">306</div><div class="stat-l">Cities Tracked</div></div>
    <div class="stat"><div class="stat-v">44</div><div class="stat-l">Tax-Free States</div></div>
  </div>
</div>

<!-- ══ INTERACTIVE HEATMAP ══ -->
<div id="mapSection">
  <div class="map-header">
    <div>
      <div class="map-title">🗺 US Market Heatmap — 306 Cities · All 50 States</div>
      <div class="map-subtitle">Color intensity = strength of opportunity. Hover any state or city dot for details.</div>
    </div>
    <div class="map-toggle">
      <button class="mtbtn buyer-on" id="btnBuyer">🔵 Buyer Markets</button>
      <button class="mtbtn" id="btnSeller">🔴 Seller Markets</button>
      <button class="mtbtn" id="btnSplit">⚡ Split View</button>
    </div>
  </div>
  <div id="mapWrap">
    <div class="map-loader" id="mapLoader"><div class="spin"></div>Loading map…</div>
    <svg id="usMap"></svg>
    <div id="mapTooltip"></div>
  </div>
  <div class="map-legend">
    <div class="leg-item" id="legBuyer">
      <span style="font-size:.75rem;color:var(--txt2);">Low</span>
      <div class="leg-swatch" style="background:linear-gradient(90deg,#BBDEFB,#0D47A1);"></div>
      <span style="font-size:.75rem;color:var(--txt2);">High Buyer Score</span>
    </div>
    <div class="leg-item" id="legSeller" style="display:none;">
      <span style="font-size:.75rem;color:var(--txt2);">Low</span>
      <div class="leg-swatch" style="background:linear-gradient(90deg,#FFCDD2,#B71C1C);"></div>
      <span style="font-size:.75rem;color:var(--txt2);">High Seller Score</span>
    </div>
    <div class="leg-item" id="legSplit" style="display:none;">
      <div class="leg-swatch" style="background:linear-gradient(90deg,#1565C0,#7B1FA2,#C62828);"></div>
      <span style="font-size:.75rem;color:var(--txt2);">Buyer → Both → Seller</span>
    </div>
    <div class="leg-tax">
      <div class="leg-tax-swatch"></div>
      <span>Sales tax penalty on PM</span>
    </div>
    <div class="leg-item"><span style="color:var(--txt2);">Circle size = population</span></div>
  </div>
  <div class="map-info-bar">
    <span id="mapInfoText">Hover a state or city for details</span>
    <span style="color:var(--txt2);">Click a state to filter the city table below</span>
  </div>
</div>

<!-- OPP CARDS — prices updated to current spot -->
<div class="opp-grid">
  <div class="occ hot">
    <div class="ot">🔥 Silver Eagle (1–4 oz)</div>
    <div class="od">Buy r/pmsforsale ~spot +4%, sell APMEX buyback +11%. At $75.76 spot that's ~$5.30/oz net after fees.</div>
    <div class="op">+$5.30/oz</div><div class="om">After fees · ~15 min to execute</div>
    <div class="ovs"><span class="vtag reddit">Reddit → Buy</span><span class="vtag apmex">APMEX → Sell</span></div>
  </div>
  <div class="occ warm">
    <div class="ot">⚡ 1oz Gold Maple Leaf</div>
    <div class="od">eBay completed ~$4,762 vs JM Bullion sell at $4,781. Slim but consistent at this price level.</div>
    <div class="op">+$19.00/oz</div><div class="om">After 13.25% eBay fees · 3–7 days</div>
    <div class="ovs"><span class="vtag ebay">eBay → Buy</span><span class="vtag jmb">JM Bullion → Sell</span></div>
  </div>
  <div class="occ watch">
    <div class="ot">👁 Platinum Eagle (1oz)</div>
    <div class="od">Platinum lagging gold/silver rally — eBay averaging $2,028 vs APMEX sell $2,078. Solid arb window.</div>
    <div class="op">+$50.00/oz</div><div class="om">Best platinum play right now · Act fast</div>
    <div class="ovs"><span class="vtag ebay">eBay → Buy</span><span class="vtag apmex">APMEX → Sell</span></div>
  </div>
</div>

<!-- MAIN GRID -->
<div class="mgrid">
<div>

<!-- ARB TABLE -->
<div class="card">
  <div class="sec-title">Live Arbitrage Table <span class="badge">UPDATED TO CURRENT SPOT</span></div>
  <div class="tabs">
    <button class="tab on">All Metals</button><button class="tab">Silver</button><button class="tab">Gold</button><button class="tab">Platinum</button><button class="tab">Copper</button><button class="tab">Palladium</button>
  </div>
  <div class="filters">
    <span class="fl">Buy:</span>
    <span class="chip on">All</span><span class="chip">eBay</span><span class="chip">Reddit</span><span class="chip">Local</span><span class="chip">Costco</span><span class="chip">Auctions</span>
  </div>
  <table>
    <thead><tr><th>Product</th><th>Buy Venue</th><th>Buy Price</th><th>Sell Venue</th><th>Sell Price</th><th>Net Spread</th><th>Signal</th></tr></thead>
    <tbody>
      <tr><td><div class="pname">Silver Eagle</div><div class="psub">1oz · 2025 · Qty 1–4</div></td><td><span class="vtag reddit">r/pmsforsale</span></td><td>$78.80</td><td><span class="vtag apmex">APMEX Buyback</span></td><td>$84.10</td><td><span class="arb-pos">+$5.30</span></td><td><span class="abadge ab-hot">🔥 HOT</span></td></tr>
      <tr><td><div class="pname">Silver Maple Leaf</div><div class="psub">1oz · Back Date · Qty 5–24</div></td><td><span class="vtag ebay">eBay Sold</span></td><td>$79.40</td><td><span class="vtag jmb">JM Bullion</span></td><td>$83.80</td><td><span class="arb-pos">+$4.40</span></td><td><span class="abadge ab-hot">🔥 HOT</span></td></tr>
      <tr><td><div class="pname">Platinum Eagle</div><div class="psub">1oz · 2023–2025</div></td><td><span class="vtag ebay">eBay Sold</span></td><td>$2,028</td><td><span class="vtag apmex">APMEX</span></td><td>$2,078</td><td><span class="arb-pos">+$50.00</span></td><td><span class="abadge ab-hot">🔥 HOT</span></td></tr>
      <tr><td><div class="pname">10oz Silver Bar</div><div class="psub">Generic · Qty 2–9</div></td><td><span class="vtag costco">Costco</span></td><td>$790.50</td><td><span class="vtag sd">SD Bullion</span></td><td>$803.20</td><td><span class="arb-pos">+$12.70</span></td><td><span class="abadge ab-warm">⚡ WARM</span></td></tr>
      <tr><td><div class="pname">1oz Gold Eagle</div><div class="psub">2024 · Qty 1</div></td><td><span class="vtag lcs">Local Coin Shop</span></td><td>$4,730</td><td><span class="vtag apmex">APMEX Buyback</span></td><td>$4,762</td><td><span class="arb-pos">+$32.00</span></td><td><span class="abadge ab-warm">⚡ WARM</span></td></tr>
      <tr><td><div class="pname">Silver Round (Generic)</div><div class="psub">1oz · Qty 100–499</div></td><td><span class="vtag reddit">r/pmsforsale</span></td><td>$77.10</td><td><span class="vtag jmb">JM Bullion</span></td><td>$79.90</td><td><span class="arb-pos">+$2.80</span></td><td><span class="abadge ab-warm">⚡ WARM</span></td></tr>
      <tr><td><div class="pname">100oz Silver Bar</div><div class="psub">Sunshine Mint · Qty 1–4</div></td><td><span class="vtag ebay">eBay Sold</span></td><td>$7,682</td><td><span class="vtag apmex">APMEX Buyback</span></td><td>$7,648</td><td><span class="arb-neg">−$34.00</span></td><td><span class="abadge ab-cold">— AVOID</span></td></tr>
      <tr><td><div class="pname">Palladium Bar (1oz)</div><div class="psub">PAMP Suisse · Qty 1</div></td><td><span class="vtag ebay">eBay Sold</span></td><td>$1,498</td><td><span class="vtag apmex">APMEX</span></td><td>$1,542</td><td><span class="arb-pos">+$44.00</span></td><td><span class="abadge ab-warm">⚡ WARM</span></td></tr>
    </tbody>
  </table>
</div>

<!-- HEATMAP -->
<div class="card">
  <div class="sec-title">Venue Premium Heatmap <span style="font-size:.72rem;color:var(--txt2);font-weight:400;">— Silver Eagles at $75.76 spot</span></div>
  <div class="hmap">
    <div class="hcell hm-hot"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">r/PMS</div><div style="font-weight:800;color:var(--green);">+4.0%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">BUY</div></div>
    <div class="hcell hm-warm"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">eBay Avg</div><div style="font-weight:800;color:var(--gold);">+5.3%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">BUY</div></div>
    <div class="hcell hm-warm"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">SD Bullion</div><div style="font-weight:800;color:var(--gold);">+6.5%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">MID</div></div>
    <div class="hcell hm-neu"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">JM Bullion</div><div style="font-weight:800;">+7.8%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">MID</div></div>
    <div class="hcell hm-neu"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">Costco</div><div style="font-weight:800;">+7.9%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">MID</div></div>
    <div class="hcell hm-cool"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">APMEX</div><div style="font-weight:800;">+9.2%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">SELL</div></div>
    <div class="hcell hm-cool"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">Provident</div><div style="font-weight:800;">+9.6%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">SELL</div></div>
    <div class="hcell hm-cool"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">Coin Shop</div><div style="font-weight:800;">+11–18%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">SELL</div></div>
    <div class="hcell hm-cool"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">US Mint</div><div style="font-weight:800;">+13.0%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">SELL</div></div>
    <div class="hcell hm-cool"><div style="color:rgba(255,255,255,.6);margin-bottom:3px;">Pawn</div><div style="font-weight:800;">+15–25%</div><div style="font-size:.62rem;color:rgba(255,255,255,.4);margin-top:2px;">SELL</div></div>
  </div>
  <div style="font-size:.7rem;color:var(--txt2);margin-top:.9rem;">🟢 Green = cheapest buy · 🔴 Red = most expensive for buyer (best for sellers) · Premiums compress as spot rises</div>
</div>

<!-- DEALER COMPARISON TABLE — populated from prices.json -->
<div class="card" id="dealerCompCard" style="display:none;">
  <div class="sec-title">Dealer Spread Comparison <span class="badge" id="dealerBadge">LIVE DATA</span></div>
  <div style="font-size:.75rem;color:var(--txt2);margin-bottom:.85rem;">Buy price vs spot — ranked cheapest to most expensive. Run <code style="background:rgba(255,255,255,.06);padding:2px 5px;border-radius:3px;">scraper.py</code> to refresh.</div>
  <div style="overflow-x:auto;">
    <table id="dealerTable" style="font-size:.78rem;">
      <thead>
        <tr>
          <th>Product</th>
          <th>Best Buy</th>
          <th style="text-align:right;">Best $</th>
          <th style="text-align:right;">Best %</th>
          <th>Most Exp.</th>
          <th style="text-align:right;">Spread $</th>
          <th style="text-align:right;">Spread %</th>
          <th>eBay Avg</th>
        </tr>
      </thead>
      <tbody id="dealerTableBody"></tbody>
    </table>
  </div>
  <div style="font-size:.68rem;color:var(--txt2);margin-top:.7rem;padding-top:.6rem;border-top:1px solid var(--border);">
    ⚠ Dealer prices are estimated from typical market premiums. Verify with dealer before transacting.
    Spot source: Swissquote. Data quality: <span id="dealerQuality">estimated</span>.
    Last scraped: <span id="dealerScrapedAt">—</span>
  </div>
</div>

</div><!-- end left col -->

<!-- SIDEBAR -->
<div>
  <div class="spot-card">
    <div class="sec-title"><span class="live-dot"></span>Live Spot <span id="spotCardSrc" style="font-weight:400;font-size:.7rem;color:var(--txt2);">loading…</span></div>
    <div class="spot-row"><div class="spot-metal"><span class="dot" style="background:var(--gold)"></span>Gold</div><div style="text-align:right"><div id="spot-gold" class="spot-main">$4,747.20</div><div id="spot-gold-ch" class="spot-ch dn">▼ −0.38% today</div></div></div>
    <div class="spot-row"><div class="spot-metal"><span class="dot" style="background:var(--silver)"></span>Silver</div><div style="text-align:right"><div id="spot-silver" class="spot-main">$75.76</div><div id="spot-silver-ch" class="spot-ch up">▲ +0.73% today</div></div></div>
    <div class="spot-row"><div class="spot-metal"><span class="dot" style="background:#e8e8e8"></span>Platinum</div><div style="text-align:right"><div id="spot-platinum" class="spot-main">$2,044.00</div><div id="spot-platinum-ch" class="spot-ch dn">▼ −2.67% today</div></div></div>
    <div class="spot-row"><div class="spot-metal"><span class="dot" style="background:#999"></span>Palladium</div><div style="text-align:right"><div id="spot-palladium" class="spot-main">$1,507.00</div><div id="spot-palladium-ch" class="spot-ch dn">▼ −2.43% today</div></div></div>
    <div class="spot-row"><div class="spot-metal"><span class="dot" style="background:var(--copper)"></span>Copper</div><div style="text-align:right"><div id="spot-copper" class="spot-main">$5.78/lb</div><div class="spot-ch up">LME estimate</div></div></div>
    <div style="margin-top:.9rem;">
      <div style="font-size:.72rem;color:var(--txt2);margin-bottom:4px;">Gold / Silver Ratio</div>
      <div id="spot-gsr" style="font-size:1.25rem;font-weight:800;color:var(--gold);">62.66</div>
      <div style="font-size:.7rem;color:var(--txt2);">Normal range — both metals running hot in 2026</div>
    </div>
  </div>

  <div class="card">
    <div class="sec-title">🔔 Arbitrage Alerts <span id="alertBadge" class="badge" style="display:none;"></span></div>
    <div id="alertList">
      <div class="alert-item"><div class="adot" style="background:var(--green)"></div><div><div>Platinum/Silver ratio at 5-yr low — pt arbitrage window wide</div><div class="ameta">eBay vs APMEX · 6 min ago</div></div></div>
      <div class="alert-item"><div class="adot" style="background:var(--gold)"></div><div><div>Costco 10oz bars back in stock — spread +$12.70</div><div class="ameta">Costco → SD Bullion · 14 min ago</div></div></div>
      <div class="alert-item"><div class="adot" style="background:var(--red)"></div><div><div>100oz silver bar spread inverted — avoid eBay buy</div><div class="ameta">eBay avg · 21 min ago</div></div></div>
      <div class="alert-item"><div class="adot" style="background:var(--gold)"></div><div><div>⚠️ Virginia PM tax exemption expires July 1, 2026</div><div class="ameta">Regulatory · Buy now, not after July</div></div></div>
    </div>
    <button class="btn-out" style="width:100%;margin-top:.7rem;font-size:.78rem;">⚙ Set Custom Alerts</button>
  </div>

  <div class="card">
    <div class="sec-title">Buy Premiums — Silver Eagles</div>
    <div style="font-size:.72rem;color:var(--txt2);margin-bottom:.85rem;">% over $75.76 spot — lower = better for buyer</div>
    <div class="pbar-row"><div class="pbar-lbl">r/pmsforsale</div><div class="pbar-track"><div class="pbar-fill" style="width:28%;background:var(--green);">4.0%</div></div></div>
    <div class="pbar-row"><div class="pbar-lbl">eBay Avg</div><div class="pbar-track"><div class="pbar-fill" style="width:37%;background:#9ACD50;">5.3%</div></div></div>
    <div class="pbar-row"><div class="pbar-lbl">SD Bullion</div><div class="pbar-track"><div class="pbar-fill" style="width:46%;background:#C9A84C;">6.5%</div></div></div>
    <div class="pbar-row"><div class="pbar-lbl">JM Bullion</div><div class="pbar-track"><div class="pbar-fill" style="width:55%;background:#D4882C;">7.8%</div></div></div>
    <div class="pbar-row"><div class="pbar-lbl">APMEX</div><div class="pbar-track"><div class="pbar-fill" style="width:65%;background:#E06030;">9.2%</div></div></div>
    <div class="pbar-row"><div class="pbar-lbl">US Mint</div><div class="pbar-track"><div class="pbar-fill" style="width:91%;background:#F04040;">13.0%</div></div></div>
    <div style="font-size:.7rem;color:var(--txt2);margin-top:.6rem;">Note: premiums compressed vs 2025 as spot surged — % gap narrower but $ spread still significant at high price levels.</div>
  </div>
</div>
</div><!-- end mgrid -->

</div><!-- end wrap -->

<!-- ══════════════════════════════════════════════════════
     CITY MARKET EXPLORER
══════════════════════════════════════════════════════ -->
<div id="cityExplorer" class="city-section">
<div class="wrap">

  <div class="city-header">
    <div>
      <h2>🗺 City Market Explorer</h2>
      <p>All 50 states · 306 cities at 50,000+ population · Scored by buyer advantage, seller access, sales tax, dealer density &amp; coin show activity</p>
    </div>
  </div>

  <!-- TAX STRIP -->
  <div class="tax-strip">
    <div class="tax-box good">
      <strong class="head" style="color:var(--green);">✅ Zero Sales Tax on PM (~44 States)</strong>
      AL, AK, AZ, AR, CA, CT, DE, GA, ID, IL, IN, IA, KS, KY, LA, MA, MI, MN, MS, MO, MT, NE, NV, NH, NJ, NY, NC, ND, OH, OK, OR, PA, RI, SC, SD, TN, TX, UT, WV, WI, WY — plus DC exempts investment bullion.
    </div>
    <div class="tax-box warn">
      <strong class="head" style="color:#FFA500;">⚡ Partial / Conditional Exemptions</strong>
      <strong>Florida:</strong> exempt on purchases &gt;$500 per item.<br>
      <strong>Colorado:</strong> exempt on purchases &gt;$500.<br>
      <strong>Virginia:</strong> exempt NOW — <em>expires July 1, 2026</em>. Buy before then.
    </div>
    <div class="tax-box bad">
      <strong class="head" style="color:var(--red);">🚫 States That Tax Precious Metals</strong>
      <strong>Washington:</strong> 10.25% (reinstated Jan 1, 2026) — worst in US<br>
      <strong>Maryland:</strong> 6% · <strong>Vermont:</strong> 6% · <strong>D.C.:</strong> 6%<br>
      <strong>Maine:</strong> 5.5% · <strong>New Mexico:</strong> 5.125% GRT<br>
      <strong>Hawaii:</strong> 4.5% GET + island supply premium
    </div>
  </div>

  <!-- STATE LEGEND -->
  <div class="card">
    <div class="sec-title">All 50 States + DC — Tax Status at a Glance</div>
    <div class="state-grid" id="stateLegend"></div>
  </div>

  <!-- CONTROLS -->
  <div class="city-controls">
    <input class="city-search" id="citySearch" type="text" placeholder="🔍 Search city or state…">
    <select class="city-sel" id="stateFilter">
      <option value="ALL">All States</option>
    </select>
    <span class="fl">Sort:</span>
    <button class="sort-btn on" data-sort="buyer">Buyer Score</button>
    <button class="sort-btn" data-sort="seller">Seller Score</button>
    <button class="sort-btn" data-sort="pop">Population</button>
    <button class="sort-btn" data-sort="city">City A–Z</button>
    <span class="fl" style="margin-left:auto;">Filter:</span>
    <span class="chip on city-f" data-f="all">All</span>
    <span class="chip city-f" data-f="buyer">Best Buyers</span>
    <span class="chip city-f" data-f="seller">Best Sellers</span>
    <span class="chip city-f" data-f="notax">No Sales Tax</span>
    <span class="chip city-f" data-f="shows">Coin Shows</span>
    <span class="chip city-f" data-f="taxed">⚠ Taxed States</span>
  </div>

  <!-- TOP CARDS -->
  <div id="topCards" class="top-city-grid"></div>

  <!-- FULL TABLE -->
  <div class="card">
    <div class="sec-title">Full City Database <span class="badge" id="resultCount">306 CITIES</span></div>
    <div class="results-info" id="resultsInfo"></div>
    <div class="city-table-wrap">
    <table id="cityTable">
      <thead><tr>
        <th data-col="city">City ▲</th>
        <th data-col="state">State</th>
        <th data-col="pop">Population</th>
        <th data-col="tax">Sales Tax on PM</th>
        <th data-col="buyer">Buyer Score ▼</th>
        <th data-col="seller">Seller Score</th>
        <th data-col="shows">Shows/yr</th>
        <th>Highlights</th>
        <th>Verdict</th>
      </tr></thead>
      <tbody id="cityTbody"></tbody>
    </table>
    </div>
    <div class="pg-btns" id="pgBtns"></div>
  </div>

  <!-- INSIGHT CARDS -->
  <div class="insight-grid">
    <div class="ig-card" style="border-color:rgba(63,185,80,.3)">
      <div class="ig-title" style="color:var(--green)">🏆 Top Buyer Cities</div>
      <div class="ig-row"><strong>#1 Dallas/Fort Worth, TX</strong> — Heritage HQ, no tax, highest dealer competition in South</div>
      <div class="ig-row"><strong>#2 Las Vegas, NV</strong> — Pawn ecosystem, cash economy, no tax, 24/7 market</div>
      <div class="ig-row"><strong>#3 Phoenix/Scottsdale, AZ</strong> — Monthly shows, estate sales, no tax</div>
      <div class="ig-row"><strong>#4 Portland, OR</strong> — Zero statewide sales tax, strong stacker culture</div>
      <div class="ig-row"><strong>#5 Houston, TX</strong> — Oil wealth, no tax, refinery access</div>
    </div>
    <div class="ig-card" style="border-color:rgba(201,168,76,.3)">
      <div class="ig-title" style="color:var(--gold)">💰 Top Seller Cities</div>
      <div class="ig-row"><strong>#1 New York City, NY</strong> — Heritage, Stack's Bowers, most auction density</div>
      <div class="ig-row"><strong>#2 Dallas/Fort Worth, TX</strong> — Heritage HQ, highest buyback competition</div>
      <div class="ig-row"><strong>#3 Orlando, FL</strong> — FUN Show (world's largest coin show, twice/yr)</div>
      <div class="ig-row"><strong>#4 Baltimore, MD</strong> — Spring &amp; Fall Baltimore shows (despite 6% buy tax)</div>
      <div class="ig-row"><strong>#5 Los Angeles, CA</strong> — Heritage West, Stack's Bowers, huge collector base</div>
    </div>
    <div class="ig-card" style="border-color:rgba(248,81,73,.3)">
      <div class="ig-title" style="color:var(--red)">🚫 Avoid Buying In</div>
      <div class="ig-row"><strong>Seattle, WA</strong> — 10.25% tax reinstated Jan 2026; $4,747 gold = +$486 tax hit</div>
      <div class="ig-row"><strong>All WA cities</strong> — Bellevue, Tacoma, Spokane all now cost 10.25% more to buy</div>
      <div class="ig-row"><strong>Honolulu, HI</strong> — 4.5% GET + island logistics premium</div>
      <div class="ig-row"><strong>Baltimore/Rockville, MD</strong> — 6% tax; buy online, sell locally</div>
      <div class="ig-row"><strong>Virginia cities after July 1</strong> — Exemption expiring; buy before deadline</div>
    </div>
  </div>

</div>
</div>

<footer>
  <div>© 2026 MetalScope · Not financial or investment advice. Prices from Kitco (Apr 10, 2026 close). City scores are estimates.</div>
  <div><a href="#">API</a> · <a href="#">Affiliate Program</a> · <a href="#">Terms</a> · Data: COMEX, Kitco, dealer feeds, eBay, Reddit</div>
</footer>

<script>
// ══════════════════════════════════════════════════════
// DATA
// ══════════════════════════════════════════════════════

const STATE_TAX = {
  AL:{name:'Alabama',tax:0,status:'exempt',note:'Full exemption'},
  AK:{name:'Alaska',tax:0,status:'notax',note:'No state sales tax'},
  AZ:{name:'Arizona',tax:0,status:'exempt',note:'Full exemption'},
  AR:{name:'Arkansas',tax:0,status:'exempt',note:'Full exemption'},
  CA:{name:'California',tax:0,status:'exempt',note:'Bullion exempt'},
  CO:{name:'Colorado',tax:0,status:'partial',note:'Exempt >$500'},
  CT:{name:'Connecticut',tax:0,status:'exempt',note:'Full exemption'},
  DE:{name:'Delaware',tax:0,status:'notax',note:'No state sales tax'},
  FL:{name:'Florida',tax:0,status:'partial',note:'Exempt per item >$500'},
  GA:{name:'Georgia',tax:0,status:'exempt',note:'Full exemption'},
  HI:{name:'Hawaii',tax:4.5,status:'taxed',note:'4.5% GET'},
  ID:{name:'Idaho',tax:0,status:'exempt',note:'Full exemption'},
  IL:{name:'Illinois',tax:0,status:'exempt',note:'Full exemption'},
  IN:{name:'Indiana',tax:0,status:'exempt',note:'Full exemption'},
  IA:{name:'Iowa',tax:0,status:'exempt',note:'Full exemption'},
  KS:{name:'Kansas',tax:0,status:'exempt',note:'Full exemption'},
  KY:{name:'Kentucky',tax:0,status:'exempt',note:'Full exemption'},
  LA:{name:'Louisiana',tax:0,status:'exempt',note:'Full exemption'},
  ME:{name:'Maine',tax:5.5,status:'taxed',note:'5.5% sales tax'},
  MD:{name:'Maryland',tax:6.0,status:'taxed',note:'6% sales tax'},
  MA:{name:'Massachusetts',tax:0,status:'exempt',note:'Investment bullion exempt'},
  MI:{name:'Michigan',tax:0,status:'exempt',note:'Full exemption'},
  MN:{name:'Minnesota',tax:0,status:'exempt',note:'Full exemption'},
  MS:{name:'Mississippi',tax:0,status:'exempt',note:'Full exemption'},
  MO:{name:'Missouri',tax:0,status:'exempt',note:'Full exemption'},
  MT:{name:'Montana',tax:0,status:'notax',note:'No state sales tax'},
  NE:{name:'Nebraska',tax:0,status:'exempt',note:'Full exemption'},
  NV:{name:'Nevada',tax:0,status:'exempt',note:'Full exemption'},
  NH:{name:'New Hampshire',tax:0,status:'notax',note:'No state sales tax'},
  NJ:{name:'New Jersey',tax:0,status:'exempt',note:'Investment bullion exempt'},
  NM:{name:'New Mexico',tax:5.125,status:'taxed',note:'5.125% GRT'},
  NY:{name:'New York',tax:0,status:'exempt',note:'Investment bullion exempt'},
  NC:{name:'North Carolina',tax:0,status:'exempt',note:'Full exemption'},
  ND:{name:'North Dakota',tax:0,status:'exempt',note:'Full exemption'},
  OH:{name:'Ohio',tax:0,status:'exempt',note:'Full exemption'},
  OK:{name:'Oklahoma',tax:0,status:'exempt',note:'Full exemption'},
  OR:{name:'Oregon',tax:0,status:'notax',note:'No state sales tax'},
  PA:{name:'Pennsylvania',tax:0,status:'exempt',note:'Full exemption'},
  RI:{name:'Rhode Island',tax:0,status:'exempt',note:'Full exemption'},
  SC:{name:'South Carolina',tax:0,status:'exempt',note:'Full exemption'},
  SD:{name:'South Dakota',tax:0,status:'exempt',note:'Full exemption'},
  TN:{name:'Tennessee',tax:0,status:'exempt',note:'Full exemption'},
  TX:{name:'Texas',tax:0,status:'exempt',note:'Full exemption'},
  UT:{name:'Utah',tax:0,status:'exempt',note:'Full exemption'},
  VT:{name:'Vermont',tax:6.0,status:'taxed',note:'6% sales tax'},
  VA:{name:'Virginia',tax:0,status:'expiring',note:'Exempt — EXPIRES Jul 1, 2026!'},
  WA:{name:'Washington',tax:10.25,status:'taxed',note:'10.25% — reinstated Jan 2026'},
  WV:{name:'West Virginia',tax:0,status:'exempt',note:'Full exemption'},
  WI:{name:'Wisconsin',tax:0,status:'exempt',note:'Full exemption'},
  WY:{name:'Wyoming',tax:0,status:'exempt',note:'Full exemption'},
  DC:{name:'D.C.',tax:6.0,status:'taxed',note:'6% sales tax'}
};

// flags: heritage=Heritage Auctions, stacks=Stack's Bowers, fun=FUN show, ana=ANA show,
// csns=Central States, pawn=pawn density, estate=high estate sales, military=military community,
// intl=international buyers, tech=tech wealth, wealth=high wealth, mint=US Mint nearby,
// refinery=near refinery, shows=active show scene, auction=major auction access
const RAW = [
  // ALABAMA
  ['Birmingham','AL',212237,['shows']],
  ['Huntsville','AL',215006,['military']],
  ['Montgomery','AL',200603,['military']],
  ['Mobile','AL',186658,[]],
  ['Tuscaloosa','AL',100300,[]],
  ['Hoover','AL',92606,[]],
  ['Auburn','AL',76143,[]],
  // ALASKA
  ['Anchorage','AK',288000,['military']],
  // ARIZONA
  ['Phoenix','AZ',1625000,['estate','shows']],
  ['Tucson','AZ',542629,['military','estate']],
  ['Mesa','AZ',504258,['estate']],
  ['Chandler','AZ',275987,['tech']],
  ['Scottsdale','AZ',258069,['estate','shows','wealth']],
  ['Gilbert','AZ',267918,[]],
  ['Glendale','AZ',248325,[]],
  ['Tempe','AZ',195805,[]],
  ['Peoria','AZ',175961,['estate']],
  ['Surprise','AZ',141664,['estate']],
  ['Goodyear','AZ',101178,[]],
  ['Avondale','AZ',87985,[]],
  ['Flagstaff','AZ',73964,[]],
  ['Yuma','AZ',97284,['military']],
  ['Buckeye','AZ',91502,[]],
  ['Casa Grande','AZ',57247,[]],
  ['Lake Havasu City','AZ',55600,['estate']],
  ['Maricopa','AZ',51798,[]],
  // ARKANSAS
  ['Little Rock','AR',202591,[]],
  ['Fort Smith','AR',88001,[]],
  ['Fayetteville','AR',93949,[]],
  ['Springdale','AR',81799,[]],
  ['Jonesboro','AR',77463,[]],
  // CALIFORNIA
  ['Los Angeles','CA',3900000,['heritage','stacks','intl','shows','auction']],
  ['San Diego','CA',1390000,['military','intl']],
  ['San Jose','CA',1030000,['tech']],
  ['San Francisco','CA',874000,['intl','tech','auction']],
  ['Fresno','CA',542000,[]],
  ['Sacramento','CA',524000,['shows']],
  ['Long Beach','CA',466000,['intl','shows']],
  ['Oakland','CA',440000,[]],
  ['Bakersfield','CA',407000,[]],
  ['Anaheim','CA',346000,[]],
  ['Santa Ana','CA',310000,['intl']],
  ['Riverside','CA',330000,[]],
  ['Stockton','CA',320000,[]],
  ['Chula Vista','CA',274000,['intl','military']],
  ['Irvine','CA',307000,['tech','wealth']],
  ['Fremont','CA',230000,['tech']],
  ['San Bernardino','CA',222000,[]],
  ['Modesto','CA',218000,[]],
  ['Fontana','CA',214000,[]],
  ['Moreno Valley','CA',208000,[]],
  ['Glendale (CA)','CA',196000,['intl']],
  ['Huntington Beach','CA',199000,[]],
  ['Santa Clarita','CA',225000,[]],
  ['Oxnard','CA',207000,['intl']],
  ['Garden Grove','CA',173000,['intl']],
  ['Oceanside','CA',174000,['military']],
  ['Rancho Cucamonga','CA',177000,[]],
  ['Ontario','CA',175000,[]],
  ['Corona','CA',165000,[]],
  ['Elk Grove','CA',174000,[]],
  ['Salinas','CA',160000,[]],
  ['Pomona','CA',150000,[]],
  ['Escondido','CA',150000,[]],
  ['Torrance','CA',148000,[]],
  ['Pasadena','CA',138000,['wealth']],
  ['Orange','CA',136000,[]],
  ['Fullerton','CA',137000,[]],
  ['Roseville','CA',140000,['estate']],
  ['Hayward','CA',157000,[]],
  ['Sunnyvale','CA',153000,['tech']],
  ['Victorville','CA',134000,[]],
  ['Murrieta','CA',115000,['estate']],
  ['Costa Mesa','CA',112000,[]],
  ['Santa Rosa','CA',174000,[]],
  ['Thousand Oaks','CA',126000,['wealth']],
  ['Simi Valley','CA',126000,[]],
  ['Concord','CA',130000,[]],
  ['El Monte','CA',108000,[]],
  ['Downey','CA',111000,[]],
  ['West Covina','CA',106000,[]],
  ['Inglewood','CA',107000,[]],
  ['Richmond','CA',115000,[]],
  ['Antioch','CA',115000,[]],
  ['Norwalk','CA',103000,[]],
  ['Burbank','CA',104000,[]],
  ['Daly City','CA',107000,['intl']],
  ['El Cajon','CA',103000,['intl']],
  ['Santa Clara','CA',127000,['tech']],
  ['Berkeley','CA',117000,[]],
  ['Carlsbad','CA',114000,[]],
  ['Temecula','CA',113000,['estate']],
  ['Clovis','CA',120000,[]],
  ['Visalia','CA',136000,[]],
  ['Rialto','CA',102000,[]],
  ['Jurupa Valley','CA',107000,[]],
  ['South Gate','CA',95000,[]],
  ['Mission Viejo','CA',93000,['wealth','estate']],
  ['Vacaville','CA',100000,[]],
  ['Fairfield','CA',120000,['military']],
  ['Chico','CA',100000,[]],
  ['Livermore','CA',92000,['tech']],
  ['San Mateo','CA',104000,['tech']],
  ['Santa Maria','CA',107000,[]],
  ['Vallejo','CA',120000,['military']],
  ['Hesperia','CA',100000,[]],
  ['Westminster','CA',89000,['intl']],
  ['Hawthorne','CA',87000,[]],
  ['Citrus Heights','CA',87000,[]],
  ['Alhambra','CA',82000,['intl']],
  ['Tracy','CA',95000,[]],
  ['Indio','CA',90000,['estate']],
  ['Menifee','CA',100000,[]],
  ['Ventura','CA',110000,[]],
  ['Santa Monica','CA',91000,['wealth']],
  ['Lakewood (CA)','CA',83000,[]],
  ['San Leandro','CA',90000,[]],
  // COLORADO
  ['Denver','CO',715000,['mint','shows']],
  ['Colorado Springs','CO',480000,['military']],
  ['Aurora','CO',387000,[]],
  ['Fort Collins','CO',168000,[]],
  ['Lakewood','CO',160000,[]],
  ['Thornton','CO',140000,[]],
  ['Arvada','CO',118000,[]],
  ['Westminster (CO)','CO',113000,[]],
  ['Pueblo','CO',111000,[]],
  ['Centennial','CO',109000,['wealth']],
  ['Boulder','CO',105000,['tech','wealth']],
  ['Greeley','CO',103000,[]],
  ['Longmont','CO',96000,[]],
  ['Loveland','CO',78000,[]],
  ['Castle Rock','CO',73000,['wealth']],
  ['Grand Junction','CO',63000,[]],
  ['Broomfield','CO',68000,['tech']],
  ['Parker','CO',65000,['wealth']],
  // CONNECTICUT
  ['Bridgeport','CT',148000,[]],
  ['New Haven','CT',134000,[]],
  ['Hartford','CT',121000,[]],
  ['Stamford','CT',135000,['wealth','intl']],
  ['Waterbury','CT',113000,[]],
  ['Norwalk (CT)','CT',91000,['wealth']],
  ['Danbury','CT',84000,[]],
  // DELAWARE
  ['Wilmington','DE',70800,[]],
  // FLORIDA
  ['Jacksonville','FL',949000,['military']],
  ['Miami','FL',442000,['intl','auction','stacks','estate']],
  ['Tampa','FL',400000,['estate','shows']],
  ['Orlando','FL',307000,['fun','shows','estate']],
  ['St. Petersburg','FL',258000,['estate']],
  ['Hialeah','FL',224000,['intl']],
  ['Port St. Lucie','FL',214000,['estate']],
  ['Tallahassee','FL',196000,[]],
  ['Cape Coral','FL',194000,['estate']],
  ['Fort Lauderdale','FL',182000,['intl','wealth','estate']],
  ['Pembroke Pines','FL',171000,['estate']],
  ['Hollywood','FL',153000,['intl']],
  ['Gainesville','FL',141000,[]],
  ['Miramar','FL',138000,['intl']],
  ['Coral Springs','FL',134000,['estate']],
  ['Clearwater','FL',117000,['estate']],
  ['Palm Bay','FL',120000,['military']],
  ['Pompano Beach','FL',112000,['intl','estate']],
  ['West Palm Beach','FL',112000,['wealth','estate']],
  ['Lakeland','FL',112000,['estate']],
  ['Davie','FL',105000,[]],
  ['Miami Gardens','FL',111000,['intl']],
  ['Sunrise','FL',96000,[]],
  ['Boca Raton','FL',99000,['wealth','estate']],
  ['Deltona','FL',98000,['estate']],
  ['Plantation','FL',91000,[]],
  ['Deerfield Beach','FL',82000,['estate']],
  ['Boynton Beach','FL',80000,['estate']],
  ['North Port','FL',73000,['estate']],
  ['Melbourne','FL',82000,['military']],
  ['Kissimmee','FL',76000,[]],
  ['Daytona Beach','FL',69000,['estate']],
  ['Fort Myers','FL',86000,['estate']],
  ['Ocala','FL',63000,['estate']],
  ['Sarasota','FL',57000,['wealth','estate']],
  ['Pensacola','FL',53000,['military']],
  ['Port Orange','FL',59000,['estate']],
  ['Doral','FL',72000,['intl']],
  ['Lauderhill','FL',71000,[]],
  // GEORGIA
  ['Atlanta','GA',498000,['ana','shows','auction']],
  ['Columbus (GA)','GA',206000,['military']],
  ['Augusta','GA',202000,['military']],
  ['Macon','GA',155000,[]],
  ['Savannah','GA',147000,['ana']],
  ['Athens','GA',127000,[]],
  ['Sandy Springs','GA',108000,['wealth']],
  ['Warner Robins','GA',78000,['military']],
  ['Roswell','GA',94000,['wealth']],
  ['South Fulton','GA',107000,[]],
  ['Johns Creek','GA',83000,['wealth']],
  ['Alpharetta','GA',65000,['wealth','tech']],
  // HAWAII
  ['Honolulu','HI',350000,['intl']],
  // IDAHO
  ['Boise','ID',235000,[]],
  ['Meridian','ID',114000,[]],
  ['Nampa','ID',100000,[]],
  ['Idaho Falls','ID',64000,[]],
  ['Caldwell','ID',65000,[]],
  ['Pocatello','ID',57000,[]],
  // ILLINOIS
  ['Chicago','IL',2700000,['heritage','csns','shows','auction']],
  ['Aurora','IL',180000,[]],
  ['Naperville','IL',149000,['wealth']],
  ['Joliet','IL',147000,[]],
  ['Rockford','IL',143000,[]],
  ['Elgin','IL',113000,[]],
  ['Peoria','IL',113000,[]],
  ['Springfield (IL)','IL',114000,[]],
  ['Champaign','IL',88000,[]],
  ['Waukegan','IL',87000,[]],
  ['Cicero','IL',82000,['intl']],
  ['Schaumburg','IL',74000,['csns','shows']],
  ['Bloomington (IL)','IL',78000,[]],
  ['Bolingbrook','IL',73000,[]],
  ['Evanston','IL',74000,['wealth']],
  // INDIANA
  ['Indianapolis','IN',882000,['shows']],
  ['Fort Wayne','IN',265000,[]],
  ['Evansville','IN',117000,[]],
  ['South Bend','IN',103000,[]],
  ['Carmel','IN',100000,['wealth']],
  ['Fishers','IN',99000,['wealth']],
  ['Hammond','IN',76000,[]],
  ['Gary','IN',70000,[]],
  ['Muncie','IN',66000,[]],
  ['Lafayette','IN',72000,[]],
  ['Bloomington (IN)','IN',79000,[]],
  ['Greenwood','IN',62000,[]],
  ['Noblesville','IN',71000,['wealth']],
  ['Anderson','IN',53000,[]],
  // IOWA
  ['Des Moines','IA',214000,[]],
  ['Cedar Rapids','IA',134000,[]],
  ['Davenport','IA',101000,[]],
  ['Sioux City','IA',83000,[]],
  ['Iowa City','IA',73000,[]],
  ['Waterloo','IA',67000,[]],
  ['Council Bluffs','IA',60000,[]],
  ['West Des Moines','IA',67000,['wealth']],
  // KANSAS
  ['Wichita','KS',395000,['military']],
  ['Overland Park','KS',195000,['wealth']],
  ['Kansas City (KS)','KS',153000,[]],
  ['Topeka','KS',126000,[]],
  ['Olathe','KS',140000,['wealth']],
  ['Lawrence','KS',96000,[]],
  ['Manhattan (KS)','KS',55000,['military']],
  ['Shawnee','KS',65000,[]],
  ['Lenexa','KS',55000,[]],
  // KENTUCKY
  ['Louisville','KY',633000,['shows']],
  ['Lexington','KY',323000,['wealth']],
  ['Bowling Green','KY',72000,[]],
  ['Owensboro','KY',60000,[]],
  // LOUISIANA
  ['New Orleans','LA',383000,['intl','shows']],
  ['Baton Rouge','LA',225000,[]],
  ['Shreveport','LA',181000,[]],
  ['Metairie','LA',143000,[]],
  ['Lafayette (LA)','LA',120000,[]],
  ['Lake Charles','LA',77000,[]],
  ['Kenner','LA',67000,[]],
  ['Bossier City','LA',71000,['military']],
  // MAINE
  ['Portland (ME)','ME',68000,[]],
  // MARYLAND
  ['Baltimore','MD',569000,['shows','ana','stacks','auction']],
  ['Frederick','MD',78000,['military']],
  ['Gaithersburg','MD',70000,['wealth']],
  ['Rockville','MD',67000,['wealth']],
  ['Bowie','MD',60000,[]],
  // MASSACHUSETTS
  ['Boston','MA',675000,['wealth','auction','shows']],
  ['Worcester','MA',185000,[]],
  ['Springfield (MA)','MA',153000,[]],
  ['Cambridge','MA',118000,['tech','wealth']],
  ['Lowell','MA',111000,[]],
  ['Brockton','MA',105000,[]],
  ['New Bedford','MA',99000,[]],
  ['Quincy','MA',94000,[]],
  ['Lynn','MA',93000,[]],
  ['Fall River','MA',89000,[]],
  ['Newton','MA',88000,['wealth']],
  ['Somerville','MA',81000,['tech']],
  ['Lawrence (MA)','MA',80000,[]],
  ['Framingham','MA',72000,[]],
  ['Haverhill','MA',65000,[]],
  ['Waltham','MA',60000,['tech']],
  ['Malden','MA',60000,[]],
  ['Medford','MA',57000,[]],
  // MICHIGAN
  ['Detroit','MI',620000,['shows']],
  ['Grand Rapids','MI',196000,[]],
  ['Warren','MI',138000,[]],
  ['Sterling Heights','MI',133000,[]],
  ['Ann Arbor','MI',121000,['tech']],
  ['Lansing','MI',112000,[]],
  ['Dearborn','MI',95000,['intl']],
  ['Livonia','MI',94000,[]],
  ['Clinton Township','MI',99000,[]],
  ['Troy','MI',83000,['wealth']],
  ['Farmington Hills','MI',80000,['wealth']],
  ['Macomb Township','MI',85000,[]],
  ['Westland','MI',81000,[]],
  ['Rochester Hills','MI',73000,['wealth']],
  ['Kalamazoo','MI',71000,[]],
  ['Wyoming (MI)','MI',75000,[]],
  ['Southfield','MI',73000,[]],
  ['Flint','MI',82000,[]],
  ['Waterford','MI',69000,[]],
  // MINNESOTA
  ['Minneapolis','MN',425000,['shows']],
  ['Saint Paul','MN',307000,[]],
  ['Rochester (MN)','MN',121000,[]],
  ['Duluth','MN',89000,[]],
  ['Bloomington (MN)','MN',89000,[]],
  ['Brooklyn Park','MN',81000,[]],
  ['Plymouth','MN',80000,['wealth']],
  ['Woodbury','MN',75000,['wealth']],
  ['Maple Grove','MN',70000,['wealth']],
  ['Saint Cloud','MN',66000,[]],
  ['Eagan','MN',65000,[]],
  ['Coon Rapids','MN',62000,[]],
  ['Burnsville','MN',62000,[]],
  // MISSISSIPPI
  ['Jackson','MS',153000,[]],
  ['Gulfport','MS',72000,[]],
  ['Southaven','MS',55000,[]],
  // MISSOURI
  ['Kansas City (MO)','MO',510000,['shows']],
  ['Saint Louis','MO',300000,['shows','auction']],
  ['Springfield (MO)','MO',167000,[]],
  ['Columbia (MO)','MO',126000,[]],
  ['Independence','MO',120000,[]],
  ["Lee's Summit",'MO',98000,['wealth']],
  ["O'Fallon",'MO',87000,[]],
  ['St. Joseph','MO',74000,[]],
  ['St. Charles','MO',70000,[]],
  ['St. Peters','MO',57000,[]],
  ['Blue Springs','MO',55000,[]],
  ['Joplin','MO',52000,[]],
  // MONTANA
  ['Billings','MT',117000,[]],
  ['Missoula','MT',73000,[]],
  ['Great Falls','MT',58000,['military']],
  ['Bozeman','MT',54000,['wealth']],
  // NEBRASKA
  ['Omaha','NE',486000,['wealth']],
  ['Lincoln','NE',289000,[]],
  ['Bellevue','NE',64000,['military']],
  ['Grand Island','NE',52000,[]],
  // NEVADA
  ['Las Vegas','NV',641000,['pawn','intl','shows','wealth']],
  ['Henderson','NV',320000,['wealth','estate']],
  ['Reno','NV',255000,['pawn']],
  ['North Las Vegas','NV',262000,[]],
  ['Sparks','NV',98000,[]],
  ['Carson City','NV',58000,[]],
  // NEW HAMPSHIRE
  ['Manchester','NH',115000,[]],
  ['Nashua','NH',90000,[]],
  // NEW JERSEY
  ['Newark','NJ',311000,['intl']],
  ['Jersey City','NJ',292000,['intl','wealth']],
  ['Paterson','NJ',157000,['intl']],
  ['Elizabeth','NJ',137000,['intl']],
  ['Lakewood (NJ)','NJ',135000,[]],
  ['Edison','NJ',107000,['intl']],
  ['Woodbridge','NJ',99000,[]],
  ['Toms River','NJ',92000,['estate']],
  ['Hamilton (NJ)','NJ',87000,[]],
  ['Clifton','NJ',83000,['intl']],
  ['Trenton','NJ',83000,[]],
  ['Camden','NJ',74000,[]],
  ['Passaic','NJ',69000,['intl']],
  ['Union City','NJ',68000,['intl']],
  ['East Orange','NJ',65000,[]],
  ['Bayonne','NJ',65000,[]],
  ['Vineland','NJ',60000,[]],
  ['New Brunswick','NJ',55000,[]],
  ['Perth Amboy','NJ',52000,['intl']],
  // NEW MEXICO
  ['Albuquerque','NM',560000,[]],
  ['Las Cruces','NM',114000,['military']],
  ['Rio Rancho','NM',105000,[]],
  ['Santa Fe','NM',84000,['wealth']],
  // NEW YORK
  ['New York City','NY',8300000,['heritage','stacks','auction','shows','intl','wealth']],
  ['Buffalo','NY',278000,[]],
  ['Rochester (NY)','NY',211000,[]],
  ['Yonkers','NY',211000,['intl']],
  ['Syracuse','NY',148000,['shows']],
  ['Albany','NY',99000,[]],
  ['New Rochelle','NY',79000,['wealth']],
  ['Mount Vernon','NY',73000,[]],
  ['Schenectady','NY',66000,[]],
  ['Utica','NY',60000,[]],
  ['White Plains','NY',57000,['wealth']],
  ['Troy (NY)','NY',51000,[]],
  // NORTH CAROLINA
  ['Charlotte','NC',879000,['shows','wealth']],
  ['Raleigh','NC',467000,['tech','shows']],
  ['Greensboro','NC',296000,[]],
  ['Durham','NC',283000,['tech']],
  ['Winston-Salem','NC',250000,[]],
  ['Fayetteville (NC)','NC',208000,['military']],
  ['Cary','NC',170000,['tech','wealth']],
  ['Wilmington (NC)','NC',120000,['estate']],
  ['High Point','NC',112000,[]],
  ['Concord (NC)','NC',101000,[]],
  ['Asheville','NC',92000,[]],
  ['Jacksonville (NC)','NC',74000,['military']],
  ['Gastonia','NC',82000,[]],
  ['Rocky Mount','NC',54000,[]],
  ['Kannapolis','NC',50000,[]],
  // NORTH DAKOTA
  ['Fargo','ND',125000,[]],
  ['Bismarck','ND',73000,[]],
  ['Grand Forks','ND',57000,['military']],
  // OHIO
  ['Columbus (OH)','OH',898000,['shows']],
  ['Cleveland','OH',365000,['shows']],
  ['Cincinnati','OH',309000,['shows']],
  ['Toledo','OH',270000,[]],
  ['Akron','OH',190000,[]],
  ['Dayton','OH',137000,['military']],
  ['Parma','OH',79000,[]],
  ['Canton','OH',70000,[]],
  ['Youngstown','OH',60000,[]],
  ['Lorain','OH',63000,[]],
  ['Hamilton (OH)','OH',62000,[]],
  ['Springfield (OH)','OH',58000,[]],
  ['Kettering','OH',57000,[]],
  ['Elyria','OH',53000,[]],
  ['Lakewood (OH)','OH',50000,[]],
  ['Dublin (OH)','OH',50000,['wealth']],
  // OKLAHOMA
  ['Oklahoma City','OK',681000,['military']],
  ['Tulsa','OK',413000,[]],
  ['Norman','OK',122000,[]],
  ['Broken Arrow','OK',114000,[]],
  ['Lawton','OK',91000,['military']],
  ['Edmond','OK',90000,['wealth']],
  ['Moore','OK',60000,[]],
  ['Midwest City','OK',56000,['military']],
  ['Enid','OK',51000,[]],
  // OREGON
  ['Portland','OR',652000,['pawn','shows']],
  ['Salem','OR',175000,[]],
  ['Eugene','OR',172000,[]],
  ['Gresham','OR',111000,[]],
  ['Hillsboro','OR',106000,['tech']],
  ['Bend','OR',97000,['wealth']],
  ['Beaverton','OR',98000,['tech']],
  ['Medford','OR',83000,[]],
  ['Springfield (OR)','OR',60000,[]],
  ['Corvallis','OR',58000,[]],
  // PENNSYLVANIA
  ['Philadelphia','PA',1560000,['auction','shows']],
  ['Pittsburgh','PA',305000,['ana','shows']],
  ['Allentown','PA',125000,[]],
  ['Erie','PA',95000,[]],
  ['Reading','PA',95000,['intl']],
  ['Scranton','PA',77000,[]],
  ['Bethlehem','PA',76000,[]],
  ['Lancaster','PA',59000,[]],
  ['Harrisburg','PA',50000,[]],
  // RHODE ISLAND
  ['Providence','RI',190000,[]],
  ['Cranston','RI',82000,[]],
  ['Warwick','RI',82000,[]],
  ['Pawtucket','RI',75000,[]],
  // SOUTH CAROLINA
  ['Charleston','SC',150000,['wealth','estate']],
  ['Columbia (SC)','SC',136000,['military']],
  ['North Charleston','SC',114000,['military']],
  ['Mount Pleasant','SC',93000,['wealth']],
  ['Rock Hill','SC',73000,[]],
  ['Greenville','SC',70000,[]],
  ['Summerville','SC',53000,[]],
  // SOUTH DAKOTA
  ['Sioux Falls','SD',192000,[]],
  ['Rapid City','SD',74000,[]],
  // TENNESSEE
  ['Nashville','TN',689000,['shows','wealth']],
  ['Memphis','TN',635000,[]],
  ['Knoxville','TN',190000,[]],
  ['Chattanooga','TN',181000,[]],
  ['Clarksville','TN',159000,['military']],
  ['Murfreesboro','TN',150000,[]],
  ['Franklin','TN',83000,['wealth']],
  ['Jackson (TN)','TN',67000,[]],
  ['Johnson City','TN',67000,[]],
  ['Kingsport','TN',54000,[]],
  ['Bartlett','TN',59000,[]],
  ['Hendersonville','TN',58000,[]],
  // TEXAS
  ['Houston','TX',2300000,['heritage','intl','shows','refinery']],
  ['San Antonio','TX',1434000,['military','shows']],
  ['Dallas','TX',1304000,['heritage','shows','auction']],
  ['Austin','TX',979000,['tech','shows']],
  ['Fort Worth','TX',918000,['heritage','shows']],
  ['El Paso','TX',678000,['military','intl']],
  ['Arlington','TX',394000,[]],
  ['Corpus Christi','TX',316000,['military']],
  ['Plano','TX',285000,['wealth','tech']],
  ['Laredo','TX',261000,['intl']],
  ['Lubbock','TX',258000,['military']],
  ['Garland','TX',238000,['intl']],
  ['Irving','TX',236000,['intl']],
  ['Amarillo','TX',200000,[]],
  ['McKinney','TX',195000,['wealth']],
  ['Frisco','TX',200000,['wealth','tech']],
  ['Grand Prairie','TX',194000,[]],
  ['Brownsville','TX',184000,['intl']],
  ['Killeen','TX',150000,['military']],
  ['Pasadena (TX)','TX',151000,[]],
  ['McAllen','TX',143000,['intl']],
  ['Denton','TX',141000,[]],
  ['Mesquite','TX',141000,[]],
  ['Waco','TX',139000,[]],
  ['Carrollton','TX',131000,['intl']],
  ['Midland','TX',130000,['wealth']],
  ['Round Rock','TX',128000,['tech']],
  ['Beaumont','TX',116000,[]],
  ['Odessa','TX',114000,['wealth']],
  ['Abilene','TX',125000,['military']],
  ['Pearland','TX',120000,['wealth']],
  ['Richardson','TX',120000,['tech']],
  ['Sugar Land','TX',118000,['intl','wealth']],
  ['College Station','TX',117000,[]],
  ['Tyler','TX',103000,[]],
  ['Lewisville','TX',107000,[]],
  ['League City','TX',105000,['wealth']],
  ['Wichita Falls','TX',102000,['military']],
  ['New Braunfels','TX',100000,[]],
  ['Conroe','TX',85000,[]],
  ['Allen','TX',98000,['wealth']],
  ['Edinburg','TX',96000,['intl']],
  ['Mission (TX)','TX',84000,['intl']],
  ['Pharr','TX',78000,['intl']],
  ['Flower Mound','TX',77000,['wealth']],
  ['Baytown','TX',78000,[]],
  ['San Angelo','TX',99000,[]],
  ['Longview','TX',82000,[]],
  ['Mansfield','TX',71000,[]],
  ['Cedar Park','TX',77000,['tech']],
  ['Temple','TX',76000,['military']],
  ['Harlingen','TX',64000,['intl']],
  ['Rowlett','TX',66000,[]],
  ['North Richland Hills','TX',69000,[]],
  // UTAH
  ['Salt Lake City','UT',200000,['shows','mint']],
  ['West Valley City','UT',136000,[]],
  ['Provo','UT',115000,[]],
  ['West Jordan','UT',113000,[]],
  ['Orem','UT',98000,[]],
  ['Sandy','UT',96000,[]],
  ['Ogden','UT',87000,[]],
  ['St. George','UT',90000,['estate']],
  ['South Jordan','UT',75000,['wealth']],
  ['Layton','UT',78000,['military']],
  ['Lehi','UT',71000,['tech']],
  ['Taylorsville','UT',59000,[]],
  ['Millcreek','UT',62000,[]],
  // VERMONT (no cities over 50k — Burlington ~44k)
  // VIRGINIA
  ['Virginia Beach','VA',459000,['military','estate']],
  ['Norfolk','VA',238000,['military']],
  ['Chesapeake','VA',244000,['military']],
  ['Arlington (VA)','VA',236000,['wealth','military']],
  ['Richmond','VA',226000,['shows']],
  ['Newport News','VA',187000,['military']],
  ['Alexandria','VA',160000,['wealth','military']],
  ['Hampton','VA',137000,['military']],
  ['Roanoke','VA',100000,[]],
  ['Portsmouth','VA',96000,['military']],
  ['Suffolk','VA',90000,[]],
  ['Lynchburg','VA',80000,['military']],
  ['Harrisonburg','VA',54000,[]],
  ['Leesburg','VA',55000,['wealth']],
  // WASHINGTON — TAXED 10.25%
  ['Seattle','WA',737000,['tech','wealth']],
  ['Spokane','WA',222000,[]],
  ['Tacoma','WA',219000,['military']],
  ['Vancouver (WA)','WA',190000,[]],
  ['Bellevue','WA',147000,['tech','wealth']],
  ['Kent','WA',130000,[]],
  ['Everett','WA',112000,['military']],
  ['Renton','WA',106000,['tech']],
  ['Federal Way','WA',95000,[]],
  ['Spokane Valley','WA',97000,[]],
  ['Kirkland','WA',92000,['tech','wealth']],
  ['Bellingham','WA',90000,[]],
  ['Kennewick','WA',82000,[]],
  ['Yakima','WA',92000,[]],
  ['Auburn (WA)','WA',82000,[]],
  ['Marysville','WA',65000,[]],
  ['Pasco','WA',75000,[]],
  ['Lakewood (WA)','WA',64000,['military']],
  ['Redmond','WA',68000,['tech','wealth']],
  ['Sammamish','WA',66000,['wealth','tech']],
  ['Shoreline','WA',55000,[]],
  ['Richland','WA',57000,[]],
  ['Burien','WA',52000,[]],
  // WEST VIRGINIA (largest cities under 50k)
  // WISCONSIN
  ['Milwaukee','WI',577000,['shows']],
  ['Madison','WI',269000,['tech']],
  ['Green Bay','WI',107000,[]],
  ['Kenosha','WI',100000,[]],
  ['Racine','WI',77000,[]],
  ['Appleton','WI',75000,[]],
  ['Waukesha','WI',72000,['wealth']],
  ['Oshkosh','WI',66000,[]],
  ['Eau Claire','WI',65000,[]],
  ['Janesville','WI',66000,[]],
  ['West Allis','WI',61000,[]],
  ['La Crosse','WI',51000,[]],
  // WYOMING
  ['Cheyenne','WY',64000,['military']],
  ['Casper','WY',58000,[]],
  // DC
  ['Washington D.C.','DC',689000,['wealth','intl','auction','shows','military']],
];

// ══════════════════════════════════════════════════════
// SCORING
// ══════════════════════════════════════════════════════
function bScore(st, pop, flags) {
  let s = 5.0;
  const tax = STATE_TAX[st];
  if (tax.status==='notax') s += 2.0;
  else if (tax.status==='exempt') s += 1.5;
  else if (tax.status==='partial') s += 0.8;
  else if (tax.status==='expiring') s += 1.2;
  else if (tax.tax <= 5.5) s -= 1.2;
  else if (tax.tax <= 6.5) s -= 2.0;
  else s -= 3.8; // WA 10.25%
  if (pop >= 1000000) s += 1.2;
  else if (pop >= 500000) s += 0.9;
  else if (pop >= 200000) s += 0.6;
  else if (pop >= 100000) s += 0.3;
  if (flags.includes('pawn')) s += 0.6;
  if (flags.includes('estate')) s += 0.4;
  if (flags.includes('military')) s += 0.2;
  if (flags.includes('intl')) s += 0.3;
  if (flags.includes('mint')) s += 0.2;
  return Math.min(9.9, Math.max(1.0, s));
}
function sScore(st, pop, flags) {
  let s = 5.0;
  if (pop >= 2000000) s += 2.5;
  else if (pop >= 1000000) s += 2.0;
  else if (pop >= 500000) s += 1.5;
  else if (pop >= 200000) s += 1.0;
  else if (pop >= 100000) s += 0.5;
  if (flags.includes('heritage')) s += 1.8;
  if (flags.includes('stacks')) s += 1.5;
  if (flags.includes('auction')) s += 1.0;
  if (flags.includes('fun')) s += 1.2;
  if (flags.includes('ana')) s += 0.8;
  if (flags.includes('csns')) s += 0.8;
  if (flags.includes('shows')) s += 0.5;
  if (flags.includes('intl')) s += 0.4;
  if (flags.includes('wealth')) s += 0.3;
  return Math.min(9.9, Math.max(1.0, s));
}
function showsEst(pop, flags) {
  let base = flags.includes('fun') ? 10 : flags.includes('ana')||flags.includes('csns') ? 6 : flags.includes('shows') ? 5 : 2;
  if (pop >= 1000000) base += 4;
  else if (pop >= 500000) base += 2;
  else if (pop >= 200000) base += 1;
  return base;
}
function scoreColor(v) {
  if (v >= 8.5) return 'var(--green)';
  if (v >= 7.0) return 'var(--gold)';
  if (v >= 5.5) return '#FFA500';
  return 'var(--red)';
}
function taxBadge(st) {
  const t = STATE_TAX[st];
  if (t.status==='notax') return ['tb-free','No Tax'];
  if (t.status==='exempt') return ['tb-free','Tax-Free'];
  if (t.status==='partial') return ['tb-part','Partial'];
  if (t.status==='expiring') return ['tb-exp','⚡ Expiring'];
  return ['tb-taxed', t.tax+'%'];
}
function tagLabel(f) {
  const m={heritage:'Heritage Auctions',stacks:"Stack's Bowers",fun:'FUN Show',ana:'ANA Show',csns:'Central States',pawn:'Pawn Density',estate:'Estate Sales',military:'Military',intl:'Intl Buyers',tech:'Tech Wealth',wealth:'High Wealth',mint:'US Mint',refinery:'Refinery',shows:'Coin Shows',auction:'Auction Hub'};
  return m[f]||f;
}

// Build CITIES array
const CITIES = RAW.map(r => {
  const [city, st, pop, flags] = r;
  return {
    city, state: st, stateName: STATE_TAX[st]?.name||st, pop,
    flags,
    buyer: bScore(st, pop, flags),
    seller: sScore(st, pop, flags),
    shows: showsEst(pop, flags),
    tax: STATE_TAX[st]
  };
});

// ══════════════════════════════════════════════════════
// STATE LEGEND
// ══════════════════════════════════════════════════════
function buildStateLegend() {
  const el = document.getElementById('stateLegend');
  const states = Object.entries(STATE_TAX).sort((a,b)=>a[1].name.localeCompare(b[1].name));
  el.innerHTML = states.map(([abbr, d]) => {
    let cls='si-tax ';
    let label=d.note;
    if (d.status==='notax'){cls+='tb-free';label='No Sales Tax';}
    else if (d.status==='exempt'){cls+='tb-free';label='✅ Exempt';}
    else if (d.status==='partial'){cls+='tb-part';label='Partial';}
    else if (d.status==='expiring'){cls+='tb-exp';label='⚡ Expires Jul 2026';}
    else{cls+='tb-taxed';label='⚠ '+d.tax+'% tax';}
    return `<div class="state-item"><span class="si-name">${d.name}</span><span class="${cls}">${label}</span></div>`;
  }).join('');
}

// ══════════════════════════════════════════════════════
// CITY TABLE + CARDS
// ══════════════════════════════════════════════════════
let currentFilter = 'all';
let currentSort = 'buyer';
let currentSearch = '';
let currentState = 'ALL';
let currentPage = 1;
const PAGE_SIZE = 30;
let sortDir = {buyer:-1, seller:-1, pop:-1, city:1};

function filteredCities() {
  let list = [...CITIES];
  if (currentState !== 'ALL') list = list.filter(c => c.state === currentState);
  if (currentSearch) {
    const q = currentSearch.toLowerCase();
    list = list.filter(c => c.city.toLowerCase().includes(q) || c.stateName.toLowerCase().includes(q) || c.state.toLowerCase().includes(q));
  }
  if (currentFilter === 'buyer') list = list.filter(c => c.buyer >= 7.5);
  else if (currentFilter === 'seller') list = list.filter(c => c.seller >= 7.5);
  else if (currentFilter === 'notax') list = list.filter(c => c.tax.tax === 0);
  else if (currentFilter === 'shows') list = list.filter(c => c.shows >= 5);
  else if (currentFilter === 'taxed') list = list.filter(c => c.tax.tax > 0 || c.tax.status==='partial'||c.tax.status==='expiring');
  // sort
  list.sort((a,b)=>{
    if (currentSort==='buyer') return (b.buyer - a.buyer) * -sortDir.buyer;
    if (currentSort==='seller') return (b.seller - a.seller) * -sortDir.seller;
    if (currentSort==='pop') return (b.pop - a.pop) * -sortDir.pop;
    if (currentSort==='city') return a.city.localeCompare(b.city) * sortDir.city;
    return 0;
  });
  return list;
}

function buildTopCards(list) {
  const top = list.slice(0, 6);
  const grid = document.getElementById('topCards');
  if (!top.length) { grid.innerHTML='<div style="color:var(--txt2);font-size:.85rem;">No cities match your filters.</div>'; return; }
  grid.innerHTML = top.map((c, i) => {
    const [tbcls, tblbl] = taxBadge(c.state);
    const bv = c.buyer.toFixed(1), sv = c.seller.toFixed(1);
    const topTags = c.flags.slice(0,3).map(f=>`<span class="ctag">${tagLabel(f)}</span>`).join('');
    const rankBadge = i < 3 ? `<div class="rank-pill rk${i+1}">#${i+1}</div>` : '';
    return `<div class="city-card">${rankBadge}
      <div class="cc-top">
        <div><div class="cc-name">${c.city}</div><div class="cc-state">${c.stateName} · ${c.state}</div></div>
        <span class="tax-badge ${tbcls}">${tblbl}</span>
      </div>
      <div class="cc-scores">
        <div class="cc-score"><div class="csl">Buyer Score</div><div class="csv" style="color:${scoreColor(c.buyer)}">${bv}</div><div class="cbar"><div class="cbar-f" style="width:${c.buyer*10}%;background:${scoreColor(c.buyer)}"></div></div></div>
        <div class="cc-score"><div class="csl">Seller Score</div><div class="csv" style="color:${scoreColor(c.seller)}">${sv}</div><div class="cbar"><div class="cbar-f" style="width:${c.seller*10}%;background:${scoreColor(c.seller)}"></div></div></div>
      </div>
      <div class="cc-meta"><span>🗓 ${c.shows} shows/yr</span><span>👥 ${(c.pop/1000).toFixed(0)}k pop</span><span style="color:${c.tax.tax>0?'var(--red)':'var(--green)'}">${c.tax.tax>0?'⚠ +'+c.tax.tax+'%':'✅ No Tax'}</span></div>
      <div class="cc-tags">${topTags||'<span class="ctag">General Market</span>'}</div>
    </div>`;
  }).join('');
}

function buildTable(list) {
  const total = list.length;
  const pages = Math.ceil(total / PAGE_SIZE);
  if (currentPage > pages) currentPage = 1;
  const slice = list.slice((currentPage-1)*PAGE_SIZE, currentPage*PAGE_SIZE);
  document.getElementById('resultCount').textContent = total + ' CITIES';
  document.getElementById('resultsInfo').textContent = `Showing ${(currentPage-1)*PAGE_SIZE+1}–${Math.min(currentPage*PAGE_SIZE,total)} of ${total} cities`;
  const tbody = document.getElementById('cityTbody');
  tbody.innerHTML = slice.map(c => {
    const [tbcls, tblbl] = taxBadge(c.state);
    const bv = c.buyer.toFixed(1), sv = c.seller.toFixed(1);
    const topFlags = c.flags.slice(0,2).map(f=>`<span class="ctag">${tagLabel(f)}</span>`).join(' ');
    let verdict = '';
    if (c.tax.tax > 8) verdict = '<span style="color:var(--red);font-size:.72rem;">⚠️ Avoid buying — heavy tax</span>';
    else if (c.tax.status==='expiring') verdict = '<span style="color:#FFA500;font-size:.72rem;">⚡ Buy before Jul 1 2026</span>';
    else if (c.buyer >= 8.5 && c.seller >= 8.5) verdict = '<span class="abadge ab-hot">🔥 Elite Both</span>';
    else if (c.buyer >= 8.5) verdict = '<span class="abadge ab-hot">Buy Here</span>';
    else if (c.seller >= 8.5) verdict = '<span class="abadge ab-warm">Sell Here</span>';
    else if (c.tax.tax > 0) verdict = '<span class="abadge ab-cold">Buy Online</span>';
    else verdict = '<span class="abadge ab-warm">⚡ Solid</span>';
    return `<tr>
      <td><strong>${c.city}</strong></td>
      <td>${c.state}</td>
      <td>${(c.pop/1000).toFixed(0)}k</td>
      <td><span class="tax-badge ${tbcls}" style="font-size:.7rem;">${tblbl}</span></td>
      <td><strong style="color:${scoreColor(c.buyer)}">${bv}</strong></td>
      <td><strong style="color:${scoreColor(c.seller)}">${sv}</strong></td>
      <td>${c.shows}</td>
      <td>${topFlags||'—'}</td>
      <td>${verdict}</td>
    </tr>`;
  }).join('');
  // Pagination
  const pg = document.getElementById('pgBtns');
  if (pages <= 1) { pg.innerHTML=''; return; }
  let html = '';
  for (let i=1; i<=pages; i++) html += `<button class="pg-btn ${i===currentPage?'on':''}" data-p="${i}">${i}</button>`;
  pg.innerHTML = html;
  pg.querySelectorAll('.pg-btn').forEach(b => b.addEventListener('click', function(){
    currentPage = parseInt(this.dataset.p);
    render();
    document.getElementById('cityExplorer').scrollIntoView({behavior:'smooth', block:'start'});
  }));
}

function render() {
  const list = filteredCities();
  buildTopCards(list);
  buildTable(list);
}

// ══════════════════════════════════════════════════════
// INIT & EVENTS
// ══════════════════════════════════════════════════════

// Populate state dropdown
const sel = document.getElementById('stateFilter');
Object.entries(STATE_TAX).sort((a,b)=>a[1].name.localeCompare(b[1].name)).forEach(([abbr,d])=>{
  const opt = document.createElement('option');
  opt.value = abbr; opt.textContent = d.name + ' (' + abbr + ')';
  sel.appendChild(opt);
});

// Sort buttons
document.querySelectorAll('.sort-btn').forEach(b => {
  b.addEventListener('click', function() {
    const col = this.dataset.sort;
    if (currentSort === col) sortDir[col] *= -1;
    currentSort = col;
    document.querySelectorAll('.sort-btn').forEach(x=>x.classList.remove('on'));
    this.classList.add('on');
    currentPage = 1;
    render();
  });
});

// Table header sort
document.querySelectorAll('#cityTable thead th[data-col]').forEach(th => {
  th.addEventListener('click', function() {
    const col = this.dataset.col;
    if (!col) return;
    if (currentSort === col) sortDir[col] *= -1;
    currentSort = col;
    currentPage = 1;
    render();
  });
});

// Filter chips
document.querySelectorAll('.city-f').forEach(chip => {
  chip.addEventListener('click', function() {
    document.querySelectorAll('.city-f').forEach(c=>c.classList.remove('on'));
    this.classList.add('on');
    currentFilter = this.dataset.f;
    currentPage = 1;
    render();
  });
});

// Search
document.getElementById('citySearch').addEventListener('input', function() {
  currentSearch = this.value.trim();
  currentPage = 1;
  render();
});

// State dropdown
document.getElementById('stateFilter').addEventListener('change', function() {
  currentState = this.value;
  currentPage = 1;
  render();
});

// Existing tab/chip handlers
document.querySelectorAll('.tab').forEach(btn => {
  btn.addEventListener('click', function() {
    document.querySelectorAll('.tab').forEach(b=>b.classList.remove('on'));
    this.classList.add('on');
  });
});
document.querySelectorAll('.chip:not(.city-f)').forEach(chip => {
  chip.addEventListener('click', function() {
    const parent = this.parentElement;
    parent.querySelectorAll('.chip:not(.city-f)').forEach(c=>c.classList.remove('on'));
    this.classList.add('on');
  });
});

buildStateLegend();
render();

// ══════════════════════════════════════════════════════
// CITY COORDINATES (lat, lon)
// ══════════════════════════════════════════════════════
const COORDS = {
  'Birmingham':[33.52,-86.80],'Huntsville':[34.73,-86.59],'Montgomery':[32.37,-86.30],
  'Mobile':[30.69,-88.04],'Tuscaloosa':[33.21,-87.57],'Hoover':[33.40,-86.81],'Auburn':[32.61,-85.48],
  'Anchorage':[61.22,-149.90],
  'Phoenix':[33.45,-112.07],'Tucson':[32.22,-110.97],'Mesa':[33.42,-111.83],
  'Chandler':[33.31,-111.84],'Scottsdale':[33.49,-111.93],'Gilbert':[33.35,-111.79],
  'Glendale':[33.54,-112.19],'Tempe':[33.43,-111.94],'Peoria':[33.58,-112.24],
  'Surprise':[33.63,-112.37],'Goodyear':[33.44,-112.36],'Avondale':[33.43,-112.35],
  'Flagstaff':[35.20,-111.65],'Yuma':[32.69,-114.63],'Buckeye':[33.37,-112.58],
  'Casa Grande':[32.88,-111.76],'Lake Havasu City':[34.48,-114.32],'Maricopa':[33.06,-112.05],
  'Little Rock':[34.75,-92.29],'Fort Smith':[35.39,-94.40],'Fayetteville':[36.07,-94.16],
  'Springdale':[36.19,-94.13],'Jonesboro':[35.84,-90.70],
  'Los Angeles':[34.05,-118.24],'San Diego':[32.72,-117.16],'San Jose':[37.34,-121.89],
  'San Francisco':[37.77,-122.42],'Fresno':[36.74,-119.77],'Sacramento':[38.58,-121.49],
  'Long Beach':[33.77,-118.19],'Oakland':[37.80,-122.27],'Bakersfield':[35.37,-119.02],
  'Anaheim':[33.83,-117.91],'Santa Ana':[33.75,-117.87],'Riverside':[33.98,-117.37],
  'Stockton':[37.96,-121.29],'Chula Vista':[32.64,-117.08],'Irvine':[33.68,-117.82],
  'Fremont':[37.55,-121.99],'San Bernardino':[34.10,-117.29],'Modesto':[37.64,-120.99],
  'Fontana':[34.09,-117.43],'Moreno Valley':[33.94,-117.23],'Glendale (CA)':[34.14,-118.26],
  'Huntington Beach':[33.66,-117.99],'Santa Clarita':[34.39,-118.54],'Oxnard':[34.20,-119.18],
  'Garden Grove':[33.78,-117.94],'Oceanside':[33.20,-117.38],'Rancho Cucamonga':[34.11,-117.59],
  'Ontario':[34.06,-117.65],'Corona':[33.88,-117.57],'Elk Grove':[38.41,-121.37],
  'Salinas':[36.68,-121.66],'Pomona':[34.06,-117.75],'Escondido':[33.12,-117.09],
  'Torrance':[33.84,-118.34],'Pasadena':[34.15,-118.14],'Orange':[33.79,-117.85],
  'Fullerton':[33.87,-117.93],'Roseville':[38.75,-121.29],'Hayward':[37.67,-122.08],
  'Sunnyvale':[37.37,-122.04],'Victorville':[34.54,-117.29],'Murrieta':[33.55,-117.21],
  'Costa Mesa':[33.64,-117.92],'Santa Rosa':[38.44,-122.71],'Thousand Oaks':[34.17,-118.84],
  'Simi Valley':[34.27,-118.74],'Concord':[37.98,-122.03],'El Monte':[34.07,-118.03],
  'Downey':[33.94,-118.13],'West Covina':[34.07,-117.94],'Inglewood':[33.96,-118.35],
  'Richmond':[37.94,-122.35],'Antioch':[38.00,-121.81],'Norwalk':[33.90,-118.08],
  'Burbank':[34.18,-118.31],'Daly City':[37.71,-122.47],'El Cajon':[32.79,-116.96],
  'Santa Clara':[37.35,-121.95],'Berkeley':[37.87,-122.27],'Carlsbad':[33.16,-117.35],
  'Temecula':[33.49,-117.15],'Clovis':[36.83,-119.70],'Visalia':[36.33,-119.29],
  'Rialto':[34.11,-117.39],'Jurupa Valley':[33.99,-117.49],'South Gate':[33.95,-118.21],
  'Mission Viejo':[33.60,-117.66],'Vacaville':[38.36,-121.99],'Fairfield':[38.25,-122.04],
  'Chico':[39.73,-121.84],'Livermore':[37.68,-121.77],'San Mateo':[37.56,-122.32],
  'Santa Maria':[34.95,-120.44],'Vallejo':[38.10,-122.26],'Hesperia':[34.43,-117.30],
  'Westminster':[33.75,-117.99],'Hawthorne':[33.92,-118.35],'Citrus Heights':[38.71,-121.28],
  'Alhambra':[34.10,-118.13],'Tracy':[37.74,-121.43],'Indio':[33.72,-116.22],
  'Menifee':[33.69,-117.19],'Ventura':[34.28,-119.29],'Santa Monica':[34.02,-118.50],
  'Lakewood (CA)':[33.85,-118.13],'San Leandro':[37.73,-122.16],
  'Denver':[39.74,-104.98],'Colorado Springs':[38.83,-104.82],'Aurora':[39.73,-104.83],
  'Fort Collins':[40.59,-105.08],'Lakewood':[39.70,-105.08],'Thornton':[39.87,-104.97],
  'Arvada':[39.80,-105.09],'Westminster (CO)':[39.84,-105.04],'Pueblo':[38.25,-104.61],
  'Centennial':[39.58,-104.88],'Boulder':[40.01,-105.27],'Greeley':[40.42,-104.71],
  'Longmont':[40.17,-105.10],'Loveland':[40.40,-105.07],'Castle Rock':[39.37,-104.86],
  'Grand Junction':[39.06,-108.55],'Broomfield':[39.92,-105.09],'Parker':[39.52,-104.76],
  'Bridgeport':[41.17,-73.21],'New Haven':[41.31,-72.92],'Hartford':[41.76,-72.68],
  'Stamford':[41.05,-73.54],'Waterbury':[41.56,-73.05],'Norwalk (CT)':[41.12,-73.41],'Danbury':[41.39,-73.45],
  'Wilmington':[39.75,-75.55],
  'Jacksonville':[30.33,-81.66],'Miami':[25.77,-80.19],'Tampa':[27.95,-82.46],
  'Orlando':[28.54,-81.38],'St. Petersburg':[27.77,-82.64],'Hialeah':[25.86,-80.28],
  'Port St. Lucie':[27.29,-80.35],'Tallahassee':[30.44,-84.28],'Cape Coral':[26.56,-81.95],
  'Fort Lauderdale':[26.12,-80.14],'Pembroke Pines':[26.01,-80.30],'Hollywood':[26.01,-80.15],
  'Gainesville':[29.65,-82.32],'Miramar':[25.99,-80.23],'Coral Springs':[26.27,-80.27],
  'Clearwater':[27.97,-82.80],'Palm Bay':[28.03,-80.59],'Pompano Beach':[26.24,-80.12],
  'West Palm Beach':[26.71,-80.06],'Lakeland':[28.04,-81.95],'Davie':[26.07,-80.25],
  'Miami Gardens':[25.94,-80.25],'Sunrise':[26.17,-80.26],'Boca Raton':[26.36,-80.08],
  'Deltona':[28.90,-81.24],'Plantation':[26.13,-80.24],'Deerfield Beach':[26.32,-80.10],
  'Boynton Beach':[26.53,-80.07],'North Port':[27.05,-82.24],'Melbourne':[28.08,-80.61],
  'Kissimmee':[28.29,-81.41],'Daytona Beach':[29.21,-81.02],'Fort Myers':[26.64,-81.87],
  'Ocala':[29.19,-82.14],'Sarasota':[27.34,-82.53],'Pensacola':[30.42,-87.22],
  'Port Orange':[29.11,-81.01],'Doral':[25.82,-80.35],'Lauderhill':[26.17,-80.21],
  'Atlanta':[33.75,-84.39],'Columbus (GA)':[32.46,-84.99],'Augusta':[33.47,-82.01],
  'Macon':[32.84,-83.63],'Savannah':[32.08,-81.09],'Athens':[33.96,-83.38],
  'Sandy Springs':[33.92,-84.38],'Warner Robins':[32.61,-83.60],'Roswell':[34.02,-84.36],
  'South Fulton':[33.63,-84.56],'Johns Creek':[34.03,-84.20],'Alpharetta':[34.08,-84.30],
  'Honolulu':[21.31,-157.82],
  'Boise':[43.62,-116.20],'Meridian':[43.62,-116.39],'Nampa':[43.58,-116.56],
  'Idaho Falls':[43.49,-112.03],'Caldwell':[43.66,-116.69],'Pocatello':[42.87,-112.45],
  'Chicago':[41.88,-87.63],'Aurora (IL)':[41.76,-88.32],'Naperville':[41.79,-88.15],
  'Joliet':[41.52,-88.08],'Rockford':[42.27,-89.09],'Elgin':[42.04,-88.29],
  'Peoria':[40.69,-89.59],'Springfield (IL)':[39.80,-89.65],'Champaign':[40.12,-88.24],
  'Waukegan':[42.36,-87.84],'Cicero':[41.85,-87.75],'Schaumburg':[42.03,-88.08],
  'Bloomington (IL)':[40.48,-88.99],'Bolingbrook':[41.70,-88.07],'Evanston':[42.05,-87.69],
  'Indianapolis':[39.77,-86.16],'Fort Wayne':[41.13,-85.13],'Evansville':[37.97,-87.56],
  'South Bend':[41.68,-86.25],'Carmel':[39.98,-86.12],'Fishers':[39.96,-86.01],
  'Hammond':[41.59,-87.50],'Gary':[41.59,-87.35],'Muncie':[40.19,-85.39],
  'Lafayette':[40.42,-86.88],'Bloomington (IN)':[39.16,-86.53],'Greenwood':[39.61,-86.11],
  'Noblesville':[40.05,-86.01],'Anderson':[40.10,-85.68],
  'Des Moines':[41.59,-93.62],'Cedar Rapids':[41.98,-91.67],'Davenport':[41.52,-90.58],
  'Sioux City':[42.50,-96.40],'Iowa City':[41.66,-91.53],'Waterloo':[42.50,-92.34],
  'Council Bluffs':[41.26,-95.86],'West Des Moines':[41.58,-93.71],
  'Wichita':[37.69,-97.34],'Overland Park':[38.90,-94.67],'Kansas City (KS)':[39.11,-94.63],
  'Topeka':[39.05,-95.69],'Olathe':[38.88,-94.82],'Lawrence':[38.97,-95.24],
  'Manhattan (KS)':[39.18,-96.57],'Shawnee':[39.02,-94.72],'Lenexa':[38.95,-94.73],
  'Louisville':[38.25,-85.76],'Lexington':[38.04,-84.50],'Bowling Green':[36.99,-86.44],'Owensboro':[37.77,-87.11],
  'New Orleans':[29.95,-90.07],'Baton Rouge':[30.45,-91.15],'Shreveport':[32.53,-93.75],
  'Metairie':[29.98,-90.17],'Lafayette (LA)':[30.22,-92.02],'Lake Charles':[30.23,-93.22],
  'Kenner':[29.99,-90.24],'Bossier City':[32.52,-93.73],
  'Portland (ME)':[43.66,-70.26],
  'Baltimore':[39.29,-76.61],'Frederick':[39.41,-77.41],'Gaithersburg':[39.14,-77.22],
  'Rockville':[39.08,-77.15],'Bowie':[38.94,-76.73],
  'Boston':[42.36,-71.06],'Worcester':[42.26,-71.80],'Springfield (MA)':[42.10,-72.59],
  'Cambridge':[42.37,-71.11],'Lowell':[42.64,-71.32],'Brockton':[42.08,-71.01],
  'New Bedford':[41.64,-70.94],'Quincy':[42.25,-71.00],'Lynn':[42.47,-70.95],
  'Fall River':[41.70,-71.15],'Newton':[42.34,-71.21],'Somerville':[42.39,-71.10],
  'Lawrence (MA)':[42.71,-71.16],'Framingham':[42.28,-71.42],'Haverhill':[42.78,-71.08],
  'Waltham':[42.38,-71.24],'Malden':[42.43,-71.07],'Medford':[42.42,-71.11],
  'Detroit':[42.33,-83.05],'Grand Rapids':[42.96,-85.67],'Warren':[42.49,-83.03],
  'Sterling Heights':[42.58,-83.03],'Ann Arbor':[42.28,-83.74],'Lansing':[42.73,-84.56],
  'Dearborn':[42.32,-83.18],'Livonia':[42.37,-83.35],'Clinton Township':[42.58,-82.92],
  'Troy (MI)':[42.60,-83.15],'Farmington Hills':[42.49,-83.38],'Macomb Township':[42.67,-82.91],
  'Westland':[42.32,-83.40],'Rochester Hills':[42.66,-83.15],'Kalamazoo':[42.29,-85.59],
  'Wyoming (MI)':[42.91,-85.71],'Southfield':[42.47,-83.25],'Flint':[43.01,-83.69],'Waterford':[42.67,-83.40],
  'Minneapolis':[44.98,-93.27],'Saint Paul':[44.95,-93.09],'Rochester (MN)':[44.02,-92.48],
  'Duluth':[46.79,-92.10],'Bloomington (MN)':[44.84,-93.39],'Brooklyn Park':[45.09,-93.37],
  'Plymouth':[45.01,-93.46],'Woodbury':[44.92,-92.96],'Maple Grove':[45.07,-93.46],
  'Saint Cloud':[45.56,-94.16],'Eagan':[44.80,-93.17],'Coon Rapids':[45.12,-93.31],'Burnsville':[44.77,-93.28],
  'Jackson':[32.30,-90.18],'Gulfport':[30.37,-89.09],'Southaven':[34.99,-90.01],
  'Kansas City (MO)':[39.10,-94.58],'Saint Louis':[38.63,-90.20],'Springfield (MO)':[37.21,-93.30],
  'Columbia (MO)':[38.95,-92.33],'Independence':[39.09,-94.42],"Lee's Summit":[38.91,-94.38],
  "O'Fallon":[38.81,-90.70],'St. Joseph':[39.77,-94.85],'St. Charles':[38.78,-90.50],
  'St. Peters':[38.79,-90.63],'Blue Springs':[39.02,-94.28],'Joplin':[37.08,-94.51],
  'Billings':[45.78,-108.50],'Missoula':[46.87,-114.02],'Great Falls':[47.50,-111.30],'Bozeman':[45.68,-111.04],
  'Omaha':[41.26,-95.94],'Lincoln':[40.81,-96.68],'Bellevue':[41.14,-95.91],'Grand Island':[40.92,-98.34],
  'Las Vegas':[36.17,-115.14],'Henderson':[36.04,-114.98],'Reno':[39.53,-119.81],
  'North Las Vegas':[36.20,-115.12],'Sparks':[39.53,-119.75],'Carson City':[39.16,-119.77],
  'Manchester':[42.99,-71.46],'Nashua':[42.77,-71.47],
  'Newark':[40.74,-74.17],'Jersey City':[40.72,-74.04],'Paterson':[40.91,-74.17],
  'Elizabeth':[40.66,-74.21],'Lakewood (NJ)':[40.10,-74.22],'Edison':[40.52,-74.41],
  'Woodbridge':[40.56,-74.28],'Toms River':[39.95,-74.20],'Hamilton (NJ)':[40.23,-74.72],
  'Clifton':[40.86,-74.16],'Trenton':[40.22,-74.76],'Camden':[39.93,-75.12],
  'Passaic':[40.86,-74.13],'Union City':[40.77,-74.03],'East Orange':[40.77,-74.21],
  'Bayonne':[40.67,-74.11],'Vineland':[39.49,-74.99],'New Brunswick':[40.49,-74.45],'Perth Amboy':[40.51,-74.27],
  'Albuquerque':[35.08,-106.65],'Las Cruces':[32.31,-106.78],'Rio Rancho':[35.23,-106.69],'Santa Fe':[35.69,-105.94],
  'New York City':[40.71,-74.01],'Buffalo':[42.89,-78.86],'Rochester (NY)':[43.16,-77.61],
  'Yonkers':[40.93,-73.90],'Syracuse':[43.05,-76.15],'Albany':[42.65,-73.76],
  'New Rochelle':[40.91,-73.78],'Mount Vernon':[40.91,-73.83],'Schenectady':[42.81,-73.94],
  'Utica':[43.10,-75.23],'White Plains':[41.03,-73.76],'Troy (NY)':[42.73,-73.69],
  'Charlotte':[35.23,-80.84],'Raleigh':[35.78,-78.64],'Greensboro':[36.07,-79.79],
  'Durham':[35.99,-78.90],'Winston-Salem':[36.10,-80.24],'Fayetteville (NC)':[35.05,-78.88],
  'Cary':[35.79,-78.78],'Wilmington (NC)':[34.23,-77.95],'High Point':[35.96,-80.00],
  'Concord (NC)':[35.41,-80.58],'Asheville':[35.58,-82.56],'Jacksonville (NC)':[34.75,-77.43],
  'Gastonia':[35.26,-81.19],'Rocky Mount':[35.94,-77.79],'Kannapolis':[35.49,-80.62],
  'Fargo':[46.88,-96.79],'Bismarck':[46.81,-100.78],'Grand Forks':[47.93,-97.03],
  'Columbus (OH)':[39.96,-83.00],'Cleveland':[41.50,-81.69],'Cincinnati':[39.10,-84.51],
  'Toledo':[41.66,-83.56],'Akron':[41.08,-81.52],'Dayton':[39.76,-84.19],
  'Parma':[41.38,-81.73],'Canton':[40.80,-81.37],'Youngstown':[41.10,-80.65],
  'Lorain':[41.45,-82.18],'Hamilton (OH)':[39.40,-84.56],'Springfield (OH)':[39.92,-83.81],
  'Kettering':[39.69,-84.17],'Elyria':[41.37,-82.11],'Lakewood (OH)':[41.48,-81.80],'Dublin (OH)':[40.10,-83.11],
  'Oklahoma City':[35.47,-97.52],'Tulsa':[36.15,-95.99],'Norman':[35.22,-97.44],
  'Broken Arrow':[36.06,-95.79],'Lawton':[34.61,-98.39],'Edmond':[35.65,-97.48],
  'Moore':[35.34,-97.49],'Midwest City':[35.46,-97.40],'Enid':[36.39,-97.88],
  'Portland':[45.52,-122.68],'Salem':[44.94,-123.03],'Eugene':[44.05,-123.09],
  'Gresham':[45.50,-122.43],'Hillsboro':[45.52,-122.99],'Bend':[44.06,-121.31],
  'Beaverton':[45.49,-122.80],'Medford':[42.33,-122.87],'Springfield (OR)':[44.05,-123.02],'Corvallis':[44.56,-123.26],
  'Philadelphia':[39.95,-75.17],'Pittsburgh':[40.44,-80.00],'Allentown':[40.60,-75.49],
  'Erie':[42.13,-80.08],'Reading':[40.34,-75.93],'Scranton':[41.41,-75.66],
  'Bethlehem':[40.63,-75.37],'Lancaster':[40.04,-76.30],'Harrisburg':[40.27,-76.89],
  'Providence':[41.82,-71.42],'Cranston':[41.78,-71.44],'Warwick':[41.70,-71.42],'Pawtucket':[41.88,-71.38],
  'Charleston':[32.78,-79.94],'Columbia (SC)':[34.00,-81.03],'North Charleston':[32.86,-80.00],
  'Mount Pleasant':[32.83,-79.83],'Rock Hill':[34.92,-81.02],'Greenville':[34.85,-82.40],'Summerville':[33.02,-80.18],
  'Sioux Falls':[43.54,-96.73],'Rapid City':[44.08,-103.23],
  'Nashville':[36.17,-86.78],'Memphis':[35.15,-90.05],'Knoxville':[35.96,-83.92],
  'Chattanooga':[35.05,-85.31],'Clarksville':[36.53,-87.36],'Murfreesboro':[35.85,-86.39],
  'Franklin':[35.93,-86.87],'Jackson (TN)':[35.61,-88.81],'Johnson City':[36.32,-82.36],
  'Kingsport':[36.55,-82.56],'Bartlett':[35.20,-89.87],'Hendersonville':[36.30,-86.62],
  'Houston':[29.76,-95.37],'San Antonio':[29.42,-98.49],'Dallas':[32.78,-96.80],
  'Austin':[30.27,-97.74],'Fort Worth':[32.75,-97.33],'El Paso':[31.76,-106.49],
  'Arlington':[32.74,-97.11],'Corpus Christi':[27.80,-97.40],'Plano':[33.02,-96.70],
  'Laredo':[27.51,-99.51],'Lubbock':[33.58,-101.85],'Garland':[32.91,-96.64],
  'Irving':[32.82,-96.95],'Amarillo':[35.22,-101.83],'McKinney':[33.20,-96.64],
  'Frisco':[33.15,-96.82],'Grand Prairie':[32.75,-97.00],'Brownsville':[25.90,-97.50],
  'Killeen':[31.12,-97.73],'Pasadena (TX)':[29.69,-95.21],'McAllen':[26.20,-98.23],
  'Denton':[33.21,-97.13],'Mesquite':[32.77,-96.60],'Waco':[31.55,-97.15],
  'Carrollton':[32.95,-96.89],'Midland':[31.99,-102.08],'Round Rock':[30.51,-97.68],
  'Beaumont':[30.08,-94.13],'Odessa':[31.85,-102.37],'Abilene':[32.45,-99.73],
  'Pearland':[29.56,-95.29],'Richardson':[32.94,-96.73],'Sugar Land':[29.62,-95.64],
  'College Station':[30.63,-96.34],'Tyler':[32.35,-95.30],'Lewisville':[33.05,-96.99],
  'League City':[29.51,-95.10],'Wichita Falls':[33.91,-98.49],'New Braunfels':[29.70,-98.13],
  'Conroe':[30.31,-95.46],'Allen':[33.10,-96.67],'Edinburg':[26.30,-98.16],
  'Mission (TX)':[26.21,-98.33],'Pharr':[26.19,-98.18],'Flower Mound':[33.01,-97.10],
  'Baytown':[29.74,-94.98],'San Angelo':[31.46,-100.44],'Longview':[32.50,-94.74],
  'Mansfield':[32.56,-97.14],'Cedar Park':[30.52,-97.82],'Temple':[31.10,-97.34],
  'Harlingen':[26.19,-97.70],'Rowlett':[32.90,-96.56],'North Richland Hills':[32.85,-97.23],
  'Salt Lake City':[40.76,-111.89],'West Valley City':[40.69,-112.00],'Provo':[40.23,-111.66],
  'West Jordan':[40.60,-111.96],'Orem':[40.30,-111.69],'Sandy':[40.57,-111.89],
  'Ogden':[41.22,-111.97],'St. George':[37.10,-113.58],'South Jordan':[40.56,-111.93],
  'Layton':[41.06,-111.97],'Lehi':[40.39,-111.85],'Taylorsville':[40.66,-111.94],'Millcreek':[40.69,-111.87],
  'Virginia Beach':[36.85,-75.98],'Norfolk':[36.85,-76.29],'Chesapeake':[36.78,-76.29],
  'Arlington (VA)':[38.88,-77.10],'Richmond':[37.54,-77.43],'Newport News':[37.09,-76.47],
  'Alexandria':[38.80,-77.05],'Hampton':[37.03,-76.35],'Roanoke':[37.27,-80.02],
  'Portsmouth':[36.84,-76.30],'Suffolk':[36.73,-76.59],'Lynchburg':[37.41,-79.14],
  'Harrisonburg':[38.44,-78.87],'Leesburg':[39.12,-77.56],
  'Seattle':[47.61,-122.33],'Spokane':[47.66,-117.43],'Tacoma':[47.25,-122.44],
  'Vancouver (WA)':[45.64,-122.66],'Bellevue':[47.61,-122.20],'Kent':[47.38,-122.23],
  'Everett':[47.98,-122.20],'Renton':[47.48,-122.21],'Federal Way':[47.32,-122.31],
  'Spokane Valley':[47.67,-117.24],'Kirkland':[47.68,-122.21],'Bellingham':[48.75,-122.48],
  'Kennewick':[46.21,-119.14],'Yakima':[46.60,-120.51],'Auburn (WA)':[47.31,-122.23],
  'Marysville':[48.05,-122.18],'Pasco':[46.24,-119.10],'Lakewood (WA)':[47.17,-122.52],
  'Redmond':[47.67,-122.12],'Sammamish':[47.62,-122.03],'Shoreline':[47.75,-122.34],
  'Richland':[46.29,-119.28],'Burien':[47.47,-122.35],
  'Milwaukee':[43.04,-87.91],'Madison':[43.07,-89.40],'Green Bay':[44.52,-88.02],
  'Kenosha':[42.59,-87.82],'Racine':[42.73,-87.78],'Appleton':[44.26,-88.42],
  'Waukesha':[43.01,-88.23],'Oshkosh':[44.02,-88.54],'Eau Claire':[44.81,-91.50],
  'Janesville':[42.68,-89.02],'West Allis':[43.02,-88.01],'La Crosse':[43.80,-91.24],
  'Cheyenne':[41.14,-104.82],'Casper':[42.87,-106.31],
  'Washington D.C.':[38.91,-77.04]
};

// ══════════════════════════════════════════════════════
// FIPS → STATE ABBR
// ══════════════════════════════════════════════════════
const FIPS = {
  '01':'AL','02':'AK','04':'AZ','05':'AR','06':'CA','08':'CO','09':'CT','10':'DE',
  '11':'DC','12':'FL','13':'GA','15':'HI','16':'ID','17':'IL','18':'IN','19':'IA',
  '20':'KS','21':'KY','22':'LA','23':'ME','24':'MD','25':'MA','26':'MI','27':'MN',
  '28':'MS','29':'MO','30':'MT','31':'NE','32':'NV','33':'NH','34':'NJ','35':'NM',
  '36':'NY','37':'NC','38':'ND','39':'OH','40':'OK','41':'OR','42':'PA','44':'RI',
  '45':'SC','46':'SD','47':'TN','48':'TX','49':'UT','50':'VT','51':'VA','53':'WA',
  '54':'WV','55':'WI','56':'WY'
};

// ══════════════════════════════════════════════════════
// D3 MAP
// ══════════════════════════════════════════════════════
let mapMode = 'buyer'; // 'buyer' | 'seller' | 'split'
let mapSvg, mapProjection, mapPath;

// Precompute state averages
const stateAvg = {};
CITIES.forEach(c => {
  if (!stateAvg[c.state]) stateAvg[c.state] = {b:[],s:[]};
  stateAvg[c.state].b.push(c.buyer);
  stateAvg[c.state].s.push(c.seller);
});
Object.keys(stateAvg).forEach(st => {
  const d = stateAvg[st];
  stateAvg[st].buyer = d.b.reduce((a,v)=>a+v,0)/d.b.length;
  stateAvg[st].seller = d.s.reduce((a,v)=>a+v,0)/d.s.length;
});

// Color functions
function stateColor(abbr, mode) {
  const d = stateAvg[abbr];
  if (!d) return '#1C2330';
  if (mode === 'buyer') {
    const t = Math.max(0, Math.min(1, (d.buyer - 3) / 6));
    return d3.interpolateBlues(0.15 + t * 0.85);
  } else if (mode === 'seller') {
    const t = Math.max(0, Math.min(1, (d.seller - 3) / 6));
    return d3.interpolateReds(0.15 + t * 0.85);
  } else {
    // split: buyer score drives blue, seller drives red → mix
    const tb = Math.max(0, Math.min(1, (d.buyer - 3) / 6));
    const ts = Math.max(0, Math.min(1, (d.seller - 3) / 6));
    // bivariate: high both = purple, buyer > seller = blue, seller > buyer = red
    const diff = tb - ts;
    if (diff > 0.2) return d3.interpolateBlues(0.2 + tb * 0.75);
    if (diff < -0.2) return d3.interpolateReds(0.2 + ts * 0.75);
    return d3.interpolatePurples(0.2 + ((tb + ts) / 2) * 0.75);
  }
}

function cityColor(c, mode) {
  if (mode === 'buyer') {
    const t = Math.max(0, Math.min(1, (c.buyer - 3) / 6));
    return d3.interpolateBlues(0.35 + t * 0.65);
  } else if (mode === 'seller') {
    const t = Math.max(0, Math.min(1, (c.seller - 3) / 6));
    return d3.interpolateReds(0.35 + t * 0.65);
  } else {
    const tb = Math.max(0, Math.min(1, (c.buyer - 3) / 6));
    const ts = Math.max(0, Math.min(1, (c.seller - 3) / 6));
    const diff = tb - ts;
    if (diff > 0.2) return d3.interpolateBlues(0.4 + tb * 0.6);
    if (diff < -0.2) return d3.interpolateReds(0.4 + ts * 0.6);
    return d3.interpolatePurples(0.4 + ((tb + ts) / 2) * 0.6);
  }
}

function scoreColor2(v) {
  if (v >= 8.5) return '#3FB950';
  if (v >= 7.0) return '#C9A84C';
  if (v >= 5.5) return '#FFA500';
  return '#F85149';
}

async function initMap() {
  const loader = document.getElementById('mapLoader');
  const wrap = document.getElementById('mapWrap');
  const W = wrap.clientWidth || 900;
  const H = 520;

  let us;
  try {
    us = await d3.json('https://cdn.jsdelivr.net/npm/us-atlas@3/states-10m.json');
  } catch(e) {
    loader.innerHTML = '<span style="color:#F85149">⚠ Map failed to load. Check your connection.</span>';
    return;
  }

  loader.style.display = 'none';
  const svgEl = document.getElementById('usMap');
  svgEl.setAttribute('width', W);
  svgEl.setAttribute('height', H);

  mapSvg = d3.select('#usMap');
  mapProjection = d3.geoAlbersUsa().scale(W * 1.28).translate([W / 2, H / 2]);
  mapPath = d3.geoPath().projection(mapProjection);

  const states = topojson.feature(us, us.objects.states);
  const mesh   = topojson.mesh(us, us.objects.states, (a, b) => a !== b);

  // Tax overlay pattern defs
  const defs = mapSvg.append('defs');
  defs.append('pattern')
    .attr('id','taxPattern').attr('patternUnits','userSpaceOnUse')
    .attr('width',8).attr('height',8)
    .append('path')
      .attr('d','M-1,1 l2,-2 M0,8 l8,-8 M7,9 l2,-2')
      .attr('stroke','rgba(255,165,0,0.55)').attr('stroke-width',1.5);

  const gStates = mapSvg.append('g').attr('class','g-states');
  const gTax    = mapSvg.append('g').attr('class','g-tax');
  const gMesh   = mapSvg.append('g').attr('class','g-mesh');
  const gCities = mapSvg.append('g').attr('class','g-cities');
  const tooltip = document.getElementById('mapTooltip');

  // Draw states
  gStates.selectAll('path')
    .data(states.features)
    .join('path')
      .attr('d', mapPath)
      .attr('fill', d => stateColor(FIPS[d.id] || String(d.id).padStart(2,'0'), mapMode))
      .attr('stroke', 'none')
      .style('cursor', 'pointer')
      .on('mouseover', function(event, d) {
        const abbr = FIPS[d.id] || String(d.id).padStart(2,'0');
        const tax = STATE_TAX[abbr];
        const avg = stateAvg[abbr];
        if (!avg || !tax) return;
        const bv = avg.buyer.toFixed(1), sv = avg.seller.toFixed(1);
        tooltip.innerHTML = `
          <div class="tt-city">${tax.name}</div>
          <div class="tt-state">${abbr} — State Average</div>
          <div class="tt-row"><span class="tt-lbl">🔵 Avg Buyer</span><span class="tt-val" style="color:${scoreColor2(avg.buyer)}">${bv}/10</span></div>
          <div class="tt-row"><span class="tt-lbl">🔴 Avg Seller</span><span class="tt-val" style="color:${scoreColor2(avg.seller)}">${sv}/10</span></div>
          <div class="tt-row"><span class="tt-lbl">Sales Tax</span><span class="tt-val" style="color:${tax.tax>0?'#F85149':'#3FB950'}">${tax.tax>0?tax.tax+'%':'✅ None'}</span></div>
          <span class="tt-tax" style="background:${tax.tax>0?'rgba(248,81,73,.15)':tax.status==='expiring'?'rgba(255,165,0,.15)':'rgba(63,185,80,.15)'};color:${tax.tax>0?'#F85149':tax.status==='expiring'?'#FFA500':'#3FB950'}">${tax.note}</span>`;
        tooltip.style.display = 'block';
        document.getElementById('mapInfoText').textContent = `${tax.name} · Buyer ${bv} · Seller ${sv} · ${tax.note}`;
        d3.select(this).attr('stroke','#C9A84C').attr('stroke-width',1.5);
      })
      .on('mousemove', function(event) {
        const [mx, my] = d3.pointer(event, wrap);
        const tx = mx + 15 > W - 230 ? mx - 235 : mx + 15;
        const ty = my + 10 > H - 160 ? my - 145 : my + 10;
        tooltip.style.left = tx + 'px';
        tooltip.style.top  = ty + 'px';
      })
      .on('mouseout', function() {
        tooltip.style.display = 'none';
        d3.select(this).attr('stroke','none');
        document.getElementById('mapInfoText').textContent = 'Hover a state or city for details';
      })
      .on('click', function(event, d) {
        const abbr = FIPS[d.id] || String(d.id).padStart(2,'0');
        const selEl = document.getElementById('stateFilter');
        if (selEl.value === abbr) { selEl.value = 'ALL'; }
        else { selEl.value = abbr; }
        currentState = selEl.value;
        currentPage = 1;
        render();
        document.getElementById('cityExplorer').scrollIntoView({behavior:'smooth'});
      });

  // Tax overlay
  gTax.selectAll('path')
    .data(states.features.filter(d => {
      const abbr = FIPS[d.id] || String(d.id).padStart(2,'0');
      const tax = STATE_TAX[abbr];
      return tax && (tax.tax > 0 || tax.status === 'expiring');
    }))
    .join('path')
      .attr('d', mapPath)
      .attr('fill','url(#taxPattern)')
      .attr('pointer-events','none');

  // State mesh borders
  gMesh.append('path')
    .datum(mesh)
    .attr('d', mapPath)
    .attr('fill','none')
    .attr('stroke','rgba(0,0,0,0.35)')
    .attr('stroke-width', 0.5)
    .attr('pointer-events','none');

  // City circles
  const cityData = CITIES.map(c => {
    const coord = COORDS[c.city];
    if (!coord) return null;
    const proj = mapProjection([coord[1], coord[0]]);
    if (!proj) return null;
    return { ...c, px: proj[0], py: proj[1] };
  }).filter(Boolean);

  const maxPop = d3.max(cityData, d => d.pop);
  const rScale = d3.scaleSqrt().domain([0, maxPop]).range([2, 14]);

  gCities.selectAll('circle')
    .data(cityData.sort((a,b) => b.pop - a.pop))
    .join('circle')
      .attr('cx', d => d.px)
      .attr('cy', d => d.py)
      .attr('r',  d => rScale(d.pop))
      .attr('fill', d => cityColor(d, mapMode))
      .attr('stroke', 'rgba(0,0,0,0.5)')
      .attr('stroke-width', 0.6)
      .attr('opacity', 0.88)
      .style('cursor','pointer')
      .on('mouseover', function(event, d) {
        const [tbcls, tblbl] = (() => {
          const t = d.tax;
          if (t.status==='notax') return ['#3FB950','No Tax'];
          if (t.status==='exempt') return ['#3FB950','Tax-Free'];
          if (t.status==='partial') return ['#FFA500','Partial'];
          if (t.status==='expiring') return ['#FFB300','⚡ Expiring'];
          return ['#F85149', t.tax+'%'];
        })();
        tooltip.innerHTML = `
          <div class="tt-city">${d.city}</div>
          <div class="tt-state">${d.stateName} · Pop ${(d.pop/1000).toFixed(0)}k</div>
          <div class="tt-row"><span class="tt-lbl">🔵 Buyer Score</span><span class="tt-val" style="color:${scoreColor2(d.buyer)}">${d.buyer.toFixed(1)}/10</span></div>
          <div class="tt-row"><span class="tt-lbl">🔴 Seller Score</span><span class="tt-val" style="color:${scoreColor2(d.seller)}">${d.seller.toFixed(1)}/10</span></div>
          <div class="tt-row"><span class="tt-lbl">Coin Shows</span><span class="tt-val">${d.shows}/yr</span></div>
          <span class="tt-tax" style="background:rgba(0,0,0,.3);color:${tbcls}">${tblbl}</span>`;
        tooltip.style.display = 'block';
        document.getElementById('mapInfoText').textContent = `${d.city}, ${d.state} · Buyer ${d.buyer.toFixed(1)} · Seller ${d.seller.toFixed(1)} · ${d.tax.note}`;
        d3.select(this).attr('stroke','#C9A84C').attr('stroke-width',1.5).attr('opacity',1);
      })
      .on('mousemove', function(event) {
        const [mx, my] = d3.pointer(event, wrap);
        const tx = mx + 15 > W - 230 ? mx - 235 : mx + 15;
        const ty = my + 10 > H - 160 ? my - 145 : my + 10;
        tooltip.style.left = tx + 'px';
        tooltip.style.top  = ty + 'px';
      })
      .on('mouseout', function() {
        tooltip.style.display = 'none';
        d3.select(this).attr('stroke','rgba(0,0,0,0.5)').attr('stroke-width',0.6).attr('opacity',0.88);
        document.getElementById('mapInfoText').textContent = 'Hover a state or city for details';
      });

  // ── redraw on mode change ──
  function redraw() {
    gStates.selectAll('path')
      .transition().duration(400)
      .attr('fill', d => stateColor(FIPS[d.id] || String(d.id).padStart(2,'0'), mapMode));
    gCities.selectAll('circle')
      .transition().duration(400)
      .attr('fill', d => cityColor(d, mapMode));
    // legend
    document.getElementById('legBuyer').style.display  = mapMode === 'buyer'  ? '' : 'none';
    document.getElementById('legSeller').style.display = mapMode === 'seller' ? '' : 'none';
    document.getElementById('legSplit').style.display  = mapMode === 'split'  ? '' : 'none';
  }

  document.getElementById('btnBuyer').addEventListener('click', () => {
    mapMode = 'buyer';
    ['btnBuyer','btnSeller','btnSplit'].forEach(id => document.getElementById(id).className = 'mtbtn');
    document.getElementById('btnBuyer').classList.add('buyer-on');
    redraw();
  });
  document.getElementById('btnSeller').addEventListener('click', () => {
    mapMode = 'seller';
    ['btnBuyer','btnSeller','btnSplit'].forEach(id => document.getElementById(id).className = 'mtbtn');
    document.getElementById('btnSeller').classList.add('seller-on');
    redraw();
  });
  document.getElementById('btnSplit').addEventListener('click', () => {
    mapMode = 'split';
    ['btnBuyer','btnSeller','btnSplit'].forEach(id => document.getElementById(id).className = 'mtbtn');
    document.getElementById('btnSplit').classList.add('split-on');
    redraw();
  });
}

// Resize handler
window.addEventListener('resize', () => {
  const wrap = document.getElementById('mapWrap');
  if (!mapSvg || !wrap) return;
  const W = wrap.clientWidth;
  mapSvg.attr('width', W);
  mapProjection.translate([W/2, 520/2]).scale(W * 1.28);
  mapSvg.selectAll('path').attr('d', mapPath);
  mapSvg.selectAll('circle').each(function(d) {
    const p = mapProjection([COORDS[d.city]?.[1], COORDS[d.city]?.[0]]);
    if (p) d3.select(this).attr('cx', p[0]).attr('cy', p[1]);
  });
});

initMap();

// ── Live Prices Loader (prices.json) ─────────────────────────────────────────
(async function loadPrices() {
  try {
    const res = await fetch('prices.json?t=' + Date.now());
    if (!res.ok) return; // file not present yet — silently keep static values
    const data = await res.json();
    const spot = data.spot || {};
    const spreads = data.spreads || [];
    const alerts = data.arbitrage_alerts || [];
    const scrapedAt = data.scraped_at ? new Date(data.scraped_at) : null;

    // Format helpers
    const fmt = (n, d=2) => n != null ? n.toLocaleString('en-US',{minimumFractionDigits:d,maximumFractionDigits:d}) : '—';
    const timeStr = scrapedAt
      ? scrapedAt.toLocaleTimeString('en-US',{hour:'2-digit',minute:'2-digit',timeZoneName:'short'})
      : '—';

    // ── Update ticker bar ──────────────────────────────────────────────────
    const tickerMap = [
      ['tick-gold',      spot.gold,            '$', ''],
      ['tick-silver',    spot.silver,           '$', ''],
      ['tick-platinum',  spot.platinum,         '$', ''],
      ['tick-palladium', spot.palladium,        '$', ''],
      ['tick-copper',    spot.copper_per_lb,    '$', '/lb'],
    ];
    tickerMap.forEach(([id, val, pre, suf]) => {
      const el = document.getElementById(id);
      if (el && val) el.textContent = pre + fmt(val) + suf;
    });
    const tickSrc = document.getElementById('tickerSrc');
    if (tickSrc) tickSrc.textContent = 'Swissquote · ' + timeStr;

    // ── Update sidebar spot card ───────────────────────────────────────────
    const spotCardMap = [
      ['spot-gold',      spot.gold],
      ['spot-silver',    spot.silver],
      ['spot-platinum',  spot.platinum],
      ['spot-palladium', spot.palladium],
      ['spot-copper',    spot.copper_per_lb],
    ];
    spotCardMap.forEach(([id, val]) => {
      const el = document.getElementById(id);
      if (el && val) {
        const isCopper = id === 'spot-copper';
        el.textContent = '$' + fmt(val) + (isCopper ? '/lb' : '');
      }
    });
    const gsrEl = document.getElementById('spot-gsr');
    if (gsrEl && spot.gold_silver_ratio) gsrEl.textContent = spot.gold_silver_ratio.toFixed(2);
    const srcEl = document.getElementById('spotCardSrc');
    if (srcEl) srcEl.textContent = '· Swissquote · ' + timeStr;

    // ── Update hero description with live spot ─────────────────────────────
    if (spot.gold && spot.silver) {
      const heroP = document.querySelector('.hero p');
      if (heroP) {
        heroP.textContent = heroP.textContent
          .replace(/Gold at \$[\d,]+/, 'Gold at $' + fmt(spot.gold, 0))
          .replace(/Silver at \$[\d.]+/, 'Silver at $' + fmt(spot.silver, 2));
      }
    }

    // ── Inject arbitrage alerts ────────────────────────────────────────────
    if (alerts.length) {
      const alertList = document.getElementById('alertList');
      const alertBadge = document.getElementById('alertBadge');
      if (alertList) {
        const colorMap = { spread:'var(--green)', tax_warning:'var(--gold)', opportunity:'var(--red)' };
        alertList.innerHTML = alerts.map(a => {
          const color = colorMap[a.type] || 'var(--txt2)';
          const meta = a.savings_per_oz
            ? (a.metal === 'gold' ? 'Save $' + fmt(a.savings_per_oz, 0) + '/oz' : 'Save $' + fmt(a.savings_per_oz, 2) + '/oz')
            : 'Regulatory';
          return `<div class="alert-item">
            <div class="adot" style="background:${color}"></div>
            <div>
              <div>${a.message}</div>
              <div class="ameta">${meta} · scraped ${timeStr}</div>
            </div>
          </div>`;
        }).join('');
      }
      if (alertBadge) {
        alertBadge.textContent = alerts.length + ' LIVE';
        alertBadge.style.display = 'inline';
      }
    }

    // ── Populate dealer comparison table ──────────────────────────────────
    if (spreads.length) {
      const tbody = document.getElementById('dealerTableBody');
      const card  = document.getElementById('dealerCompCard');
      const badge = document.getElementById('dealerBadge');
      const qa    = document.getElementById('dealerQuality');
      const sat   = document.getElementById('dealerScrapedAt');

      if (tbody) {
        const metalColor = {silver:'var(--silver)', gold:'var(--gold)', platinum:'#e8e8e8', palladium:'#999', copper:'var(--copper)'};
        tbody.innerHTML = spreads.map(s => {
          const dot = `<span class="dot" style="background:${metalColor[s.metal]||'#aaa'};width:7px;height:7px;display:inline-block;border-radius:50%;margin-right:4px;"></span>`;
          const ebayStr = s.ebay_avg_price
            ? `$${fmt(s.ebay_avg_price)} <span style="color:var(--txt2);font-size:.68rem;">(+$${fmt(s.ebay_vs_best,2)})</span>`
            : '—';
          const spreadColor = s.spread_pct > 2 ? 'var(--red)' : s.spread_pct > 1 ? 'var(--gold)' : 'var(--green)';
          return `<tr>
            <td>${dot}${s.product}</td>
            <td style="color:var(--green)">${s.best_dealer}</td>
            <td style="text-align:right;font-weight:700;">$${fmt(s.best_price, s.metal==='silver'||s.metal==='platinum'||s.metal==='palladium' ? 2 : 2)}</td>
            <td style="text-align:right;color:var(--green);">${s.best_premium_pct.toFixed(1)}%</td>
            <td style="color:var(--txt2)">${s.worst_dealer}</td>
            <td style="text-align:right;color:${spreadColor};font-weight:700;">$${fmt(s.spread_dollar,2)}</td>
            <td style="text-align:right;color:${spreadColor};">${s.spread_pct.toFixed(1)}%</td>
            <td style="font-size:.72rem;">${ebayStr}</td>
          </tr>`;
        }).join('');
      }

      if (card) card.style.display = 'block';
      if (badge) badge.textContent = 'LIVE · ' + timeStr;
      if (qa) {
        const allQuality = (data.products||[]).every(p => p.data_quality === 'live') ? 'live' : 'estimated';
        qa.textContent = allQuality;
        qa.style.color = allQuality === 'live' ? 'var(--green)' : 'var(--gold)';
      }
      if (sat && scrapedAt) sat.textContent = scrapedAt.toLocaleString();
    }

    console.log('[MetalScope] prices.json loaded — spot Au:' + spot.gold + ' Ag:' + spot.silver);

  } catch (err) {
    console.warn('[MetalScope] prices.json not loaded:', err.message,
      '— run scraper.py to generate it, or serve via a local HTTP server.');
  }
})();
</script>
</body>
</html>
