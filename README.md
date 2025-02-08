# trydar
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Página Divertida</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
            transition: background-color 0.5s;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            background-color: #0077cc;
            color: white;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <h1>¡Haz clic para cambiar el color!</h1>
    <button onclick="cambiarColor()">Cambiar Color</button>

    <script>
        function cambiarColor() {
            const colores = ["#ffcc00", "#ccff00", "#00ccff", "#ff00cc", "#cc00ff"];
            const colorAleatorio = colores[Math.floor(Math.random() * colores.length)];
            document.body.style.backgroundColor = colorAleatorio;
        }
    </script>
</body>
</html>
