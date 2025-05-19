<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Catch the Heart 💖</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      overflow: hidden;
      background: linear-gradient(to top right, #fceabb, #f8b500);
      font-family: 'Comic Sans MS', cursive, sans-serif;
    }
    #gameArea {
      position: relative;
      width: 100vw;
      height: 100vh;
    }
    .heart {
      position: absolute;
      font-size: 2rem;
      animation: fall 4s linear infinite;
      cursor: pointer;
    }
    @keyframes fall {
      0% {
        transform: translateY(-100px);
        opacity: 1;
      }
      100% {
        transform: translateY(100vh);
        opacity: 0;
      }
    }
    #scoreBoard {
      position: absolute;
      top: 10px;
      left: 10px;
      font-size: 1.5rem;
      color: #d63384;
      background: white;
      padding: 10px 20px;
      border-radius: 20px;
      box-shadow: 0 0 10px #ff6f91;
    }
    #message {
      position: absolute;
      bottom: 20px;
      width: 100%;
      text-align: center;
      font-size: 1.3rem;
      color: #6a0572;
      font-weight: bold;
    }
  </style>
</head>
<body>

<div id="gameArea">
  <div id="scoreBoard">Score: 0</div>
  <div id="message">You're amazing. You matter. 💕 Keep catching love!</div>
</div>

<audio autoplay loop>
  <source src="https://www.bensound.com/bensound-music/bensound-sunny.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

<script>
  const gameArea = document.getElementById('gameArea');
  const scoreBoard = document.getElementById('scoreBoard');
  let score = 0;

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.innerText = '💖';

    // Random horizontal position
    heart.style.left = Math.random() * (window.innerWidth - 50) + 'px';

    heart.addEventListener('click', () => {
      score += 1;
      scoreBoard.innerText = `Score: ${score}`;
      heart.remove();
    });

    gameArea.appendChild(heart);

    // Remove heart after it falls
    setTimeout(() => {
      heart.remove();
    }, 4000);
  }

  // Spawn hearts every 600ms
  setInterval(createHeart, 600);
</script>

</body>
</html>
