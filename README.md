<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Valentine?</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  height: 100vh;
  background: radial-gradient(circle at top, #ffb6c1, #ff6f91);
  font-family: 'Pacifico', cursive;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  text-align: center;
}

h1 {
  color: #b30000;
  font-size: 3.2em;
  text-shadow: 2px 2px 12px rgba(255,255,255,0.8);
}

.buttons {
  position: relative;
  width: 420px;
  height: 260px;
}

button {
  position: absolute;
  font-size: 1.4em;
  padding: 14px 38px;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  font-family: 'Pacifico', cursive;
}

#yes {
  background: #ff2f6e;
  color: white;
  left: 140px;
  top: 120px;
  box-shadow: 0 0 30px rgba(255,47,110,.9);
  animation: pulse 1.3s infinite;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.18); }
  100% { transform: scale(1); }
}

#no {
  background: #444;
  color: white;
  left: 280px;
  top: 40px;
}

#message {
  display: none;
  font-size: 2.3em;
  color: white;
  margin-top: 25px;
  text-shadow: 2px 2px 10px rgba(0,0,0,.4);
}

img {
  display: none;
  max-width: 75%;
  margin-top: 30px;
  border-radius: 22px;
  box-shadow: 0 0 40px rgba(255,255,255,.9);
}

.heart, .confetti {
  position: absolute;
  pointer-events: none;
}

.heart {
  font-size: 20px;
  animation: floatUp 6s linear forwards;
}

@keyframes floatUp {
  from { transform: translateY(100vh); opacity: 1; }
  to { transform: translateY(-15vh); opacity: 0; }
}

.confetti {
  width: 10px;
  height: 10px;
  animation: fall 3s linear forwards;
}

@keyframes fall {
  to {
    transform: translateY(120vh) rotate(900deg);
    opacity: 0;
  }
}
</style>
</head>

<body>

<h1 id="title">Leonie, will you be my valentine? 💘</h1>

<div class="buttons">
  <button id="yes" onclick="yesClicked()">Yes 💖</button>
  <button id="no" onmouseover="noPanic()">No 🙃</button>
</div>

<div id="message">YAY 💕 I knew you’d say yes 💖✨</div>
<img id="photo" src="your-image.jpg">

<audio id="music" loop>
  <source src="romantic-music.mp3" type="audio/mpeg">
</audio>

<script>
let chaos = 0;
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");

// YES smoothly follows cursor without disappearing
let yesX = window.innerWidth / 2 - yesBtn.offsetWidth/2;
let yesY = window.innerHeight / 2 - yesBtn.offsetHeight/2;
yesBtn.style.left = yesX + "px";
yesBtn.style.top = yesY + "px";

document.addEventListener("mousemove", e => {
  const targetX = e.clientX - yesBtn.offsetWidth/2;
  const targetY = e.clientY - yesBtn.offsetHeight/2;
  yesX += (targetX - yesX) * 0.08; // smoothing factor
  yesY += (targetY - yesY) * 0.08;
  yesBtn.style.left = yesX + "px";
  yesBtn.style.top = yesY + "px";
});


// NO panics → spins → disappears
function noPanic() {
  chaos++;
  if (chaos > 7) {
    noBtn.style.display = "none";
    return;
  }
  noBtn.style.left = Math.random()*(window.innerWidth-100)+"px";
  noBtn.style.top  = Math.random()*(window.innerHeight-60)+"px";
  noBtn.style.transform = `rotate(${Math.random()*chaos*50}deg)`;
}

// YES clicked
function yesClicked() {
  document.getElementById("title").style.display = "none";
  document.querySelector(".buttons").style.display = "none";
  document.getElementById("message").style.display = "block";
  document.getElementById("photo").style.display = "block";
  document.getElementById("music").play();
  hearts();
  fireworks();
}

// hearts forever
function hearts() {
  setInterval(() => {
    const h = document.createElement("div");
    h.className = "heart";
    h.innerHTML = "❤️";
    h.style.left = Math.random()*100+"vw";
    h.style.fontSize = Math.random()*25+15+"px";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),6000);
  }, 250);
}

// confetti fireworks
function fireworks() {
  for (let i=0;i<180;i++) {
    const c = document.createElement("div");
    c.className = "confetti";
    c.style.background = `hsl(${Math.random()*360},100%,70%)`;
    c.style.left = Math.random()*100+"vw";
    c.style.top = "-10px";
    document.body.appendChild(c);
    setTimeout(()=>c.remove(),3000);
  }
}
</script>

</body>
</html>

