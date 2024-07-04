# ASISTENTE-VIRTUAL
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iniciar tu solicitud</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');

        body {
            font-family: 'Open Sans', sans-serif;
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

        #question-container,
        #processing,
        #result {
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
            font-family: 'Open Sans', sans-serif;
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

        input[type="text"],
        input[type="number"] {
            width: calc(100% - 24px);
            padding: 12px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            box-sizing: border-box;
            font-family: 'Open Sans', sans-serif;
            background-color: #ffffff;
            color: #1d0552;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            transition: box-shadow 0.3s, transform 0.3s;
        }

        input[type="text"]:focus,
        input[type="number"]:focus {
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

        h1,
        p {
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
            justify-content: space-around;
            align-items: center;
        }

        .option {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
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
            font-family: 'Open Sans', sans-serif;
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

        .intro {
            font-family: 'Open Sans', sans-serif;
            font-size: 18px;
        }

        /* Media queries para dispositivos móviles */
        @media (max-width: 600px) {
            .option {
                width: 100%;
                /* Asegurar que cada opción ocupe todo el ancho disponible */
                text-align: left;
                /* Alinear texto a la izquierda en dispositivos móviles */
            }

            .button {
                width: 100%;
                /* Botón ocupa todo el ancho en dispositivos móviles */
            }
        }
    </style>
</head>

<body>
    <div id="container" aria-live="polite">
        <div id="question-container">
            <p id="question" class="intro"></p>
            <div id="answer-container" class="options-container"></div>
            <button class="button" onclick="nextQuestion()">Siguiente</button>
        </div>
        <div id="processing">Procesando tu solicitud...</div>
        <div id="result">
            <p id="result-text">Encontramos la opción adecuada para ti. Si estás interesado, haz clic en el botón Solicitar.</p>
            <a id="request-button" href="https://track.adtraction.com/t/t?a=1497931818&as=1889896122&t=2&tk=1" class="button" target="_blank">Solicitar</a>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "¿Estás de acuerdo en continuar con la solicitud?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "Edad",
                type: "number",
                required: true,
                min: 18,
                max: 99
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
                question: "Actividad laboral*",
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
                question: "ASNEF*",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Actualmente tienes préstamos o deudas pendientes?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Tienes nacionalidad española o residencia en España?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Posees propiedades o aval?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            }
        ];

        const userResponses = {};

        let currentQuestion = 0;

        function showQuestion() {
            if (currentQuestion < questions.length) {
                const questionData = questions[currentQuestion];

                const questionElement = document.getElementById('question');
                questionElement.textContent = questionData.question;

                const answerContainer = document.getElementById('answer-container');
                answerContainer.innerHTML = ''; // Limpiar contenedor de respuestas anteriores

                if (questionData.type === 'text' || questionData.type === 'number') {
                    const input = document.createElement('input');
                    input.type = questionData.type;
                    input.id = 'answer';
                    input.required = questionData.required;
                    if (questionData.min !== undefined) {
                        input.min = questionData.min;
                    }
                    if (questionData.max !== undefined) {
                        input.max = questionData.max;
                    }
                    answerContainer.appendChild(input);
                } else if (questionData.type === 'radio') {
                    questionData.options.forEach(option => {
                        const optionContainer = document.createElement('div');
                        optionContainer.className = 'option';

                        const input = document.createElement('input');
                        input.type = 'radio';
                        input.name = 'answer';
                        input.value = option;
                        input.required = questionData.required;

                        const label = document.createElement('label');
                        label.textContent = option;

                        optionContainer.appendChild(input);
                        optionContainer.appendChild(label);
                        answerContainer.appendChild(optionContainer);
                    });
                }

                document.getElementById('question-container').style.display = 'block';
            } else {
                processResponses();
            }
        }

        function nextQuestion() {
            const questionData = questions[currentQuestion];
            const answerElement = document.querySelector('[name="answer"]:checked') || document.getElementById('answer');

            if (answerElement && answerElement.checkValidity()) {
                userResponses[questionData.question] = answerElement.value;
                currentQuestion++;
                showQuestion();
            } else {
                answerElement.reportValidity();
            }
        }

        function processResponses() {
            document.getElementById('question-container').style.display = 'none';
            document.getElementById('processing').style.display = 'block';

            setTimeout(() => {
                let link = "https://track.adtraction.com/t/t?a=1497931818&as=1889896122&t=2&tk=1"; // Enlace por defecto

                const age = parseInt(userResponses["Edad"], 10);
                const amount = parseFloat(userResponses["Cantidad que necesitas (mínimo 50 euros)"]);
                const employmentStatus = userResponses["Actividad laboral*"];
                const asnef = userResponses["ASNEF*"];
                const debts = userResponses["¿Actualmente tienes préstamos o deudas pendientes?"];
                const nationality = userResponses["¿Tienes nacionalidad española o residencia en España?"];

                if (amount <= 1000 && employmentStatus === "Trabajo asalariado" && asnef === "No") {
                    link = "http://doafftracking.tech/credityes.es/u2wsh/1";
                } else if (amount > 1000 && employmentStatus === "Autónomo" && asnef === "No") {
                    link = "https://track.adtraction.com/t/t?a=1498404511&as=1889896122&t=2&tk=1";
                } else if (age >= 21 && age <= 65 && employmentStatus === "Pensionista") {
                    link = "https://track.adtraction.com/t/t?a=1319987434&as=1889896122&t=2&tk=1";
                } else if (employmentStatus === "Desempleado" || asnef === "Sí" || debts === "Sí" || nationality === "No") {
                    link = "https://track.adtraction.com/t/t?a=1280180470&as=1889896122&t=2&tk=1";
                } else {
                    link = "https://track.adtraction.com/t/t?a=1871477231&as=1889896122&t=2&tk=1";
                }

                document.getElementById('request-button').href = link;
                document.getElementById('processing').style.display = 'none';
                document.getElementById('result').style.display = 'block';
            }, 2000);
        }

        document.addEventListener('DOMContentLoaded', () => {
            showQuestion();
        });
    </script>
</body>

</html>






