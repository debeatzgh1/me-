
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --banner-bg: rgba(13, 17, 23, 0.85);
            --accent-pink: #FF1493;
            --accent-glow: rgba(255, 20, 147, 0.4);
            --text-white: #ffffff;
            --border-glass: rgba(255, 255, 255, 0.1);
        }

        /* Floating Banner Container */
        .top-floating-banner {
            position: fixed;
            top: 15px;
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 700px;
            height: 50px;
            background: var(--banner-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--border-glass);
            border-radius: 100px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 10px 0 25px;
            z-index: 10000;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
            overflow: hidden;
            animation: slideDown 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        /* Carousel Wrapper */
        .carousel-wrapper {
            flex: 1;
            overflow: hidden;
            position: relative;
            margin-right: 15px;
        }

        .carousel-content {
            display: flex;
            white-space: nowrap;
            animation: scrollText 15s linear infinite;
        }

        .carousel-content span {
            font-family: 'Segoe UI', Roboto, sans-serif;
            font-size: 0.85rem;
            color: var(--text-white);
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* Launch Button */
        .banner-btn {
            background: var(--accent-pink);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
            box-shadow: 0 0 15px var(--accent-glow);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .banner-btn:hover {
            transform: scale(1.05);
            background: #ff69b4;
            box-shadow: 0 0 25px var(--accent-glow);
        }

        /* Modal Overlay for Milkshake */
        #milkshake-modal {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.9);
            display: none;
            z-index: 10001;
            flex-direction: column;
            animation: fadeIn 0.3s ease;
        }

        .modal-header {
            padding: 15px 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #161b22;
        }

        .close-btn {
            background: #f85149;
            color: white;
            border: none;
            padding: 5px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        #msha-iframe {
            width: 100%;
            flex-grow: 1;
            border: none;
        }

        /* Animations */
        @keyframes scrollText {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }

        @keyframes slideDown {
            from { transform: translate(-50%, -100px); opacity: 0; }
            to { transform: translate(-50%, 0); opacity: 1; }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Mobile Adjustments */
        @media (max-width: 600px) {
            .carousel-content span { font-size: 0.75rem; }
            .banner-btn span { display: none; }
            .banner-btn { padding: 8px 12px; }
        }
    </style>
</head>
<body>

    <div class="top-floating-banner">
        <div class="carousel-wrapper">
            <div class="carousel-content">
                <span>
                    💻 Access your lifestyle, productivity tools and ideas All in one place! 🚀 💡 📈
                </span>
            </div>
        </div>
        
        <button class="banner-btn" onclick="openMilkshake()">
            <span>Launch Hub</span> ⭐️
        </button>
    </div>

    <div id="milkshake-modal">
        <div class="modal-header">
            <span style="color:white; font-family: sans-serif; font-weight: bold;">Debeatzgh Hub</span>
            <button class="close-btn" onclick="closeMilkshake()">✕ Close</button>
        </div>
        <iframe id="msha-iframe" src=""></iframe>
    </div>

    <script>
        function openMilkshake() {
            const modal = document.getElementById('milkshake-modal');
            const iframe = document.getElementById('msha-iframe');
            
            // Set source only when clicked to save performance
            iframe.src = "https://msha.ke/debeatzgh";
            modal.style.display = "flex";
            document.body.style.overflow = "hidden"; // Disable scroll
        }

        function closeMilkshake() {
            const modal = document.getElementById('milkshake-modal');
            const iframe = document.getElementById('msha-iframe');
            
            modal.style.display = "none";
            iframe.src = ""; // Stop the iframe content
            document.body.style.overflow = "auto"; // Re-enable scroll
        }
    </script>

</body>
</html>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --nav-bg: rgba(13, 17, 23, 0.95);
            --nav-border: #30363d;
            --nav-accent: #58a6ff;
            --nav-hover: #1f6feb;
            --glow-color: rgba(88, 166, 255, 0.6);
        }

        /* Dock Container */
        .nav-dock {
            position: fixed;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            z-index: 10000;
        }

        /* Launcher (Button with the > icon) */
        #nav-launcher {
            width: 40px;
            height: 40px;
            background: var(--nav-bg);
            border: 1px solid var(--nav-border);
            color: var(--nav-accent);
            border-radius: 10px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 4px 15px rgba(0,0,0,0.4);
            outline: none;
        }

        #nav-launcher.open {
            transform: rotate(-180deg);
            background: var(--nav-hover);
            color: white;
            border-color: var(--nav-accent);
        }

        /* Button Group Hidden State */
        .nav-group {
            display: flex;
            flex-direction: column;
            gap: 12px;
            visibility: hidden;
            pointer-events: none;
        }

        .nav-group.active {
            visibility: visible;
            pointer-events: auto;
        }

        /* Navigator Tiny Arrows */
        .nav-btn {
            width: 36px;
            height: 36px;
            background: var(--nav-bg);
            border: 1px solid var(--nav-border);
            color: #c9d1d9;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transform: scale(0.5) translateX(40px);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-decoration: none;
            position: relative;
        }

        .nav-group.active .nav-btn {
            opacity: 1;
            transform: scale(1) translateX(0);
        }

        /* Heartbeat Glow Animation */
        @keyframes heartbeatGlow {
            0% { box-shadow: 0 0 0 0 var(--glow-color); transform: scale(1); }
            50% { box-shadow: 0 0 20px 8px var(--glow-color); transform: scale(1.15); }
            100% { box-shadow: 0 0 0 0 var(--glow-color); transform: scale(1); }
        }

        .pulse {
            animation: heartbeatGlow 1.2s ease-in-out;
        }

        .nav-btn:hover {
            background: var(--nav-hover);
            color: white;
            border-color: var(--nav-accent);
        }

        /* Staggered transition delays */
        .nav-group.active .nav-btn:nth-child(1) { transition-delay: 0.1s; }
        .nav-group.active .nav-btn:nth-child(2) { transition-delay: 0.2s; }
        .nav-group.active .nav-btn:nth-child(3) { transition-delay: 0.3s; }

        svg { width: 18px; height: 18px; fill: none; stroke: currentColor; stroke-width: 3; stroke-linecap: round; stroke-linejoin: round; }
    </style>
</head>
<body>

    <div class="nav-dock">
        <button id="nav-launcher" onclick="toggleNav()">
            <svg viewBox="0 0 24 24"><polyline points="9 18 15 12 9 6"></polyline></svg>
        </button>

        <div class="nav-group" id="navGroup">
            <button class="nav-btn" onclick="window.scrollTo({top: 0, behavior: 'smooth'})" title="Scroll to Top">
                <svg viewBox="0 0 24 24"><polyline points="18 15 12 9 6 15"></polyline></svg>
            </button>

            <a href="https://debeatzgh1.github.io/Home-/" class="nav-btn" title="Go Home">
                <svg viewBox="0 0 24 24" stroke-width="2.5"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path><polyline points="9 22 9 12 15 12 15 22"></polyline></svg>
            </a>

            <button class="nav-btn" onclick="window.scrollTo({top: document.body.scrollHeight, behavior: 'smooth'})" title="Scroll to Bottom">
                <svg viewBox="0 0 24 24"><polyline points="6 9 12 15 18 9"></polyline></svg>
            </button>
        </div>
    </div>

    <script>
        function toggleNav() {
            const group = document.getElementById('navGroup');
            const launcher = document.getElementById('nav-launcher');
            const buttons = document.querySelectorAll('.nav-btn');
            
            const isOpening = group.classList.toggle('active');
            launcher.classList.toggle('open');

            if (isOpening) {
                buttons.forEach((btn, index) => {
                    // Reset animation state
                    btn.classList.remove('pulse');
                    // Force a tiny delay so the browser sees the removal
                    setTimeout(() => {
                        // Apply heartbeat pulse
                        btn.classList.add('pulse');
                    }, (index + 1) * 150);
                });
            }
        }
    </script>
</body>
</html>


<!-- Elfsight FAQ | FAQ -->
<script src="https://elfsightcdn.com/platform.js" async></script>
<div class="elfsight-app-e78e03db-1434-4f96-aea0-fcbc6c92c429" data-elfsight-app-lazy></div>




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
<button onclick="openFrame('https://debeatzgh1.github.io/Home-/')">Open</button>
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

<!-- Floating Launcher -->
<div id="launcher" onclick="openFrame('https://debeatzgh1.github.io/Home-/')">
🚀 Home 
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
