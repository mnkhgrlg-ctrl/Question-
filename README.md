# Question?
<!Mnkhgrls html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>

<style>
*{box-sizing:border-box}

body{
  margin:0;
  height:100vh;
  overflow:hidden;
  font-family:-apple-system, BlinkMacSystemFont, sans-serif;
  background:radial-gradient(circle at top,#1a0033,#000);
  color:white;
}

/* ===== STARS ===== */
.star{
  position:fixed;
  width:2px;
  height:2px;
  background:white;
  border-radius:50%;
  animation:twinkle linear infinite;
}
@keyframes twinkle{50%{opacity:.2}}

/* ===== CENTER ===== */
.center{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  text-align:center;
}

/* ===== GLASS ===== */
.glass{
  background:rgba(255,255,255,.08);
  backdrop-filter:blur(12px);
  padding:30px 40px;
  border-radius:18px;
  box-shadow:0 0 40px rgba(255,0,150,.25);
}

/* ===== LOCK ===== */
#lock{
  display:flex;
  flex-direction:column;
  gap:14px;
  align-items:center;
  animation:fadeIn 1.5s;
}

.hint{
  font-size:14px;
  color:#ff9ecf;
  opacity:.9;
}

#lock input{
  padding:12px;
  font-size:20px;
  border:none;
  border-radius:10px;
  outline:none;
  text-align:center;
  background:#00000080;
  color:white;
  letter-spacing:3px;
  width:180px;
}

#lock button{
  padding:10px 26px;
  border:none;
  border-radius:12px;
  font-size:16px;
  cursor:pointer;
  background:linear-gradient(45deg,#ff0055,#ff5cab);
  color:white;
  box-shadow:0 0 20px #ff3b7f;
  transition:.3s;
}

#lock button:hover{transform:scale(1.05)}

/* ===== BIG GIFT BOX ===== */
#gift{
  display:none;
  width:240px;
  height:170px;
  background:#c8002d;
  border-radius:16px;
  position:relative;
  cursor:pointer;
  box-shadow:0 25px 70px rgba(255,0,80,.7);
  animation:float 2.5s infinite ease-in-out, glow 2s infinite alternate;
}

#gift:before{
  content:"";
  position:absolute;
  width:40px;
  height:170px;
  background:#ffd1dc;
  left:100px;
}

#gift:after{
  content:"";
  position:absolute;
  width:240px;
  height:40px;
  background:#ffd1dc;
  top:65px;
}

#lid{
  width:260px;
  height:55px;
  background:#ff0033;
  position:absolute;
  top:-55px;
  left:-10px;
  border-radius:12px;
  transition:1s cubic-bezier(.19,1,.22,1);
}

/* ===== MAIN MESSAGE ===== */
#mainMsg{
  display:none;
  font-size:42px;
  font-weight:900;
  color:#ffd1ea;
  text-shadow:0 0 40px hotpink;
  animation:zoom 1.5s ease;
  margin-bottom:20px;
}

/* ===== LOVE TEXT ===== */
#loveBox{
  display:none;
  height:55vh;
  width:85vw;
  max-width:650px;
  overflow:hidden;
  font-size:22px;
  font-weight:700;
  color:#ffd1ea;
  text-shadow:0 0 20px pink;
}

.scroll{
  animation:scrollUp 28s linear infinite;
}

@keyframes scrollUp{
  from{transform:translateY(100%)}
  to{transform:translateY(-100%)}
}

/* ===== EFFECTS ===== */
@keyframes float{50%{transform:translateY(-14px)}}
@keyframes glow{
  from{box-shadow:0 0 30px #ff004c}
  to{box-shadow:0 0 80px #ff6aa2}
}
@keyframes fadeIn{
  from{opacity:0;transform:translateY(20px)}
  to{opacity:1}
}
@keyframes zoom{
  from{opacity:0;transform:scale(.4)}
  to{opacity:1;transform:scale(1)}
}

/* ===== FIREWORK ===== */
.boom{
  position:fixed;
  font-size:28px;
  pointer-events:none;
  animation:blast 3s ease-out forwards;
}

@keyframes blast{
  to{
    transform:translate(
      calc(-300px + 600px * var(--x)),
      calc(-300px + 600px * var(--y))
    ) scale(.2);
    opacity:0;
  }
}

/* ===== MOBILE ===== */
@media(max-width:600px){
  #mainMsg{font-size:30px}
  #loveBox{font-size:18px}
  #gift{width:210px;height:150px}
}

</style>
</head>

<body>

<div class="center">

<!-- PASSWORD -->
<div id="lock" class="glass">
  <div style="font-size:22px">🔐 Нууц үг оруул</div>
  <div class="hint">Hint: Tiim ❤️</div>
  <input id="code" placeholder="Энд бич">
  <button onclick="unlock()">Нээх 💖</button>
</div>

<!-- GIFT -->
<div id="gift">
  <div id="lid"></div>
</div>

<!-- MAIN LOVE MESSAGE -->
<div id="mainMsg">💗 Надтай үерхээч 💗</div>

<!-- LOVE WORDS -->
<div id="loveBox">
  <div class="scroll" id="loveText"></div>
</div>

</div>

<script>

/* ===== STARS ===== */
for(let i=0;i<150;i++){
  let s=document.createElement("div");
  s.className="star";
  s.style.left=Math.random()*100+"vw";
  s.style.top=Math.random()*100+"vh";
  s.style.animationDuration=2+Math.random()*4+"s";
  document.body.appendChild(s);
}

/* ===== PASSWORD ===== */
function unlock(){
  if(code.value==="Tiim"){
    lock.style.display="none";
    gift.style.display="block";
  }else{
    navigator.vibrate?.(200);
    alert("💔 Буруу нууц үг");
  }
}

/* ===== GIFT CLICK ===== */
let opened=false;

gift.onclick = () => {
  if(opened) return;
  opened = true;

  // lid эргэх animation
  lid.style.transform = "rotateX(160deg) translateY(-110px)";

  // gift-ийг lid animation дууссаны дараа алга болгох
  setTimeout(() => { gift.style.display = "none"; }, 1000);

  // FIREWORK
  for(let i=0; i<90; i++){
    explode("❤️");
    explode("✨");
  }

  // SHOW MAIN TEXT
  setTimeout(() => { mainMsg.style.display = "block"; }, 600);

  // SHOW LOVE WORDS
  setTimeout(() => { loveBox.style.display = "block"; }, 2000);
};

/* ===== FIREWORK FUNCTION ===== */
function explode(t){
  const e=document.createElement("div");
  e.className="boom";
  e.innerHTML=t;
  e.style.left=innerWidth/2+"px";
  e.style.top=innerHeight/2+"px";
  e.style.setProperty("--x",Math.random());
  e.style.setProperty("--y",Math.random());
  document.body.appendChild(e);
  setTimeout(()=>e.remove(),3000);
}

/* ===== LOVE WORDS ===== */
const words=[
  "I love you ❤️","Forever mine 💖","You are my world 🌎",
  "My heart is yours 💕","Only you 😘","My sunshine ☀️",
  "My angel 😇","My baby 💗","Endless love ♾️",
  "Always together 💞","My everything 💘",
  "I choose you everyday ❤️","Soulmate 💍","My happiness 🥰"
];

let textHTML="";
for(let i=0;i<35;i++){
  textHTML+=words[Math.floor(Math.random()*words.length)]+"<br><br>";
}
loveText.innerHTML=textHTML;

</script>

</body>
</html>
