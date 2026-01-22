<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Be My Valentine ❤️</title>
  <style>
    :root{
      --bg: #ffc0cb;
      --card: #fff;
      --accent: #d10068;
      --button: #e11;
      --button-contrast: #fff;
      --radius: 16px;
      --max-width: 420px;
      --shadow: 0 10px 20px rgba(0,0,0,0.18);
    }
    html,body{height:100%}
    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: var(--bg);
      font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      padding: 20px;
      color: #222;
    }
    main.card {
      background: var(--card);
      padding: clamp(20px, 4vw, 36px);
      border-radius: var(--radius);
      text-align: center;
      box-shadow: var(--shadow);
      width: 100%;
      max-width: var(--max-width);
    }
    .heart {
      font-size: clamp(36px, 8vw, 64px);
      color: #ff234d;
      animation: beat 1000ms ease-in-out infinite;
      user-select: none;
      pointer-events: none;
    }
    @keyframes beat { 0%{transform:scale(1)}50%{transform:scale(1.18)}100%{transform:scale(1)} }
    h1{ margin: 12px 0 6px; font-size: 1.25rem; color:#111 }
    p.lead{ margin:0; font-size:0.98rem; color:var(--accent) }

    /* Anchor styled as button */
    a.btn {
      display: inline-block;
      margin-top: 12px;
      padding: 12px 28px;
      font-size: 1rem;
      border-radius: 10px;
      background-color: var(--button);
      color: var(--button-contrast);
      text-decoration: none;
      cursor: pointer;
      box-shadow: 0 6px 12px rgba(0,0,0,0.12);
    }
    a.btn:focus { outline: 3px solid rgba(209,0,104,0.14); outline-offset: 3px; }
    #message { margin-top: 14px; font-size:1rem; color:var(--accent); min-height:1.2em }

    @media (prefers-reduced-motion: reduce) { .heart{ animation:none } }
    .sr-only {
      position:absolute!important; height:1px;width:1px;overflow:hidden;clip:rect(1px,1px,1px,1px);
      white-space:nowrap;clip-path:inset(50%);border:0;padding:0;margin:-1px;
    }
  </style>
</head>
<body>
  <main class="card" role="main" aria-labelledby="title">
    <span class="heart" aria-hidden="true">❤️</span>
    <span class="sr-only" id="heart-label">Animated heart</span>
    <h1 id="title">Will you be my Valentine?</h1>
    <p class="lead">A little question — big feelings 💕</p>

    <!-- Link opens in a new tab -->
    <a id="yesLink" class="btn"
       href="https://brunthashhinikumar.github.io/Bruntha/"
       target="_blank"
       rel="noopener noreferrer"
       role="button"
       aria-describedby="message">YES</a>

    <div id="message" role="status" aria-live="polite"></div>
  </main>

  <script>
    (function () {
      const link = document.getElementById('yesLink');
      const msg = document.getElementById('message');

      function showLove() {
        msg.textContent = "Yay! 💕 I’m so happy! 🥰💐";
        // Visual feedback on the link after acceptance
        link.textContent = "Hooray!";
        link.setAttribute('aria-disabled', 'true');
        link.style.opacity = '0.8';
        link.style.pointerEvents = 'none';
      }

      link.addEventListener('click', function (ev) {
        const href = link.getAttribute('href') || '';
        // If href is a placeholder, prevent navigation and show the message
        if (href === '#' || href.trim() === '' || href.startsWith('javascript:')) {
          ev.preventDefault();
          showLove();
          return;
        }

        // For target="_blank", the current page remains open — show feedback there.
        try { showLove(); } catch (e) { /* ignore */ }
        // Allow the navigation to proceed in the new tab.
      });
    })();
  </script>
</body>
</html>
