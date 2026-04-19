<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para Mili 💖</title>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    overflow: hidden;
    background: #000;
    font-family: 'Arial', sans-serif;
    color: white;
    height: 100vh;
    width: 100vw;
  }

  canvas {
    position: fixed;
    top: 0;
    left: 0;
    display: block;
  }

  .carta {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    max-width: 90%;
    width: 600px;
    text-align: center;
    background: rgba(0, 0, 0, 0.75);
    padding: 30px;
    border-radius: 20px;
    box-shadow: 0 0 30px rgba(255, 77, 166, 0.3);
    animation: fadeIn 2s ease;
    border: 2px solid rgba(255, 77, 166, 0.2);
    backdrop-filter: blur(10px);
    z-index: 10;
  }

  h1 {
    color: #ff4da6;
    font-size: 2.5rem;
    margin-bottom: 20px;
    text-shadow: 0 0 10px rgba(255, 77, 166, 0.5);
  }

  p {
    margin: 15px 0;
    line-height: 1.6;
    font-size: 1.1rem;
    animation: slideIn 0.8s ease forwards;
    opacity: 0;
  }

  p:nth-child(1) { animation-delay: 0.5s; }
  p:nth-child(2) { animation-delay: 0.7s; }
  p:nth-child(3) { animation-delay: 0.9s; }
  p:nth-child(4) { animation-delay: 1.1s; }
  p:nth-child(5) { animation-delay: 1.3s; }
  p:nth-child(6) { animation-delay: 1.5s; }

  .firma {
    margin-top: 30px;
    font-style: italic;
    color: #ff4da6;
    animation-delay: 1.7s;
    text-shadow: 0 0 10px rgba(255, 77, 166, 0.5);
  }

  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translate(-50%, -60%);
    }
    to {
      opacity: 1;
      transform: translate(-50%, -50%);
    }
  }

  @keyframes slideIn {
    from {
      opacity: 0;
      transform: translateY(10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @media (max-width: 768px) {
    .carta {
      width: 95%;
      padding: 20px;
    }

    h1 {
      font-size: 1.8rem;
    }

    p {
      font-size: 1rem;
    }
  }

  @media (max-width: 480px) {
    .carta {
      padding: 15px;
    }

    h1 {
      font-size: 1.5rem;
    }

    p {
      font-size: 0.9rem;
      margin: 10px 0;
    }
  }
</style>
</head>
<body>

<canvas id="space"></canvas>

<div class="carta">
  <h1>Para vos, Mili 💖</h1>
  
  <p>
    No sé cómo explicarlo bien… pero desde que apareciste, algo en mí cambió.
  </p>
  
  <p>
    Empecé a pensar en vos sin darme cuenta, a sonreír solo recordándote…  
    y a sentir que, de alguna forma, todo es un poco mejor cuando estás.
  </p>
  
  <p>
    No es solo lo linda que sos… es tu forma de ser, tu energía,  
    eso que tenés que no se puede explicar pero se siente fuerte.
  </p>
  
  <p>
    Me hacés bien, de verdad.  
    Y en un mundo donde todo va tan rápido… encontrarte fue como frenar  
    y darme cuenta de lo que realmente importa.
  </p>
  
  <p>
    No sé qué va a pasar mañana… pero sí sé lo que siento hoy.  
    Y hoy, lo que siento… es que te amo.
  </p>
  
  <p>
    Te amo, Mili… y no es algo que diga por decir.  
    Es algo que me nace, que me sale solo…  
    y que cada día crece un poco más 💫
  </p>
  
  <p class="firma">
    Atentamente, tu amor Axel 💖
  </p>

</div>

<script>
  const canvas = document.getElementById("space");
  const ctx = canvas.getContext("2d", { alpha: true });

  let animationId;

  function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }

  resizeCanvas();

  let particles = [];

  function initParticles() {
    particles = [];
    for (let i = 0; i < 100; i++) {
      particles.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        radius: Math.random() * 1.5 + 0.5,
        speed: Math.random() * 0.3 + 0.1,
        opacity: Math.random() * 0.5 + 0.5
      });
    }
  }

  initParticles();

  function draw() {
    ctx.fillStyle = "rgba(0, 0, 0, 0.2)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    particles.forEach(p => {
      ctx.fillStyle = `rgba(255, 255, 255, ${p.opacity})`;
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
      ctx.fill();

      p.y += p.speed;

      if (p.y > canvas.height) {
        p.y = -p.radius;
        p.x = Math.random() * canvas.width;
        p.opacity = Math.random() * 0.5 + 0.5;
      }
    });

    animationId = requestAnimationFrame(draw);
  }

  draw();

  window.addEventListener("resize", () => {
    resizeCanvas();
    initParticles();
  });

  window.addEventListener("unload", () => {
    cancelAnimationFrame(animationId);
  });
</script>

</body>
</html>
