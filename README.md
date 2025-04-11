<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday Kittu Baccha</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">
  <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
  <style>
    html, body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: url('https://images.unsplash.com/photo-1508615070457-7baeba4003ab?auto=format&fit=crop&w=1950&q=80') no-repeat center center fixed;
      background-size: cover;
      color: #fff;
      overflow-x: hidden;
    }

    .hidden {
      display: none;
    }

    .centered {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
      padding: 20px;
      background-color: rgba(0, 0, 0, 0.7);
    }

    h1, h2 {
      font-family: 'Great Vibes', cursive;
    }

    .mirror {
      -webkit-transform: scaleX(-1);
      transform: scaleX(-1);
    }

    .glow {
      color: #ff6ec4;
      text-shadow: 0 0 10px #ff6ec4, 0 0 20px #ff6ec4, 0 0 30px #ff6ec4;
    }

    input, button {
      padding: 10px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      margin-top: 10px;
    }

    canvas, .balloon {
      position: fixed;
      pointer-events: none;
      z-index: 1;
    }

    .balloon {
      animation: float 8s ease-in-out infinite;
    }

    @keyframes float {
      0% { transform: translateY(100vh); opacity: 1; }
      100% { transform: translateY(-100vh); opacity: 0; }
    }

    .main-content {
      z-index: 2;
      position: relative;
    }

    .wish-box {
      margin: 30px auto;
      max-width: 500px;
      padding: 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 10px;
    }

    .wish-box button {
      background-color: #ff9ecb;
      color: #000;
      font-weight: bold;
      cursor: pointer;
    }

    .gallery img {
      width: 300px;
      border-radius: 20px;
      margin: 10px;
    }

    footer {
      margin: 40px;
      font-size: 1.2em;
      color: #ffd1dc;
    }

    .letter {
      padding: 20px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 15px;
      max-width: 800px;
      margin: 50px auto;
    }
  </style>
</head>
<body>
  <!-- Fireworks Canvas -->
  <canvas id="fireworks"></canvas>

  <!-- Falling Stars Background -->
  <canvas id="stars" style="z-index: 0;"></canvas>

  <!-- Balloons -->
  <img src="https://i.postimg.cc/RZFTbTG1/balloon.png" class="balloon" style="left: 20%;" />
  <img src="https://i.postimg.cc/RZFTbTG1/balloon.png" class="balloon" style="left: 50%;" />
  <img src="https://i.postimg.cc/RZFTbTG1/balloon.png" class="balloon" style="left: 80%;" />

  <!-- Lock Screen -->
  <div id="lockScreen" class="centered">
    <h1 class="glow">🔒 Enter Password to Unlock</h1>
    <input type="password" id="password" placeholder="Enter password">
    <p>
      <input type="checkbox" id="agree"> 
      I am Aman's girlfriend and I promise that I will marry Aman only. If I am not able to marry Aman then I will spend my whole life as a pig.
    </p>
    <button onclick="unlock()">Enter</button>
    <p id="error" style="color: pink;"></p>
  </div>

  <!-- Main Content -->
  <div id="mainContent" class="hidden main-content">
    <div class="centered">
      <h1 class="glow" style="font-size: 4em;" data-aos="zoom-in">🎉 Happy Birthday Kittu Baccha 🎉</h1>
      <h2 class="mirror glow" data-aos="fade-up">4 June</h2>
    </div>

    <div class="centered" data-aos="fade-up" data-aos-delay="200">
      <p>You light up my world like no one else. Your smile is the sunrise to my soul and your love is the starlight that guides me every night. Being with you makes everything feel magical.</p>
      <p class="glow">You're not just my love, you're my dream come true, my forever person.</p>
    </div>

    <div class="gallery centered" data-aos="fade-up">
      <img src="https://i.postimg.cc/Nf7H85sT/Chat-GPT-Image-Mar-30-2025-03-48-17-PM.png" />
      <img src="https://i.postimg.cc/6ppydc1J/Chat-GPT-Image-Mar-30-2025-04-13-31-PM.png" />
      <img src="https://i.postimg.cc/VNyPYLtG/Chat-GPT-Image-Mar-30-2025-03-47-49-PM.png" />
      <img src="https://i.postimg.cc/d0RpwRw3/Chat-GPT-Image-Mar-30-2025-at-05-56-42-PM.png" />
    </div>

    <div class="wish-box centered" data-aos="zoom-in">
      <h3>🎁 Tap for a Birthday Wish</h3>
      <button onclick="generateWish()">Get Wish</button>
      <p id="wishText"></p>
    </div>

    <div class="letter" data-aos="fade-up">
      <h2>💌 A Letter from Aman</h2>
      <p>Dear Kittu Baccha,</p>
      <p>You are the most precious person in my life. Every second I spend with you feels like a beautiful dream. Without you, my life has no meaning. You complete me in every possible way. I want to grow old with you, laugh with you, cry with you, and share every chapter of life with you.</p>
      <p>My only wish is to call you mine, forever. No matter what comes, I’ll be by your side. Always.</p>
      <p>Forever yours,<br>– Aman 💖</p>
    </div>

    <footer>
      Made with 💕 for Kittu Baccha
    </footer>
  </div>

  <!-- Scripts -->
  <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
  <script>
    AOS.init({ once: true });

    function unlock() {
      const pass = document.getElementById('password').value;
      const agree = document.getElementById('agree').checked;
      const error = document.getElementById('error');

      if (pass === "1205" && agree) {
        document.getElementById('lockScreen').style.display = "none";
        document.getElementById('mainContent').classList.remove("hidden");
      } else {
        error.innerText = "Wrong password or you did not agree to the terms!";
      }
    }

    const wishes = [
      "Wishing you endless smiles today and always!",
      "You deserve the whole universe today, my love!",
      "To the one who owns my heart — Happy Birthday!",
      "May your day be as lovely as your soul.",
      "My forever starts with you. Happy Birthday!",
    ];

    function generateWish() {
      const wish = wishes[Math.floor(Math.random() * wishes.length)];
      document.getElementById('wishText').innerText = wish;
    }

    // Fireworks on click
    const canvas = document.getElementById('fireworks');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    let particles = [];

    class Particle {
      constructor(x, y, dx, dy, color, life) {
        this.x = x;
        this.y = y;
        this.dx = dx;
        this.dy = dy;
        this.color = color;
        this.life = life;
        this.opacity = 1;
      }

      update() {
        this.x += this.dx;
        this.y += this.dy;
        this.dy += 0.05;
        this.life--;
        this.opacity = this.life / 100;
      }

      draw() {
        ctx.beginPath();
        ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(${this.color},${this.opacity})`;
        ctx.fill();
      }
    }

    function createFirework(x, y) {
      const color = `${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}`;
      for (let i = 0; i < 50; i++) {
        const angle = Math.random() * 2 * Math.PI;
        const speed = Math.random() * 5;
        particles.push(new Particle(x, y, Math.cos(angle) * speed, Math.sin(angle) * speed, color, 100));
      }
    }

    function animateFireworks() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach((p, i) => {
        p.update();
        p.draw();
        if (p.life <= 0) particles.splice(i, 1);
      });
      requestAnimationFrame(animateFireworks);
    }

    animateFireworks();
    document.addEventListener("click", (e) => createFirework(e.clientX, e.clientY));

    // Falling stars
    const starCanvas = document.getElementById('stars');
    const starCtx = starCanvas.getContext('2d');
    starCanvas.width = window.innerWidth;
    starCanvas.height = window.innerHeight;
    let stars = [];

    for (let i = 0; i < 100; i++) {
      stars.push({
        x: Math.random() * starCanvas.width,
        y: Math.random() * starCanvas.height,
        radius: Math.random() * 1.5,
        speedY: Math.random() * 0.8 + 0.2,
      });
    }

    function drawStars() {
      starCtx.clearRect(0, 0, starCanvas.width, starCanvas.height);
      starCtx.fillStyle = 'white';
      stars.forEach(s => {
        starCtx.beginPath();
        starCtx.arc(s.x, s.y, s.radius, 0, Math.PI * 2);
        starCtx.fill();
        s.y += s.speedY;
        if (s.y > starCanvas.height) s.y = 0;
      });
      requestAnimationFrame(drawStars);
    }

    drawStars();
  </script>
</body>
</html>
