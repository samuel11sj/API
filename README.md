<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>Conselho Aleatório</title>
  <link rel="stylesheet" href="style.css">
  <style>
  </style>
</head>
<body>

  <h1>Conselho Aleatório</h1>
  <div id="advice">Clique no botão para receber um conselho!</div>
  <button id="btnAdvice">Gerar Conselho</button>

  <script>
    const adviceDiv = document.getElementById('advice');
    const btn = document.getElementById('btnAdvice');

    async function fetchAdvice() {
      try {
        const response = await fetch('https://api.adviceslip.com/advice');
        const data = await response.json();
        adviceDiv.textContent = `"${data.slip.advice}"`;
      } catch (error) {
        adviceDiv.textContent = 'Ops! Não consegui buscar um conselho. Tente novamente.';
        console.error(error);
      }
    }

    btn.addEventListener('click', fetchAdvice);
  </script>

</body>
</html>
