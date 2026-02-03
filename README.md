<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Be My Pixel Valentine 💖</title>
<style>
  /* Pixel style font */
  @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

  body {
    margin: 0;
    padding: 0;
    background: #ffe6f7;
    font-family: 'Press Start 2P', cursive;
    overflow-x: hidden;
    color: #d6336c;
    user-select: none;
    position: relative;
  }
  h1 {
    margin-top: 50px;
    font-size: 18px;
    text-align: center;
    text-shadow: 2px 2px 0 #ff80bf;
  }

  /* Container for buttons and result */
  .container {
    max-width: 400px;
    margin: 20px auto;
    text-align: center;
  }

  button {
    background: #ff66aa;
    border: 3px solid #d6336c;
    color: white;
    font-family: 'Press Start 2P', cursive;
    font-size: 14px;
    padding: 15px 30px;
    margin: 10px;
    border-radius: 10px;
    cursor: pointer;
    box-shadow: 0 0 8px #ff80bf;
    transition: background 0.3s;
  }
  button:hover {
    background: #d6336c;
  }
  button:disabled {
    background: #ffa1cc;
    border-color: #ffb7d8;
    cursor: default;
  }

  #result {
    margin-top: 30px;
    font-size: 16px;
    min-height: 40px;
    color: #d6336c;
    text-shadow: 1px 1px 0 #ff80bf;
  }

  /* Pixel heart floating background */
  .heart {
    position: fixed;
    width: 20px;
    height: 20px;
    background: url('https://i.ibb.co/fD5Fphg/pixel-heart.png') no-repeat center/contain;
    animation: floatUp linear infinite;
    pointer-events: none;
    opacity: 0.8;
  }
  @keyframes floatUp {
    0% {
      transform: translateY(100vh) scale(1);
      opacity: 0.8;
    }
    100% {
      transform: translateY(-50px) scale(0.8);
      opacity: 0;
    }
  }

  /* Confetti and emoji containers */
  #confetti, #cryingEmoji {
    position: fixed;
    top: 0; left: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    overflow: hidden;
    z-index: 9999;
  }

  /* Pixel GIF style */
  #pixelGif {
    display: block;
    margin: 25px auto 0 auto;
    width: 150px;
    image-rendering: pixelated;
  }
</style>
</head>
<body>

<h1>Will you be my Valentine? 💖</h1>

<div class="container">
  <button id="yesBtn">Yes! 💘</button>
  <button id="noBtn">No 😢</button>

  <div id="result"></div>
  <img id="pixelGif" style="display:none" alt="pixel gif" />
</div>

<div id="confetti"></div>
<div id="cryingEmoji"></div>

<script>
  const yesBtn = document.getElementById('yesBtn');
  const noBtn = document.getElementById('noBtn');
  const result = document.getElementById('result');
  const confettiContainer = document.getElementById('confetti');
  const cryingContainer = document.getElementById('cryingEmoji');
  const pixelGif = document.getElementById('pixelGif');

  yesBtn.onclick = () => {
    disableButtons();
    result.textContent = "You just made me the happiest person ever ❤️";
    pixelGif.src = "https://media4.giphy.com/media/v1.Y2lkPTZjMDliOTUyZWdoOXlhODRpZ2c1a2tmajl0bWdtaW9pejd1c3BrOXF3dGVmZ2V2aiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/OuQmhmAAdJFLi/giphy.gif"; // pixel heart gif
    pixelGif.style.display = "block";
    launchConfetti();
  };

  noBtn.onclick = () => {
    disableButtons();
    result.textContent = "WHYYYY! 😢";
    pixelGif.src = "https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUydndrYWFubXFocHhxYnRlaXF2bG11aGMzMGIyejF6Y3JpNXM4d3VxNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Xs4TtKRfCTE9G/giphy.gif"; // pixel crying emoji gif
    pixelGif.style.display = "block";
    launchCryingEmojis();
  };

  function disableButtons() {
    yesBtn.disabled = true;
    noBtn.disabled = true;
  }

  // Create floating pixel hearts in background
  function createHearts() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.style.left = Math.random() * window.innerWidth + 'px';
    heart.style.animationDuration = (5 + Math.random() * 5) + 's';
    heart.style.opacity = (0.5 + Math.random() * 0.5);
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 10000);
  }
  // Continuously create hearts every 300ms
  setInterval(createHearts, 300);

  // Confetti for yes - updated to pixel heart images
  function launchConfetti() {
    const confettiCount = 100;
    for (let i = 0; i < confettiCount; i++) {
      const confetti = document.createElement('img');
      confetti.src = 'https://i.ibb.co/fD5Fphg/pixel-heart.png';  // pixel heart image
      confetti.style.position = 'absolute';
      confetti.style.width = '15px';
      confetti.style.height = '15px';
      confetti.style.left = Math.random() * window.innerWidth + 'px';
      confetti.style.top = '-20px';
      confetti.style.opacity = '0.9';
      confetti.style.animation = `fallConfetti 3s ease forwards`;
      confettiContainer.appendChild(confetti);
      setTimeout(() => confetti.remove(), 3000);
    }
  }

  // Crying emoji rain for no
  function launchCryingEmojis() {
    const emojiChar = "😭";
    for (let i = 0; i < 50; i++) {
      const emoji = document.createElement('div');
      emoji.textContent = emojiChar;
      emoji.style.position = 'absolute';
      emoji.style.fontSize = '20px';
      emoji.style.left = Math.random() * window.innerWidth + 'px';
      emoji.style.top = '-20px';
      emoji.style.opacity = '0.9';
      emoji.style.animation = `fallCry 4s linear forwards`;
      cryingContainer.appendChild(emoji);
      setTimeout(() => emoji.remove(), 4000);
    }
  }

  // Keyframes for falling confetti and crying emojis
  const style = document.createElement('style');
  style.textContent = `
    @keyframes fallConfetti {
      0% {transform: translateY(0) rotate(0deg);}
      100% {transform: translateY(100vh) rotate(360deg); opacity: 0;}
    }
    @keyframes fallCry {
      0% {transform: translateY(0);}
      100% {transform: translateY(100vh); opacity: 0;}
    }
  `;
  document.head.appendChild(style);
</script>

</body>
</html>
