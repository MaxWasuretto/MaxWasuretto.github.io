<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ралли Карелия</title>
    <style>
        /* Подключение шрифтов */
        @font-face {
            font-family: 'Suzuki Alstare Extreme Racing';
            src: url('SuzukiAlstareExtremeRacing.woff2') format('woff2'),
                 url('SuzukiAlstareExtremeRacing.woff') format('woff'),
                 url('SuzukiAlstareExtremeRacing.ttf') format('truetype');
            font-weight: normal;
            font-style: normal;
        }

        @font-face {
            font-family: 'MTS Wide';
            src: url('MTSWide.woff2') format('woff2'),
                 url('MTSWide.woff') format('woff'),
                 url('MTSWide.ttf') format('truetype');
            font-weight: normal;
            font-style: normal;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-color: #2a2a2a;
            color: #ffffff;
            overflow-x: hidden;
        }

        .container {
            max-width: 1600px;
            height: 780px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Навигационная панель */
        .nav-bar {
            display: flex;
            justify-content: flex-start;
            margin-bottom: 60px;
            margin-top: 40px;
            width: 1560px;
        }

        .nav-button {
            background-color: #008ADF;
            color: #ffffff;
            border: none;
            width: 4500px;
            padding: 15px 40px;
            font-weight: regular;
            cursor: pointer;
            transition: background-color 0.3s ease;
            white-space: nowrap;
        }

        .nav-button:hover {
            background-color: #0070b8;
        }

        .nav-button.left {
            font-family: 'Suzuki Alstare Extreme Racing', 'Arial', sans-serif;
        }

        .nav-button.middle,
        .nav-button.right {
            font-family: 'MTS Wide', 'Arial', sans-serif;
        }

        .nav-button.left {
            border-top-left-radius: 60px;
            font-size: 36px;
        }

        .nav-button.middle {
            border-radius: 0;
            font-size: 24px;
        }

        .nav-button.right {
            border-bottom-right-radius: 60px;
            font-size: 24px;
        }

        /* Основной контент */
        .main-content {
            display: grid;
            grid-template-columns: 1fr 1.5fr;
            gap: 60px;
            align-items: start;
            min-height: calc(100vh - 200px);
        }

        /* Текстовые блоки */
        .text-content {
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        .text-block-large {
            font-size: 64px;
            font-weight: regular;
            text-transform: uppercase;
            color: #ffffff;
            line-height: 1.2;
            font-family: 'Suzuki Alstare Extreme Racing', 'Arial', sans-serif;
        }

        .text-block-small {
            font-size: 30px;
            color: #ffffff;
            line-height: 1.6;
            font-family: 'MTS Wide', 'Arial', sans-serif;
        }

        /* Видео блок */
        .video-container {
            position: relative;
            width: 100%;
            padding-bottom: 56.25%; /* 16:9 соотношение */
            background-color: #3a3a3a;
            border-top-left-radius: 30px;
            border-top-right-radius: 0px;
            border-bottom-right-radius: 30px;
            border-bottom-left-radius: 30px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        .video-container video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .video-controls {
            position: absolute;
            top: 15px;
            right: 15px;
            width: 30px;
            height: 30px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: background-color 0.3s ease;
            z-index: 10;
        }

        .video-controls:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }

        .video-controls svg {
            width: 18px;
            height: 18px;
            fill: #ffffff;
        }

        /* Блок новостей */
        .news-section {
            background-color: #E8E8E8;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 1920px;
            margin: 60px auto 0;
            padding: 40px;
        }

        .news-header {
            font-size: 48px;
            font-weight: bold;
            color: #000000;
            margin-bottom: 40px;
            align-self: flex-start;
            padding-left: 120px;
            font-family: 'MTS Wide', 'Arial', sans-serif;
        }

        /* Большой баннер "УЖЕ СКОРО" */
        .news-banner-wrapper {
            display: flex;
            flex-direction: column;
            justify-content: center;
            margin-bottom: 40px;
            width: 1320px;
            background-color: #d8d8d8;
            border: 6px solid #585858;
            border-bottom-right-radius: 30px;
            border-bottom-left-radius: 30px;
            transition: filter 0.3s ease;
            cursor: pointer;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        }

        .news-banner {
            width: 1400px;
            max-width: 100%;
            height: 383px;
            border-bottom: 6px solid #585858;
            overflow: hidden;
            position: relative;
        }

        .news-banner img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .news-banner-text {
            padding: 20px;
            color: #ffffff;
            font-size: 58px;
            font-weight: bold;
            text-align: center;
            font-family: 'MTS Wide', 'Arial', sans-serif;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        }

        /* Контейнер для маленьких блоков новостей */
        .news-items {
            display: grid;
            grid-template-columns: repeat(2, 635px);
            gap: 40px;
            justify-content: center;
        }

        /* Маленькие блоки новостей */
        .news-item {
            width: 635px;
            max-width: 100%;
            height: 543px;
            background-color: #ffffff;
            border-radius: 20px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            border: 6px solid #585858;
            transition: filter 0.3s ease;
            cursor: pointer;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        }

        .news-item:hover {
            filter: brightness(0.85);
        }

        .news-banner-wrapper:hover {
            filter: brightness(0.85);
        }


        .news-item-image {
            width: 100%;
            height: auto;
            flex: 1;
            object-fit: cover;
        }

        .news-item-text {
            padding: 20px;
            background-color: #d8d8d8;
            color: #000000;
            font-size: 24px;
            font-weight: bold;
            text-align: center;
            font-family: 'MTS Wide', 'Arial', sans-serif;
        }

        /* Адаптивность */
        @media (max-width: 1200px) {
            .news-section {
                width: 100%;
                padding: 40px 20px;
            }

            .news-banner {
                width: 100%;
                height: auto;
                aspect-ratio: 1200 / 383;
            }

            .news-items {
                grid-template-columns: 1fr;
                justify-content: center;
            }

            .news-item {
                width: 100%;
                max-width: 635px;
                height: auto;
                aspect-ratio: 635 / 543;
            }
        }

        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .text-block-large {
                font-size: 36px;
            }

            .text-block-small {
                font-size: 20px;
            }

            .news-items {
                grid-template-columns: 1fr;
            }

            .news-item {
                max-width: 100%;
            }
        }

        @media (max-width: 768px) {
            .nav-bar {
                flex-direction: column;
                gap: 0;
            }

            .nav-button {
                width: 100%;
                border-radius: 0 !important;
            }

            .nav-button.left {
                border-top-left-radius: 15px !important;
                border-top-right-radius: 15px !important;
            }

            .nav-button.right {
                border-bottom-left-radius: 15px !important;
                border-bottom-right-radius: 15px !important;
            }

            .text-block-large {
                font-size: 28px;
            }

            .text-block-small {
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Навигационная панель -->
        <nav class="nav-bar">
            <button class="nav-button left">РАЛЛИ КАРЕЛИЯ</button>
            <button class="nav-button middle">Новости</button>
            <button class="nav-button right">Турниры</button>
        </nav>

        <!-- Основной контент -->
        <main class="main-content">
            <!-- Текстовые блоки -->
            <div class="text-content">
                <div class="text-block-large">
                    <p>Будь</p> 
                    <p>первым</p>
                </div>
                <div class="text-block-small">
                    <p>Зритель или пилот -</p> 
                    <p>нет права упустить</p>
                    <p>свой шанс</p>
                    <p>Каждое мгновение</p>
                    <p>дарит тонны эмоций</p>
                </div>
            </div>

            <!-- Видео блок -->
            <div class="video-container">
                <video id="rallyVideo" controls autoplay muted playsinline loop>
                    <source src="video.mp4" type="video/mp4">
                    Ваш браузер не поддерживает воспроизведение видео.
                </video>
                <div class="video-controls" onclick="toggleMute()">
                    <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/>
                    </svg>
                </div>
            </div>
        </main>

    </div>

    <!-- Блок новостей -->
    <section class="news-section">
        <h2 class="news-header">НОВОСТИ</h2>
        
        <!-- Большой баннер "УЖЕ СКОРО" -->
        <div class="news-banner-wrapper">
            <div class="news-banner">
                <img src="1.png" alt="Ралли Карелия">
            </div>
            <div class="news-banner-text">УЖЕ СКОРО!</div>
        </div>

        <!-- Маленькие блоки новостей -->
        <div class="news-items">
            <div class="news-item">
                <img src="2.png" alt="Новость 1" class="news-item-image">
                <div class="news-item-text">Успешный дебют братьев Семёновых на недавнем РК2024!</div>
            </div>
            <div class="news-item">
                <img src="3.png" alt="Новость 2" class="news-item-image">
                <div class="news-item-text">Сход с дистанции - не приговор!<p>Сафронов и Крупин о своём опыте</p></div>
            </div>
        </div>
    </section>

    <script>
        function toggleMute() {
            const video = document.getElementById('rallyVideo');
            video.muted = !video.muted;
        }

        // Автозапуск видео при загрузке страницы
        window.addEventListener('DOMContentLoaded', function() {
            const video = document.getElementById('rallyVideo');
            
            // Попытка запуска сразу
            const playPromise = video.play();
            
            if (playPromise !== undefined) {
                playPromise.catch(error => {
                    // Если автозапуск не удался, попробуем после загрузки данных
                    video.addEventListener('loadeddata', function() {
                        video.play().catch(err => {
                            console.log('Автозапуск видео не удался:', err);
                        });
                    }, { once: true });
                });
            }
        });
    </script>
</body>
</html>
