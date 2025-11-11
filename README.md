<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>MISSION: IMCHUGGUS</title>
  <meta name="author" content="ImChuggus">
  <style>
    /* --- Reset & base --- */
    :root{
      --bg:#071226;
      --card:#0f2033;
      --muted:#9fb0c6;
      --accent:#ffd166;
      --glass: rgba(255,255,255,0.04);
      --rounded: 16px;
    }
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: radial-gradient(1200px 600px at 10% 10%, rgba(30,60,90,0.12), transparent),
                  radial-gradient(800px 400px at 90% 80%, rgba(50,20,80,0.10), transparent),
                  var(--bg);
      color: #ecf7ff;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      padding: 36px 18px;
      line-height:1.5;
    }

    /* --- layout --- */
    .page {
      max-width: 980px;
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1fr 380px;
      gap: 28px;
      align-items: start;
    }

    header {
      grid-column: 1 / -1;
      display:flex;
      align-items:center;
      gap:18px;
      margin-bottom:6px;
    }
    .logo {
      width:92px;
      height:92px;
      border-radius:18px;
      background: linear-gradient(180deg,#0d2a4a,#071226);
      display:flex;
      align-items:center;
      justify-content:center;
      box-shadow: 0 6px 22px rgba(0,0,0,0.6), inset 0 -6px 20px rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.03);
    }
    .logo svg{width:62px;height:62px;display:block}

    h1{
      font-size: clamp(22px, 4vw, 36px);
      letter-spacing: 1px;
    }
    .sub {
      color:var(--muted);
      font-size: 14px;
      margin-top:6px;
    }

    /* --- left column content --- */
    .intro-card {
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius: var(--rounded);
      padding: 22px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.6);
      border: 1px solid rgba(255,255,255,0.03);
    }
    .intro-card p{
      color:#e9f6ff;
      font-size: 15px;
      margin-top:10px;
      text-align: justify;
    }

    /* --- right column: visual / rocket & space --- */
    .visual {
      background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
      border-radius: var(--rounded);
      padding: 18px;
      position: relative;
      min-height: 420px;
      overflow: hidden;
      border:1px solid rgba(255,255,255,0.03);
    }

    /* animated stars */
    .stars, .stars:after {
      position:absolute;
      inset:0;
      background-image: radial-gradient(#fff 1px, transparent 1px);
      background-size: 3px 3px;
      opacity:0.06;
      pointer-events:none;
      mix-blend-mode: screen;
    }
    .stars:after {
      transform:translateY(130px) scale(1.6);
      opacity:0.025;
    }

    /* planet graphic */
    .planet {
      position:absolute;
      top:18px;
      right:18px;
      width:88px;
      height:88px;
      border-radius:50%;
      background: linear-gradient(120deg,#ffb86b,#ff7b7b);
      box-shadow: 0 12px 30px rgba(255,123,123,0.06), inset -6px -6px 20px rgba(0,0,0,0.15);
      opacity:0.95;
    }

    /* rocket wrapper & animation */
    .rocket-wrap {
      position:absolute;
      left:12px;
      bottom: -20px;
      width: 100%;
      display:flex;
      justify-content: center;
      pointer-events: none;
    }
    .rocket {
      width:160px;
      transform-origin: 50% 90%;
      animation: bob 3s ease-in-out infinite;
      filter: drop-shadow(0 18px 24px rgba(0,0,0,0.45));
    }
    @keyframes bob {
      0%{transform: translateY(0) rotate(-2deg)}
      50%{transform: translateY(-10px) rotate(2deg)}
      100%{transform: translateY(0) rotate(-2deg)}
    }

    /* Indian flag on rocket: implemented inside SVG */

    /* --- Hobbies interactive area --- */
    .hobbies {
      margin-top:18px;
      display:flex;
      flex-direction:column;
      gap:12px;
    }
    .hobby-btn {
      background: var(--card);
      border-radius:12px;
      padding:12px 14px;
      display:flex;
      justify-content:space-between;
      align-items:center;
      gap:10px;
      cursor:pointer;
      border:1px solid rgba(255,255,255,0.02);
      transition: transform .15s ease, box-shadow .15s ease;
    }
    .hobby-btn:hover{ transform: translateY(-5px); box-shadow: 0 12px 30px rgba(0,0,0,0.45) }
    .hobby-btn .title { font-weight:600; color:#e8f8ff;}
    .hobby-content {
      margin-top:8px;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:10px;
      padding:12px;
      color:var(--muted);
      font-size:14px;
      display:none;
    }
    .hobby-btn .chev{ color:var(--muted); font-size:18px }

    /* --- bottom area & contact --- */
    .contact {
      margin-top:26px;
      text-align:center;
      color:var(--muted);
      font-size:14px;
      padding:12px;
      border-radius:12px;
      background:var(--glass);
      border:1px solid rgba(255,255,255,0.02);
    }
    footer {
      grid-column: 1 / -1;
      margin-top:22px;
      text-align:center;
      color: #9fb0c6;
      font-size:13px;
      opacity:0.95;
    }

    /* --- responsive --- */
    @media (max-width:880px){
      .page { grid-template-columns: 1fr; }
      .visual{ order:-1; }
      .rocket{ width:128px }
    }

  </style>
</head>
<body>
  <main class="page" role="main">
    <header>
      <div class="logo" aria-hidden="true">
        <!-- small space badge SVG -->
        <svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="logo">
          <circle cx="32" cy="32" r="30" fill="#0b243a"/>
          <g transform="translate(7,7)">
            <rect x="2" y="24" width="8" height="24" rx="3" fill="#ffd166"/>
            <rect x="18" y="16" width="8" height="32" rx="4" fill="#8bd3ff"/>
            <path d="M2 20 L56 2 L54 10 L10 28 Z" fill="#fff1"/>
          </g>
        </svg>
      </div>

      <div>
        <h1>MISSION: IMCHUGGUS 🚀</h1>
        <div class="sub">A small spacey page about me — hobbies, what I like, and my learning journey.</div>
      </div>
    </header>

    <!-- LEFT: intro + hobbies -->
    <section class="intro-card" aria-labelledby="intro-title">
      <h2 id="intro-title" style="font-size:18px;">Hello — I'm ImChuggus</h2>

      <p>
        I'm an 8th-grade kid who really loves doing stuff that feels fun and new. I play cricket with my friends almost every weekend, and I get super excited about scoring runs or learning a new shot. I also love gaming — whether it's a quick mobile match or trying to learn strategies for a team game. When I'm not outside, I enjoy indoor games and acting in little school plays; I like practicing short scenes and making faces that get my classmates to laugh. On the school side, I'm still learning coding — I tinker with HTML and CSS to make small pages, and I try basic projects in Java and Python. I don't always get things right the first time, but I like fixing bugs and figuring out why something didn't work. Mostly, I want to try lots of things, meet new people, and keep learning — tiny steps every day. This page is my little mission board: simple, honest, and a bit adventurous.
      </p>

      <div class="hobbies" aria-label="Hobbies list">
        <h3 style="margin-top:18px; margin-bottom:6px; color:#fff;">My Hobbies</h3>

        <div class="hobby">
          <div class="hobby-btn" data-target="h1" role="button" tabindex="0" aria-expanded="false" aria-controls="h1">
            <div class="title">🏏 Playing Cricket</div>
            <div class="chev">+</div>
          </div>
          <div id="h1" class="hobby-content">I enjoy batting and bowling with my friends. Cricket teaches teamwork, patience and quick decisions on the field. I love practicing shots and watching highlight reels of players I admire.</div>
        </div>

        <div class="hobby">
          <div class="hobby-btn" data-target="h2" role="button" tabindex="0" aria-expanded="false" aria-controls="h2">
            <div class="title">🎮 Gaming & Esports</div>
            <div class="chev">+</div>
          </div>
          <div id="h2" class="hobby-content">I play casual and competitive games. Gaming helps me think fast, plan strategies, and sometimes work with a team. I enjoy practicing to improve my skills and learning from replays.</div>
        </div>

        <div class="hobby">
          <div class="hobby-btn" data-target="h3" role="button" tabindex="0" aria-expanded="false" aria-controls="h3">
            <div class="title">🎭 Acting & Performing</div>
            <div class="chev">+</div>
          </div>
          <div id="h3" class="hobby-content">Acting is fun — I like learning short dialogues and trying different expressions. It helps me present in class and feel confident speaking in front of people.</div>
        </div>

        <div class="hobby">
          <div class="hobby-btn" data-target="h4" role="button" tabindex="0" aria-expanded="false" aria-controls="h4">
            <div class="title">💻 Learning Coding (HTML, CSS, Java, Python)</div>
            <div class="chev">+</div>
          </div>
          <div id="h4" class="hobby-content">I'm learning to build small web pages with HTML and style them with CSS. I try basic Java exercises and simple Python scripts too. It’s exciting to make something that actually works on a browser.</div>
        </div>

      </div>

      <div class="contact" style="margin-top:18px;">
        Want to say hi? Email: <strong>imchuggus@example.com</strong> (just a placeholder — replace with your real contact).
      </div>
    </section>

    <!-- RIGHT: visual area (rocket + stars + planet) -->
    <aside class="visual" aria-hidden="false" aria-label="space-visual">
      <div class="stars" aria-hidden="true"></div>
      <div class="planet" aria-hidden="true"></div>

      <!-- central decorative content -->
      <div style="padding:18px; position:relative; z-index:2; text-align:center; margin-top:36px;">
        <h3 style="letter-spacing:1px; margin-bottom:6px;">Reach for the stars</h3>
        <p style="color:var(--muted); font-size:14px; margin-bottom:10px;">A little launcher for ideas — try clicking the hobbies to reveal more.</p>
      </div>

      <div class="rocket-wrap" aria-hidden="true">
        <!-- Rocket SVG with Indian flag on its body -->
        <svg class="rocket" viewBox="0 0 120 240" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="rocket">
          <!-- smoke -->
          <g transform="translate(0,100)" opacity="0.12">
            <ellipse cx="60" cy="120" rx="46" ry="18" fill="#000" />
          </g>

          <!-- body shadow -->
          <defs>
            <linearGradient id="bodyGrad" x1="0" x2="1">
              <stop offset="0" stop-color="#ffffff"/>
              <stop offset="1" stop-color="#c7e6ff"/>
            </linearGradient>
            <linearGradient id="finGrad" x1="0" x2="1">
              <stop offset="0" stop-color="#ff6b6b"/>
              <stop offset="1" stop-color="#c04040"/>
            </linearGradient>
          </defs>

          <!-- rocket main -->
          <g transform="translate(24,6)">
            <path d="M36 0 C60 6 84 36 84 72 C84 108 36 168 36 168 C36 168 -12 108 -12 72 C-12 36 12 6 36 0 Z" fill="url(#bodyGrad)" stroke="#0e1530" stroke-opacity="0.06"/>
            <!-- window -->
            <circle cx="36" cy="64" r="14" fill="#073b58" stroke="#bfe3ff" stroke-width="3"/>
            <!-- fins -->
            <path d="M84 82 C106 74 118 84 118 84 C118 84 106 110 86 104 Z" fill="url(#finGrad)"/>
            <path d="M0 82 C-22 74 -34 84 -34 84 C-34 84 -22 110 -2 104 Z" fill="url(#finGrad)"/>
            <!-- flame -->
            <g transform="translate(36,168)">
              <path d="M0 0 C6 12 18 26 36 36 C54 26 64 12 72 0 L36 44 Z" fill="#ffb347"/>
            </g>

            <!-- Indian flag on the body -->
            <g transform="translate(12,92)">
              <rect width="48" height="12" rx="1" fill="#fff"/>
              <rect width="48" height="4" fill="#FF9933"/>
              <rect y="4" width="48" height="4" fill="#fff"/>
              <rect y="8" width="48" height="4" fill="#138808"/>
              <!-- Ashoka chakra - simple -->
              <circle cx="24" cy="6" r="2.2" fill="#0b3b61"/>
              <g stroke="#0b3b61" stroke-width="0.4" transform="translate(24,6)">
                <path d="M0 -2.2 L0 2.2 M-2.2 0 L2.2 0 M-1.55 -1.55 L1.55 1.55 M1.55 -1.55 L-1.55 1.55" stroke-linecap="round"/>
              </g>
            </g>

          </g>
        </svg>
      </div>

    </aside>

    <footer>
      Designed by <strong>ImChuggus</strong> • Keep exploring the universe! ✨
    </footer>
  </main>

  <script>
    // Hobby toggle behavior
    (function(){
      const buttons = document.querySelectorAll('.hobby-btn');
      buttons.forEach(btn => {
        const targetId = btn.getAttribute('data-target');
        const content = document.getElementById(targetId);
        const chev = btn.querySelector('.chev');

        function toggle(open){
          const isOpen = (open === undefined) ? (content.style.display !== 'none' && content.style.display !== '') : open;
          if(isOpen){
            content.style.display = 'none';
            btn.setAttribute('aria-expanded','false');
            chev.textContent = '+';
          } else {
            content.style.display = 'block';
            btn.setAttribute('aria-expanded','true');
            chev.textContent = '−';
          }
        }

        // initialize closed
        content.style.display = 'none';
        btn.setAttribute('aria-expanded','false');

        btn.addEventListener('click', () => toggle());
        btn.addEventListener('keydown', (e) => {
          if(e.key === 'Enter' || e.key === ' '){
            e.preventDefault();
            toggle();
          }
        });
      });
    })();
  </script>
</body>
</html>
