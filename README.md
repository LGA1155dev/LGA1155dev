<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Gabriel Alves — GitHub Profile Preview</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap');
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    background: #080808;
    font-family: 'Courier New', monospace;
    color: #ccc;
    min-height: 100vh;
    overflow-x: hidden;
  }
  /* Animated background grid */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(247,127,0,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(247,127,0,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }
  .page {
    max-width: 860px;
    margin: 0 auto;
    padding: 30px 20px;
    position: relative;
    z-index: 1;
  }
  /* ── HEADER ── */
  .header {
    text-align: center;
    padding: 50px 30px 40px;
    border: 1px solid rgba(247,127,0,0.3);
    border-radius: 16px;
    background: linear-gradient(135deg, #0a0a0a 0%, #1a0500 50%, #0a0a0a 100%);
    position: relative;
    overflow: hidden;
    margin-bottom: 30px;
  }
  .header::before {
    content: '';
    position: absolute; top: 0; left: -100%;
    width: 100%; height: 3px;
    background: linear-gradient(90deg, transparent, #f77f00, transparent);
    animation: scan 4s linear infinite;
  }
  @keyframes scan { to { left: 200%; } }
  .grid-bg {
    position: absolute; inset: 0;
    background-image: linear-gradient(rgba(247,127,0,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(247,127,0,0.04) 1px, transparent 1px);
    background-size: 30px 30px;
  }
  .corner { position: absolute; width: 20px; height: 20px; }
  .corner::before, .corner::after { content: ''; position: absolute; background: #f77f00; }
  .corner::before { width: 100%; height: 2px; top: 0; }
  .corner::after { width: 2px; height: 100%; top: 0; }
  .corner.tl { top: 12px; left: 12px; }
  .corner.tr { top: 12px; right: 12px; transform: scaleX(-1); }
  .corner.bl { bottom: 12px; left: 12px; transform: scaleY(-1); }
  .corner.br { bottom: 12px; right: 12px; transform: scale(-1,-1); }
  .header-title {
    font-family: 'Courier New', monospace;
    font-size: clamp(36px, 7vw, 64px);
    font-weight: 900;
    background: linear-gradient(90deg, #f77f00, #ff4444, #f77f00);
    background-size: 200%;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: shimmer 3s linear infinite, pulse 3s ease-in-out infinite;
    letter-spacing: 4px;
    position: relative; z-index: 1;
    filter: drop-shadow(0 0 20px rgba(247,127,0,0.4));
    margin-bottom: 16px;
  }
  @keyframes shimmer { to { background-position: 200% center; } }
  @keyframes pulse { 0%,100% { opacity:1; } 50% { opacity:0.85; } }
  .header-sub {
    font-size: 14px;
    letter-spacing: 5px;
    color: #ff6b35;
    margin-bottom: 8px;
    position: relative; z-index: 1;
    text-shadow: 0 0 10px rgba(255,107,53,0.5);
  }
  .header-div {
    width: 300px; height: 1px;
    background: linear-gradient(90deg, transparent, #f77f00, transparent);
    margin: 12px auto;
  }
  .header-sub2 {
    font-size: 12px;
    letter-spacing: 4px;
    color: #ff9500;
    position: relative; z-index: 1;
  }
  .cursor-blink {
    display: inline-block;
    width: 10px; height: 18px;
    background: #f77f00;
    vertical-align: middle;
    margin-left: 6px;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }
  /* ── BADGES ── */
  .badges {
    text-align: center;
    margin-bottom: 30px;
    display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;
  }
  .badge {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 8px 16px;
    background: #1a0500;
    border: 1px solid rgba(247,127,0,0.4);
    border-radius: 6px;
    font-size: 12px;
    letter-spacing: 1px;
    color: #f77f00;
    text-transform: uppercase;
  }
  .badge span { color: #fff; }
  /* ── TERMINAL ── */
  .terminal {
    background: #111;
    border: 1px solid rgba(247,127,0,0.4);
    border-radius: 12px;
    margin-bottom: 30px;
    overflow: hidden;
  }
  .term-bar {
    background: #1a0500;
    padding: 10px 16px;
    display: flex; align-items: center; gap: 8px;
  }
  .dot { width: 13px; height: 13px; border-radius: 50%; }
  .dot.r { background: #ff5f57; }
  .dot.y { background: #ffbd2e; }
  .dot.g { background: #28c840; }
  .term-title { flex: 1; text-align: center; font-size: 12px; color: #666; }
  .term-body { padding: 20px 24px; }
  .term-line { margin: 6px 0; font-size: 14px; line-height: 1.6; }
  .prompt { color: #f77f00; }
  .cmd { color: #fff; }
  .key { color: #ff6b35; display: inline-block; width: 80px; }
  .val { color: #ccc; }
  .val.green { color: #28c840; }
  .val.orange { color: #f77f00; }
  /* ── SECTION TITLES ── */
  .section-title {
    font-size: 18px; font-weight: bold;
    color: #f77f00;
    margin: 30px 0 20px;
    display: flex; align-items: center; gap: 12px;
    letter-spacing: 2px;
  }
  .section-title::after {
    content: '';
    flex: 1; height: 1px;
    background: linear-gradient(90deg, rgba(247,127,0,0.4), transparent);
  }
  /* ── JOURNEY TIMELINE ── */
  .timeline {
    background: #0d0d0d;
    border: 1px solid rgba(247,127,0,0.3);
    border-radius: 12px;
    padding: 30px 24px;
    margin-bottom: 30px;
    position: relative; overflow: hidden;
  }
  .tl-track {
    display: flex; align-items: center;
    position: relative;
    padding: 20px 0 40px;
  }
  .tl-line {
    position: absolute; top: 50%; left: 0; right: 0; height: 2px;
    background: #222;
    transform: translateY(-50%);
    margin-top: -10px;
  }
  .tl-progress {
    position: absolute; top: 50%; left: 0; height: 2px;
    background: linear-gradient(90deg, #f77f00, #ff4444);
    transform: translateY(-50%);
    margin-top: -10px;
    width: 70%;
    animation: progressLoad 2.5s ease-out;
  }
  @keyframes progressLoad { from { width: 0; } }
  .tl-nodes {
    display: flex; justify-content: space-between;
    position: relative; z-index: 2;
    width: 100%;
  }
  .tl-node { text-align: center; display: flex; flex-direction: column; align-items: center; gap: 8px; }
  .node-circle {
    width: 44px; height: 44px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 13px; font-weight: bold;
    border: 2px solid #f77f00;
    background: #1a0500;
    color: #f77f00;
    position: relative;
  }
  .node-circle.active {
    background: #f77f00; color: #000;
    animation: nodePulse 2s ease-in-out infinite;
    box-shadow: 0 0 20px rgba(247,127,0,0.6);
  }
  .node-circle.locked { border-color: #333; color: #444; background: #0d0d0d; }
  @keyframes nodePulse { 0%,100% { box-shadow: 0 0 20px rgba(247,127,0,0.6); } 50% { box-shadow: 0 0 35px rgba(247,127,0,0.9); } }
  .node-year { font-size: 11px; color: #666; }
  .node-name { font-size: 12px; color: #f77f00; font-weight: bold; }
  .node-sub { font-size: 10px; color: #555; }
  .node-status { font-size: 10px; }
  .node-status.done { color: #28c840; }
  .node-status.active { color: #ffbd2e; }
  .node-status.locked { color: #444; }
  /* ── SKILL BARS ── */
  .skills-box {
    background: #0d0d0d;
    border: 1px solid rgba(247,127,0,0.3);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 30px;
  }
  .skills-header {
    text-align: center; letter-spacing: 4px; font-size: 12px;
    color: #f77f00; margin-bottom: 20px;
  }
  .skill-row { margin: 14px 0; }
  .skill-label { display: flex; justify-content: space-between; margin-bottom: 6px; }
  .skill-name { font-size: 13px; color: #ff6b35; }
  .skill-pct { font-size: 11px; color: #f77f00; }
  .skill-track {
    height: 14px; background: #1a1a1a; border-radius: 7px; overflow: hidden;
  }
  .skill-fill {
    height: 100%; border-radius: 7px;
    animation: fillBar 2s ease-out;
    position: relative; overflow: hidden;
  }
  .skill-fill::after {
    content: '';
    position: absolute; top: 0; left: -100%;
    width: 60px; height: 100%;
    background: rgba(255,255,255,0.2);
    transform: skewX(-20deg);
    animation: shine 2.5s ease-in-out infinite;
  }
  @keyframes fillBar { from { width: 0 !important; } }
  @keyframes shine { to { left: 200%; } }
  /* ── PENTEST SECTION ── */
  .pentest-box {
    background: linear-gradient(135deg, #0d0000, #0a0a0a);
    border: 1px solid rgba(204,0,0,0.5);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 30px;
    display: grid;
    grid-template-columns: 200px 1fr;
    gap: 24px;
    align-items: center;
  }
  .dragon-container {
    display: flex; align-items: center; justify-content: center;
  }
  .dragon-svg { filter: drop-shadow(0 0 20px rgba(247,127,0,0.5)); }
  .dragon-aura {
    animation: dragonGlow 3s ease-in-out infinite;
  }
  @keyframes dragonGlow {
    0%,100% { filter: drop-shadow(0 0 20px rgba(247,127,0,0.5)); }
    50% { filter: drop-shadow(0 0 40px rgba(255,68,68,0.8)); }
  }
  .nmap-terminal { font-size: 13px; line-height: 1.8; }
  .nmap-prompt { color: #f77f00; }
  .nmap-cmd { color: #fff; }
  .nmap-open { color: #28c840; }
  .nmap-warn { color: #ff4444; }
  .nmap-info { color: #f77f00; }
  .nmap-note { color: #555; font-style: italic; font-size: 11px; margin-top: 8px; }
  /* ── TECH BADGES ── */
  .tech-badges {
    display: flex; flex-wrap: wrap; gap: 8px;
    justify-content: center;
    margin-bottom: 30px;
  }
  .tech-badge {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 7px 14px;
    border-radius: 6px;
    font-size: 12px; font-weight: bold;
    letter-spacing: 0.5px;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: default;
  }
  .tech-badge:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(247,127,0,0.3);
  }
  .tb-html { background: #f77f00; color: #fff; }
  .tb-css  { background: #2965f1; color: #fff; }
  .tb-js   { background: #F7DF1E; color: #000; }
  .tb-java { background: #e76f00; color: #fff; }
  .tb-spring { background: #6DB33F; color: #fff; }
  .tb-kali { background: #1a1a2e; color: #268BEE; border: 1px solid #268BEE; }
  .tb-linux { background: #FCC624; color: #000; }
  .tb-git  { background: #F05032; color: #fff; }
  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 28px;
    border: 1px solid rgba(247,127,0,0.2);
    border-radius: 12px;
    background: linear-gradient(90deg, #0d0d0d, #1a0500, #2a0800, #1a0500, #0d0d0d);
    position: relative; overflow: hidden;
    margin-top: 10px;
  }
  .footer::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, #f77f00, transparent);
    animation: borderPulse 2s ease-in-out infinite;
  }
  @keyframes borderPulse { 50% { opacity: 0.4; } }
  .footer-title {
    font-size: 20px; letter-spacing: 10px;
    color: #f77f00; margin-bottom: 10px;
    text-shadow: 0 0 20px rgba(247,127,0,0.5);
  }
  .footer-quote { font-size: 12px; color: #555; font-style: italic; }
  /* Particles */
  .particles { position: fixed; inset: 0; pointer-events: none; z-index: 0; overflow: hidden; }
  .particle {
    position: absolute;
    width: 2px; height: 2px;
    background: #f77f00;
    border-radius: 50%;
    opacity: 0;
    animation: float linear infinite;
  }
  @keyframes float {
    0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
    10% { opacity: 0.6; }
    90% { opacity: 0.4; }
    100% { transform: translateY(-20px) rotate(720deg); opacity: 0; }
  }
  hr { border: none; border-top: 1px solid rgba(247,127,0,0.15); margin: 24px 0; }
</style>
</head>
<body>

<!-- Floating particles -->
<div class="particles" id="particles"></div>

<div class="page">

  <!-- ═══ HEADER ═══ -->
  <div class="header">
    <div class="grid-bg"></div>
    <div class="corner tl"></div><div class="corner tr"></div>
    <div class="corner bl"></div><div class="corner br"></div>
    <div class="header-title">GABRIEL ALVES</div>
    <div class="header-sub">☕ &nbsp; BACKEND JAVA DEVELOPER</div>
    <div class="header-div"></div>
    <div class="header-sub2">🐉 &nbsp; FUTURE PENTESTER &nbsp;·&nbsp; ETHICAL HACKER<span class="cursor-blink"></span></div>
  </div>

  <!-- ═══ BADGES ═══ -->
  <div class="badges">
    <div class="badge">STATUS <span>LEVELING UP ⚡</span></div>
    <div class="badge">FOCUS <span>Java + Pentest</span></div>
    <div class="badge">OS <span>Kali Linux 🐉</span></div>
    <div class="badge">MODE <span>🔓 Hacker</span></div>
  </div>

  <!-- ═══ TERMINAL WHOAMI ═══ -->
  <div class="terminal">
    <div class="term-bar">
      <div class="dot r"></div><div class="dot y"></div><div class="dot g"></div>
      <div class="term-title">gabriel@kali: ~</div>
    </div>
    <div class="term-body">
      <div class="term-line"><span class="prompt">$ </span><span class="cmd">whoami</span></div>
      <div class="term-line" style="margin-top:12px">
        <span class="key">NAME</span><span style="color:#555">→ </span><span class="val">Gabriel Alves</span>
      </div>
      <div class="term-line">
        <span class="key">ROLE</span><span style="color:#555">→ </span><span class="val">Java Backend Developer | Future Pentester</span>
      </div>
      <div class="term-line">
        <span class="key">OS</span><span style="color:#555">→ </span><span class="val">Kali Linux (main) · Windows (legacy)</span>
      </div>
      <div class="term-line">
        <span class="key">FOCUS</span><span style="color:#555">→ </span><span class="val">APIs · Spring Boot · Ethical Hacking</span>
      </div>
      <div class="term-line">
        <span class="key">STATUS</span><span style="color:#555">→ </span>
        <span class="val green">████████████</span><span style="color:#333">░░░░░  </span>
        <span class="val orange">Evoluindo...</span>
      </div>
      <div class="term-line" style="margin-top:14px; opacity:0.6; font-size:12px; font-style:italic; color:#555">
        "Primeiro aprendo a construir sistemas. Depois aprendo a quebrá-los."
      </div>
      <div class="term-line" style="margin-top:10px"><span class="prompt">$ <span style="color:#fff">_</span></span><span class="cursor-blink" style="width:8px;height:14px;margin-left:2px"></span></div>
    </div>
  </div>

  <!-- ═══ JOURNEY ═══ -->
  <div class="section-title">🚀 &nbsp; JORNADA</div>
  <div class="timeline">
    <div class="tl-track">
      <div class="tl-line"></div>
      <div class="tl-progress"></div>
      <div class="tl-nodes">
        <div class="tl-node">
          <div class="node-status done">✓ DONE</div>
          <div class="node-circle">01</div>
          <div class="node-year">2020</div>
          <div class="node-name">Frontend</div>
          <div class="node-sub">HTML · CSS · JS</div>
        </div>
        <div class="tl-node">
          <div class="node-status active">⚡ ACTIVE</div>
          <div class="node-circle">02</div>
          <div class="node-year">2023</div>
          <div class="node-name">Backend</div>
          <div class="node-sub">Java · APIs</div>
        </div>
        <div class="tl-node">
          <div class="node-status active">● NOW</div>
          <div class="node-circle active">03</div>
          <div class="node-year">2024</div>
          <div class="node-name">Kali Linux</div>
          <div class="node-sub">Pentest</div>
        </div>
        <div class="tl-node">
          <div class="node-status locked">[ LOCKED ]</div>
          <div class="node-circle locked">04</div>
          <div class="node-year">????</div>
          <div class="node-name" style="color:#444">Pro</div>
          <div class="node-sub">Pentester</div>
        </div>
      </div>
    </div>
  </div>

  <!-- ═══ SKILL BARS ═══ -->
  <div class="section-title">⚙️ &nbsp; SKILL MATRIX</div>
  <div class="skills-box">
    <div class="skills-header">/ / ARSENAL TÉCNICO / /</div>

    <div class="skill-row">
      <div class="skill-label"><span class="skill-name">HTML5</span><span class="skill-pct">90%</span></div>
      <div class="skill-track"><div class="skill-fill" style="width:90%;background:linear-gradient(90deg,#f77f00,#ff9500)"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-label"><span class="skill-name">CSS3</span><span class="skill-pct">85%</span></div>
      <div class="skill-track"><div class="skill-fill" style="width:85%;background:linear-gradient(90deg,#f77f00,#ff9500)"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-label"><span class="skill-name">JavaScript</span><span class="skill-pct">70%</span></div>
      <div class="skill-track"><div class="skill-fill" style="width:70%;background:linear-gradient(90deg,#ff9500,#ffb347)"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-label"><span class="skill-name">Java</span><span class="skill-pct">60%</span></div>
      <div class="skill-track"><div class="skill-fill" style="width:60%;background:linear-gradient(90deg,#ff4444,#f77f00)"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-label"><span class="skill-name">Kali Linux</span><span class="skill-pct">40%</span></div>
      <div class="skill-track"><div class="skill-fill" style="width:40%;background:linear-gradient(90deg,#cc3300,#ff4444)"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-label"><span class="skill-name">Pentest</span><span class="skill-pct">30%</span></div>
      <div class="skill-track"><div class="skill-fill" style="width:30%;background:linear-gradient(90deg,#8b0000,#cc0000)"></div></div>
    </div>
  </div>

  <!-- ═══ TECH BADGES ═══ -->
  <div class="tech-badges">
    <span class="tech-badge tb-html">⬜ HTML5</span>
    <span class="tech-badge tb-css">🔷 CSS3</span>
    <span class="tech-badge tb-js">⭐ JavaScript</span>
    <span class="tech-badge tb-java">☕ Java</span>
    <span class="tech-badge tb-spring">🍃 Spring Boot</span>
    <span class="tech-badge tb-kali">🐉 Kali Linux</span>
    <span class="tech-badge tb-linux">🐧 Linux</span>
    <span class="tech-badge tb-git">🔧 Git</span>
  </div>

  <!-- ═══ PENTEST SECTION ═══ -->
  <div class="section-title">🐉 &nbsp; PENTEST &amp; SEGURANÇA</div>
  <div class="pentest-box">
    <div class="dragon-container">
      <svg class="dragon-svg dragon-aura" width="180" height="200" viewBox="0 0 180 200" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="dragonAura" cx="50%" cy="50%" r="50%">
            <stop offset="0%" style="stop-color:#f77f00;stop-opacity:0.15"/>
            <stop offset="100%" style="stop-color:#f77f00;stop-opacity:0"/>
          </radialGradient>
        </defs>
        <!-- Aura -->
        <ellipse cx="90" cy="105" rx="75" ry="85" fill="url(#dragonAura)">
          <animate attributeName="rx" values="75;85;75" dur="3s" repeatCount="indefinite"/>
          <animate attributeName="ry" values="85;95;85" dur="3s" repeatCount="indefinite"/>
        </ellipse>
        <!-- Wings -->
        <path d="M85,75 L15,25 L55,80 L10,95 L65,105 Z" fill="#1a0000" stroke="#f77f00" stroke-width="1.8" opacity="0.85"/>
        <path d="M95,75 L165,25 L125,80 L170,95 L115,105 Z" fill="#1a0000" stroke="#f77f00" stroke-width="1.8" opacity="0.85"/>
        <!-- Wing veins -->
        <path d="M85,75 L30,40" stroke="#f77f00" stroke-width="0.8" opacity="0.4"/>
        <path d="M75,85 L20,60" stroke="#f77f00" stroke-width="0.6" opacity="0.3"/>
        <path d="M95,75 L150,40" stroke="#f77f00" stroke-width="0.8" opacity="0.4"/>
        <path d="M105,85 L160,60" stroke="#f77f00" stroke-width="0.6" opacity="0.3"/>
        <!-- Body -->
        <ellipse cx="90" cy="125" rx="32" ry="45" fill="#1a0000" stroke="#f77f00" stroke-width="2"/>
        <!-- Scale pattern -->
        <path d="M68,115 Q90,108 112,115" stroke="#f77f00" stroke-width="1" fill="none" opacity="0.4"/>
        <path d="M66,127 Q90,120 114,127" stroke="#f77f00" stroke-width="1" fill="none" opacity="0.4"/>
        <path d="M68,139 Q90,132 112,139" stroke="#f77f00" stroke-width="1" fill="none" opacity="0.4"/>
        <path d="M70,151 Q90,144 110,151" stroke="#f77f00" stroke-width="0.8" fill="none" opacity="0.3"/>
        <!-- Neck -->
        <path d="M75,82 Q80,70 90,65 Q100,70 105,82" fill="#1a0000" stroke="#f77f00" stroke-width="1.5"/>
        <!-- Head -->
        <ellipse cx="90" cy="55" rx="30" ry="27" fill="#200000" stroke="#f77f00" stroke-width="2.2"/>
        <!-- Snout -->
        <path d="M72,65 Q90,80 108,65" fill="#1a0000" stroke="#f77f00" stroke-width="1.5"/>
        <!-- Eyes -->
        <ellipse cx="78" cy="50" rx="9" ry="8" fill="#f77f00"/>
        <ellipse cx="102" cy="50" rx="9" ry="8" fill="#f77f00"/>
        <circle cx="78" cy="50" r="4.5" fill="#cc0000">
          <animate attributeName="opacity" values="1;0.4;1" dur="2.5s" repeatCount="indefinite"/>
        </circle>
        <circle cx="102" cy="50" r="4.5" fill="#cc0000">
          <animate attributeName="opacity" values="1;0.4;1" dur="2.5s" repeatCount="indefinite"/>
        </circle>
        <!-- Eye glow -->
        <circle cx="78" cy="50" r="11" fill="none" stroke="#f77f00" stroke-width="1" opacity="0.3">
          <animate attributeName="r" values="11;14;11" dur="2.5s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0.3;0.6;0.3" dur="2.5s" repeatCount="indefinite"/>
        </circle>
        <circle cx="102" cy="50" r="11" fill="none" stroke="#f77f00" stroke-width="1" opacity="0.3">
          <animate attributeName="r" values="11;14;11" dur="2.5s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0.3;0.6;0.3" dur="2.5s" repeatCount="indefinite"/>
        </circle>
        <!-- Horns -->
        <path d="M76,32 L62,5 L80,28" fill="#f77f00" stroke="#ff4444" stroke-width="1.2"/>
        <path d="M104,32 L118,5 L100,28" fill="#f77f00" stroke="#ff4444" stroke-width="1.2"/>
        <!-- Horn glow -->
        <line x1="65" y1="8" x2="80" y2="28" stroke="#ff4444" stroke-width="0.5" opacity="0.5"/>
        <line x1="115" y1="8" x2="100" y2="28" stroke="#ff4444" stroke-width="0.5" opacity="0.5"/>
        <!-- Nostrils -->
        <circle cx="82" cy="67" r="2.5" fill="#300000"/>
        <circle cx="98" cy="67" r="2.5" fill="#300000"/>
        <!-- Fangs -->
        <path d="M81,73 L78,83" stroke="#ddd" stroke-width="2" stroke-linecap="round"/>
        <path d="M99,73 L102,83" stroke="#ddd" stroke-width="2" stroke-linecap="round"/>
        <!-- Tail -->
        <path d="M90,168 Q105,178 92,188 Q118,183 114,195" stroke="#f77f00" stroke-width="2" fill="none"/>
        <!-- Flame breath hint -->
        <path d="M85,78 Q78,88 65,92 Q72,89 68,98" stroke="#f77f00" stroke-width="1" fill="none" opacity="0.4">
          <animate attributeName="opacity" values="0.4;0.1;0.4" dur="1.5s" repeatCount="indefinite"/>
        </path>
      </svg>
    </div>
    <div class="nmap-terminal">
      <div><span class="nmap-prompt">┌─[gabriel@kali]─[~]</span></div>
      <div><span class="nmap-prompt">└─$ </span><span class="nmap-cmd">nmap -sV --script=vuln target.io</span></div>
      <div style="color:#666;margin-top:6px">Starting Nmap 7.94...</div>
      <div class="nmap-open">[+] 22/tcp   open  ssh</div>
      <div class="nmap-open">[+] 80/tcp   open  http</div>
      <div class="nmap-open">[+] 443/tcp  open  https</div>
      <div class="nmap-warn">[!] CVE-2024-XXXX detected</div>
      <div class="nmap-info">[*] Learning in progress...</div>
      <div class="nmap-note" style="margin-top:12px">Explorando vulnerabilidades com ética.</div>
      <div class="nmap-note">Construindo o caminho: Pentester Profissional.</div>
    </div>
  </div>

  <!-- ═══ FOOTER ═══ -->
  <div class="footer">
    <div class="footer-title">CODE · HACK · EVOLVE</div>
    <div class="footer-quote">"Primeiro aprendo a construir sistemas. Depois aprendo a quebrá-los."</div>
  </div>

</div>

<script>
  // Floating particles
  const container = document.getElementById('particles');
  for (let i = 0; i < 25; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    p.style.cssText = `
      left: ${Math.random()*100}%;
      width: ${Math.random()*3+1}px;
      height: ${Math.random()*3+1}px;
      animation-duration: ${Math.random()*15+10}s;
      animation-delay: ${Math.random()*15}s;
      opacity: ${Math.random()*0.4};
    `;
    container.appendChild(p);
  }
</script>
</body>
</html>
