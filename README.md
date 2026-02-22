<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Surprise site</title>

<style>
body{
    margin:0;
    overflow:hidden;
    background:black;
    color:#00ff00;
    font-family: monospace;
}

canvas{
    position:fixed;
    top:0;
    left:0;
    z-index:-1;
}

.center{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%);
    text-align:center;
}

#loading{
    font-size:40px;
}

button{
    padding:15px 30px;
    font-size:20px;
    background:red;
    color:white;
    border:none;
    cursor:pointer;
    margin-top:20px;
    position:absolute;
}

#final{
    display:none;
    font-size:30px;
    margin-top:20px;
}

/* SCREEN SHAKE */
.shake{
    animation: shake 0.1s infinite;
}
@keyframes shake{
    0%{transform:translate(2px,2px);}
    25%{transform:translate(-2px,2px);}
    50%{transform:translate(-2px,-2px);}
    75%{transform:translate(2px,-2px);}
    100%{transform:translate(2px,-2px);}
}

/* POPUP STYLE */
.popup{
    position:fixed;
    background:white;
    color:black;
    padding:20px;
    border:3px solid red;
    font-weight:bold;
    z-index:9999;
}
</style>
</head>
<body>

<canvas id="matrix"></canvas>

<div class="center">
    <div id="loading">Surprise 0%</div>
    <button id="runBtn">Энд дараарай бойс</button>
    <div id="final">💀 Za ingd utas cn mnih bollodo 💀</div>
</div>

<!-- Hacker voice -->
<audio id="voice">
<source src="https://www.soundjay.com/human/evil-laugh-1.mp3" type="audio/mpeg">
</audio>

<script>
/* MATRIX EFFECT */
const canvas = document.getElementById("matrix");
const ctx = canvas.getContext("2d");
canvas.height = window.innerHeight;
canvas.width = window.innerWidth;

const letters = "01ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const fontSize = 16;
const columns = canvas.width / fontSize;
const drops = [];

for(let x = 0; x < columns; x++) drops[x] = 1;

function draw(){
    ctx.fillStyle = "rgba(0,0,0,0.05)";
    ctx.fillRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle = "#0F0";
    ctx.font = fontSize+"px monospace";
    for(let i=0;i<drops.length;i++){
        const text = letters.charAt(Math.random()*letters.length);
        ctx.fillText(text,i*fontSize,drops[i]*fontSize);
        if(drops[i]*fontSize>canvas.height && Math.random()>0.975)
            drops[i]=0;
        drops[i]++;
    }
}
setInterval(draw,33);

/* FAKE LOADING */
let percent=0;
const loading=document.getElementById("loading");
const final=document.getElementById("final");
const voice=document.getElementById("voice");

const fake=setInterval(()=>{
    percent++;
    loading.innerText="System Breach "+percent+"%";
    if(percent===30){
        document.body.classList.add("shake"); // screen shake
    }
    if(percent===60){
        webcamFake();
    }
    if(percent>=100){
        clearInterval(fake);
        loading.innerText="ACCESS GRANTED";
        final.style.display="block";
        voice.play();
        popupSpam();
    }
},80);

/* RUNAWAY BUTTON */
const btn=document.getElementById("runBtn");
btn.addEventListener("mouseover",()=>{
    btn.style.left=Math.random()*(window.innerWidth-100)+"px";
    btn.style.top=Math.random()*(window.innerHeight-50)+"px";
});

/* FULLSCREEN */
document.addEventListener("click",()=>{
    if(!document.fullscreenElement){
        document.documentElement.requestFullscreen().catch(()=>{});
    }
});

/* FAKE WEBCAM ACCESS */
function webcamFake(){
    const cam=document.createElement("div");
    cam.style.position="fixed";
    cam.style.top="20px";
    cam.style.right="20px";
    cam.style.width="200px";
    cam.style.height="150px";
    cam.style.background="black";
    cam.style.border="3px solid lime";
    cam.style.color="lime";
    cam.style.display="flex";
    cam.style.alignItems="center";
    cam.style.justifyContent="center";
    cam.innerText="📷 WEBCAM ACTIVE";
    document.body.appendChild(cam);
}

/* VIRUS POPUP SPAM */
function popupSpam(){
    setInterval(()=>{
        const pop=document.createElement("div");
        pop.className="popup";
        pop.style.top=Math.random()*window.innerHeight+"px";
        pop.style.left=Math.random()*window.innerWidth+"px";
        pop.innerText="⚠ Utasruucn ortsn geel bod ⚠";
        document.body.appendChild(pop);
    },500);
}
</script>

</body>
</html>
