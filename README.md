<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Preguntas Dinámicas</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
      color: #333;
      text-align: center;
      padding: 40px;
    }

    h2 {
      margin-bottom: 30px;
    }

    .card {
      background-color: white;
      padding: 25px;
      margin: 20px auto;
      border-radius: 15px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      width: 80%;
      max-width: 500px;
      transition: transform 0.3s ease;
    }

    .card:hover {
      transform: scale(1.02);
    }

    button {
      background-color: #ff6b6b;
      border: none;
      color: white;
      padding: 12px 24px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
      margin-top: 10px;
    }

    button:hover {
      background-color: #ff3f3f;
    }

    .respuesta {
      margin-top: 15px;
      font-weight: bold;
      opacity: 0;
      transition: opacity 0.5s ease;
    }

    .visible {
      opacity: 1;
    }
  </style>
</head>
<body>

  <h2>Responde con estilo 😎</h2>

  <div class="card">
    <p><strong>¿Eres gay?</strong></p>
    <button onclick="responder('gay')">Responder</button>
    <p class="respuesta" id="respuestaGay"></p>
  </div>

  <div class="card">
    <p><strong>¿Te duele el chiquito?</strong></p>
    <button onclick="responder('chiquito')">Responder</button>
    <p class="respuesta" id="respuestaChiquito"></p>
  </div>

  <script>
    function responder(pregunta) {
      let respuestas = {
        gay: [
          "😌 Sí, soy.",
          "😔 Sí soy, pero me duele aceptarlo."
        ],
        chiquito: [
          "😣 Sí me duele.",
          "🔥 Me arde."
        ]
      };

      let elementoId = pregunta === 'gay' ? 'respuestaGay' : 'respuestaChiquito';
      let respuestaElemento = document.getElementById(elementoId);
      let opciones = respuestas[pregunta];
      let seleccion = opciones[Math.floor(Math.random() * opciones.length)];

      // Mostrar respuesta con efecto
      respuestaElemento.textContent = seleccion;
      respuestaElemento.classList.remove("visible");
      setTimeout(() => {
        respuestaElemento.classList.add("visible");
      }, 100);
    }
  </script>

</body>
</html>
