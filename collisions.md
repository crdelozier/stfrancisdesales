* Next, we work toward making a simple pong game.  We go back to a simple program first:

```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
}
```

* This code draws a 2-D ball in the middle of the screen.  The next step is to make the ball move.

```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  x = x + 1;
}
```

* Have the students try changing "x + 1" to different values
  * "x - 1" to make the ball move in the opposite direction
  * "x + 5" to make the ball move faster
* Have the students make the ball move vertically instead of horizontally
  * "y = y + 1" instead of "x = x + 1"
* Have the students figure out how to make the ball move diagonally
  * Change both x and y
  
* Next, we want to be able to "programmatically" change the direction of the ball.
* So, we need variables to control the direction that the ball is moving.

```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;
int xdir = 1;
int ydir = 1;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  x = x + xdir;
  y = y + ydir;
}
```

* Now, the variables (currently constants) xdir and ydir control the movement of the ball.
* Have the students change xdir and ydir and attempt to make the ball move to each corner
  of the screen in a diagonal line.
* Have the students change the speed of the ball by changing the values of xdir and ydir.

* Next, we want to keep the ball in the screen!  This is where we introduce if-statements to the
  students to help them keep the ball in the screen.
  
```
if(condition{
  code
}
```

* "If you finish your homework, you can watch TV."

```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;
int xdir = 1;
int ydir = 1;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  x = x + xdir;
  y = y + ydir;
  
  check();
}

void check(){
  if(x == 790){
    xdir = -1;
  }
  
  if(y == 790){
    ydir = -1;
  }
}
```

* Show them how to detect collsions in the x direction first.  Then, try to get them to figure
  out how to stop the ball in the y direction too.
  
* Next, ask them how to stop the ball at the top and left of the screen.  Usually, you'll need 
  to remind them where the top-left (0,0) and bottom-right (800,800) of the screen are.
  
```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;
int xdir = 1;
int ydir = 1;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  x = x + xdir;
  y = y + ydir;
  
  check();
}

void check(){
  if(x == 790){
    xdir = -1;
  }
  
  if(y == 790){
    ydir = -1;
  }
  
  if(x == 10){
    xdir = 1;
  }
  
  if(y == 10){
    ydir = 1;
  }
}
```

* Next, we want to add a speed variable to the code so that students can 
  control the speed independently of the direction.
  
```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;
int xdir = 1;
int ydir = 1;
int speed = 1;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  x = x + xdir * speed;
  y = y + ydir * speed;
  
  check();
}

void check(){
  if(x == 790){
    xdir = -1;
  }
  
  if(y == 790){
    ydir = -1;
  }
  
  if(x == 10){
    xdir = 1;
  }
  
  if(y == 10){
    ydir = 1;
  }
}
```

* Once the students have added the speed variable to the code, have them try different values of 
  speed and see which ones work.
  * This works well as a contest.  Have them try to find the largest value that still keeps the 
    ball in the screen.
    
* The largest value that my students found was 39.  You can then show them that it works for 390 as well.

* Show them that we're starting at 400 and going to 790 (790 - 400 = 390).  So, anything that divides cleanly
  (without a remainder) into 390 will work.
  * They probably won't really understand the math too well, but that's ok.
  
* So, we need to fix this so that it works for values that "just miss" 790 and 10.  We can use less-than and 
  greater-than to catch more values.

* I recommend making this change very slowly because some of them will get lost here now that the code is getting
  too large to keep all of it on the screen.

```
void setup(){
  size(800,800);
}

int x = 400;
int y = 400;
int xdir = 1;
int ydir = 1;
int speed = 1;

void draw(){
  background(255);
  fill(0);
  ellipse(x,y,20,20);
  x = x + xdir * speed;
  y = y + ydir * speed;
  
  check();
}

void check(){
  if(x < 790){
    xdir = -1;
  }
  
  if(y < 790){
    ydir = -1;
  }
  
  if(x > 10){
    xdir = 1;
  }
  
  if(y > 10){
    ydir = 1;
  }
}
```

* This is it for how collisions work.  Next we move onto the code for a pong game.
