Pong
--------

* Now that we have basic collision detection, we can create a Pong game by adding a paddle and performing 
  collision detection on the paddle.
  
* The first thing we need to add to our existing code is a paddle.  We'll use the mouse to control the position 
   of the paddle.  We can add the following line of code to the draw() function to draw our paddle.
   
```
rect(40,mouseX,20,50);
```

* Next, we need to add collision detection for the paddle.  We can add the following code to the check() or 
  checkCollisions() function.
  
```
if(x > 30 && x < 70){
  if(y > mouseY && y < mouseY + 50){
    xdir = 1;
  }
}
```

* This code checks a range of values around our paddle to see if the ball is colliding with the paddle.

* Now that we can block the ball with the paddle, we should stop the ball from bouncing off of the left side of the
  window.  Instead, we should reset the game when the ball goes past the paddle.
  
```
void check(){
  ...
  if(x < 0){
    reset();
  }
  ...
}

void reset(){
  x = 400;
  y = 400;
  speed = 1;
}
```

* Finally, we need to add a scoring system to our game.  We should add a score variable and update it each time
  the user hits the paddle.

```
// This creates the window
void setup(){
  size(800,800); 
}

// x and y are the ball's position
int x = 400;
int y = 400;

// xdir and ydir are the ball's direction
int xdir = 1;
int ydir = 1;

// This is the ball's speed
int speed = 1;

// This is the game score
int score = 0;

void draw(){
  // These calls set the colors
  background(255);
  fill(0);
  
  // This draws the ball
  ellipse(x,y,20,20);
  
  // This draws the paddle
  rect(40,mouseY,20,50);
  
  moveBall();
  checkCollisions();
}

// This function moves the ball on the screen
void moveBall(){
  x = x + xdir * speed;
  y = y + ydir * speed;
}

void checkCollisions(){
  // If the ball goes out of the screen, the game is over
  if(x < 0){
    reset();
  }
  
  // This makes the ball bounce off of the right side
  // of the window
  if(x > 790){
    xdir = -1;
  }
  
  // This makes the ball bounce off of the top of the window
  if(y < 10){
    ydir = 1; 
  }
  
  // This makes the ball bounce off of the bottom of the window
  if(y > 790){
    ydir = -1;
  }
  
  // This code does collision detection on the paddle
  if(x > 30 && x < 70){
    if(y > mouseY && y < mouseY + 50){
      if(xdir == -1){
        speed++;
        score++;
      }
      xdir = 1;
    }
  }
}

// This function gets called when the game is over
// We should reset the game state here
void reset(){
  println("Score: " + score);
  speed = 1;
  score = 0;
  x = 400;
  y = 400;
}
```

* Now that the students have a functioning Pong game, you can direct them to the ideas.md file and have them modify 
  their existing version of pong to do something new!
