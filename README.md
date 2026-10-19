
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Traje de Assalto Bio-SAMS - Exo-Chassi Quântico</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        suit: {
                            bg: '#02060e',
                            panel: 'rgba(6, 16, 29, 0.90)',
                            cyan: '#00f3ff',
                            emerald: '#10b981',
                            amber: '#f59e0b',
                            purple: '#a855f7',
                            danger: '#ef4444',
                            border: 'rgba(0, 243, 255, 0.22)'
                        }
                    },
                    fontFamily: {
                        mono: ['Consolas', 'Courier New', 'monospace'],
                        sans: ['Inter', 'Segoe UI', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style>
        ::-webkit-scrollbar { width: 5px; height: 5px; }
        ::-webkit-scrollbar-track { background: rgba(2, 6, 14, 0.95); }
        ::-webkit-scrollbar-thumb { background: rgba(0, 243, 255, 0.3); border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: rgba(0, 243, 255, 0.7); }

        .neon-glow-cyan { text-shadow: 0 0 10px rgba(0, 243, 255, 0.6); }
        .neon-glow-emerald { text-shadow: 0 0 10px rgba(16, 185, 129, 0.6); }
        .neon-glow-danger { text-shadow: 0 0 12px rgba(239, 68, 68, 0.8); }

        .glass-panel {
            background: rgba(6, 16, 29, 0.88);
            backdrop-filter: blur(14px);
            border: 1px solid rgba(0, 243, 255, 0.22);
        }
        canvas { touch-action: none; }
    </style>
</head>
<body class="bg-[#02060e] text-gray-200 font-sans h-screen flex flex-col overflow-hidden select-none">

    <!-- Header Bar -->
    <header class="h-14 border-b border-suit-border bg-suit-bg flex items-center justify-between px-4 z-20 shrink-0">
        <div class="flex items-center gap-3">
            <div id="status-beacon" class="w-3.5 h-3.5 rounded-full bg-suit-cyan animate-pulse shadow-[0_0_12px_#00f3ff]"></div>
            <h1 class="font-bold text-sm sm:text-base tracking-wider text-suit-cyan neon-glow-cyan uppercase">
                EXO-CHASSI BIO-SAMS <span class="text-xs text-suit-purple font-mono font-normal">| ARMADURA DE COMBATE & BLINDAGEM MÉTICA</span>
            </h1>
        </div>
        <div class="flex items-center gap-3 text-xs font-mono">
            <div class="hidden sm:flex items-center gap-2 bg-black/70 px-3 py-1 rounded border border-suit-border">
                <span class="text-gray-400">FLUIDO SAMS:</span>
                <span id="hdr-fluid-state" class="text-suit-emerald font-bold">VISCOSO / FLEXÍVEL</span>
            </div>
            <div class="hidden md:flex items-center gap-2 bg-black/70 px-3 py-1 rounded border border-suit-border">
                <span class="text-gray-400">BOLHA MÉTRICA:</span>
                <span id="hdr-bubble-status" class="text-suit-cyan font-bold">100% ISOLADA</span>
            </div>
            <button id="btn-manual" class="bg-suit-cyan/20 hover:bg-suit-cyan/40 text-suit-cyan border border-suit-cyan px-3 py-1 rounded transition text-xs font-bold">
                Manual Militar
            </button>
        </div>
    </header>

    <!-- Main Content Workspace -->
    <div class="flex-1 grid grid-cols-1 lg:grid-cols-12 overflow-hidden relative">

        <!-- Controls Sidebar -->
        <aside class="lg:col-span-3 glass-panel p-4 flex flex-col gap-3 overflow-y-auto z-10 max-h-[42vh] lg:max-h-full border-r border-suit-border">
            
            <!-- System Operation Modes -->
            <div class="space-y-1.5">
                <label class="text-[10px] font-mono uppercase text-gray-400 tracking-wider">Modos Operacionais da Armadura</label>
                <div class="grid grid-cols-1 gap-1.5 font-mono text-xs">
                    <button id="btn-mode-fluid" onclick="setMode('FLUID')" class="w-full text-left p-2 rounded border border-suit-cyan bg-suit-cyan/20 text-suit-cyan font-bold transition flex items-center justify-between">
                        <span>1. Camada Fluida Inteligente</span>
                        <span class="text-[10px] bg-suit-emerald/30 px-1.5 py-0.5 rounded text-suit-emerald">NANOSEGUNDOS</span>
                    </button>
                    <button id="btn-mode-mjolnir" onclick="setMode('MJOLNIR')" class="w-full text-left p-2 rounded border border-suit-border bg-black/40 text-gray-400 hover:text-suit-amber transition flex items-center justify-between">
                        <span>2. Operação Mjolnir (Massa Extrema)</span>
                        <span class="text-[10px] bg-suit-amber/30 px-1.5 py-0.5 rounded text-suit-amber">ENERGIA NEGATIVA</span>
                    </button>
                    <button id="btn-mode-boom" onclick="setMode('BOOM_BUBBLE')" class="w-full text-left p-2 rounded border border-suit-border bg-black/40 text-gray-400 hover:text-suit-purple transition flex items-center justify-between">
                        <span>3. Bolha Isolante do Boom Tube</span>
                        <span class="text-[10px] bg-suit-purple/30 px-1.5 py-0.5 rounded text-suit-purple">ISOLAMENTO BAROMÉTRICO</span>
                    </button>
                </div>
            </div>

            <!-- Kinetic Impact Trigger Button -->
            <button id="btn-impact" onclick="triggerKineticImpact()" class="w-full bg-gradient-to-r from-suit-cyan via-suit-emerald to-suit-amber hover:opacity-90 text-black font-black text-xs p-3 rounded shadow-lg shadow-suit-cyan/20 transition transform active:scale-95 flex flex-col items-center justify-center gap-0.5 border border-white/40 tracking-wider uppercase">
                <span class="text-sm">💥 SIMULAR IMPACTO BALÍSTICO / ONDA DE CHOQUE</span>
                <span class="text-[9.5px] font-mono font-semibold text-black/80">INDUZIR CAMPO MAGNÉTICO DE RIGIDEZ SROS</span>
            </button>

            <!-- Metric Compensation Slider -->
            <div class="space-y-2 bg-black/50 p-3 rounded border border-suit-border font-mono text-xs">
                <div class="flex justify-between items-center">
                    <span class="text-gray-300 font-bold">Compensação Métrico-Articular:</span>
                    <span id="val-compensation" class="text-suit-cyan font-bold">100.0%</span>
                </div>
                <input type="range" id="slider-compensation" min="0" max="100" value="100" class="w-full accent-suit-cyan bg-gray-800 rounded h-1.5 cursor-pointer">
                <div class="text-[10px] text-gray-400 flex justify-between">
                    <span class="text-suit-danger font-bold">0% (Ruptura Espinhal)</span>
                    <span class="text-suit-emerald">100% (Anulada)</span>
                </div>
            </div>

            <!-- Event Log Console -->
            <div class="flex-1 flex flex-col min-h-[110px] bg-black/90 rounded border border-suit-border/70 p-2 font-mono text-[11px] overflow-hidden">
                <div class="text-gray-500 border-b border-gray-800 pb-1 mb-1 flex justify-between">
                    <span>> REGISTRO DE EVENTOS DA ARMADURA</span>
                    <span id="log-clock" class="text-suit-cyan">00:00:00</span>
                </div>
                <div id="log-console" class="flex-1 overflow-y-auto space-y-1 text-gray-300 pr-1">
                    <p class="text-suit-cyan">[SROS] Exo-chassi em monitoramento de varredura pré-colisão.</p>
                    <p class="text-suit-emerald">[BIO-SAMS] Fluido em estado viscoelástico basal ativado.</p>
                </div>
            </div>

        </aside>

        <!-- Center 2D Canvas Interactive Area -->
        <main class="lg:col-span-6 relative flex flex-col items-center justify-center bg-black overflow-hidden">
            
            <canvas id="suitCanvas" class="w-full h-full cursor-crosshair"></canvas>

            <!-- Dynamic HUD Title Banner -->
            <div class="absolute top-4 left-4 pointer-events-none font-mono text-xs space-y-1 bg-black/80 p-3 rounded border border-suit-border backdrop-blur-md z-10">
                <div class="text-suit-cyan font-bold flex items-center gap-2">
                    <span id="hud-status-dot" class="inline-block w-2.5 h-2.5 rounded-full bg-suit-cyan animate-ping"></span>
                    <span id="hud-mode-title">MODO 1: CAMADA FLUIDA INTELIGENTE</span>
                </div>
                <div class="text-gray-400 text-[11px]" id="hud-mode-sub">SROS monitorando vetores cinéticos e térmicos de entrada</div>
                <div class="text-suit-emerald text-[11px]">Rigidez do Fluido: <span id="hud-hardness-val" class="text-white">12.5 GPa (Ultra-Denso)</span></div>
            </div>

            <!-- Impact Alert HUD Banner -->
            <div id="hud-impact-banner" class="hidden absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 pointer-events-none text-center z-20">
                <h2 class="text-4xl sm:text-6xl font-black text-transparent bg-clip-text bg-gradient-to-r from-suit-cyan via-white to-suit-emerald neon-glow-emerald tracking-widest uppercase animate-bounce">
                    IMPACTO DISSIPADO!
                </h2>
                <div class="text-xs font-mono text-suit-emerald font-bold tracking-widest mt-2 bg-black/90 px-4 py-1.5 rounded border border-suit-emerald inline-block">
                    CRISTALIZAÇÃO MOLECULAR SROS EM NANOSEGUNDOS
                </div>
            </div>

        </main>

        <!-- Telemetry & Soldier Health Sidebar -->
        <aside class="lg:col-span-3 glass-panel p-4 flex flex-col gap-3.5 overflow-y-auto z-10 max-h-[42vh] lg:max-h-full border-l border-suit-border">
            
            <h2 class="text-xs font-mono uppercase text-suit-cyan tracking-wider flex items-center gap-1 border-b border-suit-border/40 pb-2 font-bold">
                <span>🛡️</span> Telemetria Biomecânica do Operador
            </h2>

            <!-- Metric Cards -->
            <div class="grid grid-cols-2 gap-2 text-xs font-mono">
                <div class="bg-black/70 p-2 rounded border border-suit-cyan/40">
                    <span class="text-gray-400 block text-[10px]">PRESSÃO INTERNA</span>
                    <span id="tele-pressure" class="text-suit-cyan text-sm font-bold">1.00 ATM</span>
                </div>
                <div class="bg-black/70 p-2 rounded border border-suit-emerald/40">
                    <span class="text-gray-400 block text-[10px]">RIGIDEZ SAMS</span>
                    <span id="tele-rigidity" class="text-suit-emerald text-sm font-bold">0.05 GPa</span>
                </div>
                <div class="bg-black/70 p-2 rounded border border-suit-amber/40">
                    <span class="text-gray-400 block text-[10px]">ENERGIA NEGATIVA</span>
                    <span id="tele-neg-energy" class="text-suit-amber text-sm font-bold">0.00 TeV</span>
                </div>
                <div class="bg-black/70 p-2 rounded border border-suit-purple/40">
                    <span class="text-gray-400 block text-[10px]">ESTRESSE ESPINHAL</span>
                    <span id="tele-spinal-stress" class="text-suit-purple text-sm font-bold">0.0%</span>
                </div>
            </div>

            <!-- Progress Bars for Mechanical Stress -->
            <div class="bg-black/70 p-3 rounded border border-suit-border space-y-2.5 font-mono text-xs">
                <div>
                    <div class="flex justify-between text-[11px] mb-1">
                        <span class="text-suit-emerald font-bold">INTEGRIDADE DA BOLHA MÉTRICA</span>
                        <span id="tele-bubble-pct" class="text-suit-emerald">100.0%</span>
                    </div>
                    <div class="w-full bg-gray-900 h-2 rounded overflow-hidden p-0.5 border border-gray-800">
                        <div id="bar-bubble" class="bg-gradient-to-r from-blue-500 to-suit-emerald h-full w-[100%] transition-all duration-300"></div>
                    </div>
                </div>

                <div>
                    <div class="flex justify-between text-[11px] mb-1">
                        <span class="text-suit-amber font-bold">DISSIPAÇÃO KINÉTICA DE IMPACTO</span>
                        <span id="tele-dissipation-pct" class="text-suit-amber">99.8%</span>
                    </div>
                    <div class="w-full bg-gray-900 h-2 rounded overflow-hidden p-0.5 border border-gray-800">
                        <div id="bar-dissipation" class="bg-gradient-to-r from-yellow-500 to-suit-amber h-full w-[99.8%] transition-all duration-300"></div>
                    </div>
                </div>

                <div>
                    <div class="flex justify-between text-[11px] mb-1">
                        <span class="text-suit-danger font-bold">RISCO DE FRATURA OSSEA (CARGA)</span>
                        <span id="tele-fracture-pct" class="text-suit-danger">0.0%</span>
                    </div>
                    <div class="w-full bg-gray-900 h-2 rounded overflow-hidden p-0.5 border border-gray-800">
                        <div id="bar-fracture" class="bg-gradient-to-r from-emerald-500 to-suit-danger h-full w-[0%] transition-all duration-300"></div>
                    </div>
                </div>
            </div>

            <!-- Technical Narrative Description -->
            <div class="space-y-2 font-mono text-xs">
                <h3 class="text-suit-cyan font-bold text-[11px] uppercase border-b border-suit-cyan/20 pb-1">
                    🔬 Engenharia do Traje Bio-SAMS
                </h3>
                <div id="mode-doc-text" class="bg-black/50 p-2.5 rounded border border-gray-800 text-gray-300 text-[11px] leading-relaxed space-y-1.5">
                    <p>
                        <strong class="text-suit-cyan">Estado Flexível:</strong> Fluido Bio-SAMS em repouso permitindo total amplitude biomecânica e conforto térmico ao soldado.
                    </p>
                </div>
            </div>

            <!-- Visual Legend -->
            <div class="bg-black/60 p-2.5 rounded border border-suit-border/40 space-y-1 text-[11px] font-mono">
                <div class="text-gray-400 mb-0.5 font-bold">Legenda de Componentes:</div>
                <div class="flex items-center gap-2">
                    <span class="w-2.5 h-2.5 rounded-full bg-suit-emerald inline-block"></span>
                    <span class="text-gray-300">Camada Bio-SAMS Magnetorregulada</span>
                </div>
                <div class="flex items-center gap-2">
                    <span class="w-2.5 h-2.5 rounded-full bg-suit-amber inline-block"></span>
                    <span class="text-gray-300">Focos de Energia Negativa (Mjolnir)</span>
                </div>
                <div class="flex items-center gap-2">
                    <span class="w-2.5 h-2.5 rounded-full bg-suit-purple inline-block"></span>
                    <span class="text-gray-300">Bolha Isolante Métrico-Barométrica</span>
                </div>
            </div>

        </aside>

    </div>

    <!-- Manual Modal -->
    <div id="info-modal" class="hidden fixed inset-0 bg-black/85 backdrop-blur-md z-50 flex items-center justify-center p-4">
        <div class="glass-panel max-w-2xl w-full p-6 rounded-lg border border-suit-cyan space-y-4 max-h-[85vh] overflow-y-auto font-mono">
            <div class="flex justify-between items-center border-b border-suit-cyan/30 pb-3">
                <h2 class="text-base sm:text-lg text-suit-cyan font-bold uppercase">Manual do Traje de Assalto Bio-SAMS</h2>
                <button id="close-modal-x" class="text-gray-400 hover:text-suit-danger text-xl font-bold">&times;</button>
            </div>
            
            <div class="space-y-3 text-xs text-gray-300 leading-relaxed">
                <p>
                    O **Traje de Assalto Bio-SAMS** transforma a blindagem passiva tradicional em um exo-chassi ativo de amortecimento quântico e isolamento métrico.
                </p>

                <div class="bg-black/60 p-3 rounded border border-suit-border space-y-1">
                    <h4 class="text-suit-emerald font-bold">1. Endurecimento Molecular SROS em Nanossegundos</h4>
                    <p>O fluido Bio-SAMS flui entre a pele e a armadura. Ao detectar um choque cinético ou onda de pulso térmico, o SROS aplica um campo magnético instantâneo, cristalizando o fluido em uma barreira molecular ultra-densa (até 85 GPa) antes do impacto atingir o operador.</p>
                </div>

                <div class="bg-black/60 p-3 rounded border border-suit-border space-y-1">
                    <h4 class="text-suit-amber font-bold">2. Anulação de Carga Extrema (Interface Mjolnir)</h4>
                    <p>Ao empunhar armas de densidade singular ou massa extrema, o traje projeta focos de energia negativa nas articulações e na coluna espinhal, compensando a aceleração gravitacional e impedindo o fraturamento ósseo do usuário.</p>
                </div>

                <div class="bg-black/60 p-3 rounded border border-suit-border space-y-1">
                    <h4 class="text-suit-purple font-bold">3. Bolha Isolante do Boom Tube</h4>
                    <p>A armadura gera um invólucro métrico independente durante o teletransporte. Enquanto o reator HD-MHD rasga o espaço ao redor, a pressão barométrica e a assinatura biológica do soldado permanecem 100% inalteradas, anulando a Descompensação Métrica.</p>
                </div>
            </div>

            <div class="text-right pt-2 border-t border-suit-cyan/30">
                <button id="close-modal-btn" class="bg-suit-cyan/20 hover:bg-suit-cyan/40 text-suit-cyan border border-suit-cyan px-4 py-2 rounded text-xs font-bold transition">
                    ENTENDIDO - RETORNAR AO SISTEMA
                </button>
            </div>
        </div>
    </div>

    <!-- JavaScript Simulation Engine & Web Audio -->
    <script>
        // --- State Management ---
        const state = {
            mode: 'FLUID',             // FLUID, MJOLNIR, BOOM_BUBBLE
            compensationRaw: 100,      // Slider 0 - 100%
            compensationPct: 100.0,
            
            // Physics / Bio Parameters
            pressureAtm: 1.00,
            rigidityGpa: 0.05,
            negEnergyTev: 0.00,
            spinalStressPct: 0.0,
            bubbleIntegrityPct: 100.0,
            kineticDissipationPct: 99.8,
            fractureRiskPct: 0.0,
            
            time: 0,
            impactActive: false,
            impactRadius: 0
        };

        const modeTexts = {
            FLUID: {
                title: "MODO 1: CAMADA FLUIDA INTELIGENTE",
                sub: "Transição viscoelástica para barreira molecular ultra-densa em nanossegundos",
                doc: `<p><strong class="text-suit-emerald">Amortecimento Dinâmico:</strong> O fluido Bio-SAMS permanece leve e flexível durante movimentos basais, solidificando-se em até 85 GPa de rigidez extrema apenas na zona exata de impacto cinético.</p>`
            },
            MJOLNIR: {
                title: "MODO 2: OPERAÇÃO MJOLNIR (MASSA EXTREMA)",
                sub: "Micro-focos de energia negativa nas articulações anulando o estresse mecânico",
                doc: `<p><strong class="text-suit-amber">Estabilização Articular:</strong> A armadura comunica-se com a IA do armamento, gerando campos gravitacionais repulsivos negativos nas articulações e espinha para evitar colapso ósseo.</p>`
            },
            BOOM_BUBBLE: {
                title: "MODO 3: BOLHA ISOLANTE DO BOOM TUBE",
                sub: "Invólucro métrico isolando a assinatura biológica e pressão barométrica interna",
                doc: `<p><strong class="text-suit-purple">Isolamento Barométrico:</strong> Uma bolha de espaço plano é mantida ao redor do soldado durante a travessia do tubo, impedindo a Descompensação Métrica e o trauma vestibular.</p>`
            }
        };

        // Canvas Setup
        const canvas = document.getElementById('suitCanvas');
        const ctx = canvas.getContext('2d');
        let width = 0;
        let height = 0;

        let fluidParticles = [];
        let negativeEnergyNodes = [];

        // Web Audio Synthesizer
        let audioCtx = null;

        function initAudio() {
            if (!audioCtx) {
                const AudioContext = window.AudioContext || window.webkitAudioContext;
                audioCtx = new AudioContext();
            }
        }

        function playHardeningSound() {
            try {
                initAudio();
                if (!audioCtx) return;
                const now = audioCtx.currentTime;

                // High pitch SROS magnetic pulse + low impact thud
                const oscPulse = audioCtx.createOscillator();
                const gainPulse = audioCtx.createGain();

                oscPulse.type = 'sawtooth';
                oscPulse.frequency.setValueAtTime(1400, now);
                oscPulse.frequency.exponentialRampToValueAtTime(400, now + 0.25);

                gainPulse.gain.setValueAtTime(0.3, now);
                gainPulse.gain.exponentialRampToValueAtTime(0.001, now + 0.25);

                const oscThud = audioCtx.createOscillator();
                const gainThud = audioCtx.createGain();

                oscThud.type = 'sine';
                oscThud.frequency.setValueAtTime(180, now);
                oscThud.frequency.exponentialRampToValueAtTime(40, now + 0.4);

                gainThud.gain.setValueAtTime(0.5, now);
                gainThud.gain.exponentialRampToValueAtTime(0.001, now + 0.4);

                oscPulse.connect(gainPulse);
                gainPulse.connect(audioCtx.destination);
                oscThud.connect(gainThud);
                gainThud.connect(audioCtx.destination);

                oscPulse.start(now);
                oscThud.start(now);
                oscPulse.stop(now + 0.25);
                oscThud.stop(now + 0.4);
            } catch(e) {
                console.log("Audio sintético pronto.");
            }
        }

        function initEntities() {
            fluidParticles = [];
            negativeEnergyNodes = [];

            // Fluid Layer Particles around the Suit Body
            for (let i = 0; i < 60; i++) {
                fluidParticles.push({
                    angle: Math.random() * Math.PI * 2,
                    dist: Math.random() * 20 + 80,
                    size: Math.random() * 3.5 + 2,
                    speed: Math.random() * 0.03 + 0.01,
                    hardened: false
                });
            }

            // Negative Energy Joint Nodes for Mjolnir Mode
            const jointPositions = [
                { x: -35, y: -40 }, { x: 35, y: -40 }, // Ombros
                { x: -45, y: 10 }, { x: 45, y: 10 },   // Cotovelos
                { x: 0, y: -10 },                      // Espinha Central
                { x: -20, y: 60 }, { x: 20, y: 60 }    // Joelhos
            ];

            jointPositions.forEach(j => {
                negativeEnergyNodes.push({
                    x: j.x,
                    y: j.y,
                    pulse: Math.random() * Math.PI
                });
            });
        }

        function handleResize() {
            const container = canvas.parentElement;
            width = container.clientWidth;
            height = container.clientHeight;
            canvas.width = width;
            canvas.height = height;

            initEntities();
        }

        window.addEventListener('resize', handleResize);

        // --- Render Loop ---
        function draw() {
            state.time += 0.03;

            ctx.fillStyle = '#02060e';
            ctx.fillRect(0, 0, width, height);

            const centerX = width / 2;
            const centerY = height / 2;

            ctx.save();
            ctx.translate(centerX, centerY);

            // Render Modes
            if (state.mode === 'BOOM_BUBBLE') {
                renderMetricBubble();
            }

            renderSoldierSilhouette();
            renderBioSamsLayer();

            if (state.mode === 'MJOLNIR') {
                renderMjolnirJointNodes();
            }

            ctx.restore();

            if (state.impactActive) {
                renderImpactWave();
            }

            updateTelemetryAndCalculations();
            requestAnimationFrame(draw);
        }

        // 1. Soldier & Exo-Suit Base Silhouette
        function renderSoldierSilhouette() {
            ctx.strokeStyle = state.fractureRiskPct > 40 ? '#ef4444' : '#00f3ff';
            ctx.lineWidth = 2.5;

            // Head / Helmet
            ctx.beginPath();
            ctx.arc(0, -90, 18, 0, Math.PI * 2);
            ctx.stroke();

            // Torso / Spine
            ctx.beginPath();
            ctx.moveTo(0, -72);
            ctx.lineTo(0, -10);

            // Arms / Exo-Arms
            ctx.moveTo(-45, -45);
            ctx.lineTo(0, -60);
            ctx.lineTo(45, -45);

            // Legs / Exo-Legs
            ctx.moveTo(0, -10);
            ctx.lineTo(-25, 75);
            ctx.moveTo(0, -10);
            ctx.lineTo(25, 75);

            ctx.stroke();
        }

        // 2. Intelligent Bio-SAMS Fluid Layer Render
        function renderBioSamsLayer() {
            fluidParticles.forEach((p, idx) => {
                p.angle += p.speed;
                const isHard = state.impactActive || p.hardened;
                const currentDist = p.dist + Math.sin(state.time * 4 + idx) * 4;

                const x = Math.cos(p.angle) * currentDist;
                const y = Math.sin(p.angle) * currentDist;

                ctx.fillStyle = isHard ? '#10b981' : 'rgba(0, 243, 255, 0.6)';
                ctx.beginPath();
                ctx.arc(x, y, isHard ? p.size * 1.5 : p.size, 0, Math.PI * 2);
                ctx.fill();

                if (isHard) {
                    // Crystalline molecular lattice lines
                    ctx.strokeStyle = 'rgba(16, 185, 129, 0.5)';
                    ctx.lineWidth = 0.8;
                    ctx.beginPath();
                    ctx.moveTo(x, y);
                    ctx.lineTo(x + Math.cos(p.angle) * 15, y + Math.sin(p.angle) * 15);
                    ctx.stroke();
                }
            });
        }

        // 3. Mjolnir Joint Negative Energy Nodes
        function renderMjolnirJointNodes() {
            const compFactor = state.compensationPct / 100;

            negativeEnergyNodes.forEach(node => {
                node.pulse += 0.05;
                const radius = 8 + Math.sin(node.pulse) * 3;

                ctx.fillStyle = `rgba(245, 158, 11, ${0.4 + compFactor * 0.5})`;
                ctx.shadowBlur = 12 * compFactor;
                ctx.shadowColor = '#f59e0b';
                ctx.beginPath();
                ctx.arc(node.x, node.y, radius, 0, Math.PI * 2);
                ctx.fill();
                ctx.shadowBlur = 0;
            });

            // Heavy Weapon Projection
            ctx.strokeStyle = '#f59e0b';
            ctx.lineWidth = 3;
            ctx.beginPath();
            ctx.moveTo(45, -45);
            ctx.lineTo(75, -20); // Right Arm holding Mjolnir
            ctx.stroke();

            // Mjolnir Hammer Head
            ctx.fillStyle = '#f59e0b';
            ctx.fillRect(65, -35, 25, 30);
        }

        // 4. Boom Tube Metric Bubble
        function renderMetricBubble() {
            const bubbleRadius = 135 + Math.sin(state.time * 2) * 5;

            ctx.strokeStyle = 'rgba(168, 85, 247, 0.8)';
            ctx.lineWidth = 2.5;
            ctx.shadowBlur = 18;
            ctx.shadowColor = '#a855f7';
            ctx.beginPath();
            ctx.arc(0, 0, bubbleRadius, 0, Math.PI * 2);
            ctx.stroke();
            ctx.shadowBlur = 0;

            // Space Distortions outside bubble
            ctx.strokeStyle = 'rgba(239, 68, 68, 0.3)';
            ctx.lineWidth = 1;
            for (let i = 0; i < 8; i++) {
                const angle = (i / 8) * Math.PI * 2 + state.time;
                ctx.beginPath();
                ctx.moveTo(Math.cos(angle) * (bubbleRadius + 5), Math.sin(angle) * (bubbleRadius + 5));
                ctx.lineTo(Math.cos(angle) * (bubbleRadius + 35), Math.sin(angle) * (bubbleRadius + 35));
                ctx.stroke();
            }
        }

        // Impact Wave Expansion
        function renderImpactWave() {
            state.impactRadius += 12;
            const centerX = width / 2;
            const centerY = height / 2;

            ctx.strokeStyle = `rgba(16, 185, 129, ${Math.max(0, 1 - state.impactRadius / (width * 0.45))})`;
            ctx.lineWidth = 6;
            ctx.beginPath();
            ctx.arc(centerX, centerY, state.impactRadius, 0, Math.PI * 2);
            ctx.stroke();

            if (state.impactRadius > width * 0.45) {
                state.impactActive = false;
            }
        }

        // Mode Switching
        function setMode(modeType) {
            state.mode = modeType;

            ['fluid', 'mjolnir', 'boom'].forEach(m => {
                const btn = document.getElementById(`btn-mode-${m}`);
                btn.className = 'w-full text-left p-2 rounded border border-suit-border bg-black/40 text-gray-400 hover:text-white transition flex items-center justify-between';
            });

            const activeBtn = document.getElementById(`btn-mode-${modeType === 'BOOM_BUBBLE' ? 'boom' : modeType.toLowerCase()}`);
            const colorClass = modeType === 'FLUID' ? 'border-suit-emerald bg-suit-emerald/20 text-suit-emerald font-bold' : (modeType === 'MJOLNIR' ? 'border-suit-amber bg-suit-amber/20 text-suit-amber font-bold' : 'border-suit-purple bg-suit-purple/20 text-suit-purple font-bold');
            activeBtn.className = `w-full text-left p-2 rounded border transition flex items-center justify-between ${colorClass}`;

            const info = modeTexts[modeType];
            document.getElementById('hud-mode-title').innerText = info.title;
            document.getElementById('hud-mode-sub').innerText = info.sub;
            document.getElementById('mode-doc-text').innerHTML = info.doc;

            addLog(`[SISTEMA] Modo operacional alterado para: ${info.title}`);
        }

        function triggerKineticImpact() {
            state.impactActive = true;
            state.impactRadius = 10;
            playHardeningSound();

            const banner = document.getElementById('hud-impact-banner');
            banner.classList.remove('hidden');
            setTimeout(() => { banner.classList.add('hidden'); }, 1500);

            addLog('💥 [IMPACTO CINÉTICO] Campo SROS ativado. Cristalização molecular do fluido Bio-SAMS executada.', 'emerald');
        }

        // Dynamic Calculations
        function updateTelemetryAndCalculations() {
            state.compensationRaw = parseInt(document.getElementById('slider-compensation').value);
            state.compensationPct = state.compensationRaw;
            document.getElementById('val-compensation').innerText = `${state.compensationPct.toFixed(1)}%`;

            const compFactor = state.compensationPct / 100;

            if (state.mode === 'FLUID') {
                state.pressureAtm = 1.00;
                state.rigidityGpa = state.impactActive ? 85.0 : 0.05;
                state.negEnergyTev = 0.00;
                state.spinalStressPct = 0.0;
                state.fractureRiskPct = 0.0;
            } else if (state.mode === 'MJOLNIR') {
                state.pressureAtm = 1.05;
                state.rigidityGpa = 42.0;
                state.negEnergyTev = (14.8 * compFactor).toFixed(1);
                state.spinalStressPct = ((1 - compFactor) * 88.0).toFixed(1);
                state.fractureRiskPct = ((1 - compFactor) * 94.0).toFixed(1);
            } else if (state.mode === 'BOOM_BUBBLE') {
                state.pressureAtm = 1.00; // Perfect 1 ATM internally
                state.rigidityGpa = 15.0;
                state.negEnergyTev = 2.40;
                state.spinalStressPct = 1.2;
                state.fractureRiskPct = 0.0;
            }

            document.getElementById('hdr-fluid-state').innerText = state.impactActive ? 'CRISTALIZADO (85 GPa)' : 'VISCOSO / FLEXÍVEL';
            document.getElementById('tele-pressure').innerText = `${state.pressureAtm} ATM`;
            document.getElementById('tele-rigidity').innerText = `${state.rigidityGpa} GPa`;
            document.getElementById('tele-neg-energy').innerText = `${state.negEnergyTev} TeV`;
            document.getElementById('tele-spinal-stress').innerText = `${state.spinalStressPct}%`;

            document.getElementById('tele-fracture-pct').innerText = `${state.fractureRiskPct}%`;
            document.getElementById('bar-fracture').style.width = `${state.fractureRiskPct}%`;

            document.getElementById('hud-hardness-val').innerText = `${state.rigidityGpa} GPa`;
            document.getElementById('log-clock').innerText = new Date().toTimeString().split(' ')[0];
        }

        function addLog(msg, type = 'cyan') {
            const consoleBox = document.getElementById('log-console');
            const p = document.createElement('p');

            if (type === 'emerald') p.className = 'text-suit-emerald font-bold';
            else if (type === 'amber') p.className = 'text-suit-amber font-bold';
            else if (type === 'purple') p.className = 'text-suit-purple font-bold';
            else p.className = 'text-suit-cyan';

            p.innerText = `${msg}`;
            consoleBox.appendChild(p);
            consoleBox.scrollTop = consoleBox.scrollHeight;
        }

        window.onload = () => {
            handleResize();

            document.getElementById('btn-manual').addEventListener('click', () => {
                document.getElementById('info-modal').classList.remove('hidden');
            });
            const closeModal = () => document.getElementById('info-modal').classList.add('hidden');
            document.getElementById('close-modal-x').addEventListener('click', closeModal);
            document.getElementById('close-modal-btn').addEventListener('click', closeModal);

            setMode('FLUID');
            draw();
            addLog('[INICIALIZAÇÃO] Traje de Assalto Bio-SAMS & Exo-Chassi Quântico Ativo.');
        };
    </script>
</body>
</html>
