<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Modelo Gravedad y Órbitas</title>
  <style>
    body { font-family: sans-serif; background: #000; color: white; text-align: center; }
    canvas { border: 1px solid #333; background: #111; margin-top: 20px; }
    button { margin: 10px; padding: 10px; border: none; background: #007BFF; color: white; border-radius: 5px; cursor: pointer; }
  </style>
</head>
<body>
  <h1>Modelo: Gravedad en el Espacio Exterior</h1>
  <button onclick="toggleGravity()">Activar/Desactivar Gravedad</button>
  <canvas id="orbitCanvas" width="500" height="400"></canvas>

  <script>
    const canvas = document.getElementById('orbitCanvas');
    const ctx = canvas.getContext('2d');
    let gravityOn = true;
    let angle = 0;
    let radius = 100;

    function drawOrbitingBody() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = 'yellow';
      ctx.beginPath();
      ctx.arc(250, 200, 20, 0, Math.PI * 2); // estrella o planeta central
      ctx.fill();

      if (gravityOn) angle += 0.02;
      const x = 250 + radius * Math.cos(angle);
      const y = 200 + radius * Math.sin(angle);

      ctx.fillStyle = 'blue';
      ctx.beginPath();
      ctx.arc(x, y, 10, 0, Math.PI * 2);
      ctx.fill();
    }

    function toggleGravity() {
      gravityOn = !gravityOn;
    }

    function animate() {
      drawOrbitingBody();
      requestAnimationFrame(animate);
    }

    animate();
  </script>
</body>
</html>
