
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>G-Dev Portfolio | Hiring Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Google+Sans:wght@400;500;700&display=swap');

        :root {
            --g-blue: #8ab4f8;
            --g-green: #34A853;
            --dark-bg: #1a1c1e;
            --dark-card: #2d2f31;
            --glass-border: rgba(255, 255, 255, 0.08);
        }

        body { font-family: 'Google Sans', sans-serif; background: #121212; margin: 0; }

        /* 1. LAUNCHER WITH ENTRANCE ANIMATION */
        #gdev-launcher {
            position: fixed; left: 20px; top: 50%; transform: translateY(-50%);
            display: flex; align-items: center; gap: 12px;
            background: var(--dark-card); padding: 8px 18px 8px 8px;
            border-radius: 40px; cursor: pointer; z-index: 9999;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid var(--glass-border);
            animation: slide-wobble 1.2s ease forwards;
            opacity: 0;
        }

        @keyframes slide-wobble {
            0% { transform: translateY(-50%) translateX(-100px); opacity: 0; }
            60% { transform: translateY(-50%) translateX(10px); opacity: 1; }
            80% { transform: translateY(-50%) translateX(-2px); }
            100% { transform: translateY(-50%) translateX(0); opacity: 1; }
        }

        #gdev-launcher:hover { transform: translateY(-50%) scale(1.08) translateX(5px); border-color: var(--g-blue); }

        .dev-avatar {
            width: 30px; height: 30px; background: #121212; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            border: 2px solid var(--g-blue); color: var(--g-blue); position: relative;
        }

        .status-dot {
            position: absolute; bottom: 2px; right: 2px; width: 10px; height: 10px;
            background: var(--g-green); border-radius: 50%; border: 2px solid var(--dark-card);
        }

        .status-glow {
            position: absolute; inset: 0; background: var(--g-green);
            border-radius: 50%; animation: status-pulse 2s infinite;
        }

        @keyframes status-pulse { 0% { transform: scale(1); opacity: 0.8; } 100% { transform: scale(2.5); opacity: 0; } }

        /* 2. OVERLAY MODAL */
        #gdev-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.85);
            backdrop-filter: blur(12px); display: none; z-index: 10000;
            justify-content: center; align-items: center; padding: 20px;
            opacity: 0; transition: opacity 0.4s ease;
        }

        #gdev-overlay.active { display: flex; opacity: 1; }

        .gdev-modal {
            width: 100%; max-width: 950px; height: 92vh;
            background: var(--dark-bg); border-radius: 28px;
            display: flex; flex-direction: column; overflow: hidden;
            border: 1px solid var(--glass-border); position: relative;
            transform: scale(0.9); transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        #gdev-overlay.active .gdev-modal { transform: scale(1); }

        /* 3. IFRAME & FOOTER */
        #gdev-frame { flex-grow: 1; width: 100%; border: none; background: #fff; }

        .close-gdev {
            position: absolute; top: 20px; right: 25px; width: 30px; height: 30px;
            background: var(--dark-card); border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; color: #fff; z-index: 20; transition: 0.3s;
        }
        .close-gdev:hover { background: #ff4d4d; }

        .hire-btn {
            background: var(--g-green); color: white; padding: 8px 18px;
            border-radius: 20px; font-size: 11px; font-weight: 800;
            text-transform: uppercase; letter-spacing: 1px; display: flex;
            align-items: center; gap: 8px; transition: 0.3s;
            box-shadow: 0 4px 15px rgba(52, 168, 83, 0.3);
        }
        .hire-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(52, 168, 83, 0.4); background: #2e964a; }

        @media (max-width: 768px) {
            .gdev-modal { height: 100vh; border-radius: 0; }
            .footer-controls { flex-direction: column; gap: 10px; padding: 15px; }
        }
    </style>
</head>
<body>

    <div id="gdev-launcher" onclick="toggleGDev(true)">
        <div class="dev-avatar">
            <i class="fab fa-google"></i>
            <div class="status-dot"><div class="status-glow"></div></div>
        </div>
        <div class="hidden sm:block">
            <div class="flex items-center gap-2">
                <span class="text-[9px] text-[#34A853] font-bold uppercase tracking-widest">Active</span>
            </div>
            <p class="text-[14px] font-medium text-gray-200">@debeatzgh</p>
        </div>
    </div>

    <div id="gdev-overlay">
        <div class="gdev-modal">
            <div class="close-gdev" onclick="toggleGDev(true)"><i class="fas fa-times"></i></div>
            <iframe id="gdev-frame" src=""></iframe>
            <div class="footer-controls p-4 bg-[#1a1c1e] border-t border-white/5 flex justify-between items-center px-8">
                <span class="text-[9px] text-gray-600 font-bold uppercase tracking-[2px]">G-Dev Protocol v4.0</span>
                <div class="flex items-center gap-3">
                    <button id="copy-btn" class="text-[11px] text-[#8ab4f8] font-bold px-4 py-2 hover:text-white transition" onclick="copyProfileLink()">
                        Copy Profile
                    </button>
                    <a href="https://wa.me/233549757544" target="_blank" class="hire-btn">
                        <i class="fas fa-briefcase"></i> Contact Me
                    </a>
                </div>
            </div>
        </div>
    </div>

    <script>
        const overlay = document.getElementById('gdev-overlay');
        const frame = document.getElementById('gdev-frame');
        const profileUrl = "https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header";
        
        let autoPopTimer = null;
        let isUserInteracted = false;

        function toggleGDev(isManual = false) {
            // If user clicks, stop all automatic pop-ups/closings
            if (isManual) {
                isUserInteracted = true;
                clearTimeout(autoPopTimer);
            }

            if (overlay.classList.contains('active')) {
                overlay.classList.remove('active');
                setTimeout(() => { 
                    overlay.style.display = 'none'; 
                    frame.src = ""; 
                }, 400);
                document.body.style.overflow = 'auto';
            } else {
                overlay.style.display = 'flex';
                setTimeout(() => overlay.classList.add('active'), 10);
                frame.src = profileUrl;
                document.body.style.overflow = 'hidden';
            }
        }

        // --- AUTOMATIC ENGINE ---
        window.addEventListener('load', () => {
            // 1. Auto Open after 6 seconds
            autoPopTimer = setTimeout(() => {
                if (!isUserInteracted) {
                    toggleGDev();
                    
                    // 2. Auto Close after 6 more seconds
                    autoPopTimer = setTimeout(() => {
                        if (!isUserInteracted) toggleGDev();
                    }, 6000);
                }
            }, 6000);
        });

        async function copyProfileLink() {
            await navigator.clipboard.writeText(profileUrl);
            const btn = document.getElementById('copy-btn');
            btn.innerText = "Copied!";
            setTimeout(() => { btn.innerText = "Copy Profile"; }, 2000);
        }

        overlay.onclick = (e) => { if (e.target === overlay) toggleGDev(true); };
    </script>
</body>
</html>




<div id="firebase-mini-banner" class="firebase-node-mini">
    <div class="mini-content">
        <div class="status-indicator">
            <span class="pulse-dot"></span>
        </div>
        <div class="mini-text">
            <span class="label">Internal Build</span>
            <span class="version">v2.4-stable</span>
        </div>
    </div>
    <button onclick="openFirebaseNode()" class="mini-action-btn">
        <i class="fas fa-download"></i>
    </button>
</div>

<style>
    .firebase-node-mini {
        position: fixed;
        bottom: 25px;
        left: 25px; /* Positioned left to avoid clashing with the 'Suggest' button */
        width: 180px;
        height: 42px;
        background: rgba(10, 10, 12, 0.85);
        backdrop-filter: blur(12px);
        -webkit-backdrop-filter: blur(12px);
        border: 1px solid rgba(0, 242, 255, 0.2);
        border-radius: 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 6px 0 12px;
        z-index: 9999;
        box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);
        transition: all 0.3s ease;
    }

    .firebase-node-mini:hover {
        border-color: #00f2ff;
        transform: translateY(-3px);
    }

    .mini-content {
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .status-indicator {
        position: relative;
        display: flex;
        align-items: center;
    }

    .pulse-dot {
        width: 6px;
        height: 6px;
        background: #00f2ff;
        border-radius: 50%;
        box-shadow: 0 0 8px #00f2ff;
        animation: miniPulse 2s infinite;
    }

    @keyframes miniPulse {
        0% { transform: scale(1); opacity: 1; }
        50% { transform: scale(1.5); opacity: 0.5; }
        100% { transform: scale(1); opacity: 1; }
    }

    .mini-text {
        display: flex;
        flex-direction: column;
    }

    .mini-text .label {
        font-size: 8px;
        font-weight: 900;
        text-transform: uppercase;
        color: #475569;
        letter-spacing: 1px;
    }

    .mini-text .version {
        font-size: 10px;
        font-family: monospace;
        color: #f1f5f9;
        font-weight: bold;
    }

    .mini-action-btn {
        background: #00f2ff;
        color: #000;
        border: none;
        width: 30px;
        height: 30px;
        border-radius: 8px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 12px;
        cursor: pointer;
        transition: 0.2s;
    }

    .mini-action-btn:hover {
        background: #fff;
        transform: scale(1.1);
    }

    /* Integration with your Master Overlay System */
</style>

<script>
    function openFirebaseNode() {
        // Using the same openLink/openFrame logic we built for your Hub
        if (typeof openLink === "function") {
            openLink('https://appdistribution.firebase.dev/i/dc2da2d4d3766b8a');
        } else if (typeof openFrame === "function") {
            openFrame('https://appdistribution.firebase.dev/i/dc2da2d4d3766b8a');
        } else {
            // Fallback for standalone use
            window.open('https://appdistribution.firebase.dev/i/dc2da2d4d3766b8a', '_blank');
        }
    }
</script>


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Digital Command Center</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap');

        :root {
            --accent: #00f2ff;
            --bg-deep: #050507;
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(0, 242, 255, 0.2);
            --ui-glow: rgba(0, 242, 255, 0.4);
        }

        body {
            background-color: var(--bg-deep);
            color: #f0f6fc;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            margin: 0;
        }

        /* --- BACKGROUND CANVAS --- */
        #bgCanvas {
            position: fixed; inset: 0;
            z-index: 0;
            pointer-events: none;
            opacity: 0.5;
        }

        /* --- FLOATING BROWSER BANNER --- */
        .ui-browser-banner {
            position: fixed;
            top: 15px; left: 50%;
            transform: translateX(-50%);
            width: 90%; max-width: 340px;
            height: 50px;
            background: rgba(10, 10, 12, 0.9);
            backdrop-filter: blur(15px);
            border: 1px solid var(--border);
            border-radius: 14px;
            display: flex; align-items: center;
            justify-content: space-between;
            padding: 0 10px 0 18px;
            z-index: 10001;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.8), 0 0 15px var(--ui-glow);
        }

        .slider-box { flex: 1; overflow: hidden; height: 22px; }
        .slider-content {
            display: flex; flex-direction: column;
            animation: slideText 7s infinite cubic-bezier(0.65, 0, 0.35, 1);
        }
        @keyframes slideText {
            0%, 25% { transform: translateY(0); }
            33%, 58% { transform: translateY(-22px); }
            66%, 91% { transform: translateY(-44px); }
            100% { transform: translateY(0); }
        }

        /* --- CAROUSEL & CARDS --- */
        .hub-carousel {
            display: flex; gap: 20px;
            overflow-x: auto; padding: 20px 0;
            scroll-snap-type: x mandatory;
            scrollbar-width: none;
        }
        .hub-carousel::-webkit-scrollbar { display: none; }

        .card {
            min-width: 290px;
            background: var(--glass);
            border: 1px solid rgba(255, 255, 255, 0.06);
            border-radius: 22px;
            overflow: hidden;
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            scroll-snap-align: center;
        }
        .card:hover {
            transform: translateY(-8px);
            border-color: var(--accent);
            box-shadow: 0 15px 45px rgba(0, 242, 255, 0.1);
        }

        /* --- OVERLAY IFRAME --- */
        #master-overlay {
            position: fixed; inset: 0;
            background: rgba(0, 0, 0, 0.98);
            display: none; flex-direction: column;
            z-index: 20000;
            animation: overlayFade 0.4s ease;
        }
        @keyframes overlayFade {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        /* --- LAZY LOAD --- */
        .reveal {
            opacity: 0; transform: translateY(40px);
            transition: all 0.9s ease-out;
        }
        .reveal.active { opacity: 1; transform: translateY(0); }

        .pulse-node {
            width: 7px; height: 7px;
            background: var(--accent);
            border-radius: 50%;
            box-shadow: 0 0 10px var(--accent);
        }
    </style>
</head>
<body>

    <canvas id="bgCanvas"></canvas>

    <div class="ui-browser-banner">
        <div class="slider-box">
            <div class="slider-content font-bold text-[10px] uppercase tracking-widest text-cyan-400">
                <span class="h-[22px] flex items-center gap-3"><div class="pulse-node"></div> AI Interface Active</span>
                <span class="h-[22px] flex items-center gap-3"><div class="pulse-node"></div> Digital Hub Online</span>
                <span class="h-[22px] flex items-center gap-3"><div class="pulse-node"></div> Syncing Ecosystem</span>
            </div>
        </div>
        <button onclick="openLink('https://debeatzgh1.github.io/firebase-front-end-components/')" class="bg-cyan-500 text-black px-4 py-2 rounded-lg text-[9px] font-black uppercase hover:bg-white transition">Explore</button>
    </div>

    <main class="relative z-10 pt-36 px-6 max-w-6xl mx-auto">
        <section class="mb-16 reveal">
            <h1 class="text-5xl md:text-7xl font-black tracking-tighter mb-4 leading-none">
                DIGITAL <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-500">ECOSYSTEM.</span>
            </h1>
            <p class="text-gray-400 max-w-lg text-sm md:text-base">
                Synchronized access to AI agents, digital tools, and strategic collaboration nodes. One interface. Infinite possibilities.
            </p>
        </section>

        <div class="hub-carousel reveal" style="transition-delay: 200ms;">
            
            <div class="card">
                <div class="h-44 relative overflow-hidden">
                    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/createaboldeye-catchingsocialmediaflyerfeaturingtwosplitsectionsorcharacters2273204207149586064.jpg" class="w-full h-full object-cover">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                </div>
                <div class="p-6">
                    <h3 class="font-bold text-lg text-cyan-400 mb-1">AI Agent</h3>
                    <p class="text-[11px] text-gray-500 leading-relaxed mb-5">Next-gen automation and conversational intelligence tailored for your workflow.</p>
                    <button onclick="openLink('https://debeatzgh1.github.io/ai-chat/')" class="w-full py-3 bg-white/5 border border-white/10 rounded-xl text-[10px] font-bold uppercase tracking-widest hover:bg-cyan-500 hover:text-black transition">Initialize Node</button>
                </div>
            </div>

            <div class="card">
                <div class="h-44 relative overflow-hidden">
                    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/amoderncleanworkspaceshowcasingfront-endcodesnippetsonasleeklaptopscreensurroundedbytailwindcsslogoshtml5andfirebaseicons5315964892159237038.jpg" class="w-full h-full object-cover">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                </div>
                <div class="p-6">
                    <h3 class="font-bold text-lg text-purple-400 mb-1">Tools Hub</h3>
                    <p class="text-[11px] text-gray-500 leading-relaxed mb-5">A curated library of productivity widgets and developer resources.</p>
                    <button onclick="openLink('https://debeatzgh1.github.io/debeatzgh/')" class="w-full py-3 bg-white/5 border border-white/10 rounded-xl text-[10px] font-bold uppercase tracking-widest hover:bg-purple-500 hover:text-black transition">Open Toolkit</button>
                </div>
            </div>

            <div class="card">
                <div class="h-44 relative overflow-hidden">
                    <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamoderntech-inspiredlogoforadigitalcontenthubcalledappdategh4933013559151235986.jpg" class="w-full h-full object-cover">
                    <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
                </div>
                <div class="p-6">
                    <h3 class="font-bold text-lg text-green-400 mb-1">E. Hub</h3>
                    <p class="text-[11px] text-gray-500 leading-relaxed mb-5">Stay updated with digital content and software release cycles.</p>
                    <button onclick="openLink('https://debeatzgh1.github.io/appdategh/')" class="w-full py-3 bg-white/5 border border-white/10 rounded-xl text-[10px] font-bold uppercase tracking-widest hover:bg-green-500 hover:text-black transition">Launch Hub</button>
                </div>
            </div>

        </div>

        <section class="mt-20 mb-20 reveal">
            <div class="bg-black/40 border border-white/5 rounded-2xl overflow-hidden font-mono text-[10px] md:text-xs">
                <div class="bg-white/5 px-4 py-2 border-b border-white/5 flex gap-1.5">
                    <div class="w-2 h-2 rounded-full bg-red-500/50"></div>
                    <div class="w-2 h-2 rounded-full bg-yellow-500/50"></div>
                    <div class="w-2 h-2 rounded-full bg-green-500/50"></div>
                </div>
                <div class="p-5 space-y-1" id="log-container">
                    <div class="text-cyan-500/80">>> system_auth: Success</div>
                    <div class="text-gray-500">>> node_sync: [##########] 100%</div>
                    <div id="typewriter" class="text-white"></div>
                    <span class="inline-block w-1.5 h-3 bg-cyan-500 animate-pulse"></span>
                </div>
            </div>
        </section>
    </main>

    <div id="master-overlay">
        <div class="h-14 border-b border-white/10 flex items-center justify-between px-6 bg-black">
            <span class="text-[9px] font-black uppercase tracking-widest text-cyan-400">Node_Stream // Active_Session</span>
            <button onclick="closeLink()" class="px-4 py-1.5 border border-white/10 rounded-lg text-[9px] font-bold text-gray-400 hover:text-white transition">CLOSE [ESC]</button>
        </div>
        <iframe id="master-frame" class="w-full flex-grow bg-white"></iframe>
    </div>

    <button onclick="openLink('https://form.svhrt.com/60f4a0aeedc1993c8c7b3989')" class="fixed bottom-6 right-6 z-50 bg-cyan-500 text-black px-6 py-3 rounded-full font-black text-xs shadow-2xl shadow-cyan-500/20 hover:scale-110 transition animate-bounce">
        🚀 SUGGEST
    </button>

    <script>
        // --- CANVAS ANIMATION ---
        const canvas = document.getElementById('bgCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function initCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            particles = Array.from({length: 60}, () => ({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height,
                vX: (Math.random() - 0.5) * 0.4,
                vY: (Math.random() - 0.5) * 0.4
            }));
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = 'rgba(0, 242, 255, 0.4)';
            particles.forEach(p => {
                p.x += p.vX; p.y += p.vY;
                if(p.x < 0 || p.x > canvas.width) p.vX *= -1;
                if(p.y < 0 || p.y > canvas.height) p.vY *= -1;
                ctx.beginPath(); ctx.arc(p.x, p.y, 1, 0, Math.PI * 2); ctx.fill();
            });
            requestAnimationFrame(animate);
        }

        // --- OVERLAY SYSTEM ---
        function openLink(url) {
            document.getElementById('master-frame').src = url;
            document.getElementById('master-overlay').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }
        function closeLink() {
            document.getElementById('master-overlay').style.display = 'none';
            document.getElementById('master-frame').src = '';
            document.body.style.overflow = 'auto';
        }

        // --- TYPEWRITER ---
        const messages = ["Accessing Digital Ecosystem...", "Updating AI Prompt Libraries...", "Syncing with Collaborator Nodes...", "System Ready. Welcome, Architect."];
        let mIdx = 0, cIdx = 0;
        function type() {
            if (mIdx < messages.length) {
                if (cIdx < messages[mIdx].length) {
                    document.getElementById('typewriter').innerHTML += messages[mIdx].charAt(cIdx);
                    cIdx++; setTimeout(type, 50);
                } else {
                    setTimeout(() => {
                        document.getElementById('typewriter').innerHTML += "<br>> ";
                        mIdx++; cIdx = 0; type();
                    }, 1500);
                }
            }
        }

        // --- LAZY LOAD & INIT ---
        window.addEventListener('scroll', () => {
            document.querySelectorAll('.reveal').forEach(el => {
                if(el.getBoundingClientRect().top < window.innerHeight - 100) el.classList.add('active');
            });
        });

        window.addEventListener('resize', initCanvas);
        initCanvas(); animate(); type();
        document.addEventListener('keydown', (e) => { if(e.key === "Escape") closeLink(); });
        setTimeout(() => document.querySelector('.reveal').classList.add('active'), 100);
    </script>
</body>
</html>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --ui-accent: #00f2ff; /* Cyber Cyan */
            --ui-bg: rgba(10, 10, 12, 0.9);
            --ui-glow: rgba(0, 242, 255, 0.4);
            --text-light: #f0f6fc;
        }

        /* --- TOPMOST FLOATING BANNER --- */
        .ui-browser-banner {
            position: fixed;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            width: 310px;
            height: 48px;
            background: var(--ui-bg);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 1px solid rgba(0, 242, 255, 0.2);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 8px 0 15px;
            z-index: 10001; /* Higher than other banners */
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.8), 0 0 10px var(--ui-glow);
            overflow: hidden;
        }

        /* Auto-Slide Text Container */
        .ui-slider-box {
            flex: 1;
            overflow: hidden;
            position: relative;
            height: 20px;
            margin-right: 10px;
        }

        .ui-slider-content {
            display: flex;
            flex-direction: column;
            animation: slideText 6s cubic-bezier(0.645, 0.045, 0.355, 1) infinite;
        }

        .ui-slider-content span {
            height: 20px;
            font-family: 'Monaco', 'Consolas', monospace;
            font-size: 0.75rem;
            color: var(--ui-accent);
            display: flex;
            align-items: center;
            gap: 6px;
            letter-spacing: 1px;
            font-weight: bold;
        }

        /* Action Button */
        .ui-open-btn {
            background: var(--ui-accent);
            color: #000;
            border: none;
            padding: 6px 14px;
            border-radius: 6px;
            font-size: 0.7rem;
            font-weight: 900;
            cursor: pointer;
            text-transform: uppercase;
            transition: 0.3s ease;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .ui-open-btn:hover {
            background: #fff;
            box-shadow: 0 0 15px #fff;
            transform: scale(1.05);
        }

        /* --- OVERLAY IFRAME --- */
        #ui-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.95);
            display: none;
            flex-direction: column;
            z-index: 20000;
            animation: overlayFade 0.4s ease;
        }

        .ui-overlay-nav {
            height: 50px;
            background: #111;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 20px;
            border-bottom: 2px solid var(--ui-accent);
        }

        .ui-frame {
            width: 100%;
            flex-grow: 1;
            border: none;
            background: #fff;
        }

        /* --- ANIMATIONS --- */
        @keyframes slideText {
            0%, 20% { transform: translateY(0); }
            33%, 53% { transform: translateY(-20px); }
            66%, 86% { transform: translateY(-40px); }
            100% { transform: translateY(0); }
        }

        @keyframes overlayFade {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .pulse-icon {
            width: 6px;
            height: 6px;
            background: var(--ui-accent);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--ui-accent);
        }
    </style>
</head>
<body>

    <div class="ui-browser-banner">
        <div class="ui-slider-box">
            <div class="ui-slider-content">
                <span><div class="pulse-icon"></div> Browse UI & Interfaces</span>
                <span><div class="pulse-icon"></div> Discover Experience</span>
                <span><div class="pulse-icon"></div> Portfolio Access</span>
            </div>
        </div>
        <button class="ui-open-btn" onclick="openUIHub()">
            Explore <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
        </button>
    </div>

    <div id="ui-overlay">
        <div class="ui-overlay-nav">
            <span style="color: var(--ui-accent); font-family: monospace; font-weight: bold; font-size: 0.8rem;">DEBEATZGH // UI_INTERFACES</span>
            <button onclick="closeUIHub()" style="background:none; border: 1px solid #444; color: #888; padding: 4px 12px; cursor: pointer; border-radius: 4px; font-size: 0.7rem;">CLOSE [ESC]</button>
        </div>
        <iframe class="ui-frame" id="ui-iframe"></iframe>
    </div>

    <script>
        const uiOverlay = document.getElementById('ui-overlay');
        const uiIframe = document.getElementById('ui-iframe');

        function openUIHub() {
            uiIframe.src = "https://debeatzgh1.github.io/Home-/";
            uiOverlay.style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeUIHub() {
            uiOverlay.style.display = 'none';
            uiIframe.src = "";
            document.body.style.overflow = 'auto';
        }

        // Close on Escape key
        document.addEventListener('keydown', (e) => {
            if (e.key === "Escape") closeUIHub();
        });
    </script>
</body>
</html>


<!-- Elfsight Portfolio | Portfolio -->
<script src="https://elfsightcdn.com/platform.js" async></script>
<div class="elfsight-app-c8b5bd3d-12c1-4531-9f1f-e354d2c51f79" data-elfsight-app-lazy></div>



<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>My – Digital Hub Carousel</title>

<style>
:root{
  --primary:#16a34a;
  --dark:#0f172a;
  --light:#f8fafc;
}

body{
  margin:0;
  font-family: system-ui, -apple-system, BlinkMacSystemFont;
  background:linear-gradient(135deg,#f1f5f9,#e2e8f0);
  color:#0f172a;
}

/* ===== Carousel ===== */
.carousel{
  display:flex;
  gap:18px;
  overflow-x:auto;
  padding:20px;
  scroll-snap-type:x mandatory;
}
.card{
  min-width:280px;
  background:#fff;
  border-radius:16px;
  box-shadow:0 10px 25px rgba(0,0,0,.08);
  scroll-snap-align:start;
  overflow:hidden;
  transition:.3s;
}
.card:hover{transform:translateY(-6px);}
.card img{
  width:100%;
  height:160px;
  object-fit:cover;
}
.card-content{
  padding:14px;
}
.card h3{
  margin:0 0 6px;
  font-size:18px;
}
.card p{
  font-size:14px;
  color:#475569;
}
.card button{
  margin-top:10px;
  width:100%;
  border:none;
  padding:10px;
  border-radius:10px;
  background:var(--primary);
  color:#fff;
  font-weight:600;
  cursor:pointer;
}
.card button:hover{opacity:.9}

/* ===== Modal ===== */
#modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.7);
  display:none;
  z-index:9999;
}
#modal iframe{
  width:100%;
  height:100%;
  border:none;
  background:#fff;
}
.close{
  position:absolute;
  top:12px;
  right:14px;
  background:#000;
  color:#fff;
  padding:6px 12px;
  border-radius:8px;
  cursor:pointer;
  z-index:10;
}

/* ===== Floating Button ===== */
#launcher{
  position:fixed;
  bottom:18px;
  right:18px;
  background:var(--primary);
  color:#fff;
  padding:14px 18px;
  border-radius:999px;
  font-weight:700;
  cursor:pointer;
  box-shadow:0 12px 30px rgba(0,0,0,.3);
  animation:pulse 2s infinite;
  z-index:1000;
}
@keyframes pulse{
  0%{transform:scale(1)}
  50%{transform:scale(1.05)}
  100%{transform:scale(1)}
}
</style>
</head>

<body>

<h2 style="padding:16px 20px;">🚀 My Digital Ecosystem</h2>
<p style="padding:0 20px;color:#475569">
Explore AI tools, digital hubs, menus, updates, and collaboration spaces — all in one place.
</p>

<div class="carousel">

<!-- AI Agent -->
<div class="card">
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/createaboldeye-catchingsocialmediaflyerfeaturingtwosplitsectionsorcharacters2273204207149586064.jpg">
<div class="card-content">
<h3>AI Agent</h3>
<p>Chat, automate tasks, and explore AI-powered assistance.</p>
<button onclick="openFrame('https://debeatzgh1.github.io/ai-chat/')">Open</button>
</div>
</div>

<!-- Tools -->
<div class="card">
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/amoderncleanworkspaceshowcasingfront-endcodesnippetsonasleeklaptopscreensurroundedbytailwindcsslogoshtml5andfirebaseicons5315964892159237038.jpg">
<div class="card-content">
<h3>Tools Hub</h3>
<p>Access widgets, generators, and productivity tools.</p>
<button onclick="openFrame('https://debeatzgh1.github.io/debeatzgh/')">Open</button>
</div>
</div>

<!-- Menu -->
<div class="card">
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/17631483793116166606987906632973.jpg">
<div class="card-content">
<h3>Menu</h3>
<p>Navigation hub to explore all projects.</p>
<button onclick="openUrl('https://debeatzgh1.github.io/-Firebase-Login-Popup/')">Open</button>
</div>
</div>

<!-- E Hub -->
<div class="card">
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamoderntech-inspiredlogoforadigitalcontenthubcalledappdategh4933013559151235986.jpg">
<div class="card-content">
<h3>E. Hub</h3>
<p>Digital content and app update ecosystem.</p>
<button onclick="openFrame('https://debeatzgh1.github.io/appdategh/')">Open</button>
</div>
</div>

<!-- Collaborate -->
<div class="card">
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/11/screenshot_20251121-103715_12380909417515729112.png">
<div class="card-content">
<h3>Collaborate</h3>
<p>Connect with contributors and partners.</p>
<button onclick="openFrame('https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/')">Open</button>
</div>
</div>

<!-- Updates -->
<div class="card">
<img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/screenshot_20251206-065712_18880183932568216810.png">
<div class="card-content">
<h3>Updates</h3>
<p>Latest announcements, releases, and news.</p>
<button onclick="openFrame('https://debeatzgh1.github.io/dk/')">Open</button>
</div>
</div>

</div>


<!-- Modal -->
<div id="modal">
<div class="close" onclick="closeFrame()">✕ Close</div>
<iframe id="frame"></iframe>
</div>

<script>
function openFrame(url){
  document.getElementById('modal').style.display='block';
  document.getElementById('frame').src=url;
}
function closeFrame(){
  document.getElementById('modal').style.display='none';
  document.getElementById('frame').src='';
}
</script>

</body>
</html>
