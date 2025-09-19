<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>¿Me amas?</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: white;
            color: black;
            font-family: Arial, sans-serif;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            text-align: center;
            display: none;
        }

        .container.active {
            display: block;
        }

        h1 {
            margin-bottom: 30px;
            font-size: 2em;
        }

        button {
            padding: 10px 20px;
            margin: 10px;
            font-size: 1em;
            cursor: pointer;
            border: 2px solid black;
            background-color: white;
            transition: background-color 0.3s, color 0.3s;
        }

        button:hover {
            background-color: black;
            color: white;
        }

        .respuesta {
            margin-top: 30px;
            font-size: 1.5em;
            color: #d11a2a;
        }
    </style>
</head>
<body>
    <!-- Pregunta 1 -->
    <div class="container active" id="paso1">
        <h1>¿Me amas?</h1>
        <button onclick="mostrarRespuesta('si')">Sí</button>
        <button onclick="mostrarRespuesta('no')">No</button>
        <div id="respuesta1" class="respuesta"></div>
    </div>

    <!-- Pregunta 2 -->
    <div class="container" id="paso2">
        <h1>¿Cuánto?</h1>
        <button onclick="cuantoRespuesta('poco')">Un poco</button>
        <button onclick="cuantoRespuesta('mucho')">Mucho</button>
    </div>

    <!-- Pregunta 3 -->
    <div class="container" id="paso3">
        <h1>¿Por qué hiciste todo si me amabas mucho?</h1>
        <div class="respuesta">Porque el amor verdadero a veces también duele 💔</div>
    </div>

    <script>
        function mostrarRespuesta(opcion) {
            const respuesta1 = document.getElementById('respuesta1');
            if (opcion === 'si') {
                respuesta1.textContent = "Yo también ❤️";
                setTimeout(() => {
                    mostrarPaso('paso1', 'paso2');
                }, 1500);
            } else {
                respuesta1.textContent = "Mientes 😢";
            }
        }

        function cuantoRespuesta(nivel) {
            if (nivel === 'poco') {
                // Pantalla blanca con emoji de enojo
                document.body.innerHTML = '<div style="font-size: 5em; text-align: center; margin-top: 20%;">😠</div>';
                document.body.style.backgroundColor = 'white';
            } else if (nivel === 'mucho') {
                mostrarPaso('paso2', 'paso3');
            }
        }

        function mostrarPaso(actual, siguiente) {
            document.getElementById(actual).classList.remove('active');
            document.getElementById(siguiente).classList.add('active');
        }
    </script>
</body>
</html>
