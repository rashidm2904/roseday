let canvas, ctx, roseX, roseY, basketX, score, speed, gameRunning;

function startGame() {
    canvas = document.getElementById("gameCanvas");
    ctx = canvas.getContext("2d");
    canvas.width = Math.min(window.innerWidth * 0.9, 400);
    canvas.height = 450;
    canvas.style.display = "block";

    roseX = Math.random() * (canvas.width - 50);
    roseY = 0;
    basketX = canvas.width / 2 - 50;
    score = 0;
    speed = 3;
    gameRunning = true;

    document.addEventListener("keydown", moveBasket);
    canvas.addEventListener("touchmove", touchMoveBasket);

    gameLoop();
}

function gameLoop() {
    if (!gameRunning) return;

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Draw Falling Rose
    ctx.fillStyle = "red";
    ctx.beginPath();
    ctx.arc(roseX + 25, roseY + 25, 20, 0, Math.PI * 2);
    ctx.shadowBlur = 10;
    ctx.shadowColor = "pink";
    ctx.fill();

    // Draw Basket
    ctx.fillStyle = "brown";
    ctx.fillRect(basketX, canvas.height - 50, 100, 20);

    // Move rose down
    roseY += speed;

    // Check if caught
    if (roseY + 25 >= canvas.height - 50 && roseX >= basketX && roseX <= basketX + 100) {
        score++;
        speed += 0.5;
        roseX = Math.random() * (canvas.width - 50);
        roseY = 0;
        updateScore();
        showPopup();
    }

    // Check if rose falls off screen
    if (roseY >= canvas.height) {
        gameOver();
    }

    requestAnimationFrame(gameLoop);
}

function moveBasket(event) {
    if (event.key === "ArrowLeft" && basketX > 0) basketX -= 30;
    if (event.key === "ArrowRight" && basketX < canvas.width - 100) basketX += 30;
}

// Mobile support (touch move)
function touchMoveBasket(event) {
    let touchX = event.touches[0].clientX - canvas.getBoundingClientRect().left;
    basketX = touchX - 50;
    if (basketX < 0) basketX = 0;
    if (basketX > canvas.width - 100) basketX = canvas.width - 100;
}

// Update Score
function updateScore() {
    document.getElementById("score").innerText = score;
}

// Show Pop-up Messages
function showPopup() {
    let popup = document.getElementById("popup");
    popup.innerText = `Aliza caught a rose! 🌹 +1 Point!`;
    popup.style.display = "block";
    setTimeout(() => { popup.style.display = "none"; }, 2000);
}

// End Game
function gameOver() {
    gameRunning = false;
    showLoveLetter();
}

function showLoveLetter() {
    let loveLetter = document.getElementById("love-letter");
    loveLetter.style.display = "block";
}
