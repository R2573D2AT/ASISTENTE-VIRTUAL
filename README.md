# ASISTENTE-VIRTUAL
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iniciar tu solicitud</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #1d0552;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            padding: 10px;
            box-sizing: border-box;
        }
        #container {
            background-color: rgba(29, 5, 82, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.7);
            text-align: center;
            width: 100%;
            max-width: 600px;
            transition: all 0.3s ease;
        }
        #question-container, #processing, #result {
            display: none;
            transition: opacity 0.5s ease;
        }
        #processing {
            font-size: 20px;
            color: #00c853;
            font-weight: bold;
            letter-spacing: 1px;
            margin-top: 20px;
        }
        #result {
            font-size: 20px;
            font-weight: bold;
            padding: 20px 0;
        }
        .button {
            background-color: #4caf50;
            border: none;
            color: #ffffff;
            padding: 15px 40px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 20px;
            margin-top: 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-weight: bold;
            letter-spacing: 1px;
            display: block;
            margin: 20px auto 0;
            width: 200px;
        }
        .button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }
        input[type="text"], input[type="number"] {
            width: calc(100% - 24px);
            padding: 12px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #ffffff;
            color: #1d0552;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: box-shadow 0.3s, transform 0.3s;
        }
        input[type="text"]:focus, input[type="number"]:focus {
            outline: none;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transform: scale(1.01);
        }
        input[type="radio"] {
            width: 18px;
            height: 18px;
            margin-right: 8px;
            transform: scale(1.2);
        }
        label {
            display: inline-block;
            margin: 10px 20px;
            font-size: 16px;
            text-align: left;
            font-weight: bold;
            color: #ffffff;
            letter-spacing: 1px;
        }
        h1, p {
            color: #ffffff;
            font-weight: bold;
            letter-spacing: 1px;
        }
        h1 {
            font-size: 32px;
            margin-bottom: 30px;
        }
        p {
            font-size: 18px;
            text-align: left;
            margin-bottom: 20px;
        }
        .options-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
        }
        .option {
            width: calc(50% - 10px);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        .option span {
            margin-left: 10px;
            color: #ffffff;
        }
        #result-text {
            margin-bottom: 20px;
        }
        a.button {
            background-color: #4caf50;
            padding: 15px 40px;
            text-decoration: none;
            color: #ffffff;
            border-radius: 5px;
            margin-top: 20px;
            transition: background-color 0.3s, transform 0.3s;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-weight: bold;
            letter-spacing: 1px;
            font-size: 20px;
            display: block;
            margin: 20px auto 0;
            width: 200px;
        }
        a.button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div id="container" aria-live="polite">
        <h1>Iniciar tu solicitud</h1>
        <div id="question-container">
            <p id="question"></p>
            <div id="answer-container" class="options-container"></div>
            <button class="button" onclick="nextQuestion()">Siguiente</button>
        </div>
        <div id="processing">Procesando tu solicitud...</div>
        <div id="result">
            <p id="result-text">Hemos encontrado la oferta adecuada para ti. Si estás interesado, haz clic en el botón de abajo.</p>
            <a href="http://doafftracking.tech/zaimoo.es/u2wsh/1" class="button" target="_blank">Solicitar</a>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "Hola, soy el Asistente virtual y te ayudaré a encontrar la financiación que necesitas. ¿Estás de acuerdo?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "Cantidad que necesitas (mínimo 50 euros)",
                type: "number",
                required: true,
                min: 50
            },
            {
                question: "Plazo (en meses, mínimo 1 mes)",
                type: "number",
                required: true,
                min: 1
            },
            {
                question: "Actividad laboral (necesario)*",
                type: "radio",
                options: ["Trabajo asalariado", "Autónomo", "Pensionista", "Desempleado"],
                required: true
            },
            {
                question: "Ingresos mensuales aproximados",
                type: "number",
                required: true,
                min: 0
            },
            {
                question: "ASNEF (necesario)*",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Actualmente tienes préstamos o deudas pendientes? (necesario)*",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Tienes un código de oferta?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "Si tienes un código de oferta, colócalo aquí. (opcional)",
                type: "text",
                required: false
            }
        ];

        const userResponses = {};

        let currentQuestion = 0;

        function showQuestion() {
            if (currentQuestion < questions.length) {
                const questionData = questions[currentQuestion];
                document.getElementById('question').innerText = questionData.question;
                const answerContainer = document.getElementById('answer-container');
                answerContainer.innerHTML = '';

                if (questionData.type === 'text' || questionData.type === 'number') {
                    const input = document.createElement('input');
                    input.type = questionData.type;
                    input.id = 'answer';
                    input.required = questionData.required;
                    if (questionData.min !== undefined) {
                        input.min = questionData.min;
                    }
                    input.classList.add('input-field');
                    answerContainer.appendChild(input);
                } else if (questionData.type === 'radio') {
                    const optionsContainer = document.createElement('div');
                    optionsContainer.classList.add('options-container');

                    questionData.options.forEach(option => {
                        const label = document.createElement('label');
                        label.classList.add('option');

                        const input = document.createElement('input');
                        input.type = 'radio';
                        input.name = 'answer';
                        input.value = option;
                        input.required = questionData.required;

                        const span = document.createElement('span');
                        span.textContent = option;

                        label.appendChild(input);
                        label.appendChild(span);
                        optionsContainer.appendChild(label);
                    });

                    answerContainer.appendChild(optionsContainer);
                }
            } else {
                processResults();
            }
        }

        function nextQuestion() {
            const answerElement = document.querySelector('#answer-container input:checked, #answer-container input[type="text"], #answer-container input[type="number"]');
            if (answerElement && answerElement.value.trim() !== '') {
                userResponses[currentQuestion] = answerElement.value;
                currentQuestion++;
                showQuestion();
            } else if (questions[currentQuestion].required) {
                alert('Por favor, responde a la pregunta.');
            } else {
                currentQuestion++;
                showQuestion();
            }
        }

        function processResults() {
            document.getElementById('question-container').style.display = 'none';
            document.getElementById('processing').style.display = 'block';

            setTimeout(() => {
                document.getElementById('processing').style.display = 'none';
                document.getElementById('result').style.display = 'block';
            }, 2000);
        }

        document.addEventListener('DOMContentLoaded', () => {
            document.getElementById('question-container').style.display = 'block';
            showQuestion();
        });
    </script>
</body>
</html>
