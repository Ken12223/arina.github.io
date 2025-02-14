<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Открытка на День святого Валентина</title>
    <style>
        /* Общие стили */
        body {
            margin: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            background: #ffebee; /* Фон для главной страницы */
        }

        .container {
            text-align: center;
            position: relative;
            z-index: 1;
            width: 100%;
            max-width: 800px; /* Ограничиваем ширину контейнера */
            padding: 20px;
        }

        h1 {
            color: #d32f2f;
            font-size: 3em;
            margin-bottom: 40px;
        }

        .buttons {
            display: flex;
            gap: 30px;
            justify-content: center;
            flex-wrap: wrap; /* Кнопки переносятся на маленьких экранах */
        }

        button {
            padding: 20px 50px; /* Увеличиваем размер кнопок */
            font-size: 1.5em;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: transform 0.3s;
        }

        #yesBtn {
            background: #4CAF50;
            color: white;
        }

        #noBtn {
            background: #f44336;
            color: white;
        }

        button:hover {
            transform: scale(1.1);
        }

        /* Стили для страницы с открыткой */
        .valentine-page {
            display: none;
            background: linear-gradient(45deg, #ff6b6b, #ff8e8e);
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            justify-content: center;
            align-items: center;
            flex-direction: column; /* Центрируем текст вертикально */
        }

        .heart {
            position: relative;
            width: 150px; /* Увеличиваем размер сердца */
            height: 150px;
            margin: 30px auto;
            cursor: pointer;
            transition: transform 0.3s ease;
            transform-style: preserve-3d;
            animation: heartbeat 1.5s ease-in-out infinite;
        }

        .heart::before,
        .heart::after {
            content: '';
            position: absolute;
            width: 78px; /* Увеличиваем размер частей сердца */
            height: 120px;
            border-radius: 50px 50px 0 0;
            background: linear-gradient(45deg, #ff0000, #ff6b6b);
            left: 75px;
            transform: rotate(-45deg);
            transform-origin: 0 100%;
            box-shadow: 0 0 30px rgba(255, 0, 0, 0.8);
        }

        .heart::after {
            left: 0;
            transform: rotate(45deg);
            transform-origin: 100% 100%;
        }

        .message {
            color: white;
            font-size: 2.5em; /* Увеличиваем размер текста */
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            margin: 20px;
            opacity: 0;
            animation: fadeIn 2s ease-in-out forwards;
        }

        .sub-message {
            color: white;
            font-size: 1.5em; /* Увеличиваем размер текста */
            margin-top: 20px;
            opacity: 0;
            animation: fadeIn 2s ease-in-out 1s forwards;
        }

        .floating-hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .floating-heart {
            position: absolute;
            font-size: 30px; /* Увеличиваем размер плавающих сердечек */
            color: rgba(255, 255, 255, 0.8);
            animation: float 6s linear infinite;
        }

        .floating-butterflies {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .floating-butterfly {
            position: absolute;
            font-size: 30px; /* Размер бабочек */
            color: rgba(255, 255, 255, 0.8);
            animation: floatButterfly 6s linear infinite;
        }

        @keyframes floatButterfly {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        /* Стили для страницы 404 */
        .error-page {
            display: none;
            background: #212121;
            color: white;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            justify-content: center;
            align-items: center;
        }

        .error-container {
            text-align: center;
        }

        .error-container h1 {
            font-size: 8em;
            margin: 0;
            animation: glitch 1s infinite;
        }

        .error-container p {
            font-size: 2em; /* Увеличиваем размер текста */
        }

        .back-btn {
            padding: 20px 50px; /* Увеличиваем размер кнопки */
            background: #2196F3;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            margin-top: 30px;
            font-size: 1.2em;
        }

        /* Анимации */
        @keyframes heartbeat {
            0% { transform: scale(1); }
            25% { transform: scale(1.1); }
            50% { transform: scale(1); }
            75% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes glitch {
            0% { text-shadow: 2px 2px red; }
            25% { text-shadow: -2px -2px blue; }
            50% { text-shadow: 2px -2px green; }
            75% { text-shadow: -2px 2px yellow; }
            100% { text-shadow: 2px 2px red; }
        }
    </style>
</head>
<body>
    <!-- Главная страница -->
    <div class="container main-page">
        <h1>Ты любишь меня?</h1>
        <div class="buttons">
            <button id="yesBtn">ДА</button>
            <button id="noBtn">НЕТ</button>
        </div>
    </div>

    <!-- Страница с открыткой -->
    <div class="valentine-page">
        <div class="floating-hearts"></div>
        <div class="floating-butterflies"></div>
        <div class="heart"></div>
        <div class="message">С Днём Святого Валентина!</div>
        <div class="sub-message">Ты - самое прекрасное, что есть в моей жизни ❤️</div>
  	<div class="sub-message">ЛЮБЛЮ АРИНУ ☺️❤️</div>
 	<div class="sub-message">ЛЮБЛЮ АРИНУ ☺️❤️</div>
	<div class="sub-message">ЛЮБЛЮ АРИНУ ☺️❤️</div>
    </div>

    <!-- Страница 404 -->
    <div class="error-page">
        <div class="error-container">
            <h1>404</h1>
            <p>Неверный ответ! Сердце не найдено ❤️</p>
            <button class="back-btn" onclick="goBack()">Вернуться назад</button>
        </div>
    </div>

    <script>
        // Обработка нажатия на кнопку "ДА"
        document.getElementById('yesBtn').addEventListener('click', () => {
            document.querySelector('.main-page').style.display = 'none';
            document.querySelector('.valentine-page').style.display = 'flex'; /* Используем flex для центрирования */
            startFloatingHearts();
            startFloatingButterflies();
        });

        // Обработка нажатия на кнопку "НЕТ"
        document.getElementById('noBtn').addEventListener('click', () => {
            document.querySelector('.main-page').style.display = 'none';
            document.querySelector('.error-page').style.display = 'flex'; /* Используем flex для центрирования */
        });

        // Функция для создания плавающих сердечек
        function createFloatingHearts() {
            const container = document.querySelector('.floating-hearts');
            const heart = document.createElement('div');
            heart.innerHTML = '❤';
            heart.className = 'floating-heart';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = 6 + Math.random() * 4 + 's';
            container.appendChild(heart);
            setTimeout(() => heart.remove(), 10000);
        }

        // Функция для создания плавающих бабочек
        function createFloatingButterflies() {
            const container = document.querySelector('.floating-butterflies');
            const butterfly = document.createElement('div');
            butterfly.innerHTML = '🦋';
            butterfly.className = 'floating-butterfly';
            butterfly.style.left = Math.random() * 100 + 'vw';
            butterfly.style.animationDuration = 6 + Math.random() * 4 + 's';
            container.appendChild(butterfly);
            setTimeout(() => butterfly.remove(), 10000);
        }

        // Запуск анимации плавающих сердечек
        function startFloatingHearts() {
            setInterval(createFloatingHearts, 300);
        }

        // Запуск анимации плавающих бабочек
        function startFloatingButterflies() {
            setInterval(createFloatingButterflies, 500);
        }

        // Функция для возврата на главную страницу
        function goBack() {
            document.querySelector('.error-page').style.display = 'none';
            document.querySelector('.main-page').style.display = 'block';
        }
    </script>
</body>
</html>
# arina.github.io
