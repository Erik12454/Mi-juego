# Mi-juego
Es un juego super creativo, para jugar con tu pareja o con un amigo/a con la que tienes mucha confianza 
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Verdad o Reto: Parejas</title>
  <style>
    body {
      background: linear-gradient(to right, #ffc0cb, #ffe4e1);
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      padding: 50px;
      color: #b30059;
    }
    h1 {
      font-size: 2.5rem;
      margin-bottom: 30px;
    }
    button {
      background-color: #ff66a3;
      border: none;
      color: white;
      padding: 15px 30px;
      font-size: 1.2rem;
      margin: 10px;
      border-radius: 12px;
      cursor: pointer;
      transition: 0.3s ease;
    }
    button:hover {
      background-color: #e60073;
    }
    #output {
      margin-top: 40px;
      font-size: 1.5rem;
      background: white;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
    }
    #timer {
      margin-top: 20px;
      font-size: 1.5rem;
      background-color: red;
      color: white;
      width: 100px;
      height: 100px;
      line-height: 100px;
      border-radius: 50%;
      margin: 20px auto;
      font-weight: bold;
      box-shadow: 0 0 10px rgba(0,0,0,0.3);
    }
  </style>
</head>
<body>
  <h1>💘 Verdad o Reto: Parejas 💘</h1>
  <button onclick="showTruth()">Verdad 🔍</button>
  <button onclick="showDare()">Reto 🔥</button>
  <button onclick="showRandom()">Aleatorio 🎲</button>
  <div id="output">Pulsa un botón para empezar...</div>
  <div id="timer">⏱️</div>
  <audio id="beep-sound" src="https://www.soundjay.com/button/beep-07.wav" preload="auto"></audio>
  <audio id="background-music" src="https://www.bensound.com/bensound-music/bensound-love.mp3" autoplay loop></audio>

  <script>
    const truths = [
      "¿Has fantaseado con alguien más?",
      "¿Qué parte de mi cuerpo te gusta más?",
      "¿Qué fue lo primero que pensaste de mí al conocerme?",
      "¿Cuál es tu mayor secreto conmigo?",
      "¿Te has sentido celoso alguna vez? ¿Cuándo?",
      "¿Hay algo que te gustaría cambiar de nuestra relación?",
      "¿Alguna vez has mentido para evitar una pelea conmigo?",
      "¿Qué es lo más atrevido que has pensado hacer conmigo?",
      "¿Tendrías una cita secreta conmigo si estuviéramos en un lugar prohibido?",
      "¿Te atreverías a hacer un trío? ¿Con quién?",
      "¿Has soñado conmigo de forma picante? ¿Qué pasó?",
      "¿Qué parte de tu cuerpo te gustaría que yo explorara más?",
      "¿Qué te gustaría probar en la cama pero no has dicho todavía?"
    ];

    const dares = [
      "Dame un beso de al menos 10 segundos.",
      "Hazme un masaje en la espalda durante 1 minuto.",
      "Susúrrame algo muy atrevido al oído.",
      "Haz un baile sensual para mí.",
      "Bésame en el cuello como si fuera nuestra primera cita.",
      "Haz una imitación sexy de mí.",
      "Hazme una pregunta súper picante.",
      "Di lo que más te enciende de mí.",
      "Mírame fijo y no digas nada durante 20 segundos.",
      "Hazme reír mientras me acaricias.",
      "Simula un striptease divertido (puede ser con ropa).",
      "Envíame un mensaje picante como si estuvieras lejos de mí."
    ];

    function showTruth() {
      const random = truths[Math.floor(Math.random() * truths.length)];
      document.getElementById("output").innerText = "💬 VERDAD: " + random;
      startTimer();
    }

    function showDare() {
      const random = dares[Math.floor(Math.random() * dares.length)];
      document.getElementById("output").innerText = "🔥 RETO: " + random;
      startTimer();
    }

    function showRandom() {
      const isTruth = Math.random() < 0.5;
      if (isTruth) {
        showTruth();
      } else {
        showDare();
      }
    }

    function startTimer() {
      let time = 30; // segundos
      const timerElement = document.getElementById("timer");
      const sound = document.getElementById("beep-sound");
      timerElement.innerText = time + "s";
      sound.play();
      const interval = setInterval(() => {
        time--;
        timerElement.innerText = time + "s";
        if (time <= 0) {
          clearInterval(interval);
          timerElement.innerText = "⏱️";
        }
      }, 1000);
    }
  </script>
</body>
</html>
