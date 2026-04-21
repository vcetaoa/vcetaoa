<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>VCETAOA.EXE — SYSTEM TERMINATED</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=VT323&display=swap" rel="stylesheet"/>
<style>
:root {
  --neon: #00FF41;
  --neon2: #00FFAA;
  --magenta: #FF00FF;
  --cyan: #00FFFF;
  --yellow: #FFFF00;
  --red: #FF0040;
  --void: #000000;
  --near-void: #020408;
  --grid: rgba(0,255,65,0.06);
  --dim: rgba(0,255,65,0.35);
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--void);
  color: var(--neon);
  font-family: 'Share Tech Mono', monospace;
  overflow-x: hidden;
  cursor: crosshair;
  min-height: 100vh;
}

/* ═══ CRT OVERLAY ═══ */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background:
    repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.15) 2px,
      rgba(0,0,0,0.15) 4px
    );
  pointer-events: none;
  z-index: 9999;
  animation: crt-flicker 0.15s infinite;
}

@keyframes crt-flicker {
  0%,100% { opacity: 1; }
  92% { opacity: 1; }
  93% { opacity: 0.85; }
  94% { opacity: 1; }
}

/* ═══ GRID BACKGROUND ═══ */
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image:
    linear-gradient(var(--grid) 1px, transparent 1px),
    linear-gradient(90deg, var(--grid) 1px, transparent 1px);
  background-size: 40px 40px;
  pointer-events: none;
  z-index: 0;
}

/* ═══ MATRIX CANVAS ═══ */
#matrix {
  position: fixed;
  inset: 0;
  z-index: 0;
  opacity: 0.12;
}

/* ═══ VIGNETTE ═══ */
.vignette {
  position: fixed;
  inset: 0;
  background: radial-gradient(ellipse at center, transparent 40%, rgba(0,0,0,0.85) 100%);
  pointer-events: none;
  z-index: 1;
}

/* ═══ WRAPPER ═══ */
.page {
  position: relative;
  z-index: 2;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 20px 100px;
}

/* ═══ GLITCH TEXT ═══ */
.glitch {
  position: relative;
  display: inline-block;
}
.glitch::before,
.glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
}
.glitch::before {
  color: var(--magenta);
  animation: glitch-before 3s infinite;
  clip-path: polygon(0 0, 100% 0, 100% 45%, 0 45%);
}
.glitch::after {
  color: var(--cyan);
  animation: glitch-after 3s infinite;
  clip-path: polygon(0 55%, 100% 55%, 100% 100%, 0 100%);
}
@keyframes glitch-before {
  0%,90%,100% { transform: translate(0); opacity: 0; }
  91% { transform: translate(-4px, -2px); opacity: 1; }
  93% { transform: translate(4px, 2px); opacity: 1; }
  95% { transform: translate(-3px, 1px); opacity: 0; }
}
@keyframes glitch-after {
  0%,88%,100% { transform: translate(0); opacity: 0; }
  89% { transform: translate(4px, 2px); opacity: 1; }
  91% { transform: translate(-4px, -1px); opacity: 1; }
  93% { transform: translate(2px, -2px); opacity: 0; }
}

/* ═══ HERO ═══ */
.hero {
  text-align: center;
  padding: 60px 0 40px;
  border-bottom: 1px solid var(--dim);
  position: relative;
}

.hero-eyebrow {
  font-family: 'VT323', monospace;
  font-size: 18px;
  color: var(--magenta);
  letter-spacing: 8px;
  text-transform: uppercase;
  margin-bottom: 20px;
  animation: blink-text 3s step-end infinite;
}
@keyframes blink-text {
  0%,100% { opacity: 1; }
  50% { opacity: 0.3; }
}

.hero-title {
  font-family: 'Orbitron', sans-serif;
  font-weight: 900;
  font-size: clamp(40px, 9vw, 90px);
  color: var(--neon);
  letter-spacing: -2px;
  line-height: 0.95;
  text-shadow:
    0 0 10px var(--neon),
    0 0 30px var(--neon),
    0 0 60px rgba(0,255,65,0.4);
  margin-bottom: 6px;
  animation: title-pulse 4s ease-in-out infinite;
}
@keyframes title-pulse {
  0%,100% { text-shadow: 0 0 10px var(--neon), 0 0 30px var(--neon), 0 0 60px rgba(0,255,65,0.4); }
  50% { text-shadow: 0 0 20px var(--neon), 0 0 60px var(--neon), 0 0 100px rgba(0,255,65,0.6), 0 0 150px rgba(0,255,65,0.2); }
}

.hero-sub {
  font-family: 'VT323', monospace;
  font-size: 28px;
  color: var(--cyan);
  letter-spacing: 6px;
  margin: 12px 0 30px;
  text-shadow: 0 0 10px var(--cyan);
}

.status-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  background: var(--dim);
  border: 1px solid var(--dim);
  margin: 28px 0;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}
.status-cell {
  background: var(--void);
  padding: 14px 10px;
  text-align: center;
  transition: background 0.2s;
}
.status-cell:hover { background: rgba(0,255,65,0.05); }
.s-label {
  font-size: 9px;
  letter-spacing: 3px;
  color: var(--dim);
  text-transform: uppercase;
  display: block;
  margin-bottom: 6px;
}
.s-val {
  font-family: 'Orbitron', sans-serif;
  font-size: 13px;
  font-weight: 700;
  color: var(--neon);
  text-shadow: 0 0 8px var(--neon);
}
.s-val.red { color: var(--red); text-shadow: 0 0 8px var(--red); }
.s-val.mag { color: var(--magenta); text-shadow: 0 0 8px var(--magenta); }
.s-val.cyan { color: var(--cyan); text-shadow: 0 0 8px var(--cyan); }

/* ═══ SECTION ═══ */
.section { margin: 56px 0; }

.sec-header {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 20px;
}
.sec-num {
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  color: var(--magenta);
  letter-spacing: 2px;
  opacity: 0.6;
  white-space: nowrap;
}
.sec-title {
  font-family: 'Orbitron', sans-serif;
  font-size: 14px;
  font-weight: 700;
  color: var(--neon);
  letter-spacing: 4px;
  text-transform: uppercase;
  text-shadow: 0 0 12px var(--neon);
}
.sec-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--dim), transparent);
}

/* ═══ TERMINAL BLOCK ═══ */
.term {
  background: rgba(0,255,65,0.02);
  border: 1px solid rgba(0,255,65,0.2);
  border-left: 3px solid var(--neon);
  padding: 24px 28px;
  position: relative;
  overflow: hidden;
  font-size: 13px;
  line-height: 2;
}
.term::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 24px;
  background: rgba(0,255,65,0.05);
  border-bottom: 1px solid rgba(0,255,65,0.15);
}
.term::after {
  content: '● ● ●';
  position: absolute;
  top: 5px; left: 14px;
  font-size: 8px;
  color: var(--dim);
  letter-spacing: 4px;
}
.term pre {
  font-family: 'Share Tech Mono', monospace;
  font-size: 13px;
  line-height: 1.9;
  white-space: pre-wrap;
  word-break: break-word;
  margin-top: 8px;
}

/* COLORS */
.g  { color: var(--neon); }
.m  { color: var(--magenta); }
.c  { color: var(--cyan); }
.y  { color: var(--yellow); }
.r  { color: var(--red); }
.d  { color: rgba(0,255,65,0.35); }
.w  { color: #ffffff; }

/* ═══ PLACEMENT MAP ═══ */
.placement-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.place-card {
  border: 1px solid rgba(0,255,65,0.15);
  padding: 18px 20px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
  cursor: default;
}
.place-card:hover {
  border-color: var(--neon);
  box-shadow: 0 0 20px rgba(0,255,65,0.15), inset 0 0 20px rgba(0,255,65,0.03);
  transform: translateX(4px);
}
.place-card::before {
  content: '';
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 3px;
}
.pc-safe::before   { background: var(--neon); box-shadow: 0 0 8px var(--neon); }
.pc-warn::before   { background: var(--yellow); box-shadow: 0 0 8px var(--yellow); }
.pc-dead::before   { background: var(--red); box-shadow: 0 0 8px var(--red); }
.pc-galaxy::before { background: var(--magenta); box-shadow: 0 0 8px var(--magenta); }

.pc-icon { font-size: 22px; margin-bottom: 8px; display: block; }
.pc-name {
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  letter-spacing: 3px;
  color: var(--dim);
  text-transform: uppercase;
  margin-bottom: 6px;
}
.pc-desc { font-size: 12px; color: rgba(0,255,65,0.7); line-height: 1.5; }

/* ═══ HALL OF FAME ═══ */
.hof-item {
  display: grid;
  grid-template-columns: 60px 1fr;
  gap: 20px;
  align-items: start;
  padding: 20px 0;
  border-bottom: 1px solid rgba(0,255,65,0.08);
  position: relative;
}
.hof-item:last-child { border-bottom: none; }
.hof-item:hover .hof-medal { text-shadow: 0 0 20px currentColor; transform: scale(1.2); }
.hof-medal {
  font-size: 40px;
  text-align: center;
  transition: all 0.3s;
  display: block;
}
.hof-role {
  font-family: 'Orbitron', sans-serif;
  font-size: 10px;
  letter-spacing: 4px;
  color: var(--magenta);
  text-transform: uppercase;
  margin-bottom: 6px;
  text-shadow: 0 0 8px var(--magenta);
}
.hof-title {
  font-family: 'VT323', monospace;
  font-size: 24px;
  color: var(--neon);
  margin-bottom: 6px;
  letter-spacing: 2px;
}
.hof-desc { font-size: 12px; color: var(--dim); line-height: 1.6; }

/* ═══ ERROR LOGS ═══ */
.log-line {
  display: flex;
  gap: 16px;
  padding: 12px 0;
  border-bottom: 1px solid rgba(255,0,64,0.1);
  align-items: flex-start;
  font-size: 12.5px;
  position: relative;
  animation: log-appear 0.3s ease;
}
.log-line:hover { background: rgba(255,0,64,0.03); }
.log-badge {
  font-family: 'Orbitron', sans-serif;
  font-size: 8px;
  font-weight: 700;
  letter-spacing: 1px;
  padding: 3px 8px;
  border-radius: 2px;
  white-space: nowrap;
  margin-top: 2px;
  flex-shrink: 0;
}
.lb-fatal { background: rgba(255,0,64,0.2); color: var(--red); border: 1px solid var(--red); box-shadow: 0 0 6px rgba(255,0,64,0.3); }
.lb-error { background: rgba(255,255,0,0.1); color: var(--yellow); border: 1px solid var(--yellow); }
.lb-crit  { background: rgba(255,0,255,0.1); color: var(--magenta); border: 1px solid var(--magenta); }
.log-text { color: rgba(255,255,255,0.8); line-height: 1.5; }
.log-sub  { display: block; font-size: 11px; color: rgba(0,255,65,0.4); margin-top: 3px; }

/* ═══ PING VISUALIZER ═══ */
.ping-container {
  padding: 20px 0;
  font-family: 'Share Tech Mono', monospace;
}
.ping-attempt {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 5px 0;
  font-size: 13px;
  color: rgba(255,0,64,0.6);
  animation: ping-in 0.5s ease forwards;
  opacity: 0;
}
.ping-attempt:nth-child(1) { animation-delay: 0.1s; }
.ping-attempt:nth-child(2) { animation-delay: 0.6s; }
.ping-attempt:nth-child(3) { animation-delay: 1.1s; }
.ping-success { animation-delay: 1.8s !important; color: var(--neon) !important; }
.ping-success2 { animation-delay: 2.0s !important; color: var(--cyan) !important; }
.ping-success3 { animation-delay: 2.2s !important; color: var(--yellow) !important; }

@keyframes ping-in {
  from { opacity: 0; transform: translateX(-10px); }
  to   { opacity: 1; transform: translateX(0); }
}
.ping-bullet {
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--red);
  box-shadow: 0 0 6px var(--red);
  flex-shrink: 0;
  animation: pulse-dot 1s infinite;
}
.pb-ok { background: var(--neon); box-shadow: 0 0 10px var(--neon); animation: none !important; }

/* ═══ FINAL COMMIT ═══ */
.final {
  border: 1px solid rgba(0,255,65,0.3);
  padding: 48px 36px;
  position: relative;
  overflow: hidden;
  text-align: center;
  margin-top: 60px;
}
.final::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(0,255,65,0.03), transparent 60%, rgba(255,0,255,0.03));
}
.final::after {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--magenta), var(--neon), var(--cyan));
  box-shadow: 0 0 12px var(--neon);
}

.commit-id {
  font-size: 10px;
  letter-spacing: 4px;
  color: var(--dim);
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.commit-id::before, .commit-id::after {
  content: '──────';
  opacity: 0.3;
}

.final-title {
  font-family: 'Orbitron', sans-serif;
  font-weight: 900;
  font-size: clamp(28px, 6vw, 56px);
  color: var(--neon);
  text-shadow: 0 0 20px var(--neon), 0 0 60px rgba(0,255,65,0.3);
  line-height: 1.1;
  margin: 12px 0 28px;
  animation: title-pulse 3s ease-in-out infinite;
}

.log-poem {
  max-width: 560px;
  margin: 0 auto 32px;
  text-align: left;
}
.lp-line {
  display: flex;
  gap: 12px;
  align-items: center;
  padding: 5px 0;
  font-size: 13px;
  color: rgba(0,255,65,0.65);
  border-left: 2px solid transparent;
  padding-left: 12px;
  transition: all 0.2s;
}
.lp-line:hover {
  color: var(--neon);
  border-left-color: var(--neon);
  padding-left: 20px;
  text-shadow: 0 0 8px var(--neon);
}
.lp-arrow { color: var(--magenta); flex-shrink: 0; }

.final-verdict {
  font-family: 'VT323', monospace;
  font-size: 22px;
  color: var(--cyan);
  letter-spacing: 3px;
  line-height: 1.6;
  margin-bottom: 28px;
  text-shadow: 0 0 10px var(--cyan);
  font-style: italic;
}

.eof {
  font-family: 'Orbitron', sans-serif;
  font-weight: 900;
  font-size: 48px;
  letter-spacing: 12px;
  color: var(--neon);
  text-shadow: 0 0 30px var(--neon), 0 0 80px rgba(0,255,65,0.4);
  animation: eof-glitch 5s ease-in-out infinite;
}
@keyframes eof-glitch {
  0%,95%,100% { transform: none; filter: none; }
  96% { transform: translate(3px,-1px); filter: hue-rotate(90deg); }
  97% { transform: translate(-3px,1px); filter: hue-rotate(-90deg); }
  98% { transform: none; filter: none; }
}

/* ═══ FOOTER ═══ */
.footer {
  border-top: 1px solid rgba(0,255,65,0.15);
  padding: 48px 0 32px;
  margin-top: 80px;
  text-align: center;
}

.timeline-bar {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0;
  margin: 0 auto 28px;
  max-width: 500px;
  font-size: 11px;
}
.tl-date {
  font-family: 'Orbitron', sans-serif;
  font-size: 11px;
  color: var(--neon);
  letter-spacing: 2px;
  text-shadow: 0 0 8px var(--neon);
}
.tl-track {
  flex: 1;
  height: 2px;
  background: linear-gradient(90deg, var(--neon), var(--magenta));
  box-shadow: 0 0 8px var(--neon);
  margin: 0 12px;
  position: relative;
}
.tl-track::after {
  content: '730 DAYS';
  position: absolute;
  top: -18px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 9px;
  letter-spacing: 3px;
  color: var(--dim);
  white-space: nowrap;
}

.star-btn {
  display: inline-block;
  border: 1px solid var(--neon);
  padding: 12px 32px;
  font-family: 'Orbitron', sans-serif;
  font-size: 11px;
  letter-spacing: 4px;
  color: var(--neon);
  text-transform: uppercase;
  text-decoration: none;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 0 12px rgba(0,255,65,0.2), inset 0 0 12px rgba(0,255,65,0.03);
}
.star-btn::before {
  content: '';
  position: absolute;
  top: 0; left: -100%;
  width: 100%; height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0,255,65,0.15), transparent);
  animation: btn-shimmer 2s linear infinite;
}
@keyframes btn-shimmer {
  from { left: -100%; }
  to   { left: 100%; }
}
.star-btn:hover {
  background: rgba(0,255,65,0.08);
  box-shadow: 0 0 30px rgba(0,255,65,0.4);
  letter-spacing: 6px;
}

.footer-tagline {
  font-family: 'VT323', monospace;
  font-size: 18px;
  color: rgba(0,255,65,0.3);
  letter-spacing: 4px;
  margin-top: 24px;
}

/* ═══ SHUTDOWN OVERLAY ═══ */
#shutdown {
  position: fixed;
  inset: 0;
  background: var(--void);
  z-index: 99999;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  animation: boot-out 1.5s ease 1.2s forwards;
}
@keyframes boot-out {
  0% { opacity: 1; }
  80% { opacity: 1; }
  100% { opacity: 0; pointer-events: none; }
}
.boot-text {
  font-family: 'VT323', monospace;
  font-size: 20px;
  color: var(--neon);
  letter-spacing: 4px;
  text-align: center;
  line-height: 1.8;
}
.boot-cursor {
  display: inline-block;
  animation: blink 0.5s step-end infinite;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

/* ═══ MISC ═══ */
@keyframes pulse-dot {
  0%,100% { transform: scale(1); opacity: 1; }
  50%      { transform: scale(0.6); opacity: 0.4; }
}

.scan-h {
  position: fixed;
  left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(0,255,65,0.3), transparent);
  pointer-events: none;
  z-index: 9998;
  animation: scan-move 6s linear infinite;
}
@keyframes scan-move {
  0%   { top: 0; }
  100% { top: 100vh; }
}

/* NOISE TEXTURE */
.noise {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9997;
  opacity: 0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  background-size: 200px 200px;
}

/* CORNER DECOR */
.corner-tl, .corner-tr, .corner-bl, .corner-br {
  position: fixed;
  width: 20px; height: 20px;
  border-color: rgba(0,255,65,0.3);
  border-style: solid;
  z-index: 9998;
  pointer-events: none;
}
.corner-tl { top: 12px; left: 12px; border-width: 1px 0 0 1px; }
.corner-tr { top: 12px; right: 12px; border-width: 1px 1px 0 0; }
.corner-bl { bottom: 12px; left: 12px; border-width: 0 0 1px 1px; }
.corner-br { bottom: 12px; right: 12px; border-width: 0 1px 1px 0; }

/* Responsive */
@media (max-width: 600px) {
  .status-grid { grid-template-columns: repeat(2,1fr); }
  .placement-grid { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<!-- BOOT SCREEN -->
<div id="shutdown">
  <div class="boot-text">
    VCETAOA.EXE<br/>
    INITIALIZING...<br/>
    LOADING LEGEND DATA<br/>
    <span class="boot-cursor">█</span>
  </div>
</div>

<!-- EFFECTS -->
<canvas id="matrix"></canvas>
<div class="vignette"></div>
<div class="scan-h"></div>
<div class="noise"></div>
<div class="corner-tl"></div>
<div class="corner-tr"></div>
<div class="corner-bl"></div>
<div class="corner-br"></div>

<div class="page">

<!-- ═══════════ HERO ═══════════ -->
<div class="hero">
  <p class="hero-eyebrow">▶ SYSTEM: VCETAOA.EXE ◀ PROCESS TERMINATED ◀ APR 20 2083</p>
  <h1 class="hero-title glitch" data-text="THE REPO">THE REPO</h1>
  <p class="hero-sub">THE MYTH.&nbsp; THE LEGEND.&nbsp; THE MACHINE.</p>

  <div class="status-grid">
    <div class="status-cell">
      <span class="s-label">uptime</span>
      <span class="s-val">730 DAYS</span>
    </div>
    <div class="status-cell">
      <span class="s-label">exit code</span>
      <span class="s-val">0x00</span>
    </div>
    <div class="status-cell">
      <span class="s-label">status</span>
      <span class="s-val mag">ARCHIVED</span>
    </div>
    <div class="status-cell">
      <span class="s-label">exams</span>
      <span class="s-val cyan">ALL ✓</span>
    </div>
  </div>
</div>

<!-- ═══════════ ORIGIN ═══════════ -->
<div class="section">
  <div class="sec-header">
    <span class="sec-num">// 001</span>
    <span class="sec-title">ORIGIN.TXT</span>
    <span class="sec-line"></span>
  </div>

  <div class="term">
    <pre>
<span class="d">DATE</span>     <span class="d">:</span> <span class="c">April 21, 2081</span>
<span class="d">LOCATION</span> <span class="d">:</span> college lab. corner seat. back row. god mode.
<span class="d">STATUS</span>   <span class="d">:</span> <span class="r">exam in 10 mins.</span> <span class="r">zero preparation.</span> <span class="r">pure panic.</span>
<span class="d">ACTION</span>   <span class="d">:</span> bag → corner. phone → inside. hotspot → <span class="g">ON</span>.
<span class="d">RESULT</span>   <span class="d">:</span> <span class="g">PASSED ✓</span>
<span class="d">DECISION</span> <span class="d">:</span> <span class="m">never. delete. this. repo. ever.</span>

<span class="d">// and that was just day one.</span> <span class="g">🫡</span>
</pre>
  </div>
</div>

<!-- ═══════════ RITUAL ═══════════ -->
<div class="section">
  <div class="sec-header">
    <span class="sec-num">// 002</span>
    <span class="sec-title">EXAM_RITUAL.SH</span>
    <span class="sec-line"></span>
  </div>

  <div class="term">
    <pre>
<span class="d">#!/bin/bash</span>
<span class="d"># THE SACRED PROTOCOL — executed every exam morning, 9:55 AM sharp</span>
<span class="d"># no exceptions. no holidays. no mercy.</span>

<span class="m">bag_corner</span>    --wall-side             <span class="d"># natural. invisible. certified ghost.</span>
<span class="m">phone.hotspot</span> --on --dnd --silent     <span class="d"># silent as death. deadly as results.</span>
<span class="m">wifi.connect</span>  --act-normal            <span class="d"># connect. breathe. say nothing.</span>
<span class="m">github.open</span>   <span class="g">vcetaoa/&lt;repo&gt;</span>         <span class="d"># HOME. this is always home. 🏠</span>
<span class="m">code.copy</span>     --paste --rename-vars   <span class="d"># not blind. SMART. always rename.</span>
<span class="m">submit</span>        --poker-face --walk-up  <span class="d"># act like you wrote it from scratch.</span>
<span class="m">bag.pickup</span>    <span class="d">&&</span> <span class="g">exit 0</span>              <span class="d"># out like a ghost. legend confirmed. 😎</span>

<span class="d"># return code 0 every single time.</span>
<span class="d"># for two years.</span>
<span class="d"># undefeated.</span>
</pre>
  </div>
</div>

<!-- ═══════════ BAG PLACEMENT ═══════════ -->
<div class="section">
  <div class="sec-header">
    <span class="sec-num">// 003</span>
    <span class="sec-title">TACTICAL MAP</span>
    <span class="sec-line"></span>
  </div>

  <div class="placement-grid">
    <div class="place-card pc-safe">
      <span class="pc-icon">✅</span>
      <div class="pc-name">Corner · Wall Side</div>
      <div class="pc-desc">Safest. Classic. 730 days battle-tested. The original spot. The sacred corner. Never failed.</div>
    </div>
    <div class="place-card pc-warn">
      <span class="pc-icon">⚠️</span>
      <div class="pc-name">Under Your Seat</div>
      <div class="pc-desc" style="color:rgba(255,255,0,0.6)">Risky. Teacher checks here too. Proceed with prayer and strong hotspot signal.</div>
    </div>
    <div class="place-card pc-dead">
      <span class="pc-icon">💀</span>
      <div class="pc-name">On The Table</div>
      <div class="pc-desc" style="color:rgba(255,0,64,0.7)">ABSOLUTELY NOT. Immediate execution. No trial. No mercy. Expulsion.exe loading.</div>
    </div>
    <div class="place-card pc-galaxy">
      <span class="pc-icon">🧠</span>
      <div class="pc-name">Someone Else's Bag</div>
      <div class="pc-desc" style="color:rgba(255,0,255,0.7)">Galaxy-brain tier play. Coordinate first. Requires mutual trust and WiFi password.</div>
    </div>
  </div>

  <div class="term" style="margin-top:12px; padding:12px 18px; font-size:12px; border-left-color:var(--yellow);">
    <pre><span class="d">// pro tip:</span> <span class="y">always DND before entering. always charge to 100. always set PUBLIC.</span>
<span class="d">// lesson: learned the hard way. applied: every exam after. ✅</span></pre>
  </div>
</div>

<!-- ═══════════ HALL OF FAME ═══════════ -->
<div class="section">
  <div class="sec-header">
    <span class="sec-num">// 004</span>
    <span class="sec-title">HALL OF FAME</span>
    <span class="sec-line"></span>
  </div>

  <div class="term" style="padding: 12px 28px;">
    <div class="hof-item">
      <span class="hof-medal">🥇</span>
      <div>
        <div class="hof-role">RANK 001 — MVP · THE BACKBONE</div>
        <div class="hof-title">THE HOTSPOT BEARER</div>
        <div class="hof-desc">Ran hotspot silently from inside the bag, every single exam. Without you, nothing compiles. Without you, we are nothing. The silent pillar holding the entire operation. The true, undisputed Dhurandhar.</div>
      </div>
    </div>
    <div class="hof-item">
      <span class="hof-medal">🥈</span>
      <div>
        <div class="hof-role">RANK 002 — STRATEGIST · PRE-GAME IQ</div>
        <div class="hof-title">THE LINK SENDER</div>
        <div class="hof-desc">Sent the GitHub link on WhatsApp at 9:58 AM — before walking into the lab. That 2-minute head start changed everything. Senior developer energy. The planner. The foresight. The clutch.</div>
      </div>
    </div>
    <div class="hof-item">
      <span class="hof-medal">🥉</span>
      <div>
        <div class="hof-role">RANK 003 — DISTRACTION · UNSUNG HERO</div>
        <div class="hof-title">THE DECOY</div>
        <div class="hof-desc">Sat near the teacher. Asked questions. Acted confused. Gave everyone else the cover to work freely. Sacrificed their own comfort for the collective win. The shield. The legend in disguise.</div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════ ERROR LOG ═══════════ -->
<div class="section">
  <div class="sec-header">
    <span class="sec-num">// 005</span>
    <span class="sec-title">ERRORS.LOG</span>
    <span class="sec-line"></span>
  </div>

  <div class="term">
    <div class="log-line">
      <span class="log-badge lb-crit">CRITICAL</span>
      <span class="log-text">Someone's phone rang mid-exam. Bag vibrated. 💀
        <span class="log-sub">→ 15 hearts stopped simultaneously. Teacher looked. Time froze. Somehow survived.</span>
      </span>
    </div>
    <div class="log-line">
      <span class="log-badge lb-error">ERROR</span>
      <span class="log-text">Hotspot name was "FBI Surveillance Van". 💀
        <span class="log-sub">→ Teacher connected by accident. Asked who it belonged to. Silence. Pure silence.</span>
      </span>
    </div>
    <div class="log-line">
      <span class="log-badge lb-error">ERROR</span>
      <span class="log-text">Copy kiya variable name bhi. Teacher noticed. 💀
        <span class="log-sub">→ <code style="color:var(--magenta)">int studentName = 5;</code> appeared in THREE different submissions. Three.</span>
      </span>
    </div>
    <div class="log-line">
      <span class="log-badge lb-fatal">FATAL</span>
      <span class="log-text">Repo was PRIVATE on exam day. 15 people locked out. 💀
        <span class="log-sub">→ The Great Blackout of Semester 3. Never spoken of. Never forgotten. Never repeated.</span>
      </span>
    </div>
    <div class="log-line">
      <span class="log-badge lb-fatal">FATAL</span>
      <span class="log-text">Phone battery: 2%. Hotspot died mid-copy. 💀
        <span class="log-sub">→ Half-written code. Full panic. Found out that day what you actually remembered.</span>
      </span>
    </div>
  </div>
</div>

<!-- ═══════════ PING ═══════════ -->
<div class="section">
  <div class="sec-header">
    <span class="sec-num">// 006</span>
    <span class="sec-title">PING GITHUB.COM</span>
    <span class="sec-line"></span>
  </div>

  <div class="term">
    <pre><span class="d"># from inside enemy territory. lab wifi blocked. bag deployed.</span></pre>
    <div class="ping-container">
      <div class="ping-attempt">
        <div class="ping-bullet"></div>
        PING github.com — <span class="r">request timeout &nbsp;[00001]</span>
      </div>
      <div class="ping-attempt">
        <div class="ping-bullet"></div>
        PING github.com — <span class="r">request timeout &nbsp;[00002]</span>
      </div>
      <div class="ping-attempt">
        <div class="ping-bullet"></div>
        PING github.com — <span class="r">request timeout &nbsp;[00003]</span>
      </div>
      <div class="ping-attempt" style="color:var(--yellow); opacity:0; animation:ping-in 0.5s ease 1.4s forwards;">
        <div class="ping-bullet" style="background:var(--yellow); box-shadow:0 0 8px var(--yellow);"></div>
        <span class="y">--- SWITCHING TO HOTSPOT --- </span>
        <span class="d">bag deployed. phone glows. ⚡</span>
      </div>
      <div class="ping-attempt ping-success">
        <div class="ping-bullet pb-ok"></div>
        <span class="g">64 bytes from github.com: time=42ms &nbsp;&nbsp;&nbsp;✅ REPO LOADED</span>
      </div>
      <div class="ping-attempt ping-success2">
        <div class="ping-bullet pb-ok" style="background:var(--cyan); box-shadow:0 0 10px var(--cyan);"></div>
        <span class="c">code copied. variables renamed. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ ARMED &amp; READY</span>
      </div>
      <div class="ping-attempt ping-success3">
        <div class="ping-bullet pb-ok" style="background:var(--yellow); box-shadow:0 0 10px var(--yellow);"></div>
        <span class="y">we survive again. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✅ LEGEND CONFIRMED</span>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════ FINAL COMMIT ═══════════ -->
<div class="final">
  <div class="commit-id">COMMIT [LAST_COMMIT] · SUN APR 20 2083 · author: vcetaoa</div>
  <div class="final-title glitch" data-text="SIGNING OFF">SIGNING OFF</div>

  <div class="log-poem">
    <div class="lp-line"><span class="lp-arrow">▶</span> two years ago this was a panic decision.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> today it closes as a certified legend.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> every lab. every exam. every hotspot from the bag.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> every "bhai link bhej" on WhatsApp at 9:58 AM.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> every Alt+Tab when the teacher walked by.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> every variable renamed so it doesn't look copied.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> this repo didn't just store code.</div>
    <div class="lp-line"><span class="lp-arrow">▶</span> it stored two years of pure, unfiltered <span style="color:var(--neon)">SURVIVAL</span>.</div>
  </div>

  <p class="final-verdict">
    "to everyone who used it — tu pass hua.<br/>
    that's enough. that was always enough."
  </p>

  <div class="eof">[ EOF ]</div>
</div>

<!-- ═══════════ FOOTER ═══════════ -->
<div class="footer">
  <div class="timeline-bar">
    <span class="tl-date">APR 21 2081</span>
    <div class="tl-track"></div>
    <span class="tl-date">APR 20 2083</span>
  </div>

  <div class="star-btn">⭐ STAR THIS REPO — it carried your GPA. least you can do. ⭐</div>

  <p class="footer-tagline">
    repo: ARCHIVED &nbsp;·&nbsp; status: GRADUATED &nbsp;·&nbsp; $ shutdown -h now
  </p>
</div>

</div><!-- /page -->

<script>
// ═══ MATRIX RAIN ═══
const canvas = document.getElementById('matrix');
const ctx = canvas.getContext('2d');

function resize() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

const chars = 'VCETAOA01GITHUBHOTSPOT悪夢終了合格卒業EXAMPASS'.split('');
const col = 18;
const cols = Math.floor(canvas.width / col);
const drops = Array.from({length: cols}, () => Math.random() * -100);

function draw() {
  ctx.fillStyle = 'rgba(0,0,0,0.06)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  drops.forEach((y, i) => {
    const char = chars[Math.floor(Math.random() * chars.length)];
    const x = i * col;

    // Head char brighter
    ctx.fillStyle = '#FFFFFF';
    ctx.font = `${col - 2}px 'Share Tech Mono'`;
    ctx.fillText(char, x, y * col);

    ctx.fillStyle = 'rgba(0,255,65,0.8)';
    ctx.fillText(chars[Math.floor(Math.random() * chars.length)], x, (y - 1) * col);

    ctx.fillStyle = 'rgba(0,255,65,0.4)';
    ctx.fillText(chars[Math.floor(Math.random() * chars.length)], x, (y - 2) * col);

    if (y * col > canvas.height && Math.random() > 0.975) drops[i] = 0;
    else drops[i] += 0.35;
  });
}

setInterval(draw, 50);
</script>

</body>
</html>
