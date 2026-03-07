
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
<div id="launcher" onclick="openFrame('https://form.svhrt.com/60f4a0aeedc1993c8c7b3989')">
🚀 sggst 
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
