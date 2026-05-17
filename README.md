<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Muhammad Ajim — Silent Hustler</title>
  <link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@300;400;500&family=Syne:wght@400;500;600;700&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #f7f6f3; --bg2: #f0efe9; --ink: #141414; --muted: #7a7a70;
      --gold: #c9a84c; --border: #e0dfd8; --card: #ffffff;
      --mono: 'DM Mono', monospace; --sans: 'DM Sans', sans-serif; --display: 'Syne', sans-serif;
      --wa: #25D366; --shadow: 0 4px 24px rgba(0,0,0,0.07);
    }
    [data-theme="dark"] {
      --bg: #0e0e0e; --bg2: #151515; --ink: #f0efe9; --muted: #888880;
      --border: #2a2a2a; --card: #1a1a1a; --shadow: 0 4px 24px rgba(0,0,0,0.4);
    }

    html { scroll-behavior: smooth; }
    body { background: var(--bg); color: var(--ink); font-family: var(--sans); font-size: 16px; line-height: 1.6; -webkit-font-smoothing: antialiased; transition: background 0.3s, color 0.3s; }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 200;
      display: flex; justify-content: space-between; align-items: center;
      padding: 1.1rem 3rem;
      background: rgba(247,246,243,0.88); backdrop-filter: blur(14px);
      border-bottom: 1px solid var(--border); transition: background 0.3s, border-color 0.3s;
    }
    [data-theme="dark"] nav { background: rgba(14,14,14,0.88); }
    .nav-logo { font-family: var(--mono); font-size: 0.82rem; letter-spacing: 0.1em; color: var(--ink); text-decoration: none; }
    .nav-right { display: flex; align-items: center; gap: 2rem; }
    .nav-links { display: flex; gap: 1.8rem; list-style: none; }
    .nav-links a { font-size: 0.82rem; color: var(--muted); text-decoration: none; letter-spacing: 0.04em; transition: color 0.2s; }
    .nav-links a:hover { color: var(--ink); }
    .dark-toggle { background: none; border: 1px solid var(--border); border-radius: 20px; padding: 0.3rem 0.75rem; cursor: pointer; font-size: 0.78rem; color: var(--muted); transition: border-color 0.2s, color 0.2s; }
    .dark-toggle:hover { border-color: var(--gold); color: var(--gold); }

    section { padding: 7rem 3rem; max-width: 960px; margin: 0 auto; }

    /* HERO */
    #hero { min-height: 100vh; display: flex; flex-direction: column; justify-content: center; padding-top: 6rem; position: relative; opacity: 0; animation: fadeUp 0.9s 0.15s forwards; }
    .hero-top { display: flex; align-items: center; gap: 2.5rem; margin-bottom: 2rem; }
    .hero-photo-placeholder { width: 100px; height: 100px; border-radius: 50%; border: 2px solid var(--gold); background: linear-gradient(135deg, #1a1a1a 60%, #333); display: flex; flex-direction: column; align-items: center; justify-content: center; flex-shrink: 0; gap: 4px; }
    .hero-photo-placeholder span { font-size: 1.8rem; }
    .hero-photo-placeholder small { font-family: var(--mono); font-size: 0.5rem; color: #999; letter-spacing: 0.06em; }
    .hero-tag { font-family: var(--mono); font-size: 0.75rem; color: var(--gold); letter-spacing: 0.14em; text-transform: uppercase; margin-bottom: 0.6rem; }
    .hero-name { font-family: var(--display); font-size: clamp(2.6rem, 6vw, 4.8rem); font-weight: 700; line-height: 1.05; letter-spacing: -0.02em; margin-bottom: 1.1rem; }
    .hero-name span { color: var(--gold); }
    .hero-desc { font-size: 1rem; color: var(--muted); max-width: 500px; margin-bottom: 2rem; font-weight: 300; line-height: 1.8; }
    .hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; }
    .btn-primary { display: inline-flex; align-items: center; gap: 0.5rem; background: var(--ink); color: var(--bg); font-family: var(--mono); font-size: 0.78rem; letter-spacing: 0.08em; padding: 0.75rem 1.5rem; border-radius: 4px; text-decoration: none; transition: background 0.2s, transform 0.2s; border: none; cursor: pointer; }
    .btn-primary:hover { background: var(--gold); color: #fff; transform: translateY(-2px); }
    .btn-outline { display: inline-flex; align-items: center; gap: 0.5rem; border: 1px solid var(--border); color: var(--ink); font-family: var(--mono); font-size: 0.78rem; letter-spacing: 0.08em; padding: 0.75rem 1.5rem; border-radius: 4px; text-decoration: none; transition: border-color 0.2s, color 0.2s, transform 0.2s; }
    .btn-outline:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }
    .hero-scroll { position: absolute; bottom: 2.5rem; left: 3rem; font-family: var(--mono); font-size: 0.68rem; color: var(--muted); letter-spacing: 0.1em; writing-mode: vertical-rl; display: flex; align-items: center; gap: 0.8rem; }
    .hero-scroll::before { content: ''; display: block; width: 1px; height: 48px; background: var(--muted); animation: scrollLine 2s ease-in-out infinite; }
    @keyframes scrollLine { 0%,100%{opacity:0.3;} 50%{opacity:1;} }

    /* COUNTERS */
    #counters { background: var(--ink); color: var(--bg); padding: 3.5rem 3rem; max-width: 100%; }
    [data-theme="dark"] #counters { background: #0a0a0a; border-top: 1px solid var(--border); }
    .counters-inner { max-width: 960px; margin: 0 auto; display: grid; grid-template-columns: repeat(4,1fr); gap: 2rem; text-align: center; }
    .counter-num { font-family: var(--display); font-size: 2.5rem; font-weight: 700; line-height: 1; margin-bottom: 0.4rem; color: var(--gold); }
    .counter-label { font-family: var(--mono); font-size: 0.7rem; letter-spacing: 0.1em; opacity: 0.55; }

    .section-label { font-family: var(--mono); font-size: 0.72rem; letter-spacing: 0.16em; color: var(--gold); text-transform: uppercase; margin-bottom: 2.5rem; }

    /* ABOUT */
    #about { border-top: 1px solid var(--border); }
    .about-grid { display: grid; grid-template-columns: 160px 1fr; gap: 4rem; align-items: start; }
    .about-photo-wrap { display: flex; flex-direction: column; align-items: center; gap: 0.8rem; }
    .about-photo { width: 150px; height: 190px; border-radius: 6px; background: linear-gradient(160deg,#1c1c1c,#2e2e2e); display: flex; flex-direction: column; align-items: center; justify-content: center; border: 1px solid var(--border); gap: 8px; }
    .about-photo span { font-size: 2.5rem; }
    .about-photo small { font-family: var(--mono); font-size: 0.58rem; color: #888; text-align: center; line-height: 1.6; }
    .about-photo-hint { font-family: var(--mono); font-size: 0.62rem; color: var(--muted); text-align: center; line-height: 1.6; }
    .about-text { font-size: 0.98rem; color: var(--muted); font-weight: 300; line-height: 1.85; }
    .about-text p+p { margin-top: 1rem; }
    .about-text strong { color: var(--ink); font-weight: 500; }
    .skills-list { display: flex; flex-direction: column; gap: 0.5rem; margin-top: 1.8rem; }
    .skill-item { display: flex; justify-content: space-between; align-items: center; padding: 0.65rem 1rem; background: var(--card); border: 1px solid var(--border); border-radius: 4px; font-family: var(--mono); font-size: 0.78rem; transition: border-color 0.2s, transform 0.2s; }
    .skill-item:hover { border-color: var(--gold); transform: translateX(4px); }
    .skill-tag { font-size: 0.65rem; color: var(--muted); letter-spacing: 0.06em; }

    /* PROJECTS */
    #projects { border-top: 1px solid var(--border); }
    .projects-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.4rem; }
    .project-card { background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 1.75rem; text-decoration: none; color: inherit; transition: border-color 0.25s, transform 0.25s, box-shadow 0.25s; display: block; position: relative; overflow: hidden; }
    .project-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: var(--gold); transform: scaleX(0); transform-origin: left; transition: transform 0.3s; }
    .project-card:hover::before { transform: scaleX(1); }
    .project-card:hover { border-color: var(--gold); transform: translateY(-4px); box-shadow: var(--shadow); }
    .project-icon { font-size: 1.8rem; margin-bottom: 0.8rem; }
    .project-num { font-family: var(--mono); font-size: 0.68rem; color: var(--muted); margin-bottom: 0.5rem; }
    .project-title { font-family: var(--display); font-size: 1rem; font-weight: 600; margin-bottom: 0.6rem; }
    .project-desc { font-size: 0.86rem; color: var(--muted); font-weight: 300; line-height: 1.7; margin-bottom: 1.1rem; }
    .project-tags { display: flex; gap: 0.5rem; flex-wrap: wrap; }
    .tag { font-family: var(--mono); font-size: 0.68rem; color: var(--gold); background: rgba(201,168,76,0.08); border: 1px solid rgba(201,168,76,0.25); border-radius: 3px; padding: 0.18rem 0.5rem; }

    /* TESTIMONIALS */
    #testimonials { border-top: 1px solid var(--border); background: var(--bg2); max-width: 100%; padding: 5rem 3rem; }
    .testimonials-inner { max-width: 960px; margin: 0 auto; }
    .testimonials-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.4rem; }
    .testimonial-card { background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 1.5rem; }
    .testimonial-quote { font-size: 2.2rem; color: var(--gold); line-height: 1; margin-bottom: 0.7rem; }
    .testimonial-text { font-size: 0.87rem; color: var(--muted); line-height: 1.75; margin-bottom: 1.1rem; font-weight: 300; }
    .testimonial-author { font-family: var(--mono); font-size: 0.75rem; color: var(--ink); }
    .testimonial-role { font-family: var(--mono); font-size: 0.67rem; color: var(--muted); }

    /* NEWSLETTER */
    #newsletter { border-top: 1px solid var(--border); text-align: center; }
    .newsletter-inner { max-width: 520px; margin: 0 auto; }
    .newsletter-heading { font-family: var(--display); font-size: clamp(1.6rem,3.5vw,2.4rem); font-weight: 700; margin-bottom: 0.8rem; }
    .newsletter-sub { font-size: 0.92rem; color: var(--muted); margin-bottom: 2rem; font-weight: 300; }
    .newsletter-form { display: flex; gap: 0.75rem; }
    .newsletter-form input { flex: 1; padding: 0.85rem 1.2rem; border: 1px solid var(--border); border-radius: 4px; background: var(--card); color: var(--ink); font-family: var(--sans); font-size: 0.9rem; outline: none; transition: border-color 0.2s; }
    .newsletter-form input:focus { border-color: var(--gold); }
    .newsletter-form input::placeholder { color: var(--muted); }
    .newsletter-form button { padding: 0.85rem 1.5rem; background: var(--gold); color: #fff; border: none; border-radius: 4px; font-family: var(--mono); font-size: 0.78rem; letter-spacing: 0.08em; cursor: pointer; transition: opacity 0.2s, transform 0.2s; }
    .newsletter-form button:hover { opacity: 0.85; transform: translateY(-1px); }
    .newsletter-note { font-family: var(--mono); font-size: 0.68rem; color: var(--muted); margin-top: 1rem; }

    /* CONTACT */
    #contact { border-top: 1px solid var(--border); }
    .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; }
    .contact-heading { font-family: var(--display); font-size: clamp(1.6rem,3.5vw,2.6rem); font-weight: 700; letter-spacing: -0.01em; margin-bottom: 0.8rem; }
    .contact-sub { font-size: 0.92rem; color: var(--muted); margin-bottom: 2rem; font-weight: 300; line-height: 1.8; }
    .contact-links { display: flex; flex-direction: column; gap: 0.7rem; }
    .contact-link { display: flex; align-items: center; gap: 1rem; font-family: var(--mono); font-size: 0.78rem; color: var(--ink); text-decoration: none; padding: 0.85rem 1.1rem; border: 1px solid var(--border); border-radius: 4px; background: var(--card); transition: border-color 0.2s, color 0.2s, transform 0.2s; }
    .contact-link:hover { border-color: var(--gold); color: var(--gold); transform: translateX(5px); }
    .contact-link.wa:hover { border-color: var(--wa); color: var(--wa); }
    .contact-link-label { color: var(--muted); font-size: 0.67rem; letter-spacing: 0.08em; margin-left: auto; }

    /* CLOSING */
    #closing { background: var(--ink); color: var(--bg); text-align: center; padding: 6rem 3rem; max-width: 100%; }
    [data-theme="dark"] #closing { background: #050505; }
    .closing-inner { max-width: 640px; margin: 0 auto; }
    .closing-tag { font-family: var(--mono); font-size: 0.72rem; letter-spacing: 0.14em; color: var(--gold); text-transform: uppercase; margin-bottom: 1.5rem; }
    .closing-heading { font-family: var(--display); font-size: clamp(2rem,5vw,3.5rem); font-weight: 700; line-height: 1.1; margin-bottom: 1rem; }
    .closing-sub { font-size: 0.95rem; opacity: 0.5; margin-bottom: 2.5rem; font-weight: 300; line-height: 1.8; }
    .closing-motto { font-family: var(--mono); font-size: 0.8rem; letter-spacing: 0.1em; color: var(--gold); margin-top: 3rem; opacity: 0.75; }

    footer { text-align: center; padding: 1.8rem; font-family: var(--mono); font-size: 0.68rem; color: var(--muted); border-top: 1px solid var(--border); letter-spacing: 0.06em; }

    @keyframes fadeUp { from{opacity:0;transform:translateY(24px);} to{opacity:1;transform:translateY(0);} }
    .reveal { opacity: 0; transform: translateY(20px); transition: opacity 0.75s ease, transform 0.75s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    @media (max-width: 700px) {
      nav { padding: 1rem 1.2rem; }
      .nav-links { display: none; }
      section { padding: 5rem 1.4rem; }
      #counters, #testimonials, #closing { padding: 3.5rem 1.4rem; }
      .counters-inner { grid-template-columns: repeat(2,1fr); }
      .about-grid, .projects-grid, .testimonials-grid, .contact-grid { grid-template-columns: 1fr; gap: 2rem; }
      .hero-top { flex-direction: column; align-items: flex-start; gap: 1.2rem; }
      .hero-scroll { display: none; }
      .newsletter-form { flex-direction: column; }
    }
  </style>
</head>
<body>

  <nav>
    <a class="nav-logo" href="#hero">EG.dev</a>
    <div class="nav-right">
      <ul class="nav-links">
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Work</a></li>
        <li><a href="#testimonials">Reviews</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
      <button class="dark-toggle" onclick="toggleDark()" id="darkBtn">🌙 Dark</button>
    </div>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-top">
      <img 
