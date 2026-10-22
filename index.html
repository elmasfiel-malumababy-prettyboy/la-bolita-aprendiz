<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>La Bolita Aprendiz 3D</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Three.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800;900&display=swap" rel="stylesheet">
    
    <style>
        * {
            box-sizing: border-box;
            user-select: none;
            -webkit-user-select: none;
            -webkit-touch-callout: none;
        }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            font-family: 'Outfit', sans-serif;
            background-color: #080c14;
        }

        #canvas-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        /* Capa HUD */
        .ui-hud {
            position: absolute;
            inset: 0;
            z-index: 10;
            pointer-events: none;
        }

        .interactive-ui {
            pointer-events: auto !important;
            cursor: pointer;
        }

        .glass-card {
            background: rgba(15, 23, 42, 0.88);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 12px 32px 0 rgba(0, 0, 0, 0.45);
        }

        .glow-text {
            text-shadow: 0 0 16px rgba(56, 189, 248, 0.8);
        }

        /* Estilos para botones de acción móvil */
        .touch-action-btn {
            background: rgba(30, 41, 59, 0.9);
            backdrop-filter: blur(8px);
            border: 2px solid rgba(255, 255, 255, 0.3);
            touch-action: manipulation;
            transition: transform 0.1s, background-color 0.15s, border-color 0.15s;
        }

        .touch-action-btn:active {
            transform: scale(0.92);
            background: rgba(56, 189, 248, 0.6);
            border-color: #38bdf8;
        }

        @keyframes popIn {
            0% { transform: scale(0.85); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .animate-pop {
            animation: popIn 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        /* Estilos explícitos de capas modales */
        .modal-overlay {
            position: fixed;
            inset: 0;
            background: rgba(4, 7, 13, 0.82);
            backdrop-filter: blur(12px);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 1rem;
            transition: opacity 0.2s ease, visibility 0.2s ease;
        }

        .modal-overlay.hidden-modal {
            opacity: 0;
            visibility: hidden;
            pointer-events: none !important;
        }

        .modal-overlay:not(.hidden-modal) {
            opacity: 1;
            visibility: visible;
            pointer-events: auto !important;
        }
    </style>
</head>
<body class="text-white">

    <!-- CANVAS 3D -->
    <div id="canvas-container"></div>

    <!-- HUD INTERFAZ (TOP & CONTROLES) -->
    <div class="ui-hud flex flex-col justify-between p-4 md:p-6">
        
        <!-- ENCABEZADO Y PROGRESO DE OBJETIVO -->
        <div class="flex flex-col md:flex-row justify-between items-center w-full max-w-5xl mx-auto gap-3">
            
            <!-- Panel del Estado del Aprendizaje -->
            <div class="glass-card rounded-2xl p-4 w-full md:w-auto min-w-[300px]">
                <div class="flex items-center justify-between mb-2">
                    <span id="level-badge" class="text-xs font-black tracking-widest uppercase px-3 py-1 rounded-full bg-cyan-500/20 text-cyan-400 border border-cyan-500/30">
                        Paso 1: Rodar
                    </span>
                    <span id="gems-count" class="text-sm font-bold text-amber-300 flex items-center gap-1">
                        💎 0 / 3
                    </span>
                </div>
                <!-- Banner de Objetivo -->
                <div class="bg-cyan-950/60 border border-cyan-500/30 rounded-xl p-2.5 text-center">
                    <span class="text-[10px] text-cyan-300 font-semibold uppercase tracking-wider block mb-0.5">Misión Actual:</span>
                    <p id="objective-text" class="text-xs md:text-sm font-bold text-white">Rueda con WASD o el Joystick para recolectar las 3 orbes doradas.</p>
                </div>
            </div>

            <!-- Panel de Habilidades Unlocked y Botón Reintentar -->
            <div class="flex gap-2 items-center self-end md:self-auto">
                <div class="glass-card rounded-2xl p-2.5 flex gap-2">
                    <div id="skill-move" class="flex flex-col items-center px-3 py-1.5 rounded-xl bg-cyan-500/20 border border-cyan-400/50">
                        <span class="text-[10px] text-cyan-200 font-bold mb-0.5">Rodar</span>
                        <span class="text-xs bg-slate-900 px-2 py-0.5 rounded text-cyan-300 font-mono font-bold">WASD</span>
                    </div>
                    <div id="skill-jump" class="flex flex-col items-center px-3 py-1.5 rounded-xl bg-slate-800/40 border border-white/5 opacity-40 transition-all">
                        <span class="text-[10px] text-gray-400 font-bold mb-0.5">Saltar</span>
                        <span class="text-xs bg-slate-900/60 px-2 py-0.5 rounded text-gray-400 font-mono font-bold">Espacio</span>
                    </div>
                    <!-- CAMBIO: Refactorización visual de habilidad Dash a Sprint con barra de Estamina -->
                    <div id="skill-dash" class="flex flex-col items-center px-3 py-1.5 rounded-xl bg-slate-800/40 border border-white/5 opacity-40 transition-all relative overflow-hidden min-w-[80px]">
                        <span class="text-[10px] text-gray-400 font-bold mb-0.5">Sprint</span>
                        <span class="text-xs bg-slate-900/60 px-2 py-0.5 rounded text-gray-400 font-mono font-bold">Shift (Mantener)</span>
                        <div class="w-full bg-slate-700/60 h-1.5 rounded-full mt-1 overflow-hidden">
                            <div id="stamina-bar-hud" class="h-full bg-purple-400 w-full transition-all duration-75"></div>
                        </div>
                    </div>
                </div>

                <!-- Botón Reiniciar Checkpoint (Siempre disponible) -->
                <button id="btn-quick-respawn" title="Reintentar Checkpoint (Tecla R)" class="interactive-ui glass-card p-3 rounded-2xl hover:bg-slate-700/50 active:scale-90 transition-all border border-amber-500/40 text-amber-300 font-bold text-xs flex flex-col items-center">
                    <span class="text-lg leading-none mb-1">🔄</span>
                    <span>'R'</span>
                </button>
            </div>
        </div>

        <!-- CONTROLES TÁCTILES MÓVILES -->
        <div class="w-full max-w-5xl mx-auto flex justify-between items-end pb-2">
            <!-- Joystick Virtual -->
            <div id="touch-joystick-zone" class="interactive-ui w-28 h-28 rounded-full glass-card relative flex items-center justify-center touch-none border-2 border-white/20">
                <div id="touch-joystick-knob" class="w-10 h-10 rounded-full bg-cyan-400 shadow-lg shadow-cyan-500/50 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 pointer-events-none"></div>
            </div>

            <!-- Botones de Acción (Habilitados progresivamente) -->
            <div class="flex gap-3">
                <button id="mobile-btn-jump" class="interactive-ui touch-action-btn hidden w-16 h-16 rounded-2xl flex flex-col items-center justify-center text-xs font-black text-white shadow-xl">
                    <span class="text-lg mb-0.5">🦘</span>
                    <span>SALTAR</span>
                </button>
                <!-- CAMBIO: Botón Móvil de Sprint mantenido -->
                <button id="mobile-btn-dash" class="interactive-ui touch-action-btn hidden w-16 h-16 rounded-2xl flex flex-col items-center justify-center text-xs font-black text-white shadow-xl border-purple-400/50">
                    <span class="text-lg mb-0.5">⚡</span>
                    <span>SPRINT</span>
                </button>
            </div>
        </div>

    </div>

    <!-- MODAL PRINCIPAL DE DIÁLOGO E INSTRUCCIONES -->
    <div id="modal-container" style="z-index: 9999;" class="modal-overlay">
        <div id="instruction-box" class="interactive-ui glass-card rounded-3xl p-6 md:p-8 max-w-md w-full text-center border-2 border-cyan-400/50 shadow-2xl animate-pop">
            <div id="instruction-icon" class="text-6xl mb-3">🔮</div>
            <h3 id="instruction-title" class="text-2xl font-black mb-2 text-cyan-300 glow-text">La Bolita Aprendiz</h3>
            <p id="instruction-desc" class="text-sm md:text-base text-slate-200 leading-relaxed mb-6 font-medium">
                ¡Hola! Esta pequeña bolita quiere aprender a dominar el movimiento 3D.
                <br><br>
                <strong class="text-cyan-400">Paso 1:</strong> Usa <strong class="text-cyan-300">WASD / Flechas</strong> (o el Joystick táctil) para rodar y recolectar las <strong class="text-amber-300">3 orbes doradas</strong>.
            </p>
            <button id="btn-modal-action" class="interactive-ui px-8 py-4 bg-gradient-to-r from-cyan-400 to-blue-600 hover:from-cyan-300 hover:to-blue-500 text-slate-950 font-black text-base rounded-2xl shadow-xl shadow-cyan-500/40 active:scale-95 transition-all w-full border border-cyan-200">
                ¡Entendido! Comenzar
            </button>
        </div>
    </div>

    <!-- MODAL REINTENTO AL CAER (GAME OVER / CHECKPOINT) -->
    <div id="respawn-screen" style="z-index: 9990;" class="modal-overlay hidden-modal">
        <div class="interactive-ui glass-card p-8 rounded-3xl text-center max-w-sm border-2 border-amber-400/50 shadow-2xl animate-pop">
            <div class="text-5xl mb-3">🌌</div>
            <h3 class="text-2xl font-black text-white mb-2">¡Te has caído!</h3>
            <p class="text-slate-300 text-sm mb-6">No pasa nada, aprender requiere caerse y levantarse. Vuelve a intentarlo desde tu punto de control.</p>
            <button id="btn-respawn" class="interactive-ui px-6 py-4 bg-amber-400 hover:bg-amber-300 text-slate-950 font-black text-base rounded-2xl w-full transition-all shadow-xl shadow-amber-500/30 active:scale-95 border border-amber-200">
                🔄 Reintentar Checkpoint (Tecla 'R')
            </button>
        </div>
    </div>

    <!-- SCRIPT DE JUEGO (THREE.JS + FÍSICAS MEJORADAS + AUDIOS) -->
    <script>
        /* ==========================================
           1. SISTEMA DE AUDIO SINTÉTICO (WEB AUDIO API)
           ========================================== */
        class AudioSystem {
            constructor() {
                this.ctx = null;
            }

            init() {
                if (!this.ctx) {
                    const AudioContext = window.AudioContext || window.webkitAudioContext;
                    this.ctx = new AudioContext();
                }
                if (this.ctx.state === 'suspended') {
                    this.ctx.resume();
                }
            }

            playClick() {
                if (!this.ctx) return;
                const now = this.ctx.currentTime;
                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(600, now);
                osc.frequency.exponentialRampToValueAtTime(1200, now + 0.05);
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.05);
                osc.connect(gain);
                gain.connect(this.ctx.destination);
                osc.start(now);
                osc.stop(now + 0.05);
            }

            playCollect() {
                if (!this.ctx) return;
                const now = this.ctx.currentTime;
                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(523.25, now);
                osc.frequency.exponentialRampToValueAtTime(1046.50, now + 0.15);
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.18);
                osc.connect(gain);
                gain.connect(this.ctx.destination);
                osc.start(now);
                osc.stop(now + 0.18);
            }

            playJump() {
                if (!this.ctx) return;
                const now = this.ctx.currentTime;
                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();
                osc.type = 'triangle';
                osc.frequency.setValueAtTime(220, now);
                osc.frequency.exponentialRampToValueAtTime(580, now + 0.22);
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.22);
                osc.connect(gain);
                gain.connect(this.ctx.destination);
                osc.start(now);
                osc.stop(now + 0.22);
            }

            playDash() {
                if (!this.ctx) return;
                const now = this.ctx.currentTime;
                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(500, now);
                osc.frequency.exponentialRampToValueAtTime(120, now + 0.28);
                gain.gain.setValueAtTime(0.35, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.28);
                osc.connect(gain);
                gain.connect(this.ctx.destination);
                osc.start(now);
                osc.stop(now + 0.28);
            }

            playFall() {
                if (!this.ctx) return;
                const now = this.ctx.currentTime;
                const osc = this.ctx.createOscillator();
                const gain = this.ctx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(300, now);
                osc.frequency.exponentialRampToValueAtTime(80, now + 0.35);
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.35);
                osc.connect(gain);
                gain.connect(this.ctx.destination);
                osc.start(now);
                osc.stop(now + 0.35);
            }

            playLevelUp() {
                if (!this.ctx) return;
                const now = this.ctx.currentTime;
                const notes = [261.63, 329.63, 392.00, 523.25, 659.25];
                notes.forEach((freq, idx) => {
                    const osc = this.ctx.createOscillator();
                    const gain = this.ctx.createGain();
                    osc.type = 'sine';
                    osc.frequency.value = freq;
                    gain.gain.setValueAtTime(0.2, now + idx * 0.07);
                    gain.gain.exponentialRampToValueAtTime(0.001, now + idx * 0.07 + 0.25);
                    osc.connect(gain);
                    gain.connect(this.ctx.destination);
                    osc.start(now + idx * 0.07);
                    osc.stop(now + idx * 0.07 + 0.25);
                });
            }
        }

        const SFX = new AudioSystem();

        /* ==========================================
           2. THREE.JS ESCENARIO Y CÁMARA
           ========================================== */
        const container = document.getElementById('canvas-container');
        const scene = new THREE.Scene();
        scene.background = new THREE.Color(0x080c14);
        scene.fog = new THREE.FogExp2(0x080c14, 0.008);

        const camera = new THREE.PerspectiveCamera(60, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        container.appendChild(renderer.domElement);

        // Luces
        const ambientLight = new THREE.AmbientLight(0xddeeff, 0.7);
        scene.add(ambientLight);

        const dirLight = new THREE.DirectionalLight(0xffffff, 1.3);
        dirLight.position.set(25, 45, 25);
        dirLight.castShadow = true;
        dirLight.shadow.mapSize.width = 2048;
        dirLight.shadow.mapSize.height = 2048;
        const d = 60;
        dirLight.shadow.camera.left = -d;
        dirLight.shadow.camera.right = d;
        dirLight.shadow.camera.top = d;
        dirLight.shadow.camera.bottom = -d;
        scene.add(dirLight);

        /* ==========================================
           3. JUGADOR (BOLA NEÓN Y ESTELA DE PARTÍCULAS)
           ========================================== */
        const ballRadius = 0.8;
        const ballGeometry = new THREE.SphereGeometry(ballRadius, 32, 32);
        const ballMaterial = new THREE.MeshStandardMaterial({
            color: 0x00f0ff,
            metalness: 0.1,
            roughness: 0.15,
            emissive: 0x005588,
            emissiveIntensity: 0.6
        });

        const player = new THREE.Group();
        const ballMesh = new THREE.Mesh(ballGeometry, ballMaterial);
        ballMesh.castShadow = true;
        ballMesh.receiveShadow = true;
        player.add(ballMesh);

        // Núcleo brillante
        const coreGeo = new THREE.IcosahedronGeometry(0.38, 2);
        const coreMat = new THREE.MeshBasicMaterial({ color: 0xffffff, wireframe: true });
        const coreMesh = new THREE.Mesh(coreGeo, coreMat);
        player.add(coreMesh);

        scene.add(player);

        // Estela de Partículas MEJORADA
        const trailParticles = [];
        const trailGeo = new THREE.SphereGeometry(0.15, 8, 8);
        const trailMatNormal = new THREE.MeshBasicMaterial({ color: 0x38bdf8, transparent: true, opacity: 0.8 });
        const trailMatSprint = new THREE.MeshBasicMaterial({ color: 0xc084fc, transparent: true, opacity: 0.9 });

        function createTrailParticle(isSprinting = false) {
            if (physics.velocity.lengthSq() < 1) return;
            const mat = isSprinting ? trailMatSprint.clone() : trailMatNormal.clone();
            const p = new THREE.Mesh(trailGeo, mat);
            p.position.copy(player.position);
            p.position.y -= 0.2;
            
            if (isSprinting) {
                p.scale.setScalar(1.4);
            }
            
            scene.add(p);
            trailParticles.push({ mesh: p, life: 1.0, isSprint: isSprinting });
        }

        function updateTrail(delta) {
            for (let i = trailParticles.length - 1; i >= 0; i--) {
                const pt = trailParticles[i];
                const decay = pt.isSprint ? 4.5 : 3.0;
                pt.life -= delta * decay;
                pt.mesh.scale.multiplyScalar(0.91);
                pt.mesh.material.opacity = Math.max(0, pt.life);
                if (pt.life <= 0) {
                    scene.remove(pt.mesh);
                    trailParticles.splice(i, 1);
                }
            }
        }

        /* ==========================================
           4. FÍSICAS Y SISTEMA DE SPRINT / ESTAMINA
           ========================================== */
        const physics = {
            position: new THREE.Vector3(0, ballRadius + 1, 0),
            velocity: new THREE.Vector3(0, 0, 0),
            radius: ballRadius,
            isGrounded: false,
            // Velocidades normal y sprint (Súper Sprint incrementado)
            baseSpeed: 38,
            sprintSpeed: 115,
            jumpForce: 16.5,
            friction: 0.88,
            gravity: -34,
            canJump: false,
            canDash: false, // Usado para habilidad Sprint
            // Sistema de Estamina
            stamina: 100,
            maxStamina: 100,
            staminaDrainRate: 30, // Se agota en ~3.3s
            staminaRegenRate: 25, // Se regenera en 4s
            isExhausted: false,
            isSprinting: false,
            sprintRequested: false, // Variable de control de presión activa
            checkpoint: new THREE.Vector3(0, ballRadius + 1, 0)
        };

        player.position.copy(physics.position);

        /* ==========================================
           5. ESCENARIO Y PLATAFORMAS (AJUSTADAS DE FORMA ALCANZABLE)
           ========================================== */
        const platforms = [];
        const collectibles = [];
        const movingPlatforms = [];

        const matFloor = new THREE.MeshStandardMaterial({ color: 0x1e293b, roughness: 0.35 });
        const matAccent = new THREE.MeshStandardMaterial({ color: 0x0ea5e9, roughness: 0.2 });
        const matGold = new THREE.MeshStandardMaterial({ color: 0xf59e0b, emissive: 0xd97706, emissiveIntensity: 0.9 });

        function createPlatform(x, y, z, width, height, depth, material = matFloor) {
            const geo = new THREE.BoxGeometry(width, height, depth);
            const mesh = new THREE.Mesh(geo, material);
            mesh.position.set(x, y, z);
            mesh.receiveShadow = true;
            mesh.castShadow = true;
            scene.add(mesh);

            const box = new THREE.Box3().setFromObject(mesh);
            const pObj = { mesh, box };
            platforms.push(pObj);
            return pObj;
        }

        function createGem(x, y, z, level) {
            const geo = new THREE.OctahedronGeometry(0.55, 0);
            const mesh = new THREE.Mesh(geo, matGold);
            mesh.position.set(x, y, z);
            mesh.castShadow = true;

            const light = new THREE.PointLight(0xf59e0b, 1.2, 5);
            mesh.add(light);

            scene.add(mesh);
            collectibles.push({ mesh, level, active: true, baseY: y, isStar: false });
        }

        function createMasterStar(x, y, z) {
            const geo = new THREE.IcosahedronGeometry(0.9, 0);
            const mat = new THREE.MeshStandardMaterial({ color: 0xfacc15, emissive: 0xeab308, emissiveIntensity: 1.2 });
            const mesh = new THREE.Mesh(geo, mat);
            mesh.position.set(x, y, z);
            scene.add(mesh);

            collectibles.push({ mesh, level: 3, active: true, baseY: y, isStar: true });
        }

        // --- DISEÑO DEL ESCENARIO ---
        // PASO 1: Plataforma Inicial (Aprender a Rodar)
        createPlatform(0, -0.5, 0, 22, 1, 22);
        createGem(0, 1.2, -6, 1);
        createGem(-6, 1.2, 0, 1);
        createGem(6, 1.2, 0, 1);

        // PASO 2: Plataforma de Salto (Abismo pequeño perfectamente alcanzable)
        createPlatform(0, -0.5, -24, 18, 1, 16);
        // Obstáculo para saltar encima
        createPlatform(0, 0.8, -20, 14, 1.2, 1, matAccent);
        createGem(0, 3.2, -20, 2);
        
        // Plataformas escalonadas
        createPlatform(-4, 2.0, -27, 6, 1, 6, matAccent);
        createGem(-4, 3.8, -27, 2);

        createPlatform(4, 3.5, -31, 6, 1, 6, matAccent);
        createGem(4, 5.2, -31, 2);

        // PASO 3: Plataforma de Dash (Abismo Grande)
        createPlatform(0, 4.0, -48, 14, 1, 14);
        
        // Gap largo alcanzable con DASH (Shift)
        createPlatform(0, 4.0, -78, 12, 1, 12, matAccent);
        
        // Plataforma móvil
        const pMov = createPlatform(0, 4.0, -98, 10, 1, 10, matAccent);
        movingPlatforms.push({ obj: pMov, startZ: -98, endZ: -114, speed: 6, dir: 1 });

        // Meta Final
        createPlatform(0, 4.0, -135, 18, 1, 18, matAccent);
        createMasterStar(0, 6.2, -135);

        /* ==========================================
           6. PROGRESIÓN DE JUEGO Y MODALES
           ========================================== */
        const gameProgression = {
            currentLevel: 1,
            gemsCollectedInLevel: 0,
            requiredGemsPerLevel: { 1: 3, 2: 3, 3: 1 },
            isPausedForModal: true
        };

        const uiElements = {
            badge: document.getElementById('level-badge'),
            gemsCount: document.getElementById('gems-count'),
            objectiveText: document.getElementById('objective-text'),
            skillJump: document.getElementById('skill-jump'),
            skillDash: document.getElementById('skill-dash'),
            btnJumpMobile: document.getElementById('mobile-btn-jump'),
            btnDashMobile: document.getElementById('mobile-btn-dash'),
            modalContainer: document.getElementById('modal-container'),
            instructionIcon: document.getElementById('instruction-icon'),
            instructionTitle: document.getElementById('instruction-title'),
            instructionDesc: document.getElementById('instruction-desc'),
            btnModalAction: document.getElementById('btn-modal-action'),
            respawnScreen: document.getElementById('respawn-screen'),
            btnRespawn: document.getElementById('btn-respawn'),
            btnQuickRespawn: document.getElementById('btn-quick-respawn'),
            staminaBarHud: document.getElementById('stamina-bar-hud')
        };

        function closeAllModals() {
            uiElements.modalContainer.classList.add('hidden-modal');
            uiElements.respawnScreen.classList.add('hidden-modal');
            gameProgression.isPausedForModal = false;
        }

        function handleModalAction() {
            SFX.init();
            SFX.playClick();
            closeAllModals();

            if (gameProgression.currentLevel === 2) {
                physics.checkpoint.set(0, 1.5, -18);
            } else if (gameProgression.currentLevel === 3) {
                physics.checkpoint.set(0, 5.5, -48);
            }
        }

        uiElements.btnModalAction.addEventListener('click', handleModalAction);
        uiElements.btnModalAction.addEventListener('touchend', (e) => {
            e.preventDefault();
            handleModalAction();
        });

        function showStepModal(icon, title, descHTML, buttonText = "¡Entendido! Continuar") {
            gameProgression.isPausedForModal = true;
            uiElements.instructionIcon.textContent = icon;
            uiElements.instructionTitle.textContent = title;
            uiElements.instructionDesc.innerHTML = descHTML;
            uiElements.btnModalAction.textContent = buttonText;
            uiElements.modalContainer.classList.remove('hidden-modal');
        }

        function updateHUD() {
            const req = gameProgression.requiredGemsPerLevel[gameProgression.currentLevel];
            uiElements.gemsCount.textContent = `💎 ${gameProgression.gemsCollectedInLevel} / ${req}`;
        }

        function unlockJumpPhase() {
            gameProgression.currentLevel = 2;
            gameProgression.gemsCollectedInLevel = 0;
            physics.canJump = true;

            uiElements.badge.textContent = "Paso 2: Saltar";
            uiElements.badge.className = "text-xs font-black tracking-widest uppercase px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 border border-emerald-500/30";
            uiElements.objectiveText.textContent = "Usa SALTAR (Espacio / Botón) para superar obstáculos y juntar 3 orbes elevadas.";

            uiElements.skillJump.classList.remove('opacity-40', 'bg-slate-800/40');
            uiElements.skillJump.classList.add('bg-emerald-500/20', 'border-emerald-400/50');
            uiElements.skillJump.querySelector('span').classList.replace('text-gray-400', 'text-emerald-300');
            uiElements.btnJumpMobile.classList.remove('hidden');

            updateHUD();
            SFX.playLevelUp();

            showStepModal(
                "🦘",
                "¡Habilidad Unlocked: SALTO!",
                "¡Dominas el arte de rodar!<br><br>Ahora se ha activado la capacidad de <strong class='text-emerald-400'>SALTAR</strong>.<br>Presiona <strong class='text-emerald-300'>ESPACIO</strong> o usa el botón táctil <strong class='text-emerald-300'>SALTAR</strong>."
            );
        }

        function unlockDashPhase() {
            gameProgression.currentLevel = 3;
            gameProgression.gemsCollectedInLevel = 0;
            physics.canDash = true;

            uiElements.badge.textContent = "Paso 3: Sprint Continuo";
            uiElements.badge.className = "text-xs font-black tracking-widest uppercase px-3 py-1 rounded-full bg-purple-500/20 text-purple-400 border border-purple-500/30";
            uiElements.objectiveText.textContent = "MANTÉN Shift o SPRINT para correr rápido a través del gran abismo.";

            uiElements.skillDash.classList.remove('opacity-40', 'bg-slate-800/40');
            uiElements.skillDash.classList.add('bg-purple-500/20', 'border-purple-400/50');
            uiElements.skillDash.querySelector('span').classList.replace('text-gray-400', 'text-purple-300');
            uiElements.btnDashMobile.classList.remove('hidden');

            updateHUD();
            SFX.playLevelUp();

            showStepModal(
                "⚡",
                "¡Habilidad Unlocked: SPRINT CONTINUO!",
                "¡Increíbles saltos!<br><br>Has desbloqueado la capacidad de <strong class='text-purple-400'>SPRINT CONTINUO</strong>.<br><strong class='text-purple-300'>MANTÉN PRESIONADO SHIFT</strong> o el botón táctil <strong class='text-purple-300'>SPRINT</strong> para correr a máxima velocidad mientras consumes Estamina."
            );
        }

        /* ==========================================
           7. SISTEMA DE REINICIO Y CHECKPOINTS
           ========================================== */
        function triggerRespawnModal() {
            if (gameProgression.isPausedForModal) return;
            gameProgression.isPausedForModal = true;
            SFX.playFall();
            uiElements.respawnScreen.classList.remove('hidden-modal');
        }

        function executeRespawn() {
            closeAllModals();
            physics.position.copy(physics.checkpoint);
            physics.velocity.set(0, 0, 0);
            physics.stamina = physics.maxStamina;
            physics.isExhausted = false;
            physics.isSprinting = false;
            player.position.copy(physics.position);
        }

        uiElements.btnRespawn.addEventListener('click', executeRespawn);
        uiElements.btnRespawn.addEventListener('touchend', (e) => {
            e.preventDefault();
            executeRespawn();
        });

        uiElements.btnQuickRespawn.addEventListener('click', executeRespawn);
        uiElements.btnQuickRespawn.addEventListener('touchend', (e) => {
            e.preventDefault();
            executeRespawn();
        });

        /* ==========================================
           8. CONTROLES DE ENTRADA (MANTENER PRESIONADO SPRINT)
           ========================================== */
        const keys = { forward: false, backward: false, left: false, right: false, shift: false };

        window.addEventListener('keydown', (e) => {
            SFX.init();

            if (e.code === 'KeyR') {
                executeRespawn();
                return;
            }

            if (gameProgression.isPausedForModal) return;

            switch (e.code) {
                case 'KeyW': case 'ArrowUp': keys.forward = true; break;
                case 'KeyS': case 'ArrowDown': keys.backward = true; break;
                case 'KeyA': case 'ArrowLeft': keys.left = true; break;
                case 'KeyD': case 'ArrowRight': keys.right = true; break;
                case 'Space':
                    if (physics.canJump && physics.isGrounded) performJump();
                    break;
                case 'ShiftLeft': case 'ShiftRight':
                    keys.shift = true;
                    physics.sprintRequested = true;
                    break;
            }
        });

        window.addEventListener('keyup', (e) => {
            switch (e.code) {
                case 'KeyW': case 'ArrowUp': keys.forward = false; break;
                case 'KeyS': case 'ArrowDown': keys.backward = false; break;
                case 'KeyA': case 'ArrowLeft': keys.left = false; break;
                case 'KeyD': case 'ArrowRight': keys.right = false; break;
                case 'ShiftLeft': case 'ShiftRight':
                    keys.shift = false;
                    physics.sprintRequested = false;
                    break;
            }
        });

        // Joystick Táctil
        const joystickZone = document.getElementById('touch-joystick-zone');
        const joystickKnob = document.getElementById('touch-joystick-knob');
        let joystickActive = false;
        let joystickTouchId = null;
        const joystickOrigin = { x: 0, y: 0 };

        joystickZone.addEventListener('touchstart', (e) => {
            SFX.init();
            if (gameProgression.isPausedForModal) return;

            const touch = e.changedTouches[0];
            joystickActive = true;
            joystickTouchId = touch.identifier;
            const rect = joystickZone.getBoundingClientRect();
            joystickOrigin.x = rect.left + rect.width / 2;
            joystickOrigin.y = rect.top + rect.height / 2;
        }, { passive: true });

        window.addEventListener('touchmove', (e) => {
            if (!joystickActive || gameProgression.isPausedForModal) return;
            for (let i = 0; i < e.changedTouches.length; i++) {
                if (e.changedTouches[i].identifier === joystickTouchId) {
                    const touch = e.changedTouches[i];
                    const dx = touch.clientX - joystickOrigin.x;
                    const dy = touch.clientY - joystickOrigin.y;
                    const dist = Math.min(Math.hypot(dx, dy), 35);
                    const angle = Math.atan2(dy, dx);

                    const knobX = Math.cos(angle) * dist;
                    const knobY = Math.sin(angle) * dist;

                    joystickKnob.style.transform = `translate(calc(-50% + ${knobX}px), calc(-50% + ${knobY}px))`;

                    keys.left = dx < -10;
                    keys.right = dx > 10;
                    keys.forward = dy < -10;
                    keys.backward = dy > 10;
                }
            }
        }, { passive: true });

        const resetJoystick = () => {
            joystickActive = false;
            joystickTouchId = null;
            joystickKnob.style.transform = `translate(-50%, -50%)`;
            keys.forward = keys.backward = keys.left = keys.right = false;
        };

        window.addEventListener('touchend', resetJoystick);
        window.addEventListener('touchcancel', resetJoystick);

        // Botón Salto Móvil
        function triggerMobileJump(e) {
            e.preventDefault();
            SFX.init();
            if (!gameProgression.isPausedForModal && physics.canJump && physics.isGrounded) {
                performJump();
            }
        }
        uiElements.btnJumpMobile.addEventListener('touchstart', triggerMobileJump);
        uiElements.btnJumpMobile.addEventListener('click', triggerMobileJump);

        // Botón Sprint Móvil (Mantenimiento continuo con pointerdown/up)
        const startSprintHold = (e) => {
            if (e) e.preventDefault();
            SFX.init();
            if (!gameProgression.isPausedForModal && physics.canDash) {
                physics.sprintRequested = true;
            }
        };

        const stopSprintHold = (e) => {
            if (e) e.preventDefault();
            physics.sprintRequested = false;
        };

        uiElements.btnDashMobile.addEventListener('pointerdown', startSprintHold);
        uiElements.btnDashMobile.addEventListener('pointerup', stopSprintHold);
        uiElements.btnDashMobile.addEventListener('pointercancel', stopSprintHold);
        uiElements.btnDashMobile.addEventListener('mouseleave', stopSprintHold);

        /* ==========================================
           9. MOVIMIENTO, SPRINT Y LÓGICA DE FÍSICAS
           ========================================== */
        function performJump() {
            physics.velocity.y = physics.jumpForce;
            physics.isGrounded = false;
            SFX.playJump();
        }

        function updatePhysics(delta) {
            if (gameProgression.isPausedForModal) return;

            // Lógica de Sprint y Estamina continua
            const isMoving = keys.forward || keys.backward || keys.left || keys.right;
            const canSprintNow = physics.canDash && physics.sprintRequested && isMoving && !physics.isExhausted;

            if (canSprintNow) {
                physics.isSprinting = true;
                physics.stamina = Math.max(0, physics.stamina - physics.staminaDrainRate * delta);
                
                if (physics.stamina <= 0) {
                    physics.isExhausted = true;
                    physics.isSprinting = false;
                }
            } else {
                physics.isSprinting = false;
                // Regenerar Estamina
                if (physics.stamina < physics.maxStamina) {
                    physics.stamina = Math.min(physics.maxStamina, physics.stamina + physics.staminaRegenRate * delta);
                    if (physics.isExhausted && physics.stamina >= 25) { // Requiere 25% para salir de agotamiento
                        physics.isExhausted = false;
                    }
                }
            }

            // Actualizar barra de Estamina UI
            const staminaPct = (physics.stamina / physics.maxStamina) * 100;
            uiElements.staminaBarHud.style.width = `${staminaPct}%`;
            if (physics.isExhausted) {
                uiElements.staminaBarHud.className = "h-full bg-red-500 w-full transition-all duration-75 animate-pulse";
            } else if (physics.isSprinting) {
                uiElements.staminaBarHud.className = "h-full bg-purple-400 w-full transition-all duration-75 shadow-lg shadow-purple-500/80";
            } else {
                uiElements.staminaBarHud.className = "h-full bg-cyan-400 w-full transition-all duration-75";
            }

            // Gravedad
            physics.velocity.y += physics.gravity * delta;

            // Movimiento & Velocidad según Sprint
            const moveDir = new THREE.Vector3();
            if (keys.forward) moveDir.z -= 1;
            if (keys.backward) moveDir.z += 1;
            if (keys.left) moveDir.x -= 1;
            if (keys.right) moveDir.x += 1;

            moveDir.normalize();

            const currentSpeed = physics.isSprinting ? physics.sprintSpeed : physics.baseSpeed;
            // Mayor aceleración al hacer sprint para respuesta inmediata
            const accelMultiplier = physics.isSprinting ? 1.8 : 1.0;
            const accel = currentSpeed * accelMultiplier * delta;

            physics.velocity.x += moveDir.x * accel;
            physics.velocity.z += moveDir.z * accel;

            physics.velocity.x *= physics.friction;
            physics.velocity.z *= physics.friction;

            const nextPos = physics.position.clone().addScaledVector(physics.velocity, delta);

            // Colisiones con plataformas
            physics.isGrounded = false;

            for (let p of platforms) {
                const box = p.box;
                const closestPoint = new THREE.Vector3(
                    Math.max(box.min.x, Math.min(nextPos.x, box.max.x)),
                    Math.max(box.min.y, Math.min(nextPos.y, box.max.y)),
                    Math.max(box.min.z, Math.min(nextPos.z, box.max.z))
                );

                const distance = nextPos.distanceTo(closestPoint);

                if (distance < physics.radius) {
                    const normal = nextPos.clone().sub(closestPoint).normalize();

                    if (isNaN(normal.x) || distance === 0) normal.set(0, 1, 0);

                    if (normal.y > 0.4) {
                        physics.isGrounded = true;
                        physics.velocity.y = 0;
                        nextPos.y = closestPoint.y + physics.radius;
                    } else {
                        const overlap = physics.radius - distance;
                        nextPos.addScaledVector(normal, overlap);
                        if (normal.y < -0.4) physics.velocity.y = 0;
                    }
                }
            }

            physics.position.copy(nextPos);
            player.position.copy(physics.position);

            // Rotación visual e intensidad de partículas
            const distMoved = new THREE.Vector3(physics.velocity.x, 0, physics.velocity.z).length() * delta;
            if (distMoved > 0.001) {
                const rotAxis = new THREE.Vector3(-physics.velocity.z, 0, physics.velocity.x).normalize();
                const speedMultiplier = physics.isSprinting ? 2.5 : 1.0;
                ballMesh.rotateOnWorldAxis(rotAxis, (distMoved / physics.radius) * speedMultiplier);
                createTrailParticle(physics.isSprinting);
                if (physics.isSprinting) {
                    createTrailParticle(true); // Partícula extra para mayor densidad de estela
                }
            }

            coreMesh.rotation.x += delta * (physics.isSprinting ? 8.0 : 1.5);
            coreMesh.rotation.y += delta * (physics.isSprinting ? 10.0 : 2.0);

            // Caída al vacío
            if (physics.position.y < -12) {
                triggerRespawnModal();
            }
        }

        /* ==========================================
           10. COLECCIONABLES Y PLATAFORMAS MÓVILES
           ========================================== */
        function updateCollectibles(time) {
            collectibles.forEach(gem => {
                if (!gem.active) return;

                // Animación de flotación y rotación
                gem.mesh.rotation.y += 0.02;
                gem.mesh.position.y = gem.baseY + Math.sin(time * 3 + gem.mesh.position.x) * 0.25;

                // Colisión con jugador
                if (player.position.distanceTo(gem.mesh.position) < (physics.radius + 0.6)) {
                    gem.active = false;
                    scene.remove(gem.mesh);
                    SFX.playCollect();

                    gameProgression.gemsCollectedInLevel++;
                    updateHUD();

                    const req = gameProgression.requiredGemsPerLevel[gameProgression.currentLevel];
                    if (gameProgression.gemsCollectedInLevel >= req) {
                        if (gameProgression.currentLevel === 1) {
                            unlockJumpPhase();
                        } else if (gameProgression.currentLevel === 2) {
                            unlockDashPhase();
                        } else if (gameProgression.currentLevel === 3) {
                            showStepModal(
                                "🏆",
                                "¡VICTORIA TOTAL!",
                                "¡Has completado todo el entrenamiento de movimiento 3D!<br><br>Ahora dominas la aceleración, los saltos calculados y el sprint continuo con estamina.",
                                "¡Volver a Jugar!"
                            );
                            gameProgression.currentLevel = 1;
                            gameProgression.gemsCollectedInLevel = 0;
                            physics.canJump = false;
                            physics.canDash = false;
                            physics.checkpoint.set(0, ballRadius + 1, 0);
                            location.reload();
                        }
                    }
                }
            });
        }

        function updateMovingPlatforms(delta) {
            movingPlatforms.forEach(p => {
                p.obj.mesh.position.z += p.speed * p.dir * delta;
                p.obj.box.setFromObject(p.obj.mesh);

                if (p.obj.mesh.position.z <= p.endZ) {
                    p.dir = 1;
                } else if (p.obj.mesh.position.z >= p.startZ) {
                    p.dir = -1;
                }
            });
        }

        /* ==========================================
           11. CÁMARA DINÁMICA CON EFECTO FOV DE VELOCIDAD
           ========================================== */
        const cameraOffset = new THREE.Vector3(0, 5.5, 11);
        const cameraTarget = new THREE.Vector3();

        function updateCamera(delta) {
            const desiredPos = player.position.clone().add(cameraOffset);
            camera.position.lerp(desiredPos, delta * 5.0);

            cameraTarget.copy(player.position).add(new THREE.Vector3(0, 0.5, 0));
            camera.lookAt(cameraTarget);

            // Transición de FOV más dramática al hacer Súper Sprint
            const targetFOV = physics.isSprinting ? 85 : 60;
            camera.fov = THREE.MathUtils.lerp(camera.fov, targetFOV, delta * 8.0);
            camera.updateProjectionMatrix();
        }

        let lastTime = performance.now();

        function animate() {
            requestAnimationFrame(animate);

            const now = performance.now();
            const delta = Math.min((now - lastTime) / 1000, 0.1);
            lastTime = now;

            updatePhysics(delta);
            updateTrail(delta);
            updateCollectibles(now / 1000);
            updateMovingPlatforms(delta);
            updateCamera(delta);

            renderer.render(scene, camera);
        }

        window.onload = function () {
            animate();
        };

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });
    </script>
</body>
</html>