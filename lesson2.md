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

Demo
====

```
void setup(){
  size(400,400);
}

void draw() {
  background(0);
  rect(100,100,100,100);
}
```

* Discuss how graphics are drawn on the screen
  * Colors using rgb or hex values
  * Pixels for each point on the screen

* Demonstrate a simple program that draws a square that follows the mouse
* Show the code for the program and briefly cover what it does
  * Try to not go too far into specifics about how the code works.  This example is just to show what some code looks like.

* Have students make a few modifications to the code

* Change each parameter to rect to 50 (one at a time) to see what changes
```
rect(50,100,100,100);
```

* Change the position of rect to follow the mouse
```
rect(mouseX,mouseY,100,100);
```

* Change the size of the rectangle so that it changes as the mouse moves
```
rect(mouseX,mouseY,mouseX,mouseY);
```

* Move the redraw of the background to the setup phase
```
void setup(){
  size(400,400);
  background(0);
}

void draw(){
  rect(mouseX,mouseY,100,100);
}
```

Follow-Up Discussion
====================

* Discuss how solving the problem in code is similar to writing the real-life algorithms that they worked on in the previous class
  * Reiterate the terms "algorithm" and "abstraction"
