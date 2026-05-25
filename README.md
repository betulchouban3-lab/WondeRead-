# WondeRead-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Wonderead — Stories That Stay With You</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Nunito:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #1a1f3a;
    --navy-light: #252b4a;
    --navy-mid: #2e3660;
    --amber: #f0a500;
    --amber-light: #ffc94d;
    --amber-pale: #fff8e7;
    --coral: #e8614a;
    --sage: #6ab89a;
    --cream: #fdf8f0;
    --cream-dark: #f5ede0;
    --text-dark: #1a1f3a;
    --text-mid: #4a5070;
    --text-light: #8a90b0;
    --font-display: 'Playfair Display', Georgia, serif;
    --font-body: 'Nunito', sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: var(--font-body);
    background: var(--cream);
    color: var(--text-dark);
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--amber);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: multiply;
  }
  .cursor.hover { width: 32px; height: 32px; background: var(--amber-light); opacity: 0.6; }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 4rem;
    background: transparent;
    transition: background 0.4s, box-shadow 0.4s;
  }
  nav.scrolled {
    background: rgba(253, 248, 240, 0.95);
    backdrop-filter: blur(12px);
    box-shadow: 0 1px 0 rgba(26,31,58,0.08);
  }
  .nav-logo {
    font-family: var(--font-display);
    font-size: 1.6rem;
    font-weight: 700;
    color: var(--navy);
    text-decoration: none;
    display: flex; align-items: center; gap: 10px;
  }
  .nav-logo .logo-dot {
    width: 10px; height: 10px;
    background: var(--amber);
    border-radius: 50%;
    animation: pulse-dot 2s ease-in-out infinite;
  }
  @keyframes pulse-dot { 0%,100%{transform:scale(1)} 50%{transform:scale(1.4)} }
  .nav-links { display: flex; align-items: center; gap: 2.5rem; }
  .nav-links a {
    font-size: 0.9rem; font-weight: 500;
    color: var(--text-mid);
    text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--navy); }
  .nav-cta {
    background: var(--navy);
    color: var(--cream) !important;
    padding: 0.6rem 1.4rem;
    border-radius: 999px;
    transition: background 0.2s, transform 0.15s !important;
  }
  .nav-cta:hover { background: var(--navy-mid) !important; transform: translateY(-1px); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; align-items: center;
    position: relative;
    overflow: hidden;
    padding: 7rem 4rem 4rem;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 60% at 60% 40%, #e8d5b7 0%, var(--cream) 70%);
    z-index: 0;
  }
  /* Floating orbs */
  .orb {
    position: absolute;
    border-radius: 50%;
    pointer-events: none;
    z-index: 0;
  }
  .orb-1 { width: 500px; height: 500px; background: radial-gradient(circle, rgba(240,165,0,0.15) 0%, transparent 70%); top: -100px; right: -100px; animation: float1 8s ease-in-out infinite; }
  .orb-2 { width: 300px; height: 300px; background: radial-gradient(circle, rgba(106,184,154,0.12) 0%, transparent 70%); bottom: 50px; left: 100px; animation: float2 10s ease-in-out infinite; }
  .orb-3 { width: 200px; height: 200px; background: radial-gradient(circle, rgba(232,97,74,0.1) 0%, transparent 70%); top: 200px; right: 300px; animation: float1 12s ease-in-out infinite reverse; }
  @keyframes float1 { 0%,100%{transform:translateY(0) scale(1)} 50%{transform:translateY(-30px) scale(1.05)} }
  @keyframes float2 { 0%,100%{transform:translateY(0) rotate(0deg)} 50%{transform:translateY(-20px) rotate(5deg)} }

  .hero-content {
    position: relative; z-index: 1;
    max-width: 620px;
    animation: fadeUp 0.9s ease both;
  }
  @keyframes fadeUp { from{opacity:0;transform:translateY(32px)} to{opacity:1;transform:translateY(0)} }

  .hero-eyebrow {
    display: inline-flex; align-items: center; gap: 8px;
    font-size: 0.8rem; font-weight: 600; letter-spacing: 0.12em;
    text-transform: uppercase; color: var(--amber);
    background: rgba(240,165,0,0.1);
    border: 1px solid rgba(240,165,0,0.25);
    padding: 6px 16px; border-radius: 999px;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.9s 0.1s ease both;
  }
  .hero-eyebrow span { width: 6px; height: 6px; background: var(--amber); border-radius: 50%; }

  h1 {
    font-family: var(--font-display);
    font-size: clamp(3rem, 6vw, 5rem);
    font-weight: 900;
    line-height: 1.05;
    color: var(--navy);
    margin-bottom: 1.5rem;
    animation: fadeUp 0.9s 0.2s ease both;
  }
  h1 em {
    font-style: italic;
    color: var(--amber);
  }
  .hero-sub {
    font-size: 1.15rem;
    line-height: 1.7;
    color: var(--text-mid);
    max-width: 480px;
    margin-bottom: 2.5rem;
    animation: fadeUp 0.9s 0.3s ease both;
  }
  .hero-actions {
    display: flex; align-items: center; gap: 1rem; flex-wrap: wrap;
    animation: fadeUp 0.9s 0.4s ease both;
  }
  .btn-primary {
    background: var(--navy);
    color: var(--cream);
    font-family: var(--font-body);
    font-size: 1rem; font-weight: 600;
    padding: 0.9rem 2rem;
    border-radius: 999px;
    border: none; cursor: pointer;
    text-decoration: none;
    display: inline-flex; align-items: center; gap: 8px;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 20px rgba(26,31,58,0.25);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(26,31,58,0.3); }
  .btn-primary .arrow { transition: transform 0.2s; }
  .btn-primary:hover .arrow { transform: translateX(4px); }
  .btn-secondary {
    font-size: 0.95rem; font-weight: 600;
    color: var(--text-mid);
    text-decoration: none;
    display: inline-flex; align-items: center; gap: 6px;
    padding: 0.9rem 0;
    transition: color 0.2s;
  }
  .btn-secondary:hover { color: var(--navy); }
  .hero-trust {
    display: flex; align-items: center; gap: 1rem; margin-top: 3rem;
    animation: fadeUp 0.9s 0.5s ease both;
  }
  .trust-avatars { display: flex; }
  .trust-avatars span {
    width: 34px; height: 34px; border-radius: 50%;
    border: 2px solid var(--cream);
    background: var(--navy-mid);
    color: var(--amber-light);
    font-size: 0.7rem; font-weight: 700;
    display: flex; align-items: center; justify-content: center;
    margin-left: -8px;
  }
  .trust-avatars span:first-child { margin-left: 0; }
  .trust-text { font-size: 0.85rem; color: var(--text-light); line-height: 1.4; }
  .trust-text strong { color: var(--text-mid); }

  /* Hero visual / book mockup */
  .hero-visual {
    position: absolute; right: 4rem; top: 50%; transform: translateY(-50%);
    z-index: 1;
    animation: fadeUp 0.9s 0.3s ease both;
  }
  .book-stack { position: relative; width: 340px; height: 400px; }
  .book {
    position: absolute;
    border-radius: 4px 14px 14px 4px;
    box-shadow: 6px 8px 30px rgba(26,31,58,0.18);
  }
  .book-main {
    width: 220px; height: 300px;
    background: linear-gradient(135deg, var(--navy) 0%, var(--navy-mid) 100%);
    top: 50px; left: 80px;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    padding: 2rem;
    transform: rotate(-3deg);
    transition: transform 0.4s;
  }
  .book-main:hover { transform: rotate(0deg) scale(1.03); }
  .book-main .book-star {
    font-family: var(--font-display);
    font-size: 3rem; color: var(--amber);
    margin-bottom: 0.5rem;
  }
  .book-main .book-title {
    font-family: var(--font-display);
    font-size: 1rem; font-weight: 700; color: var(--cream);
    text-align: center; line-height: 1.3;
    margin-bottom: 0.5rem;
  }
  .book-main .book-line { width: 40px; height: 2px; background: var(--amber); margin: 0.5rem auto; }
  .book-main .book-sub { font-size: 0.7rem; color: rgba(253,248,240,0.5); text-align: center; }
  .book-back {
    width: 200px; height: 280px;
    background: linear-gradient(135deg, var(--coral) 0%, #c0432c 100%);
    top: 80px; left: 40px;
    transform: rotate(-8deg);
  }
  .book-back2 {
    width: 190px; height: 270px;
    background: linear-gradient(135deg, var(--sage) 0%, #3d8f6e 100%);
    top: 90px; left: 120px;
    transform: rotate(6deg);
  }
  /* Floating elements around book */
  .float-el {
    position: absolute;
    font-family: var(--font-display);
    background: white;
    border-radius: 12px;
    padding: 0.6rem 1rem;
    box-shadow: 0 4px 20px rgba(26,31,58,0.1);
    white-space: nowrap;
    pointer-events: none;
  }
  .float-el-1 { top: 0; right: 0; font-size: 0.8rem; color: var(--navy); animation: float2 6s ease-in-out infinite; }
  .float-el-1 strong { color: var(--amber); }
  .float-el-2 { bottom: 30px; left: 0; font-size: 0.8rem; color: var(--navy); animation: float1 7s ease-in-out infinite; }
  .float-el-2 strong { color: var(--sage); }

  /* SECTION COMMON */
  section { padding: 6rem 4rem; }
  .section-tag {
    display: inline-block;
    font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em;
    text-transform: uppercase; color: var(--amber);
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: var(--font-display);
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 700;
    line-height: 1.15;
    color: var(--navy);
    margin-bottom: 1rem;
  }
  .section-sub {
    font-size: 1.05rem;
    color: var(--text-mid);
    line-height: 1.7;
    max-width: 520px;
  }

  /* HOW IT WORKS */
  .how { background: var(--cream-dark); }
  .how-inner { max-width: 1100px; margin: 0 auto; }
  .how-header { text-align: center; margin-bottom: 4rem; }
  .how-header .section-sub { margin: 0 auto; }
  .steps { display: grid; grid-template-columns: repeat(4, 1fr); gap: 2rem; position: relative; }
  .steps::before {
    content: '';
    position: absolute;
    top: 48px; left: calc(12.5% + 24px); right: calc(12.5% + 24px);
    height: 1px;
    background: repeating-linear-gradient(90deg, var(--amber) 0, var(--amber) 8px, transparent 8px, transparent 18px);
    opacity: 0.4;
  }
  .step { text-align: center; }
  .step-num {
    width: 56px; height: 56px;
    background: var(--navy);
    color: var(--amber-light);
    font-family: var(--font-display);
    font-size: 1.4rem; font-weight: 700;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 1.2rem;
    position: relative; z-index: 1;
    box-shadow: 0 4px 16px rgba(26,31,58,0.2);
    transition: transform 0.3s;
  }
  .step:hover .step-num { transform: scale(1.12) rotate(-5deg); }
  .step-title { font-weight: 700; font-size: 1rem; color: var(--navy); margin-bottom: 0.5rem; }
  .step-desc { font-size: 0.9rem; color: var(--text-mid); line-height: 1.6; }

  /* FEATURES */
  .features-inner { max-width: 1100px; margin: 0 auto; }
  .features-header { margin-bottom: 3.5rem; }
  .features-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
  .feature-card {
    background: white;
    border-radius: 20px;
    padding: 2rem;
    border: 1px solid rgba(26,31,58,0.06);
    transition: transform 0.3s, box-shadow 0.3s;
    position: relative; overflow: hidden;
  }
  .feature-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: var(--accent-color, var(--amber));
    transform: scaleX(0); transform-origin: left;
    transition: transform 0.3s;
  }
  .feature-card:hover { transform: translateY(-4px); box-shadow: 0 16px 40px rgba(26,31,58,0.1); }
  .feature-card:hover::before { transform: scaleX(1); }
  .feature-icon {
    width: 52px; height: 52px;
    border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.6rem;
    margin-bottom: 1.2rem;
  }
  .feature-title { font-weight: 700; font-size: 1.05rem; color: var(--navy); margin-bottom: 0.5rem; }
  .feature-desc { font-size: 0.9rem; color: var(--text-mid); line-height: 1.65; }
  .feature-card.large { grid-column: span 2; display: flex; gap: 2rem; align-items: flex-start; }
  .feature-card.large .feature-content { flex: 1; }
  .feature-card.large .feature-visual {
    flex-shrink: 0; width: 160px; height: 120px;
    background: var(--cream-dark); border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 3rem;
  }

  /* MODES */
  .modes { background: var(--navy); padding: 6rem 4rem; }
  .modes-inner { max-width: 1100px; margin: 0 auto; }
  .modes .section-title { color: var(--cream); }
  .modes .section-sub { color: rgba(253,248,240,0.6); }
  .modes-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-top: 3.5rem; }
  .mode-panel {
    border-radius: 24px;
    padding: 2.5rem;
    position: relative; overflow: hidden;
  }
  .mode-panel.adult {
    background: var(--navy-light);
    border: 1px solid rgba(240,165,0,0.2);
  }
  .mode-panel.kids {
    background: linear-gradient(135deg, #2e4a3e 0%, #1a3028 100%);
    border: 1px solid rgba(106,184,154,0.2);
  }
  .mode-badge {
    display: inline-flex; align-items: center; gap: 6px;
    font-size: 0.75rem; font-weight: 700; letter-spacing: 0.1em;
    text-transform: uppercase; padding: 5px 14px; border-radius: 999px;
    margin-bottom: 1.2rem;
  }
  .mode-panel.adult .mode-badge { background: rgba(240,165,0,0.15); color: var(--amber-light); }
  .mode-panel.kids .mode-badge { background: rgba(106,184,154,0.15); color: var(--sage); }
  .mode-name {
    font-family: var(--font-display);
    font-size: 1.8rem; font-weight: 700;
    color: var(--cream); margin-bottom: 1rem;
  }
  .mode-list { list-style: none; }
  .mode-list li {
    font-size: 0.9rem;
    color: rgba(253,248,240,0.7);
    padding: 0.5rem 0;
    border-bottom: 1px solid rgba(253,248,240,0.06);
    display: flex; align-items: center; gap: 10px;
  }
  .mode-list li:last-child { border-bottom: none; }
  .mode-list li::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: var(--accent, var(--amber)); flex-shrink: 0; }
  .mode-panel.kids .mode-list li::before { background: var(--sage); }

  /* PRICING */
  .pricing-inner { max-width: 860px; margin: 0 auto; }
  .pricing-header { text-align: center; margin-bottom: 3.5rem; }
  .pricing-header .section-sub { margin: 0 auto; }
  .pricing-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; }
  .price-card {
    border-radius: 24px;
    padding: 2.5rem;
    position: relative;
  }
  .price-card.free { background: var(--cream-dark); border: 1px solid rgba(26,31,58,0.08); }
  .price-card.premium {
    background: var(--navy);
    color: var(--cream);
    box-shadow: 0 20px 50px rgba(26,31,58,0.25);
    transform: scale(1.02);
  }
  .price-badge {
    position: absolute; top: -12px; left: 50%; transform: translateX(-50%);
    background: var(--amber); color: var(--navy);
    font-size: 0.7rem; font-weight: 700; letter-spacing: 0.1em;
    text-transform: uppercase; padding: 4px 16px; border-radius: 999px;
    white-space: nowrap;
  }
  .price-tier { font-size: 0.8rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 1rem; }
  .price-card.free .price-tier { color: var(--text-light); }
  .price-card.premium .price-tier { color: var(--amber-light); }
  .price-amount {
    font-family: var(--font-display);
    font-size: 3rem; font-weight: 900;
    margin-bottom: 0.25rem;
  }
  .price-card.free .price-amount { color: var(--navy); }
  .price-card.premium .price-amount { color: var(--cream); }
  .price-period { font-size: 0.85rem; margin-bottom: 1.8rem; }
  .price-card.free .price-period { color: var(--text-light); }
  .price-card.premium .price-period { color: rgba(253,248,240,0.5); }
  .price-features { list-style: none; margin-bottom: 2rem; }
  .price-features li {
    font-size: 0.9rem; padding: 0.6rem 0;
    border-bottom: 1px solid rgba(26,31,58,0.06);
    display: flex; align-items: center; gap: 10px;
  }
  .price-card.premium .price-features li { border-color: rgba(253,248,240,0.08); color: rgba(253,248,240,0.85); }
  .price-features li::before { content: '✓'; font-weight: 700; font-size: 0.85rem; }
  .price-card.free .price-features li::before { color: var(--sage); }
  .price-card.premium .price-features li::before { color: var(--amber-light); }
  .price-features li.no { opacity: 0.4; }
  .price-features li.no::before { content: '—'; }
  .btn-price-free {
    display: block; text-align: center; width: 100%;
    padding: 0.9rem; border-radius: 999px;
    background: transparent; border: 2px solid var(--navy);
    color: var(--navy); font-family: var(--font-body);
    font-size: 0.95rem; font-weight: 700;
    cursor: pointer; text-decoration: none;
    transition: background 0.2s, color 0.2s;
  }
  .btn-price-free:hover { background: var(--navy); color: var(--cream); }
  .btn-price-premium {
    display: block; text-align: center; width: 100%;
    padding: 0.9rem; border-radius: 999px;
    background: var(--amber); border: none;
    color: var(--navy); font-family: var(--font-body);
    font-size: 0.95rem; font-weight: 700;
    cursor: pointer; text-decoration: none;
    transition: background 0.2s, transform 0.2s;
  }
  .btn-price-premium:hover { background: var(--amber-light); transform: translateY(-1px); }

  /* TESTIMONIALS */
  .testimonials { background: var(--cream-dark); }
  .testimonials-inner { max-width: 1100px; margin: 0 auto; }
  .testimonials-header { text-align: center; margin-bottom: 3.5rem; }
  .testimonials-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
  .testimonial {
    background: white; border-radius: 20px; padding: 2rem;
    border: 1px solid rgba(26,31,58,0.06);
    position: relative;
  }
  .quote-mark {
    font-family: var(--font-display);
    font-size: 4rem; line-height: 1; color: var(--amber);
    opacity: 0.3; position: absolute; top: 1rem; right: 1.5rem;
  }
  .testimonial-text {
    font-size: 0.95rem; line-height: 1.7; color: var(--text-mid);
    margin-bottom: 1.5rem; font-style: italic;
  }
  .testimonial-author { display: flex; align-items: center; gap: 10px; }
  .author-avatar {
    width: 38px; height: 38px; border-radius: 50%;
    background: var(--navy-mid);
    color: var(--amber-light);
    font-size: 0.75rem; font-weight: 700;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .author-name { font-weight: 700; font-size: 0.9rem; color: var(--navy); }
  .author-role { font-size: 0.8rem; color: var(--text-light); }

  /* CTA */
  .cta-section {
    background: var(--navy);
    text-align: center;
    padding: 7rem 4rem;
    position: relative; overflow: hidden;
  }
  .cta-section::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 70% 60% at 50% 50%, rgba(240,165,0,0.08) 0%, transparent 70%);
  }
  .cta-section .section-title { color: var(--cream); position: relative; z-index: 1; margin-bottom: 1rem; }
  .cta-section .section-sub { color: rgba(253,248,240,0.6); margin: 0 auto 2.5rem; position: relative; z-index: 1; }
  .cta-actions { display: flex; justify-content: center; gap: 1rem; position: relative; z-index: 1; flex-wrap: wrap; }
  .btn-cta {
    background: var(--amber);
    color: var(--navy);
    font-family: var(--font-body);
    font-size: 1.05rem; font-weight: 700;
    padding: 1rem 2.5rem; border-radius: 999px;
    border: none; cursor: pointer;
    text-decoration: none;
    display: inline-flex; align-items: center; gap: 8px;
    transition: transform 0.2s, background 0.2s;
    box-shadow: 0 4px 24px rgba(240,165,0,0.35);
  }
  .btn-cta:hover { background: var(--amber-light); transform: translateY(-2px); }
  .btn-cta-ghost {
    background: transparent;
    color: rgba(253,248,240,0.8);
    font-family: var(--font-body);
    font-size: 1rem; font-weight: 600;
    padding: 1rem 2rem; border-radius: 999px;
    border: 1px solid rgba(253,248,240,0.2); cursor: pointer;
    text-decoration: none;
    transition: border-color 0.2s, color 0.2s;
  }
  .btn-cta-ghost:hover { border-color: rgba(253,248,240,0.5); color: var(--cream); }

  /* FOOTER */
  footer {
    background: var(--navy);
    border-top: 1px solid rgba(253,248,240,0.06);
    padding: 3rem 4rem;
    display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 1.5rem;
  }
  .footer-logo {
    font-family: var(--font-display);
    font-size: 1.3rem; font-weight: 700;
    color: var(--cream);
  }
  .footer-links { display: flex; gap: 2rem; }
  .footer-links a { font-size: 0.85rem; color: rgba(253,248,240,0.45); text-decoration: none; transition: color 0.2s; }
  .footer-links a:hover { color: rgba(253,248,240,0.8); }
  .footer-copy { font-size: 0.8rem; color: rgba(253,248,240,0.3); }

  /* SCROLL ANIMATIONS */
  .reveal { opacity: 0; transform: translateY(24px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
  .reveal-delay-4 { transition-delay: 0.4s; }

  @media (max-width: 900px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .hero { padding: 7rem 1.5rem 4rem; }
    .hero-visual { display: none; }
    section { padding: 4rem 1.5rem; }
    .steps { grid-template-columns: 1fr 1fr; }
    .steps::before { display: none; }
    .features-grid { grid-template-columns: 1fr; }
    .feature-card.large { grid-column: span 1; flex-direction: column; }
    .modes-grid, .pricing-grid, .testimonials-grid { grid-template-columns: 1fr; }
    .price-card.premium { transform: none; }
    .modes { padding: 4rem 1.5rem; }
    footer { padding: 2rem 1.5rem; flex-direction: column; align-items: flex-start; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>

<!-- NAV -->
<nav id="nav">
  <a href="#" class="nav-logo"><div class="logo-dot"></div>Wonderead</a>
  <div class="nav-links">
    <a href="#how">How it works</a>
    <a href="#features">Features</a>
    <a href="#pricing">Pricing</a>
    <a href="#" class="nav-cta">Start free</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>

  <div class="hero-content">
    <div class="hero-eyebrow"><span></span>Stories that stay with you</div>
    <h1>Read together.<br>In <em>your</em> voice.<br>Always.</h1>
    <p class="hero-sub">Wonderead is the family reading platform where AI crafts stories around your child, narrated in your own voice — and saved forever as a family keepsake.</p>
    <div class="hero-actions">
      <a href="#pricing" class="btn-primary">Start for free <span class="arrow">→</span></a>
      <a href="#how" class="btn-secondary">See how it works ↓</a>
    </div>
    <div class="hero-trust">
      <div class="trust-avatars">
        <span>SR</span><span>MK</span><span>JP</span><span>AL</span>
      </div>
      <p class="trust-text"><strong>Join 2,000+ families</strong><br>already reading together</p>
    </div>
  </div>

  <div class="hero-visual">
    <div class="book-stack">
      <div class="book book-back2"></div>
      <div class="book book-back"></div>
      <div class="book book-main">
        <div class="book-star">✦</div>
        <div class="book-title">The Dragon Who Was Afraid of Butterflies</div>
        <div class="book-line"></div>
        <div class="book-sub">A story for Matilda, age 5</div>
      </div>
      <div class="float-el float-el-1">🎙️ Narrated by <strong>Mum</strong></div>
      <div class="float-el float-el-2">✨ <strong>AI-personalized</strong> just for her</div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="how" id="how">
  <div class="how-inner">
    <div class="how-header reveal">
      <div class="section-tag">How it works</div>
      <h2 class="section-title">Four steps to a story<br>they'll never forget</h2>
      <p class="section-sub">From setup to storytime in minutes.</p>
    </div>
    <div class="steps">
      <div class="step reveal reveal-delay-1">
        <div class="step-num">1</div>
        <p class="step-title">Create a child profile</p>
        <p class="step-desc">Add their favorite color, food, characters, and quirks. The more detail, the better the magic.</p>
      </div>
      <div class="step reveal reveal-delay-2">
        <div class="step-num">2</div>
        <p class="step-title">Record your voice</p>
        <p class="step-desc">A short reading sample is all it takes. Your voice becomes the narrator for every personalized story.</p>
      </div>
      <div class="step reveal reveal-delay-3">
        <div class="step-num">3</div>
        <p class="step-title">AI crafts the story</p>
        <p class="step-desc">Our AI weaves their favorites into an original tale — reviewed and refined by real human creators.</p>
      </div>
      <div class="step reveal reveal-delay-4">
        <div class="step-num">4</div>
        <p class="step-title">Read it together</p>
        <p class="step-desc">Listen live, sync with family anywhere, or save it to your family memory library forever.</p>
      </div>
    </div>
  </div>
</section>

<!-- FEATURES -->
<section class="features" id="features">
  <div class="features-inner">
    <div class="features-header reveal">
      <div class="section-tag">Features</div>
      <h2 class="section-title">Everything a reading family needs</h2>
      <p class="section-sub">Built for the bedtime ritual, the long car ride, and every reading moment in between.</p>
    </div>
    <div class="features-grid">
      <div class="feature-card large reveal" style="--accent-color: var(--amber);">
        <div class="feature-content">
          <div class="feature-icon" style="background:#fff8e7;">🎙️</div>
          <h3 class="feature-title">Your voice, their story</h3>
          <p class="feature-desc">Record a short voice sample and Wonderead uses it to narrate every personalized story. Bedtime sounds like you — even when you're far away. A gift that lasts forever as a keepsake.</p>
        </div>
        <div class="feature-visual">🎧</div>
      </div>
      <div class="feature-card reveal reveal-delay-1" style="--accent-color: var(--sage);">
        <div class="feature-icon" style="background:#f0faf5;">✨</div>
        <h3 class="feature-title">AI personalization</h3>
        <p class="feature-desc">Every story is built around your child's world — their name, interests, and personality woven in by AI and refined by human creators.</p>
      </div>
      <div class="feature-card reveal reveal-delay-2" style="--accent-color: var(--coral);">
        <div class="feature-icon" style="background:#fdf2f0;">🌙</div>
        <h3 class="feature-title">Adaptive mood audio</h3>
        <p class="feature-desc">Music shifts automatically — energetic melodies for daytime, soft and calming for bedtime. The app senses the time and the story's tone.</p>
      </div>
      <div class="feature-card reveal" style="--accent-color: var(--amber);">
        <div class="feature-icon" style="background:#fff8e7;">👨‍👩‍👧</div>
        <h3 class="feature-title">Listen together, anywhere</h3>
        <p class="feature-desc">Sync a session with family across the globe. Real-time text and voice chat keeps the story shared, even apart.</p>
      </div>
      <div class="feature-card reveal reveal-delay-1" style="--accent-color: #7c6fcf;">
        <div class="feature-icon" style="background:#f4f3fe;">👋</div>
        <h3 class="feature-title">Interactive prompts</h3>
        <p class="feature-desc">Kids clap, draw, answer, and react — turning passive listening into active play. Great for ages 3–10.</p>
      </div>
      <div class="feature-card reveal reveal-delay-2" style="--accent-color: var(--sage);">
        <div class="feature-icon" style="background:#f0faf5;">📊</div>
        <h3 class="feature-title">Parental insights</h3>
        <p class="feature-desc">Themed reports on your child's reading habits — with real conversation starters sent straight to your inbox.</p>
      </div>
    </div>
  </div>
</section>

<!-- MODES -->
<section class="modes" id="modes">
  <div class="modes-inner">
    <div class="reveal">
      <div class="section-tag">Designed for everyone</div>
      <h2 class="section-title">Two modes.<br>One safe space.</h2>
      <p class="section-sub">Wonderead adapts to who's reading — a fully controlled kids environment, or the full adult platform.</p>
    </div>
    <div class="modes-grid">
      <div class="mode-panel adult reveal reveal-delay-1">
        <div class="mode-badge">👤 Adult mode</div>
        <h3 class="mode-name">Your command center</h3>
        <ul class="mode-list">
          <li>Math-based age gate for access</li>
          <li>Manage all child profiles & settings</li>
          <li>Record your voice for narration</li>
          <li>Full content library + premium features</li>
          <li>Parental insights & activity reports</li>
          <li>Gift stories to friends & family</li>
        </ul>
      </div>
      <div class="mode-panel kids reveal reveal-delay-2">
        <div class="mode-badge">🌟 Kids mode</div>
        <h3 class="mode-name">Safe, simple, delightful</h3>
        <ul class="mode-list">
          <li>Age-only login — no personal data collected</li>
          <li>Parental consent required to activate</li>
          <li>Family-controlled content filters</li>
          <li>One-tap parental settings panel</li>
          <li>Interactive story prompts & games</li>
          <li>Bedtime & daytime story modes</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing" id="pricing">
  <div class="pricing-inner">
    <div class="pricing-header reveal">
      <div class="section-tag">Simple pricing</div>
      <h2 class="section-title">Stories for every family</h2>
      <p class="section-sub">Start free with a world of classic stories. Unlock the full magic with a monthly membership.</p>
    </div>
    <div class="pricing-grid reveal">
      <div class="price-card free">
        <div class="price-tier">Free forever</div>
        <div class="price-amount">€0</div>
        <div class="price-period">No credit card needed</div>
        <ul class="price-features">
          <li>Public domain classic stories</li>
          <li>Kids mode access</li>
          <li>Basic listening & reading</li>
          <li>Discussion forums</li>
          <li class="no">Parent voice narration</li>
          <li class="no">AI-personalized stories</li>
          <li class="no">Family memory library</li>
          <li class="no">Sync listening sessions</li>
        </ul>
        <a href="#" class="btn-price-free">Get started free</a>
      </div>
      <div class="price-card premium">
        <div class="price-badge">Most popular</div>
        <div class="price-tier">Wonderead Plus</div>
        <div class="price-amount">€7.99</div>
        <div class="price-period">per month · cancel anytime</div>
        <ul class="price-features">
          <li>Everything in Free</li>
          <li>Parent voice narration</li>
          <li>Unlimited AI-personalized stories</li>
          <li>Family memory library & keepsakes</li>
          <li>Synchronized family listening</li>
          <li>Adaptive mood audio</li>
          <li>Parental insights & reports</li>
          <li>Story gifting</li>
        </ul>
        <a href="#" class="btn-price-premium">Start free 14-day trial</a>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="testimonials">
  <div class="testimonials-inner">
    <div class="testimonials-header reveal">
      <div class="section-tag">Families love it</div>
      <h2 class="section-title">What parents are saying</h2>
    </div>
    <div class="testimonials-grid">
      <div class="testimonial reveal reveal-delay-1">
        <div class="quote-mark">"</div>
        <p class="testimonial-text">My daughter asks for her Wonderead story every single night. Hearing bedtime stories in my voice — even on nights I travel — makes me emotional every time.</p>
        <div class="testimonial-author">
          <div class="author-avatar">SR</div>
          <div><div class="author-name">Sophie R.</div><div class="author-role">Mum of two, Berlin</div></div>
        </div>
      </div>
      <div class="testimonial reveal reveal-delay-2">
        <div class="quote-mark">"</div>
        <p class="testimonial-text">The personalized stories are incredible. Our son is obsessed with dinosaurs — the AI wrote him a story where a T-Rex helped him find his missing sock. He's asked for it 30 times.</p>
        <div class="testimonial-author">
          <div class="author-avatar">MK</div>
          <div><div class="author-name">Marcus K.</div><div class="author-role">Dad, Amsterdam</div></div>
        </div>
      </div>
      <div class="testimonial reveal reveal-delay-3">
        <div class="quote-mark">"</div>
        <p class="testimonial-text">We're a bilingual family and finding quality content in both languages has always been a struggle. Wonderead finally gets us.</p>
        <div class="testimonial-author">
          <div class="author-avatar">AL</div>
          <div><div class="author-name">Amara L.</div><div class="author-role">Parent, London</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section">
  <h2 class="section-title">Your child's story<br>is waiting to be told.</h2>
  <p class="section-sub">Start with free classics. Record your voice. Watch the wonder begin.</p>
  <div class="cta-actions">
    <a href="#" class="btn-cta">Start for free →</a>
    <a href="#" class="btn-cta-ghost">See a sample story</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Wonderead</div>
  <div class="footer-links">
    <a href="#">Privacy</a>
    <a href="#">Terms</a>
    <a href="#">For Creators</a>
    <a href="#">Blog</a>
    <a href="#">Contact</a>
  </div>
  <div class="footer-copy">© 2026 Wonderead. Made with love for families.</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
  });
  document.querySelectorAll('a, button, .book-main').forEach(el => {
    el.addEventListener('mouseenter', () => cursor.classList.add('hover'));
    el.addEventListener('mouseleave', () => cursor.classList.remove('hover'));
  });

  // Nav scroll state
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 40);
  });

  // Scroll reveal
  const revealEls = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.12 });
  revealEls.forEach(el => observer.observe(el));
</script>
</body>
</html>
