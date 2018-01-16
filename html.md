Introduction to HTML
--------------------

* HTML is short for Hyper Text Markup Language.

* HTML tags describe the structure of a website.  They are not shown by the web browser.

* Every HTML tag is opened and closed, just like braces that open and close a scope in Processing.

Let's Get Started!
------------------

* Navigate to the Documents folder on your computer.
* Create a new document named index.html
* Use right click -> Edit to open the document with Notepad

```
<html>
<head>
<title>My Website</title>
</head>
<body>
<h1>Name</h1>
<p>Hello!</p>
</body>
</html>
```

* Every HTML document has 3 tags - html, head, body
* html surrounds the entire document
* head is the first part, usually containing title and other metadata about the website
* body is the text of the website
* h1, h2, h3, h4, h5, h6 are headers of different sizes (try a few)
* p is for a paragraph, smaller text, the actual content of the website

Links and Images
----------------

* Links allow your website to link to other websites!

```
<a href = "http://www.google.com">Google!</a>
```

* href specifies where the link goes to, and the text between the tags specifies what will appear on the website.
* href is an "attribute".  Tags often have multiple attributes like fonts, sizes, etc.

* Images can be displayed on a website in a similar way.

```
<img src="http://www.catster.com/wp-content/uploads/2017/08/A-fluffy-cat-looking-funny-surprised-or-concerned.jpg" alt="Angry Cat"></img>
```

* src is an attribute that indicates where the image is
* What is the alt attribute for?
* alt is useful for blind and deaf website visitors.
* height and width allow us to size the image in pixels, percents, or others
* Why is sizing using pixels a bad idea? (i.e. think about a phone's size)

Line Breaks
-----------

```
<br />
<hr />
```

* With these tags, we end the tag in a single element, rather than using an opening and closing tag.
* br makes an extra line of space
* hr makes a horizontal divider

* By default, HTML will ignore extra spaces that you add.

```
<p>This is some text.

This is some other text.</p>
```

* The code above will show as a single line, not multiple lines as expected.

* The pre tag allows you to format the text as you want to, but it should only be used in selected cases (e.g. code).

```
<pre>This is some text.

  This is some other text.</pre>
```

Comments
--------

* You can add comments to your html code with:

```
<!-- Do not display this at the moment -->
```

Exercise
--------

* Create a website about you!  There should be headings for things about you, where you're from, what you've done, things you like.
* You can include links to websites that you're interested in!
* You can include pictures of things that you're interested in!
* Next week, we'll start learning how to format it for more customization!
