let w = 700; // SCREEN WIDTH
let h = 700; // SCREEN HEIGHT
let turnX = false;
let turnO = true;
let player1Name = "P1";
let player2Name = "CPU"; //WRITE P2 TO PLAY WITH ANOTHER HUMAN
let winsLinesWidth = 50;
let numberOfGames = 0;

// 8 represents the empty square

let g = [
  [[8], [8], [8]],
  [[8], [8], [8]],
  [[8], [8], [8]],
];

function setup() {
  createCanvas(w, h); //initialization of the screen
}

function convertMouseToG() {
  x = Math.floor((3 * mouseX) / w); //convert mouse x to grid coordinates
  y = Math.floor((3 * mouseY) / h); //convert mouse y to grid coordinates
  return [x, y];
}

function grid() {
  strokeWeight(2); //grid lines size
  stroke(0); // grid lines color

  // draw grid lines
  for (let x = w / 3; x < w; x = x + w / 3) {
    //vertical grid lines
    line(x, 0, x, h);
  }
  for (let y = h / 3; y < h; y = y + h / 3) {
    //horizontal grid lines
    line(0, y, w, y);
  }

  let co = convertMouseToG();
}
//0 represents O and 1 represents X
function drawO() {
  // draw O
  fill(0, 255, 0); // O color
  strokeWeight(8);
  for (let i = 0; i < g.length; i++) {
    for (let j = 0; j < g[i].length; j++) {
      if (g[i][j] == 0) {
        // check if O in the grid
        ellipse(
          w / 6 + (j * w) / 3, //ellipse x coor
          h / 6 + (i * h) / 3, //ellipse y coor
          w / 3 - 130 / 3, //ellipse's width
          h / 3 - 130 / 3 //ellips's height
        );
      }
    }
  }
}

function drawX() {
  // draw X
  fill(225, 0, 0); //X color
  stroke(225, 0, 0);
  strokeWeight(8);
  for (let a = 0; a < g.length; a++) {
    for (let b = 0; b < g[a].length; b++) {
      if (g[a][b] == 1) {
        // draw two intresct lines
        line(
          20 + (b * w) / 3,
          20 + (a * h) / 3,
          w / 3 - 20 + (b * w) / 3,
          h / 3 - 20 + (a * h) / 3
        );
        line(
          w / 3 - 20 + (b * w) / 3,
          20 + (a * h) / 3,
          20 + (b * w) / 3,
          h / 3 - 20 + (a * h) / 3
        );
      }
    }
  }
  stroke(0);
}
function winText() {
  strokeWeight(3);
  textSize(30);
  c = color(0, 0, 255);
  fill(c);
  textAlign(CENTER, TOP);
  text("CLICK MOUSE TO PLAY AGAIN", w / 2, h / 2);
}

class Player {
  //Player class
  constructor(player, name) {
    this.p = player;
    this.name = name;
    this.score = 0;
  }
  drawPlayer() {
    strokeWeight(3);
    textSize(20);
    if (this.p === "p1") {
      textAlign(LEFT, BOTTOM);
      text(this.name + " : " + this.score, 0, 0, 100, 70);
    } else {
      textAlign(RIGHT, BOTTOM);
      text(this.name + " : " + this.score, w - 200, 0, 100, 70);
    }
  }
  winner() {
    // rows
    for (let i = 0; i < g.length; i++) {
      if (g[i][0] == g[i][1] && g[i][1] == g[i][2]) {
        if (g[i][0] == 1 && this.p == "p1") {
          let c = color(0, 0, 0, 100);
          stroke(c);
          strokeWeight(winsLinesWidth);
          line(
            w / 6,
            (h / 6) * (2 * i + 1),
            5 * (w / 6),
            (h / 6) * (2 * i + 1)
          );
          winText();
          return this.p;
        }
        if (g[i][0] == 0 && this.p == "p2") {
          let c = color(0, 0, 0, 100);
          stroke(c);
          strokeWeight(winsLinesWidth);
          line(
            w / 6,
            (h / 6) * (2 * i + 1),
            5 * (w / 6),
            (h / 6) * (2 * i + 1)
          );
          winText();
          return this.p;
        }
      }
    }

    // columns
    for (let i = 0; i < g.length; i++) {
      if (g[0][i] == g[1][i] && g[1][i] == g[2][i]) {
        if (g[0][i] == 1 && this.p === "p1") {
          let c = color(0, 0, 0, 100);
          stroke(c);
          strokeWeight(winsLinesWidth);
          line(
            ((2 * i + 1) * w) / 6,
            h / 6,
            ((2 * i + 1) * w) / 6,
            (5 * w) / 6
          );
          winText();
          return this.p;
        }
        if (g[0][i] == 0 && this.p === "p2" && g[2][i] == 0) {
          let c = color(0, 0, 0, 100);
          stroke(c);
          strokeWeight(winsLinesWidth);
          line(
            ((2 * i + 1) * w) / 6,
            h / 6,
            ((2 * i + 1) * w) / 6,
            (5 * w) / 6
          );
          winText();
          return this.p;
        }
      }
    }

    // diagonals
    if (
      (g[0][0] == g[1][1] && g[1][1] == g[2][2]) ||
      (g[0][2] == g[1][1] && g[1][1] == g[2][0])
    ) {
      if (g[1][1] == 1 && this.p == "p1") {
        let c = color(0, 0, 0, 100);
        stroke(c);
        strokeWeight(winsLinesWidth);
        if (g[0][0] == 1 && g[2][2] == 1) {
          line(w / 6, h / 6, (5 * w) / 6, (5 * h) / 6);
        }
        if (g[0][2] == 1 && g[2][0]) {
          line((5 * w) / 6, h / 6, w / 6, (5 * h) / 6);
        }
        winText();
        return this.p;
      }
      if (g[1][1] == 0 && this.p == "p2") {
        let c = color(0, 0, 0, 100);
        stroke(c);
        strokeWeight(winsLinesWidth);
        if (g[0][0] == 0) {
          line(w / 6, h / 6, (5 * w) / 6, (5 * h) / 6);
        }
        if (g[0][2] == 0) {
          line((5 * w) / 6, h / 6, w / 6, (5 * h) / 6);
        }
        winText();
        return this.p;
      }
    }
    let s = 0;
    for (let i = 0; i < g.length; i++) {
      for (let j = 0; j < g[i].length; j++) {
        if (g[i][j] != 8) {
          s += 1;
        }
        if (s === 9) {
          emptyGrid();
        }
      }
    }
  }
}
function emptyGrid() {
  for (let i = 0; i < g.length; i++) {
    for (let j = 0; j < g[i].length; j++) {
      g[i][j] = 8;
      numberOfGames += 1;
    }
  }
}
let p1 = new Player("p1", player1Name);
let p2 = new Player("p2", player2Name);

function mouseClicked() {
  let w1 = p1.winner();
  let w2 = p2.winner();
  let c = convertMouseToG();
  let x = c[0];
  let y = c[1];
  if (turnX === true && g[y][x] == 8) {
    turnX = turnO;
    turnO = !turnX;
    g[y][x] = 1;
  }
  if (turnO === true && g[y][x] == 8) {
    turnX = turnO;
    turnO = !turnX;
    g[y][x] = 0;
  }
  if (w1 === "p1") {
    p1.score += 1;
    emptyGrid();
  }
  if (w2 === "p2" || w2 === "CPU") {
    p2.score += 1;
    emptyGrid();
  }
}

function CPU() {
  let l = [];
  //check if the square available
  for (let a = 0; a < g.length; a++) {
    for (let b = 0; b < g[a].length; b++) {
      if (g[a][b] == 8) {
        l.push([a, b]);
      }
    }
  }
  let c = Math.floor(Math.random() * l.length);
  let x = l[c][0];
  let y = l[c][1];

  g[x][y] = 0;
  l.splice(c, 1);

  turnX = turnO;
  turnO = !turnX;
}



function bestMoveCalc(){
  let possibleMoves = 0;
  for (let i=0; i<g.length;i++){
    for (let j=0;j<g[i].length;j++){
      if (g[i][j]==8){possibleMoves+=1}
    }
  }
  
  for (let i=0;i<=possibleMoves;i++){
    for (let a = 0;a<g.length;a++){
      for (let b = 0;b<g.length;b++){
        
      }
    }
  }
}

function draw() {
  background(225);
  if (player2Name === "CPU" && turnO === true && p1.winner() != "p1") {
    CPU();
  }
  grid();
  drawX();
  drawO();
  p1.drawPlayer();
  p2.drawPlayer();
  p1.winner();
  p2.winner();
}
