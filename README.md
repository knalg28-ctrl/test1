<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Preguntas Dinámicas</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(-45deg, #ff9a9e, #fad0c4, #fad0c4, #fbc2eb);
      background-size: 400% 400%;
      animation: gradientBG 10s ease infinite;
      color: #333;
      text-align: center;
      padding: 40px;
    }

    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    h2 {
      font-size: 2em;
      margin-bottom: 30px;
      color: #fff;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
    }

    .card {
      background-color: white;
      padding: 25px;
      margin: 20px auto;
      border-radius: 20px;
      box-shadow: 0 12px 24px rgba(0,0,0,0.2);
      width: 80%;
      max-width: 500px;
      transition: transform 0.3s ease, background-color 0.6s ease;
      position: relative;
    }

    .card:hover {
      transform: scale(1.03);
    }

    button {
      background-color: #ff6b6b;
      border: none;
      color: white;
      padding: 14px 28px;
      font-size: 16px;
      font-weight: bold;
      border-radius: 10px;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.2s;
      margin-top: 10px;
    }

    button:hover {
      background-color: #ff3f3f;
      transform: scale(1.05);
    }

    .respuesta {
      margin-top: 20px;
      font-weight: bold;
      font-size: 18px;
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.5s ease;
    }

    .respuesta.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .emoji-burst {
      position: absolute;
      top: -10px;
      right: 10px;
      font-size: 24px;
      animation: float 1s ease-out forwards;
    }

    @keyframes float {
      from { opacity: 1; transform: translateY(0); }
      to { opacity: 0; transform: translateY(-40px) scale(1.5); }
    }
  </style>
</head>
<body>

  <h2>Responde con estilo 😎</h2>

  <div class="card" id="cardGay">
    <p><strong>🌈 ¿Eres gay?</strong></p>
    <button onclick="responder('gay', 'cardGay', 'respuestaGay')">Responder</button>
    <p class="respuesta" id="respuestaGay"></p>
  </div>

  <div class="card" id="cardChiquito">
    <p><strong>🍑 ¿Te duele el chiquito?</strong></p>
    <button onclick="responder('chiquito', 'cardChiquito', 'respuestaChiquito')">Responder</button>
    <p class="respuesta" id="respuestaChiquito"></p>
  </div>

  <script>
    function responder(pregunta, cardId, respuestaId) {
      let respuestas = {
        gay: [
          "🌈 ¡Sí soy! ¡Y orgullosamente! 💅",
          "😌 Obvio que sí, reina.",
          "👀 Eso no se pregunta... se nota.",
          "🎉 ¡Sí y felizmente libre!"
        ],
        chiquito: [
          "😣 Me duele... pero con gusto.",
          "🔥 ¡Está on fire!",
          "🥵 Sí, pero ya me acostumbré.",
          "💥 Dolor rico 😏"
        ]
      };

      let colores = ['#ffe0e0', '#e0fff4', '#fff3e0', '#f0e0ff', '#e0f7ff'];

      // Elegir respuesta aleatoria
      let opciones = respuestas[pregunta];
      let seleccion = opciones[Math.floor(Math.random() * opciones.length)];

      // Elementos
      let respuestaElemento = document.getElementById(respuestaId);
      let tarjeta = document.getElementById(cardId);

      // Cambiar fondo de la tarjeta
      tarjeta.style.backgroundColor = colores[Math.floor(Math.random() * colores.length)];

      // Mostrar respuesta con animación
      respuestaElemento.classList.remove("visible");
      setTimeout(() => {
        respuestaElemento.textContent = seleccion;
        respuestaElemento.classList.add("visible");
      }, 100);

      // Efecto de emojis flotantes
      const burst = document.createElement("div");
      burst.className = "emoji-burst";
      burst.textContent = pregunta === "gay" ? "🌈" : "🔥";
      tarjeta.appendChild(burst);
      setTimeout(() => burst.remove(), 1000);
    }
  </script>

</body>
</html>
