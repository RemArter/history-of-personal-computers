<!DOCTYPE html>
<html lang="ru" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>История развития ПК: от IBM до современных</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Roboto+Slab:wght@400;500;600&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/feather-icons/dist/feather.min.js"></script>
    <script src="https://unpkg.com/feather-icons"></script>
    <style>
        .bg-circuit-pattern {
            background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%23ffffff' fill-opacity='0.1' fill-rule='evenodd'/%3E%3C/svg%3E");
        }
        
        .test-container {
            transition: all 0.3s ease;
        }
        
        .question-card {
            transform: translateX(0);
            opacity: 1;
            transition: all 0.5s ease;
        }
        
        .question-card.hidden {
            transform: translateX(100px);
            opacity: 0;
            position: absolute;
            pointer-events: none;
        }
        
        .option-card {
            transition: all 0.2s ease;
            cursor: pointer;
        }
        
        .option-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
        }
        
        .option-card.selected {
            border-color: #ff6b35;
            background-color: #fff5f0;
        }
        
        .option-card.correct {
            border-color: #00b894;
            background-color: #e8f8f4;
        }
        
        .option-card.incorrect {
            border-color: #e84393;
            background-color: #fce4ec;
        }
        
        .progress-bar {
            transition: width 0.5s ease;
        }
        
        .result-badge {
            animation: pulse 2s infinite;
        }
        
        .certificate {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            border: 15px solid #ffd700;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        
        .explanation-box {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s ease;
        }
        
        .explanation-box.show {
            max-height: 200px;
        }
        
        /* Стили для модального окна с увеличением изображения */
        .image-modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.9);
            animation: fadeIn 0.3s;
        }
        
        .modal-content {
            margin: auto;
            display: block;
            max-width: 90%;
            max-height: 90%;
            margin-top: 2%;
            animation: zoomIn 0.3s;
            border-radius: 10px;
            box-shadow: 0 0 30px rgba(255,255,255,0.1);
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            right: 35px;
            color: #f1f1f1;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            z-index: 1001;
        }
        
        .close-modal:hover {
            color: #bbb;
            transform: scale(1.1);
        }
        
        .zoomable-image {
            cursor: zoom-in;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .zoomable-image:hover {
            transform: scale(1.02);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }
        
        .zoom-overlay {
            position: absolute;
            bottom: 10px;
            left: 10px;
            background: rgba(0,0,0,0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            opacity: 0;
            transition: opacity 0.3s ease;
            pointer-events: none;
        }
        
        .zoomable-image:hover .zoom-overlay {
            opacity: 1;
        }
        
        /* Единый масштаб для всех изображений */
        .standard-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            object-position: center;
        }
        
        .timeline-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
            object-position: center;
        }
        
        @keyframes fadeIn {
            from {opacity: 0;}
            to {opacity: 1;}
        }
        
        @keyframes zoomIn {
            from {transform: scale(0.8); opacity: 0;}
            to {transform: scale(1); opacity: 1;}
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        /* Яркие цветовые классы */
        .bg-primary-500 { background-color: #ff6b35; }
        .bg-primary-600 { background-color: #e55a2b; }
        .bg-accent-500 { background-color: #00cec9; }
        .bg-accent-600 { background-color: #00a8a3; }
        .bg-success-500 { background-color: #00b894; }
        .bg-warning-500 { background-color: #fdcb6e; }
        .bg-info-500 { background-color: #0984e3; }
        .bg-purple-500 { background-color: #a29bfe; }
        .bg-pink-500 { background-color: #fd79a8; }
        
        .text-primary-500 { color: #ff6b35; }
        .text-primary-600 { color: #e55a2b; }
        .text-accent-500 { color: #00cec9; }
        .text-accent-600 { color: #00a8a3; }
        .text-success-500 { color: #00b894; }
        .text-warning-500 { color: #fdcb6e; }
        .text-info-500 { color: #0984e3; }
        .text-purple-500 { color: #a29bfe; }
        .text-pink-500 { color: #fd79a8; }
        
        .border-primary-500 { border-color: #ff6b35; }
        .border-accent-500 { border-color: #00cec9; }
        .border-success-500 { border-color: #00b894; }
        
        .from-primary-500 { --tw-gradient-from: #ff6b35; }
        .to-accent-500 { --tw-gradient-to: #00cec9; }
        .from-primary-600 { --tw-gradient-from: #e55a2b; }
        .to-accent-600 { --tw-gradient-to: #00a8a3; }
        
        .hover\:from-primary-600:hover { --tw-gradient-from: #e55a2b; }
        .hover\:to-accent-600:hover { --tw-gradient-to: #00a8a3; }
        
        .bg-gradient-to-br { background-image: linear-gradient(to bottom right, var(--tw-gradient-stops)); }
        .bg-gradient-to-r { background-image: linear-gradient(to right, var(--tw-gradient-stops)); }
        
        /* Анимации и эффекты */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .floating {
            animation: float 6s ease-in-out infinite;
        }
        
        .glow {
            box-shadow: 0 0 20px rgba(255, 107, 53, 0.5);
        }
        
        .hover-glow:hover {
            box-shadow: 0 0 30px rgba(255, 107, 53, 0.7);
        }
        
        .text-gradient {
            background: linear-gradient(135deg, #ff6b35, #00cec9);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .neon-text {
            text-shadow: 0 0 10px #ff6b35, 0 0 20px #ff6b35, 0 0 30px #ff6b35;
        }
        
        .particle {
            position: absolute;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            animation: float 8s infinite ease-in-out;
        }
        
        /* Стили для красивого футера */
        .footer-gradient {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .contact-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        /* Стили для линии таймлайна */
        .timeline-container {
            position: relative;
        }
        
        .timeline-line {
            position: absolute;
            left: 50%;
            top: 0;
            bottom: 200px; /* Останавливаем линию перед кнопками */
            width: 3px;
            background: linear-gradient(to bottom, #8b5cf6, #ec4899, #f59e0b);
            transform: translateX(-50%);
            z-index: 1;
        }
        
        .timeline-line::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 50px;
            background: linear-gradient(to bottom, transparent, #f59e0b);
        }
        
        /* Новые улучшенные стили */
        .hero-glow {
            box-shadow: 0 0 50px rgba(139, 92, 246, 0.5);
        }
        
        .card-hover {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        
        .card-hover:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
        }
        
        .gradient-border {
            position: relative;
            background: linear-gradient(white, white) padding-box,
                        linear-gradient(135deg, #667eea, #764ba2) border-box;
            border: 2px solid transparent;
        }
        
        .shine-effect {
            position: relative;
            overflow: hidden;
        }
        
        .shine-effect::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                to bottom right,
                rgba(255, 255, 255, 0.3) 0%,
                rgba(255, 255, 255, 0.1) 40%,
                rgba(255, 255, 255, 0) 60%
            );
            transform: rotate(30deg);
            transition: all 0.6s;
        }
        
        .shine-effect:hover::before {
            animation: shine 1.5s ease-out;
        }
        
        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(30deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(30deg); }
        }
        
        .pulse-glow {
            animation: pulse-glow 2s infinite;
        }
        
        @keyframes pulse-glow {
            0% { box-shadow: 0 0 5px rgba(139, 92, 246, 0.5); }
            50% { box-shadow: 0 0 20px rgba(139, 92, 246, 0.8); }
            100% { box-shadow: 0 0 5px rgba(139, 92, 246, 0.5); }
        }
        
        .text-stroke {
            -webkit-text-stroke: 1px rgba(255, 255, 255, 0.3);
            color: transparent;
        }
        
        .glass-effect {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
    </style>
</head>
<body class="bg-gradient-to-br from-gray-50 to-purple-50 font-sans text-gray-800 overflow-x-hidden">
    <!-- Модальное окно для увеличения изображений -->
    <div id="imageModal" class="image-modal">
        <span class="close-modal">&times;</span>
        <img class="modal-content" id="modalImage">
        <div id="modalCaption" class="text-white text-center mt-4 text-lg"></div>
    </div>
    
    <!-- Частицы фона -->
    <div id="particles-container" class="fixed inset-0 pointer-events-none z-0"></div>
    
    <!-- Навигация -->
    <nav class="bg-gradient-to-r from-purple-700 to-pink-600 shadow-2xl sticky top-0 z-50 glass-effect">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <a href="#" class="text-2xl font-heading font-bold text-white neon-text pulse-glow">История ПК</a>
            <div class="flex space-x-6">
                <a href="#timeline" class="text-white/90 hover:text-white font-medium transition-all hover:scale-110 shine-effect px-3 py-1 rounded-lg">Хронология</a>
                <a href="#models" class="text-white/90 hover:text-white font-medium transition-all hover:scale-110 shine-effect px-3 py-1 rounded-lg">Модели</a>
                <a href="#test-section" class="text-white font-bold bg-white/20 px-4 py-2 rounded-lg glow shine-effect">Пройти тест</a>
            </div>
        </div>
    </nav>
    
    <main class="container mx-auto px-4 relative z-10">
        <!-- Hero Section -->
        <section class="relative h-screen flex items-center justify-center overflow-hidden">
            <div class="absolute inset-0 bg-gradient-to-r from-purple-900/80 to-pink-700/80 z-10"></div>
            <video autoplay muted loop class="absolute inset-0 w-full h-full object-cover">
                <source src="https://assets.mixkit.co/videos/preview/mixkit-circuit-board-with-computer-code-850-large.mp4" type="video/mp4">
            </video>
            <div class="relative z-20 text-center px-4 max-w-6xl">
                <h1 class="text-6xl md:text-8xl font-heading font-bold text-white mb-6 leading-tight floating">
                    <span class="text-gradient text-stroke">История</span> развития<br>персональных компьютеров
                </h1>
                <p class="text-xl md:text-2xl text-gray-200 mb-12 max-w-3xl mx-auto glass-effect p-6 rounded-2xl">
                    От революционного IBM PC 5150 до современных мощных систем — полная хронология технологического прогресса
                </p>
                <div class="flex flex-wrap justify-center gap-6">
                    <a href="#timeline" class="bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white px-8 py-4 rounded-xl font-semibold text-lg transition-all shadow-2xl hover:shadow-3xl flex items-center gap-2 transform hover:scale-105 hover-glow shine-effect">
                        <i data-feather="clock"></i> Хронология
                    </a>
                    <a href="#models" class="bg-white hover:bg-gray-100 text-purple-700 px-8 py-4 rounded-xl font-semibold text-lg transition-all shadow-2xl hover:shadow-3xl flex items-center gap-2 transform hover:scale-105 shine-effect gradient-border">
                        <i data-feather="cpu"></i> Легендарные модели
                    </a>
                    <a href="#test-section" class="bg-gradient-to-r from-yellow-500 to-orange-600 hover:from-yellow-600 hover:to-orange-700 text-white px-8 py-4 rounded-xl font-semibold text-lg transition-all shadow-2xl hover:shadow-3xl flex items-center gap-2 transform hover:scale-105 hover-glow shine-effect">
                        <i data-feather="award"></i> Пройти тест
                    </a>
                </div>
            </div>
            <div class="absolute bottom-8 left-0 right-0 z-20 text-center animate-bounce">
                <a href="#timeline" class="text-white">
                    <i data-feather="chevron-down" class="w-12 h-12"></i>
                </a>
            </div>
        </section>
        
        <!-- Enhanced Timeline Preview -->
        <section id="timeline" class="py-24 bg-gradient-to-br from-white to-purple-50 relative overflow-hidden">
            <div class="absolute inset-0 opacity-10">
                <div class="absolute inset-0 bg-circuit-pattern"></div>
            </div>
            <div class="container mx-auto px-4 relative z-10">
                <div class="text-center mb-20">
                    <h2 class="text-6xl font-heading font-bold mb-4 text-gradient text-shadow">Хронология развития</h2>
                    <div class="w-32 h-2 bg-gradient-to-r from-purple-500 to-pink-500 mx-auto mb-6 rounded-full"></div>
                    <p class="text-xl text-gray-600 max-w-4xl mx-auto glass-effect p-4 rounded-xl">
                        Полная история развития персональных компьютеров от первых микрокомпьютеров до современных систем
                    </p>
                </div>
                
                <div class="timeline-container">
                    <!-- Timeline line -->
                    <div class="timeline-line"></div>
                    
                    <!-- Timeline items -->
                    <div class="space-y-16 lg:space-y-0 lg:grid lg:grid-cols-2 lg:gap-y-20">
                        <!-- Item 1 -->
                        <div class="lg:pr-12">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-purple-500 card-hover shine-effect">
                                <div class="text-purple-500 font-bold text-xl mb-2">1950-1970</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">Предыстория ПК</h3>
                                <p class="text-gray-600 mb-4">
                                    Первые электронные компьютеры (ENIAC, UNIVAC), транзисторная революция, появление мэйнфреймов и миникомпьютеров.
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=dc84bde434c851d3076ce060c3d4cbe3_l-5879281-images-thumbs&n=13" 
                                         alt="Предыстория ПК" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="Эпоха мэйнфреймов - IBM System/360">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Item 2 -->
                        <div class="lg:pl-12 lg:mt-24">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-pink-500 card-hover shine-effect">
                                <div class="text-pink-500 font-bold text-xl mb-2">1970-е</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">Рождение персональных компьютеров</h3>
                                <p class="text-gray-600 mb-4">
                                    Altair 8800 (1975), Apple I (1976), Commodore PET (1977). Появление первых микропроцессоров (Intel 4004, 8008).
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=3b6a067e7bb0e51a4008820f75318622399ea915-11541841-images-thumbs&n=13" 
                                         alt="Рождение персональных компьютеров" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="Altair 8800 - первый коммерчески успешный ПК">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Item 3 -->
                        <div class="lg:pr-12">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-purple-500 card-hover shine-effect">
                                <div class="text-purple-500 font-bold text-xl mb-2">1980-е</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">Золотой век ПК</h3>
                                <p class="text-gray-600 mb-4">
                                    IBM PC (1981), Apple Macintosh (1984), Commodore 64 (1982). Windows 1.0 (1985). Рост рынка домашних компьютеров.
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=277d8815f0aecc8c347eb307f4d4b7c8_l-12422631-images-thumbs&n=13" 
                                         alt="Золотой век ПК" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="IBM PC 5150 - компьютер, изменивший мир">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Item 4 -->
                        <div class="lg:pl-12 lg:mt-24">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-pink-500 card-hover shine-effect">
                                <div class="text-pink-500 font-bold text-xl mb-2">1990-е</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">Эра Internet</h3>
                                <p class="text-gray-600 mb-4">
                                    Расцвет интернета, появление первых браузеров (Netscape, IE). Развитие мобильных технологий и КПК (Palm Pilot).
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=73bd9e893bf159572680010701d5d078_l-9234614-images-thumbs&n=13" 
                                         alt="Эра Internet" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="Windows 95 и начало эры интернета">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Item 5 -->
                        <div class="lg:pr-12">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-purple-500 card-hover shine-effect">
                                <div class="text-purple-500 font-bold text-xl mb-2">2000-е</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">Многоядерные процессоры и мобильность</h3>
                                <p class="text-gray-600 mb-4">
                                    Intel Core (2006), MacBook (2006), нетбуки (2007). Windows XP (2001) и Vista (2007). Начало эры смартфонов.
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=158e64fa0f46822f97b655009257b949_l-5223638-images-thumbs&n=13" 
                                         alt="Многоядерные процессоры и мобильность" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="Intel Core 2 Duo - эра многоядерных процессоров">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Item 6 -->
                        <div class="lg:pl-12 lg:mt-24">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-pink-500 card-hover shine-effect">
                                <div class="text-pink-500 font-bold text-xl mb-2">2010-2020</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">Ультрабуки и облачные технологии</h3>
                                <p class="text-gray-600 mb-4">
                                    MacBook Air (2010), Windows 8 (2012), Chromebooks (2011). SSD накопители, тонкие ультрабуки, трансформеры.
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=80631d750fb1001368791a37d2e9f572_l-4114739-images-thumbs&n=13" 
                                         alt="Ультрабуки и облачные технологии" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="MacBook Air - революция в дизайне ноутбуков">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Item 7 -->
                        <div class="lg:pr-12">
                            <div class="p-8 bg-white rounded-2xl shadow-2xl border-l-6 border-purple-500 card-hover shine-effect">
                                <div class="text-purple-500 font-bold text-xl mb-2">2020-е</div>
                                <h3 class="text-2xl font-heading font-bold mb-4">ИИ и квантовые компьютеры</h3>
                                <p class="text-gray-600 mb-4">
                                    Apple M1 (2020), Windows 11 (2021). ИИ-ускорители в процессорах. Развитие квантовых и нейроморфных компьютеров.
                                </p>
                                <div class="relative">
                                    <img src="https://avatars.mds.yandex.net/i?id=646f4262c80658434772c0b78d4963b0_l-5675359-images-thumbs&n=13" 
                                         alt="ИИ и квантовые компьютеры" 
                                         class="zoomable-image timeline-image rounded-xl shadow-lg cursor-zoom-in"
                                         data-caption="Современные технологии: ИИ и квантовые вычисления">
                                    <div class="zoom-overlay">
                                        <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                        Нажмите для увеличения
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Кнопки выбора источника -->
                    <div class="text-center mt-32">
                        <div class="mb-8">
                            <h3 class="text-2xl font-heading font-bold mb-4 text-purple-700">Изучите полную хронология</h3>
                            <p class="text-gray-600 mb-6 glass-effect p-4 rounded-xl">Выберите источник для более детального изучения истории компьютеров</p>
                        </div>
                        <div class="flex flex-col sm:flex-row gap-6 justify-center items-center">
                            <a href="https://en.wikipedia.org/wiki/History_of_personal_computers" target="_blank" 
                               class="inline-flex items-center px-8 py-4 bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white rounded-xl font-bold text-lg transition-all shadow-xl hover:shadow-2xl transform hover:scale-105 hover-glow shine-effect">
                                <i data-feather="external-link" class="mr-3 w-6 h-6"></i>
                                Wikipedia
                            </a>
                            <span class="text-gray-500 font-bold text-lg">или</span>
                            <a href="https://trashbox.ru/link/computer-history-from-1951" target="_blank" 
                               class="inline-flex items-center px-8 py-4 bg-gradient-to-r from-blue-600 to-teal-600 hover:from-blue-700 hover:to-teal-700 text-white rounded-xl font-bold text-lg transition-all shadow-xl hover:shadow-2xl transform hover:scale-105 hover-glow shine-effect">
                                <i data-feather="external-link" class="mr-3 w-6 h-6"></i>
                                Trashbox
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Legendary Computers Section -->
        <section id="models" class="py-20 bg-gradient-to-br from-purple-50 to-pink-50 relative overflow-hidden">
            <div class="absolute inset-0 opacity-10">
                <div class="absolute inset-0 bg-circuit-pattern"></div>
            </div>
            <div class="container mx-auto px-4 relative z-10">
                <div class="text-center mb-16">
                    <h2 class="text-6xl font-heading font-bold mb-6 text-gradient text-shadow">Легендарные компьютеры</h2>
                    <div class="w-32 h-2 bg-gradient-to-r from-purple-500 to-pink-500 mx-auto mb-8 rounded-full"></div>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto glass-effect p-4 rounded-xl">
                        Иконы компьютерной индустрии, изменившие технологический ландшафт
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                    <!-- IBM PC Card -->
                    <div class="bg-white rounded-2xl overflow-hidden shadow-2xl card-hover shine-effect">
                        <div class="relative h-64 overflow-hidden">
                            <div class="relative h-full">
                                <img src="https://avatars.dzeninfra.ru/get-zen_doc/271828/pub_68d0fcf7374d7b55b4dcf541_68d14439a9d7265e333a60c6/scale_1200" 
                                    alt="IBM PC 5150" 
                                    class="zoomable-image standard-image"
                                    data-caption="IBM PC 5150 (1981) - компьютер, задавший стандарты">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Нажмите для увеличения
                                    </div>
                            </div>
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent"></div>
                            <span class="absolute top-4 right-4 bg-purple-500 text-white px-3 py-1 rounded-full text-sm font-bold glow">1981</span>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-2">IBM PC 5150</h3>
                            <p class="text-gray-600 mb-6">Компьютер, задавший стандарты индустрии</p>
                            <div class="flex justify-between items-center">
                                <a href="https://en.wikipedia.org/wiki/IBM_Personal_Computer" target="_blank" 
                                    class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                    Исследовать <i data-feather="arrow-up-right" class="ml-1 w-4 h-4"></i>
                                </a>
                                <span class="text-xs bg-purple-100 text-purple-800 px-2 py-1 rounded">x86 архитектура</span>
                            </div>
                        </div>
                    </div>

                    <!-- Apple Macintosh Card -->
                    <div class="bg-white rounded-2xl overflow-hidden shadow-2xl card-hover shine-effect">
                        <div class="relative h-64 overflow-hidden">
                            <div class="relative h-full">
                                <img src="https://habrastorage.org/r/w1560/getpro/habr/upload_files/14b/d17/5ae/14bd175ae83fe8135fbcb95ed47f87ca.png" 
                                    alt="Apple Macintosh" 
                                    class="zoomable-image standard-image"
                                    data-caption="Apple Macintosh (1984) - революция графического интерфейса">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Нажмите для увеличения
                                </div>
                            </div>
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent"></div>
                            <span class="absolute top-4 right-4 bg-pink-500 text-white px-3 py-1 rounded-full text-sm font-bold glow">1984</span>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-2">Apple Macintosh</h3>
                            <p class="text-gray-600 mb-6">Революция графического интерфейса</p>
                            <div class="flex justify-between items-center">
                                <a href="https://en.wikipedia.org/wiki/Macintosh" target="_blank" 
                                    class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                    Исследовать <i data-feather="arrow-up-right" class="ml-1 w-4 h-4"></i>
                                </a>
                                <span class="text-xs bg-pink-100 text-pink-800 px-2 py-1 rounded">GUI революция</span>
                            </div>
                        </div>
                    </div>

                    <!-- Commodore 64 Card -->
                    <div class="bg-white rounded-2xl overflow-hidden shadow-2xl card-hover shine-effect">
                        <div class="relative h-64 overflow-hidden">
                            <div class="relative h-full">
                                <img src="https://avatars.mds.yandex.net/i?id=06be01952e25fa517dd6d45159500b1c_l-4461053-images-thumbs&n=13" 
                                    alt="Commodore 64" 
                                    class="zoomable-image standard-image"
                                    data-caption="Commodore 64 (1982) - самый продаваемый компьютер в истории">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Нажмите для увеличения
                                </div>
                            </div>
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent"></div>
                            <span class="absolute top-4 right-4 bg-yellow-500 text-white px-3 py-1 rounded-full text-sm font-bold glow">1982</span>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-2">Commodore 64</h3>
                            <p class="text-gray-600 mb-6">Самый продаваемый ПК в истории</p>
                            <div class="flex justify-between items-center">
                                <a href="https://en.wikipedia.org/wiki/Commodore_64" target="_blank" 
                                    class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                    Исследовать <i data-feather="arrow-up-right" class="ml-1 w-4 h-4"></i>
                                </a>
                                <span class="text-xs bg-yellow-100 text-yellow-800 px-2 py-1 rounded">17 млн продаж</span>
                            </div>
                        </div>
                    </div>

                    <!-- Modern PC Card -->
                    <div class="bg-white rounded-2xl overflow-hidden shadow-2xl card-hover shine-effect">
                        <div class="relative h-64 overflow-hidden">
                            <div class="relative h-full">
                                <img src="https://avatars.mds.yandex.net/i?id=04a7b1fca488a8a0ae36eed5be551dd8_l-5268893-images-thumbs&n=13" 
                                    alt="Современные ПК" 
                                    class="zoomable-image standard-image"
                                    data-caption="Современные ПК - мощь в ультратонком корпусе">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Нажмите для увеличения
                                </div>
                            </div>
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent"></div>
                            <span class="absolute top-4 right-4 bg-teal-500 text-white px-3 py-1 rounded-full text-sm font-bold glow">2020</span>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-2">Современные ПК</h3>
                            <p class="text-gray-600 mb-6">Мощь в ультратонком корпусе</p>
                            <div class="flex justify-between items-center">
                                <a href="https://en.wikipedia.org/wiki/Personal_computer" target="_blank" 
                                    class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                    Исследовать <i data-feather="arrow-up-right" class="ml-1 w-4 h-4"></i>
                                </a>
                                <span class="text-xs bg-teal-100 text-teal-800 px-2 py-1 rounded">Многоядерность</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="text-center mt-16">
                    <a href="https://en.wikipedia.org/wiki/History_of_personal_computers" target="_blank" 
                        class="inline-flex items-center px-8 py-4 bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white rounded-xl font-bold text-lg transition-all shadow-xl hover:shadow-2xl transform hover:scale-105 hover-glow shine-effect">
                        Полная хронология на Wikipedia
                        <i data-feather="external-link" class="ml-3 w-6 h-6"></i>
                    </a>
                </div>
            </div>
        </section>

        <!-- Enhanced Horizontal Timeline -->
        <section class="mb-24 bg-gradient-to-r from-white to-purple-50 rounded-2xl shadow-2xl overflow-hidden hero-glow">
            <div class="flex flex-col md:flex-row justify-between items-center px-8 py-6 bg-gradient-to-r from-purple-600 to-pink-600">
                <h2 class="text-4xl font-heading font-bold mb-4 md:mb-0 text-white text-shadow">Эволюция технологий</h2>
                <a href="https://en.wikipedia.org/wiki/History_of_personal_computers" target="_blank" class="flex items-center text-lg font-bold text-white hover:text-yellow-300 transition-colors shine-effect px-4 py-2 rounded-lg">
                    Исследовать на Wikipedia <i data-feather="external-link" class="ml-2 w-4 h-4"></i>
                </a>
            </div>
            <div class="timeline relative px-8 pb-8">
                <div class="flex overflow-x-auto pb-6 gap-6 snap-x snap-mandatory">
                    <!-- Timeline Item 1 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-purple-500 font-bold text-lg mb-2">1950-1960</div>
                            <h3 class="text-xl font-heading font-bold mb-3">Эра мэйнфреймов</h3>
                            <p class="text-gray-600 mb-4">ENIAC, UNIVAC, IBM 700 series</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=6be68834697d576db1f4dec6693eed6e_l-5425095-images-thumbs&n=13" 
                                     alt="Эра мэйнфреймов" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="IBM System/360 - эпоха мэйнфреймов">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Timeline Item 2 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-pink-500 font-bold text-lg mb-2">1970-е</div>
                            <h3 class="text-xl font-heading font-bold mb-3">Первые ПК</h3>
                            <p class="text-gray-600 mb-4">Altair 8800, Apple I, Commodore PET</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=172f6eecb2fd09c7023ed2bf8851e94f_l-5874305-images-thumbs&n=13" 
                                     alt="Первые ПК" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="Altair 8800 - начало эры персональных компьютеров">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Timeline Item 3 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-purple-500 font-bold text-lg mb-2">1980-е</div>
                            <h3 class="text-xl font-heading font-bold mb-3">IBM PC и Mac</h3>
                            <p class="text-gray-600 mb-4">IBM 5150, Apple II, Macintosh</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=52949273c05fad6f34d3d93846ab868b_l-12421995-images-thumbs&n=13" 
                                     alt="IBM PC и Mac" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="IBM PC и Apple Macintosh - конкуренция гигантов">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Timeline Item 4 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-pink-500 font-bold text-lg mb-2">1990-е</div>
                            <h3 class="text-xl font-heading font-bold mb-3">Internet и мобильность</h3>
                            <p class="text-gray-600 mb-4">Netscape, IE, Palm Pilot, первые ноутбуки</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=e9f066f1fe5f8a6d590aa60ce81755c3_l-4987479-images-thumbs&n=13" 
                                     alt="Internet и мобильность" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="Windows 95 и Netscape - начало интернет-эры">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Timeline Item 5 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-purple-500 font-bold text-lg mb-2">2000-е</div>
                            <h3 class="text-xl font-heading font-bold mb-3">Ноутбуки и Core</h3>
                            <p class="text-gray-600 mb-4">MacBook, Intel Core, нетбуки</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=43efaa543002437b9b7139b21b3fb0b7_l-10471591-images-thumbs&n=13" 
                                     alt="Ноутбуки и Core" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="Intel Core и MacBook - новая эра мобильности">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Timeline Item 6 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-pink-500 font-bold text-lg mb-2">2010-е</div>
                            <h3 class="text-xl font-heading font-bold mb-3">Ультрабуки и облака</h3>
                            <p class="text-gray-600 mb-4">MacBook Air, Surface, Chromebooks</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=62d650838d4b6bb19cab19b0b51cf086_l-5855238-images-thumbs&n=13" 
                                     alt="Ультрабуки и облака" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="MacBook Air и облачные технологии">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Timeline Item 7 -->
                    <div class="flex-shrink-0 w-80 snap-center">
                        <div class="bg-white rounded-2xl shadow-xl p-6 card-hover shine-effect">
                            <div class="text-purple-500 font-bold text-lg mb-2">2020-е</div>
                            <h3 class="text-xl font-heading font-bold mb-3">ИИ и ARM</h3>
                            <p class="text-gray-600 mb-4">Apple M1, Windows 11, квантовые ПК</p>
                            <div class="relative">
                                <img src="https://avatars.mds.yandex.net/i?id=6529bcb36000b5725e46d0e4f16234d9_l-5305527-images-thumbs&n=13" 
                                     alt="ИИ и ARM" 
                                     class="zoomable-image timeline-image rounded-xl"
                                     data-caption="Apple M1 и искусственный интеллект">
                                <div class="zoom-overlay">
                                    <i data-feather="zoom-in" class="w-3 h-3 mr-1 inline"></i>
                                    Увеличить
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Tech Milestones -->
        <section id="tech" class="mb-24">
            <div class="container mx-auto px-4">
                <div class="text-center mb-16">
                    <h2 class="text-6xl font-heading font-bold mb-6 text-gradient text-shadow">Ключевые технологические прорывы</h2>
                    <div class="w-32 h-2 bg-gradient-to-r from-purple-500 to-pink-500 mx-auto mb-8 rounded-full"></div>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto glass-effect p-4 rounded-xl">
                        Инновации, изменившие компьютерную индустрию
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <div class="bg-white rounded-2xl shadow-2xl overflow-hidden card-hover shine-effect">
                        <div class="h-48 bg-gradient-to-r from-purple-600 to-pink-600 flex items-center justify-center">
                            <i data-feather="cpu" class="w-20 h-20 text-white"></i>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-3">Изобретение микропроцессора</h3>
                            <p class="text-gray-600 mb-4">Intel 4004 (1971) - первый в мире микропроцессор, положивший начало эре персональных компьютеров.</p>
                            <a href="https://ru.wikipedia.org/wiki/Intel_4004" target="_blank" class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                Узнать больше <i data-feather="arrow-right" class="ml-2 w-4 h-4"></i>
                            </a>
                        </div>
                    </div>

                    <div class="bg-white rounded-2xl shadow-2xl overflow-hidden card-hover shine-effect">
                        <div class="h-48 bg-gradient-to-r from-pink-600 to-purple-600 flex items-center justify-center">
                            <i data-feather="monitor" class="w-20 h-20 text-white"></i>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-3">Графический интерфейс</h3>
                            <p class="text-gray-600 mb-4">Xerox Alto (1973) и Apple Macintosh (1984) революционизировали взаимодействие человека с компьютером.</p>
                            <a href="https://ru.wikipedia.org/wiki/Графический_интерфейс_пользователя" target="_blank" class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                Узнать больше <i data-feather="arrow-right" class="ml-2 w-4 h-4"></i>
                            </a>
                        </div>
                    </div>

                    <div class="bg-white rounded-2xl shadow-2xl overflow-hidden card-hover shine-effect">
                        <div class="h-48 bg-gradient-to-r from-yellow-500 to-orange-600 flex items-center justify-center">
                            <i data-feather="globe" class="w-20 h-20 text-white"></i>
                        </div>
                        <div class="p-6">
                            <h3 class="text-2xl font-heading font-bold mb-3">Появление интернета</h3>
                            <p class="text-gray-600 mb-4">ARPANET (1969) и World Wide Web (1991) изменили способ передачи информации и общения.</p>
                            <a href="https://ru.wikipedia.org/wiki/История_Интернета" target="_blank" class="text-purple-500 font-semibold hover:underline flex items-center transition-all hover:scale-105">
                                Узнать больше <i data-feather="arrow-right" class="ml-2 w-4 h-4"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Улучшенная секция теста -->
        <section id="test-section" class="py-20 bg-gradient-to-br from-purple-600 via-pink-600 to-orange-600 relative overflow-hidden">
            <div class="absolute inset-0 opacity-10">
                <div class="absolute inset-0 bg-circuit-pattern"></div>
            </div>
            <div class="container mx-auto px-4 relative z-10">
                <div class="text-center mb-16">
                    <h2 class="text-6xl font-heading font-bold mb-6 text-white text-shadow">Проверьте свои знания</h2>
                    <div class="w-32 h-2 bg-yellow-300 mx-auto mb-8"></div>
                    <p class="text-xl text-white/90 max-w-3xl mx-auto glass-effect p-6 rounded-2xl">
                        Пройдите тест и узнайте, насколько хорошо вы разбираетесь в истории персональных компьютеров
                    </p>
                </div>
                
                <!-- Контейнер для теста -->
                <div id="test-container" class="test-container bg-white rounded-2xl shadow-2xl p-8 max-w-4xl mx-auto hero-glow">
                    <!-- Экран регистрации -->
                    <div id="register-screen">
                        <div class="text-center mb-8">
                            <div class="inline-flex items-center justify-center w-20 h-20 bg-gradient-to-r from-purple-600 to-pink-600 text-white rounded-full mb-4 pulse-glow">
                                <i data-feather="user" class="w-10 h-10"></i>
                            </div>
                            <h3 class="text-3xl font-heading font-bold mb-2 text-purple-700">Регистрация</h3>
                            <p class="text-gray-600">Введите ваше имя для участия в рейтинге</p>
                        </div>
                        
                        <div class="mb-6">
                            <label for="user-name" class="block text-gray-700 font-medium mb-2">Ваше имя</label>
                            <input type="text" id="user-name" class="w-full px-4 py-3 border border-gray-300 rounded-xl focus:outline-none focus:ring-2 focus:ring-purple-500 focus:border-transparent gradient-border" placeholder="Введите ваше имя">
                        </div>
                        
                        <button id="register-btn" class="w-full bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white text-center font-bold py-4 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl transform hover:scale-105 shine-effect">
                            Начать тест
                        </button>
                    </div>
                    
                    <!-- Начальный экран -->
                    <div id="start-screen" class="hidden">
                        <div class="text-center">
                            <div class="mb-8">
                                <div class="inline-flex items-center justify-center w-20 h-20 bg-gradient-to-r from-purple-600 to-pink-600 text-white rounded-full mb-4 pulse-glow">
                                    <i data-feather="award" class="w-10 h-10"></i>
                                </div>
                                <h3 class="text-3xl font-heading font-bold mb-2 text-purple-700">Готовы начать?</h3>
                                <p class="text-gray-600">Проверьте свои знания прямо сейчас!</p>
                            </div>
                            
                            <div class="space-y-6 mb-8">
                                <div class="flex items-center justify-between bg-gradient-to-r from-blue-50 to-purple-50 p-4 rounded-xl border border-blue-200 card-hover">
                                    <div class="flex items-center">
                                        <i data-feather="clock" class="w-5 h-5 text-blue-500 mr-2"></i>
                                        <span class="text-blue-700">Время прохождения</span>
                                    </div>
                                    <span class="font-bold text-blue-700">5-7 минут</span>
                                </div>
                                
                                <div class="flex items-center justify-between bg-gradient-to-r from-green-50 to-teal-50 p-4 rounded-xl border border-green-200 card-hover">
                                    <div class="flex items-center">
                                        <i data-feather="help-circle" class="w-5 h-5 text-green-500 mr-2"></i>
                                        <span class="text-green-700">Количество вопросов</span>
                                    </div>
                                    <span class="font-bold text-green-700">15</span>
                                </div>
                                
                                <div class="flex items-center justify-between bg-gradient-to-r from-orange-50 to-red-50 p-4 rounded-xl border border-orange-200 card-hover">
                                    <div class="flex items-center">
                                        <i data-feather="bar-chart" class="w-5 h-5 text-orange-500 mr-2"></i>
                                        <span class="text-orange-700">Сложность</span>
                                    </div>
                                    <span class="font-bold text-orange-700">Разная</span>
                                </div>
                            </div>
                            
                            <button id="start-test-btn" class="w-full bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white text-center font-bold py-4 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl transform hover:scale-105 shine-effect">
                                Начать тест
                            </button>
                            
                            <p class="text-center text-gray-500 text-sm mt-4">
                                После завершения вы получите сертификат с вашим результатом
                            </p>
                        </div>
                    </div>
                    
                    <!-- Экран с вопросами -->
                    <div id="questions-screen" class="hidden">
                        <!-- Прогресс бар -->
                        <div class="mb-8">
                            <div class="flex justify-between text-sm text-gray-600 mb-2">
                                <span class="font-medium text-purple-700">Вопрос <span id="current-question">1</span> из <span id="total-questions">15</span></span>
                                <span id="score" class="font-bold text-pink-600">0 баллов</span>
                            </div>
                            <div class="w-full bg-gray-200 rounded-full h-3">
                                <div id="progress-bar" class="progress-bar bg-gradient-to-r from-purple-600 to-pink-600 h-3 rounded-full" style="width: 0%"></div>
                            </div>
                        </div>
                        
                        <!-- Вопрос -->
                        <div id="question-container">
                            <h3 id="question-text" class="text-2xl font-heading font-bold mb-6 text-purple-800"></h3>
                            
                            <!-- Варианты ответов -->
                            <div id="options-container" class="space-y-4 mb-8">
                                <!-- Варианты будут добавляться динамически -->
                            </div>
                            
                            <!-- Блок с объяснением -->
                            <div id="explanation-container" class="explanation-box bg-blue-50 border border-blue-200 rounded-xl p-4 mb-6">
                                <div class="flex items-start">
                                    <i data-feather="info" class="w-5 h-5 text-blue-500 mr-2 mt-0.5 flex-shrink-0"></i>
                                    <div>
                                        <h4 class="font-bold text-blue-700 mb-1">Объяснение:</h4>
                                        <p id="explanation-text" class="text-blue-800"></p>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Кнопка "Следующий вопрос" -->
                            <button id="next-question-btn" class="w-full bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white font-bold py-3 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl disabled:opacity-50 disabled:cursor-not-allowed transform hover:scale-105 shine-effect">
                                Следующий вопрос
                            </button>
                        </div>
                    </div>
                    
                    <!-- Экран с результатами -->
                    <div id="results-screen" class="hidden text-center">
                        <div class="mb-8">
                            <div class="result-badge inline-flex items-center justify-center w-24 h-24 bg-gradient-to-r from-green-500 to-teal-500 text-white rounded-full mb-6 pulse-glow">
                                <i data-feather="award" class="w-12 h-12"></i>
                            </div>
                            <h3 class="text-3xl font-heading font-bold mb-2 text-purple-700">Тест завершен!</h3>
                            <p class="text-gray-600">Ваш результат:</p>
                        </div>
                        
                        <div class="mb-8">
                            <div class="text-5xl font-bold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent mb-2" id="final-score">0</div>
                            <div class="text-xl text-gray-600 mb-4" id="result-text">Новичок</div>
                            <div class="bg-gradient-to-r from-blue-50 to-purple-50 rounded-xl p-4 max-w-md mx-auto border border-blue-200 card-hover">
                                <p id="result-description" class="text-gray-700"></p>
                            </div>
                        </div>
                        
                        <div class="flex flex-col sm:flex-row gap-4 justify-center mb-8">
                            <button id="show-certificate-btn" class="bg-gradient-to-r from-yellow-500 to-orange-600 hover:from-yellow-600 hover:to-orange-700 text-white font-bold py-3 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl transform hover:scale-105 shine-effect">
                                Получить сертификат
                            </button>
                            <button id="restart-test-btn" class="bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white font-bold py-3 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl transform hover:scale-105 shine-effect">
                                Пройти еще раз
                            </button>
                            <button id="share-result-btn" class="bg-gradient-to-r from-blue-600 to-teal-600 hover:from-blue-700 hover:to-teal-700 text-white font-bold py-3 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl flex items-center justify-center gap-2 transform hover:scale-105 shine-effect">
                                <i data-feather="share"></i> Поделиться
                            </button>
                        </div>
                    </div>
                    
                    <!-- Экран с сертификатом -->
                    <div id="certificate-screen" class="hidden text-center">
                        <div class="certificate rounded-2xl p-8 mb-8 hero-glow">
                            <div class="border-4 border-double border-gold-500 p-6 rounded-lg">
                                <h2 class="text-4xl font-heading font-bold text-purple-800 mb-4">СЕРТИФИКАТ</h2>
                                <p class="text-xl text-gray-700 mb-2">Настоящим удостоверяется, что</p>
                                <h3 class="text-3xl font-bold text-purple-700 mb-6" id="certificate-name"></h3>
                                <p class="text-lg text-gray-700 mb-4">успешно прошел(ла) тест по истории персональных компьютеров</p>
                                <div class="text-2xl font-bold bg-gradient-to-r from-purple-600 to-pink-600 bg-clip-text text-transparent mb-4" id="certificate-score"></div>
                                <p class="text-lg text-gray-700 mb-6" id="certificate-level"></p>
                                <div class="flex justify-between items-center mt-8">
                                    <div class="text-center">
                                        <div class="w-32 h-1 bg-gray-400 mx-auto mb-2"></div>
                                        <p class="text-gray-600">Дата</p>
                                        <p class="font-bold" id="certificate-date"></p>
                                    </div>
                                    <div class="text-center">
                                        <div class="w-32 h-1 bg-gray-400 mx-auto mb-2"></div>
                                        <p class="text-gray-600">Подпись</p>
                                        <p class="font-bold">История ПК</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex flex-col sm:flex-row gap-4 justify-center">
                            <button id="download-certificate-btn" class="bg-gradient-to-r from-green-600 to-teal-600 hover:from-green-700 hover:to-teal-700 text-white font-bold py-3 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl flex items-center justify-center gap-2 transform hover:scale-105 shine-effect">
                                <i data-feather="download"></i> Скачать сертификат
                            </button>
                            <button id="back-to-results-btn" class="bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700 text-white font-bold py-3 px-6 rounded-xl transition-all shadow-lg hover:shadow-xl transform hover:scale-105 shine-effect">
                                К результатам
                            </button>
                        </div>
                    </div>
                </div>
                
                <!-- Рейтинг участников -->
                <div id="rating-section" class="mt-16 bg-white/20 backdrop-blur-sm rounded-2xl p-8 text-white border border-white/30 glass-effect hidden">
                    <h3 class="text-2xl font-heading font-bold mb-8 text-center text-shadow">Рейтинг участников</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-white">
                            <thead>
                                <tr class="border-b border-white/30">
                                    <th class="py-3 px-4 text-left">Место</th>
                                    <th class="py-3 px-4 text-left">Имя</th>
                                    <th class="py-3 px-4 text-left">Результат</th>
                                    <th class="py-3 px-4 text-left">Уровень</th>
                                    <th class="py-3 px-4 text-left">Дата</th>
                                </tr>
                            </thead>
                            <tbody id="rating-table">
                                <!-- Данные рейтинга будут добавляться динамически -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Отзывы участников -->
                <div class="mt-16 text-center">
                    <h3 class="text-2xl font-heading font-bold mb-8 text-white text-shadow">Отзывы участников</h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <div class="bg-white/20 backdrop-blur-sm rounded-2xl p-6 text-white border border-white/30 glass-effect card-hover">
                            <div class="flex items-center mb-4">
                                <div class="w-12 h-12 bg-gradient-to-r from-yellow-400 to-orange-500 rounded-full flex items-center justify-center mr-4">
                                    <span class="font-bold text-white">ИШ</span>
                                </div>
                                <div>
                                    <h4 class="font-bold">Илья Ш.</h4>
                                    <div class="flex text-yellow-300">
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                    </div>
                                </div>
                            </div>
                            <p class="text-white/90">"Я обожаю историю технологий, и этот тест оказался для меня настоящей находкой. Вопросы составлены так, что даже знатоки найдут что-то новое. Лично я был впечатлен историей Commodore 64 — не думал, что этот компьютер был настолько популярен. Объяснения после каждого ответа — это отличная идея, они помогают разобраться в теме. Рекомендую!"</p>
                        </div>
                        
                        <div class="bg-white/20 backdrop-blur-sm rounded-2xl p-6 text-white border border-white/30 glass-effect card-hover">
                            <div class="flex items-center mb-4">
                                <div class="w-12 h-12 bg-gradient-to-r from-blue-400 to-purple-500 rounded-full flex items-center justify-center mr-4">
                                    <span class="font-bold text-white">КЗ</span>
                                </div>
                                <div>
                                    <h4 class="font-bold">Кирилл З.</h4>
                                    <div class="flex text-yellow-300">
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4"></i>
                                    </div>
                                </div>
                            </div>
                            <p class="text-white/90">"Как студент IT-направления, я оценил глубину вопросов. Тест охватывает не только основные вехи, но и малоизвестные факты. Вопрос про первый микропроцессор Intel 4004 был особенно интересным. Единственное, хотелось бы больше вопросов про современные тенденции. В целом - отлично структурированный и познавательный тест!"</p>
                        </div>
                        
                        <div class="bg-white/20 backdrop-blur-sm rounded-2xl p-6 text-white border border-white/30 glass-effect card-hover">
                            <div class="flex items-center mb-4">
                                <div class="w-12 h-12 bg-gradient-to-r from-green-400 to-teal-500 rounded-full flex items-center justify-center mr-4">
                                    <span class="font-bold text-white">РФ</span>
                                </div>
                                <div>
                                    <h4 class="font-bold">Руслан Ф.</h4>
                                    <div class="flex text-yellow-300">
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                    </div>
                                </div>
                            </div>
                            <p class="text-white/90">"Прошел тест вместе с сыном-подростком, который увлекается компьютерами. Оба узнали много нового! Вопросы составлены грамотно, охватывают разные эпохи развития ПК. Сын теперь хочет углубленно изучать историю компьютерной техники. Отличный способ провести время с пользой и привить интерес к технологиям подрастающему поколению!"</p>
                        </div>
                    </div>
                    
                    <!-- Новые отзывы участников -->
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-8">
                        <div class="bg-white/20 backdrop-blur-sm rounded-2xl p-6 text-white border border-white/30 glass-effect card-hover">
                            <div class="flex items-center mb-4">
                                <div class="w-12 h-12 bg-gradient-to-r from-purple-400 to-pink-500 rounded-full flex items-center justify-center mr-4">
                                    <span class="font-bold text-white">АС</span>
                                </div>
                                <div>
                                    <h4 class="font-bold">Алексей С.</h4>
                                    <div class="flex text-yellow-300">
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                    </div>
                                </div>
                            </div>
                            <p class="text-white/90">"Потрясающий проект! Как человек, работающий в IT-сфере более 10 лет, я оценил глубину проработки материала. Особенно понравился раздел про эволюцию процессоров - от Intel 4004 до современных многоядерных монстров. Дизайн сайта просто шикарный, анимации плавные, все работает идеально. Обязательно добавлю в закладки!"</p>
                        </div>
                        
                        <div class="bg-white/20 backdrop-blur-sm rounded-2xl p-6 text-white border border-white/30 glass-effect card-hover">
                            <div class="flex items-center mb-4">
                                <div class="w-12 h-12 bg-gradient-to-r from-red-400 to-orange-500 rounded-full flex items-center justify-center mr-4">
                                    <span class="font-bold text-white">АД</span>
                                </div>
                                <div>
                                    <h4 class="font-bold">Андрей Д.</h4>
                                    <div class="flex text-yellow-300">
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                    </div>
                                </div>
                            </div>
                            <p class="text-white/90">"Великолепно! Я коллекционирую старые компьютеры, и этот сайт стал для меня настоящей находкой. Хронология составлена очень грамотно, все ключевые моменты отражены. Тест прошел на 93% - горжусь собой! Отдельное спасибо за качественные изображения и возможность их увеличивать. Теперь использую этот ресурс для подготовки к лекциям по истории вычислительной техники."</p>
                        </div>
                        
                        <div class="bg-white/20 backdrop-blur-sm rounded-2xl p-6 text-white border border-white/30 glass-effect card-hover">
                            <div class="flex items-center mb-4">
                                <div class="w-12 h-12 bg-gradient-to-r from-indigo-400 to-blue-500 rounded-full flex items-center justify-center mr-4">
                                    <span class="font-bold text-white">НМ</span>
                                </div>
                                <div>
                                    <h4 class="font-bold">Никита М.</h4>
                                    <div class="flex text-yellow-300">
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4 fill-current"></i>
                                        <i data-feather="star" class="w-4 h-4"></i>
                                    </div>
                                </div>
                            </div>
                            <p class="text-white/90">"Отличный образовательный ресурс! Как начинающий веб-разработчик, я не только узнал много нового об истории ПК, но и почерпнул идеи для собственных проектов. Особенно впечатлила реализация таймлайна с анимированной линией и плавными переходами. Тест challenging, но справедливый. Единственное, хотелось бы видеть больше вопросов про советские компьютеры. В целом - браво разработчикам!"</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
    
    <!-- Красивый футер с контактами -->
    <footer class="footer-gradient text-white pt-16 pb-8">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 mb-12">
                <!-- Информация о проекте -->
                <div class="contact-card rounded-2xl p-8 card-hover">
                    <h3 class="text-3xl font-heading font-bold mb-6 text-white">О проекте</h3>
                    <p class="text-lg text-white/90 mb-6 leading-relaxed">
                        Этот проект создан с целью сохранения и популяризации истории развития персональных компьютеров. 
                        Мы стремимся показать, как технологии меняли наш мир, от первых громоздких мэйнфреймов до современных 
                        мощных систем с искусственным интеллектом.
                    </p>
                    <p class="text-lg text-white/90 leading-relaxed">
                        Здесь вы найдете не только исторические факты, но и интерактивный тест для проверки знаний, 
                        который поможет лучше понять эволюцию компьютерных технологий и их влияние на современный мир.
                    </p>
                </div>
                
                <!-- Контакты разработчика -->
                <div class="contact-card rounded-2xl p-8 card-hover">
                    <h3 class="text-3xl font-heading font-bold mb-6 text-white">Связь с разработчиком</h3>
                    <p class="text-lg text-white/90 mb-8 leading-relaxed">
                        Есть вопросы, предложения или хотите сотрудничать? 
                        Буду рад услышать ваше мнение о проекте!
                    </p>
                    
                    <div class="space-y-6">
                        <div class="flex items-center group">
                            <div class="w-12 h-12 bg-white/20 rounded-full flex items-center justify-center mr-4 group-hover:bg-white/30 transition-all">
                                <i data-feather="mail" class="w-6 h-6 text-white"></i>
                            </div>
                            <div>
                                <p class="text-white/70 text-sm">Электронная почта</p>
                                <a href="mailto:artemvladimirovich1912@gmail.com" 
                                   class="text-white text-lg font-semibold hover:text-yellow-300 transition-colors">
                                    artemvladimirovich1912@gmail.com
                                </a>
                            </div>
                        </div>
                        
                        <div class="flex items-center group">
                            <div class="w-12 h-12 bg-white/20 rounded-full flex items-center justify-center mr-4 group-hover:bg-white/30 transition-all">
                                <i data-feather="phone" class="w-6 h-6 text-white"></i>
                            </div>
                            <div>
                                <p class="text-white/70 text-sm">Рабочий телефон</p>
                                <a href="tel:+79280353792" 
                                   class="text-white text-lg font-semibold hover:text-yellow-300 transition-colors">
                                    +7 (928) 035-37-92
                                </a>
                            </div>
                        </div>
                        
                        <div class="flex items-center group">
                            <div class="w-12 h-12 bg-white/20 rounded-full flex items-center justify-center mr-4 group-hover:bg-white/30 transition-all">
                                <i data-feather="message-circle" class="w-6 h-6 text-white"></i>
                            </div>
                            <div>
                                <p class="text-white/70 text-sm">Мессенджеры</p>
                                <div class="flex space-x-4 mt-2">
                                    <a href="https://wa.me/79280353792" target="_blank" 
                                       class="text-white text-lg font-semibold hover:text-green-300 transition-colors flex items-center">
                                        <i data-feather="message-circle" class="w-5 h-5 mr-2"></i> WhatsApp
                                    </a>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex items-center group">
                            <div class="w-12 h-12 bg-white/20 rounded-full flex items-center justify-center mr-4 group-hover:bg-white/30 transition-all">
                                <i data-feather="heart" class="w-6 h-6 text-white"></i>
                            </div>
                            <div>
                                <p class="text-white/70 text-sm">Статус проекта</p>
                                <p class="text-white text-lg font-semibold">Активно развивается</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Нижняя часть футера -->
            <div class="border-t border-white/20 pt-8 text-center">
                <div class="flex flex-col md:flex-row justify-between items-center">
                    <p class="text-white/80 mb-4 md:mb-0">
                        © 2026 История развития персональных компьютеров. Все права защищены.
                    </p>
                    <div class="flex space-x-6">
                        <a href="#timeline" class="text-white/80 hover:text-white transition-colors">Хронология</a>
                        <a href="#models" class="text-white/80 hover:text-white transition-colors">Модели</a>
                        <a href="#test-section" class="text-white/80 hover:text-white transition-colors">Тест</a>
                    </div>
                </div>
            </div>
        </div>
    </footer>
    
    <script>
        // Инициализация иконок
        feather.replace();
        
        // Создание частиц фона
        function createParticles() {
            const container = document.getElementById('particles-container');
            const particleCount = 30;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                
                // Случайные параметры
                const size = Math.random() * 10 + 5;
                const left = Math.random() * 100;
                const animationDuration = Math.random() * 10 + 10;
                const animationDelay = Math.random() * 5;
                
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                particle.style.left = `${left}%`;
                particle.style.top = `${Math.random() * 100}%`;
                particle.style.animationDuration = `${animationDuration}s`;
                particle.style.animationDelay = `${animationDelay}s`;
                particle.style.opacity = Math.random() * 0.5 + 0.2;
                
                container.appendChild(particle);
            }
        }
        
        // Функционал модального окна для увеличения изображений
        function initImageModal() {
            const modal = document.getElementById("imageModal");
            const modalImg = document.getElementById("modalImage");
            const modalCaption = document.getElementById("modalCaption");
            const closeBtn = document.getElementsByClassName("close-modal")[0];
            
            // Добавляем обработчики клика на все изображения с классом zoomable-image
            document.querySelectorAll('.zoomable-image').forEach(img => {
                img.addEventListener('click', function() {
                    modal.style.display = "block";
                    modalImg.src = this.src;
                    modalCaption.textContent = this.getAttribute('data-caption') || '';
                });
            });
            
            // Закрытие модального окна
            closeBtn.addEventListener('click', function() {
                modal.style.display = "none";
            });
            
            // Закрытие при клике вне изображения
            modal.addEventListener('click', function(event) {
                if (event.target === modal) {
                    modal.style.display = "none";
                }
            });
            
            // Закрытие по клавише ESC
            document.addEventListener('keydown', function(event) {
                if (event.key === 'Escape') {
                    modal.style.display = "none";
                }
            });
            
            console.log('Image modal initialized - click any image to zoom!');
        }
        
        // Данные теста - теперь 15 вопросов
        const testQuestions = [
            {
                question: "Какой компьютер считается первым массовым персональным компьютером?",
                options: [
                    "IBM PC 5150",
                    "Apple I",
                    "Commodore PET",
                    "Altair 8800"
                ],
                correct: 0,
                explanation: "IBM PC 5150, выпущенный в 1981 году, стал первым массовым персональным компьютером и установил стандарты для всей индустрии."
            },
            {
                question: "В каком году был представлен первый Macintosh?",
                options: [
                    "1982",
                    "1984",
                    "1986",
                    "1988"
                ],
                correct: 1,
                explanation: "Apple Macintosh был представлен 24 января 1984 года и стал революционным благодаря графическому интерфейсу и мыши."
            },
            {
                question: "Какой микропроцессор использовался в IBM PC 5150?",
                options: [
                    "Intel 8088",
                    "Intel 8086",
                    "Motorola 68000",
                    "Zilog Z80"
                ],
                correct: 0,
                explanation: "IBM PC 5150 использовал процессор Intel 8088 с тактовой частотой 4,77 МГц."
            },
            {
                question: "Какой компьютер стал самым продаваемым в истории?",
                options: [
                    "IBM PC",
                    "Apple Macintosh",
                    "Commodore 64",
                    "ZX Spectrum"
                ],
                correct: 2,
                explanation: "Commodore 64, выпущенный в 1982 году, стал самым продаваемым компьютером в истории с тиражом более 17 миллионов единиц."
            },
            {
                question: "Какая операционная система была установлена на первом IBM PC?",
                options: [
                    "MS-DOS",
                    "CP/M",
                    "Unix",
                    "Windows 1.0"
                ],
                correct: 0,
                explanation: "Первый IBM PC поставлялся с операционной системой PC DOS 1.0, которая была лицензированной версией MS-DOS от Microsoft."
            },
            {
                question: "Какой компьютер положил начало эре домашних компьютеров в СССР?",
                options: [
                    "БК-0010",
                    "Агат",
                    "Электроника Б3-34",
                    "Микроша"
                ],
                correct: 1,
                explanation: "Агат - первый советский серийный 8-разрядный персональный компьютер, созданный по образцу Apple II."
            },
            {
                question: "Кто считается изобретателем первого программируемого компьютера?",
                options: [
                    "Алан Тьюринг",
                    "Чарльз Бэббидж",
                    "Билл Гейтс",
                    "Стив Джобс"
                ],
                correct: 1,
                explanation: "Чарльз Бэббидж разработал концепцию Аналитической машины в 1837 году, которая считается прообразом современного компьютера."
            },
            {
                question: "В каком году появился первый транзистор?",
                options: [
                    "1947",
                    "1955",
                    "1962",
                    "1971"
                ],
                correct: 0,
                explanation: "Первый работающий транзистор был создан в 1947 году в Bell Labs Уильямом Шокли, Джоном Бардином и Уолтером Браттейном."
            },
            {
                question: "Какой был первый микропроцессор от Intel?",
                options: [
                    "Intel 4004",
                    "Intel 8008",
                    "Intel 8080",
                    "Intel 8086"
                ],
                correct: 0,
                explanation: "Intel 4004, выпущенный в 1971 году, был первым в мире коммерчески доступным микропроцессором."
            },
            {
                question: "Какая компания создала первый ноутбук?",
                options: [
                    "IBM",
                    "Apple",
                    "Osborne",
                    "Compaq"
                ],
                correct: 2,
                explanation: "Osborne 1, выпущенный в 1981 году, считается первым коммерчески успешным портативным компьютером."
            },
            {
                question: "В каком году появилась операционная система Windows?",
                options: [
                    "1981",
                    "1985",
                    "1990",
                    "1995"
                ],
                correct: 1,
                explanation: "Первая версия Windows была выпущена 20 ноября 1985 года как графическая надстройка для MS-DOS."
            },
            {
                question: "Какой компьютер использовал процессор MOS 6502?",
                options: [
                    "IBM PC",
                    "Apple II",
                    "Commodore Amiga",
                    "ZX Spectrum"
                ],
                correct: 1,
                explanation: "Apple II, выпущенный в 1977 году, использовал процессор MOS Technology 6502 с тактовой частотой 1 МГц."
            },
            {
                question: "Когда был представлен первый смартфон?",
                options: [
                    "1992",
                    "1996",
                    "2000",
                    "2007"
                ],
                correct: 0,
                explanation: "IBM Simon, представленный в 1992 году, считается первым в мире смартфоном."
            },
            {
                question: "Какой интерфейс заменил параллельные порты в современных компьютерах?",
                options: [
                    "USB",
                    "FireWire",
                    "Thunderbolt",
                    "HDMI"
                ],
                correct: 0,
                explanation: "USB (Universal Serial Bus) стал стандартом для подключения периферийных устройств, заменив параллельные и последовательные порты."
            },
            {
                question: "В каком году появился первый коммерческий SSD?",
                options: [
                    "1978",
                    "1989",
                    "1991",
                    "2000"
                ],
                correct: 2,
                explanation: "Первый коммерческий SSD был представлен компанией SanDisk в 1991 году и имел объем 20 МБ."
            }
        ];
        
        // Переменные состояния теста
        let currentQuestion = 0;
        let score = 0;
        let userAnswers = [];
        let userName = "";
        let userResults = JSON.parse(localStorage.getItem('pcHistoryTestResults')) || [];
        
        // Элементы DOM
        const registerScreen = document.getElementById('register-screen');
        const startScreen = document.getElementById('start-screen');
        const questionsScreen = document.getElementById('questions-screen');
        const resultsScreen = document.getElementById('results-screen');
        const certificateScreen = document.getElementById('certificate-screen');
        const ratingSection = document.getElementById('rating-section');
        const registerBtn = document.getElementById('register-btn');
        const startTestBtn = document.getElementById('start-test-btn');
        const nextQuestionBtn = document.getElementById('next-question-btn');
        const restartTestBtn = document.getElementById('restart-test-btn');
        const shareResultBtn = document.getElementById('share-result-btn');
        const showCertificateBtn = document.getElementById('show-certificate-btn');
        const downloadCertificateBtn = document.getElementById('download-certificate-btn');
        const backToResultsBtn = document.getElementById('back-to-results-btn');
        const questionText = document.getElementById('question-text');
        const optionsContainer = document.getElementById('options-container');
        const explanationContainer = document.getElementById('explanation-container');
        const explanationText = document.getElementById('explanation-text');
        const currentQuestionElement = document.getElementById('current-question');
        const totalQuestionsElement = document.getElementById('total-questions');
        const progressBar = document.getElementById('progress-bar');
        const scoreElement = document.getElementById('score');
        const finalScoreElement = document.getElementById('final-score');
        const resultTextElement = document.getElementById('result-text');
        const resultDescriptionElement = document.getElementById('result-description');
        const certificateName = document.getElementById('certificate-name');
        const certificateScore = document.getElementById('certificate-score');
        const certificateLevel = document.getElementById('certificate-level');
        const certificateDate = document.getElementById('certificate-date');
        const ratingTable = document.getElementById('rating-table');
        const userNameInput = document.getElementById('user-name');
        
        // Инициализация теста
        function initTest() {
            totalQuestionsElement.textContent = testQuestions.length;
            registerBtn.addEventListener('click', registerUser);
            startTestBtn.addEventListener('click', startTest);
            nextQuestionBtn.addEventListener('click', nextQuestion);
            restartTestBtn.addEventListener('click', restartTest);
            shareResultBtn.addEventListener('click', shareResult);
            showCertificateBtn.addEventListener('click', showCertificate);
            downloadCertificateBtn.addEventListener('click', downloadCertificate);
            backToResultsBtn.addEventListener('click', backToResults);
            
            // Скрыть блок с объяснением изначально
            explanationContainer.classList.remove('show');
            
            // Показать рейтинг, если есть результаты
            if (userResults.length > 0) {
                ratingSection.classList.remove('hidden');
                updateRatingTable();
            }
        }
        
        // Регистрация пользователя
        function registerUser() {
            const name = userNameInput.value.trim();
            if (name === "") {
                alert("Пожалуйста, введите ваше имя");
                return;
            }
            
            userName = name;
            registerScreen.classList.add('hidden');
            startScreen.classList.remove('hidden');
        }
        
        // Начать тест
        function startTest() {
            startScreen.classList.add('hidden');
            questionsScreen.classList.remove('hidden');
            currentQuestion = 0;
            score = 0;
            userAnswers = [];
            loadQuestion();
        }
        
        // Загрузить вопрос
        function loadQuestion() {
            const question = testQuestions[currentQuestion];
            questionText.textContent = question.question;
            currentQuestionElement.textContent = currentQuestion + 1;
            
            // Обновить прогресс бар
            const progress = ((currentQuestion) / testQuestions.length) * 100;
            progressBar.style.width = `${progress}%`;
            
            // Обновить счет
            scoreElement.textContent = `${score} баллов`;
            
            // Очистить контейнер с вариантами ответов
            optionsContainer.innerHTML = '';
            
            // Скрыть блок с объяснением
            explanationContainer.classList.remove('show');
            
            // Добавить варианты ответов
            question.options.forEach((option, index) => {
                const optionElement = document.createElement('div');
                optionElement.className = 'option-card bg-white border-2 border-gray-200 rounded-xl p-4';
                optionElement.innerHTML = `
                    <div class="flex items-center">
                        <div class="w-8 h-8 flex items-center justify-center rounded-full border border-gray-300 mr-3 font-bold text-purple-700">
                            ${String.fromCharCode(65 + index)}
                        </div>
                        <span class="text-gray-800">${option}</span>
                    </div>
                `;
                
                optionElement.addEventListener('click', () => selectOption(index, optionElement));
                optionsContainer.appendChild(optionElement);
            });
            
            // Сбросить состояние кнопки "Следующий вопрос"
            nextQuestionBtn.disabled = true;
            nextQuestionBtn.textContent = currentQuestion === testQuestions.length - 1 ? 'Завершить тест' : 'Следующий вопрос';
        }
        
        // Выбрать вариант ответа
        function selectOption(optionIndex, optionElement) {
            // Сбросить выделение всех вариантов
            document.querySelectorAll('.option-card').forEach(card => {
                card.classList.remove('selected', 'correct', 'incorrect');
            });
            
            // Выделить выбранный вариант
            optionElement.classList.add('selected');
            
            // Включить кнопку "Следующий вопрос"
            nextQuestionBtn.disabled = false;
            
            // Сохранить ответ пользователя
            userAnswers[currentQuestion] = optionIndex;
        }
        
        // Перейти к следующему вопросу
        function nextQuestion() {
            // Проверить ответ
            const question = testQuestions[currentQuestion];
            const userAnswer = userAnswers[currentQuestion];
            
            // Показать правильный ответ и объяснение
            document.querySelectorAll('.option-card').forEach((card, index) => {
                if (index === question.correct) {
                    card.classList.add('correct');
                } else if (index === userAnswer && userAnswer !== question.correct) {
                    card.classList.add('incorrect');
                }
            });
            
            // Показать объяснение
            explanationText.textContent = question.explanation;
            explanationContainer.classList.add('show');
            
            // Обновить счет, если ответ правильный
            if (userAnswer === question.correct) {
                score++;
            }
            
            // Обновить счет
            scoreElement.textContent = `${score} баллов`;
            
            // Отключить кнопку "Следующий вопрос" до таймаута
            nextQuestionBtn.disabled = true;
            
            // Задержка перед переходом к следующему вопросу
            setTimeout(() => {
                currentQuestion++;
                
                if (currentQuestion < testQuestions.length) {
                    loadQuestion();
                } else {
                    showResults();
                }
            }, 3000); // Увеличил время до 3 секунд, чтобы пользователь успел прочитать объяснение
        }
        
        // Показать результаты
        function showResults() {
            questionsScreen.classList.add('hidden');
            resultsScreen.classList.remove('hidden');
            
            // Обновить прогресс бар до 100%
            progressBar.style.width = '100%';
            
            // Вычислить процент правильных ответов
            const percentage = Math.round((score / testQuestions.length) * 100);
            finalScoreElement.textContent = `${score}/${testQuestions.length}`;
            
            // Определить уровень знаний
            let resultText, resultDescription;
            if (percentage >= 90) {
                resultText = "Эксперт!";
                resultDescription = "Потрясающе! Вы настоящий эксперт в истории персональных компьютеров. Ваши знания охватывают все ключевые моменты развития компьютерной техники.";
            } else if (percentage >= 70) {
                resultText = "Опытный пользователь";
                resultDescription = "Отличный результат! Вы хорошо разбираетесь в истории ПК и знаете основные вехи развития компьютерной индустрии.";
            } else if (percentage >= 50) {
                resultText = "Любитель";
                resultDescription = "Хороший результат! Вы знакомы с основными моментами истории персональных компьютеров, но есть куда расти.";
            } else {
                resultText = "Новичок";
                resultDescription = "Не расстраивайтесь! История ПК обширна и многогранна. Пройдите тест еще раз, чтобы закрепить знания.";
            }
            
            resultTextElement.textContent = resultText;
            resultDescriptionElement.textContent = resultDescription;
            
            // Сохранить результат
            saveResult(userName, score, testQuestions.length, resultText);
            
            // Показать рейтинг
            ratingSection.classList.remove('hidden');
            updateRatingTable();
        }
        
        // Сохранить результат
        function saveResult(name, score, total, level) {
            const result = {
                name: name,
                score: score,
                total: total,
                level: level,
                date: new Date().toLocaleDateString('ru-RU'),
                percentage: Math.round((score / total) * 100)
            };
            
            userResults.push(result);
            
            // Сортировка по проценту правильных ответов
            userResults.sort((a, b) => b.percentage - a.percentage);
            
            // Сохранить в localStorage
            localStorage.setItem('pcHistoryTestResults', JSON.stringify(userResults));
        }
        
        // Обновить таблицу рейтинга
        function updateRatingTable() {
            ratingTable.innerHTML = '';
            
            userResults.slice(0, 10).forEach((result, index) => {
                const row = document.createElement('tr');
                row.className = 'border-b border-white/20';
                
                let medal = '';
                if (index === 0) medal = '🥇';
                else if (index === 1) medal = '🥈';
                else if (index === 2) medal = '🥉';
                
                row.innerHTML = `
                    <td class="py-3 px-4">${index + 1} ${medal}</td>
                    <td class="py-3 px-4">${result.name}</td>
                    <td class="py-3 px-4">${result.score}/${result.total} (${result.percentage}%)</td>
                    <td class="py-3 px-4">${result.level}</td>
                    <td class="py-3 px-4">${result.date}</td>
                `;
                
                ratingTable.appendChild(row);
            });
        }
        
        // Показать сертификат
        function showCertificate() {
            resultsScreen.classList.add('hidden');
            certificateScreen.classList.remove('hidden');
            
            const percentage = Math.round((score / testQuestions.length) * 100);
            
            certificateName.textContent = userName;
            certificateScore.textContent = `${score}/${testQuestions.length} (${percentage}%)`;
            certificateLevel.textContent = resultTextElement.textContent;
            certificateDate.textContent = new Date().toLocaleDateString('ru-RU');
        }
        
        // Вернуться к результатам
        function backToResults() {
            certificateScreen.classList.add('hidden');
            resultsScreen.classList.remove('hidden');
        }
        
        // Скачать сертификат
        function downloadCertificate() {
            alert("Функция скачивания сертификата будет реализована в полной версии приложения!");
        }
        
        // Перезапустить тест
        function restartTest() {
            resultsScreen.classList.add('hidden');
            startScreen.classList.remove('hidden');
        }
        
        // Поделиться результатом
        function shareResult() {
            const percentage = Math.round((score / testQuestions.length) * 100);
            const shareText = `Я прошел тест по истории персональных компьютеров и набрал ${score} из ${testQuestions.length} баллов (${percentage}%)! Попробуйте и вы:`;
            
            if (navigator.share) {
                navigator.share({
                    title: 'Тест по истории ПК',
                    text: shareText,
                    url: window.location.href
                });
            } else {
                // Fallback для браузеров без поддержки Web Share API
                navigator.clipboard.writeText(shareText + ' ' + window.location.href).then(() => {
                    alert('Результат скопирован в буфер обмена!');
                });
            }
        }
        
        // Инициализировать тест при загрузке страницы
        document.addEventListener('DOMContentLoaded', function() {
            initTest();
            initImageModal();
            createParticles();
            feather.replace();
            
            console.log('Website fully loaded! Image zoom functionality is ready.');
        });
    </script>
</body>
</html>
