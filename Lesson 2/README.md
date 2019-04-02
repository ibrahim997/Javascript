# Lesson 2

## Including Javascript in Your Web Page

Previously, you learned that Javascript programs are pased to the browser along with page content. But how exactly is that achieved? Two basic methods associate Javascript code with a HTML page, both of which use the <script></script> element introduced in Lesson 1.

One method is to include the Javascript statements directly into the HTML file, just like you did previously:
```javascript
<script>
  ... Javascript statements are written here...
</script>
```
A second method and more favourable method is to include your code in a separate file and use the <script> element to include that file by name using the scr (source) attribute:
```javascript
<script src='mycode.js'></script>
```
The file *mycode.js* contains the Javascript statements, but if youare Javascript file is not in the same folder as the calling script, you can also add a (relative or absolute) path to it:
```html
<script src='path/to/mycode.js'></script>
```
or
```html
<script src='http://www.example.com/path/to/mycode.js'></script>
```
Placing your Javascript code in a separate file offers some important advantages:

* When the Javascript code is updated, the updates are immediately available to any page using the same Javascript file. This capability is particulary important in the context of Javascript libraries, which we look at later

* The code for the HTML page is kept cleaner and therefore is easier to read and maintain

* Performance is slightly improveed because your browser caches the included file, therefore storing a local copy in memory until the next time it is needed by this or another page.

> Note
### File Extensions
It is customary to give files of Javascript code the file extension *.js*, as in this example. However, your included code files can have any extension, and the browser will try to interpret the contents as Javascript.

> Caution
### Take Care with Markup
The Javascript statements in the external file must NOT be surrounded by <script> .. </script> tags. In addition, you cannot place any HTML markup within the external file. Just include the raw Javascript code.

*Lesson2* shows the simple web page used in Lesson 1, but now with a file of Javascript code included in the <body> section. Javascript can be placed in either the head or body of the HTML page. In fact, it is more common - and generally recommened - for Javascript code to be placed in the head of the page, where it provides a number of functions that can be called from elsewhere in the document. Functions are discussed in Lesson 3.

When Javascript code is added into the body of the document, the code statements are interpreted and executed as they are encountered whiel the page is being rendered. For this reason, it's important that Javascript instructions do not try to access DOM elements that haven't yet been defined. Instead, Javascript must be included *after* the HTML defines such terms.

> Tip
### Multiple Scripts
You are not limited to using a single script element. You can have as many of them on the page as possible.

> Note
### HTML Comments
You sometimes see HTML-style comment notation *<! --* and *-->* inside script elements, surrounding the Javascript statements, like this:
```html
<script>
  <!---
    ... Javascript statements are written here ...
  -->
</script>
```
