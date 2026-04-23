<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gagandeep Singh — Lead Developer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0a0a0b;
      --bg2: #111114;
      --bg3: #18181d;
      --border: rgba(255,255,255,0.08);
      --border-hover: rgba(255,255,255,0.16);
      --text: #f0efe8;
      --muted: #888885;
      --accent: #5DCAA5;
      --accent2: #AFA9EC;
      --accent3: #F0997B;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-size: 16px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* ── Noise overlay ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 0;
      opacity: 0.4;
    }

    /* ── Nav ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.25rem 4rem;
      border-bottom: 1px solid var(--border);
      background: rgba(10,10,11,0.85);
      backdrop-filter: blur(12px);
    }

    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.1rem;
      letter-spacing: -0.02em;
      color: var(--text);
      text-decoration: none;
    }
    .nav-logo span { color: var(--accent); }

    .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.85rem;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      font-family: 'DM Mono', monospace;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--text); }

    .nav-cta {
      font-family: 'DM Mono', monospace;
      font-size: 0.8rem;
      padding: 0.5rem 1.25rem;
      border: 1px solid var(--accent);
      color: var(--accent);
      border-radius: 2px;
      text-decoration: none;
      letter-spacing: 0.04em;
      transition: background 0.2s, color 0.2s;
    }
    .nav-cta:hover { background: var(--accent); color: #0a0a0b; }

    /* ── Hero ── */
    #hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 8rem 4rem 4rem;
      position: relative;
      overflow: hidden;
    }

    .hero-grid-bg {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(93,202,165,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(93,202,165,0.04) 1px, transparent 1px);
      background-size: 64px 64px;
      mask-image: radial-gradient(ellipse 80% 60% at 50% 0%, black 30%, transparent 100%);
    }

    .hero-orb {
      position: absolute;
      width: 700px;
      height: 700px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(93,202,165,0.12) 0%, transparent 70%);
      top: -200px;
      right: -100px;
      pointer-events: none;
    }

    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      font-family: 'DM Mono', monospace;
      font-size: 0.75rem;
      color: var(--accent);
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-bottom: 1.5rem;
    }
    .hero-tag::before {
      content: '';
      display: inline-block;
      width: 6px; height: 6px;
      border-radius: 50%;
      background: var(--accent);
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.5; transform: scale(0.8); }
    }

    h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(3rem, 7vw, 6rem);
      font-weight: 800;
      line-height: 1.0;
      letter-spacing: -0.03em;
      margin-bottom: 1.5rem;
    }
    h1 em {
      font-style: normal;
      color: transparent;
      -webkit-text-stroke: 1px rgba(255,255,255,0.3);
    }
    h1 .accent-word { color: var(--accent); }

    .hero-sub {
      max-width: 540px;
      color: var(--muted);
      font-size: 1.05rem;
      margin-bottom: 2.5rem;
      line-height: 1.8;
    }

    .hero-actions {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
    }

    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.875rem 2rem;
      background: var(--accent);
      color: #0a0a0b;
      font-family: 'DM Mono', monospace;
      font-size: 0.85rem;
      font-weight: 500;
      letter-spacing: 0.03em;
      text-decoration: none;
      border-radius: 2px;
      transition: opacity 0.2s, transform 0.2s;
    }
    .btn-primary:hover { opacity: 0.9; transform: translateY(-1px); }

    .btn-ghost {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.875rem 2rem;
      border: 1px solid var(--border-hover);
      color: var(--text);
      font-family: 'DM Mono', monospace;
      font-size: 0.85rem;
      letter-spacing: 0.03em;
      text-decoration: none;
      border-radius: 2px;
      transition: border-color 0.2s, background 0.2s;
    }
    .btn-ghost:hover { border-color: var(--text); background: rgba(255,255,255,0.04); }

    .hero-stats {
      display: flex;
      gap: 3rem;
      margin-top: 5rem;
      padding-top: 3rem;
      border-top: 1px solid var(--border);
    }
    .stat-num {
      font-family: 'Syne', sans-serif;
      font-size: 2.5rem;
      font-weight: 800;
      color: var(--text);
    }
    .stat-num span { color: var(--accent); }
    .stat-label {
      font-size: 0.8rem;
      color: var(--muted);
      font-family: 'DM Mono', monospace;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      margin-top: 0.25rem;
    }

    /* ── Sections ── */
    section {
      padding: 6rem 4rem;
      position: relative;
    }

    .section-label {
      font-family: 'DM Mono', monospace;
      font-size: 0.75rem;
      color: var(--accent);
      letter-spacing: 0.12em;
      text-transform: uppercase;
      margin-bottom: 1rem;
    }

    h2 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 800;
      letter-spacing: -0.02em;
      line-height: 1.1;
      margin-bottom: 3rem;
    }

    /* ── About ── */
    #about {
      background: var(--bg2);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
    }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 5rem;
      align-items: center;
    }

    .about-text p {
      color: var(--muted);
      font-size: 1.05rem;
      margin-bottom: 1.25rem;
    }
    .about-text p strong { color: var(--text); font-weight: 500; }

    .about-meta {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
    .meta-row {
      display: flex;
      align-items: center;
      gap: 1rem;
      padding: 1rem 1.25rem;
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: 4px;
    }
    .meta-icon {
      width: 36px; height: 36px;
      border-radius: 50%;
      background: rgba(93,202,165,0.1);
      display: flex; align-items: center; justify-content: center;
      font-size: 0.9rem;
      flex-shrink: 0;
    }
    .meta-label { font-size: 0.75rem; color: var(--muted); font-family: 'DM Mono', monospace; }
    .meta-val { font-size: 0.95rem; color: var(--text); font-weight: 500; }

    /* ── Skills ── */
    #skills { background: var(--bg); }

    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
      border-radius: 4px;
      overflow: hidden;
    }

    .skill-card {
      background: var(--bg);
      padding: 2rem;
      transition: background 0.2s;
    }
    .skill-card:hover { background: var(--bg3); }

    .skill-icon {
      font-family: 'DM Mono', monospace;
      font-size: 0.7rem;
      color: var(--accent);
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-bottom: 0.75rem;
    }
    .skill-card h3 {
      font-family: 'Syne', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
    }
    .skill-card p { font-size: 0.875rem; color: var(--muted); line-height: 1.6; }

    /* ── Experience ── */
    #experience {
      background: var(--bg2);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
    }

    .exp-timeline { position: relative; }
    .exp-timeline::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0; bottom: 0;
      width: 1px;
      background: var(--border);
    }

    .exp-item {
      padding: 0 0 3.5rem 3rem;
      position: relative;
    }
    .exp-item::before {
      content: '';
      position: absolute;
      left: -4px;
      top: 6px;
      width: 9px; height: 9px;
      border-radius: 50%;
      background: var(--accent);
      box-shadow: 0 0 0 3px rgba(93,202,165,0.2);
    }

    .exp-period {
      font-family: 'DM Mono', monospace;
      font-size: 0.75rem;
      color: var(--accent);
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }
    .exp-role {
      font-family: 'Syne', sans-serif;
      font-size: 1.4rem;
      font-weight: 700;
      margin-bottom: 0.25rem;
    }
    .exp-company {
      font-size: 0.9rem;
      color: var(--muted);
      margin-bottom: 1rem;
    }
    .exp-bullets {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
    .exp-bullets li {
      font-size: 0.9rem;
      color: var(--muted);
      padding-left: 1.2rem;
      position: relative;
      line-height: 1.6;
    }
    .exp-bullets li::before {
      content: '→';
      position: absolute;
      left: 0;
      color: var(--accent);
      font-size: 0.8rem;
    }

    /* ── Projects ── */
    #projects { background: var(--bg); }

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.5rem;
    }

    .project-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: 4px;
      padding: 2rem;
      transition: border-color 0.2s, transform 0.2s;
      position: relative;
      overflow: hidden;
    }
    .project-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(93,202,165,0.04) 0%, transparent 60%);
      opacity: 0;
      transition: opacity 0.3s;
    }
    .project-card:hover { border-color: rgba(93,202,165,0.3); transform: translateY(-3px); }
    .project-card:hover::before { opacity: 1; }

    .project-tag {
      display: inline-block;
      font-family: 'DM Mono', monospace;
      font-size: 0.7rem;
      padding: 3px 10px;
      border-radius: 2px;
      margin-bottom: 1rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }
    .tag-mobile { background: rgba(175,169,236,0.12); color: var(--accent2); }
    .tag-ai { background: rgba(93,202,165,0.12); color: var(--accent); }
    .tag-fintech { background: rgba(240,153,123,0.12); color: var(--accent3); }
    .tag-health { background: rgba(93,202,165,0.08); color: #5DCAA5; }
    .tag-auth { background: rgba(175,169,236,0.08); color: var(--accent2); }
    .tag-hospitality { background: rgba(240,153,123,0.08); color: var(--accent3); }

    .project-card h3 {
      font-family: 'Syne', sans-serif;
      font-size: 1.15rem;
      font-weight: 700;
      margin-bottom: 0.75rem;
    }
    .project-card p {
      font-size: 0.875rem;
      color: var(--muted);
      line-height: 1.65;
    }

    /* ── Tech Tags ── */
    .tech-cloud {
      display: flex;
      flex-wrap: wrap;
      gap: 0.6rem;
      margin-top: 2.5rem;
    }
    .tech-tag {
      font-family: 'DM Mono', monospace;
      font-size: 0.75rem;
      padding: 0.4rem 0.9rem;
      border: 1px solid var(--border);
      border-radius: 2px;
      color: var(--muted);
      letter-spacing: 0.03em;
      transition: border-color 0.2s, color 0.2s;
    }
    .tech-tag:hover { border-color: var(--accent); color: var(--accent); }

    /* ── Contact ── */
    #contact {
      background: var(--bg2);
      border-top: 1px solid var(--border);
      text-align: center;
    }
    #contact h2 { margin-bottom: 1rem; }
    #contact .sub {
      color: var(--muted);
      max-width: 480px;
      margin: 0 auto 3rem;
      font-size: 1rem;
    }

    .contact-links {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
      margin-bottom: 4rem;
    }

    .contact-chip {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      padding: 0.75rem 1.5rem;
      border: 1px solid var(--border);
      border-radius: 2px;
      color: var(--text);
      text-decoration: none;
      font-family: 'DM Mono', monospace;
      font-size: 0.8rem;
      letter-spacing: 0.04em;
      transition: border-color 0.2s, background 0.2s;
    }
    .contact-chip:hover { border-color: var(--accent); color: var(--accent); background: rgba(93,202,165,0.05); }

    /* ── Footer ── */
    footer {
      padding: 2rem 4rem;
      border-top: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-family: 'DM Mono', monospace;
      font-size: 0.75rem;
      color: var(--muted);
    }

    /* ── Animations ── */
    .fade-up {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .fade-up.visible { opacity: 1; transform: translateY(0); }

    /* ── Responsive ── */
    @media (max-width: 900px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      section { padding: 4rem 1.5rem; }
      #hero { padding: 7rem 1.5rem 3rem; }
      .about-grid { grid-template-columns: 1fr; gap: 2.5rem; }
      .hero-stats { gap: 2rem; flex-wrap: wrap; }
      footer { padding: 1.5rem; flex-direction: column; gap: 0.5rem; text-align: center; }
    }

    @media (max-width: 600px) {
      .stat-num { font-size: 2rem; }
      .hero-actions { flex-direction: column; }
      .btn-primary, .btn-ghost { justify-content: center; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <a href="#hero" class="nav-logo">GS<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="mailto:iamgagan22@gmail.com" class="nav-cta">Hire Me</a>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-grid-bg"></div>
    <div class="hero-orb"></div>

    <div class="hero-tag">Available for new opportunities</div>

    <h1>
      Gagandeep<br/>
      <em>Singh</em><br/>
      <span class="accent-word">Lead</span> Dev.
    </h1>

    <p class="hero-sub">
      Engineering Lead with <strong>11+ years</strong> building scalable mobile platforms, AI-driven solutions, and leading cross-functional teams. Specialised in Android, system architecture &amp; healthcare tech.
    </p>

    <div class="hero-actions">
      <a href="#projects" class="btn-primary">View My Work →</a>
      <a href="mailto:iamgagan22@gmail.com" class="btn-ghost">Get In Touch</a>
    </div>

    <div class="hero-stats">
      <div>
        <div class="stat-num">11<span>+</span></div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div>
        <div class="stat-num">15<span>+</span></div>
        <div class="stat-label">Engineers Led</div>
      </div>
      <div>
        <div class="stat-num">6<span>+</span></div>
        <div class="stat-label">Major Products</div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="fade-up">
      <div class="about-grid">
        <div class="about-text">
          <div class="section-label">// About</div>
          <h2>Architect.<br/>Leader.<br/>Builder.</h2>
          <p>I'm an Engineering Lead who has spent over a decade turning complex problems into elegant mobile solutions. From fintech and healthcare to hospitality and dating platforms — I've shipped products that millions of people rely on.</p>
          <p>As a <strong>Solution Architect</strong>, I collaborate directly with international clients to define technical roadmaps and design scalable systems. I'm deeply hands-on with modern AI development workflows including <strong>Cursor</strong> and <strong>Antigravity</strong>, and currently building AI voice agents and conversational automation systems.</p>
          <p>I believe great software is built by great teams — I mentor engineers, lead sprints, and sweat every architecture decision.</p>
        </div>
        <div class="about-meta">
          <div class="meta-row">
            <div class="meta-icon">📍</div>
            <div>
              <div class="meta-label">Location</div>
              <div class="meta-val">Ambala Cantt, Haryana</div>
            </div>
          </div>
          <div class="meta-row">
            <div class="meta-icon">🏢</div>
            <div>
              <div class="meta-label">Current Role</div>
              <div class="meta-val">Lead Developer @ SmartData Enterprises</div>
            </div>
          </div>
          <div class="meta-row">
            <div class="meta-icon">🎓</div>
            <div>
              <div class="meta-label">Education</div>
              <div class="meta-val">B.Tech Computer Science (2010–2013)</div>
            </div>
          </div>
          <div class="meta-row">
            <div class="meta-icon">🌐</div>
            <div>
              <div class="meta-label">Languages</div>
              <div class="meta-val">English, Hindi, Punjabi</div>
            </div>
          </div>
          <div class="meta-row">
            <div class="meta-icon">📧</div>
            <div>
              <div class="meta-label">Email</div>
              <div class="meta-val">iamgagan22@gmail.com</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="fade-up">
      <div class="section-label">// Skills</div>
      <h2>What I Build With</h2>

      <div class="skills-grid">
        <div class="skill-card">
          <div class="skill-icon">01 / Mobile</div>
          <h3>Android Development</h3>
          <p>Kotlin, Java, Jetpack Compose — crafting high-performance native Android apps from architecture to production.</p>
        </div>
        <div class="skill-card">
          <div class="skill-icon">02 / AI</div>
          <h3>AI &amp; Voice Agents</h3>
          <p>Building conversational AI systems, inbound/outbound voice agents, and AI-assisted development workflows using Cursor &amp; Antigravity.</p>
        </div>
        <div class="skill-card">
          <div class="skill-icon">03 / Cloud</div>
          <h3>AWS &amp; Backend</h3>
          <p>EC2, S3, RDS, IAM, Lambda, Amplify, Rekognition — designing secure, scalable cloud infrastructure.</p>
        </div>
        <div class="skill-card">
          <div class="skill-icon">04 / Integrations</div>
          <h3>APIs &amp; SDKs</h3>
          <p>REST APIs, Firebase, WebSockets, BLE device communication, payment gateways, QR payments &amp; third-party SDK integrations.</p>
        </div>
        <div class="skill-card">
          <div class="skill-icon">05 / Architecture</div>
          <h3>Solution Architecture</h3>
          <p>Collaborating with international clients to define technical architecture, product strategy, and scalable system design.</p>
        </div>
        <div class="skill-card">
          <div class="skill-icon">06 / Leadership</div>
          <h3>Team &amp; Delivery</h3>
          <p>Agile/Scrum delivery, managing 10–15 engineer teams, sprint planning, code reviews, and technical mentorship.</p>
        </div>
      </div>

      <div class="tech-cloud">
        <span class="tech-tag">Kotlin</span>
        <span class="tech-tag">Java</span>
        <span class="tech-tag">Jetpack Compose</span>
        <span class="tech-tag">Android SDK</span>
        <span class="tech-tag">Firebase</span>
        <span class="tech-tag">REST APIs</span>
        <span class="tech-tag">WebSockets</span>
        <span class="tech-tag">AWS EC2</span>
        <span class="tech-tag">AWS S3</span>
        <span class="tech-tag">AWS Lambda</span>
        <span class="tech-tag">AWS Rekognition</span>
        <span class="tech-tag">Amplify</span>
        <span class="tech-tag">BLE / IoT</span>
        <span class="tech-tag">Cursor AI</span>
        <span class="tech-tag">OpenTok</span>
        <span class="tech-tag">Agile / Scrum</span>
        <span class="tech-tag">Voice AI</span>
        <span class="tech-tag">Conversational AI</span>
        <span class="tech-tag">Payment Gateways</span>
        <span class="tech-tag">Biometrics</span>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience">
    <div class="fade-up">
      <div class="section-label">// Experience</div>
      <h2>Career Timeline</h2>

      <div class="exp-timeline">
        <div class="exp-item">
          <div class="exp-period">Sep 2017 — Present</div>
          <div class="exp-role">Lead Developer / Technical Lead</div>
          <div class="exp-company">SmartData Enterprises Ltd. · Sahibzada Ajit Singh Nagar</div>
          <ul class="exp-bullets">
            <li>Lead mobile development initiatives and architect scalable applications across security, healthcare, hospitality, and social platforms.</li>
            <li>Collaborate with international clients as a Solution Architect to refine product ideas and define technical architecture.</li>
            <li>Manage engineering teams of 10–15, sprint planning, and end-to-end project delivery.</li>
            <li>Drive AI-assisted development workflows to improve engineering productivity.</li>
            <li>Ensure code quality through reviews, performance optimisation, and scalable architecture decisions.</li>
          </ul>
        </div>

        <div class="exp-item">
          <div class="exp-period">Jun 2014 — Sep 2017</div>
          <div class="exp-role">Android Application Developer</div>
          <div class="exp-company">Ameba Softwares Pvt. Ltd.</div>
          <ul class="exp-bullets">
            <li>Developed and maintained multiple native Android applications using Java, delivering scalable, high-performance mobile solutions.</li>
            <li>Implemented REST API integrations, push notifications, and third-party SDKs across various apps.</li>
            <li>Collaborated with UI/UX designers, backend developers, and QA teams to deliver production-ready applications.</li>
            <li>Participated in architecture discussions, code reviews, and release cycles to ensure quality mobile apps.</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="fade-up">
      <div class="section-label">// Projects</div>
      <h2>Selected Work</h2>

      <div class="projects-grid">
        <div class="project-card">
          <span class="project-tag tag-auth">Auth / Security</span>
          <h3>LegitimatelyU Platform</h3>
          <p>Solution architect for a revolutionary identity protection app. Implemented Voice Match, Facial Match, and biometric authentication for complete digital identity security.</p>
        </div>
        <div class="project-card">
          <span class="project-tag tag-mobile">Social / Dating</span>
          <h3>TapDating / SeeMe</h3>
          <p>Led end-to-end development of a real-time dating platform with OpenTok video calling, social login, location-based matching, and push notification systems.</p>
        </div>
        <div class="project-card">
          <span class="project-tag tag-health">Healthcare</span>
          <h3>NAHA / CareNow</h3>
          <p>Built healthcare apps integrating BLE medical devices — glucometer, BP monitor, pulse oximeter — with secure health data workflows and real-time patient monitoring.</p>
        </div>
        <div class="project-card">
          <span class="project-tag tag-hospitality">Hospitality</span>
          <h3>Go Hotel Life</h3>
          <p>Led development of a hotel guest experience application featuring service requests, personalised guest features, and full backend integrations.</p>
        </div>
        <div class="project-card">
          <span class="project-tag tag-fintech">Fintech</span>
          <h3>xCash Apps</h3>
          <p>Led development of fintech applications supporting QR payments, secure authentication, and transaction analytics with merchant management features.</p>
        </div>
        <div class="project-card">
          <span class="project-tag tag-ai">AI / Automation</span>
          <h3>AI Voice Agents</h3>
          <p>Currently managing AI-powered voice automation systems including inbound/outbound call agents and conversational workflow automation.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="fade-up">
      <div class="section-label">// Contact</div>
      <h2>Let's Build Together</h2>
      <p class="sub">Open to exciting opportunities, consulting work, and interesting architectural challenges. Let's connect.</p>

      <div class="contact-links">
        <a href="mailto:iamgagan22@gmail.com" class="contact-chip">
          ✉ iamgagan22@gmail.com
        </a>
        <a href="tel:9034777022" class="contact-chip">
          📞 9034777022
        </a>
        <a href="https://www.linkedin.com/in/iamgagan22/" target="_blank" rel="noopener" class="contact-chip">
          in LinkedIn
        </a>
        <a href="https://github.com/gagansmartdata" target="_blank" rel="noopener" class="contact-chip">
          ⌥ GitHub
        </a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <span>© 2025 Gagandeep Singh</span>
    <span>Lead Developer · Ambala Cantt, Haryana</span>
  </footer>

  <script>
    // Intersection observer for fade-up animations
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

    // Smooth active state on nav
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-links a');
    window.addEventListener('scroll', () => {
      let current = '';
      sections.forEach(s => {
        if (window.scrollY >= s.offsetTop - 120) current = s.id;
      });
      navLinks.forEach(a => {
        a.style.color = a.getAttribute('href') === '#' + current ? '#f0efe8' : '';
      });
    });
  </script>
</body>
</html>
