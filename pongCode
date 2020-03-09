/* **************************
Pong v1.0
Developed by Aining Wang
************************** */
function setup() {
  createCanvas(600, 400);
  // Set new text font
  textFont("Bubbleboddy Neue Trial");
}

/* **************************
Variables defination 
************************** */
var hitSound;
var missSound;
var scoreL = 0;
var scoreR = 0;

var gameStatus = 0;

var playerHeight = 80;
var playerWidth = 20;
var playerSpeed = 8;
var playerL = 200;
var playerR = 200;

var ballX = 300;
var ballY = 200;
var ballSize = 20;
var ballXSpeed = 0;
var ballYSpeed = 0;

/* **************************
Functions defination 
************************** */
//recurring run in backgroud
function draw(){
  
  clickToStart();
  
  if(gameStatus == 0){
    startPage();
  }else if(gameStatus == 2){
    gameOver();
  }else{
    inGame();
  }
  
  checkGameOver();
}

// preload he backgroud image, useful resources by p5.js
function preload() {
  soundFormats("wav");
  hitSound = loadSound("ballSound.wav");
  missSound = loadSound("missSound.wav");
}

function inGame() {
  background(19, 51, 55);
  strokeWeight(0.5);
  stroke(255, 255, 255);
  line(300, 30, 300, 370);
  
  // draw left player
  fill(19, 51, 55);
  strokeWeight(1.5);
  rect(0, playerL, playerWidth, playerHeight, 20);
  
  // draw right player
  fill(19, 51, 55);
  strokeWeight(1.5);
  rect(width-playerWidth, playerR, playerWidth, playerHeight, 20);
  
  // draw ball
  fill(19, 51, 55);
  strokeWeight(1.5);
  ellipse(ballX, ballY, ballSize)
  
  
  /* User Input */
  // 'W' key
  if (keyIsDown(87)) {
    playerL = playerL - playerSpeed
  }
  // 'S' key
  if (keyIsDown(83)) {
    playerL = playerL + playerSpeed
  }
  
  if (keyIsDown(UP_ARROW)) {
    playerR = playerR - playerSpeed
  }
  if (keyIsDown(DOWN_ARROW)) {
    playerR = playerR + playerSpeed
  }
  
  /* Game logic */
  if (playerL <= 0) {
    playerL = 0;
  }
  if (playerL > height - playerHeight) {
    playerL = height - playerHeight;
  }
  
  if (playerR <= 0) {
    playerR = 0;
  }
  if (playerR > height - playerHeight) {
    playerR = height - playerHeight;
  }
  
  ballX = ballX + ballXSpeed;
  ballY = ballY + ballYSpeed;
  
  // Bounce off top wall
  if (ballY < 0) {
    ballY = 0;
    ballYSpeed = -ballYSpeed;
  }

  // Bounce off bottom wall
  if (ballY > height) {
    ballY = height;
    ballYSpeed = -ballYSpeed;
  }
  
  // bounce off right player
  if (ballX > width - playerWidth && ballY >= playerR && ballY <= playerR + playerHeight) {
    hitSound.play();
    ballX = width - playerWidth;
    ballXSpeed = - ballXSpeed;
    // speed++
    ballXSpeed = ballXSpeed - 0.5;
    ballYSpeed = ballYSpeed + random(-1,1);
  }
  
  // bounce off left player
  if (ballX < playerWidth && ballY >= playerL && ballY <= playerL + playerHeight) {
    hitSound.play();
    ballX = playerWidth;
    ballXSpeed = - ballXSpeed;
    // speed++
    ballXSpeed = ballXSpeed + 0.5;
    ballYSpeed = ballYSpeed + random(-1,1);
  }
  
  // playerL scores!
  if (ballX > width) {
    missSound.play();
    ballX = width/2
    ballY = height/2
    scoreL = scoreL + 1
    ballXSpeed = - ballXSpeed 
    // reset speed
    ballXSpeed = -3;
    ballYSpeed = random(-1, 1);
  }
  fill(255, 255, 255);
  text("PlayerL: " + scoreL, 10, 30);
  
  // playerR scores!
  if (ballX < 0) {
    missSound.play();
    ballX = width/2
    ballY = height/2
    scoreR = scoreR + 1
    ballXSpeed = - ballXSpeed 
    // reset speed
    ballXSpeed = 3;
    ballYSpeed = random(-1, 1); 
  }
  fill(255, 255, 255);
  text("PlayerR: " + scoreR, 500, 370);
  
}

// function to draw the start page
function startPage(){
  background(19, 51, 55);
  strokeWeight(0.5);
  stroke(255, 255, 255);
  line(300, 30, 300, 370);
  fill(255, 255, 255);
  textSize(20);
  text("PONG", 150, 150);
  text("Click to start", 150, 200);
  textSize(12);
  text("PlayerL use W & S", 150, 250);
  text("PlayerR use Up & Down", 150, 270);
}

function clickToStart(){ 
  if(mouseIsPressed){
    gameStatus = 1;
    ballXSpeed = 3;
    ballYSpeed = random(-1, 1);
  }
}

function checkGameOver(){
  if(scoreL >= 5 || scoreR >= 5){
    gameStatus = 2;
  }
}

function gameOver(){
  background(19, 51, 55);
  strokeWeight(0.5);
  stroke(255, 255, 255);
  line(300, 30, 300, 370);
  fill(255, 255, 255);
  textSize(20);
  text("Game Over", 150, 150);
  if(scoreL > scoreR){
    text("Player L win!", 150, 200);
  }else{
    text("Player R win!", 150, 200);
  }
  noLoop();
}
