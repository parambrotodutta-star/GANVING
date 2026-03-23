<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ganving — Rooftop Café, Kolkata</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Syne:wght@400;500;600;700;800&family=Instrument+Serif:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
/* ═══════════════════════════════════════════════════════
   GANVING v4 — GEN Z EDITORIAL DARK LUXURY
   Fonts: Syne (GenZ bold) + Instrument Serif (editorial)
   Palette: Near-Black · Amber · Warm White · Real Wood
═══════════════════════════════════════════════════════ */
:root{
  /* Amber accents — constant across themes */
  --amb:#D4862A; --amb-lt:#EBA952;
  --amb-glow:rgba(212,134,42,.22);
  --blur:blur(28px) saturate(200%);
  --r:12px; --rl:20px; --rxl:32px;
  --blk:#080706; --blk2:#0E0D0B; --blk3:#141210;
  --ww:#F0EBE0; --ww60:rgba(240,235,224,.6);
  --ww35:rgba(240,235,224,.35); --ww12:rgba(240,235,224,.1);
  --wd1:#160C04; --wd2:#1F1008; --wd3:#2E1710; --wd4:#3E2016; --wd5:#523024;
  --gls:rgba(8,7,6,.55); --gls-b:rgba(212,134,42,.18);
  /* wood section overlays */
  /* review section overlays */
  /* glass card bg */
  /* menu section bg */
  /* contact section bg */
  /* nav glass */
  /* mob menu */
  /* text muted */
  /* footer */
  /* hero grade */
  /* river strip */
  /* hours table border */
  /* section dividers */
  /* loader bg */
}

/* light mode removed */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{background:var(--blk);color:var(--ww);transition:background .4s,color .4s;font-family:'DM Sans',sans-serif;overflow-x:hidden;}
::selection{background:var(--amb);color:#000}
::-webkit-scrollbar{width:2px}::-webkit-scrollbar-track{background:var(--blk)}
::-webkit-scrollbar-thumb{background:var(--amb)}

/* cursor removed */

/* GRAIN */
body::before{content:'';position:fixed;inset:0;z-index:9998;pointer-events:none;
  background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='200' height='200' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
  opacity:.55;mix-blend-mode:overlay}

/* ══════════════════════════════════════════
   CINEMATIC 3D INTRO SEQUENCE
══════════════════════════════════════════ */

/* Stage — full screen black canvas */
#loader{
  position:fixed;inset:0;z-index:9997;
  background:#000;
  display:flex;align-items:center;justify-content:center;
  overflow:hidden;
  transition:opacity 1s cubic-bezier(.76,0,.24,1), visibility 1s;
}
#loader.gone{opacity:0;visibility:hidden;pointer-events:none}

/* Canvas for 3D particle depth field */
#intro-canvas{
  position:absolute;inset:0;
  width:100%;height:100%;
  opacity:0;
  animation:cvFadeIn 1.2s 0.3s ease forwards;
}
@keyframes cvFadeIn{to{opacity:1}}

/* Horizontal scan lines — CRT/film effect */
#loader::before{
  content:'';position:absolute;inset:0;z-index:2;pointer-events:none;
  background:repeating-linear-gradient(
    0deg,
    transparent 0px, transparent 3px,
    rgba(0,0,0,.18) 3px, rgba(0,0,0,.18) 4px
  );
  animation:scanPan 8s linear infinite;
}
@keyframes scanPan{from{background-position:0 0}to{background-position:0 100px}}

/* Vignette */
#loader::after{
  content:'';position:absolute;inset:0;z-index:2;pointer-events:none;
  background:radial-gradient(ellipse at center,transparent 40%,rgba(0,0,0,.75) 100%);
}

/* Center stage content */
.ld-stage{
  position:relative;z-index:3;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  gap:1.4rem;
  perspective:600px;
}

/* Location tag */
.ld-loc{
  font-family:'DM Sans',sans-serif;
  font-size:.6rem;letter-spacing:.5em;text-transform:uppercase;
  color:rgba(212,134,42,.6);
  opacity:0;
  animation:ldLocIn 1s .2s cubic-bezier(.16,1,.3,1) forwards;
}
@keyframes ldLocIn{
  from{opacity:0;transform:translateY(12px) translateZ(-80px);letter-spacing:.8em}
  to{opacity:1;transform:translateY(0) translateZ(0);letter-spacing:.5em}
}

/* GANVING — massive 3D title */
.ld-title{
  position:relative;
  overflow:hidden;
  line-height:1;
}
.ld-title-inner{
  font-family:'Syne',sans-serif;
  font-size:clamp(4rem,14vw,10rem);
  font-weight:800;
  letter-spacing:-.04em;
  color:transparent;
  display:block;
  /* 3D depth reveal */
  transform:translateZ(-200px) scale(1.8);
  opacity:0;
  animation:titleZoom 1.4s .4s cubic-bezier(.16,1,.3,1) forwards;
  -webkit-text-stroke:1px rgba(240,235,224,.15);
}
@keyframes titleZoom{
  0%{transform:translateZ(-200px) scale(1.8);opacity:0;-webkit-text-stroke-color:rgba(240,235,224,.15)}
  60%{opacity:1}
  100%{transform:translateZ(0) scale(1);opacity:1;-webkit-text-stroke-color:rgba(240,235,224,0);color:var(--ww)}
}
/* Amber gradient reveal sweeps across title */
.ld-title-inner::after{
  content:'GANVING';
  position:absolute;inset:0;
  font-family:'Syne',sans-serif;
  font-size:inherit;font-weight:800;letter-spacing:inherit;
  background:linear-gradient(90deg,
    transparent 0%,
    rgba(212,134,42,.9) 30%,
    rgba(235,169,82,.95) 50%,
    rgba(212,134,42,.9) 70%,
    transparent 100%
  );
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-clip:text;
  background-size:200% 100%;
  background-position:200% 0;
  animation:sweepShine 1.6s .8s ease forwards;
}
@keyframes sweepShine{
  from{background-position:200% 0}
  to{background-position:-200% 0}
}

/* Tagline */
.ld-tagline{
  font-family:'Instrument Serif',serif;
  font-size:clamp(.9rem,2vw,1.35rem);
  font-style:italic;
  color:rgba(212,134,42,.8);
  letter-spacing:.05em;
  opacity:0;
  transform:translateY(20px);
  animation:ldFadeUp .9s 1.2s cubic-bezier(.16,1,.3,1) forwards;
}
@keyframes ldFadeUp{to{opacity:1;transform:translateY(0)}}

/* Progress line */
.ld-progress{
  width:200px;height:1px;
  background:rgba(240,235,224,.08);
  overflow:hidden;border-radius:1px;
  opacity:0;
  animation:ldFadeUp .6s 1.4s ease forwards;
}
.ld-prog-fill{
  height:100%;
  background:linear-gradient(to right,var(--amb),var(--amb-lt),var(--amb));
  background-size:200% 100%;
  width:0;
  animation:progFill 2s 1.5s cubic-bezier(.4,0,.2,1) forwards, progShimmer 1.5s 1.5s ease infinite;
}
@keyframes progFill{to{width:100%}}
@keyframes progShimmer{
  0%{background-position:0% 0}50%{background-position:100% 0}100%{background-position:0% 0}
}

/* Entering label */
.ld-enter{
  font-size:.58rem;letter-spacing:.4em;text-transform:uppercase;
  color:rgba(240,235,224,.25);
  opacity:0;
  animation:ldFadeUp .6s 1.8s ease forwards;
}

/* ── HERO 3D ENTRANCE ── */
#app{
  opacity:0;
  transform:scale(1.04) translateZ(0);
  transform-origin:center center;
  transition:opacity 1.2s cubic-bezier(.16,1,.3,1), transform 1.8s cubic-bezier(.16,1,.3,1);
}
#app.in{opacity:1;transform:scale(1) translateZ(0)}

/* Hero 3D perspective container */
#hero{
  position:relative;height:100vh;min-height:700px;
  overflow:hidden;display:flex;align-items:flex-end;
  /* 3D perspective for children */
  perspective:1200px;
  perspective-origin:50% 40%;
}

/* Background layers get depth */
.hbg-css,.hbg-grade,.hbg-bloom{transform-style:preserve-3d}

/* Cinematic letterbox bars — animate out on load */
.hero-lb-top,.hero-lb-bot{
  position:absolute;left:0;right:0;z-index:6;
  background:#000;
  height:12vh;
  transition:height 1.4s cubic-bezier(.76,0,.24,1);
}
.hero-lb-top{top:0}
.hero-lb-bot{bottom:0}
#app.in .hero-lb-top,#app.in .hero-lb-bot{height:0}

/* Hero content 3D entrance */
.h-wrap{
  position:relative;z-index:5;
  width:100%;padding:0 6vw 8vh;
  transform:translateZ(0) translateY(20px);
  opacity:0;
  transition:
    transform 1.6s 0.4s cubic-bezier(.16,1,.3,1),
    opacity 1.2s 0.4s cubic-bezier(.16,1,.3,1);
}
#app.in .h-wrap{transform:translateZ(0) translateY(0);opacity:1}

/* Hero eyebrow — individual word reveal */
.h-eye{
  display:flex;align-items:center;gap:.9rem;margin-bottom:2rem;
  overflow:hidden;
}

#app.in .h-pill{opacity:1;transform:translateY(0);transition-delay:.6s}
#app.in .h-yr{opacity:1;transform:translateY(0);transition-delay:.72s}

/* Hero title — each line reveals with 3D flip */
.h-title{line-height:1;margin-bottom:.8rem}
.ht-sm,.ht-big,.ht-it{
  display:block;
  opacity:0;
  transform:rotateX(90deg) translateY(30px);
  transform-origin:bottom center;
  transition:opacity .9s cubic-bezier(.16,1,.3,1), transform .9s cubic-bezier(.16,1,.3,1);
}
#app.in .ht-sm{opacity:1;transform:rotateX(0) translateY(0);transition-delay:.75s}
#app.in .ht-big{opacity:1;transform:rotateX(0) translateY(0);transition-delay:.9s}
#app.in .ht-it{opacity:1;transform:rotateX(0) translateY(0);transition-delay:1.05s}

/* Meta strip — slide up staggered */
.h-meta{
  display:flex;align-items:center;gap:2rem;flex-wrap:wrap;
  margin:2rem 0 2.5rem;padding-top:1.4rem;
  border-top:1px solid rgba(240,235,224,.08);
  opacity:0;transform:translateY(24px);
  transition:opacity .9s 1.2s cubic-bezier(.16,1,.3,1), transform .9s 1.2s cubic-bezier(.16,1,.3,1);
}
#app.in .h-meta{opacity:1;transform:translateY(0)}

/* Buttons — fade up */
.h-btns{
  display:flex;gap:1rem;align-items:center;flex-wrap:wrap;
  opacity:0;transform:translateY(20px);
  transition:opacity .8s 1.4s cubic-bezier(.16,1,.3,1), transform .8s 1.4s cubic-bezier(.16,1,.3,1);
}
#app.in .h-btns{opacity:1;transform:translateY(0)}

/* Scroll hint */
.h-scr{
  position:absolute;right:5vw;bottom:3rem;z-index:5;
  display:flex;flex-direction:column;align-items:center;gap:.6rem;
  opacity:0;transform:translateY(10px);
  transition:opacity .8s 1.8s ease, transform .8s 1.8s ease;
}
#app.in .h-scr{opacity:.7;transform:translateY(0)}

/* Ambient floating particles over hero */
#hero-particles{
  position:absolute;inset:0;z-index:4;pointer-events:none;overflow:hidden;
}
.hp{
  position:absolute;
  width:2px;height:2px;border-radius:50%;
  background:rgba(212,134,42,.6);
  animation:hpFloat var(--d,8s) var(--dl,0s) ease-in-out infinite alternate;
}
@keyframes hpFloat{
  0%{transform:translate(0,0) scale(1);opacity:.3}
  100%{transform:translate(var(--tx,10px),var(--ty,-30px)) scale(1.5);opacity:.8}
}

/* NAV */
nav{position:fixed;top:18px;left:50%;transform:translateX(-50%);z-index:500;
  width:calc(100% - 2.5rem);max-width:1180px;
  display:flex;align-items:center;justify-content:space-between;
  padding:.82rem 1.8rem;background:rgba(8,7,6,.42);
  backdrop-filter:var(--blur);-webkit-backdrop-filter:var(--blur);
  border:1px solid rgba(212,134,42,.18);border-radius:100px;
  transition:all .5s cubic-bezier(.77,0,.175,1)}
nav.dk{top:0;left:0;transform:none;width:100%;max-width:none;
  border-radius:0;border-left:0;border-right:0;border-top:0;
  background:rgba(8,7,6,.92);padding:.7rem 3rem;}
.n-logo{font-family:'Syne',sans-serif;font-size:1.4rem;font-weight:800;
  color:var(--ww);text-decoration:none;letter-spacing:-.03em}
.n-logo em{color:var(--amb);font-style:normal}
.n-links{display:flex;gap:2.2rem;list-style:none}
.n-links a{font-size:.7rem;letter-spacing:.15em;text-transform:uppercase;
  color:rgba(240,235,224,.6);text-decoration:none;font-weight:400;transition:color .3s}
.n-links a:hover{color:var(--ww)}
.n-cta{font-size:.68rem;letter-spacing:.1em;text-transform:uppercase;font-weight:600;
  background:var(--amb);color:#000;padding:.5rem 1.4rem;border-radius:100px;
  text-decoration:none;box-shadow:0 0 20px var(--amb-glow);transition:all .3s}
.n-cta:hover{background:var(--amb-lt);transform:translateY(-1px);box-shadow:0 4px 28px rgba(212,134,42,.4)}
.n-ham{display:none;background:none;border:none;padding:4px;cursor:pointer;flex-direction:column;gap:5px}
.n-ham span{width:22px;height:1.5px;background:var(--ww);display:block;transition:.3s}
.mob{display:none;position:fixed;inset:0;z-index:490;background:rgba(8,7,6,.98);
  backdrop-filter:blur(30px);flex-direction:column;align-items:center;justify-content:center;gap:2.8rem}
.mob.on{display:flex}
.mob a{font-family:'Syne',sans-serif;font-size:2.8rem;font-weight:700;
  color:var(--ww);text-decoration:none;letter-spacing:-.04em;transition:color .25s}
.mob a:hover{color:var(--amb)}
.mob-x{position:absolute;top:2rem;right:2rem;background:none;border:none;color:var(--ww60);font-size:1.8rem;cursor:pointer}

/* ═══════ HERO ═══════ */
#hero{position:relative;height:100vh;min-height:700px;overflow:hidden;display:flex;align-items:flex-end}

/* LAYER 1: CSS gradient — ALWAYS visible, no loading needed */
.hbg-css{
  position:absolute;inset:0;z-index:0;
  background-image:url('');
  background-size:cover;
  background-position:center 45%;
  background-repeat:no-repeat;
  background-color:#1A0C02;
  transform:scale(1.06);will-change:transform;
}
/* LAYER 2: Real photo — fades in on top once loaded */
/* hbg-photo layer removed — using embedded bridge image in hbg-css */
/* LAYER 3: Cinematic grade */
.hbg-grade{
  position:absolute;inset:0;z-index:2;
  background:
    linear-gradient(108deg,rgba(8,7,6,.92) 0%,rgba(8,7,6,.72) 30%,rgba(8,7,6,.1) 56%,transparent 72%),
    linear-gradient(to top,rgba(8,7,6,1) 0%,rgba(8,7,6,.65) 26%,rgba(8,7,6,.1) 55%,transparent 72%)}
.hbg-bloom{position:absolute;bottom:0;left:0;z-index:3;width:60%;height:65%;
  background:radial-gradient(ellipse at 0% 100%,rgba(212,134,42,.18) 0%,transparent 65%);pointer-events:none}



/* HERO CONTENT */
.h-wrap{position:relative;z-index:5;width:100%;padding:0 6vw 8vh}

/* EYEBROW */
.h-eye{display:flex;align-items:center;gap:.9rem;margin-bottom:1.8rem;
  opacity:0;animation:slideL .8s cubic-bezier(.76,0,.24,1) .3s both}
.h-pill{display:inline-flex;align-items:center;gap:.5rem;
  background:rgba(212,134,42,.12);border:1px solid rgba(212,134,42,.28);
  border-radius:100px;padding:.3rem .9rem;
  font-size:.62rem;letter-spacing:.22em;text-transform:uppercase;color:var(--amb-lt);font-weight:500}
.hp-dot{width:5px;height:5px;border-radius:50%;background:var(--amb);
  box-shadow:0 0 8px var(--amb);animation:blink 2s infinite}
.h-yr{font-size:.65rem;letter-spacing:.22em;text-transform:uppercase;color:var(--ww35)}

/* GEN Z TITLE */
.h-title{line-height:1;margin-bottom:.8rem;}
.ht-sm{display:block;font-family:'Syne',sans-serif;font-size:clamp(.72rem,1.2vw,.95rem);
  font-weight:400;letter-spacing:.1em;text-transform:uppercase;color:var(--ww35);margin-bottom:.15rem;
  transform-style:preserve-3d;}
.ht-big{display:block;font-family:'Syne',sans-serif;
  font-size:clamp(3.8rem,8vw,8rem);font-weight:800;
  line-height:.82;letter-spacing:-.05em;
  background:linear-gradient(130deg,#fff 0%,var(--ww) 25%,var(--amb-lt) 62%,var(--amb) 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  filter:drop-shadow(0 0 44px rgba(212,134,42,.28))}
.ht-it{display:block;font-family:'Instrument Serif',serif;
  font-size:clamp(1.4rem,2.8vw,3rem);font-style:italic;font-weight:400;
  color:var(--amb-lt);letter-spacing:-.02em;margin-top:-.1rem;opacity:.88}

/* META STRIP */
.h-meta{display:flex;align-items:center;gap:2rem;flex-wrap:wrap;
  margin:2rem 0 2.5rem;padding-top:1.4rem;border-top:1px solid rgba(240,235,224,.08);}
.hm{display:flex;flex-direction:column;gap:.18rem}
.hm-l{font-size:.55rem;letter-spacing:.28em;text-transform:uppercase;color:var(--amb);font-weight:600}
.hm-v{font-size:.85rem;color:var(--ww60);font-weight:300}
.hm-sep{width:1px;height:28px;background:rgba(240,235,224,.1);flex-shrink:0}

/* BTNS */
.h-btns{display:flex;gap:1rem;align-items:center;flex-wrap:wrap;}
.btn-a{position:relative;overflow:hidden;
  font-size:.72rem;letter-spacing:.12em;text-transform:uppercase;font-weight:600;
  background:var(--amb);color:#000;padding:.9rem 2.4rem;border-radius:100px;
  text-decoration:none;transition:all .4s cubic-bezier(.76,0,.24,1);box-shadow:0 4px 24px var(--amb-glow)}
.btn-a::before{content:'';position:absolute;inset:0;background:var(--amb-lt);
  transform:translateY(101%);transition:transform .4s cubic-bezier(.76,0,.24,1)}
.btn-a:hover::before{transform:translateY(0)}
.btn-a:hover{transform:translateY(-3px);box-shadow:0 12px 36px rgba(212,134,42,.45)}
.btn-a span{position:relative;z-index:1}
.btn-g{font-size:.72rem;letter-spacing:.12em;text-transform:uppercase;font-weight:400;
  color:var(--ww);background:rgba(240,235,224,.07);padding:.9rem 2.4rem;border-radius:100px;
  text-decoration:none;border:1px solid rgba(240,235,224,.18);backdrop-filter:blur(10px);transition:all .3s}
.btn-g:hover{background:rgba(240,235,224,.13);border-color:rgba(240,235,224,.35);transform:translateY(-2px)}

/* SCROLL HINT */
.h-scr{position:absolute;right:5vw;bottom:3rem;z-index:5;
  display:flex;flex-direction:column;align-items:center;gap:.6rem;}
.hs-l{font-size:.55rem;letter-spacing:.3em;text-transform:uppercase;color:var(--ww35);writing-mode:vertical-rl}
.hs-line{width:1px;height:54px;background:linear-gradient(to bottom,var(--amb),transparent);animation:scl 2.5s infinite}

/* ═══════ SECTION BASE ═══════ */
section{padding:7rem 5vw}
.ct{max-width:1200px;margin:0 auto}
.s-lbl{display:inline-flex;align-items:center;gap:.65rem;font-size:.62rem;
  letter-spacing:.32em;text-transform:uppercase;color:var(--amb);font-weight:500;margin-bottom:1.1rem}
.s-lbl::before{content:'';width:22px;height:1px;background:var(--amb);box-shadow:0 0 8px var(--amb-glow)}
.s-h{font-family:'Syne',sans-serif;font-size:clamp(2rem,4.5vw,3.5rem);
  font-weight:700;line-height:1.05;letter-spacing:-.03em;color:var(--ww)}
.s-h em{font-family:'Instrument Serif',serif;font-style:italic;font-weight:400;
  color:var(--amb-lt);letter-spacing:-.01em}
.s-div{width:44px;height:1px;margin:1.6rem 0;
  background:linear-gradient(to right,var(--amb),var(--amb-lt),transparent);
  box-shadow:0 0 8px var(--amb-glow)}

/* SCROLL REVEAL */
[data-r]{opacity:0;transform:translateY(52px) scale(.96);
  transition:opacity 1.1s cubic-bezier(.16,1,.3,1),transform 1.1s cubic-bezier(.16,1,.3,1)}
[data-r].on{opacity:1;transform:none}
[data-r="fl"]{transform:translateX(-52px) scale(.96)}[data-r="fl"].on{transform:none}
[data-r="fr"]{transform:translateX(52px) scale(.96)}[data-r="fr"].on{transform:none}
[data-r="sc"]{transform:scale(.88);opacity:0}[data-r="sc"].on{transform:scale(1);opacity:1}
[data-d="1"]{transition-delay:.08s}[data-d="2"]{transition-delay:.17s}
[data-d="3"]{transition-delay:.26s}[data-d="4"]{transition-delay:.35s}
[data-d="5"]{transition-delay:.44s}[data-d="6"]{transition-delay:.53s}

/* MARQUEE */
.mq-wrap{background:var(--amb);overflow:hidden;padding:.68rem 0;
  border-top:1px solid rgba(0,0,0,.08);border-bottom:1px solid rgba(0,0,0,.08)}
.mq-track{display:flex;animation:mq 22s linear infinite;width:max-content}
.mq-track:hover{animation-play-state:paused}
.mq-item{font-family:'Syne',sans-serif;font-size:.72rem;font-weight:700;
  letter-spacing:.14em;text-transform:uppercase;color:#000;
  padding:0 2.5rem;white-space:nowrap;display:flex;align-items:center;gap:1.5rem}
.mq-item::before{content:'★';font-size:.6rem;opacity:.7}
@keyframes mq{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ═══════ VIBE — REAL WOOD TEXTURE ═══════ */
#vibe{
  position:relative;overflow:hidden;
  background-image:
    linear-gradient(158deg,rgba(22,12,4,.62) 0%,rgba(31,16,8,.48) 35%,rgba(46,23,16,.42) 65%,rgba(62,32,22,.38) 100%),
    url('');
  background-size:cover,cover;
  background-position:center,center;
  background-blend-mode:multiply,normal;
}
#vibe::after{content:'';position:absolute;inset:0;pointer-events:none;
  background:linear-gradient(135deg,transparent 42%,rgba(255,200,130,.025) 50%,transparent 58%)}
.vg{display:grid;grid-template-columns:1fr 1fr;gap:5.5rem;align-items:center;position:relative;z-index:1}
.vp{color:rgba(240,235,224,.6);line-height:1.9;font-size:.96rem;font-weight:300;margin-bottom:1.2rem}
.vcards{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-top:2.5rem}
.vc{padding:1.5rem;border-radius:var(--r);
  background:rgba(240,235,224,.05);backdrop-filter:var(--blur);-webkit-backdrop-filter:var(--blur);
  border:1px solid rgba(212,134,42,.1);
  transition:transform .5s cubic-bezier(.16,1,.3,1),box-shadow .5s,border-color .3s;
  cursor:default;position:relative;overflow:hidden}
.vc::before{content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,transparent 30%,rgba(212,134,42,.08) 50%,transparent 70%);
  transform:translateX(-100%);transition:transform .6s ease}
.vc:hover::before{transform:translateX(100%)}
.vc:hover{transform:translateY(-7px) scale(1.01);border-color:rgba(212,134,42,.3);box-shadow:0 22px 48px rgba(0,0,0,.45)}
.vc-i{font-size:1.6rem;margin-bottom:.65rem}
.vc-t{font-family:'Syne',sans-serif;font-size:.93rem;font-weight:600;
  color:var(--amb-lt);margin-bottom:.35rem;letter-spacing:-.01em}
.vc-d{font-size:.8rem;color:var(--ww60);line-height:1.62;margin:0}
.vi{position:relative;border-radius:var(--rxl);overflow:hidden}
.vi img{width:100%;aspect-ratio:3/4;object-fit:cover;display:block;
  filter:brightness(.88) saturate(.85);transition:transform .9s cubic-bezier(.16,1,.3,1),filter .5s}
.vi:hover img{transform:scale(1.05);filter:brightness(.95) saturate(1)}
.vi-b{position:absolute;bottom:1.3rem;left:1.3rem;right:1.3rem;padding:.95rem 1.35rem;
  background:rgba(8,7,6,.92);backdrop-filter:var(--blur);-webkit-backdrop-filter:var(--blur);
  border:1px solid rgba(212,134,42,.2);border-radius:var(--r)}
.vi-bt{font-family:'Syne',sans-serif;font-size:.9rem;font-weight:600;color:var(--amb-lt);letter-spacing:-.01em}
.vi-bs{font-size:.66rem;color:var(--ww60);letter-spacing:.1em;margin-top:.2rem}

/* RIVER STRIP */
.rstrip{position:relative;height:500px;overflow:hidden}
.rs-bg{position:absolute;inset:-80px;z-index:0;
  background:
    radial-gradient(ellipse at 50% 68%,rgba(212,134,42,.28) 0%,transparent 38%),
    linear-gradient(180deg,#0E0E12 0%,#1A1208 10%,#3A1E08 22%,#7A3C10 32%,
      #AA5C1A 42%,#C87828 50%,#7A4A1A 58%,#2A2030 68%,#141825 80%,#080C14 100%);
  will-change:transform}
.rs-real{position:absolute;inset:-80px;z-index:1;
  background-size:cover;background-position:center 42%;
  filter:saturate(1.3) brightness(.5) hue-rotate(-5deg);
  opacity:0;transition:opacity 2s ease;will-change:transform}
.rs-real.rdy{opacity:1}
.rs-ov{position:absolute;inset:0;z-index:2;
  background:linear-gradient(to bottom,rgba(8,7,6,.88) 0%,rgba(8,7,6,.08) 20%,rgba(8,7,6,.08) 76%,rgba(8,7,6,.88) 100%)}
.rs-cnt{position:relative;z-index:3;height:100%;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  text-align:center;padding:2rem;gap:1rem}
.rs-kicker{font-size:.63rem;letter-spacing:.32em;text-transform:uppercase;color:var(--amb);font-weight:500}
.rs-q{font-family:'Instrument Serif',serif;font-size:clamp(2rem,4.8vw,3.6rem);
  font-style:italic;font-weight:400;color:var(--ww);line-height:1.2;max-width:760px;
  text-shadow:0 2px 40px rgba(0,0,0,.7)}
.rs-q em{color:var(--amb-lt)}
.rs-attr{font-size:.66rem;letter-spacing:.24em;text-transform:uppercase;color:var(--amb);margin-top:.3rem}

/* ══ MENU — GLASS 3D CARDS ══ */
#menu{
  background:#0E0D0B;position:relative;
  overflow:hidden;
}
#menu::before{
  content:'';position:absolute;inset:0;
  background:
    radial-gradient(ellipse at 90% 10%,rgba(212,134,42,.08) 0%,transparent 45%),
    radial-gradient(ellipse at 10% 90%,rgba(212,134,42,.05) 0%,transparent 40%);
  pointer-events:none;z-index:0;
}

/* Category tabs — pill style with glow */
.mtabs{
  display:flex;flex-wrap:wrap;gap:.55rem;
  margin:2.2rem 0 3rem;position:relative;z-index:1;
}
.mt{
  font-family:'DM Sans',sans-serif;font-size:.67rem;letter-spacing:.1em;text-transform:uppercase;
  font-weight:500;padding:.55rem 1.35rem;border-radius:100px;cursor:pointer;
  border:1px solid rgba(240,235,224,.1);color:var(--ww60);background:rgba(240,235,224,.04);
  backdrop-filter:blur(12px);-webkit-backdrop-filter:blur(12px);
  transition:all .35s cubic-bezier(.16,1,.3,1);
  position:relative;overflow:hidden;
}
.mt::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(212,134,42,.15),transparent);
  opacity:0;transition:opacity .3s;
}
.mt:hover{border-color:rgba(212,134,42,.4);color:var(--ww);transform:translateY(-2px);box-shadow:0 8px 24px rgba(0,0,0,.3)}
.mt:hover::before{opacity:1}
.mt.on{
  background:linear-gradient(135deg,var(--amb),#9A5C1A);
  color:#000;border-color:transparent;font-weight:600;
  box-shadow:0 0 28px rgba(212,134,42,.4),0 8px 24px rgba(0,0,0,.3);
  transform:translateY(-2px);
}

/* Panel */
.mp{display:none}.mp.on{display:block;animation:panelIn .5s cubic-bezier(.16,1,.3,1)}
@keyframes panelIn{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}

/* 3-column glass card grid */
.mg{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:1.2rem;
  position:relative;z-index:1;
}

/* GLASS 3D CARD */
.mi{
  position:relative;
  background:rgba(240,235,224,.05);
  backdrop-filter:blur(24px) saturate(180%);
  -webkit-backdrop-filter:blur(24px) saturate(180%);
  border:1px solid rgba(212,134,42,.12);
  border-radius:18px;
  padding:1.5rem 1.6rem 1.4rem;
  display:flex;flex-direction:column;gap:.55rem;
  overflow:hidden;
  /* 3D perspective base */
  transform-style:preserve-3d;
  transform:perspective(800px) rotateX(0deg) rotateY(0deg);
  transition:transform .1s ease, box-shadow .3s ease, border-color .3s;
  will-change:transform;
}
/* top-left corner glow */
.mi::before{
  content:'';position:absolute;top:-30%;left:-20%;
  width:80%;height:80%;
  background:radial-gradient(circle,rgba(212,134,42,.12) 0%,transparent 65%);
  pointer-events:none;transition:opacity .4s;opacity:0;
  border-radius:50%;
}
/* bottom shimmer line */
.mi::after{
  content:'';position:absolute;bottom:0;left:0;right:0;height:1px;
  background:linear-gradient(to right,transparent,rgba(212,134,42,.4),transparent);
  opacity:0;transition:opacity .4s;
}
.mi:hover{
  border-color:rgba(212,134,42,.35);
  box-shadow:
    0 24px 48px rgba(0,0,0,.5),
    0 0 0 1px rgba(212,134,42,.15),
    inset 0 1px 0 rgba(255,255,255,.08);
}
.mi:hover::before{opacity:1}
.mi:hover::after{opacity:1}

/* Card header row */
.mi-top{display:flex;align-items:flex-start;justify-content:space-between;gap:.8rem}
.mi-left{flex:1;min-width:0}

/* Dish name */
.mn{
  font-family:'Instrument Serif',serif;
  font-size:1.05rem;font-style:italic;
  color:var(--ww);line-height:1.3;
  display:flex;align-items:center;gap:.4rem;flex-wrap:wrap;
}

/* Description */
.md{font-size:.74rem;color:var(--ww60);line-height:1.58;margin-top:.1rem}

/* Price badge */
.mpr{
  font-family:'Syne',sans-serif;font-size:.78rem;font-weight:700;
  color:#000;background:var(--amb);
  padding:.2rem .65rem;border-radius:100px;
  white-space:nowrap;flex-shrink:0;
  letter-spacing:-.01em;
  box-shadow:0 2px 8px rgba(212,134,42,.35);
  margin-top:.1rem;
  align-self:flex-start;
}

/* veg/nonveg indicator dot */
.di{
  display:inline-block;width:7px;height:7px;border-radius:50%;
  flex-shrink:0;margin-top:.35rem;
}
.di.v{background:#5DBE7A;box-shadow:0 0 6px #5DBE7A}
.di.n{background:#E05A4A;box-shadow:0 0 6px #E05A4A}

/* number badge on card */
.mi-num{
  position:absolute;top:1rem;right:1.2rem;
  font-family:'Syne',sans-serif;font-size:.6rem;font-weight:700;
  color:rgba(212,134,42,.35);letter-spacing:.05em;
}

/* GALLERY */
.gal{display:flex;gap:0;overflow:hidden;height:280px}
.gal img{flex:1;object-fit:cover;filter:brightness(.6) saturate(.7);
  transition:flex .8s cubic-bezier(.16,1,.3,1),filter .5s;cursor:pointer}
.gal img:hover{flex:3;filter:brightness(.88) saturate(1.1)}

/* REVIEWS */
#reviews{position:relative;overflow:hidden;
  background-image:
    linear-gradient(158deg,rgba(62,32,22,.72) 0%,rgba(46,23,16,.62) 45%,rgba(31,16,8,.68) 100%),
    url('');
  background-size:cover,cover;
  background-position:center,center;
  background-blend-mode:multiply,normal;
}
.rg{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:1.2rem;margin-top:2.8rem}
.rc{padding:1.85rem 2rem;border-radius:var(--rl);
  background:rgba(240,235,224,.04);backdrop-filter:var(--blur);-webkit-backdrop-filter:var(--blur);
  border:1px solid rgba(212,134,42,.1);position:relative;overflow:hidden;cursor:default;
  transition:transform .45s cubic-bezier(.16,1,.3,1),box-shadow .45s,border-color .3s}
.rc:hover{transform:translateY(-7px);border-color:rgba(212,134,42,.28);box-shadow:0 24px 56px rgba(0,0,0,.5)}
.rc::before{content:'\201C';font-family:'Instrument Serif',serif;font-size:5.8rem;
  color:var(--amb);opacity:.12;position:absolute;top:0;left:.7rem;line-height:1;pointer-events:none}
.stars{color:var(--amb);font-size:.78rem;letter-spacing:3px;margin-bottom:.9rem;text-shadow:0 0 8px var(--amb-glow)}
.rt{font-family:'Instrument Serif',serif;font-size:1rem;font-style:italic;
  color:rgba(240,235,224,.74);line-height:1.8;margin-bottom:1.4rem}
.rvr{display:flex;align-items:center;gap:.88rem}
.rav{width:38px;height:38px;border-radius:50%;
  background:linear-gradient(135deg,var(--wd4),var(--amb));
  display:flex;align-items:center;justify-content:center;
  font-family:'Syne',sans-serif;font-size:.92rem;font-weight:700;color:var(--ww);flex-shrink:0}
.rname{font-family:'Syne',sans-serif;font-size:.84rem;font-weight:600;color:var(--ww);letter-spacing:-.01em}
.rsrc{font-size:.7rem;color:var(--ww35)}

/* ══ CONTACT — DARK GOLDEN GRADIENT ══ */
#contact{
  position:relative;
  overflow:hidden;
  /* Rich dark-to-gold gradient — deep onyx at top, warm molten gold at bottom */
  background:
    linear-gradient(
      160deg,
      #080706 0%,
      #0E0A04 18%,
      #1A1004 32%,
      #2A1A06 46%,
      #3D2608 58%,
      #5C3A0C 68%,
      #7A4E12 76%,
      #9A6418 82%,
      #B87C22 88%,
      #C8902A 92%,
      #D4A03A 95%,
      #E0B84E 98%,
      #EAC85A 100%
    );
}
/* golden light bloom from bottom */
#contact::before{
  content:'';position:absolute;bottom:0;left:0;right:0;
  height:55%;z-index:0;pointer-events:none;
  background:
    radial-gradient(ellipse at 30% 100%, rgba(212,168,42,.28) 0%, transparent 55%),
    radial-gradient(ellipse at 70% 100%, rgba(235,185,60,.22) 0%, transparent 50%);
}
/* subtle noise texture over gradient */
#contact::after{
  content:'';position:absolute;inset:0;z-index:0;pointer-events:none;
  background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='200' height='200' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  opacity:.4;mix-blend-mode:overlay;
}
/* all contact children above pseudo-elements */
#contact .ct{ position:relative; z-index:1; }

/* text overrides for golden bg */
#contact .s-h{ color:#F0EBE0; }
#contact .s-h em{ color:#EAC85A; }
#contact .s-lbl{ color:#D4A03A; }
#contact .s-lbl::before{ background:#D4A03A; }
#contact .s-div{
  background:linear-gradient(to right,#EAC85A,#C8902A,transparent);
  box-shadow:0 0 10px rgba(234,200,90,.35);
}
#contact .clbl{ color:#EAC85A; }
#contact .cval{ color:rgba(240,235,220,.7); }
#contact .cval a{ color:rgba(240,235,220,.7); }
#contact .cval a:hover{ color:#EAC85A; }
#contact .hday{ color:rgba(240,235,220,.6); }
#contact .htime{ color:#F0EBE0; }
#contact .htbl td{ border-bottom:1px solid rgba(240,200,80,.12); }
#contact .cico{
  background:rgba(234,200,90,.12);
  border:1px solid rgba(234,200,90,.28);
}
#contact .mpbox{
  background:rgba(8,6,2,.45);
  backdrop-filter:blur(28px);-webkit-backdrop-filter:blur(28px);
  border:1px solid rgba(234,200,90,.22);
}
#contact .maddr{ color:rgba(240,235,220,.65); }
#contact .mplink{
  color:#EAC85A;
  border-color:rgba(234,200,90,.35);
  font-family:'Syne',sans-serif;font-weight:600;
}
#contact .mplink:hover{
  background:rgba(234,200,90,.15);
  box-shadow:0 0 20px rgba(234,200,90,.3);
}
.cg{display:grid;grid-template-columns:1fr 1fr;gap:5.5rem;align-items:start}
.crow{display:flex;align-items:flex-start;gap:1rem;margin-bottom:1.5rem}
.cico{width:40px;height:40px;border-radius:10px;flex-shrink:0;margin-top:2px;
  display:flex;align-items:center;justify-content:center;font-size:1rem;
  background:rgba(212,134,42,.1);border:1px solid rgba(212,134,42,.2)}
.clbl{font-size:.6rem;letter-spacing:.22em;text-transform:uppercase;color:var(--amb);margin-bottom:.28rem;font-weight:600}
.cval{font-size:.9rem;color:var(--ww60);line-height:1.65}
.cval a{color:var(--ww60);text-decoration:none;transition:color .3s}
.cval a:hover{color:var(--amb-lt)}
.htbl{width:100%;border-collapse:collapse;margin-top:1.5rem}
.htbl td{padding:.45rem 0;font-size:.83rem;border-bottom:1px solid rgba(240,235,224,.08)}
.hday{color:var(--ww60)}.htime{color:var(--ww);text-align:right;font-family:'Syne',sans-serif;font-weight:600;font-size:.8rem}
.mpbox{border-radius:var(--rxl);border:1px solid rgba(212,134,42,.12);min-height:310px;
  display:flex;flex-direction:column;align-items:center;justify-content:center;gap:1.2rem;padding:3rem 2rem;
  background:rgba(240,235,224,.04);backdrop-filter:var(--blur);-webkit-backdrop-filter:var(--blur)}
.mppin{font-size:2.6rem}
.mpaddr{font-family:'Instrument Serif',serif;font-style:italic;font-size:1rem;
  color:var(--ww60);text-align:center;line-height:1.75;max-width:230px}
.mplink{font-size:.68rem;letter-spacing:.16em;text-transform:uppercase;
  color:var(--amb-lt);border:1px solid rgba(212,134,42,.28);
  padding:.5rem 1.4rem;border-radius:100px;text-decoration:none;
  font-family:'Syne',sans-serif;font-weight:600;transition:all .3s}
.mplink:hover{background:rgba(212,134,42,.12);box-shadow:0 0 18px var(--amb-glow)}

footer{
  background:linear-gradient(to bottom,#EAC85A 0%,#C8902A 35%,#5C3A0C 65%,#080706 100%);
  border-top:none;
  padding:2.8rem;text-align:center;
  position:relative;overflow:hidden;
}
footer::before{
  content:'';position:absolute;inset:0;z-index:0;
  background:radial-gradient(ellipse at 50% 0%,rgba(234,200,90,.18) 0%,transparent 60%);
  pointer-events:none;
}
footer .fl, footer p{ position:relative;z-index:1; }
.fl{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;
  letter-spacing:-.04em;color:#0E0A04;margin-bottom:.45rem}
.fl em{color:#3D2608;font-style:normal}
footer p{font-size:.7rem;color:rgba(8,6,2,.65);letter-spacing:.12em}

/* FLOATS */
.floats{position:fixed;right:1.4rem;bottom:2rem;z-index:600;display:flex;flex-direction:column;gap:.7rem}
.fb{width:52px;height:52px;border-radius:50%;display:flex;align-items:center;justify-content:center;
  text-decoration:none;font-size:1.22rem;transition:transform .3s cubic-bezier(.16,1,.3,1),box-shadow .3s;position:relative}
.fb:hover{transform:scale(1.12) translateY(-2px)}
.fwa{background:#25D366;color:#fff;box-shadow:0 4px 20px rgba(37,211,102,.35)}
.fwa:hover{box-shadow:0 8px 30px rgba(37,211,102,.55)}
.fcl{background:var(--amb);color:#000;box-shadow:0 4px 20px var(--amb-glow)}
.fcl:hover{box-shadow:0 8px 30px rgba(212,134,42,.5)}
.ftip{position:absolute;right:60px;background:rgba(8,7,6,.9);backdrop-filter:blur(12px);
  border:1px solid rgba(212,134,42,.18);color:var(--ww);font-size:.67rem;letter-spacing:.08em;
  white-space:nowrap;padding:.35rem .82rem;border-radius:8px;opacity:0;pointer-events:none;transition:opacity .2s}
.fb:hover .ftip{opacity:1}

/* KEYFRAMES */
@keyframes slideL{from{opacity:0;transform:translateX(-40px)}to{opacity:1;transform:translateX(0)}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
@keyframes scl{0%,100%{opacity:1}50%{opacity:.25}}

/* RESPONSIVE */
@media(max-width:980px){
  nav{padding:.75rem 1.5rem;width:calc(100% - 2rem)}nav.dk{padding:.7rem 1.5rem;width:100%}
  .n-links,.n-cta{display:none}.n-ham{display:flex}
  .h-wrap{padding:0 6vw 6vh}
  .vg,.cg{grid-template-columns:1fr;gap:3rem}
  .vi{order:-1}.vi img{aspect-ratio:16/9}
  section{padding:5rem 1.5rem}.vcards{grid-template-columns:1fr 1fr}

}
@media(max-width:560px){
  .vcards{grid-template-columns:1fr}.gal{height:165px}
  .mg{grid-template-columns:1fr!important}
  .mt{font-size:.63rem;padding:.42rem .9rem}
  .mg{grid-template-columns:1fr 1fr!important}
  .rg{grid-template-columns:1fr}.hm-sep{display:none}
}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}

/* theme toggle CSS removed */

/* Light mode section overrides */
















































/* Vibe + Reviews wood sections in light mode */
/* light vibe handled by JS */
/* light reviews handled by JS */




</style>
</head>
<body>

<!-- CINEMATIC 3D INTRO -->
<div id="loader">
  <canvas id="intro-canvas"></canvas>
  <div class="ld-stage">
    <div class="ld-loc">Kolkata &nbsp;&bull;&nbsp; Strand Road &nbsp;&bull;&nbsp; 6th Floor</div>
    <div class="ld-title">
      <span class="ld-title-inner">GANVING</span>
    </div>
    <div class="ld-tagline">where the river meets the sky</div>
    <div class="ld-progress"><div class="ld-prog-fill"></div></div>
    <div class="ld-enter">Entering &bull; Est. 2019</div>
  </div>
</div>

<!-- Embedded images — loaded once, referenced by JS -->
<img id="img-bridge" src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEBLAEsAAD/4Y8YRXhpZgAATU0AKgAAAAgACgEPAAIAAAASAAAAhgEQAAIAAAAMAAAAmAEaAAUAAAABAAAApAEbAAUAAAABAAAArAEoAAMAAAABAAIAAAExAAIAAAALAAAAtAEyAAIAAAAUAAAAwAITAAMAAAABAAIAAIdpAAQAAAABAAAA1IglAAQAAAABAACO/gAAAABOSUtPTiBDT1JQT1JBVElPTgBOSUtPTiBEMzEwMAAAAAEsAAAAAQAAASwAAAABUGhvdG9TY2FwZQAAMjAxNDoxMDowMyAxOTozMjoxMQAAKIKaAAUAAAABAAACuoKdAAUAAAABAAACwogiAAMAAAABAAQAAIgnAAMAAAABDIAAAJAAAAcAAAAEMDIyMZADAAIAAAAUAAACypAEAAIAAAAUAAAC3pEBAAcAAAAEAQIDAJECAAUAAAABAAAC8pIEAAoAAAABAAAC+pIFAAUAAAABAAADApIHAAMAAAABAAUAAJIIAAMAAAABAAoAAJIJAAMAAAABAAAAAJIKAAUAAAABAAADCpJ8AAcAAIuSAAADEpKGAAcAAAAsAACOpJKQAAIAAAADMzAAAJKRAAIAAAADMzAAAJKSAAIAAAADMzAAAKAAAAcAAAAEMDEwMKABAAMAAAABAAEAAKACAAMAAAABEgAAAKADAAMAAAABDAAAAKAFAAQAAAABAACO4KIXAAMAAAABAAIAAKMAAAcAAAABAwAAAKMBAAcAAAABAQAAAKMCAAcAAAAIAACO0KQBAAMAAAABAAAAAKQCAAMAAAABAAAAAKQDAAMAAAABAAEAAKQEAAUAAAABAACO2KQFAAMAAAABACQAAKQGAAMAAAABAAEAAKQHAAMAAAABAAIAAKQIAAMAAAABAAAAAKQJAAMAAAABAAAAAKQKAAMAAAABAAAAAKQMAAMAAAABAAAAAAAAAAAAAAAKAAAAyAAAACgAAAAKMjAxNDoxMDowMyAxOTozMjoxMQAyMDE0OjEwOjAzIDE5OjMyOjExAAAAAAQAAAABAAAAAAAAAAYAAAAoAAAACgAAAPAAAAAKTmlrb24AAhAAAE1NACoAAAAIADUAAQAHAAAABDAyMTAAAgADAAAAAgAADIAABAACAAAACAAAAooABQACAAAADQAAApIABwACAAAABwAAAqAACAACAAAADQAAAqgACQACAAAAFAAAArYACwAIAAAAAgAAAAAADAAFAAAABAAAAsoADQAHAAAABAABBgAADgAHAAAABO4BDAAAEQAEAAAAAQAALAoAEgAHAAAABAIBBgAAEwADAAAAAgAAAyAAFgADAAAABAAAAuoAFwAHAAAABAABBgAAGAAHAAAABAAAAAAAGQAKAAAAAQAAAvIAGwADAAAABwAAAvoAHAAHAAAAAwABBgAAHQACAAAACAAAAwgAHgADAAAAAQABAAAAHwAHAAAACAAAAxAAIgADAAAAAf//AAAAIwAHAAAAOgAAAxgAJAAHAAAABAFKAQIAJQAHAAAADgAAA1IAKwAHAAAAEAAAA2AALAAHAAACPgAAA3AALQADAAAAAwAABa4AgwABAAAAAQ4AAAAAhAAFAAAABAAABbQAhwABAAAAAQAAAAAAiQADAAAAAQAgAAAAigADAAAAAQABAAAAiwAHAAAABEABDAAAkQAHAAAicQAABdQAlQACAAAABQAAKEYAlwAHAAACYAAAKEwAmAAHAAAAIQAAKqwAnQADAAAAAQAAAAAAngADAAAACgAAKs4AogAEAAAAAQBd9YgAowABAAAAAQAAAAAApwAEAAAAAQAAI6AAqAAHAAAALgAAKuIAqwACAAAAEAAAKxAAsAAHAAAAEAAAKyAAsQADAAAAAQAEAAAAtgAHAAAACAAAKzAAtwAHAAAAHgAAKzgAuAAHAAAArAAAK1YAuwAHAAAACAAALAIAAAAARklORSAgIABDTE9VRFkgICAgICAAAEFGLUEgIAAATk9STUFMICAgICAgAAAgICAgICAgICAgICAgICAgICAgAAAAAkIAAAEAAAABJAAAAQAAAAEAAAABAAAAAQAAAAEAAAAAABIADABNTQAqAAAACAAAEkAMDBJADAwAAAAAODE4MzgwNAAwMTAwAQEAADAxMDBMQU5EU0NBUEUAAAAAAAAAAAAAAExBTkRTQ0FQRQAAAAAAAAAAAAAABMcAAACAhICAgID///94AQwAAABgAQwAAAAAATAxMDABBAECAAAAAAAAAAAwMTAxIwABaADwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgAAAAAAAAAAtAAAAAoAAAImAAAACgAAACMAAAAKAAAAOAAAAAowMjE5OZ+T7wAvflOvpXAgxt056NAIkJcwFG1clRTEMxQh4RiYYXPOak+XCN2vR+rzKolQROxbRlxZvcwH46/vbP0xiCgmQ76mj+TubDMXF/fm/DL4Wt1obQIvQasNm3iVjYEepzUz9JK7PC77zRhfCLwBhJRG1LuHGacAXrRmW3+V045KbfRkii+ChozvjboGtnmgEMnLFqqHrRzU1R+yjrMh2Nghs46yH9XUHK2HqhbLyRCiZZoGu/X81HvexXGe5XFIaNGDfsIcJU+sV1ebJvoZgTApa/fK503F9LO/k64bwbj4gVNu00R1tDwMJ5s2KmnxwNk75toXnW6E9Y+LtlIYIZUsIl/jrsQz27LqdlDlk/hIsCNl70Xs3AIrdeqxrBTH5RzzTuRhPwxc58ju5dkE2ZuCwzPciCW5gro3l/hcsTjokTjeXpolBAevQiwmuz+7i9irtgqnj+U15wCtEzL+h8WQky4SP7V0fMVnSne1q70Bx3mrG4nfIcWlzyb+7lHoyPFjHiJvBeQMfUjF+8WGv9HZtRfV6NJ3FXth1fGVoU4Y5eXAROVFV510BNWWS0mRJvw6mRs0eRznSO80nuNxz+2FANK8aqG+LvXXgNGExH/NVrEJtRgQhUPAwudpTHbPz/MMOS+AA4NDVlhVS94WDZyGTICh6uPDU5gPAj7DkagIsaPeYi9FpEw9d/rG2zng0AmLVmrHbVyUFd/yTvPhGJhhc85yX5UU3O1H6tYLiVBguVtGeve9zCTFr+JeIzGIKBFDvoKP5YRsnRfa5jvZwPBpMPfQphb97vRkEzTSmjniQBLLk9k0kv0r5cv0aSsyghsAP2FOprW/PE/CfoPRaEhx456i74VkjP23ugabeaAQycsWqoetHNTVH7KOsyHY2CGzjrIf1dQcrYeqFss3EF55mwa6tv2MZIXvop7jcUho0YN+wk8lRKxdV5om+xmAMClr9srnTfz0Nb+SrhPBuPiBU27Sf3W0PA0nmjIxIRLY4SPGovlwHoTlj4K+QxMni8YgJvi33uWWbvR62Fo4YFKGCCHwR+3cFI1fcs5zYZg7QetO8t0al6sI8e9cgwnfxxnc+/p3LYhbAC5i30Gw0ayTvMH9D2UE7Gw6Wma7WUBw6VTJ9dhyw8uKgK0RrP6HR75sUe3ASguDspg1iZSpsACZe6Ya19UoO1owvfxorhc375weoq8EZPOCa46GG/kgkElLlioHLZxUVZ8yDjOhWEikOm6lo9XUzy0HKpZLSZAg+RA2OktrPGEFaUco+bHlu30/YnPB+dty3dcap3mdALHpq3ZKJ008fLUfEi6TQTh4CdPuUv/lNLytpwq2q+lwQFm7Zlr3HeUMZQ0C/sORqAixol5iL0WlTT13+sbbOODQCYtWacdtXBQVH/JOc+EYmGFzzrJelBTcaOrssz2JryX3Fgs0u/uKYIDrugpyY9luVAH9wYuZ5jL2NtqcOVFIeOGjvgJ/Qzy8g3/jb7frtt6ld8r221GQmCmDrpoPKRCDGfsmml5eeUYsR9RchdFoSHHjnqLvhWSM/be6BkJ9oBDJyxeWhq0c1NUfso6zIdjYIbOOsh/V1Byth6oWy8kQoDf/Brq3/Yxkhe+inuNxSGjRg37CTyVErF1Xmib7GYAwKWv2yudN/PQ1v5KuE8G4+IFTbtJ/dbQ8DSeKNitp8MDZO+baF51shOWPgr5DESiIMSNe4q/FJMy993pGW7lgUIkL1upH7dwUlV9yznNhmBgeMrCdIBCUG23Hla2LCdDpxi45NYjgTLe60J11oKc/L2pqwgb0gv9O4ZKmSUeMvI4VBErJW35BrwitrzYui4WhvHnQX8QAj6U2uLGoEFdL85n5pj7XWCyhpeG9IfyA6N7xReHMbwwbqX0nOq4buSCLSW1pmPjuY7Sqec3RzF+n6V588OZhY6vz0kzUKrWcbvUHkHixyY3z9/vV3I2duDaOr6AAlTC9OyIjFeWghK7/hszrdkpnzXx0tT8SLpNBOHj+aRA7AQo09I2n9Uqr6XBIpk2Zjmj87Bea8f2VwGefj0otJfbVvF8cx60B5CeUHGP16arvOxKhzehPD7cOauUrn3IwH6RY7xAWoREB8Gqrl7lBuc73+8wMOtoc9yMziDcRCr6JcBp7F50D2vk78cDRaTHJHNjKw2CKui2+rEQHxz+sUJVAMAkfs3c3OpXIzl7nLttgqZhStNuOPCx9h5Zij2tgTRCMmjQDfkS2ZY1fNKzLFqqHrRzU1R+yjrMh2NjeXnB34P3UWa2bVc/LzhC0hlv5wkhljHGF71074Gd/7yoqgsa0wr8OoVJmCQfMfM7VxAoJG74Bb8jtb3buS0VhfLmQn4TAT+X2+HHo0JcLM9m55v4XGGzh5aF9YbzAKJ4xBaEMr8zbab3nem5b+WBLiS0pWLguI/RquY0RjJ9nqR68sCYhI2szkoyU6nXcLjXHUDhxic2zt7uVnE1d+PbOb2DA1fB9++LjVaVgRG6/Royrtgqnjbw09f9S7tMBeDg+RtFtYOoLyxiwtoOGTGvvWwR4z6gi+zlysL1h3KY/PwqUc30cm5l4IujG0cSO9W8UtWGV+VJvKwpgv9hmvCutvszR/Woma2Ha0dDpt5xrVo7kc+dKAtu70pCdwxwGFK2u9guVMFoZ02Ak5BGUbd1v/BTKtxhxkwpCy8XbZLynS/4sNj2AGshDEFp1SX42hR+mRJt3TtJT+3Ly1UscdPX2bEwjn2jSaZNKKKP5BM47LfJ1oRQwEmlr6iOPsw5852d+jhutIWqhCzi6/RnVVq8TBOS7pIiqd3s4Wj2g9E7/l+6cw31wGtFTdugpO8wwH4m0ZEl8Jw08tHV/0m5Tgfi4wROWFL81zRRP6MkBlHlizxn7IZpXXaxEJU/CfoPRaEhx456i79iTWf23ugabeaAQycsWqoetHNTeH7KOsyHY2CGzjqse19caqYKtA93eCLlbuCKShfWFWKzlqbTvcUho0YN+wk8lRKxdV5om+xmAMClr9srnTfz0Nb+SrhPBuPiBU27Sf3W0Hg0nihUrafDl2Tvm/xedbNblj4LsQxEo2jEjXrCvxSSfvfdCUVu5WEiJC+7zR+3kDZVfStdzYaAB4fN2698VrHltx1Jziwnoxjnb/tx3PXSCRS9a+aOxMC2RwwaHD2U8UR2XWma7WUBw6au2CqeNvDT1/1Lu0wF4OEGTLhI/tXR8zWdKduupsACZe6Ya190sxKXPQv4DUejI8WMeIm8F5Ax9NzqGG/kgkElLlioHLZxUVZ8yDjOhWFihMw4yn1VUnC0HKpZLSZAg+RuGOjd9DOQFbyIeY/HI6FED/kLPpcQs3dcapnuZALCp63ZKZ818dLU/Ei6TQTh4AdPuUv/1PimNouWuq+lxd1m7VkmXWV0UZQ8OAsORqDqxnCBzL0ZjzD13+n/bBg/cCbwgBsdtVUcV3/J88+EYoWFz3mKTOthzrGfb+Du4UL/krLGBqAhJ2hp0HSXVzj936uRhfXga+ZFm4qVpcAa/DzbUwddJg0HJCqCL2a4+LccUpNHNYEKzK7g4va+y3DCAZkTZ5cryWbv4MLWBfK4XFQwc6V8w8po/A1hH0X0QfWWUtCldepLjCwjA51FE7q0l305zQ3K6q+iSeljJFB7n167GW0dAAvOTfhRX6RSEMzfufAM1OPi7W6OIR1NWhF/Pep4LNxKwO6vAyOVDbq5HLfakkSUwisvv89z381SeLx0mxBGV6EOQexJ2b8E8ztfXxNwrt9gywTlDILXRJWqzrna8IRQyEiHJaJCN8YycbeMcDLGFoKJjIbIxv6t2dgc/xgQ/HeDCsduz0L+RxE73NYQcw7Uw2PMn4uWmWW4mNaWWdE3VenLBw4oCKRUM/rdFkq3558BqUwOQmJWJPvbVZOasWefgqvs7WqS9QVymNz8k1+F/oHAT+8hOfVlmDH3Htjx48XrU46uqasVx7Hajrd4s8Q1kop1I0vhWSdQt7V5GdlmNwoLxG/gS/P08DjYViuYjHxyyM/MiJAdZrGRdT9YXi52oMqcKTMBNkU4cz0V+LAGtEiqrRXJQdWv2xge/7MQxpUDwOfuyktbBNy5Vv058gQXauln3wKAtMSbUPy901vlVGFojY2ggAbWtFU5vnGYXjKtgy8M7ODwo/n6vH8ykrw+gQov6O84ZAU9m39XitvHdOJr6kWjqhzvMDjcffnyDffDwwVqoAo2brjwnTRxmwW1RCospErqdKZ52wz1uLflEoD5b8fC6PIo0HoWXzhzhXbp6H3NCwYfxzI5/Xh4U4few+qEJO+JNcczXCaXG5HEtYCIr4jB4Xco+AG1frkTZxcgic7t6Un/hPC+3Paz8i2dw2rtbqiDF2QxsP29Wvgm1mBODQ+Boblt+JGMXQwywBwCKQ8PaWHWp9JYnNyLMi4VkAxHwulB+4Zxm/Xds3aldUbrfs+II95AOpBOllvQJJbqe4+liiYixj7RjbpYMuw+iaksDujjVi/T+DKXGLjMtiMKRW/jcnGlMRfV3xDyC/3DZ65PqI4WbTKTfRxZUTmXYYkDLaAItEQbejWc+bNN/5nrLg9qanQM0TO3+RJRb55BK4RvakBvB3KYzNwqd6VyYelHzgstFe+Zk329WtkP1eZJpg4BgrcHtfqcrHIzz7OBC7+PQ8vVonDbHnwbEe8XIglnb7pDRwZQYF5OMTIG0Mn46mSIm53mEZN9FVJ4jubRwk4tKasHRbL5Nh3RMGb2KC0vbePK9yXI2DZ1GRJvFamod2pr5D+vu5FfzTmQ5F1E727poLiEbJESdD9Z8qpc4OmBB6qiHEaQe7WOVbjGHgGpJC4gSJClQdr53xqw1DQkBM9vyUJ3hXE3a3+a26X8AOHmzam0vG+ykfwWUcME9mtpJyUIsJVmu9Id1HO5V70jKS5uTND+JnNRPP+YMWyWAouk7erK9gV8uh7eGF+ldgD6beQtYR3nmit1uNrTjX3hQw+Mi6O1zxHalBYxEZQ1poB9o+9DP4TYWZd0GQHHFCAKTmX4QeGEchrWXhvmBNVLYq1kr6GXTFG53z/C2CdUaEqEPyoHkVcQ4b0f8LBMvqIvD69qI9ct0ng29ZGYzJ2uqmfk65E1Bte7Xc2rcrbnwsNpRQoqtmayHnZd23is9kJajyVIAExumt27FHgwgpShKY6mwuD2BfvYfXUwEuReiwiHbukmVC13C9XfnFUH1cDi7s9hIrwNVpD0vlFTD91o+yUHqOS2RvHaLR57ucc/KCgMPIoKXKf5WB9/mTlHnCCp7O1K6HaHsjjQVhpzh3bBwGd+iSMR57Qy9b9Sb6f940EFrPmJl7Wz/B6VfSFPJYVAjYcZIZUE0l21XJORZ50KD8xn6np/jng6VHY5eAyV5WjvTIAjrWYbu103WNqO0qBiDkUpC78lFttUn3iwZrSgKy/N6WJVjVJcPPqRmmy96RNt5khid2zxmd/VNlAGd2jLbuUICFzMOxD8XQnaLlHJSg2lqKAWxrB5nVxbOESeoWcsrIhAFKfZWr5nCp5CPOMg50TRSHSOf1vVW7r7Bfds6YJFjOK8Jxea/C5SsQl3a/ENI4qgvH7ZWJ80SzHZIdEKLAhAYvS2W1k9dxqJ5xAKiUTvyth2Bd9a3la6UYdeEcbvbAPhl+c6OEW8UhkVlUFJrCyphDfOUXiel1qxzz0GiImHceDXZNLTvZyLsO+9AIHOZ4rr9KZysEhcO7KkxPBq7cwTCRV3kZfXflhQ5P7qyEwtqQkXTzTZDB36MkeWgCGnp0lj/6daehR8mJAkliH4T+bByb2M+zvZ3z/2hHVCyeTPgCEUbtMTf79xWKTS4mDvrWiCPM642Ze2cxJGPCarqi5A4fXHgVqQf5iKTBqiouYs20JUjWsxdf2548f1Ss6MRomg/GOSEtx8e1kmVeLpAwyICrQMtd4fFvXDR7WJCgYE6kLfphHKN3G4kG+coCvu7WxiVSvxgFz0ePORfsnirYYhg5VXOhV/ttpTr59hSaatq4E/RZVS/r97s283yaCHj8jDfTrS0d//GpHHnzkDRk/qa3SAahjeZLl4DtaQ4GdOqrOVTB279RXUcKxeQIgOhfODdAaQ85kf2pJFtCIhpQ3JaXeNUFoedCPZTpaTCrXu5cPmRlMpsV11kKR9eul0xRIA1mARmny189K2dlpCjYWPCLbEMlsdlH+wRjaii+iMSpBUpfHQln0akuIYjYnNRP/rcodbE91/oPuF3YDrbM2DABQlGBj0vlvZhd1j888KEgj0RnKy3hbTMe8/gYkmj+hgVGz7cbnekBlluSIJZi9CQnSHGhre3px0jHRpmc2Mi7Wbx1oJV75Yxwxf+cks5asr/ec74JyXUxHNd6y/dR9je/0k2Nvd/rkw9dciicpt7ANlhD6afN4R+CX54WQ4TCijD30Ri1+30tBcdOpATScJqZ9FkMEUH/K6zBYCK48t0+HnJ1JYLNy6Eu8/q8LFTEnBbwzTW1sVOVPU38TNb8wCApZmEZZ+PdPwDvaqyMyYqgI0zTJ5lx9iOMg2QSmshMpCVj932rx/M75kKAED3U7IAniE8ZvF3Tj7Lf9g4WxLwSqU7RKYzp7xWQfdUbgNLAhuNkyxEvi8sTJPFcciJgBCcFQmbRk9/DoZZ7ySAWbNYkh2J3KcXNyYcSdy4zpLzlMrmSUS23ca0tel7UFBDC5ji3XHFV5eL1s7xzUIlKuvQel3jlBRNXyRmySViIvEb+vBXwVwGN7em7AmdIvw50Zgo5WGMbHxuXb5JNZjSIwtKSe3RbOXvA/4gGa5oAsttcl71Z7c0jz+EbJgnYGI7cxgyaeEublffbnwjvNA+07nCulVapvcXr1h0pwUWOSNraCAOsTQcZ2aejjDNLEjrozKSMCH2U4+7RqwLj6jiedsweLeh3lRx1SYsQ9VwmnpDRk4nm+Qktw0WpMt3WtjPU8oEDLms/gdnHs5bbYzAIyC60u/pvlZPX8Sne0WKq1C5WLE9ofYqtbWHFOv9EMKZ0xtIT3hshl7vM77pVfrwYzMqYm1RTvwNJ39+YU/gqx9jitiV65Q25d8E5nmFTALzU/o5bUOcDTe3BH8At755lVMuomXYBuJ3796kqx4Yg6GL60PvUeykaTfmPLMNgwrB4/DT9+FWtgc3JqGRJWhisXMbfvtDnK1Xc8TqsR3CMlkzwhiENKZm/61u1GsFmDoHyUoirTGMvqbnjI4FjSDidYMAOL8hNP4vFcgkMQV7grcbkLCUM9QW91XsPGPvfvL7HWPEhZlAhr3tNhTg3Ujyw+tqga8ZLPaNrZxs+81ASo+Ckqi1id5Wb/3ujFmhLCrLEVI43SVUrqU+DLxsZZDaO/qAYuV59AzfbzaybV3wUmOrqMBl4GRcp1f35PPFwYmTwlB4T+M+NE1dEuRz50pO8pv6+N1jlka9l65dgL0wWBvZAC7jaYRmf2/WCgiFyBCDS0pD7ddOGgeDXqwZraYCy+s62P9iVJatnY7smSdggLH7kvj1Sbx1VRUjzCjfsLj7l+DfLTkQ5peF1n+os5CQg1PIqiyxDZamZ36MPa1w6kvLnLAVIST2DxxGbJkPImKb2zhUNSPd7tVX5r4B9RxrX7tp6K+ZzB8/DzyY4Vf6cvVLzggFka7U58283FnlZEiLI7AaPAGU0kt/zgVZJQDqUbH6Oj+DXT+3t34eenOwKptRInFFWeemn2020Gtf0FJDK6pgT/lMHoUt1s7zRWIqO8m2eN3pPh5vcSRG881BClGL+DhV452Glzc+fAWVstqz1+IMQ3mHRv/t3T4hPZAyowvIQ+/Tz75PD1L2miuAisnDUvhf6VyaDbUmRL0l6OdSPRL6fcO0xsd07n6jD9C10zFKoKWxhOQbpzb0DxScuiPJezCBMY8fR+M/LLFnAchjiZ4wlQhEZjcdBiwbBQzAK1mSejcDDMxX12zVQf04GG+bQEgH2eaOP6+2dMn0WmJDSiyO7ZMM9ofPHGrZZ4CSCouaGLWphXRPv+YMmUUYIFG7XjC9CX6WpzIGHIH3iHoT+4TA5XN2Bl9vFpRhdfQSoosgUEdZTPWHh3js4+94KHnjUvhFabQwb/+sNXHHSJIxndqA/8merq+VvvyptZDSE9MySMRZ1mK/T9aWqTeQOouDQlxtc+62b4d3DJGvIArzwVravUF4Ho2Xp0aBhUjCuzC6WnXhHeZf/WqcAZ/yvlszyooFEQDmH+/0XKm3hJKia+oqH7kctKdnHLyFDZhq7wOivI3LN1/vD96kM4GY6jnxOtBdo9RHf9bInGFV8hBTkVLhLxPmJD6NHtTBdRnwQ3GqAI8SnnwthzpF+69FaiQDOhCng5zWzX/gBMuHF7KRlVK4PYV0jB2/7r3FhRB6E/MK6K1J4obbzzsWaf1Sd+GqCNBNOSZYpyRexnVMaDKLo8h6VWm2MM1drkzrxXoKe7l6ElFpnSY1H7t8oR2w2qkBkCgJkQTuX83megGLtr0TI+pCTXDsPwdFdqwxFYBCS8P42l/pfL5lPzqOmg/4YLNTGnju47xOt3VuKImdWLjZcUAABbgkQg9HNvQBFZEqhNPqoA+5jrxFRh4MMQw4yGuZkji/o142LzFWjBK9qMC7G5PcnYleZnRfrjjr/dKqc1PieKeZZiqdnibcY3X4eWFDAgTlMaY2r8e+bNHt4cCL4aoSMYmw2sf3ZgRx7TiIszt6OL8j/i41NR69Y/+Y2ltbgunFccTPf+WElOmfeNbLI6rAYdHMPo9fnshzxaCMI0s7+tV7uHbE/2b0ecbq1tKT6jL14xwE33aO+os/mloLU2Ag5ViCZv3NXDyhlTIV4atCckyb7JbHn86lFY0ACONL91j1w3QUo/cmDJCxwAATe5pQ/WE8bnf/bvSh6Ny6W7PCiCQ7JKSXB3TcIZ04ggdv4qAPOZwUxy2WzL0pIHDrixi2lynUVjeZTQQZjQ5CMZ8SUDmh1A531c4nSnVwEnuXYuglEUYulw8S1Gl1WHNQSYqQL7EiXrZHPGZrb0DBuyuwuDWDlPbHViiE2eWiqlGz+pi9I/yunTesnGN/CnobcwDqzflsDlXcMrxpUXjQ6QKg6k97bPwHJ93OwedhOgHp+nhV6bQ8z1embHlPQALz+XoQ1+Okupe3DvaDn3CaO/OoKEfYgsZlb9K0CzUZsoOLy9xnE0wUxgVOiJslnKjLT1fdF8nSlM8/bsa7p+hqk9OaQN3jFOTXr8S0hb3wsFOZSgKNOKRGlyvUpMu+uCsjQ3qgpTEsmEXnPCS1rWHKbyPKuIebdOYnnmVkGQeixrMRutubCVVO41fmPsF3cJr5s/Nog5/HLDsOElTy/1j4wctKMK2ZPMUnRx5sS+XJQIGBMpixyTa+T91ehmOtLqH3OVI0nSf0LR83Ph7j/yj6GVec2Mlrwgx/b7S3RfF4XHtrgEBN1cz/BqdWbvHv4Iqj+dLy2Mm4lE/vFKZz1eqqUx+QNleBmE4VPqZEobUQUptzIsjhW5xG/0t0FKsVmDqBjeLgxftqvM0FbmaRoQwia0LScN9NXDYn845EnQ9A5hf5Ovj94ByuXipGXKuc0JpT98LGhSME5D8tdHapvTiYIenqKKyxDp7mL2SWs60A4+uhShgtCfxXrx9EpZllnnIxiTpamwB8z3dtbhzzfHiaW5dC6K3YxCKjrZyeCX/uwsPqiLwNmSx+Lkc+rHNlUEoJo7MVJYmeXk1/fgQ6FaiIUxFSOhcDfiSXlx68cdXI+KtzjOBMWVQm3E0WPAPU0nBACQr6zXNsHgctRszTR6CgK8NSOvXBPC5t7SZs21dEoJGbWBBJc5WEn58G/bG10ti786PQBtksVJ+39rwFFiQcgxvESFnTbLJHhrak2ymIimnLctiVzdQ+hRdupFmnSmqDcRhaXwM27ldkLtyDj0I80zNCKoUhjkImr+XkCQG4uiHrWoKlso2Y50UUjLEMoPjq45owF+l0Vi8ejqw5JOiqMTMS0J8JxG7FF2z8ydlwOvsz72i1m0SmvY92VLtVWXpLS4oCrdmsfiDXvm7VT8LSsws7GFWPrPZv92YCU+c4gfMbWhqdiPyWlD8OFLF9kPMX+wZYTNnop11vNphp31B+Y+kOyi8TzLSvJl7E8exgKIfhenxf4R+0TNcGRH1tSoLxWeKK3dMcjvUFjvfhNZbcuV2iKm1RRmZ/7XYGybGSEjurYkJNUWy2x432LxG9uqhLa/BydwFenoqfi0AZjgLqP7tY3HVFHG7d/w5eaR1csFuzCgoluwRkly9e9Le1+tqjC/IwDZEGFO9FjpwRzaD44yOSupUJ3G7/F86lkAUK4L9RGFZds95v5//mvsv/8BvzE2LMJbnGoh0NnsBhdfjwyUELYC2RWFAPRzTsUGXAqgGrmAgxKR7Uz1/WJFnHKCqzu7ryP6F8Bpe3jjRB3YBSu3sIwUXZZife3wQ0QVVpWuMrKmDocdzWZw//zXFtyoAZwdb3TcmyFO3djkT4ZIqacbP6ME3hlY63tyR9gZYzTrtQCgjl1S6Wf+XWHF8VorCTGepCf0rsHEcn9K6bZYiDQeP+evXpVLYDFwXMOSVqSofTu/DZYzKW9XfO+gkFZDXaO8iIpzCspB0t1uiJFagSO2tkoJ0Rn9Rn7hguMa8g6omjkjOVK3RSC5XODDGNquq6S7vQmcMayvdzRDzjffua0xHqagWJRAafrxpEtf9o+sBBqKiNK6z+D7eebNHtSEiBA3awvQMdVH7xZozxbSji6jlaGL2hfpwXva6T41yU+ht5qEZFcWQG/y2epmn30ltXqSZgzTBMHoOnVsRzxmiq6/Nw9NXJtDTEd4LceafgYPOZ+rq9Yb4OO5Wv3AP30FqF+wA45VksRtfPFj7JvZhyg6vq4O15bL3PAX68K6cHSk9CeFi1rHScDZWmRByDaOob865Y/UMc7vfdxlwJnXC6WbtCCiU7rsSVq1T+qXW4kqFP7kkFMY4W78dPzrOfoGJrA1i4FaP+XK//5Oa7BSpAM9s6UC0hzE5/d0Q8wfdSmns16uiFmOamPyyW1kDdWvLGAZisr9u87k7FNmL7x0bKMzkxmB0JFN7Hd/ZgU0eossuz25E0ixo0o7cOkgvZMnObdwNCRfnovl3tPLTYRfra4y9CQENwzvaHT97kUQ3IA4jjXHD9x/w+7VuC5PENSExzG1qQeeEsDLeVpn6DPZhXO9MoKmX7ZOp/59y8Cf0YsgMqysBFeU6aZSf6iLWhyOrDY/KKddPulr8+bsQbBehilrsI6G0JHIZWX+7cqZdz2XO7TgEHrSVAv7909CsXkLoH4+igrbGMvjdHmhCzjQxMYyOTOD4LfvavB+ZneS2IXxNHsti9KV5D8RdmPsP80JqxM0lopYNMhj2PmlRB/RbRa8kCCI0RDPqP1rxu0cfDyouLshyXizRUaPtGrEPnq4DTM3owvYP+JB3VLpzgXxrRu/GGSO/Q7JTfb7aGqY1YkkGjgcrt88xeJ6PexvNMwYurQthY/cmYls//LqR5h4Ci019y0NzJUgYdlaz1q7cUaSHT2gDhWYbk/21WPYk3uBIDo+AIpdPkPueN3iyNLAAIR0JQMtVAdB6tHaTOmSloyAdBOtz94TkkXv3E7Ia9ULN5N+IIj7guVj+vHkal5rSSoWnoICWzLJrtR5ScMaWIyOsj8vgVI3R2rd3mjDmtCOJzyDRTXbl/wP9XZq7rdUNKSMPZfqmSO9nAUJbUyaXY8sIbioAt6lKAhGmAV+KSvjXk/AyjhvYAT0ZGIAAAMDIxNQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAI/qfeYy9H5k0ZdvrH9znhwiOHXGr+fUyWDJS5RvvpEJhhc8dye5X+3PBH7dwBiUBwqVtJevi95CTtr8peCz2CJBtHuoeJ5ZB0hR/T5j/Z0OR9OyaKIx0srG1/1mJfgNS4wDHLsNo6yO0t6Pb2azx9gBGyVJmoXl5UHE+Kbp7VZEhg45eytoE0swK3pQabecQQrfI9roetx9T6H7KL+SGS2CGj77YE19QcrYeqFsvNEKB5mwa6t/mMZIXuo9+gNwpo04NWwk0kT6wPVpgm6RjoOS5j4srjffD0N4OMkez+R8d+Um7Sf3S0PA0mijUmaPDA2T/s2hedaYTmsfm/LBE+iCcdieO8xXMzUcjHQpy5bWyIcBsXsuyCFphbdspynrAYI/Ew8ygX1l1JxmpMkVYP4DkkgwaNx5BbMpYlIV6xRKxuwj4wMjA0HoEm3mRvIJLWfVqp6uel0d5VlAhqx21dlhHf8w4AAAAAAAAAAAAAAAAAAAAAAAAAAAAwMTA0AAAAAAAAAP8AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAICAgICAgICAgICAgICAgADAxMDAAAAAAAAAAAAAAAAAH3goDEx87ADAxMDAACAIB2QQAAAAAAAAAAAAAAAAAAAAAAAAAADAxMDAAAABkDTwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwMjAw////AAAHAQMAAwAAAAEABgAAARoABQAAAAEAACxkARsABQAAAAEAACxsASgAAwAAAAEAAgAAAgEABAAAAAEAACx0AgIABAAAAAEAAF8TAhMAAwAAAAEAAgAAAAAAAAAAASwAAAABAAABLAAAAAH/2P/bAIQABgkJCwkIDQsKCw4NDQ8TIBUTERETJxwdFyAuKDAvLSgsKzM5ST4zNkU2Kyw/VkBFS01RUlExPVlfWE9fSVBRTgEGDg4TERMlFRUlTjQsNE5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5OTk5O/8AAEQgBdwI6AwEhAAIRAQMRAf/EAaIAAAEFAQEBAQEBAAAAAAAAAAABAgMEBQYHCAkKCxAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6AQADAQEBAQEBAQEBAAAAAAAAAQIDBAUGBwgJCgsRAAIBAgQEAwQHBQQEAAECdwABAgMRBAUhMQYSQVEHYXETIjKBCBRCkaGxwQkjM1LwFWJy0QoWJDThJfEXGBkaJicoKSo1Njc4OTpDREVGR0hJSlNUVVZXWFlaY2RlZmdoaWpzdHV2d3h5eoKDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uLj5OXm5+jp6vLz9PX29/j5+v/aAAwDAQACEQMRAD8A+YaWsDUKKYxaBSGFLSAKKQC0UDClpDFxRQMKKkBaWmUJRUiCigYtFDEgpaQwoqOowoqmAUlIYtJVCFpKgYtFMApKYC0lAhaSgQUlUAUUhhRVEiUlAC0lABR0oQhKKoQlLTASimIKKTGFJTEFFUIKM0wEpaQBRQAtFIAopDFpaQwooAKWkAUtIYtFBQYpaQBRSGFFIAopDFooAKMUDClpMBMUUAFLQAmKWmAlLSGJRQIKKAEopiCiqASloEJRSASimISiqASigQUUxBRTATFFAhKKYwpaBCUVQhKMUAFFAgpaQBS0AFFAxaKkoWigQUtQULRTAWikMWikMMYoxQMKWpGFFABRQMKMUgD6UuKACikMKMZoAKKBhSUCFooAKSmgCigQlGKYBSUCCiqEIaSgQUVQgpKAEooEFFMAxRTAKSmIKKYgpKQwpKZIUtBIUtAwooGLRUgFLSGLRQUFLUjDpS0AFLUjFooYxaKQwopDCikAtFBQlFO4gpagA60U7jCigAopDCkpiDFLQISigApKoAooEJRigQGkqhBSUhBSVQBSUCCimIKKYCUUwCkoAKKokSlqQEozViEpaYgpakAopDFpaTAKWkMWkpFC0tAwpaQBS0ihcUUhhRSGFLSAWjFIoTtS0hCUtAwopAJS0DCigBaKQxtLTASimSFFABSUwCimISkoJFpKYBSUAFJVEiUVQgooASkpiFooASimIKSgAooEFFUAlFMgKWgYUtSMWikMKWgBaKRQtFIYtLSGFLSGFLSGFLSKCikMKMUgCikAtJQULRSAKKQBRikAUUxhSdqYgooAKKBBSVQgpKACkqiRabSAOtJTELSVQhKKBCUUxBSVQBRQhBRTASigQUUwEpaYDaWmQGKWkMKWpAKWgYUtIoKKQC0opDFpakoKWgYUtSMKWgYmaWpGLSUrjDFGKLgLRQMKKTASlpDEpaBhS/hQAlFAhKWmAlBoEFJTEFFMQlFMQmKSmIWm0wCkoEFJVCCimISigQtJTAKKYhKKBBSUwCj8aBCUVRIU6kAUtAwpakYUtAwoqRi0AUgHYpcYpFhTsUhoKKkYUUhi0UDCioGFLQMKSgYtJSELRSKCimAUlSAUtNCCkxzTAKSgAopiEpaoQlJTJDFFUMSkoJCk7UEhSVQBRTJEopgFJQAUUxBSUAFFMQlFACUtUQLS4pjDFLUgLiikygpcUDFxQKkYuKKQxadSKClqRhS0hi0lIYtFCKCkqQFpKQxaKkAooASlpjCigYUVABRTQBRigQUlUAUdqCRKMVQCGjFAhKKsQlJQISigkKSqAKKoQlFMQlFIQUUwEopiEooEFFUAUUyRcUUAFLSGLRUjFpRSGFFIYtOoGFLUjFpaksKWkAUtBQUVJQUVIBRQMWkxSGFFAwooEFFIYtJQAUuKQCUUwCimIKSgQYpKYBSYoJCkqxCYpDTJCkoAKSmISlqiRKSqELim0AFFMQUlMApKYgpKAFpaogKWkMWikAtFIYU6pGFLQMKWpGLS0hi0UihaKljHUUXLCipGGKKgYUtMYUlIYUUgCigAopAgopjClpAFJQAUlMkKKYC0mKoApKCBKSqEJSUxBSUyQpKYCUVRIlFUAlFAhKKYgNJQIKKYBRTAWkpkDqKQBS0DFopDFpakYUtSMWigoWnUhhS1IxaKRYtFSULSUDACl/Cs2MKTFMYtJSEFAoKCikIKKkApaooSlpCCigAxSUwClxTEN+tFMQGkpiENJVkCUlAgpKokSigBKSqJDFJTAKKoQhopiEooEFJTAKTigB1LTIFpaQwooGLilxUgFLSGLiigoXFFQMWloKHUVIxaWkWhaKksSloAMUVIwopDCkxQAYpakYUnegBaKQBRQMKKYBiigQUUAFFAhtLTEJSVRLEpKskSigQ2irRIlJTASkpkAaKBhSVRIYopiEopiCkoASk5oYD6WqIFooKCnUgClqRi0UihaWkMWipAWlpFC0UihaWkULiipLDvRSASlqRhRSKCjvQAUUgCjHNAwoqQCimMKKVxhS0CCkpiDH5UUCEoqxCUlIkKbVEiGkqxCUlUiQpKZI2lpiEoqhCUUAJRTEFJQIKSmIKTFUA+lpki0tIYUtAC0VJQtLikMWlpDClqRi0YqShaXFIYuKWkWgoqCgxRQULSUhiUtIAoqRhRSAKKYwxS4zSAbilpDFooAKMUAGKKYgpMUCDFJViD60lBImKSrENxSUyApKsQlJTJDFJimISimAYpKYhKKYgpKBBSVQhKKBDxTsVQgpaQwpcUhjqKQxaWgYtFSMXFLUjAClxSKFpcVJQtLSKCipKFpuKkoWkpAFFAwoqWMKKAFpKChaMUhhij8KQBRQAfhRQAUd6BBRQhBikqxBSGrRI3FJTIEptUSJRVCEptMkPakpiDFFMQUlMQlFMBKKCQpKoBKTFAiSnUyRelFIYtOxSKQUuKQwp2KAFFFSUFFIY6lqSkOopFC9qWoKClpMsMUlSUJRSEJRRcYUVIxKWgAoxUjCjvQMWikMKPWlcYDmloASimSFFUAUlMkSkrQhhTTTQhKT60yGNpKoQlJVkhSUyQooEJSUCCkqgCkoJFpKoBtJ+FMlk1LTAWnUMYU7FZjFpaCgpaBi0UhhS4qAFpaCwp1SyhwBPQE0tQWhKKRYUlZsoQ0lAgoqgCikAUYqGMKPpQULRUjDHajFAC0lAxRRQAGkoAO9JTJFo71ZAlJViExTaZAlNNUQJTaoQUlUSxKKZIUlMQlFMBKKBCUUEiUUwEo5oYiWlArQQ6nYpFDsUuKgsXFGKBi4pcVIC0YoGGKXFIoMUYxUjHYJrWgsmf7+V43bR1xjr7Dnqazk7K5rGLbsjp7OCP7dHBDGJHUklUYkccgZHU8dRUOswQJdSFYWVVba3ZlbGR9R+pwee9eLzydRantKCVN6HPmxkdDJADKmM/dwcZxnH1PbNZhUqSCMEdQa9JSu7dTzXG2omKTFWITFJSJEpKoQtJUjCloYCUUihaKgY6k6UFB1opCFpKYBSUxMKWqAUAmrAhOMuQg9zz+VDdgSbOln0lbaG3Z5MLPuwzJgggDI/Uf1rEubGW3AYjch5DD6D/ABrlhVu7M6J0mloZPNNr0DgYlNNMgbRVkiUlMgbRQSFJVoApKoQdKKQBTaCQpMVQgox70wJsUoqhD6cBUloftp22oNLC4NJikOw7FLigBMUuKQC49KMUhiYq7BaTT5KIxVepwTiobSV2aRTbsjYht1hlCuhMhHC9+/J7Af4V2WvN88QhztLExpnO7OCv1A/nxXjTfNJanrwjyxZnaPcGHUVaNGmKEqzKeWd/lJz6c/p2zSaq4j1y6hmUsDhWCjqMAnHv3HvWLt7T1Runal6M2FxZ+GzHn/SIyZA65w0TOgB9CM44PPPSuFmDYWRQHgb5dp52HrgHqPUe30NCbcm3/X9McklFJf1/SNXVtDXT5njWVi0ZbcpTHAcqGHPTAB/GuRMLfwYceq8/p1ralW543aMKlLlehXxSGu84LCEUlUSJRQMTtS1IBRQMWlpFBRUjCjpQIXtSUwCimBejsp5DjZtwu75yFyPbPWpJbcWs8kE6v50bMjIMDBBx15z/AJ5rn9or8q3N1TaXM9judHgtnW/t5rdGkSzllzt/1bheACef/r9PWuRtUWCM3cnVTiJfVvX6D+f0NckZvmlr0VvxOyUY8sfV3/A37yZ10XSpTy26Y89/mGR9KxpJnh/eQtuiccoxyDnj8+xP+NXCKTa8/wBEZTk7J9bfqzZ1jSYllt3tsobmISbDjAJJH9PT6VwkkTxMQ6kH3rrpzvozlqQtqiCkruOBjabVkCU2mSFJVEMSimAtNp3EFFACUlUIKSmSFJSAtAUoqhEgHNSAZqWaosKmasCBvSsGzqjG5EY8Uzbmi4mhNtLtqiLBt9aNtIVhdtTRW8k0gSJGdiQABUt21KSuaiWSxOvn5IPTHO49gB3+vT610MEyx2sjRcNFIPujPDAg4btyF/yOfHqyc1pse1SioPXcwcFJVgUZlZh5hHbH8I+nf/63PY64yxxLNEo+eSQBlQqqluX4PIPYdePpSl0t1/II6p/1qO8JsttNJcMjPghBtGSC3yj26msXxGjp4gugQQ4cdPXApP8Aj/IIv9zbzO2MUzeC5rYw7ZEO/PAyu9cqPcMDx7j1ryu0m2N5bruRuCp7/wCB9P8AAmsoO7kjaWii2d34wL2muxlWBIjJB29V3vtGO/y4H4U3w3bRy3sksWBGyKGXJyj+Ym3H+yWxz2GfQE+bHmWHu3rZ/qdUrOrb0OObF7l0C+cB8yYHzj1Hv/P+enqmjQWc6wJIySncQHxhgHZRz2OFB5457d+qE+SMUv60MpwU5SbMD+zJzbSz7QqxEhg5wRgqDx9WX8/Y4yvKfIAGc/3ea9OFWMm0jzZU3FXY+S3lhbbLE6EHGGUg1Bt7YrdNPVGTi07MQqQTweOtG0jrTuTYNp9KMU7jsLijFZjsGKXFFx2F2nHSpYreWdtkMbyN6IpJpXSQ7FsaddeW0jwtGinBaX5Bn0ycc+3WtG00c3k1vEl1Bmd1jXO4fMT0+7+oyBxXP7VfZ1N1SfXQz0+zLgiJnCnlpGwpH+6Oc/jWzdQ/Lp/2CMxPcQMzBGPXzJB1J4GFHtxWHM5Wu9GbpJJ2WpmgRpOkET78uBJIP4jnt7fzro9cX7HreoTNgXD3UhjX+4Nx+b6+n5+hrFv315p/oaxXuPsmv1J/CzxiXUzcE7G0+VWbrjOMfjnp71yF1N58vyLsjUYRM/dFbxX75+SX6mDl+787v9DstQUnwnpPJwDMcf8AAxXI2kikm3kPyv0JOMH+gPT8j2reMb83qYzduX0Oj1yYRXdqj8qLZVkQDlfmbH4gYx7deppunW63Nw9tNH58Tqvlsuc5LADHt8x4Pfjsaxfwcy8/1N0vf5X5foctcWO1swP5qEbgQMHH+f8APWsdlKkhgQR1Br0ac+dHnVKfK9NiM02utHExKSrMwNJVCEopiCmnjvQIWimAlJQSFRs6r1piFBBGaWgR2keo6ddWYs3sre1cL8l07PlT1OdoOc9OhA9utLCNLW2uIZf38wXMc8UpUE9vlZckeoxn0IrvjBKHNJ69v6/zPKpRlCo1dtPXW1l5LqVLS3gW+EOpefAn8QSPL8jI4JHWugGgPcq82nSxzQqeksiRyAepUscc575745rjlZI9TnaaSV7/ANf1/mMOlT2hiaVVdJAWzE4fAHUnGcY969xtvD+kXWhrNvaOYLlm4Zc9s46duTXm1IvmSbsj0I4mnBeemnr+Xq9DwvUrM2lw8UilGU8hhg1hrHvkCLgsxwATipg9DsmtToYtAvZLpLbZGjum9S0ihWX1Bzg9/wAjWbe6fLYXLQTbN69djhx+YJFdPQ8unUjVipQ2M/yzTvLJ7UXN7GraabJcOoC5L52jOM/jWna5W+gjixEwlG12XAU54OD/ADOa8+crvlPQpx5VzEl9H5nl+USkrKQynJ8tcngHv3J78/WtzSoHXSWuYI5N8Ux4GcOpXgt/ukZ/E15DdqX3b9r/APDnq2bq6HPJp8g8i4jiKRyuMk5wvPAB7gn/AD69VdwNqV4TbrvSRpXwcgMOrDBHBHOOP4eldF1zLXa5jZqLfex6L4S0U2Wn3Mk8ZbMg2Z78BlOB3zj8axL/AMOXFxqt5fM6Q5kOxmz8oABZvqO2cdetY1KjjLm6W/r8jOEErq/Vf1+KK9xOv/CHGKOMwPGN6xgEOi+cFUk4xncrE+/OK5L+yDZmO8uY/L81gCiYOHPIQDtnrz90HHJNckZuN33f9fielKKej6Gv4xWK51OGCHDAxZhK4xkyPwCOCO3tx71U8K6e9nqRe5GG2cREkFhuAY9OgGee5HGcVxU5KOGa73HyXqLraxxtvpbzziW3J8kk4OcFSOSCfYc7umOevFdd4uslk1CAQOzyCADDYG5QzAEfgAT9c10KprTXVb/cN03abfX/ADCG0EXhe+W7mYkeW2wfeQblCnHoQScH0HSsZrH+wLATzjF/cYNuD1jQEHfg+vTn1PoaftHzSjHq/wBNfwJUNFKXTX1/p6BaWEl/r19JJPNBbwO8lxKgOVUHoPet691CT7DFFAk9naXMshh2k7m4XliOWzkg9fxxy5pScYJaW/4b8ghLlvJvW/8Aw/8AXqS6LLqUF3qb6h9pdra0laMTFiEcEcj0OM8jsTXMynVpbdJrOW/khlc8gsTnA4JHXHr3/Qc8lTcrpK2n4s0UqiWr11/r8TofEjOdfu4LHzITbqNsC52lBGCSF7Ec/h9OcITufCJmKEz/AG4L55XJ2+Wflz6Z5xWyjHkXy/FnHVlJvT+rGjpJA1KwivIVlNw8QWFoht2nHzkY54Jx+fscW2W8/eLcQxQRqNzSS2ifKM89V5PQfiKEoqV29Nevmb3bXu+RZ1G6Kw2M1pZ20cckDFh9mR+fNcckr1wB6D0Aq5PcQxC5juLS1llT94wSBEMQLBQuVH3sNnnIBA44IrOSko3u769X/mbwab1Stp0RyE8l5YTfurh0V13I8J2B1PQ8fiPYgg8irFyjX0Bki4ktztkhRcLtLYVlA4HJAIwOSDzk49Wyspdt/wBd/vPPu9Yk1vaSHTWjjMMzPKSE6kuo4AI68Oxx0OB16E0KO5utes5lZd6zptMnC7gRtXjoOMcDgfSiElzS06/ov6/4czadkv67/wBehi3VnPBcLbsoYkAxmPlXB6MD3zXX39ncLolk1vJE6rbESBD8+0SuSfdQT29s9q5uePs422Z0Rpy5pLqjm9HgjN9BLcEeWJVUKf4jn+Q7/wD166TxBpqzanf3FiXkMdy6zRnllO48j1B/MfrW9SbVVdknf8DCEbwa7/1/mbvhaRbNtThjCSMmnSu5OGVmAHHoQOn4muJvrJXhF9api3kOCuclG7g/57g8ZwIi2qzl0sv1LesPZ9tf8zvrm1EvgCxlAGYvM3HHPMgry2GAIhuZx+7U4Vf759Pp/n1x6VN25vU4J6tXOr8UwA3cJEnmymLc5Iw2SzYz68YHtgD0pvh+ymnBTGJWT/R+zLuYLu+mSD+Huc8/N+6l8/zOtRbqr5HFxyG2fy5d2zOQQPmQ+o9/Ud8fQjqr2C2GmwteReXNIQY5oxw6nJJPoPudvXvkU5v4ZR6/1/XoTT+1GXT+v69TiZ7R4cMCrofuspyDWdXsQlzI8aceViUldByiU2qEM3rnGeafTELVKX79WiGWI/uCmtIoNN7iWxA0uQcZFM8xsVViWxokPrTCSTzWiiRcMnFJmqsMlpwOOlaGJKsjq4dWKsOQwODW7Y6zfafM0ttOVdsbiwDA49QeDUvV3NYNxd0XZ9aub1JBcpDI8jBt4jCsp7424HPfit7T/EbWdjcW8sEczOm2JnGdhyMn8q5oWpuLS2BQtBxi7foc7c6hNdzmecq8jEHOABx2x0xVaNXkIVASfQVxNWR7Cbkz3LS7+y/sm1imJS9ilPlhi2ACBz/d5x7dKp6bpU2oapc7hFLbvu3MWUMo5IIz6e38qHKM5Qiuz/MKlNRi093/AJJDJT4bK4e9kTyiVGyFWLLgYzgjJ6847c1nW66Fd3awQ3F8xfAVVtVJJ+gf/GsObmt0Ilo2kew23hTTJbSGaPVY3h5VGKAAk9uT1/wrz3XYLTSb0xRbJV3Ao4G0oFzkDn9T6GuWcFZNS3OmlVblZo5+BppFKRfOvlrHJcE4VMtkbn6D05PtXRWU5vh9jWK2N2TJNHIsqhcMhUqccA8Ljp2z7+VOOjezPZUtUifS3s5baf7XclbiNIlCxTIFICfKWLcDHAPPH1Brmn1i3bVC1o2ceYAM93zuOe/BIGPX8+tU4NXje+v4nJ7SSbjK1tPwPWLDxZo0WmPHfSlJPNVnKHcGYbRnjnHAzj0NcZfePtPu/PiW0kWOTLMzN/rG8vZ0HQfj0HrTqQlUglFdNf8AgfeYQcYz5pPqv6/BGhZ61p1zo0kU155QjYxCZADJIocMCBjIPP3iByc9axdVvXu7eyvjLDHHDLuji3lioAUbc9M/JnBOfmz0rwp05ppvyf8AXY9pVIyX9f1/XyOi1LULaK/tLlhF9seEbVyqou/cd245BALdu4yTxiuMsdbjHiqW+upvLjuHUMy/MUCsrYwOcfIB9D3p0qLs7+a/EyTUEo7G3d6hZf2HPYWkkKQ5BEmNolIIbG0AkdgC3XbyeONZddsZpItTiIlvsMoicEeUpZz95hg9doAIznHPSuZUJ8um/wDS/Dt9xt7SLVn/AJf1/mjD0S/gNhqBv3R4d3nvh/mdi6EAjrwV64IG7355/wAYzvcXdo83lJILdVaJM/JgnjnuO4zkdK66VKUZxf8AW1r/ANdzGbUeaC/r+vzZ0y6of7Gu4YYEhiZwZJJE58wODJlecgAgHg8EZxkCtKO/t5V0tbOKKWaKRzBg/JhduSTnIGE4DAHBBJwDnkdKam2uv5bHRzQdrrb+v1MvTLuKPVNWi1CNYCYZoy5wCIzzjbnJwAMY7ewGG3OqQ3FpYWt1Dt09lfnaQMcFdrED5gQR2XOf4aJ0Zudl2X33f/BKjOEYq/pqad7eB9V1C5sWRrv7Opcgby26MKNm3KgDIJJPUgD3yotS0h9EMTJEHEy3PkfMIvNKlcE4zt4zj8M1py1N476fd+Zzv2b0f9W1RoxThvEFs15LF9qijiaNR8rBgoDJggD5sEgdiQOCWFZcslpaaQ8FnPazWLTRqztkbyFYsX4yM5+X02ccjNQoSdlZtf8AB2/C5ako6pr/AIcrWdxYRT2Bs2W5uYf3UCy/KqjzWbec4BOGwPQgnsM1IY4ruTU5ZLiFEmjIeVTxjzA2ccckIQAcZJX1q5OUbxa3T/r8fwRHJGbuvT+vuHSRxX2lR2ptYrZUZjBL5iliCQq+7glWyVHU5A42nE0eC4hvbm88jKwpKjrJj5SyMo3Ke24gHtzzXWublkt7+u77ESS5kWL7TGitIFtI3BeRplG77oO0bc9GIPPHYg8duxNhajVYLmUSQXNmI5rqFusuUVndR2YHORjoM+tJT5dbdfwt6eWxTjJ7bHLaPHa3elXFtqM0yBJUFs8Sb2jLBt3vt4BIHpVbWLefTpdPtYnJu7SFkcxHOD5jsMfVWB+hqeflmk36/JFy1i7f1qbUdhaajq1nLaqUKtG8kR/1cgAVpdh7FcklfTkelWtMQf8ACYy3sscn9mzyTkysp2OmG79xnH44q7pO0trP8WjK0789/wCv6/Ev6RplvBHfX0TrBaXVnJb4uDgwyttwpPcdw3p6U/TLnT9P0vULaSPzIEaJQzDmRiSGOPYdh24zzmvPc5yTTWun4bfmjWNNd/66npZ0a2/4Q6SzSVDCqhzIGBCrv3nn0x3xyOcdq8K1i5068tre1ikSARhnjLqBhcLjkd+Ccc5yepxn6HklyRmuv5o8tTTnKMv6/rcn1AW8uqpd3cyPCGaIRl8lhvY8+igMMfTjoSKGmalaW3iG8lkniSIoEUyMQMGRAcd/u7sfT2rNqUlJJdH/AF/XmdmkWrvqv6/ryOF/tCyjiYzq810pwuADHxxk88n9DgZzzWRea3dXlsluzbY1OT6sctyT/wACI/nmvShh5Sa5tl/X9eR5c8RGKajuylp9+1jcByoljPDxt0Yf4+lPeeKR8xhlGBkN645/WvUlTtLmR5kanucrKckmCAuKqlmbqelbxjc5pMA7DPP50F3Pc1rymdxmCeaBu9TWjSZNyzHb3ErxpFHI7SttRVUkuemB6mpobG7uWlWG3mkaFS8gVSdijqT6AVirJ2KsyxHpN7Lp0uoJA32SJgjSnAGT0A9fw6VYfRL2LSk1KWMR28j7Iy7ANJ7qvUj36VDmrs0UJF/VPDV7o9hbXN+0UT3HK2xY+aq+pGOB+NWk8NPHor6nqNylkrKDbwupMk+ehA7KR/F0pe1TjeOo1Td0mR+H9AGrO891cR21hbsv2iVmwQCeFUc8nBxkY461Gml2uqa/9h0iYpbyNiJ7tgpxjuemf/rVDrx5nHtuNU/duzW8Uafo2lSRWOmyS3FxFkXE7HCsehAXHGCD/ia87+T0Na05uUbsc4qLsNpa7TjHipcgdqyZojqNB1BtO1WG5jjaR0bKoqgkn05Bra8SajqGt6m095aTRyRxqu1o8FVxnnAHqTn0rmm2n5G6szjvMJAViSF4GewrrdKvLK0BeZGeRXUqQONvOQR+VebVTtZHsUXFSTkdL4g8RQaxMjpaRwBQARGMZrkbu+T7TI+nLJZxnG1PMyy8c/Nwe5ripqSd2ehWlGSsvxMBGEswEzP8x5cDJHvjv+dTRtHFcxllk2AqWCvhj64OOPyOPevX0Wh89ZvU9zTWbVNDAtILuRpkI2yqD5TKV+YSADJIPOOc9ffCn1bTbe2u4v7OurlGICSXD4khYjIyRx13cd8Vy6J2tf8A4Ik2r6nD3OpRTyPlJbZCiBY0lbAYY+Y5zx1OPUism9WNTC9ncTTs8W6YshUo+TuX3GMHPv26VaST1NeeTW5g5LepNSruXoSD9K7bIwTbdzfnsok06O5ia7Z2cqQ9vtjxz0fccnpxj19OedJI69awTuatNGzHcRWkEckM0nnnkqoxsweOc+2fyrbGtrNbyRst3Jvbe4a4BBc5+YjbyeT79a5J03I641VEprrFyhbYWXcu089RnODx0zzWe2oTs+9ndmwBksTwAAB+AAFRGkuhcqjbuS/2pchXUSNtZQjA/wASgggH8QPyqp9sl9cZ7DjvmmqMVsL2rZcjvrsyyzLORIfmd2flskZ68k5Of1qV9QM64vGnndOI283hRg9iD3KntwD65EOktkaqrJqz2KM10WmkaMuEdicO25sZ7nAyffFSTXhd1MIdFCjILZJbA3HOB1PP6c4q+RGbqNlY3UpYtvbJzk5o+0ScLvOAfWl7NdQ9pItTSSEpLJcb2k+9hiWHbn/9dbekWD6pJKpu0t0iXczyMeQSBgAdTk1nJRUbtBzyKupR3Ol6pLBNP5k8LYMiknJ4IIJ5/GqLmRFIDIysf4WBz+FZJQcb9GN1Ghsd5NbzRyxtseIjay4+Uj0p76jPIZC75Mv3yABu5B5/ECtnSTKjVa1I/tUhjUMN0a52qc4XpnFWbO7kinJTYGkBUs+cYPBz+BNKVO6sWquoslw6gRMiqqsWVQTgZxyOfYVpXGqyySrJJEElEaruXIJXaFHf0x9aw5Df2vRkcepGKwuLRYx5dwyMSwyQVzjHHHXr6cVnm4V1X5juUbVw3PXv69apUle/9difaK1jc/t+U6ot+rFJFcOwWRjuIORksSfQfQCr0XiOCyImWN3eRGWZfN4YtnkDHBwR0Pr61DpNqyYKqo6s5iTV1iW6S2zsuQF2sc7BkNgc+owCe1QxXUj6dMn2mNAjBvLb7z54ypx278/yrf2Ctdr+kZe2TaSZDc6td3uHmnBKRhMgBcqOB06n361izXEtw4dyCQoX5VA4Ax2+nXv1NejCnFbI8mUm9T0ODRtHe0gbU/EclvO6BzD9ikcICMgZOM8Y6DHuRzXNXkGjIki2c97NII1CM8aorPu5JGTgBcDHcnORjB5Yzk5NQj37W/P9PIbWnvMyWjtBaQmMytcfMZdwAUD+EL3Pck++McZOkkejm/cO94LQJhWVFLs2AMkZwBnJxk8DGf4q9Fuqunf/AIBzJROnW08O3NvM9ql8GhUt+/uYU3ccAA4LHr0z90cDd8sE+oeHVs2gtdHn3MM+ZNOCwYKVHIHTksQMZYjPAFeevrElrZf1/Xc29xOxxF/NBPeyS2tstrCx+SIOW2j6nkn1/p0qxJPZnSoYIrQi78xmkuWkJ3L2VV6Adc5yfftXqxUlFLqc903cj02azt7sSahavdQgf6pZNmT2ycZx7DB966VdZ0uKNhFocO/yiiNJIXwWGGYg9SP4fT3OCMKyqN2iXBxW5cfxFZqAlroWnrH0AlUu20cgFuMnPJPfgdOKym8QziG7jht7e3a6+WR4Y9hMePuccBeO2M988Y5Y4ebV5SNXUj0RfPi7UftCzQ+VB5MXl26xpxbg8HZnoTnryT655rD/ALbv/wCz2sfOAgkbc+1QC5znLMOW/HNbxwyWt9Re22Hy6ld6hZJb3N6FgtYx5URXAOMAABRjdg9T1wcnpTbrU7zUmWe8v2aaBB5bSFi7c9iB15zk+nXpW6pJK6MvaMzL29uNQuDNdztLIcAu5yTgY59aqvI5VYhIXQHj0/WiNNJWE5u9yBWKngkH2oxjnBrrUE3sZXdiSV2lkMjsWJ7moOPercFFaBzX3H0tMzHqcdKUtk9azZSFBxXU2l5PBEQsjAEetcVVJqzOynuYMsrPIWY5J701ZCO9CWhpzam5ealNdyRvKzEogUZJPFY8srSPuYkn3rmp01E6qlRyf3FfcaUNg13WPOuXhcP5YXccA8DNJ9pk2MvmNh/vDPWuXkTHcrPKznLMTxjk0ea3qa05UNSaY0SEHqad5ue5puKLUmbEWozRQeWssgX0DYrNlmMxy5Lema5uRc1zoU9LEBKkfcFTW9w9s+6L5W9q1abTVzO6TTSLM2o3U8m95nz7HFVlu50JKyuCe4Y1ywoQStY6JVpt3uS/2hc/895f++jTzqd2Tn7TNn13mn7CD6B7efcRNSu0TYtzKFznAc4qGW+uJ2DSzOxAwCzZqvYRvdIX1idrXHrf3Ii8oTyeX127uKeupXKMjLM25BhTnpQ6EdwVeS6jft8xDAvkNycjPNIb6U7fuHaMD5BWPsIrY0+sSHi/k+f5IfmGP9Uv6ccVYh1W4t43SIogcbWIQZIyD1+oB/Ch0E1a7+8n23kvuFl1Wae4eeZYpJHJZmeNTuJ6k8VCdQcoV8qDk54iXP8AKo9hbRN/eWq1lsvuJIdReJgRDbtj+9CrfzFPGpsqSL9ntjvOeYVyPpxxQ6Db+J/eaRrpdF9xG2pMUQCC3GzuIl5+vHNMh1AxeZ+4gYuMfNGDt+npWnsW09WQ66uvdQrXwaJE+zxAqSdwHJ+taa6tbtdtNJptuUYY8pSyqDjqOePWolRlbSRpGvG+sUZ4vYfJaN7VWYtlX3sNo9KyWZgcrJjPOADxWkabT953MJ1E17qsCb94/fEc5yBSMh3YEpOOhxiuxuMXojks5LVl23sFmV2a4CbRn7hOaRbINCzefhgQAu3r+NYOvq1Y3VDS9zRbRZ109rhZ0KAgsnIPpn9axxbjAy4BNaxqqV9DB0nF7nUJ4faZIzBqFv8AOOkhIwfwzWfd6Ld2YlBnhlVFV28tzg56dQM1xxxkVLlaOqWGbV0zJnt7lYoZWB8qTIjG7OAD09utaltYavFqElrbCRLpUIcJKAdpHIznuD0r0nWhfV/0jg9lPoiCXStWtwfMs7kDGCQhIOO3H0rIlFxER5yyJ6bwR7/1pxrwmtJEypTi9UQGVyOT0qyt5MHViUO1doDICMYx06fj689a7m3KXM9zlVkrISS6eQfMkY/3UC/yFVjIacpOTdxqyF81sD26UnmHGMU4yaVgeoplJOT6Ypm+sXqUmPaUlQvYUNKTt9hituayem6sZ2GmTPrT2l3Iq4ACjHA61nD3ehT1BJdisMZ3DHPakSXY6t1wc8jP6GtG/d5RLe4jSbjyaZuFEpc0mwSsrC4pakgUCnYPpUlCqDmumSzvRFzBLtK7s4OMdjXFVaS1O6km3oc64OaQda1Wxk9yZxg//XqGoRchM0c1sYE4Vj3FMII61kMYRSYqwFpaRRZCkLnIqEqfWsjSwnGOtAHPr+NMoU4HGBTOtCBiUcUyA4o4ouAnFLTAXFGKkoMEUuDQAu09MGgg+lZ3LsxwRs4Ao2GhtDsxpVsdKQKT0FO6FZi7WxnFSBW3Yxz6UmxpMbtPXFOZeAajmKsxyL8w4z+NP25fGPrmpb1NEtC9DsVSGQk/zqJQoX7pzmuPXmbOvTlWh0rzRjS9rQuW6BsjA5+v6VyQOG5BFbQVrnNUepfaQ4XBIH8qqtITuyTzxzWPIaORVZidoyfl6VbiupIpjIshDEYLV18qaOVSaZu/23eFMec20Z4479e1bzeI55LQxSMrBsD5h+eea+dnh10PXjXZweo3P2y9knwBvOeBjtVyeaJtFtoBEgdZGZnA55xxXvWapxXmvzPLbTqN+T/Ik0IwJqG65jjkQI2FkXIJxxXciy0S5jWMweU/lj503cnp3/wrgxdSpGouR9Dpw8ISg+ZGhdeGNGkhd7eSSNwVAVW3YPpz9c9e1cc3hqM200qXDKIyQCw+8ecfTkY61z08dNL3lc6J4SD+FjZPCU6PCvno3m5I2DJC8DP61zI0a+MMswgJiizucdOK9WONg276HnSwslaxTk066jtVuXhYQscBjVJ4ZI9u9GXcARkYyPWvaU4yvZ7HnOMluiHFGK0MhKSqGFLimMt/hS9qyIRIuMZxSscmpYyWAMZkCHDEjBzivoyS0it9KM2YpZiNg8kK+5umMBvfqCT7V4WLdrI+jwa+JngF9IJbqR1QoCx+Vjkj61TiXcxO5QRgjd35xXoQ0gjyp6zOmvYk86N/Mjn3opPlDhT0wRjjpnFc3LGqt159B2rOnLQ6aySYnl5jyB+NRqgJrruecdRHp4eGN5ImXdzudgqgdzz1rKMMTh2QbQD3cdPp3rz/AGjuzoUUUWjAPbFSx2/mcLgn0zXS52Q1C7I0ty54DflQ8AVsZ/MYp84chrw2UcqspkkEw4CCMnP4iqT2hU8nGPXvXM6lnY6I07oY0CqpIdWweMd6qBDnGM/SqjO4pRsPaMqOcfgagx7flVp3IcbMCAOxxRx6EGruZ2Qcehph9qpCYoA9af1pNlJDO9HWkIXPFLk461HQdx27I680m49OMVNi+YN2euKA3qBUtajuIXz0ApobBrRLTUhy1HByO9S+YQecNmsnG5opMVXG7JGR6Zpd+eNoFTZl8w5XBY8D8BmnOw8zJ3YP51m0+ZGia5TUgSNgQzYBHQqevaqSjMiqGQEnvWCb5rHQ7cqZoBP3JZsBgwAXPJ98fhWMQQ/B/CuuD0OOe48MxGCScfrUJDjqPxzQtGS7tEJJOKcAea6djn6j+3alz7YPsKxLKr/e6k/WlLHZjtXTbQwb1EQ4NaUc8qtlWIA9KwqxUtzSEmtjRa/uTtbzZMKehYHt1xSpqk5heNW+QtuK7QBXkOimtj0PatM1n1+4YrIqMJVXbvOD+QxVq31mWHSZbUxPKkhO3JyE5GTXI8Ppvv8A8OdSra3sE2ri50tIJ4GzvG2Q4AAyM5GMGtjULq2ksraOIAojqPvZJXrkgds+v/16ycGk15m6mn9w3xQLUWcSW8aQ/MF5TluAcjH/AOvnFUrrS7NPD+Ug3TqcrKudrevU/wCce5qaVScKT9f8iJwjKpr2Od0fSYr+N/NSTORh0YHA7/L19e9QxaE91qo0+GSGJgcb5m2/mOufoPfpk19FPFNSstjx1RTjfqclLG0MrRupVkJVgfWoM17UJc0VJdThlHlbXYuk8YpuaDnRKDSHOakZetWVZlZpJYtpyHiXLA/mK9qe7trXTxcQXEsTEkjzRlmOO4XHX1rxcTfRI+gwrSvdnidyd1w7FsliSSFxUUO3d8+cdsc13xXuHmSfvmpcP5jIySOyhQBuYZXjoOfWs9sAnofbNZw0VjWo7u5MrqQFwv4ZquNvmc5/A4rVHKdfEm6zbMKqw+YuwZmI7E84xkjt3rIu55pkxLIJAhKqc4wPQDpj6VwqKudKZllskAAA4qwrFf485GMZzWzV0aReokcrxHGMDvwOfzoJJ5xgemMVNir9DvdOWS3s/ljgLNkq8sP3Tjn5uOn865WWdjPufy8MxZsKefz57Vxys5HVG6iOluo5GXbGvPUBcD8qpnzFkDIu4jHQVnFW3OiTUth0wbcu6BVPuCM/marDkZAUAdeR/WtYt8u5jLfYaAr8FACOfvgZp7ou0EqAfT2quZq1mRZPoREIqAMrLnkHsahdCuMn3roUncxklYVF38d/0qZ49pwy7SOSKltjSTGpGj56A+hPWgwhjxs/BjxWfO1uVyJ7ERiU8Bhn64oEHy7hkjpntWntNLsj2eowRNngH2prK4xuB/HijnT6kckkJtbGcU5omAB+Uk9vSr5rEKLZEUYDJKn6Uigk9M+1bJ3M3FpkgDZ4Az9aQowPOPzqHJGvKxoBLcDOPSlI9Rj8KDOwBM9eKdt7+nsaTeo0i4iyCMkAMvU4bGPrUQJyMkKSeMmsna50a2LrjbwZBub+H/8AXxVDPYAU0jNvUQZ6cD6UpIKnJH4iqtqSQlgaZndxx1610GLZNhQvABJ9+lN5x9B61iUVyKdyB04PtXWtjn6iKCeBV+PLYRV56cc5rmqK60NYDi742ZbP92gSMFGHYMvTnp/hXBayOrqWV8zAfG0Z6n29Perscv7pY8Iy8kjGSPx9a5ZJbHTFvdg4tpcbS6AH75XgD8O9aEIjSVDCiYBID8kPz6c9gaxm3a3Q1XK3cj1Mhrgq0h8vHIZQrKeoBwMfl61YQyTWewW6SIEyQqYYDA55GTj61lFL2dim/fH6UmxpAxjDMgIVSCF+pPc46Z71sadcWyak1xIE6hMuybV46k9c8D1FKpdybQR+E8w1IxvqNw0JBjMjFSowMZ7CsqvsqN1TjfseHUac2WadW9jkHA4FBqLAW7dmEgVSBuOMnt+NeiSywXTRzTSRPIwAY+fHx+BA9h6AV5VZPmVj2aLXK0zh9Q8pbllhd2X/AGnVse2V4PHeqMPDjhSDwQRn9K64fDqccvi0NJ4HjTf8jAnaQHyQfp/XpWczYPAx7VlB82prUjyuzELHb149KaGLHj+Vb2OQ2YoJxhi6gYyCJhn9DmqDJtOByc9D/TnmuGMlzWRvZkTLnkrjj0NAXjqgx685rpY0iUfJhtwyfwxSkBucAc/Ss3boao6iCKKO1XF1gn765OAPwJ/lWCyAuNisQDgEGuNtOWp1pPlsTTxEkeY8zvjgOd39ajgjlyCnljqBurH4lsaNNO5NL9pZFWUsQo4GGIx6/wD6qzw23OME9+tELWsVO99R6hJBuYhT6g//AF6HkUEDHTv1pJ62uLS1xAVcjbtDduOv6VBJuEnOA1XF6mUrWLIkYJgDK5+6rgnNSQ3BjkJBIbBHBA/XNDhfVDU7WHKRgNuIbnJ3p/jUO8Hjb8oJ/iFRZpml7ob8ykFVLHrjGSPrxVgbxBuULhjyfLyfwJ/pUyVldiT1IGnBBJchun3dox+FAJ8vA2sCerE8VVnvbQSlfRbiIrORtK59hn/69RiaRnGcAnuV4FbWuiG2hkjgnOBgDGMmkTOOAMeprWOsTN/ESlVz99HB6lQePzqTcEPyIvTnd1IrCWrNloNQJI4CkKx7k8UruGwCOAO3+OKet1cNLaCpGVXeTjdkAg8Z9OlDD59vO70WqctRKNkOEMjAjHIHIPJ/KmGInkrtbp8y4/KpUlcbg7HSR6bFFayC6lYSMoaMLF1+uRnrxnIrlBHtfDKDjsDzW6luc0oWsifaigFoRn3PBqmwUtkAL6CiLdwaRFsJ7H8qUKpOBx9eK7G7I5LDpEVT0Yex5qAoR0yKmLT3Boip3AHSuowFU81ZycjPP4VzSRrEmXA4BX/dbGP51XZufm2/8Bxj9K5IxuzobsOBOCQG9yelSbSysTnd296UkkJDvmAwN6kdT0q8t0FygJyQRvzzg9c8c8VlVjdGkHYklmePKGT5DyynIyfcdT+NQfaGgQmNYyXyA4UD26dh+Vc8IJxstLmzlZmjHNPahJSCUIxsKhhxzgjPv7fzq0fOljb/AEaWT5gQVGNoPOCMEke9YSik9zRSe1jJ1FQvlhon+UEB+ob6cDjv0rnCBn7pH417WHb5NGefWtzBTq9c88eDzzTjnsOPpSA0LJniuVZSAenzR7h+WD/KurTUb10eOFI5zsO7yoD8oP0xg+/X9K8yqlc9Ok7I5C4lMhw8Sq/dsHPT64psOccgBCwy7JnFbJXjuY3tLY2bpWijhWOWF4jkjARWzgZBwc49M++O9YrY4w2fqf8A69ZwVka1L3F3MBuXgjvuORRFncTkcDPzAkV0HIbyMDEFN5Z7QOnkNkZ99hqgxkWRvI3ZjBDBQcgdycAccmvN2kdCM12JbaAoI/uknNSIzKchifw/xrsa0GnqXoSjEglSR/e2gfrUkSzTsRbwtJzk7I93T6fWuXqdJ1uy1hih85YY5V+WWNYplkGepJPy/hxWDKrxS5jMW0cDhW4/XNcjetzpgtLdSI38qMAXLEDqEyoB9FIwOtMW8HmhmkcopzhcRn8gCBS5NLopzd7XK1zKhChWQgDACjH0z8oyaoiRVT/VEse5PH5Yq4wdtTOc1fT+vwIi5IGUUY74pC75yHAz/d4rZQtuc3O+hKjquH82XzPb/HNNkkDkHk49WzVOLUroE1a1wWQEbXBI7fP0qwiwqgyS57rgD9amd1sVGz3IXChuRkY/vCrcR8t8psHBHOxuvsRWUtrGqWpEUKZZtpwf7y/yFUyzHIBxnqAKlKMtdwd0WI4ZHYfKSDxwDVqWNI8jZlj6k5ptJaJhFPdopbGCbvLcL/eGcVF36jPqc11JIwd0OLYBBCY9sUI4BByMj1UEflRbTQL66jwFLZJXAxnBArTE8CRfITvx3bAB+grhm3ZI64cqd2UiyMwLDYD/AHSTn8zUTOhYkKo56YrZJvYzuupKHYgA/dPt1pj7g2HXp/skYFNRjcTk2jXDqybomiUZ+75bFh+n9TVVBNLKqRsxboCsZzXKnrrodLbtoX7m4aO3RAzMzgA7thIx6cZH6fjWIGeNuBk56Nz+ldsYpanDJu5WL5Y78D2AqYIQobZIo9QOtapcu7M92ROwY5xj6AD+VIGCn5gcGtLXVjPZjy0WRsZwfwpWlDJjBOPYVny31K5kil3o/hru6HL1FUqO351aTYQSy/L7Guad7msbDmEZUL90jjg7s/rSqyqPulffPNR71jTS4EB1OSwHbcc8VcCJDD80Dl3UbckY+uMVzO9mjVWvdkexjOAyxxkngNtXHfnNAVHYKroigEqSB+vGTWcnZjSIZUYPiV0HGQQQcj8P61JNlEUoyvHnBABxn8QKFZxVtidn5j4pGjkLvld2Qy/d+o5479K2rS6gEdxuh8yZmDLJ0WLryAuMHkdiOO1Yz0ejLj5mJNeSPO0gdgGPIRiMDpj8Qcd6yztzXbTi1BWMpSTlrqQ0v4V7Z5ZIBxQQD7UFGpY2n2qbZ5qRr1Ysyrge24gZ9s16BFFDcp++mtfPdvW1RSoXJy3JDE4A46etePXbvotfn+h69C1nd/l+p5/fQyJdTkoCqSFSyL8ufqAB+grPjCmRQ5wueSBkgfmK7YfCjhnpI0yIo5C0DSM4f5VEYK45/wBo+3HPU+nNaaWWQkSmU85Ib19cVnq7Nm0rLREbqwUfM233BGP8806KaeDcYJXQH5SUYjI/wrZ26nKaPlbrfCxxBlwXZ2CMOvAG/kYwc4/+vFEkzN5dtJNscgMACMntwCc1yaXdzbczXXaTtLEeuDU0agqTsJ/4CcfzrW/u3RSWuo7kDaSFx7VMNgXnn6Hp+lZN6bm3U0vs90Ix5sbc8DzCc/h/nvVWONlIMojAzj525/xrjbinpudCTZNKyylSs0ScYKgn+ppIy0aZWbDdDmZefpzmsLaa3Om6b3Kcx3sGAOfQszflx/WmYlQHa0ox7EVvFJKzMG3e6GAyMRlio6ZYnH61HvAXBf6DYDW1lcx16hww5Iz7gD+tQFOhBBPsa1jJoyaTQ3aR/Fip92OGkGParm1YmN0xWxsGCuP97/69R4UH73865+jNXa41lwc/L9c0gCn+ICtlaxk73HFBjJccelRkD+Ek/UVSs+gnp1DP1/KnAsB14+lU4oV2BbHTH1FNy2ev50JA2SIzA/JnPoKk8yVcYUjPtWbjd6mibWwpeRwMg8dOKiPbp+RoSsNtsaJHB7GneZuOGANHs1uL2j2LizIBgQrjry//ANeoVlCtu8uPrkDGax5bO5tzK2iLUkwkZmeJELdNqgL+WDVMMFOcsCPStYxsYOV2IZE/uknvmo9654WqtJkcyGbhnoKerYPBAz6YNU0upN+xN8gUEvz02gHP8qiaQMMZPHTmkk2irpEBPJ5zTsNtyQcdjiukwEXBPPH4VYXbuG4tx1wcVE9BxJ5gFkyqlRgcbge3tUJBU5ypI9BmuON2jpdh5PzcgEdvlC1ciCFHzCXPUDccD8hWMtEWtWRIs6RCZo2EWeDjjv8A/Xp2/wAw/u8qByeTgUpK7v2Gm0vUhkLopEm8FsEcnGOff3qcuotlQIFI5378/wBabTcdNhJ2epPCblkAjEhRScHbkZPfk4Bq5ZFoyfMm2qrZ8mQfu39cgnjr6GuaVlsjRXKWqSM10zAxRhwPkhfKjj2rJEs4AAlkAHQBjXZQ0hqc9R+8VM0ua9w80eDxjH5U7DE4Ctk+lSMtQ7FlQOJBhucdfw967CC1vFYpp41dpYiS8axMNvpkKePmBya82o9enzPTgtOpganNcyyIt3B5Uka7NrO7MoBPBDMSOc8cVlIYtoDRuWyckOACOMdvr/nrtCNo2RzzleV2XRb3L48iKRlYnaqkuwx2IH09B0qnIjKx3iTdn+IYNNW36lO/yI9+BggHP971oVkwQyg574OR+taHOX4nBQDJB4GBEMEfX1zjt/KnT26wfLNI/mY5TYVKn3yBXJLR7GqM7aMZ5x6mnrGGbH65wP1rduw0h4A7Acdct/8AXpp45Dfz4rO5pY2Ij/o+DJAwx/HIwIHoBn156U4xMhWRry3jLYIWNyff+Hp/OuV76o6FtuiGSR32tNPvI4+Zyx/EHP8AKqpkO7hgzHAHBrK3ZGzfdkRVuMqrZHU8A0oTcpOxQfr/AImt427mFm3sPCFRuCxr2+/gn9aiZ2AwW4/2SDWas2XrFFcDuD+tOLDOcYHpmujToc4u445LAexpRvY7RyfX/wCvTa7hcRRk8yBB+NIc55JGe+cZrPfYvZDyNqjL9fRwf60xnOfv9OnJouh2stxcE87wc/7dNOwEEZH+frVc3QixIm1idzuPcDP9ai7cZP1pvTSwDSSOAKYM+lbdDBj9jEZ2nFPwFP3cH0JpNotLuKBu6K3viozjOB+tR1Lew4KvcD8DQcDAXNVdt2JsrD8DHLH8f/11IG6ABGA7FetZs0Q4SgDBijPYdc/oaqkKSefwqosyaJCNoGRtPuP/AK1R5B4FXe4mrDNvfJ/Kjb7frWxkH1zSAE/xfh1pIBpFJmtCB4OCCCOPUZpvfFQ0UTqwHJUMMdCTTCYySdpHsDxWVmaXXUOAPb/PvUkbKGBbaR0w2cD8qmzuxXLjMGUmNURSOeGI/WogVIBkZRg9o+v8q5NbWZ0aEUmQg2urAd1XBH1OKtbmeEgyqSefmHP4HHH51VrR1QddGS2yy+WHjhlkGeSqHH51eRoGyjXk0MY5BMIwx+gPHp3/AArjmtW0r/M2i2kr6GJc7POJWdpc8lmBBJqrn/ar1afwq6OKVr6MjB9qUe/6V6BxkmMjhTimY+lBRdhzGVlV4i3PyuufzBGO/wClaLxO8RnL24Rix2ecu4f8BBGOvAwPpXnzaTsdcEzIkK7+HVhgcquO1W7a+ltElWLy8SrtYmNWbHIOCRleD2xXRy3VnsQpcruidLh5PNBujEjAsVGUVjxkAKCP5Dj8Ky8ejisYwUehrKcpLVgCc4yvPsKlUkHPydepNatnOaMEdvIWM0yxHA2KvOTkDv04yc5qG4Fsj/ubjzVxgnYQT+Z6f5wK403zWsa9CjuyBncadhscKwHqRW7GtSwhlVMhpADwfl4NIzFnH74Y6biDU2uXd2IUZkcFZPxA/wAavSFd2d3mE95FUH8ec1Et0XHZorH7uMofpj/GpsvkfNEucdgcfhiud28/xN1fpYe6hSA00bqDj5FHI9aqMMn5EZh6kf4VUV2VgltrqNwxHK4+gppjcJkNkD0IOK3bS3MLNibGADkrjOMZGfyqTzHP8bDjFD1Yk2hVkYfL5j4znj+fWnlpSMvJMFHrn/GstN7Gl5bJkbFSP9ZIf94f/XpTnH+tHTuaTt1QLyYxtyjPmDB9GH8s0zcT95s+xNaXTVzN3Q4OOfu49O/8qQDodjEfWlqkGjJB/soOPUioiXHQ8ezUuupbemg07s5YGnBlxyK3d+himuoFVPI/9CpcYxkj8xWDNbLcfkKcqGP/AAEUokAGCFycc4IxRZvVBzW0Agv91F9cgE/0oLndyo44wPl/lQ9eo9tUiUT7Wy4ckdD5mMUpfzDuUNGB/tZ5/SlyPdl8/RDUBlYhiCcfxMF/WopIwjlSUYjrsOR+eK1T6GDVxm0dBhfqabkY+9mtE3cgaTnuaYAPX86vzIF4HUZ+hp7FeNpYe3Bod+glYi6d6bkdzWpmO696kX7pJ5x71LZQYZxhccdgP/rUpVsDKAe5yM1nzLuVZsGJAxg4phBA5YfSkr7jY3aB/F+GKsKUPylyAPViB/Kh3ewKy3GFkB2qcdi2eDTmfqN2f8+9Z2bKvYZ5hyCTuI7nmrEcrRfNGzbs5BDEYqZQVtBqWpHLcS3GDcSyybRhdz5wPxqvvI/jb866IxUVZGUm29RlLiuw5w6f/rp6lQwLAlc8gHBxUjNuyuLUSf6YZ3Bxyqox47fNn2rRll0m5mkIju4vMIOV2HbzzhQgB/Na82cZ30t+J6UJU7Wd7/I54xRvJL5c2EXlPMXaX5x0GQDjnk44PPrWGGYfMFye+cCutN7WONpbluGJ7hzGjRZHd2VAefVsVVwM8kAUlLWxTi7XHoVBztyBz0/+vUO7ArQyL2+DyVBHz55bacj/AMex+lWjfQpCYobOHJ/5aPlnH07fpXG1OTtsappFN7yaTglQMYwqADH4D2quCe4/pWygkPmbJVeMZ3KM9uTxT45JFdXTeCOjBjkVNr7l37G1Pb6jboJHFwsZ4BEmR+lZZdkYGeWRgeqrJzj64rkio7JHS+ZK7A3YChY0A25wWUMT+lQG4nkJO45JzwoH8q1VJXuxOq7WQh3gfOAPc9aCy7iC+R0yqgZpcq9SG31GAox+Y49zk5pN0YAwH/P/AOtTSktEJuI7zDxsLgjvnNM3NyeDnj5hmhRXUTk+gqMo++qH65/pTv3f0P8Avf8A1qtp3BNW1FfcPuDjrjfmmKXbomfzotfVhdp6DiZO+wdugFSbpI0A3REdeik1DUUtWV7zZGGJyT5f1wKsBo8dAT1OB2/Kud66Jmqfew1XQ4UbEBPJKg4/M1HuCdJc/RapKXYm69BhOSf3g/EGmDJPDL+PFbpJGTd+pKw2kByv1XB/lSOiIfvhs9MAf5FNS7FWXUaoOT3+gzUrSDYFKOPxNRa+wLTcZu2kH5vxXpT/ADwVwQufXBzWfJ9otTtoW3lKkESiQqNoJG4Y+hFMWdgP9ZGP+2Qz+ePes1bqbNvuO3sqlknB4xt5HXr1FVDjbk7c85O4e3bFbo5WNIOP4f8AvqmFQOuK3TM2MICnG4H6Cm554P6VstUZMXoeq/iDQfp+QqVqBHRWxmPGM85x7VNhCTtLqD0yM/rWbvsWrEjrGnSQk47oOfzNQFRjhs8f3cVjHXdGjVhpXB5wPzpMAdHH4Zra6RFibB2g7v1qFiT3P4VOhQmOc5/IU4h+coePUVZAgZgeMDHsKk80nrs/75FQ431KTI956AKc/wCzUe//AGR+tUlYVxM0cV0HOOxTuDgZH5UwLZtzuG1llXOPlPJ9sHnv6VrWOnPKd7CUx/xPAnmOnodoYd8Dn1rjnUSWp2Qptswtj+YY2wpGQd/GKmEMpjkMa+ZGmGd0XIUZwCT2GTjn2oTStYzs2R/Z5TglCAV3AtwCM4zz78UnkkZ3Oi/jn+VauS2Js7EeOvOfoKeXyAMAY74A/kKmxOw8SKFC+Umf72Tn+dW0jSS3Jjt5zIDzJuGwfUY/XNQ21rcpald0KYDFORn5XDfyzUPbp+NO9y0SpGrYDzBATycZx+VPiS2bd500qYHy7Yw2T6feGKL9EirK17liK3tmR2e72EfcXy8sx/PA/OtKWwZAGadog6hlN3H5ZYeq8nI9645z6OJ0Qiv5jEdGjlx5ydfvI3FWdzIxEjyujHsxAb3yaG4taL7wV09/uKsgVGKlU47q2aavlsDuVhgZyFz/AFq1z8un+RL5b6/5gBHgkMnHZgeacWTGOFGP4B/U1UmyVZABHtyznPbnNMYx/wAG73yoqVzX0RT5bDsxbOGl3/Tj+dCOgHziRj/vAD+RqrSJvEbw3t9BTVK56MfxxRZibQbuOoHtzR+B/AYo5R3F2MDyjZ68ik5/vKDnoBTunsKzRL+8ZcDysep2g/rTJNwOGMZI/u4/mKSt3Zbv5ERY5JCqPYU8Mw55Aq7eZlfsgJ3D7wPsTS4PTCevBzWey1Ze4p3RsDgj0K8Zpmc84Y596tWZLuhQyg/Mhwac3ltjYp/Oi0lqth3i9GNIToFYH3IoQrn5y5Ge1Oza8xaIlWHzN3lsOBk72Vfyyeai8vrkrwM8OKu9iLXGYUdcj8KQYJ70+uwhc+xFAYZ53Ae1PViELDPBJHqVpOp/+tRsIQkUnX1J+tWSH1FO+XuGFJ3HoKSpGAxA96cATwCCKzbtuX6EZBHWm5Pqa0Rm9xBuzxUrSSMPnZj9TVOKbuNMl8890X8EUf0qHk5JTj1rFw1vcrm6FhWRU+V3B9MY/rVg+Uy5O/d7Jn9c1jLm6GisVZOAOSR3yec/TNRZX1H5VvHbUzZFRXWc4o696Xkcg4/GgA79e9XZoBG6fvVKOAQ25SQPcAnH061izRalYGMIwKkv2YNx+WP61Fn/ACKoCZ5ZJceY7vgYG45x2/kBTFUE8sqj1NJ6IFqOYxiT5dzL9MH+tSCVFLbIsg9NzElfyxUO72DQVbmZGDLI6lehDHioXkeQ5kcsfU81CgkNu43ipABjO8A/jWjGhv1B/E08ZA+4G9+TU3aKFViTgkLnuAMio8rzkE+hzQxFjzOQyKkZUdQOp/E05pUdt0g3HPIRAn9P6Vzyjf1NlKy8iONJDllhLjp0JFRgkk44q/mTr2AyHoT+lJkA8An2Iq7dhX7iBgDkqD9c1Ism0Y2KfwpOLfUFJLoO89tuAAp/vAnNOM25ssXJ4yS2TWHs+5r7RlfdzkFqkaRmPLnn1Oa0UbbonmfRi+Y5J+7x6IP8KcGIOSyH2K//AFqycY3RSlKxBgdcincY4c5+laNWVrEJ63E+Xn5mz9KmRgQVLRqPcGnK6Q4tJjDtHIKk+gzSBghyVDexNZ35kPRMAUzkg/gcVIpi3DJYDPYbuPzFVaQk4gZVbAZM4/2jTCyA5Ve3c5/pWSjJGkpReyJGZ+CxVgRwAR/SkUGRsAEnGcU1Gy0E23uT4nPSEtu6HZnNKp+UrNbynIym1toB9cYOelVa+zG7roVGKEco4Pck5/pUY2e59ulb6nM7EpaPaNiOG7ksCPyxUTNls4H/AHzimk+o210GcU4bTxkir2Mx+049eezA1CeO1PcBQfakqxDwVwOefQjikyM9v1rLW4xw56BfqTTevVf1palDwXBPBOeooxg8h/woXkA0tyfmb6mkzn+I/lR0AQqfUfnRtIPOPzq7pk2Y/aOpAOOoBoPl8nBHpzSbfQpWGce/40ce1WiBmKXn0rRmYZoz7UgHrtJ+dio9QM0+KUwvvQITgj50DD8iMVL10KWmpJJDMiJLJE6pLkoxXAb1xUBGMHBGeme9JNFNMlLQ+SoEb+bk7mLjaR2wMcfnSCVAHHkodwwMk/L7jn+dGoJogz7UVRA8DJxx+JxT2YAbdq5B6jP+OKTGhgPoKdkgg4A+oqGWN3YOQefYYqb7TN5Ri82Ty2O4puOCfXFK1wuRA/7ANBOOCoBFKz6Md/IMqR3z6YqUFAoIVWPpk1m+ZGisRHJ6gD8KcuwA7gxPbHGK1tpoQvMAy45UD6f/AK6l3xlxu3EDsqhc1k+boUrWGhmGSgA9zjikd33nexJPX5s1KSvruW27abEe4HtzSgrzkH2xWlnYz0EyOmD+dIQR1Uj60X7jsugrSSOcsxJ9SablhS9nFaoXM2Sb93UAfQCm/LnoSPyp6oLoMjsp/E0oKfxKfwOKTTYaDfkHXP4U7MeeFb8W/wDrUncPdQ792R/HnPTjGPrSKqNnLhMDODnmi8tbl2iyVo41wQ+8dxggiomwfuxgY9Dms+aXXQdkvMMx5+42MdN3f8qUiM8jcDnpj+tae8T7o5kjwCJc+2Dn/CrSz3EimA3UgjfqHc7T9RStf4kPbZiiO44iSbcJDtCI+7dz6Con82FzuPIOOOP04qLx9B2aKu5+m4/nSgtg9T+Fb8qWplzMbuJ68fhSBsHqPxFMVxCck8A/TikpxQmFNrQkdwTyT9acwUdGz+FQ3YaG/RqTHGcimhijjqB+NHFTZAP5zhmYc85FKAcH5iKgocBKed3T1bFISxPP8+KLIbuOw3BAOR6UEuDlh97nlaOu4DQHIJVcgdcCodx9B+VafMgbRmugyHEk9/0pwA29859KkBMf7NPDkAAKoI796TV9CkxjEsSSeT7UgOKErIG7llZVETIYEZm6SEtlee3OPzHeneSRGHeSJQ3IG4E/kMkfjWTdmXa6K35VNJE0e3cUO5dw2uG498Hg+xqrkDjCVlCSSRrkA7t24DjP8OaayKv3Zkf6A/1FRfUZDyerE1KIyejIcDPJx/Om7IpK5Lsxgs0X0B/wpCyAbkwDnoQCP1rFvsbW7gZUZcOrFv727+lRArtAC856nNCUkDaZZdk28GMew3f1qujopyUD8dGzx+Rpq4nYeskS9Yt344ApN8QwQjE9+RipUZ9GXzQ6okeaN8bYVi91JJ/U1XY7mJLE5PU0knH4ncbalsrDeAcjn6ilDDvn8q2d7aGGlxd56ZOPagvk5PJ9Sc0mmVcbu46Cp4RMxIgDsSDnb6d6hxVtQT7DS7qCrADnPKjP+NN38nofwqElJXTLba0Y4bMfMOc9m/8ArUuI+cMRjt1z+lQ7u9i0l1FLq4UEvgDA3PkD9KHSNQMTBz6Kp4/Oq95bIXuvdkQ2AfeOfpUm0H/lqn5Hj9Ktt9iEl3I+O+DmrUn2dVXymct3DRgf+zGk3LdD93qVi+cnYufXFODtgAFBjnoKfJ3YubshS5d/mZO/IXA/QUAqc/ISccfNwP0p2tsO99xro0ZG9CuRkZBGR61Fx3zW5iJigFh0/SlZMV7E3nyFdu4AegAGaaJPkI8tST/Ec5H61kqaTbNOdvcQu57AfQYphJJyetapWIbFwOMA5703FWQGDTirKcHIz2NGg9RuDQevanYQ/IxwgzUfHpUq5Q4EDoDn60vy9wc0mmCLKmJSmXYYPIKZGPz5qDCk9cdelY63NNLAyk424PHbP9airZakMlKbSN4dARkcUgbaOOazavcewokIGAzAelRZ96aiK4flRiuoxEp3JpAJ+NAyTgDNAD1YA8orfXNSxztH90KPwyPy6Gs2rmmw3z5TF5RdjGDnZk4z9KhoSsDdwx60vHpTJHckDOMe1WpIwsYdCrIxwCSA2cc/Lk8c9azejGVNxHTigknliTWnUBAcdgfrQCfQUrAh3zD2/GpUUNndKqfXPP5CkykIpCvnaJAOxzg09pt2R5UY9MDpWLje2tjVStfqV888AflT8EjkKPxrTbqZ7h8o6kH6ZpMjpj8am9x7Bn3p+Y9owhLdyW4P4Yo16Bp1G/fOOBn8Kcyqp4ywPTkU9g31HNzj5FSozz1cnFY31tuaNadhuB68UnHsa2WxkTRwvLnaUGOu5wv8zSeU2Ccrx/tCo50nZlqDauIVUAev1phTHUj8CDTU0DiM2jPWnbevI/OtHJEWY5ULdKm8iXONhNQ5xi7MtQk1dEOQOq0442j5QPfnmn6EifIc5yPoP/r0qIjvgyKg9WB/pmi76oqy6Msr9phXCmRVPpkA0j/aUQGTzQjZALZwfWs7QLvNIiEqdGiB9wef603zEwP3Y/M1pZmd0SCZVYFYgMe55/WmtK7DBZsemSRWfLd3Y+a2xB+f40oJHQkVukZXF45JP4UygBPwpeaoQoYgEYHPtSHHY1NihePcGpBIcY2qw9x/Wla472G7h0wRn0NISpxyffNCuGhJtiyf3p25/u800qu7hlI9xijmfYLeYmSmQMHP40BiOQwz6YqWrq4eQ7dkYyv/AHzTQxHQ/lSsMcSMDlST161DxVq4mNzS5rcyFzxjOBScUgFAJ6CtCewuraNJJ4HjRxlGI4Yex79azlKMbXe5pGLlexn4qUxsqKzYAboMjP5dRWjZG5Fx60oI75P0pCEyPSn7vbtxk9KQxvHOTj6Ck4qeowzT9jYBKnB74phYX5MdTn02/wD16fuXYcMc9hsH86htlaDRNIEKCRgrclQeD+FRk00guGT6UA+1UIX8akyGyXdicccZ/rUMaEdkJ+RSBjuc0zj1o16g7dBKKokXc2MZOPSkyRUqKLbAkk5JJ+tJmrtbYlu+4u4YxtB96XdxwoHuKzaKTJmd5BmSUkjAAYk8dKgxnvQkkNu4UnFWQHFLQA3mihJBcWkpWC5ICDgFBx1OetIV9Mfnmp2epW6EwR1NW47kxhgkajcNpIZhn8jWcoKWhSdhskqOFxAseBglWPPuck81CAG6YH41orrcl2YbB3dRTCMdKd7sLByaXjvmgkTjtRViHYGOSPpTePSpTuirC5I6UmTz0OaokdtY84NTGKRIwXhIB5DEHpUNruWk30IQRjkH86AQDkfqM09SR/3m42Ant0oJGwDy1yOrAnn9ah32uWgZoio2o4Pf5sj+VND4zwD9RTs3uK6RKrR45QZ9STQrorZVT34ODWaU0ty7xHy3LyYDlmC9AWJAHtVXd7itIqxLdyOnhSckA8dcdq6TLd2Q0+wo/CgQfMeOaXax9eKz0NEmNoqyBaWgQn4UfhQMKUUgLEgiG3yndvl+bcoXB9uTkVBmp3AduJGMAfhSYFCKE49KOtUSSBFIyXA9sU+QRBv3LOVx/GMHP51k272NLKwxlCgESKx9Bn/Co800JqwoJHSjce5qbDuOO3AOTuPUYwBTelUhMXd9PypuTmhIBfqaXjuKbEKCFYEgN7HoafJLvctsVAT91RwPaoauWnZERJY5JJNJz2rQgXnvRkelSAmR6UfjQxj8rjBX8qcAG6DH1bFRqilZiMpX/wCsc1Hg04u6JasG33FOVVP3nA/CqbsNIb+FJVIgSjFMBfwpfpSATJ9TSUrDFoqyQ+opMj0pDFxSYpiDFLyO5pWRVxxZm+8SfrSlSuMkYPoQaWi0HqOZFHKvn2IwaYCVOQeala6NA/IlV13EuBzznGf0zTWZT0XHrU2a2KuhgA9AfrTmwSDgD2FaXJGkDHBzTcU9yRtL9KsQvJ6mkBIOQcGkBN50vlmPzG2E7iueCfXFOaB0jjkYptkyRhwSMHHIByPxqNEaXbNAXVqLXyWsIi+D+/WRw+e3U7f/AB3p+dZIYDPGalJq+oNp20F3krt6D0AoVgDyoP1q7EibvQCk3ZqiRcmnb+mFAx+tSwJ5rl55Gd1iBbrsiVB+AAAH4VVJyc8VCjY0buL164qZVRjjdt/2m6fkM1TdiUMdQrEBw49Vzg/nTOae4icxrgfvU5GTweP0qNlA6OrfTNY82uxpyre5HTtzeuPpWm5AhZmOWYk+pop2sNu4Z9qcCuec49qQhxZeNikcc55zTdzYxUWutTS6T0G0laGYc0UgHAgdQDSsQSSAB7DtU63K6DKKokKKYClhjAUZ9aQsT6fgKmw7icipQ6jGUBweevNO3YLgzBjlUCewzTcAdaUU0tWOTTegcd81LsQgnzR9MHNNuwkiHB9aORVEjgM9WA+tN/GlfWw7BSUCDmk5qgFopiEpaAE69qKBjwpPTH50mPU0rq9hjtpwCOh7mpZoHgfY+0nGco4cfmCRWbkk0mUou1yuRjqMUuSBjj8q03IEp4JA6UmMaTSZpoBv4UZqhBRQAc0UCFCkjNJSGFGaAClzTExce4pMUgDHvRQAZ9hRk0gF5FJmgYUlMAp2fWpAWkoAlWV4jmNtpzkEdR+NQ5PrUcqvcu7tYUU6qJDNJnNIB3Tqf1plCdxtWCjFUSH1ooAOaX8aAE4pc564oAMUYoACpFG01N0VZiYPej8KtCHBiO5FGSe9ZtdR3Ac9SB70HAPDA0X1ATNJmqELSc0wFweuKTFMQdOwoz7UgFz7YpKaASigApxJNKxVx3zHv+tLhzzyfep0Qasj5oz7VYgzS5pgNJLEkkkmkpiDijJoFYKKAJnkkkxvkZsDAyc4FR/jStYd7i5GDkHP1o4oEGcdKGbcxJxyc8DFIBtHXtTAKKAF/CjNACZo4pDFGO+aepQH5lJ/Gk79Bq3Ubx6GngJ3LD8M1N2UrDSF4wTn6UnFMliUYFUIOKSkMMUUxBinUAJiipGLmigA3UlACUUxC04HByVB+tSykWBOMAGGM469ef1qF2DNkIE9hnj8651CSd7m7kmtiOlz711nMP8AMwuNi59SOajJzzWdtbl30sJikxWpAUtADsD1pKQCZNGaQxaKZIUUDDNFMA/AU7I9Dn61Lv0GhAMnA/WlZSuM45GeDSbV7D6DaWrJCimAzFLj3pgJipzCwVGyuHzj5xn8R2/GkAksLQvscqTgH5WDDkZ6ioaSd1dDtYKMVQC0maRIufajigYuQKszXDztucRj2SNUH5ACoauNXKtLVksXHuKcVwPvD6VNyrDQpPQZo6dqYhKOKACigAo4pDF49TRikAbaSmIWjFACUnNAxaXNAgzSUgF4o/CmMKfhdvU59MVIxlP8pyhfa20cE44ovbcEm9iLFGDViF5ooAPrTsjsKlgJmgYzyDj2qhB8vqaCB2JqbjEoqgDPtSUCFxRQAUUhjtvGabikncYUtWISikBajnaNwwCMRwA6hh+Rqv3qUtblX0CkrQgZS8UDHAgEZGfY1Mohx8zODjsM1nK9tCla+pBQSfQflWhA3mlxQMWk4oJCkpFBS4pgXIbSe4R3iidkTG98fKvpk9B0qIxOqhjjB9CDWTkk7DSbIcUlWSLk0uKQxKXOaYCZozQIKKAF4oz7UgCjgdKBi/jRjnG4fWobKJCmOjKfcGmlTnGVP0NQpplOImxgenT05pGVlJDAgjgg1qmmZtNCUUxBxRmgAyaKBhSdKAFz61MDFt5Vi3ru4/lUO/QpW6lvbbbdoZt56Nu+Ufhiop4BCwCzRSgjO6M/4gVhGcr+8jdxjb3WUyCOoptdZzBS0xBSUrDFzTg5A7flQ1cBpbJozQIWjcRTAdvOCOPyplQkU2FOzVEliIQlgJWkQeqqG/TIqvUa3L0sHFFWSJRVALS5+lICKiqAKKQwp6kAgkZHpQIekhjkV1CkqcgMAw/EHg1K1w7QLCVjCqcgiNQx+rYyaxcb2uVexUpa2JCjFIAxS0CDPvSZpDQ7NHSgRJ5h2FMLg/7Iz+fWouO9TYocSuOF/M02hX6gwpaokSigYUYoELRSASjFMYUnFJjHUuamwDaWmIXFJ9aYg4pM0wEpaBhRSAKKYBmijYQUu44x2oASimMM0UEhSd6BhTqADFJigApKYC0tIYlLmgBwGaCCME96LgN4opgf/9kAQVNDSUkAAAAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAAAgACAQIAAQAAAAEAAAABAAIAAQACAAAABFI5OAAAAgAHAAAABDAxMDAAAAAAAAEAAAABAAAABAICAAAAAAAA/9sAQwAJBgcIBwYJCAcICgoJCw0WDw0MDA0bFBUQFiAdIiIgHR8fJCg0LCQmMScfHy09LTE1Nzo6OiMrP0Q/OEM0OTo3/9sAQwEKCgoNDA0aDw8aNyUfJTc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3Nzc3/8AAEQgCLAV4AwEiAAIRAQMRAf/EABwAAAIDAQEBAQAAAAAAAAAAAAABAgMEBQYHCP/EAEwQAAEDAgQFAgQEBAQFAwIBDQEAAgMEEQUSITEGE0FRYSJxFDKBkQcjQqEVUrHBM2Jy0RYkQ+HwNILxU5IlY6KywhcmNURkc3Sj0v/EABkBAAMBAQEAAAAAAAAAAAAAAAABAgMEBf/EADQRAAICAQMCAwcDBQEBAQEBAAABAhEDEiExBEETIlEyYXGBkaGxFNHwBSNCweFS8SRiM//aAAwDAQACEQMRAD8A+MbpXTHZHRZDDuj6o900CC90ggI7IGM3SCf1SQA00b3S+qBgEDqiyNkgA9U9tkbo23QABO10IugYtTdCflCBAB1QjdGyBggoQkML9EAlMDRJABt/2QhSOyAF0QgFNABpZF7oQkMY2SG6aEAIoCaEABRbRARtsgAHVPb2SGuiNUDWw/ZI9UwgBIOQ21sn0Sy27o1sgpAj+yl9EiEBQDdHlCEAH0R909r2KEDQumyY20COqNkhh7JG4RqmgQkDwEI3FgmILp9NEZUkig1TQPKY8oAQR7o0TtogBXKAeyOtkeyADRB2RZG97oAOiEAaICAQvonZBv1Str1QA9tkX+qEwgBW3QPZNJAUGqAkD7pg32QCYu900IsgYd0gpJE3QDAbIui1tUAIAPdB7pjc90roEJPwQgiyANUAg9tkbeyaRNygGIdU9kIA3QAbhF9ExsUggKDqn7o0tZA0QMXRF7otdFtNSgA2QnrbRHRACRpqgkpoBC6I2RbdCADS+yN9ghAKAQbbI1CYRpdAULqmi4+yAgYeySaSCQJRohCAGlone6XsgYHe4R0TujZAC790Cye6XdABfoChNLrugAQhCABJMXQdECQrd0xqhIIAEBPdB0TALaqJ3TBQgAGyBruhPVAC+iXsmkUAFkXR1QECDTsjVCD5QIQ6o8IG3hCYCKNk7IQLuJHhCEAHRHXZBR9UAHhJNCAEEFCExCGl0zsjVJAgQE0jsgAST6ICYgAuCkNEx1QkMEuidrFIpgCY0QEkAI6po3SKBB3R3QE+6BCSBTSQA9e6EaIsgYd0bC6EX0QMQ3TSKECH0UU0JiBCVkIAfndGyaECADQo8IQgQBCAj3SGhjS6QGmyfRFtd0CGlbVHdCBjCCEDwlYoAEboGu6fdAxDZHQpoQAeyBsmhAxe26LWRbwn0SExNG907IsLbIQPsFtEWsltdSGoQArJpAFPogaEeqYHlBCEAGqBqhACAFeykAkQmEgQEaoT+iQQMOidroCEgEEwkLhNAB1QEEKTUDSEgIt1QgfA/qgJJ3skAuqlokn0QNEdU7oF0EaIGCEd0dEAHdG6DsiyBCsnZNIIAEd0J7bBA0LSyLXGqdkkABCAnsUkAPvco90XRZAB7JItZMDpbVAxJhCNt0ACAgIIQAEao1CEDdIASsCEDZNMBW0TItsgbbpbhAgT1sgBH0QNC1vujqmlqgBnZIJ7jVHjZAxEIumjpsgQblCEDqgaC10timkbkoExoCLI2FkAF0AIO2lkBAD8oA+yBsgJDEEd0aoTAAjdA87p7IAj3T6WTtui2mqAQrIsmkUAG6EWuiyAC1whARZABZB06osgjUoAQsmdtEWQAgQBKye5TQFCG2qX9E97p2ugCI0T90fRCBisnYIQLIEKyLdEx1TA+yAoD4sl9EFFuyABHui2mqSAHYXSPYJ2uiwQPsJFtEWQEEhZGiYskQgARuEtkIAZCVtCbo6bIsbJiYWHdHdGXdGvVACR5QjugSFtdG+iOmydtLphuKwQnaySACyEa6/3QgQIshK2qACyNEd0WKACyPolZCBCsn0RZO3ZMVCt2RZFkdEDoSEboQIPqj6o8ItugAAQUBCYC8p2CAjoUhiv2SvvdA3TsmSA8I67ISQAaIuhCBBbqnayAO6fdAyPVCf0UUAMISKe+iAsSEAnVOyYhbIQEJAMap9NEITEFgg2OwRYISAB1R/RB7IQAwALpDRF9EXNkAOyNkDRAATBAhHVFkhh0QOqLfUJhIBIT+iSYDt2RsgIIQMNUgm3ZM+EgAIO6AjykAdUbIBsnugBDW+qEWT7oGCBbVLa6EAM2OyOiEaWQAICExsgACEBPqkUKyAhPRACujdFkIENMEpItdBQDe39UeED90zfdAAEWQntskCFshG6eiBhYIPYBJuyNDdAx2sEjqLob2RrsgAA0R5TB6I6oELui26Y97I0QOhDa90+qdglp3QFAnbVIJddEBwNK1kwn7IAWyEI/ogACd7A63SR3QAdEhc6p9EwgYhsg7J7bWSASABoCgaDdPZI3QNAEICe6AFp1KYSI8IBAuAmIE9ilbsnbdIBEJ9TqhJMY0tU9kIASE/CW6BIP2QLBHsmPKBoR1QNE9tEjdAgF00DZCAQk+vhHVCQw3Rbui6DugA6JDsmRqjbqgAGnRHlA3QEDBG6B17o6IEAH2QRpqmLpIGNLUIvvojdAB0QN0WsdUd0AMDQ6pbIAQUD7ANPdB2KEIEIJ7oTGiBIjumLbFFro7oDcNEIBQbIGCOiLo6IEJGqdhqjRACslqn7JpiF0QhO1kgEdDZLondG+yYB/RFk7KPVAmMeUHVAQdt0AhBFkyl4QAuqeySffRAheyLFGyYTELokndFt0AFwAkSi26aBkU0X3si2iCRITS+mqADqn3SR13QABHRLymmCENkxslshAAjVPRLRAhJWUvqlZAciRuEwR3QmAtkxqhJAgRui6NAEACVymlbTVAWBB6o6aI+qAmIAhHdCACyXVO6SAGEimDohACGiNEWQEAF7oR3RugQbI+qLXQgACEIQA7JFPTVGiYhWsnon0SQIOqZ2S2T90hoB5Qg6IQAWQOyAj2QME7JXRe3ugY0WPRCOqQB3QO1k7pd0APukNEdU0AJPVIa3TAQIQumjugJDH0RsNUgjqgENAF0iE+mqAGeyXRHSyBtoEDQh+yl0SsmBpZAANUXRshIYIHVCaACyPZIdydU0DBCAEykAbpBF0zsgAQNrIb900FIPojojTukD4QA0bosjRA6BHZNF/KQJC01T3QEaIGRITGqaQTEHQ2SUkDugBW0skApdED7oCtwS3R1TCQANtEIRsmMXdA8JoCQqDohBsjTqgoQTOl0dylvsgQwEboQgYEaI90BCYCTuhHRIASHlHhNMB7pC6EfRIA6p7JIQCBJOyLBAAkQnt1R4TAAjon3QkMSOpRbyjRAg8IQjogAypDRMIQAJ2CRTQNCtujqj3RZABqgd0dUWugBKQ7pAW0T9kAhBO17pXt5T+qBisjZPS+qN9EAha3T6JbI1KBWA21TujQpHcIAEa9UIG5BQIEWTQd9EDEjynshAC3vqjZAT6IASBshA62CBDCL6Je4QUBYW1QEdEboAE9UWSsgEGySf9Ud7IAEBFkkxD6pXT1SukAfVJPpoEbpgII6J9Lp2QKiP7IG6aSABLfdHdAHlAgCe40S6ITAN7o8FGwR3KBCuhCECCyXgp+UHXVAxfVFuiNLlJMQ/ZJNCAAHUpHqhCABJNCBCQdBujuhMQkaWumbI6IAXQJ+6LJDrZAAUJpIAAjTZH1R00TASaQQECBAQmNEAR6Iun1QgACEW3R3QAkdEICADon0Ql0QAD3QhCAGOyaBshBIrJjr4TSAQAXTHVK3VCABATHVKyAGkmOqXXZIYIKYGqLaJgA2QB1KdrGyEhi+qZ23TSQAW6IA6IAQfKABP6o0sjdIACSaEAA2Ra6ACmgEASTKBsge4AIuEapoBCQE+lv3RcBIAQACN0vomgA+qOiY+6Q2QMBfogIFipaIGhDdA0T6aIGyQ6Io8J9CmOyA5EFLola6fukUg6JDdGpTTAD4SsmjwkAk7DuUWCaASEPdCNjsg+UDFdAT2BQExALo3OiYQkUIhIDunon00QKhaXRZA3TvdAJAPKOpQLoQMSPCfRJAUMfKkUWsi+6ABGiExtsgBW0R0RsjqgQX6IRbVFrlAIEWT2/3SQMAN0IKAgB9EuiLJ+AgBWRt0QN0+6AF9EBCAgARbug6pjZAISZH1QjX2QMXfZFk0e6BISOiaN0DEAUW1TtohAhqKaBvsgYkDaylbyohAAnumkgASG+6dkdEBQAIPsgdUAIH2BAFzonYpbX1QAeEdChA8oEK6fRO2iLdEDIpgIAR7oEHRAGqPZA30KASDUHVCdrosgZFPoi1kWQISaBsUFAUI+yf7o7oH0QISYR0/uiwCBiRunshAhI7ppCyAAIHshCAAbFJMdbJJgF00gN00hBpqkb2R7poAL6JWRun3TAiQLI36p6hCBESjopEJW1QAkWQd+6fRMQaIslshACQhBQIR3Rb7oAR4umIEICaQEUwnZR2TEO2iSEttkDY9hZB1QhAhdEIui3fZABqlbdNHdMASR7FHhAgR0QgoBB7oAR0QEwFsgJ2RqgBblHSyE0ALqn1QkgAshHVFkCFtdA91IjRJAwQhCBD2QNrhH0uFJBJEabIHsn3QLFAwCLfVAtZMbIGL6aIKYHdLS+6QgCLJpWTAaAi3lMIHQIsgBG6Q0IWTsgJX7BAB7ItqjropDwgQW0tdIovqgpAO10ICNe6AD2QLoHhPb6pFIQ8p7bI9kaX3TAXdMI76oCQIeySBdHRABZCO6bfKAqwAQn1RprZIdC0QjZMIBAdUAJhLVAwT9t0e6EDEnpZCEgQI2QR4QgYINkJoAXlJSASQAJ+4QjS6BpCt2TCO6YCBpBawKQsUzsojwgGNHQpFBQAXQiw6J+EAh6JIHulrqUDGfZLpuhCBAgI6HdH0QAbJhKyEAFkbJgoJQFCTtqdUAaE3QOqBpB0RZHlA21KADUAoCf0QEgI+yYCSZITEOySEahA0A6pWTG26SBAmNkXvomBbogpAFEqRA6pW3QAAd0zsojqnYWQCBCYsi26AoPKBtdGuqR9ikCGQNUDwkgIAaWiY90a3QFEdVIW1QiyASBCEIGK2iYQi2iAoE7IHVF7IH2EGo9kdUIICyEdUIGAIQgDeyEDBFkWS6IEPqhAHdCBi3v2RtdMabJ2QFEfZPpZFrE6p20QKiPhOyEdygAS8lO5O6EBQrWKNwhO6AERpsi2m6aQTFQDZGyZ8KN+6BASjpdABsgoEh7BIIQAgYJJp7hAmJAR3QgAI8pWsn5S7pgJPZGyLoASSZQgkRStqmgakpgCQ6p6oN0AxdEkwi3lAgsg+6EkCoLao3R3S8JhQ9kkbosgAR01TSQAIQkEACE0JiEEWSCdvKBAhA6pIGA2QmEeyAEnpbRL+iNLaJiDdFgl36JoANEuqYQUgDqhAR0TAEISCAD2QhCAJdEk/pqi2lkEgNAgeE0gEAIblNMfVCLAAhA2RYIGHVA0TslZADSshPogAsQgIQgYdNUW8oCPokIXdMFNFkAAPZL2THsghAwsgboCFIe8DvcI6JtQANUwBpFkgjoiyAHumBbRIJt8/dIaAdUJ2ACSLHQJ6WRuiyQ0GiBtsml0QICUNKB1ugadEAPqbo26o6poLQkW7IClYIAiBdMfLui3lFtEhAgIASCBof1R9UCyYQMj1RsU00BW4kD3RY9wgAaoGPdARa6XhIAui1uqAncH3QAku6e5TtumJC6FHRJO4QMEI8FCBhoi2iEAiyBBbygI+iLaICgQAEIQAbnZA0N0AIOyBod1Huiydr6oC2x7qI6qXRJIGATuj2R0QAuiBZOwSTEA66o89EIKBh03R1QBfr9E+6ASAovbygeEdEhgjola/unZAC6I0KTUzomAx2TRbRL3SKEU/ZAQBugkW/VNPZFrdEDoWyEHVCADojdSdbYKA3QA9EIT2QCFsmLXSQgY0k99glYoABomlbvogFBNhqgIKLd0AO/bRHfVFkEFBRE66pgd0zp0SAPRBI+miWifRFuwQMX10SBUiNEhsgQX0R4RZBKAF7qXlIICAD2R3QiyAC6Om6PZA7oAXhATIQgAtpZIJlG6ABBKO9kiNUAHRFkDQITEJG100raIECaXhCAQaIKO6Q21QFi8Jnui+lii4TJC4soqRCWiBB7pb+6fQpW0QAXQhFrJgJCaSADrZLqn5R1QJkTvumN0WTTEI6ICY1S+iB0Fkkd0BAAgI0S6oENLVFk0wIpoQUCC6EWQgAGiB1QUDRACKPKZ1SsgGA/dHsjZCBAfZJMhACABK6Zug6JgIJpIQAIQEIES6FCaLWQAbbpgbpJhIACO6N+miPqgBICfTVHcJgF7o0RZHVADS6poH7oGGyDbdFuqNrpCAe6EDqmUDQrFHRBTSAQCaEWQMBpsENKEd0hB1TA0StomLWtqgaC5PVHRHTdCYBfwnfRK2hTASGhap2KZt0St3SGCd9EaIFigARqEdShAUG6L/ALIHVCBgCi6D2QNEAA8hS/ukEeyQ0P3CLbpKQAtdIORI90zodEv6oGkCB7I11QNBqgYdPKEDVO26AFZFtCmAjdA6EhOyXe6AA67o1snbwl1QITdEE3UtOiSAqgSsmCSghA0CNk+iWiAYG1rXS6J++iSBDR9UgnZAxFCdrhL6JiAe6Dp7JhK10DQ22T7pWQdkhoEA90dN0IAOiYHZIeU9CgBG3dLRNH0QABA62QGnUosgEL2TG2iLWRt1QADqhOySAYk0W3CEAgHlFuyEBAw+qAi3hCAGkmEW8oBCHdM9UIt9kDBAOqNLbpd0AMBI6J6W0S6IAAQndAH0R0QJBqQn0SQLIKQ/ql0unYE+UWFkhNEbo1QQQmN0yQPcp7I0SP7JFDuAi+9kkwEACXRMpd0IQfRFrFPykgBjqlqmB5SQAAXSsU0JgLyhMhAQIPYJJ7dUh7oCgAuUAWumLi6OiB0BQNAjrqgIAXsUxrqg7pBAu4I1T8lJACKEx3S7oEHRAOiB5TTAXUpEaJ7BLfqgQJfRSGiR1QIXRMbIGqLIAXVIlSCRTChG9tkr2UteqLIEIDsl0KaLIASeltUbDRIoAEgjW6LdkybBCLIQAAaKJUidEkIBAJjdCEwYkd0fVCBAEaIRfugQrICeiSYB3QUJ6IASOqAgoAEdEd0XQAkIKaAEPdGqAmNEAJBRdCBBZIJgIQIBZCEJjsn4QhFkkIN0d0CyBa6AHsknuhACQNEWTt2QAgmhAQCC2hQ0dkzsjVAwST1S90gGNAUDqhtrbp7oGIm6AEWRsgB+yVt0wjqgBW8pjW6EDRIEBS0t5QbHupb9UAJAFr2Ra6f0QAk7EIA3TtukUkK2qE0WQMN0AfdK/RPohAgPVAQdBdIeUAx7osE7WQkIQUvZL2TGl0FISeyEe6QCt1UhokOqdkAhXQUWKZGiChWTHkJfVHhAAmDpojvcpdUDQ+6YQBpZG2lkhhZBQLBCBha2hRbug/8AhRZAhHRKyYCDZMQDTqhLdFumyAD2KEdEx5QAkCyYASsgBmyV0DdGiBoDsgC2yLhF+6AEDZMe6EAboEhjyhL2TQMSARqhAQAa9UwkEWBugBoBslvohAD07pBPdB0NwgBICfQ6pdEAPQ6JkaXURdM/ZAAEbIHlH1QAIGh1R1KaCkhfVCEDdIAQna6PZAUG6XVO52S3KBgNSmbdEvYINkCGEAoCSAJd1Eap7pa2QDGB9kH2QEdEAIeE7IGyehCBpC/ol7pjUIKAa2DokUx1ul3QSMdUx3Sbp0TCChaIt0TJt9UtwgNh2u1LqgbJoAWltEuqkOqSBMDdCLX1GiOuyAC9r6I3toldF+yACyNk90IACdClqUWSuLoAfsi+6Wqe3smJB0SUt7qJQJjtdBQNN0vdAAO10JlK2iABIosn0QISXVMItYpiEgKXTVI90AJPpZI7oFvqgAQjSyNgUCBRN7qV91HumgDTVCOu6CgQW7pFPRGiAEDZCNPKLJki+iE0kAHRCBtul3CAC6EuiaYgt5SvdHugeN0BQwEu+iLoQGwISRfsgAG6fRIITECN0f0QgBe6AnZAQABHRCY0SAQQfCEbJgKyEbhCBUAS6p7oCBB9UJoQBL6JoRoEIAHVCAbIBJQAW8ITCLdkrGL6oHVNJMQ0HT3TQNd0DDfVIJ9LIskOg3RfTdK1t07EjRAABpdIjVMBHk90AHcEoPdO/dCAFbQFH7JhI+yQgQQmEzroQkNC1KQT2RfsgdAEJnyEWCADogHykLap2sgaDVA1KL+6NroGHhCaW50QADUWTAsga6IFkAFwgbJBP+iQx2KAjojykAahGifQoQMANNN0DumNUIGKyXRSS8FAAEEXQEe6Bh0RZFvqmNkAgui6BbqhIYr6fVMd0A9EAiyBoPojbqi9wgW2QAI017oP2QPKAFbVIqRulZMVANEdUrJ7IAX1QjdMIEL2T90ijXVAAi90dEAIGB2QNEIQABCCChAB0KOiAmBZAUCDojugeUAHugdkaIuEhgBZJOyOiYqEmkLWKAUAiXcJbo6p3SGhHsi3dH9EA9EDDugaDdO+mqD7IHQJddEAb3TFkCDYIv7oPsgkndABa6LIGqEAA33QjpogjRAwKLeLJfRSGqAFbskPdSKBpsgBbdUX02TGtyhAxJ9dkJdSgSDYo3QEwgBIPsjqUIABe26Y8JBSHugKF9EXQT0Ra6BhtsUBB8oHeyACyLI/ol1KAAfZHdF7XQ09wgSoLdkeeqLhJAgQmClugAue6ABdO2+qR0TAdkrJ7JaWSAPCLbpJpkgEG3RCEACSEX3QAItZNLogQJXUgdNUiEAIFB21QOyO90xIXRMfshF9EAIosi+9kaoEIpJ7osExB0QOoQdEIBCS+qYQNkCEga9U0vdMBXSUhqUigQaW8pdEx7IQDF9EdEX0QmJAB/2R5QEDXqgYG2oCWidkkACN90rJgoJBCV0JgHdG6OqOiBD6JJ3SSGCPqgJW18JgMoOyChAhIvZATFkALrqjugoQINihA8oQBaO6WnRNFkDADVBTsLJdwgBo9kDRCkaBLupCyEwI/RMCyE/CLEBGiWoTARZKyg0P0S22TF+qOiaYALWRZMBBtbdAURTGyYFwgaJCoQ3QnrukhAGtkDyndFkhpAQUAIt5TQMRRrqj3TGoQAe6LJbJ9N0DQvBTCEuu6BBvogeE/dMaJDoQR5Rsi90xh+6YCBa2iNkgHZIbqTGPefSCSey62F4NLVuJIGRur5HHKxn+p2ymUlFWyoxcuDnUtO+okyRi58Bb4sPY52QNc4nTzddmlo6GSr+Bw2V9VUAeudgyRstvl6n3UMKwpldXGH+Jxw5Wl2d7SAbeVzzzbPsdEMTRlZwtUVMJlw6ZlRYXLAbOHiy4MsUkMjo543Rvbu1wsQvq1LguG1OGQVOHvlpq1rcjp4SQS4b5ht/8rgY/TtpZIoMfhbUiS5jqYjleB1v3XPg6zVJxe/5OrJ0kXG1s/seFsjou8/AG1Lc+D1kdTcn8l/okH0Oh+i489PNTSGKpjfFI0/K8WXdHJGXBxSxSjyUp90WTVGZGyLpo02QME7JWCL6WKBoB1TRY30SF7aoAY03R3SsUIAB3RtqmEWQMSD1smRuooEwF0zqTZDUC1kBQrIHVO9/ZRTEOyXumjSyAC10WSvfZAKADwhGyAgACduqVkA7oGB7IF00fRAqEjoi1k7IBB01S+ifRA16oKAaITtokgTVAOqYskgpAhoNwlqmgYunlLqn0QEwDoj6p2GqQ3QAxt4QACUk0hoNVI7aKPRA2QAWRbdA2QBugAsU7FLqnfTdA0JNvZA12S12QADdA1TCECAJ2SuQCmkUg8pXRuhMAsiyASi+p1QISOiaYvrZAEfoi6YCfRAhICSlfRA0Jw6oGmyetkkAHRFtUeyNtkAIjsgaI6I06IECLFLYapg6aoEFrXS6J9PKLIHQII0vdGyECBBCAjZAxWR51R1KeqZIkHun1uUG9kgI2RqFJI+xTFQdErHpqp5Sb20XQgjbDTZntDH7gvBu4Ht4UylRUY3yczogBdF8DZ4XPBYCwdDq76LBYgag+6alZLVMjbykn0KExCsjogoTEHRJPdI7oANbaICAgFAhIsmopiC10rG+ikPCCgVEdkJ/VH9kARQmi2iYqEUBB3QPKADTol3Tsge6AFr3R3R1TAvumAtuiEaIQIEvKaAgBAa7IsjwjZAhFPoj6pX7oABunZK3/AMo9kwC2iAO6OiECof8AVIIRskADqkUICYw3QdQjwjpoUCADyhF0IDZF3VNACL2SKC3hK1immjcVISVlIaIQMjlPZCkgaIFQh7I11UjcI6bIBIQQRdO2hR0SKFsE7EoshACt4T8I7pAapAO2qAPsmEkwD6JWJ9lLokECCyE7oSKQFLxsnfRAN+qAEAjoUzsUAixugEKxRsLJ9EfVACCLdlK2m6Q0SChAWT90HfVA2sgYd7pAEXUuikxhebAJhRGxH1WmjoZaqRrIo3Pc42a1rbkrtcP8OTYpMGtDgxvqe8DUDwF1KzD8bgPwOH0X8PpHD1TXBdIP8z/7Cy5554p6U9zpx9O5bs5xpsPwZoGIyCeqt/6Ondsf87/7DVTMeIYvG0V8nwWHx6tp422A9m9/JWmLDqDAImz10gE5F25hd7v9Leg8lXU+Iyy0NRiVRGIaCCwbG0+qZ5+UE9upsudzct4/X9jrUIw2l9P3Impw3h+icxueWsn3iabFjOgcfO+iy8NvbLiTjMbxiJ73NAvYAXK4DTPiNa6R15J5XFziV7L8PADxCYnsY5r4HsdYdClmgoQb5dEY5ty24OrwzWump3YxLlbSy1BhcwN1jA0a7t4K5lTOzHavFcFqHZp2TOkpJTrt0uvU8NUIpuHoaCeENHrD/TbNdx186L51jkDqDFJKqhkP5Eti5u+h0v8A0XJg0zyy0/I7JuUYb/M4rjPTSvjlzNkY6xB3BC6tNj8r4hDiEUVbANMkwuR7O3C38SUkeK4XDxBQM1IDKtjR8rv5l5Qey9KOnLG2tzz5asUqT2O4/DcMrhnw+c0sh/6M5zN+jrf1XOxDC6vDz/zERDOjxq0/Vei4EwaDG34hTVBcCynL4iDazvPhdThLC5a2lrXfxB9PBE1psWiRhOt7tPgLGXUeE2m+PU0WKOSN1TPngF9kjv5XrsbwuhppWNrqfkc1uaKqpDeOT3af7LkS4FUOGaglirGWv+W6zwPLSuiGeElfBlPp5RdLc5A2QBY3U5I3xPMcrHMeN2uFio2WpjQXQEblCChoS7pe6QhhHU3QEimA90tr2RogdUCH3SKY6pWsUAw0so2vspnZRG6EJoNwknZCYh9NkkAp+yQxCw6JdUzokmAwhL2T+qAQrJ38ougFAC/dMBHQougER1Uhoi6EDQr2O6flFghAhDr2TQAhAIN0api1jcpJDBCY3QdEADUX1RbRLdADT6JA7o+iBod0gnfTZJAB7o/oml5ugYBCAnbqgAGyEBCQw9kBNJMA0KAl30T1QJDtZCQ3QkOwSAKZRfVMQeLoQSgaoAd1HbVPwg9UAAt0R0S1GxTtqgEHTRAJSUggBIP9UDRCAEUeyLAlAQIAgdUuqCgBoQgIALXKBogElG5QCAaIR0QgYW6I6IsbIQTQCydr9FoEUbo2ZA7P+pxOi0NFDTFpeX1Tv5WjK0fXcqdRosbfJlp6aWokEcMbpH75WC5W4YcynYTW1McR/wDpsOd/16BKbGKoxmGmDKWE7shblv7ncrFTwSVMzIYWl0sjsrR5U+Z7vYtKCdLdnseDxhs9WeTh9hC3NLV1D81u1hsF0cfoqOuw+rxasikDGtaykYx2UvANsxJGg12WKoMOCYU3DI8rj6XVTh+sk/L9f6L1HG7IzwXUkMIcxseXLs0XC8nJN+NGS4bo73FRx00eCwulopIankOdFWxkOZHI4OztG9uh9k6nDqabM6MRwZjoQTyX++5Yf2XPw6gmqaGoraV351K9pA623v8AsuvTYxHSxRVRgvSy6SBoGaN/UW6jqB2XdPWm3F2ckIwa8yPN1+Hy0koZJG6NzhcNdsfIOxCyWsSCNV9AHw9ZRk0ro56N2roHt9DT46xn2XDrcBEpJw50j3Ea00tuYP8ASRo8e2vhXj6hPaWzIydM15o7o8z3S7q2WFzHEEG7dHAixB8quy6kzkaENLpXTF0BMREIF9k7C5QgBWOqE0raJioXsmNkuqaBCQmgICiKE7FJAhW7oOoTN0WsmArlAQgoACkne4QgTF3S1T1uhMVANEt09UIASOqNQmgQrJWTujuUAHRIIueqAgQFCEJjQI0Kd0kAF9bI76JD2TOyAFqUKXRJMBWuhNCQqReNUEKR8I3CmyyPVMaXTai3lAUL6pbbKQ/dCaYURTA3QCn9UkJC213T6aoNrlHTTVMYIT6IAFlIxItqUECyNzqmAAdUEb9U7aIsgQzYbJd0+hSbqgBWuiyfU2T0CQESLbIP7pkdUboGIC90e6enRJFgCLdVIbapdUAkLqjf3T6bJbboGPY2SIumkkAxa2qbRe9gtFJQzVT8sTCf7LafgqD8tgFXUA9PkH+6hzS2RrHG3u9kVUmFyzMM0hEUA3kk0b9O5XRoIIcrnwwveALMNvU93gdB5VRw+ur5mGtkEbQL5HGwY3vbot9ZjtJRwMpsMjEhaMpd+kefJXNOUpbR3OrHjjHeWyPRUdIx/ClLUS54p6eqdcwuIOpsQSNT0XVqaw4fgtXV8x88kceaPm6tv0VfB1RJPwvW0Tnxc6drpGgj1A7X+4C4uLSshwapw6Nz3uhpWvlL9zI46hedpc8lP1O6MqgzxlOyqxvFAZJDJNK67nuOgH+wWjiCtimnbR0Tr0dL6I7frd1d99vC0vy4JggZHpX1zdf8kXX6n+izcN4UMQrrynLTQjmSuO1h3Xq3FebsuDzdMvZ7s6mDNGA4W7F5Wg1U3opmPHfckfuuv+H8bZcee4tIeIXOBHU3HReUxvEv4piWeO4po/RC3s0dfquzgeJTYV8TW0wDpIorjMDbcLmzY5Sxu+WbwktelcI+kSPENbJE6R182jX9PAXyvEpxHxBidO9wMT53A5l9B4axD/iGhZiNTTNjlzlpsSb2XzHiIt/j2IdPz3W+65ehg1klB8o6M814aZ0uHa4YLiktFWnNQ1YySA7WOx9x1XL4jweTBcTfASXQu9cMltHNOyceWuo+Wb86IeknqF38Pd/xRw9Jhsp//EKBueBzt3NH6V3N+HLX9f3OfSpx0/Q6X4MSU7MbqY6gEmWKzLDre63x4DNg9NiL6QnmumnDYnHR0NzofNtV5/8ADaGX+NNLXct0Lw6TN22P9V7XieOVmIVcsUL3UgpJfzm31eR2XD1U/wC64J80a9PH19DwGDzR11K/h3E5Mocb0crt2O6D2K4NXFVYbWSU1Q0xyxOt2v5BV0TvjIGnmZZo9RYfuu9URDivCDOwj+MUbQHtIsZmD+67rWOW/D59z9SWtapcrg48eOPkj5VfDFVR6D84XcB4dulJQ4dUtL6ad8D/AOSQZm/dccCx1/del4CoabEeJqekrYzLTva7MwEi+mmyrIlji5rsZRnq2mrOPVYTVUrDKWiSIa52G4ssC+j8PYNQfxrFKKslmjbDI6OINcW5rE79CbdFx8dw2kpqaKujY2soptBOwZXRu7Otos8fVpy0Pk0n0yauOx5FJdX+HUs//o60NJF8k4y/uNFlqsOq6UXlhdlvYPb6mn6hdSnF7HPLFKJkR7bo3QArM6DVLVSPhL6IFQIQeiEAJJPqj2QINktwmgbIEL3QCAU/6pIGMBFhdCV9UDC3dA8IFrGyExAjZDU+iQCsnawS8o0TASdihAQIBtZARa+qNkDGEuiEwkAgLI1TskgYJ69UkxqgSC/dG2+yP7I32QMQ2R5Tt3RYoAEbdEyNEhrfVA6BNBR7oHQX8o9kuiAgQ9AmFFMWSKHcJWTCOiAYdEHZGiWgugQIT6XR4QAkI8JeExBumEJhA0CL6IRskAvKAU90tkxBoi/RCEgFZNCN+qY6AI22QlogQd0I0+6LIAB10QUBPQDdAgCBror2U02Rs76eXkZgM+UgE9rrWKGGOd4xFz6JjRcRZCZHX2sD/VS5JGqxyZzQO5sFupMKrasZoad/L/8Aqv8AS37laI8SpKR7XYdQtztNxLUes39tlnrsUra+3xVQ54GzR6Wj2AUNzfCr4lxhjStu/gX/AAVBSl3xlYZXAf4dOL3P+rZeswF1BRYca44RAySU5aRsvrc7oXG+wXnOGsIjrC6uxC7cPpzd3/5V3Rg91djOKyVVeyN1rcxrS1h9LG3FmD+65sqc3oT+J04tMVqapHquM8KpsI4SqI4BmklrY3SSZA3M7KSbdh4XzO2pX2P8UagN4PZG3KRNWAkndtgdl8dcLo6CTlit+pzZm27I301XsuG8O/hOHjFapp+KnBbSxkbD+Y/+bLk8KYOMTrHTT6UdN65SdjbWy28UYy6eVzYhlBbkjHSNn+5/ZXmk5y8KPzNMGNQj4kjkYhXuqqhjbDK2S7srrh7idXL6rxm97eEMRyOysysBGb/MOi+O04Bmiab2ztvbfdfYuLHt/wCFcYDRmLY4xr0u4Ll6yKjkxJepWFuUZNnyvB8Tdh1eyZxLoD6Jmj9TTv8AXqutV0keG4gYJXg4ZiABbKflbfVrv3+y85MQXABtgB0XfwV4xrDX4LUOPNiBfSuOunVv9/uu2arzfUxxSu4s40wqsIr5GwTOikYbZ2H5h/cLuUGPU1Y1tPiTGwuJ/wARvyE/1afIXOljdW0DxKB8ZReh46uj6H6be1lx+hBCpwjkVPklZJYntwfRZ+HajFy6KSNsshaHR1FwHtHS52e3914fE8LqcOqpKeojySRuyutsvbfhviM8uF4nSTufJDTNa6IN+ZoN7geNFfxY2gfi1FDWiQMdQM5bwbOuSep3+q5IZp4srxvdG88cc0VJcnzI6HUJLuVeGZJpYZI3Mcw3ErQSwt6E9R7rmVVFLTOtI3Qi7XA3Dh3BXfHJGRxTxSjyZgknZHRaGQuiEICAEghOyECF4STSG6YgvYJWumUAoASNEWRZMQraoRfRFgUCQJJ6aoQAkdEFB/ZMBdEDun0QUCC6RQhABrZK6f3R7IEF9EvqkmNtUxcgi6Cj2QAICEBA0CCEd0IASY6o8JIAaEDRCANZHdFhYqdgL/slY2Kg1aIW00StupZbJgFPYncgAE9FKyW10gItGqkBZFrIFkAHRK2qYF0wNdEwEgDdSyi2yjte25SALXPZICykPKCgGRO26Y3Rbsi1tUWICBcC6VreVK1uiD+6EAk9LIA/+UBA0FhrZAubo1vqgjukMSB5TsixP0SELbRBAupFRtc6JjoVk7XCdjbut8GHHIJal7Y4ztm3PsFLklyXGDlwYY4nPNgN118MwqOZ4dVScqAOAdK4aAnYK4UkTIgIWvdUuIyR20A6lx6ey9FgOHiowrEKSsLZCHMks0mwtdcmfqNMbR24OluW5TW4DLXQtZQVlLHTNtaKI6u8k9SqpMOouH2xB35lZJqxu7/fwF0cNxHDosQdTUgBEVy+UjQW6XXlsRnkiknmmeXVtQ4uzE6xtv8A3H7LnxeJN6JPb8nXk0Y1qS3KsaxBsg+HhGU5s00l/mPRvsFdw5Q04zYlibslHBq0EX5jugCxYNhr8TrOXq2JgzSydGhXY1iDJ3spKRuSjpyWx/5vJXW1t4cfmcSdvxZ/I9xhuL0eBYdR4vWUjnCtdJGJIjcsF9iPp+yzVE+EVhqcVoHVUkTQJKwTR2AA+Vo9zorXYe7E/wAMWBj2B1NO2wJ1JJ7f+5GKQx4ZwNUUkIN3sa6U/wA3q39lwxUL990dcZOW/ZHg6ueoxjE3zFg51Q/RjB6W9gB2AXbx58WC4ZFglK7/AJiRofVvadD4T4fhiwfDpMcrGNMlstLG7cnuvOTzSVM8k8zs0kji5xPUruXnlS4X5/4cjeiNvl/gUA/MZbo4L6Bw/hpxanxekc/1Gjc5gB1c4aj+i8JQsL6yEMtcvA1X1n8P6SoixWeWRjQ0R5SWOve5/os+qlpjZOF8sv4Ap3U/CdCxz2uEuaUtA1FzsV8t4nDf+IsRsLfnusvs2HwR0cQpIo3xsgvGA89jv7L41xKCOIcSDj/13dPK4+ilqzzl6nVniljo58EroJmvbuOi6YqJcOrKfFqI3IcCQP3B91yO+q24dICXU0rjy5Nr9D3XpSS5ObHLsfT8EpKLFP4rPQWDMToC5wAuY5Bf7G65XBclXU8K4vLiFTUStETmRtlcTls03stf4PTijxSsopo781vpJ8f7rqS0cWDYLiWHxv2bUyBt/lBJt+xC8jNLS3j53VHXCTlNnxmBxjyuB13XWpKyWiq4sToT64z62HZw2IK4zbhoV9NLy3G59J0IuvYnGzljKmeh4nw2CspmcQYVbkTH/mIh/wBN6j+Htb/DuKaSoDQ4Eljr9A7S6hw9iTcJrHR1I5uGVYDZ2kXAv1XoOHuFfhuM46eNzH0UsTpad5Nw8W2v3C48stGKWOXpt+3yN3BTev6nq8doqBuIYi2dpLq9/N00tlZu3zp+6+aYLiseHyPp6hnNwup9M8Tv0/5h5X0KPFKbig1hZT1UdZRRPjcC0WabEEfsvkNNJy3+q2XtuuboYScZRyXao1lLTGK9DocRYM7B52Pp386hqPVTzjUEdj5C58FdUU3+DK5t9wDp9l6PAsQpuS/B8aOfDqg/lyH/AKD+hv0C4mOYRPg1e6mn9TTrHINnt6Fehjnb0T5/P87nPki154FrKmGsIZU0bZJDoHRHI4/bQqT8JilMjKQVAmj+eN7DdvvYaKvho2x/Dy52QfEM9V9tQvrlVR1eH8a4jiFMyOUSU8bw0tsJL6Ft+h9P7rDqc/gOl6WXjrJ7SPiklNLGSHsI9lVay+hV0sfFdO+OKOOkxinc52QCwmbrpfuF4nM2GV8VVAQ5ps5jtCCujDmc1ut/QzyYNL24MXdH1XQENHKHEOdG7oNwoNw/OxxZMwZejtFr4ke5n4Muxhsg7KRFiR27KKsyoX1TTskmAjtsgbFPvZGyCaFZKyZR3QMRCf1RbVNAC6I1RsgoAWp2TA3Qg7lAIRQE0jqgQ7pIS1TAe4R9U+iAkMATZJA3TQCF7I3KaLdUDAoQi99AgAHVO2tykN0D2QA0tkdFIDTVAciujqUxoEggYW6hCNEdSkAJhJPVAIPogXQjogYWQUBG90CEE7J2SJQNIOhQEin7oAR90DqmgIEKyPCPdGyAAIsjRF0wELo6ppIEO6AkLDqttFhWIVx/5OinlH8wYQPuUm1FWyoxb4RjvqVIRuffI0m2psF6GHhCqL2tr66iocxtZ8oc4/Qf7rq0PAFZUPrjR4nCaOnZd1RtzCBcgAdPKwl1WKP+Rt4E1vJUjw1tdASell16Lh3FKstIpDEw/wDUnIY391OPHTS08ceGUkNOWtF5coc9x6m5XPqq2qrHZqqpkk1vZztFbeSXGwtOOPLs6smFYVQN/wCfxP4iTflUjdB4LircNqIZ6ptNguFwxyXuaioPM5bRu430C4tFST19WylpI88sh0HQdyfA7r0E1VS4LRfCUZEkhIMjy3/Hd0P+gdB1WU01tdv+ehviae9JJHrMGxL43H6DDZi2dkTXSNu0DO4C4eR08Bee/FdkjeMpxJbSCLLruMv+6z/h3O53GdPJI673tfdzupIUvxSL3ccYjzLXAjtY7DIFy4sfh9XpX/n/AGLNk179v+nkxpfVdDAsJlxit5EZDImDPNKdo2DcrLR001bUx0tMzPNK7K1q9TiU9NgWHnCKJ2c//wA3KP8ArSfyjwF25cjXljy/5Zlhx6t5cIz8QYlTiKGjw0OipIRlhYDqe8h8lefprmphF2+qVo9Z036quR5keXncrRht/wCI0gGp58e4v+oIhBQjQSya5I+p/ii5sXCdNSnlSStqW53RuuG6EgL5TR0c1dWR0lM0ullNgB0X1j8VmEcNySCMjm17NfZhC8thFJ/w3g5xCYWxKrblia7eNvU/+eFw9Jl0dPa5b2LUPEkvuRxmeLBqBmEUjvTEQZ3W/wAR+9v9146WR8ry+Q3JNytFbUunkd6i4A7k3uepWX3Xbhx6FvyRmyanS4LaPWqgBNhzG/1X1zjyOYcL1RjacjiwOsPK+T4Z/wDxGkuNeczS3kL7Lx8QOEK0cxzS2RhDADY+oLj63/8A2x/EvBOoNHxWZjm/M0jtdRgnkpqiKohcWyRuzNI6FXVV/SS6+nVZT2Xox3RySdPY9Tib+bFT8R4dH1y1UfQHYg+D/dcTF6ZkUraiDWnqBzIj2Hb3Gy28L4lFRVclNWjNQ1beXKHHRp6OWipoX0M82B1OXlyP5tLIdr+/YrGPklp/lf8ADd/3I2dP8MRG44pBLqJmsZbvcldvj6qpKjiOmw7ESOXJRCNklvkdmOVcj8OWQ0keL1taJw2i5by2MC5IzdPosX4mVHx2LUdcI+Uyqo2SxtJ9QaSbX7Fc7hr6pv8AnBaloxJ1wY4auvw7EPgqmQ82G7YjJs4fyk9QVsmp6WtY/wCBLIrfPA8ejN103afIVNM6LiTBTTvd/wDjFG28ZP8A1me/dch8r6iISxB8VdTC0tjq8D9Xv0K10NvbZr+fQ0U41b3TJVWFgOIZ+VJ0ied/9J6rlSxOjJDgQRuCLWXfw/GIKn/lMVa0MdtIRoD3Pb3C9A/hSorM0QLZYyMzJnn1NFtLO/UFXjvE6yGb6eOVasZ89AQRZbcSw+bD6qWmmtzI3EHKbg2WLUbiy64tSVo4ZRcXTEhBSVEBa6NE7KJG6EIEbC5QmEByIG4SOiZ7pdUAxI2vZHhHlMkBqjygeEWKADZLW5TGyR0QJhZFkITEG6WyfRJABokdk/ZCAYkBP3S7hMQwkhNAEU0XSQA0I2QgYuqY9kI6IAaEkIA6bm+Ei23TVa3xWF1UWd1gpHW4MzEaoA3Vzm7qFtdCnqI0lZ7IAup21QG9UyaI5TayVrXU9eqLboQ2iFkgp5dUy3wnZNEAlbqrAClYW1KYiNiQjKpDsmQgCuyewUreU9gUgSI7hK2qeupTGp0QMhZO3VSy66fdG3S6BURsi2mqkB2T8IGkVnqnZTIF1dTUs1TII4Y3Pcdg0KW0txxi26Rm2C10dBNVXLQGRtF3SP0a0eSu5gfDnxlc+BssEkkMZlkjzbgfpFuq3xwUGIQj4gTU0A0DPlDT3suXJ1UU6R24ejb3keffPRUY5dExtTMQLzPHpB8Dr7rq4dRRxQmvxiW7z8jHHYHv/sqp2UeAzCQQ82cm8DHjYdHO/sFzoxiGPVxY55e5xLnE/K0dSpa1x2dL17mqfhyp7v0R0RiL6qZ1NhEIDTq+Ut/f/wCV3uCxTPxCsw59S9zKmncM1rlzxv8A1K8zX1sFBTHDsLdcn/Hn6u8DwrOFW1f8SpnUUvJeDYyWvlB02+qyyYl4TrZFLI9env8Ags4coHwSPFU0iIzGO1vmcL6ey43KqcUxNzG3fUTSWv8A+dAF67Fw6ixmkoTIXMjkfJa2tyND7lYbjhrDzKcv8WqwcoIuYWHrbuqx5m3qXMuB5MSpLsijGaqDB8P/AIHh5DpXWdVz9Sf5QvNBuoG91J5LnOe5xLnG5J6la8OgbI98sxtDCMztbX7ALqhFY4nFJvJOlx2Pf8D4SyobUSyPeQ1uVrDcNa63zdr2SnpZ8SxGtoanOIAI4w5zbAsbqf8A5WapbU4dgeH1eHVc9M+rvnGbTNu39l3qOuqGcMmfG6vPIRZ8jGgZQ42G3vuvJySlqc0+XXvPSxrZI+ecU4q3Eq/l0wDKKmHLgY3YgaZvquLbot2LYZLhVa+CX1MPqjlGz29CsgAK9bGoqK08HmZdTm9XJqwiPPiFOLX/ADBpbyvq3DldTYNPNVVkoip7BjidL6918z4YibJj1Ex+YNMg1buvoHEuEmThzEX0nOkEQbI8G1g0HUrn6latn7jTDVUz0raiOunfV0MzJaeV5Ic1+a31XxriYl3EOIk789wX1v8ADuhjPCNI83Eji826WudV8n4maRxFiLdCee7VcvRrTmkv5ybZZqWOvSjj2te6Y3Ft1IgjS67XDuEsq3Pra53Lw+lGaV/83geSvQlNRVswhFydI9DwTPFSYvR1NXO2BjBmc92gOm1+i9zjcLMTp66ppHRyNkhewPa8HQjx5XB4KDeIaDHHGGOISRCKFttGAA5f+66WHTU9BgNa2hZHlpInZg3ZzgNbrweqk3ltcpo7oJXceVt9T4m0ENtbZI9RZd7ifD4WGDFcPA+BrhmaB/039WlcIC69+E1OOo45wcJUa6N4c0wy/KdvC99+GGJSOxmmwuuILIQ99PKTqNPl9l83BLdgvS8JzPbitFK5wjLZm2e7QAdVzdXBSxyNMbvy2fSKTCm4RV8RSAZfiKh8jHXPqaW329yV8PaN7HS6/QmNUrq1009I7MOUWlwcLG7bL8+lpYSw7tJH2XJ/Ssnia5PnYrJ7CZbDK0tMUo9BXqsHqqfGqEYDjD7OH/oaojVjujSV5DoVdFJdmUk3BuHDovRyY1JbEwnRtgwypo+IYcPqmFs7Z2t20droR3C+y1MdTI2lfAea+OwmLXDYX0+68JgmIwYzLQNxMhmLUU7DBOf+s3MND5XsKTCjRcc4zWSMBhljjc1utiXDU/cfuvI6+WtrXs0vrub40oez8T5IKl3xL3CUxyskc5kgOrTddupgj4rpjNC1sWNRMu+OwAqWjqPK8vP/AOpmIFvzHadtStFHVyQSxyxPLJoyCx4OxXqyxulKPJHiW3GXBicx7HOZI0se02LXCxBXvK/BKZ9Hwe6CGOP4xhbO4MuHEWNyOu5WSqpoOLKWSppWsixqJl5om6Ccdx5Xu6OiiqeHeF6gNzGlJDgRbKchB/cLk6nqdMU+Grv6BHHpkvR/9PN4xFw/LiVRhmIYdS01QwBsdTCMrCSLi9tt+q8Vi2FOwyo5VXE+JrvkkBD2PHcFbuM5S3i3EHNN7lv19ITwvHQ2I0OJQtqqB4ty3bs8tPRaYIzhBTTtNLb9i5aJeVqmcI0rXsvHNG7xex/dQhpHSzcoXDt9BddzFOHeXTmvwaT4uhNybfPF4cP7rvcFuqP+CsaloY2NqqaRr46hrRnG1wfFgfutp9Qo49Ud+3w+Jj4S1VJHgJYjE8tJvZQsV9I/EvETS1GH0zaWmLzDmmfJGHOcdt+268IamB59dGwafocQr6fPLLjU65Mp4op0nRhPlC6GTD5QAZKiF3ctDx/us08MbXhsEnNva1mkEntZbqSIeNpFA10CB2XqRwBxH8HFVGjjDZRcMMoDh7josZ4Rx0Zy/D5G5Wl17g3t0FuvhZxz4pOlJfUfhSq6OFZPot0uE10LC6WjqGgd4iFlfE9l8wLfcWWiknwxPHJcoqKQUh/Twg221+yZOlkbot3VzYXGIyemw6ZtfsqrjqR9UXY9DXKFodQgK6Kmknvyg02H8wF1U0i3zBOxaXy0FtLJAK2KMyuyR2J7XCrNmkhxAOx1R7gcXVgQi2ilEDK9rI7FzjYC6JWOikdHLZrgbEEo9wVtZEeyQUhY9QpyRPhdllblJFxc7hKwSZWBrrsixTsN7hTdFI1jXOaWtdqCeqLGk2VgaJ2+6ALqzkScnm5Xcu9s1tL+6LEosr9gj2UvFwpshe5jnMY4tb8zgNAiytL7FWqFLKdSpNje++RhdpcgC6LDSysBA3TtZNrS42aCT2CBURtpqgBSLCCQQQRuCNkAFA6FZJTc1wOVwLSOhFkh1SBoVrbaIG6dkwCgKEBqg7KWQ9x51Sc0M0Lm/QoHTIbp6XTJAb5W+kwLF6trX0+GVcjTqHCIgH6lDkkrboFFvg5xGqF6OLgrHXi8lPFTtt800rQrf+EYoNa/iCghtuI7vP8AZZfqcX/r6b/gvwMj4R5dC9phXDfD1XXRUlJxDI6ukP5R5QDcw12/7qnEH4Tw9X1VHLQMxauiktJVTEtYTa+jNtFK6mLlpim38K/I1g9WeRjYXuDYwXvJsGsBJP0XYpOFsbrGh0GGzhp6ygRj/wDOW93G2JRscyhgpKJh0/JhAICdNFi+NQGuxnFJaXDmH1VEjiA/wxv6j7IlkypW0l9/sio44etmebg7FIog5rqWaZzwwU8Mud5v100sOqurMAkwR9IOKInR0r2OdG2nILnuHQkbbqqtx9sFM+h4ejfR0pFnzuP503lzug8Bem/Esn/hThHMcznQuJcevpYstebXGMuHfx4HLw4Pyo82ziKio7DCsCpYiNnz/mO/dZsQ4mxrE7RvrHhp0EcIyj9lyGtc54a25J6BdaKGLCYoqmoa2WV17RF1iRbf2/qtXjxxd1b+v5CE8k+9Iughiw2nbV145kp/w2X1d/27n7L2/wCG1eZcE4krKyzy2MktGgsGHQdgvmNTUzVczpqh+Zx2HQDsB0C+i/hpTc/g/iTJn50kb4xcgNADNPrqubq8aWFufNr8jlk1JxXB8zAIaAraWmmq6mOnpozJNIQ1rBuUomPncyKCN0kryGsY0auJXquXFwtROY0xy4lJpUPv8g6xMPfufou3Jk07LlkQxanb4G403DmHOgic2SeT0zytOsp/kaejB1PUryk80lRKZJXXcdz/ALKysqJKqd00tsx2aNA0dAPCoU4send8sMuTV5Y8I9f+Fdxxa1wLfTTyEZm310Vf4mwcvjWtYCXyPbETpqXFo6K/8Jco4wZnNrwPH9F6His0FJxXiePVRifLE5kFLDm1MgYLvI8XXFOejrG//wCf9jxx1Uv5yefhiZwrhT85aMZqo/U7f4aM9PBP/my8jPI6VwLyXW0uVoxCtlramSaZ7nvebucepWS+67MWNxuUuWGWS9lcERuteGenEaRxFwJ2H/8AOCy9V1+FqI4hxDh9LZ1nTNLiBs0alXkajFtmWNeY+v8AGs9N/DcLbXkNo3VTpZGkfMWtcWj72XybiXFpMSq3yvcW5xYMB0YzoP8Ade5/FjmluF0EEb5WwF+aUMOrzs33tcr5W65Jvv5Xnf0/GnjU2bObjjpLkVhZMa30SCY8r0zm2NWENLsVoWgXJqIwP/uC+0cZwip4TxSwa0s5dnOPUvGi+N4K3NjOHi9v+aj/AP0gvr/GDjFwzXxk5ufJHbXazrrzusf93GdGJeRnxzEacwOjzOY4uF/SVjsuli7A2SPS3pXOO1l6EPZOWa8xAgWt916qjk/4hwI0pN8SoGgwu/U+MbD6bfZeWOi0YbXTYdXQ1lP88br2/mHUfUInDUtuUXinpfuPYcNYi11BiUcjHMdWsFPM9o+WaxAJ7Agn6qv8VqJ1Bi9BC57CG0MbG5Tewbcf2XocLoaStM09GAKLGWsJA/6cgvcjyD+68Xx7VVNVjTmVhjMtMPhyY9nZb+r6riwtSz7HTmVY+Tz9JUS0tTHU07sssbg5pXo8UjbX0sfEWFWbK11qqIC5Y7yOy8uurw1jTsFxDmPZzaSYZJ4u7e/uF2ZIN+aPK+/uOfDkS8suGZa2Br2CrgH5MpN2/wAjuo/2XsODsTdT8LYgaoGeKmlbkjOpDSNQFy8XpBgtQTC7nYPXgOYQLjvp5C3YDRFvD+NQXa95LXM1tmbY2I+65s8oZMO/G35OrDjccux0capKCtlpXOJFP8G17XDcZnE3K8vjOAOo42TtlZNTybSN2aex7L0PGtQ/h3GcNZA9k0fwEbJogLNc0aW/ZYHTCmp3V2GAVWGTH82mcdYidx4WWHXBRcXszSXhZbTW55KemfCRmbodiDcFUHfay9RSUtDVlwoqox53XY2cXYCf0O7eCsdbgz2zGLlmnqOkTz6X/wCl2xXdHOrpnFPpWlcTh/VK1rq2aGWB5ZMwseNwQqit07ORqtmGmyaQQmINkimLa3S0QJkRugHQppJki6pphLqUAHVG6SaBB03SuhBHZAhAlOyNkBMaF0QhH1QAaJBOyECC6WyaVtCgQI6oHVFu6YAn7pIQNBqhCLoAEJoSA9lU0bWk6LnvhIBFl7viPCvgp5IyACDa1r2K8lVRFrt7hedjyWezOCatHIdH9FWW66rW9tnHXXsqXNsSAuhM5HEz5dToi1ySrbbqNtdFdmbRAjRGVTsev3Ty9P3RYqK8th9UWutDYS4abp/DPAunqQtLM5adkstr3V7o+4UMqdioqtui3lWkJZSixELAHui3kqzLoUW62QFELA30t7KNtVaGnsggX2SsKKralBbpdXZOwSDSdACe1k7CisAW8qbYnOtZa6ahc8F0hDGDUk9V0Kaq+FtHhlPmqnaCeQXLf9I2HusZ5a2ib48N+0Vw4O2mY2fFZvhozq2O15HjwP7lTZUVFWDS4VD8NTkWcb6uH+Z39gpihLZficVqDI46kF17/X/ZRqcZcWGDDo+UNs43PsOi59UpPbf8HYoxgt9vyzpcPPpuG8Wp5aiZ5a/0yZBchp02/ddGV9IMZq6idxbQwgzRtlaQXjp++y4mD4PW1NXy4Q2epa3myNL7WHb3XXGI0WO1jKCWgqg99mXa4XFj1K5csblfPqdONpL0ODW01ZxDi+dgzOMYdI92zG+VVW4jDRUr8Nwo+g6TTjeT/svVcU0NRheB/C4cyzXn83KQXli+eNYXEBoNzsO66Omks0dXZcI5c/8Abe3L7k6WB9TM2KMan9gva8P0VXQ4RWcQYYYJI6X8t0crCcw0ufHRecq4v4VTto3EfFyAPlLf0NOzb9+6+h/he2Gv4dr8KqX2jqGuAAHTY/XZT1mSsertf2IxrRfqZOG65+PVL34hhlGws1bNluSfF15Tjiim/iTsRbIJ6Sf0slabhpGmX9l3sGkkwsfGysDad0roBCNX+m93AfRecwjGG0s1RQ18bpMNqZDnY4ax3PzD2WWCMlkcocLsdeetCjJ8nDggkqJWQxNLnvIa0DqVtxG0FsPZbLCfzCOr+v2XRrqFmASSVNPLzhIctHM0aEHd3uFx6Kmmr6tsMZOZx9Tj07krvU1Pzdjh8Nw8vdn02pghm/DuOqceZJRhr2xAa3Bt/Qrk4nHVQcO1VFMzNJJGyTKL3brex8rvcO1Lp6KswqRoyNpmlhDd9wT51C4OJ18raPF5eY5z4ZoomuPUN3/uvKw34jj77+p3U1B2cPCJGY1Q/wAHrHZahn/o5juD1afC4k9NLSVMlPOwsljOVwK62I0XNjixXDGvyE3kYwaxvXRqIf8AiTDTUtjy4rTC0jAP8Zg6jyvS1aJX2f2OLS8ka7ox8FR8ziWibp8xOvsV9sw+iFTR4jRuDS2pp3Rm3kEf3Xyn8MYM/FdMTG12VjzZw20X2+ANgmtyQ1zxoWiyzzt8o522o0cTAYTh+FUdHJFEx0UDQcm501JXw/iWxx/ET1+IdYfVfbC7lVc7LW/MIC+P4zQyVvE9ZBSscXvqDbTbuVxdHJubs7HGo36nOwXCZsXr200INj87+jR5XSx6tbWPp8BwOMmlgkygjeok2Lvbsu3itFUYBgowzDYXOqKkXqagC3p/lCOH6Sn4WwZ2OYowOqpBlpITuL/3PfoF0SzRfmW/oveXHG4r4nsvw9wqHBOdQPeZJZImvl12OtwuY3Dn4dwtVUUOXmtimBzaaEnUnvqqPw4raurq3Vc5Mks0x5rh+kWNvpsunxEXRux5jc2UUji3/UQSbfsvKm5+O4N90zSCrI67pP8A0fNeF52SCfh3EnEQVRtGT/0pehv5XCraOagq5aSpZllicWu8+R4WioPxNOypaf8AmI7B9uvYr0raVvGFFSTc1sWIU/5dS5w0MY/WT4XtufhvU+Hz8TNw1LT6cHncDwd+KTvc5/JpIW555yNGN/38L6H+HdXBiPED6alp2tw+lpnMha4Xc65F3O8leVqXOxeaLh3hmM/BRuu+U6c53V7j2HQL3/B4w3AsYhwiiyy1DIy6ql8nYH/bouPrMlwer/4vViUdMJKPNGvAfhMOgxOkpI8zafO0vt6XPAJIPtovlfEVDDVUbMdw1loJbCpiGvJk/wBivrdfDSUwximyEGoMs7rHYlt9F8lwmrbg1SGyAT4XWsDZmHbKf7hc/wDT35pzi7/2arzxba5o80BdAOVdXiDCDhFZljdzKSX108vR7T/cLHRUUlZI4RgCNgvJI75WDuSvbU4uOpcHI4STruW0dQWzRPabPY4Frr2sbr7pMyonZTyg5n5G8zIbh2i+WcJQCqxejp6SkMlFFUNdUTPZfOel+w8L6dh8lNh2O4lCyHLFFZ8znmwaXC4t4Xh/1N6pJLlHVC4r3nwmrYYqqeJ4s5sjg4djdVheqx2mp8cppcYwxgZUxuPxlO0+fnHheWAXs4p64+/uY5IOMtzZRVctNMyaB7o5ozdrgvrPD1TJW8BB7C8VDJXE2sMzrkm3jVfNsNwyCGk/ieMB7aY6QQNNnzu7js0dSvrWC0MeE0OD/CSSNgqI80sHzlz7Alwv9dl5X9TcHFVzZpG4pX/KPjvFpc7iWvc4EesaW6W0XIabFfQ+OMMpMaxjEZsIkvW0pAmpyNZG2Hqb7bL59Ygm+/bsvS6XIp4l8EZ5IvVq9TfhmKVOHTCalkLXDcdHDsQvf8B4lS1tViUdJT/Dc6EOnhbqxzr/ADDt7L59huHyV73uztip4Rmmmdswf3PYL33AOG4fNRYriVM2pglp3MbC8ONyzc6bG9ly9esfhS9f5yawctO/B538RZJZMWiM7C1wjIGmhF9F5GxC+v8A4jnD3y4fRYpDKOZC5zahp9UZ03C+aYvgtRhbxmImp3/4dREbsf8AXv4Wn9PzJ4YxapkZoOf9xHOggkqJWQwtL5HkNa0L6RBgkHDmBQ1E3J5wqYXvqC0Ej1C9j2slwJw58HJFUVbP+dmZnYw/9GP+Y+Sq/wASuIm1UjMGpchZDbnPaBYkbN/3WGbqJZ+oWHH7K3ZWOPhLU+S3H+JJanhitraB5jaavkMkHzFvU+CV87hq6uFx5NVOyx3bIR/dejJI/D0gda4f0XmLa3XX0mKGOMlFdxZpPavQ6MOPYvB8mJVNul3l39V6Thr+J43DPUYxPJNhMej2ZBmnf0Y3S++9lw+F+HqjiGv5ERMcEfqnm6Mb/uV9TxGqw/hnCWvyR8iBgbTRN3c//fufdc3W54wax44pzY8Wp8sx4RLQ8IwllXCJhWRmd9PFHnNO0dzvl1tfuuVxRxRimEVTH09Fh0+H1Dc9PMYSbjsdd1zsMqJZ8Wx6olJzuw17rE/LoDYeFl4exCnrqN2B4qf+TqCOS8nWCTx4usY4En4k1q9fn6fA1lFW65OlwtxYavF4qWqwqgcyqc98jmx2IIb/ANlzX8e1Je4fwnDC0OIF4r6KjCMPnwniyGiqh+bCH3I2IymxH0Xl/wBTib7nddcOnwSm3W1L/ZlNyirPpvCUcXELZccfh1IKunqY4WxNaGxOadyR3138BaOJ8VbhsHxmF4NQ1FLHIYqgSxgPheD1HZX/AIOxt/4exNxyk/Etdb2AXmpscFBxPisdTHzqWWoeyeI6h7b/ANQuFw19TKKVqPYeOWu7IUvGME9QJ5uHsNe6HVoDLXubHoupxRxVRYXjU9HT8O4fIxjWHM5ovctB7eV5vF8F/hFQ6SmeZsPqmtdTTDtmBsfIVHG1zxRWX7R//oBdccOGc1XFPu/cEk4wt8npOHMTw/i7GYMJruH6KCGTM5z4PS4ZQSNRZd7HoKTCqQtpMBw6orYIWyOhLAS6LUXBtqRbULx34Wt//fWh8Nk//RK7f4j4nJhfG9PJAQxjKZl7dPU7/wAsufLj/wD1LHC6q6tkQl5ql6HBPFlBUN5TuF8MaH6ZgACL/RdzFMcwOjwnD6mPhmkkfK58ZYQNMhte5B3XncewyJ748awtoNLM8c6JuvJef/1T0+yq4hsMDwpo6S1H/wCkF0+Fim4ab+r9H7zSpKLs3O4swhzrnhGh7fpv/wDor2vFGGcO8O8O0+JDh+CfM5jQ1+hGa513XxxpLSHDcFfYPxQqW1PA2GyNbbmyRPHj0lZdThUMuOMW0m993+5jqk2jyH/FfD+0nCFL9C3/AGXWw+u4WqMFxLEJOG4wadoe2IO9JvZtvv4XzrvcL0+FEHhPFw0a8ljbW6mQLbN08IpaW+V3f7muPz2mbIOI+HJSYGcGwEykCwc2/wBDbRetwLhXAa6nrMSmwqSCIMuKcSnIQBuAN/qvI4BhdNhdFLimKktjYACBu49I2+T17Bew4GxWbFOHuJqypNjYhkbfljYIzZoXL1CbTeKTSXe2Ka8ODff/AKeOGO8HnV/CbrdCJd/3XQwOp4OxfFqWjgwSoo3PcQXtkIzaHQ2Oy+fi/LHsu7wM0DiijJvube9l2ZenjHHJpu69WJO5UdSoxLgaGqnh/wCHal4je5odzT6rG1/mW+gwLBOJYopcBwyowwMlbmnkeTmHZoudV5zAsClx7HJ48uWnZM4yydhmOnuvVU2PwScWYNguE2bh1PVNa5zNOa4X/YH7rny3Hy4m7SttttL/AOlJKNtmfiGDgrBMXnw6rwmtqJ4cvMlEx1JF7/MO6wfG8AFpvg9ePZ5//wCll/EqzuN8TN/1MH/5gXmLGx/ddGHDqxxk5Stpd2Z2e+xym4Mw6eCPEYsSrKmaBkplDzoDsNx0Wego+CMSqGUtFh2KSVEmjQHm1/uudxw0yYvRRxNc55oYQ1jRck2XXBi4FwiwLZMerGadRAz/AM/f2WLTWOOmTcnxv/Nkaabluimq4JgwCndiWJtOI0zAWyQ0ryDG64s4nsuTFiPC8QBjwCWbzJUHVd6bHKnBsH4cqnDnxzMmbVRPN+cwkXB89V5/ivA48PMGJYY7m4PXeqnkH/TPVjvI/srw6p7ZW97qm0tgbUOEaTxNgcIvT8KU1xtneD/ZTh43bCy1Nw/h0fY2/wCy8mfIRsuj9Niapq/m/wBzN5ZHrZZMH4tmo5K4jCq10vIlkjbeMixLT730WLiCt4kwjEJMMrsRqGup/SzI7KHM/SRbuFxyAcOINwTL/ZezocnHHDxw+d4GPYbHmpZD81TF1Ye5H+x7qXFY6veK+w23Vnhp6qqqCTUVMst9fW8lVOta53UnRua5zXNLXNNi1wsQR0KiAb911qlwYvVe53eAg13GWE59ud/YqfGsRqeN8TgoY3yOfOAxjQSScov+91q4L4fxepr4sQoYhG6EOdAZdBI7KdAsU9VjeE0zpKmB9PNiDnPdWOH5jx1aD0/qubVF524tXVV87NVjpeYtjpMN4fs/FmsrsTG1Ex144j05h6nwFysTxSsxao51dKHZdI42CzIx2aOixBpBOu+qfdbRgk9T3f8AOCHO9lsJ9y0kdl9D/El7peHuEYma/wDLOdYdfSwBfP4opKiZkMLXOkkOVrWi917f8Qm4hTzYVSup5DS0FCAyfIbO2Die2wWOVrxYL4/gcYXueagEGHRc2RuaY/K0/wDmy51RM+pldNM/M925Sme6UlziST1KhsFvGNbvkJzvyrgVt19Q/DGRkfBPEjn3OVkhsNz+WvmIFhdfSsDwTEovw2xNlFC81tYcz4tiI9O/WwOi5etlHw1FvlomELTs89SRxcMUed5a7FZGDOQbmmYR8o/znqei8xUVMlTKXyH/AEt7BacQoqvD5jTV8b43jUB2xHgrHaxK3xxXtXbfcrJN1pSpEb3QmRpfut2CYVPi9cyngFh80kh2jb1JWrkoq2ZKLk6R638I6Dm43NXTF0cUEeVr7aFxO32C4PGEdWeIcTqKmB8RdUuNnDa+33FivonBU9OeIm4PhoHw1JTOdqPmdcC586rXxLDR4jjldhksbGVpAfGH6c9lhcX+n03Xjfqpx6lzcdmvsdfhLV4d9j4na99UeF08awiXC6ktLXclzjlcR8p/lPkLnAFexGamtUeDmnBwdMjtsvoHDNIMDbRh5DcTr5GAk6mCMuGnuVxeD8KildNi2ID/AJOlPoYdppOjfor6XEZq7jCgdO8F3xsZcR19WgHgbLj6h+JeNcLn9jowxUFrfyPpnFVDFWUtPSvmfA51W50EoNi2QM0P3vovk/EOFSxyzTlgbLG7LUxAfK7+cf5Xbr6f+LE7oeHKUwts/wCIzh4dYtsDt+y85Q1reJML+Ngja/FaSPl1VO7apjP++47FcHRylixqd+X8Bj0zxqMj5ta+yANSunjWHNpJWT0zjJSTjNE+1rd2nyDoVzwF7KlatHLKDi2mbuHmB+PYcy9s1TGP/wA4L7XxtR0x4cDpBI1zpGh2Q67r41ww2/EmFj/+qj/qvu/FreZgL2gx8sSszE7jVcHVRvJFlKTWlL1Ph3E9PBDLByOZZzCSZO9+i4BbY/3XruOouXU0li03jO3TVeSe2xtfZd2F+Uyy8lZHZTpYJ6qpjpqZhfLKcrW+Umtc9waxrnOcbBoGpK9dR0X8AowxxazE6hl5ZHainjOw8OKqeTQveGLHrdvhHosIxGHh7ApcMo6gT18D8p09IcdSb9gvM8X4S2DEo4nzOfWVMDZ3lxFjI65IH9l2ODYYq/AcYby8+d7Yg4GziLd/c3UfxPwyRmLieCdr3U9NG6zTrbUf2Xm45KPUON79ztmlKC2PnJBBIcNjqi1zZbqpnPpxXNFg85ZLbB3/AHWEL1k7OBx0s9Jw1iEE8D8BxQg0lQfyZHH/AApOn0uung1BV4XJLBMzmVVLVNbHG7USxkXI17208rxccb5pGRxNc+R5s1rRqT4X2SniGG8P0mI43EX1VHGC4sfrmG3ubWXn9Y/CW3+Xb3/94O7pp6uex884/wATgxLiCSWlcTE1jWC4sQQNRb3K5ODYpLhVVzGAPifpNE7Z7ev18rq8V0NZLictXNTmE1Y+KjYSCSx22y82BrYrqwRg8Kj2o5srlHLqR6jEcOhijGOYDeahebTQkax92kdlqhxellojHURmegJA9Qu6E9Af9wuDgONT4LV8yP8AMp5BlngO0jf911sSw+JjP43w8501BJ/jwW1i7gjssZ499M/k/wDXxOrHltNw+aOvScKOxCHO6USUT2h0b3m7wDtld1HuvJYzgNVhlU+MxvdDmOSbIcsg7gr0+FYw2HhepoqfPFzHk0zx6vUTqw/+dV3+MooG1WG4PiVSI3imD43Rvtlk2P3t1XPDPmxZae63+3cvJihkik9mfISCLhHRepxjBZIczp4rgH/HjGjvcdF5yenfGSbeno4bFenjzRyK0edl6eeNlKVk7EbpWWpziF0lKySYhd0I7oCCQuhASQAAd07hHRL2QILJbKQ2STAAB1RfwjdJAB7ISTQIRsn9UkBMB/1QEupQgB31ISt1RbXVBSGM2skAjdA90xD6IQEJAfoXH8IkxNpnwycVcZBzSEgXK+aYlG6CpfDMAJGEtcLg2PuF9CoYKrCMImlxCtip2tJJbI4esdv+y+U41isk1dPLdoEjy8ENtoV50YqUrieum4QpsrmexrtXKnM19yCCsEjnPNyb36q+to5KCo5XOim9IcJIXXabhdGn3mFtptLYsfI1ptf6KLHh7tToszJHF3rsm59vlPuqozk7Pf4PgfDjY4qipxKKru0Exl+VoceltytPFfBUVLh0uM4W8MgY3M+ndfT/AEnf6FfPqKd7XDlhpIN7kL6/wvWYnSUUsmFUjKirewNa+d7jG0+w/oLbq4NN6JV8TxpdBmwuXUvO3XbtR57gnD+GpWRz4vM+are+zKXIeXbSxJG/svp38K4MkgLJqSjjcB6hYtcD9F8vrqHFqLFY6zGIoWS1MvNLoTZty7XTpuvZ0lfQ0uG1d5HDEHSel7mZgQLaap9RN4fI0j1ccHPCsu+/oeJ42oOFaeKA8NVNRJPncJmuvlDeh1A1v26LxpZYk2XVxGoE1TUPfa7pXONhYXJJ0XY4bwGixKhlrauYPAcWMgjfZ1+5XPCW1sz6rPj6aGqdv7s8lkJ2+yAw3K6eLYZPhOIPo6kNEjWhws692nZeuwngCmrsBhrJMSe2sqRmhjiDXNaOzuq2gnNbGmpUn6nz4tF7WSLF0paGWCaSGYASRPLHjsQbJCjcQbhZ3RWltmAR6I5R3C3/AApAttbe6j8O46gaI1ISRj5a6GEUvNnMYAzuIyk7X2UfhnHYLs8N0hNewkH5hf7rLLkqDNsMU5qyuojOF1lRSSwxzSssDc6G4vovR4VTUs2Ay1badtM4Al5OgNvK5XE1O6qxCGeO13NyOI6Fp3+xWmpo5XYFVugqHRwFoEjCbg62Fl5uRa4Lemz0YupP3HlsWpKp0plc7mxOd6XMNwPCrMcWHQBzSJKx24tpEP8Add3D6Celp5ajnMHLsWxzAtLwere6vHCzsXaajD3MY+/5jHOFvddPjwjUZPYxlibua595i4Jqn0eI/Eaua4hs1z+kne/7/RaqmKPDsXqZaZ3LjhdzY3kXD76gKOE0zKV9ZBNSkvhhdnZISOYR/ZV0WKU+IzxUD6FwbLKBdr/lH+wWM05TlJcHRCoRSk9zLxHilccUgqw18EjYQHBw0d9OyspoI6hhxGkpgysyEsgds538wC38U0LZOJaKhhcA2WJjMzjcDUgLXxG2kwh0NHLh+ashYC2qhlLQ8fzW/smsi0RUVu/wTSc3q4PBNimqavIQ9073eq41v1X0ngnD54mQOpKyJkMMruaHmxk01sqXYVBiWFx18OSCuqWZWOebEnXT3K2YVw6+u/D3EMPlZlq6eR0jb9HDXfyFGbqI5o6eN6I0LEm+b7hJglRLjtPWU+R1LC95Lc4uS69zb6rwMFLHimIcqR4jdzixzraWvufZet/DGje0VdfI0FhtGwk633On2XP/AA4fDFxfL8SwFj2yts4X6oxyePxFd6Ugyy1JWjrfwGrDZcNrnwVFDKByjG8XgI2IC8rimGzcNQGAyNdUVRsHt0swH+pXQmooxxW+KF4Z8PW2LM1g5l7j9l3+JqyhxLFDhOINZE2SISU8/wD9N+v9bJwnOEknunuy2lJX9yGOY3XcNYTg0lPTwTRVEFnOkBDg4WNrg7arFisgxLgebEvhIYJqiQXEQ39dr+618cgz8BYa4N0ppWtzebEH90nStwrg2Oedge2IM5bCPnf007AqYVpjJLzavqRG3ab2Lfw+wYxPdQzyM+MkYKh0Dm3DQNAD5PZdUNL8ca7+E0zKd7bsqYnWN9iCLb3uvPfhRXTScTVlVO4ySSReq++pXr8MqIZOIcRwiSIxxxS8yN5/mPqP9VeaN5HF80ZQlpdrgfDnD8NLxt8bSBojMThKwH5X6a/Ves4lzRx072lwHMs63UWXF4Yo5qfjLFHPc4AxMJaRpewFwvQcV2bgNbKW3dFE6Rlu4F12RwufSST5OKeRfqYvscmlgmqqaSdguwn0LjYZgVJSYu99U4/GYjISwDdrANbL1XDcT48Ep+cxzC5uazvOq8nSR1Un4nVcr2ufFTsa1p6RgtBsFwLB4Mbvk3WVylOK4R1HfGfxp1PUTwmih0s+IZiTa2uy8d+JeFGvmlfQvL5KBoMlOB+lwvcDvovZcQVkv/FNNRBgbTimM7njdzr2A+i8DxXidbhHGDcUMLhFNE2NzTtIBuFzwxOHUvTyuPebYbklL3GngZlRTcD4tiGHyFlXCHPjNgR6RfbrsV0MKxHEMb4AxesxJ8TnOikDHMaG3AH+913eEqSjlwjEY8PcHUtU0va0fpzt1H/Zcfh2kDPw5looiefPTuY1jza7nX2+6WWUX52t3JBfmaXZo+VYJRT1dSIqaKSUOac7Wi+i+p4ZhWG4dR0eFMqWU1dK0Pnp5GEulv38BeapZIcFr6PAcI/MqHTM+OqWC5JBF2DwNbr6HxHLS0eM4ZJHEHV9aOQxxGgY05jf7rXrMk58cVZd6JRS72eO4jjpOAsNdBhTWnEK55LXO1yN7/ToFx/wxpnVWLVck7pDljMkkmpN7g38q78X35+JaUXuG0ot21cV0fwXLfjMRB6xtuPqnp//ABuUnvLl/MnXJY9T5PS1z6PGIq/EsNrYp44aZzXBtz0/7L4pSzgwGmmAMbrWJ/SV9h4KpGUHDmOMAblbPUAW3s24F/svmuC4Aw0P8Wxl5psNZ8v885/laP7p9Foxa43smqLi5W4rhF2B0s+LYZNhVZEHUzHB0NU425BvsD1v2V9Jw9XYtO/Dmwuw/CaV15nvFjIR+onqf2C+kUWG0+H4FRS4dUCDDpjzKkTjM517Wt2N9F5z8X8RdS0VBhtE7lw1Ic+XILF4bawPjW6mHUznn8OCq/t769ReJFqq/iOZR49SNxahwLhxjGULJRzJ7aykdutr9f7L2jagurWSPab1IAku3X0tO6+V/h6G/wDF2HZhoHk6f6SvqnDVZV4jxNjdPiDo3MopAyAhliWm5F/pZYdfgrJUey399say1FtrsfJKfEJaWvdXUQEcrHFr4wLNkbfqF2HYLhwzcQS087cPyh7aPJrJJ2H+S/VR4f4YbVuZU4rUuo6eolMdPp65nE7gHp5X1mlwzJWinqmwGlhjaymNvU8WF7+y6Op6pYmlD5/z+UVPKo+0fPKShEcI4m4sDWi1qOjGwHRoH/ncr2dNiTarDMNqXx5JYdWj+UOFl8142xGbF+KKqORx+HppjTwxjZoBsTbuSvp7ozSVWBYQI4pKWeBzjI4WdeMDT63C5+qxTcFLvXyS9CZSVJyX8o+YcV1joeL66Sn/ACalkrSyUG1/SLg+Cq5MNpuJ3MraNvw07T/z7Q0lrf8AM3yey28Q4HLiPG2LsYWw0dO9rp6g/LE3KD9SvacOYFTYdg9PJR1jJaKpk5kz5mAOtb0gWXTkzxwYouPtUvwVrWlXweIw7Co8ThL6gPoOHaH1HmaOmcNyfJ/7Bei4V4kZiL8UpaenEFGGNbBGBrlFxc+fC5P4sVzhi1PhNOclLDEJXMboC5xO/ewH7rofh7TOpeEsSxGnLDO6oZG5sgu0Nu0X+zj9lOWLy9Prly+F6f8ARPJFpNr0OV+KVU6prMLeTYiB2224VPAeCYhi87J5XSNwindzHg6tc9u3pO/leh/ETABW43hNNTZY4hTvMz2j5WgjX3N16jhenNFSzsZAGUghtGy1r2CzfUrH00Ma5f23JbrG5x2XY87xNM/hPB6yvbOZa3En2heRq02/o0bBfIWEFznSue5xub73PlfTPxVnkqMEwVzyw3e512bH0r5lqu3+mx/s6ny+flsRJydOR6V8R/8A2dh/MBBrvltqvO01PNUzNhpYnyzONmsY0klelDXO/D2JrRdz6+zQBcnsPuvccBYA/B2RyBjDVvcHVcmhyN6MH9059Uunxyk93bLlG0n7jbgeDtwDhn0hmWNpkq5A65zAXJPttZfL8fxibHq8SkObC05YISPlF9/cr7JxZWTUOEYlV0ccfpmja5jtA4Xbmv7g2XzDFsKipKmlxnCm3w+eVpy9YJL6tPYXXD0Ljrllnu3wysLc42elqOEjhGHYjXCoa6WTDXNliOjment20Xy1g2Db3PZfofiOOM4VjNTkF34YWl3XQP8A918dwbCpYWU1RyubX1RtRU1v/wDY7sB0XT0mbySbdkYpyzLfseh4YwyqxXD4nV9PJHX0jnciWQFr5GFttb7jWy8hJwpXRvcw1FEHNdYtdUNBH3X2mvjl/guHy0tVyqqngeBKAHZnBtrG+4JC+ZYvSRcV4Z/GKGMDEoWgVUTRrIB+oDus8GeSyNp+V18rNIvxI7o9D+G1BVYdhuJQSyw/nPaGBsgcHG3Qjr4Xz7iMf/vFiVtCKl9/uvqn4VU9O7hAP0zsrXPI7HQf0K8JiGEuxXi/GZJH8ihgqnvqJ+jW32HcnoFeF6epySk+3+6M4SuTikXcG0dXjUbsMqYJJMNs5zJTcNhkFrWd57KXFPCGKTY9USZ6VvMy5RJMGusAB/ZfSeC6cRYdUQSxinbI0GGl6xxWsM3+Y6kri8U4XFxBLV0E72mqgf8A8lOdLGwJjd91h+qaz3F0vrRXiOU3CtkeX4M4YxXDOJaKsJpnMaXB3LlzEAgrnfig2X/iUOmFi6na4a3uLuW38NI5cO45+FrI3RTcqSN7HHY6H+yu/F6N03FlFBTxlzzRMY1jRck532sumDl+sTk78pMnU9KXKPK4BiFTTSOp4I3TNlGV0QYXZgfC7PH2CS4TQ4VG674A6XLJ5NjZeh4FwZuF11Nnka2TnBs82nrfraJngdT9F6fjaChq6iPCqoXZVRvky31BBHqb5F1nl6lRzqUVsufo/wAFuUrWL1R8HbG5xysaXOOgAG6+p/iLDUxcDYS2ohMbmGNrh1acp0XhpsMqcEx2KlnJDmSsdHMNnNvo4L6r+MTm/wDClOL3Jqma9/S5dGeSnkxtP3mLuEor1PiAb2XvuDsHndw9V4lUTsioSRzLi7mtab5rf0WDg/hl2IyNrKln/Lg/ltdoJCNyf8o/fZfVa+spaDgf42O08DGNBuBZ7C4A/SxWXV9Rq/tQ57/t8TS3icWuW6PivEWMOxeqa2IGKhg9NPD2HVx8leu/DltX/wAMcQxwwSvErLR2bo52UjQ/Zec4rwNmGSsrqD8zCqs5oXg3DD/Kf7L334eTln4dYuS+xh52T/L6Af6q8umfTpY+P2FldK3vx+T5oeF8bYLfwyex7NW/hfCsVpuJKJnwL2zvLnMbN6AbDU3WTC2Yvi1TDSUlXVGR3XmusB3PhfZeDsOpsLBoJpvia5kIkle85nNvtvtex08I6jqJQWiTTb+JWRxxxclyfNuI8WiwOhkwDBy3nPv8bO3e53aD379tl5zhR3J4nwmQHRtUzT3Nv7rv8VYbFisEuO4WwZmSObWwt3aQSM9v6/dYPw+gim4ywpsou0Sl31DSR+9lWLTHp5Nc07+NBkTttl3HVDX1XFuJzx0VQ+N0gDXCM2IDQO3hedlw+tiaXSUk7QNSTGQAvX8e4xiVLxbicNJX1EcLXtDWNfYD0jZdrg6graqBmJcTYhM6gkIjjppX6TOcbC46jx1RHNLFhi5VwgShpTZkfPSYbDFxNXwE1T6aOKhpn2vcDV5/37e68BX1lRiNZNV1chfPKbuPbwPC+l/iThNJPi3wOHxtiqaaka+GJuge25u0D6L5i4HK4DQ7ajUFX0sUrb54+C7DbcoqS4Z6Tihr28NcMgtIBilNyN9QlwfjFNTsnwXG25sHrzlcesEnR47efuvQfiaInYDws6nDWMMLy0AdMrF43AsHqsbxKOho2Xc7WR52jb1JSxNSwXPbl/dk2pq3sUY7hE2C4rUYdNI2UxEFsjdnsOrXfZc3L4X23EOBsBxHhumfSykVZbyoKp0h/McL2B6WNivkFdRTUFTLSVLCyaJxa5p3BC2w9Qp7dyFplddipsbjQue1ri1sgzOGw0Soa2qw+tirKGUx1ELg5jh/T2Ks9Qw0tv6DN072WS3hbLdNMJPg9dxtBR4rhtJxVhkfK+Kdyq6EbRzDr9e/t3XPgpsNwSJlRiLmVla5odHSxm7W9s5/svSfhKyGrkxjD66Fk9FJA2SRjxcXB7f+bLzXFWADBaxjqa8lBUt5lNKNbsPQnuFyQmtb6dvj7r0scHXC3R2+AcUqsU4/w+WtlGVrJRHEwZWM9B0AUocco63EcQwDHAHUEtS/4WYnWFxcba9tdO3suZ+HEcj+MKQRkB3LlJJ2AyFefrQH1cxsB6joESxRnlcfRKvduyrftP3f7NfEOBVOBVxp6j1Ru1hmA0kH+65kUT5pWxRNc57zZrQNSV7rhWvg4ipG8N43d5dpSVB1e0jYX/p9lwi93D89ZTR07mV0cjohM7UNtoSPJWkM094SXmX0fvDw4yd9jWHR8J08rWNZNjEjQA/QthBH9V9L4uxqDCMLwV9cznU07eXOSLmxaNbdfK+IPzvc50ji57jcuJ1JK+ifis5zcPwOCQSB5gvYkWFgL3HfUfuubPhUssFLe7sHJOSa2r9jz3F3DAw22I4Y4TYZPZzS03yX/wD1exXlibDbReu4P4kbh18NxT8zC5vSc2vJvubfynqPqreI+HKHhvFIKqZsk2G1N3wMbq0Ea5SeoW+PLLHLwsm77P1/6JwUnsYcFwyLDaVmNYvFmjJ/5eAkXd/mIPTsF9J/DrEHYlwzjFZO4tLppAAT8oDBZfJMVxKoxOpMsx9A0YwbNC+h/h6HRfh9jct3NjBldmb8ws0Xt5WHVwbxapbtv6DyNadEeNvyYqStw/jKlfhuJNbDiMZIY4aZxf5m+e4Xh8fwSrwOr5NSM0Tz+VKBo7/Y+FmzvbKZY3Oa8OzMeDYg30Puve4Dj1JxNSnB8eYx1S4AMedBMRsb9Hj91emXS+aG8O69PehtrJs+T53DDLUTMhhZnkkcGtaOpXrqqWn4dwM4dT+qtnOaaZulz29go4phZ4Mq3BwkklqGXpp3C1mdf/cvLSzyTyl8zi5x6kre/wBRTXs/kUdOON92e6/B6Yt4smLiSZKZwuepzNKy/iTWVH/GU88csjJYHjlvGhbYDZafwehMnE80hDiIqYuGU21uNCsH4kRTM4srXzNyc1wc1ua9hYD6Lm2/Wte4iL8za9P9ndoaum4xwqTnRtGIRsAqYW6Zx0e3z/TbYrxv/DlWcaiw5huyY5mTnQFg3J7EdQsuHVdRhtZHWUT8k8Ru0nY9wfBX2OrwiPiPg8V+FQmOuqoxLEGvyhr9na+dQVOSb6SW3sy+zNHOLitZ824hxOniiZh2Gg/DU4yRm/zHq8+65vCoJ4kwwAXJqWf1VGJ4fVYbVupq9mWYAHe4I6WK6HBMYfxbg9yR/wA0039tV1JRjhbTvZ7k5Jyct+x9H/Fd2XhiiD7h7pbAEa7FfKsHxSowbEYq6lJzsNns6Pb1aV9W/FikLsGZPK57iKkmMZtGjLZfI6WmlqqiOnp4zJLI7K1rdyVy/wBO0/p6ZEbcItfzc+iVdBT4vAypw5nMw/Ejd7etPL1d4vsQvBYphk2F1boJhfU5Xdxey+xcCUUeBYVWUTZi+WJoknltdrXkage1gsfF/DVFUzNw8Of8ZNG6aCWQ/M+5zAf1t/ss+n6rTlcP8Ssj1S0tbnzPhVoPEmGHtUs/qvuvN51JOzI1+aVos4XGmq+LcP0c9NxVRU8rCyWOpAc09LL7vT0MhljLwbEXuOi16jVLNFRMZOMY+Y+TfivFlqcOtGxn5bx6W2vqF87lFr6L61+M9MYp8NIabFklj9QvNcDcMR4lWxVmIgCmz5YWF1uc8fvYfuuuE/Ch5uxnXiU0YuH8MOHQMxCaLPXT+mkieNGX/W7suTj9fzJnU8bzIQbzSm13u6/QHZfV8coo/wCFVlTG6KmigGR0pFyS7QW9rhfGMRoZsOrJKWpYWyMO56juFPTy8WWqXJrllpjpjwe9/C45cOq8rw1zqpg+lr/7qvj3F30PGUVSxjXsbA2OSN2z2m9x+6s/D6oZhnCOJ4q+m55pqnMGtfYkBo/3XI/E1xkxqnnfEInTUschZe+UkbHysIw1dY2+OPsaN1iTXY5FTEzDKoxtcXYZXNDm9bt6H3BXKqKWaGq5GRznk2YG6577W911cIJxWkdgr/VLcyUZO4d1aPBXqsPwqq4cwkYtWU7Kiviby4mnUQgmwJPUrrlm8LZ8/n0/6Lw1kVrgwUtJFwdTMnqGRy4/UMvFEdRTNP6j5W/h6idinDtfWz1NTPUfEHI3P6eZYeq225+y8biFXJNLJJNIZamU5pZD18Dwve/huXnAImRg+qvdm06WBXN1SlDC5vn+fY1wy8+lcEPxapKqlxKjqadt2U9M0Oc39JuQPpoV8/rohK0VkDLRvPraB8jv9l9B4+xeXD+KIpaiMPpqiAxTwuFw+O5H0I3C8hXwHA60tieJsLrm3a4ahzL6exCro5NYo/b9viZygnGmzz66WAYzU4LXCaC0kT/TLC75ZGnuq5MOldWx09Ix0/OtysguXAr0tLQ0XCgElc2Kuxq2ZlODeODsXdyurLkhp0tXfYxx45qV8Uesj4co6c82N8cOGvJe+OQ2yl3Y9NbL5vj9TUV9XJNNM+oLTla92pyDZe9E2K4zwiypr5Y5mBxcKeJmXn2dazj0A8dlw/xRkjwjFqOKjEOaKka1zIyCANdHLzujcllcZbvc7M8k8e72PO4TxHXYeWxud8RAP0PNyB4K7ZhwzG4zLh8ggn3dE4aH3H9wvASVbnuJDWtudm7BKKrljcHNeQ4bEGxC9WfR6nqjszz4ddp8st0d6toOTI5kg5cgOjb3DvIK5srCw2IN12+HcXZX1LaHEWNfnGVr3C4v5/3Xcx3hGKgo/jG1QbCY7tZKblzuzVl4/hTWPJybPBHNDXi4PDG1kumqukjtfQ3G4VC607OGScWF0uqdtNUrJkB0QjVGyADRKyTntA1KpknFvTuqSbJbSL+6BZZec+26BUOHRPQydSNKN1XFJnGys0F0qodgklnaBe6jzm6opitFirkkyDZQdPY6BQkkMgAIsqURORL4g9gpxSl7rELNZDSWm4VuCJUjbdFlmEzhfVLmuve5UaGXqRrASWbnORzn7XRoYtSNXhCy85/dCNDDUjrzVUst+bI9x/zOJUaermpp2TQPyyxuDmuIBsR4KozggpsLbnOSNNwLrKMaOhyb5Ln1Ukj5ZJbOkmJL3EDUk3J8KHNJsL6DRQB01HsiyH7xxtcE2jqpWvpZJhv0WiKEvOgUN0axhq4HQlrJQXaeR0X2/gKsL5A6kqYamFjRlZGyxGmubyvjUNFJ6btcL6DRej4VxOt4axKOpp3AMccsod8pB6+6wnkT2TNcnS5J4nFH2DiOsfLTxNngtmJvduy8zaoFPNKyKF8UeY5pCPyhbUi+9+y4WL/iHNWcqMUOXISHOEl869JJhks+EfFCUMa5oc7UOtfwl/UuohGap7PYqvC6eMJc2fHXSPOfMfmJuujws+OPGaYzc7l5wLxGxBO30uu1UYXR1LTPS0f5YtHmykNc4HVx10uN7aL3GEcHYIzCjJHVQmaKcH4mncTncLEAa9zZXhyJ1Ubv1OPqJKCWo6LcFwqsqGT4rAyrlsWcx7b3A6LE/hqjpcYD8CaaepLgQGxkMsdx2XT4jnh4fwiXE6mpj5kerWOsC430AHW6+dV/GdRX1VDWR4i+gz3fJaUPay3TKNfoVLlKE2qo6cbT49D3Nb+G5qIKipFUPjpXF+RzfRe+uo7qul/DaY0RM9TGyoLdGAXbf3Xj638SHTSwVdPiVdCG6VNLcFsh7x9htcE9V5+q/ELiOqh5L8Wn5ewy2abeSNSnep24fc5dWRPdn0fGeAo8Pwl9Y+rjtGA6QPFg3pofcrFDwFPJTxzOxHD4oni7SXHUHqvmtXxRilbRmmrMQqpYekbpTl97dVzn100xaZJS7IAGgnQAeFDxNytbIvW65Ptsv4ZyGmY+nq4ZJTa97htvBC04ZwJWUgfK58JkBFmXOtvK8fwli3Fz6ekrMPjrq2hp3EFg+U9xa+q+mcOcc4XjbJh6qaSH52ybfQq9OCbalsRryx3W5yZuApHUhcyVpmvcRnYfVWP4LqP4DNSxPYJXt0YTpe/de4EsZj5gcMlr5r6W7qplbSySCOOoie92zWvBJWkul6d8/kldVmR4DGeFMWxChDTHCw0sTeXncLuIGoFtvqvK4HibcAqpmVFM+GSUAvDmnM0W09J7r6RxhjTKVsVFHHNK+VwDuUdQAdbeV8u49xmjrcc5+HxTnLE1kjpgW+oE6AHsP3Xl5MONzeOG6XvPR6fLOUbyLYz0eK/HTmTGiBaJ7GOaLZbnQmy51HSfB4lHLRn40EZmBjSCD2t3CKHE8IbR1oxainlnfHlpXRSWDHd3ajx39luo8fwvC8HinoG1UeNtl9MgsWZTobg6Wt4vdPw5RtRXJ1a4vnsUYrWF3EtDMTfltYSfqp4ziMmKVELzH+ZEXMDm/rbdcPn1dbM6f4eaeUXe9zWlxGup0C73CdfhMGLZ8fkqKaONhLCwG4d5sL7JvFSTrdD1LzMx1dbJUYX8Iy92ShwO1rL23AHEwp4ZKPEea+aVpcZcmYEDTXsvOyz8GycStjiqKxuEOjzSSnNcSfUXt9N1yn4pRU+IV0eGz1hpSXMhkBsZGf5vCUsVxpKmJ6cm0u6PX8N1f8MibhkLM8MZklmma27T/Lr/AObLwWD1TqWrqJ43ZX5Hlpt1uvpv4ftw92DVRqq91M2b0PhuLkW3FwT9l5mh/wCEaLHq9lXU1DKCO4gqGg3cfNhfe9tNbKMMK1XvYSktbpcHQ4GpKLiPiWorMZiY8ugYctyBmtY/2X0MYLwxI4UdXQ0M7iMsUkzGuc4DpmOtx/51Xyfg/F5K3FZnYbK2KeP1NMxF5ADoLe2q9ZNgtZKyVtXikAhe8zSP5drG99Oy7o9TDFHTKG6R5+fBLJO4z2NuNUWCuwiihc+MxNe60QkvmDXG39F4bi2olr8OmbYNzVDGxxtOjWgaBQ4zxPAMJ5UOC4kcS5nqkja7SNw65h37LyUnEs1S/JMAIDuxvfusVgcnrUaOjHljGGmUrPX0dfh+D4bLh+GvBqxBzKipb1k0s0eytixWZ9YapxaJZ3MBy39ivKYfidLE8/DU8ge8W9PqP2XbbXYbBg8NXPXZq01Ba6iyZXsFj6r9tvuolhafHJtHItPuPt/DNZBiLJ5mWM8LuS53W2hC7M8Uc0ZZMAWHcHYr4Lw5xWylqJTSVEtO54u5xOhA7rZjXH2J/wAOnbT4nBIyRuUh7bn6W2XdHqFCKx6bPMn0zlNyT2Pp9XiYmrYGxuy07X/NfR1tz7LkcR8WYFg2INp/i4W1Fa68r2m4YA213EbbABfEcW42xvEKOnpZJ2RRwxcq8LcpeO7j1P2XnhUOyvDiXZrXJ1K5n0k8yfivl9i7xRarsfY5eJqbE5Keqjqo3yCMU5Gb1avHRWcTVtDXY3W4DiLxHG+Nj6aY/oksvkGGYvPhk0ktPHC9zoywc2PNlv1HYjoV1MM4xxKhFYZGU9ZLVMDXS1UedzLdR/50Cxf9NcXcO3B2R6rHS2o+jcBYy3BKV+HTHNM6rMRDdbkjQjxcLuyU38OwTEYWPc7EmU5EWX9BdfKG+V8i4VmGIcQ0hra0UYdLc1Fh6D/QL6Ni2N12B1NZUYXXYdiNFQxsEkj2Euu86XLTYkabd1y9T0c/EtfP4micZex3+9e8vw7DcP4DwplZiRbNi1WQxjb3sTuB4HUrPiGOmsxGKaU3/hj5Q1/e7QvFYlj1VjA/5/EufLmzNAhAA8A9B4XrOE6qhpcGqsTqcZp2YjG1zY6aZgyvNtBbdxJ0uClLpZN65byZcXGC1yVs4f4jytnxqlka7NajZc+SSVHgbGXYNPWTtIzcsfXVdTizEa6gmwf+MR0rGUb8zJ6eAkOcRfK4E9raLy9fXU2J4xPVmoyxVDwXvbBky9Pluf66reEdeBQrauRVv/o+q4O2amwitrMRIjpJhJOYxbPMDcnToNf3XMhwltSwcR8Zvjp6GFoNLh4+SJvQEdSe3/wra+tqcMwmOswWvpMToKeISOlqIiXkDQtBFhYaH9l4is4tOLsd/EsRqCblzIhTtyNPS2q5MXT5W5V67tckK5PVdWesxXiWlxigp6emidGynqo52N2s0XsCvO/inUuqKjCHuDgXU7nXtpqRos/D8+GONS3FsYdQ2hLozyg7OSP/ADTqsON1dXSVeGvxGpErvhmSw2jzANOwIPtqunB0zx5U1wr+6LmseiltRj4WqRR45SVJNgx9/wBl9c4OgqJn1mMzObBTVxDmtB9Tw1tr+Bovj9dV01S9zoJpHOkcXyB0TWAHxZdvhzjXFMMhNNSmGdrGejnMJ5bRqbahX1fTzyrVHn/Rm/YcInuKTDA8/wDE/FUgp42C1FRg2bE39It1cf8AzxpwTHP4nxKypccsboeUxhdo0gkkj30+y8BjfGtRjsb4qmcgyubkhEQDI7fyne67uFNo5KTCzguL8zGXyEy00sd2ABpLrgC9the+t1y5Okm05S2/CRcVFxevl7bcI8rjDgMexCXW3xchBH+sr6TRY/HimIYKKZzOdBE8Pc46NDg3f7LxNZxoKvDK+ikghjkqbNcY4AAwg9NVwMGxWowusY6ikAlcW3zsDgbHQLongnlhuqaKk48P+bH1mrw4Y9iFWKwimwKjlLqh+bKauQblx6NG30XHxDiKkq5aenw5mSipqgSstoC0Ajbt1XIr/wAS8RqGuo30lMNHRvayIuBJ0uATuFycOnw/4ar/AIlXVMFa9o+EY2G7XuJsQ7TT9ljHpJ15+3BOBpPz/JE/xDlE/FT3B1/yIx+1/wC66PBuPx0WCV+GZQ+oqJGmBl7F7jbT2uAubLiP/D3E9Sayd9RURgMc5kLCHDKLaO2WjhX/AIcnxCprscr5qYtGanLW29XW4AI00sF0vFeFY2tqQ3oW/J9Mo+H6mecVuLVGccsOldmsL/yjs0fuuVBxfHWzYtJQkfC0bGxU4H67nV1u3bwFwOIeLMTwwUuF4hWvdTyQNlzQQNa97T0de46dFRwniFNS4kyuxKeupMNmjcGvdAAHknTZuo32XF+juOolQe8sjuuEiP4ikHh3AtDmzPuD00XzpzgCQTay+i8f49V3oqmKoY6kqi6amApwC0N9IvfuDdfP6iY1khfK4OeTdxDQF6XQxlDElJev5Jmr3vc9pwNS1uJQU1HE6NsccxkjzaWPVx/svVYtjLKHFaHh7Dp2ukdO0104975B/f7d181oqytw7DYauGoqoYJXuia6OwuRqdfquvhUjMVhPJZi0stO5r5JIo2lsbQb3JAvffVc+XpXLI5ypo3VSSTeyPXY1XSVvB+OPe71MnYG26nOB/Zef4cxelgMkNewyUNQMlVF2PR48hbeIcTpIsP+O4brpn0NNJCHxyQ3zyXLrknW2y4T+NDUnFBMzIcRaGvEcTbMsLCxJ0/dZ4umkoOKW1/sGqK24T+R9QqfjXU2IRywipjNHljaHf4oN7D3N15PGppOGqN4ke2TiTEGAPLPlo4ujW/0H3Qa+kpsAbPwxi9W2Wgp+bVRzR5xe4sPVtrfa4Xn8Jx6prseirJH1VTiD7sZkiYSSdLWtZZYOmnC+6X83M4R35pfT+I9TgmJTVWBwUWbN8LTvLj9Oq+b8PY3UYJXR1UALm/9SO+jm9QvqVPgtO+j/h9NV1lLjpjdJURPbe7CDcWtbXS1l8qg/h7Jg2sZVsANnNjy5h336rq6bHHzpq7oc5Rk/Jt/OT7DgbqUxumwK76KtnbK4NItHJb1N8bXVFe2jwunmxSviAo453SU8H6quoJPrPgdPAv2XE4KdgTKU0uG4jXQ4lJPenjmGZnuWj0nS9+q4OKcaYhPLJSVlQZBT1OdhbCwZS0nQePC5F0k/Gel2vvRPfmvU9HwbjFVPVYvWVU16mpMYI7DUWA7Bc7FsY/hnHWJOkzOpJXxtlDT8pDRZw8goxKuxk0MfEIgngZiLxDzMrMjhs3K3VwOh1K4mI4jV4biNRTYmaxkj5GyyAxtaXkbOs4bfst4dM3klJrlVX0NU8ftJn0WppafFnRYzQOY/FaNoEmT/rxOGht7f3Cx4xFFJxJ8VOXU8cFBGJayVtuU31Xy33cdh21XLpeKOGsRxNmI4pJisFXHE2NssVmAAXuCGb3J6rD+ImKztxptJWV8tRBymShscbWAXvuOpt/VZ4+nmpJP0MoOpV2QjV1GL4zTVFDBJFQUTh8PG1ptG0fqdbqVDj7Ep21mD1ccpFSxr5GuvcjUW/ouxwVxNiVVh8mC4HSOqHthd6pWtBYD1JuL77LzOP0U7cOoMUqXy1FO9hax4jsGa7X67FbRxpZYuS4tGupNNbe7c9bTNw7jnBGR5mU+Is+S51ik7f6XLtYphU/EtBSUNXcNpZmmdo3dlaRb6kr5pR8XSUmDVGG0sbGmUjlz8oCSPW+hB/8AhdKi4oxykw59Q3EmyzOJdIDEHPAtvfbQLnydJmjJaHST291melyvSb+PMfgw+F+AYS9rXBobVSx7NA/6bfHf/wCVsNa+f8KJIHOvkhYAQdf8QaLyQ4gjq4OXJLmkc7M4mjjNze++69lSOxbhfAqrFq6np3wEguo5oLFgcbB1hoNelvstJYdEYRqmmn8RtRSu7/c87wbi9JkkwHGRnw2rOW5/6buhB6ar1OFYVV4BguOYG8GXntc6mlG0jXNsPrfQhfPG4xAHyvPJu8g6Uo9PsL6L2VTizq1lFiOFY2Kk4dRuqJ6Z1PlZHsLaa330JO3lXnxZHenZPf5/9Bxi2qfJ04IKL8POHBPU5JsXqBZre7u3+kdVzPwxxOonx3E5quXmzVLWue8nrc/suVU8b0mIvq34pR0k1RKxrYZJInOEIB2A638WXoqepw2bAIMWwGOip6uF2SaGOIiwsb5nb26hYzxTWKSmvNLuQoqqlu3seHwbGpMGxieZtpKZ8r2zRnUPbmP7rvHB48I4owbGsJdzMJq6hpYQb8px0LD9zZcWLH8IYBnwjDZbsLXOcH3JPW/dUycSVLKFuG4VyKeJxByszO9YNw4X2N11yxzlLaNXs79C5uL5Z7SPhsYtxjjGK4meXhlNNdzn6B5a0XF+wtqVw8c4odi/EVC6juzD6SoYKaICwdYj1Eef2V2M8ax4nhkeDinZBDlAqM8xu94OtyBtdW8NYDhePVzoaealp3tZma5kznnMOwNljjhNO8i34QQVLXN7Ir/EuslZxeKmFxDo6ePIe264eKwRYpTOxWijyyj/ANXA39J/mHg9V6vH67BZsXp4eIaEienIjnlhmFnxj5SB1BvfvZZcKp8Jq+KYIsAiMUTi5o5lTcPGu4108KseRqCdO19y4bR0vhIp4linxfCeEKOiidNO+lc1jR/7Rc9gLbq3G6mn4Rww4Bhb2uxGdoOIVTd2g/oH0/b3XpaTEKPg81VBikNqyJpbSSQtBa6N3qs2+1idb9gvnxiw6pjBlFdJiElQXSPMrCHsJ3Jv8yIJvyy4X7siEXJ7cfm9z0VdihP4YYTDE8tlbUgAjQjKXEEfsqMUpxxpgZxCnY3+O4ezLURtFjUxj9QHcf7jsrq7BKbC5I8L4gkqqWia109IYrSOJJsWusDt/wCFZ6abCsFqIa7Cq2tdUsfIMhiAGXpm7g/+WIStxdq7u1+w/Di4+Xnm+x4d7rYbYD/rf2WVmpt9l3+McLrYatuKOw59FRYk7mQscQRewJ0Gw1uAbLNw9hVLW10MNVVTRxyH1PZAX5ft56r0VNKGpmTi5S2PV/hQ6OCoxuSZ1mCjFz2FysvCNVT43h8nCuKyBokJfQTu3jk/l9u31HZdeHA/4BhmMVlHJUVVHLTiHm8nKM2a2xN7a7heRZhkIOajrpXzsyuYyOmfe/WxHZcCcckpS9arb0NIYrTpnb4Ao5sD/EJlHiUZZLGyVpPQjLcEeCB+68vj2STGq6WIBsbp3OY0NtYE6aL6JjFZPiWExYjQU76jGsNBjnmbA5oMbmm7iDb3t0N14mHBnVOAS4w7EKbmNlDDSuNpDc2v/f2v2WmHI5PxJbdiVFd+eCHCDjHxLhb7kWq47ke6+v8AGDMExjEhw7XhsVRPBzaea2ofcjTzpt1XguHuEqgcSU0dPXUUz6aRsrix5cHAAHTTynxMyTGcbqqt1dTU7qS0YE7yx1wTqPYrPNJZJpL6+gvB1zTTql+Ty+O4FW4BibqOuj63jkt6ZG33C+jfjEITgWGZABIXi5A1tlWycU2OcN/wziirozXMA5NTBKHXNvSfBPUdV4zjPF6jGqyGlfG6jjgjabVQyEm3np2ShlllnG1vHl/sEYOTTe1X8zxRb0P7L7rhMmHP/D3Dp8ZjhfAynja58rQQ3Zt/C+Oz4VNAymPPpJDUgZWxzAuFzbUdF7niFlZh/DlFwxPy21b4WtezmjJYG9yfoq61eJGKT7g8WppXW/4PP8bcHTYBP8XTAy4bKRleNchPQ+OxXuvwwjgd+H9aJ2tc0vmzBw0Og3VfAzsVjp5cCx+i51CLRNkc9r8pcL5Drq22x6be2fHKmn4FwGqwmnzn4yV76S+oLTbM0m/Q6a9wsHnlJeC/M+z9V/wyyJyehvfY+TzD8x/bMdumqjA90NRHLGbPY9rmkHYgroSYTXiqNK6mPxLnAcoEE3Ow/dKowXE6SWUVFFMw05Bl0uGa7kheqpxqrNNL1Wfa+IZcMbwvBLikcLmzyiMukbe2a/XovknFPCcuEE1lDmnw52ubd0X+rx5Xd4txKqxLCKLBoI3ySl4c2NouSegH3Kx8NY/U4LUSYTjkL/hmeh7ZW6xeHDq1ed08cmOGuHzXqvX4leEopxfxN/4JW/4gxD//ABRb/wC5YvxVIfxdOALENAP2XqsOw2h4UrqnG6eTlYbWQctl7lsT73FndWnovB45LPjmL1NXDDJKHvdlcxpcHAbn2VY5rJ1DypbUZwxO3L5HBy+F99/Dt7WcE4Y536IHEj/3FfDZqKpiiZI+mmY2UXjc6MjOPHdfT8MxF+FcG0McjZI5G0745WPBaWkk2BBR171Y1XqEsLyJRRLFMIw/izBPjaEtyEuLT+qnkvqHf5e4+q8NwxQ1FBxzhtJWR8uaOpGYdDobEeCreFMfrOHMRNQGOfRyuy1EJBs4dx0zBfUKvCaDEX4bjdF6nQvbLBINCW/yHxrpfYrnlOXSpwe8GnXuKyeV1L5M534uEnhmlLSbGoIsNSTqvO8PcPy4BhZrpY2nFaiMuY1+gpmW1J7H/wCF28Qx3Bp8RpX4lKHtpDLLBCf1SXAAI7jXdeT4t4kNYX01I4l0pvUytvZ/Zo8BGN5ZwjiSpdysONwilLsex4AxKHEo8Z5IcKZhijaSfU4kOu4nyV1scfT4njb8EmlEFW2JtRRTN3DhvbyO3UXXh/w2qI4cFx4hwzZoi33AK53GOKvn4hp62mlyzwMa5sgOrXA3SeFPqHFdiXjlKbyfzsfQafBGYriVJiXLZDiuHzBlZENnttoR4sbg+4Xt6Z2aoezK4BrRrpY3XjuG8bhxukhxmnLY66mby6yEH5m9R7dWn3Hdezo2wSXq4HZmzNaQfH/hXo9CvEmk/ajyeb1Lf+R4z8SMHbitVhrqhwZSQNkdM7qRdtmj3WWKngwyXD5a9gjq6omKhov/AKEYBJJHcganpe3de0xtlFFTjEMRP5NEDLlOxNtPfx5Xw1vEM+L8fU+JVjrjM5sbGnSNmU2A/v3W/U4XqlJ/IvpsjlFRXzPUVYp/+HcUosQlMVPWYnIzmnZl7W9hdeLqsLqa4PwDEmkYxRsJopToKmIfpv1NtR9lLirHuZg81DI4Br5TKATuSVTh3EFHjmB/B4xVmlxXDxnw+ucTd1tmk99B7+658Mcihrr+ev7ndJxT0vudDhWN3/AeM08mZrjVFjm9QbN3Cxfio4u4iY0NNxExjW21Oi7FFjsWKcMT1kcbYq3mxira0AZ3i3rHuLLoQT4fC6TiDHGCoxZtoqSkda97XDrdPfosVOUM7nJeu30LlBPEq/nBw+G8IpuGHUlfjUfMxKocBBStFzCy+rz5A+2269EZocVxrGYsQin/AIfT0zZGxOcQA47ED6E/VeTnxYsx2mdLIJa2ednxMo1DG3Hob4C602MN/iWMODLtqoeW119sgP8AulnjOT1Plr/fYqEI1SPmzi4lxIOpX0Th6pqaH8Lqqqw+V8VSyqcWkC/Vo/ovmzqiJpIc6x7L23DPGmBUHCT8IxCKpdKajmXjaLObmBPXwu/q8U541pje6OLHOCnuy38UYpIqzC2VDnSTiibzHu3c7r+65/BtDJxA2fBZWk07W81s2/Jd99j2U/xA4swbibFPiaOSaGOCnDWB8esj77DXQe/ZeOfj2ImCKGOcwsiblHK9BIvfUjU/VPD0+R4FCqf4E+ohB6m+x9ZGG0eA4XLSYTWskxWL0vaHB0oB+YgfpAXzWtrWxvkGc+onO8m7nFcSOtqo53zx1MzZn3DpA8hzr73PlUySOfbM4my1wdE8bblK7MsvXao0kevr+LZI+F8OwnDJnxujDzUPAIOriQAfqvIzTPmeZJHFz3G7nE3JKhdC68WCGK9K5OTL1E8nIkITWpgON7o3BzHFpBvcL1Yx2TFsCqG18tTPiNO5phkc8CNkWgIt3uV5NFys8mKOSm+Ub4c8sT9x7zjimp6SppKenEeaKjhbM6Mg5321J8rypF1z2SOF7OKvZUECx1WUMLhGrs1nnWR3Rosgeyr5l7EbI5osehTpk7Fc8xabNVBked3FOU5nXGig3stopJGEpOwJJSUiEAaKiCKLKSR2QIGuI2UnOdbdRGye4QO2K2m6QvZSvol0QBFMIshADSTASTEJNFkWQAITRZIBIUmscQSGk9yAhFodM2ArtYhSYNDhlP8ACVNY/EyAZopIwIx3sfsuGDY7ErRTva1xLhpZc0k+UztxtLY0wYZXVEM80FJNLFBHzJXtboxn8x8LO3wbptqZW5wySQNeMrmhxAcOx7hWxND9RH+6TdclwjbHTwyTOyxMLndmi5Xdwejkz3fGQSfSXC1liwsGOsjyP5ZcbXB3B0svpXFlNR0U2H/COYx7oiHsab5trFed1Wdp6fU9TpMUU02b+G+FXYrRPjlAFwC15HynuFo4m4JZTMNQCzIW/pbs5T4Y4lZhVO/4hrgG6ODhb2IU+JOMoKyMxNLeWPmYDcnzdcmrF4W16zV/qv1G3sHzGvp2xSlmU3HUiy4z5Jc5a1zsp/TmNl2MVrWzSl0T5C3b19l2/wAOJcCjrp5McdAdLRxzNuHX330XTCWmFyDqIp8HjmVFTFrG97XDazivXQcUcRDAxjkEdLLS0MrIpg+1ydALjQ9vuud+IBppeJKl2FUgo6Q5WNbZoa5wGpAGgvcLzDqSeozhskQLB6ml+W/m3hdcJNpJPa7PK6nEpLzL6ntMZ/FGfHYwyvwehIikY+NuUuBsbkOJ6HwvH47WMxCrkq2RxQiR1+TCzKxngBct0MjHEXa63VrrhVnMN9r9FvoTnq7mCnpjpGXHYph9jZXQ/AmtiFR8S2jLhzCyxkA626LWcFqammxDEcKglkwmklDTNM5jXgOPpu2+58XV0jE52dMO8rTJFQNoGu+InFfzSHRcscsMtoc173v0ssgICVCo9hwnxzinD0BpaeYyUZJPJcNAfB3C9TwkRV4Pi+K07YqdjJfUwEku0ubeNV4jhfBsLxf4w4pjsWFtp4xIwPjzGbXUN1GtumpN19J4V4Tpaqmqqfhvi6Oow+oux0ZphzRpvYkfewXLl6dS9lbmuPJolZ7LDayqxzBzTU9TTNkfTANY8EF1xrf/AOF4/E60cHYw2LF4m55Yw+J1OTYC9jbbXRej4S4exbhfGRBVV0FThpjIjc8hjsxPQak2t36rm/iHiWFS4uyjr8KgrXVdII6eqEoJpiXkFx006EW3tbuiWHHOuz4FDNLG3W6Z5up44iqa2NznSinaDYZbO+6ML4exPiWI1VLSxmG5Je4/Md9e910uLeDMG4dwugxGlfJUxOeInte6/MJBIcCNrW2XX4U4npcEbFRVJY2ilu9sjbnl++izhhwY8jjLY3jln4flPleJUbqSsmirqcQvF2hm2Q+R/ZaaGkkhoX1rcKkq6eIBz5XROLAOuuwX0v8AEXFeFqjC6et5dHiBkmDHOglaJWtsSSLa9ANe64fCv4mYZhWET4dVUT2xRseYCz15r7NcP7q4Qg01J8eg11Uoq4rc8jgPHlTw3XVEtDRRcqbdjxrbpqsHE/GVdj+LRYhV0VMwRsDGsa3RwBJ9Xfcrnx11OKGqpJKGme+pLMlVISHU9jqRboeq6XF3DdDgFXTQsxeLEIZoGyZ6a3p731O+4VxhBPdCfUSb1dzm4vjFHXOD6PD20bwLENdcFcySeYAAu03BC6/C/ClfxTVy0+EMa90YzEyOyhrfJWPiKhbheJzULqeemnp7MlimcHWfbWxGhB3B7FbRxxjSSFPqZydtnbwD8RcZwSKngYIKiKmLjE2Vmxd3I1O5XDxbHqvFJJZJxGHyyuleY22zOcbn6LkOKjdOODGnaRD6mfqWCR7XBzXFrh1BsVY+rqJW5HTSOb2LyQs/TdF1rpRhrfqWNd33TjldFIHt+ZpBB8qrVMAnYEooakzpU1cWStmYMkrT8w6nulWV81XUOmndnkdu6y517LRDDLLG57YnuY35nAXAWbxxTs3WaclpQc138x1SMhO5XpML4A4nxfDP4lhuGGWmIJYeaxrngEg2BIPT/ZcfG8DxTAamOmxmjfSTSxCVjXkG7SSL6HuDpuE1pfBk206ZiJUbqN0dE6Cx5rqQOqhfdAeBpZOhpmiNxvovS4XVubw1jNA0XdUmItFt7OuVycLwirxFwZRQve8jTNZocezSdyuhWYXVYVM6jxOhnhrI2B7oy6+h2IsbELmy1LY7sM9PtHU4RxDBsLp62PHMGdWyzMAp33H5Z1+3TUa6Ln+p80ot6HSZoze2XVcymmopJG/ESuazYusSW/RehoKfgt1NG/EsYxH4jO4vbBB6cttNx3t/23WMoNv/AIaxzRgrPS8XYnhNfTsp201T8XUlvxNQ43iGVvpLdTqNNgNL3XjaXD6c1TKWrq+U94ubN0t4Pldrn/h+ImNfV4u6RhYS/li+vzC3/n1XJxmfhh8cJwaWtEmvNNRGLeLW/dZY8UoR0q/oUs2O+D00+JUslDWUsVc5sL6YUjIXNAETQRc76k63XK4NlwXCMafU1b4qxkLS1sU7LtffcjcXC8uaik19Tj/7UNq6MXzMcfonDp5RTSb3CfUQlzE9TxRT4TXNq8SoZRHK+7mUzMrWMAOwCjxHjmCYrw3hlPHQStxenaxslWTpkAILd9dbdF5R9XCA4RjR21xqFV8S22t1rjwyile9GU8sJbLb5m6BlIXtzukN97EaLdRNw6KWQCaRjiwt9RvuPZcI1DCOoUBO0a3VvFKXccM8Y9j3vD2NYfguH18EMdPVNq48rnVLQHxmx27jVZcJrI+G+K4ap9poIm5nZZQ7MHN7j3Xj5HviyGWN7Q9uZmZtsze48KLagDuo/TXdvkP1EP8Ayen4hfBi3EFXU0dLTYZTvykQ8wWGgudNLnfRcwRtp62I8yORrXNfnY643/quS6o1tYoE9hYXWixSJWXHVJfc9Fg+KT4LjzMWpBDJJFKXtZKLg3v/ALqfE2Nz49jJxWaOKGWQt9MWwtsV5vnkbklL4k5uqfhsnXBS1HruMuIo+IKilMdBT07qdrmunj+ae9tXadLedyuHHksWvdYeFzDUHXRPnXGqSw1FRRcc0YvZHu8QrcHxTlVWJVF5ooWQhjXEEBo327roVfFmH1mF0+EYi4TUNIwGIC4LrCwFx40XzIy63CbZr76LH9HtWpm36yLryo9/xPxTQ4pw/R4HQwxQUsWV+d7XOfGRf0gleNa1jJmM5zQHgBzwD6L9Vs4Xw6lxvF46KtxSLDoXNJM8ouLjYC5AufJV+D4DR4jW4pTT49R0Yog8wyyj01NiQMuo0Ngep1GhVxhHGmrMXNN2kSq6yCXBKXB21LHNp6h8omykBwdorcB4hxDh6KpZhlaxrKpuSVpjDrjUAi/XUrktpcOPD8tY/EyzE2ThraHlEh7Ors23f7eVzeY4aqo4000Esq4cT2OA8SvwnBMSw2GWICvPLe6SPNlYWlriPK4UsVFDG4QzulfcZZA0tA7iy5RkuuvwvU4XDjlJJj8L5sODvzmM3IsbfQG1/CfhabaYnni/8To01VSYfg87Y8RbPNiMBZLAInAwEOFrk6G4WLC8ROH1cVTTyuZNEczHsOrSpcYT4LLj9U/htjmYddvLaQR0FyL62vfdcQv7JLCnfvD9Rstj3tBx/WU+Nuxipm51W6Ewm7ABbobDz2Xma+tbW1tRV1EhdNPI6V5y2u5xudOm6yYfV0cLpzXUPxbXwuZGOcY+W87P03t26rG19m2PREcKXAPOn2R3MLxWLDcTpqlocRC8OuN1inliknle0khzy65FiblYA8G56pZ1SxJOwfUWqZ6al4jngpYKZ9RPJTU8glhhc+7WPGxHbcqzGeKqnF61lZW8uaYNDczoxo0dP/O68tzCAoh591P6eN2NdRp4R3qSsw51cJK+J/wrnetkW4HhWcR4nSYliRqabmhgjbGOZa9miwXn2v021UngtAJIsfKPBipah/qW400dbDcalwuUz0c1RDP8uaM2uD3W2biqpqMPo8Pme80dKHARZfS699T5sbLzYcOikHOc0uDSWtsHG23ZN4YN20R+oaOhBPRQVL5G82RrNY2uaPUfK0Q4wI44WMDrskc9xtrr09lx86us0Rsc193G+ZtrZfqlLHF8lxzyXB0aSpwwVjHTioiizZnhjbm3Zeixjjyauw6vpG1dQ9tWQx3NYLCIbNHbfVeU/h1eMN/ifwkooc/LNSW+jN2usZcoeGEpKXoLx9qaRvpIqeV4+IqTCCbXDM1h3XWw2ujw6HFKeKfmCrpzAHFpGhO68y6U9DspsL5JA1jrvPRVLE5cscM8Y9jRNEGSFrZGvA0DgNCvXcH8W1WA0z6ASwOpJn53Mmju1rrd99bD7LxBldsUuYWm5O2yJ4tcdLF4sPQ6GIRMfM6dk0TjK4ucxjcoaSbkAdB2VVHHypmTl7CGPFwDrusnMuDqln91Si6oHkhq1Ua5LyVUsgcPU8kfUrv8IzQ0WMU9VVtZJTwOL3sdYhxsbC3uvK8wdypNlPQ7qcmJyjRUM0U9z6DxiMOx/FDilI8UueJrXsaQ67h137WH0XB/hVVS07KymMkjBLy+Y0WDXbgb7rzheTqCR9VJs8jWFrZHht75cxtfuso4JxVatvgarqMaXlX3PTcU1kmIQ4YZHcyWnpjHO7NmOfMb3+llwoIpHOAYxxPTRZRI4Xu467+U/iZsmTmuy/y30WsMbjHSiHmjeo9hxFX0dTwth1LIys/jNNK5tRJNKXgtAOg122t2sfdeTDJCMwZIWjQusbKr4iQ3JeTfe5WuDGsRp6ZlNDUubTseZGx2Fg4ixP7IjCUVsLxIX3NlXi1fV4VDR1lTNKynIEDHuuGNt0XPinmjILZHgg6ZXEKE9ZNVSulqJC+QjVx6pRVcrH5mOsRpsmoNLgHkV7M+mcB17qvDsVwnH8UlpMPbT58sm7STqRcdNNO5Xz0VdRTz56aqmjId6XseWmydRjFfWcoVNQ6URAhmca/U9fqtH8eldzzLRUcj5WgB5iALCOrbdVlHHKLbrk0cob1Jnrvw44jr244aKqq5ZKWrY7mtkOa9mkg3Oy8Uaqojnc+CZ8dnHKWu1GuiQxOUSF8LWQki35YsoCpYYwx0LG/5huhY2pNtD1w7Pc9twHxFjLMcpooJ3zumIZIJTf031NztZT/Eqjq8Px91RHOyVtUOaBG2+TW2v2XksOxeTDJ2T00bOYARmOuhXWpuMZ4rGWmbI4uuXE2Nuy5548incY2vQ1Tg5atVMjhPEWI4ZXU9VZjjC7MGyxAX/a66f4l4nLVcQMnIjzGmjIs24FwT/defxPGIq6VjnUgjY39IeSSTur8YxfDsSq+eKKdreU1jQ6a50+nZUoytPTXuCTg3ae/qUU2O1TIxHy6RzGkH1UzCTbubXX0TjHDsR4jwGixuLDYoJYKMy1DHemzNxYHfQE2XzaSXB3P/ACqeqYMpzZpARf8A8uurWcV1FThtPQNqqtkLIORMOZfO2+g9rJyhbTiiJJumpK0cyDiOrpockVPS3vcSGMh4I2IN9x0XaxCqfW/h7HNNFTOeyv5ecNJk2LjqSdyV5WXkGQGMyZDa+a11vq8Qpzg38Opw8M+J53q32srljjcWl3JWpp6pHOjrSxwdywXA3DrkG/uuvhGOQtxWKfFKN1XC+QfEMMzryg99ddbGx3sufT0lDMy8mINgdlc4iSMnUDQadSlhNZJh1fT11M4Nnp5BJHmbmFx3C0lGElwZqWRbWe24+j5GNvrcBw6Skp6ARsdNTAhrX2uCSNBuAvJvxRlTVy1GJUz6qSU3e4zFpcfou5i3HGI4hSYjSF8TIMQkEkzWs2sGiw/+0LyhDQ64OYe6yxQ8q1cjuUdv+n1DgnFcMxTBa3DMbpqmopqaMTxxyTEsYxulhsdD/wCBeIbNNh1dOKGeeJnqY3kyaFh6X6haeHKqmpY8QPxAa+ajfGGu0uey73AlXgFTOIuJmMaIWWhe42a4dnW7dFkk1JpcGkloi5+pyIcUbiDaCjqji81XBljpMkrAGm4y9PbU9l6niVlM3B5WYnVT1mNyy3ZMx35fotcWFgAB4vdcd1dgNDXYnVYffmgubRyF5bymnQkDqey6jOJeFoKrCKqCGNnwTJGGK1xKXCxcSfvc66rOW7VL7Dhq0p1+EeJ/j0nwcdDNUzimZLz25GNJDu4J1Xt+F+Mv41jhpsQxeeKCqjbFYUzW+obWIvYm51t9l4jimKDEayqxXDIXNgfJeSNjfRCTsLj2WbBG/wAMrKXEauYRRRO5jcgDzmbqARfS63lhxThdfIlqcnUl/wAOtxzS4ZQ8QSjC62aZgN5Xy/MJLm9tB4WfC8d5JLpMWc0iB0LWvpA8ZT9f3XmMUxB+IYlU1slg+eV0jg0aalY82u66V01wSkYvqdLpH2zAsTwbEeFKemxLiKlojSExZGwhj3NtoTcm9+4H7rwMuNy4YahsT4ZOewtvJGHXadnDsVwWTYeMDkaeecSdOMpsOW2IDe++a/0ssUs7pAOYSbCwKiPSQ1N1/wBE+o0xaXf7H1zgPE8TxqqlOGUGEl9NRcuW4MRcCdCbA3Oh8ey5ldx5xHgFeaRlRDEI73iYBI3XXr1XzmlrZ6VznU80sLnNLS6N5aSDuNOnhUvkc43c4nyVUejjGepGM86lBp9z3uKfiXjOIx8qtdFNCDflOYA12ltbdt1yuE8+MY5HTsqaOkmEb3cyqfla7Tb3t/ReSL3KtxuujwE00c0c0ovY2VdS+apdObXzaDcLPzSXFzxe/ZUF3ZF1soJKjOWVt2djDMZfRMfE4OdE83LQdL9CttRxZI94kbTsfLkyGWS5IHZeZv3XqsL/AA84sxNsUlNgk4ilaHNklIjBB2PqIWUsOLVqkaLqctaUziHFKjLZuVpzZg4D1A+Ck7Fa4sIM7tb3PXXde1j/AAf4ucWNfTU0eZrjd04s23Q2vqen9lbQfgzxVV08Er/g6fmtLiyaQ5mdg4Bp1P182TvET4mT/wBHze9zqokr6Fxt+GU/CmFUtTLicVXV1EwiFLFEQSSP063d22G4VeN/hpU4DwY3HcVr44K17m5aBzdbE7Xv81tSLaK1mh6mThJngUlLIbFe/wCAvwxq+JaOXEsSqThmGtb+XNJHcynuASPT/m+ne1ynGKtmaTZ8+DSdlPlnZap4BT1MsTXtkDHloe3ZwB3C7PCPC2IcWYxHRYewtjBBnqC27YW9z3PYdfuUPIkr7D0tbHm3Mc1RXruP+GqbhfHP4dS4gK5ojDnPygFpN7tIBOun7qPBHBVdxhiTYKUGGkYb1FW5pysHYd3a6BLxY6dTG4NOjygBJ0CsZCTuvtlF+DND/F5DLicrsGYwASDKJZJD0BsRl8/Tyr6X8IMIp6SqgqayWbE5y80TQ/KGNGxcOu4v72HnCXWY13LWJnwp0ZG2qiWm2q+81P4WcOvpIcGw+cyYwzLJVV2c+hl9SWXt4AGvcqjEPw+4XxeupsH4feyI4aGuxSsEt3OYb7XuC8kHsB9gl+sgNYXR8NAXSGBVzsAOOZGfAio+HzZxmz2vtvay+8u4T4GxunjpaKOlbR4Q4CqnhcGvkGU2DnDUgnc9wbdVOqpeD+K5wSKKPCcFNpI4/Q6S4s3axDAdu5/eZdauxUcFcn51YS0eFqrMOrqWCGeroqiCKZuaJ8sTmiQd2kjUey+tcUcY8LYhxfhrK/D21WDUMZaAyIgknQXbpdosNPP0XnvxW47bxRJBRUMWTDoPWzmMyvLtRrrtbotIZZSa8vJTxaVufN027pIC6jkJd1pGHVxovjRR1BpC7KJ+Ucl+2a1ldw/R02I41RUVbWNo6aeZrJKh40jB6/8Ac6L7P+KXFmHYFw1Fwzw/DCaaWLlXaczGsFvlN9Tfr3v1WM8umSiuWaY4avgfCD1UVIndRutkZsYV0FNNUyshponyzPNmxxtLnOPYAKhfeuC28G8D4JTYm+sgxLE6ljZBPC0OfFmAGUC/pAuQSbE637LHNmWJL3mmOGt0j4dUUdTSzGCqglhmabGORha4H2K62McH4/gdLFVYthstLBKBke8g/Q2JsfBsV9X4f4g4WxKvq+KseqYZcWZK6GChe1oaGfoLQRcm36idNtFz6rjbCOLuJY6PiqWWjwKOMvjhGxlG2cgXta/1ssf1E26r4m/6eKtvhHhOH+AOIeIcKnxPDaVjqaJ2UF8gaXkb5Qd7LDgHC2K4/iTKHD6aRxMgZJMWHlw36vIBsN19S47/ABML6F9DgDuTA5rRHUxOsXN6i1vTpZb6D8Q+G8M4dczhSlbTVfLa+WGdhAzaAlzr+o+fCj9Tk06q2H+nqo93/Nzw+J/hLj9DicWH0xirjIMxkiuBE29ruvt+90+PfwyHCGGwVYxZtW6RwYYzFkN7bjU3C9VSfixQMw8ikojBjDmuElQ8B0chF7a3vr52XlsP/ER1NxlJjeL0UWItdAYQ0WbkOnqbe9joR7EpQyZ3ytx+HCKtnS4e/B17sMqK3i2udhVmgxMaWEAW3cb/ALfuvHYNwfWY7xAMNww54DMY/jXMPKaBc6kDcgaDqu1xf+IOIY9SS0/PMdFKxoFJYHIb3+a10uC/xNr+GsHODCjgnpnTZmyElr2Bx9Q038Hp50tcZZ3By7+gpQhGo92e1xvg7grhThM0mMRsdixjdkqLvLpJLbjoBtp/XdeG4D/D6q4lq4Jq9s1JhEmb/mmsFnkfpbfa+utraEbrz/EONTYlUOMlVNOOY94Mji7LfoL+wXYwH8RMbwrBYsFbLE+gY8kNdHdwaTcsv2vc9/NtElHMsdp7jksakoJ/M+o/iDjOBcPcNjh2Ggglknp+VCYmNDRbTMbbG/7oXweuredK3ll+Vuxcdbk3KFePDJR3LWeGPyx3Ih4Dco1Rm3Xtcel4eljIo8CjppCAczZnae2q8dLkvZrbC6MeVZFdEyg4bEA7VaYZg0WeST4WVSaRa6tqwhPSzcatge0xgtAXTfjHLLH05OYEG7tbLgNIvqFqnqGShoZAyOwsco38lYzxRbVo68XUyinuehdxZiU8rH1MrZg0lwY9oy3OnRYp8Tle9znOve2nQK/g6nwqpxMfxiN8sDR/hhxaHHzbVer40wzheDCY34bhwp6g6teydzrj2J1C45PDjyaNO52QnmlC1weDlqnyC9xr2CpfUTcsR5iGg3+6GmMOs7ULr0NVhUT2mbCIp7D1cyZ9j9AV07RXBz65S7nFB9eSR5Ate97qzDqeknme2trHwR29LmtzXK04rNh753mloWwtIsAJC4fuuUXgbNC0jco7bGEpKL33FPGIpnxslD2g2DhpdVerupl4sRYKBdbotlZxy0t2iNzfTVbgM9BlaXhxdqOhWMG2gVsdS+OMsabBKSb4KxOKe5sqYo20rZAPUbXJWEEX0UpKuSWMMefSqmnVKMWluPLOMn5S5rySvR8K8S13D1e2qoSM+zmnUOHULzTH+F1sDxGLD8RhqnU0c4YfVHJ8rh1CTbjuiFTPS8X8d1XE2KQ1MLXUccMQY2NsmbW5JN7DXX9lw53PjDpG1hc8kHKCbu+vVemxbjTCZ8ShrKThTC4mxx5eW9gOY+bAA+NFhn41pJJc/wDwxgzfAjK5abdpFRdKmYaziLF6nDKbDpsQfJRU7g+OJwHpPTW1za53UK3iOsqqcQ1EjA2MenK0NWvH+LcPxXDKejg4cw+hfE7MZoNHO8aAae5KlwTxDguETVL8UwKmxESNAbzbOy97BwIT0WrkhL3HkTOSSSd9yoCc3vm+i6nEM+GVOJSzYZh7aOB5JETZC4D27Dwt3DuNYHh2HVcGJcNU2IyzNytmklIdH7aae4sfK3i1V0Q0zzwqbA5o2uBFtUQ1IjmbKYY3hv8A03D0n3SkkjLnFkTWtN8oufSqtL7LRJVwEW07R6fCeNKjCuIo8WoqeKjiORs9HSflxyNGhHud/dcrijE4ca4gr8TpoZIYamXO2OWQvc3TW599fGyOH8QpMMxaCsq8MgxGKMm9POfQ7S2u/vqCrarE6OaeofFhNLFFNIXNiaTaO52HhT7L2Rahre7o4RS2XqaDHsPpaB1LJw7h9Rc3Msl8/tfdcOd1PI9zooGxNJuGBxICccjb3jQSwpK1IxoAVwaw/purYzCDrGDbpdW5EKFsyqTHlpJuugJqYaspWgjrmOqqkfC8EiIA+CpU77GvhpbpmVzrm5W/DsYrMMD/AIOXlh4s4WBBHsVXFLBGPXTtf7kq+KemvmfSRkHopk01TRUE4u1Kjfg3GGOYbnp6LFJoYpgWvbm0F+oHQ+Qudi1dU4nOJq2skqnsaGNdK8uIaNgLnZe74Y4owWgo208/DlDUNGmeSNr3b67hasZxnhWsGvCtFE7a8QyE/wD22XP4sYu9Jo8cpc/U+VEWUSdV7SokwD4cxR4QGtzXzcwlwPuubUtwd1LM2KhLJXD0yGUnKfAWkeoT7Mb6Rpe0jzrrX9JP1SA7EJGOQE6GwSs/sV1HHweu4e45xrh/CqjDqdtNPTSA5BUMuYSb3LbEb+Vw8SqYpKaknjxGrqayVh+KEwPoINmgOucwsufaQsIEZ91WY5Bux32ULHFOxucuww8turTVOdbU6b+Vns7qClld2K00pka5I3xv5rSWgixSJtpddDBXwMo3RVML3OL76dl6bCqfAnFpqcJnl165rLiy51jb2bPQw9NLJFNM8Re5TuTde9xGn4Zia5z8DlhI3Od+i4Yl4dZKT8I97Ts0yEWUw6pTVqL/AJ8y5dG4+1JHni7027KF/K9K6fhzUjD37WtzisE/8ILrwxSMB/TnutY5r/xZnLpmt9SOSCi4C7FO3CXvyyMly9w5bzBw1kN46jNfS0iUs6T9lhHpXJWpI8yXucBmc4hosLnYJXuvR8nh2O5e2psemfZNzeGC0ZKesa7vzf8Asjx1/wCX9Cv0kl/kvqebQCvQRUuByPJe+qawakAi4H2Ww0HC2UkTV2b/AFN/2Q+oiuz+g49JN8NfU8oEl6T4Th1puX1mXtmF0zTcK5SQ/EQ73b/shZ4vs/oT+lndWvqecaLnU6dU7DWxXTNPhea7Zp8vQEC66lFh3C74z8RV14k6BgbsnLNGKtp/QI9LJ919TDjNBgsH8OGE4u+q50AdVmSEt5Mn8o7/AL276rHXQUsMVMaepgndJDnfys14jc+l1xYkeF1p8P4ea/0Vlby+7mturIsL4YIcZsQxAdsrGqFnil3+hf6TIvT6nmNUwdbkrsYhh+FQ2+ErJ33/AJ2Bc9kdOPmkdbsAtI5FJWiJYpwdMoBF7pPdfZamwU5cAZyB/p2XVocLwGVp+KxSpjd0DYR/ulLJGO7v6BHFOfB54Jgr0FXguEsv8NjD3/5XwW/e6zQYRSyShj8UYxp68slJZ4NX/ph+lyp1X3OQHaIBvdejm4dwtjSYsea93QGnI/uqKTBKKao5cmMxRN/mERd+yS6jG1f+mP8AS5VyvucLN0RfsvX1XCOFxxGSPiVr9NA6kcLn7riw4RC6YMlxKKNpdYvyEgDvZOPUYpK0/syf0uVPg5XutmEQ0dViVPBiVWaOke/LLUBhfyx3su/JwdTlmeDH6aTvmiLf91zxw61suR2KUrQTuc3+yS6nFLh/ZlPpMy7HMr44Ia6phpKn4injlc2GfLl5jASGusdrjWyovbqvUngwGHOzGqNzv5crtVzTw+9smQ11Lf8A1H/ZOPUYpcMX6XMuUc+KONwuZmtPY30Xa4TOBw4s9/EkHx1EyI2hjlcxznG1iNRe2ulx31stcHA0k8HMjxrDr/ykuv8A0XNquG6yjmLXT07iNnNf/wBlC6jFK0pbj/T5e8TkyFvMfywWszHK0m5AvoLoY9zWuDHEB247r0OH8FYliLObDU0TWfzPlt+yy4hwxXYfKWTTUr//AO3LdWs+JutW5P6fKuxyG33X0P8ACTBYMVxKrNThlJXtZFoKl9mxm+9rG68rR8N1lSLsqaNp7PmsT+y9r+HWC4hhvEURqa2KCkex3OMFSA52mg+4C5+ozQ0NKQ/AyKLbR6ilmZiHET8Co8Gw5lFHcVFBLYxF7XavaALA/TovG/i9R0tHX0MNHgcWGtY14fJDHlZM7TQEAA2H11XUwGanPH9Q7JJDhjpHiCRs/qB6OJvfU3O/Vc/jzD8axfECw10MtBTyPFMJqluaxO57k6brjwSjjypN135/m4eFKT2XY+dVE0kzy6V5cbAXPhVxFokaXXIB1ANl1f8Ah3ES/IBATffnNsrRwljBdYQxEfzCVtl6fjYkvaQv0+Vv2To1mCYfiMVHJwxUtmkfCPiIKmVrJGy3tpe1wbqur/D7iymo5KuXB3mnia975GTxOAa29zo6/QrnP4ZxhhIdTgW6iVv+61M4X4kZT5oWSGFzSMsdSLEHcEX6qI5ccf8ANMU8OaXEaMNdw9jeH/DtrsKq4DUkCAPjN5SegHU67bpYrgOLYNT0s+KUT6ZlW0mISOGY23Bbe4Pg2WieHiJj6d9RNWmWmINO51QSYj3brpsNlllocWrZi+ds9RISSXPfmOpud+63jkx07a+pk8Oe1t8Tn212QLjqugcGxQ+kUUhtr0Wyl4O4hqo+ZBhxc3zKwfsSpebGuZL6mng5F/iziB1uqA7uV0Kvh7GKKXl1OHysdfwQfqFKl4dxmsLhS4dPJl3sAP6p+Jjq9S+oLHk9Gc0uOtk89yOmi6FTw/jNIbVGG1DOvy3/AKKiLC8RmkyQ0NQ9/YMKFODVpoejJ6Mr+GqPg3VYid8O14jMnTMdQP2VWtr2IHddN+D49SscJMNrWMcLEGEkH9lSaHEOWY3UNRfzGdEa49midOT0MIdZTDldNhtdTtzVFHPEO74yFS2OVxs2NzjfYC5TtPgNMlyjVhgppK6nbiEkjKQyNEz4xdzWX1IHey6/ENDg7MSrRw9WvmpI+WIGyMcXy3HqINtge9lz48ExkNL/AOEVuW3zch1v6Kpj62knD42TwzNOhDSCFk935WaqMlu0ZnZm3DgR7iyQfpoVt+ExWsBl+DrJhuXiFzv7LCWuBILSCNCCFapiaaLGuc7RoJsL6dkZyQDc2Ox6K6gocQneTQ0VROWtJPLhLgBt2WrHcRxDEp4n4lAIpYYWwta2DlgNbtp3S2ukNKXLMBcbEgGw3KOaQ0hEEM87iyngllda5bGwuNvYJSwzQOyTwyROOuWRhaf3T24E3ImWVDadtQ6KUU73FrZSw5HOG4B2JHZREhstEFc5tGKWZ8kkLC5zIXEljHHdwHQ+Vje43u4EX7tslVsSbW5YXOIv0HVbsC/hMuLQMx6pnp6E35ksDczmm2nQ6fQrkGQE3PTYd1Bgbck/ZVo2Icn2OlUupxUzCkkMkIkcInuFiW30JHeyrv0OiyQ5A45rgK27Cw5nkdknGjSMh84AkbqwTCwFv3WIcsTgOuW36K4GOMmwvcdeipxRMZPkuM42v+62U1Zh7WNbUQVDrOGYsnAuOo2NjdclhgDJMxcZDbKBsO91Wwg3AOnVLw0yXlZ26ifCXROMfxkc3L9Ie9rml999trfW64j6yRpIa8Zb9lRM4F5sb+VACMxm5fzL6drf7rWGJJbmE88r2Or8aOWY21Ega4AvYPlJGyxyzkD5rrGEKljSJfUzaL2yXJupZvKzKbCQqcSFkb5PYfhxi2FYdxE0Y5BBLRTMLHPmjziM9D99Fj4uqKGfHZxhsEEVI11mGECxHfRcKCRkcmaWPmNsRlzW16bKlzzrZY+CvE1nR4/9vSWue0HfRNr2FwDjp1WZXUghdO0VGblE+os3WriqOdTtmzFI4KeWNlPKJWvja8kdCdwsbrE6aKo/MbIubm6IxpDnPVJugdYHQ3QL9lNzw7LZjW2FtOqkZDkyDrv5VGZ0OGsSgwbHaLEqqijroad+c08jrBxsbHY7GxHkL6ifxxxJxPLwana3T5pXE+enUW/7r5VgWInCsVp634SnqzCSeTUszMdcEajxe482WjGcabieIz1baKnozIB+VTizAe9vK58kHKfHbmzaKio2z6PR/jRinxcbq+ihkpmvJdHCcrnA7C5vt+6qxL8a8bfUO+BpqSGKxAD2l5+9xsvlokab3F1Lm0+QB8by71XIf/8Ab077pQ6aLl/1hKaW9HTxfijFMTxpmLT1UnxcTw+J9/kINxYdgeijxHxLinEczZsXqjM5vy6WA9gNB9FyIyzMM1vqtFdJSSVDhRROipx8jXvzEe56roh08NOr0Ilmk3XqZi05S4bL0MvGmOVeBQYNU1rnUVOwRsYBlu0bAkb2sLXXny8FgaRsenVaZH0IoIRCycVd3c4ucCw6+nLpfbe6t4oZF8N9yFOUHZS05nErs4DxhjHD9NWUeF1Rip6ogyNtqCOrTuDbTRcJrrAgdU2cnnNMjHFmYFzWutcdRfos5QjJU9xqTTsnUVT6mZ00hJe43cSdyuxgnFuM4PhdThtBWOio6h+d7GixzaC4duLgDr0XJqzSPmcaSF8UZJyte/MfvYKeHijZPnr2TSxsLXcuNwGcZhmBPS4vqOqTxxlHS1sVrlGepnUfxZjj6CCjfiM5gpj+Q0OsY9bjUa6dL3t0Vb+JcYkxAYg7Eqn423/qGyEPta1rjpbotHGlTw1V1zJ+E6Kqo6YsAfBPbRw6j1Hf3XDnbCya1O6R0dgQXgA3tr+6X6eCV0innlxZ9C4Swc4xg9djc3GbcJq43GF7C7KS021e7MCQSe3T7cbjfCJOEsaFPR48K4zU4dJNTnJoT8rgHHewO+oIXloWwyS2me5rcp1Aub20H3SgEL32lc5jLE3a25J6BXDDFK6W5k8s7dssNZO6odMZXh7tyDa+v+6jznOn5zpSZN819U6c073Fs7pGNykgtbc3A0HsT1Wf0l1xcI8NJWPxJN7sm95MheXkuJvc7qp5c9xJJJPVa6KGmqZ3MqKh0DRG5zHNjzZnAaN30v3Sp6OSp5roGlwiALzmAsCbdT3W0cMpJOKuyHk3abMRSWiaHlPfHJcPabHUH+igI2ndxH0UPyumC34IA2Vksr5AwPe5zWCzQTo0eF0aHB+aaOWvknoqGqkLGVslM50em9iPmsdNFDFqClpK6Wnpq4VMbDZsrYiwP+h2VxxOUHkXCFqp6DmgAg2KhYjddeDBMRfQtrIqGeSlkdlZNk9JO1gVVLguJRycuWina87NLNTrZarBkcdSi/oRrjdWc4K2OV0bXCNxbfex3V82G1VPIY6iGSOQGxY9hBuiWibFTRyuqWc1znNdBlOZlu9xbXwsnik7TXBalVNdyhj8pvfXwlnJcSSTfdXUlLHO2Zz6qOIxszNa4G8hvaw8631VIjGvqUOFLU+5WtvYb5CTudlJk1mFqiY26Wf+ylHHGDdz9ult1GxVy7BnbY3b9QURtjkv+ZkIH6titrqKmfhxrRXwtkMpjNLlOcAAHN2sdlRhlIyrroaWSqgpmzOymeckMZ5JC6IR0tWrsyb2+BmcTsotdYrW5sdLVfNHUBlwbXsfKKWjFX8Q4VEUfJj5mV5N3i4Fm6anW/sE3gerSufQNW1mQm5JQ0kHwrMrGXFw6+y24VhsVc2qfJX09N8PGH5JSc0utrMHU+FMMbnJRjyDlp3ZzL6oV0sbWPIZJmbfe1kKKp0x0zsVtW6SV2uhPay5r3XJWiqtazdx5WRw3K5ccUkdeSTbDMmD5UBugFa0Zplocnm0sqwUwdQpotM6uEVPw0weNRexXc4kxaOemiZELOaNwBqvKRSkGysmkJb4XNPApZFJnfi6hxxOBFsmtyVe2f0lt1juLJ5ls4pnGsjRZK+5sqSTqhzrqBOmqpKjOUrYwe6V0rpb9NFVGbJ3Sv3SsbeEteidASTBuFAlAP2RQrLWlWMdboqL9lNlypaHZrMoc3ZUl3dRvv3USb6XUKIMm5+hRE+yqupBVQIk91yoh9gbqLiFEFNLYLJX1RmUSR9UaW3ToVkgbFMO3VdxYp30RRSZPNukT2UQ7wkXIoqyQd5TBHVQDrX0SDiiibNAPkJEqvPZIPJS0laiy6bb33VWZSDjdFDs30xcDYnS+61uOwJ0G2q5THm2UkhNzj/MVjLHbNY5KNkgy3Adus1yL+q6ozEXOqQeSrUKB5LLna9UMIB9RVF9d0idVWklz3s6AmhYw3JzeAoOljc3dyxX7pm29yp0It5m+xY4s1UQ8XvZVlK5Gl1aRi5bmuOpLDotsWN1sbbMksPZchtzumHdFEsUZco2jnnHhnTnxeqnYRJIXX3usD3Am6rJSubbpxhGPCFkyynvJkr20SzKN0rq6MtRa11iLFAeb7qq6eqKGpstzX1ujN5VV0rpUDmXZzm+YqQkI0Dj91n6ouLo0oFkaNBkd/MVAvJNy4qsuSuhRCWRssMh7qbZnfzG6z7pp6UCyyNfxDrauJR8S4C11kuUXS0Ivx5Lg0umed3XVXMPdV3KSaiiHlky0PPQqYmcBYOWcJg6I0oFkZo57+rkmzvB0cVTdIFLSh+JL1NnxUltXKvnuBBB6qjNol9UKCG80vU3GvnLbCVx9yqvipLnVZh7pgpaIrsHjzfLNzMQna3KJDb3UH1UjnZi5ZA7VBOm6PDj6F+PNqrNra2VosHusNd1A1Ty/MSfBWUFBKPDj6E+PJ9zfHXSgWzaKL6x7j6nX7LFeyLmySxx9BvqZ1VnQir5Y75XmxUJKyV7g4vusTXWTzXR4cbuhvqJuNWbYa97L2tc9QtbcYnvfS/suMCpZik8UX2HDqckVSZ0RiEvMzXtbyrJMXqHA5nl2llycxKMx2ul4MPQF1M1wzeK17jck6dytzMcqGMy5iR2zFcIEqRdpoiWGD5RUOqyR3TOpJi00j82d31K0fxuYNLcz7f6yFwrlFyk+ng+xS6vInydKTEpXuJzOt/qTgxWSInV/sHkWXLzJg63T8GFVRP6rJd2dh+MzP3e/wD+4rXQ8RVVK20L3gnezyvOXupNkIUy6fG1VFx6zKnyd+r4hq5jd8rzf/Nsp0HEtTSyFzXvva18y84ZDfdGbRT+lx6aor9bk1Wmeqq+K6moFnvesMGPTxzB4fIAOztbrgl56FMOPdOPS44qkgfX5W7s9lU8ZVklOGCebbq7quPNj9ZITmnl76PK4pcT1UcxuiHSYo8ImfXZHsdmpxyoqY2tnnkfl2u5VwYly3A3IIOhaVySSkDqtPAhVUZPrMjdtnv4OPJ4sPbT55840zmS+i4j8fmfMZHSve697krz2fRGdYx6PFFtpcm367Iz6LhfHrKWhfTzc/MR6Xgg5fovM12MRVE75SNXHqF58E7pFxvdEOixQbaCXX5GqPo3BfHEGDiSGeSdsbtWlgvb6KHEnGNLiNWXsfI6MaNDmbL56x1inmPZQ+gxa9Y49fNbpKz6bwrxlQYdW8188kTS2xcI/wCvhbOOOMMIxZgEM7p5OhEZAaPqvlLX2TdJ3us3/TsetTtl/rbeppWehwzFaSjxGnqH3AjeHXDQdl7LHON8IxDDp6cVJdzGZcpgtp7r5QTm3KkMtt9vC1ydDjnJSbdoiPWyW1I7M8mDxU5fFT8+XYNJIt5XBe+aRjWW9Lb2sFaC2+pKvvTgf4j79rLphHR7zDLN5fRfA513N0uUFzyLXK0yBlzYqIDNNStdRy6ZJ1ZRd1uqQLu5Wx7Yx8rifootDQd9PZGpBod8mYB/QH7IBPUG67lI+na3MaksIOxZdQq5o3uuyUO85bLPxXdUb/plpvUcXXXRFz2W9jrE6j6q5jmZfUGH6KnkrsZxw33OVqjXoF1mPY03Aafou/g89KHgvig1FzmsFnk6hwV6bNsXR+JKtR4rXsVONr3fKwn2C+i4jiVI+F7Y4Yr7agfL2XlZHsFwxoAJ3CjF1TyLeNGmXoFjftWctlBXSjNHSTOHdrCVQ9j43FkjXNcNwRay9tgOINoYiIzKeujtlz8RlFVJnkYHOJ37pR6mWtpx2HPoorGpKW55e6A4jVeuwmCk5zebTNkBB+YL3GGYdgdbCHSYdEHAWa1zQLnqb9FM+ujF1pIXQNx1aj41e6AV6/jDBaOkrT8HC5gtd+lhfwvPRRRi4LdF0QzRnHUjllhcZUUikm5QmcwZCdDdVvBDtQV1AWhuUDRJjWkm9kllfc08H0ObCwyvDRpfS6hM0xyOYdwbL3fDskEMkbgyJxYb+poIP+695/yMjXOrcJw2Vzm3u6naSuLL/UlinTjsda/p7lC09z4LdK+u6+3NwjhmrlMVRglLE7Qgx+m4+hSfwNwnPUhooZowRa0U7t++t1K/rGFe1Foyl/T8vZnxJC91xhwjhOG1UMeFVU5zG0jJrEt/YKHEXA1NheFR1lHigqHE2ewtAt7WK64ddgko788bGL6PKr2PHQMjdBUOe+z2tBY3+Y31/ZU3VzqZ7QbkL12E8AS4lgpr/wCJwRPLS5sLmHbyVtPNjxLVN7GccOSe0VweLuUA6q2SndHI5hsS02JGy6WA8OV2OzPionQhzACea/KLd1cskIx1SdIzjCcpaUtzk5z0KMx7rfjeDVeCVzqOs5ZkABvG8OBHe4TwrAsTxguGHUrpi02NnAf1KPEx6dd7D0T1aa3OfmPdAcdrruz8GcSU5/MwioOtvQA7+iwOwbFGFzXYdVAtNiOU7Q/ZJZccltJfUfhZPRmHMe6YcQN1J0MrCQ+J7SDY3aRYqtWtzOmuSWY90ZyopdUwJ5iEF3uoICa2ETDj1QZOyiNlHqlQ7N0uK101BT4fLVSvo6ZznQwl3pjLjc2HS5WXmu1J1v3UEkJUqCzQ2rnbDyWzSCO98gebX72UzWS5AedIXDu4rM3qkr1zqrEq9Db8a8su57nP65jdUOndJ83e6pAKFNu2yr2ot5hAIakH7qsIHVKhWW57dEc0W2VXVJLSh6mXCX0kdLpB4GoCrQVVklmfMSTud1JkvLvk0LgQfZUITUmnqTClVFpI6qyGfk58oBLm5TcdFmQnGUoy1J7hSexaXAoVQKFDVsLOnOAHkAG11mJ1KskLjqdB0uqXA31WUUbyluJARbRAVGY76pgqKYQNMujflIO6smkD9Roeyqjjc9pcCNPKnNC+MgOLdWhwsb6KKVm8ZPSVXUmnooaoN0zKxk6qJSJuknRLY0XQkmIlfsUj7pIKAsepQFEJgoESBU2k9FVeyYOqVDLr6EqKQPlRufdKgsleyAfKhfRO9htqnQWGyLJXQgA8I3SQmILpghI+EgO6B2TSKQNkIHew0BAKNEAO1+qEvZNIEJTB1OirOikDrugLLAbqRKWdwHf6ID9NtVJaESfZBdogk9Sq8yaQrodyndRJugd0wTJ3Sv3QATogttukVuK5S3TOyQa47JiAGxUrqOXpZXMY22u6TYRTZVmOvVJW5Wi+l0nZL7H2RZVMrKApOy9Bb6qNh2TRDBCMoBRayAVglYp9N0uiAY0W7Itoga9UBRHYlF1IgJAeUyRXTF0J2Ft0DQiUa9lIE2KLJDoh0QpnToo7piEE9UJ2QCEjomBZFvdIYkJgIKBULVMBHuj2QMNkIN0a22QAJX3THsj6IAEIRdAAj2STQCBNRKfRA7D6oujrsmEAA0TtdJCQxm1tCkNt0adEJgxWReyE0EgCpA6KKLjrdIpOhlCSNEAPukAgaIumA7BRICaWiEDFZACdghBND8WS7posgYtEJi3VFkAAATQ33T0skUhtskeqbSCmRukPsVm10xcBGW/ZBTEK2qsDRa9rqLRmKuMYyXSbHFWZyEgpPBuUgqJfI+iGb6pgbptbcpDXJfG1nVt9OhVcga29h91ZGwZSSD9Cny2ZC5zumyi9zfTaMwKkHgDUXTDRZTaGa5xdU2ZJOytr231C6NHUiOSNxja4NPyuGhWSJjQ4Wt9V2aWmDRFbIc51cdm+6xyyikdfTQk5WjNV1Yfc8loB0AA2XPdLc/Lb2XfnkgOaPlRkx6Gx9LvZcSUMMpLWhoJ0HZRharg06iMubJwVb4mENFwd1I1BkcbBDGBt8xHiyDHqZAd1XlszTlR08MqbgRFrBr8xXr8PlmfHLNHFFIIWZvnAAN9wSvIYSYm6OiZK4nQHQgr2WGRxGCRtXR0rmNBPNLiMp76aH2XBnS1HVFvQeW4mr5Kqd0k9NHFJazyx979l5q5G4svUcS0wa7miPNE5pLXMNwSDqvLu1JNrBduCtGx52VNSAkkpMOttVEHUgBSsQbraiIyZtpSW7k2XWdWSxtc2KU5iOt9lyYmt5RcblwTc9wHyuF9rLmnBSe52wyaInXosUqYJQSLtcNR/ddGHiaenqmSRxMDWggMzb+5XkXPeHgCQAq0l4iDg5rx1sNlnLpcct2gXUOqOrjGMMrZxK1rmuDrkF17qyuxptRQxxmnYcos7XT3915tzrPvbRXNqCIyzKMvey0/TQSVLgldQ9zPI4Fy9XhPEktDgxggEVyCxzZADp3C8jJa+isbIAwtyg36rXJhjkSUkY48zhJsqkIMjj1uvS8F4w3Cah7+UyTM03z9F5YkXV9O8MO1x2VZsSyY3B8GOLI4ZNR0uK61uI4pJUtyjN0aLADsuz+H2L/wp05y572Ibb7ryEurj5WmhmfA68bnAHeyzyYIyweF2NYZv7+tn2XDOI455pmN9TiL6tII8BaqDG4aqnewaPY+xadjY918hhxKpY92V5DXCxG91tNdMynYKesdFb1ZG7kryJ/030Z6azRabo+mYnJSzzNZPSxkt1LtNb9bWXGnwDAH4myIULYogMxEbtdehPQdV42PG64Znvku+2U5tb6qyLG690nz3zC3oFiEodHmx+zL7h4mJ8o9zNwJw1VcqOGi5EebM8se4uIHS5OxXNxL8MMJmqQ6kqpKOO1nNJzi/SxP/AHVWFcSSudG2USyPaC0uaAb6WF/Zdan4jY+mLaiKYuJIcCwWtfcLHxOtxPaTF4GKS4R4R34e1P8AxB/CmVYcCL84Rk6W7XXM4j4SrMCJMjhKwGwc0HXyvb0uOtOOTZIpp4mhzIwQRkJ6k72XD45xR9ayKPkvYI7hxLjYnwOi9TB1XVSyxjLjuc2XpMKhJpHhMhUchVzlGy9hM8dqi/DMLrMVq2UlBFzZn3ytuBt5K7WL8DY1g+Ex4lWsgbE94Zy2ygvB8ge3QqnhCWSnx2lmiyeh13F7bgN6r6d+IuJUU+BcoyAxyNzxujIzF3QeB3XB1PVzx5Y44rk7cHTRyQcmfE8pbcFFlNwsSDqolegmcVbiA6rpYdw/imJB5o6R8gYzmOOgAbrrc+ywR3zg6aEHXZfdeEcUw+PCBkIDg0CRzmmxJ6DwuHrurl00E4xs6ul6dZm7fB8LFNN6iIn2bubaBRmglgfknifG+wOV7SDYi4P1Gq+14NheGz1VcamlaY3SOewvOUD3b5V+I4DhU1ZQFlHC9sd2uu0OaWm25Pa2nhcj/rMFKnE6X/TuakfCUL69xFwPRSwTOoAyme+TMHFlmeB4CuH4dYZPh1JDMyUTxQlrp4SGCRx1u64N7Xt7LVf1jp3FSdmT/p+S9j45ZC+mx/hPLJUaYg0U7XeslvrcOzRtf3Xn8Z4DxTD8S+FiYyVj7ujIeL5R321XVDrenm1FS3Zg+lypXR5Hqiy6tVgVZC60bHSjLdxDCA0721G6Y4exN9Gyrpqc1ETm5jyfWWa29QGo2W/iw9SPByehyShaaigrKZgfUU00bC7KHOYQCe11RHG6QkNFyNVpHz+zuZyTjyRshSc1zTZzSDvqEJCN74ZScrm3O4WZ4I0PReyxfhylGHU+I0tfO6OZhayFsOd+cdDY2AI+y8k+EkkNZlLR6gTqubFkjNWjrzYnB7mdCnl3UbWJW5zBsEJ20SskMtjZmFzceyZAt6StuG0VPUjLNXNp3lwaA9py2PUkbBFTE8Xo2VDJGRyEDLs89ws9aujqWJ6NRzxY63RbypZGtdlc+xG6gRc6OVnOwIAG+qVigj7pXTJGRYJJpWuhAGoRrbZPKAPKQQIBvsmL9kCwOyOmhQCAA6qyOIvdYC57KLdlY0kO9Li09wUmMTonNeWnopCB1jqAgvyO+a/eyRmup3HSK8qC0gHRNzwToSlfyqEK2l9UiFIm/VBcbaXsgRD6ITubJJjHshFzsn6kDRFO2iLDqjSyBIMuieW3VAI7IukAgna3VK4RdAyQAU42Zj47qobbqbCbEAoY0aOSQDbfdLl6bgIbKQ3K7UIzNcLkALPc02Icu+gH7oMbm6FoITLh0ChmJ0N01YUgLOwA8JFrratRoepujXoSqEkuwwLXBTOgVfq7qRJsih3sK10dNUrnui5veyZINVjWl18ig0dVNpsCRdJlREbg2O6gbqZaSVEtt11QgZHN0shFtFHYpkE7i2yV730RZOwCAF7hG6PogIAdkdUktUDJG1tkvohKyBMO6Y9kgE9UCQaWT2SsUEeUFBdJOyimSSQCki3VA0SB+yV9bXSsU7BIBgi26EZEFpQPcBayPZKxvomPKABHVMbotdIdEdU1IDylcHRMVCte9vulbwrG+Lo0JsbpWOisA9ka9VY4WURunYqI+6atsAPlRl32SsrSUp2IVrGj+X6q0RtdvoEnKhxxtmUA9kzfqFPVtwLK0ZT/AIg+yGw09jOktGRpN7Ic1m7QdN7hGoehmca7J5T0CmW6m2ysbZo0cde6LEolFjeykGE7XJVlmk63t4UmTNjPpzAjY2St9ilBXuUZDY9+yMhAuVYZC5xJF77qZeDbS1kWxaUUZNLqOU6rWZNCQGn3CiywN7AjsUKQ3BFGQkKJaQtJeNQGi3dQJ00CakxOCooGyBop6kg2ATH0TshRIa9LosVshDTE5pfbw3qqXDLplKWot42lZUGOIuEsjuy2RfLawA6pPaL3vp0ulr3K8K1ZnZE8kBo38okY5ji11rjsV06aCBpeZqljXDZuU6/VYZI253WcCOhSU7ZUsTjGyoMJ2ISIIOqviaA8a7dFfM9swtlja4bEblGrcSx2rswtDnHQJljhvZXMcQDspuyEafMf2T1MNCozBhurBHmBuTfsnYaEbq5jsrTtc9UnIIwXcyvjLT1t5Sa299dlfIC/9YKqLbHQ6pp7EONMiGa7ptBBUmgtNypN9RuevRFjjFFrB6SS1xsNwNlB503sey10zOddri6OO2rspsVXUwNbLljlD223ss1JXR0uD0WjINVc2N3LJt0uqmtOc6HwtDXFtzcabgqmzKEV3KWtdcF1luo5nMeRlD2+6yGQE6t07LSMri3kNAuNQDqVE91ua4ri9mXurpGRvYGhtz0C57nOzeptitT3QMF3lxdbr3WaR+c3LMv1SgkuEVlk3yyxlW5gyiJjrjctuoCWQm1reFNgYLZmm3YFItac97jtqnt6E+auSyKUtfbl6k6X6ruzYvXUQhjbTNhYwZuU5ps7/UDuuKxkT42F4lEjTuDoQvRUeJwxwTtHPnqXtDI7gOPbUkbLDJVray03TVnnavFJ5pnvLDEHttkZ6Wkey5rnlxJt9l0sRlkLmune0u+WxI9NumiyOcxgcAG9iQbgrphSWyOOd3uygOsEw69hqSgWO4+qkwFp7KyY2a2zuygxizgEOfI9hvsd1THES4OvutD2ON23B7+qyxdJnTHU0ZmDK+5H1Vks7tbFVsY7No248FSe2wJduq2sjhbFWcvdbQeSri8g5XWPTRUXaLgaocD0NrqqIToJC2+g+qhnbbZPKctzt/VDYzkJHRUqIdlZIVlO8NkDnMDmg7HqqiAeqeWxVPglbOy6dzHuLmNDR/KFCJ4B2v8AVQN/qgAjqlW1Dct7NZcM12iwt0KnzQ4AOJJb1usLS8HVWxHKdNyocS4zNDXXGYyWd2VkVXNBM2aGTJI0+lwOqokfYaDbwq85zB3X2U6bLU6O3BW1U0wfI1hde7jcarTBiFXC17+cbMd/hPGw8LgCpkaQ6PQjq0apCd80jnSNzAi1rkWWTwJ9jVZ67ndhxQMrJalgexzh6Q15uD5PZcvGK99ZK57gG33AN1meS0uZoPF9lROwtA1urx4YqVk5M0nFooKXhI7aJjZdRwdzp4DUspKvmSC4NgNL213Xb4vqaKobG+mqS8HUNLSCb7nx7Ly9O4ska5rrWPRdvEsQfV07RO2KUNBDHdR/5quTJj/vRmd2DIvBlA8863TZIBMjUo2XYjgfJKPQr69hlXDPw9CIJBLHHFmdE70vBHe3Q918hjIDgXahehw7GpI2GEPcyAG5Att28rg6/A80VXY7+iyqDdntcBxOga6Y1U0+ZoLREZ8oAJ6d+itqcbpoMbjniqmyNm3ja4Eg7a9PovJ02J03xZkMYeCLE5coAtZVyV9C2qZ8PE0X0cbXH7rzn0icm2nwel4seU0fRMQ4hhNK2OKYl8lxIXsJMY6m3ZdXC58zPhuc9zmsDmBzbXH9vZeAbWRsljZA5mR4aXBhPqAXVp8XL7xR1lPGDmL5XXu0jbUbLgydLslFGq3PYwzx8wk1mznB7XA9N7ey5+I1ZpcQpgwmcyAsD8mgYb6XJ1K5eHYlWSj4hsbKphJBax7BlcBqbHpbW641RUc3FORXulbUNNyXVIORpFwBb76Ix4Hq37INkdrHK18dE9sEUkEkTt3kZWnpYW1FlzOF8MZE3PNFnE1/z45Czm3Oo03A7LJi2MwRRCKhcySQDKQ5pczTrc73WvAMVkrxEamkprQMBDGvDHO11Put9GSGFtbWTcXKj0OPUNRU005oZKYBsH+HUsDxm2vYmw0G68Zwxww+oo3NfFTzZnnMwNtof829uvhdriuvc3DamnpYhIcwBklc27P9J69lVwlX1IpoaaifAGSSBr3SXLm2F9D2V9LkzYcDlFkZMcJySkrI1HCEOHUlVWB7alrInE0ro87LjQNBOv1HZC7fFGIVFPSzctjbNZku19nuJ7C+yFfS5c2SLlLf50PworscPFaAVdLPNwvIyaCmcZTBT8xzYDudSbEr5pNUc0l5s5ziSTZez4knibmbLzqWlkzcwUtG2ISO3DfmOnuvCF29l6nSR8tnmdVLegzC5S3SuUanuuw4mBGuqYCBottLRwzUdTPJXRQSRAZIXtcTL7EafdJyS5HCLk6Rtw/iCtw5rm0csUccrOXKwRg5xtrdbcdlhheIIaWVtfPE0VAfGGgE2Iyi2mltVm4awmnrJDU19VDDDGDaN13Olf8ApaGjXU9V7HiDgqrq8Nir5qiWTE8rGilB5vi2fYaa+Nlw5MmKGVWephWV4XfyPn09FVRVMlO6le2WJ2V7XWu0+VJ7aprXXDmOZo/0jRXxyGkqpY5HObIwlpAsfUD1+qnX4hJXcptTUGVse4EYaf2XU5O0cemNNs47mlzjc9d1EsOv+266c9DkZeZ/Ka7VjSNXDuskjm3AY3KALWvdWpXwYSi0ZspspxNa53rfkHeyZvdWRkvIa4AtGqpsgrlY0E5X5h3y2UMrfK0zgPPpuGjYE3VJA1ufsknaBohlCA3oExvYKd3C1wR9E7BIcUTc3qdpda20zS8Xc0g9jsqBHduYn2sF0sKjFO57azDqlxmA5MouA3XUgWs6+yzm6VlxW5NvDeJVFK2qpqbNTudkB5jb37W3WWLDbGSKWORs4dlAIFvN11XCVz5WQ4fXSRFgGXM7oLXOnfWyqwwU1W+WDF600piitEXREnMNm2H9SsPEnTZpoRgxHBpqCYsc9khDQ4ltrAFQqsIraNhdVQFjNDmFiNRcahaKuvZOW5oYXFgyh4jLc1uvus7XPJ5r6TM3ZuVpDVpCU63DREz1NFJSvDJmhrnNDgAQdCqBGzUvflt0suvI2ezJKpjWFjAGMdHYvbfwNfcrJO0S5vSAfAVRyeopY0lsYXNb+k3UhGCLkq7lNDNTr2SiYS7RXqJjAoEep3Umxm+twFpaGCSxlezTWwVjoQ6x5rSLaBS5mkcRjMJJOUOsPCrdE4A32W4xvabN1v0Gqrka+IkSMynyE1MUsdKzEBdTEbnC4C1Nfmbl0H0UmRubcEE+wT1ELGYg0gHQpsYXX1C6UMMWQiQHXayjLDCB+Ww5upU+KrL8B1ZzSLGyk0m+xV5gA1zKbLZgMmYdlWpEKLIsYZWPIFiPKg2J/wDKXey9Jh1XhLwxuIUk0gFgQJA3T7L0E9LgzqGodhxhdI+xEOYHl267XOl1zy6jQ6aN44dXc+eCJzjYCx7KOQDQnVehmp6YRl7ZYWOvYtt6lzqmNoaAG+k9Qd1Uc2oqXTuKOaRbrqrG07suYuA+q6T6KmETXQvcbjXMOvZVQU4kc4WjFhclzrWVeKmthLA1yYwxmX5xforPh28vO6oj/wBPVaTAwkWcw2GuULRUR4YaJlhJzxo62xCTybmkcF3Zxy1gBINwotbc6BXcpjiQ0nwFW6EtdbNYd1qmjmcaI5T2UwLDsoHMAbOurYQXkANuUPgIrciWuIuLfdRMRuTurpIHxus9pBUWxvF8wcPdJMpw9UVZCelkiwjdTA9XVEgcOqaZFEWtCZZ2UWl3RWA31OiAVMryG3VIAnwrnAAaOB+qrNySmmDjQwwm9vumY/qoXd30U2PDUtwVC5TrE2SLSFYXEi6hcWQrE0gDHG2m+yC10ZIeNUg9w2QXZj6rp7j2oeUkXASyutfLsnsNLpNO99boAjcjskRqnYpG590yAHdPbogeQVI69EDW5EC/RWR2AIyi5SGmuVBuehFkuSkqJG40y2ChlJv3Tv3uSmbkbJFciy23Cj0OilY9VA3umS9iQuNUZv8AwqNynlIQFi1uUWTvZHm6BA0uGgKkXu/UbpN0cmXb6BA1sJxJ21SaS031BUmk2SzE7hAu9gXk6XUhJYWIuoN02UgSCSQAUDtjEhY64F0Ca52soOObf9k2BtjobpUhqbsnmCWazr5Ux3A/dRLiTsgbZYJSBq2ylzyBbQhU5r6m6gRre6WlB4jReXAglDX6aqpuxNylv1KdAp9y4PFjbqm3VpsG+5VGoOqm3UaGyVDUrZNriGkenVRNr2USLE9vCLG1xdOgstDLNBvdNrD9CqQ7KLXRmI6n7pUxqSRbIxrHjI8PFtTaygSDe5VTiSbC6WtrEpqJDn6Ezbv91G3lK+iAVVEai2Ow16+6b3XF9VW22uqDqprcvVtRISO7qTnudYkKoXT3GpTpCUnRujqmckxCmgLiNJHE5h+9lSHMa65AJ7KpjR3Q8qdKs11trc0ROa45TZoU3sp2/MTqNLHZZGP7AoLrnylp3KWVJcE35WuIbqO5Tjc29i0/RVZhqm1w6FOtjNS3NcjWBpY/O2TsQpGCF4iFNLmcR6xIQAD/ALLMJSXXcXfRRuwEn1ZvZSos11RZfO0tJAc029JLdko5WRhodE241zEbqnmEnZ1kEtJvr7lOttyde9oufJA8Xy5fGqsgETXAgkMOh72WNzg46q2FwFg7brpdJx2KjNOW6NwDTK4R1DWMvYFx6KuphdTt9TmPBN80bgVfHLRNy6udYXu5uxVDpIZMzjG4O6EGwWSu+Dplprncyuy3s2/3UuUMw1uDvZVSWaQQ6+uy0wVMLG2cDm69lq7S2OWNN0y20eUNETXi979fZXwSyQSPbG1tyfkPRV0Rp31Ac7QG9gdRdbTh1FLI3NUPa8gaNZfMfuueUktpHbji2tUSufC444XyVcp5zhma2JwLW+653MDRctaemupXpaihw99KGOqXUhJIjeSXB/a4PReeMLWh35jXOadx1RiyaluHUY9L8qKxyZGm8jmntZEYDHcxpa/Kb66g+6cVNLLHI+FrbR2LnFwFlKjpXSzNie2wcbZhsFs2kuTlVuti34gZ87mtlDt2R3sPC2QUhqpC3DozIwtvypJAHHvYqvEWNoakx0lU9+QZc4Fh9D1CuwjCm4zmgp6ynp6hgzDnvyBw62PfwsrVaina2ZgqaKWnc9lTSSQRh1jnF7eL91llhLG5o9Yi4hpK1Pa+CVtNPLI9pfs2QuHbMO6yyxPZK9jTcNJGq2izmkqMx3vupsec2jbk7BSDCRlAzFHJcN7hXaJSYOmcDaxBHdXmYmOzGi53KyuY8mzru8rUyF0bfzGSNFrgtAsVLSLi5boqjLgSAbKMhbfK5ziFc4SNYXBvpva91nNjrYk9kL1CWyobTELhtyokgutmsEgxwPpaT9EyyUC743AHa4VEbhcC4cb9rJPLR8ut1E2G4TuCLJibIHMNVIOso3A6JXFiLJkWPNqphwUG9irAY+rSPCGNbkgTfNv7qTCG+oi6qGW//mitGmjNVLKTFzM1/Va/RQJGtnFEjQHWLbfVJrcpBGqaoTbNIcYobxyaH5h3VTXl2gUCS42t9ArhKI4izlMDj+o6lTRadlVyASDqqzm1urGE77qMrw79Nj3uqXJL4KUgLoRdWYMmAW6dVYAwNOZ7hpoB1UIshvnJCR8JFrZET4Ufqm5padSEh1VEMbfZa4Wsyab91l26q2J+XpcKZbo0hSZrjqOSfS0HtfZBnDpOYGjMTcqjPcH0X/soAO3a1xB7BZ6Ea+I1sjoxVlTE8TRAZ75bBaqfFa+Bsggpw0SaPJZe65cb3taHNJa7oQdQVoZiVXG1uSWUFp3ad1lLGn2RtHM1y2WVMlbIWzOqs7ra2GW3hQp63lVAkfEyR3UOF7rM6WRws29ye+6mKkmRrpoWEttcAZb+6pQ2qifFd3Z2zjU0kBidHSsbbQ8oAi3lTwvG56XPJTxQCdwylzxuPHZeclqA9xOUjwNlbHWRuBa8FvYhZPpo6ao2j1Tvk7+K4zNNIxtbTsMYYdGAAknrf3XTwrHhSUVNTUkTzBI4OIMgzh500sNl46eeIx2ifKSfmDtrqXxxEEceXSMk6+VD6WLgo0UupqTbZ9DxWUyU0tZVYfP8S45Y5ZidG9NhrbuhfO/j5S1rfipzbZuc2CFnDo3FUaPrI+h7njjCsMwbC5aWiw/nzR71MtUS6MG18rAf6914KjxE0rX5Kalkc63rliDy32vovoPE/E9PTSSNw6ClmZGcrpjSR2lPg2PRfNamTPK97Whoc4mwG11v0epwqaOTq2lJNML3JJ6qNz0UbmyASuyjiuyTM19bK5tRIyN8THWY+2Yd7KgG11to6U5WVVXTVJos2V0sLevYE6JSruaY7ukdbCsSMtNTYdBSQQVjZs8VcH8twP8AnJ6BdDEqviWmoJaGu57qd1+ZKGPyyA9Q7YjS6poHUXwctRR/HmtY/wD5ccphiyN19fcqeM4hjmO1FPHJJidRmDnGLMA0gb5QNBbUdVwtJz4Ve89SLccXP0OI+KmeGCFwDANXP3J6rSyOlaG5ZWs9Ju7I6xXGni5U7mEFmuxOylG1zzlLzbobmwXU42uTznOm9i6omdK8Oke99tBcnQLM4a3TfG5rjupxuflt0VpUjNu2U3Oy1UTGPeWvF7jT1WUHDOfUTtbVXClY1hkFRDdv6Q45kN7ExRbIynp5CJIZXNy7hwNj9tlgec7iQMoJuAtTIi8ZzIHN/VY3KneBrbPa57TqNALfXqpTodXwYQLHUp5y46kpSkAnJmDel1ESOIsSbBWLvRpYM2l/YL09NVSw/D02K4piMNOxoaBARIxjDrbf9l5Ier9Z+q6NDFDI6OOWtZTwSOAc55Nm+SBqsckb5NIuj1z8apYY89BJHMG3jDKiiHqv1+Y6rkYzxJX1EEdLFDS02W+b4emYwu9zuu9SYXw3h0JZW49BWwt/MJpql8TiQNBlsdQuLXNwaBsVZDVTVTZSc8ckrS7301+4XJj0p8N/I0p0Y6XhnFsSo4a6B0MrZ5OWxjZWl+bsW30SjrcawSMMLpadjXuAaR6S7ZylWY3h1RNIKGhFHA6NrCJXc5wtuQSBb6JVgpGUUb6bEru2fByyR5cCf6LbzPaa2+BcVGrRhr8TqaypkqJX/mP3IZoPZZTK4t1mLj1GXZaamrkf+U2te+N3rc0sDfV1VUPLa14a4uLxa50yrVJJcENtvkoMn+Vx+igHvIu1pt7LXJ+WS3mhwtuCs5lIBGbfyqW/YKruThinlJIFgBq7KbKynjkM4DGNcb/y3CpZVSxxuYyZ7GuFiA42IRDPJE8OilLXDqENNlQlFUdumgmdMXCpZC8N3a0DQLl1DmOncXPMpvqXq6CWJ0Tn1UzdB6fy8ywvdCXEskLtdy2yyhFpuzozTi4JI1tZT5T6RptqtDKVsbBJKJmscNOW4G6yCeNpBDGOPYhXtxMDRlPA1vUWOqpqXYxjpT3GZKa4zsfba5es0kbXEmKZvgXWkTtmdmihibf9NtAqpCI3XDY2uHQAWUx2KatFHJc1mZ0jDra19QuhRPpYYZ21AY8lvpAedT9lglfJI5z/AEE+AB+ygOZa5DPKtptGdqL2NNNDHVyFr3si1ADnEgDXc6HReow7BMPgrR8ZiWEzU2Q2dSzEvJ9tP3XK4dxOjpZJBXUFJOwsLbSTPivfy269bT4fhsz2y0GHcMNikDQ4yYk5uTvvqPsscrdUa4krtnJr8Pjp4HyRcP1UkYJHNaywt9Lrz7q2kcwQNoZI3Rk2u0Fxv3Xo8ZkbHiE9Oyrw5gYQGPgr5JGt/wBJO/2XnxVfD115uTV2N7tJsfqs8adbrc6pNbU9vgVxsklhdI0NbGDYF9gbrOHvY3PyA4A6kjRaH1HOntHSsc8nTO667GH0zoqY1FV8PbUupZszRJb20VSnoVtCjDW6izj890n58NLGCDYsDgR9lGuNS+P84RMYflYwgW+i7MUxnhkkihgoLaARRn1eLrPlqcxiFJz83ylw091Kyb8GrxNx5OBDA95ytZf6hKWIsdbLqN+q6dVG6mjaOdS5tQY4vmHuVSJC6KwDS7uF0Kb5OPwUtjGG8wgBjW5R00utdNRSEZgwtI/XrYKkFpjeXPDSLWHUrsYPOWUzsjwZtbB5LRb3UZZyUdi8GODlUjlzyzRE5qlshGxY1Zpqh0jADI4kdOi74wl/Nyyz0cpLc9hN+3uuTUUbYalzJmMYN7NdeycJwY82Ka3XBzm66gpuDiNR+66jaOmtdtQAD3bsq5aWJhBbIHA7a7rRZVZg8E0jnZb23H0Rym39RP1W2QtiNg0k9QVpY6SpawDDjIBoC126PEYo4U3Te5yQyPNc3RIyMOuwmy6bqV3MyupOTb9JBJVclLXQAfk8s9AWWv8AdNZF6g8LSObkFrgqfJblDrlWine+S0hI7laWwRR35c4kAtuDYqnOiI4mzmEWNrotpuulUwTECS1OG9GtcAfsstg42IbdNTtESxtMoa3ypGM9CrmwOLvSfr0V3w8zWEiNzm9Xhht90OY44mzEQ4aEoLT3CukjsdGuPnKUNbHazmn3T1CcHZTkcOuqiRY6q57YWt9Ehc6+2WygMt/UmmQ12IC/lWtbILmw+6kHsGoH7o2GvVKy4xSIcyRtyolz3XsLqwZXH1PsFppYKaR1n1Ab5CTkkilCUnSMjdvUDdGaxtddGnpIXSyNkfKYwDkyNDi49FkfA4PLcj732tqElJMbxyirZS4utoFWbnrZa2QtdZpL299Lp1VGyO/IMzv9cdk1JXRLxyasxtuOoTJuN1cynZ+px210TjpOaTy5LW/mCepErHPsZrpgjstU9AYbF0zXX2sDZQbAy2swvbbKUaotB4c06ZnJN9076KYhHcn2UhTSF2VjST2CdolRkU3sU2lSfE5ujgR4IUGtJNgU9mLdPckHZUy4Ef8AZQyuvsizuoRSC2PQeUWJ62TaNDopeu210gogRYWKkAdLJFzuybHm2o+6NxpqyQa9xsBc+FF926FWCaMG/JF7dCVXnF72+iSsppVyRaSSdCjMb7FTa472TEhLs2x2TJSK8ziflUg42tlsphxvo79k85bcOAPgosaXeysX3CC42OqkHaW0UbgjfVCB7Eb/AHQpANO7voj8sd0CI2JvayWrrqRydyo+AU0SxWKViFIEgIz9wmIQPlSHv7JtIIsQB5UyA0aWUtlxiQJIHRADiDYJm7vdP1ADt7ICrAFzR8qdw4bJPN9kjf8AS21kiuAB1tdI27pC/hPxpomIdwEmuSDgAQm0jVAizmE9LKBeb72UmuaRY2KYyWN23KRW7IZjc+pMv09KR5dvKR12TJ3Qs1xtr3UmSEHUqFjZMgp7CTZojMW5cT4BUs7ALMLxfuVmFgNkw0EXuFNGinRNz2XPX3UQ1u+ZV5R0KtZky7/RFUJO3ua4xGGfMRb9QC2UtI2Zszm1LI8jL2ebZvA8rkmQ2AtoFrycyGN0QsTuHd/CynF+p1Y5r0OlAGvzwvqWtkbHoZX207Bc9sro3XbG11tPU26QpZiSHwm9twNbeyzzNdC/KC7ToRZTGKvkqeRtW0FQ6Tmg7A627LTQ1UkUmZ7S8Daw2PdZMzsofzLk/pyqbKqRu1gfay0cbVUYKdSuzummjnfHI6qiAdYyNcCwt8DRURTtpaqWWip+aGggsniEgaO97fusTppqhjWOmc62oGbYrS2PEqB7Y6h89MH2JaeoPW19Vio0t2aznF8GapnuA6XK0u2LQLge3RZzIx1gwnfcjdbvjxBJIWxmVr75swDbm+hsL2Wd/wAS+ja+RzeS27mNLx1OthvutIrYwk7ZQTlHpNj7pXI0LipU74815L28KcjhKfTrZUCVqynMLm5sVY1hc3/EIsdtTdVtYS8hjQTbqFKLm65XADYi+6GJP1JEvBsTcdlY2cNaRGwNPUgKnK+9up6XU3Q1EbM74TY7EpUilJpkRIA4lzXeQk6YOGpdYbAnZJri52UgDypVEZaReEa7FvVOlYrbWxQQZLkuaEgLbFWABoF23PYofZupZoqszruUO0OinFJbbQp5Q4elqBlabOZr3VEU7CRxedXaIa5rQm066FIsBPoOYnskvQv3khJELF7S4E6tBspCWPXIyzTtc6gKlrLH1tIClZt/Tf7IpCTY8+pAAA8p6OGrmtUmwktzDc+FHltbfm38FtklQ6YNa4OOQF1t9E8gdrb6Ihia9pyyHN0HdQcwscQdD4KAqkDg1rdC4OVZcC06qYa54OUt07lV5SWl2gt+6pENkEe5QbpeFZmTabHa6bnBxOlkha2isbJG3R0fMFtibWPdIpblBugKbiDewt4UE0S9iTQTsrQHZS4OGnRVMNiSHFpU9QL5v2SZUScb3OuLE+yuiMjScpfH41VERIJs6y2S8uzHNqTK83u2xGX6rOW2xrDfcgI73IJHuFZCCfVe7NlcHu5XNc9xc0ZQDa1llD2akSWc39LmaLPdmtJM6scVU2jbK9lO2nJOQloLiffdc2ojfI8l7Hg23snDVP5gs22uzTZEzp+YSS62xBddKKae45Si47GIxyONhYq5lBUCxdC4Ai4PSyRJ1aG636FaKd5YHh8z2h27Gi4IWjk62MYwTe5ZTve12VrGl1rAnopxwcoujqaZrzIA5rnh2ntbof7KDJIHtItI57W20AH3V1JM4Fj5IKh9ODlID7a+D/ZZO9zoioukUQUTMhkMsehsGD5vdCsquU6V74GyNbe4zkXH1QjzPex6Irseox3AsOrQ+o/jGE0b4nCM09JC7lnyCL6914meOKnmlY78wjRhykAjuvR4a7iTieB1HTRVlYxhz2YbNzdydBf3Xnq2llgqn08zH/ENcWPY83II6J4VKPlkzPPpl5ooyWH0UXWB0vbypvaY3FrwWuGhCrvddKOMY1K20kwYRDU1FQymLvW2I3+wva6yN1uVZzTYAgG3dTJXsXBtOzu0/wDCYaxwosdq6enIu50lOQ4i21mndbcV/gk1Q/8AhOMPbFE2wfM17S++4Gu3+683SVr6aZssccbnM2D4w4fYrbR1+HMjy12FfEkvzZhJkNu2nlc88Tu9/sd2PqFWnZfUwl0AYHZmvdc+nKdB3ujmCQWDS32C6Mnw89JU1VPhboYmPGUtkzNjuTob6lYBUtP6G6dlqna4OacaK8ryCA1zrbpEubfp0IUn1MhGVriBfYKp2a+oN/KpWZS9wepztXWWgxM1vKw/VZ8ptspRRvc8COLO49ENEGoD4cgBzSbX0epvLTCCJoyQbZG3v7rG6CRt7sygGx16qxhtYmNlgdbGxKlopPYrcXE2ufqohz2O3snM8cx2VuUE3AveyhfUkglWhGymmne3lxtz9dGAmwWmnxGSMlgZDICLWfA139t1hgdHkN2OF/1A7Lsw0lU/DxMaqlbBGbta5vqv5sP6lZTpclxtltFRNNPLJPBVsp3NsZGwRutc20uVikw+jeGfBOrpAb5y+JgAt29S10k1J8fkrqikbHkN5XU73td/7QQbrNURQR1Exoqvn0+Y+sU7mi3kHYLNNosxSxRwVBiDX3GgD7alQmhqYnEysDbHbMCnUyNmkLnNjj0/6bLAqUc0QYGva3bQBmpWu9CXoZXOc9xc/UlX0mUSF73NbkGb1a38WSlkjfYsjy2Fj5UWh+UlrSR1IT5QLYhK7mPJva5voEhGbXFim12UkloU2Sx/9Rp+hT3XA1v3HAC0nRjtNnK1+RxH5bWAb2VQqAAQ06diFY2uLGEcpjr7khS1I0hp7stIpZA1tw229tys80MTHHK/0+EMkzuNw1uvsr3xBwFnh3cgpK4st1NcGL0B2p09lohfC1xtKLdLtUXxFuu9/CkGl7PRHe2pIGqptNGMU0y6SsjdIfRHsNWiyoczNqxoKsc30Xd6e6rbk2EhapVdjRyb5JtjdGA8HK7cEHUK/D6UVtQBJWU8Jcd53loPubaLMG3BvILeVfQfARuc+vJe1urYmA3f9eiN6EqPSNwqGYRsZHRwMYSC9lc14kt77LTWYRE6m+Ejw6aZ8YLzPTBkmh19ThsAs9BHwriHKdBP/Dns+eCXO7P9Rsu5TcK4sXitw99PU4dNbLEahwB12Izf1K5JyaZ1QSo8myhkpqeSBuFQOedRLLJdw9rGywzsqGQBz6OKIDUuDhc/S69hxDSYyGNirWx0jblzWxMjbbwCDcry9VHMxhkPNla39brJ48jlyXKCjHY5DBzHdfoujCByWiSKcjNbO2X/APVVDY6iqn/KGaRx0AtcqwU2Jm8RppzlN7Nbey2k77meNNG5lZGyIU0jqlsV/wBYBAP9Vhkqy2oDY5SWg2BN7JTR1LA10tLVNHUujsquSHva6PmkuOmYNCmMI8ms8k6pHQlqWSx+ikp22NiWg3d5uue/O1jiI5PcDQLTGDBIWzOLXA6CzSFOSqicOVznMN9crRqktnsht6t2zmMETyebKY/JbdXxxU5Iy4hH7Frgt4w4SscW1TXEWsw2ub/VVvoWMc6KqkbCR1y3/oq8SL7mawzXYymJhBtd3kElUyksaBNG4gjQG4XYbSU8TQcPrZZn6XyU7r/RY6uGSK+dz3C+hkYWk/dEJpsc8UlGzml7NrEfVWc3M1uVuW3YqbJQYnsMMVz+otuQoMuwg2HtZa7HNuu4cxua7hmPYlWc9rG5qcOhk7tlIV8VfK2IxuggdGT+qEE/dQe9j2ODqNpcdnC4y+ym/VGunbZmMzTF2Z8ji/cEuJKt/iFdK1rJJ3yNb8ocb29lcBG2LK6Jmc7Ev/sqRO+J7S9sbg39JOirZ9jOpR5kWGvla7Rup3Vjawy2ZLEy3TK2yUszXyZhTUzL6+k3WhtQW0+Tm2b2DAVm0kuDaDbvzF1NMI4nsZQxzG+jiy5/dcqeQ88kxNbrsBYLUx0JcTLnLeuU2Kz1UtPzjyY3BnQONyiC34HklcaIOdY2EtvACuiqczeSx82UnYONvsqQIZnhjckeZwGd17N9/CvrcOkpBeKto6gE2HIluftoVpS4ZjGUlui+SoZFTOp+S4vOmZzDdYbBnzxuse4VsMuIzFsLZh2Ac8Afcq6Simgd/wA9cv8A/uChVHZltvJulwc8iO5JBA6KOQE/KSFfUOY86BrCNLNZYKi5BNtVsm2c0krG4DNcR5QraeXLf0AjqHNuosleNLOt2VvLqJWZuVLl2vbRS/eXBb2iyodFPlcyJjbCxDBlB8qgMaLnKr6endFKDJE8N6l8ZIH0VkDYXFzRJGw3+dzHafQKLrY10uTvgpZZ7b8wtA6apSRgWeyQuBFzuLIffPy2lr9fmAK0Mhnjjdeie8bF2UnVHBSjq2ZjZUct2YNLnDvsrWyyTNOQuJGtm30UH000T7T08sel/U0g27qTZmMa1ojflzeoga2VNJ8Gacls+C000r4uY1rrtNnXPVQMdTI4NcRtpmdaytppaR7nmeOoI6FgFx7qyZ1BHldFFUjTZ439vCi2nVGqhFq7MnwtVOQIml312VT6WaLWSN2nWxstcNfJFmZDDYOOhJNwrmzvjeySWGSVo6SEgFPVNdifDhLhmOKnMwJY1wv2U/gnxND5TIy5sLiy0vdM4GSCLlXNwRfT6rG+aV7yZHOe7c5n3STkynCEUJ8dUWuyfmMbva2irAkdl5jAB7C6ta2cEvij+o1spGOpkYZ3Maxo62sP/lXZk4Ju1Ym2t6WtFki0kn0nTU6KcD6inkLQSzOOo3C6MEtU6jeIMTfmB1p231He+yhto1jGMkcZ+d7r6ut2Cpfa/ULqRVlSA6EF7SLjTT3TaW8p5dK4G1nDKCbKlNrlGTwprZnMYBa5Nz2SkLSblob4C2zUDw2OSNzHxvOga4Fw9wreVSxk8xrp2A2J1bon4i5F4Mqo5bXMzatv7FRLgP0rr01Nh08sj3ubHGblkTpcpA/1WVT201KXgMDnOHoIeHADzpun4ivgn9PKrbRyw4dlbFO1l7xsdf8AmF1oe50oEbGMAvYaAfuomOSFxa5rSRodjZVqTM9LT2KjdxLmsHsFH8x/pbHf2Cvaxkj8pkbHpe52S5dtr27hGpD0MpMUoNnROB8hS+Gm5RlbEcgNiexWyKN0jgAx0ltSLG5CuqAPV+WYbD5TuFLyOzWOBNWzkbHUC6mynmlDixmYN31WlkLbl7rk9NBZSIc3VrdOthsqc/Qzji9TnmJ9yC2yLWGy6rX3blazTcEtA1WWqzOkLjbyQiM23Qp4VFWmYx5TA86Jk3JKmy+1ldmKQMDbalBaTchyvhjk1c1gNhrdSf5LST2CjUbLHsZG5ztqU383qrxI8GzQB9ApAFx9ZF+mqNQtFrkogjdM4jM1turjZImSxGU6dQF16SIuylpjtfrIBZVSyVMz3FpJZ2zjVT4ls28BKO7OSC46a/ZTGcdLreHzvFjFmttqBZZ5nkvzZA3wCqUrMniUe5U6SQgNexgsOjACoNJF7AK1kgLyXtc4dgdVoho/inPMGSMN1tI/W3903JLklQcnsY2mxuWg+FL0OuScvstPIbGCJbk+DsqxCb6C9+iWpMbhJFNm62JP0Udh1V81PJH87bE7aqsN73VJonS09yLb9FIF7j8iYAuACr4WPv6Wl3e3RS2OMW3QwyYtyspw8uGmlyqWU73SGN7XNd2y3P2VjoZ2P0ztvqFFrXNdmD5BIOt0ky2re6E+DlvynMBfW7bEfRRkaxpORxcO5Fla6Jz3F73OLidSTe6g6CQC4Y77Jp+8TjzSKzG4jS/3UmukgOrz3srmVL2MEMoY1vcxAlaHzsqZAZBTssABkgsD9km33KjBcpmD4mYvzNe+46gnRNxdKS5znOJ31utxq2U7yGcuRn+VmRZRLFmzMblJ310Qn6IJR7OQoWuDrxlwd0Kb4HtcHFwcT0CfOZGCW7+FVHUSMnbIGtdlNwHAEH3RuyXpS3NtM+ee0LKZj32JaWxC/wBT2Wt9HWuikjlw2odygBLLExzsg6XINgs7IoqosfI+Gmzk3LT/AGCqnjNMclO7QnK4sn9L/O6jZsp2ohO+jbH/AMp8S5xdY81gDQPFidVnc+4uNLixu1SEz6WoDjHGHNdfLcOF1OrldPKJ5XMJfqbEf0GyvuZcora4ZNSD02VT3OaTY/ZDn5ybBWNDXDbUdwnwCd7Ipa+99DfvfZTjjBaTzLHtbdWZ8rXCzQD0yqrMXP0AbfsnYfEYja5wu8/dWnKzRj3a6G6iJb+k206pPJc4k6lTv3K2XBNsXMOkgtslypAbNBPsqs5Gmw90nZmu0ff6p0xWqGL5vW6xCHX/AJ7qu56pZiqojUTMltDdIdyo5huShzhZOhWO+psUBztgVEEdQnZp2QFs0MBjbmcMw7XUWXL7suOyiCANCptnDGFvLaST83VTRSaFLNUAnNI6x033UbZh6iVLmtd8zQfBSzst8oB73KEHzJ8qIXyyE22OypJIcfUrQ+PKepPlONzRfKxpP+YXCFfcK9CkggZ7i21rpiMPbcbjonK652H0VbHWvrb2T7EbJ7kSLHVAA1QTqUtFRAwbXCZdp0Uo+Ve7ySEy1huQWgDugqnRVY2uhtr6/spaX8KLrXNtkyR6HqpMY53t3KC5paAGBpG7r7rRDbLoQpbpFRjZVlc0aDdXRyPDQXMuAb3tuoyOOo/sq2SXFnOICnlFqoujaS2UtlNK9sI0c+ME/wDZVunjJ+b0g6XaLhXUFRHlMJqTCx2hLr2+tlJ0bI2EwVMedp36O9rrLh00b8q0VhglY17ZGNOwDrC4VDw2N/rN9emxUrTXzBzD9v6Ksau/NIFz1CtIhsbQ25Mb736DotEBcRo8NLRprqVSKYPkDIZGOJNr3t/VSeGQOMcsV5G6Eh1xfvok9wjsyb44C3M58nMzer03Fvvug8tody6iTLe4AaQD53VZlaczoiGbem5N1ZGZJnnO4OJOobayW9bjVXsVwPY5x5r3+AChbKeKl+JBdUNiBADwWX662PfyhROavuaRgzTilfSsrpo6bDI6MNBZy6eokOU9731XGf8Al1ORgMpBBs5hBPgjde6jxF7Y5aBuIcP4U2we2pjpSZXeM1iV5jE69oiGXFZqqsEhLpGxADyc+56J4pdq/Isq9WcuvnbU1UkzIIqdrrflwghrfa5J/dZwVJ7g7W1j/VR83XSlscbdsYI1WzD46GWdgrZZI47gOybkeDssQ16JhpI2RJWhwdO2dOvoqSnrD8DV8+mJGV36rdbhZ57mbLGXvF8rDksT207rozg4aaaswf42IMa0ukmDdJLX9Nuna60zx49VUMtZV01dJFCebJM42a1ztnft0XOpNVbOyWNO6X0OY3DK/lzPdTzsZC4NlD25Q1x2Bv13Ucss1mEM0GgAAsoyVNXOXvqamZ5lN3Oe8nN5PlKF0WQB8ko9WoaRsr37mLca2K5QRoGi47KAdoSRqpyvia5xiOZuwzb2VGa4PqHsqXBk9mWhzXDUEHwkHWv6nN8gqsEAalWBzXCxbdqZJJ0he1rXT3a35QeiGvjtYn9tVFxhzHKx1vdV6Ddpsih8F0hY4HljQbXGqi1zsuXW3hVhzTe1wj7hFCsva2O9jI4NPS3VTjc5hLA5xjO6oAH+b7qzM4WbG5411u7RS0NbG34qeSLlRuiDGiwIiAd990fE10dLJAyvyQvtnjvYO91CiZNzmmmiLpQdfzQAQV2mcN4rUfmuoImR5tS+qjt7au6LJuMXvRato84+LKCeeH/6QotHrszmE26BdquwY0dhNVUIc8EhsFU2Sw+iomwrKIfg6oSPlHVzW2/dWpoag+TmmmqGtzOY5rf82ily5RAHE2jJ/mGv0UqikqYbCd+p/wDygP8AdZxE4fVWHAFgOub91B0dtjdaGUr3NeWgejcE7JOikYLEAA6osWkrjiOnpKudEywvofZVASsN2uII7HZBdPJ+ouPsh2+41pSL2MpiCJXO2/SFWWwt/wAMyfVJ1PVX9UTxp1aq2skzW9V+1kJe8pvtVEsrmWNnAHZaIMrRcvcD1VfKe1uZ2Ye7Sln7tzWUvcI+V2bAYZPS51r9VS9kbT6XXHsoCQkWbCrWMdqTFv5UVRrakqM5AGl7KLmkj/ZWObZxzMA+q3UtPDHTieqZWNPMytkjylu17WPVXdGWm3RZhM2JxSjkPyg2B9LDp7FdMyElzaurOXNctZFck+wNln5eFyUwfUYnWwTF2rXUAc0D/UCP6KL5+RO2HDMYM8Ido6Sm5d/pqVzzWrc6sbcNjJVRMMkhaHWJ0c8EadOqzOps0BcZ2afpzarrV7a6Bsjp3gOcetMQCO4JC5GVrrvdVw+2Ui37KsbbXI8i9xQ2B5BMZ2TZU1NMSYqmRjuuRxUjMWOytlGu5AWumqWMDc/LfY7ObutG2uVZlFK6ToX8cxKSLkzYjIY7EepuaywAvkdrJ9cq9G6mop4jIaujp3A/4euv2VVNyI4ZGtqXuLnWtC0C473KyWSKXljR0PBNtKUrRxxDK1xLmHL3LTYrQxlEyIOe0OkH6GtIB+t0qucGV0cb6hzAbAPdc/ssbi5twQ76rWnIwbUH6m+jNO5zzNATc+gNJH0XSI9IfB8REHaOLW57LhRBwNxE9xOgsri6aFpzR1LGkd3ALOWO3yb4s1R4PSUxJpJDR41iDXsFyz4fK3Tpe64dXPJUScyurJpT/m1KzwzSFpyMrC07lrzqtEVHNNFJI+nkAGmZ5tYqVDQ7f+inl8RVFfkoEYsXRzDwCN1TJme7Vzb9wrRCWOIJBt0Vb6eU2fk9J2stU16mEoutkaIKSoc05JYyB5K2RSyU7Q3lUkj765rl32XJDHsByuIPYFONrLl7yXHtmKTjfJcZ0qSOs50lW4hgpozbrGAPuuXVUMzDZ8sbvDCpRzRghuZ4H+ta4/4eQea6YO0sRICB3vopVw4Kko5Vuc5kMsbgJLsPsugwSOjs0ue0C1xF/UqcjaOT1x1DyzqXbpNrZo2ctlS/Js1h2CTk5DhjUeXsDqK4JlmZHYXsWm58aLERTmVoc2YsvrYC9laayWN5LnZvN1DnNkJLja/ZOOpckz0PgcsEDpyKRspj6cwgEpml5bg2pgdAx1jnLbkDuruS50ZMIDh5cP8AdSeyaNkfxEEgZ0IcNUa36gsa5oz8jCg43qKktzWDms3HfVKdtGDanM0hH63Otf6K2UF17Ursv6dSsbQQb5LKlb3smVLakVSNyk+lw12KGObfW48rVzWnV9MXjr6rXWeZwdfLHy29Be60TvkwcVHhmiKN1RoyaJttg91iVfSVElJLeYSyRNPqYySwJ7rFFJlYOW52bsQLKZfUONyQD9FDje3YuE0t1yaRiA5rnjObnRjrmw7J0kkc9a5007qVoBLfRe57KpuLVrIjEahhjBvblt/rZKbGKyohEUk5cxpuBYb91Phvsv59DV5o939v+mys+Eiu9oM5cNTI1zSD9FdRyvo4mTPeHseLtEUpDmHysD8SmqWs+KrZnZBZt2g27KdNiDWQgTVTrsPpbk0+6l45aa5Lhmg5Wti+vq6mRofJVvdG46NfIHHT91jMlLJC1jQ5soBL3Odo72RPUxTuzxvLQB+sC5K0YdX0RnaMQhjfDsS1gDk0nGN0S5qU92ZmyA+mOFwsNchJv5WwVU0tuW+JpjbYMm1J9tFN9TR0dafhpTyiNXR2uAeg9lA1eGta5zfi3PubXDbEdEt5b0aKo7ORVC1jXO+IiDz0DSW29lnqHDM4NY8a6Bzr2VzcSg9ZdTudIR6HF4s3/dUSVGV122Lr3uNVUVK90ZSlFxqLJQ1LKcZnxMk8PJ0+xU4n0z5eaRTht/8ADdmt7q0YnJUvcaqkpp3OaRnkGX66WF1kEZc57W0hsTcFgJsml6i1OtnZZLFA8F0VQyM/ytJ19ldyYDCWh0kjgfmzaD6LFLGKdwBFyRexGynDBUTPywxtcSL2Lht9U2tuQjJJ8bmsCnbTmO1M6UEnNJmDrdt7LTSS4XTRiSowmWokNrXnysP0AulHSQMhhNVhb2uLHOL+ebSdiBY2/us8kdOxlnU9S17h6SXWHjostpbb/wA+DNd470idZiVNPO11Pg8FKxgIyxPcSbnckndElVhzpmmGmq448vrOcF1/Giwt5LXObO6TbTJ3TihZzWiOoBabEuItZXpil/8ATJTnf/wtjaX1jDTUtRMS6zWm4Lvstc8mPinMM1BO2EvDiJICLkebLQ+CshLIaSsFQJtQ9p+X630Wac4nFVRxTVU8mVwsBNex7bqFJSfY2eNwW7a+BVBidXTNMBoqRz2vvd8ALh49lpilrKlssvxdFTh1rxktaT7Cyy1oZJMXMjqGyXu50kgcXHvoFkqA+NxzQub/AKuqvSpdiNcoXb2LpY8rieZHIeuVyA2aqkdI+OR7Gt1LBsAsou9hLad73b3Gysilkiu0wztvoQ0kadVelmOpX7gPKIDY4nl/Uk3/AGV0QgZy/iWVDdy4W0I6WUJDE97XUudmmocdVGVtVIM3LkeB6QbEo52H7O5qq3wOY2ShhmjjAykudu5Z2PtI01EMkgcdiT6vqsdnseQ4OBB1B0srxJeMtcS4DYZzojRSDxdTs2fEQlx+HidAW7DNf+qjEyuqpHQwFrjluc0jQCB7rEIucTy2htv0l+6uDIuWGiFrSNM1ySUtKXA1KUt3x7hyyyRHK4RuLdxuFA5Xkc5zWA6+kX/ZVysc1xALSB1GxURzGG4DT9FSSoylJ3XYhkaHkA3F1ohpWvYX81osbWvqq3O7sF/CrvY3ym3hVuzNaYvc6Hw0DIfzJJeY4Xbb5bKh1NIxuYxSDNq13QhVNe1+ha+/Tqro462WM8sVLo2G3puQLqaa5Zu5RlwiuCNrngSuc0H+UXKtmpzA4ggOHS4RU0c9KWmaGeN1r+ptlWxz5g8l0jiPm16I53T2ElVxa3LIpGte3NDGcpvbLe/utNLq6R7aSCRtiSJPTb21CVNUwU5jmgq5oahupzRggHwq31LaiSSSSTPK92YvItf6KHbNYtKrZqpsPrppM4w+pfHqTygQAPdKrojTvbMyiqWQusLTWzZvCwmtqmh0bamZrHCzg15sR5SbUnM0mSTMP1Em4RpkHiY6onWUtS0iR1LM1jtiYyAVU2nkc1pjhnJ7hpXSbitUYi2StdOCfkeSbeQofGvkux/qznUNvdClNbUHh427sqgwyeSn57oKsMJ0cIzY+xV7qKnY0AjEHvuBl5dr+FRL8bT5TLFUMYfkEgdYjxdWx4rWxPGd00Z2a4Ety+yT1vdFRWNbNGSSMOlLGQT5wdGv3CobYGz2u31sr5ahxnc5xdISblxNyVCWYFga1gaTre2q0VmElFttFDtXkRsce2lym2R8ZOj2u2NtFbGaprvyA+/doW2lq6yMu5DHOlIsSGA6JydE44JvmiqIU742OFTK2a/qzj0ge+6VQxrLtLmuJ2cw7p4hPUOlaKyF0bwNjEG6eyzGWNuUtu4di21ioSfJq5JWgJkvlAdceVKOKtcwOibMWnS7QSptmZI78x4YHb+k/wBlbHHmH/LzD2z5U3KuxKhfcIpq+NwZIHZiPTnjBP7q17ayqe50lO5ziLl7IrbeyTKaone0sqY+dtZ0wB+5UHU2KRuLQyV1zb0PzA/ZRtfY1WpLe2iEjKTlNaRMJAfzC6Pb90E4dHG4MZK9xHpzgAAqbqWtykz0dQLbvLSqM1MRkySB38zv9lS3Ie3ZfMpeRI85YGNHYIcwZbyRka7tIWhtKZW5opGk9W5SrY8IqQwzPbE6MbjmAE+FWuK5Zi8Un2MUJAeC0PuDpbdaf+TYG3pJpCPns8tut1HgVZWAupMNqbbh0d3N+9l18OoqWiLJBTVdTOwfmsdCJo7+wG3uolliuC44JPk85O+hlZC2CgdC61pHukLsxvuB0WOojYx55YJb3Isvo3ENBg0+Fiqo3VMGcNMr24cREw7EAhot9188ndGXFsT3lo0ueqeKerczyxUe5Q1rS06kH3TbESdHfuk0AO0BK2000Wz2aDoditJSa4MoQ1MpbTMJs6S1/Km3DuYRlqoRfbO+33Wmaemdm5FIxpte4feyi2rbyeU+NpzG7jyhcexUapG7x41sZY6V7nZRy3H/AFi33WmbDzFCXOkpSegbLcj6KOena+7oS9g3aTa6vlnoBBlbh8YcdQ4TkkeLJOUr4HGEa3OU+IjQWPsUmR9hqFqe+B2jKUtPcPKjyZsmdsLwzvutFJ0ZPH6FDrkkEKFrdVN2Yb3QWt0H91SMmVHfQIAuFY5oGxVsfKEbi5ri/SxvoPdOxRjbM4ZcX1upNaQNVc7k5Wlrjm6iyWSPc3tfulqHpKsrm62sD1UcpOy1RzU8E2ZkLZW/yyi4P2KkyencbPo2hpsLsJBH7o1P0Gor1MRBHdH7rXUmlzO5HMazoHEaKuJ5DS0OOU9E09rJap1ZmsnmI2Ktd9FUWnumnZO6AP1JSumWWSsnsTbEE0kJgMAqWX0k20SaBYlwKYDdbApDRE7ICZKigCbRc2UwLH1Dbsq2kg/3VtnuN7X9kmVEsaYxe7ZATtYpsaHB1pAB5CgLbF7gFFxDSbP/AGU0XZqiELgBIBoPmAUXRg/KAW+yoikN/wDEsOxWlln6NnYzTqbKGmmWmpIAYom2cXuPgWUoImTPzVAlDCLiw/urIaV8jCfiom2/S52pVEpewkc0kbbqbvZF1StrY0OhwuNrg6WYyX0bYWWWUwXIjc7wSFnlF7lzte6iO+ay0UPeRLJbqjVJcRhoeHNcL6CygwBjPVLlv0AKqaR+op8xg0PqRRLknuBfctA36kdUK59U17GhrGNy7ECxQjf0E9uGesq+IeDoAXYbw2TOwtdHJLM4gkOHzAki1gvNY7jL8ZrTUvpqenGXK2OCMMa0fTqu3RtqJ6uQVL4MPqJ2SMLpaK4Oh0AsbEkW20XJg4dxeokfBS0ksuXJfKLfN8uhWWNY4vd7+9m2XxJLbj3HJa10jwxjS5xNgANSeylLFLC8xzRujeDYteLEH2V9XSVGHVLoai8VRGdWhwu0/Tqs7nuke58j3Pe43c5xuSe66U74ORprZllM9kMzXywNmYN43EgH6jVEUYkeGlzW3PU6BFLGyWojjmlMTHOAc8NLsovvbquriGEUFKHfC41FUyCTJyjA+J1u5zDTVRKSTo2hCUo2uC7Do8LdhFa+vML5Y3tEBMrmuN7/AKBuO56aKnD3UIrYo8Tln/h5/wAVkEvqI+uidbgjqOnkmjeytjhka2WppzmhGYXAB0N9+i34E7hJj6n+OxVhYWjlcoatNjfr103XPKkm1b+B177KVKvucrFYaKSrccGpZmUmUFoqJWuefJtos5pZWRkvpfl3OfVb67EKCWsZNQ4U2GBoDRHcnNbqfJVc8cr4n1LaUtZe4vIPSPZaRk6V/c55wjbp/Q5hBaSHQana99FDUfostLpZJAckXu69yqS+TW97lao52Qv4VjHRG/MDh2yqFn3Fh+y0GOpdlDmt0FhsCgSIsEBc1rpeWCfU7KTYd7KqURNJDJuYL6HKQruTVSsMgiu1gsSANE/iZhCYHRRgEAfIAfuhDZkFiNCpsFzYvTfmuLtaPZTGYuaCxv8AuhsSNNPBHLpLVNYGi98hP0XpcLl4ZlgEOKUULJCL8xsctxYabE3v7Lz7IIWf+qimbnbdhiI+5WigjoGStFbWTQsLrOLY8zgO4XPkWpcv5G0NjsTQ8FTAcyrdSPZ8wp4JHcz/AO46Kp9FwY8Z48WrWxF2XK5nqHm1tlJ54OikJzVNYw2Bc5hjIPcWKpxOPhGwOHyTl+5aSQ32uQSsk+3mLa+BysQpsIZVStwyrlmgBHLdK3KXDqs7zhnw5aW1Bqc4s4OGTL183WqonwmWaLkUZpow2zwJDIXHvqf2RFX4dFRz0wwiCaR59FU97w9g8NvZdCb95Kpehz+Wx78sF+4zOCTaeR7gA5pJNgMy3QYg+OndTRQwuYTn9UIJvtvvbwszIpZi4siPp1cQ3RqpNhpVlJp3tcQbXHYpmJ7DqP3WqPDqie3KlgsTYZpA3+qzObJA50bnNzA2NnA/ui77g4pEmNYWHMHF3Qgptj5ZzFkgv1CqDnAaPAUmzSvcAZ7AdT0RTHFx7lsks7wAXS2v1JSYy7/8bl2/UbrQ0iTKZsQbppbJsFCUQtlsJhI0fqAtdRfY1lG92Lm5QY31UjmW1yk6qHMhabCaRv8A7Qrg6hJtZwPUgptp6B7tJJj3tZFpci0t8UZ8wkBJqXX7W1UhkG8rrLQ6CiheATO5mmmn1UG/BvqQzJLHBf1SWzOA9tLotPgHFx5KSYQbkuctVHUUgf8An81rL/pIJ/dUzCnLyIJHvYD6SY8pI72uuhheFOxd4ocMp5Kitf6gQLZQNxb+6Tqtwi3F7HYw3iSkpqeVhqq+OUv9EzcrmlttAWkfvddMcWiowgUbMVfT5Rl5UVM1xdbY5jqFxIuDsddTSSDD6s5SWEMh0uPPVaML4TxmlnZVPmgwx7XXiknlAIcP8tif2XPKOP1OiEptrYyVWNVczg5+KVM5AsBURtOi5DjLJIMjQ6+5LbXXfxfhitiy1UuN4fWPlcS8U7iXDydNFz6mnETfRxA10p0MbY3Cw9yAnBwXstfz5Gj1S5TowNzhxjbTU+YXuZN7q+H0xGKbDKaZ5NxIJCCPsbKgRwlxdNiL3vzWuIi6476rdHNhEMDnPra2WdurYhCAx/vrork3W3+yIJXu6+hJodBFy4sPhErv+oH8y3sLqmWkxWiGeTD3NDtQ6SOzT7LV/wAQiClcMOgdBI7R7+S0hvsVlZiPxVQ2bFqiqDb3/LiDh9ASAoisnLW33N5SxcKRnkNU2xnpaa7m3B0v+xVEUrQ7108W/wCpxA/qupU1GD1UnMnrapoBtljpWi46dbLKyto4Y8tJUzNzfNzKdpt2WkW2uPyYyjHV7X4LqqqgbE0F8DXW2gJs39luoa2ipogTWMMjmDV7i6x7W6Lktr6yRnLdWRgF18r4AAD3vZTJdNSOhlqqQAnMD8PY37ZraKJY01T/AJ9jSGVp3H+fc1yxfxCW/wAfQxMJvmDyAPosU2GSiYiKZkzerw/RdSk4boJ6a0OMQGpt6mOjGQexv/Zc/FaOKkhZD/EaWot/9IG7NeqUJxvTF/YJwdapr7meejnp3ZCWOJ2LHBw+6pfzoxvvpYhXRYex1OJfj6bKTbLns4e4WWWAsdcPa8bXDluqfc5pKt6+5IRyaF8Ti07kBXy0cTSHsMzWkfqiO/hRga0kNfGWs6uDlKZrnR5Ip3EA6C5Jsle5aitN0URuDJWkxh5vqxzNLLXN/Dh6nRuY+98uU/3Kro6eMvAfUNjkvq59xZOpoXOOYztf3dmJA9zZDcW6sUVNRbSs0x1dMxvKiAbfXMIsx/dWVLab4YSfETXaLBr6YgD6rkRMcJf8XKQfmBK6j6ipdT8kYk/lkEubJKQw+LKHBJqmawzOSdowj4R8Uj5ap7JQPQxkFwT2JvoszWROF3zOHezFdYxEyRTw6dA5E9bK8AZIQB/K3f3Wyvsczp8iY+MxOa6VgAOhMdyfqp001O4FtRUyRgHTJHdUOrqj12bFZ9r/AJY6duyzsc4vF2A36J6LW5Hj09jrNq5JQ2IYo4MabtDgQAVZT0eHkF1XiZuT+lpKyUVe+lceXR073H/6jAbLoYmK9oirZTRRNkaA1kEjHE+SBe31WUotOlt9P2OnHKLjqkr+v7nIn5LXOEdQXgE2NiLhFNO2J+YPbcdHNuD91KrmfM1rSIgG7FrAD9T1WZrD4WyScdzkk6nsazLSgOc8HMejRoiCbDvV8THM649JY/Lb30KyEljr2GncK41kr9OVDYgCzYm/7I0jjk9fwT5MErrU8gYLX/NcFABjMzXNbIbWBa7Y91G3M9LYn8z+Vrf7KjNbcEJpClJeheWyFpPKdkHW2ithqWxaPhD29QTZW0VVhrWFlZDVuaR/0pg3X2IUHwU+USQTHKTYMefWFLrhopRfMWTdUxSksjoAQ61hclwPgqdM6ggEjK/C53yEHIWy5cp6XFtQqpIZ6SRrpnPY/wCYZXj+ydU6VpY6ohe4O9QLn6uHuppPZfk0trd8/AlC+jErJajDXugAOZjZ8pPm9lFn8Oka4BlQ06kHMCB4VVXJDLlMFKYABYgyF1/uqY2RZCZHOB/Tl6qlHa9yNVOtmbaaWKllDoqeOp09TZ2kj9ipvqM0xk5dLEDswMJDVkhELXWeXEeCtUAoi69VUPiYSLZW5iBfX9lMtjSDbVFcl5XEgt03OwUmSTRMLG1Ppd0ZIbLVXMwVrnikxWaUZfTmpstz23XLhkps35pkLezLBKPmXH2CT0y5+420kkouyzifOq1N4exR9MKllK58JNszCD+26jBHHMXCItY4/KDJb6XKsiljiIbL8S7INQx+gPcWTc5/4ijjhyyqnoKnn8p7XtPVr3ZbBdV1BNRxxPqcsp+a4kLwwdiFyJKiN7i4NnLhbK979QtD8bq8vLbVVgjLcrmulzA/9lMo5JPYuE8WPkrqYppM0uWFrCd2ED9rqDoqmSAujivGz5ntZt7lQZPTOnLpmSOBH6SAQfsnFUUzQ5rmyeo2+YiyupLsZpxk+TLeUtyh32S/OjkIdmaexXSNThzWBow0OfYDP8Q6/nTyoVHLne19LTCFpdaz5s39U1P3fgjw++q/qRjmcQGkxhwGj7kEKRM8wvIBJY7l+qTqd+j3wNIG9nXutEcMT6bM3CrvL9JecbAdrf3UNo2jGT2ZVNNLTua58EYaWg5Gu0t5soPry+PL8PGADe4vf232VuIYbU08pElI2P0ggNlDtPusbYJXTCKOI57fLdOKg1ZM5Ti6NIlbPCWxUoY8EHmB527WVtNSVdQ8mmL2G9m/mAG657fiCXBjbW1NuiOc4WLgCe5T0P8AxJWVf5F0lJWyVMkUge+ZriHg6m6zvilhIz+kq3nyNBdE4Nv1B1VbQ8nMWhxPdUr7kS0vi7L6GaopqqOogmLJmOzMc21wVtr5aiqnE0kjp5n6vuwA3+iwNjYfns3XogwgtL2OcQ3qoaTdmsG1GiUomicWStexw3DhZUyPe4m2vRaCKZ8Y5ksgcBrYZlmcIwPS5xP+lVEidojd4+YfdWxB7XNcCNDcaqlhaXDmPIF9Ta6uHKJsJWt31IOypmUDXLUF7i7OxrstiT1WcVFTGTyZnNG/ocQiKGmc/LLVADTVrCVbPBhwlDaaqmdHbV72ZdfAus1pW3+jobnLdfkUdfVOe176p9x1cbrQMSlmljM00bzGTk/Lbb66a/VZJaFrBmbMxzSLi5AJWcMDLWIzdLFGmEt0LxMkOTq1GJSTuyOp6C5sC9sQb17rJI9zXuAbHa+uTUKmJmdxuC72K2SQyRyg0rJC0AH15SUqjHYrVKe7NEFRhppnCqp5TKToYmtHTv7rnPa0tPLjeDfbddOklrYQXMiD9beuO4BVU8Nc2ZsYpm5yMwa2Pe6iLp/9NpLVBfscrQO1zA9FdAXXN3OA9lqmw6uhi509A5jHC+Z4ssr3ggAQtZbfLfVa2pLY5lGUHudd0tLVUTjXVFcahtmwuBDmAeQdfsstRHFG+NsNS6r9O0jMoB8arLFme4M5TnA62aLlBgDxYsy2/UeihRrubuepcFbXOY8FtiR1utLzV1by4xOlcBrlZ0HsqHU0UeYZ726hX0zNLwTuYXaH12VNrkyhGTdMtoGUbrsq46jO9wyuicBYeQRqtddg3w8QqKCeZ4zaMI9Q+yzGnaJoWsqw1zt3PkGUKT5Rn5jqjO9u2Wwv9QsZOVpxZ1QjBRcZIWHx1M+IsdWNkcb6GYOsfGxW2rrqqh/KNOyF1j6ZYGm3sCFmrKieqjjlc54YP/y9ybabX0UKusopWwuqJKupcxmWz3beLocdTTaFqUItJ/NlFJXOEgM0jcgv80Qdb6LcKhk5LW/Audb5zEWn9lyXXkF2xFg91XGJmSAxl7XdC1aOCe/BjDNKOz3OtGzkTtnlippXMNywtu13uFCaY1ILPhWRXffPGMtrm9kfBVLmNdO+oZn3LxofKvjpWOzQNxKa4Fw0x3afqCs20u50x1PZLYsqcCrpIo30sVRLTH/qlzSLrmTYYWT8rmgO/wAxAstpfynt5tVLEwaEMu7XvZY/iKeQObLVTM10/KBv76oxvJ6/YnLDF8/iMUgpg4Sz5z2ZYj73UQ2nlIZEJi8nUXFvok8QNkDIK9z2FoJLoba9k45GwhxbUw5m/L+Te/1stN+TG0tux6HDOHMUlaDhrqkxW9TDVNjIJ6Wur6+gnwCR0Tzi1CXgjmtmHqB6WDtdfK5OC4kZ6pjqmtoIQXWIqICWW82XWqH4bW1Un8Rx7DIoyLZo6eVwuNBYA9lztZFLzfhmqnDT5eDE7AsVlp4ahwrKmjqMxDo5Q46b3bc21PVU1uCUOCsjlxenxDnOIc2mdka17fLg4kfZXV0/CdPVn4ds1dS5AAI3ugu62psQTuuRidXR1mX4CggomRtsRznPdJrvr1t2W0Nb/lHHPSYc8TpnGKAtaXXawm9h2v1WuV0kkLBJ6WjYZP7rNALH1GMhXtmabxFrsh3tqtJchj4Isa2B4Lo4ZQeh6fZWOimewytZBGy2hzDVSkhpXOBa2YxNHrc1oaf6lYpWRB3pLg2+l90luOXlVM20eINpGvY+CjkzbmSLMR7arLNWCR2jIreGAJNbTXOZ9xbrdBpohctkilA6BxBVJRuyNU6pEZqgSaiKOMafJf8A3VQBPyyO9tUsgBuWEt7AqeeO94WmPwTdXxwQ23uxtp5pGuLWggC5N7aKoQv1028rTCKWRjzUTTNeB6OWwEH31VLmaemQu+iE2DigaMpy2a4+6ZiNgLN131VR0F1Jt3DQm/ZBCaIObkcbbK2FjpHhrIzI4/pCg7u4/stdDBDUF152wuAuC4HX7Aok6VlQjbpEmSR5LCkijdewe6+v9kpZJAS15Y4dgbhUSEA5S5zgD3TLYS27C4f6iFNLku2UvDrEAfZRyuB9FyD1srYpRE/MHOuNiCtTKkTQhjAGvzXuZN/oqba7EKKl3Mwp/RnN9NwoiNhaXFxFvC2x86IutKWEtLXWsbg7qLqSmLbR4gP9L2EfupU/UrwttkYskZaTmPgKoAE2N/srpGcokCQO8tKjHC6RkjxLG3IL2c6xdrbQdVojGS7FJbukB5Uje+pSsbbKjMmAbXtcBRJPQJsA1zEj2UxZupaD7pFVZVql3U3G52A9lEFMloApNc4HR1vYpNsVdHG07tv9UmyopvgGNOXMTdWNkyC5A8XCk5tMIT+Q/mE6ESaAKJjJaA2F2vnUqLTNlFoTSw3Lg2/hWHk5QC/X/K1U5GjRwePdOnje95EBAdfTM4D+qGgTom+SJu2ZRZUQMFnQcz3cQp1VHWUrmmqge3OMzS4aOHcdws5eD6eUL+EJJoUnJMtknpXEkUhHYCQql7m/9Nha3te6Vmn9JB91fBSyVByQ3c7sq2iTcpMoYb7sJ9lO7XNs1i1tHwwMcmZpBIcA4bqPxEbQQ1jHaWGbop1XwWoVyVU9JNVPayCJznuNg1jbkoWkYhlMXLiijezXmMzAn31QobydkXGOKvMTzYZ8ROX1lfLGGXhcGgOL/wDMCdB7LHNPLMA58xJsGgA20Gy62M8J4lhLKY1T6SQ1BIYymmEjrjoQ3+y4b43MLg5p9JsTYjVXHS907M5ua5VET7/dHTdBA6IDeysxtjjcY3h7HEOabgg6grS+WrldNNLNKXTi8j3uJMgv1PXUKqlpZamURQ5cxBIzODRoL7lWVNJVUjY/iGhokaHMs8G4+hSbV13NIqWm6dG6hwXEakRRB3IiqHZWuncWRucOhJ0vqtmMcF4/gzXPraSzA/IHNeDm0vcdbeVkpK2evLKTEMTqxCCXRtDTKM58X3K70VXgOINj/wCKMWxKeWJzgCC4kxgaNAN7G91zTnkjL3fBnXDFjnC7+rPHHmfKXfS6nGJn+lshJNtC7Qq2pGHOqZTTOnigzHliQZnW6XI6pH4AQel0zpT00DQujscml29ydRSVMA5khha29vTIDr7ArKbtvqD7Kxnwgb62yFx6ghQzR7BoB90IlhHIW39NyRYG+yfMJd+YMxAsNUD17uaB3VkbWRsMkmSRm1g6xTZJDmOLbF7rA6BUuJJOp+qvcYHDMM49OgFjqqACdgfshDAg20F0w15+VpJ8BO7mktIIIOoPRWU8tRFKJKZzmSM1DmnUIEVjMCL52lWicRuuJnX8i6vnr8SkANRO52Yl132JJ7rp4fxVi9FSfDQTUYYDmvJSxucT2uRdQ7rj+fQtJepz6c00zgHz1Rc5rrhkIdc9OuyUTaEU7Q6irH1GclxzDIW9rWvfzddyLjHiCqHJZUUDM5AF6aJgBvvciwVlRxdxDBF8FHW4c10b8nNpY4w8nvmA28rO58V9/wDhdLk4/wDEaKmgkZBhUUkkhuJKhhJj8N1WQ4nPdpAjbkHpAiaLfstmK1GJyTSQ4m6F0sR1cS0kn/UN1nOI1TmhhipnBoDRaMDb2VRW26+4d+SuoxWrqwRUTZrgA5WBtwPYKmOVuV7ZJJWNIvYDdba7C8SoGRy1tKIBUAOju5vqB1va6zyyUouBE9xLLAueNHd9tlS09h1JbtmIlrr3vZJuXqSpuJDtC36JszPNgW697BadjJO2WuhpgwGOdznH9JZZRiiiJ/Mkc3zluhwlicWOAuN7aphkrwCWix2uRqo39TRtXwS5VKL/AJzz/wC2ys5dCC3815v81xslT0/PzASQRkf/AFH5b+y2GgZlvJUUMQboSZM2bzpdS3Xc2jBtWkUhlDzi1srTHfQu0WiV8d7QMog5x0dHm0WNraTXOY3EHQi4uuvhkfD87D8XP8O5v6dfV9VE3pV7sqHmdbIpfU4iIww08OVwtnEHzDvdZTBXep4jGUbnQW+itxCWluYoKrOxvyEOdYfQrJDTSTucfiRoL6EpRW18Dm1dXZKN9UblpYPJAVlL/ExLejzGTf8AKaS79tVvdwZjxpXVlPCypgDWuc6Cdjy0O2u0G9/Fk8Pwfi/Dn/G4dRYtTPDNZYontJaquHqjPzLszqVreKq3DhUTYjR08cQ0gbKIHn/22FyuU44jhzqeTEGU04nbdmeqzG1+uV1x9VtZxbxvQ1bZXVuIumjGgnhzgD2IVWL8Q8UYvK2oxdj5n5bNzUQbp9GhZ6HXCoqM2pcs21762KhZIyXDo2vFxHBVOkc36XK49TPJUObJU1bWPYwNb6XONh1W2gio5qGWTEsfkoJs1vg46Bz3O830ACyTxiXkPkqq2W4sDJTWsBtbXVZxgonY5uS2JSRYfLTGZ9fXzzA+ospQGge91hbHh73NDKuqbc+pzob2+xXREUbY3iKqbM4AXjylt76aeUmuqKSn5lDiNPG9hvy8xzg+NE4y7L+fYTx3u1/PqZo48LjaTNWzyODxZhpiA4eTdQkmwqaaQOdLFEPlyg6/QlZ8Rkr3taaur5lxexdcrJBHNIHiPl/Lc5iB9rraOO93Iwllp6VH7G2Kkpp3u5dbTQsO3Nc7/ZSidHQscYqgSTG2V0T9G+4I1XNYyUA2LQ077KdPI+CS7eU4n+docFbhfcyWRJ3VHTZUNqi92ImrqHn5S2UafcL0dJjPD8NHyW0eNPOTK9rp2lv2XmTUOldmfNBGf5YodP2Wf4maIl8VQ0OBuPTYrCeLXs/9nTHLo3OxWU+GB4dR0OJgu2ElgHe1limo6Zrw6ehq42gjMwN376nqpsxvF7Nl/i5a5puNNQfssdViFbPKZZcSkledzc6pwhNPd/djyZcbV1+CmsfQ81wpqOaNt9A99z/RKkdTtla+aklljHzNa+372VDnvkeTJKb9SdVZypWsvHPv2JC6KSVHFqblaX4Ns1ZhxkcKbDpY2Eg2fOSR+yq+KgdKTaWGPs05j91mbBpd87QT3uq3RAOID2u8jqpUIlvLkXYvmkprXgfOXX/XbZSbiFS1pDZ5GZm5Tl0zDysvKIPpFypAZD64ye4uq0xM/Em/cSdK8tbeRxA2HZVuc9wsSVfz4smlPY33zFOKpa0k8gH3KN12HV7ORlBI7qQcLWc4/ZaX1cbnXdTM3vvuqnyROOkOX2cmm3yiaS4Y4WU77B1QIze3qaT9dFvbhsL35Y8VosoF87i5v7ELmhjTcjK33KRs3T0k90mm+GVFxS3R0mFmHVTjFPSVdhYF0Zc0+wKn/E5AHD4ejcCLaRAW9lym/wCoK+JzWXu5h91Lgu+5rDK+FsjTaYsdJ8NG8EbgDRZbSA6sAv7KL5I3G9reyjmjFxr900mRKSZY6V9sr42H6KMM3LJOTfzZQIaf1C/ukMuoJTpURqdnTiro5DH+S5jozuySxd9VJ9OJai9MDHrdoc4Ot7lcwcm2rlptScoPdJd1/lBIKzcK4N45HJeY6v8ABqpsRrHVNM9wflc0OBdf/SlBLBR1Gdwp36asmizArkte1kmaCaRnbVSe7nP9cz5PLlGiX+TNY5YpeVbmmtrYayTMYKaI7ARR5Bb2WJzQ0OJex1tLZr/ZWhseaz2FwG+XdSa6gaHAQTS++lla24Ibct20ZmFsj2tEd9flzWv9Vt+GtM7LQtJA/wAPPmHve6zulonRlopzG8bG5N0QCmzf4zxprYEJuyI1w6Zs5NYKdx/hbWhh1k5Zv9bqqlp3Sy2fTB+nqB0spSyU4Ia2oqJm21BNv7qbJ8PiddlPUF38xltqs7dcG+mLfP8APoZJ6UZiGNjAv/MospcrAXRB176tkGw8LpQuoJHAzRPyn+VwuqvhcNu/WX5vTm3t5smsnZkvpk3qVGepOHCW0VNM2Pf1yAu28Cyg+ohH/po3xjy65W2SmwyAOfFO6YnQRuhcLeb3WGrcHua6IR2tsxhFlUWpepM4uKvb5EXVb5Yyyolfa9wBZWcmgewZKmpzZbkGMb9t1VJVOcwsNLA0kbtjsVETuLGRtgjBA+YNsXe6uttjJSX+W4GGBsZcZZhNm0by9Ld7338WVr8RqnU7KfmHkxm7AI2i31tdQF3WzR++u6GRvkcI4GuL/wCW6NnySk17JnJJcSb3JuVrpnwnSR+XtoTdSip66UFscL3N8gLXSYbVm5aA2wJI0v8AupnONbs0xYp3sil1Q1l23Y4dw4gEKrnQlwJYAOrQ46roT0tZHHlDfy9weW0/uFjkkljuwSC3fIBdZxcXwbz1Re5Q6SkLicstiNNflKpzxDUF5PW6tkNVLqQXi9h6U2x1fy2aCdLWC2VLuc7bk+PsVQOpuaDNn5f6g02J9lrn/hJgIgbV80nQuc3KB9khgmJ5bile7w3UrK6nqIv8SGRl9szSLouLezFU4LzR+wMp2yC7WvJ8JStjaSI2yADuU2yVDQQ2RzQRqAd1WHyAn1u13TVkNxrZETcm5v8AdWNbKGGwkyeL2UmvdJbPJtoPTdWgjLlM8mXshscY33M7S4O0B9lcHs6xuJ7XSysykmazhsLbqstbfWb9kbMN0B11DQFdE57fUI43aWGYXWc26G6Qfl1CdWRF0zoxxVb2gspmEE6HlpikrIwX/Cxmxt6mg6+yysrJQ3LzHgDYBxUudcZjUuv9VnUkdKljfqRkiqA67om3J6DRTa2drSx1HG5zjo62o9tVB8g0PMJ+qmHUgBdzpS7oCwW/qnbohKOrk2voKpk0Uc2E8tz2B4F3AOHe91thoaNrTJLTMI2c2OZ12f7rnfEM5Rb8QLW0LibjwFfT1dHEHCV0Uluoc4E/sueam1sduJ44vevnRvnfgssWWClqmTRm7nMc4lw9jsuRPVOa9r4X1ejbXe7Uex7JGqdTyudS1YbmFjkcdlVJOHWL5A89RnJv5V48en3k5cyktqT9xGSbm3c98znd3uurooqSRjQ2rcJLahzdLpBrDBnBj3/m1t7KgxwtIJmFj/Lc2WnJz2075OvT00zPzYapjnMNg6I6hZixjnPbNJNmJ9Ra3Mua9+U2ikd/RLnPBvzHj2KlYnzZb6iPFGoxvY7/AAJXN7lpF1E5cpywPBOiofUSvNnVEhHkoEj9hMfsr0sy8RXsSaSy92X9wkIy8k8twHcBSjhmldZj85PQDVWhlQy7TJlsdWkouhJNiZFC6zS17X9SNSVRLAQ+13D3C2hjnsDfiY2uBBsGG5+qrqoqwNa+Ueg3DSTqUoy35KnjTjwZwJBdoe7bur6MPc6xEjm9TlJt5VMccpOlr9rq1slTTt00ubGzrJy3VEY9nbOpLHJFSZjDJIwO/wARsl7DoC3oqXQUckYl5lfHNa7w2EZR2sbqqkrKqKTnRPYxw3Jdv9Oq7beLMYqQY56ammZpm/JIzDyQuZrJHhfc7lLHPZ/g4MpaGgsqp3i+zwQqmPkgaHx1MVyfltcj9l3azEqqpj5MdDSRM3BZm0Pm5XKmjrIZ7EwiQ9Q5pBWkJN8meWCTuLM0tfUTNDJHxusSR+WBv5ATDp307nGogys0EZNifYLayCqdA4/8lfNbKZBmP/ZX0WE4q93MpqFs43DoZGmyrVFLsZaJvuyrB8UZT5mVuG0NbBa3LlOQ36EOGq2l0dPTTVL6HCHwzP8A8ISNdIwX2bY3HusUkdbE++I0NTy43eq0I+17WVWITYc9rnUbK2E9GytaRf3FktNvYV0tzDNPCXEMpgxvvdQD4LXyOv2OyraC9+t7+Ar2sniZmkgcGE2zOYQFrSRy22yAdEL6GybpgD+Xdo8hWstIMrgGgbKbaFxILamC5NrFyVruaKMmtjG5+bV0jr/6VWDY3D83uFplidGSHtB9iqCRqWuaD2KtNPgzmn3NEbgGF4Mbj1DmpyTNy5csA63Y3X7rM250zN+6m2nfIQGFhJ6XSpdxqbrYuimLAcoZYixuLoippZw5zAyw3uVezCKxsIkdSh7SLgteD+11Q+inO0MjR21UKUXwzXRNe0iySjfE0SPawA/pus5YN26X8qBicDZztR3KYYLH12Pa26pJ+pEmnwhOiZf5r+yly4gAWvde2oIsqi5w0TaHuOgVb+plavgC4X8K2OWMbmyqyEE5mqLmgG9hZFJjTcdzoRCmeDmIN99d02wwyuaI4ozfTLzDque18QBzRknpY2SMjf05m699lOh+pp4ia4NdRRPicczYm2GwkukxpscjIWm27nBZHG5uXuJ7lIG+mZVpdbmakk9kb5DOAGEQDTcOGoSjlkgaHmOnfrcZjf8Aa6xhttQ7T2RYuOgDvZLSivEZpkrszwXU8Gl9A2wKynMPVYAHsixv8mvlLYaghWklwZyk3yIa7pnxcJEpAjumQMX6KYD3aXFvdQ22JT9WU22QNETe9rqcMgjzZomPuLeroq0C6BXTsvjdHzMz2Xb2BVxlZawc8M7dljBUmut2+qlxsuM6Nck8bmi17g66JMLSP3+W5+6ovmOjWj2VsYdqMrj/AKVNUXrbZoa6nax8cjIHOktZ7g4GPVUk0zXjPEHNG+Rx18pTPiznMySw/m3UzJhzorMhna7qcwISS+Jb39DTNKHsj5cr5Y2MDWid18vgeFlbSCVz/wDmqdhAvYuIB9lXzIA30iQG/ixCrzh2gH7Jxi0KUk+S1jo4nASMZKOtiRf6rTHJRFreQyWOe+t3AtKwljuoPjRSa0NFyHB3QgIcUyYTafBplBEw5gYTbpsVsEsENM7n0kWZwBbZoP7rlukaRZ5dp4QBE7T8wX7aqXC1uaLJT2N1FUBzZIue2GFxuQWA6/ZCxspiDcOc0H+YIUyjG+QUnW6PV4XT4HQw/GYNxZNFjDWXhjfTctoNvUC8kj2XlZKiSd7zVTyyZ5C+S7vmcevuvQYtjPCM8EsOH8LS08nKyRzGueS19/mI2PsvNVMTIJA2OeOZpY12aMGwJFy3UDUbKsUXy7+df6Iyy7ECG3Njp0S9kgjU7LYwJakWJTDT0KhcglSaJCQGNLidha5QCZON0sbg+J5Y9pu1wdYg+FbSU9ZVzNjpoXzyuuQ1rcxK7uG4BxXTOcaTCpWumhe08yJpu23qtm2Nj7rHh3DWM1YkMcLoMha1wldkccxto35j3NgVj4sN3aOiOGeypnNFJVOqRTmF3OzBoYRY3JtZepfw1U4CxlZjlDh/okDBSOqQ57zuCWtJuPr1XJxnhnEcIxOKgrJ4ebK0Oa5kpIsT16j6hUQYZSZXvnximjcyTKAA9xd/mFhslJ6kmnsOMXFtNGjEJMPixPmHBnwsDg51K6YhpaegNrhc/EJaeonL6WjjpGfyNe537lXcukjdITK2rcRlbfM23+b/ALLFkDXFudv9lUUkZzbKrkHUBWMnLb/lRm46t2UjC8uIa9rrdipOo6hjmMDQ50nytY4OJ+y0tGStCfWylgYGxtA6Naq3VE0jruOwtsoEPa4ggtcDYg9EOc4uJc4k9UUgtss5zybnU+VvwfFDh9QXuw6jrA4EcupYXAki19wRZcsX6FMvf3ScU1Qajr1NdRTtaz+BwQyNblLo55NT3sSVLDOGcSxWmklw6kmqCxwaQxt9/K4rXPvoSuxheF4tO9hwyoja8tMgy1bWGzfcjXwoknFbOviVF3ybavheswilkON4HiLJHAcqSORuQHzYH7XXKr8PmoZmRz0FTTue0EMmGpPjRaanH8empZKaqxWofCXhzojJcEjYrG1tXPNGI5nSyvcA0B13EnYJQ1/5NfcctL2RQ9vLJa6N7CDYtO4WygraOlzGpwtlXdtgJJXNAPfRWOwbFH1ksEzWMqGE8wTTNZYjuSbXVFPQsldM2pxCmp+WzM3NmfnN/lGUHVV5WuQjaexbVYjQVDGCPCOVI15JLahxBb/KAdve6573NcSWxZR2veymIyTlY7N7BSdTStALhvtqhKK4Kbk+SpjbmwjJPZDri7XMAI8IdHIw2206FQs6+xKtbkcE2tkcbMa4+wT5Ml/8J32SidODeIuBHZaKeKumcRCyV7uthdJui4xUvUpFNI42yOHupmjfG4NkFiRca9FqkZiMMWSWQBh3bmH7qhshOVp5bbdbKNTZo4RXN2bI8Lhkhe4TsYY23cHOG/jXVYOUwE3y6ebXTkY0Eu5rXXPTRQ5bRrmBRG+7FJp8IkQ3drBYeVINflvlCGmNrdc5NtLW3Uonss4vbJm/Tba/lDBImG1dNIySGTluFnNdG8tIXdpeM+K2RiGLFpntj1tIWuI+p1KxYZisNLFNFV4RDXMkynNMDmZbo0g6XWGpEZlfUNwt8FPKSY2hzi1vsTuAopS2kvwaXStM9SfxBxeeH4TFqyflWs805axzh2JAVH8awR7Q+qxviF7rWyRkenwCSuNh+JxUfNb/AAenqWPGomBcRp0PRdOi4sdSU7aebhvBZo2nM0VFJd33uCVCxKPsr7leK65+xixKtwKSZhw92LPaf8R9W9pcT3FlhjfECZGVc0ZGjRbp73XSqcekqpOa/D8Fhu0tDY6WwZ5sOq5ed4A/MiIvq4MF1dbD12AdGJAY6uXPe4drdaY43xvzFjiN8zuqcMwgs9s0cp6AxbLZDi0kNQ2X4pg1ByFmZo+hWc3Lsv59DbFBLdsc+G1eINZJHDFO4tvdjwCB2I2VEMVW2LlNpomhpuXZWlx+624liNbW0zgJ6MQuNyWQsjd9xquJBAfVIJKd1gfS92p9rKcak470a5NMZXFOy6pqCxzRI0FwN8vLCjHlmldJ8AXttswGw86KuzmxiaajDmE73Nv6q+jpZKh3pgnYw6+h9tPqtNkjnVykbMOhoGO5mIUczYXAhrmhxu7toVoZUUzqaWDC8HqBO8gOLiXhw7WI0XFnp42PLY/iAQdQ5wU452wvHLr6uK59RHT91DxqW9v7mqyOO1fg31dBinLscB5IIJLjHY+/hcuShqhGXupi0AXuSBotjqmikkJrcRr5tLXt/XXZc+d9MXfkyEgbXBVw1Lb/AE/3M8ig97+6HTMkGZ0cD3WHqIbcJsnZch8JJHY2VLZJSwtie4NO4aTb6pilmLDJls3uStGl3MFJpeVGsV8TI8rqKO99xuioxUTMLTR02+h5diPqFnjpJHtLjNE23QndUlhadS1JQhZUsmRL3F8dRThhvSBx75iLKsyWs5tM1o/zXN1YyRobb4nKOwYd1S9zXOsX3HdNLcht1/8ADS1zjFrDE07gg2QJHSNDTOxoHQgLNDFFK/K6pEfkglD6N2a0Mgk1sCOqNMe49U6tI0SRQvAyyRjyVWaWJoJ+JZt0B1SbhtWWlwZ9CbFSkwqvjbd8Vh3uChNLbUDUnu4FZgjIbaRrr72OysGHzvH5MReO4cCqjSzxi7m6HsreRUxxXzFrL7Xt+ybfowjFPmLM7qaZri3lnMDYgKstfYgtV7w+MXzuBO1ioOMh3D/qFSbMpRXYps5LMR0V5Y4/MQPdJ0bWszcxnsN1SZm4MqLjroFJpb1YizejvullNiQQgSsYyWJyqxvLO7dlRY91IZh1Q0OMjReMDRoV0bpGx5o42adbLJGXX3+61ww80WdNG0HqQVnJJHTjdkObU57g2d4VoZWx+oMPr7DcJGjYz1Gsh9gTf+iQjke1xbWXydC46+yW3YtKS5ISMqCbvhePoqC14d8jgpkSG45x83cVAB9/8UfdWjCTsYc5vzBwUuY465XO+iYjz/NMB2urII7Od+exlti4HVJtDipMba6URcsg5L3tYKh1RI4kXIBVr8wkPrY4fsqC83uWoil2Q5Tlw2Ns8sfySOb9VP4qRw9UhPa4VL5A/ZoCQf4uq0p9jPW13LhVTsvllcL9kfFSkeuUn3VfNaW2MQv3uUgA46h1ztZGlegKcuzGJTrqpCUgaEXHVDKYvvrlt3UOX7/ZLyh51uXGuqSAecQfCUuIVczryzvce5KrbA9+jWOJ9ij4d97Ws7sdEJQ9BueV92XNxCqDMgqH5eovooGpe75nA/RRFLMb2aD7EKL4JGC5FvqioBryVvZayrlbezyL9lF0z3HV5VIuOistpq26elISnJrk1wYjVwD8qtmZew9LyES4hUSgieoll7Zn3ssTtDq2ygbeUljjzRTzzqrNbJC+93/cqRDTs77lYtEx9UaCVl2po1vL2jK9zbKJa52oe2yz/RSaXA9UaRqdlwY0g3N0rMAPovrvdQLt/UUF5simO0NrmB2u3ZBdESbAjsqzmKhrdPSZ6i70G/ry/TdRIt+tpURr0CmGj+VHA1uOOw/U36hXQSRxSEuijmG1nA2VGUZrAJ2DTuRZJ7lJtGgsheD+WGjpbooxww3Ie9g7Xuqua6+rj9lHO218xv7JKL9S3KL7GmNkDMxcxkhvpckKcIpiTnpgRfo8grG2YtN2kXHcKYnlINnN+yHFjjkguxvdHRhvphNr/wAxNllmFO0+gO8m6q5kgA9f2ULOcL5h9SlGDXLHPLFrZE3cs/KT7JgMy6McXdFUxz2u0IurbTNGcvb91VGSaZFsUj75InmwubDZWwctoPNY8uCo5j7k8wg+Eszju+6GrBNJ2ahJHb5XA9wVNpDvlB+p3WEvP8yTZCHXDrEJaC1mo7DKupZGIjm5QNxcaX91mzvc8nJYnTULIaqctDTIS0G4BOikKmY7kG2mqlY6NH1Cexa+ORhBa7MTvlUZRUAetrgDsLKtsrxrcLV8W+3riadE90SnGXeikRVBbdoeQN/SdFufFiz4hI2FwjYwXMYtp5sh9ZG6ACOOeM/qcH6fZUtr6wPLYaucBw1BfoQo8z7I1qEf8n8i+noa6ocXCGR9/wBOYi9+uqzVmF1lE7/mG8q509YP9FccRnbGMk8pePmL7ELPLXTy35jyfBCUVkvtQT8HTy7J0+HTztvHI2/QF4H9Sp09LMJW8ypdA0mxeDe32WVkr2g2LrHwrIqqqY5ssTnDKdLtBCpqbIjLGl3PVtocUpqFzcK4mhqGA6wR1ABsf8pK5J4frcksmJCphazUuZG14t3+YKj+P4oYwBFBlB+YQN/2WRtTC7SppnONtMj7arOEckea/n0HkyYnwaYIMIa1zpMUrGyW9LGUw38nMsTnvl9LppHNB0vqnOaSxELJ9hYvt9dlQ0C51cFsl7zn1e4biWXs+/uE46kt0MbX67lAij1zSEqxkERIs5wKbce446uwn1N7/lNYD2JVAs5wuQL+VrNO1msjs48KT2Q6Gxa07HdSpJcFOEpcmb4Z50a6M+xTdDUQ2z3bcdD0V16Rv63X8tQamAg5W38o1S9BKEV33M+ac6cx5HZSBlAs+R48ElS57Nw2w8FRMt9Q0/VPf0C67kTG3cyfcqtzbA6qwy2AGRv1UHyZiTkA9lSsh0RFidS6yvjkLB6ZXg+yoDralPmC+gTasSlRaZ5Tu/N7hXR1Dngh5j17sCylwfsz7KFh/KVOlMam0a54YmjSRpO+gVccRf8AI1pPkqsQm13NdZWBlm/KR5KOFyGzfAzTzRtJLAPsVWC8A2iB/wDaptYwuIebexUnMbHf8xwPuhP1Fp9CcGIS04LBTw6/zR3KjU4hLPa8bGFu2RoCI2QyNvJWFhGwLCU3MPLP54dY6DLuO6VRu6NPPXOxmNQ9xBkN7KU1VJO1rXm4aLNHYJENOtwSVAkt/QNP3VpIxuREWvrqp/l62BHZQLr9APZK5VEk22OrnWQ9oB0cHA9lFrgDq0O8J5i82ZHbwEqDYi4AEgaoG5QQRuCPdIEjZUT3GQpNA7Jh99CAeylynnVrTbwpspL0JRgG/wCWD7usokuBzNGXtZyI2XNnggK/4amykmWQHpZuim0uS0m1sVMeXuAc0vPXXdbDQmaEywRiFotcSyAZvZUw0rJJLRc59tTlbqt4hijjcyoZXXscjfSQolL0NYQtbnMyzQuIsy4HQgq2Eglokjdr/JukI4XH1vlj06R3/uoxRw+oPqnxuG1mE3/dVyTppkX2c+xe5ovpcJWA/wCud9rFPK071IuNrhWCFkls1bHtrdp0RdBRBzKdwBFS4OPzZ26LUaGASRilxWFxIuS8FuU3WGSFofZsrXjuAtEVAXRl7ZYTl3F9UPbuEd3WkdpDI5j6mF1r+ou0NkKoxNDSSGF38oJuhKkO36HuqwwUVCyj4UxDD8ZrDdsxbg4aWNt83Mfe/ZeCrYZ6eofHVMyTA3c3TS/tovSM4i4dppC2l4ZLqdwGZk9c92YjrYWF1rxrjqlfQU9LwzgtLhGX/GmEbXySdAMxG3vqs8euL2j+P9F5NEo7yPFljxa7XC+1xa6GgnqFoxHE6/FqjnV9VJUSAWDnnYLJY910q63OR12JEanW6lFK+GVkkb3MexwLXNNiCOqgB3K0UEFNPUcusrBSRZSeaYy/W2gsNddkOq3CKd7HfmxCqrqV2L/8RSCtgk/wZ5ncxwsPUywt0t9FzKzGMRqcUGJy4lNJXaETtJa5pAtuLdOy5jWszWe85b7gLqRwYJHiETJK+rloyWGSRkAa4C/qABJ2GxWShCPb7fY6PElPvXzMUrqmrlkqJ5nyyHVz5HEuP1O6IaCtmvyKWd9hclsZOndX4i7Dm1tUzDZKh9IJP+XfNYOLP8wHVbcOkoJaKvdiGLVUEzIgaWFjXOEzr7E9B7qnKldGahb3Zy6igrqdgfUU80bTs5zSAoimlyNeQAxwJBzDonJM02AkkcLah5vqhlTy5WPZlBb/AJb/AHBVW6FSvkrDCOl1YxzoX3DLW7hIzNfIXOc7U3OVWvqLuLI5ZDCRs5HbcjvsVzzumeXvja2/8rbXRTTQxS55qZs7dixzi39wrXyVHwYaXh0GcuawuBs61r23CzB5FzYHwig4JyyRPkcYozEw/oDr2+q2uhwg4Yx8dRXNrxfPG6JpjdqLWN7jre4WKSd0jWBsUbMot6BqfdREsobYHRJpgmTgpZJ5mxtLWucbXecoH1KctFJFI5kr4wWmwOa4d5B6qtkkkcge19nA3BW+CGvxWEg1cTmU7S5rJpwzKCdcoPc9kNtBR08N4Rjq6B9ZNxDhdIxswitK5/quL3FhrZZqnh4UwitWl7pL5S2Ihp1sCDfY+wVGH4UyqfKypxOjpWxNLjzZT6j2bYHVTrsKpqaQMgxakqnubmyxOdZo7FxAF1lqlq9r7GlRrgwS0ckQtJo4nYnVasMweSuzt+LpIMoJ/PlDb27Ip3QSiMSzU8XL1Hovn/1Faqviaukc5jG0MLbBtqeljaCB5squb2QJRW7K6J+QxQ4ZTSVNXKDG5skYeC4n9AGt1krzUiplNTCIZWuyvYI8tiNCLdCpQYzX0r81LWSwOzZrxHKQe4ss3xs2aUl/MdKDndJ6ibnU3PXyhRd2NzVUVtfKCS0H7ILpQbkOB21CQle3Z1knSPfq57j7laUZ2SHMGtiroH1bSW07pgSNQwlZsztsxVkdRNEbxyub5BQ0VCVMuBqGgtcH6m506qwxRFmdzpS62oDdFnFXPr+c/XfXdL4iQ3vI7XfVTpZrrjW5Y1oeQGM+6ubG8OIjhYTbuseYdXH6KN9dyjSyFJXZ0o4XtbmdEw6/zdVMVMrASyOMDbuuZmZ/mKkJWgG11DhfJosi7HToqavxGYw0pzPtcC4H7k2XSw7gzifGIqh1DSvnZTPySDnN9Lt7AX1+i8uXX3Jt7q+KqdTAfCz1ETj8xY8i5+ielrgnWnyexwrgXF3ytbVYbW31vHG4Ncbe4Wqu4Vnw6QyS4ZIYdbH4kOeB2Ita68i7EoH0rCJ8T+MuS9zp/Qfbr+6mDP8Awdz6ige9sr7srXSPJFtC0a2t9FhPHkfMv59TfHliuEdmrwKmmja+npMSa4/PnDA0HwbrNR8MRTxGeSrhpow4AiWZua217brnwz11ZCAZ4eXGA1oklDLD26qLOU1zoqmSlzE/42dxy/ZCjkSqzXVilvpL5ocJoJ3wPqZKstcRzIm2YR4vqVI12DGF0XJeOrXiME38km9lljrKGAOzQCd2wcSf7q04nhMrI21GFXy/M6OTKXfsm4t8pjjNJbNIupK7BWOe6rpzI4j06WaPoqqjEKAyZaZjGstuYrKZqeGHRPHwdc19jk9bTYrlB9M2Q5YnFh2B3TjjTd0xTzSSq4nSb/DKhjhPWmF36csRsffVRbDh4eG/xSXKP1CM6fS6zRUj5o3SCB2RuhOmib6ejbDnEzQ4/oLtUUltb+xGqT30r7nTfTYecz4MbYRf0tljcHH36LNPSNe1z/i6J3X0v3+llzg2n1Abn832VkMLr+ilzm+hzf2TUa7/AIKWXVtp/JMcwROENLDJr8wFyh0tQ8csUkEbx2ZYolfLA50Yi5brahpKyufK43IddXFWZzlTo0NkrmXZlJvoW5VTL8T8s0Zb2BFlHmVMYEhL2g7G+6H1lVI7PJK5x7k7JqL9xm5qqdjY97QRlFvIVZLnE3arm4jWAZRK4tve1lY3EakgZmRuy7Fzbo8y7BcWuTOW2F8gUQB1A+qtdV1BN7tFtflCsZiVXyjES0sve3LH+yfmElBvn7FrOQMpD6djsu9ifv5WUyPa85Jr2OhbotXxbeWWyU8bjfctA/dD5aeZoHw8Mdje7LglQtuUatJrZmdzauY/O53u9QHxLLtEjh1+ZaXRUjhfRv8A70o4KIkg1AZpu65H7J6l6fYlwlfP3Kc1S3TnG3gqXMqSRmqQ23UquobFG/LFMJGjZwBCr9NtXKqszcnF1f3NpmkiLXNrGSE66M6+UjW1bnuLpw7MdbgWVLIYDE5zqxjXDZuU6qvli/pdmS0x/iK1yX/0uqGu5hvJG/uWjRU8tzj8wUnNfGAXM06XKgDoQWD3Ca4JlTe5LkOAzOb6ehSDTrZoKAWka3+6YfA2/M5hNtMpsnuKoomyPLbOGC46lSAZl/Qdf5lQ40xPp5lrdbKTPhA05nSk9hoihqr2Ndi5gawxC/kKrPIxpbcADsQoZInH8sENP8x1Q6CNrR+a2x3t0UJI0tvdEsxNr8v9lqFPT8hrpHxnWxyuN1zpo4WG0chd5siNtMWnmySAjazb3/dNxtbCjk0umjU6KiDbiVxd/L0VMYYDfQpMbRfqkl+gCGNp9fW73RVeom7a4JSOjBvym6/5tkml1wQGfVAbCb5n9NNN1F3IHyOfv1CaE7uy4F4vfleyrMbCCXPH/tUPyNSHP+oTY6G5uXN8jVFBd8g+KNtrSA3CbWRMBJeXHpZJ0tOBZjCT3co3pwNcx7p7iem9qG18YJvcD2VjatzXBwlIt/lBSbJR5XB0b79CCqncq5yNdl6X3RV8oV1wzU6rzuLnPJP+kaq2PECy+dwNxYWFrLFzILaQuv8A61F0kdzljNvJU+Gn2LWWS7m9+IzWAY8gDYrFNK+V+Z5F+4FrqPNaBo390zLG4aR/W6cYKPCJnkclTZC7gd/slY2+ZIu8IbJlPygrQysdnXJJQ1z2jRyubUsy5TA0+bkFIviPysLfrdTb9ClFdmVF7ydbH3Sv1sFYTHmGQnzcKbZGNbbKCix6fVlIP+QKQzWH5VwPCsZOGk3aDfuFL4gFuVvpCLfoCjF9ysPH/wBOxS5jbWLfqpvlBGmp8hVA76AoSE3Wwy9p0ypEgnQWTaQP0pFzb7FMTYADrdIhuu6WYJ5m9ygWxJpYOibnH9JQ0wEepzg720UHFt9CkVbSJGWQ7m6YMj3WAJPgXKrJKbXubsSCnROom6KUmxB+oS5EtrBhP0SMjzrnJ83UhUztJtI7XyjcpOHcrMcl7FpH0TbG8D5T9lMyvkdd5uVac4ZqT7XStgoLsVhkhBsw+6OW4N+Q6pcx4GUudYagXTDyBo5w6o3GqAxkbsPlWtY53pEW43zKsyF17ucSe4TBa1t+Y6/QZUtyo0huY1lw6P6XVZcASOUPCDIb6uJ+iiXEXsU0mS2uxF3+kJadk7kndFiNlRmwaQP03TLhvayV3oBudQEAhtMeYXuB1srnCny/lyS5r7EdFX6dSWhDC0OuWZvF7JFRdbE42wG4kmkbbazb/wB1EshJFpneSWph7AbiL3uUy6N2ojLT+yW5WzJsiiynLUAHyN1Hl3eW89lu91F7i8/4Qb00ClFA6Vwaxrsx0GiXHJXOyRKxbcc0EDsofNcBxA/qtpwetyEtjaQPm1tZYnQTRvyubZ17WBupjKL4Y5QlHlEwHtaGcx9jrlBTaMjrzxyZfsUPpqpkgY6GQPOwI3U52VlxHURzOcAMrXEkgdLJkEGzhgNomOuLesXsqXPcTrp9Egbbg37JgOJs7M0eQdFSRFsV77/0SzHXVJ2mmYqOa3VOg1MkSe5TDrd0MBd+tov3QYyP1N+hQLcg43TvboFc1paCHFhUHAA7D6IsKfJXm00ClmcpADqxIi3cIFuK4O90Aja5UTdRsmkFlpI6FP0nW9iqgncIodl7S0MuJdb2sFJsTnOsxwOndZtD0RcXSoakjTnlbcG5VkdZy5WufAyUN3Y/Y+6xh++pUg9pOpKWlD1sunq2ym4pYY9T8jSP7qgOAv6LqwNgIP5jw7pcaKtwaCQH3TSQm2K4vtZO7e5SAjy/Ob9km27hMVskSB8pSJJ63StYdEaWQLcLJG5SzJjXRMkYa7oCfYKY5sbicrmkdwk1z22cx5FtiE3zzSuLpZXPcerjdIpUKR8j3F0l7nuoX6KT3lw9Rue5KTMub1E28JrgTFfyrGSuFutkPZHm/KkLh0zCxUqeCaaRscNszjYAkC/3SdUOKaYGa7vl07KzPDI0gl7D0A1BUXOmZdksYu30nRVNfluTHdTReprkuZGHvIie5o8my6EWEPfDUSSVhYYWZhZpeDrtcbe645dc3yq9lYWH0MDQRYtBNj7qZRm+GVCcP8kSPM6zlyiDLrd2/hBqQTcNsoGa97aJ0xNr1NEbnuZkJjFupZqoZnWIAYfoqXZwAQ4Wd2Kg1zgnpJ1epY5xH6fsFa3mMaCx4N9xY6KsVDw0jK0g9woCVwPuimGpIuDpL5gB7oUGTyZQwXc0H5boSaK1L1PYN4twKh5f8L4SpmSxuH5lTLzTp4I3UJeL8Gqjzq3hKgfMLBoicY2lvm258rxpIJJLtVtnwuop6OOrlMIikALcs7HO17tBuPqFn4GNc/ll+Pka2/BRVVEctTLLT07aeN7iWxNcSGDtc6qoFK10LoqlRzt2dHDI8JkirDilTUQyNhJpmwxhwfJ0DuwRQnCTS8quiqPiXTNImjeA1seuYWI32K5xRlNlGm+5UZqPY9DPg+CU0kzH8RRyuGUxGCnc9pBve5NrEafdcIHK67bad1W1rSfUdO4XcwnBMNrYGzVvEFJQgkgxvie54t4Atr7qfYXmbf8APcXXiezGjkPmdK67w0kdgAiNj5nBrGi/vZasSp8Mp66aKgr5aunafy5zBkz/AEJuFka9oNw51vZWnatGdNOmSjpXyZjmjblF7E6n2Q+AM0bI2Q3/AEgqUjhcciSRxOhJFkpYJoXASNc3MAWkgi47othSK3wuj+duW+qvphSsc11U18rLG7GPDTfprY9VmcLblAbcj1BOrFwWllyQ1rR7uRNUukyWjhYGNyjIy1/J7lUEWJub27KQLet0ULkGvc03B/ZbIcSqY358kMnpy2kha4W+yyumbf0x2HkpCV1rA5R4RVgnRYSZWNbHTasBzOaCSfJU4WSStyxUwe6+9v8AwKls8zCTHK9txY5Ta47KAcdfURfylQWdb/hvGnMqJBhkxZTsD5XMFwxp6m3RZX0DoHNFayWFrm5wQzNcHbqo01Q6FkjW1lRE2QZXtjJs5vUHXUeFuY7AwwMkqcSdqLkNba3WwupuS5NEos5Qid/KfC3Ydg01bOInT01KC3NnqZMjfa/dd3CMY4ewmqZU0zMSlmaBb0xCxv8A5g7osWJY7DUulFNHPEJXlz+Zkd1uLWaLLN5MjdJDUI92cyTDnsc8QudUiNueR0LCQ1vcm2g8rOQ0j0Nd5WqbEJXmTJVTkTNyyAutnG9jbce6zMlsLB2VaJyrcTS7EeW7MGujcD2smWNI0sPCiTndd0mvclTAhFruzJglZHl62BaEzCNg9pJ7K1gpiCeYWfS6geTf0udvvlStlOFDip+ZcG9wL6a38K2EUzWPbJE9zrekg7HyraahjleGtqDGD+otJCrrKKeil5b5GEH5XsOjgo1JurNFBxWqhGKxDhGB4QGP/kbbtos7g69nO091qFHByRI6tYCRqwDUJvbliS1PYqk3+RqpLmB9yB7BXtNLG1wkdK936ctgFY+uaadkIpYSGEnOW+o37pqyWkZzLABlZCSe7iqxMQTaMAdrK+SVsli2JrLbBrdFtwjG6rCZWSUxhDmvzgyQtfY2t1G3hNulshVvyZaXE6ilc59OI2ktykmIOFvqCt8HEUz6lrq2Rwi0DxTwxtJA00FrLvfxrnwPqZ6nAZJJBZ7HwHPqdSBltdZnwYTU82aoqcDzN0a1rpmOfbr6W2/osNSl7UDpWNpXGZkqsdwJ8UrYsJqZpDpHLUVNsot1a1oG64Ek0bnOcIWtvs1pNh916CbD6N8sIw2nhqY5Mv5jmvY0O6gEnULrTcP4RhddDDiuJUQsSZm07g8xm2gISWSEFsmU8eSXLR4sTU5jDRTHODq7Ne/0Vxc0AOkoAGAb6tXqMUxbhd1MymoqKSPIdZI3G8nk32Xn6msojG1rKC7r35r5yS4diNlUJuX+LQSxxivaQ6aswsUskUmHu5zjcSh1yPAGyKeqw7lSippps/6DG4Cx7n/ZaKKoY6oa2Ohw6JztA6UkhW4piHr+GqqegaI+tLEBc+T1Uvmqf1NI+zba+hh+MwoRDNT1MsljmzS2Cyc2jsLUrr9S551Ww1mFOc1/wzmvGjhoWuHt0KZr8OMgLYcrW7EsvfxuqVrs/qQ0pcyRkdVQw2EMETvJBNvuofGvyuAYATsRfRajiUL8w5YAO5DAf2UJJaXMDCZHstd35QbY9vZUveiJf/zIz/ESzy56iVxJ0LnalT+Jax/zEjuAlLUR5wWU0Qt0uSFHkSTu05bdL2uGhVS77GSk1w7ZecUYPlgDraDPt9lD+IAhwNLFZ2+6rfGyKJoE0Ty4XIaDdvg6KTWsLRlkbfqCLWS0wXYpzyS5Y4J2sdnMTrDo0KL6p0ri6RhJ8CyujjrJWksljttYyAGyUdNVXLRk2vmvcI8vcfndJfggyrEZI+Gjdf8AnBurP4mHXD42NH+VqgKeRziHzxN8uOi202GUksMklRiNK1zBfLc3d7JS0JWyoRy35Sinr6Jr7z0bJGHcZiCqZ6iikc7lU3KaTceokhXfBU8kLpI5GAA7E6lQmpYOWHRTwAgatNwT+yS0XtY5eLpp0Zc0RdqCR2Tc2N7bQxSZr6m+ikGStsWOi2vpuqjzS43JWqOduluPk2uHaEdCoctvV1lZFTTS3bHG95AvZo6LS3DKpkHPnop+TtntYX90akuWCg3wjEGs6nZaYpaMANlMgFtSxo/uqeQ8tzNjcG3tm6KLoQ02c7VGz7iVx3SJPdE4+kut5VjBThpLyXE+bWQIaMRAmpfn6tEf91UWQ39MjvqEbMpWt3RZHHE9x/Ma0D+a6JIodMrmm/YqsMjDSRKL9rKOXS4KK94m1XBPljZrS4nayi9hZqW2v0KLSt2BB8KbRM8ZSAfdMnZg2plEeQEBvX0i6hnk6H9kg1+uiGh5Og1PlFINUuAErg4uIa6+9wlnbYgxgk9ey2sFXRsbKYYHNmBDS8Nf+3RUxulDsoDLnvZKynF8P8FTSCLCEX7q1vKiP59O426B1rq6GaOGUvqIedb9IdYfska6LKA2jjDhe7nEm6Vt9i4xjFW3uJ09Dlu2CUHtmuFF8tA5n5cUwfbW7ha6zg3dfID4TaxznEhn2T0pEvJJ9l9BkwlvpaQ7uShhjAN2XJV7WOc3K1rR72Wqmoa2WI8t1O1rdSXPaCpckio43J7GHkHctDf9RsrTAYmtcWsdcX0NwrKmGZv+O5jjf9KhGWhvLIa3W+a2qWptFrGk6ZQHtZcckH36Kcc1OAebTk6/pdZSeIbX5wBvsW3CGx0bn5X1dgd3iM2H0VWq/wDpnTTpUU/kE3IeB0sVFxjv6c31V0zaNkmWKYyNt82UjX2V9PDh8jHGSZzX/pBNtUakle4lBydKjIwQOcMxcO6k6OMPsHBw8FXvoov0VUJJHfZR/h04jdI3K+Nou5zXDRLUvUbxyXYWWJp9THEHsFnLPUcrT40V8Re3UOeAP5VCR8lvncdU1YSSoi1jw7/DJ+iOW4Ou6Mi/RQfJK7d7re6lHDPKHFgc8De3RV8SFTdJFjqeX02YfVsO6uGE4jkEnwsmQmwJHXss0MVS9xETHOyi5sdgrRUV0OmaQDtmJCl6uE0aR0PeSZTLBLE8tljc1w3BCi0WN8lwr31dTIbvJd5KXPnLbEel3cbppyrcioXsVPlLhYRMb7BQbK8HYfZXZ5IpNA3N9Cpmqne2wYzyQ0J37hP3soFTIHXGn0SMz3OzEC/sh2Yk6KOttU0kQ2+BZ3ePspNk0sWj3UQmmTbHdtkXaQEw+w2H2Ub3N7IGh5gOiZIIuUrXOg0TDD/KfskNEmCMkXJA7qx0bMxETy5vciyrbHI8kNa423sEmCQXAJCT+JcWlyi9oy3Jy/dQJaepUTG4i5c0/VREbjcAX9ikkU5dki7kuazOC0g90mwvLC67RbuVSLgWsUX73TpiuJcyKR98rb23sm+GQNucoHuqdL6OcL9kAaG77eEqYWqEQeoTa4DcJttYHPfuLbKXKDm5mu17J36kJPsJvJLhnDgOtt1JrQDdpNuxRHFf9JKsFHUvIEUZcDtl1SbXqaKLq6Jch0zSWXs0XPhVtppHEhttr6qElLUxOtIx7UMZOSchdmt0KS9zC1e6JS08sQBflsexVNibgNJ9lFzXX9Sk1pHW31VozbTew+XIBqx4HturGNqB/htdproEBsr9Obp5cr4Ketcxzoo5HtAuS3opbLjH0srkqqyV35kryQLbdExJVZtOZmH7KBcGuBkJv3Uy6ncy/Oe14GyW3oWr7sH1FZk1meB4KjDUTRva9paXA39QBQ1sDh65T9E5IqfI0wvlL/1BwFh7ISXoS9TfN/M1M+NqpHSNfAHWv63Nb9rrTBiWOUQcaWTl5Rmc+ItOg8rkmLQWd91aKFgp3SmtiaQAeXrc+FOmPf8AAb9joTcRVdRBy309OZD88vKGZxvvdc6orKmokzvcc4Fr2sqGtyElr7/RaOdK5nKbTMc+9w4MOZUoqPCJbcuTO/mvcS+7nHqo5SDZyt50o9MjSCNLEWspcyWUBoF/ACq2TSZUwM1zPt9FYIYyLtmjHglRDeU+0gcO4LVaJ4Gk2ja9v+YJNvsVGK7lTonDt9Ck2KQ6hpPlRfJG4mzLfVRL9AACD7ppMl0Wh0o0IGnSyi5zju26hd25v9VPNLbKDoeiKFdlbjfola/QqYDgd9QmXkDVOxUV5SOhTynqbe6nnadz+yiXNJ/7J7ipBbrcJAkHRAGp1upGNx2t7ICmNsZcfmaNL6qOo6Jct/ZBje3cFAEmNJOyRY031AUWlw0vZPc6lAdhFtuoPso6K4FrTqA5DnR2/wAL90WFWVDVMDQ3srGzNaLcpp91W5wdsAPZG4thWB2RY9kwPolrrYpiG1tym4AfLf6qG3VMa9UABTDL7JKTXBu7boGQIQCRtdSDm66Jh0f6gfoUAHNfaxcfukXkixU3GAt9GcO8qolJIb95MG500Uzt63NPsotLQCCf2SDm9RcIAse6HKC2+brcaLXS1Tc+d8NGbNtkkYbH7dVhLo82jTb3QMhuctu2qTVoqMqZ0n1MNVGIpoaeLKSWviaQdeh8LL8NDJIWslyi2l1mOXylp0JSUa4ZUsifKNLqMtYH81rm9QAbhUOiy7G4SbI5oIa9wB6XQCSD6z9U0mu5D0vhFzG1EUILXgMJ2BG/shWQROeSJKlsQAvmc0n6bIUNruXpfY9WPxFxObPTRYPhDIJgY/hqeiawG+lhbW68niLZY6ySKoozRzMOV8JaWlp7EHVZg4sNxmaQdDtYqUkzpMzpLvkebmRxJcU444xdpEubaoigA26JNuTYAk9AAt0mD4jFhEeLy0z20EkxgZMSNXgXIte+3W1ley5M0Ytb916LCuEsRqJGPxSmr8PoXsDhVGhklGvy2AHVecuRsV3abjHiWmaGwY3Wta0ABplJAA2FioyLJXkNMehO5lUGH1pfXx4U2Spp4WvMk7Y8oMbTqSDqOhturaWhw92IUcP8ViDZIwZ5HwEthdc+nf1aW1Vza7imCgjo4qio+Hr3OyxROa8yl4sRYXOt9lirOGsdw+F01bhdTTxsALnSMy2vss9+8kjouP8AjFs7Gfh2nxhzaysnqaelyiCSmpI2iQjX1A7i/fdGL8Ww1lZ/ymG0jqVuXJHNAwXNtbhoAIvdeXjpZ5YppWBpZE0OeS8CwJt131PRRMNow8yN1/SNwmsEW7btol9TJKoqkzoVtbnnfM2Clh5n/Tp9Gs9h0WMzl7miZz3MGm9yB2CzgA6EqRLQPTv3WiikYObZbHIGlw5IeCNMw2UDE8i4YQFXneBo4ozu6kqqZFjETzcNa4nsAhsZJIsb9k4ppYXtkie5rwbghBlkc4uc45juUbgqEWDqCnlGlk84sLi5VwmpuRZ0MgnzfMHDLl9rbotjSIyCBo0ZIdN7jdVNc2x9N12MN4mrsLY2Ohc1sYN8sjA6x+y1Px6PEQ2KqfDh0LhllNHS3Lxe9yCd/ayycprtsXUX3Oe2up3AGLCaX0jXM5xv51Kso6eqpG/xD4OilgBByzOa5u97Zb3+iqZT4fU1ULHYsYo3g55ZacgMtto0klVRUdE+tdDLicccAdb4jlOcCL7gbp7fyxfE7GI1dbi2HyVJjwelpxJm5FPHHE4HbRvzWXHpoxUGRjqingDWF2aQ2vboLA6lVzCjhnLYnOqo2u/xLFmYe3RUyOY6Rzo4y1n6Wk3t9U4xpD1ESG9DfyrqbkxytdUMMkYIJa02JCUZdYhsWbv6b2Se6V7zmvfbZVzsLgvnnhlc/lUrYmEnKBuB7rOcttGa+6up8Oral5ZT08srsuYho6d/ZQNLUNvmjLbb3UrStrL80uxUdf0gK1oIGgaL91AsP6jspAxW9ZefYJiSLHte1p/5lns0lVNY06ukKi8x3OQOA8lRzDoHISByNDGRk3D3fZXvpKUxgtqJDKd28vT73WUc61mRvGl9lEvladS5pSp+pSaS3RripI3TsjqJTDE5wDpMty0d7KzEKGKmrZoKKvbV07XWZMG5c472OyxCZ7T/ADE/zBSdUVFgNG+wCVSH5KNEcETnCOSqEQP63XIH2UKigEUQlbW0soN7Bjjm37ELI5zgTmNyqy891UYv1IlJcF8cDX5rzxMsP1X19tFfTUUcz3NMzyGtJHLYXXP/AJ1WHNom17h8pI9k2nRKce52WUFI2jLnV87ZQ7RnKOW3v3WGekLXEsOYd+6qY+ob6gZBbUaEha4sXrdnVDrdNBos9M07Ts6FLFJU1Rk+FmDQ90Tw07OtoVbT09TcSRNY65sLkH9ldLUCdl56iaQjZuY6quWpi5Qjhpyw3+Ym5KdyfYWiEXdkZKWSN5bMWtdfUAodCyIXcwvO+6I6t4iMbw5zb3HupzyzxZWzQObcXAe0i4S8w/I1ZnJzPJZEGjoALrY6ll5TJ30uVjrWsCA5VQYlPA4uiLW3O1lo/iVdI2xlZkvfKAAlLX2Hj8OnbZB9DOWtfFSZWHq12a600RqIKdwkpZZaV51AJaLjyFnkrMRdS5s4bDf9OUf91k+MqeUYxPKGE3yhxt9ktMpKnRWvHCVqzvUNRHTh7ouG46oO0zvL32/subKQHPMtC9ubZty0NWFlXVRtLWTytHYOIQ11ROb3keQN7k2TWKt/9sPHTVL8IvljlbYCmDcwuNLqMhmc1okOjRYDsnHTzZHyc1rMlr3ks437Dqr6OnhmJ5s0rRuXJtpKxKLk9u5mZO5jS1jIwf5suqBWztOry7xeytljo4iWtfK919wRayrM9O1hDInF99yRayap9iXqi61UGeSc3jgLiNToSjK8B0b4GhxO50IRFNBa3MniJ3LTooOjgOoqD/7gUcbCe6uxupZI23eWNB1HrCrDfVbmDTqh0IzWbIx47gqssIdZUiHS4NJja5tzUtvtaxVRYWmwlB9iq+W92oBsEg1wGxTS95LlfY1MpJ3tzCRjW9zIAoyNqIxZ8t2ntJcLPZxSs76or1ByVbF8YmeLi5aPK00tDzrvmnbEwbncj6dVnjp6qzS2F9nfKbaFWzU1XA7JLG5jtwFEvRM0hXMk2ElPC1zrVBe39JyWuiKCly5pZZL/AMrGqp4lB9QN+yrDpBpZNJ1yDlFPguc2lv8AltkGv6iDotlM3DpPTUGaH/OwZv2XMuRuCm2VzdgUSi2uRQyJPg0SMp2zuEcsjogdHZbE/RWfD0osTVusd/RqP3WUSE9LoIcR/hn7JaX6lKUeaOkabCQZXDE5HNaBkBhILj57JxVWDxwgGmqHzDqXjKfouSWm2rSEi23RHh3y2Px2vZijp1FXQT7Uro9dS062/os72UbpCYnyCPpmtcLIGOOgBv4VjKaZ2jWO+yFFRWzE8spu3H7Fs3wzRaHmOPUk6IilpxYSRPI6kO1VRiezRwIPlRzEH5VVJolyad0dF0tIQBE14Fv1DZVPjjfo2cNvvdZMziLWNkgHEeFKhXcp5U+UTfC0OI5lwDuAoiNoJ9Zt4CbWSOuGtJsLmw6JEuGhBHuq3IbRYI4sg/Odm7ZVOGGBziJKjJpuQVmueyCTfVFP1BTS3o18ikMmVtWQ0/qcwqmWnDXEMe2QA2zDqqrm6s58pjEZkOS97dEqa7jcoSW6IcrW1x7p8jWzTm9groeWX2lfYeyuqXwtdene8+SACjU7oFji1dmaGklmJDGONt7BBpZBfew38KwTv2DyPJUHNdc/mtta+p3QnKx6YpbEA0tv+YBbykW9c4UhAXMLuZGP8pOqbKYuOjmj6p2iaZWWEW9QN02xOtcPH3V7YGgEmzrd3WQ2G7Sc7BbW10tRSxsI6OZzyGSMabbl1lNkUzBf4ht29ioNa3KdBf31Q8AW0y9wpts0UYpEXW3dIrHupjGy80jnfy2sGqmTKToOigQy3ZVVmTlpb2L2mmzXJeR4CiX09rAPDgVRZt9CkbXT0ic/cWOcD8ugCjcWSaG9XaK8Mpi02ldcbXG6OBK5FYMVtWm6gC0bturWmNrvU/TwFc1kdriUHXY6JXQ1DUZmkD9H3T5oAtlaPNle5p1sW2SFO97M1h73RqQ9DXBGOs5YP5bT2TOISZQ1ga3W5sEQ0kkr2sjDS46AE2ukIp8pa2PrY2AulUB6slDjqphIXtc5ryb5grTT1M7iZJYwSbkveAs8UNRNK2OJjnPOgDRqU5KWpa5zZYnMc3Qh+hCKV7Am2t7YhA+7vUx1jqQ4KGUg6q5lPI1uezbd7hNxLNY3Ot5anqDRsVZHNAIcNVpifIwi8bHAjUO1uqSHSG7nfYJ8tjR80lwdUnuOOzsvqGy6AxMZ2sLKuSjkjtzAAXC41CiZAGlri53k30SZJCAeZzM3SxSVpFScGxCmBNjI0fVIwWJs8fRdAz4OKPJFRVBqrWMr5tL+1lka6NotlHvdCkweOK7lAbKLhp+yRZO31eofVbeZQEM5rZt/XkcNk5xhPJPw81WJf5XgEfdNT9wnj22l9zC0VJaS0vLfdaDSVsTDJJBLl6uVBMYPokfr4XRpqyKlDZIa+sZIdHtHZEm1whQUW/Mznh0YP5jCQpPdTFwLc9uoK1OqqapmLqiaWxO5YCVppo8NmaIM7nOcfS+zW297qXKuUy4Y1JtJoyxxYe8RD40xue6z80ZtGO9xuipZDTkxw1jKgH9ceYAfQgK+soGwwgxMc8BxGctFj2I6qFNRmoIY7lQ9AX3FypUk1dmjxyT01uVmmoXRZpMR/M/kbET+6qbSQm9n5mfzbH7LpxYNy4jLJlLAbOAeAfe3ZWyYfRGWOGBt5HaHNVNa0H7aKVlV0mW+mdXJJHMhgpmF2cB38typRyUoeGmAWvqcyhimG1VDIRNDkYdrSNf+4WFmXUOcR9Foo6ldmDyaHpUTtsw2DEJGthqaWkaSBeZ9h7k9FmmwCoY0vZUUkkeYta6Ooac2tr23XNexo1bLm+igAO6qMZLhmU5xlyjVUUktHUGN0sZe0A5o33H3UXy1Jkzmd5f/ADhxutdPR4eaGSafEQ2cD0QNiJLj5N9AsgsPkcE7slxaKCZCS5ziSTqShrpGnM0uBGxCtyE39YQIu8gVWiUmAqqg/M8u/wBWqclS6YkvZHfu1oCmIhffMrm08WQlwmB/ytuLKbiaKM2YyWW0YVE5T+kq0tjDyC5+XvbVV+kXs8/ZUjNhl01JTyCwPM17I1GzgkA46ghAbBsfmVgcwD5ST5UbPAvZKz+uiXILYb35tmNaAqwbG+ibie6Vj2VIkOZYozXKiBYp3HZFBbHm3S5jhqCVIOt0CRFzsECDNm1ckLd1Nkef9TW+5VsdGX7SM9ydkrSGot8GcN907W7rTJRSR7PY7poVQ5kjSRuhST4KcHHlA8+kAOB+ig3RPK91zZItc35hb3TIYHW6ACbpWPRK5TEOxN9EgEAlGvZADsi3ukhAEgAloldF9EDGMl9bqTWB7rNdb3UFJrblAIm+FzRu0g7EJcmSxOS4Vj4HR2DnMIIvo5LIQLh/2KmytO5MxPyX+HIHdUOO4tZNznAfO77qu511TSBtdiVha+bXtZRt5UxKbWIBHsp86Ej1QN/9pIujcmkyrKe4TaD9kwY9btP3VxNK4NDI5mn9V3A/bRFjSIgl4OeU36C17oVvLpS27Xyg9nDUIUWaKLOrTVNJ/HZn4nURxReq8scPxLXPtbMGuIvfe64c3LbK4RSGRl9HFuW/0SbDK8FzY3OF7XA0uj4d4idI7KGtdlPqF7+26qMUu5EpuXYiHEG7SQpOlc9oa57i0agE6BV/VGXS6qjNNkrhF+yVkBpOyALYJ5aeVk0Ero5WEOa9hILT0IKtrK+uxB5krqyoqHG13TSFx/crO2J7tGtJPYIdHI35o3D3CVLktSlR1cFo8GqYqk4vistE5jLwtZTmQSO7aHRV4tSYfT1hbhtWaimLWljyLE6a3HQ3vosLIJ5G5o4pHN7hpI8qogtJBBBUqL1Xq+RWtaaaNIFM065nC22uhUhG2T0w2/8Adp/VZNUa9Sqoiy4hrXWLA6x1GbdTlja6MTNYxkd8thJc3723WUlNFCtErNvouhhmHivmEb6uCkYQSZpg7I2wvrYHfZc5rnNN2myvFXUcnlc+Tli/oDjbXdJp9hqiD4wMuR+e410tZSdSzMp21Do/yXOyh9xqVVc9FI3DQTINegOye4FkUTHA5gfBXSoMIo6pln4nTwzPYXMa/QZgbBriTYX7rlNLNA6Rw11sLqBEYJs6/wBFLTfcaa7n0DhvCsFwhjK+uxvAJqlrwOROx0wYOpsNCe3RGLYtRVfE8uI4W6glpoBdgbhYyZANXObpfUnVeAOTKMt7qILhcNJFxrYrHwLlqcmWsiXY97V8YxUwNLRSUVRS3zmQ4WyNznHfS/Q7Lyc9RRNkEtK2USFvqDiLZr7jwucGnsm1j3uysYXHsArhhjDhg8rfY0srpoc/JlkZn0dlcRf3VPNJOa37rfUcOYvTUcVXVUL4YJTZj5SG3+hN1lbQS3tdhsLnK6+n0Vpw7MnzPsQfUyPcSXEaWsDoPCiyRzSfU5aZKVsYaBNE8npHdxH7LRVYfTQUsL4aqWaZxPMjMOQNHSxJ1+yTlFFxjN8GAVTm3BZG6+nqbeyiJNb5GrQyWzhaIOcNgWjVOd07JS6WGNpOtsosi/cVpdclLXk3tkaD/lSsc2j2j30TfIHOuGRs8N2UWyND/W3MB2KZDLTXVT2hjpy4N2B6KAncdHa+QtcVdTMgdG+iaSdnX1VBkp3mzobDu06qfkW7/wDRooa2enbLHFKWMmbkkaQDmHbVUzMptc0pzeAqyynLx63Mb33snOykbpFK6TTciyK3sdvTRBgpgRnkflvrlGtlfK3DxPaCWV0QG8rACfoLqdFSUcz4hPUSxsLgJHNjDsovqRrquziGCcMNc1mFcSVE8jtMslCWWPvmSc4p1bJUXXByH02HOp2TR1rGvcbPhc112eb2sVBlVBTExfDU1S2/zkOufrotjsMwtg5U2NiOTNZzHU7iG/UXVUeH4Y4HNjUbLGwHIebpaovm/oylCV7V9jsU3GEVNDy4+G8IAtbM6Mu/qVnlxCuxtzaWnocLgLnZm5I2R/S56KGHOpcPqGzQYvEXN0DjTB/7OFlTicVPWzS1DsUbK7U6sawu9gNFklC9l+Tp/uaav8GLlVc07oTJDmuQfzGho+uys/g9UWwlk9K/m6hoqG3b4I6K6Dh6pngimpqmkcyTYOna1w9wSsVRhs8M7onvhLh1ZICPuFqppuoyRk8bSuUWzc7CazKGCspnNYMwAmFvp5UTR1k096qqpy5gFjNMCLdlibS1Yc0NkNztZ60U2C4jUPMdNBLLKSBlaLqbrmSNEr4gzXNgcIaJX4zhlyNY2OJI+wVTsAeaH4uGpo5GgXLW1Az72tlOt1bBw9jBke11OyIsHrMoHpt37LFJSVks5jkAuDYZRYH2spU74minjS3cGQbQPEbi5pDgbWK2YdDQNkyVbZbuFmmO2nk3UfhK2JuaJ0ocBcnMSFCWnq5WF1RM0PAvlO9kOWpchCCjvpNNZTxUc/Lkil/y3lYbjvoEVDhTOzNonhrx8xluHDyBZcqSnltfMw9rOF1STNCS0uIt5VLHfcl59Lflo6f8Wlg/9NT08VjoRC0n7m6wzVdTO4ukmLj11UHzufq4ku6pNJNjyzvobbrSMEuxjPLKe1lTib6lAXQhhDy7mUhGYekgHROTKQA2JrbafKNU9a4IWFveznhhPTdMsb1Ovhap2mJzbiMG2w/uox1TWXDog7oD2Rqb4Dw0nTZW2NmXRri7vfRXw0zpI3FlLI62mYO0CqdU3JLGgX+qI66qiN4pi3wNvslUnwVF409y50MrYHBkLhrcku/sshjmN7tdbqrRWVLyc7g++9wrJXySbDltHQHRC1R5CShPgytikOwK1w4TiEsRnipZnxA2L2tJA+qrYwuIHNAvoSdgpf8AMMZkZUnKTfK15t9k3J9hRhHvZWRMxpHMI1tlJKrJlv6nO+61w0Mszml80TM2xkfZE1GI3ENqI5AOrXXS1Ibxzq0Z881rXTjdMw5uWT7tuE5KWaIBxAIPUOBSZVVUJ9D3NHhPZ8E7p+aybqiR7S10IIHUDZHMqYWgiItadiWqt1XUFpbzCBubBQdUTvAD5XkDYFx0Qo+4byLm3ZaysmY8uaGZrWuWDRKSsqJXFznkk7kCyhFUSRuzttmGxIur4sRqYw/KWguFico27IcfRCjO9nIqZO4b+r3WxlVGGtz0sLspvexuffVV/G0xjaJKTO4G7jnIuqjU07wQKcs10LXnQfVS1fY0jJR4kja7G5BI98VLSR5tg2P5fZZjiFQ95eZPUeoFlTalLjZ0rW20uAdUNbATpJl06gm6FCC7A8mV/wCRaJnyH/E16l1lFrg55zOb9lARgn0vbf2SETzoAE6ROqXc2XiezIASR2NkmRek5GWHa+qoMBYA50rWk9LqBY7dri7yCp0+80cvVGgNiY8OfFI5p0Ia4i6kyjqZ2tMEJ1cG5nOFtdllHxNw0Pk0OgvsVaIcQnjLuXO9t9TY7ptNdxJqXZhV0dRA8tmEYy75Xg/0VBY5xGZ4vtqVOSgrI78yCVlu7VH4SpH/AE3fVUmq5M5Rd+yyTadl7PlYB3BVjPhYSbxCoJGl3loCpbR1JFxGcvforW4bWloLaaRwOxa26Ta7sIqX+MSg3JPpaB2BTY1vV1vFlL4SqB1gkHu0pPpKtrbuhkA7lqq16kqMuWhWYAbuN0SNht+XnJ0+a31UGwzOdlbG9zjsAFN1NURm0kUjevqFk9vUW7XBWB4KYaSbhT5MzQSYyLb3V3MjbT8s0tpc1+bnOo7W2Sb9Bxi++xnGba5QY3nYkqznHlhoYABr5VYkdfQIVhsDYpXH0glWOhnZo+J31CQkIOjSh0zwflftbUlLcaSSDkTPdlZES69gB3UXU8zAS6Mjobp/nH1XLfN7KwZpDaSoG17uuUW0LSmZxHc+ogfVJzWg2v8AVaWQMdq+Rtle+kpyy8Od1t3HZGtIpYJNbHOsEANWt0bWXblF+6qMQN7kX7JqSIeNoqAb3+ilmARyjY7KJY6+yezJVot5rALAH6oEt7gXsqgwnoptikJsGknwlSKU5WXthjefnc0HYkJ/DPzHLMwW6lyyua9jvULHylmPfdGl+pXiR7o1mCqilDWPBf0LHhRkhq7kyteTfqbqlkz2EFu42NkOqZ3G/Md90kpD1Q95IMlAJyPt7K6Karic6MRm7tC10dz+4WXnzX0kfvfdamYlXWdepkNzckm5v77ptMUJxT5ZUJp2XAJaDuLKt0j9fUpvnMjsz7uPVGeE3/LP3QvgDt8MhzXHd11Jj47HNmv4CRDHfIwj6qbI4w4CSTJfra9kbEKyBkjvoD7q2mbSyvtUSuiF/mDbgJzw00bQWVPNJ3AaRb7qtjaa7eY99uuVuyWzWxatS3othpoXzFpnaGBpdnOl7dPdUZGDqrv+WHyZn36nRdSioYJGsHwMkkjhdp+KY1v1vspc9O7NI4teyOM5sQy2c7zpslaIk+p3jTddh9IGSyMdRNYYza7pgRft5WOSFzZcrmiIbiwuhZExS6dow2be2p+ibo26Fht4K0/mm7GvaATfZVtMhu3Mw+SFeoz0UVuiljOjgfLSou5uzib+669LhzKiFjpq+lguflALn/YLBVUj4ZHAF7mX9LywjMO6UZpui54pxV9jMRIdS4/dLLc2zLUKSryi0byD0DSpyYdWQSiOSB/MNiG2uU9cfUjw8nozPDHKT+Xd30XRiqqh0b2fC0jgdTmjF/oU3UFdDDeWhnaHbFzCLqLMKrXw/EugfBAb2lkjcGEjoDayzclI2WOUFwyiTLJ6DTQxPvfPnIv47K0H4eldEWUUpltZwu58dj+11SKCpe4huQm4A13W2swLE8LlZHOYOa+1mxytcTfbZDlHiyam96Kf4VPJEyWCKWcEevlxu9B6Aro0vCsbKGPEMXrZKSnc8tcxlM9z229wG3+qso8JxuUSiGryFzC9zWucS7LrbQbrh1FRXSRhss1Q6N2uVzzZxUqUpbRkKUYx3kmVzRwMYzkumc7XPmaAN9LfRVjlZf15v2SAmGjg5Gcg6tWxlY/R0vdTaXAaOIt5Sa5nXRJxjdfU3SGmWcsusXO06lKWOJjrB7j7tsqct9ikcwJ1TS94NquCy8Ol8/nQKJdDezWu9yVAuKV9dk6JssD262NkFwGzlD05fl17pBu+iKDUTDrnSyZdbexUC3TRqQY462TpE2SBaTsFYGRuHzWVJaeybWEmxNrpMEyb2tv6dvdIRk/LqfdJ8RabZmkdwUsjraf1QgfvE5rmkghAum5rmjVpHlRBcNLqhF0cs0YcI3ubfeyTppDu66rzOA0ugB3YlKkVqY85SuCfVdSDnN1yj6qJc4nZAh3brqVA26XRfwl9EyRgi2iA5KyLaJiLGvt0B9wmxzM13tzDtsqtUW03SopMscYnH0gt763VnJjNskrT4PRUAaqQIAKVeg7Q3tDXFuYHyFYImPLWQuLnk2sepVOh6KbRG3q5AlVjkj5ZIe1wOyhYW0DvsrXBhsGSnbqLaqZM4jDDOMg/TnSTKrcpAjygkvzHcW0StF/MR4IVvxE/KERdeNpzAEbFXwc19PNIzDxIwaOm5ZIZfzsEW0NRT4MWVpJs77pthc6+VzTbyrqebkyZvh2PI6OFwrH1cRYbwWkzXzA6W7WQ5PshaYtclETeW8GSAyDsSQE335hL4SxpPygEWWifEZJm2dI6/awsFnbVSNdmLiXb3JSWp7tFtRWyZXIWZvRmt5Qrp62WcDmhhsMoOUXAQqV1uQ6vZkZIpIQ1hlYcwzWZIHAe9tiqpY+XKWZ2Pt+puoK9tx1itP8ADNw+kwLBqNjnB5mpqXLLp0zEnReJOyjFPXHUKSolJGxjIy2ZshcLuaAfQb7G/wDZRGTK4EOJ6a6BajTMFDzwXZs1rdFjC0W4pRoYKdz3Xb4Iwemx7iegw2tdI2CoeQ8xkB2gJ0JB7Ln4pSR0mJ1lNEXFkM7425jc2aSBdK1q0hpemzK2V7TdryD3CthramEOEczgHCxB1BCgIxkJudLL0LMCo/8Agd+MkymqFZyQM3pDbdrbpSaXJeOMpPbsefbUzhpa2VwadcodYKFw4+q61VDY46WzYWZiQc+t/beyxjdNENvuSIHS6A0db3S17laKeFskUrnkkttbVMRnyt6lSby9iSp5xESGsYfJFyh1ZO6NsJcMjTcDKNz5QOhO5WWzQS6+91O8JgIDZTJ/qGX/AHUGSHOHEBx8hRfMX39LRr0CkCPgD907NvsVHopBul9VRIg09Gk+wWqjZSGZsdcJYwTq4aW/ZVQTSwPDoZHMcOrTZdnBDJi2O00VdNJLzn+tzrOJ08gqJNpFJFUsfDsdM4RTVr6r9NmtMe/31Cy04ikqGmKnLmtN7BjnZteoXdx2slpMfd8GIacseYgYYWMuGmw0AAv5VmLcZcRYdWyUtFi1RDCwCzW26i51tfdYxlKVJd/V/wDDZxS5Onh+AfFyfE4tTPoKcQlzQcLcxjQdb3zC9um62OruDsKomxT4jX1Msb8pjpKSKFxuN7m9x9V4LEeJcaxR7JMRxGepdGLN5jr2+i52dztXG9wp/Tyk/O9vcPxEl5T11bxlA6eT4bDmSxlpa11U1jnWPXRuhWKfjLE3wSU9Jy6OnlBEkdO3KHg7grzo90r2WkemxR4RDzTNHxs+YubK4a30SdV1DiS6VzierjdUdEDXda6V6EKcvUs5z0w5x/m+6rASuQSLp0gUmy05nm5OvlWxwMc60kgaO6oB1Uma3uk0yo13NUNLSOls+oky/wCRlyfurpYaSJgaxsofa95CNVhJSZ8xvrp1UU3vZspRqqLXwtvo5gHfMpikpuW57qwBwGjRGTdZHaHRLcKqdcmVq6ota2IubmkdluLlo1AVxgY6YiiEs8d7NLm2J+gKyNcWOBFtNdVZ8XLk5fpDSb6NAP3Q0wTXcnUQS082Wemcw75H3CbopqiRzoKNzWu2ZE1xA+91mMjifmP3VzKqoZ8k8jfZ5CdME02RdTVDBd8T2juWlR5EwIvG7XYEK5882UEzSEk9XFeh4HwmPifHo6LEaqqazI71xSAOFttSCi2PTE8yIJs2UMdfsu3T8J4xJTNqHxx08LiMrpZQ269Bj3C1DhuFYZVQzVT5avPzDJIDbKbC2i8VPI5ry29xtrqsnKUtomsIwjvK2ehGHcmmbG3HDLI05mwwghjXD/MSAuZJik1PUGRsk7qhp/xTKbj7LkmV+2Y2VrJCLXa0+4SWKvadmj6jtj2OmzijE42yCJ7WGT532u53uSskuMVz3Zny67/KFlk3Ci57ibk30VrFjXEUYy6jM9nJlxrql5dnmec2+u6j8Q52rrE+yp3Ubq1FGfiT7s0MlYNXBbabEqanId8DHM4f/U1C5W6kEpY0+So5pRex0K7FBUhoZR00OUnWNlifcrOayZ0IhDnCMG+UE2v3sp0kLHv9YuLbXU6hrI4SGRtBDvm1up8q2o0/uTuVmTmyO0Lndt1JlNUvBe2KQtG5DSrWPyPByNcbdVoZilVA17YHCLNuWXCHJr2UEMalvJ7GeGhle8Z7Ri+rpDYD3WiqpIIpTHHJA8j9TJC4feyxSVc8t+ZK5197ndKMXKdS5bFcFskWiNxsGNafopRUVTUyZIIcx65RoFfTzzQG0EhjzAglu5Cr/iFXC95jneC8WcQdwpufYrRj72VyUVTELkC17XDhqoikqCbGN310S50m+Yk+UT1M0zryyOd7lUnIzqHKsnJR1EMhje31DXRwP9FuOEmGmZPPiVBHmGkbZc7x7gA2XKa5wOjnD2KkxoJ1F0NP1HHSt6CVjWuIbOJPOouqxurLBpHpB91WdL27qkZye9lnMFtGgfVaDik/IbEC3K0WHoH9ViSKHBPkFlkuGWOmc5+d2pV8NZGwZZKaOQeRqsgQ0apuKYoza3Oo6pwp7RalmidpfK8OCjLDQu/9M+ZzeucAKingY/5r7qyeCNrrNbb6rKknSbOhSclbSJSYfFJI5tDPzA0A/mAMJPXqqnUMkYJL47/5XgrO5gBNrqs6BUlL1M5Sh/5NcdDI9jnhrnAbkEJNpmG4e8st1WcEjYlJzj1JTqXqJONcF0scTHWZPnH+myRdGNi491QkN1SiS509kaGTQB3qhLh5crzVUhddlNlb2zFYEwN0nBAssom4VcYbZjSxwNw4bqPx9RlLG1EjW9sx1WSwsg7JKCK8aZoNZVAf+pkI7F5KrdPK4eqRx+qqQFWlGbyS9S1s8rdpHD2K0HGMRLXMNZMWkWILtwsmUJhoScY90NZJrhm1uL1ojyGYlvYokxOSVjWSAWA6f1WIMF0FoB6qfDh6Giz5Eqs1RVZjlEjCcw2N1M1pkeHzkya6guOqoooGTPyvva19ChjGtcAWhw8ocY2OOSdUjQ6fmn0s9N9AXXWpj3Oa8MpI7x+o5pRcey00+FUs9M+VzXNcHtADXaagrBPSxMFmg973WNxfB0tTju/59gfzqmUehmeQ2HrAuoE0sL3xT08rJGXF2Sg6/ZRZTRubcg/dGUQOY9gBO9nAEfZWkjJt2SZVRRgcuWoaep0VbsSqiW/nvcGXy59bX33Vmcanlx6m/wAqlC5sUziIonXJ0e24RceaKqb2Towid5JzepNskYvmZf67Lv0GFUlSYBJGfzX2JabW06K9+B0LOYcjjlnyC7uil54LsOPS5GuUea+Ito1o18JGeaxaJHBp3F913Z4Y6J8j6ZuRzRod7Lk/4znPk1cbklVCalvRGTFPHtZnzO/mQ54O5upuibe2q01dDFAWhhfr3K0tGNSZiElhoEc49Fc+FjW3F1FkbXGxRsJqSKuY691ITPv1urDAwA2v90nRNbaxOvlPYlOSGyfK4uc29x1Q+aF9/wAqxt0UHRty31VjAGAODQfcKWktzVSlwV5wBZumijleRoP2W1lQ0tlDqaAkjR2Ugt9rFUPleNQdklL0G8dFIuD6ht3CugqmU8jXtp4nlpP+IMwPuFqFRzgwSxRO0sTbU/ulBSwzczMy2VtxlKWtPkbxOG8WZX1bnzGQRRAno1gAH0UXzSSPzHLfw0BWOp2C9i77oEYY7S+ndXsjPzPZsYjqZMuZjmgj03ba48K6Ch5rCZI6guadcoCrkragloMps0WaOyrFXPG70yH7qPN2N0sae9ssnpqcH8h0rha/rsFnLLagD6qQqZA24I+yUdRI0Egj7BUtRnJQb2Q455IXCwYQO7QVtbi0WQMkw2kcbG7gC06+xWduIS8l8bo4HB2tzGLrOXeq+VvtZKk+UVqlD2WXR1LA+wzNZ2BUjVOkIL3vdbTU9Fvpaemmp5XOpow5paARfr9VB9BTmSRoaQG2tYqFODdUbPHlUbtFTKqiLQx8M7rC+soAv9lX8RFHYwho/wAr/UtUmGU7aJ8wz5m2sL6JPoqaOniIiBc8EkklFxRNZH6Ep5WNo6dsZoZC4XPKaRI0/wCYkf0WaaGuYwPe10kW4ynMP2U6qjhZUctjS1th18KdTRMpoYXRSSgvFz6kRrsEnJ2n2K5cZxVjIYHzytbB/htOmW6oOLYgZOY6pkLs2a511V8ETZxI+Yue4W3cVVTxMlmDXDQutomlBf4mblldeY14fxVi1BM6WOVkhduJow8H6FLEOI6nEG5JGMhi6xQXZHfvlvYFaMSwunp2tMeb5b6kd1Giw2lnY8yMJIbca26qf7SWrSWlmk61HMNTA5jQY/UN3Zjc/uq5HvkOYSOuNrk6L0uF4LQ1JeJIjo8NBB6LRxhwxh+DU+GvozNmqWOdIXvvsemicckW6ROTFOEbbPMNqK+mjIbUyMaRs2TcFVS1VRO5rnkXYLDK0AfsiWFrNiVQdBoStUkc7k/U3R0GIS0U1YyImni1e8vAt02JufoqA2oDQQdD5BVAuQbk/dAHkp0+4JouOYj16fRNpgynmNfe2lrLPc3tcpgXI8ooakStGSbB1kvQdBdLa9kJkNljYoTfNIQkYmknK72uobI3CW49uKJOjyD5r+yr18qbRfqVINtcXKZLRWC62l0AuG6svZRznx9kWFEcx6koDrIJU4mtebOF0CIiRt9WByQcOy1Npoyy9jdV1FOyKQtaXEWG6SaDcrbIARcE/VN8mY3VeUBMhOgvYnmzN+c3HSyQzX+chRGyROiBky065Xgqv1C9iUAmxR0TQmLVGqadgmSIEp9EkBABdMgdEkA6WSGixrGuHzZT5UhTktJEkZ1ta+qpudlZHKWjRrT7hJlRSZe7DqxlN8SYgYb2zNeDr7DVZgHEXDTZWiQuJ9LR7BTjqXtdlysLR0IU6n3NNEW9ihuUj1Ag91EOAOouF04QJY3kta3TZoCqgmFLM2Tkwzb+mZmYfZJT2YPFTSsx3YSSDlHbdWR1FRFC+CGokEUnzsa4hrvcdVv5kc8jQ6lp2jsxpH91dLHDKGxinijAF8zAQTf6qfFXFGiwS3afBxM7wTqUcx1731XQfAyJry25LRpm1WUy3drHHoP5VommY6WUE3UmlvUIzXvdrduygAqI4JksOwIQooQDP//Z" style="display:none" alt=""/>
<img id="img-wood"   src="data:image/jpeg;base64,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"   style="display:none" alt=""/>
<div id="app">

<!-- NAV -->
<nav id="nav">
  <a href="#" class="n-logo">GAN<em>VING</em></a>
  <ul class="n-links">
    <li><a href="#vibe">Story</a></li><li><a href="#menu">Menu</a></li>
    <li><a href="#reviews">Reviews</a></li><li><a href="#contact">Contact</a></li>
  </ul>
  <a href="https://wa.me/919800000000" class="n-cta">Book a Table</a>
  <button class="n-ham" onclick="mobOn()"><span></span><span></span><span></span></button>
</nav>
<div class="mob" id="mob">
  <button class="mob-x" onclick="mobOff()">&#x2715;</button>
  <a href="#vibe" onclick="mobOff()">Story</a><a href="#menu" onclick="mobOff()">Menu</a>
  <a href="#reviews" onclick="mobOff()">Reviews</a><a href="#contact" onclick="mobOff()">Contact</a>
  <a href="https://wa.me/919800000000" style="color:var(--amb)" onclick="mobOff()">Book a Table</a>
</div>

<!-- HERO -->
<section id="hero">
  <!-- Layer 1: Embedded bridge photo — always visible -->
  <div class="hbg-css" id="heroCss"></div>
  <div class="hbg-grade"></div>
  <div class="hbg-bloom"></div>
  <!-- Cinematic letterbox bars — animate out on load -->
  <div class="hero-lb-top"></div>
  <div class="hero-lb-bot"></div>
  <!-- Ambient floating particles -->
  <div id="hero-particles"></div>

  <div class="h-wrap">
    <div class="h-eye">
      <div class="h-pill"><span class="hp-dot"></span>Rooftop Caf&eacute; &bull; Kolkata</div>
      <span class="h-yr">Est. 2019</span>
    </div>
    <div class="h-title">
      <span class="ht-sm">Above the Hooghly</span>
      <span class="ht-big" id="heroName">GANVING</span>
      <span class="ht-it">where the river meets the sky</span>
    </div>
    <div class="h-meta">
      <div class="hm"><span class="hm-l">Location</span><span class="hm-v">Strand Road, Kolkata</span></div>
      <div class="hm-sep"></div>
      <div class="hm"><span class="hm-l">Floor</span><span class="hm-v">6th &bull; Open Sky</span></div>
      <div class="hm-sep"></div>
      <div class="hm"><span class="hm-l">Hours</span><span class="hm-v">10 AM &ndash; 12 AM</span></div>
      <div class="hm-sep"></div>
      <div class="hm"><span class="hm-l">View</span><span class="hm-v">Hooghly + Howrah Bridge</span></div>
    </div>
    <div class="h-btns">
      <a href="#menu" class="btn-a"><span>Explore Menu</span></a>
      <a href="#contact" class="btn-g">Find Us</a>
    </div>
  </div>
  <div class="h-scr"><span class="hs-l">Scroll</span><div class="hs-line"></div></div>
</section>

<!-- MARQUEE -->
<div class="mq-wrap"><div class="mq-track">
  <span class="mq-item">Rooftop Dining</span><span class="mq-item">Hooghly River View</span>
  <span class="mq-item">Howrah Bridge</span><span class="mq-item">Kolkata Cuisine</span>
  <span class="mq-item">Open Sky</span><span class="mq-item">Edison Bulbs</span>
  <span class="mq-item">Teak Wood Interiors</span><span class="mq-item">Golden Hour</span>
  <span class="mq-item">Rooftop Dining</span><span class="mq-item">Hooghly River View</span>
  <span class="mq-item">Howrah Bridge</span><span class="mq-item">Kolkata Cuisine</span>
  <span class="mq-item">Open Sky</span><span class="mq-item">Edison Bulbs</span>
  <span class="mq-item">Teak Wood Interiors</span><span class="mq-item">Golden Hour</span>
</div></div>

<!-- VIBE — REAL WOOD -->
<section id="vibe">
  <div class="ct">
    <div class="vg">
      <div>
        <span class="s-lbl" data-r>Our Story</span>
        <h2 class="s-h" data-r data-d="1">Built for <em>real</em><br/>Kolkata moments</h2>
        <div class="s-div" data-r data-d="2"></div>
        <p class="vp" data-r data-d="2">Six floors above the Strand, Ganving is Kolkata's open-sky living room. Warm teak beams, wrought iron accents, Edison filaments &mdash; and the Howrah Bridge framed in every window. Old city soul, modern edge.</p>
        <p class="vp" data-r data-d="3">Whether it's a first date, a long overdue reunion, or just needing to breathe outside the office &mdash; the Hooghly has a way of settling everything.</p>
        <div class="vcards">
          <div class="vc" data-r data-d="2"><div class="vc-i">&#x1F339;</div><div class="vc-t">For Couples</div><p class="vc-d">Candlelit corners with the bridge glowing amber behind you all evening.</p></div>
          <div class="vc" data-r data-d="3"><div class="vc-i">&#x2615;</div><div class="vc-t">For Friends</div><p class="vc-d">Long tables, shared platters, evenings that refuse to end on time.</p></div>
          <div class="vc" data-r data-d="4"><div class="vc-i">&#x1F4BC;</div><div class="vc-t">For Workers</div><p class="vc-d">Strong coffee, river wind, a view that resets your entire week.</p></div>
          <div class="vc" data-r data-d="5"><div class="vc-i">&#x1F309;</div><div class="vc-t">Open Rooftop</div><p class="vc-d">Full panoramic Hooghly &amp; Howrah Bridge at golden hour, every night.</p></div>
        </div>
      </div>
      <div class="vi" data-r="fr" data-d="2">
        <img src="https://images.unsplash.com/photo-1600093463592-8e36ae95ef56?w=900&q=85" alt="Ganving interior" loading="lazy"/>
        <div class="vi-b"><div class="vi-bt">Rooftop with a view</div><div class="vi-bs">Open daily &bull; 10 AM &ndash; 12 AM</div></div>
      </div>
    </div>
  </div>
</section>

<!-- RIVER PARALLAX STRIP -->
<div class="rstrip" id="rStrip">
  <div class="rs-bg" id="rsBg"></div>
  <div class="rs-real" id="rsReal"></div>
  <div class="rs-ov"></div>
  <div class="rs-cnt">
    <p class="rs-kicker" data-r>The Hooghly at Golden Hour</p>
    <p class="rs-q" data-r data-d="1">&ldquo;Some caf&eacute;s fill your stomach.<br/><em>Ganving fills something else entirely.</em>&rdquo;</p>
    <p class="rs-attr" data-r data-d="2">&mdash; The Telegraph, Kolkata</p>
  </div>
</div>

<!-- MENU -->
<section id="menu">
  <div class="ct">
    <span class="s-lbl" data-r>Curated Menu</span>
    <h2 class="s-h" data-r data-d="1">Something for every <em>craving</em></h2>
    <div class="mtabs" data-r data-d="2">
      <button class="mt on" onclick="mTab('vs',this)">&#x1F966; Veg Starters</button>
      <button class="mt" onclick="mTab('nvs',this)">&#x1F357; Non-Veg Starters</button>
      <button class="mt" onclick="mTab('vm',this)">&#x1F33F; Veg Main</button>
      <button class="mt" onclick="mTab('nvm',this)">&#x1F356; Non-Veg Main</button>
      <button class="mt" onclick="mTab('cf',this)">&#x2615; Coffee</button>
      <button class="mt" onclick="mTab('dr',this)">&#x1F964; Drinks</button>
      <button class="mt" onclick="mTab('ds',this)">&#x1F36E; Desserts</button>
    </div>
    <div class="mp on" id="vs"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Kolkata Puchka Shots</div>
          <div class="md">Crisp semolina shells, tamarind water, potato mash</div>
        </div>
        <div class="mpr">&#x20B9;180</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Paneer Tikka Skewers</div>
          <div class="md">Smoky tandoor cottage cheese, mint chutney</div>
        </div>
        <div class="mpr">&#x20B9;280</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Ganving Corn Chaat</div>
          <div class="md">Grilled corn, pomegranate, chaat masala, micro herbs</div>
        </div>
        <div class="mpr">&#x20B9;200</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Mushroom Bruschetta</div>
          <div class="md">Wood-fired bread, saut&eacute;ed mushrooms, truffle oil</div>
        </div>
        <div class="mpr">&#x20B9;260</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Mustard Aloo Tuk</div>
          <div class="md">Twice-cooked baby potatoes, kasundi, sesame</div>
        </div>
        <div class="mpr">&#x20B9;190</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Baked Cheese Capsicum</div>
          <div class="md">Bell peppers, herbed ricotta, cherry tomato coulis</div>
        </div>
        <div class="mpr">&#x20B9;290</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Crispy Lotus Stem Chips</div>
          <div class="md">Thinly sliced kamal kakdi, chilli-lime dust</div>
        </div>
        <div class="mpr">&#x20B9;220</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Bengal Spice Falafel</div>
          <div class="md">Chickpea falafels, hummus, pickled radish</div>
        </div>
        <div class="mpr">&#x20B9;250</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Tomato Shorba &amp; Naan</div>
          <div class="md">Heirloom tomato soup, cream swirl, toasted naan</div>
        </div>
        <div class="mpr">&#x20B9;210</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Pea &amp; Mint Arancini</div>
          <div class="md">Risotto balls, minted pea filling, smoked yogurt</div>
        </div>
        <div class="mpr">&#x20B9;270</div>
      </div>
    </div>
    </div></div>
    <div class="mp" id="nvs"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Calcutta Chicken Kabiraji</div>
          <div class="md">Egg-crumbed chicken cutlet, kasundi mayo</div>
        </div>
        <div class="mpr">&#x20B9;320</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Bhetki Fish Tikka</div>
          <div class="md">Marinated bhetki, amchur glaze, coriander oil</div>
        </div>
        <div class="mpr">&#x20B9;360</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Prawn Koliwada</div>
          <div class="md">Crispy spiced prawns, curry leaf aioli</div>
        </div>
        <div class="mpr">&#x20B9;380</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Chicken Malai Seekh</div>
          <div class="md">Minced chicken, cream cheese, mild spices</div>
        </div>
        <div class="mpr">&#x20B9;300</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Ganga Hilsa Fritters</div>
          <div class="md">Seasonal hilsa, mustard batter, green mango pickle</div>
        </div>
        <div class="mpr">&#x20B9;420</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Smoked Duck Kebab</div>
          <div class="md">Tender duck mince, black pepper, tamarind jam</div>
        </div>
        <div class="mpr">&#x20B9;440</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Lamb Shami Sliders</div>
          <div class="md">Brioche buns, pickled onion, mint yogurt</div>
        </div>
        <div class="mpr">&#x20B9;390</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Chilli Garlic Calamari</div>
          <div class="md">Squid rings, red chilli, roasted garlic butter</div>
        </div>
        <div class="mpr">&#x20B9;350</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Pork Vindaloo Pao</div>
          <div class="md">Spiced pork belly, crusty pao, pickled cabbage</div>
        </div>
        <div class="mpr">&#x20B9;370</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Butter Chicken Crostini</div>
          <div class="md">Toasted crostini, chicken makhani, basil oil</div>
        </div>
        <div class="mpr">&#x20B9;310</div>
      </div>
    </div>
    </div></div>
    <div class="mp" id="vm"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Dal Makhani &amp; Naan</div>
          <div class="md">Slow-cooked black lentils, butter, cream, tandoor naan</div>
        </div>
        <div class="mpr">&#x20B9;340</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Paneer Lababdar</div>
          <div class="md">Rich tomato-cashew gravy, makhani base, fenugreek</div>
        </div>
        <div class="mpr">&#x20B9;360</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Aloo Posto Risotto</div>
          <div class="md">Bengali poppy seed potato, arborio rice, parmesan</div>
        </div>
        <div class="mpr">&#x20B9;380</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Ganving Garden Pasta</div>
          <div class="md">Linguine, roasted vegetables, basil pesto, pine nuts</div>
        </div>
        <div class="mpr">&#x20B9;350</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Palak Mushroom Rice</div>
          <div class="md">Spinach gravy, button mushrooms, cumin-scented rice</div>
        </div>
        <div class="mpr">&#x20B9;320</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Chana Masala Burger</div>
          <div class="md">Spiced chickpea patty, brioche, slaw, sriracha mayo</div>
        </div>
        <div class="mpr">&#x20B9;290</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Bengali Veg Kathi Roll</div>
          <div class="md">Flaky paratha, paneer, onion, green chutney</div>
        </div>
        <div class="mpr">&#x20B9;270</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Methi Thepla Thali</div>
          <div class="md">Fenugreek flatbread, three sides, pickle, lassi</div>
        </div>
        <div class="mpr">&#x20B9;420</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Rooftop Veggie Bowl</div>
          <div class="md">Brown rice, roasted veggies, tahini, avocado</div>
        </div>
        <div class="mpr">&#x20B9;330</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di v"></span>Jackfruit Biryani</div>
          <div class="md">Slow-cooked kathal, saffron rice, caramelised onion</div>
        </div>
        <div class="mpr">&#x20B9;400</div>
      </div>
    </div>
    </div></div>
    <div class="mp" id="nvm"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Kolkata Mutton Biryani</div>
          <div class="md">Long grain basmati, slow-cooked mutton, potato dum</div>
        </div>
        <div class="mpr">&#x20B9;520</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Chingri Malai Curry</div>
          <div class="md">Tiger prawns, coconut milk, whole spices, steamed rice</div>
        </div>
        <div class="mpr">&#x20B9;580</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Chicken Rezala</div>
          <div class="md">Mughlai white gravy, rose water, green cardamom</div>
        </div>
        <div class="mpr">&#x20B9;420</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Bhetki Paturi</div>
          <div class="md">Steamed bhetki in banana leaf, mustard-coconut paste</div>
        </div>
        <div class="mpr">&#x20B9;490</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Grill Chicken Platter</div>
          <div class="md">Spatchcock chicken, chimichurri, grilled vegetables</div>
        </div>
        <div class="mpr">&#x20B9;450</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Lamb Rogan Josh</div>
          <div class="md">Slow-braised lamb, Kashmiri chillies, steamed rice</div>
        </div>
        <div class="mpr">&#x20B9;560</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Chicken Tikka Masala</div>
          <div class="md">Tandoor chicken, orange gravy, cream, butter naan</div>
        </div>
        <div class="mpr">&#x20B9;410</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Sorshe Ilish Rice</div>
          <div class="md">Hilsa in mustard, gobindobhog rice &mdash; pure Bengal soul</div>
        </div>
        <div class="mpr">&#x20B9;620</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Mutton Kathi Roll &times;2</div>
          <div class="md">Two flaky parathas, spiced mutton filling, raw onion</div>
        </div>
        <div class="mpr">&#x20B9;360</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn"><span class="di n"></span>Prawn Butter Garlic Pasta</div>
          <div class="md">Linguine, tiger prawns, white wine butter, parsley</div>
        </div>
        <div class="mpr">&#x20B9;480</div>
      </div>
    </div>
    </div></div>
    <div class="mp" id="cf"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Howrah Sunset Espresso</div>
          <div class="md">Double shot, sparkling water &amp; brown sugar alongside</div>
        </div>
        <div class="mpr">&#x20B9;180</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Hooghly Cold Brew</div>
          <div class="md">18-hour steep, Madagascar vanilla, over ice</div>
        </div>
        <div class="mpr">&#x20B9;220</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Ganving Filter Coffee</div>
          <div class="md">South Indian drip, frothy milk, jaggery option</div>
        </div>
        <div class="mpr">&#x20B9;160</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Saffron Cardamom Latte</div>
          <div class="md">Espresso, steamed milk, saffron-cardamom syrup</div>
        </div>
        <div class="mpr">&#x20B9;240</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Bengal Rose Cappuccino</div>
          <div class="md">Double espresso, micro-foam, rose petal, gulkand</div>
        </div>
        <div class="mpr">&#x20B9;230</div>
      </div>
    </div>
    </div></div>
    <div class="mp" id="dr"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Aam Panna Fizz</div>
          <div class="md">Raw mango, black salt, cumin, club soda</div>
        </div>
        <div class="mpr">&#x20B9;160</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Gulabi Sherbat</div>
          <div class="md">Rose syrup, basil seeds, chilled milk, cardamom</div>
        </div>
        <div class="mpr">&#x20B9;180</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Nimbu Pudina Mojito</div>
          <div class="md">Fresh lime, garden mint, jaggery, soda</div>
        </div>
        <div class="mpr">&#x20B9;170</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Strawberry Hibiscus Cooler</div>
          <div class="md">Hibiscus tea, fresh strawberry, honey, lemon</div>
        </div>
        <div class="mpr">&#x20B9;200</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Narikel Lassi</div>
          <div class="md">Coconut water, thick yogurt, palm sugar, frost-chilled</div>
        </div>
        <div class="mpr">&#x20B9;190</div>
      </div>
    </div>
    </div></div>
    <div class="mp" id="ds"><div class="mg">
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Mishti Doi Panna Cotta</div>
          <div class="md">Bengali sweet yogurt cream, caramel, pistachio</div>
        </div>
        <div class="mpr">&#x20B9;220</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Chocolate Sandesh Tart</div>
          <div class="md">Dark chocolate ganache, cottage cheese, gold leaf</div>
        </div>
        <div class="mpr">&#x20B9;260</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Saffron Kulfi Brulee</div>
          <div class="md">Slow-churned saffron kulfi, torched caramel crust</div>
        </div>
        <div class="mpr">&#x20B9;240</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Rosogolla Cheesecake</div>
          <div class="md">Creamy cheesecake, rosogolla compote, sesame crumble</div>
        </div>
        <div class="mpr">&#x20B9;290</div>
      </div>
    </div>
      <div class="mi">
      <div class="mi-top">
        <div class="mi-left">
          <div class="mn">Gulab Jamun Lava Cake</div>
          <div class="md">Cardamom chocolate, gulab jamun centre, vanilla cream</div>
        </div>
        <div class="mpr">&#x20B9;270</div>
      </div>
    </div>
    </div></div>
  </div>
</section>

<!-- GALLERY -->
<div class="gal">
  <img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?w=600&q=78" alt="cafe" loading="lazy"/>
  <img src="https://images.unsplash.com/photo-1600093463592-8e36ae95ef56?w=600&q=78" alt="interior" loading="lazy"/>
  <img src="https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=600&q=78" alt="river bridge" loading="lazy"/>
  <img src="https://images.unsplash.com/photo-1551024601-bec78aea704b?w=600&q=78" alt="dessert" loading="lazy"/>
  <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=600&q=78" alt="coffee" loading="lazy"/>
</div>

<!-- REVIEWS — WOOD -->
<section id="reviews">
  <div class="ct">
    <span class="s-lbl" data-r>Guest Stories</span>
    <h2 class="s-h" data-r data-d="1">Kolkata&rsquo;s favourite <em>view</em> with company</h2>
    <div class="rg">
      <div class="rc" data-r><div class="stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div><p class="rt">&ldquo;The bridge lit up gold at 7pm and we both went completely quiet. Best moment of our anniversary.&rdquo;</p><div class="rvr"><div class="rav">A</div><div><div class="rname">Aditi Mukherjee</div><div class="rsrc">Google Reviews &bull; 2 weeks ago</div></div></div></div>
      <div class="rc" data-r data-d="1"><div class="stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div><p class="rt">&ldquo;The Mutton Biryani and Chingri Malai &mdash; food that makes you forget you even have an inbox.&rdquo;</p><div class="rvr"><div class="rav">R</div><div><div class="rname">Rohit Chatterjee</div><div class="rsrc">Zomato &bull; 1 month ago</div></div></div></div>
      <div class="rc" data-r data-d="2"><div class="stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div><p class="rt">&ldquo;Came after a terrible client call. Left feeling like Kolkata has never been this beautiful before.&rdquo;</p><div class="rvr"><div class="rav">P</div><div><div class="rname">Priya Sen</div><div class="rsrc">Instagram &bull; 3 weeks ago</div></div></div></div>
      <div class="rc" data-r><div class="stars">&#9733;&#9733;&#9733;&#9733;&#9734;</div><p class="rt">&ldquo;The Saffron Kulfi Brulee is genuinely extraordinary. Six of us came and all fought over the last bite.&rdquo;</p><div class="rvr"><div class="rav">S</div><div><div class="rname">Saurav Ghosh</div><div class="rsrc">Google Reviews &bull; 5 days ago</div></div></div></div>
      <div class="rc" data-r data-d="1"><div class="stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div><p class="rt">&ldquo;Table of 8 and they handled everything perfectly. Filter Coffee at sunset &mdash; I will always dream of it.&rdquo;</p><div class="rvr"><div class="rav">N</div><div><div class="rname">Nandita Bose</div><div class="rsrc">Dineout &bull; 3 weeks ago</div></div></div></div>
      <div class="rc" data-r data-d="2"><div class="stars">&#9733;&#9733;&#9733;&#9733;&#9733;</div><p class="rt">&ldquo;Found my permanent WFH spot. Reliable WiFi, strong cold brew, and the Hooghly right outside. Zero complaints.&rdquo;</p><div class="rvr"><div class="rav">D</div><div><div class="rname">Dev Sharma</div><div class="rsrc">Google Reviews &bull; 1 week ago</div></div></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="ct">
    <div class="cg">
      <div>
        <span class="s-lbl" data-r>Find Us</span>
        <h2 class="s-h" data-r data-d="1">Come up to the <em>rooftop</em></h2>
        <div class="s-div" data-r data-d="2"></div>
        <div data-r data-d="2">
          <div class="crow"><div class="cico">&#x1F4CD;</div><div><div class="clbl">Location</div><div class="cval">6th Floor, Strand Commercial Building<br/>Strand Road, Near Howrah Bridge<br/>Kolkata, West Bengal &ndash; 700001</div></div></div>
          <div class="crow"><div class="cico">&#x1F4DE;</div><div><div class="clbl">Reservations</div><div class="cval"><a href="tel:+919800000000">+91 98000 00000</a><br/><a href="tel:+913312345678">033 1234 5678</a></div></div></div>
          <div class="crow"><div class="cico">&#x1F4AC;</div><div><div class="clbl">WhatsApp</div><div class="cval"><a href="https://wa.me/919800000000">+91 98000 00000</a></div></div></div>
          <div class="crow"><div class="cico">&#x2709;&#xFE0F;</div><div><div class="clbl">Email</div><div class="cval"><a href="mailto:hello@ganving.in">hello@ganving.in</a></div></div></div>
        </div>
        <div data-r data-d="3">
          <table class="htbl">
            <tr><td class="hday">Mon &ndash; Fri</td><td class="htime">10 AM &ndash; 11 PM</td></tr>
            <tr><td class="hday">Saturday</td><td class="htime">9 AM &ndash; 12 AM</td></tr>
            <tr><td class="hday">Sunday</td><td class="htime">9 AM &ndash; 11 PM</td></tr>
            <tr><td class="hday">Holidays</td><td class="htime">10 AM &ndash; 12 AM</td></tr>
          </table>
        </div>
      </div>
      <div class="mpbox" data-r="fr" data-d="2">
        <div class="mppin">&#x1F4CD;</div>
        <p class="mpaddr">Strand Road, Near Howrah Bridge<br/>Kolkata &ndash; 700001</p>
        <a href="https://maps.google.com/?q=Howrah+Bridge+Kolkata" target="_blank" class="mplink">Open in Maps &#x2192;</a>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="fl">GAN<em>VING</em></div>
  <p>&copy; 2025 Ganving Rooftop Caf&eacute;, Kolkata &bull; All Rights Reserved</p>
  <p style="margin-top:.35rem;font-size:.65rem">Where the Hooghly meets the sky</p>
</footer>

<!-- FLOATING BUTTONS -->
<div class="floats">
  <a href="https://wa.me/919800000000" target="_blank" class="fb fwa">
    <span class="ftip">WhatsApp Us</span>
    <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
  </a>
  <a href="tel:+919800000000" class="fb fcl">
    <span class="ftip">Call Now</span>
    <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg>
  </a>
</div>

</div><!-- #app -->

<script>
/* ═══════════════════════════ JS ═══════════════════════════ */
var SY = 0;

/* ── IMAGE INJECTION: apply stored b64 images to CSS backgrounds ── */
(function injectImages(){
  function applyImages(){
    var bridge = document.getElementById('img-bridge');
    var wood   = document.getElementById('img-wood');
    if(!bridge || !wood) return;
    var bSrc = bridge.src;
    var wSrc = wood.src;

    /* Hero background */
    var heroCss = document.getElementById('heroCss');
    if(heroCss) heroCss.style.backgroundImage = "url('" + bSrc + "')";

    /* Vibe section */
    var vibe = document.getElementById('vibe');
    if(vibe){
      vibe.style.backgroundImage =
        "linear-gradient(158deg,rgba(22,12,4,.62) 0%,rgba(31,16,8,.48) 35%,rgba(46,23,16,.42) 65%,rgba(62,32,22,.38) 100%), url('" + wSrc + "')";
      vibe.style.backgroundSize = "cover,cover";
      vibe.style.backgroundBlendMode = "multiply,normal";
    }

    /* Reviews section */
    var reviews = document.getElementById('reviews');
    if(reviews){
      reviews.style.backgroundImage =
        "linear-gradient(158deg,rgba(62,32,22,.72) 0%,rgba(46,23,16,.62) 45%,rgba(31,16,8,.68) 100%), url('" + wSrc + "')";
      reviews.style.backgroundSize = "cover,cover";
      reviews.style.backgroundBlendMode = "multiply,normal";
    }

    /* Light mode: same images, different blend */
    window._bridgeSrc = bSrc;
    window._woodSrc   = wSrc;
  }

  if(document.readyState === 'loading'){
    document.addEventListener('DOMContentLoaded', applyImages);
  } else {
    applyImages();
  }
})();


/* theme JS removed */



/* ══════════════════════════════════════════════════════
   CINEMATIC 3D LANDING — Canvas depth field + sequence
══════════════════════════════════════════════════════ */

/* ── CANVAS 3D PARTICLE DEPTH FIELD ── */
(function(){
  var cv = document.getElementById('intro-canvas');
  if(!cv) return;
  var ctx = cv.getContext('2d');
  var W, H, raf, t = 0;

  /* Particle pool */
  var N = 200, pts = [];

  function rand(a,b){ return a + Math.random()*(b-a); }

  function resize(){
    W = cv.width  = window.innerWidth;
    H = cv.height = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', resize, {passive:true});

  for(var i=0; i<N; i++){
    var amber = Math.random() > 0.35;
    pts.push({
      x:  rand(0, 1),       /* normalised 0-1 */
      y:  rand(0, 1),
      z:  rand(0.05, 1),    /* depth: 1=near, 0=far */
      vx: rand(-0.06, 0.06),
      vy: rand(-0.18, -0.04),
      r:  amber ? 212 : 240,
      g:  amber ? 134 : 235,
      b:  amber ? 42  : 224,
      base_a: rand(0.08, 0.75),
      sz: rand(0.5, 2.8),
      tw: rand(0, Math.PI*2),
      ts: rand(0.008, 0.025),
    });
  }

  function draw(){
    ctx.clearRect(0,0,W,H);
    t += 0.008;

    /* 1. Deep space bg */
    var bg = ctx.createRadialGradient(W*.5, H*.55, 0, W*.5, H*.5, Math.max(W,H)*.75);
    bg.addColorStop(0,   'rgba(28,12,3,.9)');
    bg.addColorStop(0.4, 'rgba(12,7,2,.95)');
    bg.addColorStop(1,   'rgba(0,0,0,1)');
    ctx.fillStyle = bg; ctx.fillRect(0,0,W,H);

    /* 2. Amber horizon pulse */
    var pulse = 0.12 + 0.04 * Math.sin(t * 0.7);
    var hor = ctx.createRadialGradient(W*.5, H*.68, 0, W*.5, H*.65, W*.48);
    hor.addColorStop(0,   'rgba(212,134,42,'+pulse+')');
    hor.addColorStop(0.45,'rgba(212,134,42,'+(pulse*.3)+')');
    hor.addColorStop(1,   'transparent');
    ctx.fillStyle = hor; ctx.fillRect(0,0,W,H);

    /* 3. Subtle light rays */
    for(var r=0; r<3; r++){
      var rx = W*(0.28 + r*0.22);
      var rg = ctx.createLinearGradient(rx, H, rx + 40*Math.sin(t*.3+r), 0);
      rg.addColorStop(0,   'rgba(212,134,42,0)');
      rg.addColorStop(0.4, 'rgba(212,134,42,.025)');
      rg.addColorStop(0.7, 'rgba(235,169,82,.04)');
      rg.addColorStop(1,   'transparent');
      ctx.fillStyle = rg;
      ctx.beginPath();
      ctx.moveTo(rx - 30, H);
      ctx.lineTo(rx + 30, H);
      ctx.lineTo(rx + 80 + r*20, 0);
      ctx.lineTo(rx - 80 - r*20, 0);
      ctx.closePath();
      ctx.fill();
    }

    /* 4. Particles with DOF */
    pts.forEach(function(p){
      p.tw += p.ts;
      var tw   = 0.5 + 0.5 * Math.sin(p.tw);
      var near = p.z;                        /* 0=far, 1=near */
      var sz   = p.sz * (0.3 + near * 0.7) * (W/1440);
      var a    = p.base_a * tw * (0.25 + near * 0.75);

      /* depth-of-field: far particles blurred */
      if(near > 0.5){
        ctx.shadowBlur  = sz * (2 + near * 4);
        ctx.shadowColor = 'rgba('+p.r+','+p.g+','+p.b+',.7)';
      } else {
        ctx.shadowBlur = 0;
        a *= 0.35;
      }

      ctx.beginPath();
      ctx.arc(p.x * W, p.y * H, Math.max(0.3, sz), 0, Math.PI*2);
      ctx.fillStyle = 'rgba('+p.r+','+p.g+','+p.b+','+Math.min(a,1)+')';
      ctx.fill();
      ctx.shadowBlur = 0;

      /* Move */
      p.x += p.vx * 0.0003;
      p.y += p.vy * (0.3 + near * 0.7) * 0.001;

      /* Wrap */
      if(p.y < -0.02){ p.y = 1.02; p.x = rand(0,1); }
      if(p.x < -0.02)  p.x = 1.02;
      if(p.x >  1.02)  p.x = -0.02;
    });

    /* 5. Horizontal film grain lines */
    ctx.globalAlpha = 0.06;
    for(var l=0; l<H; l+=4){
      ctx.fillStyle = 'rgba(0,0,0,'+(Math.random()*.15)+')';
      ctx.fillRect(0, l, W, 1);
    }
    ctx.globalAlpha = 1;

    raf = requestAnimationFrame(draw);
  }
  draw();

  window.addEventListener('stopIntroCanvas', function(){
    cancelAnimationFrame(raf);
    /* fade canvas out */
    cv.style.transition = 'opacity .8s ease';
    cv.style.opacity = '0';
  });
})();

/* ── INTRO SEQUENCE CONTROLLER ── */
window.addEventListener('load', function(){

  /* Step 1 — after 3.2s: collapse loader */
  setTimeout(function(){
    var ld  = document.getElementById('loader');
    var app = document.getElementById('app');
    if(!ld || !app) return;

    /* Stop canvas */
    window.dispatchEvent(new Event('stopIntroCanvas'));

    /* Scale+fade the loader away */
    ld.style.transition = 'opacity 1s cubic-bezier(.76,0,.24,1), transform 1.4s cubic-bezier(.76,0,.24,1), visibility 1s';
    ld.style.transform  = 'scale(1.08) translateZ(0)';
    ld.classList.add('gone');

    /* Step 2 — 200ms later: reveal site */
    setTimeout(function(){
      app.classList.add('in');

      /* Step 3 — 400ms after site in: scramble title */
      setTimeout(startScramble, 400);

      /* Step 4 — spawn hero particles */
      setTimeout(spawnHeroParticles, 600);

    }, 200);

  }, 3200);
});

/* ── HERO AMBIENT PARTICLES ── */
function spawnHeroParticles(){
  var wrap = document.getElementById('hero-particles');
  if(!wrap) return;
  for(var i=0; i<30; i++){
    var el   = document.createElement('div');
    el.className = 'hp';
    var amber= Math.random() > 0.4;
    var sz   = 1 + Math.random() * 2.5;
    var dur  = 6 + Math.random() * 10;
    var dl   = Math.random() * 8;
    var tx   = (Math.random() - 0.5) * 80;
    var ty   = -(25 + Math.random() * 70);
    var al   = (.12 + Math.random() * .45).toFixed(2);
    el.style.cssText =
      'left:'  + (Math.random()*96+2) + '%;' +
      'top:'   + (Math.random()*90+5) + '%;' +
      'width:' + sz + 'px;height:' + sz + 'px;' +
      '--tx:'  + tx + 'px;--ty:' + ty + 'px;' +
      '--d:'   + dur + 's;--dl:' + dl + 's;' +
      'opacity:' + al + ';' +
      'background:rgba(' + (amber?'212,134,42':'240,235,224') + ',' + al + ');' +
      'box-shadow:0 0 '+(sz*4)+'px rgba(212,134,42,.6);';
    wrap.appendChild(el);
  }
}
/* NAV */
var nav = document.getElementById('nav');
window.addEventListener('scroll',function(){ SY=window.scrollY; nav.classList.toggle('dk',SY>80); },{passive:true});
function mobOn(){document.getElementById('mob').classList.add('on');}
function mobOff(){document.getElementById('mob').classList.remove('on');}

/* Hero uses embedded bridge image in CSS — no JS loader needed */

/* HERO PARALLAX */
var heroCss = document.getElementById('heroCss');
window.addEventListener('scroll',function(){
  var y = window.scrollY;
  if(heroCss) heroCss.style.transform = 'scale(1.06) translateY('+(y*.28)+'px)';
},{passive:true});

/* RIVER STRIP: same dual-layer approach */
var rsBg = document.getElementById('rsBg');
var rsReal = document.getElementById('rsReal');
var rStrip = document.getElementById('rStrip');
var riverSrcs = [
  'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=2000&q=85&auto=format&fit=crop',
  'https://images.unsplash.com/photo-1536164261511-3a17e671d380?w=2000&q=85&auto=format&fit=crop',
  'https://images.unsplash.com/photo-1582560474992-385ed5da87fc?w=2000&q=85&auto=format&fit=crop'
];
(function loadRiver(i){
  if(i >= riverSrcs.length || !rsReal) return;
  var img = new Image();
  img.onload = function(){
    rsReal.style.backgroundImage = "url('" + riverSrcs[i] + "')";
    rsReal.classList.add('rdy');
  };
  img.onerror = function(){ loadRiver(i+1); };
  img.src = riverSrcs[i];
})(0);
window.addEventListener('scroll',function(){
  if(!rStrip) return;
  var r = rStrip.getBoundingClientRect();
  var off = (window.innerHeight/2 - r.top - r.height/2) * .2;
  if(rsBg) rsBg.style.transform = 'translateY('+off+'px)';
  if(rsReal) rsReal.style.transform = 'translateY('+off+'px)';
},{passive:true});

/* MENU TABS */
function mTab(id, btn){
  document.querySelectorAll('.mp').forEach(function(p){p.classList.remove('on');});
  document.querySelectorAll('.mt').forEach(function(b){b.classList.remove('on');});
  document.getElementById(id).classList.add('on');
  btn.classList.add('on');
}

/* TEXT SCRAMBLE on hero name — Gen Z effect */
function startScramble(){
  var el = document.getElementById('heroName');
  if(!el) return;
  var orig = 'GANVING';
  var chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#&';
  var f = 0, total = orig.length*2 + 10;
  (function tick(){
    var out = '';
    for(var i=0;i<orig.length;i++){
      out += i < Math.floor(f/2) ? orig[i] : chars[Math.floor(Math.random()*chars.length)];
    }
    el.textContent = out;
    f++;
    if(f < total) requestAnimationFrame(tick);
    else el.textContent = orig;
  })();
}

/* APPLE SCROLL REVEAL — spring easing */
var obs = new IntersectionObserver(function(es){
  es.forEach(function(e){
    if(e.isIntersecting){ e.target.classList.add('on'); obs.unobserve(e.target); }
  });
},{threshold:0.1, rootMargin:'0px 0px -50px 0px'});
document.querySelectorAll('[data-r]').forEach(function(el){ obs.observe(el); });

/* MAGNETIC HOVER on CTA buttons */
document.querySelectorAll('.btn-a,.btn-g,.n-cta,.fb').forEach(function(btn){
  btn.addEventListener('mousemove',function(e){
    var r=btn.getBoundingClientRect();
    var dx=(e.clientX-r.left-r.width/2)*.22;
    var dy=(e.clientY-r.top-r.height/2)*.22;
    btn.style.transform='translate('+dx+'px,'+dy+'px)';
  });
  btn.addEventListener('mouseleave',function(){btn.style.transform='';});
});

/* ══ MENU CARD 3D TILT + GLASS HOVER ══ */
(function initMenuTilt(){
  function applyTilt(card){
    card.addEventListener('mousemove', function(e){
      var r = card.getBoundingClientRect();
      var x = e.clientX - r.left;
      var y = e.clientY - r.top;
      var cx = r.width  / 2;
      var cy = r.height / 2;
      /* max ±12deg tilt */
      var rotY =  ((x - cx) / cx) * 12;
      var rotX = -((y - cy) / cy) * 8;
      /* parallax shine position */
      var px = (x / r.width)  * 100;
      var py = (y / r.height) * 100;
      card.style.transform =
        'perspective(800px) rotateX('+rotX+'deg) rotateY('+rotY+'deg) translateZ(8px)';
      card.style.setProperty('--shine-x', px + '%');
      card.style.setProperty('--shine-y', py + '%');
    });
    card.addEventListener('mouseleave', function(){
      card.style.transform =
        'perspective(800px) rotateX(0deg) rotateY(0deg) translateZ(0)';
      card.style.boxShadow = '';
    });
  }
  /* Apply to all current and future menu items */
  function attachAll(){
    document.querySelectorAll('.mi').forEach(function(card){
      if(!card.dataset.tilt){ card.dataset.tilt='1'; applyTilt(card); }
    });
  }
  attachAll();
  /* Re-attach when tab switches (new cards become visible) */
  document.querySelectorAll('.mt').forEach(function(btn){
    btn.addEventListener('click', function(){ setTimeout(attachAll, 50); });
  });
})();
</script>
</body>
</html>
