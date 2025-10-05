<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Missão do Bem com Martina & José</title>
<style>
  :root{--bg:#dff0ff;--card:#fffef8;--accent:#ffd66b;--text:#263238}
  html,body{height:100%;margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;color:var(--text)}
  .game{display:flex;flex-direction:column;align-items:center;justify-content:flex-start;height:100%;padding:16px;box-sizing:border-box;background:linear-gradient(180deg,var(--bg),#f7fbff)}
  header{width:100%;max-width:900px;margin-bottom:8px}
  h1{margin:0;font-size:20px}
  .scene{width:100%;max-width:900px;background:var(--card);border-radius:12px;box-shadow:0 6px 18px rgba(20,30,40,0.12);overflow:hidden;padding:0;position:relative}
  .playarea{width:100%;height:540px;background:linear-gradient(#f7faff,#fff);position:relative;display:block}
  .hud{position:absolute;left:12px;top:12px;background:rgba(255,255,255,0.9);padding:8px 10px;border-radius:8px;font-weight:600}
  .dialog{position:absolute;right:12px;top:12px;background:rgba(255,255,255,0.95);padding:10px;border-radius:8px;max-width:320px}
  button{background:var(--accent);border:0;padding:8px 12px;border-radius:8px;font-weight:700;cursor:pointer}
  svg{user-select:none;-webkit-user-select:none}
  .toy{cursor:pointer;touch-action:manipulation}
  .ui-bottom{display:flex;gap:8px;align-items:center;justify-content:space-between;padding:12px}
  .center{display:flex;gap:8px;align-items:center}
  .hidden{display:none}
  .victory{position:absolute;inset:0;background:rgba(0,0,0,0.45);display:flex;align-items:center;justify-content:center}
  .victory-card{background:var(--card);padding:24px;border-radius:12px;text-align:center;max-width:80%}
  .small{font-size:13px;color:#555}
  @media(max-width:520px){.playarea{height:460px}}
</style>
</head>
<body>
<div class="game">
  <header>
    <h1>Missão do Bem com Martina & José</h1>
  </header>

  <div class="scene" role="application" aria-label="Cena: sala de estar">
    <div class="playarea" id="playarea">
      <div class="hud" id="hud">Guardados: <span id="count">0</span>/4</div>
      <div class="dialog" id="dialog">Mamãe: Oi, meus amores! Vamos deixar a sala bem arrumadinha?</div>

      <!-- SVG background + objects -->
      <svg id="svg" viewBox="0 0 900 540" preserveAspectRatio="xMidYMid meet" style="width:100%;height:100%;display:block">
        <!-- Background room -->
        <rect x="0" y="0" width="900" height="540" fill="#eaf8ff"/>
        <rect x="40" y="380" width="820" height="140" rx="12" fill="#f5e9d8"/>
        <!-- Window -->
        <rect x="620" y="40" width="220" height="120" rx="6" fill="#bde7ff"/>
        <path d="M620 40c0 0 30 30 110 30s110-30 110-30" fill="none" stroke="#ffd66b" stroke-width="6" stroke-linecap="round"/>
        <!-- Sofa -->
        <rect x="60" y="300" width="300" height="90" rx="18" fill="#9ad0ff"/>
        <!-- Toy box -->
        <g id="box" transform="translate(720,370)">
          <rect x="-10" y="-10" width="160" height="110" rx="8" fill="#cfa06b" stroke="#8b5e3a" stroke-width="4"/>
          <rect x="-10" y="-10" width="160" height="30" rx="8" fill="#e7caa0"/>
        </g>

        <!-- Mamãe (static) -->
        <g id="mamae" transform="translate(420,320)">
          <circle cx="0" cy="-60" r="28" fill="#f9d9d0"/>
          <rect x="-24" y="-40" width="48" height="80" rx="10" fill="#ffc0cb"/>
        </g>

        <!-- Martina -->
        <g id="martina" transform="translate(240,340)">
          <circle cx="0" cy="-30" r="18" fill="#f9d9d0"/>
          <rect x="-14" y="-12" width="28" height="44" rx="8" fill="#fff06b"/>
        </g>

        <!-- Jose -->
        <g id="jose" transform="translate(340,350)">
          <circle cx="0" cy="-28" r="18" fill="#f9d9d0"/>
          <rect x="-14" y="-8" width="28" height="40" rx="8" fill="#ff7b7b"/>
        </g>

        <!-- Fiel (dog) -->
        <g id="fiel" transform="translate(160,370)">
          <ellipse cx="0" cy="0" rx="26" ry="16" fill="#d69a5b"/>
          <circle cx="-12" cy="-8" r="8" fill="#d69a5b"/>
        </g>

        <!-- Toys -->
        <g id="toys">
          <!-- Carrinho -->
          <g id="carrinho" class="toy" transform="translate(120,420)" data-name="Carrinho">
            <rect x="-24" y="-12" width="48" height="24" rx="6" fill="#ff5a5a"/>
            <circle cx="-16" cy="14" r="6" fill="#111"/>
            <circle cx="16" cy="14" r="6" fill="#111"/>
          </g>
          <!-- Boneca -->
          <g id="boneca" class="toy" transform="translate(520,430)" data-name="Boneca">
            <circle cx="0" cy="-12" r="10" fill="#fde2e2"/>
            <rect x="-12" y="-2" width="24" height="28" rx="6" fill="#ffd0f0"/>
          </g>
          <!-- Livro -->
          <g id="livro" class="toy" transform="translate(220,430)" data-name="Livro">
            <rect x="-20" y="-12" width="40" height="26" rx="4" fill="#7fc3ff"/>
            <rect x="-14" y="-6" width="28" height="14" fill="#fff" />
          </g>
          <!-- Bola -->
          <g id="bola" class="toy" transform="translate(420,420)" data-name="Bola">
            <circle cx="0" cy="0" r="16" fill="#ffd700" stroke="#ff5a5a" stroke-width="4"/>
          </g>
        </g>

        <!-- Floating text target (for accessibility) -->
        <text id="targetHint" x="720" y="360" font-size="14" fill="#222" text-anchor="middle" visibility="hidden">Caixa</text>
      </svg>
    </div>

    <div class="ui-bottom" style="width:100%;max-width:900px;">
      <div class="center">
        <button id="narrationBtn">Ouvir diálogo</button>
        <button id="resetBtn">Recomeçar</button>
      </div>
      <div class="small">Toque ou clique nos brinquedos para guardá-los</div>
    </div>

    <div class="victory hidden" id="victory">
      <div class="victory-card">
        <h2>Parabéns!</h2>
        <p>Vocês ajudaram a mamãe a arrumar a sala.</p>
        <div style="margin-top:12px">
          <button id="playAgain">Jogar de novo</button>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
/* Jogo funcional sem dependências externas.
   - Clique/Toque nos elementos com classe toy para movê-los à caixa.
   - Contador de itens guardados. Vitória ao guardar 4.
   - Narração sintetizada via WebAudio (voz robótica simples).
*/

const toys = Array.from(document.querySelectorAll('.toy'));
const box = document.getElementById('box');
const countEl = document.getElementById('count');
const victory = document.getElementById('victory');
const dialogEl = document.getElementById('dialog');
let stored = 0;
let audioCtx = null;

// Função utilitária para obter coordenadas do elemento SVG
function getTransformXY(el) {
  const tr = el.getAttribute('transform') || '';
  const m = /translate\(([-0-9.]+),\s*([-0-9.]+)\)/.exec(tr);
  return m ? [parseFloat(m[1]), parseFloat(m[2])] : [0,0];
}
function setTransformXY(el,x,y){ el.setAttribute('transform',`translate(${x},${y})`); }

// Caixa coords
const boxXY = getTransformXY(box);

// Som sintetizado simples
function ensureAudio() {
  if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
}
function playBeep(freq=440, time=0.12, type='sine', gain=0.12){
  ensureAudio();
  const o = audioCtx.createOscillator();
  const g = audioCtx.createGain();
  o.type = type;
  o.frequency.value = freq;
  g.gain.value = gain;
  o.connect(g); g.connect(audioCtx.destination);
  o.start();
  o.stop(audioCtx.currentTime + time);
}
function playPickup(){ playBeep(880,0.08,'sine',0.08); playBeep(1320,0.06,'square',0.06); }
function playWin(){ playBeep(660,0.12,'sine',0.14); playBeep(880,0.12,'sine',0.12); }

// Move toy with smooth animation then hide
function moveToBox(toy){
  if (toy.dataset.stored === '1') return;
  toy.dataset.stored = '1';
  const [sx,sy] = getTransformXY(toy);
  const [tx,ty] = boxXY;
  const steps = 18;
  let i = 0;
  const dx = (tx - sx) / steps;
  const dy = (ty - sy) / steps;
  const id = setInterval(()=>{
    i++;
    setTransformXY(toy, sx + dx * i, sy + dy * i);
    toy.style.opacity = 1 - i/steps*0.6;
    if (i>=steps){
      clearInterval(id);
      toy.style.visibility = 'hidden';
      stored++;
      countEl.textContent = stored;
      playPickup();
      checkVictory();
    }
  },16);
}

// Victory check
function checkVictory(){
  if (stored >= 4){
    setTimeout(()=>{ playWin(); victory.classList.remove('hidden'); }, 300);
  }
}

// Click/touch binding
toys.forEach(t=>{
  t.addEventListener('click',()=> moveToBox(t));
  let startX=0,startY=0,dragging=false;
  t.addEventListener('pointerdown', (e)=>{
    if (t.dataset.stored==='1') return;
    dragging=true;
    startX = e.clientX; startY = e.clientY;
    t.setPointerCapture(e.pointerId);
  });
  t.addEventListener('pointermove',(e)=>{
    if(!dragging) return;
    const rect = document.getElementById('svg').getBoundingClientRect();
    const sx = e.clientX - rect.left;
    const sy = e.clientY - rect.top;
    // map to svg coords (viewBox 900x540)
    const x = sx / rect.width * 900;
    const y = sy / rect.height * 540;
    setTransformXY(t, x, y);
  });
  t.addEventListener('pointerup',(e)=>{
    if(!dragging) return;
    dragging=false;
    const [x,y] = getTransformXY(t);
    // distance to box
    const dx = x - boxXY[0];
    const dy = y - boxXY[1];
    const dist = Math.hypot(dx,dy);
    if (dist < 80) moveToBox(t);
  });
});

// Narration using simple speech synthesis fallback
document.getElementById('narrationBtn').addEventListener('click',()=>{
  const lines = [
    "Mamãe: Oi, meus amores! Vamos deixar a sala bem arrumadinha?",
    "José: Claro, mamãe! Eu pego o carrinho!",
    "Martina: Eu guardo a boneca!"
  ];
  // prefer Web Speech API if available
  if ('speechSynthesis' in window){
    speechSynthesis.cancel();
    lines.forEach((l,i)=>{
      const u = new SpeechSynthesisUtterance(l);
      u.rate = 0.95;
      u.pitch = 1.05;
      u.lang = 'pt-BR';
      setTimeout(()=>speechSynthesis.speak(u), i*1400);
    });
  } else {
    // fallback: simple beep sequence
    playBeep(440,0.12,'sine',0.08);
    setTimeout(()=>playBeep(550,0.12,'sine',0.08),400);
    setTimeout(()=>playBeep(660,0.12,'sine',0.08),800);
  }
});

// Reset and play again
function resetGame(){
  stored = 0;
  countEl.textContent = stored;
  victory.classList.add('hidden');
  toys.forEach((t,i)=>{
    t.style.visibility = 'visible';
    t.style.opacity = 1;
    t.dataset.stored = '0';
    // reset positions to initial layout
    const pos = [{x:120,y:420},{x:520,y:430},{x:220,y:430},{x:420,y:420}][i];
    setTransformXY(t,pos.x,pos.y);
  });
}
document.getElementById('resetBtn').addEventListener('click', resetGame);
document.getElementById('playAgain').addEventListener('click', resetGame);

// Initial small blink for dialog then hide
setTimeout(()=>dialogEl.textContent = "Mamãe: Oi, meus amores! Vamos deixar a sala bem arrumadinha?", 300);
setTimeout(()=>dialogEl.style.display='none', 6000);

</script>
</body>
</html>
