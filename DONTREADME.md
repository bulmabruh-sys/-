<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Анимированная машинка</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background-color: #87CEEB;
            min-height: 100vh;
            overflow: hidden;
            position: relative;
        }
        
        /* Контейнер для всей сцены */
        .scene {
            width: 100vw;
            height: 100vh;
            position: relative;
            overflow: hidden;
        }
        
        /* Дорога */
        .road {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 120px;
            background-color: #333;
        }
        
        /* Разметка на дороге */
        .road::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            width: 100%;
            height: 6px;
            background: repeating-linear-gradient(
                90deg,
                transparent,
                transparent 40px,
                yellow 40px,
                yellow 80px
            );
            transform: translateY(-50%);
        }
        
        /* Солнце */
        .sun {
            position: absolute;
            top: 40px;
            right: 80px;
            width: 70px;
            height: 70px;
            background-color: #FFD700;
            border-radius: 50%;
            box-shadow: 0 0 30px #FFA500;
        }
        
        /* Облака */
        .cloud {
            position: absolute;
            background-color: white;
            border-radius: 50px;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.8);
        }
        
        .cloud-1 {
            width: 120px;
            height: 50px;
            top: 80px;
            left: 10%;
        }
        
        .cloud-2 {
            width: 150px;
            height: 60px;
            top: 120px;
            left: 60%;
        }
        
        .cloud::before,
        .cloud::after {
            content: '';
            position: absolute;
            background-color: white;
            border-radius: 50%;
        }
        
        .cloud-1::before {
            width: 60px;
            height: 60px;
            top: -20px;
            left: 15px;
        }
        
        .cloud-1::after {
            width: 70px;
            height: 70px;
            top: -25px;
            right: 15px;
        }
        
        .cloud-2::before {
            width: 70px;
            height: 70px;
            top: -25px;
            left: 20px;
        }
        
        .cloud-2::after {
            width: 80px;
            height: 80px;
            top: -30px;
            right: 20px;
        }
        
        /* Деревья */
        .tree {
            position: absolute;
            bottom: 120px;
        }
        
        .tree-trunk {
            width: 20px;
            height: 60px;
            background-color: #8B4513;
            margin: 0 auto;
        }
        
        .tree-crown {
            width: 80px;
            height: 80px;
            background-color: #228B22;
            border-radius: 50%;
            margin-top: -40px;
        }
        
        .tree-1 {
            left: 15%;
        }
        
        .tree-2 {
            left: 85%;
        }
        
        /* Контейнер для машинки */
        .car-container {
            position: absolute;
            bottom: 60px;
            width: 200px;
            animation: drive 5s ease-out forwards;
        }
        
        /* Анимация движения машинки */
        @keyframes drive {
            0% {
                left: -200px;
            }
            100% {
                left: calc(100% - 250px); /* Останавливается за 50px до правого края */
            }
        }
        
        /* Машинка */
        .car {
            position: relative;
            width: 100%;
            height: 80px;
        }
        
        /* Кузов машинки */
        .car-body {
            position: absolute;
            width: 100%;
            height: 50px;
            background-color: #FF4500;
            border-radius: 20px 20px 0 0;
            bottom: 0;
        }
        
        /* Верхняя часть машинки */
        .car-top {
            position: absolute;
            width: 60%;
            height: 40px;
            background-color: #FF4500;
            border-radius: 15px 15px 0 0;
            bottom: 50px;
            left: 20%;
        }
        
        /* Окна машинки */
        .car-window {
            position: absolute;
            width: 45%;
            height: 25px;
            background-color: #87CEEB;
            border-radius: 10px 10px 0 0;
        }
        
        .car-window-front {
            bottom: 40px;
            left: 22%;
        }
        
        .car-window-rear {
            bottom: 40px;
            right: 22%;
        }
        
        /* Фары */
        .car-light {
            position: absolute;
            width: 15px;
            height: 10px;
            background-color: yellow;
            border-radius: 5px;
        }
        
        .car-light-front {
            bottom: 30px;
            right: 10px;
        }
        
        .car-light-rear {
            bottom: 30px;
            left: 10px;
            background-color: red;
        }
        
        /* Колеса */
        .car-wheel {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #333;
            border-radius: 50%;
            bottom: -10px;
            border: 5px solid #222;
        }
        
        .car-wheel-front {
            right: 25px;
        }
        
        .car-wheel-rear {
            left: 25px;
        }
        
        /* Диски на колесах */
        .car-wheel::after {
            content: '';
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: silver;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        
        /* Трава */
        .grass {
            position: absolute;
            bottom: 120px;
            width: 100%;
            height: 30px;
            background-color: #32CD32;
        }
        
        /* Инструкция */
        .instruction {
            position: absolute;
            top: 20px;
            left: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            padding: 10px 15px;
            border-radius: 10px;
            font-family: Arial, sans-serif;
            font-size: 14px;
            max-width: 250px;
        }
    </style>
</head>
<body>
    <div class="scene">
        <!-- Солнце -->
        <div class="sun"></div>
        
        <!-- Облака -->
        <div class="cloud cloud-1"></div>
        <div class="cloud cloud-2"></div>
        
        <!-- Деревья -->
        <div class="tree tree-1">
            <div class="tree-trunk"></div>
            <div class="tree-crown"></div>
        </div>
        
        <div class="tree tree-2">
            <div class="tree-trunk"></div>
            <div class="tree-crown"></div>
        </div>
        
        <!-- Трава -->
        <div class="grass"></div>
        
        <!-- Дорога -->
        <div class="road"></div>
        
        <!-- Машинка -->
        <div class="car-container">
            <div class="car">
                <!-- Кузов -->
                <div class="car-body"></div>
                
                <!-- Верхняя часть -->
                <div class="car-top"></div>
                
                <!-- Окна -->
                <div class="car-window car-window-front"></div>
                <div class="car-window car-window-rear"></div>
                
                <!-- Фары -->
                <div class="car-light car-light-front"></div>
                <div class="car-light car-light-rear"></div>
                
                <!-- Колеса -->
                <div class="car-wheel car-wheel-front"></div>
                <div class="car-wheel car-wheel-rear"></div>
            </div>
        </div>
        
        <!-- Инструкция -->
        <div class="instruction">
            <strong>Анимированная машинка</strong><br>
            Машинка выезжает слева и останавливается за 50px до правого края экрана.
        </div>
    </div>

    <script>
        // Добавим небольшой интерактив: при клике машинка поедет снова
        document.addEventListener('DOMContentLoaded', function() {
            const carContainer = document.querySelector('.car-container');
            
            // Перезапуск анимации по клику
            document.querySelector('.scene').addEventListener('click', function() {
                carContainer.style.animation = 'none';
                // Принудительный перезапуск анимации
                setTimeout(() => {
                    carContainer.style.animation = 'drive 5s ease-out forwards';
                }, 10);
            });
        });
    </script>
</body>
</html>
