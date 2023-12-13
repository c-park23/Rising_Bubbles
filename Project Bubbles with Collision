float factor = 0.005;
float filt;
float filtFact = 0.5;
ArrayList <Bubble> bubbles;
int total =0;
void setup() {
  size(300, 700);
  filt = height * filtFact;
  bubbles = new ArrayList <Bubble>();
}
void draw() {
  total =bubbles.size();
  background (70, 110, 150);
  printTotals();
  if (mousePressed) {
    bubbles.add(new Bubble());
  }
  for (int i = 0; i < bubbles.size(); i++) {
    bubbles.get(i).rise();
    if (bubbles.get(i).y <0) {
      bubbles.get(i).y = height;
    } else {
      bubbles.get(i).show();
    }
  }
  fill(50, 50, 100, 50);
  detectCollison(bubbles);
  markAndRemove();
}
void detectCollison(ArrayList<Bubble> b_) {
  for (int i=bubbles.size()-1; i >= 0; i--) {
    Bubble ab = b_.get(i);
    for (int j=bubbles.size()-1; j >= 0; j--) {
      Bubble sb = b_.get(j);
      if (ab != sb) {
        if ((dist(ab.x, ab.y, sb.x, sb.y)<= (ab.diam/2+sb.diam/2))) {
          bubbles.get(i).collided = true;
          bubbles.get(j).collided = true;
        }
      }
    }
  }
}

void mousePressed() {
  if (mousePressed) {
    bubbles.add(new Bubble());
  }
}
void markAndRemove() {
  for (int i=bubbles.size()-1; i >= 0; i--) {
    Bubble b = bubbles.get(i);
    if (b.collided == true||b.x-b.diam/2 <= 0 || b.x+b.diam/2 >= width) {
      System.out.println(i);
      bubbles.remove(i);
    }
  }
}
void printTotals() {
  textSize(16);
  fill(255, 105, 180);
  text("total "+total, width/2, 50);
}
class Bubble {
  float x, y, diam, floats;
  int r, g, b;
  boolean collided;
  Bubble() {
    x = width*(float)Math.random();
    y = height;
    diam = 30 * (float)Math.random() + 5;
    floats = diam * diam * factor;
    r = (int)(256*Math.random());
    g = (int)(256*Math.random());
    b = (int)(256*Math.random());
    collided = false;
  }
  Bubble(int r_, int g_, int b_) {
    this();
    r = r_;
    g = g_;
    b = b_;
  }
  Bubble(int x_, int y_) {
    this();
    x = x_;
    y = y_;
  }
  void rise() {
    x += (Math.random() - 0.5) * 2;
    y -= floats;
  }
  void show() {
    fill(r, g, b);
    ellipse(x, y, diam, diam);
    stroke(255, 0, 0);
    noStroke();
  }
}
