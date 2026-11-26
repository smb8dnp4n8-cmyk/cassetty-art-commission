# cassetty-art-commission
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#f4ebd9" />
  <meta name="description" content="Vintage-style art commission and waitlist website." />
  <title>Maison Moth — Art Commissions</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            parchment: '#f4ebd9',
            parchmentDeep: '#e9d8b9',
            ink: '#2c1e16',
            sepia: '#8e5e3b',
            rust: '#a65332',
            sage: '#68715d',
            gold: '#bd8b43'
          },
          fontFamily: {
            display: ['Playfair Display', 'Georgia', 'serif'],
            serif: ['Cormorant Garamond', 'Georgia', 'serif'],
            sans: ['DM Sans', 'Arial', 'sans-serif'],
            hand: ['Caveat', 'cursive']
          },
          boxShadow: {
            paper: '0 22px 60px rgba(66, 43, 25, .14), 0 3px 8px rgba(66, 43, 25, .08)',
            ink: '0 3px 0 rgba(44, 30, 22, .13)'
          }
        }
      }
    }
  </script>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@500;600;700&family=Cormorant+Garamond:wght@400;500;600;700&family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@500;600;700;800&display=swap" rel="stylesheet" />
  <style>
    :root {
      --parchment: #f4ebd9;
      --parchment-deep: #e9d8b9;
      --ink: #2c1e16;
      --muted: #735f4d;
      --sepia: #8e5e3b;
      --rust: #a65332;
      --sage: #68715d;
      --gold: #bd8b43;
      --line: rgba(44, 30, 22, .48);
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      color: var(--ink);
      background:
        radial-gradient(circle at 13% 19%, rgba(184, 135, 71, .12) 0 1px, transparent 1.8px),
        radial-gradient(circle at 74% 62%, rgba(91, 59, 33, .1) 0 1px, transparent 1.6px),
        linear-gradient(135deg, rgba(255, 255, 255, .22), transparent 31%, rgba(130, 91, 52, .06) 66%, transparent),
        var(--parchment);
      background-size: 22px 22px, 28px 28px, auto, auto;
      font-family: 'DM Sans', Arial, sans-serif;
      overflow-x: hidden;
    }

    ::selection { color: var(--parchment); background: var(--rust); }
    button, input, textarea { font: inherit; }
    button { cursor: pointer; }

    .site-shell {
      position: relative;
      width: min(1180px, calc(100% - 32px));
      margin: 0 auto;
    }

    .site-shell::before,
    .site-shell::after {
      content: '';
      position: absolute;
      z-index: -1;
      width: 160px;
      height: 160px;
      opacity: .33;
      pointer-events: none;
      background-image: radial-gradient(var(--sepia) 1.1px, transparent 1.1px);
      background-size: 13px 13px;
      mask-image: linear-gradient(135deg, black, transparent 72%);
    }
    .site-shell::before { top: 110px; left: -115px; }
    .site-shell::after { right: -115px; bottom: 180px; transform: rotate(180deg); }

    .paper-card {
      background: rgba(250, 243, 228, .79);
      border: 1px solid rgba(44, 30, 22, .53);
      box-shadow: 0 22px 60px rgba(66, 43, 25, .11), 0 3px 8px rgba(66, 43, 25, .06);
      position: relative;
    }
    .paper-card::before {
      content: '';
      pointer-events: none;
      position: absolute;
      inset: 5px;
      border: 1px dashed rgba(142, 94, 59, .52);
    }
    .paper-card > * { position: relative; z-index: 1; }

    .double-rule {
      border-top: 3px double rgba(44, 30, 22, .74);
      border-bottom: 1px solid rgba(44, 30, 22, .52);
    }

    .eyebrow {
      letter-spacing: .22em;
      text-transform: uppercase;
      font-size: .68rem;
      font-weight: 700;
      color: var(--sepia);
    }

    .hand-label {
      font-family: 'Caveat', cursive;
      color: var(--rust);
      font-size: 1.55rem;
      line-height: 1;
      transform: rotate(-3deg);
      display: inline-block;
    }

    .nav-link { transition: color .2s ease, transform .2s ease; }
    .nav-link:hover { color: var(--rust); transform: translateY(-1px); }

    .stamp {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      border: 1px solid currentColor;
      padding: .4rem .68rem;
      color: var(--rust);
      letter-spacing: .13em;
      text-transform: uppercase;
      font-size: .63rem;
      font-weight: 700;
      transform: rotate(-4deg);
      background: rgba(255, 251, 240, .35);
    }

    .hero-illustration {
      filter: sepia(.22) saturate(.84) contrast(.95);
      mix-blend-mode: multiply;
      opacity: .84;
    }

    .price-chart {
      min-height: 680px;
      position: relative;
      overflow: hidden;
      background:
        linear-gradient(90deg, transparent 0, rgba(255,255,255,.19) 49%, transparent 50%),
        radial-gradient(ellipse at center, rgba(191, 144, 80, .11), transparent 64%);
    }

    .chart-grid {
      position: absolute;
      inset: 0;
      background-image: linear-gradient(rgba(44,30,22,.055) 1px, transparent 1px), linear-gradient(90deg, rgba(44,30,22,.045) 1px, transparent 1px);
      background-size: 100% 48px, 48px 100%;
      opacity: .42;
      mask-image: radial-gradient(ellipse at center, black 33%, transparent 85%);
    }

    .chart-art-wrap {
      position: absolute;
      inset: 70px 25% 34px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .chart-art-wrap img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      object-position: center;
    }

    .chart-header {
      position: absolute;
      z-index: 4;
      top: 20px;
      left: 9%;
      right: 9%;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      text-align: center;
      font-family: 'Playfair Display', serif;
      font-size: .8rem;
      letter-spacing: .12em;
      text-transform: uppercase;
    }
    .chart-header span { padding: .48rem; border-bottom: 1px solid var(--line); }
    .chart-header span:first-child { color: var(--sepia); }
    .chart-header span:last-child { color: var(--rust); }

    .chart-line {
      position: absolute;
      z-index: 5;
      left: 8%;
      right: 8%;
      display: grid;
      grid-template-columns: minmax(100px, 1fr) minmax(210px, 2fr) minmax(100px, 1fr);
      align-items: center;
      gap: .5rem;
      pointer-events: none;
    }
    .chart-line::before {
      content: '';
      position: absolute;
      left: 0;
      right: 0;
      top: 50%;
      border-top: 1px dashed rgba(44, 30, 22, .61);
      z-index: -1;
    }
    .level-name {
      justify-self: start;
      display: inline-flex;
      align-items: center;
      gap: .3rem;
      background: rgba(244, 235, 217, .92);
      border: 1px solid rgba(44, 30, 22, .58);
      padding: .34rem .5rem;
      font-family: 'Playfair Display', serif;
      font-size: .86rem;
      white-space: nowrap;
      box-shadow: 2px 2px 0 rgba(44, 30, 22, .08);
    }
    .level-name::before { content: '✦'; color: var(--rust); font-size: .65rem; }
    .price-pills {
      grid-column: 3;
      justify-self: end;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: .28rem;
      background: rgba(244, 235, 217, .93);
      padding: .3rem;
      border: 1px solid rgba(44, 30, 22, .58);
      box-shadow: 2px 2px 0 rgba(44, 30, 22, .08);
      min-width: 150px;
    }
    .price-pill { text-align: center; font-size: .72rem; font-weight: 700; white-space: nowrap; }
    .price-pill:first-child { color: var(--sepia); }
    .price-pill:last-child { color: var(--rust); border-left: 1px solid rgba(44,30,22,.2); }
    .price-pill small { display: block; color: var(--muted); font-size: .51rem; text-transform: uppercase; letter-spacing: .08em; font-weight: 700; }

    .order-rule li { position: relative; padding-left: 1.95rem; }
    .order-rule li::before {
      content: attr(data-step);
      position: absolute;
      left: 0;
      top: .08rem;
      width: 1.35rem;
      height: 1.35rem;
      display: grid;
      place-items: center;
      border: 1px solid var(--sepia);
      border-radius: 999px;
      color: var(--rust);
      font-family: 'Playfair Display', serif;
      font-weight: 700;
      font-size: .73rem;
      background: rgba(255,255,255,.22);
    }

    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(1.7rem, 4vw, 2.55rem);
      line-height: .95;
      font-weight: 700;
    }

    .rule-list li { display: flex; gap: .7rem; align-items: flex-start; padding: .42rem 0; border-bottom: 1px dashed rgba(44,30,22,.24); font-family: 'Cormorant Garamond', serif; font-size: 1.12rem; }
    .rule-list li:last-child { border-bottom: 0; }
    .rule-list .yes { color: var(--sage); font-size: 1.15rem; font-weight: 700; }
    .rule-list .no { color: var(--rust); font-size: 1.15rem; font-weight: 700; }

    .field-label { display: block; margin-bottom: .4rem; font-size: .68rem; font-weight: 700; letter-spacing: .13em; text-transform: uppercase; color: var(--sepia); }
    .vintage-input {
      width: 100%;
      color: var(--ink);
      background: rgba(255,255,255,.27);
      border: 1px solid rgba(44,30,22,.58);
      border-radius: 0;
      padding: .78rem .85rem;
      outline: none;
      transition: box-shadow .2s ease, background .2s ease, border-color .2s ease;
    }
    .vintage-input:focus { border-color: var(--rust); background: rgba(255,255,255,.48); box-shadow: 3px 3px 0 rgba(166,83,50,.15); }
    .vintage-input::placeholder { color: rgba(115,95,77,.63); }
    .vintage-input:disabled { opacity: .58; cursor: not-allowed; }

    .choice-card { position: relative; }
    .choice-card input { position: absolute; opacity: 0; pointer-events: none; }
    .choice-card label {
      display: flex;
      height: 100%;
      flex-direction: column;
      justify-content: center;
      gap: .16rem;
      border: 1px solid rgba(44,30,22,.5);
      background: rgba(255,255,255,.22);
      padding: .82rem .7rem;
      cursor: pointer;
      transition: all .2s ease;
    }
    .choice-card label:hover { background: rgba(255,255,255,.55); transform: translateY(-2px); }
    .choice-card input:checked + label { background: rgba(182, 132, 69, .15); border-color: var(--rust); box-shadow: inset 0 0 0 2px rgba(166,83,50,.14), 3px 3px 0 rgba(44,30,22,.1); }
    .choice-card input:focus-visible + label { outline: 2px solid var(--rust); outline-offset: 2px; }
    .choice-card .choice-title { font-family: 'Playfair Display', serif; font-weight: 700; font-size: 1rem; }
    .choice-card .choice-meta { color: var(--muted); font-size: .72rem; }

    .check-card { display: flex; gap: .65rem; align-items: flex-start; border: 1px dashed rgba(44,30,22,.46); padding: .75rem; background: rgba(255,255,255,.2); cursor: pointer; transition: background .2s ease; }
    .check-card:hover { background: rgba(255,255,255,.48); }
    .check-card input { accent-color: var(--rust); width: 1rem; height: 1rem; margin-top: .16rem; }

    .ink-button {
      border: 1px solid var(--ink);
      color: var(--parchment);
      background: var(--ink);
      padding: .78rem 1.2rem;
      font-weight: 700;
      letter-spacing: .02em;
      box-shadow: 3px 3px 0 rgba(166,83,50,.44);
      transition: transform .18s ease, box-shadow .18s ease, background .18s ease;
    }
    .ink-button:hover:not(:disabled) { transform: translate(-1px, -1px); box-shadow: 5px 5px 0 rgba(166,83,50,.44); background: #41291d; }
    .ink-button:disabled { cursor: not-allowed; opacity: .46; box-shadow: none; }
    .outline-button { border: 1px solid var(--ink); background: transparent; color: var(--ink); padding: .74rem 1.05rem; font-weight: 700; transition: background .2s ease, color .2s ease; }
    .outline-button:hover { background: var(--ink); color: var(--parchment); }
    .text-button { color: var(--rust); font-weight: 700; text-decoration: underline; text-underline-offset: 3px; }

    .step-lock { opacity: .6; }
    .step-lock .lock-copy { display: flex; align-items: center; gap: .45rem; color: var(--muted); font-size: .84rem; }

    .total-ticket { border: 2px double var(--ink); background: rgba(255,255,255,.27); padding: .95rem 1rem; }
    .total-ticket .amount { color: var(--rust); font-family: 'Playfair Display', serif; font-size: 2.4rem; font-weight: 800; line-height: 1; }

    .waitlist-track { height: .65rem; border: 1px solid rgba(44,30,22,.6); padding: 2px; background: rgba(255,255,255,.3); }
    .waitlist-fill { height: 100%; background: repeating-linear-gradient(135deg, var(--rust) 0 8px, #8d4127 8px 16px); transition: width .4s ease; }

    .modal-backdrop { background: rgba(44,30,22,.58); backdrop-filter: blur(3px); }
    .modal-card { max-height: min(88vh, 820px); overflow-y: auto; }
    .modal-card::-webkit-scrollbar { width: 8px; }
    .modal-card::-webkit-scrollbar-thumb { background: var(--sepia); border: 2px solid var(--parchment); }

    .admin-order { border: 1px dashed rgba(44,30,22,.48); background: rgba(255,255,255,.25); }
    .admin-order + .admin-order { margin-top: .7rem; }
    .admin-order .order-key { color: var(--sepia); font-size: .64rem; letter-spacing: .12em; text-transform: uppercase; font-weight: 700; }
    .admin-order .order-value { font-size: .85rem; overflow-wrap: anywhere; }

    .empty-state { border: 1px dashed rgba(44,30,22,.45); padding: 2rem 1rem; color: var(--muted); text-align: center; font-family: 'Cormorant Garamond', serif; font-size: 1.25rem; }

    .toast { animation: toast-in .3s ease both; }
    @keyframes toast-in { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    .float-in { animation: float-in .7s ease both; }
    @keyframes float-in { from { opacity: 0; transform: translateY(12px); } to { opacity: 1; transform: translateY(0); } }

    @media (max-width: 760px) {
      .site-shell { width: min(100% - 22px, 640px); }
      .site-shell::before, .site-shell::after { display: none; }
      .price-chart { min-height: 560px; }
      .chart-art-wrap { inset: 68px 20% 30px; }
      .chart-line { left: 4%; right: 4%; grid-template-columns: minmax(87px, 1fr) minmax(30px, 1fr) minmax(100px, 1fr); }
      .level-name { font-size: .73rem; padding: .28rem .36rem; }
      .price-pills { min-width: 112px; padding: .22rem; gap: .12rem; }
      .price-pill { font-size: .64rem; }
      .price-pill small { font-size: .44rem; }
      .chart-header { left: 4%; right: 4%; }
      .chart-header span { font-size: .66rem; }
    }
  </style>
</head>
<body>
  <header class="site-shell pt-6 md:pt-8">
    <nav class="flex items-center justify-between gap-4" aria-label="Main navigation">
      <a href="#top" class="flex items-center gap-3 group">
        <span class="grid place-items-center w-10 h-10 border border-ink rounded-full font-display text-xl group-hover:bg-ink group-hover:text-parchment transition-colors">M</span>
        <span>
          <span class="block font-display font-bold text-lg leading-none">Maison Moth</span>
          <span class="block text-[.62rem] uppercase tracking-[.22em] text-sepia mt-1">Illustration atelier</span>
        </span>
      </a>
      <div class="hidden md:flex items-center gap-7 text-xs uppercase tracking-[.15em] font-semibold text-sepia">
        <a class="nav-link" href="#prices">Prices</a>
        <a class="nav-link" href="#how-to-order">How to order</a>
        <a class="nav-link" href="#rules">Rules</a>
        <a class="nav-link" href="#waitlist">Waitlist</a>
      </div>
      <button id="artistLoginButton" class="text-[.68rem] uppercase tracking-[.14em] text-sepia hover:text-rust transition-colors" type="button">Artist Login ↗</button>
    </nav>
    <div class="double-rule mt-6"></div>
  </header>

  <main id="top" class="site-shell pb-16">
    <section class="grid lg:grid-cols-[1.03fr_.97fr] gap-8 lg:gap-14 items-center pt-10 md:pt-16">
      <div class="float-in">
        <div class="flex items-center gap-3 mb-5"><span class="stamp">Commissions open</span><span class="text-xs text-sepia">No. 04 / 2026</span></div>
        <p class="eyebrow mb-4">Character portraiture · Roblox commissions</p>
        <h1 class="font-display font-bold text-5xl md:text-7xl leading-[.91] tracking-[-.045em]">A little<br /><em class="font-serif font-medium text-rust">portrait</em> for<br />your story.</h1>
        <p class="mt-6 max-w-lg font-serif text-xl leading-snug text-[#614c3b]">Hand-drawn character art, made slowly and with care. Choose a frame, bring me your favourite character, and take a place in the studio queue.</p>
        <div class="flex flex-wrap items-center gap-4 mt-8">
          <a class="ink-button inline-flex items-center gap-3" href="#waitlist">Join the waitlist <span aria-hidden="true">↓</span></a>
          <span class="hand-label">made with ink &amp; mischief</span>
        </div>
        <div class="flex items-center gap-5 mt-9 pt-5 border-t border-dashed border-sepia/60 text-xs text-sepia">
          <span><strong class="font-display text-xl text-ink">2–5</strong> days to DM</span>
          <span class="w-px h-6 bg-sepia/50"></span>
          <span><strong class="font-display text-xl text-ink">10</strong> slots max</span>
          <span class="w-px h-6 bg-sepia/50"></span>
          <span><strong class="font-display text-xl text-ink">R$</strong> Robux</span>
        </div>
      </div>

      <div id="prices" class="paper-card p-3 md:p-5 float-in" style="animation-delay:.12s">
        <div class="flex items-end justify-between gap-4 px-2 pb-2">
          <div><p class="eyebrow">The little price chart</p><h2 class="font-display font-bold text-2xl mt-1">Find your frame</h2></div>
          <span class="hand-label hidden sm:inline-block">choose your view</span>
        </div>
        <div class="price-chart" role="region" aria-label="Commission pricing by framing tier">
          <div class="chart-grid"></div>
          <div class="chart-header"><span>Sketch</span><span>Colored</span></div>
          <div class="chart-art-wrap"><img id="characterArtwork" class="hero-illustration" alt="Sepia character illustration for the commission price chart" /></div>
          <div class="chart-line" style="top: 27%;">
            <span class="level-name">Headshot</span><span></span>
            <span class="price-pills"><span class="price-pill"><small>Sketch</small>20 R$</span><span class="price-pill"><small>Colored</small>50 R$</span></span>
          </div>
          <div class="chart-line" style="top: 43%;">
            <span class="level-name">Bust</span><span></span>
            <span class="price-pills"><span class="price-pill"><small>Sketch</small>75 R$</span><span class="price-pill"><small>Colored</small>100 R$</span></span>
          </div>
          <div class="chart-line" style="top: 61%;">
            <span class="level-name">Half body</span><span></span>
            <span class="price-pills"><span class="price-pill"><small>Sketch</small>85 R$</span><span class="price-pill"><small>Colored</small>120 R$</span></span>
          </div>
          <div class="chart-line" style="top: 80%;">
            <span class="level-name">Knee up</span><span></span>
            <span class="price-pills"><span class="price-pill"><small>Sketch</small>100 R$</span><span class="price-pill"><small>Colored</small>150 R$</span></span>
          </div>
          <div class="absolute left-0 right-0 bottom-3 text-center text-[.68rem] uppercase tracking-[.16em] text-sepia"><span class="border-t border-dashed border-sepia/60 px-5 pt-2">Full-body: <strong class="text-rust">Not Available</strong></span></div>
        </div>
        <p class="text-[.66rem] text-sepia mt-3 px-2">All prices are in Robux. Add-ons are calculated live below.</p>
      </div>
    </section>

    <section id="how-to-order" class="paper-card mt-12 md:mt-20 p-7 md:p-10">
      <div class="grid lg:grid-cols-[.7fr_1.3fr] gap-8 lg:gap-14 items-start">
        <div><p class="eyebrow mb-3">Before you send a raven</p><h2 class="section-title">How to<br /><em class="font-serif font-medium text-rust">order</em></h2><p class="font-serif text-lg leading-snug text-[#614c3b] mt-5 max-w-xs">A small ritual keeps every commission smooth, clear, and fun for both of us.</p></div>
        <ol class="order-rule space-y-5 text-sm leading-relaxed text-[#554333]">
          <li data-step="1"><strong class="text-ink">Check the rules, price chart, and slots.</strong> Read the Will Do / Won't Do list, choose Sketch or Colored, and see if a waitlist place is available.</li>
          <li data-step="2"><strong class="text-ink">Enter your TikTok Username.</strong> Make sure your DMs are open so I can message you!</li>
          <li data-step="3"><strong class="text-ink">Choose your framing and finish.</strong> Pick Headshot, Bust, Half body, or Knee up; select Sketch or Colored; add optional extras; then describe your character or reference clearly.</li>
          <li data-step="4"><strong class="text-ink">Submit your request.</strong> I will DM you on TikTok within 2–5 days with a rough sketch. Once you approve the sketch, payment will be finalized.</li>
        </ol>
      </div>
    </section>

    <section id="rules" class="grid md:grid-cols-2 gap-6 mt-8">
      <div class="paper-card p-7 md:p-9">
        <p class="eyebrow mb-2">The studio door is open to</p><h2 class="section-title text-3xl md:text-4xl">Will Do <span class="text-sage">✓</span></h2>
        <ul class="rule-list mt-5">
          <li><span class="yes">✓</span><span>OC (Original Characters)</span></li><li><span class="yes">✓</span><span>Fanart</span></li><li><span class="yes">✓</span><span>Men &amp; Women</span></li><li><span class="yes">✓</span><span>LGBTQ+</span></li><li><span class="yes">✓</span><span>Couple <span class="text-sm text-sepia">(+40 Robux)</span></span></li>
        </ul>
      </div>
      <div class="paper-card p-7 md:p-9">
        <p class="eyebrow mb-2">For the peace of the studio</p><h2 class="section-title text-3xl md:text-4xl">Won't Do <span class="text-rust">✕</span></h2>
        <ul class="rule-list mt-5">
          <li><span class="no">✕</span><span>Full-body</span></li><li><span class="no">✕</span><span>Gore / Heavy Gore</span></li><li><span class="no">✕</span><span>NSFW</span></li><li><span class="no">✕</span><span>Heavy Furry</span></li><li><span class="no">✕</span><span>Pedophile / Proships</span></li><li><span class="no">✕</span><span>Old People</span></li>
        </ul>
      </div>
    </section>

    <section class="paper-card mt-8 p-6 md:p-8 border-l-4 border-l-rust">
      <div class="grid md:grid-cols-[.72fr_1.28fr] gap-6 items-center">
        <div><p class="eyebrow mb-2">Please read before booking</p><h2 class="font-display font-bold text-2xl">Important terms</h2></div>
        <div class="grid sm:grid-cols-3 gap-4 text-sm text-[#554333]"><div class="border-l border-sepia/50 pl-3"><strong class="block text-rust font-display text-lg">01</strong>No refunds.</div><div class="border-l border-sepia/50 pl-3"><strong class="block text-rust font-display text-lg">02</strong>Payment approval will be finalized after the sketch is completed.</div><div class="border-l border-sepia/50 pl-3"><strong class="block text-rust font-display text-lg">03</strong>Custom Background: <strong class="text-ink">+20 Robux</strong>.</div></div>
      </div>
    </section>

    <section id="waitlist" class="mt-12 md:mt-20 scroll-mt-8">
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-5 mb-5">
        <div><p class="eyebrow mb-3">The commission ledger</p><h2 class="section-title">Take your place<br /><em class="font-serif font-medium text-rust">in line</em></h2></div>
        <div class="paper-card p-4 min-w-[245px]" aria-live="polite"><div class="flex items-baseline justify-between gap-4"><span class="font-display font-bold text-lg">Waitlist</span><span id="waitlistCount" class="text-rust font-bold text-sm">0 / 10 slots filled</span></div><div class="waitlist-track mt-3"><div id="waitlistFill" class="waitlist-fill" style="width:0%"></div></div><p id="waitlistCaption" class="text-xs text-sepia mt-2">There is room at the table.</p></div>
      </div>

      <div id="fullWaitlistNotice" class="hidden paper-card p-8 text-center border-2 border-rust mb-6"><span class="text-3xl">✦</span><h3 class="font-display font-bold text-3xl mt-2">Waitlist is full!</h3><p class="font-serif text-xl text-[#614c3b] mt-2">Please check back later!</p></div>

      <div class="paper-card p-6 md:p-10" id="orderFormCard">
        <div class="flex items-start justify-between gap-4 border-b border-dashed border-sepia/60 pb-5 mb-7"><div><p class="eyebrow">Application form</p><h3 class="font-display font-bold text-2xl mt-1">A note for the artist</h3></div><span class="hand-label">step by step</span></div>
        <form id="commissionForm" novalidate>
          <section id="verifySection">
            <div class="flex items-center gap-3 mb-4"><span class="grid place-items-center w-7 h-7 rounded-full bg-ink text-parchment font-display font-bold text-sm">1</span><h4 class="font-display font-bold text-xl">TikTok verification</h4><span class="eyebrow ml-auto">required</span></div>
            <p class="text-sm text-[#614c3b] max-w-2xl mb-5">I use TikTok DMs to send your rough sketch and follow up, so please double-check your handle and keep your DMs open.</p>
            <div class="grid sm:grid-cols-[1fr_auto] gap-3 items-end max-w-xl"><label class="block"><span class="field-label">TikTok username</span><input id="usernameInput" class="vintage-input" type="text" placeholder="@your_username" autocomplete="off" /></label><button id="continueButton" class="ink-button" type="button">Continue <span aria-hidden="true">→</span></button></div>
            <p id="usernameFeedback" class="text-sm mt-3 min-h-[1.25rem]" aria-live="polite"></p>
          </section>

          <fieldset id="detailsFieldset" disabled class="mt-10 pt-8 border-t border-dashed border-sepia/60">
            <div class="flex items-center gap-3 mb-5"><span class="grid place-items-center w-7 h-7 rounded-full bg-ink text-parchment font-display font-bold text-sm">2</span><h4 class="font-display font-bold text-xl">Commission details</h4><span id="verifiedHandle" class="ml-auto text-xs text-sage font-semibold"></span></div>
            <div class="space-y-7">
              <div><span class="field-label">Choose a framing tier</span><div class="grid grid-cols-2 lg:grid-cols-4 gap-3" id="tierChoices"></div></div>
              <div><span class="field-label">Choose a finish style</span><div class="grid grid-cols-2 gap-3 max-w-lg" id="styleChoices"></div></div>
              <div><span class="field-label">Optional add-ons</span><div class="grid sm:grid-cols-2 gap-3 max-w-2xl"><label class="check-card"><input id="coupleAddon" type="checkbox" /><span><strong class="block font-display text-lg">Couple</strong><span class="text-xs text-sepia">Two characters, +40 Robux</span></span></label><label class="check-card"><input id="backgroundAddon" type="checkbox" /><span><strong class="block font-display text-lg">Custom background</strong><span class="text-xs text-sepia">A setting or colour field, +20 Robux</span></span></label></div></div>
              <div><label class="field-label" for="descriptionInput">Character / pose / reference details</label><textarea id="descriptionInput" class="vintage-input min-h-[145px] resize-y" placeholder="Tell me about their personality, pose, colours, expression, props, and any reference links..."></textarea><p class="text-xs text-sepia mt-2">The more visual detail, the better I can capture them.</p></div>
              <div><span class="field-label">Payment timing</span><div class="grid sm:grid-cols-2 gap-3 max-w-2xl" id="paymentChoices"><div class="choice-card"><input id="payNow" name="payment" type="radio" value="Pay Now" /><label for="payNow"><span class="choice-title">Pay Now</span><span class="choice-meta">I am ready to pay at the start.</span></label></div><div class="choice-card"><input id="payAfter" name="payment" type="radio" value="Pay After Seeing Results / Sketch" checked /><label for="payAfter"><span class="choice-title">Pay After Seeing Results / Sketch</span><span class="choice-meta">Finalize payment after sketch approval.</span></label></div></div></div>
            </div>
          </fieldset>

          <fieldset id="submitSection" disabled class="mt-10 pt-8 border-t border-dashed border-sepia/60">
            <div class="flex items-center gap-3 mb-5"><span class="grid place-items-center w-7 h-7 rounded-full bg-ink text-parchment font-display font-bold text-sm">3</span><h4 class="font-display font-bold text-xl">Submit &amp; reserve</h4></div>
            <div class="grid lg:grid-cols-[1fr_270px] gap-6 items-end"><div class="step-lock"><p class="lock-copy"><span aria-hidden="true">🔒</span> Check your details, then reserve a waitlist spot.</p><p class="text-xs text-sepia mt-2 max-w-lg">By submitting, you confirm that you have read the studio rules and understand that no refunds are offered.</p></div><div class="total-ticket"><div class="flex items-end justify-between gap-3"><span><span class="field-label mb-1">Live total</span><span class="text-xs text-sepia">estimated commission</span></span><span id="totalPrice" class="amount">20</span></div><div class="text-right text-xs text-sepia mt-1">Robux</div><button id="submitButton" class="ink-button w-full mt-4" type="submit">Join the waitlist <span aria-hidden="true">✦</span></button></div></div>
          </fieldset>
        </form>
      </div>
    </section>

    <footer class="mt-14 pt-6 border-t border-double border-ink/60 flex flex-col sm:flex-row justify-between gap-4 text-xs text-sepia">
      <p>© 2026 Maison Moth · drawn from a little room somewhere quiet.</p>
      <p>Local tab sync active · <span id="syncStatus">waiting for a commission</span></p>
    </footer>
  </main>

  <div id="toast" class="fixed bottom-5 right-5 z-50 hidden max-w-sm paper-card px-5 py-4 text-sm" role="status" aria-live="polite"></div>

  <div id="confirmationModal" class="modal-backdrop hidden fixed inset-0 z-40 p-4 items-center justify-center">
    <div class="modal-card paper-card w-full max-w-lg p-8 text-center" role="dialog" aria-modal="true" aria-labelledby="confirmationTitle"><button class="absolute top-4 right-4 text-sepia hover:text-rust text-xl" type="button" data-close-modal="confirmationModal" aria-label="Close confirmation">×</button><span class="text-4xl text-rust">✦</span><p class="eyebrow mt-3">The ledger has your name</p><h2 id="confirmationTitle" class="font-display font-bold text-3xl mt-2">You have been added to the waitlist!</h2><p class="font-serif text-xl leading-snug text-[#614c3b] mt-4">Since I will message you on TikTok DM soon, please allow at least 2–5 days.</p><div id="confirmationSummary" class="border-y border-dashed border-sepia/60 py-4 my-6 text-sm text-left"></div><button class="ink-button" type="button" data-close-modal="confirmationModal">Lovely, thank you</button></div>
  </div>

  <div id="loginModal" class="modal-backdrop hidden fixed inset-0 z-40 p-4 items-center justify-center">
    <div class="modal-card paper-card w-full max-w-md p-7" role="dialog" aria-modal="true" aria-labelledby="loginTitle"><button class="absolute top-4 right-4 text-sepia hover:text-rust text-xl" type="button" data-close-modal="loginModal" aria-label="Close artist login">×</button><p class="eyebrow">Private studio door</p><h2 id="loginTitle" class="font-display font-bold text-3xl mt-2">Artist login</h2><p class="text-sm text-[#614c3b] mt-3">Enter the studio PIN to view the waitlist ledger and image controls.</p><form id="loginForm" class="mt-6"><label class="field-label" for="pinInput">4-digit PIN</label><input id="pinInput" class="vintage-input tracking-[.5em]" type="password" inputmode="numeric" maxlength="4" placeholder="••••" autocomplete="off" /><p id="loginFeedback" class="min-h-[1.25rem] text-sm mt-2 text-rust"></p><button class="ink-button w-full mt-3" type="submit">Open dashboard</button></form></div>
  </div>

  <div id="adminModal" class="modal-backdrop hidden fixed inset-0 z-40 p-4 items-center justify-center">
    <div class="modal-card paper-card w-full max-w-4xl p-6 md:p-8" role="dialog" aria-modal="true" aria-labelledby="adminTitle"><div class="flex items-start justify-between gap-4 border-b border-dashed border-sepia/60 pb-5"><div><p class="eyebrow">Artist-only</p><h2 id="adminTitle" class="font-display font-bold text-3xl mt-1">The studio dashboard</h2></div><button class="text-sepia hover:text-rust text-xl" type="button" data-close-modal="adminModal" aria-label="Close dashboard">×</button></div>
      <div class="grid lg:grid-cols-[1.25fr_.75fr] gap-8 mt-7"><section><div class="flex items-baseline justify-between gap-4 mb-4"><div><p class="eyebrow">Current ledger</p><h3 class="font-display font-bold text-2xl">Waitlist orders</h3></div><span id="adminWaitlistCount" class="text-xs text-rust font-bold"></span></div><div id="adminOrders"></div></section><aside class="space-y-6"><div><p class="eyebrow mb-2">Chart artwork</p><h3 class="font-display font-bold text-xl">Replace illustration</h3><p class="text-xs text-sepia mt-2 leading-relaxed">Upload a JPG, PNG, GIF, or WebP. The image is resized and stored with this studio ledger.</p><label class="outline-button inline-block mt-4 cursor-pointer"><span>Choose image</span><input id="artUpload" class="hidden" type="file" accept="image/png,image/jpeg,image/gif,image/webp" /></label><div class="mt-4 border border-dashed border-sepia/60 p-2"><img id="adminImagePreview" class="w-full h-36 object-contain" alt="Current chart artwork preview" /></div></div><div class="border-t border-dashed border-sepia/60 pt-5"><p class="eyebrow mb-2">Shared sync hook</p><h3 class="font-display font-bold text-xl">Across devices</h3><p class="text-xs text-sepia mt-2 leading-relaxed">Add a JSON GET/PUT endpoint to share this ledger between devices. Without one, this page still syncs between open tabs in the same browser.</p><label class="field-label mt-4" for="syncEndpointInput">Sync endpoint (optional)</label><input id="syncEndpointInput" class="vintage-input text-xs" type="url" placeholder="https://your-endpoint.example/data" /><button id="saveSyncButton" class="outline-button mt-3 w-full" type="button">Save sync setting</button><p id="syncFeedback" class="text-xs text-sage mt-2 min-h-[1rem]"></p></div><div class="border-t border-dashed border-sepia/60 pt-5"><button id="exportButton" class="outline-button w-full" type="button">Export ledger JSON</button><button id="clearButton" class="text-button text-xs mt-4 w-full" type="button">Clear all waitlist data</button></div></aside></div>
    </div>
  </div>

  <script>
    /*
      Optional shared sync:
      set window.VINTAGE_CONFIG = { syncEndpoint: 'https://your-json-get-put-endpoint.example/data' }
      before this script runs, or save the endpoint from Artist Login. The endpoint should
      accept GET and PUT JSON documents shaped like the local state below.
    */
    const VINTAGE_CONFIG = window.VINTAGE_CONFIG || {};
    const STORAGE_KEY = 'maison-moth-commission-ledger-v2';
    const MAX_SLOTS = 10;
    const DEFAULT_PIN = '1234';
    const tiers = [
      { id: 'headshot', name: 'Headshot', sketch: 20, colored: 50, note: 'Face & shoulders' },
      { id: 'bust', name: 'Bust', sketch: 75, colored: 100, note: 'Chest-up portrait' },
      { id: 'half', name: 'Half body', sketch: 85, colored: 120, note: 'Waist-up portrait' },
      { id: 'knee', name: 'Knee up', sketch: 100, colored: 150, note: 'Knees & above' }
    ];

    const defaultIllustration = `data:image/svg+xml;charset=UTF-8,${encodeURIComponent(`
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 520 820">
        <defs><filter id="paper"><feTurbulence baseFrequency=".03" numOctaves="2" result="noise"/><feBlend in="SourceGraphic" in2="noise" mode="multiply"/></filter></defs>
        <g fill="none" stroke="#6b4b37" stroke-linecap="round" stroke-linejoin="round" filter="url(#paper)">
          <path fill="#b88865" stroke-width="8" d="M143 178c-10-77 28-133 113-139 84-5 133 51 119 137-11 67-61 110-119 108-58-2-104-42-113-106z"/>
          <path fill="#3c2c25" stroke-width="7" d="M140 157c-10-68 18-119 80-140 58-20 134 11 153 74-31-24-59-35-91-26-35 9-55 45-102 43-13 0-27 29-40 49z"/>
          <path stroke-width="6" d="M204 176c10 8 23 8 33 0M283 176c10 8 23 8 33 0M239 221c14 12 32 12 45 0"/>
          <path stroke-width="5" d="M246 182c-4 11-5 20 2 27"/>
          <path fill="#d2b58f" stroke-width="9" d="M166 303c-3-23 15-38 37-42l42 45 42-45c21 4 39 19 36 42l31 57c28 62 42 137 35 225l-8 133H139l-8-133c-6-88 8-163 36-225z"/>
          <path fill="#8e5e3b" stroke-width="8" d="M170 310l75 45 75-45 38 76-52 22-1-55-15 19-45 3-44-3-15-19-1 55-52-22z"/>
          <path stroke-width="5" d="M205 408c16 15 31 23 40 28 10-5 25-13 41-28M174 475l-17 195M345 475l17 195"/>
          <path fill="#d0b17c" stroke-width="8" d="M139 676l74 0 12 124-105 0zM307 676l74 0 19 124-105 0z"/>
          <path stroke-width="10" d="M119 800h114M295 800h116"/>
          <path stroke-width="4" d="M96 357c-22 27-30 53-31 84M424 357c22 27 30 53 31 84M108 458c-20 31-25 71-22 110M412 458c20 31 25 71 22 110"/>
        </g>
        <g fill="#a65332" opacity=".76"><circle cx="88" cy="177" r="5"/><circle cx="429" cy="242" r="4"/><circle cx="95" cy="587" r="4"/><circle cx="426" cy="542" r="5"/><path d="M90 204l4 12 12 4-12 4-4 12-4-12-12-4 12-4z"/><path d="M430 313l3 9 9 3-9 3-3 9-3-9-9-3 9-3z"/></g>
      </svg>`)}
    `;

    let state = loadState();
    let currentUser = { username: '', verified: false };
    let channel = null;
    let toastTimer = null;

    function baseState() {
      return { version: 2, updatedAt: 0, waitlist: [], imageData: '', syncEndpoint: VINTAGE_CONFIG.syncEndpoint || '' };
    }

    function loadState() {
      try {
        const stored = JSON.parse(localStorage.getItem(STORAGE_KEY) || 'null');
        return normalizeState(stored || baseState());
      } catch (error) {
        return baseState();
      }
    }

    function normalizeState(input) {
      const safe = input && typeof input === 'object' ? input : {};
      return { ...baseState(), ...safe, waitlist: Array.isArray(safe.waitlist) ? safe.waitlist : [], imageData: typeof safe.imageData === 'string' ? safe.imageData : '', syncEndpoint: typeof safe.syncEndpoint === 'string' ? safe.syncEndpoint : '' };
    }

    function mergeStates(a, b) {
      const local = normalizeState(a);
      const remote = normalizeState(b);
      const byId = new Map();
      [...local.waitlist, ...remote.waitlist].forEach(order => { if (order && order.id) byId.set(order.id, order); });
      return normalizeState({
        ...local,
        waitlist: [...byId.values()].sort((x, y) => String(x.createdAt).localeCompare(String(y.createdAt))).slice(0, MAX_SLOTS),
        imageData: remote.updatedAt > local.updatedAt && remote.imageData ? remote.imageData : local.imageData,
        syncEndpoint: local.syncEndpoint || remote.syncEndpoint,
        updatedAt: Math.max(local.updatedAt || 0, remote.updatedAt || 0)
      });
    }

    function saveState({ broadcast = true, remote = true } = {}) {
      state.updatedAt = Date.now();
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
      if (broadcast && channel) channel.postMessage({ type: 'state', state });
      if (remote && state.syncEndpoint) pushRemoteState();
      renderAll();
    }

    function setupChannel() {
      try {
        channel = 'BroadcastChannel' in window ? new BroadcastChannel('maison-moth-ledger') : null;
        if (channel) channel.onmessage = event => { if (event.data?.type === 'state') applyIncomingState(event.data.state); };
      } catch (error) { channel = null; }
      window.addEventListener('storage', event => { if (event.key === STORAGE_KEY && event.newValue) { try { applyIncomingState(JSON.parse(event.newValue)); } catch (error) {} } });
    }

    function applyIncomingState(incoming) {
      const merged = mergeStates(state, incoming);
      if (JSON.stringify(merged) !== JSON.stringify(state)) { state = merged; localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); renderAll(); }
    }

    async function pushRemoteState() {
      if (!state.syncEndpoint) return;
      setSyncStatus('saving to shared endpoint…');
      try {
        const response = await fetch(state.syncEndpoint, { method: 'PUT', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(state) });
        if (!response.ok) throw new Error('Sync endpoint returned ' + response.status);
        setSyncStatus('shared sync connected');
      } catch (error) {
        setSyncStatus('local sync active · endpoint unavailable');
      }
    }

    async function pullRemoteState() {
      if (!state.syncEndpoint) { setSyncStatus('local tab sync active'); return; }
      try {
        const response = await fetch(state.syncEndpoint, { cache: 'no-store' });
        if (!response.ok) throw new Error('Sync endpoint returned ' + response.status);
        const remote = await response.json();
        const merged = mergeStates(state, remote);
        const changed = JSON.stringify(merged) !== JSON.stringify(state);
        state = merged;
        localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
        if (changed) renderAll();
        setSyncStatus('shared sync connected');
      } catch (error) {
        setSyncStatus('local sync active · endpoint unavailable');
      }
    }

    function setSyncStatus(text) {
      const node = document.getElementById('syncStatus');
      if (node) node.textContent = text;
    }

    function money(value) { return `${Number(value || 0)} R$`; }
    function selectedTier() { return tiers.find(tier => tier.id === document.querySelector('input[name="tier"]:checked')?.value) || tiers[0]; }
    function selectedStyle() { return document.querySelector('input[name="style"]:checked')?.value || 'sketch'; }
    function currentTotal() {
      const tier = selectedTier();
      let total = tier[selectedStyle()];
      if (document.getElementById('coupleAddon')?.checked) total += 40;
      if (document.getElementById('backgroundAddon')?.checked) total += 20;
      return total;
    }

    function renderChoices() {
      const tierRoot = document.getElementById('tierChoices');
      tierRoot.innerHTML = tiers.map((tier, index) => `<div class="choice-card"><input id="tier-${tier.id}" name="tier" type="radio" value="${tier.id}" ${index === 0 ? 'checked' : ''} /><label for="tier-${tier.id}"><span class="choice-title">${tier.name}</span><span class="choice-meta">${tier.note}</span><span class="text-xs text-rust mt-1">${money(tier.sketch)} sketch · ${money(tier.colored)} colour</span></label></div>`).join('');
      document.getElementById('styleChoices').innerHTML = `<div class="choice-card"><input id="style-sketch" name="style" type="radio" value="sketch" checked /><label for="style-sketch"><span class="choice-title">Sketch</span><span class="choice-meta">Loose, expressive ink lines</span></label></div><div class="choice-card"><input id="style-colored" name="style" type="radio" value="colored" /><label for="style-colored"><span class="choice-title">Colored</span><span class="choice-meta">Full sepia-toned colour finish</span></label></div>`;
      document.querySelectorAll('input[name="tier"], input[name="style"]').forEach(input => input.addEventListener('change', updateTotal));
    }

    function updateTotal() { document.getElementById('totalPrice').textContent = currentTotal(); }

    function renderWaitlist() {
      const count = state.waitlist.length;
      const isFull = count >= MAX_SLOTS;
      document.getElementById('waitlistCount').textContent = `${count} / ${MAX_SLOTS} slots filled`;
      document.getElementById('waitlistFill').style.width = `${Math.min(100, (count / MAX_SLOTS) * 100)}%`;
      document.getElementById('waitlistCaption').textContent = isFull ? 'The ledger is closed for now.' : `${MAX_SLOTS - count} ${MAX_SLOTS - count === 1 ? 'place remains' : 'places remain'} at the table.`;
      document.getElementById('fullWaitlistNotice').classList.toggle('hidden', !isFull);
      const formCard = document.getElementById('orderFormCard');
      formCard.classList.toggle('opacity-60', isFull);
      const form = document.getElementById('commissionForm');
      form.querySelectorAll('input, textarea, button').forEach(control => {
        if (control.id === 'continueButton') control.disabled = isFull;
      });
      const unlocked = !isFull && currentUser.verified;
      const detailSections = [document.getElementById('detailsFieldset'), document.getElementById('submitSection')];
      detailSections.forEach(section => {
        section.disabled = !unlocked;
        section.querySelectorAll('input, textarea, button').forEach(control => { control.disabled = !unlocked; });
      });
    }

    function renderArtwork() {
      const src = state.imageData || defaultIllustration;
      document.getElementById('characterArtwork').src = src;
      document.getElementById('adminImagePreview').src = src;
    }

    function renderAdminOrders() {
      const root = document.getElementById('adminOrders');
      document.getElementById('adminWaitlistCount').textContent = `${state.waitlist.length} / ${MAX_SLOTS} filled`;
      if (!state.waitlist.length) { root.innerHTML = '<div class="empty-state">No one is waiting yet.<br /><span class="text-sm">The ledger is yours to fill.</span></div>'; return; }
      root.innerHTML = state.waitlist.map((order, index) => `<article class="admin-order p-4"><div class="flex items-start justify-between gap-3"><div><span class="order-key">Slot ${index + 1} · ${escapeHtml(order.username)}</span><h4 class="font-display font-bold text-xl mt-1">${escapeHtml(order.tier)} · ${escapeHtml(order.style)}</h4></div><button type="button" class="text-xs text-rust underline underline-offset-2 remove-order" data-order-id="${escapeHtml(order.id)}">Complete / Remove</button></div><div class="grid sm:grid-cols-2 gap-x-5 gap-y-3 mt-4"><div><span class="order-key">Add-ons</span><p class="order-value">${escapeHtml(order.addons || 'None')}</p></div><div><span class="order-key">Total</span><p class="order-value text-rust font-bold">${money(order.total)}</p></div><div><span class="order-key">Payment</span><p class="order-value">${escapeHtml(order.payment)}</p></div><div><span class="order-key">Submitted</span><p class="order-value">${escapeHtml(formatDate(order.createdAt))}</p></div><div class="sm:col-span-2"><span class="order-key">Description</span><p class="order-value leading-relaxed mt-1">${escapeHtml(order.description)}</p></div></div></article>`).join('');
      root.querySelectorAll('.remove-order').forEach(button => button.addEventListener('click', () => removeOrder(button.dataset.orderId)));
    }

    function renderAll() {
      renderWaitlist();
      renderArtwork();
      renderAdminOrders();
      updateTotal();
    }

    function formatDate(value) { try { return new Intl.DateTimeFormat('en', { month: 'short', day: 'numeric', year: 'numeric' }).format(new Date(value)); } catch { return '—'; } }
    function escapeHtml(value) { return String(value ?? '').replace(/[&<>'"]/g, char => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', "'": '&#39;', '"': '&quot;' }[char])); }

    function openModal(id) { const modal = document.getElementById(id); modal.classList.remove('hidden'); modal.classList.add('flex'); document.body.classList.add('overflow-hidden'); const firstInput = modal.querySelector('input, button'); if (firstInput) setTimeout(() => firstInput.focus(), 30); }
    function closeModal(id) { const modal = document.getElementById(id); modal.classList.add('hidden'); modal.classList.remove('flex'); if (!document.querySelector('.modal-backdrop.flex')) document.body.classList.remove('overflow-hidden'); }
    function showToast(message, tone = 'normal') { const toast = document.getElementById('toast'); toast.textContent = message; toast.className = `toast fixed bottom-5 right-5 z-50 max-w-sm paper-card px-5 py-4 text-sm ${tone === 'error' ? 'border-rust text-rust' : ''}`; clearTimeout(toastTimer); toastTimer = setTimeout(() => toast.classList.add('hidden'), 4200); }

    function verifyUsername() {
      if (state.waitlist.length >= MAX_SLOTS) return;
      const input = document.getElementById('usernameInput');
      const feedback = document.getElementById('usernameFeedback');
      const raw = input.value.trim();
      const normalized = raw.startsWith('@') ? raw : `@${raw}`;
      if (!/^@[a-zA-Z0-9._]{2,30}$/.test(normalized)) { feedback.textContent = 'Please enter a valid TikTok username, like @your_name.'; feedback.className = 'text-sm mt-3 min-h-[1.25rem] text-rust'; input.focus(); return; }
      currentUser = { username: normalized, verified: true };
      input.value = normalized;
      feedback.textContent = 'Handle noted — the rest of the form is unlocked.';
      feedback.className = 'text-sm mt-3 min-h-[1.25rem] text-sage';
      document.getElementById('verifiedHandle').textContent = normalized;
      document.getElementById('detailsFieldset').disabled = false;
      document.getElementById('submitSection').disabled = false;
      document.getElementById('descriptionInput').focus();
      renderWaitlist();
    }

    function submitCommission(event) {
      event.preventDefault();
      if (!currentUser.verified || state.waitlist.length >= MAX_SLOTS) return;
      const description = document.getElementById('descriptionInput').value.trim();
      if (description.length < 10) { showToast('Please add a little more detail about your character or reference.', 'error'); document.getElementById('descriptionInput').focus(); return; }
      const tier = selectedTier();
      const style = selectedStyle();
      const addons = [document.getElementById('coupleAddon').checked ? 'Couple (+40 Robux)' : '', document.getElementById('backgroundAddon').checked ? 'Custom Background (+20 Robux)' : ''].filter(Boolean).join(' · ') || 'None';
      const order = { id: `${Date.now()}-${Math.random().toString(36).slice(2, 9)}`, username: currentUser.username, tier: tier.name, style: style === 'sketch' ? 'Sketch' : 'Colored', addons, total: currentTotal(), description, payment: document.querySelector('input[name="payment"]:checked')?.value || 'Pay After Seeing Results / Sketch', createdAt: new Date().toISOString() };
      state.waitlist.push(order);
      saveState();
      document.getElementById('confirmationSummary').innerHTML = `<div class="flex justify-between gap-4"><span class="text-sepia">TikTok</span><strong>${escapeHtml(order.username)}</strong></div><div class="flex justify-between gap-4 mt-2"><span class="text-sepia">Commission</span><strong>${escapeHtml(order.tier)} · ${escapeHtml(order.style)}</strong></div><div class="flex justify-between gap-4 mt-2"><span class="text-sepia">Estimated total</span><strong class="text-rust">${money(order.total)}</strong></div>`;
      openModal('confirmationModal');
      document.getElementById('commissionForm').reset();
      currentUser = { username: '', verified: false };
      document.getElementById('usernameFeedback').textContent = '';
      document.getElementById('verifiedHandle').textContent = '';
      document.getElementById('detailsFieldset').disabled = true;
      document.getElementById('submitSection').disabled = true;
      updateTotal();
      setSyncStatus(state.syncEndpoint ? 'saving to shared endpoint…' : 'local tab sync active');
    }

    function removeOrder(id) {
      const order = state.waitlist.find(item => item.id === id);
      if (!order || !confirm(`Remove ${order.username} from the waitlist?`)) return;
      state.waitlist = state.waitlist.filter(item => item.id !== id);
      saveState();
      showToast(`${order.username} was removed and a slot is open again.`);
    }

    function login(event) {
      event.preventDefault();
      const feedback = document.getElementById('loginFeedback');
      if (document.getElementById('pinInput').value === DEFAULT_PIN) { feedback.textContent = ''; document.getElementById('loginForm').reset(); closeModal('loginModal'); document.getElementById('syncEndpointInput').value = state.syncEndpoint || ''; openModal('adminModal'); return; }
      feedback.textContent = 'That PIN does not match the studio key.';
      document.getElementById('pinInput').select();
    }

    async function handleUpload(event) {
      const file = event.target.files?.[0];
      if (!file) return;
      if (!file.type.startsWith('image/')) { showToast('Please choose an image file.', 'error'); return; }
      const reader = new FileReader();
      reader.onload = () => {
        const image = new Image();
        image.onload = () => {
          const max = 1200;
          const scale = Math.min(1, max / Math.max(image.width, image.height));
          const canvas = document.createElement('canvas');
          canvas.width = Math.max(1, Math.round(image.width * scale)); canvas.height = Math.max(1, Math.round(image.height * scale));
          const context = canvas.getContext('2d'); context.drawImage(image, 0, 0, canvas.width, canvas.height);
          state.imageData = canvas.toDataURL('image/webp', .88);
          saveState(); showToast('The chart illustration has been replaced.');
        };
        image.src = reader.result;
      };
      reader.readAsDataURL(file);
    }

    function exportLedger() {
      const payload = JSON.stringify(state, null, 2);
      const blob = new Blob([payload], { type: 'application/json' });
      const url = URL.createObjectURL(blob); const anchor = document.createElement('a'); anchor.href = url; anchor.download = `maison-moth-ledger-${new Date().toISOString().slice(0, 10)}.json`; anchor.click(); URL.revokeObjectURL(url);
    }

    function bindEvents() {
      document.getElementById('continueButton').addEventListener('click', verifyUsername);
      document.getElementById('usernameInput').addEventListener('keydown', event => { if (event.key === 'Enter') { event.preventDefault(); verifyUsername(); } });
      document.getElementById('commissionForm').addEventListener('submit', submitCommission);
      document.getElementById('coupleAddon').addEventListener('change', updateTotal);
      document.getElementById('backgroundAddon').addEventListener('change', updateTotal);
      document.getElementById('artistLoginButton').addEventListener('click', () => openModal('loginModal'));
      document.getElementById('loginForm').addEventListener('submit', login);
      document.getElementById('artUpload').addEventListener('change', handleUpload);
      document.getElementById('exportButton').addEventListener('click', exportLedger);
      document.getElementById('clearButton').addEventListener('click', () => { if (!state.waitlist.length || confirm('Clear every current waitlist order?')) { state.waitlist = []; saveState(); showToast('The waitlist ledger is clear.'); } });
      document.getElementById('saveSyncButton').addEventListener('click', () => { state.syncEndpoint = document.getElementById('syncEndpointInput').value.trim(); saveState(); document.getElementById('syncFeedback').textContent = state.syncEndpoint ? 'Endpoint saved. Testing connection…' : 'Shared endpoint cleared; local mode is active.'; if (state.syncEndpoint) pullRemoteState(); });
      document.querySelectorAll('[data-close-modal]').forEach(button => button.addEventListener('click', () => closeModal(button.dataset.closeModal)));
      document.querySelectorAll('.modal-backdrop').forEach(modal => modal.addEventListener('click', event => { if (event.target === modal) closeModal(modal.id); }));
      document.addEventListener('keydown', event => { if (event.key === 'Escape') document.querySelectorAll('.modal-backdrop.flex').forEach(modal => closeModal(modal.id)); });
    }

    renderChoices();
    setupChannel();
    bindEvents();
    renderAll();
    if (state.syncEndpoint) pullRemoteState(); else setSyncStatus('local tab sync active');
    setInterval(() => { if (state.syncEndpoint) pullRemoteState(); }, 15000);
  </script>
</body>
</html>
