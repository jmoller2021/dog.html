<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Dog Runner Game</title>
  <style>
    body {
      margin: 0;
      font-family: sans-serif;
      background-color: #e0f7fa;
      overflow: hidden;
      text-align: center;
    }

    h1 {
      margin-top: 20px;
      color: #333;
    }

    #score {
      font-size: 24px;
      color: #444;
    }

    #gameArea {
      position: relative;
      width: 100%;
      height: 300px;
      background-color: #a7ffeb;
      border-top: 4px solid #26a69a;
      border-bottom: 4px solid #26a69a;
      overflow: hidden;
    }

    #dog {
      position: absolute;
      left: -100px;
      top: 120px;
      font-size: 48px;
      cursor: pointer;
      user-select: none;
      transition: transform 0.1s;
    }

    #dog:active {
      transform: scale(1.2);
    }
  </style>
</head>
<body>

  <h1>🐶 Dog Runner Game</h1>
  <p id="score">Score: 0</p>

  <div id="gameArea">
    <div id="dog">🐶</div>
  </div>

  <script>
    const dog = document.getElementById('dog');
    const scoreDisplay = document.getElementById('score');
    const gameArea = document.getElementById('gameArea');

    let score = 0;
    let speed = 2;
    let position = -100;

    function moveDog() {
      position += speed;
      if (position > window.innerWidth) {
        position = -100; // restart offscreen
      }
      dog.style.left = position + 'px';
      requestAnimationFrame(moveDog);
    }

    dog.addEventListener('click', () => {
      score++;
      speed += 0.5;
      scoreDisplay.textContent = `Score: ${score}`;
      position = -100; // reset dog to start
    });

    moveDog();
  </script>

</body>
</html>
