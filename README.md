<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
  <title>EnglishUp 🇺🇸 – Aprende Inglés Paso a Paso</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=DM+Sans:wght@400;500;700&display=swap" rel="stylesheet"/>
  <style>
  :root{
    --bg:#06080f;
    --surface:#0e1220;
    --surface2:#141828;
    --border:rgba(255,255,255,0.07);
    --text:#e8eaf6;
    --muted:#5a6480;
    --c1:#00e5c3;
    --c2:#ff5f6d;
    --c3:#7c5cbf;
    --c4:#f9c74f;
    --c5:#4cc9f0;
    --c6:#f77f00;
    --c7:#06d6a0;
    --c8:#ef476f;
    --c9:#118ab2;
    --c10:#ffd166;
    --c11:#8338ec;
    --c12:#3a86ff;
    --perspective:1200px;
    --depth-sm:0 2px 4px rgba(0,0,0,.3),0 8px 16px rgba(0,0,0,.2);
    --depth-md:0 4px 8px rgba(0,0,0,.4),0 12px 28px rgba(0,0,0,.25),0 24px 48px rgba(0,0,0,.15);
    --depth-lg:0 8px 16px rgba(0,0,0,.5),0 20px 40px rgba(0,0,0,.3),0 40px 80px rgba(0,0,0,.2),0 0 120px rgba(0,0,0,.1);
    --depth-glow-c1:0 8px 32px rgba(0,229,195,.15),0 2px 8px rgba(0,0,0,.4);
  }
  *{margin:0;padding:0;box-sizing:border-box}
  html{scroll-behavior:smooth}
  body{background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;min-height:100vh;overflow-x:hidden;perspective:var(--perspective)}

  .englishup-main-container {
    position: relative;
    z-index: 10;
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px 0;
    transform-style: preserve-3d;
  }

  /* ── Fondo 3D con capas de profundidad ── */
  #particles{position:fixed;inset:0;pointer-events:none;z-index:0;overflow:hidden;transform-style:preserve-3d;perspective:800px}
  .pt{position:absolute;border-radius:50%;opacity:.18;animation:drift linear infinite;transform-style:preserve-3d}
  .pt::after{content:'';position:absolute;inset:-2px;border-radius:50%;background:inherit;filter:blur(6px);opacity:.5}
  @keyframes drift{
    0%{transform:translateY(100vh) translateZ(-200px) rotate(0) scale(.6);opacity:0}
    10%{opacity:.18}
    90%{opacity:.18}
    100%{transform:translateY(-120px) translateZ(100px) rotate(720deg) scale(1);opacity:0}
  }

  /* ── Capas de fondo atmosférico ── */
  .bg-depth-layers{position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden}
  .bg-layer{position:absolute;border-radius:50%;filter:blur(100px);opacity:.08;animation:layerFloat 20s ease-in-out infinite alternate}
  .bg-layer:nth-child(1){width:600px;height:600px;background:var(--c1);top:-10%;left:-10%;animation-delay:0s}
  .bg-layer:nth-child(2){width:500px;height:500px;background:var(--c3);bottom:-15%;right:-5%;animation-delay:-7s;animation-duration:25s}
  .bg-layer:nth-child(3){width:400px;height:400px;background:var(--c5);top:40%;left:50%;animation-delay:-13s;animation-duration:30s}
  @keyframes layerFloat{
    0%{transform:translate3d(0,0,-100px) scale(1)}
    50%{transform:translate3d(40px,-30px,50px) scale(1.15)}
    100%{transform:translate3d(-20px,20px,-50px) scale(.95)}
  }

  /* ── Nav 3D ── */
  nav{
    position:sticky;top:0;z-index:200;
    background:linear-gradient(180deg,rgba(14,18,32,.95) 0%,rgba(14,18,32,.88) 100%);
    backdrop-filter:blur(24px) saturate(1.2);
    -webkit-backdrop-filter:blur(24px) saturate(1.2);
    border-bottom:1px solid var(--border);
    padding:14px 28px;
    display:flex;align-items:center;justify-content:space-between;
    border-radius:20px 20px 0 0;
    margin-bottom:10px;
    box-shadow:0 -4px 20px rgba(0,0,0,.3),0 8px 32px rgba(0,0,0,.4),inset 0 1px 0 rgba(255,255,255,.06);
    transform:translateZ(40px);
    transform-style:preserve-3d;
  }
  .logo{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;background:linear-gradient(90deg,var(--c1),var(--c3));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;filter:drop-shadow(0 2px 8px rgba(0,229,195,.25))}
  .nav-tabs{display:flex;gap:8px;flex-wrap:wrap;transform-style:preserve-3d}
  .nav-tab{
    padding:7px 18px;border-radius:22px;border:none;cursor:pointer;
    font-family:'DM Sans',sans-serif;font-weight:700;font-size:13px;
    transition:all .25s cubic-bezier(.4,0,.2,1);
    background:rgba(255,255,255,.06);color:#aaa;text-decoration:none;display:inline-block;
    box-shadow:0 2px 8px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.05);
    transform:translateZ(0) translateX(0) translateY(0);
    transform-style:preserve-3d;
    position:relative;overflow:hidden;
  }
  .nav-tab::before{content:'';position:absolute;inset:0;background:linear-gradient(180deg,rgba(255,255,255,.08) 0%,transparent 50%);border-radius:22px;pointer-events:none}
  .nav-tab.active{
    background:linear-gradient(90deg,var(--c1),#00b89c);color:#06080f;
    box-shadow:0 4px 16px rgba(0,229,195,.35),0 2px 4px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.25);
    transform:translateZ(12px) translateY(-1px);
  }
  .nav-tab:hover:not(.active){
    background:rgba(255,255,255,.12);color:#fff;
    transform:translateZ(6px) translateY(-1px);
    box-shadow:0 4px 12px rgba(0,0,0,.4),inset 0 1px 0 rgba(255,255,255,.08);
  }

  /* ── Pantallas con profundidad ── */
  .screen{
    display:none;position:relative;z-index:1;
    min-height:calc(100vh - 120px);
    background:linear-gradient(180deg,var(--surface) 0%,rgba(14,18,32,.97) 100%);
    border-radius:0 0 24px 24px;padding-bottom:40px;
    border:1px solid var(--border);border-top:none;
    box-shadow:inset 0 2px 0 rgba(255,255,255,.04),0 20px 60px rgba(0,0,0,.5),0 8px 24px rgba(0,0,0,.3);
    transform:translateZ(20px);
    transform-style:preserve-3d;
  }
  .screen.active{display:block;animation:screenIn .5s cubic-bezier(.4,0,.2,1)}
  @keyframes screenIn{from{opacity:0;transform:translateZ(-30px) rotateX(2deg)}to{opacity:1;transform:translateZ(20px) rotateX(0)}}

  /* ── Hero 3D ── */
  .hero{text-align:center;padding:64px 20px 48px;transform-style:preserve-3d;perspective:800px}
  .hero-tag{
    display:inline-block;
    background:linear-gradient(90deg,var(--c1),var(--c3));
    border-radius:30px;padding:5px 18px;font-size:11px;font-weight:700;letter-spacing:2.5px;text-transform:uppercase;margin-bottom:22px;color:#06080f;
    box-shadow:0 4px 20px rgba(0,229,195,.3),0 2px 4px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.3);
    transform:translateZ(30px);
    position:relative;overflow:hidden;
  }
  .hero-tag::after{content:'';position:absolute;top:0;left:0;right:0;height:50%;background:linear-gradient(180deg,rgba(255,255,255,.3),transparent);border-radius:30px 30px 0 0;pointer-events:none}
  .hero h1{
    font-family:'Syne',sans-serif;font-size:clamp(2.4rem,6vw,4.2rem);font-weight:800;line-height:1.08;letter-spacing:-2px;margin-bottom:18px;
    transform:translateZ(50px);
    text-shadow:0 4px 20px rgba(0,0,0,.5);
  }
  .hero h1 span{background:linear-gradient(90deg,var(--c1),var(--c5),var(--c3));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;filter:drop-shadow(0 0 30px rgba(0,229,195,.2))}
  .hero p{font-size:17px;color:var(--muted);max-width:540px;margin:0 auto 36px;line-height:1.8;transform:translateZ(20px)}

  /* ── Barra de progreso 3D ── */
  .prog-wrap{
    max-width:420px;margin:0 auto 10px;
    background:rgba(255,255,255,.06);border-radius:20px;height:12px;overflow:hidden;
    box-shadow:inset 0 2px 6px rgba(0,0,0,.6),0 1px 0 rgba(255,255,255,.05);
    transform:translateZ(15px);position:relative;
  }
  .prog-fill{
    height:100%;background:linear-gradient(90deg,var(--c1),var(--c3));border-radius:20px;transition:width .8s cubic-bezier(.4,2,.6,1);
    position:relative;overflow:hidden;
    box-shadow:0 0 12px rgba(0,229,195,.4);
  }
  .prog-fill::after{content:'';position:absolute;top:0;left:0;right:0;height:50%;background:linear-gradient(180deg,rgba(255,255,255,.35),transparent);border-radius:20px 20px 0 0}
  .prog-label{font-size:12px;color:var(--muted);margin-bottom:32px;transform:translateZ(10px)}

  /* ── Botón CTA 3D ── */
  .cta-btn{
    display:inline-block;padding:15px 40px;border-radius:22px;border:none;
    background:linear-gradient(135deg,var(--c1),#00b89c);color:#06080f;
    font-family:'DM Sans',sans-serif;font-weight:800;font-size:16px;cursor:pointer;
    transition:all .25s cubic-bezier(.4,0,.2,1);letter-spacing:.3px;text-decoration:none;
    box-shadow:0 4px 0 #009980,0 8px 24px rgba(0,229,195,.3),0 2px 4px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.25);
    transform:translateZ(25px) translateY(0);position:relative;overflow:hidden;
  }
  .cta-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.3),transparent);border-radius:22px 22px 0 0;pointer-events:none}
  .cta-btn:hover{
    transform:translateZ(30px) translateY(-2px);
    box-shadow:0 6px 0 #009980,0 16px 40px rgba(0,229,195,.4),0 4px 8px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.3);
  }
  .cta-btn:active{
    transform:translateZ(10px) translateY(3px);
    box-shadow:0 1px 0 #009980,0 2px 8px rgba(0,229,195,.2),inset 0 1px 0 rgba(255,255,255,.15);
  }

  /* ── Feature Cards 3D ── */
  .feat-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:24px;max-width:980px;margin:0 auto;padding:0 20px 70px;perspective:var(--perspective)}
  .feat-card{
    border-radius:22px;padding:26px;
    background:linear-gradient(160deg,rgba(255,255,255,.06) 0%,rgba(255,255,255,.02) 100%);
    border:1px solid var(--border);
    transition:all .3s cubic-bezier(.4,0,.2,1);
    transform-style:preserve-3d;
    transform:translateZ(0);
    box-shadow:var(--depth-md);
    position:relative;overflow:hidden;cursor:default;
  }
  .feat-card::before{
    content:'';position:absolute;top:0;left:0;right:0;height:50%;
    background:linear-gradient(180deg,rgba(255,255,255,.06),transparent);
    border-radius:22px 22px 0 0;pointer-events:none;z-index:1;
  }
  .feat-card::after{
    content:'';position:absolute;inset:0;border-radius:22px;
    background:radial-gradient(600px circle at var(--mx,50%) var(--my,50%),rgba(255,255,255,.06),transparent 40%);
    pointer-events:none;z-index:1;
  }
  .feat-card:hover{
    transform:translateZ(20px) translateY(-6px) rotateX(2deg);
    box-shadow:var(--depth-lg);border-color:rgba(255,255,255,.15);
  }
  .feat-icon{font-size:38px;margin-bottom:14px;filter:drop-shadow(0 4px 8px rgba(0,0,0,.4));transform:translateZ(10px);position:relative;z-index:2}
  .feat-card h3{font-family:'Syne',sans-serif;font-size:16px;margin-bottom:7px;transform:translateZ(8px);position:relative;z-index:2}
  .feat-card p{font-size:13px;color:var(--muted);line-height:1.65;position:relative;z-index:2}

  /* ── Levels Header ── */
  .levels-header{text-align:center;padding:48px 20px 32px;transform-style:preserve-3d}
  .levels-header h2{font-family:'Syne',sans-serif;font-size:clamp(1.8rem,4vw,2.8rem);font-weight:800;letter-spacing:-1.5px;margin-bottom:10px;text-shadow:0 4px 16px rgba(0,0,0,.4)}
  .levels-header p{color:var(--muted);font-size:15px}

  /* ── Level Cards 3D ── */
  .levels-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:28px;max-width:1100px;margin:0 auto;padding:0 20px 70px;perspective:var(--perspective)}
  @media(max-width:860px){.levels-grid{grid-template-columns:repeat(2,1fr)}}
  @media(max-width:560px){.levels-grid{grid-template-columns:1fr}}

  .level-card{
    border-radius:24px;padding:26px 24px 22px;
    background:linear-gradient(170deg,rgba(255,255,255,.06) 0%,rgba(255,255,255,.015) 100%);
    border:1.5px solid var(--border);cursor:pointer;
    transition:all .35s cubic-bezier(.4,0,.2,1);
    position:relative;overflow:hidden;
    transform-style:preserve-3d;transform:translateZ(0);
    box-shadow:var(--depth-md);
  }
  .level-card::before{
    content:'';position:absolute;top:-50px;right:-50px;width:140px;height:140px;
    border-radius:50%;opacity:.15;filter:blur(35px);transition:.3s;
    transform:translateZ(20px);
  }
  .level-card::after{
    content:'';position:absolute;inset:0;border-radius:24px;
    background:radial-gradient(500px circle at var(--mx,50%) var(--my,50%),rgba(255,255,255,.07),transparent 40%);
    pointer-events:none;z-index:1;
  }
  .level-card .specular{
    position:absolute;top:0;left:0;right:0;height:45%;
    background:linear-gradient(180deg,rgba(255,255,255,.07),transparent);
    border-radius:24px 24px 0 0;pointer-events:none;z-index:2;
  }
  .level-card:hover{
    transform:translateZ(30px) translateY(-8px) scale(1.02);
    box-shadow:var(--depth-lg);border-color:rgba(255,255,255,.2);
  }
  .level-card>*{position:relative;z-index:3}
  .level-badge{display:inline-flex;align-items:center;gap:6px;border-radius:20px;padding:4px 13px;font-size:11px;font-weight:700;letter-spacing:.5px;margin-bottom:14px;box-shadow:0 2px 8px rgba(0,0,0,.3);transform:translateZ(15px)}
  .level-card h3{font-family:'Syne',sans-serif;font-size:20px;margin-bottom:5px;transform:translateZ(12px);text-shadow:0 2px 8px rgba(0,0,0,.3)}
  .level-card .ldesc{font-size:13px;color:var(--muted);margin-bottom:16px;line-height:1.55;transform:translateZ(8px)}
  .dots{display:flex;gap:6px;margin-bottom:10px;transform:translateZ(10px)}
  .dot{
    width:10px;height:10px;border-radius:50%;
    background:rgba(255,255,255,.1);transition:.3s;
    box-shadow:inset 0 1px 2px rgba(0,0,0,.4),0 1px 0 rgba(255,255,255,.05);
    transform:translateZ(5px);
  }
  .dot.done{background:currentColor;box-shadow:inset 0 1px 2px rgba(0,0,0,.2),0 0 8px currentColor}
  .lcount{font-size:12px;color:var(--muted);margin-bottom:14px;transform:translateZ(8px)}
  .start-btn{
    padding:9px 20px;border-radius:14px;border:none;
    font-family:'DM Sans',sans-serif;font-weight:700;font-size:13px;cursor:pointer;
    transition:all .25s cubic-bezier(.4,0,.2,1);text-decoration:none;display:inline-block;text-align:center;width:100%;
    transform:translateZ(20px);
    box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px rgba(0,0,0,.25),inset 0 1px 0 rgba(255,255,255,.2);
    position:relative;overflow:hidden;
  }
  .start-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.2),transparent);border-radius:14px 14px 0 0;pointer-events:none}
  .start-btn:hover{transform:translateZ(25px) translateY(-2px) scale(1.02);box-shadow:0 5px 0 rgba(0,0,0,.3),0 12px 28px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.25)}
  .start-btn:active{transform:translateZ(10px) translateY(2px);box-shadow:0 1px 0 rgba(0,0,0,.3),0 2px 6px rgba(0,0,0,.2),inset 0 1px 0 rgba(255,255,255,.1)}

  /* ── Lesson Section ── */
  .lesson-section{max-width:760px;margin:0 auto;padding:30px 20px 70px;perspective:var(--perspective)}
  .back-btn{
    display:inline-flex;align-items:center;gap:8px;
    background:linear-gradient(180deg,rgba(255,255,255,.08),rgba(255,255,255,.04));
    border:1px solid var(--border);border-radius:14px;padding:8px 16px;cursor:pointer;
    color:#aaa;font-size:14px;font-weight:700;margin-bottom:28px;
    transition:all .25s;text-decoration:none;
    box-shadow:0 2px 0 rgba(0,0,0,.3),0 4px 12px rgba(0,0,0,.25),inset 0 1px 0 rgba(255,255,255,.06);
    transform:translateZ(10px);position:relative;overflow:hidden;
  }
  .back-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.06),transparent);border-radius:14px 14px 0 0;pointer-events:none}
  .back-btn:hover{background:linear-gradient(180deg,rgba(255,255,255,.12),rgba(255,255,255,.06));color:#fff;transform:translateZ(15px) translateY(-1px);box-shadow:0 3px 0 rgba(0,0,0,.3),0 8px 20px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.08)}
  .back-btn:active{transform:translateZ(5px) translateY(1px);box-shadow:0 1px 0 rgba(0,0,0,.3),0 2px 4px rgba(0,0,0,.2)}
  .section-title{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;letter-spacing:-1px;margin-bottom:6px;text-shadow:0 3px 12px rgba(0,0,0,.4)}
  .section-sub{color:var(--muted);margin-bottom:28px;font-size:14px}

  /* ── Lesson Rows 3D ── */
  .lesson-row{
    border-radius:20px;padding:20px;margin-bottom:14px;
    background:linear-gradient(160deg,rgba(255,255,255,.05) 0%,rgba(255,255,255,.02) 100%);
    border:1px solid var(--border);cursor:pointer;
    transition:all .3s cubic-bezier(.4,0,.2,1);
    display:flex;align-items:center;gap:16px;
    transform-style:preserve-3d;transform:translateZ(0);
    box-shadow:var(--depth-sm);position:relative;overflow:hidden;
  }
  .lesson-row::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.04),transparent);border-radius:20px 20px 0 0;pointer-events:none}
  .lesson-row::after{content:'';position:absolute;inset:0;border-radius:20px;background:radial-gradient(400px circle at var(--mx,50%) var(--my,50%),rgba(255,255,255,.05),transparent 40%);pointer-events:none}
  .lesson-row:hover{background:linear-gradient(160deg,rgba(255,255,255,.08),rgba(255,255,255,.04));border-color:rgba(255,255,255,.18);transform:translateZ(15px) translateY(-3px);box-shadow:var(--depth-md)}
  .lesson-row.done{background:linear-gradient(160deg,rgba(0,229,195,.08),rgba(0,229,195,.03));border-color:rgba(0,229,195,.3);box-shadow:var(--depth-sm),0 0 20px rgba(0,229,195,.08)}
  .lesson-icon{font-size:32px;flex-shrink:0;filter:drop-shadow(0 3px 6px rgba(0,0,0,.4));transform:translateZ(8px);position:relative;z-index:2}
  .lesson-info{flex:1;position:relative;z-index:2}
  .lesson-info h4{font-weight:700;font-size:17px;margin-bottom:3px}
  .lesson-info p{color:var(--muted);font-size:13px}
  .lesson-check{font-size:22px;transform:translateZ(8px);position:relative;z-index:2}

  /* ── Word Section ── */
  .word-section{max-width:720px;margin:0 auto;padding:30px 20px 70px;perspective:var(--perspective)}
  .lesson-top{text-align:center;margin-bottom:32px}
  .lesson-top .big-icon{font-size:56px;margin-bottom:10px;filter:drop-shadow(0 6px 16px rgba(0,0,0,.5));animation:iconFloat 3s ease-in-out infinite;display:inline-block}
  @keyframes iconFloat{0%,100%{transform:translateY(0) translateZ(20px)}50%{transform:translateY(-8px) translateZ(30px)}}
  .lesson-top h2{font-family:'Syne',sans-serif;font-size:1.9rem;font-weight:800;letter-spacing:-1px;margin-bottom:6px;text-shadow:0 3px 12px rgba(0,0,0,.4)}
  .lesson-top p{color:var(--muted);font-size:14px}

  /* ── Word Cards 3D ── */
  .word-card{
    border-radius:22px;padding:0;margin-bottom:18px;
    background:linear-gradient(170deg,rgba(255,255,255,.06) 0%,rgba(255,255,255,.015) 100%);
    border:1.5px solid var(--border);overflow:hidden;
    transition:all .35s cubic-bezier(.4,0,.2,1);
    transform-style:preserve-3d;transform:translateZ(0);
    box-shadow:var(--depth-sm);position:relative;
  }
  .word-card::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.05),transparent);border-radius:22px 22px 0 0;pointer-events:none;z-index:1}
  .word-card::after{content:'';position:absolute;inset:0;border-radius:22px;background:radial-gradient(400px circle at var(--mx,50%) var(--my,50%),rgba(255,255,255,.06),transparent 40%);pointer-events:none;z-index:1}
  .word-card.speaking{
    border-color:var(--c1);
    box-shadow:var(--depth-md),0 0 40px rgba(0,229,195,.15),0 0 80px rgba(0,229,195,.05);
    transform:translateZ(15px);
  }
  .word-card:hover{transform:translateZ(12px) translateY(-2px);box-shadow:var(--depth-md);border-color:rgba(255,255,255,.15)}
  .word-card-inner{padding:20px 24px;display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap;position:relative;z-index:2}
  .word-en{font-family:'Syne',sans-serif;font-size:24px;font-weight:800;letter-spacing:-.5px;text-shadow:0 2px 8px rgba(0,0,0,.3)}
  .word-es{color:var(--muted);font-size:14px;margin-top:3px}
  .word-actions{display:flex;align-items:center;gap:10px;flex-shrink:0}

  /* ── Phon Panel ── */
  .phon-panel{
    display:none;padding:14px 24px 18px;border-top:1px solid var(--border);
    background:linear-gradient(180deg,rgba(0,0,0,.3),rgba(0,0,0,.15));
    animation:slideDown .22s ease;position:relative;z-index:2;
    box-shadow:inset 0 4px 12px rgba(0,0,0,.3);
  }
  .phon-panel.open{display:block}
  @keyframes slideDown{from{opacity:0;transform:translateY(-6px)}to{opacity:1;transform:translateY(0)}}
  .phon-label{font-size:11px;color:var(--muted);font-weight:700;letter-spacing:1.5px;text-transform:uppercase;margin-bottom:6px}
  .phon-text{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;letter-spacing:1px;text-shadow:0 2px 8px rgba(0,229,195,.2)}
  .phon-hint{font-size:12px;color:var(--muted);margin-top:5px;line-height:1.5}

  /* ── Speak Buttons 3D ── */
  .speak-btn{
    padding:8px 16px;border-radius:12px;border:none;cursor:pointer;
    font-family:'DM Sans',sans-serif;font-weight:700;font-size:13px;
    display:inline-flex;align-items:center;gap:6px;
    transition:all .2s cubic-bezier(.4,0,.2,1);white-space:nowrap;text-decoration:none;text-align:center;
    transform:translateZ(5px);position:relative;overflow:hidden;
  }
  .speak-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.15),transparent);border-radius:12px 12px 0 0;pointer-events:none}
  .speak-btn:active{transform:translateZ(0) translateY(1px)}
  .speak-btn.primary{
    background:linear-gradient(135deg,var(--c1),#00b89c);color:#06080f;
    box-shadow:0 2px 0 #009980,0 4px 12px rgba(0,229,195,.3);
  }
  .speak-btn.primary:hover{transform:translateZ(8px) translateY(-1px);box-shadow:0 3px 0 #009980,0 8px 20px rgba(0,229,195,.4)}
  .speak-btn.primary:active{box-shadow:0 0 0 #009980,0 1px 4px rgba(0,229,195,.2)}
  .speak-btn.repeat{
    background:linear-gradient(180deg,rgba(255,255,255,.12),rgba(255,255,255,.06));color:#ddd;
    box-shadow:0 2px 0 rgba(0,0,0,.3),0 4px 10px rgba(0,0,0,.2);
  }
  .speak-btn.repeat:hover{transform:translateZ(8px) translateY(-1px);background:linear-gradient(180deg,rgba(255,255,255,.18),rgba(255,255,255,.1));box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px rgba(0,0,0,.25)}
  .speak-btn.mic{
    background:linear-gradient(180deg,rgba(255,107,109,.2),rgba(255,107,109,.1));
    border:1.5px solid rgba(255,107,109,.35);color:var(--c2);
    box-shadow:0 2px 0 rgba(0,0,0,.3),0 4px 10px rgba(255,107,109,.15);
  }
  .speak-btn.mic:hover{background:linear-gradient(180deg,rgba(255,107,109,.3),rgba(255,107,109,.15));transform:translateZ(8px) translateY(-1px);box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px rgba(255,107,109,.25)}
  .speak-btn.mic.listening{background:rgba(255,107,109,.3);animation:pulse .8s infinite}
  @keyframes pulse{0%,100%{box-shadow:0 0 0 0 rgba(255,107,109,.5),0 2px 0 rgba(0,0,0,.3)}50%{box-shadow:0 0 0 10px rgba(255,107,109,0),0 2px 0 rgba(0,0,0,.3)}}

  .mic-result{font-size:12px;padding:6px 12px;border-radius:8px;margin-top:8px;font-weight:700}
  .mic-result.correct{background:rgba(0,229,195,.15);color:var(--c1);box-shadow:inset 0 1px 3px rgba(0,229,195,.1)}
  .mic-result.wrong{background:rgba(255,107,109,.15);color:var(--c2);box-shadow:inset 0 1px 3px rgba(255,107,109,.1)}

  /* ── Tip Box 3D ── */
  .tip-box{
    border-radius:16px;padding:16px 20px;margin:10px 0 24px;font-size:14px;line-height:1.65;
    border:1px solid;background:rgba(255,193,7,.1);border-color:rgba(255,193,7,.3);
    box-shadow:inset 0 2px 8px rgba(255,193,7,.05),0 4px 16px rgba(0,0,0,.2);
    position:relative;overflow:hidden;
  }
  .tip-box::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.04),transparent);border-radius:16px 16px 0 0;pointer-events:none}

  /* ── Mark Done Button 3D ── */
  .mark-done-btn{
    width:100%;padding:15px;border-radius:18px;border:none;
    font-family:'DM Sans',sans-serif;font-weight:800;font-size:16px;cursor:pointer;
    transition:all .25s cubic-bezier(.4,0,.2,1);
    background:linear-gradient(135deg,var(--c1),#00b89c);color:#06080f;text-decoration:none;display:block;text-align:center;
    box-shadow:0 4px 0 #009980,0 8px 28px rgba(0,229,195,.3),0 2px 4px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.25);
    transform:translateZ(20px);position:relative;overflow:hidden;
  }
  .mark-done-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.3),transparent);border-radius:18px 18px 0 0;pointer-events:none}
  .mark-done-btn:hover{transform:translateZ(25px) translateY(-2px);box-shadow:0 6px 0 #009980,0 16px 40px rgba(0,229,195,.4),0 4px 8px rgba(0,0,0,.3),inset 0 1px 0 rgba(255,255,255,.3)}
  .mark-done-btn:active{transform:translateZ(8px) translateY(3px);box-shadow:0 1px 0 #009980,0 2px 8px rgba(0,229,195,.15),inset 0 2px 4px rgba(0,0,0,.1)}

  /* ── Games Section ── */
  .games-section{max-width:720px;margin:0 auto;padding:40px 20px 70px;perspective:var(--perspective)}
  .games-header{text-align:center;margin-bottom:30px}
  .games-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:18px}
  .game-card{
    background:linear-gradient(170deg,rgba(255,255,255,.06),rgba(255,255,255,.02));
    border:1.5px solid var(--border);border-radius:18px;padding:22px;text-align:center;cursor:pointer;
    transition:all .3s cubic-bezier(.4,0,.2,1);text-decoration:none;
    transform-style:preserve-3d;transform:translateZ(0);
    box-shadow:var(--depth-sm);position:relative;overflow:hidden;
  }
  .game-card::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.05),transparent);border-radius:18px 18px 0 0;pointer-events:none}
  .game-card::after{content:'';position:absolute;inset:0;border-radius:18px;background:radial-gradient(300px circle at var(--mx,50%) var(--my,50%),rgba(255,255,255,.07),transparent 40%);pointer-events:none}
  .game-card:hover{transform:translateZ(20px) translateY(-5px) scale(1.03);border-color:var(--c1);box-shadow:var(--depth-md),0 0 20px rgba(0,229,195,.1)}
  .game-icon{font-size:32px;margin-bottom:8px;filter:drop-shadow(0 3px 6px rgba(0,0,0,.4));transform:translateZ(8px);position:relative;z-index:2}
  .game-title{font-weight:700;font-size:14px;position:relative;z-index:2}

  /* ── Simulation ── */
  .sim-section{max-width:800px;margin:0 auto;padding:40px 20px 70px;perspective:var(--perspective)}
  .sim-header{text-align:center;margin-bottom:20px}
  .sim-container{
    background:linear-gradient(170deg,rgba(255,255,255,.04),rgba(255,255,255,.01));
    border-radius:22px;padding:25px;border:1px solid var(--border);min-height:400px;position:relative;overflow:hidden;
    box-shadow:var(--depth-md),inset 0 2px 0 rgba(255,255,255,.04);
  }
  .sim-container::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.03),transparent);border-radius:22px 22px 0 0;pointer-events:none}
  .sim-scene{width:100%;height:300px;background:rgba(0,0,0,.3);border-radius:14px;margin-bottom:20px;position:relative;box-shadow:inset 0 4px 16px rgba(0,0,0,.5),0 2px 0 rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.05);display:flex;align-items:center;justify-content:center;color:var(--muted);font-size:14px;text-align:center;padding:20px}
  .sim-controls{display:flex;gap:12px;justify-content:center;flex-wrap:wrap}
  .sim-btn{
    padding:10px 20px;border-radius:14px;border:none;
    background:linear-gradient(135deg,var(--c5),var(--c12));color:white;font-weight:700;cursor:pointer;text-decoration:none;
    box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px rgba(76,201,240,.25),inset 0 1px 0 rgba(255,255,255,.2);
    transform:translateZ(10px);position:relative;overflow:hidden;transition:all .2s;
  }
  .sim-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.2),transparent);border-radius:14px 14px 0 0;pointer-events:none}
  .sim-btn:hover{transform:translateZ(15px) translateY(-2px);box-shadow:0 4px 0 rgba(0,0,0,.3),0 10px 24px rgba(76,201,240,.35),inset 0 1px 0 rgba(255,255,255,.25)}
  .sim-btn:active{transform:translateZ(5px) translateY(1px);box-shadow:0 1px 0 rgba(0,0,0,.3),0 2px 6px rgba(76,201,240,.15)}

  /* ── Quiz Section ── */
  .quiz-section{max-width:620px;margin:0 auto;padding:48px 20px 70px;perspective:var(--perspective)}
  .quiz-section h2{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;letter-spacing:-1px;text-align:center;margin-bottom:6px;text-shadow:0 3px 12px rgba(0,0,0,.4)}
  .quiz-card{
    border-radius:24px;padding:36px;
    background:linear-gradient(170deg,rgba(255,255,255,.05),rgba(255,255,255,.02));
    border:1.5px solid var(--border);margin-top:32px;
    box-shadow:var(--depth-md);position:relative;overflow:hidden;
  }
  .quiz-card::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.04),transparent);border-radius:24px 24px 0 0;pointer-events:none}
  .quiz-q{font-family:'Syne',sans-serif;font-size:1.2rem;font-weight:700;margin:22px 0 26px;line-height:1.45;position:relative;z-index:2}
  .quiz-opt{
    padding:13px 20px;border-radius:14px;
    border:1.5px solid rgba(255,255,255,.1);
    background:linear-gradient(180deg,rgba(255,255,255,.06),rgba(255,255,255,.03));
    cursor:pointer;font-weight:600;font-size:15px;margin-bottom:10px;
    transition:all .25s cubic-bezier(.4,0,.2,1);text-align:left;width:100%;
    box-shadow:0 2px 0 rgba(0,0,0,.3),0 4px 10px rgba(0,0,0,.2),inset 0 1px 0 rgba(255,255,255,.05);
    transform:translateZ(5px);position:relative;overflow:hidden;
  }
  .quiz-opt::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.05),transparent);border-radius:14px 14px 0 0;pointer-events:none}
  .quiz-opt:hover:not(:disabled){
    background:linear-gradient(180deg,rgba(255,255,255,.1),rgba(255,255,255,.06));
    border-color:rgba(255,255,255,.22);
    transform:translateZ(10px) translateY(-1px);
    box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px rgba(0,0,0,.25),inset 0 1px 0 rgba(255,255,255,.08);
  }
  .quiz-opt:active:not(:disabled){transform:translateZ(0) translateY(1px);box-shadow:0 0 0 rgba(0,0,0,.3),0 1px 4px rgba(0,0,0,.2)}
  .quiz-opt.correct{background:linear-gradient(180deg,rgba(0,229,195,.25),rgba(0,229,195,.15));border-color:var(--c1);color:var(--c1);box-shadow:0 2px 0 rgba(0,0,0,.2),0 4px 16px rgba(0,229,195,.2)}
  .quiz-opt.wrong{background:linear-gradient(180deg,rgba(255,107,109,.25),rgba(255,107,109,.15));border-color:var(--c2);color:var(--c2);box-shadow:0 2px 0 rgba(0,0,0,.2),0 4px 16px rgba(255,107,109,.2)}
  .quiz-opt:disabled{cursor:default;transform:translateZ(0)}
  .quiz-result{text-align:center;padding:24px 0}
  .quiz-result .big-score{font-family:'Syne',sans-serif;font-size:3.5rem;font-weight:800;text-shadow:0 4px 20px rgba(0,0,0,.5)}
  .quiz-result p{color:var(--muted);font-size:15px;margin:10px 0 24px}
  .retry-btn{
    padding:12px 32px;border-radius:16px;border:none;
    background:linear-gradient(135deg,var(--c1),#00b89c);color:#06080f;font-weight:800;font-size:15px;cursor:pointer;text-decoration:none;display:inline-block;
    box-shadow:0 3px 0 #009980,0 6px 20px rgba(0,229,195,.3),inset 0 1px 0 rgba(255,255,255,.25);
    transform:translateZ(15px);position:relative;overflow:hidden;transition:all .2s;
  }
  .retry-btn::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.3),transparent);border-radius:16px 16px 0 0;pointer-events:none}
  .retry-btn:hover{transform:translateZ(20px) translateY(-2px);box-shadow:0 5px 0 #009980,0 12px 32px rgba(0,229,195,.4),inset 0 1px 0 rgba(255,255,255,.3)}
  .retry-btn:active{transform:translateZ(5px) translateY(2px);box-shadow:0 1px 0 #009980,0 2px 6px rgba(0,229,195,.15)}

  /* ── Level Tabs 3D ── */
  .level-tabs{display:flex;gap:8px;justify-content:center;margin-bottom:30px;flex-wrap:wrap}
  .level-tab{
    padding:8px 16px;border-radius:12px;border:none;
    background:linear-gradient(180deg,rgba(255,255,255,.07),rgba(255,255,255,.03));
    color:var(--text);cursor:pointer;transition:all .25s;text-decoration:none;
    box-shadow:0 2px 0 rgba(0,0,0,.3),0 4px 10px rgba(0,0,0,.2),inset 0 1px 0 rgba(255,255,255,.05);
    transform:translateZ(5px);position:relative;overflow:hidden;
  }
  .level-tab::before{content:'';position:absolute;top:0;left:0;right:0;height:45%;background:linear-gradient(180deg,rgba(255,255,255,.06),transparent);border-radius:12px 12px 0 0;pointer-events:none}
  .level-tab.active{background:linear-gradient(135deg,var(--c1),#00b89c);color:black;font-weight:700;box-shadow:0 3px 0 #009980,0 6px 16px rgba(0,229,195,.3),inset 0 1px 0 rgba(255,255,255,.25);transform:translateZ(12px) translateY(-1px)}
  .level-tab:hover:not(.active){transform:translateZ(8px) translateY(-1px);background:linear-gradient(180deg,rgba(255,255,255,.12),rgba(255,255,255,.06));box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px rgba(0,0,0,.25),inset 0 1px 0 rgba(255,255,255,.08)}

  /* ── Scrollbar 3D ── */
  ::-webkit-scrollbar{width:6px}
  ::-webkit-scrollbar-track{background:var(--bg);box-shadow:inset 0 0 6px rgba(0,0,0,.5)}
  ::-webkit-scrollbar-thumb{background:linear-gradient(180deg,var(--surface2),rgba(30,34,50,.9));border-radius:4px;box-shadow:0 0 4px rgba(0,0,0,.4)}

  /* ── Animación de entrada para cards ── */
  .card-enter{opacity:0;transform:translateZ(-40px) translateY(20px);transition:all .5s cubic-bezier(.4,0,.2,1)}
  .card-enter.visible{opacity:1;transform:translateZ(0) translateY(0)}
  </style>
</head>
<body>

<div class="englishup-main-container">
  <!-- Capas de fondo atmosférico 3D -->
  <div class="bg-depth-layers">
    <div class="bg-layer"></div>
    <div class="bg-layer"></div>
    <div class="bg-layer"></div>
  </div>
  <div id="particles"></div>

  <nav>
    <div class="logo">🇺🇸 EnglishUp</div>
    <div class="nav-tabs">
      <a class="nav-tab active" onclick="showScreen('home',this)">🏠 Inicio</a>
      <a class="nav-tab" onclick="showScreen('levels',this)">📚 Niveles</a>
      <a class="nav-tab" onclick="showScreen('quiz',this)">🧠 Quiz</a>
    </div>
  </nav>

  <div id="screen-home" class="screen active">
    <div class="hero">
      <div class="hero-tag">✨ Tu viaje empieza aquí</div>
      <h1>Habla Inglés<br/><span>con confianza</span></h1>
      <p>12 niveles progresivos con pronunciación real, repetición de audio, simulaciones reales y 5 juegos por nivel. De cero a conversaciones fluidas.</p>
      <div class="prog-wrap"><div class="prog-fill" id="home-prog" style="width:0%"></div></div>
      <p class="prog-label" id="home-prog-label">0 / 36 lecciones completadas</p>
      <a class="cta-btn" onclick="showScreen('levels',document.querySelectorAll('.nav-tab')[1])">🚀 Comenzar ahora</a>
    </div>
    <div class="feat-grid" id="feat-grid">
      <div class="feat-card card-enter"><div class="feat-icon">🔊</div><h3>Audio Real</h3><p>Escucha cada palabra con síntesis de voz nativa y repítela cuantas veces quieras.</p></div>
      <div class="feat-card card-enter"><div class="feat-icon">🎮</div><h3>5 Juegos x Nivel</h3><p>Memoria, unir palabras, completar frases, verdadero/falso y crucigramas divertidos.</p></div>
      <div class="feat-card card-enter"><div class="feat-icon">🚗</div><h3>Simulaciones Reales</h3><p>Conduce, pide comida, trabaja y viaja en escenarios interactivos 100% en inglés.</p></div>
      <div class="feat-card card-enter"><div class="feat-icon">📈</div><h3>12 Niveles</h3><p>Desde saludos básicos hasta debates y negocios internacionales.</p></div>
    </div>
  </div>

  <div id="screen-levels" class="screen">
    <div class="levels-header">
      <h2>Elige tu nivel</h2>
      <p>Cada nivel tiene: Lecciones + 5 Juegos + 1 Simulación Real</p>
    </div>
    <div class="levels-grid" id="levels-grid"></div>
  </div>

  <div id="screen-level-detail" class="screen">
    <div class="lesson-section">
      <a class="back-btn" onclick="showScreen('levels',document.querySelectorAll('.nav-tab')[1])">← Volver a niveles</a>
      
      <div class="levels-header" style="padding:20px 0">
        <div id="detail-badge" class="level-badge" style="margin:0 auto 15px"></div>
        <h2 id="detail-title" class="section-title"></h2>
        <p id="detail-subtitle" class="section-sub"></p>
      </div>

      <div class="level-tabs">
        <a class="level-tab active" onclick="showLevelTab('lessons', this)">📖 Lecciones</a>
        <a class="level-tab" onclick="showLevelTab('games', this)">🎮 5 Juegos</a>
        <a class="level-tab" onclick="showLevelTab('simulation', this)">🚀 Simulación</a>
      </div>

      <div id="tab-lessons" class="tab-content">
        <div id="lesson-list-rows"></div>
      </div>

      <div id="tab-games" class="tab-content" style="display:none">
        <div class="games-header">
          <h3>5 Juegos para practicar</h3>
          <p>Refuerza lo aprendido de forma divertida</p>
        </div>
        <div class="games-grid" id="games-grid"></div>
      </div>

      <div id="tab-simulation" class="tab-content" style="display:none">
        <div class="sim-header">
          <h3>🌍 Simulación del Nivel <span id="sim-level-num"></span></h3>
          <p id="sim-description"></p>
        </div>
        <div class="sim-container" id="sim-container">
          <div id="sim-content"></div>
        </div>
      </div>
    </div>
  </div>

  <div id="screen-word" class="screen">
    <div class="word-section">
      <a class="back-btn" id="word-back-btn">← Volver al nivel</a>
      <div class="lesson-top">
        <div class="big-icon" id="word-icon"></div>
        <h2 id="word-title"></h2>
        <p>Escucha 🔊 · Repite 🔁 · Habla 🎙️ · Verifica si lo dijiste bien</p>
      </div>
      <div id="word-cards"></div>
      <div class="tip-box" id="tip-box"></div>
      <a class="mark-done-btn" id="mark-done-btn">✅ Marcar lección completada</a>

      <div class="quiz-section" style="margin-top:50px;padding-top:30px;border-top:1px solid var(--border)">
        <h3 style="text-align:center;margin-bottom:20px;">📝 Mini Quiz de Refuerzo</h3>
        <div class="quiz-card" id="lesson-quiz-card"></div>
      </div>
    </div>
  </div>

  <div id="screen-quiz" class="screen">
    <div class="quiz-section">
      <div style="text-align:center;margin-bottom:4px;font-size:52px;filter:drop-shadow(0 6px 16px rgba(0,0,0,.5))">🧠</div>
      <h2>Quiz de Inglés</h2>
      <p style="text-align:center;color:var(--muted);font-size:14px">10 preguntas aleatorias de todos los niveles</p>
      <div class="quiz-card" id="quiz-card"></div>
    </div>
  </div>
</div>

<script>
const LEVELS = [
  {
    id:1, name:"Starter", emoji:"🌱", color:"#00e5c3",
    desc:"Primeras palabras esenciales",
    simTitle:"Saludos en la calle",
    simDesc:"Practica cómo saludar y despedirte correctamente con personas que encuentras en tu camino.",
    simType:"greetings",
    lessons:[
      { title:"Saludos y Despedidas", icon:"👋",
        words:[
          {en:"Hello",es:"Hola",ph:"HEH·loh",hint:"La 'H' es suave, casi silenciosa"},
          {en:"Goodbye",es:"Adiós",ph:"good·BAI",hint:"Énfasis en la segunda sílaba"},
          {en:"Good morning",es:"Buenos días",ph:"gud MOR·ning",hint:"'Morning' rima con 'corning'"},
          {en:"Good night",es:"Buenas noches",ph:"gud NAIT",hint:"'Night' suena como 'nait'"},
          {en:"See you later",es:"Hasta luego",ph:"sii yu LEI·ter",hint:"Fluye como una sola frase"},
        ],
        tip:"💡 Usa estos saludos con extranjeros que encuentres. La práctica real acelera el aprendizaje."
      },
      { title:"Educación Social", icon:"🙏",
        words:[
          {en:"Please",es:"Por favor",ph:"PLIIZ",hint:"Vocal larga, termina suave"},
          {en:"Thank you",es:"Gracias",ph:"ZANK·yu",hint:"'Th' como poner lengua entre dientes"},
          {en:"You're welcome",es:"De nada",ph:"yor WEL·kom",hint:"'You're' es contracción de 'you are'"},
          {en:"Excuse me",es:"Con permiso",ph:"ex·KIUZ·mi",hint:"Úsalo para abrirte paso"},
          {en:"Sorry",es:"Lo siento",ph:"SO·ri",hint:"'O' corta y directa"},
        ],
        tip:"💡 Estas palabras mágicas te abren puertas en cualquier país angloparlante."
      },
      { title:"Números 1–10", icon:"🔢",
        words:[
          {en:"One / Two",es:"Uno / Dos",ph:"WAN / TUU",hint:"'Two' tiene W muda"},
          {en:"Three / Four",es:"Tres / Cuatro",ph:"ZRII / FOR",hint:"'Three' empieza con 'th'"},
          {en:"Five / Six",es:"Cinco / Seis",ph:"FAIV / SIKS",hint:"'Five' termina en V sonora"},
          {en:"Seven / Eight",es:"Siete / Ocho",ph:"SEV·en / EIT",hint:"'Eight' suena como 'eit'"},
          {en:"Nine / Ten",es:"Nueve / Diez",ph:"NAIN / TEN",hint:"'Nine' rima con 'mine'"},
        ],
        tip:"💡 Cuenta objetos en inglés durante tu día. Escaleras, carros, pasos… ¡todo cuenta!"
      }
    ]
  },
  {
    id:2, name:"Explorer", emoji:"🗺️", color:"#ff5f6d",
    desc:"Frases del día a día",
    simTitle:"Presentaciones nuevas",
    simDesc:"Conoce a nuevas personas, preséntate y conoce sus nombres y países de origen.",
    simType:"introductions",
    lessons:[
      { title:"Presentaciones", icon:"🤝",
        words:[
          {en:"My name is…",es:"Mi nombre es…",ph:"mai NEIM iz",hint:"'Name' rima con 'game'"},
          {en:"I am from…",es:"Soy de…",ph:"ai am FROM",hint:"'From' con R suave americana"},
          {en:"Nice to meet you",es:"Mucho gusto",ph:"NAIS tu MIIT·yu",hint:"Fluye rápido y amigable"},
          {en:"How are you?",es:"¿Cómo estás?",ph:"hau AR·yu",hint:"Informal: 'How ya doin'?'"},
          {en:"I'm fine, thanks",es:"Estoy bien, gracias",ph:"aim FAIN·zanks",hint:"Contracción: I'm = I am"},
        ],
        tip:"💡 Practica con el espejo: salúdate a ti mismo en inglés cada mañana."
      },
      { title:"En el Restaurante", icon:"🍽️",
        words:[
          {en:"I'd like…",es:"Me gustaría…",ph:"aid·LAIK",hint:"Forma educada de pedir"},
          {en:"The bill, please",es:"La cuenta, por favor",ph:"de BIL PLIIZ",hint:"'Bill' en EE.UU., 'check' también"},
          {en:"Is it spicy?",es:"¿Es picante?",ph:"iz·it SPAI·si",hint:"'Spicy' con S inicial fuerte"},
          {en:"Water, please",es:"Agua, por favor",ph:"WO·ter PLIIZ",hint:"'Water' la T suena como D suave"},
          {en:"Delicious!",es:"¡Delicioso!",ph:"de·LI·shos",hint:"Énfasis en la segunda sílaba"},
        ],
        tip:"💡 La próxima vez que pidas comida a domicilio, practica en inglés mentalmente."
      },
      { title:"Preguntas Clave", icon:"❓",
        words:[
          {en:"Where is…?",es:"¿Dónde está…?",ph:"WER·iz",hint:"Imprescindible para orientarte"},
          {en:"How much is it?",es:"¿Cuánto cuesta?",ph:"hau MACH·iz·it",hint:"Esencial de compras"},
          {en:"What time is it?",es:"¿Qué hora es?",ph:"wot TAIM·iz·it",hint:"'Time' rima con 'crime'"},
          {en:"Can you help me?",es:"¿Me puede ayudar?",ph:"kan·yu HELP·mi",hint:"Muy útil con extraños"},
          {en:"I don't understand",es:"No entiendo",ph:"ai·dont·an·der·STAND",hint:"Sílaba final con énfasis"},
        ],
        tip:"💡 Memoriza estas 5 preguntas y sobrevives en cualquier ciudad del mundo."
      }
    ]
  }
];

let currentLevel, currentLessonIndex;

/* ── Partículas con profundidad 3D ── */
function initParticles(){
  const p = document.getElementById('particles');
  for(let i = 0; i < 35; i++){
    const pt = document.createElement('div');
    pt.className = 'pt';
    const size = Math.random() * 5 + 2;
    const depth = Math.random() * 300 - 150;
    pt.style.width = size + 'px';
    pt.style.height = size + 'px';
    pt.style.left = Math.random() * 100 + '%';
    pt.style.background = 'hsl(' + Math.random() * 360 + ',70%,50%)';
    pt.style.animationDuration = (Math.random() * 50 + 30) + 's';
    pt.style.animationDelay = (-Math.random() * 50) + 's';
    pt.style.transform = 'translateZ(' + depth + 'px)';
    pt.style.opacity = 0.05 + Math.random() * 0.15;
    p.appendChild(pt);
  }
}

/* ── Efecto tilt 3D con seguimiento del mouse ── */
function initTiltEffect(){
  document.addEventListener('mousemove', function(e){
    const cards = document.querySelectorAll('.feat-card, .level-card, .word-card, .lesson-row, .game-card, .quiz-opt');
    cards.forEach(function(card){
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      /* Solo aplicar si el mouse está cerca de la tarjeta */
      if(x > -80 && x < rect.width + 80 && y > -80 && y < rect.height + 80){
        const centerX = rect.width / 2;
        const centerY = rect.height / 2;
        const rotateX = ((y - centerY) / centerY) * -8;
        const rotateY = ((x - centerX) / centerX) * 8;
        card.style.setProperty('--mx', x + 'px');
        card.style.setProperty('--my', y + 'px');
        if(!card.matches(':active') && !card.classList.contains('speaking')){
          card.style.transform = 'translateZ(20px) translateY(-4px) rotateX(' + rotateX + 'deg) rotateY(' + rotateY + 'deg)';
        }
      } else {
        card.style.transform = '';
        card.style.setProperty('--mx', '50%');
        card.style.setProperty('--my', '50%');
      }
    });
  });
  /* Reset al salir del mouse de las tarjetas */
  document.addEventListener('mouseleave', function(){
    document.querySelectorAll('.feat-card, .level-card, .word-card, .lesson-row, .game-card, .quiz-opt').forEach(function(card){
      card.style.transform = '';
      card.style.setProperty('--mx', '50%');
      card.style.setProperty('--my', '50%');
    });
  });
}

/* ── Animación de entrada con IntersectionObserver ── */
function initScrollReveal(){
  const obs = new IntersectionObserver(function(entries){
    entries.forEach(function(entry){
      if(entry.isIntersecting){
        const parent = entry.target.parentElement;
        if(parent){
          const siblings = Array.from(parent.querySelectorAll('.card-enter'));
          const idx = siblings.indexOf(entry.target);
          setTimeout(function(){
            entry.target.classList.add('visible');
          }, idx * 120);
        } else {
          entry.target.classList.add('visible');
        }
      }
    });
  }, {threshold: 0.1});
  document.querySelectorAll('.card-enter:not(.visible)').forEach(function(el){obs.observe(el)});
}

function showScreen(id, btn){
  document.querySelectorAll('.screen').forEach(function(s){s.classList.remove('active')});
  document.getElementById('screen-' + id).classList.add('active');
  document.querySelectorAll('.nav-tab').forEach(function(b){b.classList.remove('active')});
  if(btn) btn.classList.add('active');
  /* Re-observar cards para animación de entrada */
  setTimeout(initScrollReveal, 50);
  /* Mostrar cards visibles inmediatamente */
  setTimeout(function(){
    document.querySelectorAll('.card-enter:not(.visible)').forEach(function(el){
      if(el.getBoundingClientRect().top < window.innerHeight){
        el.classList.add('visible');
      }
    });
  }, 100);
}

function renderLevels(){
  const g = document.getElementById('levels-grid');
  g.innerHTML = '';
  LEVELS.forEach(function(l){
    const c = document.createElement('div');
    c.className = 'level-card card-enter';
    c.style.borderColor = l.color;
    c.innerHTML = '<div class="specular"></div><div class="level-badge" style="background:' + l.color + '20;color:' + l.color + '">' + l.emoji + ' Nivel ' + l.id + '</div><h3>' + l.name + '</h3><p class="ldesc">' + l.desc + '</p><div class="dots">' + Array(5).fill('<div class="dot"></div>').join('') + '</div><div class="lcount">3 / 3 lecciones</div><a class="start-btn" style="background:' + l.color + ';color:#000;box-shadow:0 3px 0 rgba(0,0,0,.3),0 6px 16px ' + l.color + '44,inset 0 1px 0 rgba(255,255,255,.25)">Ver Nivel →</a>';
    c.onclick = function(){currentLevel = l; renderLevelDetail(); showScreen('level-detail')};
    g.appendChild(c);
  });
}

function renderLevelDetail(){
  document.getElementById('detail-badge').style.background = currentLevel.color + '20';
  document.getElementById('detail-badge').style.color = currentLevel.color;
  document.getElementById('detail-badge').innerHTML = currentLevel.emoji + ' Nivel ' + currentLevel.id;
  document.getElementById('detail-title').textContent = currentLevel.name;
  document.getElementById('detail-subtitle').textContent = currentLevel.desc;
  document.getElementById('sim-level-num').textContent = currentLevel.id;
  document.getElementById('sim-description').textContent = currentLevel.simDesc;

  /* Resetear a tab de lecciones */
  document.querySelectorAll('.level-tab').forEach(function(t){t.classList.remove('active')});
  document.querySelector('.level-tab').classList.add('active');
  document.querySelectorAll('.tab-content').forEach(function(t){t.style.display='none'});
  document.getElementById('tab-lessons').style.display='block';

  const r = document.getElementById('lesson-list-rows');
  r.innerHTML = '';
  currentLevel.lessons.forEach(function(les){
    const d = document.createElement('div');
    d.className = 'lesson-row card-enter';
    d.innerHTML = '<div class="lesson-icon">' + les.icon + '</div><div class="lesson-info"><h4>' + les.title + '</h4><p>Palabras y pronunciación</p></div><div class="lesson-check">➡️</div>';
    d.onclick = function(){currentLessonIndex = currentLevel.lessons.indexOf(les); renderLesson(les); showScreen('word')};
    r.appendChild(d);
  });

  /* Renderizar juegos de ejemplo */
  const gg = document.getElementById('games-grid');
  gg.innerHTML = '';
  var games = [{icon:'🧠',title:'Memoria'},{icon:'🔗',title:'Unir Parejas'},{icon:'✏️',title:'Completar'},{icon:'✅',title:'V/F'},{icon:'📝',title:'Crucigrama'}];
  games.forEach(function(gm){
    var gc = document.createElement('a');
    gc.className = 'game-card card-enter';
    gc.href = 'javascript:void(0)';
    gc.innerHTML = '<div class="game-icon">' + gm.icon + '</div><div class="game-title">' + gm.title + '</div>';
    gg.appendChild(gc);
  });

  /* Renderizar simulación de ejemplo */
  var sc = document.getElementById('sim-content');
  sc.innerHTML = '<div class="sim-scene"><div>🌍 <br><br>Escenario interactivo: <strong>' + currentLevel.simTitle + '</strong><br><small style="opacity:.6">La simulación se carga aquí</small></div></div><div class="sim-controls"><a class="sim-btn" href="javascript:void(0)">▶ Iniciar Simulación</a></div>';
}

function renderLesson(les){
  document.getElementById('word-icon').textContent = les.icon;
  document.getElementById('word-title').textContent = les.title;
  document.getElementById('tip-box').textContent = les.tip;
  const c = document.getElementById('word-cards');
  c.innerHTML = '';
  les.words.forEach(function(w){
    const card = document.createElement('div');
    card.className = 'word-card card-enter';
    const safeEn = w.en.replace(/'/g, "\\'");
    card.innerHTML = '<div class="word-card-inner"><div><div class="word-en">' + w.en + '</div><div class="word-es">' + w.es + '</div></div><div class="word-actions"><button class="speak-btn primary" onclick="event.stopPropagation();speak(\'' + safeEn + '\')">🔊 Escuchar</button><button class="speak-btn repeat" onclick="event.stopPropagation();speak(\'' + safeEn + '\')">🔁 Repetir</button></div></div><div class="phon-panel"><div class="phon-label">Pronunciación</div><div class="phon-text">/' + w.ph + '/</div><div class="phon-hint">' + w.hint + '</div></div>';
    card.onclick = function(e){
      if(e.target.closest('.speak-btn')) return;
      card.classList.toggle('speaking');
      var panel = card.querySelector('.phon-panel');
      panel.classList.toggle('open');
    };
    c.appendChild(card);
  });
}

function speak(text){
  const u = new SpeechSynthesisUtterance(text);
  u.lang = 'en-US';
  u.rate = 0.85;
  speechSynthesis.speak(u);
}

function showLevelTab(id, btn){
  document.querySelectorAll('.level-tab').forEach(function(t){t.classList.remove('active')});
  btn.classList.add('active');
  document.querySelectorAll('.tab-content').forEach(function(t){t.style.display = 'none'});
  document.getElementById('tab-' + id).style.display = 'block';
  setTimeout(initScrollReveal, 50);
}

document.getElementById('word-back-btn').onclick = function(){showScreen('level-detail')};

window.onload = function(){
  initParticles();
  renderLevels();
  initTiltEffect();
  setTimeout(initScrollReveal, 200);
};
</script>

</body>
</html>
