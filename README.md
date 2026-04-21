<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GIT CODE.RG — VCETAOA OBITUARY</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=VT323&display=swap" rel="stylesheet">
<style>
  :root {
    --cyan: #00FFFF;
    --magenta: #FF00FF;
    --green: #00FF41;
    --yellow: #FFD700;
    --red: #FF0040;
    --orange: #FF6600;
    --blue: #0080FF;
    --white: #F0F0F0;
    --bg: #000000;
    --dim: #111111;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--green);
    font-family: 'Share Tech Mono', monospace;
    font-size: 14px;
    line-height: 1.6;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* SCANLINE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,255,65,0.015) 2px,
      rgba(0,255,65,0.015) 4px
    );
    pointer-events: none;
    z-index: 9999;
  }

  /* RAIN CANVAS */
  #rain { position: fixed; top: 0; left: 0; z-index: 0; opacity: 0.12; pointer-events: none; }

  .wrapper { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 20px; }

  /* ═══════════════════ GLITCH TEXT ═══════════════════ */
  .glitch {
    position: relative;
    display: inline-block;
    animation: glitch-skew 3s infinite linear alternate-reverse;
  }
  .glitch::before, .glitch::after {
    content: attr(data-text);
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
  }
  .glitch::before {
    color: var(--magenta);
    animation: glitch-before 2s infinite;
    clip-path: polygon(0 0, 100% 0, 100% 33%, 0 33%);
  }
  .glitch::after {
    color: var(--cyan);
    animation: glitch-after 2s infinite;
    clip-path: polygon(0 67%, 100% 67%, 100% 100%, 0 100%);
  }
  @keyframes glitch-before {
    0%   { transform: translate(-2px, 0); }
    20%  { transform: translate(2px, 0); }
    40%  { transform: translate(-1px, 2px); }
    60%  { transform: translate(1px, -1px); }
    80%  { transform: translate(0, 1px); }
    100% { transform: translate(-2px, 0); }
  }
  @keyframes glitch-after {
    0%   { transform: translate(2px, 0); }
    20%  { transform: translate(-2px, 0); }
    40%  { transform: translate(1px, -2px); }
    60%  { transform: translate(-1px, 1px); }
    80%  { transform: translate(0, -1px); }
    100% { transform: translate(2px, 0); }
  }
  @keyframes glitch-skew {
    0%   { transform: skew(0deg); }
    10%  { transform: skew(-0.5deg); }
    30%  { transform: skew(0.3deg); }
    50%  { transform: skew(0deg); }
    70%  { transform: skew(-0.2deg); }
    100% { transform: skew(0deg); }
  }

  /* ═══════════════════ HEADER ═══════════════════ */
  .header {
    text-align: center;
    padding: 40px 20px;
    border: 1px solid var(--green);
    margin-bottom: 30px;
    position: relative;
    background: linear-gradient(180deg, rgba(0,255,65,0.04) 0%, transparent 100%);
    box-shadow: 0 0 30px rgba(0,255,65,0.15), inset 0 0 30px rgba(0,255,65,0.03);
  }
  .header::before {
    content: '▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓';
    display: block;
    color: var(--green);
    font-size: 9px;
    opacity: 0.4;
    margin-bottom: 10px;
    overflow: hidden;
  }

  .arcade-title {
    font-family: 'VT323', monospace;
    font-size: clamp(48px, 8vw, 96px);
    color: var(--cyan);
    text-shadow:
      0 0 10px var(--cyan),
      0 0 20px var(--cyan),
      0 0 40px var(--cyan),
      0 0 80px rgba(0,255,255,0.5);
    letter-spacing: 8px;
    animation: flicker 4s infinite;
  }
  @keyframes flicker {
    0%, 96%, 100% { opacity: 1; }
    97% { opacity: 0.3; }
    98% { opacity: 1; }
    99% { opacity: 0.1; }
  }

  .subtitle {
    font-family: 'Orbitron', monospace;
    font-size: clamp(10px, 2vw, 16px);
    color: var(--magenta);
    letter-spacing: 6px;
    margin-top: 10px;
    text-shadow: 0 0 10px var(--magenta), 0 0 20px var(--magenta);
    animation: pulse-magenta 2s infinite alternate;
  }
  @keyframes pulse-magenta {
    from { text-shadow: 0 0 5px var(--magenta); }
    to   { text-shadow: 0 0 15px var(--magenta), 0 0 30px var(--magenta), 0 0 60px rgba(255,0,255,0.4); }
  }

  .japanese {
    font-size: 22px;
    color: var(--yellow);
    margin-top: 8px;
    text-shadow: 0 0 15px var(--yellow);
    letter-spacing: 4px;
    animation: pulse-yellow 3s infinite alternate;
  }
  @keyframes pulse-yellow {
    from { opacity: 0.8; }
    to   { opacity: 1; text-shadow: 0 0 20px var(--yellow), 0 0 40px rgba(255,215,0,0.5); }
  }

  .insert-coin {
    font-family: 'Orbitron', monospace;
    font-size: 18px;
    color: var(--white);
    margin-top: 20px;
    animation: blink 1s step-end infinite;
    letter-spacing: 3px;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* ═══════════════════ BADGES ═══════════════════ */
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin: 20px 0;
  }
  .badge {
    font-family: 'Orbitron', monospace;
    font-size: 11px;
    padding: 6px 14px;
    border: 1px solid currentColor;
    letter-spacing: 2px;
    text-transform: uppercase;
    position: relative;
    overflow: hidden;
    cursor: default;
    transition: all 0.2s;
  }
  .badge::before {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
    animation: scan 3s infinite;
  }
  @keyframes scan { to { left: 200%; } }
  .badge:hover { transform: scale(1.05); filter: brightness(1.3); }
  .badge-cyan    { color: var(--cyan);    box-shadow: 0 0 8px var(--cyan);    background: rgba(0,255,255,0.05); }
  .badge-magenta { color: var(--magenta); box-shadow: 0 0 8px var(--magenta); background: rgba(255,0,255,0.05); }
  .badge-yellow  { color: var(--yellow);  box-shadow: 0 0 8px var(--yellow);  background: rgba(255,215,0,0.05); }
  .badge-red     { color: var(--red);     box-shadow: 0 0 8px var(--red);     background: rgba(255,0,64,0.05); animation: badge-alarm 1.5s infinite alternate; }
  .badge-green   { color: var(--green);   box-shadow: 0 0 8px var(--green);   background: rgba(0,255,65,0.05); }
  @keyframes badge-alarm {
    from { box-shadow: 0 0 5px var(--red); }
    to   { box-shadow: 0 0 20px var(--red), 0 0 40px rgba(255,0,64,0.4); }
  }

  /* ═══════════════════ SECTION BLOCKS ═══════════════════ */
  .section {
    margin: 30px 0;
    position: relative;
  }
  .section-title {
    font-family: 'Orbitron', monospace;
    font-size: 14px;
    letter-spacing: 3px;
    padding: 8px 0;
    margin-bottom: 15px;
    border-bottom: 1px solid;
    text-transform: uppercase;
  }
  .title-cyan    { color: var(--cyan);    border-color: var(--cyan);    text-shadow: 0 0 10px var(--cyan); }
  .title-magenta { color: var(--magenta); border-color: var(--magenta); text-shadow: 0 0 10px var(--magenta); }
  .title-yellow  { color: var(--yellow);  border-color: var(--yellow);  text-shadow: 0 0 10px var(--yellow); }
  .title-red     { color: var(--red);     border-color: var(--red);     text-shadow: 0 0 10px var(--red); }
  .title-green   { color: var(--green);   border-color: var(--green);   text-shadow: 0 0 10px var(--green); }
  .title-orange  { color: var(--orange);  border-color: var(--orange);  text-shadow: 0 0 10px var(--orange); }

  /* ═══════════════════ CODE BLOCKS ═══════════════════ */
  .code-block {
    background: var(--dim);
    border: 1px solid;
    padding: 20px;
    position: relative;
    overflow: hidden;
  }
  .code-block::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, currentColor, transparent);
    animation: scan-top 4s infinite linear;
    opacity: 0.6;
  }
  @keyframes scan-top { from { transform: translateX(-100%); } to { transform: translateX(100%); } }
  .cb-cyan    { border-color: rgba(0,255,255,0.3);    color: var(--cyan);    box-shadow: inset 0 0 20px rgba(0,255,255,0.03);    }
  .cb-magenta { border-color: rgba(255,0,255,0.3);    color: var(--magenta); box-shadow: inset 0 0 20px rgba(255,0,255,0.03);    }
  .cb-green   { border-color: rgba(0,255,65,0.3);     color: var(--green);   box-shadow: inset 0 0 20px rgba(0,255,65,0.03);     }
  .cb-yellow  { border-color: rgba(255,215,0,0.3);    color: var(--yellow);  box-shadow: inset 0 0 20px rgba(255,215,0,0.03);    }
  .cb-red     { border-color: rgba(255,0,64,0.3);     color: var(--red);     box-shadow: inset 0 0 20px rgba(255,0,64,0.03);     }
  .cb-orange  { border-color: rgba(255,102,0,0.3);    color: var(--orange);  box-shadow: inset 0 0 20px rgba(255,102,0,0.03);    }

  pre { white-space: pre-wrap; word-break: break-word; }

  /* ═══════════════════ COLOURED SPANS ═══════════════════ */
  .c  { color: var(--cyan); }
  .m  { color: var(--magenta); }
  .g  { color: var(--green); }
  .y  { color: var(--yellow); }
  .r  { color: var(--red); }
  .o  { color: var(--orange); }
  .w  { color: var(--white); }

  .glow-c { text-shadow: 0 0 8px var(--cyan); }
  .glow-m { text-shadow: 0 0 8px var(--magenta); }
  .glow-g { text-shadow: 0 0 8px var(--green); }
  .glow-y { text-shadow: 0 0 8px var(--yellow); }
  .glow-r { text-shadow: 0 0 8px var(--red); animation: red-glow 1s infinite alternate; }
  @keyframes red-glow {
    from { text-shadow: 0 0 4px var(--red); }
    to   { text-shadow: 0 0 16px var(--red), 0 0 32px rgba(255,0,64,0.5); }
  }

  /* ═══════════════════ STAGE SELECT ═══════════════════ */
  .stage-item {
    display: flex;
    align-items: center;
    padding: 8px 0;
    border-bottom: 1px solid rgba(0,255,255,0.1);
    transition: all 0.2s;
  }
  .stage-item:hover {
    background: rgba(0,255,255,0.05);
    padding-left: 10px;
    border-color: var(--cyan);
  }
  .stage-num { color: var(--cyan); min-width: 80px; font-size: 12px; }
  .stage-name { color: var(--white); flex: 1; }
  .stage-status { color: var(--green); text-shadow: 0 0 8px var(--green); font-size: 13px; }
  .stage-bonus { color: var(--yellow); text-shadow: 0 0 10px var(--yellow); animation: pulse-yellow 2s infinite alternate; }

  /* ═══════════════════ TIER LIST ═══════════════════ */
  .tier-row {
    display: flex;
    align-items: center;
    padding: 10px 0;
    gap: 15px;
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }
  .tier-label {
    font-family: 'Orbitron', monospace;
    font-size: 13px;
    min-width: 70px;
    font-weight: 700;
  }
  .tier-name { color: var(--white); min-width: 180px; }
  .tier-bar { flex: 1; height: 16px; background: rgba(255,255,255,0.05); position: relative; overflow: hidden; border: 1px solid rgba(255,255,255,0.1); }
  .tier-fill { height: 100%; position: relative; animation: fill-in 2s ease-out; }
  @keyframes fill-in { from { width: 0; } }
  .tier-s .tier-fill { background: linear-gradient(90deg, var(--green), var(--cyan)); box-shadow: 0 0 10px var(--green); }
  .tier-b .tier-fill { background: linear-gradient(90deg, var(--yellow), var(--orange)); width: 65%; }
  .tier-f .tier-fill { background: linear-gradient(90deg, var(--red), rgba(255,0,64,0.3)); width: 10%; }
  .tier-x .tier-fill { background: repeating-linear-gradient(45deg, var(--magenta), var(--magenta) 4px, transparent 4px, transparent 8px); width: 50%; animation: tier-x-anim 1s linear infinite; }
  @keyframes tier-x-anim { to { background-position: 24px 0; } }
  .tier-badge { font-family: 'Orbitron', monospace; font-size: 11px; padding: 2px 8px; border: 1px solid; }

  /* ═══════════════════ HALL OF FAME ═══════════════════ */
  .hof-entry {
    padding: 14px;
    margin: 10px 0;
    border: 1px solid;
    position: relative;
    transition: all 0.2s;
  }
  .hof-entry:hover { transform: translateX(5px); }
  .hof-1 { border-color: var(--yellow); background: rgba(255,215,0,0.04); box-shadow: 0 0 15px rgba(255,215,0,0.1); }
  .hof-2 { border-color: rgba(192,192,192,0.5); background: rgba(192,192,192,0.02); box-shadow: 0 0 15px rgba(192,192,192,0.05); }
  .hof-3 { border-color: var(--orange); background: rgba(255,102,0,0.04); box-shadow: 0 0 15px rgba(255,102,0,0.1); }
  .hof-rank { font-family: 'VT323', monospace; font-size: 36px; float: left; margin-right: 15px; line-height: 1; }
  .hof-score { font-family: 'Orbitron', monospace; font-size: 12px; float: right; }
  .hof-title { font-weight: bold; text-transform: uppercase; letter-spacing: 2px; font-size: 13px; }
  .hof-desc { font-size: 12px; opacity: 0.8; margin-top: 4px; }

  /* ═══════════════════ ERROR LOG ═══════════════════ */
  .error-entry {
    padding: 10px 14px;
    margin: 6px 0;
    border-left: 3px solid;
    background: rgba(255,0,64,0.04);
    position: relative;
    overflow: hidden;
  }
  .error-critical { border-color: var(--red); animation: critical-flash 3s infinite; }
  .error-error    { border-color: var(--orange); }
  .error-fatal    { border-color: var(--magenta); animation: fatal-flash 2s infinite; }
  @keyframes critical-flash {
    0%, 90%, 100% { background: rgba(255,0,64,0.04); }
    95% { background: rgba(255,0,64,0.12); }
  }
  @keyframes fatal-flash {
    0%, 80%, 100% { background: rgba(255,0,255,0.04); }
    90% { background: rgba(255,0,255,0.1); }
  }
  .error-tag { font-family: 'Orbitron', monospace; font-size: 10px; padding: 2px 6px; border: 1px solid; margin-right: 10px; }
  .error-lives { float: right; font-size: 12px; opacity: 0.7; }

  /* ═══════════════════ NETWORK ═══════════════════ */
  .network-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  .net-node {
    padding: 15px;
    border: 1px solid;
    text-align: center;
    position: relative;
  }
  .net-label { font-family: 'Orbitron', monospace; font-size: 11px; letter-spacing: 2px; margin-bottom: 8px; }
  .ping-fail { color: var(--red); animation: blink 0.8s step-end infinite; }
  .ping-ok   { color: var(--green); text-shadow: 0 0 10px var(--green); }

  /* ═══════════════════ FINAL COMMIT ═══════════════════ */
  .commit-block {
    border: 2px solid var(--cyan);
    padding: 25px;
    background: rgba(0,255,255,0.03);
    box-shadow: 0 0 30px rgba(0,255,255,0.1), inset 0 0 30px rgba(0,255,255,0.02);
    position: relative;
  }
  .commit-block::before {
    content: 'FINAL SAVE STATE';
    position: absolute;
    top: -10px; left: 20px;
    background: var(--bg);
    padding: 0 10px;
    color: var(--cyan);
    font-family: 'Orbitron', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    text-shadow: 0 0 10px var(--cyan);
  }
  .commit-hash { color: var(--orange); font-size: 13px; }
  .commit-meta { color: rgba(255,255,255,0.5); font-size: 12px; margin: 4px 0 15px; }
  .commit-body { color: var(--white); line-height: 2; }
  .commit-highlight { color: var(--cyan); }
  .commit-tagline { color: var(--magenta); font-size: 15px; margin-top: 15px; text-shadow: 0 0 10px var(--magenta); }

  /* ═══════════════════ GAME OVER FOOTER ═══════════════════ */
  .game-over {
    text-align: center;
    padding: 40px 20px;
    margin-top: 40px;
    border: 2px solid var(--magenta);
    background: rgba(255,0,255,0.03);
    box-shadow: 0 0 40px rgba(255,0,255,0.15), inset 0 0 40px rgba(255,0,255,0.03);
    position: relative;
  }
  .game-over-text {
    font-family: 'VT323', monospace;
    font-size: clamp(60px, 12vw, 120px);
    color: var(--magenta);
    text-shadow: 4px 4px 0 var(--red), 0 0 30px var(--magenta), 0 0 60px rgba(255,0,255,0.5);
    animation: go-glitch 5s infinite;
    display: block;
    line-height: 1;
  }
  @keyframes go-glitch {
    0%, 88%, 100% { transform: none; }
    90% { transform: skew(-3deg) translate(-3px, 0); color: var(--cyan); }
    92% { transform: skew(2deg) translate(3px, 0); color: var(--red); }
    94% { transform: none; color: var(--magenta); }
  }
  .go-japanese {
    font-family: 'VT323', monospace;
    font-size: 32px;
    color: var(--yellow);
    text-shadow: 0 0 20px var(--yellow);
    letter-spacing: 8px;
    margin: 10px 0;
  }
  .shutdown-text {
    font-family: 'Share Tech Mono', monospace;
    font-size: 13px;
    color: rgba(0,255,65,0.7);
    margin-top: 20px;
    line-height: 2;
  }
  .shutdown-cmd {
    color: var(--green);
    font-size: 16px;
    text-shadow: 0 0 10px var(--green);
    margin-top: 15px;
    animation: type-cursor 1s step-end infinite;
  }
  @keyframes type-cursor { 50% { border-right-color: transparent; } }

  /* ═══════════════════ SCROLLBAR ═══════════════════ */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--green); }

  /* ═══════════════════ DIVIDER ═══════════════════ */
  .divider {
    height: 1px;
    margin: 30px 0;
    background: linear-gradient(90deg, transparent, var(--green), var(--cyan), var(--magenta), var(--green), transparent);
    opacity: 0.4;
  }

  /* TYPING ANIMATION */
  .typing { overflow: hidden; white-space: nowrap; animation: typing 3s steps(40, end); }
  @keyframes typing { from { width: 0; } }

  /* ═══════════════════ RESPONSIVE ═══════════════════ */
  @media (max-width: 600px) {
    .network-grid { grid-template-columns: 1fr; }
    .tier-name { min-width: 120px; }
    body { font-size: 12px; }
  }
</style>
</head>
<body>

<canvas id="rain"></canvas>

<div class="wrapper">

  <!-- ══════════ HEADER ══════════ -->
  <div class="header">
    <div class="arcade-title glitch" data-text="GIT CODE.RG">GIT CODE.RG</div>
    <div class="subtitle">⚡ VCETAOA / THIS_REPO — OBITUARY ⚡</div>
    <div class="japanese">ゲームオーバー &nbsp;·&nbsp; コインをいれてください</div>
    <div class="insert-coin">▶ INSERT COIN TO CONTINUE ◀</div>
  </div>

  <!-- ══════════ BADGES ══════════ -->
  <div class="badges">
    <span class="badge badge-green">🟢 UPTIME: 730 DAYS</span>
    <span class="badge badge-cyan">PLAYER 1: GRADUATED</span>
    <span class="badge badge-yellow">HI-SCORE: 9,999,999</span>
    <span class="badge badge-red">CREDITS: 0</span>
    <span class="badge badge-magenta">EXIT CODE: 0</span>
  </div>

  <div class="divider"></div>

  <!-- ══════════ BOOT SEQUENCE ══════════ -->
  <div class="section">
    <div class="section-title title-green">⚡ POWER ON SEQUENCE</div>
    <div class="code-block cb-green">
<pre>
<span class="g">SYSTEM BOOT — <span class="y">21 APR 2081</span> — <span class="c">03.7V NOMINAL</span></span>
<span class="g">████████████████████░░░░░  LOADING...</span>

<span class="c">&gt;&gt;</span> <span class="w">ROM CHECK</span><span class="g">............................ OK ✅</span>
<span class="c">&gt;&gt;</span> <span class="w">RAM TEST</span><span class="g">............................ OK ✅</span>
<span class="c">&gt;&gt;</span> <span class="w">HOTSPOT MODULE</span><span class="g">.................. ONLINE ✅</span>
<span class="c">&gt;&gt;</span> <span class="w">GITHUB UPLINK</span><span class="m">................... LOCKED 🔒</span>
<span class="c">&gt;&gt;</span> <span class="w">TEACHER DETECTION AI</span><span class="r">.............. ARMED 🔴</span>
<span class="c">&gt;&gt;</span> <span class="w">BAG CONCEALMENT PROTOCOL</span><span class="g">........ ACTIVE 👜</span>
<span class="c">&gt;&gt;</span> <span class="w">PRAYER SUBROUTINE</span><span class="g">.............. RUNNING 🙏</span>

<span class="r">[!] ANOMALY: EXAM IN 10 MINUTES</span>
<span class="r">[!] ZERO PREPARATION LOADED INTO MEMORY</span>
<span class="r">[!] INITIATING SURVIVAL MODE...</span>

<span class="y">DATE     :</span> <span class="c">April 21, 2081</span>
<span class="y">LOCATION :</span> <span class="w">college lab. corner seat.</span>
<span class="y">REASON   :</span> <span class="w">exam in 10 mins. zero preparation.</span>
<span class="y">SOLUTION :</span> <span class="m">bag in corner. phone inside. hotspot on.</span>
<span class="y">RESULT   :</span> <span class="g">passed.</span>
<span class="y">DECISION :</span> <span class="c">never delete this repo. ever.</span>

<span class="g">&gt;&gt; LAUNCHING: ./exam_ritual.sh 🚀</span>
</pre>
    </div>
  </div>

  <!-- ══════════ STAGE SELECT ══════════ -->
  <div class="section">
    <div class="section-title title-cyan">🕹️ STAGE SELECT — THE SACRED RITUAL</div>
    <div class="code-block cb-cyan">
      <div style="font-family:'Orbitron',monospace;font-size:11px;color:rgba(0,255,255,0.5);margin-bottom:15px;letter-spacing:2px;">EXAM_RITUAL.EXE  v2.0  ·  PRESS START TO BEGIN</div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 1]</span>
        <span class="stage-name">BAG IN CORNER — WALL SIDE</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 2]</span>
        <span class="stage-name">HOTSPOT: ON — DND: ARMED</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 3]</span>
        <span class="stage-name">WIFI CONNECT — SAY NOTHING</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 4]</span>
        <span class="stage-name">NAVIGATE → vcetaoa/&lt;repo&gt;</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 5]</span>
        <span class="stage-name">COPY → PASTE → EDIT VARIABLES</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 6]</span>
        <span class="stage-name">ALT+TAB WHEN TEACHER APPROACHES</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 7]</span>
        <span class="stage-name">SUBMIT — POKER FACE EQUIPPED</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item">
        <span class="stage-num">[STAGE 8]</span>
        <span class="stage-name">EXIT LIKE A GHOST</span>
        <span class="stage-status">✅ CLEAR</span>
      </div>
      <div class="stage-item" style="border-bottom:none;padding-top:15px;">
        <span class="stage-num" style="color:var(--yellow)">[BONUS]</span>
        <span class="stage-name" style="color:var(--yellow)">"BHAI LINK BHEJ" — 9:58 AM</span>
        <span class="stage-bonus">💎 LEGEND</span>
      </div>
    </div>
  </div>

  <!-- ══════════ TIER LIST ══════════ -->
  <div class="section">
    <div class="section-title title-magenta">👾 BAG PLACEMENT TIER LIST</div>
    <div class="code-block cb-magenta">
      <div class="tier-row">
        <span class="tier-label" style="color:var(--green)">S-TIER</span>
        <span class="tier-name c">CORNER × WALL SIDE</span>
        <div class="tier-bar tier-s"><div class="tier-fill" style="width:100%"></div></div>
        <span class="tier-badge" style="color:var(--green);border-color:var(--green)">✅ SAFE</span>
      </div>
      <div style="font-size:11px;color:rgba(255,255,255,0.4);padding:2px 0 8px 85px;">"safest. classic. 730-day field tested."</div>
      <div class="tier-row">
        <span class="tier-label" style="color:var(--yellow)">B-TIER</span>
        <span class="tier-name y">UNDER YOUR SEAT</span>
        <div class="tier-bar tier-b"><div class="tier-fill" style="width:60%"></div></div>
        <span class="tier-badge" style="color:var(--yellow);border-color:var(--yellow)">⚠️ RISK</span>
      </div>
      <div style="font-size:11px;color:rgba(255,255,255,0.4);padding:2px 0 8px 85px;">"teacher checks here too. risky run."</div>
      <div class="tier-row">
        <span class="tier-label" style="color:var(--red)">F-TIER</span>
        <span class="tier-name r">ON THE TABLE</span>
        <div class="tier-bar tier-f"><div class="tier-fill" style="width:8%"></div></div>
        <span class="tier-badge" style="color:var(--red);border-color:var(--red)">❌ NO</span>
      </div>
      <div style="font-size:11px;color:rgba(255,255,255,0.4);padding:2px 0 8px 85px;">"instant game over. do NOT."</div>
      <div class="tier-row">
        <span class="tier-label" style="color:var(--magenta)">X-TIER</span>
        <span class="tier-name m">SOMEONE ELSE'S BAG</span>
        <div class="tier-bar tier-x"><div class="tier-fill" style="width:50%"></div></div>
        <span class="tier-badge" style="color:var(--magenta);border-color:var(--magenta)">🧠 ???</span>
      </div>
      <div style="font-size:11px;color:rgba(255,255,255,0.4);padding:2px 0 8px 85px;">"galaxy brain. coordinate beforehand."</div>
      <div style="margin-top:15px;padding-top:12px;border-top:1px solid rgba(255,0,255,0.2);font-size:12px;color:var(--magenta);">
        ▶ PRO TIP: DND BEFORE ENTERING. ALWAYS. NO EXCEPTIONS.
      </div>
    </div>
  </div>

  <!-- ══════════ HALL OF FAME ══════════ -->
  <div class="section">
    <div class="section-title title-yellow">🏆 HALL OF FAME — NAME ENTRY</div>
    <div class="code-block cb-yellow">
      <div style="font-family:'VT323',monospace;font-size:28px;color:var(--yellow);text-align:center;letter-spacing:6px;margin-bottom:15px;text-shadow:0 0 15px var(--yellow)">★  H I G H   S C O R E  ★</div>
      <div class="hof-entry hof-1">
        <div class="hof-score y">9,999,999 PTS</div>
        <div class="hof-rank y">🥇</div>
        <div class="hof-title y">THE ONE WITH HOTSPOT IN THE BAG</div>
        <div class="hof-desc w">→ compiler would not run without you. ever.</div>
        <div style="clear:both"></div>
      </div>
      <div class="hof-entry hof-2">
        <div class="hof-score w">8,750,000 PTS</div>
        <div class="hof-rank w">🥈</div>
        <div class="hof-title w">THE ONE WHO SENT LINK BEFORE ENTERING</div>
        <div class="hof-desc" style="color:rgba(255,255,255,0.6)">→ pre-game IQ. senior dev energy.</div>
        <div style="clear:both"></div>
      </div>
      <div class="hof-entry hof-3">
        <div class="hof-score o">7,200,000 PTS</div>
        <div class="hof-rank o">🥉</div>
        <div class="hof-title o">THE ONE WHO SAT NEAR TEACHER</div>
        <div class="hof-desc w">→ distraction specialist. the unsung hero.</div>
        <div style="clear:both"></div>
      </div>
      <div style="text-align:center;margin-top:15px;font-family:'Orbitron',monospace;font-size:11px;color:rgba(255,215,0,0.5);letter-spacing:3px;animation:blink 1s step-end infinite;">▶ PRESS START TO ENTER YOUR INITIALS</div>
    </div>
  </div>

  <!-- ══════════ ERROR LOG ══════════ -->
  <div class="section">
    <div class="section-title title-red">💀 ERROR LOG — CRITICAL FAILURES</div>
    <div class="code-block cb-red">
      <div style="font-family:'VT323',monospace;font-size:40px;color:var(--red);text-align:center;text-shadow:0 0 20px var(--red),0 0 40px rgba(255,0,64,0.4);letter-spacing:10px;margin-bottom:15px;animation:go-glitch 4s infinite;">B U G   R E P O R T</div>
      <div class="error-entry error-critical">
        <span class="error-lives r">LIVES LOST: 1 💀</span>
        <span class="error-tag r" style="border-color:var(--red)">!CRITICAL</span>
        <span class="w">phone rang mid-exam. bag vibrated. teacher turned.</span>
        <br><span style="font-size:11px;color:rgba(255,255,255,0.4);margin-left:80px;">STEALTH BROKEN — NEAR FATAL</span>
      </div>
      <div class="error-entry error-error">
        <span class="error-lives o">STEALTH: -9999 💀</span>
        <span class="error-tag o" style="border-color:var(--orange)">! ERROR</span>
        <span class="w">hotspot SSID was "FBI Surveillance Van"</span>
        <br><span style="font-size:11px;color:rgba(255,255,255,0.4);margin-left:80px;">WHAT WERE YOU THINKING</span>
      </div>
      <div class="error-entry error-error">
        <span class="error-lives o">SHAME: MAX 💀</span>
        <span class="error-tag o" style="border-color:var(--orange)">! ERROR</span>
        <span class="w">copied variable name verbatim. teacher noticed.</span>
      </div>
      <div class="error-entry error-fatal">
        <span class="error-lives m">15 PLAYERS DOWN 💀</span>
        <span class="error-tag m" style="border-color:var(--magenta)">! FATAL</span>
        <span class="w">repo set to PRIVATE on exam day.</span>
        <br><span style="font-size:11px;color:rgba(255,255,255,0.4);margin-left:80px;">MASS DISCONNECT EVENT</span>
      </div>
      <div class="error-entry error-fatal">
        <span class="error-lives m">GAME OVER 💀</span>
        <span class="error-tag m" style="border-color:var(--magenta)">! FATAL</span>
        <span class="w">battery: 2%. hotspot died. mid-copy.</span>
      </div>
      <div style="margin-top:15px;padding-top:12px;border-top:1px solid rgba(255,0,64,0.2);">
        <span class="g">LESSON_LOADED</span> <span class="w">▶ charge to 100%. set PUBLIC. set DND.</span><br>
        <span class="g">APPLIED?     </span> <span class="g">▶ every exam after that. ✅</span>
      </div>
    </div>
  </div>

  <!-- ══════════ NETWORK ══════════ -->
  <div class="section">
    <div class="section-title title-cyan">🌐 NETWORK TRACE — FROM INSIDE THE LAB</div>
    <div class="code-block cb-cyan">
      <div class="network-grid">
        <div>
          <div style="font-size:13px;color:var(--red);margin-bottom:10px;font-family:'Orbitron',monospace;font-size:11px;letter-spacing:2px;">COLLEGE WIFI</div>
          <div class="ping-fail">request timeout...  💀</div>
          <div class="ping-fail" style="animation-delay:0.3s">request timeout...  💀</div>
          <div class="ping-fail" style="animation-delay:0.6s">packet lost...      💀</div>
          <div style="color:var(--red);font-size:12px;margin-top:8px;">BLOCKED. FIREWALLED. USELESS.</div>
        </div>
        <div>
          <div style="font-family:'Orbitron',monospace;font-size:11px;letter-spacing:2px;color:var(--green);margin-bottom:10px;">BAG → 📱 HOTSPOT</div>
          <div class="ping-ok">-- HOTSPOT CONNECTED --</div>
          <div style="margin-top:8px;color:var(--green)">64 bytes from github.com</div>
          <div class="ping-ok">time = 42ms        ✅</div>
          <div class="ping-ok">repo loaded.       ✅</div>
          <div class="ping-ok">we survive again.  ✅</div>
        </div>
      </div>
      <div style="margin-top:15px;padding-top:12px;border-top:1px solid rgba(0,255,255,0.15);font-size:13px;">
        <span class="c">CRON</span> <span class="w">▶ 09:55:00 EVERY EXAM DAY:</span><br>
        <span class="g">pray --hotspot-stable --battery-full --teacher-distracted --github-loads-first-try && pass_the_exam ✅</span>
      </div>
    </div>
  </div>

  <!-- ══════════ FINAL COMMIT ══════════ -->
  <div class="section">
    <div class="section-title title-cyan">📼 FINAL SAVE — LAST COMMIT</div>
    <div class="commit-block">
      <div class="commit-hash">commit  [FINAL_SAVE_STATE_7f3a2b9]</div>
      <div class="commit-meta">author  vcetaoa &lt;survived@college.edu&gt;  ·  Sun Apr 20 2083  ·  23:59:59 +0530</div>
      <div class="commit-meta">msg     last exam. signing off. 🫡</div>
      <div style="height:1px;background:rgba(0,255,255,0.2);margin:15px 0"></div>
      <div class="commit-body">
        two years ago this was a panic decision.<br>
        today it closes as a <span class="commit-highlight">legend.</span><br><br>
        every lab. every exam. <span class="c">every hotspot from the bag.</span><br>
        every <span class="y">"bhai link bhej"</span> at 9:58 AM on whatsapp.<br>
        every <span class="m">alt+tab</span> when teacher walked by.<br>
        every variable renamed so it doesn't look copied.<br><br>
        this repo didn't just store code.<br>
        it stored <span class="y">two years of pure survival.</span><br><br>
        to everyone who used it — <span class="g">tu pass hua.</span><br>
        that's enough. that was <span class="c">always</span> enough.
      </div>
      <div class="commit-tagline">730 days · every semester · bag in corner · 0 caught 🫡</div>
    </div>
  </div>

  <!-- ══════════ GAME OVER FOOTER ══════════ -->
  <div class="game-over">
    <span class="game-over-text">GAME OVER</span>
    <div class="go-japanese">ゲームオーバー</div>
    <div class="shutdown-text">
      MACHINE ID  :  vcetaoa/THIS_REPO<br>
      BOOT DATE   :  April 21, 2081<br>
      SHUTDOWN    :  April 20, 2083<br>
      UPTIME      :  730 days · undefeated · 0 errors · 0 arrests<br>
      この機械は　伝説になった。 — This machine became a legend.
    </div>
    <div style="margin-top:20px;display:flex;flex-wrap:wrap;gap:10px;justify-content:center;">
      <span class="badge badge-yellow">ARCHIVED 🏛️</span>
      <span class="badge badge-cyan">GRADUATED 🎓</span>
      <span class="badge badge-green">FREE 🕊️</span>
    </div>
    <div class="shutdown-cmd">$ shutdown -h now █</div>
    <div style="margin-top:20px;font-size:12px;color:rgba(0,255,65,0.4);font-family:'Share Tech Mono',monospace;letter-spacing:2px;">
      ⭐ STAR THIS REPO — it carried your GPA. least you can do. ⭐
    </div>
  </div>

</div>

<!-- MATRIX RAIN -->
<script>
const canvas = document.getElementById('rain');
const ctx = canvas.getContext('2d');

function resize() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

const chars = 'アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン0123456789ABCDEF<>{}[]|/\\'.split('');
const cols = Math.floor(window.innerWidth / 16);
const drops = Array(cols).fill(1);

const colors = ['#00FF41', '#00FFFF', '#FF00FF', '#FFD700', '#FF0040'];

function draw() {
  ctx.fillStyle = 'rgba(0,0,0,0.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  drops.forEach((y, i) => {
    const char = chars[Math.floor(Math.random() * chars.length)];
    const color = colors[Math.floor(Math.random() * colors.length)];
    ctx.fillStyle = color;
    ctx.font = '14px Share Tech Mono';
    ctx.fillText(char, i * 16, y * 16);

    if (y * 16 > canvas.height && Math.random() > 0.975) drops[i] = 0;
    drops[i]++;
  });
}

setInterval(draw, 50);
</script>

</body>
</html>
