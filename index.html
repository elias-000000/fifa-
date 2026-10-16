<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Voetbal 5 tegen 5</title>
<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  background: #102330;
  color: white;
  font-family: Arial, sans-serif;
  text-align: center;
}
header { padding: 16px 10px 6px; }
h1 { margin: 0 0 10px; }
p { color: #c1d5df; line-height: 1.6; }
button {
  background: #c4ff69;
  color: #14252d;
  border: none;
  border-radius: 9px;
  padding: 11px 20px;
  font-size: 16px;
  cursor: pointer;
}
#score { font-size: 28px; margin: 12px; }
canvas {
  display: block;
  width: min(96vw, 1100px);
  margin: 15px auto;
  border: 3px solid #cce8dc;
  border-radius: 8px;
}
#melding { min-height: 26px; color: #c4ff69; }
</style>
</head>
<body>
<header>
  <h1>⚽ Voetbal 5 tegen 5</h1>
  <div id="score">Blauw 0 — 0 Rood</div>
  <button id="start">Aftrappen</button>
  <p>
    <b>Pijltjes / WASD:</b> bewegen ·
    <b>Spatie:</b> schieten ·
    <b>X:</b> passen ·
    <b>E:</b> speler wisselen ·
    <b>P:</b> pauze
  </p>
</header>
<canvas id="veld" width="1100" height="650"></canvas>
<p id="melding">Jij bent blauw. Scoor in het rechterdoel!</p>

<script>
const canvas = document.getElementById("veld");
const ctx = canvas.getContext("2d");
const melding = document.getElementById("melding");
const toetsen = new Set();

const LEFT = 35, RIGHT = 1065;
const TOP = 35, BOTTOM = 615;
const GOALTOP = 250, GOALBOTTOM = 400;

const basis = [
  [90,325],
  [320,190],
  [320,460],
  [510,250],
  [510,400]
];

const spelers = [];
for (let team = 0; team < 2; team++) {
  basis.forEach(([x,y], index) => {
    spelers.push({
      team,
      keeper: index === 0,
      nummer: index === 0 ? 1 : index + 6,
      x: team === 0 ? x : 1100-x,
      y,
      homeX: team === 0 ? x : 1100-x,
      homeY: y,
      dx: team === 0 ? 1 : -1,
      dy: 0,
      loopt: false,
      fase: index * 1.7,
      cooldown: 0,
      huid: ["#d69d72","#80543b","#e6b791",
             "#a46c48","#efc7a1"][index]
    });
  });
}

const bal = {x:550,y:325,vx:0,vy:0};
let actief = 3;
let scores = [0,0];
let gestart = false;
let pauze = false;
let laatsteTijd = 0;
let animatieTijd = 0;
let doelPauze = 0;

function afstand(a,b) {
  return Math.hypot(a.x-b.x,a.y-b.y);
}
function clamp(v,min,max) {
  return Math.max(min,Math.min(max,v));
}
function bericht(tekst) {
  melding.textContent = tekst;
}
function scoreTonen() {
  document.getElementById("score").textContent =
    `Blauw ${scores[0]} — ${scores[1]} Rood`;
}
function aftrap() {
  spelers.forEach(p => {
    p.x=p.homeX;
    p.y=p.homeY;
    p.dx=p.team===0?1:-1;
    p.dy=0;
    p.cooldown=0.5;
    p.loopt=false;
  });
  Object.assign(bal,{x:550,y:325,vx:0,vy:0});
}
function nieuweWedstrijd() {
  scores=[0,0];
  actief=3;
  gestart=true;
  pauze=false;
  doelPauze=0.6;
  toetsen.clear();
  aftrap();
  scoreTonen();
  bericht("Pak de bal! Jij scoort in het rechterdoel.");
  document.getElementById("start").textContent =
    "Nieuwe wedstrijd";
}
document.getElementById("start").onclick=nieuweWedstrijd;

function wissel() {
  const keuzes=spelers
    .map((p,i)=>({p,i}))
    .filter(o=>o.p.team===0&&!o.p.keeper&&o.i!==actief)
    .sort((a,b)=>afstand(a.p,bal)-afstand(b.p,bal));
  if(keuzes.length) actief=keuzes[0].i;
}
function trap(p,tx,ty,snelheid) {
  if(p.cooldown>0||afstand(p,bal)>43) return false;
  let dx=tx-bal.x,dy=ty-bal.y;
  let n=Math.hypot(dx,dy)||1;
  bal.vx=dx/n*snelheid;
  bal.vy=dy/n*snelheid;
  p.cooldown=0.42;
  return true;
}
function pass() {
  const p=spelers[actief];
  const opties=spelers.filter(q=>
    q.team===0&&!q.keeper&&q!==p
  );
  opties.sort((a,b)=>{
    const waarde=q=>
      afstand(p,q)-(q.x-p.x)*0.55;
    return waarde(a)-waarde(b);
  });
  if(opties[0]) trap(p,opties[0].x,opties[0].y,480);
}

window.addEventListener("keydown",e=>{
  if(["ArrowUp","ArrowDown","ArrowLeft",
      "ArrowRight","Space"].includes(e.code)) {
    e.preventDefault();
  }
  if(e.target.tagName==="BUTTON"&&
     ["Space","Enter"].includes(e.code)) return;

  toetsen.add(e.code);
  if(e.repeat||!gestart) return;

  if(e.code==="KeyP") {
    pauze=!pauze;
    bericht(pauze?"Gepauzeerd. Druk P om verder te spelen.":
      "Jij scoort in het rechterdoel!");
  }
  if(pauze||doelPauze>0) return;
  if(e.code==="KeyE") wissel();
  if(e.code==="KeyX") pass();
});
window.addEventListener("keyup",e=>toetsen.delete(e.code));
window.addEventListener("blur",()=>{
  toetsen.clear();
  if(gestart) {
    pauze=true;
    bericht("Gepauzeerd. Druk P om verder te spelen.");
  }
});

function beweeg(p,tx,ty,snelheid,dt) {
  let dx=tx-p.x,dy=ty-p.y;
  let n=Math.hypot(dx,dy);
  p.loopt=n>3;
  if(n<3) return;
  p.dx=dx/n;
  p.dy=dy/n;
  let stap=Math.min(n,snelheid*dt);
  p.x=clamp(p.x+p.dx*stap,LEFT+13,RIGHT-13);
  p.y=clamp(p.y+p.dy*stap,TOP+18,BOTTOM-13);
}

function update(dt) {
  if(!gestart||pauze) return;
  animatieTijd+=dt;
  if(doelPauze>0) {
    doelPauze-=dt;
    return;
  }
  spelers.forEach(p=>{
    p.cooldown=Math.max(0,p.cooldown-dt);
    p.loopt=false;
  });

  const jij=spelers[actief];
  const dx=Number(toetsen.has("ArrowRight")||
                  toetsen.has("KeyD"))-
           Number(toetsen.has("ArrowLeft")||
                  toetsen.has("KeyA"));
  const dy=Number(toetsen.has("ArrowDown")||
                  toetsen.has("KeyS"))-
           Number(toetsen.has("ArrowUp")||
                  toetsen.has("KeyW"));

  if(dx||dy) beweeg(jij,jij.x+dx*100,jij.y+dy*100,235,dt);

  const jagers=[0,1].map(team=>
    spelers.filter(p=>p.team===team&&!p.keeper)
      .sort((a,b)=>afstand(a,bal)-afstand(b,bal))[0]
  );

  spelers.forEach(p=>{
    if(p===jij) return;
    const teken=p.team===0?1:-1;

    if(p.keeper) {
      const dichtbij=p.team===0?bal.x<220:bal.x>880;
      beweeg(
        p,
        dichtbij?clamp(bal.x,p.homeX-30,p.homeX+30):p.homeX,
        clamp(bal.y,GOALTOP+10,GOALBOTTOM-10),
        190,dt
      );
    } else if(jagers[p.team]===p) {
      beweeg(p,bal.x-teken*15,bal.y,165,dt);
    } else {
      const steunX=p.homeX+(bal.x-550)*0.32;
      const steunY=p.homeY+(bal.y-325)*0.2;
      beweeg(p,clamp(steunX,170,930),steunY,140,dt);
    }
  });

  // Zorg dat spelers niet op elkaar blijven staan.
  for(let i=0;i<spelers.length;i++) {
    for(let j=i+1;j<spelers.length;j++) {
      let a=spelers[i],b=spelers[j];
      let dx=b.x-a.x,dy=b.y-a.y,n=Math.hypot(dx,dy);
      if(n<27) {
        if(n<0.01) {dx=1;dy=0;n=1;}
        const duw=(27-n)/2;
        a.x-=dx/n*duw;a.y-=dy/n*duw;
        b.x+=dx/n*duw;b.y+=dy/n*duw;
      }
    }
  }
  spelers.forEach(p=>{
    p.x=clamp(p.x,LEFT+13,RIGHT-13);
    p.y=clamp(p.y,TOP+18,BOTTOM-13);
  });

  // Schiet met spatie in de richting waarin je loopt.
  if(toetsen.has("Space")) {
    trap(jij,bal.x+jij.dx*300,bal.y+jij.dy*300,690);
  }

  // Automatische acties van teamgenoten en tegenstanders.
  spelers.forEach(p=>{
    if(p===jij||afstand(p,bal)>31||p.cooldown>0) return;
    const doelX=p.team===0?RIGHT+20:LEFT-20;
    if(p.keeper) {
      trap(p,p.team===0?650:450,325,540);
    } else {
      const doelY=325+(p.homeY<325?-35:35);
      trap(p,doelX,doelY,afstand(p,{x:doelX,y:325})<360
        ?580:340);
    }
  });

  // Balcontact: dribbelen en botsen.
  spelers.forEach(p=>{
    let dx=bal.x-p.x,dy=bal.y-p.y;
    let n=Math.hypot(dx,dy);
    if(n<23) {
      if(n<0.01) {dx=p.dx;dy=p.dy;n=1;}
      bal.x=p.x+dx/n*24;
      bal.y=p.y+dy/n*24;
      if(p===jij&&p.cooldown===0&&p.loopt) {
        bal.vx=p.dx*245;
        bal.vy=p.dy*245;
      } else {
        const naarSpeler=bal.vx*dx/n+bal.vy*dy/n;
        if(naarSpeler<0) {
          bal.vx-=1.6*naarSpeler*dx/n;
          bal.vy-=1.6*naarSpeler*dy/n;
        }
      }
    }
  });

  bal.x+=bal.vx*dt;
  bal.y+=bal.vy*dt;
  bal.vx*=Math.exp(-0.9*dt);
  bal.vy*=Math.exp(-0.9*dt);

  if(bal.y<TOP+8||bal.y>BOTTOM-8) {
    bal.y=clamp(bal.y,TOP+8,BOTTOM-8);
    bal.vy*=-0.75;
  }

  if(bal.x<LEFT+8||bal.x>RIGHT-8) {
    if(bal.y>GOALTOP+7&&bal.y<GOALBOTTOM-7) {
      const team=bal.x>RIGHT-8?0:1;
      scores[team]++;
      scoreTonen();
      bericht(team===0?"⚽ GOAL VOOR BLAUW!":
        "Goal voor rood. Pak hem terug!");
      aftrap();
      doelPauze=1.2;
    } else {
      bal.x=clamp(bal.x,LEFT+8,RIGHT-8);
      bal.vx*=-0.75;
    }
  }
}

function cirkel(x,y,r,kleur) {
  ctx.fillStyle=kleur;
  ctx.beginPath();
  ctx.arc(x,y,r,0,Math.PI*2);
  ctx.fill();
}
function lijn(x1,y1,x2,y2,kleur,dikte) {
  ctx.strokeStyle=kleur;
  ctx.lineWidth=dikte;
  ctx.beginPath();
  ctx.moveTo(x1,y1);
  ctx.lineTo(x2,y2);
  ctx.stroke();
}

function voetballer(p,index) {
  const stap=p.loopt?
    Math.sin(animatieTijd*15+p.fase)*6:0;
  const shirt=p.keeper?
    (p.team===0?"#f5c542":"#b78aff"):
    (p.team===0?"#2394ff":"#f34848");
  const broek=p.team===0?"#15375e":"#7e202c";

  ctx.save();
  ctx.translate(p.x,p.y);

  ctx.fillStyle="#0004";
  ctx.beginPath();
  ctx.ellipse(0,5,15,6,0,0,Math.PI*2);
  ctx.fill();

  ctx.lineCap="round";

  // Benen, sokken en schoenen.
  lijn(-5,-2,-6+stap,11,p.huid,6);
  lijn(5,-2,6-stap,11,p.huid,6);
  lijn(-6+stap,8,-6+stap,14,"#f4f5f7",5);
  lijn(6-stap,8,6-stap,14,"#f4f5f7",5);
  lijn(-6+stap,15,-3+stap,15,"#15202b",6);
  lijn(6-stap,15,9-stap,15,"#15202b",6);

  // Armen.
  lijn(-9,-23,-15,-10+stap*.5,p.huid,5);
  lijn(9,-23,15,-10-stap*.5,p.huid,5);

  // Shirt, mouwen en broek.
  ctx.fillStyle=shirt;
  ctx.fillRect(-9,-28,18,23);
  lijn(-8,-25,-12,-19,shirt,8);
  lijn(8,-25,12,-19,shirt,8);
  ctx.fillStyle=broek;
  ctx.fillRect(-9,-7,18,9);

  // Hoofd en haar.
  cirkel(0,-36,8,p.huid);
  ctx.fillStyle="#33271e";
  ctx.beginPath();
  ctx.arc(0,-38,8,Math.PI,Math.PI*2);
  ctx.fill();

  // Gezicht.
  cirkel(-2.5,-35,0.9,"#28231e");
  cirkel(2.5,-35,0.9,"#28231e");

  ctx.fillStyle="white";
  ctx.font="bold 11px Arial";
  ctx.textAlign="center";
  ctx.fillText(p.nummer,0,-13);

  if(index===actief) {
    ctx.fillStyle="#e5ff61";
    ctx.beginPath();
    ctx.moveTo(-7,-57);
    ctx.lineTo(7,-57);
    ctx.lineTo(0,-47);
    ctx.fill();
  }
  ctx.restore();
}

function tekenVeld() {
  ctx.fillStyle="#173d34";
  ctx.fillRect(0,0,1100,650);
  for(let i=0;i<10;i++) {
    ctx.fillStyle=i%2?"#2d8951":"#319458";
    ctx.fillRect(LEFT+i*103,TOP,103,BOTTOM-TOP);
  }

  ctx.strokeStyle="#d8f4dfbb";
  ctx.lineWidth=2;
  ctx.strokeRect(LEFT,TOP,RIGHT-LEFT,BOTTOM-TOP);
  lijn(550,TOP,550,BOTTOM,"#d8f4dfbb",2);
  ctx.beginPath();
  ctx.arc(550,325,78,0,Math.PI*2);
  ctx.stroke();
  cirkel(550,325,3,"#e4f5e8");

  ctx.strokeRect(LEFT,185,155,280);
  ctx.strokeRect(RIGHT-155,185,155,280);
  ctx.strokeRect(LEFT,255,55,140);
  ctx.strokeRect(RIGHT-55,255,55,140);

  [10,RIGHT].forEach(x=>{
    ctx.fillStyle="#ffffff33";
    ctx.fillRect(x,GOALTOP,25,GOALBOTTOM-GOALTOP);
    for(let y=GOALTOP;y<=GOALBOTTOM;y+=12) {
      lijn(x,y,x+25,y,"#ffffff55",1);
    }
    for(let xx=x;xx<=x+25;xx+=8) {
      lijn(xx,GOALTOP,xx,GOALBOTTOM,"#ffffff55",1);
    }
    ctx.strokeStyle="white";
    ctx.lineWidth=3;
    ctx.strokeRect(x,GOALTOP,25,GOALBOTTOM-GOALTOP);
  });
}

function teken() {
  tekenVeld();
  const volgorde=spelers.map((p,i)=>({p,i}))
    .sort((a,b)=>a.p.y-b.p.y);
  volgorde.forEach(o=>voetballer(o.p,o.i));

  cirkel(bal.x+2,bal.y+4,8,"#0004");
  cirkel(bal.x,bal.y,8,"#fff");
  cirkel(bal.x,bal.y,3,"#253039");

  if(!gestart||pauze) {
    ctx.fillStyle="#07172599";
    ctx.fillRect(0,0,1100,650);
    ctx.fillStyle="white";
    ctx.textAlign="center";
    ctx.font="bold 38px Arial";
    ctx.fillText(pauze?"PAUZE":"5 TEGEN 5",550,300);
    ctx.font="20px Arial";
    ctx.fillText(pauze?"Druk P om verder te spelen":
      "Klik op Aftrappen om te beginnen",550,340);
  }
}

function frame(tijd) {
  const dt=Math.min((tijd-laatsteTijd)/1000,0.03);
  laatsteTijd=tijd;
  update(dt);
  teken();
  requestAnimationFrame(frame);
}
aftrap();
requestAnimationFrame(frame);
</script>
</body>
</html>
