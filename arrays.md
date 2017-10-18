```
void setup(){
  size(800,800);
  
  x = new int[b];
  y = new int[b];
  xdir = new int[b];
  ydir = new int[b];
  
  for(int c = 0; c < b; c++){
    x[c] = (int)random(0,800);
    y[c] = (int)random(0,800);
    
    if(random(0,100) > 50){
      xdir[c] = 1;
    }else{
      xdir[c] = -1; 
    }
    
    if(random(0,100) > 50){
      ydir[c] = 1;
    }else{
      ydir[c] = -1; 
    }
  }
}

int b = 13;

int x[];
int y[];

int xdir[];
int ydir[];

int speed = 5;

void draw(){
  background(255);
  fill(0);
  
  for(int c = 0; c < b; c++){
    ellipse(x[c],y[c],20,20);
    x[c] = x[c] + xdir[c] * speed;
    y[c] = y[c] + ydir[c] * speed;
    check(c);
  }
}

void check(int c){
  if(x[c] > 790){
    xdir[c] = -1; 
  }
  
  if(x[c] < 10){
    xdir[c] = 1; 
  }
  
  if(y[c] > 790){
    ydir[c] = -1; 
  }
  
  if(y[c] < 10){
    ydir[c] = 1; 
  }
}
```
