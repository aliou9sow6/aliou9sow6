<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aliou Saïd Noor SOW — Développeur Web</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=Space+Mono:wght@400;700&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --card: #16161f;
    --border: #2a2a3a;
    --accent: #e8c16c;
    --accent2: #7c6af7;
    --accent3: #4fd1c5;
    --text: #e8e8f0;
    --muted: #7878a0;
    --glow: rgba(232, 193, 108, 0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 50% at 10% 20%, rgba(124,106,247,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 60% 40% at 85% 80%, rgba(232,193,108,0.06) 0%, transparent 60%),
      radial-gradient(ellipse 50% 60% at 50% 50%, rgba(79,209,197,0.04) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .noise {
    position: fixed;
    inset: 0;
    opacity: 0.03;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 960px;
    margin: 0 auto;
    padding: 0 32px;
    position: relative;
    z-index: 1;
  }

  /* HERO */
  .hero {
    padding: 100px 0 60px;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 48px;
    align-items: center;
    border-bottom: 1px solid var(--border);
  }

  .hero-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 12px;
    animation: fadeUp 0.8s ease forwards;
    opacity: 0;
    transform: translateY(16px);
  }

  .hero-eyebrow::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, var(--accent), transparent);
    max-width: 80px;
  }

  .hero-name {
    font-family: 'Playfair Display', serif;
    font-size: clamp(42px, 6vw, 72px);
    font-weight: 900;
    line-height: 1.0;
    letter-spacing: -0.02em;
    animation: fadeUp 0.8s 0.1s ease forwards;
    opacity: 0;
    transform: translateY(16px);
  }

  .hero-name .accent-word {
    color: var(--accent);
    font-style: italic;
  }

  .hero-tagline {
    margin-top: 20px;
    font-size: 16px;
    color: var(--muted);
    font-weight: 300;
    max-width: 420px;
    line-height: 1.7;
    animation: fadeUp 0.8s 0.2s ease forwards;
    opacity: 0;
    transform: translateY(16px);
  }

  .hero-cta {
    display: flex;
    gap: 12px;
    margin-top: 36px;
    animation: fadeUp 0.8s 0.3s ease forwards;
    opacity: 0;
    transform: translateY(16px);
  }

  .btn {
    padding: 11px 24px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    text-decoration: none;
    border-radius: 4px;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }

  .btn-primary {
    background: var(--accent);
    color: #0a0a0f;
    font-weight: 700;
  }

  .btn-primary:hover {
    background: #f0d080;
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(232,193,108,0.3);
  }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }

  .btn-ghost:hover {
    border-color: var(--accent);
    color: var(--accent);
    transform: translateY(-2px);
  }

  .hero-badge {
    animation: fadeUp 0.8s 0.4s ease forwards;
    opacity: 0;
    transform: translateY(16px);
  }

  .status-pill {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 12px 20px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 100px;
    font-size: 13px;
    color: var(--muted);
    white-space: nowrap;
  }

  .status-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: #4ade80;
    box-shadow: 0 0 8px #4ade80;
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.85); }
  }

  /* SECTION */
  .section {
    padding: 72px 0;
    border-bottom: 1px solid var(--border);
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 40px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .section-label::before {
    content: attr(data-num);
    color: var(--muted);
    font-size: 9px;
  }

  /* SKILLS GRID */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 12px;
  }

  .skill-chip {
    padding: 14px 16px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 6px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text);
    text-align: center;
    transition: all 0.2s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .skill-chip::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--accent2), var(--accent3));
    opacity: 0;
    transition: opacity 0.2s;
  }

  .skill-chip:hover::before { opacity: 0.08; }

  .skill-chip:hover {
    border-color: var(--accent2);
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(124,106,247,0.15);
  }

  .skill-chip span { position: relative; z-index: 1; }

  /* EDUCATION */
  .edu-list {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .edu-item {
    display: grid;
    grid-template-columns: 4px 1fr;
    gap: 20px;
    padding: 24px 0;
    border-bottom: 1px solid var(--border);
  }

  .edu-item:last-child { border-bottom: none; }

  .edu-bar {
    background: linear-gradient(to bottom, var(--accent), var(--accent2));
    border-radius: 4px;
    margin-top: 4px;
  }

  .edu-institution {
    font-family: 'Playfair Display', serif;
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 6px;
  }

  .edu-degree {
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 4px;
    line-height: 1.6;
  }

  .edu-location {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-top: 8px;
  }

  /* EXPERIENCE */
  .exp-list {
    display: flex;
    flex-direction: column;
    gap: 0;
  }

  .exp-item {
    display: grid;
    grid-template-columns: 140px 1fr;
    gap: 32px;
    padding: 28px 0;
    border-bottom: 1px solid var(--border);
    align-items: start;
  }

  .exp-item:last-child { border-bottom: none; }

  .exp-year {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    padding-top: 4px;
    letter-spacing: 0.05em;
  }

  .exp-role {
    font-family: 'Playfair Display', serif;
    font-size: 20px;
    font-weight: 700;
    margin-bottom: 6px;
  }

  .exp-company {
    font-size: 14px;
    color: var(--accent);
    margin-bottom: 4px;
    font-weight: 500;
  }

  .exp-company a { color: inherit; text-decoration: none; }
  .exp-company a:hover { text-decoration: underline; }

  /* STATS */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 24px;
  }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
    transition: border-color 0.2s;
  }

  .stat-card:hover { border-color: var(--accent2); }

  .stat-card img {
    width: 100%;
    display: block;
  }

  .stat-card-wide {
    grid-column: 1 / -1;
  }

  /* QUOTES */
  .quotes-list {
    display: flex;
    flex-direction: column;
    gap: 32px;
  }

  .quote-block {
    padding: 32px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    border-left: 3px solid var(--accent);
    position: relative;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .quote-block:hover {
    transform: translateX(6px);
    box-shadow: -6px 0 20px rgba(232,193,108,0.1);
  }

  .quote-block::before {
    content: '"';
    position: absolute;
    top: 16px;
    right: 24px;
    font-family: 'Playfair Display', serif;
    font-size: 80px;
    color: var(--border);
    line-height: 1;
  }

  .quote-text {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: 17px;
    line-height: 1.7;
    color: var(--text);
    margin-bottom: 16px;
  }

  .quote-author {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* CONTACT */
  .contact-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 16px;
  }

  .contact-card {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 20px 24px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.2s;
  }

  .contact-card:hover {
    border-color: var(--accent);
    transform: translateY(-3px);
    box-shadow: 0 12px 30px rgba(232,193,108,0.1);
  }

  .contact-icon {
    width: 40px;
    height: 40px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
  }

  .contact-icon.email { background: rgba(232,193,108,0.12); }
  .contact-icon.linkedin { background: rgba(10,102,194,0.15); }

  .contact-label {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 4px;
  }

  .contact-value {
    font-size: 13px;
    font-weight: 500;
  }

  /* FOOTER */
  .footer {
    padding: 40px 0;
    text-align: center;
  }

  .footer-text {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .footer-text span {
    color: var(--accent);
  }

  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }

  .animate-in {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .animate-in.visible {
    opacity: 1;
    transform: translateY(0);
  }

  @media (max-width: 640px) {
    .hero { grid-template-columns: 1fr; }
    .hero-badge { order: -1; }
    .exp-item { grid-template-columns: 1fr; gap: 8px; }
    .stats-grid { grid-template-columns: 1fr; }
    .stat-card-wide { grid-column: 1; }
  }
</style>
</head>
<body>
<div class="noise"></div>

<div class="container">

  <!-- HERO -->
  <section class="hero">
    <div>
      <div class="hero-eyebrow">Développeur Web Full-Stack</div>
      <h1 class="hero-name">
        Aliou<br>
        <span class="accent-word">Saïd Noor</span><br>
        SOW
      </h1>
      <p class="hero-tagline">
        Passionné par les nouvelles technologies et le développement de solutions innovantes. Angular · Spring Boot · Laravel.
      </p>
      <div class="hero-cta">
        <a href="mailto:aliou9sow6@gmail.com" class="btn btn-primary">
          ✉ Me contacter
        </a>
        <a href="https://www.linkedin.com/in/aliou-saidou-nourou-sow-054084228/" class="btn btn-ghost" target="_blank">
          LinkedIn →
        </a>
      </div>
    </div>
    <div class="hero-badge">
      <div class="status-pill">
        <span class="status-dot"></span>
        Disponible pour collaborations
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section class="section">
    <div class="section-label" data-num="01">Compétences</div>
    <div class="skills-grid animate-in">
      <div class="skill-chip"><span>Angular</span></div>
      <div class="skill-chip"><span>Spring Boot</span></div>
      <div class="skill-chip"><span>Laravel</span></div>
      <div class="skill-chip"><span>JavaScript</span></div>
      <div class="skill-chip"><span>Java</span></div>
      <div class="skill-chip"><span>PHP</span></div>
      <div class="skill-chip"><span>C</span></div>
      <div class="skill-chip"><span>TypeScript</span></div>
      <div class="skill-chip"><span>HTML/CSS</span></div>
      <div class="skill-chip"><span>REST API</span></div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section class="section">
    <div class="section-label" data-num="02">Expériences</div>
    <div class="exp-list animate-in">
      <div class="exp-item">
        <div class="exp-year">2023 — 2025</div>
        <div>
          <div class="exp-role">Développeur Web</div>
          <div class="exp-company"><a href="https://atos.net/" target="_blank">Atos Sénégal ↗</a></div>
        </div>
      </div>
      <div class="exp-item">
        <div class="exp-year">En cours</div>
        <div>
          <div class="exp-role">Ambassadeur Numérique</div>
          <div class="exp-company">Programme CFE — Banque Africaine de Développement (BAD)</div>
        </div>
      </div>
    </div>
  </section>

  <!-- EDUCATION -->
  <section class="section">
    <div class="section-label" data-num="03">Formation</div>
    <div class="edu-list animate-in">
      <div class="edu-item">
        <div class="edu-bar"></div>
        <div>
          <div class="edu-institution">WorldQuant University</div>
          <div class="edu-degree">Laboratoire de Science des Données Appliquées</div>
          <div class="edu-location">201 St. Charles Ave · New Orleans, LA 70170</div>
        </div>
      </div>
      <div class="edu-item">
        <div class="edu-bar"></div>
        <div>
          <div class="edu-institution">UNCHK</div>
          <div class="edu-degree">Certificat en Développement Logiciel</div>
          <div class="edu-location">Université Numérique Cheikh Hamidou KANE · Sénégal</div>
        </div>
      </div>
      <div class="edu-item">
        <div class="edu-bar"></div>
        <div>
          <div class="edu-institution">UADB — Bambey</div>
          <div class="edu-degree">Développement et Administration d'Applications</div>
          <div class="edu-location">Université Alioune DIOP · Bambey, Diourbel, Sénégal</div>
        </div>
      </div>
    </div>
  </section>

  <!-- GITHUB STATS -->
  <section class="section">
    <div class="section-label" data-num="04">Statistiques GitHub</div>
    <div class="stats-grid animate-in">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=aliou9sow6&show_icons=true&theme=transparent&hide_border=true&include_all_commits=true&title_color=e8c16c&icon_color=7c6af7&text_color=e8e8f0&bg_color=16161f" alt="Stats GitHub" />
      </div>
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aliou9sow6&layout=compact&theme=transparent&hide_border=true&langs_count=8&title_color=e8c16c&text_color=e8e8f0&bg_color=16161f" alt="Langages" />
      </div>
      <div class="stat-card stat-card-wide">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=aliou9sow6&theme=transparent&hide_border=true&ring=e8c16c&fire=7c6af7&currStreakLabel=e8c16c&background=16161f&sideLabels=e8e8f0&dates=7878a0&stroke=2a2a3a" alt="Streak" />
      </div>
    </div>
  </section>

  <!-- QUOTES -->
  <section class="section">
    <div class="section-label" data-num="05">Citations & Inspirations</div>
    <div class="quotes-list animate-in">
      <div class="quote-block">
        <p class="quote-text">La route du savoir est infinie.</p>
        <div class="quote-author">— Anonyme</div>
      </div>
      <div class="quote-block">
        <p class="quote-text">L'agilité est la capacité de s'adapter et de réagir aux changements. La flexibilité et la résilience sont des éléments clés de la réussite des projets agiles.</p>
        <div class="quote-author">— Anonyme</div>
      </div>
      <div class="quote-block">
        <p class="quote-text">Man is a slow, sloppy and brilliant thinker; the machine is fast, accurate and stupid.</p>
        <div class="quote-author">— William M. Kelly</div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section class="section">
    <div class="section-label" data-num="06">Contact</div>
    <div class="contact-grid animate-in">
      <a href="mailto:aliou9sow6@gmail.com" class="contact-card">
        <div class="contact-icon email">✉</div>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-value">aliou9sow6@gmail.com</div>
        </div>
      </a>
      <a href="https://www.linkedin.com/in/aliou-saidou-nourou-sow-054084228/" target="_blank" class="contact-card">
        <div class="contact-icon linkedin">in</div>
        <div>
          <div class="contact-label">LinkedIn</div>
          <div class="contact-value">Aliou Saïd Noor SOW</div>
        </div>
      </a>
      <a href="https://github.com/aliou9sow6" target="_blank" class="contact-card">
        <div class="contact-icon" style="background:rgba(255,255,255,0.07); font-size:20px;">⌥</div>
        <div>
          <div class="contact-label">GitHub</div>
          <div class="contact-value">aliou9sow6</div>
        </div>
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer">
    <p class="footer-text">Fait avec <span>♥</span> au Sénégal · Aliou Saïd Noor SOW</p>
  </footer>

</div>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, i * 80);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.animate-in').forEach(el => observer.observe(el));
</script>
</body>
</html>