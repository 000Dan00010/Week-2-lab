//Week-2-lab


Walker[] walk;

void setup() {

  size(500, 500);
  
  background(255);

  walk = new Walker[400];

  for (int i = 0; i < walk.length; i++) {
    walk[i] = new Walker(int(random(width)), int(random(height)), random(5));
  }
}

void draw() {

  for (int i = 0; i < walk.length; i++) {
    
    walk[i].draw_walk();

   

    for (int j = 0; j < walk.length; j++) {
     
      int drawline = 30;

      if (dist(walk[i].x, walk[i].y, walk[j].x, walk[j].y) <= drawline) {
        noStroke();
        strokeWeight(0);
        line(walk[i].x, walk[i].y, walk[j].x, walk[j].y);
      }
    }
  }
}


class Walker {


  int x;
  int y;

  float speed;
  

  float esize = random(200);


  color c = color(random(205), random(50), random(255), random(255));


  Walker(int x, int y, float speed) {
    this.x = x;
    this.y = y;
    this.speed = speed;
  }

  void draw_walk() {
    noStroke();
    fill(c);
    ellipse(x, y, esize, esize);
    x = x+int( random(-speed, speed) );
    y = y+int( random(-speed, speed) );
  }
}
