<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Invitation for My Love</title>

  <!-- Romantic Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Allura&family=Playfair+Display:wght@400;700&family=Cormorant+Garamond:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      min-height: 100vh;
      background: linear-gradient(135deg, #140414, #2b0f2b, #140414);
      font-family: 'Cormorant Garamond', serif;
      overflow-x: hidden;
    }

    /* Background hearts */
    .bg-animation {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
    }

    .floating-heart {
      position: absolute;
      opacity: 0.35;
      animation: float 14s infinite ease-in-out;
    }

    @keyframes float {
      0% { transform: translateY(110vh) scale(0.5); opacity: 0; }
      15% { opacity: .4; }
      85% { opacity: .4; }
      100% { transform: translateY(-120vh) scale(1.3) rotate(360deg); opacity: 0; }
    }

    .invitation-container {
      position: relative;
      z-index: 5;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 40px 20px;
    }

    /* Names */
    .names {
      font-family: 'Allura', cursive;
      font-size: 4.5rem;
      color: #ffd700;
      text-align: center;
      text-shadow: 0 0 25px rgba(255,215,0,.6);
      margin-bottom: 40px;
    }

    .ampersand {
      display: block;
      font-family: 'Great Vibes', cursive;
      font-size: 3rem;
      color: #ff69b4;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%,100%{transform:scale(1);}
      50%{transform:scale(1.2);}
    }

    /* Card */
    .invitation-card {
      background: rgba(255,255,255,0.06);
      backdrop-filter: blur(12px);
      border-radius: 30px;
      padding: 50px 40px;
      max-width: 700px;
      text-align: center;
      box-shadow: 0 20px 60px rgba(0,0,0,.6);
      border: 1px solid rgba(255,215,0,.3);
    }

    .invitation-title {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      letter-spacing: 4px;
      color: #fff;
      margin-bottom: 25px;
    }

    .invitation-text {
      font-size: 1.35rem;
      line-height: 2;
      color: #eee;
    }

    .highlight {
      display: block;
      font-size: 1.6rem;
      color: #ffd700;
      margin: 20px 0;
      font-weight: 600;
    }

    .date-section {
      margin: 40px 0;
      padding: 25px;
      border-radius: 20px;
      background: rgba(255,105,180,.12);
      border: 1px solid rgba(255,105,180,.3);
    }

    .date-label {
      letter-spacing: 3px;
      font-size: .9rem;
      color: #ff69b4;
      margin-bottom: 10px;
    }

    .date-value {
      font-size: 2rem;
      color: #fff;
    }

    .time-value {
      font-family: 'Great Vibes', cursive;
      font-size: 1.6rem;
      color: #ffd700;
    }

    .rsvp-section {
      margin-top: 45px;
      text-align: center;
    }

    .rsvp-btn {
      padding: 16px 45px;
      border-radius: 50px;
      font-size: 1.1rem;
      border: none;
      cursor: pointer;
      letter-spacing: 2px;
      transition: .4s;
      margin: 10px;
    }

    .btn-accept {
      background: linear-gradient(45deg,#ff1493,#ff69b4);
      color: white;
      box-shadow: 0 10px 30px rgba(255,20,147,.4);
    }

    .btn-accept:hover {
      transform: translateY(-4px) scale(1.05);
    }

    .btn-decline {
      background: transparent;
      border: 2px solid #777;
      color: #aaa;
    }

    .footer-quote {
      margin-top: 40px;
      font-family: 'Great Vibes', cursive;
      font-size: 1.8rem;
      color: #ffd700;
      opacity: .85;
      text-align: center;
    }

    /* Modal */
    .modal-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,.95);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 50;
    }

    .modal-overlay.active { display: flex; }

    .modal-content {
      background: linear-gradient(135deg,#2d1b2d,#140414);
      padding: 60px;
      border-radius: 30px;
      border: 2px solid #ffd700;
      text-align: center;
    }

    .modal-title {
      font-family: 'Great Vibes', cursive;
      font-size: 3rem;
      color: #ffd700;
      margin-bottom: 20px;
    }
  </style>
</head>

<body>

<div class="bg-animation" id="bg"></div>

<div class="invitation-container">

  <div class="names">
    Miti Jalal
    <span class="ampersand">&</span>
    Eva
  </div>

  <div class="invitation-card">
    <h1 class="invitation-title">You're Invited</h1>

    <p class="invitation-text">
      To a magical evening with
      <span class="highlight">Dinner & a Moonlight Walk</span>
      <br>
      Eva, I want this night to be ours alone,
      where time slows and hearts speak softly.
    </p>

    <div class="date-section">
      <div class="date-label">Save the Date</div>
      <div class="date-value" id="date"></div>
      <div class="time-value">8:00 PM</div>
    </div>
  </div>

  <div class="rsvp-section">
    <button class="rsvp-btn btn-accept" onclick="accept()">Yes, I’m Yours</button>
    <button class="rsvp-btn btn-decline" onclick="alert('You can’t escape destiny 💕')">Maybe…</button>
  </div>

  <div class="footer-quote">
    “With you, every moment becomes forever.”
  </div>
</div>

<div class="modal-overlay" id="modal">
  <div class="modal-content">
    <div class="modal-title">Eva 💖</div>
    <p style="color:white;font-size:1.3rem;">
      I knew your heart would say yes.<br>
      I’ll be waiting… ✨
    </p>
  </div>
</div>

<script>
  function accept(){
    document.getElementById("modal").classList.add("active");
  }

  function hearts(){
    const bg = document.getElementById("bg");
    const icons = ["💖","💕","💘","✨"];
    for(let i=0;i<25;i++){
      const h = document.createElement("div");
      h.className="floating-heart";
      h.textContent = icons[Math.floor(Math.random()*icons.length)];
      h.style.left = Math.random()*100+"%";
      h.style.fontSize = 15+Math.random()*25+"px";
      h.style.animationDuration = 10+Math.random()*8+"s";
      bg.appendChild(h);
    }
  }

  const d = new Date();
  document.getElementById("date").innerText =
    d.toLocaleDateString("en-US",{weekday:"long",month:"long",day:"numeric"});

  hearts();
</script>

</body>
</html>
