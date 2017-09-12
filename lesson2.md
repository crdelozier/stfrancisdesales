Looking at some code!
=====================

In this lesson, we want to give some context for how the problems that the students worked on in their last class relate to the problems that they can solve with a computer.
We'll introduce the Processing language and demo some code that draws shapes on a blank background.

Initial Discussion
==================

* What did we do in the last class?
* What were some of the challenges involved in designing an algorithm?

Installing and Starting Processing
==================================

* Download Processing from http://download.processing.org/processing-3.3.6-windows32.zip
* Extract the files
* Start Processing by double-clicking on the Processing application

Windows and Colors
==================

* The setup() function is the first thing that Processing will call for us.  We will use it to make a window of a 
  specified size and set the background color.

* When we write a function, it has the following structure:

```
return-type name ( parameters ) {
  line1;
  line2;
  ...
}
```

* The return type is what a function gives back when a program calls the function. 
  * For example, a soda machine takes a few dollars and returns a soda.
* The name of the function is what a programmer calls it.  The name should describe what the function does.
* The parameters are contained between an open and closed parenthesis.  Sometimes a function needs parameters to 
  perform a task so that it can do more than one thing.
  * For example, the parameters for a soda machine are the dollars that you put into it.  Without too few dollars, the soda
    machine will not return a soda.  With too many dollars, the soda machine will return a soda and some change.
* Between the curly braces "{" and "}" is the "body" of the function.  The body contains all of the code that will run 
  when the function is called.
  
* In programming, when you use an "open" parenthesis "(", a bracket "[", or a curly brace "{", that symbol must always be matched
  by a "closed" parenthesis ")", bracket "]", or curly brace"}" of the same kind.  If you do not match the symbols, the program 
  will not run.

* You can change the size of the window and the color of the background by changing the numbers.
  * The numbers are "parameters" to the function.  Changing these numbers changes what the function that 
    we are calling does.
   
* For our first program, we will both write and use functions.  In the code below, we write a function "setup()" that 
  creates a window using the size function and sets the background color using the background function.

```
void setup(){
  size(400,400);
  background(0);
}
```

* When we call a function, we use the form:

```
name(inputs);
```

* For the size function, the name is "size" and the inputs are the x and y size of the window we want to create.
* For the background function, the name is "background" and the input is a single number that defines the color of the window.

* We can also use a set of red, green, and blue values for the background function.

```
void setup(){
  size(400,400);
  background(0,40,0);
}
```

* By using 3 values, we can mix the colors to create any color that we choose!  Try mixing different values to produce your 
  favorite color.
  
* Discuss how graphics are drawn on the screen
  * Colors using rgb or hex values
  * Pixels for each point on the screen
  
* Why are colors in rgb?
  * A mix of these colors can create any color possible, just like you can with the primary colors yellow, blue, and red.
  * These are historically used for computers and televisions because a computer screen emits light.
  * https://upload.wikimedia.org/wikipedia/commons/c/c2/AdditiveColor.svg

* Next, we will write another function that will periodically update the screen.

```
void setup(){
  size(400,400);
}

void draw() {
  background(0);
}
```

* The "draw" function is called by Processing about once per second.  It can be used to do animations.
* Next, we'll add a "variable" to the program so that we can see the effect of the draw function updating the screen.

```
int x = 0;
```

* A variable is a letter that we can use to represent things like numbers, colors, and letters. 
* Variables can change values so that the program can do something different each time.
* We will use this variable to change the color of the background.

```
void setup(){
  size(400,400);
}

int x = 0;

void draw(){
  background(x);
  x = x + 1;
}
```

* What happened?
* Why did we only get blues after the grey colors?
* Colors can also be represented as hexadecimal values.
  * You are used to using the decimal values 0-9.  Hexadecimal uses 0-F where A = 10, B = 11, C = 12, D = 13, E = 14, and F = 15.
  * Why do we use a base 10 number system?
  * Computers use a base 2 number system that only has 0 and 1 (because they only have 2 fingers?).
  
* Let's change the program to use hexadecimal colors instead.

```
void setup(){
  size(400,400);
}

color c = #DABDAB;

void draw(){
  background(c);
  c = c + 1;
}
```

* Next, we'll look at a new function that can draw a square.

```
void setup(){
  size(400,400);
  background(255);
}

void draw(){
  rect(50,50,100,100);
}
```

* The "rect" function takes 4 inputs.  These inputs are the x and y positions of the top left of the rectangle, the width of the 
  rectangle, and the height of the rectangle.
* Try changing each of the inputs to see what happens.

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

* What happens if we change the last two inputs to also use the mouseX and mouseY variables?

```
rect(mouseX,mouseY,mouseX,mouseY);
```

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

* We can change the colors of things that we draw using the stroke() and fill() functions.

```
void setup(){
  size(400,400);
  background(255);
  stroke(0,0,255);
  fill(255,0,0);
  rect(50,50,100,100);
}
```

Follow-Up Discussion
====================

* Discuss how solving the problem in code is similar to writing the real-life algorithms that they worked on in the previous class
  * Reiterate the terms "algorithm" and "abstraction"
