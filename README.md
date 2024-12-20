# cocinero-estrella.
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cocinero Estrella: La Ruta de la Higiene</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            text-align: center;
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 20px 0;
        }
        .container {
            margin: 20px;
        }
        .button {
            display: inline-block;
            margin: 10px;
            padding: 15px 30px;
            background-color: #4CAF50;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-size: 16px;
        }
        .button:hover {
            background-color: #45a049;
        }
        .hidden {
            display: none;
        }
        .quiz {
            margin: 20px 0;
        }
        .quiz button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .quiz button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <header>
        <h1>Cocinero Estrella: La Ruta de la Higiene</h1>
    </header>

    <div class="container">
        <h2>Bienvenido al desafío</h2>
        <p>Completa los minijuegos y gana tus estrellas de higiene.</p>

        <a href="#" class="button" onclick="startGame('level1')">Comenzar Nivel 1: Higiene Personal</a>
        <a href="#" class="button hidden" id="level2Btn" onclick="startGame('level2')">Comenzar Nivel 2: Salud y Seguridad</a>
        <a href="#" class="button hidden" id="level3Btn" onclick="startGame('level3')">Comenzar Nivel 3: Presentación</a>

        <div id="gameArea"></div>
    </div>

    <script>
        function startGame(level) {
            const gameArea = document.getElementById('gameArea');
            gameArea.innerHTML = ''; // Clear previous content

            if (level === 'level1') {
                gameArea.innerHTML = `
                    <div class="quiz">
                        <h3>¿Cuál es el primer paso al lavarse las manos?</h3>
                        <button onclick="checkAnswer(true, 'level2Btn')">Mojar las manos</button>
                        <button onclick="checkAnswer(false, 'level2Btn')">Aplicar jabón directamente</button>
                    </div>
                `;
            } else if (level === 'level2') {
                gameArea.innerHTML = `
                    <div class="quiz">
                        <h3>¿Qué debes hacer si tienes fiebre mientras trabajas manipulando alimentos?</h3>
                        <button onclick="checkAnswer(true, 'level3Btn')">Informar al supervisor y no trabajar</button>
                        <button onclick="checkAnswer(false, 'level3Btn')">Usar guantes y continuar</button>
                    </div>
                `;
            } else if (level === 'level3') {
                gameArea.innerHTML = `
                    <div class="quiz">
                        <h3>¿Qué parte del uniforme es obligatoria en una cocina?</h3>
                        <button onclick="checkAnswer(true)">Gorro para el cabello</button>
                        <button onclick="checkAnswer(false)">Zapatos casuales</button>
                    </div>
                `;
            }
        }

        function checkAnswer(isCorrect, nextLevelBtnId) {
            const gameArea = document.getElementById('gameArea');
            if (isCorrect) {
                gameArea.innerHTML = '<p><strong>¡Correcto!</strong> Has avanzado al siguiente desafío.</p>';
                if (nextLevelBtnId) {
                    document.getElementById(nextLevelBtnId).classList.remove('hidden');
                }
            } else {
                gameArea.innerHTML = '<p><strong>Respuesta incorrecta.</strong> Intenta de nuevo.</p>';
            }
        }
    </script>
</body>
</html>
