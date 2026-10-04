Digital Project Manager Portfolio · HTML
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Digital Project Manager Portfolio</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Permanent+Marker&family=Patrick+Hand&display=swap" rel="stylesheet">
<style>
:root{--ink:#2b2a28;--paper:#efece3;--r:90px;--cx:50%;--cy:62%;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
html{scroll-behavior:smooth;scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--paper);color:var(--ink);font-family:'Patrick Hand',cursive,sans-serif;overflow-x:hidden}
.marker{font-family:'Permanent Marker','Patrick Hand',cursive}
@media (pointer:fine){body,a,button{cursor:none}}
/* layers */
.fixed-layer{position:fixed;inset:0;pointer-events:none}
#doodles{filter:grayscale(1);opacity:.75}
#colors{mix-blend-mode:multiply;-webkit-mask-image:radial-gradient(circle at var(--cx) var(--cy),#000 var(--r),transparent calc(var(--r) + 90px));mask-image:radial-gradient(circle at var(--cx) var(--cy),#000 var(--r),transparent calc(var(--r) + 90px))}
#colors i{position:absolute;inset:0;opacity:0;transition:opacity 1.2s ease}
#colors i.on{opacity:1}
.c-hero{background:radial-gradient(circle at 50% 62%,#ffd27a,#ff9ec4 60%,#9fd8ff)}
.c-summer{background:linear-gradient(160deg,#7ed957,#2fa84f 60%,#a8e86a)}
.c-autumn{background:linear-gradient(160deg,#f3b13e,#d9682a 55%,#7a4a26)}
.c-winter{background:linear-gradient(160deg,#e9f5ff,#8cc4ee 55%,#4f86c6)}
.c-spring{background:linear-gradient(160deg,#ffffff,#c8f2a6 55%,#6fdc6a)}
#fx{z-index:5}
/* path */
#path path{fill:none;stroke:var(--ink);stroke-width:3;stroke-dasharray:2 12;stroke-linecap:round;opacity:.55}
/* hero + sections */
section{position:relative;z-index:2}
.stage{min-height:150vh}
.sticky-wrap{position:sticky;top:12vh;padding:0 4vw;opacity:0;transform:translateY(40px);transition:opacity .9s ease,transform .9s cubic-bezier(.2,.8,.2,1)}
.stage.in .sticky-wrap{opacity:1;transform:none}
.giant{display:block;line-height:.95;color:rgba(255,255,255,.55);-webkit-text-stroke:3px var(--ink);paint-order:stroke fill;text-shadow:6px 6px 0 rgba(43,42,40,.18);filter:url(#wob);background:none;border:0;padding:0;text-align:left;transition:transform .35s cubic-bezier(.2,.8,.2,1)}
.giant:hover{transform:rotate(-2deg) scale(1.02)}
.hint{display:inline-block;margin-top:1rem;padding:.3rem .9rem;border:2px dashed var(--ink);border-radius:999px;background:rgba(255,255,255,.55);font-size:1.15rem}
/* character */
#hero-char{position:fixed;left:0;top:0;z-index:6;width:112px;height:170px;pointer-events:none;will-change:transform}
#hero-char svg{width:100%;height:100%;overflow:visible}
#hero-char{--top:#eaf1f6;--top2:#c9d8e4;--bt:#dfe9f1;--bt2:#b7c7d6;--sock:#fff;--shoe:#1c1c22;--hat:#f3d27a;--hat2:#d6513f;--sc:#e8505b;--bag:#8a5a34}
#hero-char[data-s=summer]{--top:#fff3b8;--top2:#f6dc7a;--bt:#ffd85a;--bt2:#f0b93a;--shoe:#fdfdfd}
#hero-char[data-s=autumn]{--sc:#c8452f;--top:#c4622d;--top2:#8f4516;--bt:#8a3b2a;--bt2:#e0a33a;--sock:#8a2f3a;--shoe:#5a3220;--hat:#7a3e1f}
#hero-char[data-s=winter]{--top:#4f7fc8;--top2:#365f9e;--bt:#3a62a8;--bt2:#fff;--shoe:#f4f7fb;--hat:#e8505b;--hat2:#fff}
#hero-char[data-s=spring]{--top:#cdeec8;--top2:#9fd49a;--bt:#d9c6f0;--bt2:#b99ad6;--shoe:#f6a9c6}
#hero-char[data-v=back] #frontV,#hero-char[data-v=back] #fHairBackG,#hero-char[data-v=front] #backV{display:none}
#hero-char .TOPf{fill:var(--top)}
#hero-char svg *{transition:fill .8s ease,stroke .8s ease}
#hero-char .TOPs{stroke:var(--top)}#hero-char .TOP2s{stroke:var(--top2)}#hero-char .HAT2s{stroke:var(--hat2)}#hero-char .BT{fill:var(--bt)}#hero-char .BT2{fill:var(--bt2)}#hero-char .SHOE{fill:var(--shoe)}#hero-char .SOCK{fill:var(--sock)}#hero-char .HAT{fill:var(--hat)}#hero-char .HAT2{fill:var(--hat2)}#hero-char .SC{fill:var(--sc)}#hero-char .BAG{fill:var(--bag)}
@keyframes bob{50%{transform:translateY(-3px) rotate(2deg)}}
.outfit{opacity:0;transition:opacity .6s ease}
.outfit.on{opacity:1}
/* cursor */
#cur,#ring{position:fixed;left:0;top:0;z-index:100;pointer-events:none;border-radius:50%}
#cur{width:8px;height:8px;background:var(--ink);margin:-4px 0 0 -4px}
#ring{width:34px;height:34px;margin:-17px 0 0 -17px;border:2px solid var(--ink);transition:width .25s,height .25s,margin .25s,background .25s}
#ring.big{width:64px;height:64px;margin:-32px 0 0 -32px;background:rgba(255,255,255,.35)}
@media (pointer:coarse){#cur,#ring{display:none}}
/* drawer */
#shade{position:fixed;inset:0;z-index:50;background:rgba(30,28,25,.45);opacity:0;pointer-events:none;transition:opacity .4s}
#drawer{position:fixed;top:0;right:0;bottom:0;z-index:60;width:min(540px,100%);background:var(--paper);border-left:3px solid var(--ink);padding:2rem 1.75rem calc(2rem + env(safe-area-inset-bottom,0px));overflow-y:auto;transform:translateX(102%);transition:transform .5s cubic-bezier(.2,.8,.2,1);box-shadow:-12px 0 0 rgba(43,42,40,.12)}
body.open #shade{opacity:1;pointer-events:auto}
body.open #drawer{transform:none}
#drawer h3{font-size:2.6rem;line-height:1;margin:.3rem 0 1rem}
#drawer li{margin:.35rem 0;font-size:1.2rem}
.chip{display:inline-block;margin:.2rem .25rem .2rem 0;padding:.15rem .75rem;border:2px solid var(--ink);border-radius:999px;font-size:1.1rem;background:#fff8}
.close{position:absolute;top:1rem;right:1.2rem;font-size:2rem;background:none;border:0;color:var(--ink)}
#prog{position:fixed;right:14px;top:50%;transform:translateY(-50%);z-index:20;display:flex;flex-direction:column;gap:12px}
#prog b{width:12px;height:12px;border:2px solid var(--ink);border-radius:50%;background:transparent;transition:.3s}
#prog b.on{background:var(--ink);transform:scale(1.35)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--paper:#efece3}}
@media (prefers-reduced-motion:reduce){html{scroll-behavior:auto}}
</style>
</head>
<body>
<svg width="0" height="0" style="position:absolute"><filter id="wob"><feTurbulence type="fractalNoise" baseFrequency=".02" numOctaves="2" seed="4"/><feDisplacementMap in="SourceGraphic" scale="7"/></filter></svg>
 
<div id="doodles" class="fixed-layer"></div>
<div id="colors" class="fixed-layer">
  <i class="c-hero on" data-k="hero"></i><i class="c-summer" data-k="summer"></i><i class="c-autumn" data-k="autumn"></i><i class="c-winter" data-k="winter"></i><i class="c-spring" data-k="spring"></i>
</div>
<canvas id="fx" class="fixed-layer"></canvas>
<svg id="path" class="absolute left-0 top-0 w-full z-[1] pointer-events-none"><path d=""/></svg>
<div id="cur"></div><div id="ring"></div>
<nav id="prog"><b class="on"></b><b></b><b></b><b></b><b></b></nav>
 
<div id="hero-char" data-s="hero" data-v="front"><div class="bob">
<svg viewBox="-50 -20 100 152">
<defs><g id="fl"><g fill="currentColor"><circle r="2.4" cy="-2.8"/><circle r="2.4" cx="2.7" cy="-.9"/><circle r="2.4" cx="1.7" cy="2.3"/><circle r="2.4" cx="-1.7" cy="2.3"/><circle r="2.4" cx="-2.7" cy="-.9"/></g><circle r="1.5" fill="#ffd54f" stroke="none"/></g></defs>
<ellipse id="shd" cx="0" cy="122" rx="13" ry="3.6" fill="#1b3a4a" opacity=".28"/>
<g id="bodyG" stroke-linejoin="round" stroke-linecap="round">
<g id="fHairBackG">
 <g id="fHairLow">
  <polygon points="-19,38 19,38 22,78 18,74 15,80 10,75 7,81 2,76 -2,82 -6,76 -10,81 -14,75 -18,79 -22,78" fill="#a8683a" stroke="#6b3d1f" stroke-width=".8"/>
  <path d="M-13 40Q-15 60 -17 76M-6 40Q-7 62 -8 78M0 40V78M6 40Q7 62 8 78M13 40Q15 60 17 76" stroke="#8a5028" stroke-width=".8" fill="none" opacity=".85"/>
 </g>
 <path d="M0 -.5Q-18 -.5 -18.5 22L-19.5 46Q-9 49 0 46Q9 49 19.5 46L18.5 22Q18 -.5 0 -.5Z" fill="#b2713f" stroke="#6b3d1f" stroke-width=".8"/>
 <path d="M-8 6Q-9 28 -11 44M8 6Q9 28 11 44M-14 10Q-16 28 -17 44M14 10Q16 28 17 44" stroke="#8a5028" stroke-width=".8" fill="none" opacity=".8"/>
</g>
<!-- LEGS (left; right mirrored + animated by JS) -->
<g class="legL">
 <path d="M-9 74L-2.4 74L-3.6 108L-8 108Z" fill="#f6d3b8" stroke="#c4896c" stroke-width=".7"/>
 <g class="outfit" data-o="winter"><path d="M-9.4 74L-2 74L-3.4 112L-8.4 112Z" fill="#2d3150" stroke="#1b1e33" stroke-width=".6"/></g>
 <g class="outfit" data-o="hero spring"><path d="M-8.2 99L-3.5 99L-3.6 112L-8 112Z" fill="#fff" stroke="#c9d3da" stroke-width=".6"/></g>
 <g class="outfit" data-o="autumn"><path d="M-8.8 88L-3.1 88L-3.6 112L-8.1 112Z" class="SOCK"/><path d="M-8.7 91H-3.2M-8.6 94H-3.2" stroke="#fff" stroke-width="1.2" opacity=".7"/></g>
 <g class="outfit" data-o="summer"><path d="M-8 107L-3.6 107L-3.7 112L-8 112Z" fill="#fff" stroke="#c9d3da" stroke-width=".6"/></g>
 <g class="outfit" data-o="winter"><path d="M-8.8 99L-3.1 99L-2.8 112L-9.2 112Z" fill="#f4f7fb" stroke="#9fb3c8" stroke-width=".6"/><ellipse cx="-6" cy="99" rx="4.3" ry="2" fill="#fff" stroke="#cfd8e3" stroke-width=".6" stroke-dasharray="1.2 1.2"/><path d="M-10.5 125H-1.5M-8.5 122.5V125M-3.5 122.5V125" stroke="#cfd8e3" stroke-width="1.6" fill="none"/></g>
 <path d="M-8.8 111L-3 111Q-1.8 116 -2.6 121Q-6 123 -9.6 121Q-10 116 -8.8 111Z" class="SHOE" stroke="#14141a" stroke-width=".7"/>
 <path d="M-9.6 121Q-6 123 -2.6 121" stroke="#0e0e12" stroke-width="1.6" fill="none"/>
 <path d="M-8 114Q-6 112.8 -4 114" stroke="#fff" stroke-opacity=".4" fill="none"/>
 <g class="outfit" data-o="summer"><path d="M-8 114.5H-3.6M-8.2 117H-3.4" stroke="#9aa" stroke-width=".8" fill="none"/></g>
 <g class="outfit" data-o="spring"><path d="M-9.4 116H-2.4" stroke="#fff" stroke-width="1.2" fill="none"/><circle cx="-6" cy="116" r="1" fill="#ffd54f" stroke="none"/></g>
</g>
<!-- BOTTOMS -->
<g class="outfit" data-o="hero"><polygon points="-15,54 15,54 21,82 -21,82" class="BT" stroke="#8ea4b8" stroke-width=".7"/><path d="M-8 56L-10 82M0 56V82M8 56L10 82" stroke="#8ea4b8" stroke-width=".6" fill="none"/></g>
<g class="outfit" data-o="summer"><polygon points="-15,52 15,52 25,86 20,83 15,87 10,83 5,87 0,83 -5,87 -10,83 -15,87 -20,83 -25,86" class="BT" stroke="#c9962a" stroke-width=".7"/><g fill="#fff" opacity=".85" stroke="none"><circle cx="-16" cy="80" r="1.5"/><circle cx="-6" cy="82" r="1.5"/><circle cx="7" cy="81" r="1.5"/><circle cx="17" cy="80" r="1.5"/></g></g>
<g class="outfit" data-o="autumn"><polygon points="-15,54 15,54 22,85 -22,85" class="BT" stroke="#5a1f15" stroke-width=".7"/><path d="M-19.5 78H19.5M-20.5 82H20.5M-8 56L-10 85M0 56V85M8 56L10 85" fill="none" stroke-width=".9" style="stroke:var(--bt2)"/></g>
<g class="outfit" data-o="winter"><polygon points="-16,50 16,50 24,92 -24,92" class="BT" stroke="#27457a" stroke-width=".7"/><path d="M-19 68Q0 72 19 68M-22 80Q0 84 22 80M0 52V92" fill="none" stroke="#1d3e75" stroke-width=".7" opacity=".7"/><path d="M-24 91.5H24" stroke="#fff" stroke-width="3.6" fill="none"/><path d="M-24 93.4H24" stroke="#fff" stroke-width="2.2" stroke-dasharray="1.4 2.4" fill="none"/></g>
<g class="outfit" data-o="spring"><polygon points="-15,54 15,54 22,76 -22,76" class="BT" stroke="#a58ac4" stroke-width=".7"/><polygon points="-20,72 20,72 27,88 22,86 17,89 11,86 5,89 0,86 -5,89 -11,86 -17,89 -22,86 -27,88" class="BT2" stroke="#8a6fb0" stroke-width=".7"/></g>
<!-- ARMS (left; right mirrored + animated by JS) -->
<g class="armL">
 <path d="M-15 31L-30 44L-33 31" fill="none" stroke="#c4896c" stroke-width="6.4"/>
 <path d="M-15 31L-30 44L-33 31" fill="none" stroke="#f6d3b8" stroke-width="5"/>
 <g class="outfit" data-o="summer"><path d="M-15 31L-22 37" fill="none" class="TOPs" stroke-width="9.5"/><path d="M-20.5 36L-23.2 38.4" fill="none" class="TOP2s" stroke-width="10.4"/></g>
 <g class="outfit" data-o="autumn"><path d="M-15 31L-30 44L-32.2 35" fill="none" class="TOPs" stroke-width="7.2"/><path d="M-32.1 35.6L-32.8 32.4" fill="none" class="TOP2s" stroke-width="7.8"/></g>
 <g class="outfit" data-o="winter"><path d="M-15 31L-30 44L-32.4 36" fill="none" class="TOPs" stroke-width="10.5"/><path d="M-21 37.4L-25 41M-29 44L-31 39.5" fill="none" stroke="#fff" stroke-opacity=".3" stroke-width="1"/><path d="M-32.3 36L-32.9 32.8" fill="none" stroke="#fff" stroke-width="9.6"/></g>
 <g class="outfit" data-o="hero spring"><path d="M-15 31L-30 44L-31.6 38.5" fill="none" class="TOPs" stroke-width="6.8"/><path d="M-31 40.4L-32 36.6" fill="none" class="TOP2s" stroke-width="8.2"/></g>
 <circle cx="-33" cy="29.2" r="3.4" fill="#f6d3b8" stroke="#c4896c" stroke-width=".7"/><path d="M-35 28.2Q-33 26.6 -31 28M-34.8 30.4H-31.2" fill="none" stroke="#c4896c" stroke-width=".6"/>
 <g class="outfit" data-o="winter"><circle cx="-33" cy="29.2" r="4.8" class="SC" stroke="#a02d38" stroke-width=".7"/></g>
</g>
<!-- FRONT VIEW (shown while scrolling down) -->
<g id="frontV">
<g class="outfit" data-o="hero"><path d="M-13 35Q0 32 13 35L15 56Q0 59 -15 56Z" class="TOPf" stroke="#9fb3c8" stroke-width=".7"/><path d="M-10 35L0 47L10 35L13 38L0 53L-13 38Z" fill="#c9d8e4" stroke="#9fb3c8" stroke-width=".6"/><path d="M0 46L-6 42L-6 50ZM0 46L6 42L6 50Z" fill="#d6513f" stroke="#9a2f22" stroke-width=".5"/><circle cx="0" cy="46" r="1.6" fill="#b83a2c" stroke="none"/></g>
<g class="outfit" data-o="summer"><path d="M-13 35Q0 32 13 35L13 42L-13 42Z" fill="#f6d3b8" stroke="#c4896c" stroke-width=".6"/><path d="M-12 41Q0 38.5 12 41L14 56Q0 59 -14 56Z" class="BT" stroke="#c9962a" stroke-width=".7"/><path d="M-8 41L-7.5 34M8 41L7.5 34" stroke="#f0b93a" stroke-width="2.2" fill="none"/><path d="M-14 54Q0 58 14 54" stroke="#ff6f91" stroke-width="3" fill="none"/><g fill="#fff" opacity=".85" stroke="none"><circle cx="-6" cy="47" r="1.3"/><circle cx="5" cy="49" r="1.3"/></g></g>
<g class="outfit" data-o="autumn"><path d="M-14 35Q0 31 14 35L15 57Q0 60 -15 57Z" class="TOPf" stroke="#5a2a10" stroke-width=".7"/><path d="M-4.5 34L4.5 34L5.5 58L-5.5 58Z" fill="#f3c14b" stroke="#c9962a" stroke-width=".6"/><path d="M-4.5 34L0 46L4.5 34" fill="none" stroke="#5a2a10" stroke-width=".6"/><g fill="#e0a33a" stroke="#5a2a10" stroke-width=".5"><circle cx="-8" cy="47" r="1.3"/><circle cx="-8.4" cy="53" r="1.3"/><circle cx="8" cy="47" r="1.3"/><circle cx="8.4" cy="53" r="1.3"/></g></g>
<g class="outfit" data-o="winter"><path d="M-15 35Q0 31 15 35L17 60Q0 64 -17 60Z" class="TOPf" stroke="#27457a" stroke-width=".7"/><path d="M-16 44Q0 48 16 44M-16.5 53Q0 57 16.5 53M0 36V61" fill="none" stroke="#1d3e75" stroke-width=".7" opacity=".7"/><rect x="-1.2" y="46" width="2.4" height="4" rx=".8" fill="#cfd8e3" stroke="#6b7f99" stroke-width=".4"/></g>
<g class="outfit" data-o="spring"><path d="M-13 35Q0 32 13 35L15 56Q0 59 -15 56Z" class="TOPf" stroke="#9fd49a" stroke-width=".7"/><path d="M-5 34L5 34L6 57L-6 57Z" fill="#fff" stroke="#d6e0d4" stroke-width=".5"/><path d="M0 40L-6 36L-6 44ZM0 40L6 36L6 44Z" fill="#ff9ec8" stroke="#d96a9a" stroke-width=".5"/><circle cx="0" cy="40" r="1.7" fill="#ff7fb0" stroke="none"/></g>
<rect x="-3.6" y="31" width="7.2" height="8" fill="#e8bd9d" stroke="#c4896c" stroke-width=".6"/>
<g class="outfit" data-o="autumn winter"><path d="M-13 33Q0 40 13 33L13 40Q0 47 -13 40Z" class="SC" stroke="#8a2230" stroke-width=".7"/><path d="M-4 42L-7 66L1 67L3 44Z" class="SC" stroke="#8a2230" stroke-width=".7"/><path d="M-5 52L2 53M-6 59L1 60M-9 36v5M-3 38v5M3 38v5M9 36v5" stroke="#fff" stroke-opacity=".6" fill="none"/></g>
<circle cx="-13.6" cy="21" r="2.6" fill="#f6d3b8" stroke="#c4896c" stroke-width=".6"/><circle cx="13.6" cy="21" r="2.6" fill="#f6d3b8" stroke="#c4896c" stroke-width=".6"/>
<ellipse cx="0" cy="19" rx="13.5" ry="15" fill="#f6d3b8" stroke="#c4896c" stroke-width=".8"/>
<g stroke="none"><ellipse cx="-9.5" cy="27" rx="3" ry="1.7" fill="#ff8f9f" opacity=".5"/><ellipse cx="9.5" cy="27" rx="3" ry="1.7" fill="#ff8f9f" opacity=".5"/></g>
<g id="fEyes">
 <g><ellipse cx="-6" cy="21" rx="3.7" ry="4.6" fill="#fff" stroke="#3a2419" stroke-width=".5"/><ellipse cx="-6" cy="21.6" rx="2.7" ry="3.8" fill="#7a4a2c" stroke="none"/><ellipse cx="-6" cy="21.8" rx="1.5" ry="2.4" fill="#2a170f" stroke="none"/><circle cx="-7.1" cy="19.6" r="1.1" fill="#fff" stroke="none"/><circle cx="-4.8" cy="23.4" r=".6" fill="#fff" stroke="none"/></g>
 <g><ellipse cx="6" cy="21" rx="3.7" ry="4.6" fill="#fff" stroke="#3a2419" stroke-width=".5"/><ellipse cx="6" cy="21.6" rx="2.7" ry="3.8" fill="#7a4a2c" stroke="none"/><ellipse cx="6" cy="21.8" rx="1.5" ry="2.4" fill="#2a170f" stroke="none"/><circle cx="4.9" cy="19.6" r="1.1" fill="#fff" stroke="none"/><circle cx="7.2" cy="23.4" r=".6" fill="#fff" stroke="none"/></g>
</g>
<path d="M-10.2 17.2Q-6 14.2 -2 17.6M10.2 17.2Q6 14.2 2 17.6M-10.2 17.2l-1.6 .8M10.2 17.2l1.6 .8" stroke="#3a2419" stroke-width="1.4" fill="none"/>
<path d="M-10 13Q-6 11.4 -2.5 13M10 13Q6 11.4 2.5 13" stroke="#6b3d1f" stroke-width="1.1" fill="none"/>
<path d="M0 25.4l.6 1.1M-2.8 30Q0 32.2 2.8 30" stroke="#b0554a" stroke-width=".9" fill="none"/>
<path d="M-14.5 19Q-17 -1 0 -1Q17 -1 14.5 19Q12 9 5 7Q.5 12.5 -4 7.5Q-10 8 -14.5 19Z" fill="#b2713f" stroke="#6b3d1f" stroke-width=".8"/>
<path d="M-6 2Q-7 8 -9 14M4 2Q4 6 3 9M9 3Q11 9 11.5 14" stroke="#8a5028" stroke-width=".7" fill="none"/><path d="M-9 3Q-3 0 4 2" stroke="#d9a070" stroke-width=".9" fill="none"/>
<g class="flockL"><path d="M-14 8Q-19 24 -18 44Q-17 62 -20 71Q-14 67 -12.5 62Q-10.5 44 -11 29Q-11.5 17 -14 8Z" fill="#b2713f" stroke="#6b3d1f" stroke-width=".8"/><path d="M-15 20Q-16 40 -17 58M-13 24Q-13.5 42 -14.5 60" stroke="#8a5028" stroke-width=".7" fill="none"/><path d="M-16.5 14Q-17.5 30 -18 46" stroke="#d9a070" stroke-width=".8" fill="none"/></g>
<g class="outfit" data-o="summer"><ellipse cx="0" cy="3" rx="31" ry="9" class="HAT" stroke="#c29a3d" stroke-width=".8"/><path d="M-22 3Q0 11 22 3M-26 2Q0 12 26 2" fill="none" stroke="#c29a3d" stroke-width=".5" opacity=".7"/><path d="M-15 5Q-15 -11 0 -11Q15 -11 15 5Z" class="HAT" stroke="#c29a3d" stroke-width=".8"/><path d="M-15 3Q0 8 15 3" fill="none" class="HAT2s" stroke-width="4.6"/><path d="M-9 8L-14 30L-10 28L-8 34L-5 9Z" class="HAT2" stroke="#9a2f22" stroke-width=".6"/></g>
<g class="outfit" data-o="autumn"><ellipse cx="-2" cy="1" rx="19" ry="8.5" transform="rotate(-8 -2 1)" class="HAT" stroke="#4a2410" stroke-width=".8"/><path d="M-15 3Q-2 9 12 1" fill="none" stroke="#fff" stroke-opacity=".18" stroke-width="1.4"/><circle cx="-3" cy="-7" r="2.2" class="HAT" stroke="#4a2410" stroke-width=".7"/><path d="M10 4L13 0L16 4L13 7Z" fill="#e8892f" stroke="#8f4516" stroke-width=".5"/></g>
<g class="outfit" data-o="winter"><path d="M-16 10Q-17 -6 0 -7Q17 -6 16 10Q0 14 -16 10Z" class="HAT" stroke="#a02d38" stroke-width=".8"/><path d="M-16.5 5Q0 10 16.5 5L16.5 12Q0 17 -16.5 12Z" fill="#fff" stroke="#cfd8e3" stroke-width=".7"/><path d="M-12 8v7M-6 9v7M0 9.5v7M6 9v7M12 8v7" stroke="#cfd8e3" fill="none" stroke-width=".7"/><circle cx="0" cy="-9" r="4.8" fill="#fff" stroke="#cfd8e3" stroke-width=".7"/></g>
<g class="outfit" data-o="spring"><path d="M-15 14Q0 -4 15 14" fill="none" stroke="#ff9ec8" stroke-width="2.2"/><path d="M11 3L5 -1L5 7ZM11 3L17 -1L17 7Z" fill="#ff9ec8" stroke="#d96a9a" stroke-width=".6"/><circle cx="11" cy="3" r="1.8" fill="#ff7fb0" stroke="none"/><g stroke-width=".5" stroke="#8a5028"><use href="#fl" x="-12" y="5" style="color:#fff"/><use href="#fl" x="-16" y="12" style="color:#b99ad6"/></g></g>
</g>
<g id="backV">
<!-- HAIR: lower sway layer + base -->
<g id="hairLow">
 <polygon points="-18,38 18,38 21,76 17,72 14,78 9,73 6,79 1,74 -3,80 -7,74 -11,79 -15,73 -19,77 -21,76" fill="#a8683a" stroke="#6b3d1f" stroke-width=".8"/>
 <path d="M-12 40Q-14 60 -16 74M-6 40Q-7 60 -8 76M0 40V76M6 40Q7 60 8 76M12 40Q14 60 16 74" stroke="#8a5028" stroke-width=".8" fill="none" opacity=".85"/>
 <path d="M-9 42Q-10 58 -12 72M3 42Q4 58 5 74M14 42Q15 56 17 70" stroke="#d9a070" stroke-width=".9" fill="none" opacity=".75"/>
</g>
<g id="hairBase">
 <path d="M0 -.5Q-17 -.5 -17.5 22L-18.5 46Q-9 49 0 46Q9 49 18.5 46L17.5 22Q17 -.5 0 -.5Z" fill="#b2713f" stroke="#6b3d1f" stroke-width=".8"/>
 <path d="M-9 4Q0 -1 9 4Q6 10 0 11Q-6 10 -9 4Z" fill="#d39a64" opacity=".55" stroke="none"/>
 <path d="M0 3Q-1 24 -2 46M-6 4Q-8 25 -10 46M6 4Q8 25 10 46M-12 8Q-14 27 -15 46M12 8Q14 27 15 46" stroke="#8a5028" stroke-width=".8" fill="none" opacity=".85"/>
 <path d="M-4 8Q-5 26 -6 44M9 10Q11 26 12 44M-16 14Q-17 30 -17 44" stroke="#d9a070" stroke-width=".9" fill="none" opacity=".75"/>
</g>
<!-- ACCESSORIES -->
<g class="outfit" data-o="autumn"><path d="M-9 24L-10 40M9 24L10 40" stroke="#4a2c1a" stroke-width="2.2" fill="none"/><rect x="-10" y="28" width="20" height="26" rx="4" class="BAG" stroke="#4a2c1a" stroke-width=".8"/><path d="M-10 36Q0 41 10 36" fill="none" stroke="#4a2c1a" stroke-width=".8"/><rect x="-2.5" y="38" width="5" height="4" rx="1" fill="#e0a33a" stroke="#4a2c1a" stroke-width=".6"/><circle cx="8" cy="57" r="1.8" fill="#e0a33a" stroke="#4a2c1a" stroke-width=".5"/></g>
<g class="outfit" data-o="winter"><path d="M-17 22Q0 28 17 22L16.5 31Q0 37 -16.5 31Z" class="SC" stroke="#a02d38" stroke-width=".7"/><path d="M5 33L12 68L4 70L1 36Z" class="SC" stroke="#a02d38" stroke-width=".7"/><path d="M3 46L10 44M4 56L11 54M-9 26v5M-3 27v5M3 27v5M9 26v5" stroke="#fff" stroke-opacity=".65" fill="none"/></g>
<g class="outfit" data-o="summer"><ellipse cx="0" cy="6" rx="31" ry="11" class="HAT" stroke="#c29a3d" stroke-width=".8"/><path d="M-22 6Q0 14 22 6M-26 5Q0 16 26 5" fill="none" stroke="#c29a3d" stroke-width=".5" opacity=".7"/><path d="M-15 9Q-15 -7 0 -7Q15 -7 15 9Z" class="HAT" stroke="#c29a3d" stroke-width=".8"/><path d="M-15 7Q0 12 15 7" fill="none" class="HAT2s" stroke-width="4.6"/><path d="M6 10L12 42L8 40L5 46L2 11Z" class="HAT2" stroke="#9a2f22" stroke-width=".6"/></g>
<g class="outfit" data-o="autumn"><ellipse cx="-1" cy="5" rx="19" ry="9" transform="rotate(-6 -1 5)" class="HAT" stroke="#4a2410" stroke-width=".8"/><path d="M-14 6Q-1 12 12 4" fill="none" stroke="#fff" stroke-opacity=".18" stroke-width="1.4"/><circle cx="-2" cy="-4" r="2.2" class="HAT" stroke="#4a2410" stroke-width=".7"/></g>
<g class="outfit" data-o="winter"><path d="M-17.5 17Q-19 -9 0 -10Q19 -9 17.5 17Q0 21 -17.5 17Z" class="HAT" stroke="#a02d38" stroke-width=".8"/><path d="M-18 12Q0 17 18 12L18 19Q0 24 -18 19Z" fill="#fff" stroke="#cfd8e3" stroke-width=".7"/><path d="M-12 14v7M-6 15v7M0 15.5v7M6 15v7M12 14v7" stroke="#cfd8e3" fill="none" stroke-width=".7"/><circle cx="0" cy="-13" r="5.5" fill="#fff" stroke="#cfd8e3" stroke-width=".7"/></g>
<g class="outfit" data-o="spring"><path d="M-16 12Q0 -3 16 12" fill="none" stroke="#ff9ec8" stroke-width="2.4"/><path d="M0 8L-10 2L-10 14ZM0 8L10 2L10 14Z" fill="#ff9ec8" stroke="#d96a9a" stroke-width=".7"/><circle cx="0" cy="8" r="2.4" fill="#ff7fb0" stroke="#d96a9a" stroke-width=".6"/><g stroke-width=".5" stroke="#8a5028"><use href="#fl" x="-14" y="14" style="color:#fff"/><use href="#fl" x="14" y="15" style="color:#b99ad6"/></g></g>
</g></g>
</svg></div></div>
 
<main>
  <section id="hero" data-season="hero" class="min-h-screen flex flex-col items-center justify-start text-center px-6" style="padding-top:12vh">
    <p class="text-xl tracking-widest uppercase">Project Manager · Game-Design Minded</p>
    <h1 class="marker text-[11vw] md:text-[8vw] leading-none mt-3" style="filter:url(#wob)">THE PLAYABLE<br>PROJECT</h1>
    <p class="mt-6 text-2xl max-w-xl">A pencil map of four seasons. Scroll to follow the path — colour follows the traveller.</p>
    <p class="mt-auto pb-8 text-xl animate-bounce">↓ scroll to explore</p>
  </section>
 
  <section id="s1" data-season="summer" class="stage"><div class="sticky-wrap">
    <button class="giant marker hot" data-open="summer" style="font-size:11vw">ABOUT ME Creative-minded Digital Project Manager with 3+ years of experience turning ideas into structured, deliverable digital projects. I enjoy working where technology, creativity and people meet — translating ideas and business requirements into clear plans, coordinating designers and developers, solving problems, and keeping projects moving from concept to final delivery.

My background in IT and AI project management has given me a strong understanding of digital product development, Agile/Scrum, UX/UI, frontend and backend workflows, QA and stakeholder management. 

At the same time, my experience and passion for 3D, visual design, animation and game development allow me to understand and communicate with creative teams. I’m particularly interested in digital experiences, creative campaigns, websites, interactive products and game development - projects where good organization is important, but creativity is what makes the final result stand out.</button>
    <span class="hint hot">☀ Summer — tap the title to open</span></div></section>
 
  <section id="s2" data-season="autumn" class="stage"><div class="sticky-wrap">
    <button class="giant marker hot" data-open="autumn" style="font-size:8vw">MY EXPERIENCE </button>
    <span class="hint hot">🍂 Autumn — tap the title to open</span></div></section>
 
  <section id="s3" data-season="winter" class="stage"><div class="sticky-wrap">
    <button class="giant marker hot" data-open="winter" style="font-size:15vw">SKILLS</button>
    <span class="hint hot">❄ Winter — tap the title to open</span></div></section>
 
  <section id="s4" data-season="spring" class="stage" style="min-height:130vh"><div class="sticky-wrap">
    <button class="giant marker hot" data-open="spring" style="font-size:8vw">CERTIFICATION</button>
    <span class="hint hot">🌱 Spring — tap the title to open</span></div></section>
</main>
 
<div id="shade"></div>
<aside id="drawer" aria-hidden="true"><button class="close hot" aria-label="Close">✕</button><div id="dbody"></div></aside>
 
<script>
const $=(s,c=document)=>c.querySelector(s),$$=(s,c=document)=>[...c.querySelectorAll(s)];
const SEASONS=['hero','summer','autumn','winter','spring'];
const CONTACT=`<p class="mt-6"><span class="chip">✉ hello@yourname.com</span><span class="chip">in/your-profile</span><span class="chip">yourname.dev</span></p>`;
const DATA={
 summer:{tag:'☀ Summer · Chapter 1',title:'About Me',html:`<p class="text-xl">Project manager who treats a delivery plan like a level design: clear objectives, readable paths, and a few secrets worth finding. I'm bringing my PM craft into game studios.</p><ul class="list-disc pl-6 mt-4"><li>Background in delivery and team coordination at TELUS Digital</li><li>Hands-on with web and game-design tooling</li><li>Building <b>The Playable Project</b> — this portfolio as a retro/cyberpunk PM RPG</li></ul>${CONTACT}`},
 autumn:{tag:'🍂 Autumn · Chapter 2',title:'My Experience',html:`<h4 class="marker text-2xl">TELUS Digital</h4><p class="text-lg opacity-70">Project Manager — [add dates]</p><ul class="list-disc pl-6 mt-2"><li>[Project 1 — scope, team size, outcome]</li><li>[Project 2 — what you shipped and the result]</li><li>[Project 3 — stakeholder or process win]</li></ul><h4 class="marker text-2xl mt-6">Portfolio &amp; Game Projects</h4><ul class="list-disc pl-6 mt-2"><li>[Unity / Unreal prototype or level design piece]</li><li>[Narrative design sample]</li></ul>${CONTACT}`},
 winter:{tag:'❄ Winter · Chapter 3',title:'Skills',html:`<h4 class="marker text-2xl">Web</h4><p>${['HTML/CSS','Framer','Webflow'].map(x=>`<span class="chip">${x}</span>`).join('')}</p><h4 class="marker text-2xl mt-4">Management</h4><p>${['Agile','Jira'].map(x=>`<span class="chip">${x}</span>`).join('')}</p><h4 class="marker text-2xl mt-4">Game Design</h4><p>${['Unity','Unreal Engine concepts','Level design','Narrative design'].map(x=>`<span class="chip">${x}</span>`).join('')}</p>${CONTACT}`},
 spring:{tag:'🌱 Spring · Chapter 4',title:'Certification',html:`<ul class="list-disc pl-6"><li>[Certification name — issuer, year]</li><li>[Agile / Scrum credential — issuer, year]</li><li>[Game design or engine course — issuer, year]</li></ul><p class="mt-4 text-lg opacity-70">Swap these placeholders with your real credentials.</p><h4 class="marker text-2xl mt-6">Let's build something</h4><p class="text-lg">Hiring a PM for a game studio? Let's talk.</p>${CONTACT}`}
};
 
/* ---------- doodle map ---------- */
const dood=$('#doodles');let H=innerHeight,W=innerWidth,PH=0;
function rnd(a,b){return a+Math.random()*(b-a)}
function buildDoodles(){
  H=innerHeight;W=innerWidth;let s='';
  let seed=11;const R=()=>(seed=(seed*16807)%2147483647)/2147483647,P=(a,b)=>a+R()*(b-a);
  const L='fill="none" stroke="#2b2a28" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"',F='fill="#f3f0e7"';
  const circ=(x,y,r)=>`<circle cx="${x}" cy="${y}" r="${r}" ${F}/>`;
  const leaves=(x,y,r,n)=>{let d='';for(let i=0;i<n;i++){const a=R()*6.28,q=Math.sqrt(R())*r;d+=`M${(x+Math.cos(a)*q).toFixed(1)} ${(y+Math.sin(a)*q).toFixed(1)}q3 -4 6 0`}return `<path d="${d}"/>`};
  const tree=(x,y,k)=>{let g=`<g ${L}><path d="M${x-5*k} ${y}Q${x-3*k} ${y-14*k} ${x-3*k} ${y-30*k}H${x+3*k}Q${x+3*k} ${y-14*k} ${x+5*k} ${y}Z" ${F}/><path d="M${x-k} ${y-4*k}v${-9*k}M${x+1.5*k} ${y-14*k}v${-8*k}M${x-22*k} ${y+3*k}h${44*k}M${x-16*k} ${y+7*k}h${30*k}"/>`;
    [[-15,6,13],[15,6,13],[0,10,14],[-10,-8,14],[11,-8,13],[0,-16,14]].forEach(p=>{const cx=x+p[0]*k,cy=y-44*k+p[1]*k,r=p[2]*k;g+=circ(cx,cy,r)+leaves(cx,cy,r*.7,5)});return g+'</g>'};
  const pine=(x,y,k)=>{let g=`<g ${L}><path d="M${x} ${y}v${-8*k}"/>`;[[24,-10],[19,-24],[13,-38]].forEach(([w,o])=>{const t=y+o*k;g+=`<path d="M${x} ${t-20*k}L${x+w*k} ${t}Q${x+w*.5*k} ${t+5*k} ${x} ${t}Q${x-w*.5*k} ${t+5*k} ${x-w*k} ${t}Z" ${F}/><path d="M${x} ${t-12*k}l${-5*k} ${8*k}M${x} ${t-12*k}l${5*k} ${8*k}"/>`});return g+'</g>'};
  const bush=(x,y,k)=>{let g=`<g ${L}>`;[[-10,0,9],[0,-4,11],[10,0,9]].forEach(p=>{const cx=x+p[0]*k,cy=y+p[1]*k,r=p[2]*k;g+=circ(cx,cy,r)+leaves(cx,cy,r*.6,3)});return g+`<path d="M${x-18*k} ${y+10*k}h${36*k}"/></g>`};
  const tuft=(x,y,k)=>`<path ${L} d="M${x} ${y}q${-2*k} ${-8*k} ${-6*k} ${-11*k}M${x} ${y}q0 ${-11*k} ${k} ${-14*k}M${x} ${y}q${3*k} ${-8*k} ${8*k} ${-9*k}M${x+3*k} ${y}q${5*k} ${-4*k} ${9*k} ${-4*k}"/>`;
  const fern=(x,y,k)=>{let d=`M${x} ${y}V${y-34*k}`;for(let i=1;i<=5;i++){const yy=y-i*6*k;d+=`M${x} ${yy}l${-(11-i)*k} ${-4*k}M${x} ${yy}l${(11-i)*k} ${-4*k}`}return `<path ${L} d="${d}"/>`};
  const flower=(x,y,k)=>`<g ${L}><path d="M${x} ${y}q${2*k} ${-8*k} 0 ${-14*k}M${x} ${y-8*k}l${5*k} ${-3*k}"/>${[[0,-3.5],[0,3.5],[-3.5,0],[3.5,0]].map(p=>`<circle cx="${x+p[0]*k}" cy="${y-17*k+p[1]*k}" r="${2.2*k}" ${F}/>`).join('')}<circle cx="${x}" cy="${y-17*k}" r="${1.4*k}"/></g>`;
  const rock=(x,y,k)=>`<g ${L}><path d="M${x-12*k} ${y}Q${x-10*k} ${y-12*k} ${x} ${y-13*k}Q${x+11*k} ${y-12*k} ${x+13*k} ${y}Z" ${F}/><path d="M${x-4*k} ${y-8*k}l${4*k} ${4*k}M${x+4*k} ${y-6*k}l${3*k} ${3*k}"/></g>`;
  const mount=(x,y,k)=>`<g ${L}><path d="M${x-30*k} ${y}L${x} ${y-34*k}L${x+30*k} ${y}Z" ${F}/><path d="M${x-8*k} ${y-24*k}l${4*k} ${5*k}l${4*k} ${-4*k}l${4*k} ${5*k}M${x+4*k} ${y-14*k}l${6*k} ${8*k}M${x+12*k} ${y-8*k}l${4*k} ${6*k}"/></g>`;
  const pond=(x,y,k)=>`<g ${L}><ellipse cx="${x}" cy="${y}" rx="${28*k}" ry="${10*k}" ${F}/><path d="M${x-10*k} ${y}q${6*k} ${3*k} ${12*k} 0M${x+4*k} ${y-3*k}q${5*k} ${2*k} ${9*k} 0M${x+30*k} ${y+4*k}v${-14*k}M${x+33*k} ${y+4*k}v${-10*k}"/></g>`;
  for(let i=0,n=Math.round(W*H/15000);i<n;i++){
    const x=Math.round(R()*W),y=Math.round(R()*H),k=Math.round(P(.8,1.4)*10)/10;
    if(Math.abs(x-W/2)<100)continue;const r=R();
    s+=r<.24?tree(x,y,k):r<.36?pine(x,y,k):r<.5?bush(x,y,k):r<.64?tuft(x,y,k):r<.72?fern(x,y,k):r<.82?flower(x,y,k):r<.88?rock(x,y,k):r<.94?mount(x,y,k):pond(x,y,k);
  }
  dood.innerHTML=`<svg id="dsvg" width="${W}" height="${H*3}" style="will-change:transform"><defs><g id="tile">${s}</g></defs><use href="#tile"/><use href="#tile" y="${H}"/><use href="#tile" y="${2*H}"/></svg>`;
}
buildDoodles();
 
 
/* ---------- path ---------- */
const path=$('#path');
const px=(y)=>W/2+Math.sin(y/230)*Math.min(70,W*.12);
function buildPath(){
  PH=document.documentElement.scrollHeight;path.setAttribute('height',PH);path.setAttribute('viewBox',`0 0 ${W} ${PH}`);
  let d='';for(let y=0;y<=PH;y+=20)d+=(y?'L':'M')+px(y).toFixed(1)+' '+y;
  $('path',path).setAttribute('d',d);
}
 
/* ---------- state ---------- */
/* walk-cycle rig: mirrored legs & arms, driven by scroll distance */
const SVGNS='http://www.w3.org/2000/svg';
function mirror(el){const w=document.createElementNS(SVGNS,'g'),c=el.cloneNode(true);c.setAttribute('class',el.getAttribute('class').replace('L','R'));w.setAttribute('transform','scale(-1 1)');w.appendChild(c);el.after(w);return c}
const legA=$('.legL'),armA=$('.armL'),legB=mirror(legA),armB=mirror(armA);
const fLow=$('#fHairLow'),fLockA=$('.flockL'),fLockB=mirror(fLockA),fEyes=$('#fEyes');
const hairLow=$('#hairLow'),hairBase=$('#hairBase'),bodyG=$('#bodyG'),shd=$('#shd');
let phase=0,amp=0,lastY=scrollY,lastT=performance.now();
function rig(now){
  const dt=Math.min(.05,(now-lastT)/1000);lastT=now;
  const sd=scrollY-lastY,dy=Math.abs(sd);lastY=scrollY;if(sd>1.5)char.dataset.v='front';else if(sd<-1.5)char.dataset.v='back';
  phase+=dy*.06;amp+=(Math.min(1,dy/10)-amp)*Math.min(1,dt*6);
  const s=Math.sin(phase),t=now/1000;
  const leg=(el,v)=>{const l=Math.max(0,v)*amp,st=Math.max(0,-v)*amp;el.setAttribute('transform',`translate(0 ${(74-l*7).toFixed(2)}) scale(1 ${(1-.13*l+.04*st).toFixed(3)}) translate(0 -74)`)};
  leg(legA,s);leg(legB,-s);
  armA.setAttribute('transform',`rotate(${(-15*s*amp).toFixed(2)} -15 31)`);
  armB.setAttribute('transform',`rotate(${(15*s*amp).toFixed(2)} -15 31)`);
  const sw=Math.sin(phase-.7)*7*amp+Math.sin(t*1.3)*2;
  hairLow.setAttribute('transform',`rotate(${sw.toFixed(2)} 0 38) translate(0 38) skewX(${(-sw*.5).toFixed(2)}) translate(0 -38)`);
  fLow.setAttribute('transform',hairLow.getAttribute('transform'));
  fLockA.setAttribute('transform',`rotate(${(sw*.45).toFixed(2)} -13 30)`);fLockB.setAttribute('transform',`rotate(${(-sw*.45).toFixed(2)} -13 30)`);
  fEyes.setAttribute('transform',`translate(0 21) scale(1 ${(t%4.2)<.13?.1:1}) translate(0 -21)`);
  hairBase.setAttribute('transform',`rotate(${(sw*.2).toFixed(2)} 0 6)`);
  bodyG.setAttribute('transform',`translate(0 ${(-Math.abs(s)*1.3*amp).toFixed(2)})`);
  shd.setAttribute('rx',(13-Math.abs(s)*1.5*amp).toFixed(2));
  requestAnimationFrame(rig);
}
requestAnimationFrame(rig);
const char=$('#hero-char'),layers=$$('#colors i'),dots=$$('#prog b'),stages=$$('section[data-season]');
let active='hero',walkT;
function setSeason(k){
  if(k===active)return;active=k;
  layers.forEach(l=>l.classList.toggle('on',l.dataset.k===k));
  char.dataset.s=k;$$('.outfit').forEach(o=>o.classList.toggle('on',o.dataset.o.split(' ').includes(k)));
  dots.forEach((d,i)=>d.classList.toggle('on',SEASONS[i]===k));
  particleKind={summer:'gleaf',autumn:'leaf',winter:'snow',spring:'petal'}[k]||null;
  if(k==='summer')burst(40);
}
$$('.outfit').forEach(o=>o.classList.toggle('on',o.dataset.o.split(' ').includes('hero')));
function update(){
  const y=scrollY,vh=innerHeight;
  const charY=vh*.62,cx=px(y+charY),rot=Math.cos((y+charY)/230)*10;
  char.style.transform=`translate(${cx-56}px,${charY-85}px) rotate(${rot}deg)`;
  document.documentElement.style.setProperty('--cx',cx+'px');
  document.documentElement.style.setProperty('--cy',charY+'px');
  const t=Math.min(1,y/(vh*.6)),e=t*t*(3-2*t);
  document.documentElement.style.setProperty('--r',(90+e*Math.hypot(W,vh)).toFixed(0)+'px');
  $('#dsvg').style.transform=`translateY(${-((y*.6)%H)}px)`;
  let cur='hero';
  stages.forEach(s=>{const r=s.getBoundingClientRect();if(r.top<vh*.5&&r.bottom>vh*.5)cur=s.dataset.season;
    s.classList.toggle('in',s.classList.contains('stage')&&r.top<vh*.55&&r.bottom>vh*.2)});
  setSeason(cur);
  char.classList.add('walk');clearTimeout(walkT);walkT=setTimeout(()=>char.classList.remove('walk'),160);
}
addEventListener('scroll',()=>requestAnimationFrame(update),{passive:true});
addEventListener('resize',()=>{buildDoodles();buildPath();resizeFx();update()});
 
/* ---------- particles ---------- */
const cv=$('#fx'),cx2=cv.getContext('2d');let parts=[],particleKind=null;
function resizeFx(){cv.width=innerWidth;cv.height=innerHeight}resizeFx();
const COL={gleaf:['#3fae4a','#67c95a','#2f9a45','#9be26a'],leaf:['#d9682a','#f3b13e','#a8322a','#8a5a2b'],petal:['#ffb3d1','#fff','#ffd1e3']};
function spawn(){return{x:rnd(0,innerWidth),y:-20,s:rnd(3,8)*(/leaf$/.test(particleKind||'')?1.6:1),vy:rnd(.6,1.8),vx:rnd(-.4,.4),a:rnd(0,6.28),va:rnd(-.05,.05),ph:rnd(0,6),c:null,kind:particleKind}}
function burst(n){for(let i=0;i<n;i++)parts.push(Object.assign(spawn(),{y:rnd(-500,-10),c:COL.gleaf[i%4]}))}
function tick(){
  cx2.clearRect(0,0,cv.width,cv.height);
  if(particleKind&&parts.length<(particleKind==='snow'?110:55)&&Math.random()<.5)parts.push(Object.assign(spawn(),{c:(COL[particleKind]||['#fff'])[Math.floor(Math.random()*4)%(COL[particleKind]||[1]).length]}));
  parts=parts.filter(p=>p.y<innerHeight+20);
  for(const p of parts){
    p.ph+=.03;p.x+=p.vx+Math.sin(p.ph)*.7;p.y+=p.kind==='snow'?p.vy*.7:p.vy;p.a+=p.va;
    if(p.kind!==particleKind&&!particleKind)p.y+=1.5;
    cx2.save();cx2.translate(p.x,p.y);cx2.rotate(p.a);if(/leaf$/.test(p.kind))cx2.scale(1,.45+.55*Math.abs(Math.cos(p.ph*1.5)));cx2.fillStyle=p.kind==='snow'?'#fff':p.c;cx2.strokeStyle='#2b2a28';cx2.globalAlpha=.9;
    cx2.beginPath();
    if(p.kind==='snow'){cx2.arc(0,0,p.s*.45,0,6.28);cx2.fill()}
    else if(/leaf$/.test(p.kind)){const q=p.s;cx2.moveTo(-q,0);cx2.quadraticCurveTo(0,-q*.9,q,0);cx2.quadraticCurveTo(0,q*.9,-q,0);cx2.fill();cx2.lineWidth=1;cx2.stroke();cx2.beginPath();cx2.moveTo(-q,0);cx2.lineTo(q*.8,0);cx2.stroke()}
    else{cx2.ellipse(0,0,p.s,p.s*.55,0,0,6.28);cx2.fill();cx2.lineWidth=1;cx2.stroke()}
    cx2.restore();
  }
  requestAnimationFrame(tick);
}
if(!matchMedia('(prefers-reduced-motion:reduce)').matches)tick();
 
/* ---------- cursor ---------- */
const cur=$('#cur'),ring=$('#ring');let mx=0,my=0,rx=0,ry=0;
addEventListener('pointermove',e=>{mx=e.clientX;my=e.clientY;cur.style.transform=`translate(${mx}px,${my}px)`});
(function loop(){rx+=(mx-rx)*.18;ry+=(my-ry)*.18;ring.style.transform=`translate(${rx}px,${ry}px)`;requestAnimationFrame(loop)})();
document.addEventListener('pointerover',e=>ring.classList.toggle('big',!!e.target.closest('.hot,button,a')));
 
/* ---------- drawer ---------- */
function openDrawer(k){const d=DATA[k];
  $('#dbody').innerHTML=`<p class="text-lg opacity-70">${d.tag}</p><h3 class="marker">${d.title}</h3>${d.html}`;
  document.body.classList.add('open');$('#drawer').setAttribute('aria-hidden','false')}
function closeDrawer(){document.body.classList.remove('open');$('#drawer').setAttribute('aria-hidden','true')}
$$('[data-open]').forEach(b=>b.addEventListener('click',()=>openDrawer(b.dataset.open)));
$('.close').addEventListener('click',closeDrawer);$('#shade').addEventListener('click',closeDrawer);
addEventListener('keydown',e=>{if(e.key==='Escape')closeDrawer()});
 
buildPath();update();
</script>
</body>
</html>
 


