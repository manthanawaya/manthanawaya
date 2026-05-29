<!DOCTYPE html>
<html>
<head>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;600;700&family=Space+Grotesk:wght@400;500;700&display=swap');
  *{box-sizing:border-box;margin:0;padding:0}
  body{background:#0d1117;color:#e6edf3;font-family:'Space Grotesk',sans-serif;min-height:100vh;overflow-x:hidden}
  .container{max-width:900px;margin:0 auto;padding:20px}

  /* WAVE HEADER */
  .wave-header{background:linear-gradient(135deg,#1a1f3a,#0d1117,#1a2744);border-radius:16px;padding:40px 24px 32px;text-align:center;position:relative;overflow:hidden;margin-bottom:24px;border:1px solid #21262d}
  .wave-header::before{content:'';position:absolute;top:-60px;left:-60px;width:300px;height:300px;background:radial-gradient(circle,rgba(0,217,255,0.15),transparent 70%);animation:pulse 4s ease-in-out infinite}
  .wave-header::after{content:'';position:absolute;bottom:-60px;right:-60px;width:250px;height:250px;background:radial-gradient(circle,rgba(139,92,246,0.15),transparent 70%);animation:pulse 4s ease-in-out infinite 2s}
  @keyframes pulse{0%,100%{transform:scale(1);opacity:0.5}50%{transform:scale(1.3);opacity:1}}

  .name-title{font-family:'Fira Code',monospace;font-size:2.2rem;font-weight:700;background:linear-gradient(90deg,#00d9ff,#8b5cf6,#f97316,#00d9ff);background-size:300% 100%;-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:shimmer 3s linear infinite;position:relative;z-index:1}
  @keyframes shimmer{0%{background-position:0% 50%}100%{background-position:300% 50%}}

  .subtitle{color:#8b949e;font-size:1rem;margin-top:8px;position:relative;z-index:1}

  .badge-row{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-top:16px;position:relative;z-index:1}
  .badge{padding:6px 14px;border-radius:20px;font-size:0.75rem;font-weight:600;font-family:'Fira Code',monospace;animation:fadeIn 0.6s ease forwards;opacity:0}
  .badge-blue{background:rgba(0,217,255,0.15);border:1px solid rgba(0,217,255,0.4);color:#00d9ff}
  .badge-purple{background:rgba(139,92,246,0.15);border:1px solid rgba(139,92,246,0.4);color:#a78bfa}
  .badge-orange{background:rgba(249,115,22,0.15);border:1px solid rgba(249,115,22,0.4);color:#fb923c}
  @keyframes fadeIn{to{opacity:1}}

  /* SECTION */
  .section{background:#161b22;border:1px solid #21262d;border-radius:12px;padding:24px;margin-bottom:20px;animation:slideUp 0.5s ease forwards;opacity:0}
  @keyframes slideUp{from{transform:translateY(20px);opacity:0}to{transform:translateY(0);opacity:1}}

  .section-title{font-size:1.1rem;font-weight:700;color:#e6edf3;margin-bottom:16px;display:flex;align-items:center;gap:8px}
  .section-title .emoji{font-size:1.2rem}

  /* CODE BLOCK */
  .code-block{background:#0d1117;border:1px solid #30363d;border-radius:8px;padding:16px;font-family:'Fira Code',monospace;font-size:0.78rem;line-height:1.8;overflow-x:auto}
  .kw{color:#ff7b72}.cls{color:#ffa657}.fn{color:#d2a8ff}.str{color:#a5d6ff}.prop{color:#79c0ff}.cmt{color:#8b949e}.punc{color:#e6edf3}

  /* STATS GRID */
  .stats-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
  .stat-card{background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:16px;text-align:center;transition:all 0.3s;cursor:default}
  .stat-card:hover{border-color:#00d9ff;transform:translateY(-4px);box-shadow:0 8px 24px rgba(0,217,255,0.15)}
  .stat-num{font-size:1.8rem;font-weight:700;font-family:'Fira Code',monospace;background:linear-gradient(135deg,#00d9ff,#8b5cf6);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
  .stat-label{font-size:0.72rem;color:#8b949e;margin-top:4px;text-transform:uppercase;letter-spacing:0.05em}

  /* TECH STACK */
  .tech-grid{display:flex;flex-wrap:wrap;gap:10px}
  .tech-pill{padding:8px 16px;border-radius:8px;font-size:0.8rem;font-weight:600;font-family:'Fira Code',monospace;display:flex;align-items:center;gap:6px;transition:all 0.3s;cursor:default;border:1px solid transparent}
  .tech-pill:hover{transform:scale(1.05);box-shadow:0 4px 16px rgba(0,0,0,0.4)}
  .t-python{background:rgba(59,130,246,0.15);border-color:rgba(59,130,246,0.4);color:#60a5fa}
  .t-cpp{background:rgba(239,68,68,0.15);border-color:rgba(239,68,68,0.4);color:#f87171}
  .t-flask{background:rgba(16,185,129,0.15);border-color:rgba(16,185,129,0.4);color:#34d399}
  .t-html{background:rgba(249,115,22,0.15);border-color:rgba(249,115,22,0.4);color:#fb923c}
  .t-css{background:rgba(99,102,241,0.15);border-color:rgba(99,102,241,0.4);color:#818cf8}
  .t-js{background:rgba(234,179,8,0.15);border-color:rgba(234,179,8,0.4);color:#facc15}
  .t-numpy{background:rgba(0,217,255,0.15);border-color:rgba(0,217,255,0.4);color:#00d9ff}
  .t-pandas{background:rgba(139,92,246,0.15);border-color:rgba(139,92,246,0.4);color:#a78bfa}
  .t-git{background:rgba(249,115,22,0.15);border-color:rgba(249,115,22,0.4);color:#fb923c}
  .t-vscode{background:rgba(30,167,253,0.15);border-color:rgba(30,167,253,0.4);color:#38bdf8}

  /* PROJECTS */
  .project-card{background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:18px;margin-bottom:12px;transition:all 0.3s;position:relative;overflow:hidden;cursor:default}
  .project-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,#00d9ff,#8b5cf6,#f97316);transform:scaleX(0);transition:transform 0.3s;transform-origin:left}
  .project-card:hover::before{transform:scaleX(1)}
  .project-card:hover{border-color:#30363d;transform:translateX(6px);box-shadow:0 4px 20px rgba(0,0,0,0.4)}
  .project-name{font-weight:700;color:#e6edf3;font-size:1rem;margin-bottom:6px}
  .project-desc{color:#8b949e;font-size:0.83rem;line-height:1.6}
  .project-tags{display:flex;gap:6px;margin-top:10px;flex-wrap:wrap}
  .tag{padding:3px 10px;border-radius:20px;font-size:0.7rem;font-weight:600;background:rgba(0,217,255,0.1);border:1px solid rgba(0,217,255,0.25);color:#00d9ff}

  /* SNAKE */
  .snake-container{background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:16px;position:relative;overflow:hidden;height:80px;display:flex;align-items:center}
  .snake{position:absolute;font-size:20px;animation:slither 8s linear infinite}
  @keyframes slither{0%{left:-5%;top:30px}20%{top:15px}40%{top:45px}60%{top:20px}80%{top:40px}100%{left:105%;top:30px}}
  .dot{display:inline-block;width:10px;height:10px;border-radius:50%;background:#00d9ff;margin:0 2px;animation:dotPulse 1.5s ease-in-out infinite}
  .dot:nth-child(2){background:#60a5fa;animation-delay:0.2s}
  .dot:nth-child(3){background:#a78bfa;animation-delay:0.4s}
  .dot:nth-child(4){background:#34d399;animation-delay:0.6s}
  .dot:nth-child(5){background:#fb923c;animation-delay:0.8s}
  @keyframes dotPulse{0%,100%{transform:scale(1);opacity:0.6}50%{transform:scale(1.4);opacity:1}}

  /* CONNECT */
  .connect-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
  .connect-btn{display:flex;align-items:center;gap:10px;padding:14px 18px;border-radius:10px;text-decoration:none;font-weight:600;font-size:0.85rem;transition:all 0.3s;border:1px solid transparent}
  .connect-btn:hover{transform:translateY(-3px);box-shadow:0 8px 20px rgba(0,0,0,0.3)}
  .c-linkedin{background:rgba(10,102,194,0.15);border-color:rgba(10,102,194,0.4);color:#60a5fa}
  .c-email{background:rgba(219,68,55,0.15);border-color:rgba(219,68,55,0.4);color:#f87171}
  .c-instagram{background:rgba(225,48,108,0.15);border-color:rgba(225,48,108,0.4);color:#f472b6}
  .c-github{background:rgba(139,148,158,0.15);border-color:rgba(139,148,158,0.4);color:#e6edf3}

  /* FOOTER */
  .footer-text{text-align:center;color:#8b949e;font-size:0.78rem;font-family:'Fira Code',monospace;margin-top:20px;padding:16px}
  .cursor{display:inline-block;animation:blink 1s step-end infinite}
  @keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

  /* TYPING ANIMATION */
  .typing{overflow:hidden;white-space:nowrap;border-right:2px solid #00d9ff;font-family:'Fira Code',monospace;font-size:1rem;color:#00d9ff;animation:typing 3s steps(40) 0.5s forwards,blink-caret 0.75s step-end infinite;width:0}
  @keyframes typing{to{width:100%}}
  @keyframes blink-caret{0%,100%{border-color:#00d9ff}50%{border-color:transparent}}

  /* STAGGER animations */
  .section:nth-child(1){animation-delay:0.1s}
  .section:nth-child(2){animation-delay:0.2s}
  .section:nth-child(3){animation-delay:0.3s}
  .section:nth-child(4){animation-delay:0.4s}
  .section:nth-child(5){animation-delay:0.5s}
  .section:nth-child(6){animation-delay:0.6s}
  .badge:nth-child(1){animation-delay:0.3s}
  .badge:nth-child(2){animation-delay:0.5s}
  .badge:nth-child(3){animation-delay:0.7s}

  /* ACTIVITY BARS */
  .activity-bar{display:flex;align-items:center;gap:10px;margin-bottom:10px}
  .bar-label{font-size:0.78rem;color:#8b949e;width:80px;flex-shrink:0;font-family:'Fira Code',monospace}
  .bar-track{flex:1;height:8px;background:#21262d;border-radius:4px;overflow:hidden}
  .bar-fill{height:100%;border-radius:4px;animation:barGrow 1.5s ease forwards;transform-origin:left;transform:scaleX(0)}
  @keyframes barGrow{to{transform:scaleX(1)}}
  .bar-pct{font-size:0.72rem;color:#8b949e;width:36px;text-align:right;font-family:'Fira Code',monospace}
</style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="wave-header">
    <div class="name-title">Hi there, I'm Manthan Awaya! 👋</div>
    <div class="typing" style="margin:12px auto 0;display:inline-block">B.Tech CS @ VIT Bhopal | Builder | Hacker | Coder</div>
    <div class="badge-row" style="margin-top:20px">
      <span class="badge badge-blue">🚀 DSA Enthusiast</span>
      <span class="badge badge-purple">🤖 AI Builder</span>
      <span class="badge badge-orange">🏆 Hackathon Warrior</span>
    </div>
  </div>

  <!-- ABOUT / CODE -->
  <div class="section">
    <div class="section-title"><span class="emoji">💡</span> About Me</div>
    <div class="code-block">
<span class="kw">class</span> <span class="cls">Manthan</span>:
  <span class="kw">def</span> <span class="fn">__init__</span>(<span class="prop">self</span>):
    <span class="prop">self</span>.name        = <span class="str">"Manthan Awaya"</span>
    <span class="prop">self</span>.university  = <span class="str">"VIT Bhopal"</span>
    <span class="prop">self</span>.degree      = <span class="str">"B.Tech Computer Science"</span>
    <span class="prop">self</span>.focus       = [<span class="str">"DSA"</span>, <span class="str">"Python"</span>, <span class="str">"Web Dev"</span>, <span class="str">"AI Tools"</span>]
    <span class="prop">self</span>.passion     = <span class="str">"Turning logic into code 🚀"</span>
    <span class="prop">self</span>.hackathons  = [<span class="str">"SafeSpace AI"</span>, <span class="str">"AI Resume Screener"</span>]
<br>
  <span class="kw">def</span> <span class="fn">say_hi</span>(<span class="prop">self</span>):
    <span class="fn">print</span>(<span class="str">"Thanks for dropping by! Let's build something amazing 🔥"</span>)
<br>
<span class="cmt"># Welcome to my profile!</span>
<span class="cls">Manthan</span>().say_hi()
    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="section-title"><span class="emoji">📊</span> GitHub Stats</div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-num" id="c1">0</div><div class="stat-label">Commits</div></div>
      <div class="stat-card"><div class="stat-num" id="c2">0</div><div class="stat-label">Projects</div></div>
      <div class="stat-card"><div class="stat-num" id="c3">0</div><div class="stat-label">Hackathons</div></div>
    </div>
    <br>
    <div class="activity-bar" style="animation-delay:0.2s">
      <span class="bar-label">Python</span>
      <div class="bar-track"><div class="bar-fill" style="width:75%;background:linear-gradient(90deg,#3b82f6,#60a5fa);animation-delay:0.5s"></div></div>
      <span class="bar-pct">75%</span>
    </div>
    <div class="activity-bar">
      <span class="bar-label">C++</span>
      <div class="bar-track"><div class="bar-fill" style="width:60%;background:linear-gradient(90deg,#ef4444,#f87171);animation-delay:0.7s"></div></div>
      <span class="bar-pct">60%</span>
    </div>
    <div class="activity-bar">
      <span class="bar-label">HTML/CSS</span>
      <div class="bar-track"><div class="bar-fill" style="width:65%;background:linear-gradient(90deg,#f97316,#fb923c);animation-delay:0.9s"></div></div>
      <span class="bar-pct">65%</span>
    </div>
    <div class="activity-bar">
      <span class="bar-label">JavaScript</span>
      <div class="bar-track"><div class="bar-fill" style="width:45%;background:linear-gradient(90deg,#eab308,#facc15);animation-delay:1.1s"></div></div>
      <span class="bar-pct">45%</span>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-title"><span class="emoji">🛠️</span> Tech Stack & Tools</div>
    <div style="margin-bottom:12px;font-size:0.78rem;color:#8b949e;font-family:'Fira Code',monospace">// Languages & Frameworks</div>
    <div class="tech-grid">
      <span class="tech-pill t-python">🐍 Python</span>
      <span class="tech-pill t-cpp">⚡ C++</span>
      <span class="tech-pill t-flask">🌿 Flask</span>
      <span class="tech-pill t-html">🌐 HTML5</span>
      <span class="tech-pill t-css">🎨 CSS3</span>
      <span class="tech-pill t-js">✨ JavaScript</span>
      <span class="tech-pill t-numpy">🔢 NumPy</span>
      <span class="tech-pill t-pandas">🐼 Pandas</span>
      <span class="tech-pill t-git">🔀 Git</span>
      <span class="tech-pill t-vscode">💙 VS Code</span>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section">
    <div class="section-title"><span class="emoji">📁</span> Featured Projects</div>
    <div class="project-card">
      <div class="project-name">🛡️ Grade-Guard</div>
      <div class="project-desc">A specialized Python-based predictive grading tool tailored to calculate and analyze academic performance using relative grading and weighted assessment models.</div>
      <div class="project-tags"><span class="tag">Python</span><span class="tag">Data Analysis</span><span class="tag">Academic</span></div>
    </div>
    <div class="project-card">
      <div class="project-name">🤖 SafeSpace AI</div>
      <div class="project-desc">A smart browser extension/AI utility engineered during a hackathon to enhance user safety and digital well-being.</div>
      <div class="project-tags"><span class="tag">AI</span><span class="tag">Browser Extension</span><span class="tag">Hackathon</span></div>
    </div>
    <div class="project-card">
      <div class="project-name">📄 AI Resume Screener</div>
      <div class="project-desc">An automated parser and evaluation tool designed to streamline recruitment by screening resumes against job descriptions intelligently.</div>
      <div class="project-tags"><span class="tag">NLP</span><span class="tag">Python</span><span class="tag">Automation</span></div>
    </div>
  </div>

  <!-- BEYOND THE CODE -->
  <div class="section">
    <div class="section-title"><span class="emoji">🕹️</span> Beyond the Code</div>
    <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:12px;text-align:center">
      <div style="background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:16px;transition:all 0.3s;cursor:default" onmouseover="this.style.borderColor='#00d9ff';this.style.transform='scale(1.05)'" onmouseout="this.style.borderColor='#21262d';this.style.transform='scale(1)'">
        <div style="font-size:2rem">🎮</div>
        <div style="font-size:0.78rem;color:#8b949e;margin-top:8px">Gaming</div>
      </div>
      <div style="background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:16px;transition:all 0.3s;cursor:default" onmouseover="this.style.borderColor='#34d399';this.style.transform='scale(1.05)'" onmouseout="this.style.borderColor='#21262d';this.style.transform='scale(1)'">
        <div style="font-size:2rem">⚽</div>
        <div style="font-size:0.78rem;color:#8b949e;margin-top:8px">Football</div>
      </div>
      <div style="background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:16px;transition:all 0.3s;cursor:default" onmouseover="this.style.borderColor='#f472b6';this.style.transform='scale(1.05)'" onmouseout="this.style.borderColor='#21262d';this.style.transform='scale(1)'">
        <div style="font-size:2rem">🎥</div>
        <div style="font-size:0.78rem;color:#8b949e;margin-top:8px">Binging</div>
      </div>
      <div style="background:#0d1117;border:1px solid #21262d;border-radius:10px;padding:16px;transition:all 0.3s;cursor:default" onmouseover="this.style.borderColor='#facc15';this.style.transform='scale(1.05)'" onmouseout="this.style.borderColor='#21262d';this.style.transform='scale(1)'">
        <div style="font-size:2rem">📸</div>
        <div style="font-size:0.78rem;color:#8b949e;margin-top:8px">Photography</div>
      </div>
    </div>
  </div>

  <!-- SNAKE ANIMATION -->
  <div class="section">
    <div class="section-title"><span class="emoji">🐍</span> Contribution Trail</div>
    <div class="snake-container">
      <div class="snake">🐍</div>
      <div style="display:flex;gap:6px;align-items:center;justify-content:center;width:100%">
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
        <div class="dot"></div><div class="dot"></div><div class="dot"></div>
      </div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-title"><span class="emoji">🤝</span> Connect with Me</div>
    <div class="connect-grid">
      <a href="https://www.linkedin.com/in/manthan-awaya/" class="connect-btn c-linkedin" target="_blank">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
      <a href="mailto:manthanawaya@gmail.com" class="connect-btn c-email">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 01-2.06 0L2 7"/></svg>
        Gmail
      </a>
      <a href="https://www.instagram.com/manthan_awaya" class="connect-btn c-instagram" target="_blank">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><path d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
        Instagram
      </a>
      <a href="https://github.com/manthanawaya" class="connect-btn c-github" target="_blank">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.166 6.839 9.489.5.092.682-.217.682-.482 0-.237-.009-.866-.013-1.7-2.782.605-3.369-1.343-3.369-1.343-.454-1.155-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12c0-5.523-4.477-10-10-10z"/></svg>
        GitHub
      </a>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer-text">
    <span style="color:#00d9ff">⭐ Star my repos if you find them useful!</span><br>
    <span style="color:#8b949e">Always learning, always building </span><span style="color:#f97316">🚀</span>
    <span class="cursor">|</span>
    <br><br>
    <span style="color:#8b949e;font-size:0.7rem">Made with ❤️ by <a href="https://github.com/manthanawaya" style="color:#00d9ff;text-decoration:none">Manthan</a></span>
  </div>

</div>

<script>
  function countUp(id, target, duration) {
    const el = document.getElementById(id);
    let start = 0;
    const step = target / (duration / 16);
    const timer = setInterval(() => {
      start += step;
      if (start >= target) { el.textContent = target + '+'; clearInterval(timer); }
      else el.textContent = Math.floor(start) + '+';
    }, 16);
  }
  setTimeout(() => {
    countUp('c1', 50, 1500);
    countUp('c2', 10, 1200);
    countUp('c3', 5, 800);
  }, 400);
</script>
</body>
</html>
