<section class="mt-32 mb-20 reveal">
    <div class="glass-card overflow-hidden border-cyan-500/20 bg-black/40">
        <div class="bg-white/5 px-4 py-2 border-b border-white/5 flex items-center justify-between">
            <div class="flex gap-1.5">
                <div class="w-2.5 h-2.5 rounded-full bg-red-500/50"></div>
                <div class="w-2.5 h-2.5 rounded-full bg-yellow-500/50"></div>
                <div class="w-2.5 h-2.5 rounded-full bg-green-500/50"></div>
            </div>
            <span class="text-[9px] font-mono text-gray-500 uppercase tracking-widest">System_Log_v3.0.sh</span>
        </div>
        
        <div class="p-6 font-mono text-xs md:text-sm leading-relaxed min-h-[180px]">
            <div id="log-container" class="space-y-1">
                <div class="text-cyan-500/80">>> Initializing DeBeatzGH Digital Ecosystem...</div>
                <div class="text-gray-500">[OK] Canvas Alpha-Layer Loaded.</div>
                <div class="text-gray-500">[OK] AI Hub Nodes Synchronized.</div>
                <div id="typing-log" class="text-white"></div>
                <span class="inline-block w-2 h-4 bg-cyan-500 animate-pulse align-middle ml-1"></span>
            </div>
        </div>
    </div>
</section>

<script>
    // SYSTEM LOG TYPING ENGINE
    const logMessages = [
        "Updating AI Agent prompt libraries...",
        "Syncing E-Hub with latest digital assets.",
        "Scanning collaborator network for new nodes.",
        "Optimizing glassmorphism UI rendering...",
        "System Status: All systems operational.",
        "Welcome, User. Access granted to Decode AI Kit."
    ];

    let messageIndex = 0;
    let charIndex = 0;
    const typingElement = document.getElementById('typing-log');

    function typeLog() {
        if (messageIndex < logMessages.length) {
            let currentMsg = logMessages[messageIndex];
            
            if (charIndex < currentMsg.length) {
                typingElement.innerHTML += currentMsg.charAt(charIndex);
                charIndex++;
                setTimeout(typeLog, 40); // Typing speed
            } else {
                // Message finished
                setTimeout(() => {
                    typingElement.innerHTML += `<br><span class="text-gray-500">[LOG] </span>`;
                    charIndex = 0;
                    messageIndex++;
                    typeLog();
                }, 1500); // Pause between lines
            }
        }
    }

    // Trigger typing when section is revealed
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                setTimeout(typeLog, 500);
                observer.unobserve(entry.target);
            }
        });
    });

    observer.observe(document.getElementById('log-container'));
</script>


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | AI Command Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap');

        :root {
            --accent: #00f2ff;
            --bg-deep: #050507;
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(0, 242, 255, 0.15);
        }

        body {
            background-color: var(--bg-deep);
            color: #f1f5f9;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
        }

        /* --- FLOATING COMMAND BANNER --- */
        .cmd-banner {
            position: fixed;
            top: 20px; left: 50%;
            transform: translateX(-50%);
            width: 90%; max-width: 400px;
            height: 54px;
            background: rgba(10, 10, 12, 0.8);
            backdrop-filter: blur(20px);
            border: 1px solid var(--border);
            border-radius: 16px;
            display: flex; align-items: center;
            padding: 0 10px 0 20px;
            z-index: 10001;
            box-shadow: 0 20px 40px rgba(0,0,0,0.6), 0 0 20px rgba(0, 242, 255, 0.1);
        }

        /* --- CANVAS BACKGROUND --- */
        #heroCanvas {
            position: fixed; inset: 0;
            pointer-events: none;
            z-index: 0;
            opacity: 0.6;
        }

        /* --- CAROUSEL & CARDS --- */
        .hub-carousel {
            display: flex; gap: 24px;
            overflow-x: auto; padding: 20px 0;
            scroll-snap-type: x mandatory;
            scrollbar-width: none;
        }
        .hub-carousel::-webkit-scrollbar { display: none; }

        .hub-card {
            min-width: 300px;
            background: var(--glass);
            border: 1px solid rgba(255,255,255,0.05);
            border-radius: 24px;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            scroll-snap-align: center;
        }
        .hub-card:hover {
            border-color: var(--accent);
            transform: translateY(-10px) scale(1.02);
            background: rgba(0, 242, 255, 0.02);
        }

        /* --- LAZY LOAD ANIMATION --- */
        .reveal {
            opacity: 0; transform: translateY(30px);
            transition: all 0.8s ease-out;
        }
        .reveal.active { opacity: 1; transform: translateY(0); }

        /* --- FULLSCREEN OVERLAY --- */
        #hub-overlay {
            position: fixed; inset: 0;
            background: var(--bg-deep);
            display: none; flex-direction: column;
            z-index: 20000;
            animation: slideUp 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        @keyframes slideUp {
            from { transform: translateY(100%); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .slider-text {
            animation: slideText 8s infinite;
        }
        @keyframes slideText {
            0%, 25% { transform: translateY(0); }
            30%, 55% { transform: translateY(-24px); }
            60%, 85% { transform: translateY(-48px); }
            100% { transform: translateY(0); }
        }
    </style>
</head>
<body>

    <canvas id="heroCanvas"></canvas>

    <nav class="cmd-banner">
        <div class="flex-grow overflow-hidden h-6">
            <div class="slider-text flex flex-col font-bold text-[11px] uppercase tracking-widest text-cyan-400">
                <span class="h-6 flex items-center">● System: Online</span>
                <span class="h-6 flex items-center">● Explore AI Modules</span>
                <span class="h-6 flex items-center">● Access E-Hub Nodes</span>
            </div>
        </div>
        <button onclick="openFrame('https://debeatzgh1.github.io/Home-/')" class="bg-cyan-500 text-black px-5 py-2 rounded-xl text-[10px] font-black uppercase hover:bg-white transition-all">
            Launch
        </button>
    </nav>

    <main class="relative z-10 pt-32 px-6 max-w-6xl mx-auto">
        <header class="mb-16 reveal">
            <h1 class="text-4xl md:text-6xl font-black tracking-tighter mb-4">
                THE <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-500">DIGITAL COMMAND</span> HUB
            </h1>
            <p class="text-gray-400 max-w-xl">Welcome, Strategist. Manage your AI agents, tools, and digital ecosystems from a single synchronized interface.</p>
        </header>

        <div class="hub-carousel reveal" style="transition-delay: 200ms;">
            
            <div class="hub-card group">
                <div class="h-48 overflow-hidden relative">
                    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/createaboldeye-catchingsocialmediaflyerfeaturingtwosplitsectionsorcharacters2273204207149586064.jpg" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                </div>
                <div class="p-6">
                    <h3 class="font-bold text-xl mb-2 text-cyan-400">AI Agent</h3>
                    <p class="text-xs text-gray-500 mb-6">Autonomous task management and creative intelligence.</p>
                    <button onclick="openFrame('https://debeatzgh1.github.io/ai-chat/')" class="w-full py-3 rounded-xl border border-white/10 text-xs font-bold hover:bg-cyan-500 hover:text-black transition">Sync Node</button>
                </div>
            </div>

            <div class="hub-card group">
                <div class="h-48 overflow-hidden relative">
                    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamoderntech-inspiredlogoforadigitalcontenthubcalledappdategh4933013559151235986.jpg" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                </div>
                <div class="p-6">
                    <h3 class="font-bold text-xl mb-2 text-purple-400">E. Hub</h3>
                    <p class="text-xs text-gray-500 mb-6">Digital content distribution and application updates.</p>
                    <button onclick="openFrame('https://debeatzgh1.github.io/appdategh/')" class="w-full py-3 rounded-xl border border-white/10 text-xs font-bold hover:bg-purple-500 hover:text-black transition">Access Hub</button>
                </div>
            </div>

            <div class="hub-card group">
                <div class="h-48 overflow-hidden relative">
                    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251121-103715_12380909417515729112.png" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                </div>
                <div class="p-6">
                    <h3 class="font-bold text-xl mb-2 text-green-400">Network</h3>
                    <p class="text-xs text-gray-500 mb-6">Connect with creators and strategic digital partners.</p>
                    <button onclick="openFrame('https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/')" class="w-full py-3 rounded-xl border border-white/10 text-xs font-bold hover:bg-green-500 hover:text-black transition">View Network</button>
                </div>
            </div>

        </div>
    </main>

    <div id="hub-overlay">
        <div class="h-14 border-b border-white/10 flex items-center justify-between px-6 bg-black">
            <span class="text-[10px] font-black tracking-widest text-cyan-500 uppercase">External Node Active</span>
            <button onclick="closeFrame()" class="text-[10px] font-bold text-gray-500 hover:text-white px-4 py-1 border border-white/10 rounded-lg transition">Close Node [Esc
