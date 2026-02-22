<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Surprise</title>

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
</style>
</head>
<body>

<canvas id="matrix"></canvas>

<div class="center">
    <div id="loading">Surprise 0%</div>
    <button id="runBtn">SURPRISE</button>
    <div id="final">Мангар сэвтэй байгаааздээ</div>
</div>

<audio id="beep">
<source src="https://www.soundjay.com/button/beep-07.wav" type="audio/wav">
</audio>

<script>
/* MATRIX EFFECT */
const canvas = document.getElementById("matrix");
const ctx = canvas.getContext("2d");

canvas.height = window.innerHeight;
canvas.width = window.innerWidth;

const letters = "アカサタナハマヤラワ0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const fontSize = 16;
const columns = canvas.width / fontSize;
const drops = [];

for(let x = 0; x < columns; x++)
    drops[x] = 1;

function draw(){
    ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = "#0F0";
    ctx.font = fontSize + "px monospace";

    for(let i = 0; i < drops.length; i++){
        const text = letters.charAt(Math.floor(Math.random()*letters.length));
        ctx.fillText(text, i*fontSize, drops[i]*fontSize);

        if(drops[i]*fontSize > canvas.height && Math.random() > 0.975)
            drops[i] = 0;

        drops[i]++;
    }
}
setInterval(draw, 33);

/* FAKE LOADING */
let percent = 0;
const loadingText = document.getElementById("loading");
const finalText = document.getElementById("final");
const beep = document.getElementById("beep");

const fakeLoad = setInterval(()=>{
    percent++;
    loadingText.innerText = "System Breach " + percent + "%";
    beep.play();

    if(percent >= 100){
        clearInterval(fakeLoad);
        loadingText.innerText = "DEVICE COMPROMISED";
        document.body.style.background = "darkred";
        finalText.style.display = "block";
    }
}, 80);

/* RUNAWAY BUTTON */
const btn = document.getElementById("runBtn");

btn.addEventListener("mouseover", ()=>{
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);
    btn.style.left = x + "px";
    btn.style.top = y + "px";
});

/* AUTO FULLSCREEN */
document.addEventListener("click", function() {
    if (!document.fullscreenElement) {
        document.documentElement.requestFullscreen().catch(err => {});
    }
});
</script>

</body>
</html>
