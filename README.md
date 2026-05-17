<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Supun Sandaruwan — Developer Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #060810;
    --surface: #0d1117;
    --card: #111827;
    --border: rgba(99,179,237,0.12);
    --accent: #38bdf8;
    --accent2: #818cf8;
    --accent3: #34d399;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: 0 0 32px rgba(56,189,248,0.15);
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── CANVAS BACKGROUND ── */
  #canvas-bg {
    position: fixed; inset: 0; z-index: 0; opacity: 0.5;
    pointer-events: none;
  }

  /* ── WRAPPER ── */
  .wrapper {
    position: relative; z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 48px 0 40px;
    animation: fadeDown 0.8s ease both;
  }
  .avatar-ring {
    display: inline-block;
    width: 110px; height: 110px;
    border-radius: 50%;
    padding: 3px;
    background: linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3));
    margin-bottom: 24px;
    box-shadow: 0 0 40px rgba(56,189,248,0.3);
    animation: spinRing 6s linear infinite;
  }
  @keyframes spinRing {
    from { filter: hue-rotate(0deg); }
    to   { filter: hue-rotate(360deg); }
  }
  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--bg);
    display: flex; align-items: center; justify-content: center;
    font-size: 46px;
  }
  .hero-greeting {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 5vw, 3.4rem);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -1px;
  }
  .hero-greeting .hi { color: var(--accent); }
  .cursor {
    display: inline-block;
    width: 3px; height: 1.1em;
    background: var(--accent);
    margin-left: 4px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }
  .hero-sub {
    margin-top: 12px;
    font-size: 0.82rem;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
  }
  .hero-sub span { color: var(--accent3); }

  /* ── BADGES ── */
  .badges {
    display: flex; flex-wrap: wrap; gap: 10px;
    justify-content: center;
    margin-top: 28px;
  }
  .badge {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 8px 16px;
    border-radius: 999px;
    border: 1px solid var(--border);
    background: rgba(255,255,255,0.03);
    font-size: 0.75rem;
    letter-spacing: 0.5px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.2s;
  }
  .badge:hover {
    border-color: var(--accent);
    color: var(--accent);
    box-shadow: var(--glow);
    transform: translateY(-2px);
  }
  .badge .dot {
    width: 8px; height: 8px; border-radius: 50%;
  }

  /* ── SECTION ── */
  section { margin-top: 56px; animation: fadeUp 0.6s ease both; }
  section:nth-child(2) { animation-delay: 0.1s; }
  section:nth-child(3) { animation-delay: 0.2s; }
  section:nth-child(4) { animation-delay: 0.3s; }
  section:nth-child(5) { animation-delay: 0.4s; }
  @keyframes fadeUp { from { opacity:0; transform:translateY(24px); } to { opacity:1; transform:none; } }
  @keyframes fadeDown { from { opacity:0; transform:translateY(-18px); } to { opacity:1; transform:none; } }

  .sec-label {
    font-family: 'Syne', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
    display: flex; align-items: center; gap: 10px;
  }
  .sec-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, var(--border), transparent);
  }
  .sec-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.4rem, 3vw, 2rem);
    font-weight: 800;
    margin-bottom: 20px;
    line-height: 1.2;
  }

  /* ── ABOUT CARD ── */
  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 28px 32px;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2), var(--accent3));
  }
  .about-list { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .about-list li {
    display: flex; align-items: flex-start; gap: 12px;
    font-size: 0.85rem; color: var(--text);
    line-height: 1.6;
  }
  .about-list li .ico { font-size: 1rem; flex-shrink: 0; margin-top: 1px; }

  /* ── SKILLS ── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 12px;
  }
  .skill-chip {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 14px;
    display: flex; align-items: center; gap: 10px;
    font-size: 0.78rem;
    transition: all 0.25s;
    cursor: default;
    position: relative; overflow: hidden;
  }
  .skill-chip::after {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, transparent 60%, rgba(56,189,248,0.06));
    opacity: 0;
    transition: opacity 0.25s;
  }
  .skill-chip:hover {
    border-color: var(--accent);
    transform: translateY(-3px);
    box-shadow: 0 6px 24px rgba(56,189,248,0.12);
  }
  .skill-chip:hover::after { opacity: 1; }
  .skill-chip .skill-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }

  /* ── PROJECTS ── */
  .projects-grid { display: grid; gap: 16px; }
  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px 26px;
    display: flex; flex-direction: column; gap: 8px;
    position: relative; overflow: hidden;
    transition: all 0.25s;
    text-decoration: none; color: inherit;
  }
  .project-card::before {
    content: '';
    position: absolute; left: 0; top: 0; bottom: 0; width: 3px;
    background: linear-gradient(to bottom, var(--accent), var(--accent2));
    opacity: 0; transition: opacity 0.25s;
  }
  .project-card:hover {
    border-color: rgba(99,179,237,0.3);
    transform: translateX(4px);
    box-shadow: var(--glow);
  }
  .project-card:hover::before { opacity: 1; }
  .project-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 1rem;
    color: var(--accent);
  }
  .project-desc { font-size: 0.8rem; color: var(--muted); line-height: 1.6; }
  .project-url {
    font-size: 0.72rem; color: var(--accent3);
    opacity: 0.7;
    letter-spacing: 0.3px;
    word-break: break-all;
  }

  /* ── STATS ── */
  .stats-row {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  .stat-img {
    width: 100%; border-radius: 12px;
    border: 1px solid var(--border);
    display: block;
    transition: transform 0.25s, box-shadow 0.25s;
  }
  .stat-img:hover {
    transform: translateY(-4px);
    box-shadow: var(--glow);
  }

  /* ── CONTACT ── */
  .contact-row {
    display: flex; flex-wrap: wrap; gap: 14px;
  }
  .contact-btn {
    display: inline-flex; align-items: center; gap: 9px;
    padding: 11px 22px;
    border-radius: 10px;
    font-size: 0.8rem;
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    letter-spacing: 0.4px;
    text-decoration: none;
    transition: all 0.2s;
    border: 1px solid;
  }
  .contact-btn.primary {
    background: var(--accent);
    border-color: var(--accent);
    color: #060810;
  }
  .contact-btn.primary:hover {
    background: transparent; color: var(--accent);
    box-shadow: var(--glow);
  }
  .contact-btn.secondary {
    background: transparent;
    border-color: var(--border);
    color: var(--text);
  }
  .contact-btn.secondary:hover {
    border-color: var(--accent2);
    color: var(--accent2);
    box-shadow: 0 0 24px rgba(129,140,248,0.15);
  }

  /* ── FOOTER ── */
  .footer {
    margin-top: 72px;
    text-align: center;
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 1px;
    padding-bottom: 24px;
  }
  .footer .heart { color: #f87171; }

  /* ── PROFILE VIEWS BADGE ── */
  .views-badge {
    display: inline-block;
    margin-top: 12px;
    padding: 4px 14px;
    border-radius: 999px;
    background: rgba(14,149,149,0.08);
    border: 1px solid rgba(14,149,149,0.2);
    font-size: 0.72rem;
    color: #0e9595;
  }

  @media (max-width: 560px) {
    .stats-row { grid-template-columns: 1fr; }
    .about-card { padding: 20px; }
  }
</style>
</head>
<body>

<canvas id="canvas-bg"></canvas>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="avatar-ring">
      <div class="avatar-inner">💻</div>
    </div>
    <h1 class="hero-greeting">
      <span class="hi">Hi</span> 👋, I'm<br/>
      <span id="typed-name"></span><span class="cursor"></span>
    </h1>
    <p class="hero-sub">
      Software Engineering Undergraduate &nbsp;·&nbsp;
      <span>Fullstack Developer</span> &nbsp;·&nbsp; Freelancer
    </p>

    <div class="badges">
      <a href="https://www.linkedin.com/in/supun-sandaruwan-98bab3235/" target="_blank" class="badge">
        <span class="dot" style="background:#0A66C2"></span> LinkedIn
      </a>
      <a href="mailto:jdsupunsabdaruwan@gmail.com" class="badge">
        <span class="dot" style="background:#EA4335"></span> Email
      </a>
      <a href="https://www.buymeacoffee.com/sandaruwanjds" target="_blank" class="badge">
        <span class="dot" style="background:#FFDD00"></span> Buy Me a Coffee
      </a>
      <a href="https://github.com/Sandaruwanjds" target="_blank" class="badge">
        <span class="dot" style="background:#6e40c9"></span> GitHub
      </a>
    </div>
  </div>

  <!-- ABOUT -->
  <section>
    <div class="sec-label">// about</div>
    <div class="about-card">
      <ul class="about-list">
        <li><span class="ico">🎓</span> Final-year <strong>Software Engineering Undergraduate</strong> at the Open University of Sri Lanka</li>
        <li><span class="ico">🌐</span> Fullstack developer — web systems, desktop apps, REST APIs, and mobile applications</li>
        <li><span class="ico">🎨</span> Strong interest in <strong>UI/UX design</strong> &amp; clean system architecture</li>
        <li><span class="ico">🧠</span> Passionate about solving real-world problems with elegant technology</li>
        <li><span class="ico">📌</span> Actively seeking <strong>internships, junior dev roles &amp; freelance collaborations</strong></li>
      </ul>
    </div>
  </section>

  <!-- SKILLS -->
  <section>
    <div class="sec-label">// tech stack</div>
    <div class="skills-grid" id="skills-grid"></div>
  </section>

  <!-- GITHUB STATS -->
  <section>
    <div class="sec-label">// github analytics</div>
    <div class="stats-row">
      <img class="stat-img"
        src="https://github-readme-stats.vercel.app/api?username=sandaruwanjds&show_icons=true&theme=tokyonight&hide_border=true"
        alt="GitHub Stats"/>
      <img class="stat-img"
        src="https://streak-stats.demolab.com?user=sandaruwanjds&theme=tokyonight&hide_border=true"
        alt="GitHub Streak"/>
    </div>
    <div style="margin-top:16px; text-align:center;">
      <img style="border-radius:10px; border:1px solid var(--border);"
        src="https://github-profile-trophy.vercel.app/?username=sandaruwanjds&theme=tokyonight&no-frame=true&row=1&margin-w=12"
        alt="Trophies"/>
    </div>
  </section>

  <!-- PROJECTS -->
  <section>
    <div class="sec-label">// featured projects</div>
    <div class="projects-grid">
      <a class="project-card" href="https://github.com/Sandaruwanjds/MyExpenseTracker" target="_blank">
        <div class="project-name">💰 MyExpenseTracker</div>
        <div class="project-desc">Android expense tracking app — manage budgets, log transactions and visualize spending habits on mobile.</div>
        <div class="project-url">github.com/Sandaruwanjds/MyExpenseTracker</div>
      </a>
      <a class="project-card" href="https://github.com/Sandaruwanjds/Hotel360" target="_blank">
        <div class="project-name">🏨 Hotel360</div>
        <div class="project-desc">Full-featured hotel booking &amp; management system — reservations, room inventory, admin dashboard.</div>
        <div class="project-url">github.com/Sandaruwanjds/Hotel360</div>
      </a>
      <a class="project-card" href="https://github.com/Sandaruwanjds?tab=repositories" target="_blank">
        <div class="project-name">🚀 More Projects →</div>
        <div class="project-desc">Explore all repositories including web apps, system tools, and experiments.</div>
        <div class="project-url">github.com/Sandaruwanjds?tab=repositories</div>
      </a>
    </div>
  </section>

  <!-- CONTACT -->
  <section>
    <div class="sec-label">// let's connect</div>
    <p style="font-size:0.83rem; color:var(--muted); margin-bottom:20px; line-height:1.7;">
      Open to <span style="color:var(--accent3)">internships</span>, <span style="color:var(--accent)">freelance work</span>, and <span style="color:var(--accent2)">collaborations</span>. Let's build something great together.
    </p>
    <div class="contact-row">
      <a href="mailto:jdsupunsabdaruwan@gmail.com" class="contact-btn primary">✉ Send Email</a>
      <a href="https://www.linkedin.com/in/supun-sandaruwan-98bab3235/" target="_blank" class="contact-btn secondary">💼 LinkedIn</a>
      <a href="https://github.com/Sandaruwanjds" target="_blank" class="contact-btn secondary">🐙 GitHub</a>
      <a href="https://www.buymeacoffee.com/sandaruwanjds" target="_blank" class="contact-btn secondary">☕ Buy Me a Coffee</a>
    </div>
  </section>

  <!-- FOOTER -->
  <div class="footer">
    <div class="views-badge">
      <img src="https://komarev.com/ghpvc/?username=sandaruwanjds&label=Profile+Views&color=0e9595&style=flat-square" alt="Profile views" style="vertical-align:middle; border:none;"/>
    </div>
    <p style="margin-top:14px;">Built with <span class="heart">♥</span> by Supun Sandaruwan &nbsp;·&nbsp; Open University of Sri Lanka</p>
  </div>

</div>

<script>
/* ── PARTICLE CANVAS ── */
const canvas = document.getElementById('canvas-bg');
const ctx = canvas.getContext('2d');
let W, H, particles = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * W;
    this.y = Math.random() * H;
    this.vx = (Math.random() - 0.5) * 0.3;
    this.vy = (Math.random() - 0.5) * 0.3;
    this.r = Math.random() * 1.5 + 0.5;
    this.alpha = Math.random() * 0.4 + 0.1;
    const hues = [200, 230, 160];
    this.hue = hues[Math.floor(Math.random() * hues.length)];
  }
  update() {
    this.x += this.vx; this.y += this.vy;
    if (this.x < 0 || this.x > W || this.y < 0 || this.y > H) this.reset();
  }
  draw() {
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
    ctx.fillStyle = `hsla(${this.hue},80%,65%,${this.alpha})`;
    ctx.fill();
  }
}

for (let i = 0; i < 90; i++) particles.push(new Particle());

function drawLines() {
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx*dx + dy*dy);
      if (dist < 100) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.strokeStyle = `rgba(56,189,248,${0.06 * (1 - dist/100)})`;
        ctx.lineWidth = 0.5;
        ctx.stroke();
      }
    }
  }
}

function loop() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => { p.update(); p.draw(); });
  drawLines();
  requestAnimationFrame(loop);
}
loop();

/* ── TYPED NAME EFFECT ── */
const name = "Supun Sandaruwan";
let idx = 0;
const el = document.getElementById('typed-name');
function typeChar() {
  if (idx < name.length) {
    el.textContent += name[idx++];
    setTimeout(typeChar, 70 + Math.random() * 40);
  }
}
setTimeout(typeChar, 500);

/* ── SKILLS DATA ── */
const skills = [
  { name: 'JavaScript', color: '#F7DF1E' },
  { name: 'TypeScript', color: '#3178C6' },
  { name: 'React', color: '#61DAFB' },
  { name: 'Vue.js', color: '#42B883' },
  { name: 'Node.js', color: '#339933' },
  { name: 'Java', color: '#ED8B00' },
  { name: 'Kotlin', color: '#7F52FF' },
  { name: 'Python', color: '#3776AB' },
  { name: 'C', color: '#A8B9CC' },
  { name: 'PHP', color: '#777BB4' },
  { name: 'SQL / MySQL', color: '#4479A1' },
  { name: 'SQLite', color: '#003B57' },
  { name: 'HTML5', color: '#E34F26' },
  { name: 'CSS3', color: '#1572B6' },
  { name: 'Tailwind CSS', color: '#06B6D4' },
  { name: 'Bootstrap', color: '#7952B3' },
  { name: 'Android Dev', color: '#3DDC84' },
  { name: 'Docker', color: '#2496ED' },
  { name: 'Git', color: '#F05032' },
  { name: 'Figma', color: '#F24E1E' },
  { name: 'Postman', color: '#FF6C37' },
  { name: 'GCP', color: '#4285F4' },
];

const grid = document.getElementById('skills-grid');
skills.forEach((s, i) => {
  const div = document.createElement('div');
  div.className = 'skill-chip';
  div.style.animationDelay = `${i * 30}ms`;
  div.innerHTML = `<span class="skill-dot" style="background:${s.color};box-shadow:0 0 6px ${s.color}66"></span>${s.name}`;
  grid.appendChild(div);
});

/* ── SCROLL FADE-IN ── */
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) { e.target.style.opacity = '1'; e.target.style.transform = 'none'; }
  });
}, { threshold: 0.1 });
document.querySelectorAll('section').forEach(s => {
  s.style.opacity = '0';
  s.style.transform = 'translateY(24px)';
  s.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
  obs.observe(s);
});
</script>
</body>
</html>
