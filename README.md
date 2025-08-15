<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz de Nível de TDAH</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            text-align: center;
            margin: 0;
            padding: 20px;
        }

        h1 {
            color: #333;
        }

        .quiz-container {
            background-color: #fff;
            max-width: 700px;
            margin: 20px auto;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .question {
            font-size: 20px;
            margin-bottom: 15px;
        }

        .options button {
            display: block;
            width: 80%;
            margin: 8px auto;
            padding: 12px;
            font-size: 16px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            transition: background-color 0.3s;
        }

        .options button:hover {
            background-color: #45a049;
        }

        #result {
            margin-top: 20px;
            font-size: 22px;
            font-weight: bold;
            color: #333;
        }

        #mascote {
            width: 120px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>Descubra seu nível de TDAH</h1>
        <img id="mascote" src="mascote.png" alt="Mascote do ebook">

        <div id="quiz"></div>
        <div id="result"></div>
    </div>

    <script>
        const quizData = [
            {
                question: "Você tem dificuldade em manter atenção em tarefas longas?",
                options: ["Nunca", "Às vezes", "Frequentemente", "Quase sempre"],
                scores: [0, 1, 2, 3]
            },
            {
                question: "Você se distrai facilmente com estímulos externos?",
                options: ["Nunca", "Às vezes", "Frequentemente", "Quase sempre"],
                scores: [0, 1, 2, 3]
            },
            {
                question: "Você costuma adiar tarefas importantes?",
                options: ["Nunca", "Às vezes", "Frequentemente", "Quase sempre"],
                scores: [0, 1, 2, 3]
            },
            {
                question: "Você se sente inquieto ou tem dificuldade em ficar parado?",
                options: ["Nunca", "Às vezes", "Frequentemente", "Quase sempre"],
                scores: [0, 1, 2, 3]
            },
            {
                question: "Você interrompe os outros com frequência ou age impulsivamente?",
                options: ["Nunca", "Às vezes", "Frequentemente", "Quase sempre"],
                scores: [0, 1, 2, 3]
            }
        ];

        let currentQuestion = 0;
        let score = 0;

        const quizContainer = document.getElementById("quiz");
        const resultContainer = document.getElementById("result");

        function showQuestion() {
            const q = quizData[currentQuestion];
            quizContainer.innerHTML = `
                <div class="question">${q.question}</div>
                <div class="options">
                    ${q.options.map((option, index) => 
                        `<button onclick="selectOption(${index})">${option}</button>`
                    ).join('')}
                </div>
            `;
        }

        function selectOption(index) {
            score += quizData[currentQuestion].scores[index];
            currentQuestion++;
            if (currentQuestion < quizData.length) {
                showQuestion();
            } else {
                showResult();
            }
        }

        function showResult() {
            let level = "";
            if (score <= 3) {
                level = "Baixo nível de TDAH";
            } else if (score <= 6) {
                level = "Nível moderado de TDAH";
            } else {
                level = "Nível alto de TDAH";
            }
            quizContainer.innerHTML = "";
            resultContainer.innerHTML = `Seu resultado: ${level}`;
        }

        // Inicia o quiz
        showQuestion();
    </script>
</body>
</html>
