<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>vcetaoa — GAME OVER</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&display=swap');

  :root {
    --green: #00ff41;
    --green-dim: #00aa2a;
    --green-faint: #003311;
    --amber: #ffb000;
    --red: #ff2020;
    --cyan: #00ffff;
    --bg: #050f05;
    --scanline: rgba(0,0,0,0.18);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--green);
    font-family: 'Share Tech Mono', monospace;
    font-size: 14px;
    line-height: 1.6;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* CRT scanlines */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      var(--scanline) 0px,
      var(--scanline) 1px,
      transparent 1px,
      transparent 3px
    );
    pointer-events: none;
    z-index: 999;
  }

  /* CRT flicker */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: radial-gradient(ellipse at center, transparent 60%, rgba(0,0,0,0.5) 100%);
    pointer-events: none;
    z-index: 998;
    animation: flicker 8s infinite;
  }

  @keyframes flicker {
    0%,100% { opacity: 1; }
    92% { opacity: 1; }
    93% { opacity: 0.85; }
    94% { opacity: 1; }
    96% { opacity: 0.9; }
    97% { opacity: 1; }
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 40px 24px 80px;
  }

  /* ─── HEADER ─── */
  .hero {
    border: 1px solid var(--green-dim);
    padding: 32px;
    margin-bottom: 40px;
    position: relative;
    background: linear-gradient(180deg, rgba(0,255,65,0.04) 0%, transparent 100%);
    animation: borderPulse 4s infinite;
  }

  @keyframes borderPulse {
    0%,100% { border-color: var(--green-dim); box-shadow: 0 0 8px rgba(0,255,65,0.1); }
    50% { border-color: var(--green); box-shadow: 0 0 20px rgba(0,255,65,0.25); }
  }

  .hero-label {
    position: absolute;
    top: -10px;
    left: 20px;
    background: var(--bg);
    padding: 0 8px;
    color: var(--green-dim);
    font-size: 11px;
    letter-spacing: 3px;
  }

  .big-title {
    font-family: 'VT323', monospace;
    font-size: clamp(42px, 8vw, 80px);
    color: var(--green);
    text-shadow: 0 0 20px rgba(0,255,65,0.6), 0 0 60px rgba(0,255,65,0.2);
    letter-spacing: 4px;
    animation: textGlitch 6s infinite;
    line-height: 1;
    margin-bottom: 12px;
  }

  @keyframes textGlitch {
    0%,89%,100% { transform: none; text-shadow: 0 0 20px rgba(0,255,65,0.6), 0 0 60px rgba(0,255,65,0.2); }
    90% { transform: translate(-2px,0) skewX(-1deg); text-shadow: -2px 0 #ff2020, 2px 0 var(--cyan); }
    91% { transform: translate(2px,0); }
    92% { transform: none; text-shadow: 0 0 20px rgba(0,255,65,0.6); }
    95% { transform: translate(1px,-1px) skewX(0.5deg); text-shadow: 1px 0 #ff2020; }
    96% { transform: none; text-shadow: 0 0 20px rgba(0,255,65,0.6), 0 0 60px rgba(0,255,65,0.2); }
  }

  .sub {
    color: var(--green-dim);
    font-size: 12px;
    letter-spacing: 2px;
  }

  .sub span { color: var(--amber); }

  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 20px;
  }

  .badge {
    font-family: 'VT323', monospace;
    font-size: 16px;
    padding: 4px 14px;
    border: 1px solid;
    letter-spacing: 1px;
    position: relative;
    overflow: hidden;
  }
  .badge::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0.08;
    background: currentColor;
  }
  .badge-green { color: var(--green); border-color: var(--green); }
  .badge-amber { color: var(--amber); border-color: var(--amber); }
  .badge-red   { color: var(--red);   border-color: var(--red); }
  .badge-cyan  { color: var(--cyan);  border-color: var(--cyan); }

  /* ─── SECTION ─── */
  .section {
    margin-bottom: 36px;
    border-left: 2px solid var(--green-faint);
    padding-left: 20px;
    position: relative;
  }

  .section::before {
    content: '▶';
    position: absolute;
    left: -10px;
    top: 0;
    color: var(--green);
    font-size: 12px;
  }

  .section-title {
    font-family: 'VT323', monospace;
    font-size: 26px;
    color: var(--amber);
    letter-spacing: 3px;
    margin-bottom: 16px;
    text-shadow: 0 0 10px rgba(255,176,0,0.4);
  }

  /* ─── BOOT LOG ─── */
  .boot-log {
    background: rgba(0,255,65,0.03);
    border: 1px solid var(--green-faint);
    padding: 20px;
    margin-bottom: 36px;
  }

  .log-line {
    display: flex;
    align-items: baseline;
    gap: 12px;
    padding: 2px 0;
    font-size: 13px;
  }

  .log-key { color: var(--green-dim); min-width: 240px; }
  .ok   { color: var(--green); }
  .warn { color: var(--amber); }
  .err  { color: var(--red); }
  .blink {
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* ─── TIER LIST ─── */
  .tier-list { display: flex; flex-direction: column; gap: 12px; }

  .tier {
    display: grid;
    grid-template-columns: 80px 1fr auto;
    align-items: center;
    gap: 16px;
    padding: 10px 16px;
    border: 1px solid var(--green-faint);
    background: rgba(0,255,65,0.02);
    transition: background 0.2s;
  }
  .tier:hover { background: rgba(0,255,65,0.06); }

  .tier-label {
    font-family: 'VT323', monospace;
    font-size: 22px;
    text-align: center;
  }
  .s { color: var(--green); }
  .b { color: var(--cyan); }
  .f { color: var(--red); }
  .x { color: var(--amber); }

  .tier-bar {
    height: 6px;
    background: var(--green-faint);
    position: relative;
    overflow: hidden;
  }
  .tier-bar-fill {
    height: 100%;
    position: absolute;
    left: 0;
    animation: fillBar 1.5s ease-out forwards;
  }
  @keyframes fillBar { from { width: 0; } }

  .tier-rank {
    font-family: 'VT323', monospace;
    font-size: 18px;
    white-space: nowrap;
  }

  /* ─── HALL OF FAME ─── */
  .hof { display: flex; flex-direction: column; gap: 8px; }

  .hof-entry {
    display: grid;
    grid-template-columns: 40px 1fr auto;
    align-items: center;
    gap: 14px;
    padding: 12px 16px;
    border: 1px solid var(--green-faint);
    position: relative;
    overflow: hidden;
  }

  .hof-entry::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--green-dim), transparent);
  }

  .hof-rank {
    font-family: 'VT323', monospace;
    font-size: 28px;
    text-align: center;
  }

  .hof-name { font-size: 12px; color: var(--green-dim); }
  .hof-name strong { display: block; color: var(--green); font-size: 13px; margin-bottom: 2px; }
  .hof-score {
    font-family: 'VT323', monospace;
    font-size: 24px;
    color: var(--amber);
    text-shadow: 0 0 8px rgba(255,176,0,0.4);
  }

  /* ─── ERROR LOG ─── */
  .errors { display: flex; flex-direction: column; gap: 6px; }

  .error-line {
    padding: 10px 14px;
    border-left: 3px solid var(--red);
    background: rgba(255,32,32,0.04);
    font-size: 13px;
  }

  .error-tag {
    color: var(--red);
    font-size: 11px;
    letter-spacing: 1px;
    margin-bottom: 2px;
  }

  .error-msg { color: #cc8888; }
  .error-skull { color: var(--red); float: right; font-size: 16px; }

  /* ─── NETWORK ─── */
  .network {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  @media (max-width: 540px) { .network { grid-template-columns: 1fr; } }

  .net-box {
    border: 1px solid var(--green-faint);
    padding: 16px;
  }

  .net-box-title {
    font-family: 'VT323', monospace;
    font-size: 18px;
    letter-spacing: 2px;
    margin-bottom: 10px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--green-faint);
  }

  .net-row { display: flex; justify-content: space-between; font-size: 12px; padding: 3px 0; }
  .net-row span:first-child { color: var(--green-dim); }

  /* ─── FINAL COMMIT ─── */
  .final-commit {
    border: 1px solid var(--green);
    padding: 28px;
    background: rgba(0,255,65,0.03);
    box-shadow: 0 0 30px rgba(0,255,65,0.1), inset 0 0 30px rgba(0,255,65,0.03);
    position: relative;
  }

  .commit-hash {
    font-family: 'VT323', monospace;
    font-size: 15px;
    color: var(--amber);
    margin-bottom: 16px;
    letter-spacing: 2px;
  }

  .commit-body {
    color: #88cc88;
    font-size: 13px;
    line-height: 2;
    border-left: 1px solid var(--green-faint);
    padding-left: 16px;
    margin: 16px 0;
  }

  .commit-body .highlight { color: var(--green); }
  .commit-body .hindi { color: var(--amber); }

  .commit-footer {
    margin-top: 20px;
    padding-top: 16px;
    border-top: 1px solid var(--green-faint);
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    font-size: 12px;
    color: var(--green-dim);
  }

  .commit-footer span { color: var(--green); }

  /* ─── FOOTER ─── */
  .footer {
    margin-top: 60px;
    text-align: center;
    padding: 24px;
    border-top: 1px solid var(--green-faint);
  }

  .game-over {
    font-family: 'VT323', monospace;
    font-size: clamp(48px, 10vw, 90px);
    letter-spacing: 6px;
    color: var(--red);
    text-shadow: 0 0 20px rgba(255,32,32,0.5), 0 0 60px rgba(255,32,32,0.2);
    animation: redFlicker 3s infinite;
    line-height: 1;
    margin-bottom: 8px;
  }

  @keyframes redFlicker {
    0%,100% { opacity: 1; }
    95% { opacity: 1; }
    96% { opacity: 0.7; }
    97% { opacity: 1; }
    98% { opacity: 0.8; }
    99% { opacity: 1; }
  }

  .footer-sub { color: var(--green-dim); font-size: 12px; letter-spacing: 2px; margin-top: 8px; }
  .footer-sub span { color: var(--cyan); }

  .cursor {
    display: inline-block;
    width: 10px; height: 16px;
    background: var(--green);
    vertical-align: middle;
    animation: blink 1s step-end infinite;
    margin-left: 4px;
  }

  /* ─── PROMPT LINE ─── */
  .prompt {
    color: var(--green-dim);
    font-size: 12px;
    margin-top: 4px;
  }
  .prompt::before { content: '$ '; color: var(--green); }

  /* ─── DIVIDER ─── */
  .divider {
    border: none;
    border-top: 1px solid var(--green-faint);
    margin: 8px 0 28px;
  }

  /* ─── CRON ─── */
  .cron { display: flex; flex-direction: column; gap: 6px; }
  .cron-row { display: flex; gap: 16px; font-size: 13px; }
  .cron-task { color: var(--green-dim); min-width: 70px; }
  .cron-cmd { color: var(--cyan); }
</style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="hero">
    <span class="hero-label">// README.md</span>
    <div class="big-title">GIT CODE RG</div>
    <div class="sub">vcetaoa &nbsp;·&nbsp; <span>730 days</span> &nbsp;·&nbsp; <span>0 caught</span> &nbsp;·&nbsp; <span>EXIT CODE: 0</span></div>
    <div class="prompt">navigate to vcetaoa/&lt;repo&gt; → copy → paste → change variable names → submit</div>
    <div class="badges">
      <div class="badge badge-green">▶ PLAYER 1: GRADUATED</div>
      <div class="badge badge-amber">★ HI-SCORE: 9,999,999</div>
      <div class="badge badge-red">CREDITS: 0</div>
      <div class="badge badge-cyan">STATUS: ARCHIVED</div>
    </div>
  </div>

  <!-- BOOT LOG -->
  <div class="section">
    <div class="section-title">⚡ SYSTEM BOOT — EXAM_DAY.SYS</div>
    <div class="boot-log">
      <div class="log-line"><span class="log-key">>> ROM CHECK .....................</span><span class="ok">OK ✓</span></div>
      <div class="log-line"><span class="log-key">>> HOTSPOT MODULE .................</span><span class="ok">ONLINE ✓</span></div>
      <div class="log-line"><span class="log-key">>> GITHUB UPLINK ..................</span><span class="ok">LOCKED AND LOADED ✓</span></div>
      <div class="log-line"><span class="log-key">>> TEACHER DETECTION AI ............</span><span class="warn">ARMED ⚠</span></div>
      <div class="log-line"><span class="log-key">>> BAG CONCEALMENT PROTOCOL ........</span><span class="ok">ACTIVE ✓</span></div>
      <div class="log-line"><span class="log-key">>> DND MODE .........................</span><span class="ok">ENGAGED ✓</span></div>
      <div class="log-line"><span class="log-key">>> PRAYER SUBROUTINE ................</span><span class="ok">RUNNING ✓</span></div>
      <div class="log-line"><span class="log-key">>> ANOMALY: EXAM IN 10 MINUTES .....</span><span class="err">ZERO PREP ✗</span></div>
      <div class="log-line"><span class="log-key">>> INITIATING SURVIVAL MODE ........</span><span class="ok blink">ACTIVE █</span></div>
    </div>
  </div>

  <!-- STAGE SELECT -->
  <div class="section">
    <div class="section-title">🕹 STAGE SELECT — THE RITUAL</div>
    <div style="display:flex;flex-direction:column;gap:6px;">
      <div class="log-line"><span class="log-key">[STAGE 1] BAG IN CORNER — WALL SIDE</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 2] HOTSPOT ON — DND ARMED</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 3] WIFI CONNECT — SAY NOTHING</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 4] NAVIGATE → vcetaoa/&lt;repo&gt;</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 5] COPY → PASTE → EDIT VARS</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 6] ALT+TAB ON TEACHER APPROACH</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 7] SUBMIT — POKER FACE EQUIPPED</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[STAGE 8] EXIT LIKE A GHOST</span><span class="ok">✓ CLEAR</span></div>
      <div class="log-line"><span class="log-key">[BONUS]   "BHAI LINK BHEJ" — 9:58 AM</span><span class="warn">💎 LEGEND</span></div>
    </div>
  </div>

  <!-- TIER LIST -->
  <div class="section">
    <div class="section-title">👜 BAG PLACEMENT TIER LIST</div>
    <div class="tier-list">
      <div class="tier">
        <div class="tier-label s">S</div>
        <div>
          <div style="font-size:13px;margin-bottom:6px;">CORNER × WALL SIDE</div>
          <div class="tier-bar"><div class="tier-bar-fill" style="width:100%;background:var(--green);"></div></div>
          <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">safest. classic. 730-day field tested.</div>
        </div>
        <div class="tier-rank ok">S-TIER ✓</div>
      </div>
      <div class="tier">
        <div class="tier-label b">B</div>
        <div>
          <div style="font-size:13px;margin-bottom:6px;">UNDER YOUR SEAT</div>
          <div class="tier-bar"><div class="tier-bar-fill" style="width:55%;background:var(--cyan);"></div></div>
          <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">teacher checks here too. risky run.</div>
        </div>
        <div class="tier-rank" style="color:var(--cyan);">B-TIER ⚠</div>
      </div>
      <div class="tier">
        <div class="tier-label f">F</div>
        <div>
          <div style="font-size:13px;margin-bottom:6px;">ON THE TABLE</div>
          <div class="tier-bar"><div class="tier-bar-fill" style="width:10%;background:var(--red);"></div></div>
          <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">instant game over. do NOT.</div>
        </div>
        <div class="tier-rank err">F-TIER ✗</div>
      </div>
      <div class="tier">
        <div class="tier-label x">X</div>
        <div>
          <div style="font-size:13px;margin-bottom:6px;">SOMEONE ELSE'S BAG</div>
          <div class="tier-bar"><div class="tier-bar-fill" style="width:75%;background:var(--amber);"></div></div>
          <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">galaxy brain strat. coordinate beforehand.</div>
        </div>
        <div class="tier-rank" style="color:var(--amber);">X-TIER 🧠</div>
      </div>
    </div>
    <div style="margin-top:12px;padding:10px 14px;border:1px solid var(--amber);background:rgba(255,176,0,0.04);font-size:12px;color:var(--amber);">
      ▶ PRO TIP: DND BEFORE ENTERING. ALWAYS. NO EXCEPTIONS.
    </div>
  </div>

  <!-- HALL OF FAME -->
  <div class="section">
    <div class="section-title">🏆 HALL OF FAME — NAME ENTRY</div>
    <div class="hof">
      <div class="hof-entry">
        <div class="hof-rank" style="color:gold;">🥇</div>
        <div class="hof-name">
          <strong>THE ONE WITH HOTSPOT IN THE BAG</strong>
          compiler would not run without you
        </div>
        <div class="hof-score">9,999,999</div>
      </div>
      <div class="hof-entry">
        <div class="hof-rank" style="color:silver;">🥈</div>
        <div class="hof-name">
          <strong>THE ONE WHO SENT LINK BEFORE ENTERING</strong>
          pre-game IQ off the charts
        </div>
        <div class="hof-score">8,750,000</div>
      </div>
      <div class="hof-entry">
        <div class="hof-rank" style="color:#cd7f32;">🥉</div>
        <div class="hof-name">
          <strong>THE ONE WHO SAT NEAR TEACHER</strong>
          distraction specialist. unsung hero
        </div>
        <div class="hof-score">7,200,000</div>
      </div>
    </div>
  </div>

  <!-- ERROR LOG -->
  <div class="section">
    <div class="section-title">💀 ERROR LOG — CRITICAL FAILURES</div>
    <div class="errors">
      <div class="error-line">
        <div class="error-tag">[!CRITICAL]</div>
        <div class="error-msg">phone rang mid-exam. bag vibrated. teacher turned. <span class="error-skull">💀</span></div>
        <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">LIVES LOST: 1</div>
      </div>
      <div class="error-line">
        <div class="error-tag">[! ERROR  ]</div>
        <div class="error-msg">hotspot SSID was "FBI Surveillance Van" <span class="error-skull">💀</span></div>
        <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">STEALTH RATING: -9999</div>
      </div>
      <div class="error-line">
        <div class="error-tag">[! ERROR  ]</div>
        <div class="error-msg">copied variable name verbatim. teacher noticed. <span class="error-skull">💀</span></div>
        <div style="font-size:11px;color:var(--green-dim);margin-top:4px;">SHAME METER: ██████████ MAX</div>
      </div>
      <div class="error-line">
        <div class="error-tag">[! FATAL  ]</div>
        <div class="error-msg">repo set to PRIVATE on exam day. 15 players disconnected. <span class="error-skull">💀</span></div>
      </div>
      <div class="error-line">
        <div class="error-tag">[! FATAL  ]</div>
        <div class="error-msg">battery: 2%. hotspot died. mid-copy. <span class="error-skull">💀</span></div>
      </div>
      <div style="margin-top:10px;padding:10px 14px;border:1px solid var(--green-faint);font-size:12px;color:var(--green-dim);">
        LESSON_LOADED ▶ charge to 100%. set PUBLIC. set DND.<br>
        APPLIED?       ▶ <span class="ok">every exam after that. ✓</span>
      </div>
    </div>
  </div>

  <!-- NETWORK -->
  <div class="section">
    <div class="section-title">🌐 NETWORK TRACE — INSIDE THE LAB</div>
    <div class="network">
      <div class="net-box" style="border-color:var(--red);">
        <div class="net-box-title" style="color:var(--red);">COLLEGE WIFI</div>
        <div class="net-row"><span>ping github.com</span><span class="err">timeout 💀</span></div>
        <div class="net-row"><span>ping github.com</span><span class="err">timeout 💀</span></div>
        <div class="net-row"><span>ping github.com</span><span class="err">timeout 💀</span></div>
        <div class="net-row"><span>teacher nearby</span><span class="err">🚨 ABORT</span></div>
      </div>
      <div class="net-box" style="border-color:var(--green);">
        <div class="net-box-title" style="color:var(--green);">BAG HOTSPOT 📱</div>
        <div class="net-row"><span>ping github.com</span><span class="ok">42ms ✓</span></div>
        <div class="net-row"><span>repo loaded</span><span class="ok">✓</span></div>
        <div class="net-row"><span>copy complete</span><span class="ok">✓</span></div>
        <div class="net-row"><span>we survive again</span><span class="ok">✓</span></div>
      </div>
    </div>
  </div>

  <!-- CRON -->
  <div class="section">
    <div class="section-title">⏰ SACRED SCHEDULE — 09:55 EVERY EXAM</div>
    <div class="cron">
      <div class="cron-row"><span class="cron-task">TASK_1</span><span class="cron-cmd">pray --hotspot-stable</span></div>
      <div class="cron-row"><span class="cron-task">TASK_2</span><span class="cron-cmd">pray --battery-above-80</span></div>
      <div class="cron-row"><span class="cron-task">TASK_3</span><span class="cron-cmd">pray --teacher-distracted</span></div>
      <div class="cron-row"><span class="cron-task">TASK_4</span><span class="cron-cmd">pray --github-loads-first-try</span></div>
      <div class="cron-row"><span class="cron-task">TASK_5</span><span class="cron-cmd">pray --no-one-rats-us-out</span></div>
      <div class="cron-row"><span class="cron-task">ON_TRUE</span><span class="ok">pass_the_exam ✓</span></div>
      <div class="cron-row"><span class="cron-task">ON_FALSE</span><span class="warn">pray harder. try again.</span></div>
      <div class="cron-row" style="margin-top:8px;"><span class="cron-task">STATUS</span><span class="ok">██████████████ PERFECT RECORD</span></div>
    </div>
  </div>

  <!-- FINAL COMMIT -->
  <div class="section">
    <div class="section-title">📼 FINAL COMMIT — LAST SAVE STATE</div>
    <div class="final-commit">
      <div class="commit-hash">
        commit [FINAL_SAVE_STATE]<br>
        author vcetaoa &lt;survived@college.edu&gt;<br>
        date   Sun Apr 20 2083 · 23:59:59 +0530<br>
        msg    last exam. signing off. 🫡
      </div>
      <div class="commit-body">
        two years ago this was a panic decision.<br>
        today it closes as a <span class="highlight">legend.</span><br><br>
        every lab. every exam. <span class="highlight">every hotspot from the bag.</span><br>
        every <span class="hindi">"bhai link bhej"</span> at 9:58 AM on whatsapp.<br>
        every alt+tab when teacher walked by.<br>
        every variable renamed so it doesn't look copied.<br><br>
        this repo didn't just store code.<br>
        it stored <span class="highlight">two years of pure survival.</span><br><br>
        to everyone who used it — <span class="hindi">tu pass hua.</span><br>
        that's enough. that was always enough.
      </div>
      <div class="commit-footer">
        <div>⏱ <span>730 days</span></div>
        <div>📅 <span>every semester</span></div>
        <div>👜 <span>bag in corner</span></div>
        <div>🚨 <span>0 caught</span></div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="game-over">GAME OVER</div>
    <div style="font-family:'VT323',monospace;font-size:20px;color:var(--green);letter-spacing:3px;margin-top:4px;text-shadow:0 0 10px rgba(0,255,65,0.4);">
      [ ARCHIVED ] &nbsp; [ GRADUATED ] &nbsp; [ FREE ]
    </div>
    <div class="footer-sub" style="margin-top:16px;">
      MACHINE ID: vcetaoa/THIS_REPO &nbsp;·&nbsp; UPTIME: <span>730 days</span> &nbsp;·&nbsp; EXIT CODE: <span>0</span>
    </div>
    <div class="footer-sub" style="margin-top:6px;">
      この機械は伝説になった &nbsp;·&nbsp; <span>This machine became a legend.</span>
    </div>
    <div style="margin-top:20px;font-family:'Share Tech Mono',monospace;font-size:13px;color:var(--green-dim);">
      $ shutdown -h now<span class="cursor"></span>
    </div>
    <div style="margin-top:6px;font-family:'VT323',monospace;font-size:18px;color:var(--green);text-shadow:0 0 8px rgba(0,255,65,0.4);">
      >> we made it bhai. we actually made it. 🎓
    </div>
  </div>

</div>
</body>
</html>
