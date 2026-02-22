# tsekk.github.io
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Энэ бол яаж ч болох сайт болгоомж илүүдэхгүй</title>

<style>
body{
    margin:0;
    background:black;
    color:lime;
    font-family: monospace;
    text-align:center;
    overflow:hidden;
}

h1{
    font-size:60px;
    margin-top:20vh;
    animation: blink 1s infinite;
}

@keyframes blink{
    0%{opacity:1;}
    50%{opacity:0;}
    100%{opacity:1;}
}

button{
    padding:15px 30px;
    font-size:20px;
    background:red;
    color:white;
    border:none;
    cursor:pointer;
    margin-top:30px;
}

#message{
    font-size:30px;
    margin-top:30px;
    display:none;
}
</style>
</head>
<body>

<h1>🚨 maybe your device hacked ahahha🚨</h1>

<button onclick="troll()">Болиулж бас болно</button>

<div id="message">Гэхдээ болихгүй л дээ одоо утас чинь аняагийх хахаха</div>

<script>
function troll(){
    document.body.style.background="red";
    document.getElementById("message").style.display="block";
}
</script>

</body>
</html>
