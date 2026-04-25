<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Anas Jamal — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700&family=Outfit:wght@300;400;600;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0d14;
    --bg2: #0f1320;
    --bg3: #141926;
    --purple: #7c5cfc;
    --purple-light: #a78bfa;
    --purple-dim: #4c3494;
    --blue: #3b82f6;
    --blue-light: #60a5fa;
    --cyan: #22d3ee;
    --teal: #14b8a6;
    --green: #22c55e;
    --green-dim: #166534;
    --pink: #e879f9;
    --text: #e2e8f0;
    --text-muted: #94a3b8;
    --border: rgba(124,92,252,0.18);
  }

  html, body {
    min-height: 100vh;
    background: var(--bg);
    color: var(--text);
    font-family: 'Outfit', sans-serif;
    overflow-x: hidden;
  }

  /* === CANVAS BG === */
  #bg-canvas {
    position: fixed;
    inset: 0;
    z-index: 0;
    pointer-events: none;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 48px 24px 80px;
  }

  /* === HERO === */
  .hero {
    text-align: center;
    margin-bottom: 56px;
    animation: fadeUp 0.8s ease both;
  }

  .avatar-ring {
    display: inline-block;
    margin-bottom: 20px;
    position: relative;
  }

  .avatar-ring::before {
    content: '';
    position: absolute;
    inset: -4px;
    border-radius: 50%;
    background: conic-gradient(from 0deg, var(--purple), var(--cyan), var(--green), var(--pink), var(--purple));
    animation: spin 4s linear infinite;
    z-index: -1;
  }

  .avatar-inner {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--purple-dim), var(--bg3));
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 36px;
    font-weight: 700;
    color: var(--purple-light);
    border: 3px solid var(--bg);
    position: relative;
    z-index: 1;
  }

  .hero h1 {
    font-size: clamp(28px, 5vw, 44px);
    font-weight: 800;
    background: linear-gradient(90deg, var(--purple-light), var(--cyan), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1.1;
    margin-bottom: 8px;
  }

  .hero .subtitle {
    font-size: 15px;
    color: var(--text-muted);
    font-weight: 400;
    margin-bottom: 16px;
    font-family: 'JetBrains Mono', monospace;
  }

  /* === TYPING === */
  .typing-wrapper {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 20px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 14px;
    color: var(--cyan);
    margin-bottom: 24px;
  }

  .prompt { color: var(--purple-light); margin-right: 4px; }

  .typed-text { color: var(--green); min-width: 260px; text-align: left; }

  .cursor {
    display: inline-block;
    width: 2px;
    height: 16px;
    background: var(--cyan);
    animation: blink 0.8s step-end infinite;
    vertical-align: middle;
  }

  /* === BADGES === */
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-bottom: 8px;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 5px 14px;
    border-radius: 20px;
    font-size: 12px;
    font-weight: 600;
    border: 1px solid;
    animation: fadeUp 0.6s ease both;
    letter-spacing: 0.3px;
  }

  .badge-purple { background: rgba(124,92,252,0.12); border-color: rgba(124,92,252,0.4); color: var(--purple-light); }
  .badge-blue   { background: rgba(59,130,246,0.12); border-color: rgba(59,130,246,0.4); color: var(--blue-light); }
  .badge-cyan   { background: rgba(34,211,238,0.12); border-color: rgba(34,211,238,0.4); color: var(--cyan); }
  .badge-green  { background: rgba(34,197,94,0.12);  border-color: rgba(34,197,94,0.4);  color: var(--green); }

  /* === SECTION TITLE === */
  .section-title {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 18px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* === SKILL GRID === */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 16px;
    margin-bottom: 40px;
  }

  .skill-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    position: relative;
    overflow: hidden;
    transition: transform 0.25s ease, border-color 0.25s ease, box-shadow 0.25s ease;
    animation: fadeUp 0.6s ease both;
    cursor: default;
  }

  .skill-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    border-radius: 12px 12px 0 0;
    opacity: 0.8;
    transition: opacity 0.3s;
  }

  .skill-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(0,0,0,0.5);
  }

  .skill-card:hover::before { opacity: 1; }

  .card-purple::before { background: linear-gradient(90deg, var(--purple), var(--pink)); }
  .card-blue::before   { background: linear-gradient(90deg, var(--blue), var(--cyan)); }
  .card-teal::before   { background: linear-gradient(90deg, var(--teal), var(--green)); }
  .card-green::before  { background: linear-gradient(90deg, var(--green), var(--cyan)); }
  .card-pink::before   { background: linear-gradient(90deg, var(--pink), var(--purple)); }

  .card-purple:hover { border-color: rgba(124,92,252,0.4); box-shadow: 0 16px 40px rgba(124,92,252,0.15); }
  .card-blue:hover   { border-color: rgba(59,130,246,0.4); box-shadow: 0 16px 40px rgba(59,130,246,0.15); }
  .card-teal:hover   { border-color: rgba(20,184,166,0.4); box-shadow: 0 16px 40px rgba(20,184,166,0.15); }
  .card-green:hover  { border-color: rgba(34,197,94,0.4);  box-shadow: 0 16px 40px rgba(34,197,94,0.15); }
  .card-pink:hover   { border-color: rgba(232,121,249,0.4); box-shadow: 0 16px 40px rgba(232,121,249,0.15); }

  .card-icon {
    font-size: 28px;
    margin-bottom: 10px;
    display: block;
    filter: drop-shadow(0 0 8px currentColor);
  }

  .card-title {
    font-size: 16px;
    font-weight: 700;
    margin-bottom: 6px;
  }

  .card-purple .card-title { color: var(--purple-light); }
  .card-blue   .card-title { color: var(--blue-light); }
  .card-teal   .card-title { color: var(--teal); }
  .card-green  .card-title { color: var(--green); }
  .card-pink   .card-title { color: var(--pink); }

  .card-desc {
    font-size: 12px;
    color: var(--text-muted);
    line-height: 1.6;
    margin-bottom: 14px;
  }

  .card-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
  }

  .tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    padding: 2px 8px;
    border-radius: 4px;
    background: rgba(255,255,255,0.05);
    color: var(--text-muted);
    border: 1px solid rgba(255,255,255,0.07);
  }

  /* === PROGRESS BARS === */
  .progress-section {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 40px;
    animation: fadeUp 0.7s ease 0.3s both;
  }

  .progress-item {
    margin-bottom: 18px;
  }

  .progress-item:last-child { margin-bottom: 0; }

  .progress-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 7px;
  }

  .progress-label {
    font-size: 13px;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .progress-pct {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
  }

  .progress-track {
    height: 6px;
    background: rgba(255,255,255,0.06);
    border-radius: 10px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    border-radius: 10px;
    width: 0%;
    transition: width 1.4s cubic-bezier(0.4,0,0.2,1);
  }

  .fill-purple { background: linear-gradient(90deg, var(--purple-dim), var(--purple-light)); }
  .fill-blue   { background: linear-gradient(90deg, var(--blue), var(--cyan)); }
  .fill-teal   { background: linear-gradient(90deg, var(--teal), var(--green)); }
  .fill-green  { background: linear-gradient(90deg, #166534, var(--green)); }
  .fill-pink   { background: linear-gradient(90deg, var(--purple), var(--pink)); }

  /* === STATS ROW === */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 14px;
    margin-bottom: 40px;
    animation: fadeUp 0.7s ease 0.4s both;
  }

  .stat-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px 16px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .stat-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 30px rgba(0,0,0,0.4);
  }

  .stat-value {
    font-family: 'JetBrains Mono', monospace;
    font-size: 26px;
    font-weight: 700;
    display: block;
    margin-bottom: 4px;
  }

  .stat-label {
    font-size: 11px;
    color: var(--text-muted);
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 0.8px;
  }

  .stat-glow {
    position: absolute;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    filter: blur(30px);
    opacity: 0.25;
    top: -10px;
    right: -10px;
    pointer-events: none;
  }

  /* === LANG ORBS === */
  .langs-section {
    margin-bottom: 40px;
    animation: fadeUp 0.7s ease 0.5s both;
  }

  .langs-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .lang-pill {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border-radius: 40px;
    border: 1px solid;
    font-size: 13px;
    font-weight: 600;
    font-family: 'JetBrains Mono', monospace;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: default;
  }

  .lang-pill:hover {
    transform: scale(1.06);
  }

  .lang-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  /* === CURRENTLY INTO === */
  .currently-section {
    background: linear-gradient(135deg, rgba(124,92,252,0.08), rgba(34,211,238,0.06), rgba(34,197,94,0.06));
    border: 1px solid rgba(124,92,252,0.2);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 40px;
    animation: fadeUp 0.7s ease 0.6s both;
  }

  .currently-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 14px;
  }

  .currently-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 12px;
    background: rgba(0,0,0,0.2);
    border-radius: 8px;
    border: 1px solid rgba(255,255,255,0.05);
  }

  .currently-icon { font-size: 20px; flex-shrink: 0; margin-top: 1px; }

  .currently-label {
    font-size: 13px;
    font-weight: 600;
    color: var(--text);
    line-height: 1.2;
    margin-bottom: 2px;
  }

  .currently-sub {
    font-size: 11px;
    color: var(--text-muted);
    line-height: 1.4;
  }

  /* === FOOTER === */
  .footer {
    text-align: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--text-muted);
    animation: fadeUp 0.7s ease 0.7s both;
  }

  .footer span {
    background: linear-gradient(90deg, var(--purple-light), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    font-weight: 700;
  }

  /* === ANIMATIONS === */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0; }
  }

  @keyframes float {
    0%, 100% { transform: translateY(0px); }
    50%       { transform: translateY(-8px); }
  }

  .float { animation: float 3s ease-in-out infinite; }
  .float-slow { animation: float 4.5s ease-in-out infinite; animation-delay: 0.5s; }
</style>
</head>
<body>

<canvas id="bg-canvas"></canvas>

<div class="wrapper">

  <!-- HERO -->
  <section class="hero">
    <div class="avatar-ring float">
      <div class="avatar-inner">AJ</div>
    </div>
    <h1>Anas Jamal</h1>
    <p class="subtitle">// Computer Science @ Wilfrid Laurier University</p>

    <div class="typing-wrapper">
      <span class="prompt">❯</span>
      <span class="typed-text" id="typed"></span><span class="cursor"></span>
    </div>

    <div class="badges">
      <span class="badge badge-purple" style="animation-delay:0.1s">🎓 CS Student</span>
      <span class="badge badge-blue"   style="animation-delay:0.2s">🔍 Open to Internships</span>
      <span class="badge badge-cyan"   style="animation-delay:0.3s">📍 Waterloo, ON</span>
      <span class="badge badge-green"  style="animation-delay:0.4s">⚡ Building Cool Stuff</span>
    </div>
  </section>

  <!-- SKILLS -->
  <p class="section-title">Areas of Focus</p>
  <div class="skills-grid" id="skills-grid">

    <div class="skill-card card-purple" style="animation-delay:0.05s">
      <span class="card-icon">🤖</span>
      <div class="card-title">AI / Machine Learning</div>
      <div class="card-desc">Exploring intelligent systems, model training, and the intersection of data and intelligence.</div>
      <div class="card-tags">
        <span class="tag">Python</span><span class="tag">PyTorch</span><span class="tag">scikit-learn</span><span class="tag">NumPy</span>
      </div>
    </div>

    <div class="skill-card card-blue" style="animation-delay:0.1s">
      <span class="card-icon">☁️</span>
      <div class="card-title">Cloud Computing</div>
      <div class="card-desc">Architecting scalable solutions and working with distributed systems in the cloud.</div>
      <div class="card-tags">
        <span class="tag">AWS</span><span class="tag">GCP</span><span class="tag">Docker</span><span class="tag">CI/CD</span>
      </div>
    </div>

    <div class="skill-card card-teal" style="animation-delay:0.15s">
      <span class="card-icon">📊</span>
      <div class="card-title">Data Engineering</div>
      <div class="card-desc">Designing pipelines, wrangling datasets, and transforming raw data into actionable insight.</div>
      <div class="card-tags">
        <span class="tag">SQL</span><span class="tag">Pandas</span><span class="tag">Spark</span><span class="tag">ETL</span>
      </div>
    </div>

    <div class="skill-card card-pink" style="animation-delay:0.2s">
      <span class="card-icon">🛡️</span>
      <div class="card-title">Cybersecurity</div>
      <div class="card-desc">Understanding vulnerabilities, threat modelling, and building more secure systems.</div>
      <div class="card-tags">
        <span class="tag">Networking</span><span class="tag">Cryptography</span><span class="tag">Pentesting</span>
      </div>
    </div>

    <div class="skill-card card-green" style="animation-delay:0.25s">
      <span class="card-icon">💻</span>
      <div class="card-title">Programming</div>
      <div class="card-desc">Writing clean, efficient code across systems, backend, and low-level architectures.</div>
      <div class="card-tags">
        <span class="tag">Java</span><span class="tag">Python</span><span class="tag">C</span><span class="tag">ARM</span>
      </div>
    </div>

    <div class="skill-card card-blue" style="animation-delay:0.3s">
      <span class="card-icon">🔢</span>
      <div class="card-title">CS Foundations</div>
      <div class="card-desc">Calculus, discrete math, algorithms, OOP — the bedrock everything else is built on.</div>
      <div class="card-tags">
        <span class="tag">Algorithms</span><span class="tag">Graph Theory</span><span class="tag">OOP</span>
      </div>
    </div>

  </div>

  <!-- PROFICIENCY BARS -->
  <p class="section-title">Proficiency</p>
  <div class="progress-section" id="progress-section">

    <div class="progress-item">
      <div class="progress-header">
        <span class="progress-label" style="color:var(--purple-light)">🐍 Python</span>
        <span class="progress-pct">88%</span>
      </div>
      <div class="progress-track"><div class="progress-fill fill-purple" data-target="88"></div></div>
    </div>

    <div class="progress-item">
      <div class="progress-header">
        <span class="progress-label" style="color:var(--blue-light)">☕ Java</span>
        <span class="progress-pct">82%</span>
      </div>
      <div class="progress-track"><div class="progress-fill fill-blue" data-target="82"></div></div>
    </div>

    <div class="progress-item">
      <div class="progress-header">
        <span class="progress-label" style="color:var(--cyan)">🗃️ SQL / Data</span>
        <span class="progress-pct">75%</span>
      </div>
      <div class="progress-track"><div class="progress-fill fill-teal" data-target="75"></div></div>
    </div>

    <div class="progress-item">
      <div class="progress-header">
        <span class="progress-label" style="color:var(--teal)">⚙️ ARM Assembly</span>
        <span class="progress-pct">70%</span>
      </div>
      <div class="progress-track"><div class="progress-fill fill-green" data-target="70"></div></div>
    </div>

    <div class="progress-item">
      <div class="progress-header">
        <span class="progress-label" style="color:var(--pink)">🤖 AI / ML</span>
        <span class="progress-pct">65%</span>
      </div>
      <div class="progress-track"><div class="progress-fill fill-pink" data-target="65"></div></div>
    </div>

  </div>

  <!-- QUICK STATS -->
  <p class="section-title">At a Glance</p>
  <div class="stats-row">

    <div class="stat-card">
      <div class="stat-glow" style="background:var(--purple)"></div>
      <span class="stat-value" style="color:var(--purple-light)" data-count="6">0</span>
      <span class="stat-label">Courses Active</span>
    </div>

    <div class="stat-card">
      <div class="stat-glow" style="background:var(--blue)"></div>
      <span class="stat-value" style="color:var(--blue-light)" data-count="12">0</span>
      <span class="stat-label">Projects Built</span>
    </div>

    <div class="stat-card">
      <div class="stat-glow" style="background:var(--cyan)"></div>
      <span class="stat-value" style="color:var(--cyan)" data-count="3">0</span>
      <span class="stat-label">Interests</span>
    </div>

    <div class="stat-card">
      <div class="stat-glow" style="background:var(--green)"></div>
      <span class="stat-value" style="color:var(--green)">∞</span>
      <span class="stat-label">Curiosity</span>
    </div>

  </div>

  <!-- LANGUAGES -->
  <p class="section-title">Languages & Tools</p>
  <div class="langs-section">
    <div class="langs-grid">
      <div class="lang-pill" style="background:rgba(255,222,89,0.07);border-color:rgba(255,222,89,0.3);color:#fde047">
        <span class="lang-dot" style="background:#fde047"></span>Python
      </div>
      <div class="lang-pill" style="background:rgba(239,68,68,0.07);border-color:rgba(239,68,68,0.3);color:#f87171">
        <span class="lang-dot" style="background:#f87171"></span>Java
      </div>
      <div class="lang-pill" style="background:rgba(59,130,246,0.07);border-color:rgba(59,130,246,0.3);color:#60a5fa">
        <span class="lang-dot" style="background:#60a5fa"></span>C
      </div>
      <div class="lang-pill" style="background:rgba(124,92,252,0.07);border-color:rgba(124,92,252,0.3);color:#a78bfa">
        <span class="lang-dot" style="background:#a78bfa"></span>ARM Assembly
      </div>
      <div class="lang-pill" style="background:rgba(34,197,94,0.07);border-color:rgba(34,197,94,0.3);color:#4ade80">
        <span class="lang-dot" style="background:#4ade80"></span>SQL
      </div>
      <div class="lang-pill" style="background:rgba(249,115,22,0.07);border-color:rgba(249,115,22,0.3);color:#fb923c">
        <span class="lang-dot" style="background:#fb923c"></span>Git
      </div>
      <div class="lang-pill" style="background:rgba(20,184,166,0.07);border-color:rgba(20,184,166,0.3);color:#2dd4bf">
        <span class="lang-dot" style="background:#2dd4bf"></span>Linux
      </div>
      <div class="lang-pill" style="background:rgba(99,102,241,0.07);border-color:rgba(99,102,241,0.3);color:#818cf8">
        <span class="lang-dot" style="background:#818cf8"></span>VS Code
      </div>
    </div>
  </div>

  <!-- CURRENTLY INTO -->
  <p class="section-title">Currently Into</p>
  <div class="currently-section">
    <div class="currently-grid">
      <div class="currently-item">
        <span class="currently-icon">🧠</span>
        <div>
          <div class="currently-label">Deep Learning</div>
          <div class="currently-sub">Exploring neural networks and model architectures</div>
        </div>
      </div>
      <div class="currently-item">
        <span class="currently-icon">🔐</span>
        <div>
          <div class="currently-label">Cybersecurity</div>
          <div class="currently-sub">Learning ethical hacking and system hardening</div>
        </div>
      </div>
      <div class="currently-item">
        <span class="currently-icon">🗄️</span>
        <div>
          <div class="currently-label">Data Pipelines</div>
          <div class="currently-sub">Building ETL workflows and analytics systems</div>
        </div>
      </div>
      <div class="currently-item">
        <span class="currently-icon">⚙️</span>
        <div>
          <div class="currently-label">Low-Level Systems</div>
          <div class="currently-sub">ARM assembly and architecture deep dives</div>
        </div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <p>Made with <span>♥</span> · Always learning, always building</p>
    <p style="margin-top:6px;font-size:10px;opacity:0.5">Anas Jamal · Wilfrid Laurier University · Waterloo, ON</p>
  </div>

</div>

<script>
/* ---- PARTICLE BG ---- */
const canvas = document.getElementById('bg-canvas');
const ctx = canvas.getContext('2d');
const particles = [];
const colors = ['#7c5cfc','#3b82f6','#22d3ee','#14b8a6','#22c55e','#a78bfa'];

function resize() {
  canvas.width  = window.innerWidth;
  canvas.height = document.body.scrollHeight;
}
resize();
window.addEventListener('resize', resize);

for (let i = 0; i < 55; i++) {
  particles.push({
    x: Math.random() * window.innerWidth,
    y: Math.random() * window.innerHeight * 3,
    r: Math.random() * 1.8 + 0.4,
    vx: (Math.random() - 0.5) * 0.3,
    vy: -Math.random() * 0.4 - 0.1,
    color: colors[Math.floor(Math.random() * colors.length)],
    alpha: Math.random() * 0.4 + 0.1
  });
}

function drawParticles() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  particles.forEach(p => {
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fillStyle = p.color + Math.round(p.alpha * 255).toString(16).padStart(2,'0');
    ctx.fill();
    p.x += p.vx;
    p.y += p.vy;
    if (p.y < -10) { p.y = canvas.height + 10; p.x = Math.random() * canvas.width; }
  });
  requestAnimationFrame(drawParticles);
}
drawParticles();

/* ---- TYPING EFFECT ---- */
const phrases = [
  'python main.py --mode=train',
  'git commit -m "feat: new model"',
  'ssh aj@cloud.instance.io',
  'nmap -sV target.local',
  'SELECT * FROM insights;',
  'building the future...',
];
let pi = 0, ci = 0, deleting = false;
const el = document.getElementById('typed');

function type() {
  const phrase = phrases[pi];
  if (!deleting) {
    el.textContent = phrase.slice(0, ++ci);
    if (ci === phrase.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    el.textContent = phrase.slice(0, --ci);
    if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
  }
  setTimeout(type, deleting ? 40 : 70);
}
setTimeout(type, 600);

/* ---- PROGRESS BAR ANIMATE ---- */
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      document.querySelectorAll('.progress-fill').forEach(bar => {
        const t = bar.dataset.target;
        setTimeout(() => { bar.style.width = t + '%'; }, 200);
      });
      io.disconnect();
    }
  });
}, { threshold: 0.3 });
io.observe(document.getElementById('progress-section'));

/* ---- COUNT UP ---- */
function countUp(el, target, duration) {
  let start = 0;
  const step = Math.ceil(target / (duration / 60));
  const timer = setInterval(() => {
    start = Math.min(start + step, target);
    el.textContent = start;
    if (start >= target) clearInterval(timer);
  }, 60000 / (duration * 60 / target));
}

const cio = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      document.querySelectorAll('[data-count]').forEach(el => {
        countUp(el, +el.dataset.count, 1200);
      });
      cio.disconnect();
    }
  });
}, { threshold: 0.4 });
const statsRow = document.querySelector('.stats-row');
if (statsRow) cio.observe(statsRow);
</script>
</body>
</html>
