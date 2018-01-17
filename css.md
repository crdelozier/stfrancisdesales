Making your HTML look better with CSS
-------------------------------------

* HTML describes the content of a website.
* CSS adds style to that content (colors, fonts, sizes, locations!)

* First, we need to include the CSS in your HTML file.
* Make a new CSS file style.css
* In your HTML file, add the line:

```
<link rel="stylesheet" type="text/css" href="style.css">
```

* This will link our CSS style to the content in our HTML document.
* Next, we'll edit the CSS file to add some style to our page.

```
body {
    background-color: lightblue;
}

h1 {
    color: navy;
    margin-left: 20px;
}
```

* Like in processing, we can set colors in a few different ways.

```
#5ACB88
rgb(255,100,255)
```

* Unlike processing, you won't be able to represent the color as a single color.  You'll need to use the rgb notation with numbers between 0 and 255.
