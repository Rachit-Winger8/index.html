#```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SYNAPSE HUB | Collaborate With The Future</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        cyber: {
                            base: '#040714',
                            card: 'rgba(11, 19, 43, 0.72)',
                            cyan: '#00f2fe',
                            violet: '#8a2be2',
                            electricBlue: '#3a86ff',
                            neonPink: '#ff007f',
                            glowEmerald: '#10b981'
                        }
                    },
                    boxShadow: {
                        'neon-cyan': '0 0 25px rgba(0, 242, 254, 0.45)',
                        'neon-violet': '0 0 30px rgba(138, 43, 226, 0.45)',
                        'poster-glow': '0 0 50px rgba(0, 242, 254, 0.3), 0 0 80px rgba(138, 43, 226, 0.25)'
                    },
                    animation: {
                        'pulse-glow': 'pulseGlow 3.5s ease-in-out infinite',
                        'float': 'float 5s ease-in-out infinite'
                    },
                    keyframes: {
                        pulseGlow: {
                            '0%, 100%': { opacity: '0.4' },
                            '50%': { opacity: '0.85' }
                        },
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-10px)' }
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;700;800&family=Space+Grotesk:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #040714;
            color: #e2e8f0;
            overflow-x: hidden;
        }
        .font-mono-tech {
            font-family: 'Space Grotesk', monospace;
        }
        .grid-backdrop {
            background-image: 
                radial-gradient(circle at center, rgba(0, 242, 254, 0.08) 0, transparent 70%),
                linear-gradient(rgba(0, 242, 254, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 242, 254, 0.05) 1px, transparent 1px);
            background-size: 100% 100%, 36px 36px, 36px 36px;
        }
        .glass-panel {
            background: rgba(9, 14, 34, 0.75);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(0, 242, 254, 0.18);
        }
        .gradient-cyan-violet {
            background: linear-gradient(135deg, #00f2fe 0%, #3a86ff 50%, #8a2be2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .glow-line {
            background: linear-gradient(90deg, transparent, #00f2fe, #8a2be2, transparent);
            height: 1px;
        }
    </style>
</head>
<body class="grid-backdrop min-h-screen selection:bg-cyan-400 selection:text-black">

    <!-- Sound and Toast alerts -->
    <div id="toast" class="fixed bottom-6 right-6 z-50 transform translate-y-24 opacity-0 transition-all duration-300 glass-panel border border-cyan-400 px-5 py-3 rounded-2xl shadow-neon-cyan flex items-center gap-3">
        <i class="fa-solid fa-satellite-dish text-cyan-400 text-lg"></i>
        <span id="toast-text" class="text-sm font-mono-tech text-white">Network synced</span>
    </div>

    <!-- Navigation Header -->
    <header class="sticky top-0 z-40 w-full glass-panel border-b border-cyan-500/20 px-6 py-4">
        <div class="max-w-7xl mx-auto flex items-center justify-between">
            <div class="flex items-center gap-3 cursor-pointer" onclick="playAudioTone(520)">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-cyan-400 via-blue-500 to-purple-600 flex items-center justify-center text-black font-extrabold shadow-neon-cyan">
                    <i class="fa-solid fa-brain text-slate-950 text-xl"></i>
                </div>
                <div>
                    <span class="font-mono-tech font-extrabold text-xl tracking-wider text-white">SYNAPSE<span class="text-cyan-400">HUB</span></span>
                    <span class="block text-[10px] text-cyan-300 font-mono-tech tracking-widest uppercase">Intelligent Co-Work Mesh</span>
                </div>
            </div>

            <nav class="hidden md:flex items-center gap-8 text-sm font-mono-tech text-slate-300">
                <a href="#hero" class="hover:text-cyan-400 transition">01. Vision</a>
                <a href="#poster-section" class="hover:text-cyan-400 transition">02. The Poster</a>
                <a href="#pipeline" class="hover:text-cyan-400 transition">03. Flowchart</a>
                <a href="#simulator" class="hover:text-cyan-400 transition">04. AI Simulator</a>
                <a href="#waitlist" class="hover:text-cyan-400 transition">05. Access Pods</a>
            </nav>

            <div class="flex items-center gap-3">
                <button id="sfx-toggle" onclick="toggleAudio()" class="px-3 py-1.5 rounded-lg border border-cyan-500/30 text-cyan-300 text-xs font-mono-tech hover:bg-cyan-950/40 transition">
                    <i id="sfx-icon" class="fa-solid fa-volume-high mr-1"></i> SFX: ON
                </button>
                <a href="#waitlist" class="px-4 py-2 rounded-xl bg-gradient-to-r from-cyan-400 to-blue-500 hover:from-cyan-300 hover:to-blue-400 text-black font-mono-tech font-bold text-xs uppercase tracking-wider transition shadow-neon-cyan">
                    Join Waitlist
                </a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="hero" class="relative pt-16 pb-20 px-6 max-w-7xl mx-auto">
        <div class="text-center max-w-4xl mx-auto space-y-6">
            <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-cyan-950/60 border border-cyan-400/40 text-cyan-300 text-xs font-mono-tech tracking-widest uppercase animate-pulse">
                <i class="fa-solid fa-sparkles text-cyan-400"></i> Autonomous Intelligent Workspace Architecture
            </div>

            <h1 class="text-4xl sm:text-6xl md:text-7xl font-extrabold tracking-tight leading-[1.1] text-white">
                SYNAPSE HUB:<br>
                <span class="gradient-cyan-violet">COLLABORATE WITH THE FUTURE</span>
            </h1>

            <p class="text-lg md:text-xl text-slate-300 font-light max-w-2xl mx-auto">
                Where Human Creativity Meets Intelligent Spaces. Experience fluid holographic collaboration, adaptive machine teammates, and frictionless flow state.
            </p>

            <div class="pt-4 flex flex-wrap justify-center gap-4">
                <a href="#poster-section" class="px-6 py-3.5 rounded-xl bg-cyan-400 hover:bg-cyan-300 text-slate-950 font-mono-tech font-bold text-sm tracking-wide transition shadow-neon-cyan flex items-center gap-2">
                    <i class="fa-solid fa-expand"></i> Inspect Innovation Poster
                </a>
                <a href="#simulator" class="px-6 py-3.5 rounded-xl border border-cyan-400/40 text-cyan-300 hover:bg-cyan-950/40 font-mono-tech text-sm transition flex items-center gap-2">
                    <i class="fa-solid fa-sliders"></i> Launch Workspace Simulator
                </a>
            </div>

            <!-- Stats Ribbon -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4 pt-10 border-t border-slate-800 font-mono-tech text-center">
                <div class="p-4 rounded-xl glass-panel">
                    <div class="text-2xl font-bold text-cyan-400">4.8x</div>
                    <div class="text-xs text-slate-400 uppercase mt-1">Velocity Multiplier</div>
                </div>
                <div class="p-4 rounded-xl glass-panel">
                    <div class="text-2xl font-bold text-purple-400">&lt; 1.5ms</div>
                    <div class="text-xs text-slate-400 uppercase mt-1">Holo-Mesh Latency</div>
                </div>
                <div class="p-4 rounded-xl glass-panel">
                    <div class="text-2xl font-bold text-blue-400">100%</div>
                    <div class="text-xs text-slate-400 uppercase mt-1">Contextual Sync</div>
                </div>
                <div class="p-4 rounded-xl glass-panel">
                    <div class="text-2xl font-bold text-emerald-400">Zero-Friction</div>
                    <div class="text-xs text-slate-400 uppercase mt-1">Routine Delegation</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Poster Section -->
    <section id="poster-section" class="py-20 px-6 max-w-7xl mx-auto border-t border-cyan-500/20">
        <div class="flex flex-col lg:flex-row items-center gap-12">
            
            <!-- Left: Description and Poster Highlights -->
            <div class="lg:w-1/2 space-y-6">
                <span class="px-3 py-1 rounded-full text-xs font-mono-tech font-bold text-cyan-400 bg-cyan-950/60 border border-cyan-500/40 uppercase">
                    Key Artifact • Visual Briefing
                </span>
                <h2 class="text-3xl sm:text-4xl font-extrabold text-white">
                    The Official Vision: <span class="gradient-cyan-violet">AI-Powered Co-Working</span>
                </h2>
                <p class="text-slate-300 text-sm md:text-base leading-relaxed">
                    Designed as a high-impact business blueprint, the SYNAPSE HUB poster breaks down how human talent and multi-agent machine swarms converge onto interactive hologram touch tables and zero-latency pods.
                </p>

                <div class="space-y-3 font-mono-tech text-xs">
                    <div class="flex items-center gap-3 p-3 rounded-xl glass-panel border-l-4 border-l-cyan-400">
                        <i class="fa-solid fa-qrcode text-cyan-400 text-lg"></i>
                        <div>
                            <span class="text-white font-bold uppercase block">Instant Biometric Network Onboarding</span>
                            <span class="text-slate-400">Connect in seconds with automated environment calibration.</span>
                        </div>
                    </div>
                    <div class="flex items-center gap-3 p-3 rounded-xl glass-panel border-l-4 border-l-purple-500">
                        <i class="fa-solid fa-network-wired text-purple-400 text-lg"></i>
                        <div>
                            <span class="text-white font-bold uppercase block">AI Matchmaking & Skill Synthesis</span>
                            <span class="text-slate-400">Dynamic pairings between humans and specialized AI copilots.</span>
                        </div>
                    </div>
                    <div class="flex items-center gap-3 p-3 rounded-xl glass-panel border-l-4 border-l-blue-500">
                        <i class="fa-solid fa-laptop-code text-blue-400 text-lg"></i>
                        <div>
                            <span class="text-white font-bold uppercase block">Spatial Smart Desks & Swarms</span>
                            <span class="text-slate-400">Simultaneous real-time manipulation of data, visuals, and architecture.</span>
                        </div>
                    </div>
                </div>

                <div class="flex gap-4 pt-2">
                    <button onclick="openModal()" class="px-6 py-3 rounded-xl bg-cyan-400 hover:bg-cyan-300 text-black font-mono-tech font-bold text-xs uppercase tracking-wider transition shadow-neon-cyan flex items-center gap-2">
                        <i class="fa-solid fa-magnifying-glass-plus"></i> Open Fullscreen Poster Lightbox
                    </button>
                    <button onclick="copyPosterInfo()" class="px-4 py-3 rounded-xl border border-slate-700 hover:border-cyan-400 text-slate-300 text-xs font-mono-tech transition">
                        <i class="fa-solid fa-copy"></i> Copy Poster Copy
                    </button>
                </div>
            </div>

            <!-- Right: Glowing Cyber Poster Display -->
            <div class="lg:w-1/2 flex justify-center">
                <div class="relative max-w-md w-full group cursor-pointer" onclick="openModal()">
                    <div class="absolute -inset-1 bg-gradient-to-r from-cyan-400 via-purple-600 to-blue-500 rounded-3xl blur-xl opacity-60 group-hover:opacity-90 transition duration-700 animate-pulse-glow"></div>
                    
                    <!-- Poster Container -->
                    <div class="relative rounded-2xl bg-gradient-to-b from-cyan-400 via-purple-500 to-blue-600 p-[2px] shadow-poster-glow">
                        <div class="bg-[#060a1c] rounded-2xl p-6 text-center overflow-hidden border border-cyan-400/30">
                            
                            <!-- Header in Poster -->
                            <div class="text-[11px] font-mono-tech tracking-widest text-cyan-400 font-extrabold uppercase">
                                AI-POWERED CO-WORKING
                            </div>
                            <h3 class="text-2xl font-extrabold text-white mt-1 uppercase font-mono-tech tracking-tight leading-tight">
                                COLLABORATE<br><span class="text-cyan-400">WITH THE FUTURE</span>
                            </h3>
                            <p class="text-slate-300 text-[11px] italic mt-1">
                                Where Human Creativity Meets Intelligent Spaces.
                            </p>

                            <!-- Graphic Illustration Frame -->
                            <div class="my-5 p-4 rounded-xl bg-gradient-to-b from-cyan-950/40 via-slate-900 to-purple-950/40 border border-cyan-400/30 relative">
                                <div class="w-full h-44 rounded-lg bg-slate-950 flex flex-col items-center justify-center relative border border-cyan-500/20 overflow-hidden">
                                    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,rgba(0,242,254,0.15)_0,transparent_75%)]"></div>
                                    
                                    <!-- Central Holographic Table -->
                                    <div class="w-48 h-20 rounded-xl border border-cyan-400 bg-cyan-500/10 flex flex-col items-center justify-center shadow-neon-cyan relative transform -rotate-1">
                                        <div class="absolute -top-2 px-2 py-0.5 rounded bg-cyan-400 text-black text-[8px] font-mono-tech font-bold uppercase">
                                            Interactive Smart Desk
                                        </div>
                                        <div class="flex items-center gap-3 text-cyan-300 text-lg animate-pulse">
                                            <i class="fa-solid fa-city"></i>
                                            <i class="fa-solid fa-chart-simple"></i>
                                            <i class="fa-solid fa-network-wired"></i>
                                            <i class="fa-solid fa-microchip"></i>
                                        </div>
                                        <div class="text-[9px] font-mono-tech text-cyan-200 mt-1">Mesh Holo-Canvas Active</div>
                                    </div>

                                    <!-- Surrounding Avatars -->
                                    <div class="absolute left-3 top-3 flex items-center gap-1.5">
                                        <div class="w-7 h-7 rounded-full bg-cyan-500/20 border border-cyan-400 flex items-center justify-center text-cyan-300 text-xs">
                                            <i class="fa-solid fa-robot"></i>
                                        </div>
                                        <span class="text-[8px] font-mono-tech text-cyan-300">AI Pilot</span>
                                    </div>
                                    <div class="absolute right-3 top-3 flex items-center gap-1.5">
                                        <div class="w-7 h-7 rounded-full bg-purple-500/20 border border-purple-400 flex items-center justify-center text-purple-300 text-xs">
                                            <i class="fa-solid fa-user"></i>
                                        </div>
                                        <span class="text-[8px] font-mono-tech text-purple-300">Creator</span>
                                    </div>
                                </div>
                            </div>

                            <!-- Flowchart on poster -->
                            <div class="pt-2 border-t border-cyan-500/30">
                                <div class="text-[11px] font-mono-tech font-bold text-cyan-300 uppercase tracking-widest mb-2 flex items-center justify-center gap-2">
                                    <span class="w-4 h-[1px] bg-cyan-400"></span> HOW IT WORKS <span class="w-4 h-[1px] bg-cyan-400"></span>
                                </div>
                                <div class="grid grid-cols-4 gap-1.5 text-[8px] font-mono-tech">
                                    <div class="p-1.5 rounded bg-cyan-950/40 border border-cyan-500/30">
                                        <i class="fa-solid fa-qrcode text-cyan-400 text-xs block mb-1"></i>
                                        <b class="text-white block">STEP 1</b>
                                        <span class="text-slate-300">Connect</span>
                                    </div>
                                    <div class="p-1.5 rounded bg-purple-950/40 border border-purple-500/30">
                                        <i class="fa-solid fa-handshake-angle text-purple-400 text-xs block mb-1"></i>
                                        <b class="text-white block">STEP 2</b>
                                        <span class="text-slate-300">AI Match</span>
                                    </div>
                                    <div class="p-1.5 rounded bg-blue-950/40 border border-blue-500/30">
                                        <i class="fa-solid fa-users text-blue-400 text-xs block mb-1"></i>
                                        <b class="text-white block">STEP 3</b>
                                        <span class="text-slate-300">Co-Create</span>
                                    </div>
                                    <div class="p-1.5 rounded bg-pink-950/40 border border-pink-500/30">
                                        <i class="fa-solid fa-chart-line text-pink-400 text-xs block mb-1"></i>
                                        <b class="text-white block">STEP 4</b>
                                        <span class="text-slate-300">Optimize</span>
                                    </div>
                                </div>
                            </div>

                            <!-- Bottom Poster Meta -->
                            <div class="mt-4 pt-3 border-t border-slate-800 flex items-center justify-between text-left">
                                <div>
                                    <span class="text-[9px] font-mono-tech font-bold text-cyan-300 block">DISCOVER THE NEXT EVOLUTION</span>
                                    <span class="text-[8px] font-mono-tech text-slate-400">www.futurehubcoworking.com</span>
                                </div>
                                <div class="w-7 h-7 bg-white p-0.5 rounded flex items-center justify-center text-black text-sm">
                                    <i class="fa-solid fa-qrcode"></i>
                                </div>
                            </div>

                        </div>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- Pipeline Section -->
    <section id="pipeline" class="py-20 px-6 max-w-7xl mx-auto border-t border-cyan-500/20 bg-slate-950/50">
        <div class="text-center max-w-3xl mx-auto mb-16 space-y-3">
            <span class="px-3 py-1 rounded-full text-xs font-mono-tech font-bold text-purple-400 bg-purple-950/60 border border-purple-500/40 uppercase">
                Step-by-Step Architecture
            </span>
            <h2 class="text-3xl md:text-5xl font-extrabold text-white">
                THE 4-STAGE <span class="gradient-cyan-violet">FLOWCHART</span>
            </h2>
            <p class="text-slate-400 text-sm md:text-base">
                Click any stage card below to unpack real-time metrics, node responses, and autonomous features.
            </p>
        </div>

        <!-- 4 Step Interactive Cards -->
        <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
            
            <div id="step-card-1" onclick="selectFlowStage(1)" class="cursor-pointer glass-panel p-6 rounded-2xl border-cyan-400 shadow-neon-cyan transition-all transform hover:-translate-y-1">
                <div class="w-10 h-10 rounded-xl bg-cyan-500/20 border border-cyan-400 flex items-center justify-center text-cyan-300 mb-4">
                    <i class="fa-solid fa-qrcode text-lg"></i>
                </div>
                <div class="text-xs font-mono-tech text-cyan-400 font-bold uppercase">Stage 01</div>
                <h3 class="text-lg font-bold text-white font-mono-tech mt-1">CONNECT & ACCESS</h3>
                <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                    Enter the space and instantly sync with the AI network. Custom ergonomic preferences initialize in under 200ms.
                </p>
            </div>

            <div id="step-card-2" onclick="selectFlowStage(2)" class="cursor-pointer glass-panel p-6 rounded-2xl border-slate-800 transition-all transform hover:-translate-y-1">
                <div class="w-10 h-10 rounded-xl bg-purple-500/20 border border-purple-400 flex items-center justify-center text-purple-300 mb-4">
                    <i class="fa-solid fa-handshake-angle text-lg"></i>
                </div>
                <div class="text-xs font-mono-tech text-purple-400 font-bold uppercase">Stage 02</div>
                <h3 class="text-lg font-bold text-white font-mono-tech mt-1">MEET YOUR AI ASSISTANT</h3>
                <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                    Receive custom project suggestions and matchmaking with complementary cross-discipline founders.
                </p>
            </div>

            <div id="step-card-3" onclick="selectFlowStage(3)" class="cursor-pointer glass-panel p-6 rounded-2xl border-slate-800 transition-all transform hover:-translate-y-1">
                <div class="w-10 h-10 rounded-xl bg-blue-500/20 border border-blue-400 flex items-center justify-center text-blue-300 mb-4">
                    <i class="fa-solid fa-users text-lg"></i>
                </div>
                <div class="text-xs font-mono-tech text-blue-400 font-bold uppercase">Stage 03</div>
                <h3 class="text-lg font-bold text-white font-mono-tech mt-1">REAL-TIME COLLABORATION</h3>
                <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                    Work alongside synthetic agents and peers at holographic touch desks with live shared spatial memory.
                </p>
            </div>

            <div id="step-card-4" onclick="selectFlowStage(4)" class="cursor-pointer glass-panel p-6 rounded-2xl border-slate-800 transition-all transform hover:-translate-y-1">
                <div class="w-10 h-10 rounded-xl bg-pink-500/20 border border-pink-400 flex items-center justify-center text-pink-300 mb-4">
                    <i class="fa-solid fa-chart-line text-lg"></i>
                </div>
                <div class="text-xs font-mono-tech text-pink-400 font-bold uppercase">Stage 04</div>
                <h3 class="text-lg font-bold text-white font-mono-tech mt-1">SMART OPTIMIZATION</h3>
                <p class="text-xs text-slate-400 mt-2 leading-relaxed">
                    AI automates routine operational tasks, reporting, and refactoring, maximizing your high-order creative output.
                </p>
            </div>

        </div>

        <!-- Dynamic Stage Details View -->
        <div class="mt-8 glass-panel p-8 rounded-3xl border border-cyan-500/40 relative">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 items-center">
                <div class="md:col-span-2 space-y-3">
                    <span id="stage-badge" class="px-2.5 py-0.5 rounded bg-cyan-500/20 text-cyan-300 text-xs font-mono-tech font-bold uppercase border border-cyan-400/40">
                        STAGE 01 TELEMETRY
                    </span>
                    <h4 id="stage-title" class="text-2xl font-extrabold text-white font-mono-tech">CONNECT & ACCESS ARCHITECTURE</h4>
                    <p id="stage-desc" class="text-slate-300 text-sm leading-relaxed">
                        SYNAPSE HUB eliminates the traditional check-in desk. Biometric beacons securely hydrate your workspace preferences: desk angle, display matrices, active git branches, and local neural model context buffers.
                    </p>
                    <div id="stage-pills" class="flex flex-wrap gap-2 text-xs font-mono-tech pt-2">
                        <span class="px-3 py-1 rounded-full bg-slate-900 border border-cyan-500/30 text-cyan-300">Biometric Handshake &lt;180ms</span>
                        <span class="px-3 py-1 rounded-full bg-slate-900 border border-cyan-500/30 text-cyan-300">Encrypted Cloud Context</span>
                    </div>
                </div>

                <div class="p-5 rounded-2xl bg-slate-900/80 border border-slate-800 font-mono-tech text-xs space-y-3">
                    <div class="flex justify-between text-slate-400 border-b border-slate-800 pb-2">
                        <span>STAGE METRIC</span>
                        <span id="metric-title" class="text-cyan-400">SYNC EFFICIENCY</span>
                    </div>
                    <div>
                        <div class="flex justify-between mb-1">
                            <span>Throughput:</span>
                            <span id="stage-stat" class="text-cyan-300 font-bold">99.8%</span>
                        </div>
                        <div class="w-full bg-slate-800 h-2 rounded-full overflow-hidden">
                            <div id="stage-bar" class="bg-cyan-400 h-full w-[99%] transition-all duration-500"></div>
                        </div>
                    </div>
                    <div class="text-[11px] text-slate-400 pt-1">
                        Status: <span class="text-emerald-400 font-bold">ONLINE & ACCELERATING</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- AI Simulator Section -->
    <section id="simulator" class="py-20 px-6 max-w-7xl mx-auto border-t border-cyan-500/20">
        <div class="text-center max-w-3xl mx-auto mb-14 space-y-3">
            <span class="px-3 py-1 rounded-full text-xs font-mono-tech font-bold text-cyan-400 bg-cyan-950/60 border border-cyan-500/40 uppercase">
                Customized Workspace Engine
            </span>
            <h2 class="text-3xl md:text-5xl font-extrabold text-white">
                INTERACTIVE <span class="gradient-cyan-violet">WORKSPACE SIMULATOR</span>
            </h2>
            <p class="text-slate-400 text-sm md:text-base">
                Select your persona to configure your dedicated AI co-pilot suite, specialized smart desk setup, and computed synergy index.
            </p>
        </div>

        <div class="glass-panel p-8 rounded-3xl border border-cyan-400/40 shadow-neon-cyan">
            <!-- Persona Selector Tabs -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-3 mb-8 font-mono-tech text-xs">
                <button onclick="setPersona('founder')" id="role-founder" class="p-3.5 rounded-xl border border-cyan-400 bg-cyan-500/20 text-white font-bold transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-rocket text-cyan-400"></i> Startup Founder
                </button>
                <button onclick="setPersona('designer')" id="role-designer" class="p-3.5 rounded-xl border border-slate-800 bg-slate-900/60 text-slate-400 font-bold transition flex items-center justify-center gap-2 hover:border-purple-400">
                    <i class="fa-solid fa-wand-magic-sparkles text-purple-400"></i> Lead Designer
                </button>
                <button onclick="setPersona('developer')" id="role-developer" class="p-3.5 rounded-xl border border-slate-800 bg-slate-900/60 text-slate-400 font-bold transition flex items-center justify-center gap-2 hover:border-blue-400">
                    <i class="fa-solid fa-terminal text-blue-400"></i> Software Architect
                </button>
                <button onclick="setPersona('marketer')" id="role-marketer" class="p-3.5 rounded-xl border border-slate-800 bg-slate-900/60 text-slate-400 font-bold transition flex items-center justify-center gap-2 hover:border-pink-400">
                    <i class="fa-solid fa-bullhorn text-pink-400"></i> Growth Strategist
                </button>
            </div>

            <!-- Simulator Output Screen -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center bg-slate-950/70 p-6 rounded-2xl border border-slate-800">
                <div class="lg:col-span-8 space-y-4">
                    <div class="flex items-center gap-3 font-mono-tech text-xs">
                        <span class="text-slate-400 uppercase">Configured Pod:</span>
                        <span id="sim-pod" class="px-2.5 py-0.5 rounded bg-cyan-500/20 text-cyan-300 font-bold">Pod Nexus-01: Executive Command</span>
                    </div>

                    <h3 id="sim-title" class="text-2xl font-bold font-mono-tech text-white">Venture Speed & Capital Engine</h3>
                    <p id="sim-desc" class="text-slate-300 text-sm leading-relaxed">
                        Equipped with live market intelligence swarms, cap-table dynamic modeling, pitch deck audio synthesis, and autonomous founder matching.
                    </p>

                    <div class="pt-2">
                        <span class="text-xs font-mono-tech text-slate-400 uppercase block mb-2">Dedicated Virtual Co-Agents:</span>
                        <div id="sim-agents" class="flex flex-wrap gap-2 text-xs font-mono-tech">
                            <span class="px-3 py-1 rounded-lg bg-cyan-950/60 border border-cyan-400/40 text-cyan-300 flex items-center gap-1.5">
                                <i class="fa-solid fa-microchip"></i> VentureBot-4
                            </span>
                            <span class="px-3 py-1 rounded-lg bg-purple-950/60 border border-purple-400/40 text-purple-300 flex items-center gap-1.5">
                                <i class="fa-solid fa-coins"></i> Runway Sentinel
                            </span>
                            <span class="px-3 py-1 rounded-lg bg-blue-950/60 border border-blue-400/40 text-blue-300 flex items-center gap-1.5">
                                <i class="fa-solid fa-file-waveform"></i> DeckArchitect AI
                            </span>
                        </div>
                    </div>
                </div>

                <!-- Synergy Gauge Circle -->
                <div class="lg:col-span-4 flex flex-col items-center justify-center p-6 bg-slate-900/60 rounded-2xl border border-cyan-500/30 text-center font-mono-tech">
                    <div class="relative w-32 h-32 flex items-center justify-center">
                        <svg class="w-full h-full transform -rotate-90" viewBox="0 0 36 36">
                            <path class="text-slate-800" stroke-width="3.5" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                            <path id="sim-score-circle" class="text-cyan-400 transition-all duration-1000 ease-out" stroke-dasharray="96, 100" stroke-width="3.5" stroke-linecap="round" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                        </svg>
                        <div class="absolute flex flex-col items-center">
                            <span id="sim-score-num" class="text-3xl font-extrabold text-white">96%</span>
                            <span class="text-[9px] text-cyan-400 uppercase tracking-widest">Synergy</span>
                        </div>
                    </div>
                    <span class="text-xs text-slate-300 mt-3 font-bold" id="sim-score-label">Flow State Maximized</span>
                    <a href="#waitlist" class="mt-4 w-full py-2 bg-gradient-to-r from-cyan-400 to-blue-500 text-black font-bold rounded-lg text-xs uppercase tracking-wider text-center">
                        Reserve This Setup
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Waitlist / Contact Section -->
    <section id="waitlist" class="py-20 px-6 max-w-4xl mx-auto border-t border-cyan-500/20">
        <div class="glass-panel p-8 sm:p-12 rounded-3xl border border-cyan-400/40 shadow-neon-cyan text-center">
            <span class="px-3 py-1 rounded-full text-xs font-mono-tech font-bold text-cyan-400 bg-cyan-950/60 border border-cyan-500/40 uppercase">
                Limited Founding Membership
            </span>
            <h2 class="text-3xl sm:text-4xl font-extrabold text-white mt-4 font-mono-tech">
                STEP INSIDE THE NEURAL HUB
            </h2>
            <p class="text-slate-300 text-sm max-w-lg mx-auto mt-2">
                Join our private alpha cohort. Claim early access to holographic pods, compute credits, and AI collaborative spaces.
            </p>

            <form onsubmit="handleJoin(event)" class="mt-8 max-w-md mx-auto space-y-4 font-mono-tech text-xs text-left">
                <div>
                    <label class="text-slate-300 block mb-1">Your Full Name</label>
                    <input type="text" required placeholder="Elena Vance" class="w-full bg-slate-900 border border-slate-800 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-cyan-400">
                </div>
                <div>
                    <label class="text-slate-300 block mb-1">Work Email</label>
                    <input type="email" required placeholder="elena@frontier-tech.ai" class="w-full bg-slate-900 border border-slate-800 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-cyan-400">
                </div>
                <div>
                    <label class="text-slate-300 block mb-1">Preferred Hub Location</label>
                    <select class="w-full bg-slate-900 border border-slate-800 rounded-xl px-4 py-3 text-white focus:outline-none focus:border-cyan-400">
                        <option>San Francisco (SOMA Neural Node)</option>
                        <option>Tokyo (Shibuya Holo-Tower)</option>
                        <option>London (King's Cross Matrix)</option>
                        <option>Virtual / Global Neural Stream</option>
                    </select>
                </div>
                <button type="submit" class="w-full py-3.5 rounded-xl bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600 hover:from-cyan-300 hover:to-purple-500 text-black font-extrabold uppercase tracking-wider text-xs shadow-neon-cyan transition mt-2">
                    Request Founding Access Pass
                </button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-slate-900 bg-slate-950 py-12 px-6 font-mono-tech text-xs text-slate-500">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row items-center justify-between gap-6">
            <div class="flex items-center gap-3">
                <div class="w-8 h-8 rounded-lg bg-cyan-500/20 border border-cyan-400 flex items-center justify-center text-cyan-300 font-bold">
                    <i class="fa-solid fa-brain"></i>
                </div>
                <div>
                    <span class="text-white font-bold block">SYNAPSE HUB INC.</span>
                    <span class="text-[10px]">Autonomous Co-Working Protocol</span>
                </div>
            </div>

            <div class="flex gap-6 text-slate-400">
                <a href="#hero" class="hover:text-cyan-400">Vision</a>
                <a href="#pipeline" class="hover:text-cyan-400">Flowchart</a>
                <a href="#simulator" class="hover:text-cyan-400">Simulator</a>
                <a href="https://www.futurehubcoworking.com" target="_blank" class="hover:text-cyan-400">futurehubcoworking.com</a>
            </div>

            <div class="text-[11px]">
                © 2026 SYNAPSE HUB. All Systems Nominal.
            </div>
        </div>
    </footer>

    <!-- Fullscreen Poster Modal Lightbox -->
    <div id="poster-modal" class="fixed inset-0 z-50 bg-black/90 backdrop-blur-md hidden items-center justify-center p-4">
        <div class="relative max-w-2xl w-full glass-panel rounded-3xl p-6 border border-cyan-400/60 shadow-poster-glow max-h-[92vh] overflow-y-auto">
            <div class="flex items-center justify-between pb-3 border-b border-cyan-500/20">
                <div class="flex items-center gap-2">
                    <i class="fa-solid fa-image text-cyan-400"></i>
                    <h3 class="font-mono-tech font-bold text-white text-sm uppercase">Official Poster Lightbox Preview</h3>
                </div>
                <button onclick="closeModal()" class="w-8 h-8 rounded-full bg-slate-900 border border-cyan-500/40 text-cyan-300 hover:bg-cyan-500 hover:text-black flex items-center justify-center transition">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <!-- Poster Content Inside Modal -->
            <div class="mt-4 p-6 bg-gradient-to-b from-[#090e24] via-[#050916] to-[#02050e] rounded-2xl border border-cyan-500/40 text-center">
                <span class="text-xs font-mono-tech text-cyan-400 font-extrabold uppercase tracking-widest">AI-POWERED CO-WORKING</span>
                <h2 class="text-3xl sm:text-4xl font-extrabold text-white uppercase font-mono-tech tracking-tight mt-1">
                    COLLABORATE WITH THE FUTURE
                </h2>
                <p class="text-xs text-slate-300 italic mt-1">Where Human Creativity Meets Intelligent Spaces.</p>

                <div class="my-6 p-4 rounded-xl bg-slate-950/80 border border-cyan-500/30 text-left">
                    <div class="text-xs font-mono-tech text-cyan-300 font-bold uppercase mb-3 text-center">
                        Integrated 4-Step Flowchart
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs font-mono-tech">
                        <div class="p-3 bg-slate-900 rounded-lg border border-cyan-500/20">
                            <b class="text-cyan-400">STEP 1: CONNECT & ACCESS</b>
                            <p class="text-[11px] text-slate-400 mt-1">Enter the space and instantly sync with the AI network.</p>
                        </div>
                        <div class="p-3 bg-slate-900 rounded-lg border border-purple-500/20">
                            <b class="text-purple-400">STEP 2: MEET YOUR AI ASSISTANT</b>
                            <p class="text-[11px] text-slate-400 mt-1">Receive custom project suggestions and matchmaking.</p>
                        </div>
                        <div class="p-3 bg-slate-900 rounded-lg border border-blue-500/20">
                            <b class="text-blue-400">STEP 3: REAL-TIME COLLABORATION</b>
                            <p class="text-[11px] text-slate-400 mt-1">Work alongside AI and peers at smart touch desks.</p>
                        </div>
                        <div class="p-3 bg-slate-900 rounded-lg border border-pink-500/20">
                            <b class="text-pink-400">STEP 4: SMART OPTIMIZATION</b>
                            <p class="text-[11px] text-slate-400 mt-1">AI automates routine tasks, maximizing output.</p>
                        </div>
                    </div>
                </div>

                <div class="flex items-center justify-between text-xs font-mono-tech text-slate-400 pt-2 border-t border-slate-800">
                    <span class="text-cyan-300 font-bold">DISCOVER THE NEXT EVOLUTION OF WORK</span>
                    <span>www.futurehubcoworking.com</span>
                </div>
            </div>

            <div class="mt-4 flex justify-end gap-3 font-mono-tech text-xs">
                <button onclick="copyPosterInfo()" class="px-4 py-2 rounded-xl border border-cyan-500/40 text-cyan-300 hover:bg-cyan-950 transition">
                    Copy Poster Info
                </button>
                <button onclick="closeModal()" class="px-4 py-2 rounded-xl bg-cyan-400 text-black font-bold">
                    Close Preview
                </button>
            </div>
        </div>
    </div>

    <script>
        // Web Audio Synthesizer
        let audioContext = null;
        let sfxEnabled = true;

        function getAudio() {
            if (!audioContext) {
                const AudioCtx = window.AudioContext || window.webkitAudioContext;
                if (AudioCtx) audioContext = new AudioCtx();
            }
            if (audioContext && audioContext.state === 'suspended') {
                audioContext.resume();
            }
            return audioContext;
        }

        function playAudioTone(freq = 600, duration = 0.08) {
            if (!sfxEnabled) return;
            try {
                const ctx = getAudio();
                if (!ctx) return;
                const osc = ctx.createOscillator();
                const gain = ctx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(freq, ctx.currentTime);
                osc.frequency.exponentialRampToValueAtTime(freq * 1.4, ctx.currentTime + duration);

                gain.gain.setValueAtTime(0.04, ctx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + duration);

                osc.connect(gain);
                gain.connect(ctx.destination);
                osc.start();
                osc.stop(ctx.currentTime + duration);
            } catch (e) {}
        }

        function toggleAudio() {
            sfxEnabled = !sfxEnabled;
            const btn = document.getElementById('sfx-toggle');
            const icon = document.getElementById('sfx-icon');
            if (sfxEnabled) {
                icon.className = 'fa-solid fa-volume-high mr-1';
                btn.innerHTML = '<i class="fa-solid fa-volume-high mr-1"></i> SFX: ON';
                showToast("Audio effects activated");
                playAudioTone(680);
            } else {
                icon.className = 'fa-solid fa-volume-xmark mr-1';
                btn.innerHTML = '<i class="fa-solid fa-volume-xmark mr-1"></i> SFX: OFF';
                showToast("Audio effects muted");
            }
        }

        // Flowchart Interactive Stages
        const stages = {
            1: {
                badge: "STAGE 01 TELEMETRY",
                title: "CONNECT & ACCESS ARCHITECTURE",
                desc: "SYNAPSE HUB eliminates the traditional check-in desk. Biometric beacons securely hydrate your workspace preferences: desk angle, display matrices, active git branches, and local neural model context buffers.",
                pills: ["Biometric Handshake <180ms", "Encrypted Cloud Context"],
                metricTitle: "SYNC EFFICIENCY",
                stat: "99.8%",
                width: "99%"
            },
            2: {
                badge: "STAGE 02 TELEMETRY",
                title: "AI ASSISTANT & PEER MATCHMAKING",
                desc: "Our spatial reasoning engine assesses your project's current bottlenecks in real time. It automatically pairs you with active founders with complementary skills and loads specialized domain agents into your workspace.",
                pills: ["Dynamic Skill Graphs", "Synthetic Pair Mentors", "Cross-Pod Mesh"],
                metricTitle: "PAIRING ACCURACY",
                stat: "95.4%",
                width: "95%"
            },
            3: {
                badge: "STAGE 03 TELEMETRY",
                title: "SPATIAL SMART DESK CO-CREATION",
                desc: "Holographic desks feature low-latency multi-touch surfaces allowing simultaneous 3D manipulation of product CADs, complex system diagrams, and distributed financial models alongside your team.",
                pills: ["4K Spatial Beam", "Gesture Tracking <2ms", "Spatial Multi-Touch"],
                metricTitle: "INTERACTION VELOCITY",
                stat: "98.2%",
                width: "98%"
            },
            4: {
                badge: "STAGE 04 TELEMETRY",
                title: "AUTONOMOUS OPTIMIZATION & SWARMS",
                desc: "Low-order administrative duties, meeting transcriptions, dependency audits, and CI/CD pipelines run in background micro-agents so human minds focus purely on breakthrough synthesis.",
                pills: ["Zero Operational Friction", "Autonomous Swarms", "Focus Shield active"],
                metricTitle: "CREATIVE FLOW MULTIPLIER",
                stat: "4.8x",
                width: "100%"
            }
        };

        function selectFlowStage(num) {
            playAudioTone(400 + num * 90);
            for (let i = 1; i <= 4; i++) {
                const el = document.getElementById(`step-card-${i}`);
                if (i === num) {
                    el.classList.add('border-cyan-400', 'shadow-neon-cyan');
                    el.classList.remove('border-slate-800');
                } else {
                    el.classList.remove('border-cyan-400', 'shadow-neon-cyan');
                    el.classList.add('border-slate-800');
                }
            }

            const data = stages[num];
            document.getElementById('stage-badge').innerText = data.badge;
            document.getElementById('stage-title').innerText = data.title;
            document.getElementById('stage-desc').innerText = data.desc;
            document.getElementById('metric-title').innerText = data.metricTitle;
            document.getElementById('stage-stat').innerText = data.stat;
            document.getElementById('stage-bar').style.width = data.width;

            const pillContainer = document.getElementById('stage-pills');
            pillContainer.innerHTML = data.pills.map(p => 
                `<span class="px-3 py-1 rounded-full bg-slate-900 border border-cyan-500/30 text-cyan-300">${p}</span>`
            ).join('');

            showToast(`Stage 0${num} Telemetry Loaded`);
        }

        // Persona Simulator Data
        const personas = {
            founder: {
                pod: "Pod Nexus-01: Executive Command",
                title: "Venture Speed & Capital Engine",
                desc: "Equipped with live market intelligence swarms, cap-table dynamic modeling, pitch deck audio synthesis, and autonomous founder matching.",
                agents: [
                    { name: 'VentureBot-4', icon: 'fa-microchip' },
                    { name: 'Runway Sentinel', icon: 'fa-coins' },
                    { name: 'DeckArchitect AI', icon: 'fa-file-waveform' }
                ],
                score: "96%",
                stroke: "96, 100",
                label: "Flow State Maximized"
            },
            designer: {
                pod: "Pod Chroma-04: Spatial Design Studio",
                title: "Generative UI/UX & 3D Spatial Canvas",
                desc: "Interactive spatial canvas with gesture modeling, lighting simulators, real-time user journey diffusion, and automated responsive variant generators.",
                agents: [
                    { name: 'SpatialDiffusion-X', icon: 'fa-palette' },
                    { name: 'TokenSync Engine', icon: 'fa-wand-magic' },
                    { name: 'DesignSystem Auditor', icon: 'fa-cubes' }
                ],
                score: "98%",
                stroke: "98, 100",
                label: "Creative Velocity Peaked"
            },
            developer: {
                pod: "Pod Matrix-09: Quietude Zero-G",
                title: "Autonomous Dev Environment & Cluster",
                desc: "Equipped with synthetic pair programmers, continuous micro-benchmarking, automated memory leak tracing, and zero-latency terminal mirrors.",
                agents: [
                    { name: 'KernelCoPilot', icon: 'fa-terminal' },
                    { name: 'BugHunter Agent', icon: 'fa-bug' },
                    { name: 'ShaderCompiler AI', icon: 'fa-bolt' }
                ],
                score: "95%",
                stroke: "95, 100",
                label: "Deep Work Zone Locked"
            },
            marketer: {
                pod: "Pod Pulse-02: Global Audience Hub",
                title: "Predictive Campaign & Live Sentiment Room",
                desc: "Real-time world sentiment stream monitors, copy variation multi-armed bandits, and cross-channel autonomous campaign dispatchers.",
                agents: [
                    { name: 'SentimentRadar', icon: 'fa-chart-pie' },
                    { name: 'CopyMatrix Engine', icon: 'fa-bullhorn' },
                    { name: 'OmniTracker Bot', icon: 'fa-network-wired' }
                ],
                score: "92%",
                stroke: "92, 100",
                label: "High Conversion Synergy"
            }
        };

        function setPersona(role) {
            playAudioTone(540);
            ['founder', 'designer', 'developer', 'marketer'].forEach(r => {
                const b = document.getElementById(`role-${r}`);
                if (r === role) {
                    b.className = 'p-3.5 rounded-xl border border-cyan-400 bg-cyan-500/20 text-white font-bold transition flex items-center justify-center gap-2';
                } else {
                    b.className = 'p-3.5 rounded-xl border border-slate-800 bg-slate-900/60 text-slate-400 font-bold transition flex items-center justify-center gap-2 hover:border-cyan-400';
                }
            });

            const p = personas[role];
            document.getElementById('sim-pod').innerText = p.pod;
            document.getElementById('sim-title').innerText = p.title;
            document.getElementById('sim-desc').innerText = p.desc;
            document.getElementById('sim-score-num').innerText = p.score;
            document.getElementById('sim-score-label').innerText = p.label;
            document.getElementById('sim-score-circle').setAttribute('stroke-dasharray', p.stroke);

            const agentsCont = document.getElementById('sim-agents');
            agentsCont.innerHTML = p.agents.map(a => 
                `<span class="px-3 py-1 rounded-lg bg-cyan-950/60 border border-cyan-400/40 text-cyan-300 flex items-center gap-1.5">
                    <i class="fa-solid ${a.icon}"></i> ${a.name}
                </span>`
            ).join('');

            showToast(`Preset: ${p.pod}`);
        }

        // Modal Controls
        function openModal() {
            playAudioTone(640);
            document.getElementById('poster-modal').classList.remove('hidden');
            document.getElementById('poster-modal').classList.add('flex');
        }

        function closeModal() {
            playAudioTone(380);
            document.getElementById('poster-modal').classList.add('hidden');
            document.getElementById('poster-modal').classList.remove('flex');
        }

        function copyPosterInfo() {
            playAudioTone(700);
            const text = "SYNAPSE HUB | AI-Powered Co-Working | Collaborate With The Future: Step 1: Connect & Access -> Step 2: Meet Your AI Assistant -> Step 3: Real-Time Collaboration -> Step 4: Smart Optimization. Visit: www.futurehubcoworking.com";
            const dummy = document.createElement("input");
            document.body.appendChild(dummy);
            dummy.value = text;
            dummy.select();
            document.execCommand('copy');
            document.body.removeChild(dummy);
            showToast("Poster brief copied to clipboard!");
        }

        function handleJoin(e) {
            e.preventDefault();
            playAudioTone(880, 0.15);
            showToast("Founding Access Request Synced! Check your inbox.");
            e.target.reset();
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-text').innerText = msg;
            toast.classList.remove('translate-y-24', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');

            setTimeout(() => {
                toast.classList.add('translate-y-24', 'opacity-0');
                toast.classList.remove('translate-y-0', 'opacity-100');
            }, 3000);
        }
    </script>
</body>
</html>
```
