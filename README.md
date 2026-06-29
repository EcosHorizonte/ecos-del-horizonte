<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Ecos del Horizonte</title>

<style>

body{
margin:0;
background:#222;
overflow:hidden;
font-family:Arial;
}

canvas{
display:block;
margin:auto;
background:#7bd96d;
border:4px solid black;
margin-top:20px;
}

#titulo{
text-align:center;
font-size:30px;
color:white;
margin-top:15px;
}

</style>

</head>

<body>

<div id="titulo">
🌟 ECOS DEL HORIZONTE 🌟
</div>

<canvas id="juego" width="480" height="320"></canvas>

<script>

const canvas=document.getElementById("juego");
const ctx=canvas.getContext("2d");

let jugador={
x:220,
y:150,
vel:3
};

let teclas={};

document.addEventListener("keydown",(e)=>{
teclas[e.key]=true;
});

document.addEventListener("keyup",(e)=>{
teclas[e.key]=false;
});

function actualizar(){

if(teclas["ArrowUp"]) jugador.y-=jugador.vel;

if(teclas["ArrowDown"]) jugador.y+=jugador.vel;

if(teclas["ArrowLeft"]) jugador.x-=jugador.vel;

if(teclas["ArrowRight"]) jugador.x+=jugador.vel;

}

function dibujar(){

ctx.clearRect(0,0,480,320);

ctx.fillStyle="#2e8b57";
ctx.fillRect(0,0,480,320);

ctx.fillStyle="#8B4513";
ctx.fillRect(40,40,60,60);

ctx.fillStyle="darkgreen";
ctx.beginPath();
ctx.arc(350,70,18,0,Math.PI*2);
ctx.fill();

ctx.beginPath();
ctx.arc(390,120,18,0,Math.PI*2);
ctx.fill();

ctx.fillStyle="dodgerblue";
ctx.beginPath();
ctx.arc(jugador.x,jugador.y,12,0,Math.PI*2);
ctx.fill();

}

function juego(){

actualizar();

dibujar();

requestAnimationFrame(juego);

}

juego();

</script>

</body>
</html>
