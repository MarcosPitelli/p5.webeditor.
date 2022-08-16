// variavél da Bolinha
let xBolinha = 300;
let yBolinha = 200;
let diâmetro = 25;
let raio = diâmetro / 2;

// velocidade da Bolinha
let velocidadexBolinha = 4;
let velocidadeyBolinha = 4;

// variáveis da raquete
let Xraquete = 10;
let Yraquete = 150;
let raqueteComprimento = 10;
let raqueteAltura = 90; 

// variáveis raquete oponente
let xRaquete = 580;
let yRaquete = 150;
let Raquetecomprimento = 10;
let RaqueteAltura = 90;

function setup() {
  createCanvas(600, 400);
}

function draw() {
  background(0);
  mostrarBolinha ();
  movimentaBolinha ();
  verificaColisãoBorda ();
  circle(xBolinha, yBolinha, diâmetro);
  xBolinha += velocidadexBolinha;
  yBolinha += velocidadeyBolinha;
  mostraRaquete();
  movimentaMinhaRaquete();
  verficaColisaoRaquete();
  mostraRaqueteOP();
  movimentaOPraquete();
  verificaColisaoOPraquete();
 }

 function mostrarBolinha (){
   circle(xBolinha, yBolinha, diâmetro);
 }

 function movimentaBolinha (){
  xBolinha += velocidadexBolinha;
  yBolinha += velocidadeyBolinha;
   
 }

 function verificaColisãoBorda (){
    if (xBolinha + raio> width || xBolinha - raio< 0){
   velocidadexBolinha *= -1; 
    }
  if (yBolinha + raio> height || yBolinha - raio< 0) {
   velocidadeyBolinha *= -1;
  }
 }

 function mostraRaquete(){
   rect (Xraquete, Yraquete, raqueteComprimento, raqueteAltura);
 }

 function movimentaMinhaRaquete(){
   if (keyIsDown (UP_ARROW)){
     Yraquete -= 10;  
   }
   if (keyIsDown (DOWN_ARROW)){
     Yraquete += 10;
   }
 }
 function verficaColisaoRaquete(){
   if (xBolinha - raio < Xraquete + raqueteComprimento && yBolinha - raio < Yraquete + raqueteAltura && yBolinha + raio > Yraquete){
      velocidadexBolinha *= -1;
   }
 }

 function mostraRaqueteOP(){
   rect (xRaquete, yRaquete, Raquetecomprimento, RaqueteAltura);
 }
   
 function movimentaOPraquete(){
   if (keyIsDown (RIGHT_ARROW)){
     yRaquete -= 10;
   }
   if (keyIsDown (LEFT_ARROW)){
     yRaquete += 10;
   }
 }
 function verificaColisaoOPraquete(){
   if (xBolinha - raio < yRaquete + Raquetecomprimento && yBolinha - raio < yRaquete + RaqueteAltura && yBolinha + raio > yRaquete){
      velocidadexBolinha *= -1;
   }
 }
