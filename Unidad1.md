~~~ js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(1910, 940);
  walker = new Walker();
  walker1 = new Walker();
  background(255);
  console.log("Setup started");
}

function draw() {
  walker.step();
  walker.show();

  walker1.step();
  walker1.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
  stroke(random(255), random(255), random(255));

  const choice = floor(random(4));
  let size = floor(random(6)) + 15;

  if (choice == 0) { circle(this.x, this.y, size); } 
  else if (choice == 1) { ellipse(this.x, this.y, size * 1.5, size); } 
  else if (choice == 2) { triangle( this.x, this.y - size / 2, this.x - size / 2, this.y + size / 2, this.x + size / 2, this.y + size / 2 ); } 
  else { rectMode(CENTER); square(this.x, this.y, size); } }

  step() { 
    const choice = floor(random(4)); 

    if (choice == 0) { this.x += 10; } 
    else if (choice == 1) { this.x -= 10; } 
    else if (choice == 2) { this.y += 10; } 
    else { this.y -= 10; } 
    if (this.x > width || this.x < 0) { this.x = 0 }
    if (this.y > height || this.y < 0) { this.y = 0 }}
}
~~~
