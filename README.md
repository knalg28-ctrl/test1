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
    <div class="container" id="paso1">
        <h1>¿Me amas?</h1>
        <button onclick="mostrarRespuesta('si')">Sí</button>
        <button onclick="mostrarRespuesta('no')">No</button>
        <div id="respuesta" class="respuesta"></div>
    </div>

    <div class="container" id="paso2" style="display: none;">
        <h1>¿Cuánto?</h1>
        <button onclick="cuantoRespuesta('poco')">Un poco</button>
        <button onclick="cuantoRespuesta('mucho')">Mucho</button>
    </div>

    <div class="container" id="paso3" style="display: none;">
        <h1>¿Por qué hiciste todo si me amabas mucho?</h1>
        <div class="respuesta">Porque el amor verdadero a veces también duele 💔</div>
    </div>

    <script>
        function mostrarRespuesta(opcion) {
            const paso1 = document.getElementById('paso1');
            const paso2 = document.getElementById('paso2');
            const respuesta = document.getElementById('respuesta');

            if (opcion === 'si') {
                respuesta.textContent = "Yo también ❤️";
                setTimeout(() => {
                    paso1.style.display = 'none';
                    paso2.style.display = 'block';
                }, 1500);
            } else {
                respuesta.textContent = "Mientes 😢";
            }
        }

        function cuantoRespuesta(nivel) {
            const paso2 = document.getElementById('paso2');
            const paso3 = document.getElementById('paso3');

            if (nivel === 'poco') {
                // Mostrar página en blanco con emoji enojado
                document.body.innerHTML = '<div style="font-size: 5em; text-align: center; margin-top: 20%;">😠</div>';
                document.body.style.backgroundColor = 'white';
            } else if (nivel === 'mucho') {
                // Mostrar cara enamorada y siguiente pregunta
                document.body.style.backgroundColor = 'white';
                paso2.style.display = 'none';
                paso3.style.display = 'block';
            }
        }
    </script>
</body>
</html>
