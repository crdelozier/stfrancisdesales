Intro
======

* What did we do last week?
* Today, we're going to do more animations and work with more shapes and colors!

Drawing
========

* We can also draw a square using the "line" function.  The line function takes 4 inputs for the x and y coordinate of the 
  start of the line and the x and y coordinate for the end of the line.
* Try to draw a square using the line function.

```
void setup(){
  size(400,400);
}

void draw(){
  background(255);
  line(50,50,50,100);
  line(50,100,100,100);
  line(100,100,100,50);
  line(100,50,50,50);
}
```
* Mention that by drawing a square using lines we are implementing the "rect" function.

* Next we go back to drawing square using rectangles.  This is a good time to reiterate that
  comments can be used to save code for later if we might need it.  Have the students comment
  out the calls to line().

* Now let's use a variable to change the position of each part of the square.
* Processing has two built-in variables for the position of the mouse called "mouseX" and "mouseY".
  * We will use these variables to change the position of the square.

```
void setup(){
  size(400,400);
  background(255);
}

void draw(){
  rect(mouseX,mouseY,100,100);
}
```

* Oops!  We have a bug!  What happened?
* The draw() function needs to redraw the background each time, or everything we drew the previous round becomes the background.

```
void setup(){
  size(400,400);
}

void draw(){
  background(255);
  rect(mouseX,mouseY,100,100);
}
```

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
