<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Aventuras do Bem</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(180deg, #87CEFA, #fff);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    canvas {
      background: #4CAF50;
      border: 4px solid #222;
      border-radius: 10px;
    }

    #hud {
      position: absolute;
      top: 10px;
      left: 10px;
      color: #222;
      font-weight: bold;
      font-size: 18px;
      background: rgba(255, 255, 255, 0.7);
      padding: 5px 10px;
      border-radius: 6px;
    }
  </style>
</head>
<body>
  <div id="hud">Pontos: <span id="score">0</span></div>
  <canvas id="game" width="800" height="400"></canvas>

  <script>
    const canvas = document.getElementById("game");
    const ctx = canvas.getContext("2d");

    let player = { x: 50, y: 300, w: 40, h: 40, dy: 0, jump: false };
    let gravity = 0.8;
    let ground = 340;
    let obstacles = [];
    let score = 0;
    let gameOver = false;

    function drawPlayer() {
      ctx.fillStyle = "#FFD700";
      ctx.fillRect(player.x, player.y, player.w, player.h);
    }

    function drawObstacle(o) {
      ctx.fillStyle = "#B22222";
      ctx.fillRect(o.x, o.y, o.w, o.h);
    }

    function update() {
      if (gameOver) return;

      ctx.clearRect(0, 0, canvas.width, canvas.height);

      // Player jump
      if (player.jump) {
        player.dy -= gravity;
        player.y -= player.dy;
        if (player.y >= ground) {
          player.y = ground;
          player.jump = false;
          player.dy = 0;
        }
      }

      // Obstacles
      obstacles.forEach((o, i) => {
        o.x -= 5;
        if (o.x + o.w < 0) {
          obstacles.splice(i, 1);
          score++;
          document.getElementById("score").innerText = score;
        }

        // Collision
        if (
          player.x < o.x + o.w &&
          player.x + player.w > o.x &&
          player.y < o.y + o.h &&
          player.y + player.h > o.y
        ) {
          gameOver = true;
          ctx.fillStyle = "rgba(0,0,0,0.7)";
          ctx.fillRect(0, 0, canvas.width, canvas.height);
          ctx.fillStyle = "#fff";
          ctx.font = "32px Arial";
          ctx.fillText("💥 Fim de jogo!", 300, 180);
          ctx.font = "20px Arial";
          ctx.fillText("Pressione Enter para recomeçar", 270, 220);
        }
      });

      // Draw ground
      ctx.fillStyle = "#006400";
      ctx.fillRect(0, ground + 40, canvas.width, 80);

      drawPlayer();
      obstacles.forEach(drawObstacle);

      requestAnimationFrame(update);
    }

    function spawnObstacle() {
      if (gameOver) return;
      const height = 40 + Math.random() * 30;
      obstacles.push({ x: 800, y: ground + 40 - height, w: 30, h: height });
      setTimeout(spawnObstacle, 1200 + Math.random() * 1000);
    }

    function jump() {
      if (!player.jump && !gameOver) {
        player.jump = true;
        player.dy = -12;
      }
    }

    document.addEventListener("keydown", (e) => {
      if (e.code === "Space" || e.code === "ArrowUp") jump();
      if (e.code === "Enter" && gameOver) {
        obstacles = [];
        score = 0;
        gameOver = false;
        player.y = ground;
        document.getElementById("score").innerText = score;
        update();
        spawnObstacle();
      }
    });

    update();
    spawnObstacle();
  </script>
</body>
</html>
