Pong Improvement Ideas
----------------------

* Hi everyone!  Here are some ideas to improve the Pong game that
we created in class.  You can choose one or more of these ideas
to improve your game with, or you can think of something on your
own!  

* The ideas are in order of difficulty from least code changes
to most code changes.

* For each change, I'll give you the function that you should 
make the change in and some hints on how to change the code.
However, I won't give a whole new code file, so you'll have to 
figure out how to modify the existing code.

Bigger (or Smaller) Paddle
--------------

* The first thing we need to change to make a bigger paddle
is the animated size of the paddle.

* Recall that the arguments to rect() are:

```
rect(x-position,y-position,width,height);
```

* So, we need to change the paddle animation to make the 
 height larger:

```
rect(20,mouseY,20,100);
```

* In this example, the height of the paddle becomes 100 instead
of 50.

* Next, we need to change the collision detection for the paddle
so that the collision zone is as large as the paddle itself!

```
if(y > mouseY && y < mouseY + 100){
```

* The number that we add to mouseY must be equal to the size
 of the paddle.

Decreasing Paddle Size with Each Hit
------------------------------------

* We already increase the score and speed each time we hit the ball
with the paddle.  We could also make the paddle smaller each time.

* First, we need to add a new variable for the size of the paddle.

```
int ps = 50;
```

* Next, we need to change the height of the paddle based on 
the variable we just created.

* Recall that the arguments to rect() are:

```
rect(x-position,y-position,width,height);
```

* So, we need to change the call that creates the paddle to:

```
rect(20,mouseY,20,ps);
```

* Next, we need to decrease the paddle size each time we
 hit the ball.  This should go where we increase the speed
 and the score.

```
ps = ps / 2;
```

* In this example, we're making the paddle half-size each time we hit
the ball.  You can use some other equation if you want!  Just be sure
that you don't end up with a zero size paddle!

* We also need to change the collision detection for the paddle:

```
if(y > mouseY && y < mouseY + ps){
```

* Finally, we need to reset the size of the paddle when the player loses.
 This should go where we reset the other variables when the player loses.

```
ps = 50;
```

Making the Game Two Player
--------------------------

* To allow for two players, we need to add another way to control a paddle
because we don't have two mice to use.  We'll use the keyboard to control
a second paddle.

* First, we'll add a new variable that will control where the second paddle is:

```
int p = 400;
```

* We need to add a new score variable too to keep track of both player's scores.

```
int score2 = 0;
```

* We initialize the other paddle to be in the middle of the screen (400).

* Next, we need to draw a new paddle in the draw() function:

```
rect(740,p,20,50);
```

* Now, we need to add some code to make the new paddle move.  We'll use the 
keyPressed() function to get input from the keyboard.

```
void keyPressed(){
  if(key == 'w'){
    p -= 10;
  }
  if(key == 's'){
    p += 10;
  }
}
```

* You may need to adjust how fast the new paddle moves by changing 10 to some
other number.

* Next, we need to change our collision detection code in checkCollisions() to
end the game if the ball goes past the right paddle and collide with the right
paddle.

* The following code:

```
if(x > 790){
  xdir = -1;
}
```

* should become:

```
if(x > 800){
  reset();
}
```

* This allows the ball to exit the right side of the screen and reset the game.

* Finally, we need to add collision detection code for the right paddle:

```
if(x > 730 && x < 770){
  if(y > p && y < p + 50){
    if(xdir == 1){
      speed++;
    }
    xdir = -1;
  }
}
```

* The last thing that you need to decide is how to score the two-player game.
Should players get a point each time they hit the ball?  Should players only 
get points when they get the ball past their opponent's paddle?  Choose how
to score the game and update any code that deals with the score!

Bonus Ideas (No Hints)
-----------------------

* Change the background color every time a player hits the ball.

* Change the size of the ball and make sure that when it collides with the top 
and bottom of the screen the entire ball stays visible (part of the ball should 
not exit the screen).

* Add a cheat code enabled by pressing some keyboard buttons (use keyPressed())
 that gives the player a big advantage.
 
* Program some artificial intelligence for player 2!  You should try to make the second player's moves 
  as fair as possible.  The computer opponent should have some limitations on how it can move so that 
  it isn't perfect.  Don't just make it so that the artificial intelligence always wins.
