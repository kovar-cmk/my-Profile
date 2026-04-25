<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>kovar-cmk — Cybersecurity Engineer</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;600;700;800&family=Orbitron:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
/* ═══════════ RESET & BASE ═══════════ */
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;scrollbar-width:thin;scrollbar-color:#ff0040 #0a0a0a}
::-webkit-scrollbar{width:6px}::-webkit-scrollbar-track{background:#0a0a0a}::-webkit-scrollbar-thumb{background:#ff0040;border-radius:3px}
body{background:#0a0a0a;color:#c9d1d9;font-family:'JetBrains Mono',monospace;line-height:1.7;overflow-x:hidden;position:relative}
::selection{background:rgba(255,0,64,.3);color:#fff}
a{color:#ff0040;text-decoration:none;transition:color .3s}
a:hover{color:#ff4070}

/* ═══════════ SCANLINES OVERLAY ═══════════ */
body::after{content:'';position:fixed;inset:0;z-index:9999;pointer-events:none;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,0,0,.025) 2px,rgba(0,0,0,.025) 4px);opacity:.5}

/* ═══════════ CURSOR GLOW ═══════════ */
#glow{position:fixed;width:500px;height:500px;border-radius:50%;pointer-events:none;z-index:0;background:radial-gradient(circle,rgba(255,0,64,.06) 0%,transparent 70%);transform:translate(-50%,-50%);transition:left .08s,top .08s,background .8s}
body.blue-mode #glow{background:radial-gradient(circle,rgba(0,136,255,.06) 0%,transparent 70%)}

/* ═══════════ BACKGROUND GRID ═══════════ */
.bg-grid{position:fixed;inset:0;z-index:0;pointer-events:none;
background-image:
linear-gradient(rgba(255,0,64,.03) 1px,transparent 1px),
linear-gradient(90deg,rgba(255,0,64,.03) 1px,transparent 1px);
background-size:60px 60px;
transition:background-image .8s}
body.blue-mode .bg-grid{
background-image:
linear-gradient(rgba(0,136,255,.03) 1px,transparent 1px),
linear-gradient(90deg,rgba(0,136,255,.03) 1px,transparent 1px)}

/* ═══════════ CONTAINER ═══════════ */
.container{max-width:900px;margin:0 auto;padding:0 24px;position:relative;z-index:1}

/* ═══════════ MODE TOGGLE ═══════════ */
.mode-toggle-wrap{position:fixed;top:20px;right:20px;z-index:100}
.mode-toggle{display:flex;align-items:center;gap:8px;padding:8px 14px;background:rgba(10,10,10,.9);border:1px solid rgba(255,0,64,.3);border-radius:30px;cursor:pointer;backdrop-filter:blur(12px);transition:all .5s;font-size:.65rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:#888;user-select:none}
.mode-toggle:hover{border-color:#ff0040;box-shadow:0 0 20px rgba(255,0,64,.15)}
body.blue-mode .mode-toggle{border-color:rgba(0,136,255,.3)}
body.blue-mode .mode-toggle:hover{border-color:#0088ff;box-shadow:0 0 20px rgba(0,136,255,.15)}
.mode-dot{width:8px;height:8px;border-radius:50%;background:#ff0040;box-shadow:0 0 8px rgba(255,0,64,.6);transition:all .5s}
body.blue-mode .mode-dot{background:#0088ff;box-shadow:0 0 8px rgba(0,136,255,.6)}
.mode-label-text{transition:color .5s}
body.blue-mode .mode-label-text{color:#6ab0ff}

/* ═══════════ HERO SECTION ═══════════ */
.hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:60px 24px 40px;position:relative}
.hero-wave{position:absolute;top:0;left:0;right:0;height:80px;overflow:hidden}
.hero-wave svg{position:absolute;bottom:0;width:200%}
.wave-path{fill:none;stroke:#ff0040;stroke-width:1.5;opacity:.3;transition:stroke .8s}
body.blue-mode .wave-path{stroke:#0088ff}
.wave-path-2{animation:waveShift 8s linear infinite;opacity:.15}
@keyframes waveShift{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}

.hero-name{font-family:'Orbitron',sans-serif;font-size:clamp(2rem,5vw,3.2rem);font-weight:900;color:#eaeaea;letter-spacing:.03em;margin-bottom:8px;position:relative}
.hero-name .accent{color:#ff0040;transition:color .5s}
body.blue-mode .hero-name .accent{color:#0088ff}

/* Typing effect */
.typing-wrap{height:1.6em;overflow:hidden;margin-bottom:16px;position:relative}
.typing-text{display:inline;font-size:clamp(.85rem,2vw,1.1rem);color:#ff0040;font-weight:500;white-space:nowrap;border-right:2px solid #ff0040;animation:typeLine 9s steps(1) infinite,blinkCaret .7s step-end infinite;transition:color .5s,border-color .5s}
body.blue-mode .typing-text{color:#0088ff;border-color:#0088ff}
@keyframes typeLine{
0%,2%{content:"Breaking systems to understand them."}
33%,35%{content:"Defending systems to secure them."}
66%,68%{content:"Cybersecurity Engineer | Red & Blue Team"}
99%,100%{content:"Breaking systems to understand them."}
}
@keyframes blinkCaret{50%{border-color:transparent}}

.hero-subtitle{font-size:.85rem;color:#666;margin-bottom:28px;letter-spacing:.05em}

.hero-badges{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-bottom:32px}
.hero-badge{display:inline-flex;align-items:center;gap:6px;padding:6px 14px;border-radius:6px;font-size:.7rem;font-weight:600;letter-spacing:.04em;border:1px solid;transition:all .4s}
.hero-badge.red{color:#ff0040;border-color:rgba(255,0,64,.3);background:rgba(255,0,64,.05)}
.hero-badge.red:hover{background:rgba(255,0,64,.12);border-color:#ff0040;box-shadow:0 0 16px rgba(255,0,64,.1)}
.hero-badge.blue{color:#0088ff;border-color:rgba(0,136,255,.3);background:rgba(0,136,255,.05)}
.hero-badge.blue:hover{background:rgba(0,136,255,.12);border-color:#0088ff;box-shadow:0 0 16px rgba(0,136,255,.1)}

.hero-socials{display:flex;gap:16px}
.hero-socials a{width:40px;height:40px;display:flex;align-items:center;justify-content:center;border-radius:10px;border:1px solid rgba(255,255,255,.08);color:#666;font-size:1rem;transition:all .3s}
.hero-socials a:hover{color:#ff0040;border-color:#ff0040;background:rgba(255,0,64,.06);transform:translateY(-2px)}
body.blue-mode .hero-socials a:hover{color:#0088ff;border-color:#0088ff;background:rgba(0,136,255,.06)}

.scroll-hint{position:absolute;bottom:30px;display:flex;flex-direction:column;align-items:center;gap:6px;opacity:.3}
.scroll-hint span{font-size:.6rem;letter-spacing:.2em;text-transform:uppercase;color:#666}
.scroll-line{width:1px;height:28px;background:linear-gradient(to bottom,#ff0040,transparent);animation:scrollPulse 2.5s ease-in-out infinite}
body.blue-mode .scroll-line{background:linear-gradient(to bottom,#0088ff,transparent)}
@keyframes scrollPulse{0%,100%{opacity:.3;transform:scaleY(1)}50%{opacity:.8;transform:scaleY(1.3)}}

/* ═══════════ TERMINAL BLOCK ═══════════ */
.term-block{background:#0d0d0d;border:1px solid rgba(255,255,255,.06);border-radius:10px;overflow:hidden;margin:32px 0;font-size:.78rem;transition:border-color .5s}
body.blue-mode .term-block{border-color:rgba(0,136,255,.1)}
.term-bar{display:flex;align-items:center;gap:8px;padding:10px 14px;background:rgba(255,255,255,.02);border-bottom:1px solid rgba(255,255,255,.04)}
.term-dots{display:flex;gap:5px}
.term-dots span{width:9px;height:9px;border-radius:50%}
.term-bar-title{font-size:.65rem;color:#555;letter-spacing:.04em;margin-left:6px}
.term-body{padding:14px 18px;line-height:1.8}
.term-body .prompt{color:#ff0040;font-weight:600}
body.blue-mode .term-body .prompt{color:#0088ff}
.term-body .cmd{color:#eaeaea}
.term-body .out{color:#666}
.term-body .ok{color:#00ff88}
.term-body .err{color:#ff4444}

/* ═══════════ SECTION STYLING ═══════════ */
.section{padding:60px 0}
.section-header{margin-bottom:36px;position:relative}
.section-prefix{font-size:.65rem;letter-spacing:.2em;text-transform:uppercase;color:#ff0040;font-weight:500;display:block;margin-bottom:6px;font-family:'Orbitron',sans-serif;transition:color .5s}
body.blue-mode .section-prefix{color:#0088ff}
.section-title{font-family:'Orbitron',sans-serif;font-size:clamp(1.2rem,3vw,1.6rem);font-weight:700;color:#eaeaea;letter-spacing:.03em;position:relative;display:inline-block}
.section-title::after{content:'';display:block;width:50px;height:3px;background:#ff0040;margin-top:8px;border-radius:2px;transition:width .4s,background .5s}
.section-title:hover::after{width:100%}
body.blue-mode .section-title::after{background:#0088ff}

/* ═══════════ ABOUT ═══════════ */
.about-text{font-size:.82rem;color:#888;line-height:1.9;max-width:720px}
.about-text strong{color:#eaeaea}
.about-text .hl{color:#ff0040;font-weight:500;transition:color .5s}
body.blue-mode .about-text .hl{color:#0088ff}

/* ═══════════ CERTIFICATION ═══════════ */
.cert-card{display:flex;align-items:center;gap:20px;padding:24px 28px;background:linear-gradient(135deg,rgba(255,0,64,.04),rgba(0,136,255,.02));border:1px solid rgba(255,0,64,.2);border-radius:14px;transition:all .5s;position:relative;overflow:hidden}
body.blue-mode .cert-card{background:linear-gradient(135deg,rgba(0,136,255,.04),rgba(0,136,255,.01));border-color:rgba(0,136,255,.2)}
.cert-card::before{content:'';position:absolute;top:-50%;right:-50%;width:200px;height:200px;border-radius:50%;background:radial-gradient(circle,rgba(255,0,64,.05),transparent 70%);transition:background .5s}
body.blue-mode .cert-card::before{background:radial-gradient(circle,rgba(0,136,255,.05),transparent 70%)}
.cert-icon{width:56px;height:56px;border-radius:14px;display:flex;align-items:center;justify-content:center;background:rgba(255,0,64,.1);border:1px solid rgba(255,0,64,.2);font-size:1.4rem;color:#ff0040;flex-shrink:0;transition:all .5s}
body.blue-mode .cert-icon{background:rgba(0,136,255,.1);border-color:rgba(0,136,255,.2);color:#0088ff}
.cert-info h3{font-family:'Orbitron',sans-serif;font-size:.9rem;font-weight:700;color:#eaeaea;margin-bottom:4px}
.cert-info p{font-size:.75rem;color:#888}
.cert-badges{display:flex;gap:8px;margin-top:10px;flex-wrap:wrap}
.cert-badge{font-size:.6rem;padding:3px 10px;border-radius:4px;border:1px solid rgba(255,0,64,.2);color:#ff0040;background:rgba(255,0,64,.04);transition:all .5s}
body.blue-mode .cert-badge{border-color:rgba(0,136,255,.2);color:#0088ff;background:rgba(0,136,255,.04)}

/* ═══════════ SKILLS GRID ═══════════ */
.skills-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px}
@media(max-width:700px){.skills-grid{grid-template-columns:1fr}}
.skill-panel{background:#0d0d0d;border:1px solid rgba(255,255,255,.06);border-radius:14px;overflow:hidden;transition:border-color .5s}
.skill-panel:hover{border-color:rgba(255,255,255,.1)}
.skill-panel-header{display:flex;align-items:center;gap:10px;padding:16px 20px;border-bottom:1px solid rgba(255,255,255,.04)}
.skill-panel-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}
.skill-panel-dot.red{background:#ff0040;box-shadow:0 0 10px rgba(255,0,64,.4)}
.skill-panel-dot.blue{background:#0088ff;box-shadow:0 0 10px rgba(0,136,255,.4)}
.skill-panel-title{font-family:'Orbitron',sans-serif;font-size:.8rem;font-weight:700;letter-spacing:.04em}
.skill-panel-title.red{color:#ff0040}
.skill-panel-title.blue{color:#0088ff}
.skill-list{padding:8px 0}
.skill-item{display:flex;align-items:center;justify-content:space-between;padding:10px 20px;transition:background .3s;font-size:.78rem}
.skill-item:hover{background:rgba(255,255,255,.02)}
.skill-name{color:#c9d1d9;display:flex;align-items:center;gap:8px}
.skill-name i{width:16px;text-align:center;font-size:.7rem;opacity:.5}
.skill-desc{font-size:.65rem;color:#555;max-width:200px;text-align:right}
.skill-bar-wrap{width:60px;height:4px;background:rgba(255,255,255,.04);border-radius:2px;overflow:hidden;flex-shrink:0}
.skill-bar{height:100%;border-radius:2px;width:0;transition:width 1.5s cubic-bezier(.22,.61,.36,1),background .5s}
.skill-bar.red{background:#ff0040}
.skill-bar.blue{background:#0088ff}

.skill-tools{padding:12px 20px;border-top:1px solid rgba(255,255,255,.04);display:flex;flex-wrap:wrap;gap:6px}
.skill-tool{font-size:.6rem;padding:3px 10px;border-radius:4px;border:1px solid rgba(255,255,255,.06);color:#888;background:rgba(255,255,255,.02);transition:all .3s}
.skill-tool:hover{border-color:#ff0040;color:#ff0040}
body.blue-mode .skill-tool:hover{border-color:#0088ff;color:#0088ff}

/* ═══════════ TECH STACK ═══════════ */
.tech-categories{display:flex;flex-direction:column;gap:20px}
.tech-cat-label{font-size:.6rem;letter-spacing:.15em;text-transform:uppercase;color:#555;margin-bottom:8px;font-weight:600}
.tech-row{display:flex;flex-wrap:wrap;gap:8px}
.tech-badge{display:inline-flex;align-items:center;gap:6px;padding:6px 14px;border-radius:8px;font-size:.72rem;font-weight:500;border:1px solid rgba(255,255,255,.06);background:rgba(255,255,255,.015);color:#c9d1d9;transition:all .3s;cursor:default}
.tech-badge:hover{border-color:#ff0040;color:#ff0040;transform:translateY(-2px);box-shadow:0 4px 12px rgba(255,0,64,.08)}
body.blue-mode .tech-badge:hover{border-color:#0088ff;color:#0088ff;box-shadow:0 4px 12px rgba(0,136,255,.08)}
.tech-badge i{font-size:.8rem;opacity:.7}

/* ═══════════ PROJECTS ═══════════ */
.project-card{background:#0d0d0d;border:1px solid rgba(255,255,255,.06);border-radius:12px;padding:22px 24px;margin-bottom:14px;transition:all .4s;position:relative;overflow:hidden}
.project-card::before{content:'';position:absolute;top:0;left:0;width:3px;height:100%;border-radius:2px;transition:background .4s}
.project-card.red-proj::before{background:#ff0040}
.project-card.blue-proj::before{background:#0088ff}
.project-card.neutral-proj::before{background:linear-gradient(to bottom,#ff0040,#0088ff)}
.project-card:hover{border-color:rgba(255,255,255,.12);transform:translateX(4px)}
.project-card.red-proj:hover{box-shadow:4px 0 20px rgba(255,0,64,.06)}
.project-card.blue-proj:hover{box-shadow:4px 0 20px rgba(0,136,255,.06)}
.project-header{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.project-icon{width:28px;height:28px;border-radius:7px;display:flex;align-items:center;justify-content:center;font-size:.7rem;flex-shrink:0}
.project-icon.red{background:rgba(255,0,64,.1);color:#ff0040;border:1px solid rgba(255,0,64,.2)}
.project-icon.blue{background:rgba(0,136,255,.1);color:#0088ff;border:1px solid rgba(0,136,255,.2)}
.project-icon.neutral{background:rgba(255,255,255,.04);color:#888;border:1px solid rgba(255,255,255,.08)}
.project-name{font-size:.88rem;font-weight:700;color:#eaeaea}
.project-desc{font-size:.75rem;color:#888;line-height:1.7;margin-bottom:10px}
.project-impact{font-size:.68rem;color:#ff0040;font-style:italic;padding-left:12px;border-left:2px solid rgba(255,0,64,.2);transition:color .5s,border-color .5s}
body.blue-mode .project-impact{color:#0088ff;border-left-color:rgba(0,136,255,.2)}

/* ═══════════ STATS ═══════════ */
.stats-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px}
.stat-card{background:#0d0d0d;border:1px solid rgba(255,255,255,.06);border-radius:12px;padding:20px;text-align:center;transition:all .4s}
.stat-card:hover{border-color:rgba(255,0,64,.2);box-shadow:0 0 20px rgba(255,0,64,.04)}
body.blue-mode .stat-card:hover{border-color:rgba(0,136,255,.2);box-shadow:0 0 20px rgba(0,136,255,.04)}
.stat-card img{border-radius:8px;max-width:100%}
.stat-number{font-family:'Orbitron',sans-serif;font-size:1.8rem;font-weight:900;color:#ff0040;margin-bottom:4px;transition:color .5s}
body.blue-mode .stat-number{color:#0088ff}
.stat-label{font-size:.65rem;color:#555;text-transform:uppercase;letter-spacing:.12em}

/* ═══════════ CONTACT ═══════════ */
.contact-grid{display:flex;flex-wrap:wrap;gap:12px;margin-top:16px}
.contact-link{display:inline-flex;align-items:center;gap:8px;padding:10px 18px;border-radius:10px;font-size:.78rem;font-weight:500;border:1px solid rgba(255,255,255,.08);color:#c9d1d9;background:rgba(255,255,255,.015);transition:all .3s}
.contact-link:hover{border-color:#ff0040;color:#ff0040;background:rgba(255,0,64,.04);transform:translateY(-2px);box-shadow:0 6px 20px rgba(255,0,64,.08)}
body.blue-mode .contact-link:hover{border-color:#0088ff;color:#0088ff;background:rgba(0,136,255,.04);box-shadow:0 6px 20px rgba(0,136,255,.08)}
.contact-link i{font-size:.9rem;opacity:.7}

/* ═══════════ FOOTER ═══════════ */
.footer{border-top:1px solid rgba(255,255,255,.04);padding:28px 0;text-align:center;transition:border-color .5s}
.footer-text{font-size:.68rem;color:#444;letter-spacing:.04em}
.footer-text .hl{color:#ff0040;transition:color .5s}
body.blue-mode .footer-text .hl{color:#0088ff}

/* ═══════════ SEPARATOR ═══════════ */
.sep{height:1px;background:linear-gradient(90deg,transparent,rgba(255,255,255,.06),transparent);margin:0;transition:background .5s}
body.blue-mode .sep{background:linear-gradient(90deg,transparent,rgba(0,136,255,.08),transparent)}

/* ═══════════ FADE IN ANIMATION ═══════════ */
.fade{opacity:0;transform:translateY(30px);transition:opacity .7s ease,transform .7s ease}
.fade.visible{opacity:1;transform:translateY(0)}
.fade-d1{transition-delay:.1s}.fade-d2{transition-delay:.2s}.fade-d3{transition-delay:.3s}.fade-d4{transition-delay:.4s}

/* ═══════════ BACKGROUND FLOATING ALERTS ═══════════ */
.bg-alert{position:fixed;z-index:0;pointer-events:none;font-family:'Orbitron',sans-serif;font-size:clamp(.7rem,1.5vw,1.2rem);letter-spacing:.3em;text-transform:uppercase;color:#ff0040;opacity:0;animation:alertFloat 6s ease-in-out infinite;transition:color .5s}
body.blue-mode .bg-alert{color:#0088ff}
.bg-alert:nth-child(1){top:15%;left:5%;animation-delay:0s}
.bg-alert:nth-child(2){top:45%;right:3%;animation-delay:2s}
.bg-alert:nth-child(3){bottom:20%;left:8%;animation-delay:4s}
@keyframes alertFloat{0%,100%{opacity:0;transform:translateY(0) scale(1)}15%{opacity:.04}50%{opacity:.03;transform:translateY(-20px) scale(1.02)}85%{opacity:.04}}

/* ═══════════ RESPONSIVE ═══════════ */
@media(max-width:600px){
.mode-toggle-wrap{top:auto;bottom:16px;right:16px}
.mode-toggle{padding:6px 10px;font-size:.55rem}
.hero-badges{flex-direction:column;align-items:center}
.cert-card{flex-direction:column;text-align:center}
.stats-grid{grid-template-columns:1fr}
.project-card:hover{transform:none}
}

/* ═══════════ REDUCED MOTION ═══════════ */
@media(prefers-reduced-motion:reduce){
*{animation-duration:0s!important;transition-duration:0s!important}
}
</style>
</head>
<body>

<!-- Cursor glow -->
<div id="glow"></div>

<!-- Background grid -->
<div class="bg-grid"></div>

<!-- Floating background alerts -->
<div class="bg-alert">BREACH DETECTED</div>
<div class="bg-alert">THREAT NEUTRALIZED</div>
<div class="bg-alert">PERSISTENCE ACHIEVED</div>

<!-- Mode toggle -->
<div class="mode-toggle-wrap">
<div class="mode-toggle" onclick="toggleMode()" role="button" tabindex="0" aria-label="Toggle Red/Blue mode">
<div class="mode-dot"></div>
<span class="mode-label-text">Red Mode</span>
</div>
</div>

<!-- ═══════════ HERO ═══════════ -->
<section class="hero">
<div class="hero-wave">
<svg viewBox="0 0 1440 80" preserveAspectRatio="none">
<path class="wave-path" d="M0,40 C360,80 720,0 1080,40 C1260,60 1380,20 1440,40 L1440,80 L0,80Z"/>
<path class="wave-path wave-path-2" d="M0,50 C360,10 720,70 1080,30 C1260,10 1380,60 1440,30 L1440,80 L0,80Z" style="transform:translateX(-50%)"/>
</svg>
</div>

<div class="fade">
<div style="font-size:.6rem;letter-spacing:.25em;text-transform:uppercase;color:#555;margin-bottom:12px">
<i class="fa-solid fa-shield-halved" style="color:#ff0040;margin-right:4px"></i>
<span class="mode-badge-text">RED TEAM</span> OPERATIVE
</div>
</div>

<h1 class="hero-name fade fade-d1">
Kovar <span class="accent">CMK</span>
</h1>

<div class="typing-wrap fade fade-d2">
<span class="typing-text" id="typing-text"></span>
</div>

<p class="hero-subtitle fade fade-d2">Cybersecurity Engineer &bull; Red Team & Blue Team</p>

<div class="hero-badges fade fade-d3">
<span class="hero-badge red"><i class="fa-solid fa-crosshairs"></i> Offensive Security</span>
<span class="hero-badge blue"><i class="fa-solid fa-shield-halved"></i> Defensive Security</span>
<span class="hero-badge red"><i class="fa-solid fa-bug"></i> Bug Bounty</span>
<span class="hero-badge blue"><i class="fa-solid fa-network-wired"></i> Cisco Networks</span>
</div>

<div class="hero-socials fade fade-d4">
<a href="https://github.com/kovar-cmk" aria-label="GitHub"><i class="fa-brands fa-github"></i></a>
<a href="#" aria-label="LinkedIn"><i class="fa-brands fa-linkedin-in"></i></a>
<a href="#" aria-label="Email"><i class="fa-solid fa-envelope"></i></a>
</div>

<div class="scroll-hint">
<span>Scroll</span>
<div class="scroll-line"></div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ ABOUT ═══════════ -->
<section class="section">
<div class="container">
<div class="term-block fade">
<div class="term-bar">
<div class="term-dots"><span style="background:#ff5f57"></span><span style="background:#ffbd2e"></span><span style="background:#28ca42"></span></div>
<span class="term-bar-title">kovar@kali ~ about</span>
</div>
<div class="term-body">
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ whoami</span></div>
<div><span class="out">Cybersecurity Engineer with a dual mindset — offensive and defensive.</span></div>
<br>
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ cat mindset.txt</span></div>
<div><span class="out">I operate at the intersection of <strong>attack and defense</strong> — breaking systems to understand their weaknesses, then building the defenses to close those gaps. My foundation starts at the network layer with hands-on <span class="hl">Cisco infrastructure</span> experience, scaling up to <span class="hl">web application security</span>, threat detection, and incident response.</span></div>
<br>
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ echo $APPROACH</span></div>
<div><span class="out">I approach security not as a checklist, but as a <strong>kill chain</strong> — understanding every stage from initial access to persistence, and building detection and hardening strategies at each layer.</span></div>
<br>
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ echo $STATUS</span></div>
<div><span class="ok">[READY] Active on both sides of the wire.</span></div>
</div>
</div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ CERTIFICATION ═══════════ -->
<section class="section">
<div class="container">
<div class="section-header fade">
<span class="section-prefix">// Credentials</span>
<h2 class="section-title">Certification</h2>
</div>
<div class="cert-card fade fade-d1">
<div class="cert-icon"><i class="fa-solid fa-certificate"></i></div>
<div class="cert-info">
<h3>Cisco Certified Network Associate</h3>
<p>CCNA — Routing & Switching, network fundamentals, security basics, automation</p>
<div class="cert-badges">
<span class="cert-badge"><i class="fa-solid fa-circle-check" style="margin-right:4px"></i> Active</span>
<span class="cert-badge"><i class="fa-solid fa-network-wired" style="margin-right:4px"></i> Routing & Switching</span>
<span class="cert-badge"><i class="fa-solid fa-lock" style="margin-right:4px"></i> Security Foundations</span>
</div>
</div>
</div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ SKILLS ═══════════ -->
<section class="section">
<div class="container">
<div class="section-header fade">
<span class="section-prefix">// Capabilities</span>
<h2 class="section-title">Skill Matrix</h2>
</div>

<div class="term-block fade" style="margin-bottom:24px">
<div class="term-bar">
<div class="term-dots"><span style="background:#ff5f57"></span><span style="background:#ffbd2e"></span><span style="background:#28ca42"></span></div>
<span class="term-bar-title">kovar@kali ~ capabilities</span>
</div>
<div class="term-body">
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ nmap -sV --script=skill-scan localhost</span></div>
<div><span class="out">Scanning dual capability matrix...</span></div>
<div><span class="ok">[COMPLETE] 10 skill vectors identified across Red & Blue teams.</span></div>
</div>
</div>

<div class="skills-grid fade fade-d1">
<!-- Red Team Panel -->
<div class="skill-panel">
<div class="skill-panel-header">
<div class="skill-panel-dot red"></div>
<span class="skill-panel-title red">Red Team — Offensive</span>
</div>
<div class="skill-list">
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-globe"></i> Web Exploitation</span>
<div class="skill-bar-wrap"><div class="skill-bar red" data-width="92"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-eye"></i> OSINT</span>
<div class="skill-bar-wrap"><div class="skill-bar red" data-width="90"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-bug"></i> Bug Bounty</span>
<div class="skill-bar-wrap"><div class="skill-bar red" data-width="88"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-flag"></i> CTF</span>
<div class="skill-bar-wrap"><div class="skill-bar red" data-width="94"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-microchip"></i> Reverse Engineering</span>
<div class="skill-bar-wrap"><div class="skill-bar red" data-width="65"></div></div>
</div>
</div>
<div class="skill-tools">
<span class="skill-tool">Burp Suite</span>
<span class="skill-tool">Nmap</span>
<span class="skill-tool">FFUF</span>
<span class="skill-tool">Metasploit</span>
<span class="skill-tool">Ghidra</span>
</div>
</div>

<!-- Blue Team Panel -->
<div class="skill-panel">
<div class="skill-panel-header">
<div class="skill-panel-dot blue"></div>
<span class="skill-panel-title blue">Blue Team — Defensive</span>
</div>
<div class="skill-list">
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-network-wired"></i> Network Security</span>
<div class="skill-bar-wrap"><div class="skill-bar blue" data-width="95"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-chart-line"></i> SIEM & Log Analysis</span>
<div class="skill-bar-wrap"><div class="skill-bar blue" data-width="88"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-fire-extinguisher"></i> Incident Response</span>
<div class="skill-bar-wrap"><div class="skill-bar blue" data-width="85"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-radar"></i> Threat Detection</span>
<div class="skill-bar-wrap"><div class="skill-bar blue" data-width="90"></div></div>
</div>
<div class="skill-item">
<span class="skill-name"><i class="fa-solid fa-lock"></i> System Hardening</span>
<div class="skill-bar-wrap"><div class="skill-bar blue" data-width="92"></div></div>
</div>
</div>
<div class="skill-tools">
<span class="skill-tool">Splunk</span>
<span class="skill-tool">Elastic</span>
<span class="skill-tool">Wireshark</span>
<span class="skill-tool">Sigma</span>
<span class="skill-tool">YARA</span>
<span class="skill-tool">Cisco FMC</span>
</div>
</div>
</div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ TECH STACK ═══════════ -->
<section class="section">
<div class="container">
<div class="section-header fade">
<span class="section-prefix">// Arsenal</span>
<h2 class="section-title">Tech Stack</h2>
</div>

<div class="tech-categories fade fade-d1">
<div>
<div class="tech-cat-label">Languages</div>
<div class="tech-row">
<span class="tech-badge"><i class="fa-brands fa-python"></i> Python</span>
<span class="tech-badge"><i class="fa-brands fa-js"></i> JavaScript</span>
<span class="tech-badge"><i class="fa-solid fa-terminal"></i> Bash</span>
<span class="tech-badge"><i class="fa-brands fa-golang"></i> Go</span>
</div>
</div>
<div>
<div class="tech-cat-label">Security Tools</div>
<div class="tech-row">
<span class="tech-badge"><i class="fa-solid fa-shield-virus"></i> Burp Suite</span>
<span class="tech-badge"><i class="fa-solid fa-magnifying-glass"></i> Wireshark</span>
<span class="tech-badge"><i class="fa-solid fa-skull-crossbones"></i> Metasploit</span>
<span class="tech-badge"><i class="fa-solid fa-radar"></i> Nmap</span>
<span class="tech-badge"><i class="fa-solid fa-bug"></i> FFUF</span>
</div>
</div>
<div>
<div class="tech-cat-label">Platforms</div>
<div class="tech-row">
<span class="tech-badge"><i class="fa-brands fa-linux"></i> Kali Linux</span>
<span class="tech-badge"><i class="fa-brands fa-windows"></i> Windows</span>
<span class="tech-badge"><i class="fa-solid fa-server"></i> Cisco NX-OS</span>
</div>
</div>
<div>
<div class="tech-cat-label">DevOps & Infrastructure</div>
<div class="tech-row">
<span class="tech-badge"><i class="fa-brands fa-docker"></i> Docker</span>
<span class="tech-badge"><i class="fa-solid fa-gears"></i> Ansible</span>
<span class="tech-badge"><i class="fa-brands fa-aws"></i> AWS</span>
</div>
</div>
</div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ PROJECTS ═══════════ -->
<section class="section">
<div class="container">
<div class="section-header fade">
<span class="section-prefix">// Operations</span>
<h2 class="section-title">Projects</h2>
</div>

<div class="term-block fade" style="margin-bottom:24px">
<div class="term-bar">
<div class="term-dots"><span style="background:#ff5f57"></span><span style="background:#ffbd2e"></span><span style="background:#28ca42"></span></div>
<span class="term-bar-title">kovar@kali ~ projects</span>
</div>
<div class="term-body">
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ ls -la /opt/projects/</span></div>
<div><span class="out">drwxr-xr-x  XSS Scanner Engine<br>drwxr-xr-x  Recon Pipeline<br>drwxr-xr-x  Network Segmentation Analyzer<br>drwxr-xr-x  Log Correlation Engine<br>drwxr-xr-x  CTF Writeup Collection</span></div>
</div>
</div>

<div class="fade fade-d1">
<!-- Project 1 -->
<div class="project-card red-proj">
<div class="project-header">
<div class="project-icon red"><i class="fa-solid fa-crosshairs"></i></div>
<span class="project-name">XSS Scanner Engine</span>
</div>
<p class="project-desc">Automated reflected and stored XSS detection with payload mutation and DOM-based vector discovery. Designed for high-throughput testing of enterprise web applications with customizable scan profiles.</p>
<div class="project-impact">Impact: Enabled systematic XSS identification across large web portfolios, reducing manual testing effort significantly.</div>
</div>

<!-- Project 2 -->
<div class="project-card red-proj">
<div class="project-header">
<div class="project-icon red"><i class="fa-solid fa-satellite-dish"></i></div>
<span class="project-name">Recon Pipeline</span>
</div>
<p class="project-desc">End-to-end reconnaissance automation chaining subdomain enumeration, port scanning, service fingerprinting, and web technology detection into a single streamlined pipeline.</p>
<div class="project-impact">Impact: Reduced recon phase time by 70% across engagements, enabling faster pivot to exploitation.</div>
</div>

<!-- Project 3 -->
<div class="project-card blue-proj">
<div class="project-header">
<div class="project-icon blue"><i class="fa-solid fa-diagram-project"></i></div>
<span class="project-name">Network Segmentation Analyzer</span>
</div>
<p class="project-desc">Tool that ingests network topology data and recommends microsegmentation policies based on asset criticality and traffic flow analysis. Integrates with Cisco infrastructure for policy deployment.</p>
<div class="project-impact">Impact: Identified 30+ segmentation gaps in production environments, leading to measurable risk reduction.</div>
</div>

<!-- Project 4 -->
<div class="project-card blue-proj">
<div class="project-header">
<div class="project-icon blue"><i class="fa-solid fa-chart-line"></i></div>
<span class="project-name">Log Correlation Engine</span>
</div>
<p class="project-desc">Custom log parser correlating events across firewalls, proxies, and endpoints to surface potential intrusion patterns missed by default SIEM correlation rules.</p>
<div class="project-impact">Impact: Improved detection rate of lateral movement indicators by 40% over baseline SIEM configuration.</div>
</div>

<!-- Project 5 -->
<div class="project-card neutral-proj">
<div class="project-header">
<div class="project-icon neutral"><i class="fa-solid fa-flag"></i></div>
<span class="project-name">CTF Writeup Collection</span>
</div>
<p class="project-desc">50+ detailed writeups covering active machines — from initial foothold through privilege escalation. Focused on realistic enterprise scenarios covering web, pwn, and forensics categories.</p>
<div class="project-impact">Impact: Internal training resource adopted by security team for skill development and methodology reference.</div>
</div>
</div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ STATS ═══════════ -->
<section class="section">
<div class="container">
<div class="section-header fade">
<span class="section-prefix">// Metrics</span>
<h2 class="section-title">GitHub Stats</h2>
</div>

<div class="term-block fade" style="margin-bottom:24px">
<div class="term-bar">
<div class="term-dots"><span style="background:#ff5f57"></span><span style="background:#ffbd2e"></span><span style="background:#28ca42"></span></div>
<span class="term-bar-title">kovar@kali ~ stats</span>
</div>
<div class="term-body">
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ ./fetch_github_stats --user kovar-cmk</span></div>
<div><span class="ok">[OK] Stats fetched successfully.</span></div>
</div>
</div>

<div class="stats-grid fade fade-d1">
<div class="stat-card">
<img src="https://github-readme-stats.vercel.app/api?username=kovar-cmk&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d0d0d&title_color=ff0040&icon_color=ff0040&text_color=c9d1d9" alt="GitHub Stats" loading="lazy" id="stats-card-1">
</div>
<div class="stat-card">
<img src="https://github-readme-streak-stats.herokuapp.com?user=kovar-cmk&theme=tokyonight&hide_border=true&background=0d0d0d&ring=ff0040&fire=ff0040&currStreakLabel=ff0040&sideLabels=c9d1d9&dates=444444" alt="Streak Stats" loading="lazy" id="stats-card-2">
</div>
<div class="stat-card">
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=kovar-cmk&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d0d0d&title_color=ff0040&text_color=c9d1d9" alt="Top Languages" loading="lazy" id="stats-card-3">
</div>
</div>
</div>
</section>

<div class="sep"></div>

<!-- ═══════════ CONTACT ═══════════ -->
<section class="section">
<div class="container">
<div class="section-header fade">
<span class="section-prefix">// Channel</span>
<h2 class="section-title">Contact</h2>
</div>

<div class="term-block fade" style="margin-bottom:20px">
<div class="term-bar">
<div class="term-dots"><span style="background:#ff5f57"></span><span style="background:#ffbd2e"></span><span style="background:#28ca42"></span></div>
<span class="term-bar-title">kovar@kali ~ contact</span>
</div>
<div class="term-body">
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ initiate_secure_channel --encrypt AES-256</span></div>
<div><span class="out">Establishing encrypted channel...</span></div>
<div><span class="ok">[OK] Secure channel established. Ready for communication.</span></div>
</div>
</div>

<div class="contact-grid fade fade-d1">
<a href="mailto:kovar.cmk@protonmail.com" class="contact-link"><i class="fa-solid fa-envelope"></i> kovar.cmk@protonmail.com</a>
<a href="#" class="contact-link"><i class="fa-brands fa-linkedin-in"></i> LinkedIn</a>
<a href="https://github.com/kovar-cmk" class="contact-link"><i class="fa-brands fa-github"></i> GitHub</a>
</div>
</div>
</section>

<!-- ═══════════ FOOTER ═══════════ -->
<footer class="footer">
<div class="container">
<div class="term-block fade" style="margin-bottom:16px">
<div class="term-body" style="padding:10px 18px">
<div><span class="prompt">kovar@kali</span>:<span style="color:#5555ff">~</span><span class="cmd">$ echo "Closing connection... Good hunting."</span></div>
<div><span class="out">Closing connection... Good hunting.</span></div>
</div>
</div>
<p class="footer-text"><span class="hl">kovar://</span> Designed as a security interface, not a template.</p>
</div>
</footer>

<!-- ═══════════ JAVASCRIPT ═══════════ -->
<script>
/* ── Mode Toggle ── */
let currentMode = 'red';

function toggleMode() {
    currentMode = currentMode === 'red' ? 'blue' : 'red';
    document.body.classList.toggle('blue-mode', currentMode === 'blue');

    // Update mode badge text
    document.querySelector('.mode-badge-text').textContent = currentMode === 'red' ? 'RED TEAM' : 'BLUE TEAM';
    document.querySelector('.mode-label-text').textContent = currentMode === 'red' ? 'Red Mode' : 'Blue Mode';

    // Update floating background alerts
    const alerts = document.querySelectorAll('.bg-alert');
    const redAlerts = ['BREACH DETECTED', 'FIREWALL BYPASSED', 'PERSISTENCE ACHIEVED'];
    const blueAlerts = ['THREAT NEUTRALIZED', 'PERIMETER INTACT', 'INCIDENT CONTAINED'];
    const set = currentMode === 'red' ? redAlerts : blueAlerts;
    alerts.forEach((el, i) => { el.textContent = set[i % set.length]; });

    // Update GitHub stats card colors
    const accent = currentMode === 'red' ? 'ff0040' : '0088ff';
    const c1 = document.getElementById('stats-card-1');
    const c2 = document.getElementById('stats-card-2');
    const c3 = document.getElementById('stats-card-3');
    if (c1) c1.src = c1.src.replace(/title_color=[^&]+/, 'title_color=' + accent).replace(/icon_color=[^&]+/, 'icon_color=' + accent);
    if (c2) c2.src = c2.src.replace(/ring=[^&]+/, 'ring=' + accent).replace(/fire=[^&]+/, 'fire=' + accent).replace(/currStreakLabel=[^&]+/, 'currStreakLabel=' + accent);
    if (c3) c3.src = c3.src.replace(/title_color=[^&]+/, 'title_color=' + accent);
}

// Keyboard shortcut for mode toggle
document.addEventListener('keydown', e => {
    if (e.key === 'm' || e.key === 'M') {
        if (document.activeElement.tagName !== 'INPUT') toggleMode();
    }
});

/* ── Cursor Glow ── */
const glow = document.getElementById('glow');
document.addEventListener('mousemove', e => {
    glow.style.left = e.clientX + 'px';
    glow.style.top = e.clientY + 'px';
});

/* ── Typing Effect ── */
const typingLines = [
    'Breaking systems to understand them.',
    'Defending systems to secure them.',
    'Cybersecurity Engineer | Red & Blue Team'
];
let lineIdx = 0, charIdx = 0, isDeleting = false;
const typingEl = document.getElementById('typing-text');

function typeLoop() {
    const current = typingLines[lineIdx];
    if (!isDeleting) {
        typingEl.textContent = current.substring(0, charIdx + 1);
        charIdx++;
        if (charIdx === current.length) {
            isDeleting = true;
            setTimeout(typeLoop, 2200);
            return;
        }
        setTimeout(typeLoop, 55);
    } else {
        typingEl.textContent = current.substring(0, charIdx - 1);
        charIdx--;
        if (charIdx === 0) {
            isDeleting = false;
            lineIdx = (lineIdx + 1) % typingLines.length;
            setTimeout(typeLoop, 400);
            return;
        }
        setTimeout(typeLoop, 30);
    }
}
typeLoop();

/* ── Scroll Reveal (IntersectionObserver) ── */
const fadeEls = document.querySelectorAll('.fade');
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            // Trigger skill bars inside this element
            entry.target.querySelectorAll('.skill-bar').forEach(bar => {
                bar.style.width = bar.dataset.width + '%';
            });
        }
    });
}, { threshold: 0.08, rootMargin: '0px 0px -40px 0px' });

fadeEls.forEach(el => observer.observe(el));

/* ── Background Canvas Particles ── */
const canvas = document.createElement('canvas');
canvas.style.cssText = 'position:fixed;inset:0;z-index:0;pointer-events:none';
document.body.prepend(canvas);
const ctx = canvas.getContext('2d');
let particles = [];

function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

function initParticles() {
    particles = [];
    const count = Math.min(50, Math.floor(window.innerWidth / 30));
    for (let i = 0; i < count; i++) {
        particles.push({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            vx: (Math.random() - 0.5) * 0.25,
            vy: (Math.random() - 0.5) * 0.25,
            r: Math.random() * 1.2 + 0.4,
            o: Math.random() * 0.4 + 0.08
        });
    }
}
initParticles();

function drawParticles() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    const isRed = currentMode === 'red';
    const r = isRed ? 255 : 0, g = isRed ? 0 : 136, b = isRed ? 64 : 255;

    for (let i = 0; i < particles.length; i++) {
        const p = particles[i];
        p.x += p.vx; p.y += p.vy;
        if (p.x < 0) p.x = canvas.width;
        if (p.x > canvas.width) p.x = 0;
        if (p.y < 0) p.y = canvas.height;
        if (p.y > canvas.height) p.y = 0;

        ctx.beginPath();
        ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(${r},${g},${b},${p.o})`;
        ctx.fill();

        for (let j = i + 1; j < particles.length; j++) {
            const p2 = particles[j];
            const dx = p.x - p2.x, dy = p.y - p2.y;
            const dist = Math.sqrt(dx * dx + dy * dy);
            if (dist < 110) {
                ctx.beginPath();
                ctx.moveTo(p.x, p.y);
                ctx.lineTo(p2.x, p2.y);
                ctx.strokeStyle = `rgba(${r},${g},${b},${0.05 * (1 - dist / 110)})`;
                ctx.lineWidth = 0.5;
                ctx.stroke();
            }
        }
    }
    requestAnimationFrame(drawParticles);
}
drawParticles();
</script>
</body>
</html>
