<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Inglês para Programação</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:#0d0d14; --surface:#14141f; --surface2:#1c1c2e; --border:#2a2a40;
    --accent:#7c6af7; --accent2:#f772c0; --accent3:#72f7c6; --accent4:#f7c672;
    --text:#e8e8f0; --text-muted:#7878a0; --blue:#4a9eff; --green:#52e8a0; --orange:#f7924a;
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  body{background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;font-size:15px;line-height:1.7;overflow-x:hidden;}
  body::before{content:'';position:fixed;inset:0;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");pointer-events:none;z-index:0;opacity:0.5;}
  .grid-bg{position:fixed;inset:0;background-image:linear-gradient(rgba(124,106,247,0.04) 1px,transparent 1px),linear-gradient(90deg,rgba(124,106,247,0.04) 1px,transparent 1px);background-size:40px 40px;pointer-events:none;z-index:0;}
  .container{max-width:900px;margin:0 auto;padding:0 24px;position:relative;z-index:1;}

  /* HEADER */
  header{padding:60px 0 40px;border-bottom:1px solid var(--border);margin-bottom:60px;}
  .header-tag{font-family:'Space Mono',monospace;font-size:11px;color:var(--accent);letter-spacing:3px;text-transform:uppercase;margin-bottom:20px;display:flex;align-items:center;gap:10px;}
  .header-tag::before{content:'';width:24px;height:1px;background:var(--accent);}
  h1{font-family:'Syne',sans-serif;font-size:clamp(36px,6vw,64px);font-weight:800;line-height:1.1;letter-spacing:-2px;background:linear-gradient(135deg,#fff 30%,var(--accent) 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;margin-bottom:20px;}
  .header-sub{color:var(--text-muted);font-size:16px;max-width:560px;}

  /* STATS BAR */
  .stats-bar{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-top:28px;}
  .stat-item{background:var(--surface);border:1px solid var(--border);border-radius:12px;padding:16px;text-align:center;}
  .stat-num{font-family:'Space Mono',monospace;font-size:24px;font-weight:700;color:var(--accent);line-height:1;}
  .stat-label{font-size:11px;color:var(--text-muted);margin-top:4px;letter-spacing:0.5px;}
  @media(max-width:520px){.stats-bar{grid-template-columns:repeat(2,1fr);}}

  /* SECTIONS */
  section{margin-bottom:56px;}
  .section-label{font-family:'Space Mono',monospace;font-size:10px;letter-spacing:3px;text-transform:uppercase;color:var(--text-muted);margin-bottom:24px;display:flex;align-items:center;gap:12px;}
  .section-label::after{content:'';flex:1;height:1px;background:var(--border);}
  h3{font-family:'Syne',sans-serif;font-size:16px;font-weight:600;margin-bottom:6px;}

  /* BADGE */
  .badge{display:inline-flex;align-items:center;gap:6px;padding:4px 12px;border-radius:100px;font-family:'Space Mono',monospace;font-size:11px;font-weight:700;letter-spacing:1px;white-space:nowrap;}
  .badge-purple{background:rgba(124,106,247,0.15);color:var(--accent);border:1px solid rgba(124,106,247,0.3);}
  .badge-pink{background:rgba(247,114,192,0.15);color:var(--accent2);border:1px solid rgba(247,114,192,0.3);}
  .badge-green{background:rgba(82,232,160,0.12);color:var(--accent3);border:1px solid rgba(82,232,160,0.3);}
  .badge-orange{background:rgba(247,198,114,0.12);color:var(--accent4);border:1px solid rgba(247,198,114,0.3);}
  .badge-blue{background:rgba(74,158,255,0.12);color:var(--blue);border:1px solid rgba(74,158,255,0.3);}

  /* CARD */
  .card{background:var(--surface);border:1px solid var(--border);border-radius:16px;padding:28px;transition:border-color 0.2s,transform 0.2s;}
  .card-al{border-left:3px solid var(--accent);}
  .card-al-pink{border-left:3px solid var(--accent2);}
  .card-al-green{border-left:3px solid var(--accent3);}
  .card-al-orange{border-left:3px solid var(--accent4);}
  .card-al-blue{border-left:3px solid var(--blue);}
  .grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
  @media(max-width:640px){.grid-3{grid-template-columns:1fr;}}

  /* OBJETIVO */
  .objetivo-box{background:linear-gradient(135deg,rgba(124,106,247,0.12) 0%,rgba(247,114,192,0.08) 100%);border:1px solid rgba(124,106,247,0.3);border-radius:20px;padding:36px;text-align:center;position:relative;overflow:hidden;}
  .objetivo-box::before{content:'';position:absolute;top:-60px;right:-60px;width:200px;height:200px;background:radial-gradient(circle,rgba(124,106,247,0.15) 0%,transparent 70%);border-radius:50%;}
  .objetivo-box p{font-size:18px;color:var(--text);max-width:540px;margin:0 auto;}
  .objetivo-box strong{color:var(--accent);}

  /* ROTINA INTERATIVA */
  .rotina-card{background:var(--surface);border:1px solid var(--border);border-radius:16px;overflow:hidden;transition:border-color 0.3s,background 0.3s;margin-bottom:0;}
  .rotina-card.done{border-color:rgba(82,232,160,0.4);background:rgba(82,232,160,0.04);}
  .rotina-header{display:flex;gap:16px;align-items:center;padding:20px 24px;cursor:pointer;user-select:none;}
  .rotina-header:hover{background:rgba(255,255,255,0.02);}
  .rotina-number{font-family:'Space Mono',monospace;font-size:18px;font-weight:700;min-width:44px;height:44px;display:flex;align-items:center;justify-content:center;border-radius:12px;flex-shrink:0;transition:all 0.3s;}
  .rn-purple{background:rgba(124,106,247,0.15);color:var(--accent);}
  .rn-green{background:rgba(82,232,160,0.12);color:var(--accent3);}
  .rn-pink{background:rgba(247,114,192,0.15);color:var(--accent2);}
  .rn-orange{background:rgba(247,198,114,0.12);color:var(--accent4);}
  .rn-done{background:rgba(82,232,160,0.2);color:var(--accent3);}
  .rotina-info{flex:1;}
  .rotina-time{font-family:'Space Mono',monospace;font-size:10px;color:var(--text-muted);letter-spacing:1px;margin-bottom:2px;}
  .rotina-title{font-family:'Syne',sans-serif;font-weight:700;font-size:16px;}
  .rotina-check-btn{width:34px;height:34px;border-radius:50%;border:2px solid var(--border);background:transparent;cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:15px;transition:all 0.2s;color:var(--text-muted);flex-shrink:0;}
  .rotina-check-btn:hover{border-color:var(--accent3);color:var(--accent3);}
  .rotina-check-btn.checked{background:var(--accent3);border-color:var(--accent3);color:#0d0d14;font-weight:700;}
  .rotina-body{padding:0 24px 20px 84px;border-top:1px solid rgba(255,255,255,0.04);}
  .rotina-desc{color:var(--text-muted);font-size:14px;margin:12px 0 10px;}
  .rotina-tip{padding:8px 12px;background:rgba(255,255,255,0.04);border-radius:8px;font-size:13px;color:var(--text-muted);}
  .rotina-tip code{font-family:'Space Mono',monospace;font-size:11px;color:var(--accent3);}

  /* CALENDÁRIO */
  .calendar-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;}
  .cal-nav{background:var(--surface2);border:1px solid var(--border);border-radius:8px;width:36px;height:36px;color:var(--text);cursor:pointer;font-size:18px;display:flex;align-items:center;justify-content:center;transition:background 0.2s;}
  .cal-nav:hover{background:rgba(124,106,247,0.2);border-color:var(--accent);}
  .cal-month-title{font-family:'Syne',sans-serif;font-size:20px;font-weight:700;}
  .cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:4px;}
  .cal-weekday{text-align:center;font-family:'Space Mono',monospace;font-size:10px;color:var(--text-muted);padding:8px 0;letter-spacing:1px;}
  .cal-day{aspect-ratio:1;display:flex;align-items:center;justify-content:center;border-radius:10px;font-size:13px;font-family:'Space Mono',monospace;cursor:pointer;border:1px solid transparent;transition:all 0.15s;background:var(--surface2);color:var(--text-muted);position:relative;}
  .cal-day:hover:not(.cal-empty):not(.cal-future){border-color:rgba(124,106,247,0.5);color:var(--text);}
  .cal-empty{background:transparent;cursor:default;}
  .cal-future{opacity:0.3;cursor:not-allowed;}
  .cal-today{border-color:var(--accent);color:var(--accent);font-weight:700;}
  .cal-studied{background:rgba(82,232,160,0.15);border-color:rgba(82,232,160,0.5);color:var(--accent3);font-weight:700;}
  .cal-studied::after{content:'·';position:absolute;bottom:3px;font-size:16px;line-height:1;color:var(--accent3);}
  .cal-streak{margin-top:16px;display:flex;align-items:center;gap:12px;font-size:13px;color:var(--text-muted);}

  /* SEMANA */
  .week-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:8px;}
  @media(max-width:600px){.week-grid{grid-template-columns:repeat(3,1fr) !important;}}
  .week-day-card{background:var(--surface2);border:1px solid var(--border);border-radius:12px;padding:14px 10px;text-align:center;cursor:pointer;transition:all 0.2s;user-select:none;}
  .week-day-card:hover:not(.rest){border-color:rgba(124,106,247,0.4);transform:translateY(-2px);}
  .week-day-card.active{background:rgba(124,106,247,0.1);border-color:rgba(124,106,247,0.5);}
  .week-day-card.rest{cursor:default;opacity:0.5;}
  .week-day-name{font-family:'Syne',sans-serif;font-weight:700;font-size:13px;margin-bottom:10px;}
  .week-day-tasks{display:flex;flex-direction:column;gap:4px;}
  .wtchip{font-size:10px;padding:3px 7px;border-radius:6px;font-family:'Space Mono',monospace;letter-spacing:0.3px;}
  .wt-purple{background:rgba(124,106,247,0.2);color:var(--accent);}
  .wt-pink{background:rgba(247,114,192,0.2);color:var(--accent2);}
  .wt-green{background:rgba(82,232,160,0.15);color:var(--accent3);}
  .wt-orange{background:rgba(247,198,114,0.15);color:var(--accent4);}
  .wt-blue{background:rgba(74,158,255,0.15);color:var(--blue);}
  .wt-gray{background:rgba(120,120,160,0.15);color:var(--text-muted);}
  .week-day-check{margin-top:10px;font-size:18px;opacity:0;transition:opacity 0.2s;}
  .week-day-card.active .week-day-check{opacity:1;}

  /* VOCAB */
  .vocab-stats{display:flex;align-items:center;gap:16px;margin-bottom:14px;}
  .vocab-bar-wrap{flex:1;height:6px;background:var(--border);border-radius:100px;overflow:hidden;}
  .vocab-bar{height:100%;background:linear-gradient(90deg,var(--accent),var(--accent3));border-radius:100px;transition:width 0.4s ease;}
  .vocab-count-text{font-family:'Space Mono',monospace;font-size:11px;color:var(--text-muted);white-space:nowrap;}
  .vocab-grid{display:flex;flex-wrap:wrap;gap:8px;}
  .vocab-word{padding:8px 14px;background:var(--surface2);border:1px solid var(--border);border-radius:100px;font-family:'Space Mono',monospace;font-size:12px;cursor:pointer;transition:all 0.2s;user-select:none;display:flex;align-items:center;gap:6px;}
  .vocab-word:hover{background:rgba(124,106,247,0.12);border-color:rgba(124,106,247,0.4);color:var(--accent);}
  .vocab-word.learned{background:rgba(82,232,160,0.12);border-color:rgba(82,232,160,0.4);color:var(--accent3);}
  .v-trans{color:var(--text-muted);font-size:10px;}
  .vocab-word.learned .v-trans{color:rgba(82,232,160,0.6);}
  .v-check{font-size:10px;opacity:0;transition:opacity 0.2s;}
  .vocab-word.learned .v-check{opacity:1;}
  .small-btn{font-family:'Space Mono',monospace;font-size:10px;background:transparent;border:1px solid var(--border);color:var(--text-muted);border-radius:8px;padding:6px 12px;cursor:pointer;transition:all 0.2s;letter-spacing:1px;}
  .small-btn:hover{border-color:var(--accent2);color:var(--accent2);}

  /* FERRAMENTAS */
  .tool-card{display:flex;flex-direction:column;gap:8px;cursor:pointer;}
  .tool-card:hover{border-color:rgba(124,106,247,0.4);transform:translateY(-2px);}
  .tool-card.selected{border-color:rgba(124,106,247,0.55) !important;background:rgba(124,106,247,0.07);}
  .tool-icon-wrap{font-size:28px;margin-bottom:4px;transition:transform 0.2s;}
  .tool-card.selected .tool-icon-wrap{transform:scale(1.1);}
  .tool-name{font-family:'Syne',sans-serif;font-weight:700;font-size:15px;}
  .tool-desc{font-size:13px;color:var(--text-muted);line-height:1.5;}
  .tool-url{font-family:'Space Mono',monospace;font-size:10px;color:var(--accent);text-decoration:none;letter-spacing:0.5px;display:inline-flex;align-items:center;gap:4px;margin-top:auto;}
  .tool-url:hover{text-decoration:underline;}
  .tool-tag{font-family:'Space Mono',monospace;font-size:9px;background:rgba(124,106,247,0.2);color:var(--accent);border-radius:6px;padding:2px 8px;letter-spacing:1px;display:none;width:fit-content;}
  .tool-card.selected .tool-tag{display:block;}

  /* TIMELINE */
  .timeline{display:flex;flex-direction:column;}
  .timeline-item{display:flex;gap:24px;}
  .timeline-left{display:flex;flex-direction:column;align-items:center;min-width:60px;}
  .timeline-dot{width:56px;height:56px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Space Mono',monospace;font-weight:700;font-size:13px;flex-shrink:0;border:2px solid var(--border);z-index:1;}
  .td-1{border-color:var(--accent);background:rgba(124,106,247,0.15);color:var(--accent);box-shadow:0 0 20px rgba(124,106,247,0.3);}
  .td-2{border-color:var(--accent2);background:rgba(247,114,192,0.12);color:var(--accent2);box-shadow:0 0 20px rgba(247,114,192,0.2);}
  .td-3{border-color:var(--accent3);background:rgba(82,232,160,0.1);color:var(--accent3);box-shadow:0 0 20px rgba(82,232,160,0.2);}
  .timeline-line{width:2px;flex:1;background:linear-gradient(to bottom,var(--border),transparent);min-height:32px;}
  .timeline-content{padding:8px 0 40px;}
  .timeline-title{font-family:'Syne',sans-serif;font-size:20px;font-weight:700;margin-bottom:8px;}
  .timeline-items{list-style:none;color:var(--text-muted);font-size:14px;}
  .timeline-items li::before{content:'→ ';color:var(--accent);font-family:'Space Mono',monospace;}

  /* GOLDEN TIP */
  .golden-tip{background:linear-gradient(135deg,rgba(247,198,114,0.08) 0%,rgba(247,146,74,0.06) 100%);border:1px solid rgba(247,198,114,0.25);border-radius:20px;padding:36px;position:relative;overflow:hidden;}
  .golden-tip::after{content:'⚡';position:absolute;right:24px;top:50%;transform:translateY(-50%);font-size:80px;opacity:0.06;}
  .golden-tip h3{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;color:var(--accent4);margin-bottom:16px;}
  .golden-tip-item{display:flex;align-items:center;gap:12px;font-size:15px;margin-bottom:10px;}
  .gti-arrow{font-family:'Space Mono',monospace;color:var(--accent4);font-size:12px;}

  /* RESUMO */
  .resumo-box{background:linear-gradient(135deg,rgba(82,232,160,0.08) 0%,rgba(74,158,255,0.06) 100%);border:1px solid rgba(82,232,160,0.2);border-radius:20px;padding:36px;text-align:center;}
  .resumo-checks{display:flex;justify-content:center;gap:32px;margin:20px 0;flex-wrap:wrap;}
  .chk-item{display:flex;align-items:center;gap:8px;font-size:15px;}
  .chk{width:22px;height:22px;border-radius:50%;background:rgba(82,232,160,0.2);color:var(--accent3);display:flex;align-items:center;justify-content:center;font-size:12px;flex-shrink:0;}
  .resumo-final{font-family:'Syne',sans-serif;font-size:20px;font-weight:700;color:var(--accent3);margin-top:16px;}

  /* TOAST */
  .toast{position:fixed;bottom:24px;right:24px;background:var(--surface2);border:1px solid var(--border);border-radius:12px;padding:14px 20px;font-size:13px;font-family:'Space Mono',monospace;z-index:1000;transform:translateY(80px);opacity:0;transition:all 0.3s ease;pointer-events:none;max-width:260px;}
  .toast.show{transform:translateY(0);opacity:1;}
  .toast.tg{border-color:rgba(82,232,160,0.4);color:var(--accent3);}
  .toast.tp{border-color:rgba(124,106,247,0.4);color:var(--accent);}

  footer{border-top:1px solid var(--border);padding:40px 0;margin-top:80px;text-align:center;color:var(--text-muted);font-family:'Space Mono',monospace;font-size:11px;letter-spacing:1px;}

  @keyframes fadeInUp{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}
  .fade-in{animation:fadeInUp 0.5s ease forwards;}
  @keyframes pop{0%{transform:scale(1)}50%{transform:scale(1.18)}100%{transform:scale(1)}}
  .pop{animation:pop 0.22s ease;}
</style>
</head>
<body>

<div class="grid-bg"></div>
<div class="toast" id="toast"></div>

<div class="container">

  <!-- HEADER + STATS -->
  <header class="fade-in">
    <div class="header-tag">Plano de Estudos · 3 a 6 meses</div>
    <h1>Inglês para<br>Programação</h1>
    <p class="header-sub">Aprenda a ler, entender documentação, códigos e conteúdos técnicos em inglês.</p>
    <div class="stats-bar">
      <div class="stat-item"><div class="stat-num" id="stat-dias">0</div><div class="stat-label">Dias estudados</div></div>
      <div class="stat-item"><div class="stat-num" id="stat-streak">0</div><div class="stat-label">Sequência 🔥</div></div>
      <div class="stat-item"><div class="stat-num" id="stat-vocab">0</div><div class="stat-label">Palavras aprendidas</div></div>
      <div class="stat-item"><div class="stat-num" id="stat-rotina">0/4</div><div class="stat-label">Rotina de hoje</div></div>
    </div>
  </header>

  <!-- 01 OBJETIVO -->
  <section class="fade-in">
    <div class="section-label">01 — Objetivo</div>
    <div class="objetivo-box">
      <p>Aprender a <strong>ler</strong>, <strong>entender documentação</strong>, <strong>códigos</strong> e <strong>conteúdos técnicos</strong> em inglês — sem depender de tradução para cada palavra.</p>
    </div>
  </section>

  <!-- 02 ROTINA INTERATIVA -->
  <section class="fade-in">
    <div class="section-label">02 — Rotina de Hoje</div>
    <p style="color:var(--text-muted);font-size:13px;margin-bottom:16px;">Clique no ✓ para marcar cada atividade como concluída.</p>
    <div style="display:flex;flex-direction:column;gap:12px;">

      <div class="rotina-card" id="rotina-0">
        <div class="rotina-header" onclick="toggleRotinaBody(0)">
          <div class="rotina-number rn-purple" id="rnum-0">1</div>
          <div class="rotina-info">
            <div class="rotina-time">15 – 20 MIN</div>
            <div class="rotina-title">Vocabulário técnico</div>
          </div>
          <button class="rotina-check-btn" id="rbtn-0" onclick="event.stopPropagation();checkRotina(0)" title="Marcar como feito">✓</button>
        </div>
        <div class="rotina-body" id="rbody-0" style="display:none;">
          <p class="rotina-desc">Aprenda palavras essenciais: <code>function, variable, request, response, database, query, server, error, login, authentication, API</code></p>
          <div class="rotina-tip">📌 Use <code>Anki</code> (flashcards) ou caderno · 10 a 20 palavras por dia</div>
        </div>
      </div>

      <div class="rotina-card" id="rotina-1">
        <div class="rotina-header" onclick="toggleRotinaBody(1)">
          <div class="rotina-number rn-green" id="rnum-1">2</div>
          <div class="rotina-info">
            <div class="rotina-time">20 – 30 MIN</div>
            <div class="rotina-title">Leitura prática</div>
          </div>
          <button class="rotina-check-btn" id="rbtn-1" onclick="event.stopPropagation();checkRotina(1)" title="Marcar como feito">✓</button>
        </div>
        <div class="rotina-body" id="rbody-1" style="display:none;">
          <p class="rotina-desc">Leia conteúdos reais: documentação · artigos de programação · tutoriais</p>
          <div class="rotina-tip">📌 <strong style="color:var(--text)">Regra:</strong> <code>NÃO traduz tudo</code> — tente entender pelo contexto</div>
        </div>
      </div>

      <div class="rotina-card" id="rotina-2">
        <div class="rotina-header" onclick="toggleRotinaBody(2)">
          <div class="rotina-number rn-pink" id="rnum-2">3</div>
          <div class="rotina-info">
            <div class="rotina-time">20 – 30 MIN</div>
            <div class="rotina-title">Vídeos com legenda</div>
          </div>
          <button class="rotina-check-btn" id="rbtn-2" onclick="event.stopPropagation();checkRotina(2)" title="Marcar como feito">✓</button>
        </div>
        <div class="rotina-body" id="rbody-2" style="display:none;">
          <p class="rotina-desc">YouTube (programação, tecnologia) com <span style="color:var(--accent)">legenda em inglês</span></p>
          <div class="rotina-tip">📌 Ex: <code>"How to build an API"</code> · <code>"JavaScript tutorial"</code></div>
        </div>
      </div>

      <div class="rotina-card" id="rotina-3">
        <div class="rotina-header" onclick="toggleRotinaBody(3)">
          <div class="rotina-number rn-orange" id="rnum-3">4</div>
          <div class="rotina-info">
            <div class="rotina-time">10 – 15 MIN</div>
            <div class="rotina-title">Tradução ativa</div>
          </div>
          <button class="rotina-check-btn" id="rbtn-3" onclick="event.stopPropagation();checkRotina(3)" title="Marcar como feito">✓</button>
        </div>
        <div class="rotina-body" id="rbody-3" style="display:none;">
          <p class="rotina-desc">Pegue um trecho em inglês → tente traduzir sozinho → depois confira</p>
          <div class="rotina-tip">📌 Copie um parágrafo de qualquer doc técnica e tente ao máximo antes de verificar</div>
        </div>
      </div>

    </div>
  </section>

  <!-- 03 CALENDÁRIO DE ESTUDOS -->
  <section class="fade-in">
    <div class="section-label">03 — Calendário de Estudos</div>
    <div class="card">
      <div class="calendar-header">
        <button class="cal-nav" onclick="changeMonth(-1)">‹</button>
        <div class="cal-month-title" id="cal-title"></div>
        <button class="cal-nav" onclick="changeMonth(1)">›</button>
      </div>
      <div class="cal-grid" id="cal-grid"></div>
      <div class="cal-streak">
        <span style="font-size:20px;">🔥</span>
        <span id="streak-text" style="font-size:13px;"></span>
      </div>
    </div>
  </section>

  <!-- 04 SEMANA INTERATIVA -->
  <section class="fade-in">
    <div class="section-label">04 — Semana Estruturada</div>
    <p style="color:var(--text-muted);font-size:13px;margin-bottom:16px;">Clique no dia para marcá-lo como seu dia atual de estudo.</p>
    <div class="week-grid">
      <div class="week-day-card" id="wd-0" onclick="selectWeekDay(0)">
        <div class="week-day-name">Seg</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-purple">Vocabulário</span>
          <span class="wtchip wt-green">Leitura</span>
        </div>
        <div class="week-day-check">✓</div>
      </div>
      <div class="week-day-card" id="wd-1" onclick="selectWeekDay(1)">
        <div class="week-day-name">Ter</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-pink">Vídeo</span>
          <span class="wtchip wt-green">Leitura</span>
        </div>
        <div class="week-day-check">✓</div>
      </div>
      <div class="week-day-card" id="wd-2" onclick="selectWeekDay(2)">
        <div class="week-day-name">Qua</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-purple">Vocabulário</span>
          <span class="wtchip wt-blue">Prática</span>
        </div>
        <div class="week-day-check">✓</div>
      </div>
      <div class="week-day-card" id="wd-3" onclick="selectWeekDay(3)">
        <div class="week-day-name">Qui</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-pink">Vídeo</span>
          <span class="wtchip wt-orange">Tradução</span>
        </div>
        <div class="week-day-check">✓</div>
      </div>
      <div class="week-day-card" id="wd-4" onclick="selectWeekDay(4)">
        <div class="week-day-name">Sex</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-green">Revisão</span>
        </div>
        <div class="week-day-check">✓</div>
      </div>
      <div class="week-day-card" id="wd-5" onclick="selectWeekDay(5)">
        <div class="week-day-name">Sáb</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-blue">Livre</span>
        </div>
        <div class="week-day-check">✓</div>
      </div>
      <div class="week-day-card rest" id="wd-6">
        <div class="week-day-name">Dom</div>
        <div class="week-day-tasks">
          <span class="wtchip wt-gray">Descanso 🌙</span>
        </div>
      </div>
    </div>
  </section>

  <!-- 05 FERRAMENTAS INTERATIVAS -->
  <section class="fade-in">
    <div class="section-label">05 — Ferramentas</div>
    <p style="color:var(--text-muted);font-size:13px;margin-bottom:16px;">Clique para marcar as ferramentas que você já utiliza.</p>
    <div class="grid-3">
      <div class="card tool-card card-al-blue" id="tool-0" onclick="toggleTool(0)">
        <span class="tool-tag">EM USO ✓</span>
        <div class="tool-icon-wrap">🌐</div>
        <div class="tool-name">Google Tradutor</div>
        <div class="tool-desc">Use com moderação para traduções rápidas e pontuais</div>
        <a href="https://translate.google.com" target="_blank" class="tool-url" onclick="event.stopPropagation()">translate.google.com ↗</a>
      </div>
      <div class="card tool-card card-al" id="tool-1" onclick="toggleTool(1)">
        <span class="tool-tag">EM USO ✓</span>
        <div class="tool-icon-wrap">✨</div>
        <div class="tool-name">DeepL</div>
        <div class="tool-desc">Melhor tradução com contexto mais natural e preciso</div>
        <a href="https://www.deepl.com" target="_blank" class="tool-url" onclick="event.stopPropagation()">deepl.com ↗</a>
      </div>
      <div class="card tool-card card-al-green" id="tool-2" onclick="toggleTool(2)">
        <span class="tool-tag">EM USO ✓</span>
        <div class="tool-icon-wrap">🧠</div>
        <div class="tool-name">Anki</div>
        <div class="tool-desc">Repetição espaçada para memorização eficiente</div>
        <a href="https://apps.ankiweb.net" target="_blank" class="tool-url" onclick="event.stopPropagation()">ankiweb.net ↗</a>
      </div>
      <div class="card tool-card card-al-pink" id="tool-3" onclick="toggleTool(3)">
        <span class="tool-tag">EM USO ✓</span>
        <div class="tool-icon-wrap">▶️</div>
        <div class="tool-name">YouTube</div>
        <div class="tool-desc">Vídeos de programação com legendas em inglês</div>
        <a href="https://www.youtube.com" target="_blank" class="tool-url" onclick="event.stopPropagation()">youtube.com ↗</a>
      </div>
      <div class="card tool-card card-al-orange" id="tool-4" onclick="toggleTool(4)">
        <span class="tool-tag">EM USO ✓</span>
        <div class="tool-icon-wrap">💬</div>
        <div class="tool-name">ChatGPT</div>
        <div class="tool-desc">Para tirar dúvidas de vocabulário e praticar</div>
        <a href="https://chat.openai.com" target="_blank" class="tool-url" onclick="event.stopPropagation()">chat.openai.com ↗</a>
      </div>
      <div class="card tool-card card-al-blue" id="tool-5" onclick="toggleTool(5)">
        <span class="tool-tag">EM USO ✓</span>
        <div class="tool-icon-wrap">📖</div>
        <div class="tool-name">MDN Docs</div>
        <div class="tool-desc">Documentação de referência em inglês técnico</div>
        <a href="https://developer.mozilla.org" target="_blank" class="tool-url" onclick="event.stopPropagation()">developer.mozilla.org ↗</a>
      </div>
    </div>
  </section>

  <!-- 06 VOCABULÁRIO INTERATIVO -->
  <section class="fade-in">
    <div class="section-label">06 — Vocabulário Essencial</div>
    <div class="card">
      <div class="vocab-stats">
        <div class="vocab-bar-wrap"><div class="vocab-bar" id="vocab-bar" style="width:0%"></div></div>
        <span class="vocab-count-text" id="vocab-count">0 / 28</span>
        <button class="small-btn" onclick="resetVocab()">RESETAR</button>
      </div>
      <p style="color:var(--text-muted);font-size:13px;margin-bottom:14px;">Clique nas palavras que você já conhece para marcá-las como aprendidas.</p>
      <div class="vocab-grid" id="vocab-grid"></div>
    </div>
  </section>

  <!-- 07 EVOLUÇÃO -->
  <section class="fade-in">
    <div class="section-label">07 — Evolução Esperada</div>
    <div class="timeline">
      <div class="timeline-item">
        <div class="timeline-left"><div class="timeline-dot td-1">1M</div><div class="timeline-line"></div></div>
        <div class="timeline-content">
          <div class="timeline-title">1º mês</div>
          <ul class="timeline-items"><li>Entende palavras básicas</li><li>Começa a reconhecer padrões</li></ul>
        </div>
      </div>
      <div class="timeline-item">
        <div class="timeline-left"><div class="timeline-dot td-2">2–3M</div><div class="timeline-line"></div></div>
        <div class="timeline-content">
          <div class="timeline-title">2–3 meses</div>
          <ul class="timeline-items"><li>Entende documentação simples</li><li>Consegue estudar programação em inglês</li></ul>
        </div>
      </div>
      <div class="timeline-item">
        <div class="timeline-left"><div class="timeline-dot td-3">4–6M</div></div>
        <div class="timeline-content">
          <div class="timeline-title">4–6 meses</div>
          <ul class="timeline-items"><li>Lê quase tudo com boa compreensão</li><li>Depende pouco de tradução</li></ul>
        </div>
      </div>
    </div>
  </section>

  <!-- 08 DICA DE OURO -->
  <section class="fade-in">
    <div class="section-label">08 — Dica de Ouro</div>
    <div class="golden-tip">
      <h3>🔥 Isso acelera MUITO</h3>
      <div class="golden-tip-item"><span class="gti-arrow">→</span><span>Estude inglês + programação <strong style="color:var(--accent4)">juntos</strong></span></div>
      <div class="golden-tip-item"><span class="gti-arrow">→</span><span>Ver código em inglês · ler erros em inglês · assistir aulas em inglês</span></div>
      <div class="golden-tip-item"><span class="gti-arrow">→</span><span>O contexto real <strong style="color:var(--accent4)">acelera o aprendizado</strong> muito mais do que exercícios isolados</span></div>
    </div>
  </section>

  <!-- 09 RESUMO -->
  <section class="fade-in">
    <div class="section-label">09 — Resumo</div>
    <div class="resumo-box">
      <p style="color:var(--text-muted);font-size:15px;margin-bottom:8px;">Se você seguir isso:</p>
      <div class="resumo-checks">
        <div class="chk-item"><div class="chk">✓</div><span>1h–2h por dia</span></div>
        <div class="chk-item"><div class="chk">✓</div><span>Foco em conteúdo real</span></div>
        <div class="chk-item"><div class="chk">✓</div><span>Consistência diária</span></div>
      </div>
      <div class="resumo-final">👉 Em 3 a 6 meses você já lê inglês técnico tranquilo</div>
    </div>
    <br>
    <div style="text-align:center;margin-top:16px;">
      <button class="small-btn" onclick="resetAll()">↺ RESETAR TODO O PROGRESSO</button>
    </div>
  </section>

</div>

<footer>
  <div class="container">Inglês para Programação · Plano de 3 a 6 meses · Seja consistente 🚀</div>
</footer>

<script>
// ===== STORAGE =====
const ls = { get: k => { try { return JSON.parse(localStorage.getItem(k)) } catch(e) { return null } }, set: (k,v) => localStorage.setItem(k, JSON.stringify(v)) }

// ===== TOAST =====
let toastTimer
function toast(msg, type='tg') {
  const el = document.getElementById('toast')
  el.textContent = msg; el.className = 'toast show ' + type
  clearTimeout(toastTimer)
  toastTimer = setTimeout(() => el.className = 'toast', 2600)
}

// ===== TODAY KEY =====
const todayKey = () => { const d = new Date(); return `${d.getFullYear()}-${d.getMonth()+1}-${d.getDate()}` }

// ===== VOCABULARY =====
const VOCAB = [
  ['function','função'],['variable','variável'],['request','requisição'],['response','resposta'],
  ['database','banco de dados'],['query','consulta'],['server','servidor'],['error','erro'],
  ['login','acesso'],['authentication','autenticação'],['array','vetor'],['object','objeto'],
  ['string','texto'],['boolean','lógico'],['loop','laço'],['condition','condição'],
  ['return','retornar'],['parameter','parâmetro'],['callback','retorno'],['promise','promessa'],
  ['async','assíncrono'],['await','aguardar'],['debug','depurar'],['deploy','publicar'],
  ['commit','confirmar'],['branch','ramificação'],['merge','mesclar'],['compile','compilar']
]

function renderVocab() {
  const learned = ls.get('vocab_learned') || []
  const grid = document.getElementById('vocab-grid')
  grid.innerHTML = ''
  VOCAB.forEach(([en, pt], i) => {
    const el = document.createElement('span')
    el.className = 'vocab-word' + (learned.includes(i) ? ' learned' : '')
    el.innerHTML = `${en} <span class="v-trans">${pt}</span><span class="v-check"> ✓</span>`
    el.onclick = () => toggleVocab(i)
    grid.appendChild(el)
  })
  const count = learned.length
  const pct = Math.round(count / VOCAB.length * 100)
  document.getElementById('vocab-bar').style.width = pct + '%'
  document.getElementById('vocab-count').textContent = `${count} / ${VOCAB.length}`
}

function toggleVocab(i) {
  const learned = ls.get('vocab_learned') || []
  const idx = learned.indexOf(i)
  if (idx >= 0) { learned.splice(idx, 1); toast(`"${VOCAB[i][0]}" desmarcada`) }
  else { learned.push(i); toast(`"${VOCAB[i][0]}" aprendida! 🎉`) }
  ls.set('vocab_learned', learned)
  renderVocab(); updateStats()
}

function resetVocab() {
  if (!confirm('Resetar palavras aprendidas?')) return
  ls.set('vocab_learned', []); renderVocab(); updateStats()
  toast('Vocabulário resetado', 'tp')
}

// ===== ROTINA =====
function toggleRotinaBody(idx) {
  const el = document.getElementById('rbody-' + idx)
  el.style.display = el.style.display === 'none' ? 'block' : 'none'
}

function checkRotina(idx) {
  const key = 'rotinas_' + todayKey()
  const done = ls.get(key) || []
  const pos = done.indexOf(idx)
  if (pos >= 0) { done.splice(pos, 1); toast(['Vocabulário','Leitura','Vídeos','Tradução'][idx] + ' desmarcado') }
  else { done.push(idx); toast(['Vocabulário','Leitura','Vídeos','Tradução'][idx] + ' concluído! ✓') }
  ls.set(key, done); renderRotinas(); updateStats()
}

function renderRotinas() {
  const done = ls.get('rotinas_' + todayKey()) || []
  for (let i = 0; i < 4; i++) {
    const card = document.getElementById('rotina-' + i)
    const btn  = document.getElementById('rbtn-' + i)
    const num  = document.getElementById('rnum-' + i)
    const isDone = done.includes(i)
    card.classList.toggle('done', isDone)
    btn.classList.toggle('checked', isDone)
    if (isDone) { num.className = 'rotina-number rn-done' }
    else { num.className = 'rotina-number ' + ['rn-purple','rn-green','rn-pink','rn-orange'][i] }
  }
}

// ===== CALENDAR =====
let calY, calM
function renderCalendar() {
  const now = new Date()
  if (calY === undefined) { calY = now.getFullYear(); calM = now.getMonth() }
  const months = ['Janeiro','Fevereiro','Março','Abril','Maio','Junho','Julho','Agosto','Setembro','Outubro','Novembro','Dezembro']
  document.getElementById('cal-title').textContent = `${months[calM]} ${calY}`
  const studied = ls.get('studied_days') || {}
  const grid = document.getElementById('cal-grid')
  grid.innerHTML = ''
  // headers
  'DSTQQSS'.split('').forEach(d => { const el = document.createElement('div'); el.className = 'cal-weekday'; el.textContent = d; grid.appendChild(el) })
  const firstDay = new Date(calY, calM, 1).getDay()
  const totalDays = new Date(calY, calM + 1, 0).getDate()
  for (let i = 0; i < firstDay; i++) { const el = document.createElement('div'); el.className = 'cal-day cal-empty'; grid.appendChild(el) }
  for (let d = 1; d <= totalDays; d++) {
    const key = `${calY}-${calM+1}-${d}`
    const isToday = calY === now.getFullYear() && calM === now.getMonth() && d === now.getDate()
    const isFuture = new Date(calY, calM, d) > now && !isToday
    const el = document.createElement('div')
    el.className = 'cal-day' + (isToday ? ' cal-today' : '') + (isFuture ? ' cal-future' : '') + (studied[key] ? ' cal-studied' : '')
    el.textContent = d
    if (!isFuture) el.onclick = () => toggleStudyDay(key)
    grid.appendChild(el)
  }
  updateStreakText()
}

function toggleStudyDay(key) {
  const studied = ls.get('studied_days') || {}
  if (studied[key]) { delete studied[key]; toast('Dia desmarcado', 'tp') }
  else { studied[key] = true; toast('Dia de estudo marcado! 🎉') }
  ls.set('studied_days', studied); renderCalendar(); updateStats()
}

function changeMonth(dir) {
  calM += dir
  if (calM > 11) { calM = 0; calY++ }
  if (calM < 0)  { calM = 11; calY-- }
  renderCalendar()
}

function calcStreak() {
  const studied = ls.get('studied_days') || {}
  let streak = 0
  const now = new Date()
  for (let i = 0; i < 365; i++) {
    const d = new Date(now); d.setDate(d.getDate() - i)
    const key = `${d.getFullYear()}-${d.getMonth()+1}-${d.getDate()}`
    if (studied[key]) streak++
    else if (i > 0) break
  }
  return streak
}

function updateStreakText() {
  const studied = ls.get('studied_days') || {}
  const total = Object.keys(studied).length
  const streak = calcStreak()
  const el = document.getElementById('streak-text')
  el.textContent = total === 0
    ? 'Clique em um dia para marcar que você estudou.'
    : `${total} dia(s) estudado(s) · Sequência atual: ${streak} dia(s) 🔥`
}

// ===== WEEK =====
function selectWeekDay(idx) {
  const prev = ls.get('selected_weekday')
  const next = prev === idx ? null : idx
  ls.set('selected_weekday', next)
  for (let i = 0; i < 7; i++) { const el = document.getElementById('wd-' + i); if (el) el.classList.toggle('active', i === next) }
  if (next !== null) toast(['Segunda','Terça','Quarta','Quinta','Sexta','Sábado'][next] + ' selecionado!', 'tp')
}

function renderWeekDay() {
  const saved = ls.get('selected_weekday')
  for (let i = 0; i < 7; i++) { const el = document.getElementById('wd-' + i); if (el) el.classList.toggle('active', i === saved) }
}

// ===== TOOLS =====
const TOOL_NAMES = ['Google Tradutor','DeepL','Anki','YouTube','ChatGPT','MDN Docs']
function toggleTool(idx) {
  const tools = ls.get('selected_tools') || []
  const pos = tools.indexOf(idx)
  if (pos >= 0) { tools.splice(pos, 1); toast(TOOL_NAMES[idx] + ' removido', 'tp') }
  else { tools.push(idx); toast(TOOL_NAMES[idx] + ' adicionado! ✓', 'tp') }
  ls.set('selected_tools', tools); renderTools()
}

function renderTools() {
  const tools = ls.get('selected_tools') || []
  for (let i = 0; i < 6; i++) { const el = document.getElementById('tool-' + i); if (el) el.classList.toggle('selected', tools.includes(i)) }
}

// ===== STATS =====
function updateStats() {
  const total   = Object.keys(ls.get('studied_days') || {}).length
  const streak  = calcStreak()
  const vocab   = (ls.get('vocab_learned') || []).length
  const rotinas = (ls.get('rotinas_' + todayKey()) || []).length
  const ids = ['stat-dias','stat-streak','stat-vocab','stat-rotina']
  const vals = [total, streak, vocab, rotinas + '/4']
  ids.forEach((id, i) => {
    const el = document.getElementById(id)
    el.textContent = vals[i]
    el.classList.remove('pop'); void el.offsetWidth; el.classList.add('pop')
  })
}

// ===== RESET ALL =====
function resetAll() {
  if (!confirm('Apagar TODO o progresso? Isso não pode ser desfeito.')) return
  localStorage.clear()
  renderVocab(); renderRotinas(); renderCalendar(); renderWeekDay(); renderTools(); updateStats()
  toast('Progresso resetado', 'tp')
}

// ===== INIT =====
document.addEventListener('DOMContentLoaded', () => {
  renderVocab(); renderRotinas(); renderCalendar(); renderWeekDay(); renderTools(); updateStats()
  // Auto-select today's weekday if not set
  if (ls.get('selected_weekday') === null || ls.get('selected_weekday') === undefined) {
    const map = {1:0, 2:1, 3:2, 4:3, 5:4, 6:5}
    const wd = map[new Date().getDay()]
    if (wd !== undefined) { ls.set('selected_weekday', wd); renderWeekDay() }
  }
})
</script>
</body>
</html>
