// キャンバスとコンテキストの取得
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

// 下の壁アイテム用の状態
let bottomWallActive = false;
let bottomWallTimer = 0;
let itemDrops = [];

// Zキー加速用の状態
let boostActive = false;
let boostTimer = 0;
let paddleHue = 0;

// スコア表示用
let score = 0;

// パドルやボールの状態
let paddleX = 300;
const paddleWidth = 100;
const paddleHeight = 10;
const ballRadius = 8;
let speedMultiplier = 1;
let rightPressed = false;
let leftPressed = false;
let gameRunning = true;

let balls = [{
  x: 400,
  y: 300,
  dx: 2,
  dy: -2,
  trail: [],
  color: "white"
}];

let explosionParticles = [];

// 虹色エフェクト用の背景ボール
let backgroundBalls = [];
for (let i = 0; i < 30; i++) {
  backgroundBalls.push({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    radius: 10 + Math.random() * 10,
    hue: Math.random() * 360,
    dx: (Math.random() - 0.5) * 1,
    dy: (Math.random() - 0.5) * 1,
  });
}

// ブロック設定
const blockRowCount = 5;
const blockColumnCount = 10;
const blockWidth = 70;
const blockHeight = 20;
const blockPadding = 10;
const blockOffsetTop = 60;
const blockOffsetLeft = 35;

let blocks = [];
function initBlocks() {
  blocks = [];
  for (let c = 0; c < blockColumnCount; c++) {
    blocks[c] = [];
    for (let r = 0; r < blockRowCount; r++) {
      blocks[c][r] = { x: 0, y: 0, status: 1, color: `hsl(${Math.random() * 360}, 100%, 50%)` };
    }
  }
}
initBlocks();

function drawBlocks() {
  for (let c = 0; c < blockColumnCount; c++) {
    for (let r = 0; r < blockRowCount; r++) {
      if (blocks[c][r].status === 1) {
        const blockX = c * (blockWidth + blockPadding) + blockOffsetLeft;
        const blockY = r * (blockHeight + blockPadding) + blockOffsetTop;
        blocks[c][r].x = blockX;
        blocks[c][r].y = blockY;
        ctx.beginPath();
        ctx.rect(blockX, blockY, blockWidth, blockHeight);
        ctx.fillStyle = blocks[c][r].color;
        ctx.fill();
        ctx.closePath();
      }
    }
  }
}

function drawBackgroundBalls() {
  for (let ball of backgroundBalls) {
    ball.x += ball.dx;
    ball.y += ball.dy;
    ball.hue = (ball.hue + 1) % 360;

    if (ball.x < -20) ball.x = canvas.width + 20;
    if (ball.x > canvas.width + 20) ball.x = -20;
    if (ball.y < -20) ball.y = canvas.height + 20;
    if (ball.y > canvas.height + 20) ball.y = -20;

    ctx.beginPath();
    ctx.arc(ball.x, ball.y, ball.radius, 0, Math.PI * 2);
    ctx.fillStyle = `hsl(${ball.hue}, 100%, 60%)`;
    ctx.fill();
    ctx.closePath();
  }
}

function drawScore() {
  ctx.font = "20px monospace";
  ctx.fillStyle = "white";
  ctx.textAlign = "left";
  ctx.fillText("SCORE: " + score.toString().padStart(3, '0'), 10, 30);
}

// 省略: 他の関数（drawPaddle, drawBall, drawItems, drawExplosions など）は変更せず続く

function collisionDetection(ball) {
  for (let c = 0; c < blockColumnCount; c++) {
    for (let r = 0; r < blockRowCount; r++) {
      const b = blocks[c][r];
      if (b.status === 1) {
        if (
          ball.x > b.x &&
          ball.x < b.x + blockWidth &&
          ball.y > b.y &&
          ball.y < b.y + blockHeight
        ) {
          ball.dy = -ball.dy;
          b.status = 0;
          score++;
          if (Math.random() < 0.1) createItem(b.x + blockWidth / 2, b.y);
          if (score === blockRowCount * blockColumnCount) endGame(true);
        }
      }
    }
  }
}

function draw() {
  if (!gameRunning) return;
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  drawBackgroundBalls();
  drawScore();
  drawBlocks();
  drawPaddle();
  drawBottomWall();
  drawExplosions();

  if (boostActive) {
    boostTimer--;
    if (boostTimer <= 0) boostActive = false;
  }

  const paddleSpeed = boostActive ? 12 : 6;

  balls.forEach(ball => {
    drawBall(ball);
    collisionDetection(ball);

    if (ball.x + ball.dx * speedMultiplier > canvas.width - ballRadius || ball.x + ball.dx * speedMultiplier < ballRadius) {
      ball.dx = -ball.dx;
      ball.color = `hsl(${Math.random() * 360}, 100%, 60%)`;
      createWallBounceEffect(ball.x, ball.y);
    }
    if (ball.y + ball.dy * speedMultiplier < ballRadius) {
      ball.dy = -ball.dy;
      ball.color = `hsl(${Math.random() * 360}, 100%, 60%)`;
      createWallBounceEffect(ball.x, ball.y);
    } else if (ball.y + ball.dy * speedMultiplier > canvas.height - ballRadius) {
      if (bottomWallActive) {
        ball.dy = -Math.abs(ball.dy);
      } else if (ball.x > paddleX && ball.x < paddleX + paddleWidth) {
        ball.dy = -ball.dy;
      } else {
        balls = balls.filter(b => b !== ball);
        if (balls.length === 0) {
          endGame(false);
          return;
        }
      }
    }

    ball.x += ball.dx * speedMultiplier;
    ball.y += ball.dy * speedMultiplier;
  });

  drawItems();

  if (rightPressed && paddleX < canvas.width - paddleWidth) {
    paddleX += paddleSpeed * speedMultiplier;
  } else if (leftPressed && paddleX > 0) {
    paddleX -= paddleSpeed * speedMultiplier;
  }

  requestAnimationFrame(draw);
}

draw();
