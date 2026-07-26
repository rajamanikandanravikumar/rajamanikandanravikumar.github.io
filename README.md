<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rajamanikandan — Full-Stack &amp; Cloud Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#0c1220;
    --bg-alt:#0f1626;
    --surface:#131c30;
    --surface-hi:#182339;
    --border:#232f47;
    --text:#e7ecf3;
    --text-dim:#8b96ac;
    --text-faint:#5b657c;
    --teal:#4fd6c4;
    --teal-dim:rgba(79,214,196,0.14);
    --amber:#f2a93b;
    --amber-dim:rgba(242,169,59,0.14);
    --radius:14px;
    --mono:'JetBrains Mono', monospace;
    --display:'Space Grotesk', sans-serif;
    --body:'Inter', sans-serif;
  }

  *{ box-sizing:border-box; margin:0; padding:0; }

  html{ scroll-behavior:smooth; }

  body{
    background:var(--bg);
    color:var(--text);
    font-family:var(--body);
    line-height:1.6;
    overflow-x:hidden;
  }

  ::selection{ background:var(--teal); color:#06120f; }

  a{ color:inherit; text-decoration:none; }

  .wrap{
    max-width:1080px;
    margin:0 auto;
    padding:0 32px;
  }

  /* background grid texture */
  .grid-bg{
    position:fixed;
    inset:0;
    z-index:-2;
    background-image:
      linear-gradient(to right, rgba(255,255,255,0.025) 1px, transparent 1px),
      linear-gradient(to bottom, rgba(255,255,255,0.025) 1px, transparent 1px);
    background-size:44px 44px;
    mask-image:radial-gradient(ellipse 80% 60% at 50% 0%, #000 40%, transparent 100%);
  }

  /* ---------- nav ---------- */
  header{
    position:sticky;
    top:0;
    z-index:50;
    backdrop-filter:blur(10px);
    background:rgba(12,18,32,0.72);
    border-bottom:1px solid var(--border);
  }
  nav{
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:18px 0;
  }
  .logo{
    font-family:var(--mono);
    font-size:15px;
    letter-spacing:0.02em;
    color:var(--text);
  }
  .logo span{ color:var(--teal); }
  .nav-links{
    display:flex;
    gap:32px;
    list-style:none;
    font-family:var(--mono);
    font-size:13px;
    color:var(--text-dim);
  }
  .nav-links a{
    position:relative;
    padding-bottom:4px;
    transition:color .2s ease;
  }
  .nav-links a::after{
    content:'';
    position:absolute;
    left:0; bottom:0;
    width:0; height:1px;
    background:var(--teal);
    transition:width .25s ease;
  }
  .nav-links a:hover{ color:var(--text); }
  .nav-links a:hover::after{ width:100%; }
  .nav-cta{
    font-family:var(--mono);
    font-size:13px;
    border:1px solid var(--border);
    padding:8px 16px;
    border-radius:8px;
    color:var(--teal);
    transition:border-color .2s ease, background .2s ease;
  }
  .nav-cta:hover{ border-color:var(--teal); background:var(--teal-dim); }

  @media (max-width:720px){
    .nav-links{ display:none; }
  }

  /* ---------- hero ---------- */
  .hero{
    position:relative;
    padding:110px 0 90px;
    overflow:hidden;
  }
  .eyebrow{
    font-family:var(--mono);
    font-size:13px;
    color:var(--teal);
    display:flex;
    align-items:center;
    gap:10px;
    margin-bottom:22px;
  }
  .eyebrow::before{
    content:'';
    width:7px; height:7px;
    border-radius:50%;
    background:var(--teal);
    box-shadow:0 0 0 0 rgba(79,214,196,0.6);
    animation:pulse-dot 2.2s infinite;
  }
  @keyframes pulse-dot{
    0%{ box-shadow:0 0 0 0 rgba(79,214,196,0.55); }
    70%{ box-shadow:0 0 0 9px rgba(79,214,196,0); }
    100%{ box-shadow:0 0 0 0 rgba(79,214,196,0); }
  }

  h1{
    font-family:var(--display);
    font-weight:700;
    font-size:clamp(40px, 6vw, 74px);
    line-height:1.04;
    letter-spacing:-0.02em;
    max-width:820px;
  }
  h1 .accent{ color:var(--teal); }

  .role-line{
    margin-top:24px;
    font-family:var(--mono);
    font-size:clamp(15px, 2vw, 19px);
    color:var(--text-dim);
    min-height:1.6em;
  }
  .caret{
    display:inline-block;
    width:9px; height:1.05em;
    background:var(--teal);
    margin-left:2px;
    vertical-align:text-bottom;
    animation:blink 1s steps(1) infinite;
  }
  @keyframes blink{ 50%{ opacity:0; } }

  .chip-row{
    margin-top:34px;
    display:flex;
    flex-wrap:wrap;
    gap:12px;
  }
  .chip{
    font-family:var(--mono);
    font-size:12.5px;
    color:var(--text-dim);
    border:1px solid var(--border);
    background:var(--surface);
    padding:8px 14px;
    border-radius:100px;
    display:flex;
    align-items:center;
    gap:8px;
  }
  .chip .dot{ width:6px; height:6px; border-radius:50%; background:var(--teal); }

  .hero-actions{
    margin-top:44px;
    display:flex;
    gap:14px;
    flex-wrap:wrap;
  }
  .btn{
    font-family:var(--mono);
    font-size:13.5px;
    padding:13px 22px;
    border-radius:9px;
    display:inline-flex;
    align-items:center;
    gap:8px;
    transition:transform .2s ease, background .2s ease, border-color .2s ease;
  }
  .btn-primary{
    background:var(--teal);
    color:#06140f;
    font-weight:500;
  }
  .btn-primary:hover{ transform:translateY(-2px); background:#63e2d1; }
  .btn-ghost{
    border:1px solid var(--border);
    color:var(--text);
  }
  .btn-ghost:hover{ border-color:var(--teal); transform:translateY(-2px); }

  /* sparkline */
  .spark-wrap{
    margin-top:70px;
    position:relative;
  }
  .spark-wrap svg{ width:100%; height:auto; display:block; }
  .spark-label{
    position:absolute;
    font-family:var(--mono);
    font-size:11px;
    color:var(--amber);
    background:var(--amber-dim);
    border:1px solid rgba(242,169,59,0.35);
    padding:3px 8px;
    border-radius:6px;
    white-space:nowrap;
    opacity:0;
    transition:opacity .5s ease 1.4s;
  }
  .spark-wrap.revealed .spark-label{ opacity:1; }
  .spark-caption{
    margin-top:10px;
    font-family:var(--mono);
    font-size:11.5px;
    color:var(--text-faint);
    text-align:right;
  }

  /* ---------- section shell ---------- */
  section{ padding:100px 0; border-top:1px solid var(--border); }
  .section-head{ margin-bottom:52px; }
  .section-head .eyebrow{ margin-bottom:14px; }
  .section-head h2{
    font-family:var(--display);
    font-size:clamp(26px,3vw,36px);
    font-weight:600;
    letter-spacing:-0.01em;
  }

  .reveal{
    opacity:0;
    transform:translateY(24px);
    transition:opacity .7s ease, transform .7s ease;
  }
  .reveal.in{ opacity:1; transform:translateY(0); }

  /* ---------- about ---------- */
  .about-grid{
    display:grid;
    grid-template-columns:1.1fr 1fr;
    gap:56px;
    align-items:start;
  }
  .about-grid p{ color:var(--text-dim); font-size:16px; max-width:46ch; }
  .about-grid p + p{ margin-top:16px; }

  .stat-cards{ display:flex; flex-direction:column; gap:14px; }
  .stat-card{
    background:var(--surface);
    border:1px solid var(--border);
    border-radius:var(--radius);
    padding:20px 22px;
  }
  .stat-card .label{
    font-family:var(--mono);
    font-size:11.5px;
    color:var(--teal);
    text-transform:uppercase;
    letter-spacing:0.06em;
    margin-bottom:8px;
  }
  .stat-card .value{ font-size:15px; color:var(--text); }

  @media (max-width:800px){
    .about-grid{ grid-template-columns:1fr; }
  }

  /* ---------- skills ---------- */
  .skill-group{ margin-bottom:30px; }
  .skill-group:last-child{ margin-bottom:0; }
  .skill-group h3{
    font-family:var(--mono);
    font-size:12.5px;
    color:var(--text-faint);
    text-transform:uppercase;
    letter-spacing:0.07em;
    margin-bottom:14px;
  }
  .skill-tags{ display:flex; flex-wrap:wrap; gap:10px; }
  .tag{
    font-family:var(--body);
    font-size:14px;
    font-weight:500;
    padding:9px 16px;
    border-radius:9px;
    border:1px solid var(--border);
    background:var(--surface);
    color:var(--text);
    transition:transform .18s ease, border-color .18s ease, background .18s ease;
  }
  .tag:hover{
    transform:translateY(-3px);
    border-color:var(--teal);
    background:var(--surface-hi);
  }

  /* ---------- project ---------- */
  .project-card{
    background:var(--surface);
    border:1px solid var(--border);
    border-radius:20px;
    overflow:hidden;
    transition:border-color .25s ease, transform .25s ease;
  }
  .project-card:hover{ border-color:var(--teal); transform:translateY(-4px); }
  .project-top{
    padding:32px 32px 0;
    display:flex;
    justify-content:space-between;
    align-items:flex-start;
    gap:20px;
    flex-wrap:wrap;
  }
  .project-top h3{
    font-family:var(--display);
    font-size:24px;
    font-weight:600;
  }
  .project-top .status{
    font-family:var(--mono);
    font-size:11.5px;
    color:var(--teal);
    border:1px solid rgba(79,214,196,0.35);
    background:var(--teal-dim);
    padding:5px 11px;
    border-radius:100px;
    white-space:nowrap;
  }
  .project-desc{
    padding:16px 32px 0;
    color:var(--text-dim);
    max-width:60ch;
    font-size:15px;
  }
  .feature-ribbon{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:1px;
    background:var(--border);
    margin-top:28px;
  }
  .feature-ribbon div{
    background:var(--surface);
    padding:20px 24px;
  }
  .feature-ribbon .f-label{
    font-family:var(--mono);
    font-size:11px;
    color:var(--text-faint);
    text-transform:uppercase;
    letter-spacing:0.05em;
    margin-bottom:6px;
  }
  .feature-ribbon .f-val{ font-size:14.5px; color:var(--text); }
  @media (max-width:700px){
    .feature-ribbon{ grid-template-columns:1fr; }
  }
  .project-bottom{
    padding:22px 32px 30px;
    display:flex;
    justify-content:space-between;
    align-items:center;
    flex-wrap:wrap;
    gap:16px;
  }
  .stack-tags{ display:flex; gap:8px; flex-wrap:wrap; }
  .stack-tags span{
    font-family:var(--mono);
    font-size:11.5px;
    color:var(--text-dim);
    border:1px solid var(--border);
    padding:5px 10px;
    border-radius:6px;
  }
  .more-note{
    margin-top:20px;
    font-family:var(--mono);
    font-size:12.5px;
    color:var(--text-faint);
    text-align:center;
  }

  /* ---------- status list ---------- */
  .status-list{ display:flex; flex-direction:column; }
  .status-row{
    display:grid;
    grid-template-columns:140px 1fr 130px;
    align-items:center;
    gap:24px;
    padding:22px 0;
    border-top:1px solid var(--border);
  }
  .status-row:first-child{ border-top:none; }
  .status-row .s-key{
    font-family:var(--mono);
    font-size:12px;
    color:var(--text-faint);
    text-transform:uppercase;
    letter-spacing:0.06em;
  }
  .status-row .s-val{ font-size:15.5px; color:var(--text); }
  .status-badge{
    justify-self:end;
    font-family:var(--mono);
    font-size:11.5px;
    display:flex;
    align-items:center;
    gap:8px;
  }
  .status-badge .d{ width:7px; height:7px; border-radius:50%; }
  .d.active{ background:var(--teal); box-shadow:0 0 0 0 rgba(79,214,196,0.55); animation:pulse-dot 2.2s infinite; }
  .d.progress{ background:var(--amber); }
  .d.open{ background:#6ea8ff; }
  @media (max-width:640px){
    .status-row{ grid-template-columns:1fr; gap:6px; }
    .status-badge{ justify-self:start; }
  }

  /* ---------- contact ---------- */
  .terminal{
    background:var(--bg-alt);
    border:1px solid var(--border);
    border-radius:16px;
    overflow:hidden;
  }
  .terminal-bar{
    display:flex;
    gap:7px;
    padding:14px 18px;
    border-bottom:1px solid var(--border);
  }
  .terminal-bar span{ width:10px; height:10px; border-radius:50%; background:var(--border); }
  .terminal-body{ padding:28px 32px 34px; font-family:var(--mono); font-size:14.5px; }
  .terminal-body .cmd{ color:var(--text-faint); }
  .terminal-body .cmd b{ color:var(--teal); font-weight:400; }
  .terminal-line{ margin-bottom:20px; }
  .terminal-line:last-child{ margin-bottom:0; }
  .terminal-out{
    display:flex;
    align-items:center;
    justify-content:space-between;
    flex-wrap:wrap;
    gap:14px;
    margin-top:8px;
    color:var(--text);
  }
  .terminal-out a.btn{ padding:9px 16px; font-size:12.5px; }

  footer{
    padding:36px 0 50px;
    text-align:center;
    font-family:var(--mono);
    font-size:12px;
    color:var(--text-faint);
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation:none !important; transition:none !important; }
    .reveal{ opacity:1; transform:none; }
  }
</style>
</head>
<body>

<div class="grid-bg"></div>

<header>
  <div class="wrap">
    <nav>
      <div class="logo">raja<span>manikandan</span></div>
      <ul class="nav-links">
        <li><a href="#about">About</a></li>
        <li><a href="#skills">Skills</a></li>
        <li><a href="#work">Work</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
      <a href="#contact" class="nav-cta">Say hi ↗</a>
    </nav>
  </div>
</header>

<section class="hero">
  <div class="wrap">
    <div class="eyebrow">$ whoami</div>
    <h1>Rajamanikandan —<br>building <span class="accent">full-stack</span> &amp; <span class="accent">cloud</span> systems.</h1>
    <div class="role-line" id="roleLine"><span class="caret"></span></div>

    <div class="chip-row">
      <div class="chip"><span class="dot"></span>Open to internships</div>
      <div class="chip">Chennai, IN</div>
      <div class="chip">Full-Stack · Cloud · AI Automation</div>
    </div>

    <div class="hero-actions">
      <a href="#work" class="btn btn-primary">View my work</a>
      <a href="mailto:rajamanikandanravikumar@gmail.com" class="btn btn-ghost">Email me</a>
    </div>

    <div class="spark-wrap" id="sparkWrap">
      <svg viewBox="0 0 1000 260" preserveAspectRatio="none">
        <line x1="0" y1="230" x2="1000" y2="230" stroke="var(--border)" stroke-width="1"/>
        <path id="sparkPath"
          d="M0,200 C60,196 120,206 180,192 C260,178 300,210 360,206 C430,200 470,140 520,130 C560,124 600,158 640,176 C700,198 730,64 770,50 C800,42 820,88 850,140 C900,172 950,164 1000,182"
          fill="none" stroke="url(#sparkGrad)" stroke-width="2.5" stroke-linecap="round"/>
        <defs>
          <linearGradient id="sparkGrad" x1="0" y1="0" x2="1" y2="0">
            <stop offset="0%" stop-color="#4fd6c4" stop-opacity="0.35"/>
            <stop offset="70%" stop-color="#4fd6c4"/>
            <stop offset="100%" stop-color="#4fd6c4"/>
          </linearGradient>
        </defs>
        <circle cx="770" cy="50" r="5" fill="#f2a93b"/>
        <circle cx="770" cy="50" r="5" fill="none" stroke="#f2a93b" stroke-width="1.5">
          <animate attributeName="r" values="5;16;5" dur="2.4s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0.9;0;0.9" dur="2.4s" repeatCount="indefinite"/>
        </circle>
      </svg>
      <div class="spark-label" style="left:66%; top:6%;">▲ anomaly flagged — same instinct behind my cost-monitor project</div>
    </div>
    <div class="spark-caption">// this is the exact chart shape from the cost-anomaly detector below</div>
  </div>
</section>

<section id="about">
  <div class="wrap">
    <div class="section-head reveal">
      <div class="eyebrow">// about</div>
      <h2>The short version</h2>
    </div>
    <div class="about-grid reveal">
      <div>
        <p>I'm an IT student at Saveetha Engineering College, based in Chennai, working toward a career in full-stack development and cloud engineering. Most things I build start with a slow workflow or a cloud bill that's grown a mind of its own — from there I reach for Python, Django, and AWS to make it faster, cheaper, or both.</p>
        <p>I completed an internship at Surya Information as a Python Developer, and lately I've been pairing that hands-on experience with AI-assisted automation, plus picking up Go on the side for anything that needs to run lean.</p>
      </div>
      <div class="stat-cards">
        <div class="stat-card">
          <div class="label">Education</div>
          <div class="value">Saveetha Engineering College</div>
        </div>
        <div class="stat-card">
          <div class="label">Internship</div>
          <div class="value">Surya Information — Python Developer</div>
        </div>
        <div class="stat-card">
          <div class="label">Focus areas</div>
          <div class="value">Full-stack development · cloud cost optimization · AI automation</div>
        </div>
        <div class="stat-card">
          <div class="label">Learning right now</div>
          <div class="value">Go, and Dockerized microservices</div>
        </div>
        <div class="stat-card">
          <div class="label">Open to</div>
          <div class="value">Internships &amp; entry-level roles in full-stack engineering or cloud infrastructure</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="skills">
  <div class="wrap">
    <div class="section-head reveal">
      <div class="eyebrow">$ ls ./skills</div>
      <h2>Tools I reach for</h2>
    </div>
    <div class="reveal">
      <div class="skill-group">
        <h3>Languages &amp; core</h3>
        <div class="skill-tags">
          <span class="tag">Python</span>
          <span class="tag">Java</span>
          <span class="tag">JavaScript</span>
          <span class="tag">SQL</span>
        </div>
      </div>
      <div class="skill-group">
        <h3>Frameworks &amp; web</h3>
        <div class="skill-tags">
          <span class="tag">Django</span>
          <span class="tag">HTML5</span>
          <span class="tag">CSS3</span>
        </div>
      </div>
      <div class="skill-group">
        <h3>Cloud &amp; DevOps</h3>
        <div class="skill-tags">
          <span class="tag">AWS</span>
          <span class="tag">Docker</span>
          <span class="tag">Git</span>
          <span class="tag">GitHub</span>
        </div>
      </div>
      <div class="skill-group">
        <h3>Also comfortable with</h3>
        <div class="skill-tags">
          <span class="tag">LLM prompting &amp; AI workflows</span>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="work">
  <div class="wrap">
    <div class="section-head reveal">
      <div class="eyebrow">// featured build</div>
      <h2>AWS Cost Monitor SaaS</h2>
    </div>

    <div class="project-card reveal">
      <div class="project-top">
        <h3>AWS Cost Monitor SaaS</h3>
        <span class="status">● tracking live spend</span>
      </div>
      <p class="project-desc">A dark-themed cloud analytics dashboard that tracks AWS service spend, flags anomalous expenditure spikes the moment they happen, and gives teams a shared thread to talk through what to do about it — instead of finding out from the invoice.</p>

      <div class="feature-ribbon">
        <div>
          <div class="f-label">Spend tracking</div>
          <div class="f-val">Per-service AWS cost breakdown</div>
        </div>
        <div>
          <div class="f-label">Anomaly alerts</div>
          <div class="f-val">Flags unusual spikes automatically</div>
        </div>
        <div>
          <div class="f-label">Team threads</div>
          <div class="f-val">Discuss a spike without leaving the dashboard</div>
        </div>
      </div>

      <div class="project-bottom">
        <div class="stack-tags">
          <span>Python</span><span>Django</span><span>AWS</span><span>Chart.js</span><span>CSS3</span>
        </div>
        <a href="https://github.com/rajamanikandanravikumar/cost-monitor-saas" class="btn btn-ghost" target="_blank" rel="noopener">View repository ↗</a>
      </div>
    </div>
    <p class="more-note">// more builds in progress — this page grows as they ship</p>
  </div>
</section>

<section>
  <div class="wrap">
    <div class="section-head reveal">
      <div class="eyebrow">$ status --watch</div>
      <h2>What I'm up to</h2>
    </div>
    <div class="status-list reveal">
      <div class="status-row">
        <div class="s-key">Focus</div>
        <div class="s-val">Full-stack systems, cloud cost optimization, AI automation</div>
        <div class="status-badge"><span class="d active"></span>active</div>
      </div>
      <div class="status-row">
        <div class="s-key">Learning</div>
        <div class="s-val">Go, and Dockerized microservices</div>
        <div class="status-badge"><span class="d progress"></span>in progress</div>
      </div>
      <div class="status-row">
        <div class="s-key">Open to</div>
        <div class="s-val">Internships &amp; entry-level roles — full-stack / cloud</div>
        <div class="status-badge"><span class="d open"></span>open</div>
      </div>
    </div>
  </div>
</section>

<section id="contact">
  <div class="wrap">
    <div class="section-head reveal">
      <div class="eyebrow">$ contact --send</div>
      <h2>Let's talk</h2>
    </div>
    <div class="terminal reveal">
      <div class="terminal-bar"><span></span><span></span><span></span></div>
      <div class="terminal-body">
        <div class="terminal-line">
          <div class="cmd">$ contact <b>--method email</b></div>
          <div class="terminal-out">
            <span>rajamanikandanravikumar@gmail.com</span>
            <a href="mailto:rajamanikandanravikumar@gmail.com" class="btn btn-primary">Send email</a>
          </div>
        </div>
        <div class="terminal-line">
          <div class="cmd">$ contact <b>--method linkedin</b></div>
          <div class="terminal-out">
            <span>linkedin.com/in/rajamanikandan-r-481a65298</span>
            <a href="https://www.linkedin.com/in/rajamanikandan-r-481a65298" class="btn btn-ghost" target="_blank" rel="noopener">Open profile ↗</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<footer>Built by Rajamanikandan — Coimbatore, India</footer>

<script>
  // typing effect for role line
  const roleText = "Full-Stack Development — Cloud Cost Optimization — AI Automation";
  const roleEl = document.getElementById('roleLine');
  const caret = roleEl.querySelector('.caret');
  let i = 0;
  const prefersReduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  function typeChar(){
    if(i < roleText.length){
      caret.insertAdjacentText('beforebegin', roleText.charAt(i));
      i++;
      setTimeout(typeChar, 32);
    }
  }
  if(prefersReduced){
    roleEl.textContent = roleText;
  } else {
    typeChar();
  }

  // scroll reveal
  const revealEls = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if(entry.isIntersecting){
        entry.target.classList.add('in');
        io.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });
  revealEls.forEach(el => io.observe(el));

  // sparkline draw-in
  const path = document.getElementById('sparkPath');
  const sparkWrap = document.getElementById('sparkWrap');
  const len = path.getTotalLength();
  path.style.strokeDasharray = len;
  path.style.strokeDashoffset = len;
  requestAnimationFrame(() => {
    path.style.transition = 'stroke-dashoffset 1.8s ease';
    setTimeout(() => {
      path.style.strokeDashoffset = 0;
      sparkWrap.classList.add('revealed');
    }, 300);
  });
</script>

</body>
</html>
