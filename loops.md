Loops
=======

* In the next few classes, we'll look at how to use loops to repeat things.

* The first type of loop that we need to know how to use is a "while" loop.

```
while(condition){
  code
}
```

* A while loop will continue executing the code in between its braces until the condition is no longer true.

* A loop can be infinite (in fact infinite loops can be useful!), so we need to make sure that the condition will eventually 
  be false.
  
  ```
  while(true){
    code
  }
  ```
  
* The loop above here will run forever and might keep the program from finishing execution.
  
* By having loops in a programming language, it is subject to "The Halting Problem."
  * Ask students if they could write a program that is the longest possible running program but that still exits.
  * Ask them if they can write a program that runs forever.
  * Explain that it's not possible to know whether a program finishes running or not due to the halting problem.
  
* Next, let's use a loop to draw some things.

```
void setup(){
  size(800,800);
  background(255);
  fill(0);
  
  int c = 0;
  while(c < 800){
     ellipse(c,c,1,1);
     c++;
  }
}
```

* We can do the same thing with a "for" loop instead.  For loops are more natural for counter-based code.

```
void setup(){
  size(800,800);
  background(255);
  fill(0);
  
  for(int c = 0; c < 800; c++){
    ellipse(c,c,1,1);
  }
}
```

* We can nest loops so that we can "iterate" over more than one variable at a time.

```
void setup(){
  size(800,800);
  background(255);
  fill(0);
  
  for(int x = 0; x < 800; x++){
    for(int y = 0; y < 800; y++){
      ellipse(x,y,1,1);
    }
  }
}
```
