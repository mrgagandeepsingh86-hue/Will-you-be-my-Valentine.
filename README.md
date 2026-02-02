<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover" />
  <title>Will you be my Valentine?</title>

  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>

  <style>
    :root {
      --bg1: #ffd6e7;
      --bg2: #ffeef6;
      --card: #ffffffcc;
      --yes: #ff3b7a;
      --yesHover: #ff1f68;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      min-height: 100svh;
      display: grid;
      place-items: center;
      background:
        radial-gradient(circle at 10% 20%, #ffb3c6 0 120px, transparent 130px),
        radial-gradient(circle at 90% 30%, #ffc2d1 0 140px, transparent 150px),
        radial-gradient(circle at 50% 80%, #ffd6e7 0 160px, transparent 170px),
        radial-gradient(circle at top, var(--bg2), var(--bg1));
      font-family: system-ui, sans-serif;
      overflow: hidden;
      padding: 16px;
    }

    #confettiCanvas {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 9999;
    }

    .card {
      width: min(720px, 92vw);
      padding: 26px 22px;
      background: var(--card);
      backdrop-filter: blur(10px);
      border-radius: 22px;
      text-align: center;
      box-shadow: 0 18px 60px rgba(0,0,0,.15);
    }

    .art {
      width: min(280px, 85vw);
      margin: 0 auto 10px;
      display: block;
      filter: drop-shadow(0 10px 14px rgba(0,0,0,.12));
    }

    h1 {
      font-size: clamp(26px, 4vw, 44px);
      margin: 12px 0 18px;
    }

    .button-zone {
      position: relative;
      width: min(520px, 92%);
      height: 150px;
      margin: 0 auto;
      touch-action: none;
    }

    button {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      padding: 16px 24px;
      font-size: 18px;
      font-weight: 800;
      border-radius: 999px;
      border: none;
      cursor: pointer;
      box-shadow: 0 10px 24px rgba(0,0,0,.14);
      user-select: none;
      -webkit-tap-highlight-color: transparent;
    }

    #yesBtn {
      left: 18%;
      background: var(--yes);
      color: #fff;
    }

    #noBtn {
      left: 62%;
      background: #e5e7eb;
      color: #111827;
    }

    .hint {
      margin-top: 10px;
      font-size: 13px;
      opacity: .7;
    }

    .result {
      display: none;
      margin-top: 18px;
      animation: pop .35s ease;
    }

    .result h2 {
      font-size: clamp(30px, 4.5vw, 46px);
      margin: 10px 0;
    }

    @keyframes pop {
      from { transform: scale(.96); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }
  </style>
</head>

<body>
<canvas id="confettiCanvas"></canvas>

<main class="card">

<!-- CAT WITH HEARTS & FLOWERS -->
<svg class="art" viewBox="0 0 320 260" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="cat" x1="0" x2="1">
      <stop offset="0" stop-color="#ffe0c7"/>
      <stop offset="1" stop-color="#ffcfa8"/>
    </linearGradient>
  </defs>

  <!-- Floating hearts -->
  <g fill="#ff4d7d" opacity="0.9">
    <path d="M40 40 C40 25 60 25 60 40 C60 55 40 60 40 75 C40 60 20 55 20 40 C20 25 40 25 40 40Z"/>
    <path d="M280 50 C280 35 300 35 300 50 C300 65 280 70 280 85 C280 70 260 65 260 50 C260 35 280 35 280 50Z"/>
    <path d="M160 15 C160 0 180 0 180 15 C180 30 160 35 160 50 C160 35 140 30 140 15 C140 0 160 0 160 15Z"/>
  </g>

  <!-- Flowers -->
  <g transform="translate(30 180)">
    <circle cx="0" cy="0" r="10" fill="#ffb703"/>
    <circle cx="-12" cy="0" r="10" fill="#ffafcc"/>
    <circle cx="12" cy="0" r="10" fill="#ffafcc"/>
    <circle cx="0" cy="-12" r="10" fill="#ffafcc"/>
    <circle cx="0" cy="12" r="10" fill="#ffafcc"/>
  </g>

  <g transform="translate(290 185)">
    <circle cx="0" cy="0" r="10" fill="#ffb703"/>
    <circle cx="-12" cy="0" r="10" fill="#cdb4db"/>
    <circle cx="12" cy="0" r="10" fill="#cdb4db"/>
    <circle cx="0" cy="-12" r="10" fill="#cdb4db"/>
    <circle cx="0" cy="12" r="10" fill="#cdb4db"/>
  </g>

  <!-- Cat face -->
  <ellipse cx="160" cy="140" rx="90" ry="75" fill="url(#cat)"/>

  <!-- Ears -->
  <path d="M90 90 L60 40 L120 70 Z" fill="#ffcfa8"/>
  <path d="M230 90 L260 40 L200 70 Z" fill="#ffcfa8"/>

  <!-- Eyes -->
  <circle cx="130" cy="135" r="8"/>
  <circle cx="190" cy="135" r="8"/>

  <!-- Nose -->
  <path d="M160 145 C154 145 150 150 150 154
           C150 160 160 165 160 170
           C160 165 170 160 170 154
           C170 150 166 145 160 145Z"
        fill="#ff7aa2"/>

  <!-- Whiskers -->
  <line x1="110" y1="150" x2="70" y2="145" stroke="#555" stroke-width="2"/>
  <line x1="110" y1="160" x2="70" y2="165" stroke="#555" stroke-width="2"/>
  <line x1="210" y1="150" x2="250" y2="145" stroke="#555" stroke-width="2"/>
  <line x1="210" y1="160" x2="250" y2="165" stroke="#555" stroke-width="2"/>
</svg>

<h1>Komal, will you be my Valentine? 💖</h1>

<section class="button-zone" id="zone">
  <button id="yesBtn">Yes</button>
  <button id="noBtn">No</button>
</section>

<div class="hint" id="hint">“No” is running but love isn’t 🐱💗</div>

<section class="result" id="result">
  <h2>YAY! 🎉💐</h2>
</section>

</main>

<script>
const zone = document.getElementById("zone");
const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");
const result = document.getElementById("result");
const hint = document.getElementById("hint");
const confettiCanvas = document.getElementById("confettiCanvas");

function resizeConfettiCanvas() {
  const dpr = Math.max(1, window.devicePixelRatio || 1);
  confettiCanvas.width = window.innerWidth * dpr;
  confettiCanvas.height = window.innerHeight * dpr;
}
resizeConfettiCanvas();
window.addEventListener("resize", resizeConfettiCanvas);

const confettiInstance = confetti.create(confettiCanvas, { resize: false });

function fullScreenConfetti() {
  const end = Date.now() + 1500;
  (function frame() {
    confettiInstance({
      particleCount: 15,
      spread: 100,
      origin: { x: Math.random(), y: Math.random() * 0.4 }
    });
    if (Date.now() < end) requestAnimationFrame(frame);
  })();
}

let yesScale = 1;
function growYes() {
  yesScale = Math.min(2.2, yesScale + 0.1);
  yesBtn.style.transform = `translateY(-50%) scale(${yesScale})`;
}

function clamp(n, min, max) {
  return Math.max(min, Math.min(max, n));
}

function moveNo(px, py) {
  const z = zone.getBoundingClientRect();
  const b = noBtn.getBoundingClientRect();
  let dx = (b.left + b.width/2) - px;
  let dy = (b.top + b.height/2) - py;
  let mag = Math.hypot(dx, dy) || 1;
  dx /= mag; dy /= mag;

  let newLeft = (b.left - z.left) + dx * 150;
  let newTop  = (b.top - z.top) + dy * 150;

  noBtn.style.left = clamp(newLeft, 0, z.width - b.width) + "px";
  noBtn.style.top  = clamp(newTop, 0, z.height - b.height) + "px";
  growYes();
}

zone.addEventListener("pointermove", e => {
  const b = noBtn.getBoundingClientRect();
  const d = Math.hypot((b.left+b.width/2)-e.clientX,(b.top+b.height/2)-e.clientY);
  if (d < 140) moveNo(e.clientX, e.clientY);
});

yesBtn.addEventListener("click", () => {
  zone.style.display = "none";
  hint.style.display = "none";
  result.style.display = "block";
  fullScreenConfetti();
});
</script>

</body>
</html>
