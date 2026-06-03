<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jermiah Booker — Frontend UI Engineer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&family=Outfit:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0d0d0d;
    --surface: #161616;
    --border: #2a2a2a;
    --accent: #a855f7;
    --accent-dim: #7c3aed;
    --text: #f0ede6;
    --muted: #888;
    --serif: 'DM Serif Display', Georgia, serif;
    --mono: 'DM Mono', monospace;
    --sans: 'Outfit', sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-weight: 300;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* GRID LINES BACKGROUND */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(168,85,247,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(168,85,247,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.25rem 3rem;
    border-bottom: 1px solid var(--border);
    background: rgba(13,13,13,0.85);
    backdrop-filter: blur(12px);
  }

  .nav-logo {
    font-family: var(--mono);
    font-size: 0.85rem;
    color: var(--accent);
    letter-spacing: 0.08em;
    text-decoration: none;
  }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-family: var(--mono);
    font-size: 0.78rem;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--accent); }

  /* HERO */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: flex-end;
    padding: 8rem 3rem 5rem;
    z-index: 1;
  }

  .hero-content { max-width: 900px; }

  .hero-tag {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-family: var(--mono);
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 2rem;
  }

  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 24px;
    height: 1px;
    background: var(--accent);
  }

  .hero h1 {
    font-family: var(--serif);
    font-size: clamp(3.5rem, 9vw, 8rem);
    line-height: 0.95;
    font-weight: 400;
    color: var(--text);
    margin-bottom: 2.5rem;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .hero-desc {
    max-width: 520px;
    font-size: 1rem;
    color: var(--muted);
    line-height: 1.8;
    margin-bottom: 3rem;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    align-items: center;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: var(--accent);
    color: #ffffff;
    font-family: var(--mono);
    font-size: 0.8rem;
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    text-decoration: none;
    padding: 0.85rem 1.75rem;
    transition: background 0.2s, transform 0.2s;
  }

  .btn-primary:hover { background: #b76ef9; transform: translateY(-2px); }

  .btn-ghost {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    border: 1px solid var(--border);
    color: var(--muted);
    font-family: var(--mono);
    font-size: 0.8rem;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    text-decoration: none;
    padding: 0.85rem 1.75rem;
    transition: border-color 0.2s, color 0.2s;
  }

  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); }

  /* MARQUEE */
  .marquee-wrap {
    position: relative;
    z-index: 1;
    overflow: hidden;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 1rem 0;
    background: var(--surface);
  }

  .marquee-track {
    display: flex;
    gap: 3rem;
    animation: marquee 24s linear infinite;
    width: max-content;
  }

  .marquee-item {
    font-family: var(--mono);
    font-size: 0.75rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    white-space: nowrap;
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .marquee-item span {
    color: var(--accent);
    font-size: 0.6rem;
  }

  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  /* SECTION */
  section {
    position: relative;
    z-index: 1;
    padding: 6rem 3rem;
  }

  .section-label {
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--accent);
    letter-spacing: 0.14em;
    text-transform: uppercase;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .section-label::after {
    content: '';
    flex: 1;
    max-width: 60px;
    height: 1px;
    background: var(--accent);
    opacity: 0.4;
  }

  .section-title {
    font-family: var(--serif);
    font-size: clamp(2rem, 4vw, 3.5rem);
    font-weight: 400;
    line-height: 1.1;
    margin-bottom: 4rem;
    color: var(--text);
  }

  /* ABOUT */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .about-text p {
    color: var(--muted);
    line-height: 1.9;
    margin-bottom: 1.5rem;
  }

  .about-text p strong { color: var(--text); font-weight: 400; }

  .stat-row {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    border-left: 1px solid var(--border);
    padding-left: 3rem;
  }

  .stat {
    display: flex;
    flex-direction: column;
  }

  .stat-num {
    font-family: var(--serif);
    font-size: 3rem;
    color: var(--accent);
    line-height: 1;
  }

  .stat-label {
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-top: 0.25rem;
  }

  /* SKILLS */
  .skills-section { background: var(--surface); }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1px;
    border: 1px solid var(--border);
  }

  .skill-cell {
    padding: 1.75rem;
    border: 1px solid var(--border);
    transition: background 0.2s;
  }

  .skill-cell:hover { background: rgba(200,245,87,0.04); }

  .skill-icon {
    font-size: 1.5rem;
    margin-bottom: 0.75rem;
    display: block;
  }

  .skill-name {
    font-family: var(--mono);
    font-size: 0.82rem;
    color: var(--text);
    letter-spacing: 0.04em;
    margin-bottom: 0.25rem;
  }

  .skill-type {
    font-size: 0.72rem;
    color: var(--muted);
  }

  /* PROJECTS */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
    gap: 1px;
    border: 1px solid var(--border);
  }

  .project-card {
    background: var(--surface);
    padding: 2rem;
    border: 1px solid var(--border);
    text-decoration: none;
    color: inherit;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    transition: background 0.25s, border-color 0.25s;
    position: relative;
    overflow: hidden;
  }

  .project-card::after {
    content: '→';
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    font-family: var(--mono);
    font-size: 1rem;
    color: var(--muted);
    transition: color 0.2s, transform 0.2s;
  }

  .project-card:hover {
    background: rgba(200,245,87,0.05);
    border-color: var(--accent-dim);
  }

  .project-card:hover::after {
    color: var(--accent);
    transform: translate(2px, -2px);
  }

  .project-num {
    font-family: var(--mono);
    font-size: 0.68rem;
    color: var(--muted);
    letter-spacing: 0.1em;
  }

  .project-title {
    font-family: var(--serif);
    font-size: 1.4rem;
    font-weight: 400;
    color: var(--text);
    line-height: 1.2;
  }

  .project-desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.7;
  }

  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: auto;
  }

  .tag {
    font-family: var(--mono);
    font-size: 0.68rem;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    padding: 0.3rem 0.65rem;
    border: 1px solid var(--border);
    color: var(--muted);
  }

  .project-card:hover .tag { border-color: rgba(200,245,87,0.25); }

  /* CONTACT */
  .contact-section { background: var(--surface); }

  .contact-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .contact-text p {
    color: var(--muted);
    line-height: 1.9;
    margin-bottom: 2rem;
  }

  .contact-links {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: 1rem;
    color: var(--muted);
    text-decoration: none;
    font-family: var(--mono);
    font-size: 0.82rem;
    letter-spacing: 0.04em;
    padding: 1rem 1.25rem;
    border: 1px solid var(--border);
    transition: color 0.2s, border-color 0.2s;
  }

  .contact-link:hover { color: var(--accent); border-color: var(--accent-dim); }

  .contact-link-icon { font-size: 1.1rem; }

  /* FOOTER */
  footer {
    position: relative;
    z-index: 1;
    padding: 2rem 3rem;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  footer p {
    font-family: var(--mono);
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.06em;
  }

  /* ANIMATIONS */
  .fade-up {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .fade-up.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* MOBILE */
  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { gap: 1.5rem; }
    .hero { padding: 7rem 1.5rem 4rem; }
    section { padding: 4rem 1.5rem; }
    .about-grid, .contact-inner { grid-template-columns: 1fr; gap: 2.5rem; }
    .stat-row { border-left: none; border-top: 1px solid var(--border); padding-left: 0; padding-top: 2rem; flex-direction: row; flex-wrap: wrap; gap: 2rem; }
    .projects-grid { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 0.5rem; text-align: center; padding: 1.5rem; }
  }
</style>
</head>
<body>

<nav>
  <a href="#" class="nav-logo">JB.dev</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-content">
    <div class="hero-tag">Frontend UI Engineer · Minnesota · Open to Remote</div>
    <h1>Jermiah<br><em>Booker</em></h1>
    <p class="hero-desc">
      Building fast, intuitive, and responsive web interfaces.
      Passionate about clean UI, smooth interactions, and production‑ready code.
      Currently leveling up with React, TypeScript &amp; Node.js.
    </p>
    <div class="hero-actions">
      <a href="#projects" class="btn-primary">View Projects ↓</a>
      <a href="https://www.linkedin.com/in/jermiah-booker" target="_blank" class="btn-ghost">LinkedIn →</a>
      <a href="https://github.com/tony34x" target="_blank" class="btn-ghost">GitHub →</a>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track">
    <div class="marquee-item">JavaScript <span>✦</span></div>
    <div class="marquee-item">React <span>✦</span></div>
    <div class="marquee-item">HTML5 <span>✦</span></div>
    <div class="marquee-item">CSS3 <span>✦</span></div>
    <div class="marquee-item">Node.js <span>✦</span></div>
    <div class="marquee-item">TypeScript <span>✦</span></div>
    <div class="marquee-item">Git <span>✦</span></div>
    <div class="marquee-item">Figma <span>✦</span></div>
    <div class="marquee-item">Webpack <span>✦</span></div>
    <div class="marquee-item">Tailwind <span>✦</span></div>
    <div class="marquee-item">Netlify <span>✦</span></div>
    <div class="marquee-item">Vercel <span>✦</span></div>
    <!-- duplicate for seamless loop -->
    <div class="marquee-item">JavaScript <span>✦</span></div>
    <div class="marquee-item">React <span>✦</span></div>
    <div class="marquee-item">HTML5 <span>✦</span></div>
    <div class="marquee-item">CSS3 <span>✦</span></div>
    <div class="marquee-item">Node.js <span>✦</span></div>
    <div class="marquee-item">TypeScript <span>✦</span></div>
    <div class="marquee-item">Git <span>✦</span></div>
    <div class="marquee-item">Figma <span>✦</span></div>
    <div class="marquee-item">Webpack <span>✦</span></div>
    <div class="marquee-item">Tailwind <span>✦</span></div>
    <div class="marquee-item">Netlify <span>✦</span></div>
    <div class="marquee-item">Vercel <span>✦</span></div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-label">01 — About</div>
  <h2 class="section-title">Who I am</h2>
  <div class="about-grid">
    <div class="about-text fade-up">
      <p>I'm a <strong>Frontend UI Engineer</strong> based in Minnesota, currently in the TripleTen Software Engineering bootcamp and actively building production-ready web applications.</p>
      <p>My focus is on creating interfaces that feel as good as they look — <strong>responsive, accessible, and fast</strong>. I care deeply about the details: smooth transitions, consistent spacing, and code that other developers can actually read.</p>
      <p>I'm expanding into full-stack development with <strong>Node.js and TypeScript</strong>, and I'm actively seeking remote roles where I can contribute and grow.</p>
    </div>
    <div class="stat-row fade-up" style="transition-delay: 0.15s;">
      <div class="stat">
        <span class="stat-num">7+</span>
        <span class="stat-label">Projects shipped</span>
      </div>
      <div class="stat">
        <span class="stat-num">8+</span>
        <span class="stat-label">Technologies used</span>
      </div>
      <div class="stat">
        <span class="stat-num">100%</span>
        <span class="stat-label">Remote-ready</span>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" class="skills-section">
  <div class="section-label">02 — Skills</div>
  <h2 class="section-title">Tools of the trade</h2>
  <div class="skills-grid">
    <div class="skill-cell fade-up"><span class="skill-icon">⚡</span><div class="skill-name">JavaScript</div><div class="skill-type">Language</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🔷</span><div class="skill-name">TypeScript</div><div class="skill-type">Language</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">⚛️</span><div class="skill-name">React</div><div class="skill-type">Framework</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🌐</span><div class="skill-name">HTML5</div><div class="skill-type">Markup</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🎨</span><div class="skill-name">CSS3</div><div class="skill-type">Styling</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">💨</span><div class="skill-name">Tailwind</div><div class="skill-type">CSS Framework</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🟢</span><div class="skill-name">Node.js</div><div class="skill-type">Backend (learning)</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🗄️</span><div class="skill-name">MySQL</div><div class="skill-type">Database</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🔧</span><div class="skill-name">Git &amp; GitHub</div><div class="skill-type">Version Control</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">📦</span><div class="skill-name">Webpack</div><div class="skill-type">Bundler</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🎭</span><div class="skill-name">Figma</div><div class="skill-type">Design</div></div>
    <div class="skill-cell fade-up"><span class="skill-icon">🚀</span><div class="skill-name">Netlify / Vercel</div><div class="skill-type">Deployment</div></div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label">03 — Projects</div>
  <h2 class="section-title">Selected work</h2>
  <div class="projects-grid">

    <a class="project-card fade-up" href="https://userprofilemanager2.netlify.app" target="_blank">
      <div class="project-num">01</div>
      <div class="project-title">User Profile Manager</div>
      <p class="project-desc">Modern interface for viewing and editing user profiles with dynamic updates and a fully responsive layout. Built with real-world UX patterns.</p>
      <div class="project-tags">
        <span class="tag">JavaScript</span>
        <span class="tag">CSS</span>
        <span class="tag">API</span>
        <span class="tag">Netlify</span>
      </div>
    </a>

    <a class="project-card fade-up" href="https://github.com/tony34x/se_project_todo-app" target="_blank" style="transition-delay: 0.07s;">
      <div class="project-num">02</div>
      <div class="project-title">Task Manager App</div>
      <p class="project-desc">Interactive JavaScript app for creating, tracking, and completing tasks with local data persistence. Focused on usability and clean state management.</p>
      <div class="project-tags">
        <span class="tag">JavaScript</span>
        <span class="tag">LocalStorage</span>
        <span class="tag">DOM</span>
      </div>
    </a>

    <a class="project-card fade-up" href="https://project-2-sandy-beta.vercel.app" target="_blank" style="transition-delay: 0.14s;">
      <div class="project-num">03</div>
      <div class="project-title">Portfolio Landing Page</div>
      <p class="project-desc">Card-based personal portfolio showcasing professional introduction and project highlights. Built to pixel-perfect design specs with clean HTML &amp; CSS.</p>
      <div class="project-tags">
        <span class="tag">HTML</span>
        <span class="tag">CSS</span>
        <span class="tag">Vercel</span>
      </div>
    </a>

    <a class="project-card fade-up" href="https://project-1-stage-3.vercel.app" target="_blank" style="transition-delay: 0.21s;">
      <div class="project-num">04</div>
      <div class="project-title">Triple Peaks Library</div>
      <p class="project-desc">Fully responsive webpage built to match a professional design brief using semantic HTML and CSS. Demonstrated strong attention to layout precision.</p>
      <div class="project-tags">
        <span class="tag">HTML</span>
        <span class="tag">CSS</span>
        <span class="tag">Responsive</span>
      </div>
    </a>

    <a class="project-card fade-up" href="https://coffeeshoplandingpage3.netlify.app" target="_blank" style="transition-delay: 0.28s;">
      <div class="project-num">05</div>
      <div class="project-title">Coffeeshop Landing Page</div>
      <p class="project-desc">Visually polished static site following a professional design brief. Demonstrates clean layout construction and consistent visual hierarchy.</p>
      <div class="project-tags">
        <span class="tag">HTML</span>
        <span class="tag">CSS</span>
        <span class="tag">Netlify</span>
      </div>
    </a>

    <a class="project-card fade-up" href="https://github.com/tony34x/project_spots" target="_blank" style="transition-delay: 0.35s;">
      <div class="project-num">06</div>
      <div class="project-title">Project Spots</div>
      <p class="project-desc">A clean web interface for managing and updating user profiles with editable sections and a user-friendly UI focused on smooth interaction flows.</p>
      <div class="project-tags">
        <span class="tag">CSS</span>
        <span class="tag">JavaScript</span>
        <span class="tag">UX</span>
      </div>
    </a>

    <a class="project-card fade-up" href="https://github.com/tony34x/se_project_react" target="_blank" style="transition-delay: 0.42s;">
      <div class="project-num">07</div>
      <div class="project-title">WTWR — What to Wear?</div>
      <p class="project-desc">React app that fetches live weather data and recommends clothing based on current conditions. Displays real-time temperature and location, and filters clothing cards dynamically by weather type.</p>
      <div class="project-tags">
        <span class="tag">React</span>
        <span class="tag">Weather API</span>
        <span class="tag">Components</span>
        <span class="tag">State</span>
      </div>
    </a>

  </div>
</section>

<!-- CONTACT -->
<section id="contact" class="contact-section">
  <div class="section-label">04 — Contact</div>
  <h2 class="section-title">Let's build<br>something together</h2>
  <div class="contact-inner">
    <div class="contact-text fade-up">
      <p>I'm actively seeking remote frontend or full-stack roles. If you're building something interesting and need a developer who cares about the craft, reach out — I'd love to hear from you.</p>
      <a href="mailto:bookerjermiah8@gmail.com" class="btn-primary">Send an Email →</a>
    </div>
    <div class="contact-links fade-up" style="transition-delay: 0.1s;">
      <a href="https://www.linkedin.com/in/jermiah-booker" target="_blank" class="contact-link">
        <span class="contact-link-icon">💼</span>
        linkedin.com/in/jermiah-booker
      </a>
      <a href="https://github.com/tony34x" target="_blank" class="contact-link">
        <span class="contact-link-icon">🐙</span>
        github.com/tony34x
      </a>
      <a href="mailto:bookerjermiah8@gmail.com" class="contact-link">
        <span class="contact-link-icon">✉️</span>
        bookerjermiah8@gmail.com
      </a>
      <a href="https://vercel.com/tony34xs-projects" target="_blank" class="contact-link">
        <span class="contact-link-icon">▲</span>
        vercel.com/tony34xs-projects
      </a>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 Jermiah Booker</p>
  <p>Frontend UI Engineer · Minnesota</p>
</footer>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.12 });

  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
</script>

</body>
</html>
