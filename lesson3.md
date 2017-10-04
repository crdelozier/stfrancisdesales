Intro
======

* What did we do last week?
* Today, we're going to do more animations and work with more shapes and colors!

Drawing
========

* We can use another built-in variable to track the previous position of the mouse.
  * pmouseX and pmouseY track the previous position of the mouse (from the last time draw() was called).

```
void setup(){
  size(640,640);
  background(255);
}

void draw(){
  line(pmouseX,pmouseY,mouseX,mouseY);
}
```

* Why does this draw curves?
  * It's drawing a bunch of very small lines.
  * Try moving the mouse very fast to make it draw a straight line.
  
* We can use another function to do something when the mouse has been clicked.

```
void setup(){
  size(640,640);
  background(255);
}

int x1 = 0;
int y1 = 0;

void draw(){
  line(x1,y1,mouseX,mouseY);
}

void mouseClicked(){
  x1 = mouseX;
  y1 = mouseY;
}
```

* The mouseClicked() function is called when the user clicks the mouse.
* We add two variables x1 and y1 to track the last place that the user clicked.
* We can draw lines from that old start point by using it in the call to line.

* We can also change the color of the lines we're drawing when the mouse is pressed.

```
void setup(){
  size(640,640);
  background(255);
}

int x1 = 0;
int y1 = 0;
color c = 0;

void draw(){
  stroke(c);
  line(x1,y1,mouseX,mouseY);
}

void mouseClicked(){
  x1 = mouseX;
  y1 = mouseY;
  c = color(random(0,255),random(0,255),random(0,255));
}
```

* The random() function gives us random numbers between the two parameters that we specify.  In this case, 
  we specify 0 and 255 to make colors.

* Side note: How do computers generate random numbers?
  * Computer randomness is a math trick.  Random numbers are actually sequences of numbers that start at a "random" point.
  * For example, we might generate "random" numbers by adding 3 each time, but these aren't really random.
  * Random number generators do the same thing but with much more complicated math sequences.
  * Computers can generate random numbers by using their hardware and examining places in memory that are likely to be random.
  * This is important for protecting things like passwords.
  
```
int w = 400;
int h = 350;

void setup(){
  size(400,350);
}

int x = 50;
int y = 0;

int xdir = 1;
int ydir = 1;

int speed = 1;

void draw(){
  background(255);
  fill(0);
  rect(x,y,50,50);
  
  x = x + (speed * xdir);
  y = y + (speed * ydir);
  
  if(x >= 350){
    xdir = -1; 
  }
  
  if(x <= 0){
    xdir = 1; 
  }
  
  if(y >= 300){
    ydir = -1; 
  }
  
  if(y <= 0){
    ydir = 1; 
  }
}

void mouseClicked(){
  speed = speed + 1; 
}
```

* Next, we work on making a simple pong game.  Students can then modify the pong game to make it harder, or add an AI opponent!

```
void setup(){
  size(800,800); 
}

int x = 400;
int y = 400;
int xdir = 1;
int ydir = 1;
int speed = 1;
int l = 0;
int r = 0;
int p = 400;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  rect(760,mouseY,20,50);
  rect(40,p,20,50);
  
  moveBall();
  checkCollisions();
}

void moveBall(){
  x = x + xdir * speed;
  y = y + ydir * speed;
}

void checkCollisions(){
  if(x < 0){
    r++;
    reset();
  }
  
  if(x > 800){
    l++;
    reset();
  }
  
  if(y < 10){
    ydir = 1; 
  }
  
  if(y > 790){
    ydir = -1;
  }
  
  if(x > 20 && x < 60){
    if(y > p - 20 && y < p + 20){
      xdir = 1;
    }
  }
  
  if(x > 740 && x < 780){
    if(y > mouseY - 20 && y < mouseY + 20){
      xdir = -1; 
    }
  }
}

void keyPressed(){
  if(key == 'w'){
    p = p - 10;
  }else if(key == 's'){
    p = p + 10;
  }
}

void reset(){
  println(l + " - " + r);
  x = 400;
  y = 400;
}
```
