<!DOCTYPE html>
<html>
<head>
<title>Apanha as Moedas</title>
<style>
body{
    text-align:center;
    font-family:Arial;
}

#game{
    width:400px;
    height:400px;
    border:3px solid black;
    margin:auto;
    position:relative;
}

#player{
    width:30px;
    height:30px;
    background:red;
    position:absolute;
}

.coin{
    width:20px;
    height:20px;
    background:gold;
    border-radius:50%;
    position:absolute;
}
</style>
</head>

<body>

<h1>Apanha as Moedas</h1>
<p>Pontos: <span id="score">0</span></p>

<div id="game">
<div id="player"></div>
</div>

<script>
let player = document.getElementById("player")
let game = document.getElementById("game")
let score = 0

let x = 180
let y = 180

document.addEventListener("keydown", function(e){

if(e.key=="ArrowRight") x+=10
if(e.key=="ArrowLeft") x-=10
if(e.key=="ArrowUp") y-=10
if(e.key=="ArrowDown") y+=10

player.style.left=x+"px"
player.style.top=y+"px"

checkCoin()

})

function createCoin(){

let coin=document.createElement("div")
coin.className="coin"

coin.style.left=Math.random()*380+"px"
coin.style.top=Math.random()*380+"px"

game.appendChild(coin)

}

function checkCoin(){

let coins=document.querySelectorAll(".coin")

coins.forEach(c=>{
let cx=c.offsetLeft
let cy=c.offsetTop

if(Math.abs(cx-x)<20 && Math.abs(cy-y)<20){

c.remove()
score++
document.getElementById("score").innerText=score

createCoin()

}

})

}

createCoin()
</script>

</body>
</html>
