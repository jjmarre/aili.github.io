# aili.github.io
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AILI — Competitive Landscape Dashboard</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,400&family=Playfair+Display:wght@500;700;800&display=swap" rel="stylesheet">
<style>
:root{--bg:#F5F3EE;--card:#fff;--card-alt:#FAFAF7;--text:#1a1a1a;--text-muted:#777;--accent:#C2553A;--accent2:#2D6A4F;--accent3:#4A6FA5;--border:#E0DDD6;--border-light:#EDEBE6;--shadow:0 2px 16px rgba(0,0,0,.05);--shadow-lg:0 8px 32px rgba(0,0,0,.08);--radius:16px;--radius-sm:10px}
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);font-size:15px;line-height:1.65}
::selection{background:rgba(194,85,58,.15)}

/* HEADER */
.header{background:linear-gradient(135deg,#2D2926,#423B36);padding:40px 52px 32px;color:#fff;position:relative;overflow:hidden}
.header::before{content:'';position:absolute;top:-40%;right:-10%;width:50%;height:180%;background:radial-gradient(circle,rgba(194,85,58,.12) 0%,transparent 70%);pointer-events:none}
.header h1{font-family:'Playfair Display',serif;font-size:34px;font-weight:800;letter-spacing:-.5px;position:relative;z-index:1}
.header p{font-size:15px;color:rgba(255,255,255,.55);margin-top:5px;position:relative;z-index:1}

/* TABS */
.tab-bar{display:flex;background:var(--card);border-bottom:2px solid var(--border);padding:0 52px;position:sticky;top:0;z-index:100;box-shadow:0 2px 8px rgba(0,0,0,.04);overflow-x:auto}
.tab-btn{padding:15px 22px;font-size:14px;font-weight:500;color:var(--text-muted);border:none;background:none;cursor:pointer;border-bottom:3px solid transparent;margin-bottom:-2px;transition:all .25s;white-space:nowrap;font-family:'DM Sans',sans-serif}
.tab-btn:hover{color:var(--text)}
.tab-btn.active{color:var(--accent);border-bottom-color:var(--accent);font-weight:600}
.tab-content{display:none;padding:36px 52px 60px}
.tab-content.active{display:block;animation:fadeUp .3s ease}
@keyframes fadeUp{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
.section-label{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:2px;color:var(--text-muted);margin-bottom:22px}

/* ===== OVERVIEW ===== */
.overview-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(340px,1fr));gap:20px;margin-top:12px}
.brand-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:0;box-shadow:var(--shadow);transition:transform .2s,box-shadow .2s;overflow:hidden}
.brand-card:hover{transform:translateY(-3px);box-shadow:var(--shadow-lg)}
.brand-card-img-zone{height:140px;background:#F4F2ED;display:flex;align-items:center;justify-content:center;cursor:pointer;position:relative;overflow:hidden;border-bottom:1px solid var(--border-light);transition:background .2s}
.brand-card-img-zone:hover{background:#EBE8E1}
.brand-card-img-zone img{max-width:90%;max-height:130px;object-fit:contain}
.brand-card-img-zone .placeholder{text-align:center;color:var(--text-muted);font-size:12px;pointer-events:none}
.brand-card-img-zone .placeholder svg{display:block;margin:0 auto 6px;opacity:.35}
.brand-card-img-zone input[type="file"]{display:none}
.brand-card-body{padding:20px 22px 22px}
.brand-card .brand-name{font-family:'Playfair Display',serif;font-size:19px;font-weight:700;margin-bottom:4px}
.brand-card .brand-type{font-size:12.5px;color:var(--text-muted);margin-bottom:12px;line-height:1.4}
.brand-card .tag-row{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:14px}
.tag{display:inline-block;padding:4px 11px;border-radius:20px;font-size:11.5px;font-weight:600;border:1px solid}
.tag-direct{background:#FFF0EC;color:#C2553A;border-color:#F0C8BD}
.tag-indirect{background:#E8F5EE;color:#2D6A4F;border-color:#B7DBCB}
.brand-card .meta-row{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.meta-item .label{color:var(--text-muted);font-size:10px;text-transform:uppercase;letter-spacing:1px;font-weight:600}
.meta-item .value{font-weight:600;color:var(--text);margin-top:2px;font-size:13.5px;line-height:1.4}

/* ===== CLAIMS ===== */
.claims-brand-selector{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:28px}
.brand-sel-btn{padding:9px 20px;border-radius:24px;font-size:14px;font-weight:500;cursor:pointer;border:2px solid var(--border);background:var(--card);color:var(--text);transition:all .2s;font-family:'DM Sans',sans-serif}
.brand-sel-btn:hover{border-color:var(--accent);color:var(--accent)}
.brand-sel-btn.active{background:var(--accent);color:#fff;border-color:var(--accent)}
.claims-profile{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);box-shadow:var(--shadow);overflow:hidden}
.claims-profile-head{padding:26px 32px;background:linear-gradient(135deg,#2D2926,#423B36);color:#fff;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
.claims-profile-head h2{font-family:'Playfair Display',serif;font-size:24px;font-weight:700}
.comp-tag{padding:5px 14px;border-radius:20px;font-size:13px;font-weight:600}
.comp-tag-direct{background:rgba(194,85,58,.3);color:#FFB8A4}
.comp-tag-indirect{background:rgba(45,106,79,.3);color:#7ECBA1}
.claims-profile-body{padding:0}
.claims-grid{display:grid;grid-template-columns:1fr 1fr;gap:0}
.claims-field{padding:18px 24px;border-bottom:1px solid var(--border-light);border-right:1px solid var(--border-light)}
.claims-field:nth-child(even):not(.full-width){border-right:none}
.claims-field.full-width{grid-column:1/-1;border-right:none}
.claims-field-label{font-size:10.5px;font-weight:700;text-transform:uppercase;letter-spacing:1.4px;color:var(--accent);margin-bottom:7px}
.claims-field-value{font-size:14px;color:var(--text);line-height:1.6;white-space:pre-line}

/* ===== PRICING ===== */
.price-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:20px}
.price-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow)}
.price-card-head{padding:18px 24px;background:linear-gradient(135deg,#2D2926,#423B36);color:#fff}
.price-card-head h3{font-family:'Playfair Display',serif;font-size:18px;font-weight:700}
.price-card-head span{font-size:12px;opacity:.6;display:block;margin-top:2px}
.price-card-body{padding:20px 24px}
.price-line{display:flex;justify-content:space-between;padding:9px 0;border-bottom:1px solid var(--border-light);font-size:14px}
.price-line:last-child{border-bottom:none}
.price-line .pl-label{color:var(--text-muted)}
.price-line .pl-val{font-weight:600;color:var(--accent)}

/* ===== DISTRIBUTION ===== */
.dist-controls{display:flex;gap:10px;margin-bottom:24px;flex-wrap:wrap;align-items:center}
.dist-controls label{font-size:14px;font-weight:600;color:var(--text-muted);margin-right:4px}
.filter-btn{padding:8px 20px;border-radius:24px;font-size:14px;font-weight:500;cursor:pointer;border:2px solid var(--border);background:var(--card);color:var(--text);transition:all .2s;font-family:'DM Sans',sans-serif}
.filter-btn:hover{border-color:var(--accent);color:var(--accent)}
.filter-btn.active{background:var(--accent);color:#fff;border-color:var(--accent)}
.check-grid-wrap{overflow-x:auto;border-radius:var(--radius);border:1px solid var(--border);box-shadow:var(--shadow);margin-bottom:32px}
.check-grid{width:100%;border-collapse:collapse;font-size:14px;background:var(--card)}
.check-grid th{background:#2D2926;color:#fff;padding:13px 14px;text-align:center;font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.6px;white-space:nowrap}
.check-grid th:first-child{text-align:left;min-width:170px}
.check-grid td{padding:10px 14px;border-bottom:1px solid var(--border-light);text-align:center;font-size:14px}
.check-grid td:first-child{text-align:left;font-weight:500;white-space:nowrap}
.check-grid tr:nth-child(even) td{background:var(--card-alt)}
.check-grid tr:hover td{background:#F0EDE6}
.ck{color:var(--accent2);font-size:18px;font-weight:700}
.ck-no{color:#D4D0CA;font-size:16px}
.dist-detail-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(380px,1fr));gap:20px;margin-top:16px}
.dist-detail-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow)}
.dist-detail-head{padding:16px 20px;background:linear-gradient(135deg,#2D2926,#423B36);color:#fff;display:flex;justify-content:space-between;align-items:center}
.dist-detail-head h3{font-family:'Playfair Display',serif;font-size:16px}
.ch-badge{padding:3px 10px;border-radius:12px;font-size:11px;font-weight:600}
.ch-badge-store{background:rgba(45,106,79,.25);color:#7ECBA1}
.ch-badge-online{background:rgba(74,111,165,.25);color:#8BB4E0}
.dist-detail-body{padding:18px 20px}
.dist-section-title{font-size:12px;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:8px;display:flex;align-items:center;gap:6px}
.dist-section-title.in-store{color:var(--accent2)}
.dist-section-title.online{color:var(--accent3)}
.dist-list{list-style:none;margin-bottom:16px}
.dist-list li{padding:5px 0;font-size:13.5px;display:flex;align-items:flex-start;gap:8px;line-height:1.4}
.dist-list li::before{content:'';width:6px;height:6px;border-radius:50%;flex-shrink:0;margin-top:7px}
.dist-list.in-store li::before{background:var(--accent2)}
.dist-list.online li::before{background:var(--accent3)}
.note-card{background:linear-gradient(135deg,#FFF8F5,#FFF3ED);border:1px solid #F0C8BD;border-radius:var(--radius);padding:20px 24px;margin-top:32px;font-size:14px;color:#8B4A35;line-height:1.6}
.note-card strong{color:var(--accent)}

/* ===== COMMON TRAITS ===== */
.common-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(360px,1fr));gap:20px}
.common-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:24px;box-shadow:var(--shadow)}
.common-card-head{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:12px}
.common-card h3{font-family:'Playfair Display',serif;font-size:17px;font-weight:700}
.common-count{background:var(--accent);color:#fff;padding:4px 12px;border-radius:20px;font-size:12px;font-weight:700;white-space:nowrap}
.common-card p{font-size:13.5px;color:var(--text-muted);line-height:1.5;margin-bottom:10px}
.common-brands{display:flex;flex-wrap:wrap;gap:5px}
.common-brands span{font-size:11px;padding:3px 9px;border-radius:12px;background:#F0EDE6;color:var(--text);font-weight:500}

/* ===== FEATURE MATRIX ===== */
.matrix-wrap{overflow-x:auto;border-radius:var(--radius);border:1px solid var(--border);box-shadow:var(--shadow)}
.matrix{width:100%;border-collapse:collapse;font-size:13px;background:var(--card)}
.matrix th{background:#2D2926;color:#fff;padding:12px 14px;text-align:center;font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;white-space:nowrap;position:sticky;top:0}
.matrix th:first-child{text-align:left;min-width:200px}
.matrix td{padding:10px 14px;border-bottom:1px solid var(--border-light);text-align:center;font-size:13px}
.matrix td:first-child{text-align:left;font-weight:600;font-size:13px;white-space:nowrap}
.matrix tr:nth-child(even) td{background:var(--card-alt)}
.matrix tr:hover td{background:#F0EDE6}
.mx-yes{color:var(--accent2);font-weight:700;font-size:16px}
.mx-no{color:#D4D0CA}

/* ===== SLIDESHOW ===== */
.slideshow-wrap{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);box-shadow:var(--shadow-lg);overflow:hidden}
.slideshow-brand-nav{display:flex;flex-wrap:wrap;gap:6px;padding:18px 24px;background:var(--card-alt);border-bottom:1px solid var(--border)}
.slide-brand-btn{padding:7px 16px;border-radius:20px;font-size:13px;font-weight:500;cursor:pointer;border:2px solid var(--border);background:var(--card);color:var(--text);transition:all .2s;font-family:'DM Sans',sans-serif}
.slide-brand-btn:hover{border-color:var(--accent);color:var(--accent)}
.slide-brand-btn.active{background:var(--accent);color:#fff;border-color:var(--accent)}
.slideshow-stage{position:relative;min-height:420px;display:flex;align-items:center;justify-content:center;background:#F6F4EF;overflow:hidden}
.slideshow-stage img{max-width:85%;max-height:400px;object-fit:contain;transition:opacity .35s ease}
.slide-arrow{position:absolute;top:50%;transform:translateY(-50%);width:44px;height:44px;border-radius:50%;border:none;background:rgba(255,255,255,.92);box-shadow:0 2px 10px rgba(0,0,0,.1);cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:20px;color:var(--text);transition:all .2s;z-index:5}
.slide-arrow:hover{background:var(--accent);color:#fff}
.slide-arrow.left{left:16px}
.slide-arrow.right{right:16px}
.slide-counter{position:absolute;bottom:14px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,.5);color:#fff;padding:4px 14px;border-radius:16px;font-size:12px;font-weight:500}
.slideshow-info{padding:20px 28px;border-top:1px solid var(--border-light);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
.slideshow-info h3{font-family:'Playfair Display',serif;font-size:20px;font-weight:700}
.slideshow-info p{font-size:13px;color:var(--text-muted);margin-top:2px}
.slideshow-info .img-link{font-size:13px;color:var(--accent);text-decoration:none;font-weight:600}
.slideshow-info .img-link:hover{text-decoration:underline}
.slide-upload-area{margin-top:28px;background:var(--card);border:2px dashed var(--border);border-radius:var(--radius);padding:28px;text-align:center;transition:all .2s}
.slide-upload-area:hover,.slide-upload-area.drag-over{border-color:var(--accent);background:#FFF8F5}
.slide-upload-area h4{font-family:'Playfair Display',serif;font-size:17px;margin-bottom:4px}
.slide-upload-area p{font-size:13px;color:var(--text-muted);margin-bottom:14px}
.upload-row{display:flex;gap:12px;justify-content:center;align-items:center;flex-wrap:wrap}
.upload-row select{padding:9px 14px;border-radius:10px;border:2px solid var(--border);font-size:14px;font-family:'DM Sans',sans-serif;background:var(--card);cursor:pointer}
.upload-row select:focus{border-color:var(--accent);outline:none}
.upload-btn{padding:10px 24px;border-radius:24px;font-size:14px;font-weight:600;cursor:pointer;border:2px solid var(--accent);background:var(--accent);color:#fff;font-family:'DM Sans',sans-serif;transition:all .2s}
.upload-btn:hover{background:#A84530;border-color:#A84530}
.slide-upload-area input[type="file"]{display:none}
.user-images-strip{display:flex;gap:12px;flex-wrap:wrap;margin-top:20px}
.user-img-thumb{position:relative;width:100px;height:100px;border-radius:var(--radius-sm);overflow:hidden;border:2px solid var(--border);cursor:pointer;transition:all .2s}
.user-img-thumb:hover{border-color:var(--accent)}
.user-img-thumb img{width:100%;height:100%;object-fit:cover}
.user-img-label{position:absolute;bottom:0;left:0;right:0;background:rgba(0,0,0,.65);color:#fff;font-size:9px;padding:3px 5px;text-align:center;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.user-img-remove{position:absolute;top:2px;right:2px;width:20px;height:20px;border-radius:50%;background:rgba(0,0,0,.6);color:#fff;font-size:12px;border:none;cursor:pointer;display:flex;align-items:center;justify-content:center;opacity:0;transition:opacity .2s}
.user-img-thumb:hover .user-img-remove{opacity:1}

@media(max-width:768px){.header{padding:24px 20px}.header h1{font-size:24px}.tab-bar{padding:0 12px}.tab-btn{padding:12px 14px;font-size:12px}.tab-content{padding:20px 16px 40px}.overview-grid,.price-grid,.dist-detail-grid,.common-grid{grid-template-columns:1fr}.claims-grid{grid-template-columns:1fr}.claims-field{border-right:none!important}}
/* === INSIGHTS SUMMARY TAB === */
.insights-layout{display:flex;gap:0;min-height:600px}
.insights-nav{width:240px;flex-shrink:0;background:var(--card);border-right:1px solid var(--border);border-radius:var(--r) 0 0 var(--r);padding:20px 0;position:sticky;top:60px;height:fit-content;max-height:calc(100vh - 80px);overflow-y:auto;box-shadow:var(--shadow)}
.ins-nav-title{font-family:'Fraunces',serif;font-size:15px;font-weight:700;padding:0 20px 12px;color:var(--text);border-bottom:1px solid var(--border-light);margin-bottom:8px}
.ins-nav-part{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;color:var(--accent);padding:14px 20px 4px;margin-top:4px}
.insights-nav a{display:block;padding:6px 20px;font-size:13px;color:var(--text-muted);text-decoration:none;transition:all .15s;border-left:3px solid transparent}
.insights-nav a:hover{color:var(--accent);background:var(--accent-light);border-left-color:var(--accent)}
.insights-body{flex:1;min-width:0;padding:32px 40px 60px}
.ins-header{margin-bottom:32px}
.ins-header h2{font-family:'Fraunces',serif;font-size:28px;font-weight:700;color:var(--text)}
.ins-header p{font-size:14px;color:var(--text-muted);margin-top:4px}
.ins-part-label{font-family:'Fraunces',serif;font-size:20px;font-weight:700;color:var(--accent);margin:40px 0 12px;padding-top:24px;border-top:2px solid var(--border)}
.ins-intro{font-size:14.5px;color:var(--text-mid);margin-bottom:24px;line-height:1.6}
.ins-disclaimer{font-size:13px;color:var(--text-muted);background:var(--card-alt);padding:12px 16px;border-radius:var(--rs);border-left:3px solid var(--accent);margin-bottom:24px}
.insights-body h3{font-family:'Fraunces',serif;font-size:18px;font-weight:700;color:var(--text);margin:32px 0 10px;padding-top:16px;scroll-margin-top:80px}
.insights-body h4{font-size:15px;font-weight:600;color:var(--text);margin:18px 0 8px}
.insights-body ul,.insights-body ol{padding-left:20px;margin-bottom:14px}
.insights-body li{font-size:14.5px;line-height:1.6;margin-bottom:6px;color:var(--text)}
.insights-body blockquote{border-left:3px solid var(--accent);padding:10px 16px;margin:12px 0;background:var(--accent-light);border-radius:0 var(--rs) var(--rs) 0;font-size:14px;color:var(--text-mid)}
.insights-body p{font-size:14.5px;line-height:1.65;margin-bottom:12px;color:var(--text)}
.ref-sup{font-size:10.5px;color:var(--accent);text-decoration:none;font-weight:700;vertical-align:super;margin:0 1px}
.ref-sup:hover{text-decoration:underline}
.ins-table{width:100%;border-collapse:collapse;font-size:14px;margin:12px 0 20px;background:var(--card);border:1px solid var(--border);border-radius:var(--rs);overflow:hidden}
.ins-table th{background:var(--text);color:#fff;padding:10px 16px;text-align:left;font-size:12px;font-weight:600;text-transform:uppercase;letter-spacing:.5px}
.ins-table td{padding:10px 16px;border-bottom:1px solid var(--border-light)}
.ins-parents-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:16px;margin:16px 0 24px}
.ins-parent-card{background:var(--card);border:1px solid var(--border);border-radius:var(--rs);padding:18px 20px;box-shadow:var(--shadow)}
.ins-parent-card h4{font-family:'Fraunces',serif;font-size:16px;font-weight:700;margin-bottom:6px;color:var(--text)}
.ins-parent-card p{font-size:13.5px;color:var(--text-mid);line-height:1.5;margin:0}
.ins-refs{margin-top:12px}
.ins-ref{padding:6px 0;font-size:13px;display:flex;gap:8px;border-bottom:1px solid var(--border-light)}
.ins-ref-num{font-weight:700;color:var(--accent);min-width:30px}
.ins-ref a{color:var(--accent3);text-decoration:none}
.ins-ref a:hover{text-decoration:underline}
@media(max-width:900px){.insights-nav{display:none}.insights-body{padding:20px 16px 40px}}
</style>
</head>
<body>
<div class="header">
  <h1>AILI Competitive Landscape Analysis</h1>
  <p>Keto Dessert & Cheesecake Market — 9 Competitor Profiles</p>
</div>
<div class="tab-bar">
  <button class="tab-btn active" onclick="switchTab('overview')">Overview</button>
  <button class="tab-btn" onclick="switchTab('claims')">Claims & Positioning</button>
  <button class="tab-btn" onclick="switchTab('pricing')">Pricing</button>
  <button class="tab-btn" onclick="switchTab('distribution')">Distribution</button>
  <button class="tab-btn" onclick="switchTab('common')">Common Traits</button>
  <button class="tab-btn" onclick="switchTab('matrix')">Feature Matrix</button>
  <button class="tab-btn" onclick="switchTab('insights')">Insights Summary</button>
  <button class="tab-btn" onclick="switchTab('images')">Product Images</button>
</div>

<div id="tab-overview" class="tab-content active"><p class="section-label">Brand Profiles — Click image area to add product photo</p><div class="dist-controls" style="margin-bottom:20px"><label>Filter:</label><button class="filter-btn active" onclick="filterOV('all',this)">All Brands</button><button class="filter-btn" onclick="filterOV('direct',this)">Direct Competitors</button><button class="filter-btn" onclick="filterOV('indirect',this)">Indirect Competitors</button></div><div class="overview-grid" id="overviewGrid"></div></div>
<div id="tab-claims" class="tab-content"><p class="section-label">Full Competitive Profile — Select a Brand</p><div class="claims-brand-selector" id="claimsBrandSelector"></div><div id="claimsProfileArea"></div></div>
<div id="tab-pricing" class="tab-content"><p class="section-label">Price Bands by Product Format</p><div class="price-grid" id="priceGrid"></div></div>
<div id="tab-distribution" class="tab-content">
  <p class="section-label">Retailer / Channel Summary — All 9 Brands</p>
  <div class="check-grid-wrap"><table class="check-grid" id="checkGrid"></table></div>
  <p class="section-label" style="margin-top:36px">Detailed Distribution by Company</p>
  <div class="dist-controls"><label>Filter:</label><button class="filter-btn active" onclick="filterDist('all',this)">All Channels</button><button class="filter-btn" onclick="filterDist('in-store',this)">In-Store Only</button><button class="filter-btn" onclick="filterDist('online',this)">Online Only</button></div>
  <div class="dist-detail-grid" id="distDetailGrid"></div>
  <div class="note-card"><strong>&#9888; Note:</strong> The Unsweetened Tooth is a small, artisan DTC-only business with no wholesale or retail partnerships. Cheesecake Factory Low-Licious is a specialty/limited-distribution SKU — not carried in Costco, Walmart, Sam&#8217;s Club, or Target the way the standard Cheesecake Factory frozen cheesecakes are.</div>
</div>
<div id="tab-common" class="tab-content"><p class="section-label">What&#8217;s Common Among the Competitive Set</p><div class="common-grid" id="commonGrid"></div></div>
<div id="tab-matrix" class="tab-content"><p class="section-label">Feature Matrix — Side-by-Side Comparison</p><div class="matrix-wrap"><table class="matrix" id="matrixTable"></table></div></div>
<div id="tab-insights" class="tab-content" style="padding:36px 52px 60px">

<div class="insights-layout">
<nav class="insights-nav" id="insNav">
  <div class="ins-nav-title">Contents</div>
  <div class="ins-nav-part">Part 1 — Facebook Ads</div>
  <a href="#sec-headlines" onclick="jumpSec(event)">1. Headlines & Claims</a>
  <a href="#sec-supporting" onclick="jumpSec(event)">2. Supporting Messaging</a>
  <a href="#sec-flavors" onclick="jumpSec(event)">3. Flavor Naming</a>
  <a href="#sec-emotional" onclick="jumpSec(event)">4. Emotional Positioning</a>
  <a href="#sec-netcarb" onclick="jumpSec(event)">5. Net Carb & Protein</a>
  <a href="#sec-glp1" onclick="jumpSec(event)">6. GLP-1</a>
  <a href="#sec-fiber" onclick="jumpSec(event)">7. Fiber</a>
  <a href="#sec-animal" onclick="jumpSec(event)">8. Animal-Based Products</a>
  <a href="#sec-cup" onclick="jumpSec(event)">9. Cheesecake Cup Format</a>
  <div class="ins-nav-part">Part 2 — Packaging</div>
  <a href="#sec-pkgformat" onclick="jumpSec(event)">1. Packaging Format</a>
  <a href="#sec-crosssection" onclick="jumpSec(event)">2. Cross-Sectional Image</a>
  <a href="#sec-singleserve" onclick="jumpSec(event)">3. Single-Serve Cups</a>
  <a href="#sec-navy" onclick="jumpSec(event)">4. Color Psychology: Navy</a>
  <a href="#sec-fontstrat" onclick="jumpSec(event)">5. Font & Color Strategy</a>
  <a href="#sec-flavpkg" onclick="jumpSec(event)">6. Flavor Naming on Pack</a>
  <a href="#sec-featurepos" onclick="jumpSec(event)">7. Feature Positioning</a>
  <a href="#sec-sweetener" onclick="jumpSec(event)">8. Sweetener Landscape</a>
  <div class="ins-nav-part">Part 3 — Parent Companies</div>
  <a href="#sec-parents" onclick="jumpSec(event)">Parent Company Landscape</a>
  <div class="ins-nav-part">Part 4 — Ad Test Bank</div>
  <a href="#sec-truefalse" onclick="jumpSec(event)">True/False Hooks</a>
  <div class="ins-nav-part">References</div>
  <a href="#sec-refs" onclick="jumpSec(event)">All 30 Sources</a>
</nav>
<div class="insights-body">

<div class="ins-header">
  <h2>AILI Competitive Insights</h2>
  <p>Facebook Ad Messaging & Packaging Shelf Clarity — Draft for Internal Review</p>
</div>

<!-- ==================== PART 1 ==================== -->
<div class="ins-part-label">Part 1 — Facebook Ad Messaging Recommendations</div>
<p class="ins-intro">Based on competitive analysis of 9 brands in the keto dessert and cheesecake market. These are recommendations for pain points, language, and framing to test in Facebook ad creative.</p>

<h3 id="sec-headlines">1. Primary Headlines & Claim Hierarchy</h3>
<p>These are the front-of-pack claims that appear across almost every competitor. They function as the first filter for consumer attention.</p>

<h4>No Added Sugar / Low Sugar</h4>
<ul>
<li>Appeals to diabetics and those focused on glucose management.</li>
<li>This is essentially a <strong>sight word</strong> now. Consumers may not even turn to read the nutrition label without seeing this on the front.</li>
</ul>

<h4>Low Carb</h4>
<ul>
<li>"Low carb" captures all audiences and is less confusing or specific than "net carb."</li>
<li>Anybody who types "weight loss" into Google or TikTok will hear "eat less carbs." Whether the consumer understands the science is irrelevant — it's now something they are conscious of and look out for.</li>
</ul>

<h4>Gluten-Free</h4>
<ul>
<li>For those with celiac or gluten sensitivities, plus health-conscious individuals who avoid gluten.</li>
<li>In messaging, emphasize more that it's a GF kitchen (not just a GF product).</li>
</ul>

<h3 id="sec-supporting">2. Supporting Messaging Angles</h3>

<h4>Health Condition Appeal — Beyond Diabetics</h4>
<ul>
<li>No added sugar / low sugar always appeals to diabetics and weight loss audiences.</li>
<li>According to the CDC, roughly 2 in 5 adults in the US have prediabetes.<a href="https://www.cdc.gov/diabetes/communication-resources/prediabetes-statistics.html" target="_blank" class="ref-sup" title="CDC">[3]</a> Some people hear this and start trying to swap out products with less sugar or no added sugar — appealing to an even larger market.</li>
<li>Worth looking at those who are worried about their blood sugar, hypertension (high blood pressure), and cholesterol — since sugar affects them all and is generally restricted for heart health. <strong>In the messaging, don't just center on diabetics.</strong></li>
</ul>
<blockquote><em>Sample angle: "Are you worried about your health? Has high blood pressure made you avoid sugary foods?"</em></blockquote>
<ul>
<li>Although possibly a stretch: as people get older, they avoid sugar to reduce chance of stroke. Could this be an underrepresented market AILI isn't looking at?</li>
</ul>

<h4>"Good for You" But Doesn't Taste Like It</h4>
<ul>
<li>Obvious point, but still matters — people are no longer willing to compromise on taste.</li>
</ul>
<blockquote><em>Sample angle: "Have you ever had a good-for-you cheesecake? Did it taste good?"</em></blockquote>

<h4>High Protein</h4>
<ul>
<li>Expo West 2025 supports a big jump in consumer focus on protein.<a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2025" target="_blank" class="ref-sup" title="S2G — Expo West 2025">[6]</a><a href="https://www.bain.com/insights/expo-west-2025-winning-brands-ride-on-strongest--consumer-trends/" target="_blank" class="ref-sup" title="Bain — Expo West 2025">[7]</a><a href="https://seuratgroup.com/project/top-10-trends-from-expo-west-2025/" target="_blank" class="ref-sup" title="Seurat — Expo West 2025">[8]</a></li>
<li>Expo West 2026 reinforces the trend: "Another clear theme was the spread of functional benefits into indulgent categories. Candy, chocolate, and frozen desserts with added protein or fiber appeared widely across the show floor."<a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2026" target="_blank" class="ref-sup" title="S2G — Expo West 2026">[9]</a></li>
</ul>

<h4>Reducing Label Fatigue — "We Do the Math for You"</h4>
<ul>
<li>Counting calories, reading labels, and calculating macros is time-consuming and eventually causes people to fall off a diet. It's why apps like Yuka have been so successful — taking advantage of this fatigue.</li>
</ul>
<blockquote><em>Sample angle: "Do you want low-sugar or alternative snacks that do the math for you?"</em></blockquote>
<ul>
<li>With platforms like TikTok and the internet shifting information flow, when people hear something is "good for them," may help them be healthier, and live longer — they jump on it.</li>
</ul>

<h4>"Weight Loss Journey" Language</h4>
<ul>
<li>It's a weight loss <em>journey</em>, not a "path" or anything else. Whether it's a hashtag or an explanation, these products are helping consumers on their "journey." It's vague and encompassing of any journey.</li>
</ul>

<h4>"Creamy" as a Keyword</h4>
<ul>
<li>Protein products or protein powders mixed into foods tend to be "gritty" or clumpy. The opposite = smooth and creamy.</li>
<li>Sugar aftertaste and gritty, crumbly texture of a pastry vs. the creamy, smooth cheesecake cup — this is a meaningful differentiator.</li>
<li>Simple enough word that evokes the same understanding for most people regardless of education level. Linguistically, French "crème" and Spanish "cremoso" are close enough for some translatory understanding.</li>
<li>Expo West also mentioned consumers moving back into real, dairy products — thus = creamy.<a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2026" target="_blank" class="ref-sup" title="S2G — Expo West 2026">[9]</a><a href="https://www.bain.com/insights/expo-west-2025-winning-brands-ride-on-strongest--consumer-trends/" target="_blank" class="ref-sup" title="Bain — Expo West 2025">[7]</a></li>
</ul>

<h4>Use of "Delicious" as a Keyword</h4>
<ul>
<li>Seems obvious, but the prevalence across almost all competitors is worth noting. It's worth using in the messaging.</li>
<li>Studies show a link between using the word "delicious" as a cue that something will have a good taste.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
<li>Since it's a universal word, it may be worth using in messaging to reduce the predisposition that healthy food may be gritty.</li>
<li>Use of "delicious" is similar to the same word in other languages such as "delicioso" and "délicieux." If included in the marketing, it could increase the market share.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
</ul>
<blockquote><em>Sample angle: "Are you looking for delicious products with no added sugar?"</em></blockquote>

<h3 id="sec-flavors">3. Flavor Naming Insights</h3>
<ul>
<li>Non-direct competitors tend to only do strawberry or raspberry cheesecake.</li>
<li>Likely because a New York–style cheesecake is traditionally topped with strawberries or strawberry coulis.</li>
</ul>
<blockquote><em>Messaging idea: "Do you miss healthier New York–style cheesecake?"</em></blockquote>

<h3 id="sec-emotional">4. Emotional Positioning & Indulgence vs. Health Cues</h3>

<h4>Guilt-Free "Snack" vs. "Treat"</h4>
<ul>
<li>Across competitors, the product is framed as a <strong>"snack" rather than a "treat."</strong></li>
<li>Not sacrificing "goals" for taste — continue this line of thought in AILI messaging.</li>
<li>Emphasis on convenience may play into why it's a "snack": a "treat" is something you sit to enjoy (think Kit Kat or Snickers "take a break" commercials), but snacks are on the go.</li>
</ul>

<h4>Performance Meets Permission to Indulge</h4>
<ul>
<li>"Permission to snack" — performance meets permission to indulge.</li>
<li>Using the words "performance" and "permission" especially when it comes to protein.</li>
<li>"Delicious and creamy" consistently in messaging, pointing away from gritty protein flavors.</li>
</ul>

<h4>Common Denominator Across Competitors</h4>
<ul>
<li>For indirect competitors: they want to reach those who are health-conscious. The ones focused on being no added sugar / low sugar lean into "diabetic friendly" too.</li>
<li><em>"Creamy snack" framing keeps it tethered to health without being clinical.</em></li>
</ul>

<h4>Expo West 2026 Context</h4>
<blockquote><em>"As these products expand, indulgent categories still follow a simple rule: taste must come first."<a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2026" target="_blank" class="ref-sup" title="S2G — Expo West 2026">[9]</a></em></blockquote>

<h3 id="sec-netcarb">5. Net Carb, Protein & Clean Ingredients Messaging</h3>
<ul>
<li>All around, clean ingredients with no artificial flavors, preservatives, etc.</li>
<li>With messaging, test whether "clean ingredients" or specifically <strong>"no refined sugar"</strong> increases engagement — this is less clinical than numbers and people understand it better.</li>
<li>10+ g of protein across the set, but anything protein-forward (Legendary, Ratio) boasts 20g+.</li>
<li>No more than 4g of net carbs and no more than 10g of sugar across the competitive set.</li>
</ul>

<h3 id="sec-glp1">6. GLP-1 — The Emerging Halo Audience</h3>
<p>GLP-1 is one of the most important emerging messaging levers in the category, but it has to be handled carefully — the science of how to position to GLP-1 households (vs. GLP-1 users themselves) matters.</p>

<h4>The Adoption vs. Interest Gap</h4>
<ul>
<li>Hershey, via Food Business News: "While only 8%–10% of Americans have used GLP-1 drugs, 30%–35% are interested."<a href="https://www.foodbusinessnews.net/articles/27181-hershey-acknowledges-mild-impact-from-glp-1-drugs" target="_blank" class="ref-sup" title="Food Business News">[5]</a></li>
<li>Affordability and consumers looking for an easier weight loss solution may explain the gap between interest and use.</li>
</ul>

<h4>The GLP-1 Halo Effect — Shaping How Non-Users Eat</h4>
<ul>
<li>An article by CNBC dives into this.<a href="https://www.cnbc.com/2026/03/21/glp-1-diets-restaurants-protein-fiber-weight-loss-drugs.html" target="_blank" class="ref-sup" title="CNBC — GLP-1">[15]</a> Notably, big names like <strong>Nestlé</strong> (also mentioned by Food Navigator) are moving toward GLP-1 friendly products and innovation.<a href="https://www.foodnavigator.com/Article/2026/01/20/glp-1-halo-effect-explained/" target="_blank" class="ref-sup" title="Food Navigator — GLP-1 Halo">[14]</a></li>
<li>2025 Sage Journal study tracking 150,000 GLP-1 households from July 2022 to Sept 2024 (summarized by the Cornell Chronicle).<a href="https://journals.sagepub.com/doi/10.1177/00222437251412834" target="_blank" class="ref-sup" title="Sage Journal — GLP-1 Study">[16]</a><a href="https://news.cornell.edu/stories/2025/12/ozempic-changing-foods-americans-buy" target="_blank" class="ref-sup" title="Cornell Chronicle">[17]</a> Note: "preadoption" refers to before taking GLP-1.</li>
<li>"At the household level, the share of U.S. households reporting at least one GLP-1 user increased from 11.5% in October 2023 to 16.3% in July 2024, corresponding to a population-level incidence rate rising from 5.5% to 8.3%, respectively."<a href="https://journals.sagepub.com/doi/10.1177/00222437251412834" target="_blank" class="ref-sup" title="Sage Journal — GLP-1 Study">[16]</a></li>
<li>"An interesting exception is candy and chocolates, where spending increases by 6.7% relative to preadoption levels, possibly reflecting partial weakening of appetite suppression as users stabilize at lower maintenance doses."<a href="https://journals.sagepub.com/doi/10.1177/00222437251412834" target="_blank" class="ref-sup" title="Sage Journal — GLP-1 Study">[16]</a><a href="https://news.cornell.edu/stories/2025/12/ozempic-changing-foods-americans-buy" target="_blank" class="ref-sup" title="Cornell Chronicle">[17]</a></li>
<li>"The notable exception is again candy and chocolates, where spending increases to 11.4% above preadoption levels after medication discontinuation."<a href="https://journals.sagepub.com/doi/10.1177/00222437251412834" target="_blank" class="ref-sup" title="Sage Journal — GLP-1 Study">[16]</a><a href="https://news.cornell.edu/stories/2025/12/ozempic-changing-foods-americans-buy" target="_blank" class="ref-sup" title="Cornell Chronicle">[17]</a></li>
</ul>
<blockquote><em>In short: GLP-1 users and their households can't seem to give up sweets regardless. Why not present them with a product like AILI cheesecakes they wouldn't have to give up?</em></blockquote>
<ul>
<li>According to data collected by the UK's Institute of Grocery Distribution: 55% of people using GLP-1 agree it has affected the way the rest of their household eats, and 38% of users agree the household is having fewer collective meals than before.<a href="https://www.morningstar.com/news/pr-newswire/20260414ny33220/halo-effect-of-glp-1s-signals-new-consumer-lifestyle-and-health-and-wellness-trends" target="_blank" class="ref-sup" title="Morningstar — GLP-1 Halo">[19]</a></li>
</ul>

<h4>The Credibility Problem — Why "GLP-1 Friendly" vs. "GLP-1 Alternative"</h4>
<ul>
<li>NPR states there is no regulated or medically defined GLP-1 safe product standard — so it's all marketing. But it's risky because there is no medical credibility backing, hence the use of "GLP-1 Friendly" vs. "GLP-1 alternative."<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
<li>A 2024 study (BMCC and Equilibrium Economics journal) found that 69% of U.S. adults lacked insurance coverage for GLP-1 medications, leaving substantial out-of-pocket costs — reinforcing why so many consumers are looking for non-prescription alternatives.<a href="https://bariatricsurgeryco.org/weight-loss/can-i-afford-ozempic-wegovy-mounjaro-or-zepbound/" target="_blank" class="ref-sup" title="BMCC">[4]</a><a href="https://equilibriumecon.wisc.edu/2025/01/09/a-heavy-price-the-economic-and-social-costs-of-glp-1-weight-loss-drugs/" target="_blank" class="ref-sup" title="Equilibrium Economics">[13]</a></li>
</ul>

<h4>Strategic Recommendation</h4>
<ul>
<li>Use <strong>"GLP-1 friendly"</strong> in the marketing messaging, but <strong>lower on the claim hierarchy</strong> so as not to alienate consumers who are concerned about medical credibility.</li>
<li>Expo West 2026 highlighted that GLP-1 is on the rise but companies are avoiding making direct claims that relate to the drug itself.<a href="https://www.foodnavigator-usa.com/Article/2026/03/31/expo-west-2026-food-trends-whats-driving-innovation/" target="_blank" class="ref-sup" title="Food Navigator — Expo West 2026">[10]</a><a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2026" target="_blank" class="ref-sup" title="S2G — Expo West 2026">[9]</a></li>
</ul>

<h3 id="sec-fiber">7. Fiber — The Co-Star, Not the Lead</h3>
<ul>
<li>Based on Expo West 2026 research, fiber isn't being used on its own like protein. It is paired with other nutritional factors, especially protein and GLP-1 friendly / supportive marketing.<a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2026" target="_blank" class="ref-sup" title="S2G — Expo West 2026">[9]</a><a href="https://foodinstitute.com/focus/3-key-takeaways-from-expo-west-2026/" target="_blank" class="ref-sup" title="Food Institute — Expo West 2026">[11]</a><a href="https://nielseniq.com/global/en/insights/analysis/2026/expo-west-2026-trends/" target="_blank" class="ref-sup" title="NIQ — Expo West 2026">[12]</a><a href="https://www.foodnavigator-usa.com/Article/2026/03/31/expo-west-2026-food-trends-whats-driving-innovation/" target="_blank" class="ref-sup" title="Food Navigator — Expo West 2026">[10]</a></li>
<li>NIQ specifically called fiber a <strong>"co-star."</strong><a href="https://nielseniq.com/global/en/insights/analysis/2026/expo-west-2026-trends/" target="_blank" class="ref-sup" title="NIQ — Expo West 2026">[12]</a></li>
<li>A comment by Whitney Herrera in the Food Institute article is interesting: "it's really easy to distract yourself and go with what's new and shiny, but how long-term will that be new and shiny?"<a href="https://foodinstitute.com/focus/3-key-takeaways-from-expo-west-2026/" target="_blank" class="ref-sup" title="Food Institute — Expo West 2026">[11]</a></li>
</ul>

<h4>Hypothesis</h4>
<p>Since protein's popularity is currently being transformed into more, every-day products, is the further inclusion of fiber in the marketing of protein products a way for them to not be trapped in a singular lane? As Herrera mentioned, protein is not necessarily becoming less shiny but taking on a different shine. Maybe companies are hoping to include fiber as a way to catch the eyes of a large consumer base that is becoming jaded with protein.</p>

<h3 id="sec-animal">8. Animal-Based Products — The Return of Real Dairy</h3>
<ul>
<li>Expo West brought up the return of real animal-based products. Consumers want real ingredients like butter, heavy cream, and full-fat dairy, with an explicit trend of consumers preferring products that do not contain seed oils.<a href="https://www.bain.com/insights/expo-west-2025-winning-brands-ride-on-strongest--consumer-trends/" target="_blank" class="ref-sup" title="Bain — Expo West 2025">[7]</a><a href="https://www.bain.com/insights/expo-west-2025-winning-brands-ride-on-strongest--consumer-trends/" target="_blank" class="ref-sup" title="Bain — Expo West 2025">[24]</a></li>
<li>Advertising the real Philadelphia cream cheese in the cheesecake could be another attractive point for those seeking real animal-based products.</li>
</ul>

<h3 id="sec-cup">9. The "Cheesecake Cup" Format — An Underused Differentiator</h3>
<ul>
<li>AILI is calling it a <strong>cheesecake cup</strong> — you have space in your fridge for a cup, not a cake — differentiating itself from places that do slices or cakes.</li>
<li>The top on the cups allows you to take bites when you want — it's a built-in portion control and convenience advantage that competitors selling whole cakes or slices can't match.</li>
<li>This ties directly into the "snack vs. treat" framing: a cup is grab-and-go, fits your fridge, and lets you control your own pacing.</li>
</ul>

<!-- ==================== PART 2 ==================== -->
<div class="ins-part-label">Part 2 — Shelf Clarity & Packaging Recommendations</div>
<p class="ins-intro">Observations and recommendations for the graphic designer revamping AILI's packaging. Organized by packaging format, color and font strategy, and visual hierarchy.</p>
<p class="ins-disclaimer"><strong>Disclaimer:</strong> Part 2 includes/repeats all the above observations. Below, in addition to those observations, are insights that did not seemingly apply to Facebook Ad Messaging.</p>

<h3 id="sec-pkgformat">1. Packaging Format Observations</h3>

<h4>Direct Competitors</h4>
<ul>
<li>Some form of clear opening showing specifically the "top" of the product inside.</li>
<li>Gives the consumer a peek inside because some people eat with their eyes first; also communicates portion size.</li>
<li>3.5 to 7.2 oz cups.</li>
</ul>

<h4>Indirect Competitors</h4>
<ul>
<li>Bright colors to attract consumers. Think Quest and Poppi — the colors are so polarizing and not dull.</li>
<li>However, Legendary's copy-and-paste packaging approach may even create the opposite effect.</li>
</ul>

<h4>Gen Z Packaging Trend</h4>
<blockquote><em>Seurat Group (Expo West 2025): "Brands that embrace ultra-bright, dopamine-inducing packaging — featuring bold fonts, saturated colors, and a distinct badge-value aesthetic — are resonating deeply with Gen Z."<a href="https://seuratgroup.com/project/top-10-trends-from-expo-west-2025/" target="_blank" class="ref-sup" title="Seurat — Expo West 2025">[8]</a></em></blockquote>

<h3 id="sec-crosssection">2. Cross-Sectional Image on Packaging</h3>
<ul>
<li>Social media trends, such as mukbangs and user-generated food content, have changed how people socially engage with food.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
<li>Research shows that having a transparent window and a graphic image similar to Quest have an equally great impact. That means both the cross-sectional image in the marketing and the window in the packaging could have a compounding effect.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
<li>Research illustrates that looking at a cake from a top-down angle actually makes people want it less.<a href="https://www.emerald.com/ejm/article-abstract/56/11/2833/85767/" target="_blank" class="ref-sup" title="Emerald — Proximal Depiction">[22]</a></li>
<li>Publications "Bottom-up and top-down factors influencing consumer responses" and "Visual communication design: a neglected factor" are great reads on consumer habits and how to properly design nutrition labels.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
</ul>

<h3 id="sec-singleserve">3. Single-Serve Cups — Format & Market Demand</h3>
<ul>
<li>A study on cake consumption consumer preferences found that there is a great demand for ready-made, portion-controlled options.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
<li>TikTok trends such as Japanese yogurt cheesecake are indicators that consumers are looking for the healthier "dupe" versions of their favorite desserts.</li>
<li>"The [protein dessert cups] market is expected to expand at a steady CAGR of 8.2% from 2025 to 2033, reaching a forecasted value of USD 3.52 billion by 2033. This growth trajectory is attributed to rising health consciousness, the surge in fitness-oriented lifestyles, and the continuous innovation in product offerings by key industry players."<a href="https://growthmarketreports.com/report/protein-dessert-cups-market" target="_blank" class="ref-sup" title="Protein Dessert Cups Market 2033">[23]</a></li>
</ul>

<h3 id="sec-navy">4. Color Psychology: Navy</h3>
<ul>
<li>The color black is normally associated with luxury, sophistication, authority, and exclusivity, while blue is "the world's favorite color" based on a global survey done by YouGov.<a href="https://yougov.com/articles/12336-why-blue-worlds-favorite-color-1" target="_blank" class="ref-sup" title="YouGov — Blue">[29]</a></li>
<li>Huang and Lu's research suggests that products in blue packaging are perceived as healthier and more likely to be purchased than products in red packaging.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a> The use of navy blue is greatly backed by research and would be an effective package color.<a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank" class="ref-sup" title="Misc. PDFs">[30]</a></li>
<li>Reference Articles: OneThing Design, GPPrint, & LabEX.<a href="https://www.onething.design/post/what-is-the-most-popular-color-and-their-psychological-impact-on-decisions" target="_blank" class="ref-sup" title="OneThing Design">[27]</a><a href="https://gpprint.co.uk/n/news/the-psychology-of-colour-in-print" target="_blank" class="ref-sup" title="GPPrint">[26]</a><a href="https://www.labex.com.au/how-to/how-to-use-colour-psychology.html" target="_blank" class="ref-sup" title="LabEX">[28]</a></li>
</ul>

<h3 id="sec-fontstrat">5. Font & Color Strategy</h3>

<h4>Nostalgia as a Design Lever</h4>
<ul>
<li>Multiple brands try to weave in nostalgia (Wonder Monday, Junior's, Cheesecake Factory, Legendary).</li>
<li>Legendary specifically plays on adult Pop-Tart nostalgia.</li>
<li>Hypothesis: most buyers are older. It's only been 26 years into the 21st century. The first flip phones were popular in the early 90s, the first iPhone was released in 2007. For those 30+, that's a lot of change in a short period. Maybe they lean on nostalgic flavors and looks for that emotional positioning?</li>
<li>General psychological narratives in media in recent years also center on reconnecting with your inner child.</li>
<li>Forbes has done an article on the rise of nostalgia marketing.<a href="https://www.forbes.com/sites/kianbakhtiari/2025/08/31/the-power-and-perils-of-nostalgia-marketing/" target="_blank" class="ref-sup" title="Forbes">[1]</a></li>
</ul>

<h4>Brand Name in White — The Color Science</h4>
<ul>
<li>Across competitors, the brand name is almost always in white.</li>
<li>Additive Theory of Light: black is seen as the absence of color and white is the culmination of all color. White affects all color receptors (red, green, blue cones) simultaneously. It's why people find it harder to see in dark mode, or easier to read white text because the lighter contrast stimulates all receptors.</li>
<li>The Smithsonian has an article on the science of color supporting this.<a href="https://library.si.edu/exhibition/color-in-a-new-light/science" target="_blank" class="ref-sup" title="Smithsonian">[2]</a></li>
<li>White also has the least longitudinal error — if you have bad eyesight, it's easier to read and focus on white than any other color.</li>
</ul>

<h4>Macros & Features in Dark Font on Light Background</h4>
<ul>
<li>On a lighter background (especially a warm color), a dark font has the high contrast that sticks out.</li>
<li>Wonder Monday is a great example: for the strawberry cheesecake, placing the protein in red behind a white background plays on how our receptors pick up light.</li>
</ul>

<h4>"Protein" Color Strategy</h4>
<ul>
<li>"Protein" — even when right below the brand name — is always in a different color. Example: use of yellow for protein or macros (Ratio, Legendary, Wonder Monday).</li>
<li>This plays into two things: (1) your eyes pick up different wavelengths of light for color, keeping the eye engaged; (2) we are in a high-stimulation society. Bland = boring. People want pops of color and care about aesthetics (see Poppi).</li>
<li>Brings attention to the protein count, but since yellow is a lighter color (vs. dark blue), it draws attention without overwhelming. The most palatable wavelengths sit in the middle of the spectrum — yellow and green (Wonder Monday is genius on the science here). With ROYGBIV, red has the longest wavelength and violet the shortest; yellow and green sit in the middle.</li>
</ul>

<h4>Flavor Name Color Differentiation</h4>
<ul>
<li>The name of the flavor or "cheesecake" is in a completely different color from the rest of the packaging (notice Dannon, Wonder Monday, Quest, Legendary).</li>
</ul>

<h4>Brand Name Font Case — Uppercase vs. Lowercase</h4>
<table class="ins-table">
<thead><tr><th>Lowercase</th><th>Uppercase</th><th>Neither</th></tr></thead>
<tbody><tr><td>Ratio, Wonder Monday</td><td>Legendary, Dannon, Hail Merry, Quest</td><td>Unsweetened Tooth, Junior's, Cheesecake Factory</td></tr></tbody>
</table>
<ul>
<li>The brand names on the packaging are notably different.</li>
<li>Notable: 3 of 4 direct competitors fall under "neither" — <em>worth considering what that signals about the cheesecake subcategory specifically.</em></li>
</ul>

<h4>Bold, Large Macro Numbers Front & Center</h4>
<ul>
<li>Numbers are large (e.g. "10g") and the descriptive word ("protein") sits right under rather than to the side or written out.</li>
<li>Possibly designed to grab consumer attention from far away before they even know what they're looking at.</li>
</ul>

<h4>High-Contrast Color Palettes</h4>
<ul>
<li>Rich background colors corresponding to flavor with bold, high-contrast packaging colors (mainly in indirect competitors).</li>
<li>Pattern: darker colors in the back with lighter text, OR vice versa — the key is high contrast.</li>
</ul>

<h4>Realistic Product & Fruit Imagery</h4>
<ul>
<li>Realistic images of the fruit or dessert on the front.</li>
<li>Plays into the indulgence / "not sacrificing taste for health" idea. If there's a pretty cheesecake on the front of a protein bar, it makes you think you can have your protein and cheesecake too (Quest).</li>
<li>For companies that have no clear opening to see the products like Quest and Legendary (that aren't clearly yogurts), they show both the product (e.g. protein bar) and its flavoring (cheesecake).</li>
<li><em>Essentially, competitors have caught on that customers would like to see what they are consuming before purchasing.</em></li>
</ul>

<h3 id="sec-flavpkg">6. Flavor Naming on Packaging</h3>
<ul>
<li>Kept simple — possibly to avoid throwing people off. People are afraid of the unknown and like to play it safe.</li>
<li>Aside from Wonder Monday, most companies don't have a wide variety of flavors.</li>
</ul>

<h3 id="sec-featurepos">7. Net Carb, Protein & Feature Positioning on Pack</h3>
<ul>
<li>Low sugar / no sugar, protein, and net carb macros are normally front and center across the competitive set.</li>
<li>All around, clean ingredients with no artificial flavors, preservatives, etc.</li>
<li>With messaging, see if "clean ingredients" or specifically <strong>"no refined sugar"</strong> increases engagement — less clinical than numbers and easier for consumers to understand.</li>
</ul>

<h3 id="sec-sweetener">8. Sweetener Landscape Across the Competitive Set</h3>
<table class="ins-table">
<thead><tr><th>Sweetener</th><th>Prevalence</th><th>Notes</th></tr></thead>
<tbody>
<tr><td>Erythritol</td><td>3 of 9 (2 indirect)</td><td></td></tr>
<tr><td>Sucralose</td><td>5 of 9 (4 indirect)</td><td>Most common across the set</td></tr>
<tr><td>Stevia</td><td>3 of 9 (2 indirect)</td><td></td></tr>
</tbody>
</table>

<!-- ==================== PART 3 ==================== -->
<div class="ins-part-label">Part 3 — Parent Company Landscape</div>
<p class="ins-intro">Ownership and funding context for each competitor — useful for understanding which brands have deep-pocketed backing vs. which are independent or family-run.</p>

<div id="sec-parents"></div>
<div class="ins-parents-grid">
  <div class="ins-parent-card"><h4>Legendary</h4><p>Privately owned and self-funded by Ron Penna, the previous co-founder of Quest Nutrition.</p></div>
  <div class="ins-parent-card"><h4>Wonder Monday</h4><p>Funded by Snack Futures, which is under Mondelēz International.<a href="https://ir.mondelezinternational.com/news-releases/news-release-details/mondelez-internationals-snackfutures-announces-start-ups/" target="_blank" class="ref-sup" title="Mondelēz SnackFutures">[18]</a></p></div>
  <div class="ins-parent-card"><h4>Cheesecake Factory</h4><p>Publicly traded under CAKE; Cheesecake Factory Incorporated is the parent company. In addition to over 200 Cheesecake Factory locations, the company operates North Italia, Flower Child, and several other Fox Restaurant Concepts brands.</p></div>
  <div class="ins-parent-card"><h4>Junior's</h4><p>Family-owned, 3rd generation Rosen family. It is currently owned by Alan Rosen.</p></div>
  <div class="ins-parent-card"><h4>Dannon</h4><p>Under Danone, based in Paris but Spanish in origin. Brands include Dannon, Oikos, Activia, Silk, and Light + Fit.</p></div>
  <div class="ins-parent-card"><h4>Quest</h4><p>The Simply Good Foods Company.</p></div>
  <div class="ins-parent-card"><h4>:Ratio</h4><p>Previously General Mills, now Lactalis.</p></div>
  <div class="ins-parent-card"><h4>Unsweetened Tooth</h4><p>Owned by private bakery owner Juda Sharpe.</p></div>
  <div class="ins-parent-card"><h4>Hail Merry</h4><p>Independent LLC by Susan O'Brien but backed by several investment firms, including Blue Horizon, HBC Investments, Powerplant Ventures, and GroundForce Capital.</p></div>
</div>

<!-- ==================== PART 4 ==================== -->
<div class="ins-part-label">Part 4 — Facebook Ad Test Bank</div>
<p class="ins-intro">True/false hooks and "Hack This" headlines drawn from the messaging insights in Part 1. These are intended as starting points for Facebook ad testing to map back to a specific pain point or insight in the summary above.</p>

<div id="sec-truefalse"></div>

<h4>Health Conditions & Diabetics</h4>
<ol>
<li><strong>True or False:</strong> You're worried about your health, and high blood pressure has made you avoid food with a lot of sugar.</li>
<li><strong>True or False:</strong> You're worried about your blood sugar, hypertension, or cholesterol so sugar is one of the first things you cut.</li>
<li><strong>True or False:</strong> You're cutting back on sugar as you get older to reduce your chance of stroke.</li>
<li><strong>True or False:</strong> Your doctor has told you that you're prediabetic, and you've started swapping to anything with no added sugar.</li>
</ol>

<h4>Taste & "Good for You"</h4>
<ol start="5">
<li><strong>True or False:</strong> You've had a "good-for-you" cheesecake before — and it actually tasted good.</li>
<li><strong>True or False:</strong> You're looking for delicious products with no added sugar.</li>
<li><strong>True or False:</strong> You miss New York–style cheesecake but want a healthier version.</li>
<li><strong>True or False:</strong> You'd eat more no-sugar desserts if they didn't have a chalky aftertaste.</li>
</ol>

<h4>Texture — Creamy vs. Gritty</h4>
<ol start="9">
<li><strong>True or False:</strong> You've given up on protein desserts because they always end up gritty or clumpy.</li>
<li><strong>True or False:</strong> You'd rather eat something creamy and smooth than crumble through another dry protein bar.</li>
</ol>

<h4>Label Fatigue & Simplicity</h4>
<ol start="11">
<li><strong>True or False:</strong> You're tired of counting calories and reading labels just to figure out if a snack fits your goals.</li>
<li><strong>True or False:</strong> You want low-sugar or alternative snacks that do the math for you.</li>
<li><strong>True or False:</strong> You'd rather see "no refined sugar" on a label than try to decode a list of macros.</li>
</ol>

<h4>Format — Cup vs. Cake</h4>
<ol start="14">
<li><strong>True or False:</strong> You'd rather have a single-serve cheesecake cup that fits in your fridge than a whole cake taking up shelf space.</li>
<li><strong>True or False:</strong> You want to take a few bites of cheesecake and save the rest without committing to a whole slice.</li>
<li><strong>True or False:</strong> Your fridge has more room for a cup than a cake.</li>
</ol>

<h4>GLP-1 Audience</h4>
<ol start="17">
<li><strong>True or False:</strong> You're on a GLP-1 medication and find yourself craving sweets at lower doses or after stopping.</li>
<li><strong>True or False:</strong> You're interested in GLP-1 medications but the cost has kept you from trying them.</li>
<li><strong>True or False:</strong> Someone in your household is on GLP-1, and it's changed how the rest of you eat.</li>
<li><strong>True or False:</strong> You're looking for desserts that fit a GLP-1 friendly lifestyle without giving up the things you love.</li>
</ol>

<h4>Protein & "Journey"</h4>
<ol start="21">
<li><strong>True or False:</strong> You're on a weight loss journey and refuse to give up dessert to get there.</li>
<li><strong>True or False:</strong> You're trying to hit your protein goals every day but you're bored of bars and shakes.</li>
<li><strong>True or False:</strong> You want a snack that earns its place — protein, low sugar, AND tastes like an actual dessert.</li>
</ol>

<!-- ==================== REFERENCES ==================== -->
<h3 id="sec-refs">References</h3>
<div class="ins-refs">
<div class="ins-ref"><span class="ins-ref-num">[1]</span> <a href="https://www.forbes.com/sites/kianbakhtiari/2025/08/31/the-power-and-perils-of-nostalgia-marketing/" target="_blank">Forbes</a></div>
<div class="ins-ref"><span class="ins-ref-num">[2]</span> <a href="https://library.si.edu/exhibition/color-in-a-new-light/science" target="_blank">Smithsonian</a></div>
<div class="ins-ref"><span class="ins-ref-num">[3]</span> <a href="https://www.cdc.gov/diabetes/communication-resources/prediabetes-statistics.html" target="_blank">CDC</a></div>
<div class="ins-ref"><span class="ins-ref-num">[4]</span> <a href="https://bariatricsurgeryco.org/weight-loss/can-i-afford-ozempic-wegovy-mounjaro-or-zepbound/" target="_blank">BMCC</a></div>
<div class="ins-ref"><span class="ins-ref-num">[5]</span> <a href="https://www.foodbusinessnews.net/articles/27181-hershey-acknowledges-mild-impact-from-glp-1-drugs" target="_blank">Food Business News</a></div>
<div class="ins-ref"><span class="ins-ref-num">[6]</span> <a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2025" target="_blank">S2G — Expo West 2025</a></div>
<div class="ins-ref"><span class="ins-ref-num">[7]</span> <a href="https://www.bain.com/insights/expo-west-2025-winning-brands-ride-on-strongest--consumer-trends/" target="_blank">Bain — Expo West 2025</a></div>
<div class="ins-ref"><span class="ins-ref-num">[8]</span> <a href="https://seuratgroup.com/project/top-10-trends-from-expo-west-2025/" target="_blank">Seurat — Expo West 2025</a></div>
<div class="ins-ref"><span class="ins-ref-num">[9]</span> <a href="https://www.s2ginvestments.com/insights/takeaways-expo-west-2026" target="_blank">S2G — Expo West 2026</a></div>
<div class="ins-ref"><span class="ins-ref-num">[10]</span> <a href="https://www.foodnavigator-usa.com/Article/2026/03/31/expo-west-2026-food-trends-whats-driving-innovation/" target="_blank">Food Navigator — Expo West 2026</a></div>
<div class="ins-ref"><span class="ins-ref-num">[11]</span> <a href="https://foodinstitute.com/focus/3-key-takeaways-from-expo-west-2026/" target="_blank">Food Institute — Expo West 2026</a></div>
<div class="ins-ref"><span class="ins-ref-num">[12]</span> <a href="https://nielseniq.com/global/en/insights/analysis/2026/expo-west-2026-trends/" target="_blank">NIQ — Expo West 2026</a></div>
<div class="ins-ref"><span class="ins-ref-num">[13]</span> <a href="https://equilibriumecon.wisc.edu/2025/01/09/a-heavy-price-the-economic-and-social-costs-of-glp-1-weight-loss-drugs/" target="_blank">Equilibrium Economics</a></div>
<div class="ins-ref"><span class="ins-ref-num">[14]</span> <a href="https://www.foodnavigator.com/Article/2026/01/20/glp-1-halo-effect-explained/" target="_blank">Food Navigator — GLP-1 Halo</a></div>
<div class="ins-ref"><span class="ins-ref-num">[15]</span> <a href="https://www.cnbc.com/2026/03/21/glp-1-diets-restaurants-protein-fiber-weight-loss-drugs.html" target="_blank">CNBC — GLP-1</a></div>
<div class="ins-ref"><span class="ins-ref-num">[16]</span> <a href="https://journals.sagepub.com/doi/10.1177/00222437251412834" target="_blank">Sage Journal — GLP-1 Study</a></div>
<div class="ins-ref"><span class="ins-ref-num">[17]</span> <a href="https://news.cornell.edu/stories/2025/12/ozempic-changing-foods-americans-buy" target="_blank">Cornell Chronicle</a></div>
<div class="ins-ref"><span class="ins-ref-num">[18]</span> <a href="https://ir.mondelezinternational.com/news-releases/news-release-details/mondelez-internationals-snackfutures-announces-start-ups/" target="_blank">Mondelēz SnackFutures</a></div>
<div class="ins-ref"><span class="ins-ref-num">[19]</span> <a href="https://www.morningstar.com/news/pr-newswire/20260414ny33220/halo-effect-of-glp-1s-signals-new-consumer-lifestyle-and-health-and-wellness-trends" target="_blank">Morningstar — GLP-1 Halo</a></div>
<div class="ins-ref"><span class="ins-ref-num">[20]</span> <a href="https://www.foodandwine.com/glp-1-medications-driving-changes-in-food-industry-11868730" target="_blank">Food & Wine — GLP-1</a></div>
<div class="ins-ref"><span class="ins-ref-num">[21]</span> <a href="https://www.tandfonline.com/doi/full/10.1080/00218499.2025.2464293" target="_blank">Tandfonline — Designing Delicious</a></div>
<div class="ins-ref"><span class="ins-ref-num">[22]</span> <a href="https://www.emerald.com/ejm/article-abstract/56/11/2833/85767/" target="_blank">Emerald — Proximal Depiction</a></div>
<div class="ins-ref"><span class="ins-ref-num">[23]</span> <a href="https://growthmarketreports.com/report/protein-dessert-cups-market" target="_blank">Protein Dessert Cups Market 2033</a></div>
<div class="ins-ref"><span class="ins-ref-num">[24]</span> <a href="https://www.bain.com/insights/expo-west-2025-winning-brands-ride-on-strongest--consumer-trends/" target="_blank">Bain — Expo West 2025</a></div>
<div class="ins-ref"><span class="ins-ref-num">[25]</span> <a href="https://cba-design.com/united-states/news/blog_categorie/insight/" target="_blank">CBA Design</a></div>
<div class="ins-ref"><span class="ins-ref-num">[26]</span> <a href="https://gpprint.co.uk/n/news/the-psychology-of-colour-in-print" target="_blank">GPPrint</a></div>
<div class="ins-ref"><span class="ins-ref-num">[27]</span> <a href="https://www.onething.design/post/what-is-the-most-popular-color-and-their-psychological-impact-on-decisions" target="_blank">OneThing Design</a></div>
<div class="ins-ref"><span class="ins-ref-num">[28]</span> <a href="https://www.labex.com.au/how-to/how-to-use-colour-psychology.html" target="_blank">LabEX</a></div>
<div class="ins-ref"><span class="ins-ref-num">[29]</span> <a href="https://yougov.com/articles/12336-why-blue-worlds-favorite-color-1" target="_blank">YouGov — Blue</a></div>
<div class="ins-ref"><span class="ins-ref-num">[30]</span> <a href="https://drive.google.com/drive/folders/1H98rty6zd3qhhNNhR7GhOiORdrIyXUdf?usp=sharing" target="_blank">Misc. PDFs</a></div>

</div>

</div><!-- end insights-body -->
</div><!-- end insights-layout -->

</div>

<div id="tab-images" class="tab-content">
  <p class="section-label">Product Image Slideshow — Upload & Assign to Companies</p>
  <div class="slideshow-wrap">
    <div class="slideshow-brand-nav" id="slideBrandNav"></div>
    <div class="slideshow-stage" id="slideStage">
      <button class="slide-arrow left" onclick="slideNav(-1)">&#8249;</button>
      <img id="slideImg" src="" alt="">
      <button class="slide-arrow right" onclick="slideNav(1)">&#8250;</button>
      <div class="slide-counter" id="slideCounter"></div>
    </div>
    <div class="slideshow-info" id="slideInfo"></div>
  </div>
  <div class="slide-upload-area" id="uploadZone">
    <h4>Add Product Images</h4>
    <p>Select a company, then upload images. They&#8217;ll be added to that company&#8217;s slideshow.</p>
    <div class="upload-row">
      <select id="uploadBrandSelect"></select>
      <button class="upload-btn" onclick="document.getElementById('fileInput').click()">Choose Images</button>
    </div>
    <input type="file" id="fileInput" accept="image/*" multiple>
  </div>
  <div class="user-images-strip" id="userImgStrip"></div>
</div>

<script>
const brands=[
{name:"Wonder Monday",type:"Mini Cheesecakes — 3.5 oz single-serve",competitor:"direct",
format:"Single-serve mini cheesecakes, 12/24 packs, Cheesecake Bites",sweetener:"Allulose + Stevia",
colorStrategy:"Bright pastels, vibrant retro scheme",primaryHeadlineShort:"No Added Sugar Cheesecake · Higher Protein",
website:"https://wondermonday.com/",
pricing:[{label:"Individual Mini Cheesecake (DTC)",val:"$6.66"},{label:"Individual Mini Cheesecake (Retail)",val:"$6.79"},{label:"12-Pack Case",val:"$79.99"},{label:"24-Pack Case",val:"$148.00"},{label:"28 Bites Pack",val:"$69.99"}],
inStore:["Target (Classic Plain, core flavors)","Kroger (national Nov. 2025 — Classic Plain, Strawberry Bliss, Key Lime Pie, Double Chocolate)","Fresh Thyme Market (Classic Plain, Strawberry Bliss)","Nugget Markets","Central Market","Giant Food","Dillons (Kroger-family)"],
online:["WonderMonday.com — full lineup incl. specialty/limited; 12-ct cases ($79.99)","Amazon","Delivered Cold (specialty cold-chain)"],
packagingFormat:"3.5 oz single-serve mini cheesecakes in round plastic containers\nMultipack mini cheesecakes (round plastic) in 12 or 24 packs\nSquare cheesecake bites in rectangular plastic containers",
whereSold:"Online + Retail + Mass/Specialty Grocery",
primaryHeadline:"Originally \"Wonder Monday Cheesecake\" was the headline — now repositioned around:\n\n\"Higher Protein\"\n\"No Added Sugar Cheesecake\" (primary message)",
claimHierarchy:"1. No Added Sugar / Low Sugar\n2. High Protein\n3. Keto-Friendly / Low Carb\n4. Gluten-Free",
supportingMessaging:"\"GLP-1 Friendly + High Protein Cheesecake: keto-friendly, diabetic-friendly, high-protein, and gluten-free\"\n\n\"World's first good-for-you cheesecake\"",
fontDominance:"Retro 70s style with lowercase lettering throughout",
flavorNaming:"Key Lime Pie, Classic Plain, Strawberry Bliss, Double Chocolate, Red Velvet, White Chocolate Razz, Salted Caramel, Cr\u00e8me Br\u00fbl\u00e9e, Peanut Butter Chocolate",
emotionalPositioning:"Guilt-free and whimsical — positioned as a \"snack\" rather than a \"treat.\" Emphasizes fun, approachable branding with a health-conscious twist.",
indulgenceVsHealth:"Emphasis on health cues with indulgent coloring. The visual palette suggests indulgence, but the messaging leads with nutritional benefits.",
netCarbProteinPos:"Large font on front of package next to name. Reiterated in bold next to the brand name — 3g Net Carb and 11g Protein are front-and-center.",
colorStrategyFull:"Bright pastels with a vibrant retro color scheme. Realistic images of the fruit or flavor appear on the front, positioned under or adjacent to the protein callout.",
priceBand:"Individual: $6.66 (DTC) / $6.79 (Retail)\n12-Pack: $79.99\n24-Pack: $148\n28 Bites Pack: $69.99\n12 Cake + 28 Bites Pack: $149.99\n48-Pack: $316",
shelfFootprint:"Major chains Kroger and Target only carry three flavors at a time.",
featuresAndBenefits:"2\u20134g net carbs\nGluten-free and grain-free\nClean ingredients with no artificial flavors or preservatives\n10+ g of protein\nSnack-sized portions\nHandmade\nDiabetic-friendly — minimizes blood sugar spikes\nNaturally sweetened with allulose",
competitorType:"Direct Competitor",sweeteners:"Allulose + Stevia",
ingredients:"Strawberry Bliss: Pasteurized Cultured Milk and Cream, Allulose, Eggs, Almond Flour, Milk Protein, Strawberries, Coconut Oil, Cream, Water, Tapioca Flour, Vanilla, Crystallized Lemon (Lemon Juice, Lemon Oil, Citric Acid), Cinnamon, Salt, Contains Less than 2% of: Carob and Guar Gum, Tomato Lycopene Extract (Color), Stevia, Natural Flavors",
featureFlags:{noSugar:1,highProtein:1,keto:1,glutenFree:1,glp1:1,dairyFree:0,paleo:0,nonGMO:0,artisan:0}},

{name:"Junior's",type:"Little Fellas No Sugar Added — 4 oz mini cheesecakes",competitor:"direct",
format:"4 oz singles, 18-pack sets, 8-inch whole cake",sweetener:"Xylitol",
colorStrategy:"Blood orange & white stripes — NYC carnival",primaryHeadlineShort:"No Added Sugar Cheesecake",
website:"https://www.juniorscheesecake.com/",
pricing:[{label:"Individual Mini Cheesecake (DTC)",val:"$6.58"},{label:"Individual Mini Cheesecake (Retail)",val:"$4.29"},{label:"8-inch Whole Cake",val:"$57.95"},{label:"18-Pack Mini Cheesecakes",val:"$78.95"}],
inStore:["Whole Foods Market","ShopRite","Fairway Market","Key Food","Morton Williams Supermarket","Walmart (individual + 4-ct fruit-topped varieties)"],
online:["Amazon (single unit)","Junior's website (juniorscheesecake.com) — ships frozen, 18-ct packs","Instacart (via above stores)","Walmart.com (18-ct Favorites Little Fellas Sampler)"],
packagingFormat:"8-inch whole cheesecake in cardboard + plastic box with clear view opening\n4 oz single-serve mini cheesecakes / \"Little Fellas\" in plastic containers (18-pack)",
whereSold:"Online + Restaurant",
primaryHeadline:"\"No Added Sugar Cheesecake\"",
claimHierarchy:"1. No Added Sugar / Low Sugar\n2. Keto-Friendly / Low Carb\n3. Customizable (add your own toppings)",
supportingMessaging:"\"No sugar added, no carb cheesecake\"",
fontDominance:"Carnival-style / Rhode Island-style packaging with bold, nostalgic typography",
flavorNaming:"Classic Plain, Raspberry Swirl, Chocolate Swirl, Cappuccino",
emotionalPositioning:"\"Same flavor, different sugar.\" Leans heavily on brand heritage — \"Our Original New York Cheesecake, but with no added sugar. Same great taste. Made with Xylitol, an all-natural sweetener.\"",
indulgenceVsHealth:"Positioned as a more sugar-conscious version of the original cheesecake. The health angle is secondary — the brand identity leads with indulgence and heritage.",
netCarbProteinPos:"Minimal front-of-pack advertising. Nutrition details are mainly on the back near ingredients. \"No Sugar\" is the primary front-facing callout.",
colorStrategyFull:"Blood orange and white stripes — reminiscent of NYC carnival aesthetics. Warm, nostalgic palette reinforces heritage positioning.",
priceBand:"Individual: $6.58 (DTC) / $4.29 (Retail)\n8-inch Cake: $57.95\n18-Pack: $78.95",
shelfFootprint:"Virtually none — mainly sold online or in person at specific restaurants.",
featuresAndBenefits:"Sweetened with xylitol\n3g net carbs",
competitorType:"Direct Competitor",sweeteners:"Xylitol",
ingredients:"Cream Cheese (Pasteurized Milk and Cream, Salt, Carob Bean Gum, Cheese Culture), Low Carb Cheesecake Base (Xylitol, Almond Flour, Whey, Protein Concentrate, Psyllium Husk, Salt, Natural Flavor, Organic Lemon Oil), Water, Eggs",
featureFlags:{noSugar:1,highProtein:0,keto:1,glutenFree:0,glp1:0,dairyFree:0,paleo:0,nonGMO:0,artisan:0}},

{name:"Ratio Keto",type:"Protein Strawberry Cheesecake Dairy Snack — 5.3 oz",competitor:"indirect",
format:"5.3 oz single-serve yogurt cups, 4-pack retail box",sweetener:"Sucralose",
colorStrategy:"Clean dark blue with bold yellow protein stats",primaryHeadlineShort:"25g Protein · Dairy Snack · 3g Sugar",
website:"https://ratiofood.com/",
pricing:[{label:"Individual 5.3 oz Yogurt Cup",val:"$1.50\u2013$2.00"},{label:"4-Pack Retail Box",val:"$5.00\u2013$7.00"}],
inStore:["Walmart (single cup and 4-pack)","Target (single cup)","Kroger and Kroger-family stores (Fred Meyer, Smith's, Dillons, Metro Market)","Martin's Food Markets","Save Mart","Coborn's Marketplace","Weis Markets"],
online:["Amazon","RatioFood.com (links to retailer pages)","Instacart (via above stores)"],
packagingFormat:"5.3 oz single-serve yogurt cup with plastic pull-tab lid\n4-pack retail multipack box",
whereSold:"Online + Mass Grocery",
primaryHeadline:"\"25G Protein\" · \"Dairy Snack\" · \"3g Added Sugar\" · \"Flavored with Other Natural Flavor\"",
claimHierarchy:"1. High Protein\n2. Low Sugar (also no added sugar)\n3. Keto-Friendly\n4. Gluten-Free\n5. Low Fat / Low Carb\n6. GLP-1 Friendly",
supportingMessaging:"\"We do the math so you don't have to\"\n\"Pro-taste meets protein\"\n\"Delivering the right ratio of delicious macros\"\n\"Spend less time reading labels and more time living\"\n\"Making it easy to crush your protein goals\"",
fontDominance:"Large protein gram count (25G) emphasized on lid and cup front in yellow. Brand name \":ratio\" in small, modern lowercase font with \"PROTEIN\" highlighted in yellow. Nutrition stats displayed in icon/badge format on the cup.",
flavorNaming:"Strawberry Cheesecake (Protein line)",
emotionalPositioning:"Performance-focused: meeting your goals without compromising taste. Emphasis on convenience and reduced decision fatigue — \"We did the math for you.\" Designed for keto, high-protein, and nutrition-conscious communities.",
indulgenceVsHealth:"Not positioned as a dessert replacement but as a dairy snack — separating it from the \"treat\" category. \"Delicious and creamy\" messaging consistently steers away from gritty protein associations. Indulgence is implied through flavor names, not through visual or textual explanation. Clean, fact-based iconography suggests discipline over indulgence.",
netCarbProteinPos:"25g protein and low sugar (3g) dominate the front of pack. Total carbs (9g) are visible on the side in smaller font. Keto-friendly badge displayed on packaging. Calorie count positioned on the upper left to emphasize that high protein doesn't compromise low carb goals.",
colorStrategyFull:"Clean dark blue cup with color accents per flavor (e.g., pink for strawberry cheesecake). Bold white brand name with \"Protein\" in yellow for contrast. Minimal, functional design with a cartoon/graphic cheesecake image. Lid features large macro stats in yellow badge form.",
priceBand:"5.3 oz Cup: $1.50\u2013$2.00\n4-Pack Retail: $5\u2013$7",
shelfFootprint:"Sits in the Greek yogurt / high-protein yogurt set. Typically 3\u20136 flavors per retailer.",
featuresAndBenefits:"25g protein (Protein line)\n3g total sugar\n9g total carbs\n170 calories\nKeto-Friendly\nGluten-Free\n0g added sugar\nLow fat (3.5g)\nGLP-1 Friendly\nSingle-serve cup\nNo artificial colors (beet juice for color)",
competitorType:"Indirect Competitor",sweeteners:"Sucralose",
ingredients:"Cultured Pasteurized Ultra-Filtered Nonfat Milk, Cultured Pasteurized Milk, Whey Protein Concentrate, Nonfat Milk. Contains 2% or less of: Sunflower Oil, Natural Flavor, Sucralose, Beet Juice Concentrate (for color), Carrageenan.",
featureFlags:{noSugar:1,highProtein:1,keto:1,glutenFree:1,glp1:1,dairyFree:0,paleo:0,nonGMO:0,artisan:0}},

{name:"Hail Merry",type:"Cups, Tarts & Cookie Dough — refrigerated plant-based",competitor:"indirect",
format:"3 oz tarts, 1.5 oz cups (2-pk), cookie dough bites",sweetener:"Maple Syrup",
colorStrategy:"White & blue watercolor — luxury artisan",primaryHeadlineShort:"Crafted with Almond Flour, Coconut Oil & Maple Syrup",
website:"https://hailmerry.com/",
pricing:[{label:"Individual 3 oz Tart",val:"$4.00\u2013$5.00"},{label:"2-Pack Mini Cups (3 oz)",val:"$3.50\u2013$4.50"}],
inStore:["Whole Foods Market (most locations \u2014 widest in-store selection)","Sprouts Farmers Market","Natural Grocers / Vitamin Cottage","Meijer","Wegmans","Some Kroger and Walmart locations (limited, varies by region)"],
online:["HailMerry.com \u2014 full product line, ships with cold packs","Amazon (refrigerated/cold shipping)","Shop Gourmet and other specialty online retailers"],
packagingFormat:"3 oz single-serve mini cake tart in square packaging\n1.5 oz single-serve mini cake cups in 2-pack rectangular packaging\n8 cookie dough bites in plastic zipper bag",
whereSold:"Online + Retail + Mass/Specialty Grocery",
primaryHeadline:"\"Crafted with almond flour, coconut oil, and maple syrup\" (positioned at the top of packaging)",
claimHierarchy:"1. No Added Sugar / Clean \"Plant\" Ingredients\n2. Luxury / Indulgence\n3. Grain and Seed Oil Free\n4. Paleo-Friendly / Low Carb\n5. Not Baked\n6. Gluten-Free",
supportingMessaging:"\"Luxuriously delicious indulgent sweet snacks with side benefits (not side-effects)\"",
fontDominance:"Calligraphy-style font, reminiscent of lettering found in seaside towns. Evokes craft and artisanal care.",
flavorNaming:"Key Lime Pie, Meyer Lemon, Sweet Potato Pie, Chocolate Almond Butter, Chocolate Peanut Butter, Dark Chocolate, Dark Chocolate Espresso, Cookies and Cream",
emotionalPositioning:"Healthy and unbaked. Positioned as a \"snack\" rather than a \"treat.\" \"Bite-sized treats you can feel good about.\" Grain-free emphasis reinforces clean-eating identity.",
indulgenceVsHealth:"Emphasis on health cues — not indulgent-forward. White coloring suggests luxury rather than indulgence, yet indulgent language appears in the messaging. A careful balance between premium positioning and wellness credentials.",
netCarbProteinPos:"Medium font (not overpowering) on front of package under the cake image. Reiterated in bold next to the ingredients list.",
colorStrategyFull:"White and blue watercolor palette (not pastels). Vivid images of the cake product. Gray labels for health association accreditations. Overall aesthetic is premium and clean.",
priceBand:"Single Tart (3 oz): $4\u2013$5\n2-Pack Cups (3 oz): $3.50\u2013$4.50",
shelfFootprint:"Refrigerated specialty snack sections. Typically 2\u20134 flavors per retailer or store.",
featuresAndBenefits:"5.5\u20137g sugar\nPaleo-friendly\nDairy-free\n11g plant protein (tarts)\nGluten-free",
competitorType:"Indirect Competitor",sweeteners:"Maple Syrup",
ingredients:"Blanched almonds, organic maple syrup, cocoa processed with alkali, organic virgin coconut oil, sea salt",
featureFlags:{noSugar:0,highProtein:0,keto:0,glutenFree:1,glp1:0,dairyFree:1,paleo:1,nonGMO:0,artisan:0}},

{name:"Dannon Light + Fit",type:"Cheesecake-Style Yogurt Cups & Remix",competitor:"indirect",
format:"5.3 oz yogurt cups, 4.5 oz Remix cups with toppings",sweetener:"Fructose + Sucralose",
colorStrategy:"Bold teal/blue & white — mass-market grocery",primaryHeadlineShort:"80 Calories · 12g Protein · Fat Free",
website:"https://www.lightandfit.com/",
pricing:[{label:"Individual 5.3 oz Yogurt Cup",val:"$1.00\u2013$1.50"},{label:"4-Pack Yogurt Cups",val:"$4.00\u2013$5.50"},{label:"Remix 4-Pack (with toppings)",val:"$5.99\u2013$6.99"}],
inStore:["Walmart","Target","Kroger and Kroger-family stores (Smith's, Fred Meyer, Dillons, etc.)","Safeway / Albertsons family (Safeway, Vons, Pavilions, Randalls, Tom Thumb)","Martin's Food Markets","Save Mart","Weis Markets","Most major conventional grocery chains (widely distributed)"],
online:["Amazon","Walmart.com","Instacart (via all above stores)"],
packagingFormat:"5.3 oz single-serve yogurt cup\n4.5 oz \"Remix\" single-serve yogurt cup with mix-in toppings",
whereSold:"Mass Grocery (national distribution)",
primaryHeadline:"\"80 Calories\" \u00b7 \"12g Protein\" \u00b7 \"Fat Free\" \u00b7 \"Strawberry Cheesecake\"",
claimHierarchy:"1. Low Calorie (80 cal)\n2. High Protein (12g)\n3. Fat Free / 0g Fat\n4. Gluten-Free\n5. No Added Fat\n6. Yogurt + Type 2 Diabetes Risk Reduction (FDA-qualified claim)",
supportingMessaging:"\"Just grab your spoon and enjoy\"\n\"A mindful snack\"\n\"Enjoy every delicious bite with 80 calories and 12g of protein\"\n\"Fits right into an active routine\"\n\"Live your life uninterrupted \u2014 enjoy on the go\"",
fontDominance:"Bold, large calorie count (80 cal) and protein (12g) front-and-center on lid and cup. Brand name \"Light + Fit\" in an established consumer-facing font. Flavor name is prominent. \"Fat Free Greek\" descriptor is clearly labeled. Nutrition claim badges stack on the lid and front label.",
flavorNaming:"Strawberry Cheesecake (Greek, primary cheesecake SKU)\nStrawberry Cheesecake REMIX (with graham cookies, caramel pearls & dark chocolate mix-ins)",
emotionalPositioning:"Everyday, accessible \"permission to snack\" \u2014 guilt-free and calorically friendly. Positioned as a mainstream healthy habit, not a dietary lifestyle brand. Appeal is broad (women 25\u201350, health-aware mainstream consumers). \"Do you\" messaging \u2014 individual empowerment without intensity.",
indulgenceVsHealth:"Balanced: \"mindful snack\" framing keeps it tethered to health without being clinical. Flavor names (Strawberry Cheesecake, Key Lime) provide dessert permission, but the identity is firmly health: low-cal, fat-free, protein-rich. Contrast with AILI: indulgence-by-flavor-name vs. indulgence-by-format (actual cheesecake).",
netCarbProteinPos:"Large font on front of package next to name. Reiterated in bold on lid: 80 cal, 12g Protein front-and-center.",
colorStrategyFull:"Bold teal/blue and white brand palette (Dannon corporate colors). Bright, vivid fruit photography on the label. Clean white cup body with colorful lid per flavor. Familiar, mass-market grocery aesthetic \u2014 shelf impact through brand recognition.",
priceBand:"Single Cup: ~$1.00\u2013$1.50\n4-Pack: ~$4.00\u2013$5.50\nRemix 4-Pack: ~$5.99\u2013$6.99",
shelfFootprint:"Dominant national mass-grocery presence \u2014 Walmart, Target, Kroger, HEB, Albertsons, Safeway, Tom Thumb, Randalls, Meijer, Publix, and virtually all grocery chains. Yogurt/dairy aisle with premium placement due to Dannon (Danone) scale and retailer relationships.",
featuresAndBenefits:"80 calories per 5.3 oz serving\n12g protein (Greek line)\n0g fat\n5\u20138g sugar per serving\nGluten-free\nNo artificial colors (beet/carrot juice for color)\nProbiotics (L. Bulgaricus & S. Thermophilus)",
competitorType:"Indirect Competitor",sweeteners:"Fructose + Sucralose",
ingredients:"Cultured Pasteurized Non Fat Milk, Water, Strawberry Puree, Fructose, Less than 1%: Natural & Artificial Flavors, Black Carrot Juice (for Color), Modified Food Starch, Acesulfame Potassium, Sucralose, Citric Acid, Potassium Sorbate, Yogurt Cultures",
featureFlags:{noSugar:0,highProtein:1,keto:0,glutenFree:1,glp1:0,dairyFree:0,paleo:0,nonGMO:0,artisan:0}},

{name:"Quest",type:"White Chocolate Raspberry Protein Bar — 2.12 oz",competitor:"indirect",
format:"2.12 oz protein bar singles, 4-packs, 12-packs",sweetener:"Erythritol + Stevia + Sucralose",
colorStrategy:"Vibrant colors per flavor, rich dessert photography",primaryHeadlineShort:"White Chocolate Raspberry · 20g Protein",
website:"https://www.questnutrition.com/",
pricing:[{label:"Individual 2.12 oz Protein Bar",val:"$2.50\u2013$3.50"},{label:"12-Count Box",val:"$24\u2013$30"},{label:"36-Count Box",val:"$65\u2013$72"}],
inStore:["Target (single + 4-ct)","Walmart (single + 4-ct)","Kroger and family stores (Fred Meyer, Smith's, etc.) \u2014 4-ct and 12-ct","GNC (single + multi-packs)","Vitamin Shoppe","Weis Markets","CVS","Walgreens","Macey's","Most major grocery and specialty fitness retailers"],
online:["Amazon (singles, 4-packs, 12-packs, variety packs)","QuestNutrition.com","GNC.com","Walmart.com / Target.com"],
packagingFormat:"2.12 oz single-serve protein bar\nProtein bar boxes (4-ct, 12-ct, 36-ct)",
whereSold:"Online + Mass Grocery + Specialty Fitness Retailers",
primaryHeadline:"\"White Chocolate Raspberry\" \u00b7 20g Protein",
claimHierarchy:"1. High Protein\n2. Keto-Friendly / Low Carb\n3. Low Sugar\n4. Rich in Fiber\n5. Not Baked\n6. Gluten-Free",
supportingMessaging:"\"Hack your snack\" / \"Snack like a genius\" / \"It's basically cheating\" / \"Cheat clean\"\n\"The protein bar that tastes like a dessert without the sugar\"",
fontDominance:"Bold, large protein gram count (20g) front-and-center on the wrapper. Flavor name is prominent. Brand name is consistent across all SKUs.",
flavorNaming:"White Chocolate Raspberry\nStrawberry Cheesecake (no longer sold)",
emotionalPositioning:"Performance meets permission to indulge \u2014 fueling goals while satisfying cravings. \"Genius hacker\" identity: you're outsmarting bad nutrition, not depriving yourself.",
indulgenceVsHealth:"Strong health/protein emphasis; indulgence is conveyed through food photography and dessert-inspired flavor names. \"Guilt-free\" framing \u2014 the bar is positioned as cheating on junk food.",
netCarbProteinPos:"20g protein and 4\u20135g net carbs prominently displayed on front of wrapper. Calorie count and sugar (1\u20132g) also highlighted.",
colorStrategyFull:"Bright, vibrant background colors unique to each flavor. Rich food photography of the dessert each flavor mimics. Bold black/white brand name for contrast. Playful illustrated icons per flavor.",
priceBand:"Individual: ~$2.50\u2013$3.50\n12-ct box: ~$24\u2013$30\n36-ct box: ~$65\u2013$72",
shelfFootprint:"Dominant shelf presence in the protein/health bar aisle.",
featuresAndBenefits:"20g protein\n4g net carbs\n1g sugar\nRich in fiber\nKeto-Friendly",
competitorType:"Indirect Competitor",sweeteners:"Erythritol + Stevia + Sucralose",
ingredients:"Protein Blend (Milk Protein Isolate, Whey Protein Isolate), Polydextrose (Prebiotic Fiber), Almonds, Water, Erythritol, Palm Kernel Oil, Glycerin, Raspberries, Sodium Caseinate. Contains less than 2%: Natural Flavors, Salt, Lecithin, Stevia, Sucralose",
featureFlags:{noSugar:1,highProtein:1,keto:1,glutenFree:1,glp1:0,dairyFree:0,paleo:0,nonGMO:0,artisan:0}},

{name:"Legendary",type:"Protein Pastries — Pop-Tart style, 2.2 oz",competitor:"indirect",
format:"2.2 oz single-serve protein pastry, 4-packs, 10-packs",sweetener:"Erythritol + Stevia + Sucralose",
colorStrategy:"Bright playful colors per flavor, 3D pastry imagery",primaryHeadlineShort:"Protein Pastry · 20g Protein / 4g Net Carb",
website:"https://www.eatlegendary.com/",
pricing:[{label:"Individual Protein Pastry (4-Pack Box)",val:"$8\u2013$10"},{label:"8-Pack Online",val:"$22\u2013$27"},{label:"10-Pack",val:"$32.49"}],
inStore:["Target \u2014 4-ct boxes (Strawberry and core flavors)","Walmart \u2014 multiple flavors","Kroger and family stores \u2014 10-ct packs","GNC \u2014 specialty/fitness formats, incl. Protein Donuts","Vitamin Shoppe \u2014 full pastry line + donuts"],
online:["EatLegendary.com \u2014 full lineup, subscription available; 12-packs from $38.99","Amazon \u2014 8-packs (~$29.99), most flavors","Walmart.com / Target.com / Kroger.com"],
packagingFormat:"2.2 oz single-serve protein pastry in 4-pack and 10-pack boxes\nProtein pastry packs (4-ct, 8-ct)",
whereSold:"Online + Mass Grocery + Specialty Fitness Retailers",
primaryHeadline:"\"Protein Pastry\"\n20g Protein / 4g Net Carb",
claimHierarchy:"1. High Protein\n2. Low Carb\n3. Low Sugar\n4. Gluten-Free\n5. GLP-1 and Keto-Friendly",
supportingMessaging:"\"Waaay better than a protein bar\"",
fontDominance:"Bold, high-contrast colors with metallic typography and a 3D font style. Rich background colors correspond to each flavor.",
flavorNaming:"Brown Sugar Cinnamon, Strawberry, Chocolate Cake, Blueberry, Hot Fudge Sundae, S'mores, Cherry Crumble",
emotionalPositioning:"\"Guilt-free performance\" with strong nostalgia tied to the similarity to Pop-Tarts. Messaging repeatedly grants \"permission to cheat while staying on track,\" emphasizing convenience and alluding to cheat days.",
indulgenceVsHealth:"Heavy visual indulgence \u2014 icing and jelly visibly pouring out of the pastry. Contrasted sharply with strict, clinical macro numbers.",
netCarbProteinPos:"Bold, large protein gram count (20g) and net carb (4g) are prominent on the front. Brand logo and flavor name are clearly visible.",
colorStrategyFull:"Bright, playful colors per flavor (blue for blueberry, pink for strawberry). 3D image of the pastry. Clean white band for nutrition stats. Block lettering font. A \"bite\" taken out of the pastry reveals the filling.",
priceBand:"4-Pack Retail: ~$8\u2013$10\n8-Pack Online: ~$22\u2013$27\n10-Pack: $32.49\n10-Pack GNC: $34.99",
shelfFootprint:"Health aisle, normally near protein bars and snacks or in the specialty nutrition section. Typically 3\u20136 flavors per store.",
featuresAndBenefits:"20g protein\n1g sugar\n4g net carbs\nKeto-friendly\nGluten-conscious\nDiabetic-friendly\nHelps with glucose management\n170\u2013180 calories\nIndividually wrapped\nCan be eaten cold or microwaved for 10 seconds",
competitorType:"Indirect Competitor",sweeteners:"Erythritol + Stevia + Sucralose",
ingredients:"Protein Blend (Micellar Casein, Calcium Caseinate, Whey Protein Isolate), Erythritol, High Oleic Sunflower/Safflower Oil, Collagen Peptides, Polydextrose, Glycerin, Palm Kernel Oil, Water, Sunflower Lecithin, Natural Flavors",
featureFlags:{noSugar:1,highProtein:1,keto:1,glutenFree:1,glp1:1,dairyFree:0,paleo:0,nonGMO:0,artisan:0}},

{name:"The Unsweetened Tooth",type:"Mini Cheesecakes (7.3 oz) & Whole Cakes",competitor:"direct",
format:"7.3 oz mini cups (4-pack), 6-inch & 8-inch whole cakes",sweetener:"Allulose",
colorStrategy:"Light blue, white, dark purple — artisan bakery",primaryHeadlineShort:"Mother's Keto Cheesecake · 6 Net Carbs · No Sugar Added",
website:"https://theunsweetenedtooth.com/",
pricing:[{label:"Mini Cheesecake 4-Pack (7.3 oz each)",val:"$48.00"},{label:"6-inch Whole Cheesecake",val:"$59.00"},{label:"8-inch Whole Cheesecake",val:"$129.00"}],
inStore:["No retail store distribution","Local pickup available in Seattle, WA area only"],
online:["TheUnsweetenedTooth.com \u2014 ships frozen via 2-day air in insulated containers","No Amazon / Walmart / other marketplace presence confirmed"],
packagingFormat:"7.3 oz single-serve mini cups in a 4-count pack\n8-inch whole cake",
whereSold:"Online Only (theunsweetenedtooth.com)",
primaryHeadline:"\"Mother's Keto Cheesecake\"\n6 net carbs and \"no sugar added\" displayed directly below the brand name",
claimHierarchy:"1. No Sugar Added\n2. Keto-Friendly\n3. Diabetic-Friendly\n4. No Sugar Spikes\n5. Gluten-Free\n6. Non-GMO\n7. Clean Ingredients\n8. Artisan / Baked to Order",
supportingMessaging:"\"Ultra-creamy, perfectly portioned, and truly unforgettable. No added sugar and 10 grams of protein.\"\n\"Dense, silky, undeniably decadent\"",
fontDominance:"Minimal, functional font on website and packaging. Artisan bakery aesthetic with a swirling, handwritten-style font.",
flavorNaming:"Original (Plain)\nFruit curds available as pairings (Blackberry, Strawberry, Sour Cherry, Peach) sold separately\nFlourless Chocolate Cake",
emotionalPositioning:"Heavy emphasis on artisanal quality, luxury texture, and a \"gourmet experience.\" Focuses on delivering the same indulgent taste without guilt or pain. Projects a personal, \"small neighborhood bakery\" image.",
indulgenceVsHealth:"Leans on comfort through the \"Mother's Keto\" name. Health cues are still emphasized \u2014 net carbs, no sugar added, \"perfect\" portioning \u2014 targeting diabetics, keto followers, and health-conscious dessert lovers.",
netCarbProteinPos:"Net carb count (6g) appears under \"Mother's Keto\" inside a purple heart graphic.",
colorStrategyFull:"Light blue, white, and dark purple palette. Elegant and understated \u2014 not overtly colorful or performance-driven. Artisan bakery aesthetic with swirling font reinforces the craft identity.",
priceBand:"6-inch Cheesecake: $59\n8-inch Cheesecake: $129\nMini 4-Pack: $48",
shelfFootprint:"No retail presence \u2014 zero shelf footprint since the brand is online-only. Small-batch, baked to order.",
featuresAndBenefits:"No sugar added\nSweetened with allulose\nKeto-friendly\nDiabetic-friendly\nGluten-free\nNon-GMO\nClean ingredients\nArtisan baked to order\nWest Coast cream cheese\nAlmond-pecan crust\nShips frozen nationwide",
competitorType:"Direct Competitor",sweeteners:"Allulose",
ingredients:"Cream Cheese (pasteurized milk and cream, sea salt, cultures), Sour Cream (cultured cream), Allulose, Heavy Cream, Eggs, Almond Flour, Pecan Flour, Water, Lemon Juice, Butter (pasteurized sweet cream, natural flavor)",
featureFlags:{noSugar:1,highProtein:0,keto:1,glutenFree:1,glp1:0,dairyFree:0,paleo:0,nonGMO:1,artisan:1}},

{name:"Cheesecake Factory",type:"Low-Licious — 6-inch, 24 oz whole cheesecake",competitor:"direct",
format:"24 oz (6-inch) whole cake in window box",sweetener:"Erythritol + Isomalt + Sucralose",
colorStrategy:"Signature brand stripes, elegant restaurant photography",primaryHeadlineShort:"Too Good To Be True · Low-Licious Cheesecake",
website:"https://www.thecheesecakefactory.com/",
pricing:[{label:"6-inch Whole Cheesecake (Retail/Grocery)",val:"$19.99\u2013$25.99"},{label:"Restaurant Slice",val:"$16.95"}],
inStore:["Safeway (and Albertsons-family: Vons, Pavilions, Randalls, Tom Thumb)","Grocery Outlet","Instacart-confirmed stores vary by region","\u26a0 NOT carried in Costco, Walmart, Sam's Club, or Target (Low-Licious only)"],
online:["Instacart (via above stores for delivery)","Not confirmed on Amazon or Walmart.com for this SKU"],
packagingFormat:"24 oz (6-inch) whole cake in cardboard window box",
whereSold:"Online + Restaurant + Mass Grocery (limited distribution)",
primaryHeadline:"\"Too Good To Be True\"\n\"Low-Licious Cheesecake\"",
claimHierarchy:"1. Low Carb\n2. No Sugar Added\n3. Gluten-Free",
supportingMessaging:"\"Low Carb, No Sugar Added, and Gluten-Free \u2014 Too Good to Be True\"",
fontDominance:"Traditional Cheesecake Factory logo dominates. \"Low-Licious\" appears in smaller font, understated in white without stylization or curvature compared to the logo. Uses the cream/orange color of the cheesecake from the box cutout.",
flavorNaming:"Plain",
emotionalPositioning:"The most prominent element is the Cheesecake Factory brand itself. Evokes a nostalgic feeling through box shape and coloring \u2014 feels classic and not overly stimulating. Positioned as \"your favorite indulgence, made permissible.\"",
indulgenceVsHealth:"Leans firmly on indulgence, since \"cheesecake\" inherently signals indulgence. Health and low-sugar attributes are the modification, not the identity. Contrast with health-first competitors: Cheesecake Factory starts with the food, then removes the sugar.",
netCarbProteinPos:"Appears on packaging in small, hard-to-see lettering. Focus is on \"no added sugar\" and \"fewer carbs\" without specific numbers dominating the front of pack.",
colorStrategyFull:"Signature Cheesecake Factory brand palette with stripes. Elegant, restaurant-quality photography of a cheesecake slice (similar to how it's served in the restaurant). Deep bright pink accents draw the eye to the box.",
priceBand:"$19.99\u2013$25.99 (retail)\n$16.95/slice (restaurant)",
shelfFootprint:"Frozen dessert aisle in grocery stores. Also served in Cheesecake Factory restaurants.",
featuresAndBenefits:"5g net carbs per serving\n3g sugar",
competitorType:"Direct Competitor",sweeteners:"Erythritol + Isomalt + Sucralose",
ingredients:"Cream Cheese (Pasteurized Milk and Cream, Cheese Culture, Salt, Stabilizers), Neufch\u00e2tel Cheese, Sweetener Blend (Polydextrose, Soluble Maize Fibers, Chicory Root Fiber, Erythritol, Isomalt, Sucralose)",
featureFlags:{noSugar:1,highProtein:0,keto:1,glutenFree:1,glp1:0,dairyFree:0,paleo:0,nonGMO:0,artisan:0}}
];

// ===== COMMON TRAITS DATA =====
const commonTraits=[
{trait:"No Added Sugar / Low Sugar",desc:"The single most common claim across the set \u2014 nearly every competitor positions around reduced or zero sugar as a primary selling point.",
brands:["Wonder Monday","Junior's","Ratio Keto","Quest","Legendary","The Unsweetened Tooth","Cheesecake Factory"]},
{trait:"Keto-Friendly / Low Carb",desc:"Keto positioning is the second most prevalent claim, reflecting the market's core consumer: carb-conscious dieters and keto followers.",
brands:["Wonder Monday","Junior's","Ratio Keto","Quest","Legendary","The Unsweetened Tooth","Cheesecake Factory"]},
{trait:"Gluten-Free",desc:"Gluten-free is essentially table stakes in this category \u2014 it functions more as a checkbox than a differentiator.",
brands:["Wonder Monday","Ratio Keto","Hail Merry","Dannon Light + Fit","Quest","Legendary","The Unsweetened Tooth","Cheesecake Factory"]},
{trait:"High Protein (10g+)",desc:"High protein positioning is increasingly common, especially among indirect competitors in the snack/bar/yogurt space.",
brands:["Wonder Monday","Ratio Keto","Dannon Light + Fit","Quest","Legendary"]},
{trait:"GLP-1 Friendly Messaging",desc:"An emerging claim that reflects the growing GLP-1 medication market. Only a few brands have adopted this language so far.",
brands:["Wonder Monday","Ratio Keto","Legendary"]},
{trait:"Guilt-Free / Permission Messaging",desc:"Most competitors use some form of \"guilt-free\" or \"permission to indulge\" framing \u2014 signaling that the product lets you enjoy dessert without compromise.",
brands:["Wonder Monday","Junior's","Quest","Legendary","Dannon Light + Fit","Cheesecake Factory"]},
{trait:"Clean / Natural Ingredients",desc:"Brands positioning around ingredient transparency and \"clean label\" values, avoiding artificial additives.",
brands:["Wonder Monday","Hail Merry","The Unsweetened Tooth"]},
{trait:"DTC / Online-First Distribution",desc:"Several competitors rely heavily or exclusively on direct-to-consumer online sales, often with frozen cold-chain shipping.",
brands:["Junior's","The Unsweetened Tooth","Wonder Monday"]},
{trait:"Mass Retail Distribution (Target, Walmart, Kroger)",desc:"The largest competitive advantage in this space. Brands with mass retail presence have significantly wider consumer reach.",
brands:["Wonder Monday","Ratio Keto","Dannon Light + Fit","Quest","Legendary"]}
];

// ===== FEATURE MATRIX DATA =====
const matrixFeatures=["No Added Sugar","High Protein (10g+)","Keto-Friendly","Gluten-Free","GLP-1 Friendly","Dairy-Free","Paleo-Friendly","Non-GMO","Artisan / Small Batch"];
const matrixKeys=["noSugar","highProtein","keto","glutenFree","glp1","dairyFree","paleo","nonGMO","artisan"];

// ===== PERSISTENT STORAGE HELPERS =====
function resizeImage(dataUrl, maxW, maxH){
  return new Promise(resolve=>{
    const img=new Image();
    img.onload=()=>{
      let w=img.width,h=img.height;
      if(w>maxW||h>maxH){const r=Math.min(maxW/w,maxH/h);w=Math.round(w*r);h=Math.round(h*r);}
      const c=document.createElement('canvas');c.width=w;c.height=h;
      c.getContext('2d').drawImage(img,0,0,w,h);
      resolve(c.toDataURL('image/jpeg',0.45));
    };
    img.src=dataUrl;
  });
}
function storageReady(){return typeof window.storage!=='undefined'&&window.storage&&typeof window.storage.set==='function';}
async function waitForStorage(maxWait){
  const start=Date.now();
  while(!storageReady()&&(Date.now()-start)<(maxWait||5000)){
    await new Promise(r=>setTimeout(r,150));
  }
  return storageReady();
}
function showSaveStatus(msg,ok){
  let el=document.getElementById('saveToast');
  if(!el){el=document.createElement('div');el.id='saveToast';el.style.cssText='position:fixed;bottom:20px;right:20px;padding:10px 20px;border-radius:10px;font-size:13px;font-weight:600;font-family:DM Sans,sans-serif;z-index:9999;transition:opacity .3s;pointer-events:none;';document.body.appendChild(el);}
  el.style.background=ok?'#2D6A4F':'#C2553A';el.style.color='#fff';el.textContent=msg;el.style.opacity='1';
  clearTimeout(el._t);el._t=setTimeout(()=>{el.style.opacity='0';},2500);
}
async function storageSave(key,val){
  for(let attempt=0;attempt<3;attempt++){
    try{
      const r=await window.storage.set(key,val);
      if(r)return true;
    }catch(e){}
    await new Promise(r=>setTimeout(r,300));
  }
  return false;
}
async function storageLoad(key){
  try{
    const r=await window.storage.get(key);
    if(r&&r.value)return r.value;
  }catch(e){}
  return null;
}
async function saveOverviewImages(){
  if(!await waitForStorage(2000)){showSaveStatus('Storage not available',false);return;}
  const keys=Object.keys(overviewImages);
  let ok=true;
  for(const name of keys){
    const k='aili-ov-'+name.replace(/[^a-zA-Z0-9]/g,'_');
    const saved=await storageSave(k,overviewImages[name]);
    if(!saved)ok=false;
  }
  // Save index of which brands have images
  await storageSave('aili-ov-index',JSON.stringify(keys));
  showSaveStatus(ok?'Image saved!':'Partial save — some images may not persist',ok);
}
async function saveUserSlideImages(){
  if(!await waitForStorage(2000)){return;}
  // Save each slide individually
  const index=[];
  for(let i=0;i<userImages.length;i++){
    const s=userImages[i];
    const k='aili-slide-'+i;
    const saved=await storageSave(k,JSON.stringify({src:s.src,alt:s.alt,brand:s.brand}));
    if(saved)index.push(i);
  }
  await storageSave('aili-slide-count',String(userImages.length));
  showSaveStatus('Slideshow saved!',true);
}
async function loadSavedData(){
  if(!await waitForStorage(5000)){return;}
  // Load overview images
  try{
    const idxStr=await storageLoad('aili-ov-index');
    if(idxStr){
      const names=JSON.parse(idxStr);
      for(const name of names){
        const k='aili-ov-'+name.replace(/[^a-zA-Z0-9]/g,'_');
        const imgData=await storageLoad(k);
        if(imgData)overviewImages[name]=imgData;
      }
    }
  }catch(e){}
  // Load slideshow images
  try{
    const countStr=await storageLoad('aili-slide-count');
    if(countStr){
      const count=parseInt(countStr);
      for(let i=0;i<count;i++){
        const data=await storageLoad('aili-slide-'+i);
        if(data){
          const s=JSON.parse(data);
          const slide={src:s.src,alt:s.alt,brand:s.brand};
          if(!allSlides[s.brand])allSlides[s.brand]=[];
          allSlides[s.brand].push(slide);
          userImages.push(slide);
        }
      }
    }
  }catch(e){}
}

// ===== OVERVIEW IMAGES =====
const overviewImages = {};

// ===== RENDER: OVERVIEW =====
let ovFilter='all';
function filterOV(mode,btn){
  document.querySelectorAll('#tab-overview .filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  ovFilter=mode;renderOverview();
}
function renderOverview(){
  const filtered=brands.map((b,i)=>({b,i})).filter(({b})=>ovFilter==='all'||b.competitor===ovFilter);
  document.getElementById('overviewGrid').innerHTML=filtered.map(({b,i})=>{
    const imgHtml = overviewImages[b.name]
      ? `<img src="${overviewImages[b.name]}" alt="${b.name}">`
      : `<div class="placeholder"><svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="m21 15-5-5L5 21"/></svg><span>Click to add image</span></div>`;
    return `<div class="brand-card">
      <div class="brand-card-img-zone" onclick="document.getElementById('ovImg${i}').click()">
        ${imgHtml}
        <input type="file" id="ovImg${i}" accept="image/*" onchange="handleOverviewImg(${i},event)" style="display:none">
      </div>
      <div class="brand-card-body">
        <div class="brand-name">${b.name}</div>
        <div class="brand-type">${b.type}</div>
        <div class="tag-row"><span class="tag ${b.competitor==='direct'?'tag-direct':'tag-indirect'}">${b.competitor==='direct'?'Direct Competitor':'Indirect Competitor'}</span></div>
        <div class="meta-row">
          <div class="meta-item"><div class="label">Primary Headline</div><div class="value" style="font-size:12px;line-height:1.35">${b.primaryHeadlineShort}</div></div>
          <div class="meta-item"><div class="label">Sweetener</div><div class="value">${b.sweetener}</div></div>
          <div class="meta-item"><div class="label">Format</div><div class="value" style="font-size:12px">${b.format}</div></div>
          <div class="meta-item"><div class="label">Color Strategy</div><div class="value" style="font-size:12px">${b.colorStrategy}</div></div>
        </div>
      </div>
    </div>`}).join('');
}
async function handleOverviewImg(idx,e){
  const f=e.target.files[0]; if(!f)return;
  const r=new FileReader();
  r.onload=async ev=>{
    const resized=await resizeImage(ev.target.result,400,300);
    overviewImages[brands[idx].name]=resized;
    renderOverview();
    saveOverviewImages();
  };
  r.readAsDataURL(f);
}

// ===== RENDER: CLAIMS =====
function renderClaimsBrandSelector(){
  document.getElementById('claimsBrandSelector').innerHTML=brands.map((b,i)=>`<button class="brand-sel-btn ${i===0?'active':''}" onclick="selectClaimsBrand(${i},this)">${b.name}</button>`).join('');
}
function selectClaimsBrand(idx,btn){
  document.querySelectorAll('.brand-sel-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');renderClaimsProfile(idx);
}
function nl2br(s){return s?s.replace(/\n/g,'<br>'):'<span style="color:var(--text-muted)">N/A</span>';}
function renderClaimsProfile(idx){
  const b=brands[idx];
  const fields=[
    {label:"Packaging Format",value:b.packagingFormat},
    {label:"Where Sold \u2014 Online/Retail Locations",value:b.whereSold},
    {label:"Primary Headline (on the package)",value:b.primaryHeadline,full:1},
    {label:"Claim Hierarchy",value:b.claimHierarchy},
    {label:"Supporting Messaging",value:b.supportingMessaging},
    {label:"Font Dominance",value:b.fontDominance,full:1},
    {label:"Flavor Naming",value:b.flavorNaming,full:1},
    {label:"Emotional Positioning",value:b.emotionalPositioning,full:1},
    {label:"Indulgence vs. Health Cues",value:b.indulgenceVsHealth,full:1},
    {label:"Net Carb / Protein Positioning",value:b.netCarbProteinPos,full:1},
    {label:"Color Strategy",value:b.colorStrategyFull,full:1},
    {label:"Price Band",value:b.priceBand},
    {label:"Shelf Footprint",value:b.shelfFootprint},
    {label:"Features & Benefits",value:b.featuresAndBenefits,full:1},
    {label:"Direct vs. Indirect Competitor",value:b.competitorType},
    {label:"Sweetened With",value:b.sweeteners},
    {label:"Ingredients",value:b.ingredients,full:1}
  ];
  document.getElementById('claimsProfileArea').innerHTML=`<div class="claims-profile" style="animation:fadeUp .3s ease"><div class="claims-profile-head"><div><h2>${b.name}</h2><span style="font-size:14px;opacity:.7">${b.type}</span></div><span class="comp-tag ${b.competitor==='direct'?'comp-tag-direct':'comp-tag-indirect'}">${b.competitorType}</span></div><div class="claims-profile-body"><div class="claims-grid">${fields.map(f=>`<div class="claims-field ${f.full?'full-width':''}"><div class="claims-field-label">${f.label}</div><div class="claims-field-value">${nl2br(f.value)}</div></div>`).join('')}</div></div></div>`;
}

// ===== RENDER: PRICING =====
function renderPricing(){
  document.getElementById('priceGrid').innerHTML=brands.map(b=>`<div class="price-card"><div class="price-card-head"><h3>${b.name}</h3><span>${b.format}</span></div><div class="price-card-body">${b.pricing.map(p=>`<div class="price-line"><span class="pl-label">${p.label}</span><span class="pl-val">${p.val}</span></div>`).join('')}</div></div>`).join('');
}

// ===== RENDER: DISTRIBUTION =====
function buildCheckGrid(){
  const allR=new Set();
  brands.forEach(b=>{
    b.inStore.forEach(s=>{const c=s.split('(')[0].split('\u2014')[0].split('\u2013')[0].replace(/[\u26a0]/g,'').trim();if(c&&c!=='No retail store distribution')allR.add(c);});
    b.online.forEach(s=>{const c=s.split('(')[0].split('\u2014')[0].split('\u2013')[0].replace(/[\u26a0]/g,'').replace('Not confirmed on ','').trim();if(c&&!c.startsWith('No ')&&!c.startsWith('Not '))allR.add(c);});
  });
  const ret=[...allR].sort();
  let h='<thead><tr><th>Retailer / Channel</th>';
  brands.forEach(b=>{h+='<th>'+(b.name.length>14?b.name.substring(0,13)+'\u2026':b.name)+'</th>';});
  h+='</tr></thead><tbody>';
  ret.forEach(r=>{
    h+='<tr><td>'+r+'</td>';
    brands.forEach(b=>{
      const has=b.inStore.concat(b.online).some(s=>{const c=s.split('(')[0].split('\u2014')[0].split('\u2013')[0].replace(/[\u26a0]/g,'').replace('Not confirmed on ','').trim();return c===r;});
      h+=has?'<td><span class="ck">\u2713</span></td>':'<td><span class="ck-no">\u2014</span></td>';
    });h+='</tr>';
  });h+='</tbody>';
  document.getElementById('checkGrid').innerHTML=h;
}
function renderDistDetail(f){
  document.getElementById('distDetailGrid').innerHTML=brands.map(b=>{
    const sI=f==='all'||f==='in-store',sO=f==='all'||f==='online';let bd='';
    if(sI)bd+=`<div class="dist-section-title in-store"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg> In-Store</div><ul class="dist-list in-store">${b.inStore.map(s=>`<li>${s}</li>`).join('')}</ul>`;
    if(sO)bd+=`<div class="dist-section-title online"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg> Online</div><ul class="dist-list online">${b.online.map(s=>`<li>${s}</li>`).join('')}</ul>`;
    return `<div class="dist-detail-card"><div class="dist-detail-head"><h3>${b.name}</h3><div style="display:flex;gap:6px">${b.inStore.some(s=>!s.includes('No retail'))?'<span class="ch-badge ch-badge-store">In-Store</span>':''}<span class="ch-badge ch-badge-online">Online</span></div></div><div class="dist-detail-body">${bd}</div></div>`;
  }).join('');
}

// ===== RENDER: COMMON TRAITS =====
function renderCommon(){
  document.getElementById('commonGrid').innerHTML=commonTraits.map(t=>`<div class="common-card"><div class="common-card-head"><h3>${t.trait}</h3><span class="common-count">${t.brands.length} of 9</span></div><p>${t.desc}</p><div class="common-brands">${t.brands.map(b=>`<span>${b}</span>`).join('')}</div></div>`).join('');
}

// ===== RENDER: FEATURE MATRIX =====
function renderMatrix(){
  let h='<thead><tr><th>Feature</th>';
  brands.forEach(b=>{h+='<th>'+(b.name.length>14?b.name.substring(0,13)+'\u2026':b.name)+'</th>';});
  h+='</tr></thead><tbody>';
  matrixFeatures.forEach((feat,fi)=>{
    h+='<tr><td>'+feat+'</td>';
    brands.forEach(b=>{
      const v=b.featureFlags[matrixKeys[fi]];
      h+=v?'<td><span class="mx-yes">\u2713</span></td>':'<td><span class="mx-no">\u2014</span></td>';
    });h+='</tr>';
  });
  // Add sweetener row
  h+='<tr><td style="font-weight:600">Sweetener</td>';
  brands.forEach(b=>{h+='<td style="font-size:11px">'+b.sweeteners+'</td>';});
  h+='</tr>';
  h+='</tbody>';
  document.getElementById('matrixTable').innerHTML=h;
}

// ===== SLIDESHOW =====
let allSlides={},currentBrandFilter='all',currentSlide=0,userImages=[];
function initSlideshow(){
  brands.forEach(b=>{if(!allSlides[b.name])allSlides[b.name]=[];});
  const nav=document.getElementById('slideBrandNav');
  nav.innerHTML=`<button class="slide-brand-btn active" onclick="filterSlides('all',this)">All</button>`+brands.map(b=>`<button class="slide-brand-btn" onclick="filterSlides('${b.name}',this)">${b.name}</button>`).join('');
  const sel=document.getElementById('uploadBrandSelect');
  sel.innerHTML=brands.map(b=>`<option value="${b.name}">${b.name}</option>`).join('');
  showSlide(0);
}
function getFilteredSlides(){
  if(currentBrandFilter==='all'){
    let arr=[];
    for(const k in allSlides) arr=arr.concat(allSlides[k]);
    return arr;
  }
  return allSlides[currentBrandFilter]||[];
}
function filterSlides(brand,btn){
  document.querySelectorAll('.slide-brand-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  currentBrandFilter=brand;currentSlide=0;showSlide(0);
}
function showSlide(idx){
  const slides=getFilteredSlides();
  if(!slides.length){
    document.getElementById('slideImg').style.display='none';
    document.getElementById('slideCounter').textContent='No images';
    document.getElementById('slideInfo').innerHTML='<p style="color:var(--text-muted)">No images yet for this selection. Upload images below and assign them to a company.</p>';
    return;
  }
  currentSlide=((idx%slides.length)+slides.length)%slides.length;
  const s=slides[currentSlide],img=document.getElementById('slideImg');
  img.src=s.src;img.alt=s.alt;img.style.display='';
  const stage=document.getElementById('slideStage');
  const ed=stage.querySelector('div[style*="text-align:center"]');if(ed)ed.remove();
  img.onerror=function(){this.style.display='none';};
  document.getElementById('slideCounter').textContent=(currentSlide+1)+' / '+slides.length;
  document.getElementById('slideInfo').innerHTML=`<div><h3>${s.brand}</h3><p>${s.alt}</p></div>`;
}
function slideNav(dir){showSlide(currentSlide+dir);}
function setupUploadZone(){
  const zone=document.getElementById('uploadZone'),fi=document.getElementById('fileInput');
  zone.addEventListener('dragover',e=>{e.preventDefault();zone.classList.add('drag-over');});
  zone.addEventListener('dragleave',()=>zone.classList.remove('drag-over'));
  zone.addEventListener('drop',e=>{e.preventDefault();zone.classList.remove('drag-over');handleFiles(e.dataTransfer.files);});
  fi.addEventListener('change',e=>{handleFiles(e.target.files);e.target.value='';});
}
function handleFiles(files){
  const brand=document.getElementById('uploadBrandSelect').value;
  [...files].forEach(f=>{
    if(!f.type.startsWith('image/'))return;
    const r=new FileReader();
    r.onload=async e=>{
      const resized=await resizeImage(e.target.result,500,400);
      const slide={src:resized,alt:f.name,brand:brand};
      if(!allSlides[brand])allSlides[brand]=[];
      allSlides[brand].push(slide);
      userImages.push(slide);
      renderUserThumbs();showSlide(getFilteredSlides().length-1);
      saveUserSlideImages();
    };
    r.readAsDataURL(f);
  });
}
function renderUserThumbs(){
  document.getElementById('userImgStrip').innerHTML=userImages.map((img,i)=>`<div class="user-img-thumb" onclick="currentBrandFilter='${img.brand}';showSlide(allSlides['${img.brand}'].indexOf(userImages[${i}]))"><img src="${img.src}" alt="${img.alt}"><div class="user-img-label">${img.brand}</div><button class="user-img-remove" onclick="event.stopPropagation();removeUserImage(${i})">\u2715</button></div>`).join('');
}
function removeUserImage(i){
  const s=userImages[i],arr=allSlides[s.brand];
  if(arr){const ai=arr.indexOf(s);if(ai>=0)arr.splice(ai,1);}
  userImages.splice(i,1);renderUserThumbs();
  const fs=getFilteredSlides();
  if(currentSlide>=fs.length)currentSlide=Math.max(0,fs.length-1);
  showSlide(currentSlide);
  saveUserSlideImages();
}

// ===== TAB LOGIC =====
function jumpSec(e){e.preventDefault();const id=e.target.getAttribute('href').substring(1);const el=document.getElementById(id);if(el)el.scrollIntoView({behavior:'smooth',block:'start'});}
function switchTab(id){
  document.querySelectorAll('.tab-content').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('tab-'+id).classList.add('active');
  event.target.classList.add('active');
}
function filterDist(mode,btn){
  document.querySelectorAll('.dist-controls .filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');renderDistDetail(mode);
}
document.addEventListener('keydown',e=>{
  if(!document.getElementById('tab-images').classList.contains('active'))return;
  if(e.key==='ArrowLeft')slideNav(-1);if(e.key==='ArrowRight')slideNav(1);
});

// ===== INIT =====
(async function(){
  // Render page immediately so it's usable
  renderOverview();renderClaimsBrandSelector();renderClaimsProfile(0);
  renderPricing();buildCheckGrid();renderDistDetail('all');
  renderCommon();renderMatrix();initSlideshow();setupUploadZone();
  // Then load saved data and re-render with it
  await loadSavedData();
  renderOverview();
  renderUserThumbs();
  // Re-show current slide if user images were loaded
  if(userImages.length>0){showSlide(0);}
})();
</script>
</body>
</html>
