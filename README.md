<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Juego de Snake</title>
    <style>
        canvas {
            display: block;
            margin: 0 auto;
            background-color: #000;
        }
    </style>
</head>
<body>
    <h1 style="text-align: center;">Juego de Snake</h1>
    <canvas id="gameCanvas" width="400" height="400"></canvas>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');

        let snake = [{ x: 200, y: 200 }];
        let direction = { x: 0, y: 0 };
        let food = { x: 0, y: 0 };
        let score = 0;

        function drawSnake() {
            ctx.fillStyle = 'lime';
            snake.forEach(part => ctx.fillRect(part.x, part.y, 10, 10));
        }

        function drawFood() {
            ctx.fillStyle = 'red';
            ctx.fillRect(food.x, food.y, 10, 10);
        }

        function update() {
            const head = { x: snake[0].x + direction.x * 10, y: snake[0].y + direction.y * 10 };
            snake.unshift(head);

            if (head.x === food.x && head.y === food.y) {
                score++;
                placeFood();
            } else {
                snake.pop();
            }
        }

        function placeFood() {
            food.x = Math.floor(Math.random() * 40) * 10;
            food.y = Math.floor(Math.random() * 40) * 10;
        }

        function gameLoop() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawSnake();
            drawFood();
            update();
            setTimeout(gameLoop, 100);
        }

        placeFood();
        gameLoop();

        window.addEventListener('keydown', e => {
            switch (e.key) {
                case 'ArrowUp': if (direction.y === 0) direction = { x: 0, y: -1 }; break;
                case 'ArrowDown': if (direction.y === 0) direction = { x: 0, y: 1 }; break;
                case 'ArrowLeft': if (direction.x === 0) direction = { x: -1, y: 0 }; break;
                case 'ArrowRight': if (direction.x === 0) direction = { x: 1, y: 0 }; break;
            }
        });
    </script>
</body>
</html>
