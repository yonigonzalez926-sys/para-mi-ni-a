<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feliz Aniversario, Mi Amor</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400;1,600&family=Montserrat:wght@300;400;500;600&family=Sacramento&display=swap" rel="stylesheet">
    <!-- FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: {
                            light: '#fce7f3',
                            DEFAULT: '#f472b6',
                            dark: '#c084fc',
                            glow: 'rgba(244, 114, 182, 0.4)'
                        },
                        rose: {
                            DEFAULT: '#e879f9',
                            glow: 'rgba(232, 121, 249, 0.4)'
                        },
                        dark: {
                            bg: '#0f0814',
                            card: '#1a0b2e',
                            border: '#3b0764'
                        }
                    },
                    fontFamily: {
                        serif: ['"Cormorant Garamond"', 'serif'],
                        sans: ['"Montserrat"', 'sans-serif'],
                        cursive: ['"Sacramento"', 'cursive']
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #0f0814;
            color: #fce7f3;
            font-family: 'Montserrat', sans-serif;
            overflow-x: hidden;
            user-select: none;
        }

        #particles-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .gold-border-glow {
            border: 1px solid rgba(232, 121, 249, 0.35);
            box-shadow: 0 10px 30px -10px rgba(15, 8, 20, 0.9), 0 0 25px rgba(232, 121, 249, 0.2);
        }

        .gold-gradient-text {
            background: linear-gradient(135deg, #fce7f3 0%, #f472b6 50%, #c084fc 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gold-button {
            background: linear-gradient(135deg, #ec4899 0%, #a855f7 100%);
            color: #ffffff;
            transition: all 0.3s ease;
        }

        .gold-button:hover {
            background: linear-gradient(135deg, #f472b6 0%, #c084fc 100%);
            box-shadow: 0 0 20px rgba(236, 72, 153, 0.5);
            transform: translateY(-2px);
        }

        /* Lock CSS Effects */
        .lock-container {
            perspective: 1000px;
        }

        .fingerprint-scanner {
            position: relative;
            width: 90px;
            height: 90px;
            margin: 0 auto;
            border-radius: 50%;
            background: rgba(244, 114, 182, 0.08);
            border: 2px solid rgba(244, 114, 182, 0.4);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(244, 114, 182, 0.2);
            transition: all 0.3s ease;
        }

        .fingerprint-scanner:hover {
            transform: scale(1.05);
            border-color: rgba(244, 114, 182, 0.8);
            box-shadow: 0 0 30px rgba(244, 114, 182, 0.5);
        }

        .scan-line {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, transparent, #e879f9, #f472b6, transparent);
            box-shadow: 0 0 10px #f472b6;
            opacity: 0;
        }

        .scanning .scan-line {
            opacity: 1;
            animation: scanAnim 1.5s infinite linear;
        }

        @keyframes scanAnim {
            0% { top: 10%; }
            50% { top: 85%; }
            100% { top: 10%; }
        }

        .pulse-ring {
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 2px solid #f472b6;
            animation: pulseRing 2s infinite ease-out;
            pointer-events: none;
        }

        @keyframes pulseRing {
            0% { transform: scale(0.95); opacity: 0.8; }
            100% { transform: scale(1.35); opacity: 0; }
        }

        .lock-shackle {
            width: 60px;
            height: 60px;
            border: 8px solid #f472b6;
            border-bottom: none;
            border-radius: 35px 35px 0 0;
            margin: 0 auto -10px;
            transition: transform 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .lock-shackle.unlocked {
            transform: translateY(-20px) rotateY(180deg);
        }

        .heart-card {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
        }

        .heart-card:hover {
            transform: translateY(-8px) scale(1.03);
            box-shadow: 0 15px 30px rgba(244, 114, 182, 0.3);
        }

        .modal-backdrop {
            background: rgba(15, 8, 20, 0.92);
            backdrop-filter: blur(10px);
        }

        @keyframes pulse-slow {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        .pulse-heart {
            animation: pulse-slow 2s infinite ease-in-out;
        }

        /* Sobres de carta interactiva */
        .envelope-wrapper {
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        .envelope-wrapper:hover {
            transform: scale(1.02);
        }

        /* Animación suave de pétalos rotando */
        @keyframes petalFall {
            0% {
                transform: translateY(-10vh) rotate(0deg) translateX(0);
                opacity: 1;
            }
            100% {
                transform: translateY(105vh) rotate(360deg) translateX(50px);
                opacity: 0.2;
            }
        }

        .petal {
            position: fixed;
            background: linear-gradient(135deg, #f472b6, #e879f9);
            border-radius: 15px 0 15px 0;
            pointer-events: none;
            z-index: 2;
            opacity: 0.7;
            box-shadow: 0 0 10px rgba(244, 114, 182, 0.3);
        }
    </style>
</head>
<body class="relative min-h-screen">
    <!-- Canvas para Partículas -->
    <canvas id="particles-canvas"></canvas>

    <!-- FASE 1: CANDADO DEL AMOR CON ESCÁNER DE HUELLA -->
    <div id="lock-screen" class="fixed inset-0 z-50 flex flex-col items-center justify-center p-4 bg-dark-bg transition-all duration-1000">
        <div class="text-center max-w-sm w-full gold-border-glow bg-dark-card/95 p-8 rounded-3xl backdrop-blur-md relative overflow-hidden flex flex-col items-center">
            
            <span class="text-pink-400 text-xs tracking-[0.3em] uppercase mb-4 font-medium flex items-center gap-1.5">
                <i class="fa-solid fa-fingerprint text-[12px]"></i> Candado Biométrico
            </span>

            <!-- Gráfico de Candado -->
            <div class="lock-container my-2">
                <div id="lock-shackle" class="lock-shackle"></div>
            </div>

            <!-- Escáner de Huella -->
            <div id="fingerprint-btn" onclick="triggerScan()" class="fingerprint-scanner my-4 group">
                <div class="pulse-ring"></div>
                <div class="scan-line"></div>
                <i class="fa-solid fa-fingerprint text-5xl text-pink-400 group-hover:text-pink-300 transition-colors"></i>
            </div>

            <h2 class="font-serif text-2xl text-white font-normal mt-1 mb-1">Escanea tu Huella</h2>
            <p class="text-purple-300/70 text-xs mb-4">O ingresa el código de nuestro aniversario (2406)</p>

            <!-- Digitos de Combinación (4 DÍGITOS PARA 2406) -->
            <div class="flex gap-2 justify-center mb-5">
                <input type="text" maxlength="1" class="code-input w-12 h-14 bg-black/60 border border-pink-500/40 rounded-xl text-center text-xl font-bold text-pink-300 focus:outline-none focus:border-pink-400 focus:ring-1 focus:ring-pink-400" data-index="0" inputmode="numeric">
                <input type="text" maxlength="1" class="code-input w-12 h-14 bg-black/60 border border-pink-500/40 rounded-xl text-center text-xl font-bold text-pink-300 focus:outline-none focus:border-pink-400 focus:ring-1 focus:ring-pink-400" data-index="1" inputmode="numeric">
                <input type="text" maxlength="1" class="code-input w-12 h-14 bg-black/60 border border-pink-500/40 rounded-xl text-center text-xl font-bold text-pink-300 focus:outline-none focus:border-pink-400 focus:ring-1 focus:ring-pink-400" data-index="2" inputmode="numeric">
                <input type="text" maxlength="1" class="code-input w-12 h-14 bg-black/60 border border-pink-500/40 rounded-xl text-center text-xl font-bold text-pink-300 focus:outline-none focus:border-pink-400 focus:ring-1 focus:ring-pink-400" data-index="3" inputmode="numeric">
            </div>

            <button id="unlock-btn" class="gold-button w-full py-3 rounded-xl text-xs font-semibold uppercase tracking-wider flex items-center justify-center gap-2">
                <i class="fa-solid fa-lock-open"></i> Abrir Candado
            </button>

            <p id="error-msg" class="text-pink-400 text-xs mt-3 hidden">Código incorrecto. ¡Inténtalo de nuevo, mi amor!</p>
        </div>
    </div>

    <!-- PANTALLA PRINCIPAL CON LOS 3 CORAZONES Y CONTENIDO -->
    <main id="main-content" class="relative z-10 opacity-0 transition-opacity duration-1000 max-w-4xl mx-auto px-4 py-8 md:py-12 w-full">

        <!-- CABECERA -->
        <header class="text-center mb-10">
            <div class="inline-flex items-center justify-center gap-2 px-4 py-1.5 rounded-full border border-pink-500/30 bg-pink-500/10 text-pink-300 text-xs tracking-[0.25em] uppercase mb-4">
                <i class="fa-solid fa-gem text-[10px]"></i> Capítulo Especial
            </div>
            <h1 class="font-serif text-4xl md:text-6xl text-white font-normal mb-2 tracking-wide">
                ¡Feliz Aniversario!
            </h1>
            <p id="girlfriend-name-display" class="font-cursive text-3xl md:text-4xl text-pink-300">
                Para el amor de mi vida
            </p>
        </header>

        <!-- SECCIÓN DE LOS TRES CORAZONES -->
        <section class="mb-12">
            <div class="text-center mb-6">
                <h3 class="text-xs uppercase tracking-[0.25em] text-purple-300/80">Toca cada corazón para descubrir las sorpresas</h3>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-10">
                <!-- CORAZÓN 1 -->
                <div onclick="openHeartModal(1)" class="heart-card gold-border-glow bg-dark-card/90 p-6 rounded-2xl text-center relative group">
                    <div class="w-16 h-16 rounded-full bg-pink-500/10 border border-pink-500/30 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform">
                        <i class="fa-solid fa-heart text-2xl text-pink-400 pulse-heart"></i>
                    </div>
                    <span class="text-[10px] tracking-widest text-pink-300 uppercase block mb-1">Sorpresa 1</span>
                    <h4 class="font-serif text-xl text-white font-medium mb-2">Carta de Amor</h4>
                    <p class="text-xs text-purple-200/70 font-light">Mis palabras más profundas escritas para ti en este día.</p>
                </div>

                <!-- CORAZÓN 2 -->
                <div onclick="openHeartModal(2)" class="heart-card gold-border-glow bg-dark-card/90 p-6 rounded-2xl text-center relative group">
                    <div class="w-16 h-16 rounded-full bg-pink-500/10 border border-pink-500/30 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform">
                        <i class="fa-solid fa-hourglass-half text-2xl text-purple-400 pulse-heart"></i>
                    </div>
                    <span class="text-[10px] tracking-widest text-pink-300 uppercase block mb-1">Sorpresa 2</span>
                    <h4 class="font-serif text-xl text-white font-medium mb-2">Tiempo Juntos</h4>
                    <p class="text-xs text-purple-200/70 font-light">El contador exacto de cada segundo a tu lado.</p>
                </div>

                <!-- CORAZÓN 3 -->
                <div onclick="openHeartModal(3)" class="heart-card gold-border-glow bg-dark-card/90 p-6 rounded-2xl text-center relative group">
                    <div class="w-16 h-16 rounded-full bg-pink-500/10 border border-pink-500/30 flex items-center justify-center mx-auto mb-4 group-hover:scale-110 transition-transform">
                        <i class="fa-solid fa-star text-2xl text-fuchsia-400 pulse-heart"></i>
                    </div>
                    <span class="text-[10px] tracking-widest text-pink-300 uppercase block mb-1">Sorpresa 3</span>
                    <h4 class="font-serif text-xl text-white font-medium mb-2">Mis Promesas</h4>
                    <p class="text-xs text-purple-200/70 font-light">Todo lo que te prometo para nuestro futuro juntos.</p>
                </div>
            </div>

            <!-- CONTADOR DE TIEMPO EN VIVO CON ROSAS Y DECORACIÓN -->
            <div class="gold-border-glow bg-dark-card/90 p-6 md:p-8 rounded-3xl text-center max-w-2xl mx-auto mb-16 relative overflow-hidden">
                <div class="text-center mb-3">
                    <p class="font-serif italic text-pink-200 text-lg">Para ti, mi amor</p>
                    <p class="text-xs text-purple-300/80 max-w-md mx-auto my-2 leading-relaxed">
                        "Este mes volví a confirmar que el tiempo se puede medir en miradas. Que las palabras pueden volverse caricia y que un «hola» al amanecer puede sostener el resto del día."
                    </p>
                </div>

                <span class="text-[10px] tracking-[0.3em] text-pink-300 uppercase block mb-2 font-medium">
                    <i class="fa-solid fa-heart text-pink-400 mr-1"></i> feliz mes, mi amor
                </span>

                <div class="grid grid-cols-2 md:grid-cols-4 gap-3 my-4">
                    <div class="bg-black/60 border border-pink-500/30 p-4 rounded-2xl backdrop-blur-sm">
                        <span id="main-c-days" class="font-serif text-3xl md:text-4xl text-pink-300 font-bold block">0</span>
                        <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Días</span>
                    </div>
                    <div class="bg-black/60 border border-pink-500/30 p-4 rounded-2xl backdrop-blur-sm">
                        <span id="main-c-hours" class="font-serif text-3xl md:text-4xl text-pink-300 font-bold block">0</span>
                        <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Horas</span>
                    </div>
                    <div class="bg-black/60 border border-pink-500/30 p-4 rounded-2xl backdrop-blur-sm">
                        <span id="main-c-mins" class="font-serif text-3xl md:text-4xl text-pink-300 font-bold block">0</span>
                        <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Minutos</span>
                    </div>
                    <div class="bg-black/60 border border-pink-500/30 p-4 rounded-2xl backdrop-blur-sm">
                        <span id="main-c-secs" class="font-serif text-3xl md:text-4xl text-pink-300 font-bold block">0</span>
                        <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Segundos</span>
                    </div>
                </div>

                <!-- Ilustración Decorativa de Rosas -->
                <div class="mt-4 opacity-80 flex justify-center items-center gap-3 text-pink-400">
                    <i class="fa-solid fa-rose text-2xl"></i>
                    <i class="fa-solid fa-heart text-xs"></i>
                    <i class="fa-solid fa-rose text-2xl"></i>
                </div>
            </div>

            <!-- SECCIÓN ABRE LA CARTA (SOBRE INTERACTIVO) -->
            <div class="max-w-xl mx-auto text-center my-12">
                <h2 class="font-serif text-3xl md:text-4xl text-white italic mb-6">Abre la carta</h2>
                
                <div onclick="openLetterModal()" class="envelope-wrapper gold-border-glow bg-gradient-to-b from-amber-200 to-amber-500 p-8 md:p-12 rounded-3xl relative overflow-hidden shadow-2xl mx-auto max-w-md cursor-pointer border-2 border-amber-300">
                    <div class="flex flex-col items-center justify-center">
                        <div class="w-16 h-16 rounded-full bg-pink-600 border-2 border-white shadow-lg flex items-center justify-center mb-3">
                            <i class="fa-solid fa-heart text-2xl text-white"></i>
                        </div>
                        <span class="text-amber-950 font-serif text-sm font-semibold tracking-wider">Toca el sobre para abrir</span>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- MODAL DE CARTA (ABRE LA CARTA ESTILO VIDEO) -->
    <div id="letter-modal" class="fixed inset-0 z-50 flex items-center justify-center p-4 modal-backdrop opacity-0 pointer-events-none transition-all duration-300">
        <div class="bg-[#faf3e0] text-gray-800 max-w-md w-full rounded-2xl p-6 md:p-8 relative shadow-2xl border-2 border-amber-300 max-h-[85vh] flex flex-col font-serif">
            <button onclick="closeLetterModal()" class="absolute top-4 right-4 text-gray-500 hover:text-black text-xl w-8 h-8 rounded-full bg-amber-200/50 flex items-center justify-center">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <div class="overflow-y-auto pr-2 space-y-4 text-sm md:text-base leading-relaxed text-justify">
                <h3 class="font-serif text-2xl text-center text-rose-800 italic mb-2">Mi amor bonito,</h3>
                <p>Hoy celebramos otro aniversario más juntos y no encuentro las palabras exactas para decirte lo feliz que me haces.</p>
                <p>Gracias por cada sonrisa, por tu paciencia infinita y por hacer que cada día a tu lado sea único e inolvidable. Contigo aprendí que querer bonito es fácil cuando es con la persona correcta.</p>
                <p>Gracias por las noches largas, las pláticas tontas y por sostenerme siempre. Eres mi lugar seguro y mi coincidencia favorita.</p>
                <p>Espero seguir celebrando muchos años más a tu lado, construyendo nuestra historia paso a paso.</p>
                <p class="text-right font-serif italic text-rose-900 font-bold mt-6">— Te amo infinitamente</p>
            </div>
        </div>
    </div>

    <!-- MODAL DE CONTENIDOS (CORAZÓN 1, 2 O 3) -->
    <div id="heart-modal" class="fixed inset-0 z-50 flex items-center justify-center p-4 modal-backdrop opacity-0 pointer-events-none transition-all duration-300">
        <div class="bg-dark-card border border-pink-500/40 max-w-lg w-full rounded-3xl p-6 md:p-8 relative gold-border-glow max-h-[85vh] flex flex-col">
            <button onclick="closeHeartModal()" class="absolute top-4 right-4 text-purple-300 hover:text-white text-xl w-8 h-8 rounded-full bg-black/40 flex items-center justify-center">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <!-- CONTENIDO DINÁMICO DEL MODAL -->
            <div id="modal-content-container" class="overflow-y-auto pr-1 flex-1">
                <!-- Se llena dinámicamente desde JavaScript -->
            </div>
        </div>
    </div>

    <footer class="relative z-10 text-center py-6 border-t border-purple-900/50 text-purple-300/60 text-xs font-light">
        <p>Hecho con amor ✦ ¡Por muchos años más juntos!</p>
    </footer>

    <script>
        // CONFIGURACIÓN PERSONALIZABLE
        const config = {
            correctCode: "2406",
            girlfriendName: "Mi Amor",
            boyfriendName: "Tu Amor",
            startDate: "2026-06-24T00:00:00"
        };

        // ABRIR Y CERRAR CARTA
        function openLetterModal() {
            const modal = document.getElementById('letter-modal');
            if (modal) modal.classList.remove('opacity-0', 'pointer-events-none');
        }

        function closeLetterModal() {
            const modal = document.getElementById('letter-modal');
            if (modal) modal.classList.add('opacity-0', 'pointer-events-none');
        }

        // GENERAR PÉTALOS FLOTANTES DE ROSAS
        function createPetals() {
            const petalanimationContainer = document.body;
            for (let i = 0; i < 15; i++) {
                const petal = document.createElement('div');
                petal.className = 'petal';
                const size = Math.random() * 12 + 10;
                petal.style.width = `${size}px`;
                petal.style.height = `${size * 1.3}px`;
                petal.style.left = `${Math.random() * 100}vw`;
                petal.style.animation = `petalFall ${Math.random() * 6 + 6}s linear infinite`;
                petal.style.animationDelay = `${Math.random() * 5}s`;
                petalanimationContainer.appendChild(petal);
            }
        }

        // CANDADO DE AMOR Y HUELLA DACTILAR LOGIC
        const inputs = document.querySelectorAll('.code-input');
        const unlockBtn = document.getElementById('unlock-btn');
        const lockShackle = document.getElementById('lock-shackle');
        const errorMsg = document.getElementById('error-msg');
        const fingerprintBtn = document.getElementById('fingerprint-btn');

        let isScanning = false;

        function triggerScan() {
            if (isScanning) return;
            isScanning = true;
            fingerprintBtn.classList.add('scanning');

            setTimeout(() => {
                inputs[0].value = "2";
                inputs[1].value = "4";
                inputs[2].value = "0";
                inputs[3].value = "6";
                fingerprintBtn.classList.remove('scanning');
                isScanning = false;
                checkCode();
            }, 1200);
        }

        inputs.forEach((input, index) => {
            input.addEventListener('input', (e) => {
                if (e.target.value.length === 1 && index < inputs.length - 1) {
                    inputs[index + 1].focus();
                }
            });

            input.addEventListener('keydown', (e) => {
                if (e.key === 'Backspace' && !e.target.value && index > 0) {
                    inputs[index - 1].focus();
                }
            });
        });

        function checkCode() {
            let enteredCode = "";
            inputs.forEach(input => enteredCode += input.value);

            if (enteredCode === config.correctCode) {
                if (errorMsg) errorMsg.classList.add('hidden');
                if (lockShackle) lockShackle.classList.add('unlocked');
                
                setTimeout(() => {
                    const lockScreen = document.getElementById('lock-screen');
                    const mainContent = document.getElementById('main-content');
                    if (lockScreen) lockScreen.classList.add('opacity-0', 'pointer-events-none');
                    setTimeout(() => {
                        if (lockScreen) lockScreen.style.display = 'none';
                        if (mainContent) mainContent.classList.remove('opacity-0');
                        startLiveCounter();
                        createPetals();
                    }, 1000);
                }, 600);
            } else {
                if (errorMsg) errorMsg.classList.remove('hidden');
                inputs.forEach(input => input.value = '');
                inputs[0].focus();
            }
        }

        if (unlockBtn) unlockBtn.addEventListener('click', checkCode);

        // CONTENIDO DE LOS 3 CORAZONES
        function openHeartModal(number) {
            const container = document.getElementById('modal-content-container');
            const modal = document.getElementById('heart-modal');
            if (!container || !modal) return;

            if (number === 1) {
                container.innerHTML = `
                    <div class="text-center mb-6">
                        <i class="fa-solid fa-envelope-open-text text-pink-400 text-4xl mb-3"></i>
                        <h3 class="font-serif text-3xl text-white">Nuestra Carta</h3>
                        <p class="text-xs text-pink-300 tracking-widest uppercase">Palabras del corazón</p>
                    </div>
                    <div class="font-serif text-lg text-purple-100 leading-relaxed space-y-4 italic font-light text-justify">
                        <p>Mi amor bonito,</p>
                        <p>Hoy celebramos un aniversario más juntos, y no puedo evitar sonreír al recordar cada instante a tu lado. Gracias por llegar a mi vida y llenarla de luz, de risas sinceras y de un amor tan puro y único.</p>
                        <p>Contigo he aprendido lo hermoso que es compartir la vida de la mano de alguien especial. Cada día a tu lado es mi regalo favorito.</p>
                        <p class="text-center text-pink-300 font-semibold not-italic mt-6">— Te amo infinitamente —</p>
                    </div>
                `;
            } else if (number === 2) {
                container.innerHTML = `
                    <div class="text-center mb-6">
                        <i class="fa-solid fa-clock text-pink-400 text-4xl mb-3"></i>
                        <h3 class="font-serif text-3xl text-white">Tiempo de Amor</h3>
                        <p class="text-xs text-pink-300 tracking-widest uppercase">Cada segundo cuenta</p>
                    </div>
                    <div id="live-counter" class="grid grid-cols-2 gap-3 text-center my-6">
                        <div class="bg-black/50 border border-pink-500/30 p-4 rounded-2xl">
                            <span id="c-days" class="font-serif text-3xl text-pink-300 font-bold block">0</span>
                            <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Días</span>
                        </div>
                        <div class="bg-black/50 border border-pink-500/30 p-4 rounded-2xl">
                            <span id="c-hours" class="font-serif text-3xl text-pink-300 font-bold block">0</span>
                            <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Horas</span>
                        </div>
                        <div class="bg-black/50 border border-pink-500/30 p-4 rounded-2xl">
                            <span id="c-mins" class="font-serif text-3xl text-pink-300 font-bold block">0</span>
                            <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Minutos</span>
                        </div>
                        <div class="bg-black/50 border border-pink-500/30 p-4 rounded-2xl">
                            <span id="c-secs" class="font-serif text-3xl text-pink-300 font-bold block">0</span>
                            <span class="text-[10px] text-purple-300/70 uppercase tracking-widest">Segundos</span>
                        </div>
                    </div>
                    <p class="text-center text-xs text-purple-200/70 italic">Construyendo una historia eterna juntos.</p>
                `;
                startLiveCounter();
            } else if (number === 3) {
                container.innerHTML = `
                    <div class="text-center mb-6">
                        <i class="fa-solid fa-hand-holding-heart text-pink-400 text-4xl mb-3"></i>
                        <h3 class="font-serif text-3xl text-white">Mis Promesas</h3>
                        <p class="text-xs text-pink-300 tracking-widest uppercase">Para nuestro futuro</p>
                    </div>
                    <div class="space-y-3 font-serif italic text-purple-100 text-base">
                        <div class="p-3.5 rounded-2xl bg-black/40 border border-purple-900/40 flex items-start gap-3">
                            <span class="text-pink-400 font-bold not-italic">1.</span>
                            <p>Estar a tu lado en cada momento, cuidándote y celebrando tus logros.</p>
                        </div>
                        <div class="p-3.5 rounded-2xl bg-black/40 border border-purple-900/40 flex items-start gap-3">
                            <span class="text-pink-400 font-bold not-italic">2.</span>
                            <p>Sacarte una sonrisa incluso en tus días más difíciles.</p>
                        </div>
                        <div class="p-3.5 rounded-2xl bg-black/40 border border-purple-900/40 flex items-start gap-3">
                            <span class="text-pink-400 font-bold not-italic">3.</span>
                            <p>Seguir enamorándote todos los días como la primera vez.</p>
                        </div>
                        <div class="p-3.5 rounded-2xl bg-black/40 border border-purple-900/40 flex items-start gap-3">
                            <span class="text-pink-400 font-bold not-italic">4.</span>
                            <p>Construir juntos todos los sueños que imaginamos.</p>
                        </div>
                    </div>
                `;
            }

            modal.classList.remove('opacity-0', 'pointer-events-none');
        }

        function closeHeartModal() {
            const modal = document.getElementById('heart-modal');
            if (modal) modal.classList.add('opacity-0', 'pointer-events-none');
        }

        // CONTADOR EN TIEMPO REAL
        let counterInterval = null;
        function startLiveCounter() {
            if (counterInterval) clearInterval(counterInterval);
            
            function update() {
                const start = new Date(config.startDate);
                const now = new Date();
                const diff = now - start;

                const days = Math.floor(diff / (1000 * 60 * 60 * 24));
                const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
                const mins = Math.floor((diff / 1000 / 60) % 60);
                const secs = Math.floor((diff / 1000) % 60);

                if (document.getElementById('c-days')) document.getElementById('c-days').innerText = days;
                if (document.getElementById('c-hours')) document.getElementById('c-hours').innerText = hours;
                if (document.getElementById('c-mins')) document.getElementById('c-mins').innerText = mins;
                if (document.getElementById('c-secs')) document.getElementById('c-secs').innerText = secs;

                if (document.getElementById('main-c-days')) document.getElementById('main-c-days').innerText = days;
                if (document.getElementById('main-c-hours')) document.getElementById('main-c-hours').innerText = hours;
                if (document.getElementById('main-c-mins')) document.getElementById('main-c-mins').innerText = mins;
                if (document.getElementById('main-c-secs')) document.getElementById('main-c-secs').innerText = secs;
            }

            update();
            counterInterval = setInterval(update, 1000);
        }

        // PARTICULAS DE FONDO ROSA Y MORADAS
        const canvas = document.getElementById('particles-canvas');
        const ctx = canvas ? canvas.getContext('2d') : null;
        let particles = [];

        function resizeCanvas() {
            if (!canvas) return;
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        const particleColors = ['#f472b6', '#e879f9', '#c084fc', '#fce7f3'];

        class Particle {
            constructor() { this.reset(); }
            reset() {
                this.x = Math.random() * (canvas ? canvas.width : 500);
                this.y = (canvas ? canvas.height : 500) + Math.random() * 20;
                this.size = Math.random() * 2.5 + 1;
                this.speedY = Math.random() * 0.8 + 0.3;
                this.speedX = (Math.random() - 0.5) * 0.4;
                this.opacity = Math.random() * 0.5 + 0.3;
                this.color = particleColors[Math.floor(Math.random() * particleColors.length)];
            }
            update() {
                this.y -= this.speedY;
                this.x += this.speedX;
                if (this.y < -10) this.reset();
            }
            draw() {
                if (!ctx) return;
                ctx.save();
                ctx.globalAlpha = this.opacity;
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
                ctx.restore();
            }
        }

        function initParticles() {
            particles = [];
            const count = Math.min(Math.floor(window.innerWidth / 15), 45);
            for (let i = 0; i < count; i++) particles.push(new Particle());
        }

        function animateParticles() {
            if (canvas && ctx) {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                particles.forEach(p => { p.update(); p.draw(); });
            }
            requestAnimationFrame(animateParticles);
        }

        window.onload = () => {
            initParticles();
            animateParticles();
        };
    </script>
</body>
</html>
