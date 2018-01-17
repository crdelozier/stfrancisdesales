More HTML!
-----------

* There are many more tags in HTML.  Today, we'll look at a few that allow you to format data in lists, tables, and forms.

Tables
------

* Tables display data.  In a pinch, they can also be used to layout parts of the website.
* In the past, tables were used for almost all website layouts (before CSS became the defacto choice).

```
<table>
<tr>
<th>Name</th>
<th>City</th>
</tr>
<tr>
<td>Mr. DeLozier</td>
<td>Philadelphia</td>
</tr>
<tr>
<td>Mr. Picozzi</td>
<td>Pittsburgh</td>
</tr>
<tr>
<td>Mr. Stockton</td>
<td>Twin Cities</td>
</tr>
</table>
```

* The table tag starts and ends a table.
* The tr tag indicates a new row of the table.
* Tables in HTML are structured by rows first, then columns.
* The th tag indicates a new column that is meant to be the description of the data in the table for that column.
* The td tag indicates a new cell in the table.
* The number of th and td cells should match in each tr unless you want an uneven table.

Lists
-----

* HTML also allows us to make lists of things.

* ul is used for unordered lists, and ol is used for ordered lists.

```
<ul>
<li>One</li>
<li>Two</li>
<li>Three</li>
</ul>
```
* Lists can be nested.

Divs and Classes
----------------

* When we work with CSS, one of the main ways that we interface with it is by naming and classifying elements.

* For example, we might have part of our page dedicated to all of the links to otther pages.

```
<div id="navigation"></div>
```

* We can then refer to the name of our div in the CSS file using #navigation.

* We can also assign a class to an element.

```
<p class="emphasize"></p>
```

* We can refer to classes using .emphasize
