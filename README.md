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
      touch-action:
